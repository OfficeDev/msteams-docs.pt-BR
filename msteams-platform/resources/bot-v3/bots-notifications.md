---
title: Manipular eventos de bot
description: Descreve como lidar com eventos em bots para o Microsoft Teams
keywords: eventos de bots do teams
ms.date: 05/20/2019
author: laujan
ms.openlocfilehash: 5ef37a931d421f245cca4fbb984b69217f779785
ms.sourcegitcommit: 3fc7ad33e2693f07170c3cb1a0d396261fc5c619
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2020
ms.locfileid: "48796173"
---
# <a name="handle-bot-events-in-microsoft-teams"></a>Manipular eventos de bot no Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

O Microsoft Teams envia notificações ao bot para alterações ou eventos que ocorrem em escopos onde o bot está ativo. Você pode usar esses eventos para disparar a lógica de serviço, como o seguinte:

* Acionar uma mensagem de boas-vindas quando seu bot é adicionado a uma equipe
* Informações de consulta e de grupo de cache quando o bot é adicionado a um chat de grupo
* Atualizar informações armazenadas em cache nas informações de associação ou canal da equipe
* Remover informações armazenadas em cache de uma equipe se o bot for removido
* Quando uma mensagem de bot é curtida por um usuário

Cada evento de bot é enviado como um `Activity` objeto no qual `messageType` define quais informações estão no objeto. Para mensagens do tipo `message` , consulte [envio e recebimento de mensagens](~/resources/bot-v3/bot-conversations/bots-conversations.md).

Equipes e eventos de grupo, geralmente disparados `conversationUpdate` com o tipo, têm informações de evento adicionais do teams passadas como parte do objeto e, `channelData` portanto, seu manipulador de eventos deve consultar a `channelData` carga das equipes `eventType` e metadados adicionais específicos do evento.

A tabela a seguir lista os eventos que o seu bot pode receber e executar ações.

