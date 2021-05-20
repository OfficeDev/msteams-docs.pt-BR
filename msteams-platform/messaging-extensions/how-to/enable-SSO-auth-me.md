---
title: Suporte SSO para suas extensões de mensagens
author: KirtiPereira
description: Como ativar o suporte ao SSO para suas extensões de mensagens
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
# <a name="single-sign-on-sso-support-for-messaging-extensions"></a><span data-ttu-id="c68f0-103">Suporte de login único (SSO) para extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="c68f0-103">Single sign-on (SSO) support for messaging extensions</span></span>
 
<span data-ttu-id="c68f0-104">O suporte de login único já está disponível para extensões de mensagens e desvendação de links.</span><span class="sxs-lookup"><span data-stu-id="c68f0-104">Single sign-on support is now available for messaging extensions and link unfurling.</span></span> <span data-ttu-id="c68f0-105">Habilitar O SSO (Single Sign-on, on-on) para extensões de mensagens atualiza silenciosamente o token de autenticação, o que minimiza o número de vezes que você precisa para inserir seu sinal em credenciais para Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="c68f0-105">Enabling Single sign-on (SSO) for messaging extensions silently refreshes the authentication token, which minimizes the number of times you need to enter your sign in credentials for Microsoft Teams.</span></span>

<span data-ttu-id="c68f0-106">Este documento orienta você sobre como ativar o SSO e armazenar seu token de autenticação, se necessário.</span><span class="sxs-lookup"><span data-stu-id="c68f0-106">This document guides you on how to enable the SSO and store your authentication token, if required.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c68f0-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="c68f0-107">Prerequisites</span></span>

