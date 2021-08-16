---
title: Pré-requisitos e referências de API para aplicativos de reuniões do Teams
author: surbhigupta
description: Trabalhar com aplicativos para Teams reuniões
ms.topic: conceptual
ms.author: lajanuar
localization_priority: Normal
keywords: api de função de participante de reuniões de aplicativos do teams
ms.openlocfilehash: 1e0910a3f8fa76aae541b9f3bd1f79f673f64d92
ms.sourcegitcommit: 2c4c77dc8344f2fab8ed7a3f7155f15f0dd6a5ce
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2021
ms.locfileid: "58345357"
---
# <a name="prerequisites-and-api-references-for-apps-in-teams-meetings"></a>Pré-requisitos e referências de API para aplicativos de reuniões do Teams

Para expandir os recursos do aplicativo em todo o ciclo de vida da reunião, Teams permite que você trabalhe com aplicativos para Teams reuniões. Vá pelos pré-requisitos e use as referências da API de aplicativos de reunião para aprimorar a experiência de reunião.

## <a name="prerequisites"></a>Pré-requisitos

Antes de trabalhar com aplicativos para Teams reuniões, você deve ter um entendimento dos seguintes pré-requisitos:

* Saiba como desenvolver Teams aplicativos. Para obter mais informações sobre como desenvolver Teams aplicativo, [consulte Teams desenvolvimento de aplicativos.](../overview.md)

