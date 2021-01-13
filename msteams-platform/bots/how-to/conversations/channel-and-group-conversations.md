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
# <a name="channel-and-group-chat-conversations-with-a-microsoft-teams-bot"></a><span data-ttu-id="92a62-103">Conversas de canal e chat em grupo com um bot do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="92a62-103">Channel and group chat conversations with a Microsoft Teams bot</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="92a62-104">Ao adicionar o ou escopo ao seu bot, ele pode estar disponível para ser instalado em um chat de equipe `teams` `groupchat` ou grupo.</span><span class="sxs-lookup"><span data-stu-id="92a62-104">By adding the `teams` or `groupchat` scope to your bot, it can be available to be installed in a team or group chat.</span></span> <span data-ttu-id="92a62-105">Isso permite que todos os membros da conversa interajam com seu bot.</span><span class="sxs-lookup"><span data-stu-id="92a62-105">This allows all members of the conversation to interact with your bot.</span></span> <span data-ttu-id="92a62-106">Uma vez instalado, ele também terá acesso a metadados sobre a conversa, como a lista de membros da conversa e quando instalado em detalhes de uma equipe sobre essa equipe e a lista completa de canais.</span><span class="sxs-lookup"><span data-stu-id="92a62-106">Once installed, it will also have access to metadata about the conversation like the list of conversation members, and when installed in a team details about that team and the full list of channels.</span></span>

<span data-ttu-id="92a62-107">Os bots em um grupo ou canal só recebem mensagens quando são mencionados (@botname), eles não recebem nenhuma outra mensagem enviada para a conversa.</span><span class="sxs-lookup"><span data-stu-id="92a62-107">Bots in a group or channel only receive messages when they are mentioned (@botname), they do not receive any other messages sent to the conversation.</span></span>

> [!NOTE]
> <span data-ttu-id="92a62-108">O bot deve ser @mentioned diretamente.</span><span class="sxs-lookup"><span data-stu-id="92a62-108">The bot must be @mentioned directly.</span></span> <span data-ttu-id="92a62-109">Seu bot não receberá uma mensagem quando a equipe ou o canal for mencionado, ou quando alguém responder a uma mensagem do seu bot sem @mentioning-la.</span><span class="sxs-lookup"><span data-stu-id="92a62-109">Your bot will not receive a message when the team or channel is mentioned, or when someone replies to a message from your bot without @mentioning it.</span></span>

## <a name="design-guidelines"></a><span data-ttu-id="92a62-110">Diretrizes de design</span><span class="sxs-lookup"><span data-stu-id="92a62-110">Design guidelines</span></span>

<span data-ttu-id="92a62-111">Veja como projetar [conversas de bot em canais e chats.](~/bots/design/bots.md)</span><span class="sxs-lookup"><span data-stu-id="92a62-111">See how to [design bot conversations in channels and chats](~/bots/design/bots.md).</span></span>

## <a name="creating-new-conversation-threads"></a><span data-ttu-id="92a62-112">Criando novos threads de conversa</span><span class="sxs-lookup"><span data-stu-id="92a62-112">Creating new conversation threads</span></span>

<span data-ttu-id="92a62-113">Quando o bot é instalado em uma equipe, às vezes pode ser necessário criar um novo thread de conversa em vez de responder a um já existente.</span><span class="sxs-lookup"><span data-stu-id="92a62-113">When your bot is installed in a team, it can sometimes be necessary to create a new conversation thread rather than replying to an existing one.</span></span> <span data-ttu-id="92a62-114">Essa é uma forma de mensagens [proativas.](~/bots/how-to/conversations/send-proactive-messages.md)</span><span class="sxs-lookup"><span data-stu-id="92a62-114">This is a form of [proactive messaging](~/bots/how-to/conversations/send-proactive-messages.md).</span></span>

## <a name="working-with-mentions"></a><span data-ttu-id="92a62-115">Trabalhar com menções</span><span class="sxs-lookup"><span data-stu-id="92a62-115">Working with mentions</span></span>

<span data-ttu-id="92a62-116">Cada mensagem para o bot de um grupo ou canal conterá um @mention com seu próprio nome no texto da mensagem, portanto, você precisará garantir que a análise de mensagens lidará com isso.</span><span class="sxs-lookup"><span data-stu-id="92a62-116">Every message to your bot from a group or channel will contain an @mention with its own name in the message text, so you'll need to ensure your message parsing handles that.</span></span> <span data-ttu-id="92a62-117">Seu bot também pode recuperar outros usuários mencionados em uma mensagem e adicionar menções a qualquer mensagem enviada.</span><span class="sxs-lookup"><span data-stu-id="92a62-117">Your bot can also retrieve other users mentioned in a message, and add mentions to any messages it sends.</span></span>

### <a name="stripping-mentions-from-message-text"></a><span data-ttu-id="92a62-118">Menções de remoção do texto da mensagem</span><span class="sxs-lookup"><span data-stu-id="92a62-118">Stripping mentions from message text</span></span>

<span data-ttu-id="92a62-119">Você pode achar necessário retirar a @mentions do texto da mensagem que seu bot recebe.</span><span class="sxs-lookup"><span data-stu-id="92a62-119">You may find it necessary to strip out the @mentions from the text of the message your bot receives.</span></span>

