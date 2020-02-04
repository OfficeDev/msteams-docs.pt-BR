---
title: Detalhes técnicos sobre como lidar com notificações de chamada de entrada
description: Informações técnicas detalhadas sobre o tratamento de notificações de chamadas de entrada
keywords: chamar as notificações de chamadas afinidade de região de retorno de chamada
ms.date: 04/02/2019
ms.openlocfilehash: be8860ff70cd7dff4fd9599079ea7aab4f454174
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672872"
---
# <a name="incoming-call-notifications-technical-details"></a><span data-ttu-id="418d4-104">Notificações de chamada de entrada: detalhes técnicos</span><span class="sxs-lookup"><span data-stu-id="418d4-104">Incoming call notifications: technical details</span></span>

<span data-ttu-id="418d4-105">Ao [registrar um bot de chamada e reunião para o Microsoft Teams](./registering-calling-bot.md#creating-a-new-bot-or-adding-calling-capabilities-to-an-existing-bot), mencionamos a URL de **webhook (para chamada)** , o ponto de extremidade de webhook para todas as chamadas de entrada para o bot.</span><span class="sxs-lookup"><span data-stu-id="418d4-105">In [Registering a calling and meeting bot for Microsoft Teams](./registering-calling-bot.md#creating-a-new-bot-or-adding-calling-capabilities-to-an-existing-bot), we mentioned the **Webhook (for calling)** URL — the webhook endpoint for all incoming calls to your bot.</span></span> <span data-ttu-id="418d4-106">Este tópico discute os detalhes técnicos que você precisará para responder a essas notificações.</span><span class="sxs-lookup"><span data-stu-id="418d4-106">This topic discusses the technical details you'll need to respond to these notifications.</span></span>

## <a name="protocol-determination"></a><span data-ttu-id="418d4-107">Determinação de protocolo</span><span class="sxs-lookup"><span data-stu-id="418d4-107">Protocol determination</span></span>

<span data-ttu-id="418d4-108">A notificação de entrada é fornecida no formato Legacy para compatibilidade com o [protocolo Skype](/azure/bot-service/dotnet/bot-builder-dotnet-real-time-media-concepts?view=azure-bot-service-3.0)anterior.</span><span class="sxs-lookup"><span data-stu-id="418d4-108">The incoming notification is provided in legacy format for compatibility with the previous [Skype protocol](/azure/bot-service/dotnet/bot-builder-dotnet-real-time-media-concepts?view=azure-bot-service-3.0).</span></span> <span data-ttu-id="418d4-109">Para converter a chamada para o protocolo Microsoft Graph, seu bot deve determinar se a notificação está no formato herdado e responder com:</span><span class="sxs-lookup"><span data-stu-id="418d4-109">In order to convert the call to the Microsoft Graph protocol, your bot must determine whether the notification is in legacy format and reply with:</span></span>

```http
HTTP/1.1 204 No Content
```

<span data-ttu-id="418d4-110">O bot receberá a notificação novamente, mas desta vez no protocolo Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="418d4-110">Your bot will receive the notification again, but this time in the Microsoft Graph protocol.</span></span>

<span data-ttu-id="418d4-111">Em uma versão futura da plataforma de mídia em tempo real, vamos permitir que você configure o protocolo que seu aplicativo suporta para evitar receber o retorno de chamada inicial no formato herdado.</span><span class="sxs-lookup"><span data-stu-id="418d4-111">In a future release of the Real-time Media Platform, we'll allow you to configure the protocol your application supports to avoid receiving the initial callback in the legacy format.</span></span>

## <a name="redirects-for-region-affinity"></a><span data-ttu-id="418d4-112">Redireciona para afinidade de região</span><span class="sxs-lookup"><span data-stu-id="418d4-112">Redirects for region affinity</span></span>

<span data-ttu-id="418d4-113">Você chamará o webhook do centro de dados que hospeda a chamada.</span><span class="sxs-lookup"><span data-stu-id="418d4-113">You'll call your webhook from the data-center hosting the call.</span></span> <span data-ttu-id="418d4-114">A chamada pode começar em qualquer data center e não leva em conta as afinidades de região.</span><span class="sxs-lookup"><span data-stu-id="418d4-114">The call may start in any data center and doesn't take into account region affinities.</span></span> <span data-ttu-id="418d4-115">A notificação será enviada para sua implantação, dependendo da resolução do GeoDNS.</span><span class="sxs-lookup"><span data-stu-id="418d4-115">The notification will be sent to your deployment depending on the GeoDNS resolution.</span></span> <span data-ttu-id="418d4-116">Se o aplicativo determinar, inspecionar a carga de notificação inicial ou, caso contrário, ele precisará ser executado em uma implantação diferente, o aplicativo pode responder com:</span><span class="sxs-lookup"><span data-stu-id="418d4-116">If your application determines, by inspecting the initial notification payload or otherwise, that it needs to run in a different deployment, the application may reply with:</span></span>

```http
HTTP/1.1 302 Found
Location: your-new-location
```

<span data-ttu-id="418d4-117">Habilite o bot para atender a uma chamada de entrada usando a API de [resposta](https://developer.microsoft.com/graph/docs/api-reference/beta/api/call_answer) .</span><span class="sxs-lookup"><span data-stu-id="418d4-117">Enable your bot to answer an incoming call using the [answer](https://developer.microsoft.com/graph/docs/api-reference/beta/api/call_answer) API.</span></span> <span data-ttu-id="418d4-118">Você pode especificar o `callbackUri` para lidar com essa chamada específica.</span><span class="sxs-lookup"><span data-stu-id="418d4-118">You can specify the `callbackUri` to handle this particular call.</span></span> <span data-ttu-id="418d4-119">Isso é útil para instâncias de _estado_ em que sua chamada é manipulada por uma determinada partição e você deseja inserir essas informações `callbackUri` no para roteamento para a instância correta.</span><span class="sxs-lookup"><span data-stu-id="418d4-119">This is useful for _stateful_ instances where your call is handled by a particular partition and you want to embed this information in the `callbackUri` for routing to the right instance.</span></span>

## <a name="authenticating-the-callback"></a><span data-ttu-id="418d4-120">Autenticar o retorno de chamada</span><span class="sxs-lookup"><span data-stu-id="418d4-120">Authenticating the callback</span></span>

<span data-ttu-id="418d4-121">O bot deve inspecionar o token Postado no seu webhook para validar a solicitação.</span><span class="sxs-lookup"><span data-stu-id="418d4-121">Your bot should inspect the token posted to your webhook to validate the request.</span></span> <span data-ttu-id="418d4-122">Sempre que a API é postada para o webhook, a mensagem HTTP POST contém um token OAuth no cabeçalho Authorization como um token de portador, com o público como a ID de aplicativo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="418d4-122">Whenever the API posts to the webhook, the HTTP POST message contains an OAuth token in the Authorization header as a Bearer token, with audience as your application's App ID.</span></span>

<span data-ttu-id="418d4-123">O aplicativo deve validar esse token antes de aceitar a solicitação de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="418d4-123">Your application should validate this token before accepting the callback request.</span></span>

```http
POST https://bot.contoso.com/api/calls
Content-Type: application/json
Authentication: Bearer <TOKEN>

"value": [
    "subscriptionId": "2887CEE8344B47C291F1AF628599A93C",
    "subscriptionExpirationDateTime": "2016-11-20T18:23:45.9356913Z",
    "changeType": "updated",
    "resource": "/app/calls/8A934F51F25B4EE19613D4049491857B",
    "resourceData": {
        "@odata.type": "#microsoft.graph.call",
        "state": "Established"
    }
]
```

<span data-ttu-id="418d4-124">O token OAuth terá valores como os seguintes e será assinado pelo Skype.</span><span class="sxs-lookup"><span data-stu-id="418d4-124">The OAuth token will have values like the following, and will be signed by Skype.</span></span> <span data-ttu-id="418d4-125">A configuração de OpenID publicada <https://api.aps.skype.com/v1/.well-known/OpenIdConfiguration> em pode ser usada para verificar o token.</span><span class="sxs-lookup"><span data-stu-id="418d4-125">The OpenID configuration published at <https://api.aps.skype.com/v1/.well-known/OpenIdConfiguration> can be used to verify the token.</span></span>

```json
{
    "aud": "0efc74f7-41c3-47a4-8775-7259bfef4241",
    "iss": "https://api.botframework.com",
    "iat": 1466741440,
    "nbf": 1466741440,
    "exp": 1466745340,
    "tid": "1fdd12d0-4620-44ed-baec-459b611f84b2"
}
```

* <span data-ttu-id="418d4-126">o público-alvo **AUD** é o URI da ID do aplicativo especificado para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="418d4-126">**aud** audience is the App ID URI specified for the application.</span></span>
* <span data-ttu-id="418d4-127">**tid** é a ID do locatário para contoso.com.</span><span class="sxs-lookup"><span data-stu-id="418d4-127">**tid** is the tenant id for Contoso.com.</span></span>
* <span data-ttu-id="418d4-128">o **ISS** é o emissor do token `https://api.botframework.com`,.</span><span class="sxs-lookup"><span data-stu-id="418d4-128">**iss** is the token issuer, `https://api.botframework.com`.</span></span>

<span data-ttu-id="418d4-129">Seu código de manipulação do webhook deve validar o token, garantir que ele não tenha expirado e verificar se ele foi assinado pela nossa configuração de OpenID publicada.</span><span class="sxs-lookup"><span data-stu-id="418d4-129">Your code handling the webhook should validate the token, ensure it hasn't expired, and check whether it has been signed by our published OpenID configuration.</span></span> <span data-ttu-id="418d4-130">Você também deve verificar se o **AUD** corresponde à ID do aplicativo antes de aceitar a solicitação de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="418d4-130">You should also check whether **aud** matches your App ID before accepting the callback request.</span></span>

<span data-ttu-id="418d4-131">[Exemplo](https://github.com/microsoftgraph/microsoft-graph-comms-samples/blob/master/Samples/Common/Sample.Common/Authentication/AuthenticationProvider.cs) mostra como validar solicitações de entrada.</span><span class="sxs-lookup"><span data-stu-id="418d4-131">[Sample](https://github.com/microsoftgraph/microsoft-graph-comms-samples/blob/master/Samples/Common/Sample.Common/Authentication/AuthenticationProvider.cs) shows how to validate inbound requests.</span></span>
