---
title: Eventos de conversa
author: WashingtonKayaker
description: Trabalhe com eventos de conversa do bot do Microsoft Teams, atualizações de eventos de canal, eventos de membro da equipe e eventos de reação de mensagem com exemplos (.NET, Node.js,Python).
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: anclear
keywords: conversa reação mensagem canal bot eventos
ms.openlocfilehash: 6bf1be094afc778317f2e4d5a7657514d35b9777
ms.sourcegitcommit: 75d0072c021609af33ce584d671f610d78b3aaef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2022
ms.locfileid: "68100354"
---
# <a name="conversation-events-in-your-teams-bot"></a>Eventos de conversa em seu bot do Teams

[!INCLUDE [pre-release-label](~/includes/v4-to-v3-pointer-bots.md)]

Ao criar seus bots de conversa do Microsoft Teams, você poderá trabalhar com eventos de conversa. O Teams envia notificações ao bot de eventos de conversa que ocorrem em escopos onde o bot está ativo. Você poderá capturar esses eventos em seu código e executar as seguintes ações:

* Dispare uma mensagem de boas-vindas quando seu bot for adicionado a uma equipe.
* Dispare uma mensagem de boas-vindas quando um novo membro da equipe for adicionado ou removido.
* Dispare uma notificação quando um canal for criado, renomeado ou excluído.
* Dispare uma notificação quando uma mensagem de bot for curtida por um usuário.
* Identifique o canal padrão para o bot da entrada do usuário (seleção) durante a instalação.

## <a name="conversation-update-events"></a>Eventos de atualização de conversa

Você pode usar eventos de atualização de conversa para fornecer melhores notificações e ações efetivas de bot.

> [!IMPORTANT]
>
> * Você poderá adicionar novos eventos a qualquer momento e seu bot começará a recebê-los.
> * Você deve projetar seu bot para receber eventos inesperados.
> * Se estiver usando o SDK do Bot Framework, o bot responderá automaticamente com um `200 - OK` a todos os eventos que você escolher não manipular.

Um bot receberá um evento `conversationUpdate` em um dos seguintes casos:

* Quando o bot foi adicionado a uma conversa.
* Outros membros são adicionados ou removidos de uma conversa.
* Os metadados da conversa foram alterados.

O evento `conversationUpdate` é enviado ao seu bot quando ele recebe informações sobre atualizações de membros para as equipes onde foi adicionado. Ele também receberá uma atualização quando for adicionado pela primeira vez para conversas pessoais.

A tabela a seguir mostra uma lista de eventos de atualização de conversa do Teams com mais detalhes:

