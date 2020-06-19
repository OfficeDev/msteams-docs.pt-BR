---
title: Autenticação para guias usando o Azure Active Directory
description: Descreve a autenticação no Microsoft Teams e como usá-la em guias
keywords: AAD de guias de autenticação de equipes
ms.openlocfilehash: 211c08ce1a51a8f0f13e622856a808661dc97b39
ms.sourcegitcommit: fdcd91b270d4c2e98ab2b2c1029c76c49bb807fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "44800965"
---
# <a name="authenticate-a-user-in-a-microsoft-teams-tab"></a>Autenticar um usuário em uma guia do Microsoft Teams

> [!Note]
> Para que a autenticação funcione para sua guia em clientes móveis, é necessário garantir que você esteja usando a versão 1.4.1 ou posterior do SDK do Microsoft Teams JavaScript.

Há muitos serviços que você pode desejar usar dentro do seu aplicativo do Microsoft Teams e a maioria desses serviços requer autenticação e autorização para obter acesso ao serviço. Os serviços incluem o Facebook, o Twitter e o Microsoft Teams. Os usuários de Teams têm informações de perfil de usuário armazenadas no Azure Active Directory (Azure AD) usando o Microsoft Graph, e este artigo se concentrará na autenticação usando o Azure AD para obter acesso a essas informações.

O OAuth 2,0 é um padrão aberto para autenticação usada pelo Azure AD e muitos outros provedores de serviços. A compreensão do OAuth 2,0 é um pré-requisito para trabalhar com autenticação no Teams e no Azure AD. Os exemplos abaixo usam o fluxo de concessão implícita do OAuth 2,0 com o objetivo de eventualmente ler as informações de perfil do usuário do Azure AD e do Microsoft Graph.

