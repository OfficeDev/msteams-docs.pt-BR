---
title: Bots somente de notificação
description: Descreve quais bots somente notificação estão no Microsoft Teams
keywords: Notificação de bots do teams
ms.topic: conceptual
localization_priority: Normal
ms.date: 01/29/2020
ms.openlocfilehash: 3de462f73733f5f7cf223444ffe6deeb53faaaaa
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566758"
---
# <a name="notification-only-bots-in-microsoft-teams"></a>Bots somente notificação Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Se o único objetivo do bot é fornecer notificação aos usuários e não for conversa, você poderá habilitar o campo `isNotificationOnly` no manifesto do aplicativo. Isso produz as seguintes alterações:

* Os usuários não podem enviar mensagens ao bot somente notificação.
* Os usuários não @mention o bot.

> [!NOTE]
> Os aplicativos somente bot aparecerão na bandeja do aplicativo pessoal em ambos os casos: `isNotificationOnly: true` ou `isNotificationOnly: false` .

## <a name="app-manifest"></a>Manifesto do aplicativo

Para habilitar isso, de definir `isNotificationOnly` como `true` .

> [!NOTE]
> Esteja ciente de que o valor de `isNotificationOnly` é booleano e não uma cadeia de caracteres.

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

## <a name="best-practices-and-limitations"></a>Melhores práticas e limitações

* Os bots somente notificação usam mensagens proativas para se comunicar com o usuário. Para obter mais informações, consulte [Mensagens proativas para bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md).
