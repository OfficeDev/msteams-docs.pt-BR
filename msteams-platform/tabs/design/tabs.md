---
title: Projetando sua guia para área de trabalho e Web
description: Saiba como criar uma guia do Teams (área de trabalho e Web) e obter o kit de interface do usuário do Microsoft Teams.
author: heath-hamilton
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 692a21c78dc86cbca5bf248e55d0332bd71c6b92
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2020
ms.locfileid: "49604640"
---
# <a name="designing-your-tab-for-microsoft-teams-desktop-and-web"></a><span data-ttu-id="b5397-103">Projetando sua guia para a área de trabalho e a Web do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="b5397-103">Designing your tab for Microsoft Teams desktop and web</span></span>

<span data-ttu-id="b5397-104">Uma guia é uma tela grande para o conteúdo que facilita a colaboração.</span><span class="sxs-lookup"><span data-stu-id="b5397-104">A tab is a large canvas for content that facilitates collaboration.</span></span> <span data-ttu-id="b5397-105">Para guiar o design do aplicativo, as informações a seguir descrevem e ilustra como as pessoas podem adicionar, usar e gerenciar guias no Teams.</span><span class="sxs-lookup"><span data-stu-id="b5397-105">To guide your app design, the following information describes and illustrates how people can add, use, and manage tabs in Teams.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="b5397-106">Kit de interface do usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="b5397-106">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="b5397-107">Você pode encontrar diretrizes de design de guia abrangentes, incluindo elementos que podem ser capturados e modificados conforme necessário, no kit de interface do usuário do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="b5397-107">You can find comprehensive tab design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span> <span data-ttu-id="b5397-108">O kit de interface do usuário também tem tópicos essenciais, como acessibilidade e dimensionamento responsivo que não são abordados aqui.</span><span class="sxs-lookup"><span data-stu-id="b5397-108">The UI kit also has essential topics such as accessibility and responsive sizing that aren't covered here.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b5397-109">Obter o kit de interface do usuário do Microsoft Teams (figma)</span><span class="sxs-lookup"><span data-stu-id="b5397-109">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-tab"></a><span data-ttu-id="b5397-110">Adicionar uma guia</span><span class="sxs-lookup"><span data-stu-id="b5397-110">Add a tab</span></span>

<span data-ttu-id="b5397-111">Você pode adicionar uma guia do repositório do Teams (AppSource) ou em um dos seguintes contextos:</span><span class="sxs-lookup"><span data-stu-id="b5397-111">You can add a tab from the Teams store (AppSource) or in one of the following contexts:</span></span>

* <span data-ttu-id="b5397-112">Chat</span><span class="sxs-lookup"><span data-stu-id="b5397-112">Chat</span></span>
* <span data-ttu-id="b5397-113">Canal</span><span class="sxs-lookup"><span data-stu-id="b5397-113">Channel</span></span>
* <span data-ttu-id="b5397-114">Reunião (antes, durante ou após a reunião)</span><span class="sxs-lookup"><span data-stu-id="b5397-114">Meeting (before, during, or after the meeting)</span></span>

<span data-ttu-id="b5397-115">O exemplo a seguir mostra como uma guia é adicionada em um canal.</span><span class="sxs-lookup"><span data-stu-id="b5397-115">The following example shows how a tab is added in a channel.</span></span>

:::image type="content" source="../../assets/images/tabs/design-add-tab.png" alt-text="O exemplo mostra uma guia que está sendo adicionada em um canal." border="false":::

## <a name="set-up-a-tab"></a><span data-ttu-id="b5397-117">Configurar uma guia</span><span class="sxs-lookup"><span data-stu-id="b5397-117">Set up a tab</span></span>

