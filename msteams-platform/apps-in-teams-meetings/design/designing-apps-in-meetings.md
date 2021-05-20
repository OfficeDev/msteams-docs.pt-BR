---
title: Projetando sua extensão de reunião
author: heath-hamilton
description: Aprenda a projetar aplicativos em reuniões Teams e obtenha o kit de interface do usuário Microsoft Teams.
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
# <a name="designing-your-microsoft-teams-meeting-extension"></a><span data-ttu-id="657f0-103">Projetando sua extensão de reunião de Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="657f0-103">Designing your Microsoft Teams meeting extension</span></span>

<span data-ttu-id="657f0-104">Você pode criar aplicativos para tornar as reuniões mais produtivas.</span><span class="sxs-lookup"><span data-stu-id="657f0-104">You can create apps to make meetings more productive.</span></span> <span data-ttu-id="657f0-105">Por exemplo, peça às pessoas para concluir uma pesquisa durante uma chamada ou enviar um lembrete rápido que não interrompa o fluxo da reunião.</span><span class="sxs-lookup"><span data-stu-id="657f0-105">For example, ask people to complete a survey during a call or send a quick reminder that doesn’t interrupt the flow of the meeting.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="657f0-106">Kit de Interface do Usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="657f0-106">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="657f0-107">Você pode encontrar diretrizes de design mais abrangentes, incluindo elementos que você pode pegar e modificar conforme necessário, no Microsoft Teams UI Kit.</span><span class="sxs-lookup"><span data-stu-id="657f0-107">You can find more comprehensive design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="657f0-108">Obtenha o Kit de Interface do Usuário do Microsoft Teams (Figma)</span><span class="sxs-lookup"><span data-stu-id="657f0-108">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-meeting-extension"></a><span data-ttu-id="657f0-109">Adicione uma extensão de reunião</span><span class="sxs-lookup"><span data-stu-id="657f0-109">Add a meeting extension</span></span>

<span data-ttu-id="657f0-110">Você pode adicionar uma extensão de reunião antes e durante as reuniões.</span><span class="sxs-lookup"><span data-stu-id="657f0-110">You can add a meeting extension before and during meetings.</span></span> <span data-ttu-id="657f0-111">Você também pode adicionar um aplicativo para uma reunião específica diretamente da loja Teams (AppSource).</span><span class="sxs-lookup"><span data-stu-id="657f0-111">You also can add an app for a specific meeting directly from the Teams store (AppSource).</span></span>

### <a name="add-before-a-meeting"></a><span data-ttu-id="657f0-112">Adicione antes de uma reunião</span><span class="sxs-lookup"><span data-stu-id="657f0-112">Add before a meeting</span></span>

<span data-ttu-id="657f0-113">Nos detalhes da reunião, selecione **Adicionar uma guia +** para abrir o flyout do aplicativo e encontrar aplicativos otimizados para reuniões.</span><span class="sxs-lookup"><span data-stu-id="657f0-113">In the meeting details, select **Add a tab +** to open the app flyout and find apps optimized for meetings.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/add-before-meeting.png" alt-text="Exemplo mostra como adicionar uma extensão de reunião antes de uma reunião." border="false":::

### <a name="add-during-a-meeting"></a><span data-ttu-id="657f0-115">Adicione durante uma reunião</span><span class="sxs-lookup"><span data-stu-id="657f0-115">Add during a meeting</span></span>

Em uma reunião, selecione **Mais** :::image type="icon" source="../../assets/icons/teams-client-more.png":::  >  **Adicionar um aplicativo** e escolha o aplicativo que deseja.

:::image type="content" source="../../assets/images/apps-in-meetings/add-during-meeting.png" alt-text="Exemplo mostra como adicionar uma extensão de reunião durante uma reunião." border="false":::

## <a name="before-a-meeting"></a><span data-ttu-id="657f0-118">Antes de uma reunião</span><span class="sxs-lookup"><span data-stu-id="657f0-118">Before a meeting</span></span>

<span data-ttu-id="657f0-119">Antes da reunião, você pode adicionar conteúdo na guia. O exemplo a seguir mostra uma pergunta de pesquisa que as pessoas responderão durante a chamada.</span><span class="sxs-lookup"><span data-stu-id="657f0-119">Prior to your meeting, you can add content in the tab. The following example shows a draft survey question that people will answer during the call.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/before-meeting-tab.png" alt-text="Exemplo mostra como app conteúdo nos detalhes da reunião antes de uma chamada." border="false":::

### <a name="anatomy-meeting-tab-before-and-after-meetings"></a><span data-ttu-id="657f0-121">Anatomia: Guia de reunião (antes e depois das reuniões)</span><span class="sxs-lookup"><span data-stu-id="657f0-121">Anatomy: Meeting tab (before and after meetings)</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/meeting-details-tab-anatomy.png" alt-text="O exemplo mostra a anatomia estrutural de uma guia de reunião antes e depois de uma reunião." border="false":::

