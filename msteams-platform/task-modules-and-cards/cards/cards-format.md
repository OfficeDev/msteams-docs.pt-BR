---
title: Formatação de texto em cartões
description: Descreve a formatação de texto de cartão no Microsoft Teams
keywords: formato de cartões de bots do teams
ms.date: 03/29/2018
ms.openlocfilehash: 1221693ab9ae002ee982ef34a05ead1feb8b1f27
ms.sourcegitcommit: 47cf0d05e15e5c23616b18ae4e815fd871bbf827
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2021
ms.locfileid: "50455390"
---
# <a name="format-cards-in-teams"></a><span data-ttu-id="3c9ce-104">Formatar cartões no Teams</span><span class="sxs-lookup"><span data-stu-id="3c9ce-104">Format cards in Teams</span></span>

<span data-ttu-id="3c9ce-105">Você pode adicionar formatação de rich text aos cartões usando Markdown ou HTML, dependendo do tipo de cartão.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-105">You can add rich text formatting to your cards using either Markdown or HTML, depending on the card type.</span></span>

<span data-ttu-id="3c9ce-106">Os cartões suportam formatação somente na propriedade text, não nas propriedades title ou subtitle.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-106">Cards support formatting in the text property only, not in the title or subtitle properties.</span></span> <span data-ttu-id="3c9ce-107">A formatação pode ser especificada usando um subconjunto de formatação XML (HTML) ou Markdown, dependendo do tipo de cartão.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-107">Formatting can be specified using a subset of XML (HTML) formatting, or Markdown depending on card type.</span></span> <span data-ttu-id="3c9ce-108">Para cartões adaptáveis de desenvolvimento atual e futuro usando formatação Markdown é recomendável.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-108">For current and future development Adaptive cards using Markdown formatting is recommended.</span></span>

<span data-ttu-id="3c9ce-109">O suporte à formatação difere entre tipos de cartão diferentes, e a renderização do cartão pode diferir ligeiramente entre a área de trabalho e os clientes do Teams móveis, bem como o Teams no navegador da área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-109">Formatting support differs between different card types, and rendering of the card can differ slightly between the desktop and the mobile Teams clients, as well as Teams in the desktop browser.</span></span>

<span data-ttu-id="3c9ce-110">Você pode incluir uma imagem em linha com qualquer cartão do Teams.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-110">You can include an inline image with any Teams card.</span></span> <span data-ttu-id="3c9ce-111">Imagens formatadas como , ou arquivos e não devem exceder  `.png` `.jpg` `.gif` 1024 ×1024 px ou 1 MB.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-111">Images an be formatted as  `.png`, `.jpg`, or `.gif` files and must not exceed 1024 ×1024 px or 1 MB.</span></span> <span data-ttu-id="3c9ce-112">Gif animado não tem suporte oficial.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-112">Animated GIF is not officially supported.</span></span> <span data-ttu-id="3c9ce-113">*Consulte* [Referência de cartões](./cards-reference.md#inline-card-images)</span><span class="sxs-lookup"><span data-stu-id="3c9ce-113">*See* [Cards reference](./cards-reference.md#inline-card-images)</span></span>

## <a name="formatting-cards-with-markdown"></a><span data-ttu-id="3c9ce-114">Formatação de cartões com Markdown</span><span class="sxs-lookup"><span data-stu-id="3c9ce-114">Formatting cards with Markdown</span></span>

<span data-ttu-id="3c9ce-115">Há dois tipos de cartão que suportam Markdown no Teams:</span><span class="sxs-lookup"><span data-stu-id="3c9ce-115">There are two card types that support Markdown in Teams:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="3c9ce-116">**Cartões adaptáveis**: a marcação é suportada no campo cartão `Textblock` adaptável, bem como `Fact.Title` e `Fact.Value` .</span><span class="sxs-lookup"><span data-stu-id="3c9ce-116">**Adaptive cards**: Markdown is supported in Adaptive card `Textblock` field, as well as `Fact.Title` and `Fact.Value`.</span></span> <span data-ttu-id="3c9ce-117">HTML não é suportado em cartões adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-117">HTML is not supported in Adaptive cards.</span></span>
> * <span data-ttu-id="3c9ce-118">Cartões de conector **O365**: Markdown e HTML limitado são suportados em cartões do Conector do Office 365 nos campos de texto.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-118">**O365 Connector Cards**: Markdown and limited HTML is supported in Office 365 Connector cards in the text fields.</span></span>

# <a name="markdown-formatting-adaptive-cards"></a>[<span data-ttu-id="3c9ce-119">**Formatação de marcação: cartões adaptáveis**</span><span class="sxs-lookup"><span data-stu-id="3c9ce-119">**Markdown formatting: Adaptive cards**</span></span>](#tab/adaptive-md)

 <span data-ttu-id="3c9ce-120">Os estilos com suporte `Textblock` para e `Fact.Title` `Fact.Value` são:</span><span class="sxs-lookup"><span data-stu-id="3c9ce-120">The supported styles for `Textblock`, `Fact.Title` and `Fact.Value` are:</span></span>

