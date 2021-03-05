---
title: Atualizar e excluir mensagens enviadas do bot
author: WashingtonKayaker
description: Como atualizar e excluir mensagens enviadas do bot do Microsoft Teams
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 664bd531bdee0093c6766bc23e35d2bf10307eb4
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449497"
---
# <a name="update-and-delete-messages-sent-from-your-bot"></a><span data-ttu-id="9b0eb-103">Atualizar e excluir mensagens enviadas do bot</span><span class="sxs-lookup"><span data-stu-id="9b0eb-103">Update and delete messages sent from your bot</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

## <a name="update-messages"></a><span data-ttu-id="9b0eb-104">Atualizar mensagens</span><span class="sxs-lookup"><span data-stu-id="9b0eb-104">Update messages</span></span>

<span data-ttu-id="9b0eb-105">Seu bot pode atualizar dinamicamente as mensagens depois de enviá-las.</span><span class="sxs-lookup"><span data-stu-id="9b0eb-105">Your bot can dynamically update messages after sending them.</span></span> <span data-ttu-id="9b0eb-106">Você pode usar atualizações dinâmicas de mensagens para cenários como atualizações de sondagem, modificação de ações disponíveis depois de pressionar um botão ou qualquer outra alteração de estado assíncrona.</span><span class="sxs-lookup"><span data-stu-id="9b0eb-106">You can use dynamic message updates for scenarios such as poll updates, modifying available actions after a button press, or any other asynchronous state change.</span></span>

