---
title: Projetando sua guia para área de trabalho e Web
description: Saiba como projetar uma guia Teams (área de trabalho e Web) e obter o Microsoft Teams de interface do usuário.
author: heath-hamilton
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 9dc5489f4a6a4c6f0e1188250a9e2a9bc5793690
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101846"
---
# <a name="designing-your-tab-for-microsoft-teams-desktop-and-web"></a><span data-ttu-id="8ddba-103">Projetando sua guia para Microsoft Teams desktop e web</span><span class="sxs-lookup"><span data-stu-id="8ddba-103">Designing your tab for Microsoft Teams desktop and web</span></span>

<span data-ttu-id="8ddba-104">Uma guia é uma tela grande para seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="8ddba-104">A tab is a large canvas for your content.</span></span> <span data-ttu-id="8ddba-105">Para orientar o design do aplicativo, as informações a seguir descrevem e ilustram como as pessoas podem adicionar, usar e gerenciar guias no Teams.</span><span class="sxs-lookup"><span data-stu-id="8ddba-105">To guide your app design, the following information describes and illustrates how people can add, use, and manage tabs in Teams.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="8ddba-106">Kit de Interface do Usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="8ddba-106">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="8ddba-107">Você pode encontrar diretrizes abrangentes de design de guia, incluindo elementos que você pode pegar e modificar conforme necessário, no Kit Microsoft Teams interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="8ddba-107">You can find comprehensive tab design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span> <span data-ttu-id="8ddba-108">O kit de interface do usuário também tem tópicos essenciais, como acessibilidade e tamanho responsivo que não são abordados aqui.</span><span class="sxs-lookup"><span data-stu-id="8ddba-108">The UI kit also has essential topics such as accessibility and responsive sizing that aren't covered here.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8ddba-109">Obtenha o Kit de Interface do Usuário do Microsoft Teams (Figma)</span><span class="sxs-lookup"><span data-stu-id="8ddba-109">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-tab"></a><span data-ttu-id="8ddba-110">Adicionar uma guia</span><span class="sxs-lookup"><span data-stu-id="8ddba-110">Add a tab</span></span>

<span data-ttu-id="8ddba-111">Você pode adicionar uma guia do Teams (AppSource) ou em um dos seguintes contextos:</span><span class="sxs-lookup"><span data-stu-id="8ddba-111">You can add a tab from the Teams store (AppSource) or in one of the following contexts:</span></span>

* <span data-ttu-id="8ddba-112">Chat</span><span class="sxs-lookup"><span data-stu-id="8ddba-112">Chat</span></span>
* <span data-ttu-id="8ddba-113">Canal</span><span class="sxs-lookup"><span data-stu-id="8ddba-113">Channel</span></span>
* <span data-ttu-id="8ddba-114">Reunião (antes, durante ou após a reunião)</span><span class="sxs-lookup"><span data-stu-id="8ddba-114">Meeting (before, during, or after the meeting)</span></span>

<span data-ttu-id="8ddba-115">O exemplo a seguir mostra como uma guia é adicionada a um canal.</span><span class="sxs-lookup"><span data-stu-id="8ddba-115">The following example shows how a tab is added in a channel.</span></span>

:::image type="content" source="../../assets/images/tabs/design-add-tab.png" alt-text="Exemplo mostra uma guia sendo adicionada a um canal." border="false":::

## <a name="set-up-a-tab"></a><span data-ttu-id="8ddba-117">Configurar uma guia</span><span class="sxs-lookup"><span data-stu-id="8ddba-117">Set up a tab</span></span>

<span data-ttu-id="8ddba-118">Há um curto processo de instalação para adicionar um aplicativo como canal, chat ou guia de reunião. A experiência é em grande parte com você.</span><span class="sxs-lookup"><span data-stu-id="8ddba-118">There's a short setup process to add an app as a channel, chat, or meeting tab. The experience is largely up to you.</span></span> <span data-ttu-id="8ddba-119">Por exemplo, você pode ter uma descrição de como usar o aplicativo e algumas configurações opcionais.</span><span class="sxs-lookup"><span data-stu-id="8ddba-119">For example, you could have a description of how to use the app and some optional settings.</span></span> <span data-ttu-id="8ddba-120">Inclua uma etapa de login aqui se você precisar autenticar usuários.</span><span class="sxs-lookup"><span data-stu-id="8ddba-120">Include a sign-in step here if you need to authenticate users.</span></span>

