---
title: Referências à API de aplicativos de reunião
author: surbhigupta
description: Neste artigo, aprenda as referências de API de aplicativos de reunião que estão disponíveis para o cliente do Teams e os SDK do Bot Framework com exemplos, exemplos de código e códigos de resposta.
ms.topic: conceptual
ms.author: lajanuar
ms.localizationpriority: medium
ms.date: 04/07/2022
ms.openlocfilehash: 8277e0fb947ac109f3482c31613c01fd924fa139
ms.sourcegitcommit: d5628e0d50c3f471abd91c3a3c2f99783b087502
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2022
ms.locfileid: "67435010"
---
# <a name="meeting-apps-api-references"></a>Referências à API de aplicativos de reunião

A extensibilidade da reunião fornece APIs para aprimorar a experiência de reunião. Você pode executar o seguinte com a ajuda das APIs listadas:

* Crie aplicativos ou integre aplicativos existentes no ciclo de vida da reunião.
* Use APIs para tornar seu aplicativo ciente da reunião.
* Selecione as APIs necessárias para melhorar a experiência de reunião.

> [!NOTE]
> Use o Teams [JavaScript SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) (*Versão*: 1.10 e posterior) para que o SSO funcione no painel lateral da reunião.

A tabela a seguir fornece uma lista de APIs disponíveis nos SDKs do Microsoft Teams Client (MSTC) e Microsoft Bot Framework (MSBF):

