---
title: Obter Teams contexto específico para seu bot
author: laujan
description: Como obter o contexto específico do Microsoft Team para seu bot, incluindo a lista de canais, detalhes e lista de conversas.
ms.topic: conceptual
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: 6a8f903fb2f3ed8120e31b7536b65f22fdf6d620
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2021
ms.locfileid: "52630163"
---
# <a name="get-teams-specific-context-for-your-bot"></a><span data-ttu-id="0d050-103">Obter Teams contexto específico para seu bot</span><span class="sxs-lookup"><span data-stu-id="0d050-103">Get Teams specific context for your bot</span></span>

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

<span data-ttu-id="0d050-104">Um bot pode acessar dados de contexto adicionais sobre uma equipe ou chat em que está instalado.</span><span class="sxs-lookup"><span data-stu-id="0d050-104">A bot can access additional context data about a team or chat where it is installed.</span></span> <span data-ttu-id="0d050-105">Essas informações podem ser usadas para enriquecer a funcionalidade do bot e fornecer uma experiência mais personalizada.</span><span class="sxs-lookup"><span data-stu-id="0d050-105">This information can be used to enrich the bot's functionality and provide a more personalized experience.</span></span>

## <a name="fetch-the-roster-or-user-profile"></a><span data-ttu-id="0d050-106">Buscar a lista ou o perfil de usuário</span><span class="sxs-lookup"><span data-stu-id="0d050-106">Fetch the roster or user profile</span></span>

<span data-ttu-id="0d050-107">Seu bot pode consultar a lista de membros e seus perfis de usuário básicos, incluindo Teams IDs de usuário e informações Azure Active Directory (AAD), como nome e objectId.</span><span class="sxs-lookup"><span data-stu-id="0d050-107">Your bot can query for the list of members and their basic user profiles, including Teams user IDs and Azure Active Directory (AAD) information, such as name and objectId.</span></span> <span data-ttu-id="0d050-108">Você pode usar essas informações para correlacionar identidades de usuário.</span><span class="sxs-lookup"><span data-stu-id="0d050-108">You can use this information to correlate user identities.</span></span> <span data-ttu-id="0d050-109">Por exemplo, para verificar se um usuário conectado a uma guia por meio de credenciais do AAD é membro da equipe.</span><span class="sxs-lookup"><span data-stu-id="0d050-109">For example, to check whether a user logged into a tab through AAD credentials, is a member of the team.</span></span> <span data-ttu-id="0d050-110">Para obter membros da conversa, o tamanho mínimo ou máximo da página depende da implementação.</span><span class="sxs-lookup"><span data-stu-id="0d050-110">For get conversation members, minimum or maximum page size depends on the implementation.</span></span> <span data-ttu-id="0d050-111">O tamanho da página menor que 50, são tratados como 50 e maiores que 500 são limitados a 500.</span><span class="sxs-lookup"><span data-stu-id="0d050-111">Page size less than 50, are treated as 50, and greater than 500, are capped at 500.</span></span> <span data-ttu-id="0d050-112">Mesmo que você use a versão não páginada, ela não é confiável em equipes grandes e não deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="0d050-112">Even if you use the non-paged version, it is unreliable in large teams and must not be used.</span></span> <span data-ttu-id="0d050-113">Para obter mais informações, consulte [changes to Teams Bot APIs for fetching team or chat members](~/resources/team-chat-member-api-changes.md).</span><span class="sxs-lookup"><span data-stu-id="0d050-113">For more information, see [changes to Teams Bot APIs for fetching team or chat members](~/resources/team-chat-member-api-changes.md).</span></span>

<span data-ttu-id="0d050-114">O código de exemplo a seguir usa o ponto de extremidade pagedo para buscar a lista:</span><span class="sxs-lookup"><span data-stu-id="0d050-114">The following sample code uses the paged endpoint for fetching the roster:</span></span>

# <a name="c"></a>[<span data-ttu-id="0d050-115">C#</span><span class="sxs-lookup"><span data-stu-id="0d050-115">C#</span></span>](#tab/dotnet)

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

# <a name="typescript"></a>[<span data-ttu-id="0d050-116">TypeScript</span><span class="sxs-lookup"><span data-stu-id="0d050-116">TypeScript</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="0d050-117">Python</span><span class="sxs-lookup"><span data-stu-id="0d050-117">Python</span></span>](#tab/python)

```python
async def _show_members(
    self, turn_context: TurnContext
):
    members = await TeamsInfo.get_team_members(turn_context)
```

