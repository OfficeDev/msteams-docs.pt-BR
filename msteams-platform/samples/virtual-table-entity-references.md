---
title: Referências de entidade de tabela virtual
author: surbhigupta
description: Neste módulo, saiba mais sobre a referência de entidade de tabelas virtuais e seus atributos no Microsoft Teams.
ms.localizationpriority: medium
ms.author: v-npaladugu
ms.topic: conceptual
ms.openlocfilehash: 34166c49eb61c52f8eec94b34844ef27d52715ef
ms.sourcegitcommit: 0bb822b30739e4a532a36764dad2dbf35a81ba29
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/03/2022
ms.locfileid: "67178774"
---
# <a name="virtual-tables-entity-reference"></a>Referência de entidade de tabelas virtuais

A colaboração controla entidades virtuais e seus atributos têm um mapeamento um-para-um com um tipo de recurso específico do Microsoft Graph. Por exemplo, as entidades da Tarefa Planejador do Graph são mapeadas para o [tipo de recurso da Tarefa planejador do Microsoft Graph](/graph/api/resources/plannertask). A entidade virtual compartilha os mesmos atributos que o tipo de recurso.

> [!NOTE]
> Atualmente, os controles de colaboração estão disponíveis apenas na [versão prévia do desenvolvedor público](~/resources/dev-preview/developer-preview-intro.md).

## <a name="collaboration-controls-virtual-entities"></a>A colaboração controla entidades virtuais

| Nome | Descrição |
|---|---|
| Tarefa Planejador de Grafo | A tabela de tarefas planejador do Graph representa uma tarefa do Planner no Microsoft 365. |
| Plano planejador do Graph | A tabela Plano planejador do Graph representa um plano do Planner no Microsoft 365. |
| Evento Graph | A tabela Evento do Graph representa um evento em um calendário de usuário ou o calendário padrão de um grupo do Microsoft 365. |
| Compromisso de reserva do Graph | A tabela Compromisso de Reserva do Graph representa um compromisso do cliente para um Serviço de Reserva, executado por um conjunto de membros da equipe, provIDed por um Microsoft Bookings negócios. |
| Unidade do Graph | A tabela Unidade do Graph representa o objeto de nível superior que representa o OneDrive de um usuário ou uma biblioteca de documentos no SharePoint. |
| Item de Unidade de Grafo | A tabela Item de Unidade do Graph representa um arquivo, pasta ou outro item armazenado em uma unidade. |

## <a name="graph-planner-task"></a>Tarefa Planejador de Grafo

* Nome da entidade: m365_graphplannertask.
* Recurso do Graph: [tipo de recurso plannerTask](/graph/api/resources/plannertask)
* Não há suporte para classificação.
* Não há suporte para filtragem.
* Há suporte para paginação controlada pelo servidor, com o tamanho máximo da página sendo 400.

### <a name="attributes-for-graph-planner-task"></a>Atributos para a tarefa Planejador de Grafo

