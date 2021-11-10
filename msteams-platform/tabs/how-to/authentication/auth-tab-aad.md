---
title: Autenticação para guias usando Azure Active Directory
description: Descreve a autenticação no Teams e como usá-la em guias
ms.topic: how-to
ms.localizationpriority: medium
keywords: guias de autenticação do teams AAD
ms.openlocfilehash: a15d3c78d471bbcc510da019558faa45e3b76241
ms.sourcegitcommit: af1d0a4041ce215e7863ac12c71b6f1fa3e3ba81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2021
ms.locfileid: "60889346"
---
# <a name="authenticate-a-user-in-a-microsoft-teams-tab"></a>Autenticar um usuário em uma Microsoft Teams guia

> [!Note]
> Para que a autenticação funcione para sua guia em clientes móveis, você precisa garantir que esteja usando a versão 1.4.1 ou posterior do SDK do Teams JavaScript.

Há muitos serviços que você pode querer consumir no seu aplicativo Teams, e a maioria desses serviços exige autenticação e autorização para obter acesso ao serviço. Os serviços incluem Facebook, Twitter e Teams. Teams informações de perfil de usuário são armazenadas no Azure Active Directory (Azure AD) usando o Microsoft Graph e este artigo se concentrará na autenticação usando o Azure AD para obter acesso a essas informações.

OAuth 2.0 é um padrão aberto para autenticação usado pelo Azure AD e muitos outros provedores de serviços. Noções básicas sobre o OAuth 2.0 é um pré-requisito para trabalhar com autenticação no Teams e no Azure AD. Os exemplos a seguir usam o fluxo de Concessão Implícita OAuth 2.0 com o objetivo de, eventualmente, ler as informações de perfil do usuário do Azure AD e do Microsoft Graph.

