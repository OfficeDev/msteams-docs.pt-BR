---
title: Criar aplicativos para reuniões do Teams
author: laujan
description: criar aplicativos para reuniões do teams
ms.topic: conceptual
ms.author: lajanuar
keywords: api de função de participante de reuniões de aplicativos do teams
ms.openlocfilehash: ac0d3dee30e82cde51651f7eab3b05e569b820f7
ms.sourcegitcommit: 94b1d3e50563b31c1ff01c52d563c112a2553611
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2021
ms.locfileid: "51435033"
---
# <a name="create-apps-for-teams-meetings"></a>Crie aplicativos para reuniões do Teams

## <a name="prerequisites-and-considerations"></a>Pré-requisitos e considerações

Antes de criar aplicativos para reuniões do Teams, você deve ter uma compreensão do seguinte:

* Você deve ter conhecimento de como desenvolver aplicativos do Teams. Para obter mais informações, consulte [Desenvolvimento de aplicativos do Teams](../overview.md).

* Você deve atualizar o manifesto do aplicativo do Teams para indicar que o aplicativo está disponível para reuniões. Para obter mais informações, consulte [manifesto do aplicativo](#update-your-app-manifest).

* Para que seu aplicativo funcione no ciclo de vida da reunião como uma guia, ele deve dar suporte a guias configuráveis no escopo de groupchat. Para obter mais informações, consulte [groupchat scope](../resources/schema/manifest-schema.md#configurabletabs) and [build a group tab](../build-your-first-app/build-channel-tab.md).

* Você deve seguir as diretrizes gerais de design de guia do Teams para cenários pré e pós-reunião. Para experiências durante as reuniões, consulte a guia na reunião e as diretrizes de design da caixa de diálogo na reunião. Para obter mais informações, consulte Diretrizes de design de [guia do Teams,](../tabs/design/tabs.md)diretrizes de [design](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab) da guia de reunião e diretrizes de design de caixa de diálogo [na reunião.](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)

* Você deve dar suporte ao escopo para habilitar seu aplicativo em chats de `groupchat` pré-reunião e pós-reunião. Com a experiência do aplicativo de pré-reunião, você pode encontrar e adicionar aplicativos de reunião e realizar tarefas de pré-reunião. Com a experiência do aplicativo pós-reunião, você pode exibir os resultados da reunião, como resultados da pesquisa ou comentários.

* Os parâmetros de URL da API de reunião `meetingId` devem ter , e `userId` `tenantId` . Eles estão disponíveis como parte da atividade de SDK e bot do cliente do Teams. Além disso, informações confiáveis para iD de usuário e ID de locatário podem ser recuperadas usando [a autenticação tab SSO](../tabs/how-to/authentication/auth-aad-sso.md).

* A `GetParticipant` API deve ter um registro de bot e uma ID para gerar tokens de auth. Para obter mais informações, [consulte registro de bot e ID](../build-your-first-app/build-bot.md).

* Para que seu aplicativo seja atualizado em tempo real, ele deve estar atualizado com base nas atividades do evento na reunião. Esses eventos podem estar dentro da caixa de diálogo na reunião e em outros estágios no ciclo de vida da reunião. Para a caixa de diálogo na reunião, consulte o parâmetro completion `bot Id` em `Notification Signal API` .

## <a name="meeting-apps-api-reference"></a>Referência da API de aplicativos de reunião

|API|Descrição|Solicitação|Origem|
|---|---|----|---|
|**GetUserContext**| Essa API permite que você receba informações contextuais para exibir conteúdo relevante em uma guia do Teams. |_**microsoftTeams.getContext( ( ) => { /*...* / } )**_|SDK de cliente do Microsoft Teams|
|**GetParticipant**| Essa API permite que um bot busque informações dos participantes por meio da ID da reunião e da ID do participante. |**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_ |Microsoft Bot Framework SDK|
|**NotificationSignal** | Essa API permite que você forneça sinais de reunião que são entregues usando a API de notificação de conversa existente para chat de usuário-bot. Ele permite sinalizar com base na ação do usuário que mostra uma caixa de diálogo na reunião. |**POST** _**/v3/conversations/{conversationId}/activities**_|Microsoft Bot Framework SDK|

### <a name="getusercontext"></a>GetUserContext

Para identificar e recuperar informações contextuais para o conteúdo da guia, consulte [obter contexto para a guia Do Teams.](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library) `meetingId` é usado por uma guia ao ser executado no contexto da reunião e é adicionado para a carga de resposta.

### <a name="getparticipant-api"></a>GetParticipant API

> [!NOTE]
> * Não armazenar em cache as funções do participante, pois o organizador da reunião pode alterar uma função a qualquer momento.
> * No momento, o Teams não dá suporte a grandes listas de distribuição ou tamanhos de lista de mais de 350 participantes para a `GetParticipant` API.

#### <a name="query-parameters"></a>Parâmetros de consulta

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**meetingId**| string | Sim | O identificador de reunião está disponível por meio do Bot Invoke e do SDK do Cliente do Teams.|
|**participantId**| string | Sim | A ID do participante é a ID do usuário. Ele está disponível em Tab SSO, Bot Invoke e Teams Client SDK. É recomendável obter uma ID do participante no SSO da guia. |
|**tenantId**| string | Sim | A ID do locatário é necessária para os usuários do locatário. Ele está disponível em Tab SSO, Bot Invoke e Teams Client SDK. É recomendável obter uma ID de locatário do SSO de tabulação. |

#### <a name="example"></a>Exemplo

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

|Código da resposta|Descrição|
|---|---|
| **403** | O aplicativo não tem permissão para obter informações do participante. Essa é a resposta de erro mais comum e é disparada se o aplicativo não estiver instalado na reunião. Por exemplo, se o aplicativo for desabilitado pelo administrador do locatário ou bloqueado durante a migração do site ao vivo.|
| **200** | As informações do participante são recuperadas com êxito.|
| **401** | O aplicativo responde com um token inválido.|
| **404** | A reunião expirou ou o participante não pode ser encontrado.|
| **500** | A reunião expirou mais de 60 dias desde que a reunião terminou ou o participante não tem permissões com base em sua função.|

### <a name="notificationsignal-api"></a>NotificationSignal API

Todos os usuários em uma reunião recebem as notificações enviadas por meio da `NotificationSignal` API.

> [!NOTE]
> * Quando uma caixa de diálogo na reunião é invocada, o conteúdo é apresentado como uma mensagem de chat.
> * Atualmente, não há suporte para o envio de notificações direcionadas.

#### <a name="query-parameters"></a>Parâmetros de consulta

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**conversationId**| string | Sim | O identificador de conversa está disponível como parte da invocação de bot |

#### <a name="example"></a>Exemplo

O `Bot ID` é declarado no manifesto e o bot recebe um objeto de resultado.

> [!NOTE]
> * O `completionBotId` parâmetro do é opcional no exemplo de carga `externalResourceUrl` solicitada. `Bot ID` é declarado no manifesto e o bot recebe um objeto de resultado.
> * Os `externalResourceUrl` parâmetros de largura e altura devem estar em pixels. Para garantir que as dimensões estão dentro dos limites permitidos, consulte [diretrizes de design](design/designing-apps-in-meetings.md).
> * A URL é a página carregada como `<iframe>` uma caixa de diálogo na reunião. O domínio deve estar na matriz do aplicativo `validDomains` no manifesto do aplicativo.

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

* * *

#### <a name="response-codes"></a>Códigos de resposta

|Código da resposta|Descrição|
|---|---|
| **201** | A atividade com sinal é enviada com êxito |
| **401** | O aplicativo responde com um token inválido. |
| **403** | O aplicativo não consegue enviar o sinal. Isso pode acontecer devido a vários motivos, como o administrador de locatários desabilita o aplicativo, o aplicativo é bloqueado durante a migração de site ao vivo e assim por diante. Nesse caso, a carga contém uma mensagem de erro detalhada. |
| **404** | O chat de reunião não existe. |

## <a name="enable-your-app-for-teams-meetings"></a>Habilitar seu aplicativo para reuniões do Teams

### <a name="update-your-app-manifest"></a>Atualizar o manifesto do aplicativo

Os recursos do aplicativo de reuniões são declarados no manifesto do aplicativo usando `configurableTabs` `scopes` as matrizes , e `context` . O escopo define a quem e o contexto define onde seu aplicativo está disponível.

> [!NOTE]
> Tente atualizar o manifesto do aplicativo com o [esquema de manifesto](../resources/schema/manifest-schema-dev-preview.md).

```json

"configurableTabs": [
    {
      "configurationUrl": "https://contoso.com/teamstab/configure",
      "canUpdateConfiguration": true,
      "scopes": [
        "team",
        "groupchat"
      ],
      "context":[
        "channelTab",
        "privateChatTab",
        "meetingChatTab",
        "meetingDetailsTab",
        "meetingSidePanel"
     ]
    }
  ]
```

### <a name="context-property"></a>Propriedade Context

A guia `context` e `scopes` as propriedades permitem determinar onde seu aplicativo deve aparecer. Guias no `team` escopo ou podem `groupchat` ter mais de um contexto. A seguir estão os valores da propriedade da qual você pode usar todos ou `context` alguns dos valores:

|Valor|Descrição|
|---|---|
| **channelTab** | Uma guia no header de um canal de equipe. |
| **privateChatTab** | Uma guia no header de um chat de grupo entre um conjunto de usuários que não está no contexto de uma equipe ou reunião. |
| **meetingChatTab** | Uma guia no header de um chat de grupo entre um conjunto de usuários no contexto de uma reunião agendada. |
| **meetingDetailsTab** | Uma guia no header da exibição de detalhes da reunião do calendário. |
| **meetingSidePanel** | Um painel na reunião foi aberto por meio da barra unificada (U-bar). |

> [!NOTE]
> `Context` atualmente, não há suporte para clientes móveis.

## <a name="configure-your-app-for-meeting-scenarios"></a>Configurar seu aplicativo para cenários de reunião

> [!NOTE]
> * Para que seu aplicativo seja visível na galeria de guias, ele deve dar suporte a guias configuráveis e ao escopo de chat de grupo.
> * Os clientes móveis suportam guias somente em estágios pré e pós-reunião.
> * As experiências na reunião que estão na caixa de diálogo e na guia da reunião atualmente não são suportadas em clientes móveis. Para obter mais informações, consulte [diretrizes para guias em dispositivos móveis](../tabs/design/tabs-mobile.md) ao criar suas guias para dispositivos móveis.

### <a name="before-a-meeting"></a>Antes de uma reunião

Antes de uma reunião, os usuários podem adicionar guias, bots e extensões de mensagens a uma reunião. Os usuários com funções de organizador e apresentador podem adicionar guias a uma reunião.

**Para adicionar uma guia a uma reunião**

1. Em seu calendário, selecione uma reunião à qual deseja adicionar uma guia.
1. Selecione a **guia Detalhes** e selecione mais <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>. A galeria de guias é exibida.

    ![Experiência de pré-reunião](../assets/images/apps-in-meetings/PreMeeting.png)

1. Na galeria de guias, selecione o aplicativo que você deseja adicionar e siga as etapas conforme necessário. O aplicativo é instalado como uma guia.
    > [!NOTE] 
    > Atualmente, na guia reuniões, não há suporte para obter detalhes da reunião e informações dos participantes.

**Para adicionar uma extensão de mensagens a uma reunião**

1. Selecione as releições ou o menu de estouro &#x25CF;&#x25CF;&#x25CF; localizado na área de mensagem de redação no chat.
1. Selecione o aplicativo que você deseja adicionar e siga as etapas conforme necessário. O aplicativo é instalado como uma extensão de mensagens.

**Para adicionar um bot a uma reunião**

Em um chat de reunião, insira **@** a chave e selecione Obter **bots**.

> [!NOTE]
> * A identidade do usuário deve ser confirmada usando [Guias SSO](../tabs/how-to/authentication/auth-aad-sso.md). Após a autenticação, o aplicativo pode recuperar a função de usuário usando a `GetParticipant` API.
> * Com base na função de usuário, o aplicativo tem a capacidade de fornecer experiências específicas de função. Por exemplo, um aplicativo de sondagem permite que apenas organizadores e apresentadores criem uma nova sondagem.
> * As atribuições de função podem ser alteradas enquanto uma reunião está em andamento. Para obter mais informações, [consulte funções em uma reunião do Teams](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).

### <a name="during-a-meeting"></a>Durante uma reunião

#### <a name="sidepanel"></a>sidePanel

Com o sidePanel, você pode personalizar experiências em uma reunião que permitem que organizadores e apresentadores tenham diferentes tipos de exibição e ações. No manifesto do aplicativo, você deve adicionar sidePanel à matriz de contexto. Na reunião e em todos os cenários, o aplicativo é renderizado em uma guia na reunião que tem 320 pixels de largura. Para obter mais informações, consulte [Interface FrameContext](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/framecontext?view=msteams-client-js-latest&preserve-view=true
).

Para usar a `userContext` API para rotear solicitações de acordo, consulte [Teams SDK](../tabs/how-to/access-teams-context.md#user-context). Consulte [Fluxo de autenticação do Teams para guias](../tabs/how-to/authentication/auth-flow-tab.md). O fluxo de autenticação para guias é muito semelhante ao fluxo de autenticação para sites. Portanto, as guias podem usar o OAuth 2.0 diretamente. Consulte a plataforma de identidade da Microsoft e o fluxo de código de autorização do [OAuth 2.0.](/azure/active-directory/develop/v2-oauth2-auth-code-flow)

A extensão de mensagens funciona conforme o esperado quando um usuário está em uma exibição em reunião e o usuário pode postar cartões de extensão de mensagem de composição. AppName in-meeting é uma dica de ferramenta que informa o nome do aplicativo na U-bar de reunião.

#### <a name="in-meeting-dialog"></a>Caixa de diálogo na reunião

A caixa de diálogo na reunião pode ser usada para envolver os participantes durante a reunião e coletar informações ou comentários durante a reunião. Use a [`NotificationSignal`](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) API para sinalizar que uma notificação de bolha deve ser disparada. Como parte da carga da solicitação de notificação, inclua a URL onde o conteúdo a ser mostrado está hospedado.

A caixa de diálogo na reunião não deve usar o módulo de tarefa. O módulo de tarefa não é invocado em um chat de reunião. Uma URL de recurso externo é usada para exibir a bolha de conteúdo em uma reunião. Você pode usar o `submitTask` método para enviar dados em um chat de reunião.

> [!NOTE]
> * Você deve invocar [a função submitTask()](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) para descartar automaticamente depois que um usuário realizar uma ação no web-view. Esse é um requisito para envio de aplicativo. Para obter mais informações, consulte [Módulo de tarefas do SDK do Teams.](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true)
> * Se você quiser que seu aplicativo suporte usuários anônimos, sua carga inicial de solicitação de invocação deve depender dos metadados de solicitação no objeto, não `from.id` `from` nos `from.aadObjectId` metadados de solicitação. `from.id` é a ID do usuário e é a ID do `from.aadObjectId` Azure Active Directory (AAD) do usuário. Para obter mais informações, [consulte using task modules in tabs](../task-modules-and-cards/task-modules/task-modules-tabs.md) e [create and send the task module](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).

### <a name="after-a-meeting"></a>Após uma reunião

As configurações pós-reunião e pré-reunião são equivalentes.

## <a name="code-sample"></a>Exemplo de código

|Exemplo de nome | Descrição | C# |
|----------------|-----------------|--------------|
| Extensibilidade de reuniões | Exemplo de extensibilidade de reunião do Microsoft Teams para tokens de passagem. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) |
| Bot de bolha de conteúdo de reunião | Exemplo de extensibilidade de reunião do Microsoft Teams para interagir com o bot de bolha de conteúdo em uma reunião. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/csharp) |

## <a name="see-also"></a>Confira também

> [!div class="nextstepaction"]
> [Diretrizes de design de caixa de diálogo na reunião](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
> [!div class="nextstepaction"]
> [Fluxo de autenticação do Teams para guias](../tabs/how-to/authentication/auth-flow-tab.md)
