---
title: Mensagens em conversas de bot
description: Aprenda as maneiras de ter uma conversa com um bot do Teams e dados de canal do Teams, notificação para sua mensagem, mensagens de imagem, cartões adaptáveis usando exemplos de código
ms.topic: overview
ms.author: anclear
ms.localizationpriority: medium
ms.openlocfilehash: 20cac5ed941e572e4d13cfd4535cb8be7d481355
ms.sourcegitcommit: 1cda2fd3498a76c09e31ed7fd88175414ad428f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/27/2022
ms.locfileid: "67035190"
---
# <a name="messages-in-bot-conversations"></a>Mensagens em conversas de bot

Cada mensagem em uma conversa é um `Activity` objeto do tipo `messageType: message`. Quando um usuário envia uma mensagem, o Teams posta a mensagem em seu bot. O Teams envia um objeto JSON para o ponto de extremidade de mensagens do bot. Seu bot examina a mensagem para determinar seu tipo e responde adequadamente.

As conversas básicas são tratadas por meio do conector do Bot Framework, uma única API REST. Essa API permite que seu bot se comunique com o Teams e outros canais. O SDK do Construtor de Bot fornece os seguintes recursos:

* Acesso fácil ao conector do Bot Framework.
* Funcionalidade adicional para gerenciar o estado e o fluxo da conversa.
* Maneiras simples de incorporar serviços cognitivos, como nLP (processamento de linguagem natural).

Seu bot recebe mensagens do Teams usando `Text` a propriedade e envia respostas de uma ou várias mensagens aos usuários.

Para obter mais informações, consulte [Atribuição de usuário para mensagens de bot](/microsoftteams/platform/messaging-extensions/how-to/action-commands/respond-to-task-module-submit?tabs=dotnet%2Cdotnet-1&branch=pr-en-us-5926#user-attribution-for-bots-messages)

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

Para enviar uma mensagem de texto, especifique a cadeia de caracteres que você deseja enviar como a atividade. No manipulador de atividades do bot, use o método do objeto de `SendActivityAsync` contexto de turno para enviar uma única resposta de mensagem. Use o método do objeto `SendActivitiesAsync` para enviar várias respostas ao mesmo tempo.

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

    this.onMembersAddedActivity(async (context, next) => {
        await Promise.all((context.activity.membersAdded || []).map(async (member) => {
            if (member.id !== context.activity.recipient.id) {
                await context.sendActivity(
                    `Welcome to the team ${member.givenName} ${member.surname}`
                );
            }
        }));

        await next();
    });
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
    "type": "message",
    "from": {
        "id": "28:c9e8c047-2a34-40a1-b28a-b162d5f5327c",
        "name": "Teams TestBot"
    },
    "conversation": {
        "id": "a:17I0kl8EkpE1O9PH5TWrzrLNwnWWcfrU7QZjKR0WSfOpzbfcAg2IaydGElSo10tVr4C7Fc6GtieTJX663WuJCc1uA83n4CSrHSgGBj5XNYLcVlJAs2ZX8DbYBPck201w-",
        "name": "Convo1"
   },
   "recipient": {
        "id": "29:1XJKJMvc5GBtc2JwZq0oj8tHZmzrQgFmB25ATiQWA85gQtHieVkKilBZ9XHoq9j7Zaqt7CZ-NJWi7me2kHTL3Bw",
        "name": "Megan Bowen"
    },
    "text": "My bot's reply",
    "replyToId": "1632474074231"
}

```

---

> [!NOTE]
> A divisão de mensagens ocorre quando uma mensagem de texto e um anexo são enviados na mesma carga de atividade. Essa atividade é dividida em atividades separadas pelo Microsoft Teams, uma com apenas uma mensagem de texto e a outra com um anexo. À medida que a atividade é dividida, você não recebe a ID da mensagem em resposta, que é usada para atualizar [ou](~/bots/how-to/update-and-delete-bot-messages.md) excluir a mensagem proativamente. É recomendável enviar atividades separadas em vez de depender da divisão de mensagens.

As mensagens enviadas entre usuários e bots incluem dados internos do canal dentro da mensagem. Esses dados permitem que o bot se comunique corretamente nesse canal. O SDK do Construtor de Bot permite modificar a estrutura da mensagem.

## <a name="send-suggested-actions"></a>Enviar ações sugeridas

As ações sugeridas permitem que o bot apresente botões que o usuário pode selecionar para fornecer entrada. As ações sugeridas aprimoram a experiência do usuário, permitindo que o usuário responda a uma pergunta ou faça uma escolha com a seleção de um botão, em vez de digitar uma resposta com um teclado. Os botões permanecem visíveis e acessíveis para o usuário nos cartões avançados, mesmo depois que o usuário faz uma seleção, enquanto para ações sugeridas, os botões não estão disponíveis. Isso impede que o usuário escolha botões obsoletos em uma conversa.

Para adicionar ações sugeridas a uma mensagem, `suggestedActions` defina a propriedade do objeto [Activity](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference) para especificar a lista de objetos [CardAction](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference) que representam os botões a serem apresentados ao usuário. Para obter mais informações, consulte [`SugestedActions`](/dotnet/api/microsoft.bot.builder.messagefactory.suggestedactions)

Este é um exemplo de implementação e experiência de ações sugeridas:

``` json
"suggestedActions": {
    "actions": [
      {
        "type": "imBack",
        "title": "Action 1",
        "value": "Action 1"
      },
      {
        "type": "imBack",
        "title": "Action 2",
        "value": "Action 2"
      }
    ],
    "to": [<list of recepientIds>]
  }
