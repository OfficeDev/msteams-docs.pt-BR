---
title: Webhooks e conectores
author: clearab
description: Entenda como webhooks e conectores podem conectar seus serviços Web ao Teams cliente.
localization_priority: Normal
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 2cb763a6637abd3faa500de871119f0b829871bf
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140051"
---
# <a name="webhooks-and-connectors"></a><span data-ttu-id="3fc0f-103">Webhooks e conectores</span><span class="sxs-lookup"><span data-stu-id="3fc0f-103">Webhooks and connectors</span></span>

<span data-ttu-id="3fc0f-104">Webhooks e conectores ajudam a conectar os serviços Web a canais e equipes em Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-104">Webhooks and connectors help to connect the web services to channels and teams in Microsoft Teams.</span></span> <span data-ttu-id="3fc0f-105">Webhooks são retorno de chamada HTTP definido pelo usuário que notifica os usuários sobre qualquer ação que tenha sido realizada no canal Microsoft Teams usuário.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-105">Webhooks are user defined HTTP callback that notifies users about any action that has taken place in the Microsoft Teams channel.</span></span> <span data-ttu-id="3fc0f-106">É uma maneira de um aplicativo obter dados em tempo real.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-106">It is a way for an app to get real time data.</span></span> <span data-ttu-id="3fc0f-107">Os conectores permitem aos usuários se inscreverem para receber notificações e mensagens dos serviços da Web.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-107">Connectors allow users to subscribe to receive notifications and messages from your web services.</span></span> <span data-ttu-id="3fc0f-108">Eles expõem um ponto de extremidade HTTPS para seu serviço postar mensagens na forma de cartões.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-108">They expose an HTTPS endpoint for your service to post messages in the form of cards.</span></span>

## <a name="outgoing-webhooks"></a><span data-ttu-id="3fc0f-109">Webhooks de saída</span><span class="sxs-lookup"><span data-stu-id="3fc0f-109">Outgoing Webhooks</span></span>

<span data-ttu-id="3fc0f-110">Webhooks ajudam a Teams se integrar com aplicativos externos.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-110">Webhooks help Teams to integrate with external apps.</span></span> <span data-ttu-id="3fc0f-111">Com Webhooks de saída, você pode enviar mensagens de texto de um canal para os serviços Web.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-111">With Outgoing Webhooks, you can send text messages from a channel to the web services.</span></span> <span data-ttu-id="3fc0f-112">Depois de configurar os Webhooks de saída, os usuários podem @mention Webhook de saída e enviar uma mensagem para os serviços Web.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-112">After configuring the Outgoing Webhooks, users can @mention Outgoing Webhook and send a message to web services.</span></span> <span data-ttu-id="3fc0f-113">O serviço responde dentro de dez segundos à mensagem com um texto ou um cartão.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-113">The service responds within ten seconds to the message with a text or a card.</span></span>

> [!NOTE]
> <span data-ttu-id="3fc0f-114">Os Webhooks de saída são configurados por equipe e não podem ser incluídos como parte de um aplicativo Teams normal.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-114">Outgoing Webhooks are configured on a per team basis and cannot be included as part of a normal Teams app.</span></span>

## <a name="connectors"></a><span data-ttu-id="3fc0f-115">Conectores</span><span class="sxs-lookup"><span data-stu-id="3fc0f-115">Connectors</span></span>

<span data-ttu-id="3fc0f-116">Os conectores permitem que os usuários assinem para receber notificações e mensagens dos serviços Web.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-116">Connectors allow users to subscribe to receive notifications and messages from the web services.</span></span> <span data-ttu-id="3fc0f-117">Eles expõem o ponto de extremidade HTTPS para que o serviço poste mensagens Teams canais, normalmente na forma de cartões.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-117">They expose the HTTPS endpoint for the service to post messages to Teams channels, typically in the form of cards.</span></span>

### <a name="incoming-webhooks"></a><span data-ttu-id="3fc0f-118">Webhooks de entrada</span><span class="sxs-lookup"><span data-stu-id="3fc0f-118">Incoming Webhooks</span></span>

