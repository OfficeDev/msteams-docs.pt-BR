---
title: Projetando Cartões Adaptáveis para seu aplicativo
description: Aprenda a projetar Cartões Adaptáveis para o Teams e obtenha o Kit de IU do Microsoft Teams.
localization_priority: Priority
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 8e56928da44e22006feb59715c8bdbf821ec4c42
ms.sourcegitcommit: 99b1f151e4e36a86c6a5d2ccbde01bf45b61f526
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/21/2021
ms.locfileid: "53037653"
---
# <a name="designing-adaptive-cards-for-your-microsoft-teams-app"></a><span data-ttu-id="2fd2a-103">Projetando Cartões Adaptáveis para seu aplicativo Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="2fd2a-103">Designing Adaptive Cards for your Microsoft Teams app</span></span>

<span data-ttu-id="2fd2a-104">Um Cartão Adaptável contém um corpo de elementos de cartão de forma livre e um conjunto opcional de ações.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-104">An Adaptive Card contains a freeform body of card elements and optional set of actions.</span></span> <span data-ttu-id="2fd2a-105">Cartões Adaptáveis são fragmentos de conteúdo acionáveis que você pode adicionar a uma conversa por meio de um bot ou extensão de mensagem.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-105">Adaptive Cards are actionable snippets of content that you can add to a conversation through a bot or messaging extension.</span></span> <span data-ttu-id="2fd2a-106">Usando texto, gráficos e botões, esses cartões fornecem uma comunicação rica para seu público-alvo.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-106">Using text, graphics, and buttons, these cards provide rich communication to your audience.</span></span>

<span data-ttu-id="2fd2a-107">A estrutura de Cartão Adaptável é usada em muitos produtos da Microsoft, incluindo o Teams.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-107">The Adaptive Card framework is used across many Microsoft products, including Teams.</span></span> <span data-ttu-id="2fd2a-108">Você pode enviar cartões dentro de mensagens para usuários por meio de bots ou extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-108">You can send cards inside messages to users via bots or messaging extensions.</span></span> <span data-ttu-id="2fd2a-109">Os usuários também podem realizar ações em cartões quando presentes.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-109">Users can also take actions on cards when present.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/adaptive-card-overview.png" alt-text="Exemplo de visão geral de um Cartão Adaptável." border="false":::

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="2fd2a-111">Kit de IU do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="2fd2a-111">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="2fd2a-112">Você pode encontrar diretrizes de design mais abrangentes para Cartões Adaptáveis no Teams, incluindo elementos que você pode pegar e modificar conforme necessário, no Kit de IU do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-112">You can find more comprehensive design guidelines for Adaptive Cards in Teams, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span> <span data-ttu-id="2fd2a-113">O kit de IU também cobre tópicos essenciais, como temas, acessibilidade e dimensionamento dinâmico.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-113">The UI kit also covers essential topics such as theming, accessibility, and responsive sizing.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2fd2a-114">Obtenha o Kit de IU do Microsoft Teams (Figma)</span><span class="sxs-lookup"><span data-stu-id="2fd2a-114">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="adaptive-cards-designer"></a><span data-ttu-id="2fd2a-115">Designer de cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="2fd2a-115">Adaptive Cards designer</span></span>

