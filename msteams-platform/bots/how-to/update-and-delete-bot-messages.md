---
title: Atualizar e excluir mensagens enviadas do bot
author: WashingtonKayaker
description: Como atualizar e excluir mensagens enviadas de seu Microsoft Teams bot
ms.topic: overview
localization_priority: Normal
ms.author: anclear
ms.openlocfilehash: 90dc50fd2ec153813457f199ac029e17a0157502
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101531"
---
# <a name="update-and-delete-messages-sent-from-your-bot"></a><span data-ttu-id="c0dd4-103">Atualizar e excluir mensagens enviadas do bot</span><span class="sxs-lookup"><span data-stu-id="c0dd4-103">Update and delete messages sent from your bot</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="c0dd4-104">Seu bot pode atualizar dinamicamente as mensagens depois de enviá-las em vez de tê-las como instantâneos estáticos de dados.</span><span class="sxs-lookup"><span data-stu-id="c0dd4-104">Your bot can dynamically update messages after sending them instead of having them as static snapshots of data.</span></span> <span data-ttu-id="c0dd4-105">As mensagens também podem ser excluídas usando o método da Estrutura de `DeleteActivity` Bot.</span><span class="sxs-lookup"><span data-stu-id="c0dd4-105">Messages can also be deleted using the Bot Framework's `DeleteActivity` method.</span></span>

## <a name="update-messages"></a><span data-ttu-id="c0dd4-106">Atualizar mensagens</span><span class="sxs-lookup"><span data-stu-id="c0dd4-106">Update messages</span></span>

<span data-ttu-id="c0dd4-107">Você pode usar atualizações dinâmicas de mensagens para cenários, como atualizações de sondagem, modificação de ações disponíveis após uma pressionamento de botão ou qualquer outra alteração de estado assíncrona.</span><span class="sxs-lookup"><span data-stu-id="c0dd4-107">You can use dynamic message updates for scenarios, such as poll updates, modifying available actions after a button press, or any other asynchronous state change.</span></span>

<span data-ttu-id="c0dd4-108">Não é necessário que a nova mensagem corresponder ao tipo original.</span><span class="sxs-lookup"><span data-stu-id="c0dd4-108">It is not necessary for the new message to match the original in type.</span></span> <span data-ttu-id="c0dd4-109">Por exemplo, se a mensagem original contiver um anexo, a nova mensagem poderá ser uma mensagem de texto simples.</span><span class="sxs-lookup"><span data-stu-id="c0dd4-109">For example, if the original message contains an attachment, the new message can be a simple text message.</span></span>

# <a name="c"></a>[<span data-ttu-id="c0dd4-110">C#</span><span class="sxs-lookup"><span data-stu-id="c0dd4-110">C#</span></span>](#tab/dotnet)

