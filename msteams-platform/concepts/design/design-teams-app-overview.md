---
title: Criando seu aplicativo personalizado
author: heath-hamilton
description: Saiba como projetar os aplicativos do Microsoft Teams. Os recursos incluem o Microsoft Teams UI Kit, práticas recomendadas, exemplos e muito mais.
ms.author: lajanuar
ms.topic: overview
ms.openlocfilehash: 0160a59ed4ebc51e900acbb5d74735ccae0b6083
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2020
ms.locfileid: "49605746"
---
# <a name="designing-your-microsoft-teams-app"></a><span data-ttu-id="10b07-104">Projetando seu aplicativo do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="10b07-104">Designing your Microsoft Teams app</span></span>

:::image type="content" source="../../assets/images/design-guidelines-overview.png" alt-text="Imagem conceitual apresentando as diretrizes de design do Microsoft Teams.":::

<span data-ttu-id="10b07-106">Independentemente de você ser um designer, gerente de produto, desenvolvedor ou criador usando ferramentas de código baixo, essas diretrizes podem ajudá-lo a tomar as decisões corretas de design para seu aplicativo Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="10b07-106">Whether you're a designer, product manager, developer, or maker using low-code tools, these guidelines can help you quickly make the right design decisions for your Microsoft Teams app.</span></span>

## <a name="teams-app-design-principles"></a><span data-ttu-id="10b07-107">Princípios de design de aplicativos do teams</span><span class="sxs-lookup"><span data-stu-id="10b07-107">Teams app design principles</span></span>

<span data-ttu-id="10b07-108">Os aplicativos do teams ajudam as pessoas a se reunirem mais.</span><span class="sxs-lookup"><span data-stu-id="10b07-108">Teams apps help people achieve more together.</span></span> <span data-ttu-id="10b07-109">Use estes princípios para orientar seu design.</span><span class="sxs-lookup"><span data-stu-id="10b07-109">Use these principles to guide your design.</span></span>

:::row:::
   :::column span="":::

### <a name="collaborative"></a><span data-ttu-id="10b07-110">Colaborativa</span><span class="sxs-lookup"><span data-stu-id="10b07-110">Collaborative</span></span>

<span data-ttu-id="10b07-111">Os aplicativos do teams ajudam as pessoas a se reunirem mais.</span><span class="sxs-lookup"><span data-stu-id="10b07-111">Teams apps help people achieve more together.</span></span> <span data-ttu-id="10b07-112">Use estes princípios para orientar seu design.</span><span class="sxs-lookup"><span data-stu-id="10b07-112">Use these principles to guide your design.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="trustworthy"></a><span data-ttu-id="10b07-113">Confiança</span><span class="sxs-lookup"><span data-stu-id="10b07-113">Trustworthy</span></span>

<span data-ttu-id="10b07-114">O aplicativo é seguro e em conformidade.</span><span class="sxs-lookup"><span data-stu-id="10b07-114">The app is secure and compliant.</span></span> <span data-ttu-id="10b07-115">Os usuários podem encontrar informações sobre privacidade com facilidade.</span><span class="sxs-lookup"><span data-stu-id="10b07-115">Users can easily find information about privacy.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="globally-inclusive"></a><span data-ttu-id="10b07-116">Globalmente inclusivo</span><span class="sxs-lookup"><span data-stu-id="10b07-116">Globally inclusive</span></span>

<span data-ttu-id="10b07-117">Pessoas de todos os planos de fundo, skillsets e disciplinas podem usar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="10b07-117">People of all backgrounds, skillsets, and disciplines can use the app.</span></span> <span data-ttu-id="10b07-118">É cultural, racially e reconhece socialmente.</span><span class="sxs-lookup"><span data-stu-id="10b07-118">It’s culturally, racially, and socially aware.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="light"></a><span data-ttu-id="10b07-119">Leve</span><span class="sxs-lookup"><span data-stu-id="10b07-119">Light</span></span>

