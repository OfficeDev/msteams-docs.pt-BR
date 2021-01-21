---
title: Projetando seu aplicativo personalizado
author: heath-hamilton
description: Saiba como projetar aplicativos do Microsoft Teams. Os recursos incluem o Kit de Interface do Usuário do Microsoft Teams, práticas recomendadas, exemplos e muito mais.
ms.author: lajanuar
ms.topic: overview
ms.openlocfilehash: 0c791b1e4733cd2a015e443ca5c4d0c433dd4d31
ms.sourcegitcommit: 00c657e3bf57d3b92aca7da941cde47a2eeff4d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "49911902"
---
# <a name="designing-your-microsoft-teams-app"></a><span data-ttu-id="1aad2-104">Projetando seu aplicativo do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="1aad2-104">Designing your Microsoft Teams app</span></span>

:::image type="content" source="../../assets/images/design-guidelines-overview.png" alt-text="Imagem conceitual apresentando as diretrizes de design do Microsoft Teams.":::

<span data-ttu-id="1aad2-106">Seja você um designer, gerente de produtos, desenvolvedor ou criador usando ferramentas de código baixo, essas diretrizes podem ajudá-lo a tomar rapidamente as decisões de design corretas para seu aplicativo do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="1aad2-106">Whether you're a designer, product manager, developer, or maker using low-code tools, these guidelines can help you quickly make the right design decisions for your Microsoft Teams app.</span></span>

## <a name="teams-app-design-principles"></a><span data-ttu-id="1aad2-107">Princípios de design de aplicativos do Teams</span><span class="sxs-lookup"><span data-stu-id="1aad2-107">Teams app design principles</span></span>

<span data-ttu-id="1aad2-108">Os aplicativos do Teams ajudam as pessoas a obter mais em conjunto.</span><span class="sxs-lookup"><span data-stu-id="1aad2-108">Teams apps help people achieve more together.</span></span> <span data-ttu-id="1aad2-109">Use estes princípios para orientar seu design.</span><span class="sxs-lookup"><span data-stu-id="1aad2-109">Use these principles to guide your design.</span></span>

:::row:::
   :::column span="":::

### <a name="collaborative"></a><span data-ttu-id="1aad2-110">Collaborative</span><span class="sxs-lookup"><span data-stu-id="1aad2-110">Collaborative</span></span>

<span data-ttu-id="1aad2-111">Os aplicativos do Teams ajudam as pessoas a obter mais em conjunto.</span><span class="sxs-lookup"><span data-stu-id="1aad2-111">Teams apps help people achieve more together.</span></span> <span data-ttu-id="1aad2-112">Use estes princípios para orientar seu design.</span><span class="sxs-lookup"><span data-stu-id="1aad2-112">Use these principles to guide your design.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="trustworthy"></a><span data-ttu-id="1aad2-113">Confiável</span><span class="sxs-lookup"><span data-stu-id="1aad2-113">Trustworthy</span></span>

<span data-ttu-id="1aad2-114">O aplicativo é seguro e compatível.</span><span class="sxs-lookup"><span data-stu-id="1aad2-114">The app is secure and compliant.</span></span> <span data-ttu-id="1aad2-115">Os usuários podem encontrar facilmente informações sobre privacidade.</span><span class="sxs-lookup"><span data-stu-id="1aad2-115">Users can easily find information about privacy.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="globally-inclusive"></a><span data-ttu-id="1aad2-116">Globalmente inclusivo</span><span class="sxs-lookup"><span data-stu-id="1aad2-116">Globally inclusive</span></span>

<span data-ttu-id="1aad2-117">Pessoas de todas as origens, habilidades e disciplinas podem usar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1aad2-117">People of all backgrounds, skillsets, and disciplines can use the app.</span></span> <span data-ttu-id="1aad2-118">É cultural, racial e socialmente ciente.</span><span class="sxs-lookup"><span data-stu-id="1aad2-118">It’s culturally, racially, and socially aware.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="light"></a><span data-ttu-id="1aad2-119">Leve</span><span class="sxs-lookup"><span data-stu-id="1aad2-119">Light</span></span>

<span data-ttu-id="1aad2-120">O aplicativo se concentra em cenários principais que se misturam com fluxos de trabalho do Teams.</span><span class="sxs-lookup"><span data-stu-id="1aad2-120">The app focuses on core scenarios that blend with Teams workflows.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="native-or-distinct"></a><span data-ttu-id="1aad2-121">Nativo ou distinto</span><span class="sxs-lookup"><span data-stu-id="1aad2-121">Native or distinct</span></span>

