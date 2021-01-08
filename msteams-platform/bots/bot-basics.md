---
title: Noções básicas de bot
author: clearab
description: Entenda as noções básicas dos bots no Teams.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 43dd351b30fdba3435d39aca43aae0f2de00ed24
ms.sourcegitcommit: d0e71ea63af2f67eba75ba283ec46cc7cdf87d75
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/24/2020
ms.locfileid: "49731955"
---
# <a name="bot-basics"></a>Noções básicas de bot

Esta é uma introdução que se baseia no artigo [como os bots funcionam](https://aka.ms/how-bots-work) na documentação principal da [estrutura do bot](https://aka.ms/azure-bot-service-docs). Você pode encontrar esse artigo e os outros artigos na seção *conceitos* , útil.

A principal diferença no bots desenvolvido para o Microsoft Teams é a forma como as atividades são tratadas. O manipulador de atividades do Microsoft Teams é derivado do manipulador de atividades da estrutura de bot para encaminhar todas as atividades do teams antes de permitir que qualquer atividade específica de terceiros não possa ser manipulada.

## <a name="teams-activity-handlers"></a>Manipuladores de atividade do teams

Quando um bot para o Microsoft Teams recebe uma atividade, ele a passa para seus *manipuladores de atividade*. Nos bastidores, há um manipulador de base chamado de *manipulador de ativação*, que todas as atividades são roteadas. O *manipulador de Turn* chama o manipulador de atividade necessário para lidar com qualquer tipo de atividade recebido. Onde um bot projetado para o Microsoft Teams difere é que ele é derivado de `TeamsActivityHandler` uma classe derivada da classe da estrutura de bot `ActivityHandler` .

# <a name="c"></a>[C#](#tab/csharp)

Como com qualquer bot criado usando o Microsoft bot Framework, se o bot receber uma atividade de mensagem, o manipulador de ativação vê essa atividade de entrada e a envia para o `OnMessageActivityAsync` manipulador de atividade. No Teams, essa funcionalidade permanece a mesma. Se o bot receber uma atividade de atualização de conversa, o manipulador de ativação enxergará a atividade de entrada e a enviará para o `OnConversationUpdateActivityAsync` . O manipulador de atividades do Microsoft *Teams* que irá primeiro procurar qualquer evento específico do Teams e passá-lo ao manipulador de atividade da estrutura de bot, se nenhum for encontrado.

Na classe do manipulador de atividades do Microsoft Teams, há dois manipuladores de atividade de equipes principais, `OnConversationUpdateActivityAsync` que roteiam todas as atividades de atualização de conversa e `OnInvokeActivityAsync` que roteiam as atividades de chamadas de todas as equipes.

Para implementar sua lógica para manipuladores de atividade específicos do Teams, você substituirá esses métodos no bot, conforme mostrado na seção de [lógica de bot](#bot-logic) abaixo. Para cada um desses manipuladores, não há nenhuma implementação de base, portanto, basta adicionar a lógica que você deseja na substituição.

# <a name="javascript"></a>[JavaScript](#tab/javascript)

Como com qualquer bot criado usando o Microsoft bot Framework, se o bot receber uma atividade de mensagem, o manipulador de ativação vê essa atividade de entrada e a envia para o `onMessage` manipulador de atividade. No Teams, essa funcionalidade permanece a mesma. Se o bot receber uma atividade de atualização de conversa, o manipulador de ativação enxergará a atividade de entrada e a enviará para o `dispatchConversationUpdateActivity` . O manipulador de atividades do Microsoft *Teams* que irá primeiro procurar qualquer evento específico do Teams e passá-lo ao manipulador de atividade de estruturas de bot, se nenhum for encontrado.

Na classe do manipulador de atividades do Microsoft Teams, há dois manipuladores de atividade de equipes principais, `dispatchConversationUpdateActivity` que roteiam todas as atividades de atualização de conversa e `onInvokeActivity` que roteiam as atividades de chamadas de todas as equipes.

Para implementar sua lógica para manipuladores de atividade específicos do Teams, você substituirá esses métodos no bot conforme visto na seção [lógica de bot](#bot-logic) . Para cada um desses manipuladores, defina sua lógica de bot e, em seguida, **não se esqueça de ligar para `next()` o fim**. Chamando `next()` você garante que o próximo manipulador será executado.

# <a name="python"></a>[Python](#tab/python)

Os bots são criados usando a estrutura do Microsoft bot, se esse bot receber uma atividade de mensagem, então o manipulador de ativação recebe uma notificação da atividade de entrada. O manipulador Turn, em seguida, envia a atividade de entrada para o `on_message_activity` manipulador de atividade. No Teams, essa funcionalidade permanece a mesma. Se o bot receber uma atividade de atualização de conversa, o manipulador de ativação receberá uma notificação da atividade de entrada e enviará a atividade de entrada para `on_conversation_update_activity` . O manipulador de atividades do Microsoft Teams primeiro verificará eventos específicos do teams. Se nenhum evento for encontrado, ele passará para o manipulador de atividade da estrutura de bot.

Na classe do manipulador de atividades do Teams, há dois manipuladores de atividade principais do teams `on_conversation_update_activity` e `on_invoke_activity` . `on_conversation_update_activity` roteia todas as atividades de atualização de conversa e `on_invoke_activity` roteia todas as atividades de chamada de equipe.

Para implementar sua lógica para manipuladores de atividade específicos do Teams, você precisa substituir esses métodos no bot conforme mostrado na seção de [lógica de bot](#bot-logic) . Não há nenhuma implementação de base para esses manipuladores, portanto, você precisa adicionar a lógica que você deseja na substituição.

---

## <a name="bot-logic"></a>Lógica de bot

A lógica de bot processa as atividades de entrada de um ou mais dos seus canais de bot e gera atividades de saída em resposta.  Isso ainda se aplica aos bots provenientes da classe manipulador de atividades do Microsoft Teams, que primeiro verifica as atividades de equipes e, em seguida, passa todas as outras atividades para o manipulador de atividade de estruturas de bot.

# <a name="c"></a>[C#](#tab/csharp)

#### <a name="core-bot-framework-handlers"></a>Manipuladores da estrutura principal do bot

Todos os manipuladores de atividade descritos abaixo continuarão a funcionar como fazem com um bot que não é um Teams, com exceção das atividades de tratamento de membros *adicionados* e membros *removidos* , eles serão diferentes no contexto de uma equipe, onde o novo membro é adicionado à equipe, em vez de um thread de mensagem.

Os manipuladores definidos no `ActivityHandler` são descritos abaixo:

| Evento | Indicador | Descrição |
| :-- | :-- | :-- |
| Qualquer tipo de atividade recebido | `OnTurnAsync` | Chama um dos outros manipuladores, com base no tipo de atividade recebida. |
| Atividade de mensagem recebida | `OnMessageActivityAsync` | Substitua isso para lidar com uma `Message` atividade. |
| Atividade de atualização de conversa recebida | `OnConversationUpdateActivityAsync` | Em uma `ConversationUpdate` atividade, chama um manipulador se outros membros que não o bot ingressaram ou saíram da conversa. |
| Membros não-bot ingressaram na conversa | `OnMembersAddedAsync` | Substitua isso para lidar com membros que participam de uma conversa. |
| Membros que não são bot saíram da conversa | `OnMembersRemovedAsync` | Substitua isso para lidar com membros que saem de uma conversa. |
| Atividade de evento recebida | `OnEventActivityAsync` | Em uma `Event` atividade, chama um manipulador específico para o tipo de evento. |
| Atividade de evento de resposta de token recebida | `OnTokenResponseEventAsync` | Substitua isso para manipular eventos de resposta de token. |
| Atividade de evento de resposta não token recebida | `OnEventAsync` | Substitua isso para manipular outros tipos de eventos. |
| Outro tipo de atividade recebido | `OnUnrecognizedActivityTypeAsync` | Substitua isso para lidar com qualquer tipo de atividade, caso contrário, não manipulado. |

#### <a name="teams-specific-handlers"></a>Manipuladores específicos de equipes

O `TeamsActivityHandler` estende a lista de manipuladores acima para incluir o seguinte:

| Evento | Indicador | Descrição |
| :-- | :-- | :-- |
| channelCreated | `OnTeamsChannelCreatedAsync` | Substitua isso para manipular um canal do teams que está sendo criado. Para obter mais informações, consulte [canal criado](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| channelDeleted | `OnTeamsChannelDeletedAsync` | Substitua isso para manipular um canal do teams que está sendo excluído. Para obter mais informações, consulte [canal excluído](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| channelRenamed | `OnTeamsChannelRenamedAsync` | Substitua isso para manipular um canal do teams que está sendo renomeado. Para obter mais informações, consulte [canal renomeado](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| teamRenamed | `OnTeamsTeamRenamedAsync` | `return Task.CompletedTask;` Substitua isso para lidar com a equipe de equipes que está sendo renomeada. Para obter mais informações, confira [Team renomeado](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| MembersAdded | `OnTeamsMembersAddedAsync` | Chama o `OnMembersAddedAsync` método no `ActivityHandler` . Substitua isso para lidar com membros que participam de uma equipe. Para obter mais informações, consulte [membros da equipe adicionados](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-added) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| MembersRemoved | `OnTeamsMembersRemovedAsync` | Chama o `OnMembersRemovedAsync` método no `ActivityHandler` . Substitua isso para lidar com os membros que saem de uma equipe. Para obter mais informações, consulte [membros da equipe removidos](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-removed) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|

#### <a name="teams-invoke-activities"></a>Atividades de invocação do teams

Veja a seguir uma lista de todos os manipuladores de atividade do teams chamados do manipulador de atividade do `OnInvokeActivityAsync` _Teams_ :

| Tipos de invocação                    | Indicador                              | Descrição                                                  |
| :-----------------------------  | :----------------------------------- | :----------------------------------------------------------- |
| Cardaction. Invoke               | `OnTeamsCardActionInvokeAsync`       | Invocação de ação de cartão de equipe. |
| fileconsentimento/invocação              | `OnTeamsFileConsentAcceptAsync`      | Aceitação de consentimento de arquivo do teams. |
| fileconsentimento/invocação              | `OnTeamsFileConsentAsync`            | Consentimento de arquivo do teams. |
| fileconsentimento/invocação              | `OnTeamsFileConsentDeclineAsync`     | Consentimento de arquivo do teams. |
| actionableMessage/ExecuteAction | `OnTeamsO365ConnectorCardActionAsync` | Ação do cartão de conector do O365 da equipe. |
| entrada/verificação              | `OnTeamsSigninVerifyStateAsync`      | O estado de verificação do teams. |
| tarefa/busca                      | `OnTeamsTaskModuleFetchAsync`        | Busca do módulo de tarefa do teams. |
| tarefa/envio                     | `OnTeamsTaskModuleSubmitAsync`       | Envio do módulo de tarefas do teams. |

As atividades de invocação listadas acima são para bots de conversas no Microsoft Teams. O SDK da estrutura de bot também oferece suporte a chamadas específicas para extensões de mensagens. Para obter mais informações, consulte [o que são extensões de mensagens](https://aka.ms/azure-bot-what-are-messaging-extensions)

# <a name="javascript"></a>[JavaScript](#tab/javascript)

Todos os manipuladores de atividade descritos abaixo continuarão a funcionar como fazem com um bot que não é um Teams, com a exceção de lidar com as atividades dos membros *adicionados* e *removidas* , eles serão diferentes no contexto de uma equipe, onde o novo membro é adicionado à equipe, em vez de um thread de mensagem.

#### <a name="core-bot-framework-handlers"></a>Manipuladores da estrutura principal do bot

Os manipuladores definidos no `ActivityHandler` são descritos abaixo.

| Evento | Indicador | Descrição |
| :-- | :-- | :-- |
| Qualquer tipo de atividade recebido | `onTurn` | Chama um dos outros manipuladores, com base no tipo de atividade recebida. |
| Atividade de mensagem recebida | `onMessage` | Forneça uma função para que isso trate de uma `Message` atividade. |
| Atividade de atualização de conversa recebida | `onConversationUpdate` | Em uma `ConversationUpdate` atividade, chama um manipulador se outros membros que não o bot ingressaram ou saíram da conversa. |
| Membros não-bot ingressaram na conversa | `onMembersAdded` | Forneça uma função para isso para lidar com membros que participam de uma conversa. |
| Membros que não são bot saíram da conversa | `onMembersRemoved` | Forneça uma função para isso para lidar com os membros que saem de uma conversa. |
| Atividade de evento recebida | `onEvent` | Em uma `Event` atividade, chama um manipulador específico para o tipo de evento. |
| Atividade de evento de resposta de token recebida | `onTokenResponseEvent` | Forneça uma função para tratar de eventos de resposta de token. |
| Outro tipo de atividade recebido | `onUnrecognizedActivityType` | Forneça uma função para que isso trate de qualquer tipo de atividade, caso contrário, não manipulado. |
| Manipuladores de atividade concluídos | `onDialog` | Forneça uma função para que isso trate de qualquer processamento que deve ser feito no final de uma vez depois que o restante de seus manipuladors de atividade tiver concluído. |

#### <a name="teams-specific-handlers"></a>Manipuladores específicos de equipes

O `TeamsActivityHandler` estende a lista de manipuladores na seção principais manipuladores da estrutura do bot para incluir o seguinte:

| Evento | Indicador | Descrição |
| :-- | :-- | :-- |
| channelCreated | `OnTeamsChannelCreatedAsync` | Substitua isso para manipular um canal do teams que está sendo criado. Para obter mais informações, consulte [canal criado](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| channelDeleted | `OnTeamsChannelDeletedAsync` | Substitua isso para manipular um canal do teams que está sendo excluído. Para obter mais informações, consulte [canal excluído](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| channelRenamed | `OnTeamsChannelRenamedAsync` | Substitua isso para manipular um canal do teams que está sendo renomeado. Para obter mais informações, consulte [canal renomeado](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| teamRenamed | `OnTeamsTeamRenamedAsync` | `return Task.CompletedTask;` Substitua isso para lidar com a equipe de equipes que está sendo renomeada. Para obter mais informações, confira [Team renomeado](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| MembersAdded | `OnTeamsMembersAddedAsync` | Chama o `OnMembersAddedAsync` método no `ActivityHandler` . Substitua isso para lidar com membros que participam de uma equipe. Para obter mais informações, consulte [membros da equipe adicionados](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-added) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| MembersRemoved | `OnTeamsMembersRemovedAsync` | Chama o `OnMembersRemovedAsync` método no `ActivityHandler` . Substitua isso para lidar com os membros que saem de uma equipe. Para obter mais informações, consulte [membros da equipe removidos](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-removed) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events). |

#### <a name="teams-invoke-activities"></a>Atividades de invocação do teams

Veja a seguir uma lista de todos os manipuladores de atividade do teams chamados do `onInvokeActivity` manipulador de atividade do teams:

| Tipos de invocação                    | Indicador                              | Descrição                                                  |
| :-----------------------------  | :----------------------------------- | :----------------------------------------------------------- |
| Cardaction. Invoke               | `handleTeamsCardActionInvoke`       | Invocação de ação de cartão de equipe. |
| fileconsentimento/invocação              | `handleTeamsFileConsentAccept`      | Aceitação de consentimento de arquivo do teams. |
| fileconsentimento/invocação              | `handleTeamsFileConsent`            | Consentimento de arquivo do teams. |
| fileconsentimento/invocação              | `handleTeamsFileConsentDecline`     | Consentimento de arquivo do teams. |
| actionableMessage/ExecuteAction | `handleTeamsO365ConnectorCardAction` | Ação do cartão de conector do O365 da equipe. |
| entrada/verificação              | `handleTeamsSigninVerifyState`      | O estado de verificação do teams. |
| tarefa/busca                      | `handleTeamsTaskModuleFetch`        | Busca do módulo de tarefa do teams. |
| tarefa/envio                     | `handleTeamsTaskModuleSubmit`       | Envio do módulo de tarefas do teams. |

As atividades de invocação listadas na seção atividades de invocação do teams são para bots de conversa no Teams. O SDK da estrutura de bot também oferece suporte a atividades específicas para extensões de mensagens. Para obter mais informações, consulte [o que são extensões de mensagens](https://aka.ms/azure-bot-what-are-messaging-extensions).

# <a name="python"></a>[Python](#tab/python)

#### <a name="core-bot-framework-handlers"></a>Manipuladores da estrutura principal do bot

>[!NOTE]
> Exceto para as atividades dos membros adicionados e removidos, todos os manipuladores de atividade descritos nesta seção continuam a funcionar como em um bot não Teams.

Manipuladores de atividade são diferentes no contexto de uma equipe, onde o novo membro é adicionado à equipe em vez de um thread de mensagem.

A lista de manipuladores definida em `ActivityHandler` inclui o seguinte:

| Evento | Indicador | Descrição |
| :-- | :-- | :-- |
| Qualquer tipo de atividade recebido | `on_turn` | Chama um dos outros manipuladores, com base no tipo de atividade recebida. |
| Atividade de mensagem recebida | `on_message_activity` | Substitui isso para lidar com uma `Message` atividade. |
| Atividade de atualização de conversa recebida | `on_conversation_update_activity` | Chama um manipulador se outros membros que não o bot ingressam ou saem da conversa. |
| Membros não-bot ingressaram na conversa | `on_members_added_activity` | Substitui isso para lidar com membros que participam de uma conversa. |
| Membros que não são bot saíram da conversa | `on_members_removed_activity` | Substitui isso para lidar com membros que saem de uma conversa. |
| Atividade de evento recebida | `on_event_activity` | Chama um manipulador específico para o tipo de evento. |
| Atividade de evento de resposta de token recebida | `on_token_response_event` | Substitui isso para lidar com eventos de resposta de token. |
| Atividade de evento de resposta não token recebida | `on_event` | Substitui isso para manipular outros tipos de eventos. |
| Outros tipos de atividade recebidos | `on_unrecognized_activity_type` | Substitui isso para lidar com qualquer tipo de atividade que não é manipulado. |

#### <a name="teams-specific-handlers"></a>Manipuladores específicos de equipes

O `TeamsActivityHandler` estende a lista de manipuladores da seção manipuladores da estrutura principal do bot para incluir o seguinte:

| Evento | Indicador | Descrição |
| :-- | :-- | :-- |
| channelCreated | `on_teams_channel_created` | Substitui isso para lidar com um canal de equipe que está sendo criado. Para obter mais informações, consulte [canal criado](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| channelDeleted | `on_teams_channel_deleted` | Substitui isso para lidar com um canal do teams sendo excluído. Para obter mais informações, consulte [canal excluído](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| channelRenamed | `on_teams_channel_renamed` | Substitui isso para lidar com um canal do teams sendo renomeado. Para obter mais informações, consulte [canal renomeado](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| teamRenamed | `on_teams_team_renamed` | `return Task.CompletedTask;` Substitui isso para lidar com a equipe de equipes que está sendo renomeada. Para obter mais informações, consulte [Team renomeed](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) in [Conversation Update Events](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| MembersAdded | `on_teams_members_added` | Chama o `OnMembersAddedAsync` método no `ActivityHandler` . Substitui isso para lidar com membros que participam de uma equipe. Para obter mais informações, consulte [membros da equipe adicionados](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-added) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| MembersRemoved | `on_teams_members_removed` | Chama o `OnMembersRemovedAsync` método no `ActivityHandler` . Substitui isso para lidar com os membros que saem de uma equipe. Para obter mais informações, consulte [membros da equipe removidos](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-removed) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|

#### <a name="teams-invoke-activities"></a>Atividades de invocação do teams

A lista de manipuladores de atividade do teams chamados do `on_invoke_activity` manipulador de atividades do teams inclui o seguinte:

| Tipos de invocação                    | Indicador                              | Descrição                                                  |
| :-----------------------------  | :----------------------------------- | :----------------------------------------------------------- |
| Cardaction. Invoke               | `on_teams_card_action_invoke`       | Invocação de ação de cartão de equipe. |
| fileconsentimento/invocação              | `on_teams_file_consent_accept`      | Aceitação de consentimento de arquivo do teams. |
| fileconsentimento/invocação              | `on_teams_file_consent`            | Consentimento de arquivo do teams. |
| fileconsentimento/invocação              | `on_teams_file_consent_decline`     | Recusa de consentimento de arquivo do teams. |
| actionableMessage/ExecuteAction | `on_teams_o365_connector_card_action` | Ação do cartão de conector do O365 da equipe. |
| entrada/verificação              | `on_teams_signin_verify_state`      | O estado de verificação do teams. |
| tarefa/busca                      | `on_teams_task_module_fetch`        | Busca do módulo de tarefa do teams. |
| tarefa/envio                     | `on_teams_task_module_submit`       | Envio do módulo de tarefas do teams. |

As atividades de invocação listadas na seção atividades de invocação do teams são para bots de conversa no Teams. O SDK da estrutura de bot também oferece suporte a atividades específicas para extensões de mensagens. Para obter mais informações, consulte [o que são extensões de mensagens](https://aka.ms/azure-bot-what-are-messaging-extensions).

---
