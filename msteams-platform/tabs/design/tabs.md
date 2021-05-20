---
title: Projetando sua guia para desktop e web
description: Aprenda a projetar uma guia Teams (desktop e web) e obtenha o kit de interface do usuário Microsoft Teams.
author: heath-hamilton
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: baa17cd97ff4e2cad91615dced5c4e4cf5e533c8
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566877"
---
# <a name="designing-your-tab-for-microsoft-teams-desktop-and-web"></a><span data-ttu-id="e2b10-103">Projetando sua guia para Microsoft Teams desktop e web</span><span class="sxs-lookup"><span data-stu-id="e2b10-103">Designing your tab for Microsoft Teams desktop and web</span></span>

<span data-ttu-id="e2b10-104">Uma guia é uma tela grande para o seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="e2b10-104">A tab is a large canvas for your content.</span></span> <span data-ttu-id="e2b10-105">Para orientar o design do aplicativo, as seguintes informações descrevem e ilustram como as pessoas podem adicionar, usar e gerenciar guias em Teams.</span><span class="sxs-lookup"><span data-stu-id="e2b10-105">To guide your app design, the following information describes and illustrates how people can add, use, and manage tabs in Teams.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="e2b10-106">Kit de Interface do Usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="e2b10-106">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="e2b10-107">Você pode encontrar diretrizes abrangentes de design de guias, incluindo elementos que você pode pegar e modificar conforme necessário, no Microsoft Teams UI Kit.</span><span class="sxs-lookup"><span data-stu-id="e2b10-107">You can find comprehensive tab design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span> <span data-ttu-id="e2b10-108">O kit de interface do usuário também tem tópicos essenciais, como acessibilidade e dimensionamento responsivo que não são abordados aqui.</span><span class="sxs-lookup"><span data-stu-id="e2b10-108">The UI kit also has essential topics such as accessibility and responsive sizing that aren't covered here.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e2b10-109">Obtenha o Kit de Interface do Usuário do Microsoft Teams (Figma)</span><span class="sxs-lookup"><span data-stu-id="e2b10-109">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-tab"></a><span data-ttu-id="e2b10-110">Adicionar uma guia</span><span class="sxs-lookup"><span data-stu-id="e2b10-110">Add a tab</span></span>

<span data-ttu-id="e2b10-111">Você pode adicionar uma guia na loja Teams (AppSource) ou em um dos seguintes contextos:</span><span class="sxs-lookup"><span data-stu-id="e2b10-111">You can add a tab from the Teams store (AppSource) or in one of the following contexts:</span></span>

* <span data-ttu-id="e2b10-112">Chat</span><span class="sxs-lookup"><span data-stu-id="e2b10-112">Chat</span></span>
* <span data-ttu-id="e2b10-113">Canal</span><span class="sxs-lookup"><span data-stu-id="e2b10-113">Channel</span></span>
* <span data-ttu-id="e2b10-114">Reunião (antes, durante ou depois da reunião)</span><span class="sxs-lookup"><span data-stu-id="e2b10-114">Meeting (before, during, or after the meeting)</span></span>

<span data-ttu-id="e2b10-115">O exemplo a seguir mostra como uma guia é adicionada em um canal:</span><span class="sxs-lookup"><span data-stu-id="e2b10-115">The following example shows how a tab is added in a channel:</span></span>

:::image type="content" source="../../assets/images/tabs/design-add-tab.png" alt-text="O exemplo mostra uma guia sendo adicionada em um canal." border="false":::

## <a name="set-up-a-tab"></a><span data-ttu-id="e2b10-117">Configure uma guia</span><span class="sxs-lookup"><span data-stu-id="e2b10-117">Set up a tab</span></span>

