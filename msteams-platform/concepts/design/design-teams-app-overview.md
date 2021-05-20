---
title: Projetando seu aplicativo personalizado
author: heath-hamilton
description: Aprenda a projetar Microsoft Teams aplicativos. Os recursos incluem o kit de interface do usuário Microsoft Teams, práticas recomendadas, exemplos e muito mais.
localization_priority: Normal
ms.author: lajanuar
ms.topic: overview
ms.openlocfilehash: 2f21872bd8c37026528ff6fde282e8c433d5e052
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565113"
---
# <a name="designing-your-microsoft-teams-app"></a><span data-ttu-id="93d62-104">Projetando seu aplicativo de Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="93d62-104">Designing your Microsoft Teams app</span></span>

:::image type="content" source="../../assets/images/design-guidelines-overview.png" alt-text="Imagem conceitual introduzindo as diretrizes de design Microsoft Teams.":::

<span data-ttu-id="93d62-106">Se você é um designer, gerente de produto, desenvolvedor ou fabricante usando ferramentas de baixo código, essas diretrizes podem ajudá-lo a tomar rapidamente as decisões de design certas para o seu aplicativo Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="93d62-106">Whether you're a designer, product manager, developer, or maker using low-code tools, these guidelines can help you quickly make the right design decisions for your Microsoft Teams app.</span></span>

## <a name="teams-app-design-principles"></a><span data-ttu-id="93d62-107">Teams princípios de design de aplicativos</span><span class="sxs-lookup"><span data-stu-id="93d62-107">Teams app design principles</span></span>

<span data-ttu-id="93d62-108">Teams aplicativos ajudam as pessoas a alcançar mais juntos.</span><span class="sxs-lookup"><span data-stu-id="93d62-108">Teams apps help people achieve more together.</span></span> <span data-ttu-id="93d62-109">Use esses princípios para orientar seu design.</span><span class="sxs-lookup"><span data-stu-id="93d62-109">Use these principles to guide your design.</span></span>

:::row:::
   :::column span="":::

### <a name="collaborative"></a><span data-ttu-id="93d62-110">colaborativo</span><span class="sxs-lookup"><span data-stu-id="93d62-110">Collaborative</span></span>

<span data-ttu-id="93d62-111">Teams aplicativos ajudam as pessoas a alcançar mais juntos.</span><span class="sxs-lookup"><span data-stu-id="93d62-111">Teams apps help people achieve more together.</span></span> <span data-ttu-id="93d62-112">Use esses princípios para orientar seu design.</span><span class="sxs-lookup"><span data-stu-id="93d62-112">Use these principles to guide your design.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="trustworthy"></a><span data-ttu-id="93d62-113">confiável</span><span class="sxs-lookup"><span data-stu-id="93d62-113">Trustworthy</span></span>

<span data-ttu-id="93d62-114">O aplicativo é seguro e compatível.</span><span class="sxs-lookup"><span data-stu-id="93d62-114">The app is secure and compliant.</span></span> <span data-ttu-id="93d62-115">Os usuários podem facilmente encontrar informações sobre privacidade.</span><span class="sxs-lookup"><span data-stu-id="93d62-115">Users can easily find information about privacy.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="globally-inclusive"></a><span data-ttu-id="93d62-116">Globalmente inclusivo</span><span class="sxs-lookup"><span data-stu-id="93d62-116">Globally inclusive</span></span>

<span data-ttu-id="93d62-117">Pessoas de todas as origens, habilidades e disciplinas podem usar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="93d62-117">People of all backgrounds, skillsets, and disciplines can use the app.</span></span> <span data-ttu-id="93d62-118">É cultural, racial e socialmente consciente.</span><span class="sxs-lookup"><span data-stu-id="93d62-118">It’s culturally, racially, and socially aware.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="light"></a><span data-ttu-id="93d62-119">Leve</span><span class="sxs-lookup"><span data-stu-id="93d62-119">Light</span></span>

<span data-ttu-id="93d62-120">O aplicativo se concentra em cenários centrais que se misturam com fluxos de trabalho Teams.</span><span class="sxs-lookup"><span data-stu-id="93d62-120">The app focuses on core scenarios that blend with Teams workflows.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="native-or-distinct"></a><span data-ttu-id="93d62-121">Nativo ou distinto</span><span class="sxs-lookup"><span data-stu-id="93d62-121">Native or distinct</span></span>

