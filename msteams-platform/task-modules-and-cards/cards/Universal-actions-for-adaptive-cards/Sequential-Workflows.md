---
title: Fluxos de Trabalho Sequenciais
description: Exemplo de fluxos de trabalho sequenciais usando ações universais
author: surbhigupta12
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: f36e65133572569cd01de1053044336c810656f3
ms.sourcegitcommit: 999f5c607671e088ea8a461fa7dbb63f8d61c39b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2021
ms.locfileid: "52649640"
---
# <a name="sequential-workflows"></a><span data-ttu-id="3d368-103">Fluxos de Trabalho Sequenciais</span><span class="sxs-lookup"><span data-stu-id="3d368-103">Sequential Workflows</span></span>

<span data-ttu-id="3d368-104">Os Cartões Adaptáveis agora suportam fluxos de trabalho sequenciais que são quando cartões adaptáveis são atualizados na ação do usuário e o usuário pode progredir por meio de uma série de cartões que exigem a entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="3d368-104">Adaptive Cards now support Sequential Workflows that is when Adaptive Cards are updated on user action and user can progress through a series of cards that require user input.</span></span> <span data-ttu-id="3d368-105">Isso é suportado por meio de , que permite que os desenvolvedores de bot retornem Cartões `Action.Execute` Adaptáveis em resposta a uma ação do usuário.</span><span class="sxs-lookup"><span data-stu-id="3d368-105">This is supported through `Action.Execute`, which allows bot developers to return Adaptive Cards in response to a user action.</span></span>

<span data-ttu-id="3d368-106">Por exemplo, veja um cenário em que o cafeteria deseja fazer um pedido para uma equipe ou canal.</span><span class="sxs-lookup"><span data-stu-id="3d368-106">For example, take a scenario where the cafeteria wants to take an order for a team or channel.</span></span> <span data-ttu-id="3d368-107">Com a escolha do usuário para vários itens, como alimentos, bebidas e assim por diante, pode ser gravado `Action.Execute` sequencialmente.</span><span class="sxs-lookup"><span data-stu-id="3d368-107">With `Action.Execute` the user's choice for various items, such as food, drinks, and so on can be recorded sequentially.</span></span> <span data-ttu-id="3d368-108">O usuário também pode ir e voltar pelos cartões de acordo com a lógica definida pelo desenvolvedor do bot.</span><span class="sxs-lookup"><span data-stu-id="3d368-108">User can also go back and forth through the cards as per the logic defined by the bot developer.</span></span> <br/>

<span data-ttu-id="3d368-109">A imagem a seguir mostra o Fluxo de Trabalho Sequencial:</span><span class="sxs-lookup"><span data-stu-id="3d368-109">The following image shows the Sequential Workflow:</span></span>

<img src="~/assets/images/bots/sequentialWorkflow.gif" alt="Sequential Workflow" width="400"/>

<span data-ttu-id="3d368-110">Um usuário pode progredir no fluxo de trabalho sem modificar o cartão para outros usuários.</span><span class="sxs-lookup"><span data-stu-id="3d368-110">A user can progress through their workflow without modifying the card for other users.</span></span> <span data-ttu-id="3d368-111">Isso também é útil para realizar testes usando Cartões Adaptáveis sequenciais.</span><span class="sxs-lookup"><span data-stu-id="3d368-111">This is also useful for conducting quizzes using sequential Adaptive Cards.</span></span> <span data-ttu-id="3d368-112">Conforme mostrado na imagem a seguir, diferentes usuários podem estar em diferentes estágios do fluxo de trabalho e ver estados diferentes do cartão:</span><span class="sxs-lookup"><span data-stu-id="3d368-112">As shown in the following image, different users can be at different stages of the workflow and they see different states of the card:</span></span>

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-catering-bot.png" alt-text="Estados de bot de bufê":::

> [!NOTE]
> <span data-ttu-id="3d368-114">Para sincronizar o progresso do usuário entre dispositivos, use a `refresh` propriedade em Adaptive Card JSON.</span><span class="sxs-lookup"><span data-stu-id="3d368-114">In order to sync the user's progress across devices, use the `refresh` property in Adaptive Card JSON.</span></span>

## <a name="sequential-workflow-for-adaptive-cards"></a><span data-ttu-id="3d368-115">Fluxo de trabalho sequencial para cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="3d368-115">Sequential Workflow for Adaptive Cards</span></span>

<span data-ttu-id="3d368-116">O código a seguir fornece um exemplo de Cartões Adaptáveis:</span><span class="sxs-lookup"><span data-stu-id="3d368-116">The following code provides an example of Adaptive Cards:</span></span>

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

