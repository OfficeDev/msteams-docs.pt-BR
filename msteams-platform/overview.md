---
title: Criar aplicativos para a plataforma do Microsoft Teams
author: heath-hamilton
description: Obter uma visão geral de como os desenvolvedores podem estender os recursos do Microsoft Teams com aplicativos personalizados.
ms.topic: overview
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: 45be2dd7d0e421ac331cfc02703f0b81eab3dfe5
ms.sourcegitcommit: 4539479289b43812eaae07a1c0f878bed815d2d2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/12/2021
ms.locfileid: "49797768"
---
# <a name="build-apps-for-microsoft-teams"></a><span data-ttu-id="828c8-103">Crie aplicativos para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="828c8-103">Build apps for Microsoft Teams</span></span>

<span data-ttu-id="828c8-104">Os aplicativos do Microsoft Teams trazem informações importantes, ferramentas comuns e processos confiáveis para onde as pessoas se reúnem, aprendem e trabalham cada vez mais.</span><span class="sxs-lookup"><span data-stu-id="828c8-104">Microsoft Teams apps bring key information, common tools, and trusted processes to where people increasingly gather, learn, and work.</span></span>

<span data-ttu-id="828c8-105">Os aplicativos são como você estende o Teams para se ajustar às suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="828c8-105">Apps are how you extend Teams to fit your needs.</span></span> <span data-ttu-id="828c8-106">Crie algo novo para o Teams ou integre um aplicativo existente.</span><span class="sxs-lookup"><span data-stu-id="828c8-106">Create something brand new for Teams or integrate an existing app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="828c8-107">Iniciar aqui</span><span class="sxs-lookup"><span data-stu-id="828c8-107">Start here</span></span>](build-your-first-app/build-first-app-overview.md)

## <a name="what-are-teams-apps"></a><span data-ttu-id="828c8-108">O que são aplicativos do Teams?</span><span class="sxs-lookup"><span data-stu-id="828c8-108">What are Teams apps?</span></span>

<span data-ttu-id="828c8-109">Os aplicativos do Teams são uma combinação [de recursos](concepts/capabilities-overview.md) e pontos [de entrada.](concepts/extensibility-points.md)</span><span class="sxs-lookup"><span data-stu-id="828c8-109">Teams apps are a combination of [capabilities](concepts/capabilities-overview.md) and [entry points](concepts/extensibility-points.md).</span></span> <span data-ttu-id="828c8-110">Por exemplo, as pessoas podem conversar com o *bot* (recurso) do seu aplicativo em um *canal* (ponto de entrada).</span><span class="sxs-lookup"><span data-stu-id="828c8-110">For example, people can chat with your app's *bot* (capability) in a *channel* (entry point).</span></span>

<span data-ttu-id="828c8-111">Alguns aplicativos são simples (enviar notificações), enquanto outros são complexos (gerenciar registros de pacientes).</span><span class="sxs-lookup"><span data-stu-id="828c8-111">Some apps are simple (send notifications), while others are complex (manage patient records).</span></span> <span data-ttu-id="828c8-112">Ao planejar seu aplicativo, lembre-se de que o Teams é um hub de colaboração.</span><span class="sxs-lookup"><span data-stu-id="828c8-112">When planning your app, remember that Teams is a collaboration hub.</span></span> <span data-ttu-id="828c8-113">Os melhores aplicativos do Teams ajudam as pessoas a se expressarem e trabalharem melhor juntas.</span><span class="sxs-lookup"><span data-stu-id="828c8-113">The best Teams apps help people express themselves and work better together.</span></span>

:::row:::
   :::column span="":::

### <a name="tabs"></a><span data-ttu-id="828c8-114">Guias</span><span class="sxs-lookup"><span data-stu-id="828c8-114">Tabs</span></span>

<span data-ttu-id="828c8-115">**Obter informações de maneira mais conveniente:** às vezes, você só precisa facilitar a sua encontrar.</span><span class="sxs-lookup"><span data-stu-id="828c8-115">**Get information more conveniently**: Sometimes you just need to make things easier to find.</span></span> <span data-ttu-id="828c8-116">Exibir uma página da Web importante em uma [guia,](tabs/what-are-tabs.md)que fornece uma experiência de tela inteira para conteúdo estático e dinâmico no Teams.</span><span class="sxs-lookup"><span data-stu-id="828c8-116">Display an important webpage in a [tab](tabs/what-are-tabs.md), which provides a full-screen web experience for static and dynamic content in Teams.</span></span>

