---
title: Projetando seu aplicativo personalizado
author: heath-hamilton
description: Saiba como projetar aplicativos do Microsoft Teams. Os recursos incluem o Kit de interface do usuário do Microsoft Teams, práticas recomendadas, exemplos e muito mais.
localization_priority: Normal
ms.author: lajanuar
ms.topic: overview
ms.openlocfilehash: d7f3e89ce5ad51fb1a8cecddf0b22d59544ecc09
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019878"
---
# <a name="designing-your-microsoft-teams-app"></a><span data-ttu-id="a4e75-104">Projetando seu aplicativo do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="a4e75-104">Designing your Microsoft Teams app</span></span>

:::image type="content" source="../../assets/images/design-guidelines-overview.png" alt-text="Imagem conceitual apresentando as diretrizes de design do Microsoft Teams.":::

<span data-ttu-id="a4e75-106">Se você é um designer, gerente de produto, desenvolvedor ou criador usando ferramentas de código baixo, essas diretrizes podem ajudá-lo a tomar rapidamente as decisões de design corretas para seu aplicativo do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="a4e75-106">Whether you're a designer, product manager, developer, or maker using low-code tools, these guidelines can help you quickly make the right design decisions for your Microsoft Teams app.</span></span>

## <a name="teams-app-design-principles"></a><span data-ttu-id="a4e75-107">Princípios de design de aplicativos do Teams</span><span class="sxs-lookup"><span data-stu-id="a4e75-107">Teams app design principles</span></span>

<span data-ttu-id="a4e75-108">Os aplicativos do Teams ajudam as pessoas a alcançarem mais juntos.</span><span class="sxs-lookup"><span data-stu-id="a4e75-108">Teams apps help people achieve more together.</span></span> <span data-ttu-id="a4e75-109">Use esses princípios para orientar seu design.</span><span class="sxs-lookup"><span data-stu-id="a4e75-109">Use these principles to guide your design.</span></span>

:::row:::
   :::column span="":::

### <a name="collaborative"></a><span data-ttu-id="a4e75-110">Colaborativo</span><span class="sxs-lookup"><span data-stu-id="a4e75-110">Collaborative</span></span>

<span data-ttu-id="a4e75-111">Os aplicativos do Teams ajudam as pessoas a alcançarem mais juntos.</span><span class="sxs-lookup"><span data-stu-id="a4e75-111">Teams apps help people achieve more together.</span></span> <span data-ttu-id="a4e75-112">Use esses princípios para orientar seu design.</span><span class="sxs-lookup"><span data-stu-id="a4e75-112">Use these principles to guide your design.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="trustworthy"></a><span data-ttu-id="a4e75-113">Confiável</span><span class="sxs-lookup"><span data-stu-id="a4e75-113">Trustworthy</span></span>

<span data-ttu-id="a4e75-114">O aplicativo é seguro e compatível.</span><span class="sxs-lookup"><span data-stu-id="a4e75-114">The app is secure and compliant.</span></span> <span data-ttu-id="a4e75-115">Os usuários podem encontrar facilmente informações sobre privacidade.</span><span class="sxs-lookup"><span data-stu-id="a4e75-115">Users can easily find information about privacy.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="globally-inclusive"></a><span data-ttu-id="a4e75-116">Globalmente inclusiva</span><span class="sxs-lookup"><span data-stu-id="a4e75-116">Globally inclusive</span></span>

<span data-ttu-id="a4e75-117">Pessoas de todos os backgrounds, skillsets e disciplinas podem usar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a4e75-117">People of all backgrounds, skillsets, and disciplines can use the app.</span></span> <span data-ttu-id="a4e75-118">É cultural, racial e socialmente ciente.</span><span class="sxs-lookup"><span data-stu-id="a4e75-118">It’s culturally, racially, and socially aware.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="light"></a><span data-ttu-id="a4e75-119">Leve</span><span class="sxs-lookup"><span data-stu-id="a4e75-119">Light</span></span>

<span data-ttu-id="a4e75-120">O aplicativo se concentra em cenários principais que se misturam com fluxos de trabalho do Teams.</span><span class="sxs-lookup"><span data-stu-id="a4e75-120">The app focuses on core scenarios that blend with Teams workflows.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="native-or-distinct"></a><span data-ttu-id="a4e75-121">Nativo ou distinto</span><span class="sxs-lookup"><span data-stu-id="a4e75-121">Native or distinct</span></span>

