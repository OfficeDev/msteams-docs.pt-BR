---
title: Atualizar e excluir mensagens enviadas do bot
author: WashingtonKayaker
description: Como atualizar e excluir mensagens enviadas do bot do Microsoft Teams
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: a2836d59c22b9784f1f1a0c84306072bb6a97d3e
ms.sourcegitcommit: dd2220f691029d043aaddfc7c229e332735acb1d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2021
ms.locfileid: "51995999"
---
# <a name="update-and-delete-messages-sent-from-your-bot"></a>Atualizar e excluir mensagens enviadas do bot

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Seu bot pode atualizar dinamicamente as mensagens depois de enviá-las em vez de tê-las como instantâneos estáticos de dados. As mensagens também podem ser excluídas usando o método da Estrutura de `DeleteActivity` Bot.

## <a name="update-messages"></a>Atualizar mensagens

Você pode usar atualizações dinâmicas de mensagens para cenários, como atualizações de sondagem, modificação de ações disponíveis após uma pressionamento de botão ou qualquer outra alteração de estado assíncrona.

Não é necessário que a nova mensagem corresponder ao tipo original. Por exemplo, se a mensagem original contiver um anexo, a nova mensagem poderá ser uma mensagem de texto simples.

# <a name="c"></a>[C#](#tab/dotnet)

Para atualizar uma mensagem existente, passe um novo objeto com a ID de atividade existente `Activity` para o método da `UpdateActivityAsync` `TurnContext` classe. Para obter mais informações, consulte [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable&preserve-view=true).

```csharp
var newActivity = MessageFactory.Text("The new text for the activity");
newActivity.Id = activityId;
await turnContext.UpdateActivityAsync(newActivity, cancellationToken);
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

Para atualizar uma mensagem existente, passe um novo objeto com a ID de atividade existente `Activity` para o método do `updateActivity` `TurnContext` objeto. Para obter mais informações, consulte [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--&preserve-view=true).

```typescript
const newActivity = MessageFactory.text('The new text for the activity');
newActivity.id = activityId;
await turnContext.updateActivity(newActivity);
```

# <a name="python"></a>[Python](#tab/python)

Para atualizar uma mensagem existente, passe um novo objeto com a ID de atividade existente `Activity` para o método da `update_activity` `TurnContext` classe. Consulte [TurnContextClass](/python/api/botbuilder-core/botbuilder.core.turncontext?view=botbuilder-py-latest&preserve-view=true).

```python
new_activity = MessageFactory.text("The new text for the activity")
new_activity.id = activity_id
update_result = await context.update_activity(new_activity)
```

# <a name="rest-api"></a>[API REST](#tab/rest)

> [!NOTE]

> Você pode desenvolver aplicativos do Teams em qualquer tecnologia de programação da Web e chamar diretamente as APIs REST do serviço [do Conector de Bot.](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true) Para fazer isso, você precisa implementar [procedimentos](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0&preserve-view=true) de segurança de autenticação com suas solicitações de API.

Para atualizar uma atividade existente dentro de uma conversa, inclua `conversationId` o e no ponto de extremidade da `activityId` solicitação. Para concluir esse cenário, você deve armazenar em cache a ID de atividade retornada pela chamada de postagem original.

```http
PUT /v3/conversations/{conversationId}/activities/{activityId}
```

| **Solicitação e Responce** | **Descrição** |
|----|----|
| Um [objeto activity](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object&preserve-view=true) | Um [objeto ResourceResponse](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object&preserve-view=true) |

---
* * *

Agora que você atualizou as mensagens, atualize o cartão existente na seleção de botão para atividades de entrada.

## <a name="update-cards"></a>Atualizar cartões

Para atualizar o cartão existente na seleção de botão, você pode usar `ReplyToId` a atividade de entrada.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

Para atualizar o cartão existente em uma seleção de botão, passe um novo objeto com cartão atualizado e como ID de atividade para `Activity` `ReplyToId` o método da `UpdateActivityAsync` `TurnContext` classe. Consulte [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable&preserve-view=true).

```csharp
var activity = MessageFactory.Attachment(card.ToAttachment());
activity.Id = turnContext.Activity.ReplyToId;
await turnContext.UpdateActivityAsync(activity, cancellationToken);
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

Para atualizar o cartão existente em uma seleção de botão, passe um novo objeto com cartão atualizado e como ID de atividade para `Activity` `replyToId` o método do `updateActivity` `TurnContext` objeto. Consulte [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--&preserve-view=true).

