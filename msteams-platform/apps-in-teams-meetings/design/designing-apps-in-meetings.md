---
title: Projetando sua extensão de reunião
author: heath-hamilton
description: Saiba como projetar aplicativos em reuniões Teams e obter o kit Microsoft Teams interface do usuário.
ms.author: lajanuar
localization_priority: Normal
ms.topic: conceptual
ms.openlocfilehash: 7196017f92bebb776d1b73680893ebfe3684a74c
ms.sourcegitcommit: 6e4d2c8e99426125f7b72b9640ee4a4b4f374401
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2021
ms.locfileid: "53114255"
---
# <a name="designing-your-microsoft-teams-meeting-extension"></a><span data-ttu-id="f38ba-103">Projetando sua extensão Microsoft Teams reunião</span><span class="sxs-lookup"><span data-stu-id="f38ba-103">Designing your Microsoft Teams meeting extension</span></span>

<span data-ttu-id="f38ba-104">Você pode criar aplicativos para tornar as reuniões mais produtivas.</span><span class="sxs-lookup"><span data-stu-id="f38ba-104">You can create apps to make meetings more productive.</span></span> <span data-ttu-id="f38ba-105">Por exemplo, peça que as pessoas concluam uma pesquisa durante uma chamada ou enviem um lembrete rápido que não interrompa o fluxo da reunião.</span><span class="sxs-lookup"><span data-stu-id="f38ba-105">For example, ask people to complete a survey during a call or send a quick reminder that doesn’t interrupt the flow of the meeting.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="f38ba-106">Kit de IU do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="f38ba-106">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="f38ba-107">Você pode encontrar diretrizes de design mais abrangentes, incluindo elementos que você pode obter e modificar conforme necessário, no Kit de interface do usuário Microsoft Teams usuário.</span><span class="sxs-lookup"><span data-stu-id="f38ba-107">You can find more comprehensive design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f38ba-108">Obtenha o Kit de IU do Microsoft Teams (Figma)</span><span class="sxs-lookup"><span data-stu-id="f38ba-108">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-meeting-extension"></a><span data-ttu-id="f38ba-109">Adicionar uma extensão de reunião</span><span class="sxs-lookup"><span data-stu-id="f38ba-109">Add a meeting extension</span></span>

<span data-ttu-id="f38ba-110">Os usuários podem adicionar uma extensão de reunião antes e durante as reuniões.</span><span class="sxs-lookup"><span data-stu-id="f38ba-110">Users can add a meeting extension before and during meetings.</span></span> <span data-ttu-id="f38ba-111">Eles também podem adicionar um aplicativo para uma reunião específica diretamente do Teams store.</span><span class="sxs-lookup"><span data-stu-id="f38ba-111">They also can add an app for a specific meeting directly from the Teams store.</span></span>

### <a name="add-before-a-meeting"></a><span data-ttu-id="f38ba-112">Adicionar antes de uma reunião</span><span class="sxs-lookup"><span data-stu-id="f38ba-112">Add before a meeting</span></span>

<span data-ttu-id="f38ba-113">Nos detalhes da reunião, os usuários podem selecionar **Adicionar uma guia +** para abrir o flyout do aplicativo e encontrar aplicativos otimizados para reuniões.</span><span class="sxs-lookup"><span data-stu-id="f38ba-113">In the meeting details, users can select **Add a tab +** to open the app flyout and find apps optimized for meetings.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/add-before-meeting.png" alt-text="Exemplo mostra como adicionar uma extensão de reunião antes de uma reunião." border="false":::

### <a name="add-during-a-meeting"></a><span data-ttu-id="f38ba-115">Adicionar durante uma reunião</span><span class="sxs-lookup"><span data-stu-id="f38ba-115">Add during a meeting</span></span>

# <a name="desktop"></a>[<span data-ttu-id="f38ba-116">Desktop</span><span class="sxs-lookup"><span data-stu-id="f38ba-116">Desktop</span></span>](#tab/desktop)

Em uma reunião, os usuários podem selecionar **Mais** :::image type="icon" source="../../assets/icons/teams-client-more.png":::  >  **Adicionar um aplicativo** e escolher o aplicativo que eles querem.

