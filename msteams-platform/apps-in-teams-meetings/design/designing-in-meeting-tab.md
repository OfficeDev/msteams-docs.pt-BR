---
title: Desenvolva uma guia na reunião
author: heath-hamilton
description: Saiba como projetar efetivamente uma guia na reunião do Microsoft Teams.
ms.author: lajanuar
ms.topic: conceptual
ms.openlocfilehash: fc10c5b60672d243ac2e330ce93b4e01c2e7a278
ms.sourcegitcommit: 64acd30eee8af5fe151e9866c13226ed3f337c72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2020
ms.locfileid: "49346669"
---
# <a name="design-an-in-meeting-tab"></a><span data-ttu-id="acac3-103">Desenvolva uma guia na reunião</span><span class="sxs-lookup"><span data-stu-id="acac3-103">Design an in-meeting tab</span></span>

<span data-ttu-id="acac3-104">A guia na reunião é uma tela para aumentar a colaboração durante as reuniões.</span><span class="sxs-lookup"><span data-stu-id="acac3-104">The in-meeting tab is a canvas for augmenting collaboration during meetings.</span></span> <span data-ttu-id="acac3-105">Com base na capacidade de guia do Teams, os participantes podem ver e interagir com o conteúdo do aplicativo em um espaço dedicado fora do estágio da reunião por meio de exibições compartilhadas ou baseadas em função.</span><span class="sxs-lookup"><span data-stu-id="acac3-105">Based on the Teams tab capability, attendees can see and interact with app content in a dedicated space outside the meeting stage through shared or role-based views.</span></span>

## <a name="use-cases"></a><span data-ttu-id="acac3-106">Casos de uso</span><span class="sxs-lookup"><span data-stu-id="acac3-106">Use cases</span></span>

<span data-ttu-id="acac3-107">As pessoas podem usar a guia na reunião para:</span><span class="sxs-lookup"><span data-stu-id="acac3-107">People might use the in-meeting tab to:</span></span>

* <span data-ttu-id="acac3-108">Fornecer feedback detalhado (por exemplo, avaliar um candidato a trabalho)</span><span class="sxs-lookup"><span data-stu-id="acac3-108">Provide detailed feedback (for example, evaluate a job candidate)</span></span>
* <span data-ttu-id="acac3-109">Criar rapidamente um item de pesquisa, pesquisa ou tarefa para os participantes da reunião</span><span class="sxs-lookup"><span data-stu-id="acac3-109">Quickly create a poll, survey, or task item for the meeting participants</span></span>
* <span data-ttu-id="acac3-110">Exibir anotações relevantes para a reunião (por exemplo, informações sobre um líder de vendas)</span><span class="sxs-lookup"><span data-stu-id="acac3-110">Display notes relevant to the meeting (for example, information about a sales lead)</span></span>

## <a name="example"></a><span data-ttu-id="acac3-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="acac3-111">Example</span></span>

<span data-ttu-id="acac3-112">O exemplo a seguir mostra a guia na reunião que exibe o conteúdo do aplicativo de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="acac3-112">The following example shows the in-meeting tab displaying survey app content.</span></span>

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-organizer-view.png" alt-text="O exemplo mostra como a guia na reunião da reunião pode parecer da perspectiva de um organizador da reunião.":::

<span data-ttu-id="acac3-114"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Consulte o cenário completo (figma)</a></span><span class="sxs-lookup"><span data-stu-id="acac3-114"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">See the full scenario (Figma)</a></span></span>

<span data-ttu-id="acac3-115"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Ver outros exemplos de exemplos de uso (figma)</a></span><span class="sxs-lookup"><span data-stu-id="acac3-115"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">See other example use cases (Figma)</a></span></span>

## <a name="anatomy"></a><span data-ttu-id="acac3-116">Anatomia</span><span class="sxs-lookup"><span data-stu-id="acac3-116">Anatomy</span></span>

<span data-ttu-id="acac3-117">A guia na reunião exibe o conteúdo do aplicativo usando as seguintes dimensões:</span><span class="sxs-lookup"><span data-stu-id="acac3-117">The in-meeting tab displays your app content using the following dimensions:</span></span>

