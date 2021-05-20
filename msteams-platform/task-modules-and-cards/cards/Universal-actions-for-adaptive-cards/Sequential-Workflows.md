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
# <a name="sequential-workflows"></a>Fluxos de Trabalho Sequenciais

Cartões adaptativos agora suportam fluxos de trabalho sequenciais que é quando cartões adaptativos são atualizados sobre a ação do usuário e o usuário pode progredir através de uma série de cartões que requerem a entrada do usuário. Isso é suportado através `Action.Execute` de , o que permite que os desenvolvedores de bots retornem Cartões Adaptativos em resposta a uma ação do usuário.

Por exemplo, tome um cenário onde o refeitório quer pegar um pedido para uma equipe ou canal. Com `Action.Execute` a escolha do usuário para vários itens, como alimentos, bebidas, e assim por diante pode ser registrado sequencialmente. O usuário também pode ir e voltar através das cartas de acordo com a lógica definida pelo desenvolvedor de bots. <br/>

A imagem a seguir mostra o fluxo de trabalho sequencial:

<img src="~/assets/images/bots/sequentialWorkflow.gif" alt="Sequential Workflow" width="400"/>

Um usuário pode progredir através de seu fluxo de trabalho sem modificar o cartão para outros usuários. Isso também é útil para a realização de testes usando cartões adaptativos sequenciais. Como mostrado na imagem a seguir, diferentes usuários podem estar em diferentes estágios do fluxo de trabalho e vêem diferentes estados do cartão:

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-catering-bot.png" alt-text="Estados de bot de bufê":::

> [!NOTE]
> Para sincronizar o progresso do usuário entre os dispositivos, use a `refresh` propriedade em Adaptive Card JSON.

## <a name="sequential-workflow-for-adaptive-cards"></a>Fluxo de trabalho sequencial para cartões adaptativos

O código a seguir fornece um exemplo de Cartões Adaptativos:

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

`Action.Execute`invocar o bot pode retornar Cartões Adaptativos como uma resposta, que substitui a placa existente em Teams.
O exemplo a seguir fornece o que o bot retorna na seleção de alimentos ou bebidas ou confirmação do pedido:

* Na seleção de alimentos do Cartão 1, o bot pode devolver um cartão para seleção de bebidas que é o Cartão 2.
* Na seleção de bebidas do Cartão 2, o bot pode devolver um cartão de confirmação de pedido que é o Cartão 3.
* Na confirmação do pedido do Cartão 3, o bot pode retornar um cartão confirmado por ordem que é o Cartão 4.

## <a name="invoke-request-received-on-bot-side"></a>Invocar solicitação recebida no lado do bot

O código a seguir fornece um exemplo de uma solicitação de invocação recebida no lado do bot:

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

## <a name="invoke-response-to-return-adaptive-cards"></a>Invoque a resposta para retornar cartões adaptativos

O código a seguir fornece um exemplo de uma resposta de invocação para retornar cartões adaptativos:

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

## <a name="see-also"></a>Confira também

* [Ações de Cartão Adaptativo em Teams](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)
* [Como os bots funcionam](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true)
* [Trabalhar com Ações Universais para Cartões Adaptáveis](Work-with-universal-actions-for-adaptive-cards.md)