<span data-ttu-id="93d62-122">O aplicativo usa componentes nativos de design Teams ou seus próprios.</span><span class="sxs-lookup"><span data-stu-id="93d62-122">The app uses native Teams design components or your own.</span></span> <span data-ttu-id="93d62-123">Não há mistura de esquemas de cores, controles, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="93d62-123">There’s no blend of color schemes, controls, and so on.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="useful"></a><span data-ttu-id="93d62-124">útil</span><span class="sxs-lookup"><span data-stu-id="93d62-124">Useful</span></span>

<span data-ttu-id="93d62-125">O aplicativo é baseado em um cenário que as pessoas precisam fazer em Teams.</span><span class="sxs-lookup"><span data-stu-id="93d62-125">The app is based on a scenario people need to do in Teams.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="easy-to-use"></a><span data-ttu-id="93d62-126">Fácil de usar</span><span class="sxs-lookup"><span data-stu-id="93d62-126">Easy to use</span></span>

<span data-ttu-id="93d62-127">A interface do usuário é fácil de entender, agradável no visual e no tom, e torna as pessoas mais produtivas.</span><span class="sxs-lookup"><span data-stu-id="93d62-127">The UI is easy to understand, pleasant in look and tone, and makes people more productive.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="responsive"></a><span data-ttu-id="93d62-128">Dinâmico</span><span class="sxs-lookup"><span data-stu-id="93d62-128">Responsive</span></span>

<span data-ttu-id="93d62-129">O aplicativo é dispositivo e tela agnóstica.</span><span class="sxs-lookup"><span data-stu-id="93d62-129">The app is device and screen agnostic.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="accessible"></a><span data-ttu-id="93d62-130">Acessíveis</span><span class="sxs-lookup"><span data-stu-id="93d62-130">Accessible</span></span>

<span data-ttu-id="93d62-131">O aplicativo atende Teams requisitos de acessibilidade em termos de contraste de cores, alternativas de navegação e muito mais.</span><span class="sxs-lookup"><span data-stu-id="93d62-131">The app meets Teams accessibility requirements in terms of color contrast, navigation alternatives, and more.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="well-described"></a><span data-ttu-id="93d62-132">Bem descrito</span><span class="sxs-lookup"><span data-stu-id="93d62-132">Well described</span></span>

<span data-ttu-id="93d62-133">Texto, ícones e imagens deixam claro para que é o aplicativo e como usá-lo.</span><span class="sxs-lookup"><span data-stu-id="93d62-133">Text, icons, and images make it clear what the app is for and how to use it.</span></span>

   :::column-end:::
:::row-end:::

## <a name="creating-a-cohesive-experience"></a><span data-ttu-id="93d62-134">Criando uma experiência coesa</span><span class="sxs-lookup"><span data-stu-id="93d62-134">Creating a cohesive experience</span></span>

<span data-ttu-id="93d62-135">Projetar um aplicativo Teams é como projetar um aplicativo web convencional — mas também um pouco diferente.</span><span class="sxs-lookup"><span data-stu-id="93d62-135">Designing a Teams app is like designing a conventional web app—but also a little different.</span></span> <span data-ttu-id="93d62-136">Um design eficaz destaca os atributos exclusivos do seu aplicativo, ao mesmo tempo em que se encaixa naturalmente com Teams recursos e contextos.</span><span class="sxs-lookup"><span data-stu-id="93d62-136">An effective design highlights your app's unique attributes while fitting naturally with Teams features and contexts.</span></span>

<span data-ttu-id="93d62-137">Essas diretrizes e recursos podem ajudá-lo a atingir esse equilíbrio.</span><span class="sxs-lookup"><span data-stu-id="93d62-137">These guidelines and resources can help you strike that balance.</span></span> <span data-ttu-id="93d62-138">Você saberá o que fazer e o que evitar ao projetar seu aplicativo Teams (como navegação multiníníveis em uma guia).</span><span class="sxs-lookup"><span data-stu-id="93d62-138">You'll know what to do and what to avoid when designing your Teams app (such as multi-level navigation in a tab).</span></span>

