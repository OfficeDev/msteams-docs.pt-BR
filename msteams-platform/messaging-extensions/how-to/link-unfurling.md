---
title: Desenrolamento de link
author: surbhigupta
description: Como executar o link desfraldamento com a extensão de mensagens em um Microsoft Teams aplicativo.
localization_priority: Normal
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 7713fe794c9d15453438cfe3e1bde0238bde9d8c
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2021
ms.locfileid: "53068948"
---
# <a name="link-unfurling"></a><span data-ttu-id="a74d2-103">Desenrolamento de link</span><span class="sxs-lookup"><span data-stu-id="a74d2-103">Link unfurling</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

<span data-ttu-id="a74d2-104">Este documento orienta você sobre como adicionar link desfraldado ao manifesto do aplicativo usando o App studio e manualmente.</span><span class="sxs-lookup"><span data-stu-id="a74d2-104">This document guides you on how to add link unfurling to your app manifest using App studio and manually.</span></span> <span data-ttu-id="a74d2-105">Com o desenrolamento do link, seu aplicativo pode se registrar para receber uma atividade `invoke` quando URLs com um domínio específico são coladas na área de composição de mensagem.</span><span class="sxs-lookup"><span data-stu-id="a74d2-105">With link unfurling your app can register to receive an `invoke` activity when URLs with a particular domain are pasted into the compose message area.</span></span> <span data-ttu-id="a74d2-106">O contém a URL completa que foi colar na área de mensagem de composição e você pode responder com um cartão que o usuário pode desafraldar, fornecendo informações ou `invoke` ações adicionais.</span><span class="sxs-lookup"><span data-stu-id="a74d2-106">The `invoke` contains the full URL that was pasted into the compose message area, and you can respond with a card that the user can unfurl, providing additional information or actions.</span></span> <span data-ttu-id="a74d2-107">Isso funciona de forma semelhante a um comando de pesquisa com a URL servindo como o termo de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="a74d2-107">This works similar to a search command with the URL serving as the search term.</span></span>

> [!NOTE]
> * <span data-ttu-id="a74d2-108">Atualmente, não há suporte para a desalinização de link em clientes Móveis.</span><span class="sxs-lookup"><span data-stu-id="a74d2-108">Currently, link unfurling is not supported on Mobile clients.</span></span>
> * <span data-ttu-id="a74d2-109">O resultado de desfralização do link é armazenado em cache por 30 minutos.</span><span class="sxs-lookup"><span data-stu-id="a74d2-109">The link unfurling result is cached for 30 minutes.</span></span>

<span data-ttu-id="a74d2-110">A Azure DevOps de mensagens usa o link desfraldamento para procurar URLs colaram na área de mensagem de composição apontando para um item de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a74d2-110">The Azure DevOps messaging extension uses link unfurling to look for URLs pasted into the compose message area pointing to a work item.</span></span> <span data-ttu-id="a74d2-111">Na imagem a seguir, um usuário pastou uma URL para um item de trabalho no Azure DevOps, que a extensão de mensagens resolveu em um cartão:</span><span class="sxs-lookup"><span data-stu-id="a74d2-111">In the following image, a user has pasted a URL for a work item in Azure DevOps, which the messaging extension has resolved into a card:</span></span>

![Exemplo de desfraldamento de link](~/assets/images/compose-extensions/messagingextensions_linkunfurling.png)

## <a name="add-link-unfurling-to-your-app-manifest"></a><span data-ttu-id="a74d2-113">Adicionar a desaplicação de link ao manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="a74d2-113">Add link unfurling to your app manifest</span></span>

