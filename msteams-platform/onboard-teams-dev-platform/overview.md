---
title: Plataforma de desenvolvedor do teams
author: clearab
description: Visão geral de como os desenvolvedores podem estender e personalizar os recursos do Microsoft Teams usando a plataforma do teams.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 4af4d34ffa4581be6e69f6233d3eb356aa6a2a08
ms.sourcegitcommit: 52732714105fac07c331cd31e370a9685f45d3e1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "46874881"
---
# <a name="building-for-microsoft-teams"></a><span data-ttu-id="b0ae0-103">Criando o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="b0ae0-103">Building for Microsoft Teams</span></span>

<span data-ttu-id="b0ae0-104">Os aplicativos do Microsoft Teams trazem informações importantes, ferramentas comuns e processos confiáveis para o local em que as pessoas coletam, aprendem e funcionam cada vez.</span><span class="sxs-lookup"><span data-stu-id="b0ae0-104">Microsoft Teams apps bring key information, common tools, and trusted processes to where people increasingly gather, learn, and work.</span></span>

<span data-ttu-id="b0ae0-105">Os aplicativos são como estender o Microsoft Teams para atender às suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="b0ae0-105">Apps are how you extend Teams to fit your needs.</span></span> <span data-ttu-id="b0ae0-106">Você pode criar algo novo para o Microsoft Teams ou simplesmente integrar recursos em seus aplicativos e serviços favoritos.</span><span class="sxs-lookup"><span data-stu-id="b0ae0-106">You can create something brand new for Teams or simply integrate features in your favorite apps and services.</span></span>

## <a name="what-can-teams-apps-do"></a><span data-ttu-id="b0ae0-107">O que os aplicativos do teams podem fazer?</span><span class="sxs-lookup"><span data-stu-id="b0ae0-107">What can Teams apps do?</span></span>

<span data-ttu-id="b0ae0-108">As pessoas descobrem e usam aplicativos do teams por meio de um conjunto de [recursos](capabilities-overview.md)de plataforma.</span><span class="sxs-lookup"><span data-stu-id="b0ae0-108">People discover and use Teams apps through a set of platform [capabilities](capabilities-overview.md).</span></span>

<span data-ttu-id="b0ae0-109">Alguns aplicativos são simples (notificações de envio), enquanto outros são complexos (exibir registros de pacientes).</span><span class="sxs-lookup"><span data-stu-id="b0ae0-109">Some apps are simple (send notifications), while others are complex (view patient records).</span></span> <span data-ttu-id="b0ae0-110">Ao planejar seu aplicativo, lembre-se de que o Microsoft Teams é um hub de colaboração.</span><span class="sxs-lookup"><span data-stu-id="b0ae0-110">When planning your app, remember that Teams is a collaboration hub.</span></span> <span data-ttu-id="b0ae0-111">Os melhores aplicativos do teams ajudam as pessoas a se expressarem e trabalhem melhor juntos.</span><span class="sxs-lookup"><span data-stu-id="b0ae0-111">The best Teams apps help people express themselves and work better together.</span></span>

### <a name="get-information-more-conveniently"></a><span data-ttu-id="b0ae0-112">Obter informações de forma mais conveniente</span><span class="sxs-lookup"><span data-stu-id="b0ae0-112">Get information more conveniently</span></span>

<span data-ttu-id="b0ae0-113">Às vezes, você só precisa tornar tudo mais fácil de encontrar.</span><span class="sxs-lookup"><span data-stu-id="b0ae0-113">Sometimes you just need to make things easier to find.</span></span> <span data-ttu-id="b0ae0-114">Exibir uma página da Web importante em uma [guia](doc-links/what-are-tabs.md), que oferece uma experiência de tela inteira para conteúdo estático e dinâmico no Teams.</span><span class="sxs-lookup"><span data-stu-id="b0ae0-114">Display an important webpage in a [tab](doc-links/what-are-tabs.md), which provides a full-screen web experience for static and dynamic content in Teams.</span></span>

![Representação conceitual da aparência das guias no cliente do teams.](doc-links/images/overview-tabs.png)

### <a name="share-links-without-switching-context"></a><span data-ttu-id="b0ae0-116">Compartilhar links sem alternar contexto</span><span class="sxs-lookup"><span data-stu-id="b0ae0-116">Share links without switching context</span></span>

