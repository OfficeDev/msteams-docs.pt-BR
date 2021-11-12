---
title: Autenticação silenciosa
description: Descreve autenticação silenciosa, login único, Azure Active Directory para guias
ms.topic: conceptual
ms.localizationpriority: medium
keywords: Autenticação do teams SSO AAD guia
ms.openlocfilehash: e5e8de1878aaec29c8ae1cd8dc1350a110d38b5e
ms.sourcegitcommit: 1431dfe08d5a19a63dbf1542a2e6c661e4dd7fc1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2021
ms.locfileid: "60949044"
---
# <a name="silent-authentication"></a>Autenticação silenciosa

> [!NOTE]
> Para que a autenticação funcione para sua guia em clientes móveis, verifique se você está usando pelo menos a versão 1.4.1 do SDK do Teams JavaScript.

A autenticação silenciosa no Azure Active Directory (AAD) minimiza o número de vezes que um usuário inssinge suas credenciais de entrada atualize silenciosamente o token de autenticação. Para ver o suporte verdadeiro ao login único, consulte [documentação do SSO](~/tabs/how-to/authentication/auth-aad-sso.md).

Se você quiser manter seu código completamente no lado do cliente, você pode usar [a](/azure/active-directory/develop/active-directory-authentication-libraries) biblioteca de autenticação AAD para JavaScript para obter um token de AAD de acesso silenciosamente. Se o usuário tiver se assinado recentemente, ele nunca verá uma caixa de diálogo pop-up.

Embora a biblioteca ADAL.js seja otimizada para aplicativos AngularJS, ela também funciona com aplicativos de página única JavaScript puros.

> [!NOTE]
> Atualmente, a autenticação silenciosa só funciona para guias. Ele não funciona ao entrar de um bot.

## <a name="how-silent-authentication-works"></a>Como funciona a autenticação silenciosa

A ADAL.js cria um iframe oculto para o fluxo implícito de concessão do OAuth 2.0. Mas a biblioteca especifica `prompt=none` , portanto, o Azure AD nunca mostra a página de logom. Se a interação do usuário for necessária porque o usuário precisa entrar ou conceder acesso ao aplicativo, AAD retornará imediatamente um erro que ADAL.js para seu aplicativo. Neste ponto, seu aplicativo pode mostrar um botão de login, se necessário.

## <a name="how-to-do-silent-authentication"></a>Como fazer autenticação silenciosa

O código neste artigo vem do aplicativo de exemplo Teams que é [Teams de autenticação.](https://github.com/OfficeDev/Microsoft-Teams-Samples/blob/main/samples/app-auth/nodejs/src/views/tab/silent/silent.hbs)

[Inicie a guia configurável de](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-channel-group-config-page-auth/csharp) autenticação silenciosa e simples usando AAD e siga as instruções para executar o exemplo em seu computador local.

### <a name="include-and-configure-adal"></a>Incluir e configurar o ADAL

Inclua a ADAL.js em suas páginas de tabulação e configure o ADAL com a ID do cliente e a URL de redirecionamento:

```html
<script src="https://secure.aadcdn.microsoftonline-p.com/lib/1.0.15/js/adal.min.js" integrity="sha384-lIk8T3uMxKqXQVVfFbiw0K/Nq+kt1P3NtGt/pNexiDby2rKU6xnDY8p16gIwKqgI" crossorigin="anonymous"></script>
<script type="text/javascript">
    // ADAL.js configuration
    let config = {
        clientId: "YOUR_APP_ID_HERE",
        // redirectUri must be in the list of redirect URLs for the Azure AD app
        redirectUri: window.location.origin + "/tab-auth/silent-end",
        cacheLocation: "localStorage",
        navigateToLoginRequestUrl: false,
    };
</script>
```

### <a name="get-the-user-context"></a>Obter o contexto do usuário

Na página de conteúdo da guia, chame para obter uma dica de `microsoftTeams.getContext()` login para o usuário atual. Isso é usado como loginHint na chamada para AAD.

```javascript
// Set up extra query parameters for ADAL
// - openid and profile scope adds profile information to the id_token
// - login_hint provides the expected user name
if (loginHint) {
    config.extraQueryParameter = "scope=openid+profile&login_hint=" + encodeURIComponent(loginHint);
} else {
    config.extraQueryParameter = "scope=openid+profile";
}
```

### <a name="authenticate"></a>Autenticar

Se a ADAL tiver um token armazenado em cache para o usuário que não expirou, use esse token. Como alternativa, tente obter um token silenciosamente chamando `acquireToken(resource, callback)` . ADAL.js chama a função de retorno de chamada com o token solicitado ou fornece um erro se a autenticação falhar.

Se você receber um erro na função de retorno de chamada, mostre um botão de login e volte para uma assinatura explícita.

```javascript
let authContext = new AuthenticationContext(config); // from the ADAL.js library
// See if there's a cached user and it matches the expected user
let user = authContext.getCachedUser();
if (user) {
    if (user.profile.oid !== userObjectId) {
        // User doesn't match, clear the cache
        authContext.clearCache();
    }
}

// In this example we are getting an id token (which ADAL.js returns if we ask for resource = clientId)
authContext.acquireToken(config.clientId, function (errDesc, token, err, tokenType) {
    if (token) {
        // Make sure ADAL gave us an id token
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

ADAL.js analisar o resultado de AAD chamando a página de retorno de chamada `AuthenticationContext.handleWindowCallback(hash)` de login.

Verifique se você tem um usuário válido e chame ou para relatar o status à página de conteúdo `microsoftTeams.authentication.notifySuccess()` `microsoftTeams.authentication.notifyFailure()` da guia principal.

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

### <a name="handle-sign-out-flow"></a>Manipular fluxo de saída

Use o seguinte código para manipular o fluxo de saída no AAD Auth:

> [!NOTE]
> Quando você faz logout Teams guia ou bot, a sessão atual é desmarcada.

```javascript
function logout() {
localStorage.clear();
window.location.href = "@Url.Action("<<Action Name>>", "<<Controller Name>>")";
}
```
## <a name="see-also"></a>Confira também

[Configurar provedores de identidade para usar AAD](~/concepts/authentication/configure-identity-provider.md)
