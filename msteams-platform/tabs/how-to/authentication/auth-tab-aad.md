---
title: Autenticação para guias usando o Azure Active Directory
description: Descreve a autenticação no Teams e como usá-la nas guias
keywords: guias de autenticação do Teams AAD
ms.openlocfilehash: f6df2dbf84583488ddc0c57798d423b6288af16d
ms.sourcegitcommit: 23ceb25d07a76f03ffe92cf1ac578b7c50b0bafc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2021
ms.locfileid: "49777928"
---
# <a name="authenticate-a-user-in-a-microsoft-teams-tab"></a>Autenticar um usuário em uma guia do Microsoft Teams

> [!Note]
> Para que a autenticação funcione para sua guia em clientes móveis, você precisa garantir que esteja usando a versão 1.4.1 ou posterior do SDK JavaScript do Teams.

Há muitos serviços que você pode querer consumir dentro de seu aplicativo do Teams, e a maioria desses serviços exige autenticação e autorização para obter acesso ao serviço. Os serviços incluem o Facebook, o Twitter e, claro, o Teams. Os usuários do Teams têm informações de perfil de usuário armazenadas no Azure Active Directory (Azure AD) usando o Microsoft Graph e este artigo se concentrará na autenticação usando o Azure AD para obter acesso a essas informações.

O OAuth 2.0 é um padrão aberto para autenticação usado pelo Azure AD e muitos outros provedores de serviços. Compreender o OAuth 2.0 é um pré-requisito para trabalhar com autenticação no Teams e no Azure AD. Os exemplos a seguir usam o fluxo de Concessão Implícita do OAuth 2.0 com o objetivo de, eventualmente, ler as informações de perfil do usuário do Azure AD e do Microsoft Graph.

