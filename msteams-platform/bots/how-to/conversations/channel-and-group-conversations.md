---
title: Conversas em canal e em grupo
author: clearab
description: Como enviar, receber e lidar com mensagens de um bot em um canal ou em um chat de grupo.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: ccc27d7638820cfa3c2b7cfe12b91b3a3a9fef1d
ms.sourcegitcommit: 61c93b22490526b1de87c0b14a3c7eb6e046caf6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2020
ms.locfileid: "44800998"
---
# <a name="channel-and-group-chat-conversations-with-a-microsoft-teams-bot"></a>Conversas de chat de grupo e canal com um bot do Microsoft Teams

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Ao adicionar o `teams` `groupchat` escopo ou ao bot, ele pode estar disponível para ser instalado em uma equipe ou em um chat de grupo. Isso permite que todos os membros da conversa interajam com o bot. Depois de instalado, ele também terá acesso aos metadados sobre a conversa como a lista de membros da conversa e, quando instalado em detalhes da equipe sobre essa equipe e a lista completa de canais.

Os bots em um grupo ou canal só recebem mensagens quando são mencionadas ("@botname"), elas não recebem nenhuma outra mensagem enviada à conversa.

> [!NOTE]
> O bot deve ser @mentioned diretamente. O bot não receberá uma mensagem quando a equipe ou canal for mencionado ou quando alguém responder a uma mensagem do bot sem @mentioning-la.

## <a name="design-considerations"></a>Considerações de design

Um bot deve fornecer informações apropriadas e relevantes a todos os membros em um grupo ou canal. Conversas com ela são visíveis para todas as pessoas que fazem parte do grupo ou canal. Um bot bem projetado pode adicionar valor a todos os usuários enquanto não compartilha inadvertidamente as informações mais apropriadas em uma conversa de um-para-um. Conversas multiturnas como caixas de diálogo devem ser evitadas-use cartões e/ou módulos de tarefas para coletar informações.

## <a name="creating-new-conversation-threads"></a>Criando novos threads de conversa

Quando o bot é instalado em uma equipe, às vezes, pode ser necessário criar um novo thread de conversa em vez de responder a um existente. Essa é uma forma de [mensagens pró-ativas](~/bots/how-to/conversations/send-proactive-messages.md).

## <a name="working-with-mentions"></a>Trabalhando com menção

Cada mensagem para o bot a partir de um grupo ou canal conterá um @mention com seu próprio nome no texto da mensagem, portanto, você precisará garantir que as alças de análise da mensagem. O bot também pode recuperar outros usuários mencionados em uma mensagem e adicionar menção a qualquer mensagem enviada.

### <a name="stripping-mentions-from-message-text"></a>Como retirar menção do texto da mensagem

Você pode achar necessário retirar o @mentions do texto da mensagem que seu bot recebe.

### <a name="retrieving-mentions"></a>Como recuperar menção

As menção são retornadas no `entities` objeto no Payload e contêm a identificação exclusiva do usuário e, na maioria dos casos, o nome do usuário mencionado. O texto da mensagem também incluirá a menção, como `<at>@John Smith<at>` . No entanto, você não deve confiar no texto da mensagem para recuperar as informações sobre o usuário; é possível que a pessoa que está enviando a mensagem a altere. Em vez disso, use o `entities` objeto.

Você pode recuperar todas as menção na mensagem chamando a `GetMentions` função no SDK do bot Builder, que retorna uma matriz de `Mention` objetos.

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

### <a name="adding-mentions-to-your-messages"></a>Adicionando menção às suas mensagens

O bot pode mencionar outros usuários em mensagens postadas em canais. Para fazer isso, sua mensagem deve fazer o seguinte:

O `Mention` objeto tem duas propriedades que você precisará definir:

* Incluir <at>@username</at> no texto da mensagem
* Incluir o objeto menção dentro da coleção Entities

O SDK da estrutura de bot fornece métodos e objetos auxiliares para facilitar a criação da menção.

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

O `text` campo no objeto na `entities` matriz deve corresponder *exatamente* a uma parte do `text` campo Message. Caso contrário, a menção será ignorada.

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

## <a name="sending-a-message-on-installation"></a>Enviando uma mensagem na instalação

Quando seu bot é adicionado ao grupo ou equipe, pode ser útil enviar uma mensagem introduzindo-a. A mensagem deve fornecer uma breve descrição dos recursos do bot e como usá-los. Você desejará inscrever-se no `conversationUpdate` evento com o `teamMemberAdded` EventType.  Como o evento é enviado quando um novo membro da equipe é adicionado, você precisa verificar se o novo membro adicionado é o bot. Consulte [Enviar uma mensagem de boas-vindas para um novo membro da equipe](~/bots/how-to/conversations/send-proactive-messages.md) para obter mais detalhes.

Você também pode querer enviar uma mensagem pessoal para cada membro da equipe quando o bot é adicionado. Para fazer isso, você pode obter a lista de equipes e enviar uma mensagem direta a cada usuário.

Não é recomendável enviar uma mensagem nas seguintes situações:

* A equipe é grande (obviamente subjetiva, mas por exemplo, mais de 100 membros). Seu bot pode ser visto como ' spam ' e a pessoa que o adicionou pode receber reclamações, a menos que você comunique claramente a proposta de valor do bot para todos os usuários que veem a mensagem de boas-vindas.
* Seu bot é mencionado pela primeira vez em um grupo ou canal (em vez de ser adicionado a uma equipe)
* Um grupo ou canal é renomeado
* Um membro da equipe é adicionado a um grupo ou canal

## <a name="learn-more"></a>Saiba mais

Seu bot tem acesso a informações adicionais sobre o bate-papo de grupo ou equipe em que ele está instalado. Veja [obter o contexto do Microsoft Teams](~/bots/how-to/get-teams-context.md) para APIs adicionais disponíveis para o bot.

Há também outros eventos que o seu bot pode assinar e responder. Consulte [inscrever-se em eventos de conversa](~/bots/how-to/conversations/subscribe-to-conversation-events.md) para saber como.

[!INCLUDE [sample](~/includes/bots/teams-bot-samples.md)]
