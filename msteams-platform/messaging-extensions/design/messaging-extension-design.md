---
title: Projetando sua extensão de mensagens
description: Saiba como criar uma extensão de mensagens do Teams e obter o Kit de Interface do Usuário do Microsoft Teams.
keywords: práticas recomendadas de dicas de extensões de mensagens de referência de diretrizes de design do teams
author: heath-hamilton
localization_priority: Priority
ms.author: qinch
ms.topic: conceptual
ms.openlocfilehash: f4d1ba1e6e0b71b37e2b7b2d2a32fb729822ba1c
ms.sourcegitcommit: 99b1f151e4e36a86c6a5d2ccbde01bf45b61f526
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/21/2021
ms.locfileid: "53037667"
---
# <a name="designing-your-microsoft-teams-messaging-extension"></a><span data-ttu-id="fdc01-104">Criando sua extensão de mensagens do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="fdc01-104">Designing your Microsoft Teams messaging extension</span></span>

<span data-ttu-id="fdc01-105">Extensões de mensagens são atalhos para inserir conteúdo do aplicativo ou agir em uma mensagem sem sair da conversa.</span><span class="sxs-lookup"><span data-stu-id="fdc01-105">Messaging extensions are shortcuts for inserting app content or acting on a message without navigating away from the conversation.</span></span>
<span data-ttu-id="fdc01-106">Para orientar a criação do seu aplicativo, as informações a seguir descrevem e ilustram como as pessoas podem adicionar, usar e gerenciar extensões de mensagens no Teams.</span><span class="sxs-lookup"><span data-stu-id="fdc01-106">To guide your app design, the following information describes and illustrates how people can add, use, and manage messaging extensions in Teams.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="fdc01-107">Kit de IU do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="fdc01-107">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="fdc01-108">No Kit de Interface do Usuário do Microsoft Teams, você encontra diretrizes de design de extensão de mensagem mais abrangentes, incluindo elementos que você pode modificar conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="fdc01-108">You can find comprehensive messaging extension design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fdc01-109">Obtenha o Kit de IU do Microsoft Teams (Figma)</span><span class="sxs-lookup"><span data-stu-id="fdc01-109">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-messaging-extension"></a><span data-ttu-id="fdc01-110">Adicionar uma extensão de mensagem</span><span class="sxs-lookup"><span data-stu-id="fdc01-110">Add a messaging extension</span></span>

<span data-ttu-id="fdc01-111">Você pode adicionar uma extensão de mensagens nos seguintes contextos do Teams:</span><span class="sxs-lookup"><span data-stu-id="fdc01-111">You can add a messaging extension in the following Teams contexts:</span></span>

* <span data-ttu-id="fdc01-112">Vá para a Teams Store.</span><span class="sxs-lookup"><span data-stu-id="fdc01-112">From the Teams store.</span></span>
* <span data-ttu-id="fdc01-113">Em um canal, chat ou reunião (antes, durante e depois) próximo à caixa de redação.</span><span class="sxs-lookup"><span data-stu-id="fdc01-113">In a channel, chat, or meeting (before, during, and after) near the compose box.</span></span> <span data-ttu-id="fdc01-114">Vale a pena observar que se você adicionar uma extensão de mensagens em um desses locais, somente você poderá usá-la nesse contexto.</span><span class="sxs-lookup"><span data-stu-id="fdc01-114">It's worth noting if you add a messaging extension in one of these places, only you can use it in that context.</span></span>

<span data-ttu-id="fdc01-115">O exemplo a seguir mostra como adicionar uma extensão de mensagens em um canal:</span><span class="sxs-lookup"><span data-stu-id="fdc01-115">The following example shows how you add a messaging extension in a channel:</span></span>

# <a name="desktop"></a>[<span data-ttu-id="fdc01-116">Desktop</span><span class="sxs-lookup"><span data-stu-id="fdc01-116">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/add-in-channel.png" alt-text="O exemplo mostra como adicionar uma extensão de mensagens perto da caixa de redação em um canal." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="fdc01-118">Dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="fdc01-118">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-add-in-channel.png" alt-text="O exemplo mostra como adicionar uma extensão de mensagens perto da caixa de redação em um canal no celular." border="false":::

---

## <a name="set-up-a-messaging-extension"></a><span data-ttu-id="fdc01-120">Criar uma extensão de mensagem</span><span class="sxs-lookup"><span data-stu-id="fdc01-120">Set up a messaging extension</span></span>

<span data-ttu-id="fdc01-121">A autenticação não é obrigatória, mas se seu aplicativo for algo como uma ferramenta de acompanhamento de tíquetes, talvez seja necessário que as pessoas se conectem para usar a extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="fdc01-121">Authentication isn't mandatory, but if your app is something like a ticket tracking tool, you may need people to sign in to use the messaging extension.</span></span>

