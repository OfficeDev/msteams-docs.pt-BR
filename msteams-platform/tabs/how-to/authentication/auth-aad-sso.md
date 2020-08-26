---
title: Logon Único
description: Descreve o logon único (SSO)
keywords: API de logon único do AAD no SSO de autenticação de equipes
ms.openlocfilehash: 503d5ff9779224d922ab0d45c6e2a3b33d7e0de7
ms.sourcegitcommit: 52732714105fac07c331cd31e370a9685f45d3e1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "46874853"
---
# <a name="single-sign-on-sso"></a>Logon único (SSO)

Os usuários entram no Microsoft Teams por meio de suas contas corporativas, de estudante ou da Microsoft (Office 365, Outlook, etc.). Você pode aproveitar isso permitindo que um único logon autorize sua guia do Microsoft Teams (ou módulo de tarefa) em clientes móveis ou de desktop. Portanto, se um usuário concorda em usar seu aplicativo, ele não precisará ser remetido em outro dispositivo, ele será conectado automaticamente. Além disso, prefetch seu token de acesso para melhorar o desempenho e os tempos de carga.

>[!NOTE]
> **Versões do cliente móvel do teams que dão suporte a SSO**  
>
> ✔ Teams for Android (1416/1.0.0.2020073101 e posterior)
>
> ✔ Teams para iOS (_versão_: 2.0.18 e posterior)  
>
> Para obter a melhor experiência com o Microsoft Teams, use a versão mais recente do iOS e do Android.

## <a name="how-sso-works-at-runtime"></a>Como o SSO funciona em tempo de execução

O diagrama a seguir mostra como funciona o processo de SSO:

<!-- markdownlint-disable MD033 -->
<img src="~/assets/images/tabs/tabs-sso-diagram.png" alt="Tab single sign-on SSO diagram" width="75%"/>

1. Na guia, é feita uma chamada JavaScript `getAuthToken()` . Isso instrui o Microsoft Teams a obter um token de autenticação para o aplicativo de guia.
2. Se esta é a primeira vez que o usuário atual usou seu aplicativo de guia, haverá um prompt de solicitação para o consentimento (se o consentimento for necessário) ou para lidar com a autenticação de depuração (como autenticação de dois fatores).
3. O Microsoft Teams solicita o token do aplicativo guia do ponto de extremidade do Azure AD para o usuário atual.
4. O Azure AD envia o token do aplicativo guia para o aplicativo Teams.
5. O Microsoft Teams envia o token do aplicativo guia para a guia como parte do objeto de resultado retornado pela `getAuthToken()` chamada.
6. O token será analisado no aplicativo guia, via JavaScript, para extrair as informações necessárias, como o endereço de email do usuário.

