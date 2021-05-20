---
title: Obtenha contexto para o seu bot Microsoft Teams
description: Descreve como obter contexto para bots em Microsoft Teams
keywords: contexto de bots equipes
ms.topic: conceptual
localization_priority: Normal
ms.date: 05/20/2019
ms.openlocfilehash: cda2e24816330964342b097f52bb955c8846c54a
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566485"
---
# <a name="get-context-for-your-microsoft-teams-bot"></a><span data-ttu-id="f5f0c-104">Obtenha contexto para o seu bot Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="f5f0c-104">Get context for your Microsoft Teams bot</span></span>

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

<span data-ttu-id="f5f0c-105">Seu bot pode acessar contexto adicional sobre a equipe ou bate-papo, como perfil do usuário.</span><span class="sxs-lookup"><span data-stu-id="f5f0c-105">Your bot can access additional context about the team or chat, such as user profile.</span></span> <span data-ttu-id="f5f0c-106">Essas informações podem ser usadas para enriquecer a funcionalidade do seu bot e proporcionar uma experiência mais personalizada.</span><span class="sxs-lookup"><span data-stu-id="f5f0c-106">This information can be used to enrich your bot's functionality and provide a more personalized experience.</span></span>

> [!NOTE]
>
> * <span data-ttu-id="f5f0c-107">Microsoft Teams APIs de bot específicas são melhor acessadas através de nossas extensões para o Bot Builder SDK.</span><span class="sxs-lookup"><span data-stu-id="f5f0c-107">Microsoft Teams-specific bot APIs are best accessed through our extensions for the Bot Builder SDK.</span></span>
> * <span data-ttu-id="f5f0c-108">Para C# ou .NET, baixe nosso pacote [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet.</span><span class="sxs-lookup"><span data-stu-id="f5f0c-108">For C# or .NET, download our [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet package.</span></span>
> * <span data-ttu-id="f5f0c-109">Para Node.js desenvolvimento, o Bot Builder for Teams funcionalidade é incorporado ao [Bot Framework SDK](https://github.com/microsoft/botframework-sdk) v4.6.</span><span class="sxs-lookup"><span data-stu-id="f5f0c-109">For Node.js development, the Bot Builder for Teams functionality is incorporated into the [Bot Framework SDK](https://github.com/microsoft/botframework-sdk) v4.6.</span></span>

## <a name="fetch-the-team-roster"></a><span data-ttu-id="f5f0c-110">Buscar a lista da equipe</span><span class="sxs-lookup"><span data-stu-id="f5f0c-110">Fetch the team roster</span></span>

<span data-ttu-id="f5f0c-111">Seu bot pode consultar a lista de membros da equipe e seus perfis básicos.</span><span class="sxs-lookup"><span data-stu-id="f5f0c-111">Your bot can query for the list of team members and their basic profiles.</span></span> <span data-ttu-id="f5f0c-112">Os perfis básicos incluem Teams IDs do usuário e informações de Azure Active Directory (AAD), como nome e ID de objeto.</span><span class="sxs-lookup"><span data-stu-id="f5f0c-112">The basic profiles include Teams user IDs and Azure Active Directory (AAD) information such as name and object ID.</span></span> <span data-ttu-id="f5f0c-113">Você pode usar essas informações para correlacionar as identidades dos usuários.</span><span class="sxs-lookup"><span data-stu-id="f5f0c-113">You can use this information to correlate user identities.</span></span> <span data-ttu-id="f5f0c-114">Por exemplo, verifique se um usuário logado em uma guia através de credenciais AAD é um membro da equipe.</span><span class="sxs-lookup"><span data-stu-id="f5f0c-114">For example, check if a user logged into a tab through AAD credentials is a team member.</span></span>

### <a name="rest-api-example"></a><span data-ttu-id="f5f0c-115">Exemplo de API REST</span><span class="sxs-lookup"><span data-stu-id="f5f0c-115">REST API example</span></span>

<span data-ttu-id="f5f0c-116">Emita diretamente uma solicitação GET sobre [`/conversations/{teamId}/members/`](/bot-framework/rest-api/bot-framework-rest-connector-api-reference#get-conversation-members) , usando o valor como ponto `serviceUrl` final.</span><span class="sxs-lookup"><span data-stu-id="f5f0c-116">Directly issue a GET request on [`/conversations/{teamId}/members/`](/bot-framework/rest-api/bot-framework-rest-connector-api-reference#get-conversation-members), using the `serviceUrl` value as the endpoint.</span></span>

<span data-ttu-id="f5f0c-117">O `teamId` pode ser encontrado no objeto da carga de atividade que o bot recebe nos `channeldata` seguintes cenários:</span><span class="sxs-lookup"><span data-stu-id="f5f0c-117">The `teamId` can be found in the `channeldata` object of the activity payload that your bot receives in the following scenarios:</span></span>

* <span data-ttu-id="f5f0c-118">Quando um usuário mensagee ou interage com seu bot em um contexto de equipe.</span><span class="sxs-lookup"><span data-stu-id="f5f0c-118">When a user messages or interacts with your bot in a team context.</span></span> <span data-ttu-id="f5f0c-119">Para obter mais informações, consulte [receber mensagens](~/resources/bot-v3/bot-conversations/bots-conversations.md#receiving-messages).</span><span class="sxs-lookup"><span data-stu-id="f5f0c-119">For more information, see [receiving messages](~/resources/bot-v3/bot-conversations/bots-conversations.md#receiving-messages).</span></span>
* <span data-ttu-id="f5f0c-120">Quando um novo usuário ou bot é adicionado a uma equipe.</span><span class="sxs-lookup"><span data-stu-id="f5f0c-120">When a new user or bot is added to a team.</span></span> <span data-ttu-id="f5f0c-121">Para obter mais informações, consulte [bot ou usuário adicionado a uma equipe](~/resources/bot-v3/bots-notifications.md#bot-or-user-added-to-a-team).</span><span class="sxs-lookup"><span data-stu-id="f5f0c-121">For more information, see [bot or user added to a team](~/resources/bot-v3/bots-notifications.md#bot-or-user-added-to-a-team).</span></span>

> [!NOTE]
>
>* <span data-ttu-id="f5f0c-122">Use sempre o ID da equipe ao chamar a API.</span><span class="sxs-lookup"><span data-stu-id="f5f0c-122">Always use the team ID when calling the API.</span></span>
>* <span data-ttu-id="f5f0c-123">O `serviceUrl` valor tende a ser estável, mas pode mudar.</span><span class="sxs-lookup"><span data-stu-id="f5f0c-123">The `serviceUrl` value tends to be stable but can change.</span></span> <span data-ttu-id="f5f0c-124">Quando uma nova mensagem chega, seu bot deve verificar seu `serviceUrl` valor armazenado.</span><span class="sxs-lookup"><span data-stu-id="f5f0c-124">When a new message arrives, your bot must verify its stored `serviceUrl` value.</span></span>

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

### <a name="net-example"></a><span data-ttu-id="f5f0c-125">Exemplo .NET</span><span class="sxs-lookup"><span data-stu-id="f5f0c-125">.NET example</span></span>

<span data-ttu-id="f5f0c-126">Ligue `GetConversationMembersAsync` `Team.Id` usando para retornar uma lista de IDs do usuário.</span><span class="sxs-lookup"><span data-stu-id="f5f0c-126">Call `GetConversationMembersAsync` using `Team.Id` to return a list of user IDs.</span></span>

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

### <a name="nodejs-or-typescript-example"></a><span data-ttu-id="f5f0c-127">Node.js ou exemplo TypeScript</span><span class="sxs-lookup"><span data-stu-id="f5f0c-127">Node.js or TypeScript example</span></span>

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

## <a name="fetch-user-profile-or-roster-in-personal-or-group-chat"></a><span data-ttu-id="f5f0c-128">Buscar perfil ou lista de usuários em bate-papo pessoal ou em grupo</span><span class="sxs-lookup"><span data-stu-id="f5f0c-128">Fetch user profile or roster in personal or group chat</span></span>

<span data-ttu-id="f5f0c-129">Você pode fazer a chamada de API para qualquer chat pessoal para obter as informações de perfil do usuário conversando com seu bot.</span><span class="sxs-lookup"><span data-stu-id="f5f0c-129">You can make the API call for any personal chat to obtain the profile information of the user chatting with your bot.</span></span>

<span data-ttu-id="f5f0c-130">A chamada API, os métodos SDK e o objeto de resposta são idênticos à obtenção da lista da equipe.</span><span class="sxs-lookup"><span data-stu-id="f5f0c-130">The API call, SDK methods, and the response object are identical to fetching the team roster.</span></span> <span data-ttu-id="f5f0c-131">A única diferença é que você passa o `conversationId` em vez do `teamId` .</span><span class="sxs-lookup"><span data-stu-id="f5f0c-131">The only difference is you pass the `conversationId` instead of the `teamId`.</span></span>

## <a name="fetch-the-list-of-channels-in-a-team"></a><span data-ttu-id="f5f0c-132">Buscar a lista de canais em uma equipe</span><span class="sxs-lookup"><span data-stu-id="f5f0c-132">Fetch the list of channels in a team</span></span>

<span data-ttu-id="f5f0c-133">Seu bot pode consultar a lista de canais em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="f5f0c-133">Your bot can query the list of channels in a team.</span></span>

> [!NOTE]
>
>* <span data-ttu-id="f5f0c-134">O nome do canal geral padrão é retornado `null` para permitir a localização.</span><span class="sxs-lookup"><span data-stu-id="f5f0c-134">The name of the default General channel is returned as `null` to allow for localization.</span></span>
>* <span data-ttu-id="f5f0c-135">A ID do canal para o canal Geral sempre corresponde ao ID da equipe.</span><span class="sxs-lookup"><span data-stu-id="f5f0c-135">The channel ID for the General channel always matches the team ID.</span></span>

### <a name="rest-api-example"></a><span data-ttu-id="f5f0c-136">Exemplo de API REST</span><span class="sxs-lookup"><span data-stu-id="f5f0c-136">REST API example</span></span>

<span data-ttu-id="f5f0c-137">Emita diretamente uma solicitação GET sobre `/teams/{teamId}/conversations/` , usando o valor como ponto `serviceUrl` final.</span><span class="sxs-lookup"><span data-stu-id="f5f0c-137">Directly issue a GET request on `/teams/{teamId}/conversations/`, using the `serviceUrl` value as the endpoint.</span></span>

<span data-ttu-id="f5f0c-138">A única fonte para `teamId` é uma mensagem do contexto da equipe.</span><span class="sxs-lookup"><span data-stu-id="f5f0c-138">The only source for `teamId` is a message from the team context.</span></span> <span data-ttu-id="f5f0c-139">A mensagem é uma mensagem de um usuário ou a mensagem que seu bot recebe quando é adicionado a uma equipe.</span><span class="sxs-lookup"><span data-stu-id="f5f0c-139">The message is either a message from a user or the message that your bot receives when it is added to a team.</span></span> <span data-ttu-id="f5f0c-140">Para obter mais informações, consulte [bot ou usuário adicionado a uma equipe](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition).</span><span class="sxs-lookup"><span data-stu-id="f5f0c-140">For more information, see [bot or user added to a team](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition).</span></span>

> [!NOTE]
> <span data-ttu-id="f5f0c-141">O `serviceUrl` valor tende a ser estável, mas pode mudar.</span><span class="sxs-lookup"><span data-stu-id="f5f0c-141">The `serviceUrl` value tends to be stable but can change.</span></span> <span data-ttu-id="f5f0c-142">Quando uma nova mensagem chega, seu bot deve verificar seu `serviceUrl` valor armazenado.</span><span class="sxs-lookup"><span data-stu-id="f5f0c-142">When a new message arrives, your bot must verify its stored `serviceUrl` value.</span></span>

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

#### <a name="net-example"></a><span data-ttu-id="f5f0c-143">Exemplo .NET</span><span class="sxs-lookup"><span data-stu-id="f5f0c-143">.NET example</span></span>

<span data-ttu-id="f5f0c-144">O exemplo a seguir usa a `FetchChannelList` chamada das [extensões Teams para o Bot Builder SDK para .NET](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams):</span><span class="sxs-lookup"><span data-stu-id="f5f0c-144">The following example uses the `FetchChannelList` call from the [Teams extensions for the Bot Builder SDK for .NET](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams):</span></span>

```csharp
ConversationList channels = client.GetTeamsConnectorClient().Teams.FetchChannelList(activity.GetChannelData<TeamsChannelData>().Team.Id);
```

#### <a name="nodejs-example"></a><span data-ttu-id="f5f0c-145">Node.js exemplo</span><span class="sxs-lookup"><span data-stu-id="f5f0c-145">Node.js example</span></span>

<span data-ttu-id="f5f0c-146">O exemplo a seguir usa `fetchChannelList` chamada das [extensões Teams para o Bot Builder SDK para Node.js](https://www.npmjs.com/package/botbuilder-teams):</span><span class="sxs-lookup"><span data-stu-id="f5f0c-146">The following example uses `fetchChannelList` call from the [Teams extensions for the Bot Builder SDK for Node.js](https://www.npmjs.com/package/botbuilder-teams):</span></span>

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

## <a name="get-clientinfo-in-your-bot-context"></a><span data-ttu-id="f5f0c-147">Obtenha clienteInfo em seu contexto de bot</span><span class="sxs-lookup"><span data-stu-id="f5f0c-147">Get clientInfo in your bot context</span></span>

<span data-ttu-id="f5f0c-148">Você pode buscar o clienteInfo dentro da atividade do seu bot.</span><span class="sxs-lookup"><span data-stu-id="f5f0c-148">You can fetch the clientInfo within your bot's activity.</span></span> <span data-ttu-id="f5f0c-149">O clienteInfo contém as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="f5f0c-149">The clientInfo contains the following properties:</span></span>

* <span data-ttu-id="f5f0c-150">Locale</span><span class="sxs-lookup"><span data-stu-id="f5f0c-150">Locale</span></span>
* <span data-ttu-id="f5f0c-151">País/Região</span><span class="sxs-lookup"><span data-stu-id="f5f0c-151">Country</span></span>
* <span data-ttu-id="f5f0c-152">Plataforma</span><span class="sxs-lookup"><span data-stu-id="f5f0c-152">Platform</span></span>
* <span data-ttu-id="f5f0c-153">Fuso horário</span><span class="sxs-lookup"><span data-stu-id="f5f0c-153">Timezone</span></span>

### <a name="json-example"></a><span data-ttu-id="f5f0c-154">Exemplo JSON</span><span class="sxs-lookup"><span data-stu-id="f5f0c-154">JSON example</span></span>

```json
[
    {
        "type": "clientInfo",
        "locale": "en-US",
        "country": "US",
        "platform": "Windows",
        "timezone": "Asia/Calcutta"
    }
]
```

### <a name="c-example"></a><span data-ttu-id="f5f0c-155">C# exemplo</span><span class="sxs-lookup"><span data-stu-id="f5f0c-155">C# example</span></span>

```csharp
var connector = new ConnectorClient(new Uri(context.Activity.ServiceUrl));

{
    var clientinfo = context.Activity.Entities[0];
    await context.PostAsync($"ClientInfo: clientinfo ");
}
```

## <a name="see-also"></a><span data-ttu-id="f5f0c-156">Confira também</span><span class="sxs-lookup"><span data-stu-id="f5f0c-156">See also</span></span>

<span data-ttu-id="f5f0c-157">[Amostras do Bot Framework](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span><span class="sxs-lookup"><span data-stu-id="f5f0c-157">[Bot Framework samples](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).</span></span>