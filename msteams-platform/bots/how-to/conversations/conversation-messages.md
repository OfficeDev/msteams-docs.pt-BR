---
title: Mensagens em conversas de bot
description: Descreve maneiras de ter uma conversa com um Microsoft Teams bot
ms.topic: overview
ms.author: anclear
ms.localizationpriority: medium
keyword: receive message send message picture message channel data adaptive cards
ms.openlocfilehash: b46ce611ca09c4d5883cc66e0078291422e2b65a
ms.sourcegitcommit: 211f2eaa05494a11b8c2a050d7f1a9ca1c1c78a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2021
ms.locfileid: "59491671"
---
# <a name="messages-in-bot-conversations"></a>Mensagens em conversas de bot

Cada mensagem em uma conversa é um `Activity` objeto do tipo `messageType: message` . Quando um usuário envia uma mensagem, Teams a mensagem para o bot. Teams envia um objeto JSON para o ponto de extremidade de mensagens do bot. Seu bot examina a mensagem para determinar seu tipo e responde de acordo.

As conversas básicas são manipuladas por meio do conector da Estrutura do Bot, uma única API REST. Essa API permite que seu bot se comunique com Teams e outros canais. O SDK do Construtor de Bots fornece os seguintes recursos:

* Acesso fácil ao conector da Estrutura de Bot.
* Funcionalidade adicional para gerenciar o fluxo e o estado da conversa.
* Maneiras simples de incorporar serviços cognitivos, como o processamento de linguagem natural (NLP).

Seu bot recebe mensagens de Teams usando a propriedade e envia respostas de mensagem única ou múltipla `Text` aos usuários.

## <a name="receive-a-message"></a>Receber uma mensagem

Para receber uma mensagem de texto, use a propriedade `Text` do objeto `Activity`. No manipulador de atividades do bot, alterne o contexto do objeto `Activity` para ler uma única solicitação de mensagem.

O código a seguir mostra um exemplo de recebimento de uma mensagem:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  await turnContext.SendActivityAsync(MessageFactory.Text($"Echo: {turnContext.Activity.Text}"), cancellationToken);
}

```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```typescript

export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onMessage(async (context, next) => {
            await context.sendActivity(`Echo: '${context.activity.text}'`);
            await next();
        });
    }
}

```

# <a name="python"></a>[Python](#tab/python)

<!-- Verify -->
```python

async def on_message_activity(self, turn_context: TurnContext):
    return await turn_context.send_activity(MessageFactory.text(f"Echo: {turn_context.activity.text}"))

```

# <a name="json"></a>[JSON](#tab/json)

```json
{
    "type": "message",
    "id": "1485983408511",
    "timestamp": "2017-02-01T21:10:07.437Z",
    "localTimestamp": "2017-02-01T14:10:07.437-07:00",
    "serviceUrl": "https://smba.trafficmanager.net/amer/",
    "channelId": "msteams",
    "from": {
        "id": "29:1XJKJMvc5GBtc2JwZq0oj8tHZmzrQgFmB39ATiQWA85gQtHieVkKilBZ9XHoq9j7Zaqt7CZ-NJWi7me2kHTL3Bw",
        "name": "Megan Bowen",
        "aadObjectId": "7faf8ab2-3d56-4244-b585-20c8a42ed2b8"
    },
    "conversation": {
        "conversationType": "personal",
        "id": "a:17I0kl9EkpE1O9PH5TWrzrLNwnWWcfrU7QZjKR0WSfOpzbfcAg2IaydGElSo10tVr4C7Fc6GtieTJX663WuJCc1uA83n4CSrHSgGBj5XNYLcVlJAs2ZX8DbYBPck201w-"
    },
    "recipient": {
        "id": "28:c9e8c047-2a74-40a2-b28a-b162d5f5327c",
        "name": "Teams TestBot"
    },
    "textFormat": "plain",
    "text": "Hello Teams TestBot.Sending bold-italic rich text",
    "attachments": [
      {
            "contentType": "text/html",
            "content": "<div><div>Hello Teams TestBot. Sending <strong>bold</strong>-<em>italic</em> rich text.</div>\n</div>"
      } 
    ],
    "entities": [
      { 
        "locale": "en-US",
        "country": "US",
        "platform": "Windows",
        "timezone": "America/Los_Angeles",
        "type": "clientInfo"
      }
    ],
    "channelData": {
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    },
    "locale": "en-US"
}
```

---

## <a name="send-a-message"></a>Enviar uma mensagem

Para enviar uma mensagem de texto, especifique a cadeia de caracteres que você deseja enviar como a atividade. No manipulador de atividades do bot, use o método do objeto turn context `SendActivityAsync` para enviar uma única resposta de mensagem. Use o método do `SendActivitiesAsync` objeto para enviar várias respostas ao mesmo tempo.

O código a seguir mostra um exemplo de envio de uma mensagem quando um usuário é adicionado a uma conversa:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
protected override async Task OnMembersAddedAsync(IList<ChannelAccount> membersAdded, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
  await turnContext.SendActivityAsync(MessageFactory.Text($"Hello and welcome!"), cancellationToken);
}

```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```typescript

export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onMessage(async (context, next) => {
            await context.sendActivity('Hello and welcome!');
            await next();
        });
    }
}
```