<span data-ttu-id="10b07-120">O aplicativo se concentra nos cenários principais que se misturam com os fluxos de trabalho do teams.</span><span class="sxs-lookup"><span data-stu-id="10b07-120">The app focuses on core scenarios that blend with Teams workflows.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="native-or-distinct"></a><span data-ttu-id="10b07-121">Nativo ou distinto</span><span class="sxs-lookup"><span data-stu-id="10b07-121">Native or distinct</span></span>

<span data-ttu-id="10b07-122">O aplicativo usa os componentes de design de equipes nativas ou seus próprios.</span><span class="sxs-lookup"><span data-stu-id="10b07-122">The app uses native Teams design components or your own.</span></span> <span data-ttu-id="10b07-123">Não há mistura de esquemas de cores, controles, etc.</span><span class="sxs-lookup"><span data-stu-id="10b07-123">There’s no blend of color schemes, controls, etc.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="useful"></a><span data-ttu-id="10b07-124">Convé</span><span class="sxs-lookup"><span data-stu-id="10b07-124">Useful</span></span>

<span data-ttu-id="10b07-125">O aplicativo é baseado em um cenário que as pessoas precisam fazer no Teams.</span><span class="sxs-lookup"><span data-stu-id="10b07-125">The app is based on a scenario people need to do in Teams.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="easy-to-use"></a><span data-ttu-id="10b07-126">Fácil de usar</span><span class="sxs-lookup"><span data-stu-id="10b07-126">Easy to use</span></span>

<span data-ttu-id="10b07-127">A interface do usuário é fácil de entender, agradável em aparência e Tom, e torna as pessoas mais produtivas.</span><span class="sxs-lookup"><span data-stu-id="10b07-127">The UI is easy to understand, pleasant in look and tone, and makes people more productive.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="responsive"></a><span data-ttu-id="10b07-128">Dinâmico</span><span class="sxs-lookup"><span data-stu-id="10b07-128">Responsive</span></span>

<span data-ttu-id="10b07-129">O aplicativo é um dispositivo e uma tela independente.</span><span class="sxs-lookup"><span data-stu-id="10b07-129">The app is device and screen agnostic.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="accessible"></a><span data-ttu-id="10b07-130">Acessíveis</span><span class="sxs-lookup"><span data-stu-id="10b07-130">Accessible</span></span>

<span data-ttu-id="10b07-131">O aplicativo atende aos requisitos de acessibilidade do teams em termos de contraste de cores, alternativas de navegação e muito mais.</span><span class="sxs-lookup"><span data-stu-id="10b07-131">The app meets Teams accessibility requirements in terms of color contrast, navigation alternatives, and more.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="well-described"></a><span data-ttu-id="10b07-132">Bem descrita</span><span class="sxs-lookup"><span data-stu-id="10b07-132">Well described</span></span>

<span data-ttu-id="10b07-133">Texto, ícones e imagens tornam claro o que o aplicativo é e como usá-lo.</span><span class="sxs-lookup"><span data-stu-id="10b07-133">Text, icons, and images make it clear what the app is for and how to use it.</span></span>

   :::column-end:::
:::row-end:::

## <a name="creating-a-cohesive-experience"></a><span data-ttu-id="10b07-134">Criar uma experiência coesa</span><span class="sxs-lookup"><span data-stu-id="10b07-134">Creating a cohesive experience</span></span>

<span data-ttu-id="10b07-135">Criar um aplicativo do teams é como criar um aplicativo Web convencional, mas também um pouco diferente.</span><span class="sxs-lookup"><span data-stu-id="10b07-135">Designing a Teams app is like designing a conventional web app—but also a little different.</span></span> <span data-ttu-id="10b07-136">Um design eficaz realça os atributos exclusivos do seu aplicativo, ao se ajustar naturalmente com recursos e contextos do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="10b07-136">An effective design highlights your app's unique attributes while fitting naturally with Teams features and contexts.</span></span>