<span data-ttu-id="3fc0f-119">Webhooks de entrada ajudam a postar mensagens de aplicativos para Teams.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-119">Incoming Webhooks help in posting messages from apps to Teams.</span></span> <span data-ttu-id="3fc0f-120">Se os Webhooks de entrada estão habilitados para uma equipe em qualquer canal, ele expõe o ponto de extremidade HTTPS, que aceita o JSON formatado corretamente e insere as mensagens nesse canal.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-120">If Incoming Webhooks are enabled for a team in any channel, it exposes the HTTPS endpoint, which accepts correctly formatted JSON and inserts the messages into that channel.</span></span> <span data-ttu-id="3fc0f-121">Por exemplo, você pode criar um Webhook de entrada em seu canal DevOps, configurar sua com build e, simultaneamente, implantar e monitorar serviços para enviar alertas.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-121">For example, you can create an Incoming Webhook in your DevOps channel, configure your build, and simultaneously deploy and monitor services to send alerts.</span></span>

### <a name="office-365-connectors"></a><span data-ttu-id="3fc0f-122">Conectores de Office 365</span><span class="sxs-lookup"><span data-stu-id="3fc0f-122">Office 365 Connectors</span></span>

<span data-ttu-id="3fc0f-123">Office 365 Os conectores permitem que você crie uma página de configuração personalizada para seu Webhook de Entrada e empacote-os como parte de um Teams app.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-123">Office 365 Connectors allow you to create a custom configuration page for your Incoming Webhook and package them as part of a Teams app.</span></span> <span data-ttu-id="3fc0f-124">Você envia mensagens principalmente usando Office 365 conector e tem a capacidade de adicionar um conjunto limitado de ações de cartão a eles.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-124">You send messages primarily using Office 365 Connector cards and have the ability to add a limited set of card actions to them.</span></span> <span data-ttu-id="3fc0f-125">Por exemplo, um conector de clima que permite que os usuários selecionem um local e hora do dia, para receber atualizações sobre o clima de amanhã.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-125">For example, a weather connector that allows users to select a location and time of day, to receive updates about tomorrow's weather.</span></span> <span data-ttu-id="3fc0f-126">Eles são configurados em um nível de canal, mas são instalados em um nível de equipe.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-126">They are configured on a channel level but are installed at a team level.</span></span>

> [!NOTE]
> <span data-ttu-id="3fc0f-127">Você pode distribuir o Office 365 conector Teams aplicativo para nosso AppStore.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-127">You can distribute the Office 365 Connector Teams app to our AppStore.</span></span>

## <a name="create-and-send-messages"></a><span data-ttu-id="3fc0f-128">Criar e enviar mensagens</span><span class="sxs-lookup"><span data-stu-id="3fc0f-128">Create and send messages</span></span>

<span data-ttu-id="3fc0f-129">As mensagens ativas permitem que os usuários adoeciem sem sair do cliente de email, aumentando o envolvimento do usuário.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-129">Actionable messages allow users to take action without leaving their email client, increasing user engagement.</span></span> <span data-ttu-id="3fc0f-130">Com Office 365 e Webhooks de entrada, você pode enviar mensagens postando uma carga JSON na URL do webhook.</span><span class="sxs-lookup"><span data-stu-id="3fc0f-130">With Office 365 and Incoming Webhooks, you can send messages by posting a JSON payload to the webhook URL.</span></span>

## <a name="see-also"></a><span data-ttu-id="3fc0f-131">Também consulte</span><span class="sxs-lookup"><span data-stu-id="3fc0f-131">See also</span></span>

* [<span data-ttu-id="3fc0f-132">Criar um Webhook de entrada</span><span class="sxs-lookup"><span data-stu-id="3fc0f-132">Create an Incoming Webhook</span></span>](~/webhooks-and-connectors/how-to/add-incoming-webhook.md)
* [<span data-ttu-id="3fc0f-133">Criar um conector do Office 365</span><span class="sxs-lookup"><span data-stu-id="3fc0f-133">Create an Office 365 Connector</span></span>](~/webhooks-and-connectors/how-to/connectors-creating.md)
* [<span data-ttu-id="3fc0f-134">Criar e enviar mensagens</span><span class="sxs-lookup"><span data-stu-id="3fc0f-134">Create and send messages</span></span>](~/webhooks-and-connectors/how-to/connectors-using.md)

## <a name="next-step"></a><span data-ttu-id="3fc0f-135">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="3fc0f-135">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3fc0f-136">Criar um Webhook de Saída</span><span class="sxs-lookup"><span data-stu-id="3fc0f-136">Create an Outgoing Webhook</span></span>](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md)
