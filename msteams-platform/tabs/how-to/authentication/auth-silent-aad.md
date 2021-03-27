---
title: Autenticação silenciosa
description: Descreve a autenticação silenciosa
ms.topic: conceptual
keywords: autenticação do teams SSO silent AAD
ms.openlocfilehash: 7facaef0941ff7602b3e23444653ef41415c3396
ms.sourcegitcommit: 3727fc58e84b6f1752612884c2e0b25e207fb56e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2021
ms.locfileid: "51382342"
---
# <a name="silent-authentication"></a><span data-ttu-id="cfb62-104">Autenticação silenciosa</span><span class="sxs-lookup"><span data-stu-id="cfb62-104">Silent authentication</span></span>

> [!NOTE]
> <span data-ttu-id="cfb62-105">Para que a autenticação funcione para sua guia em clientes móveis, verifique se você está usando pelo menos a versão 1.4.1 do SDK JavaScript do Teams.</span><span class="sxs-lookup"><span data-stu-id="cfb62-105">For authentication to work for your tab on mobile clients, ensure you are using at least 1.4.1 version of the Teams JavaScript SDK.</span></span>

<span data-ttu-id="cfb62-106">A autenticação silenciosa no Azure Active Directory (AAD) minimiza o número de vezes que um usuário inssinge suas credenciais de entrada atualize silenciosamente o token de autenticação.</span><span class="sxs-lookup"><span data-stu-id="cfb62-106">Silent authentication in Azure Active Directory (AAD) minimizes the number of times a user enters their sign in credentials by silently refreshing the authentication token.</span></span> <span data-ttu-id="cfb62-107">Para ver o suporte verdadeiro ao login único, consulte [documentação do SSO](~/tabs/how-to/authentication/auth-aad-sso.md).</span><span class="sxs-lookup"><span data-stu-id="cfb62-107">For true single sign-on support, see [SSO documentation](~/tabs/how-to/authentication/auth-aad-sso.md).</span></span>

<span data-ttu-id="cfb62-108">Se você quiser manter seu código completamente no lado do cliente, você pode usar a biblioteca de autenticação [do AAD](/azure/active-directory/develop/active-directory-authentication-libraries) para JavaScript para obter um token de acesso AAD silenciosamente.</span><span class="sxs-lookup"><span data-stu-id="cfb62-108">If you want to keep your code completely client-side, you can use the [AAD authentication library](/azure/active-directory/develop/active-directory-authentication-libraries) for JavaScript to get an AAD access token silently.</span></span> <span data-ttu-id="cfb62-109">Se o usuário tiver se assinado recentemente, ele nunca verá uma caixa de diálogo pop-up.</span><span class="sxs-lookup"><span data-stu-id="cfb62-109">If the user has signed in recently, they never see a popup dialog box.</span></span>

<span data-ttu-id="cfb62-110">Embora a biblioteca ADAL.js seja otimizada para aplicativos AngularJS, ela também funciona com aplicativos de página única JavaScript puros.</span><span class="sxs-lookup"><span data-stu-id="cfb62-110">Even though the ADAL.js library is optimized for AngularJS applications, it also works with pure JavaScript single-page applications.</span></span>

> [!NOTE]
> <span data-ttu-id="cfb62-111">Atualmente, a autenticação silenciosa só funciona para guias.</span><span class="sxs-lookup"><span data-stu-id="cfb62-111">Currently, silent authentication only works for tabs.</span></span> <span data-ttu-id="cfb62-112">Ele não funciona ao entrar de um bot.</span><span class="sxs-lookup"><span data-stu-id="cfb62-112">It does not work when signing in from a bot.</span></span>

## <a name="how-silent-authentication-works"></a><span data-ttu-id="cfb62-113">Como funciona a autenticação silenciosa</span><span class="sxs-lookup"><span data-stu-id="cfb62-113">How silent authentication works</span></span>

<span data-ttu-id="cfb62-114">A ADAL.js cria um iframe oculto para o fluxo implícito de concessão do OAuth 2.0.</span><span class="sxs-lookup"><span data-stu-id="cfb62-114">The ADAL.js library creates a hidden iframe for OAuth 2.0 implicit grant flow.</span></span> <span data-ttu-id="cfb62-115">Mas a biblioteca especifica `prompt=none` , portanto, o Azure AD nunca mostra a página de logom.</span><span class="sxs-lookup"><span data-stu-id="cfb62-115">But the library specifies `prompt=none`, so Azure AD never shows the sign in page.</span></span> <span data-ttu-id="cfb62-116">Se a interação do usuário for necessária porque o usuário precisa entrar ou conceder acesso ao aplicativo, o AAD retornará imediatamente um erro que ADAL.js relatórios para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cfb62-116">If user interaction is required because the user needs to sign in or grant access to the application, AAD immediately returns an error that ADAL.js reports to your app.</span></span> <span data-ttu-id="cfb62-117">Neste ponto, seu aplicativo pode mostrar um botão de login, se necessário.</span><span class="sxs-lookup"><span data-stu-id="cfb62-117">At this point your app can show a sign in button if required.</span></span>

## <a name="how-to-do-silent-authentication"></a><span data-ttu-id="cfb62-118">Como fazer autenticação silenciosa</span><span class="sxs-lookup"><span data-stu-id="cfb62-118">How to do silent authentication</span></span>