# <a name="json"></a>[<span data-ttu-id="0d050-118">JSON</span><span class="sxs-lookup"><span data-stu-id="0d050-118">JSON</span></span>](#tab/json)

<span data-ttu-id="0d050-119">Você pode emitir diretamente uma solicitação GET em `/v3/conversations/{conversationId}/pagedmembers?pageSize={pageSize}&continuationToken={continuationToken}` , usando o valor de como ponto de `serviceUrl` extremidade.</span><span class="sxs-lookup"><span data-stu-id="0d050-119">You can directly issue a GET request on `/v3/conversations/{conversationId}/pagedmembers?pageSize={pageSize}&continuationToken={continuationToken}`, using the value of `serviceUrl` as the endpoint.</span></span> <span data-ttu-id="0d050-120">O valor de `serviceUrl` é estável, mas pode mudar.</span><span class="sxs-lookup"><span data-stu-id="0d050-120">The value of `serviceUrl` is stable but can change.</span></span> <span data-ttu-id="0d050-121">Quando uma nova mensagem chega, seu bot deve verificar seu valor armazenado para `serviceUrl` .</span><span class="sxs-lookup"><span data-stu-id="0d050-121">When a new message arrives, your bot must verify its stored value for `serviceUrl`.</span></span> <span data-ttu-id="0d050-122">A carga de resposta também indica se o usuário é um usuário regular ou anônimo.</span><span class="sxs-lookup"><span data-stu-id="0d050-122">The response payload also indicates if the user is a regular or anonymous user.</span></span>

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

<span data-ttu-id="0d050-123">Depois de buscar a lista ou o perfil de usuário, você pode obter detalhes de um único membro.</span><span class="sxs-lookup"><span data-stu-id="0d050-123">After you fetch the roster or user profile, you can get details of a single member.</span></span> <span data-ttu-id="0d050-124">Atualmente, para recuperar informações de um ou mais membros de um chat ou equipe, use as APIs de bot Microsoft Teams de C# ou para `TeamsInfo.GetMembersAsync` `TeamsInfo.getMembers` APIs TypeScript.</span><span class="sxs-lookup"><span data-stu-id="0d050-124">Currently, to retrieve information for one or more members of a chat or team, use the Microsoft Teams bot APIs `TeamsInfo.GetMembersAsync` for C# or `TeamsInfo.getMembers` for TypeScript APIs.</span></span>

## <a name="get-single-member-details"></a><span data-ttu-id="0d050-125">Obter detalhes de membro único</span><span class="sxs-lookup"><span data-stu-id="0d050-125">Get single member details</span></span>

<span data-ttu-id="0d050-126">Você também pode recuperar os detalhes de um usuário específico usando Teams ID de usuário, UPN ou ID de objeto AAD.</span><span class="sxs-lookup"><span data-stu-id="0d050-126">You can also retrieve the details of a particular user using their Teams user ID, UPN, or AAD Object ID.</span></span>

<span data-ttu-id="0d050-127">O código de exemplo a seguir é usado para obter detalhes de membro único:</span><span class="sxs-lookup"><span data-stu-id="0d050-127">The following sample code is used to get single member details:</span></span>

# <a name="c"></a>[<span data-ttu-id="0d050-128">C#</span><span class="sxs-lookup"><span data-stu-id="0d050-128">C#</span></span>](#tab/dotnet)

```csharp
public class MyBot : TeamsActivityHandler
{
    protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
    {
        var member = await TeamsInfo.GetMemberAsync(turnContext, turnContext.Activity.From.Id, cancellationToken);
    }
}
```

# <a name="typescript"></a>[<span data-ttu-id="0d050-129">TypeScript</span><span class="sxs-lookup"><span data-stu-id="0d050-129">TypeScript</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="0d050-130">Python</span><span class="sxs-lookup"><span data-stu-id="0d050-130">Python</span></span>](#tab/python)

```python
async def _show_members(
    self, turn_context: TurnContext
):
    member = await TeamsInfo.get_member(turn_context, turn_context.activity.from_property.id)
```

# <a name="json"></a>[<span data-ttu-id="0d050-131">JSON</span><span class="sxs-lookup"><span data-stu-id="0d050-131">JSON</span></span>](#tab/json)

