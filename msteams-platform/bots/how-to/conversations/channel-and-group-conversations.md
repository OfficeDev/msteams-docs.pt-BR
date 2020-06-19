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
# <a name="channel-and-group-chat-conversations-with-a-microsoft-teams-bot"></a><span data-ttu-id="e4bc4-103">Conversas de chat de grupo e canal com um bot do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="e4bc4-103">Channel and Group chat conversations with a Microsoft Teams bot</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="e4bc4-104">Ao adicionar o `teams` `groupchat` escopo ou ao bot, ele pode estar disponível para ser instalado em uma equipe ou em um chat de grupo.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-104">By adding the `teams` or `groupchat` scope to your bot, it can be available to be installed in a team or group chat.</span></span> <span data-ttu-id="e4bc4-105">Isso permite que todos os membros da conversa interajam com o bot.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-105">This allows all members of the conversation to interact with your bot.</span></span> <span data-ttu-id="e4bc4-106">Depois de instalado, ele também terá acesso aos metadados sobre a conversa como a lista de membros da conversa e, quando instalado em detalhes da equipe sobre essa equipe e a lista completa de canais.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-106">Once installed, it will also have access to metadata about the conversation like the list of conversation members, and when installed in a team details about that team and the full list of channels.</span></span>

<span data-ttu-id="e4bc4-107">Os bots em um grupo ou canal só recebem mensagens quando são mencionadas ("@botname"), elas não recebem nenhuma outra mensagem enviada à conversa.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-107">Bots in a group or channel only receive messages when they are mentioned ("@botname"), they do not receive any other messages sent to the conversation.</span></span>

> [!NOTE]
> <span data-ttu-id="e4bc4-108">O bot deve ser @mentioned diretamente.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-108">The bot must be @mentioned directly.</span></span> <span data-ttu-id="e4bc4-109">O bot não receberá uma mensagem quando a equipe ou canal for mencionado ou quando alguém responder a uma mensagem do bot sem @mentioning-la.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-109">Your bot will not receive a message when the team or channel is mentioned, or when someone replies to a message from your bot without @mentioning it.</span></span>

## <a name="design-considerations"></a><span data-ttu-id="e4bc4-110">Considerações de design</span><span class="sxs-lookup"><span data-stu-id="e4bc4-110">Design considerations</span></span>

<span data-ttu-id="e4bc4-111">Um bot deve fornecer informações apropriadas e relevantes a todos os membros em um grupo ou canal.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-111">A bot should provide information that is both appropriate and relevant to all members in a group or channel.</span></span> <span data-ttu-id="e4bc4-112">Conversas com ela são visíveis para todas as pessoas que fazem parte do grupo ou canal.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-112">Conversations with it are visible to everyone that is a part of the group or channel.</span></span> <span data-ttu-id="e4bc4-113">Um bot bem projetado pode adicionar valor a todos os usuários enquanto não compartilha inadvertidamente as informações mais apropriadas em uma conversa de um-para-um.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-113">A well designed bot can add value to all users while not inadvertently sharing information that is more appropriate in a one-to-one conversation.</span></span> <span data-ttu-id="e4bc4-114">Conversas multiturnas como caixas de diálogo devem ser evitadas-use cartões e/ou módulos de tarefas para coletar informações.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-114">Multi-turn conversations like dialogs should be avoided - use cards and/or task modules to collect information instead.</span></span>

## <a name="creating-new-conversation-threads"></a><span data-ttu-id="e4bc4-115">Criando novos threads de conversa</span><span class="sxs-lookup"><span data-stu-id="e4bc4-115">Creating new conversation threads</span></span>

<span data-ttu-id="e4bc4-116">Quando o bot é instalado em uma equipe, às vezes, pode ser necessário criar um novo thread de conversa em vez de responder a um existente.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-116">When your bot is installed in a team, it can sometimes be necessary to create a new conversation thread rather than replying to an existing one.</span></span> <span data-ttu-id="e4bc4-117">Essa é uma forma de [mensagens pró-ativas](~/bots/how-to/conversations/send-proactive-messages.md).</span><span class="sxs-lookup"><span data-stu-id="e4bc4-117">This is a form of [proactive messaging](~/bots/how-to/conversations/send-proactive-messages.md).</span></span>

## <a name="working-with-mentions"></a><span data-ttu-id="e4bc4-118">Trabalhando com menção</span><span class="sxs-lookup"><span data-stu-id="e4bc4-118">Working with mentions</span></span>

<span data-ttu-id="e4bc4-119">Cada mensagem para o bot a partir de um grupo ou canal conterá um @mention com seu próprio nome no texto da mensagem, portanto, você precisará garantir que as alças de análise da mensagem.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-119">Every message to your bot from a group or channel will contain an @mention with its own name in the message text, so you'll need to ensure your message parsing handles that.</span></span> <span data-ttu-id="e4bc4-120">O bot também pode recuperar outros usuários mencionados em uma mensagem e adicionar menção a qualquer mensagem enviada.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-120">Your bot can also retrieve other users mentioned in a message, and add mentions to any messages it sends.</span></span>

