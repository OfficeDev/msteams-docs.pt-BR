---
title: Referências à API de aplicativos de reunião
author: surbhigupta
description: Identificar as referências da API de aplicativos de reunião com exemplos e exemplos de código
ms.topic: conceptual
ms.author: lajanuar
ms.localizationpriority: medium
keywords: consulta de sinal de notificação do usuário de função de usuário de reuniões de aplicativos do teams
ms.openlocfilehash: 251f8bbd65bf8ba563f09302b16bf7285a5c4267
ms.sourcegitcommit: 85d0584877db21e2d3e49d3ee940d22675617582
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/29/2021
ms.locfileid: "61216066"
---
# <a name="meeting-apps-api-references"></a>Referências à API de aplicativos de reunião

As extensibilidades de reunião fornecem APIs para transformar a experiência de reunião:

* Crie aplicativos ou integre aplicativos existentes ao ciclo de vida da reunião.
* Use as APIs para tornar seu aplicativo ciente da reunião.
* Selecione as APIs que você deseja usar para aprimorar a experiência de reunião.

A tabela a seguir fornece uma lista de APIs:

|API|Descrição|Solicitação|Origem|
|---|---|----|---|
|**GetUserContext**| Permite que você receba informações contextuais para exibir conteúdo relevante em uma Teams guia. |_**microsoftTeams.getContext( ( ) => { /*...* / } )**_|Microsoft Teams SDK do cliente|
|**GetParticipant**| Permite que um bot busque informações do participante por meio da ID da reunião e da ID do participante. |**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_ |Microsoft Bot Framework SDK|
|**NotificationSignal** | Permite que você forneça sinais de reunião que são entregues usando a API de notificação de conversa existente para chat usuário-bot. Ele permite sinalizar com base na ação do usuário que mostra uma caixa de diálogo na reunião. |**POST** _**/v3/conversations/{conversationId}/activities**_|Microsoft Bot Framework SDK|
|**Detalhes da reunião** | Permite que você receba metadados de reunião estáticos. |**GET** _**/v1/meetings/{meetingId}**_| Bot SDK |
|**shareAppContentToStage**| Permite compartilhar partes específicas do aplicativo para o estágio de reunião do painel lateral do aplicativo em uma reunião. |_**microsoftTeams.meeting.shareAppContentToStage((err, result) => {} , appContentUrl)**_|Microsoft Teams SDK do cliente|
|**getAppContentStageSharingState**| Permite que você busque informações sobre o estado de compartilhamento de aplicativos no estágio da reunião. |_**microsoftTeams.meeting.getAppContentStageSharingState((err, result)) => {}**_|Microsoft Teams SDK do cliente|
|**getAppContentStageSharingCapabilities**| Permite que você busque os recursos dos aplicativos para compartilhamento no estágio de reunião. |_**microsoftTeams.meeting.getAppContentStageSharingCapabilities((err, result)) => {}**_|Microsoft Teams SDK do cliente|

A tabela a seguir fornece os métodos SDK da Estrutura de Bot para as APIs:

|API|Método SDK da Estrutura de Bot|
|---|---|
|**GetParticipant**| `GetMeetingParticipantAsync (Microsoft.Bot.Builder.ITurnContext turnContext, string meetingId = default, string participantId = default, string tenantId = default, System.Threading.CancellationToken cancellationToken = default);` |
|**NotificationSignal** | `activity.TeamsNotifyUser(true, "https://teams.microsoft.com/l/bubble/APP_ID?url=&height=&width=&title=<title>&completionBotId=BOT_APP_ID");` |
|**Detalhes da reunião** | `TeamsMeetingInfo (string id = default);` |

## <a name="getusercontext-api"></a>GetUserContext API

Para identificar e recuperar informações contextuais para o conteúdo da guia, consulte obter contexto para sua guia [Teams](../tabs/how-to/access-teams-context.md#get-context-by-using-the-microsoft-teams-javascript-library). é usado por uma guia ao ser executado no contexto da reunião e é adicionado para a carga de `meetingId` resposta.

## <a name="getparticipant-api"></a>GetParticipant API

> [!NOTE]
> * Não armazenar em cache as funções do participante, pois o organizador da reunião pode alterar as funções a qualquer momento.
> * Teams atualmente não suporta listas de distribuição grandes ou tamanhos de lista de mais de 350 participantes para o `GetParticipant` API.

A `GetParticipant` API permite que um bot busque informações do participante por meio da ID da reunião e da ID do participante. A API inclui parâmetros de consulta, exemplos e códigos de resposta.

### <a name="query-parameters"></a>Parâmetros de consulta

A `GetParticipant` API inclui os seguintes parâmetros de consulta:

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**meetingId**| Cadeia de Caracteres | Sim | O identificador de reunião está disponível por meio de Bot Invoke e Teams Client SDK.|
|**participantId**| Cadeia de Caracteres | Sim | A ID do participante é a ID do usuário. Ele está disponível em Tab SSO, Bot Invoke e Teams Client SDK. É recomendável obter uma ID de participante do SSO da guia. |
|**tenantId**| Cadeia de caracteres | Sim | A ID do locatário é necessária para os usuários do locatário. Ele está disponível em Tab SSO, Bot Invoke e Teams Client SDK. É recomendável obter uma ID de locatário do SSO de tabulação. | 

### <a name="example"></a>Exemplo

A `GetParticipant` API inclui os seguintes exemplos:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  TeamsMeetingParticipant participant = await TeamsInfo.GetMeetingParticipantAsync(turnContext, "yourMeetingId", "yourParticipantId", "yourParticipantTenantId").ConfigureAwait(false);
  TeamsChannelAccount member = participant.User;
  MeetingParticipantInfo meetingInfo = participant.Meeting;
  ConversationAccount conversation = participant.Conversation;

  await turnContext.SendActivityAsync(MessageFactory.Text($"The participant role is: {meetingInfo.Role}"), cancellationToken);
}

```

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```typescript

export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onMessage(async (context, next) => {
            TeamsMeetingParticipant participant = getMeetingParticipant(turnContext, "yourMeetingId", "yourParticipantId", "yourTenantId");
            let member = participant.user;
            let meetingInfo = participant.meeting;
            let conversation = participant.conversation;
            
            await context.sendActivity(`The participant role is: '${meetingInfo.role}'`);
            await next();
        });
    }
}

