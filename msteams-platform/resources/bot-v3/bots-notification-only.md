---
title: Bots somente de notificação
description: Descreve quais bots somente notificação estão no Microsoft Teams
keywords: Notificação de bots do teams
ms.topic: conceptual
ms.localizationpriority: medium
ms.date: 01/29/2020
ms.openlocfilehash: d3ee5343ea159950859237f2a488557d9063eb6e
ms.sourcegitcommit: 2fdca6fb0ade3f6b460eb9a4dfea0a8e2ab8d3b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63355724"
---
# <a name="notification-only-bots-in-microsoft-teams"></a>Bots somente notificação Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Se o único objetivo do bot é fornecer notificação aos usuários e não for conversa, você poderá `isNotificationOnly` habilitar o campo no manifesto do aplicativo. Isso produz as seguintes alterações:

* Os usuários não podem enviar mensagens ao bot somente notificação.
* Os usuários não @mention o bot.

> [!NOTE]
> Os aplicativos somente bot aparecerão na bandeja do aplicativo pessoal em ambos os casos: `isNotificationOnly: true` ou `isNotificationOnly: false`.

## <a name="app-manifest"></a>Manifesto do aplicativo

Para habilitar isso, de definir `isNotificationOnly` como `true`.

> [!NOTE]
> O valor de `isNotificationOnly` é Boolean e não uma cadeia de caracteres.

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
