---
title: Atualizar e excluir mensagens enviadas do bot
author: WashingtonKayaker
description: Como atualizar e excluir mensagens enviadas do bot do Microsoft Teams
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 222409fa0d02a571b7295dedb0c60b1ca3f90cca
ms.sourcegitcommit: 61edf47c9dd1dbc1df03d0d9fb83bfedca4c423b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2020
ms.locfileid: "43914606"
---
# <a name="update-and-delete-messages-sent-from-your-bot"></a><span data-ttu-id="8e68d-103">Atualizar e excluir mensagens enviadas do bot</span><span class="sxs-lookup"><span data-stu-id="8e68d-103">Update and delete messages sent from your bot</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

## <a name="updating-messages"></a><span data-ttu-id="8e68d-104">Atualizando mensagens</span><span class="sxs-lookup"><span data-stu-id="8e68d-104">Updating messages</span></span>

<span data-ttu-id="8e68d-105">Em vez de fazer com que suas mensagens sejam instantâneos de dados estáticos, seu bot pode atualizar mensagens dinamicamente após enviá-las.</span><span class="sxs-lookup"><span data-stu-id="8e68d-105">Rather than have your messages be static snapshots of data, your bot can dynamically update messages after sending them.</span></span> <span data-ttu-id="8e68d-106">Você pode usar atualizações de mensagens dinâmicas para cenários como atualizações de pesquisa, modificação de ações disponíveis após um pressionamento de botão ou qualquer outra alteração de estado assíncrono.</span><span class="sxs-lookup"><span data-stu-id="8e68d-106">You can use dynamic message updates for scenarios such as poll updates, modifying available actions after a button press, or any other asynchronous state change.</span></span>

<span data-ttu-id="8e68d-107">A nova mensagem não precisa coincidir com o original no tipo.</span><span class="sxs-lookup"><span data-stu-id="8e68d-107">The new message need not match the original in type.</span></span> <span data-ttu-id="8e68d-108">Por exemplo, se a mensagem original contiver um anexo, a nova mensagem poderá ser uma mensagem de texto simples.</span><span class="sxs-lookup"><span data-stu-id="8e68d-108">For instance, if the original message contained an attachment, the new message can be a simple text message.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="8e68d-109">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="8e68d-109">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="8e68d-110">Para atualizar uma mensagem existente, passe um novo `Activity` objeto com a ID de atividade existente para `UpdateActivityAsync` o método da `TurnContext` classe.</span><span class="sxs-lookup"><span data-stu-id="8e68d-110">To update an existing message, pass a new `Activity` object with the existing activity ID to the `UpdateActivityAsync` method of the `TurnContext` class.</span></span> <span data-ttu-id="8e68d-111">*Consulte* [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable)</span><span class="sxs-lookup"><span data-stu-id="8e68d-111">*See* [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable)</span></span>

```csharp
var newActivity = MessageFactory.Text("The new text for the activity");
newActivity.Id = activityId;
await turnContext.UpdateActivityAsync(newActivity, cancellationToken);
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="8e68d-112">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="8e68d-112">TypeScript/Node.js</span></span>](#tab/typescript)

<span data-ttu-id="8e68d-113">Para atualizar uma mensagem existente, passe um novo `Activity` objeto com a ID de atividade existente para `updateActivity` o método do `TurnContext` objeto.</span><span class="sxs-lookup"><span data-stu-id="8e68d-113">To update an existing message, pass a new `Activity` object with the existing activity ID to the `updateActivity` method of the `TurnContext` object.</span></span> <span data-ttu-id="8e68d-114">*Consulte* [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--)</span><span class="sxs-lookup"><span data-stu-id="8e68d-114">*See* [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--)</span></span>

```typescript
const newActivity = MessageFactory.text('The new text for the activity');
newActivity.id = activityId;
await turnContext.updateActivity(newActivity);
```

# <a name="python"></a>[<span data-ttu-id="8e68d-115">Python</span><span class="sxs-lookup"><span data-stu-id="8e68d-115">Python</span></span>](#tab/python)

<span data-ttu-id="8e68d-116">Para atualizar uma mensagem existente, passe um novo `Activity` objeto com a ID de atividade existente para `update_activity` o método da `TurnContext` classe.</span><span class="sxs-lookup"><span data-stu-id="8e68d-116">To update an existing message, pass a new `Activity` object with the existing activity ID to the `update_activity` method of the `TurnContext` class.</span></span> <span data-ttu-id="8e68d-117">Consulte [TurnContextClass](link to Python API ref docs).</span><span class="sxs-lookup"><span data-stu-id="8e68d-117">See [TurnContextClass](link to Python API ref docs).</span></span>

```python

