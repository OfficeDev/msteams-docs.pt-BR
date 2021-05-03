---
title: Projetando sua extensão de mensagens
description: Saiba como projetar uma extensão Teams de mensagens e obter o kit Microsoft Teams interface do usuário.
keywords: Práticas práticas práticas de referência de extensões de mensagens de referência de diretrizes de design do teams
author: heath-hamilton
localization_priority: Normal
ms.author: qinch
ms.topic: conceptual
ms.openlocfilehash: 8b918c59910cbdc560fe415354d2c62c0fdd443c
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101573"
---
# <a name="designing-your-microsoft-teams-messaging-extension"></a><span data-ttu-id="1ee56-104">Projetando sua extensão Microsoft Teams de mensagens</span><span class="sxs-lookup"><span data-stu-id="1ee56-104">Designing your Microsoft Teams messaging extension</span></span>

<span data-ttu-id="1ee56-105">Extensões de mensagens são atalhos para inserir conteúdo do aplicativo ou agir em uma mensagem sem sair da conversa.</span><span class="sxs-lookup"><span data-stu-id="1ee56-105">Messaging extensions are shortcuts for inserting app content or acting on a message without navigating away from the conversation.</span></span>
<span data-ttu-id="1ee56-106">Para orientar o design do aplicativo, as informações a seguir descrevem e ilustram como as pessoas podem adicionar, usar e gerenciar extensões de mensagens em Teams.</span><span class="sxs-lookup"><span data-stu-id="1ee56-106">To guide your app design, the following information describes and illustrates how people can add, use, and manage messaging extensions in Teams.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="1ee56-107">Kit de Interface do Usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="1ee56-107">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="1ee56-108">Você pode encontrar diretrizes abrangentes de design de extensão de mensagens, incluindo elementos que você pode pegar e modificar conforme necessário, no Kit de interface do usuário Microsoft Teams usuário.</span><span class="sxs-lookup"><span data-stu-id="1ee56-108">You can find comprehensive messaging extension design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1ee56-109">Obtenha o Kit de Interface do Usuário do Microsoft Teams (Figma)</span><span class="sxs-lookup"><span data-stu-id="1ee56-109">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-messaging-extension"></a><span data-ttu-id="1ee56-110">Adicionar uma extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="1ee56-110">Add a messaging extension</span></span>

<span data-ttu-id="1ee56-111">Você pode adicionar uma extensão de mensagens nos seguintes Teams contextos:</span><span class="sxs-lookup"><span data-stu-id="1ee56-111">You can add a messaging extension in the following Teams contexts:</span></span>

* <span data-ttu-id="1ee56-112">A partir da loja do Microsoft Teams (AppSource).</span><span class="sxs-lookup"><span data-stu-id="1ee56-112">From the Teams store (AppSource).</span></span>
* <span data-ttu-id="1ee56-113">Em um canal, chat ou reunião (antes, durante e depois) perto da caixa de composição.</span><span class="sxs-lookup"><span data-stu-id="1ee56-113">In a channel, chat, or meeting (before, during, and after) near the compose box.</span></span> <span data-ttu-id="1ee56-114">Vale a pena notar se você adicionar uma extensão de mensagens em um desses locais, somente você poderá usá-la nesse contexto.</span><span class="sxs-lookup"><span data-stu-id="1ee56-114">It's worth noting if you add a messaging extension in one of these places, only you can use it in that context.</span></span>

<span data-ttu-id="1ee56-115">O exemplo a seguir mostra como você adiciona uma extensão de mensagens em um canal.</span><span class="sxs-lookup"><span data-stu-id="1ee56-115">The following example shows how you add a messaging extension in a channel.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/add-in-channel.png" alt-text="Exemplo mostra como adicionar uma extensão de mensagens perto da caixa de redação em um canal." border="false":::

## <a name="set-up-a-messaging-extension"></a><span data-ttu-id="1ee56-117">Configurar uma extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="1ee56-117">Set up a messaging extension</span></span>

<span data-ttu-id="1ee56-118">A autenticação não é obrigatória, mas se seu aplicativo for algo como uma ferramenta de controle de tíquetes, talvez seja necessário que as pessoas entre para usar a extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="1ee56-118">Authentication isn't mandatory, but if your app is something like a ticket tracking tool, you may need people to sign in to use the messaging extension.</span></span>

