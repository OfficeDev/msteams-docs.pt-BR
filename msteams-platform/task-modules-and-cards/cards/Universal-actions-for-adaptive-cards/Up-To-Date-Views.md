---
title: Exibições atualizadas
description: Exemplo de exibições atualizadas usando o Bot Universal
author: surbhigupta12
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: 2027d07961929fb40e7afc3ee268e1267b235a02
ms.sourcegitcommit: 1256639fa424e3833b44207ce847a245824d48e6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2021
ms.locfileid: "52088811"
---
# <a name="up-to-date-cards"></a><span data-ttu-id="2e352-103">Cartões atualizados</span><span class="sxs-lookup"><span data-stu-id="2e352-103">Up to date cards</span></span>

<span data-ttu-id="2e352-104">Agora você pode fornecer informações mais recentes aos usuários sobre Cartões Adaptáveis com uma combinação de edições de atualização e mensagens Teams.</span><span class="sxs-lookup"><span data-stu-id="2e352-104">You can now provide latest information to your users on Adaptive Cards with a combination of refresh and message edits in Teams.</span></span> <span data-ttu-id="2e352-105">Com isso, você pode atualizar dinamicamente as Exibições Específicas do Usuário para seu estado mais recente, como e quando há uma alteração em seu serviço.</span><span class="sxs-lookup"><span data-stu-id="2e352-105">With this you are able to update the User Specific Views dynamically to its latest state as and when there is a change on your service.</span></span> <span data-ttu-id="2e352-106">Por exemplo, no caso de cartões de gerenciamento de projeto ou de tíquetes, você pode atualizar comentários e o status da tarefa.</span><span class="sxs-lookup"><span data-stu-id="2e352-106">For example, in the case of project management or ticketing cards, you can update comments and the status of the task.</span></span> <span data-ttu-id="2e352-107">Em caso de aprovações, o estado mais recente é refletido, além de fornecer informações e ações diferenciadas.</span><span class="sxs-lookup"><span data-stu-id="2e352-107">In case of approvals the latest state is reflected while also providing differentiated information and actions.</span></span>

<span data-ttu-id="2e352-108">Por exemplo, um usuário pode criar uma solicitação de aprovação de ativo em uma Teams conversa.</span><span class="sxs-lookup"><span data-stu-id="2e352-108">For example, a user can create an asset approval request in a Teams conversation.</span></span> <span data-ttu-id="2e352-109">Alex cria uma solicitação de aprovação e a atribui a Megan e Nestor.</span><span class="sxs-lookup"><span data-stu-id="2e352-109">Alex creates an approval request and assigns it to Megan and Nestor.</span></span> <span data-ttu-id="2e352-110">Veja a seguir as duas partes para criar a solicitação de aprovação:</span><span class="sxs-lookup"><span data-stu-id="2e352-110">The following are the two parts to create the approval request:</span></span>

* <span data-ttu-id="2e352-111">Os Exibições Específicas do Usuário podem ser aproveitados usando `refresh` a propriedade dos Cartões Adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="2e352-111">User Specific Views can be leveraged using the `refresh` property of the Adaptive Cards.</span></span>
<span data-ttu-id="2e352-112">Usar Exibições Específicas do Usuário  pode mostrar um cartão com botões **Aprovar** ou Rejeitar para um conjunto de usuários e mostrar um cartão sem esses botões para outros usuários.</span><span class="sxs-lookup"><span data-stu-id="2e352-112">Using User Specific Views one can show a card with **Approve** or **Reject** buttons to a set of users, and show a card without these buttons to other users.</span></span>

* <span data-ttu-id="2e352-113">Para manter o estado do cartão atualizado sempre, Teams mecanismo de edição de mensagens pode ser aproveitado.</span><span class="sxs-lookup"><span data-stu-id="2e352-113">To keep the card state updated at all times, Teams message edit mechanism can be leveraged.</span></span> <span data-ttu-id="2e352-114">Por exemplo, sempre que houver uma aprovação, o bot pode disparar uma edição de mensagem para todos os usuários.</span><span class="sxs-lookup"><span data-stu-id="2e352-114">For example, each time there is an approval, bot can trigger a message edit to all users.</span></span> <span data-ttu-id="2e352-115">Essa edição de mensagem bot dispara uma solicitação de invocação para todos os usuários de atualização automática, para os quais o bot pode responder com o cartão `adaptiveCard/action` específico do usuário atualizado.</span><span class="sxs-lookup"><span data-stu-id="2e352-115">This bot message edit triggers an `adaptiveCard/action` invoke request for all automatic refresh users, to which the bot can respond with the updated user specific card.</span></span>