<span data-ttu-id="b5397-118">Há um pequeno processo de configuração para adicionar um aplicativo como uma guia de canal, chat ou reunião. A experiência é larga para você.</span><span class="sxs-lookup"><span data-stu-id="b5397-118">There's a short setup process to add an app as a channel, chat, or meeting tab. The experience is largely up to you.</span></span> <span data-ttu-id="b5397-119">Por exemplo, você pode ter uma descrição de como usar o aplicativo e algumas configurações opcionais.</span><span class="sxs-lookup"><span data-stu-id="b5397-119">For example, you could have a description of how to use the app and some optional settings.</span></span> <span data-ttu-id="b5397-120">Inclua uma etapa de logon aqui se você precisar autenticar usuários.</span><span class="sxs-lookup"><span data-stu-id="b5397-120">Include a sign-in step here if you need to authenticate users.</span></span>

### <a name="tab-configuration-modal"></a><span data-ttu-id="b5397-121">Configuração da guia modal</span><span class="sxs-lookup"><span data-stu-id="b5397-121">Tab configuration modal</span></span>

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-config.png" alt-text="O exemplo mostra uma configuração de guia modal." border="false":::

### <a name="anatomy-tab-configuration-modal"></a><span data-ttu-id="b5397-123">Anatomia: janela de configuração da guia</span><span class="sxs-lookup"><span data-stu-id="b5397-123">Anatomy: Tab configuration modal</span></span>

:::image type="content" source="../../assets/images/tabs/test.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de uma configuração de tabulação modal." border="false":::

|<span data-ttu-id="b5397-125">Contador</span><span class="sxs-lookup"><span data-stu-id="b5397-125">Counter</span></span>|<span data-ttu-id="b5397-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="b5397-126">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="b5397-127">1</span><span class="sxs-lookup"><span data-stu-id="b5397-127">1</span></span>|<span data-ttu-id="b5397-128">**Logotipo do aplicativo**: logotipo completo do aplicativo de cor do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b5397-128">**App logo**: Full color app logo of your app.</span></span>|
|<span data-ttu-id="b5397-129">2 </span><span class="sxs-lookup"><span data-stu-id="b5397-129">2</span></span>|<span data-ttu-id="b5397-130">**Nome do aplicativo**: nome completo do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b5397-130">**App name**: Full name of your app.</span></span>|
|<span data-ttu-id="b5397-131">3 </span><span class="sxs-lookup"><span data-stu-id="b5397-131">3</span></span>|<span data-ttu-id="b5397-132">**iframe**: espaço responsivo para o conteúdo do aplicativo (por exemplo, configurações de guia ou autenticação).</span><span class="sxs-lookup"><span data-stu-id="b5397-132">**iframe**: Responsive space for your app’s content (for example, tab settings or authentication).</span></span>|
|<span data-ttu-id="b5397-133">4 </span><span class="sxs-lookup"><span data-stu-id="b5397-133">4</span></span>|<span data-ttu-id="b5397-134">**Sobre link**: abre uma caixa de diálogo mostrando mais informações sobre o aplicativo, como uma descrição completa, permissões exigidas pelo aplicativo e links para sua política de privacidade e termos de serviço.</span><span class="sxs-lookup"><span data-stu-id="b5397-134">**About link**: Opens a dialog showing more information about the app, such as a full description, permissions required by the app, and links to your privacy policy and terms of service.</span></span>
|<span data-ttu-id="b5397-135">5 </span><span class="sxs-lookup"><span data-stu-id="b5397-135">5</span></span>|<span data-ttu-id="b5397-136">**Botão fechar**: fecha a janela restrita.</span><span class="sxs-lookup"><span data-stu-id="b5397-136">**Close button**: Closes the modal.</span></span>|
|<span data-ttu-id="b5397-137">6 </span><span class="sxs-lookup"><span data-stu-id="b5397-137">6</span></span>|<span data-ttu-id="b5397-138">**Opção notificar membros da equipe**: a janela restrita pergunta se você deseja criar uma postagem permitindo que outros saibam que você adicionou uma guia.</span><span class="sxs-lookup"><span data-stu-id="b5397-138">**Notify team members option**: The modal asks if you want to create a post letting others know you added a tab.</span></span>|
|<span data-ttu-id="b5397-139">7 </span><span class="sxs-lookup"><span data-stu-id="b5397-139">7</span></span>|<span data-ttu-id="b5397-140">**Botão voltar**: vai para a etapa anterior com base em onde a caixa de diálogo foi aberta.</span><span class="sxs-lookup"><span data-stu-id="b5397-140">**Back button**: Goes to the previous step based on where the dialog opened.</span></span>|
|<span data-ttu-id="b5397-141">8 </span><span class="sxs-lookup"><span data-stu-id="b5397-141">8</span></span>|<span data-ttu-id="b5397-142">**Botão salvar**: conclui a configuração da guia.</span><span class="sxs-lookup"><span data-stu-id="b5397-142">**Save button**: Completes tab setup.</span></span>|

