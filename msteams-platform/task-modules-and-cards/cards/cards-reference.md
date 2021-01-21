---
title: Referência de cartões
description: Descreve todas as ações de cartões e cartões disponíveis para bots no Teams
keywords: referência de cartões de bots
ms.topic: reference
ms.openlocfilehash: 839430baa5ce5e8950a21a1472036c6fd96f4edf
ms.sourcegitcommit: 00c657e3bf57d3b92aca7da941cde47a2eeff4d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "49911889"
---
# <a name="cards-reference"></a>Referência de cartões

Os cartões listados nesta seção têm suporte em bots para o Microsoft Teams. Eles são baseados em cartões definidos pela Estrutura de Bot, mas o Teams não dá suporte a todos os cartões do Bot Framework e adicionou alguns de seus próprios cartões. Diferenças são destacadas nas referências neste documento.

## <a name="card-examples"></a>Exemplos de cartão

Você pode encontrar informações adicionais sobre como usar cartões na documentação do SDK do Construtor de Bots (v3). Exemplos de código também estão disponíveis no repositório Microsoft/BotBuilder-Samples no GitHub.

* .NET
  * [Adicionar cartões como anexos a mensagens](/bot-framework/dotnet/bot-builder-dotnet-add-rich-card-attachments)
  * [Código de exemplo de cartões (Construtor de Bots v3)](https://github.com/Microsoft/BotBuilder-Samples/tree/v3-sdk-samples/CSharp/cards-RichCards)
* Node.js
  * [Adicionar cartões como anexos a mensagens](/bot-framework/nodejs/bot-builder-nodejs-send-rich-cards)
  * [Código de exemplo de cartões (Construtor de Bots v3)](https://github.com/Microsoft/BotBuilder-Samples/tree/v3-sdk-samples/Node/cards-RichCards)

## <a name="types-of-cards"></a>Tipos de cartões

Esta tabela mostra os tipos de cartões disponíveis para você:

| Tipo de cartão | Descrição |
| --- | --- |
| [Cartão adaptável](#adaptive-card) | Cartão altamente personalizável que pode conter qualquer combinação de texto, fala, imagens, botões e campos de entrada. |
| [Cartão de herói](#hero-card) | Normalmente contém uma única imagem grande, um ou mais botões e uma pequena quantidade de texto. |
| [Cartão de lista](#list-card) | Uma lista de rolagem de itens. |
| [Cartão de conector do Office 365](#office-365-connector-card) | Layout flexível com várias seções, campos, imagens e ações. |
| [Cartão de confirmação](#receipt-card) | Fornece um recibo ao usuário. |
| [Signin card](#signin-card) | Permite que um bot solicite que um usuário entre. |
| [Cartão de miniatura](#thumbnail-card) | Normalmente contém uma única imagem em miniatura, algum texto curto e um ou mais botões. |
| [Coleções de cartões](#card-collections) | Usado para retornar vários itens em uma única resposta. |

## <a name="common-properties-for-all-cards"></a>Propriedades comuns para todos os cartões

### <a name="inline-card-images"></a>Imagens de cartão em linha

O cartão pode conter uma imagem em linha incluindo um link para a imagem publicamente disponível. Para fins de desempenho, é altamente recomendável que você hospede a imagem em uma CDN (rede pública de distribuição de conteúdo).

As imagens são dimensionados para cima ou para baixo em tamanho, mantendo a taxa de proporção para cobrir a área da imagem e, em seguida, cortadas do centro para obter a taxa de proporção apropriada para o cartão.

As imagens devem ter, no máximo, 1024×1024, em formato PNG, JPEG ou GIF, e GIF animado não é suportado.

| Propriedade | Tipo  | Descrição |
| --- | --- | --- |
| url | URL | URL HTTPS para a imagem |
| alt | Cadeia de caracteres | Descrição acessível da imagem |

### <a name="buttons"></a>Botões

Os botões são mostrados empilhados na parte inferior do cartão. O texto do botão está sempre em uma única linha e será truncado se o texto exceder a largura do botão. Quaisquer botões adicionais além do número máximo suportado pelo cartão não serão mostrados.

Consulte [Ações do Cartão](~/task-modules-and-cards/cards/cards-actions.md) para obter mais informações.

### <a name="card-formatting"></a>Formatação de cartão

Consulte [Formatação de Cartão](~/task-modules-and-cards/cards/cards-format.md) para obter mais informações sobre formatação de texto em cartões.

## <a name="adaptive-card"></a>Cartão adaptável

Um cartão adaptável é um cartão personalizável que pode conter qualquer combinação de texto, fala, imagens, botões e campos de entrada. Consulte [Cartões Adaptáveis v1.2.0.](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0)

### <a name="support-for-adaptive-cards"></a>Suporte para cartões adaptáveis

| Bots no Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

> [!NOTE]
> * A plataforma do Teams é compatível com a versão 1.2 ou anterior dos recursos de cartão adaptável.
> * Atualmente, os elementos de mídia não têm suporte no cartão adaptável v1.2 na plataforma do Teams.

### <a name="example-of-an-adaptive-card"></a>Exemplo de um cartão adaptável

![Exemplo de um cartão adaptável](~/assets/images/cards/adaptivecard.png)

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

#### <a name="additional-information-on-adaptive-cards"></a>Informações adicionais sobre cartões adaptáveis

* [Visão geral dos cartões adaptáveis](/adaptive-cards/)
* [Ações de cartão adaptáveis no Teams](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)

## <a name="hero-card"></a>Cartão de herói

Um cartão que normalmente contém uma única imagem grande, um ou mais botões e texto.

### <a name="support-for-hero-cards"></a>Suporte para cartões de herói

| Bots no Teams | Extensões de Mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

### <a name="properties-of-a-hero-card"></a>Propriedades de um cartão de herói

| Propriedade | Tipo  | Descrição |
| --- | --- | --- |
| title | Rich text  | Título do cartão. Máximo de 2 linhas. |
| subtitle | Rich text  | Subtítulo do cartão. Máximo de 2 linhas.|
| texto | Rich text  | O texto aparece logo abaixo do subtítulo; consulte [Formatação de cartão](~/task-modules-and-cards/cards/cards-format.md) para opções de formatação. |
| images | Matriz de imagens | Imagem exibida na parte superior do cartão. Taxa de proporção 16:9. |
| buttons | Matriz de objetos de ação | Conjunto de ações aplicáveis ao cartão atual. Máximo 6. |
| tocar | Objeto Action | Essa ação será ativada quando o usuário tocar no próprio cartão. |

### <a name="example-of-a-hero-card"></a>Exemplo de um cartão de herói

![Exemplo de um cartão de herói](~/assets/images/cards/hero.png)

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

### <a name="additional-information-on-hero-cards"></a>Informações adicionais sobre cartões de herói

Referência da Estrutura de Bot:

* [Nó de cartão de herói](https://docs.microsoft.com/javascript/api/botframework-schema/herocard)
* [Cartão de herói C #](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.herocard?view=botbuilder-dotnet-3.0&preserve-view=true)

## <a name="list-card"></a>Cartão de lista

O cartão de lista foi adicionado pelo Teams para fornecer funções além do que a coleção de listas pode fornecer. O cartão de lista fornece uma lista de rolagem de itens.

### <a name="support-for-list-cards"></a>Suporte para cartões de lista

| Bots no Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✖ | ✖ |✔ |

### <a name="properties-of-a-list-card"></a>Propriedades de um cartão de lista

| Propriedade | Tipo  | Descrição |
| --- | --- | --- |
| title | Rich text  | Título do cartão. Máximo de 2 linhas.|
| items | Matriz de itens de lista  ||
| buttons | Matriz de objetos de ação | Conjunto de ações aplicáveis ao cartão atual. Máximo 6. |

### <a name="example-of-a-list-card"></a>Exemplo de um cartão de lista

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

## <a name="office-365-connector-card"></a>Cartão de conector do Office 365

O cartão do Conector do Office 365 é compatível com o Teams, não no Bot Framework. Este cartão fornece um layout flexível com várias seções, campos, imagens e ações. Esse cartão encapsula um cartão de conector para que ele possa ser usado por bots. Consulte a seção de observações para ver as diferenças entre cartões de conector e o cartão O365.

### <a name="support-for-office-365-connector-cards"></a>Suporte para cartões de conector do Office 365

| Bots no Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✔ | ✖ |

### <a name="properties-of-the-office-365-connector-card"></a>Propriedades do cartão de conector do Office 365

| Propriedade | Tipo  | Descrição |
| --- | --- | --- |
| title | Rich text  | Título do cartão. Máximo de 2 linhas. |
| summary | Rich text  | Resumo do cartão. Máximo de 2 linhas. |
| texto | Rich text  | O texto aparece logo abaixo do subtítulo; consulte [Formatação de cartão](~/task-modules-and-cards/cards/cards-format.md) para opções de formatação. |
| themeColor | Cadeia de caracteres HEX | Cor que substitui a accentColor fornecida do manifesto do aplicativo. |

### <a name="notes-on-the-office-365-connector-card"></a>Observações sobre o cartão de conector do Office 365

Cartões de conector do Office 365 funcionam corretamente no Microsoft Teams, incluindo [ações actionCard](/outlook/actionable-messages/card-reference#actioncard-action).

Uma diferença importante entre usar cartões de conector de um conector e usar cartões de conector em seu bot é o tratamento de ações de cartão.

* Para um conector, o ponto de extremidade recebe a carga do cartão via HTTP POST.
* Para um bot, a ação dispara uma atividade que envia apenas a ID de ação `HttpPOST` e o corpo para o `invoke` bot.

Cada cartão de conector pode exibir no máximo 10 seções, e cada seção pode conter no máximo 5 imagens e 5 ações.

> [!NOTE]
> Quaisquer seções, imagens ou ações adicionais em uma mensagem não serão exibidas.

Todos os campos de texto suportam Markdown e HTML. Você pode controlar quais seções usam Markdown ou HTML definindo `markdown` a propriedade em uma mensagem. Por padrão, `markdown` é definido como ; se você quiser usar HTML em vez `true` disso, de definida como `markdown` `false` .

Se você especificar a `themeColor` propriedade, ela substituirá `accentColor` a propriedade no manifesto do aplicativo.

Para especificar o estilo de `activityImage` renderização, você pode definir `activityImageType` da seguinte forma:

| Valor | Descrição |
| --- | --- |
| `avatar` | Padrão; `activityImage` será cortada como um círculo. |
| `article` | `activityImage` será exibido como um retângulo e manterá sua taxa de proporção. |

Para obter todos os outros detalhes sobre as propriedades do cartão do conector, consulte a referência [de cartão de mensagem a actionable.](/outlook/actionable-messages/card-reference) As únicas propriedades de cartão de conector que o Microsoft Teams não dá suporte no momento são as seguinte:

* `heroImage`
* `hideOriginalBody`
* `startGroup` (sempre tratado como `true` no Teams)
* `originator`
* `correlationId`

### <a name="example-of-an-office-365-connector-card"></a>Exemplo de um cartão de conector do Office 365

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

## <a name="receipt-card"></a>Cartão de confirmação

O Teams dá suporte ao cartão de confirmação. É um cartão que permite que um bot forneça um recibo ao usuário. Normalmente, ele contém a lista de itens a incluir no recibo, como imposto e informações totais.

### <a name="support-for-receipt-cards"></a>Suporte para cartões de confirmação

| Bots no Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

### <a name="example-of-a-receipt-card"></a>Exemplo de um cartão de confirmação

![Exemplo de um cartão de confirmação](~/assets/images/cards/receipt.png)

```json
{
  "contentType": "application/vnd.microsoft.card.receipt",
  "content": {
    "title": "John Doe",
    "facts": [
      {
        "key": "Order Number",
        "value": "1234"
      },
      {
        "key": "Payment Method",
        "value": "VISA 5555-****"
      }
    ],
    "items": [
      {
        "title": "Data Transfer",
        "image": {
          "url": "https://github.com/amido/azure-vector-icons/raw/master/renders/traffic-manager.png"
        },
        "price": "$ 38.45",
        "quantity": "368"
      },
      {
        "title": "App Service",
        "image": {
          "url": "https://github.com/amido/azure-vector-icons/raw/master/renders/cloud-service.png"
        },
        "price": "$ 45.00",
        "quantity": "720"
      }
    ],
    "total": "$ 90.95",
    "tax": "$ 7.50",
    "buttons": [
      {
        "type": "openUrl",
        "title": "More information",
        "image": "https://account.windowsazure.com/content/6.10.1.38-.8225.160809-1618/aux-pre/images/offer-icon-freetrial.png",
        "value": "https://azure.microsoft.com/en-us/pricing/"
      }
    ]
  }
}
```

### <a name="additional-information-on-receipt-cards"></a>Informações adicionais sobre cartões de confirmação

Referência da Estrutura de Bot:

* [Nó do cartão de confirmação](https://docs.microsoft.com/javascript/api/botframework-schema/receiptcard?view=botbuilder-ts-latest&preserve-view=true)
* [Cartão de confirmação C #](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.receiptcard?view=botbuilder-dotnet-3.0&preserve-view=true)

## <a name="signin-card"></a>Signin card

O cartão de acesso permite que um bot solicite que um usuário entre. Com suporte no Teams de uma forma ligeiramente diferente da encontrada na Estrutura do Bot. O cartão de login no Teams é semelhante ao cartão de login na Estrutura do Bot, exceto pelo fato de que o cartão de login no Teams só dá suporte a duas ações: `signin` e `openUrl` .

A *ação de entrar* pode ser usada em qualquer cartão no Teams, não apenas no cartão de visita. Para obter mais detalhes sobre autenticação, confira [o fluxo de autenticação do Microsoft Teams para bots.](~/bots/how-to/authentication/auth-flow-bot.md)

### <a name="support-for-signin-cards"></a>Suporte para cartões de login

| Bots no Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✖ | ✖ | ✔ |

### <a name="additional-information-on-signin-cards"></a>Informações adicionais sobre cartões de assinatura

Referência da Estrutura de Bot:

* [Nó do cartão de conexão](/javascript/api/botframework-schema/signincard?view=botbuilder-ts-latest&preserve-view=true)
* [Signin card C #](/dotnet/api/microsoft.bot.connector.signincard?view=botbuilder-dotnet-3.0&preserve-view=true)

## <a name="thumbnail-card"></a>Cartão de miniatura

Um cartão que normalmente contém uma única imagem em miniatura, um ou mais botões e texto.

### <a name="support-for-thumbnail-cards"></a>Suporte para cartões de miniatura

| Bots no Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

![Exemplo de um cartão em miniatura](~/assets/images/cards/thumbnail.png)

### <a name="properties-of-a-thumbnail-card"></a>Propriedades de um cartão de miniatura

| Propriedade | Tipo  | Descrição |
| --- | --- | --- |
| title | Rich text  | Título do cartão. Máximo de 2 linhas.|
| subtitle | Rich text  | Subtítulo do cartão. Máximo de 2 linhas.|
| texto | Rich text  | O texto aparece logo abaixo do subtítulo; consulte [Formatação de cartão](~/task-modules-and-cards/cards/cards-format.md) para opções de formatação. |
| images | Matriz de imagens | Imagem exibida na parte superior do cartão. Taxa de proporção 1:1 (quadrado). |
| buttons | Matriz de objetos de ação | Conjunto de ações aplicáveis ao cartão atual. Máximo 6. |
| tocar | Objeto Action | Essa ação será ativada quando o usuário tocar no próprio cartão. |

### <a name="example-of-a-thumbnail-card"></a>Exemplo de um cartão em miniatura

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

### <a name="additional-information"></a>Informações adicionais

Referência da Estrutura de Bot:

* [Nó do cartão de miniatura](https://docs.microsoft.com/javascript/api/botframework-schema/thumbnailcard?view=botbuilder-ts-latest&preserve-view=true)
* [Cartão de miniatura C #](https://docs.microsoft.com/dotnet/api/microsoft.bot.connector.thumbnailcard?view=botbuilder-dotnet-3.0&preserve-view=true)

## <a name="card-collections"></a>Coleções de cartões

O Teams dá suporte a coleções de cartões.

Coleções de cartões: `builder.AttachmentLayout.carousel` e `builder.AttachmentLayout.list` . Essas coleções contêm cartões adaptáveis, em forma de herói ou em miniatura.

## <a name="carousel-collection"></a>Coleção Carousel

O [layout do carrossel](/azure/bot-service/dotnet/bot-builder-dotnet-add-rich-card-attachments?view=azure-bot-service-3.0&preserve-view=true) mostra um carrossel de cartões, opcionalmente com botões de ação associados.

### <a name="support-for-carousel-collections"></a>Suporte para coleções de carrossel

| Bots no Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✖ | ✖ | ✔ |

> [!NOTE]
> Um carrossel pode exibir no máximo 10 cartões por mensagem.

### <a name="properties-of-a-carousel-card"></a>Propriedades de um cartão de carrossel

As propriedades de um cartão carrossel são iguais às dos cartões Hero e Thumbnail.

### <a name="example-of-a-carousel-collection"></a>Exemplo de uma coleção de carrossel

![Exemplo de um carrossel de cartões](~/assets/images/cards/carousel.png)

```json
{
 "attachmentLayout": "carousel",
 "attachments":[
    {
      "contentType": "application/vnd.microsoft.card.adaptive",
      "content": {
        "type": "AdaptiveCard",
        "version": "1.0",
        "body": [
          {
            "type": "Container",
            "items": [
              {
                "type": "TextBlock",
                "size": "extraLarge",
                "weight": "bolder",
                "text": "Welcome to Employee Connect",
                "height": "stretch"
              },
              {
                "type": "TextBlock",
                "size": "medium",
                "weight": "bolder",
                "text": "Add events to your calendar",
                "height": "stretch"
              },
              {
                "type": "TextBlock",
                "weight": "bolder",
                "text": "The bot can send \r\rnotification to remind \r\ryou about the latest \r\revents and trainings.",
                "wrap": true,
                "height": "stretch"
              },
              {
                "type": "ColumnSet",
                "columns": [
                  {
                    "type": "Column",
                    "items": [],
                    "height": "stretch"
                  }
                ]
              },
              {
                "type": "ColumnSet",
                "columns": [
                  {
                    "type": "Column",
                    "items": [],
                    "height": "stretch"
                  }
                ]
              }
            ]
          }
        ],
        "actions": [
          {
            "type": "Action.Submit",
            "title": "Let's get started"
          }
        ]
      }
    },
    {
      "contentType": "application/vnd.microsoft.card.adaptive",
      "content": {
        "type": "AdaptiveCard",
        "version": "1.2",
        "body": [
          {
            "type": "Container",
            "items": [
              {
                "type": "TextBlock",
                "size": "large",
                "weight": "bolder",
                "text": "Employee connect"
              },
              {
                "type": "TextBlock",
                "text": "The bot can send notifications \r\rto remind you about the latest \r\r events and trainings",
                "wrap": true,
                "maxWidth": 2
              },
              {
                "type": "ColumnSet",
                "columns": [
                  {
                    "type": "Column",
                    "items": [],
                    "height": "stretch"
                  }
                ]
              },
              {
                "type": "ColumnSet",
                "columns": [
                  {
                    "type": "Column",
                    "items": [],
                    "height": "stretch"
                  }
                ]
              }
            ]
          }
        ],
        "actions": [
          {
            "type": "Action.Submit",
            "title": "Let's get started"
          }
        ]
      }
    },
    {
      "contentType": "application/vnd.microsoft.card.adaptive",
      "content": {
        "type": "AdaptiveCard",
        "version": "1.0",
        "body": [
          {
            "type": "Container",
            "items": [
              {
                "type": "TextBlock",
                "size": "large",
                "weight": "bolder",
                "text": "Employee Connect final"
              },
              {
                "type": "TextBlock",
                "weight": "bolder",
                "text": "Create and manage your tasks",
                "wrap": true
              },
              {
                "type": "TextBlock",
                "text": "The app identifies all your pending tasks \r\r and helps you manage everything at \r\r one place.",
                "wrap": true
              },
              {
                "type": "TextBlock",
                "weight": "bolder",
                "text": "Try these commands \r\r- Pending Submissions \r\r- Pending Approvals- My Tools",
                "wrap": true,
                "height": "stretch"
              }
            ]
          }
        ],
        "actions": [
          {
            "type": "Action.Submit",
            "title": "Let's get started"
          }
        ]
      }
    }
  ]
}
```

### <a name="syntax-for-carousel-collections"></a>Sintaxe para coleções de carrossel

`builder.AttachmentLayoutTypes.Carousel`

## <a name="list-collection"></a>Listar coleção

### <a name="support-for-list-collections"></a>Suporte para coleções de listas

O layout da lista mostra uma lista de cartões empilhados verticalmente, opcionalmente com botões de ação associados.

| Bots no Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

### <a name="example-of-a-list-collection"></a>Exemplo de uma coleção de listas

![Exemplo de uma lista de cartões](~/assets/images/cards/list.png)

As propriedades são iguais às do herói ou da miniatura.

Uma lista pode exibir no máximo 10 cartões por mensagem.

> [!NOTE]
> Algumas combinações de cartões de lista ainda não têm suporte no iOS e no Android.

### <a name="syntax-for-list-collections"></a>Sintaxe para coleções de listas

`builder.AttachmentLayout.list`

## <a name="cards-not-supported-in-teams"></a>Cartões não suportados no Teams

Os cartões a seguir são implementados pela Estrutura de Bot, mas NÃO são suportados pelo Teams.

* Cartões de animação
* Cartões de áudio
* Placas de vídeo
