---
title: Configurar a autenticação OAuth de terceiros
description: Neste artigo, saiba mais sobre Teams de autenticação Microsoft Azure AD, autenticação no Teams e como usá-la em guias.
ms.topic: how-to
ms.localizationpriority: medium
ms.openlocfilehash: 12146d5651fa0e975dcfdd7f60159700e1f8914e
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66142266"
---
# <a name="configure-third-party-oauth-authentication"></a>Configurar a autenticação OAuth de terceiros

> [!Note]
> Para que a autenticação funcione para sua guia em clientes móveis, verifique se você está usando a versão 1.4.1 ou posterior do SDK Teams JavaScript.

Existem muitos serviços que você pode querer consumir dentro do seu aplicativo do Teams, e a maioria desses serviços exige autenticação e autorização para obter acesso ao serviço. Os serviços incluem Facebook, Twitter e Teams.
As informações de perfil do usuário do Teams são armazenadas no Azure AD usando o Microsoft Graph e este artigo se concentrará na autenticação usando o Microsoft Azure AD para obter acesso a essas informações.

OAuth 2.0 é um padrão aberto para autenticação usado pelo Microsoft Azure AD e muitos outros provedores de serviços. Entender o OAuth 2.0 é um pré-requisito para trabalhar com autenticação no Teams e no Microsoft Azure AD. Os exemplos a seguir usam o fluxo de Concessão Implícita do OAuth 2.0. Ele lê as informações de perfil do usuário do Azure AD e do Microsoft Graph.

