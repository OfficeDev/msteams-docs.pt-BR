---
title: Criar aplicativos para a plataforma Microsoft Teams
author: heath-hamilton
description: Obter uma visão geral de como os desenvolvedores podem estender os recursos do Microsoft Teams com aplicativos personalizados.
ms.topic: overview
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: e40d2b0d8b0d12e6275b97f79d103310d22f9720
ms.sourcegitcommit: 3bd2627b7a334568f61ccc606395e3d89aa521d9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/31/2021
ms.locfileid: "51475925"
---
# <a name="build-apps-for-microsoft-teams"></a><span data-ttu-id="aafb7-103">Crie aplicativos para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="aafb7-103">Build apps for Microsoft Teams</span></span>

<span data-ttu-id="aafb7-104">Os aplicativos do Microsoft Teams trazem informações importantes, ferramentas comuns e processos confiáveis para onde as pessoas coletam, aprendem e trabalham cada vez mais.</span><span class="sxs-lookup"><span data-stu-id="aafb7-104">Microsoft Teams apps bring key information, common tools, and trusted processes to where people increasingly gather, learn, and work.</span></span>

<span data-ttu-id="aafb7-105">Aplicativos são como você estende o Teams para se ajustar às suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="aafb7-105">Apps are how you extend Teams to fit your needs.</span></span> <span data-ttu-id="aafb7-106">Crie algo novo para o Teams ou integre um aplicativo existente.</span><span class="sxs-lookup"><span data-stu-id="aafb7-106">Create something brand new for Teams or integrate an existing app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="aafb7-107">Iniciar aqui</span><span class="sxs-lookup"><span data-stu-id="aafb7-107">Start here</span></span>](build-your-first-app/build-first-app-overview.md)

## <a name="what-are-teams-apps"></a><span data-ttu-id="aafb7-108">O que são aplicativos do Teams?</span><span class="sxs-lookup"><span data-stu-id="aafb7-108">What are Teams apps?</span></span>

<span data-ttu-id="aafb7-109">Os aplicativos do Teams são uma combinação de [recursos](concepts/capabilities-overview.md) e [pontos de entrada.](concepts/extensibility-points.md)</span><span class="sxs-lookup"><span data-stu-id="aafb7-109">Teams apps are a combination of [capabilities](concepts/capabilities-overview.md) and [entry points](concepts/extensibility-points.md).</span></span> <span data-ttu-id="aafb7-110">Por exemplo, as pessoas podem conversar com o bot (recurso) do seu *aplicativo* em um *canal* (ponto de entrada).</span><span class="sxs-lookup"><span data-stu-id="aafb7-110">For example, people can chat with your app's *bot* (capability) in a *channel* (entry point).</span></span>

<span data-ttu-id="aafb7-111">Alguns aplicativos são simples (notificações de envio), enquanto outros são complexos (gerenciar registros de pacientes).</span><span class="sxs-lookup"><span data-stu-id="aafb7-111">Some apps are simple (send notifications), while others are complex (manage patient records).</span></span> <span data-ttu-id="aafb7-112">Ao planejar seu aplicativo, lembre-se de que o Teams é um hub de colaboração.</span><span class="sxs-lookup"><span data-stu-id="aafb7-112">When planning your app, remember that Teams is a collaboration hub.</span></span> <span data-ttu-id="aafb7-113">Os melhores aplicativos do Teams ajudam as pessoas a se expressarem e trabalharem melhor juntas.</span><span class="sxs-lookup"><span data-stu-id="aafb7-113">The best Teams apps help people express themselves and work better together.</span></span>

:::row:::
   :::column span="":::

### <a name="tabs"></a><span data-ttu-id="aafb7-114">Guias</span><span class="sxs-lookup"><span data-stu-id="aafb7-114">Tabs</span></span>

