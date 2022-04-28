---
title: Responder à ação de envio do módulo de tarefas
author: surbhigupta
description: Descreve como responder à ação de envio do módulo de tarefa de um comando de ação de extensão de mensagem com mensagem proativa, outro módulo de tarefa, bot de cartão adaptável e muito mais usando exemplos de código.
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 4cd42fec6209b79a43ba6cc7489d5ac9afea3759
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65104473"
---
# <a name="respond-to-the-task-module-submit-action"></a>Responder à ação de envio do módulo de tarefas

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Este documento orienta você sobre como seu aplicativo responde aos comandos de ação, como a ação de envio do módulo de tarefa do usuário.
Depois que um usuário envia o módulo de tarefa, seu serviço Web recebe uma mensagem de invocação com a `composeExtension/submitAction` ID do comando e os valores de parâmetro. Seu aplicativo tem cinco segundos para responder à invocação; caso contrário, o usuário recebe uma mensagem de erro Não é possível acessar o **aplicativo e qualquer** resposta a ser invocada é ignorada pelo Teams cliente.

Você tem as seguintes opções para responder:

* Nenhuma resposta: use a ação de envio para disparar um processo em um sistema externo e não fornecer comentários ao usuário. É útil para processos de execução longa e para fornecer comentários como alternativa. Por exemplo, você pode enviar comentários com uma [mensagem proativa](~/bots/how-to/conversations/send-proactive-messages.md).
* [Outro módulo de](#respond-with-another-task-module) tarefa: você pode responder com um módulo de tarefa adicional como parte de uma interação de várias etapas.
* [Resposta do](#respond-with-a-card-inserted-into-the-compose-message-area) cartão: você pode responder com um cartão com o qual o usuário pode interagir ou inserir em uma mensagem.
* [Cartão Adaptável do bot](#bot-response-with-adaptive-card): insira um Cartão Adaptável diretamente na conversa.
* [Solicite que o usuário se autentique](~/messaging-extensions/how-to/add-authentication.md).
* [Solicite ao usuário que forneça configuração adicional](~/get-started/first-message-extension.md).

Para autenticação ou configuração, depois que o usuário concluir o processo, a invocação original será reenviada ao seu serviço Web. A tabela a seguir mostra quais tipos de respostas estão disponíveis com base no local `commandContext` de invocação da extensão de mensagem:

|Tipo de Resposta | Escrever | Barra de comandos | Mensagem |
|--------------|:-------------:|:-------------:|:---------:|
|Resposta do cartão | ✔ | ✔ | ✔ |
|Outro módulo de tarefa | ✔ | ✔ | ✔ |
|Bot com Cartão Adaptável | ✔ | x | ✔ |
| Nenhuma resposta | ✔ | ✔ | ✔ |

> [!NOTE]
>
> * Quando você seleciona **Action.Submit** por meio de cartões ME, ele envia a atividade de invocação com o nome **composeExtension**, em que o valor é igual ao conteúdo normal.
> * Ao selecionar **Action.Submit por** meio da conversa, você recebe a atividade de mensagem com o nome **onCardButtonClicked**, em que o valor é igual ao conteúdo normal.

Se o aplicativo contiver um bot de conversa, instale o bot na conversa e carregue o módulo de tarefa. O bot é útil para obter contexto adicional para o módulo de tarefa. Para instalar o bot de conversa, consulte [Solicitar para instalar o bot de conversa](create-task-module.md#request-to-install-your-conversational-bot).

## <a name="the-submitaction-invoke-event"></a>O evento de invocação submitAction

Exemplos de recebimento da mensagem de invocação são os seguintes:

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

Este é um exemplo do objeto JSON que você recebe. O `commandContext` parâmetro indica de onde a extensão de mensagem foi disparada. O `data` objeto contém os campos no formulário como parâmetros e os valores que o usuário enviou. O objeto JSON realça os campos mais relevantes.

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

A maneira mais comum de responder à solicitação `composeExtension/submitAction` é com um cartão inserido na área de mensagem de composição. O usuário envia o cartão para a conversa. Para obter mais informações sobre como usar cartões, consulte [cartões e ações de cartão](~/task-modules-and-cards/cards/cards-actions.md).

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

Você pode selecionar para responder ao evento `submitAction` com um módulo de tarefa adicional. Isso é útil quando você precisa:

* Colete grandes quantidades de informações.
* Altere dinamicamente a coleção de informações com base na entrada do usuário.
* Valide as informações enviadas pelo usuário e reenvie o formulário com uma mensagem de erro se algo estiver errado.

O método de resposta é o mesmo [que responder ao evento `fetchTask` inicial](~/messaging-extensions/how-to/action-commands/create-task-module.md). Se você estiver usando o SDK do Bot Framework, os mesmos gatilhos de evento para ambas as ações de envio. Para fazer isso funcionar, você deve adicionar uma lógica que determine a resposta correta.

## <a name="bot-response-with-adaptive-card"></a>Resposta do bot com Cartão Adaptável

> [!NOTE]
> O pré-requisito para obter a resposta do bot com um cartão adaptável `bot` é que você deve adicionar o objeto ao manifesto do aplicativo e definir o escopo necessário para o bot. Use a mesma ID da extensão de mensagem para o bot.

Você também pode responder ao inserir `submitAction` uma mensagem com um Cartão Adaptável no canal com um bot. O usuário pode visualizar a mensagem antes de enviá-la. Isso é útil em cenários em que você coleta informações dos usuários antes de criar uma resposta de Cartão Adaptável ou quando você atualiza o cartão depois que alguém interage com ele.

O cenário a seguir mostra como o aplicativo Polly configura uma votação sem incluir as etapas de configuração na conversa do canal:

Para configurar a votação:

1. O usuário seleciona a extensão de mensagem para invocar o módulo de tarefa.
1. O usuário configura a votação com o módulo de tarefa.
1. Depois de enviar o módulo de tarefa, o aplicativo usa as informações fornecidas para criar a votação como um Cartão Adaptável e a `botMessagePreview` envia como uma resposta ao cliente.
1. Em seguida, o usuário pode visualizar a mensagem cartão adaptável antes que o bot a insira no canal. Se o aplicativo não for um membro do canal, selecione para `Send` adicioná-lo.

    > [!NOTE]
    >
    > * Os usuários também podem selecionar a `Edit` mensagem, que os retorna ao módulo de tarefa original.
    > * A interação com o Cartão Adaptável altera a mensagem antes de enviá-la.
    >
1. Depois que o usuário selecionar o `Send` bot, poste a mensagem no canal.

## <a name="respond-to-initial-submit-action"></a>Responder à ação de envio inicial

O módulo de tarefa deve responder à mensagem inicial `composeExtension/submitAction` com uma visualização do cartão que o bot envia para o canal. O usuário pode verificar o cartão antes de enviar e tentar instalar o bot na conversa se o bot ainda não estiver instalado.

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

> [!NOTE]
>
> * Deve `activityPreview` conter uma atividade `message` com exatamente um anexo de Cartão Adaptável. O `<< Card Payload >>` valor é um espaço reservado para o cartão que você deseja enviar.

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

### <a name="the-botmessagepreview-send-and-edit-events"></a>O botMessagePreview envia e edita eventos

Sua extensão de mensagem deve responder a dois novos tipos de invocação `composeExtension/submitAction` , onde `value.botMessagePreviewAction = "send"`e `value.botMessagePreviewAction = "edit"`.

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

Se o usuário editar o cartão antes de enviar, selecionando **Editar**, você receberá uma invocação `composeExtension/submitAction` com `value.botMessagePreviewAction = edit`. Responda retornando o módulo de tarefa enviado, em resposta à invocação inicial `composeExtension/fetchTask` que iniciou a interação. Isso permite que o usuário inicie o processo reinstalando as informações originais. Use as informações disponíveis para atualizar o módulo de tarefa para que o usuário não precise preencher todas as informações do zero.
Para obter mais informações sobre como responder ao evento inicial `fetchTask` , consulte [responder ao evento `fetchTask` inicial](~/messaging-extensions/how-to/action-commands/create-task-module.md).

### <a name="respond-to-botmessagepreview-send"></a>Responder ao envio de botMessagePreview

Depois que o usuário selecionar **Enviar**, você receberá uma invocação `composeExtension/submitAction` com `value.botMessagePreviewAction = send`. Seu serviço Web deve criar e enviar uma mensagem proativa com o Cartão Adaptável para a conversa e também responder à invocação.

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

Em cenários em que um bot envia mensagens em nome de um usuário, atribuir a mensagem a esse usuário ajuda com o envolvimento e demonstra um fluxo de interação mais natural. Esse recurso permite atribuir uma mensagem do bot a um usuário em cujo nome ela foi enviada.

Na imagem a seguir, à esquerda está uma mensagem de cartão enviada por um bot sem atribuição do usuário e à direita está um cartão enviado por um bot com atribuição de usuário.

![bots de atribuição de usuário](../../../assets/images/messaging-extension/user-attribution-bots.png)

Para usar a atribuição de usuário nas equipes, `OnBehalfOf` `ChannelData` `Activity` você deve adicionar a entidade de menção à sua carga que é enviada para Teams.

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

#### <a name="details-of--onbehalfof-entity-schema"></a>Detalhes do  `OnBehalfOf` esquema de entidade

A seção a seguir é uma descrição das entidades na `OnBehalfOf` Matriz:

|Campo|Tipo|Descrição|
|:---|:---|:---|
|`itemId`|Inteiro|Descreve a identificação do item. Seu valor deve ser `0`.|
|`mentionType`|Cadeia de caracteres|Descreve a menção de uma "pessoa".|
|`mri`|Cadeia de caracteres|MRI (identificador de recurso de mensagem) da pessoa em cujo nome a mensagem é enviada. O nome do remetente da mensagem seria exibido como "\<user\> através \<bot name\>".|
|`displayName`|String|Nome da pessoa. Usado como fallback caso a resolução de nomes não esteja disponível.|
  
## <a name="code-sample"></a>Exemplo de código

| Nome do exemplo           | Descrição | .NET    | Node.js   |
|:---------------------|:--------------|:---------|:--------|
|Teams de extensão de mensagem| Descreve como definir comandos de ação, criar módulo de tarefa e responder à ação de envio do módulo de tarefa. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) |
|Teams de extensão de mensagem   |  Descreve como definir comandos de pesquisa e responder a pesquisas.        |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Definir comandos de pesquisa](~/messaging-extensions/how-to/search-commands/define-search-command.md)

## <a name="see-also"></a>Confira também

[Responder ao comando de pesquisa](~/messaging-extensions/how-to/search-commands/respond-to-search.md)
