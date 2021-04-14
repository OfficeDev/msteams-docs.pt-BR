---
title: Pontos de entrada para os aplicativos do Teams
author: heath-hamilton
description: Descreve onde as pessoas podem descobrir e usar seu aplicativo no Teams.
ms.topic: conceptual
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: 72ce2620160f854bbe458821db01e91d2d9f62cd
ms.sourcegitcommit: 098d38dd947e87e69d289b99e807bea2d95c42f9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/18/2020
ms.locfileid: "49713624"
---
# <a name="entry-points-for-teams-apps"></a><span data-ttu-id="84125-103">Pontos de entrada para os aplicativos do Teams</span><span class="sxs-lookup"><span data-stu-id="84125-103">Entry points for Teams apps</span></span>

<span data-ttu-id="84125-104">A plataforma Teams fornece um conjunto flexível de pontos de entrada onde as pessoas podem descobrir e usar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="84125-104">The Teams platform provides a flexible set of entry points where people can discover and use your app.</span></span> <span data-ttu-id="84125-105">Seu aplicativo pode ser tão simples quanto incorporar conteúdo existente da Web em uma guia ou um aplicativo com várias facetas com o qual os usuários interagem em vários contextos.</span><span class="sxs-lookup"><span data-stu-id="84125-105">Your app can be as simple as embedding existing web content in a tab or a multi-faceted app that users interact with across several contexts.</span></span>

<span data-ttu-id="84125-106">Os aplicativos mais bem-sucedidos parecem nativos do Teams, por isso é importante planejar cuidadosamente os pontos de entrada do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="84125-106">The most successful apps feel native to Teams, so it's important to carefully plan your app's entry points.</span></span>

## <a name="teams-channels-and-chats"></a><span data-ttu-id="84125-107">Equipes, canais e chats</span><span class="sxs-lookup"><span data-stu-id="84125-107">Teams, channels, and chats</span></span>

<span data-ttu-id="84125-108">Equipes, canais e chats são espaços de colaboração.</span><span class="sxs-lookup"><span data-stu-id="84125-108">Teams, channels, and chats are collaboration spaces.</span></span> <span data-ttu-id="84125-109">Os aplicativos nesses contextos estão disponíveis para todos nesse espaço e normalmente se concentram em fluxos de trabalho adicionais ou desbloqueiam novas interações sociais.</span><span class="sxs-lookup"><span data-stu-id="84125-109">Apps in these contexts are available to everyone in that space and typically focus on additional workflows or unlocking new social interactions.</span></span>

<span data-ttu-id="84125-110">Veja como os recursos do aplicativo Teams são comumente usados em contextos colaborativos:</span><span class="sxs-lookup"><span data-stu-id="84125-110">Here's how Teams app capabilities are commonly used in collaborative contexts:</span></span>

* <span data-ttu-id="84125-111">As [**Guias**](~/tabs/what-are-tabs.md) oferecem uma experiência da Web inserida em tela inteira configurada para a equipe, o canal ou o chat em grupo.</span><span class="sxs-lookup"><span data-stu-id="84125-111">[**Tabs**](~/tabs/what-are-tabs.md) provide a full-screen embedded web experience configured for the team, channel, or group chat.</span></span> <span data-ttu-id="84125-112">Todos os membros interagem com o mesmo conteúdo baseado na Web, portanto, uma experiência de aplicativo de página única, sem estado, é típica.</span><span class="sxs-lookup"><span data-stu-id="84125-112">All members interact with the same web-based content, so a stateless single page app experience is typical.</span></span>

* <span data-ttu-id="84125-113">As [**extensões e mensagens**](~/messaging-extensions/what-are-messaging-extensions.md) são atalhos para inserir conteúdo externo em uma conversa ou fazer ações em mensagens sem sair do Teams.</span><span class="sxs-lookup"><span data-stu-id="84125-113">[**Messaging extensions**](~/messaging-extensions/what-are-messaging-extensions.md) are shortcuts for inserting external content into a conversation or taking action on messages without leaving Teams.</span></span> <span data-ttu-id="84125-114">A divisão de links fornece conteúdo completo ao compartilhar conteúdo de uma URL comum.</span><span class="sxs-lookup"><span data-stu-id="84125-114">Link unfurling provides rich content when sharing content from a common URL.</span></span>