* <span data-ttu-id="acac3-118">**Largura**: 280 pixels para a área de WebView.</span><span class="sxs-lookup"><span data-stu-id="acac3-118">**Width**: 280 pixels for the webview area.</span></span> <span data-ttu-id="acac3-119">Há 20 pixels de enchimento nos lados esquerdo e direito do WebView.</span><span class="sxs-lookup"><span data-stu-id="acac3-119">There are 20 pixels of padding on the left and right sides of the webview.</span></span>
* <span data-ttu-id="acac3-120">**Altura**: sangramento completo para a parte inferior da guia. Há 20 pixels de preenchimento entre a área da WebView e o cabeçalho da guia.</span><span class="sxs-lookup"><span data-stu-id="acac3-120">**Height**: Full bleed to the bottom of the tab. There are 20 pixels of padding between the webview area and tab header.</span></span>

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-anatomy.png" alt-text="Ilustração mostrando a anatomia da interface de usuário de uma guia na reunião da extensão de reunião." border="false":::

1. <span data-ttu-id="acac3-122">**Ícone do aplicativo**: o ponto de entrada para a guia na reunião.</span><span class="sxs-lookup"><span data-stu-id="acac3-122">**App icon**: The entry point to the in-meeting tab.</span></span>
1. <span data-ttu-id="acac3-123">**Cabeçalho**: inclui o nome da guia.</span><span class="sxs-lookup"><span data-stu-id="acac3-123">**Header**: Includes the tab name.</span></span>
1. <span data-ttu-id="acac3-124">**Nome**: o nome da instância de tabulação.</span><span class="sxs-lookup"><span data-stu-id="acac3-124">**Name**: The name of the tab instance.</span></span>
1. <span data-ttu-id="acac3-125">**Dispensar**: descarta a guia. Sempre use o ícone de fechamento superior direito em vez de uma ação no rodapé.</span><span class="sxs-lookup"><span data-stu-id="acac3-125">**Dismiss**: Dismisses the tab. Always use the upper-right close icon instead of an action in the footer.</span></span>
1. <span data-ttu-id="acac3-126">**WebView**: exibe todo o conteúdo de aplicativo de terceiros.</span><span class="sxs-lookup"><span data-stu-id="acac3-126">**Webview**: Displays all third-party app content.</span></span>

## <a name="behavior"></a><span data-ttu-id="acac3-127">Comportamento</span><span class="sxs-lookup"><span data-stu-id="acac3-127">Behavior</span></span>

### <a name="scale"></a><span data-ttu-id="acac3-128">Escala</span><span class="sxs-lookup"><span data-stu-id="acac3-128">Scale</span></span>

<span data-ttu-id="acac3-129">No momento, a largura da guia na reunião é corrigida.</span><span class="sxs-lookup"><span data-stu-id="acac3-129">Currently, the width of the in-meeting tab is fixed.</span></span>

### <a name="scrolling"></a><span data-ttu-id="acac3-130">Rolagem</span><span class="sxs-lookup"><span data-stu-id="acac3-130">Scrolling</span></span>

<span data-ttu-id="acac3-131">Veja o que saber sobre rolagem na guia na reunião:</span><span class="sxs-lookup"><span data-stu-id="acac3-131">Here's what to know about scrolling in the in-meeting tab:</span></span>

* <span data-ttu-id="acac3-132">Você só deve rolar verticalmente.</span><span class="sxs-lookup"><span data-stu-id="acac3-132">You should only be able to scroll vertically.</span></span>
* <span data-ttu-id="acac3-133">Você só pode ver o conteúdo que você rolou para (nada acima ou abaixo).</span><span class="sxs-lookup"><span data-stu-id="acac3-133">You can only see the content you've scrolled to (nothing above or below).</span></span>
* <span data-ttu-id="acac3-134">O ScrollBar é parte do conteúdo da WebView.</span><span class="sxs-lookup"><span data-stu-id="acac3-134">The scrollbar is part of the webview content.</span></span>

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-scroll.png" alt-text="Ilustração que mostra como a rolagem do conteúdo da WebView na guia na reunião funciona." border="false":::

### <a name="navigation"></a><span data-ttu-id="acac3-136">Navegação</span><span class="sxs-lookup"><span data-stu-id="acac3-136">Navigation</span></span>

<span data-ttu-id="acac3-137">Para cenários com camadas de navegação ou conteúdo pesado, recomendamos permitir que os usuários naveguem para uma camada secundária.</span><span class="sxs-lookup"><span data-stu-id="acac3-137">For scenarios with navigation layers or heavy content, we recommend allowing users to navigate to a secondary layer.</span></span> <span data-ttu-id="acac3-138">Os usuários devem ser capazes de voltar para a camada anterior.</span><span class="sxs-lookup"><span data-stu-id="acac3-138">Users must be able to go back to the previous layer.</span></span>

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-nav.png" alt-text="Ilustração mostrando como funciona a navegação para uma camada secundária na guia na reunião." border="false":::

