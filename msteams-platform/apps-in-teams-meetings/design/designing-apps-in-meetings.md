---
title: Projetando sua extensão de reunião
author: heath-hamilton
description: Saiba como projetar aplicativos em reuniões Teams e obter o kit Microsoft Teams interface do usuário.
ms.author: lajanuar
localization_priority: Normal
ms.topic: conceptual
ms.openlocfilehash: 0a888c333305e9caafcd0bac0e5549bf08ead424
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566023"
---
# <a name="designing-your-microsoft-teams-meeting-extension"></a><span data-ttu-id="a1f9e-103">Projetando sua extensão Microsoft Teams reunião</span><span class="sxs-lookup"><span data-stu-id="a1f9e-103">Designing your Microsoft Teams meeting extension</span></span>

<span data-ttu-id="a1f9e-104">Você pode criar aplicativos para tornar as reuniões mais produtivas.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-104">You can create apps to make meetings more productive.</span></span> <span data-ttu-id="a1f9e-105">Por exemplo, peça que as pessoas concluam uma pesquisa durante uma chamada ou enviem um lembrete rápido que não interrompa o fluxo da reunião.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-105">For example, ask people to complete a survey during a call or send a quick reminder that doesn’t interrupt the flow of the meeting.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="a1f9e-106">Kit de Interface do Usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="a1f9e-106">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="a1f9e-107">Você pode encontrar diretrizes de design mais abrangentes, incluindo elementos que você pode obter e modificar conforme necessário, no Kit de interface do usuário Microsoft Teams usuário.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-107">You can find more comprehensive design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a1f9e-108">Obtenha o Kit de Interface do Usuário do Microsoft Teams (Figma)</span><span class="sxs-lookup"><span data-stu-id="a1f9e-108">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-meeting-extension"></a><span data-ttu-id="a1f9e-109">Adicionar uma extensão de reunião</span><span class="sxs-lookup"><span data-stu-id="a1f9e-109">Add a meeting extension</span></span>

<span data-ttu-id="a1f9e-110">Você pode adicionar uma extensão de reunião antes e durante as reuniões.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-110">You can add a meeting extension before and during meetings.</span></span> <span data-ttu-id="a1f9e-111">Você também pode adicionar um aplicativo para uma reunião específica diretamente do Teams store (AppSource).</span><span class="sxs-lookup"><span data-stu-id="a1f9e-111">You also can add an app for a specific meeting directly from the Teams store (AppSource).</span></span>

### <a name="add-before-a-meeting"></a><span data-ttu-id="a1f9e-112">Adicionar antes de uma reunião</span><span class="sxs-lookup"><span data-stu-id="a1f9e-112">Add before a meeting</span></span>

<span data-ttu-id="a1f9e-113">Nos detalhes da reunião, selecione **Adicionar uma guia +** para abrir o flyout do aplicativo e encontrar aplicativos otimizados para reuniões.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-113">In the meeting details, select **Add a tab +** to open the app flyout and find apps optimized for meetings.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/add-before-meeting.png" alt-text="Exemplo mostra como adicionar uma extensão de reunião antes de uma reunião." border="false":::

### <a name="add-during-a-meeting"></a><span data-ttu-id="a1f9e-115">Adicionar durante uma reunião</span><span class="sxs-lookup"><span data-stu-id="a1f9e-115">Add during a meeting</span></span>

Em uma reunião, selecione **Mais** :::image type="icon" source="../../assets/icons/teams-client-more.png":::  >  **Adicionar um aplicativo** e escolha o aplicativo que você deseja.

:::image type="content" source="../../assets/images/apps-in-meetings/add-during-meeting.png" alt-text="Exemplo mostra como adicionar uma extensão de reunião durante uma reunião." border="false":::

## <a name="before-a-meeting"></a><span data-ttu-id="a1f9e-118">Antes de uma reunião</span><span class="sxs-lookup"><span data-stu-id="a1f9e-118">Before a meeting</span></span>

<span data-ttu-id="a1f9e-119">Antes da reunião, você pode adicionar conteúdo na guia. O exemplo a seguir mostra uma pergunta de rascunho de pesquisa que as pessoas responderão durante a chamada.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-119">Prior to your meeting, you can add content in the tab. The following example shows a draft survey question that people will answer during the call.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/before-meeting-tab.png" alt-text="Exemplo mostra como o conteúdo do aplicativo nos detalhes da reunião antes de uma chamada." border="false":::

### <a name="anatomy-meeting-tab-before-and-after-meetings"></a><span data-ttu-id="a1f9e-121">Anatomia: guia Reunião (antes e depois das reuniões)</span><span class="sxs-lookup"><span data-stu-id="a1f9e-121">Anatomy: Meeting tab (before and after meetings)</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/meeting-details-tab-anatomy.png" alt-text="Exemplo mostra a anatomia estrutural de uma guia de reunião antes e depois de uma reunião." border="false":::

