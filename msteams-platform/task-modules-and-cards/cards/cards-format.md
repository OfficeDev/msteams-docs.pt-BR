---
title: Formatação de texto em cartões
description: Descreve a formatação de texto do cartão no Microsoft Teams
keywords: formato de cartões de bots da equipe
ms.date: 03/29/2018
ms.openlocfilehash: 4a467c5b0b21cc3c19977bf7caa25e6790904b10
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672894"
---
# <a name="card-formatting"></a><span data-ttu-id="77a74-104">Formatação de cartão</span><span class="sxs-lookup"><span data-stu-id="77a74-104">Card formatting</span></span>

<span data-ttu-id="77a74-105">Você pode adicionar formatação de Rich Text aos seus cartões usando redução ou HTML, dependendo do tipo de cartão.</span><span class="sxs-lookup"><span data-stu-id="77a74-105">You can add rich text formatting to your cards using either markdown or HTML, depending on the card type.</span></span>

<span data-ttu-id="77a74-106">Os cartões dão suporte à formatação somente na propriedade Text, e não nas propriedades Title ou subtítulo.</span><span class="sxs-lookup"><span data-stu-id="77a74-106">Cards support formatting in the text property only, not in the title or subtitle properties.</span></span> <span data-ttu-id="77a74-107">A formatação pode ser especificada usando um subconjunto de formatação XML (HTML) ou redução, dependendo do tipo de cartão.</span><span class="sxs-lookup"><span data-stu-id="77a74-107">Formatting can be specified using a subset of XML (HTML) formatting, or Markdown depending on card type.</span></span> <span data-ttu-id="77a74-108">Para obter cartões adaptáveis de desenvolvimento futuro AMD atuais usando a formatação de redução é recomendável.</span><span class="sxs-lookup"><span data-stu-id="77a74-108">For current amd future development Adaptive cards using markdown formatting is recommended.</span></span>

<span data-ttu-id="77a74-109">O suporte à formatação difere entre diferentes tipos de cartão, e a renderização do cartão pode diferir ligeiramente entre a área de trabalho e os clientes do Mobile Teams, bem como o Microsoft Teams no navegador da área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="77a74-109">Formatting support differs between different card types, and rendering of the card can differ slightly between the desktop and the mobile Teams clients, as well as Teams in the desktop browser.</span></span>

## <a name="card-types"></a><span data-ttu-id="77a74-110">Tipos de cartão</span><span class="sxs-lookup"><span data-stu-id="77a74-110">Card types</span></span>

<span data-ttu-id="77a74-111">Há três tipos de cartões que dão suporte à redução no Microsoft Teams:</span><span class="sxs-lookup"><span data-stu-id="77a74-111">There are three types of cards that support Markdown in Teams:</span></span>

* <span data-ttu-id="77a74-112">**Cartões adaptáveis**: a redução é suportada no `Textblock` campo de cartão adaptável, `Fact.Title` bem `Fact.Value`como e.</span><span class="sxs-lookup"><span data-stu-id="77a74-112">**Adaptive Cards**: Markdown is supported in Adaptive Card `Textblock` field, as well as `Fact.Title` and `Fact.Value`.</span></span> <span data-ttu-id="77a74-113">O HTML não é suportado em cartões adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="77a74-113">HTML is not supported in adaptive cards.</span></span>
* <span data-ttu-id="77a74-114">**Cartões de conector do O365**: redução e HTML limitado são suportados nos cartões de conector do Office 365 nos campos de texto.</span><span class="sxs-lookup"><span data-stu-id="77a74-114">**O365 Connector Cards**: Markdown and limited HTML is supported in Office 365 Connector cards in the text fields.</span></span>
* <span data-ttu-id="77a74-115">**Cartões simples**: há suporte para HTML limitado, mas não há suporte para redução em cartões simples.</span><span class="sxs-lookup"><span data-stu-id="77a74-115">**Simple Cards**: Limited HTML is supported, but markdown is not supported in simple cards.</span></span>

## <a name="markdown-formatting-for-adaptive-cards"></a><span data-ttu-id="77a74-116">Redução da formatação de cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="77a74-116">Markdown formatting for Adaptive Cards</span></span>

 <span data-ttu-id="77a74-117">Os estilos suportados para `Textblock` `Fact.Title` e `Fact.Value` são:</span><span class="sxs-lookup"><span data-stu-id="77a74-117">The supported styles for `Textblock`, `Fact.Title` and `Fact.Value` are:</span></span>