<span data-ttu-id="a4e75-122">O aplicativo usa componentes nativos de design do Teams ou seus próprios.</span><span class="sxs-lookup"><span data-stu-id="a4e75-122">The app uses native Teams design components or your own.</span></span> <span data-ttu-id="a4e75-123">Não há combinação de esquemas de cores, controles etc.</span><span class="sxs-lookup"><span data-stu-id="a4e75-123">There’s no blend of color schemes, controls, etc.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="useful"></a><span data-ttu-id="a4e75-124">Útil</span><span class="sxs-lookup"><span data-stu-id="a4e75-124">Useful</span></span>

<span data-ttu-id="a4e75-125">O aplicativo se baseia em um cenário que as pessoas precisam fazer no Teams.</span><span class="sxs-lookup"><span data-stu-id="a4e75-125">The app is based on a scenario people need to do in Teams.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="easy-to-use"></a><span data-ttu-id="a4e75-126">Fácil de usar</span><span class="sxs-lookup"><span data-stu-id="a4e75-126">Easy to use</span></span>

<span data-ttu-id="a4e75-127">A interface do usuário é fácil de entender, agradável na aparência e no tom e torna as pessoas mais produtivas.</span><span class="sxs-lookup"><span data-stu-id="a4e75-127">The UI is easy to understand, pleasant in look and tone, and makes people more productive.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="responsive"></a><span data-ttu-id="a4e75-128">Dinâmico</span><span class="sxs-lookup"><span data-stu-id="a4e75-128">Responsive</span></span>

<span data-ttu-id="a4e75-129">O aplicativo é agnóstico de dispositivo e tela.</span><span class="sxs-lookup"><span data-stu-id="a4e75-129">The app is device and screen agnostic.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="accessible"></a><span data-ttu-id="a4e75-130">Acessíveis</span><span class="sxs-lookup"><span data-stu-id="a4e75-130">Accessible</span></span>

<span data-ttu-id="a4e75-131">O aplicativo atende aos requisitos de acessibilidade do Teams em termos de contraste de cores, alternativas de navegação e muito mais.</span><span class="sxs-lookup"><span data-stu-id="a4e75-131">The app meets Teams accessibility requirements in terms of color contrast, navigation alternatives, and more.</span></span>

   :::column-end:::
   :::column span="":::

### <a name="well-described"></a><span data-ttu-id="a4e75-132">Bem descrito</span><span class="sxs-lookup"><span data-stu-id="a4e75-132">Well described</span></span>

<span data-ttu-id="a4e75-133">Texto, ícones e imagens fazem com que ele seja claro para o que o aplicativo é e como usá-lo.</span><span class="sxs-lookup"><span data-stu-id="a4e75-133">Text, icons, and images make it clear what the app is for and how to use it.</span></span>

   :::column-end:::
:::row-end:::

## <a name="creating-a-cohesive-experience"></a><span data-ttu-id="a4e75-134">Criando uma experiência coesiva</span><span class="sxs-lookup"><span data-stu-id="a4e75-134">Creating a cohesive experience</span></span>

<span data-ttu-id="a4e75-135">Projetar um aplicativo do Teams é como projetar um aplicativo Web convencional, mas também um pouco diferente.</span><span class="sxs-lookup"><span data-stu-id="a4e75-135">Designing a Teams app is like designing a conventional web app—but also a little different.</span></span> <span data-ttu-id="a4e75-136">Um design efetivo realça os atributos exclusivos do seu aplicativo ao se ajustar naturalmente aos recursos e contextos do Teams.</span><span class="sxs-lookup"><span data-stu-id="a4e75-136">An effective design highlights your app's unique attributes while fitting naturally with Teams features and contexts.</span></span>

<span data-ttu-id="a4e75-137">Essas diretrizes e recursos podem ajudá-lo a atingir esse equilíbrio.</span><span class="sxs-lookup"><span data-stu-id="a4e75-137">These guidelines and resources can help you strike that balance.</span></span> <span data-ttu-id="a4e75-138">Você vai saber o que fazer e o que evitar ao projetar seu aplicativo do Teams (como navegação de vários níveis em uma guia).</span><span class="sxs-lookup"><span data-stu-id="a4e75-138">You'll know what to do and what to avoid when designing your Teams app (such as multi-level navigation in a tab).</span></span>

