---
title: Desenrolamento de link
author: surbhigupta
description: Saiba como adicionar link desfralhado com a extensão de mensagem em um aplicativo Microsoft Teams com manifesto do aplicativo ou manualmente usando exemplos de código e exemplos.
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 2dee02545a522b202e9cc695f7099848269e8944
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65104403"
---
# <a name="link-unfurling"></a>Desenrolamento de link

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Este documento orienta você sobre como adicionar link desfralhamento ao manifesto do aplicativo usando o App Studio e manualmente. Com o link desfralinhado, `invoke` seu aplicativo pode se registrar para receber uma atividade quando as URLs com um domínio específico são coladas na área de mensagem de composição. Contém `invoke` a URL completa que foi colada na área de mensagem de composição e você pode responder com um cartão que o usuário pode desfralham, fornecendo informações ou ações adicionais. Isso funciona de forma semelhante a um comando de pesquisa com a URL que serve como o termo de pesquisa.

> [!NOTE]
>
> * Atualmente, não há suporte para a desaplicação de link em clientes móveis.
> * O resultado da desfralização do link é armazenado em cache por 30 minutos.

A Azure DevOps de mensagem usa o desfralamento de link para procurar URLs coladas na área de mensagem de composição apontando para um item de trabalho. Na imagem a seguir, um usuário coleu uma URL para um item de trabalho no Azure DevOps, que a extensão da mensagem resolveu em um cartão:

![Exemplo de desarmamento de link](~/assets/images/compose-extensions/messagingextensions_linkunfurling.png)

## <a name="add-link-unfurling-to-your-app-manifest"></a>Adicionar link desfralização ao manifesto do aplicativo

Para adicionar um link desfraldamento ao manifesto do aplicativo, adicione uma nova `messageHandlers` matriz `composeExtensions` à seção do manifesto JSON do aplicativo. Você pode adicionar a matriz com a ajuda do App Studio ou manualmente. As listagem de domínio podem incluir caracteres curinga, por exemplo `*.example.com`. Isso corresponde exatamente a um segmento do domínio; se você precisar corresponder, `a.b.example.com` use `*.*.example.com`.

> [!NOTE]
> Não adicione domínios que não estão em seu controle, diretamente ou por meio de caracteres curinga. Por exemplo, `yourapp.onmicrosoft.com` é válido, mas `*.onmicrosoft.com` não é válido. Além disso, os domínios de nível superior são proibidos. Por exemplo, `*.com`, `*.org`.

### <a name="add-link-unfurling-using-app-studio"></a>Adicionar link desfralização usando o App Studio

1. Abra **o App Studio** no Microsoft Teams cliente e selecione a guia **Editor de Manifesto**.
1. Carregue o manifesto do aplicativo.
1. Na página **Extensão de** Mensagem, adicione o domínio que você deseja procurar na seção **Manipuladores de** mensagens. A imagem a seguir explica o processo:

    ![seção manipuladores de mensagens no App Studio](~/assets/images/link-unfurling.png)

### <a name="add-link-unfurling-manually"></a>Adicionar link desfraldando manualmente

Para permitir que a extensão de mensagem interaja com links, primeiro você deve adicionar `messageHandlers` a matriz ao manifesto do aplicativo. O exemplo a seguir explica como adicionar o link desfraldamento manualmente:

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

Para obter um exemplo de manifesto completo, consulte a [referência de manifesto](~/resources/schema/manifest-schema.md).

## <a name="handle-the-composeextensionquerylink-invoke"></a>Manipular a `composeExtension/queryLink` invocação

Depois de adicionar o domínio ao manifesto do aplicativo, você deve atualizar o código do serviço Web para manipular a solicitação de invocação. Use a URL recebida para pesquisar seu serviço e criar uma resposta de cartão. Se você responder com mais de um cartão, somente a primeira resposta do cartão será usada.

Há suporte para os seguintes tipos de cartão:

* [cartão de Miniatura](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [cartão Hero](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [cartão do Conector do Office 365](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [Cartão Adaptável](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

Para obter mais informações, consulte [Invocação de tipo de ação](~/task-modules-and-cards/cards/cards-actions.md#action-type-invoke).

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

A seguir está um exemplo do `invoke` enviado para o bot:

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

## <a name="step-by-step-guide"></a>Guias passo a passo

Siga o [guia passo a passo para](../../sbs-botbuilder-linkunfurling.yml) desfralhar links Teams bot.

## <a name="see-also"></a>Confira também

* [Cartões](~/task-modules-and-cards/what-are-cards.md)
* [Link de guias desfralização e Modo de Exibição de Estágio](~/tabs/tabs-link-unfurling.md)