<span data-ttu-id="aafb7-115">**Obter informações de forma mais conveniente:** às vezes, você só precisa tornar as coisas mais fáceis de encontrar.</span><span class="sxs-lookup"><span data-stu-id="aafb7-115">**Get information more conveniently**: Sometimes you just need to make things easier to find.</span></span> <span data-ttu-id="aafb7-116">Exibe uma página da Web importante em [uma guia](tabs/what-are-tabs.md), que fornece uma experiência da Web de tela inteira para conteúdo estático e dinâmico no Teams.</span><span class="sxs-lookup"><span data-stu-id="aafb7-116">Display an important webpage in a [tab](tabs/what-are-tabs.md), which provides a full-screen web experience for static and dynamic content in Teams.</span></span>

:::image type="content" source="assets/images/overview-tabs.png" alt-text="Representação conceitual de como as guias são no cliente do Teams." border="false":::

   :::column-end:::

   :::column span="":::

### <a name="bots"></a><span data-ttu-id="aafb7-118">Bots</span><span class="sxs-lookup"><span data-stu-id="aafb7-118">Bots</span></span>

<span data-ttu-id="aafb7-119">**Transformar palavras em ações**: as conversas geralmente resultam na necessidade de fazer algo (gerar um pedido, revisar meu código, verificar o status do tíquete, etc.).</span><span class="sxs-lookup"><span data-stu-id="aafb7-119">**Turn words into actions**: Conversations often result in the need to do something (generate an order, review my code, check ticket status, etc.).</span></span> <span data-ttu-id="aafb7-120">Um [bot](bots/what-are-bots.md) pode dar início a esses tipos de fluxos de trabalho dentro do Teams.</span><span class="sxs-lookup"><span data-stu-id="aafb7-120">A [bot](bots/what-are-bots.md) can kick off these kinds of workflows right inside Teams.</span></span>

:::image type="content" source="assets/images/overview-bots.png" alt-text="Representação conceitual de como os bots são no cliente do Teams." border="false":::

   :::column-end:::

:::row-end:::

:::row:::

   :::column span="":::

### <a name="messaging-extensions"></a><span data-ttu-id="aafb7-122">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="aafb7-122">Messaging extensions</span></span>

<span data-ttu-id="aafb7-123">**Facilita a multitarefa**: Com extensões de mensagens, você pode compartilhar rapidamente informações [externas](messaging-extensions/what-are-messaging-extensions.md)em uma conversa.</span><span class="sxs-lookup"><span data-stu-id="aafb7-123">**Make it easier to multitask**: With [messaging extensions](messaging-extensions/what-are-messaging-extensions.md), you can quickly share external information in a conversation.</span></span> <span data-ttu-id="aafb7-124">Você também pode agir em uma mensagem, como criar um tíquete de ajuda com base no conteúdo de uma postagem de canal.</span><span class="sxs-lookup"><span data-stu-id="aafb7-124">You also can act on a message, such as creating a help ticket based on the content of a channel post.</span></span>

:::image type="content" source="assets\images\overview-messaging.png" alt-text="Representação conceitual de como são as extensões de mensagens no cliente do Teams." border="false":::

   :::column-end:::

   :::column span="":::

### <a name="webhooks"></a><span data-ttu-id="aafb7-126">Webhooks</span><span class="sxs-lookup"><span data-stu-id="aafb7-126">Webhooks</span></span>

<span data-ttu-id="aafb7-127">**Comunicar-se com aplicativos** externos : [Webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) de entrada são uma maneira simples de enviar notificações automaticamente de outro aplicativo para um canal do Teams.</span><span class="sxs-lookup"><span data-stu-id="aafb7-127">**Communicate with external apps**: [Incoming webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) are a simple way to automatically send notifications from another app to a Teams channel.</span></span> <span data-ttu-id="aafb7-128">Com [webhooks de saída](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks), mensagem seu serviço Web com um @mention.</span><span class="sxs-lookup"><span data-stu-id="aafb7-128">With [outgoing webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks), message your web service with an @mention.</span></span>

