---
title: Projetando sua extensão de reunião
author: heath-hamilton
description: Saiba como projetar aplicativos em reuniões Teams e obter o kit Microsoft Teams interface do usuário.
ms.author: lajanuar
localization_priority: Normal
ms.topic: conceptual
ms.openlocfilehash: 33b11a6dfc759fabd54ca2fe2c68978a5d5d1475
ms.sourcegitcommit: 4224c44d169b1a289cbf1d3353de6bc6de7c7ea8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2021
ms.locfileid: "52644596"
---
# <a name="designing-your-microsoft-teams-meeting-extension"></a><span data-ttu-id="4152c-103">Projetando sua extensão Microsoft Teams reunião</span><span class="sxs-lookup"><span data-stu-id="4152c-103">Designing your Microsoft Teams meeting extension</span></span>

<span data-ttu-id="4152c-104">Você pode criar aplicativos para tornar as reuniões mais produtivas.</span><span class="sxs-lookup"><span data-stu-id="4152c-104">You can create apps to make meetings more productive.</span></span> <span data-ttu-id="4152c-105">Por exemplo, peça que as pessoas concluam uma pesquisa durante uma chamada ou enviem um lembrete rápido que não interrompa o fluxo da reunião.</span><span class="sxs-lookup"><span data-stu-id="4152c-105">For example, ask people to complete a survey during a call or send a quick reminder that doesn’t interrupt the flow of the meeting.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="4152c-106">Kit de Interface do Usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="4152c-106">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="4152c-107">Você pode encontrar diretrizes de design mais abrangentes, incluindo elementos que você pode obter e modificar conforme necessário, no Kit de interface do usuário Microsoft Teams usuário.</span><span class="sxs-lookup"><span data-stu-id="4152c-107">You can find more comprehensive design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4152c-108">Obtenha o Kit de Interface do Usuário do Microsoft Teams (Figma)</span><span class="sxs-lookup"><span data-stu-id="4152c-108">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-meeting-extension"></a><span data-ttu-id="4152c-109">Adicionar uma extensão de reunião</span><span class="sxs-lookup"><span data-stu-id="4152c-109">Add a meeting extension</span></span>

<span data-ttu-id="4152c-110">Os usuários podem adicionar uma extensão de reunião antes e durante as reuniões.</span><span class="sxs-lookup"><span data-stu-id="4152c-110">Users can add a meeting extension before and during meetings.</span></span> <span data-ttu-id="4152c-111">Eles também podem adicionar um aplicativo para uma reunião específica diretamente do Teams store.</span><span class="sxs-lookup"><span data-stu-id="4152c-111">They also can add an app for a specific meeting directly from the Teams store.</span></span>

### <a name="add-before-a-meeting"></a><span data-ttu-id="4152c-112">Adicionar antes de uma reunião</span><span class="sxs-lookup"><span data-stu-id="4152c-112">Add before a meeting</span></span>

<span data-ttu-id="4152c-113">Nos detalhes da reunião, os usuários podem selecionar **Adicionar uma guia +** para abrir o flyout do aplicativo e encontrar aplicativos otimizados para reuniões.</span><span class="sxs-lookup"><span data-stu-id="4152c-113">In the meeting details, users can select **Add a tab +** to open the app flyout and find apps optimized for meetings.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/add-before-meeting.png" alt-text="Exemplo mostra como adicionar uma extensão de reunião antes de uma reunião." border="false":::

### <a name="add-during-a-meeting"></a><span data-ttu-id="4152c-115">Adicionar durante uma reunião</span><span class="sxs-lookup"><span data-stu-id="4152c-115">Add during a meeting</span></span>

# <a name="desktop"></a>[<span data-ttu-id="4152c-116">Desktop</span><span class="sxs-lookup"><span data-stu-id="4152c-116">Desktop</span></span>](#tab/desktop)

Em uma reunião, os usuários podem selecionar **Mais** :::image type="icon" source="../../assets/icons/teams-client-more.png":::  >  **Adicionar um aplicativo** e escolher o aplicativo que eles querem.

