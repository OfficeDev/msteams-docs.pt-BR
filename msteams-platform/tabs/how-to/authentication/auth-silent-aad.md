---
title: Autenticação silenciosa
description: Descreve a autenticação silenciosa
keywords: AAD silencioso do SSO de autenticação do Microsoft Teams
ms.openlocfilehash: b8a5b8cb9328635f5730ca089da29140d0a17ac4
ms.sourcegitcommit: fdcd91b270d4c2e98ab2b2c1029c76c49bb807fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "44800950"
---
# <a name="silent-authentication"></a>Autenticação silenciosa

> [!NOTE]
> Para que a autenticação funcione para sua guia em clientes móveis, é necessário garantir que você esteja usando pelo menos a versão 1.4.1 do SDK do Microsoft Teams JavaScript.

A autenticação silenciosa no Azure Active Directory (Azure AD) minimiza o número de vezes que um usuário precisa inserir suas credenciais de logon, atualizando silenciosamente o token de autenticação. (Para obter suporte para o single sign-on, veja nossa [documentação de SSO](~/tabs/how-to/authentication/auth-aad-sso.md))

Se você quiser manter seu código completamente no lado do cliente, poderá usar a [biblioteca de autenticação do Azure Active Directory](/azure/active-directory/develop/active-directory-authentication-libraries) para JavaScript para tentar adquirir um token de acesso do Azure AD de forma silenciosa. Isso significa que o usuário pode nunca ver uma caixa de diálogo pop-up se tiver entrado recentemente.

Embora a biblioteca de ADAL.js seja otimizada para aplicativos AngularJS, ela também funciona com aplicativos de uma única página JavaScript puro.

> [!NOTE]
> No momento, a autenticação silenciosa só funciona para guias. Ainda não funciona ao entrar em um bot.

## <a name="how-silent-authentication-works"></a>Como funciona a autenticação silenciosa

A biblioteca de ADAL.js cria um iframe oculto para o fluxo de concessão implícita do OAuth 2,0, mas especifica `prompt=none` para que o Azure ad nunca mostre a página de logon. Se a interação do usuário for necessária porque o usuário precisa fazer logon ou conceder acesso ao aplicativo, o Azure AD retornará imediatamente um erro que ADAL.js relatará para o seu aplicativo. Neste ponto, seu aplicativo pode mostrar um botão de login, se necessário.

## <a name="how-to-do-silent-authentication"></a>Como fazer a autenticação silenciosa

O código deste artigo vem do exemplo de aplicativo de exemplo do [Microsoft Teams Authentication (nó)](https://github.com/OfficeDev/microsoft-teams-sample-complete-node).

### <a name="include-and-configure-adal"></a>incluir e configurar ADAL

Inclua a biblioteca de ADAL.js em suas páginas de guia e configure a ADAL com a ID do cliente e a URL de redirecionamento:

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

### <a name="get-the-user-context"></a>Obter o contexto de usuário

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

Se a ADAL tiver um token não expirado armazenado no cache para o usuário, use-o. Caso contrário, tente obter um token de forma silenciosa chamando `acquireToken(resource, callback)` . ADAL.js chamará a função de retorno de chamada com o token solicitado ou um erro se a autenticação falhar.

Se você receber um erro na função de retorno de chamada, mostrar um botão de login e retornar a um logon explícito.

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

Deixe ADAL.js cuidar da análise do resultado do Azure AD chamando `AuthenticationContext.handleWindowCallback(hash)` na página de retorno de chamada de logon.

Verifique se temos um usuário válido e liga `microsoftTeams.authentication.notifySuccess()` ou `microsoftTeams.authentication.notifyFailure()` para reportar o status de volta para a página de conteúdo da guia principal.

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