O código neste artigo vem do exemplo de autenticação de [guia do Microsoft Teams (Node)](https://github.com/OfficeDev/microsoft-teams-sample-complete-node). Ela contém uma guia estática que solicita um token de acesso para o Microsoft Graph e mostra as informações de perfil básicas do usuário atual do Azure AD.

Para uma visão geral do fluxo de autenticação para guias, consulte o tópico [Fluxo de autenticação nas guias.](~/tabs/how-to/authentication/auth-flow-tab.md)

O fluxo de autenticação nas guias difere ligeiramente do fluxo de autenticação em bots.

## <a name="configuring-identity-providers"></a>Configurando provedores de identidade

Consulte o tópico Configurar provedores de identidade para etapas [detalhadas](~/concepts/authentication/configure-identity-provider.md) de configuração de URLs de redirecionamento de retorno de chamada do OAuth 2.0 ao usar o Azure Active Directory como um provedor de identidade.

## <a name="initiate-authentication-flow"></a>Iniciar fluxo de autenticação

O fluxo de autenticação deve ser disparado por uma ação do usuário. Você não deve abrir o pop-up de autenticação automaticamente porque isso provavelmente disparará o bloqueador de pop-ups do navegador, além de confundir o usuário.

Adicione um botão à sua página de configuração ou conteúdo para permitir que o usuário entre quando necessário. Isso pode ser feito na página de [configuração da](~/tabs/how-to/create-tab-pages/configuration-page.md) guia ou em qualquer [página de](~/tabs/how-to/create-tab-pages/content-page.md) conteúdo.

O Azure AD, como a maioria dos provedores de identidade, não permite que seu conteúdo seja colocado em um iframe. Isso significa que você precisará adicionar uma página pop-up para hospedar o provedor de identidade. No exemplo a seguir, esta página é `/tab-auth/simple-start` . Use a função do SDK do cliente Microsoft Teams para iniciar `microsoftTeams.authenticate()` esta página quando o botão estiver selecionado.

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

* A URL que você passa é `microsoftTeams.authentication.authenticate()` a página inicial do fluxo de autenticação. Neste exemplo, que é `/tab-auth/simple-start` . Isso deve corresponder ao que você registrou no Portal de Registro de [Aplicativos do Azure AD.](https://apps.dev.microsoft.com)

* O fluxo de autenticação deve iniciar em uma página que está em seu domínio. Esse domínio também deve estar listado [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) na seção do manifesto. Não fazer isso resultará em um pop-up vazio.

* Não usar `microsoftTeams.authentication.authenticate()` causará um problema com o pop-up não fechar no final do processo de login.

## <a name="navigate-to-the-authorization-page-from-your-popup-page"></a>Navegue até a página de autorização em sua página pop-up

Quando sua página pop-up ( ) é `/tab-auth/simple-start` exibida, o código a seguir é executado. O principal objetivo desta página é redirecionar para seu provedor de identidade para que o usuário possa entrar. Esse redirecionamento pode ser feito no lado do servidor usando HTTP 302, mas nesse caso é feito no lado do cliente usando com uma chamada para `window.location.assign()` . Isso também permite ser usado para recuperar informações de dicas que `microsoftTeams.getContext()` podem ser passadas para o Azure AD.

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

Depois que o usuário concluir a autorização, o usuário será redirecionado para a página de retorno de chamada que você especificou para seu aplicativo em `/tab-auth/simple-end` .

### <a name="notes"></a>Observações

* Consulte [obter informações de contexto do usuário para](~/tabs/how-to/access-teams-context.md) obter ajuda na criação de solicitações de autenticação e URLs. Por exemplo, você pode usar o nome de logon do usuário como o valor para entrar no Azure AD, o que significa que o usuário pode precisar `login_hint` digitar menos. Lembre-se de que você não deve usar esse contexto diretamente como prova de identidade, pois um invasor pode carregar sua página em um navegador mal-intencionado e fornecer as informações que quiser.
* Embora o contexto de guia fornece informações úteis sobre o usuário, não use essas informações para autenticar o usuário se você as recebe como parâmetros de URL para a URL de conteúdo da guia ou chamando a função no SDK do cliente `microsoftTeams.getContext()` do Microsoft Teams. Um ator mal-intencionado pode invocar a URL do conteúdo da guia com seus próprios parâmetros, e uma página da Web que representa o Microsoft Teams pode carregar a URL do conteúdo da guia em um iframe e retornar seus próprios dados para a `getContext()` função. Você deve tratar as informações relacionadas à identidade no contexto de guia simplesmente como dicas e validá-las antes de usá-las.
* O parâmetro é usado para confirmar se o serviço que está chamando o URI de `state` retorno de chamada é o serviço que você chamou. Se o parâmetro no retorno de chamada não corresponder ao parâmetro enviado durante a chamada, a chamada de retorno não será verificada e `state` deverá ser encerrada.
* Não é necessário incluir o domínio do provedor de identidade na lista no arquivo manifest.js`validDomains` no aplicativo.

## <a name="the-callback-page"></a>A página de retorno de chamada

Na última seção, você chamou o serviço de autorização do Azure AD e passou informações de usuário e aplicativo para que o Azure AD pudesse apresentar ao usuário sua própria experiência de autorização monolítica. Seu aplicativo não tem controle sobre o que acontece nessa experiência. Tudo o que ele sabe é o que é retornado quando o Azure AD chama a página de retorno de chamada que você forneceu ( `/tab-auth/simple-end` ).

Nesta página, você precisa determinar o sucesso ou a falha com base nas informações retornadas pelo Azure AD e na chamada `microsoftTeams.authentication.notifySuccess()` ou `microsoftTeams.authentication.notifyFailure()` . Se o logon for bem-sucedido, você terá acesso aos recursos de serviço.

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

Este código analisará os pares chave-valor recebidos do Azure AD usando `window.location.hash` a `getHashParameters()` função auxiliar. Se encontrar um , e o valor for o mesmo fornecido no início do fluxo de autenticação, ele retornará o token de acesso para a guia chamando; caso contrário, ele relata um `access_token` `state` erro com `notifySuccess()` `notifyFailure()` .

### <a name="notes"></a>Observações

`NotifyFailure()` tem os seguintes motivos de falha predefinidos:

* `CancelledByUser` o usuário fechou a janela pop-up antes de concluir o fluxo de autenticação.
* `FailedToOpenWindow` não foi possível abrir a janela pop-up. Ao executar o Microsoft Teams em um navegador, isso geralmente significa que a janela foi bloqueada por um bloqueador de pop-ups.

Se bem-sucedido, você pode atualizar ou recarregar a página e mostrar o conteúdo relevante para o usuário autenticado agora. Se a autenticação falhar, exibirá uma mensagem de erro.

Seu aplicativo pode definir seu próprio cookie de sessão para que o usuário não precise entrar novamente quando retornar à guia no dispositivo atual.

> [!NOTE]
> O Chrome 80, agendado para lançamento no início de 2020, apresenta novos valores de cookie e impõe políticas de cookie por padrão. É recomendável definir o uso pretendido para seus cookies em vez de depender do comportamento padrão do navegador. *Veja* [o atributo de cookie SameSite (atualização de 2020).](../../../resources/samesite-cookie-update.md)

>[!NOTE]
>Para obter o token correto para usuários convidados e gratuitos do Microsoft Teams, é importante que os aplicativos usem o ponto de extremidade específico do https://login.microsoftonline.com/ **locatário {tenantId}**. Você pode obter tenantId no contexto de guia ou mensagem de bot. Se os aplicativos usarem, os usuários receberão tokens incorretos e entrarão no locatário "home" em vez do locatário em que estão https://login.microsoftonline.com/common atualmente assinados.

Para obter mais informações sobre o Sign-On único (SSO), consulte o artigo [Autenticação silenciosa.](~/tabs/how-to/authentication/auth-silent-AAD.md)

## <a name="samples"></a>Exemplos

Para ver o código de exemplo mostrando o processo de autenticação de guia usando o Azure AD, confira:

* [Exemplo de autenticação de guia do Microsoft Teams (Nó)](https://github.com/OfficeDev/microsoft-teams-sample-auth-node)
