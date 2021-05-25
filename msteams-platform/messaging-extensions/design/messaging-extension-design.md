---
title: Projetando sua extensão de mensagens
description: Saiba como projetar uma extensão Teams de mensagens e obter o kit Microsoft Teams interface do usuário.
keywords: Práticas práticas práticas de referência de extensões de mensagens de referência de diretrizes de design do teams
author: heath-hamilton
localization_priority: Normal
ms.author: qinch
ms.topic: conceptual
ms.openlocfilehash: fd870d8e10ef74c36f8f6d145d48980f53e9303c
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2021
ms.locfileid: "52631017"
---
# <a name="designing-your-microsoft-teams-messaging-extension"></a><span data-ttu-id="4f505-104">Projetando sua extensão Microsoft Teams de mensagens</span><span class="sxs-lookup"><span data-stu-id="4f505-104">Designing your Microsoft Teams messaging extension</span></span>

<span data-ttu-id="4f505-105">Extensões de mensagens são atalhos para inserir conteúdo do aplicativo ou agir em uma mensagem sem sair da conversa.</span><span class="sxs-lookup"><span data-stu-id="4f505-105">Messaging extensions are shortcuts for inserting app content or acting on a message without navigating away from the conversation.</span></span>
<span data-ttu-id="4f505-106">Para orientar o design do aplicativo, as informações a seguir descrevem e ilustram como as pessoas podem adicionar, usar e gerenciar extensões de mensagens em Teams.</span><span class="sxs-lookup"><span data-stu-id="4f505-106">To guide your app design, the following information describes and illustrates how people can add, use, and manage messaging extensions in Teams.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="4f505-107">Kit de Interface do Usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="4f505-107">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="4f505-108">Você pode encontrar diretrizes abrangentes de design de extensão de mensagens, incluindo elementos que você pode pegar e modificar conforme necessário, no Kit de interface do usuário Microsoft Teams usuário.</span><span class="sxs-lookup"><span data-stu-id="4f505-108">You can find comprehensive messaging extension design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4f505-109">Obtenha o Kit de Interface do Usuário do Microsoft Teams (Figma)</span><span class="sxs-lookup"><span data-stu-id="4f505-109">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-messaging-extension"></a><span data-ttu-id="4f505-110">Adicionar uma extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="4f505-110">Add a messaging extension</span></span>

<span data-ttu-id="4f505-111">Você pode adicionar uma extensão de mensagens nos seguintes Teams contextos:</span><span class="sxs-lookup"><span data-stu-id="4f505-111">You can add a messaging extension in the following Teams contexts:</span></span>

* <span data-ttu-id="4f505-112">No Teams store.</span><span class="sxs-lookup"><span data-stu-id="4f505-112">From the Teams store.</span></span>
* <span data-ttu-id="4f505-113">Em um canal, chat ou reunião (antes, durante e depois) perto da caixa de composição.</span><span class="sxs-lookup"><span data-stu-id="4f505-113">In a channel, chat, or meeting (before, during, and after) near the compose box.</span></span> <span data-ttu-id="4f505-114">Vale a pena notar se você adicionar uma extensão de mensagens em um desses locais, somente você poderá usá-la nesse contexto.</span><span class="sxs-lookup"><span data-stu-id="4f505-114">It's worth noting if you add a messaging extension in one of these places, only you can use it in that context.</span></span>

<span data-ttu-id="4f505-115">O exemplo a seguir mostra como você adiciona uma extensão de mensagens em um canal:</span><span class="sxs-lookup"><span data-stu-id="4f505-115">The following example shows how you add a messaging extension in a channel:</span></span>

# <a name="desktop"></a>[<span data-ttu-id="4f505-116">Desktop</span><span class="sxs-lookup"><span data-stu-id="4f505-116">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/add-in-channel.png" alt-text="Exemplo mostra como adicionar uma extensão de mensagens perto da caixa de redação em um canal." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="4f505-118">Mobile</span><span class="sxs-lookup"><span data-stu-id="4f505-118">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-add-in-channel.png" alt-text="Exemplo mostra como adicionar uma extensão de mensagens perto da caixa de redação em um canal no celular." border="false":::

---

## <a name="set-up-a-messaging-extension"></a><span data-ttu-id="4f505-120">Configurar uma extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="4f505-120">Set up a messaging extension</span></span>

<span data-ttu-id="4f505-121">A autenticação não é obrigatória, mas se seu aplicativo for algo como uma ferramenta de controle de tíquetes, talvez seja necessário que as pessoas entre para usar a extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="4f505-121">Authentication isn't mandatory, but if your app is something like a ticket tracking tool, you may need people to sign in to use the messaging extension.</span></span>

<span data-ttu-id="4f505-122">Para ter consistência Teams aplicativos, você não pode personalizar a tela de login.</span><span class="sxs-lookup"><span data-stu-id="4f505-122">For consistency across Teams apps, you can't customize the sign-in screen.</span></span> <span data-ttu-id="4f505-123">Se você usar a autenticação de logom único (SSO), os usuários serão automaticamente assinados.</span><span class="sxs-lookup"><span data-stu-id="4f505-123">If you use single sign-on (SSO) authentication, users are signed in automatically.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="4f505-124">Desktop</span><span class="sxs-lookup"><span data-stu-id="4f505-124">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/set-up.png" alt-text="Exemplo mostra a tela de instalação de extensão de mensagens com um botão de login." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="4f505-126">Mobile</span><span class="sxs-lookup"><span data-stu-id="4f505-126">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-set-up.png" alt-text="Exemplo mostra a tela de configuração de extensão de mensagens com um botão de login no celular." border="false":::

