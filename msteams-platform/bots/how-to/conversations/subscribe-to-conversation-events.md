---
title: Eventos de conversa
author: WashingtonKayaker
description: Como trabalhar com eventos de conversa do seu bot do Microsoft Teams.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: af06dba58b3784a03dbcbbc627fa38fce681eeb8
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696343"
---
# <a name="conversation-events-in-your-teams-bot"></a><span data-ttu-id="3a975-103">Eventos de conversa no bot do Teams</span><span class="sxs-lookup"><span data-stu-id="3a975-103">Conversation events in your Teams bot</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="3a975-104">Ao criar seus bots de conversa para o Microsoft Teams, você pode trabalhar com eventos de conversa.</span><span class="sxs-lookup"><span data-stu-id="3a975-104">When building your conversational bots for Microsoft Teams, you can work with conversation events.</span></span> <span data-ttu-id="3a975-105">O Teams envia notificações ao bot para eventos de conversa que ocorrem em escopos onde o bot está ativo.</span><span class="sxs-lookup"><span data-stu-id="3a975-105">Teams sends notifications to your bot for conversation events that happen in scopes where your bot is active.</span></span> <span data-ttu-id="3a975-106">Você pode capturar esses eventos em seu código e tomar as seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="3a975-106">You can capture these events in your code and take the following actions:</span></span>

* <span data-ttu-id="3a975-107">Acionar uma mensagem de boas-vindas quando seu bot for adicionado a uma equipe.</span><span class="sxs-lookup"><span data-stu-id="3a975-107">Trigger a welcome message when your bot is added to a team.</span></span>
* <span data-ttu-id="3a975-108">Acionar uma mensagem de boas-vindas quando um novo membro da equipe for adicionado ou removido.</span><span class="sxs-lookup"><span data-stu-id="3a975-108">Trigger a welcome message when a new team member is added or removed.</span></span>
* <span data-ttu-id="3a975-109">Acionar uma notificação quando um canal for criado, renomeado ou excluído.</span><span class="sxs-lookup"><span data-stu-id="3a975-109">Trigger a notification when a channel is created, renamed, or deleted.</span></span>
* <span data-ttu-id="3a975-110">Quando uma mensagem bot é curtida por um usuário.</span><span class="sxs-lookup"><span data-stu-id="3a975-110">When a bot message is liked by a user.</span></span>

## <a name="conversation-update-events"></a><span data-ttu-id="3a975-111">Eventos de atualização de conversa</span><span class="sxs-lookup"><span data-stu-id="3a975-111">Conversation update events</span></span>

<span data-ttu-id="3a975-112">Você pode usar eventos de atualização de conversa para fornecer notificações melhores e ações de bot mais eficazes.</span><span class="sxs-lookup"><span data-stu-id="3a975-112">You can use conversation update events to provide better notifications and more effective bot actions.</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="3a975-113">Você pode adicionar novos eventos a qualquer momento e seu bot começa a recebê-los.</span><span class="sxs-lookup"><span data-stu-id="3a975-113">You can add new events any time and your bot begins to receive them.</span></span>
> * <span data-ttu-id="3a975-114">Você deve projetar seu bot para receber eventos inesperados.</span><span class="sxs-lookup"><span data-stu-id="3a975-114">You must design your bot to receive unexpected events.</span></span>
> * <span data-ttu-id="3a975-115">Se você estiver usando o SDK da Estrutura de Bots, seu bot responderá automaticamente com um a quaisquer `200 - OK` eventos que você escolher não manipular.</span><span class="sxs-lookup"><span data-stu-id="3a975-115">If you are using the Bot Framework SDK, your bot automatically responds with a `200 - OK` to any events you choose not to handle.</span></span>

<span data-ttu-id="3a975-116">Um bot recebe um `conversationUpdate` evento em um dos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="3a975-116">A bot receives a `conversationUpdate` event in either of the following cases:</span></span>

* <span data-ttu-id="3a975-117">Quando o bot foi adicionado a uma conversa.</span><span class="sxs-lookup"><span data-stu-id="3a975-117">When bot has been added to a conversation.</span></span>
* <span data-ttu-id="3a975-118">Outros membros são adicionados ou removidos de uma conversa.</span><span class="sxs-lookup"><span data-stu-id="3a975-118">Other members are added to or removed from a conversation.</span></span>
* <span data-ttu-id="3a975-119">Os metadados de conversa foram alterados.</span><span class="sxs-lookup"><span data-stu-id="3a975-119">Conversation metadata has changed.</span></span>

<span data-ttu-id="3a975-120">O evento `conversationUpdate` é enviado ao seu bot quando ele recebe informações sobre atualizações de membros para as equipes onde foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="3a975-120">The `conversationUpdate` event is sent to your bot when it receives information on membership updates for teams where it has been added.</span></span> <span data-ttu-id="3a975-121">Ele também recebe uma atualização quando foi adicionada pela primeira vez para conversas pessoais.</span><span class="sxs-lookup"><span data-stu-id="3a975-121">It also receives an update when it has been added for the first time for personal conversations.</span></span>

<span data-ttu-id="3a975-122">A tabela a seguir mostra uma lista de eventos de atualização de conversa do Teams com mais detalhes:</span><span class="sxs-lookup"><span data-stu-id="3a975-122">The following table shows a list of Teams conversation update events with more details:</span></span>

