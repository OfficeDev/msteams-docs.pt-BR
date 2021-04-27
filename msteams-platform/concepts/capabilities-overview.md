---
title: Compreender os recursos do aplicativo
author: heath-hamilton
description: Recursos de aplicativo do Teams explicados
ms.topic: conceptual
localization_priority: Normal
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: d1c6916c9433b15ddcd13e9128b25170dd990dd4
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019927"
---
# <a name="understand-microsoft-teams-app-capabilities"></a><span data-ttu-id="77b19-103">Entender os recursos do aplicativo do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="77b19-103">Understand Microsoft Teams app capabilities</span></span>

<span data-ttu-id="77b19-104">Extensibilidade ou pontos de entrada são maneiras diferentes nas quais um aplicativo pode se manifesto para um usuário.</span><span class="sxs-lookup"><span data-stu-id="77b19-104">Extensibility or entry points are different ways in which an app can manifest itself to a user.</span></span> <span data-ttu-id="77b19-105">Por exemplo, um usuário pode interagir com um aplicativo em uma guia de tela para fazer uma atividade ou pode optar por fazer o mesmo usando um bot de conversa.</span><span class="sxs-lookup"><span data-stu-id="77b19-105">For example, a user can interact with an app on a canvas tab to do an activity or might choose to do the same using a conversational bot.</span></span> <span data-ttu-id="77b19-106">Os vários recursos usados para criar seu aplicativo do Teams permitem que você aumente seu escopo de uso.</span><span class="sxs-lookup"><span data-stu-id="77b19-106">The various capabilities used to build your Teams app allow you to increase its usage scope.</span></span>

<span data-ttu-id="77b19-107">Há várias maneiras de estender o Teams, portanto, cada aplicativo é exclusivo.</span><span class="sxs-lookup"><span data-stu-id="77b19-107">There are multiple ways to extend Teams, so every app is unique.</span></span> <span data-ttu-id="77b19-108">Alguns têm apenas um recurso, como um webhook, enquanto outros têm mais de um recurso para dar aos usuários várias opções.</span><span class="sxs-lookup"><span data-stu-id="77b19-108">Some only have one capability, such as a webhook, while others have more than one feature to give users various options.</span></span> <span data-ttu-id="77b19-109">Por exemplo, seu aplicativo pode exibir dados em  um local central, ou seja, a guia e apresentar essas mesmas informações por meio de uma interface de conversa, ou seja, o **bot**.</span><span class="sxs-lookup"><span data-stu-id="77b19-109">For example, your app can display data in a central location, that is, the **tab** and present that same information through a conversational interface, that is, the **bot**.</span></span>

## <a name="app-capabilities"></a><span data-ttu-id="77b19-110">Recursos do aplicativo</span><span class="sxs-lookup"><span data-stu-id="77b19-110">App capabilities</span></span>

<span data-ttu-id="77b19-111">Seu aplicativo do Teams tem um ou todos os seguintes recursos principais:</span><span class="sxs-lookup"><span data-stu-id="77b19-111">Your Teams app have one or all of the following core capabilities:</span></span>

* [<span data-ttu-id="77b19-112">Guias</span><span class="sxs-lookup"><span data-stu-id="77b19-112">Tabs</span></span>](../tabs/what-are-tabs.md)
* [<span data-ttu-id="77b19-113">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="77b19-113">Messaging extensions</span></span>](../messaging-extensions/what-are-messaging-extensions.md)
* [<span data-ttu-id="77b19-114">Bots</span><span class="sxs-lookup"><span data-stu-id="77b19-114">Bots</span></span>](../bots/what-are-bots.md)
* [<span data-ttu-id="77b19-115">Webhooks e conectores</span><span class="sxs-lookup"><span data-stu-id="77b19-115">Webhooks and connectors</span></span>](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)

<span data-ttu-id="77b19-116">Seu aplicativo também pode tirar proveito dos recursos avançados, como a [API do Microsoft Graph para o Teams.](https://docs.microsoft.com/graph/teams-concept-overview)</span><span class="sxs-lookup"><span data-stu-id="77b19-116">Your app can also take advantage of advanced capabilities, such as the [Microsoft Graph API for Teams](https://docs.microsoft.com/graph/teams-concept-overview).</span></span>

<span data-ttu-id="77b19-117">A ilustração a seguir fornece uma ideia de quais recursos fornecerão os recursos que você deseja em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="77b19-117">The following illustration gives you an idea of which capabilities will provide the features you want in your app.</span></span>

:::image type="content" source="../assets/images/capabilities-overview.png" alt-text="Mapeie ilustrando quais são os recursos do aplicativo do Teams.":::

## <a name="always-consider-your-user"></a><span data-ttu-id="77b19-119">Sempre considere seu usuário</span><span class="sxs-lookup"><span data-stu-id="77b19-119">Always consider your user</span></span>

<span data-ttu-id="77b19-120">À medida que você se familiariza com o desenvolvimento de aplicativos do Teams, você compreende seus principais fundamentos.</span><span class="sxs-lookup"><span data-stu-id="77b19-120">As you familiarize yourself with Teams app development, you understand its core fundamentals.</span></span> <span data-ttu-id="77b19-121">Você entende que há mais de uma maneira de criar determinados recursos.</span><span class="sxs-lookup"><span data-stu-id="77b19-121">You understand that there is more than one way to build certain features.</span></span> <span data-ttu-id="77b19-122">Nesses cenários, considere como você pode fornecer uma experiência mais nativa ao usuário.</span><span class="sxs-lookup"><span data-stu-id="77b19-122">In such scenarios, consider how you can provide a more native experience to your user.</span></span>
<span data-ttu-id="77b19-123">Por exemplo, você pode coletar a entrada do usuário em um formulário criado como uma guia no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="77b19-123">For example, you can collect user input in a form built as a tab in the app.</span></span> <span data-ttu-id="77b19-124">Você também pode fazer isso usando um módulo de tarefa sem alternar exibições e interromper o fluxo de trabalho do usuário.</span><span class="sxs-lookup"><span data-stu-id="77b19-124">You can also do this using a task module without switching views and disrupting user's flow of work.</span></span> <span data-ttu-id="77b19-125">É importante escolher pontos de extensão que forneçam menor desvio do fluxo regular de trabalho de um usuário.</span><span class="sxs-lookup"><span data-stu-id="77b19-125">It is important to choose extension points that provide least deviation from a user's regular flow of work.</span></span>

## <a name="see-also"></a><span data-ttu-id="77b19-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="77b19-126">See also</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="77b19-127">Criar aplicativos para o Teams</span><span class="sxs-lookup"><span data-stu-id="77b19-127">Build apps for Teams</span></span>](../overview.md)
## <a name="next-step"></a><span data-ttu-id="77b19-128">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="77b19-128">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="77b19-129">Pontos de entrada do aplicativo Teams</span><span class="sxs-lookup"><span data-stu-id="77b19-129">Teams app entry points</span></span>](../concepts/extensibility-points.md)