## <a name="planning-your-app"></a><span data-ttu-id="93d62-139">Planejando seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="93d62-139">Planning your app</span></span>

<span data-ttu-id="93d62-140">Para projetar um aplicativo de Teams de alta qualidade, você deve primeiro entender o que você quer que seu aplicativo faça e como você acha que as pessoas vão usá-lo.</span><span class="sxs-lookup"><span data-stu-id="93d62-140">To design a high-quality Teams app, you must first understand what you want your app to do and how you think people will use it.</span></span> <span data-ttu-id="93d62-141">Se você ainda não tem, tire um tempo para planejar corretamente [seu aplicativo](../../concepts/extensibility-points.md).</span><span class="sxs-lookup"><span data-stu-id="93d62-141">If you haven't already, take some time to properly [plan your app](../../concepts/extensibility-points.md).</span></span>

## <a name="design-fundamentals"></a><span data-ttu-id="93d62-142">Conceitos básicos de design</span><span class="sxs-lookup"><span data-stu-id="93d62-142">Design fundamentals</span></span>

<span data-ttu-id="93d62-143">Conheça os [fundamentos do design de aplicativos Teams](design-teams-app-fundamentals.md), incluindo layout, esquemas de cores e muito mais.</span><span class="sxs-lookup"><span data-stu-id="93d62-143">Learn the [fundamentals of Teams app design](design-teams-app-fundamentals.md), including layout, color schemes, and more.</span></span>

## <a name="basic-fluent-ui-components-for-teams"></a><span data-ttu-id="93d62-144">Componentes básicos da interface do usuário fluente para Teams</span><span class="sxs-lookup"><span data-stu-id="93d62-144">Basic Fluent UI components for Teams</span></span>

<span data-ttu-id="93d62-145">Com base na Interface Fluent, estes são os [elementos centrais para criar interfaces Teams familiares](design-teams-app-basic-ui-components.md).</span><span class="sxs-lookup"><span data-stu-id="93d62-145">Based on Fluent UI, these are the [core elements for creating familiar Teams interfaces](design-teams-app-basic-ui-components.md).</span></span>

## <a name="ui-templates"></a><span data-ttu-id="93d62-146">Modelos de Interface de Usuário </span><span class="sxs-lookup"><span data-stu-id="93d62-146">UI templates</span></span>

<span data-ttu-id="93d62-147">Crie rapidamente designs complexos e de alta fidelidade com [modelos para casos de uso de Teams comum e fluxos de trabalho](design-teams-app-ui-templates.md).</span><span class="sxs-lookup"><span data-stu-id="93d62-147">Quickly create complex, high-fidelity designs with [templates for common Teams use cases and workflows](design-teams-app-ui-templates.md).</span></span>

## <a name="app-capabilities"></a><span data-ttu-id="93d62-148">Recursos do aplicativo</span><span class="sxs-lookup"><span data-stu-id="93d62-148">App capabilities</span></span>

<span data-ttu-id="93d62-149">Entenda como as pessoas adicionam, usam e gerenciam aplicativos Teams para aproveitar ao máximo cada capacidade em seu design.</span><span class="sxs-lookup"><span data-stu-id="93d62-149">Understand how people add, use, and manage Teams apps to make the most of each capability in your design.</span></span>

* [<span data-ttu-id="93d62-150">Aplicativos pessoais</span><span class="sxs-lookup"><span data-stu-id="93d62-150">Personal apps</span></span>](../../concepts/design/personal-apps.md)
* [<span data-ttu-id="93d62-151">Guias</span><span class="sxs-lookup"><span data-stu-id="93d62-151">Tabs</span></span>](../../tabs/design/tabs.md)
* [<span data-ttu-id="93d62-152">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="93d62-152">Messaging extensions</span></span>](../../messaging-extensions/design/messaging-extension-design.md)
* [<span data-ttu-id="93d62-153">Bots</span><span class="sxs-lookup"><span data-stu-id="93d62-153">Bots</span></span>](../../bots/design/bots.md)
* [<span data-ttu-id="93d62-154">Extensões de reunião</span><span class="sxs-lookup"><span data-stu-id="93d62-154">Meeting extensions</span></span>](../../apps-in-teams-meetings/design/designing-apps-in-meetings.md)
* [<span data-ttu-id="93d62-155">Módulos de tarefas</span><span class="sxs-lookup"><span data-stu-id="93d62-155">Task modules</span></span>](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)
* [<span data-ttu-id="93d62-156">Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="93d62-156">Adaptive Cards</span></span>](../../task-modules-and-cards/cards/design-effective-cards.md)

