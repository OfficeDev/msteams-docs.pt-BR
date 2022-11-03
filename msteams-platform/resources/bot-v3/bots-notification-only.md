---
title: Bots somente de notificação
description: Neste módulo, saiba quais bots somente notificações estão no Microsoft Teams, manifesto de aplicativo e suas melhores práticas e limitações
ms.topic: conceptual
ms.localizationpriority: medium
ms.date: 01/29/2020
ms.openlocfilehash: ac412f37cba03c5da43163bf2eadd47adc676f08
ms.sourcegitcommit: c3601696cced9aadc764f1e734646ee7711f154c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2022
ms.locfileid: "68833013"
---
# <a name="notification-only-bots-in-microsoft-teams"></a>Bots somente notificação no Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Se a única finalidade do bot for fornecer notificação aos usuários e não for conversacional, você poderá habilitar o campo no manifesto do `isNotificationOnly` aplicativo. Isso produz as seguintes alterações:

* Os usuários não podem enviar mensagens ao bot somente notificação.
* Os usuários não podem @mention o bot.

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

Os bots somente notificação usam mensagens proativas para se comunicar com o usuário. Para obter mais informações, consulte [mensagens proativas para bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md).
