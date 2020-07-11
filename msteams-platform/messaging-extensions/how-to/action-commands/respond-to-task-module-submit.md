---
title: Responder à ação de envio do módulo de tarefa
author: clearab
description: Descreve como responder à ação enviar do módulo de tarefa a partir de um comando de ação de extensão de mensagens
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: a876275f5f4f9c3a7c1fea275eecb9c26b780fd0
ms.sourcegitcommit: 3ba5a5a7d9d9d906abc3ee1df9c2177de0cfd767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2020
ms.locfileid: "45103009"
---
# <a name="respond-to-the-task-module-submit-action"></a>Responder à ação de envio do módulo de tarefa

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Quando um usuário envia o módulo de tarefa, seu serviço Web receberá uma `composeExtension/submitAction` mensagem de invocação com os valores de ID de comando e de parâmetro definidos. Seu aplicativo terá cinco segundos para responder à invocação, caso contrário, o usuário receberá uma mensagem de erro "não é possível acessar o aplicativo" e qualquer resposta à invocação será ignorada pelo cliente do teams.

Você tem as seguintes opções para responder.

* Sem resposta-você pode optar por usar a ação enviar para acionar um processo em um sistema externo e não fornecer nenhum feedback para o usuário. Isso pode ser útil para processos de execução longa, e você pode optar por fornecer comentários de outra maneira (por exemplo, com uma [mensagem proativa](~/bots/how-to/conversations/send-proactive-messages.md).
* [Outro módulo de tarefa](#respond-with-another-task-module) : você pode responder com um módulo de tarefa adicional como parte de uma interação de várias etapas.
* [Resposta do cartão](#respond-with-a-card-inserted-into-the-compose-message-area) -você pode responder com um cartão em que o usuário pode interagir e/ou inserir em uma mensagem.
* [Cartão adaptável do bot](#bot-response-with-adaptive-card) -Insira um cartão adaptável diretamente na conversa.
* [Solicitar que o usuário autentique](~/messaging-extensions/how-to/add-authentication.md)
* [Solicitar que o usuário forneça configuração adicional](~/messaging-extensions/how-to/add-configuration-page.md)

A tabela abaixo mostra quais tipos de respostas estão disponíveis com base no local de invocação ( `commandContext` ) da extensão de mensagens. Para autenticação ou configuração, depois que o usuário concluir o fluxo, a chamada original será reenviada ao seu serviço Web.

|Tipo de resposta | Redação | barra de comandos | message |
|--------------|:-------------:|:-------------:|:---------:|
|Resposta de cartão | x | x | x |
|Outro módulo de tarefa | x | x | x |
|Bot com cartão adaptável | x |  | x |
| Nenhuma resposta | x | x | x |

## <a name="the-submitaction-invoke-event"></a>O evento de chamar enviaraction

Veja a seguir alguns exemplos de como receber a mensagem Invoke.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionSubmitActionAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken) {
  //code to handle the submit action
}
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  constructor() {
  handleTeamsMessagingExtensionSubmitAction(context, action) {
  
  //code to handle the submit action
    }
  }
}
```

# <a name="json"></a>[JSON](#tab/json)

Este é um exemplo do objeto JSON que você receberá. O `commandContext` parâmetro indica onde sua extensão de mensagens foi disparada. O `data` objeto contém os campos no formulário como parâmetros e os valores que o usuário enviou. O objeto JSON aqui é reduzido para realçar os campos mais relevantes.

```json
{
  "name": "composeExtension/submitAction",
  "imdisplayname": "Bob Smith",
  "serviceUrl": "https://smba.trafficmanager.net/amer/",
  "value": {
    "commandId": "giveKudos",
    "commandContext": "compose",
    "context": {
      "theme": "default"
    },
    "data": {
      "id": "submitButton",
      "formField1": "formField1_value",
      "formField2": "formField2_value",
      "formField3": "formField3_value"
    }
  },
  "conversation": {
    "id": "19:7705841b240044b297123ad7f9c99217@thread.skype"
  }
}
```

* * *

## <a name="respond-with-a-card-inserted-into-the-compose-message-area"></a>Responder com um cartão inserido na área de mensagem de composição

A maneira mais comum de responder à `composeExtension/submitAction` solicitação é com um cartão inserido na área de mensagem de composição. O usuário pode então optar por enviar o cartão para a conversa. Para obter mais informações sobre o uso de cartões [, consulte cartões e ações de cartão](~/task-modules-and-cards/cards/cards-actions.md).

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionSubmitActionAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
    dynamic Data = JObject.Parse(action.Data.ToString());
    var response = new MessagingExtensionActionResponse
    {
        ComposeExtension = new MessagingExtensionResult
        {
            AttachmentLayout = "list",
            Type = "result",
        },
    };
    var card = new HeroCard
    {
        Title = Data["formField1"] as string,
        Subtitle = Data["formField2"]  as string,
        Text = Data["formField3"]  as string,
    };

    var attachments = new List<MessagingExtensionAttachment>();
    attachments.Add(new MessagingExtensionAttachment
    {
        Content = card,
        ContentType = HeroCard.ContentType,
        Preview = card.ToAttachment(),
    });

    response.ComposeExtension.Attachments = attachments;

    return response;

}
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  handleTeamsMessagingExtensionSubmitAction(context, action) {
    const data = action.data;
    const heroCard = CardFactory.heroCard(data.title, data.text);
    heroCard.content.subtitle = data.subTitle;
    const attachment = { contentType: heroCard.contentType, content: heroCard.content, preview: heroCard };

    return {
      composeExtension: {
        type: 'result',
        attachmentLayout: 'list',
        attachments: [
          attachment
        ]
      }
    }
  }
}
```

# <a name="json"></a>[JSON](#tab/json)

```json
{
  "composeExtension": {
    "attachmentLayout": "list",
    "type": "result",
    "attachments": [
      {
        "preview": {
          "contentType": "application/vnd.microsoft.card.hero",
          "content": {
            "title": "formField1_value",
            "subtitle": "formField2_value",
            "text": "formField3_value"
          }
        },
        "contentType": "application/vnd.microsoft.card.hero",
        "content": {
          "title": "formField1_value",
          "subtitle": "formField2_value",
          "text": "formField3_value"
        }
      }
    ]
  }
}
```

* * *

## <a name="respond-with-another-task-module"></a>Responder com outro módulo de tarefa

Você pode optar por responder ao `submitAction` evento com um módulo de tarefa adicional. Isso pode ser útil quando:

* Você precisa coletar grandes quantidades de informações.
* Se você precisar alterar dinamicamente quais informações você está coletando com base na entrada do usuário
* Se você precisar validar as informações enviadas pelo usuário e, potencialmente, reenviar o formulário com uma mensagem de erro, se houver algum problema. 

O método de resposta é o mesmo que [responder ao `fetchTask` evento inicial](~/messaging-extensions/how-to/action-commands/create-task-module.md). Se você estiver usando o SDK da estrutura de bot, o mesmo evento será disparado para as duas ações de envio. Isso significa que você precisa certificar-se de adicionar lógica que determina a resposta correta.

## <a name="bot-response-with-adaptive-card"></a>Resposta de bot com cartão adaptável

>[!Note]
>Esse fluxo requer que você adicione o `bot` objeto ao manifesto do seu aplicativo e que você tenha o escopo necessário definido para o bot. Use a mesma ID que sua extensão de mensagens para o bot.

Você também pode responder à ação de envio inserindo uma mensagem com um cartão adaptável no canal com um bot. O usuário poderá visualizar a mensagem antes de enviá-la e potencialmente editar/interagir com ela também. Isso pode ser muito útil em cenários em que você precisa coletar informações de seus usuários antes de criar uma resposta de cartão adaptável ou quando precisar atualizar o cartão após alguém interagir com ele. O cenário a seguir mostra como o aplicativo Polly usa esse fluxo para configurar uma pesquisa sem incluir as etapas de configuração na conversa do canal.

1. O usuário clica na extensão de mensagens para disparar o módulo de tarefa.
2. O usuário configura a pesquisa com o módulo de tarefa.
3. Depois de enviar o módulo de tarefa, o aplicativo usa as informações fornecidas para compilar a pesquisa como um cartão adaptável e a envia como `botMessagePreview` resposta ao cliente.
4. O usuário pode visualizar a mensagem de cartão adaptável antes do bot inseri-la no canal. Se o aplicativo ainda não for um membro do canal, clique em `Send` adicionará a ele.
   1. O usuário também pode escolher a `Edit` mensagem, que as retorna para o módulo de tarefa original.
5. Interagir com o cartão adaptável altera a mensagem antes de enviá-la.
6. Quando o usuário clica `Send` no bot envia a mensagem para o canal.

### <a name="respond-to-initial-submit-action"></a>Responder à ação de envio inicial

Para habilitar esse fluxo, seu módulo de tarefa deve responder à `composeExtension/submitAction` mensagem inicial com uma visualização do cartão que o bot enviará ao canal. Isso dá ao usuário a oportunidade de verificar o cartão antes de enviá-lo e também tentará instalar o bot na conversa se ele ainda não estiver instalado.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionSubmitActionAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  dynamic Data = JObject.Parse(action.Data.ToString());
  var response = new MessagingExtensionActionResponse
  {
    ComposeExtension = new MessagingExtensionResult
    {
      Type = "botMessagePreview",
      ActivityPreview = MessageFactory.Attachment(new Attachment
      {
        Content = new AdaptiveCard("1.0")
        {
          Body = new List<AdaptiveElement>()
          {
            new AdaptiveTextBlock() { Text = "FormField1 value was:", Size = AdaptiveTextSize.Large },
            new AdaptiveTextBlock() { Text = Data["FormField1"] as string }
          },
          Height = AdaptiveHeight.Auto,
          Actions = new List<AdaptiveAction>()
          {
            new AdaptiveSubmitAction
            {
              Type = AdaptiveSubmitAction.TypeName,
              Title = "Submit",
              Data = new JObject { { "submitLocation", "messagingExtensionFetchTask" } },
            },
          }
        },
        ContentType = AdaptiveCard.ContentType
      }) as Activity
    }
  };

  return response;
}
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  handleTeamsMessagingExtensionSubmitAction(context, action) {
    const submittedData = action.data;
    const adaptiveCard = CardFactory.adaptiveCard({
      actions: [
        { type: 'Action.Submit', title: 'Submit', data: { submitLocation: 'messagingExtensionSubmit' } }
      ],
      body: [
          { text: 'Adaptive Card from Task Module', type: 'TextBlock', weight: 'bolder' },
          { text: `${ submittedData.Question }`, type: 'TextBlock', id: 'Question' },
          { id: 'Answer', placeholder: 'Answer here...', type: 'Input.Text' },
        {
          choices: [
            { title: submittedData.Option1, value: submittedData.Option1 },
            { title: submittedData.Option2, value: submittedData.Option2 },
            { title: submittedData.Option3, value: submittedData.Option3 }
          ],
          id: 'Choices',
          isMultiSelect: submittedData.MultiSelect,
          style: 'expanded',
          type: 'Input.ChoiceSet'
        }
      ],
      type: 'AdaptiveCard',
      version: '1.0'
    });
    return {
      composeExtension: {
        activityPreview: MessageFactory.attachment(adaptiveCard, null, null, InputHints.ExpectingInput),
        type: 'botMessagePreview'
      }
    };
  }
}
```

# <a name="json"></a>[JSON](#tab/json)

>[!Note]
>O `activityPreview` deve conter uma `message` atividade com exatamente 1 anexo de cartão adaptável. O `<< Card Payload >>` valor é um espaço reservado para o cartão que você deseja enviar.

```json
{
  "composeExtension": {
    "type": "botMessagePreview",
    "activityPreview": {
      "type": "message",
      "attachments":  [
        {
          "contentType": "application/vnd.microsoft.card.adaptive",
          "content": << Card Payload >>
        }
      ]
    }
  }
}
```

* * *

### <a name="the-botmessagepreview-send-and-edit-events"></a>Eventos de envio e edição do botMessagePreview

Sua extensão de mensagem agora precisará responder a duas novas variedades da `composeExtension/submitAction` invocação, onde `value.botMessagePreviewAction = "send"` e `value.botMessagePreviewAction = "edit"` .

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionBotMessagePreviewEditAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  //handle the event
}

protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionBotMessagePreviewSendAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  //handle the event
}

```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  handleTeamsMessagingExtensionBotMessagePreviewEdit(context, action) {

    //handle the event
  }
  
  handleTeamsMessagingExtensionBotMessagePreviewSend(context, action) {

    //handle the event
  }
}

