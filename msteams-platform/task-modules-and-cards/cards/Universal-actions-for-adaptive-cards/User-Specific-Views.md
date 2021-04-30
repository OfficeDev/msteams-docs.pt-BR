---
title: Exibições específicas do usuário
description: Exemplo de exibições específicas do usuário usando ações universais
author: surbhigupta12
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: 984b32511dda544942df11f7c5d8a25cca8e9a8a
ms.sourcegitcommit: 1256639fa424e3833b44207ce847a245824d48e6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2021
ms.locfileid: "52088806"
---
# <a name="user-specific-views"></a><span data-ttu-id="c1e40-103">Exibições específicas do usuário</span><span class="sxs-lookup"><span data-stu-id="c1e40-103">User Specific Views</span></span>

<span data-ttu-id="c1e40-104">Anteriormente, se cartões adaptáveis foram enviados em uma conversa Teams, todos os usuários verão exatamente o mesmo conteúdo do cartão.</span><span class="sxs-lookup"><span data-stu-id="c1e40-104">Earlier if Adaptive Cards was sent in a Teams conversation, all users see the exact same card content.</span></span> <span data-ttu-id="c1e40-105">Com a introdução do modelo de Ações Universais e para Cartões Adaptáveis, os desenvolvedores de bot agora podem fornecer exibições específicas do usuário de cartões `refresh` adaptáveis aos usuários.</span><span class="sxs-lookup"><span data-stu-id="c1e40-105">With the introduction of the Universal Actions model and `refresh` for Adaptive Cards, bot developers can now provide User Specific Views of Adaptive Cards to users.</span></span> <span data-ttu-id="c1e40-106">O mesmo Cartão Adaptável agora pode atualizar para um Cartão Adaptável Específico do Usuário.</span><span class="sxs-lookup"><span data-stu-id="c1e40-106">The same Adaptive Card can now refresh to a User Specific Adaptive Card.</span></span>

<span data-ttu-id="c1e40-107">Por exemplo, Megan, uma inspetora de segurança da Contoso, deseja criar um incidente e atribuí-lo a Alex.</span><span class="sxs-lookup"><span data-stu-id="c1e40-107">For example, Megan, a safety inspector at Contoso, wants to create an incident and assign it to Alex.</span></span> <span data-ttu-id="c1e40-108">Ela também quer que todos na equipe sejam cientes sobre o incidente.</span><span class="sxs-lookup"><span data-stu-id="c1e40-108">She also wants everyone in the team to be aware about the incident.</span></span> <span data-ttu-id="c1e40-109">Megan usa a extensão de mensagem de relatório de incidentes da Contoso alimentada por Ações Universais para Cartões Adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="c1e40-109">Megan uses Contoso incident reporting message extension powered by Universal Actions for Adaptive Cards.</span></span>

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-incident-management.png" alt-text="Exibições específicas do usuário":::

## <a name="user-specific-views-for-adaptive-cards"></a><span data-ttu-id="c1e40-111">Exibições específicas do usuário para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="c1e40-111">User Specific Views for Adaptive Cards</span></span>

<span data-ttu-id="c1e40-112">O código a seguir fornece um exemplo de Cartões Adaptáveis:</span><span class="sxs-lookup"><span data-stu-id="c1e40-112">The following code provides an example of Adaptive Cards:</span></span>

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

<span data-ttu-id="c1e40-113">**Para enviar cartões adaptáveis, atualize exibições específicas do usuário e invoque solicitações ao bot**</span><span class="sxs-lookup"><span data-stu-id="c1e40-113">**To send Adaptive Cards, refresh User Specific Views, and invoke requests to the bot**</span></span>

1. <span data-ttu-id="c1e40-114">Quando Megan cria um novo incidente, o bot envia o Cartão Adaptável ou o cartão comum com detalhes de incidentes na Teams conversa.</span><span class="sxs-lookup"><span data-stu-id="c1e40-114">When Megan creates a new incident, the bot sends the Adaptive Card or common card with incident details in the Teams conversation.</span></span>
2. <span data-ttu-id="c1e40-115">Agora, esse cartão é atualizado automaticamente para o User Specific View para Megan e Alex.</span><span class="sxs-lookup"><span data-stu-id="c1e40-115">Now this card automatically refreshes to User Specific View for Megan and Alex.</span></span> <span data-ttu-id="c1e40-116">Os MRIs de usuário de Alex e Megan são adicionados na propriedade da propriedade `userIds` `refresh` JSON do Cartão Adaptável.</span><span class="sxs-lookup"><span data-stu-id="c1e40-116">Alex's and Megan's user MRIs are added in `userIds` property of `refresh` property of the Adaptive Card JSON.</span></span> <span data-ttu-id="c1e40-117">O cartão permanece o mesmo para outros usuários na conversa.</span><span class="sxs-lookup"><span data-stu-id="c1e40-117">The card remains the same for other users in the conversation.</span></span>
3. <span data-ttu-id="c1e40-118">Para Megan, a atualização automática dispara uma `adaptiveCard/action` solicitação de invocação para o bot.</span><span class="sxs-lookup"><span data-stu-id="c1e40-118">For Megan, automatic refresh triggers an `adaptiveCard/action` invoke request to the bot.</span></span> <span data-ttu-id="c1e40-119">O bot pode retornar um cartão de criador de incidentes com `Edit` um botão como resposta a essa solicitação de invocação.</span><span class="sxs-lookup"><span data-stu-id="c1e40-119">The bot can return an incident creator card with `Edit` button as a response to this invoke request.</span></span>
4. <span data-ttu-id="c1e40-120">Da mesma forma para Alex, a atualização automática dispara outra `adaptiveCard/action` solicitação de invocação para o bot.</span><span class="sxs-lookup"><span data-stu-id="c1e40-120">Similarly for Alex, automatic refresh triggers another `adaptiveCard/action` invoke request to the bot.</span></span> <span data-ttu-id="c1e40-121">O bot pode retornar um botão de cartão de proprietário `Resolve` de incidente como resposta a essa solicitação de invocação.</span><span class="sxs-lookup"><span data-stu-id="c1e40-121">The bot can return an incident owner card `Resolve` button as a response to this invoke request.</span></span>

