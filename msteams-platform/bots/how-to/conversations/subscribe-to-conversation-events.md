---
title: Inscrever-se em eventos de conversa
author: WashingtonKayaker
description: Como inscrever-se em eventos de conversa do bot do Microsoft Teams.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: a8c6c39989a7d09a325412438f0d2ace78259cb7
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672850"
---
# <a name="subscribe-to-conversation-events"></a><span data-ttu-id="5d4dd-103">Inscrever-se em eventos de conversa</span><span class="sxs-lookup"><span data-stu-id="5d4dd-103">Subscribe to conversation events</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="5d4dd-104">O Microsoft Teams envia notificações ao bot para eventos que ocorrem em escopos onde seu bot está ativo.</span><span class="sxs-lookup"><span data-stu-id="5d4dd-104">Microsoft Teams sends notifications to your bot for events that happen in scopes where your bot is active.</span></span> <span data-ttu-id="5d4dd-105">Você pode capturar esses eventos no seu código e tomar ações sobre eles, como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5d4dd-105">You can capture these events in your code and take action on them, such as the following:</span></span>

* <span data-ttu-id="5d4dd-106">Acionar uma mensagem de boas-vindas quando seu bot é adicionado a uma equipe</span><span class="sxs-lookup"><span data-stu-id="5d4dd-106">Trigger a welcome message when your bot is added to a team</span></span>
* <span data-ttu-id="5d4dd-107">Acionar uma mensagem de boas-vindas quando um novo membro da equipe for adicionado ou removido</span><span class="sxs-lookup"><span data-stu-id="5d4dd-107">Trigger a welcome message when a new team member is added or removed</span></span>
* <span data-ttu-id="5d4dd-108">Acionar uma notificação quando um canal é criado, renomeado ou excluído</span><span class="sxs-lookup"><span data-stu-id="5d4dd-108">Trigger a notification when a channel is created, renamed or deleted</span></span>
* <span data-ttu-id="5d4dd-109">Quando uma mensagem de bot é curtida por um usuário</span><span class="sxs-lookup"><span data-stu-id="5d4dd-109">When a bot message is liked by a user</span></span>

## <a name="conversation-update-events"></a><span data-ttu-id="5d4dd-110">Eventos de atualização de conversa</span><span class="sxs-lookup"><span data-stu-id="5d4dd-110">Conversation update events</span></span>

<span data-ttu-id="5d4dd-111">Um bot recebe um `conversationUpdate` evento quando ele foi adicionado a uma conversa, outros membros foram adicionados ou removidos de uma conversa ou os metadados da conversa foram alterados.</span><span class="sxs-lookup"><span data-stu-id="5d4dd-111">A bot receives a `conversationUpdate` event when it has been added to a conversation, other members have been added to or removed from a conversation, or conversation metadata has changed.</span></span>

<span data-ttu-id="5d4dd-112">O `conversationUpdate` evento é enviado ao bot quando recebe informações sobre atualizações de associação para equipes em que foram adicionadas.</span><span class="sxs-lookup"><span data-stu-id="5d4dd-112">The `conversationUpdate` event is sent to your bot when it receives information on membership updates for teams where it has been added.</span></span> <span data-ttu-id="5d4dd-113">Ele também recebe uma atualização quando foi adicionado pela primeira vez especificamente para conversas pessoais.</span><span class="sxs-lookup"><span data-stu-id="5d4dd-113">It also receives an update when it has been added for the first time specifically for personal conversations.</span></span>

<span data-ttu-id="5d4dd-114">A tabela a seguir mostra uma lista de eventos de atualização de conversa do Teams, com links para mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="5d4dd-114">The following table shows a list of Teams conversation update events, with links to more details.</span></span>