<span data-ttu-id="2e352-116">Para obter mais informações, [consulte como fazer uma edição de mensagem de bot](https://docs.microsoft.com/microsoftteams/platform/bots/how-to/update-and-delete-bot-messages?tabs=dotnet#update-cards).</span><span class="sxs-lookup"><span data-stu-id="2e352-116">For more information, see [how to do a bot message edit](https://docs.microsoft.com/microsoftteams/platform/bots/how-to/update-and-delete-bot-messages?tabs=dotnet#update-cards).</span></span>

## <a name="approval-base-card"></a><span data-ttu-id="2e352-117">Cartão base de aprovação</span><span class="sxs-lookup"><span data-stu-id="2e352-117">Approval base card</span></span>

<span data-ttu-id="2e352-118">O código a seguir fornece um exemplo de um cartão base de aprovação:</span><span class="sxs-lookup"><span data-stu-id="2e352-118">The following code provides an example of an approval base card:</span></span>

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "version": "1.4",
  "refresh": {
    "action": {
      "type": "Action.Execute",
      "title": "Refresh",
      "verb": "acceptRejectView"
    },
    "userIds": ["<Megan's user MRI>", "<Nestor's user MRI>"]
  },
  "body": [
    {
      "type": "TextBlock",
      "text": "Asset Request B12"
    },
    {
      "type": "TextBlock",
      "text": "Submitted by **Alex**"
    },
    {
      "type": "TextBlock",
      "text": "Approval pending from **Megan and Nestor**"
    }
  ]
}
```

## <a name="approval-card-with-approve-and-reject-buttons"></a><span data-ttu-id="2e352-119">Cartão de aprovação com botões Aprovar e Rejeitar</span><span class="sxs-lookup"><span data-stu-id="2e352-119">Approval card with Approve and Reject buttons</span></span>

<span data-ttu-id="2e352-120">O código a seguir fornece um exemplo de cartão de aprovação com **botões Aprovar** e **Rejeitar:**</span><span class="sxs-lookup"><span data-stu-id="2e352-120">The following code provides an example of an approval card with **Approve** and **Reject** buttons:</span></span>

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "version": "1.4",
  "refresh": {
    "action": {
      "type": "Action.Execute",
      "title": "Refresh",
      "verb": "acceptRejectView"
    },
    "userIds": ["<Nestor's user MRI>", "<Megan's user MRI>"]
  },
  "body": [
    {
      "type": "TextBlock",
      "text": "Approval Request B12"
    },
    {
      "type": "TextBlock",
      "text": "Submitted by **Alex**"
    },
    {
      "type": "TextBlock",
      "text": "Approval pending from **Megan and Nestor**"
    }
  ],
  "actions": [
    {
      "type": "Action.Execute",
      "title": "Approve",
      "verb": "approve",
      "data": {
            "more info": "<more info>"
      }
    },
    {
      "type": "Action.Execute",
      "title": "Reject",
      "verb": "reject",
      "data": {
            "more info": "<more info>"
      }
    }
  ]
}
```

<span data-ttu-id="2e352-121">A seguir estão as duas funções mostradas aos usuários, dependendo do envolvimento na solicitação de aprovação:</span><span class="sxs-lookup"><span data-stu-id="2e352-121">Following are the two roles that are shown to users depending on their involvement in the approval request:</span></span>

* <span data-ttu-id="2e352-122">Cartão base de aprovação: mostrado para usuários que não fazem parte da lista de aprovadores e ainda não aprovaram ou rejeitaram a solicitação e não fazem parte da lista na propriedade do JSON do Cartão `userIds` `refresh` Adaptável.</span><span class="sxs-lookup"><span data-stu-id="2e352-122">Approval base card: Shown to users who are not part of approvers list and have not yet approved or rejected the request, and are not part of `userIds` list in `refresh` property of the Adaptive Card JSON.</span></span>
* <span data-ttu-id="2e352-123">Cartão de aprovação **com** botões Aprovar ou Rejeitar: mostrado para os usuários que fazem parte da lista de aprovadores e a lista na propriedade do JSON do Cartão  `userIds` `refresh` Adaptável.</span><span class="sxs-lookup"><span data-stu-id="2e352-123">Approval card with **Approve** or **Reject** buttons: Shown to the users who are part of the approvers list and the `userIds` list in the `refresh` property of the Adaptive Card JSON.</span></span>

<span data-ttu-id="2e352-124">**Para enviar a solicitação de aprovação de ativos**</span><span class="sxs-lookup"><span data-stu-id="2e352-124">**To send the asset approval request**</span></span>

