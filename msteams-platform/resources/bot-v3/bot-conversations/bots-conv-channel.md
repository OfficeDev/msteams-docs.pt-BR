---
title: Conversas de chat de canal e grupo com bots
description: Descreve o cenário de ponta a ponta de ter uma conversa com um bot em um canal no Microsoft Teams
keywords: teams scenarios channels conversation bot
localization_priority: Normal
ms.topic: conceptual
ms.date: 06/25/2019
ms.openlocfilehash: e254302271cf101638c897e1a1952d302705d6a4
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566793"
---
# <a name="channel-and-group-chat-conversations-with-a-microsoft-teams-bot"></a><span data-ttu-id="86494-104">Canais e conversas de chat em grupo com um bot do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="86494-104">Channel and Group chat conversations with a Microsoft Teams bot</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="86494-105">Microsoft Teams permite que os usuários tragam bots para seus canais ou conversas de chat em grupo.</span><span class="sxs-lookup"><span data-stu-id="86494-105">Microsoft Teams allows users to bring bots into their channel or group chat conversations.</span></span> <span data-ttu-id="86494-106">Ao adicionar um bot a uma equipe ou chat, todos os usuários da conversa podem tirar proveito da funcionalidade do bot logo na conversa.</span><span class="sxs-lookup"><span data-stu-id="86494-106">By adding a bot to a team or chat, all users of the conversation can take advantage of the bot functionality right in the conversation.</span></span> <span data-ttu-id="86494-107">Você também pode acessar Teams funcionalidade específica do bot, como consultar informações da equipe e @mentioning usuários.</span><span class="sxs-lookup"><span data-stu-id="86494-107">You can also access Teams-specific functionality within your bot like querying team information and @mentioning users.</span></span>

<span data-ttu-id="86494-108">O chat em canais e chats de grupo difere do chat pessoal, já que o usuário precisa @mention o bot.</span><span class="sxs-lookup"><span data-stu-id="86494-108">Chat in channels and group chats differ from personal chat in that the user needs to @mention the bot.</span></span> <span data-ttu-id="86494-109">Se um bot for usado em vários escopos, como pessoal, groupchat ou canal, você precisará detectar de que escopo as mensagens bot vieram e processá-las de acordo.</span><span class="sxs-lookup"><span data-stu-id="86494-109">If a bot is used in multiple scopes such as personal, groupchat, or channel, you need to detect what scope the bot messages came from, and process them accordingly.</span></span>

## <a name="designing-a-great-bot-for-channels-or-groups"></a><span data-ttu-id="86494-110">Criar um ótimo bot para canais ou grupos</span><span class="sxs-lookup"><span data-stu-id="86494-110">Designing a great bot for channels or groups</span></span>

<span data-ttu-id="86494-111">Os bots adicionados a uma equipe se tornam outro membro da equipe e podem ser @mentioned como parte da conversa.</span><span class="sxs-lookup"><span data-stu-id="86494-111">Bots added to a team become another team member and can be @mentioned as part of the conversation.</span></span> <span data-ttu-id="86494-112">Na verdade, os bots só recebem mensagens quando @mentioned, portanto, outras conversas no canal não são enviadas para o bot.</span><span class="sxs-lookup"><span data-stu-id="86494-112">In fact, bots only receive messages when they are @mentioned, so other conversations on the channel are not sent to the bot.</span></span>

<span data-ttu-id="86494-113">Um bot em um grupo ou canal deve fornecer informações relevantes e apropriadas para todos os membros.</span><span class="sxs-lookup"><span data-stu-id="86494-113">A bot in a group or channel should provide information relevant and appropriate for all members.</span></span> <span data-ttu-id="86494-114">Embora o bot certamente possa fornecer informações relevantes para a experiência, tenha em mente que as conversas com ele são visíveis para todos.</span><span class="sxs-lookup"><span data-stu-id="86494-114">While your bot can certainly provide any information relevant to the experience, keep in mind conversations with it are visible to everyone.</span></span> <span data-ttu-id="86494-115">Portanto, um ótimo bot em um grupo ou canal deve adicionar valor a todos os usuários e, certamente, não compartilhar inadvertidamente informações mais apropriadas a uma conversa um para um.</span><span class="sxs-lookup"><span data-stu-id="86494-115">Therefore, a great bot in a group or channel should add value to all users, and certainly not inadvertently share information more appropriate to a one-to-one conversation.</span></span>