```

# <a name="json"></a>[JSON](#tab/json)

```json
{
  "name": "composeExtension/submitAction",
  "type": "invoke",
  "conversation": { "id": "19:c366b75791784100b6e8b515fd55b063@thread.skype" },
  "imdisplayname": "Pranav Smith",
  ...
  "value": {
    "botMessagePreviewAction": "edit | send",
    "botActivityPreview": [
      {
        "type": "message/card",
        "attachments": [
          {
            "content":
              {
                "type": "AdaptiveCard",
                "body": [{<<card payload>>}]
              },
            "contentType" : "application/vnd.microsoft.card.adaptive"
          }
        ],
        "context": { "theme": "default" }
      }
    ],
  }
}
```

* * *

### <a name="respond-to-botmessagepreview-edit"></a>Responder à edição do botMessagePreview

Se o usuário decidir editar o cartão antes de enviá-lo clicando no botão **Editar** , você receberá uma `composeExtension/submitAction` chamada `value.botMessagePreviewAction = edit` . Normalmente, você deve responder retornando o módulo de tarefa enviado em resposta à `composeExtension/fetchTask` chamada inicial que iniciou a interação. Isso permite que o usuário inicie o processo, inserindo novamente as informações originais. Você também deve considerar o uso das informações que agora estão disponíveis para preencher previamente o módulo de tarefa, para que o usuário não tenha preenchido todas as informações do zero.

Confira [responder ao `fetchTask` evento inicial](~/messaging-extensions/how-to/action-commands/create-task-module.md).

### <a name="respond-to-botmessagepreview-send"></a>Responder a botMessagePreview enviar

Quando o usuário clicar no botão **Enviar** , você receberá uma `composeExtension/submitAction` chamada com `value.botMessagePreviewAction = send` . Seu serviço Web precisará criar e enviar uma mensagem proativa com o cartão adaptável à conversa e também responder à invocação.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionBotMessagePreviewSendAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  var activityPreview = action.BotActivityPreview[0];
  var attachmentContent = activityPreview.Attachments[0].Content;
  var previewedCard = JsonConvert.DeserializeObject<AdaptiveCard>(attachmentContent.ToString(),
          new JsonSerializerSettings { NullValueHandling = NullValueHandling.Ignore });
  
  previewedCard.Version = "1.0";

  var responseActivity = Activity.CreateMessageActivity();
  Attachment attachment = new Attachment()
  {
    ContentType = AdaptiveCard.ContentType,
    Content = previewedCard
  };
  responseActivity.Attachments.Add(attachment);
  
  // Attribute the message to the user on whose behalf the bot is posting
  responseActivity.ChannelData = new {
    OnBehalfOf = new []
    {
      new
      {
        ItemId = 0,
        MentionType = "person",
        Mri = turnContext.Activity.From.Id,
        DisplayName = turnContext.Activity.From.Name
      }  
    }
  };
  
  await turnContext.SendActivityAsync(responseActivity);

  return new MessagingExtensionActionResponse();
}
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
    async handleTeamsMessagingExtensionBotMessagePreviewSend(context, action) {
      // The data has been returned to the bot in the action structure.
      const activityPreview = action.botActivityPreview[0];
      const attachmentContent = activityPreview.attachments[0].content;
      const userText = attachmentContent.body[1].text;
      const choiceSet = attachmentContent.body[3];

      const submitData = {
        MultiSelect: choiceSet.isMultiSelect ? 'true' : 'false',
        Option1: choiceSet.choices[0].title,
        Option2: choiceSet.choices[1].title,
        Option3: choiceSet.choices[2].title,
        Question: userText
      };

      const adaptiveCard = CardFactory.adaptiveCard({
        actions: [
          { type: 'Action.Submit', title: 'Submit', data: { submitLocation: 'messagingExtensionSubmit' } }
        ],
        body: [
          { text: 'Adaptive Card from Task Module', type: 'TextBlock', weight: 'bolder' },
          { text: `${ submitData.Question }`, type: 'TextBlock', id: 'Question' },
          { id: 'Answer', placeholder: 'Answer here...', type: 'Input.Text' },
          {
            choices: [
                { title: submitData.Option1, value: submitData.Option1 },
                { title: submitData.Option2, value: submitData.Option2 },
                { title: submitData.Option3, value: submitData.Option3 }
            ],
            id: 'Choices',
            isMultiSelect: submitData.MultiSelect,
            style: 'expanded',
            type: 'Input.ChoiceSet'
          }
        ],
        type: 'AdaptiveCard',
        version: '1.0'
      });
      const responseActivity = { type: 'message', attachments: [adaptiveCard], channelData: {
          onBehalfOf: [
              { itemId: 0, mentionType: 'person', mri: context.activity.from.id, displayname: context.activity.from.name }
          ]
      }};

      await context.sendActivity(responseActivity);
    }
}
```