### <a name="tab-authentication-with-single-sign-on"></a><span data-ttu-id="b5397-143">Autenticação de guia com logon único</span><span class="sxs-lookup"><span data-stu-id="b5397-143">Tab authentication with single sign-on</span></span>

<span data-ttu-id="b5397-144">Você pode adicionar uma etapa em que os usuários devem entrar primeiro com suas credenciais da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b5397-144">You can add a step in which users must first sign in with their Microsoft credentials.</span></span> <span data-ttu-id="b5397-145">Esse método de autenticação é chamado SSO (logon único).</span><span class="sxs-lookup"><span data-stu-id="b5397-145">This authentication method is called single sign-on (SSO).</span></span>

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-auth.png" alt-text="O exemplo mostra uma tela de autenticação de guia." border="false":::

### <a name="designing-a-tab-setup-with-ui-templates"></a><span data-ttu-id="b5397-147">Projetando uma configuração de guia com modelos de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="b5397-147">Designing a tab setup with UI templates</span></span>

<span data-ttu-id="b5397-148">Use um dos seguintes modelos de interface do usuário do Microsoft Teams para ajudar a criar sua experiência de configuração de guia:</span><span class="sxs-lookup"><span data-stu-id="b5397-148">Use one of the following Teams UI templates to help design your tab setup experience:</span></span>

