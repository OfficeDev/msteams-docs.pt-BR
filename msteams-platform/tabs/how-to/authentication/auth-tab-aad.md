---
title: Autenticação para guias usando o Azure Active Directory
description: Descreve a autenticação no Microsoft Teams e como usá-la em guias
keywords: AAD de guias de autenticação de equipes
ms.openlocfilehash: a1d3a96e23706012b643b5827701b49e2306d847
ms.sourcegitcommit: f9a2f5cedc9d30ef7a9cf78a47d01cfd277e150d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "48237780"
---
# <a name="authenticate-a-user-in-a-microsoft-teams-tab"></a><span data-ttu-id="3463e-104">Autenticar um usuário em uma guia do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="3463e-104">Authenticate a user in a Microsoft Teams tab</span></span>

> [!Note]
> <span data-ttu-id="3463e-105">Para que a autenticação funcione para sua guia em clientes móveis, é necessário garantir que você esteja usando a versão 1.4.1 ou posterior do SDK do Microsoft Teams JavaScript.</span><span class="sxs-lookup"><span data-stu-id="3463e-105">For authentication to work for your tab on mobile clients, you need to ensure you're using version 1.4.1 or later of the Teams JavaScript SDK.</span></span>

<span data-ttu-id="3463e-106">Há muitos serviços que você pode desejar usar dentro do seu aplicativo do Microsoft Teams e a maioria desses serviços requer autenticação e autorização para obter acesso ao serviço.</span><span class="sxs-lookup"><span data-stu-id="3463e-106">There are many services that you may wish to consume inside your Teams app, and most of those services require authentication and authorization to get access to the service.</span></span> <span data-ttu-id="3463e-107">Os serviços incluem o Facebook, o Twitter e o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="3463e-107">Services include Facebook, Twitter, and of course Teams.</span></span> <span data-ttu-id="3463e-108">Os usuários de Teams têm informações de perfil de usuário armazenadas no Azure Active Directory (Azure AD) usando o Microsoft Graph, e este artigo se concentrará na autenticação usando o Azure AD para obter acesso a essas informações.</span><span class="sxs-lookup"><span data-stu-id="3463e-108">Users of Teams have user profile information stored in Azure Active Directory (Azure AD) using Microsoft Graph and this article will focus on authentication using Azure AD to get access to this information.</span></span>

<span data-ttu-id="3463e-109">O OAuth 2,0 é um padrão aberto para autenticação usada pelo Azure AD e muitos outros provedores de serviços.</span><span class="sxs-lookup"><span data-stu-id="3463e-109">OAuth 2.0 is an open standard for authentication used by Azure AD and many other service providers.</span></span> <span data-ttu-id="3463e-110">A compreensão do OAuth 2,0 é um pré-requisito para trabalhar com autenticação no Teams e no Azure AD.</span><span class="sxs-lookup"><span data-stu-id="3463e-110">Understanding OAuth 2.0 is a prerequisite for working with authentication in Teams and Azure AD.</span></span> <span data-ttu-id="3463e-111">Os exemplos abaixo usam o fluxo de concessão implícita do OAuth 2,0 com o objetivo de eventualmente ler as informações de perfil do usuário do Azure AD e do Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="3463e-111">The examples below use the OAuth 2.0 Implicit Grant flow with the goal of eventually reading the user's profile information from Azure AD and Microsoft Graph.</span></span>