new_activity = MessageFactory.text("The new text for the activity")
new_activity.id = activity_id
update_result = await context.update_activity(new_activity)

```

---

## <a name="deleting-messages"></a><span data-ttu-id="8e68d-118">Excluir mensagens</span><span class="sxs-lookup"><span data-stu-id="8e68d-118">Deleting messages</span></span>

<span data-ttu-id="8e68d-119">Na estrutura do bot, cada mensagem tem seu próprio identificador de atividade exclusivo.</span><span class="sxs-lookup"><span data-stu-id="8e68d-119">In the Bot Framework, every message has its own unique activity identifier.</span></span>
<span data-ttu-id="8e68d-120">As mensagens podem ser excluídas usando o método `DeleteActivity` da estrutura de bot, conforme mostrado aqui.</span><span class="sxs-lookup"><span data-stu-id="8e68d-120">Messages can be deleted using the Bot Framework's `DeleteActivity` method as shown here.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="8e68d-121">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="8e68d-121">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="8e68d-122">Para excluir essa mensagem, passe a ID da atividade para o `DeleteActivityAsync` método da `TurnContext` classe.</span><span class="sxs-lookup"><span data-stu-id="8e68d-122">To delete that message, pass that activity's ID to the `DeleteActivityAsync` method of the `TurnContext` class.</span></span> <span data-ttu-id="8e68d-123">*Confira* o [método TurnContext. DeleteActivityAsync](/dotnet/api/microsoft.bot.builder.turncontext.deleteactivityasync?view=botbuilder-dotnet-stable)</span><span class="sxs-lookup"><span data-stu-id="8e68d-123">*See* [TurnContext.DeleteActivityAsync Method](/dotnet/api/microsoft.bot.builder.turncontext.deleteactivityasync?view=botbuilder-dotnet-stable)</span></span>

```csharp
foreach (var activityId in _list)
{
    await turnContext.DeleteActivityAsync(activityId, cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="8e68d-124">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="8e68d-124">TypeScript/Node.js</span></span>](#tab/typescript)

<span data-ttu-id="8e68d-125">Para excluir essa mensagem, passe a ID dessa atividade para o `deleteActivity` método do `TurnContext` objeto.</span><span class="sxs-lookup"><span data-stu-id="8e68d-125">To delete that message, pass that activity's ID to the `deleteActivity` method of the `TurnContext` object.</span></span> <span data-ttu-id="8e68d-126">*Consulte* [deleteActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#deleteactivity-string---partial-conversationreference--)</span><span class="sxs-lookup"><span data-stu-id="8e68d-126">*See* [deleteActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#deleteactivity-string---partial-conversationreference--)</span></span>

```typescript
for (let i = 0; i < activityIds.length; i++) {
    await turnContext.deleteActivity(activityIds[i]);
}
```

# <a name="python"></a>[<span data-ttu-id="8e68d-127">Python</span><span class="sxs-lookup"><span data-stu-id="8e68d-127">Python</span></span>](#tab/python)

<span data-ttu-id="8e68d-128">Para excluir essa mensagem, passe a ID dessa atividade para o `delete_activity` método do `TurnContext` objeto.</span><span class="sxs-lookup"><span data-stu-id="8e68d-128">To delete that message, pass that activity's ID to the `delete_activity` method of the `TurnContext` object.</span></span> <span data-ttu-id="8e68d-129">Consulte [Activity-Update-and-Delete](https://github.com/microsoft/botbuilder-python/blob/c04ecacb22c1f4b43a671fe2f1e4782218391975/tests/teams/scenarios/activity-update-and-delete/bots/activity_update_and_delete_bot.py).</span><span class="sxs-lookup"><span data-stu-id="8e68d-129">See [activity-update-and-delete](https://github.com/microsoft/botbuilder-python/blob/c04ecacb22c1f4b43a671fe2f1e4782218391975/tests/teams/scenarios/activity-update-and-delete/bots/activity_update_and_delete_bot.py).</span></span>

```python
for each activity_id in _list:
    await TurnContext.delete_activity(activity_id)
```

---

