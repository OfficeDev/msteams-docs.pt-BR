---
title: Crie e envie o módulo de tarefas
author: surbhigupta
description: Como manipular a ação de invocação inicial e responder com um módulo de tarefa de um comando de extensão de mensagens de ação
localization_priority: Normal
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: f3d34a4e574169aadf49180ee8b857c8ee2b60a8
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069060"
---
# <a name="create-and-send-the-task-module"></a>Crie e envie o módulo de tarefas

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Você pode criar o módulo de tarefa usando um Cartão Adaptável ou um exibição da Web incorporado. Para criar um módulo de tarefa, você deve executar o processo chamado de solicitação de invocação inicial. Este documento abrange a solicitação de invocação inicial, propriedades de atividade de carga quando um módulo de tarefa é invocado a partir de chat 1:1, chat de grupo, canal (nova postagem), canal (resposta ao thread) e caixa de comando. 
> [!NOTE]
> Se você não estiver preenchendo o módulo de tarefas com parâmetros definidos no manifesto do aplicativo, você deve criar o módulo de tarefa para usuários com um Cartão Adaptável ou uma exibição da Web incorporada.

## <a name="the-initial-invoke-request"></a>A solicitação de invocação inicial

No processo da solicitação de invocação inicial, seu serviço recebe um objeto do tipo e você deve responder com um objeto contendo um Cartão Adaptável ou uma URL para o exibição `Activity` `composeExtension/fetchTask` da Web `task` incorporado. Junto com as propriedades de atividade de bot padrão, a carga de invocação inicial contém os seguintes metadados de solicitação:

|Nome da propriedade|Objetivo|
|---|---|
|`type`| Tipo de solicitação. Deve ser `invoke` . |
|`name`| Tipo de comando emitido ao seu serviço. Deve ser `composeExtension/fetchTask` . |
|`from.id`| ID do usuário que enviou a solicitação. |
|`from.name`| Nome do usuário que enviou a solicitação. |
|`from.aadObjectId`| Azure Active Directory ID do objeto do usuário que enviou a solicitação. |
|`channelData.tenant.id`| Locatário do Azure Active Directory. |
|`channelData.channel.id`| ID do canal (se a solicitação foi feita em um canal). |
|`channelData.team.id`| ID da equipe (se a solicitação foi feita em um canal). |
|`value.commandId` | Contém a ID do comando que foi invocado. |
|`value.commandContext` | O contexto que disparou o evento. Deve ser `compose` . |
|`value.context.theme` | O tema cliente do usuário, útil para formatação de exibição da Web incorporada. Deve ser `default` , `contrast` ou `dark` . |

### <a name="example"></a>Exemplo

O código da solicitação de invocação inicial é dado no exemplo a seguir:

```json
{
  "type": "invoke",
  "id": "f:bc319b1d-571a-194d-9ffb-11d7ab37c9ff",
  "from": {
    "id": "29:1aBjVi5MwCFfhPIV03E5uDdfpBFXp_2Yz-sjrvVg12oavg96cqpE_DiMhOpmN9zHeZpYbJcuUEKuSDy2AYWPz1A",
    "name": "Olo Brockhouse",
    "aadObjectId": "b130c271-d2eb-45f9-83ab-9eb3fe3788bc"
  }
  "channelData": {
    "tenant": {
      "id": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
    },
    "source": {
      "name": "compose"
    }
  },
  "value": {
    "commandId": "Test",
    "commandContext": "compose",
    "requestId": "fe50f49e5c74440bb2ebf07f49e9553c",
    "context": {
      "theme": "default"
    }
  },
  "name": "composeExtension/fetchTask"
```

## <a name="payload-activity-properties-when-a-task-module-is-invoked-from-11-chat"></a>Propriedades de atividade de carga quando um módulo de tarefa é invocado do chat 1:1 

As propriedades de atividade de carga quando um módulo de tarefa é invocado do chat 1:1 são listadas da seguinte forma:

