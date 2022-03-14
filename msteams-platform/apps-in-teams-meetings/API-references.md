---
title: Referências à API de aplicativos de reunião
author: surbhigupta
description: Identificar as referências da API de aplicativos de reunião com exemplos e exemplos de código
ms.topic: conceptual
ms.author: lajanuar
ms.localizationpriority: medium
keywords: consulta de sinal de notificação de contexto de usuário de api de usuário de reuniões de aplicativos do teams
ms.openlocfilehash: 150a0bec1d8566392914ffeaf4990de21e3ec7de
ms.sourcegitcommit: ca902f505a125641c379a917ee745ab418bd1ce6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2022
ms.locfileid: "63464249"
---
# <a name="meeting-apps-api-references"></a>Referências à API de aplicativos de reunião

A extensibilidade da reunião fornece APIs para aprimorar a experiência de reunião. Você pode executar o seguinte com a ajuda das APIs listadas:

* Crie aplicativos ou integre aplicativos existentes ao ciclo de vida da reunião.
* Use APIs para tornar seu aplicativo ciente da reunião.
* Selecione APIs necessárias para melhorar a experiência de reunião.

> [!NOTE]
> Use Teams [SDK JavaScript](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) (*versão*: 1.10 e posterior) para que o SSO funcione no painel do lado da reunião.

A tabela a seguir fornece uma lista de APIs disponíveis nos SDKs Microsoft Teams Client (MSTC) e Microsoft Bot Framework (MSBF) :

