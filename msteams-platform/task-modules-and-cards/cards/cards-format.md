---
title: Formatação de texto em cartões
description: Descreve a formatação de texto do cartão no Microsoft Teams
keywords: formato de cartões de bots da equipe
ms.date: 03/29/2018
ms.openlocfilehash: 0c723c436346498ed2e5704db6f6401204530165
ms.sourcegitcommit: 646a8224523be7db96f9686e22d420d62d55d4b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2020
ms.locfileid: "42365245"
---
# <a name="format-cards-in-teams"></a><span data-ttu-id="d783a-104">Formatar cartões no Teams</span><span class="sxs-lookup"><span data-stu-id="d783a-104">Format cards in Teams</span></span>

<span data-ttu-id="d783a-105">Você pode adicionar formatação de Rich Text aos seus cartões usando redução ou HTML, dependendo do tipo de cartão.</span><span class="sxs-lookup"><span data-stu-id="d783a-105">You can add rich text formatting to your cards using either Markdown or HTML, depending on the card type.</span></span>

<span data-ttu-id="d783a-106">Os cartões dão suporte à formatação somente na propriedade Text, e não nas propriedades Title ou subtítulo.</span><span class="sxs-lookup"><span data-stu-id="d783a-106">Cards support formatting in the text property only, not in the title or subtitle properties.</span></span> <span data-ttu-id="d783a-107">A formatação pode ser especificada usando um subconjunto de formatação XML (HTML) ou redução, dependendo do tipo de cartão.</span><span class="sxs-lookup"><span data-stu-id="d783a-107">Formatting can be specified using a subset of XML (HTML) formatting, or Markdown depending on card type.</span></span> <span data-ttu-id="d783a-108">É recomendável usar os cartões adaptáveis de desenvolvimento atuais e futuros usando a formatação de redução.</span><span class="sxs-lookup"><span data-stu-id="d783a-108">For current and future development Adaptive cards using Markdown formatting is recommended.</span></span>

<span data-ttu-id="d783a-109">O suporte à formatação difere entre diferentes tipos de cartão, e a renderização do cartão pode diferir ligeiramente entre a área de trabalho e os clientes do Mobile Teams, bem como o Microsoft Teams no navegador da área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="d783a-109">Formatting support differs between different card types, and rendering of the card can differ slightly between the desktop and the mobile Teams clients, as well as Teams in the desktop browser.</span></span>

