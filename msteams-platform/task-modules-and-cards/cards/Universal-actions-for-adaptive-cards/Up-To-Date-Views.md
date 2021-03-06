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
# <a name="up-to-date-cards"></a>Cartões atualizados

Agora você pode fornecer informações mais recentes aos usuários sobre Cartões Adaptáveis com uma combinação de edições de atualização e mensagens Teams. Com isso, você pode atualizar dinamicamente as Exibições Específicas do Usuário para seu estado mais recente, como e quando há uma alteração em seu serviço. Por exemplo, no caso de cartões de gerenciamento de projeto ou de tíquetes, você pode atualizar comentários e o status da tarefa. Em caso de aprovações, o estado mais recente é refletido, além de fornecer informações e ações diferenciadas.

Por exemplo, um usuário pode criar uma solicitação de aprovação de ativo em uma Teams conversa. Alex cria uma solicitação de aprovação e a atribui a Megan e Nestor. Veja a seguir as duas partes para criar a solicitação de aprovação:

* Os Exibições Específicas do Usuário podem ser aproveitados usando `refresh` a propriedade dos Cartões Adaptáveis.
Usar Exibições Específicas do Usuário  pode mostrar um cartão com botões **Aprovar** ou Rejeitar para um conjunto de usuários e mostrar um cartão sem esses botões para outros usuários.

* Para manter o estado do cartão atualizado sempre, Teams mecanismo de edição de mensagens pode ser aproveitado. Por exemplo, sempre que houver uma aprovação, o bot pode disparar uma edição de mensagem para todos os usuários. Essa edição de mensagem bot dispara uma solicitação de invocação para todos os usuários de atualização automática, para os quais o bot pode responder com o cartão `adaptiveCard/action` específico do usuário atualizado.

Para obter mais informações, [consulte como fazer uma edição de mensagem de bot](https://docs.microsoft.com/microsoftteams/platform/bots/how-to/update-and-delete-bot-messages?tabs=dotnet#update-cards).

## <a name="approval-base-card"></a>Cartão base de aprovação

O código a seguir fornece um exemplo de um cartão base de aprovação:

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

## <a name="approval-card-with-approve-and-reject-buttons"></a>Cartão de aprovação com botões Aprovar e Rejeitar

O código a seguir fornece um exemplo de cartão de aprovação com **botões Aprovar** e **Rejeitar:**

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

A seguir estão as duas funções mostradas aos usuários, dependendo do envolvimento na solicitação de aprovação:

* Cartão base de aprovação: mostrado para usuários que não fazem parte da lista de aprovadores e ainda não aprovaram ou rejeitaram a solicitação e não fazem parte da lista na propriedade do JSON do Cartão `userIds` `refresh` Adaptável.
* Cartão de aprovação **com** botões Aprovar ou Rejeitar: mostrado para os usuários que fazem parte da lista de aprovadores e a lista na propriedade do JSON do Cartão  `userIds` `refresh` Adaptável.

**Para enviar a solicitação de aprovação de ativos**

1. Alex levanta uma solicitação de aprovação de ativos em uma Teams e a atribui a Megan e Nestor.
2. Bot envia o cartão base de aprovação na conversa.
3. Todos os outros usuários na conversa veem o cartão enviado pelo bot. A atualização automática é disparada para Megan e Nestor, que  agora veem o cartão específico do usuário com os botões **Aprovar** ou Rejeitar como seus MRIs de usuário são adicionados à lista na propriedade do `userIds` Cartão `refresh` Adaptável.

    :::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views-1.png" alt-text="Exibições Específicas do Usuário":::

4. Nestor seleciona o botão **Aprovar** que é alimentado com `Action.Execute` . O bot recebe uma `adaptiveCard/action` solicitação de invocação à qual ele pode retornar um Cartão Adaptável em resposta.
5. O bot dispara uma edição de mensagem com um cartão atualizado que diz que Nestor aprovou a solicitação enquanto a aprovação de Megan está pendente.
6. A edição de mensagem bot dispara uma atualização automática para Megan e ela vê o cartão específico do  usuário atualizado, que diz que Nestor aprovou a solicitação, mas também vê os botões **Aprovar** ou Rejeitar. A MRI do usuário de Nestor é removida da lista na propriedade deste JSON de Cartão Adaptável nas etapas `userIds` `refresh` 4 e 5. Agora, a atualização automática só é disparada para Megan.

    :::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views-2.png" alt-text="Exibições específicas do usuário atualizadas":::

7. Agora, Megan seleciona o **botão Aprovar,** que é alimentado com `Action.Execute` . O bot recebe uma `adaptiveCard/action` solicitação de invocação à qual ele pode retornar um Cartão Adaptável em resposta.
8. O bot dispara uma edição de mensagem com um cartão atualizado, que diz que Nestor e Megan aprovaram a solicitação.
9. A edição da mensagem bot não dispara nenhuma atualização automática. A MRI do usuário de Megan também é removida da lista na propriedade deste JSON de Cartão Adaptável nas etapas `userIds` `refresh` 7 e 8.

    :::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views-3.png" alt-text="Exibições atualizadas":::

## <a name="adaptive-card-sent-as-response-of-adaptivecardaction-and-message-edit"></a>Cartão Adaptável enviado como resposta `adaptiveCard/action` de e `message edit`

O código a seguir fornece um exemplo de Cartões Adaptáveis enviados como resposta e para as `adaptiveCard/action` `message edit` etapas 4 e 5:

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

O código a seguir fornece um exemplo de Cartões Adaptáveis enviados como resposta de invocar por meio da atualização automática para a `adaptiveCard/action` etapa 6:

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

O código a seguir fornece um exemplo de Cartões Adaptáveis enviados como resposta e para as `adaptiveCard/action` `message edit` etapas 7 e 8:

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

## <a name="see-also"></a>Confira também

* [Trabalhar com Ações Universais para Cartões Adaptáveis](Work-with-universal-actions-for-adaptive-cards.md)
* [Exibições Específicas do Usuário](User-Specific-Views.md)
