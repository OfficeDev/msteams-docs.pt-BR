---
title: Guias de design para desktop, web e mobile
description: Saiba como projetar uma guia Teams para desktop, web e celular e obter o Microsoft Teams de interface do usuário.
author: heath-hamilton
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: f1823a064cd182d0271aa97bef58ec724c7819b3
ms.sourcegitcommit: 33a43c61f27ae750776616b2cf90159455d8ba6c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2021
ms.locfileid: "52721840"
---
# <a name="design-your-tab-for-microsoft-teams"></a><span data-ttu-id="1fee4-103">Projete sua guia para Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="1fee4-103">Design your tab for Microsoft Teams</span></span>

<span data-ttu-id="1fee4-104">Uma guia é uma tela grande para o conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1fee4-104">A tab is a large canvas for your app content.</span></span> <span data-ttu-id="1fee4-105">Para orientar o design do aplicativo, as informações a seguir descrevem e ilustram como as pessoas podem adicionar, usar e gerenciar guias no Teams.</span><span class="sxs-lookup"><span data-stu-id="1fee4-105">To guide your app design, the following information describes and illustrates how people can add, use, and manage tabs in Teams.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="1fee4-106">Kit de Interface do Usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="1fee4-106">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="1fee4-107">Você pode encontrar diretrizes abrangentes de design de guia, incluindo elementos que você pode pegar e modificar conforme necessário, no Kit Microsoft Teams interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="1fee4-107">You can find comprehensive tab design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span> <span data-ttu-id="1fee4-108">O kit de interface do usuário também tem tópicos essenciais, como acessibilidade e tamanho responsivo que não são abordados aqui.</span><span class="sxs-lookup"><span data-stu-id="1fee4-108">The UI kit also has essential topics such as accessibility and responsive sizing that aren't covered here.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1fee4-109">Obtenha o Kit de Interface do Usuário do Microsoft Teams (Figma)</span><span class="sxs-lookup"><span data-stu-id="1fee4-109">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-tab"></a><span data-ttu-id="1fee4-110">Adicionar uma guia</span><span class="sxs-lookup"><span data-stu-id="1fee4-110">Add a tab</span></span>

<span data-ttu-id="1fee4-111">Você pode adicionar uma guia do Teams (AppSource) ou em um dos seguintes contextos:</span><span class="sxs-lookup"><span data-stu-id="1fee4-111">You can add a tab from the Teams store (AppSource) or in one of the following contexts:</span></span>

* <span data-ttu-id="1fee4-112">Chat</span><span class="sxs-lookup"><span data-stu-id="1fee4-112">Chat</span></span>
* <span data-ttu-id="1fee4-113">Canal</span><span class="sxs-lookup"><span data-stu-id="1fee4-113">Channel</span></span>
* <span data-ttu-id="1fee4-114">Reunião (antes, durante ou após a reunião)</span><span class="sxs-lookup"><span data-stu-id="1fee4-114">Meeting (before, during, or after the meeting)</span></span>

# <a name="desktop"></a>[<span data-ttu-id="1fee4-115">Desktop</span><span class="sxs-lookup"><span data-stu-id="1fee4-115">Desktop</span></span>](#tab/desktop)

<span data-ttu-id="1fee4-116">O exemplo a seguir mostra como os usuários podem adicionar uma guia em um canal.</span><span class="sxs-lookup"><span data-stu-id="1fee4-116">The following example shows how users can add a tab in a channel.</span></span>