### <a name="stripping-mentions-from-message-text"></a><span data-ttu-id="e4bc4-121">Como retirar menção do texto da mensagem</span><span class="sxs-lookup"><span data-stu-id="e4bc4-121">Stripping mentions from message text</span></span>

<span data-ttu-id="e4bc4-122">Você pode achar necessário retirar o @mentions do texto da mensagem que seu bot recebe.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-122">You may find it necessary to strip out the @mentions from the text of the message your bot receives.</span></span>

### <a name="retrieving-mentions"></a><span data-ttu-id="e4bc4-123">Como recuperar menção</span><span class="sxs-lookup"><span data-stu-id="e4bc4-123">Retrieving mentions</span></span>

<span data-ttu-id="e4bc4-124">As menção são retornadas no `entities` objeto no Payload e contêm a identificação exclusiva do usuário e, na maioria dos casos, o nome do usuário mencionado.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-124">Mentions are returned in the `entities` object in payload and contain both the unique ID of the user and, in most cases, the name of user mentioned.</span></span> <span data-ttu-id="e4bc4-125">O texto da mensagem também incluirá a menção, como `<at>@John Smith<at>` .</span><span class="sxs-lookup"><span data-stu-id="e4bc4-125">The text of the message will also include the mention like `<at>@John Smith<at>`.</span></span> <span data-ttu-id="e4bc4-126">No entanto, você não deve confiar no texto da mensagem para recuperar as informações sobre o usuário; é possível que a pessoa que está enviando a mensagem a altere.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-126">However, you should not rely on the text in the message to retrieve any information about the user; it is possible for the person sending the message to alter it.</span></span> <span data-ttu-id="e4bc4-127">Em vez disso, use o `entities` objeto.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-127">Instead, use the `entities` object.</span></span>

<span data-ttu-id="e4bc4-128">Você pode recuperar todas as menção na mensagem chamando a `GetMentions` função no SDK do bot Builder, que retorna uma matriz de `Mention` objetos.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-128">You can retrieve all mentions in the message by calling the `GetMentions` function in the Bot Builder SDK which returns an array of `Mention` objects.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="e4bc4-129">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="e4bc4-129">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="e4bc4-130">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="e4bc4-130">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="e4bc4-131">JSON</span><span class="sxs-lookup"><span data-stu-id="e4bc4-131">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="e4bc4-132">Python</span><span class="sxs-lookup"><span data-stu-id="e4bc4-132">Python</span></span>](#tab/python)

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

### <a name="adding-mentions-to-your-messages"></a><span data-ttu-id="e4bc4-133">Adicionando menção às suas mensagens</span><span class="sxs-lookup"><span data-stu-id="e4bc4-133">Adding mentions to your messages</span></span>

<span data-ttu-id="e4bc4-134">O bot pode mencionar outros usuários em mensagens postadas em canais.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-134">Your bot can mention other users in messages posted into channels.</span></span> <span data-ttu-id="e4bc4-135">Para fazer isso, sua mensagem deve fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e4bc4-135">To do this, your message must do the following:</span></span>

<span data-ttu-id="e4bc4-136">O `Mention` objeto tem duas propriedades que você precisará definir:</span><span class="sxs-lookup"><span data-stu-id="e4bc4-136">The `Mention` object has two properties that you will need to set:</span></span>

* <span data-ttu-id="e4bc4-137">Incluir <at>@username</at> no texto da mensagem</span><span class="sxs-lookup"><span data-stu-id="e4bc4-137">Include <at>@username</at> in the message text</span></span>
* <span data-ttu-id="e4bc4-138">Incluir o objeto menção dentro da coleção Entities</span><span class="sxs-lookup"><span data-stu-id="e4bc4-138">Include the mention object inside the entities collection</span></span>

<span data-ttu-id="e4bc4-139">O SDK da estrutura de bot fornece métodos e objetos auxiliares para facilitar a criação da menção.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-139">The Bot Framework SDK provides helper methods and objects to make constructing the mention easier.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="e4bc4-140">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="e4bc4-140">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="e4bc4-141">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="e4bc4-141">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="e4bc4-142">JSON</span><span class="sxs-lookup"><span data-stu-id="e4bc4-142">JSON</span></span>](#tab/json)

<span data-ttu-id="e4bc4-143">O `text` campo no objeto na `entities` matriz deve corresponder *exatamente* a uma parte do `text` campo Message.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-143">The `text` field in the object in the `entities` array must *exactly* match a portion of the message `text` field.</span></span> <span data-ttu-id="e4bc4-144">Caso contrário, a menção será ignorada.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-144">If it does not, the mention will be ignored.</span></span>

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

# <a name="python"></a>[<span data-ttu-id="e4bc4-145">Python</span><span class="sxs-lookup"><span data-stu-id="e4bc4-145">Python</span></span>](#tab/python)

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