|Nome da propriedade|Objetivo|
|---|---|
|`type`| Tipo de solicitação. Deve ser `invoke` . |
|`name`| Tipo de comando emitido ao seu serviço. Deve ser `composeExtension/fetchTask` . |
|`from.id`| ID do usuário que enviou a solicitação. |
|`from.name`| Nome do usuário que enviou a solicitação. |
|`from.aadObjectId`| Azure Active Directory ID do objeto do usuário que enviou a solicitação. |
|`channelData.tenant.id`| Locatário do Azure Active Directory. |
|`channelData.source.name`| O nome de origem de onde o módulo de tarefa é invocado. |
|`ChannelData.legacy. replyToId`| Obtém ou define a ID da mensagem para a qual esta mensagem é uma resposta. |
|`value.commandId` | Contém a ID do comando que foi invocado. |
|`value.commandContext` | O contexto que disparou o evento. Deve ser `compose` . |
|`value.context.theme` | O tema cliente do usuário, útil para formatação de exibição da Web incorporada. Deve ser `default` , `contrast` ou `dark` . |

### <a name="example"></a>Exemplo

As propriedades de atividade de carga quando um módulo de tarefa é invocado do chat 1:1 são fornecidas no exemplo a seguir:

```json
{
  "type": "invoke",
  "id": "f:bc319b1d-571a-194d-9ffb-11d7ab37c9ff",
  "from": {
    "id": "29:1aBjVi5MwCFfhPIV03E5uDdfpBFXp_2Yz-sjrvVg12oavg96cqpE_DiMhOpmN9zHeZpYbJcuUEKuSDy2AYWPz1A",
    "name": "Olo Brockhouse",
    "aadObjectId": "b130c271-d2eb-45f9-83ab-9eb3fe3788bc"
  }
  "channelData": {
    "tenant": {
      "id": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
    },
    "source": {
      "name": "compose"
    }
  },
  "value": {
    "commandId": "Test",
    "commandContext": "compose",
    "requestId": "fe50f49e5c74440bb2ebf07f49e9553c",
    "context": {
      "theme": "default"
    }
  },
  "name": "composeExtension/fetchTask"
}
```
## <a name="payload-activity-properties-when-a-task-module-is-invoked-from-a-group-chat"></a>Propriedades de atividade de carga quando um módulo de tarefa é invocado de um chat de grupo 

As propriedades de atividade de carga quando um módulo de tarefa é invocado de um chat de grupo são listadas da seguinte forma:

|Nome da propriedade|Objetivo|
|---|---|
|`type`| Tipo de solicitação. Deve ser `invoke` . |
|`name`| Tipo de comando emitido ao seu serviço. Deve ser `composeExtension/fetchTask` . |
|`from.id`| ID do usuário que enviou a solicitação. |
|`from.name`| Nome do usuário que enviou a solicitação. |
|`from.aadObjectId`| Azure Active Directory ID do objeto do usuário que enviou a solicitação. |
|`channelData.tenant.id`| Locatário do Azure Active Directory. |
|`channelData.source.name`| O nome de origem de onde o módulo de tarefa é invocado. |
|`ChannelData.legacy. replyToId`| Obtém ou define a ID da mensagem para a qual esta mensagem é uma resposta. |
|`value.commandId` | Contém a ID do comando que foi invocado. |
|`value.commandContext` | O contexto que disparou o evento. Deve ser `compose` . |
|`value.context.theme` | O tema cliente do usuário, útil para formatação de exibição da Web incorporada. Deve ser `default` , `contrast` ou `dark` . |

### <a name="example"></a>Exemplo

As propriedades de atividade de carga quando um módulo de tarefa é invocado de um chat de grupo são fornecidas no exemplo a seguir:

```json
{
  "type": "invoke",
  "id": "f:bf72031f-a17e-f99c-48dc-5c0714950d87",
  "from": {
    "id": "29:1aBjVi5MwCFfhPIV03E5uDdfpBFXp_2Yz-sjrvVg12oavg96cqpE_DiMhOpmN9zHeZpYbJcuUEKuSDy2AYWPz1A",
    "name": "Olo Brockhouse",
    "aadObjectId": "b130c271-d2eb-45f9-83ab-9eb3fe3788bc"
  },
  "conversation": {
    "isGroup": true,
    "conversationType": "groupChat",
    "id": "19:d77be72390a1416e9644261e9064fa00@thread.skype",
    "tenantId": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
  },
  "channelData": {
    "tenant": {
      "id": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
    },
    "source": {
      "name": "compose"
    }
  },
  "value": {
    "commandId": "Test",
    "commandContext": "compose",
    "requestId": "213167a1e3b6428b93e186ea5407c759",
    "context": {
      "theme": "default"
    }
  },
  "name": "composeExtension/fetchTask"
}
```

