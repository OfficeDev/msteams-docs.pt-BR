---
title: Criar aplicativos para a plataforma do Microsoft Teams
author: heath-hamilton
description: Visão geral de como os desenvolvedores podem estender e personalizar os recursos do Microsoft Teams com aplicativos personalizados.
ms.topic: overview
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: c430add71e7c23a44a552270c5e3c1bacbe650e4
ms.sourcegitcommit: 1aa0b172931d0f81db346452788c41dc4a6717b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48209785"
---
# <a name="build-apps-for-microsoft-teams"></a><span data-ttu-id="50cac-103">Criar aplicativos para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="50cac-103">Build apps for Microsoft Teams</span></span>

<span data-ttu-id="50cac-104">Os aplicativos do Microsoft Teams trazem informações importantes, ferramentas comuns e processos confiáveis para o local em que as pessoas coletam, aprendem e funcionam cada vez.</span><span class="sxs-lookup"><span data-stu-id="50cac-104">Microsoft Teams apps bring key information, common tools, and trusted processes to where people increasingly gather, learn, and work.</span></span>

<span data-ttu-id="50cac-105">Os aplicativos são como estender o Microsoft Teams para atender às suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="50cac-105">Apps are how you extend Teams to fit your needs.</span></span> <span data-ttu-id="50cac-106">Crie uma marca de algo novo para o Microsoft Teams ou integre um aplicativo existente.</span><span class="sxs-lookup"><span data-stu-id="50cac-106">Create something brand new for Teams or integrate an existing app.</span></span>

## <a name="what-are-teams-apps"></a><span data-ttu-id="50cac-107">O que são aplicativos do teams?</span><span class="sxs-lookup"><span data-stu-id="50cac-107">What are Teams apps?</span></span>

<span data-ttu-id="50cac-108">Os aplicativos do teams são uma combinação de [recursos](concepts/capabilities-overview.md) e [pontos de entrada](concepts/extensibility-points.md).</span><span class="sxs-lookup"><span data-stu-id="50cac-108">Teams apps are a combination of [capabilities](concepts/capabilities-overview.md) and [entry points](concepts/extensibility-points.md).</span></span> <span data-ttu-id="50cac-109">Por exemplo, as pessoas podem bater papo com o *bot* do seu aplicativo (recurso) em um *canal* (ponto de entrada).</span><span class="sxs-lookup"><span data-stu-id="50cac-109">For example, people can chat with your app's *bot* (capability) in a *channel* (entry point).</span></span>

<span data-ttu-id="50cac-110">Alguns aplicativos são simples (notificações de envio), enquanto outros são complexos (gerenciar registros de pacientes).</span><span class="sxs-lookup"><span data-stu-id="50cac-110">Some apps are simple (send notifications), while others are complex (manage patient records).</span></span> <span data-ttu-id="50cac-111">Ao planejar seu aplicativo, lembre-se de que o Microsoft Teams é um hub de colaboração.</span><span class="sxs-lookup"><span data-stu-id="50cac-111">When planning your app, remember that Teams is a collaboration hub.</span></span> <span data-ttu-id="50cac-112">Os melhores aplicativos do teams ajudam as pessoas a se expressarem e trabalhem melhor juntos.</span><span class="sxs-lookup"><span data-stu-id="50cac-112">The best Teams apps help people express themselves and work better together.</span></span>

:::row:::
   :::column span="":::

### <a name="tabs"></a><span data-ttu-id="50cac-113">Guias</span><span class="sxs-lookup"><span data-stu-id="50cac-113">Tabs</span></span>

<span data-ttu-id="50cac-114">**Obter informações de forma mais conveniente**: às vezes você só precisa fazer coisas mais fáceis de encontrar.</span><span class="sxs-lookup"><span data-stu-id="50cac-114">**Get information more conveniently**: Sometimes you just need to make things easier to find.</span></span> <span data-ttu-id="50cac-115">Exibir uma página da Web importante em uma [guia](tabs/what-are-tabs.md), que oferece uma experiência de tela inteira para conteúdo estático e dinâmico no Teams.</span><span class="sxs-lookup"><span data-stu-id="50cac-115">Display an important webpage in a [tab](tabs/what-are-tabs.md), which provides a full-screen web experience for static and dynamic content in Teams.</span></span>

:::image type="content" source="assets/images/overview-tabs.png" alt-text="Representação conceitual da aparência das guias no cliente do teams." border="false":::

   :::column-end:::
   :::column span="":::

