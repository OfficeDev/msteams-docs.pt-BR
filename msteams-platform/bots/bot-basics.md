---
title: Noções básicas sobre bot
author: clearab
description: Entenda as noções básicas de bots no Teams.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 3c4e707fa4677c2441f348e8d09ecf4428ef1296
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014499"
---
# <a name="bot-basics"></a>Noções básicas sobre bot

Este documento fornece uma introdução aos bots no Microsoft Teams que se baseia no artigo Como os [bots](https://aka.ms/how-bots-work) funcionam na documentação principal [do Bot Framework.](https://aka.ms/azure-bot-service-docs) A principal diferença entre os bots desenvolvidos para o Microsoft Teams e a Estrutura de Bot principal está nos recursos fornecidos no Teams.

## <a name="teams-activity-handlers"></a>Manipuladores de atividades do Teams

O manipulador de atividades do Teams é derivado do manipulador de atividades do Microsoft Bot Framework. Ele encaminha todas as atividades do Teams antes de permitir que qualquer atividade específica que não seja do Teams seja manipulada.

Quando um bot para o Teams recebe uma atividade, ele é direcionado para os *manipuladores de atividades.* Todas as atividades são roteados por um manipulador de base chamado manipulador *de rotação.* O *manipulador de turno* chama o manipulador de atividades necessário para gerenciar qualquer atividade recebida. O bot do Teams é derivado da `TeamsActivityHandler` classe, que é derivada da classe do Bot `ActivityHandler` Framework.

# <a name="c"></a>[C#](#tab/csharp)

Os bots são criados usando a Estrutura de Bot. Se os bots receberem uma atividade de mensagem, o manipulador de turno receberá uma notificação dessa atividade de entrada. Em seguida, o manipulador de turno envia a atividade de entrada para o `OnMessageActivityAsync` manipulador de atividades. No Teams, essa funcionalidade permanece a mesma. Se o bot receber uma atividade de atualização de conversa, o manipulador de turno receberá uma notificação dessa atividade de entrada e enviará a atividade de entrada para `OnConversationUpdateActivityAsync` . O manipulador de atividades do Teams primeiro verifica se há eventos específicos do Teams. Se nenhum evento for encontrado, ele os passará para o manipulador de atividades do Bot Framework.

Na classe do manipulador de atividades do Teams, há dois manipuladores de atividades principais do Teams `OnConversationUpdateActivityAsync` `OnInvokeActivityAsync` e. `OnConversationUpdateActivityAsync` encaminha todas as atividades de atualização de conversa e `OnInvokeActivityAsync` encaminha todas as atividades de invocação do Teams.

Para implementar sua lógica para manipuladores de atividades específicos do Teams, você deve substituir os métodos em seu bot, conforme mostrado na seção [de lógica de bot.](#bot-logic) Não há nenhuma implementação base para esses manipuladores, portanto, você deve adicionar a lógica que deseja em sua substituição.

# <a name="javascript"></a>[JavaScript](#tab/javascript)

Os bots são criados usando a Estrutura de Bot. Se os bots receberem uma atividade de mensagem, o manipulador de turno receberá uma notificação dessa atividade de entrada. Em seguida, o manipulador de turno envia a atividade de entrada para o `onMessage` manipulador de atividades. No Teams, essa funcionalidade permanece a mesma. Se o bot receber uma atividade de atualização de conversa, o manipulador de turno receberá uma notificação dessa atividade de entrada e enviará a atividade de entrada para `dispatchConversationUpdateActivity` . O manipulador de atividades do Teams primeiro verifica se há eventos específicos do Teams. Se nenhum evento for encontrado, ele os passará para o manipulador de atividades do Bot Framework.

Na classe do manipulador de atividades do Teams, há dois manipuladores de atividades principais do Teams `dispatchConversationUpdateActivity` `onInvokeActivity` e. `dispatchConversationUpdateActivity` encaminha todas as atividades de atualização de conversa e `onInvokeActivity` encaminha todas as atividades de invocação do Teams.

Para implementar sua lógica para manipuladores de atividades específicos do Teams, você deve substituir os métodos em seu bot, conforme mostrado na seção [de lógica de bot.](#bot-logic) Defina sua lógica de bot para esses manipuladores e, em seguida, **certifique-se de chamar no `next()` final.** Chamando `next()` você, verifique se o próximo manipulador é executado.

# <a name="python"></a>[Python](#tab/python)

Os bots são criados usando a Estrutura de Bot. Se os bots receberem uma atividade de mensagem, o manipulador de turno receberá uma notificação dessa atividade de entrada. Em seguida, o manipulador de turno envia a atividade de entrada para o `on_message_activity` manipulador de atividades. No Teams, essa funcionalidade permanece a mesma. Se o bot receber uma atividade de atualização de conversa, o manipulador de turno receberá uma notificação dessa atividade de entrada e enviará a atividade de entrada para `on_conversation_update_activity` . O manipulador de atividades do Teams primeiro verifica se há eventos específicos do Teams. Se nenhum evento for encontrado, ele os passará para o manipulador de atividades do Bot Framework.

Na classe do manipulador de atividades do Teams, há dois manipuladores de atividades principais do Teams `on_conversation_update_activity` `on_invoke_activity` e. `on_conversation_update_activity` encaminha todas as atividades de atualização de conversa e `on_invoke_activity` encaminha todas as atividades de invocação do Teams.

Para implementar sua lógica para manipuladores de atividades específicos do Teams, você deve substituir os métodos em seu bot, conforme mostrado na seção [de lógica de bot.](#bot-logic) Não há nenhuma implementação base para esses manipuladores, portanto, você deve adicionar a lógica que deseja em sua substituição.

---

## <a name="bot-logic"></a>Lógica de bot

A lógica de bot processa as atividades de entrada de um ou mais de seus canais de bot e, em resposta, gera atividades de saída. Isso ainda vale para bots derivados da classe do manipulador de atividades do Teams, que primeiro verifica as atividades do Teams. Depois de verificar as atividades do Teams, ele passa todas as outras atividades para o manipulador de atividades do Bot Framework.

# <a name="c"></a>[C#](#tab/csharp)

#### <a name="core-bot-framework-handlers"></a>Manipuladores do Core Bot Framework

>[!NOTE]
> Exceto pelas atividades  *dos* membros adicionados e removidos, todos os manipuladores de atividades descritos nesta seção continuam a funcionar da mesma forma que com um bot que não seja do Teams.

Manipuladores de atividades são diferentes no contexto de uma equipe, onde um novo membro é adicionado à equipe em vez de um thread de mensagem.

A lista de manipuladores definidos `ActivityHandler` inclui o seguinte:

| Event | Manipulador | Descrição |
| :-- | :-- | :-- |
| Qualquer tipo de atividade recebido | `OnTurnAsync` | Esse método chama um dos outros manipuladores, com base no tipo de atividade recebida. |
| Atividade de mensagem recebida | `OnMessageActivityAsync` | Esse método pode ser substituído para manipular uma `Message` atividade. |
| Atividade de atualização de conversa recebida | `OnConversationUpdateActivityAsync` | Esse método chama um manipulador se membros diferentes do bot ingressaram ou deixaram a conversa em uma `ConversationUpdate` atividade. |
| Membros não bot ingressam na conversa | `OnMembersAddedAsync` | Esse método pode ser substituído para manipular membros in joining a uma conversa. |
| Membros não bot deixaram a conversa | `OnMembersRemovedAsync` | Esse método pode ser substituído para manipular membros que deixam uma conversa. |
| Atividade de evento recebida | `OnEventActivityAsync` | Esse método chama um manipulador específico para o tipo de evento, em uma `Event` atividade. |
| Atividade de evento de resposta de token recebida | `OnTokenResponseEventAsync` | Esse método pode ser substituído para manipular eventos de resposta de token. |
| Atividade de evento de não-resposta de token recebida | `OnEventAsync` | Esse método pode ser substituído para lidar com outros tipos de eventos. |
| Outro tipo de atividade recebido | `OnUnrecognizedActivityTypeAsync` | Esse método pode ser substituído para manipular qualquer tipo de atividade sem tratar. |

#### <a name="teams-specific-activity-handlers"></a>Manipuladores de atividades específicos do Teams

Estende `TeamsActivityHandler` a lista de manipuladores na seção manipuladores do Core Bot Framework para incluir o seguinte:

| Event | Manipulador | Descrição |
| :-- | :-- | :-- |
| channelCreated | `OnTeamsChannelCreatedAsync` | Esse método pode ser substituído para manipular um canal do Teams que está sendo criado. Para obter mais informações, consulte [Canal criado em](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created) eventos de atualização de [conversa.](https://aka.ms/azure-bot-subscribe-to-conversation-events) |
| channelDeleted | `OnTeamsChannelDeletedAsync` | Esse método pode ser substituído para manipular um canal do Teams que está sendo excluído. Para obter mais informações, consulte [Canal excluído em](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted) eventos de atualização de [conversa.](https://aka.ms/azure-bot-subscribe-to-conversation-events)|
| channelRenamed | `OnTeamsChannelRenamedAsync` | Esse método pode ser substituído para manipular um canal do Teams que está sendo renomeado. Para obter mais informações, consulte [Canal renomeado em](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) [eventos de atualização de conversa.](https://aka.ms/azure-bot-subscribe-to-conversation-events)|
| teamRenamed | `OnTeamsTeamRenamedAsync` | `return Task.CompletedTask;` Esse método pode ser substituído para manipular uma equipe do Teams que está sendo renomeada. Para obter mais informações, consulte [Equipe renomeada em](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) [eventos de atualização de conversa.](https://aka.ms/azure-bot-subscribe-to-conversation-events)|
| MembersAdded | `OnTeamsMembersAddedAsync` | Este método chama o `OnMembersAddedAsync` método em `ActivityHandler` . O método pode ser substituído para lidar com membros in joining a uma equipe. Para obter mais informações, consulte [Membros da equipe adicionados](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-added) em [eventos de atualização de conversa.](https://aka.ms/azure-bot-subscribe-to-conversation-events)|
| MembersRemoved | `OnTeamsMembersRemovedAsync` | Este método chama o `OnMembersRemovedAsync` método em `ActivityHandler` . O método pode ser substituído para manipular membros que deixam uma equipe. Para obter mais informações, consulte [Membros da equipe removidos](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-removed) em [eventos de atualização de conversa.](https://aka.ms/azure-bot-subscribe-to-conversation-events)|

#### <a name="teams-invoke-activities"></a>Atividades de invocação do Teams

A lista de manipuladores de atividades do Teams chamado do manipulador `OnInvokeActivityAsync` de atividades do Teams inclui o seguinte:

| Invocar tipos                    | Manipulador                              | Descrição                                                  |
| :-----------------------------  | :----------------------------------- | :----------------------------------------------------------- |
| CardAction.Invoke               | `OnTeamsCardActionInvokeAsync`       | Esse método é invocado quando uma atividade de invocação de ação de cartão é recebida do conector. |
| fileConsent/invoke              | `OnTeamsFileConsentAcceptAsync`      | Esse método é invocado quando um cartão de consentimento de arquivo é aceito pelo usuário. |
| fileConsent/invoke              | `OnTeamsFileConsentAsync`            | Esse método é invocado quando uma atividade de cartão de consentimento de arquivo é recebida do conector. |
| fileConsent/invoke              | `OnTeamsFileConsentDeclineAsync`     | Esse método é invocado quando um cartão de consentimento de arquivo é recusado pelo usuário. |
| actionableMessage/executeAction | `OnTeamsO365ConnectorCardActionAsync` | Esse método é invocado quando uma atividade de ação do cartão do conector do O365 é recebida do conector. |
| signin/verifyState              | `OnTeamsSigninVerifyStateAsync`      | Esse método é invocado quando uma atividade de estado de entrada é recebida do conector. |
| task/fetch                      | `OnTeamsTaskModuleFetchAsync`        | Esse método pode ser substituído em uma classe derivada para fornecer lógica quando um módulo de tarefa é buscado. |
| tarefa/envio                     | `OnTeamsTaskModuleSubmitAsync`       | Esse método pode ser substituído em uma classe derivada para fornecer lógica quando um módulo de tarefa é enviado. |

As atividades de invocação listadas nesta seção são para bots de conversa no Teams. O SDK da Estrutura de Bot também dá suporte a atividades de invocação específicas para extensões de mensagens. Para obter mais informações, consulte [O que são extensões de mensagens.](https://aka.ms/azure-bot-what-are-messaging-extensions)

# <a name="javascript"></a>[JavaScript](#tab/javascript)

#### <a name="core-bot-framework-handlers"></a>Manipuladores do Core Bot Framework

>[!NOTE]
> Exceto pelas atividades  *dos* membros adicionados e removidos, todos os manipuladores de atividades descritos nesta seção continuam a funcionar da mesma forma que com um bot que não seja do Teams.

Manipuladores de atividades são diferentes no contexto de uma equipe, onde o novo membro é adicionado à equipe em vez de um thread de mensagem.

A lista de manipuladores definidos `ActivityHandler` inclui o seguinte:

| Event | Manipulador | Descrição |
| :-- | :-- | :-- |
| Qualquer tipo de atividade recebido | `onTurn` | Esse método chama um dos outros manipuladores, com base no tipo de atividade recebida. |
| Atividade de mensagem recebida | `onMessage` | Esse método ajuda a manipular uma `Message` atividade. |
| Atividade de atualização de conversa recebida | `onConversationUpdate` | Esse método chama um manipulador se membros diferentes do bot ingressaram ou deixaram a conversa em uma `ConversationUpdate` atividade. |
| Membros não bot ingressam na conversa | `onMembersAdded` | Esse método ajuda a manipular membros que estão inando em uma conversa. |
| Membros não bot deixaram a conversa | `onMembersRemoved` | Esse método ajuda a manipular membros que deixam uma conversa. |
| Atividade de evento recebida | `onEvent` | Esse método chama um manipulador específico para o tipo de evento, em uma `Event` atividade. |
| Atividade de evento de resposta de token recebida | `onTokenResponseEvent` | Esse método ajuda a manipular eventos de resposta de token. |
| Outro tipo de atividade recebido | `onUnrecognizedActivityType` | Esse método ajuda a manipular qualquer tipo de atividade sem ser utilizado. |

#### <a name="teams-specific-activity-handlers"></a>Manipuladores de atividades específicos do Teams

Estende `TeamsActivityHandler` a lista de manipuladores na seção manipuladores do Core Bot Framework para incluir o seguinte:

| Event | Manipulador | Descrição |
| :-- | :-- | :-- |
| channelCreated | `OnTeamsChannelCreatedAsync` | Esse método pode ser substituído para manipular um canal do Teams que está sendo criado. Para obter mais informações, consulte [Canal criado em](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created) eventos de atualização de [conversa.](https://aka.ms/azure-bot-subscribe-to-conversation-events) |
| channelDeleted | `OnTeamsChannelDeletedAsync` | Esse método pode ser substituído para manipular um canal do Teams que está sendo excluído. Para obter mais informações, consulte [Canal excluído em](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted) eventos de atualização de [conversa.](https://aka.ms/azure-bot-subscribe-to-conversation-events)|
| channelRenamed | `OnTeamsChannelRenamedAsync` | Esse método pode ser substituído para manipular um canal do Teams que está sendo renomeado. Para obter mais informações, consulte [Canal renomeado em](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) [eventos de atualização de conversa.](https://aka.ms/azure-bot-subscribe-to-conversation-events) |
| teamRenamed | `OnTeamsTeamRenamedAsync` | `return Task.CompletedTask;` Esse método pode ser substituído para manipular uma equipe do Teams que está sendo renomeada. Para obter mais informações, consulte [Equipe renomeada em](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) [eventos de atualização de conversa.](https://aka.ms/azure-bot-subscribe-to-conversation-events) |
| MembersAdded | `OnTeamsMembersAddedAsync` | Este método chama o `OnMembersAddedAsync` método em `ActivityHandler` . O método pode ser substituído para lidar com membros in joining a uma equipe. Para obter mais informações, consulte [Membros da equipe adicionados](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-added) em [eventos de atualização de conversa.](https://aka.ms/azure-bot-subscribe-to-conversation-events) |
| MembersRemoved | `OnTeamsMembersRemovedAsync` | Este método chama o `OnMembersRemovedAsync` método em `ActivityHandler` . O método pode ser substituído para manipular membros que deixam uma equipe. Para obter mais informações, consulte [Membros da equipe removidos](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-removed) em [eventos de atualização de conversa.](https://aka.ms/azure-bot-subscribe-to-conversation-events) |

#### <a name="teams-invoke-activities"></a>Atividades de invocação do Teams

A lista de manipuladores de atividades do Teams chamado do manipulador `onInvokeActivity` de atividades do Teams inclui o seguinte:

| Invocar tipos                    | Manipulador                              | Descrição                                                  |
| :-----------------------------  | :----------------------------------- | :----------------------------------------------------------- |
| CardAction.Invoke               | `handleTeamsCardActionInvoke`       | Esse método é invocado quando uma atividade de invocação de ação de cartão é recebida do conector. |
| fileConsent/invoke              | `handleTeamsFileConsentAccept`      | Esse método é invocado quando um cartão de consentimento de arquivo é aceito pelo usuário. |
| fileConsent/invoke              | `handleTeamsFileConsent`            | Esse método é invocado quando uma atividade de cartão de consentimento de arquivo é recebida do conector. |
| fileConsent/invoke              | `handleTeamsFileConsentDecline`     | Esse método é invocado quando um cartão de consentimento de arquivo é recusado pelo usuário. |
| actionableMessage/executeAction | `handleTeamsO365ConnectorCardAction` | Esse método é invocado quando uma atividade de ação do cartão do conector do O365 é recebida do conector. |
| signin/verifyState              | `handleTeamsSigninVerifyState`      | Esse método é invocado quando uma atividade de estado de entrada é recebida do conector. |
| task/fetch                      | `handleTeamsTaskModuleFetch`        | Esse método pode ser substituído em uma classe derivada para fornecer lógica quando um módulo de tarefa é buscado. |
| tarefa/envio                     | `handleTeamsTaskModuleSubmit`       | Esse método pode ser substituído em uma classe derivada para fornecer lógica quando um módulo de tarefa é enviado. |

As atividades de invocação listadas nesta seção são para bots de conversa no Teams. O SDK da Estrutura de Bot também dá suporte a atividades de invocação específicas para extensões de mensagens. Para obter mais informações, [consulte O que são extensões de mensagens.](https://aka.ms/azure-bot-what-are-messaging-extensions)

# <a name="python"></a>[Python](#tab/python)

#### <a name="core-bot-framework-handlers"></a>Manipuladores do Core Bot Framework

>[!NOTE]
> Exceto pelas atividades  *dos* membros adicionados e removidos, todos os manipuladores de atividades descritos nesta seção continuam a funcionar da mesma forma que com um bot que não seja do Teams.

Manipuladores de atividades são diferentes no contexto de uma equipe, onde o novo membro é adicionado à equipe em vez de um thread de mensagem.

A lista de manipuladores definidos `ActivityHandler` inclui o seguinte:

| Event | Manipulador | Descrição |
| :-- | :-- | :-- |
| Qualquer tipo de atividade recebido | `on_turn` | Esse método chama um dos outros manipuladores, com base no tipo de atividade recebida. |
| Atividade de mensagem recebida | `on_message_activity` | Esse método pode ser substituído para manipular uma `Message` atividade. |
| Atividade de atualização de conversa recebida | `on_conversation_update_activity` | Esse método chama um manipulador se membros diferentes do bot ingressarem ou saírem da conversa. |
| Membros não bot ingressam na conversa | `on_members_added_activity` | Esse método pode ser substituído para manipular membros in joining a uma conversa. |
| Membros não bot deixaram a conversa | `on_members_removed_activity` | Esse método pode ser substituído para manipular membros que deixam uma conversa. |
| Atividade de evento recebida | `on_event_activity` | Esse método chama um manipulador específico para o tipo de evento. |
| Atividade de evento de resposta de token recebida | `on_token_response_event` | Esse método pode ser substituído para manipular eventos de resposta de token. |
| Atividade de evento de não-resposta de token recebida | `on_event` | Esse método pode ser substituído para lidar com outros tipos de eventos. |
| Outros tipos de atividade recebidos | `on_unrecognized_activity_type` | Esse método pode ser substituído para manipular qualquer tipo de atividade que não seja manipulada. |

#### <a name="teams-specific-activity-handlers"></a>Manipuladores de atividades específicos do Teams

Estende `TeamsActivityHandler` a lista de manipuladores da seção manipuladores do Core Bot Framework para incluir o seguinte:

| Event | Manipulador | Descrição |
| :-- | :-- | :-- |
| channelCreated | `on_teams_channel_created` | Esse método pode ser substituído para manipular um canal do Teams que está sendo criado. Para obter mais informações, consulte [Canal criado em](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created) eventos de atualização de [conversa.](https://aka.ms/azure-bot-subscribe-to-conversation-events) |
| channelDeleted | `on_teams_channel_deleted` | Esse método pode ser substituído para manipular um canal do Teams que está sendo excluído. Para obter mais informações, consulte [Canal excluído em](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted) eventos de atualização de [conversa.](https://aka.ms/azure-bot-subscribe-to-conversation-events)|
| channelRenamed | `on_teams_channel_renamed` | Esse método pode ser substituído para manipular um canal do Teams que está sendo renomeado. Para obter mais informações, consulte [Canal renomeado em](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) [eventos de atualização de conversa.](https://aka.ms/azure-bot-subscribe-to-conversation-events)|
| teamRenamed | `on_teams_team_renamed` | `return Task.CompletedTask;` Esse método pode ser substituído para manipular uma equipe do Teams que está sendo renomeada. Para obter mais informações, consulte [Equipe renomeada em](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) [eventos de atualização de conversa.](https://aka.ms/azure-bot-subscribe-to-conversation-events)|
| MembersAdded | `on_teams_members_added` | Este método chama o `OnMembersAddedAsync` método em `ActivityHandler` . O método pode ser substituído para lidar com membros in joining a uma equipe. Para obter mais informações, consulte [Membros da equipe adicionados](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-added) em [eventos de atualização de conversa.](https://aka.ms/azure-bot-subscribe-to-conversation-events)|
| MembersRemoved | `on_teams_members_removed` | Este método chama o `OnMembersRemovedAsync` método em `ActivityHandler` . O método pode ser substituído para manipular membros que deixam uma equipe. Para obter mais informações, consulte [Membros da equipe removidos](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-removed) em [eventos de atualização de conversa.](https://aka.ms/azure-bot-subscribe-to-conversation-events)|

#### <a name="teams-invoke-activities"></a>Atividades de invocação do Teams

A lista de manipuladores de atividades do Teams chamado do manipulador `on_invoke_activity` de atividades do Teams inclui o seguinte:

| Invocar tipos                    | Manipulador                              | Descrição                                                  |
| :-----------------------------  | :----------------------------------- | :----------------------------------------------------------- |
| CardAction.Invoke               | `on_teams_card_action_invoke`       | Esse método é invocado quando uma atividade de invocação de ação de cartão é recebida do conector. |
| fileConsent/invoke              | `on_teams_file_consent_accept`      | Esse método é invocado quando um cartão de consentimento de arquivo é aceito pelo usuário. |
| fileConsent/invoke              | `on_teams_file_consent`            | Esse método é invocado quando uma atividade de cartão de consentimento de arquivo é recebida do conector. |
| fileConsent/invoke              | `on_teams_file_consent_decline`     | Esse método é invocado quando um cartão de consentimento de arquivo é recusado pelo usuário. |
| actionableMessage/executeAction | `on_teams_o365_connector_card_action` | Esse método é invocado quando uma atividade de ação do cartão do conector do O365 é recebida do conector. |
| signin/verifyState              | `on_teams_signin_verify_state`      | Esse método é invocado quando um signIn verifica se a atividade de estado é recebida do conector. |
| task/fetch                      | `on_teams_task_module_fetch`        | Esse método pode ser substituído em uma classe derivada para fornecer lógica quando um módulo de tarefa é buscado. |
| tarefa/envio                     | `on_teams_task_module_submit`       | Esse método pode ser substituído em uma classe derivada para fornecer lógica quando um módulo de tarefa é enviado. |

As atividades de invocação listadas nesta seção são para bots de conversa no Teams. O SDK da Estrutura de Bot também dá suporte a atividades de invocação específicas para extensões de mensagens. Para obter mais informações, consulte [O que são extensões de mensagens.](https://aka.ms/azure-bot-what-are-messaging-extensions)

---
