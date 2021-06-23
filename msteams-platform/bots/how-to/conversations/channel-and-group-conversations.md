---
title: Conversas de canal e grupo com um bot
author: surbhigupta
description: Como enviar, receber e manipular mensagens para um bot em um chat de canal ou grupo.
ms.topic: conceptual
localization_priority: Normal
ms.author: anclear
ms.openlocfilehash: 399f7d7487b4992e70d4ee515b26101e2b253a62
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069007"
---
# <a name="channel-and-group-chat-conversations-with-a-bot"></a><span data-ttu-id="3640f-103">Conversas de chat de canal e grupo com um bot</span><span class="sxs-lookup"><span data-stu-id="3640f-103">Channel and group chat conversations with a bot</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="3640f-104">Para instalar o Microsoft Teams em um chat de equipe ou grupo, adicione `teams` o escopo ou ao `groupchat` bot.</span><span class="sxs-lookup"><span data-stu-id="3640f-104">To install the Microsoft Teams bot in a team or group chat, add the `teams` or `groupchat` scope to your bot.</span></span> <span data-ttu-id="3640f-105">Isso permite que todos os membros da conversa interajam com o seu bot.</span><span class="sxs-lookup"><span data-stu-id="3640f-105">This allows all members of the conversation to interact with your bot.</span></span> <span data-ttu-id="3640f-106">Depois que o bot é instalado, ele tem acesso a metadados sobre a conversa, como a lista de membros da conversa.</span><span class="sxs-lookup"><span data-stu-id="3640f-106">After the bot is installed, it has access to metadata about the conversation, such as the list of conversation members.</span></span> <span data-ttu-id="3640f-107">Além disso, quando ele é instalado em uma equipe, o bot tem acesso a detalhes sobre essa equipe e a lista completa de canais.</span><span class="sxs-lookup"><span data-stu-id="3640f-107">Also, when it is installed in a team, the bot has access to details about that team and the full list of channels.</span></span>

<span data-ttu-id="3640f-108">Os bots em um grupo ou canal só recebem mensagens quando são mencionados @botname.</span><span class="sxs-lookup"><span data-stu-id="3640f-108">Bots in a group or channel only receive messages when they are mentioned @botname.</span></span> <span data-ttu-id="3640f-109">Eles não recebem outras mensagens enviadas para a conversa.</span><span class="sxs-lookup"><span data-stu-id="3640f-109">They do not receive any other messages sent to the conversation.</span></span> <span data-ttu-id="3640f-110">O bot deve ser @mencionado diretamente.</span><span class="sxs-lookup"><span data-stu-id="3640f-110">The bot must be @mentioned directly.</span></span> <span data-ttu-id="3640f-111">Seu bot não recebe uma mensagem quando a equipe ou canal é mencionado ou quando alguém responde a uma mensagem de seu bot sem @mentioning-la.</span><span class="sxs-lookup"><span data-stu-id="3640f-111">Your bot does not receive a message when the team or channel is mentioned, or when someone replies to a message from your bot without @mentioning it.</span></span>

> [!NOTE]
> <span data-ttu-id="3640f-112">Esse recurso está disponível apenas na [visualização de desenvolvedor](../../../resources/dev-preview/developer-preview-intro.md) público.</span><span class="sxs-lookup"><span data-stu-id="3640f-112">This feature is currently available in [public developer preview](../../../resources/dev-preview/developer-preview-intro.md) only.</span></span>
>
> <span data-ttu-id="3640f-113">Usando o RSC (consentimento específico do recurso), os bots podem receber todas as mensagens de canal em equipes em que ele está instalado sem @mentioned.</span><span class="sxs-lookup"><span data-stu-id="3640f-113">Using resource-specific consent (RSC), bots can receive all channel messages in teams that it is installed in without being @mentioned.</span></span> <span data-ttu-id="3640f-114">Para obter mais informações, [consulte receive all channel messages with RSC](channel-messages-with-rsc.md).</span><span class="sxs-lookup"><span data-stu-id="3640f-114">For more information, see [receive all channel messages with RSC](channel-messages-with-rsc.md).</span></span>

## <a name="design-guidelines"></a><span data-ttu-id="3640f-115">Diretrizes de design</span><span class="sxs-lookup"><span data-stu-id="3640f-115">Design guidelines</span></span>

<span data-ttu-id="3640f-116">Ao contrário de chats pessoais, em chats em grupo e canais, seu bot deve fornecer uma introdução rápida.</span><span class="sxs-lookup"><span data-stu-id="3640f-116">Unlike personal chats, in group chats and channels, your bot must provide a quick introduction.</span></span> <span data-ttu-id="3640f-117">Você deve seguir essas e mais diretrizes de design de bot.</span><span class="sxs-lookup"><span data-stu-id="3640f-117">You must follow these and more bot design guidelines.</span></span> <span data-ttu-id="3640f-118">Para obter mais informações sobre como projetar bots em Teams, consulte como projetar conversas [de bot em canais e chats.](~/bots/design/bots.md)</span><span class="sxs-lookup"><span data-stu-id="3640f-118">For more information on how to design bots in Teams, see [how to design bot conversations in channels and chats](~/bots/design/bots.md).</span></span>

