---
title: Projetando seu aplicativo personalizado
author: heath-hamilton
description: Saiba como projetar Microsoft Teams aplicativos. Os recursos incluem Microsoft Teams kit de interface do usuário, práticas recomendadas, exemplos e muito mais.
localization_priority: Normal
ms.author: surbhigupta
ms.topic: overview
ms.openlocfilehash: 19b8f8cbcbc52aa02ccd5d94f5bc4c088f2ae28a
ms.sourcegitcommit: 4224c44d169b1a289cbf1d3353de6bc6de7c7ea8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2021
ms.locfileid: "52644872"
---
# <a name="designing-your-microsoft-teams-app"></a><span data-ttu-id="39488-104">Projetando seu Microsoft Teams aplicativo</span><span class="sxs-lookup"><span data-stu-id="39488-104">Designing your Microsoft Teams app</span></span>

:::image type="content" source="../../assets/images/design-guidelines-overview.png" alt-text="Imagem conceitual introduzindo as Microsoft Teams de design.":::

<span data-ttu-id="39488-106">Se você é um designer, gerente de produto, desenvolvedor ou criador usando ferramentas de código baixo, essas diretrizes podem ajudá-lo a tomar rapidamente as decisões de design corretas para seu Microsoft Teams app.</span><span class="sxs-lookup"><span data-stu-id="39488-106">Whether you're a designer, product manager, developer, or maker using low-code tools, these guidelines can help you quickly make the right design decisions for your Microsoft Teams app.</span></span>

## <a name="creating-a-cohesive-experience"></a><span data-ttu-id="39488-107">Criando uma experiência coesiva</span><span class="sxs-lookup"><span data-stu-id="39488-107">Creating a cohesive experience</span></span>

<span data-ttu-id="39488-108">Projetar um aplicativo Teams é como projetar um aplicativo Web convencional, mas também um pouco diferente.</span><span class="sxs-lookup"><span data-stu-id="39488-108">Designing a Teams app is like designing a conventional web app—but also a little different.</span></span> <span data-ttu-id="39488-109">Um design eficaz realça os atributos exclusivos do seu aplicativo ao se ajustar naturalmente aos Teams e contextos.</span><span class="sxs-lookup"><span data-stu-id="39488-109">An effective design highlights your app's unique attributes while fitting naturally with Teams features and contexts.</span></span>

<span data-ttu-id="39488-110">Essas diretrizes e recursos podem ajudá-lo a atingir esse equilíbrio.</span><span class="sxs-lookup"><span data-stu-id="39488-110">These guidelines and resources can help you strike that balance.</span></span> <span data-ttu-id="39488-111">Você vai saber o que fazer e o que evitar ao projetar seu aplicativo Teams (como navegação de vários níveis em uma guia).</span><span class="sxs-lookup"><span data-stu-id="39488-111">You'll know what to do and what to avoid when designing your Teams app (such as multi-level navigation in a tab).</span></span>

## <a name="teams-app-design-principles"></a><span data-ttu-id="39488-112">Teams de design de aplicativo</span><span class="sxs-lookup"><span data-stu-id="39488-112">Teams app design principles</span></span>

<span data-ttu-id="39488-113">Teams aplicativos ajudam as pessoas a alcançarem mais juntos.</span><span class="sxs-lookup"><span data-stu-id="39488-113">Teams apps help people achieve more together.</span></span> <span data-ttu-id="39488-114">Use esses princípios para orientar seu design.</span><span class="sxs-lookup"><span data-stu-id="39488-114">Use these principles to guide your design.</span></span>

:::row:::
   :::column span="":::

### <a name="collaborative"></a><span data-ttu-id="39488-115">Colaborativo</span><span class="sxs-lookup"><span data-stu-id="39488-115">Collaborative</span></span>

<span data-ttu-id="39488-116">Teams aplicativos ajudam as pessoas a alcançarem mais juntos.</span><span class="sxs-lookup"><span data-stu-id="39488-116">Teams apps help people achieve more together.</span></span> <span data-ttu-id="39488-117">Use esses princípios para orientar seu design.</span><span class="sxs-lookup"><span data-stu-id="39488-117">Use these principles to guide your design.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="trustworthy"></a><span data-ttu-id="39488-118">Confiável</span><span class="sxs-lookup"><span data-stu-id="39488-118">Trustworthy</span></span>

