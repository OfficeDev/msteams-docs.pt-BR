---
title: Criar e enviar o módulo de tarefa
author: clearab
description: Como lidar com a ação de chamada inicial e responder com um módulo de tarefa a partir de um comando Action Message Extension
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: f5f96e71517d45f52d17d2d70c583ec1eec3babd
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672769"
---
# <a name="create-and-send-the-task-module"></a><span data-ttu-id="fe543-103">Criar e enviar o módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="fe543-103">Create and send the task module</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

<span data-ttu-id="fe543-104">Se você não estiver preenchendo o módulo de tarefa com parâmetros definidos em seu manifesto de aplicativo, será necessário criar o módulo de tarefa a ser apresentado aos seus usuários.</span><span class="sxs-lookup"><span data-stu-id="fe543-104">If you are not populating your task module with parameters defined in your app manifest, you'll need to create the task module to be presented to your users.</span></span> <span data-ttu-id="fe543-105">Você pode usar um cartão adaptável ou um modo de exibição da Web incorporado.</span><span class="sxs-lookup"><span data-stu-id="fe543-105">You can use either an Adaptive Card or an embedded web view.</span></span>

## <a name="the-initial-invoke-request"></a><span data-ttu-id="fe543-106">A solicitação de chamada inicial</span><span class="sxs-lookup"><span data-stu-id="fe543-106">The initial invoke request</span></span>

<span data-ttu-id="fe543-107">O uso desse método o serviço receberá `Activity` um objeto do `composeExtension/fetchTask`tipo, e você precisará responder com um `task` objeto que contém o cartão adaptável ou uma URL para o modo de exibição da Web incorporado.</span><span class="sxs-lookup"><span data-stu-id="fe543-107">Using this method you service will receive an `Activity` object of type `composeExtension/fetchTask`, and you'll need to respond with a `task` object containing either the adaptive card or a URL to the embedded web view.</span></span> <span data-ttu-id="fe543-108">Além das propriedades de atividade de bot padrão, o payload de chamada inicial contém os seguintes metadados de solicitação:</span><span class="sxs-lookup"><span data-stu-id="fe543-108">In addition to the standard bot activity properties, the initial invoke payload contains the following request metadata:</span></span>

|<span data-ttu-id="fe543-109">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="fe543-109">Property name</span></span>|<span data-ttu-id="fe543-110">Finalidade</span><span class="sxs-lookup"><span data-stu-id="fe543-110">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="fe543-111">Tipo de solicitação; deve ser `invoke`.</span><span class="sxs-lookup"><span data-stu-id="fe543-111">Type of request; must be `invoke`.</span></span> |
|`name`| <span data-ttu-id="fe543-112">Tipo de comando que é emitido para o serviço.</span><span class="sxs-lookup"><span data-stu-id="fe543-112">Type of command that is issued to your service.</span></span> <span data-ttu-id="fe543-113">Será `composeExtension/fetchTask`.</span><span class="sxs-lookup"><span data-stu-id="fe543-113">Will be `composeExtension/fetchTask`.</span></span> |
|`from.id`| <span data-ttu-id="fe543-114">ID do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="fe543-114">ID of the user that sent the request.</span></span> |
|`from.name`| <span data-ttu-id="fe543-115">Nome do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="fe543-115">Name of the user that sent the request.</span></span> |
|`from.aadObjectId`| <span data-ttu-id="fe543-116">ID de objeto do Azure Active Directory do usuário que enviou a solicitação.</span><span class="sxs-lookup"><span data-stu-id="fe543-116">Azure Active Directory object id of the user that sent the request.</span></span> |
|`channelData.tenant.id`| <span data-ttu-id="fe543-117">Locatário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="fe543-117">Azure Active Directory tenant ID.</span></span> |
|`channelData.channel.id`| <span data-ttu-id="fe543-118">ID do canal (se a solicitação tiver sido feita em um canal).</span><span class="sxs-lookup"><span data-stu-id="fe543-118">Channel ID (if the request was made in a channel).</span></span> |
|`channelData.team.id`| <span data-ttu-id="fe543-119">ID da equipe (se a solicitação tiver sido feita em um canal).</span><span class="sxs-lookup"><span data-stu-id="fe543-119">Team ID (if the request was made in a channel).</span></span> |
|`value.commandId` | <span data-ttu-id="fe543-120">Contém a ID do comando que foi invocado.</span><span class="sxs-lookup"><span data-stu-id="fe543-120">Contains the Id of the command that was invoked.</span></span> |
|`value.commandContext` | <span data-ttu-id="fe543-121">O contexto que disparou o evento.</span><span class="sxs-lookup"><span data-stu-id="fe543-121">The context that triggered the event.</span></span> <span data-ttu-id="fe543-122">Será `compose`.</span><span class="sxs-lookup"><span data-stu-id="fe543-122">Will be `compose`.</span></span> |
|`value.context.theme` | <span data-ttu-id="fe543-123">O tema do cliente do usuário, útil para a formatação de exibição da Web incorporada.</span><span class="sxs-lookup"><span data-stu-id="fe543-123">The user's client theme, useful for embedded web view formatting.</span></span> <span data-ttu-id="fe543-124">`default`Será `contrast` ou `dark`.</span><span class="sxs-lookup"><span data-stu-id="fe543-124">Will be `default`, `contrast` or `dark`.</span></span> |

