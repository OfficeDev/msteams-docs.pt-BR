---
title: Criar aplicativos para a Microsoft Teams plataforma
author: heath-hamilton
description: Obter uma visão geral de como os desenvolvedores podem estender Microsoft Teams recursos com aplicativos personalizados.
ms.topic: overview
localization_priority: Normal
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: 645b8087b367dd3cc9f5efdd53c53974307ce65e
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2021
ms.locfileid: "52630485"
---
# <a name="build-apps-for-microsoft-teams"></a><span data-ttu-id="1fac3-103">Crie aplicativos para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="1fac3-103">Build apps for Microsoft Teams</span></span>

<span data-ttu-id="1fac3-104">Microsoft Teams aplicativos trazem informações importantes, ferramentas comuns e processos confiáveis para onde as pessoas coletam, aprendem e trabalham cada vez mais.</span><span class="sxs-lookup"><span data-stu-id="1fac3-104">Microsoft Teams apps bring key information, common tools, and trusted processes to where people increasingly gather, learn, and work.</span></span>

<span data-ttu-id="1fac3-105">Aplicativos são como você estende Teams para se ajustar às suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="1fac3-105">Apps are how you extend Teams to fit your needs.</span></span> <span data-ttu-id="1fac3-106">Crie algo novo para Teams ou integre um aplicativo existente.</span><span class="sxs-lookup"><span data-stu-id="1fac3-106">Create something brand new for Teams or integrate an existing app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1fac3-107">Iniciar aqui</span><span class="sxs-lookup"><span data-stu-id="1fac3-107">Start here</span></span>](build-your-first-app/build-first-app-overview.md)

## <a name="what-are-teams-apps"></a><span data-ttu-id="1fac3-108">O que Teams aplicativos?</span><span class="sxs-lookup"><span data-stu-id="1fac3-108">What are Teams apps?</span></span>

<span data-ttu-id="1fac3-109">Teams aplicativos são uma combinação de [recursos.](concepts/capabilities-overview.md)</span><span class="sxs-lookup"><span data-stu-id="1fac3-109">Teams apps are a combination of [capabilities](concepts/capabilities-overview.md).</span></span> <span data-ttu-id="1fac3-110">Alguns aplicativos são simples (notificações de envio), enquanto outros são complexos (gerenciar registros de pacientes).</span><span class="sxs-lookup"><span data-stu-id="1fac3-110">Some apps are simple (send notifications), while others are complex (manage patient records).</span></span> <span data-ttu-id="1fac3-111">Ao planejar seu aplicativo, lembre-se de que Teams é um hub de colaboração.</span><span class="sxs-lookup"><span data-stu-id="1fac3-111">When planning your app, remember that Teams is a collaboration hub.</span></span> <span data-ttu-id="1fac3-112">A melhor Teams aplicativos ajudam as pessoas a se expressarem e trabalharem melhor juntas.</span><span class="sxs-lookup"><span data-stu-id="1fac3-112">The best Teams apps help people express themselves and work better together.</span></span>

### <a name="personal-apps"></a><span data-ttu-id="1fac3-113">Aplicativos pessoais</span><span class="sxs-lookup"><span data-stu-id="1fac3-113">Personal apps</span></span>

:::row:::
   :::column span="1":::

<span data-ttu-id="1fac3-114">**Ajude as pessoas** a se concentrarem : um aplicativo [pessoal](concepts/design/personal-apps.md) é um espaço dedicado ou bot para ajudar os usuários a se concentrarem em suas próprias tarefas ou exibir atividades importantes para eles.</span><span class="sxs-lookup"><span data-stu-id="1fac3-114">**Help people focus**: A [personal app](concepts/design/personal-apps.md) is a dedicated space or bot to help users focus on their own tasks or view activities important to them.</span></span>

   :::column-end:::

   :::column span="3":::

:::image type="content" source="assets/images/overview-personal-apps-2021.png" alt-text="Representação conceitual de como os aplicativos pessoais são no cliente Teams cliente." border="false":::

   :::column-end:::

:::row-end:::

### <a name="tabs"></a><span data-ttu-id="1fac3-116">Guias</span><span class="sxs-lookup"><span data-stu-id="1fac3-116">Tabs</span></span>

:::row:::
   :::column span="1":::

<span data-ttu-id="1fac3-117">**Colabore de** forma mais conveniente: exibe seu conteúdo baseado na Web em uma [guia](tabs/what-are-tabs.md) onde as pessoas podem discutir e trabalhar nele juntos.</span><span class="sxs-lookup"><span data-stu-id="1fac3-117">**Collaborate more conveniently**: Display your web-based content in a [tab](tabs/what-are-tabs.md) where people can discuss and work on it together.</span></span>

   :::column-end:::

   :::column span="3":::

:::image type="content" source="assets/images/overview-channel-chat-apps-2021.png" alt-text="Representação conceitual de como as guias são no cliente Teams cliente." border="false":::

   :::column-end:::

:::row-end:::

### <a name="bots"></a><span data-ttu-id="1fac3-119">Bots</span><span class="sxs-lookup"><span data-stu-id="1fac3-119">Bots</span></span>

