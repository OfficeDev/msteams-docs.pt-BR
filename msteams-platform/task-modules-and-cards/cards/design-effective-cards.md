---
title: Criando cartões adaptáveis para seu aplicativo
description: Saiba como projetar cartões adaptáveis para equipes e obter o kit de interface do usuário do Microsoft Teams.
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: bd48846284620415cc8cadabc59f2ab7b61d5189
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2020
ms.locfileid: "49604491"
---
# <a name="designing-adaptive-cards-for-your-microsoft-teams-app"></a><span data-ttu-id="e6b36-103">Projetando cartões adaptáveis para seu aplicativo do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="e6b36-103">Designing Adaptive Cards for your Microsoft Teams app</span></span>

<span data-ttu-id="e6b36-104">Um cartão adaptável contém um corpo de forma livre de elementos de cartão e conjunto opcional de ações.</span><span class="sxs-lookup"><span data-stu-id="e6b36-104">An Adaptive Card contains a freeform body of card elements and optional set of actions.</span></span> <span data-ttu-id="e6b36-105">Cartões adaptáveis são trechos acionáveis do conteúdo que você pode adicionar a uma conversa por meio de um bot ou extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="e6b36-105">Adaptive Cards are actionable snippets of content that you can add to a conversation through a bot or messaging extension.</span></span> <span data-ttu-id="e6b36-106">Usando texto, elementos gráficos e botões, esses cartões fornecem comunicação avançada com o público.</span><span class="sxs-lookup"><span data-stu-id="e6b36-106">Using text, graphics, and buttons, these cards provide rich communication to your audience.</span></span>

<span data-ttu-id="e6b36-107">A estrutura de cartão adaptável é usada em vários produtos da Microsoft, incluindo o Teams.</span><span class="sxs-lookup"><span data-stu-id="e6b36-107">The Adaptive Card framework is used across many Microsoft products, including Teams.</span></span> <span data-ttu-id="e6b36-108">Você pode enviar cartões dentro de mensagens para usuários via bots ou extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="e6b36-108">You can send cards inside messages to users via bots or messaging extensions.</span></span> <span data-ttu-id="e6b36-109">Os usuários podem executar ações em cartões, quando presentes.</span><span class="sxs-lookup"><span data-stu-id="e6b36-109">Users can take actions on cards when present.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/adaptive-card-overview.png" alt-text="O exemplo mostra um cartão adaptável." border="false":::

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="e6b36-111">Kit de interface do usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="e6b36-111">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="e6b36-112">Você pode encontrar diretrizes de design mais abrangentes para cartões adaptáveis no Teams, incluindo elementos que podem ser capturados e modificados conforme necessário, no kit de interface do usuário do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="e6b36-112">You can find more comprehensive design guidelines for Adaptive Cards in Teams, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span> <span data-ttu-id="e6b36-113">O kit de interface do usuário também aborda tópicos essenciais, como temas, acessibilidade e dimensionamento responsivo.</span><span class="sxs-lookup"><span data-stu-id="e6b36-113">The UI kit also covers essential topics such as theming, accessibility, and responsive sizing.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e6b36-114">Obter o kit de interface do usuário do Microsoft Teams (figma)</span><span class="sxs-lookup"><span data-stu-id="e6b36-114">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="adaptive-cards-designer"></a><span data-ttu-id="e6b36-115">Designer de cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="e6b36-115">Adaptive Cards designer</span></span>

<span data-ttu-id="e6b36-116">Você também pode começar a criar seus cartões adaptáveis diretamente no navegador.</span><span class="sxs-lookup"><span data-stu-id="e6b36-116">You also can start designing your Adaptive Cards directly in the browser.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e6b36-117">Experimente o designer de cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="e6b36-117">Try the Adaptive Cards designer</span></span>](https://adaptivecards.io/designer/)

## <a name="types-of-adaptive-cards"></a><span data-ttu-id="e6b36-118">Tipos de cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="e6b36-118">Types of Adaptive Cards</span></span>

