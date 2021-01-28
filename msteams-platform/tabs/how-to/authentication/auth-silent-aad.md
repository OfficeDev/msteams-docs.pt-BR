---
title: Autenticação silenciosa
description: Descreve a autenticação silenciosa
ms.topic: conceptual
keywords: autenticação silenciosa de SSO do Teams AAD
ms.openlocfilehash: e55e415aba08fdedf4409abf39115838c3a5faf0
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014093"
---
# <a name="silent-authentication"></a>Autenticação silenciosa

> [!NOTE]
> Para que a autenticação funcione para sua guia em clientes móveis, você precisa garantir que esteja usando pelo menos a versão 1.4.1 do SDK JavaScript do Teams.

A autenticação silenciosa no Azure Active Directory (Azure AD) minimiza o número de vezes que um usuário precisa inserir suas credenciais de logon ao atualizar silenciosamente o token de autenticação. (Para suporte verdadeiro ao single sign-on, veja nossa [Documentação de SSO)](~/tabs/how-to/authentication/auth-aad-sso.md)

Se quiser manter seu código completamente do lado do cliente, você pode usar a Biblioteca de Autenticação do [Azure Active Directory](/azure/active-directory/develop/active-directory-authentication-libraries) para JavaScript para tentar adquirir um token de acesso do Azure AD silenciosamente. Isso significa que o usuário pode nunca ver uma caixa de diálogo pop-up se ele tiver se assinado recentemente.

Embora a biblioteca ADAL.js seja otimizada para aplicativos AngularJS, ela também funciona com aplicativos de página única JavaScript puros.

> [!NOTE]
> Atualmente, a autenticação silenciosa só funciona para guias. Ele ainda não funciona ao entrar de um bot.

## <a name="how-silent-authentication-works"></a>Como funciona a autenticação silenciosa

A ADAL.js biblioteca cria um iframe oculto para o fluxo de concessão implícito do OAuth 2.0, mas especifica para que o Azure AD nunca mostre a página `prompt=none` de logon. Se a interação do usuário for necessária porque o usuário precisa entrar ou conceder acesso ao aplicativo, o Azure AD retornará imediatamente um erro que ADAL.js então relata ao seu aplicativo. Neste ponto, seu aplicativo pode mostrar um botão de logon, se necessário.

## <a name="how-to-do-silent-authentication"></a>Como fazer a autenticação silenciosa

O código neste artigo vem do exemplo de aplicativo do [Microsoft Teams Authentication Sample (Node).](https://github.com/OfficeDev/microsoft-teams-sample-complete-node)

### <a name="include-and-configure-adal"></a>incluir e configurar a ADAL

Inclua a ADAL.js nas páginas de guia e configure a ADAL com a ID do cliente e a URL de redirecionamento:

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

Na página de conteúdo da guia, chame `microsoftTeams.getContext()` para obter uma dica de logon para o usuário atual. Isso será usado como um login_hint na chamada para o Azure AD.

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

Se a ADAL tiver um token não vendido em cache para o usuário, use-o. Caso contrário, tente obter um token silenciosamente `acquireToken(resource, callback)` chamando. ADAL.js chamará sua função de retorno de chamada com o token solicitado ou um erro se a autenticação falhar.

Se você receber um erro na função de retorno de chamada, mostre um botão de logon e volte para um logon explícito.

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

Deixe ADAL.js cuidar da análise do resultado do Azure AD chamando na `AuthenticationContext.handleWindowCallback(hash)` página de retorno de chamada de logon.

Verifique se temos um usuário e uma chamada válidas ou para relatar `microsoftTeams.authentication.notifySuccess()` o status de volta à página de conteúdo da guia `microsoftTeams.authentication.notifyFailure()` principal.

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