:::image type="content" source="../../assets/images/tabs/design-add-tab.png" alt-text="Exemplo mostra uma guia sendo adicionada a um canal." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="1fee4-118">Mobile</span><span class="sxs-lookup"><span data-stu-id="1fee4-118">Mobile</span></span>](#tab/mobile)

<span data-ttu-id="1fee4-119">Os usuários podem acessar guias selecionando o botão **Mais** no canal (exemplo abaixo) ou o chat no qual foram adicionados.</span><span class="sxs-lookup"><span data-stu-id="1fee4-119">Users can access tabs by selecting the **More** button in the channel (example below) or chat in which they've been added.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-design-access-tab.png" alt-text="Exemplo mostra uma guia móvel sendo adicionada em um canal." border="false":::

---

## <a name="set-up-a-tab"></a><span data-ttu-id="1fee4-121">Configurar uma guia</span><span class="sxs-lookup"><span data-stu-id="1fee4-121">Set up a tab</span></span>

<span data-ttu-id="1fee4-122">Há um curto processo de instalação para adicionar um aplicativo como canal, chat ou guia de reunião. A experiência é em grande parte com você.</span><span class="sxs-lookup"><span data-stu-id="1fee4-122">There's a short setup process to add an app as a channel, chat, or meeting tab. The experience is largely up to you.</span></span> <span data-ttu-id="1fee4-123">Por exemplo, você pode ter uma descrição de como usar o aplicativo e algumas configurações opcionais.</span><span class="sxs-lookup"><span data-stu-id="1fee4-123">For example, you could have a description of how to use the app and some optional settings.</span></span> <span data-ttu-id="1fee4-124">Inclua uma etapa de login aqui se você precisar autenticar usuários.</span><span class="sxs-lookup"><span data-stu-id="1fee4-124">Include a sign-in step here if you need to authenticate users.</span></span>

### <a name="tab-configuration-dialog"></a><span data-ttu-id="1fee4-125">Caixa de diálogo configuração de tabulação</span><span class="sxs-lookup"><span data-stu-id="1fee4-125">Tab configuration dialog</span></span>

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-config.png" alt-text="Exemplo mostra um modal de configuração de tabulação." border="false":::

### <a name="anatomy-tab-configuration-dialog"></a><span data-ttu-id="1fee4-127">Anatomia: caixa de diálogo de configuração de tabulação</span><span class="sxs-lookup"><span data-stu-id="1fee4-127">Anatomy: Tab configuration dialog</span></span>

:::image type="content" source="../../assets/images/tabs/test.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de um modal de configuração de tabulação." border="false":::

|<span data-ttu-id="1fee4-129">Contador</span><span class="sxs-lookup"><span data-stu-id="1fee4-129">Counter</span></span>|<span data-ttu-id="1fee4-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="1fee4-130">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="1fee4-131">1</span><span class="sxs-lookup"><span data-stu-id="1fee4-131">1</span></span>|<span data-ttu-id="1fee4-132">**Logotipo do aplicativo**: logotipo completo do aplicativo de cores do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1fee4-132">**App logo**: Full color app logo of your app.</span></span>|
|<span data-ttu-id="1fee4-133">2</span><span class="sxs-lookup"><span data-stu-id="1fee4-133">2</span></span>|<span data-ttu-id="1fee4-134">**Nome do** aplicativo : Nome completo do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1fee4-134">**App name**: Full name of your app.</span></span>|
|<span data-ttu-id="1fee4-135">3</span><span class="sxs-lookup"><span data-stu-id="1fee4-135">3</span></span>|<span data-ttu-id="1fee4-136">**iframe**: espaço responsivo para o conteúdo do aplicativo (por exemplo, configurações de tabulação ou autenticação).</span><span class="sxs-lookup"><span data-stu-id="1fee4-136">**iframe**: Responsive space for your app’s content (for example, tab settings or authentication).</span></span>|
|<span data-ttu-id="1fee4-137">4 </span><span class="sxs-lookup"><span data-stu-id="1fee4-137">4</span></span>|<span data-ttu-id="1fee4-138">**Sobre o link**: abre uma caixa de diálogo mostrando mais informações sobre o aplicativo, como uma descrição completa, permissões exigidas pelo aplicativo e links para sua política de privacidade e termos de serviço.</span><span class="sxs-lookup"><span data-stu-id="1fee4-138">**About link**: Opens a dialog showing more information about the app, such as a full description, permissions required by the app, and links to your privacy policy and terms of service.</span></span>|
|<span data-ttu-id="1fee4-139">5 </span><span class="sxs-lookup"><span data-stu-id="1fee4-139">5</span></span>|<span data-ttu-id="1fee4-140">**Botão Fechar**: fecha a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="1fee4-140">**Close button**: Closes the dialog.</span></span>|
|<span data-ttu-id="1fee4-141">6 </span><span class="sxs-lookup"><span data-stu-id="1fee4-141">6</span></span>|<span data-ttu-id="1fee4-142">**Opção Notificar os** membros da equipe : A caixa de diálogo pergunta aos usuários se eles querem criar uma postagem informando aos outros que adicionaram uma guia.</span><span class="sxs-lookup"><span data-stu-id="1fee4-142">**Notify team members option**: The dialog asks users if they want to create a post letting others know they added a tab.</span></span>|
|<span data-ttu-id="1fee4-143">7 </span><span class="sxs-lookup"><span data-stu-id="1fee4-143">7</span></span>|<span data-ttu-id="1fee4-144">**Botão Voltar**: vai para a etapa anterior com base em onde a caixa de diálogo foi aberta.</span><span class="sxs-lookup"><span data-stu-id="1fee4-144">**Back button**: Goes to the previous step based on where the dialog opened.</span></span>|
|<span data-ttu-id="1fee4-145">8 </span><span class="sxs-lookup"><span data-stu-id="1fee4-145">8</span></span>|<span data-ttu-id="1fee4-146">**Botão Salvar**: Conclui a configuração da guia.</span><span class="sxs-lookup"><span data-stu-id="1fee4-146">**Save button**: Completes tab setup.</span></span>|

### <a name="tab-authentication-with-single-sign-on"></a><span data-ttu-id="1fee4-147">Autenticação de tabulação com login único</span><span class="sxs-lookup"><span data-stu-id="1fee4-147">Tab authentication with single sign-on</span></span>

<span data-ttu-id="1fee4-148">Você pode adicionar uma etapa na qual os usuários devem entrar primeiro com suas credenciais da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1fee4-148">You can add a step in which users must first sign in with their Microsoft credentials.</span></span> <span data-ttu-id="1fee4-149">Esse método de autenticação é chamado de SSO (single sign-on).</span><span class="sxs-lookup"><span data-stu-id="1fee4-149">This authentication method is called single sign-on (SSO).</span></span>

:::image type="content" source="../../assets/images/tabs/design-set-up-tab-auth.png" alt-text="Exemplo mostra uma tela de autenticação de tabulação." border="false":::

### <a name="design-a-tab-setup-with-ui-templates"></a><span data-ttu-id="1fee4-151">Projetar uma configuração de tabulação com modelos de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="1fee4-151">Design a tab setup with UI templates</span></span>

<span data-ttu-id="1fee4-152">Use um dos seguintes modelos Teams de interface do usuário para ajudar a projetar sua experiência de configuração de tabulação:</span><span class="sxs-lookup"><span data-stu-id="1fee4-152">Use one of the following Teams UI templates to help design your tab setup experience:</span></span>

* <span data-ttu-id="1fee4-153">[Lista](../../concepts/design/design-teams-app-ui-templates.md#list): as listas podem exibir itens relacionados em um formato digitalizável e permitir que os usuários tomem ações em uma lista inteira ou itens individuais.</span><span class="sxs-lookup"><span data-stu-id="1fee4-153">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="1fee4-154">[Formulário](../../concepts/design/design-teams-app-ui-templates.md#form): Os formulários são para coletar, validar e enviar entrada do usuário de forma estruturada.</span><span class="sxs-lookup"><span data-stu-id="1fee4-154">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="1fee4-155">[Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): o modelo de estado vazio pode ser usado para muitos cenários, incluindo entrar, experiências de primeira executar, mensagens de erro e muito mais.</span><span class="sxs-lookup"><span data-stu-id="1fee4-155">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>

## <a name="view-a-tab"></a><span data-ttu-id="1fee4-156">Exibir uma guia</span><span class="sxs-lookup"><span data-stu-id="1fee4-156">View a tab</span></span>

<span data-ttu-id="1fee4-157">As guias fornecem uma experiência da Web de tela inteira em Teams onde você pode exibir conteúdo colaborativo, como painéis e painéis de tarefas, e informações importantes.</span><span class="sxs-lookup"><span data-stu-id="1fee4-157">Tabs provide a full-screen web experience in Teams where you can display collaborative content—such task boards and dashboards—and important information.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="1fee4-158">Desktop</span><span class="sxs-lookup"><span data-stu-id="1fee4-158">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/tabs/design-view-tab.png" alt-text="Exemplo mostra uma guia com um quadro de tarefas." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="1fee4-160">Mobile</span><span class="sxs-lookup"><span data-stu-id="1fee4-160">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/tabs/mobile-design-view-tab.png" alt-text="Exemplo mostra uma guia móvel com um quadro de tarefas." border="false":::

---

### <a name="anatomy-tab"></a><span data-ttu-id="1fee4-162">Anatomia: Guia</span><span class="sxs-lookup"><span data-stu-id="1fee4-162">Anatomy: Tab</span></span>

# <a name="desktop"></a>[<span data-ttu-id="1fee4-163">Desktop</span><span class="sxs-lookup"><span data-stu-id="1fee4-163">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/tabs/design-view-tab-anatomy.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de uma guia." border="false":::

|<span data-ttu-id="1fee4-165">Contador</span><span class="sxs-lookup"><span data-stu-id="1fee4-165">Counter</span></span>|<span data-ttu-id="1fee4-166">Descrição</span><span class="sxs-lookup"><span data-stu-id="1fee4-166">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="1fee4-167">1</span><span class="sxs-lookup"><span data-stu-id="1fee4-167">1</span></span>|<span data-ttu-id="1fee4-168">**Nome da guia**: Rótulo de navegação para sua guia.</span><span class="sxs-lookup"><span data-stu-id="1fee4-168">**Tab name**: Navigation label for your tab.</span></span>|
|<span data-ttu-id="1fee4-169">2</span><span class="sxs-lookup"><span data-stu-id="1fee4-169">2</span></span>|<span data-ttu-id="1fee4-170">**Estouro da** guia : abre ações de guia, como renomear e remover.</span><span class="sxs-lookup"><span data-stu-id="1fee4-170">**Tab overflow**: Opens tab actions, such as rename and remove.</span></span>|
|<span data-ttu-id="1fee4-171">3</span><span class="sxs-lookup"><span data-stu-id="1fee4-171">3</span></span>|<span data-ttu-id="1fee4-172">**Chat de tabulação**: abre um chat à direita, permitindo que os usuários tenham uma conversa ao lado do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="1fee4-172">**Tab chat**: Opens a chat to the right, allowing users to have a conversation next to the content.</span></span>|
|<span data-ttu-id="1fee4-173">4 </span><span class="sxs-lookup"><span data-stu-id="1fee4-173">4</span></span>|<span data-ttu-id="1fee4-174">**iframe**: exibe o conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1fee4-174">**iframe**: Displays your app content.</span></span>|

# <a name="mobile"></a>[<span data-ttu-id="1fee4-175">Mobile</span><span class="sxs-lookup"><span data-stu-id="1fee4-175">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/tabs/mobile-design-view-tab-anatomy.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de uma guia." border="false":::

|<span data-ttu-id="1fee4-177">Contador</span><span class="sxs-lookup"><span data-stu-id="1fee4-177">Counter</span></span>|<span data-ttu-id="1fee4-178">Descrição</span><span class="sxs-lookup"><span data-stu-id="1fee4-178">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="1fee4-179">1</span><span class="sxs-lookup"><span data-stu-id="1fee4-179">1</span></span>|<span data-ttu-id="1fee4-180">**Nome da guia**: Rótulo de navegação para sua guia.</span><span class="sxs-lookup"><span data-stu-id="1fee4-180">**Tab name**: Navigation label for your tab.</span></span>|
|<span data-ttu-id="1fee4-181">2</span><span class="sxs-lookup"><span data-stu-id="1fee4-181">2</span></span>|<span data-ttu-id="1fee4-182">**Chat de tabulação**: abre um chat que permite que os usuários tenham uma conversa ao lado do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="1fee4-182">**Tab chat**: Opens a chat that allows users to have a conversation next to the content.</span></span>|
|<span data-ttu-id="1fee4-183">3</span><span class="sxs-lookup"><span data-stu-id="1fee4-183">3</span></span>|<span data-ttu-id="1fee4-184">**webview**: exibe o conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1fee4-184">**webview**: Displays your app content.</span></span>|

---

### <a name="designing-a-tab-with-ui-templates-and-advanced-components"></a><span data-ttu-id="1fee4-185">Criar uma guia com modelos de interface do usuário e componentes avançados</span><span class="sxs-lookup"><span data-stu-id="1fee4-185">Designing a tab with UI templates and advanced components</span></span>

<span data-ttu-id="1fee4-186">Use um dos seguintes Teams e componentes para ajudar a projetar sua experiência de tabulação:</span><span class="sxs-lookup"><span data-stu-id="1fee4-186">Use one of the following Teams templates and components to help design your tab experience:</span></span>

* <span data-ttu-id="1fee4-187">[Lista](../../concepts/design/design-teams-app-ui-templates.md#list): as listas podem exibir itens relacionados em um formato digitalizável e permitir que os usuários tomem ações em uma lista inteira ou itens individuais.</span><span class="sxs-lookup"><span data-stu-id="1fee4-187">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="1fee4-188">[Quadro de](../../concepts/design/design-teams-app-ui-templates.md#task-board)tarefas : um quadro de tarefas, às vezes chamado de quadro kanban ou faixas de nadador, é uma coleção de cartões frequentemente usada para rastrear o status de itens de trabalho ou tíquetes.</span><span class="sxs-lookup"><span data-stu-id="1fee4-188">[Task board](../../concepts/design/design-teams-app-ui-templates.md#task-board): A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span>
* <span data-ttu-id="1fee4-189">[Painel](../../concepts/design/design-teams-app-ui-templates.md#dashboard): um painel é uma tela que contém vários cartões que fornecem uma visão geral dos dados ou conteúdo.</span><span class="sxs-lookup"><span data-stu-id="1fee4-189">[Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): A dashboard is a canvas containing multiple cards that provide an overview of data or content.</span></span>
* <span data-ttu-id="1fee4-190">[Formulário](../../concepts/design/design-teams-app-ui-templates.md#form): Os formulários são para coletar, validar e enviar entrada do usuário de forma estruturada.</span><span class="sxs-lookup"><span data-stu-id="1fee4-190">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="1fee4-191">[Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): o modelo de estado vazio pode ser usado para muitos cenários, incluindo entrar, experiências de primeira executar, mensagens de erro e muito mais.</span><span class="sxs-lookup"><span data-stu-id="1fee4-191">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>
* <span data-ttu-id="1fee4-192">[Navegação à esquerda](../../concepts/design/design-teams-app-advanced-ui-components.md#left-nav): O componente de navegação esquerdo pode ajudar se sua guia exigir alguma navegação.</span><span class="sxs-lookup"><span data-stu-id="1fee4-192">[Left nav](../../concepts/design/design-teams-app-advanced-ui-components.md#left-nav): The left nav component can help if your tab requires some navigation.</span></span> <span data-ttu-id="1fee4-193">Em geral, você deve manter a navegação de tabulação no mínimo.</span><span class="sxs-lookup"><span data-stu-id="1fee4-193">In general, you should keep tab navigation to a minimum.</span></span>

## <a name="use-a-tab-to-collaborate"></a><span data-ttu-id="1fee4-194">Usar uma guia para colaborar</span><span class="sxs-lookup"><span data-stu-id="1fee4-194">Use a tab to collaborate</span></span>

<span data-ttu-id="1fee4-195">Guias ajudam a facilitar conversas sobre conteúdo em um local central.</span><span class="sxs-lookup"><span data-stu-id="1fee4-195">Tabs help facilitate conversations about content in a central location.</span></span>

### <a name="thread-discussion"></a><span data-ttu-id="1fee4-196">Discussão de thread</span><span class="sxs-lookup"><span data-stu-id="1fee4-196">Thread discussion</span></span>

<span data-ttu-id="1fee4-197">Os usuários podem postar automaticamente em um canal ou chat depois de adicionarem uma nova guia. Isso não apenas notifica os membros da equipe do novo conteúdo e fornece um link para guia, ele permite que as pessoas comecem a falar sobre a guia.</span><span class="sxs-lookup"><span data-stu-id="1fee4-197">Users can automatically post to a channel or chat once they’ve added a new tab. This not only notifies team members of the new content and provides a link to tab, it allows people to start talking about the tab.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="1fee4-198">Desktop</span><span class="sxs-lookup"><span data-stu-id="1fee4-198">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/tabs/design-use-tab-channel.png" alt-text="Exemplo mostra uma guia sendo discutida em um thread de canal." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="1fee4-200">Mobile</span><span class="sxs-lookup"><span data-stu-id="1fee4-200">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/tabs/mobile-design-use-tab-channel.png" alt-text="Exemplo mostra uma guia móvel sendo discutida em um thread de canal." border="false":::

---

### <a name="tab-chat"></a><span data-ttu-id="1fee4-202">Chat de tabulação</span><span class="sxs-lookup"><span data-stu-id="1fee4-202">Tab chat</span></span>

<span data-ttu-id="1fee4-203">Os usuários podem ter uma conversa ao lado do conteúdo da guia que estão exibindo.</span><span class="sxs-lookup"><span data-stu-id="1fee4-203">Users can have a conversation next to the tab content they're viewing.</span></span> <span data-ttu-id="1fee4-204">Na área de trabalho, o chat é aberto ao lado do conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1fee4-204">On desktop, the chat opens to the side of the app content.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="1fee4-205">Desktop</span><span class="sxs-lookup"><span data-stu-id="1fee4-205">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/tabs/design-use-tab-side-chat.png" alt-text="Exemplo mostra uma guia com um chat aberto no lado direito." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="1fee4-207">Mobile</span><span class="sxs-lookup"><span data-stu-id="1fee4-207">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/tabs/mobile-design-use-tab-side-chat.png" alt-text="Exemplo mostra uma guia móvel com uma área de chat no contexto." border="false":::

---

### <a name="permissions-and-role-based-views"></a><span data-ttu-id="1fee4-209">Permissões e exibições baseadas em função</span><span class="sxs-lookup"><span data-stu-id="1fee4-209">Permissions and role-based views</span></span>

<span data-ttu-id="1fee4-210">A experiência de tabulação pode ser diferente para os usuários, dependendo de suas permissões.</span><span class="sxs-lookup"><span data-stu-id="1fee4-210">The tab experience may be different for users depending on their permissions.</span></span> <span data-ttu-id="1fee4-211">Por exemplo, um usuário pode acessar a guia sem precisar entrar.</span><span class="sxs-lookup"><span data-stu-id="1fee4-211">For example, one user can access the tab without having to sign in.</span></span> <span data-ttu-id="1fee4-212">Outro usuário, no entanto, deve entrar e ver conteúdo ligeiramente diferente.</span><span class="sxs-lookup"><span data-stu-id="1fee4-212">Another user, however, must sign in and see slightly different content.</span></span>

## <a name="manage-a-tab"></a><span data-ttu-id="1fee4-213">Gerenciar uma guia</span><span class="sxs-lookup"><span data-stu-id="1fee4-213">Manage a tab</span></span>

<span data-ttu-id="1fee4-214">Você pode incluir opções para renomear, remover ou modificar uma guia.</span><span class="sxs-lookup"><span data-stu-id="1fee4-214">You can include options to rename, remove, or modify a tab.</span></span>

### <a name="anatomy-tab-menu"></a><span data-ttu-id="1fee4-215">Anatomia: menu Tab</span><span class="sxs-lookup"><span data-stu-id="1fee4-215">Anatomy: Tab menu</span></span>

# <a name="desktop"></a>[<span data-ttu-id="1fee4-216">Desktop</span><span class="sxs-lookup"><span data-stu-id="1fee4-216">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/tabs/design-manage-tab-menu-anatomy.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de um menu de tabulação." border="false":::

|<span data-ttu-id="1fee4-218">Contador</span><span class="sxs-lookup"><span data-stu-id="1fee4-218">Counter</span></span>|<span data-ttu-id="1fee4-219">Descrição</span><span class="sxs-lookup"><span data-stu-id="1fee4-219">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="1fee4-220">1</span><span class="sxs-lookup"><span data-stu-id="1fee4-220">1</span></span>|<span data-ttu-id="1fee4-221">**Configurações**: (Opcional) Permite que os usuários modifiquem as configurações de uma guia depois que ela foi adicionada.</span><span class="sxs-lookup"><span data-stu-id="1fee4-221">**Settings**: (Optional) Allows users to modify a tab’s settings after it’s been added.</span></span>|
|<span data-ttu-id="1fee4-222">2</span><span class="sxs-lookup"><span data-stu-id="1fee4-222">2</span></span>|<span data-ttu-id="1fee4-223">**Renomear**: os usuários podem dar à guia um nome significativo para o canal, chat ou reunião.</span><span class="sxs-lookup"><span data-stu-id="1fee4-223">**Rename**: Users can give the tab a name that’s meaningful to the channel, chat, or meeting.</span></span>|
|<span data-ttu-id="1fee4-224">3</span><span class="sxs-lookup"><span data-stu-id="1fee4-224">3</span></span>|<span data-ttu-id="1fee4-225">**Remover**: remove a guia do canal, chat ou reunião.</span><span class="sxs-lookup"><span data-stu-id="1fee4-225">**Remove**: Removes the tab from the channel, chat, or meeting.</span></span>|

# <a name="mobile"></a>[<span data-ttu-id="1fee4-226">Mobile</span><span class="sxs-lookup"><span data-stu-id="1fee4-226">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/tabs/mobile-design-manage-tab-menu-anatomy.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de um menu de guia móvel." border="false":::

|<span data-ttu-id="1fee4-228">Contador</span><span class="sxs-lookup"><span data-stu-id="1fee4-228">Counter</span></span>|<span data-ttu-id="1fee4-229">Descrição</span><span class="sxs-lookup"><span data-stu-id="1fee4-229">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="1fee4-230">1</span><span class="sxs-lookup"><span data-stu-id="1fee4-230">1</span></span>|<span data-ttu-id="1fee4-231">**Abra no navegador**: abre o aplicativo no navegador padrão do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1fee4-231">**Open in browser**: Opens the app in the device’s default browser.</span></span>|
|<span data-ttu-id="1fee4-232">2</span><span class="sxs-lookup"><span data-stu-id="1fee4-232">2</span></span>|<span data-ttu-id="1fee4-233">**Link de cópia:** os usuários podem copiar e compartilhar um link para a guia.</span><span class="sxs-lookup"><span data-stu-id="1fee4-233">**Copy link**: Users can copy and share a link to the tab.</span></span>|
|<span data-ttu-id="1fee4-234">3</span><span class="sxs-lookup"><span data-stu-id="1fee4-234">3</span></span>|<span data-ttu-id="1fee4-235">**Configurações:**(Opcional) Modifique as configurações de uma guia depois que ela foi adicionada.</span><span class="sxs-lookup"><span data-stu-id="1fee4-235">**Settings**: (Optional) Modify a tab’s settings after it's been added.</span></span>|
|<span data-ttu-id="1fee4-236">4 </span><span class="sxs-lookup"><span data-stu-id="1fee4-236">4</span></span>|<span data-ttu-id="1fee4-237">**Renomear**: os usuários podem dar à guia um nome significativo para o canal, chat ou reunião.</span><span class="sxs-lookup"><span data-stu-id="1fee4-237">**Rename**: Users can give the tab a name that's meaningful to the channel, chat, or meeting.</span></span>|
|<span data-ttu-id="1fee4-238">5 </span><span class="sxs-lookup"><span data-stu-id="1fee4-238">5</span></span>|<span data-ttu-id="1fee4-239">**Excluir**: remove a guia do canal, chat ou reunião.</span><span class="sxs-lookup"><span data-stu-id="1fee4-239">**Delete**: Removes the tab from the channel, chat, or meeting.</span></span>|

---

## <a name="tab-notifications-and-deep-linking"></a><span data-ttu-id="1fee4-240">Notificações de tabulação e vinculação profunda</span><span class="sxs-lookup"><span data-stu-id="1fee4-240">Tab notifications and deep linking</span></span>

<span data-ttu-id="1fee4-241">Você pode enviar uma mensagem com um link profundo para sua guia. Por exemplo, um cartão mostra um resumo dos dados de bugs que um usuário pode selecionar para ver o bug inteiro em uma guia. O envio de mensagens sobre a atividade de tabulação aumenta a conscientização sem notificar explicitamente todos (ou seja, atividades sem ruído).</span><span class="sxs-lookup"><span data-stu-id="1fee4-241">You can send a message with a deep link to your tab. For example, a card shows a summary of bug data a user can select to see the entire bug in a tab. Sending messages about tab activity increases awareness without explicitly notifying everyone (i.e., activity without noise).</span></span> <span data-ttu-id="1fee4-242">Você também pode @mention usuários específicos, se necessário.</span><span class="sxs-lookup"><span data-stu-id="1fee4-242">You also can @mention specific users if needed.</span></span>

<span data-ttu-id="1fee4-243">Notificar os usuários da atividade de tabulação uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="1fee4-243">Notify users of tab activity one of the following ways:</span></span>

* <span data-ttu-id="1fee4-244">**Bot**: Este método é preferencial especialmente se o thread de tabulação for direcionado.</span><span class="sxs-lookup"><span data-stu-id="1fee4-244">**Bot**: This method is preferred especially if the tab thread is targeted.</span></span> <span data-ttu-id="1fee4-245">A conversa encadeada da guia é movida para a exibição como ativa recentemente.</span><span class="sxs-lookup"><span data-stu-id="1fee4-245">The tab’s threaded conversation is moved into view as recently active.</span></span> <span data-ttu-id="1fee4-246">Esse método também permite alguma sofisticação na forma como a notificação é enviada.</span><span class="sxs-lookup"><span data-stu-id="1fee4-246">This method also allows for some sophistication in how the notification is sent.</span></span>
* <span data-ttu-id="1fee4-247">**Mensagem**: uma mensagem aparece no feed de atividade do usuário com um [link profundo para a guia](../../concepts/build-and-test/deep-links.md?view=msteams-client-js-latest&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="1fee4-247">**Message**: A message shows up in the user’s activity feed with a [deep link to the tab](../../concepts/build-and-test/deep-links.md?view=msteams-client-js-latest&preserve-view=true).</span></span>

## <a name="best-practices"></a><span data-ttu-id="1fee4-248">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="1fee4-248">Best practices</span></span>

<span data-ttu-id="1fee4-249">Use essas recomendações para criar uma experiência de aplicativo de qualidade:</span><span class="sxs-lookup"><span data-stu-id="1fee4-249">Use these recommendations to create a quality app experience:</span></span>

### <a name="collaboration"></a><span data-ttu-id="1fee4-250">Colaboração</span><span class="sxs-lookup"><span data-stu-id="1fee4-250">Collaboration</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-do.png" alt-text="A ilustração mostra o que fazer com o design de navegação de tabulação." border="false":::

#### <a name="do-facilitate-conversation"></a><span data-ttu-id="1fee4-252">Do: Facilitar a conversa</span><span class="sxs-lookup"><span data-stu-id="1fee4-252">Do: Facilitate conversation</span></span>

<span data-ttu-id="1fee4-253">Inclua conteúdo e componentes que as pessoas possam falar.</span><span class="sxs-lookup"><span data-stu-id="1fee4-253">Include content and components people can talk about.</span></span> <span data-ttu-id="1fee4-254">Se ele não se encaixar no contexto de um chat, canal ou reunião, ele não pertence à sua guia.</span><span class="sxs-lookup"><span data-stu-id="1fee4-254">If it doesn’t fit within the context of a chat, channel, or meeting, it doesn’t belong in your tab.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-collaboration-dont.png" alt-text="Exemplo mostra o que não fazer com o design de navegação de tabulação." border="false":::

#### <a name="dont-treat-your-tab-like-any-other-webpage"></a><span data-ttu-id="1fee4-256">Não: trate sua guia como qualquer outra página da Web</span><span class="sxs-lookup"><span data-stu-id="1fee4-256">Don't: Treat your tab like any other webpage</span></span>

<span data-ttu-id="1fee4-257">Uma guia não é uma página da Web que alguém pode exibir uma vez.</span><span class="sxs-lookup"><span data-stu-id="1fee4-257">A tab isn’t a webpage someone might view once.</span></span> <span data-ttu-id="1fee4-258">Uma guia deve exibir o conteúdo mais importante e relevante que as pessoas precisam para realizar algo juntos.</span><span class="sxs-lookup"><span data-stu-id="1fee4-258">A tab should display your most important, relevant content that people need to accomplish something together.</span></span>

   :::column-end:::
:::row-end:::

### <a name="navigation"></a><span data-ttu-id="1fee4-259">Navegação</span><span class="sxs-lookup"><span data-stu-id="1fee4-259">Navigation</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-do.png" alt-text="Exemplo mostrando o que fazer com o design de navegação de tabulação." border="false":::

#### <a name="do-limit-tasks-and-data"></a><span data-ttu-id="1fee4-261">Fazer: Limitar tarefas e dados</span><span class="sxs-lookup"><span data-stu-id="1fee4-261">Do: Limit tasks and data</span></span>

<span data-ttu-id="1fee4-262">As guias funcionam melhor quando elas abordam necessidades específicas.</span><span class="sxs-lookup"><span data-stu-id="1fee4-262">Tabs work best when they address specific needs.</span></span> <span data-ttu-id="1fee4-263">Inclua um conjunto limitado de tarefas e dados relevantes para a equipe ou grupo.</span><span class="sxs-lookup"><span data-stu-id="1fee4-263">Include a limited set of tasks and data relevant to the team or group.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-nav-dont.png" alt-text="Ilustração mostrando o que não fazer com o design de navegação de tabulação." border="false":::

#### <a name="dont-embed-your-entire-app"></a><span data-ttu-id="1fee4-265">Não: incorporar seu aplicativo inteiro</span><span class="sxs-lookup"><span data-stu-id="1fee4-265">Don't: Embed your entire app</span></span>

<span data-ttu-id="1fee4-266">Usar uma guia para exibir um aplicativo inteiro com navegação de vários níveis e interações complexas leva à sobrecarga de informações.</span><span class="sxs-lookup"><span data-stu-id="1fee4-266">Using a tab to display an entire app with multi-level navigation and complex interactions leads to information overload.</span></span>

   :::column-end:::
:::row-end:::

### <a name="setup"></a><span data-ttu-id="1fee4-267">Configurar</span><span class="sxs-lookup"><span data-stu-id="1fee4-267">Setup</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-do.png" alt-text="Ilustração mostrando o que fazer com o design de configuração de tabulação." border="false":::

#### <a name="do-keep-it-simple"></a><span data-ttu-id="1fee4-269">Fazer: mantenha-o simples</span><span class="sxs-lookup"><span data-stu-id="1fee4-269">Do: Keep it simple</span></span>

<span data-ttu-id="1fee4-270">Se seu aplicativo exigir autenticação, tente integrar o SSO (login único) da Microsoft para uma experiência de login mais perfeita.</span><span class="sxs-lookup"><span data-stu-id="1fee4-270">If your app requires authentication, try integrating Microsoft single sign-on (SSO) for a more seamless sign-in experience.</span></span> <span data-ttu-id="1fee4-271">Além disso, inclua apenas informações essenciais e etapas para adicionar a guia.</span><span class="sxs-lookup"><span data-stu-id="1fee4-271">Also, only include essential information and steps to add the tab.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-setup-dont.png" alt-text="Ilustração mostrando o que não fazer com o design de configuração de tabulação." border="false":::

#### <a name="dont-have-too-many-steps"></a><span data-ttu-id="1fee4-273">Não: ter muitas etapas</span><span class="sxs-lookup"><span data-stu-id="1fee4-273">Don't: Have too many steps</span></span>

<span data-ttu-id="1fee4-274">Remova todas as etapas desnecessárias para adicionar uma guia.</span><span class="sxs-lookup"><span data-stu-id="1fee4-274">Remove any unnecessary steps for adding a tab.</span></span>

   :::column-end:::
:::row-end:::

### <a name="theming"></a><span data-ttu-id="1fee4-275">Temas</span><span class="sxs-lookup"><span data-stu-id="1fee4-275">Theming</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-do.png" alt-text="Ilustração mostrando o que fazer com temas de tabulação." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a><span data-ttu-id="1fee4-277">Do: tire proveito de Teams de cores</span><span class="sxs-lookup"><span data-stu-id="1fee4-277">Do: Take advantage of Teams color tokens</span></span>

<span data-ttu-id="1fee4-278">Cada Teams tem seu próprio esquema de cores.</span><span class="sxs-lookup"><span data-stu-id="1fee4-278">Each Teams theme has its own color scheme.</span></span> <span data-ttu-id="1fee4-279">Para lidar com alterações de tema automaticamente, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">tokens de cor (interface do usuário fluente)</a> em seu design.</span><span class="sxs-lookup"><span data-stu-id="1fee4-279">To handle theme changes automatically, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">color tokens (Fluent UI)</a> in your design.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/tabs/design-tab-theming-dont.png" alt-text="Ilustração mostrando o que não fazer com temas de tabulação." border="false":::

#### <a name="dont-hard-code-color-values"></a><span data-ttu-id="1fee4-281">Não: Valores de cor de código rígidos</span><span class="sxs-lookup"><span data-stu-id="1fee4-281">Don't: Hard code color values</span></span>

<span data-ttu-id="1fee4-282">Se você não usar tokens Teams cores, seus designs serão menos escalonáveis e levarão mais tempo para gerenciar.</span><span class="sxs-lookup"><span data-stu-id="1fee4-282">If you don’t use Teams color tokens, your designs will be less scalable and take more time to manage.</span></span>

   :::column-end:::
:::row-end:::
