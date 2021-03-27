---
title: Obter contexto específico da equipe para seu bot
author: laujan
description: Como obter o contexto específico do Microsoft Team para seu bot, incluindo a lista de canais, detalhes e lista de conversas.
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: dfbf5e1638a2397492714b1e1945721450428d63
ms.sourcegitcommit: 0206ed48c6a287d14aec3739540194a91766f0a3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2021
ms.locfileid: "51378333"
---
# <a name="get-teams-specific-context-for-your-bot"></a><span data-ttu-id="4fafd-103">Obter contexto específico da equipe para seu bot</span><span class="sxs-lookup"><span data-stu-id="4fafd-103">Get Team's specific context for your bot</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="4fafd-104">Um bot pode acessar dados de contexto adicionais sobre uma equipe ou chat em que está instalado.</span><span class="sxs-lookup"><span data-stu-id="4fafd-104">A bot can access additional context data about a team or chat it is installed in.</span></span> <span data-ttu-id="4fafd-105">Essas informações podem ser usadas para enriquecer a funcionalidade do bot e fornecer uma experiência mais personalizada.</span><span class="sxs-lookup"><span data-stu-id="4fafd-105">This information can be used to enrich the bot's functionality and provide a more personalized experience.</span></span>

## <a name="fetching-the-roster-or-user-profile"></a><span data-ttu-id="4fafd-106">Buscar a lista ou o perfil de usuário</span><span class="sxs-lookup"><span data-stu-id="4fafd-106">Fetching the roster or user profile</span></span>

<span data-ttu-id="4fafd-107">Seu bot pode consultar a lista de membros e seus perfis básicos, incluindo IDs de usuário do Teams e informações do Azure Active Directory (Azure AD), como name e objectId.</span><span class="sxs-lookup"><span data-stu-id="4fafd-107">Your bot can query for the list of members and their basic profiles, including Teams user IDs and Azure Active Directory (Azure AD) information such as name and objectId.</span></span> <span data-ttu-id="4fafd-108">Você pode usar essas informações para correlacionar identidades de usuário, por exemplo, para verificar se um usuário, conectado a uma guia por meio de credenciais do Azure AD, é membro da equipe.</span><span class="sxs-lookup"><span data-stu-id="4fafd-108">You can use this information to correlate user identities, e.g., to check whether a user, logged into a tab through Azure AD credentials, is a member of the team.</span></span> <span data-ttu-id="4fafd-109">O código de exemplo abaixo usa o ponto de extremidade pagedo para recuperar a lista.</span><span class="sxs-lookup"><span data-stu-id="4fafd-109">The sample code below uses the paged endpoint for retrieving the roster.</span></span> <span data-ttu-id="4fafd-110">Para obter membros da conversa, o tamanho mínimo ou máximo da página depende da implementação.</span><span class="sxs-lookup"><span data-stu-id="4fafd-110">For get conversation members, minimum or maximum page size depends on the implementation.</span></span> <span data-ttu-id="4fafd-111">O tamanho da página menor que 50, são tratados como 50 e o tamanho da página maior que 500 são limitados a 500.</span><span class="sxs-lookup"><span data-stu-id="4fafd-111">Page size less than 50, are treated as 50, and page size greater than 500, are capped at 500.</span></span> <span data-ttu-id="4fafd-112">Embora você ainda possa usar a versão não páginada, ela não será confiável em equipes grandes e não deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="4fafd-112">Although you may still use the non-paged version, it will be unreliable in large teams and should not be used.</span></span> <span data-ttu-id="4fafd-113">*Consulte* [Alterações nas APIs de Bot do Teams para buscar membros de equipe/chat](~/resources/team-chat-member-api-changes.md) para obter informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="4fafd-113">*See* [Changes to Teams Bot APIs for Fetching Team/Chat Members](~/resources/team-chat-member-api-changes.md) for additional information.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="4fafd-114">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="4fafd-114">C#/.NET</span></span>](#tab/dotnet)