|Método| Descrição| Source|
|---|---|----|
|[**Get contexto do usuário**](#get-user-context-api)| Obtenha informações contextuais para exibir conteúdo relevante em uma guia do Microsoft Teams.| [MSTC SDK](/microsoftteams/platform/tabs/how-to/access-teams-context#get-context-by-using-the-microsoft-teams-javascript-library) |
|[**Obter participante**](#get-participant-api)| Buscar informações do participante por ID de reunião e ID do participante. | [MSBF SDK](/dotnet/api/microsoft.bot.builder.teams.teamsinfo.getmeetingparticipantasync?view=botbuilder-dotnet-stable&preserve-view=true)
|[**Enviar notificação na reunião**](#send-an-in-meeting-notification)| Forneça sinais de reunião usando a API de notificação de conversa existente para chat de bot de usuário e permite notificar a ação do usuário que mostra uma notificação na reunião. | [MSBF SDK](/dotnet/api/microsoft.bot.builder.teams.teamsactivityextensions.teamsnotifyuser?view=botbuilder-dotnet-stable&preserve-view=true) |
|[**Get meeting details**](#get-meeting-details-api)| Obter metadados estáticos de uma reunião. | [MSBF SDK](/dotnet/api/microsoft.bot.builder.teams.teamsinfo.getmeetinginfoasync?view=botbuilder-dotnet-stable&preserve-view=true) |
|[**Enviar legendas em tempo real**](#send-real-time-captions-api)| Envie legendas em tempo real para uma reunião em andamento. | [MSTC SDK](/azure/cognitive-services/speech-service/speech-sdk?tabs=nodejs%2Cubuntu%2Cios-xcode%2Cmac-xcode%2Candroid-studio#get-the-speech-sdk&preserve-view=true) |
|[**Compartilhar Conteúdo do Aplicativo na Janela de Conteúdo Compartilhado**](#share-app-content-to-stage-api)| Compartilhe partes específicas do aplicativo para o estágio de reunião no painel lateral do aplicativo em uma reunião. | [MSTC SDK](/javascript/api/@microsoft/teams-js/meeting) |
|[**Obter Estado de Compartilhamento da Janela de Conteúdo**](#get-app-content-stage-sharing-state-api)| Busque informações sobre o estado de compartilhamento do aplicativo no estágio da reunião. | [MSTC SDK](/javascript/api/@microsoft/teams-js/meeting.iappcontentstagesharingstate) |
|[**Obter Recursos de Compartilhamento da Janela de Conteúdo**](#get-app-content-stage-sharing-capabilities-api)| Busque os recursos do aplicativo para compartilhar com o estágio da reunião. | [MSTC SDK](/javascript/api/@microsoft/teams-js/meeting.iappcontentstagesharingcapabilities) |
|[**Obtenha eventos de reunião do Teams em tempo real**](#get-real-time-teams-meeting-events-api)|Busque eventos de reunião em tempo real, como a hora real de início e término.| [MSBF SDK](/dotnet/api/microsoft.bot.builder.teams.teamsactivityhandler.onteamsmeetingstartasync?view=botbuilder-dotnet-stable&preserve-view=true) |
| [**Obter estado de áudio de entrada**](#get-incoming-audio-state) | Permite que um aplicativo obtenha a configuração de estado de áudio de entrada para o usuário da reunião.| [MSTC SDK](/javascript/api/@microsoft/teams-js/microsoftteams.meeting?view=msteams-client-js-latest&preserve-view=true) |
| [**Alternar áudio de entrada**](#toggle-incoming-audio) | Permite que um aplicativo alterne a configuração de estado de áudio de entrada para o usuário da reunião de mudo para mudo ou vice-versa.| [MSTC SDK](/javascript/api/@microsoft/teams-js/microsoftteams.meeting?view=msteams-client-js-latest&preserve-view=true) |

## <a name="get-user-context-api"></a>Obter API de contexto do usuário

Para identificar e recuperar informações contextuais para o conteúdo da guia, consulte [obter contexto para a guia Teams](../tabs/how-to/access-teams-context.md#get-context-by-using-the-microsoft-teams-javascript-library). `meetingId` é usado por uma guia em execução no contexto da reunião e é adicionado à carga útil de resposta.

## <a name="get-participant-api"></a>Obter API de participante

A API `GetParticipant` deve ter um registro de bot e uma ID para gerar tokens de autenticação. Para obter mais informações, consulte [registro e ID do bot](../build-your-first-app/build-bot.md).

> [!NOTE]
>
> * Não armazene em cache as funções de participante, pois o organizador da reunião pode alterar as funções a qualquer momento.
> * Atualmente, a API `GetParticipant` só tem suporte para listas de distribuições ou listas com menos de 350 participantes.

### <a name="query-parameters"></a>Parâmetros de consulta

> [!TIP]
> Obtenha IDs de participantes e IDs de locatários na [guia Autenticação SSO](../tabs/how-to/authentication/tab-sso-overview.md).

A API `Meeting` deve ter `meetingId`, `participantId` e `tenantId` como parâmetros de URL. Os parâmetros estão disponíveis como parte da atividade de bot e SDK do Cliente do Teams.

A tabela a seguir inclui os parâmetros de consulta:

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**meetingId**| Cadeia de caracteres | Sim | O identificador de reunião está disponível por meio do Bot Invoke e do SDK do Cliente do Teams.|
|**participantId**| Cadeia de caracteres | Sim | A ID do participante é a ID de usuário. Ele está disponível no SSO da guia, no Bot Invoke e no SDK do Cliente do Teams. É recomendável obter uma ID de participante do SSO da guia. |
|**tenantId**| Cadeia de caracteres | Sim | A ID do locatário é necessária para os usuários do locatário. Ele está disponível no SSO da guia, no Bot Invoke e no SDK do Cliente do Teams. É recomendável obter uma ID de locatário do SSO da guia. |

### <a name="example"></a>Exemplo

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
      "conversationType": "groupChat", 
      "isGroup":true
   }
}
```

---

| Nome da propriedade | Descrição |
|---|---|
| **user.id** | ID do usuário. |
| **user.aadObjectId** | ID de objeto do Azure Active Directory do usuário. |
| **user.name** | Nome do usuário. |
| **user.givenName** | Nome do usuário.|
| **user.surname** | Sobrenome do usuário. |
| **user.email** | ID de email do usuário. |
| **user.userPrincipalName** | UPN do usuário. |
| **user.tenantId** | Locatário do Azure Active Directory. |
| **user.userRole** | Função do usuário. Por exemplo, 'admin' ou 'user'. |
| **meeting.role** | A função do participante na reunião. Por exemplo, 'Organizador' ou 'Apresentador' ou 'Participante'. |
| **meeting.inMeeting** | O valor que indica se o participante está na reunião. |
| **conversation.id** | A ID de chat da reunião. |
| **conversation.isGroup** | Booliano que indica se a conversa tem mais de dois participantes. |

### <a name="response-codes"></a>Códigos de resposta

A tabela a seguir fornece os códigos de resposta:

|Código da resposta|Descrição|
|---|---|
| **403** | Obter informações do participante não é compartilhado com o aplicativo. Se o aplicativo não estiver instalado na reunião, ele disparará a resposta de erro 403. Se o administrador do locatário desabilitar ou bloquear o aplicativo durante a migração ao vivo do site, ele disparará a resposta de erro 403. |
| **200** | As informações do participante são recuperadas com êxito.|
| **401** | O aplicativo responde com um token inválido.|
| **404** | A reunião expirou ou os participantes não estão disponíveis.|

## <a name="send-an-in-meeting-notification"></a>Enviar uma notificação na reunião

Todos os usuários em uma reunião recebem as notificações enviadas por meio da carga de notificação na reunião. A carga de notificação na reunião dispara uma notificação na reunião e permite que você forneça sinais de reunião que são entregues usando a API de notificação de conversa existente para chat de bot do usuário. Você pode enviar uma notificação na reunião com base na ação do usuário. A carga está disponível por meio dos Serviços de Bot.

> [!NOTE]
>
> * Quando uma notificação na reunião é invocada, o conteúdo é apresentado como uma mensagem de chat.
> * Atualmente, não há suporte para o envio de notificações direcionadas e suporte para webapp.
> * Você deve invocar a função [submitTask()](../task-modules-and-cards/task-modules/task-modules-bots.md#submit-the-result-of-a-task-module) para ignorar automaticamente depois que um usuário executar uma ação no modo de exibição da Web. Esse é um requisito para o envio do aplicativo. Para obter mais informações, consulte [Módulo de tarefas do SDK do Teams](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).
> * Se você quiser que seu aplicativo seja compatível com usuários anônimos, o conteúdo da solicitação de invocação inicial deverá depender do objeto `from.id` para solicitar metadados em `from` e não nos metadados de solicitação `from.aadObjectId`. `from.id` é a ID de usuário e `from.aadObjectId` é a ID do Microsoft Azure Active Directory (Azure AD) do usuário. Para obter mais informações, consulte [usando módulos de tarefa em guias](../task-modules-and-cards/task-modules/task-modules-tabs.md) e [criar e enviar o módulo de tarefa](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).

### <a name="query-parameter"></a>Parâmetro de consulta

A tabela a seguir inclui o parâmetro de consulta:

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**conversationId**| String | Sim | O identificador de conversa está disponível como parte do Bot Invoke. |

### <a name="examples"></a>Exemplos

O `Bot ID` é declarado no manifesto e o bot recebe um objeto de resultado.

> [!NOTE]
>
> * O parâmetro `completionBotId` do `externalResourceUrl` é opcional no exemplo de carga solicitado.
> * Os `externalResourceUrl` largura e altura devem estar em pixels. Para obter mais informações, consulte [diretrizes de design](design/designing-apps-in-meetings.md).
> * A URL é a página, que é carregada como `<iframe>` na notificação na reunião. O domínio deve estar na matriz `validDomains` no manifesto do aplicativo.

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
```

```json

{
    "type": "message",
    "text": "John Phillips assigned you a weekly todo",
    "summary": "Don't forget to meet with Marketing next week",
    "channelData": {
        "notification": {
            "alertInMeeting": true,
            "externalResourceUrl": "https://teams.microsoft.com/l/bubble/APP_ID?url=<url>&height=<height>&width=<width>&title=<title>&<completionBotId>=<BOT_APP_ID>"
        }
    },
    "replyToId": "1493070356924"
}
```

---

| Nome da propriedade | Descrição |
|---|---|
| **type** | Tipo de atividade. |
| **text** | O conteúdo de texto da mensagem. |
| **resumo** | O texto de resumo da mensagem. |
| **channelData.notification.alertInMeeting** | Booliano que indica se uma notificação deve ser mostrada ao usuário durante uma reunião. |
| **channelData.notification.externalResourceUrl** | O valor da URL de recurso externo da notificação.|
| **replyToId** | A ID da mensagem pai ou raiz do thread. |
| **APP_ID** | ID do aplicativo declarada no manifesto. |
| **completionBotId** | ID do aplicativo de bot |

### <a name="response-codes"></a>Códigos de resposta

A tabela a seguir inclui os códigos de resposta:

|Código da resposta|Descrição|
|---|---|
| **201** | A atividade com sinal foi enviada com êxito. |
| **401** | O aplicativo responde com um token inválido. |
| **403** | O aplicativo não pode enviar o sinal. O código de resposta 403 pode ocorrer devido a vários motivos, como o administrador de locatários desabilita e bloqueia o aplicativo durante a migração ao vivo do site. Nesse caso, a carga contém uma mensagem de erro detalhada. |
| **404** | O chat da reunião não existe. |

## <a name="get-meeting-details-api"></a>Obter API de detalhes da reunião

A API de Detalhes da Reunião permite que seu aplicativo obtenha os metadados estáticos de uma reunião. Os metadados fornecem pontos de dados que não são alterados dinamicamente. A API está disponível por meio dos Serviços de Bot. Atualmente, reuniões agendadas ou recorrentes privadas e canal agendadas ou recorrentes dão suporte à API de suporte a reuniões com diferentes permissões de RSC, respectivamente.

A API `Meeting Details` deve ter um registro de bot e uma ID de bot. Ele requer que o SDK do Bot obtenha `TurnContext`. Para usar a API de Detalhes da Reunião, você deve obter uma permissão RSC diferente com base no escopo de qualquer reunião, como reunião privada ou reunião de canal.

### <a name="prerequisite"></a>Pré-requisito

Para usar a API de Detalhes da Reunião, você deve obter uma permissão RSC diferente com base no escopo de qualquer reunião, como reunião privada ou reunião de canal.

<br>

<details>

<summary><b>Para o manifesto do aplicativo versão 1.12 e posterior</b></summary>

Use o exemplo a seguir para configurar as propriedades `webApplicationInfo` e `authorization` para qualquer reunião privada:

```json
"webApplicationInfo": {
    "id": "<bot id>",
    "resource": "https://RscPermission",
},
"authorization": {
    "permissions": {
        "resourceSpecific": [
            {
                "name": "OnlineMeeting.ReadBasic.Chat",
                "type": "Application"
            }
        ]
    }
}
 ```

Use o exemplo a seguir para configurar as propriedades `webApplicationInfo` e `authorization` para qualquer reunião de canal:

```json
"webApplicationInfo": {
    "id": "<bot id>",
    "resource": "https://RscPermission",
},
"authorization": {
    "permissions": {
        "resourceSpecific": [
            {
                "name": "ChannelMeeting.ReadBasic.Group",
                "type": "Application"
            }
        ]
    }
}
 ```

<br>

</details>

<br>

<details>

<summary><b>Para o manifesto do aplicativo versão 1.11 e anterior</b></summary>

Use o exemplo a seguir para configurar a propriedade `webApplicationInfo` do manifesto do aplicativo para qualquer reunião privada:

```json
"webApplicationInfo": {
    "id": "<bot id>",
    "resource": "https://RscPermission",
    "applicationPermissions": [
      "OnlineMeeting.ReadBasic.Chat"
    ]
}
 ```

Use o exemplo a seguir para configurar a propriedade `webApplicationInfo` do manifesto do aplicativo para qualquer reunião de canal:

```json
"webApplicationInfo": {
    "id": "<bot id>",
    "resource": "https://RscPermission",
    "applicationPermissions": [
      "ChannelMeeting.ReadBasic.Group"
    ]
}
 ```

<br>

</details>

> [!NOTE]
>
> * O bot pode receber eventos de início ou término de reunião automaticamente de todas as reuniões criadas em todos os canais adicionando `ChannelMeeting.ReadBasic.Group` ao manifesto para a permissão RSC.
>
> * Para uma chamada um-para-um `organizer` é o iniciador do chat e para chamadas de `organizer` grupo é o iniciador de chamada.

### <a name="query-parameter"></a>Parâmetro de consulta

A tabela a seguir lista o parâmetro de consulta:

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**meetingId**| Cadeia de caracteres | Sim | O identificador de reunião está disponível por meio do Bot Invoke e do SDK do Cliente do Teams. |

### <a name="example"></a>Exemplo

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
MeetingInfo result = await TeamsInfo.GetMeetingInfoAsync(turnContext);
await turnContext.SendActivityAsync(JsonConvert.SerializeObject(result));
```

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```javascript

Not available

```

# <a name="json"></a>[JSON](#tab/json)

```http
GET /v1/meetings/{meetingId}
```

O corpo da resposta JSON para a API de Detalhes da Reunião é o seguinte:

* **Reuniões agendadas:**

    ```json

    {
       "details":  { 
             "id": "<meeting ID>", 
             "msGraphResourceId": "MSowYmQ0M2I4OS1lN2QxLTQxNzAtOGZhYi00OWJjYjkwOTk1YWYqMCoqMTk6bWVldGluZ19OVEkyT0RjM01qUXROV1UyW", 
             "scheduledStartTime": "2022-04-24T22:00:00Z", 
             "scheduledEndTime": "2022-04-24T23:00:00Z", 
             "joinUrl": "https://teams.microsoft.com/l/xx", 
             "title": "All Hands", 
             "type": "Scheduled" 
         },
        "conversation": { 
             "isGroup": true, 
             "conversationType": "groupChat", 
             "id": "meeting chat ID" 
             }, 
        "organizer": { 
             "id": "<organizer user ID>", 
             "aadObjectId": "<AAD object ID>",
             "objectId": "<organizer object ID>",
             "tenantId": "<Tenant ID>" 
         }
    } 
    ```

* **Chamadas um-a-um:**

    ```json
    {
        "details": {
             "id": "<meeting ID>",
             "type": "OneToOneCall"
         },
        "conversation": {
             "isGroup": true,
             "conversationType": "groupChat",
             "id": "meeting chat ID"
         },
        "organizer  ": {
             "id": "<organizer user ID>",
             "aadObjectId": "<AAD object ID>",
             "objectId": "<organizer object ID>",
             "tenantId": "<Tenant ID>" 
         }
    }
    
    ```

* **Chamadas de grupo:**

    ```json
    {
        "details": {
             "id": "<meeting ID>",
             "type": "GroupCall",
             "joinUrl": "https://teams.microsoft.com/l/xx"
         },
        "conversation": {
             "isGroup": true,
             "conversationType": "groupChat",
             "id": "meeting chat ID"
         },
        "organizer": {
             "id": "<organizer user ID>",
             "objectId": "<organizer object ID>",
             "aadObjectId": "<AAD object ID>",
             "tenantId": "<Tenant ID>" 
         }
    }
    
    ```

* **Reuniões instantâneas:**

    ```json
    { 
       "details": { 
             "id": "<meeting ID>", 
             "msGraphResourceId": "MSowYmQ0M2I4OS1lN2QxLTQxNzAtOGZhYi00OWJjYjkwOTk1YWYqMCoqMTk6bWVldGluZ19OVEkyT0RjM01qUXROV1UyW", 
             "scheduledStartTime": "2022-04-24T22:00:00Z", 
             "scheduledEndTime": "2022-04-24T23:00:00Z", 
             "joinUrl": "https://teams.microsoft.com/l/xx", 
             "title": "All Hands", 
             "type": "MeetNow" 
         }, 
        "conversation": { 
             "isGroup": true, 
             "conversationType": "groupChat", 
             "id": "meeting chat ID" 
         },
        "organizer": { 
             "id": "<organizer user ID>", 
             "aadObjectId": "<AAD object ID>", 
             "tenantId": "<Tenant ID>" ,
             "objectId": "<organizer object ID>"
         }
    }
    
    ```

---

| Nome da propriedade | Descrição |
|---|---|
| **details.id** | A ID da reunião, codificada como uma cadeia de caracteres BASE64. |
| **details.msGraphResourceId** | O MsGraphResourceId, usado especificamente para chamadas de API do Graph MS. |
| **details.scheduledStartTime** | A hora de início agendada da reunião, em UTC. |
| **details.scheduledEndTime** | A hora de término agendada da reunião, em UTC. |
| **details.joinUrl** | A URL usada para ingressar na reunião. |
| **details.title** | O título da reunião. |
| **details.type** | O tipo da reunião (GroupCall, OneToOneCall, Adhoc, Broadcast, MeetNow, Recurring, Scheduled ou Unknown). |
| **conversation.isGroup** | Booliano que indica se a conversa tem mais de dois participantes. |
| **conversation.conversationType** | O tipo de conversa. |
| **conversation.id** | A ID de chat da reunião. |
| **organizer.id** | A ID de usuário do Organizador. |
| **organizer.aadObjectId** | A ID de objeto do Azure Active Directory do Organizador. |
| **organizer.tenantId** | A ID de locatário do Azure Active Directory do Organizador. |

No caso de tipo de reunião recorrente,

**startDate**: especifica a data para começar a aplicar o padrão. O valor de startDate deve corresponder ao valor de data da propriedade start no recurso de evento. Observe que a primeira ocorrência da reunião poderá não ocorrer nessa data se ela não se ajustar ao padrão.

**endDate**: especifica a data para parar de aplicar o padrão. Observe que a última ocorrência da reunião poderá não ocorrer nessa data se ela não se ajustar ao padrão.

## <a name="send-real-time-captions-api"></a>API de envio de legendas em tempo real

A API de envio de legendas em tempo real expõe um ponto de extremidade POST para legendas DE CART (conversão em tempo real) de acesso de comunicação do Teams, legendas ocultas com tipo humano. O conteúdo de texto enviado para esse ponto de extremidade aparece para os usuários finais em uma reunião do Teams quando eles têm legendas habilitadas.

### <a name="cart-url"></a>URL DO CART

Você pode obter a URL do CART para o ponto de extremidade POST na página **de opções da** Reunião em uma reunião do Teams. Para obter mais informações, consulte [legendas CART em uma reunião do Microsoft Teams](https://support.microsoft.com/office/use-cart-captions-in-a-microsoft-teams-meeting-human-generated-captions-2dd889e8-32a8-4582-98b8-6c96cf14eb47). Você não precisa modificar a URL do CART para usar legendas CART.

#### <a name="query-parameter"></a>Parâmetro de Consulta

A URL do CART inclui os seguintes parâmetros de consulta:

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|----|
|**meetingId**| Cadeia de caracteres | Sim |O identificador de reunião está disponível por meio do Bot Invoke e do SDK do Cliente do Teams. <br/>Por exemplo, meetingid=%7b%22tId%22%3a%2272f234bf-86f1-41af-91ab-2d7cd0321b47%22%2c%22oId%22%3a%22e071f268-4241-47f8-8cf3-fc6b84437f23%22%2c%22thId%22%3a%2219%3ameeting_NzJiMjNkMGQtYzk3NS00ZDI1LWJjN2QtMDgyODVhZmI3NzJj%40thread.v2%22%2c%22mId%22%3a%220%22%7d|
|**token**| Cadeia de caracteres | Sim |Token de autorização.<br/> Por exemplo, token=04751eac |

#### <a name="example"></a>Exemplo

```http
https://api.captions.office.microsoft.com/cartcaption?meetingid=%7b%22tId%22%3a%2272f234bf-86f1-41af-91ab-2d7cd0321b47%22%2c%22oId%22%3a%22e071f268-4241-47f8-8cf3-fc6b84437f23%22%2c%22thId%22%3a%2219%3ameeting_NzJiMjNkMGQtYzk3NS00ZDI1LWJjN2QtMDgyODVhZmI3NzJj%40thread.v2%22%2c%22mId%22%3a%220%22%7d&token=gjs44ra
```

### <a name="method"></a>Método

|Resource|Método|Descrição|
|----|----|----|
|/cartcaption|POSTAR|Manipular legendas para a reunião, que foi iniciada|

> [!NOTE]
> Verifique se o tipo de conteúdo para todas as solicitações é texto sem formatação com codificação UTF-8. O corpo da solicitação contém apenas legendas.

#### <a name="example"></a>Exemplo

```http
POST /cartcaption?meetingid=04751eac-30e6-47d9-9c3f-0b4ebe8e30d9&token=04751eac&lang=en-us HTTP/1.1
Host: api.captions.office.microsoft.com
Content-Type: text/plain
Content-Length: 22
Hello I’m Cortana, welcome to my meeting. 
```

> [!Note]  
> Cada solicitação POST gera uma nova linha de legendas. Para garantir que o usuário final tenha tempo suficiente para ler o conteúdo, limite cada corpo da solicitação POST a 80 a 120 caracteres.

### <a name="error-codes"></a>Códigos de erro

A tabela a seguir fornece os códigos de erro:

|Código de erro|Descrição|
|---|---|
| **400** | Solicitação incorreta. O corpo da resposta tem mais informações. Por exemplo, não de todos os parâmetros necessários apresentados.|
| **401** | Não autorizado. Token inválido ou expirado. Se você receber esse erro, gere uma nova URL do CART no Teams. |
| **404** | Reunião não encontrada ou não iniciada. Se você receber esse erro, certifique-se de iniciar a reunião e selecione iniciar legendas. Depois que as legendas forem habilitadas na reunião, você poderá começar a POSTing de legendas na reunião.|
| **500** |Erro de servidor interno. Para obter mais informações, [contate o suporte ou forneça comentários](../feedback.md).|

## <a name="share-app-content-to-stage-api"></a>Compartilhar conteúdo do aplicativo para preparar a API

A API `shareAppContentToStage` permite que você compartilhe partes específicas do seu aplicativo no estágio da reunião. A API está disponível por meio do SDK do cliente do Teams.

### <a name="prerequisite"></a>Pré-requisito

* Para usar a API `shareAppContentToStage`, você deve obter as permissões de RSC. No manifesto do aplicativo, configure a propriedade `authorization`, e `name` e `type` no campo `resourceSpecific`. Por exemplo:

    ```json
    "authorization": {
        "permissions": { 
        "resourceSpecific": [
        { 
        "name": "MeetingStage.Write.Chat",
        "type": "Delegated"
        }
        ]
    }
    }
    ```

* `appContentUrl` deve ser permitido pela matriz `validDomains` dentro de manifest.json; caso contrário, a API retornaria 501.

### <a name="query-parameter"></a>Parâmetro de consulta

A tabela a seguir inclui os parâmetros de consulta:

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**callback**| Cadeia de caracteres | Sim | O retorno de chamada contém dois parâmetros, erro e resultado. O *erro* pode conter um erro do tipo *SdkError* ou nulo quando o compartilhamento for bem-sucedido. O *resultado* pode conter um valor verdadeiro, no caso de um compartilhamento bem-sucedido ou nulo quando o compartilhamento falha.|
|**appContentURL**| Cadeia de caracteres | Sim | A URL que será compartilhada no estágio.|

### <a name="example"></a>Exemplo

```javascript
const appContentUrl = "https://www.bing.com/";

microsoftTeams.meeting.shareAppContentToStage((err, result) => {
    if (result) {
        // handle success
    }
    if (err) {
        // handle error
    }
}, appContentUrl);
```

### <a name="response-codes"></a>Códigos de resposta

A tabela a seguir fornece os códigos de resposta:

|Código da resposta|Descrição|
|---|---|
| **500** | Erro interno. |
| **501** | A API não tem suporte no contexto atual.|
| **1.000** | O aplicativo não tem permissões adequadas para permitir o compartilhamento em estágios.|

## <a name="get-app-content-stage-sharing-state-api"></a>Obter API de estado de compartilhamento do estágio de conteúdo do aplicativo

A API `getAppContentStageSharingState` permite que você busque informações sobre o compartilhamento de aplicativos no estágio da reunião.

### <a name="query-parameter"></a>Parâmetro de consulta

A tabela a seguir inclui o parâmetro de consulta:

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**callback**| Cadeia de caracteres | Sim | O retorno de chamada contém dois parâmetros, erro e resultado. O *erro* pode conter um erro do tipo *SdkError*, no caso de um erro, ou nulo quando o compartilhamento for bem-sucedido. O *resultado* pode conter um objeto `AppContentStageSharingState` indicando recuperação bem-sucedida ou nulo, indicando falha na recuperação.|

### <a name="example"></a>Exemplo

```javascript
microsoftTeams.meeting.getAppContentStageSharingState((err, result) => {
    if (result.isAppSharing) {
        // Indicates app has permission to share contents to meeting stage.
    }
});
```

O corpo da resposta JSON para `getAppContentStageSharingState` API é:

```json
{
   "isAppSharing":true
} 
```

### <a name="response-codes"></a>Códigos de resposta

A tabela a seguir fornece os códigos de resposta:

|Código da resposta|Descrição|
|---|---|
| **500** | Erro interno. |
| **501** | A API não tem suporte no contexto atual.|
| **1.000** | O aplicativo não tem permissões adequadas para permitir o compartilhamento em estágios.|

## <a name="get-app-content-stage-sharing-capabilities-api"></a>Obter a API de recursos de compartilhamento do estágio de conteúdo do aplicativo

A API `getAppContentStageSharingCapabilities` permite que você busque os recursos do aplicativo para compartilhamento no estágio de reunião.

### <a name="query-parameter"></a>Parâmetro de consulta

A tabela a seguir inclui o parâmetro de consulta:

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**callback**| Cadeia de caracteres | Sim | O retorno de chamada contém dois parâmetros, erro e resultado. O *erro* pode conter um erro do tipo *SdkError* ou nulo quando o compartilhamento for bem-sucedido. O resultado pode conter um objeto `AppContentStageSharingState` indicando recuperação bem-sucedida ou nulo, indicando falha na recuperação.|

### <a name="example"></a>Exemplo

```javascript
microsoftTeams.meeting.getAppContentStageSharingCapabilities((err, result) => {
    if (result.doesAppHaveSharePermission) {
        // Indicates app has permission to share contents to meeting stage.
    }
});
```

O corpo da resposta JSON para `getAppContentStageSharingCapabilities` API é:

```json
{
   "doesAppHaveSharePermission":true
} 
```

### <a name="response-codes"></a>Códigos de resposta

A tabela a seguir fornece os códigos de resposta:

|Código da resposta|Descrição|
|---|---|
| **500** | Erro interno. |
| **1000** | O aplicativo não tem permissões para permitir o compartilhamento em estágios.|

## <a name="get-real-time-teams-meeting-events-api"></a>Obter API de eventos de reunião do Teams em tempo real

> [!NOTE]
> Eventos de reunião do Teams em tempo real só têm suporte para reuniões agendadas.

O usuário pode receber eventos de reunião em tempo real. Assim que qualquer aplicativo é associado a uma reunião, a hora real de início e término da reunião é compartilhada com o bot. A hora real de início e término de uma reunião é diferente da hora de início e término agendada. A API de Detalhes da Reunião fornece a hora de início e término agendada. O evento fornece a hora real de início e término.

Você deve estar familiarizado com o objeto `TurnContext` disponível por meio do SDK do Bot. O objeto `Activity` em `TurnContext` contém a carga com a hora de início e término reais. Eventos de reunião em tempo real exigem uma ID de bot registrada da plataforma Teams. O bot pode receber automaticamente o evento de início ou término da reunião adicionando `ChannelMeeting.ReadBasic.Group` no manifesto.

### <a name="prerequisite"></a>Pré-requisito

O manifesto do aplicativo deve ter a propriedade `webApplicationInfo` para receber os eventos de início e término da reunião. Use os exemplos a seguir para configurar o manifesto:

<br>

<details>

<summary><b>Para o manifesto do aplicativo versão 1.12 e posterior</b></summary>

```json
"webApplicationInfo": {
    "id": "<bot id>",
    "resource": "https://RscPermission",
    },
"authorization": {
    "permissions": {
        "resourceSpecific": [
            {
                "name": "OnlineMeeting.ReadBasic.Chat",
                "type": "Application"
            }
        ]    
    }
}
 ```

<br>

</details>

<br>

<details>

<summary><b>Para o manifesto do aplicativo versão 1.11 e anterior</b></summary>

```json
"webApplicationInfo": {
    "id": "<bot id>",
    "resource": "https://RscPermission",
    "applicationPermissions": [
      "OnlineMeeting.ReadBasic.Chat"
    ]
}
 ```

<br>

</details>

### <a name="example-of-getting-meetingstartendeventvalue"></a>Exemplo de `MeetingStartEndEventvalue`

O bot recebe o evento por meio do manipulador `OnEventActivityAsync`. Para desserializar a carga JSON, um objeto de modelo é introduzido para obter os metadados de uma reunião. Os metadados de uma reunião estão na propriedade `value` no conteúdo do evento. O objeto de modelo `MeetingStartEndEventvalue` é criado, cujas variáveis de membro correspondem às chaves sob a propriedade `value` no conteúdo do evento.

> [!NOTE]
>
> * Obtenha a ID da reunião `turnContext.ChannelData`.
> * Não use a ID da conversa como ID da reunião.
> * Não use a ID de reunião do conteúdo de eventos de reunião `turncontext.activity.value`.

O código a seguir mostra como capturar os metadados de uma reunião que é `MeetingType`, `Title`, `Id`, `JoinUrl`, `StartTime` e `EndTime` de um evento de início/término da reunião:

Evento de Início da Reunião

```csharp
protected override async Task OnTeamsMeetingStartAsync(MeetingStartEventDetails meeting, ITurnContext<IEventActivity> turnContext, CancellationToken cancellationToken)
{
    await turnContext.SendActivityAsync(JsonConvert.SerializeObject(meeting));
}
```

Evento de Término da Reunião

```csharp
protected override async Task OnTeamsMeetingEndAsync(MeetingEndEventDetails meeting, ITurnContext<IEventActivity> turnContext, CancellationToken cancellationToken)
{
    await turnContext.SendActivityAsync(JsonConvert.SerializeObject(meeting));
}
```

### <a name="example-of-meeting-start-event-payload"></a>Exemplo de conteúdo do evento de início da reunião

O código a seguir fornece um exemplo de conteúdo do evento de início da reunião:

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

### <a name="example-of-meeting-end-event-payload"></a>Exemplo de conteúdo do evento final da reunião

O código a seguir fornece um exemplo de conteúdo de evento final de reunião:

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

| Nome da propriedade | Descrição |
|---|---|
| **name** | Nome do usuário.|
| **type** | Tipo de atividade. |
| **timestamp** | Data e hora locais da mensagem, expressas no formato ISO-8601. |
| **id** | ID da atividade. |
| **channelId** | Canal ao qual essa atividade está associada. |
| **Serviceurl** | URL do serviço em que as respostas a essa atividade devem ser enviadas. |
| **from.id** | ID do usuário que enviou a solicitação. |
| **from.aadObjectId** | ID de objeto do Azure Active Directory do usuário que enviou a solicitação. |
| **conversation.isGroup** | Booliano que indica se a conversa tem mais de dois participantes. |
| **conversation.tenantId** | ID do locatário do Azure Active Directory da conversa ou reunião. |
| **conversation.id** | A ID de chat da reunião. |
| **recipient.id** | ID do usuário que recebe a solicitação. |
| **recipient.name** | Nome do usuário que recebe a solicitação. |
| **entities.locale** | que contém metadados sobre localidade. |
| **entities.country** | que contém metadados sobre o país. |
| **entities.type** | que contém metadados sobre o cliente. |
| **channelData.tenant.id** | Locatário do Azure Active Directory. |
| **channelData.source** | O nome de origem de onde o evento é acionado ou invocado. |
| **channelData.meeting.id** | A ID padrão associada à reunião. |
| **Valor. MeetingType** | O tipo de reunião. |
| **Valor. Título** | O assunto da reunião. |
| **Valor. Id** | A ID padrão associada à reunião. |
| **Valor. JoinUrl** | A URL de ingresso da reunião. |
| **Valor. Starttime** | A hora de início da reunião em UTC. |
| **Valor. Endtime** | A hora de término da reunião em UTC. |
| **locale**| A localidade da mensagem definida pelo cliente. |

## <a name="get-incoming-audio-state"></a>Obter estado de áudio de entrada

A `getIncomingClientAudioState` API permite que um aplicativo obtenha a configuração de estado de áudio de entrada para o usuário da reunião. A API está disponível por meio do SDK do cliente do Teams.

> [!NOTE]
>
> * No `getIncomingClientAudioState` momento, a API para dispositivos móveis está disponível na [Versão Prévia do Desenvolvedor Público](../resources/dev-preview/developer-preview-intro.md).
> * O consentimento específico do recurso está disponível para o manifesto versão 1.12 e versões posteriores, portanto, essa API não funciona para o manifesto versão 1.11 e versões anteriores.

### <a name="manifest"></a>Manifesto

```JSON
"authorization": {
    "permissions": {
      "resourceSpecific": [
        {
          "name": "OnlineMeetingParticipant.ToggleIncomingAudio.Chat",
          "type": "Delegated"
        }
      ]
    }
  }
```
  
### <a name="example"></a>Exemplo

```javascript
callback = (errcode, result) => {
        if (errcode) {
            // Handle error code
        }
        else {
            // Handle success code
        }
    }

microsoftTeams.meeting.getIncomingClientAudioState(this.callback)
```
### <a name="query-parameter"></a>Parâmetro de consulta

A tabela a seguir inclui o parâmetro de consulta:

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**callback**| Cadeia de caracteres | Sim | O retorno de chamada contém dois parâmetros `error` e `result`. O *erro* pode conter um tipo de erro ou `SdkError` quando `null` a busca de áudio for bem-sucedida. O *resultado* pode conter valor verdadeiro ou falso quando a busca de áudio for bem-sucedida ou nula quando a busca de áudio falhar. O áudio de entrada será ativado se o resultado for true e não for permutado se o resultado for false. |
  
### <a name="response-codes"></a>Códigos de resposta

A tabela a seguir fornece os códigos de resposta:

|Código da resposta|Descrição|
|---|---|
| **500** | Erro interno. |
| **501** | A API não tem suporte no contexto atual.|
| **1.000** | O aplicativo não tem permissões adequadas para permitir o compartilhamento em estágios.|

## <a name="toggle-incoming-audio"></a>Alternar áudio de entrada

A `toggleIncomingClientAudio` API permite que um aplicativo alterne a configuração de estado de áudio de entrada para o usuário da reunião de mudo para mudo ou vice-versa. A API está disponível por meio do SDK do cliente do Teams.

> [!NOTE]
>
> * No `toggleIncomingClientAudio` momento, a API para dispositivos móveis está disponível na [Versão Prévia do Desenvolvedor Público](../resources/dev-preview/developer-preview-intro.md).
> * O consentimento específico do recurso está disponível para o manifesto versão 1.12 e versões posteriores, portanto, essa API não funciona para o manifesto versão 1.11 e versões anteriores.

### <a name="manifest"></a>Manifesto

```JSON
"authorization": {
    "permissions": {
        "resourceSpecific": [
            {
                "name": "OnlineMeetingParticipant.ToggleIncomingAudio.Chat",
                "type": "Delegated"
            }
        ]
    }
}
```
 
### <a name="example"></a>Exemplo

```javascript
callback = (error, result) => {
        if (error) {
            // Handle error code
        }
        else {
            // Handle success code
        }
    }

microsoftTeams.meeting.toggleIncomingClientAudio(this.callback)
```
  
### <a name="query-parameter"></a>Parâmetro de consulta

A tabela a seguir inclui o parâmetro de consulta:

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**callback**| Cadeia de caracteres | Sim | O retorno de chamada contém dois parâmetros `error` e `result`. O *erro* pode conter um tipo de erro `SdkError` ou `null` quando a alternância for bem-sucedida. O *resultado* pode conter valor verdadeiro ou falso, quando a alternância for bem-sucedida ou nula quando a alternância falhar. O áudio de entrada será ativado se o resultado for true e não for permutado se o resultado for false.
  
### <a name="response-code"></a>Código da resposta

A tabela a seguir fornece os códigos de resposta:

|Código da resposta|Descrição|
|---|---|
| **500** | Erro interno. |
| **501** | A API não tem suporte no contexto atual.|
| **1.000** | O aplicativo não tem permissões adequadas para permitir o compartilhamento em estágios.|

## <a name="code-sample"></a>Exemplo de código

|Nome do exemplo | Descrição | C# | Node.js |
|----------------|-----------------|--------------|--------------|
| Extensibilidade de reuniões | Exemplo de extensibilidade de reunião do Teams para passar tokens. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/nodejs) |
| Bot de bolha de conteúdo de reunião | Exemplo de extensibilidade de reunião do Teams para interagir com o bot de bolha de conteúdo em uma reunião. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/csharp) |  [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/nodejs)|
| MeetingSidePanel de reunião | Exemplo de extensibilidade de reunião do Teams para interagir com o painel lateral na reunião. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/csharp) | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/nodejs)|
| Guia Detalhes na Reunião | Exemplo de extensibilidade de reunião do Teams para interagir com a guia Detalhes na reunião. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-details-tab/csharp) | [Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-details-tab/nodejs)|
|Exemplo de eventos de reunião|Aplicativo de exemplo para mostrar eventos de reunião do Teams em tempo real|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-events/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-events/nodejs)|
|Exemplo de convite de reunião|Aplicativo de exemplo para mostrar a experiência de reunião para cenário de recrutamento.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meeting-recruitment-app/csharp)|[Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meeting-recruitment-app/nodejs)|
|Instalação de aplicativo usando código QR|Aplicativo de exemplo que gera o código QR e instala o aplicativo usando o código QR|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-installation-using-qr-code/csharp)|[Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-installation-using-qr-code/nodejs)|

## <a name="see-also"></a>Confira também

* [Fluxo de autenticação de equipes para guias](../tabs/how-to/authentication/auth-flow-tab.md)
* [Aplicativos para reuniões do Teams](teams-apps-in-meetings.md)
* [SDK do Live Share](teams-live-share-overview.md)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Ative e configure seus aplicativos para reuniões do Teams](enable-and-configure-your-app-for-teams-meetings.md)
