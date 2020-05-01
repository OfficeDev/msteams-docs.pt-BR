---
title: Atualizar e excluir mensagens enviadas do bot
author: WashingtonKayaker
description: Como atualizar e excluir mensagens enviadas do bot do Microsoft Teams
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 46994c6810197002ef1c108af4f725426395b37f
ms.sourcegitcommit: 2b1fd50466d807869fd173371ba7dfd82a0064ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2020
ms.locfileid: "43957184"
---
# <a name="update-and-delete-messages-sent-from-your-bot"></a><span data-ttu-id="f8b55-103">Atualizar e excluir mensagens enviadas do bot</span><span class="sxs-lookup"><span data-stu-id="f8b55-103">Update and delete messages sent from your bot</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

## <a name="updating-messages"></a><span data-ttu-id="f8b55-104">Atualizando mensagens</span><span class="sxs-lookup"><span data-stu-id="f8b55-104">Updating messages</span></span>

<span data-ttu-id="f8b55-105">Em vez de fazer com que suas mensagens sejam instantâneos de dados estáticos, seu bot pode atualizar mensagens dinamicamente após enviá-las.</span><span class="sxs-lookup"><span data-stu-id="f8b55-105">Rather than have your messages be static snapshots of data, your bot can dynamically update messages after sending them.</span></span> <span data-ttu-id="f8b55-106">Você pode usar atualizações de mensagens dinâmicas para cenários como atualizações de pesquisa, modificação de ações disponíveis após um pressionamento de botão ou qualquer outra alteração de estado assíncrono.</span><span class="sxs-lookup"><span data-stu-id="f8b55-106">You can use dynamic message updates for scenarios such as poll updates, modifying available actions after a button press, or any other asynchronous state change.</span></span>

<span data-ttu-id="f8b55-107">A nova mensagem não precisa coincidir com o original no tipo.</span><span class="sxs-lookup"><span data-stu-id="f8b55-107">The new message need not match the original in type.</span></span> <span data-ttu-id="f8b55-108">Por exemplo, se a mensagem original contiver um anexo, a nova mensagem poderá ser uma mensagem de texto simples.</span><span class="sxs-lookup"><span data-stu-id="f8b55-108">For instance, if the original message contained an attachment, the new message can be a simple text message.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="f8b55-109">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="f8b55-109">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="f8b55-110">Para atualizar uma mensagem existente, passe um novo `Activity` objeto com a ID de atividade existente para `UpdateActivityAsync` o método da `TurnContext` classe.</span><span class="sxs-lookup"><span data-stu-id="f8b55-110">To update an existing message, pass a new `Activity` object with the existing activity ID to the `UpdateActivityAsync` method of the `TurnContext` class.</span></span> <span data-ttu-id="f8b55-111">*Consulte* [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable)</span><span class="sxs-lookup"><span data-stu-id="f8b55-111">*See* [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable)</span></span>

```csharp
var newActivity = MessageFactory.Text("The new text for the activity");
newActivity.Id = activityId;
await turnContext.UpdateActivityAsync(newActivity, cancellationToken);
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="f8b55-112">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="f8b55-112">TypeScript/Node.js</span></span>](#tab/typescript)

<span data-ttu-id="f8b55-113">Para atualizar uma mensagem existente, passe um novo `Activity` objeto com a ID de atividade existente para `updateActivity` o método do `TurnContext` objeto.</span><span class="sxs-lookup"><span data-stu-id="f8b55-113">To update an existing message, pass a new `Activity` object with the existing activity ID to the `updateActivity` method of the `TurnContext` object.</span></span> <span data-ttu-id="f8b55-114">*Consulte* [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--)</span><span class="sxs-lookup"><span data-stu-id="f8b55-114">*See* [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--)</span></span>

```typescript
const newActivity = MessageFactory.text('The new text for the activity');
newActivity.id = activityId;
await turnContext.updateActivity(newActivity);
```

# <a name="python"></a>[<span data-ttu-id="f8b55-115">Python</span><span class="sxs-lookup"><span data-stu-id="f8b55-115">Python</span></span>](#tab/python)

<span data-ttu-id="f8b55-116">Para atualizar uma mensagem existente, passe um novo `Activity` objeto com a ID de atividade existente para `update_activity` o método da `TurnContext` classe.</span><span class="sxs-lookup"><span data-stu-id="f8b55-116">To update an existing message, pass a new `Activity` object with the existing activity ID to the `update_activity` method of the `TurnContext` class.</span></span> <span data-ttu-id="f8b55-117">Consulte [TurnContextClass](link to Python API ref docs).</span><span class="sxs-lookup"><span data-stu-id="f8b55-117">See [TurnContextClass](link to Python API ref docs).</span></span>

```python