### <a name="example-fetchtask-request"></a><span data-ttu-id="fe543-125">Exemplo de solicitação fetchTask</span><span class="sxs-lookup"><span data-stu-id="fe543-125">Example fetchTask request</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="fe543-126">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="fe543-126">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  //handle fetch task
}
```

# <a name="javascriptnodejstabjavascript"></a>[<span data-ttu-id="fe543-127">JavaScript/node. js</span><span class="sxs-lookup"><span data-stu-id="fe543-127">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreviewBot extends TeamsActivityHandler {
  handleTeamsMessagingExtensionFetchTask(context, action) {
    //hand fetch task
  }
}
```

# <a name="jsontabjson"></a>[<span data-ttu-id="fe543-128">JSON</span><span class="sxs-lookup"><span data-stu-id="fe543-128">JSON</span></span>](#tab/json)

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

## <a name="initial-invoke-request-from-a-message"></a><span data-ttu-id="fe543-129">Solicitação de chamada inicial de uma mensagem</span><span class="sxs-lookup"><span data-stu-id="fe543-129">Initial invoke request from a message</span></span>

<span data-ttu-id="fe543-130">Quando o bot for invocado de uma mensagem em vez da área de redação ou da barra de `value` comandos, o objeto na solicitação inicial conterá os detalhes da mensagem que sua extensão de mensagens foi invocada.</span><span class="sxs-lookup"><span data-stu-id="fe543-130">When your bot is invoked from a message rather than the compose area or the command bar, the `value` object in the initial request will contain the details of the message your messaging extension was invoked from.</span></span> <span data-ttu-id="fe543-131">Um exemplo deste objeto está abaixo.</span><span class="sxs-lookup"><span data-stu-id="fe543-131">An example of this object is below.</span></span> <span data-ttu-id="fe543-132">Os `reactions` arrays e `mentions` são opcionais e não estarão presentes se não houver nenhuma reações ou menção na mensagem original.</span><span class="sxs-lookup"><span data-stu-id="fe543-132">The `reactions` and `mentions` arrays are optional, and will not be present if there are no reactions or mentions in the original message.</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="fe543-133">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="fe543-133">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  var messageText = action.MessagePayload.Body.Content;
  var fromId = action.MessagePayload.From.User.Id;

  //finish handling the fetchTask
}
```

# <a name="javascriptnodejstabjavascript"></a>[<span data-ttu-id="fe543-134">JavaScript/node. js</span><span class="sxs-lookup"><span data-stu-id="fe543-134">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  handleTeamsMessagingExtensionFetchTask(context, action) {
    const messageText = action.messagePayload.body.content;

    //finish handling the fetchTask
  }
}
```