:::row:::
   :::column span="1":::

<span data-ttu-id="1fac3-120">**Transformar palavras em ações**: as conversas geralmente resultam na necessidade de fazer algo (gerar um pedido, revisar meu código, verificar o status do tíquete e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="1fac3-120">**Turn words into actions**: Conversations often result in the need to do something (generate an order, review my code, check ticket status, and so on).</span></span> <span data-ttu-id="1fac3-121">Um [bot](bots/what-are-bots.md) pode dar início a esses tipos de fluxos de trabalho dentro Teams.</span><span class="sxs-lookup"><span data-stu-id="1fac3-121">A [bot](bots/what-are-bots.md) can kick off these kinds of workflows right inside Teams.</span></span>

   :::column-end:::

   :::column span="3":::

:::image type="content" source="assets/images/overview-bots-2021.png" alt-text="Representação conceitual de como os bots são no Teams cliente." border="false":::

   :::column-end:::

:::row-end:::

### <a name="messaging-extensions"></a><span data-ttu-id="1fac3-123">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="1fac3-123">Messaging extensions</span></span>

:::row:::

   :::column span="1":::

<span data-ttu-id="1fac3-124">**Facilita a multitarefa**: Com extensões de mensagens, você pode compartilhar rapidamente informações [externas](messaging-extensions/what-are-messaging-extensions.md)em uma conversa.</span><span class="sxs-lookup"><span data-stu-id="1fac3-124">**Make it easier to multitask**: With [messaging extensions](messaging-extensions/what-are-messaging-extensions.md), you can quickly share external information in a conversation.</span></span> <span data-ttu-id="1fac3-125">Você também pode agir em uma mensagem, como criar um tíquete de ajuda com base no conteúdo de uma postagem de canal.</span><span class="sxs-lookup"><span data-stu-id="1fac3-125">You also can act on a message, such as creating a help ticket based on the content of a channel post.</span></span>

   :::column-end:::

   :::column span="3":::

:::image type="content" source="assets/images/overview-messaging-extensions-2021.png" alt-text="Representação conceitual de como são as extensões de mensagens no cliente Teams de mensagens." border="false":::

   :::column-end:::
:::row-end:::

### <a name="meeting-extensions"></a><span data-ttu-id="1fac3-127">Extensões de reunião</span><span class="sxs-lookup"><span data-stu-id="1fac3-127">Meeting extensions</span></span>

:::row:::

   :::column span="1":::

<span data-ttu-id="1fac3-128">**Criar aplicativos para reuniões**: há algumas opções para incorporar seu aplicativo à [experiência de Teams chamada.](apps-in-teams-meetings/design/designing-apps-in-meetings.md)</span><span class="sxs-lookup"><span data-stu-id="1fac3-128">**Create apps for meetings**: There are a few options for [incorporating your app into the Teams calling experience](apps-in-teams-meetings/design/designing-apps-in-meetings.md).</span></span>

   :::column-end:::

   :::column span="3":::

:::image type="content" source="assets/images/overview-meeting-extensions-2021.png" alt-text="Representação conceitual da aparência das extensões de reunião no cliente Teams de reunião." border="false":::

   :::column-end:::
:::row-end:::

### <a name="webhooks-and-connectors"></a><span data-ttu-id="1fac3-130">Webhooks e conectores</span><span class="sxs-lookup"><span data-stu-id="1fac3-130">Webhooks and connectors</span></span>

:::row:::

   :::column span="":::

<span data-ttu-id="1fac3-131">**Comunicar-se com aplicativos** [externos: os webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) de entrada são uma maneira simples de enviar notificações automaticamente de outro aplicativo para um Teams canal.</span><span class="sxs-lookup"><span data-stu-id="1fac3-131">**Communicate with external apps**: [Incoming webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) are a simple way to automatically send notifications from another app to a Teams channel.</span></span> <span data-ttu-id="1fac3-132">Com [webhooks de saída](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks), mensagem seu serviço Web com um @mention.</span><span class="sxs-lookup"><span data-stu-id="1fac3-132">With [outgoing webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks), message your web service with an @mention.</span></span>

   :::column-end:::

   :::column span="":::

:::image type="content" source="assets/images/overview-connectors.png" alt-text="Representação conceitual de como os conectores são no Teams cliente." border="false":::

   :::column-end:::
:::row-end:::

### <a name="microsoft-graph-for-teams"></a><span data-ttu-id="1fac3-134">Microsoft Graph para Teams</span><span class="sxs-lookup"><span data-stu-id="1fac3-134">Microsoft Graph for Teams</span></span>

:::row:::

   :::column span="":::

<span data-ttu-id="1fac3-135">**Utilize Teams** dados : [a API](/graph/teams-concept-overview) do Microsoft Graph para Teams fornece acesso a informações sobre equipes, canais, usuários e mensagens que podem ajudá-lo a criar ou aprimorar recursos para seu aplicativo (como notificações rich).</span><span class="sxs-lookup"><span data-stu-id="1fac3-135">**Utilize Teams data**: The [Microsoft Graph API for Teams](/graph/teams-concept-overview) provides access to information about teams, channels, users, and messages that can help you create or enhance features for your app (such as rich notifications).</span></span>

   :::column-end:::

   :::column span="":::

:::image type="content" source="assets/images/overview-graph.png" alt-text="Representação conceitual da API Graph microsoft para Teams." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="start-building"></a><span data-ttu-id="1fac3-137">Iniciar a criação</span><span class="sxs-lookup"><span data-stu-id="1fac3-137">Start building</span></span>

<span data-ttu-id="1fac3-138">Familiarize-se rapidamente com a criação para Teams configurando seu ambiente e criando um aplicativo simples.</span><span class="sxs-lookup"><span data-stu-id="1fac3-138">Quickly familiarize yourself with building for Teams by setting up your environment and creating a simple app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1fac3-139">Desenvolver seu primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="1fac3-139">Build your first app</span></span>](build-your-first-app/build-first-app-overview.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="integrate-with-teams"></a><span data-ttu-id="1fac3-140">Integrar com o Teams</span><span class="sxs-lookup"><span data-stu-id="1fac3-140">Integrate with Teams</span></span>

<span data-ttu-id="1fac3-141">Mesclar os recursos que os usuários adoram sobre um aplicativo Web, serviço ou sistema existente com os recursos colaborativos Teams.</span><span class="sxs-lookup"><span data-stu-id="1fac3-141">Blend the features users love about an existing web app, service, or system with the collaborative features of Teams.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1fac3-142">Integrar um aplicativo existente</span><span class="sxs-lookup"><span data-stu-id="1fac3-142">Integrate an existing app</span></span>](samples/integrating-web-apps.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="a-little-code-goes-a-long-way"></a><span data-ttu-id="1fac3-143">Um pouco de código é muito longo</span><span class="sxs-lookup"><span data-stu-id="1fac3-143">A little code goes a long way</span></span>

<span data-ttu-id="1fac3-144">Você não precisa ser um programador especialista para criar um aplicativo Teams excelente.</span><span class="sxs-lookup"><span data-stu-id="1fac3-144">You don't need to be an expert programmer to build a great Teams app.</span></span> <span data-ttu-id="1fac3-145">Experimente uma das várias soluções de código baixo.</span><span class="sxs-lookup"><span data-stu-id="1fac3-145">Try one of several low-code solutions.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1fac3-146">Criar um aplicativo de código baixo</span><span class="sxs-lookup"><span data-stu-id="1fac3-146">Create a low-code app</span></span>](samples/teams-low-code-solutions.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="get-ideas-for-your-app"></a><span data-ttu-id="1fac3-147">Obter ideias para seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="1fac3-147">Get ideas for your app</span></span>

<span data-ttu-id="1fac3-148">Procurando inspiração para desenvolvimento de aplicativos?</span><span class="sxs-lookup"><span data-stu-id="1fac3-148">Looking for app development inspiration?</span></span> <span data-ttu-id="1fac3-149">Navegue pela nossa lista de cenários reais e soluções do setor com simulações de conceito de alta fidelidade para entender as várias maneiras Teams aplicativos podem ajudar seus usuários.</span><span class="sxs-lookup"><span data-stu-id="1fac3-149">Browse our list of real-world scenarios and industry solutions with high fidelity concept mocks to understand the various ways Teams apps can help your users.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1fac3-150">Consulte cenários de aplicativo</span><span class="sxs-lookup"><span data-stu-id="1fac3-150">See app scenarios</span></span>](https://adoption.microsoft.com/extensibility-look-book/scenarios/)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

## <a name="see-also"></a><span data-ttu-id="1fac3-151">Confira também</span><span class="sxs-lookup"><span data-stu-id="1fac3-151">See also</span></span>

* [<span data-ttu-id="1fac3-152">Adicionar um botão Compartilhar para Teams seu site</span><span class="sxs-lookup"><span data-stu-id="1fac3-152">Add a Share-to-Teams button to your website</span></span>](concepts/build-and-test/share-to-teams.md)
* [<span data-ttu-id="1fac3-153">Projetar seu Teams aplicativo</span><span class="sxs-lookup"><span data-stu-id="1fac3-153">Design your Teams app</span></span>](concepts/design/design-teams-app-overview.md)
* [<span data-ttu-id="1fac3-154">Microsoft Teams SDK do cliente JavaScript</span><span class="sxs-lookup"><span data-stu-id="1fac3-154">Microsoft Teams JavaScript client SDK</span></span>](/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* <span data-ttu-id="1fac3-155">SDK da Estrutura de Bots para [JavaScript](https://github.com/Microsoft/botbuilder-js) e [.NET](https://github.com/Microsoft/botbuilder-dotnet/)</span><span class="sxs-lookup"><span data-stu-id="1fac3-155">Bot Framework SDK for [JavaScript](https://github.com/Microsoft/botbuilder-js) and [.NET](https://github.com/Microsoft/botbuilder-dotnet/)</span></span>
* [<span data-ttu-id="1fac3-156">Distribuir seu Teams app</span><span class="sxs-lookup"><span data-stu-id="1fac3-156">Distribute your Teams app</span></span>](concepts/deploy-and-publish/apps-publish-overview.md)