* Atualize o Teams de aplicativos para indicar que o aplicativo está disponível para reuniões. Para obter mais informações, consulte [manifesto do aplicativo](enable-and-configure-your-app-for-teams-meetings.md#update-your-app-manifest).

* Seu aplicativo deve dar suporte a guias configuráveis no escopo de groupchat, para que seu aplicativo funcione no ciclo de vida da reunião como uma guia. Para obter mais informações, consulte [groupchat scope](../resources/schema/manifest-schema.md#configurabletabs) and [build a group tab](../build-your-first-app/build-channel-tab.md).

* Acate as diretrizes Teams de design de guias gerais para cenários pré e pós-reunião. Para experiências durante as reuniões, consulte a guia na reunião e as diretrizes de design da caixa de diálogo na reunião. Para obter mais informações, [consulte Teams](../tabs/design/tabs.md)diretrizes de design de guia, diretrizes de [design](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab)de guia na reunião e diretrizes de design de caixa de diálogo [na reunião.](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)

* Suporte ao `groupchat` escopo para habilitar seu aplicativo em chats de pré-reunião e pós-reunião. Com a experiência do aplicativo de pré-reunião, você pode encontrar e adicionar aplicativos de reunião e realizar as tarefas de pré-reunião. Com a experiência do aplicativo pós-reunião, você pode exibir os resultados da reunião, como resultados da pesquisa ou comentários.

* Os parâmetros de URL da API de reunião `meetingId` devem ter , e `userId` `tenantId` . Os parâmetros estão disponíveis como parte da atividade Teams SDK do cliente e bot. Além disso, você pode recuperar informações confiáveis para a ID do usuário e a ID do locatário usando [a autenticação SSO da guia](../tabs/how-to/authentication/auth-aad-sso.md).

* A `GetParticipant` API deve ter um registro de bot e uma ID para gerar tokens de auth. Para obter mais informações, [consulte registro de bot e ID](../build-your-first-app/build-bot.md).

* Para que seu aplicativo seja atualizado em tempo real, ele deve estar atualizado com base nas atividades do evento na reunião. Esses eventos podem estar dentro da caixa de diálogo na reunião e em outros estágios no ciclo de vida da reunião. Para a caixa de diálogo na reunião, consulte o parâmetro completion `bot Id` na `NotificationSignal` API.

* A API de Detalhes da Reunião deve ter um registro de bot e uma ID de bot. Requer o SDK de Bot para `TurnContext` obter .

* Para eventos de reunião em tempo real, você deve estar familiarizado com o objeto disponível por meio `TurnContext` do SDK bot. O objeto em contém a carga com o início e a `Activity` `TurnContext` hora de término reais. Eventos de reunião em tempo real exigem uma ID de bot registrada na plataforma Teams.

Depois de passar pelos pré-requisitos, você pode usar as referências de API de aplicativos de reunião , , e a API de Detalhes da Reunião que permitem que você acesse informações usando atributos e exibir conteúdo `GetUserContext` `GetParticipant` `NotificationSignal` relevante.

## <a name="meeting-apps-api-references"></a>Referências à API de aplicativos de reunião

As seguintes extensibilidades de reunião fornecem APIs para transformar a experiência de reunião:

* Crie aplicativos ou integre aplicativos existentes ao ciclo de vida da reunião.
* Use as APIs para tornar seu aplicativo ciente da reunião.
* Selecione as APIs que você deseja usar para aprimorar a experiência de reunião.

A tabela a seguir fornece uma lista dessas APIs:

|API|Descrição|Solicitação|Origem|
|---|---|----|---|
|**GetUserContext**| Essa API permite que você receba informações contextuais para exibir conteúdo relevante em Teams guia. |_**microsoftTeams.getContext( ( ) => { /*...* / } )**_|Microsoft Teams SDK do cliente|
|**GetParticipant**| Essa API permite que um bot busque informações dos participantes por meio da ID da reunião e da ID do participante. |**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_ |Microsoft Bot Framework SDK|
|**NotificationSignal** | Essa API permite que você forneça sinais de reunião que são entregues usando a API de notificação de conversa existente para chat de usuário-bot. Ele permite sinalizar com base na ação do usuário que mostra uma caixa de diálogo na reunião. |**POST** _**/v3/conversations/{conversationId}/activities**_|Microsoft Bot Framework SDK|
|**Detalhes da reunião** | Essa API permite que você receba metadados de reunião estáticos. |**GET** _**/v1/meetings/{meetingId}**_| Bot SDK |

A tabela a seguir fornece os métodos SDK da Estrutura de Bot para as APIs:

|API|Método SDK da Estrutura de Bot|
|---|---|
|**GetParticipant**| `GetMeetingParticipantAsync (Microsoft.Bot.Builder.ITurnContext turnContext, string meetingId = default, string participantId = default, string tenantId = default, System.Threading.CancellationToken cancellationToken = default);` |
|**NotificationSignal** | `activity.TeamsNotifyUser(true, "https://teams.microsoft.com/l/bubble/APP_ID?url=&height=&width=&title=<title>&completionBotId=BOT_APP_ID");` |
|**Detalhes da reunião** | `TeamsMeetingInfo (string id = default);` |

### <a name="getusercontext-api"></a>GetUserContext API

Para identificar e recuperar informações contextuais para o conteúdo da guia, consulte [obter contexto para](../tabs/how-to/access-teams-context.md#get-context-by-using-the-microsoft-teams-javascript-library)sua Teams guia . `meetingId`é usado por uma guia ao ser executado no contexto da reunião e é adicionado para a carga de resposta.

### <a name="getparticipant-api"></a>GetParticipant API

> [!NOTE]
> * Não armazenar em cache as funções do participante, pois o organizador da reunião pode alterar as funções a qualquer momento.
> * Teams atualmente não dá suporte a grandes listas de distribuição ou tamanhos de lista de mais de 350 participantes para a `GetParticipant` API.

A `GetParticipant` API permite que um bot busque informações do participante por meio da ID da reunião e da ID do participante. A API inclui parâmetros de consulta, exemplos e códigos de resposta.

#### <a name="query-parameters"></a>Parâmetros de consulta

A `GetParticipant` API inclui os seguintes parâmetros de consulta:

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**meetingId**| Cadeia de caracteres | Sim | O identificador de reunião está disponível por meio de Bot Invoke e Teams Client SDK.|
|**participantId**| Cadeia de caracteres | Sim | A ID do participante é a ID do usuário. Ele está disponível em Tab SSO, Bot Invoke e Teams Client SDK. É recomendável obter uma ID de participante do SSO da guia. |
|**tenantId**| Cadeia de caracteres | Sim | A ID do locatário é necessária para os usuários do locatário. Ele está disponível em Tab SSO, Bot Invoke e Teams Client SDK. É recomendável obter uma ID de locatário do SSO de tabulação. |

#### <a name="example"></a>Exemplo

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

#### <a name="response-codes"></a>Códigos de resposta

A `GetParticipant` API retorna os seguintes códigos de resposta:

|Código da resposta|Descrição|
|---|---|
| **403** | Obter informações do participante não é compartilhado com o aplicativo. Se o aplicativo não estiver instalado na reunião, ele disparará a resposta de erro mais comum 403. Se o administrador do locatário desabilitar ou bloquear o aplicativo durante a migração do site ao vivo, a resposta de erro 403 será disparada. |
| **200** | As informações do participante são recuperadas com êxito.|
| **401** | O aplicativo responde com um token inválido.|
| **404** | A reunião expirou ou o participante não pode ser encontrado.|

### <a name="notificationsignal-api"></a>NotificationSignal API

Todos os usuários em uma reunião recebem as notificações enviadas por meio da `NotificationSignal` API.

> [!NOTE]
> * Quando uma caixa de diálogo na reunião é invocada, o conteúdo é apresentado como uma mensagem de chat.
> * Atualmente, não há suporte para o envio de notificações direcionadas.

`NotificationSignal` A API permite que você forneça sinais de reunião que são entregues usando a API de notificação de conversa existente para chat usuário-bot. Essa API permite sinalizar com base na ação do usuário que mostra uma caixa de diálogo na reunião. A API inclui parâmetros de consulta, exemplos e códigos de resposta.

#### <a name="query-parameter"></a>Parâmetro de consulta

A `NotificationSignal` API inclui o seguinte parâmetro de consulta:

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**conversationId**| String | Sim | O identificador de conversa está disponível como parte de Bot Invoke. |

#### <a name="examples"></a>Exemplos

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

#### <a name="response-codes"></a>Códigos de resposta

A `NotificationSignal` API inclui os seguintes códigos de resposta:

|Código da resposta|Descrição|
|---|---|
| **201** | A atividade com sinal é enviada com êxito. |
| **401** | O aplicativo responde com um token inválido. |
| **403** | O aplicativo não consegue enviar o sinal. O código de resposta 403 pode ocorrer por vários motivos, como o administrador do locatário desabilita e bloqueia o aplicativo durante a migração do site ao vivo. Nesse caso, a carga contém uma mensagem de erro detalhada. |
| **404** | O chat de reunião não existe. |

### <a name="meeting-details-api"></a>API de Detalhes da Reunião

> [!NOTE]
> Esse recurso está disponível apenas na [visualização de desenvolvedor](../resources/dev-preview/developer-preview-intro.md) público.

A API Detalhes da Reunião permite que seu aplicativo receba metadados de reunião estáticos. Os metadados fornece pontos de dados que não mudam dinamicamente.
A API está disponível por meio dos Serviços bot.

#### <a name="prerequisite"></a>Pré-requisito

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
 
#### <a name="query-parameter"></a>Parâmetro de consulta

A API De Detalhes da Reunião inclui o seguinte parâmetro de consulta:

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**meetingId**| Cadeia de caracteres | Sim | O identificador de reunião está disponível por meio de Bot Invoke e Teams Client SDK. |

#### <a name="example"></a>Exemplo

A API De Detalhes da Reunião inclui os seguintes exemplos:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
var connectorClient = turnContext.TurnState.Get<IConnectorClient>();
var creds = connectorClient.Credentials as AppCredentials;
var bearerToken = await creds.GetTokenAsync().ConfigureAwait(false);
var request = new HttpRequestMessage(HttpMethod.Get, new Uri(new Uri(connectorClient.BaseUri.OriginalString), $"v1/meetings/{meetingId}"));
request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", bearerToken);
HttpResponseMessage response = await (connectorClient as ServiceClient<ConnectorClient>).HttpClient.SendAsync(request, CancellationToken.None).ConfigureAwait(false);
string content;
if (response.Content != null)
{
    content = await response.Content.ReadAsStringAsync().ConfigureAwait(false);
}
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

## <a name="real-time-teams-meeting-events"></a>Eventos de reunião Teams em tempo real

> [!NOTE]
> Esse recurso está disponível apenas na [visualização de desenvolvedor](../resources/dev-preview/developer-preview-intro.md) público.

O usuário pode receber eventos de reunião em tempo real. Assim que qualquer aplicativo é associado a uma reunião, o início real da reunião e a hora de término da reunião são compartilhados com o bot.

A hora real de início e término de uma reunião é diferente da hora de início e término agendada. A API de detalhes da reunião fornece a hora de início e término agendada. O evento fornece a hora real de início e término.

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
      
O código a seguir mostra como capturar os metadados de uma reunião que é , , , , e de um evento de início e fim de `MeetingType` `Title` `Id` `JoinUrl` `StartTime` `EndTime` reunião:

```csharp
protected override async Task OnEventActivityAsync(
ITurnContext<IEventActivity> turnContext, CancellationToken cancellationToken)
{
    // Event Name is either 'application/vnd.microsoft.meetingStart' or 'application/vnd.microsoft.meetingEnd'
    var meetingEventName = turnContext.Activity.Name;
    // Value contains meeting information (ex: meeting type, start time, etc).
    var meetingEventInfo = turnContext.Activity.Value as JObject; 
    var meetingEventInfoObject =
meetingEventInfo.ToObject<MeetingStartEndEventValue>();
    // Create a very simple adaptive card with meeting information
var attachmentCard = createMeetingStartOrEndEventAttachment(meetingEventName,
meetingEventInfoObject);
    await turnContext.SendActivityAsync(MessageFactory.Attachment(attachmentCard));
}
```

MeetingStartEndEventvalue.cs inclui o seguinte código:

```csharp
public class MeetingStartEndEventValue
{
    public string Id { get; set; }
    public string Title { get; set; }
    public string MeetingType { get; set; }
    public string JoinUrl { get; set; }
    public string StartTime { get; set; }
    public string EndTime { get; set; }
}
```

## <a name="code-sample"></a>Exemplo de código

|Nome do exemplo | Descrição | .NET | Node.js |
|----------------|-----------------|--------------|--------------|
| Extensibilidade de reuniões | Microsoft Teams exemplo de extensibilidade de reunião para tokens de passagem. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/nodejs) |
| Bot de bolha de conteúdo de reunião | Microsoft Teams exemplo de extensibilidade de reunião para interagir com o bot de bolha de conteúdo em uma reunião. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/csharp) |  [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/nodejs)|
| Meeting meetingSidePanel | Microsoft Teams exemplo de extensibilidade de reunião para interagir com o painel lateral na reunião. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/nodejs)|
| Guia Detalhes na Reunião | Microsoft Teams exemplo de extensibilidade de reunião para interagir com a Guia detalhes na reunião. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-details-tab/csharp) | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-details-tab/nodejs)|

## <a name="see-also"></a>Confira também

* [Diretrizes de design de caixa de diálogo na reunião](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
* [Teams fluxo de autenticação para guias](../tabs/how-to/authentication/auth-flow-tab.md)
* [Aplicativos para Teams reuniões](teams-apps-in-meetings.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Habilitar e configurar seus aplicativos para Teams reuniões](enable-and-configure-your-app-for-teams-meetings.md)