# <a name="json"></a>[JSON](#tab/json)

Você receberá uma nova `composeExtension/submitAction` mensagem semelhante à seguinte.

```json
{
  "name": "composeExtension/submitAction",
  "type": "invoke",
  "conversation": { "id": "19:c366b75791784100b6e8b515fd55b063@thread.skype" },
  "imdisplayname": "Pranav Smith",
  ...
  "value": {
    "botMessagePreviewAction": "send",
    "botActivityPreview": [
      {
        "type": "message/card",
        "attachments": [
          {
            "content":
              {
                "type": "AdaptiveCard",
                "body": [{<<card payload>>}]
              },
            "contentType" : "application/vnd.microsoft.card.adaptive"
          }
        ],
        "context": { "theme": "default" }
      }
    ],
  }
}
```

* * *

### <a name="user-attribution-for-bots-messages"></a>Atribuição de usuário para mensagens de bots 

Em cenários em que um bot envia mensagens em nome de um usuário, a atribuição da mensagem a esse usuário pode ajudar no contrato e apresentar um fluxo de interação mais natural. Este recurso permite que você envie mensagens em nome do usuário que está iniciando a mensagem.

Na imagem abaixo, à esquerda está uma mensagem de cartão enviada por um bot *sem* a atribuição de usuário e à direita é um cartão enviado por um bot *com* atribuição de usuário.

