---
title: Manipuladores de atividade de bot
author: surbhigupta
description: Entenda os manipuladores de atividades do bot no Teams.
ms.topic: conceptual
localization_priority: Normal
ms.author: anclear
ms.openlocfilehash: 4ecc40abca84466887466ef6a25ab6e57a38328c
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069032"
---
# <a name="bot-activity-handlers"></a>Manipuladores de atividade de bot

Este documento se baseia no artigo sobre como [os bots funcionam](https://aka.ms/how-bots-work) na documentação principal [da Estrutura de Bots.](https://aka.ms/azure-bot-service-docs) A principal diferença entre bots desenvolvidos para Microsoft Teams e a Estrutura de Bot principal está nos recursos fornecidos no Teams.

Para organizar a lógica de conversa para o bot, um manipulador de atividades é usado. As atividades são manipuladas de duas maneiras usando Teams manipuladores de atividade e lógica de bot. O Teams de atividades adiciona suporte Microsoft Teams eventos e interações específicos. O objeto bot contém o raciocínio ou a lógica de conversa para uma curva e expõe um manipulador de turnos, que é o método que pode aceitar atividades de entrada do adaptador de bot.

## <a name="teams-activity-handlers"></a>Teams manipuladores de atividades

Teams manipulador de atividades é derivado do manipulador de Microsoft Bot Framework de atividade do Microsoft Bot Framework. Ele encaminha todas as Teams antes de permitir que qualquer atividade não Teams específicas seja manipulada.

Quando um bot para Teams recebe uma atividade, ele é roteado para os manipuladores de atividade. Todas as atividades são roteados por um manipulador base chamado manipulador de turno. O manipulador de turno chama o manipulador de atividades necessário para gerenciar qualquer atividade recebida. O Teams bot é derivado da `TeamsActivityHandler` classe, que é derivada da classe da Estrutura de `ActivityHandler` Bot.

# <a name="c"></a>[C#](#tab/csharp)

Os bots são criados usando a Estrutura de Bot. Se os bots receberem uma atividade de mensagem, o manipulador de turno receberá uma notificação dessa atividade de entrada. Em seguida, o manipulador de turnos envia a atividade de entrada para o `OnMessageActivityAsync` manipulador de atividades. No Teams, essa funcionalidade permanece a mesma. Se o bot receber uma atividade de atualização de conversa, o manipulador de turno receberá uma notificação dessa atividade de entrada e enviará a atividade de entrada para `OnConversationUpdateActivityAsync` . O Teams de atividades verifica primeiro se há Teams eventos específicos. Se nenhum evento for encontrado, ele os passará para o manipulador de atividades da Estrutura de Bot.

Na classe Teams manipulador de atividades, há dois manipuladores Teams de atividade primários `OnConversationUpdateActivityAsync` e `OnInvokeActivityAsync` . `OnConversationUpdateActivityAsync`encaminha todas as atividades de atualização de conversa `OnInvokeActivityAsync` e encaminha todas as Teams atividades de invocação.

Para implementar sua lógica para Teams de atividades específicas, você deve substituir os métodos em seu bot, conforme mostrado na seção [lógica do bot.](#bot-logic) Não há implementação base para esses manipuladores, portanto, você deve adicionar a lógica que deseja em sua substituição.

# <a name="javascript"></a>[JavaScript](#tab/javascript)

Os bots são criados usando a Estrutura de Bot. Se os bots receberem uma atividade de mensagem, o manipulador de turno receberá uma notificação dessa atividade de entrada. Em seguida, o manipulador de turnos envia a atividade de entrada para o `onMessage` manipulador de atividades. No Teams, essa funcionalidade permanece a mesma. Se o bot receber uma atividade de atualização de conversa, o manipulador de turno receberá uma notificação dessa atividade de entrada e enviará a atividade de entrada para `dispatchConversationUpdateActivity` . O Teams de atividades verifica primeiro se há Teams eventos específicos. Se nenhum evento for encontrado, ele os passará para o manipulador de atividades da Estrutura de Bot.

Na classe Teams manipulador de atividades, há dois manipuladores Teams de atividade primários `dispatchConversationUpdateActivity` e `onInvokeActivity` . `dispatchConversationUpdateActivity`encaminha todas as atividades de atualização de conversa `onInvokeActivity` e encaminha todas as Teams atividades de invocação.

Para implementar sua lógica para Teams de atividades específicas, você deve substituir os métodos em seu bot, conforme mostrado na seção [lógica do bot.](#bot-logic) Defina sua lógica de bot para esses manipuladores e, em seguida, certifique-se de `next()` chamar no final. Ao chamar `next()` você, certifique-se de que o próximo manipulador seja executado.

# <a name="python"></a>[Python](#tab/python)

Os bots são criados usando a Estrutura de Bot. Se os bots receberem uma atividade de mensagem, o manipulador de turno receberá uma notificação dessa atividade de entrada. Em seguida, o manipulador de turnos envia a atividade de entrada para o `on_message_activity` manipulador de atividades. No Teams, essa funcionalidade permanece a mesma. Se o bot receber uma atividade de atualização de conversa, o manipulador de turno receberá uma notificação dessa atividade de entrada e enviará a atividade de entrada para `on_conversation_update_activity` . O Teams de atividades verifica primeiro se há Teams eventos específicos. Se nenhum evento for encontrado, ele os passará para o manipulador de atividades da Estrutura de Bot.

Na classe Teams manipulador de atividades, há dois manipuladores Teams de atividade primários `on_conversation_update_activity` e `on_invoke_activity` . `on_conversation_update_activity`encaminha todas as atividades de atualização de conversa `on_invoke_activity` e encaminha todas as Teams atividades de invocação.

Para implementar sua lógica para Teams de atividades específicas, você deve substituir os métodos em seu bot, conforme mostrado na seção [lógica do bot.](#bot-logic) Não há implementação base para esses manipuladores, portanto, você deve adicionar a lógica que deseja em sua substituição.

---

## <a name="bot-logic"></a>Lógica bot

A lógica do bot processa as atividades de entrada de um ou mais de seus canais bot e, em resposta, gera atividades de saída. Isso ainda é verdadeiro para bots derivados da classe Teams manipulador de atividades, que primeiro verifica Teams atividades. Depois de verificar Teams atividades, ele passa todas as outras atividades para o manipulador de atividades da Estrutura de Bot.

# <a name="c"></a>[C#](#tab/csharp)

#### <a name="core-bot-framework-handlers"></a>Manipuladores da Estrutura de Bots Principais

>[!NOTE]
> Com **exceção**  das atividades dos membros adicionados e removidos, todos os manipuladores de atividades descritos nesta seção continuam a funcionar como fazem com um bot que não Teams.

Manipuladores de atividades são diferentes no contexto de uma equipe, onde um novo membro é adicionado à equipe em vez de um thread de mensagem.

A lista de manipuladores definidos `ActivityHandler` inclui o seguinte:

| Event | Manipulador | Descrição |
| :-- | :-- | :-- |
| Qualquer tipo de atividade recebida | `OnTurnAsync` | Este método chama um dos outros manipuladores, com base no tipo de atividade recebida. |
| Atividade de mensagem recebida | `OnMessageActivityAsync` | Esse método pode ser substituído para manipular uma `Message` atividade. |
| Atividade de atualização de conversa recebida | `OnConversationUpdateActivityAsync` | Esse método chama um manipulador se outros membros que não o bot ingressaram ou deixaram a conversa em uma `ConversationUpdate` atividade. |
| Membros que não são bots ingressaram na conversa | `OnMembersAddedAsync` | Esse método pode ser substituído para lidar com membros que ingressaram em uma conversa. |
| Membros que não são bots deixaram a conversa | `OnMembersRemovedAsync` | Esse método pode ser substituído para lidar com membros deixando uma conversa. |
| Atividade de evento recebida | `OnEventActivityAsync` | Este método chama um manipulador específico para o tipo de evento, em uma `Event` atividade. |
| Atividade de evento de resposta de token recebida | `OnTokenResponseEventAsync` | Esse método pode ser substituído para manipular eventos de resposta de token. |
| Atividade de evento não-token-response recebida | `OnEventAsync` | Esse método pode ser substituído para lidar com outros tipos de eventos. |
| Outro tipo de atividade recebido | `OnUnrecognizedActivityTypeAsync` | Esse método pode ser substituído para lidar com qualquer tipo de atividade de outra forma não manuseado. |

#### <a name="teams-specific-activity-handlers"></a>Teams manipuladores de atividades específicos

O estende a lista de manipuladores na seção principais manipuladores da Estrutura de `TeamsActivityHandler` Bots para incluir o seguinte:

| Event | Manipulador | Descrição |
| :-- | :-- | :-- |
| channelCreated | `OnTeamsChannelCreatedAsync` | Esse método pode ser substituído para manipular um canal Teams sendo criado. Para obter mais informações, consulte [canal criado em](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created) eventos de atualização de [conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| channelDeleted | `OnTeamsChannelDeletedAsync` | Esse método pode ser substituído para manipular um canal Teams sendo excluído. Para obter mais informações, [consulte channel deleted in](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted) conversation update [events](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| channelRenamed | `OnTeamsChannelRenamedAsync` | Esse método pode ser substituído para manipular um canal Teams sendo renomeado. Para obter mais informações, consulte [canal renomeado em](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| teamRenamed | `OnTeamsTeamRenamedAsync` | `return Task.CompletedTask;`Esse método pode ser substituído para manipular uma equipe Teams sendo renomeada. Para obter mais informações, consulte [team renomeado em](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| MembersAdded | `OnTeamsMembersAddedAsync` | Este método chama o `OnMembersAddedAsync` método em `ActivityHandler` . O método pode ser substituído para manipular membros que ingressaram em uma equipe. Para obter mais informações, consulte [membros da equipe adicionados](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-added) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| MembersRemoved | `OnTeamsMembersRemovedAsync` | Este método chama o `OnMembersRemovedAsync` método em `ActivityHandler` . O método pode ser substituído para manipular membros deixando uma equipe. Para obter mais informações, consulte [membros da equipe removidos](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-removed) em eventos [de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|

#### <a name="teams-invoke-activities"></a>Teams atividades de invocação

A lista de Teams de atividades chamadas do manipulador de Teams `OnInvokeActivityAsync` de atividade inclui o seguinte:

| Invocar tipos                    | Manipulador                              | Descrição                                                  |
| :-----------------------------  | :----------------------------------- | :----------------------------------------------------------- |
| CardAction.Invoke               | `OnTeamsCardActionInvokeAsync`       | Esse método é invocado quando uma atividade de invocação de ação de cartão é recebida do conector. |
| fileConsent/invoke              | `OnTeamsFileConsentAcceptAsync`      | Esse método é invocado quando um cartão de consentimento de arquivo é aceito pelo usuário. |
| fileConsent/invoke              | `OnTeamsFileConsentAsync`            | Esse método é invocado quando uma atividade de cartão de consentimento de arquivo é recebida do conector. |
| fileConsent/invoke              | `OnTeamsFileConsentDeclineAsync`     | Esse método é invocado quando um cartão de consentimento de arquivo é recusado pelo usuário. |
| actionableMessage/executeAction | `OnTeamsO365ConnectorCardActionAsync` | Esse método é invocado quando uma atividade de ação de cartão de conector O365 é recebida do conector. |
| signin/verifyState              | `OnTeamsSigninVerifyStateAsync`      | Esse método é invocado quando uma atividade de estado signIn é recebida do conector. |
| task/fetch                      | `OnTeamsTaskModuleFetchAsync`        | Esse método pode ser substituído em uma classe derivada para fornecer lógica quando um módulo de tarefa é buscado. |
| task/submit                     | `OnTeamsTaskModuleSubmitAsync`       | Esse método pode ser substituído em uma classe derivada para fornecer lógica quando um módulo de tarefa é enviado. |

As atividades de invocação listadas nesta seção são para bots de conversa no Teams. O SDK da Estrutura de Bot também dá suporte a atividades de invocação específicas de extensões de mensagens. Para obter mais informações, consulte [o que são extensões de mensagens](https://aka.ms/azure-bot-what-are-messaging-extensions).

# <a name="javascript"></a>[JavaScript](#tab/javascript)

#### <a name="core-bot-framework-handlers"></a>Manipuladores da Estrutura de Bots Principais

>[!NOTE]
> Com **exceção**  das atividades dos membros adicionados e removidos, todos os manipuladores de atividades descritos nesta seção continuam a funcionar como fazem com um bot que não Teams.

Os manipuladores de atividades são diferentes no contexto de uma equipe, onde o novo membro é adicionado à equipe em vez de um thread de mensagem.

A lista de manipuladores definidos `ActivityHandler` inclui o seguinte:

| Event | Manipulador | Descrição |
| :-- | :-- | :-- |
| Qualquer tipo de atividade recebida | `onTurn` | Este método chama um dos outros manipuladores, com base no tipo de atividade recebida. |
| Atividade de mensagem recebida | `onMessage` | Esse método ajuda a manipular uma `Message` atividade. |
| Atividade de atualização de conversa recebida | `onConversationUpdate` | Esse método chama um manipulador se outros membros que não o bot ingressaram ou deixaram a conversa em uma `ConversationUpdate` atividade. |
| Membros que não são bots ingressaram na conversa | `onMembersAdded` | Esse método ajuda a lidar com membros que ingressaram em uma conversa. |
| Membros que não são bots deixaram a conversa | `onMembersRemoved` | Esse método ajuda a lidar com membros deixando uma conversa. |
| Atividade de evento recebida | `onEvent` | Este método chama um manipulador específico para o tipo de evento, em uma `Event` atividade. |
| Atividade de evento de resposta de token recebida | `onTokenResponseEvent` | Este método ajuda a lidar com eventos de resposta de token. |
| Outro tipo de atividade recebido | `onUnrecognizedActivityType` | Este método ajuda a lidar com qualquer tipo de atividade, caso contrário, não é manuseado. |

#### <a name="teams-specific-activity-handlers"></a>Teams manipuladores de atividades específicos

O estende a lista de manipuladores na seção principais manipuladores da Estrutura de `TeamsActivityHandler` Bots para incluir o seguinte:

| Event | Manipulador | Descrição |
| :-- | :-- | :-- |
| channelCreated | `OnTeamsChannelCreatedAsync` | Esse método pode ser substituído para manipular um canal Teams sendo criado. Para obter mais informações, consulte [canal criado em](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created) eventos de atualização de [conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| channelDeleted | `OnTeamsChannelDeletedAsync` | Esse método pode ser substituído para manipular um canal Teams sendo excluído. Para obter mais informações, [consulte channel deleted in](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted) conversation update [events](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| channelRenamed | `OnTeamsChannelRenamedAsync` | Esse método pode ser substituído para manipular um canal Teams sendo renomeado. Para obter mais informações, consulte [canal renomeado em](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| teamRenamed | `OnTeamsTeamRenamedAsync` | `return Task.CompletedTask;`Esse método pode ser substituído para manipular uma equipe Teams sendo renomeada. Para obter mais informações, consulte [team renomeado em](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| MembersAdded | `OnTeamsMembersAddedAsync` | Este método chama o `OnMembersAddedAsync` método em `ActivityHandler` . O método pode ser substituído para manipular membros que ingressaram em uma equipe. Para obter mais informações, consulte [membros da equipe adicionados](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-added) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| MembersRemoved | `OnTeamsMembersRemovedAsync` | Este método chama o `OnMembersRemovedAsync` método em `ActivityHandler` . O método pode ser substituído para manipular membros deixando uma equipe. Para obter mais informações, consulte [membros da equipe removidos](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-removed) em eventos [de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events). |

#### <a name="teams-invoke-activities"></a>Teams atividades de invocação

A lista de Teams de atividades chamadas do manipulador de Teams `onInvokeActivity` de atividade inclui o seguinte:

| Invocar tipos                    | Manipulador                              | Descrição                                                  |
| :-----------------------------  | :----------------------------------- | :----------------------------------------------------------- |
| CardAction.Invoke               | `handleTeamsCardActionInvoke`       | Esse método é invocado quando uma atividade de invocação de ação de cartão é recebida do conector. |
| fileConsent/invoke              | `handleTeamsFileConsentAccept`      | Esse método é invocado quando um cartão de consentimento de arquivo é aceito pelo usuário. |
| fileConsent/invoke              | `handleTeamsFileConsent`            | Esse método é invocado quando uma atividade de cartão de consentimento de arquivo é recebida do conector. |
| fileConsent/invoke              | `handleTeamsFileConsentDecline`     | Esse método é invocado quando um cartão de consentimento de arquivo é recusado pelo usuário. |
| actionableMessage/executeAction | `handleTeamsO365ConnectorCardAction` | Esse método é invocado quando uma atividade de ação de cartão de conector O365 é recebida do conector. |
| signin/verifyState              | `handleTeamsSigninVerifyState`      | Esse método é invocado quando uma atividade de estado signIn é recebida do conector. |
| task/fetch                      | `handleTeamsTaskModuleFetch`        | Esse método pode ser substituído em uma classe derivada para fornecer lógica quando um módulo de tarefa é buscado. |
| task/submit                     | `handleTeamsTaskModuleSubmit`       | Esse método pode ser substituído em uma classe derivada para fornecer lógica quando um módulo de tarefa é enviado. |

As atividades de invocação listadas nesta seção são para bots de conversa no Teams. O SDK da Estrutura de Bot também dá suporte a atividades de invocação específicas de extensões de mensagens. Para obter mais informações, consulte [o que são extensões de mensagens](https://aka.ms/azure-bot-what-are-messaging-extensions).

# <a name="python"></a>[Python](#tab/python)

#### <a name="core-bot-framework-handlers"></a>Manipuladores da Estrutura de Bots Principais

>[!NOTE]
> Com **exceção**  das atividades dos membros adicionados e removidos, todos os manipuladores de atividades descritos nesta seção continuam a funcionar como fazem com um bot que não Teams.

Os manipuladores de atividades são diferentes no contexto de uma equipe, onde o novo membro é adicionado à equipe em vez de um thread de mensagem.

A lista de manipuladores definidos `ActivityHandler` inclui o seguinte:

| Event | Manipulador | Descrição |
| :-- | :-- | :-- |
| Qualquer tipo de atividade recebida | `on_turn` | Este método chama um dos outros manipuladores, com base no tipo de atividade recebida. |
| Atividade de mensagem recebida | `on_message_activity` | Esse método pode ser substituído para manipular uma `Message` atividade. |
| Atividade de atualização de conversa recebida | `on_conversation_update_activity` | Este método chama um manipulador se membros diferentes do bot ingressar ou deixar a conversa. |
| Membros que não são bots ingressaram na conversa | `on_members_added_activity` | Esse método pode ser substituído para lidar com membros que ingressaram em uma conversa. |
| Membros que não são bots deixaram a conversa | `on_members_removed_activity` | Esse método pode ser substituído para lidar com membros deixando uma conversa. |
| Atividade de evento recebida | `on_event_activity` | Este método chama um manipulador específico para o tipo de evento. |
| Atividade de evento de resposta de token recebida | `on_token_response_event` | Esse método pode ser substituído para manipular eventos de resposta de token. |
| Atividade de evento não-token-response recebida | `on_event` | Esse método pode ser substituído para lidar com outros tipos de eventos. |
| Outros tipos de atividade recebidos | `on_unrecognized_activity_type` | Esse método pode ser substituído para manipular qualquer tipo de atividade que não seja manipulada. |

#### <a name="teams-specific-activity-handlers"></a>Teams manipuladores de atividades específicos

A estende a lista de manipuladores da seção principais manipuladores da Estrutura de `TeamsActivityHandler` Bots para incluir o seguinte:

| Event | Manipulador | Descrição |
| :-- | :-- | :-- |
| channelCreated | `on_teams_channel_created` | Esse método pode ser substituído para manipular um canal Teams sendo criado. Para obter mais informações, consulte [canal criado em](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created) eventos de atualização de [conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| channelDeleted | `on_teams_channel_deleted` | Esse método pode ser substituído para manipular um canal Teams sendo excluído. Para obter mais informações, [consulte channel deleted in](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted) conversation update [events](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| channelRenamed | `on_teams_channel_renamed` | Esse método pode ser substituído para manipular um canal Teams sendo renomeado. Para obter mais informações, consulte [canal renomeado em](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| teamRenamed | `on_teams_team_renamed` | `return Task.CompletedTask;`Esse método pode ser substituído para manipular uma equipe Teams sendo renomeada. Para obter mais informações, consulte [team renomeado em](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| MembersAdded | `on_teams_members_added` | Este método chama o `OnMembersAddedAsync` método em `ActivityHandler` . O método pode ser substituído para manipular membros que ingressaram em uma equipe. Para obter mais informações, consulte [membros da equipe adicionados](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-added) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| MembersRemoved | `on_teams_members_removed` | Este método chama o `OnMembersRemovedAsync` método em `ActivityHandler` . O método pode ser substituído para manipular membros deixando uma equipe. Para obter mais informações, consulte [membros da equipe removidos](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-members-removed) em eventos [de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|

#### <a name="teams-invoke-activities"></a>Teams atividades de invocação

A lista de Teams de atividades chamadas do manipulador de Teams `on_invoke_activity` de atividade inclui o seguinte:

| Invocar tipos                    | Manipulador                              | Descrição                                                  |
| :-----------------------------  | :----------------------------------- | :----------------------------------------------------------- |
| CardAction.Invoke               | `on_teams_card_action_invoke`       | Esse método é invocado quando uma atividade de invocação de ação de cartão é recebida do conector. |
| fileConsent/invoke              | `on_teams_file_consent_accept`      | Esse método é invocado quando um cartão de consentimento de arquivo é aceito pelo usuário. |
| fileConsent/invoke              | `on_teams_file_consent`            | Esse método é invocado quando uma atividade de cartão de consentimento de arquivo é recebida do conector. |
| fileConsent/invoke              | `on_teams_file_consent_decline`     | Esse método é invocado quando um cartão de consentimento de arquivo é recusado pelo usuário. |
| actionableMessage/executeAction | `on_teams_o365_connector_card_action` | Esse método é invocado quando uma atividade de ação de cartão de conector O365 é recebida do conector. |
| signin/verifyState              | `on_teams_signin_verify_state`      | Esse método é invocado quando uma atividade de estado signIn é recebida do conector. |
| task/fetch                      | `on_teams_task_module_fetch`        | Esse método pode ser substituído em uma classe derivada para fornecer lógica quando um módulo de tarefa é buscado. |
| task/submit                     | `on_teams_task_module_submit`       | Esse método pode ser substituído em uma classe derivada para fornecer lógica quando um módulo de tarefa é enviado. |

As atividades de invocação listadas nesta seção são para bots de conversa no Teams. O SDK da Estrutura de Bot também dá suporte a atividades de invocação específicas de extensões de mensagens. Para obter mais informações, consulte [o que são extensões de mensagens](https://aka.ms/azure-bot-what-are-messaging-extensions).

---

* * *

Agora que você se familiarizou com manipuladores de atividades de bot, vamos ver como os bots se comportam de forma diferente, dependendo da conversa e das mensagens recebidas ou enviadas.

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Noções básicas sobre conversas](~/bots/how-to/conversations/conversation-basics.md)
