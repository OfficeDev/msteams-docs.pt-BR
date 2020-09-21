---
title: Plataforma de desenvolvedores do Microsoft Teams
author: clearab
description: Visão geral de como os desenvolvedores podem estender e personalizar os recursos do Microsoft Teams usando a plataforma do teams.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 73cbd4f68d8878872147bd412972495de1b5de6e
ms.sourcegitcommit: d3bb4bbcdff9545c9869647dcdbe563a2db868be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2020
ms.locfileid: "47964568"
---
# <a name="building-for-microsoft-teams"></a><span data-ttu-id="0569d-103">Criando o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="0569d-103">Building for Microsoft Teams</span></span>

<span data-ttu-id="0569d-104">Os aplicativos do Microsoft Teams trazem informações importantes, ferramentas comuns e processos confiáveis para o local em que as pessoas coletam, aprendem e funcionam cada vez.</span><span class="sxs-lookup"><span data-stu-id="0569d-104">Microsoft Teams apps bring key information, common tools, and trusted processes to where people increasingly gather, learn, and work.</span></span>

<span data-ttu-id="0569d-105">Os aplicativos são como estender o Microsoft Teams para atender às suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="0569d-105">Apps are how you extend Teams to fit your needs.</span></span> <span data-ttu-id="0569d-106">Crie uma marca de algo novo para o Microsoft Teams ou integre um aplicativo existente.</span><span class="sxs-lookup"><span data-stu-id="0569d-106">Create something brand new for Teams or integrate an existing app.</span></span>

## <a name="what-are-teams-apps"></a><span data-ttu-id="0569d-107">O que são aplicativos do teams?</span><span class="sxs-lookup"><span data-stu-id="0569d-107">What are Teams apps?</span></span>

<span data-ttu-id="0569d-108">As pessoas descobrem e usam aplicativos do teams por meio de um conjunto de [recursos](capabilities-overview.md)de plataforma.</span><span class="sxs-lookup"><span data-stu-id="0569d-108">People discover and use Teams apps through a set of platform [capabilities](capabilities-overview.md).</span></span>

<span data-ttu-id="0569d-109">Alguns aplicativos são simples (notificações de envio), enquanto outros são complexos (exibir registros de pacientes).</span><span class="sxs-lookup"><span data-stu-id="0569d-109">Some apps are simple (send notifications), while others are complex (view patient records).</span></span> <span data-ttu-id="0569d-110">Ao planejar seu aplicativo, lembre-se de que o Microsoft Teams é um hub de colaboração.</span><span class="sxs-lookup"><span data-stu-id="0569d-110">When planning your app, remember that Teams is a collaboration hub.</span></span> <span data-ttu-id="0569d-111">Os melhores aplicativos do teams ajudam as pessoas a se expressarem e trabalhem melhor juntos.</span><span class="sxs-lookup"><span data-stu-id="0569d-111">The best Teams apps help people express themselves and work better together.</span></span>

:::row:::
   :::column span="":::

### <a name="tabs"></a><span data-ttu-id="0569d-112">Guias</span><span class="sxs-lookup"><span data-stu-id="0569d-112">Tabs</span></span>

<span data-ttu-id="0569d-113">**Obter informações de forma mais conveniente**: às vezes você só precisa fazer coisas mais fáceis de encontrar.</span><span class="sxs-lookup"><span data-stu-id="0569d-113">**Get information more conveniently**: Sometimes you just need to make things easier to find.</span></span> <span data-ttu-id="0569d-114">Exibir uma página da Web importante em uma [guia](../tabs/what-are-tabs.md), que oferece uma experiência de tela inteira para conteúdo estático e dinâmico no Teams.</span><span class="sxs-lookup"><span data-stu-id="0569d-114">Display an important webpage in a [tab](../tabs/what-are-tabs.md), which provides a full-screen web experience for static and dynamic content in Teams.</span></span>

:::image type="content" source="doc-links/images/overview-tabs.png" alt-text="Representação conceitual da aparência das guias no cliente do teams." border="false":::

   :::column-end:::
   :::column span="":::

### <a name="messaging-extensions"></a><span data-ttu-id="0569d-116">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="0569d-116">Messaging extensions</span></span>

<span data-ttu-id="0569d-117">Facilitar **a multitarefas**: com [extensões de mensagens](../messaging-extensions/what-are-messaging-extensions.md), você pode compartilhar rapidamente informações externas em uma conversa.</span><span class="sxs-lookup"><span data-stu-id="0569d-117">**Make it easier to multitask**: With [messaging extensions](../messaging-extensions/what-are-messaging-extensions.md), you can quickly share external information in a conversation.</span></span> <span data-ttu-id="0569d-118">Você também pode agir em uma mensagem, como criar um tíquete de ajuda com base no conteúdo de uma postagem de canal.</span><span class="sxs-lookup"><span data-stu-id="0569d-118">You also can act on a message, such as creating a help ticket based on the content of a channel post.</span></span>