<span data-ttu-id="b0ae0-117">Receba informações em uma conversa e nunca deixe o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="b0ae0-117">Pull information into a conversation and never leave Teams.</span></span> <span data-ttu-id="b0ae0-118">Por exemplo, com [extensões de mensagens](doc-links/what-are-messaging-extensions.md) você pode compartilhar conteúdo rico e facilmente digestible de um sistema externo usando a caixa de composição de mensagem.</span><span class="sxs-lookup"><span data-stu-id="b0ae0-118">For example, with [messaging extensions](doc-links/what-are-messaging-extensions.md) you can share rich, easily digestible content from an external system using the message compose box.</span></span>

![Representação conceitual da aparência das extensões de mensagens no cliente do teams](doc-links\images\overview-messaging.png)

### <a name="turn-words-into-actions"></a><span data-ttu-id="b0ae0-120">Transformar palavras em ações</span><span class="sxs-lookup"><span data-stu-id="b0ae0-120">Turn words into actions</span></span>

<span data-ttu-id="b0ae0-121">As conversas geralmente resultam na necessidade de algo (criar um pedido, examinar meu código, etc.).</span><span class="sxs-lookup"><span data-stu-id="b0ae0-121">Conversations often result in the need to do something (create an order, review my code, etc.).</span></span> <span data-ttu-id="b0ae0-122">Um [bot](doc-links/what-are-bots.md) pode disparar esses tipos de fluxos de trabalho no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="b0ae0-122">A [bot](doc-links/what-are-bots.md) can kick off these kinds of workflows right inside Teams.</span></span>

![Representação conceitual da aparência dos bots no cliente do teams](doc-links/images/overview-bots.png)

### <a name="communicate-with-external-apps-and-services"></a><span data-ttu-id="b0ae0-124">Comunicar-se com aplicativos e serviços externos</span><span class="sxs-lookup"><span data-stu-id="b0ae0-124">Communicate with external apps and services</span></span>