<span data-ttu-id="3640f-119">Agora, você pode criar novos threads de conversa e gerenciar facilmente diferentes conversas em canais.</span><span class="sxs-lookup"><span data-stu-id="3640f-119">Now, you can create new conversation threads and easily manage different conversations in channels.</span></span>

## <a name="create-new-conversation-threads"></a><span data-ttu-id="3640f-120">Criar novos threads de conversa</span><span class="sxs-lookup"><span data-stu-id="3640f-120">Create new conversation threads</span></span>

<span data-ttu-id="3640f-121">Quando o bot é instalado em uma equipe, você deve criar um novo thread de conversa em vez de responder a um existente.</span><span class="sxs-lookup"><span data-stu-id="3640f-121">When your bot is installed in a team, you must create a new conversation thread rather than reply to an existing one.</span></span> <span data-ttu-id="3640f-122">Às vezes, é difícil diferenciar entre duas conversas.</span><span class="sxs-lookup"><span data-stu-id="3640f-122">At times it is difficult to differentiate between two conversations.</span></span> <span data-ttu-id="3640f-123">Se a conversa for encadeada, é mais fácil organizar e gerenciar diferentes conversas em canais.</span><span class="sxs-lookup"><span data-stu-id="3640f-123">If the conversation is threaded, it is easier to organize and manage different conversations in channels.</span></span> <span data-ttu-id="3640f-124">Essa é uma forma de mensagens [proativas.](~/bots/how-to/conversations/send-proactive-messages.md)</span><span class="sxs-lookup"><span data-stu-id="3640f-124">This is a form of [proactive messaging](~/bots/how-to/conversations/send-proactive-messages.md).</span></span>

<span data-ttu-id="3640f-125">Em seguida, você pode recuperar menções usando o objeto e adicionar menções às `entities` suas mensagens usando o `Mention` objeto.</span><span class="sxs-lookup"><span data-stu-id="3640f-125">Next, you can retrieve mentions using the `entities` object and add mentions to your messages using the `Mention` object.</span></span>

## <a name="work-with-mentions"></a><span data-ttu-id="3640f-126">Trabalhar com menções</span><span class="sxs-lookup"><span data-stu-id="3640f-126">Work with mentions</span></span>

<span data-ttu-id="3640f-127">Cada mensagem para seu bot de um grupo ou canal contém um @mention com seu nome no texto da mensagem.</span><span class="sxs-lookup"><span data-stu-id="3640f-127">Every message to your bot from a group or channel contains an @mention with its name in the message text.</span></span> <span data-ttu-id="3640f-128">Seu bot também pode recuperar outros usuários mencionados em uma mensagem e adicionar menções a todas as mensagens enviadas.</span><span class="sxs-lookup"><span data-stu-id="3640f-128">Your bot can also retrieve other users mentioned in a message and add mentions to any messages it sends.</span></span>

<span data-ttu-id="3640f-129">Você também deve retirar o @mentions do conteúdo da mensagem que seu bot recebe.</span><span class="sxs-lookup"><span data-stu-id="3640f-129">You must also strip out the @mentions from the content of the message your bot receives.</span></span>

### <a name="retrieve-mentions"></a><span data-ttu-id="3640f-130">Recuperar menções</span><span class="sxs-lookup"><span data-stu-id="3640f-130">Retrieve mentions</span></span>

<span data-ttu-id="3640f-131">As menções são retornadas no objeto em carga e contêm a ID exclusiva do usuário e o `entities` nome do usuário mencionado.</span><span class="sxs-lookup"><span data-stu-id="3640f-131">Mentions are returned in the `entities` object in payload and contain both the unique ID of the user and the name of the user mentioned.</span></span> <span data-ttu-id="3640f-132">O texto da mensagem também inclui a menção, como `<at>@John Smith<at>` .</span><span class="sxs-lookup"><span data-stu-id="3640f-132">The text of the message also includes the mention, such as `<at>@John Smith<at>`.</span></span> <span data-ttu-id="3640f-133">No entanto, não confie no texto na mensagem para recuperar qualquer informação sobre o usuário.</span><span class="sxs-lookup"><span data-stu-id="3640f-133">However, do not rely on the text in the message to retrieve any information about the user.</span></span> <span data-ttu-id="3640f-134">É possível que a pessoa que envia a mensagem a altere.</span><span class="sxs-lookup"><span data-stu-id="3640f-134">It is possible for the person sending the message to alter it.</span></span> <span data-ttu-id="3640f-135">Portanto, use o `entities` objeto.</span><span class="sxs-lookup"><span data-stu-id="3640f-135">Therefore, use the `entities` object.</span></span>