:::image type="content" source="doc-links/images/overview-messaging.png" alt-text="Representação conceitual da aparência das extensões de mensagens no cliente do teams." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="bots"></a><span data-ttu-id="0569d-120">Bots</span><span class="sxs-lookup"><span data-stu-id="0569d-120">Bots</span></span>

<span data-ttu-id="0569d-121">**Transforme as palavras em ações**: as conversas freqüentemente resultam na necessidade de fazer algo (gerar um pedido, analisar meu código, verificar o status do tíquete, etc.).</span><span class="sxs-lookup"><span data-stu-id="0569d-121">**Turn words into actions**: Conversations often result in the need to do something (generate an order, review my code, check ticket status, etc.).</span></span> <span data-ttu-id="0569d-122">Um [bot](../bots/what-are-bots.md) pode disparar esses tipos de fluxos de trabalho no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="0569d-122">A [bot](../bots/what-are-bots.md) can kick off these kinds of workflows right inside Teams.</span></span>

:::image type="content" source="doc-links/images/overview-bots.png" alt-text="Representação conceitual da aparência dos bots no cliente do teams." border="false":::

   :::column-end:::
   :::column span="":::

### <a name="webhooks"></a><span data-ttu-id="0569d-124">Webhooks</span><span class="sxs-lookup"><span data-stu-id="0569d-124">Webhooks</span></span>

<span data-ttu-id="0569d-125">**Comunicar-se com aplicativos externos**: os [WebHooks de entrada](../webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) são uma maneira simples de enviar notificações automaticamente de outro aplicativo para um canal do teams.</span><span class="sxs-lookup"><span data-stu-id="0569d-125">**Communicate with external apps**: [Incoming webhooks](../webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) are a simple way to automatically send notifications from another app to a Teams channel.</span></span> <span data-ttu-id="0569d-126">Com os [WebHooks de saída](../webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks), Message Your Web Service com um @mention.</span><span class="sxs-lookup"><span data-stu-id="0569d-126">With [outgoing webhooks](../webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks), message your web service with an @mention.</span></span>

:::image type="content" source="doc-links/images/overview-connectors.png" alt-text="Representação conceitual da aparência dos conectores no cliente do teams." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="microsoft-graph-for-teams"></a><span data-ttu-id="0569d-128">Microsoft Graph para Teams</span><span class="sxs-lookup"><span data-stu-id="0569d-128">Microsoft Graph for Teams</span></span>

