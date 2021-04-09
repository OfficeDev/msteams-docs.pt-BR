---
title: Inscrever-se para eventos de conversa
author: WashingtonKayaker
description: Como assinar eventos de conversa do bot do Microsoft Teams.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: bc4ae36d8cffe5b19ee778a71e1c7b1c00c5e88c
ms.sourcegitcommit: b50f6d68482cad43a60642a9947d1be17809a7df
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2021
ms.locfileid: "51634499"
---
# <a name="subscribe-to-conversation-events"></a><span data-ttu-id="ab6fb-103">Inscrever-se para eventos de conversa</span><span class="sxs-lookup"><span data-stu-id="ab6fb-103">Subscribe to conversation events</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="ab6fb-104">Microsoft Teams envia notificações ao seu bot para eventos que acontecem em escopos onde o seu bot está ativo.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-104">Microsoft Teams sends notifications to your bot for events that happen in scopes where your bot is active.</span></span> <span data-ttu-id="ab6fb-105">Você pode capturar esses eventos em seu código e agir sobre eles, como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ab6fb-105">You can capture these events in your code and take action on them, such as the following:</span></span>

* <span data-ttu-id="ab6fb-106">Disparar uma mensagem de boas-vindas quando seu bot é adicionado a uma equipe</span><span class="sxs-lookup"><span data-stu-id="ab6fb-106">Trigger a welcome message when your bot is added to a team</span></span>
* <span data-ttu-id="ab6fb-107">Disparar uma mensagem de boas-vindas quando um novo membro da equipe é adicionado ou removido</span><span class="sxs-lookup"><span data-stu-id="ab6fb-107">Trigger a welcome message when a new team member is added or removed</span></span>
* <span data-ttu-id="ab6fb-108">Disparar uma notificação quando um canal é criado, renomeado ou excluído</span><span class="sxs-lookup"><span data-stu-id="ab6fb-108">Trigger a notification when a channel is created, renamed or deleted</span></span>
* <span data-ttu-id="ab6fb-109">Quando uma mensagem de bot é curtida por um usuário</span><span class="sxs-lookup"><span data-stu-id="ab6fb-109">When a bot message is liked by a user</span></span>

## <a name="conversation-update-events"></a><span data-ttu-id="ab6fb-110">Eventos de atualização de conversa</span><span class="sxs-lookup"><span data-stu-id="ab6fb-110">Conversation update events</span></span>

> [!Important]
> <span data-ttu-id="ab6fb-111">Novos eventos podem ser adicionados a qualquer momento e seu bot começará a recebê-los.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-111">New events can be added at any time, and your bot will begin to receive them.</span></span>
> <span data-ttu-id="ab6fb-112">Você deve projetar para a possibilidade de receber eventos inesperados.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-112">You must design for the possibility of receiving unexpected events.</span></span>
> <span data-ttu-id="ab6fb-113">Se você estiver usando o SDK da Estrutura de Bots, seu bot responderá automaticamente com um a quaisquer eventos `200 - OK` que você não escolher manipular.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-113">If you are using the Bot Framework SDK, your bot will automatically respond with a `200 - OK` to any events you do not choose to handle.</span></span>

<span data-ttu-id="ab6fb-114">Um bot recebe um evento `conversationUpdate` quando é adicionado a uma conversa, outros membros são adicionados ou removidos de uma conversa ou os metadados da conversa são alterados.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-114">A bot receives a `conversationUpdate` event when it has been added to a conversation, other members have been added to or removed from a conversation, or conversation metadata has changed.</span></span>

<span data-ttu-id="ab6fb-115">O evento `conversationUpdate` é enviado ao seu bot quando ele recebe informações sobre atualizações de membros para as equipes onde foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-115">The `conversationUpdate` event is sent to your bot when it receives information on membership updates for teams where it has been added.</span></span> <span data-ttu-id="ab6fb-116">Ele também recebe uma atualização quando é adicionado pela primeira vez, especificamente para conversas pessoais.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-116">It also receives an update when it has been added for the first time specifically for personal conversations.</span></span>

<span data-ttu-id="ab6fb-117">A tabela a seguir mostra uma lista de eventos de atualização de conversa do Teams, com links para mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-117">The following table shows a list of Teams conversation update events, with links to more details.</span></span>