O código neste artigo vem do aplicativo de exemplo do Teams [Exemplo de autenticação da guia do Microsoft Teams (Node)](https://github.com/OfficeDev/microsoft-teams-sample-complete-node). Ele contém uma guia estática que solicita um token de acesso para o Microsoft Graph e mostra as informações básicas de perfil do usuário atual do Azure AD.

Para obter uma visão geral do fluxo de autenticação para guias, consulte [o fluxo de autenticação nas guias](~/tabs/how-to/authentication/auth-flow-tab.md).

O fluxo de autenticação em guias difere do fluxo de autenticação em bots.

## <a name="configure-your-app-to-use-azure-ad-as-an-identity-provider"></a>Configurar seu aplicativo para usar Azure AD como um provedor de identidade

Os provedores de identidade que dão suporte ao OAuth 2.0 não autenticam solicitações de aplicativos desconhecidos. Você deve registrar os aplicativos com antecedência. Para fazer isso com o Azure AD, siga estas etapas:

1. Abra o [Portal de Registro do Aplicativo](https://ms.portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade).

2. Selecione seu aplicativo para exibir suas propriedades ou selecione o botão "Novo Registro". Localize a seção **URI de direcionamento** para o aplicativo.

3. Selecione **Web** no menu suspenso. Atualize a URL para o ponto de extremidade de autenticação. Para os aplicativos de exemplo TypeScript/Node.js e C# no GitHub, as URLs de redirecionamento serão semelhantes ao seguinte:

    URLs de redirecionamento: `https://<hostname>/bot-auth/simple-start`

Substitua `<hostname>` pelo host real. Esse host pode ser um site de hospedagem dedicado, como o Azure, o Glitch ou um túnel ngrok para o localhost em seu computador de desenvolvimento, como `abcd1234.ngrok.io`. Se você não tiver essas informações, verifique se você concluiu ou hospedou seu aplicativo (ou o aplicativo de exemplo). Retome esse processo quando tiver essas informações.

> [!NOTE]
> Você pode escolher qualquer provedor OAuth de terceiros, como LinkedIn, Google e outros. O processo para habilitar a autenticação para esses provedores é semelhante ao uso Azure AD provedor OAuth de terceiros. Para obter mais informações sobre como usar qualquer provedor OAuth de terceiros, visite o site do provedor específico.

## <a name="initiate-authentication-flow"></a>Iniciar o fluxo de autenticação

O fluxo de autenticação deve ser disparado por uma ação do usuário. Você não deve abrir o pop-up de autenticação automaticamente porque isso provavelmente disparará o bloqueador pop-up do navegador e confundirá o usuário.

Adicione um botão à sua configuração ou página de conteúdo para habilitar o usuário a entrar quando necessário. Isso pode ser feito na guia da página de [configuração](~/tabs/how-to/create-tab-pages/configuration-page.md) ou em qualquer página de [conteúdo](~/tabs/how-to/create-tab-pages/content-page.md).

Azure AD, como a maioria dos provedores de identidade, não permite que seu conteúdo seja colocado em um `iframe`. Isso significa que você precisará adicionar uma página pop-up para hospedar o provedor de identidade. No exemplo a seguir, esta página é `/tab-auth/simple-start`. Use a `microsoftTeams.authenticate()` função do SDK do Microsoft Teams cliente para iniciar esta página quando o botão for selecionado.

```javascript
microsoftTeams.authentication.authenticate({
    url: window.location.origin + "/tab-auth/simple-start",
    width: 600,
    height: 535,
    successCallback: function (result) {
        getUserProfile(result.accessToken);
    },
    failureCallback: function (reason) {
        handleAuthError(reason);
    }
});
```

### <a name="notes"></a>Observações

* O URL que você passa para `microsoftTeams.authentication.authenticate()` é a página inicial do fluxo de autenticação. Neste exemplo que é `/tab-auth/simple-start`. Isso deve corresponder ao que você registrou no [Portal de Registro de Aplicativos do Microsoft Azure AD](https://apps.dev.microsoft.com).

* O fluxo de autenticação deve começar em uma página que esteja no seu domínio. Este domínio também deve ser listado na seção [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) do manifesto. Não fazer isso resultará em um pop-up vazio.

* Não usar causará `microsoftTeams.authentication.authenticate()` um problema com o pop-up não fechar no final do processo de entrada.

## <a name="navigate-to-the-authorization-page-from-your-pop-up-page"></a>Navegue até a página de autorização da sua página pop-up

Quando sua página pop-up (`/tab-auth/simple-start`) for exibida, o seguinte código será executado. O principal objetivo desta página é redirecionar para seu provedor de identidade para que o usuário possa entrar. Esse redirecionamento pode ser feito no lado do servidor usando HTTP 302, mas, nesse caso, é feito no lado do cliente usando com uma chamada para `window.location.assign()`. Isso também permite que `microsoftTeams.getContext()` seja usado para recuperar informações de dicas, que podem ser passadas para o Microsoft Azure AD.

```javascript
microsoftTeams.getContext(function (context) {
    // Generate random state string and store it, so we can verify it in the callback
    let state = _guid(); // _guid() is a helper function in the sample
    localStorage.setItem("simple.state", state);
    localStorage.removeItem("simple.error");
    // Go to the Azure AD authorization endpoint
    let queryParams = {
        client_id: "YOUR_APP_ID_HERE",
        response_type: "id_token token",
        response_mode: "fragment",
        scope: "https://graph.microsoft.com/User.Read openid",
        redirect_uri: window.location.origin + "/tab-auth/simple-end",
        nonce: _guid(),
        state: state,
        // The context object is populated by Teams; the loginHint attribute
         // is used as hinting information
        login_hint: context.loginHint,
    };

    let authorizeEndpoint = "https://login.microsoftonline.com/" + context.tid + "/oauth2/v2.0/authorize?" + toQueryString(queryParams);
    window.location.assign(authorizeEndpoint);
});
```

Depois que o usuário concluir a autorização, ele será redirecionado para a página de retorno de chamada que você especificou para seu aplicativo em `/tab-auth/simple-end`.

### <a name="notes"></a>Observações

* Consulte [obter as informações de contexto do usuário](~/tabs/how-to/access-teams-context.md) para obter ajuda para criar solicitações de autenticação e URLs. Por exemplo, você pode usar o nome de logon do usuário como o valor `login_hint` para entrar no Microsoft Azure AD, o que significa que o usuário talvez precise digitar menos. Lembre-se de que você não deve usar esse contexto diretamente como prova de identidade, pois um invasor pode carregar sua página em um navegador mal-intencionado e fornecer as informações desejadas.
* Embora o contexto da guia forneça informações úteis sobre o usuário, não use essas informações para autenticar o usuário, quer você as obtenha como parâmetros de URL para seu URL de conteúdo da guia ou chamando a função `microsoftTeams.getContext()` no SDK do cliente do Microsoft Teams. Um ator mal-intencionado pode invocar o URL do conteúdo da guia com seus próprios parâmetros, e uma página da Web que representa o Microsoft Teams pode carregar o URL do conteúdo da guia em um iframe e retornar seus próprios dados para a função `getContext()`. Você deve tratar as informações relacionadas à identidade no contexto da guia simplesmente como dicas e validá-las antes de usá-las.
* O parâmetro `state` é utilizado para confirmar que o serviço que chama o URI de retorno de chamada é o serviço que você chamou. Se o `state` parâmetro no retorno de chamada não corresponder ao parâmetro enviado durante a chamada, a chamada de retorno não será verificada e deverá ser encerrada.
* Não é necessário incluir o domínio do provedor de identidade `validDomains` na lista no arquivo manifest.json do aplicativo.

## <a name="the-callback-page"></a>A página de retorno de chamada

Na última seção, você chamou o serviço de autorização do Azure AD e passou informações de usuário e aplicativo para que Azure AD pudesse apresentar ao usuário sua própria experiência de autorização monolítica. Seu aplicativo não tem controle sobre o que acontece nesta experiência. Tudo o que ele sabe é o que é retornado quando o Microsoft Azure AD chama a página de retorno de chamada que você forneceu (`/tab-auth/simple-end`).

Nesta página, você precisa determinar o êxito ou a falha com base nas informações retornadas por Azure AD e chamada `microsoftTeams.authentication.notifySuccess()` ou `microsoftTeams.authentication.notifyFailure()`. Se o logon for bem-sucedido, você terá acesso aos recursos de serviço.

````javascript
// Split the key-value pairs passed from Azure AD
// getHashParameters is a helper function that parses the arguments sent
// to the callback URL by Azure AD after the authorization call
let hashParams = getHashParameters();
if (hashParams["error"]) {
    // Authentication/authorization failed
    microsoftTeams.authentication.notifyFailure(hashParams["error"]);
} else if (hashParams["access_token"]) {
    // Get the stored state parameter and compare with incoming state
    // This validates that the data is coming from Azure AD
    let expectedState = localStorage.getItem("simple.state");
    if (expectedState !== hashParams["state"]) {
        // State does not match, report error
        microsoftTeams.authentication.notifyFailure("StateDoesNotMatch");
    } else {
        // Success: return token information to the tab
        microsoftTeams.authentication.notifySuccess({
            idToken: hashParams["id_token"],
            accessToken: hashParams["access_token"],
            tokenType: hashParams["token_type"],
            expiresIn: hashParams["expires_in"]
        })
    }
} else {
    // Unexpected condition: hash does not contain error or access_token parameter
    microsoftTeams.authentication.notifyFailure("UnexpectedFailure");
}
````

Este código analisa os pares de chave-valor recebidos do Microsoft Azure AD em `window.location.hash` usando a função auxiliar `getHashParameters()`. Se encontrar um `access_token` e o valor `state` for o mesmo que o fornecido no início do fluxo de autenticação, ele retornará o token de acesso para a guia chamando `notifySuccess()`; caso contrário, ele relatará um erro com `notifyFailure()`.

### <a name="notes"></a>Observações

`NotifyFailure()` tem os seguintes motivos de falha predefinidos:

* `CancelledByUser` o usuário fechou a janela pop-up antes de concluir o fluxo de autenticação.
* `FailedToOpenWindow` não foi possível abrir a janela pop-up. Ao executar o Microsoft Teams em um navegador, isso geralmente significa que a janela foi bloqueada por um bloqueador de pop-ups.

Se for bem-sucedido, você poderá atualizar ou recarregar a página e mostrar conteúdos relevantes para o usuário agora autenticado. Se a autenticação falhar, ela exibirá uma mensagem de erro.

Seu aplicativo pode definir seu próprio cookie de sessão para que o usuário não precise entrar novamente quando retornar à sua guia no dispositivo atual.

> [!NOTE]
>
> * O Chrome 80, agendado para lançamento no início de 2020, apresenta novos valores de cookie e impõe políticas de cookie por padrão. É recomendável que você defina o uso pretendido para seus cookies em vez de depender do comportamento padrão do navegador. *Consulte* [Atributos do cookie SameSite (atualização de 2020)](../../../resources/samesite-cookie-update.md).
> * Para obter o token correto para os usuários convidados do Microsoft Teams Gratuito, é importante que os aplicativos utilizem o ponto de extremidade específico do locatário `https://login.microsoftonline.com/**{tenantId}**`. Você pode obter a TenantID na mensagem do bot ou no contexto da guia. Se os aplicativos usarem `https://login.microsoftonline.com/common`, os usuários receberão tokens incorretos e farão logon no locatário "inicial" em vez do locatário em que estão conectados no momento.

Para obter mais informações sobre o SSO (Sign-On único), consulte o artigo [Autenticação silenciosa](~/tabs/how-to/authentication/auth-silent-AAD.md).

## <a name="code-sample"></a>Exemplo de código

Exemplo de código que mostra o processo de autenticação de guias usando o Microsoft Azure AD:

| **Nome de exemplo** | **description** | **.NET** | **Node.js** |
|-----------------|-----------------|-------------|
| Autenticação da guia do Microsoft Teams | Processo de autenticação de guias usando o Microsoft Azure AD. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-channel-group-config-page-auth/csharp) | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-auth/nodejs) |

## <a name="see-also"></a>Confira também

* [Planejar a autenticação do usuário](../../../concepts/design/understand-use-cases.md)
* [Projete sua guia para o Microsoft Teams](~/tabs/design/tabs.md)
* [Autenticação silenciosa](~/tabs/how-to/authentication/auth-silent-aad.md)
* [Adicionar autenticação à sua extensão de mensagens](~/messaging-extensions/how-to/add-authentication.md)
* [Suporte de Logon Único (SSO) para bots](~/bots/how-to/authentication/auth-aad-sso-bots.md)