<span data-ttu-id="a74d2-114">Para adicionar a desaplicação de link ao manifesto do aplicativo, adicione uma nova matriz à seção `messageHandlers` `composeExtensions` do manifesto JSON do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a74d2-114">To add link unfurling to your app manifest, add a new `messageHandlers` array to the `composeExtensions` section of your app manifest JSON.</span></span> <span data-ttu-id="a74d2-115">Você pode adicionar a matriz com a ajuda do App Studio ou manualmente.</span><span class="sxs-lookup"><span data-stu-id="a74d2-115">You can add the array either with the help of App Studio or manually.</span></span> <span data-ttu-id="a74d2-116">Listagem de domínio pode incluir caracteres curinga, por exemplo `*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="a74d2-116">Domain listings can include wildcards, for example `*.example.com`.</span></span> <span data-ttu-id="a74d2-117">Isso corresponde a exatamente um segmento do domínio; se você precisar corresponder, `a.b.example.com` use `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="a74d2-117">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span>

> [!NOTE]
> <span data-ttu-id="a74d2-118">Não adicione domínios que não estão em seu controle, diretamente ou por meio de caracteres curinga.</span><span class="sxs-lookup"><span data-stu-id="a74d2-118">Donot add domains that are not in your control, either directly or through wildcards.</span></span> <span data-ttu-id="a74d2-119">Por exemplo, `yourapp.onmicrosoft.com` é válido, mas `*.onmicrosoft.com` não é válido.</span><span class="sxs-lookup"><span data-stu-id="a74d2-119">For example, `yourapp.onmicrosoft.com` is valid, but `*.onmicrosoft.com` is not valid.</span></span> <span data-ttu-id="a74d2-120">Além disso, os domínios de nível superior são proibidos.</span><span class="sxs-lookup"><span data-stu-id="a74d2-120">Also, the top-level domains are prohibited.</span></span> <span data-ttu-id="a74d2-121">Por exemplo, `*.com` , `*.org` .</span><span class="sxs-lookup"><span data-stu-id="a74d2-121">For example, `*.com`, `*.org`.</span></span>

### <a name="add-link-unfurling-using-app-studio"></a><span data-ttu-id="a74d2-122">Adicionar link desfraldamento usando o App Studio</span><span class="sxs-lookup"><span data-stu-id="a74d2-122">Add link unfurling using App Studio</span></span>

1. <span data-ttu-id="a74d2-123">Abra **o App Studio** no cliente Microsoft Teams e selecione a guia Editor **de** Manifesto.</span><span class="sxs-lookup"><span data-stu-id="a74d2-123">Open **App Studio** from the Microsoft Teams client, and select the **Manifest Editor** tab.</span></span>
1. <span data-ttu-id="a74d2-124">Carregue o manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a74d2-124">Load your app manifest.</span></span>
1. <span data-ttu-id="a74d2-125">Na página **Extensão de Mensagens,** adicione o domínio que você deseja procurar na seção **Manipuladores de** mensagens.</span><span class="sxs-lookup"><span data-stu-id="a74d2-125">On the **Messaging Extension** page, add the domain that you want to look for in the **Message handlers** section.</span></span> <span data-ttu-id="a74d2-126">A imagem a seguir explica o processo:</span><span class="sxs-lookup"><span data-stu-id="a74d2-126">The following image explains the process:</span></span>

    ![seção manipuladores de mensagens no App Studio](~/assets/images/link-unfurling.png)
    
### <a name="add-link-unfurling-manually"></a><span data-ttu-id="a74d2-128">Adicionar link desfraldamento manualmente</span><span class="sxs-lookup"><span data-stu-id="a74d2-128">Add link unfurling manually</span></span>

<span data-ttu-id="a74d2-129">Para permitir que sua extensão de mensagens interaja com links, primeiro você deve adicionar a `messageHandlers` matriz ao manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a74d2-129">To enable your messaging extension to interact with links, first you must add the `messageHandlers` array to your app manifest.</span></span> <span data-ttu-id="a74d2-130">O exemplo a seguir explica como adicionar o link desfraldamento manualmente:</span><span class="sxs-lookup"><span data-stu-id="a74d2-130">The following example explains how to add link unfurling manually:</span></span> 


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