> [!NOTE]
> O `getAuthToken()` só é válido para o envio de um conjunto limitado de APIs de nível de usuário — email, perfil, offline_access e OpenID, e não para maiores escopos do Microsoft Graph, como `User.Read` ou `Mail.Read` . Consulte nossa seção no final deste documento para obter soluções alternativas sugeridas se você precisar de [escopos de gráfico adicionais](#apps-that-require-additional-microsoft-graph-scopes).

A API SSO também funcionará em [módulos de tarefas](../../../task-modules-and-cards/what-are-task-modules.md) que inserem conteúdo da Web.

## <a name="develop-an-sso-microsoft-teams-tab"></a>Desenvolver uma guia SSO do Microsoft Teams

Esta seção descreve as tarefas envolvidas na criação de uma guia do teams que usa SSO. Essas tarefas são descritas aqui, independente da linguagem e da estrutura.

### <a name="1-create-your-azure-active-directory-azure-ad-application"></a>1. criar seu aplicativo do Azure Active Directory (Azure AD)

#### <a name="registering-your-application-in-theazure-ad-portal-overview"></a>Registrar seu aplicativo na visão geral do[portal do Azure ad](https://azure.microsoft.com/features/azure-portal/) :

1. Obtenha sua [ID de aplicativo do Azure ad](/azure/active-directory/develop/howto-create-service-principal-portal#get-values-for-signing-in).
2. Especifique as permissões de que seu aplicativo precisa para o ponto de extremidade do Azure AD e, opcionalmente, o Microsoft Graph.
3. [Conceder permissões](/azure/active-directory/develop/howto-create-service-principal-portal#configure-access-policies-on-resources) para aplicativos de desktop, Web e móveis do teams.
4. Pré-autorizar o Microsoft Teams selecionando o botão **Adicionar um escopo** e no painel que é aberto, insira `access_as_user` como o **nome do escopo**.

> [!NOTE]
> Há algumas restrições importantes que você deve ter em mente:
>
> * Só damos suporte a permissões de API do Microsoft Graph em nível de usuário, ou seja, email, perfil, offline_access, OpenId. Se você precisar acessar outros escopos do Microsoft Graph (como `User.Read` ou `Mail.Read` ), consulte nossa [solução alternativa recomendada](#apps-that-require-additional-microsoft-graph-scopes) no final desta documentação.
> * É importante que o nome de domínio do aplicativo seja o mesmo que o nome de domínio que você está registrando para seu aplicativo do Azure AD.
> * No momento, não há suporte para vários domínios por aplicativo.
> * Não há suporte para aplicativos que usam o `azurewebsites.net` domínio porque são muito comuns e podem ser um risco de segurança. No entanto, estamos buscando ativamente a remoção dessa restrição.

#### <a name="registering-your-app-through-the-azure-active-directory-portal-in-depth"></a>Registrar seu aplicativo por meio do portal do Azure Active Directory em profundidade:

1. Registrar um novo aplicativo no portal [do Azure Active Directory – registros de aplicativos](https://go.microsoft.com/fwlink/?linkid=2083908) .
2. Selecione **novo registro** e na *página registrar um aplicativo*, defina os seguintes valores:
    * Defina o **nome** como o nome do aplicativo.
    * Escolha os **tipos de conta com suporte** (qualquer tipo de conta funcionará) ¹
    * Deixe o **URI de Redirecionamento** vazio.
    * Escolha **Registrar**.
3. Na página Visão geral, copie e salve a **ID do aplicativo (cliente)**. Você precisará dele mais tarde ao atualizar o manifesto do aplicativo do Microsoft Teams.
4. Em **Gerenciar**, selecione **Expor uma API**. 
5. Selecione o link **definir** para gerar o URI da ID do aplicativo no formato de `api://{AppID}` . Insira o nome de domínio totalmente qualificado (com uma barra "/" acrescentada ao final) entre as barras duplas de avanço e o GUID. A ID completa deve ter a forma de: `api://fully-qualified-domain-name.com/{AppID}` ²
    * ex: `api://subdomain.example.com/00000000-0000-0000-0000-000000000000` .
    
    O nome de domínio totalmente qualificado é o nome de domínio legível para pessoas a partir do qual seu aplicativo é fornecido. Se você estiver usando um serviço de encapsulamento como ngrok, será necessário atualizar esse valor sempre que o subdomínio do ngrok for alterado. 
6. Selecione o botão **Adicionar um escopo**. No painel que se abre, insira `access_as_user` como o **Nome de escopo**.
7. Definir **quem pode consentir?** para `Admins and users`
8. Preencha os campos para configurar os prompts de consentimento de usuário e administrador com os valores que são apropriados para o `access_as_user` escopo:
    * **Título do consentimento do administrador:** O Microsoft Teams pode acessar o perfil do usuário.
    * **Descrição do consentimento do administrador**: permite que o Teams chame as APIs Web do aplicativo como o usuário atual.
    * **Título de consentimento do usuário**: o Teams pode acessar o perfil do usuário e fazer solicitações no nome do usuário.
    * **Descrição do consentimento do usuário:** Habilite o Teams para chamar as APIs deste aplicativo com os mesmos direitos do usuário.
9. Verifique se o **estado** está definido como **habilitado**
10. Selecione o botão **Adicionar escopo** para salvar 
    * A parte de domínio do **nome do escopo** exibida logo abaixo do campo de texto deve coincidir automaticamente com o conjunto de URI da **ID do aplicativo** na etapa anterior, com `/access_as_user` acrescentado ao final:
        * `api://subdomain.example.com/00000000-0000-0000-0000-000000000000/access_as_user`
11. Na seção **aplicativos cliente autorizados** , identifique os aplicativos que você deseja autorizar para o aplicativo Web do seu aplicativo. Selecione *Adicionar um aplicativo cliente*. Insira cada uma das seguintes IDs de cliente e selecione o escopo autorizado que você criou na etapa anterior:
    * `1fec8e78-bce4-4aaf-ab1b-5451cc387264` (Aplicativo móvel/aplicativo de área de trabalho do Microsoft Teams)
    * `5e3ce6c0-2b1f-4285-8d4b-75ee78787346` (Aplicativo Web do Teams)
12. Navegue até **permissões de API**. Selecione *Adicionar uma permissão*  >  *Microsoft Graph*  >  *as permissões delegadas*do Microsoft Graph e, em seguida, adicione as seguintes permissões:
    * User. Read (ativado por padrão)
    * email
    * offline_access
    * OpenId
    * perfil

13. Navegar para **autenticação**

    Se um aplicativo não recebeu o consentimento do administrador de ti, os usuários precisarão fornecer consentimento na primeira vez em que usarem um aplicativo.

    Definir um URI de redirecionamento:
    * Selecione **Adicionar uma plataforma**.
    * Selecione **Web**.
    * Insira o **URI de redirecionamento** para seu aplicativo. Essa será a página em que um fluxo de concessão implícito bem-sucedido redirecionará o usuário. Este será o mesmo nome de domínio totalmente qualificado que você inseriu na etapa 5 seguido pela rota de API onde uma resposta de autenticação deve ser enviada. Se você estiver seguindo qualquer um dos exemplos do Teams, isso será: `https://subdomain.example.com/auth-end`

    Em seguida, habilite a concessão implícita marcando as seguintes caixas:  
    Token de ID de ✔  
    Token de acesso ✔  
    
Parabéns! Você concluiu a prerequsities de registro de aplicativos para prosseguir com o aplicativo de guia de SSO.     

> [!NOTE]
>
> * ¹ se o seu aplicativo do Azure AD estiver registrado no _mesmo_ locatário em que você está fazendo uma solicitação de autenticação no Teams, o usuário não será solicitado a fazer o consentimento e receberá um token de acesso imediatamente. Os usuários só precisam concordar com essas permissões se o aplicativo do Azure AD estiver registrado em um locatário diferente.
> * ² se você receber um erro informando que o domínio já pertence e você é o proprietário, siga o procedimento em [início rápido: Adicione um nome de domínio personalizado ao Azure Active Directory](/azure/active-directory/fundamentals/add-custom-domain) para registrar o domínio e, em seguida, repita a etapa 5, acima. (Esse erro também pode ocorrer se você não tiver entrado com credenciais de administrador no Office 365 locação).
> * Se você não estiver recebendo o UPN (nome principal do usuário) no token de acesso retornado, você poderá adicioná-lo como uma [declaração opcional](https://docs.microsoft.com/azure/active-directory/develop/active-directory-optional-claims) no Azure AD.

### <a name="2-update-your-microsoft-teams-application-manifest"></a>2. atualize seu manifesto de aplicativo do Microsoft Teams

Adicione novas propriedades ao manifesto do Microsoft Teams:

* **WebApplicationInfo** -o pai dos seguintes elementos:

> [!div class="checklist"]
> * **ID** – a ID do cliente do aplicativo. Esta é a ID do aplicativo que você obteve como parte do registro do aplicativo com o Azure AD.
>* **Resource** -o domínio e o subdomínio do aplicativo. Este é o mesmo URI (incluindo o `api://` protocolo) que você registrou ao criar seu `scope` na etapa 6 acima. Você não deve incluir o `access_as_user` caminho em seu recurso. A parte de domínio desse URI deve corresponder ao domínio, incluindo todos os subdomínios, usados nas URLs do manifesto de aplicativo do Microsoft Teams.

```json
"webApplicationInfo": {
  "id": "00000000-0000-0000-0000-000000000000",
  "resource": "api://subdomain.example.com/00000000-0000-0000-0000-000000000000"
}
```

> [!NOTE]
>
>* O recurso para um aplicativo do AAD normalmente será a raiz da URL do site e a appID (por exemplo, `api://subdomain.example.com/00000000-0000-0000-0000-000000000000` ). Também utilizamos esse valor para garantir que sua solicitação seja proveniente do mesmo domínio. Portanto, certifique-se de que o `contentURL` para sua guia usa os mesmos domínios de sua propriedade de recurso.
>* Você precisa usar a versão 1,5 ou superior do manifesto para implementar o `webApplicationInfo` campo.

### <a name="3-get-an-authentication-token-from-your-client-side-code"></a>3. Obtenha um token de autenticação do seu código do lado do cliente

Veja a aparência da API de autenticação:

```javascript
var authTokenRequest = {
  successCallback: function(result) { console.log("Success: " + result); },
  failureCallback: function(error) { console.log("Failure: " + error); },
};
microsoftTeams.authentication.getAuthToken(authTokenRequest);
```

Quando você chama `getAuthToken` e o consentimento do usuário adicional é necessário (para permissões no nível do usuário), mostraremos uma caixa de diálogo para o usuário incentivando-o a conceder consentimento adicional. 

Depois de receber o token de acesso no retorno de chamada de êxito, você poderá decodificar o token de acesso para exibir as declarações associadas a esse token. (Opcionalmente, você pode copiar/colar manualmente o token de acesso em uma ferramenta como o [JWT.Io](https://jwt.io/) para inspecionar seu conteúdo). Se você não estiver recebendo o UPN (nome principal do usuário) no token de acesso retornado, você poderá adicioná-lo como uma [declaração opcional](https://docs.microsoft.com/azure/active-directory/develop/active-directory-optional-claims) no Azure AD.

<p>
    <img src="~/assets/images/tabs/tabs-sso-prompt.png" alt="Tab single sign-on SSO dialog prompt" width="75%"/>
</p>

## <a name="sample-code"></a>Código de exemplo

Visite nosso exemplo de aplicativo: [guias MSTeams de SSO de exemplo-NodeJS](https://github.com/OfficeDev/msteams-tabs-sso-sample-nodejs)

O LEIAme explica como configurar seu ambiente de desenvolvimento e como configurar seu aplicativo no Azure AD. Você também pode encontrar mais informações sobre como o exemplo é estruturado na [seção estrutura de aplicativos](https://github.com/OfficeDev/msteams-tabs-sso-sample-nodejs#app-structure) para ajudar a se familiarizar com a codebase.

## <a name="known-limitations"></a>Limitações conhecidas

### <a name="apps-that-require-additional-microsoft-graph-scopes"></a>Aplicativos que exigem escopos adicionais do Microsoft Graph

Nossa implementação atual do SSO concede consentimento apenas para permissões no nível do usuário — email, perfil, offline_access, OpenId, não para outras APIs (como User. Read ou mail. Read). Se seu aplicativo precisar de mais escopos do Microsoft Graph, aqui estão algumas soluções habilitadas:

#### <a name="tenant-admin-consent"></a>Consentimento do administrador do locatário

A abordagem mais simples é obter um administrador de locatários para se concordar em nome da organização. Isso significa que os usuários não terão que se concordar com esses escopos e você poderá, então, ser livre para trocar o lado do servidor de token usando o [fluxo em nome](/azure/active-directory/develop/v1-oauth2-on-behalf-of-flow)do AD do Azure AD. Essa solução alternativa é aceitável para aplicativos de linha de negócios internos, mas pode não ser suficiente para desenvolvedores terceirizados que podem não confiar na aprovação do administrador de locatários.

Uma maneira simples de conenviar em nome de uma organização (como um administrador de locatários) é visitar:

* `https://login.microsoftonline.com/common/adminconsent?client_id=<AAD_App_ID>`

#### <a name="asking-for-additional-consent-using-the-auth-api"></a>Solicitar consentimento adicional usando a API de autenticação

Outra abordagem para obter escopos adicionais do Microsoft Graph é apresentar uma caixa de diálogo de consentimento usando nossa [abordagem existente de autenticação do Azure ad baseada na Web,](~/tabs/how-to/authentication/auth-tab-aad.md#navigate-to-the-authorization-page-from-your-popup-page) que envolve a apresentação de uma caixa de diálogo de consentimento do Azure Active Directory. Há algumas adições notáveis:

1. O token recuperado usando `getAuthToken()` precisa ser trocado no servidor usando o [fluxo em nome do](/azure/active-directory/develop/v2-oauth2-on-behalf-of-flow) Azure ad para obter acesso a essas APIs adicionais do Microsoft Graph.
    * Certifique-se de usar o ponto de extremidade v2 do Microsoft Graph para esta troca
2. Se o Exchange falhar, o Azure AD retornará uma exceção de concessão inválida. Há geralmente uma de duas mensagens de erro: `invalid_grant` ou `interaction_required`
3. Quando o Exchange falhar, você precisará solicitar o consentimento adicional. Recomendamos que você mostre algumas interfaces de usuário solicitando que o usuário conceda um consentimento adicional. Esta interface do usuário deve incluir um botão que dispara uma caixa de diálogo de consentimento do Azure Active Directory usando nossa [API de autenticação do AD do Azure](~/concepts/authentication/auth-silent-aad.md).
4. Ao solicitar o consentimento adicional do Azure AD, você precisa incluir `prompt=consent` em seu [parâmetro de cadeia de caracteres de consulta](~/tabs/how-to/authentication/auth-silent-aad.md#get-the-user-context) para o Azure ad caso contrário, o Azure ad não solicitará os escopos adicionais.
    * Em vez de: `?scope={scopes}`
    * Use: `?prompt=consent&scope={scopes}`
    * Certifique-se de `{scopes}` incluir todos os escopos para os quais você está solicitando o usuário (ex: mail. Read ou User. Read).
5. Depois que o usuário tiver concedido permissão adicional, repita o em em nome de fluxo para obter acesso a essas APIs adicionais.

### <a name="non-azure-ad-authentication"></a>Autenticação não do Azure AD

A solução de autenticação descrita acima só funciona para aplicativos e serviços que dão suporte ao Azure AD como um provedor de identidade. Os aplicativos que desejam autenticar usando serviços baseados no AD não-Azure precisam continuar usando o fluxo de [autenticação da Web](~/concepts/authentication.md)baseado em pop-up.
