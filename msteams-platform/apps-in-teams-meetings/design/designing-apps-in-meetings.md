---
title: Projetando sua extensão de reunião
author: heath-hamilton
description: Saiba como projetar aplicativos em reuniões do Teams e obter o Kit de interface do usuário do Microsoft Teams.
ms.author: lajanuar
ms.topic: conceptual
ms.openlocfilehash: c6e76356b698da4e32e279b0842ab2cc35254e99
ms.sourcegitcommit: 84f408aa2854aa7a5cefaa66ce9a373b19e0864a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/18/2021
ms.locfileid: "49886755"
---
# <a name="designing-your-microsoft-teams-meeting-extension"></a><span data-ttu-id="db907-103">Projetando sua extensão de reunião do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="db907-103">Designing your Microsoft Teams meeting extension</span></span>

<span data-ttu-id="db907-104">Você pode criar aplicativos para tornar as reuniões mais produtivas.</span><span class="sxs-lookup"><span data-stu-id="db907-104">You can create apps to make meetings more productive.</span></span> <span data-ttu-id="db907-105">Por exemplo, peça que as pessoas concluam uma pesquisa durante uma chamada ou enviem um lembrete rápido que não interrompa o fluxo da reunião.</span><span class="sxs-lookup"><span data-stu-id="db907-105">For example, ask people to complete a survey during a call or send a quick reminder that doesn’t interrupt the flow of the meeting.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="db907-106">Kit de interface do usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="db907-106">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="db907-107">Você pode encontrar diretrizes de design mais abrangentes, incluindo elementos que você pode pegar e modificar conforme necessário, no Kit de interface do usuário do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="db907-107">You can find more comprehensive design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="db907-108">Obter o Kit de Interface do Usuário do Microsoft Teams (Kit de Interface do Usuário do Microsoft Teams)</span><span class="sxs-lookup"><span data-stu-id="db907-108">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-meeting-extension"></a><span data-ttu-id="db907-109">Adicionar uma extensão de reunião</span><span class="sxs-lookup"><span data-stu-id="db907-109">Add a meeting extension</span></span>

<span data-ttu-id="db907-110">Você pode adicionar uma extensão de reunião antes e durante as reuniões.</span><span class="sxs-lookup"><span data-stu-id="db907-110">You can add a meeting extension before and during meetings.</span></span> <span data-ttu-id="db907-111">Você também pode adicionar um aplicativo para uma reunião específica diretamente da loja do Teams (AppSource).</span><span class="sxs-lookup"><span data-stu-id="db907-111">You also can add an app for a specific meeting directly from the Teams store (AppSource).</span></span>

### <a name="add-before-a-meeting"></a><span data-ttu-id="db907-112">Adicionar antes de uma reunião</span><span class="sxs-lookup"><span data-stu-id="db907-112">Add before a meeting</span></span>

<span data-ttu-id="db907-113">Nos detalhes da reunião, selecione **Adicionar uma guia +** para abrir o flyout do aplicativo e encontrar aplicativos otimizados para reuniões.</span><span class="sxs-lookup"><span data-stu-id="db907-113">In the meeting details, select **Add a tab +** to open the app flyout and find apps optimized for meetings.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/add-before-meeting.png" alt-text="O exemplo mostra como adicionar uma extensão de reunião antes de uma reunião." border="false":::

### <a name="add-during-a-meeting"></a><span data-ttu-id="db907-115">Adicionar durante uma reunião</span><span class="sxs-lookup"><span data-stu-id="db907-115">Add during a meeting</span></span>

Em uma reunião, selecione **Mais** :::image type="icon" source="../../assets/icons/teams-client-more.png":::  >  **Adicionar um aplicativo** e escolha o aplicativo que você deseja.

:::image type="content" source="../../assets/images/apps-in-meetings/add-during-meeting.png" alt-text="O exemplo mostra como adicionar uma extensão de reunião durante uma reunião." border="false":::

## <a name="before-a-meeting"></a><span data-ttu-id="db907-118">Antes de uma reunião</span><span class="sxs-lookup"><span data-stu-id="db907-118">Before a meeting</span></span>

<span data-ttu-id="db907-119">Antes da reunião, você pode adicionar conteúdo na guia. O exemplo a seguir mostra uma pergunta de rascunho da pesquisa que as pessoas responderão durante a chamada.</span><span class="sxs-lookup"><span data-stu-id="db907-119">Prior to your meeting, you can add content in the tab. The following example shows a draft survey question that people will answer during the call.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/before-meeting-tab.png" alt-text="Exemplo mostra como aplicativo conteúdo nos detalhes da reunião antes de uma chamada." border="false":::

### <a name="anatomy-meeting-tab-before-and-after-meetings"></a><span data-ttu-id="db907-121">Anatomia: guia Reunião (antes e depois das reuniões)</span><span class="sxs-lookup"><span data-stu-id="db907-121">Anatomy: Meeting tab (before and after meetings)</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/meeting-details-tab-anatomy.png" alt-text="O exemplo mostra a anatomia estrutural de uma guia de reunião antes e depois de uma reunião." border="false":::

