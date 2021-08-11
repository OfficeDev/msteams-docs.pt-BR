---
title: Conversas de canal e grupo com um bot
author: surbhigupta
description: Como enviar, receber e manipular mensagens para um bot em um chat de canal ou grupo.
ms.topic: conceptual
localization_priority: Normal
ms.author: anclear
ms.openlocfilehash: 8ff89cf88bf56a905bdf507e1bc6e4ebbbd691f70d94289c8e206024c5657fa9
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2021
ms.locfileid: "57708410"
---
# <a name="channel-and-group-chat-conversations-with-a-bot"></a>Conversas de chat de canal e grupo com um bot

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Para instalar o Microsoft Teams em um chat de equipe ou grupo, adicione `teams` o escopo ou ao `groupchat` bot. Isso permite que todos os membros da conversa interajam com o seu bot. Depois que o bot é instalado, ele tem acesso a metadados sobre a conversa, como a lista de membros da conversa. Além disso, quando ele é instalado em uma equipe, o bot tem acesso a detalhes sobre essa equipe e a lista completa de canais.

Os bots em um grupo ou canal só recebem mensagens quando são mencionados @botname. Eles não recebem outras mensagens enviadas para a conversa. O bot deve ser @mencionado diretamente. Seu bot não recebe uma mensagem quando a equipe ou canal é mencionado ou quando alguém responde a uma mensagem de seu bot sem @mentioning-la.

> [!NOTE]
> Esse recurso está disponível apenas na [visualização de desenvolvedor](../../../resources/dev-preview/developer-preview-intro.md) público.
>
> Usando o RSC (consentimento específico do recurso), os bots podem receber todas as mensagens de canal em equipes em que ele está instalado sem @mentioned. Para obter mais informações, [consulte receive all channel messages with RSC](channel-messages-with-rsc.md).

## <a name="design-guidelines"></a>Diretrizes de design

Ao contrário de chats pessoais, em chats em grupo e canais, seu bot deve fornecer uma introdução rápida. Você deve seguir essas e mais diretrizes de design de bot. Para obter mais informações sobre como projetar bots em Teams, consulte como projetar conversas [de bot em canais e chats.](~/bots/design/bots.md)

Agora, você pode criar novos threads de conversa e gerenciar facilmente diferentes conversas em canais.

## <a name="create-new-conversation-threads"></a>Criar novos threads de conversa

Quando o bot é instalado em uma equipe, você deve criar um novo thread de conversa em vez de responder a um existente. Às vezes, é difícil diferenciar entre duas conversas. Se a conversa for encadeada, é mais fácil organizar e gerenciar diferentes conversas em canais. Essa é uma forma de mensagens [proativas.](~/bots/how-to/conversations/send-proactive-messages.md)

Em seguida, você pode recuperar menções usando o objeto e adicionar menções às `entities` suas mensagens usando o `Mention` objeto.

## <a name="work-with-mentions"></a>Trabalhar com menções

Cada mensagem para seu bot de um grupo ou canal contém um @mention com seu nome no texto da mensagem. Seu bot também pode recuperar outros usuários mencionados em uma mensagem e adicionar menções a todas as mensagens enviadas.

Você também deve retirar o @mentions do conteúdo da mensagem que seu bot recebe.

### <a name="retrieve-mentions"></a>Recuperar menções

As menções são retornadas no objeto em carga e contêm a ID exclusiva do usuário e o `entities` nome do usuário mencionado. O texto da mensagem também inclui a menção, como `<at>@John Smith<at>` . No entanto, não confie no texto na mensagem para recuperar qualquer informação sobre o usuário. É possível que a pessoa que envia a mensagem a altere. Portanto, use o `entities` objeto.

Você pode recuperar todas as menções na mensagem chamando a função no SDK do Construtor de `GetMentions` Bots, que retorna uma matriz de `Mention` objetos.

O código a seguir mostra um exemplo de recuperação de menções:

# <a name="c"></a>[C#](#tab/dotnet)

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

# <a name="typescript"></a>[TypeScript](#tab/typescript)

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

### <a name="add-mentions-to-your-messages"></a>Adicionar menções às suas mensagens

Seu bot pode mencionar outros usuários em mensagens postadas em canais.

O `Mention` objeto tem duas propriedades que você deve definir usando o seguinte:

* Inclua <at>@username</at> no texto da mensagem.
* Inclua o objeto mention dentro da coleção de entidades.

O SDK da Estrutura de Bot fornece métodos e objetos auxiliares para criar menções.

O código a seguir mostra um exemplo de adição de menções às suas mensagens:

# <a name="c"></a>[C#](#tab/dotnet)

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

# <a name="typescript"></a>[TypeScript](#tab/typescript)

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

O `text` campo no objeto na matriz deve corresponder a uma parte do campo de `entities` `text` mensagem. Se isso não acontecer, a menção será ignorada.

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

Agora você pode enviar uma mensagem de introdução quando o bot for instalado pela primeira vez ou adicionado a um grupo ou equipe.

## <a name="send-a-message-on-installation"></a>Enviar uma mensagem na instalação

Quando o bot é adicionado pela primeira vez ao grupo ou à equipe, uma mensagem de introdução deve ser enviada. A mensagem deve fornecer uma breve descrição dos recursos do bot e como usá-los. Você deve se inscrever no `conversationUpdate` evento com `teamMemberAdded` o eventType.  O evento é enviado quando qualquer novo membro da equipe é adicionado. Verifique se o novo membro adicionado é o bot. Para obter mais informações, consulte [enviando uma mensagem de boas-vindas a um novo membro da equipe](~/bots/how-to/conversations/send-proactive-messages.md).

Envie uma mensagem pessoal para cada membro da equipe quando o bot for adicionado. Para fazer isso, receba a lista de equipe e envie uma mensagem direta a cada usuário.

Não envie uma mensagem nos seguintes casos:

* A equipe é grande, por exemplo, maior do que 100 membros. Seu bot pode ser visto como spam e a pessoa que o adicionou pode receber reclamações. Você deve comunicar claramente a proposta de valor do bot a todos que veem a mensagem de boas-vindas.
* Seu bot é mencionado pela primeira vez em um grupo ou canal em vez de ser adicionado pela primeira vez a uma equipe.
* Um grupo ou canal é renomeado.
* Um membro da equipe é adicionado a um grupo ou canal.

[!INCLUDE [sample](~/includes/bots/teams-bot-samples.md)]

## <a name="see-also"></a>Confira também

[Obter Teams contexto](~/bots/how-to/get-teams-context.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Inscreva-se em eventos de conversa](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
