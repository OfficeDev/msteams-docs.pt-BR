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
# <a name="update-and-delete-messages-sent-from-your-bot"></a>Atualizar e excluir mensagens enviadas do bot

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

## <a name="updating-messages"></a>Atualizando mensagens

Em vez de fazer com que suas mensagens sejam instantâneos de dados estáticos, seu bot pode atualizar mensagens dinamicamente após enviá-las. Você pode usar atualizações de mensagens dinâmicas para cenários como atualizações de pesquisa, modificação de ações disponíveis após um pressionamento de botão ou qualquer outra alteração de estado assíncrono.

A nova mensagem não precisa coincidir com o original no tipo. Por exemplo, se a mensagem original contiver um anexo, a nova mensagem poderá ser uma mensagem de texto simples.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

Para atualizar uma mensagem existente, passe um novo `Activity` objeto com a ID de atividade existente para `UpdateActivityAsync` o método da `TurnContext` classe. *Consulte* [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable)

```csharp
var newActivity = MessageFactory.Text("The new text for the activity");
newActivity.Id = activityId;
await turnContext.UpdateActivityAsync(newActivity, cancellationToken);
```

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

Para atualizar uma mensagem existente, passe um novo `Activity` objeto com a ID de atividade existente para `updateActivity` o método do `TurnContext` objeto. *Consulte* [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--)

```typescript
const newActivity = MessageFactory.text('The new text for the activity');
newActivity.id = activityId;
await turnContext.updateActivity(newActivity);
```

# <a name="python"></a>[Python](#tab/python)

Para atualizar uma mensagem existente, passe um novo `Activity` objeto com a ID de atividade existente para `update_activity` o método da `TurnContext` classe. Consulte [TurnContextClass](link to Python API ref docs).

```python

new_activity = MessageFactory.text("The new text for the activity")
new_activity.id = activity_id
update_result = await context.update_activity(new_activity)

```

# <a name="rest-api"></a>[API REST](#tab/rest)

>[!NOTE]
>Você pode desenvolver aplicativos do teams em qualquer tecnologia de programação Web e chamar diretamente as [APIs REST do serviço do conector do bot](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0). Para fazer isso, você precisará implementar procedimentos de segurança de [autenticação](/azure/bot-service/rest-api/bot-framework-rest-connector-authentication?view=azure-bot-service-4.0) com suas solicitações de API.

Para atualizar uma atividade existente em uma conversa, inclua o `conversationId` e `activityId` o ponto de extremidade da solicitação. Para concluir esse cenário, você deve armazenar em cache a ID da atividade retornada pela chamada POST original.

```http
PUT /v3/conversations/{conversationId}/activities/{activityId}
```

| | |
|----|----|
| **Corpo da solicitação** | Um objeto [Activity](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object) |
| **Retorna** | Um objeto [ResourceResponse](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#resourceresponse-object) |

---

## <a name="deleting-messages"></a>Excluir mensagens

Na estrutura do bot, cada mensagem tem seu próprio identificador de atividade exclusivo.
As mensagens podem ser excluídas usando o método `DeleteActivity` da estrutura de bot, conforme mostrado aqui.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

Para excluir essa mensagem, passe a ID da atividade para o `DeleteActivityAsync` método da `TurnContext` classe. *Confira* o [método TurnContext. DeleteActivityAsync](/dotnet/api/microsoft.bot.builder.turncontext.deleteactivityasync?view=botbuilder-dotnet-stable)

```csharp
foreach (var activityId in _list)
{
    await turnContext.DeleteActivityAsync(activityId, cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

Para excluir essa mensagem, passe a ID dessa atividade para o `deleteActivity` método do `TurnContext` objeto. *Consulte* [deleteActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#deleteactivity-string---partial-conversationreference--)

```typescript
for (let i = 0; i < activityIds.length; i++) {
    await turnContext.deleteActivity(activityIds[i]);
}
```

# <a name="python"></a>[Python](#tab/python)

Para excluir essa mensagem, passe a ID dessa atividade para o `delete_activity` método do `TurnContext` objeto. Consulte [Activity-Update-and-Delete](https://github.com/microsoft/botbuilder-python/blob/c04ecacb22c1f4b43a671fe2f1e4782218391975/tests/teams/scenarios/activity-update-and-delete/bots/activity_update_and_delete_bot.py).

```python
for each activity_id in _list:
    await TurnContext.delete_activity(activity_id)
```

# <a name="rest-api"></a>[API REST](#tab/rest)

 Para excluir uma atividade existente em uma conversa, inclua o `conversationId` e `activityId` o ponto de extremidade da solicitação.

```http
DELETE /v3/conversations/{conversationId}/activities/{activityId}
```

| | |
|----|----|
| **Corpo da solicitação** | n/d |
| **Retorna** | Um código de status HTTP que indica o resultado da operação. Nada é especificado no corpo da resposta. |

---