:::image type="content" source="assets/images/overview-connectors.png" alt-text="Representação conceitual de como os conectores são no cliente do Teams." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
   :::column-end:::
:::row-end:::

### <a name="microsoft-graph-for-teams"></a><span data-ttu-id="aafb7-130">Microsoft Graph para Teams</span><span class="sxs-lookup"><span data-stu-id="aafb7-130">Microsoft Graph for Teams</span></span>

<span data-ttu-id="aafb7-131">**Use dados do Teams**: A [API do Microsoft Graph](https://docs.microsoft.com/graph/teams-concept-overview) para Teams fornece acesso a informações sobre equipes, canais, usuários e mensagens que podem ajudá-lo a criar ou aprimorar recursos para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="aafb7-131">**Utilize Teams data**: The [Microsoft Graph API for Teams](https://docs.microsoft.com/graph/teams-concept-overview) provides access to information about teams, channels, users, and messages that can help you create or enhance features for your app.</span></span>

:::image type="content" source="assets/images/overview-graph.png" alt-text="Representação conceitual da API do Microsoft Graph para o Teams." border="false":::

   :::column-end:::
   :::column span="":::

:::row:::
   :::column span="2":::
   :::column-end:::
:::row-end:::

## <a name="build-solutions-for-microsoft-teams-apps"></a><span data-ttu-id="aafb7-133">Criar soluções para aplicativos do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="aafb7-133">Build solutions for Microsoft Teams apps</span></span>
 
<span data-ttu-id="aafb7-134">A Microsoft oferece um livro de aparência extensibilidade, uma biblioteca de cenários para aplicativos do Teams organizados pelo setor.</span><span class="sxs-lookup"><span data-stu-id="aafb7-134">Microsoft offers an extensibility look book, a scenario library for Teams apps organized by industry.</span></span> <span data-ttu-id="aafb7-135">Este livro ajuda você a criar aplicativos na plataforma teams e a entender diferentes cenários possíveis usando vários recursos de plataforma do Teams.</span><span class="sxs-lookup"><span data-stu-id="aafb7-135">This book helps you build apps on the Teams platform and understand different possible scenarios using various Teams platform capabilities.</span></span> <span data-ttu-id="aafb7-136">Os cenários do look book começam com um problema de negócios, as personas envolvidas com seus desafios e terminam com uma solução de aplicativo do Teams que aborda as necessidades comerciais.</span><span class="sxs-lookup"><span data-stu-id="aafb7-136">The look book scenarios start with a business problem, the personas involved along with their challenges, and end with a Teams app solution addressing the business needs.</span></span>

<span data-ttu-id="aafb7-137">Cada cenário nesta biblioteca é acompanhado por um conjunto de simulações de conceito de design de alta fidelidade, que podem servir de inspiração para projetar seus aplicativos e melhorar a experiência do usuário.</span><span class="sxs-lookup"><span data-stu-id="aafb7-137">Each scenario in this library is accompanied by a set of high-fidelity design concept mocks, which can serve as an inspiration for designing your apps and enhancing user experience.</span></span> <span data-ttu-id="aafb7-138">Além disso, o look book destaca as práticas recomendadas de design e arquitetura seguidas na criação de cada aplicativo.</span><span class="sxs-lookup"><span data-stu-id="aafb7-138">In addition, the look book highlights the design and architecture best practices followed in building each app.</span></span> <span data-ttu-id="aafb7-139">Para obter mais informações, consulte o livro de aparência extensibilidade.</span><span class="sxs-lookup"><span data-stu-id="aafb7-139">For more information, see the extensibility look book.</span></span> <span data-ttu-id="aafb7-140">Para obter mais informações, consulte [extensibility look book](https://adoption.microsoft.com/extensibility-look-book/scenarios/).</span><span class="sxs-lookup"><span data-stu-id="aafb7-140">For more information, see [extensibility look book](https://adoption.microsoft.com/extensibility-look-book/scenarios/).</span></span> 

## <a name="start-building"></a><span data-ttu-id="aafb7-141">Iniciar a criação</span><span class="sxs-lookup"><span data-stu-id="aafb7-141">Start building</span></span>

<span data-ttu-id="aafb7-142">Familiarize-se rapidamente com a criação do Teams criando um aplicativo simples e adicionando alguns recursos comumente usados.</span><span class="sxs-lookup"><span data-stu-id="aafb7-142">Quickly familiarize yourself with building for Teams by creating a simple app and adding some commonly used capabilities.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="aafb7-143">Crie seu primeiro aplicativo agora</span><span class="sxs-lookup"><span data-stu-id="aafb7-143">Build your first app now</span></span>](build-your-first-app/build-first-app-overview.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="integrate-with-teams"></a><span data-ttu-id="aafb7-144">Integrar com o Teams</span><span class="sxs-lookup"><span data-stu-id="aafb7-144">Integrate with Teams</span></span>

<span data-ttu-id="aafb7-145">Mesclar os recursos que os usuários adoram sobre um aplicativo Web, serviço ou sistema existente com os recursos colaborativos do Teams.</span><span class="sxs-lookup"><span data-stu-id="aafb7-145">Blend the features users love about an existing web app, service, or system with the collaborative features of Teams.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="aafb7-146">Integrar um aplicativo existente</span><span class="sxs-lookup"><span data-stu-id="aafb7-146">Integrate an existing app</span></span>](samples/integrating-web-apps.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="a-little-code-goes-a-long-way"></a><span data-ttu-id="aafb7-147">Um pouco de código é muito longo</span><span class="sxs-lookup"><span data-stu-id="aafb7-147">A little code goes a long way</span></span>

<span data-ttu-id="aafb7-148">Você não precisa ser um programador especializado para criar um ótimo aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="aafb7-148">You don't need to be an expert programmer to build a great Teams app.</span></span> <span data-ttu-id="aafb7-149">Experimente uma das várias soluções de código baixo.</span><span class="sxs-lookup"><span data-stu-id="aafb7-149">Try one of several low-code solutions.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="aafb7-150">Criar um aplicativo de código baixo</span><span class="sxs-lookup"><span data-stu-id="aafb7-150">Create a low-code app</span></span>](samples/teams-low-code-solutions.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

## <a name="resources"></a><span data-ttu-id="aafb7-151">Recursos</span><span class="sxs-lookup"><span data-stu-id="aafb7-151">Resources</span></span>

* [<span data-ttu-id="aafb7-152">Adicionar um botão Compartilhar para o Teams ao seu site</span><span class="sxs-lookup"><span data-stu-id="aafb7-152">Add a Share-to-Teams button to your website</span></span>](concepts/build-and-test/share-to-teams.md)
* [<span data-ttu-id="aafb7-153">Projetar seu aplicativo do Teams</span><span class="sxs-lookup"><span data-stu-id="aafb7-153">Design your Teams app</span></span>](concepts/design/design-teams-app-overview.md)
* [<span data-ttu-id="aafb7-154">SDK do cliente JavaScript do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="aafb7-154">Microsoft Teams JavaScript client SDK</span></span>](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* <span data-ttu-id="aafb7-155">SDK da Estrutura de Bots para [JavaScript](https://github.com/Microsoft/botbuilder-js) e [.NET](https://github.com/Microsoft/botbuilder-dotnet/)</span><span class="sxs-lookup"><span data-stu-id="aafb7-155">Bot Framework SDK for [JavaScript](https://github.com/Microsoft/botbuilder-js) and [.NET](https://github.com/Microsoft/botbuilder-dotnet/)</span></span>
* [<span data-ttu-id="aafb7-156">Publicar seu aplicativo do Teams</span><span class="sxs-lookup"><span data-stu-id="aafb7-156">Publish your Teams app</span></span>](concepts/deploy-and-publish/overview.md)
