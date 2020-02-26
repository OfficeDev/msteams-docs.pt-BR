---
title: Formatação de texto em cartões
description: Descreve a formatação de texto do cartão no Microsoft Teams
keywords: formato de cartões de bots da equipe
ms.date: 03/29/2018
ms.openlocfilehash: 21adabe35011ba77d888165b9be7a544284cb1a3
ms.sourcegitcommit: 67c021fa20eb5ea70c059fcc35be1c19c6c97c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "42279778"
---
# <a name="format-cards-in-teams"></a>Formatar cartões no Teams

Você pode adicionar formatação de Rich Text aos seus cartões usando redução ou HTML, dependendo do tipo de cartão.

Os cartões dão suporte à formatação somente na propriedade Text, e não nas propriedades Title ou subtítulo. A formatação pode ser especificada usando um subconjunto de formatação XML (HTML) ou redução, dependendo do tipo de cartão. Para obter cartões adaptáveis de desenvolvimento futuro AMD atuais usando a formatação de redução é recomendável.

O suporte à formatação difere entre diferentes tipos de cartão, e a renderização do cartão pode diferir ligeiramente entre a área de trabalho e os clientes do Mobile Teams, bem como o Microsoft Teams no navegador da área de trabalho.

Você pode incluir uma imagem embutida em qualquer placa do teams. As imagens são formatadas `.png`como `.jpg`, ou `.gif` arquivos, e não devem exceder 1024 × 1024 PX ou 1 MB. GIF animado não é oficialmente suportado. *Consulte* [referência de cartões](./cards-reference.md#inline-card-images)

## <a name="formatting-cards-with-markdown"></a>Formatando cartões com redução

Há dois tipos de cartões que dão suporte à redução no Microsoft Teams:

> [!div class="checklist"]
> * **Cartões adaptáveis**: a redução é suportada no `Textblock` campo de cartão adaptável, `Fact.Title` bem `Fact.Value`como e. O HTML não é suportado em cartões adaptáveis.
> * **Cartões de conector do O365**: redução e HTML limitado são suportados nos cartões de conector do Office 365 nos campos de texto.

# <a name="markdown-formatting-adaptive-cards"></a>[**Formatação de redução: cartões adaptáveis**](#tab/adaptive-md)

 Os estilos suportados para `Textblock` `Fact.Title` e `Fact.Value` são:

| Estilo | Exemplo | Markdown |
| --- | --- | --- |
| bold | **Negrito** | ```**Bold**``` |
| italic | _Itálico_ | ```_Italic_``` |
| lista não ordenada | <ul><li>texto</li><li>texto</li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| lista ordenada | <ol><li>texto</li><li>texto</li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| Hiperlinks |[Bing](https://www.bing.com/)| ```[Title](url)``` |

Não há suporte para as seguintes marcas de redução:

* Cabeçalhos
* Tabelas
* Imagens
* Texto pré-formatado
* Blockquote

> [!IMPORTANT]
> Os cartões adaptáveis não dão suporte a qualquer formatação HTML.

### <a name="newlines-for-adaptive-cards"></a>Novas linhas para cartões adaptáveis

Nas listas, você pode usar `\r` as `\n` sequências de escape ou de saída para novas linhas. Usar `\n\n` em uma lista fará com que o próximo elemento na lista seja recuado. Se você precisar de novas linhas em qualquer lugar no TextBlock `\n\n`, use.

### <a name="mobile-and-desktop-differences-for-adaptive-cards"></a>Diferenças móveis e de área de trabalho para cartões adaptáveis

A formatação é um pouco diferente entre a área de trabalho e as versões móveis do teams.

Na área de trabalho, a formatação de redução de cartão adaptável aparece como esta nos dois navegadores da Web e no aplicativo cliente do teams:

![Formatação de redução de cartão adaptável no cliente de desktop](/assets/images/cards/Adaptive-markdown-desktop-client.png)

No iOS, a formatação de redução de cartão adaptável aparece da seguinte maneira:

![Formatação de redução de cartão adaptável no iOS](/assets/images/cards/Adaptive-markdown-iOS-75.png)

No Android, a formatação de redução de cartão adaptável aparece da seguinte maneira:

![Formatação de redução de cartão adaptável no Android](/assets/images/cards/Adaptive-markdown-Android.png)

### <a name="more-information-on-adaptive-cards"></a>Mais informações sobre cartões adaptáveis

[Recursos de texto em cartões adaptáveis](/adaptive-cards/create/textfeatures) Os recursos de data e localização mencionados neste tópico não têm suporte no Microsoft Teams.

### <a name="formatting-sample-for-adaptive-cards"></a>Exemplo de formatação para cartões adaptáveis

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

### <a name="mention-support-within-adaptive-cards"></a>Mencione o suporte de cartões adaptáveis

> [!NOTE]
> Mencione o suporte nos cartões atualmente é suportado apenas na [visualização do desenvolvedor](../../resources/dev-preview/developer-preview-intro.md) .

Os bots e as extensões de mensagens agora podem incluir menção dentro do conteúdo do cartão nos elementos bloco de texto e FactSet.

### <a name="constructing-mentions"></a>Como criar menção

Para incluir uma menção em um cartão adaptável, seu aplicativo precisa incluir os seguintes elementos

* `<at>username</at>`nos elementos de cartão adaptável com suporte
* O `mention` objeto dentro de uma `msteams` Propriedade no conteúdo do cartão, que inclui a ID de usuário do Team do usuário que está sendo mencionado

Observe que os cartões com menção não têm suporte em clientes móveis no momento.

### <a name="sample-adaptive-card-with-a-mention"></a>Cartão adaptável de amostra com menção

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

# <a name="markdown-formatting-o365-connector-cards"></a>[**Formatação de redução: cartões de conector do O365**](#tab/connector-md)

Os cartões de conector dão suporte à redução limitada e à formatação HTML. O suporte a HTML é descrito na última seção.

| Estilo | Exemplo | Markdown |
| --- | --- | --- |
| bold | **text** | `**text**` |
| italic | *text* | `*text*` |
| cabeçalho (níveis 1&ndash;3) | **Text** | `### Text`|
| tachado | ~~text~~ | `~~text~~` |
| lista não ordenada | <ul><li>texto</li><li>texto</li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| lista ordenada | <ol><li>texto</li><li>texto</li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| texto pré-formatado | `text` | ``preformatted text`` |
| blockquote | >texto blockquote | `>blockquote text` |
| hyperlink | [Bing](https://www.bing.com/) | `[Bing](https://www.bing.com/)` |
| link de imagem |![Pato em uma pedra](https://aka.ms/Fo983c) | `![Duck](https://aka.ms/Fo983c)` |

Nos cartões conectores, as novas linhas são `\n\n`renderizadas para, `\n` mas `\r`não para ou.

### <a name="mobile-and-desktop-differences-for-connector-cards-using-markdown"></a>Diferenças de dispositivos móveis e de área de trabalho para cartões de conexão usando redução

Na área de trabalho, a redução da formatação de cartões de conector tem a seguinte aparência:

![Redução da formatação de cartões de conector no cliente de desktop](/assets/images/cards/connector-desktop-markdown-combined.png)

No iOS, a redução da formatação de cartões de conector tem a seguinte aparência:

![Redução da formatação de cartões de conector no cliente iOS](/assets/images/cards/connector-iphone-markdown-combined-80.png)

Problemas

* O cliente iOS para Teams não renderiza a redução ou as imagens embutidas HTML nos cartões de conector.
* Blockquotes são renderizados como recuados, mas sem um plano de fundo cinza.

No Android, a redução da formatação de cartões de conector tem a seguinte aparência:

![Redução da formatação de cartões de conector no cliente Android](/assets/images/cards/connector-android-markdown-combined.png)

### <a name="formatting-example-for-markdown-connector-cards"></a>Exemplo de formatação para redução de cartões de conector

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

## <a name="formatting-cards-with-html"></a>Formatando cartões com HTML

# <a name="html-formatting-o365-connector-cards"></a>[**Formatação HTML: cartões de conector do O365**](#tab/connector-html)

Os cartões de conector dão suporte à redução limitada e à formatação HTML. A redução é descrita na próxima seção.

| Estilo | Exemplo | HTML |
| --- | --- | --- |
| bold | **text** | `<strong>text</strong>` |
| italic | *text* | `<em>text</em>` |
| cabeçalho (níveis 1&ndash;3) | **Text** | `<h3>Text</h3>` |
| tachado | ~~text~~ | `<strike>text</strike>` |
| lista não ordenada | <ul><li>texto</li><li>texto</li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| lista ordenada | <ol><li>texto</li><li>texto</li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| texto pré-formatado | `text` | `<pre>text</pre>` |
| blockquote | <blockquote>texto</blockquote> | `<blockquote>text</blockquote>` |
| hyperlink | [Bing](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| link de imagem | <img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img> | `<img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

Em cartões de conector, as novas linhas são renderizadas em `<p>` HTML usando a marca.

### <a name="mobile-and-desktop-differences-for-connector-cards-using-html"></a>Diferenças móveis e de área de trabalho para cartões de conexão usando HTML

Na área de trabalho, a formatação HTML para cartões de conector tem a seguinte aparência:

![Formatação HTML para cartões de conector no cliente de desktop](/assets/images/cards/Connector-desktop-html-combined.png)

No iOS, a formatação HTML tem a seguinte aparência:

![Formatação HTML para cartões de conector no cliente iOS](/assets/images/cards/connector-iphone-html-combined-80.png)

Problemas

* As imagens embutidas não são renderizadas no iOS usando a redução ou HTML em cartões de conexão.
* O texto pré-formatado é renderizado, mas não tem um plano de fundo cinza.

No Android, a formatação HTML tem a seguinte aparência:

![Formatação HTML para cartões de conector no cliente Android](/assets/images/cards/connector-android-html-combined.png)

### <a name="formatting-sample-for-html-connector-cards"></a>Exemplo de formatação para cartões de conexão HTML

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

# <a name="html-formatting-hero-and-thumbnail-cards"></a>[**Formatação HTML: herói e cartões de miniatura**](#tab/simple-html)

Marcas HTML têm suporte para cartões simples como o herói e o cartão de miniatura. Não há suporte para redução.

| Estilo | Exemplo | HTML |
| --- | --- | --- |
| bold | **text** | `<strong>text</strong>` |
| italic | *text* | `<em>text</em>` |
| cabeçalho (níveis 1&ndash;3) | **Text** | `<h3>Text</h3>` |
| tachado | ~~text~~ | `<strike>text</strike>` |
| lista não ordenada | <ul><li>texto</li><li>texto</li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| lista ordenada | <ol><li>texto</li><li>texto</li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| texto pré-formatado | `text` | `<pre>text</pre>` |
| blockquote | <blockquote>texto</blockquote> | `<blockquote>text</blockquote>` |
| hyperlink | [Bing](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| link de imagem |<img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img>| `<img src="http://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

### <a name="mobile-and-desktop-differences-for-simple-cards"></a>Diferenças móveis e de área de trabalho para cartões simples

Devido às diferenças de resolução entre a área de trabalho e a plataforma móvel, a formatação é diferente entre a área de trabalho e a versão móvel do teams.

Na área de trabalho, a formatação HTML aparece da seguinte maneira:

![Formatação HTML no cliente de desktop](/assets/images/cards/card-formatting-xml-desktop-v2.png)

No iOS, a formatação HTML aparece da seguinte maneira:

![Formatação HTML no cliente iOS](/assets/images/cards/card-formatting-xml-mobile-v2.png)

Problemas

* A formatação de caracteres como negrito e itálico não é renderizada no iOS.

No Android, a formatação HTML aparece da seguinte maneira:

![Formatação HTML no cliente Android](/assets/images/cards/card-formatting-xml-android-60.png)

Formatação de caracteres como negrito e itálico são exibidos corretamente no Android.

### <a name="formatting-sample-for-html-formatting-in-simple-cards"></a>Exemplo de formatação para formatação HTML em cartões simples

Essas capturas de tela foram criadas usando o Teams AppStudio, onde a propriedade Text de um cartão herói foi definida como a cadeia de caracteres a seguir. Você pode testar a formatação em seus próprios cartões modificando esse código.

`<p>bold: <strong>Bold Text</strong></p><p>italic: <em>Italic Text</em></p><p>strikethrough: <strike>Strikethrough text</strike></p><h1>Header 1</h1><h2>Header 2</h2><h3>Header 3</h3><p>bullet list: <ul><li>text</li><li>text</li></ul></p><p>ordered list: <ol><li>text</li><li>text</li></ol></p><pre>preformatted text</pre><blockquote>blockquote text</blockquote></p><p>hyperlink: <a href=\"https://www.bing.com/\">Bing</a></p><p>embedded image: <img src=\"http://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img></p>`

---
