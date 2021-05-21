---
title: Suporte a SSO para extensões de mensagens
author: KirtiPereira
description: Como habilitar o suporte ao SSO para suas extensões de mensagens
localization_priority: Normal
ms.topic: conceptual
ms.author: surbhigupta
ms.openlocfilehash: 02d08506a07e955693531908f4f3cf16573a02c0
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566198"
---
# <a name="single-sign-on-sso-support-for-messaging-extensions"></a><span data-ttu-id="ea66e-103">Suporte a SSO (login único) para extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="ea66e-103">Single sign-on (SSO) support for messaging extensions</span></span>
 
<span data-ttu-id="ea66e-104">O suporte a um único sign-on agora está disponível para extensões de mensagens e desaparalização de link.</span><span class="sxs-lookup"><span data-stu-id="ea66e-104">Single sign-on support is now available for messaging extensions and link unfurling.</span></span> <span data-ttu-id="ea66e-105">A habilitação do SSO (SSO) para extensões de mensagens atualiza silenciosamente o token de autenticação, o que minimiza o número de vezes que você precisa inserir suas credenciais de entrada para Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="ea66e-105">Enabling Single sign-on (SSO) for messaging extensions silently refreshes the authentication token, which minimizes the number of times you need to enter your sign in credentials for Microsoft Teams.</span></span>

<span data-ttu-id="ea66e-106">Este documento orienta você sobre como habilitar o SSO e armazenar seu token de autenticação, se necessário.</span><span class="sxs-lookup"><span data-stu-id="ea66e-106">This document guides you on how to enable the SSO and store your authentication token, if required.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ea66e-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ea66e-107">Prerequisites</span></span>