<span data-ttu-id="39488-119">O aplicativo é seguro e compatível.</span><span class="sxs-lookup"><span data-stu-id="39488-119">The app is secure and compliant.</span></span> <span data-ttu-id="39488-120">Os usuários podem encontrar facilmente informações sobre privacidade.</span><span class="sxs-lookup"><span data-stu-id="39488-120">Users can easily find information about privacy.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="globally-inclusive"></a><span data-ttu-id="39488-121">Globalmente inclusiva</span><span class="sxs-lookup"><span data-stu-id="39488-121">Globally inclusive</span></span>

<span data-ttu-id="39488-122">Pessoas de todos os backgrounds, skillsets e disciplinas podem usar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="39488-122">People of all backgrounds, skillsets, and disciplines can use the app.</span></span> <span data-ttu-id="39488-123">É cultural, racial e socialmente ciente.</span><span class="sxs-lookup"><span data-stu-id="39488-123">It’s culturally, racially, and socially aware.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="light"></a><span data-ttu-id="39488-124">Leve</span><span class="sxs-lookup"><span data-stu-id="39488-124">Light</span></span>

<span data-ttu-id="39488-125">O aplicativo se concentra em cenários principais que se misturam com Teams fluxos de trabalho.</span><span class="sxs-lookup"><span data-stu-id="39488-125">The app focuses on core scenarios that blend with Teams workflows.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="native-or-distinct"></a><span data-ttu-id="39488-126">Nativo ou distinto</span><span class="sxs-lookup"><span data-stu-id="39488-126">Native or distinct</span></span>

<span data-ttu-id="39488-127">O aplicativo usa componentes Teams design nativos ou seus próprios.</span><span class="sxs-lookup"><span data-stu-id="39488-127">The app uses native Teams design components or your own.</span></span> <span data-ttu-id="39488-128">Não há combinação de esquemas de cores, controles e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="39488-128">There’s no blend of color schemes, controls, and so on.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="useful"></a><span data-ttu-id="39488-129">Útil</span><span class="sxs-lookup"><span data-stu-id="39488-129">Useful</span></span>

<span data-ttu-id="39488-130">O aplicativo se baseia em um cenário que as pessoas precisam fazer Teams.</span><span class="sxs-lookup"><span data-stu-id="39488-130">The app is based on a scenario people need to do in Teams.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="easy-to-use"></a><span data-ttu-id="39488-131">Fácil de usar</span><span class="sxs-lookup"><span data-stu-id="39488-131">Easy to use</span></span>

<span data-ttu-id="39488-132">A interface do usuário é fácil de entender, agradável na aparência e no tom e torna as pessoas mais produtivas.</span><span class="sxs-lookup"><span data-stu-id="39488-132">The UI is easy to understand, pleasant in look and tone, and makes people more productive.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="responsive"></a><span data-ttu-id="39488-133">Dinâmico</span><span class="sxs-lookup"><span data-stu-id="39488-133">Responsive</span></span>

<span data-ttu-id="39488-134">O aplicativo é agnóstico de dispositivo e tela.</span><span class="sxs-lookup"><span data-stu-id="39488-134">The app is device and screen agnostic.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="accessible"></a><span data-ttu-id="39488-135">Acessíveis</span><span class="sxs-lookup"><span data-stu-id="39488-135">Accessible</span></span>

<span data-ttu-id="39488-136">O aplicativo atende Teams requisitos de acessibilidade em termos de contraste de cores, alternativas de navegação e muito mais.</span><span class="sxs-lookup"><span data-stu-id="39488-136">The app meets Teams accessibility requirements in terms of color contrast, navigation alternatives, and more.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="well-described"></a><span data-ttu-id="39488-137">Bem descrito</span><span class="sxs-lookup"><span data-stu-id="39488-137">Well described</span></span>