|<span data-ttu-id="db907-123">Contador</span><span class="sxs-lookup"><span data-stu-id="db907-123">Counter</span></span>|<span data-ttu-id="db907-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="db907-124">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="db907-125">1</span><span class="sxs-lookup"><span data-stu-id="db907-125">1</span></span>|<span data-ttu-id="db907-126">**Nome da** guia: rótulo de navegação da guia.</span><span class="sxs-lookup"><span data-stu-id="db907-126">**Tab name**: Navigation label for your tab.</span></span>|
|<span data-ttu-id="db907-127">2 </span><span class="sxs-lookup"><span data-stu-id="db907-127">2</span></span>|<span data-ttu-id="db907-128">**Estouro de** guia: abre ações da guia, como renomear e remover.</span><span class="sxs-lookup"><span data-stu-id="db907-128">**Tab overflow**: Opens tab actions, such as rename and remove.</span></span>|
|<span data-ttu-id="db907-129">3</span><span class="sxs-lookup"><span data-stu-id="db907-129">3</span></span>|<span data-ttu-id="db907-130">**iframe:** exibe o conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="db907-130">**iframe**: Displays your app content.</span></span>|

### <a name="designing-with-ui-templates"></a><span data-ttu-id="db907-131">Projetando com modelos de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="db907-131">Designing with UI templates</span></span>

<span data-ttu-id="db907-132">Use um dos seguintes modelos de interface do usuário do Teams para ajudar a projetar sua guia de reunião:</span><span class="sxs-lookup"><span data-stu-id="db907-132">Use one of the following Teams UI templates to help design your meeting tab:</span></span>