## <a name="planning-your-app"></a><span data-ttu-id="a4e75-139">Planejando seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="a4e75-139">Planning your app</span></span>

<span data-ttu-id="a4e75-140">Para projetar um aplicativo do Teams de alta qualidade, você deve primeiro entender o que deseja que seu aplicativo faça e como você acha que as pessoas o usarão.</span><span class="sxs-lookup"><span data-stu-id="a4e75-140">To design a high-quality Teams app, you must first understand what you want your app to do and how you think people will use it.</span></span> <span data-ttu-id="a4e75-141">Se você ainda não tiver feito isso, desem algum tempo para planejar [corretamente seu aplicativo.](../../concepts/extensibility-points.md)</span><span class="sxs-lookup"><span data-stu-id="a4e75-141">If you haven't already, take some time to properly [plan your app](../../concepts/extensibility-points.md).</span></span>

## <a name="design-fundamentals"></a><span data-ttu-id="a4e75-142">Conceitos básicos de design</span><span class="sxs-lookup"><span data-stu-id="a4e75-142">Design fundamentals</span></span>

<span data-ttu-id="a4e75-143">Saiba os [fundamentos do design de aplicativo do Teams,](design-teams-app-fundamentals.md)incluindo layout, esquemas de cores e muito mais.</span><span class="sxs-lookup"><span data-stu-id="a4e75-143">Learn the [fundamentals of Teams app design](design-teams-app-fundamentals.md), including layout, color schemes, and more.</span></span>

## <a name="basic-fluent-ui-components-for-teams"></a><span data-ttu-id="a4e75-144">Componentes básicos da interface do usuário do Fluent para o Teams</span><span class="sxs-lookup"><span data-stu-id="a4e75-144">Basic Fluent UI components for Teams</span></span>

<span data-ttu-id="a4e75-145">Com base na interface do usuário fluente, esses são os [elementos fundamentais para a criação de interfaces familiares do Teams.](design-teams-app-basic-ui-components.md)</span><span class="sxs-lookup"><span data-stu-id="a4e75-145">Based on Fluent UI, these are the [core elements for creating familiar Teams interfaces](design-teams-app-basic-ui-components.md).</span></span>

## <a name="ui-templates"></a><span data-ttu-id="a4e75-146">Modelos de Interface de Usuário </span><span class="sxs-lookup"><span data-stu-id="a4e75-146">UI templates</span></span>

<span data-ttu-id="a4e75-147">Crie rapidamente designs complexos e de alta fidelidade com modelos para [o Teams comum usar casos e fluxos de trabalho.](design-teams-app-ui-templates.md)</span><span class="sxs-lookup"><span data-stu-id="a4e75-147">Quickly create complex, high-fidelity designs with [templates for common Teams use cases and workflows](design-teams-app-ui-templates.md).</span></span>

## <a name="app-capabilities"></a><span data-ttu-id="a4e75-148">Recursos do aplicativo</span><span class="sxs-lookup"><span data-stu-id="a4e75-148">App capabilities</span></span>

<span data-ttu-id="a4e75-149">Entenda como as pessoas adicionam, usam e gerenciam aplicativos do Teams para aproveitar ao máximo cada recurso em seu design.</span><span class="sxs-lookup"><span data-stu-id="a4e75-149">Understand how people add, use, and manage Teams apps to make the most of each capability in your design.</span></span>

* [<span data-ttu-id="a4e75-150">Aplicativos pessoais</span><span class="sxs-lookup"><span data-stu-id="a4e75-150">Personal apps</span></span>](../../concepts/design/personal-apps.md)
* [<span data-ttu-id="a4e75-151">Guias</span><span class="sxs-lookup"><span data-stu-id="a4e75-151">Tabs</span></span>](../../tabs/design/tabs.md)
* [<span data-ttu-id="a4e75-152">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="a4e75-152">Messaging extensions</span></span>](../../messaging-extensions/design/messaging-extension-design.md)
* [<span data-ttu-id="a4e75-153">Bots</span><span class="sxs-lookup"><span data-stu-id="a4e75-153">Bots</span></span>](../../bots/design/bots.md)
* [<span data-ttu-id="a4e75-154">Extensões de reunião</span><span class="sxs-lookup"><span data-stu-id="a4e75-154">Meeting extensions</span></span>](../../apps-in-teams-meetings/design/designing-apps-in-meetings.md)
* [<span data-ttu-id="a4e75-155">Módulos de tarefas</span><span class="sxs-lookup"><span data-stu-id="a4e75-155">Task modules</span></span>](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)
* [<span data-ttu-id="a4e75-156">Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="a4e75-156">Adaptive Cards</span></span>](../../task-modules-and-cards/cards/design-effective-cards.md)

