---
title: Autenticação silenciosa
description: Descreve autenticação silenciosa, login único, Microsoft Azure Active Directory (Azure AD) para guias
ms.topic: conceptual
ms.localizationpriority: medium
keywords: Guia SSO silencioso Microsoft Azure Active Directory autenticação do teams (Azure AD)
ms.openlocfilehash: 700f0d3f752beb7b09b76a805f2bbcd7adf82fb9
ms.sourcegitcommit: 90587b1ec04bf20d716ed6feb8ccca4313e87f8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/10/2022
ms.locfileid: "62518461"
---
# <a name="silent-authentication"></a>Autenticação silenciosa

> [!IMPORTANT]
> O suporte e desenvolvimento da Microsoft para a Biblioteca de Autenticação do Active Directory (ADAL), incluindo as correções de segurança, termina em 30 de junho de **2022**. Atualize seus aplicativos para usar a Biblioteca de Autenticação da Microsoft (MSAL) para continuar recebendo suporte. Consulte [Migrar aplicativos para a Biblioteca de Autenticação da Microsoft (MSAL)](/azure/active-directory/develop/msal-migration).

> [!NOTE]
> Para que a autenticação funcione para sua guia em clientes móveis, verifique se você está usando Teams JavaScript SDK versão 1.4.1 ou posterior.

A autenticação silenciosa no Microsoft Azure Active Directory (Azure AD) minimiza o número de vezes que um usuário inssure suas credenciais atualize silenciosamente o token de autenticação. Para ver o verdadeiro suporte a um único sign-on, consulte [documentação do SSO](~/tabs/how-to/authentication/auth-aad-sso.md).

Para manter seu código no lado do cliente, use a biblioteca de autenticação Microsoft Azure Active Directory [(Azure AD)](/azure/active-directory/develop/active-directory-authentication-libraries) para JavaScript para obter um token de acesso Microsoft Azure Active Directory (Azure AD) silenciosamente. Se o usuário tiver se assinado recentemente, ele não verá uma caixa de diálogo pop-up.

Embora a Biblioteca de Autenticação do Active Directory seja otimizada para aplicativos AngularJS, ela também funciona com aplicativos de página única (SPA) javaScript.

> [!NOTE]
> Atualmente, a autenticação silenciosa só funciona para guias. Ele não funciona ao entrar de um bot.

## <a name="how-silent-authentication-works"></a>Como funciona a autenticação silenciosa

A Biblioteca de Autenticação do Active Directory cria um iframe oculto para o fluxo implícito de concessão do OAuth 2.0. Mas a biblioteca especifica `prompt=none`, portanto, Microsoft Azure Active Directory (Azure AD)não exibe a página de login. A interação do usuário pode ser necessária se o usuário precisar entrar ou conceder acesso ao aplicativo. Se a interação do usuário for necessária, Microsoft Azure Active Directory (Azure AD) retornará um erro que a biblioteca relata para seu aplicativo. Se necessário, seu aplicativo agora pode exibir uma opção de login.

## <a name="how-to-do-silent-authentication"></a>Como fazer autenticação silenciosa