## <a name="components"></a><span data-ttu-id="acac3-140">Componentes</span><span class="sxs-lookup"><span data-stu-id="acac3-140">Components</span></span>

<span data-ttu-id="acac3-141">As guias na reunião são criadas principalmente com os seguintes <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">componentes de interface do usuário (figma)</a>, que se baseiam no <a href="https://fluentsite.z22.web.core.windows.net/" target="_blank">sistema de design fluente</a>.</span><span class="sxs-lookup"><span data-stu-id="acac3-141">In-meeting tabs are built primarily with the following <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">UI components (Figma)</a>, which are based on the <a href="https://fluentsite.z22.web.core.windows.net/" target="_blank">Fluent Design System</a>.</span></span>

<span data-ttu-id="acac3-142">Componente</span><span class="sxs-lookup"><span data-stu-id="acac3-142">Component</span></span> | <span data-ttu-id="acac3-143">Diretrizes</span><span class="sxs-lookup"><span data-stu-id="acac3-143">Guidelines</span></span> | <span data-ttu-id="acac3-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="acac3-144">Example</span></span>
 - | - | -
<span data-ttu-id="acac3-145">Botão</span><span class="sxs-lookup"><span data-stu-id="acac3-145">Button</span></span> | <span data-ttu-id="acac3-146">Os botões principal e secundário podem ser médios ou pequenos</span><span class="sxs-lookup"><span data-stu-id="acac3-146">Primary and secondary buttons can be medium or small</span></span> | <span data-ttu-id="acac3-147">Enviar uma resposta</span><span class="sxs-lookup"><span data-stu-id="acac3-147">Send a response</span></span>
<span data-ttu-id="acac3-148">Input</span><span class="sxs-lookup"><span data-stu-id="acac3-148">Input</span></span> | <span data-ttu-id="acac3-149">Campo para Brief entradas do usuário.</span><span class="sxs-lookup"><span data-stu-id="acac3-149">Field for brief user input.</span></span> <span data-ttu-id="acac3-150">O texto do rótulo pode incluir um ícone</span><span class="sxs-lookup"><span data-stu-id="acac3-150">Label text can include an icon</span></span>  | <span data-ttu-id="acac3-151">Inserir comentários</span><span class="sxs-lookup"><span data-stu-id="acac3-151">Enter feedback</span></span>
<span data-ttu-id="acac3-152">Lista suspensa</span><span class="sxs-lookup"><span data-stu-id="acac3-152">Dropdown</span></span> | <span data-ttu-id="acac3-153">Selecione uma ou mais opções de uma lista.</span><span class="sxs-lookup"><span data-stu-id="acac3-153">Select one or more options from a list.</span></span> <span data-ttu-id="acac3-154">Pode incluir recursos de pesquisa e seleção múltipla</span><span class="sxs-lookup"><span data-stu-id="acac3-154">Can include search and multi-selection features</span></span> | <span data-ttu-id="acac3-155">Escolha um idioma</span><span class="sxs-lookup"><span data-stu-id="acac3-155">Choose a language</span></span>
<span data-ttu-id="acac3-156">Controles de seleção</span><span class="sxs-lookup"><span data-stu-id="acac3-156">Selection controls</span></span> | <span data-ttu-id="acac3-157">Use caixas de seleção para várias opções ou botões de opção e alterna para opções individuais.</span><span class="sxs-lookup"><span data-stu-id="acac3-157">Use checkboxes for multiple choices or radio buttons and toggles for single choices.</span></span> <span data-ttu-id="acac3-158">Para seleções mais detalhadas, use um controle deslizante</span><span class="sxs-lookup"><span data-stu-id="acac3-158">For more detailed selections, use a slider</span></span> | <span data-ttu-id="acac3-159">Votar em uma votação</span><span class="sxs-lookup"><span data-stu-id="acac3-159">Vote in a poll</span></span>
<span data-ttu-id="acac3-160">Alertas</span><span class="sxs-lookup"><span data-stu-id="acac3-160">Alerts</span></span> | <span data-ttu-id="acac3-161">Independentemente de exibir uma mensagem urgente, estado de erro ou aviso, a mensagem deve ser curta e não interromperá a tarefa atual do usuário</span><span class="sxs-lookup"><span data-stu-id="acac3-161">Whether displaying an urgent message, error state, or warning, the message should be short and won't interrupt the user's current task</span></span> | <span data-ttu-id="acac3-162">Exibir problema ao enviar uma resposta</span><span class="sxs-lookup"><span data-stu-id="acac3-162">Display issue when submitting a response</span></span>