|<span data-ttu-id="657f0-123">Contador</span><span class="sxs-lookup"><span data-stu-id="657f0-123">Counter</span></span>|<span data-ttu-id="657f0-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="657f0-124">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="657f0-125">1</span><span class="sxs-lookup"><span data-stu-id="657f0-125">1</span></span>|<span data-ttu-id="657f0-126">**Nome da guia**: Etiqueta de navegação para sua guia.</span><span class="sxs-lookup"><span data-stu-id="657f0-126">**Tab name**: Navigation label for your tab.</span></span>|
|<span data-ttu-id="657f0-127">2</span><span class="sxs-lookup"><span data-stu-id="657f0-127">2</span></span>|<span data-ttu-id="657f0-128">**Estouro da** guia : Abre ações de guia, como renomear e remover.</span><span class="sxs-lookup"><span data-stu-id="657f0-128">**Tab overflow**: Opens tab actions, such as rename and remove.</span></span>|
|<span data-ttu-id="657f0-129">3</span><span class="sxs-lookup"><span data-stu-id="657f0-129">3</span></span>|<span data-ttu-id="657f0-130">**iframe**: Exibe o conteúdo do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="657f0-130">**iframe**: Displays your app content.</span></span>|

### <a name="designing-with-ui-templates"></a><span data-ttu-id="657f0-131">Projetando com modelos de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="657f0-131">Designing with UI templates</span></span>

<span data-ttu-id="657f0-132">Use um dos seguintes modelos de interface do usuário Teams para ajudar a projetar sua guia de reunião:</span><span class="sxs-lookup"><span data-stu-id="657f0-132">Use one of the following Teams UI templates to help design your meeting tab:</span></span>

