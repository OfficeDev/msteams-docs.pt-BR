---
title: Iniciar ações com extensões de mensagens
description: Criar extensões de mensagens baseadas em ação para permitir que os usuários disparem serviços externos
keywords: pesquisa de extensões de mensagens de extensões de mensagens do teams
ms.openlocfilehash: dd88360e342788fc0505809c6c8281c64fb7afbb
ms.sourcegitcommit: 0aeb60027f423d8ceff3b377db8c3efbb6da4d17
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "48997990"
---
# <a name="initiate-actions-with-messaging-extensions"></a>Iniciar ações com extensões de mensagens

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-me.md)]

As extensões de mensagens baseadas em ações permitem que os usuários disparem ações em serviços externos enquanto estão dentro do teams.

![Exemplo de cartão de extensão de mensagens](~/assets/images/compose-extensions/ceexample.png)

As seções a seguir descrevem como fazer isso.

[!include[Common content for creating extensions](~/includes/messaging-extensions/messaging-extensions-common.md)]

### <a name="action-type-message-extensions"></a>Extensões de mensagens de tipo de ação

Para iniciar ações de uma extensão de mensagens, defina o `type` parâmetro como `action` . Veja a seguir um exemplo de um manifesto com uma pesquisa e um comando criar. Uma única extensão de mensagens pode ter até 10 comandos diferentes. Isso pode incluir vários comandos de pesquisa e múltiplos baseados em ação.

