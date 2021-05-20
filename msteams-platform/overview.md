---
title: Crie aplicativos para a plataforma Microsoft Teams
author: heath-hamilton
description: Obtenha uma visão geral de como os desenvolvedores podem estender Microsoft Teams recursos com aplicativos personalizados.
ms.topic: overview
localization_priority: Normal
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: 8724b669476b11aa8cb1aca6d9586fc7ea42587d
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566506"
---
# <a name="build-apps-for-microsoft-teams"></a><span data-ttu-id="8291b-103">Crie aplicativos para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="8291b-103">Build apps for Microsoft Teams</span></span>

<span data-ttu-id="8291b-104">Microsoft Teams aplicativos trazem informações-chave, ferramentas comuns e processos confiáveis para onde as pessoas cada vez mais se reúnem, aprendem e trabalham.</span><span class="sxs-lookup"><span data-stu-id="8291b-104">Microsoft Teams apps bring key information, common tools, and trusted processes to where people increasingly gather, learn, and work.</span></span>

<span data-ttu-id="8291b-105">Aplicativos são como você estende Teams para atender às suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="8291b-105">Apps are how you extend Teams to fit your needs.</span></span> <span data-ttu-id="8291b-106">Crie algo novo para Teams ou integre um aplicativo existente.</span><span class="sxs-lookup"><span data-stu-id="8291b-106">Create something brand new for Teams or integrate an existing app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8291b-107">Iniciar aqui</span><span class="sxs-lookup"><span data-stu-id="8291b-107">Start here</span></span>](build-your-first-app/build-first-app-overview.md)

## <a name="what-are-teams-apps"></a><span data-ttu-id="8291b-108">O que são aplicativos Teams?</span><span class="sxs-lookup"><span data-stu-id="8291b-108">What are Teams apps?</span></span>

<span data-ttu-id="8291b-109">Teams aplicativos são uma combinação de [recursos](concepts/capabilities-overview.md) e pontos de [entrada.](concepts/extensibility-points.md)</span><span class="sxs-lookup"><span data-stu-id="8291b-109">Teams apps are a combination of [capabilities](concepts/capabilities-overview.md) and [entry points](concepts/extensibility-points.md).</span></span> <span data-ttu-id="8291b-110">Por exemplo, as pessoas podem conversar com *o bot* (capability) do seu aplicativo em um *canal* (ponto de entrada).</span><span class="sxs-lookup"><span data-stu-id="8291b-110">For example, people can chat with your app's *bot* (capability) in a *channel* (entry point).</span></span>

<span data-ttu-id="8291b-111">Alguns aplicativos são simples (enviar notificações), enquanto outros são complexos (gerenciar registros de pacientes).</span><span class="sxs-lookup"><span data-stu-id="8291b-111">Some apps are simple (send notifications), while others are complex (manage patient records).</span></span> <span data-ttu-id="8291b-112">Ao planejar seu aplicativo, lembre-se que Teams é um hub de colaboração.</span><span class="sxs-lookup"><span data-stu-id="8291b-112">When planning your app, remember that Teams is a collaboration hub.</span></span> <span data-ttu-id="8291b-113">Os melhores aplicativos Teams ajudam as pessoas a se expressarem e trabalharem melhor juntas.</span><span class="sxs-lookup"><span data-stu-id="8291b-113">The best Teams apps help people express themselves and work better together.</span></span>

:::row:::
   :::column span="":::

### <a name="tabs"></a><span data-ttu-id="8291b-114">Guias</span><span class="sxs-lookup"><span data-stu-id="8291b-114">Tabs</span></span>

<span data-ttu-id="8291b-115">**Obtenha informações mais convenientemente**: Às vezes você só precisa tornar as coisas mais fáceis de encontrar.</span><span class="sxs-lookup"><span data-stu-id="8291b-115">**Get information more conveniently**: Sometimes you just need to make things easier to find.</span></span> <span data-ttu-id="8291b-116">Exibir uma página importante da web em uma [guia](tabs/what-are-tabs.md), que fornece uma experiência web em tela cheia para conteúdo estático e dinâmico em Teams.</span><span class="sxs-lookup"><span data-stu-id="8291b-116">Display an important webpage in a [tab](tabs/what-are-tabs.md), which provides a full-screen web experience for static and dynamic content in Teams.</span></span>

:::image type="content" source="assets/images/overview-tabs.png" alt-text="Representação conceitual de como são as guias no Teams cliente." border="false":::

   :::column-end:::

   :::column span="":::

