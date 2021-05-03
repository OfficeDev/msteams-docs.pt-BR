---
title: Criar aplicativos para a Microsoft Teams plataforma
author: heath-hamilton
description: Obter uma visão geral de como os desenvolvedores podem estender Microsoft Teams recursos com aplicativos personalizados.
ms.topic: overview
localization_priority: Normal
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: 69c36cf5f925bdb9802e7ec081a7765187a06128
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101839"
---
# <a name="build-apps-for-microsoft-teams"></a><span data-ttu-id="07a09-103">Crie aplicativos para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="07a09-103">Build apps for Microsoft Teams</span></span>

<span data-ttu-id="07a09-104">Microsoft Teams aplicativos trazem informações importantes, ferramentas comuns e processos confiáveis para onde as pessoas coletam, aprendem e trabalham cada vez mais.</span><span class="sxs-lookup"><span data-stu-id="07a09-104">Microsoft Teams apps bring key information, common tools, and trusted processes to where people increasingly gather, learn, and work.</span></span>

<span data-ttu-id="07a09-105">Aplicativos são como você estende Teams para se ajustar às suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="07a09-105">Apps are how you extend Teams to fit your needs.</span></span> <span data-ttu-id="07a09-106">Crie algo novo para Teams ou integre um aplicativo existente.</span><span class="sxs-lookup"><span data-stu-id="07a09-106">Create something brand new for Teams or integrate an existing app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="07a09-107">Iniciar aqui</span><span class="sxs-lookup"><span data-stu-id="07a09-107">Start here</span></span>](build-your-first-app/build-first-app-overview.md)

## <a name="what-are-teams-apps"></a><span data-ttu-id="07a09-108">O que Teams aplicativos?</span><span class="sxs-lookup"><span data-stu-id="07a09-108">What are Teams apps?</span></span>

<span data-ttu-id="07a09-109">Teams aplicativos são uma combinação de [recursos e](concepts/capabilities-overview.md) pontos [de entrada.](concepts/extensibility-points.md)</span><span class="sxs-lookup"><span data-stu-id="07a09-109">Teams apps are a combination of [capabilities](concepts/capabilities-overview.md) and [entry points](concepts/extensibility-points.md).</span></span> <span data-ttu-id="07a09-110">Por exemplo, as pessoas podem conversar com o bot (recurso) do seu *aplicativo* em um *canal* (ponto de entrada).</span><span class="sxs-lookup"><span data-stu-id="07a09-110">For example, people can chat with your app's *bot* (capability) in a *channel* (entry point).</span></span>

<span data-ttu-id="07a09-111">Alguns aplicativos são simples (notificações de envio), enquanto outros são complexos (gerenciar registros de pacientes).</span><span class="sxs-lookup"><span data-stu-id="07a09-111">Some apps are simple (send notifications), while others are complex (manage patient records).</span></span> <span data-ttu-id="07a09-112">Ao planejar seu aplicativo, lembre-se de que Teams é um hub de colaboração.</span><span class="sxs-lookup"><span data-stu-id="07a09-112">When planning your app, remember that Teams is a collaboration hub.</span></span> <span data-ttu-id="07a09-113">A melhor Teams aplicativos ajudam as pessoas a se expressarem e trabalharem melhor juntas.</span><span class="sxs-lookup"><span data-stu-id="07a09-113">The best Teams apps help people express themselves and work better together.</span></span>

:::row:::
   :::column span="":::

### <a name="tabs"></a><span data-ttu-id="07a09-114">Guias</span><span class="sxs-lookup"><span data-stu-id="07a09-114">Tabs</span></span>

<span data-ttu-id="07a09-115">**Obter informações de forma mais conveniente:** às vezes, você só precisa tornar as coisas mais fáceis de encontrar.</span><span class="sxs-lookup"><span data-stu-id="07a09-115">**Get information more conveniently**: Sometimes you just need to make things easier to find.</span></span> <span data-ttu-id="07a09-116">Exibe uma página da Web importante em uma [guia](tabs/what-are-tabs.md), que fornece uma experiência da Web de tela inteira para conteúdo estático e dinâmico Teams.</span><span class="sxs-lookup"><span data-stu-id="07a09-116">Display an important webpage in a [tab](tabs/what-are-tabs.md), which provides a full-screen web experience for static and dynamic content in Teams.</span></span>

:::image type="content" source="assets/images/overview-tabs.png" alt-text="Representação conceitual de como as guias são no cliente Teams cliente." border="false":::

   :::column-end:::

   :::column span="":::

