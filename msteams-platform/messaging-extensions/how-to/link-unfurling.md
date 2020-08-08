---
title: Desenrolamento de link
author: clearab
description: Como executar o link Unfurling com a extensão de mensagens em um aplicativo do Microsoft Teams.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 32d19fcd44f2475047539350706d2745aeec3691
ms.sourcegitcommit: 7a2da3b65246a125d441a971e7e6a6418355adbe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2020
ms.locfileid: "46587801"
---
# <a name="link-unfurling"></a><span data-ttu-id="e93f4-103">Desenrolamento de link</span><span class="sxs-lookup"><span data-stu-id="e93f4-103">Link unfurling</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

> [!NOTE]
> <span data-ttu-id="e93f4-104">No momento, o link Unfurling não é suportado em clientes móveis.</span><span class="sxs-lookup"><span data-stu-id="e93f4-104">Currently, Link unfurling is not supported on Mobile clients.</span></span>

<span data-ttu-id="e93f4-105">Com o link Unfurling seu aplicativo pode se registrar para receber uma `invoke` atividade quando as URLs com um domínio específico são coladas na área de mensagem de composição.</span><span class="sxs-lookup"><span data-stu-id="e93f4-105">With link unfurling your app can register to receive an `invoke` activity when URLs with a particular domain are pasted into the compose message area.</span></span> <span data-ttu-id="e93f4-106">O `invoke` conterá a URL completa que foi colada na área de mensagem de redação, e você pode responder com um cartão que o usuário pode *unfurl*, fornecendo informações ou ações adicionais.</span><span class="sxs-lookup"><span data-stu-id="e93f4-106">The `invoke` will contain the full URL that was pasted into the compose message area, and you can respond with a card the user can *unfurl*, providing additional information or actions.</span></span> <span data-ttu-id="e93f4-107">Isso funciona de forma semelhante a um [comando de pesquisa](~/messaging-extensions/how-to/search-commands/define-search-command.md), com a URL servindo como o termo de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="e93f4-107">This works very similarly to a [search command](~/messaging-extensions/how-to/search-commands/define-search-command.md), with the URL serving as the search term.</span></span>

<span data-ttu-id="e93f4-108">A extensão de mensagens do DevOps do Azure usa o link Unfurling para procurar por URLs coladas na área de mensagem de redação que apontam para um item de trabalho.</span><span class="sxs-lookup"><span data-stu-id="e93f4-108">The Azure DevOps messaging extension uses link unfurling to look for URLs pasted into the compose message area pointing to a work item.</span></span> <span data-ttu-id="e93f4-109">Na captura de tela abaixo, um usuário colou em uma URL para um item de trabalho no Azure DevOps que a extensão de mensagens foi resolvida em um cartão.</span><span class="sxs-lookup"><span data-stu-id="e93f4-109">In the screenshot below, a user has pasted in a URL for a work item in Azure DevOps which the messaging extension has resolved into a card.</span></span>

![Exemplo de link Unfurling](~/assets/images/compose-extensions/messagingextensions_linkunfurling.png)

## <a name="add-link-unfurling-to-your-app-manifest"></a><span data-ttu-id="e93f4-111">Adicionar link Unfurling ao manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="e93f4-111">Add link unfurling to your app manifest</span></span>

<span data-ttu-id="e93f4-112">Para fazer isso, você adicionará uma nova `messageHandlers` matriz à `composeExtensions` seção de seu aplicativo JSON de manifesto.</span><span class="sxs-lookup"><span data-stu-id="e93f4-112">To do this you'll add a new `messageHandlers` array to the `composeExtensions` section of your app manifest JSON.</span></span> <span data-ttu-id="e93f4-113">Você pode fazer isso com a ajuda do App Studio ou manualmente.</span><span class="sxs-lookup"><span data-stu-id="e93f4-113">You can either do so with the help of App Studio, or manually.</span></span> <span data-ttu-id="e93f4-114">As listagens de domínio podem incluir curingas, por exemplo `*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="e93f4-114">Domain listings can include wildcards, for example `*.example.com`.</span></span> <span data-ttu-id="e93f4-115">Isso corresponde exatamente a um segmento do domínio; Se você precisar coincidir `a.b.example.com` e usar `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="e93f4-115">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span>

### <a name="using-app-studio"></a><span data-ttu-id="e93f4-116">Usando o aplicativo Studio</span><span class="sxs-lookup"><span data-stu-id="e93f4-116">Using App Studio</span></span>

