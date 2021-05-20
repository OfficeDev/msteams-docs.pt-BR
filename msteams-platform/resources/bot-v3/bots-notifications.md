---
title: Lidar com eventos de bot
description: Descreve como lidar com eventos em bots para Microsoft Teams
keywords: equipes bots eventos
ms.date: 05/20/2019
ms.topic: how-to
localization_priority: Normal
ms.author: lajanuar
author: laujan
ms.openlocfilehash: da624ea0e92e193f4ad7f334d958349d542dd6e0
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566464"
---
# <a name="handle-bot-events-in-microsoft-teams"></a>Lidar com eventos de bot em Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Microsoft Teams envia notificações ao seu bot para alterações ou eventos que acontecem em escopos onde seu bot está ativo. Você pode usar esses eventos para ativar a lógica de serviço, como o seguinte:

* Acione uma mensagem de boas-vindas quando seu bot for adicionado a uma equipe.
* Consultas e informações do grupo de cache quando o bot é adicionado a um bate-papo em grupo.
* Atualize informações armazenadas em cache sobre a adesão da equipe ou informações do canal.
* Remova informações armazenadas em cache para uma equipe se o bot for removido.
* Quando uma mensagem de bot é curtida por um usuário.

Cada evento de bot é enviado como um `Activity` objeto no qual define quais informações estão no `messageType` objeto. Para mensagens de `message` tipo, consulte [Enviar e receber mensagens](~/resources/bot-v3/bot-conversations/bots-conversations.md).

Teams e eventos em grupo, geralmente acionados fora do `conversationUpdate` tipo, têm informações adicionais de Teams evento passados como parte do `channelData` objeto e, portanto, o manipulador de eventos deve consultar a carga para os Teams `channelData` e `eventType` metadados adicionais específicos do evento.

A tabela a seguir lista os eventos que seu bot pode receber e agir.

