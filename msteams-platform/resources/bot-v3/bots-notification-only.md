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
# <a name="notification-only-bots-in-microsoft-teams"></a><span data-ttu-id="91748-104">Bots somente de notificação em Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="91748-104">Notification-only bots in Microsoft Teams</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="91748-105">Se o único propósito do seu bot é entregar notificação aos usuários e não for conversador, você pode ativar o campo no manifesto do `isNotificationOnly` aplicativo.</span><span class="sxs-lookup"><span data-stu-id="91748-105">If your bot's sole purpose is to deliver notification to users and is not conversational, you can enable the `isNotificationOnly` field in your app manifest.</span></span> <span data-ttu-id="91748-106">Isso produz as seguintes alterações:</span><span class="sxs-lookup"><span data-stu-id="91748-106">This produces the following changes:</span></span>

* <span data-ttu-id="91748-107">Os usuários não podem enviar mensagens para o bot somente de notificação.</span><span class="sxs-lookup"><span data-stu-id="91748-107">Users cannot message your notification-only bot.</span></span>
* <span data-ttu-id="91748-108">Os usuários não podem @mention o bot.</span><span class="sxs-lookup"><span data-stu-id="91748-108">Users cannot @mention the bot.</span></span>

> [!NOTE]
> <span data-ttu-id="91748-109">Os aplicativos somente para bots surgirão na bandeja do aplicativo pessoal em ambos os casos: `isNotificationOnly: true` ou `isNotificationOnly: false` .</span><span class="sxs-lookup"><span data-stu-id="91748-109">The bot-only apps will surface in the personal app tray in both cases: `isNotificationOnly: true` or `isNotificationOnly: false`.</span></span>

## <a name="app-manifest"></a><span data-ttu-id="91748-110">Manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="91748-110">App manifest</span></span>

<span data-ttu-id="91748-111">Para habilitar isso, `isNotificationOnly` `true` defina.</span><span class="sxs-lookup"><span data-stu-id="91748-111">To enable this, set `isNotificationOnly` to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="91748-112">Esteja ciente de que o valor `isNotificationOnly` é booleano e não uma corda.</span><span class="sxs-lookup"><span data-stu-id="91748-112">Be aware that the value of `isNotificationOnly` is boolean and not a string.</span></span>

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

## <a name="best-practices-and-limitations"></a><span data-ttu-id="91748-113">Melhores práticas e limitações</span><span class="sxs-lookup"><span data-stu-id="91748-113">Best practices and limitations</span></span>

* <span data-ttu-id="91748-114">Bots somente de notificação usam mensagens proativas para se comunicar com o usuário.</span><span class="sxs-lookup"><span data-stu-id="91748-114">Notification-only bots use proactive messaging to communicate with the user.</span></span> <span data-ttu-id="91748-115">Para obter mais informações, consulte [mensagens proativas para bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md).</span><span class="sxs-lookup"><span data-stu-id="91748-115">For more information, see [Proactive messaging for bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md).</span></span>