* <span data-ttu-id="b5397-149">[Lista](../../concepts/design/design-teams-app-ui-templates.md#list): as listas podem exibir itens relacionados em um formato verificável e permitir que os usuários executem ações em uma lista inteira ou em itens individuais.</span><span class="sxs-lookup"><span data-stu-id="b5397-149">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="b5397-150">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): formulários são para coletar, validar e enviar entradas do usuário de forma estruturada.</span><span class="sxs-lookup"><span data-stu-id="b5397-150">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="b5397-151">[Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): o modelo de estado vazio pode ser usado para vários cenários, incluindo o login, experiências de tela de apresentação, mensagens de erro e muito mais.</span><span class="sxs-lookup"><span data-stu-id="b5397-151">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>

## <a name="view-a-tab"></a><span data-ttu-id="b5397-152">Exibir uma guia</span><span class="sxs-lookup"><span data-stu-id="b5397-152">View a tab</span></span>

<span data-ttu-id="b5397-153">As guias fornecem uma experiência Web de tela inteira no Microsoft Teams, onde você pode exibir conteúdo colaborativo, como quadros de tarefas e painéis, e informações importantes.</span><span class="sxs-lookup"><span data-stu-id="b5397-153">Tabs provide a full-screen web experience in Teams where you can display collaborative content—such task boards and dashboards—and important information.</span></span>

:::image type="content" source="../../assets/images/tabs/design-view-tab.png" alt-text="O exemplo mostra uma guia com um quadro de tarefas." border="false":::

### <a name="anatomy-tab"></a><span data-ttu-id="b5397-155">Anatomia: Tab</span><span class="sxs-lookup"><span data-stu-id="b5397-155">Anatomy: Tab</span></span>

:::image type="content" source="../../assets/images/tabs/design-view-tab-anatomy.png" alt-text="Ilustração mostrando a anatomia da interface de usuário de uma guia." border="false":::

|<span data-ttu-id="b5397-157">Contador</span><span class="sxs-lookup"><span data-stu-id="b5397-157">Counter</span></span>|<span data-ttu-id="b5397-158">Descrição</span><span class="sxs-lookup"><span data-stu-id="b5397-158">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="b5397-159">1</span><span class="sxs-lookup"><span data-stu-id="b5397-159">1</span></span>|<span data-ttu-id="b5397-160">**Nome da guia**: rótulo de navegação para sua guia.</span><span class="sxs-lookup"><span data-stu-id="b5397-160">**Tab name**: Navigation label for your tab.</span></span>|
|<span data-ttu-id="b5397-161">2 </span><span class="sxs-lookup"><span data-stu-id="b5397-161">2</span></span>|<span data-ttu-id="b5397-162">**Estouro de tabulação**: abre ações de tabulação, como renomear e remover.</span><span class="sxs-lookup"><span data-stu-id="b5397-162">**Tab overflow**: Opens tab actions, such as rename and remove.</span></span>|
|<span data-ttu-id="b5397-163">3 </span><span class="sxs-lookup"><span data-stu-id="b5397-163">3</span></span>|<span data-ttu-id="b5397-164">**Chat de guia**: abre um thread de chat à direita, permitindo que os usuários tenham uma conversa ao lado do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="b5397-164">**Tab chat**: Opens a chat thread on the right, allowing users to have a conversation next to the content.</span></span>|
|<span data-ttu-id="b5397-165">4 </span><span class="sxs-lookup"><span data-stu-id="b5397-165">4</span></span>|<span data-ttu-id="b5397-166">**iframe**: exibe o conteúdo da guia.</span><span class="sxs-lookup"><span data-stu-id="b5397-166">**iframe**: Displays your tab’s content.</span></span>

### <a name="designing-a-tab-with-ui-templates"></a><span data-ttu-id="b5397-167">Projetando uma guia com modelos de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="b5397-167">Designing a tab with UI templates</span></span>

<span data-ttu-id="b5397-168">Use um dos seguintes modelos de interface do usuário do Microsoft Teams para ajudar a criar sua experiência de guia:</span><span class="sxs-lookup"><span data-stu-id="b5397-168">Use one of the following Teams UI templates to help design your tab experience:</span></span>

* <span data-ttu-id="b5397-169">[Lista](../../concepts/design/design-teams-app-ui-templates.md#list): as listas podem exibir itens relacionados em um formato verificável e permitir que os usuários executem ações em uma lista inteira ou em itens individuais.</span><span class="sxs-lookup"><span data-stu-id="b5397-169">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="b5397-170">[Quadro de tarefas](../../concepts/design/design-teams-app-ui-templates.md#task-board): um quadro de tarefas, às vezes chamado de um quadro Kanban ou uma pista de baixo, é uma coleção de cartões usados para acompanhar o status de itens de trabalho ou tíquetes.</span><span class="sxs-lookup"><span data-stu-id="b5397-170">[Task board](../../concepts/design/design-teams-app-ui-templates.md#task-board): A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span>
* <span data-ttu-id="b5397-171">[Painel](../../concepts/design/design-teams-app-ui-templates.md#dashboard): um painel é uma tela contendo vários cartões que oferecem uma visão geral de dados ou conteúdo.</span><span class="sxs-lookup"><span data-stu-id="b5397-171">[Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): A dashboard is a canvas containing multiple cards that provide an overview of data or content.</span></span>
* <span data-ttu-id="b5397-172">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): formulários são para coletar, validar e enviar entradas do usuário de forma estruturada.</span><span class="sxs-lookup"><span data-stu-id="b5397-172">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="b5397-173">[Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): o modelo de estado vazio pode ser usado para vários cenários, incluindo o login, experiências de tela de apresentação, mensagens de erro e muito mais.</span><span class="sxs-lookup"><span data-stu-id="b5397-173">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>
* <span data-ttu-id="b5397-174">[NAV à esquerda](../../concepts/design/design-teams-app-ui-templates.md#left-nav): o modelo de navegação à esquerda pode ajudar se sua guia requer alguma navegação.</span><span class="sxs-lookup"><span data-stu-id="b5397-174">[Left nav](../../concepts/design/design-teams-app-ui-templates.md#left-nav): The left nav template can help if your tab requires some navigation.</span></span> <span data-ttu-id="b5397-175">Em geral, você deve manter a navegação de guia no mínimo.</span><span class="sxs-lookup"><span data-stu-id="b5397-175">In general, you should keep tab navigation to a minimum.</span></span>

## <a name="use-a-tab-to-collaborate"></a><span data-ttu-id="b5397-176">Usar uma guia para colaborar</span><span class="sxs-lookup"><span data-stu-id="b5397-176">Use a tab to collaborate</span></span>

<span data-ttu-id="b5397-177">As guias ajudam a facilitar as conversas sobre o conteúdo em um local central.</span><span class="sxs-lookup"><span data-stu-id="b5397-177">Tabs help facilitate conversations about content in a central location.</span></span>

### <a name="thread-discussion"></a><span data-ttu-id="b5397-178">Discussão de thread</span><span class="sxs-lookup"><span data-stu-id="b5397-178">Thread discussion</span></span>

<span data-ttu-id="b5397-179">Os usuários podem postar automaticamente para um canal ou chat após terem adicionado uma nova guia. Isso não apenas notifica os membros da equipe do novo conteúdo e fornece um link para Tab, permitindo que as pessoas comecem a falar sobre a guia.</span><span class="sxs-lookup"><span data-stu-id="b5397-179">Users can automatically post to a channel or chat once they’ve added a new tab. This not only notifies team members of the new content and provides a link to tab, it allows people to start talking about the tab.</span></span>

:::image type="content" source="../../assets/images/tabs/design-use-tab-channel.png" alt-text="O exemplo mostra uma guia sendo discutida em um thread de canal." border="false":::

### <a name="side-by-side-discussion"></a><span data-ttu-id="b5397-181">Discussão lado a lado</span><span class="sxs-lookup"><span data-stu-id="b5397-181">Side-by-side discussion</span></span>

<span data-ttu-id="b5397-182">Os usuários podem ter uma conversa ao lado de exibir o conteúdo da guia.</span><span class="sxs-lookup"><span data-stu-id="b5397-182">Users can have a conversation next while viewing the tab’s content.</span></span>

:::image type="content" source="../../assets/images/tabs/design-use-tab-side-chat.png" alt-text="O exemplo mostra uma guia com um chat aberto no lado direito." border="false":::

### <a name="permissions-and-role-based-views"></a><span data-ttu-id="b5397-184">Permissões e exibições baseadas em função</span><span class="sxs-lookup"><span data-stu-id="b5397-184">Permissions and role-based views</span></span>

<span data-ttu-id="b5397-185">A experiência de guia pode ser diferente para os usuários, dependendo de suas permissões.</span><span class="sxs-lookup"><span data-stu-id="b5397-185">The tab experience may be different for users depending on their permissions.</span></span> <span data-ttu-id="b5397-186">Por exemplo, um usuário pode acessar a guia sem precisar fazer logon.</span><span class="sxs-lookup"><span data-stu-id="b5397-186">For example, one user can access the tab without having to sign in.</span></span> <span data-ttu-id="b5397-187">Outro usuário, no entanto, deve assinar e receberá um conteúdo ligeiramente diferente.</span><span class="sxs-lookup"><span data-stu-id="b5397-187">Another user, however, must sign and will see slightly different content.</span></span>

## <a name="manage-a-tab"></a><span data-ttu-id="b5397-188">Gerenciar uma guia</span><span class="sxs-lookup"><span data-stu-id="b5397-188">Manage a tab</span></span>

<span data-ttu-id="b5397-189">Você pode incluir opções para renomear, remover ou modificar uma guia.</span><span class="sxs-lookup"><span data-stu-id="b5397-189">You can include options to rename, remove, or modify a tab.</span></span>

### <a name="anatomy-tab-menu"></a><span data-ttu-id="b5397-190">Anatomia: menu de guia</span><span class="sxs-lookup"><span data-stu-id="b5397-190">Anatomy: Tab menu</span></span>

:::image type="content" source="../../assets/images/tabs/design-manage-tab-menu-anatomy.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de um menu guia." border="false":::

|<span data-ttu-id="b5397-192">Contador</span><span class="sxs-lookup"><span data-stu-id="b5397-192">Counter</span></span>|<span data-ttu-id="b5397-193">Descrição</span><span class="sxs-lookup"><span data-stu-id="b5397-193">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="b5397-194">1</span><span class="sxs-lookup"><span data-stu-id="b5397-194">1</span></span>|<span data-ttu-id="b5397-195">**Configurações**: (opcional) permite que os usuários modifiquem as configurações de uma guia após serem adicionadas.</span><span class="sxs-lookup"><span data-stu-id="b5397-195">**Settings**: (Optional) Allows users to modify a tab’s settings after it’s been added.</span></span>|
|<span data-ttu-id="b5397-196">2 </span><span class="sxs-lookup"><span data-stu-id="b5397-196">2</span></span>|<span data-ttu-id="b5397-197">**Rename**: permite que os usuários forneçam um nome mais significativo para a guia para a equipe.</span><span class="sxs-lookup"><span data-stu-id="b5397-197">**Rename**: Allows users to give the tab a name that’s more meaningful to the team.</span></span>|
|<span data-ttu-id="b5397-198">3 </span><span class="sxs-lookup"><span data-stu-id="b5397-198">3</span></span>|<span data-ttu-id="b5397-199">**Remover**: Remove a guia do canal, chat ou reunião.</span><span class="sxs-lookup"><span data-stu-id="b5397-199">**Remove**: Removes the tab from the channel, chat, or meeting.</span></span>|

## <a name="tab-notifications-and-deep-linking"></a><span data-ttu-id="b5397-200">Notificações de guia e vinculação profunda</span><span class="sxs-lookup"><span data-stu-id="b5397-200">Tab notifications and deep linking</span></span>

<span data-ttu-id="b5397-201">Você pode enviar uma mensagem com um link profundo para sua guia. Por exemplo, um cartão mostra um resumo dos dados de erros que um usuário pode selecionar para ver todo o bug em uma guia. O envio de mensagens sobre a atividade de guia aumenta a conscientização sem notificar explicitamente todos (ou seja, atividades sem ruído).</span><span class="sxs-lookup"><span data-stu-id="b5397-201">You can send a message with a deep link to your tab. For example, a card shows a summary of bug data a user can select to see the entire bug in a tab. Sending messages about tab activity increases awareness without explicitly notifying everyone (i.e., activity without noise).</span></span> <span data-ttu-id="b5397-202">Você também pode @mention usuários específicos, se necessário.</span><span class="sxs-lookup"><span data-stu-id="b5397-202">You also can @mention specific users if needed.</span></span>

<span data-ttu-id="b5397-203">Notifique os usuários da atividade de guia de uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="b5397-203">Notify users of tab activity one of the following ways:</span></span>

* <span data-ttu-id="b5397-204">**Bot**: esse método é preferível, especialmente se o thread de guia for direcionado.</span><span class="sxs-lookup"><span data-stu-id="b5397-204">**Bot**: This method is preferred especially if the tab thread is targeted.</span></span> <span data-ttu-id="b5397-205">A conversa encadeada da guia é movida para o modo de exibição como ativo recentemente.</span><span class="sxs-lookup"><span data-stu-id="b5397-205">The tab’s threaded conversation is moved into view as recently active.</span></span> <span data-ttu-id="b5397-206">Esse método também permite uma certa sofisticação na forma como a notificação é enviada.</span><span class="sxs-lookup"><span data-stu-id="b5397-206">This method also allows for some sophistication in how the notification is sent.</span></span>
* <span data-ttu-id="b5397-207">**Mensagem**: uma mensagem aparece no feed de atividades do usuário com um [link profundo para a guia](../../concepts/build-and-test/deep-links.md?view=msteams-client-js-latest&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="b5397-207">**Message**: A message shows up in the user’s activity feed with a [deep link to the tab](../../concepts/build-and-test/deep-links.md?view=msteams-client-js-latest&preserve-view=true).</span></span>

## <a name="best-practices"></a><span data-ttu-id="b5397-208">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="b5397-208">Best practices</span></span>

### <a name="collaboration"></a><span data-ttu-id="b5397-209">Colaboração</span><span class="sxs-lookup"><span data-stu-id="b5397-209">Collaboration</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-do.png" alt-text="Ilustração mostrando o que fazer com o design de navegação de guia." border="false":::

#### <a name="do-facilitate-conversation"></a><span data-ttu-id="b5397-211">Fazer: facilitar a conversa</span><span class="sxs-lookup"><span data-stu-id="b5397-211">Do: Facilitate conversation</span></span>

<span data-ttu-id="b5397-212">Incluir conteúdo e componentes que as pessoas podem falar.</span><span class="sxs-lookup"><span data-stu-id="b5397-212">Include content and components people can talk about.</span></span> <span data-ttu-id="b5397-213">Se ele não couber no contexto de um chat, canal ou reunião, ele não pertence à sua guia.</span><span class="sxs-lookup"><span data-stu-id="b5397-213">If it doesn’t fit within the context of a chat, channel, or meeting, it doesn’t belong in your tab.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-dont.png" alt-text="Ilustração mostrando o que não fazer com o design de navegação de guia." border="false":::

#### <a name="dont-treat-your-tab-like-any-other-webpage"></a><span data-ttu-id="b5397-215">Não: trate sua guia como qualquer outra página da Web</span><span class="sxs-lookup"><span data-stu-id="b5397-215">Don't: Treat your tab like any other webpage</span></span>

<span data-ttu-id="b5397-216">Uma guia não é uma página da Web que alguém pode exibir uma vez.</span><span class="sxs-lookup"><span data-stu-id="b5397-216">A tab isn’t a webpage someone might view once.</span></span> <span data-ttu-id="b5397-217">Uma guia deve exibir o conteúdo mais importante e relevante que as pessoas precisam para realizar algo juntos.</span><span class="sxs-lookup"><span data-stu-id="b5397-217">A tab should display your most important, relevant content that people need to accomplish something together.</span></span>

   :::column-end:::
:::row-end:::

### <a name="navigation"></a><span data-ttu-id="b5397-218">Navegação</span><span class="sxs-lookup"><span data-stu-id="b5397-218">Navigation</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-do.png" alt-text="Ilustração mostrando o que fazer com o design de navegação de guia." border="false":::

#### <a name="do-limit-tasks-and-data"></a><span data-ttu-id="b5397-220">Fazer: limitar tarefas e dados</span><span class="sxs-lookup"><span data-stu-id="b5397-220">Do: Limit tasks and data</span></span>

<span data-ttu-id="b5397-221">As guias funcionam melhor quando atendem a necessidades específicas.</span><span class="sxs-lookup"><span data-stu-id="b5397-221">Tabs work best when they address specific needs.</span></span> <span data-ttu-id="b5397-222">Inclua um conjunto limitado de tarefas e dados relevantes para a equipe ou grupo.</span><span class="sxs-lookup"><span data-stu-id="b5397-222">Include a limited set of tasks and data relevant to the team or group.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-dont.png" alt-text="Ilustração mostrando o que não fazer com o design de navegação de guia." border="false":::

#### <a name="dont-embed-your-entire-app"></a><span data-ttu-id="b5397-224">Não: Incorpore todo o aplicativo</span><span class="sxs-lookup"><span data-stu-id="b5397-224">Don't: Embed your entire app</span></span>

<span data-ttu-id="b5397-225">Usar uma guia para exibir um aplicativo inteiro com navegação de vários níveis e interações complexas leva à sobrecarga de informações.</span><span class="sxs-lookup"><span data-stu-id="b5397-225">Using a tab to display an entire app with multi-level navigation and complex interactions leads to information overload.</span></span>

   :::column-end:::
:::row-end:::

### <a name="setup"></a><span data-ttu-id="b5397-226">Configurar</span><span class="sxs-lookup"><span data-stu-id="b5397-226">Setup</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-do.png" alt-text="Ilustração mostrando o que fazer com o design da configuração de guia." border="false":::

#### <a name="do-keep-it-simple"></a><span data-ttu-id="b5397-228">Fazer: simplificar</span><span class="sxs-lookup"><span data-stu-id="b5397-228">Do: Keep it simple</span></span>

<span data-ttu-id="b5397-229">Se seu aplicativo requer autenticação, tente integrar o Microsoft Single Sign-on (SSO) para obter uma experiência de entrada mais contínua.</span><span class="sxs-lookup"><span data-stu-id="b5397-229">If your app requires authentication, try integrating Microsoft single sign-on (SSO) for a more seamless sign-in experience.</span></span> <span data-ttu-id="b5397-230">Além disso, inclua apenas as informações essenciais e as etapas para adicionar a guia.</span><span class="sxs-lookup"><span data-stu-id="b5397-230">Also, only include essential information and steps to add the tab.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-dont.png" alt-text="Ilustração mostrando o que não fazer com o design da configuração de guia." border="false":::

#### <a name="dont-have-too-many-steps"></a><span data-ttu-id="b5397-232">Não: ter muitas etapas</span><span class="sxs-lookup"><span data-stu-id="b5397-232">Don't: Have too many steps</span></span>

<span data-ttu-id="b5397-233">Remova as etapas desnecessárias para adicionar uma guia.</span><span class="sxs-lookup"><span data-stu-id="b5397-233">Remove any unnecessary steps for adding a tab.</span></span>

   :::column-end:::
:::row-end:::

### <a name="theming"></a><span data-ttu-id="b5397-234">Temas</span><span class="sxs-lookup"><span data-stu-id="b5397-234">Theming</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-do.png" alt-text="Ilustração mostrando o que fazer com os temas de tabulação." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a><span data-ttu-id="b5397-236">Fazer: aproveitar os tokens de cores do teams</span><span class="sxs-lookup"><span data-stu-id="b5397-236">Do: Take advantage of Teams color tokens</span></span>

<span data-ttu-id="b5397-237">Cada tema do teams tem seu próprio esquema de cores.</span><span class="sxs-lookup"><span data-stu-id="b5397-237">Each Teams theme has its own color scheme.</span></span> <span data-ttu-id="b5397-238">Para lidar automaticamente com alterações de temas, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">tokens de cor (IU fluente)</a> em seu design.</span><span class="sxs-lookup"><span data-stu-id="b5397-238">To handle theme changes automatically, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">color tokens (Fluent UI)</a> in your design.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-dont.png" alt-text="Ilustração mostrando o que não fazer com os temas de tabulação." border="false":::

#### <a name="dont-hard-code-color-values"></a><span data-ttu-id="b5397-240">Não: valores de cor de código fixo</span><span class="sxs-lookup"><span data-stu-id="b5397-240">Don't: Hard code color values</span></span>

<span data-ttu-id="b5397-241">Se você não usar tokens de cores do Teams, seus designs serão menos escalonáveis e levará mais tempo para gerenciar.</span><span class="sxs-lookup"><span data-stu-id="b5397-241">If you don’t use Teams color tokens, your designs will be less scalable and take more time to manage.</span></span>

   :::column-end:::
:::row-end:::

## <a name="validate-your-design"></a><span data-ttu-id="b5397-242">Validar o design</span><span class="sxs-lookup"><span data-stu-id="b5397-242">Validate your design</span></span>

<span data-ttu-id="b5397-243">Se você planeja publicar seu aplicativo no AppSource, você deve compreender os problemas de design que geralmente causam falha nos aplicativos durante o envio.</span><span class="sxs-lookup"><span data-stu-id="b5397-243">If you plan to publish your app to AppSource, you should understand the design issues that commonly cause apps to fail during submission.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b5397-244">Verificar diretrizes de validação de design</span><span class="sxs-lookup"><span data-stu-id="b5397-244">Check design validation guidelines</span></span>](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