<span data-ttu-id="1ee56-119">Para ter consistência Teams aplicativos, você não pode personalizar a tela de login.</span><span class="sxs-lookup"><span data-stu-id="1ee56-119">For consistency across Teams apps, you can't customize the sign-in screen.</span></span> <span data-ttu-id="1ee56-120">Se você usar a autenticação de logom único (SSO), os usuários serão automaticamente assinados.</span><span class="sxs-lookup"><span data-stu-id="1ee56-120">If you use single sign-on (SSO) authentication, users are signed in automatically.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/set-up.png" alt-text="Exemplo mostra a tela de instalação de extensão de mensagens com um botão de login." border="false":::

## <a name="types-of-messaging-extensions"></a><span data-ttu-id="1ee56-122">Tipos de extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="1ee56-122">Types of messaging extensions</span></span>

<span data-ttu-id="1ee56-123">As extensões de mensagens podem ter comandos de pesquisa, comandos de ação ou ambos.</span><span class="sxs-lookup"><span data-stu-id="1ee56-123">Messaging extensions can have search commands, action commands, or both.</span></span> <span data-ttu-id="1ee56-124">Seus comandos dependem dos recursos do aplicativo e de como eles se ajustam Teams casos de uso.</span><span class="sxs-lookup"><span data-stu-id="1ee56-124">Your commands depend on your app's features and how those fit within Teams use cases.</span></span>

### <a name="search-commands"></a><span data-ttu-id="1ee56-125">Comandos de pesquisa</span><span class="sxs-lookup"><span data-stu-id="1ee56-125">Search commands</span></span>

<span data-ttu-id="1ee56-126">Com comandos de pesquisa, as pessoas podem usar sua extensão de mensagens para encontrar rapidamente conteúdo externo e inserir em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="1ee56-126">With search commands, people can use your messaging extension to quickly find external content and insert into a message.</span></span> <span data-ttu-id="1ee56-127">Comandos de pesquisa são comumente disponibilizados na caixa de redação.</span><span class="sxs-lookup"><span data-stu-id="1ee56-127">Search commands are commonly made available in the compose box.</span></span> <span data-ttu-id="1ee56-128">Por exemplo, você pode iniciar ou adicionar a uma discussão compartilhando um conteúdo sem sair Teams.</span><span class="sxs-lookup"><span data-stu-id="1ee56-128">For example, you can start or add to a discussion by sharing a piece of content—without ever leaving Teams.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/search-command-type.png" alt-text="Exemplo mostra uma extensão de mensagens baseada em pesquisa lançada na caixa de redação." border="false":::

#### <a name="compose-box-layout-options"></a><span data-ttu-id="1ee56-130">Opções de layout de caixa de redação</span><span class="sxs-lookup"><span data-stu-id="1ee56-130">Compose box layout options</span></span>