|Tipo|Objeto Payload|EventType de equipes |Descrição|Escopo|
|---|---|---|---|---|
| `conversationUpdate` |`membersAdded`| `teamMemberAdded`|[Membro adicionado à equipe](#team-member-or-bot-addition)| todos os |
| `conversationUpdate` |`membersRemoved`| `teamMemberRemoved`|[O membro foi removido da equipe](#team-member-or-bot-removed)| `groupChat` & `team` |
| `conversationUpdate` | |`teamRenamed`| [A equipe foi renomeada](#team-name-updates)| `team` |
| `conversationUpdate` | |`channelCreated`| [Um canal foi criado](#channel-updates)|`team` |
| `conversationUpdate` | |`channelRenamed`| [Um canal foi renomeado](#channel-updates)|`team` |
| `conversationUpdate` | |`channelDeleted`| [Um canal foi excluído](#channel-updates)|`team` |
| `messageReaction` |`reactionsAdded`|| [Reação à mensagem de bot](#reactions)| todos os |
| `messageReaction` |`reactionsRemoved`|| [Reação removida da mensagem de bot](#reactions)| todos os |

## <a name="team-member-or-bot-addition"></a>Adição de um membro da equipe ou de bot

O [`conversationUpdate`](/azure/bot-service/dotnet/bot-builder-dotnet-activities?view=azure-bot-service-3.0#conversationupdate) evento é enviado ao bot quando recebe informações sobre atualizações de associação para equipes em que foram adicionadas. Ele também recebe uma atualização quando foi adicionado pela primeira vez especificamente para conversas pessoais. Observe que as informações do usuário ( `Id` ) são exclusivas para o bot e podem ser armazenadas em cache para uso futuro pelo serviço (como enviar uma mensagem para um usuário específico).

### <a name="bot-or-user-added-to-a-team"></a>Bot ou usuário adicionado a uma equipe

O `conversationUpdate` evento com o `membersAdded` objeto no payload é enviado quando um bot é adicionado a uma equipe ou um novo usuário é adicionado a uma equipe onde um bot foi adicionado. O Microsoft Teams também adiciona `eventType.teamMemberAdded` o `channelData` objeto.

Como esse evento é enviado em ambos os casos, você deve analisar o `membersAdded` objeto para determinar se a adição era um usuário ou o próprio bot. Para o último, uma prática recomendada é enviar uma [mensagem de boas-vindas](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#best-practice-welcome-messages-in-teams) ao canal para que os usuários possam entender os recursos que o seu bot fornece.

#### <a name="example-code-checking-whether-bot-was-the-added-member"></a>Código de exemplo: verificando se o bot foi o membro adicionado

##### <a name="net"></a>.NET

```csharp
    for (int i = 0; i < sourceMessage.MembersAdded.Count; i++)
    {
        if (sourceMessage.MembersAdded[i].Id == sourceMessage.Recipient.Id)
        {
            addedBot = true;
            break;
        }
    }
```

##### <a name="nodejs"></a>Node.js

```javascript
const builder = require('botbuilder');

var c = new builder.ChatConnector({appId: BOT_APP_ID, appPassword: .BOT_SECRET});
var bot = new builder.UniversalBot(c);

bot.on('conversationUpdate', (msg) => {
    var members = msg.membersAdded;
    // Loop through all members that were just added to the team
    for (var i = 0; i < members.length; i++) {

        // See if the member added was our bot
        if (members[i].id.includes(BOT_APP_ID)) {
            var botmessage = new builder.Message()
                .address(msg.address)
                .text('Hello World!');

            bot.send(botmessage, function(err) {});
        }
    }
});
```

#### <a name="schema-example-bot-added-to-team"></a>Exemplo de esquema: bot adicionado à equipe

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

### <a name="bot-added-for-personal-context-only"></a>Bot adicionado somente para contexto pessoal

O bot recebe um `conversationUpdate` com `membersAdded` quando um usuário o adiciona diretamente para chat pessoal. Nesse caso, a carga que seu bot recebe não contém o `channelData.team` objeto. Você deve usá-lo como um filtro caso queira que seu bot ofereça uma mensagem de [boas-vindas](~/resources/bot-v3/bot-conversations/bots-conv-personal.md#best-practice-welcome-messages-in-personal-conversations) diferente dependendo do escopo.

> [!NOTE]
> Para bots com escopo pessoal, seu bot sempre receberá o `conversationUpdate` evento uma única vez, mesmo que o bot seja removido e adicionado novamente. Para desenvolvimento e testes, você pode achar útil adicionar uma função auxiliar que permitirá redefinir seu bot completamente. Veja um [ exemplo deNode.js](https://github.com/OfficeDev/microsoft-teams-sample-complete-node/blob/master/src/middleware/SimulateResetBotChat.ts) ou um [exemplo de C#](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp/blob/master/template-bot-master-csharp/src/controllers/MessagesController.cs#L238) para obter mais detalhes sobre como implementar isso.

#### <a name="schema-example-bot-added-to-personal-context"></a>Exemplo de esquema: bot adicionado ao contexto pessoal

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

## <a name="team-member-or-bot-removed"></a>Membro da equipe ou bot removido

O `conversationUpdate` evento com o `membersRemoved` objeto no payload é enviado quando seu bot é removido de uma equipe ou um usuário é removido de uma equipe onde um bot foi adicionado. O Microsoft Teams também adiciona `eventType.teamMemberRemoved` o `channelData` objeto. Assim como com o `membersAdded` objeto, você deve analisar o `membersRemoved` objeto para a ID do aplicativo do bot para determinar quem foi removido.

### <a name="schema-example-team-member-removed"></a>Exemplo de esquema: membro da equipe removido

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

## <a name="team-name-updates"></a>Atualizações de nome de equipe

> [!NOTE]
> Não há nenhuma funcionalidade para consultar todos os nomes de equipe, e o nome da equipe não é retornado em cargas de outros eventos.

O bot é notificado quando a equipe que está sendo renomeada. Ele recebe um `conversationUpdate` evento com `eventType.teamRenamed` no `channelData` objeto. Observe que não há notificações para criação ou exclusão de equipes, porque os bots só existem como parte do Teams e não têm visibilidade fora do escopo em que foram adicionados.

### <a name="schema-example-team-renamed"></a>Exemplo de esquema: equipe renomeada

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

## <a name="channel-updates"></a>Atualizações de canal

O bot é notificado quando um canal é criado, renomeado ou excluído em uma equipe onde foi adicionado. Novamente, o `conversationUpdate` evento é recebido, e um identificador de eventos específico do teams é enviado como parte do `channelData.eventType` objeto, onde os dados do  `channel.id` canal são o GUID do canal e `channel.name` contém o próprio nome do canal.

Os eventos do canal são os seguintes:

_ **channelCreated** &emsp; um usuário adiciona um novo canal à equipe
* **channelRenamed** &emsp; Um usuário renomeia um canal existente
* **channelDeleted** &emsp; Um usuário remove um canal

### <a name="full-schema-example-channelcreated"></a>Exemplo de esquema completo: channelCreated

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

### <a name="schema-excerpt-channeldata-for-channelrenamed"></a>Trecho de esquema: channelData para channelRenamed

```json
⋮
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
⋮
```

### <a name="schema-excerpt-channeldata-for-channeldeleted"></a>Trecho de esquema: channelData para channelDeleted

```json
⋮
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
⋮
```

## <a name="reactions"></a>Reações

O `messageReaction` evento é enviado quando um usuário adiciona ou remove sua reação a uma mensagem que foi enviada originalmente pelo bot. `replyToId` contém a ID da mensagem específica.

### <a name="schema-example-a-user-likes-a-message"></a>Exemplo de esquema: um usuário gosta de uma mensagem

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
    "replyToId": "1575667808184"
}
```

### <a name="schema-example-a-user-un-likes-a-message"></a>Exemplo de esquema: um usuário não curti uma mensagem

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
    "replyToId": "1575667808184"
}
```
