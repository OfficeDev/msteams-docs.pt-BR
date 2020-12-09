---
title: Criar sua extensão de mensagens
description: Saiba como projetar uma extensão de mensagens de equipes e obter o kit de interface do usuário do Microsoft Teams.
keywords: Diretrizes de design de equipes referência de dicas de extensões de mensagens recomendadas
author: heath-hamilton
ms.author: qinch
ms.topic: conceptual
ms.openlocfilehash: ad628bdaa46058aed4acdcea1a224c7ebfe40f89
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2020
ms.locfileid: "49604791"
---
# <a name="designing-your-microsoft-teams-messaging-extension"></a><span data-ttu-id="8f5fa-104">Projetando sua extensão de mensagens do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="8f5fa-104">Designing your Microsoft Teams messaging extension</span></span>

<span data-ttu-id="8f5fa-105">As extensões de mensagens são atalhos para inserir o conteúdo do aplicativo ou atuam em uma mensagem sem precisar sair da conversa.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-105">Messaging extensions are shortcuts for inserting app content or acting on a message without navigating away from the conversation.</span></span>

<span data-ttu-id="8f5fa-106">Para guiar o design do aplicativo, as informações a seguir descrevem e ilustra como as pessoas podem adicionar, usar e gerenciar extensões de mensagens no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-106">To guide your app design, the following information describes and illustrates how people can add, use, and manage messaging extensions in Teams.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="8f5fa-107">Kit de interface do usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="8f5fa-107">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="8f5fa-108">Você pode encontrar diretrizes de design de extensão de mensagens abrangentes, incluindo elementos que podem ser capturados e modificados conforme necessário, no kit de interface do usuário do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-108">You can find comprehensive messaging extension design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8f5fa-109">Obter o kit de interface do usuário do Microsoft Teams (figma)</span><span class="sxs-lookup"><span data-stu-id="8f5fa-109">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-messaging-extension"></a><span data-ttu-id="8f5fa-110">Adicionar uma extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="8f5fa-110">Add a messaging extension</span></span>

<span data-ttu-id="8f5fa-111">Você pode adicionar uma extensão de mensagens nos seguintes contextos da equipe:</span><span class="sxs-lookup"><span data-stu-id="8f5fa-111">You can add a messaging extension in the following Teams contexts:</span></span>

* <span data-ttu-id="8f5fa-112">No repositório do Teams (AppSource).</span><span class="sxs-lookup"><span data-stu-id="8f5fa-112">From the Teams store (AppSource).</span></span>
* <span data-ttu-id="8f5fa-113">Em um canal, chat ou reunião (antes, durante e depois) próximo da caixa de composição.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-113">In a channel, chat, or meeting (before, during, and after) near the compose box.</span></span> <span data-ttu-id="8f5fa-114">Vale a pena observar se você adicionar uma extensão de mensagens em um desses lugares, somente você pode usá-lo nesse contexto.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-114">It's worth noting if you add a messaging extension in one of these places, only you can use it in that context.</span></span>

<span data-ttu-id="8f5fa-115">O exemplo a seguir mostra como você adiciona uma extensão de mensagens em um canal.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-115">The following example shows how you add a messaging extension in a channel.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/add-in-channel.png" alt-text="O exemplo mostra como adicionar uma extensão de mensagens próxima à caixa de composição em um canal." border="false":::

## <a name="set-up-a-messaging-extension"></a><span data-ttu-id="8f5fa-117">Configurar uma extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="8f5fa-117">Set up a messaging extension</span></span>

<span data-ttu-id="8f5fa-118">A autenticação não é obrigatória, mas, se o aplicativo for algo parecido com uma ferramenta de controle de tíquetes, talvez você precise que as pessoas entrem para usar a extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-118">Authentication isn't mandatory, but if your app is something like a ticket tracking tool, you may need people to sign in to use the messaging extension.</span></span>