### <a name="retrieving-mentions"></a><span data-ttu-id="92a62-120">Recuperando menções</span><span class="sxs-lookup"><span data-stu-id="92a62-120">Retrieving mentions</span></span>

<span data-ttu-id="92a62-121">As menções são retornadas no objeto na carga e contêm a ID exclusiva do usuário e, na maioria dos casos, o nome `entities` do usuário mencionado.</span><span class="sxs-lookup"><span data-stu-id="92a62-121">Mentions are returned in the `entities` object in payload and contain both the unique ID of the user and, in most cases, the name of user mentioned.</span></span> <span data-ttu-id="92a62-122">O texto da mensagem também incluirá a menção como `<at>@John Smith<at>` .</span><span class="sxs-lookup"><span data-stu-id="92a62-122">The text of the message will also include the mention like `<at>@John Smith<at>`.</span></span> <span data-ttu-id="92a62-123">No entanto, você não deve confiar no texto na mensagem para recuperar qualquer informação sobre o usuário; é possível para a pessoa que está enviando a mensagem alterá-la.</span><span class="sxs-lookup"><span data-stu-id="92a62-123">However, you should not rely on the text in the message to retrieve any information about the user; it is possible for the person sending the message to alter it.</span></span> <span data-ttu-id="92a62-124">Em vez disso, use o `entities` objeto.</span><span class="sxs-lookup"><span data-stu-id="92a62-124">Instead, use the `entities` object.</span></span>