### <a name="tab-configuration-modal"></a><span data-ttu-id="8ddba-121">Modal de configuração de tabulação</span><span class="sxs-lookup"><span data-stu-id="8ddba-121">Tab configuration modal</span></span>

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-config.png" alt-text="Exemplo mostra um modal de configuração de tabulação." border="false":::

### <a name="anatomy-tab-configuration-modal"></a><span data-ttu-id="8ddba-123">Anatomia: modal de configuração de tabulação</span><span class="sxs-lookup"><span data-stu-id="8ddba-123">Anatomy: Tab configuration modal</span></span>

:::image type="content" source="../../assets/images/tabs/test.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de um modal de configuração de tabulação." border="false":::

|<span data-ttu-id="8ddba-125">Contador</span><span class="sxs-lookup"><span data-stu-id="8ddba-125">Counter</span></span>|<span data-ttu-id="8ddba-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="8ddba-126">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="8ddba-127">1</span><span class="sxs-lookup"><span data-stu-id="8ddba-127">1</span></span>|<span data-ttu-id="8ddba-128">**Logotipo do aplicativo**: logotipo completo do aplicativo de cores do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8ddba-128">**App logo**: Full color app logo of your app.</span></span>|
|<span data-ttu-id="8ddba-129">2</span><span class="sxs-lookup"><span data-stu-id="8ddba-129">2</span></span>|<span data-ttu-id="8ddba-130">**Nome do** aplicativo : Nome completo do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8ddba-130">**App name**: Full name of your app.</span></span>|
|<span data-ttu-id="8ddba-131">3</span><span class="sxs-lookup"><span data-stu-id="8ddba-131">3</span></span>|<span data-ttu-id="8ddba-132">**iframe**: espaço responsivo para o conteúdo do aplicativo (por exemplo, configurações de tabulação ou autenticação).</span><span class="sxs-lookup"><span data-stu-id="8ddba-132">**iframe**: Responsive space for your app’s content (for example, tab settings or authentication).</span></span>|
|<span data-ttu-id="8ddba-133">4 </span><span class="sxs-lookup"><span data-stu-id="8ddba-133">4</span></span>|<span data-ttu-id="8ddba-134">**Sobre o link**: abre uma caixa de diálogo mostrando mais informações sobre o aplicativo, como uma descrição completa, permissões exigidas pelo aplicativo e links para sua política de privacidade e termos de serviço.</span><span class="sxs-lookup"><span data-stu-id="8ddba-134">**About link**: Opens a dialog showing more information about the app, such as a full description, permissions required by the app, and links to your privacy policy and terms of service.</span></span>
|<span data-ttu-id="8ddba-135">5 </span><span class="sxs-lookup"><span data-stu-id="8ddba-135">5</span></span>|<span data-ttu-id="8ddba-136">**Botão Fechar**: fecha o modal.</span><span class="sxs-lookup"><span data-stu-id="8ddba-136">**Close button**: Closes the modal.</span></span>|
|<span data-ttu-id="8ddba-137">6 </span><span class="sxs-lookup"><span data-stu-id="8ddba-137">6</span></span>|<span data-ttu-id="8ddba-138">**Opção Notificar membros da** equipe : O modal pergunta se você deseja criar uma postagem informando que você adicionou uma guia.</span><span class="sxs-lookup"><span data-stu-id="8ddba-138">**Notify team members option**: The modal asks if you want to create a post letting others know you added a tab.</span></span>|
|<span data-ttu-id="8ddba-139">7 </span><span class="sxs-lookup"><span data-stu-id="8ddba-139">7</span></span>|<span data-ttu-id="8ddba-140">**Botão Voltar**: vai para a etapa anterior com base em onde a caixa de diálogo foi aberta.</span><span class="sxs-lookup"><span data-stu-id="8ddba-140">**Back button**: Goes to the previous step based on where the dialog opened.</span></span>|
|<span data-ttu-id="8ddba-141">8 </span><span class="sxs-lookup"><span data-stu-id="8ddba-141">8</span></span>|<span data-ttu-id="8ddba-142">**Botão Salvar**: Conclui a configuração da guia.</span><span class="sxs-lookup"><span data-stu-id="8ddba-142">**Save button**: Completes tab setup.</span></span>|