<span data-ttu-id="39488-138">Texto, ícones e imagens fazem com que ele seja claro para o que o aplicativo é e como usá-lo.</span><span class="sxs-lookup"><span data-stu-id="39488-138">Text, icons, and images make it clear what the app is for and how to use it.</span></span>

   :::column-end:::
:::row-end:::

## <a name="teams-design-system"></a><span data-ttu-id="39488-139">Teams design</span><span class="sxs-lookup"><span data-stu-id="39488-139">Teams design system</span></span>

<span data-ttu-id="39488-140">Saiba os [fundamentos do Teams de aplicativos](design-teams-app-fundamentals.md), incluindo layout, esquemas de cores e muito mais.</span><span class="sxs-lookup"><span data-stu-id="39488-140">Learn the [fundamentals of Teams app design](design-teams-app-fundamentals.md), including layout, color schemes, and more.</span></span>

## <a name="app-capabilities"></a><span data-ttu-id="39488-141">Recursos do aplicativo</span><span class="sxs-lookup"><span data-stu-id="39488-141">App capabilities</span></span>

<span data-ttu-id="39488-142">Entenda como as pessoas adicionam, usam e gerenciam Teams aplicativos para aproveitar ao máximo cada recurso em seu design.</span><span class="sxs-lookup"><span data-stu-id="39488-142">Understand how people add, use, and manage Teams apps to make the most of each capability in your design.</span></span>

* [<span data-ttu-id="39488-143">Aplicativos pessoais</span><span class="sxs-lookup"><span data-stu-id="39488-143">Personal apps</span></span>](../../concepts/design/personal-apps.md)
* [<span data-ttu-id="39488-144">Guias</span><span class="sxs-lookup"><span data-stu-id="39488-144">Tabs</span></span>](../../tabs/design/tabs.md)
* [<span data-ttu-id="39488-145">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="39488-145">Messaging extensions</span></span>](../../messaging-extensions/design/messaging-extension-design.md)
* [<span data-ttu-id="39488-146">Bots</span><span class="sxs-lookup"><span data-stu-id="39488-146">Bots</span></span>](../../bots/design/bots.md)
* [<span data-ttu-id="39488-147">Extensões de reunião</span><span class="sxs-lookup"><span data-stu-id="39488-147">Meeting extensions</span></span>](../../apps-in-teams-meetings/design/designing-apps-in-meetings.md)

## <a name="ui-templates"></a><span data-ttu-id="39488-148">Modelos de Interface de Usuário </span><span class="sxs-lookup"><span data-stu-id="39488-148">UI templates</span></span>

<span data-ttu-id="39488-149">Crie rapidamente designs complexos e de alta fidelidade com modelos para Teams casos de uso e [fluxos de trabalho](design-teams-app-ui-templates.md)comuns.</span><span class="sxs-lookup"><span data-stu-id="39488-149">Quickly create complex, high-fidelity designs with [templates for common Teams use cases and workflows](design-teams-app-ui-templates.md).</span></span>

## <a name="basic-ui-components"></a><span data-ttu-id="39488-150">Componentes básicos da Interface de Usuário</span><span class="sxs-lookup"><span data-stu-id="39488-150">Basic UI components</span></span>

<span data-ttu-id="39488-151">Com base na interface do usuário fluente, esses são os [elementos principais que](design-teams-app-basic-ui-components.md) você pode usar para criar Teams experiências do zero.</span><span class="sxs-lookup"><span data-stu-id="39488-151">Based on Fluent UI, these are the [core elements](design-teams-app-basic-ui-components.md) you can use to create Teams experiences from scratch.</span></span>

## <a name="tools-and-samples"></a><span data-ttu-id="39488-152">Tools and samples</span><span class="sxs-lookup"><span data-stu-id="39488-152">Tools and samples</span></span>

<span data-ttu-id="39488-153">As ferramentas a seguir podem ajudar designers e desenvolvedores a começar:</span><span class="sxs-lookup"><span data-stu-id="39488-153">The following tools can help designers and developers get started:</span></span>

