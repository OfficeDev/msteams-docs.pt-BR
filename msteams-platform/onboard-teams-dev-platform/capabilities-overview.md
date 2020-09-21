---
title: Noções básicas sobre recursos de aplicativos do teams
author: heath-hamilton
description: Visão geral dos recursos de plataforma do Teams, que são os pontos de extensão para a criação de aplicativos do teams.
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: 9bb94d2cfd5c30b2245c5ccf580d374972315e72
ms.sourcegitcommit: d3bb4bbcdff9545c9869647dcdbe563a2db868be
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2020
ms.locfileid: "47964561"
---
# <a name="understanding-teams-app-capabilities"></a><span data-ttu-id="45cea-103">Noções básicas sobre recursos de aplicativos do teams</span><span class="sxs-lookup"><span data-stu-id="45cea-103">Understanding Teams app capabilities</span></span>

<span data-ttu-id="45cea-104">Os *recursos* são os pontos de extensão para a criação de aplicativos na plataforma do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="45cea-104">*Capabilities* are the extension points for building apps on the Microsoft Teams platform.</span></span>

<span data-ttu-id="45cea-105">Há várias maneiras de estender o cliente do Microsoft Teams, portanto, todos os aplicativos são exclusivos: alguns têm apenas um recurso (como um webhook), enquanto outros têm alguns para fornecer opções aos usuários.</span><span class="sxs-lookup"><span data-stu-id="45cea-105">There are multiple ways to extend the Teams client, so every app is unique: Some only have one capability (such as a webhook), while others have a few to give users options.</span></span> <span data-ttu-id="45cea-106">Por exemplo, seu aplicativo pode exibir dados em um local central (Tab) e apresentar as mesmas informações por meio de uma interface de conversação (bot).</span><span class="sxs-lookup"><span data-stu-id="45cea-106">For instance, your app could display data in a central location (tab) and present that same information through a conversational interface (bot).</span></span>

<span data-ttu-id="45cea-107">O aplicativo do Microsoft Teams pode ter um ou todos os seguintes recursos principais:</span><span class="sxs-lookup"><span data-stu-id="45cea-107">Your Teams app can have one or all of the following core capabilities:</span></span>

* [<span data-ttu-id="45cea-108">Guias</span><span class="sxs-lookup"><span data-stu-id="45cea-108">Tabs</span></span>](../tabs/what-are-tabs.md)
* [<span data-ttu-id="45cea-109">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="45cea-109">Messaging extensions</span></span>](../messaging-extensions/what-are-messaging-extensions.md)
* [<span data-ttu-id="45cea-110">Webhooks e conectores</span><span class="sxs-lookup"><span data-stu-id="45cea-110">Webhooks and connectors</span></span>](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)
* [<span data-ttu-id="45cea-111">Bots</span><span class="sxs-lookup"><span data-stu-id="45cea-111">Bots</span></span>](../bots/what-are-bots.md)

<span data-ttu-id="45cea-112">O aplicativo também pode aproveitar as vantagens de recursos avançados, como a [API REST do Microsoft Graph](../graph-api/rsc/resource-specific-consent.md).</span><span class="sxs-lookup"><span data-stu-id="45cea-112">Your app can also can take advantage of advanced capabilities, such as the [Microsoft Graph REST API](../graph-api/rsc/resource-specific-consent.md).</span></span>

<span data-ttu-id="45cea-113">Veja a ilustração a seguir para ter uma ideia de quais recursos fornecerão os recursos que você deseja em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="45cea-113">See the following illustration to get an idea which capabilities would provide the features you want in your app.</span></span>

![Mapa mental que ilustra o que são os recursos do teams app](doc-links/images/capabilities-overview.png)

## <a name="doing-whats-best-for-your-users"></a><span data-ttu-id="45cea-115">Como fazer o melhor para os seus usuários</span><span class="sxs-lookup"><span data-stu-id="45cea-115">Doing what's best for your users</span></span>

<span data-ttu-id="45cea-116">À medida que você se familiarizar com o desenvolvimento de aplicativos do Teams, começará a entender seus sutilezas.</span><span class="sxs-lookup"><span data-stu-id="45cea-116">As you familiarize yourself with Teams app development, you'll begin to understand its subtleties.</span></span> <span data-ttu-id="45cea-117">Há mais de uma maneira de Compilar determinados recursos (como coletar entradas do usuário).</span><span class="sxs-lookup"><span data-stu-id="45cea-117">There's more than one way to build certain features (such as collecting user input).</span></span> <span data-ttu-id="45cea-118">Por exemplo, você pode inserir um formulário baseado na Web em uma guia usando um `<iframe>` .</span><span class="sxs-lookup"><span data-stu-id="45cea-118">For example, you could embed a web-based form in a tab using an `<iframe>`.</span></span> <span data-ttu-id="45cea-119">Você também pode fazer isso em uma guia usando um módulo de tarefa, uma Convenção de interface do usuário do Microsoft Teams, para uma experiência mais nativa que os usuários possam preferir.</span><span class="sxs-lookup"><span data-stu-id="45cea-119">You could also do this in a tab using a task module, a Teams UI convention, for a more native experience your users may prefer.</span></span>

<span data-ttu-id="45cea-120">Escolher a combinação certa de recursos e convenções, controles e elementos da interface do usuário é a primeira [compreensão dos casos de uso do público](../concepts/design/understand-use-cases.md).</span><span class="sxs-lookup"><span data-stu-id="45cea-120">Choosing the right combination of capabilities and UI conventions, controls, and elements comes down to first [understanding your audience's use cases](../concepts/design/understand-use-cases.md).</span></span>

## <a name="learn-more"></a><span data-ttu-id="45cea-121">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="45cea-121">Learn more</span></span>

* [<span data-ttu-id="45cea-122">Iniciar o planejamento do aplicativo</span><span class="sxs-lookup"><span data-stu-id="45cea-122">Start planning your app</span></span>](../concepts/extensibility-points.md)