<span data-ttu-id="ea66e-108">O pré-requisito para habilitar o SSO para extensões de mensagens e a desassobilização de link são:</span><span class="sxs-lookup"><span data-stu-id="ea66e-108">The prerequisite to enable SSO for messaging extensions and link unfurling are as follows:</span></span>
* <span data-ttu-id="ea66e-109">Você deve ter uma [conta do Azure.](https://azure.microsoft.com/en-us/free/)</span><span class="sxs-lookup"><span data-stu-id="ea66e-109">You must have an [Azure](https://azure.microsoft.com/en-us/free/) account.</span></span>
* <span data-ttu-id="ea66e-110">Você deve configurar seu aplicativo por meio do portal do AAD e atualizar o manifesto do aplicativo Teams para seu bot, conforme definido no registro de seu aplicativo por meio [do portal do AAD.](../../bots/how-to/authentication/auth-aad-sso-bots.md#register-your-app-through-the-aad-portal)</span><span class="sxs-lookup"><span data-stu-id="ea66e-110">You must configure your app through the AAD portal, and update your Teams application manifest for your bot as defined in [register your app through the AAD portal](../../bots/how-to/authentication/auth-aad-sso-bots.md#register-your-app-through-the-aad-portal).</span></span>

> [!NOTE]
> <span data-ttu-id="ea66e-111">Para obter mais informações sobre como criar uma conta do Azure e atualizar o manifesto do aplicativo, consulte Suporte a [SSO (login único) para bots.](../../bots/how-to/authentication/auth-aad-sso-bots.md)</span><span class="sxs-lookup"><span data-stu-id="ea66e-111">For more information on creating an Azure account and updating your app manifest, see [Single sign-on (SSO) support for bots](../../bots/how-to/authentication/auth-aad-sso-bots.md).</span></span>

## <a name="enable-sso-for-messaging-extensions-and-link-unfurling"></a><span data-ttu-id="ea66e-112">Habilitar o SSO para extensões de mensagens e vincular desfraldamento</span><span class="sxs-lookup"><span data-stu-id="ea66e-112">Enable SSO for messaging extensions and link unfurling</span></span>

<span data-ttu-id="ea66e-113">Depois que os pré-requisitos são concluídos, você pode habilitar o SSO para extensões de mensagens e a desarquivamento de link.</span><span class="sxs-lookup"><span data-stu-id="ea66e-113">After the prerequisites are completed, you can enable SSO for messaging extensions and link unfurling.</span></span>

<span data-ttu-id="ea66e-114">**Para habilitar o SSO**</span><span class="sxs-lookup"><span data-stu-id="ea66e-114">**To enable SSO**</span></span>
1. <span data-ttu-id="ea66e-115">Atualize os detalhes da [conexão OAuth de](../../bots/how-to/authentication/auth-aad-sso-bots.md#update-the-azure-portal-with-the-oauth-connection) bots no portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="ea66e-115">Update your bots [OAuth connection](../../bots/how-to/authentication/auth-aad-sso-bots.md#update-the-azure-portal-with-the-oauth-connection) details in the Azure portal.</span></span>
2. <span data-ttu-id="ea66e-116">Baixe o [exemplo de extensões de mensagens](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config) e siga as instruções de instalação fornecidas pelo assistente.</span><span class="sxs-lookup"><span data-stu-id="ea66e-116">Download the [messaging extensions sample](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config) and follow the setup instructions provided by the wizard.</span></span>
   > [!NOTE]
   > <span data-ttu-id="ea66e-117">Use sua conexão OAuth de bots ao configurar suas extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="ea66e-117">Use your bots OAuth connection when setting up your messaging extensions.</span></span>
3. <span data-ttu-id="ea66e-118">No [arquivo TeamsMessagingExtensionsSearchAuthConfigBot.cs,](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config/Bots/TeamsMessagingExtensionsSearchAuthConfigBot.cs) atualize o valor de *auth* para *silentAuth* `OnTeamsMessagingExtensionQueryAsync` no e/ou `OnTeamsAppBasedLinkQueryAsync` .</span><span class="sxs-lookup"><span data-stu-id="ea66e-118">In the [TeamsMessagingExtensionsSearchAuthConfigBot.cs](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config/Bots/TeamsMessagingExtensionsSearchAuthConfigBot.cs) file, update the value from *auth* to *silentAuth* in the `OnTeamsMessagingExtensionQueryAsync` and / or `OnTeamsAppBasedLinkQueryAsync`.</span></span>  

    > [!NOTE]
    > <span data-ttu-id="ea66e-119">Não há suporte para outros manipuladores SSO, exceto no arquivo `OnTeamsMessagingExtensionQueryAsync` `OnTeamsAppBasedLinkQueryAsync` TeamsMessagingExtensionsSearchAuthConfigBot.cs.</span><span class="sxs-lookup"><span data-stu-id="ea66e-119">We do not support other handlers SSO, except `OnTeamsMessagingExtensionQueryAsync` and `OnTeamsAppBasedLinkQueryAsync` from the TeamsMessagingExtensionsSearchAuthConfigBot.cs file.</span></span>
   
4. <span data-ttu-id="ea66e-120">Você recebe o token no manipulador na carga ou no , dependendo de qual cenário você está habilitando `OnTeamsMessagingExtensionQueryAsync` `turnContext.Activity.Value` o `OnTeamsAppBasedLinkQueryAsync` SSO para:</span><span class="sxs-lookup"><span data-stu-id="ea66e-120">You receive the token in `OnTeamsMessagingExtensionQueryAsync` handler in the `turnContext.Activity.Value` payload or in the `OnTeamsAppBasedLinkQueryAsync`, depending on which scenario you are enabling the SSO for:</span></span>

    ```json
    JObject valueObject=JObject.FromObject(turnContext.Activity.Value);
    if(valueObject["authentication"] !=null)
     {
        JObject authenticationObject=JObject.FromObject(valueObject["authentication"]);
        if(authenticationObject["token"] !=null)
     }
    
     ```
  
    <span data-ttu-id="ea66e-121">Se você estiver usando a conexão OAuth, adicione o seguinte código ao arquivo TeamsMessagingExtensionsSearchAuthConfigBot.cs para atualizar ou adicionar o token na loja:</span><span class="sxs-lookup"><span data-stu-id="ea66e-121">If you are using the OAuth connection, add the following code to the TeamsMessagingExtensionsSearchAuthConfigBot.cs file to update or add the token in the store:</span></span>
    
   ```C#
   protected override async Task<InvokeResponse> OnInvokeActivityAsync(ITurnContext<IInvokeActivity> turnContext, CancellationToken cancellationToken)
        {
            JObject valueObject = JObject.FromObject(turnContext.Activity.Value);
            if (valueObject["authentication"] != null)
            {
                JObject authenticationObject = JObject.FromObject(valueObject["authentication"]);
                if (authenticationObject["token"] != null)
                {
                    //If the token is NOT exchangeable, then return 412 to require user consent
                    if (await TokenIsExchangeable(turnContext, cancellationToken))
                    {
                        return await base.OnInvokeActivityAsync(turnContext, cancellationToken).ConfigureAwait(false);
                    }
                    else
                    {
                        var response = new InvokeResponse();
                        response.Status = 412;
                        return response;
                    }
                }
            }
            return await base.OnInvokeActivityAsync(turnContext, cancellationToken).ConfigureAwait(false);
        }
        private async Task<bool> TokenIsExchangeable(ITurnContext turnContext, CancellationToken cancellationToken)
        {
            TokenResponse tokenExchangeResponse = null;
            try
            {
                JObject valueObject = JObject.FromObject(turnContext.Activity.Value);
                var tokenExchangeRequest =
                ((JObject)valueObject["authentication"])?.ToObject<TokenExchangeInvokeRequest>();
                tokenExchangeResponse = await (turnContext.Adapter as IExtendedUserTokenProvider).ExchangeTokenAsync(
                 turnContext,
                 _connectionName,
                 turnContext.Activity.From.Id,
                 new TokenExchangeRequest
                 {
                     Token = tokenExchangeRequest.Token,
                 },
                 cancellationToken).ConfigureAwait(false);
            }
    #pragma warning disable CA1031 //Do not catch general exception types (ignoring, see comment below)
            catch
    #pragma warning restore CA1031 //Do not catch general exception types
            {
                //ignore exceptions
                //if token exchange failed for any reason, tokenExchangeResponse above remains null, and a failure invoke response is sent to the caller.
                //This ensures the caller knows that the invoke has failed.
            }
            if (tokenExchangeResponse == null || string.IsNullOrEmpty(tokenExchangeResponse.Token))
            {
                return false;
            }
            return true;
        }
    
    ```    

## <a name="see-also"></a><span data-ttu-id="ea66e-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="ea66e-122">See also</span></span>

* [<span data-ttu-id="ea66e-123">Adicionar autenticação às extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="ea66e-123">Add authentication to your messaging extensions</span></span>](add-authentication.md)
* [<span data-ttu-id="ea66e-124">Usar SSO para bots</span><span class="sxs-lookup"><span data-stu-id="ea66e-124">Use SSO for bots</span></span>](../../bots/how-to/authentication/auth-aad-sso-bots.md)
* [<span data-ttu-id="ea66e-125">Desenrolamento de link</span><span class="sxs-lookup"><span data-stu-id="ea66e-125">Link unfurling</span></span>](link-unfurling.md)

