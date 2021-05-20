---
title: Fluxos de Trabalho Sequenciais
description: Amostra para fluxos de trabalho sequenciais usando ações universais
author: surbhigupta12
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: 7f285bf76aac4f0ca276321aee2ce4b4e5c3e7e4
ms.sourcegitcommit: 9ef3b415cbba484c2201abe9c6927e08d974388e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52555399"
---
# <a name="sequential-workflows"></a><span data-ttu-id="d9ff7-103">Fluxos de Trabalho Sequenciais</span><span class="sxs-lookup"><span data-stu-id="d9ff7-103">Sequential Workflows</span></span>

<span data-ttu-id="d9ff7-104">Cartões adaptativos agora suportam fluxos de trabalho sequenciais que é quando cartões adaptativos são atualizados sobre a ação do usuário e o usuário pode progredir através de uma série de cartões que requerem a entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="d9ff7-104">Adaptive Cards now support Sequential Workflows that is when Adaptive Cards are updated on user action and user can progress through a series of cards that require user input.</span></span> <span data-ttu-id="d9ff7-105">Isso é suportado através `Action.Execute` de , o que permite que os desenvolvedores de bots retornem Cartões Adaptativos em resposta a uma ação do usuário.</span><span class="sxs-lookup"><span data-stu-id="d9ff7-105">This is supported through `Action.Execute`, which allows bot developers to return Adaptive Cards in response to a user action.</span></span>

<span data-ttu-id="d9ff7-106">Por exemplo, tome um cenário onde o refeitório quer pegar um pedido para uma equipe ou canal.</span><span class="sxs-lookup"><span data-stu-id="d9ff7-106">For example, take a scenario where the cafeteria wants to take an order for a team or channel.</span></span> <span data-ttu-id="d9ff7-107">Com `Action.Execute` a escolha do usuário para vários itens, como alimentos, bebidas, e assim por diante pode ser registrado sequencialmente.</span><span class="sxs-lookup"><span data-stu-id="d9ff7-107">With `Action.Execute` the user's choice for various items, such as food, drinks, and so on can be recorded sequentially.</span></span> <span data-ttu-id="d9ff7-108">O usuário também pode ir e voltar através das cartas de acordo com a lógica definida pelo desenvolvedor de bots.</span><span class="sxs-lookup"><span data-stu-id="d9ff7-108">User can also go back and forth through the cards as per the logic defined by the bot developer.</span></span> <br/>

<span data-ttu-id="d9ff7-109">A imagem a seguir mostra o fluxo de trabalho sequencial:</span><span class="sxs-lookup"><span data-stu-id="d9ff7-109">The following image shows the Sequential Workflow:</span></span>

<img src="~/assets/images/bots/sequentialWorkflow.gif" alt="Sequential Workflow" width="400"/>

<span data-ttu-id="d9ff7-110">Um usuário pode progredir através de seu fluxo de trabalho sem modificar o cartão para outros usuários.</span><span class="sxs-lookup"><span data-stu-id="d9ff7-110">A user can progress through their workflow without modifying the card for other users.</span></span> <span data-ttu-id="d9ff7-111">Isso também é útil para a realização de testes usando cartões adaptativos sequenciais.</span><span class="sxs-lookup"><span data-stu-id="d9ff7-111">This is also useful for conducting quizzes using sequential Adaptive Cards.</span></span> <span data-ttu-id="d9ff7-112">Como mostrado na imagem a seguir, diferentes usuários podem estar em diferentes estágios do fluxo de trabalho e vêem diferentes estados do cartão:</span><span class="sxs-lookup"><span data-stu-id="d9ff7-112">As shown in the following image, different users can be at different stages of the workflow and they see different states of the card:</span></span>

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-catering-bot.png" alt-text="Estados de bot de bufê":::

> [!NOTE]
> <span data-ttu-id="d9ff7-114">Para sincronizar o progresso do usuário entre os dispositivos, use a `refresh` propriedade em Adaptive Card JSON.</span><span class="sxs-lookup"><span data-stu-id="d9ff7-114">In order to sync the user's progress across devices, use the `refresh` property in Adaptive Card JSON.</span></span>

## <a name="sequential-workflow-for-adaptive-cards"></a><span data-ttu-id="d9ff7-115">Fluxo de trabalho sequencial para cartões adaptativos</span><span class="sxs-lookup"><span data-stu-id="d9ff7-115">Sequential Workflow for Adaptive Cards</span></span>

<span data-ttu-id="d9ff7-116">O código a seguir fornece um exemplo de Cartões Adaptativos:</span><span class="sxs-lookup"><span data-stu-id="d9ff7-116">The following code provides an example of Adaptive Cards:</span></span>

