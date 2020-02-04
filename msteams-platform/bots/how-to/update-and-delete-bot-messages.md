---
title: Atualizar e excluir mensagens enviadas do bot
author: WashingtonKayaker
description: Como atualizar e excluir mensagens enviadas do bot do Microsoft Teams
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 012a6edb77f75c43cff01c58fb94e03fd4f61a85
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672837"
---
# <a name="update-and-delete-messages-sent-from-your-bot"></a>Atualizar e excluir mensagens enviadas do bot

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

## <a name="updating-messages"></a>Atualizando mensagens

Em vez de fazer com que suas mensagens sejam instantâneos de dados estáticos, seu bot pode atualizar mensagens dinamicamente após enviá-las. Você pode usar atualizações de mensagens dinâmicas para cenários como atualizações de pesquisa, modificação de ações disponíveis após um pressionamento de botão ou qualquer outra alteração de estado assíncrono.

A nova mensagem não precisa coincidir com o original no tipo. Por exemplo, se a mensagem original contiver um anexo, a nova mensagem poderá ser uma mensagem de texto simples.

# <a name="cnettabdotnet"></a>[C#/.NET](#tab/dotnet)

Para atualizar uma mensagem existente, passe um novo `Activity` objeto com a ID de atividade existente para `UpdateActivityAsync` o método da `TurnContext` classe. *Consulte* [TurnContextClass](/dotnet/api/microsoft.bot.builder.turncontext?view=botbuilder-dotnet-stable)

```csharp
var newActivity = MessageFactory.Text("The new text for the activity");
newActivity.Id = activityId;
await turnContext.UpdateActivityAsync(newActivity, cancellationToken);
```

# <a name="typescriptnodejstabtypescript"></a>[TypeScript/node. js](#tab/typescript)

Para atualizar uma mensagem existente, passe um novo `Activity` objeto com a ID de atividade existente para `updateActivity` o método do `TurnContext` objeto. *Consulte* [updateActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#updateactivity-partial-activity--)

```typescript
const newActivity = MessageFactory.text('The new text for the activity');
newActivity.id = activityId;
await turnContext.updateActivity(newActivity);
```

# <a name="pythontabpython"></a>[Python](#tab/python)

Para atualizar uma mensagem existente, passe um novo `Activity` objeto com a ID de atividade existente para `update_activity` o método da `TurnContext` classe. Consulte [TurnContextClass](link to Python API ref docs).

```python

new_activity = MessageFactory.text("The new text for the activity")
new_activity.id = activity_id
update_result = await context.update_activity(new_activity)

```

---

## <a name="deleting-messages"></a>Excluir mensagens

Na estrutura do bot, cada mensagem tem seu próprio identificador de atividade exclusivo.
As mensagens podem ser excluídas usando o método `DeleteActivity` da estrutura de bot, conforme mostrado aqui.

# <a name="cnettabdotnet"></a>[C#/.NET](#tab/dotnet)

Para excluir essa mensagem, passe a ID da atividade para o `DeleteActivityAsync` método da `TurnContext` classe. *Confira* o [método TurnContext. DeleteActivityAsync](/dotnet/api/microsoft.bot.builder.turncontext.deleteactivityasync?view=botbuilder-dotnet-stable)

```csharp
foreach (var activityId in _list)
{
    await turnContext.DeleteActivityAsync(activityId, cancellationToken);
}
```

# <a name="typescriptnodejstabtypescript"></a>[TypeScript/node. js](#tab/typescript)

Para excluir essa mensagem, passe a ID dessa atividade para o `deleteActivity` método do `TurnContext` objeto. *Consulte* [deleteActivity](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest#deleteactivity-string---partial-conversationreference--)

```typescript
for (let i = 0; i < activityIds.length; i++) {
    await turnContext.deleteActivity(activityIds[i]);
}
```

# <a name="pythontabpython"></a>[Python](#tab/python)

Para excluir essa mensagem, passe a ID dessa atividade para o `delete_activity` método do `TurnContext` objeto. Consulte [delete_activity](link to Python API ref docs).

```python
for each activity_id in _list:
    await TurnContext.delete_activity(activity_id)
```

---

