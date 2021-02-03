---
title: Criar e enviar o módulo de tarefas
author: clearab
description: Como manipular a ação de invocação inicial e responder com um módulo de tarefa de um comando de extensão de mensagem de ação
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 58fb7e1ff5690b33c2e23f68529f05869afa9016
ms.sourcegitcommit: ce74f821660b1258c72b3c3f71c1cf177e7e92ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/02/2021
ms.locfileid: "50072872"
---
# <a name="create-and-send-the-task-module"></a>Criar e enviar o módulo de tarefas

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Se você não estiver preenchendo o módulo de tarefa com parâmetros definidos no manifesto do aplicativo, você deve criar o módulo de tarefa para os usuários. Use um Cartão Adaptável ou uma exibição da Web incorporada.

## <a name="the-initial-invoke-request"></a>A solicitação de invocação inicial

Usando esse método, seu serviço receberá um objeto do tipo e você deverá responder com um objeto contendo o cartão adaptável ou uma URL para o modo de exibição `Activity` `composeExtension/fetchTask` da Web `task` incorporado. Juntamente com as propriedades de atividade de bot padrão, a carga de invocação inicial contém os seguintes metadados de solicitação:

|Nome da propriedade|Finalidade|
|---|---|
|`type`| Tipo de solicitação. Deve `invoke` ser. |
|`name`| Tipo de comando emitido para o serviço. Deve `composeExtension/fetchTask` ser. |
|`from.id`| ID do usuário que enviou a solicitação. |
|`from.name`| Nome do usuário que enviou a solicitação. |
|`from.aadObjectId`| Azure Active Directory object id of the user that sent the request. |
|`channelData.tenant.id`| Locatário do Azure Active Directory. |
|`channelData.channel.id`| ID do canal (se a solicitação foi feita em um canal). |
|`channelData.team.id`| ID da equipe (se a solicitação foi feita em um canal). |
|`value.commandId` | Contém a ID do comando que foi invocado. |
|`value.commandContext` | O contexto que disparou o evento. Deve `compose` ser. |
|`value.context.theme` | O tema do cliente do usuário, útil para formatação de exibição da Web incorporada. Deve ser `default` , `contrast` ou `dark` . |

### <a name="payload-activity-properties-when-invoked-a-task-module-from-11-chat-are-listed-in-the-following-section"></a>As propriedades de atividade de carga quando invocado um módulo de tarefa de chat 1:1 são listadas na seção a seguir:

|Nome da propriedade|Finalidade|
|---|---|
|`type`| Tipo de solicitação. Deve `invoke` ser. |
|`name`| Tipo de comando emitido para o serviço. Deve `composeExtension/fetchTask` ser. |
|`from.id`| ID do usuário que enviou a solicitação. |
|`from.name`| Nome do usuário que enviou a solicitação. |
|`from.aadObjectId`| Azure Active Directory object id of the user that sent the request. |
|`channelData.tenant.id`| Locatário do Azure Active Directory. |
|`channelData.source.name`| O nome de origem do qual o módulo de tarefa é invocado. |
|`ChannelData.legacy. replyToId`| Obtém ou define a ID da mensagem para a qual esta mensagem é uma resposta. |
|`value.commandId` | Contém a ID do comando que foi invocado. |
|`value.commandContext` | O contexto que disparou o evento. Deve `compose` ser. |
|`value.context.theme` | O tema do cliente do usuário, útil para formatação de exibição da Web incorporada. Deve ser `default` , `contrast` ou `dark` . |

### <a name="payload-activity-properties-when-invoked-a-task-module-from-a-group-chat-are-listed-in-the-following-section"></a>As propriedades de atividade de carga quando invocado um módulo de tarefa de um chat de grupo são listadas na seção a seguir:

|Nome da propriedade|Finalidade|
|---|---|
|`type`| Tipo de solicitação. Deve `invoke` ser. |
|`name`| Tipo de comando emitido para o serviço. Deve `composeExtension/fetchTask` ser. |
|`from.id`| ID do usuário que enviou a solicitação. |
|`from.name`| Nome do usuário que enviou a solicitação. |
|`from.aadObjectId`| Azure Active Directory object id of the user that sent the request. |
|`channelData.tenant.id`| Locatário do Azure Active Directory. |
|`channelData.source.name`| O nome de origem do qual o módulo de tarefa é invocado. |
|`ChannelData.legacy. replyToId`| Obtém ou define a ID da mensagem para a qual esta mensagem é uma resposta. |
|`value.commandId` | Contém a ID do comando que foi invocado. |
|`value.commandContext` | O contexto que disparou o evento. Deve `compose` ser. |
|`value.context.theme` | O tema do cliente do usuário, útil para formatação de exibição da Web incorporada. Deve ser `default` , `contrast` ou `dark` . |

