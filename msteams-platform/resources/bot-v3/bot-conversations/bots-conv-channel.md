---
title: Conversas de chat de grupo e canal com bots
description: Descreve o cenário de ponta a ponta de ter uma conversa com um bot em um canal no Microsoft Teams
keywords: bot de conversa de canais de cenários de equipe
ms.date: 06/25/2019
ms.openlocfilehash: d2d72bdba43de6ebb10c7504dd309459cb09d56c
ms.sourcegitcommit: 6c5c0574228310f844c81df0d57f11e2037e90c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "42227994"
---
# <a name="channel-and-group-chat-conversations-with-a-microsoft-teams-bot"></a><span data-ttu-id="da7df-104">Conversas de chat de grupo e canal com um bot do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="da7df-104">Channel and Group chat conversations with a Microsoft Teams bot</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="da7df-105">O Microsoft Teams permite que os usuários tragam bots para suas conversas de chat de grupo ou canal.</span><span class="sxs-lookup"><span data-stu-id="da7df-105">Microsoft Teams allows users to bring bots into their channel or group chat conversations.</span></span> <span data-ttu-id="da7df-106">Ao adicionar um bot a uma equipe ou chat, todos os usuários da conversa podem aproveitar o direito de funcionalidade de bot na conversa.</span><span class="sxs-lookup"><span data-stu-id="da7df-106">By adding a bot to a team or chat, all users of the conversation can take advantage of the bot functionality right in the conversation.</span></span> <span data-ttu-id="da7df-107">Você também pode acessar a funcionalidade específica do teams no seu bot, como consultar informações da equipe de consulta e usuários do @mentioning.</span><span class="sxs-lookup"><span data-stu-id="da7df-107">You can also access Teams-specific functionality within your bot like querying team information and @mentioning users.</span></span>

<span data-ttu-id="da7df-108">O chat em canais e chats de grupo diferem do bate-papo pessoal, pois o usuário precisa @mention o bot.</span><span class="sxs-lookup"><span data-stu-id="da7df-108">Chat in channels and group chats differ from personal chat in that the user needs to @mention the bot.</span></span> <span data-ttu-id="da7df-109">Se um bot for usado em vários escopos (pessoal, Groupchat ou canal), você precisará detectar de qual escopo as mensagens de bot vieram e processá-las de acordo.</span><span class="sxs-lookup"><span data-stu-id="da7df-109">If a bot is used in multiple scopes (personal, groupchat or channel) you will need to detect what scope the bot messages came from, and process them accordingly.</span></span>

## <a name="designing-a-great-bot-for-channels-or-groups"></a><span data-ttu-id="da7df-110">Criando um ótimo bot para canais ou grupos</span><span class="sxs-lookup"><span data-stu-id="da7df-110">Designing a great bot for channels or groups</span></span>

<span data-ttu-id="da7df-111">Os bots adicionados a uma equipe se tornarão outro membro da equipe, que pode ser @mentioned como parte da conversa.</span><span class="sxs-lookup"><span data-stu-id="da7df-111">Bots added to a team become another team member, who can be @mentioned as part of the conversation.</span></span> <span data-ttu-id="da7df-112">Na verdade, os bots só recebem mensagens quando estão @mentioned, portanto, outras conversas no canal não são enviadas para o bot.</span><span class="sxs-lookup"><span data-stu-id="da7df-112">In fact, bots only receive messages when they are @mentioned, so other conversations on the channel are not sent to the bot.</span></span>

> [!NOTE]
> <span data-ttu-id="da7df-113">Para conveniência ao responder a mensagens de bot em um canal, o nome do bot é anexado automaticamente na caixa de mensagem de composição.</span><span class="sxs-lookup"><span data-stu-id="da7df-113">For convenience when replying to bot messages in a channel, the bot name is prepended in the compose message box automatically.</span></span>