```JSON
{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "version": "1.4",
  "body": [
    {
      "type": "TextBlock",
      "text": "Select from food options"
    },
    { 
      "type": "ActionSet",
      "actions": [
        {
          "type": "Action.Execute",
          "title": "Chicken",
          "verb": "food",
          "data": {
              "item": "chicken"
          }
        },
        {
          "type": "Action.Execute",
          "title": "Beef",
          "verb": "food",
          "data": {
              "item": "beef"
          }
        },
        {
          "type": "Action.Execute",
          "title": "Vegan",
          "verb": "food",
          "data": {
              "item": "vegan"
          }
        }
      ]
    }
  ]
}
```

<span data-ttu-id="d9ff7-117">`Action.Execute`invocar o bot pode retornar Cartões Adaptativos como uma resposta, que substitui a placa existente em Teams.</span><span class="sxs-lookup"><span data-stu-id="d9ff7-117">`Action.Execute` invoking the bot can return Adaptive Cards as a response, which replaces the existing card in Teams.</span></span>
<span data-ttu-id="d9ff7-118">O exemplo a seguir fornece o que o bot retorna na seleção de alimentos ou bebidas ou confirmação do pedido:</span><span class="sxs-lookup"><span data-stu-id="d9ff7-118">The following example provides what the bot returns on food or drink selection or order confirmation:</span></span>

* <span data-ttu-id="d9ff7-119">Na seleção de alimentos do Cartão 1, o bot pode devolver um cartão para seleção de bebidas que é o Cartão 2.</span><span class="sxs-lookup"><span data-stu-id="d9ff7-119">On food selection from Card 1, bot can return a card for selection of drinks that is Card 2.</span></span>
* <span data-ttu-id="d9ff7-120">Na seleção de bebidas do Cartão 2, o bot pode devolver um cartão de confirmação de pedido que é o Cartão 3.</span><span class="sxs-lookup"><span data-stu-id="d9ff7-120">On drink selection from Card 2, bot can return an order confirmation card that is Card 3.</span></span>
* <span data-ttu-id="d9ff7-121">Na confirmação do pedido do Cartão 3, o bot pode retornar um cartão confirmado por ordem que é o Cartão 4.</span><span class="sxs-lookup"><span data-stu-id="d9ff7-121">On order confirmation from Card 3, bot can return an order confirmed card that is Card 4.</span></span>

## <a name="invoke-request-received-on-bot-side"></a><span data-ttu-id="d9ff7-122">Invocar solicitação recebida no lado do bot</span><span class="sxs-lookup"><span data-stu-id="d9ff7-122">Invoke request received on bot side</span></span>

<span data-ttu-id="d9ff7-123">O código a seguir fornece um exemplo de uma solicitação de invocação recebida no lado do bot:</span><span class="sxs-lookup"><span data-stu-id="d9ff7-123">The following code provides an example of an invoke request received on bot side:</span></span>

```JSON
{ 
  "type": "invoke",
  "name": "adaptiveCard/action",

  // ... other properties omitted for brevity

  "value": { 
    "action": { 
      "type": "Action.Execute", 
      "id": "", 
      "verb": "food",
      "data": { 
            "item": "vegan"
      } 
    },
    "trigger": "manual" 
  }
}
```

## <a name="invoke-response-to-return-adaptive-cards"></a><span data-ttu-id="d9ff7-124">Invoque a resposta para retornar cartões adaptativos</span><span class="sxs-lookup"><span data-stu-id="d9ff7-124">Invoke response to return Adaptive Cards</span></span>

<span data-ttu-id="d9ff7-125">O código a seguir fornece um exemplo de uma resposta de invocação para retornar cartões adaptativos:</span><span class="sxs-lookup"><span data-stu-id="d9ff7-125">The following code provides an example of an invoke response to return Adaptive Cards:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d9ff7-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="d9ff7-126">See also</span></span>

* [<span data-ttu-id="d9ff7-127">Ações de Cartão Adaptativo em Teams</span><span class="sxs-lookup"><span data-stu-id="d9ff7-127">Adaptive Card actions in Teams</span></span>](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)
* [<span data-ttu-id="d9ff7-128">Como os bots funcionam</span><span class="sxs-lookup"><span data-stu-id="d9ff7-128">How bots work</span></span>](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true)
* [<span data-ttu-id="d9ff7-129">Trabalhar com Ações Universais para Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="d9ff7-129">Work with Universal Actions for Adaptive Cards</span></span>](Work-with-universal-actions-for-adaptive-cards.md)