<span data-ttu-id="c68f0-108">O pré-requisito para habilitar o SSO para extensões de mensagens e desvendação de links é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c68f0-108">The prerequisite to enable SSO for messaging extensions and link unfurling are as follows:</span></span>
* <span data-ttu-id="c68f0-109">Você deve ter uma [conta no Azure.](https://azure.microsoft.com/en-us/free/)</span><span class="sxs-lookup"><span data-stu-id="c68f0-109">You must have an [Azure](https://azure.microsoft.com/en-us/free/) account.</span></span>
* <span data-ttu-id="c68f0-110">Você deve configurar seu aplicativo através do portal AAD e atualizar seu manifesto de aplicativo Teams para o seu bot conforme definido no [cadastro do seu aplicativo através do portal AAD](../../bots/how-to/authentication/auth-aad-sso-bots.md#register-your-app-through-the-aad-portal).</span><span class="sxs-lookup"><span data-stu-id="c68f0-110">You must configure your app through the AAD portal, and update your Teams application manifest for your bot as defined in [register your app through the AAD portal](../../bots/how-to/authentication/auth-aad-sso-bots.md#register-your-app-through-the-aad-portal).</span></span>

> [!NOTE]
> <span data-ttu-id="c68f0-111">Para obter mais informações sobre a criação de uma conta do Azure e a atualização do manifesto do aplicativo, consulte [o suporte ao Single Sign-on (SSO) para bots](../../bots/how-to/authentication/auth-aad-sso-bots.md).</span><span class="sxs-lookup"><span data-stu-id="c68f0-111">For more information on creating an Azure account and updating your app manifest, see [Single sign-on (SSO) support for bots](../../bots/how-to/authentication/auth-aad-sso-bots.md).</span></span>

## <a name="enable-sso-for-messaging-extensions-and-link-unfurling"></a><span data-ttu-id="c68f0-112">Habilite o SSO para extensões de mensagens e desvendamento de links</span><span class="sxs-lookup"><span data-stu-id="c68f0-112">Enable SSO for messaging extensions and link unfurling</span></span>

<span data-ttu-id="c68f0-113">Depois que os pré-requisitos forem concluídos, você pode habilitar o SSO para extensões de mensagens e desenrolar de links.</span><span class="sxs-lookup"><span data-stu-id="c68f0-113">After the prerequisites are completed, you can enable SSO for messaging extensions and link unfurling.</span></span>

<span data-ttu-id="c68f0-114">**Para habilitar o SSO**</span><span class="sxs-lookup"><span data-stu-id="c68f0-114">**To enable SSO**</span></span>
1. <span data-ttu-id="c68f0-115">Atualize seus bots [Detalhes da conexão OAuth](../../bots/how-to/authentication/auth-aad-sso-bots.md#update-the-azure-portal-with-the-oauth-connection) no portal Azure.</span><span class="sxs-lookup"><span data-stu-id="c68f0-115">Update your bots [OAuth connection](../../bots/how-to/authentication/auth-aad-sso-bots.md#update-the-azure-portal-with-the-oauth-connection) details in the Azure portal.</span></span>
2. <span data-ttu-id="c68f0-116">Baixe a [amostra de extensões de mensagens](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config) e siga as instruções de configuração fornecidas pelo assistente.</span><span class="sxs-lookup"><span data-stu-id="c68f0-116">Download the [messaging extensions sample](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config) and follow the setup instructions provided by the wizard.</span></span>
   > [!NOTE]
   > <span data-ttu-id="c68f0-117">Use a conexão OAuth dos bots ao configurar suas extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="c68f0-117">Use your bots OAuth connection when setting up your messaging extensions.</span></span>
3. <span data-ttu-id="c68f0-118">No arquivo [TeamsMessagingExtensionsSearchAuthConfigBot.cs,](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config/Bots/TeamsMessagingExtensionsSearchAuthConfigBot.cs) atualize o valor do *auth* para *silentAuth* no `OnTeamsMessagingExtensionQueryAsync` e/ou `OnTeamsAppBasedLinkQueryAsync` .</span><span class="sxs-lookup"><span data-stu-id="c68f0-118">In the [TeamsMessagingExtensionsSearchAuthConfigBot.cs](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config/Bots/TeamsMessagingExtensionsSearchAuthConfigBot.cs) file, update the value from *auth* to *silentAuth* in the `OnTeamsMessagingExtensionQueryAsync` and / or `OnTeamsAppBasedLinkQueryAsync`.</span></span>  

    > [!NOTE]
    > <span data-ttu-id="c68f0-119">Não suportamos outros manipuladores SSO, exceto `OnTeamsMessagingExtensionQueryAsync` e `OnTeamsAppBasedLinkQueryAsync` do arquivo TeamsMessagingExtensionsSearchAuthConfigBot.cs arquivo.</span><span class="sxs-lookup"><span data-stu-id="c68f0-119">We do not support other handlers SSO, except `OnTeamsMessagingExtensionQueryAsync` and `OnTeamsAppBasedLinkQueryAsync` from the TeamsMessagingExtensionsSearchAuthConfigBot.cs file.</span></span>
   
4. <span data-ttu-id="c68f0-120">Você recebe o token no `OnTeamsMessagingExtensionQueryAsync` manipulador na carga ou no , dependendo do cenário para o qual você está `turnContext.Activity.Value` `OnTeamsAppBasedLinkQueryAsync` habilitando o SSO:</span><span class="sxs-lookup"><span data-stu-id="c68f0-120">You receive the token in `OnTeamsMessagingExtensionQueryAsync` handler in the `turnContext.Activity.Value` payload or in the `OnTeamsAppBasedLinkQueryAsync`, depending on which scenario you are enabling the SSO for:</span></span>

    ```json
    JObject valueObject=JObject.FromObject(turnContext.Activity.Value);
    if(valueObject["authentication"] !=null)
     {
        JObject authenticationObject=JObject.FromObject(valueObject["authentication"]);
        if(authenticationObject["token"] !=null)
     }
    
     ```
  
    <span data-ttu-id="c68f0-121">Se você estiver usando a conexão OAuth, adicione o seguinte código às EquipesMessagingExtensionsSearchAuthConfigBot.cs arquivo para atualizar ou adicionar o token na loja:</span><span class="sxs-lookup"><span data-stu-id="c68f0-121">If you are using the OAuth connection, add the following code to the TeamsMessagingExtensionsSearchAuthConfigBot.cs file to update or add the token in the store:</span></span>
    
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

## <a name="see-also"></a><span data-ttu-id="c68f0-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="c68f0-122">See also</span></span>

* [<span data-ttu-id="c68f0-123">Adicione autenticação às suas extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="c68f0-123">Add authentication to your messaging extensions</span></span>](add-authentication.md)
* [<span data-ttu-id="c68f0-124">Use SSO para bots</span><span class="sxs-lookup"><span data-stu-id="c68f0-124">Use SSO for bots</span></span>](../../bots/how-to/authentication/auth-aad-sso-bots.md)
* [<span data-ttu-id="c68f0-125">Desenrolamento de link</span><span class="sxs-lookup"><span data-stu-id="c68f0-125">Link unfurling</span></span>](link-unfurling.md)

