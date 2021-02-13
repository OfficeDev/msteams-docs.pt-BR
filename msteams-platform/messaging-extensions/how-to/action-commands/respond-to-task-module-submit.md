---
title: Responder à ação de envio do módulo de tarefa
author: clearab
description: Descreve como responder à ação enviar do módulo de tarefa a partir de um comando de ação de extensão de mensagens
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 1fb2f2dc51d7de1208a5a913abf2d38cb80c401a
ms.sourcegitcommit: e3b6bc31059ec77de5fbef9b15c17d358abbca0f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2021
ms.locfileid: "50231642"
---
# <a name="respond-to-the-task-module-submit-action"></a>Responder à ação de envio do módulo de tarefa

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Depois que um usuário envia o módulo de tarefa, seu serviço Web recebe uma mensagem de invocação com a ID de comando e os valores `composeExtension/submitAction` de parâmetro. Seu aplicativo tem cinco segundos para responder à invocação, caso contrário, o usuário recebe uma mensagem de erro Não é possível alcançar o aplicativo *e* qualquer resposta à invocação é ignorada pelo cliente do Teams.

Você tem as seguintes opções para responder:

* Nenhuma resposta - Você pode optar por usar a ação enviar para disparar um processo em um sistema externo e não fornecer nenhum comentário ao usuário. Isso pode ser útil para processos de longa duração e você pode optar por fornecer comentários de outra maneira (por exemplo, com uma [mensagem proativa.](~/bots/how-to/conversations/send-proactive-messages.md)
* [Outro módulo de](#respond-with-another-task-module) tarefa - Você pode responder com um módulo de tarefa adicional como parte de uma interação em várias etapas.
* [Resposta do](#respond-with-a-card-inserted-into-the-compose-message-area) cartão - Você pode responder com um cartão com o que o usuário pode interagir e/ou inserir em uma mensagem.
* [Cartão adaptável do bot](#bot-response-with-adaptive-card) : insira um Cartão Adaptável diretamente na conversa.
* [Solicitar a autenticação do usuário](~/messaging-extensions/how-to/add-authentication.md)
* [Solicitar que o usuário forneça configuração adicional](~/messaging-extensions/how-to/add-configuration-page.md)

Para autenticação ou configuração, depois que o usuário concluir o fluxo, a invocação original será re-enviada ao seu serviço Web. A tabela a seguir mostra quais tipos de respostas estão disponíveis com base no local de `commandContext` invocação da extensão de mensagens: 

|Tipo de resposta | compose | barra de comandos | mensagem |
|--------------|:-------------:|:-------------:|:---------:|
|Resposta do cartão | x | x | x |
|Outro módulo de tarefa | x | x | x |
|Bot com Cartão Adaptável | x |  | x |
| Nenhuma resposta | x | x | x |

## <a name="the-submitaction-invoke-event"></a>O evento submitAction invoke

Exemplos de recebimento da mensagem de invocação são os seguinte:

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

Este é um exemplo do objeto JSON que você recebe. O `commandContext` parâmetro indica de onde a extensão de mensagens foi disparada. O `data` objeto contém os campos no formulário como parâmetros e os valores que o usuário enviou. O objeto JSON aqui é reduzido para realçar os campos mais relevantes.

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

## <a name="respond-with-a-card-inserted-into-the-compose-message-area"></a>Responder com um cartão inserido na área de mensagem de redação

A maneira mais comum de responder à `composeExtension/submitAction` solicitação é com um cartão inserido na área de mensagem de redação. Em seguida, o usuário pode optar por enviar o cartão para a conversa. Para obter mais informações sobre como usar cartões, consulte [cartões e ações de cartão.](~/task-modules-and-cards/cards/cards-actions.md)

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionSubmitActionAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
    var response = new MessagingExtensionActionResponse
    {
        ComposeExtension = new MessagingExtensionResult
        {
            AttachmentLayout = "list",
            Type = "result",
        },
    };
    var createCardData = ((JObject)action.Data).ToObject<CreateCardData>();
var card = new HeroCard
{
     Title = createCardData.Title,
     Subtitle = createCardData.Subtitle,
     Text = createCardData.Text,
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

Você pode optar por responder ao evento `submitAction` com um módulo de tarefa adicional. Isso pode ser útil quando:

* Você precisa coletar grandes quantidades de informações.
* Se você precisar alterar dinamicamente quais informações está coletando com base na entrada do usuário
* Se você precisar validar as informações enviadas pelo usuário e potencialmente reendá-lo com uma mensagem de erro se algo estiver errado. 

O método de resposta é o mesmo [que responder ao evento `fetchTask` inicial.](~/messaging-extensions/how-to/action-commands/create-task-module.md) Se você estiver usando o SDK da Estrutura de Bot, os mesmos gatilhos de evento para ambas as ações de envio. Isso significa que você deve adicionar lógica que determina a resposta correta.

## <a name="bot-response-with-adaptive-card"></a>Resposta de bot com Cartão Adaptável

>[!Note]
>Esse fluxo exige que você adicione o objeto ao manifesto do aplicativo e que tenha o `bot` escopo necessário definido para o bot. Use a mesma ID da extensão de mensagens do bot.

Você também pode responder à ação enviar inserindo uma mensagem com um Cartão Adaptável no canal com um bot. O usuário pode visualizar a mensagem antes de encaminhá-la e também pode editá-la ou interagir com ela. Isso pode ser muito útil em cenários em que você coleta informações de seus usuários antes de criar uma resposta de cartão adaptável ou quando você atualiza o cartão depois que alguém interage com ele. O cenário a seguir mostra como o aplicativo Quelinha usa esse fluxo para configurar uma sondagem sem incluir as etapas de configuração na conversa do canal:

1. O usuário seleciona a extensão de mensagens para disparar o módulo de tarefa.
2. O usuário configura a sondagem com o módulo de tarefa.
3. Depois de enviar o módulo de tarefa, o aplicativo usa as informações fornecidas para criar a sondagem como um Cartão Adaptável e envia-a como uma resposta `botMessagePreview` ao cliente.
4. Em seguida, o usuário pode visualizar a mensagem do cartão adaptável antes que o bot a insira no canal. Se o aplicativo ainda não for membro do canal, a seleção `Send` o adiciona.
   1. O usuário também pode escolher a `Edit` mensagem, que o retornará para o módulo de tarefa original.
5. Interagir com o cartão adaptável altera a mensagem antes de enviá-la.
6. Depois que o usuário seleciona `Send` o bot, posta a mensagem no canal.

### <a name="respond-to-initial-submit-action"></a>Responder à ação de envio inicial

Para habilitar esse fluxo, seu módulo de tarefa deve responder à mensagem inicial com uma visualização do cartão que o `composeExtension/submitAction` bot envia para o canal. Isso dá ao usuário a oportunidade de verificar o cartão antes de enviar e também tentar instalar seu bot na conversa se ele ainda não estiver instalado.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionSubmitActionAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  dynamic createCardData = ((JObject) action.Data).ToObject(typeof(JObject));
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
>Deve `activityPreview` conter uma atividade com exatamente `message` 1 anexo de cartão adaptável. O `<< Card Payload >>` valor é um espaço reservado para o cartão que você deseja enviar.

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

### <a name="the-botmessagepreview-send-and-edit-events"></a>Os eventos de envio e edição botMessagePreview

Sua extensão de mensagem deve responder agora a duas novas variedades da `composeExtension/submitAction` invocação, onde `value.botMessagePreviewAction = "send"` e `value.botMessagePreviewAction = "edit"` .

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

### <a name="respond-to-botmessagepreview-edit"></a>Responder à edição botMessagePreview

Se o usuário editar o cartão antes de enviar selecionando o **botão** Editar, você receberá uma `composeExtension/submitAction` invocação com `value.botMessagePreviewAction = edit` . Normalmente, você deve responder retornando o módulo de tarefa enviado em resposta à invocação inicial `composeExtension/fetchTask` que iniciou a interação. Isso permite que o usuário inicie o processo de novo inserindo as informações originais. Use as informações disponíveis para preencher previamente o módulo de tarefa para que o usuário não tenha que preencher todas as informações do zero.

Veja [respondendo ao evento `fetchTask` inicial.](~/messaging-extensions/how-to/action-commands/create-task-module.md)

### <a name="respond-to-botmessagepreview-send"></a>Responder ao envio de botMessagePreview

Depois que o usuário seleciona o **botão Enviar,** você recebe uma `composeExtension/submitAction` invocação com `value.botMessagePreviewAction = send` . Seu serviço Web precisa criar e enviar uma mensagem proativa com o Cartão Adaptável para a conversa e também responder à invocação.

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

Você recebe uma nova `composeExtension/submitAction` mensagem semelhante à seguinte:

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

### <a name="user-attribution-for-bots-messages"></a>Atribuição do usuário para mensagens de bots 

Em cenários em que um bot envia mensagens em nome de um usuário, atribuir a mensagem a esse usuário pode ajudar no envolvimento e mostrar um fluxo de interação mais natural. Esse recurso permite que você atribua uma mensagem do seu bot a um usuário em cujo nome ela foi enviada.

Na imagem a seguir, à esquerda há uma mensagem de cartão enviada por um *bot* sem atribuição do usuário e à direita está um cartão enviado por um *bot* com atribuição do usuário.

![Captura de tela](../../../assets/images/messaging-extension/user-attribution-bots.png)

Para usar a atribuição do usuário em equipes, você deve adicionar a entidade de menção à sua `OnBehalfOf` carga que é enviada para o `ChannelData` `Activity` Teams.

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

A seção a seguir é uma descrição das entidades na `OnBehalfOf` matriz:

#### <a name="details-of--onbehalfof-entity-schema"></a>Detalhes do  `OnBehalfOf` esquema de entidade

|Campo|Tipo|Descrição|
|:---|:---|:---|
|`itemId`|Inteiro|Deve ser 0|
|`mentionType`|Cadeia de caracteres|Deve ser "pessoa"|
|`mri`|Cadeia de caracteres|Identificador de recurso de mensagem (MRI) da pessoa em cujo nome a mensagem é enviada. O nome do remetente da mensagem apareceria como " \<user\> via \<bot name\> ".|
|`displayName`|Cadeia de caracteres|Nome da pessoa. Usado como fallback no caso de a resolução de nomes não estar disponível.|
  
## <a name="next-steps"></a>Próximas etapas

Adicionar um comando de pesquisa

* [Definir comandos de pesquisa](~/messaging-extensions/how-to/search-commands/define-search-command.md)

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]
