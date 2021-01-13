---
title: Conversas em grupo e canal com um bot
author: clearab
description: Como enviar, receber e manipular mensagens para um bot em um canal ou chat de grupo.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 8a9a58208fff5cc2fe376fcb9932bad6ac2bf36f
ms.sourcegitcommit: 4539479289b43812eaae07a1c0f878bed815d2d2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/12/2021
ms.locfileid: "49797838"
---
# <a name="channel-and-group-chat-conversations-with-a-microsoft-teams-bot"></a>Conversas de canal e chat em grupo com um bot do Microsoft Teams

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Ao adicionar o ou escopo ao seu bot, ele pode estar disponível para ser instalado em um chat de equipe `teams` `groupchat` ou grupo. Isso permite que todos os membros da conversa interajam com seu bot. Uma vez instalado, ele também terá acesso a metadados sobre a conversa, como a lista de membros da conversa e quando instalado em detalhes de uma equipe sobre essa equipe e a lista completa de canais.

Os bots em um grupo ou canal só recebem mensagens quando são mencionados (@botname), eles não recebem nenhuma outra mensagem enviada para a conversa.

> [!NOTE]
> O bot deve ser @mentioned diretamente. Seu bot não receberá uma mensagem quando a equipe ou o canal for mencionado, ou quando alguém responder a uma mensagem do seu bot sem @mentioning-la.

## <a name="design-guidelines"></a>Diretrizes de design

Veja como projetar [conversas de bot em canais e chats.](~/bots/design/bots.md)

## <a name="creating-new-conversation-threads"></a>Criando novos threads de conversa

Quando o bot é instalado em uma equipe, às vezes pode ser necessário criar um novo thread de conversa em vez de responder a um já existente. Essa é uma forma de mensagens [proativas.](~/bots/how-to/conversations/send-proactive-messages.md)

## <a name="working-with-mentions"></a>Trabalhar com menções

Cada mensagem para o bot de um grupo ou canal conterá um @mention com seu próprio nome no texto da mensagem, portanto, você precisará garantir que a análise de mensagens lidará com isso. Seu bot também pode recuperar outros usuários mencionados em uma mensagem e adicionar menções a qualquer mensagem enviada.

### <a name="stripping-mentions-from-message-text"></a>Menções de remoção do texto da mensagem

Você pode achar necessário retirar a @mentions do texto da mensagem que seu bot recebe.

### <a name="retrieving-mentions"></a>Recuperando menções

As menções são retornadas no objeto na carga e contêm a ID exclusiva do usuário e, na maioria dos casos, o nome `entities` do usuário mencionado. O texto da mensagem também incluirá a menção como `<at>@John Smith<at>` . No entanto, você não deve confiar no texto na mensagem para recuperar qualquer informação sobre o usuário; é possível para a pessoa que está enviando a mensagem alterá-la. Em vez disso, use o `entities` objeto.

Você pode recuperar todas as menções na mensagem chamando a função no SDK do Construtor de `GetMentions` Bots, que retorna uma matriz de `Mention` objetos.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
    Mention[] mentions = turnContext.Activity.GetMentions();
    if(mentions != null)
    {
        ChannelAccount firstMention = mentions[0].Mentioned;
        await turnContext.SendActivityAsync($"Hello {firstMention.Name}");
    }
    else
    {
        await turnContext.SendActivityAsync("Aw, no one was mentioned.");
    }
}
```

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

```typescript
this.onMessage(async (turnContext, next) => {
    const mentions = TurnContext.getMentions(turnContext.activity);
    if (mentions){
        const firstMention = mentions[0].mentioned;
        await turnContext.sendActivity(`Hello ${firstMention.name}.`);
    } else {
        await turnContext.sendActivity(`Aw, no one was mentioned.`);
    }

    await next();
});
```

# <a name="json"></a>[JSON](#tab/json)

```json
{
    "type": "message",
    "text": "Hey <at>Pranav Smith</at> check out this message",
    "timestamp": "2017-10-29T00:51:05.9908157Z",
    "localTimestamp": "2017-10-28T17:51:05.9908157-07:00",
    "serviceUrl": "https://skype.botframework.com",
    "channelId": "msteams",
    "from": {
        "id": "29:9e52142b-5e5e-4d7b-bb3e-e82dcf620000",
        "name": "Jane Smith"
    },
    "conversation": {
        "id": "19:aebd0ad4d6ab42c8b9ed19c251c2fc37@thread.skype;messageid=1481567603816"
    },
    "recipient": {
        "id": "8:orgid:6aebbad0-e5a5-424a-834a-20fb051f3c1a",
        "name": "stlrgload100"
    },
    "attachments": [
        {
            "contentType": "image/png",
            "contentUrl": "https://upload.wikimedia.org/wikipedia/en/a/a6/Bender_Rodriguez.png",
            "name": "Bender_Rodriguez.png"
        }
    ],
    "entities": [
        {
            "type":"mention",
            "mentioned":{
                "id":"29:08q2j2o3jc09au90eucae",
                "name":"Pranav Smith"
            },
            "text": "<at>@Pranav Smith</at>"
        }
    ],
    "replyToId": "3UP4UTkzUk1zzeyW"
}
```

# <a name="python"></a>[Python](#tab/python)

```python
@staticmethod
def get_mentions(activity: Activity) -> List[Mention]:
    result: List[Mention] = []
    if activity.entities is not None:
        for entity in activity.entities:
            if entity.type.lower() == "mention":
                    result.append(entity)
     return result
