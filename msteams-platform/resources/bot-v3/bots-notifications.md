---
title: Lidar com eventos de bot
description: Descreve como lidar com eventos em bots para Microsoft Teams
keywords: equipes bots eventos
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
# <a name="handle-bot-events-in-microsoft-teams"></a><span data-ttu-id="196a8-104">Lidar com eventos de bot em Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="196a8-104">Handle bot events in Microsoft Teams</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="196a8-105">Microsoft Teams envia notificações ao seu bot para alterações ou eventos que acontecem em escopos onde seu bot está ativo.</span><span class="sxs-lookup"><span data-stu-id="196a8-105">Microsoft Teams sends notifications to your bot for changes or events that happen in scopes where your bot is active.</span></span> <span data-ttu-id="196a8-106">Você pode usar esses eventos para ativar a lógica de serviço, como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="196a8-106">You can use these events to trigger service logic, such as the following:</span></span>

* <span data-ttu-id="196a8-107">Acione uma mensagem de boas-vindas quando seu bot for adicionado a uma equipe.</span><span class="sxs-lookup"><span data-stu-id="196a8-107">Trigger a welcome message when your bot is added to a team.</span></span>
* <span data-ttu-id="196a8-108">Consultas e informações do grupo de cache quando o bot é adicionado a um bate-papo em grupo.</span><span class="sxs-lookup"><span data-stu-id="196a8-108">Query and cache group information when the bot is added to a group chat.</span></span>
* <span data-ttu-id="196a8-109">Atualize informações armazenadas em cache sobre a adesão da equipe ou informações do canal.</span><span class="sxs-lookup"><span data-stu-id="196a8-109">Update cached information on team membership or channel information.</span></span>
* <span data-ttu-id="196a8-110">Remova informações armazenadas em cache para uma equipe se o bot for removido.</span><span class="sxs-lookup"><span data-stu-id="196a8-110">Remove cached information for a team if the bot is removed.</span></span>
* <span data-ttu-id="196a8-111">Quando uma mensagem de bot é curtida por um usuário.</span><span class="sxs-lookup"><span data-stu-id="196a8-111">When a bot message is liked by a user.</span></span>

<span data-ttu-id="196a8-112">Cada evento de bot é enviado como um `Activity` objeto no qual define quais informações estão no `messageType` objeto.</span><span class="sxs-lookup"><span data-stu-id="196a8-112">Each bot event is sent as an `Activity` object in which `messageType` defines what information is in the object.</span></span> <span data-ttu-id="196a8-113">Para mensagens de `message` tipo, consulte [Enviar e receber mensagens](~/resources/bot-v3/bot-conversations/bots-conversations.md).</span><span class="sxs-lookup"><span data-stu-id="196a8-113">For messages of type `message`, see [Sending and receiving messages](~/resources/bot-v3/bot-conversations/bots-conversations.md).</span></span>

<span data-ttu-id="196a8-114">Teams e eventos em grupo, geralmente acionados fora do `conversationUpdate` tipo, têm informações adicionais de Teams evento passados como parte do `channelData` objeto e, portanto, o manipulador de eventos deve consultar a carga para os Teams `channelData` e `eventType` metadados adicionais específicos do evento.</span><span class="sxs-lookup"><span data-stu-id="196a8-114">Teams and group events, usually triggered off the `conversationUpdate` type, have additional Teams event information passed as part of the `channelData` object, and therefore your event handler must query the `channelData` payload for the Teams `eventType` and additional event-specific metadata.</span></span>

<span data-ttu-id="196a8-115">A tabela a seguir lista os eventos que seu bot pode receber e agir.</span><span class="sxs-lookup"><span data-stu-id="196a8-115">The following table lists the events that your bot can receive and take action on.</span></span>