## <a name="invoke-request-sent-from-teams-client-to-the-bot"></a><span data-ttu-id="c1e40-122">Invocar solicitação enviada Teams cliente para o bot</span><span class="sxs-lookup"><span data-stu-id="c1e40-122">Invoke request sent from Teams client to the bot</span></span>

<span data-ttu-id="c1e40-123">O código a seguir fornece um exemplo de uma solicitação de invocação enviada do cliente Teams Alex e Megan para o bot:</span><span class="sxs-lookup"><span data-stu-id="c1e40-123">The following code provides an example of an invoke request sent from Alex's and Megan's Teams client to the bot:</span></span>

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

## <a name="adaptivecardaction-invoke-response-card"></a><span data-ttu-id="c1e40-124">adaptiveCard/action invoca o cartão de resposta</span><span class="sxs-lookup"><span data-stu-id="c1e40-124">adaptiveCard/action invoke response card</span></span>

<span data-ttu-id="c1e40-125">O código a seguir fornece um exemplo de um cartão de resposta de invocação adaptiveCard/action para Megan:</span><span class="sxs-lookup"><span data-stu-id="c1e40-125">The following code provides an example of an adaptiveCard/action invoke response card for Megan:</span></span>

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

## <a name="adaptivecardaction-invoke-response-card-for-alex"></a><span data-ttu-id="c1e40-126">adaptiveCard/action invocam o cartão de resposta para Alex</span><span class="sxs-lookup"><span data-stu-id="c1e40-126">adaptiveCard/action invoke response card for Alex</span></span>

<span data-ttu-id="c1e40-127">O código a seguir fornece um exemplo de um cartão de resposta de invocação adaptiveCard/action para Alex:</span><span class="sxs-lookup"><span data-stu-id="c1e40-127">The following code provides an example of an adaptiveCard/action invoke response card for Alex:</span></span>

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

## <a name="invoke-response-to-return-adaptive-cards"></a><span data-ttu-id="c1e40-128">Invocar resposta para retornar cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="c1e40-128">Invoke response to return Adaptive Cards</span></span>

<span data-ttu-id="c1e40-129">O código a seguir fornece um exemplo de uma resposta de invocação para retornar Cartões Adaptáveis:</span><span class="sxs-lookup"><span data-stu-id="c1e40-129">The following code provides an example of an invoke response to return Adaptive Cards:</span></span>

```C#
string cardJson = "<adaptive card json>";
var card = JsonConvert.DeserializeObject(cardJson);

var adaptiveCardResponse = JObject.FromObject(new
 {
    statusCode = 200,
    type = "application/vnd.microsoft.card.adaptive",
    value = card
 });
```

<span data-ttu-id="c1e40-130">Diretrizes de design de cartão para ter em mente ao projetar exibições específicas do usuário:</span><span class="sxs-lookup"><span data-stu-id="c1e40-130">Card design guidelines to keep in mind while designing User Specific Views:</span></span>

* <span data-ttu-id="c1e40-131">Você pode criar no máximo **60** Exibições Específicas do Usuário para um cartão específico que está sendo enviado para um chat ou canal especificando-os `userIds` na `refresh` seção.</span><span class="sxs-lookup"><span data-stu-id="c1e40-131">You can create a maximum of **60 User Specific Views** for a particular card being sent to a chat or channel by specifying their `userIds` in the `refresh` section.</span></span>
* <span data-ttu-id="c1e40-132">**Cartão Base:** A versão base do cartão que o desenvolvedor de bot envia para o chat.</span><span class="sxs-lookup"><span data-stu-id="c1e40-132">**Base Card:** The base version of the card that the bot developer sends to the chat.</span></span> <span data-ttu-id="c1e40-133">Esta é a versão do Cartão Adaptável para todos os usuários que não são especificados na `userIds` seção.</span><span class="sxs-lookup"><span data-stu-id="c1e40-133">This is the version of the Adaptive Card for all users who are not specified in the `userIds` section.</span></span>
* <span data-ttu-id="c1e40-134">Uma atualização ou edição de mensagem pode ser usada para atualizar o cartão base e atualizar simultaneamente o Cartão Específico do Usuário.</span><span class="sxs-lookup"><span data-stu-id="c1e40-134">A message update or edit can be used to update the base card and simultaneously refresh the User Specific Card.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1e40-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="c1e40-135">See also</span></span>

* [<span data-ttu-id="c1e40-136">Trabalhar com ações universais para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="c1e40-136">Work with Universal Actions for Adaptive Cards</span></span>](Work-with-universal-actions-for-adaptive-cards.md)
* [<span data-ttu-id="c1e40-137">Exibições atualizadas</span><span class="sxs-lookup"><span data-stu-id="c1e40-137">Up to date views</span></span>](Up-To-Date-Views.md)
