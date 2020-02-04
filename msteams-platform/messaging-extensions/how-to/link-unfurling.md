---
title: Link Unfurling
author: clearab
description: Como executar o link Unfurling com a extensão de mensagens em um aplicativo do Microsoft Teams.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 5b20ea303a2c3d085651a53b01af4bb449d386de
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672952"
---
# <a name="link-unfurling"></a>Link Unfurling

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Com o link Unfurling seu aplicativo pode se registrar para `invoke` receber uma atividade quando as URLs com um domínio específico são coladas na área de mensagem de composição. O `invoke` conterá a URL completa que foi colada na área de mensagem de redação, e você pode responder com um cartão que o usuário pode *unfurl*, fornecendo informações ou ações adicionais. Isso funciona de forma semelhante a um [comando de pesquisa](~/messaging-extensions/how-to/search-commands/define-search-command.md), com a URL servindo como o termo de pesquisa.

A extensão de mensagens do DevOps do Azure usa o link Unfurling para procurar por URLs coladas na área de mensagem de redação que apontam para um item de trabalho. Na captura de tela abaixo, um usuário colou em uma URL para um item de trabalho no Azure DevOps que a extensão de mensagens foi resolvida em um cartão.

![Exemplo de link Unfurling](~/assets/images/compose-extensions/messagingextensions_linkunfurling.png)

## <a name="add-link-unfurling-to-your-app-manifest"></a>Adicionar link Unfurling ao manifesto do aplicativo

Para fazer isso, você adicionará uma `messageHandlers` nova matriz à `composeExtensions` seção de seu aplicativo JSON de manifesto. Você pode fazer isso com a ajuda do App Studio ou manualmente. As listagens de domínio podem incluir curingas, `*.example.com`por exemplo. Isso corresponde exatamente a um segmento do domínio; Se você precisar coincidir `a.b.example.com` e usar `*.*.example.com`.

### <a name="using-app-studio"></a>Usando o app Studio

1. No app Studio, na guia Editor do manifesto, carregue o manifesto do aplicativo.
1. Na página **extensão de mensagens** , adicione o domínio que você deseja procurar na seção **manipuladores de mensagens** , como na captura de tela abaixo.

![seção manipuladores de mensagens no app Studio](~/assets/images/link-unfurling.png)

### <a name="manually"></a>Manualmente

Para habilitar sua extensão de mensagens para interagir com os links dessa forma, primeiro você precisará `messageHandlers` adicionar a matriz ao manifesto do aplicativo, como no exemplo abaixo. Este exemplo não é o manifesto completo, confira [referência de manifesto](~/resources/schema/manifest-schema.md) para um exemplo de manifesto completo.

```json
...
"composeExtensions": [
  {
    "botId": "abc123456-ab12-ab12-ab12-abcdef123456",
    "messageHandlers": [
      {
        "type": "link",
        "value": {
          "domains": [
            "*.trackeddomain.com"
          ]
        }
      }
    ]
  }
],
...
```

## <a name="handle-the-composeextensionquerylink-invoke"></a>Manipular a `composeExtension/queryLink` invocação

Depois de adicionar o domínio para ouvir o manifesto do aplicativo, você precisará atualizar o código do serviço Web para lidar com a solicitação de invocação. Use a URL que você recebe para pesquisar seu serviço e criar uma resposta de cartão. Se você responder com mais de um cartão, apenas o primeiro será usado.

Oferecemos suporte para os seguintes tipos de cartão:

* [Cartão de miniaturas](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [Cartão herói](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [Cartão de conexão do Office 365](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [Cartão adaptável](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

Confira [o que são cartões](~/task-modules-and-cards/what-are-cards.md) para uma visão geral.

# <a name="cnettabdotnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionResponse> OnTeamsAppBasedLinkQueryAsync(ITurnContext<IInvokeActivity> turnContext, AppBasedLinkQuery query, CancellationToken cancellationToken)
{
    //You'll use the query.link value to search your service and create a card response
    var heroCard = new ThumbnailCard
    {
        Title = "Thumbnail Card",
        Text = query.Url,
        Images = new List<CardImage> { new CardImage("https://raw.githubusercontent.com/microsoft/botframework-sdk/master/icon.png") },
    };

    var attachments = new MessagingExtensionAttachment(HeroCard.ContentType, null, heroCard);
    var result = new MessagingExtensionResult(AttachmentLayoutTypes.List, "result", new[] { attachments }, null, "test unfurl");

    return new MessagingExtensionResponse(result);
}
```

# <a name="javascriptnodejstabjavascript"></a>[JavaScript/node. js](#tab/javascript)

```javascript
class TeamsLinkUnfurlingBot extends TeamsActivityHandler {
  handleTeamsAppBasedLinkQuery(context, query) {
    const attachment = CardFactory.thumbnailCard('Thumbnail Card',
      query.url,
      ['https://raw.githubusercontent.com/microsoft/botframework-sdk/master/icon.png']);

    const result = {
      attachmentLayout: 'list',
      type: 'result',
      attachments: [attachment]
    };

    const response = {
      composeExtension: result
    };
    return response;
  }
}
```

# <a name="jsontabjson"></a>[JSON](#tab/json)

Este é um exemplo do `invoke` enviado ao bot.

```json
{
  "type": "invoke",
  "name": "composeExtension/queryLink",
  "value": {
    "url": "https://theurlsubmittedbyyouruser.trackeddomain.com/id/1234"
  }
}
```

Um exemplo da resposta é mostrado abaixo.

```json
{
  "composeExtension": {
    "type": "result",
    "attachmentLayout": "list",
    "attachments": [
      {
        "contentType": "application/vnd.microsoft.teams.card.o365connector",
        "content": {
          "sections": [
            {
              "activityTitle": "[85069]: Create a cool app",
              "activityImage": "https://placekitten.com/200/200"
            },
            {
              "title": "Details",
              "facts": [
                {
                  "name": "Assigned to:",
                  "value": "[Larry Brown](mailto:larryb@example.com)"
                },
                {
                  "name": "State:",
                  "value": "Active"
                }
              ]
            }
          ]
        }
      }
    ]
  }
}
```

* * *