O código neste artigo vem do aplicativo de exemplo Teams que é [Teams de exemplo de autenticação](https://github.com/OfficeDev/Microsoft-Teams-Samples/blob/main/samples/app-auth/nodejs/src/views/tab/silent/silent.hbs).

Inicie a guia configurável de autenticação silenciosa e simples usando [Microsoft Azure Active Directory (Azure AD)](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-channel-group-config-page-auth/csharp) e siga as instruções para executar o exemplo em seu computador local.

### <a name="include-and-configure-active-directory-authentication-library"></a>Incluir e configurar a Biblioteca de Autenticação do Active Directory

Inclua a Biblioteca de Autenticação do Active Directory em suas páginas de tabulação e configure a biblioteca com a ID do cliente e a URL de redirecionamento:

```html
<script src="https://secure.aadcdn.microsoftonline-p.com/lib/1.0.15/js/adal.min.js" integrity="sha384-lIk8T3uMxKqXQVVfFbiw0K/Nq+kt1P3NtGt/pNexiDby2rKU6xnDY8p16gIwKqgI" crossorigin="anonymous"></script>
<script type="text/javascript">
    // Active Directory Authentication Library configuration
    let config = {
        clientId: "YOUR_APP_ID_HERE",
        // redirectUri must be in the list of redirect URLs for the Microsoft Azure Active Directory (Azure AD) app
        redirectUri: window.location.origin + "/tab-auth/silent-end",
        cacheLocation: "localStorage",
        navigateToLoginRequestUrl: false,
    };
</script>
```

### <a name="get-the-user-context"></a>Obter o contexto do usuário

Na página de conteúdo da guia, chame `microsoftTeams.getContext()` para obter uma dica de login para o usuário atual. A dica é usada como um `loginHint` na chamada para Microsoft Azure Active Directory (Azure AD).

```javascript
// Set up extra query parameters for Active Directory Authentication Library
// - openid and profile scope adds profile information to the id_token
// - login_hint provides the expected user name
if (loginHint) {
    config.extraQueryParameter = "scope=openid+profile&login_hint=" + encodeURIComponent(loginHint);
} else {
    config.extraQueryParameter = "scope=openid+profile";
}
```

### <a name="authenticate"></a>Autenticar

Se a Biblioteca de Autenticação do Active Directory tiver um token não gasto armazenado em cache para o usuário, use o token. Como alternativa, chame `acquireToken(resource, callback)` para receber silenciosamente um token. A biblioteca chama uma função de retorno de chamada com o token solicitado ou gera um erro se a autenticação falhar.

Se você receber um erro na função de retorno de chamada, exibe e use uma opção de login explícita.

```javascript
let authContext = new AuthenticationContext(config); // from Active Directory Authentication Library
// See if there is a cached user and it matches the expected user
let user = authContext.getCachedUser();
if (user) {
    if (user.profile.oid !== userObjectId) {
        // User doesn't match, clear the cache
        authContext.clearCache();
    }
}

// In this example we are getting an id token (which Active Directory Authentication Library returns if we ask for resource = clientId)
authContext.acquireToken(config.clientId, function (errDesc, token, err, tokenType) {
    if (token) {
        // Make sure Active Directory Authentication Library gave us an ID token
        if (tokenType !== authContext.CONSTANTS.ID_TOKEN) {
            token = authContext.getCachedToken(config.clientId);
        }
        showProfileInformation(idToken);
    } else {
        console.log("Renewal failed: " + err);
        // Failed to get the token silently; show the login button
        showLoginButton();
        // You could attempt to launch the login popup here, but in browsers this could be blocked by
        // a popup blocker, in which case the login attempt will fail with the reason FailedToOpenWindow.
    }
});
```

### <a name="process-the-return-value"></a>Processar o valor de retorno

A Biblioteca de Autenticação do Active Directory analisará o resultado do Microsoft Azure Active Directory (Azure AD) `AuthenticationContext.handleWindowCallback(hash)` chamando na página de retorno de chamada de login.

Verifique se você tem um usuário válido e chame `microsoftTeams.authentication.notifySuccess()` ou `microsoftTeams.authentication.notifyFailure()` para relatar o status à página de conteúdo da guia principal.

```javascript
if (authContext.isCallback(window.location.hash)) {
    authContext.handleWindowCallback(window.location.hash);
    if (window.parent === window) {
        if (authContext.getCachedUser()) {
            microsoftTeams.authentication.notifySuccess();
        } else {
            microsoftTeams.authentication.notifyFailure(authContext.getLoginError());
        }
    }
}
```

### <a name="handle-the-sign-out-flow"></a>Manipular o fluxo de saída

Use o código a seguir para manipular o fluxo de saída Microsoft Azure Active Directory autenticação (Azure AD) :

> [!NOTE]
> Quando você faz logout Teams guia ou bot, a sessão atual é desmarcada.

```javascript
function logout() {
localStorage.clear();
window.location.href = "@Url.Action("<<Action Name>>", "<<Controller Name>>")";
}
```

## <a name="see-also"></a>Confira também

* [Configurar provedores de identidade para usar Microsoft Azure Active Directory (Azure AD)](../../../concepts/authentication/configure-identity-provider.md)
* [Saiba mais sobre a Biblioteca de Autenticação da Microsoft (MSAL)](/azure/active-directory/develop/msal-overview)