```csharp
public class MyBot : TeamsActivityHandler
{
    protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
    {
        var members = new List<TeamsChannelAccount>();
        string continuationToken = null;

        do
        {
            var currentPage = await TeamsInfo.GetPagedMembersAsync(turnContext, 100, continuationToken, cancellationToken);
            continuationToken = currentPage.ContinuationToken;
            members.AddRange(currentPage.Members);
         }
         while (continuationToken != null);
     }
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="4fafd-115">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="4fafd-115">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();

        // See https://aka.ms/about-bot-activity-message to learn more about the message and other activity types.
        this.onMessage(async (turnContext, next) => {
            var continuationToken;
            var members = [];

            do {
                var pagedMembers = await TeamsInfo.getPagedMembers(context, 100, continuationToken);
                continuationToken = pagedMembers.continuationToken;
                members.push(...pagedMembers.members);
            }
            while(continuationToken !== undefined)

            // By calling next() you ensure that the next BotHandler is run.
            await next();
        });
    }
}
```

# <a name="python"></a>[<span data-ttu-id="4fafd-116">Python</span><span class="sxs-lookup"><span data-stu-id="4fafd-116">Python</span></span>](#tab/python)

```python
async def _show_members(
    self, turn_context: TurnContext
):
    members = await TeamsInfo.get_team_members(turn_context)
```

# <a name="json"></a>[<span data-ttu-id="4fafd-117">JSON</span><span class="sxs-lookup"><span data-stu-id="4fafd-117">JSON</span></span>](#tab/json)

<span data-ttu-id="4fafd-118">Você pode emitir diretamente uma solicitação GET em `/v3/conversations/{conversationId}/pagedmembers?pageSize={pageSize}&continuationToken={continuationToken}` , usando o valor de como ponto de `serviceUrl` extremidade.</span><span class="sxs-lookup"><span data-stu-id="4fafd-118">You can directly issue a GET request on `/v3/conversations/{conversationId}/pagedmembers?pageSize={pageSize}&continuationToken={continuationToken}`, using the value of `serviceUrl` as the endpoint.</span></span> <span data-ttu-id="4fafd-119">O valor de `serviceUrl` tende a ser estável, mas pode mudar.</span><span class="sxs-lookup"><span data-stu-id="4fafd-119">The value of `serviceUrl` tends to be stable but can change.</span></span> <span data-ttu-id="4fafd-120">Quando uma nova mensagem chega, seu bot deve verificar seu valor armazenado para `serviceUrl` .</span><span class="sxs-lookup"><span data-stu-id="4fafd-120">When a new message arrives, your bot should verify its stored value for `serviceUrl`.</span></span> <span data-ttu-id="4fafd-121">A carga de resposta também indicará se o usuário é um usuário regular ou anônimo.</span><span class="sxs-lookup"><span data-stu-id="4fafd-121">The response payload will also indicate if the user is a regular or anonymous user.</span></span>

