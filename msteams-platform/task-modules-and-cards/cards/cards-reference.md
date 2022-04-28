---
title: Tipos de cartões
description: Descreve todos os cartões e ações de cartão disponíveis para bots no Teams
ms.localizationpriority: high
keywords: referência de cartões de bots
ms.topic: reference
ms.openlocfilehash: b1dd6d5c9ac388f1862041df836f5590d57bfe84
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65104137"
---
# <a name="types-of-cards"></a>Tipos de cartões

Cartões adaptáveis, hero, lista, Conector do Office 365, recibo, entrada e cartões de miniatura e coleções de cartões são compatíveis com bots para o Microsoft Teams. Eles são baseados em cartões definidos pelo Bot Framework, mas o Teams não dá suporte a todos os Bot Framework e adicionou alguns de seus próprios cartões.

Antes de identificar os diferentes tipos de cartão, entenda como criar um cartão hero, um cartão em miniatura ou um Cartão Adaptável.

## <a name="create-a-hero-card-thumbnail-card-or-adaptive-card"></a>Criar um cartão hero, um cartão em miniatura ou um Cartão Adaptável

Para criar um cartão de destaque, cartão de miniatura ou Cartão Adaptável do App Studio:

1. Acesse o **App Studio** do Teams.
1. Selecione **Editor de cartão**.
1. Selecione **Criar um novo cartão**.
1. Selecione **Criar** para um dos cartões entre **Cartão Hero**, **Cartão de miniatura** ou **Cartão Adaptável**. Os detalhes de metadados, botões e exemplos de código json, csharp e nó são mostrados para esse cartão.

    :::image type="content" source="../../assets/images/Cards/Herocarddetails.png" alt-text="Detalhes do cartão Hero":::

1. Selecione **Me envie este cartão**. O cartão é enviado para você como uma mensagem de chat.

## <a name="card-examples"></a>Exemplos de cartão

Você pode encontrar informações adicionais sobre como usar cartões na documentação do Bot Builder SDK v3. Exemplos de código também estão disponíveis no repositório **Microsoft/BotBuilder-Samples** no GitHub. A seguir estão alguns exemplos de cartão:

* .NET
  * [Adicionar cartões como anexos a mensagens](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true).
  * [Código de exemplo de cartões Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/06.using-cards).

* Node.js
  * [Adicionar cartões como anexos a mensagens](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true).
  * [Código de exemplo de cartões Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/06.using-cards).

## <a name="card-types"></a>Tipos de cartão

Você pode identificar e usar diferentes tipos de cartões com base nos requisitos do aplicativo. A tabela a seguir mostra os tipos de cartões disponíveis para você:

| Tipo de cartão | Descrição |
| --- | --- |
| [Cartão Adaptável](#adaptive-card) | Esse cartão é altamente personalizável e pode conter qualquer combinação de texto, fala, imagens, botões e campos de entrada. |
| [cartão Hero](#hero-card) | Esse cartão normalmente contém uma única imagem grande, um ou mais botões e uma pequena quantidade de texto. |
| [cartão de Lista](#list-card) | Este cartão contém uma lista de rolagem de itens. |
| [cartão do Conector do Office 365](#office-365-connector-card) | Este cartão tem um layout flexível com várias seções, campos, imagens e ações. |
| [cartão de Recibo](#receipt-card) | Este cartão fornece um recibo para o usuário. |
| [cartão de Entrada](#signin-card) | Esse cartão permite que um bot solicite que um usuário entre. |
| [cartão de Miniatura](#thumbnail-card) | Esse cartão normalmente contém uma única imagem em miniatura, algum texto curto e um ou mais botões. |
| [Coleções de cartões](#card-collections) | Essa coleção de cartões é usada para retornar vários itens em uma única resposta. |

## <a name="features-that-support-different-card-types"></a>Recursos que dão suporte a diferentes tipos de cartão

| Tipo de cartão | Bots | Visualizações da extensão de mensagem | Resultados da extensão de mensagem | Módulos de tarefas | Webhooks de saída | Webhooks de entrada | Conectores de Office 365 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Cartão Adaptável | ✔ | ✖ | ✔ | ✔ | ✔ | ✔ | ✖ |
| Cartão do Conector do Office 365 | ✔ | ✖ | ✔ | ✖ | ✔ | ✔ | ✔ |
| Cartão Hero | ✔ | ✔ | ✔ | ✖ | ✔ | ✔ | ✖ |
| Cartão em miniatura | ✔ | ✔ | ✔ | ✖ | ✔ | ✔ | ✖ |
| Cartão de lista | ✔ | ✖ | ✖ | ✖ | ✔ | ✔ | ✖ |
| Cartão de recibo | ✔ | ✖ | ✖ | ✖ | ✖ | ✔ | ✖ |
| Cartão de entrada | ✔ | ✖ | ✖ | ✖ | ✖ | ✖ | ✖ |

> [!NOTE]
> Para Cartões Adaptáveis em Webhooks de Entrada, todos os elementos nativos de esquema de Cartão Adaptável, exceto `Action.Submit`, têm suporte total. As ações com suporte [**Action.OpenURL**](https://adaptivecards.io/explorer/Action.OpenUrl.html), [**Action.ShowCard**](https://adaptivecards.io/explorer/Action.ShowCard.html), [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html), e [**Action.Execute**](/adaptive-cards/authoring-cards/universal-action-model#actionexecute).

## <a name="common-properties-for-all-cards"></a>Propriedades comuns para todos os cartões

Você pode percorrer algumas propriedades comuns que são aplicáveis a todos os cartões.

> [!NOTE]
> Cartões hero e miniaturas com várias ações são divididos automaticamente em vários cartões em um layout de carrossel.

### <a name="inline-card-images"></a>Imagens de cartão embutidas

O cartão pode conter uma imagem embutida, incluindo um link para a imagem disponível publicamente. Para fins de desempenho, é altamente recomendável hospedar a imagem em uma CDN (Rede de Distribuição de Conteúdo) pública.

As imagens são dimensionadas para cima ou para baixo para manter a taxa de proporção para cobrir a área da imagem. As imagens são cortadas do centro para obter a taxa de proporção apropriada para o cartão.

As imagens devem ter no máximo 1024×1024 e no formato PNG, JPEG ou GIF. GIF animado não é suportado.

A tabela a seguir fornece as propriedades de imagens de cartão embutidas:

| Propriedade | Tipo  | Descrição |
| --- | --- | --- |
| url | URL | URL HTTPS para a imagem. |
| alt | Cadeia de caracteres | Descrição acessível da imagem. |

> [!NOTE]
> Se um cartão incluir um URL de imagem que é redirecionado antes da imagem final, o redirecionamento no URL da imagem não será suportado. Isso ocorre em imagens compartilhadas na nuvem pública.

### <a name="buttons"></a>Botões

Os botões são mostrados empilhados na parte inferior do cartão. O texto do botão estará sempre em uma única linha e será truncado se o texto exceder a largura do botão. Os botões adicionais além do número máximo suportado pelo cartão não são mostrados.

Para obter mais informações, consulte [ações de cartão](~/task-modules-and-cards/cards/cards-actions.md).

### <a name="card-formatting"></a>Formatação de cartão

Para obter mais informações sobre formatação de texto em cartões, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md).

Depois de identificar as propriedades comuns de todos os cartões, agora você pode trabalhar com o Cartões Adaptáveis, o que ajuda a aumentar o envolvimento e a eficiência adicionando seu conteúdo acionável diretamente aos aplicativos que você usa.

## <a name="adaptive-card"></a>Cartão Adaptável

Um Cartão Adaptável é um cartão personalizável que pode conter qualquer combinação de texto, fala, imagens, botões e campos de entrada. Para obter mais informações, consulte [Cartões Adaptável](https://github.com/microsoft/AdaptiveCards/releases/tag/2020.07).

### <a name="support-for-adaptive-cards"></a>Suporte para Cartões Adaptáveis

A tabela a seguir fornece os recursos que dão suporte Cartões Adaptáveis:

| Bots no Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

> [!NOTE]
>
> * A plataforma Teams dá suporte à v1.4 ou anterior aos recursos do Cartão Adaptável para cartões enviados por bot e extensões de mensagens baseadas em ação.
> * A plataforma Teams dá suporte à v1.3 ou anterior aos recursos do Cartão Adaptável para outras capacidades, tais como cartões enviados pelo usuário (extensões de mensagens baseadas em pesquisa e abertura de link), guias e módulos de tarefa.
> * Não há suporte para o estilo de ação positiva ou destrutiva Cartões Adaptáveis na plataforma do Teams.
> * No momento, não há suporte para elementos de mídia no Cartão Adaptável na plataforma do Teams.

### <a name="example-of-adaptive-card"></a>Exemplo de cartão adaptável

:::image type="content" source="~/assets/images/cards/adaptivecard.png" alt-text="Exemplo de um cartão adaptável" border="true":::

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

#### <a name="additional-information-on-adaptive-cards"></a>Informações adicionais sobre Cartões Adaptáveis

Você pode passar valores dinâmicos em um Cartão Adaptável usando o símbolo do dólar ($) e chavetas.Para mais informações, consulte [Modelos de Cartões Adaptáveis](/adaptive-cards/templating/).

Exemplo:

```json
{ 
 "type": "TextBlock",
 "text": "${titleText}",
 "size": "default",
 "weight": "bolder"
}

```

Referência do Bot Framework:

* [Nó de Cartões Adaptáveis](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true)
* [C# de Cartão Adaptável](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true)

Para saber mais sobre Cartões Adaptáveis, consulte [Cartões Adaptáveis](/adaptive-cards/).

Agora você pode trabalhar com um cartão hero, que é um cartão multiuso usado para realçar visualmente uma seleção de usuário potencial.

## <a name="hero-card"></a>Cartão Hero

Um cartão que normalmente contém uma única imagem grande, um ou mais botões e texto.

### <a name="support-for-hero-cards"></a>Suporte para cartões hero

A tabela a seguir fornece os recursos que dão suporte a cartões hero:

| Bots no Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

### <a name="properties-of-a-hero-card"></a>Propriedades de um cartão hero

A tabela a seguir fornece as propriedades de um cartão hero:

| Propriedade | Tipo  | Descrição |
| --- | --- | --- |
| title | Rich text  | Título do cartão. Máximo de duas linhas. |
| subtítulo | Rich text  | Subtítulo do cartão. Máximo de duas linhas.|
| texto | Rich text  | O texto aparece sob o subtítulo. Para opções de formatação, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md). |
| imagens | Matriz de imagens | Imagem exibida na parte superior do cartão. Taxa de proporção 16:9. |
| botões | Matriz de objetos de ação | Conjunto de ações aplicáveis ao cartão atual. No máximo seis. |
| Torneira | Objeto Action | Ativado quando o usuário toca no próprio cartão. |

### <a name="example-of-a-hero-card"></a>Exemplo de um cartão hero

:::image type="content" source="../../assets/images/Cards/hero.png" alt-text="cartão Hero":::

O código a seguir mostra um exemplo de um cartão hero:

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

### <a name="additional-information-on-hero-cards"></a>Informações adicionais sobre cartões hero

Referência do Bot Framework:

* [Node.js do Cartão Hero](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-a-hero-card&preserve-view=true)
* [C# do Cartão Hero](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-hero-card&preserve-view=true)

## <a name="list-card"></a>Cartão de lista

O cartão de lista foi adicionado pelo Teams para fornecer funções além do que a coleção de listas pode fornecer. O cartão de lista fornece uma lista de rolagem de itens.

### <a name="support-for-list-cards"></a>Suporte para cartões de lista

A tabela a seguir fornece os recursos que dão suporte a cartões de lista:

| Bots no Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✖ | ✖ |✔ |

### <a name="properties-of-a-list-card"></a>Propriedades de um cartão de lista

A tabela a seguir fornece as propriedades de um cartão de lista:

| Propriedade | Tipo  | Descrição |
| --- | --- | --- |
| title | Rich text  | Título do cartão. Máximo de 2 linhas.|
| items | Matriz de itens de lista | Conjunto de itens aplicáveis ao cartão.|
| botões | Matriz de objetos de ação | Conjunto de ações aplicáveis ao cartão atual. No máximo 6. |

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

## <a name="office-365-connector-card"></a>Cartão do conector do Office 365

Você pode trabalhar com um cartão do Conector do Office 365 que fornece um layout flexível e é uma ótima maneira de obter informações úteis. O cartão do conector do Office 365 tem suporte no Teams, não no Bot Framework. Esse cartão fornece um layout flexível com várias seções, campos, imagens e ações. Esse cartão contém um cartão de conector para que possa ser usado por bots. Para obter diferenças entre os cartões conectores e o cartão do Conector do Office 365, consulte [Informações adicionais sobre o cartão conector do Office 365](#additional-information-on-the-office-365-connector-card).

### <a name="support-for-office-365-connector-cards"></a>Suporte para cartões do Conector do Office 365

A tabela a seguir fornece os recursos que dão suporte a cartões do Conector do Office 365:

| Bots no Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✔ | ✖ |

### <a name="properties-of-the-office-365-connector-card"></a>Propriedades do cartão do Conector do Office 365

A tabela a seguir fornece as propriedades do cartão do conector do Office 365:

| Propriedade | Tipo  | Descrição |
| --- | --- | --- |
| title | Rich text  | Título do cartão. Máximo de duas linhas. |
| summary | Rich text  | Resumo do cartão. Máximo de duas linhas. |
| texto | Rich text  | O texto aparece sob o subtítulo. Para opções de formatação, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md). |
| themeColor | Cadeia de caracteres HEX | Cor que substitui o `accentColor` fornecido do manifesto do aplicativo. |

### <a name="additional-information-on-the-office-365-connector-card"></a>Informações adicionais sobre o cartão do Conector do Office 365

Os cartões do Conector do Office 365 funcionam corretamente no Microsoft Teams, incluindo [`ActionCard`ações](/outlook/actionable-messages/card-reference#actioncard-action).

A diferença importante entre usar cartões conectores de um conector e usar cartões conectores no seu bot é o tratamento das ações do cartão. A tabela a seguir lista a diferença:

| Connector | Bot |
| --- | --- |
| O ponto de extremidade recebe a carga do cartão por meio de HTTP POST. | A ação `HttpPOST` dispara uma atividade `invoke` que envia apenas a ID de ação e o corpo para o bot.|

Cada cartão conector pode exibir no máximo dez seções, e cada seção pode conter no máximo cinco imagens e cinco ações.

> [!NOTE]
> Quaisquer seções, imagens ou ações adicionais em uma mensagem não aparecem.

Todos os campos de texto dão suporte a Markdown e HTML. Você pode controlar quais seções usam Markdown ou HTML definindo a propriedade `markdown` em uma mensagem. Por padrão, `markdown` é definido como `true`. Se você quiser usar HTML, defina `markdown` como `false`.

Se você especificar a propriedade `themeColor`, ele substituirá a propriedade `accentColor` no manifesto do aplicativo.

Para especificar o estilo de renderização para `activityImage`, você pode definir `activityImageType` como mostrado na tabela a seguir:

| Valor | Descrição |
| --- | --- |
| `avatar` | Padrão, `activityImage` é cortada como um círculo. |
| `article` | `activityImage` é exibido como um retângulo e mantém sua taxa de proporção. |

Para obter todos os outros detalhes sobre as propriedades do cartão do conector, consulte [referência de cartão de mensagem acionável](/outlook/actionable-messages/card-reference). As únicas propriedades de cartão de conector que o Teams não dá suporte no momento são as seguintes:

* `heroImage`
* `hideOriginalBody`
* `startGroup` sempre é tratado como `true` no Teams
* `originator`
* `correlationId`

### <a name="example-of-an-office-365-connector-card"></a>Exemplo de um cartão do Conector do Office 365

O código a seguir mostra um exemplo de um cartão do Conector do Office 365:

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

O Teams dá suporte ao cartão de confirmação. É um cartão que permite que um bot forneça um recibo ao usuário. Normalmente, ele contém a lista de itens a serem incluídos no recibo, como informações fiscais e totais.

### <a name="support-for-receipt-cards"></a>Suporte para cartões de recibo

A tabela a seguir fornece os recursos que dão suporte a cartões de recibo:

| Bots no Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

### <a name="example-of-a-receipt-card"></a>Exemplo de um cartão de confirmação

:::image type="content" source="../../assets/images/Cards/receipt.png" alt-text="Cartão de recibo":::

O código a seguir mostra um exemplo de um cartão de recibo:

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

### <a name="additional-information-on-receipt-cards"></a>Informações adicionais sobre cartões de recibo

Referência do Bot Framework:

* [Node.js do Cartão de recibo](/javascript/api/botframework-schema/receiptcard?view=botbuilder-ts-latest&preserve-view=true)
* [C# do Cartão de recibo](/dotnet/api/microsoft.bot.schema.receiptcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="signin-card"></a>Cartão de entrada

O cartão de entrada no Teams é semelhante ao cartão de entrada no Bot Framework exceto que o cartão de entrada no Teams dá suporte apenas a duas ações `signin` e `openUrl`.

A ação de entrada pode ser usada em qualquer cartão no Teams, não apenas no cartão de entrada. Para obter mais informações, consulte [Fluxo de autenticação do Teams para bots](~/bots/how-to/authentication/auth-flow-bot.md).

### <a name="support-for-signin-cards"></a>Suporte para cartões de entrada

A tabela a seguir fornece os recursos que dão suporte a cartões de entrada:

| Bots no Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✖ | ✖ | ✔ |

### <a name="additional-information-on-signin-cards"></a>Informações adicionais sobre cartões de entrada

Referência do Bot Framework:

* [Node.js do Cartão de entrada](/javascript/api/botframework-schema/signincard?view=botbuilder-ts-latest&preserve-view=true)
* [C# do Cartão de entrada](/dotnet/api/microsoft.bot.schema.signincard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="thumbnail-card"></a>Cartão em miniatura

Você pode trabalhar com um cartão em miniatura usado para enviar uma mensagem acionável simples. Um cartão que normalmente contém uma única imagem em miniatura, um ou mais botões e texto.

### <a name="support-for-thumbnail-cards"></a>Suporte para cartões em miniatura

A tabela a seguir fornece os recursos que dão suporte a cartões em miniatura:

| Bots no Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

:::image type="content" source="../../assets/images/Cards/thumbnail.png" alt-text="Cartão de miniatura":::

### <a name="properties-of-a-thumbnail-card"></a>Propriedades de um cartão em miniatura

A tabela a seguir fornece as propriedades de um cartão em miniatura:

| Propriedade | Tipo  | Descrição |
| --- | --- | --- |
| title | Rich text  | Título do cartão. Máximo de 2 linhas.|
| subtítulo | Rich text  | Subtítulo do cartão. Máximo de 2 linhas.|
| texto | Rich text  | O texto aparece sob o subtítulo. Para opções de formatação, consulte [formatação de cartão](~/task-modules-and-cards/cards/cards-format.md). |
| imagens | Matriz de imagens | Imagem exibida na parte superior do cartão. Taxa de proporção 1:1 quadrado. |
| botões | Matriz de objetos de ação | Conjunto de ações aplicáveis ao cartão atual. No máximo 6. |
| Torneira | Objeto Action | Ativado quando o usuário toca no próprio cartão. |

### <a name="example-of-a-thumbnail-card"></a>Exemplo de um cartão em miniatura

O código a seguir mostra um exemplo de um cartão em miniatura:

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

* [Node.js do Cartão de miniatura](/javascript/api/botframework-schema/thumbnailcard?view=botbuilder-ts-latest&preserve-view=true)
* [C# do Cartão de miniatura](/dotnet/api/microsoft.bot.schema.thumbnailcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="card-collections"></a>Coleções de cartões

Você pode trabalhar com coleções de cartões que incluem coleções de carrossel e listas. O Teams dá suporte a coleções de cartões. As coleções de cartões incluem `builder.AttachmentLayout.carousel` e `builder.AttachmentLayout.list`. Essas coleções contêm cartões adaptáveis, hero ou miniatura.

### <a name="carousel-collection"></a>Coleção de carrossel

O [layout de carrossel](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-carousel-of-cards&preserve-view=true) mostra um carrossel de cartões, opcionalmente com botões de ação associados.

#### <a name="support-for-carousel-collections"></a>Suporte para coleções de carrossel

A tabela a seguir fornece os recursos que dão suporte a coleções de carrossel:

| Bots no Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✖ | ✖ | ✔ |

> [!NOTE]
> Um carrossel pode exibir no máximo dez cartões por mensagem.

#### <a name="properties-of-a-carousel-card"></a>Propriedades de um cartão de carrossel

As propriedades de um cartão de carrossel são as mesmas dos cartões hero e miniatura.

#### <a name="example-of-a-carousel-collection"></a>Exemplo de uma coleção de carrossel

:::image type="content" source="../../assets/images/Cards/carousel.png" alt-text="Coleção de carrossel":::

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

### <a name="list-collection"></a>Listar coleção

O layout da lista mostra uma lista de cartões empilhados verticalmente, opcionalmente com botões de ação associados.

#### <a name="support-for-list-collections"></a>Suporte para coleções de listas

A tabela a seguir fornece os recursos que dão suporte a coleções de listas:

| Bots no Teams | Extensões de mensagens  | Conectores | Bot Framework |
| --- | --- | --- | --- |
| ✔ | ✔ | ✖ | ✔ |

#### <a name="example-of-a-list-collection"></a>Exemplo de uma coleção de listas

:::image type="content" source="../../assets/images/Cards/list.png" alt-text="Listar coleção":::

As propriedades das coleções de listas são as mesmas que os cartões hero ou miniatura.

Uma lista pode exibir no máximo dez cartões por mensagem.

> [!NOTE]
> Algumas combinações de cartões de lista ainda não têm suporte no iOS e no Android.

#### <a name="syntax-for-list-collections"></a>Sintaxe para coleções de listas

`builder.AttachmentLayout.list` é a sintaxe para coleções de listas.

## <a name="cards-not-supported-in-teams"></a>Cartões sem suporte no Teams

Os cartões a seguir são implementados pelo Bot Framework, mas não têm suporte do Teams:

* Cartões de animação
* Cartões de áudio
* Placas de vídeo

## <a name="see-also"></a>Confira também

* [Módulos de tarefas](~/task-modules-and-cards/what-are-task-modules.md)
* [Formatar cartões](~/task-modules-and-cards/cards/cards-format.md)
* [Cartões atualizados](~/task-modules-and-cards/cards/universal-actions-for-adaptive-cards/up-to-date-views.md)
* [Trabalhar com Ações Universais para Cartões Adaptáveis](~/task-modules-and-cards/cards/universal-actions-for-adaptive-cards/work-with-universal-actions-for-adaptive-cards.md)
* [Comentários de preenchimento do formulário](~/bots/how-to/conversations/conversation-messages.md#form-completion-feedback)