<span data-ttu-id="b0ae0-125">Os [WebHooks de entrada](doc-links/what-are-webhooks-and-connectors.md#incoming-webhooks) são uma maneira simples de enviar alertas automaticamente de outro aplicativo para um canal ou chat do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="b0ae0-125">[Incoming webhooks](doc-links/what-are-webhooks-and-connectors.md#incoming-webhooks) are a simple way to automatically send alerts from another app to a Teams channel or chat.</span></span> <span data-ttu-id="b0ae0-126">Com os [WebHooks de saída](doc-links/what-are-webhooks-and-connectors.md#outgoing-webhooks), você pode enviar uma mensagem ao seu serviço Web com um @mention.</span><span class="sxs-lookup"><span data-stu-id="b0ae0-126">With [outgoing webhooks](doc-links/what-are-webhooks-and-connectors.md#outgoing-webhooks), you can send a message to your web service with an @mention.</span></span>

![Representação conceitual da aparência dos conectores no cliente do teams.](doc-links/images/overview-connectors.png)

### <a name="utilize-teams-data"></a><span data-ttu-id="b0ae0-128">Usar dados do teams</span><span class="sxs-lookup"><span data-stu-id="b0ae0-128">Utilize Teams data</span></span>

<span data-ttu-id="b0ae0-129">A [API REST do Microsoft Graph para Teams](https://docs.microsoft.com/graph/teams-concept-overview) fornece acesso a informações sobre equipes, canais, usuários e mensagens que podem ajudá-lo a criar ou aprimorar recursos para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b0ae0-129">The [Microsoft Graph REST API for Teams](https://docs.microsoft.com/graph/teams-concept-overview) provides access to information about teams, channels, users, and messages that can help you create or enhance features for your app.</span></span>

!["Representação conceitual da API REST do Microsoft Graph para Teams](doc-links/images/overview-graph.png)
  
## <a name="start-building"></a><span data-ttu-id="b0ae0-131">Começar a criar</span><span class="sxs-lookup"><span data-stu-id="b0ae0-131">Start building</span></span>

   <span data-ttu-id="b0ae0-132">Familiarize-se rapidamente com a compilação para o Microsoft Teams criando um aplicativo simples e adicionando alguns recursos usados com frequência.</span><span class="sxs-lookup"><span data-stu-id="b0ae0-132">Quickly familiarize yourself with building for Teams by creating a simple app and adding a couple commonly used capabilities.</span></span>

   > [!div class="nextstepaction"]
   > [<span data-ttu-id="b0ae0-133">Criar seu primeiro aplicativo agora</span><span class="sxs-lookup"><span data-stu-id="b0ae0-133">Build your first app now</span></span>](build-your-first-app/build-real-world-app.md)

### <a name="bring-it-all-together"></a><span data-ttu-id="b0ae0-134">Reunir tudo</span><span class="sxs-lookup"><span data-stu-id="b0ae0-134">Bring it all together</span></span>

   <span data-ttu-id="b0ae0-135">Simplifique os processos e fluxos de trabalho para os usuários, combinando os aplicativos Web favoritos da sua organização, serviços e sistemas com recursos colaborativos do teams.</span><span class="sxs-lookup"><span data-stu-id="b0ae0-135">Simplify processes and workflows for users by blending your organization's favorite web apps, services, and systems with Teams collaborative features.</span></span>

   > [!div class="nextstepaction"]
   > [<span data-ttu-id="b0ae0-136">Integrar um aplicativo existente</span><span class="sxs-lookup"><span data-stu-id="b0ae0-136">Integrate an existing app</span></span>](doc-links/integrating-web-apps.md)

### <a name="trust-the-process"></a><span data-ttu-id="b0ae0-137">Confiar no processo</span><span class="sxs-lookup"><span data-stu-id="b0ae0-137">Trust the process</span></span>

   <span data-ttu-id="b0ae0-138">Entenda todo o processo de desenvolvimento da plataforma do teams para planejar, projetar, criar e publicar um aplicativo para sua organização ou qualquer pessoa com eficácia.</span><span class="sxs-lookup"><span data-stu-id="b0ae0-138">Understand the entire Teams platform development process to effectively plan, design, build, and publish an app for your organization or anyone.</span></span>

   > [!div class="nextstepaction"]
   > [<span data-ttu-id="b0ae0-139">Iniciar o planejamento do aplicativo</span><span class="sxs-lookup"><span data-stu-id="b0ae0-139">Start planning your app</span></span>](doc-links/extensibility-points.md)

### <a name="no-code-no-worries"></a><span data-ttu-id="b0ae0-140">Nenhum código, sem preocupação</span><span class="sxs-lookup"><span data-stu-id="b0ae0-140">No code, no worries</span></span>

   <span data-ttu-id="b0ae0-141">Você não precisa ser um programador para compilar um ótimo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b0ae0-141">You don't need to be a programmer to build a great app.</span></span> <span data-ttu-id="b0ae0-142">Criar um aplicativo do teams com pouco ou nenhum código usando a plataforma de alimentação da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b0ae0-142">Create a Teams app with little to no code using the Microsoft Power Platform.</span></span>

   > [!div class="nextstepaction"]
   > [<span data-ttu-id="b0ae0-143">Importar um aplicativo de plataforma de energia</span><span class="sxs-lookup"><span data-stu-id="b0ae0-143">Import a Power Platform app</span></span>](doc-links/importing-custom-microsoft-apps.md)

## <a name="resources"></a><span data-ttu-id="b0ae0-144">Recursos</span><span class="sxs-lookup"><span data-stu-id="b0ae0-144">Resources</span></span>

* [<span data-ttu-id="b0ae0-145">Adicionar um botão compartilhar ao Teams ao seu site</span><span class="sxs-lookup"><span data-stu-id="b0ae0-145">Add a Share to Teams button to your website</span></span>](doc-links/share-to-teams.md)
* [<span data-ttu-id="b0ae0-146">Sistema de design de interface do usuário fluente</span><span class="sxs-lookup"><span data-stu-id="b0ae0-146">Fluent UI Design System</span></span>](https://fluentsite.z22.web.core.windows.net/)
* [<span data-ttu-id="b0ae0-147">SDK do cliente JavaScript do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="b0ae0-147">Microsoft Teams JavaScript client SDK</span></span>](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest)
* <span data-ttu-id="b0ae0-148">[SDK da estrutura de bot para JavaScript](https://github.com/Microsoft/botbuilder-js) e [SDK da estrutura de bot para .net](https://github.com/Microsoft/botbuilder-dotnet/)</span><span class="sxs-lookup"><span data-stu-id="b0ae0-148">[Bot Framework SDK for JavaScript](https://github.com/Microsoft/botbuilder-js) and [Bot Framework SDK for .NET](https://github.com/Microsoft/botbuilder-dotnet/)</span></span>
