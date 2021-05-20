---
title: Formatação de texto em cartões
description: Descreve a formatação de texto de cartão em Microsoft Teams
keywords: equipes bots formato de cartões
localization_priority: Normal
ms.topic: reference
ms.date: 03/29/2018
ms.openlocfilehash: 848656097f2c865705cc0d91dece93049d8c6790
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566576"
---
# <a name="format-cards-in-teams"></a>Cartões de formato em Teams

Você pode adicionar formatação de texto rica em seus cartões usando markdown ou HTML, dependendo do tipo de cartão.

Os cartões suportam a formatação apenas na propriedade de texto, não nas propriedades do título ou da legenda. A formatação pode ser especificada usando um subconjunto de formatação XML (HTML) ou Markdown, dependendo do tipo de cartão. Para o desenvolvimento atual e futuro, é recomendado cartões adaptativos usando a formatação markdown.

O suporte de formatação difere entre diferentes tipos de cartão, e a renderização do cartão pode diferir ligeiramente entre o desktop e o celular Teams clientes, bem como Teams no navegador de desktop.

Você pode incluir uma imagem inline com qualquer cartão Teams. As imagens são formatadas  `.png` `.jpg` como, ou `.gif` arquivos, e não devem exceder 1024 ×1024 px ou 1 MB. Gif animado não é suportado oficialmente. Para obter mais informações, consulte [referência de Cartões](./cards-reference.md#inline-card-images).

## <a name="formatting-cards-with-markdown"></a>Cartões de formatação com Markdown

Existem dois tipos de cartões que suportam markdown em Teams:

> [!div class="checklist"]
> * **Cartões adaptativos**: A marcação é suportada no campo de cartas `Textblock` adaptativas, bem como `Fact.Title` . `Fact.Value` HTML não é suportado em cartões adaptativos.
> * **Placas conectoras O365**: Markdown e HTML limitado são suportados em Office 365 placas Connector nos campos de texto.

# <a name="markdown-formatting-adaptive-cards"></a>[**Formatação de markdown: Cartões adaptativos**](#tab/adaptive-md)

 Os estilos suportados para `Textblock` , `Fact.Title` e `Fact.Value` são:

| Style | Exemplo | Markdown |
| --- | --- | --- |
| bold | **Negrito** | ```**Bold**``` |
| italic | _Itálico_ | ```_Italic_``` |
| lista não rdenada | <ul><li>texto</li><li>texto</li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| lista ordenada | <ol><li>texto</li><li>texto</li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| Hiperlinks |[Bing](https://www.bing.com/)| ```[Title](url)``` |

As seguintes tags Markdown não são suportadas:

* Cabeçalhos
* Tabelas
* Imagens
* Texto pré-formado
* Cotas de bloqueio

> [!IMPORTANT]
> As placas adaptativas não suportam formatação HTML.

### <a name="newlines-for-adaptive-cards"></a>Linhas novas para cartões adaptativos

Em listas você pode usar as `\r` `\n` sequências ou escape para linhas novas. O uso `\n\n` em uma lista fará com que o próximo elemento da lista seja recuado. Se você precisar de novas linhas em outros lugares no bloco de texto, use `\n\n` .

### <a name="mobile-and-desktop-differences-for-adaptive-cards"></a>Diferenças móveis e desktop para cartões adaptativos

A formatação é ligeiramente diferente entre a área de trabalho e as versões móveis de Teams.

No desktop, a formatação de marcação de cartão adaptável aparece assim tanto em navegadores da Web quanto no aplicativo Teams cliente:

![Marcação de marcação de cartão adaptativo no cliente de desktop](../../assets/images/cards/Adaptive-markdown-desktop-client.png)

No iOS, a formatação de marcação de cartão adaptável aparece assim:

![Marcação de cartão adaptativo no iOS](../../assets/images/cards/Adaptive-markdown-iOS-75.png)

No Android, a formatação de marcação de cartão adaptativo aparece assim:

![Marcação de cartão adaptativo no Android](../../assets/images/cards/Adaptive-markdown-Android.png)

### <a name="more-information-on-adaptive-cards"></a>Mais informações sobre cartões adaptativos

[Recursos de texto em cartões adaptativos](/adaptive-cards/create/textfeatures) As características de data e localização mencionadas neste tópico não são suportadas em Teams.

### <a name="formatting-sample-for-adaptive-cards"></a>Amostra de formatação para cartões adaptativos

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

### <a name="mention-support-within-adaptive-cards-v12"></a>Mencionar suporte em cartões adaptativos v1.2

As menções baseadas em cartões são suportadas em clientes web, desktop e mobile. Você pode adicionar @ menções dentro de um corpo de cartão adaptativo para bots e respostas de extensão de mensagens. Para adicionar @ menções em cartões, siga a mesma lógica de notificação e renderização que a das [menções baseadas em mensagens em conversas de bate-papo de canal e grupo](../../bots/how-to/conversations/channel-and-group-conversations.md#work-with-mentions).

Bots e extensões de mensagens podem incluir menções dentro do conteúdo do cartão nos elementos [TextBlock](https://adaptivecards.io/explorer/TextBlock.html) e [FactSet.](https://adaptivecards.io/explorer/FactSet.html)

> [!NOTE]
> * [Atualmente, os elementos](https://adaptivecards.io/explorer/Media.html) de mídia não são suportados em cartões adaptáveis v1.2 na plataforma Teams.
> * As menções da Equipe de & do canal não são suportadas em mensagens de bot.

#### <a name="constructing-mentions"></a>Construindo menções

Para incluir uma menção em um Cartão Adaptativo, seu aplicativo precisa incluir os seguintes elementos:

* `<at>username</at>` nos elementos de cartão adaptável suportados.
* O `mention` objeto dentro de uma propriedade no conteúdo do `msteams` cartão, que inclui a Teams identificação do usuário do usuário sendo mencionado.
* O `userId` é exclusivo do seu ID do bot e de um determinado usuário. Ele pode ser usado para @mention um determinado usuário. O `userId` pode ser recuperado usando uma das opções mencionadas na [ção do ID do usuário](/microsoftteams/platform/bots/how-to/conversations/send-proactive-messages?tabs=dotnet#get-the-user-id-team-id-or-channel-id).

#### <a name="sample-adaptive-card-with-a-mention"></a>Cartão adaptável da amostra com uma menção

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

### <a name="information-masking-in-adaptive-cards"></a>Mascaramento de informações em cartões adaptativos
Use a propriedade de mascaramento de informações para mascarar informações específicas, como senha ou informações confidenciais dos usuários dentro do elemento de entrada do cartão [`Input.Text`](https://adaptivecards.io/explorer/Input.Text.html) Adaptive. 

> [!NOTE]
> O recurso suporta apenas o mascaramento de informações do lado do cliente, o texto de entrada mascarado é enviado como texto claro para o endereço final https especificado durante a [configuração do bot](../../build-your-first-app/build-bot.md). 

> [!NOTE]
> A propriedade de mascaramento de informações está disponível apenas na pré-visualização do desenvolvedor.

Para mascarar informações em cartões adaptativos, adicione a `isMasked` propriedade ao **tipo** `Input.Text` e defina seu valor como *verdadeiro*.

#### <a name="sample-adaptive-card-with-masking-property"></a>Cartão adaptável de amostra com propriedade de mascaramento

```json
{
    "type": "Input.Text",
    "id": "secretThing",
    "style": "password",
    "isMasked": true
  },
```

A imagem a seguir é um exemplo de mascarar informações em cartões adaptativos:

![Mascarando imagens de informações](../../assets/images/cards/masking-information-view.png)

### <a name="full-width-adaptive-card"></a>Placa adaptativa de largura completa
Você pode usar a `msteams` propriedade para expandir a largura de uma placa Adaptive e fazer uso de espaço adicional de lona. Para obter informações sobre como usar o imóvel, consulte o seguinte exemplo:

#### <a name="constructing-full-width-cards"></a>Construindo cartões de largura total
Para fazer uma placa adaptativa de largura total, o `width` objeto em propriedade no conteúdo do cartão deve ser definido para `msteams` `Full` .
Além disso, seu aplicativo deve incluir os seguintes elementos:

#### <a name="sample-adaptive-card-with-full-width"></a>Cartão adaptativo de amostra com largura total

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

Uma placa adaptativa de largura total aparece da seguinte forma: ![ Visão de cartão adaptativo de largura total](../../assets/images/cards/full-width-adaptive-card.png)

Se você não tiver definido a `width` propriedade como *Full,* então a exibição padrão da Placa Adaptativa é a seguinte: ![ Exibição de cartão adaptativo de pequena largura](../../assets/images/cards/small-width-adaptive-card.png)

### <a name="typeahead-support"></a>Suporte tipoahead

Dentro do [`Input.Choiceset`](https://adaptivecards.io/explorer/Input.ChoiceSet.html) elemento esquema, pedir aos usuários que filtram e selecionem através de um número considerável de opções pode retardar significativamente a conclusão da tarefa. O suporte tipo-cabeça dentro de cartões Adaptive pode simplificar a seleção de entrada, estreitando ou filtrando o conjunto de opções de entrada à medida que um usuário está digitando a entrada. 

#### <a name="enable-typeahead-in-adaptive-cards"></a>Habilitar typeahead em cartões adaptativos

Para habilitar a cabeça de digitar dentro do `Input.Choiceset` conjunto para e garantir que seja definido para `style` `filtered` `isMultiSelect` `false` . 

#### <a name="sample-adaptive-card-with-typeahead-support"></a>Cartão adaptativo de amostra com suporte de cabeça de digitar

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

### <a name="stage-view-for-images-in-adaptive-cards"></a>Exibição de palco para imagens em Cartões Adaptativos

> [!NOTE]
> Este recurso está atualmente disponível apenas na pré-visualização do desenvolvedor.
 
Em uma placa Adaptativa, você pode usar a `msteams` propriedade para adicionar a capacidade de exibir imagens na visualização do palco seletivamente. Quando os usuários pairam sobre as imagens, eles veriam um ícone de expansão, para o qual o `allowExpand` atributo é definido `true` . Para obter informações sobre como usar o imóvel, consulte o seguinte exemplo:

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

Quando os usuários pairam sobre a imagem, um ícone de expansão aparece no canto superior direito da imagem: ![ Cartão adaptativo com imagem expansível](../../assets/images/cards/adaptivecard-hover-expand-icon.png)

A imagem aparece na visualização do palco quando o usuário seleciona o botão expandir: ![ Imagem expandida para exibição de palco](../../assets/images/cards/adaptivecard-expand-image.png)

Na visualização do palco, os usuários podem ampliar e diminuir o zoom da imagem. Você pode selecionar quais imagens em sua placa Adaptive precisam ter esse recurso.

> [!NOTE]
> O recurso de zoom e zoom out se aplica apenas aos elementos de imagem (tipo de imagem) em uma placa Adaptive.

> [!NOTE]
> Para Teams aplicativos móveis, a funcionalidade de visualização de palco para imagens em Cartões Adaptativos está disponível por padrão e os usuários poderão visualizar imagens de placas adaptativas na visualização do palco simplesmente tocando na imagem, independentemente de o `allowExpand` atributo estar presente ou não.

# <a name="markdown-formatting-o365-connector-cards"></a>[**Formatação de markdown: Placas conectoras O365**](#tab/connector-md)

As placas conectoras suportam formatação limitada de Markdown e HTML. O suporte html é descrito na última seção.

| Style | Exemplo | Markdown |
| --- | --- | --- |
| bold | **text** | `**text**` |
| italic | *text* | `*text*` |
| cabeçalho (níveis &ndash; 13) | **Texto** | `### Text`|
| strikethrough | ~~text~~ | `~~text~~` |
| lista não rdenada | <ul><li>texto</li><li>texto</li></ul> | ```- Item 1\r- Item 2\r- Item 3``` |
| lista ordenada | <ol><li>texto</li><li>texto</li></ol> | ```1. Green\r2. Orange\r3. Blue``` |
| texto pré-formado | `text` | ``preformatted text`` |
| blockquote | >texto de cota de bloqueio | `>blockquote text` |
| hiperlink | [Bing](https://www.bing.com/) | `[Bing](https://www.bing.com/)` |
| link de imagem |![Pato em uma pedra](https://aka.ms/Fo983c) | `![Duck](https://aka.ms/Fo983c)` |

Em cartões conectores, novas linhas são renderizadas para `\n\n` , mas não para ou `\n` `\r` .

### <a name="mobile-and-desktop-differences-for-connector-cards-using-markdown"></a>Diferenças móveis e desktop para cartões conectores usando Markdown

No desktop, a formatação do Markdown para placas conectoras é assim:

![Formatação de marcação para cartões conectores no cliente Desktop](../../assets/images/cards/connector-desktop-markdown-combined.png)

No iOS, a formatação do Markdown para placas conectoras é assim:

![Formatação de marcação para cartões conectores no cliente iOS](../../assets/images/cards/connector-iphone-markdown-combined-80.png)

Questões:

* O cliente iOS para Teams não renderiza imagens em linha de Markdown ou HTML em Placas Conectoras.
* As cotas de bloqueio são renderizadas como recuadas, mas sem fundo cinza.

No Android, a formatação do Markdown para placas conectoras é assim:

![Formatação de markdown para cartões conectores no cliente Android](../../assets/images/cards/connector-android-markdown-combined.png)

### <a name="formatting-example-for-markdown-connector-cards"></a>Formatação exemplo para cartões conectores markdown

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

## <a name="formatting-cards-with-html"></a>Cartões de formatação com HTML

# <a name="html-formatting-o365-connector-cards"></a>[**Formatação HTML: Placas conectoras O365**](#tab/connector-html)

As placas conectoras suportam formatação limitada de Markdown e HTML. Markdown é descrito na próxima seção.

| Style | Exemplo | HTML |
| --- | --- | --- |
| bold | **text** | `<strong>text</strong>` |
| italic | *text* | `<em>text</em>` |
| cabeçalho (níveis &ndash; 13) | **Texto** | `<h3>Text</h3>` |
| strikethrough | ~~text~~ | `<strike>text</strike>` |
| lista não rdenada | <ul><li>texto</li><li>texto</li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| lista ordenada | <ol><li>texto</li><li>texto</li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| texto pré-formado | `text` | `<pre>text</pre>` |
| blockquote | <blockquote>texto</blockquote> | `<blockquote>text</blockquote>` |
| hiperlink | [Bing](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| link de imagem | <img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img> | `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

Nas placas de conector, as linhas novas são renderizadas em HTML usando a `<p>` tag.

### <a name="mobile-and-desktop-differences-for-connector-cards-using-html"></a>Diferenças móveis e desktop para placas conectoras usando HTML

Na área de trabalho, a formatação HTML para placas conectoras é assim:

![Formatação HTML para cartões conectores no cliente Desktop](../../assets/images/cards/Connector-desktop-html-combined.png)

No iOS, a formatação HTML é assim:

![Formatação HTML para cartões conectores no cliente iOS](../../assets/images/cards/connector-iphone-html-combined-80.png)

Questões:

* As imagens inline não são renderizadas no iOS usando markdown ou HTML em placas conectoras.
* O texto pré-formado é renderizado, mas não tem um fundo cinza.

No Android, a formatação HTML se parece com isso:

![Formatação HTML para cartões conectores no cliente Android](../../assets/images/cards/connector-android-html-combined.png)

### <a name="formatting-sample-for-html-connector-cards"></a>Amostra de formatação para placas de conector HTML

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

As tags HTML são suportadas para cartões simples, como o hero e a placa de miniatura. Markdown não é apoiado.

| Style | Exemplo | HTML |
| --- | --- | --- |
| bold | **text** | `<strong>text</strong>` |
| italic | *text* | `<em>text</em>` |
| cabeçalho (níveis &ndash; 13) | **Texto** | `<h3>Text</h3>` |
| strikethrough | ~~text~~ | `<strike>text</strike>` |
| lista não rdenada | <ul><li>texto</li><li>texto</li></ul> | `<ul><li>text</li><li>text</li></ul>` |
| lista ordenada | <ol><li>texto</li><li>texto</li></ol> | `<ol><li>text</li><li>text</li></ol>` |
| texto pré-formado | `text` | `<pre>text</pre>` |
| blockquote | <blockquote>texto</blockquote> | `<blockquote>text</blockquote>` |
| hiperlink | [Bing](https://www.bing.com/) | `<a href="https://www.bing.com/">Bing</a>` |
| link de imagem |<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>| `<img src="https://aka.ms/Fo983c" alt="Duck on a rock"></img>` |

### <a name="mobile-and-desktop-differences-for-simple-cards"></a>Diferenças móveis e desktop para cartões simples

Devido às diferenças de resolução entre a plataforma desktop e mobile, a formatação é diferente entre o desktop e a versão móvel de Teams.

No desktop, a formatação HTML aparece assim:

![Formatação html no cliente Desktop](../../assets/images/cards/card-formatting-xml-desktop-v2.png)

No iOS, a formatação HTML aparece assim:

![Formatação HTML no cliente iOS](../../assets/images/cards/card-formatting-xml-mobile-v2.png)

Questões:

* A formatação de caracteres como negrito e itálico não são renderizadas no iOS.

No Android, a formatação HTML aparece assim:

![Formatação HTML no cliente Android](../../assets/images/cards/card-formatting-xml-android-60.png)

Formatação de caracteres como exibição em negrito e itálico corretamente no Android.

### <a name="formatting-sample-for-html-formatting-in-simple-cards"></a>Amostra de formatação para formatação HTML em cartões simples

Essas capturas de tela foram criadas usando Teams AppStudio, onde a propriedade de texto de um cartão herói foi definida para a sequência seguinte. Você pode testar a formatação em seus próprios cartões modificando este código.

`<p>bold: <strong>Bold Text</strong></p><p>italic: <em>Italic Text</em></p><p>strikethrough: <strike>Strikethrough text</strike></p><h1>Header 1</h1><h2>Header 2</h2><h3>Header 3</h3><p>bullet list: <ul><li>text</li><li>text</li></ul></p><p>ordered list: <ol><li>text</li><li>text</li></ol></p><pre>preformatted text</pre><blockquote>blockquote text</blockquote></p><p>hyperlink: <a href=\"https://www.bing.com/\">Bing</a></p><p>embedded image: <img src=\"https://aka.ms/Fo983c\" alt=\"Duck on a rock\"></img></p>`

---