---

## <a name="types-of-messaging-extensions"></a><span data-ttu-id="4f505-128">Tipos de extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="4f505-128">Types of messaging extensions</span></span>

<span data-ttu-id="4f505-129">As extensões de mensagens podem ter comandos de pesquisa, comandos de ação ou ambos.</span><span class="sxs-lookup"><span data-stu-id="4f505-129">Messaging extensions can have search commands, action commands, or both.</span></span> <span data-ttu-id="4f505-130">Seus comandos dependem dos recursos do aplicativo e de como eles se ajustam Teams casos de uso.</span><span class="sxs-lookup"><span data-stu-id="4f505-130">Your commands depend on your app's features and how those fit within Teams use cases.</span></span>

### <a name="search-commands"></a><span data-ttu-id="4f505-131">Comandos de pesquisa</span><span class="sxs-lookup"><span data-stu-id="4f505-131">Search commands</span></span>

<span data-ttu-id="4f505-132">Com comandos de pesquisa, as pessoas podem usar sua extensão de mensagens para encontrar rapidamente conteúdo externo e inserir em uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="4f505-132">With search commands, people can use your messaging extension to quickly find external content and insert into a message.</span></span> <span data-ttu-id="4f505-133">Comandos de pesquisa são comumente disponibilizados na caixa de redação.</span><span class="sxs-lookup"><span data-stu-id="4f505-133">Search commands are commonly made available in the compose box.</span></span> <span data-ttu-id="4f505-134">Por exemplo, você pode iniciar ou adicionar a uma discussão compartilhando um conteúdo sem sair Teams.</span><span class="sxs-lookup"><span data-stu-id="4f505-134">For example, you can start or add to a discussion by sharing a piece of content—without ever leaving Teams.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="4f505-135">Desktop</span><span class="sxs-lookup"><span data-stu-id="4f505-135">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/search-command-type.png" alt-text="Exemplo mostra uma extensão de mensagens baseada em pesquisa lançada na caixa de redação." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="4f505-137">Mobile</span><span class="sxs-lookup"><span data-stu-id="4f505-137">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-search-command-type.png" alt-text="Exemplo mostra uma extensão de mensagens baseada em pesquisa lançada na caixa de redação no celular." border="false":::

---

#### <a name="compose-box-layout-options"></a><span data-ttu-id="4f505-139">Opções de layout de caixa de redação</span><span class="sxs-lookup"><span data-stu-id="4f505-139">Compose box layout options</span></span>

