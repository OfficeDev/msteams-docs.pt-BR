---
title: Notificações de chamadas recebidas
description: Informações técnicas detalhadas sobre como lidar com notificações de chamadas de entrada
ms.topic: conceptual
keywords: afinidade de região de retorno de chamada de chamadas
ms.date: 04/02/2019
ms.openlocfilehash: 1ab28f898d2b51b4c1c643006ecac06ca79b2d14
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696399"
---
# <a name="incoming-call-notifications"></a><span data-ttu-id="3e653-104">Notificações de chamadas recebidas</span><span class="sxs-lookup"><span data-stu-id="3e653-104">Incoming call notifications</span></span>

<span data-ttu-id="3e653-105">Ao registrar um bot de chamadas e reuniões para [o Microsoft Teams,](./registering-calling-bot.md#create-new-bot-or-add-calling-capabilities)o Webhook para a URL de chamada é mencionado.</span><span class="sxs-lookup"><span data-stu-id="3e653-105">In [registering a calls and meetings bot for Microsoft Teams](./registering-calling-bot.md#create-new-bot-or-add-calling-capabilities), the Webhook for calling URL is mentioned.</span></span> <span data-ttu-id="3e653-106">Essa URL é o ponto de extremidade do webhook para todas as chamadas de entrada para seu bot.</span><span class="sxs-lookup"><span data-stu-id="3e653-106">This URL is the webhook endpoint for all incoming calls to your bot.</span></span>

## <a name="protocol-determination"></a><span data-ttu-id="3e653-107">Determinação do protocolo</span><span class="sxs-lookup"><span data-stu-id="3e653-107">Protocol determination</span></span>

<span data-ttu-id="3e653-108">A notificação de entrada é fornecida em um formato herdado para compatibilidade com o protocolo [anterior do Skype](/azure/bot-service/dotnet/bot-builder-dotnet-real-time-media-concepts?view=azure-bot-service-3.0&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="3e653-108">The incoming notification is provided in a legacy format for compatibility with the previous [Skype protocol](/azure/bot-service/dotnet/bot-builder-dotnet-real-time-media-concepts?view=azure-bot-service-3.0&preserve-view=true).</span></span> <span data-ttu-id="3e653-109">Para converter a chamada no protocolo Microsoft Graph, o bot deve determinar se a notificação está em um formato herdado e fornecer a seguinte resposta:</span><span class="sxs-lookup"><span data-stu-id="3e653-109">In order to convert the call to the Microsoft Graph protocol, your bot must determine whether the notification is in a legacy format and provide the following response:</span></span>

```http
HTTP/1.1 204 No Content
```

<span data-ttu-id="3e653-110">Seu bot recebe a notificação novamente, mas desta vez no protocolo do Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="3e653-110">Your bot receives the notification again, but this time in the Microsoft Graph protocol.</span></span>

<span data-ttu-id="3e653-111">Em uma versão futura da Plataforma de Mídia em tempo real, você pode configurar o protocolo compatível com o aplicativo para evitar receber o retorno de chamada inicial no formato herddo.</span><span class="sxs-lookup"><span data-stu-id="3e653-111">In a future release of the Real-time Media Platform, you can configure the protocol your application supports to avoid receiving the initial callback in the legacy format.</span></span>

<span data-ttu-id="3e653-112">A próxima seção fornece detalhes sobre notificações de chamadas de entrada redirecionadas para afinidade de região para sua implantação.</span><span class="sxs-lookup"><span data-stu-id="3e653-112">The next section provides details on incoming call notifications redirected for region affinity to your deployment.</span></span>

## <a name="redirects-for-region-affinity"></a><span data-ttu-id="3e653-113">Redirecionamentos para afinidade de região</span><span class="sxs-lookup"><span data-stu-id="3e653-113">Redirects for region affinity</span></span>

<span data-ttu-id="3e653-114">Você chama seu webhook do data-center que hospeda a chamada.</span><span class="sxs-lookup"><span data-stu-id="3e653-114">You call your webhook from the data-center hosting the call.</span></span> <span data-ttu-id="3e653-115">A chamada começa em qualquer data center e não leva em conta as afinidades de região.</span><span class="sxs-lookup"><span data-stu-id="3e653-115">The call starts in any data center and does not take into account region affinities.</span></span> <span data-ttu-id="3e653-116">A notificação é enviada para sua implantação, dependendo da resolução GeoDNS.</span><span class="sxs-lookup"><span data-stu-id="3e653-116">The notification is sent to your deployment depending on the GeoDNS resolution.</span></span> <span data-ttu-id="3e653-117">Se o aplicativo determinar, inspecionando a carga de notificação inicial ou de outra forma, que ele precisa ser executado em uma implantação diferente, o aplicativo fornece a seguinte resposta:</span><span class="sxs-lookup"><span data-stu-id="3e653-117">If your application determines, by inspecting the initial notification payload or otherwise, that it needs to run in a different deployment, the application provides the following response:</span></span>

```http
HTTP/1.1 302 Found
Location: your-new-location
```

<span data-ttu-id="3e653-118">Habilita o bot a responder a uma chamada de entrada usando a API [de resposta.](https://developer.microsoft.com/graph/docs/api-reference/beta/api/call_answer)</span><span class="sxs-lookup"><span data-stu-id="3e653-118">Enable your bot to answer an incoming call using the [answer](https://developer.microsoft.com/graph/docs/api-reference/beta/api/call_answer) API.</span></span> <span data-ttu-id="3e653-119">Você pode especificar o `callbackUri` para manipular essa chamada específica.</span><span class="sxs-lookup"><span data-stu-id="3e653-119">You can specify the `callbackUri` to handle this particular call.</span></span> <span data-ttu-id="3e653-120">Isso é útil para instâncias de estado em que sua chamada é manipulada por uma partição específica e você deseja inserir essas informações no roteamento para `callbackUri` a instância certa.</span><span class="sxs-lookup"><span data-stu-id="3e653-120">This is useful for stateful instances where your call is handled by a particular partition, and you want to embed this information in the `callbackUri` for routing to the right instance.</span></span>

<span data-ttu-id="3e653-121">A próxima seção fornece detalhes sobre a autenticação do retorno de chamada inspecionando o token postado em seu webhook.</span><span class="sxs-lookup"><span data-stu-id="3e653-121">The next section provides details on authenticating the callback by inspecting the token posted to your webhook.</span></span>

## <a name="authenticate-the-callback"></a><span data-ttu-id="3e653-122">Autenticar o retorno de chamada</span><span class="sxs-lookup"><span data-stu-id="3e653-122">Authenticate the callback</span></span>

<span data-ttu-id="3e653-123">Seu bot deve inspecionar o token postado no webhook para validar a solicitação.</span><span class="sxs-lookup"><span data-stu-id="3e653-123">Your bot must inspect the token posted to your webhook to validate the request.</span></span> <span data-ttu-id="3e653-124">Sempre que a API posta no webhook, a mensagem HTTP POST contém um token OAuth no cabeçalho Autorização como um token de portador, com a audiência como iD do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3e653-124">Every time the API posts to the webhook, the HTTP POST message contains an OAuth token in the Authorization header as a bearer token, with the audience as your application's App ID.</span></span>

<span data-ttu-id="3e653-125">Seu aplicativo deve validar esse token antes de aceitar a solicitação de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="3e653-125">Your application must validate this token before accepting the callback request.</span></span>

<span data-ttu-id="3e653-126">O código de exemplo a seguir é usado para autenticar o retorno de chamada:</span><span class="sxs-lookup"><span data-stu-id="3e653-126">The following sample code is used to authenticate the callback:</span></span>

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

<span data-ttu-id="3e653-127">O token OAuth tem os seguintes valores e é assinado pelo Skype:</span><span class="sxs-lookup"><span data-stu-id="3e653-127">The OAuth token has the following values, and is signed by Skype:</span></span>

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

<span data-ttu-id="3e653-128">A configuração OpenID publicada <https://api.aps.skype.com/v1/.well-known/OpenIdConfiguration> em pode ser usada para verificar o token.</span><span class="sxs-lookup"><span data-stu-id="3e653-128">The OpenID configuration published at <https://api.aps.skype.com/v1/.well-known/OpenIdConfiguration> can be used to verify the token.</span></span> <span data-ttu-id="3e653-129">Cada valor de token OAuth é usado da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="3e653-129">Each OAuth token value is used as follows:</span></span>

* <span data-ttu-id="3e653-130">`aud` onde audiência é o URI de ID do aplicativo especificado para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3e653-130">`aud` where audience is the App ID URI specified for the application.</span></span>
* <span data-ttu-id="3e653-131">`tid` é a ID do locatário para Contoso.com.</span><span class="sxs-lookup"><span data-stu-id="3e653-131">`tid` is the tenant id for Contoso.com.</span></span>
* <span data-ttu-id="3e653-132">`iss` é o emissor de token, `https://api.botframework.com` .</span><span class="sxs-lookup"><span data-stu-id="3e653-132">`iss` is the token issuer, `https://api.botframework.com`.</span></span>

<span data-ttu-id="3e653-133">Para a manipulação de código, o webhook deve validar o token, garantir que ele não expirou e verificar se ele foi assinado pela configuração OpenID publicada.</span><span class="sxs-lookup"><span data-stu-id="3e653-133">For your code handling, the webhook must validate the token, ensure it has not expired, and check whether it has been signed by the published OpenID configuration.</span></span> <span data-ttu-id="3e653-134">Você também deve verificar se a aud corresponde à ID do aplicativo antes de aceitar a solicitação de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="3e653-134">You must also check whether aud matches your App ID before accepting the callback request.</span></span>

<span data-ttu-id="3e653-135">Para obter mais informações, consulte [validate inbound requests](https://github.com/microsoftgraph/microsoft-graph-comms-samples/blob/master/Samples/Common/Sample.Common/Authentication/AuthenticationProvider.cs).</span><span class="sxs-lookup"><span data-stu-id="3e653-135">For more information, see [validate inbound requests](https://github.com/microsoftgraph/microsoft-graph-comms-samples/blob/master/Samples/Common/Sample.Common/Authentication/AuthenticationProvider.cs).</span></span>

## <a name="next-step"></a><span data-ttu-id="3e653-136">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="3e653-136">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3e653-137">Requisitos e considerações para bots de mídia hospedados pelo aplicativo</span><span class="sxs-lookup"><span data-stu-id="3e653-137">Requirements and considerations for application-hosted media bots</span></span>](~/bots/calls-and-meetings/requirements-considerations-application-hosted-media-bots.md)
