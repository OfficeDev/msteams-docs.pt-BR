---
title: Modos de exibição atualizados
description: Neste módulo, saiba mais sobre exibições de cartões atualizadas usando o Bot Universal com exemplos de código Microsoft Teams
author: surbhigupta12
ms.topic: conceptual
ms.localizationpriority: medium
ms.openlocfilehash: 5c6f7d13cd884baf9ffbc1fd30cafb7cfab33295
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143617"
---
# <a name="up-to-date-cards"></a>Cartões atualizados

Agora você pode fornecer informações mais recentes aos usuários em Cartões Adaptáveis. Inclua uma combinação de atualizações e edições de mensagens Teams. Atualize as Exibições Específicas do Usuário dinamicamente para seu estado mais recente como e quando há uma alteração em seu serviço. Por exemplo, para gerenciamento de projetos ou cartões de tíquetes, atualize os comentários e o status da tarefa. Para aprovações, o estado mais recente é refletido, fornecendo também informações e ações diferenciadas.

Por exemplo, um usuário pode criar uma solicitação de aprovação de ativo em uma Teams conversa. Alex cria uma solicitação de aprovação e a atribui a Megan e Brenda. A seguir estão as duas partes para criar a solicitação de aprovação:

* As Exibições Específicas do Usuário podem ser aplicadas usando `refresh` a propriedade dos Cartões Adaptáveis.
Usando exibições específicas do usuário, é possível mostrar um  cartão com os botões **Aprovar** ou Rejeitar para um conjunto de usuários e mostrar um cartão sem esses botões para outros usuários.

* Para manter o estado do cartão sempre atualizado, Teams mecanismo de edição de mensagem pode ser usado. Por exemplo, para cada aprovação, o bot pode disparar uma edição de mensagem para todos os usuários. Essa edição de mensagem de bot dispara `adaptiveCard/action` uma solicitação de invocação para todos os usuários de atualização automática, às quais o bot pode responder com o cartão específico do usuário atualizado.

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

## <a name="approval-card-with-approve-and-reject-buttons"></a>Cartão de aprovação com os botões Aprovar e Rejeitar

O código a seguir fornece um exemplo de um cartão de aprovação com **os botões Aprovar** **e** Rejeitar:

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

* Cartão base de aprovação: mostrado aos usuários que não fazem parte da lista de aprovadores e a solicitação ainda não foi aprovada ou rejeitada, `userIds` `refresh` e não faz parte da lista na propriedade do JSON do Cartão Adaptável.
* Cartão de **aprovação** com  os botões Aprovar ou Rejeitar: `userIds` `refresh` mostrado para os usuários que fazem parte da lista de aprovadores e a lista na propriedade do Cartão Adaptável JSON.

Para enviar a solicitação de aprovação de ativos:

1. Alex aciona uma solicitação de aprovação de ativos em Teams conversa e a atribui a Megan e Brenda.
2. O bot envia o cartão base de aprovação na conversa.
3. Todos os outros usuários na conversa veem o cartão enviado pelo bot. A atualização automática é disparada para Sara e Brenda, que agora veem o cartão específico do usuário  com os  botões Aprovar ou Rejeitar conforme seus MRIs `userIds` `refresh` de usuário são adicionados à lista na propriedade do Cartão Adaptável.

    :::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views-1.png" alt-text="Exibições Específicas do Usuário":::

4. O Nesto seleciona **o botão** Aprovar, que é ligado com `Action.Execute`. O bot obtém uma `adaptiveCard/action` solicitação de invocação para a qual ele pode retornar um Cartão Adaptável em resposta.
5. O bot dispara uma edição de mensagem com um cartão atualizado, que diz que Brenda aprovou a solicitação enquanto a aprovação de Megan está pendente.
6. A edição da mensagem do bot dispara uma atualização automática para Sara e ela vê o cartão específico do usuário atualizado, que diz que o Brenda aprovou a solicitação, mas  também vê  os botões Aprovar ou Rejeitar. A MRI `userIds` `refresh` do usuário de Tutorial é removida da lista na propriedade deste JSON de Cartão Adaptável nas etapas 4 e 5. Agora, a atualização automática só é disparada para Megan.

    :::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views-2.png" alt-text="Exibições específicas do usuário atualizadas":::

7. Agora, Megan seleciona o **botão Aprovar** , que é ligado com `Action.Execute`. O bot obtém uma `adaptiveCard/action` solicitação de invocação para a qual ele pode retornar um Cartão Adaptável em resposta.
8. O bot dispara uma edição de mensagem com um cartão atualizado, que diz que Brenda e Sara aprovaram a solicitação.
9. A edição da mensagem do bot não dispara nenhuma atualização automática. A MRI `userIds` `refresh` de usuário de Sara também é removida da lista na propriedade deste JSON de Cartão Adaptável nas etapas 7 e 8.

    :::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views-3.png" alt-text="Modos de exibição atualizados":::

## <a name="adaptive-card-sent-as-response-of-adaptivecardaction-and-message-edit"></a>Cartão Adaptável enviado como resposta de `adaptiveCard/action` e `message edit`

O código a seguir fornece um exemplo de Cartões Adaptáveis enviados como resposta das `adaptiveCard/action` `message edit` etapas 4 e 5:

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

O código a seguir fornece um exemplo de Cartões Adaptáveis enviados como resposta `adaptiveCard/action` de invocação por meio da atualização automática para a etapa 6:

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

O código a seguir fornece um exemplo de Cartões Adaptáveis enviados como resposta das `adaptiveCard/action` `message edit` etapas 7 e 8:

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
| Cartões Adaptáveis de Fluxos de Trabalho Sequenciais | Demonstre como implementar Fluxos de Trabalho Sequenciais, Exibições Específicas do Usuário e Cartões Adaptáveis atualizados em bots. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/csharp) | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-sequential-flow-adaptive-cards/nodejs) |

## <a name="see-also"></a>Confira também

* [Trabalhar com Ações Universais para Cartões Adaptáveis](Work-with-universal-actions-for-adaptive-cards.md)
* [Exibições Específicas do Usuário](User-Specific-Views.md)
* [Comentários de preenchimento do formulário](~/bots/how-to/conversations/conversation-messages.md#form-completion-feedback)
