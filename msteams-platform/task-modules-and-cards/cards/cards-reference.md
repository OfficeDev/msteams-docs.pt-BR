---
title: Referência de cartões
description: Descreve todas as ações de cartões e cartões disponíveis para bots no Microsoft Teams
keywords: referência de cartões de bots
ms.openlocfilehash: 0bcc905f3d5b678700a396ff3e5b8b5f0232046f
ms.sourcegitcommit: d61f14053fc695bc1956bf50e83956613c19ccca
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/13/2020
ms.locfileid: "48452607"
---
# <a name="cards-reference"></a>Referência de cartões

Os cartões listados nesta seção têm suporte em bots para o Microsoft Teams. Eles são baseados em cartões definidos pela estrutura de bot, mas o Microsoft Teams não dá suporte a todas as placas de estrutura de bot e adicionou alguns dos seus próprios. As diferenças são chamadas nas referências abaixo.

## <a name="card-examples"></a>Exemplos de cartões

Você pode encontrar informações adicionais sobre como usar cartões na documentação do SDK do bot Builder (v3). Há também exemplos de código disponíveis no repositório do Microsoft/BotBuilder-Samples no GitHub.

* .NET
  * [Adicionar cartões como anexos a mensagens](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments)
  * [Código de exemplo de cartões (Construtor de bot v3)](https://github.com/Microsoft/BotBuilder-Samples/tree/v3-sdk-samples/CSharp/cards-RichCards)
* Node.js
  * [Adicionar cartões como anexos a mensagens](/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)
  * [Código de exemplo de cartões (Construtor de bot v3)](https://github.com/Microsoft/BotBuilder-Samples/tree/v3-sdk-samples/Node/cards-RichCards)

## <a name="types-of-cards"></a>Tipos de cartões

Esta tabela mostra os tipos de cartões disponíveis para você.

| Tipo de cartão | Descrição |
| --- | --- |
| [Cartão adaptável](#adaptive-card) | Cartão altamente personalizável que pode conter qualquer combinação de texto, voz, imagens, botões e campos de entrada. |
| [Cartão herói](#hero-card) | Normalmente contém uma única imagem grande, um ou mais botões e uma pequena quantidade de texto. |
| [Cartão de lista](#list-card) | Uma lista de rolagem dos itens. |
| [Cartão de conexão do Office 365](#office-365-connector-card) | Layout flexível com várias seções, campos, imagens e ações. |
| [Cartão de recibo](#receipt-card) | Fornece um recibo para o usuário. |
| [Cartão de conexão](#signin-card) | Permite que um bot solicite a entrada de um usuário. |
| [Cartão de miniaturas](#thumbnail-card) | Normalmente contém uma única imagem em miniatura, um texto curto e um ou mais botões. |
| [Coleções de cartões](#card-collections) | Usado para retornar vários itens em uma única resposta |

## <a name="common-properties-for-all-cards"></a>Propriedades comuns de todos os cartões

### <a name="inline-card-images"></a>Imagens de cartões embutidos

Seu cartão pode conter uma imagem embutida, incluindo um link para a imagem publicamente disponível. Para fins de desempenho, recomendamos enfaticamente que você hospede sua imagem em uma CDN (rede de distribuição de conteúdo) pública.

As imagens são dimensionadas para cima ou para baixo em tamanho, mantendo a taxa de proporção para cobrir a área da imagem e, em seguida, cortadas do centro para obter a taxa de proporção apropriada para o cartão.

As imagens devem ter no máximo 1024 × 1024 e 1 MB no formato PNG, JPEG ou GIF; GIF animado não é oficialmente suportado.

| Propriedade | Tipo  | Descrição |
| --- | --- | --- |
| url | URL | URL HTTPS para a imagem |
| alt | Cadeia de caracteres | Descrição acessível da imagem |

### <a name="buttons"></a>Botões

Os botões são exibidos empilhados na parte inferior do cartão. O texto do botão está sempre em uma única linha e será truncado se o texto exceder a largura do botão. Qualquer outro botão além do número máximo suportado pelo cartão não será exibido.

Consulte [ações do cartão](~/task-modules-and-cards/cards/cards-actions.md) para obter mais informações.

### <a name="card-formatting"></a>Formatação de cartão

Consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md) para obter mais informações sobre formatação de texto em cartões.

## <a name="adaptive-card"></a>Cartão adaptável

Um cartão personalizável que pode conter qualquer combinação de texto, fala, imagem, botões e campos de entrada. *Veja* [cartões adaptáveis v 1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).

### <a name="support-for-adaptive-cards"></a>Suporte para cartões adaptáveis

| Bots no Teams | Extensões de Mensagens  | Conectores | Estrutura de bot |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |
|

> [!NOTE]
> Os elementos de mídia atualmente não têm suporte em cartões adaptáveis v 1.2 na plataforma do teams.

### <a name="example-adaptive-card"></a>Cartão adaptável de exemplo

![Exemplo de um cartão de cartão adaptável](~/assets/images/cards/adaptivecard.png)

```json
{
  "contentType": "application/vnd.microsoft.card.adaptive",
  "content": {
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
      {
        "type": "Container",
        "items": [
          {
            "type": "TextBlock",
            "text": "Publish Adaptive Card schema",
            "weight": "bolder",
            "size": "medium"
          },
          {
            "type": "ColumnSet",
            "columns": [
              {
                "type": "Column",
                "width": "auto",
                "items": [
                  {
                    "type": "Image",
                    "url": "https://pbs.twimg.com/profile_images/3647943215/d7f12830b3c17a5a9e4afcc370e3a37e_400x400.jpeg",
                    "size": "small",
                    "style": "person"
                  }
                ]
              },
              {
                "type": "Column",
                "width": "stretch",
                "items": [
                  {
                    "type": "TextBlock",
                    "text": "Matt Hidinger",
                    "weight": "bolder",
                    "wrap": true
                  },
                  {
                    "type": "TextBlock",
                    "spacing": "none",
                    "text": "Created {{DATE(2017-02-14T06:08:39Z, SHORT)}}",
                    "isSubtle": true,
                    "wrap": true
                  }
                ]
              }
            ]
          }
        ]
      },
      {
        "type": "Container",
        "items": [
          {
            "type": "TextBlock",
            "text": "Now that we have defined the main rules and features of the format, we need to produce a schema and publish it to GitHub. The schema will be the starting point of our reference documentation.",
            "wrap": true
          },
          {
            "type": "FactSet",
            "facts": [
              {
                "title": "Board:",
                "value": "Adaptive Card"
              },
              {
                "title": "List:",
                "value": "Backlog"
              },
              {
                "title": "Assigned to:",
                "value": "Matt Hidinger"
              },
              {
                "title": "Due date:",
                "value": "Not set"
              }
            ]
          }
        ]
      }
    ],
    "actions": [
      {
        "type": "Action.ShowCard",
        "title": "Set due date",
        "card": {
          "type": "AdaptiveCard",
          "body": [
            {
              "type": "Input.Date",
              "id": "dueDate"
            }
          ],
          "actions": [
            {
              "type": "Action.Submit",
              "title": "OK"
            }
          ]
        }
      },
      {
        "type": "Action.ShowCard",
        "title": "Comment",
        "card": {
          "type": "AdaptiveCard",
          "body": [
            {
              "type": "Input.Text",
              "id": "comment",
              "isMultiline": true,
              "placeholder": "Enter your comment"
            }
          ],
          "actions": [
            {
              "type": "Action.Submit",
              "title": "OK"
            }
          ]
        }
      }
    ]
  }  
}
```

#### <a name="for-more-information-on-adaptive-cards"></a>Para obter mais informações sobre cartões adaptáveis

* [Visão geral de cartões adaptáveis](/adaptive-cards/)
* [Ações de cartão adaptável no Microsoft Teams](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)

## <a name="hero-card"></a>Cartão herói

Um cartão que normalmente contém uma única imagem grande, um ou mais botões e texto.

### <a name="support-for-hero-cards"></a>Suporte para cartões herói

| Bots no Teams | Extensões de Mensagens  | Conectores | Estrutura de bot |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |
|

### <a name="properties-of-a-hero-card"></a>Propriedades de um cartão herói

| Propriedade | Tipo  | Descrição |
| --- | --- | --- |
| title | Rich text  | Título do cartão. Máximo de 2 linhas. |
| título | Rich text  | Subtítulo do cartão. Máximo de 2 linhas.|
| texto | Rich text  | O texto aparece logo abaixo do subtítulo; Veja [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md) para opções de formatação |
| imagem | Matriz de imagens | Imagem exibida na parte superior do cartão. Taxa de proporção 16:9 |
| recolhe | Matriz de objetos Action | Conjunto de ações aplicáveis ao cartão atual. Máximo de 6 |
| Aproveite | Objeto Action | Esta ação será ativada quando o usuário tocar no próprio cartão |
|

### <a name="example-hero-card"></a>Cartão herói de exemplo

![Exemplo de um cartão herói](~/assets/images/cards/hero.png)

```json
{
   "contentType": "application/vnd.microsoft.card.hero",
   "content": {
     "title": "Seattle Center Monorail",
     "subtitle": "Seattle Center Monorail",
     "text": "The Seattle Center Monorail is an elevated train line between Seattle Center (near the Space Needle) and downtown Seattle. It was built for the 1962 World's Fair. Its original two trains, completed in 1961, are still in service.",
     "images": [
       {
         "url":"https://upload.wikimedia.org/wikipedia/commons/thumb/4/49/Seattle_monorail01_2008-02-25.jpg/1024px-Seattle_monorail01_2008-02-25.jpg"
       }
     ],
    "buttons": [
      {
         "type": "openUrl",
         "title": "Official website",
         "value": "https://www.seattlemonorail.com"
       },
      {
        "type": "openUrl",
        "title": "Wikipeda page",
        "value": "https://en.wikipedia.org/wiki/Seattle_Center_Monorail"
       }
     ]
   }
}

```

### <a name="for-more-information-on-hero-cards"></a>Para obter mais informações sobre cartões de herói

Referência da estrutura do bot:

* [Nó do cartão herói](https://docs.microsoft.com/javascript/api/botframework-schema/herocard)
* [Cartão herói C #](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.herocard?view=botbuilder-dotnet-3.0&preserve-view=true)

## <a name="list-card"></a>Cartão de lista

O cartão de lista foi adicionado pelo Microsoft Teams para fornecer funções além do que a coleção List pode fornecer. O cartão de lista fornece uma lista de rolagem dos itens.

### <a name="support-for-list-cards"></a>Suporte para cartões de lista

| Bots no Teams | Extensões de Mensagens  | Conectores | Estrutura de bot |
| --- | --- | --- | --- |
| ✔ | ✖ | ✖ |✔ |
|

### <a name="properties-of-a-list-card"></a>Propriedades de um cartão de lista

| Propriedade | Tipo  | Descrição |
| --- | --- | --- |
| title | Rich text  | Título do cartão. Máximo de 2 linhas.|
| itens | Matriz de itens de lista  ||
| recolhe | Matriz de objetos Action | Conjunto de ações aplicáveis ao cartão atual. Máximo de 6. |

### <a name="example-list-card"></a>Exemplo de cartão de lista

```json
{
  "contentType": "application/vnd.microsoft.teams.card.list",
  "content": {
    "title": "Card title",
    "items": [
      {
        "type": "file",
        "id": "https://contoso.sharepoint.com/teams/new/Shared%20Documents/Report.xlsx",
        "title": "Report",
        "subtitle": "teams > new > design",
        "tap": {
          "type": "imBack",
          "value": "editOnline https://contoso.sharepoint.com/teams/new/Shared%20Documents/Report.xlsx"
        }
      },
      {
        "type": "resultItem",
        "icon": "https://cdn2.iconfinder.com/data/icons/social-icons-33/128/Trello-128.png",
        "title": "Trello title",
        "subtitle": "A Trello subtitle",
        "tap": {
          "type": "openUrl",
          "value": "http://trello.com"
        }
      },
      {
        "type": "section",
        "title": "Manager"
      },
      {
        "type": "person",
        "id": "JohnDoe@contoso.com",
        "title": "John Doe",
        "subtitle": "Manager",
        "tap": {
          "type": "imBack",
          "value": "whois JohnDoe@contoso.com"
        }
      }
    ],
    "buttons": [
      {
        "type": "imBack",
        "title": "Select",
        "value": "whois"
      }
    ]
  }
}
```

## <a name="office-365-connector-card"></a>Cartão de conexão do Office 365

Com suporte no Teams, não na estrutura de bot.

O cartão de conexão do Office 365 fornece um layout flexível com várias seções, campos, imagens e ações. Este cartão encapsula um cartão de conexão para que possa ser usado por bots. Consulte a seção observações para ver as diferenças entre os cartões de conector e o cartão do O365.

### <a name="support-for-office-365-connector-cards"></a>Suporte para cartões conectores do Office 365

| Bots no Teams | Extensões de Mensagens  | Conectores | Estrutura de bot |
| --- | --- | --- | --- |
| ✔ | ✔ | ✔ | ✖ |
|

### <a name="properties-of-the-office-365-connector-card"></a>Propriedades do cartão de conexão do Office 365

| Propriedade | Tipo  | Descrição |
| --- | --- | --- |
| title | Rich text  | Título do cartão. Máximo de 2 linhas. |
| summary | Rich text  | Resumo do cartão. Máximo de 2 linhas. |
| texto | Rich text  | O texto aparece logo abaixo do subtítulo; Veja [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md) para opções de formatação |
| themeColor | Cadeia de caracteres HEX | cor que substitui o accentColor fornecido do manifesto de aplicativo |

### <a name="notes-on-the-office-365-connector-card"></a>Observações sobre o cartão de conexão do Office 365

Os cartões conectores do Office 365 funcionam corretamente no Microsoft Teams, incluindo [ações ActionCard](/outlook/actionable-messages/card-reference#actioncard-action).

Uma diferença importante entre o uso de cartões de conexão de um conector e o uso de cartões de conector no bot é a manipulação de ações de cartão.

* Para um conector, o ponto de extremidade recebe a carga do cartão via HTTP POST.
* Para um bot, a `HttpPOST` ação dispara uma `invoke` atividade que envia apenas a ID e o corpo da ação para o bot.

Cada placa de conector pode exibir um máximo de 10 seções e cada seção pode conter no máximo 5 imagens e 5 ações.

> [!NOTE]
> Quaisquer seções, imagens ou ações adicionais em uma mensagem não serão exibidas.

Todos os campos de texto dão suporte a redução e HTML. Você pode controlar quais seções usam a redução ou HTML, definindo a `markdown` propriedade em uma mensagem. Por padrão, `markdown` é definido como `true` ; se você deseja usar HTML em vez disso, defina `markdown` como `false` .

Se você especificar a `themeColor` propriedade, ela substituirá a `accentColor` propriedade no manifesto do aplicativo.

Para especificar o estilo de renderização para `activityImage` , você pode definir `activityImageType` como a seguir.

| Valor | Descrição |
| --- | --- |
| `avatar` | Será `activityImage` será cortado como um círculo |
| `article` | `activityImage` será exibido como um retângulo e manterá sua taxa de proporção |

Para todos os outros detalhes sobre as propriedades do cartão de conexão, confira a [referência de cartão de mensagem acionável](/outlook/actionable-messages/card-reference). As únicas propriedades da placa de conector que o Microsoft Teams não suporta atualmente são as seguintes:

* `heroImage`
* `hideOriginalBody`
* `startGroup` (sempre tratado como `true` no Teams)
* `originator`
* `correlationId`

### <a name="example-office-365-connector-card"></a>Cartão de conexão de exemplo do Office 365

```json
{
  "contentType": "application/vnd.microsoft.teams.card.o365connector",
  "content": {
    "@type": "MessageCard",
    "@context": "http://schema.org/extensions",
    "summary": "John Doe commented on Trello",
    "title": "Project Tango",
    "sections": [
        {
            "activityTitle": "John Doe commented",
            "activitySubtitle": "On Project Tango",
            "activityText": "\"Here are the designs\"",
            "activityImage": "http://connectorsdemo.azurewebsites.net/images/MSC12_Oscar_002.jpg"
        },
        {
            "title": "Details",
            "facts": [
                {
                    "name": "Labels",
                    "value": "Designs, redlines"
                },
                {
                    "name": "Due date",
                    "value": "Dec 7, 2016"
                },
                {
                    "name": "Attachments",
                    "value": "[final.jpg](http://connectorsdemo.azurewebsites.net/images/WIN14_Jan_04.jpg)"
                }
            ]
        },
        {
            "title": "Images",
            "images": [
                {
                    "image":"http://connectorsdemo.azurewebsites.net/images/MicrosoftSurface_024_Cafe_OH-06315_VS_R1c.jpg"
                },
                {
                    "image":"http://connectorsdemo.azurewebsites.net/images/WIN12_Scene_01.jpg"
                },
                {
                    "image":"http://connectorsdemo.azurewebsites.net/images/WIN12_Anthony_02.jpg"
                }
            ]
        }
    ],
    "potentialAction": [
        {
            "@context": "http://schema.org",
            "@type": "ViewAction",
            "name": "View in Trello",
            "target": [
                "https://trello.com/c/1101/"
            ]
        }
    ]
  }
}
```

## <a name="receipt-card"></a>Cartão de recibo

Com suporte no Teams.

Um cartão que permite que um bot forneça um recibo para o usuário. Normalmente, ela contém a lista de itens a serem incluídos no recebimento, no imposto e nas informações totais e em outros textos.

### <a name="support-for-receipts-cards"></a>Suporte para cartões de recibos

| Bots no Teams | Extensões de Mensagens  | Conectores | Estrutura de bot |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |
|

### <a name="for-more-information-on-receipt-cards"></a>Para obter mais informações sobre cartões de recibo

Referência da estrutura do bot:

* [Nó do cartão de recibo](https://docs.microsoft.com/javascript/api/botframework-schema/receiptcard?view=botbuilder-ts-latest&preserve-view=true)
* [Cartão de recibo C #](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.receiptcard?view=botbuilder-dotnet-3.0&preserve-view=true)

## <a name="signin-card"></a>Cartão de conexão

Um cartão que permite que um bot solicite a entrada de um usuário. Suportado no Teams em um formato levemente diferente do que é encontrado na estrutura de bot. O cartão de entrada no Microsoft Teams é semelhante ao cartão de entrada na estrutura de bot com a exceção de que o cartão de entrada no Microsoft Teams suporta apenas duas ações: `signin` e `openUrl` .

A *ação de entrada* pode ser usada de qualquer cartão no Microsoft Teams, e não apenas do cartão de entrada. Consulte o tópico [Microsoft Teams Authentication Flow para bots](~/bots/how-to/authentication/auth-flow-bot.md) para obter mais detalhes sobre autenticação.

### <a name="support-for-signin-cards"></a>Suporte para placas de entrada

| Bots no Teams | Extensões de Mensagens  | Conectores | Estrutura de bot |
| --- | --- | --- | --- |
| ✔ | ✖ | ✖ | ✔ |
|

### <a name="for-more-information-on-signin-cards"></a>Para obter mais informações sobre cartões de conexão

Referência da estrutura do bot:

* [Nó do cartão de entrada](/javascript/api/botframework-schema/signincard?view=botbuilder-ts-latest&preserve-view=true)
* [Cartão de entrada C #](/dotnet/api/microsoft.bot.connector.signincard?view=botbuilder-dotnet-3.0&preserve-view=true)

## <a name="thumbnail-card"></a>Cartão de miniaturas

Um cartão que normalmente contém uma única imagem em miniatura, um ou mais botões e texto.

### <a name="support-for-thumbnail-cards"></a>Suporte para cartões em miniatura

| Bots no Teams | Extensões de Mensagens  | Conectores | Estrutura de bot |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |
|

![Exemplo de um cartão em miniatura](~/assets/images/cards/thumbnail.png)

### <a name="properties-of-a-thumbnail-card"></a>Propriedades de um cartão em miniatura

| Propriedade | Tipo  | Descrição |
| --- | --- | --- |
| title | Rich text  | Título do cartão. Máximo de 2 linhas.|
| título | Rich text  | Subtítulo do cartão. Máximo de 2 linhas.|
| texto | Rich text  | O texto aparece logo abaixo do subtítulo; Veja [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md) para opções de formatação |
| imagem | Matriz de imagens | Imagem exibida na parte superior do cartão. Taxa de proporção 1:1 (quadrado) |
| recolhe | Matriz de objetos Action | Conjunto de ações aplicáveis ao cartão atual. Máximo de 6 |
| Aproveite | Objeto Action | Esta ação será ativada quando o usuário tocar no próprio cartão |
|

### <a name="example-thumbnail-card"></a>Cartão de miniatura de exemplo

```json
{
  "contentType": "application/vnd.microsoft.card.thumbnail",
  "content": {
    "title": "Bender",
    "subtitle": "tale of a robot who dared to love",
    "text": "Bender Bending Rodríguez is a main character in the animated television series Futurama. He was created by series creators Matt Groening and David X. Cohen, and is voiced by John DiMaggio",
    "images": [
      {
        "url": "https://upload.wikimedia.org/wikipedia/en/a/a6/Bender_Rodriguez.png",
        "alt": "Bender Rodríguez"
      }
    ],
    "buttons": [
      {
        "type": "imBack",
        "title": "Thumbs Up",
        "image": "http://moopz.com/assets_c/2012/06/emoji-thumbs-up-150-thumb-autox125-140616.jpg",
        "value": "I like it"
      },
      {
        "type": "imBack",
        "title": "Thumbs Down",
        "image": "http://yourfaceisstupid.com/wp-content/uploads/2014/08/thumbs-down.png",
        "value": "I don't like it"
      },
      {
        "type": "openUrl",
        "title": "I feel lucky",
        "image": "http://thumb9.shutterstock.com/photos/thumb_large/683806/148441982.jpg",
        "value": "https://www.bing.com/images/search?q=bender&qpvt=bender&qpvt=bender&qpvt=bender&FORM=IGRE"
      }
    ],
    "tap": {
      "type": "imBack",
      "value": "Tapped it!"
    }
  }
}
```

### <a name="for-more-information"></a>Para obter mais informações

Referência da estrutura do bot:

* [Nó de cartão de miniatura](https://docs.microsoft.com/javascript/api/botframework-schema/thumbnailcard?view=botbuilder-ts-latest&preserve-view=true)
* [Cartão-miniatura C #](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.thumbnailcard?view=botbuilder-dotnet-3.0&preserve-view=true)

## <a name="card-collections"></a>Coleções de cartões

As coleções de cartões têm suporte no Microsoft Teams.

As coleções de cartões são fornecidas pela estrutura de bot: `builder.AttachmentLayout.carousel` e `builder.AttachmentLayout.list` . Essas coleções podem conter cartões adaptáveis, herói ou de miniaturas.

## <a name="carousel-collection"></a>Coleção carrossel

O [layout do carrossel](/azure/bot-service/dotnet/bot-builder-dotnet-add-rich-card-attachments?view=azure-bot-service-3.0&preserve-view=true) mostra um carrossel de cartões, opcionalmente, com os botões de ação associados.

### <a name="support-for-carousel-collections"></a>Suporte para coleções de carrossel

| Bots no Teams | Extensões de Mensagens  | Conectores | Estrutura de bot |
| --- | --- | --- | --- |
| ✔ | ✖ | ✖ | ✔ |
|

> [!NOTE]
> Um carrossel pode exibir no máximo 10 cartões por mensagem.

### <a name="example-carousel-collection"></a>Coleção de carrossel de exemplo

![Exemplo de um carrossel de cartões](~/assets/images/cards/carousel.png)

As propriedades são as mesmas do herói ou do cartão de miniatura.

### <a name="syntax-for-carousel-collections"></a>Sintaxe de coleções do carrossel

`builder.AttachmentLayout.carousel`

## <a name="list-collection"></a>Coleção List

### <a name="support-for-list-collections"></a>Suporte para coleções de listas

O layout de lista mostra uma lista de cartões empilhados verticalmente, opcionalmente com os botões de ação associados.

| Bots no Teams | Extensões de Mensagens  | Conectores | Estrutura de bot |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |
|

### <a name="example-list-collection"></a>Exemplo de coleção List

![Exemplo de uma lista de cartões](~/assets/images/cards/list.png)

As propriedades são as mesmas do herói ou do cartão de miniatura.

Uma lista pode exibir no máximo 10 cartões por mensagem.

> [!NOTE]
> Algumas combinações de cartões de lista ainda não são suportadas no iOS e no Android.

### <a name="syntax-for-list-collections"></a>Sintaxe para coleções de listas

`builder.AttachmentLayout.list`

## <a name="cards-not-supported-in-teams"></a>Cartões não suportados no Teams

Os seguintes cartões são implementados pela estrutura do bot, mas não são suportados pelo Teams.

* Cartões de animação
* Placas de áudio
* Placas de vídeo
