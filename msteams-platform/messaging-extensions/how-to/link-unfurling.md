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
# <a name="link-unfurling"></a><span data-ttu-id="e8816-103">Desenrolamento de link</span><span class="sxs-lookup"><span data-stu-id="e8816-103">Link unfurling</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

> [!NOTE]
> <span data-ttu-id="e8816-104">Atualmente, não há suporte para a desesconsição de link em clientes móveis.</span><span class="sxs-lookup"><span data-stu-id="e8816-104">Currently, Link unfurling is not supported on Mobile clients.</span></span>

<span data-ttu-id="e8816-105">Com o link desfraldado, seu aplicativo pode se registrar para receber uma atividade quando URLs com um determinado domínio são colar na `invoke` área de mensagem de composição.</span><span class="sxs-lookup"><span data-stu-id="e8816-105">With link unfurling your app can register to receive an `invoke` activity when URLs with a particular domain are pasted into the compose message area.</span></span> <span data-ttu-id="e8816-106">O conterá a URL completa que foi colar na área de mensagem de redação, e você pode responder com um cartão que o usuário possa desesconelhar, fornecendo informações ou `invoke` ações adicionais. </span><span class="sxs-lookup"><span data-stu-id="e8816-106">The `invoke` will contain the full URL that was pasted into the compose message area, and you can respond with a card the user can *unfurl*, providing additional information or actions.</span></span> <span data-ttu-id="e8816-107">Isso funciona de maneira muito semelhante a um [comando de pesquisa,](~/messaging-extensions/how-to/search-commands/define-search-command.md)com a URL servindo como termo de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="e8816-107">This works very similarly to a [search command](~/messaging-extensions/how-to/search-commands/define-search-command.md), with the URL serving as the search term.</span></span>

<span data-ttu-id="e8816-108">A extensão de mensagens do Azure DevOps usa o link desfralhado para procurar URLs colarem na área de mensagem de composição apontando para um item de trabalho.</span><span class="sxs-lookup"><span data-stu-id="e8816-108">The Azure DevOps messaging extension uses link unfurling to look for URLs pasted into the compose message area pointing to a work item.</span></span> <span data-ttu-id="e8816-109">Na captura de tela abaixo, um usuário pastou uma URL para um item de trabalho no Azure DevOps que a extensão de mensagens foi resolvida em um cartão.</span><span class="sxs-lookup"><span data-stu-id="e8816-109">In the screenshot below, a user has pasted in a URL for a work item in Azure DevOps which the messaging extension has resolved into a card.</span></span>

![Exemplo de desesqueamento de link](~/assets/images/compose-extensions/messagingextensions_linkunfurling.png)

