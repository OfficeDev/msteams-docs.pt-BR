---
title: Link Unfurling
author: clearab
description: Como executar o link Unfurling com a extensão de mensagens em um aplicativo do Microsoft Teams.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: ccc23f06fbe759dc4c38dfc63dfa356d38352c27
ms.sourcegitcommit: 67c021fa20eb5ea70c059fcc35be1c19c6c97c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "42279771"
---
# <a name="link-unfurling"></a><span data-ttu-id="5155c-103">Link Unfurling</span><span class="sxs-lookup"><span data-stu-id="5155c-103">Link unfurling</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

<span data-ttu-id="5155c-104">Com o link Unfurling seu aplicativo pode se registrar para `invoke` receber uma atividade quando as URLs com um domínio específico são coladas na área de mensagem de composição.</span><span class="sxs-lookup"><span data-stu-id="5155c-104">With link unfurling your app can register to receive an `invoke` activity when URLs with a particular domain are pasted into the compose message area.</span></span> <span data-ttu-id="5155c-105">O `invoke` conterá a URL completa que foi colada na área de mensagem de redação, e você pode responder com um cartão que o usuário pode *unfurl*, fornecendo informações ou ações adicionais.</span><span class="sxs-lookup"><span data-stu-id="5155c-105">The `invoke` will contain the full URL that was pasted into the compose message area, and you can respond with a card the user can *unfurl*, providing additional information or actions.</span></span> <span data-ttu-id="5155c-106">Isso funciona de forma semelhante a um [comando de pesquisa](~/messaging-extensions/how-to/search-commands/define-search-command.md), com a URL servindo como o termo de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="5155c-106">This works very similarly to a [search command](~/messaging-extensions/how-to/search-commands/define-search-command.md), with the URL serving as the search term.</span></span>

<span data-ttu-id="5155c-107">A extensão de mensagens do DevOps do Azure usa o link Unfurling para procurar por URLs coladas na área de mensagem de redação que apontam para um item de trabalho.</span><span class="sxs-lookup"><span data-stu-id="5155c-107">The Azure DevOps messaging extension uses link unfurling to look for URLs pasted into the compose message area pointing to a work item.</span></span> <span data-ttu-id="5155c-108">Na captura de tela abaixo, um usuário colou em uma URL para um item de trabalho no Azure DevOps que a extensão de mensagens foi resolvida em um cartão.</span><span class="sxs-lookup"><span data-stu-id="5155c-108">In the screenshot below, a user has pasted in a URL for a work item in Azure DevOps which the messaging extension has resolved into a card.</span></span>

![Exemplo de link Unfurling](~/assets/images/compose-extensions/messagingextensions_linkunfurling.png)

## <a name="add-link-unfurling-to-your-app-manifest"></a><span data-ttu-id="5155c-110">Adicionar link Unfurling ao manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="5155c-110">Add link unfurling to your app manifest</span></span>

<span data-ttu-id="5155c-111">Para fazer isso, você adicionará uma `messageHandlers` nova matriz à `composeExtensions` seção de seu aplicativo JSON de manifesto.</span><span class="sxs-lookup"><span data-stu-id="5155c-111">To do this you'll add a new `messageHandlers` array to the `composeExtensions` section of your app manifest JSON.</span></span> <span data-ttu-id="5155c-112">Você pode fazer isso com a ajuda do App Studio ou manualmente.</span><span class="sxs-lookup"><span data-stu-id="5155c-112">You can either do so with the help of App Studio, or manually.</span></span> <span data-ttu-id="5155c-113">As listagens de domínio podem incluir curingas, `*.example.com`por exemplo.</span><span class="sxs-lookup"><span data-stu-id="5155c-113">Domain listings can include wildcards, for example `*.example.com`.</span></span> <span data-ttu-id="5155c-114">Isso corresponde exatamente a um segmento do domínio; Se você precisar coincidir `a.b.example.com` e usar `*.*.example.com`.</span><span class="sxs-lookup"><span data-stu-id="5155c-114">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span>

### <a name="using-app-studio"></a><span data-ttu-id="5155c-115">Usando o aplicativo Studio</span><span class="sxs-lookup"><span data-stu-id="5155c-115">Using App Studio</span></span>

