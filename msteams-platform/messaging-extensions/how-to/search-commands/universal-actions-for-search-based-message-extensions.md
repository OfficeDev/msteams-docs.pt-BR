---
title: Ações universais para extensões de mensagens baseadas em pesquisa
author: v-ypalikila
description: Neste artigo, saiba mais sobre Ações Universais e atualização automática para cartões adaptáveis em extensões de mensagens baseadas em pesquisa.
ms.topic: conceptual
ms.author: v-ypalikila
ms.localizationpriority: medium
ms.openlocfilehash: 18f5b783797d69144aac82e5ebd95fc30dad57a2
ms.sourcegitcommit: 9ea9a70d2591bce6b8c980d22014e160f7b45f91
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2022
ms.locfileid: "68819965"
---
# <a name="universal-actions-for-search-based-message-extensions"></a>Ações Universais para extensões de mensagens baseadas em pesquisa

Cartões adaptáveis em extensões de mensagens baseadas em pesquisa agora dão suporte a Ações Universais. Para habilitar ações universais para extensões de mensagens baseadas em pesquisa, o aplicativo deve estar em conformidade com o [esquema de Ações Universais para Cartões Adaptáveis](../../../task-modules-and-cards/cards/Universal-actions-for-adaptive-cards/Work-with-Universal-Actions-for-Adaptive-Cards.md#schema-for-universal-actions-for-adaptive-cards) , juntamente com os seguintes requisitos:

1. O aplicativo deve ter um bot de conversa definido no manifesto do aplicativo.
1. Se você já tiver um bot de conversa, deverá usar o mesmo bot usado na extensão de mensagem.
1. Se o cartão for enviado em um grupo, o aplicativo deverá especificar `team` ou `groupchat` escopo em seu bot no manifesto.

Exemplo de um esquema JSON com `team` e `groupchat` valores:

```json
{
    "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.11/MicrosoftTeams.schema.json",
    "manifestVersion": "1.11",
    "version": "1.0.0",
    "id": "%MICROSOFT-APP-ID%",
    "bots": [
        {
            "botId": "%MICROSOFT-APP-ID-REGISTERED-WITH-BOT-FRAMEWORK%",
            "scopes": [
                    "team",
                    "personal",
                    "groupchat"
                ]
        }
    ],
    "composeExtensions": [
        {
            "canUpdateConfiguration": true,
            "botId": "%MICROSOFT-APP-ID-REGISTERED-WITH-BOT-FRAMEWORK%", // Use the same bot as what is specified in the bots section above
        }
    ]
}
```

## <a name="automatic-refresh-for-adaptive-cards-in-search-based-message-extensions"></a>Atualização automática para Cartões Adaptáveis em extensões de mensagem baseadas em pesquisa

Habilite a atualização automática para Cartões Adaptáveis em extensões de mensagem baseadas em pesquisa para garantir que os usuários sempre vejam as informações mais recentes. Para habilitar, defina `userIds` a matriz em  `29:<ID>` ou `8:orgid:<AAD ID>` formatar na `refresh` propriedade. Para obter mais informações, confira [trabalhar com Ações Universais para Cartões Adaptáveis](../../../task-modules-and-cards/cards/Universal-actions-for-adaptive-cards/Work-with-Universal-Actions-for-Adaptive-Cards.md#user-ids-in-refresh).

Exemplo de `userIds` matriz na `refresh` propriedade:

```json
    {
        "type": "AdaptiveCard",
        "refresh": {
            "userIds": [
                "8:orgid:<AADID>",
                "29:<id>"
            ],
            "action": {
                "type": "Action.Execute",
                "data": {}
            }
        },
        "body": [
            {
                "type": "TextBlock",
                "text": "Hello World!",
                "wrap": true
            }
        ],
        "actions": [
            {
                "type": "Action.Execute",
                "data": {},
                "title": "Hello"
            }
        ]
    }
```

> [!NOTE]
> A atualização automática está habilitada para todos os usuários no chat ou canal de grupo com *menos ou igual a* 60 usuários. Para conversas (chat em grupo ou canal) com mais de 60 usuários, os usuários podem usar o botão atualizar no menu de opções de mensagem para obter o resultado mais recente.

Exemplo de na `Action.Execute` `refresh` propriedade:

```json
    {
        "type": "AdaptiveCard",
        "refresh": {
            "action": {
                "type": "Action.Execute",
                "data": {}
            }
        },
        "body": [
            {
                "type": "TextBlock",
                "text": "Hello World!",
                "wrap": true
            }
        ],
        "actions": [
            {
                "type": "Action.Execute",
                "data": {},
                "title": "Hello"
            }
        ]
    }
```

## <a name="just-in-time-install"></a>Instalação just-in-time

O JIT (just-in-time) permite instalar uma extensão de cartão ou mensagem para vários usuários em um chat ou canal em grupo. Para dar suporte a Ações Universais em extensões de mensagem baseadas em pesquisa, o bot é adicionado à conversa em que o cartão (com `Action.Execute`) é enviado pelo usuário.

Quando um usuário seleciona um cartão e o envia em um chat ou canal em grupo, um prompt de instalação **do JIT** é exibido. Depois que o usuário seleciona a opção **enviar** , o aplicativo é adicionado para todos os usuários no chat ou canal em segundo plano.

> [!NOTE]
> Para aplicativos que não têm `Action.Execute` e `refresh` esquema definido, o prompt de instalação não é mostrado aos usuários.

Exemplo de um fluxo de usuário dinâmico de instalação de ME e JIT:

  :::image type="content" source="../../../assets/videos/dynamic-me-jit-flow.gif" alt-text="O GIF mostra o fluxo do usuário para uma extensão de mensagem dinâmica e a instalação do JIT.":::

## <a name="see-also"></a>Confira também

* [Extensões de mensagens](../../what-are-messaging-extensions.md)
* [Cartões Adaptáveis](../../../task-modules-and-cards/what-are-cards.md#adaptive-cards)
* [Ações Universais para Cartões Adaptáveis](../../../task-modules-and-cards/cards/Universal-actions-for-adaptive-cards/Overview.md)