## <a name="payload-activity-properties-when-a-task-module-is-invoked-from-a-channel-new-post"></a>Propriedades de atividade de carga quando um módulo de tarefa é invocado de um canal (nova postagem) 

As propriedades de atividade de carga quando um módulo de tarefa é invocado de um canal (nova postagem) são listadas da seguinte forma:

|Nome da propriedade|Objetivo|
|---|---|
|`type`| Tipo de solicitação. Deve ser `invoke` . |
|`name`| Tipo de comando emitido ao seu serviço. Deve ser `composeExtension/fetchTask` . |
|`from.id`| ID do usuário que enviou a solicitação. |
|`from.name`| Nome do usuário que enviou a solicitação. |
|`from.aadObjectId`| Azure Active Directory ID do objeto do usuário que enviou a solicitação. |
|`channelData.tenant.id`| Locatário do Azure Active Directory. |
|`channelData.channel.id`| ID do canal (se a solicitação foi feita em um canal). |
|`channelData.team.id`| ID da equipe (se a solicitação foi feita em um canal). |
|`channelData.source.name`| O nome de origem de onde o módulo de tarefa é invocado. |
|`ChannelData.legacy. replyToId`| Obtém ou define a ID da mensagem para a qual esta mensagem é uma resposta. |
|`value.commandId` | Contém a ID do comando que foi invocado. |
|`value.commandContext` | O contexto que disparou o evento. Deve ser `compose` . |
|`value.context.theme` | O tema cliente do usuário, útil para formatação de exibição da Web incorporada. Deve ser `default` , `contrast` ou `dark` . |

### <a name="example"></a>Exemplo

As propriedades de atividade de carga quando um módulo de tarefa é invocado de um canal (nova postagem) são fornecidas no exemplo a seguir:

```json
{
  "type": "invoke",
  "id": "f:a5fbb109-c989-c449-ee83-71ac99919d4b",
  "from": {
    "id": "29:1aBjVi5MwCFfhPIV03E5uDdfpBFXp_2Yz-sjrvVg12oavg96cqpE_DiMhOpmN9zHeZpYbJcuUEKuSDy2AYWPz1A",
    "name": "Olo Brockhouse",
    "aadObjectId": "b130c271-d2eb-45f9-83ab-9eb3fe3788bc"
  },
  "conversation": {
    "isGroup": true,
    "conversationType": "channel",
    "id": "19:6decf54d86d945e4b3924b63a9161a78@thread.skype",
    "name": "parsable",
    "tenantId": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
  },
  "channelData": {
    "channel": {
      "id": "19:6decf54d86d945e4b3924b63a9161a78@thread.skype"
    },
    "team": {
      "id": "19:acca514e83cb497e960e0b014d405336@thread.skype"
    },
    "tenant": {
      "id": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
    },
    "source": {
      "name": "compose"
    }
  },
  "value": {
    "commandId": "Test",
    "commandContext": "compose",
    "requestId": "5336640edc7748b28ce2df43f5b45963",
    "context": {
      "theme": "default"
    }
  },
  "name": "composeExtension/fetchTask"
}
```

## <a name="payload-activity-properties-when-a-task-module-is-invoked-from-a-channel-reply-to-thread"></a>Propriedades de atividade de carga quando um módulo de tarefa é invocado de um canal (responder ao thread) 

As propriedades de atividade de carga quando um módulo de tarefa é invocado de um canal (resposta ao thread) são listadas da seguinte forma:

|Nome da propriedade|Objetivo|
|---|---|
|`type`| Tipo de solicitação. Deve ser `invoke` . |
|`name`| Tipo de comando emitido ao seu serviço. Deve ser `composeExtension/fetchTask` . |
|`from.id`| ID do usuário que enviou a solicitação. |
|`from.name`| Nome do usuário que enviou a solicitação. |
|`from.aadObjectId`| Azure Active Directory ID do objeto do usuário que enviou a solicitação. |
|`channelData.tenant.id`| Locatário do Azure Active Directory. |
|`channelData.channel.id`| ID do canal (se a solicitação foi feita em um canal). |
|`channelData.team.id`| ID da equipe (se a solicitação foi feita em um canal). |
|`channelData.source.name`| O nome de origem de onde o módulo de tarefa é invocado. |
|`ChannelData.legacy. replyToId`| Obtém ou define a ID da mensagem para a qual esta mensagem é uma resposta. |
|`value.commandId` | Contém a ID do comando que foi invocado. |
|`value.commandContext` | O contexto que disparou o evento. Deve ser `compose` . |
|`value.context.theme` | O tema cliente do usuário, útil para formatação de exibição da Web incorporada. Deve ser `default` , `contrast` ou `dark` . |