<span data-ttu-id="e2b10-118">Há um pequeno processo de configuração para adicionar um aplicativo como canal, chat ou guia de reunião. A experiência depende de você.</span><span class="sxs-lookup"><span data-stu-id="e2b10-118">There's a short setup process to add an app as a channel, chat, or meeting tab. The experience is largely up to you.</span></span> <span data-ttu-id="e2b10-119">Por exemplo, você pode ter uma descrição de como usar o aplicativo e algumas configurações opcionais.</span><span class="sxs-lookup"><span data-stu-id="e2b10-119">For example, you could have a description of how to use the app and some optional settings.</span></span> <span data-ttu-id="e2b10-120">Inclua um passo de login aqui se você precisar autenticar os usuários.</span><span class="sxs-lookup"><span data-stu-id="e2b10-120">Include a sign-in step here if you need to authenticate users.</span></span>

### <a name="tab-configuration-modal"></a><span data-ttu-id="e2b10-121">Modal de configuração da guia</span><span class="sxs-lookup"><span data-stu-id="e2b10-121">Tab configuration modal</span></span>

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-config.png" alt-text="O exemplo mostra um modal de configuração de guia." border="false":::

### <a name="anatomy-tab-configuration-modal"></a><span data-ttu-id="e2b10-123">Anatomia: Modal de configuração da guia</span><span class="sxs-lookup"><span data-stu-id="e2b10-123">Anatomy: Tab configuration modal</span></span>

:::image type="content" source="../../assets/images/tabs/test.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de um modal de configuração de guia." border="false":::

|<span data-ttu-id="e2b10-125">Contador</span><span class="sxs-lookup"><span data-stu-id="e2b10-125">Counter</span></span>|<span data-ttu-id="e2b10-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="e2b10-126">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="e2b10-127">1</span><span class="sxs-lookup"><span data-stu-id="e2b10-127">1</span></span>|<span data-ttu-id="e2b10-128">**Logotipo do** aplicativo : Logotipo completo do aplicativo colorido do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e2b10-128">**App logo**: Full color app logo of your app.</span></span>|
|<span data-ttu-id="e2b10-129">2</span><span class="sxs-lookup"><span data-stu-id="e2b10-129">2</span></span>|<span data-ttu-id="e2b10-130">**Nome do** aplicativo : Nome completo do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e2b10-130">**App name**: Full name of your app.</span></span>|
|<span data-ttu-id="e2b10-131">3</span><span class="sxs-lookup"><span data-stu-id="e2b10-131">3</span></span>|<span data-ttu-id="e2b10-132">**iframe**: Espaço responsivo para o conteúdo do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e2b10-132">**iframe**: Responsive space for your app’s content.</span></span> <span data-ttu-id="e2b10-133">Por exemplo, configurações de guia ou autenticação.</span><span class="sxs-lookup"><span data-stu-id="e2b10-133">For example, tab settings or authentication.</span></span>|
|<span data-ttu-id="e2b10-134">4 </span><span class="sxs-lookup"><span data-stu-id="e2b10-134">4</span></span>|<span data-ttu-id="e2b10-135">**Sobre o link**: Abre uma caixa de diálogo mostrando mais informações sobre o aplicativo, como uma descrição completa, permissões exigidas pelo aplicativo e links para sua política de privacidade e termos de serviço.</span><span class="sxs-lookup"><span data-stu-id="e2b10-135">**About link**: Opens a dialog showing more information about the app, such as a full description, permissions required by the app, and links to your privacy policy and terms of service.</span></span>
|<span data-ttu-id="e2b10-136">5 </span><span class="sxs-lookup"><span data-stu-id="e2b10-136">5</span></span>|<span data-ttu-id="e2b10-137">**Botão de fechamento**: Fecha o modal.</span><span class="sxs-lookup"><span data-stu-id="e2b10-137">**Close button**: Closes the modal.</span></span>|
|<span data-ttu-id="e2b10-138">6 </span><span class="sxs-lookup"><span data-stu-id="e2b10-138">6</span></span>|<span data-ttu-id="e2b10-139">**Opção notificar membros da equipe**: O modal pergunta se você deseja criar um post informando que você adicionou uma guia.</span><span class="sxs-lookup"><span data-stu-id="e2b10-139">**Notify team members option**: The modal asks if you want to create a post letting others know you added a tab.</span></span>|
|<span data-ttu-id="e2b10-140">7 </span><span class="sxs-lookup"><span data-stu-id="e2b10-140">7</span></span>|<span data-ttu-id="e2b10-141">**Botão de** trás : Vai para a etapa anterior com base em onde o diálogo foi aberto.</span><span class="sxs-lookup"><span data-stu-id="e2b10-141">**Back button**: Goes to the previous step based on where the dialog opened.</span></span>|
|<span data-ttu-id="e2b10-142">8 </span><span class="sxs-lookup"><span data-stu-id="e2b10-142">8</span></span>|<span data-ttu-id="e2b10-143">**Botão salvar:** completa a configuração da guia.</span><span class="sxs-lookup"><span data-stu-id="e2b10-143">**Save button**: Completes tab setup.</span></span>|