## <a name="add-link-unfurling-to-your-app-manifest"></a><span data-ttu-id="e8816-111">Adicionar link desaplicação ao manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="e8816-111">Add link unfurling to your app manifest</span></span>

 <span data-ttu-id="e8816-112">Para adicionar link desaplicação ao manifesto do aplicativo, adicione uma nova matriz `messageHandlers` à seção do manifesto do aplicativo `composeExtensions` JSON.</span><span class="sxs-lookup"><span data-stu-id="e8816-112">To add link unfurling to your app manifest add a new `messageHandlers` array to the `composeExtensions` section of your app manifest JSON.</span></span> <span data-ttu-id="e8816-113">Você pode adicionar a matriz com a ajuda do App Studio ou manualmente.</span><span class="sxs-lookup"><span data-stu-id="e8816-113">You can add the array either with the help of App Studio or manually.</span></span> <span data-ttu-id="e8816-114">As listagem de domínio podem incluir caracteres curinga, por `*.example.com` exemplo.</span><span class="sxs-lookup"><span data-stu-id="e8816-114">Domain listings can include wildcards, for example `*.example.com`.</span></span> <span data-ttu-id="e8816-115">Isso corresponde a exatamente um segmento do domínio; se você precisar corresponder, `a.b.example.com` use `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="e8816-115">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span>

> [!NOTE]
> <span data-ttu-id="e8816-116">Não adicione domínios que estejam fora do seu controle, diretamente ou por meio de caracteres curinga.</span><span class="sxs-lookup"><span data-stu-id="e8816-116">Do not add domains that are outside your control, either directly or through wildcards.</span></span> <span data-ttu-id="e8816-117">Por exemplo, yourapp.onmicrosoft.com é válido, mas \*.onmicrosoft.com não é válido.</span><span class="sxs-lookup"><span data-stu-id="e8816-117">For example, yourapp.onmicrosoft.com is valid, but \*.onmicrosoft.com is not valid.</span></span> <span data-ttu-id="e8816-118">Além disso, os domínios de nível superior são proibidos.</span><span class="sxs-lookup"><span data-stu-id="e8816-118">Also, the top-level domains are prohibited.</span></span> <span data-ttu-id="e8816-119">Por exemplo, \*.com, \*.org.</span><span class="sxs-lookup"><span data-stu-id="e8816-119">For example, \*.com, \*.org.</span></span>

### <a name="using-app-studio"></a><span data-ttu-id="e8816-120">Usando o aplicativo Studio</span><span class="sxs-lookup"><span data-stu-id="e8816-120">Using App Studio</span></span>

1. <span data-ttu-id="e8816-121">No App Studio, na guia Editor de manifesto, carregue o manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e8816-121">In App Studio, on the Manifest editor tab, load your app manifest.</span></span>
1. <span data-ttu-id="e8816-122">Na página **Extensão de Mensagens,** adicione o domínio  que você deseja procurar na seção Manipuladores de mensagens, como na captura de tela abaixo.</span><span class="sxs-lookup"><span data-stu-id="e8816-122">On the **Messaging Extension** page, add the domain you want to look for in the **Message handlers** section as in the screenshot below.</span></span>

![seção manipuladores de mensagens no App Studio](~/assets/images/link-unfurling.png)

### <a name="manually"></a><span data-ttu-id="e8816-124">Manualmente</span><span class="sxs-lookup"><span data-stu-id="e8816-124">Manually</span></span>

<span data-ttu-id="e8816-125">Para permitir que sua extensão de mensagens interaja com links dessa forma, primeiro você precisará adicionar a matriz ao manifesto do aplicativo, como `messageHandlers` no exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="e8816-125">To enable your messaging extension to interact with links this way you'll first need to add the `messageHandlers` array to your app manifest as in the example below.</span></span> <span data-ttu-id="e8816-126">Este exemplo não é o manifesto completo, consulte a referência [de manifesto](~/resources/schema/manifest-schema.md) para um exemplo de manifesto completo.</span><span class="sxs-lookup"><span data-stu-id="e8816-126">This example is not the complete manifest, see [manifest reference](~/resources/schema/manifest-schema.md) for a complete manifest example.</span></span>

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

## <a name="handle-the-composeextensionquerylink-invoke"></a><span data-ttu-id="e8816-127">Manipular a `composeExtension/queryLink` invocação</span><span class="sxs-lookup"><span data-stu-id="e8816-127">Handle the `composeExtension/queryLink` invoke</span></span>

<span data-ttu-id="e8816-128">Depois de adicionar o domínio para escutar o manifesto do aplicativo, você precisará atualizar o código do serviço Web para manipular a solicitação de invocação.</span><span class="sxs-lookup"><span data-stu-id="e8816-128">Once you've added the domain to listen on to the app manifest, you'll need to update your web service code to handle the invoke request.</span></span> <span data-ttu-id="e8816-129">Use a URL que você recebe para pesquisar seu serviço e criar uma resposta de cartão.</span><span class="sxs-lookup"><span data-stu-id="e8816-129">Use the URL you receive to search your service and create a card response.</span></span> <span data-ttu-id="e8816-130">Se você responder com mais de um cartão, somente o primeiro será usado.</span><span class="sxs-lookup"><span data-stu-id="e8816-130">If you respond with more than one card, only the first will be used.</span></span>

<span data-ttu-id="e8816-131">Damos suporte aos seguintes tipos de cartão:</span><span class="sxs-lookup"><span data-stu-id="e8816-131">We support the following card types:</span></span>

* [<span data-ttu-id="e8816-132">Cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="e8816-132">Thumbnail card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [<span data-ttu-id="e8816-133">Cartão de herói</span><span class="sxs-lookup"><span data-stu-id="e8816-133">Hero card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [<span data-ttu-id="e8816-134">Cartão do Conector do Office 365</span><span class="sxs-lookup"><span data-stu-id="e8816-134">Office 365 Connector card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [<span data-ttu-id="e8816-135">Cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="e8816-135">Adaptive Card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

<span data-ttu-id="e8816-136">Veja [o que são cartões para](~/task-modules-and-cards/what-are-cards.md) ter uma visão geral.</span><span class="sxs-lookup"><span data-stu-id="e8816-136">See [What are cards](~/task-modules-and-cards/what-are-cards.md) for an overview.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="e8816-137">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="e8816-137">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="javascriptnodejs"></a>[<span data-ttu-id="e8816-138">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="e8816-138">JavaScript/Node.js</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="e8816-139">JSON</span><span class="sxs-lookup"><span data-stu-id="e8816-139">JSON</span></span>](#tab/json)

<span data-ttu-id="e8816-140">Este é um exemplo do `invoke` que foi enviado para seu bot.</span><span class="sxs-lookup"><span data-stu-id="e8816-140">This is an example of the `invoke` sent to your bot.</span></span>

```json
{
  "type": "invoke",
  "name": "composeExtension/queryLink",
  "value": {
    "url": "https://theurlsubmittedbyyouruser.trackeddomain.com/id/1234"
  }
}
```

<span data-ttu-id="e8816-141">Um exemplo da resposta é mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="e8816-141">An example of the response is shown below.</span></span>

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