### <a name="example"></a>Exemplo

As propriedades de atividade de carga quando um módulo de tarefa é invocado de um canal (resposta ao thread) são fornecidas no exemplo a seguir:

```json
{
  "type": "invoke",
  "id": "f:19ccc884-c792-35ef-2f40-d0ff43dcca71",
  "from": {
    "id": "29:1aBjVi5MwCFfhPIV03E5uDdfpBFXp_2Yz-sjrvVg12oavg96cqpE_DiMhOpmN9zHeZpYbJcuUEKuSDy2AYWPz1A",
    "name": "Olo Brockhouse",
    "aadObjectId": "b130c271-d2eb-45f9-83ab-9eb3fe3788bc"
  },
  "conversation": {
    "isGroup": true,
    "conversationType": "channel",
    "id": "19:6decf54d86d945e4b3924b63a9161a78@thread.skype;messageid=1611060744833",
    "name": "parsable",
    "tenantId": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
  },
  "channelData": {
    "channel": {
      "id": "19:6decf54d86d945e4b3924b63a9161a78@thread.skype"
    },
    "team": {
      "id": "19:acca514e83cb497e960e0b014d405336@thread.skype"
    },
    "tenant": {
      "id": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
    },
    "source": {
      "name": "compose"
    }
  },
  "value": {
    "commandId": "TEst",
    "commandContext": "message",
    "requestId": "7f7d22efe5414818becebcec649a7912",
    "messagePayload": {
      "linkToMessage": "https://teams.microsoft.com/l/message/19:6decf54d86d945e4b3924b63a9161a78@thread.skype/1611060744833",
      "id": "1611060744833",
      "replyToId": null,
      "createdDateTime": "2021-01-19T12:52:24.833Z",
      "lastModifiedDateTime": null,
      "deleted": false,
      "summary": null,
      "importance": "normal",
      "locale": "en-us",
      "body": {
        "contentType": "html",
        "content": "<div><div><at id=\"0\">Testing outgoing Webhook-Nikitha</at> - Hi</div>\n</div>"
      },
      "from": {
        "device": null,
        "conversation": null,
        "user": {
          "userIdentityType": "aadUser",
          "id": "b130c271-d2eb-45f9-83ab-9eb3fe3788bc",
          "displayName": "Olo Brockhouse"
        },
        "application": null
      },
      "reactions": [],
      "mentions": [
        {
          "id": 0,
          "mentionText": "Testing outgoing Webhook-Nikitha",
          "mentioned": {
            "device": null,
            "conversation": null,
            "user": null,
            "application": {
              "applicationIdentityType": "webhook",
              "id": "b8c1c68c-e290-4bdd-81c3-266f310751dc",
              "displayName": "Testing outgoing Webhook-Nikitha"
            }
          }
        }
      ],
      "attachments": []
    },
    "context": {
      "theme": "default"
    }
  },
  "name": "composeExtension/fetchTask"
}
```

## <a name="payload-activity-properties-when-a-task-module-is-invoked-from-a-command-box"></a>Propriedades de atividade de carga quando um módulo de tarefa é invocado de uma caixa de comando 

As propriedades de atividade de carga quando um módulo de tarefa é invocado de uma caixa de comando são listadas da seguinte forma:

|Nome da propriedade|Objetivo|
|---|---|
|`type`| Tipo de solicitação. Deve ser `invoke` . |
|`name`| Tipo de comando emitido ao seu serviço. Deve ser `composeExtension/fetchTask` . |
|`from.id`| ID do usuário que enviou a solicitação. |
|`from.name`| Nome do usuário que enviou a solicitação. |
|`from.aadObjectId`| Azure Active Directory ID do objeto do usuário que enviou a solicitação. |
|`channelData.tenant.id`| Locatário do Azure Active Directory. |
|`channelData.source.name`| O nome de origem de onde o módulo de tarefa é invocado. |
|`value.commandId` | Contém a ID do comando que foi invocado. |
|`value.commandContext` | O contexto que disparou o evento. Deve ser `compose` . |
|`value.context.theme` | O tema cliente do usuário, útil para formatação de exibição da Web incorporada. Deve ser `default` , `contrast` ou `dark` . |

