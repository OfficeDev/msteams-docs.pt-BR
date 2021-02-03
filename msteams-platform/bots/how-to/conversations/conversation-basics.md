---
title: Noções básicas sobre conversas
author: clearab
description: Como conversar com um bot do Microsoft Teams
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 6f7e7a4d1be08126c96dff07ddbc3e1156700a90
ms.sourcegitcommit: 94ad961ecd002805b4e0424601d1c0ec191ff376
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/02/2021
ms.locfileid: "50075690"
---
# <a name="conversation-basics"></a>Noções básicas sobre conversas

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Uma conversa é uma série de mensagens enviadas entre seu bot e um ou mais usuários. Há três tipos de conversas (também chamadas de escopos) no Teams:

* `teams` Também chamadas de conversas do canal, visíveis para todos os membros do canal.
* `personal` Conversas entre bots e um único usuário.
* `groupChat` Chat entre um bot e dois ou mais usuários. Também habilita seu bot em chats de reunião.

Um bot se comporta de forma ligeiramente diferente, dependendo do tipo de conversa em que ele está envolvido:

* Bots em conversas de chat em grupo e canal exigem que o usuário @ mencione o bot para invocá-lo em um canal.
* Os bots em uma conversa um-para-um não exigem uma @menção. Todas as mensagens enviadas pelo usuário serão roteadas para seu bot.

Para habilitar seu bot em um escopo específico, adicione esse escopo ao manifesto [do aplicativo.](~/resources/schema/manifest-schema.md)

## <a name="activities"></a>Atividades

Cada mensagem é um `Activity` objeto do tipo `messageType: message` . Quando um usuário envia uma mensagem, o Teams envia a mensagem para seu bot; especificamente, ele envia um objeto JSON para o ponto de extremidade de mensagens do bot. Seu bot examina a mensagem para determinar seu tipo e responde de acordo.

A conversa básica é manipulada por meio do Bot Framework Connector, uma única API REST para permitir que seu bot se comunique com o Teams e outros canais. O SDK do Construtor de Bots fornece acesso fácil a essa API, funcionalidade adicional para gerenciar o fluxo e o estado da conversa e maneiras simples de incorporar serviços cognitivas, como processamento de linguagem natural (NLP).

## <a name="receive-a-message"></a>Receber uma mensagem

Para receber uma mensagem de texto, use `Text` a propriedade do `Activity` objeto. No manipulador de atividades do bot, use o objeto de contexto de curva `Activity` para ler uma única solicitação de mensagem.

O código a seguir mostra um exemplo.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  await turnContext.SendActivityAsync(MessageFactory.Text($"Echo: {turnContext.Activity.Text}"), cancellationToken);
}

```

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

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
    "text": "Hello Teams TestBot",
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

Para enviar uma mensagem de texto, especifique a cadeia de caracteres que você deseja enviar como atividade. Nos manipuladores de atividades do bot, use o método do objeto de contexto de retorno `SendActivityAsync` para enviar uma única resposta de mensagem. Você também pode usar o método do `SendActivitiesAsync` objeto para enviar várias respostas ao mesmo tempo. O código a seguir mostra um exemplo de envio de uma mensagem quando alguém é adicionado a uma conversa  

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task OnMembersAddedAsync(IList<ChannelAccount> membersAdded, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
  await turnContext.SendActivityAsync(MessageFactory.Text($"Hello and welcome!"), cancellationToken);
}

```

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

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

## <a name="teams-channel-data"></a>Dados de canal do Teams

O `channelData` objeto contém informações específicas do Teams e é a fonte definitiva para IDs de equipe e canal. Talvez seja necessário armazenar em cache e usar essas IDs como chaves para o armazenamento local. O SDK normalmente obterá informações importantes do objeto para torná-lo mais facilmente acessível, no entanto, você sempre poderá acessar as informações `TeamsActivityHandler` `channelData` originais do `turnContext` objeto.

O `channelData` objeto não está incluído em mensagens em conversas pessoais, pois elas ocorrem fora de qualquer canal.