## <a name="theming"></a><span data-ttu-id="acac3-163">Temas</span><span class="sxs-lookup"><span data-stu-id="acac3-163">Theming</span></span>

### <a name="colors"></a><span data-ttu-id="acac3-164">Cores</span><span class="sxs-lookup"><span data-stu-id="acac3-164">Colors</span></span>

<span data-ttu-id="acac3-165">Use o <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">esquema de cores recomendado (figma)</a> para planos de fundo, primeiro plano e transmitir Estados.</span><span class="sxs-lookup"><span data-stu-id="acac3-165">Use the <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">recommended color scheme (Figma)</a> for backgrounds, foregrounds, and conveying states.</span></span>

### <a name="typography"></a><span data-ttu-id="acac3-166">Tipografia</span><span class="sxs-lookup"><span data-stu-id="acac3-166">Typography</span></span>

<span data-ttu-id="acac3-167">Use os <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">tamanhos de fonte e pesos (figma) recomendados</a> para títulos, corpo de texto e texto de metadados.</span><span class="sxs-lookup"><span data-stu-id="acac3-167">Use the <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">recommended font sizes and weights (Figma)</a> for titles, body text, and metadata text.</span></span>

## <a name="best-practices"></a><span data-ttu-id="acac3-168">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="acac3-168">Best practices</span></span>

### <a name="responsiveness"></a><span data-ttu-id="acac3-169">Responsividade</span><span class="sxs-lookup"><span data-stu-id="acac3-169">Responsiveness</span></span>

<span data-ttu-id="acac3-170">Os layouts de guia na reunião devem poder ser dimensionados para vários tamanhos.</span><span class="sxs-lookup"><span data-stu-id="acac3-170">In-meeting tab layouts should be able to scale to various sizes.</span></span> <span data-ttu-id="acac3-171">Considere como a guia será dimensionada e assumir forma antes, durante e depois da reunião.</span><span class="sxs-lookup"><span data-stu-id="acac3-171">Consider how the tab will scale and take shape before, during, and after the meeting.</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-before-meeting.png" alt-text="Ilustração mostrando que o conteúdo da guia na reunião parece com uma guia de tela inteira antes e depois de uma reunião." border="false":::

#### <a name="before-the-meeting"></a><span data-ttu-id="acac3-173">Antes da reunião</span><span class="sxs-lookup"><span data-stu-id="acac3-173">Before the meeting</span></span>

<span data-ttu-id="acac3-174">Certifique-se de que o layout de Tabulação pode se adaptar a um layout à direita ou à esquerda para idiomas diferentes e que os controles se movem para os locais corretos.</span><span class="sxs-lookup"><span data-stu-id="acac3-174">Make sure your tab layout can adapt to a right or left layout for different languages and that controls move to the correct locations.</span></span> <span data-ttu-id="acac3-175">(Os layouts antes da reunião também podem ser aplicados aos layouts pós-reunião.)</span><span class="sxs-lookup"><span data-stu-id="acac3-175">(Pre-meeting layouts can also apply to post-meeting layouts.)</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-during-meeting.png" alt-text="Ilustração que mostra como o conteúdo da guia de pré-reunião é condensado para a guia na reunião durante uma reunião." border="false":::

#### <a name="during-the-meeting"></a><span data-ttu-id="acac3-177">Durante a reunião</span><span class="sxs-lookup"><span data-stu-id="acac3-177">During the meeting</span></span>

<span data-ttu-id="acac3-178">O conteúdo da guia ajusta o layout e o local da guia na reunião.</span><span class="sxs-lookup"><span data-stu-id="acac3-178">Tab content adjusts to the in-meeting tab layout and location.</span></span>

   :::column-end:::
:::row-end:::

### <a name="theming"></a><span data-ttu-id="acac3-179">Temas</span><span class="sxs-lookup"><span data-stu-id="acac3-179">Theming</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-theming-do.png" alt-text="Ilustração mostrando como você deve projetar a guia na reunião para o tema escuro usado em reuniões do teams." border="false":::

#### <a name="do-design-for-a-dark-theme"></a><span data-ttu-id="acac3-181">Fazer: design para um tema escuro</span><span class="sxs-lookup"><span data-stu-id="acac3-181">Do: Design for a dark theme</span></span>

