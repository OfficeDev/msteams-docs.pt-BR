---
title: Suporte de login único para guias
description: Descreve o SSO (sign-on único)
ms.topic: how-to
keywords: api de login único do SSO AAD de autenticação do teams
ms.openlocfilehash: 7b8406473b8356b9c26948641b49f7e1239e697a
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449259"
---
# <a name="single-sign-on-sso-support-for-tabs"></a>Suporte a SSO (login único) para guias

Os usuários entrar no Microsoft Teams por meio de suas contas de trabalho, escola ou Microsoft (Office 365, Outlook, etc. Você pode tirar proveito disso permitindo que um único login autorize sua guia do Microsoft Teams (ou módulo de tarefas) em clientes desktop ou móveis. Assim, se um usuário consentir em usar seu aplicativo, ele não terá que consentir novamente em outro dispositivo — ele será conectado automaticamente. Além disso, prefetchamos seu token de acesso para melhorar o desempenho e os tempos de carga.

> [!NOTE]
> **Versões do cliente móvel do Teams que suportam SSO**  
>
> ✔Teams para Android (1416/1.0.0.2020073101 e posterior)
>
> ✔Teams para iOS (_Versão_: 2.0.18 e posterior)  
>
> Para ter a melhor experiência com o Teams, use a versão mais recente do iOS e android.

> [!NOTE]
> **Início rápido**  
>
> O caminho mais simples para começar com a guia SSO é com o Microsoft Teams Toolkit para Visual Studio Code. [Saiba Mais](../../../toolkit/visual-studio-code-tab-sso.md)

## <a name="how-sso-works-at-runtime"></a>Como o SSO funciona em tempo de execução

O diagrama a seguir mostra como o processo de SSO funciona:

<!-- markdownlint-disable MD033 -->
<img src="~/assets/images/tabs/tabs-sso-diagram.png" alt="Tab single sign-on SSO diagram" width="75%"/>

1. Na guia, uma chamada JavaScript é feita para `getAuthToken()` . Isso diz ao Teams para obter um token de autenticação para o aplicativo de tabulação.
2. Se essa for a primeira vez que o usuário atual usou seu aplicativo de tabulação, haverá um prompt de solicitação para consentimento (se o consentimento for necessário) ou para manipular a autenticação de etapa (como autenticação de dois fatores).
3. O Teams solicita o token de aplicativo de tabulação do ponto de extremidade do Azure AD para o usuário atual.
4. O Azure AD envia o token de aplicativo de tabulação para o aplicativo teams.
5. O Teams envia o token de aplicativo de tabulação para a guia como parte do objeto de resultado retornado pela `getAuthToken()` chamada.
6. O token será analisado no aplicativo de tabulação, via JavaScript, para extrair as informações necessárias, como o endereço de email do usuário.

> [!NOTE]
> O é válido apenas para consentir um conjunto limitado de APIs no nível do usuário — email, perfil, offline_access e OpenId — e não para escopos do Microsoft Graph como `getAuthToken()` `User.Read` ou `Mail.Read` . Consulte nossa seção no final deste documento para obter soluções alternativas sugeridas se você precisar de [escopos adicionais do Graph.](#apps-that-require-additional-microsoft-graph-scopes)

A API do SSO também funcionará em [Módulos de Tarefas](../../../task-modules-and-cards/what-are-task-modules.md) que incorporam conteúdo da Web.

## <a name="develop-an-sso-microsoft-teams-tab"></a>Desenvolver uma guia SSO do Microsoft Teams

Esta seção descreve as tarefas envolvidas na criação de uma guia do Teams que usa SSO. Essas tarefas são descritas aqui como idioma e framework-agnóstico.

### <a name="1-create-your-azure-active-directory-azure-ad-application"></a>1. Crie seu aplicativo do Azure Active Directory (Azure AD)

#### <a name="registering-your-application-in-theazure-ad-portal-overview"></a>Registrar seu aplicativo na visão geral[do portal do Azure AD:](https://azure.microsoft.com/features/azure-portal/)

1. Obter a ID do aplicativo [do Azure AD.](/azure/active-directory/develop/howto-create-service-principal-portal#get-values-for-signing-in)
2. Especifique as permissões que seu aplicativo precisa para o ponto de extremidade do Azure AD e, opcionalmente, o Microsoft Graph.
3. [Conceda permissões](/azure/active-directory/develop/howto-create-service-principal-portal#configure-access-policies-on-resources) para aplicativos desktop, web e móveis do Teams.
4. Pré-autorizar o Teams selecionando **o botão Adicionar um escopo** e, no painel que é aberto, digite como o nome do `access_as_user` **escopo**.

> [!NOTE]
> Há algumas restrições importantes que você deve estar ciente:
>
> * Só suportamos permissões de API do Microsoft Graph no nível do usuário, ou seja, email, perfil, offline_access, OpenId. Se você precisar de acesso a outros escopos do Microsoft Graph (como ou ), consulte nossa solução alternativa recomendada no `User.Read` `Mail.Read` final desta documentação. [](#apps-that-require-additional-microsoft-graph-scopes)
> * É importante que o nome de domínio do aplicativo seja o mesmo que o nome de domínio que você registrou no aplicativo do Azure AD.
> * Atualmente, não há suporte para vários domínios por aplicativo.
> * Não suportamos aplicativos que usam o `azurewebsites.net` domínio porque ele é muito comum e pode ser um risco de segurança. No entanto, estamos procurando ativamente remover essa restrição.

#### <a name="registering-your-app-through-the-azure-active-directory-portal-in-depth"></a>Registrar seu aplicativo por meio do portal do Azure Active Directory detalhadamente:

1. Registre um novo aplicativo no [portal do Azure Active Directory – Registros de Aplicativos.](https://go.microsoft.com/fwlink/?linkid=2083908)
2. Selecione **Novo Registro** e, na página registrar um *aplicativo,* de definir os seguintes valores:
    * De **definir o** nome do seu aplicativo.
    * Escolha os **tipos de conta com** suporte (qualquer tipo de conta funcionará) ¹
    * Deixe o **URI de Redirecionamento** vazio.
    * Escolha **Registrar**.
3. Na página visão geral, copie e salve a **ID do aplicativo (cliente).** Você precisará dele mais tarde ao atualizar o manifesto do aplicativo do Teams.
4. Em **Gerenciar**, selecione **Expor uma API**. 
5. Selecione o link **Definir** para gerar o URI de ID do Aplicativo no formato `api://{AppID}` de . Insira seu nome de domínio totalmente qualificado (com uma barra de avanço "/" anexada ao final) entre as barras de avanço duplo e o GUID. A ID inteira deve ter a forma de: `api://fully-qualified-domain-name.com/{AppID}` ²
    * ex: `api://subdomain.example.com/00000000-0000-0000-0000-000000000000` .
    
    O nome de domínio totalmente qualificado é o nome de domínio acessível para humanos a partir do qual seu aplicativo é servido. Se você estiver usando um serviço de tunelamento como ngrok, precisará atualizar esse valor sempre que o subdomínio ngrok mudar. 
6. Selecione o botão **Adicionar um escopo**. No painel que se abre, insira `access_as_user` como o **Nome de escopo**.
7. Definir **Quem pode consentir?**`Admins and users`
8. Preencha os campos para configurar os prompts de consentimento do administrador e do usuário com valores apropriados para o `access_as_user` escopo:
    * **Título de consentimento do administrador:** O Teams pode acessar o perfil do usuário.
    * **Descrição do** consentimento do administrador : Permite que o Teams chame as APIs da Web do aplicativo como o usuário atual.
    * **Título de consentimento do** usuário : o Teams pode acessar o perfil de usuário e fazer solicitações em nome do usuário.
    * **Descrição do consentimento do usuário:** Habilita o Teams a chamar as APIs desse aplicativo com os mesmos direitos do usuário.
9. Verifique se **o estado** está definido como **Habilitado**
10. Selecione o **botão Adicionar escopo** para salvar 
    * A parte de domínio do nome **escopo** exibida logo abaixo do campo de texto deve corresponder automaticamente ao conjunto de URI de **ID** do aplicativo na etapa anterior, com anexado `/access_as_user` ao final:
        * `api://subdomain.example.com/00000000-0000-0000-0000-000000000000/access_as_user`
11. Na seção **Aplicativos cliente autorizados,** identifique os aplicativos que você deseja autorizar para o aplicativo Web do seu aplicativo. Selecione *Adicionar um aplicativo cliente*. Insira cada uma das seguintes IDs de cliente e selecione o escopo autorizado criado na etapa anterior:
    * `1fec8e78-bce4-4aaf-ab1b-5451cc387264` (Aplicativo móvel/desktop do Teams)
    * `5e3ce6c0-2b1f-4285-8d4b-75ee78787346` (Aplicativo Web do Teams)
12. Navegue até **Permissões de API**. Selecione *Adicionar uma permissão permissões* Delegadas do Microsoft Graph e adicione as seguintes permissões da API do Microsoft  >    >  Graph:
    * User.Read (habilitado por padrão)
    * email
    * offline_access
    * OpenId
    * perfil

13. Navegue até **Autenticação**

    Se um aplicativo não tiver sido concedido o consentimento do administrador de IT, os usuários terão que fornecer consentimento na primeira vez que usarem um aplicativo.

    Definir um URI de redirecionamento:
    * Selecione **Adicionar uma plataforma**.
    * Selecione **Web**.
    * Insira o **URI de redirecionamento** para seu aplicativo. Esta será a página onde um fluxo de concessão implícito bem-sucedido redireciona o usuário. Esse será o mesmo nome de domínio totalmente qualificado que você entrou na etapa 5 seguido pela rota da API para a qual uma resposta de autenticação deve ser enviada. Se você estiver seguindo qualquer um dos exemplos do Teams, isso será: `https://subdomain.example.com/auth-end`

    Em seguida, habilita a concessão implícita verificando as seguintes caixas:  
    ✔ token de ID  
    ✔ Token de Acesso  
    
Parabéns! Você concluiu os pré-requisitos de registro do aplicativo para continuar com seu aplicativo SSO de guia.     

> [!NOTE]
>
> * ¹ Se seu aplicativo do Azure  AD estiver registrado no mesmo locatário em que você está fazendo uma solicitação de autenticação no Teams, o usuário não será solicitado a consentir e receberá um token de acesso imediatamente. Os usuários só precisarão consentir com essas permissões se o aplicativo do Azure AD estiver registrado em um locatário diferente.
> * ² Se você receber um erro informando que o domínio já pertence e você é o proprietário, siga o procedimento em Início Rápido: Adicione um nome de domínio personalizado ao [Azure Active Directory](/azure/active-directory/fundamentals/add-custom-domain) para registrar o domínio e repita a etapa 5, acima. (Esse erro também pode ocorrer se você não estiver assinado com credenciais de administrador no escritório do Office 365).
> * Se você não estiver recebendo o UPN (Nome principal do usuário) no token de acesso retornado, poderá adicioná-lo como uma declaração [opcional](https://docs.microsoft.com/azure/active-directory/develop/active-directory-optional-claims) no Azure AD.

### <a name="2-update-your-microsoft-teams-application-manifest"></a>2. Atualizar seu manifesto de aplicativo do Microsoft Teams

Adicione novas propriedades ao manifesto do Microsoft Teams:

* **WebApplicationInfo** - O pai dos seguintes elementos:

> [!div class="checklist"]
> * **id** - A ID do cliente do aplicativo. Esta é a ID do aplicativo que você obteve como parte do registro do aplicativo no Azure AD.
>* **resource** - O domínio e o subdomínio do seu aplicativo. Esse é o mesmo URI (incluindo o protocolo) que você registrou `api://` ao criar seu na etapa `scope` 6 acima. Você não deve incluir o `access_as_user` caminho em seu recurso. A parte de domínio desse URI deve corresponder ao domínio, incluindo quaisquer subdomas, usados nas URLs do manifesto do aplicativo teams.

```json
"webApplicationInfo": {
  "id": "00000000-0000-0000-0000-000000000000",
  "resource": "api://subdomain.example.com/00000000-0000-0000-0000-000000000000"
}
```

> [!NOTE]
>
>* O recurso para um aplicativo AAD geralmente será a raiz de sua URL de site e o appID (por `api://subdomain.example.com/00000000-0000-0000-0000-000000000000` exemplo, ). Também usamos esse valor para garantir que sua solicitação seja proveniente do mesmo domínio. Portanto, certifique-se de que `contentURL` a guia para sua guia use os mesmos domínios que sua propriedade resource.
>* Você precisa usar o manifesto versão 1.5 ou superior para implementar o `webApplicationInfo` campo.

### <a name="3-get-an-authentication-token-from-your-client-side-code"></a>3. Obter um token de autenticação do código do lado do cliente

Veja a aparência da API de autenticação:

```javascript
var authTokenRequest = {
  successCallback: function(result) { console.log("Success: " + result); },
  failureCallback: function(error) { console.log("Failure: " + error); }
};
microsoftTeams.authentication.getAuthToken(authTokenRequest);
```

Quando você chamar - e o consentimento adicional do usuário for necessário (para permissões no nível do usuário) - mostraremos uma caixa de diálogo para o usuário incentivando-o `getAuthToken` a conceder consentimento adicional. 

Depois de receber o token de acesso no retorno de chamada de sucesso, você pode decodificar o token de acesso para exibir as declarações associadas a esse token. Opcionalmente, você pode copiar e colar manualmente o token de acesso em uma ferramenta, como jwt.ms [inspecionar](https://jwt.ms/) seu conteúdo. Se você não estiver recebendo o Nome da Entidade de Usuário (UPN) no token de acesso retornado, poderá adicioná-lo como uma declaração [opcional](https://docs.microsoft.com/azure/active-directory/develop/active-directory-optional-claims) no Azure AD.

<p>
    <img src="~/assets/images/tabs/tabs-sso-prompt.png" alt="Tab single sign-on SSO dialog prompt" width="75%"/>
</p>

## <a name="code-sample"></a>Exemplo de código

|**Exemplo de nome**|**Descrição**|**C#**|**TypeScript**|
|---------------|---------------|------|--------------|
| Guia SSO |Aplicativo de exemplo do Microsoft Teams para guias do Azure AD SSO| [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-sso/csharp)|[Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/blob/main/samples/tab-sso/nodejs), </br>[Teams Toolkit](../../../toolkit/visual-studio-code-tab-sso.md)|

## <a name="known-limitations"></a>Limitações conhecidas

### <a name="apps-that-require-additional-microsoft-graph-scopes"></a>Aplicativos que exigem escopos adicionais do Microsoft Graph

Nossa implementação atual para o SSO concede consentimento apenas para permissões no nível do usuário — email, perfil, offline_access, OpenId — e não para outras APIs (como User.Read ou Mail.Read). Se seu aplicativo precisar de mais escopos do Microsoft Graph, aqui estão algumas soluções alternativas de habilitação:

#### <a name="tenant-admin-consent"></a>Consentimento do administrador do locatário

A abordagem mais simples é fazer com que um administrador de locatários consenta previamente em nome da organização. Isso significa que os usuários não terão que consentir com esses escopos e você poderá ser livre para trocar o lado do servidor de token usando o fluxo [on-behalf-of](/azure/active-directory/develop/v1-oauth2-on-behalf-of-flow)do Azure AD. Essa solução alternativa é aceitável para aplicativos internos de linha de negócios, mas pode não ser suficiente para desenvolvedores de terceiros que talvez não possam depender da aprovação do administrador de locatários.

Uma maneira simples de consentir em nome de uma organização (como administrador de locatário) é visitar:

* `https://login.microsoftonline.com/common/adminconsent?client_id=<AAD_App_ID>`

#### <a name="asking-for-additional-consent-using-the-auth-api"></a>Solicitando consentimento adicional usando a API Auth

Outra abordagem para obter escopos adicionais do Microsoft Graph é apresentar uma caixa de diálogo de consentimento usando nossa abordagem de autenticação do [Azure AD](~/tabs/how-to/authentication/auth-tab-aad.md#navigate-to-the-authorization-page-from-your-popup-page) baseada na Web existente que envolve a aparecendo uma caixa de diálogo de consentimento do Azure AD. Há algumas adições notáveis:

1. O token recuperado usando precisa ser trocado no lado do servidor usando o fluxo em nome do Azure AD para obter acesso a essas `getAuthToken()` APIs adicionais do [](/azure/active-directory/develop/v2-oauth2-on-behalf-of-flow) Microsoft Graph.
    * Certifique-se de usar o ponto de extremidade do Microsoft Graph v2 para este exchange
2. Se a troca falhar, o Azure AD retornará uma exceção de concessão inválida. Geralmente, há uma das duas mensagens de erro: `invalid_grant` ou `interaction_required`
3. Quando a troca falhar, você precisará solicitar consentimento adicional. Recomendamos mostrar alguma interface do usuário solicitando que o usuário conceda consentimento adicional. Essa interface do usuário deve incluir um botão que dispara uma caixa de diálogo de consentimento do Azure AD usando nossa API de autenticação [do Azure AD.](~/concepts/authentication/auth-silent-aad.md)
4. Ao solicitar consentimento adicional do Azure AD, você precisa incluir no parâmetro de cadeia de caracteres de consulta para o Azure AD caso contrário, o Azure AD não solicitará os `prompt=consent` escopos adicionais. [](~/tabs/how-to/authentication/auth-silent-aad.md#get-the-user-context)
    * Em vez de: `?scope={scopes}`
    * Use isso: `?prompt=consent&scope={scopes}`
    * Certifique-se de que isso inclua todos os escopos que você está solicitando ao usuário `{scopes}` (por exemplo: Mail.Read ou User.Read).
5. Depois que o usuário tiver concedido permissão adicional, repetir o on-behalf-of-flow para obter acesso a essas APIs adicionais.

### <a name="non-azure-ad-authentication"></a>Autenticação não Azure AD

A solução de autenticação acima descrita só funciona para aplicativos e serviços que suportam o Azure AD como um provedor de identidade. Os aplicativos que querem autenticar usando serviços baseados no Azure AD precisam continuar usando o fluxo de autenticação da Web baseado em [pop-up.](~/concepts/authentication.md)

> [!NOTE] 
> O SSO é suportado para aplicativos de propriedade do cliente nos locatários do Azure AD B2C.
