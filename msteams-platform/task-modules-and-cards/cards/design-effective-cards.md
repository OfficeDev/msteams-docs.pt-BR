---
title: Projetando cartões adaptáveis para seu aplicativo
description: Saiba como projetar cartões adaptáveis para o Teams e obter o Kit de interface do usuário do Microsoft Teams.
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 67a2882a0a687d5ccb48759419ecefcdf9396fc3
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020279"
---
# <a name="designing-adaptive-cards-for-your-microsoft-teams-app"></a><span data-ttu-id="92002-103">Projetando cartões adaptáveis para seu aplicativo do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="92002-103">Designing Adaptive Cards for your Microsoft Teams app</span></span>

<span data-ttu-id="92002-104">Um Cartão Adaptável contém um corpo de forma livre de elementos de cartão e um conjunto opcional de ações.</span><span class="sxs-lookup"><span data-stu-id="92002-104">An Adaptive Card contains a freeform body of card elements and optional set of actions.</span></span> <span data-ttu-id="92002-105">Cartões adaptáveis são trechos acionáveis de conteúdo que você pode adicionar a uma conversa por meio de um bot ou extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="92002-105">Adaptive Cards are actionable snippets of content that you can add to a conversation through a bot or messaging extension.</span></span> <span data-ttu-id="92002-106">Usando texto, gráficos e botões, essas placas fornecem uma comunicação rica para o público-alvo.</span><span class="sxs-lookup"><span data-stu-id="92002-106">Using text, graphics, and buttons, these cards provide rich communication to your audience.</span></span>

<span data-ttu-id="92002-107">A estrutura cartão adaptável é usada em muitos produtos Microsoft, incluindo o Teams.</span><span class="sxs-lookup"><span data-stu-id="92002-107">The Adaptive Card framework is used across many Microsoft products, including Teams.</span></span> <span data-ttu-id="92002-108">Você pode enviar cartões dentro de mensagens para os usuários por meio de bots ou extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="92002-108">You can send cards inside messages to users via bots or messaging extensions.</span></span> <span data-ttu-id="92002-109">Os usuários podem tomar ações em cartões quando presentes.</span><span class="sxs-lookup"><span data-stu-id="92002-109">Users can take actions on cards when present.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/adaptive-card-overview.png" alt-text="Exemplo mostra um Cartão Adaptável." border="false":::

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="92002-111">Kit de Interface do Usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="92002-111">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="92002-112">Você pode encontrar diretrizes de design mais abrangentes para Cartões Adaptáveis no Teams, incluindo elementos que você pode obter e modificar conforme necessário, no Microsoft Teams UI Kit.</span><span class="sxs-lookup"><span data-stu-id="92002-112">You can find more comprehensive design guidelines for Adaptive Cards in Teams, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span> <span data-ttu-id="92002-113">O kit de interface do usuário também aborda tópicos essenciais, como temas, acessibilidade e tamanho responsivo.</span><span class="sxs-lookup"><span data-stu-id="92002-113">The UI kit also covers essential topics such as theming, accessibility, and responsive sizing.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="92002-114">Obtenha o Kit de Interface do Usuário do Microsoft Teams (Figma)</span><span class="sxs-lookup"><span data-stu-id="92002-114">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="adaptive-cards-designer"></a><span data-ttu-id="92002-115">Designer de Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="92002-115">Adaptive Cards designer</span></span>