### <a name="tab-authentication-with-single-sign-on"></a><span data-ttu-id="8ddba-143">Autenticação de tabulação com login único</span><span class="sxs-lookup"><span data-stu-id="8ddba-143">Tab authentication with single sign-on</span></span>

<span data-ttu-id="8ddba-144">Você pode adicionar uma etapa na qual os usuários devem entrar primeiro com suas credenciais da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8ddba-144">You can add a step in which users must first sign in with their Microsoft credentials.</span></span> <span data-ttu-id="8ddba-145">Esse método de autenticação é chamado de SSO (single sign-on).</span><span class="sxs-lookup"><span data-stu-id="8ddba-145">This authentication method is called single sign-on (SSO).</span></span>

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-auth.png" alt-text="Exemplo mostra uma tela de autenticação de tabulação." border="false":::

### <a name="designing-a-tab-setup-with-ui-templates"></a><span data-ttu-id="8ddba-147">Projetando uma configuração de tabulação com modelos de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="8ddba-147">Designing a tab setup with UI templates</span></span>

<span data-ttu-id="8ddba-148">Use um dos seguintes modelos Teams de interface do usuário para ajudar a projetar sua experiência de configuração de tabulação:</span><span class="sxs-lookup"><span data-stu-id="8ddba-148">Use one of the following Teams UI templates to help design your tab setup experience:</span></span>