```

:::image type="content" source="~/assets/images/Cards/suggested-actions.png" alt-text="Ações sugeridas pelo bot" border="true":::

> [!NOTE]
> * `SuggestedActions` só têm suporte para chatbots um-para-um e mensagens baseadas em texto e não para Cartões Adaptáveis ou anexos.
> * Atualmente é `imBack` o único tipo de ação com suporte e o Teams exibe até três ações sugeridas.

## <a name="teams-channel-data"></a>Dados do canal do Teams

O `channelData` objeto contém informações específicas do Teams e é uma fonte definitiva para IDs de equipe e canal. Opcionalmente, você pode armazenar em cache e usar essas IDs como chaves para armazenamento local. O `TeamsActivityHandler` SDK extrai informações importantes do objeto `channelData` para torná-lo facilmente acessível. No entanto, você sempre pode acessar os dados originais do `turnContext` objeto.

O `channelData` objeto não está incluído em mensagens em conversas pessoais, pois elas ocorrem fora de um canal.

Um objeto `channelData` típico em uma atividade enviada ao bot contém as seguintes informações:

* `eventType`: tipo de evento do Teams passado somente em casos de [eventos de modificação de canal](~/bots/how-to/conversations/subscribe-to-conversation-events.md).
* `tenant.id`: Microsoft Azure Active Directory (Azure AD) de locatário passada em todos os contextos.
* `team`: passado somente em contextos de canal, não no chat pessoal.
  * `id`: GUID para o canal.
  * `name`: nome da equipe passado somente em casos de [eventos de renomeação de equipe](subscribe-to-conversation-events.md#team-renamed).
* `channel`: passado somente em contextos de canal, quando o bot é mencionado ou para eventos em canais em equipes, em que o bot foi adicionado.
  * `id`: GUID para o canal.
  * `name`: nome do canal passado somente em casos de eventos [de modificação de canal](~/bots/how-to/conversations/subscribe-to-conversation-events.md).
* `channelData.teamsTeamId`: preterido. Essa propriedade só está incluída para compatibilidade com versões anteriores.
* `channelData.teamsChannelId`: preterido. Essa propriedade só está incluída para compatibilidade com versões anteriores.

### <a name="example-channeldata-object-channelcreated-event"></a>Exemplo de objeto channelData (evento channelCreated)

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

## <a name="message-content"></a>Conteúdo da mensagem

As mensagens recebidas ou enviadas ao bot podem incluir diferentes tipos de conteúdo de mensagem.

| Formatar    | Do usuário para o bot | Do bot para o usuário | Observações                                                                                   |
|-----------|------------------|------------------|-----------------------------------------------------------------------------------------|
| Rich text  | ✔️                | ✔️                | Seu bot pode enviar rich text, imagens e cartões. Os usuários podem enviar rich text e imagens para seu bot.                                                                                        |
| Imagens  | ✔️                | ✔️                | Máximo de 1024 × 1024 pixels e 1 MB no formato PNG, JPEG ou GIF. Não há suporte para GIF animado.  |
| Cartões     | ❌                | ✔️                | Consulte a referência [de cartão do Teams](~/task-modules-and-cards/cards/cards-reference.md) para obter cartões com suporte. |
| Emojis    | ✔️                | ✔️                | Atualmente, o Teams dá suporte a emojis por meio de UTF-16, como U+1F600 para rosto de sorriso. |

## <a name="notifications-to-your-message"></a>Notificações para sua mensagem

Você também pode adicionar notificações à sua mensagem usando a `Notification.Alert` propriedade. As notificações alertam os usuários sobre novas tarefas, menções e comentários. Esses alertas estão relacionados ao que os usuários estão trabalhando ou ao que devem examinar inserindo um aviso no feed de atividades. Para que as notificações disparem da mensagem do bot, defina a propriedade `TeamsChannelData` de `Notification.Alert` objetos como *true*. A geração ou não de uma notificação depende das configurações do Teams do usuário individual e você não pode substituir essas configurações. O tipo de notificação é uma faixa ou um banner e um email.

> [!NOTE]
> O **campo** Resumo exibe qualquer texto do usuário como uma mensagem de notificação no feed.

O código a seguir mostra um exemplo de como adicionar notificações à sua mensagem:

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

Para aprimorar sua mensagem, você pode incluir imagens como anexos para essa mensagem.

## <a name="picture-messages"></a>Mensagens de imagem

As imagens são enviadas adicionando anexos a uma mensagem. Para obter mais informações sobre anexos, [consulte adicionar anexos de mídia às mensagens](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments).

As imagens podem ter no máximo 1024×1024 MB e 1 MB no formato PNG, JPEG ou GIF. Não há suporte para GIF animado.

Especifique a altura e a largura de cada imagem usando XML. No markdown, o tamanho da imagem assume como padrão 256×256. Por exemplo:

* Use: `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>`.
* Não use: `![Duck on a rock](http://aka.ms/Fo983c)`.

Um bot de conversa pode incluir Cartões Adaptáveis que simplificam fluxos de trabalho de negócios. Os Cartões Adaptáveis oferecem texto, fala, imagens, botões e campos de entrada personalizáveis avançados.

## <a name="adaptive-cards"></a>Cartões Adaptáveis

Os Cartões Adaptáveis podem ser criados em um bot e mostrados em vários aplicativos, como o Teams, seu site e assim por diante. Para obter mais informações, [Cartões Adaptáveis](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card).

O código a seguir mostra um exemplo de envio de um Cartão Adaptável simples:

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

### <a name="form-completion-feedback"></a>Comentários de preenchimento do formulário

A mensagem de conclusão do formulário aparece nos Cartões Adaptáveis ao enviar uma resposta ao bot. A mensagem pode ser de dois tipos, erro ou êxito:

* **Erro**: quando uma resposta enviada ao bot não for bem-sucedida, **algo deu errado, a mensagem Tentar novamente** será exibida.

     :::image type="content" source="../../../assets/images/Cards/error-message.png" alt-text="Mensagem de erro"border="true":::

* **Êxito**: quando uma resposta enviada ao bot é bem-sucedida, **sua resposta foi enviada para a mensagem do** aplicativo.

     :::image type="content" source="../../../assets/images/Cards/success.PNG" alt-text="Mensagem de êxito"border="true":::

     Você pode selecionar **Fechar** ou alternar o chat para ignorar a mensagem.

     Se você não quiser exibir a mensagem de êxito, defina o atributo `hide` como `true` na `msTeams` `feedback` propriedade. A seguir está um exemplo:

     ```json
        "content": {
            "type": "AdaptiveCard",
            "title": "Card with hidden footer messages",
            "version": "1.0",
            "actions": [
            {
                "type": "Action.Submit",
                "title": "Submit",
                "msTeams": {
                    "feedback": {
                    "hide": true
                    }
                }
            }
            ]
        } 
     ```

Para obter mais informações sobre cartões e cartões em bots, consulte a [documentação dos cartões](~/task-modules-and-cards/what-are-cards.md).

## <a name="status-code-responses"></a>Respostas de código de status

A seguir estão os códigos de status e seu código de erro e valores de mensagem:

| Código de status | Código de erro e valores de mensagem | Descrição |
|----------------|-----------------|-----------------|
| 403 | **Código**: `ConversationBlockedByUser` <br/> **Mensagem**: o usuário bloqueou a conversa com o bot. | O usuário bloqueou o bot no chat 1:1 ou em um canal por meio de configurações de moderação. |
| 403 | **Código**: `BotNotInConversationRoster` <br/> **Mensagem**: o bot não faz parte da lista de participantes da conversa. | O bot não faz parte da conversa. |
| 403 | **Código**: `BotDisabledByAdmin` <br/> **Mensagem**: o administrador do locatário desabilitou esse bot. | O locatário bloqueou o bot. |
| 401 | **Código**: `BotNotRegistered` <br/> **Mensagem**: nenhum registro encontrado para este bot. | O registro desse bot não foi encontrado. |
| 412 | **Código**: `PreconditionFailed` <br/> **Mensagem**: Falha na pré-condição, tente novamente. | Uma pré-condição falhou em uma de nossas dependências devido a várias operações simultâneas na mesma conversa. |
| 404 | **Código**: `ConversationNotFound` <br/> **Mensagem**: Conversa não encontrada. | A conversa não foi encontrada. |
| 413 | **Código**: `MessageSizeTooBig` <br/> **Mensagem**: tamanho da mensagem muito grande. | O tamanho na solicitação de entrada era muito grande. |
| 429 | **Código**: `Throttled` <br/> **Mensagem**: muitas solicitações. Também retorna quando tentar novamente depois. | Muitas solicitações foram enviadas pelo bot. Para obter mais informações, consulte o [limite de taxa](~/bots/how-to/rate-limit.md). |

## <a name="code-sample"></a>Exemplo de código

|Nome do exemplo | Descrição | .NETCore | Node.js | Python |
|----------------|-----------------|--------------|----------------|-----------|
| Bot de conversas do Teams | Sistema de mensagens e manipulação de eventos de conversa. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/57.teams-conversation-bot)| [Exibir](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot) |

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Menus de comando do bot](~/bots/how-to/create-a-bot-commands-menu.md)

## <a name="see-also"></a>Confira também

* [Enviar mensagens proativas](~/bots/how-to/conversations/send-proactive-messages.md)
* [Inscreva-se em eventos de conversa](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
* [Enviar e receber arquivos por meio do bot](~/bots/how-to/bots-filesv4.md)
* [Enviar o ID do locatário e o ID da conversa para os cabeçalhos de solicitação do bot](~/bots/how-to/conversations/request-headers-of-the-bot.md)