# <a name="jsontabjson"></a>[<span data-ttu-id="fe543-135">JSON</span><span class="sxs-lookup"><span data-stu-id="fe543-135">JSON</span></span>](#tab/json)

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

## <a name="respond-to-the-fetchtask"></a><span data-ttu-id="fe543-136">Responder à fetchTask</span><span class="sxs-lookup"><span data-stu-id="fe543-136">Respond to the fetchTask</span></span>

<span data-ttu-id="fe543-137">Responder à solicitação Invoke com um `task` objeto que contém um `taskInfo` objeto com o cartão adaptável ou URL da Web ou uma mensagem de cadeia de caracteres simples.</span><span class="sxs-lookup"><span data-stu-id="fe543-137">Respond to the invoke request with a `task` object that contains either a `taskInfo` object with the adaptive card or web URL, or a simple string message.</span></span>

|<span data-ttu-id="fe543-138">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="fe543-138">Property name</span></span>|<span data-ttu-id="fe543-139">Finalidade</span><span class="sxs-lookup"><span data-stu-id="fe543-139">Purpose</span></span>|
|---|---|
|`type`| <span data-ttu-id="fe543-140">Pode ser `continue` para apresentar um formulário ou `message` para um pop-up simples.</span><span class="sxs-lookup"><span data-stu-id="fe543-140">Can be either `continue` to present a form, or `message` for a simple popup.</span></span> |
|`value`| <span data-ttu-id="fe543-141">Um `taskInfo` objeto de um formulário ou um `string` para uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="fe543-141">Either a `taskInfo` object for a form, or a `string` for a message.</span></span> |

<span data-ttu-id="fe543-142">O esquema para o objeto taskInfo é:</span><span class="sxs-lookup"><span data-stu-id="fe543-142">The schema for the taskInfo object is:</span></span>

|<span data-ttu-id="fe543-143">Nome da propriedade</span><span class="sxs-lookup"><span data-stu-id="fe543-143">Property name</span></span>|<span data-ttu-id="fe543-144">Finalidade</span><span class="sxs-lookup"><span data-stu-id="fe543-144">Purpose</span></span>|
|---|---|
|`title`| <span data-ttu-id="fe543-145">O título do módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="fe543-145">The title of the task module.</span></span>|
|`height`| <span data-ttu-id="fe543-146">Pode ser um número inteiro (em pixels) ou `small`, `medium`,. `large`</span><span class="sxs-lookup"><span data-stu-id="fe543-146">Can be either an integer (in pixels), or `small`, `medium`, `large`.</span></span>|
|`width`| <span data-ttu-id="fe543-147">Pode ser um número inteiro (em pixels) ou `small`, `medium`,. `large`</span><span class="sxs-lookup"><span data-stu-id="fe543-147">Can be either an integer (in pixels), or `small`, `medium`, `large`.</span></span>|
|`card`| <span data-ttu-id="fe543-148">O cartão adaptável que define o formulário (se estiver usando um).</span><span class="sxs-lookup"><span data-stu-id="fe543-148">The adaptive card defining the form (if using one).</span></span>
|`url`| <span data-ttu-id="fe543-149">A URL a ser aberta dentro do módulo de tarefa como um modo de exibição da Web incorporado.</span><span class="sxs-lookup"><span data-stu-id="fe543-149">The URL to be opened inside of the task module as an embedded web view.</span></span>|
|`fallbackUrl`| <span data-ttu-id="fe543-150">Se um cliente não oferecer suporte ao recurso do módulo de tarefa, essa URL será aberta em uma guia do navegador.</span><span class="sxs-lookup"><span data-stu-id="fe543-150">If a client does not support the task module feature, this URL is opened in a browser tab.</span></span> |

### <a name="with-an-adaptive-card"></a><span data-ttu-id="fe543-151">Com um cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="fe543-151">With an adaptive card</span></span>

<span data-ttu-id="fe543-152">Ao usar um cartão adaptável, você precisará responder com um `task` objeto com o `value` objeto que contém um cartão adaptável.</span><span class="sxs-lookup"><span data-stu-id="fe543-152">When using an adaptive card, you'll need to respond with a `task` object with the `value` object containing an adaptive card.</span></span>

