---
title: Formatação de texto em cartões
description: Descreve a formatação de texto do cartão no Microsoft Teams
keywords: formato de cartões de bots da equipe
ms.date: 03/29/2018
ms.openlocfilehash: e857a1250593c135aa23ad38a571a5561bb91431
ms.sourcegitcommit: b9e8839858ea8e9e33fe5e20e14bbe86c75fd510
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "44210684"
---
# <a name="format-cards-in-teams"></a><span data-ttu-id="f1a86-104">Formatar cartões no Teams</span><span class="sxs-lookup"><span data-stu-id="f1a86-104">Format cards in Teams</span></span>

<span data-ttu-id="f1a86-105">Você pode adicionar formatação de Rich Text aos seus cartões usando redução ou HTML, dependendo do tipo de cartão.</span><span class="sxs-lookup"><span data-stu-id="f1a86-105">You can add rich text formatting to your cards using either Markdown or HTML, depending on the card type.</span></span>

<span data-ttu-id="f1a86-106">Os cartões dão suporte à formatação somente na propriedade Text, e não nas propriedades Title ou subtítulo.</span><span class="sxs-lookup"><span data-stu-id="f1a86-106">Cards support formatting in the text property only, not in the title or subtitle properties.</span></span> <span data-ttu-id="f1a86-107">A formatação pode ser especificada usando um subconjunto de formatação XML (HTML) ou redução, dependendo do tipo de cartão.</span><span class="sxs-lookup"><span data-stu-id="f1a86-107">Formatting can be specified using a subset of XML (HTML) formatting, or Markdown depending on card type.</span></span> <span data-ttu-id="f1a86-108">É recomendável usar os cartões adaptáveis de desenvolvimento atuais e futuros usando a formatação de redução.</span><span class="sxs-lookup"><span data-stu-id="f1a86-108">For current and future development Adaptive cards using Markdown formatting is recommended.</span></span>

<span data-ttu-id="f1a86-109">O suporte à formatação difere entre diferentes tipos de cartão, e a renderização do cartão pode diferir ligeiramente entre a área de trabalho e os clientes do Mobile Teams, bem como o Microsoft Teams no navegador da área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="f1a86-109">Formatting support differs between different card types, and rendering of the card can differ slightly between the desktop and the mobile Teams clients, as well as Teams in the desktop browser.</span></span>