|Tipo|Objeto de carga|evento Teams Type |Descrição|Escopo|
|---|---|---|---|---|
| `conversationUpdate` |`membersAdded`| `teamMemberAdded`|[Membro adicionado à equipe](#team-member-or-bot-addition)| todo |
| `conversationUpdate` |`membersRemoved`| `teamMemberRemoved`|[Membro foi removido da equipe](#team-member-or-bot-removed)| `groupChat` & `team` |
| `conversationUpdate` | |`teamRenamed`| [Equipe foi renomeada](#team-name-updates)| `team` |
| `conversationUpdate` | |`channelCreated`| [Um canal foi criado](#channel-updates)|`team` |
| `conversationUpdate` | |`channelRenamed`| [Um canal foi renomeado](#channel-updates)|`team` |
| `conversationUpdate` | |`channelDeleted`| [Um canal foi excluído](#channel-updates)|`team` |
| `messageReaction` |`reactionsAdded`|| [Reação à mensagem bot](#reactions)| todo |
| `messageReaction` |`reactionsRemoved`|| [Reação removida da mensagem bot](#reactions)| todo |

## <a name="team-member-or-bot-addition"></a>Adição de membro da equipe ou bot

O [`conversationUpdate`](/azure/bot-service/dotnet/bot-builder-dotnet-activities?view=azure-bot-service-3.0#conversationupdate&preserve-view=true) evento é enviado ao seu bot quando recebe informações sobre atualizações de membros para equipes onde foi adicionado. Ele também recebe uma atualização quando é adicionado pela primeira vez, especificamente para conversas pessoais. Observe que as informações do usuário ( `Id` ) são únicas para o seu bot e podem ser armazenadas em cache para uso futuro pelo seu serviço, como, como, enviar uma mensagem para um usuário específico.

### <a name="bot-or-user-added-to-a-team"></a>Bot ou usuário adicionado a uma equipe

O `conversationUpdate` evento com o objeto na carga é enviado quando um bot é adicionado a uma equipe ou um `membersAdded` novo usuário é adicionado a uma equipe onde um bot foi adicionado. Microsoft Teams também adiciona `eventType.teamMemberAdded` no `channelData` objeto.

Como este evento é enviado em ambos os casos, você deve analisar o `membersAdded` objeto para determinar se a adição foi um usuário ou o próprio bot. Para este último, uma prática recomendada é enviar uma [mensagem de boas-vindas](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#best-practice-welcome-messages-in-teams) ao canal para que os usuários possam entender os recursos que seu bot fornece.

#### <a name="example-code-checking-whether-bot-was-the-added-member"></a>Código de exemplo: Verificando se o bot era o membro adicionado

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

#### <a name="schema-example-bot-added-to-team"></a>Exemplo de esquema: Bot adicionado à equipe

```json
{
   "membersAdded":[
      {
         "id":"28:f5d48856-5b42-41a0-8c3a-c5f944b679b0"
      }
   ],
   "type":"conversationUpdate",
   "timestamp":"2017-02-23T19:38:35.312Z",
   "localTimestamp":"2017-02-23T12:38:35.312-07:00",
   "id":"f:5f85c2ad",
   "channelId":"msteams",
   "serviceUrl":"https://smba.trafficmanager.net/amer-client-ss.msg/",
   "from":{
      "id":"29:1I9Is_Sx0OIy2rQ7Xz1lcaPKlO9eqmBRTBuW6XzkFtcjqxTjPaCMij8BVMdBcL9L_RwWNJyAHFQb0TRzXgyQvA"
   },
   "conversation":{
      "isGroup":true,
      "conversationType":"channel",
      "id":"19:efa9296d959346209fea44151c742e73@thread.skype"
   },
   "recipient":{
      "id":"28:f5d48856-5b42-41a0-8c3a-c5f944b679b0",
      "name":"SongsuggesterBot"
   },
   "channelData":{
      "team":{
         "id":"19:efa9296d959346209fea44151c742e73@thread.skype"
      },
      "eventType":"teamMemberAdded",
      "tenant":{
         "id":"72f988bf-86f1-41af-91ab-2d7cd011db47"
      }
   }
}
```

### <a name="user-added-to-a-meeting"></a>Usuário Adicionado a uma reunião

O `conversationUpdate` evento com o objeto na carga é enviado quando um usuário é adicionado a uma reunião agendada `membersAdded` privada. Os detalhes do evento serão enviados mesmo quando usuários anônimos participarem da reunião. 

> [!NOTE]
>
>* Quando um usuário anônimo é adicionado a uma reunião, o objeto de carga adicionado não tem `aadObjectId` campo.
>* Quando um usuário anônimo é adicionado a uma reunião, `from` o objeto na carga sempre tem a identificação do organizador do encontro, mesmo que o usuário anônimo tenha sido adicionado por outro apresentador.

#### <a name="schema-example-user-added-to-meeting"></a>Exemplo de esquema: Usuário adicionado à reunião

```json
{
   "membersAdded":[
      {
         "id":"229:1Z_XHWBMhDuehhDBYoPQD6Y1DSFsTtqOZx-SA5Jh9Y4zHKm4VbFGRn7-rK7SWiW1JECwxkMdrWpHoBut2sSyQPA"
      }
   ],
   "type":"conversationUpdate",
   "timestamp":"2017-02-23T19:38:35.312Z",
   "localTimestamp":"2020-09-29T21:11:38.6542339Z",
   "id":"f:a8cd1b51-9ddb-bd35-624b-7f7474165df8",
   "channelId":"msteams",
   "serviceUrl":"https://canary.botapi.skype.com/amer/",
   "from":{
      "id":"29:1siKxZhSoTapsXvI0gyf7Gywm_HM-4kEQW4BJnWuFYVIVu87xCNP99nidgQRCcwD3L3p_schiMShzx8IDRzf8mw",
      "aadObjectId":"f30ba569-abef-4e97-8762-35f85cbae706"
   },
   "conversation":{
      "isGroup":true,
      "tenantId":"e15762ef-a8d8-416b-871c-25516354f1fe",
      "id":"19:meeting_MWJlNGViOTgtMGExYi00NDA3LWExODgtOTZhMWNlYjM4ZTRj@thread.v2"
   },
   "recipient":{
      "id":"28:3af3604a-d4fc-486b-911e-86fab41aa91c",
      "name":"EchoBot1_Rename"
   },
   "channelData":{
      "tenant":{
         "id":"e15762ef-a8d8-416b-871c-25516354f1fe"
      },
      "source":null,
      "meeting":{
         "id":"MCMxOTptZWV0aW5nX01XSmxOR1ZpT1RndE1HRXhZaTAwTkRBM0xXRXhPRGd0T1RaaE1XTmxZak00WlRSakB0aHJlYWQudjIjMA=="
      }
   }
}

```

### <a name="bot-added-for-personal-context-only"></a>Bot adicionado apenas para contexto pessoal

Seu bot recebe um `conversationUpdate` com quando um usuário o adiciona `membersAdded` diretamente para bate-papo pessoal. Neste caso, a carga que o bot recebe não contém o `channelData.team` objeto. Você deve usar isso como um filtro no caso de você querer que seu bot ofereça uma [mensagem de boas-vindas](~/resources/bot-v3/bot-conversations/bots-conv-personal.md#best-practice-welcome-messages-in-personal-conversations) diferente, dependendo do escopo.

> [!NOTE]
> Para bots com escopo pessoal, o bot receberá o `conversationUpdate` evento várias vezes, mesmo que o bot seja removido e reassume. Para o desenvolvimento e testes, você pode achar útil adicionar uma função de ajudante que permitirá que você reinicie seu bot completamente. Veja um [ exemploNode.js](https://github.com/OfficeDev/microsoft-teams-sample-complete-node/blob/master/src/middleware/SimulateResetBotChat.ts) ou [C#](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp/blob/master/template-bot-master-csharp/src/controllers/MessagesController.cs#L238) para obter mais detalhes sobre a implementação disso.

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

## <a name="team-member-or-bot-removed"></a>Membro da equipe ou bot removido

O `conversationUpdate` evento com o objeto na carga é enviado quando seu bot é removido de uma equipe ou um `membersRemoved` usuário é removido de uma equipe onde um bot foi adicionado. Microsoft Teams também adiciona `eventType.teamMemberRemoved` no `channelData` objeto. Assim como no `membersAdded` objeto, você deve analisar o `membersRemoved` objeto do ID do aplicativo do seu bot para determinar quem foi removido.

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

### <a name="user-removed-from-a-meeting"></a>Usuário removido de uma reunião

O `conversationUpdate` evento com o objeto na carga é enviado quando um usuário é removido de uma reunião agendada `membersRemoved` privada. Os detalhes do evento serão enviados mesmo quando usuários anônimos participarem da reunião. 

> [!NOTE]
>
>* Quando um usuário anônimo é removido de uma reunião, o objeto de carga de carga do MembersRemoved não tem `aadObjectId` campo.
>* Quando um usuário anônimo é removido de uma reunião, `from` o objeto na carga sempre tem a identificação do organizador do encontro, mesmo que o usuário anônimo tenha sido removido por outro apresentador.

#### <a name="schema-example-user-removed-from-meeting"></a>Exemplo de esquema: Usuário removido da reunião

```
{   
      "membersRemoved": 
        {  
          "id": "29:1Z_XHWBMhDuehhDBYoPQD6Y1DSFsTtqOZx-SA5Jh9Y4zHKm4VbFGRn7-rK7SWiW1JECwxkMdrWpHoBut2sSyQPA"   
        }   
      ],   
      "type": "conversationUpdate",   
      "timestamp": "2020-09-29T21:15:08.6391139Z",   
      "id": "f:ee8dfdf3-54ac-51de-05da-9d49514974bb",   
      "channelId": "msteams",   
      "serviceUrl": "https://canary.botapi.skype.com/amer/",   
      "from": {   
        "id": "29:1siKxZhSoTapsXvI0gyf7Gywm_HM-4kEQW4BJnWuFYVIVu87xCNP99nidgQRCcwD3L3p_schiMShzx8IDRzf8mw",   
        "aadObjectId": "f30ba569-abef-4e97-8762-35f85cbae706"   
      },   
      "conversation": {    
        "isGroup": true,   
        "tenantId": "e15762ef-a8d8-416b-871c-25516354f1fe",   
        "id": "19:meeting_MWJlNGViOTgtMGExYi00NDA3LWExODgtOTZhMWNlYjM4ZTRj@thread.v2"   
      },   
      "recipient": {   
        "id": "28:3af3604a-d4fc-486b-911e-86fab41aa91c",   
        "name": "EchoBot1_Rename"   
      },   
      "channelData": {   
        "tenant": {   
          "id": "e15762ef-a8d8-416b-871c-25516354f1fe"   
        },   
        "source": null,   
        "meeting": {   
          "id": "MCMxOTptZWV0aW5nX01XSmxOR1ZpT1RndE1HRXhZaTAwTkRBM0xXRXhPRGd0T1RaaE1XTmxZak00WlRSakB0aHJlYWQudjIjMA=="   
        }   
      }   
}
```

## <a name="team-name-updates"></a>Atualizações de nomes de equipe

> [!NOTE]
> Não há funcionalidade para consultar todos os nomes da equipe, e o nome da equipe não é retornado em cargas de outros eventos.

Seu bot é notificado quando a equipe em que está foi renomeada. Ele recebe um `conversationUpdate` evento com `eventType.teamRenamed` no `channelData` objeto. Por favor, note que não há notificações para criação ou exclusão de equipe, porque os bots existem apenas como parte das equipes e não têm visibilidade fora do escopo em que foram adicionados.

### <a name="schema-example-team-renamed"></a>Exemplo de esquema: Equipe renomeada

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

## <a name="channel-updates"></a>Atualizações do canal

Seu bot é notificado quando um canal é criado, renomeado ou excluído em uma equipe onde foi adicionado. Novamente, o `conversationUpdate` evento é recebido, e um identificador de eventos específico Teams é enviado como parte do `channelData.eventType` objeto, onde os dados do canal são `channel.id` os GUID para o canal, e contém `channel.name` o próprio nome do canal.

Os eventos do canal são os seguintes:

* **canalCriado** &emsp; Um usuário adiciona um novo canal à equipe.
* **canalRenamed** &emsp; Um usuário renomeia um canal existente.
* **canalDeclou** &emsp; Um usuário remove um canal.

### <a name="full-schema-example-channelcreated"></a>Exemplo completo de esquema: canalCriado

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

### <a name="schema-excerpt-channeldata-for-channelrenamed"></a>Trecho do esquema: channelData para channelRenamed

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

### <a name="schema-excerpt-channeldata-for-channeldeleted"></a>Trecho do esquema: channelData para canalDeleted

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

O `messageReaction` evento é enviado quando um usuário adiciona ou remove sua reação a uma mensagem que foi originalmente enviada pelo seu bot. `replyToId` contém o ID da mensagem específica.

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

### <a name="schema-example-a-user-un-likes-a-message"></a>Exemplo de esquema: um usuário desapareçam de uma mensagem

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
