---
title: Desenrolamento de link
author: clearab
description: Como realizar a desaplicação de link com a extensão de mensagens em um aplicativo do Microsoft Teams.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 0d488638e63b8ec78bfa5bed8cf6f4f037883fb1
ms.sourcegitcommit: bf61ae5ad2afa4efdb0311158184d0cbb9c40174
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2021
ms.locfileid: "49845634"
---
# <a name="link-unfurling"></a>Desenrolamento de link

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

> [!NOTE]
> Atualmente, não há suporte para a desesconsição de link em clientes móveis.

Com o link desfraldado, seu aplicativo pode se registrar para receber uma atividade quando URLs com um determinado domínio são colar na `invoke` área de mensagem de composição. O conterá a URL completa que foi colar na área de mensagem de redação, e você pode responder com um cartão que o usuário possa desesconelhar, fornecendo informações ou `invoke` ações adicionais.  Isso funciona de maneira muito semelhante a um [comando de pesquisa,](~/messaging-extensions/how-to/search-commands/define-search-command.md)com a URL servindo como termo de pesquisa.

A extensão de mensagens do Azure DevOps usa o link desfralhado para procurar URLs colarem na área de mensagem de composição apontando para um item de trabalho. Na captura de tela abaixo, um usuário pastou uma URL para um item de trabalho no Azure DevOps que a extensão de mensagens foi resolvida em um cartão.

![Exemplo de desesqueamento de link](~/assets/images/compose-extensions/messagingextensions_linkunfurling.png)

## <a name="add-link-unfurling-to-your-app-manifest"></a>Adicionar link desaplicação ao manifesto do aplicativo

 Para adicionar link desaplicação ao manifesto do aplicativo, adicione uma nova matriz `messageHandlers` à seção do manifesto do aplicativo `composeExtensions` JSON. Você pode adicionar a matriz com a ajuda do App Studio ou manualmente. As listagem de domínio podem incluir caracteres curinga, por `*.example.com` exemplo. Isso corresponde a exatamente um segmento do domínio; se você precisar corresponder, `a.b.example.com` use `*.*.example.com` .

> [!NOTE]
> Não adicione domínios que estejam fora do seu controle, diretamente ou por meio de caracteres curinga. Por exemplo, yourapp.onmicrosoft.com é válido, mas *.onmicrosoft.com não é válido. Além disso, os domínios de nível superior são proibidos. Por exemplo, *.com, *.org.

### <a name="using-app-studio"></a>Usando o aplicativo Studio

1. No App Studio, na guia Editor de manifesto, carregue o manifesto do aplicativo.
1. Na página **Extensão de Mensagens,** adicione o domínio  que você deseja procurar na seção Manipuladores de mensagens, como na captura de tela abaixo.

![seção manipuladores de mensagens no App Studio](~/assets/images/link-unfurling.png)

### <a name="manually"></a>Manualmente

Para permitir que sua extensão de mensagens interaja com links dessa forma, primeiro você precisará adicionar a matriz ao manifesto do aplicativo, como `messageHandlers` no exemplo abaixo. Este exemplo não é o manifesto completo, consulte a referência [de manifesto](~/resources/schema/manifest-schema.md) para um exemplo de manifesto completo.

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

Depois de adicionar o domínio para escutar o manifesto do aplicativo, você precisará atualizar o código do serviço Web para manipular a solicitação de invocação. Use a URL que você recebe para pesquisar seu serviço e criar uma resposta de cartão. Se você responder com mais de um cartão, somente o primeiro será usado.

Damos suporte aos seguintes tipos de cartão:

* [Cartão de miniatura](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [Cartão de herói](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [Cartão do Conector do Office 365](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [Cartão adaptável](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

Veja [o que são cartões para](~/task-modules-and-cards/what-are-cards.md) ter uma visão geral.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionResponse> OnTeamsAppBasedLinkQueryAsync(ITurnContext<IInvokeActivity> turnContext, AppBasedLinkQuery query, CancellationToken cancellationToken)
{
    //You'll use the query.link value to search your service and create a card response
    var card = new HeroCard
    {
        Title = "Hero Card",
        Text = query.Url,
        Images = new List<CardImage> { new CardImage("https://raw.githubusercontent.com/microsoft/botframework-sdk/master/icon.png") },
    };

    var attachments = new MessagingExtensionAttachment(HeroCard.ContentType, null, card);
    var result = new MessagingExtensionResult(AttachmentLayoutTypes.List, "result", new[] { attachments }, null, "test unfurl");

    return new MessagingExtensionResponse(result);
}
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

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

# <a name="json"></a>[JSON](#tab/json)

Este é um exemplo do `invoke` que foi enviado para seu bot.

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
