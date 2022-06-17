---
title: Bots somente de notificação
description: Neste módulo, saiba o que os bots somente notificação estão no Microsoft Teams, no manifesto do aplicativo e em suas melhores práticas e limitações
ms.topic: conceptual
ms.localizationpriority: medium
ms.date: 01/29/2020
ms.openlocfilehash: 547ef73cfd036efe566afe15e4f50701a275c2cd
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66144296"
---
# <a name="notification-only-bots-in-microsoft-teams"></a>Bots somente notificação no Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Se a única finalidade do bot for fornecer notificação aos usuários e não for conversacional, `isNotificationOnly` você poderá habilitar o campo no manifesto do aplicativo. Isso produz as seguintes alterações:

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

* Os bots somente notificação usam mensagens proativas para se comunicar com o usuário. Para obter mais informações, consulte [mensagens proativas para bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md).
