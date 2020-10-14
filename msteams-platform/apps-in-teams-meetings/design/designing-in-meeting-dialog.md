---
title: Desenvolva uma conversa na reunião
author: heath-hamilton
description: Saiba como projetar com eficiência uma caixa de diálogo de reunião do Microsoft Teams.
ms.author: lajanuar
ms.topic: conceptual
ms.openlocfilehash: f2ac0df3ce28293d9e3f61f45dd2d460dc01f2e9
ms.sourcegitcommit: d61f14053fc695bc1956bf50e83956613c19ccca
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/13/2020
ms.locfileid: "48452670"
---
# <a name="design-an-in-meeting-dialog"></a><span data-ttu-id="678e7-103">Desenvolva uma conversa na reunião</span><span class="sxs-lookup"><span data-stu-id="678e7-103">Design an in-meeting dialog</span></span>

<span data-ttu-id="678e7-104">Caixas de diálogo na reunião exibidas no estágio de reunião do teams.</span><span class="sxs-lookup"><span data-stu-id="678e7-104">In-meeting dialogs display on the Teams meeting stage.</span></span> <span data-ttu-id="678e7-105">Eles exigem a atenção, a confirmação ou a interação de um usuário, mas são sutis e não interrompem a reunião.</span><span class="sxs-lookup"><span data-stu-id="678e7-105">They require a user's attention, confirmation, or interaction but are subtle and don't interrupt the meeting.</span></span>

## <a name="use-cases"></a><span data-ttu-id="678e7-106">Casos de uso</span><span class="sxs-lookup"><span data-stu-id="678e7-106">Use cases</span></span>

<span data-ttu-id="678e7-107">As caixas de diálogo na reunião são acionadas por um usuário (como o organizador da reunião) que pode querer que os participantes:</span><span class="sxs-lookup"><span data-stu-id="678e7-107">In-meeting dialogs are triggered by a user (such as the meeting organizer) who might want participants to:</span></span>

* <span data-ttu-id="678e7-108">Fornecer breve feedback</span><span class="sxs-lookup"><span data-stu-id="678e7-108">Provide brief feedback</span></span>
* <span data-ttu-id="678e7-109">Faça uma rápida pesquisa ou sondagem</span><span class="sxs-lookup"><span data-stu-id="678e7-109">Take a short survey or poll</span></span>
* <span data-ttu-id="678e7-110">Enviar aprovações</span><span class="sxs-lookup"><span data-stu-id="678e7-110">Submit approvals</span></span>
* <span data-ttu-id="678e7-111">Receber lembretes</span><span class="sxs-lookup"><span data-stu-id="678e7-111">Get reminders</span></span>

## <a name="example"></a><span data-ttu-id="678e7-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="678e7-112">Example</span></span>

<span data-ttu-id="678e7-113">O exemplo a seguir mostra o que a caixa de diálogo de reunião pode parecer da perspectiva de um participante da reunião.</span><span class="sxs-lookup"><span data-stu-id="678e7-113">The following example shows what the in-meeting dialog might look like from a meeting participant's perspective.</span></span> <span data-ttu-id="678e7-114">Como você pode ver, o conteúdo e a tarefa são leves.</span><span class="sxs-lookup"><span data-stu-id="678e7-114">As you can see, the content and task are lightweight.</span></span>

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-participant-view.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião.":::

<span data-ttu-id="678e7-116"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Consulte o cenário completo (figma)</a></span><span class="sxs-lookup"><span data-stu-id="678e7-116"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">See the full scenario (Figma)</a></span></span>

<span data-ttu-id="678e7-117"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Ver outros exemplos de exemplos de uso (figma)</a></span><span class="sxs-lookup"><span data-stu-id="678e7-117"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">See other example use cases (Figma)</a></span></span>

## <a name="anatomy"></a><span data-ttu-id="678e7-118">Anatomia</span><span class="sxs-lookup"><span data-stu-id="678e7-118">Anatomy</span></span>

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-anatomy.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