| Ação realizada        | EventType         | Método chamado              | Descrição                | Escopo |
| ------------------- | ----------------- | -------------------------- | -------------------------- | ----- |
| Canal criado     | channelCreated    | OnTeamsChannelCreatedAsync | [Um canal é criado](#channel-created). | Equipe |
| Canal renomeado     | channelRenamed    | OnTeamsChannelRenamedAsync | [Um canal é renomeado](#channel-renamed). | Equipe |
| Canal excluído     | channelDeleted    | OnTeamsChannelDeletedAsync | [Um canal é excluído](#channel-deleted). | Equipe |
| Canal restaurado    | channelRestored    | OnTeamsChannelRestoredAsync | [Um canal é restaurado](#channel-deleted). | Equipe |
| Membros adicionados   | membersAdded   | OnTeamsMembersAddedAsync   | [Um membro é adicionado](#members-added). | Tudo |
| Membros removidos | membersRemoved | OnTeamsMembersRemovedAsync | [Um membro é removido](#members-removed). | Todos |
| Equipe renomeada        | teamRenamed       | OnTeamsTeamRenamedAsync    | [Uma equipe é renomeada](#team-renamed).       | Equipe |
| Equipe excluída        | teamDeleted       | OnTeamsTeamDeletedAsync    | [Uma equipe é excluída](#team-deleted).       | Equipe |
| Equipe arquivada        | teamArchived       | OnTeamsTeamArchivedAsync    | [Uma equipe é arquivada](#team-archived).       | Equipe |
| Equipe desarquivada        | teamUnarchived       | OnTeamsTeamUnarchivedAsync    | [Uma equipe é desarquivada](#team-unarchived).       | Equipe |
| Equipe restaurada        | teamRestored      | OnTeamsTeamRestoredAsync    | [Uma equipe é restaurada](#team-restored)       | Equipe |

### <a name="channel-created"></a>Canal criado

O `channelCreated` evento é enviado ao bot sempre que um novo canal é criado em uma equipe em que o bot está instalado.

O código a seguir mostra um exemplo do evento Canal criado:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelCreatedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the Channel created");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

<!-- From sample: botbuilder-js\libraries\botbuilder\tests\teams\conversationUpdate\src\conversationUpdateBot.ts -->

```typescript

export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsChannelCreatedEvent(async (channelInfo: ChannelInfo, teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
            const card = CardFactory.heroCard('Channel Created', `${channelInfo.name} is the Channel created`);
            const message = MessageFactory.attachment(card);
            await turnContext.sendActivity(message);
            await next();
        });
    }
}

```

# <a name="json"></a>[JSON](#tab/json)

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

# <a name="python"></a>[Python](#tab/python)

```python
async def on_teams_channel_created(
 self, channel_info: ChannelInfo, team_info: TeamInfo, turn_context: TurnContext
):
 return await turn_context.send_activity(
  MessageFactory.text(
   f"The new channel is {channel_info.name}. The channel id is {channel_info.id}"
  )
 )
```

---

### <a name="channel-renamed"></a>Canal renomeado

O `channelRenamed` evento é enviado ao bot sempre que um canal é renomeado em uma equipe em que o bot está instalado.

O código a seguir mostra um exemplo do evento Canal renomeado:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelRenamedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the new Channel name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsChannelRenamedEvent(async (channelInfo: ChannelInfo, teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
            const card = CardFactory.heroCard('Channel Renamed', `${channelInfo.name} is the new Channel name`);
            const message = MessageFactory.attachment(card);
            await turnContext.sendActivity(message);
            await next();
        });
    }
```

# <a name="json"></a>[JSON](#tab/json)

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
}
```

# <a name="python"></a>[Python](#tab/python)

```python
async def on_teams_channel_renamed(
 self, channel_info: ChannelInfo, team_info: TeamInfo, turn_context: TurnContext
):
 return await turn_context.send_activity(
  MessageFactory.text(f"The new channel name is {channel_info.name}")
 )
```

---

### <a name="channel-deleted"></a>Canal excluído

O `channelDeleted` evento é enviado ao bot sempre que um canal é excluído em uma equipe em que o bot está instalado.

O código a seguir mostra um exemplo do evento Canal excluído:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelDeletedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the Channel deleted");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsChannelDeletedEvent(async (channelInfo: ChannelInfo, teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
            const card = CardFactory.heroCard('Channel Deleted', `${channelInfo.name} is the Channel deleted`);
            const message = MessageFactory.attachment(card);
            await turnContext.sendActivity(message);
            await next();
        });
    }
}

```

# <a name="json"></a>[JSON](#tab/json)

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
}
```

# <a name="python"></a>[Python](#tab/python)

```python
async def on_teams_channel_deleted(
 self, channel_info: ChannelInfo, team_info: TeamInfo, turn_context: TurnContext
):
 return await turn_context.send_activity(
  MessageFactory.text(f"The deleted channel is {channel_info.name}")
 )
```

---

### <a name="channel-restored"></a>Canal restaurado

O `channelRestored` evento é enviado para o bot sempre que um canal que foi excluído anteriormente é restaurado em uma equipe em que o bot já está instalado.

O código a seguir mostra um exemplo do evento Canal restaurado:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
protected override async Task OnTeamsChannelRestoredAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{channelInfo.Name} is the Channel restored.");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

<!-- From sample: botbuilder-js\libraries\botbuilder\tests\teams\conversationUpdate\src\conversationUpdateBot.ts -->

```typescript

export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsChannelRestoredEvent(async (channelInfo: ChannelInfo, teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
            const card = CardFactory.heroCard('Channel Restored', `${channelInfo.name} is the Channel restored`);
            const message = MessageFactory.attachment(card);
            await turnContext.sendActivity(message);
            await next();
        });
    }
}

```

# <a name="json"></a>[JSON](#tab/json)

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
        "eventType": "channelRestored",
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```

# <a name="python"></a>[Python](#tab/python)

```python
async def on_teams_channel_restored(
 self, channel_info: ChannelInfo, team_info: TeamInfo, turn_context: TurnContext
):
 return await turn_context.send_activity(
  MessageFactory.text(
   f"The restored channel is {channel_info.name}. The channel id is {channel_info.id}"
  )
 )
```

---

### <a name="members-added"></a>Membros adicionados

Um evento adicionado de membro é enviado ao bot nos seguintes cenários:

1. Quando o bot, em si, é instalado e adicionado a uma conversa

   > No contexto da equipe, `id` a conversation.id da atividade é definida como o canal selecionado pelo usuário durante a instalação do aplicativo ou o canal em que o bot foi instalado.

2. Quando um usuário é adicionado a uma conversa em que o bot está instalado

   > As IDs de usuário recebidas no conteúdo do evento são exclusivas para o bot e podem ser armazenadas em cache para uso futuro, como mensagens diretas para um usuário.

A atividade adicionada do membro `eventType` é definida para `teamMemberAdded` quando o evento é enviado de um contexto de equipe. Para determinar se o novo membro adicionado foi o próprio bot ou um usuário, verifique o `Activity` objeto do `turnContext`. Se a `MembersAdded` lista contiver `id` `id` `Recipient` um objeto em que seja o mesmo que o campo do objeto, o membro adicionado será o bot, caso contrário, será um usuário. O bot está `id` formatado como `28:<MicrosoftAppId>`.

> [!TIP]
> Use o [`InstallationUpdate` evento](#installation-update-event) para determinar quando o bot é adicionado ou removido de uma conversa.

O código a seguir mostra um exemplo do evento Membros da equipe adicionados:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
protected override async Task OnTeamsMembersAddedAsync(IList<TeamsChannelAccount> teamsMembersAdded , TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    foreach (TeamsChannelAccount member in teamsMembersAdded)
    {
        if (member.Id == turnContext.Activity.Recipient.Id)
        {
            // Send a message to introduce the bot to the team
            var heroCard = new HeroCard(text: $"The {member.Name} bot has joined {teamInfo.Name}");
            await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
        }
        else
        {
            var heroCard = new HeroCard(text: $"{member.Name} joined {teamInfo.Name}");
            await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
        }
    }
}
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsMembersAddedEvent(async (membersAdded: ChannelAccount[], teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
                let newMembers: string = '';
                console.log(JSON.stringify(membersAdded));
                membersAdded.forEach((account) => {
                    newMembers += account.id + ' ';
                });
                const name = !teamInfo ? 'not in team' : teamInfo.name;
                const card = CardFactory.heroCard('Account Added', `${newMembers} joined ${name}.`);
                const message = MessageFactory.attachment(card);
                await turnContext.sendActivity(message);
                await next();
        });
    }
}

```

# <a name="json"></a>[JSON](#tab/json)

A mensagem que seu bot recebe quando o bot é adicionado a uma equipe.

> [!NOTE]
> Nessa carga, e `conversation.id` `channelData.settings.selectedChannel.id` será a ID do canal que o usuário selecionou durante a instalação do aplicativo ou de onde a instalação foi disparada.

```json
{
    "type": "conversationUpdate",
    "membersAdded": [
        {
            "id": "28:608cacfd-1cea-40c9-b678-4b93e69bb72b"
        }
    ],
    "timestamp": "2021-12-07T22:34:56.534Z",
    "id": "f:0b9079f4-d4d3-3d8e-b883-798298053c7e",
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer/",
    "from": {
        "id": "29:1ljv6N86roXr5pjPrCJVIz6xHh5QxjI....",
        "aadObjectId": "eddfa9d4-346e-4cce-a18f-fa6261ad776b"
    },
    "conversation": {
        "isGroup": true,
        "conversationType": "channel",
        "tenantId": "b28fdbfd-2b78-4f93-b0f8-8881793f0f8f",
        "id": "19:0b7f32667e064dd9b25d7969801541f4@thread.tacv2",
        "name": "2021 Test Channel"
    },
    "recipient": {
        "id": "28:608cacfd-1cea-40c9-b678-4b93e69bb72b",
        "name": "Test Bot"
    },
    "channelData": {
        "settings": {
            "selectedChannel": {
                "id": "19:0b7f32667e064dd9b25d7969801541f4@thread.tacv2"
            }
        },
        "team": {
            "aadGroupId": "f3ec8cd2-e704-4344-8c47-9a3a21d683c0",
            "name": "TestTeam2022",
            "id": "19:zFLSDFWsesfzcmKArqKJ-65aOXJz@sgf462H2wz41@thread.tacv2"
        },
        "eventType": "teamMemberAdded",
        "tenant": {
            "id": "b28fdbfd-2b78-4f93-b0f8-8881793f0f8f"
        }
    }
}
```

A mensagem que seu bot recebe quando o bot é adicionado a um chat um-para-um.

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

# <a name="python"></a>[Python](#tab/python)

```python
async def on_teams_members_added(
 self, teams_members_added: [TeamsChannelAccount], turn_context: TurnContext
):
 for member in teams_members_added:
  await turn_context.send_activity(
   MessageFactory.text(f"Welcome your new team member {member.id}")
  )
 return
```

---

### <a name="members-removed"></a>Membros removidos

Um evento de membro removido é enviado para o bot nos seguintes cenários:

1. Quando o bot, em si, é desinstalado e removido de uma conversa.
2. Quando um usuário é removido de uma conversa em que o bot está instalado.

A atividade de membro removido `eventType` é definida como `teamMemberRemoved` quando o evento é enviado de um contexto de equipe. Para determinar se o novo membro removido foi o próprio bot ou um usuário, verifique o objeto `Activity` do `turnContext`. Se a `MembersRemoved` lista contiver `id` `id` `Recipient` um objeto em que seja o mesmo que o campo do objeto, o membro adicionado será o bot, caso contrário, será um usuário. A ID do bot está formatada como `28:<MicrosoftAppId>`.

> [!NOTE]
> Quando um usuário for excluído permanentemente de um locatário, o evento `membersRemoved conversationUpdate` será disparado.

O código a seguir mostra um exemplo do evento Membros da equipe removidos:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
protected override async Task OnTeamsMembersRemovedAsync(IList<ChannelAccount> membersRemoved, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    foreach (TeamsChannelAccount member in membersRemoved)
    {
        if (member.Id == turnContext.Activity.Recipient.Id)
        {
            // The bot was removed
            // You should clear any cached data you have for this team
        }
        else
        {
            var heroCard = new HeroCard(text: $"{member.Name} was removed from {teamInfo.Name}");
            await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
        }
    }
}
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```typescript

export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsMembersRemovedEvent(async (membersRemoved: ChannelAccount[], teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
            let removedMembers: string = '';
            console.log(JSON.stringify(membersRemoved));
            membersRemoved.forEach((account) => {
                removedMembers += account.id + ' ';
            });
            const name = !teamInfo ? 'not in team' : teamInfo.name;
            const card = CardFactory.heroCard('Account Removed', `${removedMembers} removed from ${teamInfo.name}.`);
            const message = MessageFactory.attachment(card);
            await turnContext.sendActivity(message);
            await next();
        });
    }
}

```

# <a name="json"></a>[JSON](#tab/json)

O objeto `channelData` no exemplo de conteúdo a seguir baseia-se na adição de um membro a uma equipe em vez de um chat em grupo ou ao iniciar uma nova conversa individual:

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

# <a name="python"></a>[Python](#tab/python)

```python
async def on_teams_members_removed(
 self, teams_members_removed: [TeamsChannelAccount], turn_context: TurnContext
):
 for member in teams_members_removed:
  await turn_context.send_activity(
   MessageFactory.text(f"Say goodbye to {member.id}")
  )
 return
```

---

### <a name="team-renamed"></a>Equipe renomeada

Seu bot será notificado quando a equipe for renomeada. Ele receberá um evento `conversationUpdate` com `eventType.teamRenamed` no objeto `channelData`.

O código a seguir mostra um exemplo do evento Equipe renomeada:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamRenamedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the new Team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsTeamRenamedEvent(async (teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
            const card = CardFactory.heroCard('Team Renamed', `${teamInfo.name} is the new Team name`);
            const message = MessageFactory.attachment(card);
            await turnContext.sendActivity(message);
            await next();
        });
    }
}
```

# <a name="json"></a>[JSON](#tab/json)

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

# <a name="python"></a>[Python](#tab/python)

```python
async def on_teams_team_renamed(
 self, team_info: TeamInfo, turn_context: TurnContext
):
 return await turn_context.send_activity(
  MessageFactory.text(f"The new team name is {team_info.name}")
 )
```

---

### <a name="team-deleted"></a>Equipe excluída

O bot recebe uma notificação quando a equipe é excluída. Ele receberá um evento `conversationUpdate` com `eventType.teamDeleted` no objeto `channelData`.

O código a seguir mostra um exemplo do evento Equipe excluída:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamDeletedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    //handle delete event
}
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsTeamDeletedEvent(async (teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
            //handle delete event
            await next();
        });
    }
}
```

# <a name="json"></a>[JSON](#tab/json)

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
            "name": "Team Name"
        },
        "eventType": "teamDeleted",
        "tenant": { 
           "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```

# <a name="python"></a>[Python](#tab/python)

```python
async def on_teams_team_deleted(
 self, team_info: TeamInfo, turn_context: TurnContext
):
 //handle delete event
 )
```

---

### <a name="team-restored"></a>Equipe restaurada

O bot receberá uma notificação quando uma equipe for restaurada após ser excluída. Ele receberá um evento `conversationUpdate` com `eventType.teamrestored` no objeto `channelData`.

O código a seguir mostra um exemplo do evento Equipe restaurada:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamrestoredAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsTeamrestoredEvent(async (teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
            const card = CardFactory.heroCard('Team restored', `${teamInfo.name} is the team name`);
            const message = MessageFactory.attachment(card);
            await turnContext.sendActivity(message);
            await next();
        });
    }
}
```

# <a name="json"></a>[JSON](#tab/json)

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
            "name": "Team Name"
        },
        "eventType": "teamrestored",
        "tenant": { 
           "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```

# <a name="python"></a>[Python](#tab/python)

```python
async def on_teams_team_restored(
 self, team_info: TeamInfo, turn_context: TurnContext
):
 return await turn_context.send_activity(
  MessageFactory.text(f"The team name is {team_info.name}")
 )
```

---

### <a name="team-archived"></a>Equipe arquivada

O bot receberá uma notificação quando a equipe for instalada e arquivada. Ele receberá um evento `conversationUpdate` com `eventType.teamarchived` no objeto `channelData`.

O código a seguir mostra um exemplo do evento Equipe arquivada:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamArchivedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsTeamArchivedEvent(async (teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
            const card = CardFactory.heroCard('Team archived', `${teamInfo.name} is the team name`);
            const message = MessageFactory.attachment(card);
            await turnContext.sendActivity(message);
            await next();
        });
    }
}
```

# <a name="json"></a>[JSON](#tab/json)

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
            "name": "Team Name"
        },
        "eventType": "teamArchived",
        "tenant": { 
           "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```