```

# <a name="json"></a>[JSON](#tab/json)

```http
GET /v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}
```

---

O corpo de resposta JSON para `GetParticipant` API é:

```json
{
   "user":{
      "id":"29:1JKiJGPAX9TTxtGxhVo0wLx_zwzo-gG8Z-X03306vBwi9p-xMTEbDXsT6KH7-0kkTS8cD-2zkrsoV6f5WJ6_aYw",
      "aadObjectId":"e236c4bf-88b1-4f3a-b1d7-8891dfc332b5",
      "name":"Bob Young",
      "givenName":"Bob",
      "surname":"Young",
      "email":"Bob.young@microsoft.com",
      "userPrincipalName":"Bob.young@microsoft.com",
      "tenantId":"2fe477ab-0efc-4dfd-bde2-484374e2c373",
      "userRole":"user"
   },
   "meeting":{
      "role ":"Presenter",
      "inMeeting":true
   },
   "conversation":{
      "id":"<conversation id>",
      "isGroup":true
   }
}
```

### <a name="response-codes"></a>Códigos de resposta

A `GetParticipant` API retorna os seguintes códigos de resposta:

|Código da resposta|Descrição|
|---|---|
| **403** | Obter informações do participante não é compartilhado com o aplicativo. Se o aplicativo não estiver instalado na reunião, ele disparará a resposta de erro mais comum 403. Se o administrador do locatário desabilitar ou bloquear o aplicativo durante a migração do site ao vivo, a resposta de erro 403 será disparada. |
| **200** | As informações do participante são recuperadas com êxito.|
| **401** | O aplicativo responde com um token inválido.|
| **404** | A reunião expirou ou o participante não pode ser encontrado.|

## <a name="notificationsignal-api"></a>NotificationSignal API

Todos os usuários em uma reunião recebem as notificações enviadas por meio da `NotificationSignal` API.

> [!NOTE]
> * Quando uma caixa de diálogo na reunião é invocada, o conteúdo é apresentado como uma mensagem de chat.
> * Atualmente, não há suporte para o envio de notificações direcionadas.

`NotificationSignal` A API permite que você forneça sinais de reunião que são entregues usando a API de notificação de conversa existente para chat usuário-bot. Essa API permite sinalizar com base na ação do usuário que mostra uma caixa de diálogo na reunião. A API inclui parâmetros de consulta, exemplos e códigos de resposta.

### <a name="query-parameter"></a>Parâmetro de consulta

A `NotificationSignal` API inclui o seguinte parâmetro de consulta:

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**conversationId**| String | Sim | O identificador de conversa está disponível como parte de Bot Invoke. |

### <a name="examples"></a>Exemplos

O `Bot ID` é declarado no manifesto e o bot recebe um objeto de resultado.

> [!NOTE]
> * O `completionBotId` parâmetro do é opcional no exemplo de carga `externalResourceUrl` solicitada. `Bot ID` é declarado no manifesto e o bot recebe um objeto de resultado.
> * Os `externalResourceUrl` parâmetros de largura e altura devem estar em pixels. Para garantir que as dimensões estão dentro dos limites permitidos, consulte [diretrizes de design](design/designing-apps-in-meetings.md).
> * A URL é a página carregada como `<iframe>` uma caixa de diálogo na reunião. O domínio deve estar na matriz do aplicativo `validDomains` no manifesto do aplicativo.

A `NotificationSignal` API inclui os seguintes exemplos:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
Activity activity = MessageFactory.Text("This is a meeting signal test");
activity.TeamsNotifyUser(true, "https://teams.microsoft.com/l/bubble/APP_ID?url=<url>&height=<height>&width=<width>&title=<title>&completionBotId=BOT_APP_ID");
await turnContext.SendActivityAsync(activity).ConfigureAwait(false);
```

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```javascript

const replyActivity = MessageFactory.text('Hi'); // this could be an adaptive card instead
replyActivity.channelData = {
    notification: {
        alertInMeeting: true,
        externalResourceUrl: 'https://teams.microsoft.com/l/bubble/APP_ID?url=<url>&height=<height>&width=<width>&title=<title>&completionBotId=BOT_APP_ID’
    }
};
await context.sendActivity(replyActivity);
```