<span data-ttu-id="a74d2-131">Para um exemplo de manifesto completo, consulte [referência de manifesto](~/resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="a74d2-131">For a complete manifest example, see [manifest reference](~/resources/schema/manifest-schema.md).</span></span>

## <a name="handle-the-composeextensionquerylink-invoke"></a><span data-ttu-id="a74d2-132">Manipular a `composeExtension/queryLink` invocação</span><span class="sxs-lookup"><span data-stu-id="a74d2-132">Handle the `composeExtension/queryLink` invoke</span></span>

<span data-ttu-id="a74d2-133">Depois de adicionar o domínio ao manifesto do aplicativo, você deve atualizar seu código de serviço Web para manipular a solicitação de invocação.</span><span class="sxs-lookup"><span data-stu-id="a74d2-133">After adding the domain to the app manifest, you must update your web service code to handle the invoke request.</span></span> <span data-ttu-id="a74d2-134">Use a URL recebida para pesquisar seu serviço e criar uma resposta de cartão.</span><span class="sxs-lookup"><span data-stu-id="a74d2-134">Use the received URL to search your service and create a card response.</span></span> <span data-ttu-id="a74d2-135">Se você responder com mais de um cartão, somente a resposta do primeiro cartão será usada.</span><span class="sxs-lookup"><span data-stu-id="a74d2-135">If you respond with more than one card, only the first card response is used.</span></span>

<span data-ttu-id="a74d2-136">Os seguintes tipos de cartão são suportados:</span><span class="sxs-lookup"><span data-stu-id="a74d2-136">The following card types are supported:</span></span>

* [<span data-ttu-id="a74d2-137">Cartão de miniatura</span><span class="sxs-lookup"><span data-stu-id="a74d2-137">Thumbnail card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [<span data-ttu-id="a74d2-138">Cartão de herói</span><span class="sxs-lookup"><span data-stu-id="a74d2-138">Hero card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [<span data-ttu-id="a74d2-139">Office 365 Cartão conector</span><span class="sxs-lookup"><span data-stu-id="a74d2-139">Office 365 Connector card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [<span data-ttu-id="a74d2-140">Cartão Adaptável</span><span class="sxs-lookup"><span data-stu-id="a74d2-140">Adaptive Card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

### <a name="example"></a><span data-ttu-id="a74d2-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a74d2-141">Example</span></span>

# <a name="cnet"></a>[<span data-ttu-id="a74d2-142">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="a74d2-142">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="javascriptnodejs"></a>[<span data-ttu-id="a74d2-143">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="a74d2-143">JavaScript/Node.js</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="a74d2-144">JSON</span><span class="sxs-lookup"><span data-stu-id="a74d2-144">JSON</span></span>](#tab/json)

<span data-ttu-id="a74d2-145">A seguir está um exemplo do `invoke` enviado para seu bot:</span><span class="sxs-lookup"><span data-stu-id="a74d2-145">Following is an example of the `invoke` sent to your bot:</span></span>

```json
{
  "type": "invoke",
  "name": "composeExtension/queryLink",
  "value": {
    "url": "https://theurlsubmittedbyyouruser.trackeddomain.com/id/1234"
  }
}
```

<span data-ttu-id="a74d2-146">A seguir está um exemplo da resposta:</span><span class="sxs-lookup"><span data-stu-id="a74d2-146">Following is an example of the response:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a74d2-147">Confira também</span><span class="sxs-lookup"><span data-stu-id="a74d2-147">See also</span></span> 

* [<span data-ttu-id="a74d2-148">Cartões</span><span class="sxs-lookup"><span data-stu-id="a74d2-148">Cards</span></span>](~/task-modules-and-cards/what-are-cards.md)
* [<span data-ttu-id="a74d2-149">Link de guias desdobradas e Exibição de Estágio</span><span class="sxs-lookup"><span data-stu-id="a74d2-149">Tabs link unfurling and Stage View</span></span>](~/tabs/tabs-link-unfurling.md)