:::image type="content" source="assets/images/overview-tabs.png" alt-text="Representação conceitual da aparência das guias no cliente do Teams." border="false":::

   :::column-end:::

   :::column span="":::

### <a name="bots"></a><span data-ttu-id="828c8-118">Bots</span><span class="sxs-lookup"><span data-stu-id="828c8-118">Bots</span></span>

<span data-ttu-id="828c8-119">**Transforme palavras em ações:** as conversas geralmente resultam na necessidade de fazer algo (gerar uma ordem, revisar meu código, verificar o status do tíquete etc.).</span><span class="sxs-lookup"><span data-stu-id="828c8-119">**Turn words into actions**: Conversations often result in the need to do something (generate an order, review my code, check ticket status, etc.).</span></span> <span data-ttu-id="828c8-120">Um [bot](bots/what-are-bots.md) pode dar início a esses tipos de fluxos de trabalho dentro do Teams.</span><span class="sxs-lookup"><span data-stu-id="828c8-120">A [bot](bots/what-are-bots.md) can kick off these kinds of workflows right inside Teams.</span></span>

:::image type="content" source="assets/images/overview-bots.png" alt-text="Representação conceitual da aparência dos bots no cliente do Teams." border="false":::

   :::column-end:::

:::row-end:::

:::row:::

   :::column span="":::

### <a name="messaging-extensions"></a><span data-ttu-id="828c8-122">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="828c8-122">Messaging extensions</span></span>

<span data-ttu-id="828c8-123">**Facilitar a multitarefa:** com extensões de mensagens, você pode compartilhar rapidamente informações [externas](messaging-extensions/what-are-messaging-extensions.md)em uma conversa.</span><span class="sxs-lookup"><span data-stu-id="828c8-123">**Make it easier to multitask**: With [messaging extensions](messaging-extensions/what-are-messaging-extensions.md), you can quickly share external information in a conversation.</span></span> <span data-ttu-id="828c8-124">Você também pode agir em uma mensagem, como criar um tíquete de ajuda com base no conteúdo de uma postagem de canal.</span><span class="sxs-lookup"><span data-stu-id="828c8-124">You also can act on a message, such as creating a help ticket based on the content of a channel post.</span></span>

:::image type="content" source="assets\images\overview-messaging.png" alt-text="Representação conceitual da aparência das extensões de mensagens no cliente do Teams." border="false":::

   :::column-end:::

   :::column span="":::

### <a name="webhooks"></a><span data-ttu-id="828c8-126">Webhooks</span><span class="sxs-lookup"><span data-stu-id="828c8-126">Webhooks</span></span>

<span data-ttu-id="828c8-127">**Comunicar-se com aplicativos** [externos: os webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) de entrada são uma maneira simples de enviar automaticamente notificações de outro aplicativo para um canal do Teams.</span><span class="sxs-lookup"><span data-stu-id="828c8-127">**Communicate with external apps**: [Incoming webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) are a simple way to automatically send notifications from another app to a Teams channel.</span></span> <span data-ttu-id="828c8-128">Com [webhooks de saída,](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks)mensagem seu serviço Web com um @mention.</span><span class="sxs-lookup"><span data-stu-id="828c8-128">With [outgoing webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks), message your web service with an @mention.</span></span>

:::image type="content" source="assets/images/overview-connectors.png" alt-text="Representação conceitual da aparência dos conectores no cliente do Teams." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="microsoft-graph-for-teams"></a><span data-ttu-id="828c8-130">Microsoft Graph para Teams</span><span class="sxs-lookup"><span data-stu-id="828c8-130">Microsoft Graph for Teams</span></span>

