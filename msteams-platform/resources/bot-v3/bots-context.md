---
title: Obter contexto para o bot
description: Descreve como obter contexto para bots no Microsoft Teams
keywords: contexto de bots do teams
ms.date: 05/20/2019
ms.openlocfilehash: 2dea6fd51e7274fa899d9ae882441a21618d7e09
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672938"
---
# <a name="get-context-for-your-microsoft-teams-bot"></a><span data-ttu-id="d00c1-104">Obter contexto para o bot do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="d00c1-104">Get context for your Microsoft Teams bot</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="d00c1-105">Seu bot pode acessar contexto adicional sobre a equipe ou chat, como perfil de usuário.</span><span class="sxs-lookup"><span data-stu-id="d00c1-105">Your bot can access additional context about the team or chat, such as user profile.</span></span> <span data-ttu-id="d00c1-106">Essas informações podem ser usadas para enriquecer a funcionalidade do seu bot e fornecer uma experiência mais personalizada.</span><span class="sxs-lookup"><span data-stu-id="d00c1-106">This information can be used to enrich your bot's functionality and provide a more personalized experience.</span></span>

> [!NOTE]
> <span data-ttu-id="d00c1-107">Essas APIs de&ndash;bot específicas do Microsoft Teams são mais bem acessadas por meio de nossas extensões para o SDK do bot Builder.</span><span class="sxs-lookup"><span data-stu-id="d00c1-107">These Microsoft Teams&ndash;specific bot APIs are best accessed through our extensions for the Bot Builder SDK.</span></span> <span data-ttu-id="d00c1-108">Para o C#/.NET, baixe [o pacote NuGet Microsoft. bot. Connector. Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) .</span><span class="sxs-lookup"><span data-stu-id="d00c1-108">For C#/.NET, download our [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet package.</span></span> <span data-ttu-id="d00c1-109">Para o desenvolvimento de Node. js, você pode instalar o pacote [botbuilder-Teams](https://www.npmjs.com/package/botbuilder-teams) NPM.</span><span class="sxs-lookup"><span data-stu-id="d00c1-109">For Node.js development, you can install the [botbuilder-teams](https://www.npmjs.com/package/botbuilder-teams) npm package.</span></span> <span data-ttu-id="d00c1-110">O construtor de bot de destino do SDKs v3.</span><span class="sxs-lookup"><span data-stu-id="d00c1-110">Both SDKs target Bot Builder v3.</span></span>

## <a name="fetching-the-team-roster"></a><span data-ttu-id="d00c1-111">Buscando a lista de equipes</span><span class="sxs-lookup"><span data-stu-id="d00c1-111">Fetching the team roster</span></span>

<span data-ttu-id="d00c1-112">O bot pode consultar a lista de membros da equipe e seus perfis básicos, que inclui as IDs de usuário do Teams e as informações do Azure Active Directory (Azure AD), como nome e objectId.</span><span class="sxs-lookup"><span data-stu-id="d00c1-112">Your bot can query for the list of team members and their basic profiles, which includes Teams user IDs and Azure Active Directory (Azure AD) information such as name and objectId.</span></span> <span data-ttu-id="d00c1-113">Você pode usar essas informações para correlacionar as identidades do usuário; por exemplo, para verificar se um usuário conectado a uma guia por meio de credenciais do Azure AD é um membro da equipe.</span><span class="sxs-lookup"><span data-stu-id="d00c1-113">You can use this information to correlate user identities; for example, to check whether a user logged into a tab through Azure AD credentials is a member of the team.</span></span>

### <a name="rest-api-example"></a><span data-ttu-id="d00c1-114">Exemplo de API REST</span><span class="sxs-lookup"><span data-stu-id="d00c1-114">REST API example</span></span>