### <a name="example"></a>Exemplo

As propriedades de atividade de carga quando um módulo de tarefa é invocado de uma caixa de comando são fornecidas no exemplo a seguir:

```json
{
  "type": "invoke",
  "id": "f:172560f1-95f9-3189-edb2-b7612cd1a3cd",
    "id": "29:1aBjVi5MwCFfhPIV03E5uDdfpBFXp_2Yz-sjrvVg12oavg96cqpE_DiMhOpmN9zHeZpYbJcuUEKuSDy2AYWPz1A",
    "name": "Olo Brockhouse",
    "aadObjectId": "b130c271-d2eb-45f9-83ab-9eb3fe3788bc"
  },
  "conversation": {
    "isGroup": true,
    "conversationType": "channel",
    "id": "19:6decf54d86d945e4b3924b63a9161a78@thread.skype",
    "name": "parsable",
    "tenantId": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
  },
  "channelData": {
    "channel": {
      "id": "19:6decf54d86d945e4b3924b63a9161a78@thread.skype"
    },
    "team": {
      "id": "19:acca514e83cb497e960e0b014d405336@thread.skype"
    },
    "tenant": {
      "id": "0d9b645f-597b-41f0-a2a3-ef103fbd91bb"
    },
    "source": {
      "name": "compose"
    }
  },
  "value": {
    "commandId": "TEst",
    "commandContext": "compose",
    "requestId": "d2ce690cdc2b4920a538e75882610a30",
    "context": {
      "theme": "default"
    }
  },
  "name": "composeExtension/fetchTask"
}
```

### <a name="example"></a>Exemplo 

A seção de código a seguir é um exemplo de `fetchTask` solicitação:

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  //handle fetch task
}
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreviewBot extends TeamsActivityHandler {
  handleTeamsMessagingExtensionFetchTask(context, action) {
    //hand fetch task
  }
}
```

# <a name="json"></a>[JSON](#tab/json)

```json
{
  "name": "composeExtension/fetchTask",
  "type": "invoke",
  "timestamp": "2019-07-01T22:57:22.175Z",
  "localTimestamp": "2019-07-01T15:57:22.175-07:00",
  "id": "f:0123456878990178955",
  "channelId": "msteams",
  "serviceURL": "https://smba.trafficmanager.net/amer/",
  "from": {
    "id": "29:1test2GgHIa0DXzDT_OGwL5vSMZdAxDlGR7hYxZ6_JBVqHz2Zq9Nm44FUNWqHCdGBwHg8WrlFRsYrd0cCAS7dig",
    "name": "John Smith",
    "aadObjectId": "1234567d-1234-462a-8952-35b75f16f1e1"
  },
  "conversation": {
    "isGroup": true,
    "conversationType": "channel",
    "tenantId": "1234abcd-1234-12ab-12ab-35b75f16f1e1",
    "id": "19:83ed1d507cb5427c93495cf914326310@thread.skype"
  },
  "recipient": {
    "id": "28:049566e0-4401-4bcf-86a1-ce22082ce03a",
    "name": "mess"
  },
  "entities": [
    {
      "locale": "en-US",
      "country": "US",
      "platform": "Windows",
      "type": "clientInfo"
    }
  ],
  "channelData": {
    "channel": {
      "id": "19:83ab1d507cb5427c93495cf912345678@thread.skype"
    },
    "team": {
      "id": "19:83ab1d507cb5427c93495cf912345678@thread.skype"
    },
    "tenant": {
      "id": "1234abcd-1234-12ab-12ab-35b75f16f1e1"
    },
    "source": {
      "name": "compose"
    }
  },
  "value": {
    "commandId": "hello",
    "commandContext": "compose",
    "context": {
      "theme": "dark"
    }
  },
  "locale": "en-US"
}
```

* * *

## <a name="initial-invoke-request-from-a-message"></a>Solicitação de invocação inicial de uma mensagem

Quando o bot é invocado de uma mensagem, o objeto na solicitação de invocação inicial deve conter os detalhes da mensagem da sua extensão de `value` mensagens. As matrizes e são opcionais e não estão presentes se não houver reações ou `reactions` `mentions` menções na mensagem original. A seção a seguir é um exemplo do `value` objeto:

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  var messageText = action.MessagePayload.Body.Content;
  var fromId = action.MessagePayload.From.User.Id;

  //finish handling the fetchTask
}
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  handleTeamsMessagingExtensionFetchTask(context, action) {
    const messageText = action.messagePayload.body.content;

    //finish handling the fetchTask
  }
}
```