<span data-ttu-id="da7df-114">Um bot em um grupo ou canal deve fornecer informações relevantes e apropriadas para todos os membros.</span><span class="sxs-lookup"><span data-stu-id="da7df-114">A bot in a group or channel should provide information relevant and appropriate for all members.</span></span> <span data-ttu-id="da7df-115">Embora seu bot possa, certamente, fornecer qualquer informação relevante para a experiência, lembre-se de que as conversas com ela são visíveis para todos.</span><span class="sxs-lookup"><span data-stu-id="da7df-115">While your bot can certainly provide any information relevant to the experience, keep in mind conversations with it are visible to everyone.</span></span> <span data-ttu-id="da7df-116">Portanto, um grande bot em um grupo ou canal deve adicionar valor a todos os usuários e certamente não compartilha inadvertidamente as informações mais apropriadas em uma conversa de um para um.</span><span class="sxs-lookup"><span data-stu-id="da7df-116">Therefore, a great bot in a group or channel should add value to all users, and certainly not inadvertently share information more appropriate in a one-to-one conversation.</span></span>

<span data-ttu-id="da7df-117">Seu bot pode ser totalmente relevante em todos os escopos como está, e não é necessário nenhum trabalho extra significativo para permitir que o bot funcione entre eles.</span><span class="sxs-lookup"><span data-stu-id="da7df-117">Your bot might be entirely relevant in all scopes as is, and no significant extra work is required to allow your bot to work across them.</span></span> <span data-ttu-id="da7df-118">No Microsoft Teams, não há nenhuma expectativa de que seu bot funcione em todos os escopos, mas você deve garantir que seu bot forneça o valor do usuário em qualquer escopo para o qual você opte por oferecer suporte.</span><span class="sxs-lookup"><span data-stu-id="da7df-118">In Microsoft Teams there is no expectation that your bot function in all scopes, but you should ensure your bot provides user value in whichever scope(s) you choose to support.</span></span> <span data-ttu-id="da7df-119">Para obter mais informações sobre escopos, consulte [aplicativos no Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md).</span><span class="sxs-lookup"><span data-stu-id="da7df-119">For more information on scopes, see [Apps in Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md).</span></span>

<span data-ttu-id="da7df-120">O desenvolvimento de um bot que funciona em grupos ou canais usa grande parte da mesma funcionalidade de conversas pessoais.</span><span class="sxs-lookup"><span data-stu-id="da7df-120">Developing a bot that works in groups or channels uses much of the same functionality from personal conversations.</span></span> <span data-ttu-id="da7df-121">Eventos e dados adicionais na carga fornecem informações de grupo e canal do teams.</span><span class="sxs-lookup"><span data-stu-id="da7df-121">Additional events and data in the payload provide Teams group and channel information.</span></span> <span data-ttu-id="da7df-122">Essas diferenças, bem como as principais diferenças em funcionalidades comuns, são descritas nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="da7df-122">Those differences, as well as key differences in common functionality are described in the following sections.</span></span>

### <a name="creating-messages"></a><span data-ttu-id="da7df-123">Criar mensagens</span><span class="sxs-lookup"><span data-stu-id="da7df-123">Creating messages</span></span>