<span data-ttu-id="0d050-132">Você pode emitir diretamente uma solicitação GET em `/v3/conversations/{conversationId}/members/{userId}` , usando o valor de como ponto de `serviceUrl` extremidade.</span><span class="sxs-lookup"><span data-stu-id="0d050-132">You can directly issue a GET request on `/v3/conversations/{conversationId}/members/{userId}`, using the value of `serviceUrl` as the endpoint.</span></span> <span data-ttu-id="0d050-133">O valor de `serviceUrl` é estável, mas pode mudar.</span><span class="sxs-lookup"><span data-stu-id="0d050-133">The value of `serviceUrl` is stable but can change.</span></span> <span data-ttu-id="0d050-134">Quando uma nova mensagem chega, seu bot deve verificar seu valor armazenado para `serviceUrl` .</span><span class="sxs-lookup"><span data-stu-id="0d050-134">When a new message arrives, your bot must verify its stored value for `serviceUrl`.</span></span> <span data-ttu-id="0d050-135">Isso pode ser usado para usuários regulares e usuários anônimos.</span><span class="sxs-lookup"><span data-stu-id="0d050-135">This can be used for regular users and anonymous users.</span></span>

<span data-ttu-id="0d050-136">Veja a seguir o exemplo de resposta para o usuário regular:</span><span class="sxs-lookup"><span data-stu-id="0d050-136">The following is the response sample for regular user:</span></span>

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

<span data-ttu-id="0d050-137">Veja a seguir o exemplo de resposta para o usuário anônimo:</span><span class="sxs-lookup"><span data-stu-id="0d050-137">The following is the response sample for anonymous user:</span></span>

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

<span data-ttu-id="0d050-138">Depois de obter detalhes de um único membro, você pode obter detalhes da equipe.</span><span class="sxs-lookup"><span data-stu-id="0d050-138">After you get details of a single member, you can get details of the team.</span></span> <span data-ttu-id="0d050-139">Atualmente, para recuperar informações de uma equipe, use as APIs Microsoft Teams bot para C# `TeamsInfo.GetMemberDetailsAsync` ou `TeamsInfo.getTeamDetails` para TypeScript.</span><span class="sxs-lookup"><span data-stu-id="0d050-139">Currently, to retrieve information for a team, use the Microsoft Teams bot APIs `TeamsInfo.GetMemberDetailsAsync` for C# or `TeamsInfo.getTeamDetails` for TypeScript.</span></span>

## <a name="get-teams-details"></a><span data-ttu-id="0d050-140">Obter detalhes da equipe</span><span class="sxs-lookup"><span data-stu-id="0d050-140">Get team's details</span></span>

<span data-ttu-id="0d050-141">Quando instalado em uma equipe, seu bot pode consultar metadados sobre essa equipe, incluindo a ID do grupo AAD.</span><span class="sxs-lookup"><span data-stu-id="0d050-141">When installed in a team, your bot can query for metadata about that team including the AAD group ID.</span></span>

<span data-ttu-id="0d050-142">O código de exemplo a seguir é usado para obter os detalhes da equipe:</span><span class="sxs-lookup"><span data-stu-id="0d050-142">The following sample code is used to get team's details:</span></span>

# <a name="c"></a>[<span data-ttu-id="0d050-143">C#</span><span class="sxs-lookup"><span data-stu-id="0d050-143">C#</span></span>](#tab/dotnet)

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

# <a name="typescript"></a>[<span data-ttu-id="0d050-144">TypeScript</span><span class="sxs-lookup"><span data-stu-id="0d050-144">TypeScript</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="0d050-145">Python</span><span class="sxs-lookup"><span data-stu-id="0d050-145">Python</span></span>](#tab/python)

```python
async def _show_details(self, turn_context: TurnContext):
    team_details = await TeamsInfo.get_team_details(turn_context)
    reply = MessageFactory.text(f"The team name is {team_details.name}. The team ID is {team_details.id}. The AADGroupID is {team_details.aad_group_id}.")
    await turn_context.send_activity(reply)
```

# <a name="json"></a>[<span data-ttu-id="0d050-146">JSON</span><span class="sxs-lookup"><span data-stu-id="0d050-146">JSON</span></span>](#tab/json)

<span data-ttu-id="0d050-147">Você pode emitir diretamente uma solicitação GET em `/v3/teams/{teamId}` , usando o valor de como ponto de `serviceUrl` extremidade.</span><span class="sxs-lookup"><span data-stu-id="0d050-147">You can directly issue a GET request on `/v3/teams/{teamId}`, using the value of `serviceUrl` as the endpoint.</span></span> <span data-ttu-id="0d050-148">O valor de `serviceUrl` é estável, mas pode mudar.</span><span class="sxs-lookup"><span data-stu-id="0d050-148">The value of `serviceUrl` is stable but can change.</span></span> <span data-ttu-id="0d050-149">Quando uma nova mensagem chega, seu bot deve verificar seu valor armazenado para `serviceUrl` .</span><span class="sxs-lookup"><span data-stu-id="0d050-149">When a new message arrives, your bot must verify its stored value for `serviceUrl`.</span></span>

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

