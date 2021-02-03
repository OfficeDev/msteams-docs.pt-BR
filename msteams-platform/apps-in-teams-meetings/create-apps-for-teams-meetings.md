---
title: Criar aplicativos para reuniões do Teams
author: laujan
description: criar aplicativos para reuniões de equipes
ms.topic: conceptual
ms.author: lajanuar
keywords: teams apps meetings user participant role api
ms.openlocfilehash: 7f6d8fec735aa21033c6bcb2462c20458634f10a
ms.sourcegitcommit: 843da1730443ff8474a05295f60a6b376ed140da
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/02/2021
ms.locfileid: "50073093"
---
# <a name="create-apps-for-teams-meetings"></a>Crie aplicativos para reuniões do Teams

## <a name="prerequisites-and-considerations"></a>Pré-requisitos e considerações

* Os aplicativos em reuniões exigem algum conhecimento básico do [desenvolvimento de aplicativos do Teams.](../overview.md) Um aplicativo em uma reunião pode ser composto de [guias,](../tabs/what-are-tabs.md) [bots](../bots/what-are-bots.md)e recursos de extensões de mensagens e exigirá atualizações no manifesto do aplicativo [Teams](#update-your-app-manifest) para indicar que o aplicativo está disponível para reuniões [](../messaging-extensions/what-are-messaging-extensions.md)

* Para que seu aplicativo funcione no ciclo de vida da reunião como uma guia, ele deve dar suporte a guias configuráveis no escopo [de chat](../resources/schema/manifest-schema.md#configurabletabs) em grupo (veja como criar uma guia [de grupo).](../build-your-first-app/build-channel-tab.md) O suporte `groupchat` ao escopo habilita o aplicativo em [chats pré-reunião](teams-apps-in-meetings.md#pre-meeting-app-experience) e [pós-reunião.](teams-apps-in-meetings.md#post-meeting-app-experience)

* Os parâmetros de URL da API de Reunião podem exigir , e tenantId Eles estão disponíveis como parte da atividade de bot e SDK de cliente do `meetingId` `userId` Teams. [](/onedrive/find-your-office-365-tenant-id) Além disso, informações confiáveis para a ID de usuário e a ID do locatário podem ser recuperadas usando a autenticação [SSO da guia.](../tabs/how-to/authentication/auth-aad-sso.md)

* Algumas APIs de reunião, como , exigem um registro de bot e `GetParticipant` [ID](../build-your-first-app/build-bot.md) para gerar tokens de auth.

* Você deve seguir as [diretrizes gerais de design](../tabs/design/tabs.md) de guia do Teams para cenários pré e pós-reunião. Para experiências durante reuniões, consulte as [](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog) diretrizes [de](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab) design da caixa de diálogo na reunião e da guia na reunião.

* Para que seu aplicativo seja atualizado em tempo real, ele deve estar atualizado com base nas atividades do evento na reunião. Esses eventos podem estar dentro da caixa de diálogo na reunião (consulte o parâmetro de conclusão em) e outras superfícies no ciclo de vida `bot Id` `Notification Signal API` da reunião

## <a name="meeting-apps-api-reference"></a>Referência da API de aplicativos de reunião

|API|Descrição|Solicitação|Source|
|---|---|----|---|
|**GetUserContext**| Obter informações contextuais para exibir conteúdo relevante em uma guia do Teams. |_**microsoftTeams.getContext( ( ) => { /*...* / } )**_|SDK do cliente Microsoft Teams|
|**GetParticipant**|Essa API permite que um bot busque informações de um participante por ID da reunião e ID do participante.|**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_ |Microsoft Bot Framework SDK|
|**NotificationSignal** |Os sinais de reunião serão entregues usando a seguinte API de notificação de conversa existente (para chat user-bot). Essa API permite que os desenvolvedores sinalizem com base na ação do usuário final para mostrar caso de uma bolha de caixa de diálogo na reunião.|**POST** _**/v3/conversations/{conversationId}/activities**_|Microsoft Bot Framework SDK|

### <a name="getusercontext"></a>GetUserContext

Confira nosso contexto obter [a documentação](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library) da guia Teams para obter orientação sobre como identificar e recuperar informações contextuais para o conteúdo da guia. Como parte da extensibilidade de reuniões, um novo valor foi adicionado para a carga de resposta:

✔ **meetingId**: usada por uma guia ao ser executado no contexto da reunião.

### <a name="getparticipant-api"></a>GetParticipant API

> [!NOTE]
>
> * Não armazenar em cache as funções dos participantes, pois o organizador da reunião pode alterar uma função a qualquer momento.
>
> * No momento, o Teams não dá suporte a listas de distribuição grandes ou tamanhos de lista de participantes com mais de 350 participantes para a `GetParticipant` API.

#### <a name="query-parameters"></a>Parâmetros de consulta

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**meetingId**| string | Sim | O identificador da reunião está disponível por meio do Bot Invoke e do SDK do Cliente do Teams.|
|**participantId**| string | Sim | A participantId é a ID de usuário. Ele está disponível no SSO da guia, no Bot Invoke e no SDK do cliente do Teams. É altamente recomendável obter uma participantId do SSO da guia. |
|**tenantId**| string | Sim | A tenantId é necessária para os usuários do locatário. Ele está disponível no SSO da guia, no Bot Invoke e no SDK do cliente do Teams. É altamente recomendável obter uma tenantId do SSO da guia. |

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
GET /v3/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}
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

* **403**: O aplicativo não tem permissão para obter informações dos participantes.  Essa é a resposta de erro mais comum e é disparada se o aplicativo não estiver instalado na reunião. Por exemplo, se o aplicativo for desabilitado pelo administrador do locatário ou bloqueado durante a migração do site ao vivo.
* **200**: Informações do participante recuperadas com êxito.
* **401**: Token inválido.
* **404**: Não foi possível encontrar o participante.
* **500**: A reunião expirou (mais de 60 dias desde o fim da reunião) ou o participante não tem permissões baseadas em sua função.


**Em breve**

* **404**: A reunião expirou ou o participante não foi encontrado.


### <a name="notificationsignal-api"></a>NotificationSignal API

> [!NOTE]
> Quando uma caixa de diálogo na reunião é invocada, o mesmo conteúdo também será apresentado como uma mensagem de chat.

#### <a name="query-parameters"></a>Parâmetros de consulta

|Valor|Tipo|Obrigatório|Descrição|
|---|---|----|---|
|**conversationId**| string | Sim | O identificador de conversa está disponível como parte da invocação de bot |

#### <a name="example"></a>Exemplo

> [!NOTE]
>
O `completionBotId` parâmetro é opcional no exemplo de carga `externalResourceUrl` solicitada. `Bot ID` é declarado no manifesto e o bot recebe um objeto de resultado.
> * Os parâmetros de largura e altura externalResourceUrl devem estar em pixels. Consulte as [diretrizes de design](design/designing-apps-in-meetings.md) para garantir que as dimensões estão dentro dos limites permitidos.
> * A URL é a página carregada como uma `<iframe>` caixa de diálogo na reunião. O domínio deve estar na matriz do aplicativo `validDomains` no manifesto do aplicativo.

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

* **201**: a atividade com sinal é enviada com êxito  
* **401**: token inválido  
* **201**: A atividade com sinal é enviada com êxito. 
* **401**: Token inválido.
* **403**: O aplicativo não pode enviar o sinal. Isso pode acontecer devido a vários motivos, como o administrador de locatários desabilita o aplicativo, o aplicativo é bloqueado durante a migração ao vivo do site e assim por diante. Nesse caso, a carga contém uma mensagem de erro detalhada. 
* **404**: O chat de reunião não existe.
 

## <a name="enable-your-app-for-teams-meetings"></a>Habilitar seu aplicativo para reuniões do Teams

### <a name="update-your-app-manifest"></a>Atualizar o manifesto do aplicativo

Os recursos do aplicativo de reuniões são declarados no manifesto do aplicativo por meio dos **escopos configurbleTabs**  ->  **e** **matrizes de** contexto. *O* escopo define para quem e *o contexto* define onde seu aplicativo estará disponível.

> [!NOTE]
> Use o [esquema de manifesto da](../resources/schema/manifest-schema-dev-preview.md) Visualização do Desenvolvedor para experimentar isso no manifesto do aplicativo.

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

A guia e as propriedades funcionam em harmonia para permitir que você `context` determine onde deseja que seu aplicativo `scopes` apareça. As guias no escopo `team` ou no escopo podem ter mais de um `groupchat` contexto. Os valores possíveis para a propriedade de contexto são:

* **channelTab**: uma guia no header de um canal de equipe.
* **privateChatTab**: uma guia no header de um chat de grupo entre um conjunto de usuários que não estão no contexto de uma equipe ou reunião.
* **meetingChatTab**: uma guia no início de um chat de grupo entre um conjunto de usuários no contexto de uma reunião agendada.
* **meetingDetailsTab**: uma guia no header da exibição de detalhes da reunião do calendário.
* **meetingSidePanel**: um painel na reunião aberto por meio da barra unificada (u-bar).

> [!NOTE]
> No momento, a propriedade "Context" não é suportada e, portanto, será ignorada em clientes móveis

## <a name="configure-your-app-for-meeting-scenarios"></a>Configurar seu aplicativo para cenários de reunião

> [!NOTE]
> * Para que seu aplicativo seja visível na galeria de guias, ele precisa dar suporte a **guias configuráveis** e ao escopo **de chat de grupo.**
>
> * Os clientes móveis só suportam Guias em Superfícies de Pré e Pós-Reunião. As experiências na reunião (caixa de diálogo e guia na reunião) em dispositivos móveis estarão disponíveis em breve. Siga as [orientações para guias em dispositivos móveis](../tabs/design/tabs-mobile.md) ao criar suas guias para dispositivos móveis.

### <a name="before-a-meeting"></a>Antes de uma reunião

Usuários com funções de organizador e/ou apresentador adicionam guias a uma reunião usando o botão mais ➕ nas páginas de detalhes de **chat** **e reunião.** Extensões de mensagens são adicionadas por meio do menu de reellipses/estouro &#x25CF;&#x25CF;&#x25CF; localizado abaixo da área de mensagem de redação no chat. Os bots são adicionados a um chat de reunião usando a **@** tecla " " e selecionando Obter **bots**.

✔ A identidade do *usuário deve* ser confirmada por meio das guias [SSO](../tabs/how-to/authentication/auth-aad-sso.md). Após essa autenticação, o aplicativo pode recuperar a função de usuário por meio da API GetParticipant.

 ✔ Com base na função de usuário, o aplicativo agora terá a capacidade de apresentar experiências específicas da função. Por exemplo, um aplicativo de sondagem pode permitir que apenas organizadores e apresentadores criem uma nova votação.

> **OBSERVAÇÃO:** as atribuições de função podem ser alteradas enquanto uma reunião está em andamento.  *Confira* [Funções em uma reunião do Teams.](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019) 

### <a name="during-a-meeting"></a>Durante uma reunião

#### <a name="sidepanel"></a>**sidePanel**

✔ no manifesto do aplicativo, adicione **sidePanel** à matriz **de contexto** conforme descrito acima.

✔ Na reunião, bem como em todos os cenários, o aplicativo será renderizado em uma guia na reunião que tem 320px de largura. Sua guia deve ser otimizada para isso. *Consulte*, [interface FrameContext](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/framecontext?view=msteams-client-js-latest&preserve-view=true
)

✔Referir ao [SDK](../tabs/how-to/access-teams-context.md#user-context) do Teams para usar a API **userContext** para encaminhar solicitações de acordo.

✔ Confira o fluxo [de autenticação do Teams para guias.](../tabs/how-to/authentication/auth-flow-tab.md) O fluxo de autenticação para guias é muito semelhante ao fluxo de autenticação de sites. Portanto, as guias podem usar o OAuth 2.0 diretamente. *Consulte também*, Microsoft Identity Platform e fluxo de código de autorização do [OAuth 2.0.](/azure/active-directory/develop/v2-oauth2-auth-code-flow)

✔ extensão de mensagem deve funcionar conforme o esperado quando um usuário está em uma exibição de reunião e deve ser capaz de postar cartões de extensão de mensagem de redação.

✔ AppName na reunião - a dica de ferramenta deve dizer o nome do aplicativo na barra U de reunião.

#### <a name="in-meeting-dialog"></a>**Caixa de diálogo na reunião**

✔ Você deve seguir as diretrizes [de design da caixa de diálogo na reunião.](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)

✔ Confira o fluxo [de autenticação do Teams para guias.](../tabs/how-to/authentication/auth-flow-tab.md)

✔ Usar a [API NotificationSignal](create-apps-for-teams-meetings.md#notificationsignal-api) para sinalizar que uma notificação de bolha precisa ser disparada.

✔ Como parte da carga da solicitação de notificação, inclua a URL onde o conteúdo a ser apresentado está hospedado.

✔ caixa de diálogo Na reunião não deve usar o módulo de tarefa.

> [!NOTE]
>
> * Essas notificações são persistentes na natureza. Você deve invocar [**a função submitTask()**](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) para descartar automaticamente depois que um usuário realizar uma ação no modo de exibição da Web. Esse é um requisito para envio de aplicativo. *Consulte também*, [SDK do Teams: módulo de tarefa.](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true)
>
> * Se você quiser que seu aplicativo suporte usuários anônimos, a carga da solicitação de invocação inicial deverá depender dos metadados de solicitação (ID do usuário) no objeto, não nos metadados de solicitação (ID do usuário) do `from.id` `from` `from.aadObjectId` Azure Active Directory. *Consulte* [Usando módulos de tarefa em guias e](../task-modules-and-cards/task-modules/task-modules-tabs.md) Criar e enviar o módulo de [tarefa.](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request)

### <a name="after-a-meeting"></a>Após uma reunião

As configurações pós-reunião e pré-reunião são equivalentes.

## <a name="meeting-app-sample"></a>Exemplo de aplicativo de reunião

 > [!div class="nextstepaction"]
> [Aplicativo gerador de token de reunião](https://github.com/OfficeDev/microsoft-teams-sample-meetings-token)
