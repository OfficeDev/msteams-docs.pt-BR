---
title: Suporte de single sign-on para guias
description: Descreve o SSO (single sign-on)
ms.topic: how-to
keywords: api de SSO AAD de autenticação de equipes
ms.openlocfilehash: ed8b52416dd1499f50d561ceb2c1edf03e5457d3
ms.sourcegitcommit: f74b74d5bed1df193e59f46121ada443fb57277b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2021
ms.locfileid: "50093264"
---
# <a name="single-sign-on-sso-support-for-tabs"></a>Suporte a SSO (single sign-on) para guias

Os usuários podem entrar no Microsoft Teams por meio de contas do trabalho, da escola ou da Microsoft (Office 365, Outlook, etc.). Você pode tirar proveito disso permitindo um único login para autorizar sua guia do Microsoft Teams (ou módulo de tarefa) em clientes móveis ou desktop. Portanto, se um usuário consentir em usar seu aplicativo, ele não terá que consentir novamente em outro dispositivo — ele será conectado automaticamente. Além disso, buscamos previamente seu token de acesso para melhorar o desempenho e os tempos de carregamento.

> [!NOTE]
> **Versões do cliente móvel do Teams que suportam SSO**  
>
> ✔Teams para Android (1416/1.0.0.2020073101 e posterior)
>
> ✔Teams para iOS (_versão_: 2.0.18 e posteriores)  
>
> Para ter a melhor experiência com o Teams, use a versão mais recente do iOS e android.

> [!NOTE]
> **Início rápido**  
>
> O caminho mais simples para começar a trabalhar com o SSO da guia é com o Kit de Ferramentas do Microsoft Teams para Visual Studio Code. [Saiba Mais](../../../toolkit/visual-studio-code-tab-sso.md)

## <a name="how-sso-works-at-runtime"></a>Como o SSO funciona em tempo de execução

O diagrama a seguir mostra como funciona o processo de SSO:

<!-- markdownlint-disable MD033 -->
<img src="~/assets/images/tabs/tabs-sso-diagram.png" alt="Tab single sign-on SSO diagram" width="75%"/>

1. Na guia, uma chamada JavaScript é feita `getAuthToken()` para. Isso informa ao Teams para obter um token de autenticação para o aplicativo guia.
2. Se esta for a primeira vez que o usuário atual usou o aplicativo de guia, haverá uma solicitação de solicitação de consentimento (se o consentimento for necessário) ou para manipular a autenticação de etapa (como a autenticação de dois fatores).
3. O Teams solicita o token do aplicativo de guia do ponto de extremidade do Azure AD para o usuário atual.
4. O Azure AD envia o token do aplicativo guia para o aplicativo Teams.
5. O Teams envia o token do aplicativo de guia para a guia como parte do objeto de resultado retornado pela `getAuthToken()` chamada.
6. O token será analisado no aplicativo guia, via JavaScript, para extrair as informações necessárias, como o endereço de email do usuário.