<span data-ttu-id="d00c1-115">Você pode emitir diretamente uma solicitação GET no [`/conversations/{teamId}/members/`](/bot-framework/rest-api/bot-framework-rest-connector-api-reference#get-conversation-members), usando o valor de `serviceUrl` como ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="d00c1-115">You can directly issue a GET request on [`/conversations/{teamId}/members/`](/bot-framework/rest-api/bot-framework-rest-connector-api-reference#get-conversation-members), using the value of `serviceUrl` as the endpoint.</span></span>

<span data-ttu-id="d00c1-116">O `teamId` pode ser encontrado no `channeldata` objeto da carga de atividade que seu bot recebe nos seguintes cenários:</span><span class="sxs-lookup"><span data-stu-id="d00c1-116">The `teamId` can be found in the `channeldata` object of the activity payload that your bot receives in the following scenarios:</span></span>
* <span data-ttu-id="d00c1-117">Quando um usuário mensagens ou interage com seu bot em um contexto de equipe (consulte [recebendo mensagens](~/resources/bot-v3/bot-conversations/bots-conversations.md#receiving-messages))</span><span class="sxs-lookup"><span data-stu-id="d00c1-117">When a user messages or interacts with your bot in a team context (see [Receiving Messages](~/resources/bot-v3/bot-conversations/bots-conversations.md#receiving-messages))</span></span>
* <span data-ttu-id="d00c1-118">Quando um novo usuário ou bot é adicionado a uma equipe (consulte [bot ou User Added to a Team](~/resources/bot-v3/bots-notifications.md#bot-or-user-added-to-a-team))</span><span class="sxs-lookup"><span data-stu-id="d00c1-118">When a new user or bot is added to a team (see [Bot or user added to a team](~/resources/bot-v3/bots-notifications.md#bot-or-user-added-to-a-team))</span></span>

> [!NOTE]
>* <span data-ttu-id="d00c1-119">Certifique-se de usar a ID da equipe ao chamar a API</span><span class="sxs-lookup"><span data-stu-id="d00c1-119">Make sure to use the team id when calling the api</span></span>
>* <span data-ttu-id="d00c1-120">O valor de `serviceUrl` tende a ser estável, mas pode ser alterado.</span><span class="sxs-lookup"><span data-stu-id="d00c1-120">The value of `serviceUrl` tends to be stable but can change.</span></span> <span data-ttu-id="d00c1-121">Quando uma nova mensagem chega, seu bot deve verificar seu valor armazenado de `serviceUrl`.</span><span class="sxs-lookup"><span data-stu-id="d00c1-121">When a new message arrives, your bot should verify its stored value of `serviceUrl`.</span></span>

```json
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

### <a name="net-example"></a><span data-ttu-id="d00c1-122">Exemplo .NET</span><span class="sxs-lookup"><span data-stu-id="d00c1-122">.NET example</span></span>

<span data-ttu-id="d00c1-123">Chamar `GetConversationMembersAsync` usando `Team.Id` para retornar uma lista de IDs de usuário.</span><span class="sxs-lookup"><span data-stu-id="d00c1-123">Call `GetConversationMembersAsync` using `Team.Id` to return a list of user IDs.</span></span>

```csharp
// Fetch the members in the current conversation
var connector = new ConnectorClient(new Uri(context.Activity.ServiceUrl));
var teamId = context.Activity.GetChannelData<TeamsChannelData>().Team.Id;
var members = await connector.Conversations.GetConversationMembersAsync(teamId);

// Concatenate information about all members into a string
var sb = new StringBuilder();
foreach (var member in members.AsTeamsChannelAccounts())
{
    sb.AppendFormat(
        "GivenName = {0}, TeamsMemberId = {1}",
        member.Name, member.Id);

    sb.AppendLine();
}

// Post the member info back into the conversation
await context.PostAsync($"People in this conversation: {sb.ToString()}");
```

### <a name="nodejstypescript-example"></a><span data-ttu-id="d00c1-124">Exemplo de Node. js/TypeScript</span><span class="sxs-lookup"><span data-stu-id="d00c1-124">Node.js/TypeScript example</span></span>

<span data-ttu-id="d00c1-125">O exemplo a seguir usa as [extensões do Microsoft Teams para o SDK do bot Builder para node. js](https://www.npmjs.com/package/botbuilder-teams).</span><span class="sxs-lookup"><span data-stu-id="d00c1-125">The following example uses the [Microsoft Teams extensions for the Bot Builder SDK for Node.js](https://www.npmjs.com/package/botbuilder-teams).</span></span>

```typescript

[...]
import * as builder from "botbuilder";
[...]

var teamId = session.message.sourceEvent.team.id;
connector.fetchMembers(
  (<builder.IChatConnectorAddress>session.message.address).serviceUrl,
  teamId,
  (err, result) => {
    if (err) {
      session.endDialog('There is some error');
    }
    else {
      session.endDialog('%s', JSON.stringify(result));
    }
  }
);
```

## <a name="fetching-user-profile-or-roster-in-personal-or-group-chat"></a><span data-ttu-id="d00c1-126">Buscando perfil de usuário ou lista no chat de grupo ou pessoal</span><span class="sxs-lookup"><span data-stu-id="d00c1-126">Fetching user profile or roster in personal or group chat</span></span>

<span data-ttu-id="d00c1-127">Você também pode fazer a mesma chamada de API para qualquer chat pessoal para obter as informações de perfil do usuário batendo papo com seu bot.</span><span class="sxs-lookup"><span data-stu-id="d00c1-127">You can also make the same API call for any personal chat to obtain the profile information of the user chatting with your bot.</span></span>

<span data-ttu-id="d00c1-128">Os métodos de chamada de API e SDK são idênticos para buscar a lista de equipes, como é o objeto de resposta.</span><span class="sxs-lookup"><span data-stu-id="d00c1-128">The API call and SDK methods are identical to fetching the team roster, as is the response object.</span></span> <span data-ttu-id="d00c1-129">A única diferença é passar no `conversationId` lugar do. `teamId`</span><span class="sxs-lookup"><span data-stu-id="d00c1-129">The only difference is you pass the `conversationId` instead of the `teamId`.</span></span>

## <a name="fetching-the-list-of-channels-in-a-team"></a><span data-ttu-id="d00c1-130">Buscando a lista de canais em uma equipe</span><span class="sxs-lookup"><span data-stu-id="d00c1-130">Fetching the list of channels in a team</span></span>

<span data-ttu-id="d00c1-131">O bot pode consultar a lista de canais de uma equipe.</span><span class="sxs-lookup"><span data-stu-id="d00c1-131">Your bot can query the list of channels in a team.</span></span>

> [!NOTE]
>
>* <span data-ttu-id="d00c1-132">O nome do canal geral padrão é retornado como `null` permitir para localização.</span><span class="sxs-lookup"><span data-stu-id="d00c1-132">The name of the default General channel is returned as `null` to allow for localization.</span></span>
>* <span data-ttu-id="d00c1-133">A ID do canal geral sempre corresponde à ID da equipe.</span><span class="sxs-lookup"><span data-stu-id="d00c1-133">The channel ID for the General channel always matches the team ID.</span></span>

### <a name="rest-api-example"></a><span data-ttu-id="d00c1-134">Exemplo de API REST</span><span class="sxs-lookup"><span data-stu-id="d00c1-134">REST API example</span></span>

<span data-ttu-id="d00c1-135">Você pode emitir diretamente uma solicitação GET no `/teams/{teamId}/conversations/`, usando o valor de `serviceUrl` como ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="d00c1-135">You can directly issue a GET request on `/teams/{teamId}/conversations/`, using the value of `serviceUrl` as the endpoint.</span></span>

<span data-ttu-id="d00c1-136">A única fonte de `teamId` é uma mensagem do contexto da equipe-uma mensagem de um usuário ou a mensagem que seu bot recebe quando é adicionada a uma equipe (consulte [bot ou User Added to a Team](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition)).</span><span class="sxs-lookup"><span data-stu-id="d00c1-136">The only source for `teamId` is a message from the team context - either a message from a user or the message that your bot receives when it is added to a team (see [Bot or user added to a team](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition)).</span></span>

> [!NOTE]
> <span data-ttu-id="d00c1-137">O valor de `serviceUrl` tende a ser estável, mas pode ser alterado.</span><span class="sxs-lookup"><span data-stu-id="d00c1-137">The value of `serviceUrl` tends to be stable but can change.</span></span> <span data-ttu-id="d00c1-138">Quando uma nova mensagem chega, seu bot deve verificar seu valor armazenado de `serviceUrl`.</span><span class="sxs-lookup"><span data-stu-id="d00c1-138">When a new message arrives, your bot should verify its stored value of `serviceUrl`.</span></span>

```json
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

#### <a name="net-example"></a><span data-ttu-id="d00c1-139">Exemplo .NET</span><span class="sxs-lookup"><span data-stu-id="d00c1-139">.NET example</span></span>

<span data-ttu-id="d00c1-140">O exemplo a seguir usa `FetchChannelList` a chamada das [extensões do Microsoft Teams para o SDK do bot Builder para .net](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams):</span><span class="sxs-lookup"><span data-stu-id="d00c1-140">The following example uses the `FetchChannelList` call from the [Microsoft Teams extensions for the Bot Builder SDK for .NET](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams):</span></span>

```csharp
ConversationList channels = client.GetTeamsConnectorClient().Teams.FetchChannelList(activity.GetChannelData<TeamsChannelData>().Team.Id);
```

#### <a name="nodejs-example"></a><span data-ttu-id="d00c1-141">Exemplo do node. js</span><span class="sxs-lookup"><span data-stu-id="d00c1-141">Node.js example</span></span>

<span data-ttu-id="d00c1-142">O exemplo a seguir `fetchChannelList` usa a chamada das [extensões do Microsoft Teams para o SDK do Configurador de bot para node. js](https://www.npmjs.com/package/botbuilder-teams).</span><span class="sxs-lookup"><span data-stu-id="d00c1-142">The following example uses `fetchChannelList` call from the [Microsoft Teams extensions for the Bot Builder SDK for Node.js](https://www.npmjs.com/package/botbuilder-teams).</span></span>

```javascript
var teamId = session.message.sourceEvent.team.id;
connector.fetchChannelList(
  (session.message.address).serviceUrl,
  teamId,
  (err, result) => {
    if (err) {
      session.endDialog('There is an error');
    }
    else {
      session.endDialog('%s', JSON.stringify(result));
    }
  }
);
```