<span data-ttu-id="cfb62-119">O código neste artigo vem do aplicativo de exemplo do Teams que é o nó de exemplo [de autenticação do Teams.](https://github.com/OfficeDev/Microsoft-Teams-Samples/blob/main/samples/app-auth/nodejs/src/views/tab/silent/silent.hbs)</span><span class="sxs-lookup"><span data-stu-id="cfb62-119">The code in this article comes from the Teams sample app that is [Teams authentication sample node](https://github.com/OfficeDev/Microsoft-Teams-Samples/blob/main/samples/app-auth/nodejs/src/views/tab/silent/silent.hbs).</span></span>

### <a name="include-and-configure-adal"></a><span data-ttu-id="cfb62-120">incluir e configurar o ADAL</span><span class="sxs-lookup"><span data-stu-id="cfb62-120">include and configure ADAL</span></span>

<span data-ttu-id="cfb62-121">Inclua a ADAL.js em suas páginas de tabulação e configure o ADAL com a ID do cliente e a URL de redirecionamento:</span><span class="sxs-lookup"><span data-stu-id="cfb62-121">Include the ADAL.js library in your tab pages and configure ADAL with your client ID and redirect URL:</span></span>

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

### <a name="get-the-user-context"></a><span data-ttu-id="cfb62-122">Obter o contexto do usuário</span><span class="sxs-lookup"><span data-stu-id="cfb62-122">Get the user context</span></span>

<span data-ttu-id="cfb62-123">Na página de conteúdo da guia, chame para obter uma dica de `microsoftTeams.getContext()` login para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="cfb62-123">In the tab's content page, call `microsoftTeams.getContext()` to get a sign in hint for the current user.</span></span> <span data-ttu-id="cfb62-124">Isso é usado como loginHint na chamada ao AAD.</span><span class="sxs-lookup"><span data-stu-id="cfb62-124">This is used as a loginHint in the call to AAD.</span></span>

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

### <a name="authenticate"></a><span data-ttu-id="cfb62-125">Autenticar</span><span class="sxs-lookup"><span data-stu-id="cfb62-125">Authenticate</span></span>

<span data-ttu-id="cfb62-126">Se a ADAL tiver um token armazenado em cache para o usuário que não expirou, use esse token.</span><span class="sxs-lookup"><span data-stu-id="cfb62-126">If ADAL has a token cached for the user that has not expired, use that token.</span></span> <span data-ttu-id="cfb62-127">Como alternativa, tente obter um token silenciosamente chamando `acquireToken(resource, callback)` .</span><span class="sxs-lookup"><span data-stu-id="cfb62-127">Alternately, attempt to get a token silently by calling `acquireToken(resource, callback)`.</span></span> <span data-ttu-id="cfb62-128">ADAL.js chama a função de retorno de chamada com o token solicitado ou fornece um erro se a autenticação falhar.</span><span class="sxs-lookup"><span data-stu-id="cfb62-128">ADAL.js calls the callback function with the requested token, or gives an error if authentication fails.</span></span>

<span data-ttu-id="cfb62-129">Se você receber um erro na função de retorno de chamada, mostre um botão de login e volte para uma assinatura explícita.</span><span class="sxs-lookup"><span data-stu-id="cfb62-129">If you get an error in the callback function, show a sign in button and fall back to an explicit sign in.</span></span>

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

### <a name="process-the-return-value"></a><span data-ttu-id="cfb62-130">Processar o valor de retorno</span><span class="sxs-lookup"><span data-stu-id="cfb62-130">Process the return value</span></span>

<span data-ttu-id="cfb62-131">ADAL.js analisar o resultado do AAD chamando a página de retorno `AuthenticationContext.handleWindowCallback(hash)` de chamada de login.</span><span class="sxs-lookup"><span data-stu-id="cfb62-131">ADAL.js parses the result from AAD by calling `AuthenticationContext.handleWindowCallback(hash)` in the sign in callback page.</span></span>

<span data-ttu-id="cfb62-132">Verifique se você tem um usuário válido e chame ou para relatar o status à página de conteúdo `microsoftTeams.authentication.notifySuccess()` `microsoftTeams.authentication.notifyFailure()` da guia principal.</span><span class="sxs-lookup"><span data-stu-id="cfb62-132">Check that you have a valid user and call `microsoftTeams.authentication.notifySuccess()` or `microsoftTeams.authentication.notifyFailure()` to report the status to your main tab content page.</span></span>

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

### <a name="handle-sign-out-flow"></a><span data-ttu-id="cfb62-133">Manipular fluxo de saída</span><span class="sxs-lookup"><span data-stu-id="cfb62-133">Handle sign out flow</span></span>

<span data-ttu-id="cfb62-134">Use o código a seguir para manipular o fluxo de saída no AAD Auth:</span><span class="sxs-lookup"><span data-stu-id="cfb62-134">Use the following code to handle sign out flow in AAD Auth:</span></span>

> [!NOTE]
> <span data-ttu-id="cfb62-135">Embora o logout para a guia ou bot do Teams seja feito, a sessão atual também está desmarcada.</span><span class="sxs-lookup"><span data-stu-id="cfb62-135">While logout for Teams tab or bot is done, the current session is also cleared.</span></span>

```javascript
function logout() {
localStorage.clear();
window.location.href = "@Url.Action("<<Action Name>>", "<<Controller Name>>")";
}
```