|<span data-ttu-id="196a8-116">Tipo</span><span class="sxs-lookup"><span data-stu-id="196a8-116">Type</span></span>|<span data-ttu-id="196a8-117">Objeto de carga</span><span class="sxs-lookup"><span data-stu-id="196a8-117">Payload object</span></span>|<span data-ttu-id="196a8-118">evento Teams Type</span><span class="sxs-lookup"><span data-stu-id="196a8-118">Teams eventType</span></span> |<span data-ttu-id="196a8-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="196a8-119">Description</span></span>|<span data-ttu-id="196a8-120">Escopo</span><span class="sxs-lookup"><span data-stu-id="196a8-120">Scope</span></span>|
|---|---|---|---|---|
| `conversationUpdate` |`membersAdded`| `teamMemberAdded`|[<span data-ttu-id="196a8-121">Membro adicionado à equipe</span><span class="sxs-lookup"><span data-stu-id="196a8-121">Member added to team</span></span>](#team-member-or-bot-addition)| <span data-ttu-id="196a8-122">todo</span><span class="sxs-lookup"><span data-stu-id="196a8-122">all</span></span> |
| `conversationUpdate` |`membersRemoved`| `teamMemberRemoved`|[<span data-ttu-id="196a8-123">Membro foi removido da equipe</span><span class="sxs-lookup"><span data-stu-id="196a8-123">Member was removed from team</span></span>](#team-member-or-bot-removed)| `groupChat` & `team` |
| `conversationUpdate` | |`teamRenamed`| [<span data-ttu-id="196a8-124">Equipe foi renomeada</span><span class="sxs-lookup"><span data-stu-id="196a8-124">Team was renamed</span></span>](#team-name-updates)| `team` |
| `conversationUpdate` | |`channelCreated`| [<span data-ttu-id="196a8-125">Um canal foi criado</span><span class="sxs-lookup"><span data-stu-id="196a8-125">A channel was created</span></span>](#channel-updates)|`team` |
| `conversationUpdate` | |`channelRenamed`| [<span data-ttu-id="196a8-126">Um canal foi renomeado</span><span class="sxs-lookup"><span data-stu-id="196a8-126">A channel was renamed</span></span>](#channel-updates)|`team` |
| `conversationUpdate` | |`channelDeleted`| [<span data-ttu-id="196a8-127">Um canal foi excluído</span><span class="sxs-lookup"><span data-stu-id="196a8-127">A channel was deleted</span></span>](#channel-updates)|`team` |
| `messageReaction` |`reactionsAdded`|| [<span data-ttu-id="196a8-128">Reação à mensagem bot</span><span class="sxs-lookup"><span data-stu-id="196a8-128">Reaction to bot message</span></span>](#reactions)| <span data-ttu-id="196a8-129">todo</span><span class="sxs-lookup"><span data-stu-id="196a8-129">all</span></span> |
| `messageReaction` |`reactionsRemoved`|| [<span data-ttu-id="196a8-130">Reação removida da mensagem bot</span><span class="sxs-lookup"><span data-stu-id="196a8-130">Reaction removed from bot message</span></span>](#reactions)| <span data-ttu-id="196a8-131">todo</span><span class="sxs-lookup"><span data-stu-id="196a8-131">all</span></span> |

## <a name="team-member-or-bot-addition"></a><span data-ttu-id="196a8-132">Adição de membro da equipe ou bot</span><span class="sxs-lookup"><span data-stu-id="196a8-132">Team member or bot addition</span></span>

<span data-ttu-id="196a8-133">O [`conversationUpdate`](/azure/bot-service/dotnet/bot-builder-dotnet-activities?view=azure-bot-service-3.0#conversationupdate&preserve-view=true) evento é enviado ao seu bot quando recebe informações sobre atualizações de membros para equipes onde foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="196a8-133">The [`conversationUpdate`](/azure/bot-service/dotnet/bot-builder-dotnet-activities?view=azure-bot-service-3.0#conversationupdate&preserve-view=true) event is sent to your bot when it receives information on membership updates for teams where it has been added.</span></span> <span data-ttu-id="196a8-134">Ele também recebe uma atualização quando é adicionado pela primeira vez, especificamente para conversas pessoais.</span><span class="sxs-lookup"><span data-stu-id="196a8-134">It also receives an update when it has been added for the first time specifically for personal conversations.</span></span> <span data-ttu-id="196a8-135">Observe que as informações do usuário ( `Id` ) são únicas para o seu bot e podem ser armazenadas em cache para uso futuro pelo seu serviço, como, como, enviar uma mensagem para um usuário específico.</span><span class="sxs-lookup"><span data-stu-id="196a8-135">Note that the user information (`Id`) is unique for your bot and can be cached for future use by your service, such as, sending a message to a specific user.</span></span>

### <a name="bot-or-user-added-to-a-team"></a><span data-ttu-id="196a8-136">Bot ou usuário adicionado a uma equipe</span><span class="sxs-lookup"><span data-stu-id="196a8-136">Bot or user added to a team</span></span>

<span data-ttu-id="196a8-137">O `conversationUpdate` evento com o objeto na carga é enviado quando um bot é adicionado a uma equipe ou um `membersAdded` novo usuário é adicionado a uma equipe onde um bot foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="196a8-137">The `conversationUpdate` event with the `membersAdded` object in the payload is sent when either a bot is added to a team or a new user is added to a team where a bot has been added.</span></span> <span data-ttu-id="196a8-138">Microsoft Teams também adiciona `eventType.teamMemberAdded` no `channelData` objeto.</span><span class="sxs-lookup"><span data-stu-id="196a8-138">Microsoft Teams also adds `eventType.teamMemberAdded` in the `channelData` object.</span></span>

<span data-ttu-id="196a8-139">Como este evento é enviado em ambos os casos, você deve analisar o `membersAdded` objeto para determinar se a adição foi um usuário ou o próprio bot.</span><span class="sxs-lookup"><span data-stu-id="196a8-139">Because this event is sent in both cases, you should parse the `membersAdded` object to determine whether the addition was a user or the bot itself.</span></span> <span data-ttu-id="196a8-140">Para este último, uma prática recomendada é enviar uma [mensagem de boas-vindas](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#best-practice-welcome-messages-in-teams) ao canal para que os usuários possam entender os recursos que seu bot fornece.</span><span class="sxs-lookup"><span data-stu-id="196a8-140">For the latter, a best practice is to send a [welcome message](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#best-practice-welcome-messages-in-teams) to the channel so users can understand the features your bot provides.</span></span>

#### <a name="example-code-checking-whether-bot-was-the-added-member"></a><span data-ttu-id="196a8-141">Código de exemplo: Verificando se o bot era o membro adicionado</span><span class="sxs-lookup"><span data-stu-id="196a8-141">Example code: Checking whether bot was the added member</span></span>

##### <a name="net"></a><span data-ttu-id="196a8-142">.NET</span><span class="sxs-lookup"><span data-stu-id="196a8-142">.NET</span></span>

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

##### <a name="nodejs"></a><span data-ttu-id="196a8-143">Node.js</span><span class="sxs-lookup"><span data-stu-id="196a8-143">Node.js</span></span>

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

#### <a name="schema-example-bot-added-to-team"></a><span data-ttu-id="196a8-144">Exemplo de esquema: Bot adicionado à equipe</span><span class="sxs-lookup"><span data-stu-id="196a8-144">Schema example: Bot added to team</span></span>

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

### <a name="user-added-to-a-meeting"></a><span data-ttu-id="196a8-145">Usuário Adicionado a uma reunião</span><span class="sxs-lookup"><span data-stu-id="196a8-145">User Added to a meeting</span></span>

<span data-ttu-id="196a8-146">O `conversationUpdate` evento com o objeto na carga é enviado quando um usuário é adicionado a uma reunião agendada `membersAdded` privada.</span><span class="sxs-lookup"><span data-stu-id="196a8-146">The `conversationUpdate` event with the `membersAdded` object in the payload is sent when a user is added to a private scheduled meeting.</span></span> <span data-ttu-id="196a8-147">Os detalhes do evento serão enviados mesmo quando usuários anônimos participarem da reunião.</span><span class="sxs-lookup"><span data-stu-id="196a8-147">The event details will be sent even when anonymous users join the meeting.</span></span> 

> [!NOTE]
>
>* <span data-ttu-id="196a8-148">Quando um usuário anônimo é adicionado a uma reunião, o objeto de carga adicionado não tem `aadObjectId` campo.</span><span class="sxs-lookup"><span data-stu-id="196a8-148">When an anonymous user is added to a meeting, membersAdded payload object does not have `aadObjectId` field.</span></span>
>* <span data-ttu-id="196a8-149">Quando um usuário anônimo é adicionado a uma reunião, `from` o objeto na carga sempre tem a identificação do organizador do encontro, mesmo que o usuário anônimo tenha sido adicionado por outro apresentador.</span><span class="sxs-lookup"><span data-stu-id="196a8-149">When an anonymous user is added to a meeting, `from` object in the payload always have the id of the meeting organizer, even if the anonymous user was added by another presenter.</span></span>

#### <a name="schema-example-user-added-to-meeting"></a><span data-ttu-id="196a8-150">Exemplo de esquema: Usuário adicionado à reunião</span><span class="sxs-lookup"><span data-stu-id="196a8-150">Schema example: User added to meeting</span></span>

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

### <a name="bot-added-for-personal-context-only"></a><span data-ttu-id="196a8-151">Bot adicionado apenas para contexto pessoal</span><span class="sxs-lookup"><span data-stu-id="196a8-151">Bot added for personal context only</span></span>

<span data-ttu-id="196a8-152">Seu bot recebe um `conversationUpdate` com quando um usuário o adiciona `membersAdded` diretamente para bate-papo pessoal.</span><span class="sxs-lookup"><span data-stu-id="196a8-152">Your bot receives a `conversationUpdate` with `membersAdded` when a user adds it directly for personal chat.</span></span> <span data-ttu-id="196a8-153">Neste caso, a carga que o bot recebe não contém o `channelData.team` objeto.</span><span class="sxs-lookup"><span data-stu-id="196a8-153">In this case, the payload that your bot receives doesn't contain the `channelData.team` object.</span></span> <span data-ttu-id="196a8-154">Você deve usar isso como um filtro no caso de você querer que seu bot ofereça uma [mensagem de boas-vindas](~/resources/bot-v3/bot-conversations/bots-conv-personal.md#best-practice-welcome-messages-in-personal-conversations) diferente, dependendo do escopo.</span><span class="sxs-lookup"><span data-stu-id="196a8-154">You should use this as a filter in case you want your bot to offer a different [welcome message](~/resources/bot-v3/bot-conversations/bots-conv-personal.md#best-practice-welcome-messages-in-personal-conversations) depending on scope.</span></span>

> [!NOTE]
> <span data-ttu-id="196a8-155">Para bots com escopo pessoal, o bot receberá o `conversationUpdate` evento várias vezes, mesmo que o bot seja removido e reassume.</span><span class="sxs-lookup"><span data-stu-id="196a8-155">For personal scoped bots, your bot will  receive the `conversationUpdate` event multiple times, even if the bot is removed and re-added.</span></span> <span data-ttu-id="196a8-156">Para o desenvolvimento e testes, você pode achar útil adicionar uma função de ajudante que permitirá que você reinicie seu bot completamente.</span><span class="sxs-lookup"><span data-stu-id="196a8-156">For development and testing you may find it useful to add a helper function that will allow you to reset your bot completely.</span></span> <span data-ttu-id="196a8-157">Veja um [ exemploNode.js](https://github.com/OfficeDev/microsoft-teams-sample-complete-node/blob/master/src/middleware/SimulateResetBotChat.ts) ou [C#](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp/blob/master/template-bot-master-csharp/src/controllers/MessagesController.cs#L238) para obter mais detalhes sobre a implementação disso.</span><span class="sxs-lookup"><span data-stu-id="196a8-157">See a [Node.js example](https://github.com/OfficeDev/microsoft-teams-sample-complete-node/blob/master/src/middleware/SimulateResetBotChat.ts) or [C# example](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp/blob/master/template-bot-master-csharp/src/controllers/MessagesController.cs#L238) for more details on implementing this.</span></span>

#### <a name="schema-example-bot-added-to-personal-context"></a><span data-ttu-id="196a8-158">Exemplo de esquema: bot adicionado ao contexto pessoal</span><span class="sxs-lookup"><span data-stu-id="196a8-158">Schema example: bot added to personal context</span></span>

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

## <a name="team-member-or-bot-removed"></a><span data-ttu-id="196a8-159">Membro da equipe ou bot removido</span><span class="sxs-lookup"><span data-stu-id="196a8-159">Team member or bot removed</span></span>

<span data-ttu-id="196a8-160">O `conversationUpdate` evento com o objeto na carga é enviado quando seu bot é removido de uma equipe ou um `membersRemoved` usuário é removido de uma equipe onde um bot foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="196a8-160">The `conversationUpdate` event with the `membersRemoved` object in the payload is sent when either your bot is removed from a team, or a user is removed from a team where a bot has been added.</span></span> <span data-ttu-id="196a8-161">Microsoft Teams também adiciona `eventType.teamMemberRemoved` no `channelData` objeto.</span><span class="sxs-lookup"><span data-stu-id="196a8-161">Microsoft Teams also adds `eventType.teamMemberRemoved` in the `channelData` object.</span></span> <span data-ttu-id="196a8-162">Assim como no `membersAdded` objeto, você deve analisar o `membersRemoved` objeto do ID do aplicativo do seu bot para determinar quem foi removido.</span><span class="sxs-lookup"><span data-stu-id="196a8-162">As with the `membersAdded` object, you should parse the `membersRemoved` object for your bot's App ID to determine who was removed.</span></span>

### <a name="schema-example-team-member-removed"></a><span data-ttu-id="196a8-163">Exemplo de esquema: membro da equipe removido</span><span class="sxs-lookup"><span data-stu-id="196a8-163">Schema example: Team member removed</span></span>

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

### <a name="user-removed-from-a-meeting"></a><span data-ttu-id="196a8-164">Usuário removido de uma reunião</span><span class="sxs-lookup"><span data-stu-id="196a8-164">User removed from a meeting</span></span>

<span data-ttu-id="196a8-165">O `conversationUpdate` evento com o objeto na carga é enviado quando um usuário é removido de uma reunião agendada `membersRemoved` privada.</span><span class="sxs-lookup"><span data-stu-id="196a8-165">The `conversationUpdate` event with the `membersRemoved` object in the payload is sent when a user is removed from a private scheduled meeting.</span></span> <span data-ttu-id="196a8-166">Os detalhes do evento serão enviados mesmo quando usuários anônimos participarem da reunião.</span><span class="sxs-lookup"><span data-stu-id="196a8-166">The event details will be sent even when anonymous users join the meeting.</span></span> 

> [!NOTE]
>
>* <span data-ttu-id="196a8-167">Quando um usuário anônimo é removido de uma reunião, o objeto de carga de carga do MembersRemoved não tem `aadObjectId` campo.</span><span class="sxs-lookup"><span data-stu-id="196a8-167">When an anonymous user is removed from a meeting, membersRemoved payload object does not have `aadObjectId` field.</span></span>
>* <span data-ttu-id="196a8-168">Quando um usuário anônimo é removido de uma reunião, `from` o objeto na carga sempre tem a identificação do organizador do encontro, mesmo que o usuário anônimo tenha sido removido por outro apresentador.</span><span class="sxs-lookup"><span data-stu-id="196a8-168">When an anonymous user is removed from a meeting, `from` object in the payload always have the id of the meeting organizer, even if the anonymous user was removed by another presenter.</span></span>

#### <a name="schema-example-user-removed-from-meeting"></a><span data-ttu-id="196a8-169">Exemplo de esquema: Usuário removido da reunião</span><span class="sxs-lookup"><span data-stu-id="196a8-169">Schema example: User removed from meeting</span></span>

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

## <a name="team-name-updates"></a><span data-ttu-id="196a8-170">Atualizações de nomes de equipe</span><span class="sxs-lookup"><span data-stu-id="196a8-170">Team name updates</span></span>

> [!NOTE]
> <span data-ttu-id="196a8-171">Não há funcionalidade para consultar todos os nomes da equipe, e o nome da equipe não é retornado em cargas de outros eventos.</span><span class="sxs-lookup"><span data-stu-id="196a8-171">There is no functionality to query all team names, and team name is not returned in payloads from other events.</span></span>

<span data-ttu-id="196a8-172">Seu bot é notificado quando a equipe em que está foi renomeada.</span><span class="sxs-lookup"><span data-stu-id="196a8-172">Your bot is notified when the team it is in has been renamed.</span></span> <span data-ttu-id="196a8-173">Ele recebe um `conversationUpdate` evento com `eventType.teamRenamed` no `channelData` objeto.</span><span class="sxs-lookup"><span data-stu-id="196a8-173">It receives a `conversationUpdate` event with `eventType.teamRenamed` in the `channelData` object.</span></span> <span data-ttu-id="196a8-174">Por favor, note que não há notificações para criação ou exclusão de equipe, porque os bots existem apenas como parte das equipes e não têm visibilidade fora do escopo em que foram adicionados.</span><span class="sxs-lookup"><span data-stu-id="196a8-174">Please note that there are no notifications for team creation or deletion, because bots exist only as part of teams and have no visibility outside the scope in which they have been added.</span></span>

### <a name="schema-example-team-renamed"></a><span data-ttu-id="196a8-175">Exemplo de esquema: Equipe renomeada</span><span class="sxs-lookup"><span data-stu-id="196a8-175">Schema example: Team renamed</span></span>

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

## <a name="channel-updates"></a><span data-ttu-id="196a8-176">Atualizações do canal</span><span class="sxs-lookup"><span data-stu-id="196a8-176">Channel updates</span></span>

<span data-ttu-id="196a8-177">Seu bot é notificado quando um canal é criado, renomeado ou excluído em uma equipe onde foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="196a8-177">Your bot is notified when a channel is created, renamed, or deleted in a team where it has been added.</span></span> <span data-ttu-id="196a8-178">Novamente, o `conversationUpdate` evento é recebido, e um identificador de eventos específico Teams é enviado como parte do `channelData.eventType` objeto, onde os dados do canal são `channel.id` os GUID para o canal, e contém `channel.name` o próprio nome do canal.</span><span class="sxs-lookup"><span data-stu-id="196a8-178">Again, the `conversationUpdate` event is received, and a Teams-specific event identifier is sent as part of the `channelData.eventType` object, where the channel data's  `channel.id` is the GUID for the channel, and `channel.name` contains the channel name itself.</span></span>

<span data-ttu-id="196a8-179">Os eventos do canal são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="196a8-179">The channel events are as follows:</span></span>

* <span data-ttu-id="196a8-180">**canalCriado** &emsp; Um usuário adiciona um novo canal à equipe.</span><span class="sxs-lookup"><span data-stu-id="196a8-180">**channelCreated**&emsp;A user adds a new channel to the team.</span></span>
* <span data-ttu-id="196a8-181">**canalRenamed** &emsp; Um usuário renomeia um canal existente.</span><span class="sxs-lookup"><span data-stu-id="196a8-181">**channelRenamed**&emsp;A user renames an existing channel.</span></span>
* <span data-ttu-id="196a8-182">**canalDeclou** &emsp; Um usuário remove um canal.</span><span class="sxs-lookup"><span data-stu-id="196a8-182">**channelDeleted**&emsp;A user removes a channel.</span></span>

### <a name="full-schema-example-channelcreated"></a><span data-ttu-id="196a8-183">Exemplo completo de esquema: canalCriado</span><span class="sxs-lookup"><span data-stu-id="196a8-183">Full schema example: channelCreated</span></span>

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

### <a name="schema-excerpt-channeldata-for-channelrenamed"></a><span data-ttu-id="196a8-184">Trecho do esquema: channelData para channelRenamed</span><span class="sxs-lookup"><span data-stu-id="196a8-184">Schema excerpt: channelData for channelRenamed</span></span>

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

### <a name="schema-excerpt-channeldata-for-channeldeleted"></a><span data-ttu-id="196a8-185">Trecho do esquema: channelData para canalDeleted</span><span class="sxs-lookup"><span data-stu-id="196a8-185">Schema excerpt: channelData for channelDeleted</span></span>

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

## <a name="reactions"></a><span data-ttu-id="196a8-186">Reações</span><span class="sxs-lookup"><span data-stu-id="196a8-186">Reactions</span></span>

<span data-ttu-id="196a8-187">O `messageReaction` evento é enviado quando um usuário adiciona ou remove sua reação a uma mensagem que foi originalmente enviada pelo seu bot.</span><span class="sxs-lookup"><span data-stu-id="196a8-187">The `messageReaction` event is sent when a user adds or removes his or her reaction to a message which was originally sent by your bot.</span></span> <span data-ttu-id="196a8-188">`replyToId` contém o ID da mensagem específica.</span><span class="sxs-lookup"><span data-stu-id="196a8-188">`replyToId` contains the ID of the specific message.</span></span>

### <a name="schema-example-a-user-likes-a-message"></a><span data-ttu-id="196a8-189">Exemplo de esquema: um usuário gosta de uma mensagem</span><span class="sxs-lookup"><span data-stu-id="196a8-189">Schema example: A user likes a message</span></span>

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

### <a name="schema-example-a-user-un-likes-a-message"></a><span data-ttu-id="196a8-190">Exemplo de esquema: um usuário desapareçam de uma mensagem</span><span class="sxs-lookup"><span data-stu-id="196a8-190">Schema example: A user un-likes a message</span></span>

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