<span data-ttu-id="3640f-136">Você pode recuperar todas as menções na mensagem chamando a função no SDK do Construtor de `GetMentions` Bots, que retorna uma matriz de `Mention` objetos.</span><span class="sxs-lookup"><span data-stu-id="3640f-136">You can retrieve all mentions in the message by calling the `GetMentions` function in the Bot Builder SDK, which returns an array of `Mention` objects.</span></span>

<span data-ttu-id="3640f-137">O código a seguir mostra um exemplo de recuperação de menções:</span><span class="sxs-lookup"><span data-stu-id="3640f-137">The following code shows an example of retrieving mentions:</span></span>

# <a name="c"></a>[<span data-ttu-id="3640f-138">C#</span><span class="sxs-lookup"><span data-stu-id="3640f-138">C#</span></span>](#tab/dotnet)

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

# <a name="typescript"></a>[<span data-ttu-id="3640f-139">TypeScript</span><span class="sxs-lookup"><span data-stu-id="3640f-139">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="3640f-140">JSON</span><span class="sxs-lookup"><span data-stu-id="3640f-140">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="3640f-141">Python</span><span class="sxs-lookup"><span data-stu-id="3640f-141">Python</span></span>](#tab/python)

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

### <a name="add-mentions-to-your-messages"></a><span data-ttu-id="3640f-142">Adicionar menções às suas mensagens</span><span class="sxs-lookup"><span data-stu-id="3640f-142">Add mentions to your messages</span></span>

<span data-ttu-id="3640f-143">Seu bot pode mencionar outros usuários em mensagens postadas em canais.</span><span class="sxs-lookup"><span data-stu-id="3640f-143">Your bot can mention other users in messages posted into channels.</span></span>

<span data-ttu-id="3640f-144">O `Mention` objeto tem duas propriedades que você deve definir usando o seguinte:</span><span class="sxs-lookup"><span data-stu-id="3640f-144">The `Mention` object has two properties that you must set using the following:</span></span>

* <span data-ttu-id="3640f-145">Inclua <at>@username</at> no texto da mensagem.</span><span class="sxs-lookup"><span data-stu-id="3640f-145">Include <at>@username</at> in the message text.</span></span>
* <span data-ttu-id="3640f-146">Inclua o objeto mention dentro da coleção de entidades.</span><span class="sxs-lookup"><span data-stu-id="3640f-146">Include the mention object inside the entities collection.</span></span>

<span data-ttu-id="3640f-147">O SDK da Estrutura de Bot fornece métodos e objetos auxiliares para criar menções.</span><span class="sxs-lookup"><span data-stu-id="3640f-147">The Bot Framework SDK provides helper methods and objects to create mentions.</span></span>

<span data-ttu-id="3640f-148">O código a seguir mostra um exemplo de adição de menções às suas mensagens:</span><span class="sxs-lookup"><span data-stu-id="3640f-148">The following code shows an example of adding mentions to your messages:</span></span>

# <a name="c"></a>[<span data-ttu-id="3640f-149">C#</span><span class="sxs-lookup"><span data-stu-id="3640f-149">C#</span></span>](#tab/dotnet)

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

# <a name="typescript"></a>[<span data-ttu-id="3640f-150">TypeScript</span><span class="sxs-lookup"><span data-stu-id="3640f-150">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="3640f-151">JSON</span><span class="sxs-lookup"><span data-stu-id="3640f-151">JSON</span></span>](#tab/json)

<span data-ttu-id="3640f-152">O `text` campo no objeto na matriz deve corresponder a uma parte do campo de `entities` `text` mensagem.</span><span class="sxs-lookup"><span data-stu-id="3640f-152">The `text` field in the object in the `entities` array must match a portion of the message `text` field.</span></span> <span data-ttu-id="3640f-153">Se isso não acontecer, a menção será ignorada.</span><span class="sxs-lookup"><span data-stu-id="3640f-153">If it does not, the mention is ignored.</span></span>

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

# <a name="python"></a>[<span data-ttu-id="3640f-154">Python</span><span class="sxs-lookup"><span data-stu-id="3640f-154">Python</span></span>](#tab/python)

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

<span data-ttu-id="3640f-155">Agora você pode enviar uma mensagem de introdução quando o bot for instalado pela primeira vez ou adicionado a um grupo ou equipe.</span><span class="sxs-lookup"><span data-stu-id="3640f-155">Now you can send an introduction message when your bot is first installed or added to a group or team.</span></span>