# <a name="python"></a>[Python](#tab/python)

```python
async def on_teams_team_archived(
 self, team_info: TeamInfo, turn_context: TurnContext
):
 return await turn_context.send_activity(
  MessageFactory.text(f"The team name is {team_info.name}")
 )
```

---

### <a name="team-unarchived"></a>Equipe desarquivada

O bot receberá uma notificação quando a equipe for instalada e desarquivada. Ele receberá um evento `conversationUpdate` com `eventType.teamUnarchived` no objeto `channelData`.

O código a seguir mostra um exemplo do evento Equipe desarquivada:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
protected override async Task OnTeamsTeamUnarchivedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var heroCard = new HeroCard(text: $"{teamInfo.Name} is the team name");
    await turnContext.SendActivityAsync(MessageFactory.Attachment(heroCard.ToAttachment()), cancellationToken);
}
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onTeamsTeamUnarchivedEvent(async (teamInfo: TeamInfo, turnContext: TurnContext, next: () => Promise<void>): Promise<void> => {
            const card = CardFactory.heroCard('Team archived', `${teamInfo.name} is the team name`);
            const message = MessageFactory.attachment(card);
            await turnContext.sendActivity(message);
            await next();
        });
    }
}
```

# <a name="json"></a>[JSON](#tab/json)

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
            "name": "Team Name"
        },
        "eventType": "teamUnarchived",
        "tenant": { 
           "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    }
}
```