```http
GET /v3/conversations/19:meeting_N2QzYTA3YmItYmMwOC00OTJmLThkYzMtZWMzZGU0NGIyZGI0@thread.v2/pagedmembers?pageSize=100&continuationToken=asdfasdfalkdsjfalksjdf

Response body
{
   "continuationToken":"asdfqwerueiqpiewr",
   "members":[
      {
         "id":"29:1GcS4EyB_oSI8A88XmWBN7NJFyMqe3QGnJdgLfFGkJnVelzRGos0bPbpsfJjcbAD22bmKc4GMbrY2g4JDrrA8vM06X1-cHHle4zOE6U4ttcc",
         "name":"Anon1 (Guest)",
         "tenantId":"29:1UX7p8Fkx7p93MZlBFS71swTB9juQOCfnXf2L3wxOUITCcIGpFcRX-JiFjLDVZhxGpEfzSTGNsZeEyTKr1iu3Vw",
         "userRole":"anonymous"
      },
      {
         "id":"29:1bSnHZ7Js2STWrgk6ScEErLk1Lp2zQuD5H2qQ960rtvstKp8tKLl-3r8b6DoW0QxZimuTxk_kupZ1DBMpvIQQUAZL-PNj0EORDvRZXy8kvWk",
         "objectId":"76b0b09f-d410-48fd-993e-84da521a597b",
         "givenName":"John",
         "surname":"Patterson",
         "email":"johnp@fabrikam.com",
         "userPrincipalName":"johnp@fabrikam.com",
         "tenantId":"29:1UX7p8Fkx7p93MZlBFS71swTB9juQOCfnXf2L3wxOUITCcIGpFcRX-JiFjLDVZhxGpEfzSTGNsZeEyTKr1iu3Vw",
         "userRole":"user"
      },
      {
         "id":"29:1URzNQM1x1PNMr1D7L5_lFe6qF6gEfAbkdG8_BUxOW2mTKryQqEZtBTqDt10-MghkzjYDuUj4KG6nvg5lFAyjOLiGJ4jzhb99WrnI7XKriCs",
         "objectId":"6b7b3b2a-2c4b-4175-8582-41c9e685c1b5",
         "givenName":"Rick",
         "surname":"Stevens",
         "email":"Rick.Stevens@fabrikam.com",
         "userPrincipalName":"rstevens@fabrikam.com",
         "tenantId":"29:1UX7p8Fkx7p93MZlBFS71swTB9juQOCfnXf2L3wxOUITCcIGpFcRX-JiFjLDVZhxGpEfzSTGNsZeEyTKr1iu3Vw",
         "userRole":"user"
      }
   ]
}
```

* * *

## <a name="get-single-member-details"></a><span data-ttu-id="4fafd-122">Obter detalhes de membro único</span><span class="sxs-lookup"><span data-stu-id="4fafd-122">Get single member details</span></span>

<span data-ttu-id="4fafd-123">Você também pode recuperar os detalhes de um usuário específico usando sua ID de usuário, UPN ou Id de objeto AAD do Teams.</span><span class="sxs-lookup"><span data-stu-id="4fafd-123">You can also retrieve the details of a particular user using their Teams user Id, UPN, or AAD Object Id.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="4fafd-124">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="4fafd-124">C#/.NET</span></span>](#tab/dotnet)

```csharp
public class MyBot : TeamsActivityHandler
{
    protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
    {
        var member = await TeamsInfo.GetMemberAsync(turnContext, turnContext.Activity.From.Id, cancellationToken);
    }
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="4fafd-125">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="4fafd-125">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();

        // See https://aka.ms/about-bot-activity-message to learn more about the message and other activity types.
        const member = await TeamsInfo.getMember(context, encodeURI('someone@somecompany.com'));

        // By calling next() you ensure that the next BotHandler is run.
        await next();
        });
    }
}
```

# <a name="python"></a>[<span data-ttu-id="4fafd-126">Python</span><span class="sxs-lookup"><span data-stu-id="4fafd-126">Python</span></span>](#tab/python)

```python
async def _show_members(
    self, turn_context: TurnContext
):
    member = TeamsInfo.get_member(turn_context, turn_context.activity.from_property.id)
```

# <a name="json"></a>[<span data-ttu-id="4fafd-127">JSON</span><span class="sxs-lookup"><span data-stu-id="4fafd-127">JSON</span></span>](#tab/json)

<span data-ttu-id="4fafd-128">Você pode emitir diretamente uma solicitação GET em `/v3/conversations/{conversationId}/members/{userId}` , usando o valor de como ponto de `serviceUrl` extremidade.</span><span class="sxs-lookup"><span data-stu-id="4fafd-128">You can directly issue a GET request on `/v3/conversations/{conversationId}/members/{userId}`, using the value of `serviceUrl` as the endpoint.</span></span> <span data-ttu-id="4fafd-129">O valor de `serviceUrl` tende a ser estável, mas pode mudar.</span><span class="sxs-lookup"><span data-stu-id="4fafd-129">The value of `serviceUrl` tends to be stable but can change.</span></span> <span data-ttu-id="4fafd-130">Quando uma nova mensagem chega, seu bot deve verificar seu valor armazenado para `serviceUrl` .</span><span class="sxs-lookup"><span data-stu-id="4fafd-130">When a new message arrives, your bot should verify its stored value for `serviceUrl`.</span></span> <span data-ttu-id="4fafd-131">Isso pode ser usado para usuários regulares e usuários anônimos.</span><span class="sxs-lookup"><span data-stu-id="4fafd-131">This can be used for regular users and anonymous users.</span></span>

