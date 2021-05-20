---
title: Criar aplicativos para reuniões do Teams
author: laujan
description: criar aplicativos para reuniões de equipes
ms.topic: conceptual
ms.author: lajanuar
localization_priority: Normal
keywords: equipes aplicativos reuniões usuário participante papel api
ms.openlocfilehash: 84d0f5564d7e8e6e34dde1f3d59cc6e7a68d3332
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565911"
---
# <a name="create-apps-for-teams-meetings"></a>Crie aplicativos para reuniões do Teams

## <a name="prerequisites-and-considerations"></a>Pré-requisitos e considerações

Antes de criar aplicativos para reuniões Teams, você deve ter uma compreensão das seguintes:

* Você deve ter conhecimento de como desenvolver aplicativos Teams. Para obter mais informações, consulte [Teams desenvolvimento de aplicativos](../overview.md).

* Você deve atualizar o manifesto do aplicativo Teams para indicar que o aplicativo está disponível para reuniões. Para obter mais informações, consulte [manifesto do aplicativo](#update-your-app-manifest).

* Para que seu aplicativo funcione no ciclo de vida de reunião como uma guia, ele deve suportar guias configuráveis no escopo do groupchat. Para obter mais informações, consulte [o escopo do groupchat](../resources/schema/manifest-schema.md#configurabletabs) e [construa uma guia de grupo](../build-your-first-app/build-channel-tab.md).

* Você deve seguir as diretrizes gerais de design de guias Teams para cenários pré e pós-reunião. Para obter experiências durante as reuniões, consulte a guia de reunião e as diretrizes de design de diálogo em reunião. Para obter mais informações, consulte Teams diretrizes de design de [guias,](../tabs/design/tabs.md) [diretrizes de design de guias em reunião](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab) e [diretrizes de design de diálogo em reunião.](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)

* Você deve apoiar o `groupchat` escopo para habilitar seu aplicativo em chats pré-reunião e pós-reunião. Com a experiência de aplicativo pré-encontro, você pode encontrar e adicionar aplicativos de reunião e executar tarefas pré-reunião. Com a experiência do aplicativo pós-reunião, você pode ver os resultados da reunião, como resultados da pesquisa ou feedback.

* Atender aos parâmetros de URL da API deve `meetingId` `userId` ter, e `tenantId` . Estes estão disponíveis como parte da atividade de Teams cliente SDK e bot. Além disso, informações confiáveis para ID do usuário e ID do inquilino podem ser recuperadas usando [autenticação Tab SSO](../tabs/how-to/authentication/auth-aad-sso.md).

* A `GetParticipant` API deve ter um registro de bot e ID para gerar tokens auth. Para obter mais informações, consulte [registro de bot e ID](../build-your-first-app/build-bot.md).

* Para que seu aplicativo atualize em tempo real, ele deve estar atualizado com base nas atividades do evento na reunião. Esses eventos podem estar dentro da caixa de diálogo presencial e outras etapas ao longo do ciclo de vida do encontro. Para a caixa de diálogo em reunião, consulte o parâmetro de conclusão `bot Id` em `Notification Signal API` .

## <a name="meeting-apps-api-reference"></a>Referência de API de aplicativos de reunião

|API|Descrição|Solicitação|Origem|
|---|---|----|---|
|**GetUserContext**| Esta API permite que você obtenha informações contextuais para exibir conteúdo relevante em uma guia Teams. |_**microsoftTeams.getContext( => { /*...* / } )**_|Microsoft Teams cliente SDK|
|**GetParticipant**| Esta API permite que um bot busque informações dos participantes atendendo o ID e o ID do participante. |**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_ |Microsoft Bot Framework SDK|
|**NotificaçõesSignal** | Esta API permite que você forneça sinais de reunião que são entregues usando a API de notificação de conversação existente para o chat usuário-bot. Ele permite que você sinalize com base na ação do usuário que mostra uma caixa de diálogo em reunião. |**POST** _**/v3/conversations/{conversationId}/activities**_|Microsoft Bot Framework SDK|

### <a name="getusercontext"></a>GetUserContext

Para identificar e recuperar informações contextuais para o conteúdo da guia, consulte [obter contexto para sua guia Teams](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library). `meetingId`é usado por uma guia ao executar no contexto da reunião e é adicionado para a carga de resposta.

### <a name="getparticipant-api"></a>GetParticipant API

> [!NOTE]
> * Não em cache de funções participantes, uma vez que o organizador do encontro pode mudar uma função a qualquer momento.
> * Teams atualmente não suporta grandes listas de distribuição ou tamanhos de listas de mais de 350 participantes para a `GetParticipant` API.

#### <a name="query-parameters"></a>Parâmetros de consulta

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**reuniãoId**| string | Sim | O identificador de reunião está disponível através do Bot Invoke e Teams Cliente SDK.|
|**participantId**| string | Sim | O ID participante é o ID do usuário. Está disponível no Tab SSO, Bot Invoke e Teams Client SDK. Recomenda-se obter um ID participante do Tab SSO. |
|**tenantId**| string | Sim | A identificação do inquilino é necessária para os usuários do inquilino. Está disponível no Tab SSO, Bot Invoke e Teams Client SDK. Recomenda-se obter um ID de inquilino do Tab SSO. |

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
| **403** | O aplicativo não tem permissão para obter informações do participante. Esta é a resposta de erro mais comum e é acionada se o aplicativo não for instalado na reunião. Por exemplo, se o aplicativo for desativado por administrador de inquilinos ou bloqueado durante a migração do site ao vivo.|
| **200** | As informações do participante são recuperadas com sucesso.|
| **401** | O aplicativo responde com um token inválido.|
| **404** | A reunião expirou ou o participante não pode ser encontrado.|
| **500** | A reunião já expirou mais de 60 dias desde o término da reunião ou o participante não tem permissões com base em seu papel.|

### <a name="notificationsignal-api"></a>NotificaçõesA API do sinal

Todos os usuários em uma reunião recebem as notificações enviadas através da `NotificationSignal` API.

> [!NOTE]
> * Quando uma caixa de diálogo em reunião é invocada, o conteúdo é apresentado como uma mensagem de bate-papo.
> * Atualmente, o envio de notificações direcionadas não é suportado.

#### <a name="query-parameters"></a>Parâmetros de consulta

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**conversationId**| string | Sim | O identificador de conversação está disponível como parte da invocação do bot. |

#### <a name="example"></a>Exemplo

O `Bot ID` é declarado no manifesto e o bot recebe um objeto resultante.

> [!NOTE]
> * O `completionBotId` parâmetro do é opcional no exemplo de carga `externalResourceUrl` solicitada. `Bot ID` é declarado no manifesto e o bot recebe um objeto resultante.
> * Os `externalResourceUrl` parâmetros de largura e altura devem estar em pixels. Para garantir que as dimensões estejam dentro dos limites permitidos, consulte [as diretrizes de design](design/designing-apps-in-meetings.md).
> * A URL é a página carregada como uma `<iframe>` caixa de diálogo em reunião. O domínio deve estar na matriz do aplicativo no manifesto do `validDomains` aplicativo.

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
| **201** | A atividade com sinal é enviada com sucesso. |
| **401** | O aplicativo responde com um token inválido. |
| **403** | O aplicativo não pode enviar o sinal. Isso pode acontecer devido a várias razões como o administrador inquilino desativa o aplicativo, o aplicativo é bloqueado durante a migração ao vivo do site, e assim por diante. Neste caso, a carga contém uma mensagem de erro detalhada. |
| **404** | O bate-papo de reunião não existe. |

## <a name="enable-your-app-for-teams-meetings"></a>Habilite seu aplicativo para reuniões Teams

### <a name="update-your-app-manifest"></a>Atualize seu manifesto de aplicativo

Os recursos do aplicativo de reuniões são declarados no manifesto do aplicativo usando o `configurableTabs` `scopes` , e `context` arrays. Escopo define para quem e contexto define onde seu aplicativo está disponível.

> [!NOTE]
> Tente atualizar seu manifesto de aplicativo com o [esquema manifesto](../resources/schema/manifest-schema-dev-preview.md).
> Aplicativos em reuniões precisam de escopo *de groupchat.* O escopo *da equipe* funciona apenas para guias em canais.

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
        "meetingSidePanel",
        "meetingStage"
     ]
    }
  ]
```
> [!NOTE]
> `meetingStage` atualmente está disponível apenas na pré-visualização do desenvolvedor.

### <a name="context-property"></a>Propriedade Context

A guia `context` e as propriedades permitem determinar onde seu aplicativo deve `scopes` aparecer. Guias no `team` escopo ou podem ter mais de um `groupchat` contexto. A seguir estão os valores para a `context` propriedade a partir da qual você pode usar todos ou alguns dos valores:

|Valor|Descrição|
|---|---|
| **channelTab** | Uma guia na cabeçalho de um canal de equipe. |
| **privateChatTab** | Uma guia no cabeçalho de um bate-papo em grupo entre um conjunto de usuários que não estão no contexto de uma equipe ou reunião. |
| **reuniãoChatTab** | Uma guia no cabeçalho de um bate-papo em grupo entre um conjunto de usuários no contexto de uma reunião agendada. |
| **reuniãoDetailsTab** | Uma guia no cabeçalho da reunião detalha a visualização do calendário. |
| **reuniãoSidePanel** | Um painel de reunião aberto através do bar unificado (U-bar). |
| **palco de reunião** | Um aplicativo do painel lateral pode ser compartilhado na fase de reunião. |

> [!NOTE]
> `Context` atualmente, a propriedade não é suportada em clientes móveis.

## <a name="configure-your-app-for-meeting-scenarios"></a>Configure seu aplicativo para cenários de reunião

> [!NOTE]
> * Para que seu aplicativo seja visível na galeria de guias, ele deve suportar guias configuráveis e o escopo de bate-papo em grupo.
> * Os clientes móveis suportam guias apenas em etapas pré e pós-reunião.
> * As experiências de encontro que são caixa de diálogo e guia no atendimento atualmente não são suportadas em clientes móveis. Para obter mais informações, consulte [orientação para guias no celular](../tabs/design/tabs-mobile.md) ao criar suas guias para celular.

### <a name="before-a-meeting"></a>Antes de uma reunião

Antes de uma reunião, os usuários podem adicionar guias, bots e extensões de mensagens a uma reunião. Usuários com funções de organizador e apresentador podem adicionar guias a uma reunião.

**Para adicionar uma guia a uma reunião**

1. Em seu calendário, selecione uma reunião à qual deseja adicionar uma guia.
1. Selecione a guia **Detalhes** e selecione mais <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>. A galeria de guias aparece.

    ![Experiência de pré-encontro](../assets/images/apps-in-meetings/PreMeeting.png)

1. Na galeria de guias, selecione o aplicativo que deseja adicionar e siga as etapas conforme necessário. O aplicativo é instalado como uma guia.
    > [!NOTE] 
    > Atualmente, na guia reuniões, não é suportada a obtenção de detalhes de reunião e informações dos participantes.

**Para adicionar uma extensão de mensagens a uma reunião**

1. Selecione as elipses ou o menu de estouro &#x25CF;&#x25CF;&#x25CF; localizado na área de compor mensagens no chat.
1. Selecione o aplicativo que deseja adicionar e siga as etapas conforme necessário. O aplicativo é instalado como uma extensão de mensagens.

**Para adicionar um bot a uma reunião**

Em um bate-papo de reunião, insira a **@** chave e selecione Obter **bots**.

> [!NOTE]
> * A identidade do usuário deve ser confirmada usando [o Tabs SSO](../tabs/how-to/authentication/auth-aad-sso.md). Após a autenticação, o aplicativo pode recuperar a função do usuário usando a `GetParticipant` API.
> * Com base na função do usuário, o aplicativo tem a capacidade de fornecer experiências específicas de função. Por exemplo, um aplicativo de votação permite apenas que organizadores e apresentadores criem uma nova enquete.
> * As atribuições de papéis podem ser alteradas enquanto uma reunião está em andamento. Para obter mais informações, consulte [papéis em uma reunião Teams](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).

### <a name="during-a-meeting"></a>Durante uma reunião

#### <a name="sidepanel"></a>sidePanel

Com o sidePanel, você pode personalizar experiências em um encontro que permite aos organizadores e apresentadores ter diferentes conjuntos de pontos de vista e ações. No manifesto do aplicativo, você deve adicionar o painel lateral à matriz de contexto. Na reunião e em todos os cenários, o aplicativo é renderizado em uma guia de reunião que tem 320 pixels de largura. Para obter mais informações, consulte [a interface FrameContext](/javascript/api/@microsoft/teams-js/framecontext?view=msteams-client-js-latest&preserve-view=true
).

Para usar a `userContext` API para rotear as solicitações de acordo, consulte [Teams SDK](../tabs/how-to/access-teams-context.md#user-context). Consulte [Teams fluxo de autenticação para guias](../tabs/how-to/authentication/auth-flow-tab.md). O fluxo de autenticação para guias é muito semelhante ao fluxo de auth para sites. Assim, as guias podem usar o OAuth 2.0 diretamente. Veja, [fluxo de código de autorização plataforma de identidade da Microsoft e OAuth 2.0](/azure/active-directory/develop/v2-oauth2-auth-code-flow).

A extensão de mensagens funciona como esperado quando um usuário está em uma exibição de reunião e o usuário pode postar cartões de extensão de mensagens. AppName na reunião é uma dica de ferramenta que afirma o nome do aplicativo em reunião U-bar.

> [!NOTE]
> Use a versão 1.7.0 ou superior do [Teams SDK,](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)pois as versões anteriores não suportam o painel lateral.

#### <a name="in-meeting-dialog"></a>Caixa de diálogo na reunião

A caixa de diálogo presencial pode ser usada para engajar os participantes durante a reunião e coletar informações ou feedback durante a reunião. Use a [`NotificationSignal`](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) API para sinalizar que uma notificação de bolha deve ser acionada. Como parte da carga de solicitação de notificação, inclua a URL onde o conteúdo a ser mostrado está hospedado.

O diálogo de reunião não deve usar o módulo de tarefas. O módulo de tarefa não é invocado em um bate-papo de reunião. Uma URL de recurso externo é usada para exibir bolha de conteúdo em uma reunião. Você pode usar o `submitTask` método para enviar dados em um bate-papo de reunião.

> [!NOTE]
> * Você deve invocar a função [submitTask()](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) para descartar automaticamente depois que um usuário tomar uma ação na exibição da Web. Este é um requisito para submissão de aplicativos. Para obter mais informações, consulte [Teams módulo de tarefas SDK](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).
> * Se você quiser que seu aplicativo apoie usuários anônimos, sua carga inicial de solicitação de invocação deve depender dos `from.id` metadados de solicitação no `from` objeto, não nos `from.aadObjectId` metadados de solicitação. `from.id`é o ID do usuário e `from.aadObjectId` é o ID Azure Active Directory (AAD) do usuário. Para obter mais informações, consulte [o uso de módulos de tarefas nas guias](../task-modules-and-cards/task-modules/task-modules-tabs.md) e [crie e envie o módulo de tarefas](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).

#### <a name="share-to-stage"></a>Compartilhar para o palco 

> [!NOTE]
> * Este recurso está atualmente disponível apenas na visualização do desenvolvedor.
> * Para usar esse recurso, o aplicativo deve suportar um painel lateral em reunião.


Esse recurso dá aos desenvolvedores a capacidade de compartilhar um aplicativo para a fase de reunião. Ao possibilitar a participação na etapa de reunião, os participantes do encontro podem colaborar em tempo real. 

O contexto necessário está `meetingStage` no manifesto do aplicativo. Um pré-requisito para isso é ter o `meetingSidePanel` contexto. Isso permite que o botão **Compartilhar** no painel lateral seja despecido na seguinte imagem:

  ![share_to_stage_during_meeting experiência](~/assets/images/apps-in-meetings/share_to_stage_during_meeting.png)

A mudança manifesto necessária para habilitar essa capacidade é a seguinte: 

```json

"configurableTabs": [
    {
      "configurationUrl": "https://contoso.com/teamstab/configure",
      "canUpdateConfiguration": true,
      "scopes": [
        "groupchat"
      ],
      "context":[
        
        "meetingSidePanel",
        "meetingStage"
     ]
    }
  ]
```



### <a name="after-a-meeting"></a>Após uma reunião

As configurações pós-reunião e pré-reunião são equivalentes.

## <a name="code-sample"></a>Exemplo de código

|Nome da amostra | Descrição | .NET | Node.js |
|----------------|-----------------|--------------|--------------|
| Extensibilidade de reuniões | Microsoft Teams amostra de extensibilidade de reunião para tokens de passagem. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/nodejs) |
| Meeting content bubble bot | Microsoft Teams a amostra de extensibilidade de reunião para interagir com o bot bolha de conteúdo em uma reunião. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/csharp) |  [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/nodejs)|
| Reunião SidePanel | Microsoft Teams amostra de extensibilidade de reunião para iteracting com o painel lateral em reunião. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/csharp) |

## <a name="see-also"></a>Confira também

* [Diretrizes de design de diálogo em reunião](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
* [fluxo de autenticação Teams para guias](../tabs/how-to/authentication/auth-flow-tab.md)