# <a name="python"></a>[Python](#tab/python)

```python
async def on_teams_team_unarchived(
 self, team_info: TeamInfo, turn_context: TurnContext
):
 return await turn_context.send_activity(
  MessageFactory.text(f"The team name is {team_info.name}")
 )
```

---

Agora que você trabalhou com os eventos de atualização de conversa, você pode entender os eventos de reação de mensagem que ocorrem para diferentes reações a uma mensagem.

## <a name="message-reaction-events"></a>Eventos de reação de mensagem

O `messageReaction` evento é enviado quando um usuário adiciona ou remove reações a uma mensagem, que foi enviada pelo bot. O `replyToId` contém a ID da mensagem e o `Type` é o tipo de reação no formato de texto. Os tipos de reações incluem irritado, coração, gargalhada, curtir, triste e surpreso. Esse evento não contém o conteúdo da mensagem original. Se o processamento de reações às suas mensagens for importante para o bot, você deverá armazenar as mensagens ao enviá-las. A tabela a seguir fornece mais informações sobre o tipo de evento e os objetos do conteúdo:

| EventType       | Objeto do conteúdo   | Descrição                                                             | Escopo |
| --------------- | ---------------- | ----------------------------------------------------------------------- | ----- |
| messageReaction | reactionsAdded   | [Reações adicionadas à mensagem do bot](#reactions-added-to-bot-message).           | Tudo   |
| messageReaction | reactionsRemoved | [Reações removidas da mensagem do bot](#reactions-removed-from-bot-message). | Tudo |

### <a name="reactions-added-to-bot-message"></a>Reações adicionadas à mensagem do bot

O código a seguir mostra um exemplo de reações a uma mensagem do bot:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
protected override async Task OnReactionsAddedAsync(IList<MessageReaction> messageReactions, ITurnContext<IMessageReactionActivity> turnContext, CancellationToken cancellationToken)
{
    foreach (var reaction in messageReactions)
    {
      var newReaction = $"You reacted with '{reaction.Type}' to the following message: '{turnContext.Activity.ReplyToId}'";
      var replyActivity = MessageFactory.Text(newReaction);
      var resourceResponse = await turnContext.SendActivityAsync(replyActivity, cancellationToken);
    }
}
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

<!-- Verify -->

```typescript

export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onReactionsAdded(async (context, next) => {
           const reactionsAdded = context.activity.reactionsAdded;
            if (reactionsAdded && reactionsAdded.length > 0) {
                for (let i = 0; i < reactionsAdded.length; i++) {
                    const reaction = reactionsAdded[i];
                    const newReaction = `You reacted with '${reaction.type}' to the following message: '${context.activity.replyToId}'`;
                    const resourceResponse = context.sendActivity(newReaction);
                    // Save information about the sent message and its ID (resourceResponse.id).
                }
            }
        });
    }
}

```

# <a name="json"></a>[JSON](#tab/json)

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
    "replyToId": "1575667808184",
    "legacy": {
      "replyToId": "1:19uJ8TZA1cZcms7-2HLOW3pWRF4nSWEoVnRqc0DPa_kY"
    }
}
```

# <a name="python"></a>[Python](#tab/python)

```python
async def on_reactions_added(
 self, message_reactions: List[MessageReaction], turn_context: TurnContext
):
 for reaction in message_reactions:
  activity = await self._log.find(turn_context.activity.reply_to_id)
  if not activity:
   await self._send_message_and_log_activity_id(
    turn_context,
    f"Activity {turn_context.activity.reply_to_id} not found in log",
   )
  else:
   await self._send_message_and_log_activity_id(
    turn_context,
    f"You added '{reaction.type}' regarding '{activity.text}'",
   )
 return
```

---

### <a name="reactions-removed-from-bot-message"></a>Reações removidas da mensagem do bot

O código a seguir mostra um exemplo de reações removidas da mensagem do bot:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
protected override async Task OnReactionsRemovedAsync(IList<MessageReaction> messageReactions, ITurnContext<IMessageReactionActivity> turnContext, CancellationToken cancellationToken)
{
    foreach (var reaction in messageReactions)
    {
      var newReaction = $"You removed the reaction '{reaction.Type}' from the following message: '{turnContext.Activity.ReplyToId}'";
      var replyActivity = MessageFactory.Text(newReaction);
      var resourceResponse = await turnContext.SendActivityAsync(replyActivity, cancellationToken);
    }
}
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

<!-- Verify -->

```typescript
export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onReactionsRemoved(async(context,next)=>{
            const reactionsRemoved = context.activity.reactionsRemoved;
            if (reactionsRemoved && reactionsRemoved.length > 0) {
                for (let i = 0; i < reactionsRemoved.length; i++) {
                    const reaction = reactionsRemoved[i];
                    const newReaction = `You removed the reaction '${reaction.type}' from the message: '${context.activity.replyToId}'`;
                    const resourceResponse = context.sendActivity(newReaction);
                    // Save information about the sent message and its ID (resourceResponse.id).
                }
            }
        });
    }
}
```

# <a name="json"></a>[JSON](#tab/json)

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
    "replyToId": "1575667808184",
    "legacy": {
      "replyToId": "1:19uJ8TZA1cZcms7-2HLOW3pWRF4nSWEoVnRqc0DPa_kY"
    }
}
```