# <a name="json"></a>[JSON](#tab/json)

```json
{
  "name": "composeExtension/submitAction",
  "type": "invoke",
...
  "value": {
    "commandId": "setReminder",
    "commandContext": "message",
    "messagePayload": {
      "id": "1111111111",
      "replyToId": null,
      "createdDateTime": "2019-02-25T21:29:36.065Z",
      "lastModifiedDateTime": null,
      "deleted": false,
      "subject": "Message subject",
      "summary": null,
      "importance": "normal",
      "locale": "en-us",
      "body": {
        "contentType": "html",
        "content": "This is the message the messaging extension was invoked from."
    },
      "from": {
        "device": null,
        "conversation": null,
        "user": {
          "userIdentityType": "aadUser",
          "id": "wxyz12ab8-ab12-cd34-ef56-098abc123876",
          "displayName": "Jamie Smythe"
        },
        "application": null
      },
      "reactions": [
        {
          "reactionType": "like",
          "createdDateTime": "2019-02-25T22:40:40.806Z",
          "user": {
            "device": null,
            "conversation": null,
            "user": {
              "userIdentityType": "aadUser",
              "id": "qrst12346-ab12-cd34-ef56-098abc123876",
              "displayName": "Jim Brown"
            },
            "application": null
          }
        }
      ],
      "mentions": [
        {
          "id": 0,
          "mentionText": "Sarah",
          "mentioned": {
            "device": null,
            "conversation": null,
            "user": {
              "userIdentityType": "aadUser",
              "id": "ab12345678-ab12-cd34-ef56-098abc123876",
              "displayName": "Sarah"
            },
            "application": null
          }
        }
      ]
    }
  ...
```

* * *

## <a name="respond-to-the-fetchtask"></a>Responder ao fetchTask

Responda à solicitação de invocação com um objeto que contém um objeto com o Cartão Adaptável ou a URL da `task` Web ou uma mensagem de cadeia de `taskInfo` caracteres simples.

|Nome da propriedade|Objetivo|
|---|---|
|`type`| Pode ser para `continue` apresentar um formulário ou para um `message` pop-up simples. |
|`value`| Um `taskInfo` objeto para um formulário ou um `string` para uma mensagem. |

O esquema do objeto taskInfo é:

|Nome da propriedade|Objetivo|
|---|---|
|`title`| O título do módulo de tarefa.|
|`height`| Deve ser um inteiro (em pixels) ou `small` `medium` , `large` .|
|`width`| Deve ser um inteiro (em pixels) ou `small` `medium` , `large` .|
|`card`| O cartão adaptável que define o formulário (se estiver usando um).
|`url`| A URL a ser aberta dentro do módulo de tarefas como uma exibição da Web incorporada.|
|`fallbackUrl`| Se um cliente não suportar o recurso de módulo de tarefa, essa URL será aberta em uma guia do navegador. |

### <a name="respond-to-the-fetchtask-with-an-adaptive-card"></a>Responder ao fetchTask com um Cartão Adaptável

Ao usar um cartão adaptável, você deve responder com um objeto com o `task` objeto que contém um Cartão `value` Adaptável.

#### <a name="example"></a>Exemplo

A seção de código a seguir é um exemplo de `fetchTask` resposta com um cartão adaptável:

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