<span data-ttu-id="acac3-182">As reuniões do teams são otimizadas para o modo escuro para ajudar a reduzir o ruído visual e cognitiva, para que os usuários possam se concentrar na discussão e no conteúdo compartilhado.</span><span class="sxs-lookup"><span data-stu-id="acac3-182">Teams meetings are optimized for dark mode to help reduce visual and cognitive noise so users can focus on the discussion and shared content.</span></span> <span data-ttu-id="acac3-183">A guia na reunião deve aplicar um tema escuro e deve seguir as diretrizes.</span><span class="sxs-lookup"><span data-stu-id="acac3-183">The in-meeting tab should apply a dark theme and should follow theming guidelines.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-theming-dont.png" alt-text="Ilustração que mostra que você não deve usar cores que não conduzam ao tema escuro da equipe." border="false":::

#### <a name="dont-use-unfamiliar-colors"></a><span data-ttu-id="acac3-185">Não: usar cores desconhecidas</span><span class="sxs-lookup"><span data-stu-id="acac3-185">Don't: Use unfamiliar colors</span></span>

<span data-ttu-id="acac3-186">As cores que em conflito com o ambiente de reunião podem ser discadas e parecer menos nativas para o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="acac3-186">Colors that clash with the meeting environment may be distracting and appear less native to Teams.</span></span>

   :::column-end:::
:::row-end:::

### <a name="scrolling"></a><span data-ttu-id="acac3-187">Rolagem</span><span class="sxs-lookup"><span data-stu-id="acac3-187">Scrolling</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-scroll-do.png" alt-text="Ilustração mostrando você só deve permitir rolagem vertical na guia na reunião." border="false":::

#### <a name="do-scroll-vertically"></a><span data-ttu-id="acac3-189">Fazer: rolar verticalmente</span><span class="sxs-lookup"><span data-stu-id="acac3-189">Do: Scroll vertically</span></span>

<span data-ttu-id="acac3-190">Os usuários antecipam a rolagem vertical no Teams (e em outros lugares).</span><span class="sxs-lookup"><span data-stu-id="acac3-190">Users anticipate vertical scrolling in Teams (and elsewhere).</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-scroll-dont.png" alt-text="Ilustração mostrando como mostrar você não deve permitir rolagem horizontal na guia na reunião." border="false":::

#### <a name="dont-scroll-horizontally"></a><span data-ttu-id="acac3-192">Não: rolar horizontalmente</span><span class="sxs-lookup"><span data-stu-id="acac3-192">Don't: Scroll horizontally</span></span>

<span data-ttu-id="acac3-193">A rolagem horizontal não é um comportamento esperado no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="acac3-193">Horizontal scrolling isn’t an expected behavior in Teams.</span></span> <span data-ttu-id="acac3-194">Outras telas no ambiente de reunião rolam verticalmente.</span><span class="sxs-lookup"><span data-stu-id="acac3-194">Other canvases in the meeting environment scroll vertically.</span></span>

   :::column-end:::
:::row-end:::

### <a name="layout"></a><span data-ttu-id="acac3-195">Layout</span><span class="sxs-lookup"><span data-stu-id="acac3-195">Layout</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-layout-do.png" alt-text="Ilustração mostrando o layout recomendado de uma única coluna na guia na reunião." border="false":::

#### <a name="do-single-columns"></a><span data-ttu-id="acac3-197">Fazer: colunas únicas</span><span class="sxs-lookup"><span data-stu-id="acac3-197">Do: Single columns</span></span>

<span data-ttu-id="acac3-198">Dada a natureza estreita da guia na reunião, é altamente recomendável exibir o conteúdo em uma única coluna.</span><span class="sxs-lookup"><span data-stu-id="acac3-198">Given the in-meeting tab’s narrow nature, we strongly recommend displaying the contents in a single column.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-layout-dont.png" alt-text="Ilustração que mostra como um layout de duas colunas na guia na reunião não é ideal." border="false":::

#### <a name="dont-multiple-columns"></a><span data-ttu-id="acac3-200">Não: várias colunas</span><span class="sxs-lookup"><span data-stu-id="acac3-200">Don't: Multiple columns</span></span>

<span data-ttu-id="acac3-201">Devido ao espaço limitado da guia na reunião, layouts com mais de uma coluna não são recomendados.</span><span class="sxs-lookup"><span data-stu-id="acac3-201">Due to the limited space of the in-meeting tab, layouts with more than one column aren’t recommended.</span></span>

   :::column-end:::
:::row-end:::