1. <span data-ttu-id="678e7-120">**ícone de aplicativo**</span><span class="sxs-lookup"><span data-stu-id="678e7-120">**App icon**</span></span>
1. <span data-ttu-id="678e7-121">**Nome do aplicativo**</span><span class="sxs-lookup"><span data-stu-id="678e7-121">**App name**</span></span>
1. <span data-ttu-id="678e7-122">**Cadeia de caracteres de ação**</span><span class="sxs-lookup"><span data-stu-id="678e7-122">**Action string**</span></span>
1. <span data-ttu-id="678e7-123">**Fechar ícone:** Fecha uma única caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="678e7-123">**Dismiss icon:** Closes a single dialog.</span></span> <span data-ttu-id="678e7-124">Sempre use o ícone de fechamento superior direito em vez de uma ação no rodapé.</span><span class="sxs-lookup"><span data-stu-id="678e7-124">Always use the upper-right close icon instead of an action in the footer.</span></span>
1. <span data-ttu-id="678e7-125">**WebView**: exibe todos os botões e o conteúdo do aplicativo de terceiros (botões Standard Teams recomendado).</span><span class="sxs-lookup"><span data-stu-id="678e7-125">**Webview**: Displays all third-party app content and buttons (standard Teams buttons recommended).</span></span>

### <a name="sizing"></a><span data-ttu-id="678e7-126">Size</span><span class="sxs-lookup"><span data-stu-id="678e7-126">Sizing</span></span>

<span data-ttu-id="678e7-127">As caixas de diálogo de reunião podem variar de tamanho para conta para diferentes casos de uso, mas você deve sempre manter os tamanhos de preenchimento e de componente.</span><span class="sxs-lookup"><span data-stu-id="678e7-127">In-meeting dialogs can vary in size to account for different use cases, but you must always maintain padding and component sizes.</span></span>

* <span data-ttu-id="678e7-128">**Altura**: a altura da caixa de diálogo é determinada pelo conteúdo do WebView.</span><span class="sxs-lookup"><span data-stu-id="678e7-128">**Height**: The height of the dialog is determined by the content in the webview.</span></span> <span data-ttu-id="678e7-129">A rolagem vertical assume o conteúdo que excede a altura máxima especificada.</span><span class="sxs-lookup"><span data-stu-id="678e7-129">Vertical scroll takes over for content that exceeds the maximum height you specify.</span></span>
* <span data-ttu-id="678e7-130">**Largura**: a largura do WebView é um valor absoluto dentro do intervalo especificado.</span><span class="sxs-lookup"><span data-stu-id="678e7-130">**Width**: The width of the webview is an absolute value within the range you specify.</span></span>

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-sizing.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

## <a name="behavior"></a><span data-ttu-id="678e7-132">Comportamento</span><span class="sxs-lookup"><span data-stu-id="678e7-132">Behavior</span></span>

<span data-ttu-id="678e7-133">Consulte comportamento geral da caixa de diálogo de reunião, como REST, carregando e mais, no <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">figma</a>.</span><span class="sxs-lookup"><span data-stu-id="678e7-133">See general in-meeting dialog behavior, such as rest, loading, and more, in <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Figma</a>.</span></span>

### <a name="position"></a><span data-ttu-id="678e7-134">Position</span><span class="sxs-lookup"><span data-stu-id="678e7-134">Position</span></span>

<span data-ttu-id="678e7-135">As caixas de diálogo de reunião são alinhadas no centro do estágio da reunião.</span><span class="sxs-lookup"><span data-stu-id="678e7-135">In-meeting dialogs are aligned in the center of the meeting stage.</span></span> <span data-ttu-id="678e7-136">Eles não podem ser arrastados e funcionam dentro da estrutura de notificações de nível de sistema do teams.</span><span class="sxs-lookup"><span data-stu-id="678e7-136">They can’t be dragged and work within the framework of Teams system-level notifications.</span></span>

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-position.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

### <a name="aggregation"></a><span data-ttu-id="678e7-138">Agregação</span><span class="sxs-lookup"><span data-stu-id="678e7-138">Aggregation</span></span>

<span data-ttu-id="678e7-139">Apenas uma caixa de diálogo é exibida por vez, pilha de classificação da última para a mais recente enviada para a parte inferior.</span><span class="sxs-lookup"><span data-stu-id="678e7-139">Only one dialog displays at a time, stack ranking from last to most recent sent to the bottom.</span></span> <span data-ttu-id="678e7-140">Depois que uma caixa de diálogo for resolvida ou ignorada, a próxima assumirá seu lugar.</span><span class="sxs-lookup"><span data-stu-id="678e7-140">Once a dialog is resolved or dismissed, the next one take its place.</span></span>

