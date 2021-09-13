---
title: Formatação de texto em cartões
description: Descreve a formatação de texto do cartão em Microsoft Teams
keywords: formato de cartões de bots do teams
ms.localizationpriority: medium
ms.topic: reference
ms.date: 06/25/2021
ms.openlocfilehash: abbdc0d1fa77744ae061e5430c4450d0e7cf83c7
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59155170"
---
# <a name="format-cards-in-microsoft-teams"></a>Formatar cartões no Microsoft Teams

A seguir estão as duas maneiras de adicionar formatação de texto rich aos cartões:
* [Markdown](#format-cards-with-markdown)
* [HTML](#format-cards-with-html)

Os cartões suportam formatação somente na propriedade text, não nas propriedades title ou subtitle. A formatação pode ser especificada usando um subconjunto de formatação XML ou HTML ou Markdown, dependendo do tipo de cartão. Para o desenvolvimento atual e futuro de Cartões Adaptáveis, a formatação markdown é recomendada.

O suporte à formatação difere entre tipos de cartão. A renderização do cartão pode diferir ligeiramente entre a área de trabalho e os clientes de Microsoft Teams móveis, bem como Teams no navegador da área de trabalho.

Você pode incluir uma imagem em linha com qualquer Teams cartão. As imagens podem ser formatadas como , ou arquivos e não devem exceder `.png` `.jpg` `.gif` 1024 ×1024 px ou 1 MB. Gif animado não é suportado. Para obter mais informações, consulte [tipos de cartões](./cards-reference.md#inline-card-images).

Você pode formatar cartões adaptáveis e Office 365 conector com Markdown que incluem determinados estilos com suporte.

## <a name="format-cards-with-markdown"></a>Formatar cartões com Markdown

Os seguintes tipos de cartão suportam a formatação markdown Teams:

* Cartões Adaptáveis: a marcação é suportada no campo Cartão `Textblock` Adaptável, bem como e `Fact.Title` `Fact.Value` . HTML não é suportado em Cartões Adaptáveis.
* Cartões do conector O365: Markdown e HTML limitado são suportados em cartões conectores O365 nos campos de texto.

Você pode usar linhas novas para Cartões Adaptáveis usando ou sequências de escape `\r` para linhas novas em `\n` listas. A formatação é diferente entre a área de trabalho e as versões móveis Teams para Cartões Adaptáveis. As menções baseadas em cartão são suportadas em clientes web, desktop e móveis. Você pode usar a propriedade de mascaramento de informações para mascarar informações específicas, como senha ou informações confidenciais de usuários dentro do elemento de entrada Cartão `Input.Text` Adaptável. Você pode expandir a largura de um Cartão Adaptável usando o `width` objeto. Você pode habilitar o suporte typeahead em Cartões Adaptáveis e filtrar o conjunto de opções de entrada à medida que o usuário digita a entrada. Você pode usar a `msteams` propriedade para adicionar a capacidade de exibir imagens no exibição de estágio seletivamente.

A formatação é diferente entre a área de trabalho e as versões móveis do Teams para Cartões Adaptáveis e cartões de conector. Nesta seção, você pode passar pelo exemplo de formato Markdown para Cartões Adaptáveis e cartões de conector.

# <a name="markdown-format-for-adaptive-cards"></a>[Formato de marcação para Cartões Adaptáveis](#tab/adaptive-md)

 A tabela a seguir fornece os estilos com suporte `Textblock` para , `Fact.Title` e `Fact.Value` :

| Estilo | Exemplo | Markdown |
| --- | --- | --- |
| Negrito | **Negrito** | ```**Bold**``` |
| Itálico | _Itálico_ | ```_Italic_``` |
| Lista não ordenada | <ul><li>texto</li><li>texto</li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| Lista ordenada | <ol><li>texto</li><li>texto</li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| Hiperlinks |[Bing](https://www.bing.com/)| ```[Title](url)``` |

As seguintes marcas Markdown não são suportadas:

* Cabeçalhos
* Tabelas
* Imagens
* Texto pré-formatado
* Blockquotes

### <a name="newlines-for-adaptive-cards"></a>Linhas novas para cartões adaptáveis

Você pode usar as `\r` sequências de `\n` escape ou para linhas novas em listas. O uso em listas faz com que o `\n\n` próximo elemento da lista seja recuado. Se você precisar de linhas novas em outro lugar no TextBlock, use `\n\n` .

### <a name="mobile-and-desktop-differences-for-adaptive-cards"></a>Diferenças de dispositivos móveis e de área de trabalho para Cartões Adaptáveis

Na área de trabalho, a formatação adaptável de Marcação de Cartão aparece como mostrado na imagem a seguir, tanto em navegadores da Web quanto no aplicativo cliente Teams cliente:

![Formatação de Marcação de Cartão Adaptável no cliente da área de trabalho](../../assets/images/cards/Adaptive-markdown-desktop-client.png)

No iOS, a formatação adaptável de Marcação de Cartão aparece conforme mostrado na imagem a seguir:

![Formatação de Marcação de Cartão Adaptável no iOS](../../assets/images/cards/Adaptive-markdown-iOS-75.png)

No Android, a formatação adaptável de Marcação de Cartão aparece conforme mostrado na imagem a seguir:

![Formatação de Marcação de Cartão Adaptável no Android](../../assets/images/cards/Adaptive-markdown-Android.png)

Para obter mais informações, consulte [recursos de texto em Cartões Adaptáveis](/adaptive-cards/create/textfeatures).

> [!NOTE]
> Os recursos de data e localização mencionados nesta seção não são suportados Teams.

### <a name="adaptive-cards-format-sample"></a>Exemplo de formato de cartões adaptáveis

O código a seguir mostra um exemplo de formatação de Cartões Adaptáveis:

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

### <a name="mention-support-within-adaptive-cards-v12"></a>Mencionar suporte em Cartões Adaptáveis v1.2

Você pode adicionar @mentions em um corpo de Cartão Adaptável para bots e respostas de extensão de mensagens. Para adicionar @mentions cartões, siga a mesma lógica de notificação e renderização das menções baseadas em mensagens em conversas de chat de canal [e grupo.](../../bots/how-to/conversations/channel-and-group-conversations.md#work-with-mentions)

Bots e extensões de mensagens podem incluir menções no conteúdo do cartão nos [elementos TextBlock](https://adaptivecards.io/explorer/TextBlock.html) e [FactSet.](https://adaptivecards.io/explorer/FactSet.html)

> [!NOTE]
> * [Atualmente,](https://adaptivecards.io/explorer/Media.html) os elementos de mídia não têm suporte em Cartões Adaptáveis v1.2 na plataforma Teams adaptável.
> * As menções de canal e equipe não são suportadas em mensagens bot.

Para incluir uma menção em um Cartão Adaptável, seu aplicativo precisa incluir os seguintes elementos:

* `<at>username</at>` nos elementos do Cartão Adaptável com suporte.
* O objeto dentro de uma propriedade no conteúdo do cartão inclui Teams ID do usuário que está `mention` `msteams` sendo mencionado.
* O `userId` é exclusivo da ID do bot e de um usuário específico. Ele pode ser usado para @mention um usuário específico. O `userId` pode ser recuperado usando uma das opções mencionadas em obter a [ID do usuário](/microsoftteams/platform/bots/how-to/conversations/send-proactive-messages?tabs=dotnet#get-the-user-id-team-id-or-channel-id).

#### <a name="sample-adaptive-card-with-a-mention"></a>Cartão Adaptável de Exemplo com uma menção

O código a seguir mostra um exemplo de Cartão Adaptável com uma menção:

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

### <a name="information-masking-in-adaptive-cards"></a>Mascaramento de informações em Cartões Adaptáveis

Use a propriedade mascarar informações para mascarar informações específicas, como senha ou informações confidenciais de usuários dentro do elemento de entrada Cartão [`Input.Text`](https://adaptivecards.io/explorer/Input.Text.html) Adaptável.

> [!NOTE]
> O recurso só dá suporte ao mascaramento de informações do lado do cliente. O texto de entrada mascarada é enviado como texto claro para o endereço de ponto de extremidade HTTPS especificado durante a configuração [do bot.](../../build-your-first-app/build-bot.md#4-register-your-bot-endpoint)

Para mascarar informações em Cartões Adaptáveis, adicione a propriedade para `isMasked` **digitar** e de definir seu valor `Input.Text` como **true**.

#### <a name="sample-adaptive-card-with-masking-property"></a>Cartão Adaptável de Exemplo com a propriedade mascaramento

O código a seguir mostra um exemplo de Cartão Adaptável com a propriedade mascaramento:

```json
{
    "type": "Input.Text",
    "id": "secretThing",
    "style": "password",
},
```

A imagem a seguir é um exemplo de informações de mascaramento em Cartões Adaptáveis:

![Imagem de informações de mascaramento](../../assets/images/cards/masking-information-view.png)

### <a name="full-width-adaptive-card"></a>Cartão Adaptável de largura total

Você pode usar a `msteams` propriedade para expandir a largura de um Cartão Adaptável e usar espaço adicional de tela. A próxima seção fornece informações sobre como usar a propriedade.

#### <a name="construct-full-width-cards"></a>Construir cartões de largura total

Para fazer um Cartão Adaptável de largura total, o objeto na propriedade no conteúdo do cartão deve `width` `msteams` ser definido como `Full` .

#### <a name="sample-adaptive-card-with-full-width"></a>Cartão Adaptável de Exemplo com largura total

Para fazer um Cartão Adaptável de largura total, seu aplicativo deve incluir os elementos do exemplo de código a seguir:

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

A imagem a seguir mostra um Cartão Adaptável de largura total:

![Exibição cartão adaptável de largura total](../../assets/images/cards/full-width-adaptive-card.png)

A imagem a seguir mostra o modo de exibição padrão do Cartão Adaptável quando você não definiu a `width` propriedade como **Full**:

![Exibição cartão adaptável de largura pequena](../../assets/images/cards/small-width-adaptive-card.png)

### <a name="typeahead-support"></a>Suporte a Typeahead

Dentro do elemento de esquema, pedir que os usuários filtrem e selecionem um número considerável de opções podem reduzir significativamente a conclusão [`Input.Choiceset`](https://adaptivecards.io/explorer/Input.ChoiceSet.html) da tarefa. O suporte typeahead em Cartões Adaptáveis pode simplificar a seleção de entrada restringindo ou filtrando o conjunto de opções de entrada à medida que o usuário digita a entrada.

Para habilitar typeahead no `Input.Choiceset` , definir como e garantir que está definido como `style` `filtered` `isMultiSelect` `false` .

#### <a name="sample-adaptive-card-with-typeahead-support"></a>Cartão Adaptável de Exemplo com suporte a typeahead

O código a seguir mostra um exemplo de Cartão Adaptável com suporte a typeahead:

``` json
{
   "type": "Input.ChoiceSet",
   "label": "Select a user",
   "isMultiSelect": false,
   "choices":  [
      { "title": "User 1", "value": "User1" },
      { "title": "User 2", "value": "User2" }
    ],
   "style": "filtered"
}
```

### <a name="stage-view-for-images-in-adaptive-cards"></a>Exibição de estágio para imagens em Cartões Adaptáveis

Em um Cartão Adaptável, você pode usar a propriedade para adicionar a capacidade de exibir imagens na exibição `msteams` de estágio seletivamente. Quando os usuários pairam sobre as imagens, eles podem ver um ícone de expansão, para o qual o `allowExpand` atributo é definido como `true` . Para obter informações sobre como usar a propriedade, consulte o exemplo a seguir:

``` json
{
    "type": "AdaptiveCard",
     "body": [
          {
            "type": "Image",
            "url": "https://picsum.photos/200/200?image=110",
            "msTeams": {
              "allowExpand": true
            }
          },
     ],
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.2"
}
```

Quando os usuários passar o mouse sobre a imagem, um ícone de expansão aparece no canto superior direito, conforme mostrado na imagem a seguir:

![Cartão Adaptável com imagem expansível](../../assets/images/cards/adaptivecard-hover-expand-icon.png)

A imagem aparece no exibição de estágio quando o usuário seleciona o ícone de expansão, conforme mostrado na imagem a seguir:

![Imagem expandida para exibição de estágio](../../assets/images/cards/adaptivecard-expand-image.png)

Na exibição de estágio, os usuários podem ampliar e diminuir o zoom da imagem. Você pode selecionar as imagens em seu Cartão Adaptável que devem ter esse recurso.

> [!NOTE]
> * A funcionalidade de zoom e zoom só se aplica aos elementos de imagem que são tipo de imagem em um Cartão Adaptável.
> * Para Teams aplicativos móveis, a funcionalidade de exibição de estágio para imagens em Cartões Adaptáveis está disponível por padrão. Os usuários podem exibir imagens do Cartão Adaptável na exibição de estágio simplesmente tocando na imagem, independentemente de o `allowExpand` atributo estar presente ou não.

# <a name="markdown-format-for-o365-connector-cards"></a>[Formato de marcação para cartões conectores O365](#tab/connector-md)

Os cartões conectores suportam a formatação limitada markdown e HTML.

| Estilo | Exemplo | Markdown |
| --- | --- | --- |
| Negrito | **text** | `**text**` |
| Itálico | *text* | `*text*` |
| Header (níveis 1 &ndash; 3) | **Texto** | `### Text`|
| Tachado | ~~text~~ | `~~text~~` |
| Lista não ordenada | <ul><li>texto</li><li>texto</li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| Lista ordenada | <ol><li>texto</li><li>texto</li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| Texto pré-formatado | `text` | ``preformatted text`` |
| Blockquote | >texto blockquote | `>blockquote text` |
| Hiperlink | [Bing](https://www.bing.com/) | `[Bing](https://www.bing.com/)` |
| Link de imagem |![Duck on a rock](https://aka.ms/Fo983c) | `![Duck](https://aka.ms/Fo983c)` |

Em cartões de conector, as linhas novas são renderizadas `\n\n` para , mas não para ou `\n` `\r` .

### <a name="mobile-and-desktop-differences-for-connector-cards"></a>Diferenças de dispositivos móveis e de área de trabalho para cartões de conector

Na área de trabalho, a formatação markdown para cartões de conector aparece como mostrado na imagem a seguir:

![Formatação de marcação para cartões conectores no cliente desktop](../../assets/images/cards/connector-desktop-markdown-combined.png)

No iOS, a formatação markdown para cartões de conector aparece conforme mostrado na imagem a seguir:

![Formatação de marcação para cartões conectores no cliente iOS](../../assets/images/cards/connector-iphone-markdown-combined-80.png)

Os cartões conectores que usam Markdown para iOS incluem os seguintes problemas:

* O cliente iOS para Teams não renderiza imagens em linha Markdown ou HTML em cartões de conector.
* As blockquotes são renderizadas como recuadas, mas sem um plano de fundo cinza.

No Android, a formatação markdown para cartões de conector aparece como mostrado na imagem a seguir:

![Formatação de marcação para cartões conectores no cliente Android](../../assets/images/cards/connector-android-markdown-combined.png)

### <a name="format-example-for-markdown-connector-cards"></a>Exemplo de formato para cartões de conector Markdown

O código a seguir mostra um exemplo de formatação para cartões de conector Markdown:

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

## <a name="format-cards-with-html"></a>Formatar cartões com HTML

Os seguintes tipos de cartão suportam formatação HTML Teams:

* Cartões do conector O365: Marcação limitada e formatação HTML é suportada em cartões Office 365 Connector.
* Cartões de herói e miniatura: as marcas HTML são suportadas para cartões simples, como cartões de herói e miniatura.

A formatação é diferente entre a área de trabalho e as versões móveis do Teams para cartões conectores O365 e cartões simples. Nesta seção, você pode passar pelo exemplo de formato HTML para cartões de conector e cartões simples.

# <a name="html-format-for-o365-connector-cards"></a>[Formato HTML para cartões conectores O365](#tab/connector-html)

Os cartões conectores suportam a formatação limitada markdown e HTML.

| Estilo | Exemplo | HTML |
| --- | --- | --- |
| Negrito | **text** | `<strong>text</strong>` |
| Itálico | *text* | `<em>text</em>` |
| Header (níveis 1 &ndash; 3) | **Texto** | `<h3>Text</h3>` |
| Tachado | ~~text~~ | `<strike>text</strike>` |
| Lista não ordenada | <ul><li>texto</li><li>texto</li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| Lista ordenada | <ol><li>texto</li><li>texto</li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| Texto pré-formatado | `text` | `<pre>text</pre>` |
| Blockquote | <blockquote>texto</blockquote> | `<blockquote>text</blockquote>` |
| Hiperlink | [Bing](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| Link de imagem | <img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img> | `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

Em cartões de conector, as linhas novas são renderizadas em HTML usando a `<p>` marca.

### <a name="mobile-and-desktop-differences-for-connector-cards"></a>Diferenças de dispositivos móveis e de área de trabalho para cartões de conector

Na área de trabalho, a formatação HTML para cartões de conector aparece como mostrado na imagem a seguir:

![Formatação HTML para cartões conectores no cliente da área de trabalho](../../assets/images/cards/Connector-desktop-html-combined.png)

No iOS, a formatação HTML aparece conforme mostrado na imagem a seguir:

![Formatação HTML para cartões de conector no cliente iOS](../../assets/images/cards/connector-iphone-html-combined-80.png)

Os cartões conectores que usam HTML para iOS incluem os seguintes problemas:

* Imagens em linha não são renderizadas no iOS usando Markdown ou HTML em cartões de conector.
* O texto pré-formatado é renderizado, mas não tem um plano de fundo cinza.

No Android, a formatação HTML aparece conforme mostrado na imagem a seguir:

![Formatação HTML para cartões de conector no cliente Android](../../assets/images/cards/connector-android-html-combined.png)

### <a name="format-sample-for-html-connector-cards"></a>Exemplo de formato para cartões de conector HTML

O código a seguir mostra um exemplo de formatação para cartões de conector HTML:

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

# <a name="html-format-for-hero-and-thumbnail-cards"></a>[Formato HTML para cartões de herói e miniatura](#tab/simple-html)

As marcas HTML são suportadas para cartões simples, como cartões de herói e miniatura. Não há suporte para markdown.

| Estilo | Exemplo | HTML |
| --- | --- | --- |
| Negrito | **text** | `<strong>text</strong>` |
| Itálico | *text* | `<em>text</em>` |
| Header (níveis 1 &ndash; 3) | **Texto** | `<h3>Text</h3>` |
| Tachado | ~~text~~ | `<strike>text</strike>` |
| Lista não ordenada | <ul><li>texto</li><li>texto</li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| Lista ordenada | <ol><li>texto</li><li>texto</li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| Texto pré-formatado | `text` | `<pre>text</pre>` |
| Blockquote | <blockquote>texto</blockquote> | `<blockquote>text</blockquote>` |
| Hiperlink | [Bing](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| Link de imagem |<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>| `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

### <a name="mobile-and-desktop-differences-for-simple-cards"></a>Diferenças de dispositivos móveis e de área de trabalho para cartões simples

Como há diferenças de resolução entre a área de trabalho e a plataforma móvel, a formatação é diferente entre a área de trabalho e a versão móvel do Teams.

Na área de trabalho, a formatação HTML aparece conforme mostrado na imagem a seguir:

![Formatação HTML no cliente da área de trabalho](../../assets/images/cards/card-formatting-xml-desktop-v2.png)

No iOS, a formatação HTML aparece conforme mostrado na imagem a seguir:

![Formatação HTML no cliente iOS](../../assets/images/cards/card-formatting-xml-mobile-v2.png)

A formatação de caracteres, como negrito e itálico, não é renderizada no iOS.

No Android, a formatação HTML aparece conforme mostrado na imagem a seguir:

![Formatação HTML no cliente Android](../../assets/images/cards/card-formatting-xml-android-60.png)

Formatação de caracteres, como negrito e exibição itálico corretamente no Android.

### <a name="format-example-for-simple-cards"></a>Exemplo de formato para cartões simples

As imagens na seção anterior foram criadas usando Teams **App Studio**, onde a propriedade de texto de um cartão de herói é definida como a seguinte cadeia de caracteres:

`<p>bold: <strong>Bold Text</strong></p><p>italic: <em>Italic Text</em></p><p>strikethrough: <strike>Strikethrough text</strike></p><h1>Header 1</h1><h2>Header 2</h2><h3>Header 3</h3><p>bullet list: <ul><li>text</li><li>text</li></ul></p><p>ordered list: <ol><li>text</li><li>text</li></ol></p><pre>preformatted text</pre><blockquote>blockquote text</blockquote></p><p>hyperlink: <a href=\"https://www.bing.com/\">Bing</a></p><p>embedded image: <img src=\"https://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img></p>`

Você pode testar a formatação em seus próprios cartões modificando esse código.

---

## <a name="see-also"></a>Confira também

* [Ações do cartão](./cards-actions.md)
* [Módulos de tarefas](~/task-modules-and-cards/cards/cards-format.md)