<span data-ttu-id="0d050-150">Depois de obter detalhes da equipe, você pode obter a lista de canais em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="0d050-150">After you get details of the team, you can get the list of channels in a team.</span></span> <span data-ttu-id="0d050-151">Atualmente, para recuperar informações de uma lista de canais em uma equipe, use as APIs Microsoft Teams bot para C# ou para `TeamsInfo.GetTeamChannelsAsync` `TeamsInfo.getTeamChannels` APIs TypeScript.</span><span class="sxs-lookup"><span data-stu-id="0d050-151">Currently, to retrieve information for a list of channels in a team, use the Microsoft Teams bot APIs `TeamsInfo.GetTeamChannelsAsync` for C# or `TeamsInfo.getTeamChannels` for TypeScript APIs.</span></span>

## <a name="get-the-list-of-channels-in-a-team"></a><span data-ttu-id="0d050-152">Obter a lista de canais em uma equipe</span><span class="sxs-lookup"><span data-stu-id="0d050-152">Get the list of channels in a team</span></span>

<span data-ttu-id="0d050-153">Seu bot pode consultar a lista de canais em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="0d050-153">Your bot can query the list of channels in a team.</span></span>

> [!NOTE]
> * <span data-ttu-id="0d050-154">O nome do canal Geral padrão é retornado para `null` permitir a localização.</span><span class="sxs-lookup"><span data-stu-id="0d050-154">The name of the default General channel is returned as `null` to allow for localization.</span></span>
> * <span data-ttu-id="0d050-155">A ID do canal para o canal Geral sempre corresponde à ID da equipe.</span><span class="sxs-lookup"><span data-stu-id="0d050-155">The channel ID for the General channel always matches the team ID.</span></span>

<span data-ttu-id="0d050-156">O código de exemplo a seguir é usado para obter a lista de canais em uma equipe:</span><span class="sxs-lookup"><span data-stu-id="0d050-156">The following sample code is used to get the list of channels in a team:</span></span>

# <a name="c"></a>[<span data-ttu-id="0d050-157">C#</span><span class="sxs-lookup"><span data-stu-id="0d050-157">C#</span></span>](#tab/dotnet)

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

# <a name="typescript"></a>[<span data-ttu-id="0d050-158">TypeScript</span><span class="sxs-lookup"><span data-stu-id="0d050-158">TypeScript</span></span>](#tab/typescript)

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

# <a name="python"></a>[<span data-ttu-id="0d050-159">Python</span><span class="sxs-lookup"><span data-stu-id="0d050-159">Python</span></span>](#tab/python)

```python
async def _show_channels(
    self, turn_context: TurnContext
):
    channels = await TeamsInfo.get_team_channels(turn_context)
    reply = MessageFactory.text(f"Total of {len(channels)} channels are currently in team")
    await turn_context.send_activity(reply)
```

# <a name="json"></a>[<span data-ttu-id="0d050-160">JSON</span><span class="sxs-lookup"><span data-stu-id="0d050-160">JSON</span></span>](#tab/json)

<span data-ttu-id="0d050-161">Você pode emitir diretamente uma solicitação GET em `/v3/teams/{teamId}/conversations` , usando o valor de como ponto de `serviceUrl` extremidade.</span><span class="sxs-lookup"><span data-stu-id="0d050-161">You can directly issue a GET request on `/v3/teams/{teamId}/conversations`, using the value of `serviceUrl` as the endpoint.</span></span> <span data-ttu-id="0d050-162">O valor de `serviceUrl` é estável, mas pode mudar.</span><span class="sxs-lookup"><span data-stu-id="0d050-162">The value of `serviceUrl` is stable but can change.</span></span> <span data-ttu-id="0d050-163">Quando uma nova mensagem chega, seu bot deve verificar seu valor armazenado para `serviceUrl` .</span><span class="sxs-lookup"><span data-stu-id="0d050-163">When a new message arrives, your bot must verify its stored value for `serviceUrl`.</span></span>

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

## <a name="next-step"></a><span data-ttu-id="0d050-164">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="0d050-164">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0d050-165">Enviar e receber arquivos por meio do bot</span><span class="sxs-lookup"><span data-stu-id="0d050-165">Send and receive files through the bot</span></span>](~/bots/how-to/bots-filesv4.md)