* <span data-ttu-id="8ddba-149">[Lista](../../concepts/design/design-teams-app-ui-templates.md#list): as listas podem exibir itens relacionados em um formato digitalizável e permitir que os usuários tomem ações em uma lista inteira ou itens individuais.</span><span class="sxs-lookup"><span data-stu-id="8ddba-149">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="8ddba-150">[Formulário](../../concepts/design/design-teams-app-ui-templates.md#form): Os formulários são para coletar, validar e enviar entrada do usuário de forma estruturada.</span><span class="sxs-lookup"><span data-stu-id="8ddba-150">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="8ddba-151">[Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): o modelo de estado vazio pode ser usado para muitos cenários, incluindo entrar, experiências de primeira executar, mensagens de erro e muito mais.</span><span class="sxs-lookup"><span data-stu-id="8ddba-151">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>

## <a name="view-a-tab"></a><span data-ttu-id="8ddba-152">Exibir uma guia</span><span class="sxs-lookup"><span data-stu-id="8ddba-152">View a tab</span></span>

<span data-ttu-id="8ddba-153">As guias fornecem uma experiência da Web de tela inteira em Teams onde você pode exibir conteúdo colaborativo, como painéis e painéis de tarefas, e informações importantes.</span><span class="sxs-lookup"><span data-stu-id="8ddba-153">Tabs provide a full-screen web experience in Teams where you can display collaborative content—such task boards and dashboards—and important information.</span></span>

:::image type="content" source="../../assets/images/tabs/design-view-tab.png" alt-text="Exemplo mostra uma guia com um quadro de tarefas." border="false":::

### <a name="anatomy-tab"></a><span data-ttu-id="8ddba-155">Anatomia: Guia</span><span class="sxs-lookup"><span data-stu-id="8ddba-155">Anatomy: Tab</span></span>

:::image type="content" source="../../assets/images/tabs/design-view-tab-anatomy.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de uma guia." border="false":::

|<span data-ttu-id="8ddba-157">Contador</span><span class="sxs-lookup"><span data-stu-id="8ddba-157">Counter</span></span>|<span data-ttu-id="8ddba-158">Descrição</span><span class="sxs-lookup"><span data-stu-id="8ddba-158">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="8ddba-159">1</span><span class="sxs-lookup"><span data-stu-id="8ddba-159">1</span></span>|<span data-ttu-id="8ddba-160">**Nome da guia**: Rótulo de navegação para sua guia.</span><span class="sxs-lookup"><span data-stu-id="8ddba-160">**Tab name**: Navigation label for your tab.</span></span>|
|<span data-ttu-id="8ddba-161">2</span><span class="sxs-lookup"><span data-stu-id="8ddba-161">2</span></span>|<span data-ttu-id="8ddba-162">**Estouro da** guia : abre ações de guia, como renomear e remover.</span><span class="sxs-lookup"><span data-stu-id="8ddba-162">**Tab overflow**: Opens tab actions, such as rename and remove.</span></span>|
|<span data-ttu-id="8ddba-163">3</span><span class="sxs-lookup"><span data-stu-id="8ddba-163">3</span></span>|<span data-ttu-id="8ddba-164">**Chat de tabulação**: abre um thread de chat à direita, permitindo que os usuários tenham uma conversa ao lado do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="8ddba-164">**Tab chat**: Opens a chat thread on the right, allowing users to have a conversation next to the content.</span></span>|
|<span data-ttu-id="8ddba-165">4 </span><span class="sxs-lookup"><span data-stu-id="8ddba-165">4</span></span>|<span data-ttu-id="8ddba-166">**iframe**: exibe o conteúdo da guia.</span><span class="sxs-lookup"><span data-stu-id="8ddba-166">**iframe**: Displays your tab’s content.</span></span>

### <a name="designing-a-tab-with-ui-templates"></a><span data-ttu-id="8ddba-167">Criar uma guia com modelos de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="8ddba-167">Designing a tab with UI templates</span></span>

<span data-ttu-id="8ddba-168">Use um dos seguintes modelos Teams de interface do usuário para ajudar a projetar sua experiência de guia:</span><span class="sxs-lookup"><span data-stu-id="8ddba-168">Use one of the following Teams UI templates to help design your tab experience:</span></span>

* <span data-ttu-id="8ddba-169">[Lista](../../concepts/design/design-teams-app-ui-templates.md#list): as listas podem exibir itens relacionados em um formato digitalizável e permitir que os usuários tomem ações em uma lista inteira ou itens individuais.</span><span class="sxs-lookup"><span data-stu-id="8ddba-169">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="8ddba-170">[Quadro de](../../concepts/design/design-teams-app-ui-templates.md#task-board)tarefas : um quadro de tarefas, às vezes chamado de quadro kanban ou faixas de nadador, é uma coleção de cartões frequentemente usada para rastrear o status de itens de trabalho ou tíquetes.</span><span class="sxs-lookup"><span data-stu-id="8ddba-170">[Task board](../../concepts/design/design-teams-app-ui-templates.md#task-board): A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span>
* <span data-ttu-id="8ddba-171">[Painel](../../concepts/design/design-teams-app-ui-templates.md#dashboard): um painel é uma tela que contém vários cartões que fornecem uma visão geral dos dados ou conteúdo.</span><span class="sxs-lookup"><span data-stu-id="8ddba-171">[Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): A dashboard is a canvas containing multiple cards that provide an overview of data or content.</span></span>
* <span data-ttu-id="8ddba-172">[Formulário](../../concepts/design/design-teams-app-ui-templates.md#form): Os formulários são para coletar, validar e enviar entrada do usuário de forma estruturada.</span><span class="sxs-lookup"><span data-stu-id="8ddba-172">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="8ddba-173">[Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): o modelo de estado vazio pode ser usado para muitos cenários, incluindo entrar, experiências de primeira executar, mensagens de erro e muito mais.</span><span class="sxs-lookup"><span data-stu-id="8ddba-173">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>
* <span data-ttu-id="8ddba-174">[Navegação à esquerda](../../concepts/design/design-teams-app-ui-templates.md#left-nav): O modelo de navegação à esquerda pode ajudar se sua guia exigir alguma navegação.</span><span class="sxs-lookup"><span data-stu-id="8ddba-174">[Left nav](../../concepts/design/design-teams-app-ui-templates.md#left-nav): The left nav template can help if your tab requires some navigation.</span></span> <span data-ttu-id="8ddba-175">Em geral, você deve manter a navegação de tabulação no mínimo.</span><span class="sxs-lookup"><span data-stu-id="8ddba-175">In general, you should keep tab navigation to a minimum.</span></span>

## <a name="use-a-tab-to-collaborate"></a><span data-ttu-id="8ddba-176">Usar uma guia para colaborar</span><span class="sxs-lookup"><span data-stu-id="8ddba-176">Use a tab to collaborate</span></span>

<span data-ttu-id="8ddba-177">Guias ajudam a facilitar conversas sobre conteúdo em um local central.</span><span class="sxs-lookup"><span data-stu-id="8ddba-177">Tabs help facilitate conversations about content in a central location.</span></span>

### <a name="thread-discussion"></a><span data-ttu-id="8ddba-178">Discussão de thread</span><span class="sxs-lookup"><span data-stu-id="8ddba-178">Thread discussion</span></span>

<span data-ttu-id="8ddba-179">Os usuários podem postar automaticamente em um canal ou chat depois de adicionarem uma nova guia. Isso não apenas notifica os membros da equipe do novo conteúdo e fornece um link para guia, ele permite que as pessoas comecem a falar sobre a guia.</span><span class="sxs-lookup"><span data-stu-id="8ddba-179">Users can automatically post to a channel or chat once they’ve added a new tab. This not only notifies team members of the new content and provides a link to tab, it allows people to start talking about the tab.</span></span>

:::image type="content" source="../../assets/images/tabs/design-use-tab-channel.png" alt-text="Exemplo mostra uma guia sendo discutida em um thread de canal." border="false":::

### <a name="side-by-side-discussion"></a><span data-ttu-id="8ddba-181">Discussão lado a lado</span><span class="sxs-lookup"><span data-stu-id="8ddba-181">Side-by-side discussion</span></span>

<span data-ttu-id="8ddba-182">Os usuários podem ter uma conversa em seguida durante a exibição do conteúdo da guia.</span><span class="sxs-lookup"><span data-stu-id="8ddba-182">Users can have a conversation next while viewing the tab’s content.</span></span>

:::image type="content" source="../../assets/images/tabs/design-use-tab-side-chat.png" alt-text="Exemplo mostra uma guia com um chat aberto no lado direito." border="false":::

### <a name="permissions-and-role-based-views"></a><span data-ttu-id="8ddba-184">Permissões e exibições baseadas em função</span><span class="sxs-lookup"><span data-stu-id="8ddba-184">Permissions and role-based views</span></span>

<span data-ttu-id="8ddba-185">A experiência de tabulação pode ser diferente para os usuários, dependendo de suas permissões.</span><span class="sxs-lookup"><span data-stu-id="8ddba-185">The tab experience may be different for users depending on their permissions.</span></span> <span data-ttu-id="8ddba-186">Por exemplo, um usuário pode acessar a guia sem precisar entrar.</span><span class="sxs-lookup"><span data-stu-id="8ddba-186">For example, one user can access the tab without having to sign in.</span></span> <span data-ttu-id="8ddba-187">Outro usuário, no entanto, deve assinar e ver conteúdo ligeiramente diferente.</span><span class="sxs-lookup"><span data-stu-id="8ddba-187">Another user, however, must sign and will see slightly different content.</span></span>

## <a name="manage-a-tab"></a><span data-ttu-id="8ddba-188">Gerenciar uma guia</span><span class="sxs-lookup"><span data-stu-id="8ddba-188">Manage a tab</span></span>

<span data-ttu-id="8ddba-189">Você pode incluir opções para renomear, remover ou modificar uma guia.</span><span class="sxs-lookup"><span data-stu-id="8ddba-189">You can include options to rename, remove, or modify a tab.</span></span>

### <a name="anatomy-tab-menu"></a><span data-ttu-id="8ddba-190">Anatomia: menu Tab</span><span class="sxs-lookup"><span data-stu-id="8ddba-190">Anatomy: Tab menu</span></span>

:::image type="content" source="../../assets/images/tabs/design-manage-tab-menu-anatomy.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de um menu de tabulação." border="false":::

|<span data-ttu-id="8ddba-192">Contador</span><span class="sxs-lookup"><span data-stu-id="8ddba-192">Counter</span></span>|<span data-ttu-id="8ddba-193">Descrição</span><span class="sxs-lookup"><span data-stu-id="8ddba-193">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="8ddba-194">1</span><span class="sxs-lookup"><span data-stu-id="8ddba-194">1</span></span>|<span data-ttu-id="8ddba-195">**Configurações**: (Opcional) Permite que os usuários modifiquem as configurações de uma guia depois que ela foi adicionada.</span><span class="sxs-lookup"><span data-stu-id="8ddba-195">**Settings**: (Optional) Allows users to modify a tab’s settings after it’s been added.</span></span>|
|<span data-ttu-id="8ddba-196">2</span><span class="sxs-lookup"><span data-stu-id="8ddba-196">2</span></span>|<span data-ttu-id="8ddba-197">**Renomear**: Permite que os usuários dêem à guia um nome mais significativo para a equipe.</span><span class="sxs-lookup"><span data-stu-id="8ddba-197">**Rename**: Allows users to give the tab a name that’s more meaningful to the team.</span></span>|
|<span data-ttu-id="8ddba-198">3</span><span class="sxs-lookup"><span data-stu-id="8ddba-198">3</span></span>|<span data-ttu-id="8ddba-199">**Remover**: remove a guia do canal, chat ou reunião.</span><span class="sxs-lookup"><span data-stu-id="8ddba-199">**Remove**: Removes the tab from the channel, chat, or meeting.</span></span>|

## <a name="tab-notifications-and-deep-linking"></a><span data-ttu-id="8ddba-200">Notificações de tabulação e vinculação profunda</span><span class="sxs-lookup"><span data-stu-id="8ddba-200">Tab notifications and deep linking</span></span>

<span data-ttu-id="8ddba-201">Você pode enviar uma mensagem com um link profundo para sua guia. Por exemplo, um cartão mostra um resumo dos dados de bugs que um usuário pode selecionar para ver o bug inteiro em uma guia. O envio de mensagens sobre a atividade de tabulação aumenta a conscientização sem notificar explicitamente todos (ou seja, atividades sem ruído).</span><span class="sxs-lookup"><span data-stu-id="8ddba-201">You can send a message with a deep link to your tab. For example, a card shows a summary of bug data a user can select to see the entire bug in a tab. Sending messages about tab activity increases awareness without explicitly notifying everyone (i.e., activity without noise).</span></span> <span data-ttu-id="8ddba-202">Você também pode @mention usuários específicos, se necessário.</span><span class="sxs-lookup"><span data-stu-id="8ddba-202">You also can @mention specific users if needed.</span></span>

<span data-ttu-id="8ddba-203">Notificar os usuários da atividade de tabulação uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="8ddba-203">Notify users of tab activity one of the following ways:</span></span>

* <span data-ttu-id="8ddba-204">**Bot**: Este método é preferencial especialmente se o thread de tabulação for direcionado.</span><span class="sxs-lookup"><span data-stu-id="8ddba-204">**Bot**: This method is preferred especially if the tab thread is targeted.</span></span> <span data-ttu-id="8ddba-205">A conversa encadeada da guia é movida para a exibição como ativa recentemente.</span><span class="sxs-lookup"><span data-stu-id="8ddba-205">The tab’s threaded conversation is moved into view as recently active.</span></span> <span data-ttu-id="8ddba-206">Esse método também permite alguma sofisticação na forma como a notificação é enviada.</span><span class="sxs-lookup"><span data-stu-id="8ddba-206">This method also allows for some sophistication in how the notification is sent.</span></span>
* <span data-ttu-id="8ddba-207">**Mensagem**: uma mensagem aparece no feed de atividade do usuário com um [link profundo para a guia](../../concepts/build-and-test/deep-links.md?view=msteams-client-js-latest&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="8ddba-207">**Message**: A message shows up in the user’s activity feed with a [deep link to the tab](../../concepts/build-and-test/deep-links.md?view=msteams-client-js-latest&preserve-view=true).</span></span>

## <a name="best-practices"></a><span data-ttu-id="8ddba-208">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="8ddba-208">Best practices</span></span>

<span data-ttu-id="8ddba-209">Use essas recomendações para criar uma experiência de aplicativo de qualidade.</span><span class="sxs-lookup"><span data-stu-id="8ddba-209">Use these recommendations to create a quality app experience.</span></span>

### <a name="collaboration"></a><span data-ttu-id="8ddba-210">Colaboração</span><span class="sxs-lookup"><span data-stu-id="8ddba-210">Collaboration</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-do.png" alt-text="A ilustração mostra o que fazer com o design de navegação de tabulação." border="false":::

#### <a name="do-facilitate-conversation"></a><span data-ttu-id="8ddba-212">Do: Facilitar a conversa</span><span class="sxs-lookup"><span data-stu-id="8ddba-212">Do: Facilitate conversation</span></span>

<span data-ttu-id="8ddba-213">Inclua conteúdo e componentes que as pessoas possam falar.</span><span class="sxs-lookup"><span data-stu-id="8ddba-213">Include content and components people can talk about.</span></span> <span data-ttu-id="8ddba-214">Se ele não se encaixar no contexto de um chat, canal ou reunião, ele não pertence à sua guia.</span><span class="sxs-lookup"><span data-stu-id="8ddba-214">If it doesn’t fit within the context of a chat, channel, or meeting, it doesn’t belong in your tab.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-dont.png" alt-text="Exemplo mostra o que não fazer com o design de navegação de tabulação." border="false":::

#### <a name="dont-treat-your-tab-like-any-other-webpage"></a><span data-ttu-id="8ddba-216">Não: trate sua guia como qualquer outra página da Web</span><span class="sxs-lookup"><span data-stu-id="8ddba-216">Don't: Treat your tab like any other webpage</span></span>

<span data-ttu-id="8ddba-217">Uma guia não é uma página da Web que alguém pode exibir uma vez.</span><span class="sxs-lookup"><span data-stu-id="8ddba-217">A tab isn’t a webpage someone might view once.</span></span> <span data-ttu-id="8ddba-218">Uma guia deve exibir o conteúdo mais importante e relevante que as pessoas precisam para realizar algo juntos.</span><span class="sxs-lookup"><span data-stu-id="8ddba-218">A tab should display your most important, relevant content that people need to accomplish something together.</span></span>

   :::column-end:::
:::row-end:::

### <a name="navigation"></a><span data-ttu-id="8ddba-219">Navegação</span><span class="sxs-lookup"><span data-stu-id="8ddba-219">Navigation</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-do.png" alt-text="Exemplo mostrando o que fazer com o design de navegação de tabulação." border="false":::

#### <a name="do-limit-tasks-and-data"></a><span data-ttu-id="8ddba-221">Fazer: Limitar tarefas e dados</span><span class="sxs-lookup"><span data-stu-id="8ddba-221">Do: Limit tasks and data</span></span>

<span data-ttu-id="8ddba-222">As guias funcionam melhor quando elas abordam necessidades específicas.</span><span class="sxs-lookup"><span data-stu-id="8ddba-222">Tabs work best when they address specific needs.</span></span> <span data-ttu-id="8ddba-223">Inclua um conjunto limitado de tarefas e dados relevantes para a equipe ou grupo.</span><span class="sxs-lookup"><span data-stu-id="8ddba-223">Include a limited set of tasks and data relevant to the team or group.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-dont.png" alt-text="Ilustração mostrando o que não fazer com o design de navegação de tabulação." border="false":::

#### <a name="dont-embed-your-entire-app"></a><span data-ttu-id="8ddba-225">Não: incorporar seu aplicativo inteiro</span><span class="sxs-lookup"><span data-stu-id="8ddba-225">Don't: Embed your entire app</span></span>

<span data-ttu-id="8ddba-226">Usar uma guia para exibir um aplicativo inteiro com navegação de vários níveis e interações complexas leva à sobrecarga de informações.</span><span class="sxs-lookup"><span data-stu-id="8ddba-226">Using a tab to display an entire app with multi-level navigation and complex interactions leads to information overload.</span></span>

   :::column-end:::
:::row-end:::

### <a name="setup"></a><span data-ttu-id="8ddba-227">Configurar</span><span class="sxs-lookup"><span data-stu-id="8ddba-227">Setup</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-do.png" alt-text="Ilustração mostrando o que fazer com o design de configuração de tabulação." border="false":::

#### <a name="do-keep-it-simple"></a><span data-ttu-id="8ddba-229">Fazer: mantenha-o simples</span><span class="sxs-lookup"><span data-stu-id="8ddba-229">Do: Keep it simple</span></span>

<span data-ttu-id="8ddba-230">Se seu aplicativo exigir autenticação, tente integrar o SSO (login único) da Microsoft para uma experiência de login mais perfeita.</span><span class="sxs-lookup"><span data-stu-id="8ddba-230">If your app requires authentication, try integrating Microsoft single sign-on (SSO) for a more seamless sign-in experience.</span></span> <span data-ttu-id="8ddba-231">Além disso, inclua apenas informações essenciais e etapas para adicionar a guia.</span><span class="sxs-lookup"><span data-stu-id="8ddba-231">Also, only include essential information and steps to add the tab.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-dont.png" alt-text="Ilustração mostrando o que não fazer com o design de configuração de tabulação." border="false":::

#### <a name="dont-have-too-many-steps"></a><span data-ttu-id="8ddba-233">Não: ter muitas etapas</span><span class="sxs-lookup"><span data-stu-id="8ddba-233">Don't: Have too many steps</span></span>

<span data-ttu-id="8ddba-234">Remova todas as etapas desnecessárias para adicionar uma guia.</span><span class="sxs-lookup"><span data-stu-id="8ddba-234">Remove any unnecessary steps for adding a tab.</span></span>

   :::column-end:::
:::row-end:::

### <a name="theming"></a><span data-ttu-id="8ddba-235">Temas</span><span class="sxs-lookup"><span data-stu-id="8ddba-235">Theming</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-do.png" alt-text="Ilustração mostrando o que fazer com temas de tabulação." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a><span data-ttu-id="8ddba-237">Do: tire proveito de Teams de cores</span><span class="sxs-lookup"><span data-stu-id="8ddba-237">Do: Take advantage of Teams color tokens</span></span>

<span data-ttu-id="8ddba-238">Cada Teams tem seu próprio esquema de cores.</span><span class="sxs-lookup"><span data-stu-id="8ddba-238">Each Teams theme has its own color scheme.</span></span> <span data-ttu-id="8ddba-239">Para lidar com alterações de tema automaticamente, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">tokens de cor (interface do usuário fluente)</a> em seu design.</span><span class="sxs-lookup"><span data-stu-id="8ddba-239">To handle theme changes automatically, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">color tokens (Fluent UI)</a> in your design.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-dont.png" alt-text="Ilustração mostrando o que não fazer com temas de tabulação." border="false":::

#### <a name="dont-hard-code-color-values"></a><span data-ttu-id="8ddba-241">Não: Valores de cor de código rígidos</span><span class="sxs-lookup"><span data-stu-id="8ddba-241">Don't: Hard code color values</span></span>

<span data-ttu-id="8ddba-242">Se você não usar tokens Teams cores, seus designs serão menos escalonáveis e levarão mais tempo para gerenciar.</span><span class="sxs-lookup"><span data-stu-id="8ddba-242">If you don’t use Teams color tokens, your designs will be less scalable and take more time to manage.</span></span>

   :::column-end:::
:::row-end:::