Este exemplo usa o [pacote AdaptiveCards NuGet](https://www.nuget.org/packages/AdaptiveCards) além do SDK da Estrutura de Bot.

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  string placeholder = "Not invoked from message";

  if (action.MessagePayload != null)
  {
      var messageText = action.MessagePayload.Body.Content;
      var fromId = action.MessagePayload.From.User.Id;
      placeholder = "Invoked from message";
  }

  var response = new MessagingExtensionActionResponse()
  {
    Task = new TaskModuleContinueResponse()
    {
      Value = new TaskModuleTaskInfo()
      {
        Height = "small",
        Width = "small",
        Title = "Example task module",
        Card = new Attachment()
        {
          ContentType = AdaptiveCard.ContentType,
          Content = new AdaptiveCard("1.0")
          {
            Body = new List<AdaptiveElement>()
            {
              new AdaptiveTextInput() { Id = "FormField1", Placeholder = placeholder},
              new AdaptiveTextInput() { Id = "FormField2", Placeholder = "FormField2"},
              new AdaptiveTextInput() { Id = "FormField3", Placeholder = "FormField3"},
            },
            Actions = new List<AdaptiveAction>()
            {
              new AdaptiveSubmitAction()
              {
                Type = AdaptiveSubmitAction.TypeName,
                Title = "Submit",
              },
            },
          },
        },
      },
    },
  };
  return response;
}
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
    handleTeamsMessagingExtensionFetchTask(context, action) {
      const adaptiveCard = CardFactory.adaptiveCard({
        actions: [{
          data: { submitLocation: 'messagingExtensionFetchTask'},
          title: 'Submit',
          type: 'Action.Submit'
        }],
        body: [
          { text: 'Task Module', type: 'TextBlock', weight: 'bolder'},
          { type: 'TextBlock', text: 'Enter text for Question:' },
          { id: 'Question', placeholder: 'Question text here', type: 'Input.Text', value: userText },
          { type: 'TextBlock', text: 'Options for Question:' },
          { type: 'TextBlock', text: 'Is Multi-Select:' },
          {
            choices: [{ title: 'True', value: 'true' }, { title: 'False', value: 'false' }],
            id: 'MultiSelect',
            isMultiSelect: false,
            style: 'expanded',
            type: 'Input.ChoiceSet',
            value: isMultiSelect ? 'true' : 'false'
          },
          { id: 'Option1', placeholder: 'Option 1 here', type: 'Input.Text', value: option1 },
          { id: 'Option2', placeholder: 'Option 2 here', type: 'Input.Text', value: option2 }
        ],
        type: 'AdaptiveCard',
        version: '1.0'
      });

      return {
        task: {
          type: 'continue',
          value: {
            card: adaptiveCard,
            height: 450,
            title: 'Task Module Fetch Example',
            url: null,
            width: 500
          }
        }
      };
    }
}
```

# <a name="json"></a>[JSON](#tab/json)

```json
 {
  "task": {
    "type": "continue",
    "value": {
      "title": "Task module title",
      "height": 500,
      "width": "medium",
      "card": {
        "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
        "type": "AdaptiveCard",
        "version": "1.0",
        "body": [
          {
            "type": "Input.Text",
            "placeholder": "FormField1",
            "id": "FormField1"
          },
          {
            "type": "Input.Text",
            "placeholder": "FormField2",
            "id": "FormField2"
          },
          {
            "type": "Input.Text",
            "placeholder": "FormField3",
            "id": "FormField3"
          },
          {
            "type": "ActionSet",
            "actions": [
              {
                "type": "Action.Submit",
                "title": "Action.Submit",
                "id": "submitAction"
              }
            ]
          }
        ]
      }
    }
  }
}
```

* * *

### <a name="create-a-task-module-with-an-embedded-web-view"></a>Criar um módulo de tarefa com um visualização da Web incorporado

Ao usar uma exibição da Web incorporada, você deve responder com um objeto com o objeto que contém a URL para o formulário `task` da Web que deseja `value` carregar. Os domínios de qualquer URL que você deseja carregar devem ser incluídos na `validDomains` matriz no manifesto do aplicativo. Para obter mais informações sobre como criar sua exibição da Web incorporada, consulte a [documentação do módulo de tarefas](~/task-modules-and-cards/what-are-task-modules.md). 

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  string placeholder = "Not invoked from message";

  if (action.MessagePayload != null)
  {
      var messageText = action.MessagePayload.Body.Content;
      var fromId = action.MessagePayload.From.User.Id;
      placeholder = "Invoked from message";
  }

  var response = new MessagingExtensionActionResponse()
  {
    Task = new TaskModuleContinueResponse()
    {
      Value = new TaskModuleTaskInfo()
      {
        Height = "small",
        Width = "small",
        Title = "Example task module",
        Url = "https://contoso.com/msteams/taskmodules/newcustomer",
        },
      },
    },
  };
  return response;
}
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  handleTeamsMessagingExtensionFetchTask(context, action) {
    return {
      task: {
        type: 'continue',
        value: {
          width: 500,
          height: 450,
          title: 'Task Module Fetch Example',
          url: 'https://contoso.com/msteams/taskmodules/newcustomer',
          fallbackUrl: 'https://contoso.com/msteams/taskmodules/newcustomer'
        }
      }
    };
  }
}
```

