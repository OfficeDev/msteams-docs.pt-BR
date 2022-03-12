---
title: Exibições atualizadas
description: Saiba mais sobre exibições atualizadas usando o Universal Bot com exemplos de código
author: surbhigupta12
ms.topic: conceptual
ms.localizationpriority: medium
keywords: aprovação cartão base rejeitar adaptável
ms.openlocfilehash: 3eea8e3c08927ab797525a10f59774410197d0e1
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2022
ms.locfileid: "63453730"
---
# <a name="up-to-date-cards"></a>Cartões atualizados

Agora você pode fornecer informações mais recentes para seus usuários em Cartões Adaptáveis. Inclua uma combinação de edições de atualização e mensagens Teams. Atualize dinamicamente as Exibições Específicas do Usuário para seu estado mais recente, como e quando há uma alteração em seu serviço. Por exemplo, para cartões de gerenciamento de projeto ou de tíquete, atualize comentários e o status da tarefa. Para aprovações, o estado mais recente é refletido, além de fornecer informações e ações diferenciadas.

Por exemplo, um usuário pode criar uma solicitação de aprovação de ativos em uma Teams conversa. Alex cria uma solicitação de aprovação e a atribui a Megan e Nestor. Veja a seguir as duas partes para criar a solicitação de aprovação:

* Exibições Específicas do Usuário podem ser aplicadas usando a `refresh` propriedade dos Cartões Adaptáveis.
Usar Exibições Específicas do Usuário pode mostrar um cartão com  botões **Aprovar** ou Rejeitar para um conjunto de usuários e mostrar um cartão sem esses botões para outros usuários.

* Para manter o estado do cartão sempre atualizado, Teams mecanismo de edição de mensagens pode ser usado. Por exemplo, para cada aprovação, o bot pode disparar uma edição de mensagem para todos os usuários. Essa edição de mensagem bot dispara uma `adaptiveCard/action` solicitação de invocação para todos os usuários de atualização automática, para os quais o bot pode responder com o cartão específico do usuário atualizado.

Para obter mais informações, [consulte como fazer uma edição de mensagem de bot](/microsoftteams/platform/bots/how-to/update-and-delete-bot-messages?tabs=dotnet#update-cards).

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

O código a seguir fornece um exemplo de cartão de aprovação com **botões Aprovar** e **Rejeitar** :

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

A seguir estão as duas funções mostradas aos usuários, dependendo da solicitação de aprovação:

* Cartão base de aprovação: mostrado aos usuários que não fazem parte da lista de aprovadores e a solicitação ainda não foi aprovada ou rejeitada, `userIds` `refresh` e não faz parte da lista na propriedade do JSON de Cartão Adaptável.
* Cartão de aprovação **com** botões Aprovar ou Rejeitar:  `userIds` `refresh` mostrado para os usuários que fazem parte da lista de aprovadores e a lista na propriedade do JSON do Cartão Adaptável.

Para enviar a solicitação de aprovação de ativos:

1. Alex levanta uma solicitação de aprovação de ativos em uma conversa Teams e a atribui a Megan e Nestor.
2. Bot envia o cartão base de aprovação na conversa.
3. Todos os outros usuários na conversa veem o cartão enviado pelo bot. A atualização automática é disparada para Megan e Nestor, que agora veem o cartão específico do usuário com os  botões **Aprovar** ou Rejeitar como seus MRIs `userIds` `refresh` de usuário são adicionados à lista na propriedade do Cartão Adaptável.

    :::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views-1.png" alt-text="Exibições Específicas do Usuário":::

4. Nestor seleciona o **botão Aprovar** , que é alimentado com `Action.Execute`. O bot recebe uma `adaptiveCard/action` solicitação de invocação à qual ele pode retornar um Cartão Adaptável em resposta.
5. O bot dispara uma edição de mensagem com um cartão atualizado, que diz que Nestor aprovou a solicitação enquanto a aprovação de Megan está pendente.
6. A edição de mensagem bot dispara uma atualização automática para Megan e ela vê o cartão específico do usuário atualizado, que diz que Nestor aprovou a solicitação, mas também vê os botões  **Aprovar** ou Rejeitar. A MRI do usuário de Nestor é `userIds` `refresh` removida da lista na propriedade deste JSON de Cartão Adaptável nas etapas 4 e 5. Agora, a atualização automática só é disparada para Megan.

    :::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views-2.png" alt-text="Exibições específicas do usuário atualizadas":::

7. Agora, Megan seleciona o **botão Aprovar** , que é alimentado com `Action.Execute`. O bot recebe uma `adaptiveCard/action` solicitação de invocação à qual ele pode retornar um Cartão Adaptável em resposta.
8. O bot dispara uma edição de mensagem com um cartão atualizado, que diz que Nestor e Megan aprovaram a solicitação.
9. A edição da mensagem bot não dispara nenhuma atualização automática. A MRI `userIds` `refresh` do usuário de Megan também é removida da lista na propriedade deste JSON de Cartão Adaptável nas etapas 7 e 8.

    :::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views-3.png" alt-text="Exibições atualizadas":::

## <a name="adaptive-card-sent-as-response-of-adaptivecardaction-and-message-edit"></a>Cartão Adaptável enviado como resposta de `adaptiveCard/action` e `message edit`

O código a seguir fornece um exemplo de Cartões Adaptáveis enviados como resposta e `adaptiveCard/action` para `message edit` as etapas 4 e 5:

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

O código a seguir fornece um exemplo de Cartões Adaptáveis enviados como resposta de `adaptiveCard/action` invocar por meio da atualização automática para a etapa 6:

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

O código a seguir fornece um exemplo de Cartões Adaptáveis enviados como resposta e `adaptiveCard/action` para `message edit` as etapas 7 e 8:

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

## <a name="code-sample"></a>Exemplo de código

|Nome do exemplo | Descrição | .NETCore | Node.js |
|----------------|-----------------|--------------|--------------|
| Cartões adaptáveis de fluxos de trabalho sequenciais | Demonstre como implementar fluxos de trabalho sequenciais, exibições específicas do usuário e cartões adaptáveis atualizados em bots. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/csharp) | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/nodejs) |

## <a name="see-also"></a>Confira também

* [Trabalhar com Ações Universais para Cartões Adaptáveis](Work-with-universal-actions-for-adaptive-cards.md)
* [Exibições Específicas do Usuário](User-Specific-Views.md)
* [Comentários de preenchimento do formulário](~/bots/how-to/conversations/conversation-messages.md#form-completion-feedback)