<span data-ttu-id="3d368-117">`Action.Execute`invocar o bot pode retornar Cartões Adaptáveis como uma resposta, que substitui o cartão existente no Teams.</span><span class="sxs-lookup"><span data-stu-id="3d368-117">`Action.Execute` invoking the bot can return Adaptive Cards as a response, which replaces the existing card in Teams.</span></span>
<span data-ttu-id="3d368-118">O exemplo a seguir fornece o que o bot retorna em seleção de alimentos ou bebidas ou confirmação de pedido:</span><span class="sxs-lookup"><span data-stu-id="3d368-118">The following example provides what the bot returns on food or drink selection or order confirmation:</span></span>

* <span data-ttu-id="3d368-119">Na seleção de alimentos do Cartão 1, o bot pode retornar um cartão para seleção de bebidas que é o Cartão 2.</span><span class="sxs-lookup"><span data-stu-id="3d368-119">On food selection from Card 1, bot can return a card for selection of drinks that is Card 2.</span></span>
* <span data-ttu-id="3d368-120">Na seleção de bebidas do Cartão 2, o bot pode retornar um cartão de confirmação de pedido que é o Cartão 3.</span><span class="sxs-lookup"><span data-stu-id="3d368-120">On drink selection from Card 2, bot can return an order confirmation card that is Card 3.</span></span>
* <span data-ttu-id="3d368-121">Na confirmação do pedido do Cartão 3, o bot pode retornar um cartão confirmado de pedido que é o Cartão 4.</span><span class="sxs-lookup"><span data-stu-id="3d368-121">On order confirmation from Card 3, bot can return an order confirmed card that is Card 4.</span></span>

## <a name="invoke-request-received-on-bot-side"></a><span data-ttu-id="3d368-122">Invocar solicitação recebida no lado do bot</span><span class="sxs-lookup"><span data-stu-id="3d368-122">Invoke request received on bot side</span></span>

<span data-ttu-id="3d368-123">O código a seguir fornece um exemplo de uma solicitação de invocação recebida no lado do bot:</span><span class="sxs-lookup"><span data-stu-id="3d368-123">The following code provides an example of an invoke request received on bot side:</span></span>

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

## <a name="invoke-response-to-return-adaptive-cards"></a><span data-ttu-id="3d368-124">Invocar resposta para retornar cartões adaptáveis</span><span class="sxs-lookup"><span data-stu-id="3d368-124">Invoke response to return Adaptive Cards</span></span>

<span data-ttu-id="3d368-125">O código a seguir fornece um exemplo de uma resposta de invocação para retornar Cartões Adaptáveis:</span><span class="sxs-lookup"><span data-stu-id="3d368-125">The following code provides an example of an invoke response to return Adaptive Cards:</span></span>

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

## <a name="code-sample"></a><span data-ttu-id="3d368-126">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="3d368-126">Code sample</span></span>

|<span data-ttu-id="3d368-127">Exemplo de nome</span><span class="sxs-lookup"><span data-stu-id="3d368-127">Sample name</span></span> | <span data-ttu-id="3d368-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="3d368-128">Description</span></span> | <span data-ttu-id="3d368-129">. NETCore</span><span class="sxs-lookup"><span data-stu-id="3d368-129">.NETCore</span></span> |
|----------------|-----------------|--------------|
| <span data-ttu-id="3d368-130">Teams de bufê</span><span class="sxs-lookup"><span data-stu-id="3d368-130">Teams catering bot</span></span> | <span data-ttu-id="3d368-131">Crie um bot simples que aceite a ordem de alimentação usando Cartões Adaptáveis.</span><span class="sxs-lookup"><span data-stu-id="3d368-131">Create a simple bot that accepts food order using Adaptive Cards.</span></span> |[<span data-ttu-id="3d368-132">View</span><span class="sxs-lookup"><span data-stu-id="3d368-132">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-teams-catering/csharp)|

## <a name="see-also"></a><span data-ttu-id="3d368-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="3d368-133">See also</span></span>

* [<span data-ttu-id="3d368-134">Ações de Cartão Adaptável em Teams</span><span class="sxs-lookup"><span data-stu-id="3d368-134">Adaptive Card actions in Teams</span></span>](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)
* [<span data-ttu-id="3d368-135">Como os bots funcionam</span><span class="sxs-lookup"><span data-stu-id="3d368-135">How bots work</span></span>](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true)
* [<span data-ttu-id="3d368-136">Trabalhar com Ações Universais para Cartões Adaptáveis</span><span class="sxs-lookup"><span data-stu-id="3d368-136">Work with Universal Actions for Adaptive Cards</span></span>](Work-with-universal-actions-for-adaptive-cards.md)