### <a name="hero"></a><span data-ttu-id="e6b36-119">Destaque</span><span class="sxs-lookup"><span data-stu-id="e6b36-119">Hero</span></span>

<span data-ttu-id="e6b36-120">Nosso maior cartão.</span><span class="sxs-lookup"><span data-stu-id="e6b36-120">Our largest card.</span></span> <span data-ttu-id="e6b36-121">Use para compartilhar artigos ou cenários onde uma imagem diz maior parte da história.</span><span class="sxs-lookup"><span data-stu-id="e6b36-121">Use for sharing articles or scenarios where an image tells most of the story.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/hero-card.png" alt-text="O exemplo mostra um cartão adaptável." border="false":::

### <a name="thumbnail"></a><span data-ttu-id="e6b36-123">Thumbnail</span><span class="sxs-lookup"><span data-stu-id="e6b36-123">Thumbnail</span></span>

<span data-ttu-id="e6b36-124">Use para enviar uma mensagem acionável simples.</span><span class="sxs-lookup"><span data-stu-id="e6b36-124">Use for sending a simple actionable message.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/thumbnail-card.png" alt-text="O exemplo mostra um cartão adaptável." border="false":::

### <a name="list"></a><span data-ttu-id="e6b36-126">Listar</span><span class="sxs-lookup"><span data-stu-id="e6b36-126">List</span></span>

<span data-ttu-id="e6b36-127">Use em cenários em que você deseja que o usuário escolha um item de uma lista, mas os itens não precisam de muita explicação.</span><span class="sxs-lookup"><span data-stu-id="e6b36-127">Use in scenarios where you want the user to pick an item from a list, but the items don’t need a lot of explanation.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/list-card.png" alt-text="O exemplo mostra um cartão adaptável." border="false":::

### <a name="digest"></a><span data-ttu-id="e6b36-129">Digest</span><span class="sxs-lookup"><span data-stu-id="e6b36-129">Digest</span></span>

<span data-ttu-id="e6b36-130">Use para resumos de notícias e postagens de arredondamento.</span><span class="sxs-lookup"><span data-stu-id="e6b36-130">Use for news digests and round-up posts.</span></span> <span data-ttu-id="e6b36-131">Observação: Recomendamos o cartão de miniatura de uma atualização única ou de um item de notícias.</span><span class="sxs-lookup"><span data-stu-id="e6b36-131">Note: We recommend the thumbnail card for a single update or news item.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/digest-card.png" alt-text="O exemplo mostra um cartão adaptável." border="false":::

### <a name="media"></a><span data-ttu-id="e6b36-133">Mídia</span><span class="sxs-lookup"><span data-stu-id="e6b36-133">Media</span></span>

<span data-ttu-id="e6b36-134">Use quando quiser combinar texto e mídia, como áudio ou vídeo.</span><span class="sxs-lookup"><span data-stu-id="e6b36-134">Use when you want to combine text and media, like audio or video.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/media-card.png" alt-text="O exemplo mostra um cartão adaptável." border="false":::

### <a name="people"></a><span data-ttu-id="e6b36-136">Pessoas</span><span class="sxs-lookup"><span data-stu-id="e6b36-136">People</span></span>

<span data-ttu-id="e6b36-137">Melhor usado quando você transmite com eficiência as pessoas envolvidas em uma tarefa.</span><span class="sxs-lookup"><span data-stu-id="e6b36-137">Best used when you to efficiently convey who's involved with a task.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/people-card.png" alt-text="O exemplo mostra um cartão adaptável." border="false":::

### <a name="request-ticket"></a><span data-ttu-id="e6b36-139">Solicitar Tíquete</span><span class="sxs-lookup"><span data-stu-id="e6b36-139">Request ticket</span></span>

