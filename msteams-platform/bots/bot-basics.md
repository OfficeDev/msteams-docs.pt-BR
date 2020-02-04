---
title: Noções básicas de bot
author: clearab
description: Entenda as noções básicas dos bots no Teams.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: e1b0c79b73ae89c8ab76ba0a1ff045603ab0b932
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672618"
---
# <a name="bot-basics"></a>Noções básicas de bot

Esta é uma introdução que se baseia no artigo [como os bots funcionam](https://aka.ms/how-bots-work) na documentação principal da [estrutura do bot](https://aka.ms/azure-bot-service-docs). Você pode encontrar esse artigo e os outros artigos na seção *conceitos* , útil.

A principal diferença no bots desenvolvido para o Microsoft Teams é a forma como as atividades são tratadas. O manipulador de atividades do Microsoft Teams é derivado do manipulador de atividades da estrutura de bot para encaminhar todas as atividades do teams antes de permitir que qualquer atividade específica de terceiros não possa ser manipulada.

## <a name="teams-activity-handlers"></a>Manipuladores de atividade do teams

Quando um bot para o Microsoft Teams recebe uma atividade, ele a passa para seus *manipuladores de atividade*. Nos bastidores, há um manipulador de base chamado de *manipulador de ativação*, que todas as atividades são roteadas. O *manipulador de Turn* chama o manipulador de atividade necessário para lidar com qualquer tipo de atividade recebido. Onde um bot projetado para o Microsoft Teams difere é que ele é `TeamsActivityHandler` derivado de uma classe derivada da classe da `ActivityHandler` estrutura de bot.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

Como com qualquer bot criado usando o Microsoft bot Framework, se o bot receber uma atividade de mensagem, o manipulador de ativação vê essa atividade de entrada e `OnMessageActivityAsync` a envia para o manipulador de atividade. No Teams, essa funcionalidade permanece a mesma. Se o bot receber uma atividade de atualização de conversa, o manipulador de ativação enxergará a atividade de entrada `OnConversationUpdateActivityAsync` e a enviará para o manipulador de atividades do Microsoft *Teams* que irá primeiro procurar qualquer evento específico do Teams e passá-lo ao manipulador de atividade da estrutura de bot, caso nenhum seja encontrado.

Na classe do manipulador de atividades do Microsoft Teams, há dois manipuladores de `OnConversationUpdateActivityAsync` atividade de equipes principais, que roteiam `OnInvokeActivityAsync` todas as atividades de atualização de conversa e que roteiam as atividades de chamadas de todas as equipes.

Para implementar sua lógica para manipuladores de atividade específicos do Teams, você substituirá esses métodos no bot, conforme mostrado na seção de [lógica de bot](#bot-logic) abaixo. Para cada um desses manipuladores, não há nenhuma implementação de base, portanto, basta adicionar a lógica que você deseja na substituição.

# <a name="javascripttabjavascript"></a>[JavaScript](#tab/javascript)

Como com qualquer bot criado usando o Microsoft bot Framework, se o bot receber uma atividade de mensagem, o manipulador de ativação vê essa atividade de entrada e `onMessage` a envia para o manipulador de atividade. No Teams, essa funcionalidade permanece a mesma. Se o bot receber uma atividade de atualização de conversa, o manipulador de ativação enxergará a atividade de entrada `dispatchConversationUpdateActivity` e a enviará para o manipulador de atividades do Microsoft *Teams* que irá primeiro procurar qualquer evento específico do Teams e passá-lo ao manipulador de atividade de estruturas de bot, se nenhum for encontrado.

Na classe do manipulador de atividades do Microsoft Teams, há dois manipuladores de `dispatchConversationUpdateActivity` atividade de equipes principais, que roteiam `onInvokeActivity` todas as atividades de atualização de conversa e que roteiam as atividades de chamadas de todas as equipes.

Para implementar sua lógica para manipuladores de atividade específicos do Teams, você substituirá esses métodos no bot conforme visto na seção [lógica de bot](#bot-logic) abaixo. Para cada um desses manipuladores, defina sua lógica de bot e, em seguida, **não se esqueça de `next()` ligar para o fim**. Chamando `next()` você garante que o próximo manipulador será executado.

---

## <a name="bot-logic"></a>Lógica de bot

A lógica de bot processa as atividades de entrada de um ou mais dos seus canais de bot e gera atividades de saída em resposta.  Isso ainda se aplica aos bots provenientes da classe manipulador de atividades do Microsoft Teams, que primeiro verifica as atividades de equipes e, em seguida, passa todas as outras atividades para o manipulador de atividade de estruturas de bot.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

#### <a name="core-bot-framework-handlers"></a>Manipuladores da estrutura principal do bot

Todos os manipuladores de atividade descritos abaixo continuarão a funcionar como fazem com um bot que não é um Teams, com exceção das atividades de tratamento de membros *adicionados* e membros *removidos* , eles serão diferentes no contexto de uma equipe, onde o novo membro é adicionado à equipe, em vez de um thread de mensagem.

Os manipuladores definidos no `ActivityHandler` são descritos abaixo.

| Evento | Indicador | Descrição |
| :-- | :-- | :-- |
| Qualquer tipo de atividade recebido | `OnTurnAsync` | Chama um dos outros manipuladores, com base no tipo de atividade recebida. |
| Atividade de mensagem recebida | `OnMessageActivityAsync` | Substitua isso para lidar com `Message` uma atividade. |
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
| teamRenamed | `OnTeamsTeamRenamedAsync` | `return Task.CompletedTask;`Substitua isso para lidar com a equipe de equipes que está sendo renomeada. Para obter mais informações, confira [Team renomeado](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| MembersAdded | `OnTeamsMembersAddedAsync` | Chama o `OnMembersAddedAsync` método no `ActivityHandler`. Substitua isso para lidar com membros que participam de uma equipe. Para obter mais informações, consulte [membro da equipe adicionado](https://aka.ms/azure-bot-subscribe-to-conversation-events#Team-Member-Added) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| MembersRemoved | `OnTeamsMembersRemovedAsync` | Chama o `OnMembersRemovedAsync` método no `ActivityHandler`. Substitua isso para lidar com os membros que saem de uma equipe. Para obter mais informações, consulte [membro da equipe removido](https://aka.ms/azure-bot-subscribe-to-conversation-events#Team-Member-Removed) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|

#### <a name="teams-invoke--activities"></a>Atividades de invocação do teams

Veja a seguir uma lista de todos os manipuladores de atividade do teams `OnInvokeActivityAsync` chamados do manipulador de atividade do _Teams_ :

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

# <a name="javascripttabjavascript"></a>[JavaScript](#tab/javascript)

Todos os manipuladores de atividade descritos abaixo continuarão a funcionar como fazem com um bot que não é um Teams, com a exceção de lidar com as atividades dos membros *adicionados* e *removidas* , eles serão diferentes no contexto de uma equipe, onde o novo membro é adicionado à equipe, em vez de um thread de mensagem.

#### <a name="core-bot-framework-handlers"></a>Manipuladores da estrutura principal do bot

Os manipuladores definidos no `ActivityHandler` são descritos abaixo.

| Evento | Indicador | Descrição |
| :-- | :-- | :-- |
| Qualquer tipo de atividade recebido | `onTurn` | Chama um dos outros manipuladores, com base no tipo de atividade recebida. |
| Atividade de mensagem recebida | `onMessage` | Forneça uma função para que isso trate de `Message` uma atividade. |
| Atividade de atualização de conversa recebida | `onConversationUpdate` | Em uma `ConversationUpdate` atividade, chama um manipulador se outros membros que não o bot ingressaram ou saíram da conversa. |
| Membros não-bot ingressaram na conversa | `onMembersAdded` | Forneça uma função para isso para lidar com membros que participam de uma conversa. |
| Membros que não são bot saíram da conversa | `onMembersRemoved` | Forneça uma função para isso para lidar com os membros que saem de uma conversa. |
| Atividade de evento recebida | `onEvent` | Em uma `Event` atividade, chama um manipulador específico para o tipo de evento. |
| Atividade de evento de resposta de token recebida | `onTokenResponseEvent` | Forneça uma função para tratar de eventos de resposta de token. |
| Outro tipo de atividade recebido | `onUnrecognizedActivityType` | Forneça uma função para que isso trate de qualquer tipo de atividade, caso contrário, não manipulado. |
| Manipuladores de atividade concluídos | `onDialog` | Forneça uma função para que isso trate de qualquer processamento que deve ser feito no final de uma vez, após a conclusão do restante dos manipuladores de atividade. |

#### <a name="teams-specific-handlers"></a>Manipuladores específicos de equipes

O `TeamsActivityHandler` estende a lista de manipuladores acima para incluir o seguinte:

| Evento | Indicador | Descrição |
| :-- | :-- | :-- |
| channelCreated | `OnTeamsChannelCreatedAsync` | Substitua isso para manipular um canal do teams que está sendo criado. Para obter mais informações, consulte [canal criado](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-created) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| channelDeleted | `OnTeamsChannelDeletedAsync` | Substitua isso para manipular um canal do teams que está sendo excluído. Para obter mais informações, consulte [canal excluído](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-deleted) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events).|
| channelRenamed | `OnTeamsChannelRenamedAsync` | Substitua isso para manipular um canal do teams que está sendo renomeado. Para obter mais informações, consulte [canal renomeado](https://aka.ms/azure-bot-subscribe-to-conversation-events#channel-renamed) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| teamRenamed | `OnTeamsTeamRenamedAsync` | `return Task.CompletedTask;`Substitua isso para lidar com a equipe de equipes que está sendo renomeada. Para obter mais informações, confira [Team renomeado](https://aka.ms/azure-bot-subscribe-to-conversation-events#team-renamed) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| MembersAdded | `OnTeamsMembersAddedAsync` | Chama o `OnMembersAddedAsync` método no `ActivityHandler`. Substitua isso para lidar com membros que participam de uma equipe. Para obter mais informações, consulte [membro da equipe adicionado](https://aka.ms/azure-bot-subscribe-to-conversation-events#Team-Member-Added) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events). |
| MembersRemoved | `OnTeamsMembersRemovedAsync` | Chama o `OnMembersRemovedAsync` método no `ActivityHandler`. Substitua isso para lidar com os membros que saem de uma equipe. Para obter mais informações, consulte [membro da equipe removido](https://aka.ms/azure-bot-subscribe-to-conversation-events#Team-Member-Removed) em [eventos de atualização de conversa](https://aka.ms/azure-bot-subscribe-to-conversation-events). |

#### <a name="teams-invoke-activities"></a>Atividades de invocação do teams

Veja a seguir uma lista de todos os manipuladores de atividade do teams `onInvokeActivity` chamados do manipulador de atividade do _Teams_ :

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

As atividades de invocação listadas acima são para bots de conversas no Microsoft Teams. O SDK da estrutura de bot também oferece suporte a invocações específicas para extensões de mensagens. Para obter mais informações, consulte [o que são extensões de mensagens](https://aka.ms/azure-bot-what-are-messaging-extensions)

---
