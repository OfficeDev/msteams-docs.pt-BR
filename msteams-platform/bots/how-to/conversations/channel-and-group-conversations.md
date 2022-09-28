---
title: Criar bots de conversa para chat em grupo ou canal
author: surbhigupta
description: Saiba como criar novos threads de conversa, trabalhar em menções e enviar mensagens na instalação. Explore o exemplo de upload de arquivo do Teams (.NET, JavaScript, Python).
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: anclear
ms.openlocfilehash: 18af255a8d0975878865b101b8787422d5cfa3d5
ms.sourcegitcommit: 75d0072c021609af33ce584d671f610d78b3aaef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2022
ms.locfileid: "68100599"
---
# <a name="channel-and-group-chat-conversations-with-a-bot"></a>Canais e conversas de chat em grupo com um bot do Microsoft Teams

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Para instalar o bot do Microsoft Teams em uma equipe ou chat em grupo, adicione o escopo `teams` ou `groupchat` ao seu bot. Isso permite que todos os membros da conversa interajam com o seu bot. Depois que o bot é instalado, ele tem acesso aos metadados sobre a conversa, como a lista de membros da conversa. Além disso, quando ele é instalado em uma equipe, o bot tem acesso a detalhes sobre essa equipe e a lista completa de canais.

Os bots em um grupo ou canal só recebem mensagens quando são mencionados @botname. Eles não recebem nenhuma outra mensagem enviada para a conversa. O bot deve ser @mencionado diretamente. O bot não recebe uma mensagem quando a equipe ou canal é mencionado ou quando alguém responde a uma mensagem do bot sem @mentioning ela.

> [!NOTE]
> No momento, esse recurso está disponível somente em [visualização pública do desenvolvedor](../../../resources/dev-preview/developer-preview-intro.md).
>
> Usando o RSC (consentimento específico do recurso), os bots podem receber todas as mensagens de canal nas equipes em que estão instalados sem serem @mentioned. Para obter mais informações, confira [receber todas as mensagens de canal com o RSC](channel-messages-with-rsc.md).
>
> No momento, não há suporte para postar uma mensagem ou um cartão adaptável em um canal privado.

Confira o vídeo a seguir para saber mais sobre conversas de chat em grupo e canal com um bot:
<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4NzEs]
<br>

## <a name="design-guidelines"></a>Diretrizes de design

Ao contrário do que ocorre em chats pessoais, seu bot deve fornecer uma introdução rápida em chats e canais em grupo. Você deve seguir essas e mais diretrizes de design de bot. Para obter mais informações sobre como projetar bots no Teams, confira [como projetar conversas de bot em canais e chats](~/bots/design/bots.md).

Agora, você pode criar novas threads de conversa e gerenciar facilmente diferentes conversas nos canais.

## <a name="create-new-conversation-threads"></a>Crie novas threads de conversa

Quando o bot é instalado em uma equipe, você deve criar uma nova thread de conversa em vez de responder a uma existente. Às vezes, é difícil diferenciar entre duas conversas. Se a conversa estiver encadeada, será mais fácil organizar e gerenciar diferentes conversas em canais. Essa é uma forma de [mensagens proativas](~/bots/how-to/conversations/send-proactive-messages.md).

Em seguida, recupere as menções usando o objeto `entities` e adicione menções às suas mensagens usando o objeto `Mention`.

## <a name="work-with-mentions"></a>Trabalhe com menções

Cada mensagem para o bot de um grupo ou canal contém uma @menção com seu nome no texto da mensagem. Seu bot também pode recuperar outros usuários mencionados em uma mensagem e adicionar menções a quaisquer mensagens que enviar.

Você também deve remover as @menções do conteúdo da mensagem que seu bot recebe.

### <a name="retrieve-mentions"></a>Recupere menções

As menções são retornadas no objeto `entities` do conteúdo e contêm a ID exclusiva do usuário e o nome do usuário mencionado. O texto da mensagem também inclui a menção, como `<at>@John Smith<at>`. No entanto, não dependa do texto na mensagem para recuperar informações sobre o usuário. É possível que a pessoa que envia a mensagem a altere. Portanto, use o objeto `entities`.

Você pode recuperar todas as menções na mensagem chamando a função `GetMentions` no SDK Bot Builder, que retorna uma matriz de objetos `Mention`.

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

### <a name="add-mentions-to-your-messages"></a>Adicione menções às suas mensagens

Seu bot pode mencionar outros usuários em mensagens postadas nos canais.

O objeto `Mention` tem duas propriedades que você deve definir usando o seguinte:

* Inclua *@nome de usuário* no texto da mensagem.
* Inclua o objeto de menção na coleção de entidades.

O SDK do Bot Framework fornece métodos auxiliares e objetos para criar menções.

O código a seguir mostra um exemplo de como adicionar menções às suas mensagens:

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

O campo `text` no objeto da matriz `entities` deve corresponder a uma parte do campo `text` da mensagem. Caso contrário, a menção será ignorada.

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

Quando o bot é adicionado pela primeira vez ao grupo ou à equipe, uma mensagem de introdução deve ser enviada. A mensagem deve fornecer uma breve descrição dos recursos do bot e como usá-los. Você deve assinar o evento `conversationUpdate` com o eventType `teamMemberAdded`.  O evento é enviado quando qualquer novo membro da equipe for adicionado. Verifique se o novo membro adicionado é o bot. Para obter mais informações, confira [enviar uma mensagem de boas-vindas a um novo membro da equipe](~/bots/how-to/conversations/send-proactive-messages.md).

Você pode enviar uma mensagem pessoal para cada membro da equipe quando o bot for adicionado. Para fazer isso, [busque a lista de participantes da equipe](../../../resources/bot-v3/bots-context.md#fetch-the-team-roster) e envie uma mensagem [direta a cada usuário](../../../resources/bot-v3/bot-conversations/bots-conv-proactive.md).

>[!NOTE]
> Verifique se a mensagem enviada pelo bot é relevante e agrega valor à mensagem inicial e não faz spam para os usuários.

Não envie uma mensagem nos seguintes casos:

* Quando a equipe é grande, por exemplo, maior que 100 membros. Seu bot pode ser visto como spam e a pessoa que o adicionou pode receber reclamações. Você deve comunicar claramente a proposta de valor do bot para todos que veem a mensagem de boas-vindas.
* Seu bot é mencionado primeiro em um grupo ou canal em vez de ser adicionado primeiramente a uma equipe.
* Um grupo ou canal é renomeado.
* Um membro da equipe é adicionado a um grupo ou canal.

[!INCLUDE [sample](~/includes/bots/teams-bot-samples.md)]

## <a name="step-by-step-guide"></a>Guias passo a passo

Siga o [guia passo a passo](../../../sbs-teams-conversation-bot.yml), para criar um bot de conversa do Teams.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Inscreva-se em eventos de conversa](~/bots/how-to/conversations/subscribe-to-conversation-events.md)

## <a name="see-also"></a>Confira também

* [Obter contexto do Teams](~/bots/how-to/get-teams-context.md)
* [Criar um canal privado em nome do usuário](/graph/api/channel-post#example-2-create-private-channel-on-behalf-of-user)
* [Conectar um bot ao Webchat canal](/azure/bot-service/bot-service-channel-connect-webchat)