# <a name="json"></a>[JSON](#tab/json)

```http
POST /v3/conversations/{conversationId}/activities

{
    "type": "message",
    "text": "John Phillips assigned you a weekly todo",
    "summary": "Don't forget to meet with Marketing next week",
    "channelData": {
        "notification": {
            "alertInMeeting": true,
            "externalResourceUrl": "https://teams.microsoft.com/l/bubble/APP_ID?url=<url>&height=<height>&width=<width>&title=<title>&completionBotId=BOT_APP_ID"
        }
    },
    "replyToId": "1493070356924"
}
```

---

### <a name="response-codes"></a>Códigos de resposta

A `NotificationSignal` API inclui os seguintes códigos de resposta:

|Código da resposta|Descrição|
|---|---|
| **201** | A atividade com sinal é enviada com êxito. |
| **401** | O aplicativo responde com um token inválido. |
| **403** | O aplicativo não consegue enviar o sinal. O código de resposta 403 pode ocorrer por vários motivos, como o administrador do locatário desabilita e bloqueia o aplicativo durante a migração do site ao vivo. Nesse caso, a carga contém uma mensagem de erro detalhada. |
| **404** | O chat de reunião não existe. |

## <a name="meeting-details-api"></a>API de Detalhes da Reunião

> [!NOTE]
> Esse recurso está disponível apenas na [visualização de desenvolvedor](../resources/dev-preview/developer-preview-intro.md) público.

