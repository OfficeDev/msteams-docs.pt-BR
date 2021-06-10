---
title: Pré-requisitos e referências de API para aplicativos de reuniões do Teams
author: laujan
description: Trabalhar com aplicativos para Teams reuniões
ms.topic: conceptual
ms.author: lajanuar
localization_priority: Normal
keywords: api de função de participante de reuniões de aplicativos do teams
ms.openlocfilehash: f42e827801e21bbd039f52dbb685d4559ae5cf81
ms.sourcegitcommit: 37325179a532897fafbe827dcf9a7ca5fa5e7d0b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2021
ms.locfileid: "52853505"
---
# <a name="prerequisites-and-api-references-for-apps-in-teams-meetings"></a>Pré-requisitos e referências de API para aplicativos de reuniões do Teams

Para expandir os recursos de seus aplicativos no ciclo de vida da reunião, Teams permite que você trabalhe com aplicativos para Teams reuniões. Você deve passar pelos pré-requisitos e usar as referências da API de aplicativos de reunião para aprimorar a experiência de reunião.

## <a name="prerequisites"></a>Pré-requisitos

Antes de trabalhar com aplicativos para Teams reuniões, você deve ter uma compreensão do seguinte:

* Você deve ter conhecimento de como desenvolver Teams aplicativos. Para obter mais informações, [consulte Teams desenvolvimento de aplicativos](../overview.md).

