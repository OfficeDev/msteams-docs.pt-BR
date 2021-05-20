---
title: Referência de cartões
description: Descreve todas as ações de cartões e cartões disponíveis para bots em Teams
localization_priority: Normal
keywords: referência de cartões de bots
ms.topic: reference
ms.openlocfilehash: cab7f1659759f40beb1aba59531ee6c1a84662c1
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566856"
---
# <a name="cards-reference"></a>Referência de cartões

Os cartões listados neste documento são suportados em bots para Microsoft Teams. Eles são baseados em cartões definidos pelo Bot Framework, mas Teams não suporta todos os cartões Bot Framework e, em vez disso, alguns cartões Teams foram adicionados. As diferenças são chamadas nas referências deste documento.

## <a name="card-examples"></a>Exemplos de cartões

Você pode encontrar informações adicionais sobre como usar cartões na documentação para o Bot Builder SDK v3. As amostras de código também estão disponíveis no repositório Microsoft/BotBuilder-Samples em GitHub.

* .NET
  * [Adicione cartões como anexos às mensagens](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true).
  * [Código de amostra de cartões Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/06.using-cards).

* Node.js
  * [Adicione cartões como anexos às mensagens](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true).
  * [Código de amostra de cartões Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/06.using-cards).

## <a name="types-of-cards"></a>Tipos de cartões

Esta tabela mostra os tipos de cartões disponíveis para você:

| Tipo de cartão | Descrição |
| --- | --- |
| [Cartão adaptativo](#adaptive-card) | Este cartão é altamente personalizável que pode conter qualquer combinação de texto, fala, imagens, botões e campos de entrada. |
| [Cartão de herói](#hero-card) | Este cartão normalmente contém uma única imagem grande, um ou mais botões, e uma pequena quantidade de texto. |
| [Cartão de lista](#list-card) | Este cartão é uma lista de itens de rolagem. |
| [cartão conector Office 365](#office-365-connector-card) | Este cartão tem um layout flexível com várias seções, campos, imagens e ações. |
| [Cartão de recebimento](#receipt-card) | Este cartão fornece um recibo ao usuário. |
| [Cartão de sinalização](#signin-card) | Este cartão permite que um bot solicite que um usuário entre. |
| [Cartão de miniatura](#thumbnail-card) | Esta placa normalmente contém uma única imagem em miniatura, algum texto curto e um ou mais botões. |
| [Coleções de cartões](#card-collections) | Este cartão é usado para retornar vários itens em uma única resposta. |

## <a name="common-properties-for-all-cards"></a>Propriedades comuns para todos os cartões

### <a name="inline-card-images"></a>Imagens de cartão inline

O cartão pode conter uma imagem inline, incluindo um link para a imagem disponível publicamente. Para fins de desempenho, é altamente recomendável que você hospede a imagem em uma rede pública de entrega de conteúdo (CDN).

As imagens são dimensionadas para cima ou para baixo em tamanho, mantendo a proporção para cobrir a área da imagem. As imagens são então cortadas do centro para alcançar a proporção apropriada para o cartão.

As imagens devem ser no máximo 1024×1024, no formato PNG, JPEG ou GIF, e não suportam GIF animado.

| Propriedade | Tipo  | Descrição |
| --- | --- | --- |
| url | URL | URL HTTPS para a imagem. |
| alt | Cadeia de caracteres | Descrição acessível da imagem. |

> [!NOTE]
> Se um cartão incluir uma URL de imagem que passa por um redirecionamento antes da imagem final, o redirecionamento na URL de imagem não será suportado. Isso ocorre para imagens compartilhadas na nuvem pública.

### <a name="buttons"></a>Botões

Os botões são mostrados empilhados na parte inferior do cartão. O texto do botão está sempre em uma única linha e é truncado se o texto exceder a largura do botão. Não são mostrados botões adicionais além do número máximo suportado pelo cartão.

Para obter mais informações, consulte [ações de cartão](~/task-modules-and-cards/cards/cards-actions.md).

### <a name="card-formatting"></a>Formatação de cartões

Para obter mais informações sobre a formatação de texto em cartões, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md).

## <a name="adaptive-card"></a>Cartão adaptativo

Uma placa adaptativa é um cartão personalizável que pode conter qualquer combinação de texto, fala, imagens, botões e campos de entrada. Para obter mais informações, consulte [cartões adaptativos v1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).

### <a name="support-for-adaptive-cards"></a>Suporte para cartões adaptativos

| Bots em Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

> [!NOTE]
> * Teams plataforma suporta v1.2 ou anteriores dos recursos de placas adaptativas.
> * Atualmente, os elementos de mídia não são suportados na placa adaptativa v1.2 na plataforma Teams.

### <a name="example-of-an-adaptive-card"></a>Exemplo de cartão adaptativo

![Exemplo de cartão adaptativo](~/assets/images/cards/adaptivecard.png)

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

#### <a name="additional-information-on-adaptive-cards"></a>Informações adicionais sobre cartões adaptativos

Referência do Bot Framework:

* [Cartões adaptativos Node.js](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true)
* [Cartão adaptativo C #](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true)

## <a name="hero-card"></a>Cartão de herói

Um cartão que normalmente contém uma única imagem grande, um ou mais botões e texto.

### <a name="support-for-hero-cards"></a>Suporte para cartões de herói

| Bots em Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

### <a name="properties-of-a-hero-card"></a>Propriedades de um cartão de herói

| Propriedade | Tipo  | Descrição |
| --- | --- | --- |
| title | Rich text  | Título do cartão. No máximo 2 linhas. |
| subtítulo | Rich text  | Legenda do cartão. No máximo 2 linhas.|
| texto | Rich text  | O texto aparece na legenda. Para opções de formatação, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md). |
| Imagens | Matriz de imagens | Imagem exibida na parte superior do cartão. Proporção 16:9. |
| Botões | Matriz de objetos de ação | Conjunto de ações aplicáveis ao cartão atual. Máximo 6. |
| torneira | Objeto Action | Ativado quando o usuário toca no próprio cartão. |

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

Referência do Bot Framework:

* [cartão de herói Node.js](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-a-hero-card&preserve-view=true)
* [Cartão de herói C #](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-hero-card&preserve-view=true)

## <a name="list-card"></a>Cartão de lista

O cartão de lista foi adicionado por Teams para fornecer funções além do que a coleção de listas pode fornecer. O cartão de lista fornece uma lista de itens de rolagem.

### <a name="support-for-list-cards"></a>Suporte para cartões de lista

| Bots em Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✖ | ✖ |✔ |

### <a name="properties-of-a-list-card"></a>Propriedades de um cartão de lista

| Propriedade | Tipo  | Descrição |
| --- | --- | --- |
| title | Rich text  | Título do cartão. No máximo 2 linhas.|
| itens | Matriz de itens de lista ||
| Botões | Matriz de objetos de ação | Conjunto de ações aplicáveis ao cartão atual. Máximo 6. |

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

## <a name="office-365-connector-card"></a>cartão conector Office 365

A placa de conector Office 365 é suportada em Teams, não no Bot Framework. Este cartão fornece um layout flexível com várias seções, campos, imagens e ações. Esta placa encapsula uma placa conectora para que possa ser usada por bots. Para obter diferenças entre as placas conectoras e a placa O365, consulte [Notas na placa de conector Office 365](#notes-on-the-office-365-connector-card).

### <a name="support-for-office-365-connector-cards"></a>Suporte para cartões de conectores Office 365

| Bots em Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✔ | ✖ |

### <a name="properties-of-the-office-365-connector-card"></a>Propriedades da placa de conector Office 365

| Propriedade | Tipo  | Descrição |
| --- | --- | --- |
| title | Rich text  | Título do cartão. No máximo 2 linhas. |
| summary | Rich text  | Resumo do cartão. No máximo 2 linhas. |
| texto | Rich text  | O texto aparece na legenda. Para opções de formatação, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md). |
| themeColor | Corda HEX | Cor que substitui o acentoColor fornecido a partir do manifesto de aplicação. |

### <a name="notes-on-the-office-365-connector-card"></a>Notas no cartão de conector Office 365

Office 365 as placas de conectore funcionam corretamente em Microsoft Teams, incluindo [ações do ActionCard](/outlook/actionable-messages/card-reference#actioncard-action).

Uma diferença importante entre o uso de cartões conectores de um conector e o uso de cartões conectores no seu bot é o manuseio de ações de cartão.

* Para um conector, o ponto final recebe a carga útil do cartão através do HTTP POST.
* Para um bot, `HttpPOST` a ação desencadeia uma `invoke` atividade que envia apenas o ID de ação e o corpo para o bot.

Cada placa conectora pode exibir no máximo dez seções, e cada seção pode conter um máximo de cinco imagens e cinco ações.

> [!NOTE]
> Não aparecem seções, imagens ou ações adicionais em uma mensagem.

Todos os campos de texto suportam marcação e HTML. Você pode controlar quais seções usam marcação ou HTML definindo a `markdown` propriedade em uma mensagem. Por padrão, `markdown` está definido como `true` . Se você quiser usar HTML em vez disso, defina `markdown` para `false` .

Se você especificar a `themeColor` propriedade, ela substitui a `accentColor` propriedade no manifesto do aplicativo.

Para especificar o estilo de renderização `activityImage` para , você pode definir o `activityImageType` seguinte:

| Valor | Descrição |
| --- | --- |
| `avatar` | Padrão; `activityImage` é cortado como um círculo. |
| `article` | `activityImage` é exibido como um retângulo e mantém sua proporção. |

Para obter todos os outros detalhes sobre as propriedades do cartão conector, consulte [referência acionável do cartão de mensagem](/outlook/actionable-messages/card-reference). As únicas propriedades de cartão de conector que Microsoft Teams não suportam atualmente são as seguintes:

* `heroImage`
* `hideOriginalBody`
* `startGroup`sempre tratado como `true` em Teams
* `originator`
* `correlationId`

### <a name="example-of-an-office-365-connector-card"></a>Exemplo de uma placa de conector Office 365

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

## <a name="receipt-card"></a>Cartão de recebimento

Teams suporta cartão de recebimento. É um cartão que permite que um bot forneça um recibo ao usuário. Ele normalmente contém a lista de itens a serem incluos no recibo, como impostos e informações totais.

### <a name="support-for-receipt-cards"></a>Suporte para cartões de recebimento

| Bots em Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

### <a name="example-of-a-receipt-card"></a>Exemplo de um cartão de recebimento

![Exemplo de um cartão de recebimento](~/assets/images/cards/receipt.png)

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

### <a name="additional-information-on-receipt-cards"></a>Informações adicionais sobre cartões de recebimento

Referência do Bot Framework:

* [Node.jsdo cartão de recebimento ](/javascript/api/botframework-schema/receiptcard?view=botbuilder-ts-latest&preserve-view=true)
* [Cartão de recebimento C #](/dotnet/api/microsoft.bot.schema.receiptcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="signin-card"></a>Cartão de sinalização

O cartão de sinalização permite que um bot solicite que um usuário faça login. Ele é suportado em Teams de forma ligeiramente diferente do encontrado no Bot Framework. O cartão de sinalização em Teams é semelhante ao cartão de sinalização no Bot Framework, exceto que o cartão de sinalização em Teams só suporta duas ações: `signin` e `openUrl` .

A ação signin pode ser usada a partir de qualquer cartão em Teams, não apenas o cartão de sinalização. Para obter mais informações sobre autenticação, consulte [Microsoft Teams fluxo de autenticação para bots](~/bots/how-to/authentication/auth-flow-bot.md).

### <a name="support-for-signin-cards"></a>Suporte para cartões de sinalização

| Bots em Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✖ | ✖ | ✔ |

### <a name="additional-information-on-signin-cards"></a>Informações adicionais sobre cartões de sinalização

Referência do Bot Framework:

* [Node.jsdo cartão de sinalização ](/javascript/api/botframework-schema/signincard?view=botbuilder-ts-latest&preserve-view=true)
* [Cartão de sinalização C #](/dotnet/api/microsoft.bot.schema.signincard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="thumbnail-card"></a>Cartão de miniatura

Um cartão que normalmente contém uma única imagem em miniatura, um ou mais botões e texto.

### <a name="support-for-thumbnail-cards"></a>Suporte para cartões de miniatura

| Bots em Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

![Exemplo de cartão de miniatura](~/assets/images/cards/thumbnail.png)

### <a name="properties-of-a-thumbnail-card"></a>Propriedades de um cartão de miniatura

| Propriedade | Tipo  | Descrição |
| --- | --- | --- |
| title | Rich text  | Título do cartão. No máximo 2 linhas.|
| subtítulo | Rich text  | Legenda do cartão. No máximo 2 linhas.|
| texto | Rich text  | O texto aparece na legenda. Para opções de formatação, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md). |
| Imagens | Matriz de imagens | Imagem exibida na parte superior do cartão. Proporção 1:1 quadrado. |
| Botões | Matriz de objetos de ação | Conjunto de ações aplicáveis ao cartão atual. Máximo 6. |
| torneira | Objeto Action | Ativado quando o usuário toca no próprio cartão. |

### <a name="example-of-a-thumbnail-card"></a>Exemplo de cartão de miniatura

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

Referência do Bot Framework:

* [cartão de miniatura Node.js](/javascript/api/botframework-schema/thumbnailcard?view=botbuilder-ts-latest&preserve-view=true)
* [Cartão de miniatura C #](/dotnet/api/microsoft.bot.schema.thumbnailcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="card-collections"></a>Coleções de cartões

Teams suporta coleções de cartões.

As coleções de cartões incluem `builder.AttachmentLayout.carousel` e `builder.AttachmentLayout.list` . Essas coleções contêm cartões adaptativos, heróis ou miniaturas.

## <a name="carousel-collection"></a>Coleção carrossel

O [layout do carrossel](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-carousel-of-cards&preserve-view=true) mostra um carrossel de cartões, opcionalmente com botões de ação associados.

### <a name="support-for-carousel-collections"></a>Suporte para coleções de carrossel

| Bots em Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✖ | ✖ | ✔ |

> [!NOTE]
> Um carrossel pode exibir no máximo dez cartões por mensagem.

### <a name="properties-of-a-carousel-card"></a>Propriedades de um cartão de carrossel

As propriedades de um cartão de carrossel são as mesmas do herói e cartões de miniatura.

### <a name="example-of-a-carousel-collection"></a>Exemplo de coleção de carrossel

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

`builder.AttachmentLayoutTypes.Carousel` é a sintaxe para coleções de carrossel.

## <a name="list-collection"></a>Coleção de listas

### <a name="support-for-list-collections"></a>Suporte para coleções de listas

O layout da lista mostra uma lista de cartões empilhadas verticalmente, opcionalmente com botões de ação associados.

| Bots em Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

### <a name="example-of-a-list-collection"></a>Exemplo de uma coleção de listas

![Exemplo de uma lista de cartões](~/assets/images/cards/list.png)

As propriedades são as mesmas do herói ou da miniatura.

Uma lista pode exibir no máximo dez cartões por mensagem.

> [!NOTE]
> Algumas combinações de cartões de lista ainda não são suportadas no iOS e Android.

### <a name="syntax-for-list-collections"></a>Sintaxe para coleções de listas

`builder.AttachmentLayout.list` é a sintaxe para coleções de listas.

## <a name="cards-not-supported-in-teams"></a>Cartões não suportados em Teams

Os seguintes cartões são implementados pelo Bot Framework, mas não são suportados por Teams:

* Cartões de animação
* Cartões de áudio
* Cartões de vídeo