## <a name="app-customization"></a><span data-ttu-id="93d62-157">Personalização de aplicativos</span><span class="sxs-lookup"><span data-stu-id="93d62-157">App customization</span></span>

<span data-ttu-id="93d62-158">Entenda como o administrador Teams pode personalizar ou renomear o aplicativo com base na necessidade da organização.</span><span class="sxs-lookup"><span data-stu-id="93d62-158">Understand how the Teams admin can customize or rebrand the app based on the organization's need.</span></span> <span data-ttu-id="93d62-159">Esta personalização é habilitada se você definir o `configurableProperties` esquema manifesto.</span><span class="sxs-lookup"><span data-stu-id="93d62-159">This customization is enabled if you define the `configurableProperties` in the manifest schema.</span></span> <span data-ttu-id="93d62-160">Para obter mais informações, consulte [Personalizar aplicativos em Microsoft Teams](/MicrosoftTeams/customize-apps).</span><span class="sxs-lookup"><span data-stu-id="93d62-160">For more information, see [Customize apps in Microsoft Teams](/MicrosoftTeams/customize-apps).</span></span>

> [!NOTE]
> <span data-ttu-id="93d62-161">A personalização de aplicativos permite que os administradores alterem a aparência dos aplicativos carregados através de bots, extensões de mensagens, guias e conectores.</span><span class="sxs-lookup"><span data-stu-id="93d62-161">App customization enables admins to change the look-and-feel of the apps loaded through bots, messaging extensions, tabs, and connectors.</span></span> <span data-ttu-id="93d62-162">Por exemplo, se o administrador Teams personalizar o nome de um aplicativo de *Contoso* para *Agente Contoso,* então o aplicativo aparecerá com o novo nome *Agente Contoso* para os usuários.</span><span class="sxs-lookup"><span data-stu-id="93d62-162">For example, if the Teams admin customizes the name of an app from *Contoso* to *Contoso Agent*, then the app will appear with the new name *Contoso Agent* to users.</span></span> <span data-ttu-id="93d62-163">No entanto, ao adicionar um conector a um chat, na lista os conectores ainda mostrarão o nome do aplicativo como *Contoso*.</span><span class="sxs-lookup"><span data-stu-id="93d62-163">However, while adding a connector to a chat, in the list the connectors will still show the name of the app as *Contoso*.</span></span>
> 
> <span data-ttu-id="93d62-164">Como uma prática recomendada, você deve fornecer diretrizes de personalização para usuários de aplicativos e clientes seguirem ao personalizar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="93d62-164">As a best practice, you must provide customization guidelines for app users and customers to follow when customizing your app.</span></span> <span data-ttu-id="93d62-165">Para obter mais informações, consulte [personalizar aplicativos em Microsoft Teams](/MicrosoftTeams/customize-apps).</span><span class="sxs-lookup"><span data-stu-id="93d62-165">For more information, see [customize apps in Microsoft Teams](/MicrosoftTeams/customize-apps).</span></span>

## <a name="tools-and-samples"></a><span data-ttu-id="93d62-166">Tools and samples</span><span class="sxs-lookup"><span data-stu-id="93d62-166">Tools and samples</span></span>

<span data-ttu-id="93d62-167">As seguintes ferramentas podem ajudar designers e desenvolvedores a começar:</span><span class="sxs-lookup"><span data-stu-id="93d62-167">The following tools can help designers and developers get started:</span></span>

### <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="93d62-168">Kit de Interface do Usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="93d62-168">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="93d62-169">Projete um aplicativo Teams com componentes de interface do usuário, modelos e exemplos que você pode arrastar, soltar e modificar conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="93d62-169">Design a Teams app with UI components, templates, and examples that you can drag, drop, and modify as needed.</span></span> <span data-ttu-id="93d62-170">O kit de interface do usuário também inclui informações abrangentes sobre como os aplicativos devem parecer e se comportar em diferentes cenários Teams.</span><span class="sxs-lookup"><span data-stu-id="93d62-170">The UI kit also includes comprehensive information about how apps should look and behave in different Teams scenarios.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="93d62-171">Obter o kit de interface do usuário (Figma)</span><span class="sxs-lookup"><span data-stu-id="93d62-171">Get the UI kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

