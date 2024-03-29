---
title: Desenrolamento de link
author: surbhigupta
description: Adicione o unfurling de link com a extensão de mensagens em um aplicativo do Microsoft Teams com manifesto de aplicativo ou manualmente. Adicionar o unfurling de link usando o Portal do Desenvolvedor. Como atualizar o código do serviço Web para lidar com a solicitação de invocação.
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: c706bd4caf8ab7859fb0c8f9b5b9e8f337a3b269
ms.sourcegitcommit: 9ea9a70d2591bce6b8c980d22014e160f7b45f91
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2022
ms.locfileid: "68820147"
---
# <a name="add-link-unfurling"></a>Adicionar desenrolamento de link

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Este documento orienta como adicionar a desenrolação de link ao manifesto do aplicativo usando o Portal do Desenvolvedor ou manualmente. Com o desenrolamento de link, seu aplicativo pode se registrar para receber uma atividade `invoke` quando as URLs com um domínio específico são coladas na área de mensagem de redação. O `invoke` contém a URL completa que foi colada na área de mensagem de composição. Você pode responder com um cartão que o usuário pode cancelar para obter informações ou ações adicionais. Isso funciona como um comando de pesquisa com a URL como o termo de pesquisa.

> [!NOTE]
>
> * Atualmente, não há suporte para desenrolamento de link em clientes móveis.
> * O resultado da desenrolamento de link é armazenado em cache por 30 minutos.
> * Os comandos de extensão de mensagens não são necessários para a desenrolação do Link. No entanto, deve haver pelo menos um comando no manifesto, pois é uma propriedade obrigatória em extensões de mensagens. Para obter mais informações, consulte [extensões de composição](/microsoftteams/platform/resources/schema/manifest-schema)

A Azure DevOps de mensagem usa o desenrolamento de link para procurar URLs coladas na área de mensagem de composição apontando para um item de trabalho. Na imagem a seguir, um usuário coleu uma URL para um item no Azure DevOps que a extensão da mensagem resolveu em um cartão:

:::image type="content" source="~/assets/images/compose-extensions/messagingextensions_linkunfurling.png" alt-text="Exemplo de desenrolamento de link":::

Confira o vídeo a seguir para saber mais sobre a desenrolação do link:
<br>
> [!VIDEO <https://www.microsoft.com/en-us/videoplayer/embed/RE4OFZG>]
<br>

## <a name="add-link-unfurling-to-your-app-manifest"></a>Adicionar desenrolamento de link ao manifesto do aplicativo

Para adicionar o desenrolamento de link ao manifesto do aplicativo, adicione uma nova matriz `messageHandlers` à seção `composeExtensions` do manifesto do aplicativo JSON. Você pode adicionar a matriz com a ajuda do Portal do Desenvolvedor ou manualmente. As listagens de domínio podem incluir caracteres curinga, por exemplo, `*.example.com`. Isso corresponde exatamente a um segmento do domínio; se você precisar corresponder `a.b.example.com` use `*.*.example.com`.

> [!NOTE]
> Não adicione domínios que não estejam no controle, diretamente ou por meio de curingas. Por exemplo, `yourapp.onmicrosoft.com` é válido, mas `*.onmicrosoft.com` não é válido. Os domínios de nível superior são proibidos, por exemplo, `*.com`, . `*.org`

### <a name="add-link-unfurling-using-developer-portal"></a>Adicionar unfurling de link usando o Portal do Desenvolvedor

1. Abra o **Portal do Desenvolvedor** no cliente do Microsoft Teams e selecione a guia **Aplicativos** .
1. Carregue o manifesto do aplicativo.
1. Na página **Extensão de Mensagens** em **Recursos de aplicativo**, selecione bot existente ou crie um novo bot.
1. Selecione **Salvar**.
1. Selecione **Adicionar um domínio** na seção **Visualizar links** e, em seguida, insira domínio válido.
1. Selecione **Adicionar**. A imagem a seguir explica o processo:

   :::image type="content" source="../../assets/images/tdp/add-domain-button.PNG" alt-text="Captura de tela da seção manipuladores de mensagens no Portal do Desenvolvedor." lightbox="../../assets/images/tdp/add-domain.PNG":::

### <a name="add-link-unfurling-manually"></a>Adicionar link desfraldando manualmente

> [!NOTE]
> Se a autenticação for adicionada por meio de Azure AD, [desmarca os links no Teams usando o bot](/microsoftteams/platform/sbs-botbuilder-linkunfurling?tabs=vs&tutorial-step=4).

Para habilitar sua extensão de mensagem para interagir com links, primeiro você deve adicionar a matriz `messageHandlers` ao manifesto do aplicativo. O exemplo a seguir explica como adicionar o link desfraldamento manualmente:

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

Para obter um exemplo de manifesto completo, consulte [referência de manifesto](~/resources/schema/manifest-schema.md).

## <a name="handle-the-composeextensionquerylink-invoke"></a>Manipular a invocação `composeExtension/queryLink`

Depois de adicionar o domínio ao manifesto do aplicativo, você deve atualizar o código do serviço Web para manipular a solicitação de invocação. Use a URL recebida para pesquisar seu serviço e criar uma resposta de cartão. Se você responder com mais de um cartão, somente a primeira resposta do cartão será usada.

Há suporte para os seguintes tipos de cartão:

* [cartão de Miniatura](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [cartão Hero](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [cartão do Conector do Office 365](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [Cartão Adaptável](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

Para obter mais informações, consulte [invocação de tipo de ação](~/task-modules-and-cards/cards/cards-actions.md#action-type-invoke).

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

A seguir, um exemplo do `invoke` enviado ao bot:

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

Siga o [guia passo a passo](../../sbs-botbuilder-linkunfurling.yml) para desenrolar links no Teams usando o bot.

## <a name="see-also"></a>Confira também

* [Extensões de mensagens](../what-are-messaging-extensions.md)
* [Cartões Adaptáveis](../../task-modules-and-cards/what-are-cards.md#adaptive-cards)
* [Link de guias desdobradas e Exibição de Estágio](../../tabs/tabs-link-unfurling.md)
* [composeExtensions](../../resources/schema/manifest-schema.md#composeextensions)