# <a name="python"></a>[Python](#tab/python)

<!-- Verify -->

```python

async def on_members_added_activity(
    self, members_added: [ChannelAccount], turn_context: TurnContext
):
    for member in teams_members_added:
        await turn_context.send_activity(f"Welcome your new team member {member.id}")
    return

```

# <a name="json"></a>[JSON](#tab/json)

```json
{
    "text": "hi",
    "textFormat": "plain",
    "type": "message",
    "timestamp": "2019-10-31T20:57:27.2347285Z",
    "localTimestamp": "2019-10-31T13:57:27.2347285-07:00",
    "id": "1572555447214",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer/",
    "from": {
        "id": "29:1Xv-kvy4dKirR0rZfSF_kAVUzotoT1SXuEzkC9XGkuZng8YBw8qyu5uh4128fQRjlGgvEiRLx-0XP4KYMwcgdZw",
        "name": "Jane Doe",
        "aadObjectId": "df486eae-88fd-42a5-b45e-c581588186db"
    },
    "conversation": {
        "conversationType": "personal",
        "tenantId": "72f988bf-86f1-41af-91ab-2d7cd011db47",
        "id": "a:1oAmWTVBBe9E0JrpGxauqNyx4CCE_iQf2ZuWon9D42722Fon3wYIpbhgbRChE3wgVS1Gwl9zS1pZy4FSu6-x1vGEq5KBQK-EbBgyPyeP_C-lbLBY3vxnGk9m9D_282jbg"
    },
    "recipient": {
        "id": "28:5baea8d1-d4ea-43a1-b101-882f4c8d9cb4",
        "name": "Imported Bot"
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
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    },
    "locale": "en-US"
}
```

---

> [!NOTE]
> A divisão de mensagens ocorre quando uma mensagem de texto e um anexo são enviados na mesma carga de atividade. Essa atividade é dividida em atividades separadas por Microsoft Teams, uma com apenas uma mensagem de texto e outra com um anexo. À medida que a atividade é dividida, você não recebe a ID da mensagem em resposta, que é usada para atualizar [ou excluir](~/bots/how-to/update-and-delete-bot-messages.md) a mensagem proativamente. É recomendável enviar atividades separadas em vez de depender da divisão de mensagens.

As mensagens enviadas entre usuários e bots incluem dados de canal interno dentro da mensagem. Esses dados permitem que o bot se comunique corretamente nesse canal. O SDK do Construtor de Bots permite modificar a estrutura de mensagens.

## <a name="teams-channel-data"></a>Teams de canal

O objeto contém Teams informações específicas e é uma fonte `channelData` definitiva para IDs de equipe e canal. Opcionalmente, você pode armazenar em cache e usar essas IDs como chaves para armazenamento local. O no SDK retira informações importantes do objeto para `TeamsActivityHandler` `channelData` torná-lo facilmente acessível. No entanto, você sempre pode acessar os dados originais do `turnContext` objeto.

O `channelData` objeto não está incluído em mensagens em conversas pessoais, pois elas ocorrem fora de um canal.

Um objeto `channelData` típico em uma atividade enviada ao bot contém as seguintes informações:

* `eventType`: Teams tipo de evento passado somente em casos de [eventos de modificação de canal.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
* `tenant.id`: Azure Active Directory ID de locatário passada em todos os contextos.
* `team`: Passado somente em contextos de canal, não em chat pessoal.
  * `id`: GUID para o canal.
  * `name`: Nome da equipe passada somente em casos de [eventos de renomear a equipe.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
* `channel`: Passado somente em contextos de canal quando o bot é mencionado ou para eventos em canais em equipes onde o bot foi adicionado.
  * `id`: GUID para o canal.
  * `name`: Nome do canal passado somente em casos de eventos [de modificação de canal.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
* `channelData.teamsTeamId`: Preterido. Essa propriedade só é incluída para compatibilidade com compatibilidade.
* `channelData.teamsChannelId`: Preterido. Essa propriedade só é incluída para compatibilidade com compatibilidade.

### <a name="example-channeldata-object-or-channelcreated-event"></a>Exemplo de objeto channelData ou evento channelCreated

O código a seguir mostra um exemplo do objeto channelData:

```json
"channelData": {
    "eventType": "channelCreated",
    "tenant": {
        "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
    },
    "channel": {
        "id": "19:693ecdb923ac4458a5c23661b505fc84@thread.skype",
        "name": "My New Channel"
    },
    "team": {
        "id": "19:693ecdb923ac4458a5c23661b505fc84@thread.skype"
    }
}
```

As mensagens recebidas ou enviadas ao bot podem incluir diferentes tipos de conteúdo de mensagem.

## <a name="message-content"></a>Conteúdo da mensagem

| Formatar    | De usuário para bot | De bot para usuário | Observações                                                                                   |
|-----------|------------------|------------------|-----------------------------------------------------------------------------------------|
| Rich text  | ✔                | ✔                | Seu bot pode enviar rich text, pictures e cards. Os usuários podem enviar texto e imagens rich para seu bot.                                                                                        |
| Imagens  | ✔                | ✔                | Máximo de 1024×1024 e 1 MB no formato PNG, JPEG ou GIF. Gif animado não é suportado.  |
| Cartões     | ✖                | ✔                | Consulte a [Teams de cartão para](~/task-modules-and-cards/cards/cards-reference.md) cartões com suporte. |
| Emojis    | ✖                | ✔                | Teams atualmente dá suporte a emojis por meio do UTF-16, como U+1F600 para rosto de goslinha. |

Você também pode adicionar notificações à sua mensagem usando a `Notification.Alert` propriedade.

## <a name="notifications-to-your-message"></a>Notificações à sua mensagem

As notificações alertam os usuários sobre novas tarefas, menções e comentários. Esses alertas estão relacionados ao que os usuários estão trabalhando ou ao que devem observar inserindo um aviso no feed de atividades. Para que as notificações acionem de sua mensagem bot, de definir a propriedade `TeamsChannelData` objects `Notification.Alert` como *true*. A ativação ou não de uma notificação depende das configurações de Teams do usuário individual e você não pode substituir essas configurações. O tipo de notificação é um banner ou um banner e um email.

> [!NOTE]
> O **campo** Resumo exibe qualquer texto do usuário como uma mensagem de notificação no feed.

O código a seguir mostra um exemplo de adição de notificações à sua mensagem:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  var message = MessageFactory.Text("You'll get a notification, if you've turned them on.");
  message.TeamsNotifyUser();

  await turnContext.SendActivityAsync(message);
}
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```typescript
this.onMessage(async (turnContext, next) => {
    let message = MessageFactory.text("You'll get a notification, if you've turned them on.");
    teamsNotifyUser(message);

    await turnContext.sendActivity(message);

    // By calling next() you ensure that the next BotHandler is run.
    await next();
});
```

# <a name="python"></a>[Python](#tab/python)

```python

async def on_message_activity(self, turn_context: TurnContext):
    message = MessageFactory.text("You'll get a notification, if you've turned them on.")
    teams_notify_user(message)

    await turn_context.send_activity(message)

```

# <a name="json"></a>[JSON](#tab/json)

```json
{
  "type": "message",
  "timestamp": "2017-04-24T21:46:00.9663655Z",
  "localTimestamp": "2017-04-24T14:46:00.9663655-07:00",
  "serviceUrl": "https://callback.com",
  "channelId": "msteams",
  "from": {
    "id": "28:e4fda94a-4b80-40eb-9bf0-6314491bc793",
    "name": "The bot"
  },
  "conversation": {
    "id": "a:1pL6i0oY3C0K8oAj8"
  },
  "recipient": {
    "id": "29:1rsVJmSSFMScF0YFyCXpvNWlo",
    "name": "User"
  },
  "text": "John Phillips assigned you a weekly todo",
  "summary": "Don't forget to meet with Marketing next week",
  "channelData": {
    "notification": {
      "alert": true
    }
  },
  "replyToId": "1493070356924"
}
```

---

Para aprimorar sua mensagem, você pode incluir imagens como anexos a essa mensagem.

## <a name="picture-messages"></a>Mensagens de imagem

As imagens são enviadas adicionando anexos a uma mensagem. Para obter mais informações sobre anexos, consulte [Documentação da Estrutura de Bots.](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments)

As imagens podem ter no máximo 1024×1024 e 1 MB no formato PNG, JPEG ou GIF. Gif animado não é suportado.

Especifique a altura e a largura de cada imagem usando XML. Na marcação, o tamanho da imagem é padrão para 256×256. Por exemplo:

* Use: `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>` .
* Não use: `![Duck on a rock](http://aka.ms/Fo983c)` .

Um bot de conversa pode incluir Cartões Adaptáveis que simplificam fluxos de trabalho de negócios. Os Cartões Adaptáveis oferecem texto, fala, imagens, botões e campos de entrada personalizáveis.

## <a name="adaptive-cards"></a>Cartões Adaptáveis

Cartões adaptáveis podem ser autorados em um bot e mostrados em vários aplicativos, como Teams, seu site e assim por diante. Para obter mais informações, consulte [Adaptive Cards](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card).

O código a seguir mostra um exemplo de envio de um cartão adaptável simples:

```json
{
    "type": "AdaptiveCard",
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.5",
    "body": [
    {
        "items": [
        {
            "size": "large",
            "text": " Simple Adaptivecard Example with a Textbox",
            "type": "TextBlock",
            "weight": "bolder",
            "wrap": true
        },
        ],
        "spacing": "extraLarge",
        "type": "Container",
        "verticalContentAlignment": "center"
    }
    ]
}
```

Para saber mais sobre cartões e cartões em bots, consulte [documentação de cartões.](~/task-modules-and-cards/what-are-cards.md)

## <a name="status-code-responses"></a>Respostas de código de status

A seguir estão os códigos de status e seus valores de código de erro e mensagem:

| Código de status | Valores de código de erro e mensagem | Descrição |
|----------------|-----------------|-----------------|
| 403 | **Código**: `ConversationBlockedByUser` <br/> **Mensagem**: o usuário bloqueou a conversa com o bot. | O usuário bloqueou o bot no chat 1:1 ou em um canal por meio de configurações de moderação. |
| 403 | **Código**: `BotNotInConversationRoster` <br/> **Mensagem**: o bot não faz parte da lista de conversas. | O bot não faz parte da conversa. |
| 403 | **Código**: `BotDisabledByAdmin` <br/> **Mensagem**: o administrador do locatário desabilitou esse bot. | O locatário bloqueou o bot. |
| 401 | **Código**: `BotNotRegistered` <br/> **Mensagem**: nenhum registro encontrado para este bot. | O registro desse bot não foi encontrado. |
| 412 | **Código**: `PreconditionFailed` <br/> **Mensagem**: Falha na pré-condição, tente novamente. | Uma pré-condição falhou em uma de nossas dependências devido a várias operações simultâneas na mesma conversa. |
| 404 | **Código**: `ConversationNotFound` <br/> **Mensagem**: Conversa não encontrada. | A conversa não foi encontrada. |
| 413 | **Código**: `MessageSizeTooBig` <br/> **Mensagem**: tamanho da mensagem muito grande. | O tamanho da solicitação de entrada era muito grande. |
| 429 | **Código**: `Throttled` <br/> **Mensagem**: solicitações demais. Também retorna quando repetir depois. | Muitas solicitações foram enviadas pelo bot. Para obter mais informações, consulte [limite de taxa](~/bots/how-to/rate-limit.md). |

## <a name="code-sample"></a>Exemplo de código

|Nome do exemplo | Descrição | .NETCore | Node.js | Python |
|----------------|-----------------|--------------|----------------|-----------|
| Bot de conversas do Teams | Manipulação de eventos de mensagens e conversas. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/57.teams-conversation-bot)| [Exibir](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot) |

## <a name="see-also"></a>Confira também

- [Enviar mensagens proativas](~/bots/how-to/conversations/send-proactive-messages.md)

- [Inscreva-se em eventos de conversa](~/bots/how-to/conversations/subscribe-to-conversation-events.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Menus de comando bot](~/bots/how-to/create-a-bot-commands-menu.md)