:::image type="content" source="../../assets/images/apps-in-meetings/add-during-meeting.png" alt-text="Exemplo mostra como adicionar uma extensão de reunião durante uma reunião." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="4152c-119">Mobile</span><span class="sxs-lookup"><span data-stu-id="4152c-119">Mobile</span></span>](#tab/mobile)

Em uma reunião, os usuários podem selecionar **Mais** :::image type="icon" source="../../assets/icons/teams-client-more.png"::: e escolher o aplicativo que eles querem.

:::image type="content" source="../../assets/images/apps-in-meetings/mobile-add-during-meeting.png" alt-text="Exemplo mostra como adicionar uma extensão de reunião durante uma reunião no celular." border="false":::

---

## <a name="before-a-meeting"></a><span data-ttu-id="4152c-122">Antes de uma reunião</span><span class="sxs-lookup"><span data-stu-id="4152c-122">Before a meeting</span></span>

<span data-ttu-id="4152c-123">Antes de uma reunião, os usuários podem adicionar conteúdo na guia. O exemplo a seguir mostra uma pergunta de rascunho de pesquisa que as pessoas responderão durante a chamada.</span><span class="sxs-lookup"><span data-stu-id="4152c-123">Prior to a meeting, users can add content in the tab. The following example shows a draft survey question that people will answer during the call.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/before-meeting-tab.png" alt-text="Exemplo mostra como o conteúdo do aplicativo nos detalhes da reunião antes de uma chamada." border="false":::

### <a name="anatomy-meeting-tab-before-and-after-meetings"></a><span data-ttu-id="4152c-125">Anatomia: guia Reunião (antes e depois das reuniões)</span><span class="sxs-lookup"><span data-stu-id="4152c-125">Anatomy: Meeting tab (before and after meetings)</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/meeting-details-tab-anatomy.png" alt-text="Exemplo mostra a anatomia estrutural de uma guia de reunião antes e depois de uma reunião." border="false":::

|<span data-ttu-id="4152c-127">Contador</span><span class="sxs-lookup"><span data-stu-id="4152c-127">Counter</span></span>|<span data-ttu-id="4152c-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="4152c-128">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="4152c-129">1</span><span class="sxs-lookup"><span data-stu-id="4152c-129">1</span></span>|<span data-ttu-id="4152c-130">**Nome da guia**: Rótulo de navegação para sua guia.</span><span class="sxs-lookup"><span data-stu-id="4152c-130">**Tab name**: Navigation label for your tab.</span></span>|
|<span data-ttu-id="4152c-131">2</span><span class="sxs-lookup"><span data-stu-id="4152c-131">2</span></span>|<span data-ttu-id="4152c-132">**Estouro da** guia : abre ações de guia, como renomear e remover.</span><span class="sxs-lookup"><span data-stu-id="4152c-132">**Tab overflow**: Opens tab actions, such as rename and remove.</span></span>|
|<span data-ttu-id="4152c-133">3</span><span class="sxs-lookup"><span data-stu-id="4152c-133">3</span></span>|<span data-ttu-id="4152c-134">**iframe**: exibe o conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4152c-134">**iframe**: Displays your app content.</span></span>|

### <a name="designing-with-ui-templates"></a><span data-ttu-id="4152c-135">Projetando com modelos de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="4152c-135">Designing with UI templates</span></span>

<span data-ttu-id="4152c-136">Use um dos seguintes modelos Teams de interface do usuário para ajudar a projetar sua guia de reunião:</span><span class="sxs-lookup"><span data-stu-id="4152c-136">Use one of the following Teams UI templates to help design your meeting tab:</span></span>

* <span data-ttu-id="4152c-137">[Lista](../../concepts/design/design-teams-app-ui-templates.md#list): as listas podem exibir itens relacionados em um formato digitalizável e permitir que os usuários tomem ações em uma lista inteira ou itens individuais.</span><span class="sxs-lookup"><span data-stu-id="4152c-137">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="4152c-138">[Quadro de](../../concepts/design/design-teams-app-ui-templates.md#task-board)tarefas : um quadro de tarefas, às vezes chamado de quadro kanban ou faixas de nadador, é uma coleção de cartões frequentemente usada para rastrear o status de itens de trabalho ou tíquetes.</span><span class="sxs-lookup"><span data-stu-id="4152c-138">[Task board](../../concepts/design/design-teams-app-ui-templates.md#task-board): A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span>
* <span data-ttu-id="4152c-139">[Painel](../../concepts/design/design-teams-app-ui-templates.md#dashboard): um painel é uma tela que contém vários cartões que fornecem uma visão geral dos dados ou conteúdo.</span><span class="sxs-lookup"><span data-stu-id="4152c-139">[Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): A dashboard is a canvas containing multiple cards that provide an overview of data or content.</span></span>
* <span data-ttu-id="4152c-140">[Formulário](../../concepts/design/design-teams-app-ui-templates.md#form): Os formulários são para coletar, validar e enviar entrada do usuário de forma estruturada.</span><span class="sxs-lookup"><span data-stu-id="4152c-140">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="4152c-141">[Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): o modelo de estado vazio pode ser usado para muitos cenários, incluindo entrar, experiências de primeira executar, mensagens de erro e muito mais.</span><span class="sxs-lookup"><span data-stu-id="4152c-141">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>
* <span data-ttu-id="4152c-142">[Navegação à esquerda](../../concepts/design/design-teams-app-advanced-ui-components.md#left-nav): O componente de navegação esquerdo pode ajudar se sua guia exigir alguma navegação.</span><span class="sxs-lookup"><span data-stu-id="4152c-142">[Left nav](../../concepts/design/design-teams-app-advanced-ui-components.md#left-nav): The left nav component can help if your tab requires some navigation.</span></span> <span data-ttu-id="4152c-143">Em geral, você deve manter a navegação no mínimo.</span><span class="sxs-lookup"><span data-stu-id="4152c-143">In general, you should keep navigation to a minimum.</span></span>

## <a name="use-an-in-meeting-tab"></a><span data-ttu-id="4152c-144">Usar uma guia em reunião</span><span class="sxs-lookup"><span data-stu-id="4152c-144">Use an in-meeting tab</span></span>

<span data-ttu-id="4152c-145">A guia na reunião é uma tela para aumentar a colaboração durante as reuniões.</span><span class="sxs-lookup"><span data-stu-id="4152c-145">The in-meeting tab is a canvas for augmenting collaboration during meetings.</span></span> <span data-ttu-id="4152c-146">Os participantes podem ver e interagir com o conteúdo do aplicativo em um espaço dedicado fora do estágio de reunião por meio de exibições compartilhadas ou baseadas em função.</span><span class="sxs-lookup"><span data-stu-id="4152c-146">Attendees can see and interact with app content in a dedicated space outside the meeting stage through shared or role-based views.</span></span>

### <a name="use-cases"></a><span data-ttu-id="4152c-147">Casos de uso</span><span class="sxs-lookup"><span data-stu-id="4152c-147">Use cases</span></span>

<span data-ttu-id="4152c-148">As pessoas podem usar a guia na reunião para:</span><span class="sxs-lookup"><span data-stu-id="4152c-148">People might use the in-meeting tab to:</span></span>

* <span data-ttu-id="4152c-149">Forneça comentários detalhados.</span><span class="sxs-lookup"><span data-stu-id="4152c-149">Provide detailed feedback.</span></span> <span data-ttu-id="4152c-150">Por exemplo, avalie um candidato a trabalho.</span><span class="sxs-lookup"><span data-stu-id="4152c-150">For example, evaluate a job candidate.</span></span>
* <span data-ttu-id="4152c-151">Crie uma sondagem, uma pesquisa ou um item de tarefa para os participantes da reunião.</span><span class="sxs-lookup"><span data-stu-id="4152c-151">Create a poll, survey, or task item for the meeting participants.</span></span>
* <span data-ttu-id="4152c-152">Exibir anotações relevantes para a reunião.</span><span class="sxs-lookup"><span data-stu-id="4152c-152">Display notes relevant to the meeting.</span></span> <span data-ttu-id="4152c-153">Por exemplo, informações sobre um líder de vendas.</span><span class="sxs-lookup"><span data-stu-id="4152c-153">For example, information about a sales lead.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="4152c-154">Desktop</span><span class="sxs-lookup"><span data-stu-id="4152c-154">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-tab.png" alt-text="Exemplo mostra como você pode apresentar o conteúdo da sondagem em uma guia na reunião." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="4152c-156">Mobile</span><span class="sxs-lookup"><span data-stu-id="4152c-156">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/apps-in-meetings/mobile-use-in-meeting-tab.png" alt-text="Exemplo mostra como você pode apresentar conteúdo de sondagem em uma guia em reunião no celular." border="false":::

---

### <a name="anatomy-in-meeting-tab"></a><span data-ttu-id="4152c-158">Anatomia: guia In-meeting</span><span class="sxs-lookup"><span data-stu-id="4152c-158">Anatomy: In-meeting tab</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-anatomy.png" alt-text="Exemplo mostra a anatomia estrutural de uma guia em reunião." border="false":::

|<span data-ttu-id="4152c-160">Contador</span><span class="sxs-lookup"><span data-stu-id="4152c-160">Counter</span></span>|<span data-ttu-id="4152c-161">Descrição</span><span class="sxs-lookup"><span data-stu-id="4152c-161">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="4152c-162">1</span><span class="sxs-lookup"><span data-stu-id="4152c-162">1</span></span>|<span data-ttu-id="4152c-163">**Ícone do aplicativo (selecionado)**: logotipo de aplicativo transparente de 16 pixels.</span><span class="sxs-lookup"><span data-stu-id="4152c-163">**App icon (selected)**: 16-pixel transparent app logo.</span></span>|
|<span data-ttu-id="4152c-164">2</span><span class="sxs-lookup"><span data-stu-id="4152c-164">2</span></span>|<span data-ttu-id="4152c-165">**Nome do aplicativo**</span><span class="sxs-lookup"><span data-stu-id="4152c-165">**App name**</span></span>|
|<span data-ttu-id="4152c-166">3</span><span class="sxs-lookup"><span data-stu-id="4152c-166">3</span></span>|<span data-ttu-id="4152c-167">**Header**: Inclui o nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4152c-167">**Header**: Includes your app name.</span></span>|
|<span data-ttu-id="4152c-168">4 </span><span class="sxs-lookup"><span data-stu-id="4152c-168">4</span></span>|<span data-ttu-id="4152c-169">**Botão Fechar**: descarta a guia. Sempre use o ícone de fechamento superior direito em vez de uma ação no rodapé.</span><span class="sxs-lookup"><span data-stu-id="4152c-169">**Close button**: Dismisses the tab. Always use the upper-right close icon instead of an action in the footer.</span></span>|
|<span data-ttu-id="4152c-170">5 </span><span class="sxs-lookup"><span data-stu-id="4152c-170">5</span></span>|<span data-ttu-id="4152c-171">**Barra de** notificações : Os alertas de erro são exibidos diretamente abaixo do header e pressionam o conteúdo do iframe para baixo em 20 pixels.</span><span class="sxs-lookup"><span data-stu-id="4152c-171">**Notification bar**: Error alerts display directly below the header and push the iframe content down by 20 pixels.</span></span>|
|<span data-ttu-id="4152c-172">6 </span><span class="sxs-lookup"><span data-stu-id="4152c-172">6</span></span>|<span data-ttu-id="4152c-173">**iframe**: exibe o conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4152c-173">**iframe**: Displays your app content.</span></span>|

### <a name="spacing"></a><span data-ttu-id="4152c-174">Espaçamento</span><span class="sxs-lookup"><span data-stu-id="4152c-174">Spacing</span></span>

<span data-ttu-id="4152c-175">Otimize sua guia na reunião para caber de ponta a ponta dentro da área de iframe de 280 pixels.</span><span class="sxs-lookup"><span data-stu-id="4152c-175">Optimize your in-meeting tab to fit edge-to-edge within the 280 pixel-wide iframe area.</span></span> <span data-ttu-id="4152c-176">Há 20 pixels de preenchimento nos lados esquerdo e direito do iframe e entre o header de tabulação.</span><span class="sxs-lookup"><span data-stu-id="4152c-176">There are 20 pixels of padding on the left and right sides of the iframe and between the tab header.</span></span> <span data-ttu-id="4152c-177">O iframe é sangramento total na parte inferior da guia.</span><span class="sxs-lookup"><span data-stu-id="4152c-177">The iframe is full bleed to the bottom of the tab.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-spacing.png" alt-text="Exemplo mostra dimensões de espaçamento da guia na reunião." border="false":::

### <a name="scrolling"></a><span data-ttu-id="4152c-179">Rolagem</span><span class="sxs-lookup"><span data-stu-id="4152c-179">Scrolling</span></span>

<span data-ttu-id="4152c-180">O conteúdo do Iframe deve rolar verticalmente.</span><span class="sxs-lookup"><span data-stu-id="4152c-180">Iframe contents should scroll vertically.</span></span> <span data-ttu-id="4152c-181">Você só pode ver o conteúdo que você roleu para (nada acima ou abaixo).</span><span class="sxs-lookup"><span data-stu-id="4152c-181">You can only see the content you've scrolled to (nothing above or below).</span></span> <span data-ttu-id="4152c-182">A barra de rolagem faz parte do conteúdo do iframe.</span><span class="sxs-lookup"><span data-stu-id="4152c-182">The scrollbar is part of the iframe content.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-scrolling.png" alt-text="Exemplo mostra como a guia na reunião rola." border="false":::

### <a name="navigation"></a><span data-ttu-id="4152c-184">Navegação</span><span class="sxs-lookup"><span data-stu-id="4152c-184">Navigation</span></span>

<span data-ttu-id="4152c-185">Para cenários com camadas de navegação ou conteúdo pesado, recomendamos permitir que os usuários naveguem até uma camada secundária.</span><span class="sxs-lookup"><span data-stu-id="4152c-185">For scenarios with navigation layers or heavy content, we recommend allowing users to navigate to a secondary layer.</span></span> <span data-ttu-id="4152c-186">Os usuários devem poder voltar para a camada anterior.</span><span class="sxs-lookup"><span data-stu-id="4152c-186">Users must be able to go back to the previous layer.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav.png" alt-text="Exemplo mostra a navegação na reunião." border="false":::

## <a name="use-an-in-meeting-dialog"></a><span data-ttu-id="4152c-188">Usar uma caixa de diálogo na reunião</span><span class="sxs-lookup"><span data-stu-id="4152c-188">Use an in-meeting dialog</span></span>

<span data-ttu-id="4152c-189">As caixas de diálogo na reunião são exibidas no Teams de reunião.</span><span class="sxs-lookup"><span data-stu-id="4152c-189">In-meeting dialogs display on the Teams meeting stage.</span></span> <span data-ttu-id="4152c-190">Eles exigem a atenção, confirmação ou interação de um usuário, mas são sutis e não interrompem a reunião.</span><span class="sxs-lookup"><span data-stu-id="4152c-190">They require a user's attention, confirmation, or interaction but are subtle and don't interrupt the meeting.</span></span> <span data-ttu-id="4152c-191">Você deve usá-los com moderação e para cenários que são leves e orientados a tarefas.</span><span class="sxs-lookup"><span data-stu-id="4152c-191">You should use these sparingly and for scenarios that are light and task oriented.</span></span>

### <a name="use-cases"></a><span data-ttu-id="4152c-192">Casos de uso</span><span class="sxs-lookup"><span data-stu-id="4152c-192">Use cases</span></span>

<span data-ttu-id="4152c-193">As caixas de diálogo na reunião são disparadas por um usuário (como o organizador da reunião) que pode querer que os participantes:</span><span class="sxs-lookup"><span data-stu-id="4152c-193">In-meeting dialogs are triggered by a user (such as the meeting organizer) who might want participants to:</span></span>

* <span data-ttu-id="4152c-194">Fornecer comentários breves</span><span class="sxs-lookup"><span data-stu-id="4152c-194">Provide brief feedback</span></span>
* <span data-ttu-id="4152c-195">Fazer uma pesquisa curta ou sondagem</span><span class="sxs-lookup"><span data-stu-id="4152c-195">Take a short survey or poll</span></span>
* <span data-ttu-id="4152c-196">Enviar aprovações</span><span class="sxs-lookup"><span data-stu-id="4152c-196">Submit approvals</span></span>
* <span data-ttu-id="4152c-197">Receber lembretes</span><span class="sxs-lookup"><span data-stu-id="4152c-197">Get reminders</span></span>

# <a name="desktop"></a>[<span data-ttu-id="4152c-198">Desktop</span><span class="sxs-lookup"><span data-stu-id="4152c-198">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-dialog.png" alt-text="Exemplo mostra como você pode usar uma caixa de diálogo na reunião." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="4152c-200">Mobile</span><span class="sxs-lookup"><span data-stu-id="4152c-200">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/apps-in-meetings/mobile-use-in-meeting-dialog.png" alt-text="Exemplo mostra como você pode usar uma caixa de diálogo na reunião no celular." border="false":::

---

### <a name="anatomy-in-meeting-dialog"></a><span data-ttu-id="4152c-202">Anatomia: caixa de diálogo na reunião</span><span class="sxs-lookup"><span data-stu-id="4152c-202">Anatomy: In-meeting dialog</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-anatomy.png" alt-text="Exemplo mostra a anatomia estrutural de uma caixa de diálogo na reunião." border="false":::

|<span data-ttu-id="4152c-204">Contador</span><span class="sxs-lookup"><span data-stu-id="4152c-204">Counter</span></span>|<span data-ttu-id="4152c-205">Descrição</span><span class="sxs-lookup"><span data-stu-id="4152c-205">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="4152c-206">1</span><span class="sxs-lookup"><span data-stu-id="4152c-206">1</span></span>|<span data-ttu-id="4152c-207">**Header**: Inclui ícone de aplicativo, nome, cadeia de caracteres de ação e ícone de fechamento.</span><span class="sxs-lookup"><span data-stu-id="4152c-207">**Header**: Includes app icon, name, action string, and close icon.</span></span>|
|<span data-ttu-id="4152c-208">2</span><span class="sxs-lookup"><span data-stu-id="4152c-208">2</span></span>|<span data-ttu-id="4152c-209">**iframe**: exibe o conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4152c-209">**iframe**: Displays your app content.</span></span>|

### <a name="anatomy-in-meeting-dialog-header"></a><span data-ttu-id="4152c-210">Anatomia: header de caixa de diálogo na reunião</span><span class="sxs-lookup"><span data-stu-id="4152c-210">Anatomy: In-meeting dialog header</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-header-anatomy.png" alt-text="Exemplo mostra a anatomia estrutural de um header de caixa de diálogo na reunião." border="false":::

<span data-ttu-id="4152c-212">Há duas variantes de header.</span><span class="sxs-lookup"><span data-stu-id="4152c-212">There are two header variants.</span></span> <span data-ttu-id="4152c-213">Quando possível, use a variante com o avatar para reforçar que a caixa de diálogo está vindo de uma pessoa.</span><span class="sxs-lookup"><span data-stu-id="4152c-213">When possible, use the variant with the avatar to reinforce that the dialog is coming from a person.</span></span>

|<span data-ttu-id="4152c-214">Contador</span><span class="sxs-lookup"><span data-stu-id="4152c-214">Counter</span></span>|<span data-ttu-id="4152c-215">Descrição</span><span class="sxs-lookup"><span data-stu-id="4152c-215">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="4152c-216">1</span><span class="sxs-lookup"><span data-stu-id="4152c-216">1</span></span>|<span data-ttu-id="4152c-217">**Avatar**: Pessoa que inicia a caixa de diálogo na reunião.</span><span class="sxs-lookup"><span data-stu-id="4152c-217">**Avatar**: Person who initiates the in-meeting dialog.</span></span>|
|<span data-ttu-id="4152c-218">2</span><span class="sxs-lookup"><span data-stu-id="4152c-218">2</span></span>|<span data-ttu-id="4152c-219">**ícone de aplicativo**</span><span class="sxs-lookup"><span data-stu-id="4152c-219">**App icon**</span></span>|
|<span data-ttu-id="4152c-220">3</span><span class="sxs-lookup"><span data-stu-id="4152c-220">3</span></span>|<span data-ttu-id="4152c-221">**Nome do aplicativo**</span><span class="sxs-lookup"><span data-stu-id="4152c-221">**App name**</span></span>|
|<span data-ttu-id="4152c-222">4 </span><span class="sxs-lookup"><span data-stu-id="4152c-222">4</span></span>|<span data-ttu-id="4152c-223">**Botão Fechar**: descarta a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="4152c-223">**Close button**: Dismisses the dialog.</span></span>|
|<span data-ttu-id="4152c-224">5 </span><span class="sxs-lookup"><span data-stu-id="4152c-224">5</span></span>|<span data-ttu-id="4152c-225">**Cadeia de caracteres** de ação : normalmente descreve quem iniciou a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="4152c-225">**Action string**: Typically describes who initiated the dialog.</span></span>|

### <a name="responsive-behavior"></a><span data-ttu-id="4152c-226">Comportamento dinâmico</span><span class="sxs-lookup"><span data-stu-id="4152c-226">Responsive behavior</span></span>

<span data-ttu-id="4152c-227">As caixas de diálogo na reunião podem variar de tamanho para levar em conta cenários diferentes.</span><span class="sxs-lookup"><span data-stu-id="4152c-227">In-meeting dialogs can vary in size to account for different scenarios.</span></span> <span data-ttu-id="4152c-228">Certifique-se de manter tamanhos de preenchimento e componentes.</span><span class="sxs-lookup"><span data-stu-id="4152c-228">Make sure to maintain padding and component sizes.</span></span>

* <span data-ttu-id="4152c-229">**Largura**: Você pode especificar a largura do iframe da caixa de diálogo em qualquer lugar dentro do intervalo de tamanhos suportado.</span><span class="sxs-lookup"><span data-stu-id="4152c-229">**Width**: You can specify the width of the dialog's iframe anywhere within the supported size range.</span></span>
* <span data-ttu-id="4152c-230">**Altura**: Você pode especificar a altura do iframe da caixa de diálogo em qualquer lugar dentro do intervalo de tamanhos suportado.</span><span class="sxs-lookup"><span data-stu-id="4152c-230">**Height**: You can specify the height of the dialog's iframe anywhere within the supported size range.</span></span> <span data-ttu-id="4152c-231">Você também pode permitir que os usuários rolem verticalmente se o conteúdo do aplicativo exceder a altura máxima.</span><span class="sxs-lookup"><span data-stu-id="4152c-231">You also can allow users to scroll vertically if your app content exceeds the maximum height.</span></span>

<span data-ttu-id="4152c-232">Para implementar, especifique a largura e a altura usando a [`externalResourceUrl`](~/apps-in-teams-meetings/create-apps-for-teams-meetings.md#notificationsignal-api) chave.</span><span class="sxs-lookup"><span data-stu-id="4152c-232">To implement, specify the width and height using the [`externalResourceUrl`](~/apps-in-teams-meetings/create-apps-for-teams-meetings.md#notificationsignal-api) key.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-responsive.png" alt-text="Exemplo mostra a caixa de diálogo na reunião. Largura: Min--280 pixels (248 pixels iframe). Max--460 pixels (428 pixels iframe). Altura: 300 pixels (iframe)." border="false":::

## <a name="after-a-meeting"></a><span data-ttu-id="4152c-234">Após uma reunião</span><span class="sxs-lookup"><span data-stu-id="4152c-234">After a meeting</span></span>

<span data-ttu-id="4152c-235">Você pode voltar para uma reunião depois que ela terminar e exibir o conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4152c-235">You can go back to a meeting after it ends and view app content.</span></span> <span data-ttu-id="4152c-236">Neste exemplo, o organizador da reunião pode ver os resultados da sondagem na guia **Contoso.** (Observação: Do ponto de vista de design, não há diferença entre uma experiência de guia pré e pós-reunião.)</span><span class="sxs-lookup"><span data-stu-id="4152c-236">In this example, the meeting organizer can look at poll results in the **Contoso** tab. (Note: From a design standpoint, there's no difference between a the pre- and post-meeting tab experience.)</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/post-meeting-experience.png" alt-text="A ilustração de exemplo mostra uma guia pós-reunião." border="false":::

## <a name="best-practices"></a><span data-ttu-id="4152c-238">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="4152c-238">Best practices</span></span>

<span data-ttu-id="4152c-239">Use essas recomendações para criar uma experiência de aplicativo de qualidade.</span><span class="sxs-lookup"><span data-stu-id="4152c-239">Use these recommendations to create a quality app experience.</span></span>

### <a name="interactions"></a><span data-ttu-id="4152c-240">Interações</span><span class="sxs-lookup"><span data-stu-id="4152c-240">Interactions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-do.png" alt-text="Exemplo mostrando como limitar o número de interações." border="false":::

#### <a name="do-limit-the-number-of-interactions"></a><span data-ttu-id="4152c-242">Fazer: Limitar o número de interações</span><span class="sxs-lookup"><span data-stu-id="4152c-242">Do: Limit the number of interactions</span></span>

<span data-ttu-id="4152c-243">Para caixas de diálogo na reunião, remova conteúdo desnecessário que não ajude os usuários a realizar algo rapidamente.</span><span class="sxs-lookup"><span data-stu-id="4152c-243">For in-meeting dialogs, remove unnecessary content that doesn't help users accomplish something quickly.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-dont.png" alt-text="Exemplo mostrando como não introduzir elementos desnecessários." border="false":::

#### <a name="dont-introduce-unnecessary-elements"></a><span data-ttu-id="4152c-245">Não: introduzir elementos desnecessários</span><span class="sxs-lookup"><span data-stu-id="4152c-245">Don't: Introduce unnecessary elements</span></span>

<span data-ttu-id="4152c-246">Uma única caixa de diálogo na reunião com várias interações pode distrair a chamada.</span><span class="sxs-lookup"><span data-stu-id="4152c-246">A single in-meeting dialog with multiple interactions can distract from the call.</span></span>

   :::column-end:::
:::row-end:::

### <a name="layout"></a><span data-ttu-id="4152c-247">Layout</span><span class="sxs-lookup"><span data-stu-id="4152c-247">Layout</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-do.png" alt-text="Exemplo mostrando como você deve usar um layout de caixa de diálogo de coluna única." border="false":::

#### <a name="do-use-a-single-column-dialog-layout"></a><span data-ttu-id="4152c-249">Fazer: usar um layout de caixa de diálogo de coluna única</span><span class="sxs-lookup"><span data-stu-id="4152c-249">Do: Use a single-column dialog layout</span></span>

<span data-ttu-id="4152c-250">Como as caixas de diálogo estão no centro do estágio de reunião, a conclusão da tarefa deve ser rápida e simples para evitar a frustração do usuário.</span><span class="sxs-lookup"><span data-stu-id="4152c-250">Since the dialogs are at the center of the meeting stage, task completion should be fast and simple to avoid user frustration.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-dont.png" alt-text="Exemplo mostrando que você não deve atrapalhar o espaço de uma extensão de reunião." border="false":::

#### <a name="dont-clutter-the-space"></a><span data-ttu-id="4152c-252">Não: desorganmente o espaço</span><span class="sxs-lookup"><span data-stu-id="4152c-252">Don't: Clutter the space</span></span>

<span data-ttu-id="4152c-253">Conteúdo densa ou estruturada em excesso pode distrair e ser avassalador, especialmente durante uma reunião.</span><span class="sxs-lookup"><span data-stu-id="4152c-253">Dense or overly structured content can be distracting and overwhelming, especially during a meeting.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-do.png" alt-text="Exemplo mostrando um layout de guia de coluna única." border="false":::

#### <a name="do-use-a-single-column-tab-layout"></a><span data-ttu-id="4152c-255">Fazer: usar um layout de guia de coluna única</span><span class="sxs-lookup"><span data-stu-id="4152c-255">Do: Use a single-column tab layout</span></span>

<span data-ttu-id="4152c-256">Dada a natureza estreita da guia na reunião, é recomendável exibir o conteúdo em uma única coluna.</span><span class="sxs-lookup"><span data-stu-id="4152c-256">Given the in-meeting tab's narrow nature, we strongly recommend displaying the contents in a single column.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-dont.png" alt-text="Exemplo mostrando uma guia com várias colunas." border="false":::

#### <a name="dont-use-multiple-columns"></a><span data-ttu-id="4152c-258">Não: use várias colunas</span><span class="sxs-lookup"><span data-stu-id="4152c-258">Don't: Use multiple columns</span></span>

<span data-ttu-id="4152c-259">Devido ao espaço limitado da guia na reunião, layouts com mais de uma coluna não são recomendados.</span><span class="sxs-lookup"><span data-stu-id="4152c-259">Due to the limited space of the in-meeting tab, layouts with more than one column aren’t recommended.</span></span>

   :::column-end:::
:::row-end:::

### <a name="controls"></a><span data-ttu-id="4152c-260">Controles</span><span class="sxs-lookup"><span data-stu-id="4152c-260">Controls</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-do.png" alt-text="Exemplo mostrando como alinhar à direita os controles primários." border="false":::

#### <a name="do-right-align-the-primary-action"></a><span data-ttu-id="4152c-262">Fazer: alinhar com a direita a ação principal</span><span class="sxs-lookup"><span data-stu-id="4152c-262">Do: Right align the primary action</span></span>

<span data-ttu-id="4152c-263">Recomendamos posicionar a ação mais pesada visualmente para o local mais à direita.</span><span class="sxs-lookup"><span data-stu-id="4152c-263">We recommend positioning the most visually heavy action to the right-most location.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-dont.png" alt-text="Exemplo mostrando como você não deve deixar de alinhar controles primários." border="false":::

#### <a name="dont-left-or-center-align-actions"></a><span data-ttu-id="4152c-265">Não: ações de alinhamento à esquerda ou central</span><span class="sxs-lookup"><span data-stu-id="4152c-265">Don't: Left or center align actions</span></span>

<span data-ttu-id="4152c-266">Isso se desvia do padrão Teams padrão para o posicionamento do controle em uma caixa de diálogo e pode entrar em conflito com uma caixa de diálogo atrás da parte superior.</span><span class="sxs-lookup"><span data-stu-id="4152c-266">This deviates from the standard Teams pattern for control placement in a dialog and may conflict with a dialog behind the top one.</span></span>

   :::column-end:::
:::row-end:::

### <a name="scroll"></a><span data-ttu-id="4152c-267">Rolar</span><span class="sxs-lookup"><span data-stu-id="4152c-267">Scroll</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-do.png" alt-text="Exemplo mostrando a rolagem vertical em uma guia na reunião." border="false":::

#### <a name="do-scroll-vertically"></a><span data-ttu-id="4152c-269">Do: role verticalmente</span><span class="sxs-lookup"><span data-stu-id="4152c-269">Do: Scroll vertically</span></span>

<span data-ttu-id="4152c-270">Os usuários esperam rolagem vertical em Teams (e em outros lugares).</span><span class="sxs-lookup"><span data-stu-id="4152c-270">Users expect vertical scrolling in Teams (and elsewhere).</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-dont.png" alt-text="Exemplo mostrando a rolagem horizontal em uma guia na reunião." border="false":::

#### <a name="dont-scroll-horizontally"></a><span data-ttu-id="4152c-272">Não: role horizontalmente</span><span class="sxs-lookup"><span data-stu-id="4152c-272">Don't: Scroll horizontally</span></span>

<span data-ttu-id="4152c-273">A rolagem horizontal não é um comportamento esperado no Teams.</span><span class="sxs-lookup"><span data-stu-id="4152c-273">Horizontal scrolling isn’t an expected behavior in Teams.</span></span> <span data-ttu-id="4152c-274">Outras telas no ambiente de reunião rolam verticalmente.</span><span class="sxs-lookup"><span data-stu-id="4152c-274">Other canvases in the meeting environment scroll vertically.</span></span>

   :::column-end:::
:::row-end:::

### <a name="workflows"></a><span data-ttu-id="4152c-275">Fluxos de trabalho</span><span class="sxs-lookup"><span data-stu-id="4152c-275">Workflows</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-workflow-do.png" alt-text="Exemplo mostrando cenário complexo em uma guia em reunião." border="false":::

#### <a name="do-surface-complex-scenarios-in-the-in-meeting-tab"></a><span data-ttu-id="4152c-277">Do: Cenários complexos do Surface na guia em reunião</span><span class="sxs-lookup"><span data-stu-id="4152c-277">Do: Surface complex scenarios in the in-meeting tab</span></span>

<span data-ttu-id="4152c-278">Se seu aplicativo incluir várias tarefas, é recomendável usar uma guia na reunião com um layout de coluna única.</span><span class="sxs-lookup"><span data-stu-id="4152c-278">If your app includes multiple tasks, we strongly recommend using an in-meeting tab with a single-column layout.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-workflow-dont.png" alt-text="Exemplo mostrando cenários complexos em uma caixa de diálogo na reunião." border="false":::

#### <a name="dont-make-in-meeting-dialogs-complex"></a><span data-ttu-id="4152c-280">Não: tornar as caixas de diálogo na reunião complexas</span><span class="sxs-lookup"><span data-stu-id="4152c-280">Don't: Make in-meeting dialogs complex</span></span>

<span data-ttu-id="4152c-281">As caixas de diálogo na reunião destinam-se a interações breves.</span><span class="sxs-lookup"><span data-stu-id="4152c-281">In-meeting dialogs are intended for brief interactions.</span></span>

   :::column-end:::
:::row-end:::

### <a name="theming"></a><span data-ttu-id="4152c-282">Temas</span><span class="sxs-lookup"><span data-stu-id="4152c-282">Theming</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-do.png" alt-text="Exemplo mostrando uma extensão de reunião com o tema escuro." border="false":::

#### <a name="do-use-teams-color-tokens"></a><span data-ttu-id="4152c-284">Do: use Teams tokens de cores</span><span class="sxs-lookup"><span data-stu-id="4152c-284">Do: Use Teams color tokens</span></span>

<span data-ttu-id="4152c-285">Teams reuniões são otimizadas para o modo escuro para ajudar a reduzir o ruído visual e cognitivo para que os usuários possam se concentrar na discussão e no conteúdo compartilhado.</span><span class="sxs-lookup"><span data-stu-id="4152c-285">Teams meetings are optimized for dark mode to help reduce visual and cognitive noise so users can focus on the discussion and shared content.</span></span> <span data-ttu-id="4152c-286">Saiba mais sobre como <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">usar tokens de cores (UI fluente)</a>.</span><span class="sxs-lookup"><span data-stu-id="4152c-286">Learn about using <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">color tokens (Fluent UI)</a>.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-dont.png" alt-text="Exemplo mostrando uma extensão de reunião com um tema padrão (claro)." border="false":::

#### <a name="dont-hard-code-hex-values"></a><span data-ttu-id="4152c-288">Não: Valores de hexaxa de código rígido</span><span class="sxs-lookup"><span data-stu-id="4152c-288">Don't: Hard code hex values</span></span>

<span data-ttu-id="4152c-289">Se você não usar tokens Teams cores, seus designs serão menos escalonáveis e levarão mais tempo para gerenciar.</span><span class="sxs-lookup"><span data-stu-id="4152c-289">If you don’t use Teams color tokens, your designs will be less scalable and take more time to manage.</span></span>

   :::column-end:::
:::row-end:::

### <a name="navigation"></a><span data-ttu-id="4152c-290">Navegação</span><span class="sxs-lookup"><span data-stu-id="4152c-290">Navigation</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-do.png" alt-text="Exemplo mostrando uma extensão de reunião com um botão voltar." border="false":::

#### <a name="do-have-a-back-button"></a><span data-ttu-id="4152c-292">Fazer: ter um botão voltar</span><span class="sxs-lookup"><span data-stu-id="4152c-292">Do: Have a back button</span></span>

<span data-ttu-id="4152c-293">Se você tiver mais de uma camada de navegação em uma guia de reunião, os usuários devem poder voltar para suas exibições anteriores.</span><span class="sxs-lookup"><span data-stu-id="4152c-293">If you have more than one layer of navigation in an in-meeting tab, users must be able to go back to their previous views.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-dont.png" alt-text="Exemplo mostrando uma extensão de reunião com dois botões de demissão." border="false":::

#### <a name="dont-include-another-dismiss-button"></a><span data-ttu-id="4152c-295">Não: inclua outro botão de demissão</span><span class="sxs-lookup"><span data-stu-id="4152c-295">Don't: Include another dismiss button</span></span>

<span data-ttu-id="4152c-296">Fornecer uma opção para fechar o conteúdo da guia de reunião pode causar problemas, já que já há um botão no header para descartar a própria guia de reunião.</span><span class="sxs-lookup"><span data-stu-id="4152c-296">Providing an option to close in-meeting tab content may cause issues since there’s already a button in the header to dismiss the in-meeting tab itself.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-caution.png" alt-text="Exemplo mostrando modais (ou módulos de tarefa) em uma guia de reunião." border="false":::

#### <a name="caution-avoid-modals-within-the-in-meeting-tab"></a><span data-ttu-id="4152c-298">Cuidado: evite modais na guia em reunião</span><span class="sxs-lookup"><span data-stu-id="4152c-298">Caution: Avoid modals within the in-meeting tab</span></span>

<span data-ttu-id="4152c-299">Modais (também conhecidos como módulos de tarefa) na guia já estreita da reunião podem envolver e obscurecer o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="4152c-299">Modals (also known as task modules) in the already narrow in-meeting tab might wrap and obscure the content.</span></span>

   :::column-end:::
:::row-end:::