O código deste artigo vem do exemplo de aplicativo de exemplo do [Microsoft Teams de autenticação de guia do Microsoft Teams (nó)](https://github.com/OfficeDev/microsoft-teams-sample-complete-node). Ele contém uma guia estática que solicita um token de acesso para o Microsoft Graph e mostra as informações do perfil básico do usuário atual do Azure AD.

Para obter uma visão geral do fluxo de autenticação para guias, consulte o tópico [fluxo de autenticação em guias](~/tabs/how-to/authentication/auth-flow-tab.md).

O fluxo de autenticação em guias difere ligeiramente do fluxo de autenticação em bots.

## <a name="configuring-identity-providers"></a>Configurando provedores de identidade

Consulte o tópico [Configure Identity Providers](~/concepts/authentication/configure-identity-provider.md) para obter etapas detalhadas sobre como configurar URLs de redirecionamento de retorno de chamada OAuth 2,0 ao usar o Azure Active Directory como um provedor de identidade.

## <a name="initiate-authentication-flow"></a>Iniciar o fluxo de autenticação

O fluxo de autenticação deve ser acionado por uma ação do usuário. Você não deve abrir o pop-up de autenticação automaticamente porque isso provavelmente disparará o bloqueador de pop-ups do navegador, além de confundir o usuário.

Adicione um botão à sua página de configuração ou conteúdo para permitir que o usuário entre quando necessário. Isso pode ser feito na página [configuração](~/tabs/how-to/create-tab-pages/configuration-page.md) da guia ou em qualquer página de [conteúdo](~/tabs/how-to/create-tab-pages/content-page.md) .

O Azure AD, como a maioria dos provedores de identidade, não permite que seu conteúdo seja colocado em um iframe. Isso significa que você precisará adicionar uma página pop-up para hospedar o provedor de identidade. No exemplo a seguir, esta página é `/tab-auth/simple-start` . Use a `microsoftTeams.authenticate()` função do Microsoft Teams Client SDK para iniciar esta página quando seu botão estiver selecionado.

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

* A URL para a qual você passa `microsoftTeams.authentication.authenticate()` é a página inicial do fluxo de autenticação. Neste exemplo `/tab-auth/simple-start` . Isso deve corresponder ao que você registrou no [portal de registro de aplicativo do Azure ad](https://apps.dev.microsoft.com).

* O fluxo de autenticação deve começar em uma página que está no seu domínio. Esse domínio também deve ser listado na [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) seção do manifesto. Se isso não for feito, resultará em um pop-up vazio.

* A não utilização causará `microsoftTeams.authentication.authenticate()` um problema com o pop-up que não está fechando no final do processo de entrada.

## <a name="navigate-to-the-authorization-page-from-your-popup-page"></a>Navegue até a página autorização na página pop-up

Quando a página pop-up ( `/tab-auth/simple-start` ) é exibida, o código a seguir é executado. O objetivo principal desta página é redirecionar para seu provedor de identidade para que o usuário possa entrar. Esse redirecionamento pode ser feito no lado do servidor usando HTTP 302, mas, nesse caso, é feito no lado do cliente usando uma chamada para `window.location.assign()` . Isso também permite que `microsoftTeams.getContext()` seja usado para recuperar informações de dicas que podem ser passadas para o Azure AD.

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
        resource: "https://graph.microsoft.com/User.Read openid",
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

* Consulte [obter informações de contexto de usuário](~/tabs/how-to/access-teams-context.md) para ajudar a criar solicitações de autenticação e URLs. Por exemplo, você pode usar o nome de logon do usuário como o `login_hint` valor para a entrada do Azure AD, o que significa que o usuário pode precisar digitar menos. Lembre-se de que você não deve usar esse contexto diretamente como prova de identidade, uma vez que um invasor pode carregar sua página em um navegador mal-intencionado e fornecer qualquer informação que desejar.
* Embora o contexto de tabulação forneça informações úteis sobre o usuário, não use essas informações para autenticar o usuário se você o recebe como parâmetros de URL para a URL de conteúdo da sua guia ou chamando a `microsoftTeams.getContext()` função no SDK do cliente do Microsoft Teams. Um ator mal-intencionado pode invocar a URL de conteúdo da guia com seus próprios parâmetros, e uma página da Web representando o Microsoft Teams pode carregar sua URL de conteúdo de tabulação em um iframe e retornar seus próprios dados para a `getContext()` função. Você deve tratar as informações relacionadas à identidade no contexto da guia simplesmente como dicas e validá-las antes de usar.
* O `state` parâmetro é usado para confirmar se o serviço que está chamando o URI de retorno de chamada é o serviço que você chamou. Se o `state` parâmetro no retorno de chamada não corresponder ao parâmetro que você enviou durante a chamada, a chamada de retorno não é verificada e deve ser encerrada.
* Não é necessário incluir o domínio do provedor de identidade na `validDomains` lista na manifest.jsdo aplicativo no arquivo.

## <a name="the-callback-page"></a>A página de retorno de chamada

Na última seção que você chamou o serviço de autorização do Azure AD e passou as informações do usuário e do aplicativo para que o Azure AD possa apresentar ao usuário sua própria experiência de autorização monolítica. Seu aplicativo não tem controle sobre o que acontece nesta experiência. Tudo o que ele sabe é o que é retornado quando o Azure AD chama a página de retorno de chamada fornecida ( `/tab-auth/simple-end` ).

Nesta página, você precisa determinar o sucesso ou a falha com base nas informações retornadas pelo Azure AD e Call `microsoftTeams.authentication.notifySuccess()` ou `microsoftTeams.authentication.notifyFailure()` . Se o logon tiver sido bem-sucedido, você terá acesso a recursos de serviço.

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

Este código analisa os pares chave-valor recebidos do Azure AD `window.location.hash` usando a `getHashParameters()` função auxiliar. Se encontrar um `access_token` , e o `state` valor for igual ao fornecido no início do fluxo de autenticação, ele retornará o token de acesso à guia chamando `notifySuccess()` ; caso contrário, ele informa um erro com `notifyFailure()` .

### <a name="notes"></a>Observações

`NotifyFailure()`o tem os seguintes motivos de falha predefinidos:

* `CancelledByUser`o usuário fechou a janela pop-up antes de concluir o fluxo de autenticação.
* `FailedToOpenWindow`Não foi possível abrir a janela pop-up. Ao executar o Microsoft Teams em um navegador, isso normalmente significa que a janela foi bloqueada por um bloqueador de pop-up.

Se tiver êxito, você poderá atualizar ou recarregar a página e mostrar o conteúdo relevante para o usuário autenticado agora. Se a autenticação falhar, exiba uma mensagem de erro.

Seu aplicativo pode definir seu próprio cookie de sessão para que o usuário não precise entrar novamente quando retornar à sua guia no dispositivo atual.

> [!NOTE]
> O Chrome 80, agendado para lançamento no início de 2020, apresenta novos valores de cookie e impõe políticas de cookies por padrão. É recomendável que você defina o uso pretendido para seus cookies, em vez de confiar no comportamento padrão do navegador. *Confira* o [atributo SameSite cookie (atualização 2020)](../../../resources/samesite-cookie-update.md).

Para obter mais informações sobre logon único (SSO), confira o artigo [autenticação silenciosa](~/tabs/how-to/authentication/auth-silent-AAD.md).

## <a name="samples"></a>Exemplos

Para obter um exemplo de código mostrando o processo de autenticação de guia usando o Azure AD, confira:

* [Exemplo de autenticação de guia do Microsoft Teams (nó)](https://github.com/OfficeDev/microsoft-teams-sample-auth-node)