A API Detalhes da Reunião permite que seu aplicativo receba metadados de reunião estáticos. Os metadados fornece pontos de dados que não mudam dinamicamente.
A API está disponível por meio dos Serviços bot.

### <a name="prerequisite"></a>Pré-requisito

Para usar a API de Detalhes da Reunião, você deve obter permissões RSC. Use o exemplo a seguir para configurar a propriedade do manifesto do `webApplicationInfo` aplicativo:

```json
"webApplicationInfo": {
    "id": "<bot id>",
    "resource": "https://RscPermission",
    "applicationPermissions": [
      "OnlineMeeting.ReadBasic.Chat"
    ]
}
 ```
 
### <a name="query-parameter"></a>Parâmetro de consulta

A API De Detalhes da Reunião inclui o seguinte parâmetro de consulta:

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**meetingId**| Cadeia de Caracteres | Sim | O identificador de reunião está disponível por meio de Bot Invoke e Teams Client SDK. |

### <a name="example"></a>Exemplo

A API De Detalhes da Reunião inclui os seguintes exemplos:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
MeetingInfo result = await TeamsInfo.GetMeetingInfoAsync(turnContext);
await turnContext.SendActivityAsync(JsonConvert.SerializeObject(result));
```

# <a name="javascript"></a>[JavaScript](#tab/javascript)

Não disponível

# <a name="json"></a>[JSON](#tab/json)

```http
GET /v1/meetings/{meetingId}
```

---

O corpo da resposta JSON para a API de Detalhes da Reunião é o seguinte:

```json
{ 
   "details": { 
        "id": "meeting ID", 
        "msGraphResourceId": "", 
        "scheduledStartTime": "2020-08-21T02:30:00+00:00", 
        "scheduledEndTime": "2020-08-21T03:00:00+00:00", 
        "joinUrl": "https://teams.microsoft.com/l/xx", 
        "title": "All Hands", 
        "type": "Scheduled" 
    }, 
    "conversation": { 
            "isGroup": true, 
            “conversationType”: “groupchat”, 
            "id": "meeting chat ID" 
    }, 
    "organizer": { 
        "id": "<organizer user ID>", 
        "aadObjectId": "<AAD ID>", 
        "tenantId": "<Tenant ID>" 
    }
} 
```

## <a name="shareappcontenttostage-api"></a>API shareAppContentToStage

A `shareAppContentToStage` API permite que você compartilhe partes específicas do seu aplicativo para o estágio de reunião. A API está disponível por meio do SDK Teams cliente.

### <a name="prerequisite"></a>Pré-requisito

Para usar a `shareAppContentToStage` API, você deve obter as permissões RSC. No manifesto do aplicativo, configure `authorization` a propriedade e o e no `name` `type` `resourceSpecific` campo. Por exemplo:

```json
"authorization": {
    "permission": { 
    "resourceSpecific": [
      { 
      "name": "MeetingStage.Write.Chat",
      "type": "Delegated"
      }
    ]
   }
}
 ```

### <a name="query-parameter"></a>Parâmetro de consulta

A `shareAppContentToStage` API inclui os seguintes parâmetros:

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**callback**| Cadeia de Caracteres | Sim | O retorno de chamada contém dois parâmetros, erro e resultado. O *erro* pode conter um erro do tipo *SdkError*, no caso de um erro ou nulo quando o compartilhamento é bem-sucedido. O *resultado* pode conter um valor verdadeiro, no caso de um compartilhamento bem-sucedido ou nulo quando o compartilhamento falhar.|
|**appContentURL**| Cadeia de Caracteres | Sim | URL que será compartilhada no estágio.|

### <a name="example"></a>Exemplo

Os códigos a seguir fornecem exemplos de `shareAppContentToStage` API:

# <a name="c"></a>[C#](#tab/dotnet)

Não disponível

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```typescript

