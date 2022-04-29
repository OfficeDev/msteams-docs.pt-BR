---
title: Atualizar e excluir mensagens enviadas do bot
author: WashingtonKayaker
description: Saiba como atualizar e excluir mensagens enviadas do bot do Microsoft Teams em ambientes diferentes e com APIs REST usando exemplos de código.
ms.topic: overview
ms.localizationpriority: high
ms.author: anclear
ms.openlocfilehash: 76befe46bab8d6cc0aa3d5c0c1e2c8c0f15bf579
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111406"
---
# <a name="update-and-delete-messages-sent-from-your-bot"></a>Atualizar e excluir mensagens enviadas do bot

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Seu bot pode atualizar mensagens dinamicamente depois de enviá-las em vez de enviá-las como instantâneos estáticos de dados. As mensagens também podem ser excluídas usando o método `DeleteActivity` do Bot Framework.

## <a name="update-messages"></a>Atualizar mensagens

Você pode usar atualizações de mensagens dinâmicas para cenários, como atualizações de votação, modificação de ações disponíveis após um pressionamento de botão ou qualquer outra alteração de estado assíncrona.

Não é necessário que a nova mensagem corresponda ao tipo original. Por exemplo, se a mensagem original contiver um anexo, a nova mensagem poderá ser uma mensagem de texto simples.

# <a name="c"></a>[C#](#tab/dotnet)

Para atualizar uma mensagem existente, passe um novo objeto `Activity` com a ID de atividade existente para o método `UpdateActivityAsync` da classe `TurnContext`. Para obter mais informações, consulte [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable&preserve-view=true).

```csharp
var newActivity = MessageFactory.Text("The new text for the activity");
newActivity.Id = activityId;
await turnContext.UpdateActivityAsync(newActivity, cancellationToken);
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

Para atualizar uma mensagem existente, passe um novo objeto `Activity` com a ID de atividade existente para o método `updateActivity` do `TurnContext` objeto. Para obter mais informações, consulte [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--&preserve-view=true).

```typescript
const newActivity = MessageFactory.text('The new text for the activity');
newActivity.id = activityId;
await turnContext.updateActivity(newActivity);
```

# <a name="python"></a>[Python](#tab/python)

Para atualizar uma mensagem existente, passe um novo objeto `Activity` com a ID de atividade existente para o método `update_activity` da classe `TurnContext`. Consulte [TurnContextClass](/python/api/botbuilder-core/botbuilder.core.turncontext?view=botbuilder-py-latest&preserve-view=true).

```python
new_activity = MessageFactory.text("The new text for the activity")
new_activity.id = activity_id
update_result = await context.update_activity(new_activity)
```

# <a name="rest-api"></a>[API REST](#tab/rest)

> [!NOTE]
> Você pode desenvolver aplicativos do Teams em qualquer tecnologia de programação da Web e chamar diretamente as [APIs REST do serviço Bot Connector](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true). Para fazer isso, você precisa implementar a [Autenticação](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0&preserve-view=true) de segurança com suas solicitações de API.

Para atualizar uma atividade existente em uma conversa, inclua o `conversationId` e `activityId` no ponto de extremidade de solicitação. Para concluir esse cenário, você deve armazenar em cache a ID da atividade retornada pela pós-chamada original.

```http
PUT /v3/conversations/{conversationId}/activities/{activityId}
```

|Solicitação |Resposta |
|----|----|
| Um objeto de [Atividade](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object&preserve-view=true). | Um objeto [ResourceResponse](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object&preserve-view=true). |

---
---

Agora que você atualizou as mensagens, atualize o cartão existente na seleção de botão para atividades de entrada.

## <a name="update-cards"></a>Atualizar cartões

Para atualizar o cartão existente na seleção de botão, você pode usar `ReplyToId` atividade de entrada.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

Para atualizar o cartão existente em uma seleção de botão, passe um novo objeto `Activity` com cartão atualizado e `ReplyToId` como ID de atividade para o método `UpdateActivityAsync` da classe `TurnContext`. Consulte [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable&preserve-view=true).

```csharp
var activity = MessageFactory.Attachment(card.ToAttachment());
activity.Id = turnContext.Activity.ReplyToId;
await turnContext.UpdateActivityAsync(activity, cancellationToken);
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

Para atualizar o cartão existente em uma seleção de botão, passe um novo objeto `Activity` com cartão atualizado e `replyToId` como ID de atividade para o método `updateActivity` do objeto `TurnContext`. Consulte [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--&preserve-view=true).