| <span data-ttu-id="5d4dd-115">Ação tomada</span><span class="sxs-lookup"><span data-stu-id="5d4dd-115">Action Taken</span></span>        | <span data-ttu-id="5d4dd-116">EventType</span><span class="sxs-lookup"><span data-stu-id="5d4dd-116">EventType</span></span>         | <span data-ttu-id="5d4dd-117">Método chamado</span><span class="sxs-lookup"><span data-stu-id="5d4dd-117">Method Called</span></span>              | <span data-ttu-id="5d4dd-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d4dd-118">Description</span></span>                | <span data-ttu-id="5d4dd-119">Escopo</span><span class="sxs-lookup"><span data-stu-id="5d4dd-119">Scope</span></span> |
| ------------------- | ----------------- | -------------------------- | -------------------------- | ----- |
| <span data-ttu-id="5d4dd-120">canal criado</span><span class="sxs-lookup"><span data-stu-id="5d4dd-120">channel created</span></span>     | <span data-ttu-id="5d4dd-121">channelCreated</span><span class="sxs-lookup"><span data-stu-id="5d4dd-121">channelCreated</span></span>    | <span data-ttu-id="5d4dd-122">OnTeamsChannelCreatedAsync</span><span class="sxs-lookup"><span data-stu-id="5d4dd-122">OnTeamsChannelCreatedAsync</span></span> | [<span data-ttu-id="5d4dd-123">Um canal foi criado</span><span class="sxs-lookup"><span data-stu-id="5d4dd-123">A channel was created</span></span>](#channel-created) | <span data-ttu-id="5d4dd-124">Equipe</span><span class="sxs-lookup"><span data-stu-id="5d4dd-124">Team</span></span> |
| <span data-ttu-id="5d4dd-125">canal renomeado</span><span class="sxs-lookup"><span data-stu-id="5d4dd-125">channel renamed</span></span>     | <span data-ttu-id="5d4dd-126">channelRenamed</span><span class="sxs-lookup"><span data-stu-id="5d4dd-126">channelRenamed</span></span>    | <span data-ttu-id="5d4dd-127">OnTeamsChannelRenamedAsync</span><span class="sxs-lookup"><span data-stu-id="5d4dd-127">OnTeamsChannelRenamedAsync</span></span> | [<span data-ttu-id="5d4dd-128">Um canal foi renomeado</span><span class="sxs-lookup"><span data-stu-id="5d4dd-128">A channel was renamed</span></span>](#channel-renamed) | <span data-ttu-id="5d4dd-129">Equipe</span><span class="sxs-lookup"><span data-stu-id="5d4dd-129">Team</span></span> |
| <span data-ttu-id="5d4dd-130">canal excluído</span><span class="sxs-lookup"><span data-stu-id="5d4dd-130">channel deleted</span></span>     | <span data-ttu-id="5d4dd-131">channelDeleted</span><span class="sxs-lookup"><span data-stu-id="5d4dd-131">channelDeleted</span></span>    | <span data-ttu-id="5d4dd-132">OnTeamsChannelDeletedAsync</span><span class="sxs-lookup"><span data-stu-id="5d4dd-132">OnTeamsChannelDeletedAsync</span></span> | [<span data-ttu-id="5d4dd-133">Um canal foi excluído</span><span class="sxs-lookup"><span data-stu-id="5d4dd-133">A channel was deleted</span></span>](#channel-deleted) | <span data-ttu-id="5d4dd-134">Equipe</span><span class="sxs-lookup"><span data-stu-id="5d4dd-134">Team</span></span> |
| <span data-ttu-id="5d4dd-135">Membros da equipe adicionados</span><span class="sxs-lookup"><span data-stu-id="5d4dd-135">team members added</span></span>   | <span data-ttu-id="5d4dd-136">teamMemberAdded</span><span class="sxs-lookup"><span data-stu-id="5d4dd-136">teamMemberAdded</span></span>   | <span data-ttu-id="5d4dd-137">OnTeamsMembersAddedAsync</span><span class="sxs-lookup"><span data-stu-id="5d4dd-137">OnTeamsMembersAddedAsync</span></span>   | [<span data-ttu-id="5d4dd-138">Um membro adicionado ao Team</span><span class="sxs-lookup"><span data-stu-id="5d4dd-138">A Member added to team</span></span>](#team-members-added)   | <span data-ttu-id="5d4dd-139">Todos</span><span class="sxs-lookup"><span data-stu-id="5d4dd-139">All</span></span> |
| <span data-ttu-id="5d4dd-140">Membros da equipe removidos</span><span class="sxs-lookup"><span data-stu-id="5d4dd-140">team members removed</span></span> | <span data-ttu-id="5d4dd-141">teamMemberRemoved</span><span class="sxs-lookup"><span data-stu-id="5d4dd-141">teamMemberRemoved</span></span> | <span data-ttu-id="5d4dd-142">OnTeamsMembersRemovedAsync</span><span class="sxs-lookup"><span data-stu-id="5d4dd-142">OnTeamsMembersRemovedAsync</span></span> | [<span data-ttu-id="5d4dd-143">Um membro foi removido da equipe</span><span class="sxs-lookup"><span data-stu-id="5d4dd-143">A Member was removed from team</span></span>](#team-members-removed) | <span data-ttu-id="5d4dd-144">groupChat & equipe</span><span class="sxs-lookup"><span data-stu-id="5d4dd-144">groupChat & team</span></span> |
| <span data-ttu-id="5d4dd-145">equipe renomeada</span><span class="sxs-lookup"><span data-stu-id="5d4dd-145">team renamed</span></span>        | <span data-ttu-id="5d4dd-146">teamRenamed</span><span class="sxs-lookup"><span data-stu-id="5d4dd-146">teamRenamed</span></span>       | <span data-ttu-id="5d4dd-147">OnTeamsTeamRenamedAsync</span><span class="sxs-lookup"><span data-stu-id="5d4dd-147">OnTeamsTeamRenamedAsync</span></span>    | [<span data-ttu-id="5d4dd-148">Uma equipe foi renomeada</span><span class="sxs-lookup"><span data-stu-id="5d4dd-148">A Team was renamed</span></span>](#team-renamed)       | <span data-ttu-id="5d4dd-149">Equipe</span><span class="sxs-lookup"><span data-stu-id="5d4dd-149">Team</span></span> |

### <a name="channel-created"></a><span data-ttu-id="5d4dd-150">Canal criado</span><span class="sxs-lookup"><span data-stu-id="5d4dd-150">Channel created</span></span>

<span data-ttu-id="5d4dd-151">O evento criado pelo canal é enviado ao seu bot sempre que um novo canal é criado em uma equipe na qual seu bot está instalado.</span><span class="sxs-lookup"><span data-stu-id="5d4dd-151">The channel created event is sent to your bot whenever a new channel is created in a team your bot is installed in.</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="5d4dd-152">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="5d4dd-152">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelCreatedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the Channel created");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejstabtypescript"></a>[<span data-ttu-id="5d4dd-153">TypeScript/node. js</span><span class="sxs-lookup"><span data-stu-id="5d4dd-153">TypeScript/Node.js</span></span>](#tab/typescript)

<!-- From sample: botbuilder-js\libraries\botbuilder\tests\teams\conversationUpdate\src\conversationUpdateBot.ts -->

```typescript

export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsChannelCreatedEvent(async (channelInfo: ChannelInfo, teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
            const card = CardFactory.heroCard('Channel Created', `${channelInfo.name} is the Channel created`);
            const message = MessageFactory.attachment(card);
            await turnContext.sendActivity(message);
            await next();
        });
    }
}

```

# <a name="jsontabjson"></a>[<span data-ttu-id="5d4dd-154">JSON</span><span class="sxs-lookup"><span data-stu-id="5d4dd-154">JSON</span></span>](#tab/json)

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

# <a name="pythontabpython"></a>[<span data-ttu-id="5d4dd-155">Python</span><span class="sxs-lookup"><span data-stu-id="5d4dd-155">Python</span></span>](#tab/python)

```python
async def on_teams_channel_created_activity(
    self, channel_info: ChannelInfo, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(
            f"The new channel is {channel_info.name}. The channel id is {channel_info.id}"
        )
    )
```

* * *

### <a name="channel-renamed"></a><span data-ttu-id="5d4dd-156">Canal renomeado</span><span class="sxs-lookup"><span data-stu-id="5d4dd-156">Channel renamed</span></span>

<span data-ttu-id="5d4dd-157">O evento renomeado de canal é enviado ao seu bot sempre que um canal é renomeado em uma equipe na qual seu bot está instalado.</span><span class="sxs-lookup"><span data-stu-id="5d4dd-157">The channel renamed event is sent to your bot whenever a channel is renamed in a team your bot is installed in.</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="5d4dd-158">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="5d4dd-158">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelRenamedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the new Channel name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejstabtypescript"></a>[<span data-ttu-id="5d4dd-159">TypeScript/node. js</span><span class="sxs-lookup"><span data-stu-id="5d4dd-159">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsChannelRenamedEvent(async (channelInfo: ChannelInfo, teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
            const card = CardFactory.heroCard('Channel Renamed', `${channelInfo.name} is the new Channel name`);
            const message = MessageFactory.attachment(card);
            await turnContext.sendActivity(message);
            await next();
        });
    }
```

# <a name="jsontabjson"></a>[<span data-ttu-id="5d4dd-160">JSON</span><span class="sxs-lookup"><span data-stu-id="5d4dd-160">JSON</span></span>](#tab/json)

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
}
```

# <a name="pythontabpython"></a>[<span data-ttu-id="5d4dd-161">Python</span><span class="sxs-lookup"><span data-stu-id="5d4dd-161">Python</span></span>](#tab/python)

```python
async def on_teams_channel_renamed_activity(
    self, channel_info: ChannelInfo, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The new channel name is {channel_info.name}")
    )
```

* * *

### <a name="channel-deleted"></a><span data-ttu-id="5d4dd-162">Canal excluído</span><span class="sxs-lookup"><span data-stu-id="5d4dd-162">Channel Deleted</span></span>

<span data-ttu-id="5d4dd-163">O evento Deleted do canal é enviado ao seu bot sempre que um canal é excluído em uma equipe em que seu bot está instalado.</span><span class="sxs-lookup"><span data-stu-id="5d4dd-163">The channel deleted event is sent to your bot whenever a channel is deleted in a team your bot is installed in.</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="5d4dd-164">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="5d4dd-164">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelDeletedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the Channel deleted");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejstabtypescript"></a>[<span data-ttu-id="5d4dd-165">TypeScript/node. js</span><span class="sxs-lookup"><span data-stu-id="5d4dd-165">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsChannelDeletedEvent(async (channelInfo: ChannelInfo, teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
            const card = CardFactory.heroCard('Channel Deleted', `${channelInfo.name} is the Channel deleted`);
            const message = MessageFactory.attachment(card);
            await turnContext.sendActivity(message);
            await next();
        });
    }
}

```

# <a name="jsontabjson"></a>[<span data-ttu-id="5d4dd-166">JSON</span><span class="sxs-lookup"><span data-stu-id="5d4dd-166">JSON</span></span>](#tab/json)

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
}
```

# <a name="pythontabpython"></a>[<span data-ttu-id="5d4dd-167">Python</span><span class="sxs-lookup"><span data-stu-id="5d4dd-167">Python</span></span>](#tab/python)

```python
async def on_teams_channel_deleted_activity(
    self, channel_info: ChannelInfo, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The deleted channel is {channel_info.name}")
    )
```

* * *

### <a name="team-members-added"></a><span data-ttu-id="5d4dd-168">Membros da equipe adicionados</span><span class="sxs-lookup"><span data-stu-id="5d4dd-168">Team members added</span></span>

<span data-ttu-id="5d4dd-169">O `teamMemberAdded` evento é enviado ao bot pela primeira vez que é adicionado a uma conversa e toda vez que um novo usuário é adicionado a uma equipe ou bate-papo de grupo no qual o bot está instalado.</span><span class="sxs-lookup"><span data-stu-id="5d4dd-169">The `teamMemberAdded` event is sent to your bot the first time it is added to a conversation and every time a new user is added to a team or group chat that your bot is installed in.</span></span> <span data-ttu-id="5d4dd-170">As informações do usuário (ID) são exclusivas para o bot e podem ser armazenadas em cache para uso futuro pelo serviço (como enviar uma mensagem para um usuário específico).</span><span class="sxs-lookup"><span data-stu-id="5d4dd-170">The user information (ID) is unique for your bot and can be cached for future use by your service (such as sending a message to a specific user).</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="5d4dd-171">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="5d4dd-171">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsMembersAddedAsync(IList<ChannelAccount> membersAdded, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    foreach (TeamsChannelAccount member in membersAdded)
    {
        if (member.Id == turnContext.Activity.Recipient.Id)
        {
            // Send a message to introduce the bot to the team
            var heroCard = new HeroCard(text: $"The {member.Name} bot has joined {teamInfo.Name}");
            await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
        }
        else
        {
            var heroCard = new HeroCard(text: $"{member.Name} joined {teamInfo.Name}");
            await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
        }
    }
}
```

# <a name="typescriptnodejstabtypescript"></a>[<span data-ttu-id="5d4dd-172">TypeScript/node. js</span><span class="sxs-lookup"><span data-stu-id="5d4dd-172">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsMembersAddedEvent(async (membersAdded: ChannelAccount[], teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
                let newMembers: string = '';
                console.log(JSON.stringify(membersAdded));
                membersAdded.forEach((account) => {
                    newMembers += account.id + ' ';
                });
                const name = !teamInfo ? 'not in team' : teamInfo.name;
                const card = CardFactory.heroCard('Account Added', `${newMembers} joined ${name}.`);
                const message = MessageFactory.attachment(card);
                await turnContext.sendActivity(message);
                await next();
        });
    }
}

```

# <a name="jsontabjson"></a>[<span data-ttu-id="5d4dd-173">JSON</span><span class="sxs-lookup"><span data-stu-id="5d4dd-173">JSON</span></span>](#tab/json)

<span data-ttu-id="5d4dd-174">Esta é a mensagem que seu bot receberá quando o bot for adicionado **a uma equipe**.</span><span class="sxs-lookup"><span data-stu-id="5d4dd-174">This is the message your bot will receive when the bot is added **to a team**.</span></span>

```json
{
    "membersAdded": [
        {
            "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0"
        }
    ],
    "type": "conversationUpdate",
    "timestamp": "2017-02-23T19:38:35.312Z",
    "localTimestamp": "2017-02-23T12:38:35.312-07:00",
    "id": "f:5f85c2ad",
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
    "recipient": {
        "id": "28:f5d48856-5b42-41a0-8c3a-c5f944b679b0",
        "name": "SongsuggesterBot"
    },
    "channelData": {
        "team": {
            "id": "19:efa9296d959346209fea44151c742e73@thread.skype"
        },
        "eventType": "teamMemberAdded",
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```

<span data-ttu-id="5d4dd-175">Esta é a mensagem que seu bot receberá quando o bot for adicionado*a um chat de um-para-um*.</span><span class="sxs-lookup"><span data-stu-id="5d4dd-175">This is the message your bot will receive when the bot is added \**to a one-to-one chat*.</span></span>

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

# <a name="pythontabpython"></a>[<span data-ttu-id="5d4dd-176">Python</span><span class="sxs-lookup"><span data-stu-id="5d4dd-176">Python</span></span>](#tab/python)

```python
async def on_teams_members_added_activity(
    self, teams_members_added: [TeamsChannelAccount], turn_context: TurnContext
):
    for member in teams_members_added:
        await turn_context.send_activity(
            MessageFactory.text(f"Welcome your new team member {member.id}")
        )
    return
```

* * *

### <a name="team-members-removed"></a><span data-ttu-id="5d4dd-177">Membros da equipe removidos</span><span class="sxs-lookup"><span data-stu-id="5d4dd-177">Team members removed</span></span>

<span data-ttu-id="5d4dd-178">O `teamMemberRemoved` evento é enviado ao bot se ele for removido de uma equipe e sempre que qualquer usuário for removido de uma equipe que o seu bot é membro.</span><span class="sxs-lookup"><span data-stu-id="5d4dd-178">The `teamMemberRemoved` event is sent to your bot if it is removed from a team and every time any user is removed from a team that your bot is a member of.</span></span> <span data-ttu-id="5d4dd-179">Você pode determinar se o novo membro removido era o próprio bot ou um usuário examinando o `Activity` objeto do. `turnContext`</span><span class="sxs-lookup"><span data-stu-id="5d4dd-179">You can determine if the new member removed was the bot itself or a user by looking at the `Activity` object of the `turnContext`.</span></span>  <span data-ttu-id="5d4dd-180">Se o `Id` campo do `MembersRemoved` objeto for igual ao `Id` campo do `Recipient` objeto, o membro removido será o bot, caso contrário, será um usuário.</span><span class="sxs-lookup"><span data-stu-id="5d4dd-180">If the `Id` field of the `MembersRemoved` object is the same as the `Id` field of the `Recipient` object, then the member removed is the bot, otherwise it is a user.</span></span>  <span data-ttu-id="5d4dd-181">O bot geralmente `Id` será:`28:<MicrosoftAppId>`</span><span class="sxs-lookup"><span data-stu-id="5d4dd-181">The bot's `Id` will generally be: `28:<MicrosoftAppId>`</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="5d4dd-182">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="5d4dd-182">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsMembersRemovedAsync(IList<ChannelAccount> membersRemoved, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    foreach (TeamsChannelAccount member in membersRemoved)
    {
        if (member.Id == turnContext.Activity.Recipient.Id)
        {
            // The bot was removed
            // You should clear any cached data you have for this team
        }
        else
        {
            var heroCard = new HeroCard(text: $"{member.Name} was removed from {teamInfo.Name}");
            await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
        }
    }
}
```

# <a name="typescriptnodejstabtypescript"></a>[<span data-ttu-id="5d4dd-183">TypeScript/node. js</span><span class="sxs-lookup"><span data-stu-id="5d4dd-183">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript

export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsMembersRemovedEvent(async (membersRemoved: ChannelAccount[], teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
            let removedMembers: string = '';
            console.log(JSON.stringify(membersRemoved));
            membersRemoved.forEach((account) => {
                removedMembers += account.id + ' ';
            });
            const name = !teamInfo ? 'not in team' : teamInfo.name;
            const card = CardFactory.heroCard('Account Removed', `${removedMembers} removed from ${teamInfo.name}.`);
            const message = MessageFactory.attachment(card);
            await turnContext.sendActivity(message);
            await next();
        });
    }
}

```

# <a name="jsontabjson"></a>[<span data-ttu-id="5d4dd-184">JSON</span><span class="sxs-lookup"><span data-stu-id="5d4dd-184">JSON</span></span>](#tab/json)

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


# <a name="pythontabpython"></a>[<span data-ttu-id="5d4dd-185">Python</span><span class="sxs-lookup"><span data-stu-id="5d4dd-185">Python</span></span>](#tab/python)

```python
async def on_teams_members_removed_activity(
    self, teams_members_removed: [TeamsChannelAccount], turn_context: TurnContext
):
    for member in teams_members_removed:
        await turn_context.send_activity(
            MessageFactory.text(f"Say goodbye to your team member {member.id}")
        )
    return
```

* * *

### <a name="team-renamed"></a><span data-ttu-id="5d4dd-186">Equipe renomeada</span><span class="sxs-lookup"><span data-stu-id="5d4dd-186">Team renamed</span></span>

<span data-ttu-id="5d4dd-187">O bot é notificado quando a equipe que está sendo renomeada.</span><span class="sxs-lookup"><span data-stu-id="5d4dd-187">Your bot is notified when the team it is in has been renamed.</span></span> <span data-ttu-id="5d4dd-188">Ele recebe um `conversationUpdate` evento com `eventType.teamRenamed` no `channelData` objeto.</span><span class="sxs-lookup"><span data-stu-id="5d4dd-188">It receives a `conversationUpdate` event with `eventType.teamRenamed` in the `channelData` object.</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="5d4dd-189">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="5d4dd-189">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamRenamedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the new Team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejstabtypescript"></a>[<span data-ttu-id="5d4dd-190">TypeScript/node. js</span><span class="sxs-lookup"><span data-stu-id="5d4dd-190">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsTeamRenamedEvent(async (teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
            const card = CardFactory.heroCard('Team Renamed', `${teamInfo.name} is the new Team name`);
            const message = MessageFactory.attachment(card);
            await turnContext.sendActivity(message);
            await next();
        });
    }
}
```

# <a name="jsontabjson"></a>[<span data-ttu-id="5d4dd-191">JSON</span><span class="sxs-lookup"><span data-stu-id="5d4dd-191">JSON</span></span>](#tab/json)

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


# <a name="pythontabpython"></a>[<span data-ttu-id="5d4dd-192">Python</span><span class="sxs-lookup"><span data-stu-id="5d4dd-192">Python</span></span>](#tab/python)

```python
async def on_teams_team_renamed_activity(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The new team name is {team_info.name}")
    )