### <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="39488-154">Kit de Interface do Usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="39488-154">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="39488-155">Projete um Teams com componentes da interface do usuário, modelos e exemplos que você pode arrastar, soltar e modificar conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="39488-155">Design a Teams app with UI components, templates, and examples that you can drag, drop, and modify as needed.</span></span> <span data-ttu-id="39488-156">O kit de interface do usuário também inclui informações abrangentes sobre como os aplicativos devem ter aparência e comportamento em diferentes Teams cenários.</span><span class="sxs-lookup"><span data-stu-id="39488-156">The UI kit also includes comprehensive information about how apps should look and behave in different Teams scenarios.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="39488-157">Obter o kit de interface do usuário (Figma)</span><span class="sxs-lookup"><span data-stu-id="39488-157">Get the UI kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

### <a name="microsoft-teams-ui-library"></a><span data-ttu-id="39488-158">Microsoft Teams Biblioteca da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="39488-158">Microsoft Teams UI Library</span></span>

<span data-ttu-id="39488-159">Exibir e testar modelos Teams de interface do usuário individuais e componentes relacionados no navegador.</span><span class="sxs-lookup"><span data-stu-id="39488-159">View and test individual Teams UI templates and related components in your browser.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="39488-160">Experimente a biblioteca da interface do usuário (playground)</span><span class="sxs-lookup"><span data-stu-id="39488-160">Try the UI library (playground)</span></span>](https://dev-int.teams.microsoft.com/storybook/main/index.html)

<span data-ttu-id="39488-161">Import these templates and related components directly into your Teams app project.</span><span class="sxs-lookup"><span data-stu-id="39488-161">Import these templates and related components directly into your Teams app project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="39488-162">Obter a biblioteca da interface do usuário (GitHub)</span><span class="sxs-lookup"><span data-stu-id="39488-162">Get the UI library (GitHub)</span></span>](https://github.com/OfficeDev/microsoft-teams-ui-component-library)

### <a name="sample-app"></a><span data-ttu-id="39488-163">Exemplo de aplicativo</span><span class="sxs-lookup"><span data-stu-id="39488-163">Sample app</span></span>

<span data-ttu-id="39488-164">Você pode carregar um aplicativo de exemplo para ver como os aplicativos devem parecer e se comportar no Teams cliente.</span><span class="sxs-lookup"><span data-stu-id="39488-164">You can upload a sample app to see how apps should look and behave in the Teams client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="39488-165">Obter o aplicativo de exemplo (GitHub)</span><span class="sxs-lookup"><span data-stu-id="39488-165">Get the sample app (GitHub)</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-ui-templates/ts)

## <a name="other-resources"></a><span data-ttu-id="39488-166">Outros recursos</span><span class="sxs-lookup"><span data-stu-id="39488-166">Other resources</span></span>

<span data-ttu-id="39488-167">Para saber mais, experimente um dos seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="39488-167">To learn more, try one of the following resources:</span></span>

### <a name="fluent-ui-documentation"></a><span data-ttu-id="39488-168">Documentação da interface do usuário do Fluent</span><span class="sxs-lookup"><span data-stu-id="39488-168">Fluent UI documentation</span></span>

<span data-ttu-id="39488-169">Obter exemplos de código e detalhes de implementação para os componentes básicos da interface do usuário fluent usados para criar Teams experiências.</span><span class="sxs-lookup"><span data-stu-id="39488-169">Get code samples and implementation details for the basic Fluent UI components used to build Teams experiences.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="39488-170">Experimente Teams da interface do usuário (interface do usuário fluente)</span><span class="sxs-lookup"><span data-stu-id="39488-170">Try Teams UI components (Fluent UI)</span></span>](https://fluentsite.z22.web.core.windows.net/)

### <a name="adaptive-cards-designer"></a><span data-ttu-id="39488-171">Designer de Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="39488-171">Adaptive Cards designer</span></span>

<span data-ttu-id="39488-172">Projete Cartões Adaptáveis em nossa ferramenta baseada na Web.</span><span class="sxs-lookup"><span data-stu-id="39488-172">Design Adaptive Cards in our web-based tool.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="39488-173">Experimente o designer de Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="39488-173">Try the Adaptive Cards designer</span></span>](https://adaptivecards.io/designer/)