* <span data-ttu-id="84125-115">Os [**bots**](~/bots/what-are-bots.md) interagem com os membros da conversa por chat e respondem a eventos (como adicionar um novo membro ou renomear um canal).</span><span class="sxs-lookup"><span data-stu-id="84125-115">[**Bots**](~/bots/what-are-bots.md) interact with members of the conversation through chat and responding to events (like adding a new member or renaming a channel).</span></span> <span data-ttu-id="84125-116">As conversas com um bot nesses contextos são visíveis para todos os membros da equipe, canal ou grupo, portanto as conversas do bot devem ser relevantes para todos.</span><span class="sxs-lookup"><span data-stu-id="84125-116">Conversations with a bot in these contexts are visible to all members of the team, channel, or group, so bot conversations should be relevant to everyone.</span></span>

* <span data-ttu-id="84125-117">Os [**webhooks e conectores**](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) permitem que um serviço externo poste mensagens em uma conversa e os usuários enviem mensagens para um serviço.</span><span class="sxs-lookup"><span data-stu-id="84125-117">[**Webhooks and connectors**](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) allow an external service to post messages into a conversation and users to send messages to a service.</span></span>

* <span data-ttu-id="84125-118">A [**API REST do Microsoft Graph**](https://docs.microsoft.com/graph/teams-concept-overview) para obter dados sobre equipes, canais e chats em grupo para ajudar a automatizar e gerenciar processos do Teams.</span><span class="sxs-lookup"><span data-stu-id="84125-118">[**Microsoft Graph REST API**](https://docs.microsoft.com/graph/teams-concept-overview) for getting data about teams, channels, and group chats to help automate and manage Teams processes.</span></span>

## <a name="personal-apps"></a><span data-ttu-id="84125-119">Aplicativos pessoais</span><span class="sxs-lookup"><span data-stu-id="84125-119">Personal apps</span></span>

<span data-ttu-id="84125-120">Os [aplicativos pessoais](~/concepts/design/personal-apps.md) se concentram nas interações com um único usuário.</span><span class="sxs-lookup"><span data-stu-id="84125-120">[Personal apps](~/concepts/design/personal-apps.md) focus on interactions with a single user.</span></span> <span data-ttu-id="84125-121">A experiência nesse contexto é exclusiva para cada usuário.</span><span class="sxs-lookup"><span data-stu-id="84125-121">The experience in this context is unique to each user.</span></span>

<span data-ttu-id="84125-122">Veja como os recursos do Teams são normalmente usados em contextos pessoais:</span><span class="sxs-lookup"><span data-stu-id="84125-122">Here's how Teams capabilities are commonly used in personal contexts:</span></span>

* <span data-ttu-id="84125-123">Os [**bots**](~/bots/what-are-bots.md) mantém conversas individuais com um usuário.</span><span class="sxs-lookup"><span data-stu-id="84125-123">[**Bots**](~/bots/what-are-bots.md) have one-on-one conversations with a user.</span></span> <span data-ttu-id="84125-124">Bots que exigem conversas de vários turnos ou fornecem notificações relevantes apenas para um usuário específico são mais adequados em aplicativos pessoais.</span><span class="sxs-lookup"><span data-stu-id="84125-124">Bots that require multi-turn conversations or provide notifications relevant only to a specific user are best suited in personal apps.</span></span>

* <span data-ttu-id="84125-125">As [**guias**](~/tabs/what-are-tabs.md) oferecem uma experiência da Web inserida em tela inteira que é significativa para o usuário que a está vendo.</span><span class="sxs-lookup"><span data-stu-id="84125-125">[**Tabs**](~/tabs/what-are-tabs.md) provide a full-screen embedded web experience that's meaningful to the user looking at it.</span></span>

## <a name="examples"></a><span data-ttu-id="84125-126">Exemplos</span><span class="sxs-lookup"><span data-stu-id="84125-126">Examples</span></span>

<span data-ttu-id="84125-127">As diretrizes de design do Aplicativo Teams fornecem elementos visuais detalhados que mostram onde as pessoas podem encontrar e usar os aplicativos do Teams.</span><span class="sxs-lookup"><span data-stu-id="84125-127">The Teams app design guidelines provide detailed visuals showing you where people can find and use Teams apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="84125-128">Veja as diretrizes de design do Aplicativo Teams</span><span class="sxs-lookup"><span data-stu-id="84125-128">See the Teams app design guidelines</span></span>](../concepts/design/design-teams-app-overview.md)