### <a name="navigation"></a><span data-ttu-id="acac3-202">Navegação</span><span class="sxs-lookup"><span data-stu-id="acac3-202">Navigation</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-nav-do.png" alt-text="Ilustração mostrar você sempre deve fornecer um botão voltar se seu aplicativo de guia na reunião tiver mais de uma camada de navegação." border="false":::

#### <a name="do-have-a-back-button"></a><span data-ttu-id="acac3-204">Fazer: ter um botão voltar</span><span class="sxs-lookup"><span data-stu-id="acac3-204">Do: Have a back button</span></span>

<span data-ttu-id="acac3-205">Se você tiver mais de uma camada de navegação, os usuários devem ser capazes de retornar ao modo de exibição anterior.</span><span class="sxs-lookup"><span data-stu-id="acac3-205">If you have more than one layer of navigation, users must be able to go back to their previous view.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-nav-dont.png" alt-text="Ilustração mostrando que adicionar outro botão fechar na guia na reunião para navegação é redundante e pode causar problemas." border="false":::

#### <a name="dont-include-another-close-button"></a><span data-ttu-id="acac3-207">Não: incluir outro botão fechar</span><span class="sxs-lookup"><span data-stu-id="acac3-207">Don't: Include another close button</span></span>

<span data-ttu-id="acac3-208">O fornecimento de uma opção para fechar o conteúdo da guia na reunião pode causar problemas, já que já existe um botão fechar no cabeçalho para ignorar a guia na reunião em si.</span><span class="sxs-lookup"><span data-stu-id="acac3-208">Providing an option to close in-meeting tab content may cause issues since there’s already a close button in the header to dismiss the in-meeting tab itself.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-nav-caution.png" alt-text="Ilustração mostrando que você precisa ter cuidado ao usar as modalidades (ou seja, módulos de tarefas) na guia na reunião, de acordo com o espaço limitado." border="false":::

#### <a name="caution-using-dialogs-in-a-narrow-space"></a><span data-ttu-id="acac3-210">Cuidado: usar caixas de diálogo em um espaço estreito</span><span class="sxs-lookup"><span data-stu-id="acac3-210">Caution: Using dialogs in a narrow space</span></span>

<span data-ttu-id="acac3-211">Caixas de diálogo, como módulos de tarefas, na guia já restrita na reunião podem quebrar e obscurecer o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="acac3-211">Dialogs, such as task modules, in the already narrow in-meeting tab might wrap and obscure the content.</span></span>

   :::column-end:::
:::row-end:::

## <a name="accessibility"></a><span data-ttu-id="acac3-212">Acessibilidade</span><span class="sxs-lookup"><span data-stu-id="acac3-212">Accessibility</span></span>

<span data-ttu-id="acac3-213">Para obter informações sobre acessibilidade, consulte <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">figma</a>.</span><span class="sxs-lookup"><span data-stu-id="acac3-213">For information on accessibility, see <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Figma</a>.</span></span>

## <a name="resources"></a><span data-ttu-id="acac3-214">Recursos</span><span class="sxs-lookup"><span data-stu-id="acac3-214">Resources</span></span>

* <span data-ttu-id="acac3-215"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Arquivo de extensões de reunião do Microsoft Teams figma</a></span><span class="sxs-lookup"><span data-stu-id="acac3-215"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Microsoft Teams meeting extensions Figma file</a></span></span>
* [<span data-ttu-id="acac3-216">Diretrizes de design de guias</span><span class="sxs-lookup"><span data-stu-id="acac3-216">Tabs design guidelines</span></span>](../../tabs/design/tabs.md)
* [<span data-ttu-id="acac3-217">Diretrizes de design de guias para dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="acac3-217">Tabs design guidelines for mobile</span></span>](../../tabs/design/tabs-mobile.md)

## <a name="validate-your-design"></a><span data-ttu-id="acac3-218">Validar o design</span><span class="sxs-lookup"><span data-stu-id="acac3-218">Validate your design</span></span>

<span data-ttu-id="acac3-219">Se você planeja publicar seu aplicativo no AppSource, você deve compreender os problemas de design que geralmente causam falha nos aplicativos durante o envio.</span><span class="sxs-lookup"><span data-stu-id="acac3-219">If you plan to publish your app to AppSource, you should understand the design issues that commonly cause apps to fail during submission.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="acac3-220">Verificar diretrizes de validação de design</span><span class="sxs-lookup"><span data-stu-id="acac3-220">Check design validation guidelines</span></span>](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
