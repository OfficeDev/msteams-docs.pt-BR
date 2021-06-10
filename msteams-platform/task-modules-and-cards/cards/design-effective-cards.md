---
title: Projetando cartões adaptáveis para seu aplicativo
description: Saiba como projetar Cartões Adaptáveis para Teams e obter o kit Microsoft Teams interface do usuário.
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: b4d5f43268c7bd5afecb56d26eb0d49ed6c9002b
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2021
ms.locfileid: "52630255"
---
# <a name="designing-adaptive-cards-for-your-microsoft-teams-app"></a><span data-ttu-id="331b2-103">Projetando cartões adaptáveis para seu Microsoft Teams app</span><span class="sxs-lookup"><span data-stu-id="331b2-103">Designing Adaptive Cards for your Microsoft Teams app</span></span>

<span data-ttu-id="331b2-104">Um Cartão Adaptável contém um corpo de forma livre de elementos de cartão e um conjunto opcional de ações.</span><span class="sxs-lookup"><span data-stu-id="331b2-104">An Adaptive Card contains a freeform body of card elements and optional set of actions.</span></span> <span data-ttu-id="331b2-105">Cartões adaptáveis são trechos acionáveis de conteúdo que você pode adicionar a uma conversa por meio de um bot ou extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="331b2-105">Adaptive Cards are actionable snippets of content that you can add to a conversation through a bot or messaging extension.</span></span> <span data-ttu-id="331b2-106">Usando texto, gráficos e botões, essas placas fornecem uma comunicação rica para o público-alvo.</span><span class="sxs-lookup"><span data-stu-id="331b2-106">Using text, graphics, and buttons, these cards provide rich communication to your audience.</span></span>

<span data-ttu-id="331b2-107">A estrutura cartão adaptável é usada em muitos produtos Microsoft, incluindo Teams.</span><span class="sxs-lookup"><span data-stu-id="331b2-107">The Adaptive Card framework is used across many Microsoft products, including Teams.</span></span> <span data-ttu-id="331b2-108">Você pode enviar cartões dentro de mensagens para os usuários por meio de bots ou extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="331b2-108">You can send cards inside messages to users via bots or messaging extensions.</span></span> <span data-ttu-id="331b2-109">Os usuários também podem tomar ações em cartões quando presentes.</span><span class="sxs-lookup"><span data-stu-id="331b2-109">Users can also take actions on cards when present.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/adaptive-card-overview.png" alt-text="Exemplo de visão geral de um Cartão Adaptável." border="false":::

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="331b2-111">Kit de Interface do Usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="331b2-111">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="331b2-112">Você pode encontrar diretrizes de design mais abrangentes para Cartões Adaptáveis no Teams, incluindo elementos que você pode obter e modificar conforme necessário, no kit de interface do usuário Microsoft Teams UI.</span><span class="sxs-lookup"><span data-stu-id="331b2-112">You can find more comprehensive design guidelines for Adaptive Cards in Teams, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span> <span data-ttu-id="331b2-113">O kit de interface do usuário também aborda tópicos essenciais, como temas, acessibilidade e tamanho responsivo.</span><span class="sxs-lookup"><span data-stu-id="331b2-113">The UI kit also covers essential topics such as theming, accessibility, and responsive sizing.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="331b2-114">Obtenha o Kit de Interface do Usuário do Microsoft Teams (Figma)</span><span class="sxs-lookup"><span data-stu-id="331b2-114">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="adaptive-cards-designer"></a><span data-ttu-id="331b2-115">Designer de Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="331b2-115">Adaptive Cards designer</span></span>

