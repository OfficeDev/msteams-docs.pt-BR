---
title: Tipos de cartões
description: Descreve todas as ações de cartões e cartões disponíveis para bots no Teams
ms.localizationpriority: medium
keywords: referência de cartões bots
ms.topic: reference
ms.openlocfilehash: 47e87ea28a1e003838152cd7f535a23d6861ac6f
ms.sourcegitcommit: e45742fd2aa2ff5e5c15e8f7c20cc14fbef6d441
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2021
ms.locfileid: "61075587"
---
# <a name="types-of-cards"></a>Tipos de cartões

Adaptável, herói, lista, conector Office 365, recibo, entrada e coleções de cartões de miniatura são suportados em bots para Microsoft Teams. Eles são baseados em cartões definidos pela Estrutura de Bot, mas Teams não dá suporte a todos os cartões da Estrutura de Bot e adicionou alguns de seus próprios.

Antes de identificar os diferentes tipos de cartão, entenda como criar um cartão de herói, um cartão em miniatura ou um Cartão Adaptável.

## <a name="create-a-hero-card-thumbnail-card-or-adaptive-card"></a>Criar um cartão de herói, um cartão em miniatura ou um Cartão Adaptável

**Para criar um cartão de herói, um cartão em miniatura ou um Cartão Adaptável do App Studio**

1. Vá para **o App Studio** Teams.
1. Selecione **Editor de cartão**.
1. Selecione **Criar um novo cartão**.
1. Selecione **Criar** para um dos cartões de **Cartão de Herói,** **Cartão de** Miniatura ou **Cartão Adaptável.** Os exemplos de detalhes de metadados, botões e json, csharp e código de nó são mostrados para esse cartão.

    ![Detalhes do cartão de herói](~/assets/images/Cards/Herocarddetails.png)

1. Selecione Enviar este cartão para **mim.** O cartão é enviado como uma mensagem de chat.

## <a name="card-examples"></a>Exemplos de cartão

Você pode encontrar informações adicionais sobre como usar cartões na documentação do SDK do Construtor de Bots v3. Exemplos de código também estão disponíveis no **repositório Microsoft/BotBuilder-Samples** no GitHub. A seguir estão alguns exemplos de cartão:

* .NET
  * [Adicionar cartões como anexos a mensagens](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true).
  * [Código de exemplo de cartões Construtor de bots v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/06.using-cards).

* Node.js
  * [Adicionar cartões como anexos a mensagens](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true).
  * [Código de exemplo de cartões Construtor de bots v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/06.using-cards).

## <a name="card-types"></a>Tipos de cartão

Você pode identificar e usar diferentes tipos de cartões com base nos requisitos do aplicativo. A tabela a seguir mostra os tipos de cartões disponíveis para você:

| Tipo de cartão | Descrição |
| --- | --- |
| [Cartão Adaptável](#adaptive-card) | Esse cartão é altamente personalizável e pode conter qualquer combinação de texto, fala, imagens, botões e campos de entrada. |
| [Cartão de herói](#hero-card) | Esse cartão normalmente contém uma única imagem grande, um ou mais botões e uma pequena quantidade de texto. |
| [Cartão de listagem](#list-card) | Este cartão contém uma lista de rolagem de itens. |
| [Office 365 conector](#office-365-connector-card) | Esse cartão tem um layout flexível com várias seções, campos, imagens e ações. |
| [Cartão de recebimento](#receipt-card) | Este cartão fornece um recibo para o usuário. |
| [Cartão de signin](#signin-card) | Esse cartão permite que um bot solicite que um usuário entre. |
| [Cartão de miniatura](#thumbnail-card) | Esse cartão normalmente contém uma única imagem em miniatura, algum texto curto e um ou mais botões. |
| [Coleções de cartões](#card-collections) | Essa coleção de cartões é usada para retornar vários itens em uma única resposta. |

## <a name="features-that-support-different-card-types"></a>Recursos que suportam diferentes tipos de cartão

| Tipo de cartão | Bots | Visualizações de extensão de mensagem | Resultados da extensão de mensagem | Módulos de tarefas | Webhooks de saída | Webhooks de entrada | Conectores de Office 365 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Cartão Adaptável | ✔ | ✖ | ✔ | ✔ | ✔ | ✔ | ✖ |
| Office 365 conector | ✔ | ✖ | ✔ | ✖ | ✔ | ✔ | ✔ |
| Cartão de herói | ✔ | ✔ | ✔ | ✖ | ✔ | ✔ | ✖ |
| Cartão de miniatura | ✔ | ✔ | ✔ | ✖ | ✔ | ✔ | ✖ |
| Cartão de listagem | ✔ | ✖ | ✖ | ✖ | ✔ | ✔ | ✖ |
| Cartão de recebimento | ✔ | ✖ | ✖ | ✖ | ✖ | ✔ | ✖ |
| Cartão de signin | ✔ | ✖ | ✖ | ✖ | ✖ | ✖ | ✖ |

> [!NOTE]
> Para Cartões Adaptáveis em Webhooks de Entrada, todos os elementos nativos de esquema de Cartão Adaptável, exceto `Action.Submit` , são totalmente suportados. As ações com suporte são [**Action.OpenURL,**](https://adaptivecards.io/explorer/Action.OpenUrl.html) [**Action.ShowCard,**](https://adaptivecards.io/explorer/Action.ShowCard.html) [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html)e [**Action.Execute**](/adaptive-cards/authoring-cards/universal-action-model#actionexecute).

## <a name="common-properties-for-all-cards"></a>Propriedades comuns para todos os cartões

Você pode passar por algumas propriedades comuns que são aplicáveis a todos os cartões.

> [!NOTE]
> Cartões de herói e miniatura com várias ações são automaticamente divididos em vários cartões em um layout de carrossel.

### <a name="inline-card-images"></a>Imagens de cartão em linha

O cartão pode conter uma imagem em linha incluindo um link para a imagem disponível publicamente. Para fins de desempenho, é altamente recomendável hospedar a imagem em uma Rede de Distribuição de Conteúdo pública (CDN).

As imagens são dimensionados para cima ou para baixo em tamanho para manter a taxa de proporção para cobrir a área da imagem. Em seguida, as imagens são cortadas do centro para atingir a proporção apropriada para o cartão.

As imagens devem ter no máximo 1024×1024 e no formato PNG, JPEG ou GIF. Gif animado não é suportado.

A tabela a seguir fornece as propriedades das imagens de cartão em linha:

| Propriedade | Tipo  | Descrição |
| --- | --- | --- |
| url | URL | URL HTTPS para a imagem. |
| alt | Cadeia de caracteres | Descrição acessível da imagem. |

> [!NOTE]
> Se um cartão incluir uma URL de imagem redirecionada antes da imagem final, o redirecionamento na URL da imagem não será suportado. Isso ocorre para imagens compartilhadas na nuvem pública.

### <a name="buttons"></a>Botões

Os botões são mostrados empilhados na parte inferior do cartão. O texto do botão está sempre em uma única linha e é truncado se o texto exceder a largura do botão. Quaisquer botões adicionais além do número máximo suportado pelo cartão não são mostrados.

Para obter mais informações, consulte [ações de cartão](~/task-modules-and-cards/cards/cards-actions.md).

### <a name="card-formatting"></a>Formatação de cartão

Para obter mais informações sobre formatação de texto em cartões, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md).

Depois de identificar as propriedades comuns para todos os cartões, agora você pode trabalhar com Cartões Adaptáveis, que ajudam a aumentar o envolvimento e a eficiência adicionando seu conteúdo a ação diretamente aos aplicativos que você usa.

## <a name="adaptive-card"></a>Cartão Adaptável

Um Cartão Adaptável é um cartão personalizável que pode conter qualquer combinação de texto, fala, imagens, botões e campos de entrada. Para obter mais informações, consulte [Adaptive Cards](https://github.com/microsoft/AdaptiveCards/releases/tag/2020.07).

### <a name="support-for-adaptive-cards"></a>Suporte para cartões adaptáveis

A tabela a seguir fornece os recursos que suportam Cartões Adaptáveis:

| Bots em Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

> [!NOTE]
> * Teams plataforma suporta v1.4 ou anterior dos recursos de Cartão Adaptável para cartões enviados por bot e extensões de mensagens baseadas em ação.
> * Teams plataforma suporta v1.3 ou anterior de recursos de Cartão Adaptável para outros recursos, como cartões enviados pelo usuário (extensões de mensagens baseadas em pesquisa e vinculação de link), guias e módulos de tarefa.
> * O estilo de ação positivo ou destrutivo não é suportado em Cartões Adaptáveis na Teams plataforma.
> * No momento, os elementos de mídia não têm suporte no Cartão Adaptável na Teams plataforma.

### <a name="example-of-adaptive-card"></a>Exemplo de cartão adaptável

![Exemplo de um cartão adaptável](~/assets/images/cards/adaptivecard.png)

O código a seguir mostra um exemplo de um Cartão Adaptável:

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

Referência da Estrutura de Bot:

* [Nó de cartões adaptáveis](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true)
* [Cartão Adaptável C #](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true)

Agora você pode trabalhar com um cartão de herói, que é um cartão multiuso usado para realçar visualmente uma seleção de usuário potencial.

## <a name="hero-card"></a>Cartão de herói

Um cartão que normalmente contém uma única imagem grande, um ou mais botões e texto.

### <a name="support-for-hero-cards"></a>Suporte para cartões de herói

A tabela a seguir fornece os recursos que suportam cartões de herói:

| Bots em Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

### <a name="properties-of-a-hero-card"></a>Propriedades de um cartão de herói

A tabela a seguir fornece as propriedades de um cartão de herói:

| Propriedade | Tipo  | Descrição |
| --- | --- | --- |
| title | Rich text  | Título do cartão. Máximo de duas linhas. |
| subtitle | Rich text  | Legenda do cartão. Máximo de duas linhas.|
| texto | Rich text  | O texto aparece sob o subtítulo. Para opções de formatação, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md). |
| images | Matriz de imagens | Imagem exibida na parte superior do cartão. Taxa de proporção 16:9. |
| botões | Matriz de objetos de ação | Conjunto de ações aplicáveis ao cartão atual. Máximo de seis. |
| tap | Objeto Action | Ativado quando o usuário toca no próprio cartão. |

### <a name="example-of-a-hero-card"></a>Exemplo de um cartão de herói

![Exemplo de um cartão de herói](~/assets/images/cards/hero.png)

O código a seguir mostra um exemplo de um cartão de herói:

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

* [Cartão de herói Node.js](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-a-hero-card&preserve-view=true)
* [Cartão de herói C #](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-hero-card&preserve-view=true)

## <a name="list-card"></a>Cartão de listagem

O cartão de lista foi adicionado por Teams para fornecer funções além do que a coleção de listas pode fornecer. O cartão de listagem fornece uma lista de rolagem de itens.

### <a name="support-for-list-cards"></a>Suporte para cartões de lista

A tabela a seguir fornece os recursos que suportam cartões de lista:

| Bots em Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✖ | ✖ |✔ |

### <a name="properties-of-a-list-card"></a>Propriedades de um cartão de listagem

A tabela a seguir fornece as propriedades de um cartão de listagem:

| Propriedade | Tipo  | Descrição |
| --- | --- | --- |
| title | Rich text  | Título do cartão. Máximo de 2 linhas.|
| items | Matriz de itens de lista | Conjunto de itens aplicáveis ao cartão.|
| botões | Matriz de objetos de ação | Conjunto de ações aplicáveis ao cartão atual. Máximo 6. |

### <a name="example-of-a-list-card"></a>Exemplo de um cartão de lista

O código a seguir mostra um exemplo de um cartão de lista:

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

## <a name="office-365-connector-card"></a>Office 365 conector

Você pode trabalhar com um cartão Office 365 Conector que fornece um layout flexível e é uma ótima maneira de obter informações úteis. O Office 365 conector de usuário é compatível com Teams, não na Estrutura de Bot. Este cartão fornece um layout flexível com várias seções, campos, imagens e ações. Esse cartão contém um cartão conector para que possa ser usado por bots. Para obter diferenças entre cartões de conector e o cartão Office 365 conector, consulte Informações adicionais [sobre o cartão Office 365 Connector.](#additional-information-on-the-office-365-connector-card)

### <a name="support-for-office-365-connector-cards"></a>Suporte para cartões Office 365 Conector

A tabela a seguir fornece os recursos que suportam Office 365 conectores:

| Bots em Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✔ | ✖ |

### <a name="properties-of-the-office-365-connector-card"></a>Propriedades do cartão Office 365 conector

A tabela a seguir fornece as propriedades do cartão Office 365 conector:

| Propriedade | Tipo  | Descrição |
| --- | --- | --- |
| title | Rich text  | Título do cartão. Máximo de duas linhas. |
| summary | Rich text  | Resumo do cartão. Máximo de duas linhas. |
| texto | Rich text  | O texto aparece sob o subtítulo. Para opções de formatação, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md). |
| themeColor | Cadeia de caracteres HEX | Cor que substitui o `accentColor` fornecido do manifesto do aplicativo. |

### <a name="additional-information-on-the-office-365-connector-card"></a>Informações adicionais sobre o cartão Office 365 conector

Office 365 conectores funcionam corretamente no Microsoft Teams, incluindo [ `ActionCard` ações](/outlook/actionable-messages/card-reference#actioncard-action).

A diferença importante entre o uso de cartões de conector de um conector e o uso de cartões de conector no bot é o tratamento de ações de cartão. A tabela a seguir lista a diferença:

| Connector | Bot |
| --- | --- |
| O ponto de extremidade recebe a carga de cartão por meio de HTTP POST. | A ação dispara uma atividade que envia apenas a ID de ação `HttpPOST` e o corpo para o `invoke` bot.|

Cada cartão de conector pode exibir no máximo dez seções, e cada seção pode conter no máximo cinco imagens e cinco ações.

> [!NOTE]
> Quaisquer seções, imagens ou ações adicionais em uma mensagem não são exibidas.

Todos os campos de texto suportam Markdown e HTML. Você pode controlar quais seções usam Markdown ou HTML definindo `markdown` a propriedade em uma mensagem. Por padrão, `markdown` é definido como `true` . Se você quiser usar HTML em vez disso, de definir `markdown` como `false` .

Se você especificar a `themeColor` propriedade, ela substituirá `accentColor` a propriedade no manifesto do aplicativo.

Para especificar o estilo de renderização `activityImage` para , você pode definir como mostrado na tabela a `activityImageType` seguir:

| Valor | Descrição |
| --- | --- |
| `avatar` | Padrão, `activityImage` é cortada como um círculo. |
| `article` | `activityImage` é exibido como um retângulo e mantém sua taxa de proporção. |

Para obter todos os outros detalhes sobre as propriedades do cartão do conector, consulte referência de cartão de mensagem a [ação.](/outlook/actionable-messages/card-reference) As únicas propriedades de cartão de conector que Teams atualmente não suportam são as seguinte:

* `heroImage`
* `hideOriginalBody`
* `startGroup`sempre tratado como `true` em Teams
* `originator`
* `correlationId`

### <a name="example-of-an-office-365-connector-card"></a>Exemplo de um cartão Office 365 conector

O código a seguir mostra um exemplo de um cartão Office 365 Connector:

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

Teams dá suporte ao cartão de recebimento. É um cartão que permite que um bot forneça um recibo ao usuário. Normalmente, ele contém a lista de itens a ser incluídos no recibo, como informações fiscais e totais.

### <a name="support-for-receipt-cards"></a>Suporte para cartões de recebimento

A tabela a seguir fornece os recursos que suportam cartões de recebimento:

| Bots em Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

### <a name="example-of-a-receipt-card"></a>Exemplo de um cartão de confirmação

![Exemplo de um cartão de confirmação](~/assets/images/cards/receipt.png)

O código a seguir mostra um exemplo de um cartão de recebimento:

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

Referência da Estrutura de Bot:

* [Cartão de Node.js](/javascript/api/botframework-schema/receiptcard?view=botbuilder-ts-latest&preserve-view=true)
* [Cartão de recebimento C #](/dotnet/api/microsoft.bot.schema.receiptcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="signin-card"></a>Cartão de signin

O cartão de Teams é semelhante ao cartão de assinatura na Estrutura de Bot, exceto que o cartão de signin no Teams suporta apenas duas ações `signin` e `openUrl` .

A ação de signin pode ser usada de qualquer cartão Teams, não apenas o cartão de assinatura. Para obter mais informações, [consulte Teams fluxo de autenticação para bots](~/bots/how-to/authentication/auth-flow-bot.md).

### <a name="support-for-signin-cards"></a>Suporte para cartões de assinatura

A tabela a seguir fornece os recursos que suportam cartões de assinatura:

| Bots em Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✖ | ✖ | ✔ |

### <a name="additional-information-on-signin-cards"></a>Informações adicionais sobre cartões de assinatura

Referência da Estrutura de Bot:

* [Cartão de Node.js](/javascript/api/botframework-schema/signincard?view=botbuilder-ts-latest&preserve-view=true)
* [Signin card C #](/dotnet/api/microsoft.bot.schema.signincard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="thumbnail-card"></a>Cartão de miniatura

Você pode trabalhar com um cartão de miniatura que é usado para enviar uma mensagem a ação simples. Um cartão que normalmente contém uma única imagem em miniatura, um ou mais botões e texto.

### <a name="support-for-thumbnail-cards"></a>Suporte para cartões de miniatura

A tabela a seguir fornece os recursos que suportam cartões de miniatura:

| Bots em Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

![Exemplo de um cartão de miniatura](~/assets/images/cards/thumbnail.png)

### <a name="properties-of-a-thumbnail-card"></a>Propriedades de um cartão de miniatura

A tabela a seguir fornece as propriedades de um cartão de miniatura:

| Propriedade | Tipo  | Descrição |
| --- | --- | --- |
| title | Rich text  | Título do cartão. Máximo de 2 linhas.|
| subtitle | Rich text  | Legenda do cartão. Máximo de 2 linhas.|
| texto | Rich text  | O texto aparece sob o subtítulo. Para opções de formatação, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md). |
| images | Matriz de imagens | Imagem exibida na parte superior do cartão. Taxa de proporção 1:1 quadrado. |
| botões | Matriz de objetos de ação | Conjunto de ações aplicáveis ao cartão atual. Máximo 6. |
| tap | Objeto Action | Ativado quando o usuário toca no próprio cartão. |

### <a name="example-of-a-thumbnail-card"></a>Exemplo de um cartão de miniatura

O código a seguir mostra um exemplo de um cartão de miniatura:

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

* [Cartão de miniatura Node.js](/javascript/api/botframework-schema/thumbnailcard?view=botbuilder-ts-latest&preserve-view=true)
* [Cartão de miniatura C #](/dotnet/api/microsoft.bot.schema.thumbnailcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="card-collections"></a>Coleções de cartões

Você pode trabalhar com coleções de cartões que incluem carrossel e coleções de lista. Teams dá suporte a coleções de cartões. As coleções de cartões `builder.AttachmentLayout.carousel` incluem `builder.AttachmentLayout.list` e . Essas coleções contêm cartões adaptáveis, herois ou miniaturas.

### <a name="carousel-collection"></a>Coleção Carousel

O [layout do carrossel](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-carousel-of-cards&preserve-view=true) mostra um carrossel de cartões, opcionalmente com botões de ação associados.

#### <a name="support-for-carousel-collections"></a>Suporte para coleções de carrossel

A tabela a seguir fornece os recursos que suportam coleções de carrossel:

| Bots em Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✖ | ✖ | ✔ |

> [!NOTE]
> Um carrossel pode exibir no máximo dez cartões por mensagem.

#### <a name="properties-of-a-carousel-card"></a>Propriedades de um cartão de carrossel

As propriedades de um cartão de carrossel são as mesmas que as de herói e miniatura.

#### <a name="example-of-a-carousel-collection"></a>Exemplo de uma coleção de carrossel

![Exemplo de um carrossel de cartões](~/assets/images/cards/carousel.png)

O código a seguir mostra um exemplo de uma coleção de carrossel:

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

#### <a name="syntax-for-carousel-collections"></a>Sintaxe para coleções de carrossel

`builder.AttachmentLayoutTypes.Carousel` é a sintaxe para coleções de carrossel.

### <a name="list-collection"></a>Coleção List

O layout da lista mostra uma lista verticalmente empilhada de cartões, opcionalmente com botões de ação associados.

#### <a name="support-for-list-collections"></a>Suporte para coleções de lista

A tabela a seguir fornece os recursos que suportam coleções de lista:

| Bots em Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

#### <a name="example-of-a-list-collection"></a>Exemplo de uma coleção de listas

![Exemplo de uma lista de cartões](~/assets/images/cards/list.png)

As propriedades das coleções de lista são as mesmas que os cartões de miniatura ou herói.

Uma lista pode exibir no máximo dez cartões por mensagem.

> [!NOTE]
> Algumas combinações de cartões de lista ainda não são suportadas no iOS e no Android.

#### <a name="syntax-for-list-collections"></a>Sintaxe para coleções de lista

`builder.AttachmentLayout.list` é a sintaxe para coleções de lista.

## <a name="cards-not-supported-in-teams"></a>Cartões não suportados em Teams

Os cartões a seguir são implementados pela Estrutura de Bot, mas não são suportados por Teams:

* Cartões de animação
* Cartões de áudio
* Cartões de vídeo

## <a name="see-also"></a>Confira também

* [Módulos de tarefas](~/task-modules-and-cards/what-are-task-modules.md)
* [Formatar cartões](~/task-modules-and-cards/cards/cards-format.md)
* [Cartões atualizados](~/task-modules-and-cards/cards/universal-actions-for-adaptive-cards/up-to-date-views.md)
* [Trabalhar com Ações Universais para Cartões Adaptáveis](~/task-modules-and-cards/cards/universal-actions-for-adaptive-cards/work-with-universal-actions-for-adaptive-cards.md)