```

* * *

## <a name="message-reaction-events"></a><span data-ttu-id="5d4dd-193">Eventos de reação de mensagens</span><span class="sxs-lookup"><span data-stu-id="5d4dd-193">Message reaction events</span></span>

<span data-ttu-id="5d4dd-194">O `messageReaction` evento é enviado quando um usuário adiciona ou remove reações a uma mensagem que foi enviada pelo bot.</span><span class="sxs-lookup"><span data-stu-id="5d4dd-194">The `messageReaction` event is sent when a user adds or removes reactions to a message which was sent by your bot.</span></span> <span data-ttu-id="5d4dd-195">O `replyToId` contém a ID da mensagem específica e o `Type` é o tipo de reação no formato de texto.</span><span class="sxs-lookup"><span data-stu-id="5d4dd-195">The `replyToId` contains the ID of the specific message, and the `Type` is the type of reaction in text format.</span></span>  <span data-ttu-id="5d4dd-196">Os tipos de reações incluem: "irritado", "coração", "Laugh", "Like", "Sad", "surpreso".</span><span class="sxs-lookup"><span data-stu-id="5d4dd-196">The types of reactions include: "angry", "heart", "laugh", "like", "Sad", "surprised".</span></span> <span data-ttu-id="5d4dd-197">Esse evento não contém o conteúdo da mensagem original, portanto, se o processamento de reações às suas mensagens for importante para o seu bot, você precisará armazenar as mensagens ao enviá-las.</span><span class="sxs-lookup"><span data-stu-id="5d4dd-197">This event does not contain the contents of the original message, so if processing reactions to your messages is important for your bot you'll need to store the messages when you send them.</span></span>

| <span data-ttu-id="5d4dd-198">EventType</span><span class="sxs-lookup"><span data-stu-id="5d4dd-198">EventType</span></span>       | <span data-ttu-id="5d4dd-199">Objeto Payload</span><span class="sxs-lookup"><span data-stu-id="5d4dd-199">Payload object</span></span>   | <span data-ttu-id="5d4dd-200">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d4dd-200">Description</span></span>                                                             | <span data-ttu-id="5d4dd-201">Escopo</span><span class="sxs-lookup"><span data-stu-id="5d4dd-201">Scope</span></span> |
| --------------- | ---------------- | ----------------------------------------------------------------------- | ----- |
| <span data-ttu-id="5d4dd-202">messageReaction</span><span class="sxs-lookup"><span data-stu-id="5d4dd-202">messageReaction</span></span> | <span data-ttu-id="5d4dd-203">reactionsAdded</span><span class="sxs-lookup"><span data-stu-id="5d4dd-203">reactionsAdded</span></span>   | [<span data-ttu-id="5d4dd-204">Reação à mensagem de bot</span><span class="sxs-lookup"><span data-stu-id="5d4dd-204">Reaction to bot message</span></span>](#reactions-to-a-bot-message)                   | <span data-ttu-id="5d4dd-205">Todos</span><span class="sxs-lookup"><span data-stu-id="5d4dd-205">All</span></span>   |
| <span data-ttu-id="5d4dd-206">messageReaction</span><span class="sxs-lookup"><span data-stu-id="5d4dd-206">messageReaction</span></span> | <span data-ttu-id="5d4dd-207">reactionsRemoved</span><span class="sxs-lookup"><span data-stu-id="5d4dd-207">reactionsRemoved</span></span> | [<span data-ttu-id="5d4dd-208">Reação removida da mensagem de bot</span><span class="sxs-lookup"><span data-stu-id="5d4dd-208">Reaction removed from bot message</span></span>](#reactions-removed-from-bot-message) | <span data-ttu-id="5d4dd-209">Todos</span><span class="sxs-lookup"><span data-stu-id="5d4dd-209">All</span></span>   |

### <a name="reactions-to-a-bot-message"></a><span data-ttu-id="5d4dd-210">Reações a uma mensagem de bot</span><span class="sxs-lookup"><span data-stu-id="5d4dd-210">Reactions to a bot message</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="5d4dd-211">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="5d4dd-211">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnReactionsAddedAsync(IList<MessageReaction> messageReactions, ITurnContext<IMessageReactionActivity> turnContext, CancellationToken cancellationToken)
{
    foreach (var reaction in messageReactions)
    {
      var newReaction = $"You reacted with '{reaction.Type}' to the following message: '{turnContext.Activity.ReplyToId}'";
      var replyActivity = MessageFactory.Text(newReaction);
      var resourceResponse = await turnContext.SendActivityAsync(replyActivity, cancellationToken);
    }
}
```

