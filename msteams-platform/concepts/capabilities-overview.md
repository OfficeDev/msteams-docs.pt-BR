---
title: Noções básicas sobre recursos de aplicativos do teams
author: heath-hamilton
description: Recursos do teams app explicados
ms.topic: conceptual
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: e7a6fe61fa5c74547ce20cc895afdd044f35e512
ms.sourcegitcommit: 1aa0b172931d0f81db346452788c41dc4a6717b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48210097"
---
# <a name="understanding-teams-app-capabilities"></a><span data-ttu-id="2fb3e-103">Noções básicas sobre recursos de aplicativos do teams</span><span class="sxs-lookup"><span data-stu-id="2fb3e-103">Understanding Teams app capabilities</span></span>

<span data-ttu-id="2fb3e-104">Os *recursos* são os pontos de extensão para a criação de aplicativos na plataforma do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="2fb3e-104">*Capabilities* are the extension points for building apps on the Microsoft Teams platform.</span></span>

<span data-ttu-id="2fb3e-105">Há várias maneiras de estender o Microsoft Teams, portanto, todos os aplicativos são exclusivos: alguns têm apenas um recurso (como um webhook), enquanto outros têm alguns para fornecer opções aos usuários.</span><span class="sxs-lookup"><span data-stu-id="2fb3e-105">There are multiple ways to extend Teams, so every app is unique: Some only have one capability (such as a webhook), while others have a few to give users options.</span></span> <span data-ttu-id="2fb3e-106">Por exemplo, seu aplicativo pode exibir dados em um local central (Tab) e apresentar as mesmas informações por meio de uma interface de conversação (bot).</span><span class="sxs-lookup"><span data-stu-id="2fb3e-106">For instance, your app could display data in a central location (tab) and present that same information through a conversational interface (bot).</span></span>

<span data-ttu-id="2fb3e-107">O aplicativo do Microsoft Teams pode ter um ou todos os seguintes recursos principais:</span><span class="sxs-lookup"><span data-stu-id="2fb3e-107">Your Teams app can have one or all of the following core capabilities:</span></span>

* [<span data-ttu-id="2fb3e-108">Guias</span><span class="sxs-lookup"><span data-stu-id="2fb3e-108">Tabs</span></span>](../tabs/what-are-tabs.md)
* [<span data-ttu-id="2fb3e-109">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="2fb3e-109">Messaging extensions</span></span>](../messaging-extensions/what-are-messaging-extensions.md)
* [<span data-ttu-id="2fb3e-110">Bots</span><span class="sxs-lookup"><span data-stu-id="2fb3e-110">Bots</span></span>](../bots/what-are-bots.md)
* [<span data-ttu-id="2fb3e-111">Webhooks e conectores</span><span class="sxs-lookup"><span data-stu-id="2fb3e-111">Webhooks and connectors</span></span>](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)

<span data-ttu-id="2fb3e-112">O aplicativo também pode aproveitar as vantagens de recursos avançados, como a [API do Microsoft Graph para Teams](https://docs.microsoft.com/graph/teams-concept-overview).</span><span class="sxs-lookup"><span data-stu-id="2fb3e-112">Your app can also can take advantage of advanced capabilities, such as the [Microsoft Graph API for Teams](https://docs.microsoft.com/graph/teams-concept-overview).</span></span>

<span data-ttu-id="2fb3e-113">Veja a ilustração a seguir para ter uma ideia de quais recursos fornecerão os recursos que você deseja em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2fb3e-113">See the following illustration to get an idea which capabilities would provide the features you want in your app.</span></span>

:::image type="content" source="../assets/images/capabilities-overview.png" alt-text="Mapa mental que ilustra o que são os recursos do teams app.":::

## <a name="doing-whats-best-for-your-users"></a><span data-ttu-id="2fb3e-115">Como fazer o melhor para os seus usuários</span><span class="sxs-lookup"><span data-stu-id="2fb3e-115">Doing what's best for your users</span></span>

<span data-ttu-id="2fb3e-116">À medida que você se familiarizar com o desenvolvimento de aplicativos do Teams, começará a entender seus sutilezas.</span><span class="sxs-lookup"><span data-stu-id="2fb3e-116">As you familiarize yourself with Teams app development, you'll begin to understand its subtleties.</span></span> <span data-ttu-id="2fb3e-117">Há mais de uma maneira de Compilar determinados recursos (como coletar entradas do usuário).</span><span class="sxs-lookup"><span data-stu-id="2fb3e-117">There's more than one way to build certain features (such as collecting user input).</span></span> <span data-ttu-id="2fb3e-118">Por exemplo, você pode inserir um formulário baseado na Web em uma guia usando um `<iframe>` .</span><span class="sxs-lookup"><span data-stu-id="2fb3e-118">For example, you could embed a web-based form in a tab using an `<iframe>`.</span></span> <span data-ttu-id="2fb3e-119">Você também pode fazer isso em uma guia usando um módulo de tarefa, uma Convenção de interface do usuário do Microsoft Teams, para uma experiência mais nativa que os usuários possam preferir.</span><span class="sxs-lookup"><span data-stu-id="2fb3e-119">You could also do this in a tab using a task module, a Teams UI convention, for a more native experience your users may prefer.</span></span>

<span data-ttu-id="2fb3e-120">A escolha dos recursos e design certos é para baixo na [compreensão inicial dos casos de uso do público](../concepts/design/understand-use-cases.md).</span><span class="sxs-lookup"><span data-stu-id="2fb3e-120">Choosing the right capabilities and design comes down to first [understanding your audience's use cases](../concepts/design/understand-use-cases.md).</span></span>
