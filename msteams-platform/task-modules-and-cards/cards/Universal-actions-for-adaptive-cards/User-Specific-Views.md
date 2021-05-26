---
title: Exibições Específicas do Usuário
description: Exemplo de exibições específicas do usuário usando ações universais
author: surbhigupta12
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: cadf66082582cfd9009a0497b3eb5e58f0a2ef02
ms.sourcegitcommit: 999f5c607671e088ea8a461fa7dbb63f8d61c39b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2021
ms.locfileid: "52649619"
---
# <a name="user-specific-views"></a><span data-ttu-id="57ef7-103">Exibições Específicas do Usuário</span><span class="sxs-lookup"><span data-stu-id="57ef7-103">User Specific Views</span></span>

<span data-ttu-id="57ef7-104">Anteriormente, se cartões adaptáveis foram enviados em uma conversa Teams, todos os usuários verão exatamente o mesmo conteúdo do cartão.</span><span class="sxs-lookup"><span data-stu-id="57ef7-104">Earlier if Adaptive Cards was sent in a Teams conversation, all users see the exact same card content.</span></span> <span data-ttu-id="57ef7-105">Com a introdução do modelo de Ações Universais e para Cartões Adaptáveis, os desenvolvedores de bot agora podem fornecer exibições específicas do usuário de cartões `refresh` adaptáveis aos usuários.</span><span class="sxs-lookup"><span data-stu-id="57ef7-105">With the introduction of the Universal Actions model and `refresh` for Adaptive Cards, bot developers can now provide User Specific Views of Adaptive Cards to users.</span></span> <span data-ttu-id="57ef7-106">O mesmo Cartão Adaptável agora pode atualizar para um Cartão Adaptável Específico do Usuário.</span><span class="sxs-lookup"><span data-stu-id="57ef7-106">The same Adaptive Card can now refresh to a User Specific Adaptive Card.</span></span>

<span data-ttu-id="57ef7-107">Por exemplo, Megan, uma inspetora de segurança da Contoso, deseja criar um incidente e atribuí-lo a Alex.</span><span class="sxs-lookup"><span data-stu-id="57ef7-107">For example, Megan, a safety inspector at Contoso, wants to create an incident and assign it to Alex.</span></span> <span data-ttu-id="57ef7-108">Ela também quer que todos na equipe sejam cientes sobre o incidente.</span><span class="sxs-lookup"><span data-stu-id="57ef7-108">She also wants everyone in the team to be aware about the incident.</span></span> <span data-ttu-id="57ef7-109">Megan usa a extensão de mensagem de relatório de incidentes da Contoso alimentada por Ações Universais para Cartões Adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="57ef7-109">Megan uses Contoso incident reporting message extension powered by Universal Actions for Adaptive Cards.</span></span>

# <a name="mobile"></a>[<span data-ttu-id="57ef7-110">Mobile</span><span class="sxs-lookup"><span data-stu-id="57ef7-110">Mobile</span></span>](#tab/mobile)

:::image type="content" source="~/assets/images/adaptive-cards/mobile-universal-bots-incident-management.jpg" alt-text="Exibições específicas do usuário móvel":::

# <a name="desktop"></a>[<span data-ttu-id="57ef7-112">Desktop</span><span class="sxs-lookup"><span data-stu-id="57ef7-112">Desktop</span></span>](#tab/desktop)

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-incident-management.png" alt-text="Exibições Específicas do Usuário":::

* * *

## <a name="user-specific-views-for-adaptive-cards"></a><span data-ttu-id="57ef7-114">Exibições específicas do usuário para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="57ef7-114">User Specific Views for Adaptive Cards</span></span>