| <span data-ttu-id="ab6fb-118">Ação tomada</span><span class="sxs-lookup"><span data-stu-id="ab6fb-118">Action Taken</span></span>        | <span data-ttu-id="ab6fb-119">EventType</span><span class="sxs-lookup"><span data-stu-id="ab6fb-119">EventType</span></span>         | <span data-ttu-id="ab6fb-120">Método Chamado</span><span class="sxs-lookup"><span data-stu-id="ab6fb-120">Method Called</span></span>              | <span data-ttu-id="ab6fb-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="ab6fb-121">Description</span></span>                | <span data-ttu-id="ab6fb-122">Escopo</span><span class="sxs-lookup"><span data-stu-id="ab6fb-122">Scope</span></span> |
| ------------------- | ----------------- | -------------------------- | -------------------------- | ----- |
| <span data-ttu-id="ab6fb-123">canal criado</span><span class="sxs-lookup"><span data-stu-id="ab6fb-123">channel created</span></span>     | <span data-ttu-id="ab6fb-124">channelCreated</span><span class="sxs-lookup"><span data-stu-id="ab6fb-124">channelCreated</span></span>    | <span data-ttu-id="ab6fb-125">OnTeamsChannelCreatedAsync</span><span class="sxs-lookup"><span data-stu-id="ab6fb-125">OnTeamsChannelCreatedAsync</span></span> | [<span data-ttu-id="ab6fb-126">Um canal foi criado</span><span class="sxs-lookup"><span data-stu-id="ab6fb-126">A channel was created</span></span>](#channel-created) | <span data-ttu-id="ab6fb-127">Equipe</span><span class="sxs-lookup"><span data-stu-id="ab6fb-127">Team</span></span> |
| <span data-ttu-id="ab6fb-128">canal renomeado</span><span class="sxs-lookup"><span data-stu-id="ab6fb-128">channel renamed</span></span>     | <span data-ttu-id="ab6fb-129">channelRenamed</span><span class="sxs-lookup"><span data-stu-id="ab6fb-129">channelRenamed</span></span>    | <span data-ttu-id="ab6fb-130">OnTeamsChannelRenamedAsync</span><span class="sxs-lookup"><span data-stu-id="ab6fb-130">OnTeamsChannelRenamedAsync</span></span> | [<span data-ttu-id="ab6fb-131">Um canal foi renomeado</span><span class="sxs-lookup"><span data-stu-id="ab6fb-131">A channel was renamed</span></span>](#channel-renamed) | <span data-ttu-id="ab6fb-132">Equipe</span><span class="sxs-lookup"><span data-stu-id="ab6fb-132">Team</span></span> |
| <span data-ttu-id="ab6fb-133">canal excluído</span><span class="sxs-lookup"><span data-stu-id="ab6fb-133">channel deleted</span></span>     | <span data-ttu-id="ab6fb-134">channelDeleted</span><span class="sxs-lookup"><span data-stu-id="ab6fb-134">channelDeleted</span></span>    | <span data-ttu-id="ab6fb-135">OnTeamsChannelDeletedAsync</span><span class="sxs-lookup"><span data-stu-id="ab6fb-135">OnTeamsChannelDeletedAsync</span></span> | [<span data-ttu-id="ab6fb-136">Um canal foi excluído</span><span class="sxs-lookup"><span data-stu-id="ab6fb-136">A channel was deleted</span></span>](#channel-deleted) | <span data-ttu-id="ab6fb-137">Equipe</span><span class="sxs-lookup"><span data-stu-id="ab6fb-137">Team</span></span> |
| <span data-ttu-id="ab6fb-138">canal restaurado</span><span class="sxs-lookup"><span data-stu-id="ab6fb-138">channel restored</span></span>    | <span data-ttu-id="ab6fb-139">channelRestored</span><span class="sxs-lookup"><span data-stu-id="ab6fb-139">channelRestored</span></span>    | <span data-ttu-id="ab6fb-140">OnTeamsChannelRestoredAsync</span><span class="sxs-lookup"><span data-stu-id="ab6fb-140">OnTeamsChannelRestoredAsync</span></span> | [<span data-ttu-id="ab6fb-141">Um canal foi restaurado</span><span class="sxs-lookup"><span data-stu-id="ab6fb-141">A channel was restored</span></span>](#channel-deleted) | <span data-ttu-id="ab6fb-142">Equipe</span><span class="sxs-lookup"><span data-stu-id="ab6fb-142">Team</span></span> |
| <span data-ttu-id="ab6fb-143">membros adicionados</span><span class="sxs-lookup"><span data-stu-id="ab6fb-143">members added</span></span>   | <span data-ttu-id="ab6fb-144">membersAdded</span><span class="sxs-lookup"><span data-stu-id="ab6fb-144">membersAdded</span></span>   | <span data-ttu-id="ab6fb-145">OnTeamsMembersAddedAsync</span><span class="sxs-lookup"><span data-stu-id="ab6fb-145">OnTeamsMembersAddedAsync</span></span>   | [<span data-ttu-id="ab6fb-146">Um membro adicionado</span><span class="sxs-lookup"><span data-stu-id="ab6fb-146">A member added</span></span>](#team-members-added)   | <span data-ttu-id="ab6fb-147">Todos</span><span class="sxs-lookup"><span data-stu-id="ab6fb-147">All</span></span> |
| <span data-ttu-id="ab6fb-148">membros removidos</span><span class="sxs-lookup"><span data-stu-id="ab6fb-148">members removed</span></span> | <span data-ttu-id="ab6fb-149">membersRemoved</span><span class="sxs-lookup"><span data-stu-id="ab6fb-149">membersRemoved</span></span> | <span data-ttu-id="ab6fb-150">OnTeamsMembersRemovedAsync</span><span class="sxs-lookup"><span data-stu-id="ab6fb-150">OnTeamsMembersRemovedAsync</span></span> | [<span data-ttu-id="ab6fb-151">Um membro foi removido</span><span class="sxs-lookup"><span data-stu-id="ab6fb-151">A member was removed</span></span>](#team-members-removed) | <span data-ttu-id="ab6fb-152">groupChat & equipe</span><span class="sxs-lookup"><span data-stu-id="ab6fb-152">groupChat & team</span></span> |
| <span data-ttu-id="ab6fb-153">equipe renomeada</span><span class="sxs-lookup"><span data-stu-id="ab6fb-153">team renamed</span></span>        | <span data-ttu-id="ab6fb-154">teamRenamed</span><span class="sxs-lookup"><span data-stu-id="ab6fb-154">teamRenamed</span></span>       | <span data-ttu-id="ab6fb-155">OnTeamsTeamRenamedAsync</span><span class="sxs-lookup"><span data-stu-id="ab6fb-155">OnTeamsTeamRenamedAsync</span></span>    | [<span data-ttu-id="ab6fb-156">Uma equipe foi renomeada</span><span class="sxs-lookup"><span data-stu-id="ab6fb-156">A Team was renamed</span></span>](#team-renamed)       | <span data-ttu-id="ab6fb-157">Equipe</span><span class="sxs-lookup"><span data-stu-id="ab6fb-157">Team</span></span> |
| <span data-ttu-id="ab6fb-158">equipe excluída</span><span class="sxs-lookup"><span data-stu-id="ab6fb-158">team deleted</span></span>        | <span data-ttu-id="ab6fb-159">teamDeleted</span><span class="sxs-lookup"><span data-stu-id="ab6fb-159">teamDeleted</span></span>       | <span data-ttu-id="ab6fb-160">OnTeamsTeamDeletedAsync</span><span class="sxs-lookup"><span data-stu-id="ab6fb-160">OnTeamsTeamDeletedAsync</span></span>    | [<span data-ttu-id="ab6fb-161">Uma equipe foi excluída</span><span class="sxs-lookup"><span data-stu-id="ab6fb-161">A Team was deleted</span></span>](#team-deleted)       | <span data-ttu-id="ab6fb-162">Equipe</span><span class="sxs-lookup"><span data-stu-id="ab6fb-162">Team</span></span> |
| <span data-ttu-id="ab6fb-163">equipe arquivada</span><span class="sxs-lookup"><span data-stu-id="ab6fb-163">team archived</span></span>        | <span data-ttu-id="ab6fb-164">teamArchived</span><span class="sxs-lookup"><span data-stu-id="ab6fb-164">teamArchived</span></span>       | <span data-ttu-id="ab6fb-165">OnTeamsTeamArchivedAsync</span><span class="sxs-lookup"><span data-stu-id="ab6fb-165">OnTeamsTeamArchivedAsync</span></span>    | [<span data-ttu-id="ab6fb-166">Uma equipe foi arquivada</span><span class="sxs-lookup"><span data-stu-id="ab6fb-166">A Team was archived</span></span>](#team-archived)       | <span data-ttu-id="ab6fb-167">Equipe</span><span class="sxs-lookup"><span data-stu-id="ab6fb-167">Team</span></span> |
| <span data-ttu-id="ab6fb-168">team unarchived</span><span class="sxs-lookup"><span data-stu-id="ab6fb-168">team unarchived</span></span>        | <span data-ttu-id="ab6fb-169">teamUnarchived</span><span class="sxs-lookup"><span data-stu-id="ab6fb-169">teamUnarchived</span></span>       | <span data-ttu-id="ab6fb-170">OnTeamsTeamUnarchivedAsync</span><span class="sxs-lookup"><span data-stu-id="ab6fb-170">OnTeamsTeamUnarchivedAsync</span></span>    | [<span data-ttu-id="ab6fb-171">Uma equipe foi desarquivada</span><span class="sxs-lookup"><span data-stu-id="ab6fb-171">A Team was unarchived</span></span>](#team-unarchived)       | <span data-ttu-id="ab6fb-172">Equipe</span><span class="sxs-lookup"><span data-stu-id="ab6fb-172">Team</span></span> |
| <span data-ttu-id="ab6fb-173">equipe restaurada</span><span class="sxs-lookup"><span data-stu-id="ab6fb-173">team restored</span></span>        | <span data-ttu-id="ab6fb-174">teamRestored</span><span class="sxs-lookup"><span data-stu-id="ab6fb-174">teamRestored</span></span>      | <span data-ttu-id="ab6fb-175">OnTeamsTeamRestoredAsync</span><span class="sxs-lookup"><span data-stu-id="ab6fb-175">OnTeamsTeamRestoredAsync</span></span>    | [<span data-ttu-id="ab6fb-176">Uma equipe foi restaurada</span><span class="sxs-lookup"><span data-stu-id="ab6fb-176">A Team was restored</span></span>](#team-restored)       | <span data-ttu-id="ab6fb-177">Equipe</span><span class="sxs-lookup"><span data-stu-id="ab6fb-177">Team</span></span> |

### <a name="channel-created"></a><span data-ttu-id="ab6fb-178">Canal criado</span><span class="sxs-lookup"><span data-stu-id="ab6fb-178">Channel created</span></span>

<span data-ttu-id="ab6fb-179">O evento criado pelo canal é enviado para o bot sempre que um novo canal é criado em uma equipe em que seu bot está instalado.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-179">The channel created event is sent to your bot whenever a new channel is created in a team your bot is installed in.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="ab6fb-180">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="ab6fb-180">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelCreatedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the Channel created");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="ab6fb-181">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="ab6fb-181">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="ab6fb-182">JSON</span><span class="sxs-lookup"><span data-stu-id="ab6fb-182">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="ab6fb-183">Python</span><span class="sxs-lookup"><span data-stu-id="ab6fb-183">Python</span></span>](#tab/python)

```python
async def on_teams_channel_created(
    self, channel_info: ChannelInfo, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(
            f"The new channel is {channel_info.name}. The channel id is {channel_info.id}"
        )
    )
```

* * *

### <a name="channel-renamed"></a><span data-ttu-id="ab6fb-184">Canal renomeado</span><span class="sxs-lookup"><span data-stu-id="ab6fb-184">Channel renamed</span></span>

<span data-ttu-id="ab6fb-185">O evento renomeado de canal é enviado para o bot sempre que um canal é renomeado em uma equipe em que seu bot está instalado.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-185">The channel renamed event is sent to your bot whenever a channel is renamed in a team your bot is installed in.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="ab6fb-186">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="ab6fb-186">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelRenamedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the new Channel name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="ab6fb-187">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="ab6fb-187">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="ab6fb-188">JSON</span><span class="sxs-lookup"><span data-stu-id="ab6fb-188">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="ab6fb-189">Python</span><span class="sxs-lookup"><span data-stu-id="ab6fb-189">Python</span></span>](#tab/python)

```python
async def on_teams_channel_renamed(
    self, channel_info: ChannelInfo, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The new channel name is {channel_info.name}")
    )
```

* * *

### <a name="channel-deleted"></a><span data-ttu-id="ab6fb-190">Canal Excluído</span><span class="sxs-lookup"><span data-stu-id="ab6fb-190">Channel Deleted</span></span>

<span data-ttu-id="ab6fb-191">O evento excluído do canal é enviado ao bot sempre que um canal é excluído em uma equipe em que seu bot está instalado.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-191">The channel deleted event is sent to your bot whenever a channel is deleted in a team your bot is installed in.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="ab6fb-192">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="ab6fb-192">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelDeletedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the Channel deleted");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="ab6fb-193">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="ab6fb-193">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="ab6fb-194">JSON</span><span class="sxs-lookup"><span data-stu-id="ab6fb-194">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="ab6fb-195">Python</span><span class="sxs-lookup"><span data-stu-id="ab6fb-195">Python</span></span>](#tab/python)

```python
async def on_teams_channel_deleted(
    self, channel_info: ChannelInfo, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The deleted channel is {channel_info.name}")
    )
```

* * *

### <a name="channel-restored"></a><span data-ttu-id="ab6fb-196">Canal restaurado</span><span class="sxs-lookup"><span data-stu-id="ab6fb-196">Channel restored</span></span>

<span data-ttu-id="ab6fb-197">O evento restaurado do canal é enviado para o bot sempre que um canal excluído anteriormente é restaurado em uma equipe em que o bot já está instalado.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-197">The channel restored event is sent to your bot whenever a channel that was previously deleted is restored in a team that your bot is already installed in.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="ab6fb-198">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="ab6fb-198">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelRestoredAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the Channel restored.");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="ab6fb-199">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="ab6fb-199">TypeScript/Node.js</span></span>](#tab/typescript)

<!-- From sample: botbuilder-js\libraries\botbuilder\tests\teams\conversationUpdate\src\conversationUpdateBot.ts -->

```typescript

export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsChannelRestoredEvent(async (channelInfo: ChannelInfo, teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
            const card = CardFactory.heroCard('Channel Restored', `${channelInfo.name} is the Channel restored`);
            const message = MessageFactory.attachment(card);
            await turnContext.sendActivity(message);
            await next();
        });
    }
}

```

# <a name="json"></a>[<span data-ttu-id="ab6fb-200">JSON</span><span class="sxs-lookup"><span data-stu-id="ab6fb-200">JSON</span></span>](#tab/json)

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
        "eventType": "channelRestored",
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```

# <a name="python"></a>[<span data-ttu-id="ab6fb-201">Python</span><span class="sxs-lookup"><span data-stu-id="ab6fb-201">Python</span></span>](#tab/python)

```python
async def on_teams_channel_restored(
    self, channel_info: ChannelInfo, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(
            f"The restored channel is {channel_info.name}. The channel id is {channel_info.id}"
        )
    )
```

* * *

### <a name="team-members-added"></a><span data-ttu-id="ab6fb-202">Membros da equipe adicionados</span><span class="sxs-lookup"><span data-stu-id="ab6fb-202">Team members added</span></span>

<span data-ttu-id="ab6fb-203">O evento é enviado ao bot na primeira vez em que é adicionado a uma conversa e sempre que um novo usuário é adicionado a uma equipe ou chat de grupo em que seu bot está `teamMemberAdded` instalado.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-203">The `teamMemberAdded` event is sent to your bot the first time it is added to a conversation and every time a new user is added to a team or group chat that your bot is installed in.</span></span> <span data-ttu-id="ab6fb-204">As informações do usuário (ID) são exclusivas para seu bot e podem ser armazenadas em cache para uso futuro pelo serviço (como o envio de uma mensagem para um usuário específico).</span><span class="sxs-lookup"><span data-stu-id="ab6fb-204">The user information (ID) is unique for your bot and can be cached for future use by your service (such as sending a message to a specific user).</span></span>

# <a name="cnet"></a>[<span data-ttu-id="ab6fb-205">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="ab6fb-205">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsMembersAddedAsync(IList<TeamsChannelAccount> teamsMembersAdded , TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    foreach (TeamsChannelAccount member in teamsMembersAdded)
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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="ab6fb-206">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="ab6fb-206">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="ab6fb-207">JSON</span><span class="sxs-lookup"><span data-stu-id="ab6fb-207">JSON</span></span>](#tab/json)

<span data-ttu-id="ab6fb-208">Esta é a mensagem que seu bot receberá quando o bot for adicionado **a uma equipe**.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-208">This is the message your bot will receive when the bot is added **to a team**.</span></span>

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

<span data-ttu-id="ab6fb-209">Esta é a mensagem que seu bot receberá quando o bot for adicionado \* a um *chat um para um.*</span><span class="sxs-lookup"><span data-stu-id="ab6fb-209">This is the message your bot will receive when the bot is added \**to a one-to-one chat*.</span></span>

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

# <a name="python"></a>[<span data-ttu-id="ab6fb-210">Python</span><span class="sxs-lookup"><span data-stu-id="ab6fb-210">Python</span></span>](#tab/python)

```python
async def on_teams_members_added(
    self, teams_members_added: [TeamsChannelAccount], turn_context: TurnContext
):
    for member in teams_members_added:
        await turn_context.send_activity(
            MessageFactory.text(f"Welcome your new team member {member.id}")
        )
    return
```

* * *

### <a name="team-members-removed"></a><span data-ttu-id="ab6fb-211">Membros da equipe removidos</span><span class="sxs-lookup"><span data-stu-id="ab6fb-211">Team members removed</span></span>

<span data-ttu-id="ab6fb-212">O evento é enviado para o bot se ele for removido de uma equipe e sempre que qualquer usuário for removido de uma equipe da que seu bot é `teamMemberRemoved` membro.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-212">The `teamMemberRemoved` event is sent to your bot if it is removed from a team and every time any user is removed from a team that your bot is a member of.</span></span> <span data-ttu-id="ab6fb-213">Você pode determinar se o novo membro removido foi o próprio bot ou um usuário olhando para o `Activity` objeto do `turnContext` .</span><span class="sxs-lookup"><span data-stu-id="ab6fb-213">You can determine if the new member removed was the bot itself or a user by looking at the `Activity` object of the `turnContext`.</span></span>  <span data-ttu-id="ab6fb-214">Se o campo do objeto for igual ao campo do objeto, o membro removido será o bot, caso `Id` `MembersRemoved` `Id` `Recipient` contrário, será um usuário.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-214">If the `Id` field of the `MembersRemoved` object is the same as the `Id` field of the `Recipient` object, then the member removed is the bot, otherwise, it is a user.</span></span>  <span data-ttu-id="ab6fb-215">Geralmente, o bot `Id` será: `28:<MicrosoftAppId>`</span><span class="sxs-lookup"><span data-stu-id="ab6fb-215">The bot's `Id` will generally be: `28:<MicrosoftAppId>`</span></span>

[!Note] <span data-ttu-id="ab6fb-216">Quando um usuário é excluído permanentemente de um locatário, `membersRemoved conversationUpdate` o evento é acionado.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-216">When a user is permanently deleted from a tenant, `membersRemoved conversationUpdate` event is triggered.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="ab6fb-217">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="ab6fb-217">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="ab6fb-218">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="ab6fb-218">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="ab6fb-219">JSON</span><span class="sxs-lookup"><span data-stu-id="ab6fb-219">JSON</span></span>](#tab/json)

<span data-ttu-id="ab6fb-220">O objeto no exemplo de carga a seguir baseia-se na adição de um membro a uma equipe em vez de um chat em grupo ou na inicialização de uma nova conversa um `channelData` para um:</span><span class="sxs-lookup"><span data-stu-id="ab6fb-220">The `channelData` object in the following payload example is based on adding a member to a team rather than a group chat, or initiating a new one-to-one conversation:</span></span>

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


# <a name="python"></a>[<span data-ttu-id="ab6fb-221">Python</span><span class="sxs-lookup"><span data-stu-id="ab6fb-221">Python</span></span>](#tab/python)

```python
async def on_teams_members_removed(
    self, teams_members_removed: [TeamsChannelAccount], turn_context: TurnContext
):
    for member in teams_members_removed:
        await turn_context.send_activity(
            MessageFactory.text(f"Say goodbye to {member.id}")
        )
    return
```

* * *

### <a name="team-renamed"></a><span data-ttu-id="ab6fb-222">Equipe renomeada</span><span class="sxs-lookup"><span data-stu-id="ab6fb-222">Team renamed</span></span>

<span data-ttu-id="ab6fb-223">Seu bot é notificado quando a equipe em que está foi renomeada.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-223">Your bot is notified when the team it is in has been renamed.</span></span> <span data-ttu-id="ab6fb-224">Ele recebe um `conversationUpdate` evento `eventType.teamRenamed` com no `channelData` objeto.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-224">It receives a `conversationUpdate` event with `eventType.teamRenamed` in the `channelData` object.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="ab6fb-225">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="ab6fb-225">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamRenamedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the new Team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="ab6fb-226">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="ab6fb-226">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="ab6fb-227">JSON</span><span class="sxs-lookup"><span data-stu-id="ab6fb-227">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="ab6fb-228">Python</span><span class="sxs-lookup"><span data-stu-id="ab6fb-228">Python</span></span>](#tab/python)

```python
async def on_teams_team_renamed(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The new team name is {team_info.name}")
    )
```

* * *

### <a name="team-deleted"></a><span data-ttu-id="ab6fb-229">Equipe excluída</span><span class="sxs-lookup"><span data-stu-id="ab6fb-229">Team deleted</span></span>

<span data-ttu-id="ab6fb-230">Seu bot é notificado quando a equipe em que está foi excluída.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-230">Your bot is notified when the team it is in has been deleted.</span></span> <span data-ttu-id="ab6fb-231">Ele recebe um `conversationUpdate` evento `eventType.teamDeleted` com no `channelData` objeto.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-231">It receives a `conversationUpdate` event with `eventType.teamDeleted` in the `channelData` object.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="ab6fb-232">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="ab6fb-232">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamDeletedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    //handle delete event
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="ab6fb-233">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="ab6fb-233">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsTeamDeletedEvent(async (teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
            //handle delete event
            await next();
        });
    }
}
```

# <a name="json"></a>[<span data-ttu-id="ab6fb-234">JSON</span><span class="sxs-lookup"><span data-stu-id="ab6fb-234">JSON</span></span>](#tab/json)

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
            "name": "Team Name"
        },
        "eventType": "teamDeleted",
        "tenant": { 
           "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```

# <a name="python"></a>[<span data-ttu-id="ab6fb-235">Python</span><span class="sxs-lookup"><span data-stu-id="ab6fb-235">Python</span></span>](#tab/python)

```python
async def on_teams_team_deleted(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    //handle delete event
    )
```

* * *

### <a name="team-restored"></a><span data-ttu-id="ab6fb-236">Equipe restaurada</span><span class="sxs-lookup"><span data-stu-id="ab6fb-236">Team restored</span></span>

<span data-ttu-id="ab6fb-237">O bot recebe uma notificação quando a equipe é restaurada da exclusão.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-237">The bot receives a notification when the team is restored from deletion.</span></span> <span data-ttu-id="ab6fb-238">O bot recebe `conversationUpdate` um evento com no `eventType.teamrestored` `channelData` objeto.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-238">The bot receives a `conversationUpdate` event with `eventType.teamrestored` in the `channelData` object.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="ab6fb-239">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="ab6fb-239">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamrestoredAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="ab6fb-240">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="ab6fb-240">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsTeamrestoredEvent(async (teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
            const card = CardFactory.heroCard('Team restored', `${teamInfo.name} is the team name`);
            const message = MessageFactory.attachment(card);
            await turnContext.sendActivity(message);
            await next();
        });
    }
}
```

# <a name="json"></a>[<span data-ttu-id="ab6fb-241">JSON</span><span class="sxs-lookup"><span data-stu-id="ab6fb-241">JSON</span></span>](#tab/json)

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
            "name": "Team Name"
        },
        "eventType": "teamrestored",
        "tenant": { 
           "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```

# <a name="python"></a>[<span data-ttu-id="ab6fb-242">Python</span><span class="sxs-lookup"><span data-stu-id="ab6fb-242">Python</span></span>](#tab/python)

```python
async def on_teams_team_restored(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The team name is {team_info.name}")
    )
```

* * *

### <a name="team-archived"></a><span data-ttu-id="ab6fb-243">Equipe arquivada</span><span class="sxs-lookup"><span data-stu-id="ab6fb-243">Team archived</span></span>

<span data-ttu-id="ab6fb-244">O bot recebe uma notificação quando a equipe em que está instalada é arquivada.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-244">The bot receives a notification when the team it is installed in is archived.</span></span> <span data-ttu-id="ab6fb-245">Ele recebe um `conversationUpdate` evento `eventType.teamarchived` com no `channelData` objeto.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-245">It receives a `conversationUpdate` event with `eventType.teamarchived` in the `channelData` object.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="ab6fb-246">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="ab6fb-246">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamArchivedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="ab6fb-247">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="ab6fb-247">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsTeamArchivedEvent(async (teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
            const card = CardFactory.heroCard('Team archived', `${teamInfo.name} is the team name`);
            const message = MessageFactory.attachment(card);
            await turnContext.sendActivity(message);
            await next();
        });
    }
}
```

# <a name="json"></a>[<span data-ttu-id="ab6fb-248">JSON</span><span class="sxs-lookup"><span data-stu-id="ab6fb-248">JSON</span></span>](#tab/json)

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
            "name": "Team Name"
        },
        "eventType": "teamArchived",
        "tenant": { 
           "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```

# <a name="python"></a>[<span data-ttu-id="ab6fb-249">Python</span><span class="sxs-lookup"><span data-stu-id="ab6fb-249">Python</span></span>](#tab/python)

```python
async def on_teams_team_archived(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The team name is {team_info.name}")
    )
```

* * *


### <a name="team-unarchived"></a><span data-ttu-id="ab6fb-250">Equipe desarquivada</span><span class="sxs-lookup"><span data-stu-id="ab6fb-250">Team unarchived</span></span>

<span data-ttu-id="ab6fb-251">O bot recebe uma notificação quando a equipe em que ele está instalado é desarquivada.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-251">The bot receives a notification when the team it is installed in is unarchived.</span></span> <span data-ttu-id="ab6fb-252">Ele recebe um `conversationUpdate` evento `eventType.teamUnarchived` com no `channelData` objeto.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-252">It receives a `conversationUpdate` event with `eventType.teamUnarchived` in the `channelData` object.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="ab6fb-253">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="ab6fb-253">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamUnarchivedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="ab6fb-254">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="ab6fb-254">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsTeamUnarchivedEvent(async (teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
            const card = CardFactory.heroCard('Team archived', `${teamInfo.name} is the team name`);
            const message = MessageFactory.attachment(card);
            await turnContext.sendActivity(message);
            await next();
        });
    }
}
```

# <a name="json"></a>[<span data-ttu-id="ab6fb-255">JSON</span><span class="sxs-lookup"><span data-stu-id="ab6fb-255">JSON</span></span>](#tab/json)

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
            "name": "Team Name"
        },
        "eventType": "teamUnarchived",
        "tenant": { 
           "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```

# <a name="python"></a>[<span data-ttu-id="ab6fb-256">Python</span><span class="sxs-lookup"><span data-stu-id="ab6fb-256">Python</span></span>](#tab/python)

```python
async def on_teams_team_unarchived(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The team name is {team_info.name}")
    )
```

* * *

## <a name="message-reaction-events"></a><span data-ttu-id="ab6fb-257">Eventos de reação de mensagens</span><span class="sxs-lookup"><span data-stu-id="ab6fb-257">Message reaction events</span></span>

<span data-ttu-id="ab6fb-258">O `messageReaction` evento é enviado quando um usuário adiciona ou remove reações a uma mensagem que foi enviada pelo bot.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-258">The `messageReaction` event is sent when a user adds or removes reactions to a message which was sent by your bot.</span></span> <span data-ttu-id="ab6fb-259">O `replyToId` contém a ID da mensagem específica e o `Type` é o tipo de reação no formato de texto.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-259">The `replyToId` contains the ID of the specific message, and the `Type` is the type of reaction in text format.</span></span>  <span data-ttu-id="ab6fb-260">Os tipos de reações incluem: "irado", "coração", "riso", "like", "Triste", "surpresa".</span><span class="sxs-lookup"><span data-stu-id="ab6fb-260">The types of reactions include: "angry", "heart", "laugh", "like", "Sad", "surprised".</span></span> <span data-ttu-id="ab6fb-261">Esse evento não contém o conteúdo da mensagem original, portanto, se processar reações às suas mensagens é importante para o bot, você precisará armazenar as mensagens quando enviá-las.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-261">This event does not contain the contents of the original message, so if processing reactions to your messages is important for your bot you'll need to store the messages when you send them.</span></span>

| <span data-ttu-id="ab6fb-262">EventType</span><span class="sxs-lookup"><span data-stu-id="ab6fb-262">EventType</span></span>       | <span data-ttu-id="ab6fb-263">Objeto Payload</span><span class="sxs-lookup"><span data-stu-id="ab6fb-263">Payload object</span></span>   | <span data-ttu-id="ab6fb-264">Descrição</span><span class="sxs-lookup"><span data-stu-id="ab6fb-264">Description</span></span>                                                             | <span data-ttu-id="ab6fb-265">Escopo</span><span class="sxs-lookup"><span data-stu-id="ab6fb-265">Scope</span></span> |
| --------------- | ---------------- | ----------------------------------------------------------------------- | ----- |
| <span data-ttu-id="ab6fb-266">messageReaction</span><span class="sxs-lookup"><span data-stu-id="ab6fb-266">messageReaction</span></span> | <span data-ttu-id="ab6fb-267">reactionsAdded</span><span class="sxs-lookup"><span data-stu-id="ab6fb-267">reactionsAdded</span></span>   | [<span data-ttu-id="ab6fb-268">Reação à mensagem bot</span><span class="sxs-lookup"><span data-stu-id="ab6fb-268">Reaction to bot message</span></span>](#reactions-to-a-bot-message)                   | <span data-ttu-id="ab6fb-269">Todos</span><span class="sxs-lookup"><span data-stu-id="ab6fb-269">All</span></span>   |
| <span data-ttu-id="ab6fb-270">messageReaction</span><span class="sxs-lookup"><span data-stu-id="ab6fb-270">messageReaction</span></span> | <span data-ttu-id="ab6fb-271">reactionsRemoved</span><span class="sxs-lookup"><span data-stu-id="ab6fb-271">reactionsRemoved</span></span> | [<span data-ttu-id="ab6fb-272">Reação removida da mensagem bot</span><span class="sxs-lookup"><span data-stu-id="ab6fb-272">Reaction removed from bot message</span></span>](#reactions-removed-from-bot-message) | <span data-ttu-id="ab6fb-273">Todos</span><span class="sxs-lookup"><span data-stu-id="ab6fb-273">All</span></span>   |

### <a name="reactions-to-a-bot-message"></a><span data-ttu-id="ab6fb-274">Reações a uma mensagem de bot</span><span class="sxs-lookup"><span data-stu-id="ab6fb-274">Reactions to a bot message</span></span>

# <a name="cnet"></a>[<span data-ttu-id="ab6fb-275">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="ab6fb-275">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="ab6fb-276">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="ab6fb-276">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="ab6fb-277">JSON</span><span class="sxs-lookup"><span data-stu-id="ab6fb-277">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="ab6fb-278">Python</span><span class="sxs-lookup"><span data-stu-id="ab6fb-278">Python</span></span>](#tab/python)

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

### <a name="reactions-removed-from-bot-message"></a><span data-ttu-id="ab6fb-279">Reações removidas da mensagem bot</span><span class="sxs-lookup"><span data-stu-id="ab6fb-279">Reactions removed from bot message</span></span>

# <a name="cnet"></a>[<span data-ttu-id="ab6fb-280">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="ab6fb-280">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="ab6fb-281">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="ab6fb-281">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="ab6fb-282">JSON</span><span class="sxs-lookup"><span data-stu-id="ab6fb-282">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="ab6fb-283">Python</span><span class="sxs-lookup"><span data-stu-id="ab6fb-283">Python</span></span>](#tab/python)

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

## <a name="samples"></a><span data-ttu-id="ab6fb-284">Exemplos</span><span class="sxs-lookup"><span data-stu-id="ab6fb-284">Samples</span></span>

<span data-ttu-id="ab6fb-285">Para um código de exemplo mostrando os eventos de conversa de bots, consulte:</span><span class="sxs-lookup"><span data-stu-id="ab6fb-285">For sample code showing the bots conversation events, see:</span></span>

[<span data-ttu-id="ab6fb-286">Exemplo de eventos de conversa de bots do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="ab6fb-286">Microsoft Teams bots conversation events sample</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot)