## <a name="send-a-message-on-installation"></a><span data-ttu-id="3640f-156">Enviar uma mensagem na instalação</span><span class="sxs-lookup"><span data-stu-id="3640f-156">Send a message on installation</span></span>

<span data-ttu-id="3640f-157">Quando o bot é adicionado pela primeira vez ao grupo ou à equipe, uma mensagem de introdução deve ser enviada.</span><span class="sxs-lookup"><span data-stu-id="3640f-157">When your bot is first added to the group or team, an introduction message must be sent.</span></span> <span data-ttu-id="3640f-158">A mensagem deve fornecer uma breve descrição dos recursos do bot e como usá-los.</span><span class="sxs-lookup"><span data-stu-id="3640f-158">The message must provide a brief description of the bot's features and how to use them.</span></span> <span data-ttu-id="3640f-159">Você deve se inscrever no `conversationUpdate` evento com `teamMemberAdded` o eventType.</span><span class="sxs-lookup"><span data-stu-id="3640f-159">You must subscribe to the `conversationUpdate` event with the `teamMemberAdded` eventType.</span></span>  <span data-ttu-id="3640f-160">O evento é enviado quando qualquer novo membro da equipe é adicionado.</span><span class="sxs-lookup"><span data-stu-id="3640f-160">The event is sent when any new team member is added.</span></span> <span data-ttu-id="3640f-161">Verifique se o novo membro adicionado é o bot.</span><span class="sxs-lookup"><span data-stu-id="3640f-161">Check if the new member added is the bot.</span></span> <span data-ttu-id="3640f-162">Para obter mais informações, consulte [enviando uma mensagem de boas-vindas a um novo membro da equipe](~/bots/how-to/conversations/send-proactive-messages.md).</span><span class="sxs-lookup"><span data-stu-id="3640f-162">For more information, see [sending a welcome message to a new team member](~/bots/how-to/conversations/send-proactive-messages.md).</span></span>

<span data-ttu-id="3640f-163">Envie uma mensagem pessoal para cada membro da equipe quando o bot for adicionado.</span><span class="sxs-lookup"><span data-stu-id="3640f-163">Send a personal message to each team member when the bot is added.</span></span> <span data-ttu-id="3640f-164">Para fazer isso, receba a lista de equipe e envie uma mensagem direta a cada usuário.</span><span class="sxs-lookup"><span data-stu-id="3640f-164">To do this, get the team roster and send each user a direct message.</span></span>

<span data-ttu-id="3640f-165">Não envie uma mensagem nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="3640f-165">Do not send a message in the following cases:</span></span>

* <span data-ttu-id="3640f-166">A equipe é grande, por exemplo, maior do que 100 membros.</span><span class="sxs-lookup"><span data-stu-id="3640f-166">The team is large, for example, larger than 100 members.</span></span> <span data-ttu-id="3640f-167">Seu bot pode ser visto como spam e a pessoa que o adicionou pode receber reclamações.</span><span class="sxs-lookup"><span data-stu-id="3640f-167">Your bot can be seen as spam and the person who added it can get complaints.</span></span> <span data-ttu-id="3640f-168">Você deve comunicar claramente a proposta de valor do bot a todos que veem a mensagem de boas-vindas.</span><span class="sxs-lookup"><span data-stu-id="3640f-168">You must clearly communicate your bot's value proposition to everyone who sees the welcome message.</span></span>
* <span data-ttu-id="3640f-169">Seu bot é mencionado pela primeira vez em um grupo ou canal em vez de ser adicionado pela primeira vez a uma equipe.</span><span class="sxs-lookup"><span data-stu-id="3640f-169">Your bot is first mentioned in a group or channel instead of being first added to a team.</span></span>
* <span data-ttu-id="3640f-170">Um grupo ou canal é renomeado.</span><span class="sxs-lookup"><span data-stu-id="3640f-170">A group or channel is renamed.</span></span>
* <span data-ttu-id="3640f-171">Um membro da equipe é adicionado a um grupo ou canal.</span><span class="sxs-lookup"><span data-stu-id="3640f-171">A team member is added to a group or channel.</span></span>

[!INCLUDE [sample](~/includes/bots/teams-bot-samples.md)]

## <a name="see-also"></a><span data-ttu-id="3640f-172">Confira também</span><span class="sxs-lookup"><span data-stu-id="3640f-172">See also</span></span>

[<span data-ttu-id="3640f-173">Obter Teams contexto</span><span class="sxs-lookup"><span data-stu-id="3640f-173">Get Teams context</span></span>](~/bots/how-to/get-teams-context.md)

## <a name="next-step"></a><span data-ttu-id="3640f-174">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="3640f-174">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3640f-175">Inscreva-se em eventos de conversa</span><span class="sxs-lookup"><span data-stu-id="3640f-175">Subscribe to conversation events</span></span>](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
