---
title: O que são WebHooks e conectores?
author: clearab
description: Entenda como os WebHooks e conectores podem conectar seus serviços Web ao cliente do teams.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 740806e43af94d5a5da876affec2070a5a461b11
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/12/2020
ms.locfileid: "46651815"
---
# <a name="what-are-webhooks-and-connectors"></a><span data-ttu-id="67c1c-103">O que são WebHooks e conectores?</span><span class="sxs-lookup"><span data-stu-id="67c1c-103">What are webhooks and connectors?</span></span>

<span data-ttu-id="67c1c-104">Os WebHooks e conectores são maneiras diretas de conectar sistemas e serviços externos aos canais e chats do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="67c1c-104">Webhooks and connectors are straightforward ways to connect external systems and services with Microsoft Teams channels and chats.</span></span>

<span data-ttu-id="67c1c-105">Os usuários podem, por exemplo, assinar notificações de outro aplicativo (normalmente na forma de cartões).</span><span class="sxs-lookup"><span data-stu-id="67c1c-105">Users can, for example, subscribe to notifications from another app (typically in the form of cards).</span></span>

## <a name="incoming-webhooks"></a><span data-ttu-id="67c1c-106">WebHooks de entrada</span><span class="sxs-lookup"><span data-stu-id="67c1c-106">Incoming webhooks</span></span>

<span data-ttu-id="67c1c-107">Os WebHooks de entrada são o tipo mais simples de conector e um modo rápido e fácil de conectar o canal de uma equipe a um serviço externo.</span><span class="sxs-lookup"><span data-stu-id="67c1c-107">Incoming webhooks are the simplest type of connector and a quick and easy way to connect a team's channel to an external service.</span></span> <span data-ttu-id="67c1c-108">Para qualquer canal (se habilitado para essa equipe), você pode expor um ponto de extremidade HTTPS que aceita JSONmente formatado corretamente e insere mensagens no canal.</span><span class="sxs-lookup"><span data-stu-id="67c1c-108">For any channel (if enabled for that team), you can expose an HTTPS endpoint that accepts correctly formatted JSON and insert messages into the channel.</span></span>

<span data-ttu-id="67c1c-109">Confira [criar um webhook de entrada](~/webhooks-and-connectors/how-to/add-incoming-webhook.md).</span><span class="sxs-lookup"><span data-stu-id="67c1c-109">See [Create an incoming webhook](~/webhooks-and-connectors/how-to/add-incoming-webhook.md).</span></span>

### <a name="user-scenarios"></a><span data-ttu-id="67c1c-110">Cenários de usuário</span><span class="sxs-lookup"><span data-stu-id="67c1c-110">User scenarios</span></span>

<span data-ttu-id="67c1c-111">Os WebHooks de entrada são melhores para cenários exclusivos para uma equipe específica.</span><span class="sxs-lookup"><span data-stu-id="67c1c-111">Incoming webhooks are best for scenarios unique to a particular team.</span></span> <span data-ttu-id="67c1c-112">Por exemplo, você pode criar um webhook de entrada no canal do DevOps e configurar seus serviços de compilação, implantação e monitoramento para enviar alertas.</span><span class="sxs-lookup"><span data-stu-id="67c1c-112">For example, you could create an incoming webhook in your DevOps channel and configure your build, deployment, and monitoring services to send alerts.</span></span>

## <a name="office-365-connectors"></a><span data-ttu-id="67c1c-113">Conectores de Office 365</span><span class="sxs-lookup"><span data-stu-id="67c1c-113">Office 365 Connectors</span></span>

<span data-ttu-id="67c1c-114">Um conector do Office 365 permite criar uma página de configuração personalizada para o seu webhook de entrada e empacotá-lo como parte de um aplicativo do teams.</span><span class="sxs-lookup"><span data-stu-id="67c1c-114">An Office 365 Connector allows you to create a custom configuration page for your incoming webhook and package it as part of a Teams app.</span></span> <span data-ttu-id="67c1c-115">Em seguida, você pode distribuir esse aplicativo de forma mais ampla ou mesmo em nossa loja de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="67c1c-115">You can then distribute that app more broadly or even to our app store.</span></span> <span data-ttu-id="67c1c-116">Você envia mensagens principalmente usando cartões de conector do Office 365 que também podem ter um conjunto limitado de ações de cartão.</span><span class="sxs-lookup"><span data-stu-id="67c1c-116">You send messages primarily using Office 365 Connector cards that can also have a limited set of card actions.</span></span> <span data-ttu-id="67c1c-117">Eles são configurados no nível do canal, mas instalados no nível da equipe.</span><span class="sxs-lookup"><span data-stu-id="67c1c-117">They are configured on the channel level but installed at the team level.</span></span>

