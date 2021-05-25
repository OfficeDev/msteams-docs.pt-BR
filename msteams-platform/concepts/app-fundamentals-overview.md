---
title: Visão geral dos fundamentos do desenvolvimento de aplicativos
author: heath-hamilton
description: Descreva os conceitos fundamentais do desenvolvimento Teams plataforma.
ms.topic: conceptual
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: 1ecae34c38950f16e49fc123f73bdc746c4b28cc
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2021
ms.locfileid: "52630152"
---
# <a name="microsoft-teams-app-development-fundamentals"></a><span data-ttu-id="60779-103">Microsoft Teams básicos de desenvolvimento de aplicativos</span><span class="sxs-lookup"><span data-stu-id="60779-103">Microsoft Teams app development fundamentals</span></span>

<span data-ttu-id="60779-104">Microsoft Teams básicos do aplicativo dão a direção que você precisa para criar seu aplicativo Teams personalizado.</span><span class="sxs-lookup"><span data-stu-id="60779-104">Microsoft Teams app fundamentals give the direction you need to create your custom Teams app.</span></span> <span data-ttu-id="60779-105">Você pode reconhecer a estrutura necessária para planejar seu Teams app.</span><span class="sxs-lookup"><span data-stu-id="60779-105">You can recognize the framework required to plan your Teams app.</span></span> <span data-ttu-id="60779-106">O documento ajuda você a entender a comunicação usuário-aplicativo e descobrir o tipo de superfícies de aplicativo que você precisa usar ou as APIs que seu aplicativo pode exigir no processo.</span><span class="sxs-lookup"><span data-stu-id="60779-106">The document helps you to understand the user-app communication and figure out the kind of app surfaces you need to use or the APIs your app might require in the process.</span></span> <span data-ttu-id="60779-107">Obter alguma inspiração para adotar a interatividade que pode aprofundar a experiência do aplicativo quando você se integra Teams.</span><span class="sxs-lookup"><span data-stu-id="60779-107">Get some inspiration to embrace interactivity that can deepen the app experience when you integrate with Teams.</span></span>

## <a name="capabilities-and-entry-points"></a><span data-ttu-id="60779-108">Recursos e pontos de entrada</span><span class="sxs-lookup"><span data-stu-id="60779-108">Capabilities and entry points</span></span>

<span data-ttu-id="60779-109">Você pode estender seu Teams de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="60779-109">You can extend your Teams app in multiple ways.</span></span> <span data-ttu-id="60779-110">Para poder estender seu aplicativo, você deve entender todos os principais recursos e os pontos de entrada que funcionam em um espaço colaborativo.</span><span class="sxs-lookup"><span data-stu-id="60779-110">To be able to extend your app you must understand all the core capabilities and the entry points that work in a collaborative space.</span></span> <span data-ttu-id="60779-111">Você pode experimentar os pontos de extensão para criar seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="60779-111">You can experiment with the extension points for building your apps.</span></span> <span data-ttu-id="60779-112">Componentes importantes do projeto de aplicativo ajudam você a configurar corretamente a página do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="60779-112">Important app project components help you to correctly configure your app page.</span></span> <span data-ttu-id="60779-113">Teams aplicativo pode ter [vários recursos e](../concepts/capabilities-overview.md) pontos de [entrada.](../concepts/extensibility-points.md)</span><span class="sxs-lookup"><span data-stu-id="60779-113">Teams app can have [multiple capabilities](../concepts/capabilities-overview.md) and [entry points](../concepts/extensibility-points.md).</span></span>

## <a name="understand-your-use-cases"></a><span data-ttu-id="60779-114">Compreender os casos de uso</span><span class="sxs-lookup"><span data-stu-id="60779-114">Understand your use cases</span></span>