#### <a name="example-fetchtask-response-with-an-adaptive-card"></a><span data-ttu-id="fe543-153">Exemplo de resposta fetchTask com um cartão adaptável</span><span class="sxs-lookup"><span data-stu-id="fe543-153">Example fetchTask response with an adaptive card</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="fe543-154">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="fe543-154">C#/.NET</span></span>](#tab/dotnet)

<span data-ttu-id="fe543-155">Este exemplo usa o [pacote NuGet do AdaptiveCards](https://www.nuget.org/packages/AdaptiveCards) além do SDK da estrutura de bot.</span><span class="sxs-lookup"><span data-stu-id="fe543-155">This sample uses the [AdaptiveCards NuGet package](https://www.nuget.org/packages/AdaptiveCards) in addition to the Bot Framework SDK.</span></span>

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

# <a name="javascriptnodejstabjavascript"></a>[<span data-ttu-id="fe543-156">JavaScript/node. js</span><span class="sxs-lookup"><span data-stu-id="fe543-156">JavaScript/Node.js</span></span>](#tab/javascript)

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

# <a name="jsontabjson"></a>[<span data-ttu-id="fe543-157">JSON</span><span class="sxs-lookup"><span data-stu-id="fe543-157">JSON</span></span>](#tab/json)

```json
{
  "task": {
    "type": "continue",
    "value": {
      "card":
      {
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
        ],
        "$schema": "http://adaptivecards.io/schemas/adaptive-card.json"
      }
    }
  }
}
```

* * *

### <a name="with-an-embedded-web-view"></a><span data-ttu-id="fe543-158">Com um modo de exibição da Web incorporado</span><span class="sxs-lookup"><span data-stu-id="fe543-158">With an embedded web view</span></span>

<span data-ttu-id="fe543-159">Ao usar um modo de exibição da Web incorporado, você precisará responder `task` com um objeto `value` com o objeto que contém a URL para o formulário da Web que você deseja carregar.</span><span class="sxs-lookup"><span data-stu-id="fe543-159">When using an embedded web view, you'll need to respond with a `task` object with the `value` object containing the URL to the web form you'd like to load.</span></span> <span data-ttu-id="fe543-160">Os domínios de qualquer URL que você deseja carregar devem ser incluídos na `validDomains` matriz no manifesto do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fe543-160">The domains of any URL you want to load must be included in the `validDomains` array in your app's manifest.</span></span> <span data-ttu-id="fe543-161">Confira a [documentação do módulo de tarefas](~/task-modules-and-cards/what-are-task-modules.md) para obter informações completas sobre como criar o modo de exibição da Web incorporado.</span><span class="sxs-lookup"><span data-stu-id="fe543-161">See the [task module documentation](~/task-modules-and-cards/what-are-task-modules.md) for complete information on building your embedded web view.</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="fe543-162">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="fe543-162">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="javascriptnodejstabjavascript"></a>[<span data-ttu-id="fe543-163">JavaScript/node. js</span><span class="sxs-lookup"><span data-stu-id="fe543-163">JavaScript/Node.js</span></span>](#tab/javascript)

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

# <a name="jsontabjson"></a>[<span data-ttu-id="fe543-164">JSON</span><span class="sxs-lookup"><span data-stu-id="fe543-164">JSON</span></span>](#tab/json)

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

## <a name="next-steps"></a><span data-ttu-id="fe543-165">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="fe543-165">Next steps</span></span>

<span data-ttu-id="fe543-166">Se você permitir que os usuários enviem uma resposta do módulo de tarefa, você precisará lidar com a ação de envio.</span><span class="sxs-lookup"><span data-stu-id="fe543-166">If you allow your users to send a response back from the task module, you'll need to handle the submit action.</span></span>

* [<span data-ttu-id="fe543-167">Criar e responder com um módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="fe543-167">Create and respond with a task module</span></span>](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]