<span data-ttu-id="1aad2-122">O aplicativo usa componentes de design nativos do Teams ou seus próprios.</span><span class="sxs-lookup"><span data-stu-id="1aad2-122">The app uses native Teams design components or your own.</span></span> <span data-ttu-id="1aad2-123">Não há mistura de esquemas de cores, controles etc.</span><span class="sxs-lookup"><span data-stu-id="1aad2-123">There’s no blend of color schemes, controls, etc.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="useful"></a><span data-ttu-id="1aad2-124">Útil</span><span class="sxs-lookup"><span data-stu-id="1aad2-124">Useful</span></span>

<span data-ttu-id="1aad2-125">O aplicativo é baseado em um cenário que as pessoas precisam fazer no Teams.</span><span class="sxs-lookup"><span data-stu-id="1aad2-125">The app is based on a scenario people need to do in Teams.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="easy-to-use"></a><span data-ttu-id="1aad2-126">Fácil de usar</span><span class="sxs-lookup"><span data-stu-id="1aad2-126">Easy to use</span></span>

<span data-ttu-id="1aad2-127">A interface do usuário é fácil de entender, se parecer com o tom e deixar as pessoas mais produtivas.</span><span class="sxs-lookup"><span data-stu-id="1aad2-127">The UI is easy to understand, pleasant in look and tone, and makes people more productive.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="responsive"></a><span data-ttu-id="1aad2-128">Dinâmico</span><span class="sxs-lookup"><span data-stu-id="1aad2-128">Responsive</span></span>

<span data-ttu-id="1aad2-129">O aplicativo é agnóstico de dispositivo e tela.</span><span class="sxs-lookup"><span data-stu-id="1aad2-129">The app is device and screen agnostic.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="accessible"></a><span data-ttu-id="1aad2-130">Acessíveis</span><span class="sxs-lookup"><span data-stu-id="1aad2-130">Accessible</span></span>

<span data-ttu-id="1aad2-131">O aplicativo atende aos requisitos de acessibilidade do Teams em termos de contraste de cor, alternativas de navegação e muito mais.</span><span class="sxs-lookup"><span data-stu-id="1aad2-131">The app meets Teams accessibility requirements in terms of color contrast, navigation alternatives, and more.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="well-described"></a><span data-ttu-id="1aad2-132">Bem descrito</span><span class="sxs-lookup"><span data-stu-id="1aad2-132">Well described</span></span>

<span data-ttu-id="1aad2-133">Texto, ícones e imagens deixa claro para que o aplicativo é e como usá-lo.</span><span class="sxs-lookup"><span data-stu-id="1aad2-133">Text, icons, and images make it clear what the app is for and how to use it.</span></span>

   :::column-end:::
:::row-end:::

## <a name="creating-a-cohesive-experience"></a><span data-ttu-id="1aad2-134">Criando uma experiência coeso</span><span class="sxs-lookup"><span data-stu-id="1aad2-134">Creating a cohesive experience</span></span>

<span data-ttu-id="1aad2-135">Projetar um aplicativo do Teams é como projetar um aplicativo Web convencional, mas também um pouco diferente.</span><span class="sxs-lookup"><span data-stu-id="1aad2-135">Designing a Teams app is like designing a conventional web app—but also a little different.</span></span> <span data-ttu-id="1aad2-136">Um design eficaz destaca os atributos exclusivos do seu aplicativo, ao mesmo tempo em que se ajusta naturalmente aos recursos e contextos do Teams.</span><span class="sxs-lookup"><span data-stu-id="1aad2-136">An effective design highlights your app's unique attributes while fitting naturally with Teams features and contexts.</span></span>

<span data-ttu-id="1aad2-137">Essas diretrizes e recursos podem ajudá-lo a atingir esse equilíbrio.</span><span class="sxs-lookup"><span data-stu-id="1aad2-137">These guidelines and resources can help you strike that balance.</span></span> <span data-ttu-id="1aad2-138">Você vai saber o que fazer e o que evitar ao projetar seu aplicativo teams (como navegação de vários níveis em uma guia).</span><span class="sxs-lookup"><span data-stu-id="1aad2-138">You'll know what to do and what to avoid when designing your Teams app (such as multi-level navigation in a tab).</span></span>

## <a name="planning-your-app"></a><span data-ttu-id="1aad2-139">Planejando seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="1aad2-139">Planning your app</span></span>