<span data-ttu-id="c0dd4-111">Para atualizar uma mensagem existente, passe um novo objeto com a ID de atividade existente `Activity` para o método da `UpdateActivityAsync` `TurnContext` classe.</span><span class="sxs-lookup"><span data-stu-id="c0dd4-111">To update an existing message, pass a new `Activity` object with the existing activity ID to the `UpdateActivityAsync` method of the `TurnContext` class.</span></span> <span data-ttu-id="c0dd4-112">Para obter mais informações, consulte [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="c0dd4-112">For more information, see [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable&preserve-view=true).</span></span>

```csharp
var newActivity = MessageFactory.Text("The new text for the activity");
newActivity.Id = activityId;
await turnContext.UpdateActivityAsync(newActivity, cancellationToken);
```

# <a name="typescript"></a>[<span data-ttu-id="c0dd4-113">TypeScript</span><span class="sxs-lookup"><span data-stu-id="c0dd4-113">TypeScript</span></span>](#tab/typescript)

<span data-ttu-id="c0dd4-114">Para atualizar uma mensagem existente, passe um novo objeto com a ID de atividade existente `Activity` para o método do `updateActivity` `TurnContext` objeto.</span><span class="sxs-lookup"><span data-stu-id="c0dd4-114">To update an existing message, pass a new `Activity` object with the existing activity ID to the `updateActivity` method of the `TurnContext` object.</span></span> <span data-ttu-id="c0dd4-115">Para obter mais informações, consulte [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="c0dd4-115">For more information, see [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--&preserve-view=true).</span></span>

```typescript
const newActivity = MessageFactory.text('The new text for the activity');
newActivity.id = activityId;
await turnContext.updateActivity(newActivity);
```

# <a name="python"></a>[<span data-ttu-id="c0dd4-116">Python</span><span class="sxs-lookup"><span data-stu-id="c0dd4-116">Python</span></span>](#tab/python)

<span data-ttu-id="c0dd4-117">Para atualizar uma mensagem existente, passe um novo objeto com a ID de atividade existente `Activity` para o método da `update_activity` `TurnContext` classe.</span><span class="sxs-lookup"><span data-stu-id="c0dd4-117">To update an existing message, pass a new `Activity` object with the existing activity ID to the `update_activity` method of the `TurnContext` class.</span></span> <span data-ttu-id="c0dd4-118">Consulte [TurnContextClass](/python/api/botbuilder-core/botbuilder.core.turncontext?view=botbuilder-py-latest&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="c0dd4-118">See [TurnContextClass](/python/api/botbuilder-core/botbuilder.core.turncontext?view=botbuilder-py-latest&preserve-view=true).</span></span>

```python
new_activity = MessageFactory.text("The new text for the activity")
new_activity.id = activity_id
update_result = await context.update_activity(new_activity)
```

# <a name="rest-api"></a>[<span data-ttu-id="c0dd4-119">API REST</span><span class="sxs-lookup"><span data-stu-id="c0dd4-119">REST API</span></span>](#tab/rest)

> [!NOTE]

> <span data-ttu-id="c0dd4-120">Você pode desenvolver Teams aplicativos em qualquer tecnologia de programação da Web e chamar diretamente as APIs REST do serviço [do Conector de Bot.](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="c0dd4-120">You can develop Teams apps in any web-programming technology and directly call the [Bot Connector service REST APIs](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span> <span data-ttu-id="c0dd4-121">Para fazer isso, você precisa implementar [procedimentos](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0&preserve-view=true) de segurança de autenticação com suas solicitações de API.</span><span class="sxs-lookup"><span data-stu-id="c0dd4-121">To do so, you need to implement [Authentication](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0&preserve-view=true) security procedures with your API requests.</span></span>

<span data-ttu-id="c0dd4-122">Para atualizar uma atividade existente dentro de uma conversa, inclua `conversationId` o e no ponto de extremidade da `activityId` solicitação.</span><span class="sxs-lookup"><span data-stu-id="c0dd4-122">To update an existing activity within a conversation, include the `conversationId` and `activityId` in the request endpoint.</span></span> <span data-ttu-id="c0dd4-123">Para concluir esse cenário, você deve armazenar em cache a ID de atividade retornada pela chamada de postagem original.</span><span class="sxs-lookup"><span data-stu-id="c0dd4-123">To complete this scenario, you must cache the activity ID returned by the original post call.</span></span>

```http
PUT /v3/conversations/{conversationId}/activities/{activityId}
```

|<span data-ttu-id="c0dd4-124">Solicitação</span><span class="sxs-lookup"><span data-stu-id="c0dd4-124">Request</span></span> |<span data-ttu-id="c0dd4-125">Resposta</span><span class="sxs-lookup"><span data-stu-id="c0dd4-125">Response</span></span> |
|----|----|
| <span data-ttu-id="c0dd4-126">Um [objeto Activity.](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="c0dd4-126">An [Activity](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object&preserve-view=true) object.</span></span> | <span data-ttu-id="c0dd4-127">Um [objeto ResourceResponse.](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="c0dd4-127">A [ResourceResponse](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object&preserve-view=true) object.</span></span> |

---
* * *

<span data-ttu-id="c0dd4-128">Agora que você atualizou as mensagens, atualize o cartão existente na seleção de botão para atividades de entrada.</span><span class="sxs-lookup"><span data-stu-id="c0dd4-128">Now that you have updated messages, update the existing card on button selection for incoming activities.</span></span>

## <a name="update-cards"></a><span data-ttu-id="c0dd4-129">Atualizar cartões</span><span class="sxs-lookup"><span data-stu-id="c0dd4-129">Update cards</span></span>

<span data-ttu-id="c0dd4-130">Para atualizar o cartão existente na seleção de botão, você pode usar `ReplyToId` a atividade de entrada.</span><span class="sxs-lookup"><span data-stu-id="c0dd4-130">To update the existing card on button selection, you can use `ReplyToId` of incoming activity.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="c0dd4-131">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="c0dd4-131">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="c0dd4-132">Para atualizar o cartão existente em uma seleção de botão, passe um novo objeto com cartão atualizado e como ID de atividade para `Activity` `ReplyToId` o método da `UpdateActivityAsync` `TurnContext` classe.</span><span class="sxs-lookup"><span data-stu-id="c0dd4-132">To update existing card on a button selection, pass a new `Activity` object with updated card and `ReplyToId` as activity ID to the `UpdateActivityAsync` method of the `TurnContext` class.</span></span> <span data-ttu-id="c0dd4-133">Consulte [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="c0dd4-133">See [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable&preserve-view=true).</span></span>

```csharp
var activity = MessageFactory.Attachment(card.ToAttachment());
activity.Id = turnContext.Activity.ReplyToId;
await turnContext.UpdateActivityAsync(activity, cancellationToken);
```

# <a name="typescript"></a>[<span data-ttu-id="c0dd4-134">TypeScript</span><span class="sxs-lookup"><span data-stu-id="c0dd4-134">TypeScript</span></span>](#tab/typescript)

<span data-ttu-id="c0dd4-135">Para atualizar o cartão existente em uma seleção de botão, passe um novo objeto com cartão atualizado e como ID de atividade para `Activity` `replyToId` o método do `updateActivity` `TurnContext` objeto.</span><span class="sxs-lookup"><span data-stu-id="c0dd4-135">To update existing card on a button selection, pass a new `Activity` object with updated card and `replyToId` as activity ID to the `updateActivity` method of the `TurnContext` object.</span></span> <span data-ttu-id="c0dd4-136">Consulte [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="c0dd4-136">See [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--&preserve-view=true).</span></span>

```typescript
const message = MessageFactory.attachment(card);
message.id = context.activity.replyToId;
await context.updateActivity(message);
```

# <a name="python"></a>[<span data-ttu-id="c0dd4-137">Python</span><span class="sxs-lookup"><span data-stu-id="c0dd4-137">Python</span></span>](#tab/python)

<span data-ttu-id="c0dd4-138">Para atualizar o cartão existente em um clique de botão, passe um novo objeto com cartão atualizado e como ID de atividade para `Activity` `reply_to_id` o método da `update_activity` `TurnContext` classe.</span><span class="sxs-lookup"><span data-stu-id="c0dd4-138">To update existing card on a button click, pass a new `Activity` object with updated card and `reply_to_id` as activity ID to the `update_activity` method of the `TurnContext` class.</span></span> <span data-ttu-id="c0dd4-139">Consulte [TurnContextClass](/python/api/botbuilder-core/botbuilder.core.turncontext?view=botbuilder-py-latest&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="c0dd4-139">See [TurnContextClass](/python/api/botbuilder-core/botbuilder.core.turncontext?view=botbuilder-py-latest&preserve-view=true).</span></span>

```python
updated_activity = MessageFactory.attachment(CardFactory.hero_card(card))
updated_activity.id = turn_context.activity.reply_to_id
await turn_context.update_activity(updated_activity)
```

# <a name="rest-api"></a>[<span data-ttu-id="c0dd4-140">API REST</span><span class="sxs-lookup"><span data-stu-id="c0dd4-140">REST API</span></span>](#tab/rest)

> [!NOTE]
> <span data-ttu-id="c0dd4-141">Você pode desenvolver Teams aplicativos em qualquer tecnologia de programação da Web e chamar diretamente as APIs REST do serviço [de conector de bot.](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="c0dd4-141">You can develop Teams apps in any web programming technology and directly call the [bot connector service REST APIs](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span> <span data-ttu-id="c0dd4-142">Para fazer isso, você deve [implementar](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0&preserve-view=true) procedimentos de segurança de autenticação com suas solicitações de API.</span><span class="sxs-lookup"><span data-stu-id="c0dd4-142">To do this, you must implement [authentication](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0&preserve-view=true) security procedures with your API requests.</span></span>

<span data-ttu-id="c0dd4-143">Para atualizar uma atividade existente dentro de uma conversa, inclua `conversationId` o e no ponto de extremidade da `activityId` solicitação.</span><span class="sxs-lookup"><span data-stu-id="c0dd4-143">To update an existing activity within a conversation, include the `conversationId` and `activityId` in the request endpoint.</span></span> <span data-ttu-id="c0dd4-144">Para concluir esse cenário, você deve armazenar em cache a ID de atividade retornada pela chamada de postagem original.</span><span class="sxs-lookup"><span data-stu-id="c0dd4-144">To complete this scenario, you must cache the activity ID returned by the original post call.</span></span>

```http
PUT /v3/conversations/{conversationId}/activities/{activityId}
```

|<span data-ttu-id="c0dd4-145">Solicitação</span><span class="sxs-lookup"><span data-stu-id="c0dd4-145">Request</span></span> |<span data-ttu-id="c0dd4-146">Resposta</span><span class="sxs-lookup"><span data-stu-id="c0dd4-146">Response</span></span> |
|----|----|
| <span data-ttu-id="c0dd4-147">Um [objeto activity.](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="c0dd4-147">An [activity](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object&preserve-view=true) object.</span></span> | <span data-ttu-id="c0dd4-148">Um [objeto ResourceResponse.](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="c0dd4-148">A [ResourceResponse](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object&preserve-view=true) object.</span></span> |

* * *

<span data-ttu-id="c0dd4-149">Agora que você atualizou cartões, você pode excluir mensagens usando a Estrutura de Bot.</span><span class="sxs-lookup"><span data-stu-id="c0dd4-149">Now that you have updated cards, you can delete messages using the Bot Framework.</span></span>

## <a name="delete-messages"></a><span data-ttu-id="c0dd4-150">Excluir mensagens</span><span class="sxs-lookup"><span data-stu-id="c0dd4-150">Delete messages</span></span>

<span data-ttu-id="c0dd4-151">Na Estrutura de Bot, cada mensagem tem seu identificador de atividade exclusivo.</span><span class="sxs-lookup"><span data-stu-id="c0dd4-151">In the Bot Framework, every message has its unique activity identifier.</span></span> <span data-ttu-id="c0dd4-152">As mensagens podem ser excluídas usando o método da Estrutura de `DeleteActivity` Bot.</span><span class="sxs-lookup"><span data-stu-id="c0dd4-152">Messages can be deleted using the Bot Framework's `DeleteActivity` method.</span></span>

# <a name="c"></a>[<span data-ttu-id="c0dd4-153">C#</span><span class="sxs-lookup"><span data-stu-id="c0dd4-153">C#</span></span>](#tab/dotnet)

<span data-ttu-id="c0dd4-154">Para excluir uma mensagem, passe a ID dessa atividade para o `DeleteActivityAsync` método da `TurnContext` classe.</span><span class="sxs-lookup"><span data-stu-id="c0dd4-154">To delete a message, pass that activity's ID to the `DeleteActivityAsync` method of the `TurnContext` class.</span></span> <span data-ttu-id="c0dd4-155">Para obter mais informações, consulte [TurnContext.DeleteActivityAsync Method](/dotnet/api/microsoft.bot.builder.turncontext.deleteactivityasync?view=botbuilder-dotnet-stable&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="c0dd4-155">For more information, see [TurnContext.DeleteActivityAsync Method](/dotnet/api/microsoft.bot.builder.turncontext.deleteactivityasync?view=botbuilder-dotnet-stable&preserve-view=true).</span></span>

```csharp
foreach (var activityId in _list)
{
    await turnContext.DeleteActivityAsync(activityId, cancellationToken);
}
```

# <a name="typescript"></a>[<span data-ttu-id="c0dd4-156">TypeScript</span><span class="sxs-lookup"><span data-stu-id="c0dd4-156">TypeScript</span></span>](#tab/typescript)

<span data-ttu-id="c0dd4-157">Para excluir uma mensagem, passe a ID dessa atividade para o `deleteActivity` método do `TurnContext` objeto.</span><span class="sxs-lookup"><span data-stu-id="c0dd4-157">To delete a message, pass that activity's ID to the `deleteActivity` method of the `TurnContext` object.</span></span> <span data-ttu-id="c0dd4-158">Para obter mais informações, consulte [deleteActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#deleteactivity-string---partial-conversationreference--&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="c0dd4-158">For more information, see [deleteActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#deleteactivity-string---partial-conversationreference--&preserve-view=true).</span></span>

```typescript
for (let i = 0; i < activityIds.length; i++) {
    await turnContext.deleteActivity(activityIds[i]);
}
```

# <a name="python"></a>[<span data-ttu-id="c0dd4-159">Python</span><span class="sxs-lookup"><span data-stu-id="c0dd4-159">Python</span></span>](#tab/python)

<span data-ttu-id="c0dd4-160">Para excluir essa mensagem, passe a ID dessa atividade para o `delete_activity` método do `TurnContext` objeto.</span><span class="sxs-lookup"><span data-stu-id="c0dd4-160">To delete that message, pass that activity's ID to the `delete_activity` method of the `TurnContext` object.</span></span> <span data-ttu-id="c0dd4-161">Para obter mais informações, [consulte activity-update-and-delete](https://github.com/microsoft/botbuilder-python/blob/c04ecacb22c1f4b43a671fe2f1e4782218391975/tests/teams/scenarios/activity-update-and-delete/bots/activity_update_and_delete_bot.py).</span><span class="sxs-lookup"><span data-stu-id="c0dd4-161">For more information, see [activity-update-and-delete](https://github.com/microsoft/botbuilder-python/blob/c04ecacb22c1f4b43a671fe2f1e4782218391975/tests/teams/scenarios/activity-update-and-delete/bots/activity_update_and_delete_bot.py).</span></span>

```python
for each activity_id in _list:
    await TurnContext.delete_activity(activity_id)
```

# <a name="rest-api"></a>[<span data-ttu-id="c0dd4-162">API REST</span><span class="sxs-lookup"><span data-stu-id="c0dd4-162">REST API</span></span>](#tab/rest)

<span data-ttu-id="c0dd4-163">Para excluir uma atividade existente dentro de uma conversa, inclua `conversationId` o e no ponto de extremidade da `activityId` solicitação.</span><span class="sxs-lookup"><span data-stu-id="c0dd4-163">To delete an existing activity within a conversation, include the `conversationId` and `activityId` in the request endpoint.</span></span>

```http
DELETE /v3/conversations/{conversationId}/activities/{activityId}
```

| <span data-ttu-id="c0dd4-164">**Solicitação e resposta**</span><span class="sxs-lookup"><span data-stu-id="c0dd4-164">**Request and response**</span></span> | <span data-ttu-id="c0dd4-165">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="c0dd4-165">**Description**</span></span> |
|----|----|
| <span data-ttu-id="c0dd4-166">N/A</span><span class="sxs-lookup"><span data-stu-id="c0dd4-166">N/A</span></span> | <span data-ttu-id="c0dd4-167">Um código de status HTTP que indica o resultado da operação.</span><span class="sxs-lookup"><span data-stu-id="c0dd4-167">An HTTP status code indicating the outcome of the operation.</span></span> <span data-ttu-id="c0dd4-168">Nada é especificado no corpo da resposta.</span><span class="sxs-lookup"><span data-stu-id="c0dd4-168">Nothing is specified in the body of the response.</span></span> |

---

## <a name="code-sample"></a><span data-ttu-id="c0dd4-169">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="c0dd4-169">Code sample</span></span>

<span data-ttu-id="c0dd4-170">O exemplo de código a seguir demonstra noções básicas de conversas:</span><span class="sxs-lookup"><span data-stu-id="c0dd4-170">The following code sample demonstrates basics of conversations:</span></span>

| <span data-ttu-id="c0dd4-171">**Exemplo de nome**</span><span class="sxs-lookup"><span data-stu-id="c0dd4-171">**Sample name**</span></span> | <span data-ttu-id="c0dd4-172">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="c0dd4-172">**Description**</span></span> | <span data-ttu-id="c0dd4-173">**.NET**</span><span class="sxs-lookup"><span data-stu-id="c0dd4-173">**.NET**</span></span> | <span data-ttu-id="c0dd4-174">**Node.js**</span><span class="sxs-lookup"><span data-stu-id="c0dd4-174">**Node.js**</span></span> | <span data-ttu-id="c0dd4-175">**Python**</span><span class="sxs-lookup"><span data-stu-id="c0dd4-175">**Python**</span></span> |
|----------------------|-----------------|--------|-------------|--------|
| <span data-ttu-id="c0dd4-176">Teams Noções básicas de conversa</span><span class="sxs-lookup"><span data-stu-id="c0dd4-176">Teams Conversation Basics</span></span>  | <span data-ttu-id="c0dd4-177">Demonstra noções básicas de conversas no Teams incluindo a atualização e exclusão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="c0dd4-177">Demonstrates basics of conversations in Teams including message update and delete.</span></span> | [<span data-ttu-id="c0dd4-178">View</span><span class="sxs-lookup"><span data-stu-id="c0dd4-178">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot) | [<span data-ttu-id="c0dd4-179">View</span><span class="sxs-lookup"><span data-stu-id="c0dd4-179">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/57.teams-conversation-bot) | [<span data-ttu-id="c0dd4-180">View</span><span class="sxs-lookup"><span data-stu-id="c0dd4-180">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot) |

## <a name="next-step"></a><span data-ttu-id="c0dd4-181">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="c0dd4-181">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c0dd4-182">Obter Teams contexto</span><span class="sxs-lookup"><span data-stu-id="c0dd4-182">Get Teams context</span></span>](~/bots/how-to/get-teams-context.md)