<span data-ttu-id="d783a-110">Você pode incluir uma imagem embutida em qualquer placa do teams.</span><span class="sxs-lookup"><span data-stu-id="d783a-110">You can include an inline image with any Teams card.</span></span> <span data-ttu-id="d783a-111">As imagens são formatadas `.png`como `.jpg`, ou `.gif` arquivos, e não devem exceder 1024 × 1024 PX ou 1 MB.</span><span class="sxs-lookup"><span data-stu-id="d783a-111">Images an be formatted as  `.png`, `.jpg`, or `.gif` files and must not exceed 1024 ×1024 px or 1 MB.</span></span> <span data-ttu-id="d783a-112">GIF animado não é oficialmente suportado.</span><span class="sxs-lookup"><span data-stu-id="d783a-112">Animated GIF is not officially supported.</span></span> <span data-ttu-id="d783a-113">*Consulte* [referência de cartões](./cards-reference.md#inline-card-images)</span><span class="sxs-lookup"><span data-stu-id="d783a-113">*See* [Cards reference](./cards-reference.md#inline-card-images)</span></span>

## <a name="formatting-cards-with-markdown"></a><span data-ttu-id="d783a-114">Formatando cartões com redução</span><span class="sxs-lookup"><span data-stu-id="d783a-114">Formatting cards with Markdown</span></span>

<span data-ttu-id="d783a-115">Há dois tipos de cartões que dão suporte à redução no Microsoft Teams:</span><span class="sxs-lookup"><span data-stu-id="d783a-115">There are two card types that support Markdown in Teams:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="d783a-116">**Cartões adaptáveis**: a redução é suportada no `Textblock` campo de cartão adaptável, `Fact.Title` bem `Fact.Value`como e.</span><span class="sxs-lookup"><span data-stu-id="d783a-116">**Adaptive Cards**: Markdown is supported in Adaptive Card `Textblock` field, as well as `Fact.Title` and `Fact.Value`.</span></span> <span data-ttu-id="d783a-117">O HTML não é suportado em cartões adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="d783a-117">HTML is not supported in adaptive cards.</span></span>
> * <span data-ttu-id="d783a-118">**Cartões de conector do O365**: redução e HTML limitado são suportados nos cartões de conector do Office 365 nos campos de texto.</span><span class="sxs-lookup"><span data-stu-id="d783a-118">**O365 Connector Cards**: Markdown and limited HTML is supported in Office 365 Connector cards in the text fields.</span></span>

# <a name="markdown-formatting-adaptive-cards"></a>[<span data-ttu-id="d783a-119">**Formatação de redução: cartões adaptáveis**</span><span class="sxs-lookup"><span data-stu-id="d783a-119">**Markdown formatting: Adaptive Cards**</span></span>](#tab/adaptive-md)

 <span data-ttu-id="d783a-120">Os estilos suportados para `Textblock` `Fact.Title` e `Fact.Value` são:</span><span class="sxs-lookup"><span data-stu-id="d783a-120">The supported styles for `Textblock`, `Fact.Title` and `Fact.Value` are:</span></span>

| <span data-ttu-id="d783a-121">Estilo</span><span class="sxs-lookup"><span data-stu-id="d783a-121">Style</span></span> | <span data-ttu-id="d783a-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d783a-122">Example</span></span> | <span data-ttu-id="d783a-123">Markdown</span><span class="sxs-lookup"><span data-stu-id="d783a-123">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="d783a-124">bold</span><span class="sxs-lookup"><span data-stu-id="d783a-124">bold</span></span> | <span data-ttu-id="d783a-125">**Negrito**</span><span class="sxs-lookup"><span data-stu-id="d783a-125">**Bold**</span></span> | ```**Bold**``` |
| <span data-ttu-id="d783a-126">italic</span><span class="sxs-lookup"><span data-stu-id="d783a-126">italic</span></span> | <span data-ttu-id="d783a-127">_Itálico_</span><span class="sxs-lookup"><span data-stu-id="d783a-127">_Italic_</span></span> | ```_Italic_``` |
| <span data-ttu-id="d783a-128">lista não ordenada</span><span class="sxs-lookup"><span data-stu-id="d783a-128">unordered list</span></span> | <ul><li><span data-ttu-id="d783a-129">texto</span><span class="sxs-lookup"><span data-stu-id="d783a-129">text</span></span></li><li><span data-ttu-id="d783a-130">texto</span><span class="sxs-lookup"><span data-stu-id="d783a-130">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="d783a-131">lista ordenada</span><span class="sxs-lookup"><span data-stu-id="d783a-131">ordered list</span></span> | <ol><li><span data-ttu-id="d783a-132">texto</span><span class="sxs-lookup"><span data-stu-id="d783a-132">text</span></span></li><li><span data-ttu-id="d783a-133">texto</span><span class="sxs-lookup"><span data-stu-id="d783a-133">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="d783a-134">Hiperlinks</span><span class="sxs-lookup"><span data-stu-id="d783a-134">Hyperlinks</span></span> |[<span data-ttu-id="d783a-135">Bing</span><span class="sxs-lookup"><span data-stu-id="d783a-135">Bing</span></span>](https://www.bing.com/)| ```[Title](url)``` |

<span data-ttu-id="d783a-136">Não há suporte para as seguintes marcas de redução:</span><span class="sxs-lookup"><span data-stu-id="d783a-136">The following Markdown tags are not supported:</span></span>

* <span data-ttu-id="d783a-137">Cabeçalhos</span><span class="sxs-lookup"><span data-stu-id="d783a-137">Headers</span></span>
* <span data-ttu-id="d783a-138">Tabelas</span><span class="sxs-lookup"><span data-stu-id="d783a-138">Tables</span></span>
* <span data-ttu-id="d783a-139">Imagens</span><span class="sxs-lookup"><span data-stu-id="d783a-139">Images</span></span>
* <span data-ttu-id="d783a-140">Texto pré-formatado</span><span class="sxs-lookup"><span data-stu-id="d783a-140">Preformatted text</span></span>
* <span data-ttu-id="d783a-141">Blockquote</span><span class="sxs-lookup"><span data-stu-id="d783a-141">Blockquotes</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d783a-142">Os cartões adaptáveis não dão suporte a qualquer formatação HTML.</span><span class="sxs-lookup"><span data-stu-id="d783a-142">Adaptive cards do not support any HTML formatting.</span></span>

### <a name="newlines-for-adaptive-cards"></a><span data-ttu-id="d783a-143">Novas linhas para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="d783a-143">Newlines for Adaptive Cards</span></span>

<span data-ttu-id="d783a-144">Nas listas, você pode usar `\r` as `\n` sequências de escape ou de saída para novas linhas.</span><span class="sxs-lookup"><span data-stu-id="d783a-144">In lists you can use the `\r` or `\n` escape sequences for newlines.</span></span> <span data-ttu-id="d783a-145">Usar `\n\n` em uma lista fará com que o próximo elemento na lista seja recuado.</span><span class="sxs-lookup"><span data-stu-id="d783a-145">Using `\n\n` in a list will cause the next element in the list to be indented.</span></span> <span data-ttu-id="d783a-146">Se você precisar de novas linhas em qualquer lugar no TextBlock `\n\n`, use.</span><span class="sxs-lookup"><span data-stu-id="d783a-146">If you need newlines elsewhere in the textblock, use `\n\n`.</span></span>

### <a name="mobile-and-desktop-differences-for-adaptive-cards"></a><span data-ttu-id="d783a-147">Diferenças móveis e de área de trabalho para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="d783a-147">Mobile and desktop differences for Adaptive Cards</span></span>

<span data-ttu-id="d783a-148">A formatação é um pouco diferente entre a área de trabalho e as versões móveis do teams.</span><span class="sxs-lookup"><span data-stu-id="d783a-148">Formatting is slightly different between the desktop and the mobile versions of Teams.</span></span>

<span data-ttu-id="d783a-149">Na área de trabalho, a formatação de redução de cartão adaptável aparece como esta nos dois navegadores da Web e no aplicativo cliente do teams:</span><span class="sxs-lookup"><span data-stu-id="d783a-149">On the desktop, Adaptive Card Markdown formatting appears like this in both web browsers and in the Teams client application:</span></span>

![Formatação de redução de cartão adaptável no cliente de desktop](/assets/images/cards/Adaptive-markdown-desktop-client.png)

<span data-ttu-id="d783a-151">No iOS, a formatação de redução de cartão adaptável aparece da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d783a-151">On iOS, Adaptive Card Markdown formatting appears like this:</span></span>

![Formatação de redução de cartão adaptável no iOS](/assets/images/cards/Adaptive-markdown-iOS-75.png)

<span data-ttu-id="d783a-153">No Android, a formatação de redução de cartão adaptável aparece da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d783a-153">On Android, Adaptive Card Markdown formatting appears like this:</span></span>

![Formatação de redução de cartão adaptável no Android](/assets/images/cards/Adaptive-markdown-Android.png)

### <a name="more-information-on-adaptive-cards"></a><span data-ttu-id="d783a-155">Mais informações sobre cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="d783a-155">More information on Adaptive Cards</span></span>

<span data-ttu-id="d783a-156">[Recursos de texto em cartões adaptáveis](/adaptive-cards/create/textfeatures) Os recursos de data e localização mencionados neste tópico não têm suporte no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="d783a-156">[Text features in Adaptive cards](/adaptive-cards/create/textfeatures) The date and localization features mentioned in this topic are not supported in Teams.</span></span>

### <a name="formatting-sample-for-adaptive-cards"></a><span data-ttu-id="d783a-157">Exemplo de formatação para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="d783a-157">Formatting sample for Adaptive cards</span></span>

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

### <a name="mention-support-within-adaptive-cards"></a><span data-ttu-id="d783a-158">Mencione o suporte de cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="d783a-158">Mention support within Adaptive cards</span></span>

> [!NOTE]
> <span data-ttu-id="d783a-159">Mencione o suporte nos cartões atualmente é suportado apenas na [visualização do desenvolvedor](../../resources/dev-preview/developer-preview-intro.md) .</span><span class="sxs-lookup"><span data-stu-id="d783a-159">Mention support in cards is currently supported in [Developer Preview](../../resources/dev-preview/developer-preview-intro.md) only.</span></span>

<span data-ttu-id="d783a-160">Os bots e as extensões de mensagens agora podem incluir menção dentro do conteúdo do cartão nos elementos bloco de texto e FactSet.</span><span class="sxs-lookup"><span data-stu-id="d783a-160">Bots and Messaging extensions can now include mentions within the card content in Text Block and FactSet elements.</span></span>

### <a name="constructing-mentions"></a><span data-ttu-id="d783a-161">Como criar menção</span><span class="sxs-lookup"><span data-stu-id="d783a-161">Constructing mentions</span></span>

<span data-ttu-id="d783a-162">Para incluir uma menção em um cartão adaptável, seu aplicativo precisa incluir os seguintes elementos</span><span class="sxs-lookup"><span data-stu-id="d783a-162">To include a mention in an Adaptive Card your app needs to include the following elements</span></span>

* <span data-ttu-id="d783a-163">`<at>username</at>`nos elementos de cartão adaptável com suporte</span><span class="sxs-lookup"><span data-stu-id="d783a-163">`<at>username</at>` in the supported adaptive card elements</span></span>
* <span data-ttu-id="d783a-164">O `mention` objeto dentro de uma `msteams` Propriedade no conteúdo do cartão, que inclui a ID de usuário do Team do usuário que está sendo mencionado</span><span class="sxs-lookup"><span data-stu-id="d783a-164">The `mention` object inside of an `msteams` property in the card content, which includes the Teams user id of the user being mentioned</span></span>

<span data-ttu-id="d783a-165">Observe que os cartões com menção não têm suporte em clientes móveis no momento.</span><span class="sxs-lookup"><span data-stu-id="d783a-165">Note that cards with mentions aren't supported on mobile clients at the moment.</span></span>

### <a name="sample-adaptive-card-with-a-mention"></a><span data-ttu-id="d783a-166">Cartão adaptável de amostra com menção</span><span class="sxs-lookup"><span data-stu-id="d783a-166">Sample Adaptive card with a mention</span></span>

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

# <a name="markdown-formatting-o365-connector-cards"></a>[<span data-ttu-id="d783a-167">**Formatação de redução: cartões de conector do O365**</span><span class="sxs-lookup"><span data-stu-id="d783a-167">**Markdown formatting: O365 Connector Cards**</span></span>](#tab/connector-md)

<span data-ttu-id="d783a-168">Os cartões de conector dão suporte à redução limitada e à formatação HTML.</span><span class="sxs-lookup"><span data-stu-id="d783a-168">Connector cards support limited Markdown and HTML formatting.</span></span> <span data-ttu-id="d783a-169">O suporte a HTML é descrito na última seção.</span><span class="sxs-lookup"><span data-stu-id="d783a-169">HTML support is described in the last section.</span></span>

| <span data-ttu-id="d783a-170">Estilo</span><span class="sxs-lookup"><span data-stu-id="d783a-170">Style</span></span> | <span data-ttu-id="d783a-171">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d783a-171">Example</span></span> | <span data-ttu-id="d783a-172">Markdown</span><span class="sxs-lookup"><span data-stu-id="d783a-172">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="d783a-173">bold</span><span class="sxs-lookup"><span data-stu-id="d783a-173">bold</span></span> | <span data-ttu-id="d783a-174">**text**</span><span class="sxs-lookup"><span data-stu-id="d783a-174">**text**</span></span> | `**text**` |
| <span data-ttu-id="d783a-175">italic</span><span class="sxs-lookup"><span data-stu-id="d783a-175">italic</span></span> | <span data-ttu-id="d783a-176">*text*</span><span class="sxs-lookup"><span data-stu-id="d783a-176">*text*</span></span> | `*text*` |
| <span data-ttu-id="d783a-177">cabeçalho (níveis 1&ndash;3)</span><span class="sxs-lookup"><span data-stu-id="d783a-177">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="d783a-178">**Text**</span><span class="sxs-lookup"><span data-stu-id="d783a-178">**Text**</span></span> | `### Text`|
| <span data-ttu-id="d783a-179">tachado</span><span class="sxs-lookup"><span data-stu-id="d783a-179">strikethrough</span></span> | <span data-ttu-id="d783a-180">~~text~~</span><span class="sxs-lookup"><span data-stu-id="d783a-180">~~text~~</span></span> | `~~text~~` |
| <span data-ttu-id="d783a-181">lista não ordenada</span><span class="sxs-lookup"><span data-stu-id="d783a-181">unordered list</span></span> | <ul><li><span data-ttu-id="d783a-182">texto</span><span class="sxs-lookup"><span data-stu-id="d783a-182">text</span></span></li><li><span data-ttu-id="d783a-183">texto</span><span class="sxs-lookup"><span data-stu-id="d783a-183">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="d783a-184">lista ordenada</span><span class="sxs-lookup"><span data-stu-id="d783a-184">ordered list</span></span> | <ol><li><span data-ttu-id="d783a-185">texto</span><span class="sxs-lookup"><span data-stu-id="d783a-185">text</span></span></li><li><span data-ttu-id="d783a-186">texto</span><span class="sxs-lookup"><span data-stu-id="d783a-186">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="d783a-187">texto pré-formatado</span><span class="sxs-lookup"><span data-stu-id="d783a-187">preformatted text</span></span> | `text` | ``preformatted text`` |
| <span data-ttu-id="d783a-188">blockquote</span><span class="sxs-lookup"><span data-stu-id="d783a-188">blockquote</span></span> | <span data-ttu-id="d783a-189">>texto blockquote</span><span class="sxs-lookup"><span data-stu-id="d783a-189">>blockquote text</span></span> | `>blockquote text` |
| <span data-ttu-id="d783a-190">hyperlink</span><span class="sxs-lookup"><span data-stu-id="d783a-190">hyperlink</span></span> | [<span data-ttu-id="d783a-191">Bing</span><span class="sxs-lookup"><span data-stu-id="d783a-191">Bing</span></span>](https://www.bing.com/) | `[Bing](https://www.bing.com/)` |
| <span data-ttu-id="d783a-192">link de imagem</span><span class="sxs-lookup"><span data-stu-id="d783a-192">image link</span></span> |![Pato em uma pedra](https://aka.ms/Fo983c) | `![Duck](https://aka.ms/Fo983c)` |

<span data-ttu-id="d783a-194">Nos cartões conectores, as novas linhas são `\n\n`renderizadas para, `\n` mas `\r`não para ou.</span><span class="sxs-lookup"><span data-stu-id="d783a-194">In connector cards, newlines are rendered for `\n\n`, but not for `\n` or `\r`.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards-using-markdown"></a><span data-ttu-id="d783a-195">Diferenças de dispositivos móveis e de área de trabalho para cartões de conexão usando redução</span><span class="sxs-lookup"><span data-stu-id="d783a-195">Mobile and desktop differences for connector cards using Markdown</span></span>

<span data-ttu-id="d783a-196">Na área de trabalho, a redução da formatação de cartões de conector tem a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="d783a-196">On the desktop, Markdown formatting for connector cards looks like this:</span></span>

![Redução da formatação de cartões de conector no cliente de desktop](/assets/images/cards/connector-desktop-markdown-combined.png)

<span data-ttu-id="d783a-198">No iOS, a redução da formatação de cartões de conector tem a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="d783a-198">On iOS, Markdown formatting for connector cards looks like this:</span></span>

![Redução da formatação de cartões de conector no cliente iOS](/assets/images/cards/connector-iphone-markdown-combined-80.png)

<span data-ttu-id="d783a-200">Problemas</span><span class="sxs-lookup"><span data-stu-id="d783a-200">Issues:</span></span>

* <span data-ttu-id="d783a-201">O cliente iOS para Teams não renderiza a redução ou as imagens embutidas HTML nos cartões de conector.</span><span class="sxs-lookup"><span data-stu-id="d783a-201">The iOS client for Teams does not render Markdown or HTML inline images in Connector Cards.</span></span>
* <span data-ttu-id="d783a-202">Blockquotes são renderizados como recuados, mas sem um plano de fundo cinza.</span><span class="sxs-lookup"><span data-stu-id="d783a-202">Blockquotes are rendered as indented but without a gray background.</span></span>

<span data-ttu-id="d783a-203">No Android, a redução da formatação de cartões de conector tem a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="d783a-203">On Android, Markdown formatting for connector cards looks like this:</span></span>

![Redução da formatação de cartões de conector no cliente Android](/assets/images/cards/connector-android-markdown-combined.png)

### <a name="formatting-example-for-markdown-connector-cards"></a><span data-ttu-id="d783a-205">Exemplo de formatação para redução de cartões de conector</span><span class="sxs-lookup"><span data-stu-id="d783a-205">Formatting example for Markdown Connector Cards</span></span>

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

## <a name="formatting-cards-with-html"></a><span data-ttu-id="d783a-206">Formatando cartões com HTML</span><span class="sxs-lookup"><span data-stu-id="d783a-206">Formatting cards with HTML</span></span>

# <a name="html-formatting-o365-connector-cards"></a>[<span data-ttu-id="d783a-207">**Formatação HTML: cartões de conector do O365**</span><span class="sxs-lookup"><span data-stu-id="d783a-207">**HTML formatting: O365 Connector Cards**</span></span>](#tab/connector-html)

<span data-ttu-id="d783a-208">Os cartões de conector dão suporte à redução limitada e à formatação HTML.</span><span class="sxs-lookup"><span data-stu-id="d783a-208">Connector cards support limited Markdown and HTML formatting.</span></span> <span data-ttu-id="d783a-209">A redução é descrita na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="d783a-209">Markdown is described in the next section.</span></span>

| <span data-ttu-id="d783a-210">Estilo</span><span class="sxs-lookup"><span data-stu-id="d783a-210">Style</span></span> | <span data-ttu-id="d783a-211">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d783a-211">Example</span></span> | <span data-ttu-id="d783a-212">HTML</span><span class="sxs-lookup"><span data-stu-id="d783a-212">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="d783a-213">bold</span><span class="sxs-lookup"><span data-stu-id="d783a-213">bold</span></span> | <span data-ttu-id="d783a-214">**text**</span><span class="sxs-lookup"><span data-stu-id="d783a-214">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="d783a-215">italic</span><span class="sxs-lookup"><span data-stu-id="d783a-215">italic</span></span> | <span data-ttu-id="d783a-216">*text*</span><span class="sxs-lookup"><span data-stu-id="d783a-216">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="d783a-217">cabeçalho (níveis 1&ndash;3)</span><span class="sxs-lookup"><span data-stu-id="d783a-217">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="d783a-218">**Text**</span><span class="sxs-lookup"><span data-stu-id="d783a-218">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="d783a-219">tachado</span><span class="sxs-lookup"><span data-stu-id="d783a-219">strikethrough</span></span> | <span data-ttu-id="d783a-220">~~text~~</span><span class="sxs-lookup"><span data-stu-id="d783a-220">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="d783a-221">lista não ordenada</span><span class="sxs-lookup"><span data-stu-id="d783a-221">unordered list</span></span> | <ul><li><span data-ttu-id="d783a-222">texto</span><span class="sxs-lookup"><span data-stu-id="d783a-222">text</span></span></li><li><span data-ttu-id="d783a-223">texto</span><span class="sxs-lookup"><span data-stu-id="d783a-223">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="d783a-224">lista ordenada</span><span class="sxs-lookup"><span data-stu-id="d783a-224">ordered list</span></span> | <ol><li><span data-ttu-id="d783a-225">texto</span><span class="sxs-lookup"><span data-stu-id="d783a-225">text</span></span></li><li><span data-ttu-id="d783a-226">texto</span><span class="sxs-lookup"><span data-stu-id="d783a-226">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="d783a-227">texto pré-formatado</span><span class="sxs-lookup"><span data-stu-id="d783a-227">preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="d783a-228">blockquote</span><span class="sxs-lookup"><span data-stu-id="d783a-228">blockquote</span></span> | <blockquote><span data-ttu-id="d783a-229">texto</span><span class="sxs-lookup"><span data-stu-id="d783a-229">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="d783a-230">hyperlink</span><span class="sxs-lookup"><span data-stu-id="d783a-230">hyperlink</span></span> | [<span data-ttu-id="d783a-231">Bing</span><span class="sxs-lookup"><span data-stu-id="d783a-231">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="d783a-232">link de imagem</span><span class="sxs-lookup"><span data-stu-id="d783a-232">image link</span></span> | <img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img> | `<img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

<span data-ttu-id="d783a-233">Em cartões de conector, as novas linhas são renderizadas em `<p>` HTML usando a marca.</span><span class="sxs-lookup"><span data-stu-id="d783a-233">In connector cards, newlines are rendered in HTML using the `<p>` tag.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards-using-html"></a><span data-ttu-id="d783a-234">Diferenças móveis e de área de trabalho para cartões de conexão usando HTML</span><span class="sxs-lookup"><span data-stu-id="d783a-234">Mobile and desktop differences for connector cards using HTML</span></span>

<span data-ttu-id="d783a-235">Na área de trabalho, a formatação HTML para cartões de conector tem a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="d783a-235">On the desktop, HTML formatting for connector cards looks like this:</span></span>

![Formatação HTML para cartões de conector no cliente de desktop](/assets/images/cards/Connector-desktop-html-combined.png)

<span data-ttu-id="d783a-237">No iOS, a formatação HTML tem a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="d783a-237">On iOS, HTML formatting looks like this:</span></span>

![Formatação HTML para cartões de conector no cliente iOS](/assets/images/cards/connector-iphone-html-combined-80.png)

<span data-ttu-id="d783a-239">Problemas</span><span class="sxs-lookup"><span data-stu-id="d783a-239">Issues:</span></span>

* <span data-ttu-id="d783a-240">As imagens embutidas não são renderizadas no iOS usando a redução ou HTML em cartões de conexão.</span><span class="sxs-lookup"><span data-stu-id="d783a-240">Inline images are not rendered on iOS using either Markdown or HTML in Connector Cards.</span></span>
* <span data-ttu-id="d783a-241">O texto pré-formatado é renderizado, mas não tem um plano de fundo cinza.</span><span class="sxs-lookup"><span data-stu-id="d783a-241">Preformatted text is rendered but does not have a gray background.</span></span>

<span data-ttu-id="d783a-242">No Android, a formatação HTML tem a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="d783a-242">On Android, HTML formatting looks like this:</span></span>

![Formatação HTML para cartões de conector no cliente Android](/assets/images/cards/connector-android-html-combined.png)

### <a name="formatting-sample-for-html-connector-cards"></a><span data-ttu-id="d783a-244">Exemplo de formatação para cartões de conexão HTML</span><span class="sxs-lookup"><span data-stu-id="d783a-244">Formatting sample for HTML Connector Cards</span></span>

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

# <a name="html-formatting-hero-and-thumbnail-cards"></a>[<span data-ttu-id="d783a-245">**Formatação HTML: herói e cartões de miniatura**</span><span class="sxs-lookup"><span data-stu-id="d783a-245">**HTML Formatting: hero and thumbnail cards**</span></span>](#tab/simple-html)

<span data-ttu-id="d783a-246">Marcas HTML têm suporte para cartões simples como o herói e o cartão de miniatura.</span><span class="sxs-lookup"><span data-stu-id="d783a-246">HTML tags are supported for simple cards such as the hero and thumbnail card.</span></span> <span data-ttu-id="d783a-247">Não há suporte para redução.</span><span class="sxs-lookup"><span data-stu-id="d783a-247">Markdown is not supported.</span></span>

| <span data-ttu-id="d783a-248">Estilo</span><span class="sxs-lookup"><span data-stu-id="d783a-248">Style</span></span> | <span data-ttu-id="d783a-249">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d783a-249">Example</span></span> | <span data-ttu-id="d783a-250">HTML</span><span class="sxs-lookup"><span data-stu-id="d783a-250">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="d783a-251">bold</span><span class="sxs-lookup"><span data-stu-id="d783a-251">bold</span></span> | <span data-ttu-id="d783a-252">**text**</span><span class="sxs-lookup"><span data-stu-id="d783a-252">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="d783a-253">italic</span><span class="sxs-lookup"><span data-stu-id="d783a-253">italic</span></span> | <span data-ttu-id="d783a-254">*text*</span><span class="sxs-lookup"><span data-stu-id="d783a-254">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="d783a-255">cabeçalho (níveis 1&ndash;3)</span><span class="sxs-lookup"><span data-stu-id="d783a-255">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="d783a-256">**Text**</span><span class="sxs-lookup"><span data-stu-id="d783a-256">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="d783a-257">tachado</span><span class="sxs-lookup"><span data-stu-id="d783a-257">strikethrough</span></span> | <span data-ttu-id="d783a-258">~~text~~</span><span class="sxs-lookup"><span data-stu-id="d783a-258">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="d783a-259">lista não ordenada</span><span class="sxs-lookup"><span data-stu-id="d783a-259">unordered list</span></span> | <ul><li><span data-ttu-id="d783a-260">texto</span><span class="sxs-lookup"><span data-stu-id="d783a-260">text</span></span></li><li><span data-ttu-id="d783a-261">texto</span><span class="sxs-lookup"><span data-stu-id="d783a-261">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="d783a-262">lista ordenada</span><span class="sxs-lookup"><span data-stu-id="d783a-262">ordered list</span></span> | <ol><li><span data-ttu-id="d783a-263">texto</span><span class="sxs-lookup"><span data-stu-id="d783a-263">text</span></span></li><li><span data-ttu-id="d783a-264">texto</span><span class="sxs-lookup"><span data-stu-id="d783a-264">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="d783a-265">texto pré-formatado</span><span class="sxs-lookup"><span data-stu-id="d783a-265">preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="d783a-266">blockquote</span><span class="sxs-lookup"><span data-stu-id="d783a-266">blockquote</span></span> | <blockquote><span data-ttu-id="d783a-267">texto</span><span class="sxs-lookup"><span data-stu-id="d783a-267">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="d783a-268">hyperlink</span><span class="sxs-lookup"><span data-stu-id="d783a-268">hyperlink</span></span> | [<span data-ttu-id="d783a-269">Bing</span><span class="sxs-lookup"><span data-stu-id="d783a-269">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="d783a-270">link de imagem</span><span class="sxs-lookup"><span data-stu-id="d783a-270">image link</span></span> |<img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img>| `<img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

### <a name="mobile-and-desktop-differences-for-simple-cards"></a><span data-ttu-id="d783a-271">Diferenças móveis e de área de trabalho para cartões simples</span><span class="sxs-lookup"><span data-stu-id="d783a-271">Mobile and desktop differences for simple cards</span></span>

<span data-ttu-id="d783a-272">Devido às diferenças de resolução entre a área de trabalho e a plataforma móvel, a formatação é diferente entre a área de trabalho e a versão móvel do teams.</span><span class="sxs-lookup"><span data-stu-id="d783a-272">Because of resolution differences between the desktop and mobile platform, formatting is different between the desktop and the mobile version of Teams.</span></span>

<span data-ttu-id="d783a-273">Na área de trabalho, a formatação HTML aparece da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d783a-273">On the desktop, HTML formatting appears like this:</span></span>

![Formatação HTML no cliente de desktop](/assets/images/cards/card-formatting-xml-desktop-v2.png)

<span data-ttu-id="d783a-275">No iOS, a formatação HTML aparece da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d783a-275">On iOS, HTML formatting appears like this:</span></span>

![Formatação HTML no cliente iOS](/assets/images/cards/card-formatting-xml-mobile-v2.png)

<span data-ttu-id="d783a-277">Problemas</span><span class="sxs-lookup"><span data-stu-id="d783a-277">Issues:</span></span>

* <span data-ttu-id="d783a-278">A formatação de caracteres como negrito e itálico não é renderizada no iOS.</span><span class="sxs-lookup"><span data-stu-id="d783a-278">Character formatting like bold and italic are not rendered on iOS.</span></span>

<span data-ttu-id="d783a-279">No Android, a formatação HTML aparece da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d783a-279">On Android, HTML formatting appears like this:</span></span>

![Formatação HTML no cliente Android](/assets/images/cards/card-formatting-xml-android-60.png)

<span data-ttu-id="d783a-281">Formatação de caracteres como negrito e itálico são exibidos corretamente no Android.</span><span class="sxs-lookup"><span data-stu-id="d783a-281">Character formatting like bold and italic display correctly on Android.</span></span>

### <a name="formatting-sample-for-html-formatting-in-simple-cards"></a><span data-ttu-id="d783a-282">Exemplo de formatação para formatação HTML em cartões simples</span><span class="sxs-lookup"><span data-stu-id="d783a-282">Formatting sample for HTML formatting in simple cards</span></span>

<span data-ttu-id="d783a-283">Essas capturas de tela foram criadas usando o Teams AppStudio, onde a propriedade Text de um cartão herói foi definida como a cadeia de caracteres a seguir.</span><span class="sxs-lookup"><span data-stu-id="d783a-283">These screenshots were created using Teams AppStudio, where the text property of a hero card was set to the following string.</span></span> <span data-ttu-id="d783a-284">Você pode testar a formatação em seus próprios cartões modificando esse código.</span><span class="sxs-lookup"><span data-stu-id="d783a-284">You can test formatting in your own cards by modifying this code.</span></span>

`<p>bold: <strong>Bold Text</strong></p><p>italic: <em>Italic Text</em></p><p>strikethrough: <strike>Strikethrough text</strike></p><h1>Header 1</h1><h2>Header 2</h2><h3>Header 3</h3><p>bullet list: <ul><li>text</li><li>text</li></ul></p><p>ordered list: <ol><li>text</li><li>text</li></ol></p><pre>preformatted text</pre><blockquote>blockquote text</blockquote></p><p>hyperlink: <a href=\"https://www.bing.com/\">Bing</a></p><p>embedded image: <img src=\"http://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img></p>`

---
