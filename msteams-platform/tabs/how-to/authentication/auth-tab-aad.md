---
title: Autenticação para guias usando o Azure Active Directory
description: Descreve a autenticação no Teams e como usá-la em guias
ms.topic: how-to
keywords: guias de autenticação do teams AAD
ms.openlocfilehash: f2429653fe875406870ba82e27fce3d643ff69f6
ms.sourcegitcommit: dd2220f691029d043aaddfc7c229e332735acb1d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2021
ms.locfileid: "51995901"
---
# <a name="authenticate-a-user-in-a-microsoft-teams-tab"></a><span data-ttu-id="a7447-104">Autenticar um usuário em uma guia do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="a7447-104">Authenticate a user in a Microsoft Teams tab</span></span>

> [!Note]
> <span data-ttu-id="a7447-105">Para que a autenticação funcione para sua guia em clientes móveis, você precisa garantir que esteja usando a versão 1.4.1 ou posterior do SDK JavaScript do Teams.</span><span class="sxs-lookup"><span data-stu-id="a7447-105">For authentication to work for your tab on mobile clients, you need to ensure you're using version 1.4.1 or later of the Teams JavaScript SDK.</span></span>

<span data-ttu-id="a7447-106">Há muitos serviços que você pode querer consumir dentro do seu aplicativo do Teams, e a maioria desses serviços exige autenticação e autorização para obter acesso ao serviço.</span><span class="sxs-lookup"><span data-stu-id="a7447-106">There are many services that you may wish to consume inside your Teams app, and most of those services require authentication and authorization to get access to the service.</span></span> <span data-ttu-id="a7447-107">Os serviços incluem Facebook, Twitter e, claro, o Teams.</span><span class="sxs-lookup"><span data-stu-id="a7447-107">Services include Facebook, Twitter, and of course Teams.</span></span> <span data-ttu-id="a7447-108">Os usuários do Teams têm informações de perfil de usuário armazenadas no Azure Active Directory (Azure AD) usando o Microsoft Graph e este artigo se concentrará na autenticação usando o Azure AD para obter acesso a essas informações.</span><span class="sxs-lookup"><span data-stu-id="a7447-108">Users of Teams have user profile information stored in Azure Active Directory (Azure AD) using Microsoft Graph and this article will focus on authentication using Azure AD to get access to this information.</span></span>

<span data-ttu-id="a7447-109">OAuth 2.0 é um padrão aberto para autenticação usado pelo Azure AD e muitos outros provedores de serviços.</span><span class="sxs-lookup"><span data-stu-id="a7447-109">OAuth 2.0 is an open standard for authentication used by Azure AD and many other service providers.</span></span> <span data-ttu-id="a7447-110">Noções básicas sobre o OAuth 2.0 é um pré-requisito para trabalhar com autenticação no Teams e no Azure AD.</span><span class="sxs-lookup"><span data-stu-id="a7447-110">Understanding OAuth 2.0 is a prerequisite for working with authentication in Teams and Azure AD.</span></span> <span data-ttu-id="a7447-111">Os exemplos a seguir usam o fluxo de Concessão Implícita OAuth 2.0 com o objetivo de, eventualmente, ler as informações de perfil do usuário do Azure AD e do Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="a7447-111">The examples below use the OAuth 2.0 Implicit Grant flow with the goal of eventually reading the user's profile information from Azure AD and Microsoft Graph.</span></span>

