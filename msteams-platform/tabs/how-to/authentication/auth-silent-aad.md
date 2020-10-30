---
title: Autenticação silenciosa
description: Descreve a autenticação silenciosa
keywords: AAD silencioso do SSO de autenticação do Microsoft Teams
ms.openlocfilehash: b8a5b8cb9328635f5730ca089da29140d0a17ac4
ms.sourcegitcommit: 3fc7ad33e2693f07170c3cb1a0d396261fc5c619
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2020
ms.locfileid: "48796362"
---
# <a name="silent-authentication"></a><span data-ttu-id="8e431-104">Autenticação silenciosa</span><span class="sxs-lookup"><span data-stu-id="8e431-104">Silent authentication</span></span>

> [!NOTE]
> <span data-ttu-id="8e431-105">Para que a autenticação funcione para sua guia em clientes móveis, é necessário garantir que você esteja usando pelo menos a versão 1.4.1 do SDK do Microsoft Teams JavaScript.</span><span class="sxs-lookup"><span data-stu-id="8e431-105">For authentication to work for your tab on mobile clients, you need to ensure you're using at least the 1.4.1 version of the Teams JavaScript SDK.</span></span>

<span data-ttu-id="8e431-106">A autenticação silenciosa no Azure Active Directory (Azure AD) minimiza o número de vezes que um usuário precisa inserir suas credenciais de logon, atualizando silenciosamente o token de autenticação.</span><span class="sxs-lookup"><span data-stu-id="8e431-106">Silent authentication in Azure Active Directory (Azure AD) minimizes the number of times a user needs to enter their login credentials by silently refreshing the authentication token.</span></span> <span data-ttu-id="8e431-107">(Para obter suporte para o single sign-on, veja nossa [documentação de SSO](~/tabs/how-to/authentication/auth-aad-sso.md))</span><span class="sxs-lookup"><span data-stu-id="8e431-107">(For true single sign-on support, view our [SSO Documentation](~/tabs/how-to/authentication/auth-aad-sso.md))</span></span>

<span data-ttu-id="8e431-108">Se você quiser manter seu código completamente no lado do cliente, poderá usar a [biblioteca de autenticação do Azure Active Directory](/azure/active-directory/develop/active-directory-authentication-libraries) para JavaScript para tentar adquirir um token de acesso do Azure AD de forma silenciosa.</span><span class="sxs-lookup"><span data-stu-id="8e431-108">If you want to keep your code completely client-side, you can use the [Azure Active Directory Authentication Library](/azure/active-directory/develop/active-directory-authentication-libraries) for JavaScript to attempt to acquire an Azure AD access token silently.</span></span> <span data-ttu-id="8e431-109">Isso significa que o usuário pode nunca ver uma caixa de diálogo pop-up se tiver entrado recentemente.</span><span class="sxs-lookup"><span data-stu-id="8e431-109">This means that the user may never see a popup dialog if they have signed in recently.</span></span>

<span data-ttu-id="8e431-110">Embora a biblioteca de ADAL.js seja otimizada para aplicativos AngularJS, ela também funciona com aplicativos de uma única página JavaScript puro.</span><span class="sxs-lookup"><span data-stu-id="8e431-110">Even though the ADAL.js library is optimized for AngularJS applications, it also works with pure JavaScript single-page applications.</span></span>

> [!NOTE]
> <span data-ttu-id="8e431-111">No momento, a autenticação silenciosa só funciona para guias.</span><span class="sxs-lookup"><span data-stu-id="8e431-111">Currently, silent authentication only works for tabs.</span></span> <span data-ttu-id="8e431-112">Ainda não funciona ao entrar em um bot.</span><span class="sxs-lookup"><span data-stu-id="8e431-112">It does not yet work when signing in from a bot.</span></span>

## <a name="how-silent-authentication-works"></a><span data-ttu-id="8e431-113">Como funciona a autenticação silenciosa</span><span class="sxs-lookup"><span data-stu-id="8e431-113">How silent authentication works</span></span>

<span data-ttu-id="8e431-114">A biblioteca de ADAL.js cria um iframe oculto para o fluxo de concessão implícita do OAuth 2,0, mas especifica `prompt=none` para que o Azure ad nunca mostre a página de logon.</span><span class="sxs-lookup"><span data-stu-id="8e431-114">The ADAL.js library creates a hidden iframe for OAuth 2.0 implicit grant flow, but it specifies `prompt=none` so that Azure AD never shows the login page.</span></span> <span data-ttu-id="8e431-115">Se a interação do usuário for necessária porque o usuário precisa fazer logon ou conceder acesso ao aplicativo, o Azure AD retornará imediatamente um erro que ADAL.js relatará para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8e431-115">If user interaction is required because the user needs to log in or grant access to the application, Azure AD will immediately return an error that ADAL.js then reports to your app.</span></span> <span data-ttu-id="8e431-116">Neste ponto, seu aplicativo pode mostrar um botão de login, se necessário.</span><span class="sxs-lookup"><span data-stu-id="8e431-116">At this point your app can show a login button if needed.</span></span>