<span data-ttu-id="4f505-140">Você tem algumas opções para exibir resultados de pesquisa de extensão de mensagens, incluindo [exibições de lista e grade.](../../messaging-extensions/how-to/search-commands/respond-to-search.md#respond-to-user-requests)</span><span class="sxs-lookup"><span data-stu-id="4f505-140">You have some options for displaying messaging extension search results, including [list and grid views](../../messaging-extensions/how-to/search-commands/respond-to-search.md#respond-to-user-requests).</span></span>

:::image type="content" source="../../assets/images/messaging-extension/search-result-layout.png" alt-text="Ilustrações mostrando opções de layout para resultados de pesquisa de extensão de mensagens." border="false":::

### <a name="action-commands"></a><span data-ttu-id="4f505-142">Comandos de ação</span><span class="sxs-lookup"><span data-stu-id="4f505-142">Action commands</span></span>

<span data-ttu-id="4f505-143">Comandos de ação permitem que as pessoas acionem ações e solicitações de processo em serviços externos Teams.</span><span class="sxs-lookup"><span data-stu-id="4f505-143">Action commands allow people to trigger actions and process requests in external services within Teams.</span></span> <span data-ttu-id="4f505-144">Por exemplo, se seu aplicativo rastreia pedidos, um usuário pode criar uma nova ordem usando o conteúdo da mensagem de um colega de dentro do chat.</span><span class="sxs-lookup"><span data-stu-id="4f505-144">For example, if your app tracks orders, a user could create a new order using the contents of a colleague’s message from right inside their chat.</span></span>

<span data-ttu-id="4f505-145">Extensões de mensagens baseadas em ação frequentemente exigem que os usuários concluam um formulário ou algum outro tipo de configuração dentro de um modal.</span><span class="sxs-lookup"><span data-stu-id="4f505-145">Action-based messaging extensions frequently require users to complete a form or some other kind of configuration within a modal.</span></span> <span data-ttu-id="4f505-146">Você pode criar essas experiências com [módulos de tarefa.](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)</span><span class="sxs-lookup"><span data-stu-id="4f505-146">You can create these experiences with [task modules](../../task-modules-and-cards/task-modules/design-teams-task-modules.md).</span></span>

## <a name="open-a-messaging-extension"></a><span data-ttu-id="4f505-147">Abrir uma extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="4f505-147">Open a messaging extension</span></span>

<span data-ttu-id="4f505-148">A caixa de redação e mensagens ou postagens são os principais contextos em que as pessoas usam extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="4f505-148">The compose box and messages or posts are the primary contexts where people use messaging extensions.</span></span>

### <a name="from-the-compose-box"></a><span data-ttu-id="4f505-149">Na caixa de redação</span><span class="sxs-lookup"><span data-stu-id="4f505-149">From the compose box</span></span>

<span data-ttu-id="4f505-150">Depois de adicionado, os usuários podem abrir sua extensão de mensagens selecionando o ícone do aplicativo abaixo da caixa de redação.</span><span class="sxs-lookup"><span data-stu-id="4f505-150">Once added, users can open your messaging extension by selecting your app icon below the compose box.</span></span> <span data-ttu-id="4f505-151">Nesses exemplos, a extensão tem comandos de pesquisa e ação.</span><span class="sxs-lookup"><span data-stu-id="4f505-151">In these examples, the extension has search and action commands.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="4f505-152">Desktop</span><span class="sxs-lookup"><span data-stu-id="4f505-152">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/open-from-compose-box.png" alt-text="Exemplo mostra como abrir uma extensão de mensagens da caixa de redação." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="4f505-154">Mobile</span><span class="sxs-lookup"><span data-stu-id="4f505-154">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-open-from-compose-box.png" alt-text="Exemplo mostra como abrir uma extensão de mensagens da caixa de redação no celular." border="false":::

---

### <a name="from-a-chat-message-or-channel-post"></a><span data-ttu-id="4f505-156">De uma mensagem de chat ou postagem de canal</span><span class="sxs-lookup"><span data-stu-id="4f505-156">From a chat message or channel post</span></span>

Depois de adicionado, os usuários podem selecionar o ícone **Mais** na mensagem de chat ou na postagem do :::image type="icon" source="../../assets/icons/teams-client-more.png"::: canal para encontrar os comandos de ação da extensão. <span data-ttu-id="4f505-158">Sua extensão pode estar listada em **Mais ações** com base no uso.</span><span class="sxs-lookup"><span data-stu-id="4f505-158">Your extension may be listed under **More actions** based on usage.</span></span>

> [!NOTE]
> <span data-ttu-id="4f505-159">O suporte para mais ações de uma mensagem de chat ou postagem de canal não está disponível Microsoft Teams plataforma móvel.</span><span class="sxs-lookup"><span data-stu-id="4f505-159">Support for more actions from a chat message or channel post is not available on Microsoft Teams mobile platform.</span></span> 

#### <a name="chat-message"></a><span data-ttu-id="4f505-160">Mensagem de chat</span><span class="sxs-lookup"><span data-stu-id="4f505-160">Chat message</span></span>

# <a name="desktop"></a>[<span data-ttu-id="4f505-161">Desktop</span><span class="sxs-lookup"><span data-stu-id="4f505-161">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/open-from-chat-message.png" alt-text="Exemplo mostra como abrir uma extensão de mensagens de uma mensagem de chat." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="4f505-163">Mobile</span><span class="sxs-lookup"><span data-stu-id="4f505-163">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-open-from-chat-post.png" alt-text="Exemplo mostra como abrir uma extensão de mensagens de uma postagem de chat no celular." border="false":::

---
':::image type="content" source="../../assets/images/messaging-extension/open-from-channel-post.png" alt-text="Example shows how to open a messaging extension from a channel post on mobile." border="false"::': null
':::image type="content" source="../../assets/images/messaging-extension/mobile-open-from-channel-post.png" alt-text="Example shows how to open a messaging extension from a channel post on mobile." border="false"::': null
---

## <a name="use-a-messaging-extension"></a><span data-ttu-id="4f505-165">Usar uma extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="4f505-165">Use a messaging extension</span></span>

<span data-ttu-id="4f505-166">Os cenários a seguir mostram as principais maneiras pelas quais as pessoas usam extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="4f505-166">The following scenarios show the primary ways people use messaging extensions.</span></span>

### <a name="insert-content-into-a-message"></a><span data-ttu-id="4f505-167">Inserir conteúdo em uma mensagem</span><span class="sxs-lookup"><span data-stu-id="4f505-167">Insert content into a message</span></span>

<span data-ttu-id="4f505-168">**1. Selecione uma extensão de mensagens**.</span><span class="sxs-lookup"><span data-stu-id="4f505-168">**1. Select a messaging extension**.</span></span> <span data-ttu-id="4f505-169">Os usuários podem pesquisar o conteúdo que eles querem compartilhar na caixa de redação.</span><span class="sxs-lookup"><span data-stu-id="4f505-169">Users can search for the content they want to share from the compose box.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="4f505-170">Desktop</span><span class="sxs-lookup"><span data-stu-id="4f505-170">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/insert-content-search.png" alt-text="Exemplo mostra um usuário procurando conteúdo para inserir na caixa de redação." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="4f505-172">Mobile</span><span class="sxs-lookup"><span data-stu-id="4f505-172">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-insert-content-search.png" alt-text="Exemplo mostra um usuário procurando conteúdo para inserir na caixa de redação no celular." border="false":::

---

<span data-ttu-id="4f505-174">**2. Insira conteúdo**.</span><span class="sxs-lookup"><span data-stu-id="4f505-174">**2. Insert content**.</span></span> <span data-ttu-id="4f505-175">Depois de postado, outras pessoas podem responder ou selecionar o conteúdo para ver mais informações em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4f505-175">Once posted, others can reply or select the content to see more information in your app.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="4f505-176">Desktop</span><span class="sxs-lookup"><span data-stu-id="4f505-176">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/insert-content-posted.png" alt-text="Exemplo mostra um usuário postando conteúdo em uma conversa de canal." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="4f505-178">Mobile</span><span class="sxs-lookup"><span data-stu-id="4f505-178">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-insert-content-posted.png" alt-text="Exemplo mostra um usuário postando conteúdo em uma conversa de canal no celular." border="false":::

---

### <a name="take-action-on-a-message"></a><span data-ttu-id="4f505-180">Tomar medidas em uma mensagem</span><span class="sxs-lookup"><span data-stu-id="4f505-180">Take action on a message</span></span>

<span data-ttu-id="4f505-181">**1. Selecione uma extensão de mensagens**.</span><span class="sxs-lookup"><span data-stu-id="4f505-181">**1. Select a messaging extension**.</span></span> <span data-ttu-id="4f505-182">Seu aplicativo pode incluir um ou mais comandos de ação.</span><span class="sxs-lookup"><span data-stu-id="4f505-182">Your app can include one or more action commands.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="4f505-183">Desktop</span><span class="sxs-lookup"><span data-stu-id="4f505-183">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/select-action-command.png" alt-text="Exemplo mostra um usuário selecionando um comando de ação de extensão de mensagens." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="4f505-185">Mobile</span><span class="sxs-lookup"><span data-stu-id="4f505-185">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-select-action-command.png" alt-text="Exemplo mostra um usuário selecionando um comando de ação de extensão de mensagens no celular." border="false":::

---

<span data-ttu-id="4f505-187">**2. Conclua a ação**.</span><span class="sxs-lookup"><span data-stu-id="4f505-187">**2. Complete the action**.</span></span> <span data-ttu-id="4f505-188">Seu aplicativo pode receber e processar qualquer conteúdo ou dados enviados pela ação da mensagem.</span><span class="sxs-lookup"><span data-stu-id="4f505-188">Your app can receive and process any content or data sent by the message action.</span></span> <span data-ttu-id="4f505-189">Isso permite que os usuários permaneçam em suas conversas e, no exemplo a seguir, não se preocupe em inserir informações diretamente em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4f505-189">This allows users to remain in their conversation and, the following example, not worry about entering information directly in your app.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="4f505-190">Desktop</span><span class="sxs-lookup"><span data-stu-id="4f505-190">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/complete-action-command.png" alt-text="Exemplo sobre como agir em uma mensagem." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="4f505-192">Mobile</span><span class="sxs-lookup"><span data-stu-id="4f505-192">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-complete-action-command.png" alt-text="Exemplo de como agir em uma mensagem no celular." border="false":::

---

### <a name="preview-links"></a><span data-ttu-id="4f505-194">Links de visualização</span><span class="sxs-lookup"><span data-stu-id="4f505-194">Preview links</span></span>

<span data-ttu-id="4f505-195">As extensões de mensagens também permitem inserir links ricos de uma URL reconhecida em uma mensagem (esse recurso é chamado [de desatada](../../messaging-extensions/how-to/link-unfurling.md)de link .)</span><span class="sxs-lookup"><span data-stu-id="4f505-195">Messaging extensions also allow you to insert rich links from a recognized URL into a message (this capability is called [link unfurling](../../messaging-extensions/how-to/link-unfurling.md).)</span></span>

<span data-ttu-id="4f505-196">**1. Colar um link reconhecido** na caixa de redação.</span><span class="sxs-lookup"><span data-stu-id="4f505-196">**1. Paste a recognized link** in the compose box.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="4f505-197">Desktop</span><span class="sxs-lookup"><span data-stu-id="4f505-197">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/paste-preview-link.png" alt-text="Exemplo mostra um usuário colar um link na caixa de compostagem." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="4f505-199">Mobile</span><span class="sxs-lookup"><span data-stu-id="4f505-199">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-paste-preview-link.png" alt-text="Exemplo mostra um usuário colar um link na caixa de compostagem no celular." border="false":::

---

<span data-ttu-id="4f505-201">**2. Insira conteúdo**.</span><span class="sxs-lookup"><span data-stu-id="4f505-201">**2. Insert content**.</span></span> <span data-ttu-id="4f505-202">Se seu aplicativo reconhecer a URL na caixa de redação, ele renderizará o link como um cartão que fornece uma visualização rica em conteúdo do conteúdo da Web.</span><span class="sxs-lookup"><span data-stu-id="4f505-202">If your app recognizes the URL in the compose box, it renders the link as a card that provides a content-rich preview of the web content.</span></span> <span data-ttu-id="4f505-203">(Consulte [Diretrizes de design de Cartões Adaptáveis](../../task-modules-and-cards/cards/design-effective-cards.md) para obter mais informações.)</span><span class="sxs-lookup"><span data-stu-id="4f505-203">(See [Adaptive Cards design guidelines](../../task-modules-and-cards/cards/design-effective-cards.md) for more information.)</span></span>

# <a name="desktop"></a>[<span data-ttu-id="4f505-204">Desktop</span><span class="sxs-lookup"><span data-stu-id="4f505-204">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/insert-preview-link.png" alt-text="Exemplo mostra como a URL, já que é reconhecida pelo seu aplicativo, inclui algum conteúdo rico na caixa de redação." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="4f505-206">Mobile</span><span class="sxs-lookup"><span data-stu-id="4f505-206">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-insert-preview-link.png" alt-text="Exemplo mostra como a URL, já que é reconhecida pelo seu aplicativo, inclui algum conteúdo rico na caixa de composição no celular." border="false":::

---

## <a name="manage-a-messaging-extension"></a><span data-ttu-id="4f505-208">Gerenciar uma extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="4f505-208">Manage a messaging extension</span></span>

<span data-ttu-id="4f505-209">Clicando com o botão direito do mouse no ícone, os usuários podem fixar, remover ou configurar sua extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="4f505-209">By right clicking your icon, users can pin, remove, or configure your messaging extension.</span></span>

## <a name="anatomy"></a><span data-ttu-id="4f505-210">Anatomia</span><span class="sxs-lookup"><span data-stu-id="4f505-210">Anatomy</span></span>

### <a name="messaging-extension-in-the-compose-box"></a><span data-ttu-id="4f505-211">Extensão de mensagens na caixa de redação</span><span class="sxs-lookup"><span data-stu-id="4f505-211">Messaging extension in the compose box</span></span>

<span data-ttu-id="4f505-212">O exemplo a seguir é uma extensão de mensagens aberta na caixa de redação.</span><span class="sxs-lookup"><span data-stu-id="4f505-212">The following example is a messaging extension opened from the compose box.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="4f505-213">Desktop</span><span class="sxs-lookup"><span data-stu-id="4f505-213">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/messaging-extension/anatomy-compose.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de uma extensão de mensagens na caixa de redação." border="false":::

|<span data-ttu-id="4f505-215">Contador</span><span class="sxs-lookup"><span data-stu-id="4f505-215">Counter</span></span>|<span data-ttu-id="4f505-216">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f505-216">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="4f505-217">1</span><span class="sxs-lookup"><span data-stu-id="4f505-217">1</span></span>|<span data-ttu-id="4f505-218">**Logotipo do aplicativo**: Ícone de cor do logotipo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4f505-218">**App logo**: Color icon of your app logo.</span></span>|
|<span data-ttu-id="4f505-219">2</span><span class="sxs-lookup"><span data-stu-id="4f505-219">2</span></span>|<span data-ttu-id="4f505-220">**Nome do** aplicativo : Nome completo do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4f505-220">**App name**: Full name of your app.</span></span>|
|<span data-ttu-id="4f505-221">3</span><span class="sxs-lookup"><span data-stu-id="4f505-221">3</span></span>|<span data-ttu-id="4f505-222">**Ícone de menu comandos de ação (opcional)**: abre uma lista de comandos de ação para sua extensão de mensagens (se você especificar algum).</span><span class="sxs-lookup"><span data-stu-id="4f505-222">**Action commands menu icon (optional)**: Opens a list of action commands for your messaging extension (if you specify any).</span></span>
|<span data-ttu-id="4f505-223">4 </span><span class="sxs-lookup"><span data-stu-id="4f505-223">4</span></span>|<span data-ttu-id="4f505-224">**Caixa de** pesquisa : Permite que os usuários encontrem o conteúdo do aplicativo que eles querem inserir.</span><span class="sxs-lookup"><span data-stu-id="4f505-224">**Search box**: Allows users to find app content they want to insert.</span></span>|
|<span data-ttu-id="4f505-225">5 </span><span class="sxs-lookup"><span data-stu-id="4f505-225">5</span></span>|<span data-ttu-id="4f505-226">**Menu Guia (opcional)**: Fornece várias categorias de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="4f505-226">**Tab menu (optional)**: Provides multiple content categories.</span></span>|
|<span data-ttu-id="4f505-227">6 </span><span class="sxs-lookup"><span data-stu-id="4f505-227">6</span></span>|<span data-ttu-id="4f505-228">**Menu comandos de ação (opcional)**: exibe a lista de comandos de ação (se você especificar algum).</span><span class="sxs-lookup"><span data-stu-id="4f505-228">**Action commands menu (optional)**: Displays list of action commands (if you specify any).</span></span>|
|<span data-ttu-id="4f505-229">7 </span><span class="sxs-lookup"><span data-stu-id="4f505-229">7</span></span>|<span data-ttu-id="4f505-230">**Conteúdo do** aplicativo : principalmente para exibir os resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="4f505-230">**App content**: Primarily to display search results.</span></span> <span data-ttu-id="4f505-231">O exemplo aqui está usando o layout da lista (layout de grade é outra opção).</span><span class="sxs-lookup"><span data-stu-id="4f505-231">The example here is using the list layout (grid layout is another option).</span></span>|
|<span data-ttu-id="4f505-232">8 </span><span class="sxs-lookup"><span data-stu-id="4f505-232">8</span></span>|<span data-ttu-id="4f505-233">**Logotipo do aplicativo**: Ícone de contorno do logotipo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4f505-233">**App logo**: Outline icon of your app logo.</span></span>|

# <a name="mobile"></a>[<span data-ttu-id="4f505-234">Mobile</span><span class="sxs-lookup"><span data-stu-id="4f505-234">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/messaging-extension/mobile-anatomy-compose.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de uma extensão de mensagens na caixa de redação no celular." border="false":::

|<span data-ttu-id="4f505-236">Contador</span><span class="sxs-lookup"><span data-stu-id="4f505-236">Counter</span></span>|<span data-ttu-id="4f505-237">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f505-237">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="4f505-238">1</span><span class="sxs-lookup"><span data-stu-id="4f505-238">1</span></span>|<span data-ttu-id="4f505-239">**Nome do** aplicativo : Nome completo do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4f505-239">**App name**: Full name of your app.</span></span>|
|<span data-ttu-id="4f505-240">2</span><span class="sxs-lookup"><span data-stu-id="4f505-240">2</span></span>|<span data-ttu-id="4f505-241">**Ícone de menu comandos de ação (opcional)**: abre uma lista de comandos de ação para sua extensão de mensagens (se você especificar algum).</span><span class="sxs-lookup"><span data-stu-id="4f505-241">**Action commands menu icon (optional)**: Opens a list of action commands for your messaging extension (if you specify any).</span></span>
|<span data-ttu-id="4f505-242">3</span><span class="sxs-lookup"><span data-stu-id="4f505-242">3</span></span>|<span data-ttu-id="4f505-243">**Caixa de** pesquisa : Permite que os usuários encontrem o conteúdo do aplicativo que eles querem inserir.</span><span class="sxs-lookup"><span data-stu-id="4f505-243">**Search box**: Allows users to find app content they want to insert.</span></span>|
|<span data-ttu-id="4f505-244">4 </span><span class="sxs-lookup"><span data-stu-id="4f505-244">4</span></span>|<span data-ttu-id="4f505-245">**Menu Guia (opcional)**: Fornece várias categorias de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="4f505-245">**Tab menu (optional)**: Provides multiple content categories.</span></span>|
|<span data-ttu-id="4f505-246">5 </span><span class="sxs-lookup"><span data-stu-id="4f505-246">5</span></span>|<span data-ttu-id="4f505-247">**Menu comandos de ação (opcional)**: exibe a lista de comandos de ação (se você especificar algum).</span><span class="sxs-lookup"><span data-stu-id="4f505-247">**Action commands menu (optional)**: Displays list of action commands (if you specify any).</span></span>|
|<span data-ttu-id="4f505-248">6 </span><span class="sxs-lookup"><span data-stu-id="4f505-248">6</span></span>|<span data-ttu-id="4f505-249">**Conteúdo do** aplicativo : principalmente para exibir os resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="4f505-249">**App content**: Primarily to display search results.</span></span>|

---

### <a name="messaging-extension-management-menu"></a><span data-ttu-id="4f505-250">Menu de gerenciamento de extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="4f505-250">Messaging extension management menu</span></span>

:::image type="content" source="../../assets/images/messaging-extension/anatomy-management-menu.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de um menu de gerenciamento de extensão de mensagens." border="false":::

|<span data-ttu-id="4f505-252">Contador</span><span class="sxs-lookup"><span data-stu-id="4f505-252">Counter</span></span>|<span data-ttu-id="4f505-253">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f505-253">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="4f505-254">1</span><span class="sxs-lookup"><span data-stu-id="4f505-254">1</span></span>|<span data-ttu-id="4f505-255">**Desempin**: Disponível se o usuário fixou seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4f505-255">**Unpin**: Available if the user has pinned your app.</span></span>|
|<span data-ttu-id="4f505-256">2</span><span class="sxs-lookup"><span data-stu-id="4f505-256">2</span></span>|<span data-ttu-id="4f505-257">**Remover**: remove a extensão de mensagens do canal, chat ou reunião.</span><span class="sxs-lookup"><span data-stu-id="4f505-257">**Remove**: Removes the messaging extension from the channel, chat, or meeting.</span></span>|

## <a name="best-practices"></a><span data-ttu-id="4f505-258">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="4f505-258">Best practices</span></span>

<span data-ttu-id="4f505-259">Use essas recomendações para criar uma experiência de aplicativo de qualidade.</span><span class="sxs-lookup"><span data-stu-id="4f505-259">Use these recommendations to create a quality app experience.</span></span>

### <a name="setup-and-general-usage"></a><span data-ttu-id="4f505-260">Instalação e uso geral</span><span class="sxs-lookup"><span data-stu-id="4f505-260">Setup and general usage</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-do.png" alt-text="Exemplo de configuração e uso geral." border="false":::

#### <a name="do-integrate-with-single-sign-on"></a><span data-ttu-id="4f505-262">Fazer: Integrar com o single-sign on</span><span class="sxs-lookup"><span data-stu-id="4f505-262">Do: Integrate with single-sign on</span></span>

<span data-ttu-id="4f505-263">O SSO torna o processo de login mais fácil, rápido e seguro.</span><span class="sxs-lookup"><span data-stu-id="4f505-263">SSO makes the sign-in process easier, faster, and secure.</span></span> <span data-ttu-id="4f505-264">Além disso, se um usuário já tiver feito login no seu aplicativo pessoal, ele não precisa também entrar novamente para acessar a extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="4f505-264">Also, if a user has already signed in to your personal app, they don’t have to also sign in again to access the messaging extension.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/setup-dont.png" alt-text="Exemplo de integração com o single-sign on." border="false":::

#### <a name="dont-take-users-away-from-the-conversation"></a><span data-ttu-id="4f505-266">Não: tire os usuários da conversa</span><span class="sxs-lookup"><span data-stu-id="4f505-266">Don't: Take users away from the conversation</span></span>

<span data-ttu-id="4f505-267">Extensões de mensagens são atalhos que devem reduzir a alternção de contexto.</span><span class="sxs-lookup"><span data-stu-id="4f505-267">Messaging extensions are shortcuts that are supposed reduce context switching.</span></span> <span data-ttu-id="4f505-268">Sua extensão não deve, por exemplo, direcionar usuários para uma página da Web fora Teams.</span><span class="sxs-lookup"><span data-stu-id="4f505-268">Your extension should not, for example, direct users to a webpage outside Teams.</span></span>

   :::column-end:::
:::row-end:::

#### <a name="do-highlight-your-messaging-extension"></a><span data-ttu-id="4f505-269">Do: Realça sua extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="4f505-269">Do: Highlight your messaging extension</span></span>

<span data-ttu-id="4f505-270">Extensões de mensagens nem sempre são fáceis de encontrar.</span><span class="sxs-lookup"><span data-stu-id="4f505-270">Messaging extensions aren't always easy to find.</span></span> <span data-ttu-id="4f505-271">Inclua capturas de tela de como usá-lo na página de detalhes do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4f505-271">Include screenshots of how to use it in your app details page.</span></span> <span data-ttu-id="4f505-272">Se seu aplicativo também incluir um bot, você poderá incluir a documentação da ajuda de extensão de mensagens em um tour de boas-vindas de bot.</span><span class="sxs-lookup"><span data-stu-id="4f505-272">If your app also includes a bot, you can include messaging extension help documentation in a bot welcome tour.</span></span>

### <a name="templating"></a><span data-ttu-id="4f505-273">Templating</span><span class="sxs-lookup"><span data-stu-id="4f505-273">Templating</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-do.png" alt-text="Exemplo de templating." border="false":::

#### <a name="do-let-teams-handle-some-of-the-design-work-if-possible"></a><span data-ttu-id="4f505-275">Fazer: deixe Teams lidar com alguns dos trabalhos de design, se possível</span><span class="sxs-lookup"><span data-stu-id="4f505-275">Do: Let Teams handle some of the design work if possible</span></span>

<span data-ttu-id="4f505-276">Se fizer sentido para seus casos de uso, considere a criação de uma extensão de mensagens baseada em pesquisa.</span><span class="sxs-lookup"><span data-stu-id="4f505-276">If it makes sense for your use cases, consider creating a search-based messaging extension.</span></span> <span data-ttu-id="4f505-277">Teams renderiza esses tipos de extensões com temas e acessibilidade integrados.</span><span class="sxs-lookup"><span data-stu-id="4f505-277">Teams renders these types of extensions with built-in theming and accessibility.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/templating-dont.png" alt-text="Exemplo sobre como manipular o trabalho de design." border="false":::

#### <a name="dont-embed-your-entire-app-in-a-task-module"></a><span data-ttu-id="4f505-279">Não: incorporar seu aplicativo inteiro em um módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="4f505-279">Don't: Embed your entire app in a task module</span></span>

<span data-ttu-id="4f505-280">Se a extensão de mensagens exigir comandos de ação, mantenha o módulo de tarefas simples e exibe apenas os componentes necessários para concluir a ação.</span><span class="sxs-lookup"><span data-stu-id="4f505-280">If your messaging extension requires action commands, keep the task module simple and display only the components required to complete the action.</span></span>

   :::column-end:::
:::row-end:::

### <a name="theming"></a><span data-ttu-id="4f505-281">Temas</span><span class="sxs-lookup"><span data-stu-id="4f505-281">Theming</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-do.png" alt-text="Exemplo sobre temas." border="false":::

#### <a name="do-take-advantage-of-teams-color-tokens"></a><span data-ttu-id="4f505-283">Do: tire proveito de Teams de cores</span><span class="sxs-lookup"><span data-stu-id="4f505-283">Do: Take advantage of Teams color tokens</span></span>

<span data-ttu-id="4f505-284">Cada Teams tem seu próprio esquema de cores.</span><span class="sxs-lookup"><span data-stu-id="4f505-284">Each Teams theme has its own color scheme.</span></span> <span data-ttu-id="4f505-285">Para lidar com alterações de tema automaticamente, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">tokens de cor (interface do usuário fluente)</a> em seu design.</span><span class="sxs-lookup"><span data-stu-id="4f505-285">To handle theme changes automatically, use <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">color tokens (Fluent UI)</a> in your design.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/theming-dont.png" alt-text="Exemplo em tokens de cores." border="false":::

#### <a name="dont-hard-code-color-values"></a><span data-ttu-id="4f505-287">Não: Valores de cor de código rígidos</span><span class="sxs-lookup"><span data-stu-id="4f505-287">Don't: Hard code color values</span></span>

<span data-ttu-id="4f505-288">Se você não usar tokens Teams cores, seus designs serão menos escalonáveis e levarão mais tempo para gerenciar.</span><span class="sxs-lookup"><span data-stu-id="4f505-288">If you don't use Teams color tokens, your designs will be less scalable and take more time to manage.</span></span>

   :::column-end:::
:::row-end:::

### <a name="actions"></a><span data-ttu-id="4f505-289">Ações</span><span class="sxs-lookup"><span data-stu-id="4f505-289">Actions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-do.png" alt-text="Exemplo de ações." border="false":::

#### <a name="do-include-action-commands-that-make-sense-in-context"></a><span data-ttu-id="4f505-291">Do: Incluir comandos de ação que fazem sentido no contexto</span><span class="sxs-lookup"><span data-stu-id="4f505-291">Do: Include action commands that make sense in context</span></span>

<span data-ttu-id="4f505-292">As ações de mensagem devem estar relacionadas ao que um usuário está olhando.</span><span class="sxs-lookup"><span data-stu-id="4f505-292">Message actions should relate to what a user is looking at.</span></span> <span data-ttu-id="4f505-293">Por exemplo, forneça aos usuários um atalho para criar um problema ou item de trabalho usando o texto na postagem de alguém.</span><span class="sxs-lookup"><span data-stu-id="4f505-293">For example, provide users a shortcut for creating an issue or work item using the text in someone’s post.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/messaging-extension/action-commands-dont.png" alt-text="Exemplo em comandos de ação." border="false":::

#### <a name="dont-include-actions-commands-that-arent-contextual"></a><span data-ttu-id="4f505-295">Não: inclua comandos de ações que não sejam contextuais</span><span class="sxs-lookup"><span data-stu-id="4f505-295">Don't: Include actions commands that aren't contextual</span></span>

<span data-ttu-id="4f505-296">Uma ação de mensagem para **Exibir seu painel** provavelmente pareceria desconectada da maioria das conversas.</span><span class="sxs-lookup"><span data-stu-id="4f505-296">A message action to **View your dashboard** would probably seem disconnected from most conversations.</span></span>

   :::column-end:::
:::row-end:::

### <a name="searches"></a><span data-ttu-id="4f505-297">Pesquisas</span><span class="sxs-lookup"><span data-stu-id="4f505-297">Searches</span></span>

#### <a name="do-show-search-results-while-typing"></a><span data-ttu-id="4f505-298">Do: Mostrar resultados da pesquisa durante a digitação</span><span class="sxs-lookup"><span data-stu-id="4f505-298">Do: Show search results while typing</span></span>

<span data-ttu-id="4f505-299">Forneça resultados de pesquisa sugeridos enquanto os usuários digitam.</span><span class="sxs-lookup"><span data-stu-id="4f505-299">Provide suggested search results while users type.</span></span> <span data-ttu-id="4f505-300">Eles podem encontrar o conteúdo de que precisam mais rapidamente com a quantidade mínima de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4f505-300">They may find the content they need faster with minimal amount of characters.</span></span>

#### <a name="dont-require-users-to-submit-a-query"></a><span data-ttu-id="4f505-301">Não: Exigir que os usuários enviem uma consulta</span><span class="sxs-lookup"><span data-stu-id="4f505-301">Don't: Require users to submit a query</span></span>

<span data-ttu-id="4f505-302">Você pode fazer com que os usuários pressionem uma tecla ou selecionem um botão para enviar consultas ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4f505-302">You can make users press a key or select a button to send queries to your app.</span></span> <span data-ttu-id="4f505-303">Embora isso possa ser mais fácil no seu serviço de serviços de aplicativo, as pessoas podem estar confusas de que não estão vendo resultados de pesquisa em tempo real à medida que digitam.</span><span class="sxs-lookup"><span data-stu-id="4f505-303">While that may be easier on your app services service, people may be confused that they're not seeing real-time search results as they type.</span></span>

#### <a name="do-consider-zero-term-queries"></a><span data-ttu-id="4f505-304">Do: considere consultas de termo zero</span><span class="sxs-lookup"><span data-stu-id="4f505-304">Do: Consider zero-term queries</span></span>

<span data-ttu-id="4f505-305">Por exemplo, antes de um usuário escrever qualquer coisa na caixa de pesquisa, exempli-lo pela última vez em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4f505-305">For example, before a user writes anything in the search box, display what they last viewed on your app.</span></span> <span data-ttu-id="4f505-306">É possível que eles queiram inserir esse conteúdo em suas conversas.</span><span class="sxs-lookup"><span data-stu-id="4f505-306">It's possible that they want to insert that content into their conversation.</span></span>