<span data-ttu-id="e6b36-140">Use para obter entradas rápidas de um usuário para criar automaticamente uma tarefa ou um tíquete.</span><span class="sxs-lookup"><span data-stu-id="e6b36-140">Use to get quick inputs from a user to automatically create a task or ticket.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/request-ticket-card.png" alt-text="O exemplo mostra um cartão adaptável." border="false":::

### <a name="imageset"></a><span data-ttu-id="e6b36-142">ImageSet</span><span class="sxs-lookup"><span data-stu-id="e6b36-142">ImageSet</span></span>

<span data-ttu-id="e6b36-143">Use para enviar várias miniaturas de imagem.</span><span class="sxs-lookup"><span data-stu-id="e6b36-143">Use to send multiple image thumbnails.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/image-set-card.png" alt-text="O exemplo mostra um cartão adaptável." border="false":::

### <a name="actionset"></a><span data-ttu-id="e6b36-145">ActionSet</span><span class="sxs-lookup"><span data-stu-id="e6b36-145">ActionSet</span></span>

<span data-ttu-id="e6b36-146">Use quando você quiser que o usuário selecione um botão e, em seguida, coletar a entrada de usuário do mesmo cartão.</span><span class="sxs-lookup"><span data-stu-id="e6b36-146">Use when you want to the user to select a button, then gather addition user input from the same card.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/action-set-card.png" alt-text="O exemplo mostra um cartão adaptável." border="false":::

### <a name="choiceset"></a><span data-ttu-id="e6b36-148">Choiceset</span><span class="sxs-lookup"><span data-stu-id="e6b36-148">ChoiceSet</span></span>

<span data-ttu-id="e6b36-149">Use para coletar várias entradas do usuário.</span><span class="sxs-lookup"><span data-stu-id="e6b36-149">Use to gather multiple inputs from the user.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/choice-set-card.png" alt-text="O exemplo mostra um cartão adaptável." border="false":::

## <a name="anatomy"></a><span data-ttu-id="e6b36-151">Anatomia</span><span class="sxs-lookup"><span data-stu-id="e6b36-151">Anatomy</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/anatomy.png" alt-text="Ilustração mostrando a anatomia de interface do usuário de um cartão adaptável." border="false":::

<span data-ttu-id="e6b36-153">Cartões adaptáveis têm muita flexibilidade.</span><span class="sxs-lookup"><span data-stu-id="e6b36-153">Adaptive Cards have a lot of flexibility.</span></span> <span data-ttu-id="e6b36-154">Mas, no mínimo, é recomendável que você inclua os seguintes componentes em todos os cartões:</span><span class="sxs-lookup"><span data-stu-id="e6b36-154">But at a minimum, we strongly suggest including the following components in every card:</span></span>

|<span data-ttu-id="e6b36-155">Contador</span><span class="sxs-lookup"><span data-stu-id="e6b36-155">Counter</span></span>|<span data-ttu-id="e6b36-156">Descrição</span><span class="sxs-lookup"><span data-stu-id="e6b36-156">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="e6b36-157">A</span><span class="sxs-lookup"><span data-stu-id="e6b36-157">A</span></span>|<span data-ttu-id="e6b36-158">**Cabeçalho**: torne os cabeçalhos claros e concisos, mas descritivos.</span><span class="sxs-lookup"><span data-stu-id="e6b36-158">**Header**: Make headers clear and concise, yet descriptive.</span></span>|
|<span data-ttu-id="e6b36-159">B</span><span class="sxs-lookup"><span data-stu-id="e6b36-159">B</span></span>|<span data-ttu-id="e6b36-160">**Cópia de corpo**: Use para transmitir detalhes que seja muito longo ou não seja importante o suficiente para incluir no cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="e6b36-160">**Body copy**: Use to convey detail that is either too long or not important enough to include in the header.</span></span>|
|<span data-ttu-id="e6b36-161">C</span><span class="sxs-lookup"><span data-stu-id="e6b36-161">C</span></span>|<span data-ttu-id="e6b36-162">**Ações principais**: como prática recomendada, inclua ações primárias de 1-3.</span><span class="sxs-lookup"><span data-stu-id="e6b36-162">**Primary actions**: As a best practice, include 1-3 primary actions.</span></span> <span data-ttu-id="e6b36-163">São permitidos no máximo seis.</span><span class="sxs-lookup"><span data-stu-id="e6b36-163">A maximum of six are allowed.</span></span>|

