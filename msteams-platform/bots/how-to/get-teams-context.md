---
title: Obter o contexto específico da equipe para o bot
author: clearab
description: Como obter o contexto específico da equipe da Microsoft para o bot, incluindo a lista de conversas, detalhes e lista de canais.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 9f70e3e052903365f03c541db83f196f33fc2322
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672839"
---
# <a name="get-teams-specific-context-for-your-bot"></a><span data-ttu-id="00315-103">Obter o contexto específico da equipe para o bot</span><span class="sxs-lookup"><span data-stu-id="00315-103">Get Team's specific context for your bot</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="00315-104">Um bot pode acessar dados de contexto adicionais sobre uma equipe ou bate-papo em que ele está instalado.</span><span class="sxs-lookup"><span data-stu-id="00315-104">A bot can access additional context data about a team or chat it is installed in.</span></span> <span data-ttu-id="00315-105">Essas informações podem ser usadas para enriquecer a funcionalidade do bot e fornecer uma experiência mais personalizada.</span><span class="sxs-lookup"><span data-stu-id="00315-105">This information can be used to enrich the bot's functionality and provide a more personalized experience.</span></span>

## <a name="fetching-the-roster-or-user-profile"></a><span data-ttu-id="00315-106">Buscando a lista ou o perfil do usuário</span><span class="sxs-lookup"><span data-stu-id="00315-106">Fetching the roster or user profile</span></span>

<span data-ttu-id="00315-107">Seu bot pode consultar a lista de membros e seus perfis básicos, incluindo IDs de usuário de equipes e informações do Azure Active Directory (Azure AD), como Name e objectId.</span><span class="sxs-lookup"><span data-stu-id="00315-107">Your bot can query for the list of members and their basic profiles, including Teams user IDs and Azure Active Directory (Azure AD) information such as name and objectId.</span></span> <span data-ttu-id="00315-108">Você pode usar essas informações para correlacionar as identidades do usuário, por exemplo, para verificar se um usuário fez logon em uma guia através de credenciais do Azure AD, é membro da equipe.</span><span class="sxs-lookup"><span data-stu-id="00315-108">You can use this information to correlate user identities, e.g., to check whether a user, logged into a tab through Azure AD credentials, is a member of the team.</span></span> <span data-ttu-id="00315-109">Você também pode usar essa chamada em um chat de um-para-um para obter informações adicionais sobre o usuário.</span><span class="sxs-lookup"><span data-stu-id="00315-109">You can also use this call in a one-to-one chat to gain additional information about your user.</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="00315-110">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="00315-110">C#/.NET</span></span>](#tab/dotnet)

```csharp
public class MyBot : TeamsActivityHandler
{
    protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
    {
        IEnumerable<TeamsChannelAccount> members = await TeamsInfo.GetMembersAsync(turnContext, cancellationToken);
    }
}
```

# <a name="typescriptnodejstabtypescript"></a>[<span data-ttu-id="00315-111">TypeScript/node. js</span><span class="sxs-lookup"><span data-stu-id="00315-111">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();

        // See https://aka.ms/about-bot-activity-message to learn more about the message and other activity types.
        this.onMessage(async (turnContext, next) => {
            const members = await TeamsInfo.getMembers(turnContext);

            // By calling next() you ensure that the next BotHandler is run.
            await next();
        });
    }
}
```

# <a name="jsontabjson"></a>[<span data-ttu-id="00315-112">JSON</span><span class="sxs-lookup"><span data-stu-id="00315-112">JSON</span></span>](#tab/json)
<span data-ttu-id="00315-113">Você pode emitir diretamente uma solicitação GET no `/v3/conversations/{teamId}/members/`, usando o valor de `serviceUrl` como ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="00315-113">You can directly issue a GET request on `/v3/conversations/{teamId}/members/`, using the value of `serviceUrl` as the endpoint.</span></span> <span data-ttu-id="00315-114">O valor de `serviceUrl` tende a ser estável, mas pode ser alterado.</span><span class="sxs-lookup"><span data-stu-id="00315-114">The value of `serviceUrl` tends to be stable but can change.</span></span> <span data-ttu-id="00315-115">Quando uma nova mensagem chega, seu bot deve confirmar seu valor armazenado para `serviceUrl`.</span><span class="sxs-lookup"><span data-stu-id="00315-115">When a new message arrives, your bot should verify its stored value for `serviceUrl`.</span></span>

```http
GET /v3/conversations/19:ja0cu120i1jod12j@skype.net/members