1. <span data-ttu-id="2e352-125">Alex levanta uma solicitação de aprovação de ativos em uma Teams e a atribui a Megan e Nestor.</span><span class="sxs-lookup"><span data-stu-id="2e352-125">Alex raises an asset approval request in a Teams conversation and assigns it to Megan and Nestor.</span></span>
2. <span data-ttu-id="2e352-126">Bot envia o cartão base de aprovação na conversa.</span><span class="sxs-lookup"><span data-stu-id="2e352-126">Bot sends the approval base card in the conversation.</span></span>
3. <span data-ttu-id="2e352-127">Todos os outros usuários na conversa veem o cartão enviado pelo bot.</span><span class="sxs-lookup"><span data-stu-id="2e352-127">All other users in the conversation see the card sent by the bot.</span></span> <span data-ttu-id="2e352-128">A atualização automática é disparada para Megan e Nestor, que  agora veem o cartão específico do usuário com os botões **Aprovar** ou Rejeitar como seus MRIs de usuário são adicionados à lista na propriedade do `userIds` Cartão `refresh` Adaptável.</span><span class="sxs-lookup"><span data-stu-id="2e352-128">Automatic refresh is triggered for Megan and Nestor, who now see the user specific card with **Approve** or **Reject** buttons as their user MRIs are added to the `userIds` list in the `refresh` property of the Adaptive Card.</span></span>

    :::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views-1.png" alt-text="Exibições específicas do usuário":::

4. <span data-ttu-id="2e352-130">Nestor seleciona o botão **Aprovar** que é alimentado com `Action.Execute` .</span><span class="sxs-lookup"><span data-stu-id="2e352-130">Nestor selects the **Approve** button which is powered with `Action.Execute`.</span></span> <span data-ttu-id="2e352-131">O bot recebe uma `adaptiveCard/action` solicitação de invocação à qual ele pode retornar um Cartão Adaptável em resposta.</span><span class="sxs-lookup"><span data-stu-id="2e352-131">The bot gets an `adaptiveCard/action` invoke request to which it can return an Adaptive Card in response.</span></span>
5. <span data-ttu-id="2e352-132">O bot dispara uma edição de mensagem com um cartão atualizado que diz que Nestor aprovou a solicitação enquanto a aprovação de Megan está pendente.</span><span class="sxs-lookup"><span data-stu-id="2e352-132">The bot triggers a message edit with an updated card which says Nestor has approved the request while Megan's approval is pending.</span></span>
6. <span data-ttu-id="2e352-133">A edição de mensagem bot dispara uma atualização automática para Megan e ela vê o cartão específico do  usuário atualizado, que diz que Nestor aprovou a solicitação, mas também vê os botões **Aprovar** ou Rejeitar.</span><span class="sxs-lookup"><span data-stu-id="2e352-133">Bot message edit triggers an automatic refresh for Megan and she sees the updated user specific card, which says Nestor has approved the request, but also sees the **Approve** or **Reject** buttons.</span></span> <span data-ttu-id="2e352-134">A MRI do usuário de Nestor é removida da lista na propriedade deste JSON de Cartão Adaptável nas etapas `userIds` `refresh` 4 e 5.</span><span class="sxs-lookup"><span data-stu-id="2e352-134">Nestor's user MRI is removed from the `userIds` list in `refresh` property of this Adaptive Card JSON in steps 4 and 5.</span></span> <span data-ttu-id="2e352-135">Agora, a atualização automática só é disparada para Megan.</span><span class="sxs-lookup"><span data-stu-id="2e352-135">Now, automatic refresh is only triggered for Megan.</span></span>

    :::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views-2.png" alt-text="Exibições específicas do usuário atualizadas":::

7. <span data-ttu-id="2e352-137">Agora, Megan seleciona o **botão Aprovar,** que é alimentado com `Action.Execute` .</span><span class="sxs-lookup"><span data-stu-id="2e352-137">Now, Megan selects the **Approve** button, which is powered with `Action.Execute`.</span></span> <span data-ttu-id="2e352-138">O bot recebe uma `adaptiveCard/action` solicitação de invocação à qual ele pode retornar um Cartão Adaptável em resposta.</span><span class="sxs-lookup"><span data-stu-id="2e352-138">The bot gets an `adaptiveCard/action` invoke request to which it can return an Adaptive Card in response.</span></span>
8. <span data-ttu-id="2e352-139">O bot dispara uma edição de mensagem com um cartão atualizado, que diz que Nestor e Megan aprovaram a solicitação.</span><span class="sxs-lookup"><span data-stu-id="2e352-139">The bot triggers a message edit with an updated card, which says Nestor and Megan have approved the request.</span></span>
9. <span data-ttu-id="2e352-140">A edição da mensagem bot não dispara nenhuma atualização automática.</span><span class="sxs-lookup"><span data-stu-id="2e352-140">Bot message edit does not trigger any automatic refresh.</span></span> <span data-ttu-id="2e352-141">A MRI do usuário de Megan também é removida da lista na propriedade deste JSON de Cartão Adaptável nas etapas `userIds` `refresh` 7 e 8.</span><span class="sxs-lookup"><span data-stu-id="2e352-141">Megan's user MRI is also removed from the `userIds` list in `refresh` property of this Adaptive Card JSON in steps 7 and 8.</span></span>

    :::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views-3.png" alt-text="Exibições atualizadas":::