<span data-ttu-id="1aad2-140">Para projetar um aplicativo do Teams de alta qualidade, você deve primeiro entender o que deseja que seu aplicativo faça e como acha que as pessoas o usarão.</span><span class="sxs-lookup"><span data-stu-id="1aad2-140">To design a high-quality Teams app, you must first understand what you want your app to do and how you think people will use it.</span></span> <span data-ttu-id="1aad2-141">Caso ainda não tenha feito isso, leve algum tempo para planejar [corretamente seu aplicativo.](../../concepts/extensibility-points.md)</span><span class="sxs-lookup"><span data-stu-id="1aad2-141">If you haven't already, take some time to properly [plan your app](../../concepts/extensibility-points.md).</span></span>

## <a name="design-fundamentals"></a><span data-ttu-id="1aad2-142">Conceitos básicos de design</span><span class="sxs-lookup"><span data-stu-id="1aad2-142">Design fundamentals</span></span>

<span data-ttu-id="1aad2-143">Conheça os [conceitos básicos do design de aplicativos](design-teams-app-fundamentals.md)do Teams, incluindo layout, esquemas de cores e muito mais.</span><span class="sxs-lookup"><span data-stu-id="1aad2-143">Learn the [fundamentals of Teams app design](design-teams-app-fundamentals.md), including layout, color schemes, and more.</span></span>

## <a name="basic-fluent-ui-components-for-teams"></a><span data-ttu-id="1aad2-144">Componentes básicos da interface do usuário do Fluent para o Teams</span><span class="sxs-lookup"><span data-stu-id="1aad2-144">Basic Fluent UI components for Teams</span></span>

<span data-ttu-id="1aad2-145">Com base na interface do usuário do Fluent, esses são os [elementos principais para a criação de interfaces conhecidas do Teams.](design-teams-app-basic-ui-components.md)</span><span class="sxs-lookup"><span data-stu-id="1aad2-145">Based on Fluent UI, these are the [core elements for creating familiar Teams interfaces](design-teams-app-basic-ui-components.md).</span></span>

## <a name="ui-templates"></a><span data-ttu-id="1aad2-146">Modelos de Interface de Usuário </span><span class="sxs-lookup"><span data-stu-id="1aad2-146">UI templates</span></span>

<span data-ttu-id="1aad2-147">Crie rapidamente designs complexos de alta fidelidade com [modelos para casos de uso comuns e fluxos de trabalho do Teams.](design-teams-app-ui-templates.md)</span><span class="sxs-lookup"><span data-stu-id="1aad2-147">Quickly create complex, high-fidelity designs with [templates for common Teams use cases and workflows](design-teams-app-ui-templates.md).</span></span>

## <a name="app-capabilities"></a><span data-ttu-id="1aad2-148">Recursos do aplicativo</span><span class="sxs-lookup"><span data-stu-id="1aad2-148">App capabilities</span></span>

<span data-ttu-id="1aad2-149">Entenda como as pessoas adicionam, usam e gerenciam aplicativos do Teams para aproveitar ao máximo cada recurso em seu design.</span><span class="sxs-lookup"><span data-stu-id="1aad2-149">Understand how people add, use, and manage Teams apps to make the most of each capability in your design.</span></span>

* [<span data-ttu-id="1aad2-150">Aplicativos pessoais</span><span class="sxs-lookup"><span data-stu-id="1aad2-150">Personal apps</span></span>](../../concepts/design/personal-apps.md)
* [<span data-ttu-id="1aad2-151">Guias</span><span class="sxs-lookup"><span data-stu-id="1aad2-151">Tabs</span></span>](../../tabs/design/tabs.md)
* [<span data-ttu-id="1aad2-152">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="1aad2-152">Messaging extensions</span></span>](../../messaging-extensions/design/messaging-extension-design.md)
* [<span data-ttu-id="1aad2-153">Bots</span><span class="sxs-lookup"><span data-stu-id="1aad2-153">Bots</span></span>](../../bots/design/bots.md)
* [<span data-ttu-id="1aad2-154">Extensões de reunião</span><span class="sxs-lookup"><span data-stu-id="1aad2-154">Meeting extensions</span></span>](../../apps-in-teams-meetings/design/designing-apps-in-meetings.md)
* [<span data-ttu-id="1aad2-155">Módulos de tarefas</span><span class="sxs-lookup"><span data-stu-id="1aad2-155">Task modules</span></span>](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)
* [<span data-ttu-id="1aad2-156">Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="1aad2-156">Adaptive Cards</span></span>](../../task-modules-and-cards/cards/design-effective-cards.md)

## <a name="tools-and-samples"></a><span data-ttu-id="1aad2-157">Tools and samples</span><span class="sxs-lookup"><span data-stu-id="1aad2-157">Tools and samples</span></span>