| <span data-ttu-id="77a74-118">Estilo</span><span class="sxs-lookup"><span data-stu-id="77a74-118">Style</span></span> | <span data-ttu-id="77a74-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="77a74-119">Example</span></span> | <span data-ttu-id="77a74-120">Markdown</span><span class="sxs-lookup"><span data-stu-id="77a74-120">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="77a74-121">bold</span><span class="sxs-lookup"><span data-stu-id="77a74-121">bold</span></span> | <span data-ttu-id="77a74-122">**Negrito**</span><span class="sxs-lookup"><span data-stu-id="77a74-122">**Bold**</span></span> | ```**Bold**``` |
| <span data-ttu-id="77a74-123">italic</span><span class="sxs-lookup"><span data-stu-id="77a74-123">italic</span></span> | <span data-ttu-id="77a74-124">_Itálico_</span><span class="sxs-lookup"><span data-stu-id="77a74-124">_Italic_</span></span> | ```_Italic_``` |
| <span data-ttu-id="77a74-125">lista não ordenada</span><span class="sxs-lookup"><span data-stu-id="77a74-125">unordered list</span></span> | <ul><li><span data-ttu-id="77a74-126">texto</span><span class="sxs-lookup"><span data-stu-id="77a74-126">text</span></span></li><li><span data-ttu-id="77a74-127">texto</span><span class="sxs-lookup"><span data-stu-id="77a74-127">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="77a74-128">lista ordenada</span><span class="sxs-lookup"><span data-stu-id="77a74-128">ordered list</span></span> | <ol><li><span data-ttu-id="77a74-129">texto</span><span class="sxs-lookup"><span data-stu-id="77a74-129">text</span></span></li><li><span data-ttu-id="77a74-130">texto</span><span class="sxs-lookup"><span data-stu-id="77a74-130">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="77a74-131">Hiperlinks</span><span class="sxs-lookup"><span data-stu-id="77a74-131">Hyperlinks</span></span> |[<span data-ttu-id="77a74-132">Bing</span><span class="sxs-lookup"><span data-stu-id="77a74-132">Bing</span></span>](https://www.bing.com/)| ```[Title](url)``` |

<span data-ttu-id="77a74-133">Não há suporte para as seguintes marcas de redução:</span><span class="sxs-lookup"><span data-stu-id="77a74-133">The following markdown tags are not supported:</span></span>

* <span data-ttu-id="77a74-134">Cabeçalhos</span><span class="sxs-lookup"><span data-stu-id="77a74-134">Headers</span></span>
* <span data-ttu-id="77a74-135">Tabelas</span><span class="sxs-lookup"><span data-stu-id="77a74-135">Tables</span></span>
* <span data-ttu-id="77a74-136">Imagens</span><span class="sxs-lookup"><span data-stu-id="77a74-136">Images</span></span>
* <span data-ttu-id="77a74-137">Texto pré-formatado</span><span class="sxs-lookup"><span data-stu-id="77a74-137">Preformatted text</span></span>
* <span data-ttu-id="77a74-138">Blockquote</span><span class="sxs-lookup"><span data-stu-id="77a74-138">Blockquotes</span></span>

<span data-ttu-id="77a74-139">Os cartões adaptáveis não dão suporte a qualquer formatação HTML.</span><span class="sxs-lookup"><span data-stu-id="77a74-139">Adaptive cards do not support any HTML formatting.</span></span>

### <a name="newlines-for-adaptive-cards"></a><span data-ttu-id="77a74-140">Novas linhas para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="77a74-140">Newlines for Adaptive Cards</span></span>

<span data-ttu-id="77a74-141">Nas listas, você pode usar `\r` as `\n` sequências de escape ou de saída para novas linhas.</span><span class="sxs-lookup"><span data-stu-id="77a74-141">In lists you can use the `\r` or `\n` escape sequences for newlines.</span></span> <span data-ttu-id="77a74-142">Usar `\n\n` em uma lista fará com que o próximo elemento na lista seja recuado.</span><span class="sxs-lookup"><span data-stu-id="77a74-142">Using `\n\n` in a list will cause the next element in the list to be indented.</span></span> <span data-ttu-id="77a74-143">Se você precisar de novas linhas em qualquer lugar no TextBlock `\n\n`, use.</span><span class="sxs-lookup"><span data-stu-id="77a74-143">If you need newlines elsewhere in the textblock, use `\n\n`.</span></span>

### <a name="mobile-and-desktop-differences-for-adaptive-cards"></a><span data-ttu-id="77a74-144">Diferenças móveis e de área de trabalho para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="77a74-144">Mobile and desktop differences for Adaptive Cards</span></span>

<span data-ttu-id="77a74-145">A formatação é um pouco diferente entre a área de trabalho e as versões móveis do teams.</span><span class="sxs-lookup"><span data-stu-id="77a74-145">Formatting is slightly different between the desktop and the mobile versions of Teams.</span></span>

<span data-ttu-id="77a74-146">Na área de trabalho, a formatação de redução de cartão adaptável aparece como esta nos dois navegadores da Web e no aplicativo cliente do teams:</span><span class="sxs-lookup"><span data-stu-id="77a74-146">On the desktop, Adaptive Card markdown formatting appears like this in both web browsers and in the Teams client application:</span></span>

![Formatação de redução de cartão adaptável no cliente de desktop](~/assets/images/cards/Adaptive-markdown-desktop-client.png)

<span data-ttu-id="77a74-148">No iOS, a formatação de redução de cartão adaptável aparece da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="77a74-148">On iOS, Adaptive Card markdown formatting appears like this:</span></span>

![Formatação de redução de cartão adaptável no iOS](~/assets/images/cards/Adaptive-markdown-iOS-75.png)

<span data-ttu-id="77a74-150">No Android, a formatação de redução de cartão adaptável aparece da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="77a74-150">On Android, Adaptive Card markdown formatting appears like this:</span></span>

![Formatação de redução de cartão adaptável no Android](~/assets/images/cards/Adaptive-markdown-Android.png)

### <a name="for-more-information-on-adaptive-cards"></a><span data-ttu-id="77a74-152">Para obter mais informações sobre cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="77a74-152">For more information on Adaptive Cards</span></span>

<span data-ttu-id="77a74-153">[Recursos de texto em cartões adaptáveis](/adaptive-cards/create/textfeatures) Os recursos de data e localização mencionados neste tópico não têm suporte no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="77a74-153">[Text features in Adaptive cards](/adaptive-cards/create/textfeatures) The date and localization features mentioned in this topic are not supported in Teams.</span></span>

### <a name="formatting-sample-for-adaptive-cards"></a><span data-ttu-id="77a74-154">Exemplo de formatação para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="77a74-154">Formatting sample for Adaptive cards</span></span>

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
## <a name="mention-support-within-adaptive-cards"></a><span data-ttu-id="77a74-155">Mencione o suporte de cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="77a74-155">Mention support within Adaptive cards</span></span> 

> [!NOTE]
> <span data-ttu-id="77a74-156">Mencione o suporte nos cartões atualmente é suportado apenas na [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro) .</span><span class="sxs-lookup"><span data-stu-id="77a74-156">Mention support in cards is currently supported in [Developer Preview](~/resources/dev-preview/developer-preview-intro) only.</span></span>

<span data-ttu-id="77a74-157">Os bots e as extensões de mensagens agora podem incluir menção dentro do conteúdo do cartão nos elementos bloco de texto e FactSet.</span><span class="sxs-lookup"><span data-stu-id="77a74-157">Bots and Messaging extensions can now include mentions within the card content in Text Block and FactSet elements.</span></span> 

### <a name="constructing-mentions"></a><span data-ttu-id="77a74-158">Como criar menção</span><span class="sxs-lookup"><span data-stu-id="77a74-158">Constructing mentions</span></span>
<span data-ttu-id="77a74-159">Para incluir uma menção em um cartão adaptável, seu aplicativo precisa incluir os seguintes elementos</span><span class="sxs-lookup"><span data-stu-id="77a74-159">To include a mention in an Adaptive Card your app needs to include the following elements</span></span>

* <span data-ttu-id="77a74-160">`<at>username</at>`nos elementos de cartão adaptável com suporte</span><span class="sxs-lookup"><span data-stu-id="77a74-160">`<at>username</at>` in the supported adaptive card elements</span></span>
* <span data-ttu-id="77a74-161">O `mention` objeto dentro de uma `msteams` Propriedade no conteúdo do cartão, que inclui a ID de usuário do Team do usuário que está sendo mencionado</span><span class="sxs-lookup"><span data-stu-id="77a74-161">The `mention` object inside of an `msteams` property in the card content, which includes the Teams user id of the user being mentioned</span></span>

<span data-ttu-id="77a74-162">Observe que os cartões com menção não têm suporte em clientes móveis no momento.</span><span class="sxs-lookup"><span data-stu-id="77a74-162">Note that cards with mentions aren't supported on mobile clients at the moment.</span></span>

### <a name="sample-adaptive-card-with-a-mention"></a><span data-ttu-id="77a74-163">Cartão adaptável de amostra com menção</span><span class="sxs-lookup"><span data-stu-id="77a74-163">Sample Adaptive card with a mention</span></span>
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

## <a name="html-formatting-for-connector-cards"></a><span data-ttu-id="77a74-164">Formatação HTML para cartões de conector</span><span class="sxs-lookup"><span data-stu-id="77a74-164">HTML formatting for Connector Cards</span></span>

<span data-ttu-id="77a74-165">Os cartões de conector dão suporte à redução limitada e à formatação HTML.</span><span class="sxs-lookup"><span data-stu-id="77a74-165">Connector cards support limited markdown and HTML formatting.</span></span> <span data-ttu-id="77a74-166">A redução é descrita na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="77a74-166">Markdown is described in the next section.</span></span>

| <span data-ttu-id="77a74-167">Estilo</span><span class="sxs-lookup"><span data-stu-id="77a74-167">Style</span></span> | <span data-ttu-id="77a74-168">Exemplo</span><span class="sxs-lookup"><span data-stu-id="77a74-168">Example</span></span> | <span data-ttu-id="77a74-169">HTML</span><span class="sxs-lookup"><span data-stu-id="77a74-169">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="77a74-170">bold</span><span class="sxs-lookup"><span data-stu-id="77a74-170">bold</span></span> | <span data-ttu-id="77a74-171">**text**</span><span class="sxs-lookup"><span data-stu-id="77a74-171">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="77a74-172">italic</span><span class="sxs-lookup"><span data-stu-id="77a74-172">italic</span></span> | <span data-ttu-id="77a74-173">*text*</span><span class="sxs-lookup"><span data-stu-id="77a74-173">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="77a74-174">cabeçalho (níveis 1&ndash;3)</span><span class="sxs-lookup"><span data-stu-id="77a74-174">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="77a74-175">**Text**</span><span class="sxs-lookup"><span data-stu-id="77a74-175">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="77a74-176">tachado</span><span class="sxs-lookup"><span data-stu-id="77a74-176">strikethrough</span></span> | <span data-ttu-id="77a74-177">~~text~~</span><span class="sxs-lookup"><span data-stu-id="77a74-177">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="77a74-178">lista não ordenada</span><span class="sxs-lookup"><span data-stu-id="77a74-178">unordered list</span></span> | <ul><li><span data-ttu-id="77a74-179">texto</span><span class="sxs-lookup"><span data-stu-id="77a74-179">text</span></span></li><li><span data-ttu-id="77a74-180">texto</span><span class="sxs-lookup"><span data-stu-id="77a74-180">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="77a74-181">lista ordenada</span><span class="sxs-lookup"><span data-stu-id="77a74-181">ordered list</span></span> | <ol><li><span data-ttu-id="77a74-182">texto</span><span class="sxs-lookup"><span data-stu-id="77a74-182">text</span></span></li><li><span data-ttu-id="77a74-183">texto</span><span class="sxs-lookup"><span data-stu-id="77a74-183">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="77a74-184">texto pré-formatado</span><span class="sxs-lookup"><span data-stu-id="77a74-184">preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="77a74-185">blockquote</span><span class="sxs-lookup"><span data-stu-id="77a74-185">blockquote</span></span> | <blockquote><span data-ttu-id="77a74-186">texto</span><span class="sxs-lookup"><span data-stu-id="77a74-186">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="77a74-187">hyperlink</span><span class="sxs-lookup"><span data-stu-id="77a74-187">hyperlink</span></span> | [<span data-ttu-id="77a74-188">Bing</span><span class="sxs-lookup"><span data-stu-id="77a74-188">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="77a74-189">link de imagem</span><span class="sxs-lookup"><span data-stu-id="77a74-189">image link</span></span> | <img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img> | `<img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

<span data-ttu-id="77a74-190">Em cartões de conector, as novas linhas são renderizadas em `<p>` HTML usando a marca.</span><span class="sxs-lookup"><span data-stu-id="77a74-190">In connector cards, newlines are rendered in HTML using the `<p>` tag.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards-using-html"></a><span data-ttu-id="77a74-191">Diferenças móveis e de área de trabalho para cartões de conexão usando HTML</span><span class="sxs-lookup"><span data-stu-id="77a74-191">Mobile and desktop differences for connector cards using HTML</span></span>

<span data-ttu-id="77a74-192">Na área de trabalho, a formatação HTML para cartões de conector tem a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="77a74-192">On the desktop, HTML formatting for connector cards looks like this:</span></span>

![Formatação HTML para cartões de conector no cliente de desktop](~/assets/images/cards/Connector-desktop-html-combined.png)

<span data-ttu-id="77a74-194">No iOS, a formatação HTML tem a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="77a74-194">On iOS, HTML formatting looks like this:</span></span>

![Formatação HTML para cartões de conector no cliente iOS](~/assets/images/cards/connector-iphone-html-combined-80.png)

<span data-ttu-id="77a74-196">Problemas</span><span class="sxs-lookup"><span data-stu-id="77a74-196">Issues:</span></span>

* <span data-ttu-id="77a74-197">As imagens embutidas não são renderizadas no iOS usando a redução ou HTML em cartões de conexão.</span><span class="sxs-lookup"><span data-stu-id="77a74-197">Inline images are not rendered on iOS using either markdown or HTML in Connector Cards.</span></span>
* <span data-ttu-id="77a74-198">O texto pré-formatado é renderizado, mas não tem um plano de fundo cinza.</span><span class="sxs-lookup"><span data-stu-id="77a74-198">Preformatted text is rendered but does not have a gray background.</span></span>

<span data-ttu-id="77a74-199">No Android, a formatação HTML tem a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="77a74-199">On Android, HTML formatting looks like this:</span></span>

![Formatação HTML para cartões de conector no cliente Android](~/assets/images/cards/connector-android-html-combined.png)

### <a name="formatting-sample-for-html-connector-cards"></a><span data-ttu-id="77a74-201">Exemplo de formatação para cartões de conexão HTML</span><span class="sxs-lookup"><span data-stu-id="77a74-201">Formatting sample for HTML Connector Cards</span></span>

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

## <a name="markdown-formatting-for-connector-cards"></a><span data-ttu-id="77a74-202">Redução da formatação de cartões de conector</span><span class="sxs-lookup"><span data-stu-id="77a74-202">Markdown formatting for Connector Cards</span></span>

<span data-ttu-id="77a74-203">Os cartões de conector dão suporte à redução limitada e à formatação HTML.</span><span class="sxs-lookup"><span data-stu-id="77a74-203">Connector cards support limited markdown and HTML formatting.</span></span> <span data-ttu-id="77a74-204">HTML é descrito na última seção.</span><span class="sxs-lookup"><span data-stu-id="77a74-204">HTML is described in the last section.</span></span>

| <span data-ttu-id="77a74-205">Estilo</span><span class="sxs-lookup"><span data-stu-id="77a74-205">Style</span></span> | <span data-ttu-id="77a74-206">Exemplo</span><span class="sxs-lookup"><span data-stu-id="77a74-206">Example</span></span> | <span data-ttu-id="77a74-207">Markdown</span><span class="sxs-lookup"><span data-stu-id="77a74-207">Markdown</span></span> |
| --- | --- | --- |
| <span data-ttu-id="77a74-208">bold</span><span class="sxs-lookup"><span data-stu-id="77a74-208">bold</span></span> | <span data-ttu-id="77a74-209">**text**</span><span class="sxs-lookup"><span data-stu-id="77a74-209">**text**</span></span> | `**text**` |
| <span data-ttu-id="77a74-210">italic</span><span class="sxs-lookup"><span data-stu-id="77a74-210">italic</span></span> | <span data-ttu-id="77a74-211">*text*</span><span class="sxs-lookup"><span data-stu-id="77a74-211">*text*</span></span> | `*text*` |
| <span data-ttu-id="77a74-212">cabeçalho (níveis 1&ndash;3)</span><span class="sxs-lookup"><span data-stu-id="77a74-212">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="77a74-213">**Text**</span><span class="sxs-lookup"><span data-stu-id="77a74-213">**Text**</span></span> | `### Text`|
| <span data-ttu-id="77a74-214">tachado</span><span class="sxs-lookup"><span data-stu-id="77a74-214">strikethrough</span></span> | <span data-ttu-id="77a74-215">~~text~~</span><span class="sxs-lookup"><span data-stu-id="77a74-215">~~text~~</span></span> | `~~text~~` |
| <span data-ttu-id="77a74-216">lista não ordenada</span><span class="sxs-lookup"><span data-stu-id="77a74-216">unordered list</span></span> | <ul><li><span data-ttu-id="77a74-217">texto</span><span class="sxs-lookup"><span data-stu-id="77a74-217">text</span></span></li><li><span data-ttu-id="77a74-218">texto</span><span class="sxs-lookup"><span data-stu-id="77a74-218">text</span></span></li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| <span data-ttu-id="77a74-219">lista ordenada</span><span class="sxs-lookup"><span data-stu-id="77a74-219">ordered list</span></span> | <ol><li><span data-ttu-id="77a74-220">texto</span><span class="sxs-lookup"><span data-stu-id="77a74-220">text</span></span></li><li><span data-ttu-id="77a74-221">texto</span><span class="sxs-lookup"><span data-stu-id="77a74-221">text</span></span></li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| <span data-ttu-id="77a74-222">texto pré-formatado</span><span class="sxs-lookup"><span data-stu-id="77a74-222">preformatted text</span></span> | `text` | ``preformatted text`` |
| <span data-ttu-id="77a74-223">blockquote</span><span class="sxs-lookup"><span data-stu-id="77a74-223">blockquote</span></span> | <span data-ttu-id="77a74-224">>texto blockquote</span><span class="sxs-lookup"><span data-stu-id="77a74-224">>blockquote text</span></span> | `>blockquote text` |
| <span data-ttu-id="77a74-225">hyperlink</span><span class="sxs-lookup"><span data-stu-id="77a74-225">hyperlink</span></span> | [<span data-ttu-id="77a74-226">Bing</span><span class="sxs-lookup"><span data-stu-id="77a74-226">Bing</span></span>](https://www.bing.com/) | `[Bing](https://www.bing.com/)` |
| <span data-ttu-id="77a74-227">link de imagem</span><span class="sxs-lookup"><span data-stu-id="77a74-227">image link</span></span> |![Pato em uma pedra](https://aka.ms/Fo983c) | `![Duck](https://aka.ms/Fo983c)` |

<span data-ttu-id="77a74-229">Nos cartões conectores, as novas linhas são `\n\n`renderizadas para, `\n` mas `\r`não para ou.</span><span class="sxs-lookup"><span data-stu-id="77a74-229">In connector cards, newlines are rendered for `\n\n`, but not for `\n` or `\r`.</span></span>

### <a name="mobile-and-desktop-differences-for-connector-cards-using-markdown"></a><span data-ttu-id="77a74-230">Diferenças de dispositivos móveis e de área de trabalho para cartões de conexão usando redução</span><span class="sxs-lookup"><span data-stu-id="77a74-230">Mobile and desktop differences for connector cards using markdown</span></span>

<span data-ttu-id="77a74-231">Na área de trabalho, a redução da formatação de cartões de conector tem a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="77a74-231">On the desktop, markdown formatting for connector cards looks like this:</span></span>

![Formatação HTML para cartões de conector no cliente de desktop](~/assets/images/cards/connector-desktop-markdown-combined.png)

<span data-ttu-id="77a74-233">No iOS, a redução da formatação de cartões de conector tem a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="77a74-233">On iOS, markdown formatting for connector cards looks like this:</span></span>

![Formatação HTML para cartões de conector no cliente iOS](~/assets/images/cards/connector-iphone-markdown-combined-80.png)

<span data-ttu-id="77a74-235">Problemas</span><span class="sxs-lookup"><span data-stu-id="77a74-235">Issues:</span></span>

* <span data-ttu-id="77a74-236">O cliente iOS para Teams não renderiza a redução ou as imagens embutidas HTML nos cartões de conector.</span><span class="sxs-lookup"><span data-stu-id="77a74-236">The iOS client for Teams does not render markdown or HTML inline images in Connector Cards.</span></span>
* <span data-ttu-id="77a74-237">Blockquotes são renderizados como recuados, mas sem um plano de fundo cinza.</span><span class="sxs-lookup"><span data-stu-id="77a74-237">Blockquotes are rendered as indented but without a gray background.</span></span>

<span data-ttu-id="77a74-238">No Android, a redução da formatação de cartões de conector tem a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="77a74-238">On Android, markdown formatting for connector cards looks like this:</span></span>

![Formatação HTML para cartões de conector no cliente Android](~/assets/images/cards/connector-android-markdown-combined.png)

### <a name="formatting-example-for-markdown-connector-cards"></a><span data-ttu-id="77a74-240">Exemplo de formatação para redução de cartões de conector</span><span class="sxs-lookup"><span data-stu-id="77a74-240">Formatting example for markdown Connector Cards</span></span>

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

## <a name="html-formatting-for-simple-cards"></a><span data-ttu-id="77a74-241">Formatação HTML para cartões simples</span><span class="sxs-lookup"><span data-stu-id="77a74-241">HTML Formatting for simple cards</span></span>

<span data-ttu-id="77a74-242">Essas marcas HTML têm suporte para cartões simples como o herói e o cartão de miniatura.</span><span class="sxs-lookup"><span data-stu-id="77a74-242">These HTML tags are supported for simple cards such as the hero and thumbnail card.</span></span> <span data-ttu-id="77a74-243">Não há suporte para redução.</span><span class="sxs-lookup"><span data-stu-id="77a74-243">Markdown is not supported.</span></span>

| <span data-ttu-id="77a74-244">Estilo</span><span class="sxs-lookup"><span data-stu-id="77a74-244">Style</span></span> | <span data-ttu-id="77a74-245">Exemplo</span><span class="sxs-lookup"><span data-stu-id="77a74-245">Example</span></span> | <span data-ttu-id="77a74-246">HTML</span><span class="sxs-lookup"><span data-stu-id="77a74-246">HTML</span></span> |
| --- | --- | --- |
| <span data-ttu-id="77a74-247">bold</span><span class="sxs-lookup"><span data-stu-id="77a74-247">bold</span></span> | <span data-ttu-id="77a74-248">**text**</span><span class="sxs-lookup"><span data-stu-id="77a74-248">**text**</span></span> | `<strong>text</strong>` |
| <span data-ttu-id="77a74-249">italic</span><span class="sxs-lookup"><span data-stu-id="77a74-249">italic</span></span> | <span data-ttu-id="77a74-250">*text*</span><span class="sxs-lookup"><span data-stu-id="77a74-250">*text*</span></span> | `<em>text</em>` |
| <span data-ttu-id="77a74-251">cabeçalho (níveis 1&ndash;3)</span><span class="sxs-lookup"><span data-stu-id="77a74-251">header (levels 1&ndash;3)</span></span> | <span data-ttu-id="77a74-252">**Text**</span><span class="sxs-lookup"><span data-stu-id="77a74-252">**Text**</span></span> | `<h3>Text</h3>` |
| <span data-ttu-id="77a74-253">tachado</span><span class="sxs-lookup"><span data-stu-id="77a74-253">strikethrough</span></span> | <span data-ttu-id="77a74-254">~~text~~</span><span class="sxs-lookup"><span data-stu-id="77a74-254">~~text~~</span></span> | `<strike>text</strike>` |
| <span data-ttu-id="77a74-255">lista não ordenada</span><span class="sxs-lookup"><span data-stu-id="77a74-255">unordered list</span></span> | <ul><li><span data-ttu-id="77a74-256">texto</span><span class="sxs-lookup"><span data-stu-id="77a74-256">text</span></span></li><li><span data-ttu-id="77a74-257">texto</span><span class="sxs-lookup"><span data-stu-id="77a74-257">text</span></span></li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| <span data-ttu-id="77a74-258">lista ordenada</span><span class="sxs-lookup"><span data-stu-id="77a74-258">ordered list</span></span> | <ol><li><span data-ttu-id="77a74-259">texto</span><span class="sxs-lookup"><span data-stu-id="77a74-259">text</span></span></li><li><span data-ttu-id="77a74-260">texto</span><span class="sxs-lookup"><span data-stu-id="77a74-260">text</span></span></li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| <span data-ttu-id="77a74-261">texto pré-formatado</span><span class="sxs-lookup"><span data-stu-id="77a74-261">preformatted text</span></span> | `text` | `<pre>text</pre>` |
| <span data-ttu-id="77a74-262">blockquote</span><span class="sxs-lookup"><span data-stu-id="77a74-262">blockquote</span></span> | <blockquote><span data-ttu-id="77a74-263">texto</span><span class="sxs-lookup"><span data-stu-id="77a74-263">text</span></span></blockquote> | `<blockquote>text</blockquote>` |
| <span data-ttu-id="77a74-264">hyperlink</span><span class="sxs-lookup"><span data-stu-id="77a74-264">hyperlink</span></span> | [<span data-ttu-id="77a74-265">Bing</span><span class="sxs-lookup"><span data-stu-id="77a74-265">Bing</span></span>](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| <span data-ttu-id="77a74-266">link de imagem</span><span class="sxs-lookup"><span data-stu-id="77a74-266">image link</span></span> |<img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img>| `<img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

### <a name="mobile-and-desktop-differences-for-simple-cards"></a><span data-ttu-id="77a74-267">Diferenças móveis e de área de trabalho para cartões simples</span><span class="sxs-lookup"><span data-stu-id="77a74-267">Mobile and desktop differences for simple cards</span></span>

<span data-ttu-id="77a74-268">Devido às diferenças de resolução entre a área de trabalho e a plataforma móvel, a formatação é diferente entre a área de trabalho e a versão móvel do teams.</span><span class="sxs-lookup"><span data-stu-id="77a74-268">Because of resolution differences between the desktop and mobile platform, formatting is different between the desktop and the mobile version of Teams.</span></span>

<span data-ttu-id="77a74-269">Na área de trabalho, a formatação HTML aparece da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="77a74-269">On the desktop, HTML formatting appears like this:</span></span>

![Formatação HTML no cliente de desktop](~/assets/images/cards/card-formatting-xml-desktop-v2.png)

<span data-ttu-id="77a74-271">No iOS, a formatação HTML aparece da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="77a74-271">On iOS, HTML formatting appears like this:</span></span>

![Formatação HTML no cliente iOS](~/assets/images/cards/card-formatting-xml-mobile-v2.png)

<span data-ttu-id="77a74-273">Problemas</span><span class="sxs-lookup"><span data-stu-id="77a74-273">Issues:</span></span>

* <span data-ttu-id="77a74-274">A formatação de caracteres como negrito e itálico não é renderizada no iOS.</span><span class="sxs-lookup"><span data-stu-id="77a74-274">Character formatting like bold and italic are not rendered on iOS.</span></span>

<span data-ttu-id="77a74-275">No Android, a formatação HTML aparece da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="77a74-275">On Android, HTML formatting appears like this:</span></span>

![Formatação HTML no cliente Android](~/assets/images/cards/card-formatting-xml-android-60.png)

<span data-ttu-id="77a74-277">Formatação de caracteres como negrito e itálico são exibidos corretamente no Android.</span><span class="sxs-lookup"><span data-stu-id="77a74-277">Character formatting like bold and italic display correctly on Android.</span></span>

### <a name="formatting-sample-for-html-formatting-in-simple-cards"></a><span data-ttu-id="77a74-278">Exemplo de formatação para formatação HTML em cartões simples</span><span class="sxs-lookup"><span data-stu-id="77a74-278">Formatting sample for HTML formatting in simple cards</span></span>

<span data-ttu-id="77a74-279">Essas capturas de tela foram criadas usando o Teams AppStudio, onde a propriedade Text de um cartão herói foi definida como a cadeia de caracteres a seguir.</span><span class="sxs-lookup"><span data-stu-id="77a74-279">These screenshots were created using Teams AppStudio, where the text property of a hero card was set to the following string.</span></span> <span data-ttu-id="77a74-280">Você pode testar a formatação em seus próprios cartões modificando esse código.</span><span class="sxs-lookup"><span data-stu-id="77a74-280">You can test formatting in your own cards by modifying this code.</span></span>

`<p>bold: <strong>Bold Text</strong></p><p>italic: <em>Italic Text</em></p><p>strikethrough: <strike>Strikethrough text</strike></p><h1>Header 1</h1><h2>Header 2</h2><h3>Header 3</h3><p>bullet list: <ul><li>text</li><li>text</li></ul></p><p>ordered list: <ol><li>text</li><li>text</li></ol></p><pre>preformatted text</pre><blockquote>blockquote text</blockquote></p><p>hyperlink: <a href=\"https://www.bing.com/\">Bing</a></p><p>embedded image: <img src=\"http://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img></p>`
