---
title: Criar aplicativos para reuniões do Teams
author: laujan
description: criar aplicativos para reuniões do teams
ms.topic: conceptual
ms.author: lajanuar
keywords: api de função de participante de reuniões de aplicativos do teams
ms.openlocfilehash: bd0f53ae34a23bdbbdc2e6f3992c7dd0836e9f28
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449490"
---
# <a name="create-apps-for-teams-meetings"></a>Crie aplicativos para reuniões do Teams

## <a name="prerequisites-and-considerations"></a>Pré-requisitos e considerações

* Os aplicativos em reuniões exigem algum conhecimento básico sobre [o desenvolvimento de aplicativos do Teams.](../overview.md) Um aplicativo em uma reunião pode ser composto [](../messaging-extensions/what-are-messaging-extensions.md) por [guias,](../tabs/what-are-tabs.md) [bots](../bots/what-are-bots.md)e recursos de extensões de mensagens e exigirá atualizações no manifesto do aplicativo [do](#update-your-app-manifest) Teams para indicar que o aplicativo está disponível para reuniões

* Para que seu aplicativo funcione no ciclo de vida da reunião como uma guia, ele deve dar suporte a guias configuráveis no escopo [de groupchat](../resources/schema/manifest-schema.md#configurabletabs) (consulte como criar [uma guia de grupo](../build-your-first-app/build-channel-tab.md)). O suporte `groupchat` ao escopo habilita o aplicativo em chats de [pré-reunião](teams-apps-in-meetings.md#pre-meeting-app-experience) e [pós-reunião.](teams-apps-in-meetings.md#post-meeting-app-experience)

* Os parâmetros de URL da API de reunião podem exigir , e o tenantId Eles estão disponíveis como parte da atividade do SDK do Cliente do `meetingId` `userId` Teams e do bot. [](/onedrive/find-your-office-365-tenant-id) Além disso, informações confiáveis para iD de usuário e ID de locatário podem ser recuperadas usando [a autenticação tab SSO](../tabs/how-to/authentication/auth-aad-sso.md).

* Algumas APIs de reunião, como , exigem um `GetParticipant` registro de bot e [ID](../build-your-first-app/build-bot.md) para gerar tokens de auth.

* Você deve seguir as [diretrizes gerais de design](../tabs/design/tabs.md) de guia do Teams para cenários pré e pós-reunião. Para experiências durante as reuniões, consulte a [guia na reunião](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab) e as [diretrizes](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog) de design da caixa de diálogo na reunião.

* Para que seu aplicativo seja atualizado em tempo real, ele deve estar atualizado com base nas atividades do evento na reunião. Esses eventos podem estar dentro da caixa de diálogo na reunião (consulte o parâmetro completion em ) e outras superfícies em todo o ciclo `bot Id` `Notification Signal API` de vida da reunião

## <a name="meeting-apps-api-reference"></a>Referência da API de aplicativos de reunião

|API|Descrição|Solicitação|Origem|
|---|---|----|---|
|**GetUserContext**| Obter informações contextuais para exibir conteúdo relevante em uma guia do Teams. |_**microsoftTeams.getContext( ( ) => { /*...* / } )**_|SDK de cliente do Microsoft Teams|
|**GetParticipant**|Essa API permite que um bot busque informações de um participante por meio da ID da reunião e da ID do participante.|**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_ |Microsoft Bot Framework SDK|
|**NotificationSignal** |Os sinais de reunião serão entregues usando a SEGUINTE API de notificação de conversa existente (para chat usuário-bot). Essa API permite que os desenvolvedores sinalizem com base na ação do usuário final para mostrar uma bolha de diálogo na reunião.|**POST** _**/v3/conversations/{conversationId}/activities**_|Microsoft Bot Framework SDK|

### <a name="getusercontext"></a>GetUserContext

Consulte nossa documentação da guia [Obter contexto](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library) do Teams para obter orientações sobre a identificação e recuperação de informações contextuais para o conteúdo da guia. Como parte da extensibilidade de reuniões, um novo valor foi adicionado para a carga de resposta:

✔ **meetingId**: usado por uma guia ao executar no contexto da reunião.

### <a name="getparticipant-api"></a>GetParticipant API

> [!NOTE]
>
> * Não armazenar em cache as funções do participante, pois o organizador da reunião pode alterar uma função a qualquer momento.
>
> * No momento, o Teams não dá suporte a grandes listas de distribuição ou tamanhos de lista de mais de 350 participantes para a `GetParticipant` API.

#### <a name="query-parameters"></a>Parâmetros de consulta

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**meetingId**| string | Sim | O identificador de reunião está disponível por meio do Bot Invoke e do SDK do Cliente do Teams.|
|**participantId**| string | Sim | O participantId é a ID do usuário. Ele está disponível em Tab SSO, Bot Invoke e Teams Client SDK. É altamente recomendável obter um participantId do SSO da guia. |
|**tenantId**| string | Sim | A tenantId é necessária para os usuários do locatário. Ele está disponível em Tab SSO, Bot Invoke e Teams Client SDK. É altamente recomendável obter um tenantId do SSO tab. |

#### <a name="example"></a>Exemplo

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

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
            TeamsMeetingParticipant participant = GetMeetingParticipantAsync(turnContext, "yourMeetingId", "yourParticipantId", "yourTenantId");
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

O corpo da resposta é:

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

* * *

#### <a name="response-codes"></a>Códigos de resposta

* **403**: O aplicativo não tem permissão para obter informações do participante. Essa é a resposta de erro mais comum e é disparada se o aplicativo não estiver instalado na reunião. Por exemplo, se o aplicativo for desabilitado pelo administrador do locatário ou bloqueado durante a mitigação de livesite.
* **200**: Informações do participante recuperadas com êxito.
* **401**: Token inválido.
* **404**: O participante não pode ser encontrado.
* **500**: A reunião expirou (mais de 60 dias desde o fim da reunião) ou o participante não tem permissões com base em sua função.


**Em breve**

* **404**: A reunião expirou ou o participante não pode ser encontrado.


### <a name="notificationsignal-api"></a>NotificationSignal API

Todos os usuários em uma reunião recebem as notificações enviadas por meio da API NotificationSignal.

> [!NOTE]
> Atualmente, não há suporte para o envio de notificações com destino.
> Quando uma caixa de diálogo na reunião é invocada, o mesmo conteúdo também será apresentado como uma mensagem de chat.

#### <a name="query-parameters"></a>Parâmetros de consulta

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**conversationId**| string | Sim | O identificador de conversa está disponível como parte da invocação de bot |

#### <a name="example"></a>Exemplo

O `Bot ID` é declarado no manifesto e o bot recebe um objeto de resultado. No exemplo a seguir, `completionBotId` o parâmetro do é opcional na carga `externalResourceUrl` solicitada:

> [!NOTE]
> * Os `externalResourceUrl` parâmetros de largura e altura devem estar em pixels. Para garantir que as dimensões estão dentro dos limites permitidos, consulte [diretrizes de design](design/designing-apps-in-meetings.md).
> * A URL é a página carregada como `<iframe>` uma na caixa de diálogo na reunião. O domínio deve estar na matriz do aplicativo `validDomains` no manifesto do aplicativo.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

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

* **201**: A atividade com sinal é enviada com êxito. 
* **401**: Token inválido.
* **403**: O aplicativo não consegue enviar o sinal. Isso pode acontecer devido a vários motivos, como o administrador de locatários desabilita o aplicativo, o aplicativo é bloqueado durante a migração de site ao vivo e assim por diante. Nesse caso, a carga contém uma mensagem de erro detalhada. 
* **404**: O chat de reunião não existe.
 

## <a name="enable-your-app-for-teams-meetings"></a>Habilitar seu aplicativo para reuniões do Teams

### <a name="update-your-app-manifest"></a>Atualizar o manifesto do aplicativo

Os recursos do aplicativo de reuniões são declarados no manifesto do aplicativo por meio dos **escopos configurbleTabs**  ->   e **matrizes de** contexto. *O* escopo define a quem e *o contexto* define onde seu aplicativo estará disponível.

> [!NOTE]
> Use o [esquema de manifesto de Visualização do Desenvolvedor](../resources/schema/manifest-schema-dev-preview.md) para experimentar isso no manifesto do aplicativo.

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

A guia e as propriedades funcionam em harmonia para permitir que você `context` determine onde deseja que seu aplicativo `scopes` apareça. Guias no `team` escopo ou podem `groupchat` ter mais de um contexto. Os valores possíveis para a propriedade context são os seguinte:

* **channelTab**: uma guia no header de um canal de equipe.
* **privateChatTab**: uma guia no header de um chat de grupo entre um conjunto de usuários que não estão no contexto de uma equipe ou reunião.
* **meetingChatTab**: uma guia no header de um chat de grupo entre um conjunto de usuários no contexto de uma reunião agendada.
* **meetingDetailsTab**: uma guia no header da exibição de detalhes da reunião do calendário.
* **meetingSidePanel**: um painel in-meeting aberto por meio da barra unificada (u-bar).

> [!NOTE]
> Atualmente, a propriedade "Context" não tem suporte e, portanto, será ignorada em clientes móveis

## <a name="configure-your-app-for-meeting-scenarios"></a>Configurar seu aplicativo para cenários de reunião

> [!NOTE]
> * Para que seu aplicativo seja visível na galeria de guias, ele precisa dar suporte a guias **configuráveis** e ao escopo **de chat de grupo.**
>
> * Os clientes móveis só suportam guias em Superfícies de Pré e Pós-Reunião. As experiências na reunião (caixa de diálogo e guia na reunião) no celular estarão disponíveis em breve. Siga as [diretrizes para guias em dispositivos móveis](../tabs/design/tabs-mobile.md) ao criar suas guias para dispositivos móveis.

### <a name="before-a-meeting"></a>Antes de uma reunião

Os usuários com funções de organizador e/ou apresentador adicionam guias a uma reunião usando o botão mais ➕ nas páginas de detalhes do **Chat** e **reunião da** reunião. Extensões de mensagens são adicionadas por meio do menu de releições/estouro &#x25CF;&#x25CF;&#x25CF; localizado abaixo da área de mensagem de composição no chat. Bots são adicionados a um chat de reunião usando a **@** tecla " " e **selecionando Obter bots**.

✔ A identidade do *usuário deve* ser confirmada por meio das guias [SSO](../tabs/how-to/authentication/auth-aad-sso.md). Após essa autenticação, o aplicativo pode recuperar a função de usuário por meio da API GetParticipant.

 ✔ com base na função de usuário, o aplicativo agora terá a capacidade de apresentar experiências específicas de função. Por exemplo, um aplicativo de sondagem pode permitir que apenas organizadores e apresentadores criem uma nova sondagem.

> **OBSERVAÇÃO**: as atribuições de função podem ser alteradas enquanto uma reunião está em andamento.  *Consulte* [Funções em uma reunião do Teams](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019). 

### <a name="during-a-meeting"></a>Durante uma reunião

#### <a name="sidepanel"></a>**sidePanel**

✔ Adicionar **sidePanel** no manifesto do aplicativo à matriz **de** contexto conforme descrito acima.

✔ Na reunião, bem como em todos os cenários, o aplicativo será renderizado em uma guia na reunião que tem 320px de largura. Sua guia deve ser otimizada para isso. *Consulte*, [interface FrameContext](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/framecontext?view=msteams-client-js-latest&preserve-view=true
)

✔Referir ao [SDK](../tabs/how-to/access-teams-context.md#user-context) do Teams para usar a API **userContext** para rotear solicitações de acordo.

✔ Consulte o fluxo de [autenticação do Teams para guias](../tabs/how-to/authentication/auth-flow-tab.md). O fluxo de autenticação para guias é muito semelhante ao fluxo de autenticação para sites. Assim, as guias podem usar o OAuth 2.0 diretamente. *Consulte também*, Plataforma de identidade da Microsoft e fluxo de código de autorização [OAuth 2.0](/azure/active-directory/develop/v2-oauth2-auth-code-flow).

✔ Extensão de mensagem deve funcionar conforme o esperado quando um usuário estiver em uma exibição em reunião e deve ser capaz de postar cartões de extensão de mensagem de composição.

✔ AppName na reunião - Dica de ferramenta deve dizer o nome do aplicativo na barra U-bar de reunião.

#### <a name="in-meeting-dialog"></a>**Caixa de diálogo na reunião**

✔ Você deve seguir as diretrizes de design da caixa de [diálogo na reunião.](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)

✔ Consulte o fluxo de [autenticação do Teams para guias](../tabs/how-to/authentication/auth-flow-tab.md).

✔ Use a [API NotificationSignal](create-apps-for-teams-meetings.md#notificationsignal-api) para sinalizar que uma notificação de bolha precisa ser disparada.

✔ Como parte da carga da solicitação de notificação, inclua a URL onde o conteúdo a ser exibido está hospedado.

✔ caixa de diálogo In-meeting não deve usar o módulo de tarefa.

> [!NOTE]
>
> * Essas notificações são persistentes na natureza. Você deve invocar [**a função submitTask()**](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) para descartar automaticamente depois que um usuário realizar uma ação no modo de exibição da Web. Esse é um requisito para envio de aplicativo. *Consulte também*, [SDK do Teams: módulo de tarefa](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).
>
> * Se você quiser que seu aplicativo suporte usuários anônimos, sua carga inicial de solicitação de invocação deve depender dos metadados de solicitação (ID do usuário) no objeto, e não nos metadados de solicitação `from.id` `from` (ID do `from.aadObjectId` Azure Active Directory do usuário). *Consulte* [Usando módulos de tarefa em guias](../task-modules-and-cards/task-modules/task-modules-tabs.md) e Criar e enviar o módulo de [tarefa](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).

### <a name="after-a-meeting"></a>Após uma reunião

As configurações pós-reunião e pré-reunião são equivalentes.

## <a name="meeting-app-sample"></a>Exemplo de aplicativo de reunião

 > [!div class="nextstepaction"]
> [Aplicativo gerador de token de reunião](https://github.com/OfficeDev/microsoft-teams-sample-meetings-token)
