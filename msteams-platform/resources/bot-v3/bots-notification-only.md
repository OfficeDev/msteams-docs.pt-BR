---
title: Bots somente de notificação
description: Descreve quais bots somente de notificação estão no Microsoft Teams
keywords: notificação de bots do teams
ms.date: 01/29/2020
ms.openlocfilehash: d312f9cd4558d35fc2492b5cf0b4f77b65660833
ms.sourcegitcommit: 44ac886c0ca34a16222d3991a61606f8483b8481
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/05/2020
ms.locfileid: "41783903"
---
# <a name="notification-only-bots-in-microsoft-teams"></a>Bots somente de notificação no Microsoft Teams

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

* Bots somente de notificação usam mensagens proativas para se comunicar com o usuário. Consulte [Proactive Messaging for bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) para obter mais detalhes.