### <a name="messaging-extensions"></a><span data-ttu-id="50cac-117">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="50cac-117">Messaging extensions</span></span>

<span data-ttu-id="50cac-118">Facilitar **a multitarefas**: com [extensões de mensagens](messaging-extensions/what-are-messaging-extensions.md), você pode compartilhar rapidamente informações externas em uma conversa.</span><span class="sxs-lookup"><span data-stu-id="50cac-118">**Make it easier to multitask**: With [messaging extensions](messaging-extensions/what-are-messaging-extensions.md), you can quickly share external information in a conversation.</span></span> <span data-ttu-id="50cac-119">Você também pode agir em uma mensagem, como criar um tíquete de ajuda com base no conteúdo de uma postagem de canal.</span><span class="sxs-lookup"><span data-stu-id="50cac-119">You also can act on a message, such as creating a help ticket based on the content of a channel post.</span></span>

:::image type="content" source="assets\images\overview-messaging.png" alt-text="Representação conceitual da aparência das extensões de mensagens no cliente do teams." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="bots"></a><span data-ttu-id="50cac-121">Bots</span><span class="sxs-lookup"><span data-stu-id="50cac-121">Bots</span></span>

<span data-ttu-id="50cac-122">**Transforme as palavras em ações**: as conversas freqüentemente resultam na necessidade de fazer algo (gerar um pedido, analisar meu código, verificar o status do tíquete, etc.).</span><span class="sxs-lookup"><span data-stu-id="50cac-122">**Turn words into actions**: Conversations often result in the need to do something (generate an order, review my code, check ticket status, etc.).</span></span> <span data-ttu-id="50cac-123">Um [bot](bots/what-are-bots.md) pode disparar esses tipos de fluxos de trabalho no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="50cac-123">A [bot](bots/what-are-bots.md) can kick off these kinds of workflows right inside Teams.</span></span>

:::image type="content" source="assets/images/overview-bots.png" alt-text="Representação conceitual da aparência dos bots no cliente do teams." border="false":::

   :::column-end:::
   :::column span="":::

### <a name="webhooks"></a><span data-ttu-id="50cac-125">Webhooks</span><span class="sxs-lookup"><span data-stu-id="50cac-125">Webhooks</span></span>

<span data-ttu-id="50cac-126">**Comunicar-se com aplicativos externos**: os [WebHooks de entrada](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) são uma maneira simples de enviar notificações automaticamente de outro aplicativo para um canal do teams.</span><span class="sxs-lookup"><span data-stu-id="50cac-126">**Communicate with external apps**: [Incoming webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) are a simple way to automatically send notifications from another app to a Teams channel.</span></span> <span data-ttu-id="50cac-127">Com os [WebHooks de saída](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks), Message Your Web Service com um @mention.</span><span class="sxs-lookup"><span data-stu-id="50cac-127">With [outgoing webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks), message your web service with an @mention.</span></span>

:::image type="content" source="assets/images/overview-connectors.png" alt-text="Representação conceitual da aparência dos conectores no cliente do teams." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="microsoft-graph-for-teams"></a><span data-ttu-id="50cac-129">Microsoft Graph para Teams</span><span class="sxs-lookup"><span data-stu-id="50cac-129">Microsoft Graph for Teams</span></span>