<span data-ttu-id="fdc01-122">Para consistência entre os aplicativos do Teams, você não pode personalizar a tela de entrada.</span><span class="sxs-lookup"><span data-stu-id="fdc01-122">For consistency across Teams apps, you can't customize the sign-in screen.</span></span> <span data-ttu-id="fdc01-123">Se você usar a autenticação de SSO (logon único), os usuários serão conectados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="fdc01-123">If you use single sign-on (SSO) authentication, users are signed in automatically.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="fdc01-124">Desktop</span><span class="sxs-lookup"><span data-stu-id="fdc01-124">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/set-up.png" alt-text="O exemplo mostra a tela de configuração da extensão de mensagens com um botão de entrada." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="fdc01-126">Dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="fdc01-126">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-set-up.png" alt-text="O exemplo mostra a tela de configuração da extensão de mensagens com um botão de entrada no celular." border="false":::

---

## <a name="types-of-messaging-extensions"></a><span data-ttu-id="fdc01-128">Tipos de extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="fdc01-128">Types of messaging extensions</span></span>

<span data-ttu-id="fdc01-129">As extensões de mensagens podem ter comandos de pesquisa, comandos de ação ou ambos.</span><span class="sxs-lookup"><span data-stu-id="fdc01-129">Messaging extensions can have search commands, action commands, or both.</span></span> <span data-ttu-id="fdc01-130">Seus comandos dependem dos recursos do seu aplicativo e de como eles se encaixam nos casos de uso do Teams.</span><span class="sxs-lookup"><span data-stu-id="fdc01-130">Your commands depend on your app's features and how those fit within Teams use cases.</span></span>

### <a name="search-commands"></a><span data-ttu-id="fdc01-131">Comandos de pesquisa</span><span class="sxs-lookup"><span data-stu-id="fdc01-131">Search commands</span></span>

<span data-ttu-id="fdc01-132">Com comandos de pesquisa, as pessoas podem usar sua extensão de mensagens para localizar rapidamente conteúdo externo e inserir em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="fdc01-132">With search commands, people can use your messaging extension to quickly find external content and insert into a message.</span></span> <span data-ttu-id="fdc01-133">Comandos de pesquisa normalmente são disponibilizados na caixa de redação.</span><span class="sxs-lookup"><span data-stu-id="fdc01-133">Search commands are commonly made available in the compose box.</span></span> <span data-ttu-id="fdc01-134">Por exemplo, você pode iniciar ou adicionar a uma discussão compartilhando um conteúdo sem sair do Teams.</span><span class="sxs-lookup"><span data-stu-id="fdc01-134">For example, you can start or add to a discussion by sharing a piece of content—without ever leaving Teams.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="fdc01-135">Desktop</span><span class="sxs-lookup"><span data-stu-id="fdc01-135">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/search-command-type.png" alt-text="O exemplo mostra uma extensão de mensagens baseada em pesquisa iniciada na caixa de redação." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="fdc01-137">Dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="fdc01-137">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-search-command-type.png" alt-text="O exemplo mostra uma extensão de mensagens baseada em pesquisa iniciada na caixa de texto no celular." border="false":::

---

#### <a name="compose-box-layout-options"></a><span data-ttu-id="fdc01-139">Opções de layout de caixa de texto</span><span class="sxs-lookup"><span data-stu-id="fdc01-139">Compose box layout options</span></span>