> [!NOTE]
> Só é válido para consentir um conjunto limitado de APIs no nível do usuário — email, perfil, offline_access e OpenId — e não para escopos posteriores do Microsoft Graph, como `getAuthToken()` `User.Read` ou `Mail.Read` . Confira nossa seção no final deste documento para obter sugestões de soluções alternativas se você precisar de [escopos adicionais do Graph.](#apps-that-require-additional-microsoft-graph-scopes)

A API SSO também funcionará em [Módulos de Tarefas](../../../task-modules-and-cards/what-are-task-modules.md) que incorporam conteúdo da Web.

## <a name="develop-an-sso-microsoft-teams-tab"></a>Desenvolver uma guia SSO do Microsoft Teams

Esta seção descreve as tarefas envolvidas na criação de uma guia do Teams que usa SSO. Essas tarefas são descritas aqui de acordo com idioma e estrutura.

### <a name="1-create-your-azure-active-directory-azure-ad-application"></a>1. Crie seu aplicativo do Azure Active Directory (Azure AD)

#### <a name="registering-your-application-in-theazure-ad-portal-overview"></a>Registrar seu aplicativo na visão geral do portal do[Azure AD:](https://azure.microsoft.com/features/azure-portal/)

1. Obter sua [ID de aplicativo do Azure AD.](/azure/active-directory/develop/howto-create-service-principal-portal#get-values-for-signing-in)
2. Especifique as permissões que seu aplicativo precisa para o ponto de extremidade do Azure AD e, opcionalmente, o Microsoft Graph.
3. [Conceda permissões para aplicativos](/azure/active-directory/develop/howto-create-service-principal-portal#configure-access-policies-on-resources) móveis, da web e da área de trabalho do Teams.
4. Pré-autorizar o Teams selecionando **o botão Adicionar** um escopo e, no painel que é aberto, insira como o nome do `access_as_user` **escopo.**

> [!NOTE]
> Há algumas restrições importantes que você deve estar ciente:
>
> * Só damos suporte a permissões de API do Microsoft Graph em nível de usuário, ou seja, email, perfil, offline_access, OpenId. Se você precisar de acesso a outros escopos do Microsoft Graph (como ou ), consulte nossa solução alternativa recomendada `User.Read` `Mail.Read` no final desta documentação. [](#apps-that-require-additional-microsoft-graph-scopes)
> * É importante que o nome de domínio do seu aplicativo seja o mesmo que o nome de domínio que você registrou para seu aplicativo do Azure AD.
> * Atualmente, não há suporte para vários domínios por aplicativo.
> * Não há suporte para aplicativos que usam o domínio `azurewebsites.net` porque é muito comum e pode ser um risco à segurança. No entanto, estamos ativamente buscando remover essa restrição.

#### <a name="registering-your-app-through-the-azure-active-directory-portal-in-depth"></a>Registrar seu aplicativo por meio do portal do Azure Active Directory em detalhes:

1. Registre um novo aplicativo no [Azure Active Directory – portal de Registros de Aplicativos.](https://go.microsoft.com/fwlink/?linkid=2083908)
2. Selecione **Novo Registro e,** na *página registrar um aplicativo,* de definir os seguintes valores:
    * De **acordo com** o nome do aplicativo.
    * Escolha os **tipos de conta com** suporte (qualquer tipo de conta funcionará) ¹
    * Deixe o **URI de Redirecionamento** vazio.
    * Escolha **Registrar**.
3. Na página de visão geral, copie e salve a **ID do aplicativo (cliente).** Você precisará dele mais tarde ao atualizar seu manifesto de aplicativo do Teams.
4. Em **Gerenciar**, selecione **Expor uma API**. 
5. Selecione o link **Definir** para gerar o URI da ID do Aplicativo na forma de `api://{AppID}` . Insira seu nome de domínio totalmente qualificado (com uma barra "/" anexada ao final) entre as duas barras e o GUID. A ID inteira deve ter a forma de: `api://fully-qualified-domain-name.com/{AppID}` ²
    * ex: `api://subdomain.example.com/00000000-0000-0000-0000-000000000000` .
    
    O nome de domínio totalmente qualificado é o nome de domínio acessível para humanos a partir do qual seu aplicativo é atendido. Se você estiver usando um serviço de túnel como o ngrok, precisará atualizar esse valor sempre que seu subdomínio ngrok mudar. 
6. Selecione o botão **Adicionar um escopo**. No painel que se abre, insira `access_as_user` como o **Nome de escopo**.
7. Definir **quem pode consentir?**`Admins and users`
8. Preencha os campos para configurar as solicitações de consentimento do administrador e do usuário com valores apropriados para o `access_as_user` escopo:
    * **Título do consentimento do administrador:** O Teams pode acessar o perfil do usuário.
    * **Descrição do** consentimento do administrador: permite que o Teams chame as APIs da Web do aplicativo como o usuário atual.
    * **Título de consentimento do** usuário: o Teams pode acessar o perfil do usuário e fazer solicitações em nome do usuário.
    * **Descrição do consentimento do usuário:** Habilita o Teams a chamar as APIs desse aplicativo com os mesmos direitos que o usuário.
9. Certifique-se **de que** o estado está definido **como Habilitado**
10. Selecione o **botão Adicionar escopo** para salvar 
    * A parte de  domínio do nome do Escopo exibida logo abaixo do campo de texto deve corresponder automaticamente ao URI **da ID** do Aplicativo definido na etapa anterior, com anexado `/access_as_user` ao final:
        * `api://subdomain.example.com/00000000-0000-0000-0000-000000000000/access_as_user`
11. Na seção **Aplicativos cliente autorizados,** identifique os aplicativos que você deseja autorizar para o aplicativo Web do seu aplicativo. Selecione *Adicionar um aplicativo cliente.* Insira cada uma das seguintes IDs de cliente e selecione o escopo autorizado criado na etapa anterior:
    * `1fec8e78-bce4-4aaf-ab1b-5451cc387264` (Aplicativo móvel/desktop do Teams)
    * `5e3ce6c0-2b1f-4285-8d4b-75ee78787346` (Aplicativo Web do Teams)
12. Navegue até **permissões de API.** Selecione *Adicionar uma permissão permissões*  >  *delegadas* do Microsoft Graph e, em  >  seguida, adicione as seguintes permissões da API do Microsoft Graph:
    * User.Read (habilitado por padrão)
    * email
    * offline_access
    * OpenId
    * perfil

13. Navegar para **Autenticação**

    Se um aplicativo não tiver sido concedido o consentimento do administrador de IT, os usuários terão que dar consentimento na primeira vez que usarem um aplicativo.

    Definir um URI de redirecionamento:
    * Selecione **Adicionar uma plataforma.**
    * Selecione **web**.
    * Insira o **URI de redirecionamento** para seu aplicativo. Esta será a página em que um fluxo de concessão implícito bem-sucedido redireciona o usuário. Esse será o mesmo nome de domínio totalmente qualificado inserido na etapa 5, seguido da rota da API para a qual uma resposta de autenticação deve ser enviada. Se você estiver seguindo qualquer um dos exemplos do Teams, isso será: `https://subdomain.example.com/auth-end`

    Em seguida, habilita a concessão implícita verificando as seguintes caixas:  
    ✔ token de ID do ✔  
    ✔ token de acesso  
    
Parabéns! Você concluiu os pré-requisitos de registro do aplicativo para continuar com seu aplicativo SSO da guia.     

> [!NOTE]
>
> * ¹ Se seu aplicativo do Azure  AD estiver registrado no mesmo locatário em que você está fazendo uma solicitação de autenticação no Teams, o usuário não será solicitado a consentir e receberá um token de acesso imediatamente. Os usuários só precisam consentir com essas permissões se o aplicativo Azure AD estiver registrado em um locatário diferente.
> * 8 Se você receber um erro informando que o domínio já é de propriedade e que você é o proprietário, siga o procedimento em Início Rápido: adicione um nome de domínio personalizado ao [Azure Active Directory](/azure/active-directory/fundamentals/add-custom-domain) para registrar o domínio e repita a etapa 5 acima. (Esse erro também poderá ocorrer se você não estiver londo com credenciais de Administrador no escritório do Office 365).
> * Se você não estiver recebendo o UPN (Nome Principal do Usuário) no token de acesso retornado, poderá adicioná-lo como uma declaração [opcional](https://docs.microsoft.com/azure/active-directory/develop/active-directory-optional-claims) no Azure AD.

### <a name="2-update-your-microsoft-teams-application-manifest"></a>2. Atualize o manifesto do aplicativo Microsoft Teams

Adicione novas propriedades ao manifesto do Microsoft Teams:

* **WebApplicationInfo** - O pai dos seguintes elementos:

> [!div class="checklist"]
> * **id** - A ID do cliente do aplicativo. Essa é a ID do aplicativo que você obteve como parte do registro do aplicativo no Azure AD.
>* **resource** - O domínio e o subdomínio do seu aplicativo. Esse é o mesmo URI (incluindo o protocolo) que você registrou `api://` ao criar o seu na etapa `scope` 6 acima. Você não deve incluir o `access_as_user` caminho em seu recurso. A parte de domínio desse URI deve corresponder ao domínio, incluindo qualquer sub-domínio, usado nas URLs do manifesto de aplicativo do Teams.

```json
"webApplicationInfo": {
  "id": "00000000-0000-0000-0000-000000000000",
  "resource": "api://subdomain.example.com/00000000-0000-0000-0000-000000000000"
}
```

> [!NOTE]
>
>* O recurso para um aplicativo AAD geralmente será a raiz de sua URL de site e a appID (por `api://subdomain.example.com/00000000-0000-0000-0000-000000000000` exemplo). Também usamos esse valor para garantir que sua solicitação seja proveniente do mesmo domínio. Portanto, certifique-se de `contentURL` que a guia da guia use os mesmos domínios da propriedade de recurso.
>* Você precisa usar o manifesto versão 1.5 ou superior para implementar o `webApplicationInfo` campo.

### <a name="3-get-an-authentication-token-from-your-client-side-code"></a>3. Obter um token de autenticação do código do lado do cliente

Esta é a aparência da API de autenticação:

```javascript
var authTokenRequest = {
  successCallback: function(result) { console.log("Success: " + result); },
  failureCallback: function(error) { console.log("Failure: " + error); }
};
microsoftTeams.authentication.getAuthToken(authTokenRequest);
```

Quando você ligar , e o consentimento adicional do usuário for necessário (para permissões no nível do usuário), mostraremos uma caixa de diálogo para o usuário incentivando-o `getAuthToken` a conceder consentimento adicional. 

Depois de receber o token de acesso no retorno de chamada de sucesso, você poderá decodificar o token de acesso para exibir as declarações associadas a esse token. (Opcionalmente, você pode copiar/colar manualmente o token de acesso em uma ferramenta como JWT.io [para](https://jwt.io/) inspecionar seu conteúdo). Se você não estiver recebendo o UPN (Nome Principal do Usuário) no token de acesso retornado, poderá adicioná-lo como uma declaração [opcional](https://docs.microsoft.com/azure/active-directory/develop/active-directory-optional-claims) no Azure AD.

<p>
    <img src="~/assets/images/tabs/tabs-sso-prompt.png" alt="Tab single sign-on SSO dialog prompt" width="75%"/>
</p>

## <a name="sample-code"></a>Código de exemplo

Visite nosso aplicativo de exemplo: [exemplo de SSO MSTeams PnP](https://github.com/pnp/teams-dev-samples/tree/master/samples/tab-sso)

O README explica como configurar seu ambiente de desenvolvimento e como configurar seu aplicativo no Azure AD. Você também pode encontrar mais informações sobre [](https://github.com/OfficeDev/msteams-tabs-sso-sample-nodejs#app-structure) como o exemplo é estruturado na seção de estrutura do aplicativo para ajudar a se familiarizar com a base de código.

## <a name="known-limitations"></a>Limitações conhecidas

### <a name="apps-that-require-additional-microsoft-graph-scopes"></a>Aplicativos que exigem escopos adicionais do Microsoft Graph

Nossa implementação atual de SSO concede consentimento apenas para permissões no nível do usuário — email, perfil, offline_access, OpenId — não para outras APIs (como User.Read ou Mail.Read). Se seu aplicativo precisar de mais escopos do Microsoft Graph, aqui estão algumas soluções alternativas de habilitação:

#### <a name="tenant-admin-consent"></a>Consentimento do administrador do locatário

A abordagem mais simples é fazer com que um administrador de locatários consenta previamente em nome da organização. Isso significa que os usuários não terão que consentir com esses escopos e, em seguida, [](/azure/active-directory/develop/v1-oauth2-on-behalf-of-flow)você poderá ficar livre para trocar o lado do servidor de token usando o fluxo em nome de do Azure AD. Essa solução alternativa é aceitável para aplicativos de linha de negócios internos, mas pode não ser suficiente para desenvolvedores de terceiros que podem não depender da aprovação do administrador de locatários.

Uma maneira simples de consentir em nome de uma organização (como administrador de locatários) é visitar:

* `https://login.microsoftonline.com/common/adminconsent?client_id=<AAD_App_ID>`

#### <a name="asking-for-additional-consent-using-the-auth-api"></a>Solicitando consentimento adicional usando a API de Auth

Outra abordagem para obter escopos adicionais do Microsoft Graph é apresentar uma caixa de diálogo de consentimento usando nossa abordagem existente de autenticação do [Azure AD](~/tabs/how-to/authentication/auth-tab-aad.md#navigate-to-the-authorization-page-from-your-popup-page) baseada na Web, que envolve abrir uma caixa de diálogo de consentimento do Azure AD. Há algumas adições notáveis:

1. O token recuperado usando precisa ser trocado no lado do servidor usando o fluxo em nome de do Azure AD para obter acesso a essas `getAuthToken()` APIs adicionais do [](/azure/active-directory/develop/v2-oauth2-on-behalf-of-flow) Microsoft Graph.
    * Certifique-se de usar o ponto de extremidade v2 do Microsoft Graph para este exchange
2. Se o intercâmbio falhar, o Azure AD retornará uma exceção de concessão inválida. Geralmente, há uma de duas mensagens de erro: `invalid_grant` ou `interaction_required`
3. Quando a troca falhar, você precisará pedir consentimento adicional. Recomendamos mostrar uma interface do usuário solicitando que o usuário conceda consentimento adicional. Essa interface do usuário deve incluir um botão que dispara uma caixa de diálogo de consentimento do Azure AD usando nossa API de autenticação do [Azure AD.](~/concepts/authentication/auth-silent-aad.md)
4. Ao solicitar consentimento adicional do Azure AD, você precisa incluir no parâmetro de cadeia de caracteres de consulta para o Azure AD, caso contrário, o Azure AD não solicitará os `prompt=consent` escopos adicionais. [](~/tabs/how-to/authentication/auth-silent-aad.md#get-the-user-context)
    * Em vez de: `?scope={scopes}`
    * Use isto: `?prompt=consent&scope={scopes}`
    * Certifique-se de incluir todos os escopos que você está solicitando ao usuário `{scopes}` (por exemplo: Mail.Read ou User.Read).
5. Depois que o usuário conceder permissão adicional, retry the on-behalf-of-flow to get access to these additional APIs.

### <a name="non-azure-ad-authentication"></a>Autenticação não Azure AD

A solução de autenticação descrita acima só funciona para aplicativos e serviços que suportam o Azure AD como um provedor de identidade. Os aplicativos que querem autenticar usando serviços não baseados no Azure AD precisam continuar usando o fluxo de autenticação [da Web baseado](~/concepts/authentication.md)em pop-up.

> [!NOTE] 
> O SSO é suportado para aplicativos de propriedade do cliente nos locatários do Azure AD B2C.