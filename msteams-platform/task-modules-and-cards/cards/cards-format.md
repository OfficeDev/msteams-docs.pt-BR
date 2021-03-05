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
# <a name="format-cards-in-teams"></a>Formatar cartões no Teams

Você pode adicionar formatação de rich text aos cartões usando Markdown ou HTML, dependendo do tipo de cartão.

Os cartões suportam formatação somente na propriedade text, não nas propriedades title ou subtitle. A formatação pode ser especificada usando um subconjunto de formatação XML (HTML) ou Markdown, dependendo do tipo de cartão. Para cartões adaptáveis de desenvolvimento atual e futuro usando formatação Markdown é recomendável.

O suporte à formatação difere entre tipos de cartão diferentes, e a renderização do cartão pode diferir ligeiramente entre a área de trabalho e os clientes do Teams móveis, bem como o Teams no navegador da área de trabalho.

Você pode incluir uma imagem em linha com qualquer cartão do Teams. Imagens formatadas como , ou arquivos e não devem exceder  `.png` `.jpg` `.gif` 1024 ×1024 px ou 1 MB. Gif animado não tem suporte oficial. *Consulte* [Referência de cartões](./cards-reference.md#inline-card-images)

## <a name="formatting-cards-with-markdown"></a>Formatação de cartões com Markdown

Há dois tipos de cartão que suportam Markdown no Teams:

> [!div class="checklist"]
> * **Cartões adaptáveis**: a marcação é suportada no campo cartão `Textblock` adaptável, bem como `Fact.Title` e `Fact.Value` . HTML não é suportado em cartões adaptáveis.
> * Cartões de conector **O365**: Markdown e HTML limitado são suportados em cartões do Conector do Office 365 nos campos de texto.

# <a name="markdown-formatting-adaptive-cards"></a>[**Formatação de marcação: cartões adaptáveis**](#tab/adaptive-md)

 Os estilos com suporte `Textblock` para e `Fact.Title` `Fact.Value` são:

| Style | Exemplo | Markdown |
| --- | --- | --- |
| bold | **Negrito** | ```**Bold**``` |
| italic | _Itálico_ | ```_Italic_``` |
| lista semordenagem | <ul><li>texto</li><li>texto</li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| lista ordenada | <ol><li>texto</li><li>texto</li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| Hiperlinks |[Bing](https://www.bing.com/)| ```[Title](url)``` |

As seguintes marcas Markdown não são suportadas:

* Cabeçalhos
* Tabelas
* Imagens
* Texto pré-formatado
* Blockquotes

> [!IMPORTANT]
> Cartões adaptáveis não suportam formatação HTML.

### <a name="newlines-for-adaptive-cards"></a>Linhas novas para cartões adaptáveis

Em listas, você pode usar `\r` as `\n` sequências de escape ou para newlines. Usar `\n\n` em uma lista fará com que o próximo elemento da lista seja recuado. Se você precisar de linhas novas em outro lugar do bloco de texto, use `\n\n` .

### <a name="mobile-and-desktop-differences-for-adaptive-cards"></a>Diferenças de dispositivos móveis e de área de trabalho para cartões adaptáveis

A formatação é ligeiramente diferente entre a área de trabalho e as versões móveis do Teams.

Na área de trabalho, a formatação de Markdown de cartão adaptável aparece assim nos navegadores da Web e no aplicativo cliente do Teams:

![Formatação de markdown de cartão adaptável no cliente da área de trabalho](../../assets/images/cards/Adaptive-markdown-desktop-client.png)

No iOS, a formatação De marcação de cartão adaptável aparece assim:

![Formatação de markdown de cartão adaptável no iOS](../../assets/images/cards/Adaptive-markdown-iOS-75.png)

No Android, a formatação adaptável de Marcação de Cartão aparece assim:

![Formatação de markdown de cartão adaptável no Android](../../assets/images/cards/Adaptive-markdown-Android.png)

### <a name="more-information-on-adaptive-cards"></a>Mais informações sobre cartões adaptáveis

[Recursos de texto em cartões adaptáveis](/adaptive-cards/create/textfeatures) Os recursos de data e localização mencionados neste tópico não são suportados no Teams.

### <a name="formatting-sample-for-adaptive-cards"></a>Exemplo de formatação para cartões adaptáveis

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

### <a name="mention-support-within-adaptive-cards-v12"></a>Mencionar suporte em cartões adaptáveis v1.2

As menções baseadas em cartão são suportadas em clientes Web, Desktop e móveis. Você pode adicionar @ menções em um corpo de cartão adaptável para bots e respostas de extensão de mensagens.  Para adicionar @ menções em cartões, siga a mesma lógica de notificação e renderização das menções baseadas em mensagens em conversas de chat de canal [e grupo.](../../bots/how-to/conversations/channel-and-group-conversations.md#working-with-mentions )

Bots e extensões de mensagens podem incluir menções no conteúdo do cartão nos [elementos TextBlock](https://adaptivecards.io/explorer/TextBlock.html) e [FactSet.](https://adaptivecards.io/explorer/FactSet.html)

> [!NOTE]
> * [Os elementos de](https://adaptivecards.io/explorer/Media.html) mídia atualmente não são suportados em cartões adaptáveis v1.2 na plataforma teams.
> * As & de equipe não são suportadas em mensagens bot.

#### <a name="constructing-mentions"></a>Criar menções

Para incluir uma menção em um cartão Adaptável, seu aplicativo precisa incluir os seguintes elementos

* `<at>username</at>` nos elementos de cartão adaptáveis com suporte
* O objeto dentro de uma propriedade no conteúdo do cartão, que inclui a id de usuário do `mention` Teams do usuário que está sendo `msteams` mencionado

#### <a name="sample-adaptive-card-with-a-mention"></a>Exemplo de cartão adaptável com uma menção

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


### <a name="information-masking-in-adaptive-cards"></a>Mascaramento de informações em cartões adaptáveis
Use a propriedade mascarar informações para mascarar informações específicas, como senha ou informações confidenciais dos usuários.

> [!NOTE]
> A propriedade de mascaramento de informações está disponível apenas na visualização do desenvolvedor.

#### <a name="mask-information"></a>Informações sobre máscara
Para mascarar informações em cartões adaptáveis, adicione a propriedade para `isMasked` **digitar** e de definir seu valor `Input.Text` como *true*.

#### <a name="sample-adaptive-card-with-masking-property"></a>Cartão adaptável de exemplo com a propriedade mascaramento

```json
{
    "type": "Input.Text",
    "id": "secretThing",
    "style": "password",
    "isMasked": true
  },
```

A imagem a seguir é um exemplo de informações de mascaramento em cartões adaptáveis:

![Imagem de informações de mascaramento](../../assets/images/cards/masking-information-view.png)

### <a name="full-width-adaptive-card"></a>Cartão adaptável de largura total
Você pode usar a propriedade para expandir a largura de um `msteams` cartão Adaptável e usar espaço adicional de tela. Para obter informações sobre como usar a propriedade, consulte o exemplo a seguir:

#### <a name="constructing-full-width-cards"></a>Construir cartões de largura total
Para fazer um cartão adaptável de largura total, o objeto na propriedade no conteúdo do cartão deve `width` `msteams` ser definido como `Full` .
Além disso, seu aplicativo deve incluir os seguintes elementos:

#### <a name="sample-adaptive-card-with-full-width"></a>Exemplo de cartão adaptável com largura total

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

Um Cartão Adaptável de largura total aparece da seguinte forma: Exibição de Cartão Adaptável de largura ![ total](../../assets/images/cards/full-width-adaptive-card.png)

Se você não tiver definido a propriedade como Full , o modo de exibição padrão do Cartão Adaptável será o seguinte: Modo de exibição cartão adaptável de largura `width`  ![ pequena](../../assets/images/cards/small-width-adaptive-card.png)



# <a name="markdown-formatting-o365-connector-cards"></a>[**Formatação de marcação: cartões de conector O365**](#tab/connector-md)

Os cartões conectores suportam a formatação limitada markdown e HTML. O suporte HTML é descrito na última seção.

| Style | Exemplo | Markdown |
| --- | --- | --- |
| bold | **text** | `**text**` |
| italic | *text* | `*text*` |
| header (níveis 1 &ndash; 3) | **Text** | `### Text`|
| strikethrough | ~~text~~ | `~~text~~` |
| lista semordenagem | <ul><li>texto</li><li>texto</li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| lista ordenada | <ol><li>texto</li><li>texto</li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| texto pré-formatado | `text` | ``preformatted text`` |
| blockquote | >texto blockquote | `>blockquote text` |
| hiperlink | [Bing](https://www.bing.com/) | `[Bing](https://www.bing.com/)` |
| link de imagem |![Duck on a rock](https://aka.ms/Fo983c) | `![Duck](https://aka.ms/Fo983c)` |

Em cartões de conector, as linhas novas são renderizadas `\n\n` para , mas não para ou `\n` `\r` .

### <a name="mobile-and-desktop-differences-for-connector-cards-using-markdown"></a>Diferenças de dispositivos móveis e de área de trabalho para cartões de conector usando Markdown

Na área de trabalho, a formatação markdown para cartões de conector tem a mesma aparência:

![Formatação de marcação para cartões conectores no cliente desktop](../../assets/images/cards/connector-desktop-markdown-combined.png)

No iOS, a formatação markdown para cartões de conector tem a aparência:

![Formatação de marcação para cartões conectores no cliente iOS](../../assets/images/cards/connector-iphone-markdown-combined-80.png)

Problemas:

* O cliente iOS do Teams não renderiza imagens em linha Markdown ou HTML em Cartões conectores.
* As blockquotes são renderizadas como recuadas, mas sem um plano de fundo cinza.

No Android, a formatação markdown para cartões de conector tem a aparência:

![Formatação de marcação para cartões conectores no cliente Android](../../assets/images/cards/connector-android-markdown-combined.png)

### <a name="formatting-example-for-markdown-connector-cards"></a>Exemplo de formatação para Cartões de Conector de Markdown

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

## <a name="formatting-cards-with-html"></a>Formatação de cartões com HTML

# <a name="html-formatting-o365-connector-cards"></a>[**Formatação HTML: Cartões de conector O365**](#tab/connector-html)

Os cartões conectores suportam a formatação limitada markdown e HTML. Markdown é descrito na próxima seção.

| Style | Exemplo | HTML |
| --- | --- | --- |
| bold | **text** | `<strong>text</strong>` |
| italic | *text* | `<em>text</em>` |
| header (níveis 1 &ndash; 3) | **Text** | `<h3>Text</h3>` |
| strikethrough | ~~text~~ | `<strike>text</strike>` |
| lista semordenagem | <ul><li>texto</li><li>texto</li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| lista ordenada | <ol><li>texto</li><li>texto</li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| texto pré-formatado | `text` | `<pre>text</pre>` |
| blockquote | <blockquote>texto</blockquote> | `<blockquote>text</blockquote>` |
| hiperlink | [Bing](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| link de imagem | <img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img> | `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

Em cartões de conector, as linhas novas são renderizadas em HTML usando a `<p>` marca.

### <a name="mobile-and-desktop-differences-for-connector-cards-using-html"></a>Diferenças de dispositivos móveis e de área de trabalho para cartões de conector usando HTML

Na área de trabalho, a formatação HTML para cartões de conector tem esta aparência:

![Formatação HTML para cartões de conector no cliente desktop](../../assets/images/cards/Connector-desktop-html-combined.png)

No iOS, a formatação HTML tem esta aparência:

![Formatação HTML para cartões de conector no cliente iOS](../../assets/images/cards/connector-iphone-html-combined-80.png)

Problemas:

* As imagens em linha não são renderizadas no iOS usando Markdown ou HTML em Cartões de Conector.
* O texto pré-formatado é renderizado, mas não tem um plano de fundo cinza.

No Android, a formatação HTML tem esta aparência:

![Formatação HTML para cartões de conector no cliente Android](../../assets/images/cards/connector-android-html-combined.png)

### <a name="formatting-sample-for-html-connector-cards"></a>Exemplo de formatação para cartões de conector HTML

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

# <a name="html-formatting-hero-and-thumbnail-cards"></a>[**Formatação HTML: cartões de herói e miniatura**](#tab/simple-html)

As marcas HTML são suportadas para cartões simples, como o herói e o cartão de miniatura. Não há suporte para markdown.

| Style | Exemplo | HTML |
| --- | --- | --- |
| bold | **text** | `<strong>text</strong>` |
| italic | *text* | `<em>text</em>` |
| header (níveis 1 &ndash; 3) | **Text** | `<h3>Text</h3>` |
| strikethrough | ~~text~~ | `<strike>text</strike>` |
| lista semordenagem | <ul><li>texto</li><li>texto</li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| lista ordenada | <ol><li>texto</li><li>texto</li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| texto pré-formatado | `text` | `<pre>text</pre>` |
| blockquote | <blockquote>texto</blockquote> | `<blockquote>text</blockquote>` |
| hiperlink | [Bing](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| link de imagem |<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>| `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

### <a name="mobile-and-desktop-differences-for-simple-cards"></a>Diferenças de dispositivos móveis e de área de trabalho para cartões simples

Devido às diferenças de resolução entre a área de trabalho e a plataforma móvel, a formatação é diferente entre a área de trabalho e a versão móvel do Teams.

Na área de trabalho, a formatação HTML aparece assim:

![Formatação HTML no cliente desktop](../../assets/images/cards/card-formatting-xml-desktop-v2.png)

No iOS, a formatação HTML aparece assim:

![Formatação HTML no cliente iOS](../../assets/images/cards/card-formatting-xml-mobile-v2.png)

Problemas:

* A formatação de caracteres como negrito e itálico não é renderizada no iOS.

No Android, a formatação HTML aparece assim:

![Formatação HTML no cliente Android](../../assets/images/cards/card-formatting-xml-android-60.png)

Formatação de caracteres como negrito e exibição itálico corretamente no Android.

### <a name="formatting-sample-for-html-formatting-in-simple-cards"></a>Exemplo de formatação para formatação HTML em cartões simples

Essas capturas de tela foram criadas usando o Teams AppStudio, onde a propriedade de texto de um cartão de herói foi definida como a cadeia de caracteres a seguir. Você pode testar a formatação em seus próprios cartões modificando esse código.

`<p>bold: <strong>Bold Text</strong></p><p>italic: <em>Italic Text</em></p><p>strikethrough: <strike>Strikethrough text</strike></p><h1>Header 1</h1><h2>Header 2</h2><h3>Header 3</h3><p>bullet list: <ul><li>text</li><li>text</li></ul></p><p>ordered list: <ol><li>text</li><li>text</li></ol></p><pre>preformatted text</pre><blockquote>blockquote text</blockquote></p><p>hyperlink: <a href=\"https://www.bing.com/\">Bing</a></p><p>embedded image: <img src=\"https://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img></p>`

---
