---
title: Fluxos de Trabalho Sequenciais
description: Neste módulo, saiba mais sobre fluxos de trabalho sequenciais para cartões adaptáveis usando ações universais com exemplos de código
author: surbhigupta12
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: bd3fbf560099487ba45c2454460b82b852b675fa
ms.sourcegitcommit: c3601696cced9aadc764f1e734646ee7711f154c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2022
ms.locfileid: "68833188"
---
# <a name="sequential-workflows"></a>Fluxos de Trabalho Sequenciais

Os cartões adaptáveis agora dão suporte a fluxos de trabalho sequenciais atualizados na ação do usuário. Usando fluxos de trabalho sequenciais, os Cartões Adaptáveis são atualizados na ação do usuário e o usuário pode progredir por meio de uma série de cartões que exigem entrada do usuário. `Action.Execute` dá suporte a fluxos de trabalho sequenciais, o que permite que os desenvolvedores de bot retornem Cartões Adaptáveis em resposta a uma ação do usuário.

Por exemplo, veja um cenário em que a cafeteria deseja fazer um pedido para uma equipe ou canal. Com `Action.Execute` a escolha do usuário para vários itens, como alimentos e bebidas, pode ser registrado sequencialmente. O usuário também pode ir e voltar pelos cartões de acordo com a lógica definida pelo desenvolvedor do bot. <br/>

A imagem a seguir mostra o fluxo de trabalho sequencial:

<img src="~/assets/images/bots/sequentialWorkflow.gif" alt="Sequential Workflow" width="400"/>

Um usuário pode progredir por meio de seu fluxo de trabalho sem modificar o cartão para outros usuários. O fluxo de trabalho também é útil para realizar testes usando cartões adaptáveis sequenciais. A imagem a seguir mostra que diferentes usuários podem estar em diferentes estágios do fluxo de trabalho e dos estados do cartão:

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-catering-bot.png" alt-text="Estados de bot de catering" lightbox="../../../assets/images/adaptive-cards/universal-bots-catering-bot.png":::

> [!NOTE]
> Para sincronizar o progresso do usuário entre dispositivos, use a `refresh` propriedade no JSON do Cartão Adaptável.

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

`Action.Execute` Invocar o bot pode retornar Cartões Adaptáveis como uma resposta, que substitui o cartão existente no Teams.
O exemplo a seguir fornece o que o bot retorna na seleção de alimentos ou bebidas ou confirmação do pedido:

* Na seleção de alimentos do Cartão 1, o bot pode retornar um cartão para seleção de bebidas que é Cartão 2.
* Na seleção de bebidas do Cartão 2, o bot pode retornar um cartão de confirmação de pedido que é o Cartão 3.
* Na confirmação do pedido do Cartão 3, o bot pode retornar um cartão confirmado por pedido que é o Cartão 4.

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
| Bot de refeições do Teams | Crie um bot que aceite a ordem dos alimentos usando Cartões Adaptáveis. |[Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-teams-catering/csharp)| NA |
| Cartões Adaptáveis de Fluxos de Trabalho Sequenciais | Demonstre como implementar Fluxos de Trabalho Sequenciais, Exibições Específicas do Usuário e Cartões Adaptáveis atualizados em bots. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/csharp) | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/nodejs) |

## <a name="see-also"></a>Confira também

* [Ações de Cartão Adaptável no Teams](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)
* [Como os bots funcionam](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true)
* [Trabalhar com Ações Universais para Cartões Adaptáveis](Work-with-universal-actions-for-adaptive-cards.md)
* [Comentários de preenchimento do formulário](~/bots/how-to/conversations/conversation-messages.md#form-completion-feedback)
