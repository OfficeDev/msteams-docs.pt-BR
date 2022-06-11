---
title: Manipuladores de atividade de bot
author: surbhigupta
description: Entenda os manipuladores de atividades de bot no Teams.
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: anclear
keywords: evento do canal de consentimento do cartão bot da estrutura do manipulador de atividades
ms.openlocfilehash: 8bf1638274c8d83c8483df13556927d98b4d8cb5
ms.sourcegitcommit: 12510f34b00bfdd0b0e92d35c8dbe6ea1f6f0be2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2022
ms.locfileid: "66032918"
---
# <a name="bot-activity-handlers"></a>Manipuladores de atividade de bot

Este documento se baseia no artigo sobre [como os bots funcionam](https://aka.ms/how-bots-work) na principal [Documentação Bot Framework](https://aka.ms/azure-bot-service-docs). A principal diferença entre os bots desenvolvidos para o Microsoft Teams e o Bot Framework principal está nos recursos fornecidos no Teams.

Para organizar a lógica de conversação do seu bot, é usado um manipulador de atividades. As atividades são tratadas de duas maneiras usando os manipuladores de atividades do Teams e a lógica de bot. O manipulador de atividades do Teams adiciona suporte para interações e eventos específicos do Microsoft Teams. O objeto de bot contém o raciocínio ou a lógica de conversação para um turno e expõe um manipulador de turnos, que é o método que pode aceitar atividades de entrada do adaptador de bot.

## <a name="teams-activity-handlers"></a>Manipuladores de atividades do Teams

O manipulador de atividades do Teams é derivado do manipulador de atividades do Microsoft Bot Framework. Ele roteia todas as atividades do Teams antes de permitir que as atividades específicas que não sejam do Teams sejam tratadas.

Quando um bot Teams recebe uma atividade, ele é roteado para os manipuladores de atividade. Todas as atividades são roteadas por meio de um manipulador base chamado manipulador de turnos. O manipulador de turnos chama o manipulador de atividades necessário para gerenciar qualquer atividade recebida. O bot do Teams é derivado da classe `TeamsActivityHandler`, que é derivada da classe `ActivityHandler` do Bot Framework.

> [!NOTE]
> Se a atividade do bot levar mais de 15 segundos para ser processda, Teams uma solicitação de repetição para o ponto de extremidade do bot. Portanto, você verá solicitações duplicadas em seu bot.

# <a name="c"></a>[C#](#tab/csharp)

Os bots são criados usando o Bot Framework. Se os bots receberem uma atividade de mensagem, o manipulador de turnos receberá uma notificação dessa atividade de entrada. Em seguida, o manipulador de turnos envia a atividade de entrada para o manipulador de atividades `OnMessageActivityAsync`. No Teams, essa funcionalidade permanece a mesma. Se o bot receber uma atividade de atualização de conversa, o manipulador de turnos receberá uma notificação dessa atividade de entrada e enviará a atividade de entrada para o `OnConversationUpdateActivityAsync`. Primeiro, o manipulador de atividades do Teams verifica se há eventos específicos do Teams. Se nenhum evento for encontrado, ele as passará para o manipulador de atividades do Bot Framework.

Na classe do manipulador de atividades do Teams, há dois manipuladores de atividades principais do Teams, `OnConversationUpdateActivityAsync` e `OnInvokeActivityAsync`. A classe `OnConversationUpdateActivityAsync` roteia todas as atividades de atualização de conversa e a classe `OnInvokeActivityAsync` roteia todas as atividades de invocação do Teams.

Para implementar sua lógica de manipuladores de atividades específicos do Teams, você deve substituir os métodos em seu bot, conforme mostrado na seção [lógica do bot](#bot-logic). Não há nenhuma implementação base para esses manipuladores, portanto, você deve adicionar a lógica desejada em sua substituição.

Os trechos de código para manipuladores de atividades do Teams:

`OnTeamsChannelCreatedAsync`

```csharp

protected override Task OnTeamsChannelCreatedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
        {
            // Code logic here
        }
```

`OnTeamsChannelDeletedAsync`

```csharp

protected override Task OnTeamsChannelDeletedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
        {
            // Code logic here
        }
```

`OnTeamsChannelRenamedAsync`

```csharp

protected override Task OnTeamsChannelRenamedAsync(ChannelInfo channelInfo, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
  {
   // Code logic here
  }
```

`OnTeamsTeamRenamedAsync`

```csharp

protected override Task OnTeamsTeamRenamedAsync(TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
  {
   // Code logic here
  }
```

`OnTeamsMembersAddedAsync`

```csharp

protected override Task OnTeamsMembersAddedAsync(IList<TeamsChannelAccount> teamsMembersAdded, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken)
  {
   // Code logic here
  }
```

`OnTeamsMembersRemovedAsync`

```csharp

protected override Task OnTeamsMembersRemovedAsync(IList<TeamsChannelAccount> teamsMembersRemoved, TeamInfo teamInfo, ITurnContext<IConversationUpdateActivity> turnContext, CancellationToken cancellationToken);
  {
   // Code logic here
  }
```

# <a name="javascript"></a>[JavaScript](#tab/javascript)

Os bots são criados usando o Bot Framework. Se os bots receberem uma atividade de mensagem, o manipulador de turnos receberá uma notificação dessa atividade de entrada. Em seguida, o manipulador de turnos envia a atividade de entrada para o manipulador de atividades `onMessage`. No Teams, essa funcionalidade permanece a mesma. Se o bot receber uma atividade de atualização de conversa, o manipulador de turnos receberá uma notificação dessa atividade de entrada e enviará a atividade de entrada para o `dispatchConversationUpdateActivity`. Primeiro, o manipulador de atividades do Teams verifica se há eventos específicos do Teams. Se nenhum evento for encontrado, ele as passará para o manipulador de atividades do Bot Framework.

Na classe do manipulador de atividades do Teams, há dois manipuladores de atividades principais do Teams, `dispatchConversationUpdateActivity` e `onInvokeActivity`. A classe `dispatchConversationUpdateActivity` roteia todas as atividades de atualização de conversa e a classe `onInvokeActivity` roteia todas as atividades de invocação do Teams.

Para implementar sua lógica de manipuladores de atividades específicos do Teams, você deve substituir os métodos em seu bot, conforme mostrado na seção [lógica do bot](#bot-logic). Defina sua lógica de bot para esses manipuladores e, em seguida, certifique-se de chamar `next()` no final. Ao chamar `next()`, você garante que o próximo manipulador seja executado.

Os trechos de código para manipuladores de atividades do Teams:

`OnTeamsChannelCreatedAsync`

```javascript

onTeamsChannelCreated(async (channelInfo, teamInfo, context, next) => {
       // code for handling
        await next()
    });
```

`OnTeamsChannelDeletedAsync`

```javascript

onTeamsChannelDeleted(async (channelInfo, teamInfo, context, next) => {
       // code for handling
       await next()
    });
```

`OnTeamsChannelRenamedAsync`

```javascript

onTeamsChannelRenamed(async (channelInfo, teamInfo, context, next) => {
       // code for handling
       await next()
    });
```

`OnTeamsTeamRenamedAsync`

```javascript

onTeamsTeamRenamedAsync(async (teamInfo, context, next) => {
       // code for handling
       await next()
    });
```

`OnTeamsMembersAddedAsync`

```javascript

onTeamsMembersAdded(async (membersAdded, teamInfo, context, next) => {
       // code for handling
    await next();
    });
```

`OnTeamsMembersRemovedAsync`

```javascript

onTeamsMembersRemoved(async (membersRemoved, teamInfo, context, next) => {
       // code for handling
    await next();
    });
```

# <a name="python"></a>[Python](#tab/python)

Os bots são criados usando o Bot Framework. Se os bots receberem uma atividade de mensagem, o manipulador de turnos receberá uma notificação dessa atividade de entrada. Em seguida, o manipulador de turnos envia a atividade de entrada para o manipulador de atividades `on_message_activity`. No Teams, essa funcionalidade permanece a mesma. Se o bot receber uma atividade de atualização de conversa, o manipulador de turnos receberá uma notificação dessa atividade de entrada e enviará a atividade de entrada para o `on_conversation_update_activity`. Primeiro, o manipulador de atividades do Teams verifica se há eventos específicos do Teams. Se nenhum evento for encontrado, ele as passará para o manipulador de atividades do Bot Framework.

Na classe do manipulador de atividades do Teams, há dois manipuladores de atividades principais do Teams, `on_conversation_update_activity` e `on_invoke_activity`. A classe `on_conversation_update_activity` roteia todas as atividades de atualização de conversa e a classe `on_invoke_activity` roteia todas as atividades de invocação do Teams.

Para implementar sua lógica de manipuladores de atividades específicos do Teams, você deve substituir os métodos em seu bot, conforme mostrado na seção [lógica do bot](#bot-logic). Não há nenhuma implementação base para esses manipuladores, portanto, você deve adicionar a lógica desejada em sua substituição.

---

## <a name="bot-logic"></a>Lógica do bot

A lógica do bot processa atividades de entrada de um ou mais de seus canais de bot e, em resposta, gera atividades de saída. Ele ainda é verdadeiro para bots derivados da classe de manipulador de Teams atividade, que primeiro verifica se há Teams atividades. Depois de verificar as atividades do Teams, ele passa todas as outras atividades para o manipulador de atividades do Bot Framework.

# <a name="c"></a>[C#](#tab/csharp)

#### <a name="core-bot-framework-handlers"></a>Manipuladores Principais do Bot Framework

>[!NOTE]
>
>* Exceto para as atividades dos membros **adicionados** e **removidos**, todos os manipuladores de atividades descritos nesta seção continuam funcionando como fazem com um bot que não é do Teams.
>* O método `onInstallationUpdateActivityAsync()` é usado para obter a Localidade do Teams ao adicionar o bot ao Teams.

Os manipuladores de atividade são diferentes no contexto de uma equipe, onde um novo membro é adicionado à equipe em vez de um thread de mensagens.

A lista de manipuladores definidos `ActivityHandler` inclui o seguinte:

| Evento | Manipulador | Descrição |
| :-- | :-- | :-- |
| Qualquer tipo de atividade recebida | `OnTurnAsync` | Esse método chama um dos outros manipuladores, com base no tipo de atividade recebida. |
| Atividade de mensagem recebida | `OnMessageActivityAsync` | Esse método pode ser substituído para manipular uma atividade de `Message`. |
| Atividade de atualização de conversa recebida | `OnConversationUpdateActivityAsync` | Esse método chama um manipulador se outros membros que não sejam o bot ingressaram ou saíram da conversa, em uma atividade de `ConversationUpdate`. |
| Membros que não são bots ingressaram na conversa | `OnMembersAddedAsync` | Esse método pode ser substituído para manipular membros que ingressam em uma conversa. |
| Membros que não são bots saíram da conversa | `OnMembersRemovedAsync` | Esse método pode ser substituído para manipular membros que saem de uma conversa. |
| Atividade de evento recebida | `OnEventActivityAsync` | Esse método chama um manipulador específico para o tipo de evento, em uma atividade de `Event`. |
| Atividade de evento de resposta de token recebida | `OnTokenResponseEventAsync` | Esse método pode ser substituído para manipular eventos de resposta de token. |
| Atividade de evento de resposta sem token recebida | `OnEventAsync` | Esse método pode ser substituído para manipular outros tipos de eventos. |
| Outro tipo de atividade recebida | `OnUnrecognizedActivityTypeAsync` | Esse método pode ser substituído para manipular qualquer tipo de atividade que não seria manipulada. |

#### <a name="teams-specific-activity-handlers"></a>Manipuladores de atividades específicos do Teams

O manipulador `TeamsActivityHandler` estende a lista de manipuladores na seção principal de manipuladores do Bot Framework para incluir o seguinte:

| Evento | Manipulador | Descrição |
| :-- | :-- | :-- |
| channelCreated | `OnTeamsChannelCreatedAsync` | Esse método pode ser substituído para manipular um canal do Teams sendo criado. Para saber mais, veja [canal criado](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| channelDeleted | `OnTeamsChannelDeletedAsync` | Esse método pode ser substituído para manipular um canal do Teams sendo excluído. Para saber mais, veja [canal excluído](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| channelRenamed | `OnTeamsChannelRenamedAsync` | Esse método pode ser substituído para manipular um canal do Teams sendo renomeado. Para saber mais, veja [canal renomeado](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| teamRenamed | `OnTeamsTeamRenamedAsync` | `return Task.CompletedTask;` Esse método pode ser substituído para manipular uma equipe do Teams sendo renomeada. Para saber mais, veja [equipe renomeada](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| MembersAdded | `OnTeamsMembersAddedAsync` | Esse método chama o método `OnMembersAddedAsync` no `ActivityHandler`. O método pode ser substituído para manipular membros que ingressam em uma equipe. Para saber mais, veja [membros da equipe adicionados](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-added) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| MembersRemoved | `OnTeamsMembersRemovedAsync` | Esse método chama o método `OnMembersRemovedAsync` no `ActivityHandler`. O método pode ser substituído para manipular membros que saem de uma equipe. Para saber mais, veja [membros da equipe removidos](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-removed) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|

#### <a name="teams-invoke-activities"></a>Atividades de invocação do Teams

A lista de Teams manipuladores de atividade chamados do manipulador `OnInvokeActivityAsync` de Teams de atividade inclui o seguinte:

| Invocar tipos                    | Manipulador                              | Descrição                                                  |
| :-----------------------------  | :----------------------------------- | :----------------------------------------------------------- |
| CardAction.Invoke               | `OnTeamsCardActionInvokeAsync`       | Esse método é invocado quando uma atividade de invocação de ação de cartão é recebida do conector. |
| fileConsent/invoke              | `OnTeamsFileConsentAcceptAsync`      | Esse método é invocado quando um cartão de consentimento de arquivo é aceito pelo usuário. |
| fileConsent/invoke              | `OnTeamsFileConsentAsync`            | Esse método é invocado quando uma atividade de cartão de consentimento de arquivo é recebida do conector. |
| fileConsent/invoke              | `OnTeamsFileConsentDeclineAsync`     | Esse método é invocado quando um cartão de consentimento de arquivo é recusado pelo usuário. |
| actionableMessage/executeAction | `OnTeamsO365ConnectorCardActionAsync` | Esse método é invocado quando uma Office 365 de ação do cartão do conector é recebida do conector. |
| signin/verifyState              | `OnTeamsSigninVerifyStateAsync`      | Esse método é invocado quando uma atividade de estado de verificação de entrada é recebida do conector. |
| task/fetch                      | `OnTeamsTaskModuleFetchAsync`        | Esse método pode ser substituído em uma classe derivada para fornecer lógica quando um módulo de tarefa é buscado. |
| task/submit                     | `OnTeamsTaskModuleSubmitAsync`       | Esse método pode ser substituído em uma classe derivada para fornecer lógica quando um módulo de tarefa é enviado. |

As atividades invoke listadas nesta seção são para bots de conversação Teams. O Bot Framework SDK também é compatível com atividades de invocação específicas para extensões de mensagem. Para saber mais, confira [o que são extensões de mensagem](https://aka.ms/azure-bot-what-are-messaging-extensions).

# <a name="javascript"></a>[JavaScript](#tab/javascript)

#### <a name="core-bot-framework-handlers"></a>Manipuladores Principais do Bot Framework

>[!NOTE]
> Exceto para as atividades dos membros **adicionados** e **removidos**, todos os manipuladores de atividades descritos nesta seção continuam funcionando como fazem com um bot que não é do Teams.

Os manipuladores de atividade são diferentes no contexto de uma equipe, onde o novo membro é adicionado à equipe em vez de um thread de mensagens.

A lista de manipuladores definidos `ActivityHandler` inclui o seguinte:

| Evento | Manipulador | Descrição |
| :-- | :-- | :-- |
| Qualquer tipo de atividade recebida | `onTurn` | Esse método chama um dos outros manipuladores, com base no tipo de atividade recebida. |
| Atividade de mensagem recebida | `onMessage` | Esse método ajuda a manipular uma atividade de `Message`. |
| Atividade de atualização de conversa recebida | `onConversationUpdate` | Esse método chama um manipulador se outros membros que não sejam o bot ingressaram ou saíram da conversa, em uma atividade de `ConversationUpdate`. |
| Membros que não são bots ingressaram na conversa | `onMembersAdded` | Esse método ajuda a manipular membros que ingressam em uma conversa. |
| Membros que não são bots saíram da conversa | `onMembersRemoved` | Esse método ajuda a manipular membros que saem de uma conversa. |
| Atividade de evento recebida | `onEvent` | Esse método chama um manipulador específico para o tipo de evento, em uma atividade de `Event`. |
| Atividade de evento de resposta de token recebida | `onTokenResponseEvent` | Esse método ajuda a manipular eventos de resposta de token. |
| Outro tipo de atividade recebida | `onUnrecognizedActivityType` | Esse método ajuda a manipular qualquer tipo de atividade que não seria manipulada. |

#### <a name="teams-specific-activity-handlers"></a>Manipuladores de atividades específicos do Teams

O manipulador `TeamsActivityHandler` estende a lista de manipuladores na seção principal de manipuladores do Bot Framework para incluir o seguinte:

| Evento | Manipulador | Descrição |
| :-- | :-- | :-- |
| channelCreated | `OnTeamsChannelCreatedAsync` | Esse método pode ser substituído para manipular um canal do Teams sendo criado. Para saber mais, veja [canal criado](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| channelDeleted | `OnTeamsChannelDeletedAsync` | Esse método pode ser substituído para manipular um canal do Teams sendo excluído. Para saber mais, veja [canal excluído](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| channelRenamed | `OnTeamsChannelRenamedAsync` | Esse método pode ser substituído para manipular um canal do Teams sendo renomeado. Para saber mais, veja [canal renomeado](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| teamRenamed | `OnTeamsTeamRenamedAsync` | `return Task.CompletedTask;` Esse método pode ser substituído para manipular uma equipe do Teams sendo renomeada. Para saber mais, veja [equipe renomeada](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| MembersAdded | `OnTeamsMembersAddedAsync` | Esse método chama o método `OnMembersAddedAsync` no `ActivityHandler`. O método pode ser substituído para manipular membros que ingressam em uma equipe. Para saber mais, veja [membros da equipe adicionados](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-added) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| MembersRemoved | `OnTeamsMembersRemovedAsync` | Esse método chama o método `OnMembersRemovedAsync` no `ActivityHandler`. O método pode ser substituído para manipular membros que saem de uma equipe. Para saber mais, veja [membros da equipe removidos](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-removed) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events). |

#### <a name="teams-invoke-activities"></a>Atividades de invocação do Teams

A lista de Teams manipuladores de atividade chamados do manipulador `onInvokeActivity` de Teams de atividade inclui o seguinte:

| Invocar tipos                    | Manipulador                              | Descrição                                                  |
| :-----------------------------  | :----------------------------------- | :----------------------------------------------------------- |
| CardAction.Invoke               | `handleTeamsCardActionInvoke`       | Esse método é invocado quando uma atividade de invocação de ação de cartão é recebida do conector. |
| fileConsent/invoke              | `handleTeamsFileConsentAccept`      | Esse método é invocado quando um cartão de consentimento de arquivo é aceito pelo usuário. |
| fileConsent/invoke              | `handleTeamsFileConsent`            | Esse método é invocado quando uma atividade de cartão de consentimento de arquivo é recebida do conector. |
| fileConsent/invoke              | `handleTeamsFileConsentDecline`     | Esse método é invocado quando um cartão de consentimento de arquivo é recusado pelo usuário. |
| actionableMessage/executeAction | `handleTeamsO365ConnectorCardAction` | Esse método é invocado quando uma Office 365 de ação do cartão do conector é recebida do conector. |
| signin/verifyState              | `handleTeamsSigninVerifyState`      | Esse método é invocado quando uma atividade de estado de verificação de entrada é recebida do conector. |
| task/fetch                      | `handleTeamsTaskModuleFetch`        | Esse método pode ser substituído em uma classe derivada para fornecer lógica quando um módulo de tarefa é buscado. |
| task/submit                     | `handleTeamsTaskModuleSubmit`       | Esse método pode ser substituído em uma classe derivada para fornecer lógica quando um módulo de tarefa é enviado. |

As atividades de invocação listadas nesta seção são para bots de conversação no Teams. O Bot Framework SDK também é compatível com atividades de invocação específicas para extensões de mensagem. Para saber mais, confira [o que são extensões de mensagem](https://aka.ms/azure-bot-what-are-messaging-extensions).

# <a name="python"></a>[Python](#tab/python)

#### <a name="core-bot-framework-handlers"></a>Manipuladores Principais do Bot Framework

>[!NOTE]
> Exceto para as atividades dos membros **adicionados** e **removidos**, todos os manipuladores de atividades descritos nesta seção continuam funcionando como fazem com um bot que não é do Teams.

Os manipuladores de atividade são diferentes no contexto de uma equipe, onde o novo membro é adicionado à equipe em vez de um thread de mensagens.

A lista de manipuladores definidos `ActivityHandler` inclui o seguinte:

| Evento | Manipulador | Descrição |
| :-- | :-- | :-- |
| Qualquer tipo de atividade recebida | `on_turn` | Esse método chama um dos outros manipuladores, com base no tipo de atividade recebida. |
| Atividade de mensagem recebida | `on_message_activity` | Esse método pode ser substituído para manipular uma atividade de `Message`. |
| Atividade de atualização de conversa recebida | `on_conversation_update_activity` | Esse método chama um manipulador se outros membros que não sejam o bot entrarem ou saírem da conversa. |
| Membros que não são bots ingressaram na conversa | `on_members_added_activity` | Esse método pode ser substituído para manipular membros que ingressam em uma conversa. |
| Membros que não são bots saíram da conversa | `on_members_removed_activity` | Esse método pode ser substituído para manipular membros que saem de uma conversa. |
| Atividade de evento recebida | `on_event_activity` | Esse método chama um manipulador específico para o tipo de evento. |
| Atividade de evento de resposta de token recebida | `on_token_response_event` | Esse método pode ser substituído para manipular eventos de resposta de token. |
| Atividade de evento de resposta sem token recebida | `on_event` | Esse método pode ser substituído para manipular outros tipos de eventos. |
| Outros tipos de atividade recebidas | `on_unrecognized_activity_type` | Esse método pode ser substituído para lidar com qualquer tipo de atividade que não seja tratada. |

#### <a name="teams-specific-activity-handlers"></a>Manipuladores de atividades específicos do Teams

O manipulador `TeamsActivityHandler` estende a lista de manipuladores da seção principal de manipuladores do Bot Framework para incluir o seguinte:

| Evento | Manipulador | Descrição |
| :-- | :-- | :-- |
| channelCreated | `on_teams_channel_created` | Esse método pode ser substituído para manipular um canal do Teams sendo criado. Para saber mais, veja [canal criado](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| channelDeleted | `on_teams_channel_deleted` | Esse método pode ser substituído para manipular um canal do Teams sendo excluído. Para saber mais, veja [canal excluído](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| channelRenamed | `on_teams_channel_renamed` | Esse método pode ser substituído para manipular um canal do Teams sendo renomeado. Para saber mais, veja [canal renomeado](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| teamRenamed | `on_teams_team_renamed` | `return Task.CompletedTask;` Esse método pode ser substituído para manipular uma equipe do Teams sendo renomeada. Para saber mais, veja [equipe renomeada](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| MembersAdded | `on_teams_members_added` | Esse método chama o método `OnMembersAddedAsync` no `ActivityHandler`. O método pode ser substituído para manipular membros que ingressam em uma equipe. Para saber mais, veja [membros da equipe adicionados](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-added) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| MembersRemoved | `on_teams_members_removed` | Esse método chama o método `OnMembersRemovedAsync` no `ActivityHandler`. O método pode ser substituído para manipular membros que saem de uma equipe. Para saber mais, veja [membros da equipe removidos](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-removed) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|

#### <a name="teams-invoke-activities"></a>Atividades de invocação do Teams

A lista de Teams manipuladores de atividade chamados do manipulador `on_invoke_activity` de Teams de atividade inclui o seguinte:

| Invocar tipos                    | Manipulador                              | Descrição                                                  |
| :-----------------------------  | :----------------------------------- | :----------------------------------------------------------- |
| CardAction.Invoke               | `on_teams_card_action_invoke`       | Esse método é invocado quando uma atividade de invocação de ação de cartão é recebida do conector. |
| fileConsent/invoke              | `on_teams_file_consent_accept`      | Esse método é invocado quando um cartão de consentimento de arquivo é aceito pelo usuário. |
| fileConsent/invoke              | `on_teams_file_consent`            | Esse método é invocado quando uma atividade de cartão de consentimento de arquivo é recebida do conector. |
| fileConsent/invoke              | `on_teams_file_consent_decline`     | Esse método é invocado quando um cartão de consentimento de arquivo é recusado pelo usuário. |
| actionableMessage/executeAction | `on_teams_o365_connector_card_action` | Esse método é invocado quando uma Office 365 de ação do cartão do conector é recebida do conector. |
| signin/verifyState              | `on_teams_signin_verify_state`      | Esse método é invocado quando uma atividade de estado de verificação de entrada é recebida do conector. |
| task/fetch                      | `on_teams_task_module_fetch`        | Esse método pode ser substituído em uma classe derivada para fornecer lógica quando um módulo de tarefa é buscado. |
| task/submit                     | `on_teams_task_module_submit`       | Esse método pode ser substituído em uma classe derivada para fornecer lógica quando um módulo de tarefa é enviado. |

As atividades de invocação listadas nesta seção são para bots de conversação no Teams. O Bot Framework SDK também é compatível com atividades de invocação específicas para extensões de mensagem. Para saber mais, confira [o que são extensões de mensagem](https://aka.ms/azure-bot-what-are-messaging-extensions).

---

---

Agora que você se familiarizou com os manipuladores de atividade do bot, vamos ver como os bots se comportam de forma diferente, dependendo da conversa e das mensagens que ele recebe ou envia.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Noções básicas sobre conversas](~/bots/how-to/conversations/conversation-basics.md)
