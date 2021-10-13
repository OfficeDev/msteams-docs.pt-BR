---
title: Desenrolamento de link
author: surbhigupta
description: Como executar o link desfraldamento com a extensão de mensagens em um Microsoft Teams aplicativo.
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 99dbfaa2bf66ee50341e52d4e8a274f7ab20a73e
ms.sourcegitcommit: 37b1724bb0d2f1b087c356e0fd0ff80145671e22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/13/2021
ms.locfileid: "60291720"
---
# <a name="link-unfurling"></a>Desenrolamento de link

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Este documento orienta você sobre como adicionar link desfraldado ao manifesto do aplicativo usando o App studio e manualmente. Com o link desfraldado, seu aplicativo pode se registrar para receber uma atividade quando URLs com um determinado domínio são colar na `invoke` área de mensagem de redação. O contém a URL completa que foi colar na área de mensagem de composição e você pode responder com um cartão que o usuário pode desafraldar, fornecendo informações ou `invoke` ações adicionais. Isso funciona de forma semelhante a um comando de pesquisa com a URL servindo como o termo de pesquisa.

> [!NOTE]
> * Atualmente, não há suporte para a desalinização de link em clientes Móveis.
> * O resultado de desfralização do link é armazenado em cache por 30 minutos.

A Azure DevOps de mensagens usa o link desfraldamento para procurar URLs colaram na área de mensagem de composição apontando para um item de trabalho. Na imagem a seguir, um usuário pastou uma URL para um item de trabalho no Azure DevOps, que a extensão de mensagens resolveu em um cartão:

![Exemplo de desfraldamento de link](~/assets/images/compose-extensions/messagingextensions_linkunfurling.png)

## <a name="add-link-unfurling-to-your-app-manifest"></a>Adicionar a desaplicação de link ao manifesto do aplicativo

Para adicionar a desaplicação de link ao manifesto do aplicativo, adicione uma nova matriz à seção `messageHandlers` `composeExtensions` do manifesto JSON do aplicativo. Você pode adicionar a matriz com a ajuda do App Studio ou manualmente. Listagem de domínio pode incluir caracteres curinga, por exemplo `*.example.com` . Isso corresponde a exatamente um segmento do domínio; se você precisar corresponder, `a.b.example.com` use `*.*.example.com` .

> [!NOTE]
> Não adicione domínios que não estão no seu controle, diretamente ou por meio de caracteres curinga. Por exemplo, `yourapp.onmicrosoft.com` é válido, mas `*.onmicrosoft.com` não é válido. Além disso, os domínios de nível superior são proibidos. Por exemplo, `*.com` , `*.org` .

### <a name="add-link-unfurling-using-app-studio"></a>Adicionar link desfraldamento usando o App Studio

1. Abra **o App Studio** no cliente Microsoft Teams e selecione a guia Editor **de** Manifesto.
1. Carregue o manifesto do aplicativo.
1. Na página **Extensão de Mensagens,** adicione o domínio que você deseja procurar na seção **Manipuladores de** mensagens. A imagem a seguir explica o processo:

    ![seção manipuladores de mensagens no App Studio](~/assets/images/link-unfurling.png)
    
### <a name="add-link-unfurling-manually"></a>Adicionar link desfraldamento manualmente

Para permitir que sua extensão de mensagens interaja com links, primeiro você deve adicionar a `messageHandlers` matriz ao manifesto do aplicativo. O exemplo a seguir explica como adicionar o link desfraldamento manualmente: 


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

Para um exemplo de manifesto completo, consulte [referência de manifesto](~/resources/schema/manifest-schema.md).

## <a name="handle-the-composeextensionquerylink-invoke"></a>Manipular a `composeExtension/queryLink` invocação

Depois de adicionar o domínio ao manifesto do aplicativo, você deve atualizar seu código de serviço Web para manipular a solicitação de invocação. Use a URL recebida para pesquisar seu serviço e criar uma resposta de cartão. Se você responder com mais de um cartão, somente a resposta do primeiro cartão será usada.

Os seguintes tipos de cartão são suportados:

* [Cartão de miniatura](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [Cartão de herói](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [Office 365 Cartão conector](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [Cartão Adaptável](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

Você pode exibir uma visualização de um cartão adaptável ou Office 365 conector na lista de resultados usando sua propriedade de visualização. A propriedade preview não será necessária se os resultados já são cartões Hero ou Thumbnail. Se você usar o anexo de visualização, ele deve ser um cartão Hero ou Thumbnail. Se nenhuma propriedade preview for especificada, a visualização do cartão falhará e nada será exibido.

### <a name="example"></a>Exemplo

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

A seguir está um exemplo do `invoke` enviado para seu bot:

```json
{
  "type": "invoke",
  "name": "composeExtension/queryLink",
  "value": {
    "url": "https://theurlsubmittedbyyouruser.trackeddomain.com/id/1234"
  }
}
```

A seguir está um exemplo da resposta:

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
              "activityImage&quot;: &quot;https://placekitten.com/200/200"
            },
            {
              "title": "Details",
              "facts": [
                {
                  "name": "Assigned to:",
                  "value&quot;: &quot;[Larry Brown](mailto:larryb@example.com)"
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

## <a name="see-also"></a>Confira também 

* [Cartões](~/task-modules-and-cards/what-are-cards.md)
* [Link de guias desdobradas e Exibição de Estágio](~/tabs/tabs-link-unfurling.md)
