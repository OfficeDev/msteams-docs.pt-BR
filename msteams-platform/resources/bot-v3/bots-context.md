---
title: Obter contexto para o bot do Microsoft Teams
description: Neste módulo, saiba como obter contexto para bots no Microsoft Teams, buscar a lista de participantes da equipe e o perfil do usuário ou lista de participantes no chat pessoal ou em grupo
ms.topic: conceptual
ms.localizationpriority: medium
ms.date: 05/20/2019
ms.openlocfilehash: fd43d9c4b3a3e4702b9bbd4955e58c0fc86caddf
ms.sourcegitcommit: de7496f9586316bed12d115cd3e4c18ba0854d4f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2022
ms.locfileid: "67780923"
---
# <a name="get-context-for-your-microsoft-teams-bot"></a>Obter contexto para o bot do Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Seu bot pode acessar contexto adicional sobre a equipe ou o chat, como o perfil do usuário. Essas informações podem ser usadas para enriquecer a funcionalidade do bot e fornecer uma experiência mais personalizada.

> [!NOTE]
>
> * As APIs de bot específicas do Microsoft Teams são mais bem acessadas por meio de nossas extensões para o SDK do Bot Builder.
> * Para C# ou .NET, baixe nosso [pacote NuGet Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) .
> * Para Node.js desenvolvimento, a funcionalidade do Bot Builder para Teams é incorporada ao [SDK do Bot Framework](https://github.com/microsoft/botframework-sdk) v4.6.

## <a name="fetch-the-team-roster"></a>Buscar a lista de participantes da equipe

Seu bot pode consultar a lista de membros da equipe e seus perfis básicos. Os perfis básicos incluem IDs de usuário e Microsoft Azure Active Directory (Azure AD) do Teams, como nome e ID de objeto. Você pode usar essas informações para correlacionar identidades de usuários. Por exemplo, verifique se um usuário fez logon em uma guia por meio Microsoft Azure Active Directory (Azure AD) é membro da equipe.

### <a name="rest-api-example"></a>Exemplo da API REST

Emita diretamente uma solicitação GET em [`/conversations/{teamId}/members/`](/bot-framework/rest-api/bot-framework-rest-connector-api-reference#get-conversation-members), usando o `serviceUrl` valor como o ponto de extremidade.

Pode `teamId` ser encontrado no objeto da `channeldata` carga de atividade que seu bot recebe nos seguintes cenários:

* Quando um usuário mensagens ou interage com o bot em um contexto de equipe. Para obter mais informações, consulte [receber mensagens](~/resources/bot-v3/bot-conversations/bots-conversations.md#receiving-messages).
* Quando um novo usuário ou bot é adicionado a uma equipe. Para obter mais informações, consulte [bot ou usuário adicionado a uma equipe](~/resources/bot-v3/bots-notifications.md#bot-or-user-added-to-a-team).

> [!NOTE]
>
>* Sempre use a ID da equipe ao chamar a API.
>* O `serviceUrl` valor tende a ser estável, mas pode ser alterado. Quando uma nova mensagem chega, o bot deve verificar seu valor `serviceUrl` armazenado.

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

Chame `GetConversationMembersAsync` usando `Team.Id` para retornar uma lista de IDs de usuário.
A `GetConversationMembersAsync` chamada para obter `userRole` a propriedade retorna o valor como usuário.

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

### <a name="nodejs-or-typescript-example"></a>Node.js ou TypeScript

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

## <a name="fetch-user-profile-or-roster-in-personal-or-group-chat"></a>Buscar perfil de usuário ou lista de participantes em chat pessoal ou em grupo

Você pode fazer a chamada à API para qualquer chat pessoal para obter as informações de perfil do usuário conversando com seu bot.

A chamada à API, os métodos do SDK e o objeto de resposta são idênticos à busca da lista de participantes da equipe. A única diferença é que você passa o `conversationId` em vez de `teamId`.

## <a name="fetch-the-list-of-channels-in-a-team"></a>Buscar a lista de canais em uma equipe

Seu bot pode consultar a lista de canais em uma equipe.

> [!NOTE]
>
>* O nome do canal geral padrão é retornado como `null` para permitir a localização.
>* A ID do canal para o canal Geral sempre corresponde à ID da equipe.

### <a name="rest-api-example"></a>Exemplo da API REST

Emita diretamente uma solicitação GET em `/teams/{teamId}/conversations/`, usando o `serviceUrl` valor como o ponto de extremidade.

A única origem é `teamId` uma mensagem do contexto da equipe. A mensagem é uma mensagem de um usuário ou a mensagem que seu bot recebe quando ele é adicionado a uma equipe. Para obter mais informações, consulte [bot ou usuário adicionado a uma equipe](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition).

> [!NOTE]
> O `serviceUrl` valor tende a ser estável, mas pode ser alterado. Quando uma nova mensagem chega, o bot deve verificar seu valor `serviceUrl` armazenado.

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

O exemplo a seguir usa a `FetchChannelList` chamada das [extensões do Teams para o SDK do Construtor de Bot para .NET](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams):

```csharp
ConversationList channels = client.GetTeamsConnectorClient().Teams.FetchChannelList(activity.GetChannelData<TeamsChannelData>().Team.Id);
```

#### <a name="nodejs-example"></a>Exemplo de Node.js

O exemplo a seguir usa `fetchChannelList` a chamada das [extensões do Teams para o SDK do Construtor de Bot para Node.js](https://www.npmjs.com/package/botbuilder-teams):

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

Você pode buscar o clientInfo dentro da atividade do bot. O clientInfo contém as seguintes propriedades:

* Locale
* País/Região
* Plataforma
* Timezone

### <a name="json-example"></a>Exemplo de JSON

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

### <a name="c-example"></a>Exemplo de C#

```csharp
var connector = new ConnectorClient(new Uri(context.Activity.ServiceUrl));

{
    var clientinfo = context.Activity.Entities[0];
    await context.PostAsync($"ClientInfo: clientinfo ");
}
```

## <a name="see-also"></a>Confira também

[Amostras do Bot Framework](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md).
