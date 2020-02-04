---
title: Usando o serviço de bot do Azure para autenticação no Microsoft Teams
description: Descreve o serviço do Azure bot OAuthCard e como ele é usado para autenticação
keywords: OAuthCard de autenticação do Microsoft Teams serviço de bot do Azure de cartões OAuth
ms.openlocfilehash: 0397c45b39470d97c1158b2681462038de618a39
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672759"
---
# <a name="using-azure-bot-service-for-authentication-in-teams"></a><span data-ttu-id="27638-104">Usando o serviço de bot do Azure para autenticação no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="27638-104">Using Azure Bot Service for Authentication in Teams</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="27638-105">Sem o OAuthCard do serviço de bot do Azure, é complicado implementar a autenticação em um bot.</span><span class="sxs-lookup"><span data-stu-id="27638-105">Without the Azure Bot Service’s OAuthCard it is complicated to implement authentication in a bot.</span></span> <span data-ttu-id="27638-106">É um desafio de pilha total que envolve a criação de uma experiência da Web, a integração com provedores OAuth externos, o gerenciamento de tokens e a manipulação das chamadas de API de servidor para servidor certas para concluir o fluxo de autenticação com segurança.</span><span class="sxs-lookup"><span data-stu-id="27638-106">It is a full-stack challenge that involving building a web experience, integrating with external OAuth providers, token management, and handling the right server-to-server API calls to complete authentication flow securely.</span></span> <span data-ttu-id="27638-107">Isso pode resultar em experiências do clunky que exijam a entrada de "números mágicos".</span><span class="sxs-lookup"><span data-stu-id="27638-107">This can result in clunky experiences requiring the entry of “magic numbers”.</span></span>

<span data-ttu-id="27638-108">Com o OAuthCard do serviço do Azure bot, é mais fácil para o bot do Microsoft Teams assinar seus usuários e acessar provedores de dados externos.</span><span class="sxs-lookup"><span data-stu-id="27638-108">With Azure Bot Service’s OAuthCard, it is easier for your Teams bot to sign in your users and access external data providers.</span></span> <span data-ttu-id="27638-109">Se você já implementou a autenticação e deseja alternar para algo mais simples, ou se você está procurando adicionar autenticação ao serviço de bot pela primeira vez, o OAuthCard pode facilitar.</span><span class="sxs-lookup"><span data-stu-id="27638-109">Whether you’ve already implemented auth and you want to switch over to something simpler, or if you are looking to add authentication to your bot service for the first time, the OAuthCard can make it easier.</span></span>

<span data-ttu-id="27638-110">Outros tópicos da [autenticação](~/resources/bot-v3/bot-authentication/auth-flow-bot.md) descrevem a autenticação sem usar o OAuthCard, portanto, se você quiser entender a autenticação no Microsoft Teams mais profundamente ou se tiver uma situação em que não possa usar o OAuthCard, ainda poderá fazer referência a esses tópicos.</span><span class="sxs-lookup"><span data-stu-id="27638-110">Other topics in [Authentication](~/resources/bot-v3/bot-authentication/auth-flow-bot.md) describe authentication without using the OAuthCard, so if you want to understand authentication in Teams more deeply, or have a situation where you can not use the OAuthCard, you can still refer to those topics.</span></span>

## <a name="support-for-the-oauthcard"></a><span data-ttu-id="27638-111">Suporte para o OAuthCard</span><span class="sxs-lookup"><span data-stu-id="27638-111">Support for the OAuthCard</span></span>

<span data-ttu-id="27638-112">No momento, há algumas restrições para onde você pode usar o OAuthCard.</span><span class="sxs-lookup"><span data-stu-id="27638-112">There are currently some restrictions to where you can use the OAuthCard.</span></span> <span data-ttu-id="27638-113">Entre elas:</span><span class="sxs-lookup"><span data-stu-id="27638-113">These include:</span></span>

