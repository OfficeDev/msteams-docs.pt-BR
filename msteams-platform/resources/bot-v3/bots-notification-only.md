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
# <a name="notification-only-bots-in-microsoft-teams"></a><span data-ttu-id="71ef7-104">Bots somente notificação Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="71ef7-104">Notification-only bots in Microsoft Teams</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="71ef7-105">Se o único objetivo do bot é fornecer notificação aos usuários e não for conversa, você poderá habilitar o campo `isNotificationOnly` no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="71ef7-105">If your bot's sole purpose is to deliver notification to users and is not conversational, you can enable the `isNotificationOnly` field in your app manifest.</span></span> <span data-ttu-id="71ef7-106">Isso produz as seguintes alterações:</span><span class="sxs-lookup"><span data-stu-id="71ef7-106">This produces the following changes:</span></span>

* <span data-ttu-id="71ef7-107">Os usuários não podem enviar mensagens ao bot somente notificação.</span><span class="sxs-lookup"><span data-stu-id="71ef7-107">Users cannot message your notification-only bot.</span></span>
* <span data-ttu-id="71ef7-108">Os usuários não @mention o bot.</span><span class="sxs-lookup"><span data-stu-id="71ef7-108">Users cannot @mention the bot.</span></span>

> [!NOTE]
> <span data-ttu-id="71ef7-109">Os aplicativos somente bot aparecerão na bandeja do aplicativo pessoal em ambos os casos: `isNotificationOnly: true` ou `isNotificationOnly: false` .</span><span class="sxs-lookup"><span data-stu-id="71ef7-109">The bot-only apps will surface in the personal app tray in both cases: `isNotificationOnly: true` or `isNotificationOnly: false`.</span></span>

## <a name="app-manifest"></a><span data-ttu-id="71ef7-110">Manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="71ef7-110">App manifest</span></span>

<span data-ttu-id="71ef7-111">Para habilitar isso, de definir `isNotificationOnly` como `true` .</span><span class="sxs-lookup"><span data-stu-id="71ef7-111">To enable this, set `isNotificationOnly` to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="71ef7-112">Esteja ciente de que o valor de `isNotificationOnly` é booleano e não uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="71ef7-112">Be aware that the value of `isNotificationOnly` is boolean and not a string.</span></span>

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

## <a name="best-practices-and-limitations"></a><span data-ttu-id="71ef7-113">Melhores práticas e limitações</span><span class="sxs-lookup"><span data-stu-id="71ef7-113">Best practices and limitations</span></span>

* <span data-ttu-id="71ef7-114">Os bots somente notificação usam mensagens proativas para se comunicar com o usuário.</span><span class="sxs-lookup"><span data-stu-id="71ef7-114">Notification-only bots use proactive messaging to communicate with the user.</span></span> <span data-ttu-id="71ef7-115">Para obter mais informações, consulte [Mensagens proativas para bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md).</span><span class="sxs-lookup"><span data-stu-id="71ef7-115">For more information, see [Proactive messaging for bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md).</span></span>