* <span data-ttu-id="db907-133">[Lista:](../../concepts/design/design-teams-app-ui-templates.md#list)as listas podem exibir itens relacionados em um formato digitalizável e permitir que os usuários tomem ações em uma lista inteira ou itens individuais.</span><span class="sxs-lookup"><span data-stu-id="db907-133">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="db907-134">[Quadro de](../../concepts/design/design-teams-app-ui-templates.md#task-board)tarefas: um quadro de tarefas, às vezes chamado de quadro kanban ou trilhos de mesa, é uma coleção de cartões frequentemente usada para acompanhar o status de itens de trabalho ou tíquetes.</span><span class="sxs-lookup"><span data-stu-id="db907-134">[Task board](../../concepts/design/design-teams-app-ui-templates.md#task-board): A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span>
* <span data-ttu-id="db907-135">[Painel:](../../concepts/design/design-teams-app-ui-templates.md#dashboard)um painel é uma tela que contém vários cartões que fornecem uma visão geral de dados ou conteúdo.</span><span class="sxs-lookup"><span data-stu-id="db907-135">[Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): A dashboard is a canvas containing multiple cards that provide an overview of data or content.</span></span>
* <span data-ttu-id="db907-136">[Formulário](../../concepts/design/design-teams-app-ui-templates.md#form): os formulários são para coletar, validar e enviar entradas do usuário de maneira estruturada.</span><span class="sxs-lookup"><span data-stu-id="db907-136">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="db907-137">[Estado vazio:](../../concepts/design/design-teams-app-ui-templates.md#empty-state)o modelo de estado vazio pode ser usado para muitos cenários, incluindo entrar, experiências de primeira executar, mensagens de erro e muito mais.</span><span class="sxs-lookup"><span data-stu-id="db907-137">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>
* <span data-ttu-id="db907-138">[Navegação à esquerda:](../../concepts/design/design-teams-app-ui-templates.md#left-nav)o modelo de navegação à esquerda pode ajudar se a guia exigir alguma navegação.</span><span class="sxs-lookup"><span data-stu-id="db907-138">[Left nav](../../concepts/design/design-teams-app-ui-templates.md#left-nav): The left nav template can help if your tab requires some navigation.</span></span> <span data-ttu-id="db907-139">Em geral, você deve manter a navegação por tabulação no mínimo.</span><span class="sxs-lookup"><span data-stu-id="db907-139">In general, you should keep tab navigation to a minimum.</span></span>

## <a name="use-an-in-meeting-tab"></a><span data-ttu-id="db907-140">Usar uma guia na reunião</span><span class="sxs-lookup"><span data-stu-id="db907-140">Use an in-meeting tab</span></span>

<span data-ttu-id="db907-141">A guia na reunião é uma tela para aumentar a colaboração durante as reuniões.</span><span class="sxs-lookup"><span data-stu-id="db907-141">The in-meeting tab is a canvas for augmenting collaboration during meetings.</span></span> <span data-ttu-id="db907-142">Os participantes podem ver e interagir com o conteúdo do aplicativo em um espaço dedicado fora do estágio da reunião por meio de exibições compartilhadas ou baseadas em função.</span><span class="sxs-lookup"><span data-stu-id="db907-142">Attendees can see and interact with app content in a dedicated space outside the meeting stage through shared or role-based views.</span></span>

### <a name="use-cases"></a><span data-ttu-id="db907-143">Casos de uso</span><span class="sxs-lookup"><span data-stu-id="db907-143">Use cases</span></span>

<span data-ttu-id="db907-144">As pessoas podem usar a guia na reunião para:</span><span class="sxs-lookup"><span data-stu-id="db907-144">People might use the in-meeting tab to:</span></span>

* <span data-ttu-id="db907-145">Fornecer comentários detalhados (por exemplo, avaliar um candidato a trabalho)</span><span class="sxs-lookup"><span data-stu-id="db907-145">Provide detailed feedback (for example, evaluate a job candidate)</span></span>
* <span data-ttu-id="db907-146">Criar rapidamente um poll, uma pesquisa ou um item de tarefa para os participantes da reunião</span><span class="sxs-lookup"><span data-stu-id="db907-146">Quickly create a poll, survey, or task item for the meeting participants</span></span>
* <span data-ttu-id="db907-147">Exibir anotações relevantes para a reunião (por exemplo, informações sobre um líder de vendas)</span><span class="sxs-lookup"><span data-stu-id="db907-147">Display notes relevant to the meeting (for example, information about a sales lead)</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-tab.png" alt-text="O exemplo mostra como você pode apresentar conteúdo de sondagem em uma guia na reunião." border="false":::

### <a name="anatomy-in-meeting-tab"></a><span data-ttu-id="db907-149">Anatomia: guia Na reunião</span><span class="sxs-lookup"><span data-stu-id="db907-149">Anatomy: In-meeting tab</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-anatomy.png" alt-text="O exemplo mostra a anatomia estrutural de uma guia em reunião." border="false":::

|<span data-ttu-id="db907-151">Contador</span><span class="sxs-lookup"><span data-stu-id="db907-151">Counter</span></span>|<span data-ttu-id="db907-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="db907-152">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="db907-153">1</span><span class="sxs-lookup"><span data-stu-id="db907-153">1</span></span>|<span data-ttu-id="db907-154">**Ícone do aplicativo (selecionado)**: logotipo do aplicativo transparente de 16 pixels.</span><span class="sxs-lookup"><span data-stu-id="db907-154">**App icon (selected)**: 16-pixel transparent app logo.</span></span>|
|<span data-ttu-id="db907-155">2 </span><span class="sxs-lookup"><span data-stu-id="db907-155">2</span></span>|<span data-ttu-id="db907-156">**Nome do aplicativo**</span><span class="sxs-lookup"><span data-stu-id="db907-156">**App name**</span></span>|
|<span data-ttu-id="db907-157">3</span><span class="sxs-lookup"><span data-stu-id="db907-157">3</span></span>|<span data-ttu-id="db907-158">**Header**: inclui o nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="db907-158">**Header**: Includes your app name.</span></span>|
|<span data-ttu-id="db907-159">4 </span><span class="sxs-lookup"><span data-stu-id="db907-159">4</span></span>|<span data-ttu-id="db907-160">**Botão Fechar:** descarta a guia. Sempre use o ícone de fechamento superior direito em vez de uma ação no rodapé.</span><span class="sxs-lookup"><span data-stu-id="db907-160">**Close button**: Dismisses the tab. Always use the upper-right close icon instead of an action in the footer.</span></span>|
|<span data-ttu-id="db907-161">5 </span><span class="sxs-lookup"><span data-stu-id="db907-161">5</span></span>|<span data-ttu-id="db907-162">**Barra de notificação:** os alertas de erro são exibidos diretamente abaixo do título e baixam o conteúdo do iframe em 20 pixels.</span><span class="sxs-lookup"><span data-stu-id="db907-162">**Notification bar**: Error alerts display directly below the header and push the iframe content down by 20 pixels.</span></span>|
|<span data-ttu-id="db907-163">6 </span><span class="sxs-lookup"><span data-stu-id="db907-163">6</span></span>|<span data-ttu-id="db907-164">**iframe:** exibe o conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="db907-164">**iframe**: Displays your app content.</span></span>|

### <a name="spacing"></a><span data-ttu-id="db907-165">Espaçamento</span><span class="sxs-lookup"><span data-stu-id="db907-165">Spacing</span></span>

<span data-ttu-id="db907-166">Otimize a guia na reunião para ajustar de ponta a ponta dentro da área de iframe de 280 pixels.</span><span class="sxs-lookup"><span data-stu-id="db907-166">Optimize your in-meeting tab to fit edge-to-edge within the 280 pixel-wide iframe area.</span></span> <span data-ttu-id="db907-167">Há 20 pixels de preenchimento nos lados esquerdo e direito do iframe e entre o header da guia.</span><span class="sxs-lookup"><span data-stu-id="db907-167">There are 20 pixels of padding on the left and right sides of the iframe and between the tab header.</span></span> <span data-ttu-id="db907-168">O iframe está com sangramento completo na parte inferior da guia.</span><span class="sxs-lookup"><span data-stu-id="db907-168">The iframe is full bleed to the bottom of the tab.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-spacing.png" alt-text="O exemplo mostra as dimensões de espaçamento de tabulação na reunião." border="false":::

### <a name="scrolling"></a><span data-ttu-id="db907-170">Rolagem</span><span class="sxs-lookup"><span data-stu-id="db907-170">Scrolling</span></span>

<span data-ttu-id="db907-171">O conteúdo do Iframe deve rolar verticalmente.</span><span class="sxs-lookup"><span data-stu-id="db907-171">Iframe contents should scroll vertically.</span></span> <span data-ttu-id="db907-172">Você só pode ver o conteúdo que você rolou para (nada acima ou abaixo).</span><span class="sxs-lookup"><span data-stu-id="db907-172">You can only see the content you've scrolled to (nothing above or below).</span></span> <span data-ttu-id="db907-173">A barra de rolagem faz parte do conteúdo do iframe.</span><span class="sxs-lookup"><span data-stu-id="db907-173">The scrollbar is part of the iframe content.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-scrolling.png" alt-text="O exemplo mostra como a guia na reunião rola." border="false":::

### <a name="navigation"></a><span data-ttu-id="db907-175">Navegação</span><span class="sxs-lookup"><span data-stu-id="db907-175">Navigation</span></span>

<span data-ttu-id="db907-176">Para cenários com camadas de navegação ou conteúdo intenso, recomendamos permitir que os usuários naveguem até uma camada secundária.</span><span class="sxs-lookup"><span data-stu-id="db907-176">For scenarios with navigation layers or heavy content, we recommend allowing users to navigate to a secondary layer.</span></span> <span data-ttu-id="db907-177">Os usuários devem poder voltar à camada anterior.</span><span class="sxs-lookup"><span data-stu-id="db907-177">Users must be able to go back to the previous layer.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav.png" alt-text="O exemplo mostra a navegação na reunião." border="false":::

## <a name="use-an-in-meeting-dialog"></a><span data-ttu-id="db907-179">Usar uma caixa de diálogo na reunião</span><span class="sxs-lookup"><span data-stu-id="db907-179">Use an in-meeting dialog</span></span>

<span data-ttu-id="db907-180">As caixas de diálogo na reunião são exibidas no estágio de reunião do Teams.</span><span class="sxs-lookup"><span data-stu-id="db907-180">In-meeting dialogs display on the Teams meeting stage.</span></span> <span data-ttu-id="db907-181">Eles exigem a atenção, a confirmação ou a interação do usuário, mas são sutis e não interrompem a reunião.</span><span class="sxs-lookup"><span data-stu-id="db907-181">They require a user's attention, confirmation, or interaction but are subtle and don't interrupt the meeting.</span></span> <span data-ttu-id="db907-182">Você deve usá-los com moderação e para cenários que são leves e orientados a tarefas.</span><span class="sxs-lookup"><span data-stu-id="db907-182">You should use these sparingly and for scenarios that are light and task oriented.</span></span>

### <a name="use-cases"></a><span data-ttu-id="db907-183">Casos de uso</span><span class="sxs-lookup"><span data-stu-id="db907-183">Use cases</span></span>

<span data-ttu-id="db907-184">As caixas de diálogo na reunião são disparadas por um usuário (como o organizador da reunião) que pode querer que os participantes:</span><span class="sxs-lookup"><span data-stu-id="db907-184">In-meeting dialogs are triggered by a user (such as the meeting organizer) who might want participants to:</span></span>

* <span data-ttu-id="db907-185">Fornecer comentários breves</span><span class="sxs-lookup"><span data-stu-id="db907-185">Provide brief feedback</span></span>
* <span data-ttu-id="db907-186">Fazer uma pequena pesquisa ou sondagem</span><span class="sxs-lookup"><span data-stu-id="db907-186">Take a short survey or poll</span></span>
* <span data-ttu-id="db907-187">Enviar aprovações</span><span class="sxs-lookup"><span data-stu-id="db907-187">Submit approvals</span></span>
* <span data-ttu-id="db907-188">Receber lembretes</span><span class="sxs-lookup"><span data-stu-id="db907-188">Get reminders</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-dialog.png" alt-text="O exemplo mostra como você pode usar uma caixa de diálogo na reunião." border="false":::

### <a name="anatomy-in-meeting-dialog"></a><span data-ttu-id="db907-190">Anatomia: Caixa de diálogo na reunião</span><span class="sxs-lookup"><span data-stu-id="db907-190">Anatomy: In-meeting dialog</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-anatomy.png" alt-text="O exemplo mostra a anatomia estrutural de uma caixa de diálogo em reunião." border="false":::

|<span data-ttu-id="db907-192">Contador</span><span class="sxs-lookup"><span data-stu-id="db907-192">Counter</span></span>|<span data-ttu-id="db907-193">Descrição</span><span class="sxs-lookup"><span data-stu-id="db907-193">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="db907-194">1</span><span class="sxs-lookup"><span data-stu-id="db907-194">1</span></span>|<span data-ttu-id="db907-195">**Header:** inclui ícone do aplicativo, nome, cadeia de caracteres de ação e ícone fechar.</span><span class="sxs-lookup"><span data-stu-id="db907-195">**Header**: Includes app icon, name, action string, and close icon.</span></span>|
|<span data-ttu-id="db907-196">2 </span><span class="sxs-lookup"><span data-stu-id="db907-196">2</span></span>|<span data-ttu-id="db907-197">**iframe:** exibe o conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="db907-197">**iframe**: Displays your app content.</span></span>|

### <a name="anatomy-in-meeting-dialog-header"></a><span data-ttu-id="db907-198">Anatomia: No-meeting dialog header</span><span class="sxs-lookup"><span data-stu-id="db907-198">Anatomy: In-meeting dialog header</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-header-anatomy.png" alt-text="O exemplo mostra a anatomia estrutural de um header de caixa de diálogo em reunião." border="false":::

<span data-ttu-id="db907-200">Há duas variantes de header.</span><span class="sxs-lookup"><span data-stu-id="db907-200">There are two header variants.</span></span> <span data-ttu-id="db907-201">Quando possível, use a variante com o avatar para reforçar que a caixa de diálogo está vindo de uma pessoa.</span><span class="sxs-lookup"><span data-stu-id="db907-201">When possible, use the variant with the avatar to reinforce that the dialog is coming from a person.</span></span>

|<span data-ttu-id="db907-202">Contador</span><span class="sxs-lookup"><span data-stu-id="db907-202">Counter</span></span>|<span data-ttu-id="db907-203">Descrição</span><span class="sxs-lookup"><span data-stu-id="db907-203">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="db907-204">1</span><span class="sxs-lookup"><span data-stu-id="db907-204">1</span></span>|<span data-ttu-id="db907-205">**Avatar**: pessoa que inicia a caixa de diálogo na reunião.</span><span class="sxs-lookup"><span data-stu-id="db907-205">**Avatar**: Person who initiates the in-meeting dialog.</span></span>|
|<span data-ttu-id="db907-206">2 </span><span class="sxs-lookup"><span data-stu-id="db907-206">2</span></span>|<span data-ttu-id="db907-207">**ícone de aplicativo**</span><span class="sxs-lookup"><span data-stu-id="db907-207">**App icon**</span></span>|
|<span data-ttu-id="db907-208">3</span><span class="sxs-lookup"><span data-stu-id="db907-208">3</span></span>|<span data-ttu-id="db907-209">**Nome do aplicativo**</span><span class="sxs-lookup"><span data-stu-id="db907-209">**App name**</span></span>|
|<span data-ttu-id="db907-210">4 </span><span class="sxs-lookup"><span data-stu-id="db907-210">4</span></span>|<span data-ttu-id="db907-211">**Botão Fechar:** descarta a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="db907-211">**Close button**: Dismisses the dialog.</span></span>|
|<span data-ttu-id="db907-212">5 </span><span class="sxs-lookup"><span data-stu-id="db907-212">5</span></span>|<span data-ttu-id="db907-213">**Cadeia de caracteres** de ação: normalmente descreve quem iniciou a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="db907-213">**Action string**: Typically describes who initiated the dialog.</span></span>|

### <a name="responsive-behavior"></a><span data-ttu-id="db907-214">Comportamento dinâmico</span><span class="sxs-lookup"><span data-stu-id="db907-214">Responsive behavior</span></span>

<span data-ttu-id="db907-215">As caixas de diálogo na reunião podem variar de tamanho para levar em conta cenários diferentes.</span><span class="sxs-lookup"><span data-stu-id="db907-215">In-meeting dialogs can vary in size to account for different scenarios.</span></span> <span data-ttu-id="db907-216">Certifique-se de manter os tamanhos de preenchimento e componente.</span><span class="sxs-lookup"><span data-stu-id="db907-216">Make sure to maintain padding and component sizes.</span></span>

* <span data-ttu-id="db907-217">**Largura**: a largura do iframe é um valor absoluto dentro do intervalo especificado.</span><span class="sxs-lookup"><span data-stu-id="db907-217">**Width**: The iframe width is an absolute value within the range you specify.</span></span>
* <span data-ttu-id="db907-218">**Altura**: a altura da caixa de diálogo é determinada pelo conteúdo no iframe.</span><span class="sxs-lookup"><span data-stu-id="db907-218">**Height**: The height of the dialog is determined by the content in the iframe.</span></span> <span data-ttu-id="db907-219">A rolagem vertical assume o controle do conteúdo que excede a altura máxima.</span><span class="sxs-lookup"><span data-stu-id="db907-219">Vertical scroll takes over for content that exceeds the maximum height.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-responsive.png" alt-text="O exemplo mostra a caixa de diálogo na reunião. Largura: Min--280 pixels (iframe de 248 pixels). Máx--460 pixels (428 pixels iframe). Altura: 300 pixels (iframe)." border="false":::

## <a name="after-a-meeting"></a><span data-ttu-id="db907-221">Após uma reunião</span><span class="sxs-lookup"><span data-stu-id="db907-221">After a meeting</span></span>

<span data-ttu-id="db907-222">Você pode voltar para uma reunião depois que ela terminar e exibir o conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="db907-222">You can go back to a meeting after it ends and view app content.</span></span> <span data-ttu-id="db907-223">Neste exemplo, o organizador da reunião pode ver os resultados da votação na guia **Contoso.** (Observação: do ponto de vista do design, não há nenhuma diferença entre a experiência de guia pré e pós-reunião.)</span><span class="sxs-lookup"><span data-stu-id="db907-223">In this example, the meeting organizer can look at poll results in the **Contoso** tab. (Note: From a design standpoint, there's no difference between a the pre- and post-meeting tab experience.)</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/post-meeting-experience.png" alt-text="O exemplo mostra uma guia pós-reunião." border="false":::

## <a name="best-practices"></a><span data-ttu-id="db907-225">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="db907-225">Best practices</span></span>

### <a name="interactions"></a><span data-ttu-id="db907-226">Interações</span><span class="sxs-lookup"><span data-stu-id="db907-226">Interactions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-do.png" alt-text="Exemplo mostrando como limitar o número de interações." border="false":::

#### <a name="do-limit-the-number-of-interactions"></a><span data-ttu-id="db907-228">Fazer: limitar o número de interações</span><span class="sxs-lookup"><span data-stu-id="db907-228">Do: Limit the number of interactions</span></span>

<span data-ttu-id="db907-229">Para caixas de diálogo na reunião, remova conteúdo desnecessário que não ajude os usuários a realizar algo rapidamente.</span><span class="sxs-lookup"><span data-stu-id="db907-229">For in-meeting dialogs, remove unnecessary content that doesn't help users accomplish something quickly.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-dont.png" alt-text="Exemplo mostrando como não introduzir elementos desnecessários." border="false":::

#### <a name="dont-introduce-unnecessary-elements"></a><span data-ttu-id="db907-231">Não: introduzir elementos desnecessários</span><span class="sxs-lookup"><span data-stu-id="db907-231">Don't: Introduce unnecessary elements</span></span>

<span data-ttu-id="db907-232">Uma única caixa de diálogo de reunião com várias interações pode distrair a chamada.</span><span class="sxs-lookup"><span data-stu-id="db907-232">A single in-meeting dialog with multiple interactions can distract from the call.</span></span>

   :::column-end:::
:::row-end:::

### <a name="layout"></a><span data-ttu-id="db907-233">Layout</span><span class="sxs-lookup"><span data-stu-id="db907-233">Layout</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-do.png" alt-text="Exemplo mostrando como você deve usar um layout de caixa de diálogo de coluna única." border="false":::

#### <a name="do-use-a-single-column-dialog-layout"></a><span data-ttu-id="db907-235">Fazer: Usar um layout de caixa de diálogo de coluna única</span><span class="sxs-lookup"><span data-stu-id="db907-235">Do: Use a single-column dialog layout</span></span>

<span data-ttu-id="db907-236">Como as caixas de diálogo estão no centro do estágio da reunião, a conclusão da tarefa deve ser rápida e simples para evitar frustração do usuário.</span><span class="sxs-lookup"><span data-stu-id="db907-236">Since the dialogs are at the center of the meeting stage, task completion should be fast and simple to avoid user frustration.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-dont.png" alt-text="Exemplo mostrando que você não deve desorganar o espaço de uma extensão de reunião." border="false":::

#### <a name="dont-clutter-the-space"></a><span data-ttu-id="db907-238">Não: desorganmente o espaço</span><span class="sxs-lookup"><span data-stu-id="db907-238">Don't: Clutter the space</span></span>

<span data-ttu-id="db907-239">Conteúdo densa ou muito estruturada pode distrair e sobrecarregar, especialmente durante uma reunião.</span><span class="sxs-lookup"><span data-stu-id="db907-239">Dense or overly structured content can be distracting and overwhelming, especially during a meeting.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-do.png" alt-text="Exemplo mostrando um layout de guia de coluna única." border="false":::

#### <a name="do-use-a-single-column-tab-layout"></a><span data-ttu-id="db907-241">Fazer: Usar um layout de guia de coluna única</span><span class="sxs-lookup"><span data-stu-id="db907-241">Do: Use a single-column tab layout</span></span>

<span data-ttu-id="db907-242">Dada a natureza estreita da guia na reunião, é recomendável exibir o conteúdo em uma única coluna.</span><span class="sxs-lookup"><span data-stu-id="db907-242">Given the in-meeting tab's narrow nature, we strongly recommend displaying the contents in a single column.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-dont.png" alt-text="Exemplo mostrando uma guia com várias colunas." border="false":::

#### <a name="dont-use-multiple-columns"></a><span data-ttu-id="db907-244">Não: use várias colunas</span><span class="sxs-lookup"><span data-stu-id="db907-244">Don't: Use multiple columns</span></span>

<span data-ttu-id="db907-245">Devido ao espaço limitado da guia na reunião, layouts com mais de uma coluna não são recomendados.</span><span class="sxs-lookup"><span data-stu-id="db907-245">Due to the limited space of the in-meeting tab, layouts with more than one column aren’t recommended.</span></span>

   :::column-end:::
:::row-end:::

### <a name="controls"></a><span data-ttu-id="db907-246">Controles</span><span class="sxs-lookup"><span data-stu-id="db907-246">Controls</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-do.png" alt-text="Exemplo mostrando como alinhar à direita os controles primários." border="false":::

#### <a name="do-right-align-the-primary-action"></a><span data-ttu-id="db907-248">Fazer: Alinhar à direita a ação principal</span><span class="sxs-lookup"><span data-stu-id="db907-248">Do: Right align the primary action</span></span>

<span data-ttu-id="db907-249">Recomendamos posicionar a ação mais intensa visualmente no local mais à direita.</span><span class="sxs-lookup"><span data-stu-id="db907-249">We recommend positioning the most visually heavy action to the right-most location.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-dont.png" alt-text="Exemplo mostrando como você não deve alinhar à esquerda os controles primários." border="false":::

#### <a name="dont-left-or-center-align-actions"></a><span data-ttu-id="db907-251">Não: ações de alinhamento à esquerda ou ao centro</span><span class="sxs-lookup"><span data-stu-id="db907-251">Don't: Left or center align actions</span></span>

<span data-ttu-id="db907-252">Isso se desvia do padrão do Teams para o posicionamento do controle em uma caixa de diálogo e pode entrar em conflito com uma caixa de diálogo atrás da superior.</span><span class="sxs-lookup"><span data-stu-id="db907-252">This deviates from the standard Teams pattern for control placement in a dialog and may conflict with a dialog behind the top one.</span></span>

   :::column-end:::
:::row-end:::

### <a name="scroll"></a><span data-ttu-id="db907-253">Rolar</span><span class="sxs-lookup"><span data-stu-id="db907-253">Scroll</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-do.png" alt-text="Exemplo mostrando a rolagem vertical em uma guia na reunião." border="false":::

#### <a name="do-scroll-vertically"></a><span data-ttu-id="db907-255">Fazer: rolar verticalmente</span><span class="sxs-lookup"><span data-stu-id="db907-255">Do: Scroll vertically</span></span>

<span data-ttu-id="db907-256">Os usuários esperam rolagem vertical no Teams (e em outro lugar).</span><span class="sxs-lookup"><span data-stu-id="db907-256">Users expect vertical scrolling in Teams (and elsewhere).</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-dont.png" alt-text="Exemplo mostrando a rolagem horizontal em uma guia na reunião." border="false":::

#### <a name="dont-scroll-horizontally"></a><span data-ttu-id="db907-258">Não: rolar horizontalmente</span><span class="sxs-lookup"><span data-stu-id="db907-258">Don't: Scroll horizontally</span></span>

<span data-ttu-id="db907-259">A rolagem horizontal não é um comportamento esperado no Teams.</span><span class="sxs-lookup"><span data-stu-id="db907-259">Horizontal scrolling isn’t an expected behavior in Teams.</span></span> <span data-ttu-id="db907-260">Outras telas no ambiente de reunião rolam verticalmente.</span><span class="sxs-lookup"><span data-stu-id="db907-260">Other canvases in the meeting environment scroll vertically.</span></span>

   :::column-end:::
:::row-end:::

### <a name="workflows"></a><span data-ttu-id="db907-261">Fluxos de trabalho</span><span class="sxs-lookup"><span data-stu-id="db907-261">Workflows</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-workflow-do.png" alt-text="Exemplo mostrando cenário complexo em uma guia na reunião." border="false":::

#### <a name="do-surface-complex-scenarios-in-the-in-meeting-tab"></a><span data-ttu-id="db907-263">Do: Surface complex scenarios in the in-meeting tab</span><span class="sxs-lookup"><span data-stu-id="db907-263">Do: Surface complex scenarios in the in-meeting tab</span></span>

<span data-ttu-id="db907-264">Se seu aplicativo incluir várias tarefas, recomendamos o uso de uma guia na reunião com um layout de coluna única.</span><span class="sxs-lookup"><span data-stu-id="db907-264">If your app includes multiple tasks, we strongly recommend using an in-meeting tab with a single-column layout.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-workflow-dont.png" alt-text="Exemplo mostrando cenários complexos em uma caixa de diálogo na reunião." border="false":::

#### <a name="dont-make-in-meeting-dialogs-complex"></a><span data-ttu-id="db907-266">Não: tornar as caixas de diálogo na reunião complexas</span><span class="sxs-lookup"><span data-stu-id="db907-266">Don't: Make in-meeting dialogs complex</span></span>

<span data-ttu-id="db907-267">As caixas de diálogo na reunião destinam-se a breves interações.</span><span class="sxs-lookup"><span data-stu-id="db907-267">In-meeting dialogs are intended for brief interactions.</span></span>

   :::column-end:::
:::row-end:::

### <a name="theming"></a><span data-ttu-id="db907-268">Temas</span><span class="sxs-lookup"><span data-stu-id="db907-268">Theming</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-do.png" alt-text="Exemplo mostrando uma extensão de reunião com o tema escuro." border="false":::

#### <a name="do-use-teams-color-tokens"></a><span data-ttu-id="db907-270">Use tokens de cor do Teams</span><span class="sxs-lookup"><span data-stu-id="db907-270">Do: Use Teams color tokens</span></span>

<span data-ttu-id="db907-271">As reuniões do Teams são otimizadas para o modo escuro para ajudar a reduzir o ruído visual e cognitiva para que os usuários possam se concentrar na discussão e no conteúdo compartilhado.</span><span class="sxs-lookup"><span data-stu-id="db907-271">Teams meetings are optimized for dark mode to help reduce visual and cognitive noise so users can focus on the discussion and shared content.</span></span> <span data-ttu-id="db907-272">Saiba como usar <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">tokens de cor (interface do usuário do Fluent).</a></span><span class="sxs-lookup"><span data-stu-id="db907-272">Learn about using <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">color tokens (Fluent UI)</a>.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-dont.png" alt-text="Exemplo mostrando uma extensão de reunião com um tema padrão (claro)." border="false":::

#### <a name="dont-hard-code-hex-values"></a><span data-ttu-id="db907-274">Não: codificar valores hexaxa</span><span class="sxs-lookup"><span data-stu-id="db907-274">Don't: Hard code hex values</span></span>

<span data-ttu-id="db907-275">Se você não usar tokens de cores do Teams, seus designs serão menos escalonáveis e levarão mais tempo para gerenciar.</span><span class="sxs-lookup"><span data-stu-id="db907-275">If you don’t use Teams color tokens, your designs will be less scalable and take more time to manage.</span></span>

   :::column-end:::
:::row-end:::

### <a name="navigation"></a><span data-ttu-id="db907-276">Navegação</span><span class="sxs-lookup"><span data-stu-id="db907-276">Navigation</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-do.png" alt-text="Exemplo mostrando uma extensão de reunião com um botão Voltar." border="false":::

#### <a name="do-have-a-back-button"></a><span data-ttu-id="db907-278">Fazer: ter um botão Voltar</span><span class="sxs-lookup"><span data-stu-id="db907-278">Do: Have a back button</span></span>

<span data-ttu-id="db907-279">Se você tiver mais de uma camada de navegação em uma guia na reunião, os usuários deverão poder voltar para suas exibições anteriores.</span><span class="sxs-lookup"><span data-stu-id="db907-279">If you have more than one layer of navigation in an in-meeting tab, users must be able to go back to their previous views.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-dont.png" alt-text="Exemplo mostrando uma extensão de reunião com dois botões de dismiss." border="false":::

#### <a name="dont-include-another-dismiss-button"></a><span data-ttu-id="db907-281">Não: incluir outro botão de descartar</span><span class="sxs-lookup"><span data-stu-id="db907-281">Don't: Include another dismiss button</span></span>

<span data-ttu-id="db907-282">Fornecer uma opção para fechar o conteúdo da guia na reunião pode causar problemas, pois já existe um botão no título para descartar a própria guia de reunião.</span><span class="sxs-lookup"><span data-stu-id="db907-282">Providing an option to close in-meeting tab content may cause issues since there’s already a button in the header to dismiss the in-meeting tab itself.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-caution.png" alt-text="Exemplo mostrando modais (ou módulos de tarefa) em uma guia na reunião." border="false":::

#### <a name="caution-avoid-modals-within-the-in-meeting-tab"></a><span data-ttu-id="db907-284">Cuidado: evite modais na guia na reunião</span><span class="sxs-lookup"><span data-stu-id="db907-284">Caution: Avoid modals within the in-meeting tab</span></span>

<span data-ttu-id="db907-285">Modais (também conhecidos como módulos de tarefa) na guia já estreita da reunião podem quebrar e ocultar o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="db907-285">Modals (also known as task modules) in the already narrow in-meeting tab might wrap and obscure the content.</span></span>

   :::column-end:::
:::row-end:::

## <a name="validate-your-design"></a><span data-ttu-id="db907-286">Validar seu design</span><span class="sxs-lookup"><span data-stu-id="db907-286">Validate your design</span></span>

<span data-ttu-id="db907-287">Se você planeja publicar seu aplicativo no AppSource, deve entender os problemas de design que normalmente causam falha nos aplicativos durante o envio.</span><span class="sxs-lookup"><span data-stu-id="db907-287">If you plan to publish your app to AppSource, you should understand the design issues that commonly cause apps to fail during submission.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="db907-288">Verificar diretrizes de validação de design</span><span class="sxs-lookup"><span data-stu-id="db907-288">Check design validation guidelines</span></span>](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