## <a name="best-practices"></a><span data-ttu-id="e6b36-164">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="e6b36-164">Best practices</span></span>

### <a name="primary-and-secondary-actions"></a><span data-ttu-id="e6b36-165">Ações primárias e secundárias</span><span class="sxs-lookup"><span data-stu-id="e6b36-165">Primary and secondary actions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-do.png" alt-text="Exemplo mostrando uma prática recomendada de cartões adaptáveis." border="false":::

#### <a name="do-use-up-to-six-primary-actions"></a><span data-ttu-id="e6b36-167">Fazer: usar até seis ações principais</span><span class="sxs-lookup"><span data-stu-id="e6b36-167">Do: Use up to six primary actions</span></span>

<span data-ttu-id="e6b36-168">Embora os cartões adaptáveis possam suportar seis ações principais, a maioria dos cartões não precisa de.</span><span class="sxs-lookup"><span data-stu-id="e6b36-168">While Adaptive Cards can support six primary actions, most cards don’t need that.</span></span> <span data-ttu-id="e6b36-169">As ações devem ser claras, concisas e diretas.</span><span class="sxs-lookup"><span data-stu-id="e6b36-169">Actions should be clear, concise, and straight forward.</span></span> <span data-ttu-id="e6b36-170">Menos é mais.</span><span class="sxs-lookup"><span data-stu-id="e6b36-170">Less is more.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-dont.png" alt-text="Exemplo mostrando uma prática recomendada de cartões adaptáveis." border="false":::

#### <a name="dont-use-more-than-six-primary-actions"></a><span data-ttu-id="e6b36-172">Não: usar mais de seis ações principais</span><span class="sxs-lookup"><span data-stu-id="e6b36-172">Don't: Use more than six primary actions</span></span>

<span data-ttu-id="e6b36-173">Os cartões adaptáveis devem apresentar conteúdo rápido e acionável.</span><span class="sxs-lookup"><span data-stu-id="e6b36-173">Adaptive Cards should present quick, actionable content.</span></span> <span data-ttu-id="e6b36-174">Muitas ações podem sobrecarregar um usuário.</span><span class="sxs-lookup"><span data-stu-id="e6b36-174">Too many actions can overwhelm a user.</span></span>

   :::column-end:::
:::row-end:::

### <a name="frequency"></a><span data-ttu-id="e6b36-175">Frequência</span><span class="sxs-lookup"><span data-stu-id="e6b36-175">Frequency</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/frequency-do.png" alt-text="Exemplo mostrando uma prática recomendada de cartões adaptáveis." border="false":::

#### <a name="do-be-concise"></a><span data-ttu-id="e6b36-177">Fazer: seja conciso</span><span class="sxs-lookup"><span data-stu-id="e6b36-177">Do: Be concise</span></span>

<span data-ttu-id="e6b36-178">É fácil enviar vários cartões para uma conversa, mas depois que os cartões saem do modo de exibição, eles se tornam menos úteis.</span><span class="sxs-lookup"><span data-stu-id="e6b36-178">It's easy to send multiple cards into a conversation, but once cards scroll out of view, they become less useful.</span></span> <span data-ttu-id="e6b36-179">Tente se limitar ao Essentials.</span><span class="sxs-lookup"><span data-stu-id="e6b36-179">Try to limit yourself to the essentials.</span></span> <span data-ttu-id="e6b36-180">Isso se aplica especialmente em um canal em que os usuários têm menos tolerância para o que eles percebem como "ruído".</span><span class="sxs-lookup"><span data-stu-id="e6b36-180">This is especially true in a channel where users have less tolerance for what they perceive as "noise".</span></span>