<span data-ttu-id="da7df-124">Para obter mais informações sobre bots Criando mensagens em canais, consulte [Proactive Messaging for bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md), e especificamente [criando uma conversa de canal](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md#creating-a-channel-conversation).</span><span class="sxs-lookup"><span data-stu-id="da7df-124">For more information on bots creating messages in channels see [Proactive messaging for bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md), and specifically [Creating a channel conversation](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md#creating-a-channel-conversation).</span></span>

### <a name="receiving-messages"></a><span data-ttu-id="da7df-125">Receber mensagens</span><span class="sxs-lookup"><span data-stu-id="da7df-125">Receiving messages</span></span>

<span data-ttu-id="da7df-126">Para um bot em um grupo ou canal, além do esquema de [mensagem regular](https://docs.botframework.com/core-concepts/reference/#activity), seu bot também recebe as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="da7df-126">For a bot in a group or channel, in addition to the [regular message schema](https://docs.botframework.com/core-concepts/reference/#activity), your bot also receives the following properties:</span></span>

* <span data-ttu-id="da7df-127">`channelData`Consulte [dados do canal do teams](~/resources/bot-v3/bot-conversations/bots-conversations.md#teams-channel-data).</span><span class="sxs-lookup"><span data-stu-id="da7df-127">`channelData` See [Teams channel data](~/resources/bot-v3/bot-conversations/bots-conversations.md#teams-channel-data).</span></span> <span data-ttu-id="da7df-128">Em um chat de grupo, contém informações específicas desse chat.</span><span class="sxs-lookup"><span data-stu-id="da7df-128">In a group chat, contains information specific to that chat.</span></span>
* <span data-ttu-id="da7df-129">`conversation.id`A ID da cadeia de resposta, consistindo na ID do canal mais a ID da primeira mensagem na cadeia de resposta</span><span class="sxs-lookup"><span data-stu-id="da7df-129">`conversation.id` The reply chain ID, consisting of channel ID plus the ID of the first message in the reply chain</span></span>
* <span data-ttu-id="da7df-130">`conversation.isGroup`É `true` para mensagens de bot em canais ou chats de grupo</span><span class="sxs-lookup"><span data-stu-id="da7df-130">`conversation.isGroup` Is `true` for bot messages in channels or group chats</span></span>
* <span data-ttu-id="da7df-131">`conversation.conversationType`Um `groupChat` ou`channel`</span><span class="sxs-lookup"><span data-stu-id="da7df-131">`conversation.conversationType` Either `groupChat` or `channel`</span></span>
* <span data-ttu-id="da7df-132">`entities`Podem conter uma ou mais mencionas (consulte [mencionas](#-mentions))</span><span class="sxs-lookup"><span data-stu-id="da7df-132">`entities` Can contain one or more mentions (see [Mentions](#-mentions))</span></span>

### <a name="replying-to-messages"></a><span data-ttu-id="da7df-133">Respondendo a mensagens</span><span class="sxs-lookup"><span data-stu-id="da7df-133">Replying to messages</span></span>

<span data-ttu-id="da7df-134">Para responder a uma mensagem existente, chame [`ReplyToActivity`](/bot-framework/dotnet/bot-builder-dotnet-connector#send-a-reply) no .net ou [`session.send`](/bot-framework/nodejs/bot-builder-nodejs-use-default-message-handler) no node. js.</span><span class="sxs-lookup"><span data-stu-id="da7df-134">To reply to an existing message, call [`ReplyToActivity`](/bot-framework/dotnet/bot-builder-dotnet-connector#send-a-reply) in .NET or [`session.send`](/bot-framework/nodejs/bot-builder-nodejs-use-default-message-handler) in Node.js.</span></span> <span data-ttu-id="da7df-135">O SDK do bot Builder trata de todos os detalhes.</span><span class="sxs-lookup"><span data-stu-id="da7df-135">The Bot Builder SDK handles all the details.</span></span>

<span data-ttu-id="da7df-136">Se você optar por usar a API REST, também poderá chamar o ponto [`/conversations/{conversationId}/activities/{activityId}`](/bot-framework/rest-api/bot-framework-rest-connector-send-and-receive-messages#send-the-reply) de extremidade.</span><span class="sxs-lookup"><span data-stu-id="da7df-136">If you choose to use the REST API, you can also call the [`/conversations/{conversationId}/activities/{activityId}`](/bot-framework/rest-api/bot-framework-rest-connector-send-and-receive-messages#send-the-reply) endpoint.</span></span>

<span data-ttu-id="da7df-137">Em um canal, responder a uma mensagem é exibido como uma resposta para a cadeia de resposta inicial.</span><span class="sxs-lookup"><span data-stu-id="da7df-137">In a channel, replying to a message shows as a reply to the initiating reply chain.</span></span> <span data-ttu-id="da7df-138">O `conversation.id` contém o canal e a ID da mensagem de nível superior.</span><span class="sxs-lookup"><span data-stu-id="da7df-138">The `conversation.id` contains the channel and the top level message ID.</span></span> <span data-ttu-id="da7df-139">Embora a estrutura de bot se encarrega dos detalhes, você pode armazenar em `conversation.id` cache as respostas futuras para esse segmento de conversa, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="da7df-139">Although the Bot Framework takes care of the details, you can cache that `conversation.id` for future replies to that conversation thread as needed.</span></span>

### <a name="best-practice-welcome-messages-in-teams"></a><span data-ttu-id="da7df-140">Práticas recomendadas: mensagens de boas-vindas no Teams</span><span class="sxs-lookup"><span data-stu-id="da7df-140">Best practice: Welcome messages in Teams</span></span>

<span data-ttu-id="da7df-141">Quando seu bot é adicionado ao grupo ou equipe, geralmente é útil enviar uma mensagem de boas-vindas apresentando o bot para todos os usuários.</span><span class="sxs-lookup"><span data-stu-id="da7df-141">When your bot is first added to the group or team, it is generally useful to send a welcome message introducing the bot to all users.</span></span> <span data-ttu-id="da7df-142">A mensagem de boas-vindas deve fornecer uma descrição da funcionalidade do bot e dos benefícios do usuário.</span><span class="sxs-lookup"><span data-stu-id="da7df-142">The welcome message should provide a description of the bot’s functionality and user benefits.</span></span> <span data-ttu-id="da7df-143">O ideal é que a mensagem também inclua comandos para o usuário interagir com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="da7df-143">Ideally the message should also include commands for the user to interact with the app.</span></span> <span data-ttu-id="da7df-144">Para fazer isso, certifique-se de que seu bot `conversationUpdate` responda à mensagem com `teamsAddMembers` o EventType no `channelData` objeto.</span><span class="sxs-lookup"><span data-stu-id="da7df-144">To do this, ensure that your bot responds to the `conversationUpdate` message, with the `teamsAddMembers` eventType in the `channelData` object.</span></span> <span data-ttu-id="da7df-145">Certifique-se de `memberAdded` que a ID é a própria ID de aplicativo do bot, porque o mesmo evento é enviado quando um usuário é adicionado a uma equipe.</span><span class="sxs-lookup"><span data-stu-id="da7df-145">Be sure that the `memberAdded` ID is the bot's App ID itself, because the same event is sent when a user is added to a team.</span></span> <span data-ttu-id="da7df-146">Confira o [membro da equipe ou a adição de bot](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="da7df-146">See [Team member or bot addition](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) for more details.</span></span>

<span data-ttu-id="da7df-147">Você também pode querer enviar uma mensagem pessoal para cada membro da equipe quando o bot é adicionado.</span><span class="sxs-lookup"><span data-stu-id="da7df-147">You might also want to send a personal message to each member of the team when the bot is added.</span></span> <span data-ttu-id="da7df-148">Para fazer isso, você poderia [buscar a lista de equipes](~/resources/bot-v3/bots-context.md#fetching-the-team-roster) e enviar uma [mensagem direta](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md)a cada usuário.</span><span class="sxs-lookup"><span data-stu-id="da7df-148">To do this, you could [fetch the team roster](~/resources/bot-v3/bots-context.md#fetching-the-team-roster) and send each user a [direct message](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md).</span></span>

<span data-ttu-id="da7df-149">Recomendamos que o bot *não* envie uma mensagem de boas-vindas nas seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="da7df-149">We recommend that your bot *not* send a welcome message in the following situations:</span></span>

* <span data-ttu-id="da7df-150">A equipe é grande (obviamente subjetiva, mas por exemplo, mais de 100 membros).</span><span class="sxs-lookup"><span data-stu-id="da7df-150">The team is large (obviously subjective, but for example larger than 100 members).</span></span> <span data-ttu-id="da7df-151">Seu bot pode ser visto como ' spam ' e a pessoa que o adicionou pode receber reclamações, a menos que você comunique claramente a proposta de valor do bot para todos os usuários que veem a mensagem de boas-vindas.</span><span class="sxs-lookup"><span data-stu-id="da7df-151">Your bot may be seen as 'spammy' and the person who added it may get complaints unless you clearly communicate your bot's value proposition to everyone who sees the welcome message.</span></span>
* <span data-ttu-id="da7df-152">Seu bot é mencionado pela primeira vez em um grupo ou canal (em vez de ser adicionado a uma equipe)</span><span class="sxs-lookup"><span data-stu-id="da7df-152">Your bot is first mentioned in a group or channel (versus being first added to a team)</span></span>
* <span data-ttu-id="da7df-153">Um grupo ou canal é renomeado</span><span class="sxs-lookup"><span data-stu-id="da7df-153">A group or channel is renamed</span></span>
* <span data-ttu-id="da7df-154">Um membro da equipe é adicionado a um grupo ou canal</span><span class="sxs-lookup"><span data-stu-id="da7df-154">A team member is added to a group or channel</span></span>

## <a name="-mentions"></a><span data-ttu-id="da7df-155">@ Menciona</span><span class="sxs-lookup"><span data-stu-id="da7df-155">@ Mentions</span></span>

<span data-ttu-id="da7df-156">Como os bots em um grupo ou canal respondem apenas quando são mencionados ("@_botname_") em uma mensagem, cada mensagem recebida por um bot em um canal de grupo contém seu próprio nome e você deve garantir que as alças de análise da mensagem.</span><span class="sxs-lookup"><span data-stu-id="da7df-156">Because bots in a group or channel respond only when they are mentioned ("@_botname_") in a message, every message received by a bot in a group channel contains its own name, and you must ensure your message parsing handles that.</span></span> <span data-ttu-id="da7df-157">Além disso, os bots podem analisar outros usuários mencionados e mencionar os usuários como parte de suas mensagens.</span><span class="sxs-lookup"><span data-stu-id="da7df-157">In addition, bots can parse out other users mentioned and mention users as part of their messages.</span></span>

### <a name="retrieving-mentions"></a><span data-ttu-id="da7df-158">Como recuperar menção</span><span class="sxs-lookup"><span data-stu-id="da7df-158">Retrieving mentions</span></span>

<span data-ttu-id="da7df-159">As menção são retornadas no `entities` objeto no Payload e contêm a identificação exclusiva do usuário e, na maioria dos casos, o nome do usuário mencionado.</span><span class="sxs-lookup"><span data-stu-id="da7df-159">Mentions are returned in the `entities` object in payload and contain both the unique ID of the user and, in most cases, the name of user mentioned.</span></span> <span data-ttu-id="da7df-160">Você pode recuperar todas as menção na mensagem chamando a `GetMentions` função no SDK do bot Builder para .net, que retorna uma matriz de `Mentioned` objetos.</span><span class="sxs-lookup"><span data-stu-id="da7df-160">You can retrieve all mentions in the message by calling the `GetMentions` function in the Bot Builder SDK for .NET, which returns an array of `Mentioned` objects.</span></span>

#### <a name="net-example-code-check-for-and-strip-bot-mention"></a><span data-ttu-id="da7df-161">Código de exemplo .NET: verificar e remover @bot mencionar</span><span class="sxs-lookup"><span data-stu-id="da7df-161">.NET example code: Check for and strip @bot mention</span></span>

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
> <span data-ttu-id="da7df-162">Você também pode usar a função `GetTextWithoutMentions`de extensão do Teams, que retira todas as menção, incluindo o bot.</span><span class="sxs-lookup"><span data-stu-id="da7df-162">You can also use the Teams extension function `GetTextWithoutMentions`, which strips out all mentions, including the bot.</span></span>

#### <a name="nodejs-example-code-check-for-and-strip-bot-mention"></a><span data-ttu-id="da7df-163">Código de exemplo do node. js: verificar e remover @bot mencionar</span><span class="sxs-lookup"><span data-stu-id="da7df-163">Node.js example code: Check for and strip @bot mention</span></span>

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

<span data-ttu-id="da7df-164">Você também pode usar a função `getTextWithoutMentions`de extensão do Teams, que retira todas as menção, incluindo o bot.</span><span class="sxs-lookup"><span data-stu-id="da7df-164">You can also use the Teams extension function `getTextWithoutMentions`, which strips out all mentions, including the bot.</span></span>

### <a name="constructing-mentions"></a><span data-ttu-id="da7df-165">Como criar menção</span><span class="sxs-lookup"><span data-stu-id="da7df-165">Constructing mentions</span></span>

<span data-ttu-id="da7df-166">O bot pode mencionar outros usuários em mensagens postadas em canais.</span><span class="sxs-lookup"><span data-stu-id="da7df-166">Your bot can mention other users in messages posted into channels.</span></span> <span data-ttu-id="da7df-167">Para fazer isso, sua mensagem deve fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="da7df-167">To do this, your message must do the following:</span></span>

* <span data-ttu-id="da7df-168">Incluir `<at>@username</at>` no texto da mensagem</span><span class="sxs-lookup"><span data-stu-id="da7df-168">Include `<at>@username</at>` in the message text</span></span>
* <span data-ttu-id="da7df-169">Incluir o `mention` objeto dentro da coleção Entities</span><span class="sxs-lookup"><span data-stu-id="da7df-169">Include the `mention` object inside the entities collection</span></span>

#### <a name="net-example"></a><span data-ttu-id="da7df-170">Exemplo .NET</span><span class="sxs-lookup"><span data-stu-id="da7df-170">.NET example</span></span>

<span data-ttu-id="da7df-171">Este exemplo usa o pacote NuGet [Microsoft. bot. Connector. Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) .</span><span class="sxs-lookup"><span data-stu-id="da7df-171">This example uses the [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet package.</span></span>

```csharp
// Create reply activity
Activity replyActivity = activity.CreateReply();

// Construct text of the form @sender Hello
replyActivity.Text = "Hello ";
replyActivity.AddMentionToText(activity.From, MentionTextLocation.AppendText);

// Send the reply activity
await client.Conversations.ReplyToActivityAsync(replyActivity);
```

#### <a name="nodejs-example"></a><span data-ttu-id="da7df-172">Exemplo do node. js</span><span class="sxs-lookup"><span data-stu-id="da7df-172">Node.js example</span></span>

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

#### <a name="example-outgoing-message-with-user-mentioned"></a><span data-ttu-id="da7df-173">Exemplo: mensagem de saída com o usuário mencionado</span><span class="sxs-lookup"><span data-stu-id="da7df-173">Example: Outgoing message with user mentioned</span></span>

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

## <a name="accessing-groupchat-or-channel-scope"></a><span data-ttu-id="da7df-174">Acessando groupChat ou escopo de canal</span><span class="sxs-lookup"><span data-stu-id="da7df-174">Accessing groupChat or channel scope</span></span>

<span data-ttu-id="da7df-175">Seu bot pode fazer mais do que enviar e receber mensagens em grupos e equipes.</span><span class="sxs-lookup"><span data-stu-id="da7df-175">Your bot can do more than send and receive messages in groups and teams.</span></span> <span data-ttu-id="da7df-176">Por exemplo, também pode buscar a lista de membros, incluindo suas informações de perfil, bem como a lista de canais.</span><span class="sxs-lookup"><span data-stu-id="da7df-176">For instance, it can also fetch the list of members, including their profile information, as well as the list of channels.</span></span> <span data-ttu-id="da7df-177">Consulte [obter contexto para o bot do Microsoft Teams](~/resources/bot-v3/bots-context.md) para saber mais.</span><span class="sxs-lookup"><span data-stu-id="da7df-177">See [Get context for your Microsoft Teams bot](~/resources/bot-v3/bots-context.md) to learn more.</span></span>

<span data-ttu-id="da7df-178">*Confira também* [exemplos da estrutura de bot](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span><span class="sxs-lookup"><span data-stu-id="da7df-178">*See also* [Bot Framework samples](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span></span>
