---
title: Ações universais para extensões de mensagem baseadas em pesquisa
author: v-ypalikila
description: Neste artigo, saiba mais sobre ações universais e atualização automática para cartões adaptáveis em extensões de mensagens baseadas em pesquisa.
ms.topic: conceptual
ms.author: v-ypalikila
ms.localizationpriority: medium
ms.openlocfilehash: 78b8c525b51603245fc379a826fa0cc11cbc5fd8
ms.sourcegitcommit: 176bbca74ba46b7ac298899d19a2d75087fb37c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2022
ms.locfileid: "68376589"
---
# <a name="universal-actions-for-search-based-message-extensions"></a>Ações universais para extensões de mensagem baseadas em pesquisa

Os Cartões Adaptáveis em extensões de mensagem baseadas em pesquisa agora dão suporte a Ações Universais. Para habilitar as Ações Universais para extensões de mensagem baseadas em pesquisa, o aplicativo deve estar em conformidade com o esquema de Ações [Universais para Cartões Adaptáveis](../../../task-modules-and-cards/cards/Universal-actions-for-adaptive-cards/Work-with-Universal-Actions-for-Adaptive-Cards.md#schema-for-universal-actions-for-adaptive-cards) , juntamente com os seguintes requisitos:

1. O aplicativo deve ter um bot de conversa definido no manifesto do aplicativo.
1. Se você já tiver um bot de conversação, deverá usar o mesmo bot que é usado em sua extensão de mensagem.
1. Se o cartão for enviado em um grupo, o aplicativo deverá especificar `team` ou `groupchat` definir o escopo em seu bot no manifesto.

Exemplo de um esquema JSON com e `team` `groupchat` valores:

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

Habilite a atualização automática para Cartões Adaptáveis em extensões de mensagem baseadas em pesquisa para garantir que os usuários sempre vejam as informações mais recentes. Para habilitar, defina `userIds` a matriz na  `29:<ID>` propriedade `8:orgid:<AAD ID>` ou no formato `refresh` . Para obter mais informações, [consulte trabalhar com Ações Universais para Cartões Adaptáveis](../../../task-modules-and-cards/cards/Universal-actions-for-adaptive-cards/Work-with-Universal-Actions-for-Adaptive-Cards.md#user-ids-in-refresh).

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
> A atualização automática está habilitada para todos os usuários no chat em grupo ou canal com *menos ou igual a* 60 usuários. Para conversas (chat em grupo ou canal) com mais de 60 usuários, os usuários podem usar o botão atualizar no menu de opções de mensagem para obter o resultado mais recente.

Exemplo de `Action.Execute` na `refresh` propriedade:

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

O JIT (Just-In-Time) permite que você instale uma extensão de cartão ou mensagem para vários usuários em um chat em grupo ou canal. Para dar suporte a Ações Universais em extensões de mensagem baseadas em pesquisa, o bot é adicionado à conversa em que o cartão ( `Action.Execute`com) é enviado pelo usuário.

Quando um usuário seleciona um cartão e o envia em um chat em grupo ou canal, um prompt de instalação **JIT** é exibido. Depois que o usuário seleciona a **opção de** envio, o aplicativo é adicionado para todos os usuários no chat ou canal em segundo plano.

> [!NOTE]
> Para aplicativos que não têm e `Action.Execute` esquema `refresh` definido, o prompt de instalação não é mostrado aos usuários.

Exemplo de um fluxo de usuário de instalação me e JIT dinâmico:

  :::image type="content" source="../../../assets/videos/dynamic-me-jit-flow.gif" alt-text="O GIF mostra o fluxo do usuário para uma extensão de mensagem dinâmica e uma instalação JIT.":::

## <a name="see-also"></a>Confira também

* [Extensões de mensagens](../../what-are-messaging-extensions.md)
* [Ações Universais para Cartões Adaptáveis](../../../task-modules-and-cards/cards/Universal-actions-for-adaptive-cards/Overview.md)