<span data-ttu-id="92002-116">Você também pode começar a projetar seus Cartões Adaptáveis diretamente no navegador.</span><span class="sxs-lookup"><span data-stu-id="92002-116">You also can start designing your Adaptive Cards directly in the browser.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="92002-117">Experimente o designer de Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="92002-117">Try the Adaptive Cards designer</span></span>](https://adaptivecards.io/designer/)

## <a name="types-of-adaptive-cards"></a><span data-ttu-id="92002-118">Tipos de cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="92002-118">Types of Adaptive Cards</span></span>

### <a name="hero"></a><span data-ttu-id="92002-119">Destaque</span><span class="sxs-lookup"><span data-stu-id="92002-119">Hero</span></span>

<span data-ttu-id="92002-120">Nosso maior cartão.</span><span class="sxs-lookup"><span data-stu-id="92002-120">Our largest card.</span></span> <span data-ttu-id="92002-121">Use para compartilhar artigos ou cenários em que uma imagem conta a maior parte da história.</span><span class="sxs-lookup"><span data-stu-id="92002-121">Use for sharing articles or scenarios where an image tells most of the story.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/hero-card.png" alt-text="Exemplo mostra Cartão Adaptável." border="false":::

### <a name="thumbnail"></a><span data-ttu-id="92002-123">Miniatura</span><span class="sxs-lookup"><span data-stu-id="92002-123">Thumbnail</span></span>

<span data-ttu-id="92002-124">Use para enviar uma mensagem simples a actionable.</span><span class="sxs-lookup"><span data-stu-id="92002-124">Use for sending a simple actionable message.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/thumbnail-card.png" alt-text="Exemplo de um Cartão Adaptável." border="false":::

### <a name="list"></a><span data-ttu-id="92002-126">List</span><span class="sxs-lookup"><span data-stu-id="92002-126">List</span></span>

<span data-ttu-id="92002-127">Use em cenários em que você deseja que o usuário escolha um item de uma lista, mas os itens não precisam de muita explicação.</span><span class="sxs-lookup"><span data-stu-id="92002-127">Use in scenarios where you want the user to pick an item from a list, but the items don’t need a lot of explanation.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/list-card.png" alt-text="Exemplo de Cartão Adaptável." border="false":::

### <a name="digest"></a><span data-ttu-id="92002-129">Digest</span><span class="sxs-lookup"><span data-stu-id="92002-129">Digest</span></span>

<span data-ttu-id="92002-130">Use para resumos de notícias e postagens arredonddas.</span><span class="sxs-lookup"><span data-stu-id="92002-130">Use for news digests and round-up posts.</span></span> <span data-ttu-id="92002-131">Observação: recomendamos o cartão de miniatura para uma única atualização ou item de notícias.</span><span class="sxs-lookup"><span data-stu-id="92002-131">Note: We recommend the thumbnail card for a single update or news item.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/digest-card.png" alt-text="A ilustração mostra um Cartão Adaptável." border="false":::

### <a name="media"></a><span data-ttu-id="92002-133">Mídia</span><span class="sxs-lookup"><span data-stu-id="92002-133">Media</span></span>

<span data-ttu-id="92002-134">Use quando quiser combinar texto e mídia, como áudio ou vídeo.</span><span class="sxs-lookup"><span data-stu-id="92002-134">Use when you want to combine text and media, like audio or video.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/media-card.png" alt-text="A ilustração mostra o Cartão Adaptável." border="false":::

### <a name="people"></a><span data-ttu-id="92002-136">Pessoas</span><span class="sxs-lookup"><span data-stu-id="92002-136">People</span></span>

<span data-ttu-id="92002-137">Melhor usado quando você transmite com eficiência quem está envolvido com uma tarefa.</span><span class="sxs-lookup"><span data-stu-id="92002-137">Best used when you to efficiently convey who's involved with a task.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/people-card.png" alt-text="Ilustração de um Cartão Adaptável." border="false":::

### <a name="request-ticket"></a><span data-ttu-id="92002-139">Tíquete de solicitação</span><span class="sxs-lookup"><span data-stu-id="92002-139">Request ticket</span></span>

<span data-ttu-id="92002-140">Use para obter entradas rápidas de um usuário para criar automaticamente uma tarefa ou tíquete.</span><span class="sxs-lookup"><span data-stu-id="92002-140">Use to get quick inputs from a user to automatically create a task or ticket.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/request-ticket-card.png" alt-text="Ilustração do Cartão Adaptável." border="false":::

### <a name="imageset"></a><span data-ttu-id="92002-142">ImageSet</span><span class="sxs-lookup"><span data-stu-id="92002-142">ImageSet</span></span>

<span data-ttu-id="92002-143">Use para enviar várias miniaturas de imagem.</span><span class="sxs-lookup"><span data-stu-id="92002-143">Use to send multiple image thumbnails.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/image-set-card.png" alt-text="Amostra de um Cartão Adaptável." border="false":::

### <a name="actionset"></a><span data-ttu-id="92002-145">ActionSet</span><span class="sxs-lookup"><span data-stu-id="92002-145">ActionSet</span></span>

<span data-ttu-id="92002-146">Use quando quiser que o usuário selecione um botão e, em seguida, reúna a entrada do usuário de adição do mesmo cartão.</span><span class="sxs-lookup"><span data-stu-id="92002-146">Use when you want to the user to select a button, then gather addition user input from the same card.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/action-set-card.png" alt-text="Exemplo mostra um Cartão Adaptável." border="false":::

### <a name="choiceset"></a><span data-ttu-id="92002-148">ChoiceSet</span><span class="sxs-lookup"><span data-stu-id="92002-148">ChoiceSet</span></span>

<span data-ttu-id="92002-149">Use para coletar várias entradas do usuário.</span><span class="sxs-lookup"><span data-stu-id="92002-149">Use to gather multiple inputs from the user.</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/choice-set-card.png" alt-text="Exemplo exibe um Cartão Adaptável." border="false":::

## <a name="anatomy"></a><span data-ttu-id="92002-151">Anatomia</span><span class="sxs-lookup"><span data-stu-id="92002-151">Anatomy</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/anatomy.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de um Cartão Adaptável." border="false":::

<span data-ttu-id="92002-153">Cartões adaptáveis têm muita flexibilidade.</span><span class="sxs-lookup"><span data-stu-id="92002-153">Adaptive Cards have a lot of flexibility.</span></span> <span data-ttu-id="92002-154">No mínimo, sugerimos incluir os seguintes componentes em cada cartão:</span><span class="sxs-lookup"><span data-stu-id="92002-154">But at minimum, we strongly suggest including the following components in every card:</span></span>

|<span data-ttu-id="92002-155">Contador</span><span class="sxs-lookup"><span data-stu-id="92002-155">Counter</span></span>|<span data-ttu-id="92002-156">Descrição</span><span class="sxs-lookup"><span data-stu-id="92002-156">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="92002-157">A</span><span class="sxs-lookup"><span data-stu-id="92002-157">A</span></span>|<span data-ttu-id="92002-158">**Header**: Tornar os headers claros e concisos, mas descritivos.</span><span class="sxs-lookup"><span data-stu-id="92002-158">**Header**: Make headers clear and concise, yet descriptive.</span></span>|
|<span data-ttu-id="92002-159">B</span><span class="sxs-lookup"><span data-stu-id="92002-159">B</span></span>|<span data-ttu-id="92002-160">**Cópia do** corpo : use para transmitir detalhes que são muito longos ou não importantes o suficiente para incluir no header.</span><span class="sxs-lookup"><span data-stu-id="92002-160">**Body copy**: Use to convey detail that is either too long or not important enough to include in the header.</span></span>|
|<span data-ttu-id="92002-161">C</span><span class="sxs-lookup"><span data-stu-id="92002-161">C</span></span>|<span data-ttu-id="92002-162">**Ações primárias**: Como prática prática, inclua ações primárias de 1 a 3.</span><span class="sxs-lookup"><span data-stu-id="92002-162">**Primary actions**: As a best practice, include 1-3 primary actions.</span></span> <span data-ttu-id="92002-163">No máximo seis são permitidos.</span><span class="sxs-lookup"><span data-stu-id="92002-163">A maximum of six are allowed.</span></span>|

## <a name="best-practices"></a><span data-ttu-id="92002-164">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="92002-164">Best practices</span></span>

### <a name="primary-and-secondary-actions"></a><span data-ttu-id="92002-165">Ações primárias e secundárias</span><span class="sxs-lookup"><span data-stu-id="92002-165">Primary and secondary actions</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-do.png" alt-text="Exemplo mostrando uma prática prática de Cartões Adaptáveis." border="false":::

#### <a name="do-use-up-to-six-primary-actions"></a><span data-ttu-id="92002-167">Fazer: usar até seis ações primárias</span><span class="sxs-lookup"><span data-stu-id="92002-167">Do: Use up to six primary actions</span></span>

<span data-ttu-id="92002-168">Embora os Cartões Adaptáveis possam dar suporte a seis ações principais, a maioria dos cartões não precisa disso.</span><span class="sxs-lookup"><span data-stu-id="92002-168">While Adaptive Cards can support six primary actions, most cards don’t need that.</span></span> <span data-ttu-id="92002-169">As ações devem ser claras, concisas e diretas.</span><span class="sxs-lookup"><span data-stu-id="92002-169">Actions should be clear, concise, and straight forward.</span></span> <span data-ttu-id="92002-170">Menos é mais.</span><span class="sxs-lookup"><span data-stu-id="92002-170">Less is more.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-dont.png" alt-text="Exemplo mostra uma prática prática de Cartões Adaptáveis." border="false":::

#### <a name="dont-use-more-than-six-primary-actions"></a><span data-ttu-id="92002-172">Não: use mais de seis ações primárias</span><span class="sxs-lookup"><span data-stu-id="92002-172">Don't: Use more than six primary actions</span></span>

<span data-ttu-id="92002-173">Cartões adaptáveis devem apresentar conteúdo rápido e ativos.</span><span class="sxs-lookup"><span data-stu-id="92002-173">Adaptive Cards should present quick, actionable content.</span></span> <span data-ttu-id="92002-174">Muitas ações podem sobrecarregar um usuário.</span><span class="sxs-lookup"><span data-stu-id="92002-174">Too many actions can overwhelm a user.</span></span>

   :::column-end:::
:::row-end:::

### <a name="frequency"></a><span data-ttu-id="92002-175">Frequência</span><span class="sxs-lookup"><span data-stu-id="92002-175">Frequency</span></span>

:::image type="content" source="../../assets/images/adaptive-cards/frequency-do.png" alt-text="Ilustração exibindo uma prática prática prática de Cartões Adaptáveis." border="false":::

#### <a name="do-be-concise"></a><span data-ttu-id="92002-177">Do: Ser conciso</span><span class="sxs-lookup"><span data-stu-id="92002-177">Do: Be concise</span></span>

<span data-ttu-id="92002-178">É fácil enviar vários cartões para uma conversa, mas quando os cartões ficam fora de exibição, eles se tornam menos úteis.</span><span class="sxs-lookup"><span data-stu-id="92002-178">It's easy to send multiple cards into a conversation, but once cards scroll out of view, they become less useful.</span></span> <span data-ttu-id="92002-179">Tente limitar-se ao essencial.</span><span class="sxs-lookup"><span data-stu-id="92002-179">Try to limit yourself to the essentials.</span></span> <span data-ttu-id="92002-180">Isso é especialmente verdadeiro em um canal onde os usuários têm menos tolerância para o que eles percebem como "ruído".</span><span class="sxs-lookup"><span data-stu-id="92002-180">This is especially true in a channel where users have less tolerance for what they perceive as "noise".</span></span>
