---
title: Criar aplicativos para reuniões do teams
author: laujan
description: criar aplicativos para reuniões do teams
ms.topic: conceptual
ms.author: lajanuar
keywords: API de função de participante do usuário de reuniões de aplicativos do teams
ms.openlocfilehash: 83e0a5b53e363a090935b4afa9840dd96c5f7381
ms.sourcegitcommit: b01986739a05c65094618fbe76aeb53d038b1c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48181971"
---
# <a name="create-apps-for-teams-meetings-preview"></a><span data-ttu-id="dfaca-104">Criar aplicativos para reuniões do Teams (visualização)</span><span class="sxs-lookup"><span data-stu-id="dfaca-104">Create apps for Teams meetings (Preview)</span></span>

>[!IMPORTANT]
> <span data-ttu-id="dfaca-105">Os recursos incluídos no Microsoft Teams Preview são fornecidos apenas para fins de acesso antecipado, teste e comentários.</span><span class="sxs-lookup"><span data-stu-id="dfaca-105">Features included in Microsoft Teams preview are provided for early-access, testing, and feedback purposes only.</span></span> <span data-ttu-id="dfaca-106">Eles podem sofrer alterações antes de ficarem disponíveis no lançamento público e não devem ser usados em aplicativos de produção.</span><span class="sxs-lookup"><span data-stu-id="dfaca-106">They may undergo changes before becoming available in the public release and should not be used in production applications.</span></span>

## <a name="prerequisites-and-considerations"></a><span data-ttu-id="dfaca-107">Pré-requisitos e considerações</span><span class="sxs-lookup"><span data-stu-id="dfaca-107">Prerequisites and considerations</span></span>