### <a name="payload-activity-properties-when-invoked-a-task-module-from-a-channel-new-post-are-listed-in-the-following-section"></a>As propriedades de atividade de carga quando invocado um módulo de tarefa de um canal (nova postagem) são listadas na seção a seguir:

|Nome da propriedade|Finalidade|
|---|---|
|`type`| Tipo de solicitação. Deve `invoke` ser. |
|`name`| Tipo de comando emitido para o serviço. Deve `composeExtension/fetchTask` ser. |
|`from.id`| ID do usuário que enviou a solicitação. |
|`from.name`| Nome do usuário que enviou a solicitação. |
|`from.aadObjectId`| Azure Active Directory object id of the user that sent the request. |
|`channelData.tenant.id`| Locatário do Azure Active Directory. |
|`channelData.channel.id`| ID do canal (se a solicitação foi feita em um canal). |
|`channelData.team.id`| ID da equipe (se a solicitação foi feita em um canal). |
|`channelData.source.name`| O nome de origem do qual o módulo de tarefa é invocado. |
|`ChannelData.legacy. replyToId`| Obtém ou define a ID da mensagem para a qual esta mensagem é uma resposta. |
|`value.commandId` | Contém a ID do comando que foi invocado. |
|`value.commandContext` | O contexto que disparou o evento. Deve `compose` ser. |
|`value.context.theme` | O tema do cliente do usuário, útil para formatação de exibição da Web incorporada. Deve ser `default` , `contrast` ou `dark` . |

### <a name="payload-activity-properties-when-invoked-a-task-module-from-a-channel-reply-to-thread-are-listed-in-the-following-section"></a>As propriedades de atividade de carga quando invocadas um módulo de tarefa de um canal (responder a thread) estão listadas na seção a seguir:

|Nome da propriedade|Finalidade|
|---|---|
|`type`| Tipo de solicitação. Deve `invoke` ser. |
|`name`| Tipo de comando emitido para o serviço. Deve `composeExtension/fetchTask` ser. |
|`from.id`| ID do usuário que enviou a solicitação. |
|`from.name`| Nome do usuário que enviou a solicitação. |
|`from.aadObjectId`| Azure Active Directory object id of the user that sent the request. |
|`channelData.tenant.id`| Locatário do Azure Active Directory. |
|`channelData.channel.id`| ID do canal (se a solicitação foi feita em um canal). |
|`channelData.team.id`| ID da equipe (se a solicitação foi feita em um canal). |
|`channelData.source.name`| O nome de origem do qual o módulo de tarefa é invocado. |
|`ChannelData.legacy. replyToId`| Obtém ou define a ID da mensagem para a qual esta mensagem é uma resposta. |
|`value.commandId` | Contém a ID do comando que foi invocado. |
|`value.commandContext` | O contexto que disparou o evento. Deve `compose` ser. |
|`value.context.theme` | O tema do cliente do usuário, útil para formatação de exibição da Web incorporada. Deve ser `default` `contrast` `dark` ou. |

### <a name="payload-activity-properties-when-invoked-a-task-module-from-a-command-box-are-listed-in-the-following-section"></a>As propriedades de atividade de carga quando invocado um módulo de tarefa de uma caixa de comando são listadas na seção a seguir:

|Nome da propriedade|Finalidade|
|---|---|
|`type`| Tipo de solicitação. Deve `invoke` ser. |
|`name`| Tipo de comando emitido para o serviço. Deve `composeExtension/fetchTask` ser. |
|`from.id`| ID do usuário que enviou a solicitação. |
|`from.name`| Nome do usuário que enviou a solicitação. |
|`from.aadObjectId`| Azure Active Directory object id of the user that sent the request. |
|`channelData.tenant.id`| Locatário do Azure Active Directory. |
|`channelData.source.name`| O nome de origem do qual o módulo de tarefa é invocado. |
|`value.commandId` | Contém a ID do comando que foi invocado. |
|`value.commandContext` | O contexto que disparou o evento. Deve `compose` ser. |
|`value.context.theme` | O tema do cliente do usuário, útil para formatação de exibição da Web incorporada. Deve ser `default` , `contrast` ou `dark` . |