# <a name="python"></a>[Python](#tab/python)

```python
async def on_reactions_removed(
 self, message_reactions: List[MessageReaction], turn_context: TurnContext
):
 for reaction in message_reactions:
  activity = await self._log.find(turn_context.activity.reply_to_id)
  if not activity:
   await self._send_message_and_log_activity_id(
    turn_context,
    f"Activity {turn_context.activity.reply_to_id} not found in log",
   )
  else:
   await self._send_message_and_log_activity_id(
    turn_context,
    f"You removed '{reaction.type}' regarding '{activity.text}'",
   )
 return
```

---

## <a name="installation-update-event"></a>Evento de atualização de instalação

O bot receberá um evento `installationUpdate` quando você instalar um bot em uma thread da conversa. A desinstalação do bot da thread também disparará o evento. Ao instalar um bot, o campo **ação** no evento será definido como *adicionar*, e quando o bot for desinstalado, o campo **ação** será definido como *remover*.

> [!NOTE]
> Quando você atualiza um aplicativo e, em seguida, adiciona ou remove um bot, a ação também dispara o evento `installationUpdate`. O campo **ação** será definido como *add-upgrade* se você adicionar um bot ou *remove-upgrade* se você remover um bot.

### <a name="install-update-event"></a>Evento Instalar atualização