1. <span data-ttu-id="dfaca-108">Os aplicativos nas reuniões exigem alguns conhecimentos básicos do [desenvolvimento de aplicativos do teams](../overview.md).</span><span class="sxs-lookup"><span data-stu-id="dfaca-108">Apps in meetings require some basic knowledge of [Teams app development](../overview.md).</span></span> <span data-ttu-id="dfaca-109">Um aplicativo em uma reunião pode consistir em [guias](../tabs/what-are-tabs.md), [bots](../bots/what-are-bots.md)e recursos de [extensões de mensagens](../messaging-extensions/what-are-messaging-extensions.md) e exigirá atualizações para o [manifesto do aplicativo](#update-your-app-manifest) Teams para indicar que o aplicativo está disponível para reuniões</span><span class="sxs-lookup"><span data-stu-id="dfaca-109">An app in a meeting can comprise of [tabs](../tabs/what-are-tabs.md), [bots](../bots/what-are-bots.md), and [messaging extensions](../messaging-extensions/what-are-messaging-extensions.md) features and will require updates to the Teams [app manifest](#update-your-app-manifest) to indicate that the app is available for meetings</span></span>

1. <span data-ttu-id="dfaca-110">Para que seu aplicativo funcione no ciclo de vida da reunião como uma guia, ele deve suportar guias configuráveis no [escopo Groupchat](../resources/schema/manifest-schema.md#configurabletabs).</span><span class="sxs-lookup"><span data-stu-id="dfaca-110">For your app to function in the meeting lifecycle as a tab, it must support configurable tabs in the [groupchat scope](../resources/schema/manifest-schema.md#configurabletabs).</span></span> <span data-ttu-id="dfaca-111">*Confira* [estender seu aplicativo do Microsoft Teams com uma guia personalizada](../tabs/how-to/add-tab.md). O suporte ao `groupchat` escopo habilitará o aplicativo em bate-papos [post-meeting](teams-apps-in-meetings.md#post-meeting-app-experience) de [pré](teams-apps-in-meetings.md#pre-meeting-app-experience) e reunião.</span><span class="sxs-lookup"><span data-stu-id="dfaca-111">*See* [Extend your Teams app with a custom tab](../tabs/how-to/add-tab.md). Supporting the `groupchat` scope will enable your app in [pre-meeting](teams-apps-in-meetings.md#pre-meeting-app-experience) and [post-meeting](teams-apps-in-meetings.md#post-meeting-app-experience) chats.</span></span>

1. <span data-ttu-id="dfaca-112">Os parâmetros de URL da API da reunião podem exigir `meetingId` , `userId` e a [tenantid](/onedrive/find-your-office-365-tenant-id) estão disponíveis como parte da atividade SDK e bot do cliente do teams.</span><span class="sxs-lookup"><span data-stu-id="dfaca-112">Meeting API URL parameters may require `meetingId`, `userId`, and the [tenantId](/onedrive/find-your-office-365-tenant-id) These are available as part of the Teams Client SDK and bot activity.</span></span> <span data-ttu-id="dfaca-113">Além disso, as informações confiáveis para ID de usuário e ID de locatário podem ser recuperadas usando a [autenticação de SSO de guia](../tabs/how-to/authentication/auth-aad-sso.md).</span><span class="sxs-lookup"><span data-stu-id="dfaca-113">Additionally, reliable information for user ID and tenant ID can be retrieved using [Tab SSO authentication](../tabs/how-to/authentication/auth-aad-sso.md).</span></span>

1. <span data-ttu-id="dfaca-114">Algumas APIs de reunião, como `GetParticipant` exigirão um [registro de bot e uma ID de aplicativo de bot](../bots/how-to/create-a-bot-for-teams.md#with-an-azure-subscription) para gerar tokens de autenticação.</span><span class="sxs-lookup"><span data-stu-id="dfaca-114">Some meeting APIs, such as `GetParticipant` will require a [bot registration and bot app ID](../bots/how-to/create-a-bot-for-teams.md#with-an-azure-subscription) to generate auth tokens.</span></span>

1. <span data-ttu-id="dfaca-115">Os desenvolvedores devem aderir às diretrizes gerais de [design da guia do teams](../tabs/design/tabs.md) para cenários anteriores e posteriores à reunião, bem como as [diretrizes de diálogo na](designing-in-meeting-dialog.md) reunião para a caixa de diálogo na reunião disparada durante uma reunião do teams.</span><span class="sxs-lookup"><span data-stu-id="dfaca-115">Developers must adhere to general [Teams tab design guidelines](../tabs/design/tabs.md) for pre- and post-meeting scenarios as well as the [in-meeting dialog guidelines](designing-in-meeting-dialog.md) for in-meeting dialog triggered during a Teams meeting.</span></span>

## <a name="meeting-apps-api-reference"></a><span data-ttu-id="dfaca-116">Referência da API de aplicativos de reunião</span><span class="sxs-lookup"><span data-stu-id="dfaca-116">Meeting apps API reference</span></span>

|<span data-ttu-id="dfaca-117">API</span><span class="sxs-lookup"><span data-stu-id="dfaca-117">API</span></span>|<span data-ttu-id="dfaca-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="dfaca-118">Description</span></span>|<span data-ttu-id="dfaca-119">Solicitação</span><span class="sxs-lookup"><span data-stu-id="dfaca-119">Request</span></span>|<span data-ttu-id="dfaca-120">Origem</span><span class="sxs-lookup"><span data-stu-id="dfaca-120">Source</span></span>|
|---|---|----|---|
|<span data-ttu-id="dfaca-121">**UserContext**</span><span class="sxs-lookup"><span data-stu-id="dfaca-121">**GetUserContext**</span></span>| <span data-ttu-id="dfaca-122">Obter informações contextuais para exibir conteúdo relevante em uma guia do teams.</span><span class="sxs-lookup"><span data-stu-id="dfaca-122">Get contextual information to display relevant content in a Teams tab.</span></span> |<span data-ttu-id="dfaca-123">_**microsoftTeams. GetContext (() => {/*...\* / } )*\*_</span><span class="sxs-lookup"><span data-stu-id="dfaca-123">_**microsoftTeams.getContext( ( ) => {  /*...*/ } )**_</span></span>|<span data-ttu-id="dfaca-124">SDK de cliente do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="dfaca-124">Microsoft Teams client SDK</span></span>|
|<span data-ttu-id="dfaca-125">**Getparticipante**</span><span class="sxs-lookup"><span data-stu-id="dfaca-125">**GetParticipant**</span></span>|<span data-ttu-id="dfaca-126">Essa API permite que um bot busque informações do participante por ID de reunião e ID de participante.</span><span class="sxs-lookup"><span data-stu-id="dfaca-126">This API allows a bot to fetch a participant information by meeting id and participant id.</span></span>|<span data-ttu-id="dfaca-127">**Obter** _ **/v1/Meetings/{meetingId}/participants/{participantId}? tenantid = {tenantid}**_</span><span class="sxs-lookup"><span data-stu-id="dfaca-127">**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_</span></span> |<span data-ttu-id="dfaca-128">SDK do Microsoft bot Framework</span><span class="sxs-lookup"><span data-stu-id="dfaca-128">Microsoft Bot Framework SDK</span></span>|
|<span data-ttu-id="dfaca-129">**NotificationSignal**</span><span class="sxs-lookup"><span data-stu-id="dfaca-129">**NotificationSignal**</span></span> |<span data-ttu-id="dfaca-130">Os sinais de reunião serão entregues usando a seguinte API de notificação de conversa existente (para chat do usuário-bot).</span><span class="sxs-lookup"><span data-stu-id="dfaca-130">Meeting signals will be delivered using the following existing conversation notification API (for user-bot chat).</span></span> <span data-ttu-id="dfaca-131">Essa API permite que os desenvolvedores sinalizem com base na ação do usuário final para mostrar uma bolha de diálogo na reunião.</span><span class="sxs-lookup"><span data-stu-id="dfaca-131">This API allows developers to signal based on end-user action to show-case an in-meeting dialog bubble.</span></span>|<span data-ttu-id="dfaca-132">**Postar** _ **/v3/Conversations/{conversationId}/Activities**_</span><span class="sxs-lookup"><span data-stu-id="dfaca-132">**POST** _**/v3/conversations/{conversationId}/activities**_</span></span>|<span data-ttu-id="dfaca-133">SDK do Microsoft bot Framework</span><span class="sxs-lookup"><span data-stu-id="dfaca-133">Microsoft Bot Framework SDK</span></span>|

### <a name="getusercontext"></a><span data-ttu-id="dfaca-134">UserContext</span><span class="sxs-lookup"><span data-stu-id="dfaca-134">GetUserContext</span></span>

<span data-ttu-id="dfaca-135">Confira a documentação [obter o contexto da guia de suas equipes](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library) para obter orientação sobre como identificar e recuperar informações contextuais para o seu conteúdo de guia.</span><span class="sxs-lookup"><span data-stu-id="dfaca-135">Please refer to our [Get context for your Teams tab](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library) documentation for guidance on identifying and  retrieving contextual information for your tab content.</span></span> <span data-ttu-id="dfaca-136">Como parte da extensibilidade de reuniões, um novo valor foi adicionado para a carga de resposta:</span><span class="sxs-lookup"><span data-stu-id="dfaca-136">As part of meetings extensibility, a new value has been added for the response payload:</span></span>

<span data-ttu-id="dfaca-137">✔ **MeetingID**: usada por uma guia ao executar no contexto da reunião.</span><span class="sxs-lookup"><span data-stu-id="dfaca-137">✔ **meetingId**: used by a tab when running in the meeting context.</span></span>

### <a name="getparticipant-api"></a><span data-ttu-id="dfaca-138">API getparticipante</span><span class="sxs-lookup"><span data-stu-id="dfaca-138">GetParticipant API</span></span>

> [!NOTE]
>
> * <span data-ttu-id="dfaca-139">Não armazenar as funções do participante em cache, pois o organizador da reunião pode alterar uma função em um determinado momento.</span><span class="sxs-lookup"><span data-stu-id="dfaca-139">Do not cache participant roles since the meeting organizer can change a role at any point in time.</span></span>
>
> * <span data-ttu-id="dfaca-140">O Microsoft Teams atualmente não oferece suporte a grandes listas de distribuição ou tamanhos de lista de mais de 350 participantes da `GetParticipant` API.</span><span class="sxs-lookup"><span data-stu-id="dfaca-140">Teams does not currently support large distribution lists or roster sizes of more than 350 participants for the `GetParticipant` API.</span></span>
>
> * <span data-ttu-id="dfaca-141">O suporte para o SDK da estrutura de bot estará disponível em breve.</span><span class="sxs-lookup"><span data-stu-id="dfaca-141">Support for the Bot Framework SDK is coming soon.</span></span>

#### <a name="request"></a><span data-ttu-id="dfaca-142">Solicitação</span><span class="sxs-lookup"><span data-stu-id="dfaca-142">Request</span></span>

```http
GET /v3/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}
```

<span data-ttu-id="dfaca-143">*Consulte* a [referência da API do bot Framework](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="dfaca-143">*See* the [Bot Framework API reference](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span>

<!-- markdownlint-disable MD025 -->

<span data-ttu-id="dfaca-144">**Exemplo de C#**</span><span class="sxs-lookup"><span data-stu-id="dfaca-144">**C# Example**</span></span>

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
```

* * *
<!-- markdownlint-disable MD001 -->

#### <a name="query-parameters"></a><span data-ttu-id="dfaca-145">Parâmetros de consulta</span><span class="sxs-lookup"><span data-stu-id="dfaca-145">Query parameters</span></span>

<span data-ttu-id="dfaca-146">**MeetingID**.</span><span class="sxs-lookup"><span data-stu-id="dfaca-146">**meetingId**.</span></span> <span data-ttu-id="dfaca-147">O identificador da reunião é obrigatório.</span><span class="sxs-lookup"><span data-stu-id="dfaca-147">The meeting identifier is required.</span></span>  
<span data-ttu-id="dfaca-148">**participante**de.</span><span class="sxs-lookup"><span data-stu-id="dfaca-148">**participantId**.</span></span> <span data-ttu-id="dfaca-149">O identificador do participante é obrigatório.</span><span class="sxs-lookup"><span data-stu-id="dfaca-149">The participant identifier is required.</span></span>  
<span data-ttu-id="dfaca-150">**tenantid**.</span><span class="sxs-lookup"><span data-stu-id="dfaca-150">**tenantId**.</span></span> <span data-ttu-id="dfaca-151">[ID do locatário](/onedrive/find-your-office-365-tenant-id) do participante.</span><span class="sxs-lookup"><span data-stu-id="dfaca-151">[Tenant id](/onedrive/find-your-office-365-tenant-id) of the participant.</span></span> <span data-ttu-id="dfaca-152">Necessário para o usuário do locatário.</span><span class="sxs-lookup"><span data-stu-id="dfaca-152">Required for tenant user.</span></span>

#### <a name="response-payload"></a><span data-ttu-id="dfaca-153">Carga de resposta</span><span class="sxs-lookup"><span data-stu-id="dfaca-153">Response Payload</span></span>
<!-- markdownlint-disable MD036 -->

<span data-ttu-id="dfaca-154">**Exemplo 1**</span><span class="sxs-lookup"><span data-stu-id="dfaca-154">**Example 1**</span></span>

```json
{
    "meetingRole":"Presenter",
    "conversation":{
            "isGroup": true,
            "id": "19:meeting_NDQxMzg1YjUtMGIzNC00Yjc1LWFmYWYtYzk1MGY2MTMwNjE0@thread.v2"
        }
}
```

<span data-ttu-id="dfaca-155">o **meetingRole** pode ser *organizador*, *apresentador*ou *participante*.</span><span class="sxs-lookup"><span data-stu-id="dfaca-155">**meetingRole** can be *Organizer*, *Presenter*, or *Attendee*.</span></span>

<span data-ttu-id="dfaca-156">**Exemplo 2**</span><span class="sxs-lookup"><span data-stu-id="dfaca-156">**Example 2**</span></span>

```json
{
    "meetingRole": "Attendee",
    "conversation": {
        "isGroup": true,
        "id": "19:meeting_OWIyYWVhZWMtM2ExMi00ZTc2LTg0OGEtYWNhMTM4MmZlZTNj@thread.v2"
        }
}
```

#### <a name="response-codes"></a><span data-ttu-id="dfaca-157">Códigos de resposta</span><span class="sxs-lookup"><span data-stu-id="dfaca-157">Response Codes</span></span>

<span data-ttu-id="dfaca-158">**403**: o aplicativo não tem permissão para obter informações do participante.</span><span class="sxs-lookup"><span data-stu-id="dfaca-158">**403**: the app is not allowed to get participant information.</span></span> <span data-ttu-id="dfaca-159">Esta será a resposta de erro mais comum e será disparada quando o aplicativo não estiver instalado na reunião, como quando o aplicativo é desabilitado pelo administrador de locatários ou bloqueado durante a mitigação de site ativo.</span><span class="sxs-lookup"><span data-stu-id="dfaca-159">This will be the most common error response and is triggered when the app is not installed in the meeting such as when the app is disabled by tenant admin or blocked during live site mitigation.</span></span>  
<span data-ttu-id="dfaca-160">**200**: informações do participante recuperadas com êxito</span><span class="sxs-lookup"><span data-stu-id="dfaca-160">**200**: participant information successfully retrieved</span></span>  
<span data-ttu-id="dfaca-161">**401**: token inválido</span><span class="sxs-lookup"><span data-stu-id="dfaca-161">**401**: invalid token</span></span>  
<span data-ttu-id="dfaca-162">**404**: a reunião não existe ou o participante não pode ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="dfaca-162">**404**: the meeting doesn't exist or participant can’t be found.</span></span>

<!-- markdownlint-disable MD024 -->
### <a name="notificationsignal-api"></a><span data-ttu-id="dfaca-163">API NotificationSignal</span><span class="sxs-lookup"><span data-stu-id="dfaca-163">NotificationSignal API</span></span>

> [!NOTE]
> <span data-ttu-id="dfaca-164">Quando uma caixa de diálogo na reunião é chamada, o mesmo conteúdo também será apresentado como uma mensagem de chat.</span><span class="sxs-lookup"><span data-stu-id="dfaca-164">When an in-meeting dialog is invoked, the same content will also be presented as a chat message.</span></span>

#### <a name="request"></a><span data-ttu-id="dfaca-165">Solicitação</span><span class="sxs-lookup"><span data-stu-id="dfaca-165">Request</span></span>

```http
POST /v3/conversations/{conversationId}/activities
```

#### <a name="query-parameters"></a><span data-ttu-id="dfaca-166">Parâmetros de consulta</span><span class="sxs-lookup"><span data-stu-id="dfaca-166">Query parameters</span></span>

<span data-ttu-id="dfaca-167">**Conversation**: o identificador de conversa.</span><span class="sxs-lookup"><span data-stu-id="dfaca-167">**conversationId**: The conversation identifier.</span></span> <span data-ttu-id="dfaca-168">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="dfaca-168">Required</span></span>

#### <a name="request-payload"></a><span data-ttu-id="dfaca-169">Carga de solicitação</span><span class="sxs-lookup"><span data-stu-id="dfaca-169">Request Payload</span></span>

# <a name="json"></a>[<span data-ttu-id="dfaca-170">JSON</span><span class="sxs-lookup"><span data-stu-id="dfaca-170">JSON</span></span>](#tab/json)

```json
{
    "type": "message",
    "text": "John Phillips assigned you a weekly todo",
    "summary": "Don't forget to meet with Marketing next week",
    "channelData": {
    "notification": {
    "alert": true,
    "externalResourceUrl": "https://teams.microsoft.com/l/bubble/APP_ID?url=&height=&width=&title=<TaskInfo.title>"
    }
},
    "replyToId": "1493070356924"
    }
```

# <a name="cnet"></a>[<span data-ttu-id="dfaca-171">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="dfaca-171">C#/.NET</span></span>](#tab/dotnet)

```csharp
Activity activity = MessageFactory.Text("This is a meeting signal test");
MeetingNotification notification = new MeetingNotification
{
    AlertInMeeting = true,
    ExternalResourceUrl = "https://teams.microsoft.com/l/bubble/APP_ID?url=&height=&width=&title=<TaskInfo.title>"
};
activity.ChannelData = new TeamsChannelData
{
    Notification = notification
};
await turnContext.SendActivityAsync(activity).ConfigureAwait(false);
```

# <a name="javascript"></a>[<span data-ttu-id="dfaca-172">JavaScript</span><span class="sxs-lookup"><span data-stu-id="dfaca-172">JavaScript</span></span>](#tab/javascript)

```javascript

const replyActivity = MessageFactory.text('Hi'); // this could be an adaptive card instead
        replyActivity.channelData = {
            notification: {
                alertInMeeting: true,
                externalResourceUrl: 'https://teams.microsoft.com/l/bubble/APP_ID?url=<TaskInfo.url>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>’
            }
        };
        await context.sendActivity(replyActivity);
```

* * *

> [!IMPORTANT]
> <span data-ttu-id="dfaca-173">A URL na bolha de conteúdo (URL taskInfo) deve estar incluída na lista de [domínios válidos](../resources/schema/manifest-schema.md#validdomains) incluída no manifesto do aplicativo Teams.</span><span class="sxs-lookup"><span data-stu-id="dfaca-173">The URL in the content bubble (taskInfo URL) must be included in the [valid domains](../resources/schema/manifest-schema.md#validdomains) list included in the Teams app manifest.</span></span>

#### <a name="response-codes"></a><span data-ttu-id="dfaca-174">Códigos de resposta</span><span class="sxs-lookup"><span data-stu-id="dfaca-174">Response Codes</span></span>

<span data-ttu-id="dfaca-175">**201**: atividade com sinal enviado com êxito</span><span class="sxs-lookup"><span data-stu-id="dfaca-175">**201**: activity with signal is successfully sent</span></span>  
<span data-ttu-id="dfaca-176">**401**: token inválido</span><span class="sxs-lookup"><span data-stu-id="dfaca-176">**401**: invalid token</span></span>  
<span data-ttu-id="dfaca-177">**403**: o aplicativo não tem permissão para enviar o sinal.</span><span class="sxs-lookup"><span data-stu-id="dfaca-177">**403**: the app is not allowed to send the signal.</span></span> <span data-ttu-id="dfaca-178">Nesse caso, a carga deve conter uma mensagem de erro mais detalhada.</span><span class="sxs-lookup"><span data-stu-id="dfaca-178">In this case, the payload should contain more detail error message.</span></span> <span data-ttu-id="dfaca-179">Podem existir vários motivos: aplicativo desabilitado pelo administrador de locatários, bloqueado durante a mitigação de sites ativos, etc.</span><span class="sxs-lookup"><span data-stu-id="dfaca-179">There can be many reasons: app disabled by tenant admin, blocked during live site mitigation, etc.</span></span>  
<span data-ttu-id="dfaca-180">**404**: o chat de reunião não existe</span><span class="sxs-lookup"><span data-stu-id="dfaca-180">**404**: meeting chat doesn't exist</span></span>  

## <a name="enable-your-app-for-teams-meetings"></a><span data-ttu-id="dfaca-181">Habilitar o aplicativo para reuniões do teams</span><span class="sxs-lookup"><span data-stu-id="dfaca-181">Enable your app for Teams meetings</span></span>

### <a name="update-your-app-manifest"></a><span data-ttu-id="dfaca-182">Atualizar o manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="dfaca-182">Update your app manifest</span></span>

<span data-ttu-id="dfaca-183">As funcionalidades de aplicativos de reuniões são declaradas em seu **configurableTabs**manifesto de aplicativo por meio de  ->  **escopos** configurableTabs e matrizes de **contexto** .</span><span class="sxs-lookup"><span data-stu-id="dfaca-183">The meetings app capabilities are declared in your app manifest via the **configurableTabs** -> **scopes** and **context** arrays.</span></span> <span data-ttu-id="dfaca-184">O *escopo* define para quem e o *contexto* define onde seu aplicativo estará disponível.</span><span class="sxs-lookup"><span data-stu-id="dfaca-184">*Scope* defines to whom and *context* defines where your app will be available.</span></span>

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

### <a name="context-property"></a><span data-ttu-id="dfaca-185">Propriedade Context</span><span class="sxs-lookup"><span data-stu-id="dfaca-185">Context property</span></span>

<span data-ttu-id="dfaca-186">A guia `context` e `scopes` as propriedades funcionam em harmonia para permitir que você determine onde você deseja que seu aplicativo apareça.</span><span class="sxs-lookup"><span data-stu-id="dfaca-186">The tab `context` and `scopes` properties work in harmony to allow you to determine where you want your app to appear.</span></span> <span data-ttu-id="dfaca-187">Enquanto as guias no `personal` escopo só podem ter um contexto, ou seja, `personalTab`  `team` ou `groupchat` abas com escopo podem ter mais de um contexto.</span><span class="sxs-lookup"><span data-stu-id="dfaca-187">While tabs in the `personal` scope can only have one context, i.e., `personalTab`,  `team` or `groupchat` scoped tabs can have more than one context.</span></span> <span data-ttu-id="dfaca-188">Os valores possíveis para a propriedade Context são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="dfaca-188">The possible values for the context property are as follows:</span></span>

* <span data-ttu-id="dfaca-189">**channelTab**: uma guia no cabeçalho de um canal de equipe.</span><span class="sxs-lookup"><span data-stu-id="dfaca-189">**channelTab**: a tab in the header of a team channel.</span></span>
* <span data-ttu-id="dfaca-190">**privateChatTab**: uma guia no cabeçalho de um grupo bate-papo entre um conjunto de usuários que não estão no contexto de uma equipe ou reunião.</span><span class="sxs-lookup"><span data-stu-id="dfaca-190">**privateChatTab**: a tab in the header of a group chat between a set of users not in the context of a team or meeting.</span></span>
* <span data-ttu-id="dfaca-191">**meetingChatTab**: uma guia no cabeçalho de um chat de grupo entre um conjunto de usuários no contexto de uma reunião agendada.</span><span class="sxs-lookup"><span data-stu-id="dfaca-191">**meetingChatTab**: a tab in the header of a group chat between a set of users in the context of a scheduled meeting.</span></span>
* <span data-ttu-id="dfaca-192">**meetingDetailsTab**: uma guia no cabeçalho do modo de exibição detalhes da reunião do calendário.</span><span class="sxs-lookup"><span data-stu-id="dfaca-192">**meetingDetailsTab**: a tab in the header of the meeting details view of the calendar.</span></span>
* <span data-ttu-id="dfaca-193">**meetingSidePanel**: um painel na reunião aberto por meio da barra unificada (u-bar).</span><span class="sxs-lookup"><span data-stu-id="dfaca-193">**meetingSidePanel**: an in-meeting panel opened via the unified bar (u-bar).</span></span>

## <a name="configure-your-app-for-meeting-scenarios"></a><span data-ttu-id="dfaca-194">Configurar seu aplicativo para cenários de reunião</span><span class="sxs-lookup"><span data-stu-id="dfaca-194">Configure your app for meeting scenarios</span></span>

> [!NOTE]
> <span data-ttu-id="dfaca-195">Para que seu aplicativo fique visível na Galeria de guias, ele precisa **suportar guias configuráveis** e o **escopo de chat de grupo**.</span><span class="sxs-lookup"><span data-stu-id="dfaca-195">For your app to be visible in the tab gallery it needs to **support configurable tabs** and the **group chat scope**.</span></span>

### <a name="pre-meeting"></a><span data-ttu-id="dfaca-196">Pré-reunião</span><span class="sxs-lookup"><span data-stu-id="dfaca-196">Pre-meeting</span></span>

<span data-ttu-id="dfaca-197">Os usuários com funções de organizador e/ou apresentador adicionam guias a uma reunião usando o botão mais ➕ nas páginas **chat** de reunião e **detalhes** da reunião.</span><span class="sxs-lookup"><span data-stu-id="dfaca-197">Users with organizer and/or presenter roles add tabs to a meeting using the plus ➕ button in the meeting **Chat** and meeting **details** pages.</span></span> <span data-ttu-id="dfaca-198">As extensões de mensagens são adicionadas ao via menu de reticências/estouro &#x25CF;&#x25CF;&#x25CF; localizada abaixo da área de mensagem de composição no chat.</span><span class="sxs-lookup"><span data-stu-id="dfaca-198">Messaging extensions are added to via the ellipses/overflow menu &#x25CF;&#x25CF;&#x25CF; located beneath the compose message area in the chat.</span></span> <span data-ttu-id="dfaca-199">Os bots são adicionados a um chat de reunião usando a **@** tecla "" e selecionando **obter bots**.</span><span class="sxs-lookup"><span data-stu-id="dfaca-199">Bots are added to a meeting chat using the "**@**" key and selecting **Get bots**.</span></span>

<span data-ttu-id="dfaca-200">✔ A identidade do usuário *deve* ser confirmada por meio de [guias de SSO](../tabs/how-to/authentication/auth-aad-sso.md).</span><span class="sxs-lookup"><span data-stu-id="dfaca-200">✔ The user identity *must* be confirmed via [Tabs SSO](../tabs/how-to/authentication/auth-aad-sso.md).</span></span> <span data-ttu-id="dfaca-201">Após essa autenticação, o aplicativo pode recuperar a função de usuário por meio da API getparticipante.</span><span class="sxs-lookup"><span data-stu-id="dfaca-201">Following this authentication, the app can retrieve the user role via the GetParticipant API.</span></span>

 <span data-ttu-id="dfaca-202">✔ Com base na função de usuário, o aplicativo agora terá a capacidade de apresentar experiências específicas de função.</span><span class="sxs-lookup"><span data-stu-id="dfaca-202">✔ Based on the user role, the app will now have the capability to present role specific experiences.</span></span> <span data-ttu-id="dfaca-203">Por exemplo, um aplicativo de sondagem pode permitir que somente os organizadores e os apresentadores criem uma nova pesquisa.</span><span class="sxs-lookup"><span data-stu-id="dfaca-203">For example, a polling app can allow only organizers and presenters to create a new poll.</span></span>

> <span data-ttu-id="dfaca-204">**Observação**: as atribuições de função podem ser alteradas enquanto uma reunião estiver em andamento.</span><span class="sxs-lookup"><span data-stu-id="dfaca-204">**NOTE**: Role assignments can be changed while a meeting is in progress.</span></span>  <span data-ttu-id="dfaca-205">*Consulte* [funções em uma reunião do teams](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span><span class="sxs-lookup"><span data-stu-id="dfaca-205">*See* [Roles in a Teams meeting](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span></span> 

### <a name="in-meeting"></a><span data-ttu-id="dfaca-206">Na reunião</span><span class="sxs-lookup"><span data-stu-id="dfaca-206">In-meeting</span></span>

#### <a name="side-panel"></a><span data-ttu-id="dfaca-207">**painel lateral**</span><span class="sxs-lookup"><span data-stu-id="dfaca-207">**side-panel**</span></span>

<span data-ttu-id="dfaca-208">✔ Em seu manifesto de aplicativo, adicione **sidePanel** à matriz **meetingSurfaces** , conforme descrito acima.</span><span class="sxs-lookup"><span data-stu-id="dfaca-208">✔ In your app manifest add **sidePanel** to the **meetingSurfaces** array as described above.</span></span>

<span data-ttu-id="dfaca-209">✔ Na reunião, bem como em todos os cenários, o aplicativo será renderizado em uma guia na reunião que tenha 320px de largura.</span><span class="sxs-lookup"><span data-stu-id="dfaca-209">✔ In the meeting as well as in all scenarios, the app will be rendered in an in-meeting tab that is 320px in width.</span></span> <span data-ttu-id="dfaca-210">Sua guia deve ser otimizada para isso.</span><span class="sxs-lookup"><span data-stu-id="dfaca-210">Your tab must be optimized for this.</span></span> <span data-ttu-id="dfaca-211">*Consulte* [FrameContext interface](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="dfaca-211">*See*, [FrameContext interface](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true)</span></span>

<span data-ttu-id="dfaca-212">✔ Consultar o [SDK do teams](../tabs/how-to/access-teams-context.md#user-context) para usar a API **userContext** para rotear as solicitações de acordo.</span><span class="sxs-lookup"><span data-stu-id="dfaca-212">✔Refer to the [Teams SDK](../tabs/how-to/access-teams-context.md#user-context) to use the **userContext** API to route requests accordingly.</span></span>

<span data-ttu-id="dfaca-213">✔ Consulte o fluxo de autenticação do Microsoft [Teams para guias](../tabs/how-to/authentication/auth-flow-tab.md).</span><span class="sxs-lookup"><span data-stu-id="dfaca-213">✔ Refer to the [Teams authentication flow for tabs](../tabs/how-to/authentication/auth-flow-tab.md).</span></span> <span data-ttu-id="dfaca-214">O fluxo de autenticação para guias é muito semelhante ao fluxo de autenticação para sites.</span><span class="sxs-lookup"><span data-stu-id="dfaca-214">Authentication flow for tabs is very similar to the auth flow for websites.</span></span> <span data-ttu-id="dfaca-215">Portanto, as guias podem usar o OAuth 2,0 diretamente.</span><span class="sxs-lookup"><span data-stu-id="dfaca-215">Thus, tabs can use OAuth 2.0 directly.</span></span> <span data-ttu-id="dfaca-216">*Confira também*a [plataforma de identidade da Microsoft e o fluxo de código de autorização do OAuth 2,0](/azure/active-directory/develop/v2-oauth2-auth-code-flow).</span><span class="sxs-lookup"><span data-stu-id="dfaca-216">*See also*, [Microsoft identity platform and OAuth 2.0 authorization code flow](/azure/active-directory/develop/v2-oauth2-auth-code-flow).</span></span>

#### <a name="in-meeting-dialog"></a><span data-ttu-id="dfaca-217">**caixa de diálogo na reunião**</span><span class="sxs-lookup"><span data-stu-id="dfaca-217">**in-meeting dialog**</span></span>

<span data-ttu-id="dfaca-218">✔ Você deve cumprir as diretrizes de [design da caixa de diálogo na reunião](designing-in-meeting-dialog.md).</span><span class="sxs-lookup"><span data-stu-id="dfaca-218">✔ You must adhere to the [in-meeting dialog design guidelines](designing-in-meeting-dialog.md).</span></span>

<span data-ttu-id="dfaca-219">✔ Consulte o fluxo de autenticação do Microsoft [Teams para guias](../tabs/how-to/authentication/auth-flow-tab.md).</span><span class="sxs-lookup"><span data-stu-id="dfaca-219">✔ Refer to the [Teams authentication flow for tabs](../tabs/how-to/authentication/auth-flow-tab.md).</span></span>

<span data-ttu-id="dfaca-220">✔ Usar a API de [notificação](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) para sinalizar que uma notificação de bolha precisa ser disparada.</span><span class="sxs-lookup"><span data-stu-id="dfaca-220">✔ Use the [notification](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) API to signal that a bubble notification needs to be triggered.</span></span>

<span data-ttu-id="dfaca-221">✔ Como parte da carga de solicitação de notificação, inclua a URL onde o conteúdo a ser expedido está hospedado.</span><span class="sxs-lookup"><span data-stu-id="dfaca-221">✔ As part of the notification request payload, include the URL where the content to be showcased is hosted.</span></span>

> [!NOTE]
> <span data-ttu-id="dfaca-222">Essas notificações são persistentes por natureza.</span><span class="sxs-lookup"><span data-stu-id="dfaca-222">These notifications are persistent in nature.</span></span> <span data-ttu-id="dfaca-223">Você deve chamar a função [**submitTask ()**](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) para descartar automaticamente após um usuário executar uma ação no modo de exibição da Web.</span><span class="sxs-lookup"><span data-stu-id="dfaca-223">You must invoke the [**submitTask()**](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) function to auto-dismiss after a user takes an action in the web-view.</span></span> <span data-ttu-id="dfaca-224">Esse é um requisito para o envio de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="dfaca-224">This is a requirement for app submission.</span></span> <span data-ttu-id="dfaca-225">*Consulte também*, [SDK do teams: módulo de tarefa](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="dfaca-225">*See also*, [Teams SDK: task module](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).</span></span>

### <a name="post-meeting"></a><span data-ttu-id="dfaca-226">Pós-reunião</span><span class="sxs-lookup"><span data-stu-id="dfaca-226">Post-meeting</span></span>

<span data-ttu-id="dfaca-227">As configurações pós-instalação e pré-reunião são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="dfaca-227">The post-meeting and pre-meeting configurations are equivalent.</span></span>

## <a name="meeting-app-sample"></a><span data-ttu-id="dfaca-228">Exemplo de aplicativo de reunião</span><span class="sxs-lookup"><span data-stu-id="dfaca-228">Meeting app sample</span></span>

 > [!div class="nextstepaction"]
> [<span data-ttu-id="dfaca-229">Aplicativo gerador de token de reunião</span><span class="sxs-lookup"><span data-stu-id="dfaca-229">Meeting token generator app</span></span>](https://github.com/OfficeDev/microsoft-teams-sample-meetings-token)
