---
title: Fluxos de Trabalho Sequenciais
description: Exemplo de fluxos de trabalho sequenciais usando ações universais
author: surbhigupta12
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: c3065080a0a470104fa2b7c06c9b0c8105a829a6
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59155171"
---
# <a name="sequential-workflows"></a>Fluxos de Trabalho Sequenciais

Os Cartões Adaptáveis agora suportam fluxos de trabalho sequenciais atualizados na ação do usuário. Usando fluxos de trabalho sequenciais, os Cartões Adaptáveis são atualizados na ação do usuário e o usuário pode progredir por meio de uma série de cartões que exigem a entrada do usuário. `Action.Execute` oferece suporte a Fluxos de Trabalho Sequenciais, o que permite que desenvolvedores de bot retornem Cartões Adaptáveis em resposta a uma ação do usuário.

Por exemplo, veja um cenário em que o cafeteria deseja fazer um pedido para uma equipe ou canal. Com a escolha do usuário para vários itens, como alimentos e bebidas, pode ser `Action.Execute` gravado sequencialmente. O usuário também pode ir e voltar pelos cartões de acordo com a lógica definida pelo desenvolvedor do bot. <br/>

A imagem a seguir mostra o Fluxo de Trabalho Sequencial:

<img src="~/assets/images/bots/sequentialWorkflow.gif" alt="Sequential Workflow" width="400"/>

Um usuário pode progredir no fluxo de trabalho sem modificar o cartão para outros usuários. O fluxo de trabalho também é útil para realizar testes usando Cartões Adaptáveis sequenciais. A imagem a seguir mostra que diferentes usuários podem estar em diferentes estágios do fluxo de trabalho e estados do cartão:

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
    type = "application/vnd.microsoft.adaptive.card",
    value = card
 });
```

## <a name="code-samples"></a>Exemplos de código

|Nome do exemplo | Descrição | .NETCore | Node.js |
|----------------|-----------------|--------------|--------------|
| Bot de refeições do Teams | Crie um bot que aceite a ordem de alimentação usando Cartões Adaptáveis. |[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-teams-catering/csharp)| Ainda não disponível |
| Cartões adaptáveis de fluxos de trabalho sequenciais | Demonstre como implementar fluxos de trabalho sequenciais, exibições específicas do usuário e cartões adaptáveis atualizados em bots. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/csharp) | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/nodejs) |


## <a name="see-also"></a>Confira também

* [Ações de Cartão Adaptável no Teams](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)
* [Como os bots funcionam](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true)
* [Trabalhar com Ações Universais para Cartões Adaptáveis](Work-with-universal-actions-for-adaptive-cards.md)