Use o evento `installationUpdate` para enviar uma mensagem introdutória do bot na instalação. Esse evento ajuda você a atender aos seus requisitos de privacidade e retenção. Você também poderá limpar e excluir dados de usuário ou thread quando o bot for desinstalado.

`conversationUpdate` Semelhante ao evento enviado quando o bot é adicionado a `installationUpdate` uma equipe, o conversation.id do evento é definido como a ID do canal selecionado por um usuário durante a instalação do aplicativo ou o canal em que a instalação ocorreu. A ID representa o canal em que o usuário pretende que o bot opere e deve ser usada pelo bot ao enviar uma mensagem de boas-vindas. Para cenários em que a ID do canal Geral é explicitamente necessária, você pode obtê-la em `team.id` `channelData`.

Neste exemplo, o e `conversation.id` as atividades `conversationUpdate` `installationUpdate` serão definidos como a ID do canal de resposta na equipe de Demonstração de Daves.

![Criar um canal selecionado](~/assets/videos/addteam.gif)

> [!NOTE]
> A ID de canal selecionada só é definida em `installationUpdate` *adicionar* eventos que são enviados quando um aplicativo é instalado em uma equipe.

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
protected override async Task OnInstallationUpdateActivityAsync(ITurnContext<IInstallationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    var activity = turnContext.Activity;
    if (string.Equals(activity.Action, "Add", StringComparison.InvariantCultureIgnoreCase))
    {
        // TO:DO Installation workflow
    }
    else
    {
        // TO:DO Uninstallation workflow
    }
    return;
}
```

Você também poderá usar um manipulador dedicado para cenários *adicionar* ou *remover* como um método alternativo para capturar um evento.

```csharp
protected override async Task OnInstallationUpdateAddAsync(ITurnContext<IInstallationUpdateActivity> turnContext, CancellationToken cancellationToken)
{
    // TO:DO Installation workflow return;
}
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```typescript
async onInstallationUpdateActivity(context: TurnContext) {
        var activity = context.activity.action;
        if(activity == "Add") {
            await context.sendActivity(MessageFactory.text("Added"));
        }
        else {
            await context.sendActivity(MessageFactory.text("Uninstalled"));
        }
    }
```