<span data-ttu-id="57ef7-115">O código a seguir fornece um exemplo de Cartões Adaptáveis:</span><span class="sxs-lookup"><span data-stu-id="57ef7-115">The following code provides an example of Adaptive Cards:</span></span>

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "originator":"c9b4352b-a76b-43b9-88ff-80edddaa243b",
  "version": "1.4",
  "refresh": {
    "action": {
      "type": "Action.Execute",
      "title": "Refresh",
      "verb": "editOrResolveView",
      "data": {
              "refresh info": "<refresh info>"
    },
    "userIds": ["<Megan's user MRI>", "<Alex's user MRI>"]
  },
  "body": [
    {
      "type": "TextBlock",
      "text": "Incident 1234"
    },
    {
      "type": "TextBlock",
      "text": "Incident details: <incident details>"
    }
  ]
}
```

<span data-ttu-id="57ef7-116">**Para enviar cartões adaptáveis, atualize exibições específicas do usuário e invoque solicitações ao bot**</span><span class="sxs-lookup"><span data-stu-id="57ef7-116">**To send Adaptive Cards, refresh User Specific Views, and invoke requests to the bot**</span></span>

1. <span data-ttu-id="57ef7-117">Quando Megan cria um novo incidente, o bot envia o Cartão Adaptável ou o cartão comum com detalhes de incidentes na Teams conversa.</span><span class="sxs-lookup"><span data-stu-id="57ef7-117">When Megan creates a new incident, the bot sends the Adaptive Card or common card with incident details in the Teams conversation.</span></span>
2. <span data-ttu-id="57ef7-118">Agora, esse cartão é atualizado automaticamente para o User Specific View para Megan e Alex.</span><span class="sxs-lookup"><span data-stu-id="57ef7-118">Now this card automatically refreshes to User Specific View for Megan and Alex.</span></span> <span data-ttu-id="57ef7-119">Os MRIs de usuário de Alex e Megan são adicionados na propriedade da propriedade `userIds` `refresh` JSON do Cartão Adaptável.</span><span class="sxs-lookup"><span data-stu-id="57ef7-119">Alex's and Megan's user MRIs are added in `userIds` property of `refresh` property of the Adaptive Card JSON.</span></span> <span data-ttu-id="57ef7-120">O cartão permanece o mesmo para outros usuários na conversa.</span><span class="sxs-lookup"><span data-stu-id="57ef7-120">The card remains the same for other users in the conversation.</span></span>
3. <span data-ttu-id="57ef7-121">Para Megan, a atualização automática dispara uma `adaptiveCard/action` solicitação de invocação para o bot.</span><span class="sxs-lookup"><span data-stu-id="57ef7-121">For Megan, automatic refresh triggers an `adaptiveCard/action` invoke request to the bot.</span></span> <span data-ttu-id="57ef7-122">O bot pode retornar um cartão de criador de incidentes com `Edit` um botão como resposta a essa solicitação de invocação.</span><span class="sxs-lookup"><span data-stu-id="57ef7-122">The bot can return an incident creator card with `Edit` button as a response to this invoke request.</span></span>
4. <span data-ttu-id="57ef7-123">Da mesma forma para Alex, a atualização automática dispara outra `adaptiveCard/action` solicitação de invocação para o bot.</span><span class="sxs-lookup"><span data-stu-id="57ef7-123">Similarly for Alex, automatic refresh triggers another `adaptiveCard/action` invoke request to the bot.</span></span> <span data-ttu-id="57ef7-124">O bot pode retornar um botão de cartão de proprietário `Resolve` de incidente como resposta a essa solicitação de invocação.</span><span class="sxs-lookup"><span data-stu-id="57ef7-124">The bot can return an incident owner card `Resolve` button as a response to this invoke request.</span></span>

## <a name="invoke-request-sent-from-teams-client-to-the-bot"></a><span data-ttu-id="57ef7-125">Invocar solicitação enviada Teams cliente para o bot</span><span class="sxs-lookup"><span data-stu-id="57ef7-125">Invoke request sent from Teams client to the bot</span></span>

<span data-ttu-id="57ef7-126">O código a seguir fornece um exemplo de uma solicitação de invocação enviada do cliente Teams Alex e Megan para o bot:</span><span class="sxs-lookup"><span data-stu-id="57ef7-126">The following code provides an example of an invoke request sent from Alex's and Megan's Teams client to the bot:</span></span>

```JSON
{ 
  "type": "invoke",
  "name": "adaptiveCard/action",

  // ... other properties omitted for brevity

  "value": { 
    "action": { 
      "type": "Action.Execute", 
      "id": "", 
      "verb": "editOrResolveView",
      "data": { 
            "refresh info": "<refresh info>"
      } 
    },
    "trigger": "automatic" 
  }
}
```

## <a name="adaptivecardaction-invoke-response-card"></a><span data-ttu-id="57ef7-127">adaptiveCard/action invoca o cartão de resposta</span><span class="sxs-lookup"><span data-stu-id="57ef7-127">adaptiveCard/action invoke response card</span></span>

<span data-ttu-id="57ef7-128">O código a seguir fornece um exemplo de um cartão de resposta de invocação adaptiveCard/action para Megan:</span><span class="sxs-lookup"><span data-stu-id="57ef7-128">The following code provides an example of an adaptiveCard/action invoke response card for Megan:</span></span>

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "originator":"c9b4352b-a76b-43b9-88ff-80edddaa243b",
  "version": "1.4",
  "refresh": {
    "action": {
      "type": "Action.Execute",
      "title": "Refresh",
      "verb": "editOrResolveView"
    },
    "userIds": ["<Megan's user MRI>", "<Alex's user MRI>"]
  },
  "body": [
    {
      "type": "TextBlock",
      "text": "Incident 1234"
    },
    {
      "type": "TextBlock",
      "text": "Incident details: <incident details>"
    }
  ],
  "actions": [
    {
      "type": "Action.Execute",
      "title": "Edit",
      "verb": "edit",
      "data": {
            "additional info": "<additional info>",
            ...
      }
    }
  ]
}
```