```typescript
const message = MessageFactory.attachment(card);
message.id = context.activity.replyToId;
await context.updateActivity(message);
```

# <a name="python"></a>[Python](#tab/python)

Para atualizar o cartão existente em um clique de botão, passe um novo objeto com cartão atualizado e como ID de atividade para `Activity` `reply_to_id` o método da `update_activity` `TurnContext` classe. Consulte [TurnContextClass](/python/api/botbuilder-core/botbuilder.core.turncontext?view=botbuilder-py-latest&preserve-view=true).

```python
updated_activity = MessageFactory.attachment(CardFactory.hero_card(card))
updated_activity.id = turn_context.activity.reply_to_id
await turn_context.update_activity(updated_activity)
```

# <a name="rest-api"></a>[API REST](#tab/rest)

> [!NOTE]
> Você pode desenvolver aplicativos do Teams em qualquer tecnologia de programação da Web e chamar diretamente as APIs REST do serviço [de conector de bot.](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true) Para fazer isso, você deve [implementar](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0&preserve-view=true) procedimentos de segurança de autenticação com suas solicitações de API.

Para atualizar uma atividade existente dentro de uma conversa, inclua `conversationId` o e no ponto de extremidade da `activityId` solicitação. Para concluir esse cenário, você deve armazenar em cache a ID de atividade retornada pela chamada de postagem original.

```http
PUT /v3/conversations/{conversationId}/activities/{activityId}
```

|Solicitação |Resposta |
|----|----|
| Um [objeto activity.](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object&preserve-view=true) | Um [objeto ResourceResponse.](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object&preserve-view=true) |

* * *

Agora que você atualizou cartões, você pode excluir mensagens usando a Estrutura de Bot.

## <a name="delete-messages"></a>Excluir mensagens

Na Estrutura de Bot, cada mensagem tem seu identificador de atividade exclusivo. As mensagens podem ser excluídas usando o método da Estrutura de `DeleteActivity` Bot.

# <a name="c"></a>[C#](#tab/dotnet)

Para excluir uma mensagem, passe a ID dessa atividade para o `DeleteActivityAsync` método da `TurnContext` classe. Para obter mais informações, consulte [TurnContext.DeleteActivityAsync Method](/dotnet/api/microsoft.bot.builder.turncontext.deleteactivityasync?view=botbuilder-dotnet-stable&preserve-view=true).

```csharp
foreach (var activityId in _list)
{
    await turnContext.DeleteActivityAsync(activityId, cancellationToken);
}
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

Para excluir uma mensagem, passe a ID dessa atividade para o `deleteActivity` método do `TurnContext` objeto. Para obter mais informações, consulte [deleteActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#deleteactivity-string---partial-conversationreference--&preserve-view=true).

```typescript
for (let i = 0; i < activityIds.length; i++) {
    await turnContext.deleteActivity(activityIds[i]);
}
```

# <a name="python"></a>[Python](#tab/python)

Para excluir essa mensagem, passe a ID dessa atividade para o `delete_activity` método do `TurnContext` objeto. Para obter mais informações, [consulte activity-update-and-delete](https://github.com/microsoft/botbuilder-python/blob/c04ecacb22c1f4b43a671fe2f1e4782218391975/tests/teams/scenarios/activity-update-and-delete/bots/activity_update_and_delete_bot.py).

```python
for each activity_id in _list:
    await TurnContext.delete_activity(activity_id)
```

# <a name="rest-api"></a>[API REST](#tab/rest)

Para excluir uma atividade existente dentro de uma conversa, inclua `conversationId` o e no ponto de extremidade da `activityId` solicitação.

```http
DELETE /v3/conversations/{conversationId}/activities/{activityId}
```

| **Solicitação e Responce** | **Descrição** |
|----|----|
| N/D | Um código de status HTTP que indica o resultado da operação. Nada é especificado no corpo da resposta. |

---

## <a name="code-sample"></a>Exemplo de código

O exemplo de código a seguir demonstra noções básicas de conversas:

| **Exemplo de nome** | **Descrição** | **.NET** | **Node.js** | **Python** |
|----------------------|-----------------|--------|-------------|--------|
| Noções básicas de conversa do Teams  | Demonstra noções básicas de conversas no Teams, incluindo atualização de mensagens e exclusão. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/57.teams-conversation-bot) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot) |

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Obter contexto do Teams](~/bots/how-to/get-teams-context.md)
