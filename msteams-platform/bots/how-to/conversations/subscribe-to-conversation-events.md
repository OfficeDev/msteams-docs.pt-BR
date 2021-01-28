---
title: Inscrever-se para eventos de conversa
author: WashingtonKayaker
description: Como assinar eventos de conversa do seu bot do Microsoft Teams.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: b4dc70e4619043bd0b675206770093b086fc5ec6
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014317"
---
# <a name="subscribe-to-conversation-events"></a><span data-ttu-id="32f3c-103">Inscrever-se para eventos de conversa</span><span class="sxs-lookup"><span data-stu-id="32f3c-103">Subscribe to conversation events</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="32f3c-104">O Microsoft Teams envia notificações ao seu bot para eventos que ocorrem em escopos em que o bot está ativo.</span><span class="sxs-lookup"><span data-stu-id="32f3c-104">Microsoft Teams sends notifications to your bot for events that happen in scopes where your bot is active.</span></span> <span data-ttu-id="32f3c-105">Você pode capturar esses eventos em seu código e tomar medidas sobre eles, como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="32f3c-105">You can capture these events in your code and take action on them, such as the following:</span></span>

* <span data-ttu-id="32f3c-106">Disparar uma mensagem de boas-vindas quando seu bot for adicionado a uma equipe</span><span class="sxs-lookup"><span data-stu-id="32f3c-106">Trigger a welcome message when your bot is added to a team</span></span>
* <span data-ttu-id="32f3c-107">Disparar uma mensagem de boas-vindas quando um novo membro da equipe for adicionado ou removido</span><span class="sxs-lookup"><span data-stu-id="32f3c-107">Trigger a welcome message when a new team member is added or removed</span></span>
* <span data-ttu-id="32f3c-108">Disparar uma notificação quando um canal é criado, renomeado ou excluído</span><span class="sxs-lookup"><span data-stu-id="32f3c-108">Trigger a notification when a channel is created, renamed or deleted</span></span>
* <span data-ttu-id="32f3c-109">Quando uma mensagem de bot é curtida por um usuário</span><span class="sxs-lookup"><span data-stu-id="32f3c-109">When a bot message is liked by a user</span></span>

## <a name="conversation-update-events"></a><span data-ttu-id="32f3c-110">Eventos de atualização de conversa</span><span class="sxs-lookup"><span data-stu-id="32f3c-110">Conversation update events</span></span>

> [!Important]
> <span data-ttu-id="32f3c-111">Novos eventos podem ser adicionados a qualquer momento, e seu bot começará a recebê-los.</span><span class="sxs-lookup"><span data-stu-id="32f3c-111">New events can be added at any time, and your bot will begin to receive them.</span></span>
> <span data-ttu-id="32f3c-112">Você deve projetar para a possibilidade de receber eventos inesperados.</span><span class="sxs-lookup"><span data-stu-id="32f3c-112">You must design for the possibility of receiving unexpected events.</span></span>
> <span data-ttu-id="32f3c-113">Se você estiver usando o SDK do Bot Framework, seu bot responderá automaticamente com um evento `200 - OK` que você não escolher manipular.</span><span class="sxs-lookup"><span data-stu-id="32f3c-113">If you are using the Bot Framework SDK, your bot will automatically respond with a `200 - OK` to any events you do not choose to handle.</span></span>

<span data-ttu-id="32f3c-114">Um bot recebe um evento quando ele foi adicionado a uma conversa, outros membros foram adicionados ou removidos de uma conversa ou metadados de conversa `conversationUpdate` foram alterados.</span><span class="sxs-lookup"><span data-stu-id="32f3c-114">A bot receives a `conversationUpdate` event when it has been added to a conversation, other members have been added to or removed from a conversation, or conversation metadata has changed.</span></span>

<span data-ttu-id="32f3c-115">O evento é enviado ao seu bot quando ele recebe informações sobre atualizações de `conversationUpdate` associação para equipes em que foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="32f3c-115">The `conversationUpdate` event is sent to your bot when it receives information on membership updates for teams where it has been added.</span></span> <span data-ttu-id="32f3c-116">Ele também recebe uma atualização quando ela foi adicionada pela primeira vez especificamente para conversas pessoais.</span><span class="sxs-lookup"><span data-stu-id="32f3c-116">It also receives an update when it has been added for the first time specifically for personal conversations.</span></span>

<span data-ttu-id="32f3c-117">A tabela a seguir mostra uma lista de eventos de atualização de conversa do Teams, com links para mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="32f3c-117">The following table shows a list of Teams conversation update events, with links to more details.</span></span>

