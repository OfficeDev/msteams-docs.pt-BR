---
title: Conversas de chat de grupo e canal com bots
description: Descreve o cenário de ponta a ponta de ter uma conversa com um bot em um canal no Microsoft Teams
keywords: bot de conversa de canais de cenários de equipe
ms.date: 06/25/2019
ms.openlocfilehash: f44db4a88ab5e6541c52395a58fc643cb07df606
ms.sourcegitcommit: b3962a7b36f260aef1af9124d14d71ae08b01ac4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2020
ms.locfileid: "47303721"
---
# <a name="channel-and-group-chat-conversations-with-a-microsoft-teams-bot"></a><span data-ttu-id="48ed6-104">Conversas de chat de grupo e canal com um bot do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="48ed6-104">Channel and Group chat conversations with a Microsoft Teams bot</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="48ed6-105">O Microsoft Teams permite que os usuários tragam bots para suas conversas de chat de grupo ou canal.</span><span class="sxs-lookup"><span data-stu-id="48ed6-105">Microsoft Teams allows users to bring bots into their channel or group chat conversations.</span></span> <span data-ttu-id="48ed6-106">Ao adicionar um bot a uma equipe ou chat, todos os usuários da conversa podem aproveitar o direito de funcionalidade de bot na conversa.</span><span class="sxs-lookup"><span data-stu-id="48ed6-106">By adding a bot to a team or chat, all users of the conversation can take advantage of the bot functionality right in the conversation.</span></span> <span data-ttu-id="48ed6-107">Você também pode acessar a funcionalidade específica do teams no seu bot, como consultar informações da equipe de consulta e usuários do @mentioning.</span><span class="sxs-lookup"><span data-stu-id="48ed6-107">You can also access Teams-specific functionality within your bot like querying team information and @mentioning users.</span></span>

<span data-ttu-id="48ed6-108">O chat em canais e chats de grupo diferem do bate-papo pessoal, pois o usuário precisa @mention o bot.</span><span class="sxs-lookup"><span data-stu-id="48ed6-108">Chat in channels and group chats differ from personal chat in that the user needs to @mention the bot.</span></span> <span data-ttu-id="48ed6-109">Se um bot for usado em vários escopos (pessoal, Groupchat ou canal), você precisará detectar de qual escopo as mensagens de bot vieram e processá-las de acordo.</span><span class="sxs-lookup"><span data-stu-id="48ed6-109">If a bot is used in multiple scopes (personal, groupchat or channel) you will need to detect what scope the bot messages came from, and process them accordingly.</span></span>

## <a name="designing-a-great-bot-for-channels-or-groups"></a><span data-ttu-id="48ed6-110">Criando um ótimo bot para canais ou grupos</span><span class="sxs-lookup"><span data-stu-id="48ed6-110">Designing a great bot for channels or groups</span></span>

<span data-ttu-id="48ed6-111">Os bots adicionados a uma equipe se tornarão outro membro da equipe e poderão ser @mentioned como parte da conversa.</span><span class="sxs-lookup"><span data-stu-id="48ed6-111">Bots added to a team become another team member and can be @mentioned as part of the conversation.</span></span> <span data-ttu-id="48ed6-112">Na verdade, os bots só recebem mensagens quando estão @mentioned, portanto, outras conversas no canal não são enviadas para o bot.</span><span class="sxs-lookup"><span data-stu-id="48ed6-112">In fact, bots only receive messages when they are @mentioned, so other conversations on the channel are not sent to the bot.</span></span>