:::image type="content" source="../../assets/images/apps-in-meetings/add-during-meeting.png" alt-text="Exemplo mostra como adicionar uma extensão de reunião durante uma reunião." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="f38ba-119">Dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="f38ba-119">Mobile</span></span>](#tab/mobile)

Em uma reunião, os usuários podem selecionar **Mais** :::image type="icon" source="../../assets/icons/teams-client-more.png"::: e escolher o aplicativo que eles querem.

:::image type="content" source="../../assets/images/apps-in-meetings/mobile-add-during-meeting.png" alt-text="Exemplo mostra como adicionar uma extensão de reunião durante uma reunião no celular." border="false":::

---

## <a name="before-a-meeting"></a><span data-ttu-id="f38ba-122">Antes de uma reunião</span><span class="sxs-lookup"><span data-stu-id="f38ba-122">Before a meeting</span></span>

<span data-ttu-id="f38ba-123">Antes de uma reunião, os usuários podem adicionar conteúdo na guia. O exemplo a seguir mostra uma pergunta de rascunho de pesquisa que as pessoas responderão durante a chamada.</span><span class="sxs-lookup"><span data-stu-id="f38ba-123">Prior to a meeting, users can add content in the tab. The following example shows a draft survey question that people will answer during the call.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/before-meeting-tab.png" alt-text="Exemplo mostra como o conteúdo do aplicativo nos detalhes da reunião antes de uma chamada." border="false":::

### <a name="anatomy-meeting-tab-before-and-after-meetings"></a><span data-ttu-id="f38ba-125">Anatomia: guia Reunião (antes e depois das reuniões)</span><span class="sxs-lookup"><span data-stu-id="f38ba-125">Anatomy: Meeting tab (before and after meetings)</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/meeting-details-tab-anatomy.png" alt-text="Exemplo mostra a anatomia estrutural de uma guia de reunião antes e depois de uma reunião." border="false":::

|<span data-ttu-id="f38ba-127">Contador</span><span class="sxs-lookup"><span data-stu-id="f38ba-127">Counter</span></span>|<span data-ttu-id="f38ba-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="f38ba-128">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="f38ba-129">1</span><span class="sxs-lookup"><span data-stu-id="f38ba-129">1</span></span>|<span data-ttu-id="f38ba-130">**Nome da guia**: Rótulo de navegação para sua guia.</span><span class="sxs-lookup"><span data-stu-id="f38ba-130">**Tab name**: Navigation label for your tab.</span></span>|
|<span data-ttu-id="f38ba-131">2 </span><span class="sxs-lookup"><span data-stu-id="f38ba-131">2</span></span>|<span data-ttu-id="f38ba-132">**Estouro da** guia : abre ações de guia, como renomear e remover.</span><span class="sxs-lookup"><span data-stu-id="f38ba-132">**Tab overflow**: Opens tab actions, such as rename and remove.</span></span>|
|<span data-ttu-id="f38ba-133">3 </span><span class="sxs-lookup"><span data-stu-id="f38ba-133">3</span></span>|<span data-ttu-id="f38ba-134">**iframe**: exibe o conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f38ba-134">**iframe**: Displays your app content.</span></span>|

### <a name="designing-with-ui-templates"></a><span data-ttu-id="f38ba-135">Projetando com modelos de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="f38ba-135">Designing with UI templates</span></span>

<span data-ttu-id="f38ba-136">Use um dos seguintes modelos Teams de interface do usuário para ajudar a projetar sua guia de reunião:</span><span class="sxs-lookup"><span data-stu-id="f38ba-136">Use one of the following Teams UI templates to help design your meeting tab:</span></span>

* <span data-ttu-id="f38ba-137">[Lista](../../concepts/design/design-teams-app-ui-templates.md#list): as listas podem exibir itens relacionados em um formato digitalizável e permitir que os usuários tomem ações em uma lista inteira ou itens individuais.</span><span class="sxs-lookup"><span data-stu-id="f38ba-137">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="f38ba-138">[Quadro de](../../concepts/design/design-teams-app-ui-templates.md#task-board)tarefas : um quadro de tarefas, às vezes chamado de quadro kanban ou faixas de nadador, é uma coleção de cartões frequentemente usada para rastrear o status de itens de trabalho ou tíquetes.</span><span class="sxs-lookup"><span data-stu-id="f38ba-138">[Task board](../../concepts/design/design-teams-app-ui-templates.md#task-board): A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span>
* <span data-ttu-id="f38ba-139">[Painel](../../concepts/design/design-teams-app-ui-templates.md#dashboard): um painel é uma tela que contém vários cartões que fornecem uma visão geral dos dados ou conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f38ba-139">[Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): A dashboard is a canvas containing multiple cards that provide an overview of data or content.</span></span>
* <span data-ttu-id="f38ba-140">[Formulário](../../concepts/design/design-teams-app-ui-templates.md#form): Os formulários são para coletar, validar e enviar entrada do usuário de forma estruturada.</span><span class="sxs-lookup"><span data-stu-id="f38ba-140">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="f38ba-141">[Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): o modelo de estado vazio pode ser usado para muitos cenários, incluindo entrar, experiências de primeira executar, mensagens de erro e muito mais.</span><span class="sxs-lookup"><span data-stu-id="f38ba-141">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>
* <span data-ttu-id="f38ba-142">[Navegação à esquerda](../../concepts/design/design-teams-app-advanced-ui-components.md#left-nav): O componente de navegação esquerdo pode ajudar se sua guia exigir alguma navegação.</span><span class="sxs-lookup"><span data-stu-id="f38ba-142">[Left nav](../../concepts/design/design-teams-app-advanced-ui-components.md#left-nav): The left nav component can help if your tab requires some navigation.</span></span> <span data-ttu-id="f38ba-143">Em geral, você deve manter a navegação no mínimo.</span><span class="sxs-lookup"><span data-stu-id="f38ba-143">In general, you should keep navigation to a minimum.</span></span>

## <a name="use-an-in-meeting-tab"></a><span data-ttu-id="f38ba-144">Usar uma guia em reunião</span><span class="sxs-lookup"><span data-stu-id="f38ba-144">Use an in-meeting tab</span></span>

<span data-ttu-id="f38ba-145">A guia na reunião é uma tela para aumentar a colaboração durante as reuniões.</span><span class="sxs-lookup"><span data-stu-id="f38ba-145">The in-meeting tab is a canvas for augmenting collaboration during meetings.</span></span> <span data-ttu-id="f38ba-146">Os participantes podem ver e interagir com o conteúdo do aplicativo em um espaço dedicado fora do estágio de reunião por meio de exibições compartilhadas ou baseadas em função.</span><span class="sxs-lookup"><span data-stu-id="f38ba-146">Attendees can see and interact with app content in a dedicated space outside the meeting stage through shared or role-based views.</span></span>

### <a name="use-cases"></a><span data-ttu-id="f38ba-147">Casos de uso</span><span class="sxs-lookup"><span data-stu-id="f38ba-147">Use cases</span></span>

<span data-ttu-id="f38ba-148">As pessoas podem usar a guia na reunião para:</span><span class="sxs-lookup"><span data-stu-id="f38ba-148">People might use the in-meeting tab to:</span></span>

* <span data-ttu-id="f38ba-149">Forneça comentários detalhados.</span><span class="sxs-lookup"><span data-stu-id="f38ba-149">Provide detailed feedback.</span></span> <span data-ttu-id="f38ba-150">Por exemplo, avalie um candidato a trabalho.</span><span class="sxs-lookup"><span data-stu-id="f38ba-150">For example, evaluate a job candidate.</span></span>
* <span data-ttu-id="f38ba-151">Crie uma sondagem, uma pesquisa ou um item de tarefa para os participantes da reunião.</span><span class="sxs-lookup"><span data-stu-id="f38ba-151">Create a poll, survey, or task item for the meeting participants.</span></span>
* <span data-ttu-id="f38ba-152">Exibir anotações relevantes para a reunião.</span><span class="sxs-lookup"><span data-stu-id="f38ba-152">Display notes relevant to the meeting.</span></span> <span data-ttu-id="f38ba-153">Por exemplo, informações sobre um líder de vendas.</span><span class="sxs-lookup"><span data-stu-id="f38ba-153">For example, information about a sales lead.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="f38ba-154">Desktop</span><span class="sxs-lookup"><span data-stu-id="f38ba-154">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-tab.png" alt-text="Exemplo mostra como você pode apresentar o conteúdo da sondagem em uma guia na reunião." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="f38ba-156">Dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="f38ba-156">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/apps-in-meetings/mobile-use-in-meeting-tab.png" alt-text="Exemplo mostra como você pode apresentar conteúdo de sondagem em uma guia em reunião no celular." border="false":::

---

### <a name="anatomy-in-meeting-tab"></a><span data-ttu-id="f38ba-158">Anatomia: guia In-meeting</span><span class="sxs-lookup"><span data-stu-id="f38ba-158">Anatomy: In-meeting tab</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-anatomy.png" alt-text="Exemplo mostra a anatomia estrutural de uma guia em reunião." border="false":::

|<span data-ttu-id="f38ba-160">Contador</span><span class="sxs-lookup"><span data-stu-id="f38ba-160">Counter</span></span>|<span data-ttu-id="f38ba-161">Descrição</span><span class="sxs-lookup"><span data-stu-id="f38ba-161">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="f38ba-162">1</span><span class="sxs-lookup"><span data-stu-id="f38ba-162">1</span></span>|<span data-ttu-id="f38ba-163">**Ícone do aplicativo (selecionado)**: logotipo de aplicativo transparente de 16 pixels.</span><span class="sxs-lookup"><span data-stu-id="f38ba-163">**App icon (selected)**: 16-pixel transparent app logo.</span></span>|
|<span data-ttu-id="f38ba-164">2 </span><span class="sxs-lookup"><span data-stu-id="f38ba-164">2</span></span>|<span data-ttu-id="f38ba-165">**Nome do aplicativo**</span><span class="sxs-lookup"><span data-stu-id="f38ba-165">**App name**</span></span>|
|<span data-ttu-id="f38ba-166">3 </span><span class="sxs-lookup"><span data-stu-id="f38ba-166">3</span></span>|<span data-ttu-id="f38ba-167">**Header**: Inclui o nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f38ba-167">**Header**: Includes your app name.</span></span>|
|<span data-ttu-id="f38ba-168">4 </span><span class="sxs-lookup"><span data-stu-id="f38ba-168">4</span></span>|<span data-ttu-id="f38ba-169">**Botão Fechar**: descarta a guia. Sempre use o ícone de fechamento superior direito em vez de uma ação no rodapé.</span><span class="sxs-lookup"><span data-stu-id="f38ba-169">**Close button**: Dismisses the tab. Always use the upper-right close icon instead of an action in the footer.</span></span>|
|<span data-ttu-id="f38ba-170">5 </span><span class="sxs-lookup"><span data-stu-id="f38ba-170">5</span></span>|<span data-ttu-id="f38ba-171">**Barra de** notificações : Os alertas de erro são exibidos diretamente abaixo do header e pressionam o conteúdo do iframe para baixo em 20 pixels.</span><span class="sxs-lookup"><span data-stu-id="f38ba-171">**Notification bar**: Error alerts display directly below the header and push the iframe content down by 20 pixels.</span></span>|
|<span data-ttu-id="f38ba-172">6 </span><span class="sxs-lookup"><span data-stu-id="f38ba-172">6</span></span>|<span data-ttu-id="f38ba-173">**iframe**: exibe o conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f38ba-173">**iframe**: Displays your app content.</span></span>|

### <a name="spacing"></a><span data-ttu-id="f38ba-174">Espaçamento</span><span class="sxs-lookup"><span data-stu-id="f38ba-174">Spacing</span></span>

<span data-ttu-id="f38ba-175">Otimize sua guia na reunião para caber de ponta a ponta dentro da área de iframe de 280 pixels.</span><span class="sxs-lookup"><span data-stu-id="f38ba-175">Optimize your in-meeting tab to fit edge-to-edge within the 280 pixel-wide iframe area.</span></span> <span data-ttu-id="f38ba-176">Há 20 pixels de preenchimento nos lados esquerdo e direito do iframe e entre o header de tabulação.</span><span class="sxs-lookup"><span data-stu-id="f38ba-176">There are 20 pixels of padding on the left and right sides of the iframe and between the tab header.</span></span> <span data-ttu-id="f38ba-177">O iframe é sangramento total na parte inferior da guia.</span><span class="sxs-lookup"><span data-stu-id="f38ba-177">The iframe is full bleed to the bottom of the tab.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-spacing.png" alt-text="Exemplo mostra dimensões de espaçamento da guia na reunião." border="false":::

### <a name="scrolling"></a><span data-ttu-id="f38ba-179">Rolagem</span><span class="sxs-lookup"><span data-stu-id="f38ba-179">Scrolling</span></span>

<span data-ttu-id="f38ba-180">Lembre-se do seguinte se você permitir a rolagem:</span><span class="sxs-lookup"><span data-stu-id="f38ba-180">Remember the following if you allow scrolling:</span></span>

* <span data-ttu-id="f38ba-181">O conteúdo no conteúdo do iframe só deve rolar verticalmente.</span><span class="sxs-lookup"><span data-stu-id="f38ba-181">Content in the iframe contents should only scroll vertically.</span></span>
* <span data-ttu-id="f38ba-182">Os usuários só devem ver o conteúdo que rolaram para (nada acima ou abaixo).</span><span class="sxs-lookup"><span data-stu-id="f38ba-182">Users should only see the content they've scrolled to (nothing above or below).</span></span> 
* <span data-ttu-id="f38ba-183">A barra de rolagem faz parte do conteúdo do iframe.</span><span class="sxs-lookup"><span data-stu-id="f38ba-183">The scrollbar is part of the iframe content.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-scrolling.png" alt-text="Exemplo mostra como a guia na reunião rola." border="false":::

### <a name="navigation"></a><span data-ttu-id="f38ba-185">Navegação</span><span class="sxs-lookup"><span data-stu-id="f38ba-185">Navigation</span></span>

<span data-ttu-id="f38ba-186">Para cenários com camadas de navegação ou conteúdo pesado, recomendamos permitir que os usuários naveguem até uma camada secundária.</span><span class="sxs-lookup"><span data-stu-id="f38ba-186">For scenarios with navigation layers or heavy content, we recommend allowing users to navigate to a secondary layer.</span></span> <span data-ttu-id="f38ba-187">Os usuários devem poder voltar para a camada anterior.</span><span class="sxs-lookup"><span data-stu-id="f38ba-187">Users must be able to go back to the previous layer.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav.png" alt-text="Exemplo mostra a navegação na reunião." border="false":::

## <a name="use-an-in-meeting-dialog"></a><span data-ttu-id="f38ba-189">Usar uma caixa de diálogo na reunião</span><span class="sxs-lookup"><span data-stu-id="f38ba-189">Use an in-meeting dialog</span></span>

<span data-ttu-id="f38ba-190">As caixas de diálogo na reunião são exibidas no Teams de reunião.</span><span class="sxs-lookup"><span data-stu-id="f38ba-190">In-meeting dialogs display on the Teams meeting stage.</span></span> <span data-ttu-id="f38ba-191">Eles exigem a atenção, confirmação ou interação de um usuário, mas são sutis e não interrompem a reunião.</span><span class="sxs-lookup"><span data-stu-id="f38ba-191">They require a user's attention, confirmation, or interaction but are subtle and don't interrupt the meeting.</span></span> <span data-ttu-id="f38ba-192">Você deve usá-los com moderação e para cenários que são leves e orientados a tarefas.</span><span class="sxs-lookup"><span data-stu-id="f38ba-192">You should use these sparingly and for scenarios that are light and task oriented.</span></span>

### <a name="use-cases"></a><span data-ttu-id="f38ba-193">Casos de uso</span><span class="sxs-lookup"><span data-stu-id="f38ba-193">Use cases</span></span>

<span data-ttu-id="f38ba-194">As caixas de diálogo na reunião são disparadas por um usuário (como o organizador da reunião) que pode querer que os participantes:</span><span class="sxs-lookup"><span data-stu-id="f38ba-194">In-meeting dialogs are triggered by a user (such as the meeting organizer) who might want participants to:</span></span>

* <span data-ttu-id="f38ba-195">Fornecer comentários breves</span><span class="sxs-lookup"><span data-stu-id="f38ba-195">Provide brief feedback</span></span>
* <span data-ttu-id="f38ba-196">Fazer uma pesquisa curta ou sondagem</span><span class="sxs-lookup"><span data-stu-id="f38ba-196">Take a short survey or poll</span></span>
* <span data-ttu-id="f38ba-197">Enviar aprovações</span><span class="sxs-lookup"><span data-stu-id="f38ba-197">Submit approvals</span></span>
* <span data-ttu-id="f38ba-198">Receber lembretes</span><span class="sxs-lookup"><span data-stu-id="f38ba-198">Get reminders</span></span>

# <a name="desktop"></a>[<span data-ttu-id="f38ba-199">Desktop</span><span class="sxs-lookup"><span data-stu-id="f38ba-199">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-dialog.png" alt-text="Exemplo mostra como você pode usar uma caixa de diálogo na reunião." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="f38ba-201">Dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="f38ba-201">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/apps-in-meetings/mobile-use-in-meeting-dialog.png" alt-text="Exemplo mostra como você pode usar uma caixa de diálogo na reunião no celular." border="false":::

---

### <a name="anatomy-in-meeting-dialog"></a><span data-ttu-id="f38ba-203">Anatomia: caixa de diálogo na reunião</span><span class="sxs-lookup"><span data-stu-id="f38ba-203">Anatomy: In-meeting dialog</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-anatomy.png" alt-text="Exemplo mostra a anatomia estrutural de uma caixa de diálogo na reunião." border="false":::

|<span data-ttu-id="f38ba-205">Contador</span><span class="sxs-lookup"><span data-stu-id="f38ba-205">Counter</span></span>|<span data-ttu-id="f38ba-206">Descrição</span><span class="sxs-lookup"><span data-stu-id="f38ba-206">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="f38ba-207">1</span><span class="sxs-lookup"><span data-stu-id="f38ba-207">1</span></span>|<span data-ttu-id="f38ba-208">**Header**: Inclui ícone de aplicativo, nome, cadeia de caracteres de ação e ícone de fechamento.</span><span class="sxs-lookup"><span data-stu-id="f38ba-208">**Header**: Includes app icon, name, action string, and close icon.</span></span>|
|<span data-ttu-id="f38ba-209">2 </span><span class="sxs-lookup"><span data-stu-id="f38ba-209">2</span></span>|<span data-ttu-id="f38ba-210">**iframe**: exibe o conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f38ba-210">**iframe**: Displays your app content.</span></span>|

### <a name="anatomy-in-meeting-dialog-header"></a><span data-ttu-id="f38ba-211">Anatomia: header de caixa de diálogo na reunião</span><span class="sxs-lookup"><span data-stu-id="f38ba-211">Anatomy: In-meeting dialog header</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-header-anatomy.png" alt-text="Exemplo mostra a anatomia estrutural de um header de caixa de diálogo na reunião." border="false":::

<span data-ttu-id="f38ba-213">Há duas variantes de header.</span><span class="sxs-lookup"><span data-stu-id="f38ba-213">There are two header variants.</span></span> <span data-ttu-id="f38ba-214">Quando possível, use a variante com o avatar para reforçar que a caixa de diálogo está vindo de uma pessoa.</span><span class="sxs-lookup"><span data-stu-id="f38ba-214">When possible, use the variant with the avatar to reinforce that the dialog is coming from a person.</span></span>

|<span data-ttu-id="f38ba-215">Contador</span><span class="sxs-lookup"><span data-stu-id="f38ba-215">Counter</span></span>|<span data-ttu-id="f38ba-216">Descrição</span><span class="sxs-lookup"><span data-stu-id="f38ba-216">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="f38ba-217">1</span><span class="sxs-lookup"><span data-stu-id="f38ba-217">1</span></span>|<span data-ttu-id="f38ba-218">**Avatar**: Pessoa que inicia a caixa de diálogo na reunião.</span><span class="sxs-lookup"><span data-stu-id="f38ba-218">**Avatar**: Person who initiates the in-meeting dialog.</span></span>|
|<span data-ttu-id="f38ba-219">2 </span><span class="sxs-lookup"><span data-stu-id="f38ba-219">2</span></span>|<span data-ttu-id="f38ba-220">**ícone de aplicativo**</span><span class="sxs-lookup"><span data-stu-id="f38ba-220">**App icon**</span></span>|
|<span data-ttu-id="f38ba-221">3 </span><span class="sxs-lookup"><span data-stu-id="f38ba-221">3</span></span>|<span data-ttu-id="f38ba-222">**Nome do aplicativo**</span><span class="sxs-lookup"><span data-stu-id="f38ba-222">**App name**</span></span>|
|<span data-ttu-id="f38ba-223">4 </span><span class="sxs-lookup"><span data-stu-id="f38ba-223">4</span></span>|<span data-ttu-id="f38ba-224">**Botão Fechar**: descarta a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="f38ba-224">**Close button**: Dismisses the dialog.</span></span>|
|<span data-ttu-id="f38ba-225">5 </span><span class="sxs-lookup"><span data-stu-id="f38ba-225">5</span></span>|<span data-ttu-id="f38ba-226">**Cadeia de caracteres** de ação : normalmente descreve quem iniciou a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="f38ba-226">**Action string**: Typically describes who initiated the dialog.</span></span>|

### <a name="responsive-behavior-in-meeting-dialogs"></a><span data-ttu-id="f38ba-227">Comportamento responsivo: caixas de diálogo na reunião</span><span class="sxs-lookup"><span data-stu-id="f38ba-227">Responsive behavior: In-meeting dialogs</span></span>

<span data-ttu-id="f38ba-228">As caixas de diálogo na reunião podem variar de tamanho para levar em conta cenários diferentes.</span><span class="sxs-lookup"><span data-stu-id="f38ba-228">In-meeting dialogs can vary in size to account for different scenarios.</span></span> <span data-ttu-id="f38ba-229">Certifique-se de manter tamanhos de preenchimento e componentes.</span><span class="sxs-lookup"><span data-stu-id="f38ba-229">Make sure to maintain padding and component sizes.</span></span>

* <span data-ttu-id="f38ba-230">**Largura**: Você pode especificar a largura do iframe da caixa de diálogo em qualquer lugar dentro do intervalo de tamanhos suportado.</span><span class="sxs-lookup"><span data-stu-id="f38ba-230">**Width**: You can specify the width of the dialog's iframe anywhere within the supported size range.</span></span>
* <span data-ttu-id="f38ba-231">**Altura**: Você pode especificar a altura do iframe da caixa de diálogo em qualquer lugar dentro do intervalo de tamanhos suportado.</span><span class="sxs-lookup"><span data-stu-id="f38ba-231">**Height**: You can specify the height of the dialog's iframe anywhere within the supported size range.</span></span> <span data-ttu-id="f38ba-232">Você também pode permitir que os usuários rolem verticalmente se o conteúdo do aplicativo exceder a altura máxima.</span><span class="sxs-lookup"><span data-stu-id="f38ba-232">You also can allow users to scroll vertically if your app content exceeds the maximum height.</span></span>

<span data-ttu-id="f38ba-233">Para implementar, especifique a largura e a altura usando a [`externalResourceUrl`](~/apps-in-teams-meetings/create-apps-for-teams-meetings.md#notificationsignal-api) chave.</span><span class="sxs-lookup"><span data-stu-id="f38ba-233">To implement, specify the width and height using the [`externalResourceUrl`](~/apps-in-teams-meetings/create-apps-for-teams-meetings.md#notificationsignal-api) key.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-responsive.png" alt-text="Exemplo mostra a caixa de diálogo na reunião. Largura: Min--280 pixels (248 pixels iframe). Max--460 pixels (428 pixels iframe). Altura: 300 pixels (iframe)." border="false":::

## <a name="use-the-shared-meeting-stage"></a><span data-ttu-id="f38ba-235">Usar o estágio de reunião compartilhado</span><span class="sxs-lookup"><span data-stu-id="f38ba-235">Use the shared meeting stage</span></span>

<span data-ttu-id="f38ba-236">O estágio de reunião compartilhado ajuda os participantes da reunião a interagir e colaborar no conteúdo do aplicativo em tempo real.</span><span class="sxs-lookup"><span data-stu-id="f38ba-236">Shared meeting stage helps meeting participants interact with and collaborate on app content in real-time.</span></span> <span data-ttu-id="f38ba-237">Por exemplo, os usuários podem concentrar sua chamada na edição de um documento, no brainstorming com um quadro de dados ou na revisão de um painel.</span><span class="sxs-lookup"><span data-stu-id="f38ba-237">For example, users can focus their call on editing a document, brainstorming with a whiteboard, or reviewing a dashboard.</span></span>

<span data-ttu-id="f38ba-238">Os aplicativos compartilhados no estágio de reunião ocupam o mesmo espaço que uma tela compartilhada.</span><span class="sxs-lookup"><span data-stu-id="f38ba-238">Apps shared to the meeting stage occupy the same space as a shared screen.</span></span> <span data-ttu-id="f38ba-239">O estágio reorienta para todos os participantes da reunião.</span><span class="sxs-lookup"><span data-stu-id="f38ba-239">The stage reorients for all meeting participants.</span></span>

### <a name="use-cases"></a><span data-ttu-id="f38ba-240">Casos de uso</span><span class="sxs-lookup"><span data-stu-id="f38ba-240">Use cases</span></span>

<span data-ttu-id="f38ba-241">O estágio de reunião compartilhada tem a ver com colaboração e participação.</span><span class="sxs-lookup"><span data-stu-id="f38ba-241">The shared meeting stage is all about collaboration and participation.</span></span> <span data-ttu-id="f38ba-242">Aqui estão alguns cenários de exemplo para ajudá-lo a começar.</span><span class="sxs-lookup"><span data-stu-id="f38ba-242">Here are some example scenarios to help you get started.</span></span>

:::row:::
   :::column span="1":::

<span data-ttu-id="f38ba-243">**Editar e revisar**: mergulhe nos painéis e no planejamento com todos na chamada.</span><span class="sxs-lookup"><span data-stu-id="f38ba-243">**Edit and review**: Dive into dashboards and planning with everyone on the call.</span></span>

   :::column-end:::
   :::column span="3":::

:::image type="content" source="~/assets/images/apps-in-meetings/shared-meeting-stage-edit-review.png" alt-text="Exemplo mostra um painel sendo revisado no estágio de reunião compartilhado." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="1":::

<span data-ttu-id="f38ba-245">**Quadro de** trabalho : desenhar e desenhar juntos em uma tela compartilhada.</span><span class="sxs-lookup"><span data-stu-id="f38ba-245">**Whiteboard**: Draw and ideate together on a shared canvas.</span></span>

   :::column-end:::
   :::column span="3":::

:::image type="content" source="~/assets/images/apps-in-meetings/shared-meeting-stage-whiteboard.png" alt-text="Exemplo mostra um quadro de trabalho no estágio de reunião compartilhado." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="1":::

<span data-ttu-id="f38ba-247">**Quiz**: Testar conhecimento e obter informações com materiais interativos.</span><span class="sxs-lookup"><span data-stu-id="f38ba-247">**Quiz**: Test knowledge and gain insights with interactive materials.</span></span>

   :::column-end:::
   :::column span="3":::

:::image type="content" source="~/assets/images/apps-in-meetings/shared-meeting-stage-quiz.png" alt-text="Exemplo mostra um teste no estágio de reunião compartilhado." border="false":::

   :::column-end:::
:::row-end:::

### <a name="anatomy-shared-meeting-stage"></a><span data-ttu-id="f38ba-249">Anatomia: Estágio de reunião compartilhado</span><span class="sxs-lookup"><span data-stu-id="f38ba-249">Anatomy: Shared meeting stage</span></span>

:::image type="content" source="~/assets/images/apps-in-meetings/shared-meeting-stage-anatomy.png" alt-text="A imagem mostra a anatomia do design do estágio de reunião compartilhado." border="false":::

|<span data-ttu-id="f38ba-251">Contador</span><span class="sxs-lookup"><span data-stu-id="f38ba-251">Counter</span></span>|<span data-ttu-id="f38ba-252">Descrição</span><span class="sxs-lookup"><span data-stu-id="f38ba-252">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="f38ba-253">1</span><span class="sxs-lookup"><span data-stu-id="f38ba-253">1</span></span>|<span data-ttu-id="f38ba-254">**Ícone do** aplicativo : O ícone realçado indica que a guia de reunião do aplicativo está aberta.</span><span class="sxs-lookup"><span data-stu-id="f38ba-254">**App icon**: The highlighted icon indicates the app's in-meeting tab is open.</span></span>|
|<span data-ttu-id="f38ba-255">2 </span><span class="sxs-lookup"><span data-stu-id="f38ba-255">2</span></span>|<span data-ttu-id="f38ba-256">**Botão Compartilhar para estágio de reunião**: O ponto de entrada para compartilhar o aplicativo no estágio de reunião.</span><span class="sxs-lookup"><span data-stu-id="f38ba-256">**Share to meeting stage button**: The entry point to share the app to the meeting stage.</span></span> <span data-ttu-id="f38ba-257">Exibe se você configurar seu aplicativo para usar o estágio de reunião compartilhado.</span><span class="sxs-lookup"><span data-stu-id="f38ba-257">Displays if you configure your app to use the shared meeting stage.</span></span>|
|<span data-ttu-id="f38ba-258">3 </span><span class="sxs-lookup"><span data-stu-id="f38ba-258">3</span></span>|<span data-ttu-id="f38ba-259">**iframe**: exibe o conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f38ba-259">**iframe**: Displays your app content.</span></span>|
|<span data-ttu-id="f38ba-260">4 </span><span class="sxs-lookup"><span data-stu-id="f38ba-260">4</span></span>|<span data-ttu-id="f38ba-261">**Botão Parar de compartilhar**: para de compartilhar o aplicativo no estágio de reunião.</span><span class="sxs-lookup"><span data-stu-id="f38ba-261">**Stop sharing button**: Stops sharing the app to the meeting stage.</span></span> <span data-ttu-id="f38ba-262">Exibe somente para o participante que iniciou o compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="f38ba-262">Displays only for the participant who started the share.</span></span>|
|<span data-ttu-id="f38ba-263">5 </span><span class="sxs-lookup"><span data-stu-id="f38ba-263">5</span></span>|<span data-ttu-id="f38ba-264">**Atribuição do apresentador**: exibe o nome do participante que compartilhou o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f38ba-264">**Presenter attribution**: Displays the name of the participant who shared the app.</span></span>|

### <a name="responsive-behavior-shared-meeting-stage"></a><span data-ttu-id="f38ba-265">Comportamento responsivo: Estágio de reunião compartilhado</span><span class="sxs-lookup"><span data-stu-id="f38ba-265">Responsive behavior: Shared meeting stage</span></span>

<span data-ttu-id="f38ba-266">Os aplicativos compartilhados com o estágio de reunião variam de tamanho com base no estado da reunião e como o usuário reencaminha a janela.</span><span class="sxs-lookup"><span data-stu-id="f38ba-266">Apps shared to the meeting stage vary in size based on the state of the meeting and how the user resizes the window.</span></span> <span data-ttu-id="f38ba-267">Mantenha o preenchimento e o layout responsivo de navegação e controles da mesma forma que faria em um navegador.</span><span class="sxs-lookup"><span data-stu-id="f38ba-267">Maintain padding and the responsive layout of navigation and controls just as you would in a browser.</span></span>

* <span data-ttu-id="f38ba-268">**Painel lateral**: um usuário pode ter o painel lateral aberto a qualquer momento durante uma reunião para conversar, exibir a lista ou usar um aplicativo (ou seja, a guia em reunião).</span><span class="sxs-lookup"><span data-stu-id="f38ba-268">**Side panel**: A user can have the side panel open at any time during a meeting to chat, view the roster, or use an app (i.e., in-meeting tab).</span></span> <span data-ttu-id="f38ba-269">O estágio reorganiza dinamicamente quando o painel está aberto.</span><span class="sxs-lookup"><span data-stu-id="f38ba-269">The stage dynamically rearranges when the panel is open.</span></span>
* <span data-ttu-id="f38ba-270">**Grade de vídeo e áudio**: a grade de vídeo e áudio sempre fica visível para mostrar os participantes da reunião.</span><span class="sxs-lookup"><span data-stu-id="f38ba-270">**Video and audio grid**: The video and audio grid is always visible to show meeting participants.</span></span> <span data-ttu-id="f38ba-271">Quando um usuário destaca ou alfineta alguém na reunião, isso aumenta a altura ou a largura da grade do participante, dependendo da orientação.</span><span class="sxs-lookup"><span data-stu-id="f38ba-271">When a user spotlights or pins someone in the meeting, this increases the height or width of the participant grid depending on the orientation.</span></span>

#### <a name="meeting-stage-without-side-panel"></a><span data-ttu-id="f38ba-272">Estágio de reunião (sem painel lateral)</span><span class="sxs-lookup"><span data-stu-id="f38ba-272">Meeting stage (without side panel)</span></span>

<span data-ttu-id="f38ba-273">Quando o painel lateral não está aberto, o estágio de reunião é de 994 x 678 pixels por padrão e pode ter no mínimo 792 x 382 pixels.</span><span class="sxs-lookup"><span data-stu-id="f38ba-273">When the side panel isn't open, the meeting stage is 994x678 pixels by default and can be a minimum 792x382 pixels.</span></span>

:::image type="content" source="~/assets/images/apps-in-meetings/meeting-stage-no-side-panel.png" alt-text="Imagem mostrando a responsividade do estágio de reunião compartilhado com o painel lateral fechado." border="false":::

#### <a name="meeting-stage-with-side-panel"></a><span data-ttu-id="f38ba-275">Estágio de reunião (com painel lateral)</span><span class="sxs-lookup"><span data-stu-id="f38ba-275">Meeting stage (with side panel)</span></span>

<span data-ttu-id="f38ba-276">Quando o painel lateral é aberto, o estágio de reunião é 918x540 pixels por padrão e pode ter no mínimo 472 x 382 pixels.</span><span class="sxs-lookup"><span data-stu-id="f38ba-276">When the side panel is open, the meeting stage is 918x540 pixels by default and can be a minimum 472x382 pixels.</span></span>

:::image type="content" source="~/assets/images/apps-in-meetings/meeting-stage-with-side-panel.png" alt-text="Imagem mostrando a capacidade de resposta do estágio de reunião compartilhado com o painel lateral aberto." border="false":::

## <a name="after-a-meeting"></a><span data-ttu-id="f38ba-278">Após uma reunião</span><span class="sxs-lookup"><span data-stu-id="f38ba-278">After a meeting</span></span>

<span data-ttu-id="f38ba-279">Você pode voltar para uma reunião depois que ela terminar e exibir o conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f38ba-279">You can go back to a meeting after it ends and view app content.</span></span> <span data-ttu-id="f38ba-280">Neste exemplo, o organizador da reunião pode ver os resultados da sondagem na guia **Contoso.** (Observação: Do ponto de vista de design, não há diferença entre uma experiência de guia pré e pós-reunião.)</span><span class="sxs-lookup"><span data-stu-id="f38ba-280">In this example, the meeting organizer can look at poll results in the **Contoso** tab. (Note: From a design standpoint, there's no difference between a the pre- and post-meeting tab experience.)</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/post-meeting-experience.png" alt-text="A ilustração de exemplo mostra uma guia pós-reunião." border="false":::

## <a name="best-practices"></a><span data-ttu-id="f38ba-282">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="f38ba-282">Best practices</span></span>

<span data-ttu-id="f38ba-283">Use essas recomendações para criar uma experiência de aplicativo de qualidade.</span><span class="sxs-lookup"><span data-stu-id="f38ba-283">Use these recommendations to create a quality app experience.</span></span>

### <a name="interactions"></a><span data-ttu-id="f38ba-284">Interações</span><span class="sxs-lookup"><span data-stu-id="f38ba-284">Interactions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-do.png" alt-text="Exemplo mostrando como limitar o número de interações." border="false":::

#### <a name="do-limit-the-number-of-interactions"></a><span data-ttu-id="f38ba-286">Fazer: Limitar o número de interações</span><span class="sxs-lookup"><span data-stu-id="f38ba-286">Do: Limit the number of interactions</span></span>

<span data-ttu-id="f38ba-287">Para caixas de diálogo na reunião, remova conteúdo desnecessário que não ajude os usuários a realizar algo rapidamente.</span><span class="sxs-lookup"><span data-stu-id="f38ba-287">For in-meeting dialogs, remove unnecessary content that doesn't help users accomplish something quickly.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-dont.png" alt-text="Exemplo mostrando como não introduzir elementos desnecessários." border="false":::

#### <a name="dont-introduce-unnecessary-elements"></a><span data-ttu-id="f38ba-289">Não: introduzir elementos desnecessários</span><span class="sxs-lookup"><span data-stu-id="f38ba-289">Don't: Introduce unnecessary elements</span></span>

<span data-ttu-id="f38ba-290">Uma única caixa de diálogo na reunião com várias interações pode distrair a chamada.</span><span class="sxs-lookup"><span data-stu-id="f38ba-290">A single in-meeting dialog with multiple interactions can distract from the call.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-shared-stage-do.png" alt-text="Exemplo mostrando como criar um ambiente focado." border="false":::

#### <a name="do-create-a-focused-environment"></a><span data-ttu-id="f38ba-292">Do: Criar um ambiente focado</span><span class="sxs-lookup"><span data-stu-id="f38ba-292">Do: Create a focused environment</span></span>

<span data-ttu-id="f38ba-293">Recomendamos manter a experiência do aplicativo com escopo apenas no estágio de reunião.</span><span class="sxs-lookup"><span data-stu-id="f38ba-293">We recommend keeping your app’s experience scoped to just the meeting stage.</span></span> <span data-ttu-id="f38ba-294">Você pode usar uma guia na reunião no painel lateral como uma exibição secundária privada para determinados cenários.</span><span class="sxs-lookup"><span data-stu-id="f38ba-294">You can use an in-meeting tab in the side panel as a secondary, private view for certain scenarios.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-shared-stage-dont.png" alt-text="Exemplo mostrando como não incluir superfícies concorrentes durante reuniões." border="false":::

#### <a name="dont-include-competing-surfaces"></a><span data-ttu-id="f38ba-296">Não: inclua superfícies concorrentes</span><span class="sxs-lookup"><span data-stu-id="f38ba-296">Don't: Include competing surfaces</span></span>

<span data-ttu-id="f38ba-297">Seu aplicativo só deve pedir que os usuários se concentrem em uma única superfície por vez, se ele está colaborando no estágio ou respondendo a uma caixa de diálogo na reunião.</span><span class="sxs-lookup"><span data-stu-id="f38ba-297">Your app should only ask users to focus on a single surface a time, whether it's collaborating on the stage or responding to an in-meeting dialog.</span></span> <span data-ttu-id="f38ba-298">(Observação: você não pode manter as caixas de diálogo sendo disparadas por outros aplicativos enquanto seu aplicativo está em estágios.)</span><span class="sxs-lookup"><span data-stu-id="f38ba-298">(Note: You can’t keep dialogs being triggered by other apps while your app is on the stage.)</span></span> 

   :::column-end:::
:::row-end:::

### <a name="layout"></a><span data-ttu-id="f38ba-299">Layout</span><span class="sxs-lookup"><span data-stu-id="f38ba-299">Layout</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-do.png" alt-text="Exemplo mostrando como você deve usar um layout de caixa de diálogo de coluna única." border="false":::

#### <a name="do-use-a-one-column-dialog"></a><span data-ttu-id="f38ba-301">Fazer: usar uma caixa de diálogo de uma coluna</span><span class="sxs-lookup"><span data-stu-id="f38ba-301">Do: Use a one-column dialog</span></span>

<span data-ttu-id="f38ba-302">Como as caixas de diálogo estão no centro do estágio de reunião, a conclusão da tarefa deve ser rápida e simples para evitar a frustração do usuário.</span><span class="sxs-lookup"><span data-stu-id="f38ba-302">Since the dialogs are at the center of the meeting stage, task completion should be fast and simple to avoid user frustration.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-dont.png" alt-text="Exemplo mostrando que você não deve atrapalhar o espaço de uma extensão de reunião." border="false":::

#### <a name="dont-clutter-the-space"></a><span data-ttu-id="f38ba-304">Não: desorganmente o espaço</span><span class="sxs-lookup"><span data-stu-id="f38ba-304">Don't: Clutter the space</span></span>

<span data-ttu-id="f38ba-305">Conteúdo densa ou estruturada em excesso pode distrair e ser avassalador, especialmente durante uma reunião.</span><span class="sxs-lookup"><span data-stu-id="f38ba-305">Dense or overly structured content can be distracting and overwhelming, especially during a meeting.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-do.png" alt-text="Exemplo mostrando um layout de guia de coluna única." border="false":::

#### <a name="do-use-a-one-column-tab"></a><span data-ttu-id="f38ba-307">Fazer: usar uma guia de uma coluna</span><span class="sxs-lookup"><span data-stu-id="f38ba-307">Do: Use a one-column tab</span></span>

<span data-ttu-id="f38ba-308">Dada a natureza estreita da guia na reunião, é recomendável exibir o conteúdo em uma única coluna.</span><span class="sxs-lookup"><span data-stu-id="f38ba-308">Given the in-meeting tab's narrow nature, we strongly recommend displaying the contents in a single column.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-dont.png" alt-text="Exemplo mostrando uma guia com várias colunas." border="false":::

#### <a name="dont-use-multiple-columns"></a><span data-ttu-id="f38ba-310">Não: use várias colunas</span><span class="sxs-lookup"><span data-stu-id="f38ba-310">Don't: Use multiple columns</span></span>

<span data-ttu-id="f38ba-311">Devido ao espaço limitado da guia na reunião, layouts com mais de uma coluna não são recomendados.</span><span class="sxs-lookup"><span data-stu-id="f38ba-311">Due to the limited space of the in-meeting tab, layouts with more than one column aren’t recommended.</span></span>

   :::column-end:::
:::row-end:::

### <a name="controls"></a><span data-ttu-id="f38ba-312">Controles</span><span class="sxs-lookup"><span data-stu-id="f38ba-312">Controls</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-do.png" alt-text="Exemplo mostrando como alinhar à direita os controles primários." border="false":::

#### <a name="do-right-align-the-primary-action"></a><span data-ttu-id="f38ba-314">Fazer: alinhar com a direita a ação principal</span><span class="sxs-lookup"><span data-stu-id="f38ba-314">Do: Right align the primary action</span></span>

<span data-ttu-id="f38ba-315">Recomendamos posicionar a ação mais pesada visualmente para o local mais à direita.</span><span class="sxs-lookup"><span data-stu-id="f38ba-315">We recommend positioning the most visually heavy action to the right-most location.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-dont.png" alt-text="Exemplo mostrando como você não deve deixar de alinhar controles primários." border="false":::

#### <a name="dont-left-or-center-align-actions"></a><span data-ttu-id="f38ba-317">Não: ações de alinhamento à esquerda ou central</span><span class="sxs-lookup"><span data-stu-id="f38ba-317">Don't: Left or center align actions</span></span>

<span data-ttu-id="f38ba-318">Isso se desvia do padrão Teams padrão para o posicionamento do controle em uma caixa de diálogo e pode entrar em conflito com uma caixa de diálogo atrás da parte superior.</span><span class="sxs-lookup"><span data-stu-id="f38ba-318">This deviates from the standard Teams pattern for control placement in a dialog and may conflict with a dialog behind the top one.</span></span>

   :::column-end:::
:::row-end:::

### <a name="scrolling"></a><span data-ttu-id="f38ba-319">Rolagem</span><span class="sxs-lookup"><span data-stu-id="f38ba-319">Scrolling</span></span>

:::row:::
   :::column span="":::

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-do.png" alt-text="Exemplo mostrando a rolagem vertical em uma guia na reunião." border="false":::

:::image type="content" source="../../assets/images/apps-in-meetings/shared-meeting-stage-scroll-do.png" alt-text="Exemplo mostrando rolagem vertical no estágio de reunião compartilhado." border="false":::

#### <a name="do-scroll-vertically"></a><span data-ttu-id="f38ba-322">Do: role verticalmente</span><span class="sxs-lookup"><span data-stu-id="f38ba-322">Do: Scroll vertically</span></span>

<span data-ttu-id="f38ba-323">Os usuários esperam rolagem vertical em Teams (e em outros lugares).</span><span class="sxs-lookup"><span data-stu-id="f38ba-323">Users expect vertical scrolling in Teams (and elsewhere).</span></span> <span data-ttu-id="f38ba-324">Isso pode não se aplicar se você tiver uma tela criativa, como um quadro de whiteboard, que os usuários podem atravessar o eixo x e y.</span><span class="sxs-lookup"><span data-stu-id="f38ba-324">This may not apply if you have a creative canvas, such as a whiteboard, which users can pan across the x and y axis.</span></span>

   :::column-end:::
   :::column span="":::

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-dont.png" alt-text="Exemplo mostrando a rolagem horizontal em uma guia na reunião." border="false":::

:::image type="content" source="../../assets/images/apps-in-meetings/shared-meeting-stage-scroll-dont.png" alt-text="Exemplo mostrando rolagem horizontal no estágio de reunião compartilhado." border="false":::

#### <a name="dont-scroll-horizontally"></a><span data-ttu-id="f38ba-327">Não: role horizontalmente</span><span class="sxs-lookup"><span data-stu-id="f38ba-327">Don't: Scroll horizontally</span></span>

<span data-ttu-id="f38ba-328">A rolagem horizontal não é um comportamento esperado no Teams (incluindo o ambiente de reunião).</span><span class="sxs-lookup"><span data-stu-id="f38ba-328">Horizontal scrolling isn’t an expected behavior in Teams (including the meeting environment).</span></span>

   :::column-end:::
:::row-end:::

### <a name="workflows"></a><span data-ttu-id="f38ba-329">Fluxos de trabalho</span><span class="sxs-lookup"><span data-stu-id="f38ba-329">Workflows</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-workflow-do.png" alt-text="Exemplo mostrando cenário complexo em uma guia em reunião." border="false":::

#### <a name="do-surface-complex-scenarios-in-the-in-meeting-tab"></a><span data-ttu-id="f38ba-331">Do: Cenários complexos do Surface na guia em reunião</span><span class="sxs-lookup"><span data-stu-id="f38ba-331">Do: Surface complex scenarios in the in-meeting tab</span></span>

<span data-ttu-id="f38ba-332">Se seu aplicativo incluir várias tarefas, é recomendável usar uma guia na reunião com um layout de coluna única.</span><span class="sxs-lookup"><span data-stu-id="f38ba-332">If your app includes multiple tasks, we strongly recommend using an in-meeting tab with a single-column layout.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-workflow-dont.png" alt-text="Exemplo mostrando cenários complexos em uma caixa de diálogo na reunião." border="false":::

#### <a name="dont-make-in-meeting-dialogs-complex"></a><span data-ttu-id="f38ba-334">Não: tornar as caixas de diálogo na reunião complexas</span><span class="sxs-lookup"><span data-stu-id="f38ba-334">Don't: Make in-meeting dialogs complex</span></span>

<span data-ttu-id="f38ba-335">As caixas de diálogo na reunião destinam-se a interações breves.</span><span class="sxs-lookup"><span data-stu-id="f38ba-335">In-meeting dialogs are intended for brief interactions.</span></span>

   :::column-end:::
:::row-end:::

### <a name="theming"></a><span data-ttu-id="f38ba-336">Temas</span><span class="sxs-lookup"><span data-stu-id="f38ba-336">Theming</span></span>

:::row:::
   :::column span="":::

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-do.png" alt-text="Exemplo mostrando uma extensão de reunião com o tema escuro." border="false":::

:::image type="content" source="../../assets/images/apps-in-meetings/shared-meeting-stage-theming-do.png" alt-text="Outro exemplo mostrando a extensão da reunião com o tema escuro." border="false":::

#### <a name="do-focus-on-dark-theme"></a><span data-ttu-id="f38ba-339">Do: Foco no tema escuro</span><span class="sxs-lookup"><span data-stu-id="f38ba-339">Do: Focus on dark theme</span></span>

<span data-ttu-id="f38ba-340">Teams reuniões são otimizadas para temas escuros para ajudar a reduzir o ruído visual e cognitivo para que os usuários possam se concentrar na discussão e no conteúdo compartilhado.</span><span class="sxs-lookup"><span data-stu-id="f38ba-340">Teams meetings are optimized for dark theme to help reduce visual and cognitive noise so users can focus on the discussion and shared content.</span></span> <span data-ttu-id="f38ba-341">Lembre-se de que determinados tipos de aplicativos (como quadro de dados e edição de documentos) não precisam de uma tela escura.</span><span class="sxs-lookup"><span data-stu-id="f38ba-341">Keep in mind certain types of apps (such as whiteboarding and document editing) don't need a dark canvas.</span></span>

   :::column-end:::
   :::column span="":::

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-dont.png" alt-text="Exemplo mostrando uma extensão de reunião com cores que não combinam com o tema da reunião." border="false":::

:::image type="content" source="../../assets/images/apps-in-meetings/shared-meeting-stage-theming-dont.png" alt-text="Outro exemplo mostrando uma extensão de reunião com cores que não combinam com o tema da reunião." border="false":::

#### <a name="dont-use-unfamiliar-colors"></a><span data-ttu-id="f38ba-344">Não: use cores desconhecidas</span><span class="sxs-lookup"><span data-stu-id="f38ba-344">Don't: Use unfamiliar colors</span></span>

<span data-ttu-id="f38ba-345">As cores que se colidem com o ambiente de reunião podem ser distrativas e aparecerem menos nativas Teams.</span><span class="sxs-lookup"><span data-stu-id="f38ba-345">Colors that clash with the meeting environment may be distracting and appear less native to Teams.</span></span> <span data-ttu-id="f38ba-346">Saiba mais sobre a Teams [de cores](https://developer.microsoft.com/fluentui#/styles/web/colors/products), incluindo neutros do tema de chamada.</span><span class="sxs-lookup"><span data-stu-id="f38ba-346">Learn about the Teams [color ramp](https://developer.microsoft.com/fluentui#/styles/web/colors/products), including call theme neutrals.</span></span>

   :::column-end:::
:::row-end:::

### <a name="navigation"></a><span data-ttu-id="f38ba-347">Navegação</span><span class="sxs-lookup"><span data-stu-id="f38ba-347">Navigation</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-do.png" alt-text="Exemplo mostrando uma extensão de reunião com um botão voltar." border="false":::

#### <a name="do-have-a-back-button"></a><span data-ttu-id="f38ba-349">Fazer: ter um botão voltar</span><span class="sxs-lookup"><span data-stu-id="f38ba-349">Do: Have a back button</span></span>

<span data-ttu-id="f38ba-350">Se você tiver mais de uma camada de navegação em uma guia de reunião, os usuários devem poder voltar para suas exibições anteriores.</span><span class="sxs-lookup"><span data-stu-id="f38ba-350">If you have more than one layer of navigation in an in-meeting tab, users must be able to go back to their previous views.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-dont.png" alt-text="Exemplo mostrando uma extensão de reunião com dois botões de demissão." border="false":::

#### <a name="dont-include-another-dismiss-button"></a><span data-ttu-id="f38ba-352">Não: inclua outro botão de demissão</span><span class="sxs-lookup"><span data-stu-id="f38ba-352">Don't: Include another dismiss button</span></span>

<span data-ttu-id="f38ba-353">Fornecer uma opção para fechar o conteúdo da guia de reunião pode causar problemas, já que já há um botão no header para descartar a própria guia de reunião.</span><span class="sxs-lookup"><span data-stu-id="f38ba-353">Providing an option to close in-meeting tab content may cause issues since there’s already a button in the header to dismiss the in-meeting tab itself.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-caution.png" alt-text="Exemplo mostrando modais (ou módulos de tarefa) em uma guia de reunião." border="false":::

#### <a name="caution-avoid-modals-within-the-in-meeting-tab"></a><span data-ttu-id="f38ba-355">Cuidado: evite modais na guia em reunião</span><span class="sxs-lookup"><span data-stu-id="f38ba-355">Caution: Avoid modals within the in-meeting tab</span></span>

<span data-ttu-id="f38ba-356">Modais (também conhecidos como módulos de tarefa) na guia já estreita da reunião podem envolver e obscurecer o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f38ba-356">Modals (also known as task modules) in the already narrow in-meeting tab might wrap and obscure the content.</span></span>

   :::column-end:::
:::row-end:::

### <a name="responsive-behavior"></a><span data-ttu-id="f38ba-357">Comportamento dinâmico</span><span class="sxs-lookup"><span data-stu-id="f38ba-357">Responsive behavior</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/shared-meeting-stage-responsiveness-do.png" alt-text="Exemplo mostrando como reorganizar corretamente uma extensão de reunião." border="false":::

#### <a name="do-resize-and-scale-your-app-responsively"></a><span data-ttu-id="f38ba-359">Do: Resize e dimensione seu aplicativo de forma responsiva</span><span class="sxs-lookup"><span data-stu-id="f38ba-359">Do: Resize and scale your app responsively</span></span>

<span data-ttu-id="f38ba-360">O conteúdo do aplicativo deve reorganizar e condensar dinamicamente em janelas menores.</span><span class="sxs-lookup"><span data-stu-id="f38ba-360">App content should dynamically resize and condense in smaller windows.</span></span> <span data-ttu-id="f38ba-361">Mantenha a navegação principal do aplicativo e quaisquer controles flutuantes visíveis.</span><span class="sxs-lookup"><span data-stu-id="f38ba-361">Keep your app’s main navigation and any floating controls visible.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/shared-meeting-stage-responsiveness-dont.png" alt-text="Exemplo mostrando como não reorganizar corretamente uma extensão de reunião." border="false":::

#### <a name="dont-crop-or-clip-primary-ui-components"></a><span data-ttu-id="f38ba-363">Não: cortar ou cortar componentes primários da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="f38ba-363">Don't: Crop or clip primary UI components</span></span>

<span data-ttu-id="f38ba-364">A navegação flutuante e os controles fora da tela e a necessidade de um rolagem para encontrar podem ser confusos para os usuários.</span><span class="sxs-lookup"><span data-stu-id="f38ba-364">Floating navigation and controls off screen and requiring a scroll to find can be confusing for users.</span></span> <span data-ttu-id="f38ba-365">O conteúdo do aplicativo não deve rolar horizontalmente quando não puder caber no iframe.</span><span class="sxs-lookup"><span data-stu-id="f38ba-365">Your app content shouldn’t scroll horizontally when it can't fit in the iframe.</span></span>

   :::column-end:::
:::row-end:::

## <a name="next-step"></a><span data-ttu-id="f38ba-366">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="f38ba-366">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f38ba-367">Configurar seu aplicativo para reuniões</span><span class="sxs-lookup"><span data-stu-id="f38ba-367">Configure your app for meetings</span></span>](~/apps-in-teams-meetings/enable-and-configure-your-app-for-teams-meetings.md)
