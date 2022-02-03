---
title: Referências à API de aplicativos de reunião
author: surbhigupta
description: Identificar as referências da API de aplicativos de reunião com exemplos e exemplos de código
ms.topic: conceptual
ms.author: lajanuar
ms.localizationpriority: medium
keywords: consulta de sinal de notificação do usuário de função de usuário de reuniões de aplicativos do teams
ms.openlocfilehash: dd46dc2622915055e46e07ae34d48c690d6d8d8e
ms.sourcegitcommit: 58a24422bb04a529b6629a56803ed2efabc17cb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/02/2022
ms.locfileid: "62323145"
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
|**CART**|Permite que você poste legendas para uma reunião, que foi iniciada.|**POST /cartcaption?meetingid=04751eac-30e6-47d9-9c3f-0b4ebe8e30d9&token=04751eac&lang=en-us HTTP/1.1**|Microsoft Teams SDK do cliente|

## <a name="getusercontext-api"></a>GetUserContext API

Para identificar e recuperar informações contextuais para o conteúdo da guia, consulte [obter](../tabs/how-to/access-teams-context.md#get-context-by-using-the-microsoft-teams-javascript-library) contexto para sua guia Teams. `meetingId` É usado por uma guia ao ser executado no contexto da reunião e é adicionado para a carga de resposta.

## <a name="getparticipant-api"></a>GetParticipant API

> [!NOTE]
> * Não armazenar em cache as funções do participante, pois o organizador da reunião pode alterar as funções a qualquer momento.
> * Teams atualmente não suporta listas de distribuição grandes ou tamanhos de lista de mais de 350 participantes para o `GetParticipant` API.

A `GetParticipant` API permite que um bot busque informações do participante por meio da ID da reunião e da ID do participante. A API inclui parâmetros de consulta, exemplos e códigos de resposta.

### <a name="query-parameters"></a>Parâmetros de consulta

A `GetParticipant` API inclui os seguintes parâmetros de consulta:

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**meetingId**| Cadeia de caracteres | Sim | O identificador de reunião está disponível por meio de Bot Invoke e Teams Client SDK.|
|**participantId**| String | Sim | A ID do participante é a ID do usuário. Ele está disponível em Tab SSO, Bot Invoke e Teams Client SDK. É recomendável obter uma ID de participante do SSO da guia. |
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
> * O `completionBotId` parâmetro do é `externalResourceUrl` opcional no exemplo de carga solicitada. `Bot ID` é declarado no manifesto e o bot recebe um objeto de resultado.
> * Os `externalResourceUrl` parâmetros de largura e altura devem estar em pixels. Para garantir que as dimensões estão dentro dos limites permitidos, consulte [diretrizes de design](design/designing-apps-in-meetings.md).
> * A URL é a página carregada como uma `<iframe>` caixa de diálogo na reunião. O domínio deve estar na matriz do aplicativo `validDomains` no manifesto do aplicativo.

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

> [!NOTE] 
> Verifique se seu aplicativo atende a todos os pré-requisitos [listados em Pré-requisitos para aplicativos em Teams reuniões](~/apps-in-teams-meetings/create-apps-for-teams-meetings.md).

Para usar a API de Detalhes da Reunião, você deve obter permissões RSC. Use o exemplo a seguir para configurar a propriedade do manifesto do aplicativo `webApplicationInfo` :

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
|**meetingId**| Cadeia de caracteres | Sim | O identificador de reunião está disponível por meio de Bot Invoke e Teams Client SDK. |

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

## <a name="cart-api"></a>CART API

A API de conversão em tempo real de acesso à comunicação (CART) expõe um ponto de extremidade POST para Microsoft Teams legendas CART, legendas fechadas do tipo humano. O conteúdo de texto enviado para esse ponto de extremidade aparece para usuários finais em uma reunião Microsoft Teams quando eles têm legendas habilitadas.

### <a name="cart-url"></a>CART URL

Você pode obter a URL CART do ponto de extremidade POST na página **Opções** de reunião em uma Microsoft Teams reunião. Para obter mais informações, consulte [legendas CART em uma Microsoft Teams reunião](https://support.microsoft.com/office/use-cart-captions-in-a-microsoft-teams-meeting-human-generated-captions-2dd889e8-32a8-4582-98b8-6c96cf14eb47). Você não precisa modificar a URL CART para usar legendas CART.

#### <a name="query-parameter"></a>Parâmetro Query

A URL cart inclui os seguintes parâmetros de consulta:

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|----|
|**meetingId**| Cadeia de caracteres | Sim |O identificador de reunião está disponível por meio de Bot Invoke e Teams Client SDK. <br/>Por exemplo, meetingid=%7b%22tId%22%3a%2272f234bf-86f1-41af-91ab-2d7cd0321b47%22%2c%22oId%22%3a%22e071f268-4241-47f8-8cf3-fc6b84437f23%22%2c%22thId%22%3a%2219%3ameeting_NzJiMjNkMGQtYzk3NS00ZDI1LWJjN2QtMDgyODVhZmI3NzJj%40thread.v2%22%2c%22mId%22%3a%220%22%22%7d|
|**token**| Cadeia de caracteres | Sim |Token de autorização.<br/> Por exemplo, token=04751eac |

#### <a name="example"></a>Exemplo

```http
https://api.captions.office.microsoft.com/cartcaption?meetingid=%7b%22tId%22%3a%2272f234bf-86f1-41af-91ab-2d7cd0321b47%22%2c%22oId%22%3a%22e071f268-4241-47f8-8cf3-fc6b84437f23%22%2c%22thId%22%3a%2219%3ameeting_NzJiMjNkMGQtYzk3NS00ZDI1LWJjN2QtMDgyODVhZmI3NzJj%40thread.v2%22%2c%22mId%22%3a%220%22%7d&token=gjs44ra
```

### <a name="method"></a>Método

|Recurso|Método|Descrição|
|----|----|----|
|/cartcaption|POST|Manipular legendas para reunião, que foi iniciada|

> [!NOTE]
> Verifique se o tipo de conteúdo para todas as solicitações é texto sem texto com codificação UTF-8. O corpo da solicitação contém apenas legendas.

#### <a name="example"></a>Exemplo

```http
POST /cartcaption?meetingid=04751eac-30e6-47d9-9c3f-0b4ebe8e30d9&token=04751eac&lang=en-us HTTP/1.1
Host: api.captions.office.microsoft.com
Content-Type: text/plain
Content-Length: 22
Hello I’m Cortana, welcome to my meeting. 
```

> [!Note]  
> Cada solicitação POST gera uma nova linha de legendas. Para garantir que o usuário final tenha tempo suficiente para ler o conteúdo, limite cada corpo de solicitação POST a 80 a 120 caracteres.

### <a name="error-codes"></a>Códigos de erro

A API CART inclui os seguintes códigos de erro:

|Código de erro|Descrição|
|---|---|
| **400** | Solicitação ruim. O corpo da resposta tem mais informações. Por exemplo, não de todos os parâmetros necessários apresentados.|
| **401** | Não autorizado. Token ruim ou expirado. Se você receber esse erro, gere uma nova URL CART no Teams. |
| **404** | Reunião não encontrada ou não iniciada. Se você receber esse erro, certifique-se de iniciar a reunião e selecione iniciar legendas. Depois que as legendas são habilitadas na reunião, você pode começar a POSTing legendas na reunião.|
| **500** |Erro de servidor interno. Para obter mais informações, [contate o suporte ou forneça comentários](../feedback.md).|

## <a name="real-time-teams-meeting-events"></a>Eventos de reunião Teams em tempo real

O usuário pode receber eventos de reunião em tempo real. Assim que qualquer aplicativo é associado a uma reunião, o início e a hora de término reais da reunião são compartilhados com o bot.

A hora real de início e término de uma reunião é diferente da hora de início e término agendada. A API De Detalhes da Reunião fornece a hora de início e término agendada. O evento fornece a hora real de início e término.

### <a name="prerequisite"></a>Pré-requisito

> [!NOTE] 
> Verifique se seu aplicativo atende a todos os pré-requisitos [listados em Pré-requisitos para aplicativos em Teams reuniões](~/apps-in-teams-meetings/create-apps-for-teams-meetings.md).

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

Para desserializar a carga json, um objeto modelo é introduzido para obter os metadados de uma reunião. Os metadados de uma reunião estão na `value` propriedade na carga de eventos. O `MeetingStartEndEventvalue` objeto model é criado, cujas variáveis de membro correspondem às chaves sob a `value` propriedade na carga do evento.
     
> [!NOTE]      
> * Obter a ID da reunião de `turnContext.ChannelData`.    
> * Não use a ID da conversa como ID da reunião.     
> * Não use a ID da reunião do carregamento de eventos de reunião `turncontext.activity.value`. 
      
O código a seguir mostra como capturar os metadados `MeetingType`de uma reunião que é , `Id``Title`, , `JoinUrl`, e `EndTime` `StartTime`de um evento de início/término de reunião:

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
| Guia Detalhes na Reunião | Microsoft Teams exemplo de extensibilidade de reunião para interagir com a Guia detalhes na reunião. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-details-tab/csharp) | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-details-tab/nodejs)|
|Exemplo de eventos de reunião|Exemplo de aplicativo para mostrar eventos de Teams reunião em tempo real|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-events/csharp)|[Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-events/nodejs)|
|Exemplo de recrutamento de reunião|Exemplo de aplicativo para mostrar a experiência de reunião para cenário de recrutamento.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meeting-recruitment-app/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meeting-recruitment-app/nodejs)|
|Instalação de aplicativo usando código QR|Exemplo de aplicativo que gera o código QR e instala o aplicativo usando o código QR|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-installation-using-qr-code/csharp)|[Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-installation-using-qr-code/nodejs)|


## <a name="see-also"></a>Confira também

* [Teams fluxo de autenticação para guias](../tabs/how-to/authentication/auth-flow-tab.md)
* [Aplicativos para reuniões do Teams](teams-apps-in-meetings.md)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Habilitar e configurar seus aplicativos para Teams reuniões](enable-and-configure-your-app-for-teams-meetings.md)