new_activity = MessageFactory.text("The new text for the activity")
new_activity.id = activity_id
update_result = await context.update_activity(new_activity)

```

# <a name="rest-api"></a>[<span data-ttu-id="f8b55-118">API REST</span><span class="sxs-lookup"><span data-stu-id="f8b55-118">REST API</span></span>](#tab/rest)

>[!NOTE]
><span data-ttu-id="f8b55-119">Você pode desenvolver aplicativos do teams em qualquer tecnologia de programação Web e chamar diretamente as [APIs REST do serviço do conector do bot](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0).</span><span class="sxs-lookup"><span data-stu-id="f8b55-119">You can develop Teams apps in any web-programming technology and directly call the [Bot Connector service REST APIs](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0).</span></span> <span data-ttu-id="f8b55-120">Para fazer isso, você precisará implementar procedimentos de segurança de [autenticação](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0) com suas solicitações de API.</span><span class="sxs-lookup"><span data-stu-id="f8b55-120">To do so, you'll need to implement [Authentication](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0) security procedures with your API requests.</span></span>

<span data-ttu-id="f8b55-121">Para atualizar uma atividade existente em uma conversa, inclua o `conversationId` e `activityId` o ponto de extremidade da solicitação.</span><span class="sxs-lookup"><span data-stu-id="f8b55-121">To update an existing activity within a conversation, include the `conversationId` and `activityId` in the request endpoint.</span></span> <span data-ttu-id="f8b55-122">Para concluir esse cenário, você deve armazenar em cache a ID da atividade retornada pela chamada POST original.</span><span class="sxs-lookup"><span data-stu-id="f8b55-122">To complete this scenario, you should cache the activity ID returned by the original POST call.</span></span>

```http
PUT /v3/conversations/{conversationId}/activities/{activityId}
```

| | |
|----|----|
| <span data-ttu-id="f8b55-123">**Corpo da solicitação**</span><span class="sxs-lookup"><span data-stu-id="f8b55-123">**Request body**</span></span> | <span data-ttu-id="f8b55-124">Um objeto [Activity](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object)</span><span class="sxs-lookup"><span data-stu-id="f8b55-124">An [Activity](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object) object</span></span> |
| <span data-ttu-id="f8b55-125">**Retorna**</span><span class="sxs-lookup"><span data-stu-id="f8b55-125">**Returns**</span></span> | <span data-ttu-id="f8b55-126">Um objeto [ResourceResponse](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object)</span><span class="sxs-lookup"><span data-stu-id="f8b55-126">A [ResourceResponse](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object) object</span></span> |

---

## <a name="deleting-messages"></a><span data-ttu-id="f8b55-127">Excluir mensagens</span><span class="sxs-lookup"><span data-stu-id="f8b55-127">Deleting messages</span></span>

<span data-ttu-id="f8b55-128">Na estrutura do bot, cada mensagem tem seu próprio identificador de atividade exclusivo.</span><span class="sxs-lookup"><span data-stu-id="f8b55-128">In the Bot Framework, every message has its own unique activity identifier.</span></span>
<span data-ttu-id="f8b55-129">As mensagens podem ser excluídas usando o método `DeleteActivity` da estrutura de bot, conforme mostrado aqui.</span><span class="sxs-lookup"><span data-stu-id="f8b55-129">Messages can be deleted using the Bot Framework's `DeleteActivity` method as shown here.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="f8b55-130">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="f8b55-130">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="f8b55-131">Para excluir essa mensagem, passe a ID da atividade para o `DeleteActivityAsync` método da `TurnContext` classe.</span><span class="sxs-lookup"><span data-stu-id="f8b55-131">To delete that message, pass that activity's ID to the `DeleteActivityAsync` method of the `TurnContext` class.</span></span> <span data-ttu-id="f8b55-132">*Confira* o [método TurnContext. DeleteActivityAsync](/dotnet/api/microsoft.bot.builder.turncontext.deleteactivityasync?view=botbuilder-dotnet-stable)</span><span class="sxs-lookup"><span data-stu-id="f8b55-132">*See* [TurnContext.DeleteActivityAsync Method](/dotnet/api/microsoft.bot.builder.turncontext.deleteactivityasync?view=botbuilder-dotnet-stable)</span></span>

```csharp
foreach (var activityId in _list)
{
    await turnContext.DeleteActivityAsync(activityId, cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="f8b55-133">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="f8b55-133">TypeScript/Node.js</span></span>](#tab/typescript)

<span data-ttu-id="f8b55-134">Para excluir essa mensagem, passe a ID dessa atividade para o `deleteActivity` método do `TurnContext` objeto.</span><span class="sxs-lookup"><span data-stu-id="f8b55-134">To delete that message, pass that activity's ID to the `deleteActivity` method of the `TurnContext` object.</span></span> <span data-ttu-id="f8b55-135">*Consulte* [deleteActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#deleteactivity-string---partial-conversationreference--)</span><span class="sxs-lookup"><span data-stu-id="f8b55-135">*See* [deleteActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#deleteactivity-string---partial-conversationreference--)</span></span>

```typescript
for (let i = 0; i < activityIds.length; i++) {
    await turnContext.deleteActivity(activityIds[i]);
}
```

# <a name="python"></a>[<span data-ttu-id="f8b55-136">Python</span><span class="sxs-lookup"><span data-stu-id="f8b55-136">Python</span></span>](#tab/python)

<span data-ttu-id="f8b55-137">Para excluir essa mensagem, passe a ID dessa atividade para o `delete_activity` método do `TurnContext` objeto.</span><span class="sxs-lookup"><span data-stu-id="f8b55-137">To delete that message, pass that activity's ID to the `delete_activity` method of the `TurnContext` object.</span></span> <span data-ttu-id="f8b55-138">Consulte [Activity-Update-and-Delete](https://github.com/microsoft/botbuilder-python/blob/c04ecacb22c1f4b43a671fe2f1e4782218391975/tests/teams/scenarios/activity-update-and-delete/bots/activity_update_and_delete_bot.py).</span><span class="sxs-lookup"><span data-stu-id="f8b55-138">See [activity-update-and-delete](https://github.com/microsoft/botbuilder-python/blob/c04ecacb22c1f4b43a671fe2f1e4782218391975/tests/teams/scenarios/activity-update-and-delete/bots/activity_update_and_delete_bot.py).</span></span>

```python
for each activity_id in _list:
    await TurnContext.delete_activity(activity_id)
```

# <a name="rest-api"></a>[<span data-ttu-id="f8b55-139">API REST</span><span class="sxs-lookup"><span data-stu-id="f8b55-139">REST API</span></span>](#tab/rest)

 <span data-ttu-id="f8b55-140">Para excluir uma atividade existente em uma conversa, inclua o `conversationId` e `activityId` o ponto de extremidade da solicitação.</span><span class="sxs-lookup"><span data-stu-id="f8b55-140">To delete an existing activity within a conversation, include the `conversationId` and `activityId` in the request endpoint.</span></span>

```http
DELETE /v3/conversations/{conversationId}/activities/{activityId}
```

| | |
|----|----|
| <span data-ttu-id="f8b55-141">**Corpo da solicitação**</span><span class="sxs-lookup"><span data-stu-id="f8b55-141">**Request body**</span></span> | <span data-ttu-id="f8b55-142">n/d</span><span class="sxs-lookup"><span data-stu-id="f8b55-142">n/a</span></span> |
| <span data-ttu-id="f8b55-143">**Retorna**</span><span class="sxs-lookup"><span data-stu-id="f8b55-143">**Returns**</span></span> | <span data-ttu-id="f8b55-144">Um código de status HTTP que indica o resultado da operação.</span><span class="sxs-lookup"><span data-stu-id="f8b55-144">An HTTP Status code that indicates the outcome of the operation.</span></span> <span data-ttu-id="f8b55-145">Nada é especificado no corpo da resposta.</span><span class="sxs-lookup"><span data-stu-id="f8b55-145">Nothing is specified in the body of the response.</span></span> |

---