<span data-ttu-id="0569d-129">**Use os dados do teams**: a [API REST do Microsoft Graph para Teams](https://docs.microsoft.com/graph/teams-concept-overview) fornece acesso a informações sobre equipes, canais, usuários e mensagens que podem ajudá-lo a criar ou aprimorar recursos para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0569d-129">**Utilize Teams data**: The [Microsoft Graph REST API for Teams](https://docs.microsoft.com/graph/teams-concept-overview) provides access to information about teams, channels, users, and messages that can help you create or enhance features for your app.</span></span>

:::image type="content" source="doc-links/images/overview-graph.png" alt-text="Representação conceitual da API REST do Microsoft Graph para o Teams." border="false":::

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

## <a name="get-started"></a><span data-ttu-id="0569d-131">Introdução</span><span class="sxs-lookup"><span data-stu-id="0569d-131">Get started</span></span>

<span data-ttu-id="0569d-132">Entre em nossos primeiros tutoriais de aplicativos, descubra como integrar e importar aplicativos existentes ou reserve um tempo para aprender sobre o ciclo de vida do desenvolvimento de aplicativos do teams.</span><span class="sxs-lookup"><span data-stu-id="0569d-132">Jump right in with our first app tutorials, find out how to integrate and import existing apps, or take your time to learn about the Teams app development lifecycle.</span></span>

:::row:::
   :::column span="2":::

### <a name="start-building"></a><span data-ttu-id="0569d-133">Começar a criar</span><span class="sxs-lookup"><span data-stu-id="0569d-133">Start building</span></span>

   <span data-ttu-id="0569d-134">Familiarize-se rapidamente com a compilação para o Microsoft Teams criando um aplicativo simples e adicionando alguns recursos usados com frequência.</span><span class="sxs-lookup"><span data-stu-id="0569d-134">Quickly familiarize yourself with building for Teams by creating a simple app and adding some commonly used capabilities.</span></span>

   > [!div class="nextstepaction"]
   > [<span data-ttu-id="0569d-135">Criar seu primeiro aplicativo agora</span><span class="sxs-lookup"><span data-stu-id="0569d-135">Build your first app now</span></span>](build-your-first-app/building-real-world-app.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

### <a name="integrate-with-teams"></a><span data-ttu-id="0569d-136">Integração com o Teams</span><span class="sxs-lookup"><span data-stu-id="0569d-136">Integrate with Teams</span></span>

   <span data-ttu-id="0569d-137">Misturar os recursos que os usuários adoram em um aplicativo Web, serviço ou sistema existente com os recursos de colaboração do teams.</span><span class="sxs-lookup"><span data-stu-id="0569d-137">Blend the features users love about an existing web app, service, or system with the collaborative features of Teams.</span></span>

   > [!div class="nextstepaction"]
   > [<span data-ttu-id="0569d-138">Integrar um aplicativo existente</span><span class="sxs-lookup"><span data-stu-id="0569d-138">Integrate an existing app</span></span>](migrating-web-apps.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

### <a name="a-little-code-goes-a-long-way"></a><span data-ttu-id="0569d-139">Um pouco de código é muito longo</span><span class="sxs-lookup"><span data-stu-id="0569d-139">A little code goes a long way</span></span>

   <span data-ttu-id="0569d-140">Você não precisa ser um programador especialista para criar um grande aplicativo do teams.</span><span class="sxs-lookup"><span data-stu-id="0569d-140">You don't need to be an expert programmer to build a great Teams app.</span></span> <span data-ttu-id="0569d-141">Tente uma das várias soluções de código baixo.</span><span class="sxs-lookup"><span data-stu-id="0569d-141">Try one of several low-code solutions.</span></span>

   > [!div class="nextstepaction"]
   > [<span data-ttu-id="0569d-142">Criar um aplicativo de código baixo</span><span class="sxs-lookup"><span data-stu-id="0569d-142">Create a low-code app</span></span>](low-code-solutions.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

### <a name="trust-the-process"></a><span data-ttu-id="0569d-143">Confiar no processo</span><span class="sxs-lookup"><span data-stu-id="0569d-143">Trust the process</span></span>

   <span data-ttu-id="0569d-144">Saiba todo o processo de desenvolvimento de plataforma do teams para planejar, projetar, criar e publicar um aplicativo para sua organização ou qualquer pessoa com eficácia.</span><span class="sxs-lookup"><span data-stu-id="0569d-144">Learn the entire Teams platform development process to effectively plan, design, build, and publish an app for your organization or anyone.</span></span>

   > [!div class="nextstepaction"]
   > [<span data-ttu-id="0569d-145">Iniciar o planejamento do aplicativo</span><span class="sxs-lookup"><span data-stu-id="0569d-145">Start planning your app</span></span>](../concepts/extensibility-points.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

## <a name="resources"></a><span data-ttu-id="0569d-146">Recursos</span><span class="sxs-lookup"><span data-stu-id="0569d-146">Resources</span></span>

* [<span data-ttu-id="0569d-147">Adicionar um botão compartilhar ao Teams ao seu site</span><span class="sxs-lookup"><span data-stu-id="0569d-147">Add a Share to Teams button to your website</span></span>](../concepts/build-and-test/share-to-teams.md)
* [<span data-ttu-id="0569d-148">Sistema de design fluente</span><span class="sxs-lookup"><span data-stu-id="0569d-148">Fluent Design System</span></span>](https://fluentsite.z22.web.core.windows.net/)
* [<span data-ttu-id="0569d-149">SDK do JavaScript do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="0569d-149">Microsoft Teams JavaScript SDK</span></span>](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* <span data-ttu-id="0569d-150">[SDK da estrutura de bot para JavaScript](https://github.com/Microsoft/botbuilder-js) e [SDK da estrutura de bot para .net](https://github.com/Microsoft/botbuilder-dotnet/)</span><span class="sxs-lookup"><span data-stu-id="0569d-150">[Bot Framework SDK for JavaScript](https://github.com/Microsoft/botbuilder-js) and [Bot Framework SDK for .NET](https://github.com/Microsoft/botbuilder-dotnet/)</span></span>
* [<span data-ttu-id="0569d-151">Publicar seu aplicativo em uma organização ou AppSource</span><span class="sxs-lookup"><span data-stu-id="0569d-151">Publish your app to an organization or AppSource</span></span>](../concepts/deploy-and-publish/overview.md)