<span data-ttu-id="86494-116">Seu bot, assim como está, pode ser totalmente relevante em todos os escopos sem exigir trabalho adicional.</span><span class="sxs-lookup"><span data-stu-id="86494-116">Your bot, just as it is, may be entirely relevant in all scopes without requiring additional work.</span></span> <span data-ttu-id="86494-117">No Microsoft Teams não há expectativa de que sua função bot funcione em todos os escopos, mas você deve garantir que o bot fornece valor ao usuário em qualquer escopo que você optar por dar suporte.</span><span class="sxs-lookup"><span data-stu-id="86494-117">In Microsoft Teams there is no expectation that your bot function in all scopes, but you should ensure that your bot provides user value in whichever scope(s) you choose to support.</span></span> <span data-ttu-id="86494-118">Para obter mais informações sobre escopos, consulte [Apps in Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md).</span><span class="sxs-lookup"><span data-stu-id="86494-118">For more information on scopes, see [Apps in Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md).</span></span>

<span data-ttu-id="86494-119">O desenvolvimento de um bot que funciona em grupos ou canais usa grande parte da mesma funcionalidade que conversas pessoais.</span><span class="sxs-lookup"><span data-stu-id="86494-119">Developing a bot that works in groups or channels uses much of the same functionality as personal conversations.</span></span> <span data-ttu-id="86494-120">Eventos e dados adicionais na carga fornecem informações Teams grupo e canal.</span><span class="sxs-lookup"><span data-stu-id="86494-120">Additional events and data in the payload provide Teams group and channel information.</span></span> <span data-ttu-id="86494-121">Essas diferenças, bem como as principais diferenças na funcionalidade comum são descritas nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="86494-121">Those differences, as well as key differences in common functionality are described in the following sections.</span></span>

### <a name="creating-messages"></a><span data-ttu-id="86494-122">Criando mensagens</span><span class="sxs-lookup"><span data-stu-id="86494-122">Creating messages</span></span>