Response body
[{
    "id": "29:1GcS4EyB_oSI8A88XmWBN7NJFyMqe3QGnJdgLfFGkJnVelzRGos0bPbpsfJjcbAD22bmKc4GMbrY2g4JDrrA8vM06X1-cHHle4zOE6U4ttcc",
    "objectId": "9d3e08f9-a7ae-43aa-a4d3-de3f319a8a9c",
    "givenName": "Larry",
    "surname": "Brown",
    "email": "Larry.Brown@fabrikam.com",
    "userPrincipalName": "labrown@fabrikam.com"
}, {
    "id": "29:1bSnHZ7Js2STWrgk6ScEErLk1Lp2zQuD5H2qQ960rtvstKp8tKLl-3r8b6DoW0QxZimuTxk_kupZ1DBMpvIQQUAZL-PNj0EORDvRZXy8kvWk",
    "objectId": "76b0b09f-d410-48fd-993e-84da521a597b",
    "givenName": "John",
    "surname": "Patterson",
    "email": "johnp@fabrikam.com",
    "userPrincipalName": "johnp@fabrikam.com"
}, {
    "id": "29:1URzNQM1x1PNMr1D7L5_lFe6qF6gEfAbkdG8_BUxOW2mTKryQqEZtBTqDt10-MghkzjYDuUj4KG6nvg5lFAyjOLiGJ4jzhb99WrnI7XKriCs",
    "objectId": "6b7b3b2a-2c4b-4175-8582-41c9e685c1b5",
    "givenName": "Rick",
    "surname": "Stevens",
    "email": "Rick.Stevens@fabrikam.com",
    "userPrincipalName": "rstevens@fabrikam.com"
}]
```

# <a name="pythontabpython"></a>[<span data-ttu-id="00315-116">Python</span><span class="sxs-lookup"><span data-stu-id="00315-116">Python</span></span>](#tab/python)

```python
async def _show_members(
    self, turn_context: TurnContext
):
    members = await TeamsInfo.get_team_members(turn_context)
```

* * *

## <a name="get-teams-details"></a><span data-ttu-id="00315-117">Obter detalhes da equipe</span><span class="sxs-lookup"><span data-stu-id="00315-117">Get team's details</span></span>

<span data-ttu-id="00315-118">Quando instalado em uma equipe, seu bot pode consultar metadados sobre essa equipe, incluindo o Azure AD GroupId.</span><span class="sxs-lookup"><span data-stu-id="00315-118">When installed in a team, your bot can query for metadata about that team including the Azure AD groupId.</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="00315-119">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="00315-119">C#/.NET</span></span>](#tab/dotnet)

```csharp
public class MyBot : TeamsActivityHandler
{
    protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
    {
        TeamDetails teamDetails = await TeamsInfo.GetTeamDetailsAsync(turnContext, turnContext.Activity.TeamsGetTeamInfo().Id, cancellationToken);
        if (teamDetails != null) {
            await turnContext.SendActivityAsync($"The groupId is: {teamDetails.AadGroupId}");
        }
        else {
            await turnContext.SendActivityAsync($"Message did not come from a channel in a team.");
        }
    }
}
```

# <a name="typescriptnodejstabtypescript"></a>[<span data-ttu-id="00315-120">TypeScript/node. js</span><span class="sxs-lookup"><span data-stu-id="00315-120">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();

        // See https://aka.ms/about-bot-activity-message to learn more about the message and other activity types.
        this.onMessage(async (turnContext, next) => {
            const teamDetails = await TeamsInfo.getTeamDetails(turnContext);
            if (teamDetails) {
                await turnContext.sendActivity(`The group ID is: ${teamDetails.aadGroupId}`);
            } else {
                await turnContext.sendActivity('This message did not come from a channel in a team.');
            }

            // By calling next() you ensure that the next BotHandler is run.
            await next();
        });
    }
}
```

# <a name="jsontabjson"></a>[<span data-ttu-id="00315-121">JSON</span><span class="sxs-lookup"><span data-stu-id="00315-121">JSON</span></span>](#tab/json)

<span data-ttu-id="00315-122">Você pode emitir diretamente uma solicitação GET no `/v3/teams/{teamId}`, usando o valor de `serviceUrl` como ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="00315-122">You can directly issue a GET request on `/v3/teams/{teamId}`, using the value of `serviceUrl` as the endpoint.</span></span> <span data-ttu-id="00315-123">O valor de `serviceUrl` tende a ser estável, mas pode ser alterado.</span><span class="sxs-lookup"><span data-stu-id="00315-123">The value of `serviceUrl` tends to be stable but can change.</span></span> <span data-ttu-id="00315-124">Quando uma nova mensagem chega, seu bot deve confirmar seu valor armazenado para `serviceUrl`.</span><span class="sxs-lookup"><span data-stu-id="00315-124">When a new message arrives, your bot should verify its stored value for `serviceUrl`.</span></span>

```http
GET /v3/teams/19:ja0cu120i1jod12j@skype.net

Response body
{
    "id": "29:1GcS4EyB_oSI8A88XmWBN7NJFyMqe3QGnJdgLfFGkJnVelzRGos0bPbpsfJjcbAD22bmKc4GMbrY2g4JDrrA8vM06X1-cHHle4zOE6U4ttcc",
    "name": "The Team Name",
    "aadGroupId": "02ce3874-dd86-41ba-bddc-013f34019978"
}
```