|Método| Descrição| Source|
|---|---|----|
|[**Obter contexto do usuário**](#get-user-context-api)| Obter informações contextuais para exibir conteúdo relevante em uma Teams guia.| MSTC SDK|
|[**Obter participante**](#get-participant-api)| Buscar informações do participante por meio da ID da reunião e da ID do participante. |MSBF SDK|
|[**Enviar notificação de reunião**](#send-an-in-meeting-notification)| Forneça sinais de reunião usando a API de notificação de conversa existente para chat usuário-bot e permite notificar a ação do usuário que mostra uma notificação na reunião. |MSBF SDK|
|[**Obter detalhes da reunião**](#get-meeting-details-api)| Obter metadados estáticos de uma reunião. |MSBF SDK |
|[**Enviar legendas em tempo real**](#send-real-time-captions-api)| Envie legendas em tempo real para uma reunião contínua. |MSTC SDK|
|[**Compartilhar conteúdo do aplicativo em estágio**](#share-app-content-to-stage-api)| Compartilhe partes específicas do aplicativo para o estágio de reunião do painel do lado do aplicativo em uma reunião. |MSTC SDK|
|[**Obter estado de compartilhamento de estágio de conteúdo do aplicativo**](#get-app-content-stage-sharing-state-api)| Busque informações sobre o estado de compartilhamento do aplicativo no estágio de reunião. |MSTC SDK|
|[**Obter recursos de compartilhamento de estágio de conteúdo do aplicativo**](#get-app-content-stage-sharing-capabilities-api)| Busque os recursos do aplicativo para compartilhamento no estágio de reunião. |MSTC SDK|
|[**Obter eventos de reunião Teams em tempo real**](#get-real-time-teams-meeting-events-api)|Buscar eventos de reunião em tempo real, como início e hora de término reais.| MSBF SDK|

## <a name="get-user-context-api"></a>Obter API de contexto do usuário

Para identificar e recuperar informações contextuais para o conteúdo da guia, consulte obter contexto para sua guia [Teams](../tabs/how-to/access-teams-context.md#get-context-by-using-the-microsoft-teams-javascript-library). `meetingId` É usada por uma guia em execução no contexto da reunião e é adicionada para a carga de resposta.

## <a name="get-participant-api"></a>Obter API do participante

A `GetParticipant` API deve ter um registro de bot e uma ID para gerar tokens de auth. Para obter mais informações, [consulte registro de bot e ID](../build-your-first-app/build-bot.md).

> [!NOTE]
>
> * Não armazenar em cache as funções do participante, pois o organizador da reunião pode alterar as funções a qualquer momento.
> * Atualmente, a `GetParticipant` API só tem suporte para listas de distribuições ou listas com menos de 350 participantes.

### <a name="query-parameters"></a>Parâmetros de consulta

> [!TIP]
> Obter IDs de participantes e IDs de locatário na [autenticação SSO da guia](../tabs/how-to/authentication/auth-aad-sso.md).

A `Meeting` API deve ter `meetingId`parâmetros , `participantId`e `tenantId` como URL. Os parâmetros estão disponíveis como parte do SDK do cliente Teams atividade de bot.

A tabela a seguir inclui os parâmetros de consulta:

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**meetingId**| Cadeia de caracteres | Sim | O identificador de reunião está disponível por meio de Bot Invoke e Teams Client SDK.|
|**participantId**| Cadeia de caracteres | Sim | A ID do participante é a ID do usuário. Ele está disponível em Tab SSO, Bot Invoke e Teams Client SDK. É recomendável obter uma ID de participante do SSO da guia. |
|**tenantId**| Cadeia de caracteres | Sim | A ID do locatário é necessária para os usuários do locatário. Ele está disponível em Tab SSO, Bot Invoke e Teams Client SDK. É recomendável obter uma ID de locatário do SSO de tabulação. |

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
      "isGroup":true
   }
}
```

---

### <a name="response-codes"></a>Códigos de resposta

A tabela a seguir fornece os códigos de resposta:

|Código da resposta|Descrição|
|---|---|
| **403** | Obter informações do participante não é compartilhado com o aplicativo. Se o aplicativo não estiver instalado na reunião, ele disparará a resposta de erro 403. Se o administrador do locatário desabilitar ou bloquear o aplicativo durante a migração do site ao vivo, ele disparará a resposta de erro 403. |
| **200** | As informações do participante são recuperadas com êxito.|
| **401** | O aplicativo responde com um token inválido.|
| **404** | A reunião expirou ou os participantes não estão disponíveis.|

## <a name="send-an-in-meeting-notification"></a>Enviar uma notificação em reunião

Todos os usuários em uma reunião recebem as notificações enviadas por meio da carga de notificação na reunião. A carga de notificação na reunião dispara uma notificação na reunião e permite que você forneça sinais de reunião que são entregues usando a API de notificação de conversa existente para chat de usuário-bot. Você pode enviar uma notificação em reunião com base na ação do usuário. A carga está disponível por meio dos Serviços bot.

> [!NOTE]
>
> * Quando uma notificação em reunião é invocada, o conteúdo é apresentado como uma mensagem de chat.
> * Atualmente, não há suporte para o envio de notificações direcionadas e suporte para webapp.
> * Você deve invocar [a função submitTask()](../task-modules-and-cards/task-modules/task-modules-bots.md#submit-the-result-of-a-task-module) para descartar automaticamente depois que um usuário realizar uma ação no visualização da Web. Esse é um requisito para envio de aplicativo. Para obter mais informações, [consulte Teams módulo de tarefa do SDK](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).
> * Se você quiser que seu aplicativo suporte usuários anônimos, `from.id` a carga inicial de solicitação de invocação deve depender dos metadados `from` de solicitação no objeto, não de `from.aadObjectId` metadados de solicitação. `from.id`é a ID do usuário e `from.aadObjectId` é a ID Microsoft Azure Active Directory (Azure AD) do usuário. Para obter mais informações, [consulte using task modules in tabs](../task-modules-and-cards/task-modules/task-modules-tabs.md) e [create and send the task module](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).

### <a name="query-parameter"></a>Parâmetro de consulta

A tabela a seguir inclui os parâmetros de consulta:

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**conversationId**| String | Sim | O identificador de conversa está disponível como parte de Bot Invoke. |

### <a name="examples"></a>Exemplos

O `Bot ID` é declarado no manifesto e o bot recebe um objeto de resultado.

> [!NOTE]
>
> * O `completionBotId` parâmetro do é `externalResourceUrl` opcional no exemplo de carga solicitada.
> * Os `externalResourceUrl` parâmetros de largura e altura devem estar em pixels. Para obter mais informações, consulte [diretrizes de design](design/designing-apps-in-meetings.md).
> * A URL é a página, que é carregada como `<iframe>` na notificação em reunião. O domínio deve estar na matriz dos `validDomains` aplicativos no manifesto do aplicativo.

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
            "externalResourceUrl": "https://teams.microsoft.com/l/bubble/APP_ID?url=<url>&height=<height>&width=<width>&title=<title>&completionBotId=BOT_APP_ID"
        }
    },
    "replyToId": "1493070356924"
}
```

---

### <a name="response-codes"></a>Códigos de resposta

A tabela a seguir inclui os códigos de resposta:

|Código da resposta|Descrição|
|---|---|
| **201** | A atividade com sinal é enviada com êxito. |
| **401** | O aplicativo responde com um token inválido. |
| **403** | O aplicativo não consegue enviar o sinal. O código de resposta 403 pode ocorrer por vários motivos, como o administrador do locatário desabilita e bloqueia o aplicativo durante a migração do site ao vivo. Nesse caso, a carga contém uma mensagem de erro detalhada. |
| **404** | O chat de reunião não existe. |

## <a name="get-meeting-details-api"></a>Obter API de detalhes da reunião

A API Detalhes da Reunião permite que seu aplicativo receba os metadados estáticos de uma reunião. Os metadados fornece pontos de dados que não mudam dinamicamente. A API está disponível por meio dos Serviços bot. Atualmente, reuniões agendadas ou recorrentes privadas e reuniões agendadas ou recorrentes no canal suportam a API com permissões RSC diferentes, respectivamente.

A `Meeting Details` API deve ter um registro de bot e uma ID de bot. Requer o SDK de Bot para obter `TurnContext`. Para usar a API de Detalhes da Reunião, você deve obter uma permissão RSC diferente com base no escopo de qualquer reunião, como reunião privada ou reunião de canal.

### <a name="prerequisite"></a>Pré-requisito

Para usar a API de Detalhes da Reunião, você deve obter uma permissão RSC diferente com base no escopo de qualquer reunião, como reunião privada ou reunião de canal.

<br>

<details>

<summary><b>Para manifesto do aplicativo versão 1.12</b></summary>

Use o exemplo a seguir para configurar as propriedades e o manifesto do seu `webApplicationInfo` `authorization` aplicativo para qualquer reunião privada:

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

Use o exemplo a seguir para configurar as propriedades e o manifesto do seu aplicativo `webApplicationInfo` `authorization` para qualquer reunião de canal:

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

<summary><b>Para manifesto do aplicativo versão 1.11 ou anterior</b></summary>

Use o exemplo a seguir para configurar a propriedade do manifesto do aplicativo `webApplicationInfo` para qualquer reunião privada:

```json
"webApplicationInfo": {
    "id": "<bot id>",
    "resource": "https://RscPermission",
    "applicationPermissions": [
      "OnlineMeeting.ReadBasic.Chat"
    ]
}
 ```

Use o exemplo a seguir para configurar a propriedade do manifesto do aplicativo `webApplicationInfo` para qualquer reunião de canal:

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
> O bot pode receber eventos de `ChannelMeeting.ReadBasic.Group` início de reunião ou término automaticamente de todas as reuniões criadas em todos os canais adicionando ao manifesto para permissão RSC.

### <a name="query-parameter"></a>Parâmetro de consulta

A tabela a seguir lista o parâmetro de consulta:

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**meetingId**| Cadeia de caracteres | Sim | O identificador de reunião está disponível por meio de Bot Invoke e Teams Client SDK. |

### <a name="example"></a>Exemplo

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
            "conversationType": "groupchat", 
            "id": "meeting chat ID" 
    }, 
    "organizer": { 
        "id": "<organizer user ID>", 
        "aadObjectId": "<AAD ID>", 
        "tenantId": "<Tenant ID>" 
    }
} 
```

---

## <a name="send-real-time-captions-api"></a>API de envio de legendas em tempo real

A API de legendas de envio em tempo real expõe um ponto de extremidade POST para Microsoft Teams legendas de conversão em tempo real de acesso à comunicação (CART), legendas fechadas digitadas por humanos. O conteúdo de texto enviado para esse ponto de extremidade aparece para usuários finais em uma reunião Microsoft Teams quando eles têm legendas habilitadas.

### <a name="cart-url"></a>CART URL

Você pode obter a URL DO CART para o ponto de extremidade POST na página **Opções** de reunião em uma reunião Microsoft Teams reunião. Para obter mais informações, [consulte legendas CART em uma Microsoft Teams reunião](https://support.microsoft.com/office/use-cart-captions-in-a-microsoft-teams-meeting-human-generated-captions-2dd889e8-32a8-4582-98b8-6c96cf14eb47). Você não precisa modificar a URL CART para usar legendas CART.

#### <a name="query-parameter"></a>Parâmetro Query

A URL cart inclui os seguintes parâmetros de consulta:

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|----|
|**meetingId**| Cadeia de caracteres | Sim |O identificador de reunião está disponível por meio de Bot Invoke e Teams Client SDK. <br/>Por exemplo, meetingid=%7b%22tId%22%3a%2272f234bf-86f1-41af-91ab-2d7cd0321b47%22%2c%22oId%22%3a%22e071f268-4241-47f8-8cf3-fc6b84437f23%22%2c%22thId%22%3a%2219%3ameeting_NzJiMjNkMGQtYzk3NS00ZDI1LWJjN2QtMDgyODVhZmI3NzJj%40thread.v2%22%2c%22mId%22%3a%220%220%22%7d|
|**token**| Cadeia de caracteres | Sim |Token de autorização.<br/> Por exemplo, token=04751eac |

#### <a name="example"></a>Exemplo

```http
https://api.captions.office.microsoft.com/cartcaption?meetingid=%7b%22tId%22%3a%2272f234bf-86f1-41af-91ab-2d7cd0321b47%22%2c%22oId%22%3a%22e071f268-4241-47f8-8cf3-fc6b84437f23%22%2c%22thId%22%3a%2219%3ameeting_NzJiMjNkMGQtYzk3NS00ZDI1LWJjN2QtMDgyODVhZmI3NzJj%40thread.v2%22%2c%22mId%22%3a%220%22%7d&token=gjs44ra
```

### <a name="method"></a>Método

|Recurso|Método|Descrição|
|----|----|----|
|/cartcaption|POSTAR|Manipular legendas para reunião, que foi iniciada|

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

A tabela a seguir fornece os códigos de erro:

|Código de erro|Descrição|
|---|---|
| **400** | Solicitação ruim. O corpo da resposta tem mais informações. Por exemplo, não de todos os parâmetros necessários apresentados.|
| **401** | Não autorizado. Token ruim ou expirado. Se você receber esse erro, gere uma nova URL cart no Teams. |
| **404** | Reunião não encontrada ou não iniciada. Se você receber esse erro, certifique-se de iniciar a reunião e selecione iniciar legendas. Depois que as legendas são habilitadas na reunião, você pode começar a POSTing legendas na reunião.|
| **500** |Erro de servidor interno. Para obter mais informações, [contate o suporte ou forneça comentários](../feedback.md).|

## <a name="share-app-content-to-stage-api"></a>Compartilhar conteúdo do aplicativo para a API de estágio

A `shareAppContentToStage` API permite que você compartilhe partes específicas do seu aplicativo para o estágio de reunião. A API está disponível por meio do SDK Teams cliente.

### <a name="prerequisite"></a>Pré-requisito

*  Para usar a `shareAppContentToStage` API, você deve obter as permissões RSC. No manifesto do aplicativo, configure a `authorization` propriedade e o `name` e `type` no `resourceSpecific` campo. Por exemplo:

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
*  `appContentUrl` deve ser permitido pela `validDomains` matriz dentro de manifest.json, senão a API retornaria 501.

### <a name="query-parameter"></a>Parâmetro de consulta

A tabela a seguir inclui os parâmetros de consulta:

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**callback**| Cadeia de caracteres | Sim | O retorno de chamada contém dois parâmetros, erro e resultado. O *erro* pode conter um erro do tipo *SdkError* ou nulo quando o compartilhamento for bem-sucedido. O *resultado* pode conter um valor verdadeiro, no caso de um compartilhamento bem-sucedido ou nulo quando o compartilhamento falhar.|
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
| **1000** | O aplicativo não tem permissões adequadas para permitir o compartilhamento em estágios.|

## <a name="get-app-content-stage-sharing-state-api"></a>Obter API de estado de compartilhamento de estágio de conteúdo do aplicativo

A `getAppContentStageSharingState` API permite que você busque informações sobre o compartilhamento de aplicativos no estágio de reunião.

### <a name="query-parameter"></a>Parâmetro de consulta

A tabela a seguir inclui os parâmetros de consulta:

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**callback**| Cadeia de caracteres | Sim | O retorno de chamada contém dois parâmetros, erro e resultado. O *erro* pode conter um erro do tipo *SdkError*, no caso de um erro, ou nulo quando o compartilhamento é bem-sucedido. O *resultado* pode conter um objeto `AppContentStageSharingState` , indicando recuperação bem-sucedida ou nulo, indicando recuperação com falha.|

### <a name="example"></a>Exemplo

```javascript
microsoftTeams.meeting.getAppContentStageSharingState((err, result) => {
    if (result.isAppSharing) {
        // Indicates app has permission to share contents to meeting stage.
    }
});
```

O corpo da resposta JSON para a `getAppContentStageSharingState` API é:

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
| **1000** | O aplicativo não tem permissões adequadas para permitir o compartilhamento em estágios.|

## <a name="get-app-content-stage-sharing-capabilities-api"></a>Obter API de recursos de compartilhamento de estágio de conteúdo do aplicativo

A `getAppContentStageSharingCapabilities` API permite que você busque os recursos do aplicativo para compartilhamento no estágio de reunião.

### <a name="query-parameter"></a>Parâmetro de consulta

A tabela a seguir inclui os parâmetros de consulta:

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**callback**| Cadeia de caracteres | Sim | O retorno de chamada contém dois parâmetros, erro e resultado. O *erro* pode conter um erro do tipo *SdkError* ou nulo quando o compartilhamento for bem-sucedido. O resultado pode conter um objeto `AppContentStageSharingState` , indicando recuperação bem-sucedida ou nulo, indicando recuperação com falha.|

### <a name="example"></a>Exemplo

```javascript
microsoftTeams.meeting.getAppContentStageSharingCapabilities((err, result) => {
    if (result.doesAppHaveSharePermission) {
        // Indicates app has permission to share contents to meeting stage.
    }
});
```

O corpo de resposta JSON para `getAppContentStageSharingCapabilities` API é:

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

## <a name="get-real-time-teams-meeting-events-api"></a>Obter API de eventos de reunião Teams em tempo real

O usuário pode receber eventos de reunião em tempo real. Assim que qualquer aplicativo é associado a uma reunião, o início e a hora de término reais da reunião são compartilhados com o bot. A hora real de início e término de uma reunião é diferente da hora de início e término agendada. A API De Detalhes da Reunião fornece a hora de início e término agendada. O evento fornece a hora real de início e término.

Você deve estar familiarizado com o `TurnContext` objeto disponível por meio do SDK bot. O `Activity` objeto em `TurnContext` contém a carga com o início e a hora de término reais. Os eventos de reunião em tempo real exigem uma ID de bot registrada na plataforma Teams. O bot pode receber automaticamente o evento inicial ou final da reunião adicionando `ChannelMeeting.ReadBasic.Group` no manifesto.

### <a name="prerequisite"></a>Pré-requisito

O manifesto do aplicativo deve ter a `webApplicationInfo` propriedade para receber os eventos de início e término da reunião. Use os exemplos a seguir para configurar seu manifesto:

<br>

<details>

<summary><b>Para manifesto do aplicativo versão 1.12</b></summary>

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

<summary><b>Para manifesto do aplicativo versão 1.11 ou anterior</b></summary>

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

### <a name="example-of-getting-meetingstartendeventvalue"></a>Exemplo de obter `MeetingStartEndEventvalue`

O bot recebe evento por meio do `OnEventActivityAsync` manipulador. Para desserializar a carga JSON, um objeto modelo é introduzido para obter os metadados de uma reunião. Os metadados de uma reunião estão na `value` propriedade na carga de eventos. O `MeetingStartEndEventvalue` objeto model é criado, cujas variáveis de membro correspondem às chaves sob a `value` propriedade na carga do evento.

> [!NOTE]
>
> * Obter a ID da reunião de `turnContext.ChannelData`.
> * Não use a ID da conversa como ID da reunião.
> * Não use a ID da reunião do carregamento de eventos de reunião `turncontext.activity.value`.

O código a seguir mostra como capturar os metadados `MeetingType`de uma reunião que é , `Id``Title`, , `JoinUrl`, e `EndTime` `StartTime`de um evento de início/término de reunião:

Evento Início da Reunião

```csharp
protected override async Task OnTeamsMeetingStartAsync(MeetingStartEventDetails meeting, ITurnContext<IEventActivity> turnContext, CancellationToken cancellationToken)
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

## <a name="code-sample"></a>Exemplo de código

|Nome do exemplo | Descrição | C# | Node.js |
|----------------|-----------------|--------------|--------------|
| Extensibilidade de reuniões | Microsoft Teams exemplo de extensibilidade de reunião para tokens de passagem. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/nodejs) |
| Bot de bolha de conteúdo de reunião | Microsoft Teams exemplo de extensibilidade de reunião para interagir com o bot de bolha de conteúdo em uma reunião. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/csharp) |  [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/nodejs)|
| Meeting meetingSidePanel | Microsoft Teams exemplo de extensibilidade de reunião para interagir com o painel lateral na reunião. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/nodejs)|
| Guia Detalhes na Reunião | Microsoft Teams exemplo de extensibilidade de reunião para interagir com a Guia detalhes na reunião. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-details-tab/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-details-tab/nodejs)|
|Exemplo de eventos de reunião|Exemplo de aplicativo para mostrar eventos de reunião Teams reunião em tempo real|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-events/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-events/nodejs)|
|Exemplo de recrutamento de reunião|Exemplo de aplicativo para mostrar a experiência de reunião para cenário de recrutamento.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meeting-recruitment-app/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meeting-recruitment-app/nodejs)|
|Instalação de aplicativo usando código QR|Exemplo de aplicativo que gera o código QR e instala o aplicativo usando o código QR|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-installation-using-qr-code/csharp)|[Exibir](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-installation-using-qr-code/nodejs)|

## <a name="see-also"></a>Confira também

* [Teams fluxo de autenticação para guias](../tabs/how-to/authentication/auth-flow-tab.md)
* [Aplicativos para reuniões do Teams](teams-apps-in-meetings.md)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Habilitar e configurar seus aplicativos para Teams reuniões](enable-and-configure-your-app-for-teams-meetings.md)