<span data-ttu-id="92a62-125">Você pode recuperar todas as menções na mensagem chamando a função no SDK do Construtor de `GetMentions` Bots, que retorna uma matriz de `Mention` objetos.</span><span class="sxs-lookup"><span data-stu-id="92a62-125">You can retrieve all mentions in the message by calling the `GetMentions` function in the Bot Builder SDK which returns an array of `Mention` objects.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="92a62-126">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="92a62-126">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="92a62-127">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="92a62-127">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="92a62-128">JSON</span><span class="sxs-lookup"><span data-stu-id="92a62-128">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="92a62-129">Python</span><span class="sxs-lookup"><span data-stu-id="92a62-129">Python</span></span>](#tab/python)

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

### <a name="adding-mentions-to-your-messages"></a><span data-ttu-id="92a62-130">Adicionando menções às suas mensagens</span><span class="sxs-lookup"><span data-stu-id="92a62-130">Adding mentions to your messages</span></span>

<span data-ttu-id="92a62-131">Seu bot pode mencionar outros usuários em mensagens postadas em canais.</span><span class="sxs-lookup"><span data-stu-id="92a62-131">Your bot can mention other users in messages posted into channels.</span></span> <span data-ttu-id="92a62-132">Para fazer isso, sua mensagem deve fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="92a62-132">To do this, your message must do the following:</span></span>

<span data-ttu-id="92a62-133">O `Mention` objeto tem duas propriedades que você precisará definir:</span><span class="sxs-lookup"><span data-stu-id="92a62-133">The `Mention` object has two properties that you will need to set:</span></span>

* <span data-ttu-id="92a62-134">Incluir <at>@username</at> no texto da mensagem</span><span class="sxs-lookup"><span data-stu-id="92a62-134">Include <at>@username</at> in the message text</span></span>
* <span data-ttu-id="92a62-135">Incluir o objeto mention dentro da coleção de entidades</span><span class="sxs-lookup"><span data-stu-id="92a62-135">Include the mention object inside the entities collection</span></span>

<span data-ttu-id="92a62-136">O SDK da Estrutura do Bot fornece métodos e objetos auxiliares para facilitar a construção da menção.</span><span class="sxs-lookup"><span data-stu-id="92a62-136">The Bot Framework SDK provides helper methods and objects to make constructing the mention easier.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="92a62-137">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="92a62-137">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="92a62-138">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="92a62-138">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="92a62-139">JSON</span><span class="sxs-lookup"><span data-stu-id="92a62-139">JSON</span></span>](#tab/json)

<span data-ttu-id="92a62-140">O campo no objeto na matriz deve corresponder `text` exatamente a uma parte do campo de `entities`  `text` mensagem.</span><span class="sxs-lookup"><span data-stu-id="92a62-140">The `text` field in the object in the `entities` array must *exactly* match a portion of the message `text` field.</span></span> <span data-ttu-id="92a62-141">Se não o fizer, a menção será ignorada.</span><span class="sxs-lookup"><span data-stu-id="92a62-141">If it does not, the mention will be ignored.</span></span>

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

# <a name="python"></a>[<span data-ttu-id="92a62-142">Python</span><span class="sxs-lookup"><span data-stu-id="92a62-142">Python</span></span>](#tab/python)

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

## <a name="sending-a-message-on-installation"></a><span data-ttu-id="92a62-143">Enviar uma mensagem na instalação</span><span class="sxs-lookup"><span data-stu-id="92a62-143">Sending a message on installation</span></span>

<span data-ttu-id="92a62-144">Quando seu bot é adicionado pela primeira vez ao grupo ou equipe, pode ser útil enviar uma mensagem apresentando-o.</span><span class="sxs-lookup"><span data-stu-id="92a62-144">When your bot is first added to the group or team, it may be useful to send a message introducing it.</span></span> <span data-ttu-id="92a62-145">A mensagem deve fornecer uma breve descrição dos recursos do bot e como usá-los.</span><span class="sxs-lookup"><span data-stu-id="92a62-145">The message should provide a brief description of the bot's features, and how to use them.</span></span> <span data-ttu-id="92a62-146">Você vai querer se inscrever no `conversationUpdate` evento, com `teamMemberAdded` o eventType.</span><span class="sxs-lookup"><span data-stu-id="92a62-146">You'll want to subscribe to the `conversationUpdate` event, with the `teamMemberAdded` eventType.</span></span>  <span data-ttu-id="92a62-147">Como o evento é enviado quando um novo membro da equipe é adicionado, você precisa verificar se o novo membro adicionado é o bot.</span><span class="sxs-lookup"><span data-stu-id="92a62-147">Since the event is sent when any new team member is added, you need to check to determine if the new member added is the bot.</span></span> <span data-ttu-id="92a62-148">Confira [Enviar uma mensagem de boas-vindas para um novo membro da equipe](~/bots/how-to/conversations/send-proactive-messages.md) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="92a62-148">See [Sending a welcome message to a new team member](~/bots/how-to/conversations/send-proactive-messages.md) for more details.</span></span>

<span data-ttu-id="92a62-149">Você também pode querer enviar uma mensagem pessoal para cada membro da equipe quando o bot for adicionado.</span><span class="sxs-lookup"><span data-stu-id="92a62-149">You might also want to send a personal message to each member of the team when the bot is added.</span></span> <span data-ttu-id="92a62-150">Para fazer isso, você pode obter a lista de participação da equipe e enviar uma mensagem direta a cada usuário.</span><span class="sxs-lookup"><span data-stu-id="92a62-150">To do this, you could get the team roster and send each user a direct message.</span></span>

<span data-ttu-id="92a62-151">Não é recomendável enviar uma mensagem nas seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="92a62-151">It is not recommended to send a message in the following situations:</span></span>

* <span data-ttu-id="92a62-152">A equipe é grande (obviamente inentente, mas, por exemplo, maior do que 100 membros).</span><span class="sxs-lookup"><span data-stu-id="92a62-152">The team is large (obviously subjective, but for example larger than 100 members).</span></span> <span data-ttu-id="92a62-153">Seu bot pode ser visto como "spammy" e a pessoa que o adicionou poderá receber reclamações, a menos que você comunique claramente a proposta de valor do bot para todos que veem a mensagem de boas-vindas.</span><span class="sxs-lookup"><span data-stu-id="92a62-153">Your bot may be seen as 'spammy' and the person who added it may get complaints unless you clearly communicate your bot's value proposition to everyone who sees the welcome message.</span></span>
* <span data-ttu-id="92a62-154">Seu bot é mencionado pela primeira vez em um grupo ou canal (em vez de ser adicionado pela primeira vez a uma equipe)</span><span class="sxs-lookup"><span data-stu-id="92a62-154">Your bot is first mentioned in a group or channel (versus being first added to a team)</span></span>
* <span data-ttu-id="92a62-155">Um grupo ou canal é renomeado</span><span class="sxs-lookup"><span data-stu-id="92a62-155">A group or channel is renamed</span></span>
* <span data-ttu-id="92a62-156">Um membro da equipe é adicionado a um grupo ou canal</span><span class="sxs-lookup"><span data-stu-id="92a62-156">A team member is added to a group or channel</span></span>

## <a name="learn-more"></a><span data-ttu-id="92a62-157">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="92a62-157">Learn more</span></span>

<span data-ttu-id="92a62-158">Seu bot tem acesso a informações adicionais sobre o chat em grupo ou a equipe em que está instalado.</span><span class="sxs-lookup"><span data-stu-id="92a62-158">Your bot has access to additional information about the group chat or team it is installed in.</span></span> <span data-ttu-id="92a62-159">Confira [o contexto de equipes](~/bots/how-to/get-teams-context.md) para APIs adicionais disponíveis para seu bot.</span><span class="sxs-lookup"><span data-stu-id="92a62-159">See [get teams context](~/bots/how-to/get-teams-context.md) for additional APIs available for your bot.</span></span>

<span data-ttu-id="92a62-160">Também há eventos adicionais que seu bot pode se inscrever e responder.</span><span class="sxs-lookup"><span data-stu-id="92a62-160">There are also additional events that your bot can subscribe and respond to.</span></span> <span data-ttu-id="92a62-161">Confira [se inscrever em eventos de conversa](~/bots/how-to/conversations/subscribe-to-conversation-events.md) para saber como.</span><span class="sxs-lookup"><span data-stu-id="92a62-161">See [subscribe to conversation events](~/bots/how-to/conversations/subscribe-to-conversation-events.md) to learn how.</span></span>

[!INCLUDE [sample](~/includes/bots/teams-bot-samples.md)]
