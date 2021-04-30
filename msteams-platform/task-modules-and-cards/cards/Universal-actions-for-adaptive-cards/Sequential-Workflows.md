---
title: Fluxos de trabalho sequenciais
description: Exemplo de fluxos de trabalho sequenciais usando ações universais
author: surbhigupta12
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: 4b37e8603d34c070bdef3003c2f8ccb0bb41550b
ms.sourcegitcommit: 1256639fa424e3833b44207ce847a245824d48e6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2021
ms.locfileid: "52088808"
---
# <a name="sequential-workflows"></a>Fluxos de trabalho sequenciais

Os Cartões Adaptáveis agora suportam fluxos de trabalho sequenciais que são quando cartões adaptáveis são atualizados na ação do usuário e o usuário pode progredir por meio de uma série de cartões que exigem a entrada do usuário. Isso é suportado por meio de , que permite que os desenvolvedores de bot retornem Cartões `Action.Execute` Adaptáveis em resposta a uma ação do usuário.

Por exemplo, veja um cenário em que o cafeteria deseja fazer um pedido para uma equipe ou canal. Com a escolha do usuário para vários itens, como alimentos, bebidas e assim por diante, pode ser gravado `Action.Execute` sequencialmente. O usuário também pode ir e voltar pelos cartões de acordo com a lógica definida pelo desenvolvedor do bot. <br/>

A imagem a seguir mostra o Fluxo de Trabalho Sequencial:

<img src="~/assets/images/bots/sequentialWorkflow.gif" alt="Sequential Workflow" width="400"/>

Um usuário pode progredir no fluxo de trabalho sem modificar o cartão para outros usuários. Isso também é útil para realizar testes usando Cartões Adaptáveis sequenciais. Conforme mostrado na imagem a seguir, diferentes usuários podem estar em diferentes estágios do fluxo de trabalho e ver estados diferentes do cartão:

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-catering-bot.png" alt-text="Estados de bot de bufê":::

> [!NOTE]
> Para sincronizar o progresso do usuário entre dispositivos, use a `refresh` propriedade em Adaptive Card JSON.

## <a name="sequential-workflow-for-adaptive-cards"></a>Fluxo de trabalho sequencial para cartões adaptáveis

O código a seguir fornece um exemplo de Cartões Adaptáveis:

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

`Action.Execute`invocar o bot pode retornar Cartões Adaptáveis como uma resposta, que substitui o cartão existente no Teams.
O exemplo a seguir fornece o que o bot retorna em seleção de alimentos ou bebidas ou confirmação de pedido:

* Na seleção de alimentos do Cartão 1, o bot pode retornar um cartão para seleção de bebidas que é o Cartão 2.
* Na seleção de bebidas do Cartão 2, o bot pode retornar um cartão de confirmação de pedido que é o Cartão 3.
* Na confirmação do pedido do Cartão 3, o bot pode retornar um cartão confirmado de pedido que é o Cartão 4.

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

## <a name="invoke-response-to-return-adaptive-cards"></a>Invocar resposta para retornar cartões adaptáveis

O código a seguir fornece um exemplo de uma resposta de invocação para retornar Cartões Adaptáveis:

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

## <a name="see-also"></a>Confira também

* [Ações de Cartão Adaptável em Teams](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)
* [Como os bots funcionam](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true)
* [Trabalhar com ações universais para cartões adaptáveis](Work-with-universal-actions-for-adaptive-cards.md)