* Você deve atualizar o manifesto Teams aplicativo para indicar que o aplicativo está disponível para reuniões. Para obter mais informações, consulte [manifesto do aplicativo](enable-and-configure-your-app-for-teams-meetings.md#update-your-app-manifest).

* Seu aplicativo deve dar suporte a guias configuráveis no escopo de groupchat, para que seu aplicativo funcione no ciclo de vida da reunião como uma guia. Para obter mais informações, consulte [groupchat scope](../resources/schema/manifest-schema.md#configurabletabs) and [build a group tab](../build-your-first-app/build-channel-tab.md).

* Você deve seguir as diretrizes gerais Teams de design de guia para cenários pré e pós-reunião. Para experiências durante as reuniões, consulte a guia na reunião e as diretrizes de design da caixa de diálogo na reunião. Para obter mais informações, [consulte Teams](../tabs/design/tabs.md)diretrizes de design de guia, diretrizes de [design](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab)de guia na reunião e diretrizes de design de caixa de diálogo [na reunião.](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)

* Você deve dar suporte ao escopo para habilitar seu aplicativo em chats de `groupchat` pré-reunião e pós-reunião. Com a experiência do aplicativo de pré-reunião, você pode encontrar e adicionar aplicativos de reunião e realizar tarefas de pré-reunião. Com a experiência do aplicativo pós-reunião, você pode exibir os resultados da reunião, como resultados da pesquisa ou comentários.

* Os parâmetros de URL da API de reunião `meetingId` devem ter , e `userId` `tenantId` . Eles estão disponíveis como parte do SDK do cliente Teams atividade de bot. Além disso, você pode recuperar informações confiáveis para a ID do usuário e a ID do locatário usando [a autenticação SSO da guia](../tabs/how-to/authentication/auth-aad-sso.md).

* A `GetParticipant` API deve ter um registro de bot e uma ID para gerar tokens de auth. Para obter mais informações, [consulte registro de bot e ID](../build-your-first-app/build-bot.md).

* Para que seu aplicativo seja atualizado em tempo real, ele deve estar atualizado com base nas atividades do evento na reunião. Esses eventos podem estar dentro da caixa de diálogo na reunião e em outros estágios no ciclo de vida da reunião. Para a caixa de diálogo na reunião, consulte o parâmetro completion `bot Id` na `NotificationSignal` API.

Depois de passar pelos pré-requisitos, você pode usar as referências de API de aplicativos de reunião e isso permite acessar informações usando atributos e exibir `GetUserContext` `GetParticipant` conteúdo `NotificationSignal` relevante.

## <a name="meeting-apps-api-references"></a>Referências à API de aplicativos de reunião

As novas extensibilidades de reunião fornecem APIs que transformam a experiência de reunião. Com esse novo recurso, você pode criar aplicativos ou integrar aplicativos existentes no ciclo de vida da reunião. Você pode usar as APIs para tornar seu aplicativo ciente da reunião. Você pode escolher quais APIs deseja usar para aprimorar a experiência de reunião.

A tabela a seguir fornece uma lista dessas APIs:

|API|Descrição|Solicitação|Source|
|---|---|----|---|
|**GetUserContext**| Essa API permite que você receba informações contextuais para exibir conteúdo relevante em Teams guia. |_**microsoftTeams.getContext( ( ) => { /*...* / } )**_|Microsoft Teams SDK do cliente|
|**GetParticipant**| Essa API permite que um bot busque informações dos participantes por meio da ID da reunião e da ID do participante. |**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_ |Microsoft Bot Framework SDK|
|**NotificationSignal** | Essa API permite que você forneça sinais de reunião que são entregues usando a API de notificação de conversa existente para chat de usuário-bot. Ele permite sinalizar com base na ação do usuário que mostra uma caixa de diálogo na reunião. |**POST** _**/v3/conversations/{conversationId}/activities**_|Microsoft Bot Framework SDK|

### <a name="getusercontext-api"></a>GetUserContext API

Para identificar e recuperar informações contextuais para o conteúdo da guia, consulte [obter contexto para](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library)sua Teams guia . `meetingId`é usado por uma guia ao ser executado no contexto da reunião e é adicionado para a carga de resposta.

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
|**participantId**| Cadeia de caracteres | Sim | A ID do participante é a ID do usuário. Ele está disponível em Tab SSO, Bot Invoke e Teams Client SDK. É recomendável obter uma ID do participante no SSO da guia. |
|**tenantId**| Cadeia de caracteres | Sim | A ID do locatário é necessária para os usuários do locatário. Ele está disponível em Tab SSO, Bot Invoke e Teams Client SDK. É recomendável obter uma ID de locatário do SSO de tabulação. |

#### <a name="example"></a>Exemplo

A `GetParticipant` API inclui os seguintes exemplos:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  TeamsMeetingParticipant participant = GetMeetingParticipantAsync(turnContext, "yourMeetingId", "yourParticipantId", "yourTenantId");
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

* * *

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

A `GetParticipant` API inclui os seguintes códigos de resposta:

|Código da resposta|Descrição|
|---|---|
| **403** | O aplicativo não tem permissão para obter informações do participante. Essa é a resposta de erro mais comum e é disparada se o aplicativo não estiver instalado na reunião. Por exemplo, se o aplicativo for desabilitado pelo administrador do locatário ou bloqueado durante a migração do site ao vivo.|
| **200** | As informações do participante são recuperadas com êxito.|
| **401** | O aplicativo responde com um token inválido.|
| **404** | A reunião expirou ou o participante não pode ser encontrado.|
| **500** | A reunião expirou (mais de 60 dias) desde que a reunião terminou ou os participantes não têm permissões com base em suas funções.|

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

activity.ChannelData = new TeamsChannelData
  {
    Notification = new NotificationInfo()
                    {
                        AlertInMeeting = true,
                        ExternalResourceUrl = "https://teams.microsoft.com/l/bubble/APP_ID?url=<url>&height=<height>&width=<width>&title=<title>&completionBotId=BOT_APP_ID"
                    }
  };
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
| **403** | O aplicativo não consegue enviar o sinal. Isso pode acontecer devido a vários motivos, como o administrador de locatários desabilita o aplicativo, o aplicativo é bloqueado durante a migração de site ao vivo e assim por diante. Nesse caso, a carga contém uma mensagem de erro detalhada. |
| **404** | O chat de reunião não existe. |

## <a name="code-sample"></a>Exemplo de código

|Exemplo de nome | Descrição | .NET | Node.js |
|----------------|-----------------|--------------|--------------|
| Extensibilidade de reuniões | Microsoft Teams exemplo de extensibilidade de reunião para tokens de passagem. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/nodejs) |
| Bot de bolha de conteúdo de reunião | Microsoft Teams exemplo de extensibilidade de reunião para interagir com o bot de bolha de conteúdo em uma reunião. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/csharp) |  [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/nodejs)|
| Meeting meetingSidePanel | Microsoft Teams exemplo de extensibilidade de reunião para interagir com o painel lateral na reunião. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/nodejs)|

## <a name="see-also"></a>Confira também

* [Diretrizes de design de caixa de diálogo na reunião](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
* [Teams fluxo de autenticação para guias](../tabs/how-to/authentication/auth-flow-tab.md)
* [Aplicativos para Teams reuniões](teams-apps-in-meetings.md)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Habilitar e configurar seus aplicativos para Teams reuniões](enable-and-configure-your-app-for-teams-meetings.md)