|<span data-ttu-id="a1f9e-123">Contador</span><span class="sxs-lookup"><span data-stu-id="a1f9e-123">Counter</span></span>|<span data-ttu-id="a1f9e-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="a1f9e-124">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="a1f9e-125">1</span><span class="sxs-lookup"><span data-stu-id="a1f9e-125">1</span></span>|<span data-ttu-id="a1f9e-126">**Nome da guia**: Rótulo de navegação para sua guia.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-126">**Tab name**: Navigation label for your tab.</span></span>|
|<span data-ttu-id="a1f9e-127">2</span><span class="sxs-lookup"><span data-stu-id="a1f9e-127">2</span></span>|<span data-ttu-id="a1f9e-128">**Estouro da** guia : abre ações de guia, como renomear e remover.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-128">**Tab overflow**: Opens tab actions, such as rename and remove.</span></span>|
|<span data-ttu-id="a1f9e-129">3</span><span class="sxs-lookup"><span data-stu-id="a1f9e-129">3</span></span>|<span data-ttu-id="a1f9e-130">**iframe**: exibe o conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-130">**iframe**: Displays your app content.</span></span>|

### <a name="designing-with-ui-templates"></a><span data-ttu-id="a1f9e-131">Projetando com modelos de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="a1f9e-131">Designing with UI templates</span></span>

<span data-ttu-id="a1f9e-132">Use um dos seguintes modelos Teams de interface do usuário para ajudar a projetar sua guia de reunião:</span><span class="sxs-lookup"><span data-stu-id="a1f9e-132">Use one of the following Teams UI templates to help design your meeting tab:</span></span>