| <span data-ttu-id="3c9ce-121">Style</span><span class="sxs-lookup"><span data-stu-id="3c9ce-121">Style</span></span> | <span data-ttu-id="3c9ce-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3c9ce-122">Example</span></span> | <span data-ttu-id="3c9ce-123">Markdown</span><span class="sxs-lookup"><span data-stu-id="3c9ce-123">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="3c9ce-124">bold</span><span class="sxs-lookup"><span data-stu-id="3c9ce-124">bold</span></span> | <span data-ttu-id="3c9ce-125">**Negrito**</span><span class="sxs-lookup"><span data-stu-id="3c9ce-125">**Bold**</span></span> | ```**Bold**``` |
| <span data-ttu-id="3c9ce-126">italic</span><span class="sxs-lookup"><span data-stu-id="3c9ce-126">italic</span></span> | <span data-ttu-id="3c9ce-127">_Itálico_</span><span class="sxs-lookup"><span data-stu-id="3c9ce-127">_Italic_</span></span> | ```_Italic_``` |
| <span data-ttu-id="3c9ce-128">lista semordenagem</span><span class="sxs-lookup"><span data-stu-id="3c9ce-128">unordered list</span></span> | <ul><li><span data-ttu-id="3c9ce-129">texto</span><span class="sxs-lookup"><span data-stu-id="3c9ce-129">text</span></span></li><li><span data-ttu-id="3c9ce-130">texto</span><span class="sxs-lookup"><span data-stu-id="3c9ce-130">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="3c9ce-131">lista ordenada</span><span class="sxs-lookup"><span data-stu-id="3c9ce-131">ordered list</span></span> | <ol><li><span data-ttu-id="3c9ce-132">texto</span><span class="sxs-lookup"><span data-stu-id="3c9ce-132">text</span></span></li><li><span data-ttu-id="3c9ce-133">texto</span><span class="sxs-lookup"><span data-stu-id="3c9ce-133">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="3c9ce-134">Hiperlinks</span><span class="sxs-lookup"><span data-stu-id="3c9ce-134">Hyperlinks</span></span> |[<span data-ttu-id="3c9ce-135">Bing</span><span class="sxs-lookup"><span data-stu-id="3c9ce-135">Bing</span></span>](https://www.bing.com/)| ```[Title](url)``` |

<span data-ttu-id="3c9ce-136">As seguintes marcas Markdown não são suportadas:</span><span class="sxs-lookup"><span data-stu-id="3c9ce-136">The following Markdown tags are not supported:</span></span>

* <span data-ttu-id="3c9ce-137">Cabeçalhos</span><span class="sxs-lookup"><span data-stu-id="3c9ce-137">Headers</span></span>
* <span data-ttu-id="3c9ce-138">Tabelas</span><span class="sxs-lookup"><span data-stu-id="3c9ce-138">Tables</span></span>
* <span data-ttu-id="3c9ce-139">Imagens</span><span class="sxs-lookup"><span data-stu-id="3c9ce-139">Images</span></span>
* <span data-ttu-id="3c9ce-140">Texto pré-formatado</span><span class="sxs-lookup"><span data-stu-id="3c9ce-140">Preformatted text</span></span>
* <span data-ttu-id="3c9ce-141">Blockquotes</span><span class="sxs-lookup"><span data-stu-id="3c9ce-141">Blockquotes</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3c9ce-142">Cartões adaptáveis não suportam formatação HTML.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-142">Adaptive cards do not support HTML formatting.</span></span>

### <a name="newlines-for-adaptive-cards"></a><span data-ttu-id="3c9ce-143">Linhas novas para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="3c9ce-143">Newlines for Adaptive cards</span></span>

<span data-ttu-id="3c9ce-144">Em listas, você pode usar `\r` as `\n` sequências de escape ou para newlines.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-144">In lists you can use the `\r` or `\n` escape sequences for newlines.</span></span> <span data-ttu-id="3c9ce-145">Usar `\n\n` em uma lista fará com que o próximo elemento da lista seja recuado.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-145">Using `\n\n` in a list will cause the next element in the list to be indented.</span></span> <span data-ttu-id="3c9ce-146">Se você precisar de linhas novas em outro lugar do bloco de texto, use `\n\n` .</span><span class="sxs-lookup"><span data-stu-id="3c9ce-146">If you need newlines elsewhere in the textblock, use `\n\n`.</span></span>

### <a name="mobile-and-desktop-differences-for-adaptive-cards"></a><span data-ttu-id="3c9ce-147">Diferenças de dispositivos móveis e de área de trabalho para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="3c9ce-147">Mobile and desktop differences for Adaptive cards</span></span>

<span data-ttu-id="3c9ce-148">A formatação é ligeiramente diferente entre a área de trabalho e as versões móveis do Teams.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-148">Formatting is slightly different between the desktop and the mobile versions of Teams.</span></span>

<span data-ttu-id="3c9ce-149">Na área de trabalho, a formatação de Markdown de cartão adaptável aparece assim nos navegadores da Web e no aplicativo cliente do Teams:</span><span class="sxs-lookup"><span data-stu-id="3c9ce-149">On the desktop, Adaptive card Markdown formatting appears like this in both web browsers and in the Teams client application:</span></span>

![Formatação de markdown de cartão adaptável no cliente da área de trabalho](../../assets/images/cards/Adaptive-markdown-desktop-client.png)

<span data-ttu-id="3c9ce-151">No iOS, a formatação De marcação de cartão adaptável aparece assim:</span><span class="sxs-lookup"><span data-stu-id="3c9ce-151">On iOS, Adaptive card Markdown formatting appears like this:</span></span>

![Formatação de markdown de cartão adaptável no iOS](../../assets/images/cards/Adaptive-markdown-iOS-75.png)

<span data-ttu-id="3c9ce-153">No Android, a formatação adaptável de Marcação de Cartão aparece assim:</span><span class="sxs-lookup"><span data-stu-id="3c9ce-153">On Android, Adaptive Card Markdown formatting appears like this:</span></span>

![Formatação de markdown de cartão adaptável no Android](../../assets/images/cards/Adaptive-markdown-Android.png)

### <a name="more-information-on-adaptive-cards"></a><span data-ttu-id="3c9ce-155">Mais informações sobre cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="3c9ce-155">More information on Adaptive cards</span></span>

<span data-ttu-id="3c9ce-156">[Recursos de texto em cartões adaptáveis](/adaptive-cards/create/textfeatures) Os recursos de data e localização mencionados neste tópico não são suportados no Teams.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-156">[Text features in Adaptive cards](/adaptive-cards/create/textfeatures) The date and localization features mentioned in this topic are not supported in Teams.</span></span>

### <a name="formatting-sample-for-adaptive-cards"></a><span data-ttu-id="3c9ce-157">Exemplo de formatação para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="3c9ce-157">Formatting sample for Adaptive cards</span></span>

``` json
{
    "$schema": "https://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
        {
            "type": "TextBlock",
            "text": "This is some **bold** text"
        },
        {
            "type": "TextBlock",
            "text": "This is some _italic_ text"
        },
        {
            "type": "TextBlock",
            "text": "- Bullet \r- List \r",
            "wrap": true
        },
        {
            "type": "TextBlock",
            "text": "1. Numbered\r2. List\r",
            "wrap": true
        },
        {
            "type": "TextBlock",
            "text": "Check out [Adaptive Cards](https://adaptivecards.io)"
        }
    ]
}
```

### <a name="mention-support-within-adaptive-cards-v12"></a><span data-ttu-id="3c9ce-158">Mencionar suporte em cartões adaptáveis v1.2</span><span class="sxs-lookup"><span data-stu-id="3c9ce-158">Mention support within Adaptive cards v1.2</span></span>

<span data-ttu-id="3c9ce-159">As menções baseadas em cartão são suportadas em clientes Web, Desktop e móveis.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-159">Card based mentions are supported in Web, Desktop and mobile clients.</span></span> <span data-ttu-id="3c9ce-160">Você pode adicionar @ menções em um corpo de cartão adaptável para bots e respostas de extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-160">You can add @ mentions within an Adaptive card body for bots and messaging extension responses.</span></span>  <span data-ttu-id="3c9ce-161">Para adicionar @ menções em cartões, siga a mesma lógica de notificação e renderização das menções baseadas em mensagens em conversas de chat de canal [e grupo.](../../bots/how-to/conversations/channel-and-group-conversations.md#working-with-mentions )</span><span class="sxs-lookup"><span data-stu-id="3c9ce-161">To add @ mentions in cards, follow the same notification logic and rendering as that of message based [mentions in channel and group chat conversations](../../bots/how-to/conversations/channel-and-group-conversations.md#working-with-mentions ).</span></span>

<span data-ttu-id="3c9ce-162">Bots e extensões de mensagens podem incluir menções no conteúdo do cartão nos [elementos TextBlock](https://adaptivecards.io/explorer/TextBlock.html) e [FactSet.](https://adaptivecards.io/explorer/FactSet.html)</span><span class="sxs-lookup"><span data-stu-id="3c9ce-162">Bots and messaging extensions can include mentions within the card content in [TextBlock](https://adaptivecards.io/explorer/TextBlock.html) and [FactSet](https://adaptivecards.io/explorer/FactSet.html) elements.</span></span>

> [!NOTE]
> * <span data-ttu-id="3c9ce-163">[Os elementos de](https://adaptivecards.io/explorer/Media.html) mídia atualmente não são suportados em cartões adaptáveis v1.2 na plataforma teams.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-163">[Media elements](https://adaptivecards.io/explorer/Media.html) are currently not supported in Adaptive cards v1.2 on the Teams platform.</span></span>
> * <span data-ttu-id="3c9ce-164">As & de equipe não são suportadas em mensagens bot.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-164">Channel & Team mentions are not supported in bot messages.</span></span>

#### <a name="constructing-mentions"></a><span data-ttu-id="3c9ce-165">Criar menções</span><span class="sxs-lookup"><span data-stu-id="3c9ce-165">Constructing mentions</span></span>

<span data-ttu-id="3c9ce-166">Para incluir uma menção em um cartão Adaptável, seu aplicativo precisa incluir os seguintes elementos</span><span class="sxs-lookup"><span data-stu-id="3c9ce-166">To include a mention in an Adaptive card your app needs to include the following elements</span></span>

* <span data-ttu-id="3c9ce-167">`<at>username</at>` nos elementos de cartão adaptáveis com suporte</span><span class="sxs-lookup"><span data-stu-id="3c9ce-167">`<at>username</at>` in the supported Adaptive card elements</span></span>
* <span data-ttu-id="3c9ce-168">O objeto dentro de uma propriedade no conteúdo do cartão, que inclui a id de usuário do `mention` Teams do usuário que está sendo `msteams` mencionado</span><span class="sxs-lookup"><span data-stu-id="3c9ce-168">The `mention` object inside of an `msteams` property in the card content, which includes the Teams user id of the user being mentioned</span></span>

#### <a name="sample-adaptive-card-with-a-mention"></a><span data-ttu-id="3c9ce-169">Exemplo de cartão adaptável com uma menção</span><span class="sxs-lookup"><span data-stu-id="3c9ce-169">Sample Adaptive card with a mention</span></span>

``` json
{
  "contentType": "application/vnd.microsoft.card.adaptive",
  "content": {
    "type": "AdaptiveCard",
    "body": [
      {
        "type": "TextBlock",
        "text": "Hi <at>John Doe</at>"
      }
    ],
    "$schema": "https://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.0",
    "msteams": {
      "entities": [
        {
          "type": "mention",
          "text": "<at>John Doe</at>",
          "mentioned": {
            "id": "29:123124124124",
            "name": "John Doe"
          }
        }
      ]
    }
  }
}
```


### <a name="information-masking-in-adaptive-cards"></a><span data-ttu-id="3c9ce-170">Mascaramento de informações em cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="3c9ce-170">Information masking in Adaptive cards</span></span>
<span data-ttu-id="3c9ce-171">Use a propriedade mascarar informações para mascarar informações específicas, como senha ou informações confidenciais dos usuários.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-171">Use the information masking property to mask specific information, such as password or sensitive information from users.</span></span>

> [!NOTE]
> <span data-ttu-id="3c9ce-172">A propriedade de mascaramento de informações está disponível apenas na visualização do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-172">The information masking property is currently available in the developer preview only.</span></span>

#### <a name="mask-information"></a><span data-ttu-id="3c9ce-173">Informações sobre máscara</span><span class="sxs-lookup"><span data-stu-id="3c9ce-173">Mask information</span></span>
<span data-ttu-id="3c9ce-174">Para mascarar informações em cartões adaptáveis, adicione a propriedade para `isMasked` **digitar** e de definir seu valor `Input.Text` como *true*.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-174">To mask information in Adaptive cards, add the `isMasked` property to **type** `Input.Text`, and set its value to *true*.</span></span>

#### <a name="sample-adaptive-card-with-masking-property"></a><span data-ttu-id="3c9ce-175">Cartão adaptável de exemplo com a propriedade mascaramento</span><span class="sxs-lookup"><span data-stu-id="3c9ce-175">Sample Adaptive card with masking property</span></span>

```json
{
    "type": "Input.Text",
    "id": "secretThing",
    "style": "password",
    "isMasked": true
  },
```

<span data-ttu-id="3c9ce-176">A imagem a seguir é um exemplo de informações de mascaramento em cartões adaptáveis:</span><span class="sxs-lookup"><span data-stu-id="3c9ce-176">The following image is an example of masking information in Adaptive cards:</span></span>

![Imagem de informações de mascaramento](../../assets/images/cards/masking-information-view.png)

### <a name="full-width-adaptive-card"></a><span data-ttu-id="3c9ce-178">Cartão adaptável de largura total</span><span class="sxs-lookup"><span data-stu-id="3c9ce-178">Full width Adaptive card</span></span>
<span data-ttu-id="3c9ce-179">Você pode usar a propriedade para expandir a largura de um `msteams` cartão Adaptável e usar espaço adicional de tela.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-179">You can use the `msteams` property to expand the width of an Adaptive card and make use of additional canvas space.</span></span> <span data-ttu-id="3c9ce-180">Para obter informações sobre como usar a propriedade, consulte o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="3c9ce-180">For information on how to use the property, see the following example:</span></span>

#### <a name="constructing-full-width-cards"></a><span data-ttu-id="3c9ce-181">Construir cartões de largura total</span><span class="sxs-lookup"><span data-stu-id="3c9ce-181">Constructing full width cards</span></span>
<span data-ttu-id="3c9ce-182">Para fazer um cartão adaptável de largura total, o objeto na propriedade no conteúdo do cartão deve `width` `msteams` ser definido como `Full` .</span><span class="sxs-lookup"><span data-stu-id="3c9ce-182">To make a full width Adaptive card the `width` object in `msteams` property in the card content must be set to `Full`.</span></span>
<span data-ttu-id="3c9ce-183">Além disso, seu aplicativo deve incluir os seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="3c9ce-183">In addition, your app must include the following elements:</span></span>

#### <a name="sample-adaptive-card-with-full-width"></a><span data-ttu-id="3c9ce-184">Exemplo de cartão adaptável com largura total</span><span class="sxs-lookup"><span data-stu-id="3c9ce-184">Sample adaptive card with full width</span></span>

``` json
{
    "type": "AdaptiveCard",
    "body": [{
        "type": "Container",
        "items": [{
            "type": "TextBlock",
            "text": "Digest card",
            "size": "Large",
            "weight": "Bolder"
        }]
    }],
    
    "msteams": {
        "width": "Full"
    },
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.2"
}
```

<span data-ttu-id="3c9ce-185">Um Cartão Adaptável de largura total aparece da seguinte forma: Exibição de Cartão Adaptável de largura ![ total](../../assets/images/cards/full-width-adaptive-card.png)</span><span class="sxs-lookup"><span data-stu-id="3c9ce-185">A full width Adaptive Card appears as follows: ![Full width Adaptive Card view](../../assets/images/cards/full-width-adaptive-card.png)</span></span>

<span data-ttu-id="3c9ce-186">Se você não tiver definido a propriedade como Full , o modo de exibição padrão do Cartão Adaptável será o seguinte: Modo de exibição cartão adaptável de largura `width`  ![ pequena](../../assets/images/cards/small-width-adaptive-card.png)</span><span class="sxs-lookup"><span data-stu-id="3c9ce-186">If you have not set the `width` property to *Full*, then the default view of the Adaptive Card is as follows: ![Small width Adaptive Card view](../../assets/images/cards/small-width-adaptive-card.png)</span></span>



# <a name="markdown-formatting-o365-connector-cards"></a>[<span data-ttu-id="3c9ce-187">**Formatação de marcação: cartões de conector O365**</span><span class="sxs-lookup"><span data-stu-id="3c9ce-187">**Markdown formatting: O365 Connector Cards**</span></span>](#tab/connector-md)

<span data-ttu-id="3c9ce-188">Os cartões conectores suportam a formatação limitada markdown e HTML.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-188">Connector cards support limited Markdown and HTML formatting.</span></span> <span data-ttu-id="3c9ce-189">O suporte HTML é descrito na última seção.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-189">HTML support is described in the last section.</span></span>

| <span data-ttu-id="3c9ce-190">Style</span><span class="sxs-lookup"><span data-stu-id="3c9ce-190">Style</span></span> | <span data-ttu-id="3c9ce-191">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3c9ce-191">Example</span></span> | <span data-ttu-id="3c9ce-192">Markdown</span><span class="sxs-lookup"><span data-stu-id="3c9ce-192">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="3c9ce-193">bold</span><span class="sxs-lookup"><span data-stu-id="3c9ce-193">bold</span></span> | <span data-ttu-id="3c9ce-194">**text**</span><span class="sxs-lookup"><span data-stu-id="3c9ce-194">**text**</span></span> | `**text**` |
| <span data-ttu-id="3c9ce-195">italic</span><span class="sxs-lookup"><span data-stu-id="3c9ce-195">italic</span></span> | <span data-ttu-id="3c9ce-196">*text*</span><span class="sxs-lookup"><span data-stu-id="3c9ce-196">*text*</span></span> | `*text*` |
| <span data-ttu-id="3c9ce-197">header (níveis 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="3c9ce-197">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="3c9ce-198">**Text**</span><span class="sxs-lookup"><span data-stu-id="3c9ce-198">**Text**</span></span> | `### Text`|
| <span data-ttu-id="3c9ce-199">strikethrough</span><span class="sxs-lookup"><span data-stu-id="3c9ce-199">strikethrough</span></span> | <span data-ttu-id="3c9ce-200">~~text~~</span><span class="sxs-lookup"><span data-stu-id="3c9ce-200">~~text~~</span></span> | `~~text~~` |
| <span data-ttu-id="3c9ce-201">lista semordenagem</span><span class="sxs-lookup"><span data-stu-id="3c9ce-201">unordered list</span></span> | <ul><li><span data-ttu-id="3c9ce-202">texto</span><span class="sxs-lookup"><span data-stu-id="3c9ce-202">text</span></span></li><li><span data-ttu-id="3c9ce-203">texto</span><span class="sxs-lookup"><span data-stu-id="3c9ce-203">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="3c9ce-204">lista ordenada</span><span class="sxs-lookup"><span data-stu-id="3c9ce-204">ordered list</span></span> | <ol><li><span data-ttu-id="3c9ce-205">texto</span><span class="sxs-lookup"><span data-stu-id="3c9ce-205">text</span></span></li><li><span data-ttu-id="3c9ce-206">texto</span><span class="sxs-lookup"><span data-stu-id="3c9ce-206">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="3c9ce-207">texto pré-formatado</span><span class="sxs-lookup"><span data-stu-id="3c9ce-207">preformatted text</span></span> | `text` | ``preformatted text`` |
| <span data-ttu-id="3c9ce-208">blockquote</span><span class="sxs-lookup"><span data-stu-id="3c9ce-208">blockquote</span></span> | <span data-ttu-id="3c9ce-209">>texto blockquote</span><span class="sxs-lookup"><span data-stu-id="3c9ce-209">>blockquote text</span></span> | `>blockquote text` |
| <span data-ttu-id="3c9ce-210">hiperlink</span><span class="sxs-lookup"><span data-stu-id="3c9ce-210">hyperlink</span></span> | [<span data-ttu-id="3c9ce-211">Bing</span><span class="sxs-lookup"><span data-stu-id="3c9ce-211">Bing</span></span>](https://www.bing.com/) | `[Bing](https://www.bing.com/)` |
| <span data-ttu-id="3c9ce-212">link de imagem</span><span class="sxs-lookup"><span data-stu-id="3c9ce-212">image link</span></span> |![Duck on a rock](https://aka.ms/Fo983c) | `![Duck](https://aka.ms/Fo983c)` |

<span data-ttu-id="3c9ce-214">Em cartões de conector, as linhas novas são renderizadas `\n\n` para , mas não para ou `\n` `\r` .</span><span class="sxs-lookup"><span data-stu-id="3c9ce-214">In connector cards, newlines are rendered for `\n\n`, but not for `\n` or `\r`.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards-using-markdown"></a><span data-ttu-id="3c9ce-215">Diferenças de dispositivos móveis e de área de trabalho para cartões de conector usando Markdown</span><span class="sxs-lookup"><span data-stu-id="3c9ce-215">Mobile and desktop differences for connector cards using Markdown</span></span>

<span data-ttu-id="3c9ce-216">Na área de trabalho, a formatação markdown para cartões de conector tem a mesma aparência:</span><span class="sxs-lookup"><span data-stu-id="3c9ce-216">On the desktop, Markdown formatting for connector cards looks like this:</span></span>

![Formatação de marcação para cartões conectores no cliente desktop](../../assets/images/cards/connector-desktop-markdown-combined.png)

<span data-ttu-id="3c9ce-218">No iOS, a formatação markdown para cartões de conector tem a aparência:</span><span class="sxs-lookup"><span data-stu-id="3c9ce-218">On iOS, Markdown formatting for connector cards looks like this:</span></span>

![Formatação de marcação para cartões conectores no cliente iOS](../../assets/images/cards/connector-iphone-markdown-combined-80.png)

<span data-ttu-id="3c9ce-220">Problemas:</span><span class="sxs-lookup"><span data-stu-id="3c9ce-220">Issues:</span></span>

* <span data-ttu-id="3c9ce-221">O cliente iOS do Teams não renderiza imagens em linha Markdown ou HTML em Cartões conectores.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-221">The iOS client for Teams does not render Markdown or HTML inline images in Connector Cards.</span></span>
* <span data-ttu-id="3c9ce-222">As blockquotes são renderizadas como recuadas, mas sem um plano de fundo cinza.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-222">Blockquotes are rendered as indented but without a gray background.</span></span>

<span data-ttu-id="3c9ce-223">No Android, a formatação markdown para cartões de conector tem a aparência:</span><span class="sxs-lookup"><span data-stu-id="3c9ce-223">On Android, Markdown formatting for connector cards looks like this:</span></span>

![Formatação de marcação para cartões conectores no cliente Android](../../assets/images/cards/connector-android-markdown-combined.png)

### <a name="formatting-example-for-markdown-connector-cards"></a><span data-ttu-id="3c9ce-225">Exemplo de formatação para Cartões de Conector de Markdown</span><span class="sxs-lookup"><span data-stu-id="3c9ce-225">Formatting example for Markdown Connector Cards</span></span>

``` json
{
  "contentType": "application/vnd.microsoft.teams.card.o365connector",
  "content": {
    "@type": "MessageCard",
    "@context": "https://schema.org/extensions",
    "summary": "Summary",
    "title": "Connector Card Markdown formatting",
    "sections": [
        {
            "text": "This is some **bold** text"
        },
        {
            "text": "This is some _italic_ text"
        },
        {
            "text": "# Header 1\r## Header 2\r### Header 3"
        },
        {
            "text": "- Bullet \r- List \r"
        },
        {
            "text": "1. Numbered\r1. List \r"
        },
        {
            "text": "Link: [Bing](https://www.bing.com)"
        },
        {
            "text": "embedded image link: ![Duck on a rock](https://aka.ms/Fo983c)"
        },
        {
            "text": "`preformatted text`"
        },
        {
            "text": "Newlines (backslash n, backslash n):\n\nline a\n\nline b\n\nline c"
        },
        {
            "text": ">This is a blockquote"
        }
     ]
  }
}

```

---

## <a name="formatting-cards-with-html"></a><span data-ttu-id="3c9ce-226">Formatação de cartões com HTML</span><span class="sxs-lookup"><span data-stu-id="3c9ce-226">Formatting cards with HTML</span></span>

# <a name="html-formatting-o365-connector-cards"></a>[<span data-ttu-id="3c9ce-227">**Formatação HTML: Cartões de conector O365**</span><span class="sxs-lookup"><span data-stu-id="3c9ce-227">**HTML formatting: O365 Connector Cards**</span></span>](#tab/connector-html)

<span data-ttu-id="3c9ce-228">Os cartões conectores suportam a formatação limitada markdown e HTML.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-228">Connector cards support limited Markdown and HTML formatting.</span></span> <span data-ttu-id="3c9ce-229">Markdown é descrito na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-229">Markdown is described in the next section.</span></span>

| <span data-ttu-id="3c9ce-230">Style</span><span class="sxs-lookup"><span data-stu-id="3c9ce-230">Style</span></span> | <span data-ttu-id="3c9ce-231">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3c9ce-231">Example</span></span> | <span data-ttu-id="3c9ce-232">HTML</span><span class="sxs-lookup"><span data-stu-id="3c9ce-232">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="3c9ce-233">bold</span><span class="sxs-lookup"><span data-stu-id="3c9ce-233">bold</span></span> | <span data-ttu-id="3c9ce-234">**text**</span><span class="sxs-lookup"><span data-stu-id="3c9ce-234">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="3c9ce-235">italic</span><span class="sxs-lookup"><span data-stu-id="3c9ce-235">italic</span></span> | <span data-ttu-id="3c9ce-236">*text*</span><span class="sxs-lookup"><span data-stu-id="3c9ce-236">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="3c9ce-237">header (níveis 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="3c9ce-237">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="3c9ce-238">**Text**</span><span class="sxs-lookup"><span data-stu-id="3c9ce-238">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="3c9ce-239">strikethrough</span><span class="sxs-lookup"><span data-stu-id="3c9ce-239">strikethrough</span></span> | <span data-ttu-id="3c9ce-240">~~text~~</span><span class="sxs-lookup"><span data-stu-id="3c9ce-240">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="3c9ce-241">lista semordenagem</span><span class="sxs-lookup"><span data-stu-id="3c9ce-241">unordered list</span></span> | <ul><li><span data-ttu-id="3c9ce-242">texto</span><span class="sxs-lookup"><span data-stu-id="3c9ce-242">text</span></span></li><li><span data-ttu-id="3c9ce-243">texto</span><span class="sxs-lookup"><span data-stu-id="3c9ce-243">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="3c9ce-244">lista ordenada</span><span class="sxs-lookup"><span data-stu-id="3c9ce-244">ordered list</span></span> | <ol><li><span data-ttu-id="3c9ce-245">texto</span><span class="sxs-lookup"><span data-stu-id="3c9ce-245">text</span></span></li><li><span data-ttu-id="3c9ce-246">texto</span><span class="sxs-lookup"><span data-stu-id="3c9ce-246">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="3c9ce-247">texto pré-formatado</span><span class="sxs-lookup"><span data-stu-id="3c9ce-247">preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="3c9ce-248">blockquote</span><span class="sxs-lookup"><span data-stu-id="3c9ce-248">blockquote</span></span> | <blockquote><span data-ttu-id="3c9ce-249">texto</span><span class="sxs-lookup"><span data-stu-id="3c9ce-249">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="3c9ce-250">hiperlink</span><span class="sxs-lookup"><span data-stu-id="3c9ce-250">hyperlink</span></span> | [<span data-ttu-id="3c9ce-251">Bing</span><span class="sxs-lookup"><span data-stu-id="3c9ce-251">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="3c9ce-252">link de imagem</span><span class="sxs-lookup"><span data-stu-id="3c9ce-252">image link</span></span> | <img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img> | `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

<span data-ttu-id="3c9ce-253">Em cartões de conector, as linhas novas são renderizadas em HTML usando a `<p>` marca.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-253">In connector cards, newlines are rendered in HTML using the `<p>` tag.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards-using-html"></a><span data-ttu-id="3c9ce-254">Diferenças de dispositivos móveis e de área de trabalho para cartões de conector usando HTML</span><span class="sxs-lookup"><span data-stu-id="3c9ce-254">Mobile and desktop differences for connector cards using HTML</span></span>

<span data-ttu-id="3c9ce-255">Na área de trabalho, a formatação HTML para cartões de conector tem esta aparência:</span><span class="sxs-lookup"><span data-stu-id="3c9ce-255">On the desktop, HTML formatting for connector cards looks like this:</span></span>

![Formatação HTML para cartões de conector no cliente desktop](../../assets/images/cards/Connector-desktop-html-combined.png)

<span data-ttu-id="3c9ce-257">No iOS, a formatação HTML tem esta aparência:</span><span class="sxs-lookup"><span data-stu-id="3c9ce-257">On iOS, HTML formatting looks like this:</span></span>

![Formatação HTML para cartões de conector no cliente iOS](../../assets/images/cards/connector-iphone-html-combined-80.png)

<span data-ttu-id="3c9ce-259">Problemas:</span><span class="sxs-lookup"><span data-stu-id="3c9ce-259">Issues:</span></span>

* <span data-ttu-id="3c9ce-260">As imagens em linha não são renderizadas no iOS usando Markdown ou HTML em Cartões de Conector.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-260">Inline images are not rendered on iOS using either Markdown or HTML in Connector Cards.</span></span>
* <span data-ttu-id="3c9ce-261">O texto pré-formatado é renderizado, mas não tem um plano de fundo cinza.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-261">Preformatted text is rendered but does not have a gray background.</span></span>

<span data-ttu-id="3c9ce-262">No Android, a formatação HTML tem esta aparência:</span><span class="sxs-lookup"><span data-stu-id="3c9ce-262">On Android, HTML formatting looks like this:</span></span>

![Formatação HTML para cartões de conector no cliente Android](../../assets/images/cards/connector-android-html-combined.png)

### <a name="formatting-sample-for-html-connector-cards"></a><span data-ttu-id="3c9ce-264">Exemplo de formatação para cartões de conector HTML</span><span class="sxs-lookup"><span data-stu-id="3c9ce-264">Formatting sample for HTML Connector Cards</span></span>

``` json
{
  "contentType": "application/vnd.microsoft.teams.card.o365connector",
  "content": {
    "@type": "MessageCard",
    "@context": "https://schema.org/extensions",
    "summary": "Summary",
    "title": "Connector Card HTML formatting",
    "sections": [
        {
            "text": "This is some <strong>bold</strong> text"
        },
        {
            "text": "This is some <em>italic</em> text"
        },
        {
            "text": "This is some <strike>strikethrough</strike> text"
        },
        {
            "text": "<h1>Header 1</h1>\r<h2>Header 2</h2>\r <h3>Header 3</h3>"
        },
        {
            "text": "bullet list <ul><li>text</li><li>text</li></ul>"
        },
        {
            "text": "ordered list <ol><li>text</li><li>text</li></ol>"
        },
        {
            "text": "hyperlink <a href=\"https://www.bing.com/\">Bing</a>"
        },
        {
            "text": "embedded image <img src=\"https://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img>"
        },
        {
            "text": "preformatted text <pre>text</pre>"
        },
        {
            "text": "Paragraphs <p>Line a</p><p>Line b</p>"
        },
        {
            "text": "<blockquote>Blockquote text</blockquote>"
        }
     ]
  }
}

```

# <a name="html-formatting-hero-and-thumbnail-cards"></a>[<span data-ttu-id="3c9ce-265">**Formatação HTML: cartões de herói e miniatura**</span><span class="sxs-lookup"><span data-stu-id="3c9ce-265">**HTML Formatting: hero and thumbnail cards**</span></span>](#tab/simple-html)

<span data-ttu-id="3c9ce-266">As marcas HTML são suportadas para cartões simples, como o herói e o cartão de miniatura.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-266">HTML tags are supported for simple cards such as the hero and thumbnail card.</span></span> <span data-ttu-id="3c9ce-267">Não há suporte para markdown.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-267">Markdown is not supported.</span></span>

| <span data-ttu-id="3c9ce-268">Style</span><span class="sxs-lookup"><span data-stu-id="3c9ce-268">Style</span></span> | <span data-ttu-id="3c9ce-269">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3c9ce-269">Example</span></span> | <span data-ttu-id="3c9ce-270">HTML</span><span class="sxs-lookup"><span data-stu-id="3c9ce-270">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="3c9ce-271">bold</span><span class="sxs-lookup"><span data-stu-id="3c9ce-271">bold</span></span> | <span data-ttu-id="3c9ce-272">**text**</span><span class="sxs-lookup"><span data-stu-id="3c9ce-272">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="3c9ce-273">italic</span><span class="sxs-lookup"><span data-stu-id="3c9ce-273">italic</span></span> | <span data-ttu-id="3c9ce-274">*text*</span><span class="sxs-lookup"><span data-stu-id="3c9ce-274">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="3c9ce-275">header (níveis 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="3c9ce-275">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="3c9ce-276">**Text**</span><span class="sxs-lookup"><span data-stu-id="3c9ce-276">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="3c9ce-277">strikethrough</span><span class="sxs-lookup"><span data-stu-id="3c9ce-277">strikethrough</span></span> | <span data-ttu-id="3c9ce-278">~~text~~</span><span class="sxs-lookup"><span data-stu-id="3c9ce-278">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="3c9ce-279">lista semordenagem</span><span class="sxs-lookup"><span data-stu-id="3c9ce-279">unordered list</span></span> | <ul><li><span data-ttu-id="3c9ce-280">texto</span><span class="sxs-lookup"><span data-stu-id="3c9ce-280">text</span></span></li><li><span data-ttu-id="3c9ce-281">texto</span><span class="sxs-lookup"><span data-stu-id="3c9ce-281">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="3c9ce-282">lista ordenada</span><span class="sxs-lookup"><span data-stu-id="3c9ce-282">ordered list</span></span> | <ol><li><span data-ttu-id="3c9ce-283">texto</span><span class="sxs-lookup"><span data-stu-id="3c9ce-283">text</span></span></li><li><span data-ttu-id="3c9ce-284">texto</span><span class="sxs-lookup"><span data-stu-id="3c9ce-284">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="3c9ce-285">texto pré-formatado</span><span class="sxs-lookup"><span data-stu-id="3c9ce-285">preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="3c9ce-286">blockquote</span><span class="sxs-lookup"><span data-stu-id="3c9ce-286">blockquote</span></span> | <blockquote><span data-ttu-id="3c9ce-287">texto</span><span class="sxs-lookup"><span data-stu-id="3c9ce-287">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="3c9ce-288">hiperlink</span><span class="sxs-lookup"><span data-stu-id="3c9ce-288">hyperlink</span></span> | [<span data-ttu-id="3c9ce-289">Bing</span><span class="sxs-lookup"><span data-stu-id="3c9ce-289">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="3c9ce-290">link de imagem</span><span class="sxs-lookup"><span data-stu-id="3c9ce-290">image link</span></span> |<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>| `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

### <a name="mobile-and-desktop-differences-for-simple-cards"></a><span data-ttu-id="3c9ce-291">Diferenças de dispositivos móveis e de área de trabalho para cartões simples</span><span class="sxs-lookup"><span data-stu-id="3c9ce-291">Mobile and desktop differences for simple cards</span></span>

<span data-ttu-id="3c9ce-292">Devido às diferenças de resolução entre a área de trabalho e a plataforma móvel, a formatação é diferente entre a área de trabalho e a versão móvel do Teams.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-292">Because of resolution differences between the desktop and mobile platform, formatting is different between the desktop and the mobile version of Teams.</span></span>

<span data-ttu-id="3c9ce-293">Na área de trabalho, a formatação HTML aparece assim:</span><span class="sxs-lookup"><span data-stu-id="3c9ce-293">On the desktop, HTML formatting appears like this:</span></span>

![Formatação HTML no cliente desktop](../../assets/images/cards/card-formatting-xml-desktop-v2.png)

<span data-ttu-id="3c9ce-295">No iOS, a formatação HTML aparece assim:</span><span class="sxs-lookup"><span data-stu-id="3c9ce-295">On iOS, HTML formatting appears like this:</span></span>

![Formatação HTML no cliente iOS](../../assets/images/cards/card-formatting-xml-mobile-v2.png)

<span data-ttu-id="3c9ce-297">Problemas:</span><span class="sxs-lookup"><span data-stu-id="3c9ce-297">Issues:</span></span>

* <span data-ttu-id="3c9ce-298">A formatação de caracteres como negrito e itálico não é renderizada no iOS.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-298">Character formatting like bold and italic are not rendered on iOS.</span></span>

<span data-ttu-id="3c9ce-299">No Android, a formatação HTML aparece assim:</span><span class="sxs-lookup"><span data-stu-id="3c9ce-299">On Android, HTML formatting appears like this:</span></span>

![Formatação HTML no cliente Android](../../assets/images/cards/card-formatting-xml-android-60.png)

<span data-ttu-id="3c9ce-301">Formatação de caracteres como negrito e exibição itálico corretamente no Android.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-301">Character formatting like bold and italic display correctly on Android.</span></span>

### <a name="formatting-sample-for-html-formatting-in-simple-cards"></a><span data-ttu-id="3c9ce-302">Exemplo de formatação para formatação HTML em cartões simples</span><span class="sxs-lookup"><span data-stu-id="3c9ce-302">Formatting sample for HTML formatting in simple cards</span></span>

<span data-ttu-id="3c9ce-303">Essas capturas de tela foram criadas usando o Teams AppStudio, onde a propriedade de texto de um cartão de herói foi definida como a cadeia de caracteres a seguir.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-303">These screenshots were created using Teams AppStudio, where the text property of a hero card was set to the following string.</span></span> <span data-ttu-id="3c9ce-304">Você pode testar a formatação em seus próprios cartões modificando esse código.</span><span class="sxs-lookup"><span data-stu-id="3c9ce-304">You can test formatting in your own cards by modifying this code.</span></span>

`<p>bold: <strong>Bold Text</strong></p><p>italic: <em>Italic Text</em></p><p>strikethrough: <strike>Strikethrough text</strike></p><h1>Header 1</h1><h2>Header 2</h2><h3>Header 3</h3><p>bullet list: <ul><li>text</li><li>text</li></ul></p><p>ordered list: <ol><li>text</li><li>text</li></ol></p><pre>preformatted text</pre><blockquote>blockquote text</blockquote></p><p>hyperlink: <a href=\"https://www.bing.com/\">Bing</a></p><p>embedded image: <img src=\"https://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img></p>`

---
