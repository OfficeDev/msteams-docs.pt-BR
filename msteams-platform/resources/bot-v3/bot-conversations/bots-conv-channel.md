---
title: Conversas de bate-papo de canal e grupo com bots
description: Descreve o cenário de ponta a ponta de ter uma conversa com um bot em um canal em Microsoft Teams
keywords: cenários equipes canais chat bot
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
# <a name="channel-and-group-chat-conversations-with-a-microsoft-teams-bot"></a><span data-ttu-id="ad68b-104">Canais e conversas de chat em grupo com um bot do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="ad68b-104">Channel and Group chat conversations with a Microsoft Teams bot</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="ad68b-105">Microsoft Teams permite que os usuários tragam bots para suas conversas de canal ou chat em grupo.</span><span class="sxs-lookup"><span data-stu-id="ad68b-105">Microsoft Teams allows users to bring bots into their channel or group chat conversations.</span></span> <span data-ttu-id="ad68b-106">Ao adicionar um bot a uma equipe ou bate-papo, todos os usuários da conversa podem aproveitar a funcionalidade do bot apenas na conversa.</span><span class="sxs-lookup"><span data-stu-id="ad68b-106">By adding a bot to a team or chat, all users of the conversation can take advantage of the bot functionality right in the conversation.</span></span> <span data-ttu-id="ad68b-107">Você também pode acessar Teams funcionalidade específica dentro do seu bot, como consultar informações da equipe e @mentioning usuários.</span><span class="sxs-lookup"><span data-stu-id="ad68b-107">You can also access Teams-specific functionality within your bot like querying team information and @mentioning users.</span></span>

<span data-ttu-id="ad68b-108">Chat em canais e bate-papos em grupo diferem do bate-papo pessoal na forma de que o usuário precisa @mention o bot.</span><span class="sxs-lookup"><span data-stu-id="ad68b-108">Chat in channels and group chats differ from personal chat in that the user needs to @mention the bot.</span></span> <span data-ttu-id="ad68b-109">Se um bot for usado em vários escopos, como pessoal, groupchat ou canal, você precisa detectar de que escopo as mensagens do bot vieram e processá-las de acordo.</span><span class="sxs-lookup"><span data-stu-id="ad68b-109">If a bot is used in multiple scopes such as personal, groupchat, or channel, you need to detect what scope the bot messages came from, and process them accordingly.</span></span>

## <a name="designing-a-great-bot-for-channels-or-groups"></a><span data-ttu-id="ad68b-110">Projetando um ótimo bot para canais ou grupos</span><span class="sxs-lookup"><span data-stu-id="ad68b-110">Designing a great bot for channels or groups</span></span>

<span data-ttu-id="ad68b-111">Bots adicionados a uma equipe tornam-se outro membro da equipe e podem ser @mentioned como parte da conversa.</span><span class="sxs-lookup"><span data-stu-id="ad68b-111">Bots added to a team become another team member and can be @mentioned as part of the conversation.</span></span> <span data-ttu-id="ad68b-112">Na verdade, os bots só recebem mensagens quando são @mentioned, de modo que outras conversas no canal não são enviadas para o bot.</span><span class="sxs-lookup"><span data-stu-id="ad68b-112">In fact, bots only receive messages when they are @mentioned, so other conversations on the channel are not sent to the bot.</span></span>

<span data-ttu-id="ad68b-113">Um bot em um grupo ou canal deve fornecer informações relevantes e apropriadas para todos os membros.</span><span class="sxs-lookup"><span data-stu-id="ad68b-113">A bot in a group or channel should provide information relevant and appropriate for all members.</span></span> <span data-ttu-id="ad68b-114">Embora seu bot certamente possa fornecer qualquer informação relevante para a experiência, tenha em mente que as conversas com ele são visíveis para todos.</span><span class="sxs-lookup"><span data-stu-id="ad68b-114">While your bot can certainly provide any information relevant to the experience, keep in mind conversations with it are visible to everyone.</span></span> <span data-ttu-id="ad68b-115">Portanto, um grande bot em um grupo ou canal deve agregar valor a todos os usuários, e certamente não compartilhar inadvertidamente informações mais apropriadas para uma conversa um-para-um.</span><span class="sxs-lookup"><span data-stu-id="ad68b-115">Therefore, a great bot in a group or channel should add value to all users, and certainly not inadvertently share information more appropriate to a one-to-one conversation.</span></span>