O código neste artigo vem do exemplo Teams exemplo de Microsoft Teams de autenticação de [tabulação (Nó)](https://github.com/OfficeDev/microsoft-teams-sample-complete-node). Ele contém uma guia estática que solicita um token de acesso para o Microsoft Graph e mostra as informações básicas de perfil do usuário atual do Azure AD.

Para uma visão geral do fluxo de autenticação para guias, consulte [Fluxo de autenticação nas guias](~/tabs/how-to/authentication/auth-flow-tab.md).

O fluxo de autenticação nas guias difere ligeiramente do fluxo de autenticação nos bots.

## <a name="configuring-identity-providers"></a>Configurando provedores de identidade

Consulte o tópico [Configure identity providers](~/concepts/authentication/configure-identity-provider.md) for detailed steps on configuring OAuth 2.0 callback redirect URL(s) when using Azure Active Directory as an identity provider.

## <a name="initiate-authentication-flow"></a>Iniciar fluxo de autenticação

O fluxo de autenticação deve ser disparado por uma ação do usuário. Você não deve abrir o pop-up de autenticação automaticamente porque isso provavelmente disparará o bloqueador pop-up do navegador, bem como confundirá o usuário.

Adicione um botão à sua configuração ou página de conteúdo para permitir que o usuário entre quando necessário. Isso pode ser feito na página de configuração [de](~/tabs/how-to/create-tab-pages/configuration-page.md) tabulação ou em qualquer [página de](~/tabs/how-to/create-tab-pages/content-page.md) conteúdo.

O Azure AD, como a maioria dos provedores de identidade, não permite que seu conteúdo seja colocado em um iframe. Isso significa que você precisará adicionar uma página pop-up para hospedar o provedor de identidade. No exemplo a seguir, esta página é `/tab-auth/simple-start` . Use a `microsoftTeams.authenticate()` função do SDK Microsoft Teams cliente para iniciar essa página quando o botão estiver selecionado.

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

* A URL que você passa `microsoftTeams.authentication.authenticate()` é a página inicial do fluxo de autenticação. Neste exemplo, que é `/tab-auth/simple-start` . Isso deve corresponder ao que você registrou no Portal de Registro de Aplicativos [do Azure AD.](https://apps.dev.microsoft.com)

* O fluxo de autenticação deve começar em uma página que está em seu domínio. Esse domínio também deve ser listado [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) na seção do manifesto. A falha ao fazer isso resultará em um pop-up vazio.

* A falha ao usar causará um problema com o pop-up não fechar `microsoftTeams.authentication.authenticate()` no final do processo de login.

## <a name="navigate-to-the-authorization-page-from-your-pop-up-page"></a>Navegue até a página de autorização de sua página pop-up

Quando sua página pop-up ( ) é `/tab-auth/simple-start` exibida, o código a seguir é executado. O principal objetivo desta página é redirecionar para seu provedor de identidade para que o usuário possa entrar. Esse redirecionamento pode ser feito no lado do servidor usando HTTP 302, mas, nesse caso, ele é feito no lado do cliente usando com uma chamada para `window.location.assign()` . Isso também permite ser usado para recuperar informações `microsoftTeams.getContext()` sugestões, que podem ser passadas para o Azure AD.

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

Depois que o usuário concluir a autorização, o usuário será redirecionado para a página de retorno de chamada especificada para seu aplicativo em `/tab-auth/simple-end` .

### <a name="notes"></a>Observações

* Consulte [obter informações de contexto do usuário](~/tabs/how-to/access-teams-context.md) para ajudar a criar solicitações de autenticação e URLs. Por exemplo, você pode usar o nome de logon do usuário como o valor para entrar no Azure AD, o que significa que o usuário pode precisar `login_hint` digitar menos. Lembre-se de que você não deve usar esse contexto diretamente como prova de identidade, pois um invasor pode carregar sua página em um navegador mal-intencionado e fornecer todas as informações que quiser.
* Embora o contexto de tabulação fornece informações úteis sobre o usuário, não use essas informações para autenticar o usuário se você as recebe como parâmetros de URL para a URL de conteúdo da guia ou chamando a função no SDK do cliente `microsoftTeams.getContext()` Microsoft Teams. Um ator mal-intencionado poderia invocar sua URL de conteúdo de tabulação com seus próprios parâmetros, e uma página da Web que representa Microsoft Teams poderia carregar sua URL de conteúdo de tabulação em um iframe e retornar seus próprios dados para a `getContext()` função. Você deve tratar as informações relacionadas à identidade no contexto da guia simplesmente como dicas e validá-las antes de usá-las.
* O parâmetro é usado para confirmar se o serviço que chama o URI de retorno de `state` chamada é o serviço chamado. Se o parâmetro no retorno de chamada não corresponder ao parâmetro enviado durante a chamada, a chamada de retorno não será verificada e `state` deverá ser encerrada.
* Não é necessário incluir o domínio do provedor de identidade na lista no `validDomains` arquivo manifest.json do aplicativo.

## <a name="the-callback-page"></a>A página de retorno de chamada

Na última seção, você chamou o serviço de autorização do Azure AD e passou informações de usuário e aplicativo para que o Azure AD pudesse apresentar ao usuário sua própria experiência de autorização monolítica. Seu aplicativo não tem controle sobre o que acontece nesta experiência. Tudo o que ele sabe é o que é retornado quando o Azure AD chama a página de retorno de chamada que você forneceu ( `/tab-auth/simple-end` ).

Nesta página, você precisa determinar o sucesso ou a falha com base nas informações retornadas pelo Azure AD e chamada `microsoftTeams.authentication.notifySuccess()` ou `microsoftTeams.authentication.notifyFailure()` . Se o logon tiver sido bem-sucedido, você terá acesso aos recursos de serviço.

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

Este código faz uma análise dos pares de valores-chave recebidos do Azure AD ao `window.location.hash` usar a `getHashParameters()` função auxiliar. Se ele encontrar um , e o valor for o mesmo fornecido no início do fluxo de autenticação, ele retornará o token de acesso à guia chamando ; caso contrário, ele relata um erro `access_token` `state` com `notifySuccess()` `notifyFailure()` .

### <a name="notes"></a>Observações

`NotifyFailure()` tem os seguintes motivos de falha predefinidos:

* `CancelledByUser` o usuário fechou a janela pop-up antes de concluir o fluxo de autenticação.
* `FailedToOpenWindow` a janela pop-up não pôde ser aberta. Ao executar Microsoft Teams em um navegador, isso normalmente significa que a janela foi bloqueada por um bloqueador pop-up.

Se tiver êxito, você poderá atualizar ou recarregar a página e mostrar conteúdo relevante para o usuário autenticado. Se a autenticação falhar, ela exibirá uma mensagem de erro.

Seu aplicativo pode definir seu próprio cookie de sessão para que o usuário não precise entrar novamente quando retornar à guia no dispositivo atual.

> [!NOTE]
> O Chrome 80, agendado para lançamento no início de 2020, introduz novos valores de cookie e impõe políticas de cookie por padrão. É recomendável definir o uso pretendido para seus cookies em vez de depender do comportamento padrão do navegador. *Consulte* [o atributo cookie SameSite (atualização 2020)](../../../resources/samesite-cookie-update.md).

>[!NOTE]
>Para obter o token correto para Microsoft Teams usuários gratuitos e convidados, é importante que os aplicativos usem o ponto de extremidade específico do `https://login.microsoftonline.com/**{tenantId}**` locatário. Você pode obter tenantId do contexto de mensagem de bot ou guia. Se os aplicativos usarem , os usuários receberão tokens incorretos e fazer logoff no locatário "home" em vez do locatário no momento em que estão `https://login.microsoftonline.com/common` entrando.

Para obter mais informações sobre o SSO (single Sign-On) consulte o artigo [Autenticação silenciosa](~/tabs/how-to/authentication/auth-silent-AAD.md).

## <a name="code-sample"></a>Exemplo de código

Código de exemplo mostrando o processo de autenticação de tabulação usando o Azure AD:

| **Nome do exemplo** | **description** | **.NET** | **Node.js** |
|-----------------|-----------------|-------------|
| Microsoft Teams autenticação de tabulação | Processo de autenticação de tabulação usando o Azure AD. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-channel-group-config-page-auth/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-auth/nodejs) |

## <a name="see-also"></a>Confira também

* [Planejar a autenticação do usuário](../../../concepts/design/understand-use-cases.md#provide-authentication)
* [Projete sua guia para o Microsoft Teams](~/tabs/design/tabs.md)
* [Autenticação silenciosa](~/tabs/how-to/authentication/auth-silent-aad.md)
* [Adicionar autenticação à sua extensão de mensagens](~/messaging-extensions/how-to/add-authentication.md)
* [Suporte a SSO (login único) para bots](~/bots/how-to/authentication/auth-aad-sso-bots.md)
