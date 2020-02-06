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
# <a name="notification-only-bots-in-microsoft-teams"></a><span data-ttu-id="b4ce4-104">Bots somente de notificação no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="b4ce4-104">Notification-only bots in Microsoft Teams</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="b4ce4-105">Se o único objetivo do seu bot é entregar a notificação para os usuários e não é uma conversa, você pode `isNotificationOnly` habilitar o campo em seu manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b4ce4-105">If your bot's sole purpose is to deliver notification to users and is not conversational, you can enable the `isNotificationOnly` field in your app manifest.</span></span> <span data-ttu-id="b4ce4-106">Isso produz as seguintes alterações:</span><span class="sxs-lookup"><span data-stu-id="b4ce4-106">This produces the following changes:</span></span>

* <span data-ttu-id="b4ce4-107">Os usuários não podem Messager o bot somente para notificação.</span><span class="sxs-lookup"><span data-stu-id="b4ce4-107">Users cannot message your notification-only bot.</span></span>
* <span data-ttu-id="b4ce4-108">Os usuários não podem @mention o bot.</span><span class="sxs-lookup"><span data-stu-id="b4ce4-108">Users cannot @mention the bot.</span></span>

## <a name="app-manifest"></a><span data-ttu-id="b4ce4-109">Manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="b4ce4-109">App manifest</span></span>

<span data-ttu-id="b4ce4-110">Para habilitar isso, defina `isNotificationOnly` como `true`.</span><span class="sxs-lookup"><span data-stu-id="b4ce4-110">To enable this, set `isNotificationOnly` to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="b4ce4-111">Lembre-se de que o `isNotificationOnly` valor de é booliano e não uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b4ce4-111">Be aware that the value of `isNotificationOnly` is boolean and not a string.</span></span>

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

## <a name="best-practices-and-limitations"></a><span data-ttu-id="b4ce4-112">Práticas recomendadas e limitações</span><span class="sxs-lookup"><span data-stu-id="b4ce4-112">Best practices and limitations</span></span>

* <span data-ttu-id="b4ce4-113">Bots somente de notificação usam mensagens proativas para se comunicar com o usuário.</span><span class="sxs-lookup"><span data-stu-id="b4ce4-113">Notification-only bots use proactive messaging to communicate with the user.</span></span> <span data-ttu-id="b4ce4-114">Consulte [Proactive Messaging for bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="b4ce4-114">See [Proactive messaging for bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) for more details.</span></span>