const appContentUrl = "https://www.bing.com/";

microsoftTeams.meeting.shareAppContentToStage ((err, result) => {
if(result) {
  this.setState({ isAppSharing: true });
 }
if(err) {
  this.setState({ sharingError: err, isAppSharing: false })
 }
}, appContentUrl); 

```

# <a name="json"></a>[JSON](#tab/json)

Não disponível

---

### <a name="response-codes"></a>Códigos de resposta

A `shareAppContentToStage` API retorna os seguintes códigos de resposta:

|Código da resposta|Descrição|
|---|---|
| **500** | Erro interno. |
| **501** | A API não tem suporte no contexto atual.|
| **1000** | O aplicativo não tem permissões adequadas para permitir o compartilhamento em estágios.|

## <a name="getappcontentstagesharingstate-api"></a>API getAppContentStageSharingState

A API permite que você busque informações sobre o `getAppContentStageSharingState` compartilhamento de aplicativos no estágio de reunião.

### <a name="query-parameter"></a>Parâmetro de consulta

A `getAppContentStageSharingState` API inclui o seguinte parâmetro:

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**callback**| Cadeia de Caracteres | Sim | O retorno de chamada contém dois parâmetros, erro e resultado. O *erro* pode conter um erro do tipo *SdkError*, no caso de um erro ou nulo quando o compartilhamento é bem-sucedido. O *resultado* pode conter um objeto, indicando recuperação bem-sucedida ou nulo, indicando recuperação `AppContentStageSharingState` com falha.|

### <a name="example"></a>Exemplo

Os códigos a seguir fornecem exemplos de `getAppContentStageSharingState` API:

# <a name="c"></a>[C#](#tab/dotnet)

Não disponível

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```microsoftTeams.meeting.getAppContentStageSharingState((err, result)) => {
  if(result.isAppSharing) {
    this.setState({ isGameSessionOver: false });
   }
  });
``` 

# <a name="json"></a>[JSON](#tab/json)

Não disponível

---

O corpo da resposta JSON para a `getAppContentStageSharingState` API é:

```json
{
   "isAppSharing":true
  }
  
```


### <a name="response-codes"></a>Códigos de resposta

A `getAppContentStageSharingState` API retorna os seguintes códigos de resposta:

|Código da resposta|Descrição|
|---|---|
| **500** | Erro interno. |
| **501** | A API não tem suporte no contexto atual.|
| **1000** | O aplicativo não tem permissões adequadas para permitir o compartilhamento em estágios.|

## <a name="getappcontentstagesharingcapabilities-api"></a>API getAppContentStageSharingCapabilities

A `getAppContentStageSharingCapabilities` API permite que você busque os recursos dos aplicativos para compartilhamento no estágio de reunião.

### <a name="query-parameter"></a>Parâmetro de consulta

O `getAppContentStageSharingCapabilities` inclui os seguintes parâmetros:

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**callback**| Cadeia de Caracteres | Sim | O retorno de chamada contém dois parâmetros, erro e resultado. O *erro* pode conter um erro do tipo *SdkError*, no caso de um erro ou nulo quando o compartilhamento é bem-sucedido. O resultado pode conter um objeto, indicando recuperação bem-sucedida ou nulo, indicando recuperação `AppContentStageSharingState` com falha.|

### <a name="example"></a>Exemplo

Os códigos a seguir fornecem exemplos de `getAppContentStageSharingCapabilities` API:

# <a name="c"></a>[C#](#tab/dotnet)

Não disponível

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```microsoftTeams.meeting.getAppContentStageSharingCapabilities((err, result)) => {
  if(result.doesAppHaveSharePermission) {
    this.setState({ isAppAllowedToShare: true });
   }
  });