<span data-ttu-id="a7447-112">O código neste artigo vem do exemplo do aplicativo de exemplo do [Microsoft Teams tab authentication sample (Node)](https://github.com/OfficeDev/microsoft-teams-sample-complete-node).</span><span class="sxs-lookup"><span data-stu-id="a7447-112">The code in this article comes from the Teams sample app [Microsoft Teams tab authentication sample (Node)](https://github.com/OfficeDev/microsoft-teams-sample-complete-node).</span></span> <span data-ttu-id="a7447-113">Ele contém uma guia estática que solicita um token de acesso para o Microsoft Graph e mostra as informações básicas de perfil do usuário atual do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="a7447-113">It contains a static tab that requests an access token for Microsoft Graph and shows the current user's basic profile information from Azure AD.</span></span>

<span data-ttu-id="a7447-114">Para uma visão geral do fluxo de autenticação para guias, consulte o tópico [Fluxo de autenticação nas guias](~/tabs/how-to/authentication/auth-flow-tab.md).</span><span class="sxs-lookup"><span data-stu-id="a7447-114">For a general overview of authentication flow for tabs see the topic [Authentication flow in tabs](~/tabs/how-to/authentication/auth-flow-tab.md).</span></span>

<span data-ttu-id="a7447-115">O fluxo de autenticação nas guias difere ligeiramente do fluxo de autenticação nos bots.</span><span class="sxs-lookup"><span data-stu-id="a7447-115">Authentication flow in tabs differs slightly from authentication flow in bots.</span></span>

## <a name="configuring-identity-providers"></a><span data-ttu-id="a7447-116">Configurando provedores de identidade</span><span class="sxs-lookup"><span data-stu-id="a7447-116">Configuring identity providers</span></span>

<span data-ttu-id="a7447-117">Consulte o tópico [Configure identity providers for](~/concepts/authentication/configure-identity-provider.md) detailed steps on configuring OAuth 2.0 callback redirect URL(s) when using Azure Active Directory as an identity provider.</span><span class="sxs-lookup"><span data-stu-id="a7447-117">See the topic [Configure identity providers](~/concepts/authentication/configure-identity-provider.md) for detailed steps on configuring OAuth 2.0 callback redirect URL(s) when using Azure Active Directory as an identity provider.</span></span>

## <a name="initiate-authentication-flow"></a><span data-ttu-id="a7447-118">Iniciar fluxo de autenticação</span><span class="sxs-lookup"><span data-stu-id="a7447-118">Initiate authentication flow</span></span>

<span data-ttu-id="a7447-119">O fluxo de autenticação deve ser disparado por uma ação do usuário.</span><span class="sxs-lookup"><span data-stu-id="a7447-119">Authentication flow should be triggered by a user action.</span></span> <span data-ttu-id="a7447-120">Você não deve abrir o pop-up de autenticação automaticamente porque isso provavelmente disparará o bloqueador pop-up do navegador, bem como confundirá o usuário.</span><span class="sxs-lookup"><span data-stu-id="a7447-120">You should not open the authentication pop-up automatically because this is likely to trigger the browser's pop-up blocker as well as confuse the user.</span></span>

<span data-ttu-id="a7447-121">Adicione um botão à sua configuração ou página de conteúdo para permitir que o usuário entre quando necessário.</span><span class="sxs-lookup"><span data-stu-id="a7447-121">Add a button to your configuration or content page to enable the user to sign in when needed.</span></span> <span data-ttu-id="a7447-122">Isso pode ser feito na página de configuração [de](~/tabs/how-to/create-tab-pages/configuration-page.md) tabulação ou em qualquer [página de](~/tabs/how-to/create-tab-pages/content-page.md) conteúdo.</span><span class="sxs-lookup"><span data-stu-id="a7447-122">This can be done in the tab [configuration](~/tabs/how-to/create-tab-pages/configuration-page.md) page or any [content](~/tabs/how-to/create-tab-pages/content-page.md) page.</span></span>

<span data-ttu-id="a7447-123">O Azure AD, como a maioria dos provedores de identidade, não permite que seu conteúdo seja colocado em um iframe.</span><span class="sxs-lookup"><span data-stu-id="a7447-123">Azure AD, like most identity providers, does not allow its content to be placed in an iframe.</span></span> <span data-ttu-id="a7447-124">Isso significa que você precisará adicionar uma página pop-up para hospedar o provedor de identidade.</span><span class="sxs-lookup"><span data-stu-id="a7447-124">This means that you will need to add a pop-up page to host the identity provider.</span></span> <span data-ttu-id="a7447-125">No exemplo a seguir, esta página é `/tab-auth/simple-start` .</span><span class="sxs-lookup"><span data-stu-id="a7447-125">In the following example this page is `/tab-auth/simple-start`.</span></span> <span data-ttu-id="a7447-126">Use a `microsoftTeams.authenticate()` função do SDK do cliente do Microsoft Teams para iniciar esta página quando o botão estiver selecionado.</span><span class="sxs-lookup"><span data-stu-id="a7447-126">Use the `microsoftTeams.authenticate()` function of the Microsoft Teams client SDK to launch this page when your button is selected.</span></span>

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

### <a name="notes"></a><span data-ttu-id="a7447-127">Observações</span><span class="sxs-lookup"><span data-stu-id="a7447-127">Notes</span></span>

* <span data-ttu-id="a7447-128">A URL que você passa `microsoftTeams.authentication.authenticate()` é a página inicial do fluxo de autenticação.</span><span class="sxs-lookup"><span data-stu-id="a7447-128">The URL you pass to `microsoftTeams.authentication.authenticate()` is the start page of the authentication flow.</span></span> <span data-ttu-id="a7447-129">Neste exemplo, que é `/tab-auth/simple-start` .</span><span class="sxs-lookup"><span data-stu-id="a7447-129">In this example that is `/tab-auth/simple-start`.</span></span> <span data-ttu-id="a7447-130">Isso deve corresponder ao que você registrou no Portal de Registro de Aplicativos [do Azure AD.](https://apps.dev.microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="a7447-130">This should match what you registered in the [Azure AD Application Registration Portal](https://apps.dev.microsoft.com).</span></span>

* <span data-ttu-id="a7447-131">O fluxo de autenticação deve começar em uma página que está em seu domínio.</span><span class="sxs-lookup"><span data-stu-id="a7447-131">Authentication flow must start on a page that's on your domain.</span></span> <span data-ttu-id="a7447-132">Esse domínio também deve ser listado [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) na seção do manifesto.</span><span class="sxs-lookup"><span data-stu-id="a7447-132">This domain should also be listed in the [`validDomains`](~/resources/schema/manifest-schema.md#validdomains) section of the manifest.</span></span> <span data-ttu-id="a7447-133">A falha ao fazer isso resultará em um pop-up vazio.</span><span class="sxs-lookup"><span data-stu-id="a7447-133">Failure to do so will result in an empty pop-up.</span></span>

* <span data-ttu-id="a7447-134">A falha ao usar causará um problema com o pop-up não fechar `microsoftTeams.authentication.authenticate()` no final do processo de login.</span><span class="sxs-lookup"><span data-stu-id="a7447-134">Failing to use `microsoftTeams.authentication.authenticate()` will cause a problem with the popup not closing at the end of the sign in process.</span></span>

## <a name="navigate-to-the-authorization-page-from-your-popup-page"></a><span data-ttu-id="a7447-135">Navegue até a página de autorização de sua página pop-up</span><span class="sxs-lookup"><span data-stu-id="a7447-135">Navigate to the authorization page from your popup page</span></span>

<span data-ttu-id="a7447-136">Quando sua página pop-up ( ) é `/tab-auth/simple-start` exibida, o código a seguir é executado.</span><span class="sxs-lookup"><span data-stu-id="a7447-136">When your popup page (`/tab-auth/simple-start`) is displayed the following code is run.</span></span> <span data-ttu-id="a7447-137">O principal objetivo desta página é redirecionar para seu provedor de identidade para que o usuário possa entrar.</span><span class="sxs-lookup"><span data-stu-id="a7447-137">The main goal of this page is to redirect to your identity provider so the user can sign in.</span></span> <span data-ttu-id="a7447-138">Esse redirecionamento pode ser feito no lado do servidor usando HTTP 302, mas, nesse caso, ele é feito no lado do cliente usando com uma chamada para `window.location.assign()` .</span><span class="sxs-lookup"><span data-stu-id="a7447-138">This redirection could be done on the server side using HTTP 302, but in this case it is done on the client side using with a call to `window.location.assign()`.</span></span> <span data-ttu-id="a7447-139">Isso também permite ser usado para recuperar informações sugestões que `microsoftTeams.getContext()` podem ser passadas para o Azure AD.</span><span class="sxs-lookup"><span data-stu-id="a7447-139">This also allows `microsoftTeams.getContext()` to be used to retrieve hinting information which can be passed to Azure AD.</span></span>

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

<span data-ttu-id="a7447-140">Depois que o usuário concluir a autorização, o usuário será redirecionado para a página de retorno de chamada especificada para seu aplicativo em `/tab-auth/simple-end` .</span><span class="sxs-lookup"><span data-stu-id="a7447-140">After the user completes authorization, the user is redirected to the callback page you specified for your app at `/tab-auth/simple-end`.</span></span>

### <a name="notes"></a><span data-ttu-id="a7447-141">Observações</span><span class="sxs-lookup"><span data-stu-id="a7447-141">Notes</span></span>

* <span data-ttu-id="a7447-142">Consulte [obter informações de contexto do usuário](~/tabs/how-to/access-teams-context.md) para ajudar a criar solicitações de autenticação e URLs.</span><span class="sxs-lookup"><span data-stu-id="a7447-142">See [get user context information](~/tabs/how-to/access-teams-context.md) for help building authentication requests and URLs.</span></span> <span data-ttu-id="a7447-143">Por exemplo, você pode usar o nome de logon do usuário como o valor para a logon do Azure AD, o que significa que o usuário pode precisar `login_hint` digitar menos.</span><span class="sxs-lookup"><span data-stu-id="a7447-143">For example, you can use the user's login name as the `login_hint` value for Azure AD sign-in, which means the user might need to type less.</span></span> <span data-ttu-id="a7447-144">Lembre-se de que você não deve usar esse contexto diretamente como prova de identidade, pois um invasor pode carregar sua página em um navegador mal-intencionado e fornecer todas as informações que quiser.</span><span class="sxs-lookup"><span data-stu-id="a7447-144">Remember that you should not use this context directly as proof of identity since an attacker could load your page in a malicious browser and provide it with any information they want.</span></span>
* <span data-ttu-id="a7447-145">Embora o contexto de guia fornece informações úteis sobre o usuário, não use essas informações para autenticar o usuário se você as recebe como parâmetros de URL para a URL de conteúdo da guia ou chamando a função no SDK do cliente do `microsoftTeams.getContext()` Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="a7447-145">Although the tab context provides useful information regarding the user, don't use this information to authenticate the user whether you get it as URL parameters to your tab content URL or by calling the `microsoftTeams.getContext()` function in the Microsoft Teams client SDK.</span></span> <span data-ttu-id="a7447-146">Um ator mal-intencionado poderia invocar sua URL de conteúdo de tabulação com seus próprios parâmetros, e uma página da Web que representa o Microsoft Teams poderia carregar sua URL de conteúdo de tabulação em um iframe e retornar seus próprios dados para a `getContext()` função.</span><span class="sxs-lookup"><span data-stu-id="a7447-146">A malicious actor could invoke your tab content URL with its own parameters, and a web page impersonating Microsoft Teams could load your tab content URL in an iframe and return its own data to the `getContext()` function.</span></span> <span data-ttu-id="a7447-147">Você deve tratar as informações relacionadas à identidade no contexto da guia simplesmente como dicas e validá-las antes de usá-las.</span><span class="sxs-lookup"><span data-stu-id="a7447-147">You should treat the identity-related information in the tab context simply as hints and validate them before use.</span></span>
* <span data-ttu-id="a7447-148">O parâmetro é usado para confirmar se o serviço que chama o URI de retorno de `state` chamada é o serviço chamado.</span><span class="sxs-lookup"><span data-stu-id="a7447-148">The `state` parameter is used to confirm that the service calling the callback URI is the service you called.</span></span> <span data-ttu-id="a7447-149">Se o parâmetro no retorno de chamada não corresponder ao parâmetro enviado durante a chamada, a chamada de retorno não será verificada e `state` deverá ser encerrada.</span><span class="sxs-lookup"><span data-stu-id="a7447-149">If the `state` parameter in the callback does not match the parameter you sent during the call the return call is not verified and should be terminated.</span></span>
* <span data-ttu-id="a7447-150">Não é necessário incluir o domínio do provedor de identidade na lista no arquivo `validDomains` manifest.jsno aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a7447-150">It is not necessary to include the identity provider's domain in the `validDomains` list in the app's manifest.json file.</span></span>

## <a name="the-callback-page"></a><span data-ttu-id="a7447-151">A página de retorno de chamada</span><span class="sxs-lookup"><span data-stu-id="a7447-151">The callback page</span></span>

<span data-ttu-id="a7447-152">Na última seção, você chamou o serviço de autorização do Azure AD e passou informações de usuário e aplicativo para que o Azure AD pudesse apresentar ao usuário sua própria experiência de autorização monolítica.</span><span class="sxs-lookup"><span data-stu-id="a7447-152">In the last section you called the Azure AD authorization service and passed in user and app information so that Azure AD could present the user with its own monolithic authorization experience.</span></span> <span data-ttu-id="a7447-153">Seu aplicativo não tem controle sobre o que acontece nesta experiência.</span><span class="sxs-lookup"><span data-stu-id="a7447-153">Your app has no control over what happens in this experience.</span></span> <span data-ttu-id="a7447-154">Tudo o que ele sabe é o que é retornado quando o Azure AD chama a página de retorno de chamada que você forneceu ( `/tab-auth/simple-end` ).</span><span class="sxs-lookup"><span data-stu-id="a7447-154">All it knows is what is returned when Azure AD calls the  callback page that you provided (`/tab-auth/simple-end`).</span></span>

<span data-ttu-id="a7447-155">Nesta página, você precisa determinar o sucesso ou a falha com base nas informações retornadas pelo Azure AD e chamada `microsoftTeams.authentication.notifySuccess()` ou `microsoftTeams.authentication.notifyFailure()` .</span><span class="sxs-lookup"><span data-stu-id="a7447-155">In this page you need to determine success or failure based on the information returned by Azure AD and call `microsoftTeams.authentication.notifySuccess()` or `microsoftTeams.authentication.notifyFailure()`.</span></span> <span data-ttu-id="a7447-156">Se o logon tiver sido bem-sucedido, você terá acesso aos recursos de serviço.</span><span class="sxs-lookup"><span data-stu-id="a7447-156">If the login was successful you will have access to service resources.</span></span>

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

<span data-ttu-id="a7447-157">Este código faz uma análise dos pares de valores-chave recebidos do Azure AD ao `window.location.hash` usar a `getHashParameters()` função auxiliar.</span><span class="sxs-lookup"><span data-stu-id="a7447-157">This code parses the key-value pairs received from Azure AD in `window.location.hash` using the `getHashParameters()` helper function.</span></span> <span data-ttu-id="a7447-158">Se ele encontrar um , e o valor for o mesmo fornecido no início do fluxo de autenticação, ele retornará o token de acesso à guia chamando ; caso contrário, ele relata um erro `access_token` `state` com `notifySuccess()` `notifyFailure()` .</span><span class="sxs-lookup"><span data-stu-id="a7447-158">If it finds an `access_token`, and the `state` value is the same as the one provided at the start of the authentication flow, it returns the access token to the tab by calling `notifySuccess()`; otherwise it reports an error with `notifyFailure()`.</span></span>

### <a name="notes"></a><span data-ttu-id="a7447-159">Observações</span><span class="sxs-lookup"><span data-stu-id="a7447-159">Notes</span></span>

<span data-ttu-id="a7447-160">`NotifyFailure()` tem os seguintes motivos de falha predefinidos:</span><span class="sxs-lookup"><span data-stu-id="a7447-160">`NotifyFailure()` has the following predefined failure reasons:</span></span>

* <span data-ttu-id="a7447-161">`CancelledByUser` o usuário fechou a janela pop-up antes de concluir o fluxo de autenticação.</span><span class="sxs-lookup"><span data-stu-id="a7447-161">`CancelledByUser` the user closed the popup window before completing the authentication flow.</span></span>
* <span data-ttu-id="a7447-162">`FailedToOpenWindow` a janela pop-up não pôde ser aberta.</span><span class="sxs-lookup"><span data-stu-id="a7447-162">`FailedToOpenWindow` the popup window could not be opened.</span></span> <span data-ttu-id="a7447-163">Ao executar o Microsoft Teams em um navegador, isso normalmente significa que a janela foi bloqueada por um bloqueador pop-up.</span><span class="sxs-lookup"><span data-stu-id="a7447-163">When running Microsoft Teams in a browser, this typically means that the window was blocked by a popup blocker.</span></span>

<span data-ttu-id="a7447-164">Se tiver êxito, você poderá atualizar ou recarregar a página e mostrar conteúdo relevante para o usuário autenticado.</span><span class="sxs-lookup"><span data-stu-id="a7447-164">If successful, you can refresh or reload the page and show content relevant to the now-authenticated user.</span></span> <span data-ttu-id="a7447-165">Se a autenticação falhar, exibirá uma mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="a7447-165">If authentication fails, display an error message.</span></span>

<span data-ttu-id="a7447-166">Seu aplicativo pode definir seu próprio cookie de sessão para que o usuário não precise entrar novamente quando retornar à guia no dispositivo atual.</span><span class="sxs-lookup"><span data-stu-id="a7447-166">Your app can set its own session cookie so that the user need not sign in again when they return to your tab on the current device.</span></span>

> [!NOTE]
> <span data-ttu-id="a7447-167">O Chrome 80, agendado para lançamento no início de 2020, introduz novos valores de cookie e impõe políticas de cookie por padrão.</span><span class="sxs-lookup"><span data-stu-id="a7447-167">Chrome 80, scheduled for release in early 2020, introduces new cookie values and imposes cookie policies by default.</span></span> <span data-ttu-id="a7447-168">É recomendável definir o uso pretendido para seus cookies em vez de depender do comportamento padrão do navegador.</span><span class="sxs-lookup"><span data-stu-id="a7447-168">It's recommended that you set the intended use for your cookies rather than rely on default browser behavior.</span></span> <span data-ttu-id="a7447-169">*Consulte* [o atributo cookie SameSite (atualização 2020)](../../../resources/samesite-cookie-update.md).</span><span class="sxs-lookup"><span data-stu-id="a7447-169">*See* [SameSite cookie attribute (2020 update)](../../../resources/samesite-cookie-update.md).</span></span>

>[!NOTE]
><span data-ttu-id="a7447-170">Para obter o token correto para o Microsoft Teams Free e usuários convidados, é importante que os aplicativos usem o ponto de extremidade específico do locatário https://login.microsoftonline.com/ **{tenantId}**.</span><span class="sxs-lookup"><span data-stu-id="a7447-170">To get the correct token for Microsoft Teams Free and guest users, it is important that the apps use tenant specific endpoint https://login.microsoftonline.com/**{tenantId}**.</span></span> <span data-ttu-id="a7447-171">Você pode obter tenantId do contexto de mensagem de bot ou guia.</span><span class="sxs-lookup"><span data-stu-id="a7447-171">You can get tenantId from the bot message or tab context.</span></span> <span data-ttu-id="a7447-172">Se os aplicativos usarem , os usuários receberão tokens incorretos e fazer logoff no locatário "home" em vez do locatário no momento em que estão https://login.microsoftonline.com/common entrando.</span><span class="sxs-lookup"><span data-stu-id="a7447-172">If the apps use https://login.microsoftonline.com/common, the users will get incorrect tokens and will log on to the "home" tenant instead of the tenant that they are currently signed into.</span></span>

<span data-ttu-id="a7447-173">Para obter mais informações sobre o SSO (single Sign-On) consulte o artigo [Autenticação silenciosa](~/tabs/how-to/authentication/auth-silent-AAD.md).</span><span class="sxs-lookup"><span data-stu-id="a7447-173">For more information on Single Sign-On (SSO) see the article [Silent authentication](~/tabs/how-to/authentication/auth-silent-AAD.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="a7447-174">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="a7447-174">Code sample</span></span>

<span data-ttu-id="a7447-175">Código de exemplo mostrando o processo de autenticação de tabulação usando o Azure AD:</span><span class="sxs-lookup"><span data-stu-id="a7447-175">Sample code showing the tab authentication process using Azure AD:</span></span>

| <span data-ttu-id="a7447-176">**Exemplo de nome**</span><span class="sxs-lookup"><span data-stu-id="a7447-176">**Sample name**</span></span> | <span data-ttu-id="a7447-177">**description**</span><span class="sxs-lookup"><span data-stu-id="a7447-177">**description**</span></span> | <span data-ttu-id="a7447-178">**.NET**</span><span class="sxs-lookup"><span data-stu-id="a7447-178">**.NET**</span></span> | <span data-ttu-id="a7447-179">**Node.js**</span><span class="sxs-lookup"><span data-stu-id="a7447-179">**Node.js**</span></span> |
|-----------------|-----------------|-------------|
| <span data-ttu-id="a7447-180">Autenticação de tabulação do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="a7447-180">Microsoft Teams tab authentication</span></span> | <span data-ttu-id="a7447-181">Processo de autenticação de tabulação usando o Azure AD.</span><span class="sxs-lookup"><span data-stu-id="a7447-181">Tab authentication process using Azure AD.</span></span> | [<span data-ttu-id="a7447-182">View</span><span class="sxs-lookup"><span data-stu-id="a7447-182">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-channel-group-config-page-auth/csharp) | [<span data-ttu-id="a7447-183">View</span><span class="sxs-lookup"><span data-stu-id="a7447-183">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-auth/nodejs) |