| <span data-ttu-id="3a975-123">Ação tomada</span><span class="sxs-lookup"><span data-stu-id="3a975-123">Action taken</span></span>        | <span data-ttu-id="3a975-124">EventType</span><span class="sxs-lookup"><span data-stu-id="3a975-124">EventType</span></span>         | <span data-ttu-id="3a975-125">Método chamado</span><span class="sxs-lookup"><span data-stu-id="3a975-125">Method called</span></span>              | <span data-ttu-id="3a975-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a975-126">Description</span></span>                | <span data-ttu-id="3a975-127">Escopo</span><span class="sxs-lookup"><span data-stu-id="3a975-127">Scope</span></span> |
| ------------------- | ----------------- | -------------------------- | -------------------------- | ----- |
| <span data-ttu-id="3a975-128">Canal criado</span><span class="sxs-lookup"><span data-stu-id="3a975-128">Channel created</span></span>     | <span data-ttu-id="3a975-129">channelCreated</span><span class="sxs-lookup"><span data-stu-id="3a975-129">channelCreated</span></span>    | <span data-ttu-id="3a975-130">OnTeamsChannelCreatedAsync</span><span class="sxs-lookup"><span data-stu-id="3a975-130">OnTeamsChannelCreatedAsync</span></span> | <span data-ttu-id="3a975-131">[Um canal é criado](#channel-created).</span><span class="sxs-lookup"><span data-stu-id="3a975-131">[A channel is created](#channel-created).</span></span> | <span data-ttu-id="3a975-132">Equipe</span><span class="sxs-lookup"><span data-stu-id="3a975-132">Team</span></span> |
| <span data-ttu-id="3a975-133">Canal renomeado</span><span class="sxs-lookup"><span data-stu-id="3a975-133">Channel renamed</span></span>     | <span data-ttu-id="3a975-134">channelRenamed</span><span class="sxs-lookup"><span data-stu-id="3a975-134">channelRenamed</span></span>    | <span data-ttu-id="3a975-135">OnTeamsChannelRenamedAsync</span><span class="sxs-lookup"><span data-stu-id="3a975-135">OnTeamsChannelRenamedAsync</span></span> | <span data-ttu-id="3a975-136">[Um canal é renomeado](#channel-renamed).</span><span class="sxs-lookup"><span data-stu-id="3a975-136">[A channel is renamed](#channel-renamed).</span></span> | <span data-ttu-id="3a975-137">Equipe</span><span class="sxs-lookup"><span data-stu-id="3a975-137">Team</span></span> |
| <span data-ttu-id="3a975-138">Canal excluído</span><span class="sxs-lookup"><span data-stu-id="3a975-138">Channel deleted</span></span>     | <span data-ttu-id="3a975-139">channelDeleted</span><span class="sxs-lookup"><span data-stu-id="3a975-139">channelDeleted</span></span>    | <span data-ttu-id="3a975-140">OnTeamsChannelDeletedAsync</span><span class="sxs-lookup"><span data-stu-id="3a975-140">OnTeamsChannelDeletedAsync</span></span> | <span data-ttu-id="3a975-141">[Um canal é excluído](#channel-deleted).</span><span class="sxs-lookup"><span data-stu-id="3a975-141">[A channel is deleted](#channel-deleted).</span></span> | <span data-ttu-id="3a975-142">Equipe</span><span class="sxs-lookup"><span data-stu-id="3a975-142">Team</span></span> |
| <span data-ttu-id="3a975-143">Canal restaurado</span><span class="sxs-lookup"><span data-stu-id="3a975-143">Channel restored</span></span>    | <span data-ttu-id="3a975-144">channelRestored</span><span class="sxs-lookup"><span data-stu-id="3a975-144">channelRestored</span></span>    | <span data-ttu-id="3a975-145">OnTeamsChannelRestoredAsync</span><span class="sxs-lookup"><span data-stu-id="3a975-145">OnTeamsChannelRestoredAsync</span></span> | <span data-ttu-id="3a975-146">[Um canal é restaurado](#channel-deleted).</span><span class="sxs-lookup"><span data-stu-id="3a975-146">[A channel is restored](#channel-deleted).</span></span> | <span data-ttu-id="3a975-147">Equipe</span><span class="sxs-lookup"><span data-stu-id="3a975-147">Team</span></span> |
| <span data-ttu-id="3a975-148">Membros adicionados</span><span class="sxs-lookup"><span data-stu-id="3a975-148">Members added</span></span>   | <span data-ttu-id="3a975-149">membersAdded</span><span class="sxs-lookup"><span data-stu-id="3a975-149">membersAdded</span></span>   | <span data-ttu-id="3a975-150">OnTeamsMembersAddedAsync</span><span class="sxs-lookup"><span data-stu-id="3a975-150">OnTeamsMembersAddedAsync</span></span>   | <span data-ttu-id="3a975-151">[Um membro é adicionado](#team-members-added).</span><span class="sxs-lookup"><span data-stu-id="3a975-151">[A member is added](#team-members-added).</span></span> | <span data-ttu-id="3a975-152">Todos</span><span class="sxs-lookup"><span data-stu-id="3a975-152">All</span></span> |
| <span data-ttu-id="3a975-153">Membros removidos</span><span class="sxs-lookup"><span data-stu-id="3a975-153">Members removed</span></span> | <span data-ttu-id="3a975-154">membersRemoved</span><span class="sxs-lookup"><span data-stu-id="3a975-154">membersRemoved</span></span> | <span data-ttu-id="3a975-155">OnTeamsMembersRemovedAsync</span><span class="sxs-lookup"><span data-stu-id="3a975-155">OnTeamsMembersRemovedAsync</span></span> | <span data-ttu-id="3a975-156">[Um membro é removido](#team-members-removed).</span><span class="sxs-lookup"><span data-stu-id="3a975-156">[A member is removed](#team-members-removed).</span></span> | <span data-ttu-id="3a975-157">groupChat e team</span><span class="sxs-lookup"><span data-stu-id="3a975-157">groupChat and team</span></span> |
| <span data-ttu-id="3a975-158">Equipe renomeada</span><span class="sxs-lookup"><span data-stu-id="3a975-158">Team renamed</span></span>        | <span data-ttu-id="3a975-159">teamRenamed</span><span class="sxs-lookup"><span data-stu-id="3a975-159">teamRenamed</span></span>       | <span data-ttu-id="3a975-160">OnTeamsTeamRenamedAsync</span><span class="sxs-lookup"><span data-stu-id="3a975-160">OnTeamsTeamRenamedAsync</span></span>    | <span data-ttu-id="3a975-161">[Uma equipe é renomeada](#team-renamed).</span><span class="sxs-lookup"><span data-stu-id="3a975-161">[A team is renamed](#team-renamed).</span></span>       | <span data-ttu-id="3a975-162">Equipe</span><span class="sxs-lookup"><span data-stu-id="3a975-162">Team</span></span> |
| <span data-ttu-id="3a975-163">Equipe excluída</span><span class="sxs-lookup"><span data-stu-id="3a975-163">Team deleted</span></span>        | <span data-ttu-id="3a975-164">teamDeleted</span><span class="sxs-lookup"><span data-stu-id="3a975-164">teamDeleted</span></span>       | <span data-ttu-id="3a975-165">OnTeamsTeamDeletedAsync</span><span class="sxs-lookup"><span data-stu-id="3a975-165">OnTeamsTeamDeletedAsync</span></span>    | <span data-ttu-id="3a975-166">[Uma equipe é excluída](#team-deleted).</span><span class="sxs-lookup"><span data-stu-id="3a975-166">[A team is deleted](#team-deleted).</span></span>       | <span data-ttu-id="3a975-167">Equipe</span><span class="sxs-lookup"><span data-stu-id="3a975-167">Team</span></span> |
| <span data-ttu-id="3a975-168">Equipe arquivada</span><span class="sxs-lookup"><span data-stu-id="3a975-168">Team archived</span></span>        | <span data-ttu-id="3a975-169">teamArchived</span><span class="sxs-lookup"><span data-stu-id="3a975-169">teamArchived</span></span>       | <span data-ttu-id="3a975-170">OnTeamsTeamArchivedAsync</span><span class="sxs-lookup"><span data-stu-id="3a975-170">OnTeamsTeamArchivedAsync</span></span>    | <span data-ttu-id="3a975-171">[Uma equipe é arquivada](#team-archived).</span><span class="sxs-lookup"><span data-stu-id="3a975-171">[A team is archived](#team-archived).</span></span>       | <span data-ttu-id="3a975-172">Equipe</span><span class="sxs-lookup"><span data-stu-id="3a975-172">Team</span></span> |
| <span data-ttu-id="3a975-173">Equipe desarquivada</span><span class="sxs-lookup"><span data-stu-id="3a975-173">Team unarchived</span></span>        | <span data-ttu-id="3a975-174">teamUnarchived</span><span class="sxs-lookup"><span data-stu-id="3a975-174">teamUnarchived</span></span>       | <span data-ttu-id="3a975-175">OnTeamsTeamUnarchivedAsync</span><span class="sxs-lookup"><span data-stu-id="3a975-175">OnTeamsTeamUnarchivedAsync</span></span>    | <span data-ttu-id="3a975-176">[Uma equipe é desarquivada.](#team-unarchived)</span><span class="sxs-lookup"><span data-stu-id="3a975-176">[A team is unarchived](#team-unarchived).</span></span>       | <span data-ttu-id="3a975-177">Equipe</span><span class="sxs-lookup"><span data-stu-id="3a975-177">Team</span></span> |
| <span data-ttu-id="3a975-178">Equipe restaurada</span><span class="sxs-lookup"><span data-stu-id="3a975-178">Team restored</span></span>        | <span data-ttu-id="3a975-179">teamRestored</span><span class="sxs-lookup"><span data-stu-id="3a975-179">teamRestored</span></span>      | <span data-ttu-id="3a975-180">OnTeamsTeamRestoredAsync</span><span class="sxs-lookup"><span data-stu-id="3a975-180">OnTeamsTeamRestoredAsync</span></span>    | [<span data-ttu-id="3a975-181">Uma equipe é restaurada</span><span class="sxs-lookup"><span data-stu-id="3a975-181">A team is restored</span></span>](#team-restored)       | <span data-ttu-id="3a975-182">Equipe</span><span class="sxs-lookup"><span data-stu-id="3a975-182">Team</span></span> |

### <a name="channel-created"></a><span data-ttu-id="3a975-183">Canal criado</span><span class="sxs-lookup"><span data-stu-id="3a975-183">Channel created</span></span>

<span data-ttu-id="3a975-184">O evento criado pelo canal é enviado para seu bot sempre que um novo canal é criado em uma equipe onde o bot está instalado.</span><span class="sxs-lookup"><span data-stu-id="3a975-184">The channel created event is sent to your bot whenever a new channel is created in a team where your bot is installed.</span></span>

<span data-ttu-id="3a975-185">O código a seguir mostra um exemplo de evento criado por canal:</span><span class="sxs-lookup"><span data-stu-id="3a975-185">The following code shows an example of channel created event:</span></span>

# <a name="c"></a>[<span data-ttu-id="3a975-186">C#</span><span class="sxs-lookup"><span data-stu-id="3a975-186">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelCreatedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the Channel created");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[<span data-ttu-id="3a975-187">TypeScript</span><span class="sxs-lookup"><span data-stu-id="3a975-187">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="3a975-188">JSON</span><span class="sxs-lookup"><span data-stu-id="3a975-188">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="3a975-189">Python</span><span class="sxs-lookup"><span data-stu-id="3a975-189">Python</span></span>](#tab/python)

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

### <a name="channel-renamed"></a><span data-ttu-id="3a975-190">Canal renomeado</span><span class="sxs-lookup"><span data-stu-id="3a975-190">Channel renamed</span></span>

<span data-ttu-id="3a975-191">O evento renomeado de canal é enviado para seu bot sempre que um canal é renomeado em uma equipe onde seu bot está instalado.</span><span class="sxs-lookup"><span data-stu-id="3a975-191">The channel renamed event is sent to your bot whenever a channel is renamed in a team where your bot is installed.</span></span>

<span data-ttu-id="3a975-192">O código a seguir mostra um exemplo de evento renomeado de canal:</span><span class="sxs-lookup"><span data-stu-id="3a975-192">The following code shows an example of channel renamed event:</span></span>

# <a name="c"></a>[<span data-ttu-id="3a975-193">C#</span><span class="sxs-lookup"><span data-stu-id="3a975-193">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelRenamedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the new Channel name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[<span data-ttu-id="3a975-194">TypeScript</span><span class="sxs-lookup"><span data-stu-id="3a975-194">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="3a975-195">JSON</span><span class="sxs-lookup"><span data-stu-id="3a975-195">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="3a975-196">Python</span><span class="sxs-lookup"><span data-stu-id="3a975-196">Python</span></span>](#tab/python)

```python
async def on_teams_channel_renamed(
    self, channel_info: ChannelInfo, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The new channel name is {channel_info.name}")
    )
```

* * *

### <a name="channel-deleted"></a><span data-ttu-id="3a975-197">Canal excluído</span><span class="sxs-lookup"><span data-stu-id="3a975-197">Channel deleted</span></span>

<span data-ttu-id="3a975-198">O evento excluído do canal é enviado para o bot sempre que um canal é excluído em uma equipe onde o bot está instalado.</span><span class="sxs-lookup"><span data-stu-id="3a975-198">The channel deleted event is sent to your bot whenever a channel is deleted in a team where your bot is installed.</span></span>

<span data-ttu-id="3a975-199">O código a seguir mostra um exemplo de evento excluído do canal:</span><span class="sxs-lookup"><span data-stu-id="3a975-199">The following code shows an example of channel deleted event:</span></span>

# <a name="c"></a>[<span data-ttu-id="3a975-200">C#</span><span class="sxs-lookup"><span data-stu-id="3a975-200">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelDeletedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the Channel deleted");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[<span data-ttu-id="3a975-201">TypeScript</span><span class="sxs-lookup"><span data-stu-id="3a975-201">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="3a975-202">JSON</span><span class="sxs-lookup"><span data-stu-id="3a975-202">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="3a975-203">Python</span><span class="sxs-lookup"><span data-stu-id="3a975-203">Python</span></span>](#tab/python)

```python
async def on_teams_channel_deleted(
    self, channel_info: ChannelInfo, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The deleted channel is {channel_info.name}")
    )
```

* * *

### <a name="channel-restored"></a><span data-ttu-id="3a975-204">Canal restaurado</span><span class="sxs-lookup"><span data-stu-id="3a975-204">Channel restored</span></span>

<span data-ttu-id="3a975-205">O evento restaurado do canal é enviado para o bot sempre que um canal que foi excluído anteriormente é restaurado em uma equipe em que o bot já está instalado.</span><span class="sxs-lookup"><span data-stu-id="3a975-205">The channel restored event is sent to your bot whenever a channel that was previously deleted is restored in a team where your bot is already installed.</span></span>

<span data-ttu-id="3a975-206">O código a seguir mostra um exemplo de evento restaurado do canal:</span><span class="sxs-lookup"><span data-stu-id="3a975-206">The following code shows an example of channel restored event:</span></span>

# <a name="c"></a>[<span data-ttu-id="3a975-207">C#</span><span class="sxs-lookup"><span data-stu-id="3a975-207">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelRestoredAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the Channel restored.");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[<span data-ttu-id="3a975-208">TypeScript</span><span class="sxs-lookup"><span data-stu-id="3a975-208">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="3a975-209">JSON</span><span class="sxs-lookup"><span data-stu-id="3a975-209">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="3a975-210">Python</span><span class="sxs-lookup"><span data-stu-id="3a975-210">Python</span></span>](#tab/python)

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

### <a name="team-members-added"></a><span data-ttu-id="3a975-211">Membros da equipe adicionados</span><span class="sxs-lookup"><span data-stu-id="3a975-211">Team members added</span></span>

<span data-ttu-id="3a975-212">O `teamMemberAdded` evento é enviado ao seu bot na primeira vez em que é adicionado a uma conversa.</span><span class="sxs-lookup"><span data-stu-id="3a975-212">The `teamMemberAdded` event is sent to your bot the first time it is added to a conversation.</span></span> <span data-ttu-id="3a975-213">O evento é enviado para seu bot sempre que um novo usuário é adicionado a uma equipe ou chat de grupo onde seu bot está instalado.</span><span class="sxs-lookup"><span data-stu-id="3a975-213">The event is sent to your bot every time a new user is added to a team or group chat where your bot is installed.</span></span> <span data-ttu-id="3a975-214">As informações do usuário que são ID são exclusivas para seu bot e podem ser armazenadas em cache para uso futuro pelo seu serviço, como o envio de uma mensagem para um usuário específico.</span><span class="sxs-lookup"><span data-stu-id="3a975-214">The user information that is ID is unique for your bot and can be cached for future use by your service, such as sending a message to a specific user.</span></span>

<span data-ttu-id="3a975-215">O código a seguir mostra um exemplo de evento adicionado aos membros da equipe:</span><span class="sxs-lookup"><span data-stu-id="3a975-215">The following code shows an example of team members added event:</span></span>

# <a name="c"></a>[<span data-ttu-id="3a975-216">C#</span><span class="sxs-lookup"><span data-stu-id="3a975-216">C#</span></span>](#tab/dotnet)

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

# <a name="typescript"></a>[<span data-ttu-id="3a975-217">TypeScript</span><span class="sxs-lookup"><span data-stu-id="3a975-217">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="3a975-218">JSON</span><span class="sxs-lookup"><span data-stu-id="3a975-218">JSON</span></span>](#tab/json)

<span data-ttu-id="3a975-219">Esta é a mensagem que seu bot recebe quando o bot é adicionado a uma equipe.</span><span class="sxs-lookup"><span data-stu-id="3a975-219">This is the message your bot receives when the bot is added to a team.</span></span>

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

<span data-ttu-id="3a975-220">Esta é a mensagem que seu bot recebe quando o bot é adicionado a um chat um para um.</span><span class="sxs-lookup"><span data-stu-id="3a975-220">This is the message your bot receives when the bot is added to a one-to-one chat.</span></span>

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

# <a name="python"></a>[<span data-ttu-id="3a975-221">Python</span><span class="sxs-lookup"><span data-stu-id="3a975-221">Python</span></span>](#tab/python)

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

### <a name="team-members-removed"></a><span data-ttu-id="3a975-222">Membros da equipe removidos</span><span class="sxs-lookup"><span data-stu-id="3a975-222">Team members removed</span></span>

<span data-ttu-id="3a975-223">O `teamMemberRemoved` evento é enviado para seu bot se for removido de uma equipe.</span><span class="sxs-lookup"><span data-stu-id="3a975-223">The `teamMemberRemoved` event is sent to your bot if it is removed from a team.</span></span> <span data-ttu-id="3a975-224">O evento é enviado ao bot sempre que qualquer usuário é removido de uma equipe em que o bot é membro.</span><span class="sxs-lookup"><span data-stu-id="3a975-224">The event is sent to your bot every time any user is removed from a team where your bot is a member.</span></span> <span data-ttu-id="3a975-225">Para determinar se o novo membro removido foi o próprio bot ou um usuário, verifique o `Activity` objeto do `turnContext` .</span><span class="sxs-lookup"><span data-stu-id="3a975-225">To determine if the new member removed was the bot itself or a user, check the `Activity` object of the `turnContext`.</span></span>  <span data-ttu-id="3a975-226">Se o campo do objeto for o mesmo que o campo do objeto, o membro removido será o bot, senão `Id` será `MembersRemoved` um `Id` `Recipient` usuário.</span><span class="sxs-lookup"><span data-stu-id="3a975-226">If the `Id` field of the `MembersRemoved` object is the same as the `Id` field of the `Recipient` object, then the member removed is the bot, else it is a user.</span></span> <span data-ttu-id="3a975-227">Geralmente, o bot `Id` é `28:<MicrosoftAppId>` .</span><span class="sxs-lookup"><span data-stu-id="3a975-227">The bot's `Id` generally is `28:<MicrosoftAppId>`.</span></span>

> [!NOTE]
> <span data-ttu-id="3a975-228">Quando um usuário é excluído permanentemente de um locatário, `membersRemoved conversationUpdate` o evento é acionado.</span><span class="sxs-lookup"><span data-stu-id="3a975-228">When a user is permanently deleted from a tenant, `membersRemoved conversationUpdate` event is triggered.</span></span>

<span data-ttu-id="3a975-229">O código a seguir mostra um exemplo de evento removido pelos membros da equipe:</span><span class="sxs-lookup"><span data-stu-id="3a975-229">The following code shows an example of team members removed event:</span></span>

# <a name="c"></a>[<span data-ttu-id="3a975-230">C#</span><span class="sxs-lookup"><span data-stu-id="3a975-230">C#</span></span>](#tab/dotnet)

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

# <a name="typescript"></a>[<span data-ttu-id="3a975-231">TypeScript</span><span class="sxs-lookup"><span data-stu-id="3a975-231">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="3a975-232">JSON</span><span class="sxs-lookup"><span data-stu-id="3a975-232">JSON</span></span>](#tab/json)

<span data-ttu-id="3a975-233">O objeto no exemplo de carga a seguir baseia-se na adição de um membro a uma equipe em vez de um chat em grupo ou na inicialização de uma nova conversa um `channelData` para um:</span><span class="sxs-lookup"><span data-stu-id="3a975-233">The `channelData` object in the following payload example is based on adding a member to a team rather than a group chat, or initiating a new one-to-one conversation:</span></span>

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


# <a name="python"></a>[<span data-ttu-id="3a975-234">Python</span><span class="sxs-lookup"><span data-stu-id="3a975-234">Python</span></span>](#tab/python)

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

### <a name="team-renamed"></a><span data-ttu-id="3a975-235">Equipe renomeada</span><span class="sxs-lookup"><span data-stu-id="3a975-235">Team renamed</span></span>

<span data-ttu-id="3a975-236">Seu bot é notificado quando a equipe em que está foi renomeada.</span><span class="sxs-lookup"><span data-stu-id="3a975-236">Your bot is notified when the team it is in has been renamed.</span></span> <span data-ttu-id="3a975-237">Ele recebe um `conversationUpdate` evento `eventType.teamRenamed` com no `channelData` objeto.</span><span class="sxs-lookup"><span data-stu-id="3a975-237">It receives a `conversationUpdate` event with `eventType.teamRenamed` in the `channelData` object.</span></span>

<span data-ttu-id="3a975-238">O código a seguir mostra um exemplo de evento renomeado para equipe:</span><span class="sxs-lookup"><span data-stu-id="3a975-238">The following code shows an example of team renamed event:</span></span>

# <a name="c"></a>[<span data-ttu-id="3a975-239">C#</span><span class="sxs-lookup"><span data-stu-id="3a975-239">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamRenamedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the new Team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[<span data-ttu-id="3a975-240">TypeScript</span><span class="sxs-lookup"><span data-stu-id="3a975-240">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="3a975-241">JSON</span><span class="sxs-lookup"><span data-stu-id="3a975-241">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="3a975-242">Python</span><span class="sxs-lookup"><span data-stu-id="3a975-242">Python</span></span>](#tab/python)

```python
async def on_teams_team_renamed(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The new team name is {team_info.name}")
    )
```

* * *

### <a name="team-deleted"></a><span data-ttu-id="3a975-243">Equipe excluída</span><span class="sxs-lookup"><span data-stu-id="3a975-243">Team deleted</span></span>

<span data-ttu-id="3a975-244">Seu bot é notificado quando a equipe em que está foi excluída.</span><span class="sxs-lookup"><span data-stu-id="3a975-244">Your bot is notified when the team it is in has been deleted.</span></span> <span data-ttu-id="3a975-245">Ele recebe um `conversationUpdate` evento `eventType.teamDeleted` com no `channelData` objeto.</span><span class="sxs-lookup"><span data-stu-id="3a975-245">It receives a `conversationUpdate` event with `eventType.teamDeleted` in the `channelData` object.</span></span>

<span data-ttu-id="3a975-246">O código a seguir mostra um exemplo de evento excluído da equipe:</span><span class="sxs-lookup"><span data-stu-id="3a975-246">The following code shows an example of team deleted event:</span></span>

# <a name="c"></a>[<span data-ttu-id="3a975-247">C#</span><span class="sxs-lookup"><span data-stu-id="3a975-247">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamDeletedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    //handle delete event
}
```

# <a name="typescript"></a>[<span data-ttu-id="3a975-248">TypeScript</span><span class="sxs-lookup"><span data-stu-id="3a975-248">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="3a975-249">JSON</span><span class="sxs-lookup"><span data-stu-id="3a975-249">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="3a975-250">Python</span><span class="sxs-lookup"><span data-stu-id="3a975-250">Python</span></span>](#tab/python)

```python
async def on_teams_team_deleted(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    //handle delete event
    )
```

* * *

### <a name="team-restored"></a><span data-ttu-id="3a975-251">Equipe restaurada</span><span class="sxs-lookup"><span data-stu-id="3a975-251">Team restored</span></span>

<span data-ttu-id="3a975-252">O bot recebe uma notificação quando uma equipe é restaurada após ser excluída.</span><span class="sxs-lookup"><span data-stu-id="3a975-252">The bot receives a notification when a team is restored after being deleted.</span></span> <span data-ttu-id="3a975-253">Ele recebe um `conversationUpdate` evento `eventType.teamrestored` com no `channelData` objeto.</span><span class="sxs-lookup"><span data-stu-id="3a975-253">It receives a `conversationUpdate` event with `eventType.teamrestored` in the `channelData` object.</span></span>

<span data-ttu-id="3a975-254">O código a seguir mostra um exemplo de evento restaurado pela equipe:</span><span class="sxs-lookup"><span data-stu-id="3a975-254">The following code shows an example of team restored event:</span></span>

# <a name="c"></a>[<span data-ttu-id="3a975-255">C#</span><span class="sxs-lookup"><span data-stu-id="3a975-255">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamrestoredAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[<span data-ttu-id="3a975-256">TypeScript</span><span class="sxs-lookup"><span data-stu-id="3a975-256">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="3a975-257">JSON</span><span class="sxs-lookup"><span data-stu-id="3a975-257">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="3a975-258">Python</span><span class="sxs-lookup"><span data-stu-id="3a975-258">Python</span></span>](#tab/python)

```python
async def on_teams_team_restored(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The team name is {team_info.name}")
    )
```

* * *

### <a name="team-archived"></a><span data-ttu-id="3a975-259">Equipe arquivada</span><span class="sxs-lookup"><span data-stu-id="3a975-259">Team archived</span></span>

<span data-ttu-id="3a975-260">O bot recebe uma notificação quando a equipe em que está instalada é arquivada.</span><span class="sxs-lookup"><span data-stu-id="3a975-260">The bot receives a notification when the team it is installed in is archived.</span></span> <span data-ttu-id="3a975-261">Ele recebe um `conversationUpdate` evento `eventType.teamarchived` com no `channelData` objeto.</span><span class="sxs-lookup"><span data-stu-id="3a975-261">It receives a `conversationUpdate` event with `eventType.teamarchived` in the `channelData` object.</span></span>

<span data-ttu-id="3a975-262">O código a seguir mostra um exemplo de evento arquivado pela equipe:</span><span class="sxs-lookup"><span data-stu-id="3a975-262">The following code shows an example of team archived event:</span></span>

# <a name="c"></a>[<span data-ttu-id="3a975-263">C#</span><span class="sxs-lookup"><span data-stu-id="3a975-263">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamArchivedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[<span data-ttu-id="3a975-264">TypeScript</span><span class="sxs-lookup"><span data-stu-id="3a975-264">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="3a975-265">JSON</span><span class="sxs-lookup"><span data-stu-id="3a975-265">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="3a975-266">Python</span><span class="sxs-lookup"><span data-stu-id="3a975-266">Python</span></span>](#tab/python)

```python
async def on_teams_team_archived(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The team name is {team_info.name}")
    )
```

* * *


### <a name="team-unarchived"></a><span data-ttu-id="3a975-267">Equipe desarquivada</span><span class="sxs-lookup"><span data-stu-id="3a975-267">Team unarchived</span></span>

<span data-ttu-id="3a975-268">O bot recebe uma notificação quando a equipe em que ele está instalado é desarquivada.</span><span class="sxs-lookup"><span data-stu-id="3a975-268">The bot receives a notification when the team it is installed in is unarchived.</span></span> <span data-ttu-id="3a975-269">Ele recebe um `conversationUpdate` evento `eventType.teamUnarchived` com no `channelData` objeto.</span><span class="sxs-lookup"><span data-stu-id="3a975-269">It receives a `conversationUpdate` event with `eventType.teamUnarchived` in the `channelData` object.</span></span>

<span data-ttu-id="3a975-270">O código a seguir mostra um exemplo de evento não pesquisado da equipe:</span><span class="sxs-lookup"><span data-stu-id="3a975-270">The following code shows an example of team unarchived event:</span></span>

# <a name="c"></a>[<span data-ttu-id="3a975-271">C#</span><span class="sxs-lookup"><span data-stu-id="3a975-271">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamUnarchivedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[<span data-ttu-id="3a975-272">TypeScript</span><span class="sxs-lookup"><span data-stu-id="3a975-272">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="3a975-273">JSON</span><span class="sxs-lookup"><span data-stu-id="3a975-273">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="3a975-274">Python</span><span class="sxs-lookup"><span data-stu-id="3a975-274">Python</span></span>](#tab/python)

```python
async def on_teams_team_unarchived(
    self, team_info: TeamInfo, turn_context: TurnContext
):
    return await turn_context.send_activity(
        MessageFactory.text(f"The team name is {team_info.name}")
    )
```

* * *

<span data-ttu-id="3a975-275">Agora que você trabalhou com os eventos de atualização de conversa, você pode entender os eventos de reação de mensagem que ocorrem para diferentes reações a uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="3a975-275">Now that you have worked with the conversation update events, you can understand the message reaction events that occur for different reactions to a message.</span></span>

## <a name="message-reaction-events"></a><span data-ttu-id="3a975-276">Eventos de reação de mensagens</span><span class="sxs-lookup"><span data-stu-id="3a975-276">Message reaction events</span></span>

<span data-ttu-id="3a975-277">O `messageReaction` evento é enviado quando um usuário adiciona ou remove reações a uma mensagem que foi enviada pelo bot.</span><span class="sxs-lookup"><span data-stu-id="3a975-277">The `messageReaction` event is sent when a user adds or removes reactions to a message which was sent by your bot.</span></span> <span data-ttu-id="3a975-278">O `replyToId` contém a ID da mensagem e o `Type` é o tipo de reação no formato de texto.</span><span class="sxs-lookup"><span data-stu-id="3a975-278">The `replyToId` contains the ID of the message, and the `Type` is the type of reaction in text format.</span></span> <span data-ttu-id="3a975-279">Os tipos de reações incluem raiva, coração, riso, como, triste e surpresa.</span><span class="sxs-lookup"><span data-stu-id="3a975-279">The types of reactions include angry, heart, laugh, like, sad, and surprised.</span></span> <span data-ttu-id="3a975-280">Esse evento não contém o conteúdo da mensagem original.</span><span class="sxs-lookup"><span data-stu-id="3a975-280">This event does not contain the contents of the original message.</span></span> <span data-ttu-id="3a975-281">Se o processamento de reações às suas mensagens for importante para o bot, você deve armazenar as mensagens ao enviá-las.</span><span class="sxs-lookup"><span data-stu-id="3a975-281">If processing reactions to your messages is important for your bot, you must store the messages when you send them.</span></span> <span data-ttu-id="3a975-282">A tabela a seguir fornece mais informações sobre o tipo de evento e objetos de carga:</span><span class="sxs-lookup"><span data-stu-id="3a975-282">The following table provides more information about the event type and payload objects:</span></span>

| <span data-ttu-id="3a975-283">EventType</span><span class="sxs-lookup"><span data-stu-id="3a975-283">EventType</span></span>       | <span data-ttu-id="3a975-284">Objeto Payload</span><span class="sxs-lookup"><span data-stu-id="3a975-284">Payload object</span></span>   | <span data-ttu-id="3a975-285">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a975-285">Description</span></span>                                                             | <span data-ttu-id="3a975-286">Escopo</span><span class="sxs-lookup"><span data-stu-id="3a975-286">Scope</span></span> |
| --------------- | ---------------- | ----------------------------------------------------------------------- | ----- |
| <span data-ttu-id="3a975-287">messageReaction</span><span class="sxs-lookup"><span data-stu-id="3a975-287">messageReaction</span></span> | <span data-ttu-id="3a975-288">reactionsAdded</span><span class="sxs-lookup"><span data-stu-id="3a975-288">reactionsAdded</span></span>   | [<span data-ttu-id="3a975-289">Reações a uma mensagem de bot</span><span class="sxs-lookup"><span data-stu-id="3a975-289">Reactions to a bot message</span></span>](#reactions-to-a-bot-message)                   | <span data-ttu-id="3a975-290">Todos</span><span class="sxs-lookup"><span data-stu-id="3a975-290">All</span></span>   |
| <span data-ttu-id="3a975-291">messageReaction</span><span class="sxs-lookup"><span data-stu-id="3a975-291">messageReaction</span></span> | <span data-ttu-id="3a975-292">reactionsRemoved</span><span class="sxs-lookup"><span data-stu-id="3a975-292">reactionsRemoved</span></span> | [<span data-ttu-id="3a975-293">Reações removidas da mensagem bot</span><span class="sxs-lookup"><span data-stu-id="3a975-293">Reactions removed from bot message</span></span>](#reactions-removed-from-bot-message) | <span data-ttu-id="3a975-294">Todos</span><span class="sxs-lookup"><span data-stu-id="3a975-294">All</span></span>   |

### <a name="reactions-to-a-bot-message"></a><span data-ttu-id="3a975-295">Reações a uma mensagem de bot</span><span class="sxs-lookup"><span data-stu-id="3a975-295">Reactions to a bot message</span></span>

<span data-ttu-id="3a975-296">O código a seguir mostra um exemplo de reações a uma mensagem de bot:</span><span class="sxs-lookup"><span data-stu-id="3a975-296">The following code shows an example of reactions to a bot message:</span></span>

# <a name="c"></a>[<span data-ttu-id="3a975-297">C#</span><span class="sxs-lookup"><span data-stu-id="3a975-297">C#</span></span>](#tab/dotnet)

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

# <a name="typescript"></a>[<span data-ttu-id="3a975-298">TypeScript</span><span class="sxs-lookup"><span data-stu-id="3a975-298">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="3a975-299">JSON</span><span class="sxs-lookup"><span data-stu-id="3a975-299">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="3a975-300">Python</span><span class="sxs-lookup"><span data-stu-id="3a975-300">Python</span></span>](#tab/python)

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

### <a name="reactions-removed-from-bot-message"></a><span data-ttu-id="3a975-301">Reações removidas da mensagem bot</span><span class="sxs-lookup"><span data-stu-id="3a975-301">Reactions removed from bot message</span></span>

<span data-ttu-id="3a975-302">O código a seguir mostra um exemplo de reações removidas da mensagem bot:</span><span class="sxs-lookup"><span data-stu-id="3a975-302">The following code shows an example of reactions removed from bot message:</span></span>

# <a name="c"></a>[<span data-ttu-id="3a975-303">C#</span><span class="sxs-lookup"><span data-stu-id="3a975-303">C#</span></span>](#tab/dotnet)

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

# <a name="typescript"></a>[<span data-ttu-id="3a975-304">TypeScript</span><span class="sxs-lookup"><span data-stu-id="3a975-304">TypeScript</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="3a975-305">JSON</span><span class="sxs-lookup"><span data-stu-id="3a975-305">JSON</span></span>](#tab/json)

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

# <a name="python"></a>[<span data-ttu-id="3a975-306">Python</span><span class="sxs-lookup"><span data-stu-id="3a975-306">Python</span></span>](#tab/python)

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

## <a name="code-sample"></a><span data-ttu-id="3a975-307">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="3a975-307">Code sample</span></span>

<span data-ttu-id="3a975-308">A tabela a seguir fornece um exemplo de código simples que incorpora eventos de conversa de bots em um aplicativo do Teams:</span><span class="sxs-lookup"><span data-stu-id="3a975-308">The following table provides a simple code sample that incorporates bots conversation events into a Teams application:</span></span>

| <span data-ttu-id="3a975-309">Amostra</span><span class="sxs-lookup"><span data-stu-id="3a975-309">Sample</span></span> | <span data-ttu-id="3a975-310">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a975-310">Description</span></span> | <span data-ttu-id="3a975-311">.NET Core</span><span class="sxs-lookup"><span data-stu-id="3a975-311">.NET Core</span></span> |
|--------|------------- |---|
| <span data-ttu-id="3a975-312">Exemplo de eventos de conversa de bots do Teams</span><span class="sxs-lookup"><span data-stu-id="3a975-312">Teams bots conversation events sample</span></span> | <span data-ttu-id="3a975-313">Exemplo de bot de conversa do Bot Framework v4 para o Teams.</span><span class="sxs-lookup"><span data-stu-id="3a975-313">Bot Framework v4 conversation bot sample for Teams.</span></span> | [<span data-ttu-id="3a975-314">View</span><span class="sxs-lookup"><span data-stu-id="3a975-314">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot)|

## <a name="next-step"></a><span data-ttu-id="3a975-315">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="3a975-315">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3a975-316">Enviar mensagens proativas</span><span class="sxs-lookup"><span data-stu-id="3a975-316">Send proactive messages</span></span>](~/bots/how-to/conversations/send-proactive-messages.md)