# <a name="typescriptnodejstabtypescript"></a>[<span data-ttu-id="5d4dd-212">TypeScript/node. js</span><span class="sxs-lookup"><span data-stu-id="5d4dd-212">TypeScript/Node.js</span></span>](#tab/typescript)

<!-- Verify -->

```typescript

export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onReactionsAdded(async (context, next) => {
           const reactionsAdded = context.activity.reactionsAdded;
            if (reactionsAdded && reactionsAdded.length > 0) {
                for (let i = 0; i < reactionsAdded.length; i++) {
                    const reaction = reactionsAdded[i];
                    const newReaction = `You reacted with '${reaction.type}' to the following message: '${context.activity.replyToId}'`;
                    const resourceResponse = context.sendActivity(newReaction);
                    // Save information about the sent message and its ID (resourceResponse.id).
                }
            }
        });
    }
}

```

# <a name="jsontabjson"></a>[<span data-ttu-id="5d4dd-213">JSON</span><span class="sxs-lookup"><span data-stu-id="5d4dd-213">JSON</span></span>](#tab/json)

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
    "replyToId": "1575667808184",
    "legacy": {
      "replyToId": "1:19uJ8TZA1cZcms7-2HLOW3pWRF4nSWEoVnRqc0DPa_kY"
    }
}
```

# <a name="pythontabpython"></a>[<span data-ttu-id="5d4dd-214">Python</span><span class="sxs-lookup"><span data-stu-id="5d4dd-214">Python</span></span>](#tab/python)

```python
async def on_reactions_added(
    self, message_reactions: List[MessageReaction], turn_context: TurnContext
):
    for reaction in message_reactions:
        activity = await self._log.find(turn_context.activity.reply_to_id)
        if not activity:
            await self._send_message_and_log_activity_id(
                turn_context,
                f"Activity {turn_context.activity.reply_to_id} not found in log",
            )
        else:
            await self._send_message_and_log_activity_id(
                turn_context,
                f"You added '{reaction.type}' regarding '{activity.text}'",
            )
    return