<span data-ttu-id="678e7-141"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Ver um exemplo (figma)</a></span><span class="sxs-lookup"><span data-stu-id="678e7-141"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">See an example (Figma)</a></span></span>

### <a name="scrolling"></a><span data-ttu-id="678e7-142">Rolagem</span><span class="sxs-lookup"><span data-stu-id="678e7-142">Scrolling</span></span>

<span data-ttu-id="678e7-143">A rolagem ocorre na parte do WebView de uma caixa de diálogo de reunião.</span><span class="sxs-lookup"><span data-stu-id="678e7-143">Scrolling occurs in the webview portion of an in-meeting dialog.</span></span> <span data-ttu-id="678e7-144">Lembre-se do seguinte sobre a rolagem:</span><span class="sxs-lookup"><span data-stu-id="678e7-144">Remember the following about scrolling:</span></span>

* <span data-ttu-id="678e7-145">Você só deve rolar verticalmente.</span><span class="sxs-lookup"><span data-stu-id="678e7-145">You should only be able to scroll vertically.</span></span>
* <span data-ttu-id="678e7-146">Você só pode ver o conteúdo que você rolou para (nada acima ou abaixo).</span><span class="sxs-lookup"><span data-stu-id="678e7-146">You can only see the content you've scrolled to (nothing above or below).</span></span>

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-scroll.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

### <a name="buttons"></a><span data-ttu-id="678e7-148">Botões</span><span class="sxs-lookup"><span data-stu-id="678e7-148">Buttons</span></span>