<span data-ttu-id="48ed6-113">Um bot em um grupo ou canal deve fornecer informações relevantes e apropriadas para todos os membros.</span><span class="sxs-lookup"><span data-stu-id="48ed6-113">A bot in a group or channel should provide information relevant and appropriate for all members.</span></span> <span data-ttu-id="48ed6-114">Embora seu bot possa, certamente, fornecer qualquer informação relevante para a experiência, lembre-se de que as conversas com ela são visíveis para todos.</span><span class="sxs-lookup"><span data-stu-id="48ed6-114">While your bot can certainly provide any information relevant to the experience, keep in mind conversations with it are visible to everyone.</span></span> <span data-ttu-id="48ed6-115">Portanto, um grande bot em um grupo ou canal deve adicionar valor a todos os usuários e certamente não compartilha inadvertidamente as informações mais apropriadas para uma conversa de um para um.</span><span class="sxs-lookup"><span data-stu-id="48ed6-115">Therefore, a great bot in a group or channel should add value to all users, and certainly not inadvertently share information more appropriate to a one-to-one conversation.</span></span>

<span data-ttu-id="48ed6-116">Seu bot, assim como é, pode ser totalmente relevante em todos os escopos sem exigir trabalho adicional.</span><span class="sxs-lookup"><span data-stu-id="48ed6-116">Your bot, just as it is, may be entirely relevant in all scopes without requiring additional work.</span></span> <span data-ttu-id="48ed6-117">No Microsoft Teams, não há nenhuma expectativa de que seu bot funcione em todos os escopos, mas você deve garantir que o seu bot forneça o valor do usuário em qualquer escopo (s) que você escolha dar suporte.</span><span class="sxs-lookup"><span data-stu-id="48ed6-117">In Microsoft Teams there is no expectation that your bot function in all scopes, but you should ensure that your bot provides user value in whichever scope(s) you choose to support.</span></span> <span data-ttu-id="48ed6-118">Para obter mais informações sobre escopos, consulte [aplicativos no Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md).</span><span class="sxs-lookup"><span data-stu-id="48ed6-118">For more information on scopes, see [Apps in Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md).</span></span>

<span data-ttu-id="48ed6-119">O desenvolvimento de um bot que funciona em grupos ou canais usa grande parte da mesma funcionalidade que as conversas pessoais.</span><span class="sxs-lookup"><span data-stu-id="48ed6-119">Developing a bot that works in groups or channels uses much of the same functionality as personal conversations.</span></span> <span data-ttu-id="48ed6-120">Eventos e dados adicionais na carga fornecem informações de grupo e canal do teams.</span><span class="sxs-lookup"><span data-stu-id="48ed6-120">Additional events and data in the payload provide Teams group and channel information.</span></span> <span data-ttu-id="48ed6-121">Essas diferenças, bem como as principais diferenças em funcionalidades comuns, são descritas nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="48ed6-121">Those differences, as well as key differences in common functionality are described in the following sections.</span></span>

### <a name="creating-messages"></a><span data-ttu-id="48ed6-122">Criar mensagens</span><span class="sxs-lookup"><span data-stu-id="48ed6-122">Creating messages</span></span>