## <a name="sending-a-message-on-installation"></a><span data-ttu-id="e4bc4-146">Enviando uma mensagem na instalação</span><span class="sxs-lookup"><span data-stu-id="e4bc4-146">Sending a message on installation</span></span>

<span data-ttu-id="e4bc4-147">Quando seu bot é adicionado ao grupo ou equipe, pode ser útil enviar uma mensagem introduzindo-a.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-147">When your bot is first added to the group or team, it may be useful to send a message introducing it.</span></span> <span data-ttu-id="e4bc4-148">A mensagem deve fornecer uma breve descrição dos recursos do bot e como usá-los.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-148">The message should provide a brief description of the bot's features, and how to use them.</span></span> <span data-ttu-id="e4bc4-149">Você desejará inscrever-se no `conversationUpdate` evento com o `teamMemberAdded` EventType.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-149">You'll want to subscribe to the `conversationUpdate` event, with the `teamMemberAdded` eventType.</span></span>  <span data-ttu-id="e4bc4-150">Como o evento é enviado quando um novo membro da equipe é adicionado, você precisa verificar se o novo membro adicionado é o bot.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-150">Since the event is sent when any new team member is added, you need to check to determine if the new member added is the bot.</span></span> <span data-ttu-id="e4bc4-151">Consulte [Enviar uma mensagem de boas-vindas para um novo membro da equipe](~/bots/how-to/conversations/send-proactive-messages.md) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-151">See [Sending a welcome message to a new team member](~/bots/how-to/conversations/send-proactive-messages.md) for more details.</span></span>

<span data-ttu-id="e4bc4-152">Você também pode querer enviar uma mensagem pessoal para cada membro da equipe quando o bot é adicionado.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-152">You might also want to send a personal message to each member of the team when the bot is added.</span></span> <span data-ttu-id="e4bc4-153">Para fazer isso, você pode obter a lista de equipes e enviar uma mensagem direta a cada usuário.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-153">To do this, you could get the team roster and send each user a direct message.</span></span>

<span data-ttu-id="e4bc4-154">Não é recomendável enviar uma mensagem nas seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="e4bc4-154">It is not recommended to send a message in the following situations:</span></span>

* <span data-ttu-id="e4bc4-155">A equipe é grande (obviamente subjetiva, mas por exemplo, mais de 100 membros).</span><span class="sxs-lookup"><span data-stu-id="e4bc4-155">The team is large (obviously subjective, but for example larger than 100 members).</span></span> <span data-ttu-id="e4bc4-156">Seu bot pode ser visto como ' spam ' e a pessoa que o adicionou pode receber reclamações, a menos que você comunique claramente a proposta de valor do bot para todos os usuários que veem a mensagem de boas-vindas.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-156">Your bot may be seen as 'spammy' and the person who added it may get complaints unless you clearly communicate your bot's value proposition to everyone who sees the welcome message.</span></span>
* <span data-ttu-id="e4bc4-157">Seu bot é mencionado pela primeira vez em um grupo ou canal (em vez de ser adicionado a uma equipe)</span><span class="sxs-lookup"><span data-stu-id="e4bc4-157">Your bot is first mentioned in a group or channel (versus being first added to a team)</span></span>
* <span data-ttu-id="e4bc4-158">Um grupo ou canal é renomeado</span><span class="sxs-lookup"><span data-stu-id="e4bc4-158">A group or channel is renamed</span></span>
* <span data-ttu-id="e4bc4-159">Um membro da equipe é adicionado a um grupo ou canal</span><span class="sxs-lookup"><span data-stu-id="e4bc4-159">A team member is added to a group or channel</span></span>

## <a name="learn-more"></a><span data-ttu-id="e4bc4-160">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="e4bc4-160">Learn more</span></span>

<span data-ttu-id="e4bc4-161">Seu bot tem acesso a informações adicionais sobre o bate-papo de grupo ou equipe em que ele está instalado.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-161">Your bot has access to additional information about the group chat or team it is installed in.</span></span> <span data-ttu-id="e4bc4-162">Veja [obter o contexto do Microsoft Teams](~/bots/how-to/get-teams-context.md) para APIs adicionais disponíveis para o bot.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-162">See [get teams context](~/bots/how-to/get-teams-context.md) for additional APIs available for your bot.</span></span>

<span data-ttu-id="e4bc4-163">Há também outros eventos que o seu bot pode assinar e responder.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-163">There are also additional events that your bot can subscribe and respond to.</span></span> <span data-ttu-id="e4bc4-164">Consulte [inscrever-se em eventos de conversa](~/bots/how-to/conversations/subscribe-to-conversation-events.md) para saber como.</span><span class="sxs-lookup"><span data-stu-id="e4bc4-164">See [subscribe to conversation events](~/bots/how-to/conversations/subscribe-to-conversation-events.md) to learn how.</span></span>

[!INCLUDE [sample](~/includes/bots/teams-bot-samples.md)]