Um objeto channelData típico em uma atividade enviada ao seu bot contém as seguintes informações:

* `eventType` Tipo de evento do Teams; passado somente em casos de eventos [de modificação de canal](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
* `tenant.id` ID de locatário do Azure Active Directory; passado em todos os contextos
* `team` Passado somente em contextos de canal, não em bate-papo pessoal.
  * `id` GUID do canal
  * `name` Nome da equipe; passado somente em casos de [eventos de renomear equipe](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
* `channel` Passado somente em contextos de canal quando o bot é mencionado ou para eventos em canais em equipes onde o bot foi adicionado
  * `id` GUID do canal
  * `name`Nome do canal; passado somente em casos de eventos [de modificação de canal.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
* `channelData.teamsTeamId` Preterido. Essa propriedade é incluída somente para compatibilidade com compatibilidade.
* `channelData.teamsChannelId` Preterido. Essa propriedade é incluída somente para compatibilidade com compatibilidade.

### <a name="example-channeldata-object-channelcreated-event"></a>Objeto channelData de exemplo (evento channelCreated)

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

## <a name="message-content"></a>Conteúdo da mensagem

Seu bot pode enviar rich text, imagens e cartões. Os usuários podem enviar rich text e imagens para seu bot.

| Formatar    | De usuário para bot | De bot para usuário | Observações                                                                                   |
|-----------|------------------|------------------|-----------------------------------------------------------------------------------------|
| Rich text  | ✔                | ✔                |                                                                                         |
| Imagens  | ✔                | ✔                | Máximo de 1024×1024 e 1 MB em formato PNG, JPEG ou GIF; NÃO há suporte para GIF animado  |
| Cartões     | ✖                | ✔                | Confira a Referência [de Cartão do Teams](~/task-modules-and-cards/cards/cards-reference.md) para cartões com suporte |
| Emojis    | ✖                | ✔                | No momento, o Teams dá suporte a emojis por meio de UTF-16 (como U+1F600 para face de lançamento)          |

## <a name="adding-notifications-to-your-message"></a>Adicionando notificações à sua mensagem

As notificações alertam os usuários sobre novas tarefas, menções e comentários relacionados ao que eles estão trabalhando ou precisam olhar inserindo um aviso em seu Feed de Atividades. Você pode definir notificações para disparar a partir de sua mensagem de bot definindo a `TeamsChannelData` propriedade de objetos como `Notification.Alert` true. A ativação ou não de uma notificação dependerá, em última análise, das configurações do Teams do usuário individual, e você não poderá substituir programaticamente essas configurações. O tipo de notificação será uma faixa ou uma faixa e um email.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  var message = MessageFactory.Text("You'll get a notification, if you've turned them on.");
  message.TeamsNotifyUser();

  await turnContext.SendActivityAsync(message);
}
```

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

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

## <a name="picture-messages"></a>Mensagens de imagem

Imagens são enviadas adicionando anexos a uma mensagem. Você pode encontrar mais informações sobre anexos na documentação [do Bot Framework.](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments?view=azure-bot-service-3.0&preserve-view=true)

As imagens podem ter no máximo 1024×1024 e 1 MB em formato PNG, JPEG ou GIF; NÃO há suporte para GIF animado.

Recomendamos que você especifique a altura e a largura de cada imagem usando XML. Se você usar Markdown, o tamanho da imagem será padrão 256×256. Por exemplo:

* Usar - `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>`
* Não usar - `![Duck on a rock](http://aka.ms/Fo983c)`

## <a name="code-sample"></a>Exemplo de código
|**Nome do exemplo** | **Descrição** | **. NETCore** | **Javascript** | **Python**|
|----------------|-----------------|--------------|----------------|-----------|
| Bot de conversa do Teams | Manipulação de eventos de mensagens e conversas. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/57.teams-conversation-bot)| [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot) |

## <a name="next-steps"></a>Próximas etapas

* [Enviar mensagens proativas](~/bots/how-to/conversations/send-proactive-messages.md)
* [Inscreva-se em eventos de conversa](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