<span data-ttu-id="86494-123">Para obter mais informações sobre bots que criam mensagens em canais, consulte [Mensagens proativas](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md)para bots e, [especificamente, Criando uma conversa de canal.](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md#creating-a-channel-conversation)</span><span class="sxs-lookup"><span data-stu-id="86494-123">For more information on bots creating messages in channels see [Proactive messaging for bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md), and specifically [Creating a channel conversation](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md#creating-a-channel-conversation).</span></span>

### <a name="receiving-messages"></a><span data-ttu-id="86494-124">Recebimento de mensagens</span><span class="sxs-lookup"><span data-stu-id="86494-124">Receiving messages</span></span>

<span data-ttu-id="86494-125">Para um bot em um grupo ou canal, além do esquema de mensagens [regular,](https://docs.botframework.com/core-concepts/reference/#activity)o bot também recebe as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="86494-125">For a bot in a group or channel, in addition to the [regular message schema](https://docs.botframework.com/core-concepts/reference/#activity), your bot also receives the following properties:</span></span>

* <span data-ttu-id="86494-126">`channelData`Consulte [Teams dados do canal](~/resources/bot-v3/bot-conversations/bots-conversations.md#teams-channel-data).</span><span class="sxs-lookup"><span data-stu-id="86494-126">`channelData` See [Teams channel data](~/resources/bot-v3/bot-conversations/bots-conversations.md#teams-channel-data).</span></span> <span data-ttu-id="86494-127">Em um chat em grupo, contém informações específicas para esse chat.</span><span class="sxs-lookup"><span data-stu-id="86494-127">In a group chat, contains information specific to that chat.</span></span>
* <span data-ttu-id="86494-128">`conversation.id` A ID da cadeia de resposta, que consiste na ID do canal mais a ID da primeira mensagem na cadeia de resposta.</span><span class="sxs-lookup"><span data-stu-id="86494-128">`conversation.id` The reply chain ID, consisting of channel ID plus the ID of the first message in the reply chain.</span></span>
* <span data-ttu-id="86494-129">`conversation.isGroup` É `true` para mensagens bot em canais ou chats de grupo.</span><span class="sxs-lookup"><span data-stu-id="86494-129">`conversation.isGroup` Is `true` for bot messages in channels or group chats.</span></span>
* <span data-ttu-id="86494-130">`conversation.conversationType` Ou `groupChat` `channel` .</span><span class="sxs-lookup"><span data-stu-id="86494-130">`conversation.conversationType` Either `groupChat` or `channel`.</span></span>
* <span data-ttu-id="86494-131">`entities` Pode conter uma ou mais menções.</span><span class="sxs-lookup"><span data-stu-id="86494-131">`entities` Can contain one or more mentions.</span></span> <span data-ttu-id="86494-132">Para obter mais informações, consulte [Menções](#-mentions).</span><span class="sxs-lookup"><span data-stu-id="86494-132">For more information, see [Mentions](#-mentions).</span></span>

### <a name="replying-to-messages"></a><span data-ttu-id="86494-133">Responder a mensagens</span><span class="sxs-lookup"><span data-stu-id="86494-133">Replying to messages</span></span>

<span data-ttu-id="86494-134">Para responder a uma mensagem existente, chame [`ReplyToActivity`](/bot-framework/dotnet/bot-builder-dotnet-connector#send-a-reply) o .NET ou [`session.send`](/bot-framework/nodejs/bot-builder-nodejs-use-default-message-handler) Node.js.</span><span class="sxs-lookup"><span data-stu-id="86494-134">To reply to an existing message, call [`ReplyToActivity`](/bot-framework/dotnet/bot-builder-dotnet-connector#send-a-reply) in .NET or [`session.send`](/bot-framework/nodejs/bot-builder-nodejs-use-default-message-handler) in Node.js.</span></span> <span data-ttu-id="86494-135">O SDK do Construtor de Bots lida com todos os detalhes.</span><span class="sxs-lookup"><span data-stu-id="86494-135">The Bot Builder SDK handles all the details.</span></span>

<span data-ttu-id="86494-136">Se você optar por usar a API REST, também poderá chamar o [`/conversations/{conversationId}/activities/{activityId}`](/bot-framework/rest-api/bot-framework-rest-connector-send-and-receive-messages#send-the-reply) ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="86494-136">If you choose to use the REST API, you can also call the [`/conversations/{conversationId}/activities/{activityId}`](/bot-framework/rest-api/bot-framework-rest-connector-send-and-receive-messages#send-the-reply) endpoint.</span></span>

<span data-ttu-id="86494-137">Em um canal, responder a uma mensagem mostra como uma resposta à cadeia de resposta de inicialização.</span><span class="sxs-lookup"><span data-stu-id="86494-137">In a channel, replying to a message shows as a reply to the initiating reply chain.</span></span> <span data-ttu-id="86494-138">O `conversation.id` contém o canal e a ID da mensagem de nível superior.</span><span class="sxs-lookup"><span data-stu-id="86494-138">The `conversation.id` contains the channel and the top level message ID.</span></span> <span data-ttu-id="86494-139">Embora a Estrutura de Bots cuide dos detalhes, você pode armazenar em cache isso para respostas futuras a `conversation.id` esse thread de conversa, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="86494-139">Although the Bot Framework takes care of the details, you can cache that `conversation.id` for future replies to that conversation thread as needed.</span></span>

### <a name="best-practice-welcome-messages-in-teams"></a><span data-ttu-id="86494-140">Prática prática: mensagens de boas-vindas no Teams</span><span class="sxs-lookup"><span data-stu-id="86494-140">Best practice: Welcome messages in Teams</span></span>

<span data-ttu-id="86494-141">Quando o bot é adicionado pela primeira vez ao grupo ou à equipe, geralmente é útil enviar uma mensagem de boas-vindas apresentando o bot para todos os usuários.</span><span class="sxs-lookup"><span data-stu-id="86494-141">When your bot is first added to the group or team, it is generally useful to send a welcome message introducing the bot to all users.</span></span> <span data-ttu-id="86494-142">A mensagem de boas-vindas deve fornecer uma descrição da funcionalidade e dos benefícios do usuário do bot.</span><span class="sxs-lookup"><span data-stu-id="86494-142">The welcome message should provide a description of the bot’s functionality and user benefits.</span></span> <span data-ttu-id="86494-143">O ideal é que a mensagem também inclua comandos para o usuário interagir com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="86494-143">Ideally the message should also include commands for the user to interact with the app.</span></span> <span data-ttu-id="86494-144">Para fazer isso, verifique se o bot responde à `conversationUpdate` mensagem, com `teamsAddMembers` o eventType no `channelData` objeto.</span><span class="sxs-lookup"><span data-stu-id="86494-144">To do this, ensure that your bot responds to the `conversationUpdate` message, with the `teamsAddMembers` eventType in the `channelData` object.</span></span> <span data-ttu-id="86494-145">Certifique-se de que a ID seja a própria ID do aplicativo do bot, pois o mesmo evento é enviado quando um usuário é `memberAdded` adicionado a uma equipe.</span><span class="sxs-lookup"><span data-stu-id="86494-145">Be sure that the `memberAdded` ID is the bot's App ID itself, because the same event is sent when a user is added to a team.</span></span> <span data-ttu-id="86494-146">Consulte [Membro da equipe ou adição de bot](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="86494-146">See [Team member or bot addition](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) for more details.</span></span>

<span data-ttu-id="86494-147">Você também pode querer enviar uma mensagem pessoal para cada membro da equipe quando o bot for adicionado.</span><span class="sxs-lookup"><span data-stu-id="86494-147">You might also want to send a personal message to each member of the team when the bot is added.</span></span> <span data-ttu-id="86494-148">Para fazer isso, você pode [buscar a lista de](~/resources/bot-v3/bots-context.md#fetch-the-team-roster) equipe e enviar a cada usuário uma mensagem [direta](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md).</span><span class="sxs-lookup"><span data-stu-id="86494-148">To do this, you could [fetch the team roster](~/resources/bot-v3/bots-context.md#fetch-the-team-roster) and send each user a [direct message](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md).</span></span>

<span data-ttu-id="86494-149">Recomendamos que seu bot *não* envie uma mensagem de boas-vindas nas seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="86494-149">We recommend that your bot *not* send a welcome message in the following situations:</span></span>

* <span data-ttu-id="86494-150">A equipe é grande (obviamente subjetivo, por exemplo, mais de 100 membros).</span><span class="sxs-lookup"><span data-stu-id="86494-150">The team is big (obviously subjective, for example, more than 100 members).</span></span> <span data-ttu-id="86494-151">Seu bot pode ser visto como "spammy" e a pessoa que o adicionou pode receber reclamações, a menos que você comunique claramente a proposta de valor do bot para todos que veem a mensagem de boas-vindas.</span><span class="sxs-lookup"><span data-stu-id="86494-151">Your bot may be seen as 'spammy' and the person who added it may get complaints unless you clearly communicate your bot's value proposition to everyone who sees the welcome message.</span></span>
* <span data-ttu-id="86494-152">Seu bot é mencionado pela primeira vez em um grupo ou canal, em vez de ser adicionado pela primeira vez a uma equipe.</span><span class="sxs-lookup"><span data-stu-id="86494-152">Your bot is first mentioned in a group or channel, versus being first added to a team.</span></span>
* <span data-ttu-id="86494-153">Um grupo ou canal é renomeado.</span><span class="sxs-lookup"><span data-stu-id="86494-153">A group or channel is renamed.</span></span>
* <span data-ttu-id="86494-154">Um membro da equipe é adicionado a um grupo ou canal.</span><span class="sxs-lookup"><span data-stu-id="86494-154">A team member is added to a group or channel.</span></span>

## <a name="-mentions"></a><span data-ttu-id="86494-155">@ Menções</span><span class="sxs-lookup"><span data-stu-id="86494-155">@ Mentions</span></span>

<span data-ttu-id="86494-156">Como os bots em um grupo ou canal respondem somente quando eles são mencionados ("@_botname_") em uma mensagem, cada mensagem recebida por um bot em um canal de grupo contém seu próprio nome e você deve garantir que a análise da mensagem lida com isso.</span><span class="sxs-lookup"><span data-stu-id="86494-156">Because bots in a group or channel respond only when they are mentioned ("@_botname_") in a message, every message received by a bot in a group channel contains its own name, and you must ensure your message parsing handles that.</span></span> <span data-ttu-id="86494-157">Além disso, os bots podem analisar outros usuários mencionados e mencionar usuários como parte de suas mensagens.</span><span class="sxs-lookup"><span data-stu-id="86494-157">In addition, bots can parse out other users mentioned and mention users as part of their messages.</span></span>

### <a name="retrieving-mentions"></a><span data-ttu-id="86494-158">Recuperando menções</span><span class="sxs-lookup"><span data-stu-id="86494-158">Retrieving mentions</span></span>

<span data-ttu-id="86494-159">As menções são retornadas no objeto em carga e contêm a ID exclusiva do usuário e, na maioria dos casos, o `entities` nome do usuário mencionado.</span><span class="sxs-lookup"><span data-stu-id="86494-159">Mentions are returned in the `entities` object in payload and contain both the unique ID of the user and, in most cases, the name of user mentioned.</span></span> <span data-ttu-id="86494-160">Você pode recuperar todas as menções na mensagem chamando a função no SDK do Construtor de Bots para .NET, que retorna uma `GetMentions` matriz de `Mentioned` objetos.</span><span class="sxs-lookup"><span data-stu-id="86494-160">You can retrieve all mentions in the message by calling the `GetMentions` function in the Bot Builder SDK for .NET, which returns an array of `Mentioned` objects.</span></span>

#### <a name="net-example-code-check-for-and-strip-bot-mention"></a><span data-ttu-id="86494-161">Código de exemplo do .NET: verifique e @bot menção</span><span class="sxs-lookup"><span data-stu-id="86494-161">.NET example code: Check for and strip @bot mention</span></span>

```csharp
Mention[] m = sourceMessage.GetMentions();
var messageText = sourceMessage.Text;

for (int i = 0;i < m.Length;i++)
{
    if (m[i].Mentioned.Id == sourceMessage.Recipient.Id)
    {
        //Bot is in the @mention list.
        //The below example will strip the bot name out of the message, so you can parse it as if it wasn't included. Note that the Text object will contain the full bot name, if applicable.
        if (m[i].Text != null)
            messageText = messageText.Replace(m[i].Text, "");
    }
}
```

> [!NOTE]
> <span data-ttu-id="86494-162">Você também pode usar a função Teams de extensão , que retira todas as `GetTextWithoutMentions` menções, incluindo o bot.</span><span class="sxs-lookup"><span data-stu-id="86494-162">You can also use the Teams extension function `GetTextWithoutMentions`, which strips out all mentions, including the bot.</span></span>

#### <a name="nodejs-example-code-check-for-and-strip-bot-mention"></a><span data-ttu-id="86494-163">Node.js código de exemplo: verifique e @bot menção</span><span class="sxs-lookup"><span data-stu-id="86494-163">Node.js example code: Check for and strip @bot mention</span></span>

```javascript
var text = message.text;
if (message.entities) {
    message.entities
        .filter(entity => ((entity.type === "mention") && (entity.mentioned.id.toLowerCase() === botId)))
        .forEach(entity => {
            text = text.replace(entity.text, "");
        });
    text = text.trim();
}
```

<span data-ttu-id="86494-164">Você também pode usar a função Teams de extensão , que retira todas as `getTextWithoutMentions` menções, incluindo o bot.</span><span class="sxs-lookup"><span data-stu-id="86494-164">You can also use the Teams extension function `getTextWithoutMentions`, which strips out all mentions, including the bot.</span></span>

### <a name="constructing-mentions"></a><span data-ttu-id="86494-165">Criar menções</span><span class="sxs-lookup"><span data-stu-id="86494-165">Constructing mentions</span></span>

<span data-ttu-id="86494-166">Seu bot pode mencionar outros usuários em mensagens postadas em canais.</span><span class="sxs-lookup"><span data-stu-id="86494-166">Your bot can mention other users in messages posted into channels.</span></span> <span data-ttu-id="86494-167">Para fazer isso, sua mensagem deve fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="86494-167">To do this, your message must do the following:</span></span>

* <span data-ttu-id="86494-168">Inclua `<at>@username</at>` no texto da mensagem.</span><span class="sxs-lookup"><span data-stu-id="86494-168">Include `<at>@username</at>` in the message text.</span></span>
* <span data-ttu-id="86494-169">Inclua o `mention` objeto dentro da coleção de entidades.</span><span class="sxs-lookup"><span data-stu-id="86494-169">Include the `mention` object inside the entities collection.</span></span>

#### <a name="net-example"></a><span data-ttu-id="86494-170">Exemplo do .NET</span><span class="sxs-lookup"><span data-stu-id="86494-170">.NET example</span></span>

<span data-ttu-id="86494-171">Este exemplo usa o [pacote Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet.</span><span class="sxs-lookup"><span data-stu-id="86494-171">This example uses the [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet package.</span></span>

```csharp
// Create reply activity
Activity replyActivity = activity.CreateReply();

// Construct text of the form @sender Hello
replyActivity.Text = "Hello ";
replyActivity.AddMentionToText(activity.From, MentionTextLocation.AppendText);

// Send the reply activity
await client.Conversations.ReplyToActivityAsync(replyActivity);
```

#### <a name="nodejs-example"></a><span data-ttu-id="86494-172">Node.js exemplo</span><span class="sxs-lookup"><span data-stu-id="86494-172">Node.js example</span></span>

```javascript
// User to mention
var toMention: builder.IIdentity = {
    name: 'John Doe',
    id: userId
};

// Create a message and add mention to it
var msg = new teams.TeamsMessage(session).text(teams.TeamsMessage.getTenantId(session.message));
var mentionedMsg = msg.addMentionToText(toMention);

// Post the message
var generalMessage = mentionedMsg.routeReplyToGeneralChannel();
session.send(generalMessage);
```

#### <a name="example-outgoing-message-with-user-mentioned"></a><span data-ttu-id="86494-173">Exemplo: mensagem de saída com o usuário mencionado</span><span class="sxs-lookup"><span data-stu-id="86494-173">Example: Outgoing message with user mentioned</span></span>

```json
{
    "type": "message", 
    "text": "Hey <at>Pranav Smith</at> check out this message",
    "timestamp": "2017-10-29T00:51:05.9908157Z",
    "localTimestamp": "2017-10-28T17:51:05.9908157-07:00",
    "serviceUrl": "https://skype.botframework.com",
    "channelId": "msteams",
    "from": {
        "id": "28:9e52142b-5e5e-4d7b-bb3e- e82dcf620000",
        "name": "SchemaTestBot"
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

## <a name="accessing-groupchat-or-channel-scope"></a><span data-ttu-id="86494-174">Acessando groupChat ou escopo de canal</span><span class="sxs-lookup"><span data-stu-id="86494-174">Accessing groupChat or channel scope</span></span>

<span data-ttu-id="86494-175">Seu bot pode fazer mais do que enviar e receber mensagens em grupos e equipes.</span><span class="sxs-lookup"><span data-stu-id="86494-175">Your bot can do more than send and receive messages in groups and teams.</span></span> <span data-ttu-id="86494-176">Por exemplo, ele também pode buscar a lista de membros, incluindo suas informações de perfil, bem como a lista de canais.</span><span class="sxs-lookup"><span data-stu-id="86494-176">For instance, it can also fetch the list of members, including their profile information, as well as the list of channels.</span></span> <span data-ttu-id="86494-177">Para obter mais informações, [consulte Obter contexto para seu Microsoft Teams bot](~/resources/bot-v3/bots-context.md).</span><span class="sxs-lookup"><span data-stu-id="86494-177">For more information, see [Get context for your Microsoft Teams bot](~/resources/bot-v3/bots-context.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="86494-178">Confira também</span><span class="sxs-lookup"><span data-stu-id="86494-178">See also</span></span>

[<span data-ttu-id="86494-179">Exemplos de Estrutura de Bot</span><span class="sxs-lookup"><span data-stu-id="86494-179">Bot Framework samples</span></span>](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)