<span data-ttu-id="828c8-131">**Utilize dados do Teams:** a API do [Microsoft Graph](https://docs.microsoft.com/graph/teams-concept-overview) para Teams fornece acesso a informações sobre equipes, canais, usuários e mensagens que podem ajudá-lo a criar ou aprimorar recursos para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="828c8-131">**Utilize Teams data**: The [Microsoft Graph API for Teams](https://docs.microsoft.com/graph/teams-concept-overview) provides access to information about teams, channels, users, and messages that can help you create or enhance features for your app.</span></span>

:::image type="content" source="assets/images/overview-graph.png" alt-text="Representação conceitual da API do Microsoft Graph para o Teams." border="false":::

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="start-building"></a><span data-ttu-id="828c8-133">Começar a construir</span><span class="sxs-lookup"><span data-stu-id="828c8-133">Start building</span></span>

   <span data-ttu-id="828c8-134">Familiarize-se rapidamente com a criação do Teams criando um aplicativo simples e adicionando alguns recursos comumente usados.</span><span class="sxs-lookup"><span data-stu-id="828c8-134">Quickly familiarize yourself with building for Teams by creating a simple app and adding some commonly used capabilities.</span></span>

   > [!div class="nextstepaction"]
   > [<span data-ttu-id="828c8-135">Crie seu primeiro aplicativo agora</span><span class="sxs-lookup"><span data-stu-id="828c8-135">Build your first app now</span></span>](build-your-first-app/build-first-app-overview.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="integrate-with-teams"></a><span data-ttu-id="828c8-136">Integração com o Teams</span><span class="sxs-lookup"><span data-stu-id="828c8-136">Integrate with Teams</span></span>

   <span data-ttu-id="828c8-137">Combinar os recursos que os usuários gostam de um aplicativo Web, serviço ou sistema existente com os recursos colaborativos do Teams.</span><span class="sxs-lookup"><span data-stu-id="828c8-137">Blend the features users love about an existing web app, service, or system with the collaborative features of Teams.</span></span>

   > [!div class="nextstepaction"]
   > [<span data-ttu-id="828c8-138">Integrar um aplicativo existente</span><span class="sxs-lookup"><span data-stu-id="828c8-138">Integrate an existing app</span></span>](samples/integrating-web-apps.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="a-little-code-goes-a-long-way"></a><span data-ttu-id="828c8-139">Um pouco de código faz um longo caminho</span><span class="sxs-lookup"><span data-stu-id="828c8-139">A little code goes a long way</span></span>

   <span data-ttu-id="828c8-140">Você não precisa ser um programador especializado para criar um ótimo aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="828c8-140">You don't need to be an expert programmer to build a great Teams app.</span></span> <span data-ttu-id="828c8-141">Experimente uma das várias soluções de código baixo.</span><span class="sxs-lookup"><span data-stu-id="828c8-141">Try one of several low-code solutions.</span></span>

   > [!div class="nextstepaction"]
   > [<span data-ttu-id="828c8-142">Criar um aplicativo de código baixo</span><span class="sxs-lookup"><span data-stu-id="828c8-142">Create a low-code app</span></span>](samples/teams-low-code-solutions.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

## <a name="resources"></a><span data-ttu-id="828c8-143">Recursos</span><span class="sxs-lookup"><span data-stu-id="828c8-143">Resources</span></span>

* [<span data-ttu-id="828c8-144">Adicionar um botão Compartilhar com o Teams ao seu site</span><span class="sxs-lookup"><span data-stu-id="828c8-144">Add a Share-to-Teams button to your website</span></span>](concepts/build-and-test/share-to-teams.md)
* <span data-ttu-id="828c8-145"><a href="https://fluentsite.z22.web.core.windows.net/" target="_blank">Interface do usuário do Fluent</a></span><span class="sxs-lookup"><span data-stu-id="828c8-145"><a href="https://fluentsite.z22.web.core.windows.net/" target="_blank">Fluent UI</a></span></span>
* [<span data-ttu-id="828c8-146">SDK do cliente JavaScript do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="828c8-146">Microsoft Teams JavaScript client SDK</span></span>](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* <span data-ttu-id="828c8-147">[SDK do Bot Framework para JavaScript](https://github.com/Microsoft/botbuilder-js) e [SDK da Estrutura de Bot para .NET](https://github.com/Microsoft/botbuilder-dotnet/)</span><span class="sxs-lookup"><span data-stu-id="828c8-147">[Bot Framework SDK for JavaScript](https://github.com/Microsoft/botbuilder-js) and [Bot Framework SDK for .NET](https://github.com/Microsoft/botbuilder-dotnet/)</span></span>
* [<span data-ttu-id="828c8-148">Publicar seu aplicativo em uma organização ou no AppSource</span><span class="sxs-lookup"><span data-stu-id="828c8-148">Publish your app to an organization or AppSource</span></span>](concepts/deploy-and-publish/overview.md)