1. <span data-ttu-id="5155c-116">No app Studio, na guia Editor do manifesto, carregue o manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5155c-116">In App Studio, on the Manifest editor tab, load your app manifest.</span></span>
1. <span data-ttu-id="5155c-117">Na página **extensão de mensagens** , adicione o domínio que você deseja procurar na seção **manipuladores de mensagens** , como na captura de tela abaixo.</span><span class="sxs-lookup"><span data-stu-id="5155c-117">On the **Messaging Extension** page, add the domain you want to look for in the **Message handlers** section as in the screenshot below.</span></span>

![seção manipuladores de mensagens no app Studio](~/assets/images/link-unfurling.png)

### <a name="manually"></a><span data-ttu-id="5155c-119">Manualmente</span><span class="sxs-lookup"><span data-stu-id="5155c-119">Manually</span></span>

<span data-ttu-id="5155c-120">Para habilitar sua extensão de mensagens para interagir com os links dessa forma, primeiro você precisará `messageHandlers` adicionar a matriz ao manifesto do aplicativo, como no exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="5155c-120">To enable your messaging extension to interact with links this way you'll first need to add the `messageHandlers` array to your app manifest as in the example below.</span></span> <span data-ttu-id="5155c-121">Este exemplo não é o manifesto completo, confira [referência de manifesto](~/resources/schema/manifest-schema.md) para um exemplo de manifesto completo.</span><span class="sxs-lookup"><span data-stu-id="5155c-121">This example is not the complete manifest, see [manifest reference](~/resources/schema/manifest-schema.md) for a complete manifest example.</span></span>

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

## <a name="handle-the-composeextensionquerylink-invoke"></a><span data-ttu-id="5155c-122">Manipular a `composeExtension/queryLink` invocação</span><span class="sxs-lookup"><span data-stu-id="5155c-122">Handle the `composeExtension/queryLink` invoke</span></span>

<span data-ttu-id="5155c-123">Depois de adicionar o domínio para ouvir o manifesto do aplicativo, você precisará atualizar o código do serviço Web para lidar com a solicitação de invocação.</span><span class="sxs-lookup"><span data-stu-id="5155c-123">Once you've added the domain to listen on to the app manifest, you'll need to update your web service code to handle the invoke request.</span></span> <span data-ttu-id="5155c-124">Use a URL que você recebe para pesquisar seu serviço e criar uma resposta de cartão.</span><span class="sxs-lookup"><span data-stu-id="5155c-124">Use the URL you receive to search your service and create a card response.</span></span> <span data-ttu-id="5155c-125">Se você responder com mais de um cartão, apenas o primeiro será usado.</span><span class="sxs-lookup"><span data-stu-id="5155c-125">If you respond with more than one card, only the first will be used.</span></span>

<span data-ttu-id="5155c-126">Oferecemos suporte para os seguintes tipos de cartão:</span><span class="sxs-lookup"><span data-stu-id="5155c-126">We support the following card types:</span></span>

* [<span data-ttu-id="5155c-127">Cartão de miniaturas</span><span class="sxs-lookup"><span data-stu-id="5155c-127">Thumbnail card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [<span data-ttu-id="5155c-128">Cartão herói</span><span class="sxs-lookup"><span data-stu-id="5155c-128">Hero card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [<span data-ttu-id="5155c-129">Cartão de conexão do Office 365</span><span class="sxs-lookup"><span data-stu-id="5155c-129">Office 365 Connector card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [<span data-ttu-id="5155c-130">Cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="5155c-130">Adaptive Card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

<span data-ttu-id="5155c-131">Confira [o que são cartões](~/task-modules-and-cards/what-are-cards.md) para uma visão geral.</span><span class="sxs-lookup"><span data-stu-id="5155c-131">See [What are cards](~/task-modules-and-cards/what-are-cards.md) for an overview.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="5155c-132">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="5155c-132">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="javascriptnodejs"></a>[<span data-ttu-id="5155c-133">JavaScript/node. js</span><span class="sxs-lookup"><span data-stu-id="5155c-133">JavaScript/Node.js</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="5155c-134">JSON</span><span class="sxs-lookup"><span data-stu-id="5155c-134">JSON</span></span>](#tab/json)

<span data-ttu-id="5155c-135">Este é um exemplo do `invoke` enviado ao bot.</span><span class="sxs-lookup"><span data-stu-id="5155c-135">This is an example of the `invoke` sent to your bot.</span></span>

```json
{
  "type": "invoke",
  "name": "composeExtension/queryLink",
  "value": {
    "url": "https://theurlsubmittedbyyouruser.trackeddomain.com/id/1234"
  }
}
```

<span data-ttu-id="5155c-136">Um exemplo da resposta é mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="5155c-136">An example of the response is shown below.</span></span>

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