<span data-ttu-id="9b0eb-107">A nova mensagem não precisa corresponder ao tipo original.</span><span class="sxs-lookup"><span data-stu-id="9b0eb-107">The new message need not match the original in type.</span></span> <span data-ttu-id="9b0eb-108">Por exemplo, se a mensagem original contiver um anexo, a nova mensagem poderá ser uma mensagem de texto simples.</span><span class="sxs-lookup"><span data-stu-id="9b0eb-108">For example, if the original message contained an attachment, the new message can be a simple text message.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="9b0eb-109">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="9b0eb-109">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="9b0eb-110">Para atualizar uma mensagem existente, passe um novo objeto com a ID de atividade existente `Activity` para o método da `UpdateActivityAsync` `TurnContext` classe.</span><span class="sxs-lookup"><span data-stu-id="9b0eb-110">To update an existing message, pass a new `Activity` object with the existing activity ID to the `UpdateActivityAsync` method of the `TurnContext` class.</span></span> <span data-ttu-id="9b0eb-111">Consulte [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="9b0eb-111">See [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable&preserve-view=true).</span></span>

```csharp
var newActivity = MessageFactory.Text("The new text for the activity");
newActivity.Id = activityId;
await turnContext.UpdateActivityAsync(newActivity, cancellationToken);
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="9b0eb-112">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="9b0eb-112">TypeScript/Node.js</span></span>](#tab/typescript)

<span data-ttu-id="9b0eb-113">Para atualizar uma mensagem existente, passe um novo objeto com a ID de atividade existente `Activity` para o método do `updateActivity` `TurnContext` objeto.</span><span class="sxs-lookup"><span data-stu-id="9b0eb-113">To update an existing message, pass a new `Activity` object with the existing activity ID to the `updateActivity` method of the `TurnContext` object.</span></span> <span data-ttu-id="9b0eb-114">Consulte [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="9b0eb-114">See [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--&preserve-view=true).</span></span>

```typescript
const newActivity = MessageFactory.text('The new text for the activity');
newActivity.id = activityId;
await turnContext.updateActivity(newActivity);
```

# <a name="python"></a>[<span data-ttu-id="9b0eb-115">Python</span><span class="sxs-lookup"><span data-stu-id="9b0eb-115">Python</span></span>](#tab/python)

<span data-ttu-id="9b0eb-116">Para atualizar uma mensagem existente, passe um novo objeto com a ID de atividade existente `Activity` para o método da `update_activity` `TurnContext` classe.</span><span class="sxs-lookup"><span data-stu-id="9b0eb-116">To update an existing message, pass a new `Activity` object with the existing activity ID to the `update_activity` method of the `TurnContext` class.</span></span> <span data-ttu-id="9b0eb-117">Consulte [TurnContextClass](/python/api/botbuilder-core/botbuilder.core.turncontext?view=botbuilder-py-latest).</span><span class="sxs-lookup"><span data-stu-id="9b0eb-117">See [TurnContextClass](/python/api/botbuilder-core/botbuilder.core.turncontext?view=botbuilder-py-latest).</span></span>

```python

new_activity = MessageFactory.text("The new text for the activity")
new_activity.id = activity_id
update_result = await context.update_activity(new_activity)

```

# <a name="rest-api"></a>[<span data-ttu-id="9b0eb-118">API REST</span><span class="sxs-lookup"><span data-stu-id="9b0eb-118">REST API</span></span>](#tab/rest)

>[!NOTE]
><span data-ttu-id="9b0eb-119">Você pode desenvolver aplicativos do Teams em qualquer tecnologia de programação da Web e chamar diretamente as APIs REST do serviço [do Conector de Bot.](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="9b0eb-119">You can develop Teams apps in any web-programming technology and directly call the [Bot Connector service REST APIs](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span> <span data-ttu-id="9b0eb-120">Para fazer isso, você precisa implementar [procedimentos](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0&preserve-view=true) de segurança de autenticação com suas solicitações de API.</span><span class="sxs-lookup"><span data-stu-id="9b0eb-120">To do so, you need to implement [Authentication](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0&preserve-view=true) security procedures with your API requests.</span></span>

<span data-ttu-id="9b0eb-121">Para atualizar uma atividade existente dentro de uma conversa, inclua `conversationId` o e no ponto de extremidade da `activityId` solicitação.</span><span class="sxs-lookup"><span data-stu-id="9b0eb-121">To update an existing activity within a conversation, include the `conversationId` and `activityId` in the request endpoint.</span></span> <span data-ttu-id="9b0eb-122">Para concluir esse cenário, você deve armazenar em cache a ID de atividade retornada pela chamada POST original.</span><span class="sxs-lookup"><span data-stu-id="9b0eb-122">To complete this scenario, you must cache the activity ID returned by the original POST call.</span></span>

```http
PUT /v3/conversations/{conversationId}/activities/{activityId}
```

| | |
|----|----|
| <span data-ttu-id="9b0eb-123">**Corpo da solicitação**</span><span class="sxs-lookup"><span data-stu-id="9b0eb-123">**Request body**</span></span> | <span data-ttu-id="9b0eb-124">Um [objeto Activity](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="9b0eb-124">An [Activity](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object&preserve-view=true) object</span></span> |
| <span data-ttu-id="9b0eb-125">**Retorna**</span><span class="sxs-lookup"><span data-stu-id="9b0eb-125">**Returns**</span></span> | <span data-ttu-id="9b0eb-126">Um [objeto ResourceResponse](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="9b0eb-126">A [ResourceResponse](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object&preserve-view=true) object</span></span> |

---

## <a name="update-cards"></a><span data-ttu-id="9b0eb-127">Atualizar cartões</span><span class="sxs-lookup"><span data-stu-id="9b0eb-127">Update cards</span></span>

<span data-ttu-id="9b0eb-128">Para atualizar o cartão existente na seleção de botão, você pode usar `ReplyToId` a atividade de entrada.</span><span class="sxs-lookup"><span data-stu-id="9b0eb-128">To update the existing card on button selection, you can use `ReplyToId` of incoming activity.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="9b0eb-129">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="9b0eb-129">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="9b0eb-130">Para atualizar o cartão existente em um clique de botão, passe um novo objeto com cartão atualizado e como ID de atividade para `Activity` `ReplyToId` o método da `UpdateActivityAsync` `TurnContext` classe.</span><span class="sxs-lookup"><span data-stu-id="9b0eb-130">To update existing card on a button click, pass a new `Activity` object with updated card and `ReplyToId` as activity ID to the `UpdateActivityAsync` method of the `TurnContext` class.</span></span> <span data-ttu-id="9b0eb-131">Consulte [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="9b0eb-131">See [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable&preserve-view=true).</span></span>
```csharp
var activity = MessageFactory.Attachment(card.ToAttachment());
activity.Id = turnContext.Activity.ReplyToId;
await turnContext.UpdateActivityAsync(activity, cancellationToken);
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="9b0eb-132">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="9b0eb-132">TypeScript/Node.js</span></span>](#tab/typescript)

<span data-ttu-id="9b0eb-133">Para atualizar o cartão existente em um clique de botão, passe um novo objeto com cartão atualizado e como ID de atividade para `Activity` `replyToId` o método do `updateActivity` `TurnContext` objeto.</span><span class="sxs-lookup"><span data-stu-id="9b0eb-133">To update existing card on a button click, pass a new `Activity` object with updated card and `replyToId` as activity ID to the `updateActivity` method of the `TurnContext` object.</span></span> <span data-ttu-id="9b0eb-134">Consulte [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="9b0eb-134">See [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--&preserve-view=true).</span></span>
```typescript
const message = MessageFactory.attachment(card);
message.id = context.activity.replyToId;
await context.updateActivity(message);
```

# <a name="python"></a>[<span data-ttu-id="9b0eb-135">Python</span><span class="sxs-lookup"><span data-stu-id="9b0eb-135">Python</span></span>](#tab/python)

<span data-ttu-id="9b0eb-136">Para atualizar o cartão existente em um clique de botão, passe um novo objeto com cartão atualizado e como ID de atividade para `Activity` `reply_to_id` o método da `update_activity` `TurnContext` classe.</span><span class="sxs-lookup"><span data-stu-id="9b0eb-136">To update existing card on a button click, pass a new `Activity` object with updated card and `reply_to_id` as activity ID to the `update_activity` method of the `TurnContext` class.</span></span> <span data-ttu-id="9b0eb-137">Consulte [TurnContextClass](/python/api/botbuilder-core/botbuilder.core.turncontext?view=botbuilder-py-latest).</span><span class="sxs-lookup"><span data-stu-id="9b0eb-137">See [TurnContextClass](/python/api/botbuilder-core/botbuilder.core.turncontext?view=botbuilder-py-latest).</span></span>

```python
updated_activity = MessageFactory.attachment(CardFactory.hero_card(card))
updated_activity.id = turn_context.activity.reply_to_id
await turn_context.update_activity(updated_activity)

```

## <a name="delete-messages"></a><span data-ttu-id="9b0eb-138">Excluir mensagens</span><span class="sxs-lookup"><span data-stu-id="9b0eb-138">Delete messages</span></span>

<span data-ttu-id="9b0eb-139">Na Estrutura de Bot, cada mensagem tem seu próprio identificador de atividade exclusivo.</span><span class="sxs-lookup"><span data-stu-id="9b0eb-139">In the Bot Framework, every message has its own unique activity identifier.</span></span>
<span data-ttu-id="9b0eb-140">As mensagens podem ser excluídas usando o método da Estrutura de `DeleteActivity` Bot, conforme mostrado aqui.</span><span class="sxs-lookup"><span data-stu-id="9b0eb-140">Messages can be deleted using the Bot Framework's `DeleteActivity` method as shown here.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="9b0eb-141">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="9b0eb-141">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="9b0eb-142">Para excluir essa mensagem, passe a ID dessa atividade para `DeleteActivityAsync` o método da `TurnContext` classe.</span><span class="sxs-lookup"><span data-stu-id="9b0eb-142">To delete that message, pass that activity's ID to the `DeleteActivityAsync` method of the `TurnContext` class.</span></span> <span data-ttu-id="9b0eb-143">Consulte [Método TurnContext.DeleteActivityAsync](/dotnet/api/microsoft.bot.builder.turncontext.deleteactivityasync?view=botbuilder-dotnet-stable&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="9b0eb-143">See [TurnContext.DeleteActivityAsync Method](/dotnet/api/microsoft.bot.builder.turncontext.deleteactivityasync?view=botbuilder-dotnet-stable&preserve-view=true).</span></span>

```csharp
foreach (var activityId in _list)
{
    await turnContext.DeleteActivityAsync(activityId, cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="9b0eb-144">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="9b0eb-144">TypeScript/Node.js</span></span>](#tab/typescript)

<span data-ttu-id="9b0eb-145">Para excluir essa mensagem, passe a ID dessa atividade para o `deleteActivity` método do `TurnContext` objeto.</span><span class="sxs-lookup"><span data-stu-id="9b0eb-145">To delete that message, pass that activity's ID to the `deleteActivity` method of the `TurnContext` object.</span></span> <span data-ttu-id="9b0eb-146">Consulte [deleteActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#deleteactivity-string---partial-conversationreference--&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="9b0eb-146">See [deleteActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#deleteactivity-string---partial-conversationreference--&preserve-view=true).</span></span>

```typescript
for (let i = 0; i < activityIds.length; i++) {
    await turnContext.deleteActivity(activityIds[i]);
}
```

# <a name="python"></a>[<span data-ttu-id="9b0eb-147">Python</span><span class="sxs-lookup"><span data-stu-id="9b0eb-147">Python</span></span>](#tab/python)

<span data-ttu-id="9b0eb-148">Para excluir essa mensagem, passe a ID dessa atividade para o `delete_activity` método do `TurnContext` objeto.</span><span class="sxs-lookup"><span data-stu-id="9b0eb-148">To delete that message, pass that activity's ID to the `delete_activity` method of the `TurnContext` object.</span></span> <span data-ttu-id="9b0eb-149">Consulte [activity-update-and-delete](https://github.com/microsoft/botbuilder-python/blob/c04ecacb22c1f4b43a671fe2f1e4782218391975/tests/teams/scenarios/activity-update-and-delete/bots/activity_update_and_delete_bot.py).</span><span class="sxs-lookup"><span data-stu-id="9b0eb-149">See [activity-update-and-delete](https://github.com/microsoft/botbuilder-python/blob/c04ecacb22c1f4b43a671fe2f1e4782218391975/tests/teams/scenarios/activity-update-and-delete/bots/activity_update_and_delete_bot.py).</span></span>

```python
for each activity_id in _list:
    await TurnContext.delete_activity(activity_id)
```

# <a name="rest-api"></a>[<span data-ttu-id="9b0eb-150">API REST</span><span class="sxs-lookup"><span data-stu-id="9b0eb-150">REST API</span></span>](#tab/rest)

 <span data-ttu-id="9b0eb-151">Para excluir uma atividade existente dentro de uma conversa, inclua `conversationId` o e no ponto de extremidade da `activityId` solicitação.</span><span class="sxs-lookup"><span data-stu-id="9b0eb-151">To delete an existing activity within a conversation, include the `conversationId` and `activityId` in the request endpoint.</span></span>

```http
DELETE /v3/conversations/{conversationId}/activities/{activityId}
```

| | |
|----|----|
| <span data-ttu-id="9b0eb-152">**Corpo da solicitação**</span><span class="sxs-lookup"><span data-stu-id="9b0eb-152">**Request body**</span></span> | <span data-ttu-id="9b0eb-153">n/d</span><span class="sxs-lookup"><span data-stu-id="9b0eb-153">n/a</span></span> |
| <span data-ttu-id="9b0eb-154">**Retorna**</span><span class="sxs-lookup"><span data-stu-id="9b0eb-154">**Returns**</span></span> | <span data-ttu-id="9b0eb-155">Um código de Status HTTP que indica o resultado da operação.</span><span class="sxs-lookup"><span data-stu-id="9b0eb-155">An HTTP Status code that indicates the outcome of the operation.</span></span> <span data-ttu-id="9b0eb-156">Nada é especificado no corpo da resposta.</span><span class="sxs-lookup"><span data-stu-id="9b0eb-156">Nothing is specified in the body of the response.</span></span> |

---

## <a name="code-samples"></a><span data-ttu-id="9b0eb-157">Exemplos de código</span><span class="sxs-lookup"><span data-stu-id="9b0eb-157">Code samples</span></span>

<span data-ttu-id="9b0eb-158">As noções básicas de conversa oficiais são as seguinte:</span><span class="sxs-lookup"><span data-stu-id="9b0eb-158">The official conversation basics are as follows:</span></span>

| <span data-ttu-id="9b0eb-159">Exemplo de nome</span><span class="sxs-lookup"><span data-stu-id="9b0eb-159">Sample Name</span></span>           | <span data-ttu-id="9b0eb-160">Descrição</span><span class="sxs-lookup"><span data-stu-id="9b0eb-160">Description</span></span>                                                                      | <span data-ttu-id="9b0eb-161">.NET</span><span class="sxs-lookup"><span data-stu-id="9b0eb-161">.NET</span></span>    | <span data-ttu-id="9b0eb-162">JavaScript</span><span class="sxs-lookup"><span data-stu-id="9b0eb-162">JavaScript</span></span>   | <span data-ttu-id="9b0eb-163">Python</span><span class="sxs-lookup"><span data-stu-id="9b0eb-163">Python</span></span>  |
|:----------------------|:---------------------------------------------------------------------------------|:--------|:-------------|:--------|
|<span data-ttu-id="9b0eb-164">Noções básicas de conversa do Teams</span><span class="sxs-lookup"><span data-stu-id="9b0eb-164">Teams Conversation Basics</span></span>  | <span data-ttu-id="9b0eb-165">Demonstra noções básicas de conversas no Teams, incluindo atualização de mensagens e exclusão.</span><span class="sxs-lookup"><span data-stu-id="9b0eb-165">Demonstrates basics of conversations in Teams, including message update and delete.</span></span>|[<span data-ttu-id="9b0eb-166">.NET &nbsp; Core</span><span class="sxs-lookup"><span data-stu-id="9b0eb-166">.NET&nbsp;Core</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot)|[<span data-ttu-id="9b0eb-167">JavaScript</span><span class="sxs-lookup"><span data-stu-id="9b0eb-167">JavaScript</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/57.teams-conversation-bot) | [<span data-ttu-id="9b0eb-168">Python</span><span class="sxs-lookup"><span data-stu-id="9b0eb-168">Python</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot)|