<span data-ttu-id="10b07-137">Essas diretrizes e recursos podem ajudá-lo a se ajustar nesse equilíbrio.</span><span class="sxs-lookup"><span data-stu-id="10b07-137">These guidelines and resources can help you strike that balance.</span></span> <span data-ttu-id="10b07-138">Você sabe o que fazer e o que evitar ao criar seu aplicativo do Teams (como navegação de vários níveis em uma guia).</span><span class="sxs-lookup"><span data-stu-id="10b07-138">You'll know what to do and what to avoid when designing your Teams app (such as multi-level navigation in a tab).</span></span>

## <a name="planning-your-app"></a><span data-ttu-id="10b07-139">Planejar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="10b07-139">Planning your app</span></span>

<span data-ttu-id="10b07-140">Para criar um aplicativo de equipes de alta qualidade, você deve primeiro compreender o que deseja que seu aplicativo faça e como acha que as pessoas o usarão.</span><span class="sxs-lookup"><span data-stu-id="10b07-140">To design a high-quality Teams app, you must first understand what you want your app to do and how you think people will use it.</span></span> <span data-ttu-id="10b07-141">Se você ainda não tiver feito isso, Reserve algum tempo para [planejar corretamente o aplicativo](../../concepts/extensibility-points.md).</span><span class="sxs-lookup"><span data-stu-id="10b07-141">If you haven't already, take some time to properly [plan your app](../../concepts/extensibility-points.md).</span></span>

## <a name="design-fundamentals"></a><span data-ttu-id="10b07-142">Conceitos básicos de design</span><span class="sxs-lookup"><span data-stu-id="10b07-142">Design fundamentals</span></span>

<span data-ttu-id="10b07-143">Aprenda os [conceitos básicos do design de aplicativos do teams](design-teams-app-fundamentals.md), incluindo layout, esquemas de cores e muito mais.</span><span class="sxs-lookup"><span data-stu-id="10b07-143">Learn the [fundamentals of Teams app design](design-teams-app-fundamentals.md), including layout, color schemes, and more.</span></span>

## <a name="basic-fluent-ui-components-for-teams"></a><span data-ttu-id="10b07-144">Componentes de interface do usuário do Fluent básicos para o Teams</span><span class="sxs-lookup"><span data-stu-id="10b07-144">Basic Fluent UI components for Teams</span></span>

<span data-ttu-id="10b07-145">Com base em uma interface do usuário fluente, estes são os [principais elementos para a criação de interfaces familiares do Microsoft Teams](design-teams-app-basic-ui-components.md).</span><span class="sxs-lookup"><span data-stu-id="10b07-145">Based on Fluent UI, these are the [core elements for creating familiar Teams interfaces](design-teams-app-basic-ui-components.md).</span></span>

## <a name="app-capabilities"></a><span data-ttu-id="10b07-146">Recursos do aplicativo</span><span class="sxs-lookup"><span data-stu-id="10b07-146">App capabilities</span></span>

<span data-ttu-id="10b07-147">Entenda como as pessoas adicionam, usam e gerenciam aplicativos do teams para aproveitar ao máximo cada capacidade em seu design.</span><span class="sxs-lookup"><span data-stu-id="10b07-147">Understand how people add, use, and manage Teams apps to make the most of each capability in your design.</span></span>

* [<span data-ttu-id="10b07-148">Aplicativos pessoais</span><span class="sxs-lookup"><span data-stu-id="10b07-148">Personal apps</span></span>](../../concepts/design/personal-apps.md)
* [<span data-ttu-id="10b07-149">Guias</span><span class="sxs-lookup"><span data-stu-id="10b07-149">Tabs</span></span>](../../tabs/design/tabs.md)
* [<span data-ttu-id="10b07-150">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="10b07-150">Messaging extensions</span></span>](../../messaging-extensions/design/messaging-extension-design.md)
* [<span data-ttu-id="10b07-151">Bots</span><span class="sxs-lookup"><span data-stu-id="10b07-151">Bots</span></span>](../../bots/design/bots.md)
* [<span data-ttu-id="10b07-152">Extensões de reunião</span><span class="sxs-lookup"><span data-stu-id="10b07-152">Meeting extensions</span></span>](../../apps-in-teams-meetings/design/designing-apps-in-meetings.md)
* [<span data-ttu-id="10b07-153">Módulos de tarefas</span><span class="sxs-lookup"><span data-stu-id="10b07-153">Task modules</span></span>](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)
* [<span data-ttu-id="10b07-154">Cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="10b07-154">Adaptive Cards</span></span>](../../task-modules-and-cards/cards/design-effective-cards.md)