* <span data-ttu-id="a1f9e-133">[Lista](../../concepts/design/design-teams-app-ui-templates.md#list): as listas podem exibir itens relacionados em um formato digitalizável e permitir que os usuários tomem ações em uma lista inteira ou itens individuais.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-133">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="a1f9e-134">[Quadro de](../../concepts/design/design-teams-app-ui-templates.md#task-board)tarefas : um quadro de tarefas, às vezes chamado de quadro kanban ou faixas de nadador, é uma coleção de cartões frequentemente usada para rastrear o status de itens de trabalho ou tíquetes.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-134">[Task board](../../concepts/design/design-teams-app-ui-templates.md#task-board): A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span>
* <span data-ttu-id="a1f9e-135">[Painel](../../concepts/design/design-teams-app-ui-templates.md#dashboard): um painel é uma tela que contém vários cartões que fornecem uma visão geral dos dados ou conteúdo.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-135">[Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): A dashboard is a canvas containing multiple cards that provide an overview of data or content.</span></span>
* <span data-ttu-id="a1f9e-136">[Formulário](../../concepts/design/design-teams-app-ui-templates.md#form): Os formulários são para coletar, validar e enviar entrada do usuário de forma estruturada.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-136">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="a1f9e-137">[Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): o modelo de estado vazio pode ser usado para muitos cenários, incluindo entrar, experiências de primeira executar, mensagens de erro e muito mais.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-137">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>
* <span data-ttu-id="a1f9e-138">[Navegação à esquerda](../../concepts/design/design-teams-app-ui-templates.md#left-nav): O modelo de navegação à esquerda pode ajudar se sua guia exigir alguma navegação.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-138">[Left nav](../../concepts/design/design-teams-app-ui-templates.md#left-nav): The left nav template can help if your tab requires some navigation.</span></span> <span data-ttu-id="a1f9e-139">Em geral, você deve manter a navegação de tabulação no mínimo.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-139">In general, you should keep tab navigation to a minimum.</span></span>

## <a name="use-an-in-meeting-tab"></a><span data-ttu-id="a1f9e-140">Usar uma guia em reunião</span><span class="sxs-lookup"><span data-stu-id="a1f9e-140">Use an in-meeting tab</span></span>

<span data-ttu-id="a1f9e-141">A guia na reunião é uma tela para aumentar a colaboração durante as reuniões.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-141">The in-meeting tab is a canvas for augmenting collaboration during meetings.</span></span> <span data-ttu-id="a1f9e-142">Os participantes podem ver e interagir com o conteúdo do aplicativo em um espaço dedicado fora do estágio de reunião por meio de exibições compartilhadas ou baseadas em função.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-142">Attendees can see and interact with app content in a dedicated space outside the meeting stage through shared or role-based views.</span></span>

### <a name="use-cases"></a><span data-ttu-id="a1f9e-143">Casos de uso</span><span class="sxs-lookup"><span data-stu-id="a1f9e-143">Use cases</span></span>

<span data-ttu-id="a1f9e-144">As pessoas podem usar a guia na reunião para:</span><span class="sxs-lookup"><span data-stu-id="a1f9e-144">People might use the in-meeting tab to:</span></span>

* <span data-ttu-id="a1f9e-145">Forneça comentários detalhados.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-145">Provide detailed feedback.</span></span> <span data-ttu-id="a1f9e-146">Por exemplo, avalie um candidato a trabalho.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-146">For example, evaluate a job candidate.</span></span>
* <span data-ttu-id="a1f9e-147">Crie uma sondagem, uma pesquisa ou um item de tarefa para os participantes da reunião.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-147">Create a poll, survey, or task item for the meeting participants.</span></span>
* <span data-ttu-id="a1f9e-148">Exibir anotações relevantes para a reunião.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-148">Display notes relevant to the meeting.</span></span> <span data-ttu-id="a1f9e-149">Por exemplo, informações sobre um líder de vendas.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-149">For example, information about a sales lead.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-tab.png" alt-text="Exemplo mostra como você pode apresentar o conteúdo da sondagem em uma guia na reunião." border="false":::

### <a name="anatomy-in-meeting-tab"></a><span data-ttu-id="a1f9e-151">Anatomia: guia In-meeting</span><span class="sxs-lookup"><span data-stu-id="a1f9e-151">Anatomy: In-meeting tab</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-anatomy.png" alt-text="Exemplo mostra a anatomia estrutural de uma guia em reunião." border="false":::

|<span data-ttu-id="a1f9e-153">Contador</span><span class="sxs-lookup"><span data-stu-id="a1f9e-153">Counter</span></span>|<span data-ttu-id="a1f9e-154">Descrição</span><span class="sxs-lookup"><span data-stu-id="a1f9e-154">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="a1f9e-155">1</span><span class="sxs-lookup"><span data-stu-id="a1f9e-155">1</span></span>|<span data-ttu-id="a1f9e-156">**Ícone do aplicativo (selecionado)**: logotipo de aplicativo transparente de 16 pixels.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-156">**App icon (selected)**: 16-pixel transparent app logo.</span></span>|
|<span data-ttu-id="a1f9e-157">2</span><span class="sxs-lookup"><span data-stu-id="a1f9e-157">2</span></span>|<span data-ttu-id="a1f9e-158">**Nome do aplicativo**</span><span class="sxs-lookup"><span data-stu-id="a1f9e-158">**App name**</span></span>|
|<span data-ttu-id="a1f9e-159">3</span><span class="sxs-lookup"><span data-stu-id="a1f9e-159">3</span></span>|<span data-ttu-id="a1f9e-160">**Header**: Inclui o nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-160">**Header**: Includes your app name.</span></span>|
|<span data-ttu-id="a1f9e-161">4 </span><span class="sxs-lookup"><span data-stu-id="a1f9e-161">4</span></span>|<span data-ttu-id="a1f9e-162">**Botão Fechar**: descarta a guia. Sempre use o ícone de fechamento superior direito em vez de uma ação no rodapé.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-162">**Close button**: Dismisses the tab. Always use the upper-right close icon instead of an action in the footer.</span></span>|
|<span data-ttu-id="a1f9e-163">5 </span><span class="sxs-lookup"><span data-stu-id="a1f9e-163">5</span></span>|<span data-ttu-id="a1f9e-164">**Barra de** notificações : Os alertas de erro são exibidos diretamente abaixo do header e pressionam o conteúdo do iframe para baixo em 20 pixels.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-164">**Notification bar**: Error alerts display directly below the header and push the iframe content down by 20 pixels.</span></span>|
|<span data-ttu-id="a1f9e-165">6 </span><span class="sxs-lookup"><span data-stu-id="a1f9e-165">6</span></span>|<span data-ttu-id="a1f9e-166">**iframe**: exibe o conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-166">**iframe**: Displays your app content.</span></span>|

### <a name="spacing"></a><span data-ttu-id="a1f9e-167">Espaçamento</span><span class="sxs-lookup"><span data-stu-id="a1f9e-167">Spacing</span></span>

<span data-ttu-id="a1f9e-168">Otimize sua guia na reunião para caber de ponta a ponta dentro da área de iframe de 280 pixels.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-168">Optimize your in-meeting tab to fit edge-to-edge within the 280 pixel-wide iframe area.</span></span> <span data-ttu-id="a1f9e-169">Há 20 pixels de preenchimento nos lados esquerdo e direito do iframe e entre o header de tabulação.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-169">There are 20 pixels of padding on the left and right sides of the iframe and between the tab header.</span></span> <span data-ttu-id="a1f9e-170">O iframe é sangramento total na parte inferior da guia.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-170">The iframe is full bleed to the bottom of the tab.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-spacing.png" alt-text="Exemplo mostra dimensões de espaçamento da guia na reunião." border="false":::

### <a name="scrolling"></a><span data-ttu-id="a1f9e-172">Rolagem</span><span class="sxs-lookup"><span data-stu-id="a1f9e-172">Scrolling</span></span>

<span data-ttu-id="a1f9e-173">O conteúdo do Iframe deve rolar verticalmente.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-173">Iframe contents should scroll vertically.</span></span> <span data-ttu-id="a1f9e-174">Você só pode ver o conteúdo que você roleu para (nada acima ou abaixo).</span><span class="sxs-lookup"><span data-stu-id="a1f9e-174">You can only see the content you've scrolled to (nothing above or below).</span></span> <span data-ttu-id="a1f9e-175">A barra de rolagem faz parte do conteúdo do iframe.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-175">The scrollbar is part of the iframe content.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-scrolling.png" alt-text="Exemplo mostra como a guia na reunião rola." border="false":::

### <a name="navigation"></a><span data-ttu-id="a1f9e-177">Navegação</span><span class="sxs-lookup"><span data-stu-id="a1f9e-177">Navigation</span></span>

<span data-ttu-id="a1f9e-178">Para cenários com camadas de navegação ou conteúdo pesado, recomendamos permitir que os usuários naveguem até uma camada secundária.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-178">For scenarios with navigation layers or heavy content, we recommend allowing users to navigate to a secondary layer.</span></span> <span data-ttu-id="a1f9e-179">Os usuários devem poder voltar para a camada anterior.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-179">Users must be able to go back to the previous layer.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav.png" alt-text="Exemplo mostra a navegação na reunião." border="false":::

## <a name="use-an-in-meeting-dialog"></a><span data-ttu-id="a1f9e-181">Usar uma caixa de diálogo na reunião</span><span class="sxs-lookup"><span data-stu-id="a1f9e-181">Use an in-meeting dialog</span></span>

<span data-ttu-id="a1f9e-182">As caixas de diálogo na reunião são exibidas no Teams de reunião.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-182">In-meeting dialogs display on the Teams meeting stage.</span></span> <span data-ttu-id="a1f9e-183">Eles exigem a atenção, confirmação ou interação de um usuário, mas são sutis e não interrompem a reunião.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-183">They require a user's attention, confirmation, or interaction but are subtle and don't interrupt the meeting.</span></span> <span data-ttu-id="a1f9e-184">Você deve usá-los com moderação e para cenários que são leves e orientados a tarefas.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-184">You should use these sparingly and for scenarios that are light and task oriented.</span></span>

### <a name="use-cases"></a><span data-ttu-id="a1f9e-185">Casos de uso</span><span class="sxs-lookup"><span data-stu-id="a1f9e-185">Use cases</span></span>

<span data-ttu-id="a1f9e-186">As caixas de diálogo na reunião são disparadas por um usuário (como o organizador da reunião) que pode querer que os participantes:</span><span class="sxs-lookup"><span data-stu-id="a1f9e-186">In-meeting dialogs are triggered by a user (such as the meeting organizer) who might want participants to:</span></span>

* <span data-ttu-id="a1f9e-187">Fornecer comentários breves</span><span class="sxs-lookup"><span data-stu-id="a1f9e-187">Provide brief feedback</span></span>
* <span data-ttu-id="a1f9e-188">Fazer uma pesquisa curta ou sondagem</span><span class="sxs-lookup"><span data-stu-id="a1f9e-188">Take a short survey or poll</span></span>
* <span data-ttu-id="a1f9e-189">Enviar aprovações</span><span class="sxs-lookup"><span data-stu-id="a1f9e-189">Submit approvals</span></span>
* <span data-ttu-id="a1f9e-190">Receber lembretes</span><span class="sxs-lookup"><span data-stu-id="a1f9e-190">Get reminders</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-dialog.png" alt-text="Exemplo mostra como você pode usar uma caixa de diálogo na reunião." border="false":::

### <a name="anatomy-in-meeting-dialog"></a><span data-ttu-id="a1f9e-192">Anatomia: caixa de diálogo na reunião</span><span class="sxs-lookup"><span data-stu-id="a1f9e-192">Anatomy: In-meeting dialog</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-anatomy.png" alt-text="Exemplo mostra a anatomia estrutural de uma caixa de diálogo na reunião." border="false":::

|<span data-ttu-id="a1f9e-194">Contador</span><span class="sxs-lookup"><span data-stu-id="a1f9e-194">Counter</span></span>|<span data-ttu-id="a1f9e-195">Descrição</span><span class="sxs-lookup"><span data-stu-id="a1f9e-195">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="a1f9e-196">1</span><span class="sxs-lookup"><span data-stu-id="a1f9e-196">1</span></span>|<span data-ttu-id="a1f9e-197">**Header**: Inclui ícone de aplicativo, nome, cadeia de caracteres de ação e ícone de fechamento.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-197">**Header**: Includes app icon, name, action string, and close icon.</span></span>|
|<span data-ttu-id="a1f9e-198">2</span><span class="sxs-lookup"><span data-stu-id="a1f9e-198">2</span></span>|<span data-ttu-id="a1f9e-199">**iframe**: exibe o conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-199">**iframe**: Displays your app content.</span></span>|

### <a name="anatomy-in-meeting-dialog-header"></a><span data-ttu-id="a1f9e-200">Anatomia: header de caixa de diálogo na reunião</span><span class="sxs-lookup"><span data-stu-id="a1f9e-200">Anatomy: In-meeting dialog header</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-header-anatomy.png" alt-text="Exemplo mostra a anatomia estrutural de um header de caixa de diálogo na reunião." border="false":::

<span data-ttu-id="a1f9e-202">Há duas variantes de header.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-202">There are two header variants.</span></span> <span data-ttu-id="a1f9e-203">Quando possível, use a variante com o avatar para reforçar que a caixa de diálogo está vindo de uma pessoa.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-203">When possible, use the variant with the avatar to reinforce that the dialog is coming from a person.</span></span>

|<span data-ttu-id="a1f9e-204">Contador</span><span class="sxs-lookup"><span data-stu-id="a1f9e-204">Counter</span></span>|<span data-ttu-id="a1f9e-205">Descrição</span><span class="sxs-lookup"><span data-stu-id="a1f9e-205">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="a1f9e-206">1</span><span class="sxs-lookup"><span data-stu-id="a1f9e-206">1</span></span>|<span data-ttu-id="a1f9e-207">**Avatar**: Pessoa que inicia a caixa de diálogo na reunião.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-207">**Avatar**: Person who initiates the in-meeting dialog.</span></span>|
|<span data-ttu-id="a1f9e-208">2</span><span class="sxs-lookup"><span data-stu-id="a1f9e-208">2</span></span>|<span data-ttu-id="a1f9e-209">**ícone de aplicativo**</span><span class="sxs-lookup"><span data-stu-id="a1f9e-209">**App icon**</span></span>|
|<span data-ttu-id="a1f9e-210">3</span><span class="sxs-lookup"><span data-stu-id="a1f9e-210">3</span></span>|<span data-ttu-id="a1f9e-211">**Nome do aplicativo**</span><span class="sxs-lookup"><span data-stu-id="a1f9e-211">**App name**</span></span>|
|<span data-ttu-id="a1f9e-212">4 </span><span class="sxs-lookup"><span data-stu-id="a1f9e-212">4</span></span>|<span data-ttu-id="a1f9e-213">**Botão Fechar**: descarta a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-213">**Close button**: Dismisses the dialog.</span></span>|
|<span data-ttu-id="a1f9e-214">5 </span><span class="sxs-lookup"><span data-stu-id="a1f9e-214">5</span></span>|<span data-ttu-id="a1f9e-215">**Cadeia de caracteres** de ação : normalmente descreve quem iniciou a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-215">**Action string**: Typically describes who initiated the dialog.</span></span>|

### <a name="responsive-behavior"></a><span data-ttu-id="a1f9e-216">Comportamento dinâmico</span><span class="sxs-lookup"><span data-stu-id="a1f9e-216">Responsive behavior</span></span>

<span data-ttu-id="a1f9e-217">As caixas de diálogo na reunião podem variar de tamanho para levar em conta cenários diferentes.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-217">In-meeting dialogs can vary in size to account for different scenarios.</span></span> <span data-ttu-id="a1f9e-218">Certifique-se de manter tamanhos de preenchimento e componentes.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-218">Make sure to maintain padding and component sizes.</span></span>

* <span data-ttu-id="a1f9e-219">**Largura**: Você pode especificar a largura do iframe da caixa de diálogo em qualquer lugar dentro do intervalo de tamanhos suportado.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-219">**Width**: You can specify the width of the dialog's iframe anywhere within the supported size range.</span></span>
* <span data-ttu-id="a1f9e-220">**Altura**: Você pode especificar a altura do iframe da caixa de diálogo em qualquer lugar dentro do intervalo de tamanhos suportado.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-220">**Height**: You can specify the height of the dialog's iframe anywhere within the supported size range.</span></span> <span data-ttu-id="a1f9e-221">Você também pode permitir que os usuários rolem verticalmente se o conteúdo do aplicativo exceder a altura máxima.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-221">You also can allow users to scroll vertically if your app content exceeds the maximum height.</span></span>

<span data-ttu-id="a1f9e-222">Para implementar, especifique a largura e a altura usando a [`externalResourceUrl`](~/apps-in-teams-meetings/create-apps-for-teams-meetings.md#notificationsignal-api) chave.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-222">To implement, specify the width and height using the [`externalResourceUrl`](~/apps-in-teams-meetings/create-apps-for-teams-meetings.md#notificationsignal-api) key.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-responsive.png" alt-text="Exemplo mostra a caixa de diálogo na reunião. Largura: Min--280 pixels (248 pixels iframe). Max--460 pixels (428 pixels iframe). Altura: 300 pixels (iframe)." border="false":::

## <a name="after-a-meeting"></a><span data-ttu-id="a1f9e-224">Após uma reunião</span><span class="sxs-lookup"><span data-stu-id="a1f9e-224">After a meeting</span></span>

<span data-ttu-id="a1f9e-225">Você pode voltar para uma reunião depois que ela terminar e exibir o conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-225">You can go back to a meeting after it ends and view app content.</span></span> <span data-ttu-id="a1f9e-226">Neste exemplo, o organizador da reunião pode ver os resultados da sondagem na guia **Contoso.** (Observação: Do ponto de vista de design, não há diferença entre uma experiência de guia pré e pós-reunião.)</span><span class="sxs-lookup"><span data-stu-id="a1f9e-226">In this example, the meeting organizer can look at poll results in the **Contoso** tab. (Note: From a design standpoint, there's no difference between a the pre- and post-meeting tab experience.)</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/post-meeting-experience.png" alt-text="A ilustração de exemplo mostra uma guia pós-reunião." border="false":::

## <a name="best-practices"></a><span data-ttu-id="a1f9e-228">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="a1f9e-228">Best practices</span></span>

<span data-ttu-id="a1f9e-229">Use essas recomendações para criar uma experiência de aplicativo de qualidade.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-229">Use these recommendations to create a quality app experience.</span></span>

### <a name="interactions"></a><span data-ttu-id="a1f9e-230">Interações</span><span class="sxs-lookup"><span data-stu-id="a1f9e-230">Interactions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-do.png" alt-text="Exemplo mostrando como limitar o número de interações." border="false":::

#### <a name="do-limit-the-number-of-interactions"></a><span data-ttu-id="a1f9e-232">Fazer: Limitar o número de interações</span><span class="sxs-lookup"><span data-stu-id="a1f9e-232">Do: Limit the number of interactions</span></span>

<span data-ttu-id="a1f9e-233">Para caixas de diálogo na reunião, remova conteúdo desnecessário que não ajude os usuários a realizar algo rapidamente.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-233">For in-meeting dialogs, remove unnecessary content that doesn't help users accomplish something quickly.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-dont.png" alt-text="Exemplo mostrando como não introduzir elementos desnecessários." border="false":::

#### <a name="dont-introduce-unnecessary-elements"></a><span data-ttu-id="a1f9e-235">Não: introduzir elementos desnecessários</span><span class="sxs-lookup"><span data-stu-id="a1f9e-235">Don't: Introduce unnecessary elements</span></span>

<span data-ttu-id="a1f9e-236">Uma única caixa de diálogo na reunião com várias interações pode distrair a chamada.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-236">A single in-meeting dialog with multiple interactions can distract from the call.</span></span>

   :::column-end:::
:::row-end:::

### <a name="layout"></a><span data-ttu-id="a1f9e-237">Layout</span><span class="sxs-lookup"><span data-stu-id="a1f9e-237">Layout</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-do.png" alt-text="Exemplo mostrando como você deve usar um layout de caixa de diálogo de coluna única." border="false":::

#### <a name="do-use-a-single-column-dialog-layout"></a><span data-ttu-id="a1f9e-239">Fazer: usar um layout de caixa de diálogo de coluna única</span><span class="sxs-lookup"><span data-stu-id="a1f9e-239">Do: Use a single-column dialog layout</span></span>

<span data-ttu-id="a1f9e-240">Como as caixas de diálogo estão no centro do estágio de reunião, a conclusão da tarefa deve ser rápida e simples para evitar a frustração do usuário.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-240">Since the dialogs are at the center of the meeting stage, task completion should be fast and simple to avoid user frustration.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-dont.png" alt-text="Exemplo mostrando que você não deve atrapalhar o espaço de uma extensão de reunião." border="false":::

#### <a name="dont-clutter-the-space"></a><span data-ttu-id="a1f9e-242">Não: desorganmente o espaço</span><span class="sxs-lookup"><span data-stu-id="a1f9e-242">Don't: Clutter the space</span></span>

<span data-ttu-id="a1f9e-243">Conteúdo densa ou estruturada em excesso pode distrair e ser avassalador, especialmente durante uma reunião.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-243">Dense or overly structured content can be distracting and overwhelming, especially during a meeting.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-do.png" alt-text="Exemplo mostrando um layout de guia de coluna única." border="false":::

#### <a name="do-use-a-single-column-tab-layout"></a><span data-ttu-id="a1f9e-245">Fazer: usar um layout de guia de coluna única</span><span class="sxs-lookup"><span data-stu-id="a1f9e-245">Do: Use a single-column tab layout</span></span>

<span data-ttu-id="a1f9e-246">Dada a natureza estreita da guia na reunião, é recomendável exibir o conteúdo em uma única coluna.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-246">Given the in-meeting tab's narrow nature, we strongly recommend displaying the contents in a single column.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-dont.png" alt-text="Exemplo mostrando uma guia com várias colunas." border="false":::

#### <a name="dont-use-multiple-columns"></a><span data-ttu-id="a1f9e-248">Não: use várias colunas</span><span class="sxs-lookup"><span data-stu-id="a1f9e-248">Don't: Use multiple columns</span></span>

<span data-ttu-id="a1f9e-249">Devido ao espaço limitado da guia na reunião, layouts com mais de uma coluna não são recomendados.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-249">Due to the limited space of the in-meeting tab, layouts with more than one column aren’t recommended.</span></span>

   :::column-end:::
:::row-end:::

### <a name="controls"></a><span data-ttu-id="a1f9e-250">Controles</span><span class="sxs-lookup"><span data-stu-id="a1f9e-250">Controls</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-do.png" alt-text="Exemplo mostrando como alinhar à direita os controles primários." border="false":::

#### <a name="do-right-align-the-primary-action"></a><span data-ttu-id="a1f9e-252">Fazer: alinhar com a direita a ação principal</span><span class="sxs-lookup"><span data-stu-id="a1f9e-252">Do: Right align the primary action</span></span>

<span data-ttu-id="a1f9e-253">Recomendamos posicionar a ação mais pesada visualmente para o local mais à direita.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-253">We recommend positioning the most visually heavy action to the right-most location.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-dont.png" alt-text="Exemplo mostrando como você não deve deixar de alinhar controles primários." border="false":::

#### <a name="dont-left-or-center-align-actions"></a><span data-ttu-id="a1f9e-255">Não: ações de alinhamento à esquerda ou central</span><span class="sxs-lookup"><span data-stu-id="a1f9e-255">Don't: Left or center align actions</span></span>

<span data-ttu-id="a1f9e-256">Isso se desvia do padrão Teams padrão para o posicionamento do controle em uma caixa de diálogo e pode entrar em conflito com uma caixa de diálogo atrás da parte superior.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-256">This deviates from the standard Teams pattern for control placement in a dialog and may conflict with a dialog behind the top one.</span></span>

   :::column-end:::
:::row-end:::

### <a name="scroll"></a><span data-ttu-id="a1f9e-257">Rolar</span><span class="sxs-lookup"><span data-stu-id="a1f9e-257">Scroll</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-do.png" alt-text="Exemplo mostrando a rolagem vertical em uma guia na reunião." border="false":::

#### <a name="do-scroll-vertically"></a><span data-ttu-id="a1f9e-259">Do: role verticalmente</span><span class="sxs-lookup"><span data-stu-id="a1f9e-259">Do: Scroll vertically</span></span>

<span data-ttu-id="a1f9e-260">Os usuários esperam rolagem vertical em Teams (e em outros lugares).</span><span class="sxs-lookup"><span data-stu-id="a1f9e-260">Users expect vertical scrolling in Teams (and elsewhere).</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-dont.png" alt-text="Exemplo mostrando a rolagem horizontal em uma guia na reunião." border="false":::

#### <a name="dont-scroll-horizontally"></a><span data-ttu-id="a1f9e-262">Não: role horizontalmente</span><span class="sxs-lookup"><span data-stu-id="a1f9e-262">Don't: Scroll horizontally</span></span>

<span data-ttu-id="a1f9e-263">A rolagem horizontal não é um comportamento esperado no Teams.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-263">Horizontal scrolling isn’t an expected behavior in Teams.</span></span> <span data-ttu-id="a1f9e-264">Outras telas no ambiente de reunião rolam verticalmente.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-264">Other canvases in the meeting environment scroll vertically.</span></span>

   :::column-end:::
:::row-end:::

### <a name="workflows"></a><span data-ttu-id="a1f9e-265">Fluxos de trabalho</span><span class="sxs-lookup"><span data-stu-id="a1f9e-265">Workflows</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-workflow-do.png" alt-text="Exemplo mostrando cenário complexo em uma guia em reunião." border="false":::

#### <a name="do-surface-complex-scenarios-in-the-in-meeting-tab"></a><span data-ttu-id="a1f9e-267">Do: Cenários complexos do Surface na guia em reunião</span><span class="sxs-lookup"><span data-stu-id="a1f9e-267">Do: Surface complex scenarios in the in-meeting tab</span></span>

<span data-ttu-id="a1f9e-268">Se seu aplicativo incluir várias tarefas, é recomendável usar uma guia na reunião com um layout de coluna única.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-268">If your app includes multiple tasks, we strongly recommend using an in-meeting tab with a single-column layout.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-workflow-dont.png" alt-text="Exemplo mostrando cenários complexos em uma caixa de diálogo na reunião." border="false":::

#### <a name="dont-make-in-meeting-dialogs-complex"></a><span data-ttu-id="a1f9e-270">Não: tornar as caixas de diálogo na reunião complexas</span><span class="sxs-lookup"><span data-stu-id="a1f9e-270">Don't: Make in-meeting dialogs complex</span></span>

<span data-ttu-id="a1f9e-271">As caixas de diálogo na reunião destinam-se a interações breves.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-271">In-meeting dialogs are intended for brief interactions.</span></span>

   :::column-end:::
:::row-end:::

### <a name="theming"></a><span data-ttu-id="a1f9e-272">Temas</span><span class="sxs-lookup"><span data-stu-id="a1f9e-272">Theming</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-do.png" alt-text="Exemplo mostrando uma extensão de reunião com o tema escuro." border="false":::

#### <a name="do-use-teams-color-tokens"></a><span data-ttu-id="a1f9e-274">Do: use Teams tokens de cores</span><span class="sxs-lookup"><span data-stu-id="a1f9e-274">Do: Use Teams color tokens</span></span>

<span data-ttu-id="a1f9e-275">Teams reuniões são otimizadas para o modo escuro para ajudar a reduzir o ruído visual e cognitivo para que os usuários possam se concentrar na discussão e no conteúdo compartilhado.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-275">Teams meetings are optimized for dark mode to help reduce visual and cognitive noise so users can focus on the discussion and shared content.</span></span> <span data-ttu-id="a1f9e-276">Saiba mais sobre como <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">usar tokens de cores (UI fluente)</a>.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-276">Learn about using <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">color tokens (Fluent UI)</a>.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-dont.png" alt-text="Exemplo mostrando uma extensão de reunião com um tema padrão (claro)." border="false":::

#### <a name="dont-hard-code-hex-values"></a><span data-ttu-id="a1f9e-278">Não: Valores de hexaxa de código rígido</span><span class="sxs-lookup"><span data-stu-id="a1f9e-278">Don't: Hard code hex values</span></span>

<span data-ttu-id="a1f9e-279">Se você não usar tokens Teams cores, seus designs serão menos escalonáveis e levarão mais tempo para gerenciar.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-279">If you don’t use Teams color tokens, your designs will be less scalable and take more time to manage.</span></span>

   :::column-end:::
:::row-end:::

### <a name="navigation"></a><span data-ttu-id="a1f9e-280">Navegação</span><span class="sxs-lookup"><span data-stu-id="a1f9e-280">Navigation</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-do.png" alt-text="Exemplo mostrando uma extensão de reunião com um botão voltar." border="false":::

#### <a name="do-have-a-back-button"></a><span data-ttu-id="a1f9e-282">Fazer: ter um botão voltar</span><span class="sxs-lookup"><span data-stu-id="a1f9e-282">Do: Have a back button</span></span>

<span data-ttu-id="a1f9e-283">Se você tiver mais de uma camada de navegação em uma guia de reunião, os usuários devem poder voltar para suas exibições anteriores.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-283">If you have more than one layer of navigation in an in-meeting tab, users must be able to go back to their previous views.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-dont.png" alt-text="Exemplo mostrando uma extensão de reunião com dois botões de demissão." border="false":::

#### <a name="dont-include-another-dismiss-button"></a><span data-ttu-id="a1f9e-285">Não: inclua outro botão de demissão</span><span class="sxs-lookup"><span data-stu-id="a1f9e-285">Don't: Include another dismiss button</span></span>

<span data-ttu-id="a1f9e-286">Fornecer uma opção para fechar o conteúdo da guia de reunião pode causar problemas, já que já há um botão no header para descartar a própria guia de reunião.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-286">Providing an option to close in-meeting tab content may cause issues since there’s already a button in the header to dismiss the in-meeting tab itself.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-caution.png" alt-text="Exemplo mostrando modais (ou módulos de tarefa) em uma guia de reunião." border="false":::

#### <a name="caution-avoid-modals-within-the-in-meeting-tab"></a><span data-ttu-id="a1f9e-288">Cuidado: evite modais na guia em reunião</span><span class="sxs-lookup"><span data-stu-id="a1f9e-288">Caution: Avoid modals within the in-meeting tab</span></span>

<span data-ttu-id="a1f9e-289">Modais (também conhecidos como módulos de tarefa) na guia já estreita da reunião podem envolver e obscurecer o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="a1f9e-289">Modals (also known as task modules) in the already narrow in-meeting tab might wrap and obscure the content.</span></span>

   :::column-end:::
:::row-end:::