<span data-ttu-id="f1a86-110">Você pode incluir uma imagem embutida em qualquer placa do teams.</span><span class="sxs-lookup"><span data-stu-id="f1a86-110">You can include an inline image with any Teams card.</span></span> <span data-ttu-id="f1a86-111">As imagens são formatadas como `.png` , `.jpg` ou `.gif` arquivos, e não devem exceder 1024 × 1024 PX ou 1 MB.</span><span class="sxs-lookup"><span data-stu-id="f1a86-111">Images an be formatted as  `.png`, `.jpg`, or `.gif` files and must not exceed 1024 ×1024 px or 1 MB.</span></span> <span data-ttu-id="f1a86-112">GIF animado não é oficialmente suportado.</span><span class="sxs-lookup"><span data-stu-id="f1a86-112">Animated GIF is not officially supported.</span></span> <span data-ttu-id="f1a86-113">*Consulte* [referência de cartões](./cards-reference.md#inline-card-images)</span><span class="sxs-lookup"><span data-stu-id="f1a86-113">*See* [Cards reference](./cards-reference.md#inline-card-images)</span></span>

## <a name="formatting-cards-with-markdown"></a><span data-ttu-id="f1a86-114">Formatando cartões com redução</span><span class="sxs-lookup"><span data-stu-id="f1a86-114">Formatting cards with Markdown</span></span>

<span data-ttu-id="f1a86-115">Há dois tipos de cartões que dão suporte à redução no Microsoft Teams:</span><span class="sxs-lookup"><span data-stu-id="f1a86-115">There are two card types that support Markdown in Teams:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="f1a86-116">**Cartões adaptáveis**: a redução é suportada no campo de cartão adaptável `Textblock` , bem como `Fact.Title` e `Fact.Value` .</span><span class="sxs-lookup"><span data-stu-id="f1a86-116">**Adaptive Cards**: Markdown is supported in Adaptive Card `Textblock` field, as well as `Fact.Title` and `Fact.Value`.</span></span> <span data-ttu-id="f1a86-117">O HTML não é suportado em cartões adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="f1a86-117">HTML is not supported in adaptive cards.</span></span>
> * <span data-ttu-id="f1a86-118">**Cartões de conector do O365**: redução e HTML limitado são suportados nos cartões de conector do Office 365 nos campos de texto.</span><span class="sxs-lookup"><span data-stu-id="f1a86-118">**O365 Connector Cards**: Markdown and limited HTML is supported in Office 365 Connector cards in the text fields.</span></span>

# <a name="markdown-formatting-adaptive-cards"></a>[<span data-ttu-id="f1a86-119">**Formatação de redução: cartões adaptáveis**</span><span class="sxs-lookup"><span data-stu-id="f1a86-119">**Markdown formatting: Adaptive Cards**</span></span>](#tab/adaptive-md)

 <span data-ttu-id="f1a86-120">Os estilos suportados para `Textblock` `Fact.Title` e `Fact.Value` são:</span><span class="sxs-lookup"><span data-stu-id="f1a86-120">The supported styles for `Textblock`, `Fact.Title` and `Fact.Value` are:</span></span>

| <span data-ttu-id="f1a86-121">Estilo</span><span class="sxs-lookup"><span data-stu-id="f1a86-121">Style</span></span> | <span data-ttu-id="f1a86-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f1a86-122">Example</span></span> | <span data-ttu-id="f1a86-123">Markdown</span><span class="sxs-lookup"><span data-stu-id="f1a86-123">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="f1a86-124">bold</span><span class="sxs-lookup"><span data-stu-id="f1a86-124">bold</span></span> | <span data-ttu-id="f1a86-125">**Negrito**</span><span class="sxs-lookup"><span data-stu-id="f1a86-125">**Bold**</span></span> | ```**Bold**``` |
| <span data-ttu-id="f1a86-126">italic</span><span class="sxs-lookup"><span data-stu-id="f1a86-126">italic</span></span> | <span data-ttu-id="f1a86-127">_Itálico_</span><span class="sxs-lookup"><span data-stu-id="f1a86-127">_Italic_</span></span> | ```_Italic_``` |
| <span data-ttu-id="f1a86-128">lista não ordenada</span><span class="sxs-lookup"><span data-stu-id="f1a86-128">unordered list</span></span> | <ul><li><span data-ttu-id="f1a86-129">texto</span><span class="sxs-lookup"><span data-stu-id="f1a86-129">text</span></span></li><li><span data-ttu-id="f1a86-130">texto</span><span class="sxs-lookup"><span data-stu-id="f1a86-130">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="f1a86-131">lista ordenada</span><span class="sxs-lookup"><span data-stu-id="f1a86-131">ordered list</span></span> | <ol><li><span data-ttu-id="f1a86-132">texto</span><span class="sxs-lookup"><span data-stu-id="f1a86-132">text</span></span></li><li><span data-ttu-id="f1a86-133">texto</span><span class="sxs-lookup"><span data-stu-id="f1a86-133">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="f1a86-134">Hiperlinks</span><span class="sxs-lookup"><span data-stu-id="f1a86-134">Hyperlinks</span></span> |[<span data-ttu-id="f1a86-135">Bing</span><span class="sxs-lookup"><span data-stu-id="f1a86-135">Bing</span></span>](https://www.bing.com/)| ```[Title](url)``` |

<span data-ttu-id="f1a86-136">Não há suporte para as seguintes marcas de redução:</span><span class="sxs-lookup"><span data-stu-id="f1a86-136">The following Markdown tags are not supported:</span></span>

* <span data-ttu-id="f1a86-137">Cabeçalhos</span><span class="sxs-lookup"><span data-stu-id="f1a86-137">Headers</span></span>
* <span data-ttu-id="f1a86-138">Tabelas</span><span class="sxs-lookup"><span data-stu-id="f1a86-138">Tables</span></span>
* <span data-ttu-id="f1a86-139">Imagens</span><span class="sxs-lookup"><span data-stu-id="f1a86-139">Images</span></span>
* <span data-ttu-id="f1a86-140">Texto pré-formatado</span><span class="sxs-lookup"><span data-stu-id="f1a86-140">Preformatted text</span></span>
* <span data-ttu-id="f1a86-141">Blockquote</span><span class="sxs-lookup"><span data-stu-id="f1a86-141">Blockquotes</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f1a86-142">Os cartões adaptáveis não oferecem suporte à formatação HTML.</span><span class="sxs-lookup"><span data-stu-id="f1a86-142">Adaptive cards do not support HTML formatting.</span></span>

### <a name="newlines-for-adaptive-cards"></a><span data-ttu-id="f1a86-143">Novas linhas para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="f1a86-143">Newlines for Adaptive Cards</span></span>

<span data-ttu-id="f1a86-144">Nas listas, você pode usar `\r` as `\n` sequências de escape ou de saída para novas linhas.</span><span class="sxs-lookup"><span data-stu-id="f1a86-144">In lists you can use the `\r` or `\n` escape sequences for newlines.</span></span> <span data-ttu-id="f1a86-145">Usar `\n\n` em uma lista fará com que o próximo elemento na lista seja recuado.</span><span class="sxs-lookup"><span data-stu-id="f1a86-145">Using `\n\n` in a list will cause the next element in the list to be indented.</span></span> <span data-ttu-id="f1a86-146">Se você precisar de novas linhas em qualquer lugar no TextBlock, use `\n\n` .</span><span class="sxs-lookup"><span data-stu-id="f1a86-146">If you need newlines elsewhere in the textblock, use `\n\n`.</span></span>

### <a name="mobile-and-desktop-differences-for-adaptive-cards"></a><span data-ttu-id="f1a86-147">Diferenças móveis e de área de trabalho para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="f1a86-147">Mobile and desktop differences for Adaptive Cards</span></span>

<span data-ttu-id="f1a86-148">A formatação é um pouco diferente entre a área de trabalho e as versões móveis do teams.</span><span class="sxs-lookup"><span data-stu-id="f1a86-148">Formatting is slightly different between the desktop and the mobile versions of Teams.</span></span>

<span data-ttu-id="f1a86-149">Na área de trabalho, a formatação de redução de cartão adaptável aparece como esta nos dois navegadores da Web e no aplicativo cliente do teams:</span><span class="sxs-lookup"><span data-stu-id="f1a86-149">On the desktop, Adaptive Card Markdown formatting appears like this in both web browsers and in the Teams client application:</span></span>

![Formatação de redução de cartão adaptável no cliente de desktop](../../assets/images/cards/Adaptive-markdown-desktop-client.png)

<span data-ttu-id="f1a86-151">No iOS, a formatação de redução de cartão adaptável aparece da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="f1a86-151">On iOS, Adaptive Card Markdown formatting appears like this:</span></span>

![Formatação de redução de cartão adaptável no iOS](../../assets/images/cards/Adaptive-markdown-iOS-75.png)

<span data-ttu-id="f1a86-153">No Android, a formatação de redução de cartão adaptável aparece da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="f1a86-153">On Android, Adaptive Card Markdown formatting appears like this:</span></span>

![Formatação de redução de cartão adaptável no Android](../../assets/images/cards/Adaptive-markdown-Android.png)

### <a name="more-information-on-adaptive-cards"></a><span data-ttu-id="f1a86-155">Mais informações sobre cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="f1a86-155">More information on Adaptive Cards</span></span>

<span data-ttu-id="f1a86-156">[Recursos de texto em cartões adaptáveis](/adaptive-cards/create/textfeatures) Os recursos de data e localização mencionados neste tópico não têm suporte no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="f1a86-156">[Text features in Adaptive cards](/adaptive-cards/create/textfeatures) The date and localization features mentioned in this topic are not supported in Teams.</span></span>

### <a name="formatting-sample-for-adaptive-cards"></a><span data-ttu-id="f1a86-157">Exemplo de formatação para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="f1a86-157">Formatting sample for Adaptive cards</span></span>

``` json
{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
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
            "text": "Check out [Adaptive Cards](http://adaptivecards.io)"
        }
    ]
}
```

### <a name="mention-support-within-adaptive-cards-v12"></a><span data-ttu-id="f1a86-158">Mencione o suporte de cartões adaptáveis v 1.2</span><span class="sxs-lookup"><span data-stu-id="f1a86-158">Mention support within Adaptive cards v1.2</span></span>

<span data-ttu-id="f1a86-159">Mencionadas com base no cartão são compatíveis com clientes Web, desktop e dispositivos móveis.</span><span class="sxs-lookup"><span data-stu-id="f1a86-159">Card based mentions are supported in Web, Desktop and mobile clients.</span></span> <span data-ttu-id="f1a86-160">Você pode adicionar @ menção dentro de um corpo de cartão adaptável para bots e respostas de extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="f1a86-160">You can add @ mentions within an adaptive card body for bots and messaging extension responses.</span></span>  <span data-ttu-id="f1a86-161">Para adicionar @ mençãos em cartões, siga a mesma lógica de notificação e renderização que as [mencionadas por mensagem em conversas de chat de grupo e canal](../../bots/how-to/conversations/channel-and-group-conversations.md#working-with-mentions ).</span><span class="sxs-lookup"><span data-stu-id="f1a86-161">To add @ mentions in cards, follow the same notification logic and rendering as that of message based [mentions in channel and group chat conversations](../../bots/how-to/conversations/channel-and-group-conversations.md#working-with-mentions ).</span></span>

<span data-ttu-id="f1a86-162">Os bots e as extensões de mensagens podem incluir menção dentro do conteúdo do cartão em elementos [TextBlock](https://adaptivecards.io/explorer/TextBlock.html) e [FactSet](https://adaptivecards.io/explorer/FactSet.html) .</span><span class="sxs-lookup"><span data-stu-id="f1a86-162">Bots and messaging extensions can include mentions within the card content in [TextBlock](https://adaptivecards.io/explorer/TextBlock.html) and [FactSet](https://adaptivecards.io/explorer/FactSet.html) elements.</span></span>

> [!NOTE]
><span data-ttu-id="f1a86-163">Os [elementos de mídia](https://adaptivecards.io/explorer/Media.html) atualmente não têm suporte em cartões adaptáveis v 1.2 na plataforma do teams.</span><span class="sxs-lookup"><span data-stu-id="f1a86-163">[Media elements](https://adaptivecards.io/explorer/Media.html) are currently not supported in Adaptive cards v1.2 on the Teams platform.</span></span>

### <a name="constructing-mentions"></a><span data-ttu-id="f1a86-164">Como criar menção</span><span class="sxs-lookup"><span data-stu-id="f1a86-164">Constructing mentions</span></span>

<span data-ttu-id="f1a86-165">Para incluir uma menção em um cartão adaptável, seu aplicativo precisa incluir os seguintes elementos</span><span class="sxs-lookup"><span data-stu-id="f1a86-165">To include a mention in an Adaptive Card your app needs to include the following elements</span></span>

* <span data-ttu-id="f1a86-166">`<at>username</at>`nos elementos de cartão adaptável com suporte</span><span class="sxs-lookup"><span data-stu-id="f1a86-166">`<at>username</at>` in the supported adaptive card elements</span></span>
* <span data-ttu-id="f1a86-167">O `mention` objeto dentro de uma `msteams` propriedade no conteúdo do cartão, que inclui a ID de usuário do Team do usuário que está sendo mencionado</span><span class="sxs-lookup"><span data-stu-id="f1a86-167">The `mention` object inside of an `msteams` property in the card content, which includes the Teams user id of the user being mentioned</span></span>

### <a name="sample-adaptive-card-with-a-mention"></a><span data-ttu-id="f1a86-168">Cartão adaptável de amostra com menção</span><span class="sxs-lookup"><span data-stu-id="f1a86-168">Sample Adaptive card with a mention</span></span>

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
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
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

# <a name="markdown-formatting-o365-connector-cards"></a>[<span data-ttu-id="f1a86-169">**Formatação de redução: cartões de conector do O365**</span><span class="sxs-lookup"><span data-stu-id="f1a86-169">**Markdown formatting: O365 Connector Cards**</span></span>](#tab/connector-md)

<span data-ttu-id="f1a86-170">Os cartões de conector dão suporte à redução limitada e à formatação HTML.</span><span class="sxs-lookup"><span data-stu-id="f1a86-170">Connector cards support limited Markdown and HTML formatting.</span></span> <span data-ttu-id="f1a86-171">O suporte a HTML é descrito na última seção.</span><span class="sxs-lookup"><span data-stu-id="f1a86-171">HTML support is described in the last section.</span></span>

| <span data-ttu-id="f1a86-172">Estilo</span><span class="sxs-lookup"><span data-stu-id="f1a86-172">Style</span></span> | <span data-ttu-id="f1a86-173">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f1a86-173">Example</span></span> | <span data-ttu-id="f1a86-174">Markdown</span><span class="sxs-lookup"><span data-stu-id="f1a86-174">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="f1a86-175">bold</span><span class="sxs-lookup"><span data-stu-id="f1a86-175">bold</span></span> | <span data-ttu-id="f1a86-176">**text**</span><span class="sxs-lookup"><span data-stu-id="f1a86-176">**text**</span></span> | `**text**` |
| <span data-ttu-id="f1a86-177">italic</span><span class="sxs-lookup"><span data-stu-id="f1a86-177">italic</span></span> | <span data-ttu-id="f1a86-178">*text*</span><span class="sxs-lookup"><span data-stu-id="f1a86-178">*text*</span></span> | `*text*` |
| <span data-ttu-id="f1a86-179">cabeçalho (níveis 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="f1a86-179">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="f1a86-180">**Text**</span><span class="sxs-lookup"><span data-stu-id="f1a86-180">**Text**</span></span> | `### Text`|
| <span data-ttu-id="f1a86-181">tachado</span><span class="sxs-lookup"><span data-stu-id="f1a86-181">strikethrough</span></span> | <span data-ttu-id="f1a86-182">~~text~~</span><span class="sxs-lookup"><span data-stu-id="f1a86-182">~~text~~</span></span> | `~~text~~` |
| <span data-ttu-id="f1a86-183">lista não ordenada</span><span class="sxs-lookup"><span data-stu-id="f1a86-183">unordered list</span></span> | <ul><li><span data-ttu-id="f1a86-184">texto</span><span class="sxs-lookup"><span data-stu-id="f1a86-184">text</span></span></li><li><span data-ttu-id="f1a86-185">texto</span><span class="sxs-lookup"><span data-stu-id="f1a86-185">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="f1a86-186">lista ordenada</span><span class="sxs-lookup"><span data-stu-id="f1a86-186">ordered list</span></span> | <ol><li><span data-ttu-id="f1a86-187">texto</span><span class="sxs-lookup"><span data-stu-id="f1a86-187">text</span></span></li><li><span data-ttu-id="f1a86-188">texto</span><span class="sxs-lookup"><span data-stu-id="f1a86-188">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="f1a86-189">texto pré-formatado</span><span class="sxs-lookup"><span data-stu-id="f1a86-189">preformatted text</span></span> | `text` | ``preformatted text`` |
| <span data-ttu-id="f1a86-190">blockquote</span><span class="sxs-lookup"><span data-stu-id="f1a86-190">blockquote</span></span> | <span data-ttu-id="f1a86-191">>texto blockquote</span><span class="sxs-lookup"><span data-stu-id="f1a86-191">>blockquote text</span></span> | `>blockquote text` |
| <span data-ttu-id="f1a86-192">hiperlink</span><span class="sxs-lookup"><span data-stu-id="f1a86-192">hyperlink</span></span> | [<span data-ttu-id="f1a86-193">Bing</span><span class="sxs-lookup"><span data-stu-id="f1a86-193">Bing</span></span>](https://www.bing.com/) | `[Bing](https://www.bing.com/)` |
| <span data-ttu-id="f1a86-194">link de imagem</span><span class="sxs-lookup"><span data-stu-id="f1a86-194">image link</span></span> |![Pato em uma pedra](https://aka.ms/Fo983c) | `![Duck](https://aka.ms/Fo983c)` |

<span data-ttu-id="f1a86-196">Nos cartões conectores, as novas linhas são renderizadas para `\n\n` , mas não para `\n` ou `\r` .</span><span class="sxs-lookup"><span data-stu-id="f1a86-196">In connector cards, newlines are rendered for `\n\n`, but not for `\n` or `\r`.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards-using-markdown"></a><span data-ttu-id="f1a86-197">Diferenças de dispositivos móveis e de área de trabalho para cartões de conexão usando redução</span><span class="sxs-lookup"><span data-stu-id="f1a86-197">Mobile and desktop differences for connector cards using Markdown</span></span>

<span data-ttu-id="f1a86-198">Na área de trabalho, a redução da formatação de cartões de conector tem a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="f1a86-198">On the desktop, Markdown formatting for connector cards looks like this:</span></span>

![Redução da formatação de cartões de conector no cliente de desktop](../../assets/images/cards/connector-desktop-markdown-combined.png)

<span data-ttu-id="f1a86-200">No iOS, a redução da formatação de cartões de conector tem a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="f1a86-200">On iOS, Markdown formatting for connector cards looks like this:</span></span>

![Redução da formatação de cartões de conector no cliente iOS](../../assets/images/cards/connector-iphone-markdown-combined-80.png)

<span data-ttu-id="f1a86-202">Problemas</span><span class="sxs-lookup"><span data-stu-id="f1a86-202">Issues:</span></span>

* <span data-ttu-id="f1a86-203">O cliente iOS para Teams não renderiza a redução ou as imagens embutidas HTML nos cartões de conector.</span><span class="sxs-lookup"><span data-stu-id="f1a86-203">The iOS client for Teams does not render Markdown or HTML inline images in Connector Cards.</span></span>
* <span data-ttu-id="f1a86-204">Blockquotes são renderizados como recuados, mas sem um plano de fundo cinza.</span><span class="sxs-lookup"><span data-stu-id="f1a86-204">Blockquotes are rendered as indented but without a gray background.</span></span>

<span data-ttu-id="f1a86-205">No Android, a redução da formatação de cartões de conector tem a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="f1a86-205">On Android, Markdown formatting for connector cards looks like this:</span></span>

![Redução da formatação de cartões de conector no cliente Android](../../assets/images/cards/connector-android-markdown-combined.png)

### <a name="formatting-example-for-markdown-connector-cards"></a><span data-ttu-id="f1a86-207">Exemplo de formatação para redução de cartões de conector</span><span class="sxs-lookup"><span data-stu-id="f1a86-207">Formatting example for Markdown Connector Cards</span></span>

``` json
{
  "contentType": "application/vnd.microsoft.teams.card.o365connector",
  "content": {
    "@type": "MessageCard",
    "@context": "http://schema.org/extensions",
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
            "text": "embedded image link: ![Duck on a rock](http://aka.ms/Fo983c)"
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

## <a name="formatting-cards-with-html"></a><span data-ttu-id="f1a86-208">Formatando cartões com HTML</span><span class="sxs-lookup"><span data-stu-id="f1a86-208">Formatting cards with HTML</span></span>

# <a name="html-formatting-o365-connector-cards"></a>[<span data-ttu-id="f1a86-209">**Formatação HTML: cartões de conector do O365**</span><span class="sxs-lookup"><span data-stu-id="f1a86-209">**HTML formatting: O365 Connector Cards**</span></span>](#tab/connector-html)

<span data-ttu-id="f1a86-210">Os cartões de conector dão suporte à redução limitada e à formatação HTML.</span><span class="sxs-lookup"><span data-stu-id="f1a86-210">Connector cards support limited Markdown and HTML formatting.</span></span> <span data-ttu-id="f1a86-211">A redução é descrita na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="f1a86-211">Markdown is described in the next section.</span></span>

| <span data-ttu-id="f1a86-212">Estilo</span><span class="sxs-lookup"><span data-stu-id="f1a86-212">Style</span></span> | <span data-ttu-id="f1a86-213">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f1a86-213">Example</span></span> | <span data-ttu-id="f1a86-214">HTML</span><span class="sxs-lookup"><span data-stu-id="f1a86-214">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="f1a86-215">bold</span><span class="sxs-lookup"><span data-stu-id="f1a86-215">bold</span></span> | <span data-ttu-id="f1a86-216">**text**</span><span class="sxs-lookup"><span data-stu-id="f1a86-216">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="f1a86-217">italic</span><span class="sxs-lookup"><span data-stu-id="f1a86-217">italic</span></span> | <span data-ttu-id="f1a86-218">*text*</span><span class="sxs-lookup"><span data-stu-id="f1a86-218">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="f1a86-219">cabeçalho (níveis 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="f1a86-219">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="f1a86-220">**Text**</span><span class="sxs-lookup"><span data-stu-id="f1a86-220">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="f1a86-221">tachado</span><span class="sxs-lookup"><span data-stu-id="f1a86-221">strikethrough</span></span> | <span data-ttu-id="f1a86-222">~~text~~</span><span class="sxs-lookup"><span data-stu-id="f1a86-222">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="f1a86-223">lista não ordenada</span><span class="sxs-lookup"><span data-stu-id="f1a86-223">unordered list</span></span> | <ul><li><span data-ttu-id="f1a86-224">texto</span><span class="sxs-lookup"><span data-stu-id="f1a86-224">text</span></span></li><li><span data-ttu-id="f1a86-225">texto</span><span class="sxs-lookup"><span data-stu-id="f1a86-225">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="f1a86-226">lista ordenada</span><span class="sxs-lookup"><span data-stu-id="f1a86-226">ordered list</span></span> | <ol><li><span data-ttu-id="f1a86-227">texto</span><span class="sxs-lookup"><span data-stu-id="f1a86-227">text</span></span></li><li><span data-ttu-id="f1a86-228">texto</span><span class="sxs-lookup"><span data-stu-id="f1a86-228">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="f1a86-229">texto pré-formatado</span><span class="sxs-lookup"><span data-stu-id="f1a86-229">preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="f1a86-230">blockquote</span><span class="sxs-lookup"><span data-stu-id="f1a86-230">blockquote</span></span> | <blockquote><span data-ttu-id="f1a86-231">texto</span><span class="sxs-lookup"><span data-stu-id="f1a86-231">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="f1a86-232">hiperlink</span><span class="sxs-lookup"><span data-stu-id="f1a86-232">hyperlink</span></span> | [<span data-ttu-id="f1a86-233">Bing</span><span class="sxs-lookup"><span data-stu-id="f1a86-233">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="f1a86-234">link de imagem</span><span class="sxs-lookup"><span data-stu-id="f1a86-234">image link</span></span> | <img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img> | `<img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

<span data-ttu-id="f1a86-235">Em cartões de conector, as novas linhas são renderizadas em HTML usando a `<p>` marca.</span><span class="sxs-lookup"><span data-stu-id="f1a86-235">In connector cards, newlines are rendered in HTML using the `<p>` tag.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards-using-html"></a><span data-ttu-id="f1a86-236">Diferenças móveis e de área de trabalho para cartões de conexão usando HTML</span><span class="sxs-lookup"><span data-stu-id="f1a86-236">Mobile and desktop differences for connector cards using HTML</span></span>

<span data-ttu-id="f1a86-237">Na área de trabalho, a formatação HTML para cartões de conector tem a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="f1a86-237">On the desktop, HTML formatting for connector cards looks like this:</span></span>

![Formatação HTML para cartões de conector no cliente de desktop](../../assets/images/cards/Connector-desktop-html-combined.png)

<span data-ttu-id="f1a86-239">No iOS, a formatação HTML tem a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="f1a86-239">On iOS, HTML formatting looks like this:</span></span>

![Formatação HTML para cartões de conector no cliente iOS](../../assets/images/cards/connector-iphone-html-combined-80.png)

<span data-ttu-id="f1a86-241">Problemas</span><span class="sxs-lookup"><span data-stu-id="f1a86-241">Issues:</span></span>

* <span data-ttu-id="f1a86-242">As imagens embutidas não são renderizadas no iOS usando a redução ou HTML em cartões de conexão.</span><span class="sxs-lookup"><span data-stu-id="f1a86-242">Inline images are not rendered on iOS using either Markdown or HTML in Connector Cards.</span></span>
* <span data-ttu-id="f1a86-243">O texto pré-formatado é renderizado, mas não tem um plano de fundo cinza.</span><span class="sxs-lookup"><span data-stu-id="f1a86-243">Preformatted text is rendered but does not have a gray background.</span></span>

<span data-ttu-id="f1a86-244">No Android, a formatação HTML tem a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="f1a86-244">On Android, HTML formatting looks like this:</span></span>

![Formatação HTML para cartões de conector no cliente Android](../../assets/images/cards/connector-android-html-combined.png)

### <a name="formatting-sample-for-html-connector-cards"></a><span data-ttu-id="f1a86-246">Exemplo de formatação para cartões de conexão HTML</span><span class="sxs-lookup"><span data-stu-id="f1a86-246">Formatting sample for HTML Connector Cards</span></span>

``` json
{
  "contentType": "application/vnd.microsoft.teams.card.o365connector",
  "content": {
    "@type": "MessageCard",
    "@context": "http://schema.org/extensions",
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
            "text": "embedded image <img src=\"http://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img>"
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

# <a name="html-formatting-hero-and-thumbnail-cards"></a>[<span data-ttu-id="f1a86-247">**Formatação HTML: herói e cartões de miniatura**</span><span class="sxs-lookup"><span data-stu-id="f1a86-247">**HTML Formatting: hero and thumbnail cards**</span></span>](#tab/simple-html)

<span data-ttu-id="f1a86-248">Marcas HTML têm suporte para cartões simples como o herói e o cartão de miniatura.</span><span class="sxs-lookup"><span data-stu-id="f1a86-248">HTML tags are supported for simple cards such as the hero and thumbnail card.</span></span> <span data-ttu-id="f1a86-249">Não há suporte para redução.</span><span class="sxs-lookup"><span data-stu-id="f1a86-249">Markdown is not supported.</span></span>

| <span data-ttu-id="f1a86-250">Estilo</span><span class="sxs-lookup"><span data-stu-id="f1a86-250">Style</span></span> | <span data-ttu-id="f1a86-251">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f1a86-251">Example</span></span> | <span data-ttu-id="f1a86-252">HTML</span><span class="sxs-lookup"><span data-stu-id="f1a86-252">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="f1a86-253">bold</span><span class="sxs-lookup"><span data-stu-id="f1a86-253">bold</span></span> | <span data-ttu-id="f1a86-254">**text**</span><span class="sxs-lookup"><span data-stu-id="f1a86-254">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="f1a86-255">italic</span><span class="sxs-lookup"><span data-stu-id="f1a86-255">italic</span></span> | <span data-ttu-id="f1a86-256">*text*</span><span class="sxs-lookup"><span data-stu-id="f1a86-256">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="f1a86-257">cabeçalho (níveis 1 &ndash; 3)</span><span class="sxs-lookup"><span data-stu-id="f1a86-257">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="f1a86-258">**Text**</span><span class="sxs-lookup"><span data-stu-id="f1a86-258">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="f1a86-259">tachado</span><span class="sxs-lookup"><span data-stu-id="f1a86-259">strikethrough</span></span> | <span data-ttu-id="f1a86-260">~~text~~</span><span class="sxs-lookup"><span data-stu-id="f1a86-260">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="f1a86-261">lista não ordenada</span><span class="sxs-lookup"><span data-stu-id="f1a86-261">unordered list</span></span> | <ul><li><span data-ttu-id="f1a86-262">texto</span><span class="sxs-lookup"><span data-stu-id="f1a86-262">text</span></span></li><li><span data-ttu-id="f1a86-263">texto</span><span class="sxs-lookup"><span data-stu-id="f1a86-263">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="f1a86-264">lista ordenada</span><span class="sxs-lookup"><span data-stu-id="f1a86-264">ordered list</span></span> | <ol><li><span data-ttu-id="f1a86-265">texto</span><span class="sxs-lookup"><span data-stu-id="f1a86-265">text</span></span></li><li><span data-ttu-id="f1a86-266">texto</span><span class="sxs-lookup"><span data-stu-id="f1a86-266">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="f1a86-267">texto pré-formatado</span><span class="sxs-lookup"><span data-stu-id="f1a86-267">preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="f1a86-268">blockquote</span><span class="sxs-lookup"><span data-stu-id="f1a86-268">blockquote</span></span> | <blockquote><span data-ttu-id="f1a86-269">texto</span><span class="sxs-lookup"><span data-stu-id="f1a86-269">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="f1a86-270">hiperlink</span><span class="sxs-lookup"><span data-stu-id="f1a86-270">hyperlink</span></span> | [<span data-ttu-id="f1a86-271">Bing</span><span class="sxs-lookup"><span data-stu-id="f1a86-271">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="f1a86-272">link de imagem</span><span class="sxs-lookup"><span data-stu-id="f1a86-272">image link</span></span> |<img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img>| `<img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

### <a name="mobile-and-desktop-differences-for-simple-cards"></a><span data-ttu-id="f1a86-273">Diferenças móveis e de área de trabalho para cartões simples</span><span class="sxs-lookup"><span data-stu-id="f1a86-273">Mobile and desktop differences for simple cards</span></span>

<span data-ttu-id="f1a86-274">Devido às diferenças de resolução entre a área de trabalho e a plataforma móvel, a formatação é diferente entre a área de trabalho e a versão móvel do teams.</span><span class="sxs-lookup"><span data-stu-id="f1a86-274">Because of resolution differences between the desktop and mobile platform, formatting is different between the desktop and the mobile version of Teams.</span></span>

<span data-ttu-id="f1a86-275">Na área de trabalho, a formatação HTML aparece da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="f1a86-275">On the desktop, HTML formatting appears like this:</span></span>

![Formatação HTML no cliente de desktop](../../assets/images/cards/card-formatting-xml-desktop-v2.png)

<span data-ttu-id="f1a86-277">No iOS, a formatação HTML aparece da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="f1a86-277">On iOS, HTML formatting appears like this:</span></span>

![Formatação HTML no cliente iOS](../../assets/images/cards/card-formatting-xml-mobile-v2.png)

<span data-ttu-id="f1a86-279">Problemas</span><span class="sxs-lookup"><span data-stu-id="f1a86-279">Issues:</span></span>

* <span data-ttu-id="f1a86-280">A formatação de caracteres como negrito e itálico não é renderizada no iOS.</span><span class="sxs-lookup"><span data-stu-id="f1a86-280">Character formatting like bold and italic are not rendered on iOS.</span></span>

<span data-ttu-id="f1a86-281">No Android, a formatação HTML aparece da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="f1a86-281">On Android, HTML formatting appears like this:</span></span>

![Formatação HTML no cliente Android](../../assets/images/cards/card-formatting-xml-android-60.png)

<span data-ttu-id="f1a86-283">Formatação de caracteres como negrito e itálico são exibidos corretamente no Android.</span><span class="sxs-lookup"><span data-stu-id="f1a86-283">Character formatting like bold and italic display correctly on Android.</span></span>

### <a name="formatting-sample-for-html-formatting-in-simple-cards"></a><span data-ttu-id="f1a86-284">Exemplo de formatação para formatação HTML em cartões simples</span><span class="sxs-lookup"><span data-stu-id="f1a86-284">Formatting sample for HTML formatting in simple cards</span></span>

<span data-ttu-id="f1a86-285">Essas capturas de tela foram criadas usando o Teams AppStudio, onde a propriedade Text de um cartão herói foi definida como a cadeia de caracteres a seguir.</span><span class="sxs-lookup"><span data-stu-id="f1a86-285">These screenshots were created using Teams AppStudio, where the text property of a hero card was set to the following string.</span></span> <span data-ttu-id="f1a86-286">Você pode testar a formatação em seus próprios cartões modificando esse código.</span><span class="sxs-lookup"><span data-stu-id="f1a86-286">You can test formatting in your own cards by modifying this code.</span></span>

`<p>bold: <strong>Bold Text</strong></p><p>italic: <em>Italic Text</em></p><p>strikethrough: <strike>Strikethrough text</strike></p><h1>Header 1</h1><h2>Header 2</h2><h3>Header 3</h3><p>bullet list: <ul><li>text</li><li>text</li></ul></p><p>ordered list: <ol><li>text</li><li>text</li></ol></p><pre>preformatted text</pre><blockquote>blockquote text</blockquote></p><p>hyperlink: <a href=\"https://www.bing.com/\">Bing</a></p><p>embedded image: <img src=\"http://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img></p>`

---