<span data-ttu-id="678e7-149">Os botões de diálogo na reunião fazem parte do WebView ([Veja alguns exemplos](#best-practices)).</span><span class="sxs-lookup"><span data-stu-id="678e7-149">In-meeting dialog buttons are part of the webview ([see some examples](#best-practices)).</span></span>

<span data-ttu-id="678e7-150">Ao contrário de componentes semelhantes, as caixas de diálogo de reunião são ignoradas quando um usuário seleciona um botão.</span><span class="sxs-lookup"><span data-stu-id="678e7-150">Unlike similar components, in-meeting dialogs are dismissed once a user selects a button.</span></span>

## <a name="components"></a><span data-ttu-id="678e7-151">Componentes</span><span class="sxs-lookup"><span data-stu-id="678e7-151">Components</span></span>

<span data-ttu-id="678e7-152">As caixas de diálogo na reunião são criadas principalmente com os seguintes <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">componentes de interface do usuário (figma)</a>, que se baseiam no <a href="https://fluentsite.z22.web.core.windows.net/" target="_blank">sistema de design fluente</a>.</span><span class="sxs-lookup"><span data-stu-id="678e7-152">In-meeting dialogs are built primarily with the following <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">UI components (Figma)</a>, which are based on the <a href="https://fluentsite.z22.web.core.windows.net/" target="_blank">Fluent Design System</a>.</span></span>

<span data-ttu-id="678e7-153">Componente</span><span class="sxs-lookup"><span data-stu-id="678e7-153">Component</span></span> | <span data-ttu-id="678e7-154">Diretrizes</span><span class="sxs-lookup"><span data-stu-id="678e7-154">Guidelines</span></span> | <span data-ttu-id="678e7-155">Exemplo</span><span class="sxs-lookup"><span data-stu-id="678e7-155">Example</span></span>
 - | - | -
<span data-ttu-id="678e7-156">Botão</span><span class="sxs-lookup"><span data-stu-id="678e7-156">Button</span></span> | <span data-ttu-id="678e7-157">Os botões principal e secundário podem ser médios ou pequenos</span><span class="sxs-lookup"><span data-stu-id="678e7-157">Primary and secondary buttons can be medium or small</span></span> | <span data-ttu-id="678e7-158">Enviar uma resposta</span><span class="sxs-lookup"><span data-stu-id="678e7-158">Send a response</span></span>
<span data-ttu-id="678e7-159">Input</span><span class="sxs-lookup"><span data-stu-id="678e7-159">Input</span></span> | <span data-ttu-id="678e7-160">Campo para Brief entradas do usuário.</span><span class="sxs-lookup"><span data-stu-id="678e7-160">Field for brief user input.</span></span> <span data-ttu-id="678e7-161">O texto do rótulo pode incluir um ícone</span><span class="sxs-lookup"><span data-stu-id="678e7-161">Label text can include an icon</span></span>  | <span data-ttu-id="678e7-162">Inserir comentários</span><span class="sxs-lookup"><span data-stu-id="678e7-162">Enter feedback</span></span>
<span data-ttu-id="678e7-163">Lista suspensa</span><span class="sxs-lookup"><span data-stu-id="678e7-163">Dropdown</span></span> | <span data-ttu-id="678e7-164">Selecione uma ou mais opções de uma lista.</span><span class="sxs-lookup"><span data-stu-id="678e7-164">Select one or more options from a list.</span></span> <span data-ttu-id="678e7-165">Pode incluir recursos de pesquisa e seleção múltipla</span><span class="sxs-lookup"><span data-stu-id="678e7-165">Can include search and multi-selection features</span></span> | <span data-ttu-id="678e7-166">Escolha um idioma</span><span class="sxs-lookup"><span data-stu-id="678e7-166">Choose a language</span></span>
<span data-ttu-id="678e7-167">Controles de seleção</span><span class="sxs-lookup"><span data-stu-id="678e7-167">Selection controls</span></span> | <span data-ttu-id="678e7-168">Use caixas de seleção para várias opções ou botões de opção e alterna para opções individuais.</span><span class="sxs-lookup"><span data-stu-id="678e7-168">Use checkboxes for multiple choices or radio buttons and toggles for single choices.</span></span> <span data-ttu-id="678e7-169">Para seleções mais detalhadas, use um controle deslizante</span><span class="sxs-lookup"><span data-stu-id="678e7-169">For more detailed selections, use a slider</span></span> | <span data-ttu-id="678e7-170">Votar em uma votação</span><span class="sxs-lookup"><span data-stu-id="678e7-170">Vote in a poll</span></span>
<span data-ttu-id="678e7-171">Alertas</span><span class="sxs-lookup"><span data-stu-id="678e7-171">Alerts</span></span> | <span data-ttu-id="678e7-172">Independentemente de exibir uma mensagem urgente, estado de erro ou aviso, a mensagem deve ser curta e não interromperá a tarefa atual do usuário</span><span class="sxs-lookup"><span data-stu-id="678e7-172">Whether displaying an urgent message, error state, or warning, the message should be short and won't interrupt the user's current task</span></span> | <span data-ttu-id="678e7-173">Exibir problema ao enviar uma resposta</span><span class="sxs-lookup"><span data-stu-id="678e7-173">Display issue when submitting a response</span></span>

## <a name="theming"></a><span data-ttu-id="678e7-174">Temas</span><span class="sxs-lookup"><span data-stu-id="678e7-174">Theming</span></span>

### <a name="colors"></a><span data-ttu-id="678e7-175">Cores</span><span class="sxs-lookup"><span data-stu-id="678e7-175">Colors</span></span>

<span data-ttu-id="678e7-176">Use o <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">esquema de cores recomendado (figma)</a> para planos de fundo, primeiro plano e transmitir Estados.</span><span class="sxs-lookup"><span data-stu-id="678e7-176">Use the <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">recommended color scheme (Figma)</a> for backgrounds, foregrounds, and conveying states.</span></span>

### <a name="typography"></a><span data-ttu-id="678e7-177">Tipografia</span><span class="sxs-lookup"><span data-stu-id="678e7-177">Typography</span></span>

<span data-ttu-id="678e7-178">Use os <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">tamanhos de fonte e pesos (figma) recomendados</a> para títulos, corpo de texto e texto de metadados.</span><span class="sxs-lookup"><span data-stu-id="678e7-178">Use the <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">recommended font sizes and weights (Figma)</a> for titles, body text, and metadata text.</span></span>

## <a name="best-practices"></a><span data-ttu-id="678e7-179">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="678e7-179">Best practices</span></span>

<span data-ttu-id="678e7-180">Enquanto as caixas de diálogo em reunião podem fazer chamadas mais eficazes, elas também podem derail chamadas se forem muito discretas.</span><span class="sxs-lookup"><span data-stu-id="678e7-180">While in-meeting dialogs can make calls more effective, they also can derail calls if too obtrusive.</span></span> <span data-ttu-id="678e7-181">Em geral, use as caixas de diálogo com moderação e siga estas práticas recomendadas.</span><span class="sxs-lookup"><span data-stu-id="678e7-181">In general, use the dialogs sparingly and follow these best practices.</span></span>

### <a name="navigation"></a><span data-ttu-id="678e7-182">Navegação</span><span class="sxs-lookup"><span data-stu-id="678e7-182">Navigation</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-steps-do.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

#### <a name="do-keep-it-contained"></a><span data-ttu-id="678e7-184">Fazer: manter continha</span><span class="sxs-lookup"><span data-stu-id="678e7-184">Do: Keep it contained</span></span>

<span data-ttu-id="678e7-185">Limite o conteúdo da caixa de diálogo de reunião para uma tela única, para que os usuários possam se concentrar na reunião.</span><span class="sxs-lookup"><span data-stu-id="678e7-185">Limit in-meeting dialog content to a single screen so users can focus on the meeting.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-steps-dont.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

#### <a name="dont-include-multiple-steps"></a><span data-ttu-id="678e7-187">Não: incluir várias etapas</span><span class="sxs-lookup"><span data-stu-id="678e7-187">Don't: Include multiple steps</span></span>

<span data-ttu-id="678e7-188">As caixas de diálogo de reunião não precisam exigir que os usuários naveguem pelo conteúdo.</span><span class="sxs-lookup"><span data-stu-id="678e7-188">In-meeting dialogs shouldn't require users to navigate through content.</span></span>

   :::column-end:::
:::row-end:::

### <a name="interactions"></a><span data-ttu-id="678e7-189">Interações</span><span class="sxs-lookup"><span data-stu-id="678e7-189">Interactions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-interactions-do.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-interactions-dont.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-tab-do.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

#### <a name="do-limit-number-of-interactions"></a><span data-ttu-id="678e7-193">Fazer: limitar o número de interações</span><span class="sxs-lookup"><span data-stu-id="678e7-193">Do: Limit number of interactions</span></span>

<span data-ttu-id="678e7-194">Remover conteúdo desnecessário que não ajude os usuários a realizar algo rapidamente.</span><span class="sxs-lookup"><span data-stu-id="678e7-194">Remove unnecessary content that doesn't help users accomplish something quickly.</span></span> <span data-ttu-id="678e7-195">Se você precisar de interações complexas, é altamente recomendável exibir seu conteúdo usando uma única coluna na guia na reunião.</span><span class="sxs-lookup"><span data-stu-id="678e7-195">If you need complex interactions, we strongly recommend displaying your content using a single column on the in-meeting tab instead.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-tab-dont.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

#### <a name="dont-introduce-unnecessary-elements"></a><span data-ttu-id="678e7-197">Não: apresentar elementos desnecessários</span><span class="sxs-lookup"><span data-stu-id="678e7-197">Don't: Introduce unnecessary elements</span></span>

<span data-ttu-id="678e7-198">Você pode ser capaz de criar uma única caixa de diálogo de reunião com várias interações, mas muitas podem distrair da reunião.</span><span class="sxs-lookup"><span data-stu-id="678e7-198">You may be able to design a single in-meeting dialog with multiple interactions, but too many can distract from the meeting.</span></span>

   :::column-end:::
:::row-end:::

### <a name="layout"></a><span data-ttu-id="678e7-199">Layout</span><span class="sxs-lookup"><span data-stu-id="678e7-199">Layout</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-layout-do.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

#### <a name="do-use-single-column-layouts"></a><span data-ttu-id="678e7-201">Fazer: usar layouts de uma única coluna</span><span class="sxs-lookup"><span data-stu-id="678e7-201">Do: Use single-column layouts</span></span>

<span data-ttu-id="678e7-202">Como as caixas de diálogo estão no centro do estágio da reunião, a conclusão da tarefa deve ser rápida e simples para evitar frustração do usuário.</span><span class="sxs-lookup"><span data-stu-id="678e7-202">Since the dialogs are at the center of the meeting stage, task completion should be fast and simple to avoid user frustration.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-layout-dont.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

#### <a name="dont-clutter-the-space"></a><span data-ttu-id="678e7-204">Não: desobstruir o espaço</span><span class="sxs-lookup"><span data-stu-id="678e7-204">Don't: Clutter the space</span></span>

<span data-ttu-id="678e7-205">O conteúdo denso ou muito estruturado pode ser confuso e impressionante, especialmente durante uma reunião.</span><span class="sxs-lookup"><span data-stu-id="678e7-205">Dense or overly structured content can be distracting and overwhelming, especially during a meeting.</span></span>

   :::column-end:::
:::row-end:::

### <a name="size"></a><span data-ttu-id="678e7-206">Size</span><span class="sxs-lookup"><span data-stu-id="678e7-206">Size</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-size-do.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

#### <a name="do-keep-it-consistent"></a><span data-ttu-id="678e7-208">Fazer: manter consistente</span><span class="sxs-lookup"><span data-stu-id="678e7-208">Do: Keep it consistent</span></span>

<span data-ttu-id="678e7-209">Isso é importante porque as caixas de diálogo na reunião sempre são exibidas no mesmo local.</span><span class="sxs-lookup"><span data-stu-id="678e7-209">This is important because in-meeting dialogs always display in the same location.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-size-dont.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

#### <a name="dont-always-fit-to-the-content"></a><span data-ttu-id="678e7-211">Não: sempre se ajusta ao conteúdo</span><span class="sxs-lookup"><span data-stu-id="678e7-211">Don't: Always fit to the content</span></span>

<span data-ttu-id="678e7-212">Você pode estar tentando evitar a rolagem horizontal, mas vários tamanhos de diálogo na reunião no mesmo aplicativo são uma experiência inconsistente.</span><span class="sxs-lookup"><span data-stu-id="678e7-212">You may be trying to avoid horizontal scrolling, but multiple in-meeting dialog sizes within the same app is an inconsistent experience.</span></span>

   :::column-end:::
:::row-end:::

### <a name="controls"></a><span data-ttu-id="678e7-213">Controles</span><span class="sxs-lookup"><span data-stu-id="678e7-213">Controls</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-controls-do.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

#### <a name="do-right-align-the-primary-action"></a><span data-ttu-id="678e7-215">Fazer: alinhar à direita a ação principal</span><span class="sxs-lookup"><span data-stu-id="678e7-215">Do: Right align the primary action</span></span>

<span data-ttu-id="678e7-216">É recomendável posicionar a ação mais visualmente pesada para a localização mais à direita.</span><span class="sxs-lookup"><span data-stu-id="678e7-216">We recommend positioning the most visually heavy action to the right-most location.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-controls-dont.png" alt-text="O exemplo mostra como a caixa de diálogo de reunião pode se parecer com a perspectiva de um participante da reunião." border="false":::

#### <a name="dont-left-or-center-align-actions"></a><span data-ttu-id="678e7-218">Não: alinhar ações à esquerda ou ao centro</span><span class="sxs-lookup"><span data-stu-id="678e7-218">Don't: Left or center align actions</span></span>

<span data-ttu-id="678e7-219">Isso se desvia do padrão da equipe padrão para o posicionamento de controle em uma caixa de diálogo e pode entrar em conflito com uma caixa de diálogo atrás da parte superior.</span><span class="sxs-lookup"><span data-stu-id="678e7-219">This deviates from the standard Teams pattern for control placement in a dialog and may conflict with a dialog behind the top one.</span></span>

   :::column-end:::
:::row-end:::

## <a name="accessibility"></a><span data-ttu-id="678e7-220">Acessibilidade</span><span class="sxs-lookup"><span data-stu-id="678e7-220">Accessibility</span></span>

<span data-ttu-id="678e7-221">Para obter informações sobre acessibilidade, consulte <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">figma</a>.</span><span class="sxs-lookup"><span data-stu-id="678e7-221">For information on accessibility, see <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Figma</a>.</span></span>

## <a name="resources"></a><span data-ttu-id="678e7-222">Recursos</span><span class="sxs-lookup"><span data-stu-id="678e7-222">Resources</span></span>

* <span data-ttu-id="678e7-223"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Arquivo de extensões de reunião do Microsoft Teams figma</a></span><span class="sxs-lookup"><span data-stu-id="678e7-223"><a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Microsoft Teams meeting extensions Figma file</a></span></span>

## <a name="validate-your-design"></a><span data-ttu-id="678e7-224">Validar o design</span><span class="sxs-lookup"><span data-stu-id="678e7-224">Validate your design</span></span>

<span data-ttu-id="678e7-225">Se você planeja publicar seu aplicativo no AppSource, você deve compreender os problemas de design que geralmente causam falha nos aplicativos durante o envio.</span><span class="sxs-lookup"><span data-stu-id="678e7-225">If you plan to publish your app to AppSource, you should understand the design issues that commonly cause apps to fail during submission.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="678e7-226">Verificar diretrizes de validação de design</span><span class="sxs-lookup"><span data-stu-id="678e7-226">Check design validation guidelines</span></span>](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines)