## <a name="how-to-do-silent-authentication"></a><span data-ttu-id="8e431-117">Como fazer a autenticação silenciosa</span><span class="sxs-lookup"><span data-stu-id="8e431-117">How to do silent authentication</span></span>

<span data-ttu-id="8e431-118">O código deste artigo vem do exemplo de aplicativo de exemplo do [Microsoft Teams Authentication (nó)](https://github.com/OfficeDev/microsoft-teams-sample-complete-node).</span><span class="sxs-lookup"><span data-stu-id="8e431-118">The code in this article comes from the Teams sample app [Microsoft Teams Authentication Sample (Node)](https://github.com/OfficeDev/microsoft-teams-sample-complete-node).</span></span>

### <a name="include-and-configure-adal"></a><span data-ttu-id="8e431-119">incluir e configurar ADAL</span><span class="sxs-lookup"><span data-stu-id="8e431-119">include and configure ADAL</span></span>

<span data-ttu-id="8e431-120">Inclua a biblioteca de ADAL.js em suas páginas de guia e configure a ADAL com a ID do cliente e a URL de redirecionamento:</span><span class="sxs-lookup"><span data-stu-id="8e431-120">Include the ADAL.js library in your tab pages and configure ADAL with your client ID and redirect URL:</span></span>

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

### <a name="get-the-user-context"></a><span data-ttu-id="8e431-121">Obter o contexto de usuário</span><span class="sxs-lookup"><span data-stu-id="8e431-121">Get the user context</span></span>

<span data-ttu-id="8e431-122">Na página de conteúdo da guia, chame `microsoftTeams.getContext()` para obter uma dica de logon para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="8e431-122">In the tab's content page, call `microsoftTeams.getContext()` to get a login hint for the current user.</span></span> <span data-ttu-id="8e431-123">Isso será usado como um login_hint na chamada para o Azure AD.</span><span class="sxs-lookup"><span data-stu-id="8e431-123">This will be used as a login_hint in the call to Azure AD.</span></span>

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

### <a name="authenticate"></a><span data-ttu-id="8e431-124">Autenticar</span><span class="sxs-lookup"><span data-stu-id="8e431-124">Authenticate</span></span>

<span data-ttu-id="8e431-125">Se a ADAL tiver um token não expirado armazenado no cache para o usuário, use-o.</span><span class="sxs-lookup"><span data-stu-id="8e431-125">If ADAL has an unexpired token cached for the user, use that.</span></span> <span data-ttu-id="8e431-126">Caso contrário, tente obter um token de forma silenciosa chamando `acquireToken(resource, callback)` .</span><span class="sxs-lookup"><span data-stu-id="8e431-126">Otherwise, attempt to get a token silently by calling `acquireToken(resource, callback)`.</span></span> <span data-ttu-id="8e431-127">ADAL.js chamará a função de retorno de chamada com o token solicitado ou um erro se a autenticação falhar.</span><span class="sxs-lookup"><span data-stu-id="8e431-127">ADAL.js will call your callback function with the requested token, or an error if authentication fails.</span></span>

<span data-ttu-id="8e431-128">Se você receber um erro na função de retorno de chamada, mostrar um botão de login e retornar a um logon explícito.</span><span class="sxs-lookup"><span data-stu-id="8e431-128">If you get an error in the callback function, show a login button and fall back to an explicit login.</span></span>

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

### <a name="process-the-return-value"></a><span data-ttu-id="8e431-129">Processar o valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8e431-129">Process the return value</span></span>

<span data-ttu-id="8e431-130">Deixe ADAL.js cuidar da análise do resultado do Azure AD chamando `AuthenticationContext.handleWindowCallback(hash)` na página de retorno de chamada de logon.</span><span class="sxs-lookup"><span data-stu-id="8e431-130">Let ADAL.js take care of parsing the result from Azure AD by calling `AuthenticationContext.handleWindowCallback(hash)` in the login callback page.</span></span>

<span data-ttu-id="8e431-131">Verifique se temos um usuário válido e liga `microsoftTeams.authentication.notifySuccess()` ou `microsoftTeams.authentication.notifyFailure()` para reportar o status de volta para a página de conteúdo da guia principal.</span><span class="sxs-lookup"><span data-stu-id="8e431-131">Check that we have a valid user and call `microsoftTeams.authentication.notifySuccess()` or `microsoftTeams.authentication.notifyFailure()` to report status back to your main tab content page.</span></span>

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