<span data-ttu-id="60779-115">Você pode reconhecer problemas do usuário e identificar as respostas a alguns problemas comuns que os usuários enfrentam.</span><span class="sxs-lookup"><span data-stu-id="60779-115">You can recognize user issues and identify the answers to some common problems the users face.</span></span> <span data-ttu-id="60779-116">Você pode criar seu Teams de usuário encontrando a combinação certa para atender às necessidades do usuário.</span><span class="sxs-lookup"><span data-stu-id="60779-116">You can build your Teams app by finding the right combination to meet your user's needs.</span></span> <span data-ttu-id="60779-117">[Entenda os casos de](../concepts/design/understand-use-cases.md) uso para saber como um usuário final interage com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="60779-117">[Understand use cases](../concepts/design/understand-use-cases.md) to know how an end-user interacts with your app.</span></span> <span data-ttu-id="60779-118">Você aprende a entender o usuário e seus problemas.</span><span class="sxs-lookup"><span data-stu-id="60779-118">You learn to understand the user and their problem.</span></span> <span data-ttu-id="60779-119">Algumas perguntas comuns respondidas são as seguinte:</span><span class="sxs-lookup"><span data-stu-id="60779-119">Some common questions answered are as follows:</span></span>

* <span data-ttu-id="60779-120">Você precisa de autenticação?</span><span class="sxs-lookup"><span data-stu-id="60779-120">Do you need authentication?</span></span>
* <span data-ttu-id="60779-121">Qual é o problema que seu aplicativo vai resolver?</span><span class="sxs-lookup"><span data-stu-id="60779-121">What problem is your app going to solve?</span></span>
* <span data-ttu-id="60779-122">Who são os usuários finais do aplicativo?</span><span class="sxs-lookup"><span data-stu-id="60779-122">Who are the end-users of the app?</span></span>
* <span data-ttu-id="60779-123">Como deve ser a experiência de integração e o que mais o aplicativo pode fazer?</span><span class="sxs-lookup"><span data-stu-id="60779-123">How should the onboarding experience be and what else the app can do?</span></span>

## <a name="map-your-use-cases-to-teams-app-capabilities"></a><span data-ttu-id="60779-124">Mapear seus casos de uso para Teams de aplicativos</span><span class="sxs-lookup"><span data-stu-id="60779-124">Map your use cases to Teams app capabilities</span></span>

<span data-ttu-id="60779-125">[Mapear seus casos de uso](../concepts/design/map-use-cases.md) abrange alguns cenários comuns e como escolher os recursos do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="60779-125">[Map your use cases](../concepts/design/map-use-cases.md) covers some common scenarios and how to choose your app's capabilities.</span></span> <span data-ttu-id="60779-126">Informações para compartilhar seu aplicativo e colaborar em itens em um sistema externo são fornecidas.</span><span class="sxs-lookup"><span data-stu-id="60779-126">Information to share your app and collaborate on items in an external system is provided.</span></span> <span data-ttu-id="60779-127">Você também pode aprender a iniciar fluxos de trabalho e enviar notificações aos usuários.</span><span class="sxs-lookup"><span data-stu-id="60779-127">You can also learn how to initiate workflows and send notifications to users.</span></span> <span data-ttu-id="60779-128">Obter dicas adicionais sobre por onde começar, como obter social com usuários, bots de conversa e combinar vários recursos.</span><span class="sxs-lookup"><span data-stu-id="60779-128">Get additional tips on where to start, how to get social with users, conversational bots, and combining multiple features.</span></span>

## <a name="see-also"></a><span data-ttu-id="60779-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="60779-129">See also</span></span>

* [<span data-ttu-id="60779-130">Integrar aplicativos Web com Teams</span><span class="sxs-lookup"><span data-stu-id="60779-130">Integrate web apps with Teams</span></span>](../samples/integrating-web-apps.md)
* [<span data-ttu-id="60779-131">Criar seu primeiro Microsoft Teams app</span><span class="sxs-lookup"><span data-stu-id="60779-131">Build your first Microsoft Teams app</span></span>](../build-your-first-app/build-first-app-overview.md)

## <a name="next-step"></a><span data-ttu-id="60779-132">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="60779-132">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="60779-133">Compreender Teams de aplicativos</span><span class="sxs-lookup"><span data-stu-id="60779-133">Understand Teams app capabilities</span></span>](capabilities-overview.md)

