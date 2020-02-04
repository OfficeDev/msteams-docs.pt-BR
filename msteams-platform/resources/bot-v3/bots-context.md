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
# <a name="get-context-for-your-microsoft-teams-bot"></a>Obter contexto para o bot do Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Seu bot pode acessar contexto adicional sobre a equipe ou chat, como perfil de usuário. Essas informações podem ser usadas para enriquecer a funcionalidade do seu bot e fornecer uma experiência mais personalizada.

> [!NOTE]
> Essas APIs de&ndash;bot específicas do Microsoft Teams são mais bem acessadas por meio de nossas extensões para o SDK do bot Builder. Para o C#/.NET, baixe [o pacote NuGet Microsoft. bot. Connector. Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) . Para o desenvolvimento de Node. js, você pode instalar o pacote [botbuilder-Teams](https://www.npmjs.com/package/botbuilder-teams) NPM. O construtor de bot de destino do SDKs v3.

## <a name="fetching-the-team-roster"></a>Buscando a lista de equipes

O bot pode consultar a lista de membros da equipe e seus perfis básicos, que inclui as IDs de usuário do Teams e as informações do Azure Active Directory (Azure AD), como nome e objectId. Você pode usar essas informações para correlacionar as identidades do usuário; por exemplo, para verificar se um usuário conectado a uma guia por meio de credenciais do Azure AD é um membro da equipe.

### <a name="rest-api-example"></a>Exemplo de API REST

Você pode emitir diretamente uma solicitação GET no [`/conversations/{teamId}/members/`](/bot-framework/rest-api/bot-framework-rest-connector-api-reference#get-conversation-members), usando o valor de `serviceUrl` como ponto de extremidade.

O `teamId` pode ser encontrado no `channeldata` objeto da carga de atividade que seu bot recebe nos seguintes cenários:
* Quando um usuário mensagens ou interage com seu bot em um contexto de equipe (consulte [recebendo mensagens](~/resources/bot-v3/bot-conversations/bots-conversations.md#receiving-messages))
* Quando um novo usuário ou bot é adicionado a uma equipe (consulte [bot ou User Added to a Team](~/resources/bot-v3/bots-notifications.md#bot-or-user-added-to-a-team))

> [!NOTE]
>* Certifique-se de usar a ID da equipe ao chamar a API
>* O valor de `serviceUrl` tende a ser estável, mas pode ser alterado. Quando uma nova mensagem chega, seu bot deve verificar seu valor armazenado de `serviceUrl`.

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

### <a name="net-example"></a>Exemplo .NET

Chamar `GetConversationMembersAsync` usando `Team.Id` para retornar uma lista de IDs de usuário.

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

### <a name="nodejstypescript-example"></a>Exemplo de Node. js/TypeScript

O exemplo a seguir usa as [extensões do Microsoft Teams para o SDK do bot Builder para node. js](https://www.npmjs.com/package/botbuilder-teams).

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

## <a name="fetching-user-profile-or-roster-in-personal-or-group-chat"></a>Buscando perfil de usuário ou lista no chat de grupo ou pessoal

Você também pode fazer a mesma chamada de API para qualquer chat pessoal para obter as informações de perfil do usuário batendo papo com seu bot.

Os métodos de chamada de API e SDK são idênticos para buscar a lista de equipes, como é o objeto de resposta. A única diferença é passar no `conversationId` lugar do. `teamId`

## <a name="fetching-the-list-of-channels-in-a-team"></a>Buscando a lista de canais em uma equipe

O bot pode consultar a lista de canais de uma equipe.

> [!NOTE]
>
>* O nome do canal geral padrão é retornado como `null` permitir para localização.
>* A ID do canal geral sempre corresponde à ID da equipe.

### <a name="rest-api-example"></a>Exemplo de API REST

Você pode emitir diretamente uma solicitação GET no `/teams/{teamId}/conversations/`, usando o valor de `serviceUrl` como ponto de extremidade.

A única fonte de `teamId` é uma mensagem do contexto da equipe-uma mensagem de um usuário ou a mensagem que seu bot recebe quando é adicionada a uma equipe (consulte [bot ou User Added to a Team](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition)).

> [!NOTE]
> O valor de `serviceUrl` tende a ser estável, mas pode ser alterado. Quando uma nova mensagem chega, seu bot deve verificar seu valor armazenado de `serviceUrl`.

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

#### <a name="net-example"></a>Exemplo .NET

O exemplo a seguir usa `FetchChannelList` a chamada das [extensões do Microsoft Teams para o SDK do bot Builder para .net](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams):

```csharp
ConversationList channels = client.GetTeamsConnectorClient().Teams.FetchChannelList(activity.GetChannelData<TeamsChannelData>().Team.Id);
```

#### <a name="nodejs-example"></a>Exemplo do node. js

O exemplo a seguir `fetchChannelList` usa a chamada das [extensões do Microsoft Teams para o SDK do Configurador de bot para node. js](https://www.npmjs.com/package/botbuilder-teams).

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
