---
title: Bots somente de notificação
description: Descreve o que são bots somente notificação no Microsoft Teams
keywords: notificação de bots do teams
ms.topic: conceptual
ms.localizationpriority: high
ms.date: 01/29/2020
ms.openlocfilehash: 1ee009fb76a52bcebdd3fe24c7a672f1ed455b42
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111476"
---
# <a name="notification-only-bots-in-microsoft-teams"></a>Bots somente notificação no Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Se a única finalidade do bot for fornecer notificação aos usuários e não for conversacional, você poderá habilitar o campo `isNotificationOnly` no manifesto do aplicativo. Isso produz as seguintes alterações:

* Os usuários não podem enviar mensagens ao bot somente notificação.
* Os usuários não podem @menção o bot.

> [!NOTE]
> Os aplicativos somente bot serão exibidos na bandeja pessoal do aplicativo em ambos os casos: `isNotificationOnly: true` ou `isNotificationOnly: false`.

## <a name="app-manifest"></a>Manifesto do aplicativo

Para habilitar isso, defina `isNotificationOnly` como `true`.

> [!NOTE]
> O valor de `isNotificationOnly` é booliano e não uma cadeia de caracteres.

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

* Os bots somente notificação usam mensagens proativas para se comunicar com o usuário. Para obter mais informações, consulte [mensagens proativas para bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md).