<span data-ttu-id="50cac-130">**Use os dados do teams**: a [API do Microsoft Graph para Teams](https://docs.microsoft.com/graph/teams-concept-overview) fornece acesso a informações sobre equipes, canais, usuários e mensagens que podem ajudá-lo a criar ou aprimorar recursos para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="50cac-130">**Utilize Teams data**: The [Microsoft Graph API for Teams](https://docs.microsoft.com/graph/teams-concept-overview) provides access to information about teams, channels, users, and messages that can help you create or enhance features for your app.</span></span>

:::image type="content" source="assets/images/overview-graph.png" alt-text="Representação conceitual da API do Microsoft Graph para Teams." border="false":::

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

## <a name="get-started"></a><span data-ttu-id="50cac-132">Introdução</span><span class="sxs-lookup"><span data-stu-id="50cac-132">Get started</span></span>

<span data-ttu-id="50cac-133">Vá em com nossos tutoriais de primeiro aplicativo ou descubra como integrar e importar aplicativos existentes.</span><span class="sxs-lookup"><span data-stu-id="50cac-133">Jump right in with our first app tutorials or find out how to integrate and import existing apps.</span></span>

:::row:::
   :::column span="2":::

### <a name="start-building"></a><span data-ttu-id="50cac-134">Começar a criar</span><span class="sxs-lookup"><span data-stu-id="50cac-134">Start building</span></span>

   <span data-ttu-id="50cac-135">Familiarize-se rapidamente com a compilação para o Microsoft Teams criando um aplicativo simples e adicionando alguns recursos usados com frequência.</span><span class="sxs-lookup"><span data-stu-id="50cac-135">Quickly familiarize yourself with building for Teams by creating a simple app and adding some commonly used capabilities.</span></span>

   > [!div class="nextstepaction"]
   > [<span data-ttu-id="50cac-136">Criar seu primeiro aplicativo agora</span><span class="sxs-lookup"><span data-stu-id="50cac-136">Build your first app now</span></span>](build-your-first-app/build-first-app-overview.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

### <a name="integrate-with-teams"></a><span data-ttu-id="50cac-137">Integração com o Teams</span><span class="sxs-lookup"><span data-stu-id="50cac-137">Integrate with Teams</span></span>

   <span data-ttu-id="50cac-138">Misturar os recursos que os usuários adoram em um aplicativo Web, serviço ou sistema existente com os recursos de colaboração do teams.</span><span class="sxs-lookup"><span data-stu-id="50cac-138">Blend the features users love about an existing web app, service, or system with the collaborative features of Teams.</span></span>

   > [!div class="nextstepaction"]
   > [<span data-ttu-id="50cac-139">Integrar um aplicativo existente</span><span class="sxs-lookup"><span data-stu-id="50cac-139">Integrate an existing app</span></span>](samples/integrating-web-apps.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

### <a name="a-little-code-goes-a-long-way"></a><span data-ttu-id="50cac-140">Um pouco de código é muito longo</span><span class="sxs-lookup"><span data-stu-id="50cac-140">A little code goes a long way</span></span>

   <span data-ttu-id="50cac-141">Você não precisa ser um programador especialista para criar um grande aplicativo do teams.</span><span class="sxs-lookup"><span data-stu-id="50cac-141">You don't need to be an expert programmer to build a great Teams app.</span></span> <span data-ttu-id="50cac-142">Tente uma das várias soluções de código baixo.</span><span class="sxs-lookup"><span data-stu-id="50cac-142">Try one of several low-code solutions.</span></span>

   > [!div class="nextstepaction"]
   > [<span data-ttu-id="50cac-143">Criar um aplicativo de código baixo</span><span class="sxs-lookup"><span data-stu-id="50cac-143">Create a low-code app</span></span>](samples/teams-low-code-solutions.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="resources"></a><span data-ttu-id="50cac-144">Recursos</span><span class="sxs-lookup"><span data-stu-id="50cac-144">Resources</span></span>

* [<span data-ttu-id="50cac-145">Adicionar um botão compartilhar ao Teams ao seu site</span><span class="sxs-lookup"><span data-stu-id="50cac-145">Add a Share to Teams button to your website</span></span>](concepts/build-and-test/share-to-teams.md)
* [<span data-ttu-id="50cac-146">Sistema de design fluente</span><span class="sxs-lookup"><span data-stu-id="50cac-146">Fluent Design System</span></span>](https://fluentsite.z22.web.core.windows.net/)
* [<span data-ttu-id="50cac-147">SDK do cliente JavaScript do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="50cac-147">Microsoft Teams JavaScript client SDK</span></span>](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* <span data-ttu-id="50cac-148">[SDK da estrutura de bot para JavaScript](https://github.com/Microsoft/botbuilder-js) e [SDK da estrutura de bot para .net](https://github.com/Microsoft/botbuilder-dotnet/)</span><span class="sxs-lookup"><span data-stu-id="50cac-148">[Bot Framework SDK for JavaScript](https://github.com/Microsoft/botbuilder-js) and [Bot Framework SDK for .NET](https://github.com/Microsoft/botbuilder-dotnet/)</span></span>
* [<span data-ttu-id="50cac-149">Publicar seu aplicativo em uma organização ou AppSource</span><span class="sxs-lookup"><span data-stu-id="50cac-149">Publish your app to an organization or AppSource</span></span>](concepts/deploy-and-publish/overview.md)