### <a name="microsoft-teams-ui-library"></a><span data-ttu-id="93d62-172">Microsoft Teams Biblioteca de Interface do Usuário</span><span class="sxs-lookup"><span data-stu-id="93d62-172">Microsoft Teams UI Library</span></span>

<span data-ttu-id="93d62-173">Exibir e testar modelos de interface do usuário individuais Teams e componentes relacionados no seu navegador.</span><span class="sxs-lookup"><span data-stu-id="93d62-173">View and test individual Teams UI templates and related components in your browser.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="93d62-174">Experimente a biblioteca de interface do usuário (playground)</span><span class="sxs-lookup"><span data-stu-id="93d62-174">Try the UI library (playground)</span></span>](https://dev-int.teams.microsoft.com/storybook/main/index.html)

<span data-ttu-id="93d62-175">Importe esses modelos e componentes relacionados diretamente no seu projeto de aplicativo Teams.</span><span class="sxs-lookup"><span data-stu-id="93d62-175">Import these templates and related components directly into your Teams app project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="93d62-176">Obtenha a biblioteca de interface do usuário (GitHub)</span><span class="sxs-lookup"><span data-stu-id="93d62-176">Get the UI library (GitHub)</span></span>](https://github.com/OfficeDev/microsoft-teams-ui-component-library)

### <a name="sample-app"></a><span data-ttu-id="93d62-177">Aplicativo de amostra</span><span class="sxs-lookup"><span data-stu-id="93d62-177">Sample app</span></span>

<span data-ttu-id="93d62-178">Instale um aplicativo de exemplo para ver como os modelos de interface do usuário parecem e se comportam dentro de Teams contextos.</span><span class="sxs-lookup"><span data-stu-id="93d62-178">Install a sample app to see how UI templates look and behave within Teams contexts.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="93d62-179">Obtenha o aplicativo de amostra (GitHub)</span><span class="sxs-lookup"><span data-stu-id="93d62-179">Get the sample app (GitHub)</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-ui-templates/ts)

## <a name="other-resources"></a><span data-ttu-id="93d62-180">Outros recursos</span><span class="sxs-lookup"><span data-stu-id="93d62-180">Other resources</span></span>

<span data-ttu-id="93d62-181">Para saber mais, experimente um dos seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="93d62-181">To learn more, try one of the following resources:</span></span>

### <a name="fluent-ui-documentation"></a><span data-ttu-id="93d62-182">Documentação de interface do usuário fluente</span><span class="sxs-lookup"><span data-stu-id="93d62-182">Fluent UI documentation</span></span>

<span data-ttu-id="93d62-183">Obtenha amostras de código e detalhes de implementação para os componentes baseados em Interface do Usuário Fluentes usados para construir experiências Teams.</span><span class="sxs-lookup"><span data-stu-id="93d62-183">Get code samples and implementation details for the Fluent UI-based components used to build Teams experiences.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="93d62-184">Experimente Teams componentes de interface do usuário (Fluent UI)</span><span class="sxs-lookup"><span data-stu-id="93d62-184">Try Teams UI components (Fluent UI)</span></span>](https://fluentsite.z22.web.core.windows.net/)

### <a name="adaptive-cards-designer"></a><span data-ttu-id="93d62-185">Designer de Cartões Adaptativos</span><span class="sxs-lookup"><span data-stu-id="93d62-185">Adaptive Cards designer</span></span>

<span data-ttu-id="93d62-186">Design Adaptive Cards em nossa ferramenta baseada na Web.</span><span class="sxs-lookup"><span data-stu-id="93d62-186">Design Adaptive Cards in our web-based tool.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="93d62-187">Experimente o designer de Cartões Adaptativos</span><span class="sxs-lookup"><span data-stu-id="93d62-187">Try the Adaptive Cards designer</span></span>](https://adaptivecards.io/designer/)