```

* * *

### <a name="adding-mentions-to-your-messages"></a>Adicionando menções às suas mensagens

Seu bot pode mencionar outros usuários em mensagens postadas em canais. Para fazer isso, sua mensagem deve fazer o seguinte:

O `Mention` objeto tem duas propriedades que você precisará definir:

* Incluir <at>@username</at> no texto da mensagem
* Incluir o objeto mention dentro da coleção de entidades

O SDK da Estrutura do Bot fornece métodos e objetos auxiliares para facilitar a construção da menção.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
    var mention = new Mention
    {
        Mentioned = turnContext.Activity.From,
        Text = $"<at>{XmlConvert.EncodeName(turnContext.Activity.From.Name)}</at>",
    };

    var replyActivity = MessageFactory.Text($"Hello {mention.Text}.");
    replyActivity.Entities = new List<Entity> { mention };

    await turnContext.SendActivityAsync(replyActivity, cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

```typescript
this.onMessage(async (turnContext, next) => {
    const mention = {
        mentioned: turnContext.activity.from,
        text: `<at>${ new TextEncoder().encode(turnContext.activity.from.name) }</at>`,
    } as Mention;

    const replyActivity = MessageFactory.text(`Hello ${mention.text}`);
    replyActivity.entities = [mention];

    await turnContext.sendActivity(replyActivity);

    // By calling next() you ensure that the next BotHandler is run.
    await next();
});
```

# <a name="json"></a>[JSON](#tab/json)

O campo no objeto na matriz deve corresponder `text` exatamente a uma parte do campo de `entities`  `text` mensagem. Se não o fizer, a menção será ignorada.

```json
{
    "type": "message",
    "text": "Hey <at>Pranav Smith</at> check out this message",
    "timestamp": "2017-10-29T00:51:05.9908157Z",
    "localTimestamp": "2017-10-28T17:51:05.9908157-07:00",
    "serviceUrl": "https://skype.botframework.com",
    "channelId": "msteams",
    "from": {
        "id": "29:9e52142b-5e5e-4d7b-bb3e-e82dcf620000",
        "name": "Jane Smith"
    },
    "conversation": {
        "id": "19:aebd0ad4d6ab42c8b9ed19c251c2fc37@thread.skype;messageid=1481567603816"
    },
    "recipient": {
        "id": "8:orgid:6aebbad0-e5a5-424a-834a-20fb051f3c1a",
        "name": "stlrgload100"
    },
    "attachments": [
        {
            "contentType": "image/png",
            "contentUrl": "https://upload.wikimedia.org/wikipedia/en/a/a6/Bender_Rodriguez.png",
            "name": "Bender_Rodriguez.png"
        }
    ],
    "entities": [
        {
            "type":"mention",
            "mentioned":{
                "id":"29:08q2j2o3jc09au90eucae",
                "name":"Pranav Smith"
            },
            "text": "<at>@Pranav Smith</at>"
        }
    ],
    "replyToId": "3UP4UTkzUk1zzeyW"
}
```

# <a name="python"></a>[Python](#tab/python)

```python
async def _mention_activity(self, turn_context: TurnContext):
        mention = Mention(
            mentioned=turn_context.activity.from_property,
            text=f"<at>{turn_context.activity.from_property.name}</at>",
            type="mention"
        )

        reply_activity = MessageFactory.text(f"Hello {mention.text}")
        reply_activity.entities = [Mention().deserialize(mention.serialize())]
        await turn_context.send_activity(reply_activity)
```

* * *

## <a name="sending-a-message-on-installation"></a>Enviar uma mensagem na instalação

Quando seu bot é adicionado pela primeira vez ao grupo ou equipe, pode ser útil enviar uma mensagem apresentando-o. A mensagem deve fornecer uma breve descrição dos recursos do bot e como usá-los. Você vai querer se inscrever no `conversationUpdate` evento, com `teamMemberAdded` o eventType.  Como o evento é enviado quando um novo membro da equipe é adicionado, você precisa verificar se o novo membro adicionado é o bot. Confira [Enviar uma mensagem de boas-vindas para um novo membro da equipe](~/bots/how-to/conversations/send-proactive-messages.md) para obter mais detalhes.

Você também pode querer enviar uma mensagem pessoal para cada membro da equipe quando o bot for adicionado. Para fazer isso, você pode obter a lista de participação da equipe e enviar uma mensagem direta a cada usuário.

Não é recomendável enviar uma mensagem nas seguintes situações:

* A equipe é grande (obviamente inentente, mas, por exemplo, maior do que 100 membros). Seu bot pode ser visto como "spammy" e a pessoa que o adicionou poderá receber reclamações, a menos que você comunique claramente a proposta de valor do bot para todos que veem a mensagem de boas-vindas.
* Seu bot é mencionado pela primeira vez em um grupo ou canal (em vez de ser adicionado pela primeira vez a uma equipe)
* Um grupo ou canal é renomeado
* Um membro da equipe é adicionado a um grupo ou canal

## <a name="learn-more"></a>Saiba mais

Seu bot tem acesso a informações adicionais sobre o chat em grupo ou a equipe em que está instalado. Confira [o contexto de equipes](~/bots/how-to/get-teams-context.md) para APIs adicionais disponíveis para seu bot.

Também há eventos adicionais que seu bot pode se inscrever e responder. Confira [se inscrever em eventos de conversa](~/bots/how-to/conversations/subscribe-to-conversation-events.md) para saber como.

[!INCLUDE [sample](~/includes/bots/teams-bot-samples.md)]