# <a name="pythontabpython"></a>[<span data-ttu-id="00315-125">Python</span><span class="sxs-lookup"><span data-stu-id="00315-125">Python</span></span>](#tab/python)

```python
async def _show_details(self, turn_context: TurnContext):
    team_details = await TeamsInfo.get_team_details(turn_context)
    reply = MessageFactory.text(f"The team name is {team_details.name}. The team ID is {team_details.id}. The AADGroupID is {team_details.aad_group_id}.")
    await turn_context.send_activity(reply)
```

* * *

## <a name="get-the-list-of-channels-in-a-team"></a><span data-ttu-id="00315-126">Obter a lista de canais em uma equipe</span><span class="sxs-lookup"><span data-stu-id="00315-126">Get the list of channels in a team</span></span>

<span data-ttu-id="00315-127">O bot pode consultar a lista de canais de uma equipe.</span><span class="sxs-lookup"><span data-stu-id="00315-127">Your bot can query the list of channels in a team.</span></span>

> [!NOTE]
>
>* <span data-ttu-id="00315-128">O nome do canal geral padrão é retornado como `null` permitir para localização.</span><span class="sxs-lookup"><span data-stu-id="00315-128">The name of the default General channel is returned as `null` to allow for localization.</span></span>
>* <span data-ttu-id="00315-129">A ID do canal geral sempre corresponde à ID da equipe.</span><span class="sxs-lookup"><span data-stu-id="00315-129">The channel ID for the General channel always matches the team ID.</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="00315-130">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="00315-130">C#/.NET</span></span>](#tab/dotnet)

```csharp
public class MyBot : TeamsActivityHandler
{
    protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
    {
        IEnumerable<ChannelInfo> channels = await TeamsInfo.GetTeamChannelsAsync(turnContext, turnContext.Activity.TeamsGetTeamInfo().Id, cancellationToken);

        await turnContext.SendActivityAsync($"The channel count is: {channels.Count()}");
    }
}
```

# <a name="typescriptnodejstabtypescript"></a>[<span data-ttu-id="00315-131">TypeScript/node. js</span><span class="sxs-lookup"><span data-stu-id="00315-131">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();

        // See https://aka.ms/about-bot-activity-message to learn more about the message and other activity types.
        this.onMessage(async (turnContext, next) => {
            const channels = await TeamsInfo.getTeamChannels(turnContext);

            await turnContext.sendActivity(`The channel count is: ${channels.length}`);

            // By calling next() you ensure that the next BotHandler is run.
            await next();
        });
    }
}
```

# <a name="jsontabjson"></a>[<span data-ttu-id="00315-132">JSON</span><span class="sxs-lookup"><span data-stu-id="00315-132">JSON</span></span>](#tab/json)

<span data-ttu-id="00315-133">Você pode emitir diretamente uma solicitação GET no `/v3/teams/{teamId}/conversations`, usando o valor de `serviceUrl` como ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="00315-133">You can directly issue a GET request on `/v3/teams/{teamId}/conversations`, using the value of `serviceUrl` as the endpoint.</span></span> <span data-ttu-id="00315-134">O valor de `serviceUrl` tende a ser estável, mas pode ser alterado.</span><span class="sxs-lookup"><span data-stu-id="00315-134">The value of `serviceUrl` tends to be stable but can change.</span></span> <span data-ttu-id="00315-135">Quando uma nova mensagem chega, seu bot deve confirmar seu valor armazenado para `serviceUrl`.</span><span class="sxs-lookup"><span data-stu-id="00315-135">When a new message arrives, your bot should verify its stored value for `serviceUrl`.</span></span>

```http
GET /v3/teams/19%3A033451497ea84fcc83d17ed7fb08a1b6%40thread.skype/conversations

Response body
{
    "conversations": [{
        "id": "19:033451497ea84fcc83d17ed7fb08a1b6@thread.skype",
        "name": null
    }, {
        "id": "19:cc25e4aae50746ecbb11473bba24c70a@thread.skype",
        "name": "Materials"
    }, {
        "id": "19:b7b84cba410c406ba671dbbf5e0a3519@thread.skype",
        "name": "Design"
    }, {
        "id": "19:fc5db2aed489454e8f8c06829ed6c986@thread.skype",
        "name": "Marketing"
    }]
}
```


# <a name="pythontabpython"></a>[<span data-ttu-id="00315-136">Python</span><span class="sxs-lookup"><span data-stu-id="00315-136">Python</span></span>](#tab/python)

```python
async def _show_channels(
    self, turn_context: TurnContext
):
    channels = await TeamsInfo.get_team_channels(turn_context)
    reply = MessageFactory.text(f"Total of {len(channels)} channels are currently in team")
    await turn_context.send_activity(reply)
```

* * *

[!INCLUDE [sample](~/includes/bots/teams-bot-samples.md)]