<span data-ttu-id="48ed6-123">Para obter mais informações sobre bots Criando mensagens em canais, consulte [Proactive Messaging for bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md), e especificamente [criando uma conversa de canal](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md#creating-a-channel-conversation).</span><span class="sxs-lookup"><span data-stu-id="48ed6-123">For more information on bots creating messages in channels see [Proactive messaging for bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md), and specifically [Creating a channel conversation](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md#creating-a-channel-conversation).</span></span>

### <a name="receiving-messages"></a><span data-ttu-id="48ed6-124">Receber mensagens</span><span class="sxs-lookup"><span data-stu-id="48ed6-124">Receiving messages</span></span>

<span data-ttu-id="48ed6-125">Para um bot em um grupo ou canal, além do esquema de [mensagem regular](https://docs.botframework.com/core-concepts/reference/#activity), seu bot também recebe as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="48ed6-125">For a bot in a group or channel, in addition to the [regular message schema](https://docs.botframework.com/core-concepts/reference/#activity), your bot also receives the following properties:</span></span>

* <span data-ttu-id="48ed6-126">`channelData` Consulte [dados do canal do teams](~/resources/bot-v3/bot-conversations/bots-conversations.md#teams-channel-data).</span><span class="sxs-lookup"><span data-stu-id="48ed6-126">`channelData` See [Teams channel data](~/resources/bot-v3/bot-conversations/bots-conversations.md#teams-channel-data).</span></span> <span data-ttu-id="48ed6-127">Em um chat de grupo, contém informações específicas desse chat.</span><span class="sxs-lookup"><span data-stu-id="48ed6-127">In a group chat, contains information specific to that chat.</span></span>
* <span data-ttu-id="48ed6-128">`conversation.id` A ID da cadeia de resposta, consistindo na ID do canal mais a ID da primeira mensagem na cadeia de resposta</span><span class="sxs-lookup"><span data-stu-id="48ed6-128">`conversation.id` The reply chain ID, consisting of channel ID plus the ID of the first message in the reply chain</span></span>
* <span data-ttu-id="48ed6-129">`conversation.isGroup` É `true` para mensagens de bot em canais ou chats de grupo</span><span class="sxs-lookup"><span data-stu-id="48ed6-129">`conversation.isGroup` Is `true` for bot messages in channels or group chats</span></span>
* <span data-ttu-id="48ed6-130">`conversation.conversationType` Um `groupChat` ou `channel`</span><span class="sxs-lookup"><span data-stu-id="48ed6-130">`conversation.conversationType` Either `groupChat` or `channel`</span></span>
* <span data-ttu-id="48ed6-131">`entities` Podem conter uma ou mais mencionas (consulte [mencionas](#-mentions))</span><span class="sxs-lookup"><span data-stu-id="48ed6-131">`entities` Can contain one or more mentions (see [Mentions](#-mentions))</span></span>

### <a name="replying-to-messages"></a><span data-ttu-id="48ed6-132">Respondendo a mensagens</span><span class="sxs-lookup"><span data-stu-id="48ed6-132">Replying to messages</span></span>

<span data-ttu-id="48ed6-133">Para responder a uma mensagem existente, chame [`ReplyToActivity`](/bot-framework/dotnet/bot-builder-dotnet-connector#send-a-reply) no .net ou [`session.send`](/bot-framework/nodejs/bot-builder-nodejs-use-default-message-handler) em Node.js.</span><span class="sxs-lookup"><span data-stu-id="48ed6-133">To reply to an existing message, call [`ReplyToActivity`](/bot-framework/dotnet/bot-builder-dotnet-connector#send-a-reply) in .NET or [`session.send`](/bot-framework/nodejs/bot-builder-nodejs-use-default-message-handler) in Node.js.</span></span> <span data-ttu-id="48ed6-134">O SDK do bot Builder trata de todos os detalhes.</span><span class="sxs-lookup"><span data-stu-id="48ed6-134">The Bot Builder SDK handles all the details.</span></span>

<span data-ttu-id="48ed6-135">Se você optar por usar a API REST, também poderá chamar o [`/conversations/{conversationId}/activities/{activityId}`](/bot-framework/rest-api/bot-framework-rest-connector-send-and-receive-messages#send-the-reply) ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="48ed6-135">If you choose to use the REST API, you can also call the [`/conversations/{conversationId}/activities/{activityId}`](/bot-framework/rest-api/bot-framework-rest-connector-send-and-receive-messages#send-the-reply) endpoint.</span></span>

<span data-ttu-id="48ed6-136">Em um canal, responder a uma mensagem é exibido como uma resposta para a cadeia de resposta inicial.</span><span class="sxs-lookup"><span data-stu-id="48ed6-136">In a channel, replying to a message shows as a reply to the initiating reply chain.</span></span> <span data-ttu-id="48ed6-137">O `conversation.id` contém o canal e a ID da mensagem de nível superior.</span><span class="sxs-lookup"><span data-stu-id="48ed6-137">The `conversation.id` contains the channel and the top level message ID.</span></span> <span data-ttu-id="48ed6-138">Embora a estrutura de bot se encarrega dos detalhes, você pode armazenar em cache as `conversation.id` respostas futuras para esse segmento de conversa, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="48ed6-138">Although the Bot Framework takes care of the details, you can cache that `conversation.id` for future replies to that conversation thread as needed.</span></span>

### <a name="best-practice-welcome-messages-in-teams"></a><span data-ttu-id="48ed6-139">Práticas recomendadas: mensagens de boas-vindas no Teams</span><span class="sxs-lookup"><span data-stu-id="48ed6-139">Best practice: Welcome messages in Teams</span></span>

<span data-ttu-id="48ed6-140">Quando seu bot é adicionado ao grupo ou equipe, geralmente é útil enviar uma mensagem de boas-vindas apresentando o bot para todos os usuários.</span><span class="sxs-lookup"><span data-stu-id="48ed6-140">When your bot is first added to the group or team, it is generally useful to send a welcome message introducing the bot to all users.</span></span> <span data-ttu-id="48ed6-141">A mensagem de boas-vindas deve fornecer uma descrição da funcionalidade do bot e dos benefícios do usuário.</span><span class="sxs-lookup"><span data-stu-id="48ed6-141">The welcome message should provide a description of the bot’s functionality and user benefits.</span></span> <span data-ttu-id="48ed6-142">O ideal é que a mensagem também inclua comandos para o usuário interagir com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="48ed6-142">Ideally the message should also include commands for the user to interact with the app.</span></span> <span data-ttu-id="48ed6-143">Para fazer isso, certifique-se de que seu bot responda à `conversationUpdate` mensagem com o `teamsAddMembers` EventType no `channelData` objeto.</span><span class="sxs-lookup"><span data-stu-id="48ed6-143">To do this, ensure that your bot responds to the `conversationUpdate` message, with the `teamsAddMembers` eventType in the `channelData` object.</span></span> <span data-ttu-id="48ed6-144">Certifique-se de que a `memberAdded` ID é a própria ID de aplicativo do bot, porque o mesmo evento é enviado quando um usuário é adicionado a uma equipe.</span><span class="sxs-lookup"><span data-stu-id="48ed6-144">Be sure that the `memberAdded` ID is the bot's App ID itself, because the same event is sent when a user is added to a team.</span></span> <span data-ttu-id="48ed6-145">Confira o [membro da equipe ou a adição de bot](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="48ed6-145">See [Team member or bot addition](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) for more details.</span></span>

<span data-ttu-id="48ed6-146">Você também pode querer enviar uma mensagem pessoal para cada membro da equipe quando o bot é adicionado.</span><span class="sxs-lookup"><span data-stu-id="48ed6-146">You might also want to send a personal message to each member of the team when the bot is added.</span></span> <span data-ttu-id="48ed6-147">Para fazer isso, você poderia [buscar a lista de equipes](~/resources/bot-v3/bots-context.md#fetching-the-team-roster) e enviar uma [mensagem direta](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md)a cada usuário.</span><span class="sxs-lookup"><span data-stu-id="48ed6-147">To do this, you could [fetch the team roster](~/resources/bot-v3/bots-context.md#fetching-the-team-roster) and send each user a [direct message](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md).</span></span>

<span data-ttu-id="48ed6-148">Recomendamos que o bot *não* envie uma mensagem de boas-vindas nas seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="48ed6-148">We recommend that your bot *not* send a welcome message in the following situations:</span></span>

* <span data-ttu-id="48ed6-149">A equipe é grande (obviamente subjetiva, mas por exemplo, mais de 100 membros).</span><span class="sxs-lookup"><span data-stu-id="48ed6-149">The team is large (obviously subjective, but for example larger than 100 members).</span></span> <span data-ttu-id="48ed6-150">Seu bot pode ser visto como ' spam ' e a pessoa que o adicionou pode receber reclamações, a menos que você comunique claramente a proposta de valor do bot para todos os usuários que veem a mensagem de boas-vindas.</span><span class="sxs-lookup"><span data-stu-id="48ed6-150">Your bot may be seen as 'spammy' and the person who added it may get complaints unless you clearly communicate your bot's value proposition to everyone who sees the welcome message.</span></span>
* <span data-ttu-id="48ed6-151">Seu bot é mencionado pela primeira vez em um grupo ou canal (em vez de ser adicionado a uma equipe)</span><span class="sxs-lookup"><span data-stu-id="48ed6-151">Your bot is first mentioned in a group or channel (versus being first added to a team)</span></span>
* <span data-ttu-id="48ed6-152">Um grupo ou canal é renomeado</span><span class="sxs-lookup"><span data-stu-id="48ed6-152">A group or channel is renamed</span></span>
* <span data-ttu-id="48ed6-153">Um membro da equipe é adicionado a um grupo ou canal</span><span class="sxs-lookup"><span data-stu-id="48ed6-153">A team member is added to a group or channel</span></span>

## <a name="-mentions"></a><span data-ttu-id="48ed6-154">@ Menciona</span><span class="sxs-lookup"><span data-stu-id="48ed6-154">@ Mentions</span></span>

<span data-ttu-id="48ed6-155">Como os bots em um grupo ou canal respondem apenas quando são mencionados ("@_botname_") em uma mensagem, cada mensagem recebida por um bot em um canal de grupo contém seu próprio nome e você deve garantir que as alças de análise da mensagem.</span><span class="sxs-lookup"><span data-stu-id="48ed6-155">Because bots in a group or channel respond only when they are mentioned ("@_botname_") in a message, every message received by a bot in a group channel contains its own name, and you must ensure your message parsing handles that.</span></span> <span data-ttu-id="48ed6-156">Além disso, os bots podem analisar outros usuários mencionados e mencionar os usuários como parte de suas mensagens.</span><span class="sxs-lookup"><span data-stu-id="48ed6-156">In addition, bots can parse out other users mentioned and mention users as part of their messages.</span></span>

### <a name="retrieving-mentions"></a><span data-ttu-id="48ed6-157">Como recuperar menção</span><span class="sxs-lookup"><span data-stu-id="48ed6-157">Retrieving mentions</span></span>

<span data-ttu-id="48ed6-158">As menção são retornadas no `entities` objeto no Payload e contêm a identificação exclusiva do usuário e, na maioria dos casos, o nome do usuário mencionado.</span><span class="sxs-lookup"><span data-stu-id="48ed6-158">Mentions are returned in the `entities` object in payload and contain both the unique ID of the user and, in most cases, the name of user mentioned.</span></span> <span data-ttu-id="48ed6-159">Você pode recuperar todas as menção na mensagem chamando a `GetMentions` função no SDK do bot Builder para .net, que retorna uma matriz de `Mentioned` objetos.</span><span class="sxs-lookup"><span data-stu-id="48ed6-159">You can retrieve all mentions in the message by calling the `GetMentions` function in the Bot Builder SDK for .NET, which returns an array of `Mentioned` objects.</span></span>

#### <a name="net-example-code-check-for-and-strip-bot-mention"></a><span data-ttu-id="48ed6-160">Código de exemplo .NET: verificar e remover @bot mencionar</span><span class="sxs-lookup"><span data-stu-id="48ed6-160">.NET example code: Check for and strip @bot mention</span></span>

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
> <span data-ttu-id="48ed6-161">Você também pode usar a função de extensão do teams `GetTextWithoutMentions` , que retira todas as menção, incluindo o bot.</span><span class="sxs-lookup"><span data-stu-id="48ed6-161">You can also use the Teams extension function `GetTextWithoutMentions`, which strips out all mentions, including the bot.</span></span>

#### <a name="nodejs-example-code-check-for-and-strip-bot-mention"></a><span data-ttu-id="48ed6-162">Node.js código de exemplo: verificar e retirar @bot menção</span><span class="sxs-lookup"><span data-stu-id="48ed6-162">Node.js example code: Check for and strip @bot mention</span></span>

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

<span data-ttu-id="48ed6-163">Você também pode usar a função de extensão do teams `getTextWithoutMentions` , que retira todas as menção, incluindo o bot.</span><span class="sxs-lookup"><span data-stu-id="48ed6-163">You can also use the Teams extension function `getTextWithoutMentions`, which strips out all mentions, including the bot.</span></span>

### <a name="constructing-mentions"></a><span data-ttu-id="48ed6-164">Como criar menção</span><span class="sxs-lookup"><span data-stu-id="48ed6-164">Constructing mentions</span></span>

<span data-ttu-id="48ed6-165">O bot pode mencionar outros usuários em mensagens postadas em canais.</span><span class="sxs-lookup"><span data-stu-id="48ed6-165">Your bot can mention other users in messages posted into channels.</span></span> <span data-ttu-id="48ed6-166">Para fazer isso, sua mensagem deve fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="48ed6-166">To do this, your message must do the following:</span></span>

* <span data-ttu-id="48ed6-167">Incluir `<at>@username</at>` no texto da mensagem</span><span class="sxs-lookup"><span data-stu-id="48ed6-167">Include `<at>@username</at>` in the message text</span></span>
* <span data-ttu-id="48ed6-168">Incluir o `mention` objeto dentro da coleção Entities</span><span class="sxs-lookup"><span data-stu-id="48ed6-168">Include the `mention` object inside the entities collection</span></span>

#### <a name="net-example"></a><span data-ttu-id="48ed6-169">Exemplo .NET</span><span class="sxs-lookup"><span data-stu-id="48ed6-169">.NET example</span></span>

<span data-ttu-id="48ed6-170">Este exemplo usa o pacote NuGet [Microsoft. bot. Connector. Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) .</span><span class="sxs-lookup"><span data-stu-id="48ed6-170">This example uses the [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet package.</span></span>

```csharp
// Create reply activity
Activity replyActivity = activity.CreateReply();

// Construct text of the form @sender Hello
replyActivity.Text = "Hello ";
replyActivity.AddMentionToText(activity.From, MentionTextLocation.AppendText);

// Send the reply activity
await client.Conversations.ReplyToActivityAsync(replyActivity);
```

#### <a name="nodejs-example"></a><span data-ttu-id="48ed6-171">Exemplo de Node.js</span><span class="sxs-lookup"><span data-stu-id="48ed6-171">Node.js example</span></span>

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

#### <a name="example-outgoing-message-with-user-mentioned"></a><span data-ttu-id="48ed6-172">Exemplo: mensagem de saída com o usuário mencionado</span><span class="sxs-lookup"><span data-stu-id="48ed6-172">Example: Outgoing message with user mentioned</span></span>

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

## <a name="accessing-groupchat-or-channel-scope"></a><span data-ttu-id="48ed6-173">Acessando groupChat ou escopo de canal</span><span class="sxs-lookup"><span data-stu-id="48ed6-173">Accessing groupChat or channel scope</span></span>

<span data-ttu-id="48ed6-174">Seu bot pode fazer mais do que enviar e receber mensagens em grupos e equipes.</span><span class="sxs-lookup"><span data-stu-id="48ed6-174">Your bot can do more than send and receive messages in groups and teams.</span></span> <span data-ttu-id="48ed6-175">Por exemplo, também pode buscar a lista de membros, incluindo suas informações de perfil, bem como a lista de canais.</span><span class="sxs-lookup"><span data-stu-id="48ed6-175">For instance, it can also fetch the list of members, including their profile information, as well as the list of channels.</span></span> <span data-ttu-id="48ed6-176">Consulte [obter contexto para o bot do Microsoft Teams](~/resources/bot-v3/bots-context.md) para saber mais.</span><span class="sxs-lookup"><span data-stu-id="48ed6-176">See [Get context for your Microsoft Teams bot](~/resources/bot-v3/bots-context.md) to learn more.</span></span>

<span data-ttu-id="48ed6-177">*Confira também* [exemplos da estrutura de bot](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span><span class="sxs-lookup"><span data-stu-id="48ed6-177">*See also* [Bot Framework samples](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span></span>