1. <span data-ttu-id="e93f4-117">No app Studio, na guia Editor do manifesto, carregue o manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e93f4-117">In App Studio, on the Manifest editor tab, load your app manifest.</span></span>
1. <span data-ttu-id="e93f4-118">Na página **extensão de mensagens** , adicione o domínio que você deseja procurar na seção **manipuladores de mensagens** , como na captura de tela abaixo.</span><span class="sxs-lookup"><span data-stu-id="e93f4-118">On the **Messaging Extension** page, add the domain you want to look for in the **Message handlers** section as in the screenshot below.</span></span>

![seção manipuladores de mensagens no app Studio](~/assets/images/link-unfurling.png)

### <a name="manually"></a><span data-ttu-id="e93f4-120">Manualmente</span><span class="sxs-lookup"><span data-stu-id="e93f4-120">Manually</span></span>

<span data-ttu-id="e93f4-121">Para habilitar sua extensão de mensagens para interagir com os links dessa forma, primeiro você precisará adicionar a `messageHandlers` matriz ao manifesto do aplicativo, como no exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="e93f4-121">To enable your messaging extension to interact with links this way you'll first need to add the `messageHandlers` array to your app manifest as in the example below.</span></span> <span data-ttu-id="e93f4-122">Este exemplo não é o manifesto completo, confira [referência de manifesto](~/resources/schema/manifest-schema.md) para um exemplo de manifesto completo.</span><span class="sxs-lookup"><span data-stu-id="e93f4-122">This example is not the complete manifest, see [manifest reference](~/resources/schema/manifest-schema.md) for a complete manifest example.</span></span>

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

## <a name="handle-the-composeextensionquerylink-invoke"></a><span data-ttu-id="e93f4-123">Manipular a `composeExtension/queryLink` invocação</span><span class="sxs-lookup"><span data-stu-id="e93f4-123">Handle the `composeExtension/queryLink` invoke</span></span>

<span data-ttu-id="e93f4-124">Depois de adicionar o domínio para ouvir o manifesto do aplicativo, você precisará atualizar o código do serviço Web para lidar com a solicitação de invocação.</span><span class="sxs-lookup"><span data-stu-id="e93f4-124">Once you've added the domain to listen on to the app manifest, you'll need to update your web service code to handle the invoke request.</span></span> <span data-ttu-id="e93f4-125">Use a URL que você recebe para pesquisar seu serviço e criar uma resposta de cartão.</span><span class="sxs-lookup"><span data-stu-id="e93f4-125">Use the URL you receive to search your service and create a card response.</span></span> <span data-ttu-id="e93f4-126">Se você responder com mais de um cartão, apenas o primeiro será usado.</span><span class="sxs-lookup"><span data-stu-id="e93f4-126">If you respond with more than one card, only the first will be used.</span></span>

<span data-ttu-id="e93f4-127">Oferecemos suporte para os seguintes tipos de cartão:</span><span class="sxs-lookup"><span data-stu-id="e93f4-127">We support the following card types:</span></span>

* [<span data-ttu-id="e93f4-128">Cartão de miniaturas</span><span class="sxs-lookup"><span data-stu-id="e93f4-128">Thumbnail card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [<span data-ttu-id="e93f4-129">Cartão herói</span><span class="sxs-lookup"><span data-stu-id="e93f4-129">Hero card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [<span data-ttu-id="e93f4-130">Cartão de conexão do Office 365</span><span class="sxs-lookup"><span data-stu-id="e93f4-130">Office 365 Connector card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [<span data-ttu-id="e93f4-131">Cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="e93f4-131">Adaptive Card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

<span data-ttu-id="e93f4-132">Confira [o que são cartões](~/task-modules-and-cards/what-are-cards.md) para uma visão geral.</span><span class="sxs-lookup"><span data-stu-id="e93f4-132">See [What are cards](~/task-modules-and-cards/what-are-cards.md) for an overview.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="e93f4-133">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="e93f4-133">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="javascriptnodejs"></a>[<span data-ttu-id="e93f4-134">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="e93f4-134">JavaScript/Node.js</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="e93f4-135">JSON</span><span class="sxs-lookup"><span data-stu-id="e93f4-135">JSON</span></span>](#tab/json)

<span data-ttu-id="e93f4-136">Este é um exemplo do `invoke` enviado ao bot.</span><span class="sxs-lookup"><span data-stu-id="e93f4-136">This is an example of the `invoke` sent to your bot.</span></span>

```json
{
  "type": "invoke",
  "name": "composeExtension/queryLink",
  "value": {
    "url": "https://theurlsubmittedbyyouruser.trackeddomain.com/id/1234"
  }
}
```

<span data-ttu-id="e93f4-137">Um exemplo da resposta é mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="e93f4-137">An example of the response is shown below.</span></span>

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