## <a name="adaptivecardaction-invoke-response-card-for-alex"></a><span data-ttu-id="57ef7-129">adaptiveCard/action invocam o cartão de resposta para Alex</span><span class="sxs-lookup"><span data-stu-id="57ef7-129">adaptiveCard/action invoke response card for Alex</span></span>

<span data-ttu-id="57ef7-130">O código a seguir fornece um exemplo de um cartão de resposta de invocação adaptiveCard/action para Alex:</span><span class="sxs-lookup"><span data-stu-id="57ef7-130">The following code provides an example of an adaptiveCard/action invoke response card for Alex:</span></span>

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "originator":"c9b4352b-a76b-43b9-88ff-80edddaa243b",
  "version": "1.4",
  "refresh": {
    "action": {
      "type": "Action.Execute",
      "title": "Refresh",
      "verb": "editOrResolveView"
    },
    "userIds": ["<Megan's user MRI>", "<Alex's user MRI>"]
  },
  "body": [
    {
      "type": "TextBlock",
      "text": "Incident 1234"
    },
    {
      "type": "TextBlock",
      "text": "Incident details: <incident details>"
    }
  ],
  "actions": [
    {
      "type": "Action.Execute",
      "title": "Resolve",
      "verb": "resolve",
      "data": {
            "additional info": "<additional info>",
            ...
      }
    }
  ]
}
```

## <a name="invoke-response-to-return-adaptive-cards"></a><span data-ttu-id="57ef7-131">Invocar resposta para retornar cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="57ef7-131">Invoke response to return Adaptive Cards</span></span>

<span data-ttu-id="57ef7-132">O código a seguir fornece um exemplo de uma resposta de invocação para retornar Cartões Adaptáveis:</span><span class="sxs-lookup"><span data-stu-id="57ef7-132">The following code provides an example of an invoke response to return Adaptive Cards:</span></span>

```C#
string cardJson = "<adaptive card json>";
var card = JsonConvert.DeserializeObject(cardJson);

var adaptiveCardResponse = JObject.FromObject(new
 {
    statusCode = 200,
    type = "application/vnd.microsoft.adaptive.card",
    value = card
 });
```

<span data-ttu-id="57ef7-133">Diretrizes de design de cartão para ter em mente ao projetar exibições específicas do usuário:</span><span class="sxs-lookup"><span data-stu-id="57ef7-133">Card design guidelines to keep in mind while designing User Specific Views:</span></span>

* <span data-ttu-id="57ef7-134">Você pode criar no máximo **60** Exibições Específicas do Usuário para um cartão específico que está sendo enviado para um chat ou canal especificando-os `userIds` na `refresh` seção.</span><span class="sxs-lookup"><span data-stu-id="57ef7-134">You can create a maximum of **60 User Specific Views** for a particular card being sent to a chat or channel by specifying their `userIds` in the `refresh` section.</span></span>
* <span data-ttu-id="57ef7-135">**Cartão Base:** A versão base do cartão que o desenvolvedor de bot envia para o chat.</span><span class="sxs-lookup"><span data-stu-id="57ef7-135">**Base Card:** The base version of the card that the bot developer sends to the chat.</span></span> <span data-ttu-id="57ef7-136">Esta é a versão do Cartão Adaptável para todos os usuários que não são especificados na `userIds` seção.</span><span class="sxs-lookup"><span data-stu-id="57ef7-136">This is the version of the Adaptive Card for all users who are not specified in the `userIds` section.</span></span>
* <span data-ttu-id="57ef7-137">Uma atualização ou edição de mensagem pode ser usada para atualizar o cartão base e atualizar simultaneamente o Cartão Específico do Usuário.</span><span class="sxs-lookup"><span data-stu-id="57ef7-137">A message update or edit can be used to update the base card and simultaneously refresh the User Specific Card.</span></span>

## <a name="see-also"></a><span data-ttu-id="57ef7-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="57ef7-138">See also</span></span>

* [<span data-ttu-id="57ef7-139">Trabalhar com Ações Universais para Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="57ef7-139">Work with Universal Actions for Adaptive Cards</span></span>](Work-with-universal-actions-for-adaptive-cards.md)
* [<span data-ttu-id="57ef7-140">Exibições atualizadas</span><span class="sxs-lookup"><span data-stu-id="57ef7-140">Up to date views</span></span>](Up-To-Date-Views.md)