## <a name="app-customization"></a><span data-ttu-id="a4e75-157">Personalização de aplicativos</span><span class="sxs-lookup"><span data-stu-id="a4e75-157">App customization</span></span>

<span data-ttu-id="a4e75-158">Entenda como o administrador do Teams pode personalizar ou renomear o aplicativo com base na necessidade da organização.</span><span class="sxs-lookup"><span data-stu-id="a4e75-158">Understand how the Teams admin can customize or rebrand the app based on the organization's need.</span></span> <span data-ttu-id="a4e75-159">Essa personalização será habilitada se você definir `configurableProperties` o esquema de manifesto.</span><span class="sxs-lookup"><span data-stu-id="a4e75-159">This customization is enabled if you define the `configurableProperties` in the manifest schema.</span></span> <span data-ttu-id="a4e75-160">Para obter mais informações, consulte [Personalizar aplicativos no Microsoft Teams](/MicrosoftTeams/customize-apps).</span><span class="sxs-lookup"><span data-stu-id="a4e75-160">For more information, see [Customize apps in Microsoft Teams](/MicrosoftTeams/customize-apps).</span></span>

> [!NOTE]
> <span data-ttu-id="a4e75-161">Esse recurso está disponível apenas na visualização do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="a4e75-161">This feature is currently available in developer preview only.</span></span>
> 
> <span data-ttu-id="a4e75-162">A personalização do aplicativo permite que os administradores alterem a aparência dos aplicativos carregados por meio de bots, extensões de mensagens, guias e conectores.</span><span class="sxs-lookup"><span data-stu-id="a4e75-162">App customization enables admins to change the look-and-feel of the apps loaded through bots, messaging extensions, tabs, and connectors.</span></span> <span data-ttu-id="a4e75-163">Por exemplo, se o administrador do Teams personalizar o nome de um aplicativo da *Contoso* para o Agente *contoso,* o aplicativo aparecerá com o novo nome Agente *contoso* para usuários.</span><span class="sxs-lookup"><span data-stu-id="a4e75-163">For example, if the Teams admin customizes the name of an app from *Contoso* to *Contoso Agent*, then the app will appear with the new name *Contoso Agent* to users.</span></span> <span data-ttu-id="a4e75-164">No entanto, ao adicionar um conector a um chat, na lista os conectores ainda mostrarão o nome do aplicativo como *Contoso*.</span><span class="sxs-lookup"><span data-stu-id="a4e75-164">However, while adding a connector to a chat, in the list the connectors will still show the name of the app as *Contoso*.</span></span>
> 
> <span data-ttu-id="a4e75-165">Como prática prática prática, você deve fornecer diretrizes de personalização para usuários de aplicativos e clientes a seguir ao personalizar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a4e75-165">As a best practice, you must provide customization guidelines for app users and customers to follow when customizing your app.</span></span> <span data-ttu-id="a4e75-166">Para obter mais informações, consulte [personalizar aplicativos no Microsoft Teams](/MicrosoftTeams/customize-apps).</span><span class="sxs-lookup"><span data-stu-id="a4e75-166">For more information, see [customize apps in Microsoft Teams](/MicrosoftTeams/customize-apps).</span></span>

## <a name="tools-and-samples"></a><span data-ttu-id="a4e75-167">Tools and samples</span><span class="sxs-lookup"><span data-stu-id="a4e75-167">Tools and samples</span></span>

<span data-ttu-id="a4e75-168">As ferramentas a seguir podem ajudar designers e desenvolvedores a começar:</span><span class="sxs-lookup"><span data-stu-id="a4e75-168">The following tools can help designers and developers get started:</span></span>