<span data-ttu-id="8f5fa-119">Para consistência entre os aplicativos do Microsoft Teams, você não pode personalizar a tela de entrada.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-119">For consistency across Teams apps, you can't customize the sign-in screen.</span></span> <span data-ttu-id="8f5fa-120">Se você usar a autenticação de logon único (SSO), os usuários serão conectados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-120">If you use single sign-on (SSO) authentication, users are signed in automatically.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/set-up.png" alt-text="Exemplo mostra a tela de configuração de extensão de mensagens com um botão de entrada." border="false":::

## <a name="types-of-messaging-extensions"></a><span data-ttu-id="8f5fa-122">Tipos de extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="8f5fa-122">Types of messaging extensions</span></span>

<span data-ttu-id="8f5fa-123">As extensões de mensagens podem ter comandos de pesquisa, comandos de ação ou ambos.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-123">Messaging extensions can have search commands, action commands, or both.</span></span> <span data-ttu-id="8f5fa-124">Seus comandos dependem dos recursos do seu aplicativo e de como eles se encaixam nos casos de uso do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-124">Your commands depend on your app's features and how those fit within Teams use cases.</span></span>

### <a name="search-commands"></a><span data-ttu-id="8f5fa-125">Comandos de pesquisa</span><span class="sxs-lookup"><span data-stu-id="8f5fa-125">Search commands</span></span>

<span data-ttu-id="8f5fa-126">Com os comandos de pesquisa, as pessoas podem usar sua extensão de mensagens para localizar rapidamente conteúdo externo e inserir em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-126">With search commands, people can use your messaging extension to quickly find external content and insert into a message.</span></span> <span data-ttu-id="8f5fa-127">Os comandos de pesquisa normalmente são disponibilizados na caixa de composição.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-127">Search commands are commonly made available in the compose box.</span></span> <span data-ttu-id="8f5fa-128">Por exemplo, você pode iniciar ou adicionar a uma discussão compartilhando uma parte do conteúdo, sem nunca deixar o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-128">For example, you can start or add to a discussion by sharing a piece of content—without ever leaving Teams.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/search-command-type.png" alt-text="O exemplo mostra uma extensão de mensagens baseada em pesquisa iniciada a partir da caixa de composição." border="false":::

#### <a name="compose-box-layout-options"></a><span data-ttu-id="8f5fa-130">Opções de layout da caixa de composição</span><span class="sxs-lookup"><span data-stu-id="8f5fa-130">Compose box layout options</span></span>