* <span data-ttu-id="657f0-133">[Lista](../../concepts/design/design-teams-app-ui-templates.md#list): As listas podem exibir itens relacionados em um formato digitalizável e permitir que os usuários tomem ações em uma lista inteira ou itens individuais.</span><span class="sxs-lookup"><span data-stu-id="657f0-133">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="657f0-134">[Quadro de](../../concepts/design/design-teams-app-ui-templates.md#task-board)tarefas : Um quadro de tarefas, às vezes chamado de placa kanban ou pistas de natação, é uma coleção de cartões frequentemente usados para rastrear o status de itens de trabalho ou bilhetes.</span><span class="sxs-lookup"><span data-stu-id="657f0-134">[Task board](../../concepts/design/design-teams-app-ui-templates.md#task-board): A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span>
* <span data-ttu-id="657f0-135">[Painel](../../concepts/design/design-teams-app-ui-templates.md#dashboard): Um painel de instrumentos é uma tela que contém vários cartões que fornecem uma visão geral de dados ou conteúdo.</span><span class="sxs-lookup"><span data-stu-id="657f0-135">[Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): A dashboard is a canvas containing multiple cards that provide an overview of data or content.</span></span>
* <span data-ttu-id="657f0-136">[Formulário](../../concepts/design/design-teams-app-ui-templates.md#form): Os formulários são para coletar, validar e enviar a entrada do usuário de forma estruturada.</span><span class="sxs-lookup"><span data-stu-id="657f0-136">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="657f0-137">[Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): O modelo de estado vazio pode ser usado para muitos cenários, incluindo login, experiências de primeira execução, mensagens de erro e muito mais.</span><span class="sxs-lookup"><span data-stu-id="657f0-137">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>
* <span data-ttu-id="657f0-138">[Navegação à esquerda](../../concepts/design/design-teams-app-ui-templates.md#left-nav): O modelo de navegação à esquerda pode ajudar se sua guia precisar de alguma navegação.</span><span class="sxs-lookup"><span data-stu-id="657f0-138">[Left nav](../../concepts/design/design-teams-app-ui-templates.md#left-nav): The left nav template can help if your tab requires some navigation.</span></span> <span data-ttu-id="657f0-139">Em geral, você deve manter a navegação de controle ao mínimo.</span><span class="sxs-lookup"><span data-stu-id="657f0-139">In general, you should keep tab navigation to a minimum.</span></span>

## <a name="use-an-in-meeting-tab"></a><span data-ttu-id="657f0-140">Use uma guia de reunião</span><span class="sxs-lookup"><span data-stu-id="657f0-140">Use an in-meeting tab</span></span>

<span data-ttu-id="657f0-141">A guia de reunião é uma tela para aumentar a colaboração durante as reuniões.</span><span class="sxs-lookup"><span data-stu-id="657f0-141">The in-meeting tab is a canvas for augmenting collaboration during meetings.</span></span> <span data-ttu-id="657f0-142">Os participantes podem ver e interagir com o conteúdo do aplicativo em um espaço dedicado fora do palco de reuniões através de visualizações compartilhadas ou baseadas em papéis.</span><span class="sxs-lookup"><span data-stu-id="657f0-142">Attendees can see and interact with app content in a dedicated space outside the meeting stage through shared or role-based views.</span></span>

### <a name="use-cases"></a><span data-ttu-id="657f0-143">Casos de uso</span><span class="sxs-lookup"><span data-stu-id="657f0-143">Use cases</span></span>

<span data-ttu-id="657f0-144">As pessoas podem usar a guia de reunião para:</span><span class="sxs-lookup"><span data-stu-id="657f0-144">People might use the in-meeting tab to:</span></span>

* <span data-ttu-id="657f0-145">Forneça feedback detalhado.</span><span class="sxs-lookup"><span data-stu-id="657f0-145">Provide detailed feedback.</span></span> <span data-ttu-id="657f0-146">Por exemplo, avalie um candidato a emprego.</span><span class="sxs-lookup"><span data-stu-id="657f0-146">For example, evaluate a job candidate.</span></span>
* <span data-ttu-id="657f0-147">Crie uma enquete, pesquisa ou item de tarefa para os participantes da reunião.</span><span class="sxs-lookup"><span data-stu-id="657f0-147">Create a poll, survey, or task item for the meeting participants.</span></span>
* <span data-ttu-id="657f0-148">Notas de exibição relevantes para a reunião.</span><span class="sxs-lookup"><span data-stu-id="657f0-148">Display notes relevant to the meeting.</span></span> <span data-ttu-id="657f0-149">Por exemplo, informações sobre um lead de vendas.</span><span class="sxs-lookup"><span data-stu-id="657f0-149">For example, information about a sales lead.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-tab.png" alt-text="O exemplo mostra como você pode apresentar o conteúdo da enquete em uma guia de reunião." border="false":::

### <a name="anatomy-in-meeting-tab"></a><span data-ttu-id="657f0-151">Anatomia: Guia de encontros</span><span class="sxs-lookup"><span data-stu-id="657f0-151">Anatomy: In-meeting tab</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-anatomy.png" alt-text="O exemplo mostra a anatomia estrutural de uma guia de encontro." border="false":::

|<span data-ttu-id="657f0-153">Contador</span><span class="sxs-lookup"><span data-stu-id="657f0-153">Counter</span></span>|<span data-ttu-id="657f0-154">Descrição</span><span class="sxs-lookup"><span data-stu-id="657f0-154">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="657f0-155">1</span><span class="sxs-lookup"><span data-stu-id="657f0-155">1</span></span>|<span data-ttu-id="657f0-156">**Ícone do aplicativo (selecionado)**: logotipo de aplicativo transparente de 16 pixels.</span><span class="sxs-lookup"><span data-stu-id="657f0-156">**App icon (selected)**: 16-pixel transparent app logo.</span></span>|
|<span data-ttu-id="657f0-157">2</span><span class="sxs-lookup"><span data-stu-id="657f0-157">2</span></span>|<span data-ttu-id="657f0-158">**Nome do aplicativo**</span><span class="sxs-lookup"><span data-stu-id="657f0-158">**App name**</span></span>|
|<span data-ttu-id="657f0-159">3</span><span class="sxs-lookup"><span data-stu-id="657f0-159">3</span></span>|<span data-ttu-id="657f0-160">**Cabeçalho**: Inclui o nome do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="657f0-160">**Header**: Includes your app name.</span></span>|
|<span data-ttu-id="657f0-161">4 </span><span class="sxs-lookup"><span data-stu-id="657f0-161">4</span></span>|<span data-ttu-id="657f0-162">**Botão de fechamento**: Dispensa a guia. Use sempre o ícone de fechamento superior direito em vez de uma ação no rodapé.</span><span class="sxs-lookup"><span data-stu-id="657f0-162">**Close button**: Dismisses the tab. Always use the upper-right close icon instead of an action in the footer.</span></span>|
|<span data-ttu-id="657f0-163">5 </span><span class="sxs-lookup"><span data-stu-id="657f0-163">5</span></span>|<span data-ttu-id="657f0-164">**Barra de notificação**: Os alertas de erro são exibidos diretamente abaixo do cabeçalho e empurram o conteúdo do iframe para baixo em 20 pixels.</span><span class="sxs-lookup"><span data-stu-id="657f0-164">**Notification bar**: Error alerts display directly below the header and push the iframe content down by 20 pixels.</span></span>|
|<span data-ttu-id="657f0-165">6 </span><span class="sxs-lookup"><span data-stu-id="657f0-165">6</span></span>|<span data-ttu-id="657f0-166">**iframe**: Exibe o conteúdo do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="657f0-166">**iframe**: Displays your app content.</span></span>|

### <a name="spacing"></a><span data-ttu-id="657f0-167">Espaçamento</span><span class="sxs-lookup"><span data-stu-id="657f0-167">Spacing</span></span>

<span data-ttu-id="657f0-168">Otimize sua guia de reunião para caber borda a ponta dentro da área de iframe de 280 pixels de largura.</span><span class="sxs-lookup"><span data-stu-id="657f0-168">Optimize your in-meeting tab to fit edge-to-edge within the 280 pixel-wide iframe area.</span></span> <span data-ttu-id="657f0-169">Há 20 pixels de preenchimento nos lados esquerdo e direito do iframe e entre o cabeçalho da guia.</span><span class="sxs-lookup"><span data-stu-id="657f0-169">There are 20 pixels of padding on the left and right sides of the iframe and between the tab header.</span></span> <span data-ttu-id="657f0-170">O iframe está sangrando até a parte inferior da guia.</span><span class="sxs-lookup"><span data-stu-id="657f0-170">The iframe is full bleed to the bottom of the tab.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-spacing.png" alt-text="Exemplo mostra dimensões de espaçamento de guias em reunião." border="false":::

### <a name="scrolling"></a><span data-ttu-id="657f0-172">Rolagem</span><span class="sxs-lookup"><span data-stu-id="657f0-172">Scrolling</span></span>

<span data-ttu-id="657f0-173">O conteúdo de iframe deve rolar verticalmente.</span><span class="sxs-lookup"><span data-stu-id="657f0-173">Iframe contents should scroll vertically.</span></span> <span data-ttu-id="657f0-174">Você só pode ver o conteúdo para o qual rolou (nada acima ou abaixo).</span><span class="sxs-lookup"><span data-stu-id="657f0-174">You can only see the content you've scrolled to (nothing above or below).</span></span> <span data-ttu-id="657f0-175">A barra de rolagem faz parte do conteúdo do iframe.</span><span class="sxs-lookup"><span data-stu-id="657f0-175">The scrollbar is part of the iframe content.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-scrolling.png" alt-text="O exemplo mostra como a guia de reunião rola." border="false":::

### <a name="navigation"></a><span data-ttu-id="657f0-177">Navegação</span><span class="sxs-lookup"><span data-stu-id="657f0-177">Navigation</span></span>

<span data-ttu-id="657f0-178">Para cenários com camadas de navegação ou conteúdo pesado, recomendamos permitir que os usuários naveguem até uma camada secundária.</span><span class="sxs-lookup"><span data-stu-id="657f0-178">For scenarios with navigation layers or heavy content, we recommend allowing users to navigate to a secondary layer.</span></span> <span data-ttu-id="657f0-179">Os usuários devem ser capazes de voltar à camada anterior.</span><span class="sxs-lookup"><span data-stu-id="657f0-179">Users must be able to go back to the previous layer.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav.png" alt-text="Exemplo mostra navegação em reunião." border="false":::

## <a name="use-an-in-meeting-dialog"></a><span data-ttu-id="657f0-181">Use um diálogo de reunião</span><span class="sxs-lookup"><span data-stu-id="657f0-181">Use an in-meeting dialog</span></span>

<span data-ttu-id="657f0-182">Diálogos em reunião são exibidos na Teams fase de reunião.</span><span class="sxs-lookup"><span data-stu-id="657f0-182">In-meeting dialogs display on the Teams meeting stage.</span></span> <span data-ttu-id="657f0-183">Eles exigem a atenção, confirmação ou interação do usuário, mas são sutis e não interrompem a reunião.</span><span class="sxs-lookup"><span data-stu-id="657f0-183">They require a user's attention, confirmation, or interaction but are subtle and don't interrupt the meeting.</span></span> <span data-ttu-id="657f0-184">Você deve usá-los com moderação e para cenários que sejam leves e orientados para tarefas.</span><span class="sxs-lookup"><span data-stu-id="657f0-184">You should use these sparingly and for scenarios that are light and task oriented.</span></span>

### <a name="use-cases"></a><span data-ttu-id="657f0-185">Casos de uso</span><span class="sxs-lookup"><span data-stu-id="657f0-185">Use cases</span></span>

<span data-ttu-id="657f0-186">Diálogos de reunião são acionados por um usuário (como o organizador da reunião) que pode querer que os participantes:</span><span class="sxs-lookup"><span data-stu-id="657f0-186">In-meeting dialogs are triggered by a user (such as the meeting organizer) who might want participants to:</span></span>

* <span data-ttu-id="657f0-187">Fornecer um breve feedback</span><span class="sxs-lookup"><span data-stu-id="657f0-187">Provide brief feedback</span></span>
* <span data-ttu-id="657f0-188">Faça uma pequena pesquisa ou enquete</span><span class="sxs-lookup"><span data-stu-id="657f0-188">Take a short survey or poll</span></span>
* <span data-ttu-id="657f0-189">Enviar aprovações</span><span class="sxs-lookup"><span data-stu-id="657f0-189">Submit approvals</span></span>
* <span data-ttu-id="657f0-190">Receber lembretes</span><span class="sxs-lookup"><span data-stu-id="657f0-190">Get reminders</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-dialog.png" alt-text="O exemplo mostra como você pode usar um diálogo de reunião." border="false":::

### <a name="anatomy-in-meeting-dialog"></a><span data-ttu-id="657f0-192">Anatomia: Diálogo de encontro</span><span class="sxs-lookup"><span data-stu-id="657f0-192">Anatomy: In-meeting dialog</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-anatomy.png" alt-text="O exemplo mostra a anatomia estrutural de um diálogo em reunião." border="false":::

|<span data-ttu-id="657f0-194">Contador</span><span class="sxs-lookup"><span data-stu-id="657f0-194">Counter</span></span>|<span data-ttu-id="657f0-195">Descrição</span><span class="sxs-lookup"><span data-stu-id="657f0-195">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="657f0-196">1</span><span class="sxs-lookup"><span data-stu-id="657f0-196">1</span></span>|<span data-ttu-id="657f0-197">**Cabeçalho**: Inclui ícone de aplicativo, nome, string de ação e ícone de fechamento.</span><span class="sxs-lookup"><span data-stu-id="657f0-197">**Header**: Includes app icon, name, action string, and close icon.</span></span>|
|<span data-ttu-id="657f0-198">2</span><span class="sxs-lookup"><span data-stu-id="657f0-198">2</span></span>|<span data-ttu-id="657f0-199">**iframe**: Exibe o conteúdo do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="657f0-199">**iframe**: Displays your app content.</span></span>|

### <a name="anatomy-in-meeting-dialog-header"></a><span data-ttu-id="657f0-200">Anatomia: Cabeçalho de diálogo de reunião</span><span class="sxs-lookup"><span data-stu-id="657f0-200">Anatomy: In-meeting dialog header</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-header-anatomy.png" alt-text="O exemplo mostra a anatomia estrutural de um cabeçalho de diálogo em reunião." border="false":::

<span data-ttu-id="657f0-202">Há duas variantes de cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="657f0-202">There are two header variants.</span></span> <span data-ttu-id="657f0-203">Quando possível, use a variante com o avatar para reforçar que o diálogo vem de uma pessoa.</span><span class="sxs-lookup"><span data-stu-id="657f0-203">When possible, use the variant with the avatar to reinforce that the dialog is coming from a person.</span></span>

|<span data-ttu-id="657f0-204">Contador</span><span class="sxs-lookup"><span data-stu-id="657f0-204">Counter</span></span>|<span data-ttu-id="657f0-205">Descrição</span><span class="sxs-lookup"><span data-stu-id="657f0-205">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="657f0-206">1</span><span class="sxs-lookup"><span data-stu-id="657f0-206">1</span></span>|<span data-ttu-id="657f0-207">**Avatar**: Pessoa que inicia o diálogo de reunião.</span><span class="sxs-lookup"><span data-stu-id="657f0-207">**Avatar**: Person who initiates the in-meeting dialog.</span></span>|
|<span data-ttu-id="657f0-208">2</span><span class="sxs-lookup"><span data-stu-id="657f0-208">2</span></span>|<span data-ttu-id="657f0-209">**ícone de aplicativo**</span><span class="sxs-lookup"><span data-stu-id="657f0-209">**App icon**</span></span>|
|<span data-ttu-id="657f0-210">3</span><span class="sxs-lookup"><span data-stu-id="657f0-210">3</span></span>|<span data-ttu-id="657f0-211">**Nome do aplicativo**</span><span class="sxs-lookup"><span data-stu-id="657f0-211">**App name**</span></span>|
|<span data-ttu-id="657f0-212">4 </span><span class="sxs-lookup"><span data-stu-id="657f0-212">4</span></span>|<span data-ttu-id="657f0-213">**Botão de fechamento**: Dispensa o diálogo.</span><span class="sxs-lookup"><span data-stu-id="657f0-213">**Close button**: Dismisses the dialog.</span></span>|
|<span data-ttu-id="657f0-214">5 </span><span class="sxs-lookup"><span data-stu-id="657f0-214">5</span></span>|<span data-ttu-id="657f0-215">**Cadeia de** ação : Normalmente descreve quem iniciou o diálogo.</span><span class="sxs-lookup"><span data-stu-id="657f0-215">**Action string**: Typically describes who initiated the dialog.</span></span>|

### <a name="responsive-behavior"></a><span data-ttu-id="657f0-216">Comportamento dinâmico</span><span class="sxs-lookup"><span data-stu-id="657f0-216">Responsive behavior</span></span>

<span data-ttu-id="657f0-217">Diálogos de encontro podem variar de tamanho para explicar diferentes cenários.</span><span class="sxs-lookup"><span data-stu-id="657f0-217">In-meeting dialogs can vary in size to account for different scenarios.</span></span> <span data-ttu-id="657f0-218">Certifique-se de manter o preenchimento e os tamanhos dos componentes.</span><span class="sxs-lookup"><span data-stu-id="657f0-218">Make sure to maintain padding and component sizes.</span></span>

* <span data-ttu-id="657f0-219">**Largura**: Você pode especificar a largura do iframe da caixa de diálogo em qualquer lugar dentro da faixa de tamanho suportada.</span><span class="sxs-lookup"><span data-stu-id="657f0-219">**Width**: You can specify the width of the dialog's iframe anywhere within the supported size range.</span></span>
* <span data-ttu-id="657f0-220">**Altura**: Você pode especificar a altura do iframe da caixa de diálogo em qualquer lugar dentro da faixa de tamanho suportada.</span><span class="sxs-lookup"><span data-stu-id="657f0-220">**Height**: You can specify the height of the dialog's iframe anywhere within the supported size range.</span></span> <span data-ttu-id="657f0-221">Você também pode permitir que os usuários rolem verticalmente se o conteúdo do aplicativo exceder a altura máxima.</span><span class="sxs-lookup"><span data-stu-id="657f0-221">You also can allow users to scroll vertically if your app content exceeds the maximum height.</span></span>

<span data-ttu-id="657f0-222">Para implementar, especifique a largura e a altura usando a [`externalResourceUrl`](~/apps-in-teams-meetings/create-apps-for-teams-meetings.md#notificationsignal-api) chave.</span><span class="sxs-lookup"><span data-stu-id="657f0-222">To implement, specify the width and height using the [`externalResourceUrl`](~/apps-in-teams-meetings/create-apps-for-teams-meetings.md#notificationsignal-api) key.</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-responsive.png" alt-text="O exemplo mostra o diálogo de reunião. Largura: Min-280 pixels (248 pixels iframe). Max-460 pixels (428 pixels iframe). Altura: 300 pixels (iframe)." border="false":::

## <a name="after-a-meeting"></a><span data-ttu-id="657f0-224">Após uma reunião</span><span class="sxs-lookup"><span data-stu-id="657f0-224">After a meeting</span></span>

<span data-ttu-id="657f0-225">Você pode voltar a uma reunião depois que terminar e visualizar o conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="657f0-225">You can go back to a meeting after it ends and view app content.</span></span> <span data-ttu-id="657f0-226">Neste exemplo, o organizador da reunião pode analisar os resultados das pesquisas na guia **Contoso.** (Nota: Do ponto de vista do design, não há diferença entre a experiência de guia pré e pós-reunião.)</span><span class="sxs-lookup"><span data-stu-id="657f0-226">In this example, the meeting organizer can look at poll results in the **Contoso** tab. (Note: From a design standpoint, there's no difference between a the pre- and post-meeting tab experience.)</span></span>

:::image type="content" source="../../assets/images/apps-in-meetings/post-meeting-experience.png" alt-text="A ilustração do exemplo mostra uma guia pós-reunião." border="false":::

## <a name="best-practices"></a><span data-ttu-id="657f0-228">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="657f0-228">Best practices</span></span>

<span data-ttu-id="657f0-229">Use essas recomendações para criar uma experiência de aplicativo de qualidade.</span><span class="sxs-lookup"><span data-stu-id="657f0-229">Use these recommendations to create a quality app experience.</span></span>

### <a name="interactions"></a><span data-ttu-id="657f0-230">Interações</span><span class="sxs-lookup"><span data-stu-id="657f0-230">Interactions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-do.png" alt-text="Exemplo mostrando como limitar o número de interações." border="false":::

#### <a name="do-limit-the-number-of-interactions"></a><span data-ttu-id="657f0-232">Faça: Limite o número de interações</span><span class="sxs-lookup"><span data-stu-id="657f0-232">Do: Limit the number of interactions</span></span>

<span data-ttu-id="657f0-233">Para diálogos de encontro, remova conteúdo desnecessário que não ajude os usuários a realizar algo rapidamente.</span><span class="sxs-lookup"><span data-stu-id="657f0-233">For in-meeting dialogs, remove unnecessary content that doesn't help users accomplish something quickly.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-dont.png" alt-text="Exemplo mostrando como não introduzir elementos desnecessários." border="false":::

#### <a name="dont-introduce-unnecessary-elements"></a><span data-ttu-id="657f0-235">Não: Introduza elementos desnecessários</span><span class="sxs-lookup"><span data-stu-id="657f0-235">Don't: Introduce unnecessary elements</span></span>

<span data-ttu-id="657f0-236">Um único diálogo de encontro com múltiplas interações pode distrair a chamada.</span><span class="sxs-lookup"><span data-stu-id="657f0-236">A single in-meeting dialog with multiple interactions can distract from the call.</span></span>

   :::column-end:::
:::row-end:::

### <a name="layout"></a><span data-ttu-id="657f0-237">Layout</span><span class="sxs-lookup"><span data-stu-id="657f0-237">Layout</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-do.png" alt-text="Exemplo mostrando como você deve usar um layout de diálogo de uma única coluna." border="false":::

#### <a name="do-use-a-single-column-dialog-layout"></a><span data-ttu-id="657f0-239">Faça: Use um layout de diálogo de uma única coluna</span><span class="sxs-lookup"><span data-stu-id="657f0-239">Do: Use a single-column dialog layout</span></span>

<span data-ttu-id="657f0-240">Como os diálogos estão no centro da fase de reunião, a conclusão da tarefa deve ser rápida e simples para evitar a frustração do usuário.</span><span class="sxs-lookup"><span data-stu-id="657f0-240">Since the dialogs are at the center of the meeting stage, task completion should be fast and simple to avoid user frustration.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-dont.png" alt-text="Exemplo mostrando que você não deve bagunçar o espaço de uma extensão de reunião." border="false":::

#### <a name="dont-clutter-the-space"></a><span data-ttu-id="657f0-242">Não: Desordene o espaço</span><span class="sxs-lookup"><span data-stu-id="657f0-242">Don't: Clutter the space</span></span>

<span data-ttu-id="657f0-243">Conteúdo denso ou excessivamente estruturado pode ser perturbador e avassalador, especialmente durante uma reunião.</span><span class="sxs-lookup"><span data-stu-id="657f0-243">Dense or overly structured content can be distracting and overwhelming, especially during a meeting.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-do.png" alt-text="Exemplo mostrando um layout de guia de uma única coluna." border="false":::

#### <a name="do-use-a-single-column-tab-layout"></a><span data-ttu-id="657f0-245">Faça: Use um layout de guia de uma única coluna</span><span class="sxs-lookup"><span data-stu-id="657f0-245">Do: Use a single-column tab layout</span></span>

<span data-ttu-id="657f0-246">Dada a natureza estreita da guia de reunião, recomendamos fortemente exibir o conteúdo em uma única coluna.</span><span class="sxs-lookup"><span data-stu-id="657f0-246">Given the in-meeting tab's narrow nature, we strongly recommend displaying the contents in a single column.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-dont.png" alt-text="Exemplo mostrando uma guia com várias colunas." border="false":::

#### <a name="dont-use-multiple-columns"></a><span data-ttu-id="657f0-248">Não: Use várias colunas</span><span class="sxs-lookup"><span data-stu-id="657f0-248">Don't: Use multiple columns</span></span>

<span data-ttu-id="657f0-249">Devido ao espaço limitado da guia de reunião, não são recomendados layouts com mais de uma coluna.</span><span class="sxs-lookup"><span data-stu-id="657f0-249">Due to the limited space of the in-meeting tab, layouts with more than one column aren’t recommended.</span></span>

   :::column-end:::
:::row-end:::

### <a name="controls"></a><span data-ttu-id="657f0-250">Controles</span><span class="sxs-lookup"><span data-stu-id="657f0-250">Controls</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-do.png" alt-text="Exemplo mostrando como alinhar os controles primários de direita." border="false":::

#### <a name="do-right-align-the-primary-action"></a><span data-ttu-id="657f0-252">Faça: Alinhar direito a ação primária</span><span class="sxs-lookup"><span data-stu-id="657f0-252">Do: Right align the primary action</span></span>

<span data-ttu-id="657f0-253">Recomendamos posicionar a ação mais visualmente pesada para o local mais certo.</span><span class="sxs-lookup"><span data-stu-id="657f0-253">We recommend positioning the most visually heavy action to the right-most location.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-dont.png" alt-text="Exemplo mostrando como você não deve deixar de alinhar controles primários." border="false":::

#### <a name="dont-left-or-center-align-actions"></a><span data-ttu-id="657f0-255">Não: Ações de alinhamento de esquerda ou centro</span><span class="sxs-lookup"><span data-stu-id="657f0-255">Don't: Left or center align actions</span></span>

<span data-ttu-id="657f0-256">Isso se desvia do padrão Teams padrão para colocação de controle em um diálogo e pode entrar em conflito com um diálogo atrás do topo.</span><span class="sxs-lookup"><span data-stu-id="657f0-256">This deviates from the standard Teams pattern for control placement in a dialog and may conflict with a dialog behind the top one.</span></span>

   :::column-end:::
:::row-end:::

### <a name="scroll"></a><span data-ttu-id="657f0-257">Rolar</span><span class="sxs-lookup"><span data-stu-id="657f0-257">Scroll</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-do.png" alt-text="Exemplo mostrando rolagem vertical em uma guia de reunião." border="false":::

#### <a name="do-scroll-vertically"></a><span data-ttu-id="657f0-259">Faça: Role verticalmente</span><span class="sxs-lookup"><span data-stu-id="657f0-259">Do: Scroll vertically</span></span>

<span data-ttu-id="657f0-260">Os usuários esperam rolagem vertical em Teams (e em outros lugares).</span><span class="sxs-lookup"><span data-stu-id="657f0-260">Users expect vertical scrolling in Teams (and elsewhere).</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-dont.png" alt-text="Exemplo mostrando rolagem horizontal em uma guia de reunião." border="false":::

#### <a name="dont-scroll-horizontally"></a><span data-ttu-id="657f0-262">Não: Role horizontalmente</span><span class="sxs-lookup"><span data-stu-id="657f0-262">Don't: Scroll horizontally</span></span>

<span data-ttu-id="657f0-263">A rolagem horizontal não é um comportamento esperado em Teams.</span><span class="sxs-lookup"><span data-stu-id="657f0-263">Horizontal scrolling isn’t an expected behavior in Teams.</span></span> <span data-ttu-id="657f0-264">Outras telas no ambiente de reunião rolam verticalmente.</span><span class="sxs-lookup"><span data-stu-id="657f0-264">Other canvases in the meeting environment scroll vertically.</span></span>

   :::column-end:::
:::row-end:::

### <a name="workflows"></a><span data-ttu-id="657f0-265">Fluxos de trabalho</span><span class="sxs-lookup"><span data-stu-id="657f0-265">Workflows</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-workflow-do.png" alt-text="Exemplo mostrando cenário complexo em uma guia de reunião." border="false":::

#### <a name="do-surface-complex-scenarios-in-the-in-meeting-tab"></a><span data-ttu-id="657f0-267">Faça: Cenários complexos de superfície na guia de reunião</span><span class="sxs-lookup"><span data-stu-id="657f0-267">Do: Surface complex scenarios in the in-meeting tab</span></span>

<span data-ttu-id="657f0-268">Se o seu aplicativo incluir várias tarefas, recomendamos fortemente o uso de uma guia de reunião com um layout de uma única coluna.</span><span class="sxs-lookup"><span data-stu-id="657f0-268">If your app includes multiple tasks, we strongly recommend using an in-meeting tab with a single-column layout.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-workflow-dont.png" alt-text="Exemplo mostrando cenários complexos em um diálogo presencial." border="false":::

#### <a name="dont-make-in-meeting-dialogs-complex"></a><span data-ttu-id="657f0-270">Não: Torne os diálogos em reunião complexos</span><span class="sxs-lookup"><span data-stu-id="657f0-270">Don't: Make in-meeting dialogs complex</span></span>

<span data-ttu-id="657f0-271">Diálogos de reunião destinam-se a interações breves.</span><span class="sxs-lookup"><span data-stu-id="657f0-271">In-meeting dialogs are intended for brief interactions.</span></span>

   :::column-end:::
:::row-end:::

### <a name="theming"></a><span data-ttu-id="657f0-272">Temas</span><span class="sxs-lookup"><span data-stu-id="657f0-272">Theming</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-do.png" alt-text="Exemplo mostrando uma extensão de reunião com o tema escuro." border="false":::

#### <a name="do-use-teams-color-tokens"></a><span data-ttu-id="657f0-274">Faça: Use tokens de cor Teams</span><span class="sxs-lookup"><span data-stu-id="657f0-274">Do: Use Teams color tokens</span></span>

<span data-ttu-id="657f0-275">Teams reuniões são otimizadas para o modo escuro para ajudar a reduzir o ruído visual e cognitivo para que os usuários possam se concentrar na discussão e no conteúdo compartilhado.</span><span class="sxs-lookup"><span data-stu-id="657f0-275">Teams meetings are optimized for dark mode to help reduce visual and cognitive noise so users can focus on the discussion and shared content.</span></span> <span data-ttu-id="657f0-276">Saiba mais sobre o uso <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">de tokens de cores (Fluent UI)</a>.</span><span class="sxs-lookup"><span data-stu-id="657f0-276">Learn about using <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">color tokens (Fluent UI)</a>.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-dont.png" alt-text="Exemplo mostrando uma extensão de reunião com um tema padrão (leve)." border="false":::

#### <a name="dont-hard-code-hex-values"></a><span data-ttu-id="657f0-278">Não: Valores hexax de código rígido</span><span class="sxs-lookup"><span data-stu-id="657f0-278">Don't: Hard code hex values</span></span>

<span data-ttu-id="657f0-279">Se você não usar Teams tokens de cor, seus designs serão menos escaláveis e levarão mais tempo para gerenciar.</span><span class="sxs-lookup"><span data-stu-id="657f0-279">If you don’t use Teams color tokens, your designs will be less scalable and take more time to manage.</span></span>

   :::column-end:::
:::row-end:::

### <a name="navigation"></a><span data-ttu-id="657f0-280">Navegação</span><span class="sxs-lookup"><span data-stu-id="657f0-280">Navigation</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-do.png" alt-text="Exemplo mostrando uma extensão de reunião com um botão traseiro." border="false":::

#### <a name="do-have-a-back-button"></a><span data-ttu-id="657f0-282">Faça: Tenha um botão traseiro</span><span class="sxs-lookup"><span data-stu-id="657f0-282">Do: Have a back button</span></span>

<span data-ttu-id="657f0-283">Se você tiver mais de uma camada de navegação em uma guia de reunião, os usuários devem ser capazes de voltar às suas visualizações anteriores.</span><span class="sxs-lookup"><span data-stu-id="657f0-283">If you have more than one layer of navigation in an in-meeting tab, users must be able to go back to their previous views.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-dont.png" alt-text="Exemplo mostrando uma extensão de reunião com dois botões de demissão." border="false":::

#### <a name="dont-include-another-dismiss-button"></a><span data-ttu-id="657f0-285">Não: Inclua outro botão de descarte</span><span class="sxs-lookup"><span data-stu-id="657f0-285">Don't: Include another dismiss button</span></span>

<span data-ttu-id="657f0-286">Fornecer uma opção para fechar o conteúdo da guia de reunião pode causar problemas, uma vez que já há um botão no cabeçalho para descartar a própria guia de reunião.</span><span class="sxs-lookup"><span data-stu-id="657f0-286">Providing an option to close in-meeting tab content may cause issues since there’s already a button in the header to dismiss the in-meeting tab itself.</span></span>

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-caution.png" alt-text="Exemplo mostrando modais (ou módulos de tarefa) dentro de uma guia de reunião." border="false":::

#### <a name="caution-avoid-modals-within-the-in-meeting-tab"></a><span data-ttu-id="657f0-288">Atenção: Evite modais dentro da guia de reunião</span><span class="sxs-lookup"><span data-stu-id="657f0-288">Caution: Avoid modals within the in-meeting tab</span></span>

<span data-ttu-id="657f0-289">Modais (também conhecidos como módulos de tarefa) na já estreita guia de reunião podem embrulhar e obscurecer o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="657f0-289">Modals (also known as task modules) in the already narrow in-meeting tab might wrap and obscure the content.</span></span>

   :::column-end:::
:::row-end:::