### <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="a4e75-169">Kit de Interface do Usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="a4e75-169">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="a4e75-170">Projete um aplicativo do Teams com componentes da interface do usuário, modelos e exemplos que você pode arrastar, soltar e modificar conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="a4e75-170">Design a Teams app with UI components, templates, and examples that you can drag, drop, and modify as needed.</span></span> <span data-ttu-id="a4e75-171">O kit de interface do usuário também inclui informações abrangentes sobre como os aplicativos devem ter aparência e comportamento em diferentes cenários do Teams.</span><span class="sxs-lookup"><span data-stu-id="a4e75-171">The UI kit also includes comprehensive information about how apps should look and behave in different Teams scenarios.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a4e75-172">Obter o kit de interface do usuário (Figma)</span><span class="sxs-lookup"><span data-stu-id="a4e75-172">Get the UI kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

### <a name="microsoft-teams-ui-library"></a><span data-ttu-id="a4e75-173">Biblioteca de interface do usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="a4e75-173">Microsoft Teams UI Library</span></span>

<span data-ttu-id="a4e75-174">Exibir e testar modelos individuais de interface do usuário do Teams e componentes relacionados em seu navegador.</span><span class="sxs-lookup"><span data-stu-id="a4e75-174">View and test individual Teams UI templates and related components in your browser.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a4e75-175">Experimente a biblioteca da interface do usuário (playground)</span><span class="sxs-lookup"><span data-stu-id="a4e75-175">Try the UI library (playground)</span></span>](https://dev-int.teams.microsoft.com/storybook/main/index.html)

<span data-ttu-id="a4e75-176">Importe esses modelos e componentes relacionados diretamente ao seu projeto de aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="a4e75-176">Import these templates and related components directly into your Teams app project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a4e75-177">Obter a biblioteca da interface do usuário (GitHub)</span><span class="sxs-lookup"><span data-stu-id="a4e75-177">Get the UI library (GitHub)</span></span>](https://github.com/OfficeDev/microsoft-teams-ui-component-library)

### <a name="sample-app"></a><span data-ttu-id="a4e75-178">Exemplo de aplicativo</span><span class="sxs-lookup"><span data-stu-id="a4e75-178">Sample app</span></span>

<span data-ttu-id="a4e75-179">Instale um aplicativo de exemplo para ver como os modelos de interface do usuário são e se comportam em contextos do Teams.</span><span class="sxs-lookup"><span data-stu-id="a4e75-179">Install a sample app to see how UI templates look and behave within Teams contexts.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a4e75-180">Obter o aplicativo de exemplo (GitHub)</span><span class="sxs-lookup"><span data-stu-id="a4e75-180">Get the sample app (GitHub)</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-ui-templates/ts)

## <a name="other-resources"></a><span data-ttu-id="a4e75-181">Outros recursos</span><span class="sxs-lookup"><span data-stu-id="a4e75-181">Other resources</span></span>

<span data-ttu-id="a4e75-182">Para saber mais, experimente um dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="a4e75-182">To learn more, try one of the following resources.</span></span>

### <a name="fluent-ui-documentation"></a><span data-ttu-id="a4e75-183">Documentação da interface do usuário do Fluent</span><span class="sxs-lookup"><span data-stu-id="a4e75-183">Fluent UI documentation</span></span>

<span data-ttu-id="a4e75-184">Obter exemplos de código e detalhes de implementação para os componentes baseados na interface do usuário fluent usados para criar experiências do Teams.</span><span class="sxs-lookup"><span data-stu-id="a4e75-184">Get code samples and implementation details for the Fluent UI-based components used to build Teams experiences.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a4e75-185">Experimente componentes da interface do usuário do Teams (Fluent UI)</span><span class="sxs-lookup"><span data-stu-id="a4e75-185">Try Teams UI components (Fluent UI)</span></span>](https://fluentsite.z22.web.core.windows.net/)

### <a name="adaptive-cards-designer"></a><span data-ttu-id="a4e75-186">Designer de Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="a4e75-186">Adaptive Cards designer</span></span>

<span data-ttu-id="a4e75-187">Projete Cartões Adaptáveis em nossa ferramenta baseada na Web.</span><span class="sxs-lookup"><span data-stu-id="a4e75-187">Design Adaptive Cards in our web-based tool.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a4e75-188">Experimente o designer de Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="a4e75-188">Try the Adaptive Cards designer</span></span>](https://adaptivecards.io/designer/)
