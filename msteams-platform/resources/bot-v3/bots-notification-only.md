---
title: Bots somente de notificação
description: Descreve quais bots somente notificação estão Microsoft Teams
keywords: notificação de bots equipes
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
# <a name="notification-only-bots-in-microsoft-teams"></a>Bots somente de notificação em Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Se o único propósito do seu bot é entregar notificação aos usuários e não for conversador, você pode ativar o campo no manifesto do `isNotificationOnly` aplicativo. Isso produz as seguintes alterações:

* Os usuários não podem enviar mensagens para o bot somente de notificação.
* Os usuários não podem @mention o bot.

> [!NOTE]
> Os aplicativos somente para bots surgirão na bandeja do aplicativo pessoal em ambos os casos: `isNotificationOnly: true` ou `isNotificationOnly: false` .

## <a name="app-manifest"></a>Manifesto do aplicativo

Para habilitar isso, `isNotificationOnly` `true` defina.

> [!NOTE]
> Esteja ciente de que o valor `isNotificationOnly` é booleano e não uma corda.

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

* Bots somente de notificação usam mensagens proativas para se comunicar com o usuário. Para obter mais informações, consulte [mensagens proativas para bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md).