### <a name="bots"></a><span data-ttu-id="8291b-118">Bots</span><span class="sxs-lookup"><span data-stu-id="8291b-118">Bots</span></span>

<span data-ttu-id="8291b-119">**Transforme palavras em ações**: Muitas vezes as conversas resultam na necessidade de fazer algo (gerar um pedido, revisar meu código, verificar o status do bilhete e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="8291b-119">**Turn words into actions**: Conversations often result in the need to do something (generate an order, review my code, check ticket status, and so on).</span></span> <span data-ttu-id="8291b-120">Um [bot](bots/what-are-bots.md) pode iniciar esse tipo de fluxos de trabalho dentro Teams.</span><span class="sxs-lookup"><span data-stu-id="8291b-120">A [bot](bots/what-are-bots.md) can kick off these kinds of workflows right inside Teams.</span></span>

:::image type="content" source="assets/images/overview-bots.png" alt-text="Representação conceitual de como os bots se parecem no Teams cliente." border="false":::

   :::column-end:::

:::row-end:::

:::row:::

   :::column span="":::

### <a name="messaging-extensions"></a><span data-ttu-id="8291b-122">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="8291b-122">Messaging extensions</span></span>

<span data-ttu-id="8291b-123">**Facilite a multitarefa**: Com [extensões de mensagens,](messaging-extensions/what-are-messaging-extensions.md)você pode compartilhar rapidamente informações externas em uma conversa.</span><span class="sxs-lookup"><span data-stu-id="8291b-123">**Make it easier to multitask**: With [messaging extensions](messaging-extensions/what-are-messaging-extensions.md), you can quickly share external information in a conversation.</span></span> <span data-ttu-id="8291b-124">Você também pode agir em uma mensagem, como criar um bilhete de ajuda com base no conteúdo de um post de canal.</span><span class="sxs-lookup"><span data-stu-id="8291b-124">You also can act on a message, such as creating a help ticket based on the content of a channel post.</span></span>

:::image type="content" source="assets\images\overview-messaging.png" alt-text="Representação conceitual de como são as extensões de mensagens no Teams cliente." border="false":::

   :::column-end:::

   :::column span="":::

### <a name="webhooks"></a><span data-ttu-id="8291b-126">Webhooks</span><span class="sxs-lookup"><span data-stu-id="8291b-126">Webhooks</span></span>

<span data-ttu-id="8291b-127">**Comunique-se com aplicativos externos**: [Webhooks recebidos](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) são uma maneira simples de enviar automaticamente notificações de outro aplicativo para um canal Teams.</span><span class="sxs-lookup"><span data-stu-id="8291b-127">**Communicate with external apps**: [Incoming webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) are a simple way to automatically send notifications from another app to a Teams channel.</span></span> <span data-ttu-id="8291b-128">Com [webhooks de saída,](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks)envie uma mensagem ao seu serviço web com um @mention.</span><span class="sxs-lookup"><span data-stu-id="8291b-128">With [outgoing webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks), message your web service with an @mention.</span></span>

:::image type="content" source="assets/images/overview-connectors.png" alt-text="Representação conceitual de como os conectores se parecem no Teams cliente." border="false":::

   :::column-end:::
:::row-end:::

:::row:::

   :::column span="":::

### <a name="microsoft-graph-for-teams"></a><span data-ttu-id="8291b-130">Microsoft Graph para Teams</span><span class="sxs-lookup"><span data-stu-id="8291b-130">Microsoft Graph for Teams</span></span>

<span data-ttu-id="8291b-131">**Utilize dados Teams**: A [API de Graph microsoft para Teams](/graph/teams-concept-overview) fornece acesso a informações sobre equipes, canais, usuários e mensagens que podem ajudá-lo a criar ou aprimorar recursos para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8291b-131">**Utilize Teams data**: The [Microsoft Graph API for Teams](/graph/teams-concept-overview) provides access to information about teams, channels, users, and messages that can help you create or enhance features for your app.</span></span>

:::image type="content" source="assets/images/overview-graph.png" alt-text="Representação conceitual da API microsoft Graph para Teams." border="false":::

   :::column-end:::

   :::column span="":::
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="start-building"></a><span data-ttu-id="8291b-133">Comece a construir</span><span class="sxs-lookup"><span data-stu-id="8291b-133">Start building</span></span>

<span data-ttu-id="8291b-134">Familiarize-se rapidamente com a construção de Teams, configurando seu ambiente e criando um aplicativo simples.</span><span class="sxs-lookup"><span data-stu-id="8291b-134">Quickly familiarize yourself with building for Teams by setting up your environment and creating a simple app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8291b-135">Desenvolver seu primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="8291b-135">Build your first app</span></span>](build-your-first-app/build-first-app-overview.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="integrate-with-teams"></a><span data-ttu-id="8291b-136">Integrar com o Teams</span><span class="sxs-lookup"><span data-stu-id="8291b-136">Integrate with Teams</span></span>

<span data-ttu-id="8291b-137">Misture os recursos que os usuários adoram sobre um aplicativo, serviço ou sistema web existente com os recursos colaborativos de Teams.</span><span class="sxs-lookup"><span data-stu-id="8291b-137">Blend the features users love about an existing web app, service, or system with the collaborative features of Teams.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8291b-138">Integre um aplicativo existente</span><span class="sxs-lookup"><span data-stu-id="8291b-138">Integrate an existing app</span></span>](samples/integrating-web-apps.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="a-little-code-goes-a-long-way"></a><span data-ttu-id="8291b-139">Um pequeno código vai longe</span><span class="sxs-lookup"><span data-stu-id="8291b-139">A little code goes a long way</span></span>

<span data-ttu-id="8291b-140">Você não precisa ser um programador especialista para construir um ótimo aplicativo de Teams.</span><span class="sxs-lookup"><span data-stu-id="8291b-140">You don't need to be an expert programmer to build a great Teams app.</span></span> <span data-ttu-id="8291b-141">Experimente uma das várias soluções de código baixo.</span><span class="sxs-lookup"><span data-stu-id="8291b-141">Try one of the several low-code solutions.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8291b-142">Crie um aplicativo de código baixo</span><span class="sxs-lookup"><span data-stu-id="8291b-142">Create a low-code app</span></span>](samples/teams-low-code-solutions.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="get-ideas-for-your-app"></a><span data-ttu-id="8291b-143">Obtenha ideias para o seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="8291b-143">Get ideas for your app</span></span>

<span data-ttu-id="8291b-144">Procurando inspiração para desenvolvimento de aplicativos?</span><span class="sxs-lookup"><span data-stu-id="8291b-144">Looking for app development inspiration?</span></span> <span data-ttu-id="8291b-145">Navegue pela nossa lista de cenários do mundo real e soluções do setor com conceito de alta fidelidade simula para entender as várias maneiras Teams aplicativos podem ajudar seus usuários.</span><span class="sxs-lookup"><span data-stu-id="8291b-145">Browse our list of real-world scenarios and industry solutions with high fidelity concept mocks to understand the various ways Teams apps can help your users.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8291b-146">Veja cenários de aplicativos</span><span class="sxs-lookup"><span data-stu-id="8291b-146">See app scenarios</span></span>](https://adoption.microsoft.com/extensibility-look-book/scenarios/)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

## <a name="see-also"></a><span data-ttu-id="8291b-147">Confira também</span><span class="sxs-lookup"><span data-stu-id="8291b-147">See also</span></span>

* [<span data-ttu-id="8291b-148">Adicione um botão Compartilhar a Teams ao seu site</span><span class="sxs-lookup"><span data-stu-id="8291b-148">Add a Share-to-Teams button to your website</span></span>](concepts/build-and-test/share-to-teams.md)
* [<span data-ttu-id="8291b-149">Projete seu aplicativo de Teams</span><span class="sxs-lookup"><span data-stu-id="8291b-149">Design your Teams app</span></span>](concepts/design/design-teams-app-overview.md)
* [<span data-ttu-id="8291b-150">Microsoft Teams Cliente JavaScript SDK</span><span class="sxs-lookup"><span data-stu-id="8291b-150">Microsoft Teams JavaScript client SDK</span></span>](/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* <span data-ttu-id="8291b-151">Bot Framework SDK para [JavaScript](https://github.com/Microsoft/botbuilder-js) e [.NET](https://github.com/Microsoft/botbuilder-dotnet/)</span><span class="sxs-lookup"><span data-stu-id="8291b-151">Bot Framework SDK for [JavaScript](https://github.com/Microsoft/botbuilder-js) and [.NET](https://github.com/Microsoft/botbuilder-dotnet/)</span></span>
* [<span data-ttu-id="8291b-152">Distribua seu aplicativo de Teams</span><span class="sxs-lookup"><span data-stu-id="8291b-152">Distribute your Teams app</span></span>](concepts/deploy-and-publish/apps-publish-overview.md)