<span data-ttu-id="fdc01-140">Você tem algumas opções para exibir os resultados da pesquisa de extensão de mensagens, incluindo [modos de exibição em lista e grade](../../messaging-extensions/how-to/search-commands/respond-to-search.md#respond-to-user-requests).</span><span class="sxs-lookup"><span data-stu-id="fdc01-140">You have some options for displaying messaging extension search results, including [list and grid views](../../messaging-extensions/how-to/search-commands/respond-to-search.md#respond-to-user-requests).</span></span>

:::image type="content" source="../../assets/images/messaging-extension/search-result-layout.png" alt-text="Ilustrações mostrando opções de layout para resultados de pesquisa de extensão de mensagens." border="false":::

### <a name="action-commands"></a><span data-ttu-id="fdc01-142">Comandos de ação</span><span class="sxs-lookup"><span data-stu-id="fdc01-142">Action commands</span></span>

<span data-ttu-id="fdc01-143">Os comandos de ação permitem que as pessoas disparem ações e processem solicitações em serviços externos no Teams.</span><span class="sxs-lookup"><span data-stu-id="fdc01-143">Action commands allow people to trigger actions and process requests in external services within Teams.</span></span> <span data-ttu-id="fdc01-144">Por exemplo, se seu aplicativo rastreia pedidos, um usuário pode criar um novo pedido usando o conteúdo da mensagem de um colega diretamente dentro do chat.</span><span class="sxs-lookup"><span data-stu-id="fdc01-144">For example, if your app tracks orders, a user could create a new order using the contents of a colleague’s message from right inside their chat.</span></span>

<span data-ttu-id="fdc01-145">Extensões de mensagens baseadas em ação frequentemente exigem que os usuários preencham um formulário ou algum outro tipo de configuração dentro de um modal.</span><span class="sxs-lookup"><span data-stu-id="fdc01-145">Action-based messaging extensions frequently require users to complete a form or some other kind of configuration within a modal.</span></span> <span data-ttu-id="fdc01-146">Você pode criar essas experiências com [módulos de tarefa](../../task-modules-and-cards/task-modules/design-teams-task-modules.md).</span><span class="sxs-lookup"><span data-stu-id="fdc01-146">You can create these experiences with [task modules](../../task-modules-and-cards/task-modules/design-teams-task-modules.md).</span></span>

## <a name="open-a-messaging-extension"></a><span data-ttu-id="fdc01-147">Abrir uma extensão de mensagem</span><span class="sxs-lookup"><span data-stu-id="fdc01-147">Open a messaging extension</span></span>

<span data-ttu-id="fdc01-148">A caixa de redação e as mensagens ou postagens são os principais contextos nos quais as pessoas usam extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="fdc01-148">The compose box and messages or posts are the primary contexts where people use messaging extensions.</span></span>

### <a name="from-the-compose-box"></a><span data-ttu-id="fdc01-149">Na caixa de redação</span><span class="sxs-lookup"><span data-stu-id="fdc01-149">From the compose box</span></span>

<span data-ttu-id="fdc01-150">Depois de adicionados, os usuários podem abrir sua extensão de mensagens selecionando o ícone do aplicativo abaixo da caixa de redação.</span><span class="sxs-lookup"><span data-stu-id="fdc01-150">Once added, users can open your messaging extension by selecting your app icon below the compose box.</span></span> <span data-ttu-id="fdc01-151">Nesses exemplos, a extensão tem comandos de pesquisa e ação.</span><span class="sxs-lookup"><span data-stu-id="fdc01-151">In these examples, the extension has search and action commands.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="fdc01-152">Desktop</span><span class="sxs-lookup"><span data-stu-id="fdc01-152">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/open-from-compose-box.png" alt-text="O exemplo mostra como abrir uma extensão de mensagens na caixa de redação." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="fdc01-154">Dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="fdc01-154">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-open-from-compose-box.png" alt-text="O exemplo mostra como abrir uma extensão de mensagens na caixa redigir no celular." border="false":::

---

### <a name="from-a-chat-message-or-channel-post"></a><span data-ttu-id="fdc01-156">De uma mensagem de chat ou postagem de canal</span><span class="sxs-lookup"><span data-stu-id="fdc01-156">From a chat message or channel post</span></span>

Depois de adicionados, os usuários podem selecionar o ícone **Mais** :::image type="icon" source="../../assets/icons/teams-client-more.png"::: na mensagem de chat ou na postagem do canal para localizar os comandos de ação da extensão. <span data-ttu-id="fdc01-158">Sua extensão pode estar listada em **mais ações** com base no uso.</span><span class="sxs-lookup"><span data-stu-id="fdc01-158">Your extension may be listed under **More actions** based on usage.</span></span>

> [!NOTE]
> <span data-ttu-id="fdc01-159">O suporte para mais ações de uma mensagem de chat ou postagem de canal não está disponível na plataforma móvel do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="fdc01-159">Support for more actions from a chat message or channel post is not available on Microsoft Teams mobile platform.</span></span> 

#### <a name="chat-message"></a><span data-ttu-id="fdc01-160">Mensagem de chat</span><span class="sxs-lookup"><span data-stu-id="fdc01-160">Chat message</span></span>

# <a name="desktop"></a>[<span data-ttu-id="fdc01-161">Desktop</span><span class="sxs-lookup"><span data-stu-id="fdc01-161">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/open-from-chat-message.png" alt-text="O exemplo mostra como abrir uma extensão de mensagens de uma mensagem de chat." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="fdc01-163">Dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="fdc01-163">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-open-from-chat-post.png" alt-text="O exemplo mostra como abrir uma extensão de mensagens de uma postagem de chat no celular." border="false":::

---
':::image type="content" source="../../assets/images/messaging-extension/open-from-channel-post.png" alt-text="Example shows how to open a messaging extension from a channel post on mobile." border="false"::': null
':::image type="content" source="../../assets/images/messaging-extension/mobile-open-from-channel-post.png" alt-text="Example shows how to open a messaging extension from a channel post on mobile." border="false"::': null
---

## <a name="use-a-messaging-extension"></a><span data-ttu-id="fdc01-165">Adicionar uma extensão de mensagem</span><span class="sxs-lookup"><span data-stu-id="fdc01-165">Use a messaging extension</span></span>

<span data-ttu-id="fdc01-166">Os cenários a seguir mostram as principais formas como as pessoas usam extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="fdc01-166">The following scenarios show the primary ways people use messaging extensions.</span></span>

### <a name="insert-content-into-a-message"></a><span data-ttu-id="fdc01-167">Inserir conteúdo em uma mensagem</span><span class="sxs-lookup"><span data-stu-id="fdc01-167">Insert content into a message</span></span>

<span data-ttu-id="fdc01-168">**1. Selecione uma extensão de mensagem**.</span><span class="sxs-lookup"><span data-stu-id="fdc01-168">**1. Select a messaging extension**.</span></span> <span data-ttu-id="fdc01-169">Os usuários podem pesquisar o conteúdo que desejam compartilhar na caixa de redação.</span><span class="sxs-lookup"><span data-stu-id="fdc01-169">Users can search for the content they want to share from the compose box.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="fdc01-170">Desktop</span><span class="sxs-lookup"><span data-stu-id="fdc01-170">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/insert-content-search.png" alt-text="O exemplo mostra um usuário pesquisando o conteúdo a ser inserido na caixa de redação." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="fdc01-172">Dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="fdc01-172">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-insert-content-search.png" alt-text="O exemplo mostra um usuário pesquisando o conteúdo a ser inserido na caixa de texto no celular." border="false":::

---

<span data-ttu-id="fdc01-174">**2. Insira conteúdo**.</span><span class="sxs-lookup"><span data-stu-id="fdc01-174">**2. Insert content**.</span></span> <span data-ttu-id="fdc01-175">Depois de postados, outras pessoas podem responder ou selecionar o conteúdo para ver mais informações em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fdc01-175">Once posted, others can reply or select the content to see more information in your app.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="fdc01-176">Desktop</span><span class="sxs-lookup"><span data-stu-id="fdc01-176">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/insert-content-posted.png" alt-text="O exemplo mostra um usuário postando conteúdo em uma conversa de canal." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="fdc01-178">Dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="fdc01-178">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-insert-content-posted.png" alt-text="O exemplo mostra um usuário postando conteúdo em uma conversa de canal no celular." border="false":::

---

### <a name="take-action-on-a-message"></a><span data-ttu-id="fdc01-180">Executar ações em uma mensagem</span><span class="sxs-lookup"><span data-stu-id="fdc01-180">Take action on a message</span></span>

<span data-ttu-id="fdc01-181">**1. Selecione uma extensão de mensagem**.</span><span class="sxs-lookup"><span data-stu-id="fdc01-181">**1. Select a messaging extension**.</span></span> <span data-ttu-id="fdc01-182">Seu aplicativo pode incluir um ou mais comandos de ação.</span><span class="sxs-lookup"><span data-stu-id="fdc01-182">Your app can include one or more action commands.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="fdc01-183">Desktop</span><span class="sxs-lookup"><span data-stu-id="fdc01-183">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/select-action-command.png" alt-text="O exemplo mostra um usuário selecionando um comando de ação de extensão de mensagens." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="fdc01-185">Dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="fdc01-185">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-select-action-command.png" alt-text="O exemplo mostra um usuário selecionando um comando de ação de extensão de mensagens no celular." border="false":::

---

<span data-ttu-id="fdc01-187">**2. Conclua a ação**.</span><span class="sxs-lookup"><span data-stu-id="fdc01-187">**2. Complete the action**.</span></span> <span data-ttu-id="fdc01-188">Seu aplicativo pode receber e processar qualquer conteúdo ou dados enviados pela ação da mensagem.</span><span class="sxs-lookup"><span data-stu-id="fdc01-188">Your app can receive and process any content or data sent by the message action.</span></span> <span data-ttu-id="fdc01-189">Isso permite que os usuários permaneçam em suas conversas e, no exemplo a seguir, não se preocupem em inserir informações diretamente em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fdc01-189">This allows users to remain in their conversation and, the following example, not worry about entering information directly in your app.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="fdc01-190">Desktop</span><span class="sxs-lookup"><span data-stu-id="fdc01-190">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/complete-action-command.png" alt-text="Exemplo de como executar uma ação em uma mensagem." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="fdc01-192">Dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="fdc01-192">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-complete-action-command.png" alt-text="Exemplo de como executar uma ação em uma mensagem no celular." border="false":::

---

### <a name="preview-links"></a><span data-ttu-id="fdc01-194">Links de visualização</span><span class="sxs-lookup"><span data-stu-id="fdc01-194">Preview links</span></span>

<span data-ttu-id="fdc01-195">As extensões de mensagens também permitem que você insira links avançados de uma URL reconhecida em uma mensagem (essa funcionalidade é chamada de [desdobramento de link](../../messaging-extensions/how-to/link-unfurling.md).)</span><span class="sxs-lookup"><span data-stu-id="fdc01-195">Messaging extensions also allow you to insert rich links from a recognized URL into a message (this capability is called [link unfurling](../../messaging-extensions/how-to/link-unfurling.md).)</span></span>

<span data-ttu-id="fdc01-196">**1. Cole um link reconhecido** na caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="fdc01-196">**1. Paste a recognized link** in the compose box.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="fdc01-197">Desktop</span><span class="sxs-lookup"><span data-stu-id="fdc01-197">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/paste-preview-link.png" alt-text="O exemplo mostra um usuário colando um link na caixa de redação." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="fdc01-199">Dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="fdc01-199">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-paste-preview-link.png" alt-text="O exemplo mostra um usuário colando um link na caixa de redação no celular." border="false":::

---

<span data-ttu-id="fdc01-201">**2. Insira conteúdo**.</span><span class="sxs-lookup"><span data-stu-id="fdc01-201">**2. Insert content**.</span></span> <span data-ttu-id="fdc01-202">Se seu aplicativo reconhecer a URL na caixa de redação, ele renderizará o link como um cartão que fornece uma visualização com conteúdo avançado do conteúdo da Web.</span><span class="sxs-lookup"><span data-stu-id="fdc01-202">If your app recognizes the URL in the compose box, it renders the link as a card that provides a content-rich preview of the web content.</span></span> <span data-ttu-id="fdc01-203">(Consulte as [Diretrizes de design de Cartões Adaptáveis](../../task-modules-and-cards/cards/design-effective-cards.md) para obter mais informações.)</span><span class="sxs-lookup"><span data-stu-id="fdc01-203">(See [Adaptive Cards design guidelines](../../task-modules-and-cards/cards/design-effective-cards.md) for more information.)</span></span>

# <a name="desktop"></a>[<span data-ttu-id="fdc01-204">Desktop</span><span class="sxs-lookup"><span data-stu-id="fdc01-204">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/insert-preview-link.png" alt-text="O exemplo mostra como a URL, já que é reconhecida pelo seu aplicativo, inclui algum conteúdo avançado na caixa de redação." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="fdc01-206">Dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="fdc01-206">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-insert-preview-link.png" alt-text="O exemplo mostra como a URL, já que é reconhecida pelo seu aplicativo, inclui algum conteúdo avançado na caixa de redação no celular." border="false":::

---

## <a name="manage-a-messaging-extension"></a><span data-ttu-id="fdc01-208">Gerenciar uma extensão de mensagem</span><span class="sxs-lookup"><span data-stu-id="fdc01-208">Manage a messaging extension</span></span>

<span data-ttu-id="fdc01-209">Ao clicar com o botão direito do mouse no ícone, os usuários podem fixar, remover ou configurar sua extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="fdc01-209">By right clicking your icon, users can pin, remove, or configure your messaging extension.</span></span>

## <a name="anatomy"></a><span data-ttu-id="fdc01-210">Anatomia</span><span class="sxs-lookup"><span data-stu-id="fdc01-210">Anatomy</span></span>

### <a name="messaging-extension-in-the-compose-box"></a><span data-ttu-id="fdc01-211">Extensão de mensagens na caixa de redação</span><span class="sxs-lookup"><span data-stu-id="fdc01-211">Messaging extension in the compose box</span></span>

<span data-ttu-id="fdc01-212">O exemplo a seguir é uma extensão de mensagens aberta na caixa de redação.</span><span class="sxs-lookup"><span data-stu-id="fdc01-212">The following example is a messaging extension opened from the compose box.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="fdc01-213">Desktop</span><span class="sxs-lookup"><span data-stu-id="fdc01-213">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/anatomy-compose.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de uma extensão de mensagens na caixa de redação." border="false":::

|<span data-ttu-id="fdc01-215">Contador</span><span class="sxs-lookup"><span data-stu-id="fdc01-215">Counter</span></span>|<span data-ttu-id="fdc01-216">Descrição</span><span class="sxs-lookup"><span data-stu-id="fdc01-216">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="fdc01-217">1</span><span class="sxs-lookup"><span data-stu-id="fdc01-217">1</span></span>|<span data-ttu-id="fdc01-218">**Logotipo do aplicativo**: ícone de cor do logotipo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fdc01-218">**App logo**: Color icon of your app logo.</span></span>|
|<span data-ttu-id="fdc01-219">2</span><span class="sxs-lookup"><span data-stu-id="fdc01-219">2</span></span>|<span data-ttu-id="fdc01-220">**Nome do aplicativo**: nome completo do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fdc01-220">**App name**: Full name of your app.</span></span>|
|<span data-ttu-id="fdc01-221">3</span><span class="sxs-lookup"><span data-stu-id="fdc01-221">3</span></span>|<span data-ttu-id="fdc01-222">**Ícone de menu de comandos de ação (opcional)**: abre uma lista de comandos de ação para sua extensão de mensagens (se você especificar algum).</span><span class="sxs-lookup"><span data-stu-id="fdc01-222">**Action commands menu icon (optional)**: Opens a list of action commands for your messaging extension (if you specify any).</span></span>
|<span data-ttu-id="fdc01-223">4</span><span class="sxs-lookup"><span data-stu-id="fdc01-223">4</span></span>|<span data-ttu-id="fdc01-224">**Caixa de pesquisa**: permite que os usuários localizem o conteúdo do aplicativo que desejam inserir.</span><span class="sxs-lookup"><span data-stu-id="fdc01-224">**Search box**: Allows users to find app content they want to insert.</span></span>|
|<span data-ttu-id="fdc01-225">5</span><span class="sxs-lookup"><span data-stu-id="fdc01-225">5</span></span>|<span data-ttu-id="fdc01-226">**Menu guia (opcional)**: fornece várias categorias de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="fdc01-226">**Tab menu (optional)**: Provides multiple content categories.</span></span>|
|<span data-ttu-id="fdc01-227">6</span><span class="sxs-lookup"><span data-stu-id="fdc01-227">6</span></span>|<span data-ttu-id="fdc01-228">**Menu de comandos de ação (opcional)**: exibe a lista de comandos de ação (se você especificar algum).</span><span class="sxs-lookup"><span data-stu-id="fdc01-228">**Action commands menu (optional)**: Displays list of action commands (if you specify any).</span></span>|
|<span data-ttu-id="fdc01-229">7</span><span class="sxs-lookup"><span data-stu-id="fdc01-229">7</span></span>|<span data-ttu-id="fdc01-230">**Conteúdo do aplicativo**: principalmente para exibir os resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="fdc01-230">**App content**: Primarily to display search results.</span></span> <span data-ttu-id="fdc01-231">O exemplo aqui está usando o layout da lista (o layout da grade é outra opção).</span><span class="sxs-lookup"><span data-stu-id="fdc01-231">The example here is using the list layout (grid layout is another option).</span></span>|
|<span data-ttu-id="fdc01-232">8</span><span class="sxs-lookup"><span data-stu-id="fdc01-232">8</span></span>|<span data-ttu-id="fdc01-233">**Logotipo do aplicativo**: ícone de contorno do logotipo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fdc01-233">**App logo**: Outline icon of your app logo.</span></span>|

# <a name="mobile"></a>[<span data-ttu-id="fdc01-234">Dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="fdc01-234">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-anatomy-compose.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de uma extensão de mensagens na caixa de redação no celular." border="false":::

|<span data-ttu-id="fdc01-236">Contador</span><span class="sxs-lookup"><span data-stu-id="fdc01-236">Counter</span></span>|<span data-ttu-id="fdc01-237">Descrição</span><span class="sxs-lookup"><span data-stu-id="fdc01-237">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="fdc01-238">1</span><span class="sxs-lookup"><span data-stu-id="fdc01-238">1</span></span>|<span data-ttu-id="fdc01-239">**Nome do aplicativo**: nome completo do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fdc01-239">**App name**: Full name of your app.</span></span>|
|<span data-ttu-id="fdc01-240">2</span><span class="sxs-lookup"><span data-stu-id="fdc01-240">2</span></span>|<span data-ttu-id="fdc01-241">**Ícone de menu de comandos de ação (opcional)**: abre uma lista de comandos de ação para sua extensão de mensagens (se você especificar algum).</span><span class="sxs-lookup"><span data-stu-id="fdc01-241">**Action commands menu icon (optional)**: Opens a list of action commands for your messaging extension (if you specify any).</span></span>
|<span data-ttu-id="fdc01-242">3</span><span class="sxs-lookup"><span data-stu-id="fdc01-242">3</span></span>|<span data-ttu-id="fdc01-243">**Caixa de pesquisa**: permite que os usuários localizem o conteúdo do aplicativo que desejam inserir.</span><span class="sxs-lookup"><span data-stu-id="fdc01-243">**Search box**: Allows users to find app content they want to insert.</span></span>|
|<span data-ttu-id="fdc01-244">4</span><span class="sxs-lookup"><span data-stu-id="fdc01-244">4</span></span>|<span data-ttu-id="fdc01-245">**Menu guia (opcional)**: fornece várias categorias de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="fdc01-245">**Tab menu (optional)**: Provides multiple content categories.</span></span>|
|<span data-ttu-id="fdc01-246">5</span><span class="sxs-lookup"><span data-stu-id="fdc01-246">5</span></span>|<span data-ttu-id="fdc01-247">**Menu de comandos de ação (opcional)**: exibe a lista de comandos de ação (se você especificar algum).</span><span class="sxs-lookup"><span data-stu-id="fdc01-247">**Action commands menu (optional)**: Displays list of action commands (if you specify any).</span></span>|
|<span data-ttu-id="fdc01-248">6</span><span class="sxs-lookup"><span data-stu-id="fdc01-248">6</span></span>|<span data-ttu-id="fdc01-249">**Conteúdo do aplicativo**: principalmente para exibir os resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="fdc01-249">**App content**: Primarily to display search results.</span></span>|

---

### <a name="messaging-extension-management-menu"></a><span data-ttu-id="fdc01-250">Menu de gerenciamento de extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="fdc01-250">Messaging extension management menu</span></span>

:::image type="content" source="../../assets/images/messaging-extension/anatomy-management-menu.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de um menu de gerenciamento de extensão de mensagens." border="false":::

|<span data-ttu-id="fdc01-252">Contador</span><span class="sxs-lookup"><span data-stu-id="fdc01-252">Counter</span></span>|<span data-ttu-id="fdc01-253">Descrição</span><span class="sxs-lookup"><span data-stu-id="fdc01-253">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="fdc01-254">1</span><span class="sxs-lookup"><span data-stu-id="fdc01-254">1</span></span>|<span data-ttu-id="fdc01-255">**Desafixar**: disponível se o usuário fixou seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fdc01-255">**Unpin**: Available if the user has pinned your app.</span></span>|
|<span data-ttu-id="fdc01-256">2</span><span class="sxs-lookup"><span data-stu-id="fdc01-256">2</span></span>|<span data-ttu-id="fdc01-257">**Remover**: remove a extensão de mensagens do canal, chat ou reunião.</span><span class="sxs-lookup"><span data-stu-id="fdc01-257">**Remove**: Removes the messaging extension from the channel, chat, or meeting.</span></span>|

## <a name="best-practices"></a><span data-ttu-id="fdc01-258">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="fdc01-258">Best practices</span></span>

<span data-ttu-id="fdc01-259">Use essas recomendações para criar uma experiência de aplicativo de qualidade.</span><span class="sxs-lookup"><span data-stu-id="fdc01-259">Use these recommendations to create a quality app experience.</span></span>

### <a name="setup-and-general-usage"></a><span data-ttu-id="fdc01-260">Configuração e uso geral</span><span class="sxs-lookup"><span data-stu-id="fdc01-260">Setup and general usage</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-do.png" alt-text="Exemplo de configuração e uso geral." border="false":::

#### <a name="do-integrate-with-single-sign-on"></a><span data-ttu-id="fdc01-262">Recomendamos: integrar com logon único</span><span class="sxs-lookup"><span data-stu-id="fdc01-262">Do: Integrate with single-sign on</span></span>

<span data-ttu-id="fdc01-263">O SSO torna o processo de entrada mais fácil, rápido e seguro.</span><span class="sxs-lookup"><span data-stu-id="fdc01-263">SSO makes the sign-in process easier, faster, and secure.</span></span> <span data-ttu-id="fdc01-264">Além disso, se um usuário já tiver entrado em seu aplicativo pessoal, ele não precisará entrar novamente para acessar a extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="fdc01-264">Also, if a user has already signed in to your personal app, they don’t have to also sign in again to access the messaging extension.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-dont.png" alt-text="Exemplo de integração com logon único." border="false":::

#### <a name="dont-take-users-away-from-the-conversation"></a><span data-ttu-id="fdc01-266">Não recomendamos: remover os usuários da conversa</span><span class="sxs-lookup"><span data-stu-id="fdc01-266">Don't: Take users away from the conversation</span></span>

<span data-ttu-id="fdc01-267">Extensões de mensagens são atalhos que devem reduzir a alternância de contexto.</span><span class="sxs-lookup"><span data-stu-id="fdc01-267">Messaging extensions are shortcuts that are supposed reduce context switching.</span></span> <span data-ttu-id="fdc01-268">Sua extensão não deve, por exemplo, direcionar usuários para uma página da Web fora do Teams.</span><span class="sxs-lookup"><span data-stu-id="fdc01-268">Your extension should not, for example, direct users to a webpage outside Teams.</span></span>

   :::column-end:::
:::row-end:::

#### <a name="do-highlight-your-messaging-extension"></a><span data-ttu-id="fdc01-269">Recomendamos: realçar sua extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="fdc01-269">Do: Highlight your messaging extension</span></span>

<span data-ttu-id="fdc01-270">As extensões de mensagens nem sempre são fáceis de localizar.</span><span class="sxs-lookup"><span data-stu-id="fdc01-270">Messaging extensions aren't always easy to find.</span></span> <span data-ttu-id="fdc01-271">Inclua capturas de tela de como usá-las na página de detalhes do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fdc01-271">Include screenshots of how to use it in your app details page.</span></span> <span data-ttu-id="fdc01-272">Se seu aplicativo também incluir um bot, você poderá incluir a documentação da ajuda da extensão de mensagens em um tour de boas-vindas do bot.</span><span class="sxs-lookup"><span data-stu-id="fdc01-272">If your app also includes a bot, you can include messaging extension help documentation in a bot welcome tour.</span></span>

### <a name="templating"></a><span data-ttu-id="fdc01-273">Modelagem</span><span class="sxs-lookup"><span data-stu-id="fdc01-273">Templating</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-do.png" alt-text="Exemplo de modelagem." border="false":::

#### <a name="do-let-teams-handle-some-of-the-design-work-if-possible"></a><span data-ttu-id="fdc01-275">Recomendamos: permitir que o Teams cuide de parte do trabalho de design, se possível</span><span class="sxs-lookup"><span data-stu-id="fdc01-275">Do: Let Teams handle some of the design work if possible</span></span>

<span data-ttu-id="fdc01-276">Se fizer sentido para seus casos de uso, considere criar uma extensão de mensagens baseada em pesquisa.</span><span class="sxs-lookup"><span data-stu-id="fdc01-276">If it makes sense for your use cases, consider creating a search-based messaging extension.</span></span> <span data-ttu-id="fdc01-277">O Teams renderiza esses tipos de extensões com temas e acessibilidade internos.</span><span class="sxs-lookup"><span data-stu-id="fdc01-277">Teams renders these types of extensions with built-in theming and accessibility.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-dont.png" alt-text="Exemplo de como o trabalho de design é cuidado." border="false":::

#### <a name="dont-embed-your-entire-app-in-a-task-module"></a><span data-ttu-id="fdc01-279">Não recomendamos: inserir todo o aplicativo em um módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="fdc01-279">Don't: Embed your entire app in a task module</span></span>

<span data-ttu-id="fdc01-280">Se a extensão de mensagens exigir comandos de ação, mantenha o módulo de tarefa simples e exiba apenas os componentes necessários para concluir a ação.</span><span class="sxs-lookup"><span data-stu-id="fdc01-280">If your messaging extension requires action commands, keep the task module simple and display only the components required to complete the action.</span></span>

   :::column-end:::
:::row-end:::

### <a name="theming"></a><span data-ttu-id="fdc01-281">Temas</span><span class="sxs-lookup"><span data-stu-id="fdc01-281">Theming</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-do.png" alt-text="Exemplo de temas." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a><span data-ttu-id="fdc01-283">Recomendamos: aproveitar os tokens de cor do Teams</span><span class="sxs-lookup"><span data-stu-id="fdc01-283">Do: Take advantage of Teams color tokens</span></span>

<span data-ttu-id="fdc01-284">Cada tema do Teams tem seu próprio esquema de cores.</span><span class="sxs-lookup"><span data-stu-id="fdc01-284">Each Teams theme has its own color scheme.</span></span> <span data-ttu-id="fdc01-285">Para manipular as alterações de tema automaticamente, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">tokens de cores (IU do Fluent)</a> em seu design.</span><span class="sxs-lookup"><span data-stu-id="fdc01-285">To handle theme changes automatically, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">color tokens (Fluent UI)</a> in your design.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-dont.png" alt-text="Exemplos de tokens de cor." border="false":::

#### <a name="dont-hard-code-color-values"></a><span data-ttu-id="fdc01-287">Não recomendamos: valores de cor de código rígido</span><span class="sxs-lookup"><span data-stu-id="fdc01-287">Don't: Hard code color values</span></span>

<span data-ttu-id="fdc01-288">Se você não usar tokens de cor do Teams, seus designs serão menos escalonáveis e levarão mais tempo para serem gerenciados.</span><span class="sxs-lookup"><span data-stu-id="fdc01-288">If you don't use Teams color tokens, your designs will be less scalable and take more time to manage.</span></span>

   :::column-end:::
:::row-end:::

### <a name="actions"></a><span data-ttu-id="fdc01-289">Ações</span><span class="sxs-lookup"><span data-stu-id="fdc01-289">Actions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-do.png" alt-text="Exemplo de ações." border="false":::

#### <a name="do-include-action-commands-that-make-sense-in-context"></a><span data-ttu-id="fdc01-291">Recomendamos: incluir comandos de ação que fazem sentido no contexto</span><span class="sxs-lookup"><span data-stu-id="fdc01-291">Do: Include action commands that make sense in context</span></span>

<span data-ttu-id="fdc01-292">As ações de mensagem devem estar relacionadas ao que um usuário está olhando.</span><span class="sxs-lookup"><span data-stu-id="fdc01-292">Message actions should relate to what a user is looking at.</span></span> <span data-ttu-id="fdc01-293">Por exemplo, forneça aos usuários um atalho para criar um problema ou item de trabalho usando o texto na postagem de alguém.</span><span class="sxs-lookup"><span data-stu-id="fdc01-293">For example, provide users a shortcut for creating an issue or work item using the text in someone’s post.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-dont.png" alt-text="Exemplos de comandos de ação." border="false":::

#### <a name="dont-include-actions-commands-that-arent-contextual"></a><span data-ttu-id="fdc01-295">Não recomendamos: incluir comandos de ações que não são contextuais</span><span class="sxs-lookup"><span data-stu-id="fdc01-295">Don't: Include actions commands that aren't contextual</span></span>

<span data-ttu-id="fdc01-296">Uma ação de mensagem para **exibir seu painel** provavelmente pareceria desconectada da maioria das conversas.</span><span class="sxs-lookup"><span data-stu-id="fdc01-296">A message action to **View your dashboard** would probably seem disconnected from most conversations.</span></span>

   :::column-end:::
:::row-end:::

### <a name="searches"></a><span data-ttu-id="fdc01-297">Pesquisas</span><span class="sxs-lookup"><span data-stu-id="fdc01-297">Searches</span></span>

#### <a name="do-show-search-results-while-typing"></a><span data-ttu-id="fdc01-298">Recomendamos: mostrar resultados da pesquisa ao digitar</span><span class="sxs-lookup"><span data-stu-id="fdc01-298">Do: Show search results while typing</span></span>

<span data-ttu-id="fdc01-299">Forneça resultados de pesquisa sugeridos enquanto os usuários digitam.</span><span class="sxs-lookup"><span data-stu-id="fdc01-299">Provide suggested search results while users type.</span></span> <span data-ttu-id="fdc01-300">Eles podem encontrar o conteúdo de que precisam mais rapidamente com a quantidade mínima de caracteres.</span><span class="sxs-lookup"><span data-stu-id="fdc01-300">They may find the content they need faster with minimal amount of characters.</span></span>

#### <a name="dont-require-users-to-submit-a-query"></a><span data-ttu-id="fdc01-301">Não recomendamos: exigir que os usuários enviem uma consulta</span><span class="sxs-lookup"><span data-stu-id="fdc01-301">Don't: Require users to submit a query</span></span>

<span data-ttu-id="fdc01-302">Você pode fazer com que os usuários pressionem uma tecla ou selecionem um botão para enviar consultas ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fdc01-302">You can make users press a key or select a button to send queries to your app.</span></span> <span data-ttu-id="fdc01-303">Embora isso possa ser mais fácil para o serviço de serviços de aplicativo, as pessoas podem ficar confusas por não estarem vendo os resultados da pesquisa em tempo real enquanto digitam.</span><span class="sxs-lookup"><span data-stu-id="fdc01-303">While that may be easier on your app services service, people may be confused that they're not seeing real-time search results as they type.</span></span>

#### <a name="do-consider-zero-term-queries"></a><span data-ttu-id="fdc01-304">Recomendamos: considerar consultas de zero termo</span><span class="sxs-lookup"><span data-stu-id="fdc01-304">Do: Consider zero-term queries</span></span>

<span data-ttu-id="fdc01-305">Por exemplo, antes de um usuário gravar qualquer coisa na caixa de pesquisa, exiba o que ele visualizou pela última vez em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fdc01-305">For example, before a user writes anything in the search box, display what they last viewed on your app.</span></span> <span data-ttu-id="fdc01-306">É possível que eles desejem inserir esse conteúdo em suas conversas.</span><span class="sxs-lookup"><span data-stu-id="fdc01-306">It's possible that they want to insert that content into their conversation.</span></span>