### <a name="tab-authentication-with-single-sign-on"></a><span data-ttu-id="e2b10-144">Autenticação de guia com login único</span><span class="sxs-lookup"><span data-stu-id="e2b10-144">Tab authentication with single sign-on</span></span>

<span data-ttu-id="e2b10-145">Você pode adicionar uma etapa na qual os usuários devem primeiro fazer login com suas credenciais microsoft.</span><span class="sxs-lookup"><span data-stu-id="e2b10-145">You can add a step in which users must first sign in with their Microsoft credentials.</span></span> <span data-ttu-id="e2b10-146">Este método de autenticação é chamado de single sign-on (SSO).</span><span class="sxs-lookup"><span data-stu-id="e2b10-146">This authentication method is called single sign-on (SSO).</span></span>

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-auth.png" alt-text="O exemplo mostra uma tela de autenticação de guias." border="false":::

### <a name="designing-a-tab-setup-with-ui-templates"></a><span data-ttu-id="e2b10-148">Projetando uma configuração de guia com modelos de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="e2b10-148">Designing a tab setup with UI templates</span></span>

<span data-ttu-id="e2b10-149">Use um dos seguintes modelos de interface do usuário Teams para ajudar a projetar sua experiência de configuração de guia:</span><span class="sxs-lookup"><span data-stu-id="e2b10-149">Use one of the following Teams UI templates to help design your tab setup experience:</span></span>