<span data-ttu-id="1ee56-131">Você tem algumas opções para exibir resultados de pesquisa de extensão de mensagens, incluindo [exibições de lista e grade.](../../messaging-extensions/how-to/search-commands/respond-to-search.md#respond-to-user-requests)</span><span class="sxs-lookup"><span data-stu-id="1ee56-131">You have some options for displaying messaging extension search results, including [list and grid views](../../messaging-extensions/how-to/search-commands/respond-to-search.md#respond-to-user-requests).</span></span>

:::image type="content" source="../../assets/images/messaging-extension/search-result-layout.png" alt-text="Ilustrações mostrando opções de layout para resultados de pesquisa de extensão de mensagens." border="false":::

### <a name="action-commands"></a><span data-ttu-id="1ee56-133">Comandos de ação</span><span class="sxs-lookup"><span data-stu-id="1ee56-133">Action commands</span></span>

<span data-ttu-id="1ee56-134">Comandos de ação permitem que as pessoas acionem ações e solicitações de processo em serviços externos Teams.</span><span class="sxs-lookup"><span data-stu-id="1ee56-134">Action commands allow people to trigger actions and process requests in external services within Teams.</span></span> <span data-ttu-id="1ee56-135">Por exemplo, se seu aplicativo rastreia pedidos, um usuário pode criar uma nova ordem usando o conteúdo da mensagem de um colega de dentro do chat.</span><span class="sxs-lookup"><span data-stu-id="1ee56-135">For example, if your app tracks orders, a user could create a new order using the contents of a colleague’s message from right inside their chat.</span></span>

<span data-ttu-id="1ee56-136">Extensões de mensagens baseadas em ação frequentemente exigem que os usuários concluam um formulário ou algum outro tipo de configuração dentro de um modal.</span><span class="sxs-lookup"><span data-stu-id="1ee56-136">Action-based messaging extensions frequently require users to complete a form or some other kind of configuration within a modal.</span></span> <span data-ttu-id="1ee56-137">Você pode criar essas experiências com [módulos de tarefa.](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)</span><span class="sxs-lookup"><span data-stu-id="1ee56-137">You can create these experiences with [task modules](../../task-modules-and-cards/task-modules/design-teams-task-modules.md).</span></span>

## <a name="open-a-messaging-extension"></a><span data-ttu-id="1ee56-138">Abrir uma extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="1ee56-138">Open a messaging extension</span></span>

<span data-ttu-id="1ee56-139">A caixa de redação e as mensagens/postagens são os principais contextos em que as pessoas usam extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="1ee56-139">The compose box and messages/posts are the primary contexts where people use messaging extensions.</span></span>

### <a name="from-the-compose-box"></a><span data-ttu-id="1ee56-140">Na caixa de redação</span><span class="sxs-lookup"><span data-stu-id="1ee56-140">From the compose box</span></span>

<span data-ttu-id="1ee56-141">Depois de adicionado, os usuários podem abrir sua extensão de mensagens selecionando o ícone do aplicativo abaixo da caixa de redação.</span><span class="sxs-lookup"><span data-stu-id="1ee56-141">Once added, users can open your messaging extension by selecting your app icon below the compose box.</span></span> <span data-ttu-id="1ee56-142">Neste exemplo, a extensão tem comandos de pesquisa e ação.</span><span class="sxs-lookup"><span data-stu-id="1ee56-142">In this example, the extension has search and action commands.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/open-from-compose-box.png" alt-text="Exemplo mostra como abrir uma extensão de mensagens da caixa de redação." border="false":::

### <a name="from-a-chat-message-or-channel-post"></a><span data-ttu-id="1ee56-144">De uma mensagem de chat ou postagem de canal</span><span class="sxs-lookup"><span data-stu-id="1ee56-144">From a chat message or channel post</span></span>

Depois de adicionado, os usuários podem selecionar o ícone **Mais** na mensagem de chat ou na postagem do :::image type="icon" source="../../assets/icons/teams-client-more.png"::: canal para encontrar os comandos de ação da extensão. <span data-ttu-id="1ee56-146">Sua extensão pode estar listada em **Mais ações** com base no uso.</span><span class="sxs-lookup"><span data-stu-id="1ee56-146">Your extension may be listed under **More actions** based on usage.</span></span>

> [!NOTE]
> <span data-ttu-id="1ee56-147">O suporte para mais ações de uma mensagem de chat ou postagem de canal não está disponível Microsoft Teams plataforma móvel.</span><span class="sxs-lookup"><span data-stu-id="1ee56-147">Support for more actions from a chat message or channel post is not available on Microsoft Teams mobile platform.</span></span> 

#### <a name="chat-message"></a><span data-ttu-id="1ee56-148">Mensagem de chat</span><span class="sxs-lookup"><span data-stu-id="1ee56-148">Chat message</span></span>

:::image type="content" source="../../assets/images/messaging-extension/open-from-chat-message.png" alt-text="Exemplo mostra como abrir uma extensão de mensagens de uma mensagem de chat." border="false":::

#### <a name="channel-post"></a><span data-ttu-id="1ee56-150">Postagem de canal</span><span class="sxs-lookup"><span data-stu-id="1ee56-150">Channel post</span></span>

:::image type="content" source="../../assets/images/messaging-extension/open-from-channel-post.png" alt-text="Exemplo mostra como abrir uma extensão de mensagens de uma postagem de canal." border="false":::

## <a name="use-a-messaging-extension"></a><span data-ttu-id="1ee56-152">Usar uma extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="1ee56-152">Use a messaging extension</span></span>

<span data-ttu-id="1ee56-153">Os cenários a seguir mostram as principais maneiras pelas quais as pessoas usam extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="1ee56-153">The following scenarios show the primary ways people use messaging extensions.</span></span>

### <a name="insert-content-into-a-message"></a><span data-ttu-id="1ee56-154">Inserir conteúdo em uma mensagem</span><span class="sxs-lookup"><span data-stu-id="1ee56-154">Insert content into a message</span></span>

<span data-ttu-id="1ee56-155">**1. Selecione uma extensão de mensagens**.</span><span class="sxs-lookup"><span data-stu-id="1ee56-155">**1. Select a messaging extension**.</span></span> <span data-ttu-id="1ee56-156">Os usuários podem pesquisar o conteúdo que eles querem compartilhar na caixa de redação.</span><span class="sxs-lookup"><span data-stu-id="1ee56-156">Users can search for the content they want to share from the compose box.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/insert-content-search.png" alt-text="Exemplo mostra um usuário procurando conteúdo para inserir na caixa de redação." border="false":::

<span data-ttu-id="1ee56-158">**2. Insira conteúdo**.</span><span class="sxs-lookup"><span data-stu-id="1ee56-158">**2. Insert content**.</span></span> <span data-ttu-id="1ee56-159">Depois de postado, outras pessoas podem responder ou selecionar o conteúdo para ver mais informações em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ee56-159">Once posted, others can reply or select the content to see more information in your app.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/insert-content-posted.png" alt-text="Exemplo mostra um usuário postando conteúdo em uma conversa de canal." border="false":::

### <a name="take-action-on-a-message"></a><span data-ttu-id="1ee56-161">Tomar medidas em uma mensagem</span><span class="sxs-lookup"><span data-stu-id="1ee56-161">Take action on a message</span></span>

<span data-ttu-id="1ee56-162">**1. Selecione uma extensão de mensagens**.</span><span class="sxs-lookup"><span data-stu-id="1ee56-162">**1. Select a messaging extension**.</span></span> <span data-ttu-id="1ee56-163">Seu aplicativo pode incluir um ou mais comandos de ação.</span><span class="sxs-lookup"><span data-stu-id="1ee56-163">Your app can include one or more action commands.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/select-action-command.png" alt-text="Exemplo mostra um usuário selecionando um comando de ação de extensão de mensagens." border="false":::

<span data-ttu-id="1ee56-165">**2. Conclua a ação**.</span><span class="sxs-lookup"><span data-stu-id="1ee56-165">**2. Complete the action**.</span></span> <span data-ttu-id="1ee56-166">Seu aplicativo pode receber e processar qualquer conteúdo ou dados enviados pela ação da mensagem.</span><span class="sxs-lookup"><span data-stu-id="1ee56-166">Your app can receive and process any content or data sent by the message action.</span></span> <span data-ttu-id="1ee56-167">Isso permite que os usuários permaneçam em suas conversas e, no exemplo a seguir, não se preocupe em inserir informações diretamente em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ee56-167">This allows users to remain in their conversation and, the following example, not worry about entering information directly in your app.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/complete-action-command.png" alt-text="Exemplo sobre como agir em uma mensagem." border="false":::

### <a name="preview-links"></a><span data-ttu-id="1ee56-169">Links de visualização</span><span class="sxs-lookup"><span data-stu-id="1ee56-169">Preview links</span></span>

<span data-ttu-id="1ee56-170">As extensões de mensagens também permitem inserir links ricos de uma URL reconhecida em uma mensagem (esse recurso é chamado [de desatada](../../messaging-extensions/how-to/link-unfurling.md)de link .)</span><span class="sxs-lookup"><span data-stu-id="1ee56-170">Messaging extensions also allow you to insert rich links from a recognized URL into a message (this capability is called [link unfurling](../../messaging-extensions/how-to/link-unfurling.md).)</span></span>

<span data-ttu-id="1ee56-171">**1. Colar um link reconhecido** na caixa de redação.</span><span class="sxs-lookup"><span data-stu-id="1ee56-171">**1. Paste a recognized link** in the compose box.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/paste-preview-link.png" alt-text="Exemplo mostra um usuário colar um link na caixa de compostagem." border="false":::

<span data-ttu-id="1ee56-173">**2. Insira conteúdo**.</span><span class="sxs-lookup"><span data-stu-id="1ee56-173">**2. Insert content**.</span></span> <span data-ttu-id="1ee56-174">Se seu aplicativo reconhecer a URL na caixa de redação, ele renderizará o link como um cartão que fornece uma visualização rica em conteúdo do conteúdo da Web.</span><span class="sxs-lookup"><span data-stu-id="1ee56-174">If your app recognizes the URL in the compose box, it renders the link as a card that provides a content-rich preview of the web content.</span></span> <span data-ttu-id="1ee56-175">(Consulte [Diretrizes de design de Cartões Adaptáveis](../../task-modules-and-cards/cards/design-effective-cards.md) para obter mais informações.)</span><span class="sxs-lookup"><span data-stu-id="1ee56-175">(See [Adaptive Cards design guidelines](../../task-modules-and-cards/cards/design-effective-cards.md) for more information.)</span></span>

:::image type="content" source="../../assets/images/messaging-extension/insert-preview-link.png" alt-text="Exemplo mostra como a URL, já que é reconhecida pelo seu aplicativo, inclui algum conteúdo rico na caixa de redação." border="false":::

## <a name="manage-a-messaging-extension"></a><span data-ttu-id="1ee56-177">Gerenciar uma extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="1ee56-177">Manage a messaging extension</span></span>

<span data-ttu-id="1ee56-178">Clicando com o botão direito do mouse no ícone, os usuários podem fixar, remover ou configurar sua extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="1ee56-178">By right clicking your icon, users can pin, remove, or configure your messaging extension.</span></span>

## <a name="anatomy"></a><span data-ttu-id="1ee56-179">Anatomia</span><span class="sxs-lookup"><span data-stu-id="1ee56-179">Anatomy</span></span>

### <a name="messaging-extension-in-the-compose-box"></a><span data-ttu-id="1ee56-180">Extensão de mensagens na caixa de redação</span><span class="sxs-lookup"><span data-stu-id="1ee56-180">Messaging extension in the compose box</span></span>

<span data-ttu-id="1ee56-181">O exemplo a seguir é uma extensão de mensagens aberta na caixa de redação.</span><span class="sxs-lookup"><span data-stu-id="1ee56-181">The following example is a messaging extension opened from the compose box.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/anatomy-compose.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de uma extensão de mensagens na caixa de redação." border="false":::

|<span data-ttu-id="1ee56-183">Contador</span><span class="sxs-lookup"><span data-stu-id="1ee56-183">Counter</span></span>|<span data-ttu-id="1ee56-184">Descrição</span><span class="sxs-lookup"><span data-stu-id="1ee56-184">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="1ee56-185">1</span><span class="sxs-lookup"><span data-stu-id="1ee56-185">1</span></span>|<span data-ttu-id="1ee56-186">**Logotipo do aplicativo**: Ícone de cor do logotipo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ee56-186">**App logo**: Color icon of your app logo.</span></span>|
|<span data-ttu-id="1ee56-187">2</span><span class="sxs-lookup"><span data-stu-id="1ee56-187">2</span></span>|<span data-ttu-id="1ee56-188">**Nome do** aplicativo : Nome completo do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ee56-188">**App name**: Full name of your app.</span></span>|
|<span data-ttu-id="1ee56-189">3</span><span class="sxs-lookup"><span data-stu-id="1ee56-189">3</span></span>|<span data-ttu-id="1ee56-190">**Ícone de menu comandos de ação (opcional)**: abre uma lista de comandos de ação para sua extensão de mensagens (se você especificar algum).</span><span class="sxs-lookup"><span data-stu-id="1ee56-190">**Action commands menu icon (optional)**: Opens a list of action commands for your messaging extension (if you specify any).</span></span>
|<span data-ttu-id="1ee56-191">4 </span><span class="sxs-lookup"><span data-stu-id="1ee56-191">4</span></span>|<span data-ttu-id="1ee56-192">**Caixa de** pesquisa : Permite que os usuários encontrem o conteúdo do aplicativo que eles querem inserir.</span><span class="sxs-lookup"><span data-stu-id="1ee56-192">**Search box**: Allows users to find app content they want to insert.</span></span>|
|<span data-ttu-id="1ee56-193">5 </span><span class="sxs-lookup"><span data-stu-id="1ee56-193">5</span></span>|<span data-ttu-id="1ee56-194">**Menu Guia (opcional)**: Fornece várias categorias de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="1ee56-194">**Tab menu (optional)**: Provides multiple content categories.</span></span>|
|<span data-ttu-id="1ee56-195">6 </span><span class="sxs-lookup"><span data-stu-id="1ee56-195">6</span></span>|<span data-ttu-id="1ee56-196">**Menu comandos de ação (opcional)**: exibe a lista de comandos de ação (se você especificar algum).</span><span class="sxs-lookup"><span data-stu-id="1ee56-196">**Action commands menu (optional)**: Displays list of action commands (if you specify any).</span></span>|
|<span data-ttu-id="1ee56-197">7 </span><span class="sxs-lookup"><span data-stu-id="1ee56-197">7</span></span>|<span data-ttu-id="1ee56-198">**Conteúdo do** aplicativo : principalmente para exibir os resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="1ee56-198">**App content**: Primarily to display search results.</span></span> <span data-ttu-id="1ee56-199">O exemplo aqui está usando o layout da lista (layout de grade é outra opção).</span><span class="sxs-lookup"><span data-stu-id="1ee56-199">The example here is using the list layout (grid layout is another option).</span></span>|
|<span data-ttu-id="1ee56-200">8 </span><span class="sxs-lookup"><span data-stu-id="1ee56-200">8</span></span>|<span data-ttu-id="1ee56-201">**Logotipo do aplicativo**: Ícone de contorno do logotipo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ee56-201">**App logo**: Outline icon of your app logo.</span></span>|

### <a name="messaging-extension-management-menu"></a><span data-ttu-id="1ee56-202">Menu de gerenciamento de extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="1ee56-202">Messaging extension management menu</span></span>

:::image type="content" source="../../assets/images/messaging-extension/anatomy-management-menu.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de um menu de gerenciamento de extensão de mensagens." border="false":::

|<span data-ttu-id="1ee56-204">Contador</span><span class="sxs-lookup"><span data-stu-id="1ee56-204">Counter</span></span>|<span data-ttu-id="1ee56-205">Descrição</span><span class="sxs-lookup"><span data-stu-id="1ee56-205">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="1ee56-206">1</span><span class="sxs-lookup"><span data-stu-id="1ee56-206">1</span></span>|<span data-ttu-id="1ee56-207">**Desempin**: Disponível se o usuário fixou seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ee56-207">**Unpin**: Available if the user has pinned your app.</span></span>|
|<span data-ttu-id="1ee56-208">2</span><span class="sxs-lookup"><span data-stu-id="1ee56-208">2</span></span>|<span data-ttu-id="1ee56-209">**Remover**: remove a extensão de mensagens do canal, chat ou reunião.</span><span class="sxs-lookup"><span data-stu-id="1ee56-209">**Remove**: Removes the messaging extension from the channel, chat, or meeting.</span></span>|

## <a name="best-practices"></a><span data-ttu-id="1ee56-210">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="1ee56-210">Best practices</span></span>

<span data-ttu-id="1ee56-211">Use essas recomendações para criar uma experiência de aplicativo de qualidade.</span><span class="sxs-lookup"><span data-stu-id="1ee56-211">Use these recommendations to create a quality app experience.</span></span>

### <a name="setup-and-general-usage"></a><span data-ttu-id="1ee56-212">Instalação e uso geral</span><span class="sxs-lookup"><span data-stu-id="1ee56-212">Setup and general usage</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-do.png" alt-text="Exemplo de configuração e uso geral." border="false":::

#### <a name="do-integrate-with-single-sign-on"></a><span data-ttu-id="1ee56-214">Fazer: Integrar com o single-sign on</span><span class="sxs-lookup"><span data-stu-id="1ee56-214">Do: Integrate with single-sign on</span></span>

<span data-ttu-id="1ee56-215">O SSO torna o processo de login mais fácil, rápido e seguro.</span><span class="sxs-lookup"><span data-stu-id="1ee56-215">SSO makes the sign-in process easier, faster, and secure.</span></span> <span data-ttu-id="1ee56-216">Além disso, se um usuário já tiver feito login no seu aplicativo pessoal, ele não precisa também entrar novamente para acessar a extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="1ee56-216">Also, if a user has already signed in to your personal app, they don’t have to also sign in again to access the messaging extension.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-dont.png" alt-text="Exemplo de integração com o single-sign on." border="false":::

#### <a name="dont-take-users-away-from-the-conversation"></a><span data-ttu-id="1ee56-218">Não: tire os usuários da conversa</span><span class="sxs-lookup"><span data-stu-id="1ee56-218">Don't: Take users away from the conversation</span></span>

<span data-ttu-id="1ee56-219">Extensões de mensagens são atalhos que devem reduzir a alternção de contexto.</span><span class="sxs-lookup"><span data-stu-id="1ee56-219">Messaging extensions are shortcuts that are supposed reduce context switching.</span></span> <span data-ttu-id="1ee56-220">Sua extensão não deve, por exemplo, direcionar usuários para uma página da Web fora Teams.</span><span class="sxs-lookup"><span data-stu-id="1ee56-220">Your extension should not, for example, direct users to a webpage outside Teams.</span></span>

   :::column-end:::
:::row-end:::

#### <a name="do-highlight-your-messaging-extension"></a><span data-ttu-id="1ee56-221">Do: Realça sua extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="1ee56-221">Do: Highlight your messaging extension</span></span>

<span data-ttu-id="1ee56-222">Extensões de mensagens nem sempre são fáceis de encontrar.</span><span class="sxs-lookup"><span data-stu-id="1ee56-222">Messaging extensions aren't always easy to find.</span></span> <span data-ttu-id="1ee56-223">Inclua capturas de tela de como usá-lo na página de detalhes do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ee56-223">Include screenshots of how to use it in your app details page.</span></span> <span data-ttu-id="1ee56-224">Se seu aplicativo também incluir um bot, você poderá incluir a documentação da ajuda de extensão de mensagens em um tour de boas-vindas de bot.</span><span class="sxs-lookup"><span data-stu-id="1ee56-224">If your app also includes a bot, you can include messaging extension help documentation in a bot welcome tour.</span></span>

### <a name="templating"></a><span data-ttu-id="1ee56-225">Templating</span><span class="sxs-lookup"><span data-stu-id="1ee56-225">Templating</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-do.png" alt-text="Exemplo de templating." border="false":::

#### <a name="do-let-teams-handle-some-of-the-design-work-if-possible"></a><span data-ttu-id="1ee56-227">Fazer: deixe Teams lidar com alguns dos trabalhos de design, se possível</span><span class="sxs-lookup"><span data-stu-id="1ee56-227">Do: Let Teams handle some of the design work if possible</span></span>

<span data-ttu-id="1ee56-228">Se fizer sentido para seus casos de uso, considere a criação de uma extensão de mensagens baseada em pesquisa.</span><span class="sxs-lookup"><span data-stu-id="1ee56-228">If it makes sense for your use cases, consider creating a search-based messaging extension.</span></span> <span data-ttu-id="1ee56-229">Teams renderiza esses tipos de extensões com temas e acessibilidade integrados.</span><span class="sxs-lookup"><span data-stu-id="1ee56-229">Teams renders these types of extensions with built-in theming and accessibility.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-dont.png" alt-text="Exemplo sobre como manipular o trabalho de design." border="false":::

#### <a name="dont-embed-your-entire-app-in-a-task-module"></a><span data-ttu-id="1ee56-231">Não: incorporar seu aplicativo inteiro em um módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="1ee56-231">Don't: Embed your entire app in a task module</span></span>

<span data-ttu-id="1ee56-232">Se a extensão de mensagens exigir comandos de ação, mantenha o módulo de tarefas simples e exibe apenas os componentes necessários para concluir a ação.</span><span class="sxs-lookup"><span data-stu-id="1ee56-232">If your messaging extension requires action commands, keep the task module simple and display only the components required to complete the action.</span></span>

   :::column-end:::
:::row-end:::

### <a name="theming"></a><span data-ttu-id="1ee56-233">Temas</span><span class="sxs-lookup"><span data-stu-id="1ee56-233">Theming</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-do.png" alt-text="Exemplo sobre temas." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a><span data-ttu-id="1ee56-235">Do: tire proveito de Teams de cores</span><span class="sxs-lookup"><span data-stu-id="1ee56-235">Do: Take advantage of Teams color tokens</span></span>

<span data-ttu-id="1ee56-236">Cada Teams tem seu próprio esquema de cores.</span><span class="sxs-lookup"><span data-stu-id="1ee56-236">Each Teams theme has its own color scheme.</span></span> <span data-ttu-id="1ee56-237">Para lidar com alterações de tema automaticamente, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">tokens de cor (interface do usuário fluente)</a> em seu design.</span><span class="sxs-lookup"><span data-stu-id="1ee56-237">To handle theme changes automatically, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">color tokens (Fluent UI)</a> in your design.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-dont.png" alt-text="Exemplo em tokens de cores." border="false":::

#### <a name="dont-hard-code-color-values"></a><span data-ttu-id="1ee56-239">Não: Valores de cor de código rígidos</span><span class="sxs-lookup"><span data-stu-id="1ee56-239">Don't: Hard code color values</span></span>

<span data-ttu-id="1ee56-240">Se você não usar tokens Teams cores, seus designs serão menos escalonáveis e levarão mais tempo para gerenciar.</span><span class="sxs-lookup"><span data-stu-id="1ee56-240">If you don't use Teams color tokens, your designs will be less scalable and take more time to manage.</span></span>

   :::column-end:::
:::row-end:::

### <a name="actions"></a><span data-ttu-id="1ee56-241">Ações</span><span class="sxs-lookup"><span data-stu-id="1ee56-241">Actions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-do.png" alt-text="Exemplo de ações." border="false":::

#### <a name="do-include-action-commands-that-make-sense-in-context"></a><span data-ttu-id="1ee56-243">Do: Incluir comandos de ação que fazem sentido no contexto</span><span class="sxs-lookup"><span data-stu-id="1ee56-243">Do: Include action commands that make sense in context</span></span>

<span data-ttu-id="1ee56-244">As ações de mensagem devem estar relacionadas ao que um usuário está olhando.</span><span class="sxs-lookup"><span data-stu-id="1ee56-244">Message actions should relate to what a user is looking at.</span></span> <span data-ttu-id="1ee56-245">Por exemplo, forneça aos usuários um atalho para criar um problema ou item de trabalho usando o texto na postagem de alguém.</span><span class="sxs-lookup"><span data-stu-id="1ee56-245">For example, provide users a shortcut for creating an issue or work item using the text in someone’s post.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-dont.png" alt-text="Exemplo em comandos de ação." border="false":::

#### <a name="dont-include-actions-commands-that-arent-contextual"></a><span data-ttu-id="1ee56-247">Não: inclua comandos de ações que não sejam contextuais</span><span class="sxs-lookup"><span data-stu-id="1ee56-247">Don't: Include actions commands that aren't contextual</span></span>

<span data-ttu-id="1ee56-248">Uma ação de mensagem para **Exibir seu painel** provavelmente pareceria desconectada da maioria das conversas.</span><span class="sxs-lookup"><span data-stu-id="1ee56-248">A message action to **View your dashboard** would probably seem disconnected from most conversations.</span></span>

   :::column-end:::
:::row-end:::

### <a name="searches"></a><span data-ttu-id="1ee56-249">Pesquisas</span><span class="sxs-lookup"><span data-stu-id="1ee56-249">Searches</span></span>

#### <a name="do-show-search-results-while-typing"></a><span data-ttu-id="1ee56-250">Do: Mostrar resultados da pesquisa durante a digitação</span><span class="sxs-lookup"><span data-stu-id="1ee56-250">Do: Show search results while typing</span></span>

<span data-ttu-id="1ee56-251">Forneça resultados de pesquisa sugeridos enquanto os usuários digitam.</span><span class="sxs-lookup"><span data-stu-id="1ee56-251">Provide suggested search results while users type.</span></span> <span data-ttu-id="1ee56-252">Eles podem encontrar o conteúdo de que precisam mais rapidamente com a quantidade mínima de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1ee56-252">They may find the content they need faster with minimal amount of characters.</span></span>

#### <a name="dont-require-users-to-submit-a-query"></a><span data-ttu-id="1ee56-253">Não: Exigir que os usuários enviem uma consulta</span><span class="sxs-lookup"><span data-stu-id="1ee56-253">Don't: Require users to submit a query</span></span>

<span data-ttu-id="1ee56-254">Você pode fazer com que os usuários pressionem uma tecla ou selecionem um botão para enviar consultas ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ee56-254">You can make users press a key or select a button to send queries to your app.</span></span> <span data-ttu-id="1ee56-255">Embora isso possa ser mais fácil no seu serviço de serviços de aplicativo, as pessoas podem estar confusas de que não estão vendo resultados de pesquisa em tempo real à medida que digitam.</span><span class="sxs-lookup"><span data-stu-id="1ee56-255">While that may be easier on your app services service, people may be confused that they're not seeing real-time search results as they type.</span></span>

#### <a name="do-consider-zero-term-queries"></a><span data-ttu-id="1ee56-256">Do: considere consultas de termo zero</span><span class="sxs-lookup"><span data-stu-id="1ee56-256">Do: Consider zero-term queries</span></span>

<span data-ttu-id="1ee56-257">Por exemplo, antes de um usuário escrever qualquer coisa na caixa de pesquisa, exempli-lo pela última vez em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ee56-257">For example, before a user writes anything in the search box, display what they last viewed on your app.</span></span> <span data-ttu-id="1ee56-258">É possível que eles queiram inserir esse conteúdo em suas conversas.</span><span class="sxs-lookup"><span data-stu-id="1ee56-258">It's possible that they want to insert that content into their conversation.</span></span>
