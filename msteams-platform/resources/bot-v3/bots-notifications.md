---
title: Manipular eventos de bot
description: Descreve como lidar com eventos em bots para Microsoft Teams
keywords: eventos de bots do teams
ms.date: 05/20/2019
ms.topic: how-to
localization_priority: Normal
ms.author: lajanuar
author: laujan
ms.openlocfilehash: da624ea0e92e193f4ad7f334d958349d542dd6e0
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566464"
---
# <a name="handle-bot-events-in-microsoft-teams"></a><span data-ttu-id="0c9f7-104">Manipular eventos de bot em Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="0c9f7-104">Handle bot events in Microsoft Teams</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="0c9f7-105">Microsoft Teams envia notificações ao bot para alterações ou eventos que ocorrem em escopos onde o bot está ativo.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-105">Microsoft Teams sends notifications to your bot for changes or events that happen in scopes where your bot is active.</span></span> <span data-ttu-id="0c9f7-106">Você pode usar esses eventos para disparar a lógica de serviço, como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0c9f7-106">You can use these events to trigger service logic, such as the following:</span></span>

* <span data-ttu-id="0c9f7-107">Acionar uma mensagem de boas-vindas quando seu bot for adicionado a uma equipe.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-107">Trigger a welcome message when your bot is added to a team.</span></span>
* <span data-ttu-id="0c9f7-108">Informações do grupo de consulta e cache quando o bot é adicionado a um chat de grupo.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-108">Query and cache group information when the bot is added to a group chat.</span></span>
* <span data-ttu-id="0c9f7-109">Atualizar informações armazenadas em cache sobre a associação de equipe ou informações do canal.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-109">Update cached information on team membership or channel information.</span></span>
* <span data-ttu-id="0c9f7-110">Remova informações armazenadas em cache para uma equipe se o bot for removido.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-110">Remove cached information for a team if the bot is removed.</span></span>
* <span data-ttu-id="0c9f7-111">Quando uma mensagem bot é curtida por um usuário.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-111">When a bot message is liked by a user.</span></span>

<span data-ttu-id="0c9f7-112">Cada evento bot é enviado como um objeto no qual `Activity` define quais informações estão no `messageType` objeto.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-112">Each bot event is sent as an `Activity` object in which `messageType` defines what information is in the object.</span></span> <span data-ttu-id="0c9f7-113">Para mensagens do tipo `message` , consulte Enviando e recebendo [mensagens](~/resources/bot-v3/bot-conversations/bots-conversations.md).</span><span class="sxs-lookup"><span data-stu-id="0c9f7-113">For messages of type `message`, see [Sending and receiving messages](~/resources/bot-v3/bot-conversations/bots-conversations.md).</span></span>

<span data-ttu-id="0c9f7-114">Teams e eventos de grupo, geralmente disparados do tipo, têm informações de evento de Teams adicionais passadas como parte do objeto e, portanto, o manipulador de eventos deve consultar a carga para os metadados específicos do evento Teams e `conversationUpdate` `channelData` `channelData` `eventType` adicionais.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-114">Teams and group events, usually triggered off the `conversationUpdate` type, have additional Teams event information passed as part of the `channelData` object, and therefore your event handler must query the `channelData` payload for the Teams `eventType` and additional event-specific metadata.</span></span>

<span data-ttu-id="0c9f7-115">A tabela a seguir lista os eventos em que o bot pode receber e tomar medidas.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-115">The following table lists the events that your bot can receive and take action on.</span></span>