* <span data-ttu-id="e2b10-150">[Lista](../../concepts/design/design-teams-app-ui-templates.md#list): As listas podem exibir itens relacionados em um formato digitalizável e permitir que os usuários tomem ações em uma lista inteira ou itens individuais.</span><span class="sxs-lookup"><span data-stu-id="e2b10-150">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="e2b10-151">[Formulário](../../concepts/design/design-teams-app-ui-templates.md#form): Os formulários são para coletar, validar e enviar a entrada do usuário de forma estruturada.</span><span class="sxs-lookup"><span data-stu-id="e2b10-151">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="e2b10-152">[Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): O modelo de estado vazio pode ser usado para muitos cenários, incluindo login, experiências de primeira execução, mensagens de erro e muito mais.</span><span class="sxs-lookup"><span data-stu-id="e2b10-152">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>

## <a name="view-a-tab"></a><span data-ttu-id="e2b10-153">Exibir uma guia</span><span class="sxs-lookup"><span data-stu-id="e2b10-153">View a tab</span></span>

<span data-ttu-id="e2b10-154">As guias fornecem uma experiência web em tela cheia em Teams onde você pode exibir conteúdo colaborativo — tais painéis de tarefas e dashboards — e informações importantes.</span><span class="sxs-lookup"><span data-stu-id="e2b10-154">Tabs provide a full-screen web experience in Teams where you can display collaborative content—such task boards and dashboards—and important information.</span></span>

:::image type="content" source="../../assets/images/tabs/design-view-tab.png" alt-text="O exemplo mostra uma guia com uma placa de tarefas." border="false":::

### <a name="anatomy-tab"></a><span data-ttu-id="e2b10-156">Anatomia: Guia</span><span class="sxs-lookup"><span data-stu-id="e2b10-156">Anatomy: Tab</span></span>

:::image type="content" source="../../assets/images/tabs/design-view-tab-anatomy.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de uma guia." border="false":::

|<span data-ttu-id="e2b10-158">Contador</span><span class="sxs-lookup"><span data-stu-id="e2b10-158">Counter</span></span>|<span data-ttu-id="e2b10-159">Descrição</span><span class="sxs-lookup"><span data-stu-id="e2b10-159">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="e2b10-160">1</span><span class="sxs-lookup"><span data-stu-id="e2b10-160">1</span></span>|<span data-ttu-id="e2b10-161">**Nome da guia**: Etiqueta de navegação para sua guia.</span><span class="sxs-lookup"><span data-stu-id="e2b10-161">**Tab name**: Navigation label for your tab.</span></span>|
|<span data-ttu-id="e2b10-162">2</span><span class="sxs-lookup"><span data-stu-id="e2b10-162">2</span></span>|<span data-ttu-id="e2b10-163">**Estouro da** guia : Abre ações de guia, como renomear e remover.</span><span class="sxs-lookup"><span data-stu-id="e2b10-163">**Tab overflow**: Opens tab actions, such as rename and remove.</span></span>|
|<span data-ttu-id="e2b10-164">3</span><span class="sxs-lookup"><span data-stu-id="e2b10-164">3</span></span>|<span data-ttu-id="e2b10-165">**Tab chat**: Abre um thread de bate-papo à direita, permitindo que os usuários tenham uma conversa ao lado do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="e2b10-165">**Tab chat**: Opens a chat thread on the right, allowing users to have a conversation next to the content.</span></span>|
|<span data-ttu-id="e2b10-166">4 </span><span class="sxs-lookup"><span data-stu-id="e2b10-166">4</span></span>|<span data-ttu-id="e2b10-167">**iframe**: Exibe o conteúdo da guia.</span><span class="sxs-lookup"><span data-stu-id="e2b10-167">**iframe**: Displays your tab’s content.</span></span>

### <a name="designing-a-tab-with-ui-templates"></a><span data-ttu-id="e2b10-168">Projetando uma guia com modelos de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="e2b10-168">Designing a tab with UI templates</span></span>

<span data-ttu-id="e2b10-169">Use um dos seguintes modelos de interface do usuário Teams para ajudar a projetar sua experiência de guia:</span><span class="sxs-lookup"><span data-stu-id="e2b10-169">Use one of the following Teams UI templates to help design your tab experience:</span></span>

* <span data-ttu-id="e2b10-170">[Lista](../../concepts/design/design-teams-app-ui-templates.md#list): As listas podem exibir itens relacionados em um formato digitalizável e permitir que os usuários tomem ações em uma lista inteira ou itens individuais.</span><span class="sxs-lookup"><span data-stu-id="e2b10-170">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="e2b10-171">[Quadro de](../../concepts/design/design-teams-app-ui-templates.md#task-board)tarefas : Um quadro de tarefas, às vezes chamado de placa kanban ou pistas de natação, é uma coleção de cartões frequentemente usados para rastrear o status de itens de trabalho ou bilhetes.</span><span class="sxs-lookup"><span data-stu-id="e2b10-171">[Task board](../../concepts/design/design-teams-app-ui-templates.md#task-board): A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span>
* <span data-ttu-id="e2b10-172">[Painel](../../concepts/design/design-teams-app-ui-templates.md#dashboard): Um painel de instrumentos é uma tela que contém vários cartões que fornecem uma visão geral de dados ou conteúdo.</span><span class="sxs-lookup"><span data-stu-id="e2b10-172">[Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): A dashboard is a canvas containing multiple cards that provide an overview of data or content.</span></span>
* <span data-ttu-id="e2b10-173">[Formulário](../../concepts/design/design-teams-app-ui-templates.md#form): Os formulários são para coletar, validar e enviar a entrada do usuário de forma estruturada.</span><span class="sxs-lookup"><span data-stu-id="e2b10-173">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="e2b10-174">[Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): O modelo de estado vazio pode ser usado para muitos cenários, incluindo login, experiências de primeira execução, mensagens de erro e muito mais.</span><span class="sxs-lookup"><span data-stu-id="e2b10-174">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>
* <span data-ttu-id="e2b10-175">[Navegação à esquerda](../../concepts/design/design-teams-app-ui-templates.md#left-nav): O modelo de navegação à esquerda pode ajudar se sua guia precisar de alguma navegação.</span><span class="sxs-lookup"><span data-stu-id="e2b10-175">[Left nav](../../concepts/design/design-teams-app-ui-templates.md#left-nav): The left nav template can help if your tab requires some navigation.</span></span> <span data-ttu-id="e2b10-176">Em geral, você deve manter a navegação de controle ao mínimo.</span><span class="sxs-lookup"><span data-stu-id="e2b10-176">In general, you should keep tab navigation to a minimum.</span></span>

## <a name="use-a-tab-to-collaborate"></a><span data-ttu-id="e2b10-177">Use uma guia para colaborar</span><span class="sxs-lookup"><span data-stu-id="e2b10-177">Use a tab to collaborate</span></span>

<span data-ttu-id="e2b10-178">As guias ajudam a facilitar conversas sobre conteúdo em um local central.</span><span class="sxs-lookup"><span data-stu-id="e2b10-178">Tabs help facilitate conversations about content in a central location.</span></span>

### <a name="thread-discussion"></a><span data-ttu-id="e2b10-179">Discussão de tópicos</span><span class="sxs-lookup"><span data-stu-id="e2b10-179">Thread discussion</span></span>

<span data-ttu-id="e2b10-180">Os usuários podem postar automaticamente em um canal ou chat depois de adicionar uma nova guia. Isso não só notifica os membros da equipe do novo conteúdo e fornece um link para a guia, ele permite que as pessoas comecem a falar sobre a guia.</span><span class="sxs-lookup"><span data-stu-id="e2b10-180">Users can automatically post to a channel or chat once they’ve added a new tab. This not only notifies team members of the new content and provides a link to tab, it allows people to start talking about the tab.</span></span>

:::image type="content" source="../../assets/images/tabs/design-use-tab-channel.png" alt-text="O exemplo mostra uma guia sendo discutida em um segmento de canal." border="false":::

### <a name="side-by-side-discussion"></a><span data-ttu-id="e2b10-182">Discussão lado a lado</span><span class="sxs-lookup"><span data-stu-id="e2b10-182">Side-by-side discussion</span></span>

<span data-ttu-id="e2b10-183">Os usuários podem ter uma conversa em seguida enquanto visualizam o conteúdo da guia.</span><span class="sxs-lookup"><span data-stu-id="e2b10-183">Users can have a conversation next while viewing the tab’s content.</span></span>

:::image type="content" source="../../assets/images/tabs/design-use-tab-side-chat.png" alt-text="O exemplo mostra uma guia com um chat aberto no lado direito." border="false":::

### <a name="permissions-and-role-based-views"></a><span data-ttu-id="e2b10-185">Permissões e visualizações baseadas em papéis</span><span class="sxs-lookup"><span data-stu-id="e2b10-185">Permissions and role-based views</span></span>

<span data-ttu-id="e2b10-186">A experiência da guia pode ser diferente para os usuários, dependendo de suas permissões.</span><span class="sxs-lookup"><span data-stu-id="e2b10-186">The tab experience may be different for users depending on their permissions.</span></span> <span data-ttu-id="e2b10-187">Por exemplo, um usuário pode acessar a guia sem ter que fazer login.</span><span class="sxs-lookup"><span data-stu-id="e2b10-187">For example, one user can access the tab without having to sign in.</span></span> <span data-ttu-id="e2b10-188">Outro usuário, no entanto, deve assinar e verá conteúdo ligeiramente diferente.</span><span class="sxs-lookup"><span data-stu-id="e2b10-188">Another user, however, must sign and will see slightly different content.</span></span>

## <a name="manage-a-tab"></a><span data-ttu-id="e2b10-189">Gerenciar uma guia</span><span class="sxs-lookup"><span data-stu-id="e2b10-189">Manage a tab</span></span>

<span data-ttu-id="e2b10-190">Você pode incluir opções para renomear, remover ou modificar uma guia.</span><span class="sxs-lookup"><span data-stu-id="e2b10-190">You can include options to rename, remove, or modify a tab.</span></span>

### <a name="anatomy-tab-menu"></a><span data-ttu-id="e2b10-191">Anatomia: Menu de guia</span><span class="sxs-lookup"><span data-stu-id="e2b10-191">Anatomy: Tab menu</span></span>

:::image type="content" source="../../assets/images/tabs/design-manage-tab-menu-anatomy.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de um menu de guia." border="false":::

|<span data-ttu-id="e2b10-193">Contador</span><span class="sxs-lookup"><span data-stu-id="e2b10-193">Counter</span></span>|<span data-ttu-id="e2b10-194">Descrição</span><span class="sxs-lookup"><span data-stu-id="e2b10-194">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="e2b10-195">1</span><span class="sxs-lookup"><span data-stu-id="e2b10-195">1</span></span>|<span data-ttu-id="e2b10-196">**Configurações**: (Opcional) Permite que os usuários modifiquem as configurações de uma guia após sua adicionada.</span><span class="sxs-lookup"><span data-stu-id="e2b10-196">**Settings**: (Optional) Allows users to modify a tab’s settings after it’s been added.</span></span>|
|<span data-ttu-id="e2b10-197">2</span><span class="sxs-lookup"><span data-stu-id="e2b10-197">2</span></span>|<span data-ttu-id="e2b10-198">**Renomear**: Permite que os usuários dêem à guia um nome mais significativo para a equipe.</span><span class="sxs-lookup"><span data-stu-id="e2b10-198">**Rename**: Allows users to give the tab a name that’s more meaningful to the team.</span></span>|
|<span data-ttu-id="e2b10-199">3</span><span class="sxs-lookup"><span data-stu-id="e2b10-199">3</span></span>|<span data-ttu-id="e2b10-200">**Remova**: Remove a guia do canal, bate-papo ou reunião.</span><span class="sxs-lookup"><span data-stu-id="e2b10-200">**Remove**: Removes the tab from the channel, chat, or meeting.</span></span>|

## <a name="tab-notifications-and-deep-linking"></a><span data-ttu-id="e2b10-201">Notificações de guias e vinculação profunda</span><span class="sxs-lookup"><span data-stu-id="e2b10-201">Tab notifications and deep linking</span></span>

<span data-ttu-id="e2b10-202">Você pode enviar uma mensagem com um link profundo para sua guia. Por exemplo, um cartão mostra um resumo dos dados de bugs que o usuário pode selecionar para ver todo o bug em uma guia. Enviar mensagens sobre atividade de guia aumenta a conscientização sem notificar explicitamente todos (ou seja, atividade sem ruído).</span><span class="sxs-lookup"><span data-stu-id="e2b10-202">You can send a message with a deep link to your tab. For example, a card shows a summary of bug data a user can select to see the entire bug in a tab. Sending messages about tab activity increases awareness without explicitly notifying everyone (i.e., activity without noise).</span></span> <span data-ttu-id="e2b10-203">Você também pode @mention usuários específicos, se necessário.</span><span class="sxs-lookup"><span data-stu-id="e2b10-203">You also can @mention specific users if needed.</span></span>

<span data-ttu-id="e2b10-204">Notifique os usuários da atividade da guia uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="e2b10-204">Notify users of tab activity one of the following ways:</span></span>

* <span data-ttu-id="e2b10-205">**Bot**: Este método é preferido especialmente se o segmento de guia for direcionado.</span><span class="sxs-lookup"><span data-stu-id="e2b10-205">**Bot**: This method is preferred especially if the tab thread is targeted.</span></span> <span data-ttu-id="e2b10-206">A conversa roscada da guia é colocada em exibição como recentemente ativa.</span><span class="sxs-lookup"><span data-stu-id="e2b10-206">The tab’s threaded conversation is moved into view as recently active.</span></span> <span data-ttu-id="e2b10-207">Este método também permite alguma sofisticação na forma como a notificação é enviada.</span><span class="sxs-lookup"><span data-stu-id="e2b10-207">This method also allows for some sophistication in how the notification is sent.</span></span>
* <span data-ttu-id="e2b10-208">**Mensagem**: Uma mensagem aparece no feed de atividades do usuário com um [link profundo para a guia](../../concepts/build-and-test/deep-links.md?view=msteams-client-js-latest&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="e2b10-208">**Message**: A message shows up in the user’s activity feed with a [deep link to the tab](../../concepts/build-and-test/deep-links.md?view=msteams-client-js-latest&preserve-view=true).</span></span>

## <a name="best-practices"></a><span data-ttu-id="e2b10-209">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="e2b10-209">Best practices</span></span>

<span data-ttu-id="e2b10-210">Use essas recomendações para criar uma experiência de aplicativo de qualidade:</span><span class="sxs-lookup"><span data-stu-id="e2b10-210">Use these recommendations to create a quality app experience:</span></span>

### <a name="collaboration"></a><span data-ttu-id="e2b10-211">Colaboração</span><span class="sxs-lookup"><span data-stu-id="e2b10-211">Collaboration</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-do.png" alt-text="A ilustração mostra o que fazer com o design de navegação de guias." border="false":::

#### <a name="do-facilitate-conversation"></a><span data-ttu-id="e2b10-213">Faça: Facilite a conversa</span><span class="sxs-lookup"><span data-stu-id="e2b10-213">Do: Facilitate conversation</span></span>

<span data-ttu-id="e2b10-214">Inclua conteúdo e componentes que as pessoas possam falar.</span><span class="sxs-lookup"><span data-stu-id="e2b10-214">Include content and components people can talk about.</span></span> <span data-ttu-id="e2b10-215">Se ele não se encaixa no contexto de um chat, canal ou reunião, ele não pertence à sua guia.</span><span class="sxs-lookup"><span data-stu-id="e2b10-215">If it doesn’t fit within the context of a chat, channel, or meeting, it doesn’t belong in your tab.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-dont.png" alt-text="Exemplo mostra o que não fazer com o design de navegação de guias." border="false":::

#### <a name="dont-treat-your-tab-like-any-other-webpage"></a><span data-ttu-id="e2b10-217">Não: Trate sua guia como qualquer outra página da Web</span><span class="sxs-lookup"><span data-stu-id="e2b10-217">Don't: Treat your tab like any other webpage</span></span>

<span data-ttu-id="e2b10-218">Uma guia não é uma página web que alguém pode visualizar uma vez.</span><span class="sxs-lookup"><span data-stu-id="e2b10-218">A tab isn’t a webpage someone might view once.</span></span> <span data-ttu-id="e2b10-219">Uma guia deve exibir seu conteúdo mais importante e relevante que as pessoas precisam para realizar algo juntos.</span><span class="sxs-lookup"><span data-stu-id="e2b10-219">A tab should display your most important, relevant content that people need to accomplish something together.</span></span>

   :::column-end:::
:::row-end:::

### <a name="navigation"></a><span data-ttu-id="e2b10-220">Navegação</span><span class="sxs-lookup"><span data-stu-id="e2b10-220">Navigation</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-do.png" alt-text="Exemplo mostrando o que fazer com o design de navegação de guias." border="false":::

#### <a name="do-limit-tasks-and-data"></a><span data-ttu-id="e2b10-222">Faça: Limite tarefas e dados</span><span class="sxs-lookup"><span data-stu-id="e2b10-222">Do: Limit tasks and data</span></span>

<span data-ttu-id="e2b10-223">As guias funcionam melhor quando abordam necessidades específicas.</span><span class="sxs-lookup"><span data-stu-id="e2b10-223">Tabs work best when they address specific needs.</span></span> <span data-ttu-id="e2b10-224">Inclua um conjunto limitado de tarefas e dados relevantes para a equipe ou grupo.</span><span class="sxs-lookup"><span data-stu-id="e2b10-224">Include a limited set of tasks and data relevant to the team or group.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-dont.png" alt-text="Ilustração mostrando o que não fazer com o design de navegação de guias." border="false":::

#### <a name="dont-embed-your-entire-app"></a><span data-ttu-id="e2b10-226">Não: incorpore todo o seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="e2b10-226">Don't: Embed your entire app</span></span>

<span data-ttu-id="e2b10-227">Usar uma guia para exibir um aplicativo inteiro com navegação em vários níveis e interações complexas leva à sobrecarga de informações.</span><span class="sxs-lookup"><span data-stu-id="e2b10-227">Using a tab to display an entire app with multi-level navigation and complex interactions leads to information overload.</span></span>

   :::column-end:::
:::row-end:::

### <a name="setup"></a><span data-ttu-id="e2b10-228">Configurar</span><span class="sxs-lookup"><span data-stu-id="e2b10-228">Setup</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-do.png" alt-text="Ilustração mostrando o que fazer com o design de configuração da guia." border="false":::

#### <a name="do-keep-it-simple"></a><span data-ttu-id="e2b10-230">Faça: Mantenha simples</span><span class="sxs-lookup"><span data-stu-id="e2b10-230">Do: Keep it simple</span></span>

<span data-ttu-id="e2b10-231">Se o seu aplicativo precisar de autenticação, tente integrar o SSO (Single Login) (Microsoft Single Sign-on) para uma experiência de login mais perfeita.</span><span class="sxs-lookup"><span data-stu-id="e2b10-231">If your app requires authentication, try integrating Microsoft single sign-on (SSO) for a more seamless sign-in experience.</span></span> <span data-ttu-id="e2b10-232">Além disso, inclua apenas informações e etapas essenciais para adicionar a guia.</span><span class="sxs-lookup"><span data-stu-id="e2b10-232">Also, only include essential information and steps to add the tab.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-dont.png" alt-text="Ilustração mostrando o que não fazer com o design de configuração da guia." border="false":::

#### <a name="dont-have-too-many-steps"></a><span data-ttu-id="e2b10-234">Não: Tenha muitos passos</span><span class="sxs-lookup"><span data-stu-id="e2b10-234">Don't: Have too many steps</span></span>

<span data-ttu-id="e2b10-235">Remova quaisquer etapas desnecessárias para adicionar uma guia.</span><span class="sxs-lookup"><span data-stu-id="e2b10-235">Remove any unnecessary steps for adding a tab.</span></span>

   :::column-end:::
:::row-end:::

### <a name="theming"></a><span data-ttu-id="e2b10-236">Temas</span><span class="sxs-lookup"><span data-stu-id="e2b10-236">Theming</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-do.png" alt-text="Ilustração mostrando o que fazer com o tema da guia." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a><span data-ttu-id="e2b10-238">Faça: Aproveite Teams tokens de cores</span><span class="sxs-lookup"><span data-stu-id="e2b10-238">Do: Take advantage of Teams color tokens</span></span>

<span data-ttu-id="e2b10-239">Cada Teams tema tem seu próprio esquema de cores.</span><span class="sxs-lookup"><span data-stu-id="e2b10-239">Each Teams theme has its own color scheme.</span></span> <span data-ttu-id="e2b10-240">Para lidar com as alterações do tema automaticamente, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">tokens de cores (Fluent UI)</a> em seu design.</span><span class="sxs-lookup"><span data-stu-id="e2b10-240">To handle theme changes automatically, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">color tokens (Fluent UI)</a> in your design.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-dont.png" alt-text="Ilustração mostrando o que não fazer com o tema da guia." border="false":::

#### <a name="dont-hard-code-color-values"></a><span data-ttu-id="e2b10-242">Não: Valores de cores de código rígido</span><span class="sxs-lookup"><span data-stu-id="e2b10-242">Don't: Hard code color values</span></span>

<span data-ttu-id="e2b10-243">Se você não usar Teams tokens de cor, seus designs serão menos escaláveis e levarão mais tempo para gerenciar.</span><span class="sxs-lookup"><span data-stu-id="e2b10-243">If you don’t use Teams color tokens, your designs will be less scalable and take more time to manage.</span></span>

   :::column-end:::
:::row-end:::