#### <a name="complete-app-manifest-example"></a>Exemplo de manifesto de aplicativo completo

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  "version": "1.0",
  "id": "57a3c29f-1fc5-4d97-a142-35bb662b7b23",
  "packageName": "com.microsoft.teams.samples.Todo",
  "developer": {
    "name": "John Developer",
    "websiteUrl": "http://todobotservice.azurewebsites.net/",
    "privacyUrl": "http://todobotservice.azurewebsites.net/privacy",
    "termsOfUseUrl": "http://todobotservice.azurewebsites.net/termsofuse"
  },
  "name": {
    "short": "To Do",
    "full": "To Do"
  },
  "description": {
    "short": "Find or create a new task in To Do",
    "full": "Find or create a new task in To Do"
  },
  "icons": {
    "outline": "todo-outline.jpg",
    "color": "todo-color.jpg"
  },
  "accentColor": "#ff6a00",
  "composeExtensions": [
    {
      "botId": "57a3c29f-1fc5-4d97-a142-35bb662b7b23",
      "canUpdateConfiguration": true,
      "commands": [
        {
          "id": "searchCmd",
          "description": "Search you Todo's",
          "title": "Search",
          "initialRun": true,
          "context": ["commandBox", "compose"],
          "parameters": [
            {
              "name": "searchKeyword",
              "description": "Enter your search keywords",
              "title": "Keywords"
            }
          ]
        },
        {
          "id": "addTodo",
          "description": "Create a To Do item",
          "title": "Create To Do",
          "type": "action",
          "context": ["commandBox", "message", "compose"],
          "parameters": [
            {
              "name": "Name",
              "description": "To Do Title",
              "title": "Title",
              "inputType": "text"
            },
            {
              "name": "Description",
              "description": "Description of the task",
              "title": "Description",
              "inputType": "textarea"
            },
            {
              "name": "Date",
              "description": "Due date for the task",
              "title": "Date",
              "inputType": "date"
            }
          ]
        },
        {
          "id": "reassignTodo",
          "description": "Reassign a todo item",
          "title": "Reassign a todo item",
          "type": "action",
          "fetchTask": true,
          "parameters": [
            {
              "name": "Name",
              "title": "Title"
            }
          ]
        }
      ]
    }
  ],
  "permissions": [
    "identity",
    "messageTeamMembers"
  ],
  "validDomains": [
    "todobotservice.azurewebsites.net",
    "*.todobotservice.azurewebsites.net"
  ]
}
```

### <a name="initiate-actions-from-messages"></a>Iniciar ações de mensagens

Além de iniciar ações da área de mensagem de composição, você também pode usar sua extensão de mensagens para iniciar uma ação de uma mensagem. Isso permitirá que você envie o conteúdo da mensagem para o seu bot para processamento e, opcionalmente, responda a essa mensagem com uma resposta usando o método descrito em [responder a enviar](#responding-to-submit). A resposta será inserida como resposta à mensagem que os usuários podem editar antes de enviar. Os usuários podem acessar sua extensão de mensagens no menu de estouro `...` e, em seguida, selecionando `Take action` como na imagem abaixo.

![Exemplo de início de uma ação de uma mensagem](~/assets/images/compose-extensions/messageextensions_messageaction.png)

Para permitir que sua extensão de mensagens funcione de uma mensagem, você precisará adicionar o `context` parâmetro ao objeto da extensão de mensagens `commands` no manifesto do aplicativo, como no exemplo abaixo. As cadeias de caracteres válidas para a `context` matriz são `"message"` , `"commandBox"` e `"compose"` . O valor padrão é `["compose", "commandBox"]`. Consulte a seção [definir comandos](#define-commands) para obter detalhes completos sobre o `context` parâmetro.

```json
"composeExtensions": [
  {
    "botId": "57a3c29f-1fc5-4d97-a142-35bb662b7b23",
    "canUpdateConfiguration": true,
    "commands": [
      {
        "id": "reassignTodo",
        "description": "Reassign a todo item",
        "title": "Create To Do",
        "type": "Action",
        "context": ["message"],
        "fetchTask": true
    }]
    ...

```

Veja a seguir um exemplo do `value` objeto que contém os detalhes da mensagem que serão enviados como parte da `composeExtension` solicitação que será enviado ao bot.

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
        "content": "this is the message"
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

### <a name="test-via-uploading"></a>Testar via carregamento

Você pode testar sua extensão de mensagens carregando seu aplicativo. Consulte [carregando seu aplicativo em uma equipe](~/concepts/deploy-and-publish/apps-upload.md) para obter detalhes.

Para abrir sua extensão de mensagens, navegue até qualquer um dos seus chats ou canais. Escolha o botão **mais opções** ( **&#8943;** ) na caixa redigir e escolha sua extensão de mensagens.

## <a name="collecting-input-from-users"></a>Coleta de entrada de usuários

Há três maneiras de coletar informações de um usuário final no Microsoft Teams.

### <a name="static-parameter-list"></a>Lista de parâmetros estáticos

Nesse método, tudo o que você precisa fazer é definir uma lista estática de parâmetros no manifesto, conforme mostrado acima, no comando "criar tarefas pendentes". Para usar esse método, verifique se `fetchTask` está definido como `false` e se você define seus parâmetros no manifesto.

Quando um usuário escolhe um comando com parâmetros estáticos, o Microsoft Teams irá gerar um formulário em um módulo de tarefa com os parâmetros definidos no manifesto. Ao pressionar enviar a `composeExtension/submitAction` é enviada ao bot. Confira o tópico [respondendo a enviar](#responding-to-submit) para obter mais informações sobre o conjunto de respostas esperado.

### <a name="dynamic-input-using-an-adaptive-card"></a>Entrada dinâmica usando um cartão adaptável

Nesse método, seu serviço pode definir um cartão adaptável personalizado para coletar a entrada do usuário final. Para esta abordagem, defina o `fetchTask` parâmetro como `true` no manifesto. Observe que, se você definir `fetchTask` como `true` qualquer parâmetro estático definido para o comando será ignorado.

Neste método, seu serviço receberá um `composeExtension/fetchTask` evento e precisa responder com uma [resposta de módulo de tarefa](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object)com base em cartão adaptável. Veja a seguir uma resposta de exemplo com um cartão adaptável:

```json
{
    "task": {
        "type": "continue",
        "value": {
            "card": {
                "contentType": "application/vnd.microsoft.card.adaptive",
                "content": {
                    "body": [
                        {
                            "type": "TextBlock",
                            "text": "Please enter the following information:"
                        },
                        {
                            "type": "TextBlock",
                            "text": "Name"
                        },
                        {
                            "type": "Input.Text",
                            "spacing": "None",
                            "title": "New Input.Toggle",
                            "placeholder": "Placeholder text"
                        },
                        {
                            "type": "TextBlock",
                            "text": "Date of birth"
                        },
                        {
                            "type": "Input.Date",
                            "spacing": "None",
                            "title": "New Input.Toggle"
                        }
                    ],
                    "type": "AdaptiveCard",
                    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
                    "version": "1.0"
                }
            }
        }
    }
}
```

O bot também pode responder com uma resposta de auth/config se o usuário precisar autenticar ou configurar a extensão antes de obter a entrada do usuário.

### <a name="dynamic-input-using-a-web-view"></a>Entrada dinâmica usando um modo de exibição da Web

Neste método, o serviço pode mostrar um `<iframe>` widget baseado para mostrar qualquer interface do usuário personalizada e coletar a entrada do usuário. Para esta abordagem, defina o `fetchTask` parâmetro como `true` no manifesto.

Assim como no fluxo de cartão adaptável, seu serviço será enviar um `fetchTask` evento e precisa responder com uma resposta de módulo de [tarefa](~/task-modules-and-cards/what-are-task-modules.md#the-taskinfo-object)baseada em URL. Veja a seguir uma resposta de exemplo com um cartão adaptável:

```json
{
    "task": {
        "value": {
            "url": "http://mywebapp.com/input"
        },
        "type": "continue"
    }
}
```

### <a name="request-to-install-your-conversational-bot"></a>Solicitação para instalar o bot de conversa

Se seu aplicativo também contiver um bot de conversação, talvez seja necessário garantir que o bot esteja instalado na conversa antes de carregar o módulo de tarefa. Isso pode ser útil em situações em que você precisa obter contexto adicional para o módulo de tarefas. Por exemplo, talvez seja necessário buscar a lista para preencher um controle do seletor de pessoas ou a lista de canais de uma equipe.

Para facilitar esse fluxo, quando o seu ramal de mensagens recebe primeiro a `composeExtension/fetchTask` verificação de invocação para ver se o seu bot está instalado no contexto atual (isso pode ser feito tentando a chamada obter, por exemplo). Se o bot não estiver instalado, você retorna um cartão adaptável com uma ação que solicita que o usuário instale seu bot Confira o exemplo a seguir. Observe que isso exige que o usuário tenha permissão para instalar aplicativos nesse local; Se eles não conseguirem receber uma mensagem solicitando que eles entrem em contato com o administrador.

Veja um exemplo da resposta:

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

Depois que o usuário concluir a instalação, seu bot receberá outra mensagem de invocação com o `name = composeExtension/submitAction` e o `value.data.msteams.justInTimeInstall = true` .

Veja um exemplo de Invoke:

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

Você deve responder a essa invocação com a mesma resposta de tarefa que você teria respondido se o bot já tiver sido instalado.

## <a name="responding-to-submit"></a>Responder a enviar

Depois que o usuário concluir a inserção de suas entradas, o bot receberá um `composeExtension/submitAction` evento com a ID de comando e os valores de parâmetro definidos.

Essas são as diferentes respostas esperadas para um `submitAction` .

### <a name="task-module-response"></a>Resposta do módulo de tarefa

Isso é usado quando sua extensão precisa encadear caixas de diálogo para obter mais informações. A resposta é exatamente a mesma `fetchTask` mencionada anteriormente.

### <a name="compose-extension-authconfig-response"></a>Resposta de autenticação/config da extensão de redação

Isso é usado quando sua extensão precisa ser autenticada ou configurada para continuar. Consulte a [seção autenticação](~/resources/messaging-extension-v3/search-extensions.md#authentication) na seção pesquisa para obter mais detalhes.

### <a name="compose-extension-result-response"></a>Resposta do resultado da extensão de composição

Isso é usado para inserir um cartão na caixa de redação como resultado de um comando. É a mesma resposta usada no comando Search, mas é limitada a um cartão ou um resultado na matriz.

```json
{
  "composeExtension": {
    "type": "result",
    "attachmentLayout": "list",
    "preview": {
          "contentType": "application/vnd.microsoft.card.thumbnail",
          "content": {
            "title": "85069: Create a cool app",
            "images": [
              {
                "url": "https://placekitten.com/200/200"
              }
            ]
          }
        },
    "attachments": [
      {  
        "contentType": "application/vnd.microsoft.teams.card.o365connector",
        "content": {
          "sections": [
            {
              "activityTitle": "[85069]: Create a cool app",
              "activityImage": "https://placekitten.com/200/200"
            },
            {
              "title": "Details",
              "facts": [
                {
                  "name": "Assigned to:",
                  "value": "[Larry Brown](mailto:larryb@example.com)"
                },
                {
                  "name": "State:",
                  "value": "Active"
                }
              ]
            }
          ]
        }
      }
    ]
  }
}
```

### <a name="respond-with-an-adaptive-card-message-sent-from-a-bot"></a>Responder com uma mensagem de cartão adaptável enviada de um bot

Você também pode responder à ação de envio inserindo uma mensagem com um cartão adaptável no canal com um bot. O usuário poderá visualizar a mensagem antes de enviá-la e potencialmente editar/interagir com ela também. Isso pode ser muito útil em cenários em que você precisa coletar informações de seus usuários antes de criar uma resposta de cartão adaptável. O cenário a seguir mostra como você pode usar esse fluxo para configurar uma pesquisa sem incluir as etapas de configuração na mensagem do canal.

1. O usuário clica na extensão de mensagens para disparar o módulo de tarefa.
1. O usuário usa o módulo de tarefa para configurar a pesquisa.
1. Depois de enviar o módulo de tarefa de configuração, o aplicativo usa as informações fornecidas no módulo de tarefa para criar um cartão adaptável e o envia como `botMessagePreview` resposta ao cliente.
1. O usuário pode visualizar a mensagem do cartão adaptável antes que o bot a insira no canal. Se o bot ainda não for um membro do canal, clicar em `Send` adicionará o bot.
1. Interagir com o cartão adaptável mudará a mensagem antes de enviá-la.
1. Quando o usuário clicar `Send` no bot, a mensagem será postada no canal.

Para habilitar esse fluxo, seu módulo de tarefa deve responder como no exemplo abaixo, que apresentará a mensagem de visualização para o usuário.

>[!Note]
>O `activityPreview` deve conter uma `message` atividade com exatamente 1 anexo de cartão adaptável.

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

Agora, sua extensão de mensagens precisará responder a dois novos tipos de interações `value.botMessagePreviewAction = "send"` e `value.botMessagePreviewAction = "edit"` . Veja a seguir um exemplo do `value` objeto que será necessário processar:

```json
{
  "name": "composeExtension/submitAction",
  "type": "invoke",
  "conversation": { "id": "19:c366b75791784100b6e8b515fd55b063@thread.skype" },
  "imdisplayname": "Pranav Smith",
  ...
  "value": {
    "botMessagePreviewAction": "send" | "edit",
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

Ao responder à `edit` solicitação, você deve responder com uma `task` resposta com os valores preenchidos com as informações que o usuário já enviou. Ao responder à `send` solicitação, você deve enviar uma mensagem para o canal que contém o cartão adaptável finalizado.

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

```typescript
teamChatConnector.onComposeExtensionSubmitAction((
    event: builder.IEvent,
    request: teamBuilder.IComposeExtensionActionCommandRequest,
    callback: (err: Error, result: any, statusCode: number) => void) => {
        let invokeValue = (<any> event).value;

        if (invokeValue.botMessagePreviewAction ) {
            let attachment = invokeValue.botActivityPreview[0].attachments[0];

            if (invokeValue.botMessagePreviewAction === 'send') {
                let msg = new builder.Message()
                    .address(event.address)
                    .addAttachment(attachment);
                teamChatConnector.send([msg.toMessage()],
                    (error) => {
                        if(error){
                            //TODO: Handle error and callback
                        }
                        else {
                            callback(null, null, 200);
                        }
                    }
                );
            }

            else if (invokeValue.botMessagePreviewAction === 'edit') {
              // Create the card and populate with user-inputted information
              let card = { ... }

              let taskResponse = {
                task: {
                  type: "continue",
                  value: {
                    title: "Card Preview",
                    card: {
                      contentType: 'application/vnd.microsoft.card.adaptive',
                      content: card
                    }
                  }
                }
              }
              callback(null, taskResponse, 200);
            }

        else {
            let attachment = {
                  //create adaptive card
                };
            let activity = new builder.Message().addAttachment(attachment).toMessage();
            let response = teamBuilder.ComposeExtensionResponse.messagePreview()
                .preview(activity)
                .toResponse();
            callback(null, response, 200);
        }
    });
```

*Confira também* [exemplos da estrutura de bot](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

Este exemplo mostra esse fluxo usando o [SDK Microsoft. bot. Connector. Teams (v3)](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams).

```csharp
public class MessagesController : ApiController
{

    [BotAuthentication]
    public async Task<HttpResponseMessage> Post([FromBody]Activity activity)
    {
        MicrosoftAppCredentials.TrustServiceUrl(activity.ServiceUrl, DateTime.MaxValue);
        ConnectorClient connectorClient = new ConnectorClient(
            new Uri(activity.ServiceUrl),
            ConfigurationManager.AppSettings[MicrosoftAppCredentials.MicrosoftAppIdKey],
            ConfigurationManager.AppSettings[MicrosoftAppCredentials.MicrosoftAppPasswordKey]);

        if (activity.Type == ActivityTypes.Invoke)
        {
            // Initial task module presented to the user
            if (activity.Name == "composeExtension/fetchTask")
            {
                string task = GetTaskModule();

                return Request.CreateResponse(HttpStatusCode.OK, JObject.Parse(task));
            }
            else if (activity.Name == "composeExtension/submitAction")
            {
                dynamic activityValue = JObject.FromObject(activity.Value);
                string botMessagePreviewAction = activityValue["botMessagePreviewAction"];

                //This is the initial card response sent after the task module is submitted
                if (botMessagePreviewAction is null)
                {
                    string text = activityValue.data.cardMessage;

                    AdaptiveCard card = new AdaptiveCard(new AdaptiveSchemaVersion("1.0"));
                    card.Body.Add(new AdaptiveTextBlock()
                    {
                        Text = "This card will be inserted into the conversation by the bot.",
                        Size = AdaptiveTextSize.Large,
                        Wrap = true
                    });
                    card.Body.Add(new AdaptiveTextBlock()
                    {
                        Text = "The text below is what you provided."
                    });
                    card.Body.Add(new AdaptiveTextBlock()
                    {
                        Text = text,
                    });

                    string cardJson = card.ToJson();

                    string cardMessage = $@"{{
                        'composeExtension': {{
                        'type': 'botMessagePreview',
                        'activityPreview': {{
                            'type': 'message',
                            'attachments': [{{
                                'contentType': 'application/vnd.microsoft.card.adaptive',
                                'content': {cardJson}
                            }}]
                        }}
                        }}
                    }}";

                    JObject res = JObject.Parse(cardMessage);
                    return Request.CreateResponse(HttpStatusCode.OK, res);

                }
                else
                {
                    //This is the "send the card to the channel" event
                    if (botMessagePreviewAction.Equals("send"))
                    {
                        string cardJson = JsonConvert.SerializeObject(activityValue.botActivityPreview[0].attachments[0].content);

                        AdaptiveCardParseResult cardResult = AdaptiveCard.FromJson(cardJson);
                        AdaptiveCard card = cardResult.Card;
                        Attachment cardAttachment = new Attachment
                        {
                            ContentType = AdaptiveCard.ContentType,
                            Content = card
                        };


                        Activity response = activity.CreateReply();
                        response.Attachments.Add(cardAttachment);

                        var result = await connectorClient.Conversations.SendToConversationAsync(response);
                    }
                    //This is fired if the user edits the card before sending it
                    else if (botMessagePreviewAction.Equals("edit"))
                    {
                        string task = GetTaskModule();

                        return Request.CreateResponse(HttpStatusCode.OK, JObject.Parse(task));
                    }
                    else
                    {
                        return Request.CreateResponse(HttpStatusCode.NotImplemented);
                    }
                }
            }
        }

        return Request.CreateResponse(HttpStatusCode.NotImplemented);

    }

    private static string GetTaskModule()
    {
        AdaptiveCard card = new AdaptiveCard(new AdaptiveSchemaVersion("1.0"));
        card.Body.Add(new AdaptiveTextBlock()
        {
            Text = "Please enter the following information:",
            Size = AdaptiveTextSize.Large
        });
        card.Body.Add(new AdaptiveTextBlock()
        {
            Text = "Card Message:"
        });
        card.Body.Add(new AdaptiveTextInput()
        {
            Id = "cardMessage",
            Spacing = AdaptiveSpacing.None,
            Placeholder = "Card message goes here."
        });
        card.Actions.Add(new AdaptiveSubmitAction()
        {
            Title = "Submit"
        });

        string cardJson = card.ToJson();

        //Create the task module response
        string task = $@"{{
                            'task': {{
                                'type': 'continue',
                                'value': {{
                                    'card': {{
                                        'contentType': 'application/vnd.microsoft.card.adaptive',
                                        'content': {cardJson}
                                        }}
                                    }}
                                }}
                            }}";
        return task;
    }

}
```