<span data-ttu-id="2fd2a-116">Você também pode começar a projetar seus Cartões Adaptáveis diretamente no navegador.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-116">You also can start designing your Adaptive Cards directly in the browser.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2fd2a-117">Experimente o designer de cartões adaptáveis </span><span class="sxs-lookup"><span data-stu-id="2fd2a-117">Try the Adaptive Cards designer</span></span>](https://adaptivecards.io/designer/)

## <a name="types-of-adaptive-cards"></a><span data-ttu-id="2fd2a-118">Tipos de Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="2fd2a-118">Types of Adaptive Cards</span></span>

### <a name="hero"></a><span data-ttu-id="2fd2a-119">Destaque</span><span class="sxs-lookup"><span data-stu-id="2fd2a-119">Hero</span></span>

<span data-ttu-id="2fd2a-120">Nosso maior cartão.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-120">Our largest card.</span></span> <span data-ttu-id="2fd2a-121">Use para compartilhar artigos ou cenários em que uma imagem conta a maior parte da história.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-121">Use for sharing articles or scenarios where an image tells most of the story.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="2fd2a-122">Desktop</span><span class="sxs-lookup"><span data-stu-id="2fd2a-122">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/hero-card.png" alt-text="O exemplo mostra um cartão de destaque do Cartão Adaptável." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="2fd2a-124">Dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="2fd2a-124">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-hero-card.png" alt-text="O exemplo mostra um cartão de destaque do Cartão Adaptável no dispositivo móvel." border="false":::

---

### <a name="thumbnail"></a><span data-ttu-id="2fd2a-126">Miniatura</span><span class="sxs-lookup"><span data-stu-id="2fd2a-126">Thumbnail</span></span>

<span data-ttu-id="2fd2a-127">Use para enviar uma mensagem acionável simples.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-127">Use for sending a simple actionable message.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="2fd2a-128">Desktop</span><span class="sxs-lookup"><span data-stu-id="2fd2a-128">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/thumbnail-card.png" alt-text="O exemplo mostra um cartão em miniatura do Cartão Adaptável." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="2fd2a-130">Dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="2fd2a-130">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-thumbnail-card.png" alt-text="O exemplo mostra um cartão em miniatura do Cartão Adaptável no dispositivo móvel." border="false":::

---

### <a name="list"></a><span data-ttu-id="2fd2a-132">List</span><span class="sxs-lookup"><span data-stu-id="2fd2a-132">List</span></span>

<span data-ttu-id="2fd2a-133">Use em cenários em que você deseja que o usuário escolha um item de uma lista, mas os itens não precisam de muitas explicações.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-133">Use in scenarios where you want the user to pick an item from a list, but the items don’t need a lot of explanation.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="2fd2a-134">Desktop</span><span class="sxs-lookup"><span data-stu-id="2fd2a-134">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/list-card.png" alt-text="O exemplo mostra um cartão de lista do Cartão Adaptável." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="2fd2a-136">Dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="2fd2a-136">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-list-card.png" alt-text="O exemplo mostra um cartão de lista do Cartão Adaptável no dispositivo móvel." border="false":::

---
Use for news digests and round-up posts. Note: We recommend the thumbnail card for a single update or news item.
':::image type="content" source="../../assets/images/adaptive-cards/digest-card.png" alt-text="Example shows an Adaptive Card digest card." border="false"::': null
':::image type="content" source="../../assets/images/adaptive-cards/mobile-digest-card.png" alt-text="Example shows an Adaptive Card digest card on mobile." border="false"::': null
---

### <a name="media"></a><span data-ttu-id="2fd2a-138">Mídia</span><span class="sxs-lookup"><span data-stu-id="2fd2a-138">Media</span></span>

<span data-ttu-id="2fd2a-139">Use quando quiser combinar texto e mídia, como áudio ou vídeo.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-139">Use when you want to combine text and media, like audio or video.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="2fd2a-140">Desktop</span><span class="sxs-lookup"><span data-stu-id="2fd2a-140">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/media-card.png" alt-text="O exemplo mostra um cartão de mídia do Cartão Adaptável." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="2fd2a-142">Dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="2fd2a-142">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-media-card.png" alt-text="O exemplo mostra um cartão de mídia do Cartão Adaptável no dispositivo móvel." border="false":::

---

### <a name="people"></a><span data-ttu-id="2fd2a-144">Pessoas</span><span class="sxs-lookup"><span data-stu-id="2fd2a-144">People</span></span>

<span data-ttu-id="2fd2a-145">Melhor usado para transmitir com eficiência quem está envolvido em uma tarefa.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-145">Best used when you to efficiently convey who's involved with a task.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="2fd2a-146">Desktop</span><span class="sxs-lookup"><span data-stu-id="2fd2a-146">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/people-card.png" alt-text="O exemplo mostra um cartão de pessoas do Cartão Adaptável." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="2fd2a-148">Dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="2fd2a-148">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-people-card.png" alt-text="O exemplo mostra um cartão de pessoas do Cartão Adaptável no dispositivo móvel." border="false":::

---

### <a name="request-ticket"></a><span data-ttu-id="2fd2a-150">Solicitar ingresso</span><span class="sxs-lookup"><span data-stu-id="2fd2a-150">Request ticket</span></span>

<span data-ttu-id="2fd2a-151">Use para obter entradas rápidas de um usuário para criar automaticamente uma tarefa ou tíquete.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-151">Use to get quick inputs from a user to automatically create a task or ticket.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="2fd2a-152">Desktop</span><span class="sxs-lookup"><span data-stu-id="2fd2a-152">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/request-ticket-card.png" alt-text="O exemplo mostra um cartão de tíquete de solicitação do Cartão Adaptável." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="2fd2a-154">Dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="2fd2a-154">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-request-ticket-card.png" alt-text="O exemplo mostra um cartão de tíquete de solicitação do Cartão Adaptável no dispositivo móvel." border="false":::

---

### <a name="image-set"></a><span data-ttu-id="2fd2a-156">Conjunto de imagens</span><span class="sxs-lookup"><span data-stu-id="2fd2a-156">Image set</span></span>

<span data-ttu-id="2fd2a-157">Use para enviar várias miniaturas de imagens.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-157">Use to send multiple image thumbnails.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="2fd2a-158">Desktop</span><span class="sxs-lookup"><span data-stu-id="2fd2a-158">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/image-set-card.png" alt-text="O exemplo mostra um cartão de conjunto de imagens do Cartão Adaptável." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="2fd2a-160">Dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="2fd2a-160">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-image-set-card.png" alt-text="O exemplo mostra um cartão de conjunto de imagens do Cartão Adaptável no dispositivo móvel." border="false":::

---

### <a name="action-set"></a><span data-ttu-id="2fd2a-162">Conjunto de ações</span><span class="sxs-lookup"><span data-stu-id="2fd2a-162">Action set</span></span>

<span data-ttu-id="2fd2a-163">Use quando quiser que o usuário selecione um botão e, em seguida, reúna a entrada adicional do usuário do mesmo cartão.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-163">Use when you want to the user to select a button, then gather addition user input from the same card.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="2fd2a-164">Desktop</span><span class="sxs-lookup"><span data-stu-id="2fd2a-164">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/action-set-card.png" alt-text="O exemplo mostra um cartão de conjunto de ações do Cartão Adaptável." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="2fd2a-166">Dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="2fd2a-166">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-action-set-card.png" alt-text="O exemplo mostra um cartão de conjunto de ações do Cartão Adaptável no dispositivo móvel." border="false":::

---

### <a name="choice-set"></a><span data-ttu-id="2fd2a-168">Conjunto de opções</span><span class="sxs-lookup"><span data-stu-id="2fd2a-168">Choice set</span></span>

<span data-ttu-id="2fd2a-169">Use para reunir várias entradas do usuário.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-169">Use to gather multiple inputs from the user.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="2fd2a-170">Desktop</span><span class="sxs-lookup"><span data-stu-id="2fd2a-170">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/choice-set-card.png" alt-text="O exemplo mostra um cartão de conjunto de opções do Cartão Adaptável." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="2fd2a-172">Dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="2fd2a-172">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-choice-set-card.png" alt-text="O exemplo mostra um cartão de conjunto de opções do Cartão Adaptável no dispositivo móvel." border="false":::

---

## <a name="anatomy"></a><span data-ttu-id="2fd2a-174">Anatomia</span><span class="sxs-lookup"><span data-stu-id="2fd2a-174">Anatomy</span></span>

<span data-ttu-id="2fd2a-175">Os Cartões Adaptáveis têm muita flexibilidade.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-175">Adaptive Cards have a lot of flexibility.</span></span> <span data-ttu-id="2fd2a-176">Mas, no mínimo, sugerimos fortemente incluir os seguintes componentes em cada cartão.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-176">But at minimum, we strongly suggest including the following components in every card.</span></span>

# <a name="desktop"></a>[<span data-ttu-id="2fd2a-177">Desktop</span><span class="sxs-lookup"><span data-stu-id="2fd2a-177">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/anatomy.png" alt-text="O exemplo mostra a anatomia do Cartão Adaptável." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="2fd2a-179">Dispositivo móvel</span><span class="sxs-lookup"><span data-stu-id="2fd2a-179">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-anatomy.png" alt-text="O exemplo mostra a anatomia do Cartão Adaptável no dispositivo móvel." border="false":::

---

|<span data-ttu-id="2fd2a-181">Contador</span><span class="sxs-lookup"><span data-stu-id="2fd2a-181">Counter</span></span>|<span data-ttu-id="2fd2a-182">Descrição</span><span class="sxs-lookup"><span data-stu-id="2fd2a-182">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="2fd2a-183">A</span><span class="sxs-lookup"><span data-stu-id="2fd2a-183">A</span></span>|<span data-ttu-id="2fd2a-184">**Cabeçalho**: Deixe seus cabeçalhos claros e concisos.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-184">**Header**: Make your headers clear and concise.</span></span>|
|<span data-ttu-id="2fd2a-185">B</span><span class="sxs-lookup"><span data-stu-id="2fd2a-185">B</span></span>|<span data-ttu-id="2fd2a-186">**Cópia do corpo**: Transmita detalhes que sejam muito longos ou não são importantes o suficiente para incluir no cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-186">**Body copy**: Convey details that are either too long or not important enough to include in the header.</span></span>|
|<span data-ttu-id="2fd2a-187">C</span><span class="sxs-lookup"><span data-stu-id="2fd2a-187">C</span></span>|<span data-ttu-id="2fd2a-188">**Ações primárias**: Como prática recomendada, inclua 13 ações principais.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-188">**Primary actions**: As a best practice, include 1-3 primary actions.</span></span> <span data-ttu-id="2fd2a-189">Você pode ter até seis.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-189">You can have up to six.</span></span>|

## <a name="best-practices"></a><span data-ttu-id="2fd2a-190">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="2fd2a-190">Best practices</span></span>

<span data-ttu-id="2fd2a-191">Use essas recomendações para criar uma experiência de aplicativo de qualidade.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-191">Use these recommendations to create a quality app experience.</span></span>

### <a name="primary-and-secondary-actions"></a><span data-ttu-id="2fd2a-192">Ações primárias e secundárias</span><span class="sxs-lookup"><span data-stu-id="2fd2a-192">Primary and secondary actions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-do.png" alt-text="Prática recomendada sobre como você deve incluir apenas um pequeno conjunto de ações em um Cartão Adaptável." border="false":::

#### <a name="do-use-up-to-six-primary-actions"></a><span data-ttu-id="2fd2a-194">Faça: Usar até seis ações principais</span><span class="sxs-lookup"><span data-stu-id="2fd2a-194">Do: Use up to six primary actions</span></span>

<span data-ttu-id="2fd2a-195">Embora os Cartões Adaptáveis possam suportar seis ações primárias, a maioria dos cartões não precisa disso.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-195">While Adaptive Cards can support six primary actions, most cards don’t need that.</span></span> <span data-ttu-id="2fd2a-196">As ações devem ser claras, concisas e diretas.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-196">Actions should be clear, concise, and straight forward.</span></span> <span data-ttu-id="2fd2a-197">Menos é mais.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-197">Less is more.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-dont.png" alt-text="Prática recomendada sobre como não sobrecarregar os usuários com demasiadas ações em um Cartão Adaptável." border="false":::

#### <a name="dont-use-more-than-six-primary-actions"></a><span data-ttu-id="2fd2a-199">Não faça: Usar mais de seis ações principais</span><span class="sxs-lookup"><span data-stu-id="2fd2a-199">Don't: Use more than six primary actions</span></span>

<span data-ttu-id="2fd2a-200">Os Cartões Adaptáveis devem apresentar conteúdo rápido e prático.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-200">Adaptive Cards should present quick, actionable content.</span></span> <span data-ttu-id="2fd2a-201">Muitas ações podem sobrecarregar um usuário.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-201">Too many actions can overwhelm a user.</span></span>

   :::column-end:::
:::row-end:::

### <a name="frequency"></a><span data-ttu-id="2fd2a-202">Frequência</span><span class="sxs-lookup"><span data-stu-id="2fd2a-202">Frequency</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/frequency-do.png" alt-text="Práticas recomendadas sobre a frequência do Cartão Adaptável." border="false":::

#### <a name="do-be-concise"></a><span data-ttu-id="2fd2a-204">Faça: Seja conciso</span><span class="sxs-lookup"><span data-stu-id="2fd2a-204">Do: Be concise</span></span>

<span data-ttu-id="2fd2a-205">É fácil enviar vários cartões em uma conversa, mas quando os cartões saem da exibição, eles se tornam menos úteis.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-205">It's easy to send multiple cards into a conversation, but once cards scroll out of view, they become less useful.</span></span> <span data-ttu-id="2fd2a-206">Experimente se limitar ao essencial.</span><span class="sxs-lookup"><span data-stu-id="2fd2a-206">Try to limit yourself to the essentials.</span></span> <span data-ttu-id="2fd2a-207">Isso é especialmente verdadeiro em um canal onde os usuários têm menos tolerância com o que percebem como "ruído".</span><span class="sxs-lookup"><span data-stu-id="2fd2a-207">This is especially true in a channel where users have less tolerance for what they perceive as "noise".</span></span>