## <a name="adaptive-card-sent-as-response-of-adaptivecardaction-and-message-edit"></a><span data-ttu-id="2e352-143">Cartão Adaptável enviado como resposta `adaptiveCard/action` de e `message edit`</span><span class="sxs-lookup"><span data-stu-id="2e352-143">Adaptive Card sent as response of `adaptiveCard/action` and `message edit`</span></span>

<span data-ttu-id="2e352-144">O código a seguir fornece um exemplo de Cartões Adaptáveis enviados como resposta e para as `adaptiveCard/action` `message edit` etapas 4 e 5:</span><span class="sxs-lookup"><span data-stu-id="2e352-144">The following code provides an example of Adaptive Cards sent as response of `adaptiveCard/action` and `message edit` for steps 4 and 5:</span></span>

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "version": "1.4",
  "refresh": {
    "action": {
      "type": "Action.Execute",
      "title": "Refresh",
      "verb": "acceptRejectView"
    },
    "userIds": ["<Megan's user MRI>"]
  },
  "body": [
    {
      "type": "TextBlock",
      "text": "Asset Request B12"
    },
    {
      "type": "TextBlock",
      "text": "Submitted by **Alex**"
    },
    {
      "type": "TextBlock",
      "text": "Approval pending from **Megan**"
    },
    {
      "type": "TextBlock",
      "text": "Approved by **Nestor**"
    }
  ]
}
```

<span data-ttu-id="2e352-145">O código a seguir fornece um exemplo de Cartões Adaptáveis enviados como resposta de invocar por meio da atualização automática para a `adaptiveCard/action` etapa 6:</span><span class="sxs-lookup"><span data-stu-id="2e352-145">The following code provides an example of Adaptive Cards sent as response of `adaptiveCard/action` invoke through automatic refresh for step 6:</span></span>

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "version": "1.4",
  "refresh": {
    "action": {
      "type": "Action.Execute",
      "title": "Refresh",
      "verb": "acceptRejectView"
    },
    "userIds": ["<Megan's user MRI>"]
  },
  "body": [
    {
      "type": "TextBlock",
      "text": "Approval Request B12"
    },
    {
      "type": "TextBlock",
      "text": "Submitted by **Alex**"
    },
    {
      "type": "TextBlock",
      "text": "Approval pending from **Megan**"
    },
    {
      "type": "TextBlock",
      "text": "Approved by **Nestor**"
    }
  ],
  "actions": [
    {
      "type": "Action.Execute",
      "title": "Approve",
      "verb": "approve",
      "data": {
            "more info": "<more info>"
      }
    },
    {
      "type": "Action.Execute",
      "title": "Reject",
      "verb": "reject",
      "data": {
            "more info": "<more info>"
      }
    }
  ]
}
```

<span data-ttu-id="2e352-146">O código a seguir fornece um exemplo de Cartões Adaptáveis enviados como resposta e para as `adaptiveCard/action` `message edit` etapas 7 e 8:</span><span class="sxs-lookup"><span data-stu-id="2e352-146">The following code provides an example of Adaptive Cards sent as response of `adaptiveCard/action` and `message edit` for steps 7 and 8:</span></span>

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "version": "1.4",
  "refresh": {
    "action": {
      "type": "Action.Execute",
      "title": "Refresh",
      "verb": "acceptRejectView"
    },
    "userIds": []
  },
  "body": [
    {
      "type": "TextBlock",
      "text": "Asset Request B12"
    },
    {
      "type": "TextBlock",
      "text": "Submitted by **Alex**"
    },
    {
      "type": "TextBlock",
      "text": "Approved by **Nestor and Megan**"
    }
  ]
}
```

## <a name="see-also"></a><span data-ttu-id="2e352-147">Confira também</span><span class="sxs-lookup"><span data-stu-id="2e352-147">See also</span></span>

* [<span data-ttu-id="2e352-148">Trabalhar com ações universais para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="2e352-148">Work with Universal Actions for Adaptive Cards</span></span>](Work-with-universal-actions-for-adaptive-cards.md)
* [<span data-ttu-id="2e352-149">Exibições específicas do usuário</span><span class="sxs-lookup"><span data-stu-id="2e352-149">User Specific Views</span></span>](User-Specific-Views.md)