| Coluna  | Tipo de Dataverse | Detalhes |
|---|---|---|
| `m365_collaborationrootid` | String | A ID raiz de colaboração do registro de sessão de colaboração está associada a várias sessões de colaboração. Isso será retornado como uma cadeia de caracteres delimitada por vírgula. Observe que esse atributo não será retornado ao recuperar vários registros. |
| `m365_activechecklistitemcount` | Int32 | Número de itens da lista de verificação com valor definido como false, representando itens incompletos. |
| `m365_graphplannertaskId` | Guid | Identificador exclusivo da tarefa planejador de grafo. |
| `m365_appliedcategories` | Cadeia de Caracteres | Número de itens da lista de verificação com valor definido como false, representando itens incompletos. |
| `m365_appliedcategories` | Cadeia de Caracteres | As categorias às quais a tarefa foi aplicada. Esse atributo é uma cadeia de caracteres codificada em JSON, por exemplo"{ \"category1\": true, \"category6\": true, \"category9\": true }" |
| `m365_assigneepriority` | String | Dica usada para ordenar itens desse tipo em um modo de exibição de lista. O formato é definido como descrito usando [dicas de ordem no Planner](/graph/api/resources/planner-order-hint-format). |
| `m365_assignments` | String | O conjunto de destinatários ao qual a tarefa é atribuída. Esse atributo é uma cadeia de caracteres codificada em JSON, por exemplo"{\" 7be...\": {\"assignedBy\": {user\": {\"\"displayName\", \"email\", \"ID\":\" 7be...\"}, \"group\": null, \"application\": null \"device\": null}" |
| `m365_bucketid` | String | ID do bucket ao qual a tarefa pertence. O bucket precisa estar no plano no qual a tarefa está. Tem 28 caracteres e diferencia maiúsculas de minúsculas. [Formatar validação](/graph/api/resources/planner-identifiers-disclaimer) é feito no serviço. |
| `m365_checklistitemcount` | Int32 | Número de itens de lista de verificação que estão presentes na tarefa. |
| `m365_completedby` | String | Identidade do usuário que concluiu a tarefa. Esse atributo é uma cadeia de caracteres codificada em JSON, por exemplo {\"user: {\"displayName,ID\"\"\":\"d55...\"}}\" |
| `m365_completeddatetime` | DateTime | Somente leitura. Data e hora em que o 'percentComplete' da tarefa é definido como '100'. O tipo Timestamp representa informações de data e hora usando o formato ISO 8601 e está sempre no horário UTC. Por exemplo, meia-noite UTC em 1º de janeiro de 2014 é 01-01-01T00:00:00Z |
| `m365_conversationthreadid` |String | Identificação do thread da conversa na tarefa. Essa é a identificação do objeto do thread da conversa criado no grupo. |
| `m365_createdby` | Cadeia de Caracteres | Identidade do usuário que criou a tarefa. Esse atributo é uma cadeia de caracteres codificada em JSON, por exemplo {\"user: {\"displayName,ID\"\"\":\"d55...\"}}\" |
| `m365_createddatetime` | DateTime | Somente leitura. A data e a hora que a tarefa é criada. O tipo Timestamp representa informações de data e hora usando o formato ISO 8601 e está sempre no horário UTC. Por exemplo, meia-noite UTC em 1º de janeiro de 2014 é 01-01-01T00:00:00Z |
| `m365_duedatetime` | DateTime | A data e a hora que a tarefa já deve estar concluída. O tipo Timestamp representa informações de data e hora usando o formato ISO 8601 e está sempre no horário UTC. Por exemplo, meia-noite UTC em 1º de janeiro de 2014 é 01-01-01T00:00:00Z |
| `m365_hasdescription` | Booliano | Somente leitura. O valor será true se o objeto de detalhes da tarefa tiver uma descrição não vazia e false caso contrário. |
| `m365_id` | String | Somente leitura. A ID da tarefa. Tem 28 caracteres e diferencia maiúsculas de minúsculas. [Formatar validação](/graph/api/resources/planner-identifiers-disclaimer) é feito no serviço.|
| `m365_orderhint` | String | Dica usada para ordenar itens desse tipo em um modo de exibição de lista. O formato é definido como descrito usando [dicas de ordem no Planner](/graph/api/resources/planner-order-hint-format). |
| `m365_percentcomplete` | Int32 | Porcentagem de conclusão da tarefa. Quando definida como 100, a tarefa é considerada concluída. |
| `m365_priority` | Int32 | Prioridade da tarefa. O intervalo válido de valores está entre 0 e 10, com o valor crescente sendo a prioridade mais baixa (0 tem a prioridade mais alta e 10 tem a prioridade mais baixa). Atualmente, o Planner interpreta os valores 0 e 1 como "urgente", 2, 3 e 4 como "importante", 5, 6 e 7 como "médio" e 8, 9 e 10 como "baixo". Além disso, o Planner define o valor 1 para "urgente", 3 para "importante", 5 para "médio" e 9 para "baixo". |
| `m365_planid` | String | ID do plano ao qual a tarefa pertence. |
| `m365_previewtype` | String | Isso define o tipo de visualização que aparece na tarefa. Os valores possíveis são: automatic, noPreview, checklist, description, reference. |
| `m365_referencecount` | Int32 | Número de referências externas existentes na tarefa.|
| `m365_startdatetime` | DateTime | A data e a hora que a tarefa começa. O tipo Timestamp representa informações de data e hora usando o formato ISO 8601 e está sempre no horário UTC. Por exemplo, meia-noite UTC em 1º de janeiro de 2014 é 01-01-01T00:00:00Z |
| `m365_title` | String |Título da tarefa. Coluna de pesquisa primária |

## <a name="graph-planner-plan"></a>Plano planejador do Graph

* Nome da entidade: m365_graphplannerplan.
* Recurso do Graph: [tipo de recurso plannerPlan](/graph/api/resources/plannerplan).
* Não há suporte para classificação.
* Não há suporte para filtragem.
* Há suporte para paginação controlada pelo servidor, com o tamanho máximo da página sendo 400.

### <a name="attributes-for-graph-planner-plan"></a>Atributos para o Plano planejador do Graph

| Coluna  | Tipo de Dataverse | Detalhes |
|---|---|---|
| `m365_collaborationrootid` | Cadeia de Caracteres | ID raiz de colaboração da sessão de colaboração à qual o registro está associado. Se o registro estiver associado a várias sessões de colaboração, isso será retornado como uma cadeia de caracteres delimitada por vírgula. Observe que esse atributo não será retornado ao recuperar vários registros.|
| `m365_graphplannerplanid` |Guid |Identificador exclusivo do plano do planejador de grafo.|
| `m365_createdby` | String | Identidade do usuário que criou a tarefa. Esse atributo é uma cadeia de caracteres codificada em JSON, por exemplo {\"user: {\"displayName,ID\"\"\":\"d55...\"}}\" |
| `m365_createddatetime` | DateTime | Somente leitura. A data e a hora que a tarefa é criada. O tipo Timestamp representa informações de data e hora usando o formato ISO 8601 e está sempre no horário UTC. Por exemplo, meia-noite UTC em 1º de janeiro de 2014 é 01-01-01T00:00:00Z |
| `m365_id` | String | Somente leitura. A ID do plano. Tem 28 caracteres e diferencia maiúsculas de minúsculas. [Formatar validação](/graph/api/resources/planner-identifiers-disclaimer) é feito no serviço.|
| `m365_owner` | Cadeia de Caracteres | A ID do [grupo](/graph/api/resources/group) que possui o plano. Depois de definida, essa propriedade não pode ser atualizada.|
| `m365_title` | Cadeia de Caracteres | Título do plano. Coluna de pesquisa primária |

## <a name="graph-event"></a>Evento Graph

* Nome da entidade: m365_graphevent
* Recurso do Graph: [tipo de recurso de evento](/graph/api/resources/event)
* Há suporte para a classificação nas seguintes colunas:
  * m365_lastmodifieddatetime
  * m365_createddatetime
  * m365_hasattachments
  * m365_importance
  * m365_responserequested
  * m365_sensitivity
  * m365_showas
  * m365_subject
* Há suporte para filtragem nas seguintes colunas:
  * m365_allownewtimeproposals
  * m365_lastmodifieddatetime
  * m365_createddatetime
  * m365_icaluID
  * m365_importance
  * m365_isallday
  * m365_iscancelled
  * m365_isdraft
  * m365_responserequested
  * m365_sensitivity
  * m365_showas
  * m365_subject
  * m365_type
* Há suporte para paginação controlada por servidor.

### <a name="attributes-for-graph-event"></a>Atributos do evento Graph

| Coluna |Tipo de Dataverse |Detalhes |
|---|---|---|
|`m365_collaborationrootid` |String |Raiz de colaboração da sessão de colaboração à qual o registro está associado. Se o registro estiver associado a várias sessões de colaboração, isso será retornado como uma cadeia de caracteres delimitada por vírgula. Observe que esse atributo não será retornado ao recuperar vários registros. |
|`m365_allownewtimeproposals` |Booliano |True, se o organizador da reunião permitir que os convidados proponham um novo horário ao responder. Caso contrário, false, que é opcional. O padrão é true. |
|`m365_attendees` |String |A coleção de participantes do evento. Esse atributo é uma cadeia de caracteres codificada em JSON, com comprimento máximo de 15.000. Por exemplo, [{{\"type\":\"required,status\"\"\":{{\"response\":\"none,time\"\"\":\"0001-01-01T00:00:00Z\"}},\"emailAddress\":\"test@contoso.com\"}}] |
|`m365_body` |Cadeia de Caracteres |O corpo da mensagem associada ao evento. Pode estar no formato HTML ou no formato de texto. Esse atributo é uma cadeia de caracteres codificada em JSON, com comprimento máximo de 15.000. Por exemplo, {contentType:html,content\"\"\":\"html/html\"}\"\"\" |
|`m365_bodypreview` |String |A visualização da mensagem associada ao evento. Está no formato de texto. |
|`m365_categories` |String |As categorias associadas ao evento. Cada categoria corresponde à propriedade displayName de uma outlookCategory definida para o usuário. Por exemplo [cadeia\" de caracteres\"] |
|`m365_changekey` |String |Identifica a versão do objeto event. Toda vez que o evento muda, ChangeKey também muda. Isso permite que o Exchange aplique alterações à versão correta do objeto. |
|`m365_createddatetime` |DateTime |O tipo Timestamp representa informações de data e hora usando o formato ISO 8601 e está sempre no horário UTC. Por exemplo, meia-noite UTC em 1º de janeiro de 2014 é 01-01-01T00:00:00Z |
|`m365_start` |DateTime |A data, a hora e o fuso horário do evento. Esse atributo é uma cadeia de caracteres codificada em JSON, com comprimento máximo de 100. Por exemplo {\"dateTime\":\"2022-01-19T11:00:00+00:00,timeZone\"\"\":\"UTC}\"|
|`m365_end` |DateTime |A data, a hora e o fuso horário em que o evento termina. Esse atributo é uma cadeia de caracteres codificada em JSON, com comprimento máximo de 100. Por exemplo {\"dateTime\":\"2022-01-19T11:00:00+00:00,timeZone\"\"\":\"UTC}\" |
|`m365_hasattachments` |Booliano |Defina como true se o evento tiver anexos. |
|`m365_hideattendees` |Booliano |Quando definido como true, cada participante só se vê na solicitação de reunião e na lista de acompanhamento da reunião. O padrão é false. |
|`m365_icaluid` |Cadeia de caracteres |Um único identificador para um evento em todos os calendários. Esta identificação é diferente para cada ocorrência em uma série recorrente. Somente leitura. |
|`m365_isallday`|Booliano |Defina como True se o evento durar o dia inteiro. Se estiver definido como True, independentemente de ser um evento de um ou de vários dias, a hora de início e término deve ser definida como meia-noite e estar no mesmo fuso horário. |
|`m365_iscancelled` |Booliano |Defina como true se o evento tiver sido cancelado. |
|`m365_id`| String |Somente leitura. ID do evento. |
|`m365_isdraft` |Booliano |Defina como true se o usuário tiver atualizado a reunião no Outlook, mas não tiver enviado as atualizações para os participantes. Defina como falso se todas as alterações forem enviadas, ou se o evento for um compromisso sem participantes.|
|`m365_isonlinemeeting`|Booliano|True se esse evento tiver informações de reunião online (ou seja, onlineMeeting aponta para um recurso onlineMeetingInfo), caso contrário, false. O padrão é false (onlineMeeting é nulo). Opcional. Depois de definir isOnlineMeeting como true, o Microsoft Graph inicializa onlineMeeting. Posteriormente, o Outlook ignora as alterações adicionais no isOnlineMeeting e a reunião permanece disponível online.|
|`m365_isorganizer`|Booliano|Defina como verdadeiro se o proprietário do calendário (especificado pela propriedade do proprietário do calendário) for o organizador do evento (especificado pela propriedade do organizador do evento). Isso também se aplica se um representante organizou o evento em nome do proprietário.|
|`m365_isremindero`n|Booliano|Defina como true se um alerta estiver definido para lembrar o usuário sobre o evento.|
|`m365_lastmodifieddatetime`|DateTime|O tipo Timestamp representa informações de data e hora usando o formato ISO 8601 e está sempre no horário UTC. Por exemplo, meia-noite UTC em 1º de janeiro de 2014 é 01-01-01T00:00:00Z|
|`m365_location`|Cadeia de Caracteres|O local do evento. Cadeia de caracteres codificada em JSON, no máximo 4000 de comprimento. Por exemplo[{\"address\":null,coordinates\"\":null,displayName\"\":\"Harry\'s Bar,locationEmailAddress\"\"\":null,locationType\"\":\"default,locationUri\"\"\":null,uniqueId\"\":\"Harry\'s Bar,uniqueIdType\"\"\":\"private}\"|
|`m365_locations`|String|Locais onde o evento é realizado ou onde participar. As propriedades location e locations sempre correspondem entre si. Se você atualizar a propriedade location, os locais anteriores na coleção locations deverão ser removidos e substituídos pelo novo valor location. Cadeia de caracteres codificada em JSON, máx. 4000 de comprimento.por exemplo[{\"address:null,coordinates\"\":null,displayName\"\":\"Harry\'s Bar,locationEmailAddress\"\"\":null,locationType\"\":\"default,locationUri\"\"\":null,uniqueId\"\":\"Harry\'s Bar,uniqueIdType\"\"\":\"private\"}]\"|
|`m365_onlinemeeting`|Cadeia de Caracteres|Detalhes para o participante entrar na reunião online. O padrão é nulo. Somente leitura. Depois de definir as propriedades isOnlineMeeting e onlineMeetingProvider para habilitar uma reunião online, o Microsoft Graph inicializa onlineMeeting. Quando definida, a reunião permanece disponível online e você não pode alterar as propriedades isOnlineMeeting, onlineMeetingProvider e onlneMeeting novamente. Cadeia de caracteres codificada em JSON, máx. 4000 de comprimento.por exemplo{conferenceId: String,joinUrl\"\"\": \"String,phones\"\"\": [{\"@odata.type\": \"microsoft.graph.phone\"}],\"quickDial\": \"String,tollFreeNumbers\"\"\": [\"String\"],\"tollNumber\": \"String}\"\"\"\"|
|`m365_onlinemeetingprovider`|String|Detalhes para o participante entrar na reunião online. O padrão é nulo. Somente leitura. Depois de definir as propriedades e isOnlineMeeting `onlineMeetingProvider` para habilitar uma reunião online, o Microsoft Graph inicializa onlineMeeting. Quando definida, a reunião permanece disponível online e você não pode alterar as propriedades isOnlineMeeting `onlineMeetingProvider`e onlneMeeting novamente.|
|`m365_onlinemeetingurl`|String|Uma URL para uma reunião online. A propriedade só é definida quando um organizador especifica no Outlook que um evento é uma reunião online como o Skype. Somente leitura. Para acessar a URL para ingressar em uma reunião online, use `joinUrl`, que é exposto por meio `onlineMeeting` da propriedade do evento. A `onlineMeetingUrl` propriedade será preterida no futuro.|
|`m365_organizer`|String|O organizador do evento. Cadeia de caracteres codificada em JSON, no máximo 4000 de comprimento. {\"emailAddress\":{\"@odata.type\":\"microsoft.graph.emailAddress\"}}|
|`m365_originalendtimezone`|String|O fuso horário de término que foi definido quando o evento foi criado. Um valor de tzone://Microsoft/Custom indica que um fuso horário personalizado herdado foi definido no Outlook da área de trabalho.|
|`m365_originalstart`|DateTime|Representa a hora de início de um evento quando ele é inicialmente criado como uma ocorrência ou exceção em uma série recorrente. Essa propriedade não é retornada para eventos que são instâncias individuais. As informações de data e hora são expressas no formato ISO 8601 e estão sempre em UTC. Por exemplo, meia-noite UTC em 1º de janeiro de 2014 é 01-01-01T00:00:00Z|
|`m365_originalstarttimezone`|String|O fuso horário de início que foi definido quando o evento foi criado. Um valor de tzone://Microsoft/Custom indica que um fuso horário personalizado herdado foi definido no Outlook da área de trabalho.|
|`m365_recurrence`|Cadeia de Caracteres|O padrão de recorrência do evento. Cadeia de caracteres codificada em JSON, máx. 4000 de comprimento.por exemplo{ padrão:{dayOfMonth\":0,daysOfWeek\"\":[\"monday,wednesday,friday\"\"\"\"\"],\"firstDayOfWeek\":\"sunday,index\"\"\":\"first,interval\"\"\":1,month\"\":0,type\"\":\"weekly\"},\"range\":{\"startDate\":\"2017-08-14,endDate\"\"\":\"2018-08-14,\"\"\"\"\" numberOfOccurrences\":0,recurrenceTimeZone\"\":\"Eastern Standard Time,type\"\"\":\"endDate\"}}|
|`m365_reminderminutesbeforestart`|Int32|O número de minutos antes da hora de início do evento em que o alerta de lembrete ocorre.|
|`m365_responserequested`|Booliano|O padrão é true, representando que o organizador gostaria de ter um convidado para enviar uma resposta para o evento.|
|`m365_responsestatus`|Cadeia de Caracteres|Indica o tipo de resposta enviada em resposta a uma mensagem de evento. Cadeia de caracteres codificada em JSON, no máximo 4000 de comprimento. {\"response\": \"String,time\"\"\": \"String (timestamp)\"}|
|`m365_sensitivity`|String|Os valores possíveis são: normal, pessoal, privado, confidencial.|
|`m365_seriesmasterid`|Cadeia de caracteres|A ID do item mestre da série recorrente se este evento for parte de uma série recorrente.|
|`m365_showas`|String|O status a ser exibido. Os valores possíveis são: livre, provisório, ocupado, oof, workingElsewhere, desconhecido.|
|`m365_subject`|String|O texto da linha de assunto do evento. Coluna de pesquisa primária|
|`m365_transactionid`|String|Um identificador personalizado especificado por um aplicativo cliente para o servidor para evitar operações POST redundantes se o cliente tentar criar o mesmo evento novamente. Isso é útil quando a conectividade de rede baixa faz com que o cliente expire antes de receber uma resposta do servidor para a solicitação anterior de criação de evento do cliente. Depois de definir `transactionId` ao criar um evento, você não pode alterar transactionId em uma atualização subsequente. Essa propriedade só será retornada em um conteúdo de resposta se um aplicativo a tiver definido. Opcional.|
|`m365_type`|String|O tipo de evento. Os valores possíveis são: singleInstance, occurrence, exception, seriesMaster. Somente leitura|
|`m365_weblink`|String|A URL para abrir o evento no Outlook na Web. Outlook na Web abrirá o evento no navegador se você estiver conectado à sua caixa de correio. Caso contrário, o Outlook na Web solicitará que você entre. Essa URL não pode ser acessada de dentro de um iFrame.|
|`m365_grapheventid`|Guid|Identificador exclusivo do evento de grafo.|
|`m365_groupid`|Cadeia de Caracteres|ID do grupo à qual o evento pertence.|

## <a name="graph-booking-appointment"></a>Compromisso de reserva do Graph

* Nome da entidade: m365_graphbookingappointment
* Recurso do Graph: [tipo de recurso bookingAppointment](/graph/api/resources/bookingappointment)
* Não há suporte para classificação.
* Há suporte para filtragem nas seguintes colunas:
  * m365_bookingbusinessID
  * m365_collaborationrootID
  * m365_customertimezone
  * m365_optoutofcustomeremail
  * m365_price
  * m365_pricetype
  * m365_serviceID
  * m365_servicename
* Não há suporte para paginação.

### <a name="attributes-for-graph-booking-appointment"></a>Atributos para compromisso de reserva do Graph

| Coluna  | Tipo de Dataverse | Detalhes |
|---|---|---|
| `m365_collaborationrootid`| String| ID raiz de colaboração da sessão de colaboração à qual o registro está associado. Se o registro estiver associado a várias sessões de colaboração, isso será retornado como uma cadeia de caracteres delimitada por vírgula. Observe que esse atributo não será retornado ao recuperar vários registros.|
| `m365_graphbookingappointmentid` | Guid | Identificador exclusivo do compromisso de reserva de grafo.|
| `m365_bookingbusinessid` | String | O Identificador exclusivo do negócio de reserva no qual o compromisso está agendado.|
| `m365_additionalinformation` | Cadeia de Caracteres | Informações adicionais que são enviadas ao cliente quando um compromisso é confirmado.|
| `m365_customers` | String| Ele lista as propriedades do cliente para um compromisso. O compromisso conterá uma lista de informações do cliente e cada unidade indicará as propriedades de um cliente que faz parte desse compromisso. Optional[{\"customerID\":\"d243c77b-f1ff-4615-a01f-1660b5cb0e79,customQuestionAnswers\"\"\":[],\"emailAddress\":\"jordanm@contoso.com,location\"\"\":{\"address\":{\"city\":\"\",\"countryOrRegion\":,\"postalCode\":\"\"\"\",\"postOfficeBox,state\"\"\":\"\",\"street\":\"\",\"type\" },\"coordinates\":{\" accuracy,altitude,altitudeAccuracy,latitude,longitude\"\"\"\"\"\"\"\"\" },\"displayName\":\"\",\"locationEmailAddress,locationType,locationUri\"\"\"\"\":\"\",\"uniqueID,uniqueIDType\"\"\" },\"name\":\"Jordan Miller,notes,phone,timeZone\"\"\"\"\"\"\",\"@odata.type:\"\" #microsoft.graph.bookingCustomerInformation\"}] |
| `m365_customertimezone` | Cadeia de Caracteres | O fuso horário do cliente. Para obter uma lista de valores possíveis, consulte [o tipo de recurso dateTimeTimeZone](/graph/api/resources/datetimetimezone). |
| `m365_duration` | Cadeia de Caracteres | O comprimento do compromisso, indicado no formato ISO8601.|
| `m365_enddatetime` | DateTime | A data, a hora e o fuso horário em que o compromisso termina.|
| `m365_filledattendeescount` | Int32 | O número atual de clientes no compromisso.|
| `m365_id` | String | A ID do bookingAppointment. Somente leitura.|
| `m365_islocationonline` | Booliano | True indica que o compromisso será mantido online. O valor padrão é falso.|
| `m365_joinweburl` | Cadeia de Caracteres | A URL da reunião online para o compromisso.|
| `m365_maximumattendeescount` | Int32 | O número máximo de clientes permitidos em um compromisso.|
| `m365_optoutofcustomeremail` | Booliano | True indica que o bookingCustomer para este compromisso não deseja receber uma confirmação para este compromisso.|
| `m365_postbuffer` | Cadeia de Caracteres | A quantidade de tempo a ser reservado após o término do compromisso, para limpeza, como exemplo. O valor é expresso no formato ISO8601.|
| `m365_prebuffer` | String | A quantidade de tempo a ser reservado antes do início do compromisso, para preparação, como exemplo. O valor é expresso no formato ISO8601.|
| `m365_price` | DecimalType | O preço normal de um compromisso para o bookingService especificado.|
| `m365_pricetype` | String | Uma configuração para fornecer flexibilidade para a estrutura de preços dos serviços. Os valores possíveis são: undefined, fixedPrice, startingAt, hourly, free, priceVaries, callUs, notSet.|
| `m365_reminders` | String | A coleção de lembretes de clientes enviados para este compromisso. O valor dessa propriedade está disponível somente ao ler este bookingAppointment pela ID. [{\"message\":\"We look forward to seeing you!\",\"offset\":\"P1D,recipients\"\"\":\"customer\"},{\"message\":\"Reminder that you have an appointment!\",\"offset\":\"P1D,recipients\"\"\":\"staff\"}] |
| `m365_selfserviceappointmentid` | Cadeia de Caracteres | Outra ID de acompanhamento para o compromisso, se o compromisso tiver sido criado diretamente pelo cliente na página de agendamento, em vez de um membro da equipe em nome do cliente.|
| `m365_serviceid` | Cadeia de Caracteres | A ID do bookingService associado a este compromisso.|
| `m365_servicelocation` | String | O local onde o serviço é entregue. {\"address\":{\"city\":\"\",\"countryOrRegion\":\"\",\"postalCode\":\"\",\"postOfficeBox,state\"\"\":,\"street\":\"\"\"\",type\" },\"\"coordinates\":{\"accuracy,altitude,altitudeAccuracy,latitude,longitude\"\"\"\"\"\"\"\"\" },\"displayName\":\"Our office address,locationEmailAddress\"\" \",\"locationType,locationUri\"\"\":\"\",\"uniqueID,uniqueIDType\"\"\" } |
| `m365_servicename` | String | O nome do bookingService associado a este compromisso. Essa propriedade é opcional ao criar um novo compromisso. Se não for especificado, ele será calculado do serviço associado ao compromisso pela propriedade serviceID. |
| `m365_servicenotes` |Cadeia de Caracteres | Anotações de um bookingStaffMember. O valor dessa propriedade está disponível somente ao ler este bookingAppointment por sua ID.|
| `m365_smsnotificationsenabled` | Booliano | True indica que as notificações por SMS serão enviadas aos clientes para o compromisso. O valor padrão é falso.|
| `m365_staffmemberids` | Cadeia de Caracteres | A ID de cada bookingStaffMember agendado neste compromisso. Armazenado como uma cadeia de caracteres separada por vírgulas. [\"string\"] |
| `m365_startdatetime` | DateTime | A data, a hora e o fuso horário em que o compromisso começa.|

## <a name="graph-drive"></a>Unidade do Graph

* Nome da entidade: m365_graphdrive
* Recurso do Graph: [tipo de recurso de unidade](/graph/api/resources/drive)
* Não há suporte para classificação.
* Não há suporte para filtragem.
* Há suporte para paginação controlada por servidor.

### <a name="attributes-for-graph-drive"></a>Atributos para a unidade do Graph

|Coluna |Tipo de Dataverse |Detalhes |
|---|---|---|
|`m365_collaborationrootid` |String | ID raiz de colaboração da sessão de colaboração à qual o registro está associado. Se o registro estiver associado a várias sessões de colaboração, isso será retornado como uma cadeia de caracteres delimitada por vírgula. Observe que esse atributo não será retornado ao recuperar vários registros. |
|`m365_createdby` |Cadeia de Caracteres |Identidade do usuário, dispositivo ou aplicativo que criou o item. Somente leitura. Esse atributo é uma cadeia de caracteres codificada em JSON, por exemplo { "user": { "displayName": "System Account" } } |
|`m365_createddatetime` |DateTime |Data e hora de criação do item. Somente leitura. |
|`m365_description` |String |Fornecer uma descrição visível para os usuários da unidade. Somente leitura. |
|`m365_drivetype` |String |Descreve o tipo de unidade representado por esse recurso. As unidades pessoais do OneDrive retornarão pessoal. OneDrive for Business retornará os negócios. As bibliotecas de documentos do SharePoint retornarão documentLibrary. Somente leitura. |
|`m365_graphdriveid` |Guid |Identificador exclusivo da unidade de grafo. |
|`m365_id` |Cadeia de Caracteres |O Identificador exclusivo da unidade. Somente leitura. |
|`m365_lastmodifiedby` | Cadeia de Caracteres |Identidade do usuário, dispositivo e aplicativo, que modificou o item pela última vez. Somente leitura. Esse atributo é uma cadeia de caracteres codificada em JSON, por exemplo { "user": { "email": "user@contoso.com", "ID": "61de164e-21ff-4b1c-8cbd-77ac440894f8", "displayName": "User Name" } } } |
|`m365_lastmodifieddatetime` |DateTime |Data e hora em que o item foi modificado pela última vez. Somente leitura.|
|`m365_name` |Cadeia de Caracteres |O nome do item. Somente leitura. |
|`m365_owner` |String |Opcional. A conta do usuário que é proprietário da unidade. Somente leitura. Esse atributo é uma cadeia de caracteres codificada em JSON. Por exemplo { "group": { "ID": "76c7286f-8645-4ba8-bc0f-c65a16424aaa", "displayName": "Nome do Grupo" }} |
|`m365_quota` |String |Opcional. Informações sobre a cota de espaço de armazenamento da unidade. Somente leitura. Esse atributo é uma cadeia de caracteres codificada em JSON. Por exemplo { "excluído": 482586, "restante": 27487788645969, "estado": "normal", "total": 27487790694400, "usado": 1565845 } |
|`m365_sharepointids` |String |Retorna identificadores úteis para compatibilidade rest do SharePoint. Somente leitura. Essa propriedade não é retornada por padrão e deve ser selecionada usando o parâmetro $select consulta. Esse atributo é uma cadeia de caracteres codificada em JSON. Por exemplo , "sharePointIDs": { "listID": "29d8457a-8e26-4291-9901-09718a388aaa", "siteID": "93618739-b3ca-4107-a77c-fba278c48aaa", "siteUrl": "<https://contoso.sharepoint.com>", "tenantID": "53986071-de92-43ad-a41f-f3c4adb2beef", "webID": "a0d0e9ec-e547-4338-92d9-4c2c62e5beef" } |
| `m365_siteid` |String |O Identificador do site que contém a biblioteca de documentos.
|`m365_system` |Cadeia de Caracteres |Se estiver presente, indica que se trata de uma unidade gerenciada pelo sistema. Somente leitura.
|`m365_weburl` |String |URL que exibe o recurso no navegador. Somente leitura.

### <a name="graph-drive-item"></a>Item de Unidade de Grafo

* Nome da entidade: m365_graphdriveitem
* Recurso do Graph: [tipo de recurso driveItem](/graph/api/resources/driveitem)
* Há suporte para a classificação na seguinte coluna:
  * m365_name
* Há suporte para filtragem na seguinte coluna:
  * m365_name
* Há suporte para paginação controlada por servidor.

### <a name="attributes-for-graph-drive-item"></a>Atributos para o item de unidade do Graph

|Coluna |Tipo de Dataverse |Detalhes |
|---|---|---|
|`m365_audio` |String |Metadados de áudio, se o item for um arquivo de áudio. Somente leitura. Somente no OneDrive Personal. Esse atributo é uma cadeia de caracteres codificada em JSON. { "album": "string", "albumArtist": "string", artist": "string", bitrate": 128, "composers": "string", copyright": "string", "disc": 0, "discCount": 0, "duration": 567, "genre": "string", "hasDrm": false, "isVariableBitrate": false, "title": "string", "track": 1, "trackCount": 16, "year": 2014 }|
|`M365_bundle` |Cadeia de Caracteres |Agrupar os metadados, se o item for um pacote. Somente leitura. Esse atributo é uma cadeia de caracteres codificada em JSON. Por exemplo, { "childCount": 3, "album": { "@odata.type": "microsoft.graph.album" }, } |
|`m365_collaborationrootid` |String |ID raiz de colaboração da sessão de colaboração à qual o registro está associado. Se o registro estiver associado a várias sessões de colaboração, isso será retornado como uma cadeia de caracteres delimitada por vírgula. Observe que esse atributo não será retornado ao recuperar vários registros. |
|`m365_copy` |Cadeia de Caracteres |Se estiver presente na solicitação, uma operação de cópia será executada. |
|`m365_createdby` |String |Identidade do usuário, dispositivo e aplicativo, que criou o item. Somente leitura. Esse atributo é uma cadeia de caracteres codificada em JSON. Por exemplo, {"user":{"displayName":"Nome de Usuário","email":"alias@contoso.com","ID":"a298b975-3493-4d9e-b2d4-3cad78f00000"},"group": null,"application","device" } |
|`m365_createddatetime` |DateTime |Data e hora de criação do item. Somente leitura. |
|`m365_ctag` |String |Uma eTag para o conteúdo do item. Essa eTag não será alterada se apenas os metadados são alterados. Observação. Essa propriedade não será retornada se o item for uma pasta. Somente leitura. |
|`m365_deleted` |Cadeia de Caracteres |Informações sobre o estado excluído do item. Somente leitura. Esse atributo é uma cadeia de caracteres codificada em JSON. Por exemplo, { "state": "string" } |
|`m365_description` |String |Fornece uma descrição visível ao usuário do item. Leitura/gravação. Somente no OneDrive Personal. |
|`m365_driveid` |Cadeia de Caracteres |O Identificador da unidade que contém o item de unidade.|
|`m365_etag` |String |eTag para o item inteiro (metadados + conteúdo). Somente leitura. |
| `m365_file` |Cadeia de Caracteres |Metadados de arquivo, se o item for um arquivo. Somente leitura. Esse atributo é uma cadeia de caracteres codificada em JSON. Por exemplo, {"hashes":{"crc32Hash","quickXorHash":"Biuzvwdu+Tmu6yRefayD27hD9vD=","sha1Hash","sha256Hash" },"mimeType":"application/vnd.openxmlformats-officedocument.wordprocessingml.document","processingMetadata" } |
| `m365_filesysteminfo` |String |Informações do sistema de arquivos no cliente. Esse atributo é uma cadeia de caracteres codificada em JSON. Por exemplo, {"createdDateTime":"2022-07-21T15:02:47+00:00","lastAccessedDateTime","lastModifiedDateTime":"2022-07-21T15:02:55+00:00"} |
|`m365_folder` |Cadeia de Caracteres | Metadados de pasta, se o item for uma pasta. Somente leitura. Esse atributo é uma cadeia de caracteres codificada em JSON. Por exemplo, {"childCount":0,"view" } |
|`m365_graphdriveitemid` |Guid |Identificador exclusivo do item de unidade de grafo. |
|`m365_id` |String |O identificador exclusivo do item dentro da unidade. Somente leitura. |
|`m365_image` |String |Metadados de imagem, se o item for uma imagem. Somente leitura. Esse atributo é uma cadeia de caracteres codificada em JSON. Por exemplo, {"height","width" } |
|`m365_lastmodifiedby` |String |Identidade do usuário, dispositivo e aplicativo, que modificou o item pela última vez. Somente leitura. Esse atributo é uma cadeia de caracteres codificada em JSON. Por exemplo, {"user":{"displayName":"Nome de Usuário","email":"alias@contoso.com","ID":"a298b975-3493-4d9e-b2d4-3cad78f9a00e"},"group","application","device" } |
|`m365_lastmodifieddatetime` |DateTime |Data e hora em que o item foi modificado pela última vez. Somente leitura. |
|`m365_location` |String |Metadados de localização, se o item tiver dados de localização. Somente leitura. Esse atributo é uma cadeia de caracteres codificada em JSON. Por exemplo, "location": { "altitude": 1,0, "latitude": 1,0, "longitude": 1,0 } |
|`m365_malware` |String |Metadados de malware, se o item for detectado como contendo malware. Somente leitura. Esse atributo é uma cadeia de caracteres codificada em JSON. Por exemplo, { "description": "string" } |
|`m365_name` |String |O nome do item (nome do arquivo e extensão). Leitura e gravação. |
|`m365_package` |Cadeia de Caracteres |Se presente, indica que esse item é um pacote, e não uma pasta ou um arquivo. Pacotes são tratados como arquivos em alguns contextos e como pastas em outros. Somente leitura. Esse atributo é uma cadeia de caracteres codificada em JSON. Por exemplo, { "type": "oneNote" } |
|`m365_parentreference` |String |Informações do pai, se o item tiver um pai. Esse atributo é uma cadeia de caracteres codificada em JSON. Por exemplo, {"driveID":"b!qgK-8nOzX0qISvfGCiC2Smbv0m0RlNhDvNQDZsCMpbSnchFAhWAaQoiTLZcSo1gq","driveType":"documentLibrary","". ID":"01EYDCV4YHV77FE3EDDFHIVD6WJ2ETT3PP","name","path":"/drives/b!qgK-8nOzX0qISvfGCiC2Smbv0m0RlNhDvNQDZsCMpbSnchFAhWAaQoiTLZcSo1no/root: /folder name","shareID","sharepointIDs":{"listID":"401172a8-6085-421a-8893-2d9712a35c3c","listItemID","listItemUniqueID":"52feaf12-836c-4e19-8a8f-d64e8939ee52","siteID":" f34e02aa-b373-4a5f-884a-f7c60a20b64a","siteUrl":"",https://contoso.sharepoint.com/sites/Contoso"tenantID","webID":"6dd2ef66-9411-43d8-bcd4-0366c08ccabd"},"siteID" } |
|`m365_parentreferenceid` |String |O Identificador do item de unidade que é o pai do item de unidade. |
|`m365_pendingoperations` |Cadeia de Caracteres |Se houver, indica que uma ou mais operações que podem afetar o estado da driveItem estão pendentes. Somente leitura. Esse atributo é uma cadeia de caracteres codificada em JSON. Por exemplo, { "pendingContentUpdate": {"@odata.type": "microsoft.graph.pendingContentUpdate"} } |
|`m365_photo` |String |Metadados de foto, se o item for uma foto. Somente leitura. Esse atributo é uma cadeia de caracteres codificada em JSON. Por exemplo, { "cameraMake": "Camera Make", "cameraModel": "Camera Model", "exposureDenominator": 1000000, "exposureNumerator": 41671, "focalLength": 4.38, "fNumber": 1.73, "iso": 70, "orientation": 6, "takenDateTime": "2020-04-29T14:17:39Z" } |
|`m365_publication` |Cadeia de Caracteres |Fornece informações sobre o estado de publicação ou de check-out de um item, nos locais que oferecem suporte a essas ações. Essa propriedade não é retornada por padrão. Somente leitura. Esse atributo é uma cadeia de caracteres codificada em JSON. Por exemplo, {"level":"published","versionID":"2.0"} |
|`m365_remoteitem` |String |Dados do item remoto, se o item for compartilhado de uma unidade diferente daquela que está sendo acessada. Somente leitura. Esse atributo é uma cadeia de caracteres codificada em JSON. Por exemplo, { "ID": "string", "createdBy": { "@odata.type": "microsoft.graph.IdentitySet" }, "createdDateTime": "timestamp", "file": { "@odata.type": "microsoft.graph.file" }, "fileSystemInfo": { "@odata.type": "microsoft.graph.fileSystemInfo" }, }, "folder": { "@odata.type": "microsoft.graph.folder" }, "image": { "@odata.type": "microsoft.graph.image" }, "lastModifiedBy": { "@odata.type": "microsoft.graph.IdentitySet" }, "lastModifiedDateTime": "timestamp", "name": "string", "package": { " @odata.type": "microsoft.graph.package" }, "parentReference": { "@odata.type": "microsoft.graph.itemReference" }, "shared": { "@odata.type": "microsoft.graph.shared" }, "sharepointIDs": { "@odata.type": "microsoft.graph.sharepointIDs" }, "specialFolder": { "@odata.type": "microsoft.graph.specialFolder" }, "size": 1024, "video": { "@odata.type": "microsoft.graph.video" }, "webDavUrl": "url", "webUrl": "url" } |
|`m365_root` |String |Se essa propriedade for não nula, indicará que o driveItem é o principal driveItem na unidade. |
|`m365_searchresult` |String |Metadados de pesquisa, se o item for de um resultado de pesquisa. Somente leitura. Esse atributo é uma cadeia de caracteres codificada em JSON. Por exemplo, { "onClickTelemetryUrl": "url" } |
|`m365_shared` |String |Indica que o item foi compartilhado com outras pessoas e fornece informações sobre o estado compartilhado desse item. Somente leitura. Esse atributo é uma cadeia de caracteres codificada em JSON. Por exemplo, { "scope": "users", "owner": { "user": { "displayName": "User Name", "ID": "bbbb6fa48aaaaaaa" } } } } |
|`m365_sharepointids` |String |Retorna identificadores úteis para compatibilidade rest do SharePoint. Somente leitura. Esse atributo é uma cadeia de caracteres codificada em JSON. por exemplo{ "listID":"401172a7-6085-421a-8893-2d9712a35aba","listItemID":"338",,"listItemUniqueID":"0edc89e5-24ea-4c6b-a019-dc51f45eeccc","siteID":"f2be02aa-b373-4a5f-884a-f7c60a20bddd","siteUrl":""https://contoso.sharepoint.com/sites/Contoso,"tenantID":"1c137272-0581-487f-b195-aeeb93cc4ccc","webID":"6dd2ef66-9411-43d8-bcd4-0366c08caaaa"} |
|`m365_siteid` |String |O Identificador do site que contém a biblioteca de documentos. |
|`m365_size` |IntType |O tamanho do item em bytes. Somente leitura. |
|`m365_specialfolder` |String |Se o item atual também estiver disponível como uma pasta especial, essa faceta será retornada. Somente leitura. Esse atributo é uma cadeia de caracteres codificada em JSON. Por exemplo, { "name": "documents" } |
|`m365_thumbnail` |String |Se estiver presente na solicitação, as miniaturas do item de unidade serão recuperadas. |
|`m365_video` |Cadeia de Caracteres |Se o item atual também estiver disponível como uma pasta especial, essa faceta será retornada. Somente leitura. Esse atributo é uma cadeia de caracteres codificada em JSON. Por exemplo, {"taxa de bits": 10646968, "duration": 1050683, "height": 720, "width": 1280, "audioBitsPerSample": 16, "audioChannels": 1, "audioFormat": "PCM", "audioSamplesPerSecond": 32000, "fourCC": "H264", "frameRate": 60} |
|`m365_webdavurl` |String | URL compatível com WebDAV para o item. |
|`m365_weburl` |String |URL que exibe o recurso no navegador. Somente leitura. |
