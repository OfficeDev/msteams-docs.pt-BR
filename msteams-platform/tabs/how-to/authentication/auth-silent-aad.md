---
title: Autenticação silenciosa
description: Descreve a autenticação silenciosa, logon único, Azure AD para guias
ms.topic: conceptual
ms.localizationpriority: high
keywords: autenticação do teams logon único tab do Azure AD
ms.openlocfilehash: 699582414a4699a69519e41232e4354d8125337b
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111644"
---
# <a name="silent-authentication"></a>Autenticação silenciosa

> [!IMPORTANT]
> O suporte e o desenvolvimento da Microsoft para Biblioteca de Autenticação do Active Directory (ADAL), incluindo as correções de segurança, termina em **30 de junho de 2022**. Atualize seus aplicativos para usar a MSAL (Biblioteca de Autenticação da Microsoft) para continuar recebendo suporte. Consulte [Migrar aplicativos para a biblioteca de autenticação da Microsoft (MSAL)](/azure/active-directory/develop/msal-migration).

> [!NOTE]
> Para que a autenticação funcione para sua guia em dispositivos móveis clientes, é necessário garantir que você esteja usando a versão 1.4.1 ou posterior do SDK JavaScript do Teams.

A autenticação silenciosa no Azure AD minimiza o número de vezes que um usuário insere suas credenciais atualizando silenciosamente o token de autenticação. Para obter suporte para logon único verdadeiro, consulte [Documentação do logon único](~/tabs/how-to/authentication/auth-aad-sso.md).

Para manter seu código no lado do cliente, use a [Biblioteca de autenticação do Azure AD](/azure/active-directory/develop/active-directory-authentication-libraries) para JavaScript para obter um token de acesso do Microsoft Azure Active Directory (Azure AD) silenciosamente. Se o usuário tiver entrado recentemente, ele não verá uma caixa de diálogo pop-up.

Embora a Biblioteca de Autenticação do Active Directory seja otimizada para aplicativos AngularJS, ela também funciona aplicativos de página única (SPA) JavaScript.

> [!NOTE]
> Atualmente, a autenticação silenciosa só funciona para guias. Ele não funciona ao entrar de um bot.

## <a name="how-silent-authentication-works"></a>Como funciona a autenticação silenciosa

O Biblioteca de Autenticação do Active Directory cria um iframe oculto para o fluxo de concessão implícita do OAuth 2.0. Mas a biblioteca especifica `prompt=none` para que o Azure AD não exiba a página de entrada. A interação do usuário poderá ser necessária se ele precisar entrar ou conceder acesso ao aplicativo. Se a interação do usuário for necessária, o Azure AD retornará um erro que a biblioteca relatará ao seu aplicativo. Se necessário, seu aplicativo agora pode exibir uma opção de entrada.

## <a name="how-to-do-silent-authentication"></a>Como fazer a autenticação silenciosa

O código neste artigo vem do aplicativo de exemplo do Teams [Nó do exemplo de autenticação do Teams](https://github.com/OfficeDev/Microsoft-Teams-Samples/blob/main/samples/app-auth/nodejs/src/views/tab/silent/silent.hbs).

[Inicie uma guia configurável de autenticação silenciosa e simples usando o Azure AD](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-channel-group-config-page-auth/csharp) e siga as instruções para executar o exemplo no computador local.

### <a name="include-and-configure-active-directory-authentication-library"></a>Incluir e configurar a Biblioteca de Autenticação do Active Directory

Inclua a Biblioteca de Autenticação do Active Directory nas páginas da guia e configure a biblioteca com a ID do cliente e a URL de redirecionamento:

```html
<script src="https://secure.aadcdn.microsoftonline-p.com/lib/1.0.15/js/adal.min.js" integrity="sha384-lIk8T3uMxKqXQVVfFbiw0K/Nq+kt1P3NtGt/pNexiDby2rKU6xnDY8p16gIwKqgI" crossorigin="anonymous"></script>
<script type="text/javascript">
    // Active Directory Authentication Library configuration
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

Na página de conteúdo da guia, chame `microsoftTeams.getContext()` para obter uma dica de entrada para o usuário atual. A dica é usada como um `loginHint` na chamada ao Azure AD.

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

Se a Biblioteca de Autenticação do Active Directory tiver um token não expirado armazenado em cache para o usuário, use-o. Como alternativa, chame `acquireToken(resource, callback)` para receber silenciosamente um token. A biblioteca chama uma função de retorno de chamada com o token solicitado ou gera um erro se a autenticação falhar.

Se você receber um erro na função de retorno de chamada, exiba e use uma opção de entrada explícita.

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

### <a name="process-the-return-value"></a>Processar o valor retornado

A Biblioteca de Autenticação do Active Directory analisa o resultado do Azure AD chamando `AuthenticationContext.handleWindowCallback(hash)` na página de retorno de chamada de entrada.

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

Use o código a seguir para lidar com o fluxo de saída na autenticação do Azure AD:

> [!NOTE]
> Quando você faz logoff da guia ou bot do Teams, a sessão atual é limpa.

```javascript
function logout() {
localStorage.clear();
window.location.href = "@Url.Action("<<Action Name>>", "<<Controller Name>>")";
}
```

## <a name="see-also"></a>Confira também

* [Configurar provedores de identidade para usar o Azure AD](../../../concepts/authentication/configure-identity-provider.md)
* [Saiba mais sobre a Biblioteca de Autenticação Microsoft (MSAL)](/azure/active-directory/develop/msal-overview)