```

* * *

### <a name="reactions-removed-from-bot-message"></a><span data-ttu-id="5d4dd-215">Reações removidas da mensagem de bot</span><span class="sxs-lookup"><span data-stu-id="5d4dd-215">Reactions removed from bot message</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="5d4dd-216">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="5d4dd-216">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnReactionsRemovedAsync(IList<MessageReaction> messageReactions, ITurnContext<IMessageReactionActivity> turnContext, CancellationToken cancellationToken)
{
    foreach (var reaction in messageReactions)
    {
      var newReaction = $"You removed the reaction '{reaction.Type}' from the following message: '{turnContext.Activity.ReplyToId}'";
      var replyActivity = MessageFactory.Text(newReaction);
      var resourceResponse = await turnContext.SendActivityAsync(replyActivity, cancellationToken);
    }
}
```

# <a name="typescriptnodejstabtypescript"></a>[<span data-ttu-id="5d4dd-217">TypeScript/node. js</span><span class="sxs-lookup"><span data-stu-id="5d4dd-217">TypeScript/Node.js</span></span>](#tab/typescript)

<!-- Verify -->

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onReactionsRemoved(async(context,next)=>{
            const reactionsRemoved = context.activity.reactionsRemoved;
            if (reactionsRemoved && reactionsRemoved.length > 0) {
                for (let i = 0; i < reactionsRemoved.length; i++) {
                    const reaction = reactionsRemoved[i];
                    const newReaction = `You removed the reaction '${reaction.type}' from the message: '${context.activity.replyToId}'`;
                    const resourceResponse = context.sendActivity(newReaction);
                    // Save information about the sent message and its ID (resourceResponse.id).
                }
            }
        });
    }
}
```

# <a name="jsontabjson"></a>[<span data-ttu-id="5d4dd-218">JSON</span><span class="sxs-lookup"><span data-stu-id="5d4dd-218">JSON</span></span>](#tab/json)

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
    "replyToId": "1575667808184",
    "legacy": {
      "replyToId": "1:19uJ8TZA1cZcms7-2HLOW3pWRF4nSWEoVnRqc0DPa_kY"
    }
}
```

# <a name="pythontabpython"></a>[<span data-ttu-id="5d4dd-219">Python</span><span class="sxs-lookup"><span data-stu-id="5d4dd-219">Python</span></span>](#tab/python)

```python
async def on_reactions_removed(
    self, message_reactions: List[MessageReaction], turn_context: TurnContext
):
    for reaction in message_reactions:
        activity = await self._log.find(turn_context.activity.reply_to_id)
        if not activity:
            await self._send_message_and_log_activity_id(
                turn_context,
                f"Activity {turn_context.activity.reply_to_id} not found in log",
            )
        else:
            await self._send_message_and_log_activity_id(
                turn_context,
                f"You removed '{reaction.type}' regarding '{activity.text}'",
            )
    return
```

* * *