<span data-ttu-id="67c1c-118">Confira [criar um conector do Office 365](~/webhooks-and-connectors/how-to/connectors-creating.md).</span><span class="sxs-lookup"><span data-stu-id="67c1c-118">See [Create an Office 365 Connector](~/webhooks-and-connectors/how-to/connectors-creating.md).</span></span>

### <a name="user-scenarios"></a><span data-ttu-id="67c1c-119">Cenários de usuário</span><span class="sxs-lookup"><span data-stu-id="67c1c-119">User scenarios</span></span>

<span data-ttu-id="67c1c-120">Um conector de clima que permite que você escolha um local e hora do dia para receber atualizações sobre a previsão de amanhã.</span><span class="sxs-lookup"><span data-stu-id="67c1c-120">A weather connector that lets you choose a location and time of day to receive updates about tomorrow's forecast.</span></span>

## <a name="outgoing-webhooks"></a><span data-ttu-id="67c1c-121">WebHooks de saída</span><span class="sxs-lookup"><span data-stu-id="67c1c-121">Outgoing webhooks</span></span>

<span data-ttu-id="67c1c-122">Os WebHooks de saída permitem que os usuários enviem mensagens de texto de um canal para seus serviços Web.</span><span class="sxs-lookup"><span data-stu-id="67c1c-122">Outgoing webhooks allow your users to send text messages from a channel to your web services.</span></span> <span data-ttu-id="67c1c-123">Após a configuração, os usuários podem @mention seu aplicativo e enviar uma mensagem para o serviço externo.</span><span class="sxs-lookup"><span data-stu-id="67c1c-123">Once configured, users can @mention your app and send a message to your external service.</span></span> <span data-ttu-id="67c1c-124">Seu serviço tem cinco segundos para enviar uma resposta para a mensagem, potencialmente contendo texto ou um cartão.</span><span class="sxs-lookup"><span data-stu-id="67c1c-124">Your service has five seconds to send a response to the message, potentially containing text or a card.</span></span>

<span data-ttu-id="67c1c-125">Os WebHooks de saída são configurados em uma base por equipe e não podem ser incluídos como parte de um aplicativo de equipes normal.</span><span class="sxs-lookup"><span data-stu-id="67c1c-125">Outgoing webhooks are configured on a per-team basis and can't be included as part of a normal Teams app.</span></span>

<span data-ttu-id="67c1c-126">Confira [criar um webhook de saída](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md).</span><span class="sxs-lookup"><span data-stu-id="67c1c-126">See [Create an outgoing webhook](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md).</span></span>

### <a name="user-scenarios"></a><span data-ttu-id="67c1c-127">Cenários de usuário</span><span class="sxs-lookup"><span data-stu-id="67c1c-127">User scenarios</span></span>

<span data-ttu-id="67c1c-128">Os WebHooks de saída são mais adequados para a conclusão de fluxos de trabalho específicos da equipe que não exigem a coleta ou troca de grandes quantidades de informações.</span><span class="sxs-lookup"><span data-stu-id="67c1c-128">Outgoing webhooks are best suited for completing team-specific workflows that don't require collecting or exchanging large amounts of information.</span></span>

## <a name="learn-more"></a><span data-ttu-id="67c1c-129">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="67c1c-129">Learn more</span></span>

* [<span data-ttu-id="67c1c-130">Planejar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="67c1c-130">Planning your app</span></span>](../../concepts/extensibility-points.md)
* [<span data-ttu-id="67c1c-131">Criar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="67c1c-131">Building your app</span></span>](../../concepts/building-an-app.md)
* [<span data-ttu-id="67c1c-132">Publicar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="67c1c-132">Publishing your app</span></span>](../../concepts/deploy-and-publish/overview.md)
