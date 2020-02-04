---
title: Somente bots de notificação
description: Descreve o que são somente notificações de bots no Microsoft Teams
keywords: notificação de bots do teams
ms.date: 05/20/2019
ms.openlocfilehash: 37652bc2d6171191c81be4e5a2875f47c79574f9
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672489"
---
# <a name="notification-only-bots-in-microsoft-teams"></a><span data-ttu-id="741af-104">Notificações somente bots no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="741af-104">Notification only bots in Microsoft Teams</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="741af-105">Se o único objetivo do seu bot é entregar a notificação para os usuários e não é uma conversa, você pode `isNotificationOnly` habilitar o campo em seu manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="741af-105">If your bot's sole purpose is to deliver notification to users and is not conversational, you can enable the `isNotificationOnly` field in your app manifest.</span></span> <span data-ttu-id="741af-106">Isso produz as seguintes alterações:</span><span class="sxs-lookup"><span data-stu-id="741af-106">This produces the following changes:</span></span>

* <span data-ttu-id="741af-107">Os usuários não podem Messager o bot somente para notificação.</span><span class="sxs-lookup"><span data-stu-id="741af-107">Users cannot message your notification only bot.</span></span>
* <span data-ttu-id="741af-108">Os usuários não podem @mention o bot.</span><span class="sxs-lookup"><span data-stu-id="741af-108">Users cannot @mention the bot.</span></span>

## <a name="app-manifest"></a><span data-ttu-id="741af-109">Manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="741af-109">App manifest</span></span>

<span data-ttu-id="741af-110">Para habilitar isso, defina `isNotificationOnly` como `true`.</span><span class="sxs-lookup"><span data-stu-id="741af-110">To enable this, set `isNotificationOnly` to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="741af-111">Lembre-se de que o `isNotificationOnly` valor de é booliano e não uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="741af-111">Be aware that the value of `isNotificationOnly` is boolean and not a string.</span></span>

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

## <a name="best-practices-and-limitations"></a><span data-ttu-id="741af-112">Práticas recomendadas e limitações</span><span class="sxs-lookup"><span data-stu-id="741af-112">Best practices and limitations</span></span>

* <span data-ttu-id="741af-113">Você não pode criar `personal` um bot de notificação somente com escopo, já que o usuário não pode Messager o bot de notificação somente em um chat pessoal.</span><span class="sxs-lookup"><span data-stu-id="741af-113">You cannot create a `personal` scoped notification only bot, as the user cannot message your notification only bot in a personal chat.</span></span> <span data-ttu-id="741af-114">Isso significa que você não pode receber `conversationUpdate` um evento que fornecerá os detalhes necessários para enviar uma notificação.</span><span class="sxs-lookup"><span data-stu-id="741af-114">This means that you can't receive a `conversationUpdate` event that would provide you with the necessary details to send a notification.</span></span> <span data-ttu-id="741af-115">Seu bot de notificação somente funcionará corretamente se oferecer suporte ao `team` escopo e adicionado a uma equipe.</span><span class="sxs-lookup"><span data-stu-id="741af-115">Your notification only bot will only function correctly if it supports the `team` scope and is added to a team.</span></span> <span data-ttu-id="741af-116">Na configuração de equipe, seu bot terá acesso às informações necessárias para enviar uma notificação para um canal ou de forma privada para um usuário.</span><span class="sxs-lookup"><span data-stu-id="741af-116">In the team setting, your bot will have access to the necessary information to either send a notification to a channel or privately to a user.</span></span>
* <span data-ttu-id="741af-117">Notificações somente os bots usam mensagens pró-ativas para se comunicar com o usuário.</span><span class="sxs-lookup"><span data-stu-id="741af-117">Notification only bots use proactive messaging to communicate with the user.</span></span> <span data-ttu-id="741af-118">Consulte [Proactive Messaging for bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="741af-118">See [Proactive messaging for bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) for more details.</span></span>