<span data-ttu-id="ad68b-116">Seu bot, assim como é, pode ser inteiramente relevante em todos os escopos sem exigir trabalho adicional.</span><span class="sxs-lookup"><span data-stu-id="ad68b-116">Your bot, just as it is, may be entirely relevant in all scopes without requiring additional work.</span></span> <span data-ttu-id="ad68b-117">Em Microsoft Teams não há expectativa de que seu bot funcione em todos os escopos, mas você deve garantir que seu bot forneça valor ao usuário em qualquer escopo que você escolher para suportar.</span><span class="sxs-lookup"><span data-stu-id="ad68b-117">In Microsoft Teams there is no expectation that your bot function in all scopes, but you should ensure that your bot provides user value in whichever scope(s) you choose to support.</span></span> <span data-ttu-id="ad68b-118">Para obter mais informações sobre escopos, consulte [Aplicativos em Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ad68b-118">For more information on scopes, see [Apps in Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md).</span></span>

<span data-ttu-id="ad68b-119">Desenvolver um bot que funciona em grupos ou canais usa muito da mesma funcionalidade que conversas pessoais.</span><span class="sxs-lookup"><span data-stu-id="ad68b-119">Developing a bot that works in groups or channels uses much of the same functionality as personal conversations.</span></span> <span data-ttu-id="ad68b-120">Eventos adicionais e dados na carga fornecem informações Teams grupo e canal.</span><span class="sxs-lookup"><span data-stu-id="ad68b-120">Additional events and data in the payload provide Teams group and channel information.</span></span> <span data-ttu-id="ad68b-121">Essas diferenças, bem como as principais diferenças na funcionalidade comum são descritas nas seguintes seções.</span><span class="sxs-lookup"><span data-stu-id="ad68b-121">Those differences, as well as key differences in common functionality are described in the following sections.</span></span>

### <a name="creating-messages"></a><span data-ttu-id="ad68b-122">Criando mensagens</span><span class="sxs-lookup"><span data-stu-id="ad68b-122">Creating messages</span></span>

<span data-ttu-id="ad68b-123">Para obter mais informações sobre bots criando mensagens em canais, consulte [mensagens proativas para bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md)e criando especificamente [uma conversa de canal](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md#creating-a-channel-conversation).</span><span class="sxs-lookup"><span data-stu-id="ad68b-123">For more information on bots creating messages in channels see [Proactive messaging for bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md), and specifically [Creating a channel conversation](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md#creating-a-channel-conversation).</span></span>

### <a name="receiving-messages"></a><span data-ttu-id="ad68b-124">Recebimento de mensagens</span><span class="sxs-lookup"><span data-stu-id="ad68b-124">Receiving messages</span></span>

<span data-ttu-id="ad68b-125">Para um bot em um grupo ou canal, além do [esquema de mensagem regular,](https://docs.botframework.com/core-concepts/reference/#activity)o bot também recebe as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="ad68b-125">For a bot in a group or channel, in addition to the [regular message schema](https://docs.botframework.com/core-concepts/reference/#activity), your bot also receives the following properties:</span></span>

* <span data-ttu-id="ad68b-126">`channelData`Veja [os dados do canal Teams](~/resources/bot-v3/bot-conversations/bots-conversations.md#teams-channel-data).</span><span class="sxs-lookup"><span data-stu-id="ad68b-126">`channelData` See [Teams channel data](~/resources/bot-v3/bot-conversations/bots-conversations.md#teams-channel-data).</span></span> <span data-ttu-id="ad68b-127">Em um bate-papo em grupo, contém informações específicas para esse bate-papo.</span><span class="sxs-lookup"><span data-stu-id="ad68b-127">In a group chat, contains information specific to that chat.</span></span>
* <span data-ttu-id="ad68b-128">`conversation.id` O ID da cadeia de resposta, que consiste no ID do canal mais o ID da primeira mensagem na cadeia de resposta.</span><span class="sxs-lookup"><span data-stu-id="ad68b-128">`conversation.id` The reply chain ID, consisting of channel ID plus the ID of the first message in the reply chain.</span></span>
* <span data-ttu-id="ad68b-129">`conversation.isGroup` É `true` para mensagens de bot em canais ou chats em grupo.</span><span class="sxs-lookup"><span data-stu-id="ad68b-129">`conversation.isGroup` Is `true` for bot messages in channels or group chats.</span></span>
* <span data-ttu-id="ad68b-130">`conversation.conversationType` Ou você `groupChat` `channel` ou.</span><span class="sxs-lookup"><span data-stu-id="ad68b-130">`conversation.conversationType` Either `groupChat` or `channel`.</span></span>
* <span data-ttu-id="ad68b-131">`entities` Pode conter uma ou mais menções.</span><span class="sxs-lookup"><span data-stu-id="ad68b-131">`entities` Can contain one or more mentions.</span></span> <span data-ttu-id="ad68b-132">Para obter mais informações, consulte [Mentions](#-mentions).</span><span class="sxs-lookup"><span data-stu-id="ad68b-132">For more information, see [Mentions](#-mentions).</span></span>

### <a name="replying-to-messages"></a><span data-ttu-id="ad68b-133">Respondendo às mensagens</span><span class="sxs-lookup"><span data-stu-id="ad68b-133">Replying to messages</span></span>

<span data-ttu-id="ad68b-134">Para responder a uma mensagem existente, ligue [`ReplyToActivity`](/bot-framework/dotnet/bot-builder-dotnet-connector#send-a-reply) para .NET ou [`session.send`](/bot-framework/nodejs/bot-builder-nodejs-use-default-message-handler) em Node.js.</span><span class="sxs-lookup"><span data-stu-id="ad68b-134">To reply to an existing message, call [`ReplyToActivity`](/bot-framework/dotnet/bot-builder-dotnet-connector#send-a-reply) in .NET or [`session.send`](/bot-framework/nodejs/bot-builder-nodejs-use-default-message-handler) in Node.js.</span></span> <span data-ttu-id="ad68b-135">O Bot Builder SDK lida com todos os detalhes.</span><span class="sxs-lookup"><span data-stu-id="ad68b-135">The Bot Builder SDK handles all the details.</span></span>

<span data-ttu-id="ad68b-136">Se você optar por usar a API REST, você também pode chamar o [`/conversations/{conversationId}/activities/{activityId}`](/bot-framework/rest-api/bot-framework-rest-connector-send-and-receive-messages#send-the-reply) ponto final.</span><span class="sxs-lookup"><span data-stu-id="ad68b-136">If you choose to use the REST API, you can also call the [`/conversations/{conversationId}/activities/{activityId}`](/bot-framework/rest-api/bot-framework-rest-connector-send-and-receive-messages#send-the-reply) endpoint.</span></span>

<span data-ttu-id="ad68b-137">Em um canal, responder a uma mensagem mostra como resposta à cadeia de resposta inicial.</span><span class="sxs-lookup"><span data-stu-id="ad68b-137">In a channel, replying to a message shows as a reply to the initiating reply chain.</span></span> <span data-ttu-id="ad68b-138">O `conversation.id` contém o canal e o ID de mensagem de nível superior.</span><span class="sxs-lookup"><span data-stu-id="ad68b-138">The `conversation.id` contains the channel and the top level message ID.</span></span> <span data-ttu-id="ad68b-139">Embora o Bot Framework cuide dos detalhes, você pode armazenar isso `conversation.id` para respostas futuras a esse segmento de conversa, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="ad68b-139">Although the Bot Framework takes care of the details, you can cache that `conversation.id` for future replies to that conversation thread as needed.</span></span>

### <a name="best-practice-welcome-messages-in-teams"></a><span data-ttu-id="ad68b-140">Melhores práticas: Mensagens de boas-vindas em Teams</span><span class="sxs-lookup"><span data-stu-id="ad68b-140">Best practice: Welcome messages in Teams</span></span>

<span data-ttu-id="ad68b-141">Quando o seu bot é adicionado pela primeira vez ao grupo ou equipe, geralmente é útil enviar uma mensagem de boas-vindas apresentando o bot a todos os usuários.</span><span class="sxs-lookup"><span data-stu-id="ad68b-141">When your bot is first added to the group or team, it is generally useful to send a welcome message introducing the bot to all users.</span></span> <span data-ttu-id="ad68b-142">A mensagem de boas-vindas deve fornecer uma descrição da funcionalidade do bot e dos benefícios do usuário.</span><span class="sxs-lookup"><span data-stu-id="ad68b-142">The welcome message should provide a description of the bot’s functionality and user benefits.</span></span> <span data-ttu-id="ad68b-143">Idealmente, a mensagem também deve incluir comandos para o usuário interagir com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ad68b-143">Ideally the message should also include commands for the user to interact with the app.</span></span> <span data-ttu-id="ad68b-144">Para fazer isso, certifique-se de que seu bot responda à `conversationUpdate` mensagem, com o `teamsAddMembers` eventType no `channelData` objeto.</span><span class="sxs-lookup"><span data-stu-id="ad68b-144">To do this, ensure that your bot responds to the `conversationUpdate` message, with the `teamsAddMembers` eventType in the `channelData` object.</span></span> <span data-ttu-id="ad68b-145">Certifique-se de que o `memberAdded` ID é o próprio App ID do bot, pois o mesmo evento é enviado quando um usuário é adicionado a uma equipe.</span><span class="sxs-lookup"><span data-stu-id="ad68b-145">Be sure that the `memberAdded` ID is the bot's App ID itself, because the same event is sent when a user is added to a team.</span></span> <span data-ttu-id="ad68b-146">Consulte [a adição de membro da equipe ou bot](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="ad68b-146">See [Team member or bot addition](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) for more details.</span></span>

<span data-ttu-id="ad68b-147">Você também pode querer enviar uma mensagem pessoal para cada membro da equipe quando o bot for adicionado.</span><span class="sxs-lookup"><span data-stu-id="ad68b-147">You might also want to send a personal message to each member of the team when the bot is added.</span></span> <span data-ttu-id="ad68b-148">Para fazer isso, você pode [buscar a lista da equipe](~/resources/bot-v3/bots-context.md#fetch-the-team-roster) e enviar uma [mensagem direta](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md)a cada usuário .</span><span class="sxs-lookup"><span data-stu-id="ad68b-148">To do this, you could [fetch the team roster](~/resources/bot-v3/bots-context.md#fetch-the-team-roster) and send each user a [direct message](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md).</span></span>

<span data-ttu-id="ad68b-149">Recomendamos que seu bot *não* envie uma mensagem de boas-vindas nas seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="ad68b-149">We recommend that your bot *not* send a welcome message in the following situations:</span></span>

* <span data-ttu-id="ad68b-150">A equipe é grande (obviamente subjetiva, por exemplo, mais de 100 membros).</span><span class="sxs-lookup"><span data-stu-id="ad68b-150">The team is big (obviously subjective, for example, more than 100 members).</span></span> <span data-ttu-id="ad68b-151">Seu bot pode ser visto como 'spammy' e a pessoa que o adicionou pode receber reclamações, a menos que você comunique claramente a proposta de valor do seu bot para todos que virem a mensagem de boas-vindas.</span><span class="sxs-lookup"><span data-stu-id="ad68b-151">Your bot may be seen as 'spammy' and the person who added it may get complaints unless you clearly communicate your bot's value proposition to everyone who sees the welcome message.</span></span>
* <span data-ttu-id="ad68b-152">Seu bot é mencionado pela primeira vez em um grupo ou canal, em vez de ser adicionado pela primeira vez a uma equipe.</span><span class="sxs-lookup"><span data-stu-id="ad68b-152">Your bot is first mentioned in a group or channel, versus being first added to a team.</span></span>
* <span data-ttu-id="ad68b-153">Um grupo ou canal é renomeado.</span><span class="sxs-lookup"><span data-stu-id="ad68b-153">A group or channel is renamed.</span></span>
* <span data-ttu-id="ad68b-154">Um membro da equipe é adicionado a um grupo ou canal.</span><span class="sxs-lookup"><span data-stu-id="ad68b-154">A team member is added to a group or channel.</span></span>

## <a name="-mentions"></a><span data-ttu-id="ad68b-155">@ Menções</span><span class="sxs-lookup"><span data-stu-id="ad68b-155">@ Mentions</span></span>

<span data-ttu-id="ad68b-156">Como os bots em um grupo ou canal respondem apenas quando são mencionados ("@_botname_") em uma mensagem, cada mensagem recebida por um bot em um canal de grupo contém seu próprio nome, e você deve garantir que sua mensagem de análise seja manipulação disso.</span><span class="sxs-lookup"><span data-stu-id="ad68b-156">Because bots in a group or channel respond only when they are mentioned ("@_botname_") in a message, every message received by a bot in a group channel contains its own name, and you must ensure your message parsing handles that.</span></span> <span data-ttu-id="ad68b-157">Além disso, os bots podem analisar outros usuários mencionados e mencionar os usuários como parte de suas mensagens.</span><span class="sxs-lookup"><span data-stu-id="ad68b-157">In addition, bots can parse out other users mentioned and mention users as part of their messages.</span></span>

### <a name="retrieving-mentions"></a><span data-ttu-id="ad68b-158">Recuperando menções</span><span class="sxs-lookup"><span data-stu-id="ad68b-158">Retrieving mentions</span></span>

<span data-ttu-id="ad68b-159">As menções são devolvidas no `entities` objeto em carga útil e contêm tanto o ID exclusivo do usuário quanto, na maioria dos casos, o nome do usuário mencionado.</span><span class="sxs-lookup"><span data-stu-id="ad68b-159">Mentions are returned in the `entities` object in payload and contain both the unique ID of the user and, in most cases, the name of user mentioned.</span></span> <span data-ttu-id="ad68b-160">Você pode recuperar todas as menções na mensagem chamando a `GetMentions` função no Bot Builder SDK para .NET, que retorna uma matriz de `Mentioned` objetos.</span><span class="sxs-lookup"><span data-stu-id="ad68b-160">You can retrieve all mentions in the message by calling the `GetMentions` function in the Bot Builder SDK for .NET, which returns an array of `Mentioned` objects.</span></span>

#### <a name="net-example-code-check-for-and-strip-bot-mention"></a><span data-ttu-id="ad68b-161">Código de exemplo .NET: Verifique e despoja @bot menção</span><span class="sxs-lookup"><span data-stu-id="ad68b-161">.NET example code: Check for and strip @bot mention</span></span>

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
> <span data-ttu-id="ad68b-162">Você também pode usar a função de extensão `GetTextWithoutMentions` Teams, que tira todas as menções, incluindo o bot.</span><span class="sxs-lookup"><span data-stu-id="ad68b-162">You can also use the Teams extension function `GetTextWithoutMentions`, which strips out all mentions, including the bot.</span></span>

#### <a name="nodejs-example-code-check-for-and-strip-bot-mention"></a><span data-ttu-id="ad68b-163">código de exemplo Node.js: Verifique e tire @bot menção</span><span class="sxs-lookup"><span data-stu-id="ad68b-163">Node.js example code: Check for and strip @bot mention</span></span>

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

<span data-ttu-id="ad68b-164">Você também pode usar a função de extensão `getTextWithoutMentions` Teams, que tira todas as menções, incluindo o bot.</span><span class="sxs-lookup"><span data-stu-id="ad68b-164">You can also use the Teams extension function `getTextWithoutMentions`, which strips out all mentions, including the bot.</span></span>

### <a name="constructing-mentions"></a><span data-ttu-id="ad68b-165">Construindo menções</span><span class="sxs-lookup"><span data-stu-id="ad68b-165">Constructing mentions</span></span>

<span data-ttu-id="ad68b-166">Seu bot pode mencionar outros usuários em mensagens postadas em canais.</span><span class="sxs-lookup"><span data-stu-id="ad68b-166">Your bot can mention other users in messages posted into channels.</span></span> <span data-ttu-id="ad68b-167">Para fazer isso, sua mensagem deve fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ad68b-167">To do this, your message must do the following:</span></span>

* <span data-ttu-id="ad68b-168">Inclua `<at>@username</at>` no texto da mensagem.</span><span class="sxs-lookup"><span data-stu-id="ad68b-168">Include `<at>@username</at>` in the message text.</span></span>
* <span data-ttu-id="ad68b-169">Inclua o `mention` objeto dentro da coleção de entidades.</span><span class="sxs-lookup"><span data-stu-id="ad68b-169">Include the `mention` object inside the entities collection.</span></span>

#### <a name="net-example"></a><span data-ttu-id="ad68b-170">Exemplo .NET</span><span class="sxs-lookup"><span data-stu-id="ad68b-170">.NET example</span></span>

<span data-ttu-id="ad68b-171">Este exemplo usa o pacote [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet.</span><span class="sxs-lookup"><span data-stu-id="ad68b-171">This example uses the [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet package.</span></span>

```csharp
// Create reply activity
Activity replyActivity = activity.CreateReply();

// Construct text of the form @sender Hello
replyActivity.Text = "Hello ";
replyActivity.AddMentionToText(activity.From, MentionTextLocation.AppendText);

// Send the reply activity
await client.Conversations.ReplyToActivityAsync(replyActivity);
```

#### <a name="nodejs-example"></a><span data-ttu-id="ad68b-172">Node.js exemplo</span><span class="sxs-lookup"><span data-stu-id="ad68b-172">Node.js example</span></span>

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

#### <a name="example-outgoing-message-with-user-mentioned"></a><span data-ttu-id="ad68b-173">Exemplo: Mensagem de saída com usuário mencionado</span><span class="sxs-lookup"><span data-stu-id="ad68b-173">Example: Outgoing message with user mentioned</span></span>

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

## <a name="accessing-groupchat-or-channel-scope"></a><span data-ttu-id="ad68b-174">Acessando o grupoChat ou escopo do canal</span><span class="sxs-lookup"><span data-stu-id="ad68b-174">Accessing groupChat or channel scope</span></span>

<span data-ttu-id="ad68b-175">Seu bot pode fazer mais do que enviar e receber mensagens em grupos e equipes.</span><span class="sxs-lookup"><span data-stu-id="ad68b-175">Your bot can do more than send and receive messages in groups and teams.</span></span> <span data-ttu-id="ad68b-176">Por exemplo, ele também pode buscar a lista de membros, incluindo suas informações de perfil, bem como a lista de canais.</span><span class="sxs-lookup"><span data-stu-id="ad68b-176">For instance, it can also fetch the list of members, including their profile information, as well as the list of channels.</span></span> <span data-ttu-id="ad68b-177">Para obter mais informações, consulte [Obter contexto para o seu Microsoft Teams bot](~/resources/bot-v3/bots-context.md).</span><span class="sxs-lookup"><span data-stu-id="ad68b-177">For more information, see [Get context for your Microsoft Teams bot](~/resources/bot-v3/bots-context.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ad68b-178">Confira também</span><span class="sxs-lookup"><span data-stu-id="ad68b-178">See also</span></span>

[<span data-ttu-id="ad68b-179">Amostras do Bot Framework</span><span class="sxs-lookup"><span data-stu-id="ad68b-179">Bot Framework samples</span></span>](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)