### <a name="bots"></a><span data-ttu-id="07a09-118">Bots</span><span class="sxs-lookup"><span data-stu-id="07a09-118">Bots</span></span>

<span data-ttu-id="07a09-119">**Transformar palavras em ações**: as conversas geralmente resultam na necessidade de fazer algo (gerar um pedido, revisar meu código, verificar o status do tíquete e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="07a09-119">**Turn words into actions**: Conversations often result in the need to do something (generate an order, review my code, check ticket status, and so on).</span></span> <span data-ttu-id="07a09-120">Um [bot](bots/what-are-bots.md) pode dar início a esses tipos de fluxos de trabalho dentro Teams.</span><span class="sxs-lookup"><span data-stu-id="07a09-120">A [bot](bots/what-are-bots.md) can kick off these kinds of workflows right inside Teams.</span></span>

:::image type="content" source="assets/images/overview-bots.png" alt-text="Representação conceitual de como os bots são no Teams cliente." border="false":::

   :::column-end:::

:::row-end:::

:::row:::

   :::column span="":::

### <a name="messaging-extensions"></a><span data-ttu-id="07a09-122">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="07a09-122">Messaging extensions</span></span>

<span data-ttu-id="07a09-123">**Facilita a multitarefa**: Com extensões de mensagens, você pode compartilhar rapidamente informações [externas](messaging-extensions/what-are-messaging-extensions.md)em uma conversa.</span><span class="sxs-lookup"><span data-stu-id="07a09-123">**Make it easier to multitask**: With [messaging extensions](messaging-extensions/what-are-messaging-extensions.md), you can quickly share external information in a conversation.</span></span> <span data-ttu-id="07a09-124">Você também pode agir em uma mensagem, como criar um tíquete de ajuda com base no conteúdo de uma postagem de canal.</span><span class="sxs-lookup"><span data-stu-id="07a09-124">You also can act on a message, such as creating a help ticket based on the content of a channel post.</span></span>

:::image type="content" source="assets\images\overview-messaging.png" alt-text="Representação conceitual de como são as extensões de mensagens no cliente Teams de mensagens." border="false":::

   :::column-end:::

   :::column span="":::

### <a name="webhooks"></a><span data-ttu-id="07a09-126">Webhooks</span><span class="sxs-lookup"><span data-stu-id="07a09-126">Webhooks</span></span>

<span data-ttu-id="07a09-127">**Comunicar-se com aplicativos** [externos: os webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) de entrada são uma maneira simples de enviar notificações automaticamente de outro aplicativo para um Teams canal.</span><span class="sxs-lookup"><span data-stu-id="07a09-127">**Communicate with external apps**: [Incoming webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) are a simple way to automatically send notifications from another app to a Teams channel.</span></span> <span data-ttu-id="07a09-128">Com [webhooks de saída](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks), mensagem seu serviço Web com um @mention.</span><span class="sxs-lookup"><span data-stu-id="07a09-128">With [outgoing webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks), message your web service with an @mention.</span></span>

:::image type="content" source="assets/images/overview-connectors.png" alt-text="Representação conceitual de como os conectores são no Teams cliente." border="false":::

   :::column-end:::
:::row-end:::

:::row:::

   :::column span="":::

### <a name="microsoft-graph-for-teams"></a><span data-ttu-id="07a09-130">Microsoft Graph para Teams</span><span class="sxs-lookup"><span data-stu-id="07a09-130">Microsoft Graph for Teams</span></span>

<span data-ttu-id="07a09-131">**Utilize Teams** dados : [a API](https://docs.microsoft.com/graph/teams-concept-overview) do Microsoft Graph para Teams fornece acesso a informações sobre equipes, canais, usuários e mensagens que podem ajudá-lo a criar ou aprimorar recursos para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="07a09-131">**Utilize Teams data**: The [Microsoft Graph API for Teams](https://docs.microsoft.com/graph/teams-concept-overview) provides access to information about teams, channels, users, and messages that can help you create or enhance features for your app.</span></span>

:::image type="content" source="assets/images/overview-graph.png" alt-text="Representação conceitual da API Graph microsoft para Teams." border="false":::

   :::column-end:::

   :::column span="":::
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="start-building"></a><span data-ttu-id="07a09-133">Iniciar a criação</span><span class="sxs-lookup"><span data-stu-id="07a09-133">Start building</span></span>

<span data-ttu-id="07a09-134">Familiarize-se rapidamente com a criação para Teams configurando seu ambiente e criando um aplicativo simples.</span><span class="sxs-lookup"><span data-stu-id="07a09-134">Quickly familiarize yourself with building for Teams by setting up your environment and creating a simple app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="07a09-135">Desenvolver seu primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="07a09-135">Build your first app</span></span>](build-your-first-app/build-first-app-overview.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="integrate-with-teams"></a><span data-ttu-id="07a09-136">Integrar com o Teams</span><span class="sxs-lookup"><span data-stu-id="07a09-136">Integrate with Teams</span></span>

<span data-ttu-id="07a09-137">Mesclar os recursos que os usuários adoram sobre um aplicativo Web, serviço ou sistema existente com os recursos colaborativos Teams.</span><span class="sxs-lookup"><span data-stu-id="07a09-137">Blend the features users love about an existing web app, service, or system with the collaborative features of Teams.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="07a09-138">Integrar um aplicativo existente</span><span class="sxs-lookup"><span data-stu-id="07a09-138">Integrate an existing app</span></span>](samples/integrating-web-apps.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="a-little-code-goes-a-long-way"></a><span data-ttu-id="07a09-139">Um pouco de código é muito longo</span><span class="sxs-lookup"><span data-stu-id="07a09-139">A little code goes a long way</span></span>

<span data-ttu-id="07a09-140">Você não precisa ser um programador especialista para criar um aplicativo Teams excelente.</span><span class="sxs-lookup"><span data-stu-id="07a09-140">You don't need to be an expert programmer to build a great Teams app.</span></span> <span data-ttu-id="07a09-141">Experimente uma das várias soluções de código baixo.</span><span class="sxs-lookup"><span data-stu-id="07a09-141">Try one of several low-code solutions.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="07a09-142">Criar um aplicativo de código baixo</span><span class="sxs-lookup"><span data-stu-id="07a09-142">Create a low-code app</span></span>](samples/teams-low-code-solutions.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="get-ideas-for-your-app"></a><span data-ttu-id="07a09-143">Obter ideias para seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="07a09-143">Get ideas for your app</span></span>

<span data-ttu-id="07a09-144">Procurando inspiração para desenvolvimento de aplicativos?</span><span class="sxs-lookup"><span data-stu-id="07a09-144">Looking for app development inspiration?</span></span> <span data-ttu-id="07a09-145">Navegue pela nossa lista de cenários reais e soluções do setor com simulações de conceito de alta fidelidade para entender as várias maneiras Teams aplicativos podem ajudar seus usuários.</span><span class="sxs-lookup"><span data-stu-id="07a09-145">Browse our list of real-world scenarios and industry solutions with high fidelity concept mocks to understand the various ways Teams apps can help your users.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="07a09-146">Consulte cenários de aplicativo</span><span class="sxs-lookup"><span data-stu-id="07a09-146">See app scenarios</span></span>](https://adoption.microsoft.com/extensibility-look-book/scenarios/)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

## <a name="see-also"></a><span data-ttu-id="07a09-147">Confira também</span><span class="sxs-lookup"><span data-stu-id="07a09-147">See also</span></span>

* [<span data-ttu-id="07a09-148">Adicionar um botão Compartilhar para Teams seu site</span><span class="sxs-lookup"><span data-stu-id="07a09-148">Add a Share-to-Teams button to your website</span></span>](concepts/build-and-test/share-to-teams.md)
* [<span data-ttu-id="07a09-149">Projetar seu Teams aplicativo</span><span class="sxs-lookup"><span data-stu-id="07a09-149">Design your Teams app</span></span>](concepts/design/design-teams-app-overview.md)
* [<span data-ttu-id="07a09-150">Microsoft Teams SDK do cliente JavaScript</span><span class="sxs-lookup"><span data-stu-id="07a09-150">Microsoft Teams JavaScript client SDK</span></span>](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* <span data-ttu-id="07a09-151">SDK da Estrutura de Bots para [JavaScript](https://github.com/Microsoft/botbuilder-js) e [.NET](https://github.com/Microsoft/botbuilder-dotnet/)</span><span class="sxs-lookup"><span data-stu-id="07a09-151">Bot Framework SDK for [JavaScript](https://github.com/Microsoft/botbuilder-js) and [.NET](https://github.com/Microsoft/botbuilder-dotnet/)</span></span>
* [<span data-ttu-id="07a09-152">Distribuir seu Teams app</span><span class="sxs-lookup"><span data-stu-id="07a09-152">Distribute your Teams app</span></span>](concepts/deploy-and-publish/apps-publish-overview.md)
