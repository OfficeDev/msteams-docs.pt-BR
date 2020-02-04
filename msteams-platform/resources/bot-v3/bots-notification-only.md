---
title: Somente bots de notificação
description: Descreve o que são somente notificações de bots no Microsoft Teams
keywords: notificação de bots do teams
ms.date: 05/20/2019
ms.openlocfilehash: 37652bc2d6171191c81be4e5a2875f47c79574f9
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672489"
---
# <a name="notification-only-bots-in-microsoft-teams"></a>Notificações somente bots no Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Se o único objetivo do seu bot é entregar a notificação para os usuários e não é uma conversa, você pode `isNotificationOnly` habilitar o campo em seu manifesto do aplicativo. Isso produz as seguintes alterações:

* Os usuários não podem Messager o bot somente para notificação.
* Os usuários não podem @mention o bot.

## <a name="app-manifest"></a>Manifesto do aplicativo

Para habilitar isso, defina `isNotificationOnly` como `true`.

> [!NOTE]
> Lembre-se de que o `isNotificationOnly` valor de é booliano e não uma cadeia de caracteres.

```json
{
  ⋮
  "bots":[
    {
      "botId":"[Microsoft App ID for your bot]",
      "isNotificationOnly": true,
      "scopes": [
        "personal",
        "team"
      ],
    }
  ],
  ...
}
```

## <a name="best-practices-and-limitations"></a>Práticas recomendadas e limitações

* Você não pode criar `personal` um bot de notificação somente com escopo, já que o usuário não pode Messager o bot de notificação somente em um chat pessoal. Isso significa que você não pode receber `conversationUpdate` um evento que fornecerá os detalhes necessários para enviar uma notificação. Seu bot de notificação somente funcionará corretamente se oferecer suporte ao `team` escopo e adicionado a uma equipe. Na configuração de equipe, seu bot terá acesso às informações necessárias para enviar uma notificação para um canal ou de forma privada para um usuário.
* Notificações somente os bots usam mensagens pró-ativas para se comunicar com o usuário. Consulte [Proactive Messaging for bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) para obter mais detalhes.