* <span data-ttu-id="27638-114">O cartão não funcionará com [acesso de convidado](/MicrosoftTeams/guest-access)</span><span class="sxs-lookup"><span data-stu-id="27638-114">The card will not work with [guest access](/MicrosoftTeams/guest-access)</span></span>
* <span data-ttu-id="27638-115">Ele não funcionará com [o Microsoft Teams gratuitamente](https://products.office.com/microsoft-teams/free)</span><span class="sxs-lookup"><span data-stu-id="27638-115">It will not work with [Microsoft Teams free](https://products.office.com/microsoft-teams/free)</span></span>
* <span data-ttu-id="27638-116">Ele só pode ser usado para a autenticação de bot</span><span class="sxs-lookup"><span data-stu-id="27638-116">It can only be used for bot authentication</span></span>
* <span data-ttu-id="27638-117">Ele funciona apenas para bots registrados no [serviço do Azure bot](https://azure.microsoft.com/services/bot-service/)</span><span class="sxs-lookup"><span data-stu-id="27638-117">It only works for bots registered in the [Azure Bot Service](https://azure.microsoft.com/services/bot-service/)</span></span>

## <a name="how-does-the-azure-bot-service-help-me-do-authentication"></a><span data-ttu-id="27638-118">Como o serviço do Azure bot ajuda a fazer a autenticação?</span><span class="sxs-lookup"><span data-stu-id="27638-118">How does the Azure Bot Service help me do authentication?</span></span>

<span data-ttu-id="27638-119">A documentação completa usando o OAuthCard está disponível no tópico: [Adicionar autenticação ao bot por meio do serviço de bot do Azure](/azure/bot-service/bot-builder-tutorial-authentication?view=azure-bot-service-3.0).</span><span class="sxs-lookup"><span data-stu-id="27638-119">Full documentation using the OAuthCard is available in the topic: [Add authentication to your bot via Azure Bot Service](/azure/bot-service/bot-builder-tutorial-authentication?view=azure-bot-service-3.0).</span></span> <span data-ttu-id="27638-120">Observe que este tópico está no conjunto de documentação do Azure bot Framework e não é específico para o Teams.</span><span class="sxs-lookup"><span data-stu-id="27638-120">Note that this topic is in the Azure Bot Framework documentation set, and is not specific to Teams.</span></span>

<span data-ttu-id="27638-121">As seções a seguir explicam como usar o OAuthCard no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="27638-121">The following sections tell how to use the OAuthCard in Teams.</span></span>

## <a name="main-benefits-for-teams-developers"></a><span data-ttu-id="27638-122">Principais benefícios para desenvolvedores de equipes</span><span class="sxs-lookup"><span data-stu-id="27638-122">Main benefits for Teams developers</span></span>

<span data-ttu-id="27638-123">O OAuthCard ajuda com a autenticação das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="27638-123">The OAuthCard helps with authentication in the following ways:</span></span>

* <span data-ttu-id="27638-124">Fornece um fluxo de autenticação sem uso baseado na Web: você não precisa mais escrever e hospedar uma página da Web para direcionar as experiências de login externas ou fornecer um redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="27638-124">Provides an out-of-box web-based authentication flow: you no longer have to write and host a web page to direct to external login experiences or provide a redirect.</span></span>
* <span data-ttu-id="27638-125">O é perfeito para usuários finais: conclua a experiência de entrada completa no Teams.</span><span class="sxs-lookup"><span data-stu-id="27638-125">Is seamless for end users: complete the full sign in experience right within Teams.</span></span>
* <span data-ttu-id="27638-126">Inclui o gerenciamento fácil de tokens: você não precisa mais implementar um sistema de armazenamento de token – em vez disso, o serviço bot cuida do cache de token e fornece um mecanismo seguro para buscar esses tokens.</span><span class="sxs-lookup"><span data-stu-id="27638-126">Includes easy token management: you no longer have to implement a token storage system – instead, the Bot Service takes care of token caching and provides a secure mechanism for fetching those tokens.</span></span>
* <span data-ttu-id="27638-127">O é suportado por SDKs completos: fácil de integrar e consumir do serviço de bot.</span><span class="sxs-lookup"><span data-stu-id="27638-127">Is supported by complete SDKs: easy to integrate and consume from your bot service.</span></span>
* <span data-ttu-id="27638-128">Tem suporte pronto para vários provedores OAuth populares, como o Azure AD/MSA, Facebook e Google.</span><span class="sxs-lookup"><span data-stu-id="27638-128">Has out-of-box support for many popular OAuth providers, such as Azure AD/MSA, Facebook, and Google.</span></span>

## <a name="when-should-i-implement-my-own-solution"></a><span data-ttu-id="27638-129">Quando devo implementar minha própria solução?</span><span class="sxs-lookup"><span data-stu-id="27638-129">When should I implement my own solution?</span></span>

<span data-ttu-id="27638-130">Como os tokens de acesso são informações confidenciais, talvez você não queira armazená-los em um serviço externo.</span><span class="sxs-lookup"><span data-stu-id="27638-130">Because access tokens are sensitive information, you may not wish to have them stored in an external service.</span></span> <span data-ttu-id="27638-131">Nesse caso, você pode optar por ainda implementar seu próprio sistema de gerenciamento de tokens e a experiência de logon no Teams, conforme descrito no restante dos tópicos de [autenticação](~/resources/bot-v3/bot-authentication/auth-flow-bot.md) do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="27638-131">In this case, you may choose to still implement your own token management system and login experience within Teams, as described in the rest of the Teams [Authentication](~/resources/bot-v3/bot-authentication/auth-flow-bot.md) topics.</span></span>

## <a name="getting-started-with-oauthcard-in-teams"></a><span data-ttu-id="27638-132">Introdução ao OAuthCard no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="27638-132">Getting started with OAuthCard in Teams</span></span>

> [!NOTE]
> <span data-ttu-id="27638-133">Este guia está usando o SDK da estrutura de bot v3.</span><span class="sxs-lookup"><span data-stu-id="27638-133">This guide is using the Bot Framework v3 SDK.</span></span> <span data-ttu-id="27638-134">Você pode encontrar a implementação v4 [aqui](/azure/bot-service/bot-builder-authentication?view=azure-bot-service-4.0&tabs=csharp).</span><span class="sxs-lookup"><span data-stu-id="27638-134">You can find the v4 implementation [here](/azure/bot-service/bot-builder-authentication?view=azure-bot-service-4.0&tabs=csharp).</span></span> <span data-ttu-id="27638-135">Você ainda precisará criar um manifesto e incluir token.botframework.com na `validDomains` seção, pois, caso contrário, o botão entrar não abrirá a janela de autenticação.</span><span class="sxs-lookup"><span data-stu-id="27638-135">You will still need to create a manifest and include token.botframework.com in the `validDomains` section, because otherwise the Sign in button will not open the authentication window.</span></span> <span data-ttu-id="27638-136">Use o [app Studio](~/concepts/build-and-test/app-studio-overview.md) para gerar seu manifesto.</span><span class="sxs-lookup"><span data-stu-id="27638-136">Use the [App Studio](~/concepts/build-and-test/app-studio-overview.md) to generate your manifest.</span></span>

<span data-ttu-id="27638-137">Primeiro, você precisará configurar o serviço do Azure bot para configurar os provedores de autenticação externa.</span><span class="sxs-lookup"><span data-stu-id="27638-137">You’ll first need to configure your Azure bot service to set up external authentication providers.</span></span> <span data-ttu-id="27638-138">Leia [Configuring Identity Providers](~/concepts/authentication/configure-identity-provider.md) for detailed etapas.</span><span class="sxs-lookup"><span data-stu-id="27638-138">Read [Configuring identity providers](~/concepts/authentication/configure-identity-provider.md) for detailed steps.</span></span>

<span data-ttu-id="27638-139">Para habilitar a autenticação usando o serviço do Azure bot, você precisará fazer essas inclusões no seu código:</span><span class="sxs-lookup"><span data-stu-id="27638-139">To enable authentication using the Azure Bot Service, you need to make these additions to your code:</span></span>

1. <span data-ttu-id="27638-140">Inclua token.botframework.com na `validDomains` seção do manifesto do aplicativo, pois o Teams incorporará a página de logon do serviço de bot.</span><span class="sxs-lookup"><span data-stu-id="27638-140">Include token.botframework.com in the `validDomains` section of your app manifest because Teams will embed the Bot Service’s login page.</span></span>
2. <span data-ttu-id="27638-141">Busque o token do serviço bot sempre que seu bot precisar acessar os recursos autenticados.</span><span class="sxs-lookup"><span data-stu-id="27638-141">Fetch the token from the Bot Service whenever your bot needs to access authenticated resources.</span></span> <span data-ttu-id="27638-142">Se nenhum token estiver disponível, envie uma mensagem com um OAuthCard para que o usuário solicite o logon no serviço externo.</span><span class="sxs-lookup"><span data-stu-id="27638-142">If no token is available, send a message with an OAuthCard to the user requesting them to log into the external service.</span></span>
3. <span data-ttu-id="27638-143">Manipular a atividade de conclusão de logon.</span><span class="sxs-lookup"><span data-stu-id="27638-143">Handle the login completion activity.</span></span> <span data-ttu-id="27638-144">Isso garante que a solicitação de autenticação e o token estejam associados ao usuário que está interagindo atualmente com seu bot.</span><span class="sxs-lookup"><span data-stu-id="27638-144">This ensures that the authentication request and the token are associated with the user currently interacting with your bot.</span></span>
4. <span data-ttu-id="27638-145">Recupere o token sempre que o bot precisar executar ações autenticadas, como chamar APIs REST externas.</span><span class="sxs-lookup"><span data-stu-id="27638-145">Retrieve the token whenever your bot needs to perform authenticated actions, such as calling external REST APIs.</span></span>

<span data-ttu-id="27638-146">No seu código de caixa de diálogo, você precisará adicionar este trecho de código (C#), que verifica um token de acesso existente:</span><span class="sxs-lookup"><span data-stu-id="27638-146">In your dialog code, you’ll need to add this snippet (C#), which checks for an existing access token:</span></span>

```CSharp
// First ask Bot Service if it already has a token for this user
var token = await context.GetUserTokenAsync(ConnectionName).ConfigureAwait(false);
if (token != null)
{
    // use the token to do exciting things!
}
else
{
    // If Bot Service does not have a token, send an OAuth card to sign in 
    await SendOAuthCardAsync(context, (Activity)context.Activity);
}
```

<span data-ttu-id="27638-147">Se não houver um token de acesso, seu código enviará uma mensagem com um OAuthCard para o usuário:</span><span class="sxs-lookup"><span data-stu-id="27638-147">If an access token doesn’t exist, your code will then send a message with an OAuthCard to the user:</span></span>

```CSharp
private async Task SendOAuthCardAsync(IDialogContext context, Activity activity)
{
    await context.PostAsync($"To do this, you'll first need to sign in.");

    var reply = await context.Activity.CreateOAuthReplyAsync(_connectionName, _signInMessage, _buttonLabel).ConfigureAwait(false);
    await context.PostAsync(reply);

    context.Wait(WaitForToken);
}
```

<span data-ttu-id="27638-148">Para lidar com a atividade de logon concluído, você precisará processar essa invocação:</span><span class="sxs-lookup"><span data-stu-id="27638-148">To handle the login complete activity, you’ll need to process this Invoke:</span></span>

```CSharp
if (activity.Name == "signin/verifyState")
{
  // We do this so that we can pass handling to the right logic in the dialog. You can
  // set this to be whatever string you want.
  activity.Text = "loginComplete";
  await Conversation.SendAsync(activity, () => new Dialogs.RootDialog());

  return Request.CreateResponse(HttpStatusCode.OK);
}
```

<span data-ttu-id="27638-149">No seu código de caixa de diálogo, você pode recuperar o token do serviço de autenticação do bot:</span><span class="sxs-lookup"><span data-stu-id="27638-149">In your dialog code, you can then retrieve the token from the Bot authentication service:</span></span>

```CSharp
if (text.Contains("loginComplete"))
  {
    // Handle login completion event.
    JObject ctx = activity.Value as JObject;

    if (ctx != null)
    {
      string code = ctx["state"].ToString();

      var oauthClient = activity.GetOAuthClient();
      var token = await oauthClient.OAuthApi.GetUserTokenAsync(activity.From.Id, ConnectionName, magicCode: code).ConfigureAwait(false);
      if (token != null)
      {
        // Make whatever API calls here you want
        await context.PostAsync($"Success! You are now signed in.");
      }
    }
  // Need to respond to the Invoke.
  return;
}
```

## <a name="using-oauthcard-with-messaging-extensions"></a><span data-ttu-id="27638-150">Usando o OAuthCard com extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="27638-150">Using OAuthCard with messaging extensions</span></span>

<span data-ttu-id="27638-151">Você também pode usar o serviço do Azure bot para conectar provedores de terceiros à sua extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="27638-151">You can also use Azure Bot Service to connect third-party providers to your messaging extension.</span></span> <span data-ttu-id="27638-152">O fluxo é o mesmo que com um bot, exceto em vez de retornar um OAuthCard, o serviço retornará um prompt de logon.</span><span class="sxs-lookup"><span data-stu-id="27638-152">The flow is the same as with a bot, except instead of returning an OAuthCard, your service will return a login prompt.</span></span>

<span data-ttu-id="27638-153">O trecho a seguir (C#) ilustra como criar a resposta de logon:</span><span class="sxs-lookup"><span data-stu-id="27638-153">The following snippet (C#) illustrates how to craft the login response:</span></span>

```CSharp
var token = await client.OAuthApi.GetUserTokenAsync(activity.From.Id, ConnectionName).ConfigureAwait(false);

if (token == null)
{
  // Send the login response with the auth link.
  string link = await client.OAuthApi.GetSignInLinkAsync(activity, ConnectionName);

  response = new ComposeExtensionResponse()
  {
    ComposeExtension = new ComposeExtensionResult()
  };
  response.ComposeExtension.Type = "auth";
  response.ComposeExtension.SuggestedActions = new ComposeExtensionSuggestedAction()
  {
    Actions = new List<CardAction>()
      {
        new CardAction(ActionTypes.OpenUrl, title: "Sign into this app", value: link)
      }
    };
  return response;
}
```

<span data-ttu-id="27638-154">Observe que, no exemplo acima, você precisa fazer a chamada `GetSignInLinkAsync` diretamente em relação à `client.OAuthApi` propriedade.</span><span class="sxs-lookup"><span data-stu-id="27638-154">Note that in the example above you need to make the call to `GetSignInLinkAsync` directly against the `client.OAuthApi` property.</span></span>

<span data-ttu-id="27638-155">Quando o usuário concluir a sequência de logon com êxito, o serviço receberá outra solicitação de chamada que contém a consulta de usuário original, juntamente com uma cadeia de caracteres de parâmetro de estado que contém o "código mágico".</span><span class="sxs-lookup"><span data-stu-id="27638-155">When the user successfully completes the login sequence, your service will receive another Invoke request containing the original user query, along with a state parameter string containing the “magic code”.</span></span> <span data-ttu-id="27638-156">Agora você pode buscar o token usando essa cadeia de caracteres, juntamente com a ID de usuário e o nome da conexão.</span><span class="sxs-lookup"><span data-stu-id="27638-156">You can now fetch the token using this string, along with the user ID and connection name.</span></span>

```CSharp
var query = activity.GetComposeExtensionQueryData();
JObject data = activity.Value as JObject;

var client = activity.GetOAuthClient();

// Check if the request comes with login state
if (data != null && data["state"] != null)
{
  var token = await client.OAuthApi.GetUserTokenAsync(activity.From.Id, ConnectionName, data["state"].ToString());

  // Do stuff with the token here.

}
```