![Captura de tela](../../../assets/images/messaging-extension/user-attribution-bots.png)

Para usar a atribuição de usuário no Teams, você precisa adicionar a `OnBehalfOf` entidade menção à `ChannelData` sua `Activity` carga que é enviada ao Teams.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet-1)

```csharp
    OnBehalfOf = new []
    {
      new
      {
        ItemId = 0,
        MentionType = "person",
        Mri = turnContext.Activity.From.Id,
        DisplayName = turnContext.Activity.From.Name
      }  
    }

```

# <a name="json"></a>[JSON](#tab/json-1)

```json
{
    "text": "Hello World!",
    "ChannelData": {
        "OnBehalfOf": [{
            "itemid": 0,
            "mentionType": "person",
            "mri": "29:orgid:89e6508d-6c0f-4ffe-9f6a-b58416d965ae",
            "displayName": "Sowrabh N R S"
        }]
    }
}
```

* * *

Veja a seguir uma descrição das entidades na `OnBehalfOf` matriz:

#### <a name="details-of--onbehalfof-entity-schema"></a>Detalhes do `OnBehalfOf` esquema de entidade

|Campo|Tipo|Descrição|
|:---|:---|:---|
|`itemId`|Número inteiro|Deve ser 0|
|`mentionType`|Cadeia de caracteres|Deve ser "Person"|
|`mri`|Cadeia de caracteres|Identificador de recurso de mensagem (MRI) da pessoa em cujo nome a mensagem foi enviada. O nome do remetente da mensagem apareceria como " \<user\> via \<bot name\> ".|
|`displayName`|Cadeia de caracteres|Nome da pessoa. Usado como fallback em caso de resolução de nome não está disponível.|
  
## <a name="next-steps"></a>Próximas etapas

Adicionar um comando de pesquisa

* [Definir comandos de pesquisa](~/messaging-extensions/how-to/search-commands/define-search-command.md)

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]