# <a name="json"></a>[JSON](#tab/json)

```json
{
    {
    "type": "installationUpdate",
    "id": "f:816eb23d-bfa1-afa3-dfeb-d2aa338e9541",
    "timestamp": "2021-11-09T04:47:30.91Z",
    "serviceUrl": "https://smba.trafficmanager.net/amer/",
    "channelId": "msteams",
    "from": {
        "id": "29:1ljv6N86roXr5pjPrCJVIz6xHh5QxjI....",
        "aadObjectId": "eddfa9d4-346e-4cce-a18f-fa6261ad776b"
    },
    "recipient": {
        "id": "28:608cacfd-1cea-40c9-b678-4b93e69bb72b",
        "name": "Test Bot"
    },
    "locale": "en-US",
    "entities": [
        {
            "type": "clientInfo",
            "locale": "en-US"
        }
    ],
    "conversation": {
        "isGroup": true,
        "id": "19:0b7f32667e064dd9b25d7969801541f4@thread.tacv2",
        "name": "2021 Test Channel",
        "conversationType": "channel",
        "tenantId": "b28fdbfd-2b78-4f93-b0f8-8881793f0f8f"
    },
    "channelData": {
        "settings": {
            "selectedChannel": {
                "id": "19:0b7f32667e064dd9b25d7969801541f4@thread.tacv2"
            }
        },
        "channel": {
            "id": "19:0b7f32667e064dd9b25d7969801541f4@thread.tacv2"
        },
        "team": {
            "aadGroupId": "da849743-4259-475f-ae7a-4f4b0fb49943",
            "name": "TestTeam2022",
            "id": "19:zFLSDFWsesfzcmKArqKJ-65aOXJz@sgf462H2wz41@thread.tacv2"
        },
        "tenant": {
            "id": "b28fdbfd-2b78-4f93-b0f8-8881793f0f8f"
        },
        "source": {
            "name": "message"
        }
    },
    "action": "add"
    }
```