<span data-ttu-id="4fafd-132">Abaixo está um exemplo de resposta para o usuário normal</span><span class="sxs-lookup"><span data-stu-id="4fafd-132">Below is a response sample for regular user</span></span>

```http
GET /v3/conversations/19:ja0cu120i1jod12j@skype.net/members/29:1GcS4EyB_oSI8A88XmWBN7NJFyMqe3QGnJdgLfFGkJnVelzRGos0bPbpsfJjcbAD22bmKc4GMbrY2g4JDrrA8vM06X1-cHHle4zOE6U4ttcc

Response body
{
    "id": "29:1GcS4EyB_oSI8A88XmWBN7NJFyMqe3QGnJdgLfFGkJnVelzRGos0bPbpsfJjcbAD22bmKc4GMbrY2g4JDrrA8vM06X1-cHHle4zOE6U4ttcc",
    "objectId": "9d3e08f9-a7ae-43aa-a4d3-de3f319a8a9c",
    "givenName": "Larry",
    "surname": "Brown",
    "email": "Larry.Brown@fabrikam.com",
    "userPrincipalName": "labrown@fabrikam.com",
    "tenantId":"72f988bf-86f1-41af-91ab-2d7cd011db47", 
    "userRole":"user"
}
```

<span data-ttu-id="4fafd-133">Abaixo está a resposta para usuário anônimo</span><span class="sxs-lookup"><span data-stu-id="4fafd-133">Below is response for anonymous user</span></span>

```http
GET /v3/conversations/19:ja0cu120i1jod12j@skype.net/members/<anonymous user id>"

Response body
{
    "id": "29:1GcS4EyB_oSI8A88XmWBN7NJFyMqe3QGnJdgLfFGkJnVelzRGos0bPbpsfJjcbAD22bmKc4GMbrY2g4JDrrA8vM06X1-cHHle4zOE6U4ttcc",
    "name": "Anon1 (Guest)",
    "tenantId":"72f988bf-86f1-41af-91ab-2d7cd011db47", 
    "userRole":"anonymous"
}
```

* * *

## <a name="get-teams-details"></a><span data-ttu-id="4fafd-134">Obter detalhes da equipe</span><span class="sxs-lookup"><span data-stu-id="4fafd-134">Get team's details</span></span>