``` 

# <a name="json"></a>[JSON](#tab/json)

Não disponível

---

O corpo de resposta JSON para `getAppContentStageSharingCapabilities` API é:

```json
{
   "doesAppHaveSharePermission":true
  }
  
```

### <a name="response-codes"></a>Códigos de resposta

A `getAppContentStageSharingCapabilities` API retorna os seguintes códigos de resposta:

|Código da resposta|Descrição|
|---|---|
| **500** | Erro interno. |
| **1000** | O aplicativo não tem permissões para permitir o compartilhamento em estágios.|

## <a name="real-time-teams-meeting-events"></a>Eventos de reunião Teams em tempo real

O usuário pode receber eventos de reunião em tempo real. Assim que qualquer aplicativo é associado a uma reunião, o início e a hora de término reais da reunião são compartilhados com o bot.

A hora real de início e término de uma reunião é diferente da hora de início e término agendada. A API De Detalhes da Reunião fornece a hora de início e término agendada. O evento fornece a hora real de início e término.

### <a name="prerequisite"></a>Pré-requisito

O manifesto do aplicativo deve ter a `webApplicationInfo` propriedade para receber os eventos de início e término da reunião. Use o exemplo a seguir para configurar seu manifesto:

```json
"webApplicationInfo": {
    "id": "<bot id>",
    "resource": "https://RscPermission",
    "applicationPermissions": [
      "OnlineMeeting.ReadBasic.Chat"
    ]
}
 ```

### <a name="example-of-meeting-start-event-payload"></a>Exemplo de carga do evento de início da reunião

O código a seguir fornece um exemplo de carga de evento de início de reunião:

```json
{ 
    "name": "application/vnd.microsoft.meetingStart", 
    "type": "event", 
    "timestamp": "2021-04-29T16:10:41.1252256Z", 
    "id": "123", 
    "channelId": "msteams", 
    "serviceUrl": "https://microsoft.com", 
    "from": { 
        "id": "userID", 
        "aadObjectId": "aadOnjectId" 
    }, 
    "conversation": { 
        "isGroup": true, 
        "tenantId": "tenantId", 
        "id": "thread id" 
    }, 
    "recipient": { 
        "id": "user Id", 
        "name": "user name" 
    }, 
    "entities": [ 
        { 
            "locale": "en-US", 
            "country": "US", 
            "type": "clientInfo" 
        } 
    ], 
    "channelData": { 
        "tenant": { 
            "id": "channel id" 
        }, 
        "source": null, 
        "meeting": { 
            "id": "meeting id" 
        } 
    }, 
    "value": { 
        "MeetingType": "Scheduled", 
        "Title": "Meeting Start/End Event", 
        "Id": "meeting id", 
        "JoinUrl": "url" 
        "StartTime": "2021-04-29T16:17:17.4388966Z" 
    }, 
    "locale": "en-US" 
}
```

### <a name="example-of-meeting-end-event-payload"></a>Exemplo de carga de evento final de reunião

O código a seguir fornece um exemplo de carga de evento final de reunião:

```json
{ 
    "name": "application/vnd.microsoft.meetingEnd", 
    "type": "event", 
    "timestamp": "2021-04-29T16:17:17.4388966Z", 
    "id": "123", 
    "channelId": "msteams", 
    "serviceUrl": "https://microsoft.com", 
    "from": { 
        "id": "user id", 
        "aadObjectId": "aadObjectId" 
    }, 
    "conversation": { 
        "isGroup": true, 
        "tenantId": "tenantId", 
        "id": "thread id" 
    }, 
    "recipient": { 
        "id": "user id", 
        "name": "user name" 
    }, 
    "entities": [ 
        { 
            "locale": "en-US", 
            "country": "US", 
            "type": "clientInfo" 
        } 
    ], 
    "channelData": { 
        "tenant": { 
            "id": "channel id" 
        }, 
        "source": null, 
        "meeting": { 
            "id": "meeting Id" 
        } 
    }, 
    "value": { 
        "MeetingType": "Scheduled", 
        "Title": "Meeting Start/End Event in Canary", 
        "Id": "19:meeting_NTM3ZDJjOTUtZGRhOS00MzYxLTk5NDAtMzY4M2IzZWFjZGE1@thread.v2", 
        "JoinUrl": "url", 
        "EndTime": "2021-04-29T16:17:17.4388966Z" 
    }, 
    "locale": "en-US" 
}
```

### <a name="example-of-getting-metadata-of-a-meeting"></a>Exemplo de obter metadados de uma reunião

Seu bot recebe o evento por meio do `OnEventActivityAsync` manipulador.

Para desserializar a carga json, um objeto modelo é introduzido para obter os metadados de uma reunião. Os metadados de uma reunião estão na `value` propriedade na carga de eventos. O `MeetingStartEndEventvalue` objeto model é criado, cujas variáveis de membro correspondem às chaves sob a propriedade na carga do `value` evento.
     
> [!NOTE]      
> * Obter a ID da reunião de `turnContext.ChannelData` .    
> * Não use a ID da conversa como ID da reunião.     
> * Não use a ID da reunião do carregamento de eventos de `turncontext.activity.value` reunião. 
      
O código a seguir mostra como capturar os metadados de uma reunião que é , , , , e de um `MeetingType` `Title` evento de `Id` `JoinUrl` `StartTime` `EndTime` início/término de reunião:

Evento Início da Reunião
```csharp
protected override async Task OnTeamsMeetingStartAsync(MeetingEndEventDetails meeting, ITurnContext<IEventActivity> turnContext, CancellationToken cancellationToken)
{
    await turnContext.SendActivityAsync(JsonConvert.SerializeObject(meeting));
}
```

Evento Meeting End
```csharp
protected override async Task OnTeamsMeetingEndAsync(MeetingEndEventDetails meeting, ITurnContext<IEventActivity> turnContext, CancellationToken cancellationToken)
{
    await turnContext.SendActivityAsync(JsonConvert.SerializeObject(meeting));
}
```

## <a name="code-sample"></a>Exemplo de código

|Nome do exemplo | Descrição | C# | Node.js | 
|----------------|-----------------|--------------|--------------|
| Extensibilidade de reuniões | Microsoft Teams exemplo de extensibilidade de reunião para tokens de passagem. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/nodejs) |
| Bot de bolha de conteúdo de reunião | Microsoft Teams exemplo de extensibilidade de reunião para interagir com o bot de bolha de conteúdo em uma reunião. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/csharp) |  [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/nodejs)|
| Meeting meetingSidePanel | Microsoft Teams exemplo de extensibilidade de reunião para interagir com o painel lateral na reunião. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/nodejs)|
| Guia Detalhes na Reunião | Microsoft Teams exemplo de extensibilidade de reunião para interagir com a Guia detalhes na reunião. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-details-tab/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-details-tab/nodejs)|
|Exemplo de eventos de reunião|Exemplo de aplicativo para mostrar eventos de Teams reunião em tempo real|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-events/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-events/nodejs)|
|Exemplo de recrutamento de reunião|Exemplo de aplicativo para mostrar a experiência de reunião para cenário de recrutamento.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meeting-recruitment-app/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meeting-recruitment-app/nodejs)|
|Instalação de aplicativo usando código QR|Exemplo de aplicativo que gera o código QR e instala o aplicativo usando o código QR|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-installation-using-qr-code/csharp)|[Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-installation-using-qr-code/nodejs)|


## <a name="see-also"></a>Confira também

* [Teams fluxo de autenticação para guias](../tabs/how-to/authentication/auth-flow-tab.md)
* [Aplicativos para Teams reuniões](teams-apps-in-meetings.md)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Habilitar e configurar seus aplicativos para Teams reuniões](enable-and-configure-your-app-for-teams-meetings.md)