# <a name="python"></a>[Python](#tab/python)

```python
async def on_installation_update(self, turn_context: TurnContext):
   if turn_context.activity.action == "add":   
       await turn_context.send_activity(MessageFactory.text("Added"))
   else:
       await turn_context.send_activity(MessageFactory.text("Uninstalled"))
```

---

## <a name="uninstall-behavior-for-personal-app-with-bot"></a>Comportamento de desinstalação do aplicativo pessoal com o bot

Quando você desinstalar um aplicativo, o bot também será desinstalado. Quando um usuário enviar uma mensagem para seu aplicativo, ele receberá um código de resposta 403. Seu bot receberá um código de resposta 403 para novas mensagens postadas pelo bot. O comportamento pós-desinstalação de bots no escopo pessoal com os escopos do Teams e do groupChat agora está alinhado. Você não pode enviar ou receber mensagens depois que um aplicativo é desinstalado.

:::image type="content" source="../../../assets/images/bots/uninstallbot.png" alt-text="Código de resposta de desinstalação"lightbox="../../../assets/images/bots/uninstallbot.png"border="true":::

## <a name="event-handling-for-install-and-uninstall-events"></a>Manipulação de eventos para instalar e desinstalar eventos

Quando você usa esses eventos de instalação e desinstalação, há algumas instâncias em que os bots oferecem exceções ao receber eventos inesperados do Teams, que ocorrem nos seguintes casos:

* Você projeta seu bot sem o SDK do Microsoft Bot Framework e, como resultado, o bot fornece uma exceção ao receber um evento inesperado.
* Você projeta seu bot com o SDK do Microsoft Bot Framework e seleciona alterar o comportamento padrão do evento substituindo o identificador de evento base.

É importante saber que novos eventos podem ser adicionados a qualquer momento no futuro e seu bot começa a recebê-los. Portanto, você deve projetar considerando a possibilidade de receber eventos inesperados. Se você estiver usando o SDK do Bot Framework, o bot responderá automaticamente com um 200 – OK para todos os eventos que você não escolher manipular.

## <a name="code-sample"></a>Exemplo de código

| **Nome de exemplo** | **Descrição** | **.NET** | **Node.js** | **Python** |
|----------|-----------------|----------|
| Bot de conversa | Código de exemplo de eventos de conversa de bots. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/57.teams-conversation-bot)  | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/57.teams-conversation-bot) | [Exibir](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot) |

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Enviar mensagens proativas](~/bots/how-to/conversations/send-proactive-messages.md)