<span data-ttu-id="4fafd-135">Quando instalado em uma equipe, seu bot pode consultar metadados sobre essa equipe, incluindo o groupId do Azure AD.</span><span class="sxs-lookup"><span data-stu-id="4fafd-135">When installed in a team, your bot can query for metadata about that team including the Azure AD groupId.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="4fafd-136">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="4fafd-136">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="4fafd-137">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="4fafd-137">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="4fafd-138">Python</span><span class="sxs-lookup"><span data-stu-id="4fafd-138">Python</span></span>](#tab/python)

```python
async def _show_details(self, turn_context: TurnContext):
    team_details = await TeamsInfo.get_team_details(turn_context)
    reply = MessageFactory.text(f"The team name is {team_details.name}. The team ID is {team_details.id}. The AADGroupID is {team_details.aad_group_id}.")
    await turn_context.send_activity(reply)
```

# <a name="json"></a>[<span data-ttu-id="4fafd-139">JSON</span><span class="sxs-lookup"><span data-stu-id="4fafd-139">JSON</span></span>](#tab/json)

<span data-ttu-id="4fafd-140">Você pode emitir diretamente uma solicitação GET em `/v3/teams/{teamId}` , usando o valor de como ponto de `serviceUrl` extremidade.</span><span class="sxs-lookup"><span data-stu-id="4fafd-140">You can directly issue a GET request on `/v3/teams/{teamId}`, using the value of `serviceUrl` as the endpoint.</span></span> <span data-ttu-id="4fafd-141">O valor de `serviceUrl` tende a ser estável, mas pode mudar.</span><span class="sxs-lookup"><span data-stu-id="4fafd-141">The value of `serviceUrl` tends to be stable but can change.</span></span> <span data-ttu-id="4fafd-142">Quando uma nova mensagem chega, seu bot deve verificar seu valor armazenado para `serviceUrl` .</span><span class="sxs-lookup"><span data-stu-id="4fafd-142">When a new message arrives, your bot should verify its stored value for `serviceUrl`.</span></span>

```http
GET /v3/teams/19:ja0cu120i1jod12j@skype.net

Response body
{
    "id": "29:1GcS4EyB_oSI8A88XmWBN7NJFyMqe3QGnJdgLfFGkJnVelzRGos0bPbpsfJjcbAD22bmKc4GMbrY2g4JDrrA8vM06X1-cHHle4zOE6U4ttcc",
    "name": "The Team Name",
    "aadGroupId": "02ce3874-dd86-41ba-bddc-013f34019978"
}
```

* * *

## <a name="get-the-list-of-channels-in-a-team"></a><span data-ttu-id="4fafd-143">Obter a lista de canais em uma equipe</span><span class="sxs-lookup"><span data-stu-id="4fafd-143">Get the list of channels in a team</span></span>

<span data-ttu-id="4fafd-144">Seu bot pode consultar a lista de canais em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="4fafd-144">Your bot can query the list of channels in a team.</span></span>

> [!NOTE]
>
>* <span data-ttu-id="4fafd-145">O nome do canal Geral padrão é retornado para `null` permitir a localização.</span><span class="sxs-lookup"><span data-stu-id="4fafd-145">The name of the default General channel is returned as `null` to allow for localization.</span></span>
>* <span data-ttu-id="4fafd-146">A ID do canal para o canal Geral sempre corresponde à ID da equipe.</span><span class="sxs-lookup"><span data-stu-id="4fafd-146">The channel ID for the General channel always matches the team ID.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="4fafd-147">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="4fafd-147">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="4fafd-148">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="4fafd-148">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="4fafd-149">Python</span><span class="sxs-lookup"><span data-stu-id="4fafd-149">Python</span></span>](#tab/python)

```python
async def _show_channels(
    self, turn_context: TurnContext
):
    channels = await TeamsInfo.get_team_channels(turn_context)
    reply = MessageFactory.text(f"Total of {len(channels)} channels are currently in team")
    await turn_context.send_activity(reply)
```

# <a name="json"></a>[<span data-ttu-id="4fafd-150">JSON</span><span class="sxs-lookup"><span data-stu-id="4fafd-150">JSON</span></span>](#tab/json)

<span data-ttu-id="4fafd-151">Você pode emitir diretamente uma solicitação GET em `/v3/teams/{teamId}/conversations` , usando o valor de como ponto de `serviceUrl` extremidade.</span><span class="sxs-lookup"><span data-stu-id="4fafd-151">You can directly issue a GET request on `/v3/teams/{teamId}/conversations`, using the value of `serviceUrl` as the endpoint.</span></span> <span data-ttu-id="4fafd-152">O valor de `serviceUrl` tende a ser estável, mas pode mudar.</span><span class="sxs-lookup"><span data-stu-id="4fafd-152">The value of `serviceUrl` tends to be stable but can change.</span></span> <span data-ttu-id="4fafd-153">Quando uma nova mensagem chega, seu bot deve verificar seu valor armazenado para `serviceUrl` .</span><span class="sxs-lookup"><span data-stu-id="4fafd-153">When a new message arrives, your bot should verify its stored value for `serviceUrl`.</span></span>

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

* * *

[!INCLUDE [sample](~/includes/bots/teams-bot-samples.md)]