| <span data-ttu-id="32f3c-118">Ação tomada</span><span class="sxs-lookup"><span data-stu-id="32f3c-118">Action Taken</span></span>        | <span data-ttu-id="32f3c-119">EventType</span><span class="sxs-lookup"><span data-stu-id="32f3c-119">EventType</span></span>         | <span data-ttu-id="32f3c-120">Método Chamado</span><span class="sxs-lookup"><span data-stu-id="32f3c-120">Method Called</span></span>              | <span data-ttu-id="32f3c-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="32f3c-121">Description</span></span>                | <span data-ttu-id="32f3c-122">Escopo</span><span class="sxs-lookup"><span data-stu-id="32f3c-122">Scope</span></span> |
| ------------------- | ----------------- | -------------------------- | -------------------------- | ----- |
| <span data-ttu-id="32f3c-123">canal criado</span><span class="sxs-lookup"><span data-stu-id="32f3c-123">channel created</span></span>     | <span data-ttu-id="32f3c-124">channelCreated</span><span class="sxs-lookup"><span data-stu-id="32f3c-124">channelCreated</span></span>    | <span data-ttu-id="32f3c-125">OnTeamsChannelCreatedAsync</span><span class="sxs-lookup"><span data-stu-id="32f3c-125">OnTeamsChannelCreatedAsync</span></span> | [<span data-ttu-id="32f3c-126">Um canal foi criado</span><span class="sxs-lookup"><span data-stu-id="32f3c-126">A channel was created</span></span>](#channel-created) | <span data-ttu-id="32f3c-127">Equipe</span><span class="sxs-lookup"><span data-stu-id="32f3c-127">Team</span></span> |
| <span data-ttu-id="32f3c-128">canal renomeado</span><span class="sxs-lookup"><span data-stu-id="32f3c-128">channel renamed</span></span>     | <span data-ttu-id="32f3c-129">channelRenamed</span><span class="sxs-lookup"><span data-stu-id="32f3c-129">channelRenamed</span></span>    | <span data-ttu-id="32f3c-130">OnTeamsChannelRenamedAsync</span><span class="sxs-lookup"><span data-stu-id="32f3c-130">OnTeamsChannelRenamedAsync</span></span> | [<span data-ttu-id="32f3c-131">Um canal foi renomeado</span><span class="sxs-lookup"><span data-stu-id="32f3c-131">A channel was renamed</span></span>](#channel-renamed) | <span data-ttu-id="32f3c-132">Equipe</span><span class="sxs-lookup"><span data-stu-id="32f3c-132">Team</span></span> |
| <span data-ttu-id="32f3c-133">canal excluído</span><span class="sxs-lookup"><span data-stu-id="32f3c-133">channel deleted</span></span>     | <span data-ttu-id="32f3c-134">channelDeleted</span><span class="sxs-lookup"><span data-stu-id="32f3c-134">channelDeleted</span></span>    | <span data-ttu-id="32f3c-135">OnTeamsChannelDeletedAsync</span><span class="sxs-lookup"><span data-stu-id="32f3c-135">OnTeamsChannelDeletedAsync</span></span> | [<span data-ttu-id="32f3c-136">Um canal foi excluído</span><span class="sxs-lookup"><span data-stu-id="32f3c-136">A channel was deleted</span></span>](#channel-deleted) | <span data-ttu-id="32f3c-137">Equipe</span><span class="sxs-lookup"><span data-stu-id="32f3c-137">Team</span></span> |
| <span data-ttu-id="32f3c-138">canal restaurado</span><span class="sxs-lookup"><span data-stu-id="32f3c-138">channel restored</span></span>    | <span data-ttu-id="32f3c-139">channelRestored</span><span class="sxs-lookup"><span data-stu-id="32f3c-139">channelRestored</span></span>    | <span data-ttu-id="32f3c-140">OnTeamsChannelRestoredAsync</span><span class="sxs-lookup"><span data-stu-id="32f3c-140">OnTeamsChannelRestoredAsync</span></span> | [<span data-ttu-id="32f3c-141">Um canal foi restaurado</span><span class="sxs-lookup"><span data-stu-id="32f3c-141">A channel was restored</span></span>](#channel-deleted) | <span data-ttu-id="32f3c-142">Equipe</span><span class="sxs-lookup"><span data-stu-id="32f3c-142">Team</span></span> |
| <span data-ttu-id="32f3c-143">members added</span><span class="sxs-lookup"><span data-stu-id="32f3c-143">members added</span></span>   | <span data-ttu-id="32f3c-144">membersAdded</span><span class="sxs-lookup"><span data-stu-id="32f3c-144">membersAdded</span></span>   | <span data-ttu-id="32f3c-145">OnTeamsMembersAddedAsync</span><span class="sxs-lookup"><span data-stu-id="32f3c-145">OnTeamsMembersAddedAsync</span></span>   | [<span data-ttu-id="32f3c-146">Um membro adicionado</span><span class="sxs-lookup"><span data-stu-id="32f3c-146">A member added</span></span>](#team-members-added)   | <span data-ttu-id="32f3c-147">Todos</span><span class="sxs-lookup"><span data-stu-id="32f3c-147">All</span></span> |
| <span data-ttu-id="32f3c-148">membros removidos</span><span class="sxs-lookup"><span data-stu-id="32f3c-148">members removed</span></span> | <span data-ttu-id="32f3c-149">membersRemoved</span><span class="sxs-lookup"><span data-stu-id="32f3c-149">membersRemoved</span></span> | <span data-ttu-id="32f3c-150">OnTeamsMembersRemovedAsync</span><span class="sxs-lookup"><span data-stu-id="32f3c-150">OnTeamsMembersRemovedAsync</span></span> | [<span data-ttu-id="32f3c-151">Um membro foi removido</span><span class="sxs-lookup"><span data-stu-id="32f3c-151">A member was removed</span></span>](#team-members-removed) | <span data-ttu-id="32f3c-152">groupChat & equipe</span><span class="sxs-lookup"><span data-stu-id="32f3c-152">groupChat & team</span></span> |
| <span data-ttu-id="32f3c-153">equipe renomeada</span><span class="sxs-lookup"><span data-stu-id="32f3c-153">team renamed</span></span>        | <span data-ttu-id="32f3c-154">teamRenamed</span><span class="sxs-lookup"><span data-stu-id="32f3c-154">teamRenamed</span></span>       | <span data-ttu-id="32f3c-155">OnTeamsTeamRenamedAsync</span><span class="sxs-lookup"><span data-stu-id="32f3c-155">OnTeamsTeamRenamedAsync</span></span>    | [<span data-ttu-id="32f3c-156">Uma equipe foi renomeada</span><span class="sxs-lookup"><span data-stu-id="32f3c-156">A Team was renamed</span></span>](#team-renamed)       | <span data-ttu-id="32f3c-157">Equipe</span><span class="sxs-lookup"><span data-stu-id="32f3c-157">Team</span></span> |
| <span data-ttu-id="32f3c-158">equipe excluída</span><span class="sxs-lookup"><span data-stu-id="32f3c-158">team deleted</span></span>        | <span data-ttu-id="32f3c-159">teamDeleted</span><span class="sxs-lookup"><span data-stu-id="32f3c-159">teamDeleted</span></span>       | <span data-ttu-id="32f3c-160">OnTeamsTeamDeletedAsync</span><span class="sxs-lookup"><span data-stu-id="32f3c-160">OnTeamsTeamDeletedAsync</span></span>    | [<span data-ttu-id="32f3c-161">Uma equipe foi excluída</span><span class="sxs-lookup"><span data-stu-id="32f3c-161">A Team was deleted</span></span>](#team-deleted)       | <span data-ttu-id="32f3c-162">Equipe</span><span class="sxs-lookup"><span data-stu-id="32f3c-162">Team</span></span> |
| <span data-ttu-id="32f3c-163">equipe arquivada</span><span class="sxs-lookup"><span data-stu-id="32f3c-163">team archived</span></span>        | <span data-ttu-id="32f3c-164">teamArchived</span><span class="sxs-lookup"><span data-stu-id="32f3c-164">teamArchived</span></span>       | <span data-ttu-id="32f3c-165">OnTeamsTeamArchivedAsync</span><span class="sxs-lookup"><span data-stu-id="32f3c-165">OnTeamsTeamArchivedAsync</span></span>    | [<span data-ttu-id="32f3c-166">Uma equipe foi arquivada</span><span class="sxs-lookup"><span data-stu-id="32f3c-166">A Team was archived</span></span>](#team-archived)       | <span data-ttu-id="32f3c-167">Equipe</span><span class="sxs-lookup"><span data-stu-id="32f3c-167">Team</span></span> |
| <span data-ttu-id="32f3c-168">equipe desarquivada</span><span class="sxs-lookup"><span data-stu-id="32f3c-168">team unarchived</span></span>        | <span data-ttu-id="32f3c-169">teamUnarchived</span><span class="sxs-lookup"><span data-stu-id="32f3c-169">teamUnarchived</span></span>       | <span data-ttu-id="32f3c-170">OnTeamsTeamUnarchivedAsync</span><span class="sxs-lookup"><span data-stu-id="32f3c-170">OnTeamsTeamUnarchivedAsync</span></span>    | [<span data-ttu-id="32f3c-171">Uma equipe foi desarquivada</span><span class="sxs-lookup"><span data-stu-id="32f3c-171">A Team was unarchived</span></span>](#team-unarchived)       | <span data-ttu-id="32f3c-172">Equipe</span><span class="sxs-lookup"><span data-stu-id="32f3c-172">Team</span></span> |
| <span data-ttu-id="32f3c-173">equipe restaurada</span><span class="sxs-lookup"><span data-stu-id="32f3c-173">team restored</span></span>        | <span data-ttu-id="32f3c-174">teamRestored</span><span class="sxs-lookup"><span data-stu-id="32f3c-174">teamRestored</span></span>      | <span data-ttu-id="32f3c-175">OnTeamsTeamRestoredAsync</span><span class="sxs-lookup"><span data-stu-id="32f3c-175">OnTeamsTeamRestoredAsync</span></span>    | [<span data-ttu-id="32f3c-176">Uma equipe foi restaurada</span><span class="sxs-lookup"><span data-stu-id="32f3c-176">A Team was restored</span></span>](#team-restored)       | <span data-ttu-id="32f3c-177">Equipe</span><span class="sxs-lookup"><span data-stu-id="32f3c-177">Team</span></span> |

### <a name="channel-created"></a><span data-ttu-id="32f3c-178">Canal criado</span><span class="sxs-lookup"><span data-stu-id="32f3c-178">Channel created</span></span>

<span data-ttu-id="32f3c-179">O evento de criação do canal é enviado ao seu bot sempre que um novo canal é criado em uma equipe em que o bot está instalado.</span><span class="sxs-lookup"><span data-stu-id="32f3c-179">The channel created event is sent to your bot whenever a new channel is created in a team your bot is installed in.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="32f3c-180">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="32f3c-180">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelCreatedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the Channel created");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="32f3c-181">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="32f3c-181">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="32f3c-182">JSON</span><span class="sxs-lookup"><span data-stu-id="32f3c-182">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="32f3c-183">Python</span><span class="sxs-lookup"><span data-stu-id="32f3c-183">Python</span></span>](#tab/python)

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

### <a name="channel-renamed"></a><span data-ttu-id="32f3c-184">Canal renomeado</span><span class="sxs-lookup"><span data-stu-id="32f3c-184">Channel renamed</span></span>

<span data-ttu-id="32f3c-185">O evento renomeado do canal é enviado para seu bot sempre que um canal é renomeado em uma equipe em que seu bot está instalado.</span><span class="sxs-lookup"><span data-stu-id="32f3c-185">The channel renamed event is sent to your bot whenever a channel is renamed in a team your bot is installed in.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="32f3c-186">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="32f3c-186">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelRenamedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the new Channel name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="32f3c-187">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="32f3c-187">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="32f3c-188">JSON</span><span class="sxs-lookup"><span data-stu-id="32f3c-188">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="32f3c-189">Python</span><span class="sxs-lookup"><span data-stu-id="32f3c-189">Python</span></span>](#tab/python)

```python
async def on_teams_channel_renamed(
    self, channel_info: ChannelInfo, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The new channel name is {channel_info.name}")
    )
```

* * *

### <a name="channel-deleted"></a><span data-ttu-id="32f3c-190">Canal Excluído</span><span class="sxs-lookup"><span data-stu-id="32f3c-190">Channel Deleted</span></span>

<span data-ttu-id="32f3c-191">O evento excluído do canal é enviado ao seu bot sempre que um canal é excluído em uma equipe em que seu bot está instalado.</span><span class="sxs-lookup"><span data-stu-id="32f3c-191">The channel deleted event is sent to your bot whenever a channel is deleted in a team your bot is installed in.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="32f3c-192">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="32f3c-192">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelDeletedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the Channel deleted");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="32f3c-193">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="32f3c-193">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="32f3c-194">JSON</span><span class="sxs-lookup"><span data-stu-id="32f3c-194">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="32f3c-195">Python</span><span class="sxs-lookup"><span data-stu-id="32f3c-195">Python</span></span>](#tab/python)

```python
async def on_teams_channel_deleted(
    self, channel_info: ChannelInfo, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The deleted channel is {channel_info.name}")
    )
```

* * *

### <a name="channel-restored"></a><span data-ttu-id="32f3c-196">Canal restaurado</span><span class="sxs-lookup"><span data-stu-id="32f3c-196">Channel restored</span></span>

<span data-ttu-id="32f3c-197">O evento restaurado do canal é enviado para o bot sempre que um canal excluído anteriormente é restaurado em uma equipe em que o bot já está instalado.</span><span class="sxs-lookup"><span data-stu-id="32f3c-197">The channel restored event is sent to your bot whenever a channel that was previously deleted is restored in a team that your bot is already installed in.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="32f3c-198">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="32f3c-198">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelRestoredAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the Channel restored.");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="32f3c-199">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="32f3c-199">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="32f3c-200">JSON</span><span class="sxs-lookup"><span data-stu-id="32f3c-200">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="32f3c-201">Python</span><span class="sxs-lookup"><span data-stu-id="32f3c-201">Python</span></span>](#tab/python)

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

### <a name="team-members-added"></a><span data-ttu-id="32f3c-202">Membros da equipe adicionados</span><span class="sxs-lookup"><span data-stu-id="32f3c-202">Team members added</span></span>

<span data-ttu-id="32f3c-203">O evento é enviado ao seu bot na primeira vez em que é adicionado a uma conversa e sempre que um novo usuário é adicionado a uma equipe ou chat de grupo em que seu `teamMemberAdded` bot está instalado.</span><span class="sxs-lookup"><span data-stu-id="32f3c-203">The `teamMemberAdded` event is sent to your bot the first time it is added to a conversation and every time a new user is added to a team or group chat that your bot is installed in.</span></span> <span data-ttu-id="32f3c-204">As informações do usuário (ID) são exclusivas para seu bot e podem ser armazenadas em cache para uso futuro pelo serviço (como enviar uma mensagem para um usuário específico).</span><span class="sxs-lookup"><span data-stu-id="32f3c-204">The user information (ID) is unique for your bot and can be cached for future use by your service (such as sending a message to a specific user).</span></span>

# <a name="cnet"></a>[<span data-ttu-id="32f3c-205">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="32f3c-205">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="32f3c-206">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="32f3c-206">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="32f3c-207">JSON</span><span class="sxs-lookup"><span data-stu-id="32f3c-207">JSON</span></span>](#tab/json)

<span data-ttu-id="32f3c-208">Esta é a mensagem que seu bot receberá quando o bot for adicionado **a uma equipe.**</span><span class="sxs-lookup"><span data-stu-id="32f3c-208">This is the message your bot will receive when the bot is added **to a team**.</span></span>

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

<span data-ttu-id="32f3c-209">Esta é a mensagem que seu bot receberá quando o bot for adicionado \* a um *chat um-para-um.*</span><span class="sxs-lookup"><span data-stu-id="32f3c-209">This is the message your bot will receive when the bot is added \**to a one-to-one chat*.</span></span>

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
    "aadObjectId": "**_"
  },
  "conversation": {
    "conversationType": "personal",
    "id": "_*_"
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

# <a name="python"></a>[<span data-ttu-id="32f3c-210">Python</span><span class="sxs-lookup"><span data-stu-id="32f3c-210">Python</span></span>](#tab/python)

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

<span data-ttu-id="32f3c-211">_ \* \*</span><span class="sxs-lookup"><span data-stu-id="32f3c-211">_ \* \*</span></span>

### <a name="team-members-removed"></a><span data-ttu-id="32f3c-212">Membros da equipe removidos</span><span class="sxs-lookup"><span data-stu-id="32f3c-212">Team members removed</span></span>

<span data-ttu-id="32f3c-213">O evento é enviado para seu bot se ele for removido de uma equipe e sempre que qualquer usuário for removido de uma equipe da que seu `teamMemberRemoved` bot é membro.</span><span class="sxs-lookup"><span data-stu-id="32f3c-213">The `teamMemberRemoved` event is sent to your bot if it is removed from a team and every time any user is removed from a team that your bot is a member of.</span></span> <span data-ttu-id="32f3c-214">Você pode determinar se o novo membro removido foi o próprio bot ou um usuário observando o `Activity` objeto do `turnContext` .</span><span class="sxs-lookup"><span data-stu-id="32f3c-214">You can determine if the new member removed was the bot itself or a user by looking at the `Activity` object of the `turnContext`.</span></span>  <span data-ttu-id="32f3c-215">Se o campo do objeto for o mesmo que o campo do objeto, o membro removido será o bot; caso `Id` `MembersRemoved` `Id` `Recipient` contrário, será um usuário.</span><span class="sxs-lookup"><span data-stu-id="32f3c-215">If the `Id` field of the `MembersRemoved` object is the same as the `Id` field of the `Recipient` object, then the member removed is the bot, otherwise, it is a user.</span></span>  <span data-ttu-id="32f3c-216">O bot geralmente `Id` será: `28:<MicrosoftAppId>`</span><span class="sxs-lookup"><span data-stu-id="32f3c-216">The bot's `Id` will generally be: `28:<MicrosoftAppId>`</span></span>

[!Note] <span data-ttu-id="32f3c-217">Quando um usuário é excluído permanentemente de um locatário, `membersRemoved conversationUpdate` o evento é acionado.</span><span class="sxs-lookup"><span data-stu-id="32f3c-217">When a user is permanently deleted from a tenant, `membersRemoved conversationUpdate` event is triggered.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="32f3c-218">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="32f3c-218">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="32f3c-219">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="32f3c-219">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="32f3c-220">JSON</span><span class="sxs-lookup"><span data-stu-id="32f3c-220">JSON</span></span>](#tab/json)

<span data-ttu-id="32f3c-221">O objeto no exemplo de carga a seguir baseia-se em adicionar um membro a uma equipe em vez de um chat em grupo ou iniciar uma nova conversa `channelData` um-para-um:</span><span class="sxs-lookup"><span data-stu-id="32f3c-221">The `channelData` object in the following payload example is based on adding a member to a team rather than a group chat, or initiating a new one-to-one conversation:</span></span>

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


# <a name="python"></a>[<span data-ttu-id="32f3c-222">Python</span><span class="sxs-lookup"><span data-stu-id="32f3c-222">Python</span></span>](#tab/python)

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

### <a name="team-renamed"></a><span data-ttu-id="32f3c-223">Equipe renomeada</span><span class="sxs-lookup"><span data-stu-id="32f3c-223">Team renamed</span></span>

<span data-ttu-id="32f3c-224">Seu bot é notificado quando a equipe em que está foi renomeada.</span><span class="sxs-lookup"><span data-stu-id="32f3c-224">Your bot is notified when the team it is in has been renamed.</span></span> <span data-ttu-id="32f3c-225">Ele recebe um `conversationUpdate` evento `eventType.teamRenamed` com no `channelData` objeto.</span><span class="sxs-lookup"><span data-stu-id="32f3c-225">It receives a `conversationUpdate` event with `eventType.teamRenamed` in the `channelData` object.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="32f3c-226">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="32f3c-226">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamRenamedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the new Team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="32f3c-227">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="32f3c-227">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="32f3c-228">JSON</span><span class="sxs-lookup"><span data-stu-id="32f3c-228">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="32f3c-229">Python</span><span class="sxs-lookup"><span data-stu-id="32f3c-229">Python</span></span>](#tab/python)

```python
async def on_teams_team_renamed(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The new team name is {team_info.name}")
    )
```

* * *

### <a name="team-deleted"></a><span data-ttu-id="32f3c-230">Equipe excluída</span><span class="sxs-lookup"><span data-stu-id="32f3c-230">Team deleted</span></span>

<span data-ttu-id="32f3c-231">Seu bot é notificado quando a equipe em que está foi excluída.</span><span class="sxs-lookup"><span data-stu-id="32f3c-231">Your bot is notified when the team it is in has been deleted.</span></span> <span data-ttu-id="32f3c-232">Ele recebe um `conversationUpdate` evento com `eventType.teamDeleted` no `channelData` objeto.</span><span class="sxs-lookup"><span data-stu-id="32f3c-232">It receives a `conversationUpdate` event with `eventType.teamDeleted` in the `channelData` object.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="32f3c-233">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="32f3c-233">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamDeletedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    //handle delete event
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="32f3c-234">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="32f3c-234">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="32f3c-235">JSON</span><span class="sxs-lookup"><span data-stu-id="32f3c-235">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="32f3c-236">Python</span><span class="sxs-lookup"><span data-stu-id="32f3c-236">Python</span></span>](#tab/python)

```python
async def on_teams_team_deleted(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    //handle delete event
    )
```

* * *

### <a name="team-restored"></a><span data-ttu-id="32f3c-237">Equipe restaurada</span><span class="sxs-lookup"><span data-stu-id="32f3c-237">Team restored</span></span>

<span data-ttu-id="32f3c-238">O bot recebe uma notificação quando é restaurado da exclusão.</span><span class="sxs-lookup"><span data-stu-id="32f3c-238">The bot receives a notification when it is restored from deletion.</span></span> <span data-ttu-id="32f3c-239">Ele recebe um `conversationUpdate` evento `eventType.teamrestored` com no `channelData` objeto.</span><span class="sxs-lookup"><span data-stu-id="32f3c-239">It receives a `conversationUpdate` event with `eventType.teamrestored` in the `channelData` object.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="32f3c-240">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="32f3c-240">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamrestoredAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="32f3c-241">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="32f3c-241">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="32f3c-242">JSON</span><span class="sxs-lookup"><span data-stu-id="32f3c-242">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="32f3c-243">Python</span><span class="sxs-lookup"><span data-stu-id="32f3c-243">Python</span></span>](#tab/python)

```python
async def on_teams_team_restored(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The team name is {team_info.name}")
    )
```

* * *

### <a name="team-archived"></a><span data-ttu-id="32f3c-244">Equipe arquivada</span><span class="sxs-lookup"><span data-stu-id="32f3c-244">Team archived</span></span>

<span data-ttu-id="32f3c-245">O bot recebe uma notificação quando a equipe em que está instalado é arquivada.</span><span class="sxs-lookup"><span data-stu-id="32f3c-245">The bot receives a notification when the team it is installed in is archived.</span></span> <span data-ttu-id="32f3c-246">Ele recebe um `conversationUpdate` evento `eventType.teamarchived` com no `channelData` objeto.</span><span class="sxs-lookup"><span data-stu-id="32f3c-246">It receives a `conversationUpdate` event with `eventType.teamarchived` in the `channelData` object.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="32f3c-247">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="32f3c-247">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamArchivedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="32f3c-248">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="32f3c-248">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="32f3c-249">JSON</span><span class="sxs-lookup"><span data-stu-id="32f3c-249">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="32f3c-250">Python</span><span class="sxs-lookup"><span data-stu-id="32f3c-250">Python</span></span>](#tab/python)

```python
async def on_teams_team_archived(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The team name is {team_info.name}")
    )
```

* * *


### <a name="team-unarchived"></a><span data-ttu-id="32f3c-251">Equipe desarquivada</span><span class="sxs-lookup"><span data-stu-id="32f3c-251">Team unarchived</span></span>

<span data-ttu-id="32f3c-252">O bot recebe uma notificação quando a equipe em que está instalado está desarquivada.</span><span class="sxs-lookup"><span data-stu-id="32f3c-252">The bot receives a notification when the team it is installed in is unarchived.</span></span> <span data-ttu-id="32f3c-253">Ele recebe um `conversationUpdate` evento `eventType.teamUnarchived` com no `channelData` objeto.</span><span class="sxs-lookup"><span data-stu-id="32f3c-253">It receives a `conversationUpdate` event with `eventType.teamUnarchived` in the `channelData` object.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="32f3c-254">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="32f3c-254">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamUnarchivedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="32f3c-255">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="32f3c-255">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="32f3c-256">JSON</span><span class="sxs-lookup"><span data-stu-id="32f3c-256">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="32f3c-257">Python</span><span class="sxs-lookup"><span data-stu-id="32f3c-257">Python</span></span>](#tab/python)

```python
async def on_teams_team_unarchived(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The team name is {team_info.name}")
    )
```

* * *

## <a name="message-reaction-events"></a><span data-ttu-id="32f3c-258">Eventos de reação de mensagem</span><span class="sxs-lookup"><span data-stu-id="32f3c-258">Message reaction events</span></span>

<span data-ttu-id="32f3c-259">O `messageReaction` evento é enviado quando um usuário adiciona ou remove reações a uma mensagem que foi enviada por seu bot.</span><span class="sxs-lookup"><span data-stu-id="32f3c-259">The `messageReaction` event is sent when a user adds or removes reactions to a message which was sent by your bot.</span></span> <span data-ttu-id="32f3c-260">Contém a ID da mensagem específica e o tipo de reação no `replyToId` `Type` formato de texto.</span><span class="sxs-lookup"><span data-stu-id="32f3c-260">The `replyToId` contains the ID of the specific message, and the `Type` is the type of reaction in text format.</span></span>  <span data-ttu-id="32f3c-261">Os tipos de reações incluem: "saúde", "coração", "insupo", "like", "Infelizmente", "surpresa".</span><span class="sxs-lookup"><span data-stu-id="32f3c-261">The types of reactions include: "angry", "heart", "laugh", "like", "Sad", "surprised".</span></span> <span data-ttu-id="32f3c-262">Esse evento não contém o conteúdo da mensagem original, portanto, se o processamento de reações às suas mensagens for importante para seu bot, você precisará armazenar as mensagens quando enviá-las.</span><span class="sxs-lookup"><span data-stu-id="32f3c-262">This event does not contain the contents of the original message, so if processing reactions to your messages is important for your bot you'll need to store the messages when you send them.</span></span>

| <span data-ttu-id="32f3c-263">EventType</span><span class="sxs-lookup"><span data-stu-id="32f3c-263">EventType</span></span>       | <span data-ttu-id="32f3c-264">Objeto Payload</span><span class="sxs-lookup"><span data-stu-id="32f3c-264">Payload object</span></span>   | <span data-ttu-id="32f3c-265">Descrição</span><span class="sxs-lookup"><span data-stu-id="32f3c-265">Description</span></span>                                                             | <span data-ttu-id="32f3c-266">Escopo</span><span class="sxs-lookup"><span data-stu-id="32f3c-266">Scope</span></span> |
| --------------- | ---------------- | ----------------------------------------------------------------------- | ----- |
| <span data-ttu-id="32f3c-267">messageReaction</span><span class="sxs-lookup"><span data-stu-id="32f3c-267">messageReaction</span></span> | <span data-ttu-id="32f3c-268">reactionsAdded</span><span class="sxs-lookup"><span data-stu-id="32f3c-268">reactionsAdded</span></span>   | [<span data-ttu-id="32f3c-269">Reação à mensagem de bot</span><span class="sxs-lookup"><span data-stu-id="32f3c-269">Reaction to bot message</span></span>](#reactions-to-a-bot-message)                   | <span data-ttu-id="32f3c-270">Todos</span><span class="sxs-lookup"><span data-stu-id="32f3c-270">All</span></span>   |
| <span data-ttu-id="32f3c-271">messageReaction</span><span class="sxs-lookup"><span data-stu-id="32f3c-271">messageReaction</span></span> | <span data-ttu-id="32f3c-272">reactionsRemoved</span><span class="sxs-lookup"><span data-stu-id="32f3c-272">reactionsRemoved</span></span> | [<span data-ttu-id="32f3c-273">Reação removida da mensagem de bot</span><span class="sxs-lookup"><span data-stu-id="32f3c-273">Reaction removed from bot message</span></span>](#reactions-removed-from-bot-message) | <span data-ttu-id="32f3c-274">Todos</span><span class="sxs-lookup"><span data-stu-id="32f3c-274">All</span></span>   |

### <a name="reactions-to-a-bot-message"></a><span data-ttu-id="32f3c-275">Reações a uma mensagem de bot</span><span class="sxs-lookup"><span data-stu-id="32f3c-275">Reactions to a bot message</span></span>

# <a name="cnet"></a>[<span data-ttu-id="32f3c-276">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="32f3c-276">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="32f3c-277">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="32f3c-277">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="32f3c-278">JSON</span><span class="sxs-lookup"><span data-stu-id="32f3c-278">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="32f3c-279">Python</span><span class="sxs-lookup"><span data-stu-id="32f3c-279">Python</span></span>](#tab/python)

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

### <a name="reactions-removed-from-bot-message"></a><span data-ttu-id="32f3c-280">Reações removidas da mensagem de bot</span><span class="sxs-lookup"><span data-stu-id="32f3c-280">Reactions removed from bot message</span></span>

# <a name="cnet"></a>[<span data-ttu-id="32f3c-281">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="32f3c-281">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="32f3c-282">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="32f3c-282">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="32f3c-283">JSON</span><span class="sxs-lookup"><span data-stu-id="32f3c-283">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="32f3c-284">Python</span><span class="sxs-lookup"><span data-stu-id="32f3c-284">Python</span></span>](#tab/python)

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

## <a name="samples"></a><span data-ttu-id="32f3c-285">Exemplos</span><span class="sxs-lookup"><span data-stu-id="32f3c-285">Samples</span></span>
<span data-ttu-id="32f3c-286">Para código de exemplo mostrando os eventos de conversa de bots, confira:</span><span class="sxs-lookup"><span data-stu-id="32f3c-286">For sample code showing the bots conversation events, see:</span></span>

[<span data-ttu-id="32f3c-287">Exemplo de eventos de conversa de bots do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="32f3c-287">Microsoft Teams bots conversation events sample</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot)



