---
title: Criar aplicativos para reuniões do Teams
author: laujan
description: criar aplicativos para reuniões do teams
ms.topic: conceptual
ms.author: lajanuar
keywords: API de função de participante do usuário de reuniões de aplicativos do teams
ms.openlocfilehash: e80dd50590d9e0828ab094c691a6b8e07ace3b0c
ms.sourcegitcommit: d61f14053fc695bc1956bf50e83956613c19ccca
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/13/2020
ms.locfileid: "48452621"
---
# <a name="create-apps-for-teams-meetings-developer-preview"></a>Criar aplicativos para reuniões do Teams (Developer Preview)

>[!IMPORTANT]
> Os recursos incluídos no Microsoft Teams Developer Preview são fornecidos apenas para fins de acesso antecipado, teste e comentários. Eles podem sofrer alterações antes de ficarem disponíveis no lançamento público e não devem ser usados em aplicativos de produção.

## <a name="prerequisites-and-considerations"></a>Pré-requisitos e considerações

1. Os aplicativos nas reuniões exigem alguns conhecimentos básicos do [desenvolvimento de aplicativos do teams](../overview.md). Um aplicativo em uma reunião pode consistir em [guias](../tabs/what-are-tabs.md), [bots](../bots/what-are-bots.md)e recursos de [extensões de mensagens](../messaging-extensions/what-are-messaging-extensions.md) e exigirá atualizações para o [manifesto do aplicativo](#update-your-app-manifest) Teams para indicar que o aplicativo está disponível para reuniões

1. Para que seu aplicativo funcione no ciclo de vida da reunião como uma guia, ele deve suportar guias configuráveis no [escopo Groupchat](../resources/schema/manifest-schema.md#configurabletabs). *Confira* [estender seu aplicativo do Microsoft Teams com uma guia personalizada](../tabs/how-to/add-tab.md). O suporte ao `groupchat` escopo habilitará o aplicativo em bate-papos [post-meeting](teams-apps-in-meetings.md#post-meeting-app-experience) de [pré](teams-apps-in-meetings.md#pre-meeting-app-experience) e reunião.

1. Os parâmetros de URL da API da reunião podem exigir `meetingId` , `userId` e a [tenantid](/onedrive/find-your-office-365-tenant-id) estão disponíveis como parte da atividade SDK e bot do cliente do teams. Além disso, as informações confiáveis para ID de usuário e ID de locatário podem ser recuperadas usando a [autenticação de SSO de guia](../tabs/how-to/authentication/auth-aad-sso.md).

1. Algumas APIs de reunião, como `GetParticipant` exigirão um [registro de bot e uma ID de aplicativo de bot](../bots/how-to/create-a-bot-for-teams.md#with-an-azure-subscription) para gerar tokens de autenticação.

1. Os desenvolvedores devem aderir às diretrizes gerais de [design da guia do teams](../tabs/design/tabs.md) para cenários anteriores e posteriores à reunião, bem como as [diretrizes de diálogo na](design/designing-in-meeting-dialog.md) reunião para a caixa de diálogo na reunião disparada durante uma reunião do teams.

## <a name="meeting-apps-api-reference"></a>Referência da API de aplicativos de reunião

|API|Descrição|Solicitação|Origem|
|---|---|----|---|
|**UserContext**| Obter informações contextuais para exibir conteúdo relevante em uma guia do teams. |_**microsoftTeams. GetContext (() => {/*...* / } )**_|SDK de cliente do Microsoft Teams|
|**Getparticipante**|Essa API permite que um bot busque informações do participante por ID de reunião e ID de participante.|**Obter** _ **/v1/Meetings/{meetingId}/participants/{participantId}? tenantid = {tenantid}**_ |SDK do Microsoft bot Framework|
|**NotificationSignal** |Os sinais de reunião serão entregues usando a seguinte API de notificação de conversa existente (para chat do usuário-bot). Essa API permite que os desenvolvedores sinalizem com base na ação do usuário final para mostrar uma bolha de diálogo na reunião.|**Postar** _ **/v3/Conversations/{conversationId}/Activities**_|SDK do Microsoft bot Framework|

### <a name="getusercontext"></a>UserContext

Confira a documentação [obter o contexto da guia de suas equipes](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library) para obter orientação sobre como identificar e recuperar informações contextuais para o seu conteúdo de guia. Como parte da extensibilidade de reuniões, um novo valor foi adicionado para a carga de resposta:

✔ **MeetingID**: usada por uma guia ao executar no contexto da reunião.

### <a name="getparticipant-api"></a>API getparticipante

> [!NOTE]
>
> * Não armazenar as funções do participante em cache, pois o organizador da reunião pode alterar uma função em um determinado momento.
>
> * O Microsoft Teams atualmente não oferece suporte a grandes listas de distribuição ou tamanhos de lista de mais de 350 participantes da `GetParticipant` API.
>
> * O suporte para o SDK da estrutura de bot estará disponível em breve.

#### <a name="request"></a>Solicitação

```http
GET /v3/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}
```

*Consulte* a [referência da API do bot Framework](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true).

<!-- markdownlint-disable MD025 -->

**Exemplo de C#**

```csharp
string meetingId = "meetingid?";
string participantId = "participantidhere";
var connectorClient = turnContext.TurnState.Get<IConnectorClient>();
var creds = connectorClient.Credentials as AppCredentials;
var bearerToken = await creds.GetTokenAsync().ConfigureAwait(false);
var request = new HttpRequestMessage();
request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", bearerToken);
request.Method = new HttpMethod("GET");
request.RequestUri = new System.Uri(Path.Combine(connectorClient.BaseUri.OriginalString, $"/meetings/{meetingId}/participants/{participantId}"));
HttpResponseMessage response = await (connectorClient as ServiceClient<ConnectorClient>).HttpClient.SendAsync(request, cancellationToken).ConfigureAwait(false);
if (response.StatusCode == System.Net.HttpStatusCode.OK)
{
    var content = await response.Content.ReadAsStringAsync().ConfigureAwait(false);
    var theObject = Rest.Serialization.SafeJsonConvert.DeserializeObject<WhateverObjectIsReturned>(content, connectorClient.DeserializationSettings);
}
```

* * *
<!-- markdownlint-disable MD001 -->

#### <a name="query-parameters"></a>Parâmetros de consulta

**MeetingID**. O identificador da reunião é obrigatório.  
**participante**de. O identificador do participante é obrigatório.  
**tenantid**. [ID do locatário](/onedrive/find-your-office-365-tenant-id) do participante. Necessário para o usuário do locatário.

#### <a name="response-payload"></a>Carga de resposta
<!-- markdownlint-disable MD036 -->

o **meetingRole** pode ser *organizador*, *apresentador*ou *participante*.

**Exemplo 1**

```json
{
  "user":
  {
      "id": "29:1JKiJGPAX9TTxtGxhVo0wLx_zwzo-gG8Z-X03306vBwi9p-xMTEbDXsT6KH7-0kkTS8cD-2zkrsoV6f5WJ6_aYw",
      "aadObjectId": "6aebbad0-e5a5-424a-834a-20fb051f3c1a",
      "name": "Allan Deyoung",
      "givenName": "Allan",
      "surname": "Deyoung",
      "email": "Allan.Deyoung@microsoft.com",
      "userPrincipalName": "Allan.Deyoung@microsoft.com",
      "tenantId": "72f988bf-86f1-41af-91ab-2d7cd011db47",
  },
  "meeting":
  {
      "role ": "Presenter",
      "inMeeting":true
  },
  "conversation":
  {
      "id": "<conversation id>"
  }
}
```
#### <a name="response-codes"></a>Códigos de resposta

**403**: o aplicativo não tem permissão para obter informações do participante. Esta será a resposta de erro mais comum e será disparada quando o aplicativo não estiver instalado na reunião, como quando o aplicativo é desabilitado pelo administrador de locatários ou bloqueado durante a mitigação de site ativo.  
**200**: informações do participante recuperadas com êxito  
**401**: token inválido  
**404**: a reunião não existe ou o participante não pode ser encontrado.

<!-- markdownlint-disable MD024 -->
### <a name="notificationsignal-api"></a>API NotificationSignal

> [!NOTE]
> Quando uma caixa de diálogo na reunião é chamada, o mesmo conteúdo também será apresentado como uma mensagem de chat.

#### <a name="request"></a>Solicitação

```http
POST /v3/conversations/{conversationId}/activities
```

#### <a name="query-parameters"></a>Parâmetros de consulta

**Conversation**: o identificador de conversa. Obrigatório

**completionBotId**: esta é a ID do bot. Opcional

#### <a name="request-payload"></a>Carga de solicitação

# <a name="json"></a>[JSON](#tab/json)

```json
{
    "type": "message",
    "text": "John Phillips assigned you a weekly todo",
    "summary": "Don't forget to meet with Marketing next week",
    "channelData": {
        "notification": {
            "alertInMeeting": true,
            "externalResourceUrl": "https://teams.microsoft.com/l/bubble/APP_ID?url=<TaskInfo.url>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID"
        }
    },
    "replyToId": "1493070356924"
}
```

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
Activity activity = MessageFactory.Text("This is a meeting signal test");
MeetingNotification notification = new MeetingNotification
  {
    AlertInMeeting = true,
    ExternalResourceUrl = "https://teams.microsoft.com/l/bubble/APP_ID?url=<TaskInfo.url>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID"
  };
activity.ChannelData = new TeamsChannelData
  {
    Notification = notification
  };
await turnContext.SendActivityAsync(activity).ConfigureAwait(false);
```

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```javascript

const replyActivity = MessageFactory.text('Hi'); // this could be an adaptive card instead
        replyActivity.channelData = {
            notification: {
                alertInMeeting: true,
                externalResourceUrl: 'https://teams.microsoft.com/l/bubble/APP_ID?url=<TaskInfo.url>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID’
            }
        };
await context.sendActivity(replyActivity);
```

* * *

> [!IMPORTANT]
> A URL na bolha de conteúdo (URL taskInfo) deve estar incluída na lista de [domínios válidos](../resources/schema/manifest-schema.md#validdomains) incluída no manifesto do aplicativo Teams.

#### <a name="response-codes"></a>Códigos de resposta

**201**: atividade com sinal enviado com êxito  
**401**: token inválido  
**403**: o aplicativo não tem permissão para enviar o sinal. Nesse caso, a carga deve conter uma mensagem de erro mais detalhada. Podem existir vários motivos: aplicativo desabilitado pelo administrador de locatários, bloqueado durante a mitigação de sites ativos, etc.  
**404**: o chat de reunião não existe  

## <a name="enable-your-app-for-teams-meetings"></a>Habilitar o aplicativo para reuniões do teams

### <a name="update-your-app-manifest"></a>Atualizar o manifesto do aplicativo

As funcionalidades de aplicativos de reuniões são declaradas em seu **configurableTabs**manifesto de aplicativo por meio de  ->  **escopos** configurableTabs e matrizes de **contexto** . O *escopo* define para quem e o *contexto* define onde seu aplicativo estará disponível.

> [!NOTE]
> * Use o [esquema de manifesto da visualização do desenvolvedor](../resources/schema/manifest-schema-dev-preview.md) para experimentá-lo em seu manifesto de aplicativo.
> * Atualmente, a plataforma móvel oferece suporte somente ao esquema de manifesto 1,6
> * A plataforma móvel oferece suporte a guias apenas nas superfícies de reunião prévia e posterior. As experiências de reunião (guia e caixa de diálogo na reunião) no Mobile estarão disponíveis em breve

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

A guia `context` e `scopes` as propriedades funcionam em harmonia para permitir que você determine onde você deseja que seu aplicativo apareça. As guias no `team` `groupchat` escopo ou podem ter mais de um contexto. Os valores possíveis para a propriedade Context são os seguintes:

* **channelTab**: uma guia no cabeçalho de um canal de equipe.
* **privateChatTab**: uma guia no cabeçalho de um grupo bate-papo entre um conjunto de usuários que não estão no contexto de uma equipe ou reunião.
* **meetingChatTab**: uma guia no cabeçalho de um chat de grupo entre um conjunto de usuários no contexto de uma reunião agendada.
* **meetingDetailsTab**: uma guia no cabeçalho do modo de exibição detalhes da reunião do calendário.
* **meetingSidePanel**: um painel na reunião aberto por meio da barra unificada (u-bar).

## <a name="configure-your-app-for-meeting-scenarios"></a>Configurar seu aplicativo para cenários de reunião

> [!NOTE]
> Para que seu aplicativo fique visível na Galeria de guias, ele precisa **suportar guias configuráveis** e o **escopo de chat de grupo**.

### <a name="pre-meeting"></a>Pré-reunião

Os usuários com funções de organizador e/ou apresentador adicionam guias a uma reunião usando o botão mais ➕ nas páginas **chat** de reunião e **detalhes** da reunião. As extensões de mensagens são adicionadas ao via menu de reticências/estouro &#x25CF;&#x25CF;&#x25CF; localizada abaixo da área de mensagem de composição no chat. Os bots são adicionados a um chat de reunião usando a **@** tecla "" e selecionando **obter bots**.

✔ A identidade do usuário *deve* ser confirmada por meio de [guias de SSO](../tabs/how-to/authentication/auth-aad-sso.md). Após essa autenticação, o aplicativo pode recuperar a função de usuário por meio da API getparticipante.

 ✔ Com base na função de usuário, o aplicativo agora terá a capacidade de apresentar experiências específicas de função. Por exemplo, um aplicativo de sondagem pode permitir que somente os organizadores e os apresentadores criem uma nova pesquisa.

> **Observação**: as atribuições de função podem ser alteradas enquanto uma reunião estiver em andamento.  *Consulte* [funções em uma reunião do teams](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019). 

### <a name="in-meeting"></a>Na reunião

#### <a name="sidepanel"></a>**sidePanel**

✔ Em seu manifesto de aplicativo, adicione **sidePanel** à matriz de **contexto** , conforme descrito acima.

✔ Na reunião, bem como em todos os cenários, o aplicativo será renderizado em uma guia na reunião que tenha 320px de largura. Sua guia deve ser otimizada para isso. *Consulte* [FrameContext interface](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true)

✔ Consultar o [SDK do teams](../tabs/how-to/access-teams-context.md#user-context) para usar a API **userContext** para rotear as solicitações de acordo.

✔ Consulte o fluxo de autenticação do Microsoft [Teams para guias](../tabs/how-to/authentication/auth-flow-tab.md). O fluxo de autenticação para guias é muito semelhante ao fluxo de autenticação para sites. Portanto, as guias podem usar o OAuth 2,0 diretamente. *Confira também*a [plataforma de identidade da Microsoft e o fluxo de código de autorização do OAuth 2,0](/azure/active-directory/develop/v2-oauth2-auth-code-flow).

#### <a name="in-meeting-dialog"></a>**caixa de diálogo na reunião**

✔ Você deve cumprir as diretrizes de [design da caixa de diálogo na reunião](design/designing-in-meeting-dialog.md).

✔ Consulte o fluxo de autenticação do Microsoft [Teams para guias](../tabs/how-to/authentication/auth-flow-tab.md).

✔ Usar a API de [notificação](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) para sinalizar que uma notificação de bolha precisa ser disparada.

✔ Como parte da carga de solicitação de notificação, inclua a URL onde o conteúdo a ser expedido está hospedado.

> [!NOTE]
>
> * Essas notificações são persistentes por natureza. Você deve chamar a função [**submitTask ()**](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) para descartar automaticamente após um usuário executar uma ação no modo de exibição da Web. Esse é um requisito para o envio de aplicativos. *Consulte também*, [SDK do teams: módulo de tarefa](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).
>
> * Se quiser que seu aplicativo dê suporte a usuários anônimos, a carga de solicitação de chamada inicial deve confiar no `from.id`  (ID do usuário) solicitar metadados no `from` objeto, e não no `from.aadObjectId` (Azure Active Directory ID do usuário) solicitar metadados. *Consulte* [usando módulos de tarefas em guias](../task-modules-and-cards/task-modules/task-modules-tabs.md) e [criar e enviar o módulo de tarefa](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).

### <a name="post-meeting"></a>Pós-reunião

As configurações pós-instalação e pré-reunião são equivalentes.

## <a name="meeting-app-sample"></a>Exemplo de aplicativo de reunião

 > [!div class="nextstepaction"]
> [Aplicativo gerador de token de reunião](https://github.com/OfficeDev/microsoft-teams-sample-meetings-token)