<span data-ttu-id="3463e-112">O código deste artigo vem do exemplo de aplicativo de exemplo do [Microsoft Teams de autenticação de guia do Microsoft Teams (nó)](https://github.com/OfficeDev/microsoft-teams-sample-complete-node).</span><span class="sxs-lookup"><span data-stu-id="3463e-112">The code in this article comes from the Teams sample app [Microsoft Teams tab authentication sample (Node)](https://github.com/OfficeDev/microsoft-teams-sample-complete-node).</span></span> <span data-ttu-id="3463e-113">Ele contém uma guia estática que solicita um token de acesso para o Microsoft Graph e mostra as informações do perfil básico do usuário atual do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="3463e-113">It contains a static tab that requests an access token for Microsoft Graph and shows the current user's basic profile information from Azure AD.</span></span>

<span data-ttu-id="3463e-114">Para obter uma visão geral do fluxo de autenticação para guias, consulte o tópico [fluxo de autenticação em guias](~/tabs/how-to/authentication/auth-flow-tab.md).</span><span class="sxs-lookup"><span data-stu-id="3463e-114">For a general overview of authentication flow for tabs see the topic [Authentication flow in tabs](~/tabs/how-to/authentication/auth-flow-tab.md).</span></span>

<span data-ttu-id="3463e-115">O fluxo de autenticação em guias difere ligeiramente do fluxo de autenticação em bots.</span><span class="sxs-lookup"><span data-stu-id="3463e-115">Authentication flow in tabs differs slightly from authentication flow in bots.</span></span>

## <a name="configuring-identity-providers"></a><span data-ttu-id="3463e-116">Configurando provedores de identidade</span><span class="sxs-lookup"><span data-stu-id="3463e-116">Configuring identity providers</span></span>

<span data-ttu-id="3463e-117">Consulte o tópico [Configure Identity Providers](~/concepts/authentication/configure-identity-provider.md) para obter etapas detalhadas sobre como configurar URLs de redirecionamento de retorno de chamada OAuth 2,0 ao usar o Azure Active Directory como um provedor de identidade.</span><span class="sxs-lookup"><span data-stu-id="3463e-117">See the topic [Configure identity providers](~/concepts/authentication/configure-identity-provider.md) for detailed steps on configuring OAuth 2.0 callback redirect URL(s) when using Azure Active Directory as an identity provider.</span></span>

## <a name="initiate-authentication-flow"></a><span data-ttu-id="3463e-118">Iniciar o fluxo de autenticação</span><span class="sxs-lookup"><span data-stu-id="3463e-118">Initiate authentication flow</span></span>

<span data-ttu-id="3463e-119">O fluxo de autenticação deve ser acionado por uma ação do usuário.</span><span class="sxs-lookup"><span data-stu-id="3463e-119">Authentication flow should be triggered by a user action.</span></span> <span data-ttu-id="3463e-120">Você não deve abrir o pop-up de autenticação automaticamente porque isso provavelmente disparará o bloqueador de pop-ups do navegador, além de confundir o usuário.</span><span class="sxs-lookup"><span data-stu-id="3463e-120">You should not open the authentication pop-up automatically because this is likely to trigger the browser's pop-up blocker as well as confuse the user.</span></span>

<span data-ttu-id="3463e-121">Adicione um botão à sua página de configuração ou conteúdo para permitir que o usuário entre quando necessário.</span><span class="sxs-lookup"><span data-stu-id="3463e-121">Add a button to your configuration or content page to enable the user to sign in when needed.</span></span> <span data-ttu-id="3463e-122">Isso pode ser feito na página [configuração](~/tabs/how-to/create-tab-pages/configuration-page.md) da guia ou em qualquer página de [conteúdo](~/tabs/how-to/create-tab-pages/content-page.md) .</span><span class="sxs-lookup"><span data-stu-id="3463e-122">This can be done in the tab [configuration](~/tabs/how-to/create-tab-pages/configuration-page.md) page or any [content](~/tabs/how-to/create-tab-pages/content-page.md) page.</span></span>

<span data-ttu-id="3463e-123">O Azure AD, como a maioria dos provedores de identidade, não permite que seu conteúdo seja colocado em um iframe.</span><span class="sxs-lookup"><span data-stu-id="3463e-123">Azure AD, like most identity providers, does not allow its content to be placed in an iframe.</span></span> <span data-ttu-id="3463e-124">Isso significa que você precisará adicionar uma página pop-up para hospedar o provedor de identidade.</span><span class="sxs-lookup"><span data-stu-id="3463e-124">This means that you will need to add a pop-up page to host the identity provider.</span></span> <span data-ttu-id="3463e-125">No exemplo a seguir, esta página é `/tab-auth/simple-start` .</span><span class="sxs-lookup"><span data-stu-id="3463e-125">In the following example this page is `/tab-auth/simple-start`.</span></span> <span data-ttu-id="3463e-126">Use a `microsoftTeams.authenticate()` função do Microsoft Teams Client SDK para iniciar esta página quando seu botão estiver selecionado.</span><span class="sxs-lookup"><span data-stu-id="3463e-126">Use the `microsoftTeams.authenticate()` function of the Microsoft Teams client SDK to launch this page when your button is selected.</span></span>

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

### <a name="notes"></a><span data-ttu-id="3463e-127">Observações</span><span class="sxs-lookup"><span data-stu-id="3463e-127">Notes</span></span>

* <span data-ttu-id="3463e-128">A URL para a qual você passa `microsoftTeams.authentication.authenticate()` é a página inicial do fluxo de autenticação.</span><span class="sxs-lookup"><span data-stu-id="3463e-128">The URL you pass to `microsoftTeams.authentication.authenticate()` is the start page of the authentication flow.</span></span> <span data-ttu-id="3463e-129">Neste exemplo `/tab-auth/simple-start` .</span><span class="sxs-lookup"><span data-stu-id="3463e-129">In this example that is `/tab-auth/simple-start`.</span></span> <span data-ttu-id="3463e-130">Isso deve corresponder ao que você registrou no [portal de registro de aplicativo do Azure ad](https://apps.dev.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="3463e-130">This should match what you registered in the [Azure AD Application Registration Portal](https://apps.dev.microsoft.com).</span></span>

* <span data-ttu-id="3463e-131">O fluxo de autenticação deve começar em uma página que está no seu domínio.</span><span class="sxs-lookup"><span data-stu-id="3463e-131">Authentication flow must start on a page that's on your domain.</span></span> <span data-ttu-id="3463e-132">Esse domínio também deve ser listado na [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) seção do manifesto.</span><span class="sxs-lookup"><span data-stu-id="3463e-132">This domain should also be listed in the [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) section of the manifest.</span></span> <span data-ttu-id="3463e-133">Se isso não for feito, resultará em um pop-up vazio.</span><span class="sxs-lookup"><span data-stu-id="3463e-133">Failure to do so will result in an empty pop-up.</span></span>

* <span data-ttu-id="3463e-134">A não utilização causará `microsoftTeams.authentication.authenticate()` um problema com o pop-up que não está fechando no final do processo de entrada.</span><span class="sxs-lookup"><span data-stu-id="3463e-134">Failing to use `microsoftTeams.authentication.authenticate()` will cause a problem with the popup not closing at the end of the sign in process.</span></span>

## <a name="navigate-to-the-authorization-page-from-your-popup-page"></a><span data-ttu-id="3463e-135">Navegue até a página autorização na página pop-up</span><span class="sxs-lookup"><span data-stu-id="3463e-135">Navigate to the authorization page from your popup page</span></span>

<span data-ttu-id="3463e-136">Quando a página pop-up ( `/tab-auth/simple-start` ) é exibida, o código a seguir é executado.</span><span class="sxs-lookup"><span data-stu-id="3463e-136">When your popup page (`/tab-auth/simple-start`) is displayed the following code is run.</span></span> <span data-ttu-id="3463e-137">O objetivo principal desta página é redirecionar para seu provedor de identidade para que o usuário possa entrar.</span><span class="sxs-lookup"><span data-stu-id="3463e-137">The main goal of this page is to redirect to your identity provider so the user can sign in.</span></span> <span data-ttu-id="3463e-138">Esse redirecionamento pode ser feito no lado do servidor usando HTTP 302, mas, nesse caso, é feito no lado do cliente usando uma chamada para `window.location.assign()` .</span><span class="sxs-lookup"><span data-stu-id="3463e-138">This redirection could be done on the server side using HTTP 302, but in this case it is done on the client side using with a call to `window.location.assign()`.</span></span> <span data-ttu-id="3463e-139">Isso também permite que `microsoftTeams.getContext()` seja usado para recuperar informações de dicas que podem ser passadas para o Azure AD.</span><span class="sxs-lookup"><span data-stu-id="3463e-139">This also allows `microsoftTeams.getContext()` to be used to retrieve hinting information which can be passed to Azure AD.</span></span>

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

<span data-ttu-id="3463e-140">Depois que o usuário concluir a autorização, o usuário será redirecionado para a página de retorno de chamada que você especificou para seu aplicativo em `/tab-auth/simple-end` .</span><span class="sxs-lookup"><span data-stu-id="3463e-140">After the user completes authorization, the user is redirected to the callback page you specified for your app at `/tab-auth/simple-end`.</span></span>

### <a name="notes"></a><span data-ttu-id="3463e-141">Observações</span><span class="sxs-lookup"><span data-stu-id="3463e-141">Notes</span></span>

* <span data-ttu-id="3463e-142">Consulte [obter informações de contexto de usuário](~/tabs/how-to/access-teams-context.md) para ajudar a criar solicitações de autenticação e URLs.</span><span class="sxs-lookup"><span data-stu-id="3463e-142">See [get user context information](~/tabs/how-to/access-teams-context.md) for help building authentication requests and URLs.</span></span> <span data-ttu-id="3463e-143">Por exemplo, você pode usar o nome de logon do usuário como o `login_hint` valor para a entrada do Azure AD, o que significa que o usuário pode precisar digitar menos.</span><span class="sxs-lookup"><span data-stu-id="3463e-143">For example, you can use the user's login name as the `login_hint` value for Azure AD sign-in, which means the user might need to type less.</span></span> <span data-ttu-id="3463e-144">Lembre-se de que você não deve usar esse contexto diretamente como prova de identidade, uma vez que um invasor pode carregar sua página em um navegador mal-intencionado e fornecer qualquer informação que desejar.</span><span class="sxs-lookup"><span data-stu-id="3463e-144">Remember that you should not use this context directly as proof of identity since an attacker could load your page in a malicious browser and provide it with any information they want.</span></span>
* <span data-ttu-id="3463e-145">Embora o contexto de tabulação forneça informações úteis sobre o usuário, não use essas informações para autenticar o usuário se você o recebe como parâmetros de URL para a URL de conteúdo da sua guia ou chamando a `microsoftTeams.getContext()` função no SDK do cliente do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="3463e-145">Although the tab context provides useful information regarding the user, don't use this information to authenticate the user whether you get it as URL parameters to your tab content URL or by calling the `microsoftTeams.getContext()` function in the Microsoft Teams client SDK.</span></span> <span data-ttu-id="3463e-146">Um ator mal-intencionado pode invocar a URL de conteúdo da guia com seus próprios parâmetros, e uma página da Web representando o Microsoft Teams pode carregar sua URL de conteúdo de tabulação em um iframe e retornar seus próprios dados para a `getContext()` função.</span><span class="sxs-lookup"><span data-stu-id="3463e-146">A malicious actor could invoke your tab content URL with its own parameters, and a web page impersonating Microsoft Teams could load your tab content URL in an iframe and return its own data to the `getContext()` function.</span></span> <span data-ttu-id="3463e-147">Você deve tratar as informações relacionadas à identidade no contexto da guia simplesmente como dicas e validá-las antes de usar.</span><span class="sxs-lookup"><span data-stu-id="3463e-147">You should treat the identity-related information in the tab context simply as hints and validate them before use.</span></span>
* <span data-ttu-id="3463e-148">O `state` parâmetro é usado para confirmar se o serviço que está chamando o URI de retorno de chamada é o serviço que você chamou.</span><span class="sxs-lookup"><span data-stu-id="3463e-148">The `state` parameter is used to confirm that the service calling the callback URI is the service you called.</span></span> <span data-ttu-id="3463e-149">Se o `state` parâmetro no retorno de chamada não corresponder ao parâmetro que você enviou durante a chamada, a chamada de retorno não é verificada e deve ser encerrada.</span><span class="sxs-lookup"><span data-stu-id="3463e-149">If the `state` parameter in the callback does not match the parameter you sent during the call the return call is not verified and should be terminated.</span></span>
* <span data-ttu-id="3463e-150">Não é necessário incluir o domínio do provedor de identidade na `validDomains` lista na manifest.jsdo aplicativo no arquivo.</span><span class="sxs-lookup"><span data-stu-id="3463e-150">It is not necessary to include the identity provider's domain in the `validDomains` list in the app's manifest.json file.</span></span>

## <a name="the-callback-page"></a><span data-ttu-id="3463e-151">A página de retorno de chamada</span><span class="sxs-lookup"><span data-stu-id="3463e-151">The callback page</span></span>

<span data-ttu-id="3463e-152">Na última seção que você chamou o serviço de autorização do Azure AD e passou as informações do usuário e do aplicativo para que o Azure AD possa apresentar ao usuário sua própria experiência de autorização monolítica.</span><span class="sxs-lookup"><span data-stu-id="3463e-152">In the last section you called the Azure AD authorization service and passed in user and app information so that Azure AD could present the user with its own monolithic authorization experience.</span></span> <span data-ttu-id="3463e-153">Seu aplicativo não tem controle sobre o que acontece nesta experiência.</span><span class="sxs-lookup"><span data-stu-id="3463e-153">Your app has no control over what happens in this experience.</span></span> <span data-ttu-id="3463e-154">Tudo o que ele sabe é o que é retornado quando o Azure AD chama a página de retorno de chamada fornecida ( `/tab-auth/simple-end` ).</span><span class="sxs-lookup"><span data-stu-id="3463e-154">All it knows is what is returned when Azure AD calls the  callback page that you provided (`/tab-auth/simple-end`).</span></span>

<span data-ttu-id="3463e-155">Nesta página, você precisa determinar o sucesso ou a falha com base nas informações retornadas pelo Azure AD e Call `microsoftTeams.authentication.notifySuccess()` ou `microsoftTeams.authentication.notifyFailure()` .</span><span class="sxs-lookup"><span data-stu-id="3463e-155">In this page you need to determine success or failure based on the information returned by Azure AD and call `microsoftTeams.authentication.notifySuccess()` or `microsoftTeams.authentication.notifyFailure()`.</span></span> <span data-ttu-id="3463e-156">Se o logon tiver sido bem-sucedido, você terá acesso a recursos de serviço.</span><span class="sxs-lookup"><span data-stu-id="3463e-156">If the login was successful you will have access to service resources.</span></span>

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

<span data-ttu-id="3463e-157">Este código analisa os pares chave-valor recebidos do Azure AD `window.location.hash` usando a `getHashParameters()` função auxiliar.</span><span class="sxs-lookup"><span data-stu-id="3463e-157">This code parses the key-value pairs received from Azure AD in `window.location.hash` using the `getHashParameters()` helper function.</span></span> <span data-ttu-id="3463e-158">Se encontrar um `access_token` , e o `state` valor for igual ao fornecido no início do fluxo de autenticação, ele retornará o token de acesso à guia chamando `notifySuccess()` ; caso contrário, ele informa um erro com `notifyFailure()` .</span><span class="sxs-lookup"><span data-stu-id="3463e-158">If it finds an `access_token`, and the `state` value is the same as the one provided at the start of the authentication flow, it returns the access token to the tab by calling `notifySuccess()`; otherwise it reports an error with `notifyFailure()`.</span></span>

### <a name="notes"></a><span data-ttu-id="3463e-159">Observações</span><span class="sxs-lookup"><span data-stu-id="3463e-159">Notes</span></span>

<span data-ttu-id="3463e-160">`NotifyFailure()` o tem os seguintes motivos de falha predefinidos:</span><span class="sxs-lookup"><span data-stu-id="3463e-160">`NotifyFailure()` has the following predefined failure reasons:</span></span>

* <span data-ttu-id="3463e-161">`CancelledByUser` o usuário fechou a janela pop-up antes de concluir o fluxo de autenticação.</span><span class="sxs-lookup"><span data-stu-id="3463e-161">`CancelledByUser` the user closed the popup window before completing the authentication flow.</span></span>
* <span data-ttu-id="3463e-162">`FailedToOpenWindow` Não foi possível abrir a janela pop-up.</span><span class="sxs-lookup"><span data-stu-id="3463e-162">`FailedToOpenWindow` the popup window could not be opened.</span></span> <span data-ttu-id="3463e-163">Ao executar o Microsoft Teams em um navegador, isso normalmente significa que a janela foi bloqueada por um bloqueador de pop-up.</span><span class="sxs-lookup"><span data-stu-id="3463e-163">When running Microsoft Teams in a browser, this typically means that the window was blocked by a popup blocker.</span></span>

<span data-ttu-id="3463e-164">Se tiver êxito, você poderá atualizar ou recarregar a página e mostrar o conteúdo relevante para o usuário autenticado agora.</span><span class="sxs-lookup"><span data-stu-id="3463e-164">If successful, you can refresh or reload the page and show content relevant to the now-authenticated user.</span></span> <span data-ttu-id="3463e-165">Se a autenticação falhar, exiba uma mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="3463e-165">If authentication fails, display an error message.</span></span>

<span data-ttu-id="3463e-166">Seu aplicativo pode definir seu próprio cookie de sessão para que o usuário não precise entrar novamente quando retornar à sua guia no dispositivo atual.</span><span class="sxs-lookup"><span data-stu-id="3463e-166">Your app can set its own session cookie so that the user need not sign in again when they return to your tab on the current device.</span></span>

> [!NOTE]
> <span data-ttu-id="3463e-167">O Chrome 80, agendado para lançamento no início de 2020, apresenta novos valores de cookie e impõe políticas de cookies por padrão.</span><span class="sxs-lookup"><span data-stu-id="3463e-167">Chrome 80, scheduled for release in early 2020, introduces new cookie values and imposes cookie policies by default.</span></span> <span data-ttu-id="3463e-168">É recomendável que você defina o uso pretendido para seus cookies, em vez de confiar no comportamento padrão do navegador.</span><span class="sxs-lookup"><span data-stu-id="3463e-168">It's recommended that you set the intended use for your cookies rather than rely on default browser behavior.</span></span> <span data-ttu-id="3463e-169">*Confira* o [atributo SameSite cookie (atualização 2020)](../../../resources/samesite-cookie-update.md).</span><span class="sxs-lookup"><span data-stu-id="3463e-169">*See* [SameSite cookie attribute (2020 update)](../../../resources/samesite-cookie-update.md).</span></span>

>[!NOTE]
><span data-ttu-id="3463e-170">Para obter o token correto para os usuários gratuitos e convidados do Microsoft Teams, é importante que os aplicativos usem o ponto de extremidade específico do locatário https://login.microsoftonline.com/ **{tenantid}**.</span><span class="sxs-lookup"><span data-stu-id="3463e-170">To get the correct token for Microsoft Teams Free and guest users, it is important that the apps use tenant specific endpoint https://login.microsoftonline.com/**{tenantId}**.</span></span> <span data-ttu-id="3463e-171">Você pode obter tenantid da mensagem do bot ou do contexto da guia.</span><span class="sxs-lookup"><span data-stu-id="3463e-171">You can get tenantId from the bot message or tab context.</span></span> <span data-ttu-id="3463e-172">Se os aplicativos usarem https://login.microsoftonline.com/common , os usuários receberão tokens incorretos e farão logon no locatário "Home", em vez do locatário que estão atualmente conectados.</span><span class="sxs-lookup"><span data-stu-id="3463e-172">If the apps use https://login.microsoftonline.com/common, the users will get incorrect tokens and will log on to the "home" tenant instead of the tenant that they are currently signed into.</span></span>

<span data-ttu-id="3463e-173">Para obter mais informações sobre logon único (SSO), confira o artigo [autenticação silenciosa](~/tabs/how-to/authentication/auth-silent-AAD.md).</span><span class="sxs-lookup"><span data-stu-id="3463e-173">For more information on Single Sign-On (SSO) see the article [Silent authentication](~/tabs/how-to/authentication/auth-silent-AAD.md).</span></span>

## <a name="samples"></a><span data-ttu-id="3463e-174">Exemplos</span><span class="sxs-lookup"><span data-stu-id="3463e-174">Samples</span></span>

<span data-ttu-id="3463e-175">Para obter um exemplo de código mostrando o processo de autenticação de guia usando o Azure AD, confira:</span><span class="sxs-lookup"><span data-stu-id="3463e-175">For sample code showing the tab authentication process using Azure AD see:</span></span>

* [<span data-ttu-id="3463e-176">Exemplo de autenticação de guia do Microsoft Teams (nó)</span><span class="sxs-lookup"><span data-stu-id="3463e-176">Microsoft Teams tab authentication sample (Node)</span></span>](https://github.com/OfficeDev/microsoft-teams-sample-auth-node)
