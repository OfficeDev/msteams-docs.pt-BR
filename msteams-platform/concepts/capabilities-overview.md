---
title: Noções básicas sobre os recursos do aplicativo teams
author: heath-hamilton
description: Recursos de aplicativo do Teams explicados
ms.topic: conceptual
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: 5336b36b52cf81be414f18ccaaf9e235c079e626
ms.sourcegitcommit: 49d1ecda14042bf3f368b14c1971618fe979b914
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51034702"
---
# <a name="understanding-teams-app-capabilities"></a><span data-ttu-id="675e3-103">Noções básicas sobre os recursos do aplicativo teams</span><span class="sxs-lookup"><span data-stu-id="675e3-103">Understanding Teams app capabilities</span></span>

<span data-ttu-id="675e3-104">*Os* recursos são os pontos de extensão para a criação de aplicativos na plataforma do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="675e3-104">*Capabilities* are the extension points for building apps on the Microsoft Teams platform.</span></span>

<span data-ttu-id="675e3-105">Há várias maneiras de estender o Teams, portanto, cada aplicativo é exclusivo: Alguns têm apenas um recurso (como um webhook), enquanto outras têm algumas para dar opções aos usuários.</span><span class="sxs-lookup"><span data-stu-id="675e3-105">There are multiple ways to extend Teams, so every app is unique: Some only have one capability (such as a webhook), while others have a few to give users options.</span></span> <span data-ttu-id="675e3-106">Por exemplo, seu aplicativo pode exibir dados em um local central (guia) e apresentar essas mesmas informações por meio de uma interface de conversa (bot).</span><span class="sxs-lookup"><span data-stu-id="675e3-106">For instance, your app could display data in a central location (tab) and present that same information through a conversational interface (bot).</span></span>

<span data-ttu-id="675e3-107">Seu aplicativo do Teams tem um ou todos os seguintes recursos principais:</span><span class="sxs-lookup"><span data-stu-id="675e3-107">Your Teams app have one or all of the following core capabilities:</span></span>

* [<span data-ttu-id="675e3-108">Guias</span><span class="sxs-lookup"><span data-stu-id="675e3-108">Tabs</span></span>](../tabs/what-are-tabs.md)
* [<span data-ttu-id="675e3-109">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="675e3-109">Messaging extensions</span></span>](../messaging-extensions/what-are-messaging-extensions.md)
* [<span data-ttu-id="675e3-110">Bots</span><span class="sxs-lookup"><span data-stu-id="675e3-110">Bots</span></span>](../bots/what-are-bots.md)
* [<span data-ttu-id="675e3-111">Webhooks e conectores</span><span class="sxs-lookup"><span data-stu-id="675e3-111">Webhooks and connectors</span></span>](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)

<span data-ttu-id="675e3-112">Seu aplicativo também pode tirar proveito dos recursos avançados, como a [API do Microsoft Graph para o Teams.](https://docs.microsoft.com/graph/teams-concept-overview)</span><span class="sxs-lookup"><span data-stu-id="675e3-112">Your app can also take advantage of advanced capabilities, such as the [Microsoft Graph API for Teams](https://docs.microsoft.com/graph/teams-concept-overview).</span></span>

<span data-ttu-id="675e3-113">Confira a ilustração a seguir para obter uma ideia de quais recursos forneceriam os recursos que você deseja em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="675e3-113">See the following illustration to get an idea which capabilities would provide the features you want in your app.</span></span>

:::image type="content" source="../assets/images/capabilities-overview.png" alt-text="Mapeie ilustrando quais são os recursos do aplicativo do Teams.":::

## <a name="doing-whats-best-for-your-users"></a><span data-ttu-id="675e3-115">Fazendo o que é melhor para seus usuários</span><span class="sxs-lookup"><span data-stu-id="675e3-115">Doing what's best for your users</span></span>

<span data-ttu-id="675e3-116">Ao se familiarizar com o desenvolvimento de aplicativos do Teams, você começará a entender suas sutilezas.</span><span class="sxs-lookup"><span data-stu-id="675e3-116">As you familiarize yourself with Teams app development, you'll begin to understand its subtleties.</span></span> <span data-ttu-id="675e3-117">Há mais de uma maneira de criar determinados recursos (como coletar entrada do usuário).</span><span class="sxs-lookup"><span data-stu-id="675e3-117">There's more than one way to build certain features (such as collecting user input).</span></span> <span data-ttu-id="675e3-118">Por exemplo, você pode inserir um formulário baseado na Web em uma guia usando um `<iframe>` .</span><span class="sxs-lookup"><span data-stu-id="675e3-118">For example, you could embed a web-based form in a tab using an `<iframe>`.</span></span> <span data-ttu-id="675e3-119">Você também pode fazer isso em uma guia usando um módulo de tarefa, uma convenção de interface do usuário do Teams, para uma experiência mais nativa que seus usuários podem preferir.</span><span class="sxs-lookup"><span data-stu-id="675e3-119">You could also do this in a tab using a task module, a Teams UI convention, for a more native experience your users may prefer.</span></span>

<span data-ttu-id="675e3-120">Escolher os recursos e o design certos se resume a entender primeiro os casos de uso [do seu público.](../concepts/design/understand-use-cases.md)</span><span class="sxs-lookup"><span data-stu-id="675e3-120">Choosing the right capabilities and design comes down to first [understanding your audience's use cases](../concepts/design/understand-use-cases.md).</span></span>
