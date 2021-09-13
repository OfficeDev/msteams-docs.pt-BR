---
title: Obter contexto para seu Microsoft Teams bot
description: Descreve como obter contexto para bots no Microsoft Teams
keywords: contexto de bots do teams
ms.topic: conceptual
ms.localizationpriority: medium
ms.date: 05/20/2019
ms.openlocfilehash: 5c9dac9712f6bdc9a62262614ceaf90fd100e19e
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59155247"
---
# <a name="get-context-for-your-microsoft-teams-bot"></a>Obter contexto para seu Microsoft Teams bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Seu bot pode acessar contexto adicional sobre a equipe ou chat, como o perfil do usuário. Essas informações podem ser usadas para enriquecer a funcionalidade do bot e fornecer uma experiência mais personalizada.

> [!NOTE]
>
> * Microsoft Teams APIs de bot específicas são mais acessadas por meio de nossas extensões para o SDK do Construtor de Bots.
> * Para C# ou .NET, baixe nosso [pacote Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet pacote.
> * Para Node.js desenvolvimento, o Construtor de Bots para Teams funcionalidade é incorporado ao [SDK](https://github.com/microsoft/botframework-sdk) da Estrutura de Bot v4.6.

## <a name="fetch-the-team-roster"></a>Buscar a lista de equipe

Seu bot pode consultar a lista de membros da equipe e seus perfis básicos. Os perfis básicos incluem Teams IDs de usuário e Azure Active Directory (AAD), como nome e ID do objeto. Você pode usar essas informações para correlacionar identidades de usuário. Por exemplo, verifique se um usuário conectado a uma guia por meio de credenciais do AAD é membro da equipe.

### <a name="rest-api-example"></a>Exemplo da API REST

Emito diretamente uma solicitação GET [`/conversations/{teamId}/members/`](/bot-framework/rest-api/bot-framework-rest-connector-api-reference#get-conversation-members) em , usando o valor como ponto de `serviceUrl` extremidade.

O pode ser encontrado no objeto da carga de atividade que `teamId` seu bot recebe nos seguintes `channeldata` cenários:

* Quando um usuário mensagens ou interage com seu bot em um contexto de equipe. Para obter mais informações, consulte [recebimento de mensagens](~/resources/bot-v3/bot-conversations/bots-conversations.md#receiving-messages).
* Quando um novo usuário ou bot é adicionado a uma equipe. Para obter mais informações, [consulte bot ou user added to a team](~/resources/bot-v3/bots-notifications.md#bot-or-user-added-to-a-team).

> [!NOTE]
>
>* Sempre use a ID da equipe ao chamar a API.
>* O `serviceUrl` valor tende a ser estável, mas pode mudar. Quando uma nova mensagem chega, seu bot deve verificar seu valor `serviceUrl` armazenado.

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

### <a name="net-example"></a>Exemplo do .NET

Chame `GetConversationMembersAsync` usando para retornar uma lista de `Team.Id` IDs de usuário.

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

### <a name="nodejs-or-typescript-example"></a>Node.js exemplo ou TypeScript

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

## <a name="fetch-user-profile-or-roster-in-personal-or-group-chat"></a>Buscar perfil de usuário ou lista em chat pessoal ou em grupo

Você pode fazer a chamada da API para qualquer chat pessoal para obter as informações de perfil do usuário conversando com seu bot.

A chamada da API, os métodos SDK e o objeto de resposta são idênticos à busca da lista de equipe. A única diferença é que você passa o `conversationId` em vez de `teamId` .

## <a name="fetch-the-list-of-channels-in-a-team"></a>Buscar a lista de canais em uma equipe

Seu bot pode consultar a lista de canais em uma equipe.

> [!NOTE]
>
>* O nome do canal Geral padrão é retornado para `null` permitir a localização.
>* A ID do canal para o canal Geral sempre corresponde à ID da equipe.

### <a name="rest-api-example"></a>Exemplo da API REST

Emito diretamente uma solicitação GET `/teams/{teamId}/conversations/` em , usando o valor como ponto de `serviceUrl` extremidade.

A única fonte para `teamId` é uma mensagem do contexto da equipe. A mensagem é uma mensagem de um usuário ou a mensagem que seu bot recebe quando é adicionada a uma equipe. Para obter mais informações, [consulte bot ou user added to a team](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition).

> [!NOTE]
> O `serviceUrl` valor tende a ser estável, mas pode mudar. Quando uma nova mensagem chega, seu bot deve verificar seu valor `serviceUrl` armazenado.

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

#### <a name="net-example"></a>Exemplo do .NET

O exemplo a seguir usa `FetchChannelList` a chamada das [extensões Teams para o SDK](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams)do Construtor de Bots para .NET :

```csharp
ConversationList channels = client.GetTeamsConnectorClient().Teams.FetchChannelList(activity.GetChannelData<TeamsChannelData>().Team.Id);
```

#### <a name="nodejs-example"></a>Node.js exemplo

O exemplo a seguir usa `fetchChannelList` a chamada Teams [extensões do SDK ](https://www.npmjs.com/package/botbuilder-teams)do Construtor de Bots para Node.js:

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

## <a name="get-clientinfo-in-your-bot-context"></a>Obter clientInfo no contexto do bot

Você pode buscar o clientInfo na atividade do bot. O clientInfo contém as seguintes propriedades:

* Locale
* País
* Plataforma
* Timezone

### <a name="json-example"></a>Exemplo JSON

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

### <a name="c-example"></a>C# exemplo

```csharp
var connector = new ConnectorClient(new Uri(context.Activity.ServiceUrl));

{
    var clientinfo = context.Activity.Entities[0];
    await context.PostAsync($"ClientInfo: clientinfo ");
}
```

## <a name="see-also"></a>Confira também

[Exemplos de Estrutura de Bot](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).