# <a name="json"></a>[JSON](#tab/json)

```json
{
  "task": {
    "type": "continue",
    "value": {
      "title": "Task module title",
      "height": 500,
      "width": "medium",
      "url": "https://contoso.com/msteams/taskmodules/newcustomer",
      "fallbackUrl": "https://contoso.com/msteams/taskmodules/newcustomer"
    }
  }
}
```

* * *

### <a name="request-to-install-your-conversational-bot"></a>Solicitar a instalação do bot de conversa

Se o aplicativo contiver um bot de conversa, instale o bot na conversa e carregue o módulo de tarefa. O bot é útil para obter contexto adicional para o módulo de tarefa. Um exemplo para esse cenário é buscar a lista para preencher um controle de selador de pessoas ou a lista de canais em uma equipe.

Quando a extensão de mensagens receber a invocação, verifique se o bot está instalado no `composeExtension/fetchTask` contexto atual para facilitar o fluxo. Por exemplo, verifique o fluxo com uma chamada get roster. Se o bot não estiver instalado, retorne um Cartão Adaptável com uma ação que solicita que o usuário instale o bot. O usuário deve ter a permissão para instalar os aplicativos nesse local para verificação. Se a instalação do aplicativo não tiver êxito, o usuário receberá uma mensagem para entrar em contato com o administrador.

#### <a name="example"></a>Exemplo 

A seção de código a seguir é um exemplo da resposta:

```json
{
  "type": "AdaptiveCard",
  "body": [
    {
      "type": "TextBlock",
      "text": "Looks like you haven't used Disco in this team/chat"
    }
  ],
  "actions": [
    {
      "type": "Action.Submit",
      "title": "Continue",
      "data": {
        "msteams": {
          "justInTimeInstall": true
        }
      }
    }
  ],
  "version": "1.0"
}
```

Após a instalação do bot de conversa, ele recebe outra mensagem de invocação `name = composeExtension/submitAction` com e `value.data.msteams.justInTimeInstall = true` .

#### <a name="example"></a>Exemplo 

A seção de código a seguir é um exemplo da resposta da tarefa à invocação:

```json
{
  "value": {
    "commandId": "giveKudos",
    "commandContext": "compose",
    "context": {
      "theme": "default"
    },
    "data": {
      "msteams": {
        "justInTimeInstall": true
      }
    }
  },
  "conversation": {
    "id": "19:7705841b240044b297123ad7f9c99217@thread.skype"
  },
  "name": "composeExtension/submitAction",
  "imdisplayname": "Bob Smith"
}
```

A resposta da tarefa à invocação deve ser semelhante à do bot instalado.

#### <a name="example"></a>Exemplo 

A seção de código a seguir é um exemplo de instalação just-in-time do aplicativo com cartão Adaptável: 

```csharp
private static Attachment GetAdaptiveCardAttachmentFromFile(string fileName)
  {
      //Read the card json and create attachment.
         string[] paths = { ".", "Resources", fileName };
         var adaptiveCardJson = File.ReadAllText(Path.Combine(paths));
         var adaptiveCardAttachment = new Attachment()
            {
                ContentType = "application/vnd.microsoft.card.adaptive",
                Content = JsonConvert.DeserializeObject(adaptiveCardJson),
            };
            return adaptiveCardAttachment;
        }
```

* * *

## <a name="code-sample"></a>Exemplo de código

| Exemplo de nome           | Descrição | .NET    | Node.js   |   
|:---------------------|:--------------|:---------|:--------|
|Teams ação de extensão de mensagens| Descreve como definir comandos de ação, criar módulo de tarefa e responder à ação de envio do módulo de tarefa. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) | 
|Teams de extensão de mensagens   |  Descreve como definir comandos de pesquisa e responder a pesquisas.        |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|

## <a name="see-also"></a>Confira também

[Definir comandos de ação](~/messaging-extensions/how-to/action-commands/define-action-command.md)


## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"] 
> [Responder ao comando de ação](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)