<span data-ttu-id="1aad2-158">As ferramentas a seguir podem ajudar designers e desenvolvedores a começar.</span><span class="sxs-lookup"><span data-stu-id="1aad2-158">The following tools can help designers and developers get started.</span></span>

### <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="1aad2-159">Kit de interface do usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="1aad2-159">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="1aad2-160">Projete um aplicativo do Teams com componentes da interface do usuário, modelos e exemplos que você pode arrastar, soltar e modificar conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="1aad2-160">Design a Teams app with UI components, templates, and examples that you can drag, drop, and modify as needed.</span></span> <span data-ttu-id="1aad2-161">O kit de interface do usuário também inclui informações abrangentes sobre como os aplicativos devem ter aparência e comportamento em diferentes cenários do Teams.</span><span class="sxs-lookup"><span data-stu-id="1aad2-161">The UI kit also includes comprehensive information about how apps should look and behave in different Teams scenarios.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1aad2-162">Obter o kit de interface do usuário (Ltdma)</span><span class="sxs-lookup"><span data-stu-id="1aad2-162">Get the UI kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

### <a name="microsoft-teams-ui-library"></a><span data-ttu-id="1aad2-163">Biblioteca de interface do usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="1aad2-163">Microsoft Teams UI Library</span></span>

<span data-ttu-id="1aad2-164">Exibir e testar modelos de interface do usuário individuais do Teams e componentes relacionados em seu navegador.</span><span class="sxs-lookup"><span data-stu-id="1aad2-164">View and test individual Teams UI templates and related components in your browser.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1aad2-165">Experimente a biblioteca de interface do usuário (playground)</span><span class="sxs-lookup"><span data-stu-id="1aad2-165">Try the UI library (playground)</span></span>](https://dev-int.teams.microsoft.com/storybook/main/index.html)

<span data-ttu-id="1aad2-166">Importe esses modelos e componentes relacionados diretamente para seu projeto de aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="1aad2-166">Import these templates and related components directly into your Teams app project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1aad2-167">Obter a biblioteca de interface do usuário (GitHub)</span><span class="sxs-lookup"><span data-stu-id="1aad2-167">Get the UI library (GitHub)</span></span>](https://github.com/OfficeDev/microsoft-teams-ui-component-library)

### <a name="sample-app"></a><span data-ttu-id="1aad2-168">Aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="1aad2-168">Sample app</span></span>

<span data-ttu-id="1aad2-169">Instale um aplicativo de exemplo para ver a aparência e o comportamento dos modelos de interface do usuário nos contextos do Teams.</span><span class="sxs-lookup"><span data-stu-id="1aad2-169">Install a sample app to see how UI templates look and behave within Teams contexts.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1aad2-170">Obter o aplicativo de exemplo (GitHub)</span><span class="sxs-lookup"><span data-stu-id="1aad2-170">Get the sample app (GitHub)</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-ui-templates/ts)

## <a name="other-resources"></a><span data-ttu-id="1aad2-171">Outros recursos</span><span class="sxs-lookup"><span data-stu-id="1aad2-171">Other resources</span></span>

<span data-ttu-id="1aad2-172">Para saber mais, tente um dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="1aad2-172">To learn more, try one of the following resources.</span></span>

### <a name="fluent-ui-documentation"></a><span data-ttu-id="1aad2-173">Documentação da interface do usuário do Fluent</span><span class="sxs-lookup"><span data-stu-id="1aad2-173">Fluent UI documentation</span></span>

<span data-ttu-id="1aad2-174">Obter exemplos de código e detalhes de implementação para os componentes baseados na interface do usuário do Fluent usados para criar experiências do Teams.</span><span class="sxs-lookup"><span data-stu-id="1aad2-174">Get code samples and implementation details for the Fluent UI-based components used to build Teams experiences.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1aad2-175">Experimente os componentes da interface do usuário do Teams (interface do usuário do Fluent)</span><span class="sxs-lookup"><span data-stu-id="1aad2-175">Try Teams UI components (Fluent UI)</span></span>](https://fluentsite.z22.web.core.windows.net/)

### <a name="adaptive-cards-designer"></a><span data-ttu-id="1aad2-176">Designer de Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="1aad2-176">Adaptive Cards designer</span></span>

<span data-ttu-id="1aad2-177">Projete cartões adaptáveis em nossa ferramenta baseada na Web.</span><span class="sxs-lookup"><span data-stu-id="1aad2-177">Design Adaptive Cards in our web-based tool.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1aad2-178">Experimente o designer de Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="1aad2-178">Try the Adaptive Cards designer</span></span>](https://adaptivecards.io/designer/)