<span data-ttu-id="8f5fa-131">Você tem algumas opções para exibir resultados de pesquisa de extensão de mensagens, incluindo [modos de exibição de lista e de grade](../../messaging-Ask about extensions/how-to/search-commands/respond-to-search.md#respond-to-user-requests).</span><span class="sxs-lookup"><span data-stu-id="8f5fa-131">You have some options for displaying messaging extension search results, including [list and grid views](../../messaging-Ask about extensions/how-to/search-commands/respond-to-search.md#respond-to-user-requests).</span></span>

:::image type="content" source="../../assets/images/messaging-extension/search-result-layout.png" alt-text="Ilustrações mostrando opções de layout para resultados de pesquisa de extensão de mensagens." border="false":::

### <a name="action-commands"></a><span data-ttu-id="8f5fa-133">Comandos de ação</span><span class="sxs-lookup"><span data-stu-id="8f5fa-133">Action commands</span></span>

<span data-ttu-id="8f5fa-134">Os comandos de ação permitem que as pessoas disparem ações e processem solicitações em serviços externos no Teams.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-134">Action commands allow people to trigger actions and process requests in external services within Teams.</span></span> <span data-ttu-id="8f5fa-135">Por exemplo, se o seu aplicativo rastreia pedidos, um usuário pode criar um novo pedido usando o conteúdo da mensagem de um colega da direita dentro do bate-papo.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-135">For example, if your app tracks orders, a user could create a new order using the contents of a colleague’s message from right inside their chat.</span></span>

<span data-ttu-id="8f5fa-136">As extensões de mensagens baseadas em ação freqüentemente exigem que os usuários concluam um formulário ou outro tipo de configuração em uma janela restrita.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-136">Action-based messaging extensions frequently require users to complete a form or some other kind of configuration within a modal.</span></span> <span data-ttu-id="8f5fa-137">Você pode criar essas experiências com [módulos de tarefa](../../task-modules-and-cards/task-modules/design-teams-task-modules.md).</span><span class="sxs-lookup"><span data-stu-id="8f5fa-137">You can create these experiences with [task modules](../../task-modules-and-cards/task-modules/design-teams-task-modules.md).</span></span>

## <a name="open-a-messaging-extension"></a><span data-ttu-id="8f5fa-138">Abrir uma extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="8f5fa-138">Open a messaging extension</span></span>

<span data-ttu-id="8f5fa-139">A caixa de redação e mensagens/postagens são os principais contextos em que as pessoas usam as extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-139">The compose box and messages/posts are the primary contexts where people use messaging extensions.</span></span>

### <a name="from-the-compose-box"></a><span data-ttu-id="8f5fa-140">Na caixa de composição</span><span class="sxs-lookup"><span data-stu-id="8f5fa-140">From the compose box</span></span>

<span data-ttu-id="8f5fa-141">Depois de adicionado, os usuários podem abrir sua extensão de mensagens selecionando o ícone do aplicativo abaixo da caixa de composição.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-141">Once added, users can open your messaging extension by selecting your app icon below the compose box.</span></span> <span data-ttu-id="8f5fa-142">Neste exemplo, a extensão tem comandos Search e Action.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-142">In this example, the extension has search and action commands.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/open-from-compose-box.png" alt-text="O exemplo mostra como abrir uma extensão de mensagens na caixa de composição." border="false":::

### <a name="from-a-chat-message-or-channel-post"></a><span data-ttu-id="8f5fa-144">De uma mensagem de chat ou postagem de canal</span><span class="sxs-lookup"><span data-stu-id="8f5fa-144">From a chat message or channel post</span></span>

Depois de adicionado, os usuários podem selecionar o ícone **mais** :::image type="icon" source="../../assets/icons/teams-client-more.png"::: na mensagem de chat ou postagem de canal para localizar os comandos de ação da extensão. <span data-ttu-id="8f5fa-146">Sua extensão pode ser listada em **mais ações** com base no uso.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-146">Your extension may be listed under **More actions** based on usage.</span></span>

#### <a name="chat-message"></a><span data-ttu-id="8f5fa-147">Mensagem de chat</span><span class="sxs-lookup"><span data-stu-id="8f5fa-147">Chat message</span></span>

:::image type="content" source="../../assets/images/messaging-extension/open-from-chat-message.png" alt-text="O exemplo mostra como abrir uma extensão de mensagens de uma mensagem de chat." border="false":::

#### <a name="channel-post"></a><span data-ttu-id="8f5fa-149">Postagem de canal</span><span class="sxs-lookup"><span data-stu-id="8f5fa-149">Channel post</span></span>

:::image type="content" source="../../assets/images/messaging-extension/open-from-channel-post.png" alt-text="O exemplo mostra como abrir uma extensão de mensagens de uma postagem de canal." border="false":::

## <a name="use-a-messaging-extension"></a><span data-ttu-id="8f5fa-151">Usar uma extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="8f5fa-151">Use a messaging extension</span></span>

<span data-ttu-id="8f5fa-152">Os cenários a seguir mostram as principais maneiras pelas quais as pessoas usam as extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-152">The following scenarios show the primary ways people use messaging extensions.</span></span>

### <a name="insert-content-into-a-message"></a><span data-ttu-id="8f5fa-153">Inserir conteúdo em uma mensagem</span><span class="sxs-lookup"><span data-stu-id="8f5fa-153">Insert content into a message</span></span>

<span data-ttu-id="8f5fa-154">**1. Selecione uma extensão de mensagens**.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-154">**1. Select a messaging extension**.</span></span> <span data-ttu-id="8f5fa-155">Os usuários podem pesquisar o conteúdo que deseja compartilhar da caixa de composição.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-155">Users can search for the content they want to share from the compose box.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/insert-content-search.png" alt-text="O exemplo mostra um usuário procurando conteúdo a ser inserido na caixa de composição." border="false":::

<span data-ttu-id="8f5fa-157">**2. Insira o conteúdo**.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-157">**2. Insert content**.</span></span> <span data-ttu-id="8f5fa-158">Depois de publicado, as outras pessoas podem responder ou selecionar o conteúdo para ver mais informações em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-158">Once posted, others can reply or select the content to see more information in your app.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/insert-content-posted.png" alt-text="O exemplo mostra um usuário postando conteúdo em uma conversa de canal." border="false":::

### <a name="take-action-on-a-message"></a><span data-ttu-id="8f5fa-160">Executar uma ação em uma mensagem</span><span class="sxs-lookup"><span data-stu-id="8f5fa-160">Take action on a message</span></span>

<span data-ttu-id="8f5fa-161">**1. Selecione uma extensão de mensagens**.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-161">**1. Select a messaging extension**.</span></span> <span data-ttu-id="8f5fa-162">Seu aplicativo pode incluir um ou mais comandos de ação.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-162">Your app can include one or more action commands.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/select-action-command.png" alt-text="O exemplo mostra um usuário selecionando um comando de ação de extensão de mensagem." border="false":::

<span data-ttu-id="8f5fa-164">**2. Conclua a ação**.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-164">**2. Complete the action**.</span></span> <span data-ttu-id="8f5fa-165">Seu aplicativo pode receber e processar qualquer conteúdo ou dados enviados pela ação de mensagem.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-165">Your app can receive and process any content or data sent by the message action.</span></span> <span data-ttu-id="8f5fa-166">Isso permite que os usuários permaneçam em sua conversa e, no exemplo a seguir, não se preocupe em inserir informações diretamente em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-166">This allows users to remain in their conversation and, the following example, not worry about entering information directly in your app.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/complete-action-command.png" alt-text="O exemplo mostra um usuário procurando conteúdo a ser inserido na caixa de composição." border="false":::

### <a name="preview-links"></a><span data-ttu-id="8f5fa-168">Visualizar links</span><span class="sxs-lookup"><span data-stu-id="8f5fa-168">Preview links</span></span>

<span data-ttu-id="8f5fa-169">As extensões de mensagens também permitem que você insira links ricos de uma URL reconhecida em uma mensagem (esse recurso é chamado de [link Unfurling](../../messaging-extensions/how-to/link-unfurling.md).)</span><span class="sxs-lookup"><span data-stu-id="8f5fa-169">Messaging extensions also allow you to insert rich links from a recognized URL into a message (this capability is called [link unfurling](../../messaging-extensions/how-to/link-unfurling.md).)</span></span>

<span data-ttu-id="8f5fa-170">**1. Cole um link reconhecido** na caixa de composição.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-170">**1. Paste a recognized link** in the compose box.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/paste-preview-link.png" alt-text="O exemplo mostra um usuário colando um link na caixa Compost." border="false":::

<span data-ttu-id="8f5fa-172">**2. Insira o conteúdo**.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-172">**2. Insert content**.</span></span> <span data-ttu-id="8f5fa-173">Se seu aplicativo reconhece a URL na caixa de composição, ele renderiza o link como um cartão que fornece uma visualização rica no conteúdo do conteúdo da Web.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-173">If your app recognizes the URL in the compose box, it renders the link as a card that provides a content-rich preview of the web content.</span></span> <span data-ttu-id="8f5fa-174">(Confira [diretrizes de design de cartões adaptáveis](../../task-modules-and-cards/cards/design-effective-cards.md) para obter mais informações.)</span><span class="sxs-lookup"><span data-stu-id="8f5fa-174">(See [Adaptive Cards design guidelines](../../task-modules-and-cards/cards/design-effective-cards.md) for more information.)</span></span>

:::image type="content" source="../../assets/images/messaging-extension/insert-preview-link.png" alt-text="O exemplo mostra como a URL, como é reconhecida pelo seu aplicativo, inclui um conteúdo avançado na caixa de composição." border="false":::

## <a name="manage-a-messaging-extension"></a><span data-ttu-id="8f5fa-176">Gerenciar uma extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="8f5fa-176">Manage a messaging extension</span></span>

<span data-ttu-id="8f5fa-177">Ao clicar com o botão direito do mouse no ícone, os usuários podem fixar, remover ou configurar sua extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-177">By right clicking your icon, users can pin, remove, or configure your messaging extension.</span></span>

## <a name="anatomy"></a><span data-ttu-id="8f5fa-178">Anatomia</span><span class="sxs-lookup"><span data-stu-id="8f5fa-178">Anatomy</span></span>

### <a name="messaging-extension-in-the-compose-box"></a><span data-ttu-id="8f5fa-179">Extensão de mensagens na caixa de composição</span><span class="sxs-lookup"><span data-stu-id="8f5fa-179">Messaging extension in the compose box</span></span>

<span data-ttu-id="8f5fa-180">O exemplo a seguir é uma extensão de mensagens aberta da caixa de composição.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-180">The following example is a messaging extension opened from the compose box.</span></span>

:::image type="content" source="../../assets/images/messaging-extension/anatomy-compose.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de uma extensão de mensagens na caixa de composição." border="false":::

|<span data-ttu-id="8f5fa-182">Contador</span><span class="sxs-lookup"><span data-stu-id="8f5fa-182">Counter</span></span>|<span data-ttu-id="8f5fa-183">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f5fa-183">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="8f5fa-184">1</span><span class="sxs-lookup"><span data-stu-id="8f5fa-184">1</span></span>|<span data-ttu-id="8f5fa-185">**Logotipo do aplicativo**: ícone de cor do logotipo do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-185">**App logo**: Color icon of your app logo.</span></span>|
|<span data-ttu-id="8f5fa-186">2 </span><span class="sxs-lookup"><span data-stu-id="8f5fa-186">2</span></span>|<span data-ttu-id="8f5fa-187">**Nome do aplicativo**: nome completo do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-187">**App name**: Full name of your app.</span></span>|
|<span data-ttu-id="8f5fa-188">3 </span><span class="sxs-lookup"><span data-stu-id="8f5fa-188">3</span></span>|<span data-ttu-id="8f5fa-189">**Ícone de menu de comandos de ação (opcional)**: abre uma lista de comandos de ação para sua extensão de mensagens (se você especificar any).</span><span class="sxs-lookup"><span data-stu-id="8f5fa-189">**Action commands menu icon (optional)**: Opens a list of action commands for your messaging extension (if you specify any).</span></span>
|<span data-ttu-id="8f5fa-190">4 </span><span class="sxs-lookup"><span data-stu-id="8f5fa-190">4</span></span>|<span data-ttu-id="8f5fa-191">**Caixa de pesquisa**: permite que os usuários encontrem o conteúdo de aplicativo que deseja inserir.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-191">**Search box**: Allows users to find app content they want to insert.</span></span>|
|<span data-ttu-id="8f5fa-192">5 </span><span class="sxs-lookup"><span data-stu-id="8f5fa-192">5</span></span>|<span data-ttu-id="8f5fa-193">**Menu guia (opcional)**: fornece várias categorias de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-193">**Tab menu (optional)**: Provides multiple content categories.</span></span>|
|<span data-ttu-id="8f5fa-194">6 </span><span class="sxs-lookup"><span data-stu-id="8f5fa-194">6</span></span>|<span data-ttu-id="8f5fa-195">**Menu de comandos de ação (opcional)**: exibe a lista de comandos de ação (se você especificar any).</span><span class="sxs-lookup"><span data-stu-id="8f5fa-195">**Action commands menu (optional)**: Displays list of action commands (if you specify any).</span></span>|
|<span data-ttu-id="8f5fa-196">7 </span><span class="sxs-lookup"><span data-stu-id="8f5fa-196">7</span></span>|<span data-ttu-id="8f5fa-197">**Conteúdo do aplicativo**: primariamente para exibir resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-197">**App content**: Primarily to display search results.</span></span> <span data-ttu-id="8f5fa-198">O exemplo a seguir é usar o layout de lista (layout de grade é outra opção).</span><span class="sxs-lookup"><span data-stu-id="8f5fa-198">The example here is using the list layout (grid layout is another option).</span></span>|
|<span data-ttu-id="8f5fa-199">8 </span><span class="sxs-lookup"><span data-stu-id="8f5fa-199">8</span></span>|<span data-ttu-id="8f5fa-200">**Logotipo do aplicativo**: ícone de estrutura de tópicos do logotipo do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-200">**App logo**: Outline icon of your app logo.</span></span>|

### <a name="messaging-extension-management-menu"></a><span data-ttu-id="8f5fa-201">Menu de gerenciamento de extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="8f5fa-201">Messaging extension management menu</span></span>

:::image type="content" source="../../assets/images/messaging-extension/anatomy-management-menu.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de um menu de gerenciamento de extensão de mensagens." border="false":::

|<span data-ttu-id="8f5fa-203">Contador</span><span class="sxs-lookup"><span data-stu-id="8f5fa-203">Counter</span></span>|<span data-ttu-id="8f5fa-204">Descrição</span><span class="sxs-lookup"><span data-stu-id="8f5fa-204">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="8f5fa-205">1</span><span class="sxs-lookup"><span data-stu-id="8f5fa-205">1</span></span>|<span data-ttu-id="8f5fa-206">**Desafixar**: disponível se o usuário tiver afixado seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-206">**Unpin**: Available if the user has pinned your app.</span></span>|
|<span data-ttu-id="8f5fa-207">2 </span><span class="sxs-lookup"><span data-stu-id="8f5fa-207">2</span></span>|<span data-ttu-id="8f5fa-208">**Remover**: Remove a extensão de mensagens do canal, chat ou reunião.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-208">**Remove**: Removes the messaging extension from the channel, chat, or meeting.</span></span>|

## <a name="best-practices"></a><span data-ttu-id="8f5fa-209">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="8f5fa-209">Best practices</span></span>

### <a name="setup-and-general-usage"></a><span data-ttu-id="8f5fa-210">Configuração e uso geral</span><span class="sxs-lookup"><span data-stu-id="8f5fa-210">Setup and general usage</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-do.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de mensagens." border="false":::

#### <a name="do-integrate-with-single-sign-on"></a><span data-ttu-id="8f5fa-212">Fazer: integrar com logon único</span><span class="sxs-lookup"><span data-stu-id="8f5fa-212">Do: Integrate with single-sign on</span></span>

<span data-ttu-id="8f5fa-213">O SSO torna o processo de entrada mais fácil, rápido e seguro.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-213">SSO makes the sign-in process easier, faster, and secure.</span></span> <span data-ttu-id="8f5fa-214">Além disso, se um usuário já tiver entrado no seu aplicativo pessoal, ele também não precisará entrar novamente para acessar a extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-214">Also, if a user has already signed in to your personal app, they don’t have to also sign in again to access the messaging extension.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-dont.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de mensagens." border="false":::

#### <a name="dont-take-users-away-from-the-conversation"></a><span data-ttu-id="8f5fa-216">Não: retirar os usuários da conversa</span><span class="sxs-lookup"><span data-stu-id="8f5fa-216">Don't: Take users away from the conversation</span></span>

<span data-ttu-id="8f5fa-217">As extensões de mensagens são atalhos que supostamente reduzem a alternância de contexto.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-217">Messaging extensions are shortcuts that are supposed reduce context switching.</span></span> <span data-ttu-id="8f5fa-218">Sua extensão não deve, por exemplo, direcionar os usuários para uma página da Web fora do teams.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-218">Your extension should not, for example, direct users to a webpage outside Teams.</span></span>

   :::column-end:::
:::row-end:::

#### <a name="do-highlight-your-messaging-extension"></a><span data-ttu-id="8f5fa-219">Fazer: realçar sua extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="8f5fa-219">Do: Highlight your messaging extension</span></span>

<span data-ttu-id="8f5fa-220">As extensões de mensagens nem sempre são fáceis de encontrar.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-220">Messaging extensions aren't always easy to find.</span></span> <span data-ttu-id="8f5fa-221">Inclua capturas de tela de como usá-lo na página de detalhes do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-221">Include screenshots of how to use it in your app details page.</span></span> <span data-ttu-id="8f5fa-222">Se seu aplicativo também incluir um bot, você poderá incluir a documentação de ajuda de extensão de mensagens em um tour de boas-vindas do bot.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-222">If your app also includes a bot, you can include messaging extension help documentation in a bot welcome tour.</span></span>

### <a name="templating"></a><span data-ttu-id="8f5fa-223">Refere</span><span class="sxs-lookup"><span data-stu-id="8f5fa-223">Templating</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-do.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de mensagens." border="false":::

#### <a name="do-let-teams-handle-some-of-the-design-work-if-possible"></a><span data-ttu-id="8f5fa-225">Fazer: permitir que as equipes manipulem alguns dos trabalhos de design, se possível</span><span class="sxs-lookup"><span data-stu-id="8f5fa-225">Do: Let Teams handle some of the design work if possible</span></span>

<span data-ttu-id="8f5fa-226">Se fizer sentido para seus casos de uso, considere a criação de uma extensão de mensagens baseada em pesquisa.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-226">If it makes sense for your use cases, consider creating a search-based messaging extension.</span></span> <span data-ttu-id="8f5fa-227">O Microsoft Teams processa esses tipos de extensões com temas e acessibilidade internos.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-227">Teams renders these types of extensions with built-in theming and accessibility.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-dont.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de mensagens." border="false":::

#### <a name="dont-embed-your-entire-app-in-a-task-module"></a><span data-ttu-id="8f5fa-229">Não: Incorpore todo o aplicativo em um módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="8f5fa-229">Don't: Embed your entire app in a task module</span></span>

<span data-ttu-id="8f5fa-230">Se sua extensão de mensagens requer comandos de ação, mantenha o módulo de tarefas simples e exiba apenas os componentes necessários para concluir a ação.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-230">If your messaging extension requires action commands, keep the task module simple and display only the components required to complete the action.</span></span>

   :::column-end:::
:::row-end:::

### <a name="theming"></a><span data-ttu-id="8f5fa-231">Temas</span><span class="sxs-lookup"><span data-stu-id="8f5fa-231">Theming</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-do.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de mensagens." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a><span data-ttu-id="8f5fa-233">Fazer: aproveitar os tokens de cores do teams</span><span class="sxs-lookup"><span data-stu-id="8f5fa-233">Do: Take advantage of Teams color tokens</span></span>

<span data-ttu-id="8f5fa-234">Cada tema do teams tem seu próprio esquema de cores.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-234">Each Teams theme has its own color scheme.</span></span> <span data-ttu-id="8f5fa-235">Para lidar automaticamente com alterações de temas, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">tokens de cor (IU fluente)</a> em seu design.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-235">To handle theme changes automatically, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">color tokens (Fluent UI)</a> in your design.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-dont.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de mensagens." border="false":::

#### <a name="dont-hard-code-color-values"></a><span data-ttu-id="8f5fa-237">Não: valores de cor de código fixo</span><span class="sxs-lookup"><span data-stu-id="8f5fa-237">Don't: Hard code color values</span></span>

<span data-ttu-id="8f5fa-238">Se você não usar tokens de cores do Teams, seus designs serão menos escalonáveis e levará mais tempo para gerenciar.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-238">If you don't use Teams color tokens, your designs will be less scalable and take more time to manage.</span></span>

   :::column-end:::
:::row-end:::

### <a name="actions"></a><span data-ttu-id="8f5fa-239">Ações</span><span class="sxs-lookup"><span data-stu-id="8f5fa-239">Actions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-do.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de mensagens." border="false":::

#### <a name="do-include-action-commands-that-make-sense-in-context"></a><span data-ttu-id="8f5fa-241">Fazer: incluir comandos de ação que fazem sentido no contexto</span><span class="sxs-lookup"><span data-stu-id="8f5fa-241">Do: Include action commands that make sense in context</span></span>

<span data-ttu-id="8f5fa-242">As ações de mensagens devem estar relacionadas ao que um usuário está examinando.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-242">Message actions should relate to what a user is looking at.</span></span> <span data-ttu-id="8f5fa-243">Por exemplo, forneça aos usuários um atalho para a criação de um problema ou item de trabalho usando o texto na postagem de alguém.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-243">For example, provide users a shortcut for creating an issue or work item using the text in someone’s post.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-dont.png" alt-text="Exemplo mostrando uma prática recomendada de extensão de mensagens." border="false":::

#### <a name="dont-include-actions-commands-that-arent-contextual"></a><span data-ttu-id="8f5fa-245">Não: incluir comandos de ações que não são contextuais</span><span class="sxs-lookup"><span data-stu-id="8f5fa-245">Don't: Include actions commands that aren't contextual</span></span>

<span data-ttu-id="8f5fa-246">Uma ação de mensagem para **exibir seu painel** provavelmente parece ser desconectada da maioria das conversas.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-246">A message action to **View your dashboard** would probably seem disconnected from most conversations.</span></span>

   :::column-end:::
:::row-end:::

### <a name="searches"></a><span data-ttu-id="8f5fa-247">Search</span><span class="sxs-lookup"><span data-stu-id="8f5fa-247">Searches</span></span>

#### <a name="do-show-search-results-while-typing"></a><span data-ttu-id="8f5fa-248">: Mostrar resultados da pesquisa ao digitar</span><span class="sxs-lookup"><span data-stu-id="8f5fa-248">Do: Show search results while typing</span></span>

<span data-ttu-id="8f5fa-249">Fornecer resultados de pesquisa sugeridos enquanto os usuários digitam.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-249">Provide suggested search results while users type.</span></span> <span data-ttu-id="8f5fa-250">Eles podem encontrar o conteúdo que precisam mais rápido com uma quantidade mínima de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-250">They may find the content they need faster with minimal amount of characters.</span></span>

#### <a name="dont-require-users-to-submit-a-query"></a><span data-ttu-id="8f5fa-251">Não: exigir que os usuários enviem uma consulta</span><span class="sxs-lookup"><span data-stu-id="8f5fa-251">Don't: Require users to submit a query</span></span>

<span data-ttu-id="8f5fa-252">Você pode fazer com que os usuários pressionem uma tecla ou selecione um botão para enviar consultas ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-252">You can make users press a key or select a button to send queries to your app.</span></span> <span data-ttu-id="8f5fa-253">Embora isso possa ser mais fácil no serviço de serviços de aplicativos, as pessoas podem ficar confusas de que não estão vendo os resultados de pesquisa em tempo real à medida que eles digitam.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-253">While that may be easier on your app services service, people may be confused that they're not seeing real-time search results as they type.</span></span>

#### <a name="do-consider-zero-term-queries"></a><span data-ttu-id="8f5fa-254">Fazer: considerar consultas de zero prazos</span><span class="sxs-lookup"><span data-stu-id="8f5fa-254">Do: Consider zero-term queries</span></span>

<span data-ttu-id="8f5fa-255">Por exemplo, antes que um usuário escreva qualquer coisa na caixa de pesquisa, exiba o que foi exibido pela última vez em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-255">For example, before a user writes anything in the search box, display what they last viewed on your app.</span></span> <span data-ttu-id="8f5fa-256">É possível que eles desejam inserir esse conteúdo em sua conversa.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-256">It's possible that they want to insert that content into their conversation.</span></span>

## <a name="validate-your-design"></a><span data-ttu-id="8f5fa-257">Validar o design</span><span class="sxs-lookup"><span data-stu-id="8f5fa-257">Validate your design</span></span>

<span data-ttu-id="8f5fa-258">Se você planeja publicar seu aplicativo no AppSource, você deve compreender os problemas de design que geralmente causam falha nos aplicativos durante o envio.</span><span class="sxs-lookup"><span data-stu-id="8f5fa-258">If you plan to publish your app to AppSource, you should understand the design issues that commonly cause apps to fail during submission.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8f5fa-259">Verificar diretrizes de validação de design</span><span class="sxs-lookup"><span data-stu-id="8f5fa-259">Check design validation guidelines</span></span>](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