```typescript
const message = MessageFactory.attachment(card);
message.id = context.activity.replyToId;
await context.updateActivity(message);
```

# <a name="python"></a>[Python](#tab/python)

Para atualizar o cartão existente com um clique de botão, passe um novo objeto `Activity` com o cartão atualizado e o `reply_to_id` como ID de atividade para o método `update_activity` da classe `TurnContext`. Consulte [TurnContextClass](/python/api/botbuilder-core/botbuilder.core.turncontext?view=botbuilder-py-latest&preserve-view=true).

```python
updated_activity = MessageFactory.attachment(CardFactory.hero_card(card))
updated_activity.id = turn_context.activity.reply_to_id
await turn_context.update_activity(updated_activity)
```

# <a name="rest-api"></a>[API REST](#tab/rest)

> [!NOTE]
> Você pode desenvolver aplicativos do Teams em qualquer tecnologia de programação da Web e chamar diretamente as [APIs REST de serviço de conector de bot](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true). Para fazer isso, você deve implementar a [autenticação](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0&preserve-view=true) de segurança com suas solicitações de API.

Para atualizar uma atividade existente em uma conversa, inclua o `conversationId` e `activityId` no ponto de extremidade de solicitação. Para concluir esse cenário, você deve armazenar em cache a ID da atividade retornada pela pós-chamada original.

```http
PUT /v3/conversations/{conversationId}/activities/{activityId}
```

|Solicitação |Resposta |
|----|----|
| Um objeto de [atividade](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object&preserve-view=true). | Um objeto [ResourceResponse](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object&preserve-view=true). |

---

Agora que você atualizou os cartões, pode excluir mensagens usando o Bot Framework.

## <a name="delete-messages"></a>Excluir mensagens

No Bot Framework, cada mensagem tem seu identificador de atividade exclusivo. As mensagens podem ser excluídas usando o método `DeleteActivity` do Bot Framework.

# <a name="c"></a>[C#](#tab/dotnet)

Para excluir uma mensagem, passe a ID da atividade para o `DeleteActivityAsync` da classe `TurnContext`. Para obter mais informações, consulte Método [TurnContext.DeleteActivityAsync](/dotnet/api/microsoft.bot.builder.turncontext.deleteactivityasync?view=botbuilder-dotnet-stable&preserve-view=true).

```csharp
foreach (var activityId in _list)
{
    await turnContext.DeleteActivityAsync(activityId, cancellationToken);
}
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

Para excluir uma mensagem, passe o ID dessa atividade para o método `deleteActivity` do objeto `TurnContext`. Para obter mais informações, consulte [deleteActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#deleteactivity-string---partial-conversationreference--&preserve-view=true).

```typescript
for (let i = 0; i < activityIds.length; i++) {
    await turnContext.deleteActivity(activityIds[i]);
}
```

# <a name="python"></a>[Python](#tab/python)

Para excluir essa mensagem, passe o ID dessa atividade para o método `delete_activity` do objeto `TurnContext`. Para obter mais informações, consulte [activity-update-and-delete](https://github.com/microsoft/botbuilder-python/blob/c04ecacb22c1f4b43a671fe2f1e4782218391975/tests/teams/scenarios/activity-update-and-delete/bots/activity_update_and_delete_bot.py).

```python
for each activity_id in _list:
    await TurnContext.delete_activity(activity_id)
```

# <a name="rest-api"></a>[API REST](#tab/rest)

Para excluir uma atividade existente em uma conversa, inclua o `conversationId` e `activityId` no ponto de extremidade da solicitação.

```http
DELETE /v3/conversations/{conversationId}/activities/{activityId}
```

| **Solicitação e resposta** | **Descrição** |
|----|----|
| N/D | Um código de status HTTP que indica o resultado da operação. Nada é especificado no corpo da resposta. |

---

## <a name="code-sample"></a>Exemplo de código

O exemplo de código a seguir demonstra noções básicas de conversas:

| **Nome de exemplo** | **Descrição** | **.NET** | **Node.js** | **Python** |
|----------------------|-----------------|--------|-------------|--------|
| Noções básicas de conversa do Teams  | Demonstra noções básicas de conversas no Teams, incluindo atualização e exclusão de mensagens. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/57.teams-conversation-bot) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot) |

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Obter contexto do Teams](~/bots/how-to/get-teams-context.md)