### <a name="example-fetchtask-request"></a>Exemplo de solicitação fetchTask

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

Quando seu bot é invocado a partir de uma mensagem em vez da área de composição ou da barra de comandos, o objeto na solicitação inicial deve conter os detalhes da mensagem da sua extensão de mensagens é `value` invocada. Consulte a seção a seguir para ver o exemplo deste objeto. The `reactions` and `mentions` arrays are optional, and they are not present if there are no reação or mentions in the original message.

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

## <a name="respond-to-the-fetchtask"></a>Responder à fetchTask

Responda à solicitação de invocação com um objeto que contém um objeto com o cartão adaptável ou a URL da Web ou uma mensagem de cadeia `task` `taskInfo` de caracteres simples.

|Nome da propriedade|Finalidade|
|---|---|
|`type`| Pode ser `continue` para apresentar um formulário ou para um `message` pop-up simples. |
|`value`| Um `taskInfo` objeto para um formulário ou um `string` para uma mensagem. |

O esquema do objeto taskInfo é:

|Nome da propriedade|Finalidade|
|---|---|
|`title`| O título do módulo de tarefa.|
|`height`| Ele deve ser um inteiro (em pixels) ou `small` , `medium` `large` .|
|`width`| Ele deve ser um inteiro (em pixels) ou `small` , `medium` `large` .|
|`card`| O cartão adaptável definindo o formulário (se estiver usando um).
|`url`| A URL a ser aberta dentro do módulo de tarefa como uma exibição da Web incorporada.|
|`fallbackUrl`| Se um cliente não suportar o recurso de módulo de tarefa, essa URL será aberta em uma guia do navegador. |

### <a name="with-an-adaptive-card"></a>Com um cartão adaptável

Ao usar um cartão adaptável, você deve responder com um `task` objeto com o objeto que contém um cartão `value` adaptável.

#### <a name="example-fetchtask-response-with-an-adaptive-card"></a>Exemplo de resposta fetchTask com um cartão adaptável

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

Este exemplo usa o [pacote NuGet AdaptiveCards,](https://www.nuget.org/packages/AdaptiveCards) além do SDK do Bot Framework.

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

### <a name="with-an-embedded-web-view"></a>Com uma exibição da Web incorporada

Ao usar uma exibição da Web incorporada, você deve responder com um objeto com o objeto que contém a URL para o formulário da Web que `task` `value` você gostaria de carregar. Os domínios de qualquer URL que você deseja carregar devem ser incluídos na `validDomains` matriz no manifesto do aplicativo. Consulte a [documentação do módulo de tarefas](~/task-modules-and-cards/what-are-task-modules.md) para obter informações completas sobre como criar seu visualização da Web incorporada.

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

Se o aplicativo contiver um bot de conversa, instale o bot na conversa antes de carregar o módulo de tarefa. É útil obter contexto adicional para o módulo de tarefa. O exemplo típico para esse cenário é buscar a lista de listas para popular um controle selador de pessoas ou a lista de canais em uma equipe.

Quando a extensão de mensagens receber a invocação, verifique se o bot está instalado no `composeExtension/fetchTask` contexto atual para facilitar o fluxo. Por exemplo, verifique o fluxo com uma chamada para obter lista de lista. Se o bot não estiver instalado, retorne um Cartão Adaptável com uma ação que solicita que o usuário instale o bot. Veja a ação no exemplo a seguir. O usuário deve ter permissão para instalar os aplicativos nesse local para verificação. Se a instalação do aplicativo não for bem-sucedida, o usuário receberá uma mensagem para entrar em contato com o administrador.

#### <a name="example-of-the-response"></a>Exemplo da resposta:

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

Após a instalação, o bot recebe outra mensagem de invocação com `name = composeExtension/submitAction` e `value.data.msteams.justInTimeInstall = true` .

#### <a name="example-of-the-invoke"></a>Exemplo da invocação:

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

#### <a name="example-of-just-in-time-installation-of-app-with-adaptive-card"></a>Exemplo de instalação just-in time do aplicativo com cartão adaptável: 

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

## <a name="next-steps"></a>Próximas etapas

Se você permitir que seus usuários enviem uma resposta de volta do módulo de tarefa, deverá manipular a ação de envio.

* [Criar e responder com um módulo de tarefa](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]