## <a name="ui-templates"></a><span data-ttu-id="10b07-155">Modelos de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="10b07-155">UI templates</span></span>

<span data-ttu-id="10b07-156">Crie rapidamente designs complexos e de alta fidelidade com [modelos para casos de uso e fluxos de trabalho comuns do teams](design-teams-app-ui-templates.md).</span><span class="sxs-lookup"><span data-stu-id="10b07-156">Quickly create complex, high-fidelity designs with [templates for common Teams use cases and workflows](design-teams-app-ui-templates.md).</span></span>

## <a name="get-started-with-the-microsoft-teams-ui-kit"></a><span data-ttu-id="10b07-157">Introdução ao kit de interface do usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="10b07-157">Get started with the Microsoft Teams UI Kit</span></span>

<span data-ttu-id="10b07-158">O kit de interface do usuário do Microsoft Teams tem componentes de interface do usuário, modelos e exemplos que você pode arrastar, descartar e modificar conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="10b07-158">The Microsoft Teams UI Kit has UI components, templates, and examples that you can drag, drop, and modify as needed.</span></span> <span data-ttu-id="10b07-159">O kit de interface do usuário também inclui informações abrangentes sobre como os aplicativos devem se parecer e se comportar em diferentes cenários do teams.</span><span class="sxs-lookup"><span data-stu-id="10b07-159">The UI kit also includes comprehensive information about how apps should look and behave in different Teams scenarios.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="10b07-160">Obter o kit de interface do usuário do Microsoft Teams (figma)</span><span class="sxs-lookup"><span data-stu-id="10b07-160">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="other-resources"></a><span data-ttu-id="10b07-161">Outros recursos</span><span class="sxs-lookup"><span data-stu-id="10b07-161">Other resources</span></span>

<span data-ttu-id="10b07-162">Para saber mais, tente um dos recursos a seguir.</span><span class="sxs-lookup"><span data-stu-id="10b07-162">To learn more, try one of the following resources.</span></span>

### <a name="fluent-ui"></a><span data-ttu-id="10b07-163">Interface do usuário do Fluent</span><span class="sxs-lookup"><span data-stu-id="10b07-163">Fluent UI</span></span>

<span data-ttu-id="10b07-164">Obtenha exemplos de código e detalhes de implementação para os componentes de interface do usuário fluente usados para criar experiências de equipes.</span><span class="sxs-lookup"><span data-stu-id="10b07-164">Get code samples and implementation details for the Fluent UI-based components used to build Teams experiences.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="10b07-165">Experimente o Teams UI Components (UI Fluent)</span><span class="sxs-lookup"><span data-stu-id="10b07-165">Try out Teams UI components (Fluent UI)</span></span>](https://fluentsite.z22.web.core.windows.net/)

### <a name="adaptive-cards-designer"></a><span data-ttu-id="10b07-166">Designer de cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="10b07-166">Adaptive Cards designer</span></span>

<span data-ttu-id="10b07-167">Designar cartões adaptáveis em uma ferramenta baseada na Web.</span><span class="sxs-lookup"><span data-stu-id="10b07-167">Design Adaptive Cards in a web-based tool.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="10b07-168">Experimente o designer de cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="10b07-168">Try the Adaptive Cards designer</span></span>](https://adaptivecards.io/designer/)