|<span data-ttu-id="0c9f7-116">Tipo</span><span class="sxs-lookup"><span data-stu-id="0c9f7-116">Type</span></span>|<span data-ttu-id="0c9f7-117">Objeto Payload</span><span class="sxs-lookup"><span data-stu-id="0c9f7-117">Payload object</span></span>|<span data-ttu-id="0c9f7-118">Teams eventType</span><span class="sxs-lookup"><span data-stu-id="0c9f7-118">Teams eventType</span></span> |<span data-ttu-id="0c9f7-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="0c9f7-119">Description</span></span>|<span data-ttu-id="0c9f7-120">Escopo</span><span class="sxs-lookup"><span data-stu-id="0c9f7-120">Scope</span></span>|
|---|---|---|---|---|
| `conversationUpdate` |`membersAdded`| `teamMemberAdded`|[<span data-ttu-id="0c9f7-121">Membro adicionado à equipe</span><span class="sxs-lookup"><span data-stu-id="0c9f7-121">Member added to team</span></span>](#team-member-or-bot-addition)| <span data-ttu-id="0c9f7-122">all</span><span class="sxs-lookup"><span data-stu-id="0c9f7-122">all</span></span> |
| `conversationUpdate` |`membersRemoved`| `teamMemberRemoved`|[<span data-ttu-id="0c9f7-123">Membro foi removido da equipe</span><span class="sxs-lookup"><span data-stu-id="0c9f7-123">Member was removed from team</span></span>](#team-member-or-bot-removed)| `groupChat` & `team` |
| `conversationUpdate` | |`teamRenamed`| [<span data-ttu-id="0c9f7-124">A equipe foi renomeada</span><span class="sxs-lookup"><span data-stu-id="0c9f7-124">Team was renamed</span></span>](#team-name-updates)| `team` |
| `conversationUpdate` | |`channelCreated`| [<span data-ttu-id="0c9f7-125">Um canal foi criado</span><span class="sxs-lookup"><span data-stu-id="0c9f7-125">A channel was created</span></span>](#channel-updates)|`team` |
| `conversationUpdate` | |`channelRenamed`| [<span data-ttu-id="0c9f7-126">Um canal foi renomeado</span><span class="sxs-lookup"><span data-stu-id="0c9f7-126">A channel was renamed</span></span>](#channel-updates)|`team` |
| `conversationUpdate` | |`channelDeleted`| [<span data-ttu-id="0c9f7-127">Um canal foi excluído</span><span class="sxs-lookup"><span data-stu-id="0c9f7-127">A channel was deleted</span></span>](#channel-updates)|`team` |
| `messageReaction` |`reactionsAdded`|| [<span data-ttu-id="0c9f7-128">Reação à mensagem bot</span><span class="sxs-lookup"><span data-stu-id="0c9f7-128">Reaction to bot message</span></span>](#reactions)| <span data-ttu-id="0c9f7-129">all</span><span class="sxs-lookup"><span data-stu-id="0c9f7-129">all</span></span> |
| `messageReaction` |`reactionsRemoved`|| [<span data-ttu-id="0c9f7-130">Reação removida da mensagem bot</span><span class="sxs-lookup"><span data-stu-id="0c9f7-130">Reaction removed from bot message</span></span>](#reactions)| <span data-ttu-id="0c9f7-131">all</span><span class="sxs-lookup"><span data-stu-id="0c9f7-131">all</span></span> |

## <a name="team-member-or-bot-addition"></a><span data-ttu-id="0c9f7-132">Membro da equipe ou adição de bot</span><span class="sxs-lookup"><span data-stu-id="0c9f7-132">Team member or bot addition</span></span>

<span data-ttu-id="0c9f7-133">O evento é enviado ao bot quando ele recebe informações sobre atualizações de associação para equipes onde [`conversationUpdate`](/azure/bot-service/dotnet/bot-builder-dotnet-activities?view=azure-bot-service-3.0#conversationupdate&preserve-view=true) foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-133">The [`conversationUpdate`](/azure/bot-service/dotnet/bot-builder-dotnet-activities?view=azure-bot-service-3.0#conversationupdate&preserve-view=true) event is sent to your bot when it receives information on membership updates for teams where it has been added.</span></span> <span data-ttu-id="0c9f7-134">Ele também recebe uma atualização quando é adicionado pela primeira vez, especificamente para conversas pessoais.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-134">It also receives an update when it has been added for the first time specifically for personal conversations.</span></span> <span data-ttu-id="0c9f7-135">Observe que as informações do usuário ( ) são exclusivas para seu bot e podem ser armazenadas em cache para uso futuro pelo seu serviço, como o envio de uma mensagem `Id` para um usuário específico.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-135">Note that the user information (`Id`) is unique for your bot and can be cached for future use by your service, such as, sending a message to a specific user.</span></span>

### <a name="bot-or-user-added-to-a-team"></a><span data-ttu-id="0c9f7-136">Bot ou usuário adicionado a uma equipe</span><span class="sxs-lookup"><span data-stu-id="0c9f7-136">Bot or user added to a team</span></span>

<span data-ttu-id="0c9f7-137">O evento com o objeto na carga é enviado quando um bot é adicionado a uma equipe ou um novo usuário é adicionado a uma equipe em que um `conversationUpdate` `membersAdded` bot foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-137">The `conversationUpdate` event with the `membersAdded` object in the payload is sent when either a bot is added to a team or a new user is added to a team where a bot has been added.</span></span> <span data-ttu-id="0c9f7-138">Microsoft Teams também adiciona `eventType.teamMemberAdded` no `channelData` objeto.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-138">Microsoft Teams also adds `eventType.teamMemberAdded` in the `channelData` object.</span></span>

<span data-ttu-id="0c9f7-139">Como esse evento é enviado em ambos os casos, você deve analisar o objeto para determinar se a adição foi um usuário ou `membersAdded` o próprio bot.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-139">Because this event is sent in both cases, you should parse the `membersAdded` object to determine whether the addition was a user or the bot itself.</span></span> <span data-ttu-id="0c9f7-140">Para o último, uma prática [](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#best-practice-welcome-messages-in-teams) prática é enviar uma mensagem de boas-vindas ao canal para que os usuários possam entender os recursos que seu bot fornece.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-140">For the latter, a best practice is to send a [welcome message](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#best-practice-welcome-messages-in-teams) to the channel so users can understand the features your bot provides.</span></span>

#### <a name="example-code-checking-whether-bot-was-the-added-member"></a><span data-ttu-id="0c9f7-141">Código de exemplo: Verificando se bot foi o membro adicionado</span><span class="sxs-lookup"><span data-stu-id="0c9f7-141">Example code: Checking whether bot was the added member</span></span>

##### <a name="net"></a><span data-ttu-id="0c9f7-142">.NET</span><span class="sxs-lookup"><span data-stu-id="0c9f7-142">.NET</span></span>

```csharp
    for (int i = 0; i < sourceMessage.MembersAdded.Count; i++)
    {
        if (sourceMessage.MembersAdded[i].Id == sourceMessage.Recipient.Id)
        {
            addedBot = true;
            break;
        }
    }
```

##### <a name="nodejs"></a><span data-ttu-id="0c9f7-143">Node.js</span><span class="sxs-lookup"><span data-stu-id="0c9f7-143">Node.js</span></span>

```javascript
const builder = require('botbuilder');

var c = new builder.ChatConnector({appId: BOT_APP_ID, appPassword: .BOT_SECRET});
var bot = new builder.UniversalBot(c);

bot.on('conversationUpdate', (msg) => {
    var members = msg.membersAdded;
    // Loop through all members that were just added to the team
    for (var i = 0; i < members.length; i++) {

        // See if the member added was our bot
        if (members[i].id.includes(BOT_APP_ID)) {
            var botmessage = new builder.Message()
                .address(msg.address)
                .text('Hello World!');

            bot.send(botmessage, function(err) {});
        }
    }
});
```

#### <a name="schema-example-bot-added-to-team"></a><span data-ttu-id="0c9f7-144">Exemplo de esquema: Bot adicionado à equipe</span><span class="sxs-lookup"><span data-stu-id="0c9f7-144">Schema example: Bot added to team</span></span>

```json
{
   "membersAdded":[
      {
         "id":"28:f5d48856-5b42-41a0-8c3a-c5f944b679b0"
      }
   ],
   "type":"conversationUpdate",
   "timestamp":"2017-02-23T19:38:35.312Z",
   "localTimestamp":"2017-02-23T12:38:35.312-07:00",
   "id":"f:5f85c2ad",
   "channelId":"msteams",
   "serviceUrl":"https://smba.trafficmanager.net/amer-client-ss.msg/",
   "from":{
      "id":"29:1I9Is_Sx0OIy2rQ7Xz1lcaPKlO9eqmBRTBuW6XzkFtcjqxTjPaCMij8BVMdBcL9L_RwWNJyAHFQb0TRzXgyQvA"
   },
   "conversation":{
      "isGroup":true,
      "conversationType":"channel",
      "id":"19:efa9296d959346209fea44151c742e73@thread.skype"
   },
   "recipient":{
      "id":"28:f5d48856-5b42-41a0-8c3a-c5f944b679b0",
      "name":"SongsuggesterBot"
   },
   "channelData":{
      "team":{
         "id":"19:efa9296d959346209fea44151c742e73@thread.skype"
      },
      "eventType":"teamMemberAdded",
      "tenant":{
         "id":"72f988bf-86f1-41af-91ab-2d7cd011db47"
      }
   }
}
```

### <a name="user-added-to-a-meeting"></a><span data-ttu-id="0c9f7-145">User Added to a meeting</span><span class="sxs-lookup"><span data-stu-id="0c9f7-145">User Added to a meeting</span></span>

<span data-ttu-id="0c9f7-146">O `conversationUpdate` evento com o objeto na carga é enviado quando um usuário é adicionado a uma reunião `membersAdded` agendada privada.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-146">The `conversationUpdate` event with the `membersAdded` object in the payload is sent when a user is added to a private scheduled meeting.</span></span> <span data-ttu-id="0c9f7-147">Os detalhes do evento serão enviados mesmo quando usuários anônimos ingressarem na reunião.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-147">The event details will be sent even when anonymous users join the meeting.</span></span> 

> [!NOTE]
>
>* <span data-ttu-id="0c9f7-148">Quando um usuário anônimo é adicionado a uma reunião, o objeto de carga membersAdded não tem `aadObjectId` campo.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-148">When an anonymous user is added to a meeting, membersAdded payload object does not have `aadObjectId` field.</span></span>
>* <span data-ttu-id="0c9f7-149">Quando um usuário anônimo é adicionado a uma reunião, o objeto na carga sempre tem a id do organizador da reunião, mesmo que o usuário anônimo tenha sido adicionado por `from` outro apresentador.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-149">When an anonymous user is added to a meeting, `from` object in the payload always have the id of the meeting organizer, even if the anonymous user was added by another presenter.</span></span>

#### <a name="schema-example-user-added-to-meeting"></a><span data-ttu-id="0c9f7-150">Exemplo de esquema: usuário adicionado à reunião</span><span class="sxs-lookup"><span data-stu-id="0c9f7-150">Schema example: User added to meeting</span></span>

```json
{
   "membersAdded":[
      {
         "id":"229:1Z_XHWBMhDuehhDBYoPQD6Y1DSFsTtqOZx-SA5Jh9Y4zHKm4VbFGRn7-rK7SWiW1JECwxkMdrWpHoBut2sSyQPA"
      }
   ],
   "type":"conversationUpdate",
   "timestamp":"2017-02-23T19:38:35.312Z",
   "localTimestamp":"2020-09-29T21:11:38.6542339Z",
   "id":"f:a8cd1b51-9ddb-bd35-624b-7f7474165df8",
   "channelId":"msteams",
   "serviceUrl":"https://canary.botapi.skype.com/amer/",
   "from":{
      "id":"29:1siKxZhSoTapsXvI0gyf7Gywm_HM-4kEQW4BJnWuFYVIVu87xCNP99nidgQRCcwD3L3p_schiMShzx8IDRzf8mw",
      "aadObjectId":"f30ba569-abef-4e97-8762-35f85cbae706"
   },
   "conversation":{
      "isGroup":true,
      "tenantId":"e15762ef-a8d8-416b-871c-25516354f1fe",
      "id":"19:meeting_MWJlNGViOTgtMGExYi00NDA3LWExODgtOTZhMWNlYjM4ZTRj@thread.v2"
   },
   "recipient":{
      "id":"28:3af3604a-d4fc-486b-911e-86fab41aa91c",
      "name":"EchoBot1_Rename"
   },
   "channelData":{
      "tenant":{
         "id":"e15762ef-a8d8-416b-871c-25516354f1fe"
      },
      "source":null,
      "meeting":{
         "id":"MCMxOTptZWV0aW5nX01XSmxOR1ZpT1RndE1HRXhZaTAwTkRBM0xXRXhPRGd0T1RaaE1XTmxZak00WlRSakB0aHJlYWQudjIjMA=="
      }
   }
}

```

### <a name="bot-added-for-personal-context-only"></a><span data-ttu-id="0c9f7-151">Bot adicionado somente para contexto pessoal</span><span class="sxs-lookup"><span data-stu-id="0c9f7-151">Bot added for personal context only</span></span>

<span data-ttu-id="0c9f7-152">Seu bot recebe um `conversationUpdate` com quando um usuário o adiciona diretamente para chat `membersAdded` pessoal.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-152">Your bot receives a `conversationUpdate` with `membersAdded` when a user adds it directly for personal chat.</span></span> <span data-ttu-id="0c9f7-153">Nesse caso, a carga que seu bot recebe não contém o `channelData.team` objeto.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-153">In this case, the payload that your bot receives doesn't contain the `channelData.team` object.</span></span> <span data-ttu-id="0c9f7-154">Você deve usá-lo como um filtro caso queira que seu bot ofereça uma [mensagem](~/resources/bot-v3/bot-conversations/bots-conv-personal.md#best-practice-welcome-messages-in-personal-conversations) de boas-vindas diferente, dependendo do escopo.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-154">You should use this as a filter in case you want your bot to offer a different [welcome message](~/resources/bot-v3/bot-conversations/bots-conv-personal.md#best-practice-welcome-messages-in-personal-conversations) depending on scope.</span></span>

> [!NOTE]
> <span data-ttu-id="0c9f7-155">Para bots com escopo pessoal, o bot receberá o evento várias vezes, mesmo que o bot seja `conversationUpdate` removido e adicionado de forma reagressada.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-155">For personal scoped bots, your bot will  receive the `conversationUpdate` event multiple times, even if the bot is removed and re-added.</span></span> <span data-ttu-id="0c9f7-156">Para desenvolvimento e teste, você pode achar útil adicionar uma função auxiliar que permitirá redefinir completamente o bot.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-156">For development and testing you may find it useful to add a helper function that will allow you to reset your bot completely.</span></span> <span data-ttu-id="0c9f7-157">Consulte um [Node.js exemplo ou](https://github.com/OfficeDev/microsoft-teams-sample-complete-node/blob/master/src/middleware/SimulateResetBotChat.ts) C# [para](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp/blob/master/template-bot-master-csharp/src/controllers/MessagesController.cs#L238) obter mais detalhes sobre como implementá-lo.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-157">See a [Node.js example](https://github.com/OfficeDev/microsoft-teams-sample-complete-node/blob/master/src/middleware/SimulateResetBotChat.ts) or [C# example](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp/blob/master/template-bot-master-csharp/src/controllers/MessagesController.cs#L238) for more details on implementing this.</span></span>

#### <a name="schema-example-bot-added-to-personal-context"></a><span data-ttu-id="0c9f7-158">Exemplo de esquema: bot adicionado ao contexto pessoal</span><span class="sxs-lookup"><span data-stu-id="0c9f7-158">Schema example: bot added to personal context</span></span>

```json
{
  "membersAdded": [{
      "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0"
    },
    {
      "id": "29:<userID>",
      "aadObjectId": "***"
    }
  ],
  "type": "conversationUpdate",
  "timestamp": "2019-04-23T10:17:44.349Z",
  "id": "f:5f85c2ad",
  "channelId": "msteams",
  "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
  "from": {
    "id": "29:<USERID>",
    "aadObjectId": "***"
  },
  "conversation": {
    "conversationType": "personal",
    "id": "***"
  },
  "recipient": {
    "id": "28:<BOT ID>",
    "name": "<BOT NAME>"
  },
  "channelData": {
    "tenant": {
      "id": "<TENANT ID>"
    }
  }
}
```

## <a name="team-member-or-bot-removed"></a><span data-ttu-id="0c9f7-159">Membro da equipe ou bot removido</span><span class="sxs-lookup"><span data-stu-id="0c9f7-159">Team member or bot removed</span></span>

<span data-ttu-id="0c9f7-160">O evento com o objeto na carga é enviado quando seu bot é removido de uma equipe ou um usuário é removido de uma equipe em que um `conversationUpdate` `membersRemoved` bot foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-160">The `conversationUpdate` event with the `membersRemoved` object in the payload is sent when either your bot is removed from a team, or a user is removed from a team where a bot has been added.</span></span> <span data-ttu-id="0c9f7-161">Microsoft Teams também adiciona `eventType.teamMemberRemoved` no `channelData` objeto.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-161">Microsoft Teams also adds `eventType.teamMemberRemoved` in the `channelData` object.</span></span> <span data-ttu-id="0c9f7-162">Assim como no objeto, você deve analisar o objeto para a ID do aplicativo do `membersAdded` bot para determinar quem foi `membersRemoved` removido.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-162">As with the `membersAdded` object, you should parse the `membersRemoved` object for your bot's App ID to determine who was removed.</span></span>

### <a name="schema-example-team-member-removed"></a><span data-ttu-id="0c9f7-163">Exemplo de esquema: Membro da equipe removido</span><span class="sxs-lookup"><span data-stu-id="0c9f7-163">Schema example: Team member removed</span></span>

```json
{
    "membersRemoved": [
        {
            "id": "29:1_LCi5Up14pAy65yZuaJzG1uIT7ujYhjjSTsUNqjORsZHjLHKiQIBJa4cX2XsAsRoaY7va2w6ZymA9-1VtSY_g"
        }
    ],
    "type": "conversationUpdate",
    "timestamp": "2017-02-23T19:37:06.96Z",
    "localTimestamp": "2017-02-23T12:37:06.96-07:00",
    "id": "f:d8a6a4aa",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
    "from": {
        "id": "29:1I9Is_Sx0OIy2rQ7Xz1lcaPKlO9eqmBRTBuW6XzkFtcjqxTjPaCMij8BVMdBcL9L_RwWNJyAHFQb0TRzXgyQvA"
    },
    "conversation": {
        "isGroup": true,
        "conversationType": "channel",
        "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
    },
    "recipient":
    {
        "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0",
        "name": "SongsuggesterBot"
    },
    "channelData": {
        "team": {
            "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
        },
        "eventType": "teamMemberRemoved",
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```

### <a name="user-removed-from-a-meeting"></a><span data-ttu-id="0c9f7-164">Usuário removido de uma reunião</span><span class="sxs-lookup"><span data-stu-id="0c9f7-164">User removed from a meeting</span></span>

<span data-ttu-id="0c9f7-165">O evento com o objeto na carga é enviado quando um usuário `conversationUpdate` é removido de uma reunião `membersRemoved` agendada privada.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-165">The `conversationUpdate` event with the `membersRemoved` object in the payload is sent when a user is removed from a private scheduled meeting.</span></span> <span data-ttu-id="0c9f7-166">Os detalhes do evento serão enviados mesmo quando usuários anônimos ingressarem na reunião.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-166">The event details will be sent even when anonymous users join the meeting.</span></span> 

> [!NOTE]
>
>* <span data-ttu-id="0c9f7-167">Quando um usuário anônimo é removido de uma reunião, o objeto de carga MembersRemoved não tem `aadObjectId` campo.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-167">When an anonymous user is removed from a meeting, membersRemoved payload object does not have `aadObjectId` field.</span></span>
>* <span data-ttu-id="0c9f7-168">Quando um usuário anônimo é removido de uma reunião, o objeto na carga sempre tem a id do organizador da reunião, mesmo que o usuário anônimo tenha sido removido `from` por outro apresentador.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-168">When an anonymous user is removed from a meeting, `from` object in the payload always have the id of the meeting organizer, even if the anonymous user was removed by another presenter.</span></span>

#### <a name="schema-example-user-removed-from-meeting"></a><span data-ttu-id="0c9f7-169">Exemplo de esquema: usuário removido da reunião</span><span class="sxs-lookup"><span data-stu-id="0c9f7-169">Schema example: User removed from meeting</span></span>

```
{   
      "membersRemoved": 
        {  
          "id": "29:1Z_XHWBMhDuehhDBYoPQD6Y1DSFsTtqOZx-SA5Jh9Y4zHKm4VbFGRn7-rK7SWiW1JECwxkMdrWpHoBut2sSyQPA"   
        }   
      ],   
      "type": "conversationUpdate",   
      "timestamp": "2020-09-29T21:15:08.6391139Z",   
      "id": "f:ee8dfdf3-54ac-51de-05da-9d49514974bb",   
      "channelId": "msteams",   
      "serviceUrl": "https://canary.botapi.skype.com/amer/",   
      "from": {   
        "id": "29:1siKxZhSoTapsXvI0gyf7Gywm_HM-4kEQW4BJnWuFYVIVu87xCNP99nidgQRCcwD3L3p_schiMShzx8IDRzf8mw",   
        "aadObjectId": "f30ba569-abef-4e97-8762-35f85cbae706"   
      },   
      "conversation": {    
        "isGroup": true,   
        "tenantId": "e15762ef-a8d8-416b-871c-25516354f1fe",   
        "id": "19:meeting_MWJlNGViOTgtMGExYi00NDA3LWExODgtOTZhMWNlYjM4ZTRj@thread.v2"   
      },   
      "recipient": {   
        "id": "28:3af3604a-d4fc-486b-911e-86fab41aa91c",   
        "name": "EchoBot1_Rename"   
      },   
      "channelData": {   
        "tenant": {   
          "id": "e15762ef-a8d8-416b-871c-25516354f1fe"   
        },   
        "source": null,   
        "meeting": {   
          "id": "MCMxOTptZWV0aW5nX01XSmxOR1ZpT1RndE1HRXhZaTAwTkRBM0xXRXhPRGd0T1RaaE1XTmxZak00WlRSakB0aHJlYWQudjIjMA=="   
        }   
      }   
}
```

## <a name="team-name-updates"></a><span data-ttu-id="0c9f7-170">Atualizações de nome da equipe</span><span class="sxs-lookup"><span data-stu-id="0c9f7-170">Team name updates</span></span>

> [!NOTE]
> <span data-ttu-id="0c9f7-171">Não há nenhuma funcionalidade para consultar todos os nomes de equipe, e o nome da equipe não é retornado em cargas de outros eventos.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-171">There is no functionality to query all team names, and team name is not returned in payloads from other events.</span></span>

<span data-ttu-id="0c9f7-172">Seu bot é notificado quando a equipe em que está foi renomeada.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-172">Your bot is notified when the team it is in has been renamed.</span></span> <span data-ttu-id="0c9f7-173">Ele recebe um `conversationUpdate` evento `eventType.teamRenamed` com no `channelData` objeto.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-173">It receives a `conversationUpdate` event with `eventType.teamRenamed` in the `channelData` object.</span></span> <span data-ttu-id="0c9f7-174">Observe que não há notificações para criação ou exclusão de equipe, pois os bots existem apenas como parte das equipes e não têm visibilidade fora do escopo no qual foram adicionados.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-174">Please note that there are no notifications for team creation or deletion, because bots exist only as part of teams and have no visibility outside the scope in which they have been added.</span></span>

### <a name="schema-example-team-renamed"></a><span data-ttu-id="0c9f7-175">Exemplo de esquema: Equipe renomeada</span><span class="sxs-lookup"><span data-stu-id="0c9f7-175">Schema example: Team renamed</span></span>

```json
{ 
    "type": "conversationUpdate",
    "timestamp": "2017-02-23T19:35:56.825Z",
    "localTimestamp": "2017-02-23T12:35:56.825-07:00",
    "id": "f:1406033e",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/", 
    "from": { 
        "id": "29:1I9Is_Sx0O-Iy2rQ7Xz1lcaPKlO9eqmBRTBuW6XzkFtcjqxTjPaCMij8BVMdBcL9L_RwWNJyAHFQb0TRzXgyQvA"
    }, 
    "conversation": {
        "isGroup": true,
        "conversationType": "channel",
        "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
    },
    "recipient": { 
        "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0",
        "name": "SongsuggesterLocal"
    },
    "channelData": {
        "team": {
            "id": "19:efa9296d959346209fea44151c742e73@thread.skype",
            "name": "New Team Name"
        },
        "eventType": "teamRenamed",
        "tenant": { 
           "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```

## <a name="channel-updates"></a><span data-ttu-id="0c9f7-176">Atualizações de canal</span><span class="sxs-lookup"><span data-stu-id="0c9f7-176">Channel updates</span></span>

<span data-ttu-id="0c9f7-177">Seu bot é notificado quando um canal é criado, renomeado ou excluído em uma equipe em que foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-177">Your bot is notified when a channel is created, renamed, or deleted in a team where it has been added.</span></span> <span data-ttu-id="0c9f7-178">Novamente, o evento é recebido e um identificador de evento específico Teams é enviado como parte do objeto, onde os dados do canal são o GUID do canal e contém o próprio nome do `conversationUpdate` `channelData.eventType` `channel.id` `channel.name` canal.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-178">Again, the `conversationUpdate` event is received, and a Teams-specific event identifier is sent as part of the `channelData.eventType` object, where the channel data's  `channel.id` is the GUID for the channel, and `channel.name` contains the channel name itself.</span></span>

<span data-ttu-id="0c9f7-179">Os eventos do canal são os seguinte:</span><span class="sxs-lookup"><span data-stu-id="0c9f7-179">The channel events are as follows:</span></span>

* <span data-ttu-id="0c9f7-180">**channelCreated** &emsp; Um usuário adiciona um novo canal à equipe.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-180">**channelCreated**&emsp;A user adds a new channel to the team.</span></span>
* <span data-ttu-id="0c9f7-181">**channelRenamed** &emsp; Um usuário renomeia um canal existente.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-181">**channelRenamed**&emsp;A user renames an existing channel.</span></span>
* <span data-ttu-id="0c9f7-182">**channelDeleted** &emsp; Um usuário remove um canal.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-182">**channelDeleted**&emsp;A user removes a channel.</span></span>

### <a name="full-schema-example-channelcreated"></a><span data-ttu-id="0c9f7-183">Exemplo de esquema completo: channelCreated</span><span class="sxs-lookup"><span data-stu-id="0c9f7-183">Full schema example: channelCreated</span></span>

```json
{
    "type": "conversationUpdate",
    "timestamp": "2017-02-23T19:34:07.478Z",
    "localTimestamp": "2017-02-23T12:34:07.478-07:00",
    "id": "f:dd6ec311",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
    "from": {
        "id": "29:1wR7IdIRIoerMIWbewMi75JA3scaMuxvFon9eRQW2Nix5loMDo0362st2IaRVRirPZBv1WdXT8TIFWWmlQCizZQ"
    },
    "conversation": {
        "isGroup": true,
        "conversationType": "channel",
        "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
    },
    "recipient": {
        "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0",
        "name": "SongsuggesterBot"
    },
    "channelData": {
        "channel": {
            "id": "19:6d97d816470f481dbcda38244b98689a@thread.skype",
            "name": "FunDiscussions"
        },
        "team": {
            "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
        },
        "eventType": "channelCreated",
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```

### <a name="schema-excerpt-channeldata-for-channelrenamed"></a><span data-ttu-id="0c9f7-184">Trecho de esquema: channelData para channelRenamed</span><span class="sxs-lookup"><span data-stu-id="0c9f7-184">Schema excerpt: channelData for channelRenamed</span></span>

```json
⋮
"channelData": {
    "channel": {
        "id": "19:6d97d816470f481dbcda38244b98689a@thread.skype",
        "name": "PhotographyUpdates"
    },
    "team": {
        "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
    },
    "eventType": "channelRenamed",
    "tenant": {
        "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
    }
}
⋮
```

### <a name="schema-excerpt-channeldata-for-channeldeleted"></a><span data-ttu-id="0c9f7-185">Trecho de esquema: channelData para channelDeleted</span><span class="sxs-lookup"><span data-stu-id="0c9f7-185">Schema excerpt: channelData for channelDeleted</span></span>

```json
⋮
"channelData": {
    "channel": {
        "id": "19:6d97d816470f481dbcda38244b98689a@thread.skype",
        "name": "PhotographyUpdates"
    },
    "team": {
        "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
    },
    "eventType": "channelDeleted",
    "tenant": {
        "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
    }
}
⋮
```

## <a name="reactions"></a><span data-ttu-id="0c9f7-186">Reações</span><span class="sxs-lookup"><span data-stu-id="0c9f7-186">Reactions</span></span>

<span data-ttu-id="0c9f7-187">O evento é enviado quando um usuário adiciona ou remove sua reação a uma mensagem `messageReaction` que foi originalmente enviada pelo bot.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-187">The `messageReaction` event is sent when a user adds or removes his or her reaction to a message which was originally sent by your bot.</span></span> <span data-ttu-id="0c9f7-188">`replyToId` contém a ID da mensagem específica.</span><span class="sxs-lookup"><span data-stu-id="0c9f7-188">`replyToId` contains the ID of the specific message.</span></span>

### <a name="schema-example-a-user-likes-a-message"></a><span data-ttu-id="0c9f7-189">Exemplo de esquema: um usuário gosta de uma mensagem</span><span class="sxs-lookup"><span data-stu-id="0c9f7-189">Schema example: A user likes a message</span></span>

```json
{
    "reactionsAdded": [
        {
            "type": "like"
        }
    ],
    "type": "messageReaction",
    "timestamp": "2017-10-16T18:45:41.943Z",
    "id": "f:9f78d1f3",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
    "from": {
        "id": "29:1I9Is_Sx0O-Iy2rQ7Xz1lcaPKlO9eqmBRTBuW6XzkFtcjqxTjPaCMij8BVMdBcL9L_RwWNJyAHFQb0TRzXgyQvA",
        "aadObjectId": "c33aafc4-646d-4543-9d4c-abd28e4d2110"
    },
    "conversation": {
        "isGroup": true,
        "conversationType": "channel",
        "id": "19:3629591d4b774aa08cb0887902eee7c1@thread.skype"
    },
    "recipient": {
        "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0",
        "name": "SongsuggesterLocal"
    },
    "channelData": {
        "channel": {
            "id": "19:3629591d4b774aa08cb0887902eee7c1@thread.skype"
        },
        "team": {
            "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
        },
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    },
    "replyToId": "1575667808184"
}
```

### <a name="schema-example-a-user-un-likes-a-message"></a><span data-ttu-id="0c9f7-190">Exemplo de esquema: um usuário não gosta de uma mensagem</span><span class="sxs-lookup"><span data-stu-id="0c9f7-190">Schema example: A user un-likes a message</span></span>

```json
{
    "reactionsRemoved": [
        {
            "type": "like"
        }
    ],
    "type": "messageReaction",
    "timestamp": "2017-10-16T18:45:41.943Z",
    "id": "f:9f78d1f3",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
    "from": {
        "id": "29:1I9Is_Sx0O-Iy2rQ7Xz1lcaPKlO9eqmBRTBuW6XzkFtcjqxTjPaCMij8BVMdBcL9L_RwWNJyAHFQb0TRzXgyQvA",
        "aadObjectId": "c33aafc4-646d-4543-9d4c-abd28e4d2110"
    },
    "conversation": {
        "isGroup": true,
        "conversationType": "channel",
        "id": "19:3629591d4b774aa08cb0887902eee7c1@thread.skype"
    },
    "recipient": {
        "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0",
        "name": "SongsuggesterLocal"
    },
    "channelData": {
        "channel": {
            "id": "19:3629591d4b774aa08cb0887902eee7c1@thread.skype"
        },
        "team": {
            "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
        },
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    },
    "replyToId": "1575667808184"
}
```