<span data-ttu-id="331b2-116">Você também pode começar a projetar seus Cartões Adaptáveis diretamente no navegador.</span><span class="sxs-lookup"><span data-stu-id="331b2-116">You also can start designing your Adaptive Cards directly in the browser.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="331b2-117">Experimente o designer de Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="331b2-117">Try the Adaptive Cards designer</span></span>](https://adaptivecards.io/designer/)

## <a name="types-of-adaptive-cards"></a><span data-ttu-id="331b2-118">Tipos de cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="331b2-118">Types of Adaptive Cards</span></span>

### <a name="hero"></a><span data-ttu-id="331b2-119">Destaque</span><span class="sxs-lookup"><span data-stu-id="331b2-119">Hero</span></span>

<span data-ttu-id="331b2-120">Nosso maior cartão.</span><span class="sxs-lookup"><span data-stu-id="331b2-120">Our largest card.</span></span> <span data-ttu-id="331b2-121">Use para compartilhar artigos ou cenários em que uma imagem conta a maior parte da história.</span><span class="sxs-lookup"><span data-stu-id="331b2-121">Use for sharing articles or scenarios where an image tells most of the story.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="331b2-122">Desktop</span><span class="sxs-lookup"><span data-stu-id="331b2-122">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/hero-card.png" alt-text="Exemplo mostra um cartão de herói do Cartão Adaptável." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="331b2-124">Mobile</span><span class="sxs-lookup"><span data-stu-id="331b2-124">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-hero-card.png" alt-text="Exemplo mostra um cartão de herói do Cartão Adaptável no celular." border="false":::

---

### <a name="thumbnail"></a><span data-ttu-id="331b2-126">Miniatura</span><span class="sxs-lookup"><span data-stu-id="331b2-126">Thumbnail</span></span>

<span data-ttu-id="331b2-127">Use para enviar uma mensagem simples a actionable.</span><span class="sxs-lookup"><span data-stu-id="331b2-127">Use for sending a simple actionable message.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="331b2-128">Desktop</span><span class="sxs-lookup"><span data-stu-id="331b2-128">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/thumbnail-card.png" alt-text="Exemplo mostra um cartão de miniatura do Cartão Adaptável." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="331b2-130">Mobile</span><span class="sxs-lookup"><span data-stu-id="331b2-130">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-thumbnail-card.png" alt-text="Exemplo mostra um cartão de miniatura do Cartão Adaptável no celular." border="false":::

---

### <a name="list"></a><span data-ttu-id="331b2-132">List</span><span class="sxs-lookup"><span data-stu-id="331b2-132">List</span></span>

<span data-ttu-id="331b2-133">Use em cenários em que você deseja que o usuário escolha um item de uma lista, mas os itens não precisam de muita explicação.</span><span class="sxs-lookup"><span data-stu-id="331b2-133">Use in scenarios where you want the user to pick an item from a list, but the items don’t need a lot of explanation.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="331b2-134">Desktop</span><span class="sxs-lookup"><span data-stu-id="331b2-134">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/list-card.png" alt-text="Exemplo mostra um cartão de lista cartão adaptável." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="331b2-136">Mobile</span><span class="sxs-lookup"><span data-stu-id="331b2-136">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-list-card.png" alt-text="Exemplo mostra um cartão de lista cartão adaptável no celular." border="false":::

---
Use for news digests and round-up posts. Note: We recommend the thumbnail card for a single update or news item.
':::image type="content" source="../../assets/images/adaptive-cards/digest-card.png" alt-text="Example shows an Adaptive Card digest card." border="false"::': null
':::image type="content" source="../../assets/images/adaptive-cards/mobile-digest-card.png" alt-text="Example shows an Adaptive Card digest card on mobile." border="false"::': null
---

### <a name="media"></a><span data-ttu-id="331b2-138">Mídia</span><span class="sxs-lookup"><span data-stu-id="331b2-138">Media</span></span>

<span data-ttu-id="331b2-139">Use quando quiser combinar texto e mídia, como áudio ou vídeo.</span><span class="sxs-lookup"><span data-stu-id="331b2-139">Use when you want to combine text and media, like audio or video.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="331b2-140">Desktop</span><span class="sxs-lookup"><span data-stu-id="331b2-140">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/media-card.png" alt-text="Exemplo mostra um cartão de mídia cartão adaptável." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="331b2-142">Mobile</span><span class="sxs-lookup"><span data-stu-id="331b2-142">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-media-card.png" alt-text="Exemplo mostra um cartão de mídia cartão adaptável no celular." border="false":::

---

### <a name="people"></a><span data-ttu-id="331b2-144">Pessoas</span><span class="sxs-lookup"><span data-stu-id="331b2-144">People</span></span>

<span data-ttu-id="331b2-145">Melhor usado quando você transmite com eficiência quem está envolvido com uma tarefa.</span><span class="sxs-lookup"><span data-stu-id="331b2-145">Best used when you to efficiently convey who's involved with a task.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="331b2-146">Desktop</span><span class="sxs-lookup"><span data-stu-id="331b2-146">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/people-card.png" alt-text="Exemplo mostra um cartão de pessoas do Cartão Adaptável." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="331b2-148">Mobile</span><span class="sxs-lookup"><span data-stu-id="331b2-148">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-people-card.png" alt-text="Exemplo mostra um cartão de pessoas do Cartão Adaptável no celular." border="false":::

---

### <a name="request-ticket"></a><span data-ttu-id="331b2-150">Tíquete de solicitação</span><span class="sxs-lookup"><span data-stu-id="331b2-150">Request ticket</span></span>

<span data-ttu-id="331b2-151">Use para obter entradas rápidas de um usuário para criar automaticamente uma tarefa ou tíquete.</span><span class="sxs-lookup"><span data-stu-id="331b2-151">Use to get quick inputs from a user to automatically create a task or ticket.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="331b2-152">Desktop</span><span class="sxs-lookup"><span data-stu-id="331b2-152">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/request-ticket-card.png" alt-text="Exemplo mostra um cartão de tíquete de solicitação de Cartão Adaptável." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="331b2-154">Mobile</span><span class="sxs-lookup"><span data-stu-id="331b2-154">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-request-ticket-card.png" alt-text="Exemplo mostra um cartão de tíquete de solicitação de Cartão Adaptável no celular." border="false":::

---

### <a name="image-set"></a><span data-ttu-id="331b2-156">Conjunto de imagens</span><span class="sxs-lookup"><span data-stu-id="331b2-156">Image set</span></span>

<span data-ttu-id="331b2-157">Use para enviar várias miniaturas de imagem.</span><span class="sxs-lookup"><span data-stu-id="331b2-157">Use to send multiple image thumbnails.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="331b2-158">Desktop</span><span class="sxs-lookup"><span data-stu-id="331b2-158">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/image-set-card.png" alt-text="Exemplo mostra um cartão de conjunto de imagens do Cartão Adaptável." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="331b2-160">Mobile</span><span class="sxs-lookup"><span data-stu-id="331b2-160">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-image-set-card.png" alt-text="Exemplo mostra um cartão de conjunto de imagens do Cartão Adaptável no celular." border="false":::

---

### <a name="action-set"></a><span data-ttu-id="331b2-162">Conjunto de ações</span><span class="sxs-lookup"><span data-stu-id="331b2-162">Action set</span></span>

<span data-ttu-id="331b2-163">Use quando quiser que o usuário selecione um botão e, em seguida, reúna a entrada do usuário de adição do mesmo cartão.</span><span class="sxs-lookup"><span data-stu-id="331b2-163">Use when you want to the user to select a button, then gather addition user input from the same card.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="331b2-164">Desktop</span><span class="sxs-lookup"><span data-stu-id="331b2-164">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/action-set-card.png" alt-text="Exemplo mostra um cartão de conjunto de ações cartão adaptável." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="331b2-166">Mobile</span><span class="sxs-lookup"><span data-stu-id="331b2-166">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-action-set-card.png" alt-text="Exemplo mostra um cartão de conjunto de ações do Cartão Adaptável no celular." border="false":::

---

### <a name="choice-set"></a><span data-ttu-id="331b2-168">Conjunto de opções</span><span class="sxs-lookup"><span data-stu-id="331b2-168">Choice set</span></span>

<span data-ttu-id="331b2-169">Use para coletar várias entradas do usuário.</span><span class="sxs-lookup"><span data-stu-id="331b2-169">Use to gather multiple inputs from the user.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="331b2-170">Desktop</span><span class="sxs-lookup"><span data-stu-id="331b2-170">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/choice-set-card.png" alt-text="Exemplo mostra um cartão de conjunto de opções do Cartão Adaptável." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="331b2-172">Mobile</span><span class="sxs-lookup"><span data-stu-id="331b2-172">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-choice-set-card.png" alt-text="Exemplo mostra um cartão de conjunto de opções de Cartão Adaptável no celular." border="false":::

---

## <a name="anatomy"></a><span data-ttu-id="331b2-174">Anatomia</span><span class="sxs-lookup"><span data-stu-id="331b2-174">Anatomy</span></span>

<span data-ttu-id="331b2-175">Cartões adaptáveis têm muita flexibilidade.</span><span class="sxs-lookup"><span data-stu-id="331b2-175">Adaptive Cards have a lot of flexibility.</span></span> <span data-ttu-id="331b2-176">No mínimo, sugerimos incluir os seguintes componentes em cada cartão.</span><span class="sxs-lookup"><span data-stu-id="331b2-176">But at minimum, we strongly suggest including the following components in every card.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="331b2-177">Desktop</span><span class="sxs-lookup"><span data-stu-id="331b2-177">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/anatomy.png" alt-text="EExample mostra a anatomia do Cartão Adaptável." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="331b2-179">Mobile</span><span class="sxs-lookup"><span data-stu-id="331b2-179">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-anatomy.png" alt-text="Exemplo mostra a anatomia do Cartão Adaptável no celular." border="false":::

---

|<span data-ttu-id="331b2-181">Contador</span><span class="sxs-lookup"><span data-stu-id="331b2-181">Counter</span></span>|<span data-ttu-id="331b2-182">Descrição</span><span class="sxs-lookup"><span data-stu-id="331b2-182">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="331b2-183">A</span><span class="sxs-lookup"><span data-stu-id="331b2-183">A</span></span>|<span data-ttu-id="331b2-184">**Header**: tornar seus headers claros e concisos.</span><span class="sxs-lookup"><span data-stu-id="331b2-184">**Header**: Make your headers clear and concise.</span></span>|
|<span data-ttu-id="331b2-185">B</span><span class="sxs-lookup"><span data-stu-id="331b2-185">B</span></span>|<span data-ttu-id="331b2-186">**Cópia do** corpo : transmita detalhes que são muito longos ou não importantes o suficiente para incluir no header.</span><span class="sxs-lookup"><span data-stu-id="331b2-186">**Body copy**: Convey details that are either too long or not important enough to include in the header.</span></span>|
|<span data-ttu-id="331b2-187">C</span><span class="sxs-lookup"><span data-stu-id="331b2-187">C</span></span>|<span data-ttu-id="331b2-188">**Ações primárias**: Como prática prática, inclua ações primárias de 1 a 3.</span><span class="sxs-lookup"><span data-stu-id="331b2-188">**Primary actions**: As a best practice, include 1-3 primary actions.</span></span> <span data-ttu-id="331b2-189">Você pode ter até seis.</span><span class="sxs-lookup"><span data-stu-id="331b2-189">You can have up to six.</span></span>|

## <a name="best-practices"></a><span data-ttu-id="331b2-190">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="331b2-190">Best practices</span></span>

<span data-ttu-id="331b2-191">Use essas recomendações para criar uma experiência de aplicativo de qualidade.</span><span class="sxs-lookup"><span data-stu-id="331b2-191">Use these recommendations to create a quality app experience.</span></span>

### <a name="primary-and-secondary-actions"></a><span data-ttu-id="331b2-192">Ações primárias e secundárias</span><span class="sxs-lookup"><span data-stu-id="331b2-192">Primary and secondary actions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-do.png" alt-text="Práticas práticas sobre como você deve incluir apenas um pequeno conjunto de ações em um Cartão Adaptável." border="false":::

#### <a name="do-use-up-to-six-primary-actions"></a><span data-ttu-id="331b2-194">Fazer: usar até seis ações primárias</span><span class="sxs-lookup"><span data-stu-id="331b2-194">Do: Use up to six primary actions</span></span>

<span data-ttu-id="331b2-195">Embora os Cartões Adaptáveis possam dar suporte a seis ações principais, a maioria dos cartões não precisa disso.</span><span class="sxs-lookup"><span data-stu-id="331b2-195">While Adaptive Cards can support six primary actions, most cards don’t need that.</span></span> <span data-ttu-id="331b2-196">As ações devem ser claras, concisas e diretas.</span><span class="sxs-lookup"><span data-stu-id="331b2-196">Actions should be clear, concise, and straight forward.</span></span> <span data-ttu-id="331b2-197">Menos é mais.</span><span class="sxs-lookup"><span data-stu-id="331b2-197">Less is more.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-dont.png" alt-text="Práticas práticas sobre como não sobrecarregar os usuários com muitas ações em um Cartão Adaptável." border="false":::

#### <a name="dont-use-more-than-six-primary-actions"></a><span data-ttu-id="331b2-199">Não: use mais de seis ações primárias</span><span class="sxs-lookup"><span data-stu-id="331b2-199">Don't: Use more than six primary actions</span></span>

<span data-ttu-id="331b2-200">Cartões adaptáveis devem apresentar conteúdo rápido e ativos.</span><span class="sxs-lookup"><span data-stu-id="331b2-200">Adaptive Cards should present quick, actionable content.</span></span> <span data-ttu-id="331b2-201">Muitas ações podem sobrecarregar um usuário.</span><span class="sxs-lookup"><span data-stu-id="331b2-201">Too many actions can overwhelm a user.</span></span>

   :::column-end:::
:::row-end:::

### <a name="frequency"></a><span data-ttu-id="331b2-202">Frequência</span><span class="sxs-lookup"><span data-stu-id="331b2-202">Frequency</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/frequency-do.png" alt-text="Prática prática sobre a frequência do Cartão Adaptável." border="false":::

#### <a name="do-be-concise"></a><span data-ttu-id="331b2-204">Do: Ser conciso</span><span class="sxs-lookup"><span data-stu-id="331b2-204">Do: Be concise</span></span>

<span data-ttu-id="331b2-205">É fácil enviar vários cartões para uma conversa, mas quando os cartões ficam fora de exibição, eles se tornam menos úteis.</span><span class="sxs-lookup"><span data-stu-id="331b2-205">It's easy to send multiple cards into a conversation, but once cards scroll out of view, they become less useful.</span></span> <span data-ttu-id="331b2-206">Tente limitar-se ao essencial.</span><span class="sxs-lookup"><span data-stu-id="331b2-206">Try to limit yourself to the essentials.</span></span> <span data-ttu-id="331b2-207">Isso é especialmente verdadeiro em um canal onde os usuários têm menos tolerância para o que eles percebem como "ruído".</span><span class="sxs-lookup"><span data-stu-id="331b2-207">This is especially true in a channel where users have less tolerance for what they perceive as "noise".</span></span>
