---
title: Criar aplicativos para reuniões do Teams
author: laujan
description: criar aplicativos para reuniões do teams
ms.topic: conceptual
ms.author: lajanuar
keywords: API de função de participante do usuário de reuniões de aplicativos do teams
ms.openlocfilehash: cf42d660c9b4a82f8e28d4d4379194c1bcc681e1
ms.sourcegitcommit: 3fc7ad33e2693f07170c3cb1a0d396261fc5c619
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2020
ms.locfileid: "48796166"
---
# <a name="create-apps-for-teams-meetings-developer-preview"></a><span data-ttu-id="55cb1-104">Criar aplicativos para reuniões do Teams (Developer Preview)</span><span class="sxs-lookup"><span data-stu-id="55cb1-104">Create apps for Teams meetings (Developer Preview)</span></span>

>[!IMPORTANT]
> <span data-ttu-id="55cb1-105">Os recursos incluídos no Microsoft Teams Developer Preview são fornecidos apenas para fins de acesso antecipado, teste e comentários.</span><span class="sxs-lookup"><span data-stu-id="55cb1-105">Features included in Microsoft Teams Developer Preview are provided for early-access, testing, and feedback purposes only.</span></span> <span data-ttu-id="55cb1-106">Eles podem sofrer alterações antes de ficarem disponíveis no lançamento público e não devem ser usados em aplicativos de produção.</span><span class="sxs-lookup"><span data-stu-id="55cb1-106">They may undergo changes before becoming available in the public release and should not be used in production applications.</span></span>

## <a name="prerequisites-and-considerations"></a><span data-ttu-id="55cb1-107">Pré-requisitos e considerações</span><span class="sxs-lookup"><span data-stu-id="55cb1-107">Prerequisites and considerations</span></span>

1. <span data-ttu-id="55cb1-108">Os aplicativos nas reuniões exigem alguns conhecimentos básicos do [desenvolvimento de aplicativos do teams](../overview.md).</span><span class="sxs-lookup"><span data-stu-id="55cb1-108">Apps in meetings require some basic knowledge of [Teams app development](../overview.md).</span></span> <span data-ttu-id="55cb1-109">Um aplicativo em uma reunião pode consistir em [guias](../tabs/what-are-tabs.md), [bots](../bots/what-are-bots.md)e recursos de [extensões de mensagens](../messaging-extensions/what-are-messaging-extensions.md) e exigirá atualizações para o [manifesto do aplicativo](#update-your-app-manifest) Teams para indicar que o aplicativo está disponível para reuniões</span><span class="sxs-lookup"><span data-stu-id="55cb1-109">An app in a meeting can comprise of [tabs](../tabs/what-are-tabs.md), [bots](../bots/what-are-bots.md), and [messaging extensions](../messaging-extensions/what-are-messaging-extensions.md) features and will require updates to the Teams [app manifest](#update-your-app-manifest) to indicate that the app is available for meetings</span></span>

1. <span data-ttu-id="55cb1-110">Para que seu aplicativo funcione no ciclo de vida da reunião como uma guia, ele deve suportar guias configuráveis no [escopo Groupchat](../resources/schema/manifest-schema.md#configurabletabs).</span><span class="sxs-lookup"><span data-stu-id="55cb1-110">For your app to function in the meeting lifecycle as a tab, it must support configurable tabs in the [groupchat scope](../resources/schema/manifest-schema.md#configurabletabs).</span></span> <span data-ttu-id="55cb1-111">*Confira* [estender seu aplicativo do Microsoft Teams com uma guia personalizada](../tabs/how-to/add-tab.md). O suporte ao `groupchat` escopo habilitará o aplicativo em bate-papos [post-meeting](teams-apps-in-meetings.md#post-meeting-app-experience) de [pré](teams-apps-in-meetings.md#pre-meeting-app-experience) e reunião.</span><span class="sxs-lookup"><span data-stu-id="55cb1-111">*See* [Extend your Teams app with a custom tab](../tabs/how-to/add-tab.md). Supporting the `groupchat` scope will enable your app in [pre-meeting](teams-apps-in-meetings.md#pre-meeting-app-experience) and [post-meeting](teams-apps-in-meetings.md#post-meeting-app-experience) chats.</span></span>

1. <span data-ttu-id="55cb1-112">Os parâmetros de URL da API da reunião podem exigir `meetingId` , `userId` e a [tenantid](/onedrive/find-your-office-365-tenant-id) estão disponíveis como parte da atividade SDK e bot do cliente do teams.</span><span class="sxs-lookup"><span data-stu-id="55cb1-112">Meeting API URL parameters may require `meetingId`, `userId`, and the [tenantId](/onedrive/find-your-office-365-tenant-id) These are available as part of the Teams Client SDK and bot activity.</span></span> <span data-ttu-id="55cb1-113">Além disso, as informações confiáveis para ID de usuário e ID de locatário podem ser recuperadas usando a [autenticação de SSO de guia](../tabs/how-to/authentication/auth-aad-sso.md).</span><span class="sxs-lookup"><span data-stu-id="55cb1-113">Additionally, reliable information for user ID and tenant ID can be retrieved using [Tab SSO authentication](../tabs/how-to/authentication/auth-aad-sso.md).</span></span>

1. <span data-ttu-id="55cb1-114">Algumas APIs de reunião, como `GetParticipant` exigirão um [registro de bot e uma ID de aplicativo de bot](../bots/how-to/create-a-bot-for-teams.md#with-an-azure-subscription) para gerar tokens de autenticação.</span><span class="sxs-lookup"><span data-stu-id="55cb1-114">Some meeting APIs, such as `GetParticipant` will require a [bot registration and bot app ID](../bots/how-to/create-a-bot-for-teams.md#with-an-azure-subscription) to generate auth tokens.</span></span>

1. <span data-ttu-id="55cb1-115">Os desenvolvedores devem aderir às diretrizes gerais de [design da guia do teams](../tabs/design/tabs.md) para cenários anteriores e posteriores à reunião, bem como as [diretrizes de diálogo na](design/designing-in-meeting-dialog.md) reunião para a caixa de diálogo na reunião disparada durante uma reunião do teams.</span><span class="sxs-lookup"><span data-stu-id="55cb1-115">Developers must adhere to general [Teams tab design guidelines](../tabs/design/tabs.md) for pre- and post-meeting scenarios as well as the [in-meeting dialog guidelines](design/designing-in-meeting-dialog.md) for in-meeting dialog triggered during a Teams meeting.</span></span>

## <a name="meeting-apps-api-reference"></a><span data-ttu-id="55cb1-116">Referência da API de aplicativos de reunião</span><span class="sxs-lookup"><span data-stu-id="55cb1-116">Meeting apps API reference</span></span>

|<span data-ttu-id="55cb1-117">API</span><span class="sxs-lookup"><span data-stu-id="55cb1-117">API</span></span>|<span data-ttu-id="55cb1-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="55cb1-118">Description</span></span>|<span data-ttu-id="55cb1-119">Solicitação</span><span class="sxs-lookup"><span data-stu-id="55cb1-119">Request</span></span>|<span data-ttu-id="55cb1-120">Origem</span><span class="sxs-lookup"><span data-stu-id="55cb1-120">Source</span></span>|
|---|---|----|---|
|<span data-ttu-id="55cb1-121">**UserContext**</span><span class="sxs-lookup"><span data-stu-id="55cb1-121">**GetUserContext**</span></span>| <span data-ttu-id="55cb1-122">Obter informações contextuais para exibir conteúdo relevante em uma guia do teams.</span><span class="sxs-lookup"><span data-stu-id="55cb1-122">Get contextual information to display relevant content in a Teams tab.</span></span> |<span data-ttu-id="55cb1-123">_**microsoftTeams. GetContext (() => {/ *...* / } )**_</span><span class="sxs-lookup"><span data-stu-id="55cb1-123">_**microsoftTeams.getContext( ( ) => {  / *...* / } )**_</span></span>|<span data-ttu-id="55cb1-124">SDK de cliente do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="55cb1-124">Microsoft Teams client SDK</span></span>|
|<span data-ttu-id="55cb1-125">**Getparticipante**</span><span class="sxs-lookup"><span data-stu-id="55cb1-125">**GetParticipant**</span></span>|<span data-ttu-id="55cb1-126">Essa API permite que um bot busque informações do participante por ID de reunião e ID de participante.</span><span class="sxs-lookup"><span data-stu-id="55cb1-126">This API allows a bot to fetch a participant information by meeting id and participant id.</span></span>|<span data-ttu-id="55cb1-127">**Obter** _**/v1/Meetings/{meetingId}/participants/{participantId}? tenantid = {tenantid}**_</span><span class="sxs-lookup"><span data-stu-id="55cb1-127">**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_</span></span> |<span data-ttu-id="55cb1-128">SDK do Microsoft bot Framework</span><span class="sxs-lookup"><span data-stu-id="55cb1-128">Microsoft Bot Framework SDK</span></span>|
|<span data-ttu-id="55cb1-129">**NotificationSignal**</span><span class="sxs-lookup"><span data-stu-id="55cb1-129">**NotificationSignal**</span></span> |<span data-ttu-id="55cb1-130">Os sinais de reunião serão entregues usando a seguinte API de notificação de conversa existente (para chat do usuário-bot).</span><span class="sxs-lookup"><span data-stu-id="55cb1-130">Meeting signals will be delivered using the following existing conversation notification API (for user-bot chat).</span></span> <span data-ttu-id="55cb1-131">Essa API permite que os desenvolvedores sinalizem com base na ação do usuário final para mostrar uma bolha de diálogo na reunião.</span><span class="sxs-lookup"><span data-stu-id="55cb1-131">This API allows developers to signal based on end-user action to show-case an in-meeting dialog bubble.</span></span>|<span data-ttu-id="55cb1-132">**Postar** _**/v3/Conversations/{conversationId}/Activities**_</span><span class="sxs-lookup"><span data-stu-id="55cb1-132">**POST** _**/v3/conversations/{conversationId}/activities**_</span></span>|<span data-ttu-id="55cb1-133">SDK do Microsoft bot Framework</span><span class="sxs-lookup"><span data-stu-id="55cb1-133">Microsoft Bot Framework SDK</span></span>|

### <a name="getusercontext"></a><span data-ttu-id="55cb1-134">UserContext</span><span class="sxs-lookup"><span data-stu-id="55cb1-134">GetUserContext</span></span>

<span data-ttu-id="55cb1-135">Confira a documentação [obter o contexto da guia de suas equipes](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library) para obter orientação sobre como identificar e recuperar informações contextuais para o seu conteúdo de guia.</span><span class="sxs-lookup"><span data-stu-id="55cb1-135">Please refer to our [Get context for your Teams tab](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library) documentation for guidance on identifying and  retrieving contextual information for your tab content.</span></span> <span data-ttu-id="55cb1-136">Como parte da extensibilidade de reuniões, um novo valor foi adicionado para a carga de resposta:</span><span class="sxs-lookup"><span data-stu-id="55cb1-136">As part of meetings extensibility, a new value has been added for the response payload:</span></span>

<span data-ttu-id="55cb1-137">✔ **MeetingID** : usada por uma guia ao executar no contexto da reunião.</span><span class="sxs-lookup"><span data-stu-id="55cb1-137">✔ **meetingId** : used by a tab when running in the meeting context.</span></span>

### <a name="getparticipant-api"></a><span data-ttu-id="55cb1-138">API getparticipante</span><span class="sxs-lookup"><span data-stu-id="55cb1-138">GetParticipant API</span></span>

> [!NOTE]
>
> * <span data-ttu-id="55cb1-139">Não armazenar as funções do participante em cache, pois o organizador da reunião pode alterar uma função em um determinado momento.</span><span class="sxs-lookup"><span data-stu-id="55cb1-139">Do not cache participant roles since the meeting organizer can change a role at any point in time.</span></span>
>
> * <span data-ttu-id="55cb1-140">O Microsoft Teams atualmente não oferece suporte a grandes listas de distribuição ou tamanhos de lista de mais de 350 participantes da `GetParticipant` API.</span><span class="sxs-lookup"><span data-stu-id="55cb1-140">Teams does not currently support large distribution lists or roster sizes of more than 350 participants for the `GetParticipant` API.</span></span>
>
> * <span data-ttu-id="55cb1-141">O suporte para o SDK da estrutura de bot estará disponível em breve.</span><span class="sxs-lookup"><span data-stu-id="55cb1-141">Support for the Bot Framework SDK is coming soon.</span></span>

#### <a name="request"></a><span data-ttu-id="55cb1-142">Solicitação</span><span class="sxs-lookup"><span data-stu-id="55cb1-142">Request</span></span>

```http
GET /v3/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}
```

<span data-ttu-id="55cb1-143">*Consulte* a [referência da API do bot Framework](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="55cb1-143">*See* the [Bot Framework API reference](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true).</span></span>

<!-- markdownlint-disable MD025 -->

<span data-ttu-id="55cb1-144">**Exemplo de C#**</span><span class="sxs-lookup"><span data-stu-id="55cb1-144">**C# Example**</span></span>

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

#### <a name="query-parameters"></a><span data-ttu-id="55cb1-145">Parâmetros de consulta</span><span class="sxs-lookup"><span data-stu-id="55cb1-145">Query parameters</span></span>

|<span data-ttu-id="55cb1-146">Valor</span><span class="sxs-lookup"><span data-stu-id="55cb1-146">Value</span></span>|<span data-ttu-id="55cb1-147">Tipo</span><span class="sxs-lookup"><span data-stu-id="55cb1-147">Type</span></span>|<span data-ttu-id="55cb1-148">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="55cb1-148">Required</span></span>|<span data-ttu-id="55cb1-149">Descrição</span><span class="sxs-lookup"><span data-stu-id="55cb1-149">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="55cb1-150">**MeetingID**</span><span class="sxs-lookup"><span data-stu-id="55cb1-150">**meetingId**</span></span>| <span data-ttu-id="55cb1-151">string</span><span class="sxs-lookup"><span data-stu-id="55cb1-151">string</span></span> | <span data-ttu-id="55cb1-152">Sim</span><span class="sxs-lookup"><span data-stu-id="55cb1-152">Yes</span></span> | <span data-ttu-id="55cb1-153">O identificador de reunião está disponível por meio do bot Invoke e do Team Client SDK.</span><span class="sxs-lookup"><span data-stu-id="55cb1-153">The meeting identifier is available via Bot Invoke and Teams Client SDK.</span></span>|
|<span data-ttu-id="55cb1-154">**participante de participantes**</span><span class="sxs-lookup"><span data-stu-id="55cb1-154">**participantId**</span></span>| <span data-ttu-id="55cb1-155">string</span><span class="sxs-lookup"><span data-stu-id="55cb1-155">string</span></span> | <span data-ttu-id="55cb1-156">Sim</span><span class="sxs-lookup"><span data-stu-id="55cb1-156">Yes</span></span> | <span data-ttu-id="55cb1-157">Este campo é a ID de usuário e está disponível no SSO de guia, na invocação de bot e no SDK do Team Client.</span><span class="sxs-lookup"><span data-stu-id="55cb1-157">This field is the User ID and it is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="55cb1-158">O SSO de guia é altamente recomendado</span><span class="sxs-lookup"><span data-stu-id="55cb1-158">Tab SSO is highly recommended</span></span>|
|<span data-ttu-id="55cb1-159">**tenantId**</span><span class="sxs-lookup"><span data-stu-id="55cb1-159">**tenantId**</span></span>| <span data-ttu-id="55cb1-160">string</span><span class="sxs-lookup"><span data-stu-id="55cb1-160">string</span></span> | <span data-ttu-id="55cb1-161">Sim</span><span class="sxs-lookup"><span data-stu-id="55cb1-161">Yes</span></span> | <span data-ttu-id="55cb1-162">Isso é necessário para os usuários do locatário.</span><span class="sxs-lookup"><span data-stu-id="55cb1-162">This required for tenant users.</span></span> <span data-ttu-id="55cb1-163">Ele está disponível no SSO de guia, no bot Invoke e no SDK do teams Client.</span><span class="sxs-lookup"><span data-stu-id="55cb1-163">It is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="55cb1-164">O SSO de guia é altamente recomendado</span><span class="sxs-lookup"><span data-stu-id="55cb1-164">Tab SSO is highly recommended</span></span>|

#### <a name="response-payload"></a><span data-ttu-id="55cb1-165">Carga de resposta</span><span class="sxs-lookup"><span data-stu-id="55cb1-165">Response Payload</span></span>
<!-- markdownlint-disable MD036 -->

<span data-ttu-id="55cb1-166">**função** em "reunião" pode ser *organizador* , *apresentador* ou *participante* .</span><span class="sxs-lookup"><span data-stu-id="55cb1-166">**role** under "meeting" can be *Organizer* , *Presenter* , or *Attendee* .</span></span>

<span data-ttu-id="55cb1-167">**Exemplo 1**</span><span class="sxs-lookup"><span data-stu-id="55cb1-167">**Example 1**</span></span>

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
      "userRole": "user"
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
#### <a name="response-codes"></a><span data-ttu-id="55cb1-168">Códigos de resposta</span><span class="sxs-lookup"><span data-stu-id="55cb1-168">Response Codes</span></span>

<span data-ttu-id="55cb1-169">**403** : o aplicativo não tem permissão para obter informações do participante.</span><span class="sxs-lookup"><span data-stu-id="55cb1-169">**403** : the app is not allowed to get participant information.</span></span> <span data-ttu-id="55cb1-170">Esta será a resposta de erro mais comum e será disparada quando o aplicativo não estiver instalado na reunião, como quando o aplicativo é desabilitado pelo administrador de locatários ou bloqueado durante a mitigação de site ativo.</span><span class="sxs-lookup"><span data-stu-id="55cb1-170">This will be the most common error response and is triggered when the app is not installed in the meeting such as when the app is disabled by tenant admin or blocked during live site mitigation.</span></span>  
<span data-ttu-id="55cb1-171">**200** : informações do participante recuperadas com êxito</span><span class="sxs-lookup"><span data-stu-id="55cb1-171">**200** : participant information successfully retrieved</span></span>  
<span data-ttu-id="55cb1-172">**401** : token inválido</span><span class="sxs-lookup"><span data-stu-id="55cb1-172">**401** : invalid token</span></span>  
<span data-ttu-id="55cb1-173">**404** : a reunião não existe ou o participante não pode ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="55cb1-173">**404** : the meeting doesn't exist or participant can’t be found.</span></span>

<!-- markdownlint-disable MD024 -->
### <a name="notificationsignal-api"></a><span data-ttu-id="55cb1-174">API NotificationSignal</span><span class="sxs-lookup"><span data-stu-id="55cb1-174">NotificationSignal API</span></span>

> [!NOTE]
> <span data-ttu-id="55cb1-175">Quando uma caixa de diálogo na reunião é chamada, o mesmo conteúdo também será apresentado como uma mensagem de chat.</span><span class="sxs-lookup"><span data-stu-id="55cb1-175">When an in-meeting dialog is invoked, the same content will also be presented as a chat message.</span></span>

#### <a name="request"></a><span data-ttu-id="55cb1-176">Solicitação</span><span class="sxs-lookup"><span data-stu-id="55cb1-176">Request</span></span>

```http
POST /v3/conversations/{conversationId}/activities
```

#### <a name="query-parameters"></a><span data-ttu-id="55cb1-177">Parâmetros de consulta</span><span class="sxs-lookup"><span data-stu-id="55cb1-177">Query parameters</span></span>

|<span data-ttu-id="55cb1-178">Valor</span><span class="sxs-lookup"><span data-stu-id="55cb1-178">Value</span></span>|<span data-ttu-id="55cb1-179">Tipo</span><span class="sxs-lookup"><span data-stu-id="55cb1-179">Type</span></span>|<span data-ttu-id="55cb1-180">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="55cb1-180">Required</span></span>|<span data-ttu-id="55cb1-181">Descrição</span><span class="sxs-lookup"><span data-stu-id="55cb1-181">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="55cb1-182">**conversationId**</span><span class="sxs-lookup"><span data-stu-id="55cb1-182">**conversationId**</span></span>| <span data-ttu-id="55cb1-183">string</span><span class="sxs-lookup"><span data-stu-id="55cb1-183">string</span></span> | <span data-ttu-id="55cb1-184">Sim</span><span class="sxs-lookup"><span data-stu-id="55cb1-184">Yes</span></span> | <span data-ttu-id="55cb1-185">O identificador de conversa está disponível como parte da invocação de bot</span><span class="sxs-lookup"><span data-stu-id="55cb1-185">The conversation identifier is available as part of bot invoke</span></span> |

#### <a name="request-payload"></a><span data-ttu-id="55cb1-186">Carga de solicitação</span><span class="sxs-lookup"><span data-stu-id="55cb1-186">Request Payload</span></span>

> [!NOTE]
>
> <span data-ttu-id="55cb1-187">O completionBotId no externalResourceUrl na carga de solicitação abaixo é um parâmetro opcional.</span><span class="sxs-lookup"><span data-stu-id="55cb1-187">The completionBotId in the externalResourceUrl in the requeste payload below is an optional parameter.</span></span> <span data-ttu-id="55cb1-188">É a ID do bot que é declarada no manifesto.</span><span class="sxs-lookup"><span data-stu-id="55cb1-188">It is the Bot ID that is declared in the manifest.</span></span> <span data-ttu-id="55cb1-189">O bot receberá um objeto result.</span><span class="sxs-lookup"><span data-stu-id="55cb1-189">The bot will receive a result object.</span></span>

# <a name="json"></a>[<span data-ttu-id="55cb1-190">JSON</span><span class="sxs-lookup"><span data-stu-id="55cb1-190">JSON</span></span>](#tab/json)

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

# <a name="cnet"></a>[<span data-ttu-id="55cb1-191">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="55cb1-191">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="javascript"></a>[<span data-ttu-id="55cb1-192">JavaScript</span><span class="sxs-lookup"><span data-stu-id="55cb1-192">JavaScript</span></span>](#tab/javascript)

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
> <span data-ttu-id="55cb1-193">A URL na bolha de conteúdo (URL taskInfo) deve estar incluída na lista de [domínios válidos](../resources/schema/manifest-schema.md#validdomains) incluída no manifesto do aplicativo Teams.</span><span class="sxs-lookup"><span data-stu-id="55cb1-193">The URL in the content bubble (taskInfo URL) must be included in the [valid domains](../resources/schema/manifest-schema.md#validdomains) list included in the Teams app manifest.</span></span>

#### <a name="response-codes"></a><span data-ttu-id="55cb1-194">Códigos de resposta</span><span class="sxs-lookup"><span data-stu-id="55cb1-194">Response Codes</span></span>

<span data-ttu-id="55cb1-195">**201** : atividade com sinal enviado com êxito</span><span class="sxs-lookup"><span data-stu-id="55cb1-195">**201** : activity with signal is successfully sent</span></span>  
<span data-ttu-id="55cb1-196">**401** : token inválido</span><span class="sxs-lookup"><span data-stu-id="55cb1-196">**401** : invalid token</span></span>  
<span data-ttu-id="55cb1-197">**403** : o aplicativo não tem permissão para enviar o sinal.</span><span class="sxs-lookup"><span data-stu-id="55cb1-197">**403** : the app is not allowed to send the signal.</span></span> <span data-ttu-id="55cb1-198">Nesse caso, a carga deve conter uma mensagem de erro mais detalhada.</span><span class="sxs-lookup"><span data-stu-id="55cb1-198">In this case, the payload should contain more detail error message.</span></span> <span data-ttu-id="55cb1-199">Podem existir vários motivos: aplicativo desabilitado pelo administrador de locatários, bloqueado durante a mitigação de sites ativos, etc.</span><span class="sxs-lookup"><span data-stu-id="55cb1-199">There can be many reasons: app disabled by tenant admin, blocked during live site mitigation, etc.</span></span>  
<span data-ttu-id="55cb1-200">**404** : o chat de reunião não existe</span><span class="sxs-lookup"><span data-stu-id="55cb1-200">**404** : meeting chat doesn't exist</span></span>  

## <a name="enable-your-app-for-teams-meetings"></a><span data-ttu-id="55cb1-201">Habilitar o aplicativo para reuniões do teams</span><span class="sxs-lookup"><span data-stu-id="55cb1-201">Enable your app for Teams meetings</span></span>

### <a name="update-your-app-manifest"></a><span data-ttu-id="55cb1-202">Atualizar o manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="55cb1-202">Update your app manifest</span></span>

<span data-ttu-id="55cb1-203">As funcionalidades de aplicativos de reuniões são declaradas em seu **configurableTabs** manifesto de aplicativo por meio de  ->  **escopos** configurableTabs e matrizes de **contexto** .</span><span class="sxs-lookup"><span data-stu-id="55cb1-203">The meetings app capabilities are declared in your app manifest via the **configurableTabs** -> **scopes** and **context** arrays.</span></span> <span data-ttu-id="55cb1-204">O *escopo* define para quem e o *contexto* define onde seu aplicativo estará disponível.</span><span class="sxs-lookup"><span data-stu-id="55cb1-204">*Scope* defines to whom and *context* defines where your app will be available.</span></span>

> [!NOTE]
> * <span data-ttu-id="55cb1-205">Use o [esquema de manifesto da visualização do desenvolvedor](../resources/schema/manifest-schema-dev-preview.md) para experimentá-lo em seu manifesto de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="55cb1-205">Please use [Developer Preview manifest schema](../resources/schema/manifest-schema-dev-preview.md) to try this in your app manifest.</span></span>

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

### <a name="context-property"></a><span data-ttu-id="55cb1-206">Propriedade Context</span><span class="sxs-lookup"><span data-stu-id="55cb1-206">Context property</span></span>

<span data-ttu-id="55cb1-207">A guia `context` e `scopes` as propriedades funcionam em harmonia para permitir que você determine onde você deseja que seu aplicativo apareça.</span><span class="sxs-lookup"><span data-stu-id="55cb1-207">The tab `context` and `scopes` properties work in harmony to allow you to determine where you want your app to appear.</span></span> <span data-ttu-id="55cb1-208">As guias no `team` `groupchat` escopo ou podem ter mais de um contexto.</span><span class="sxs-lookup"><span data-stu-id="55cb1-208">Tabs in the `team` or `groupchat` scope can have more than one context.</span></span> <span data-ttu-id="55cb1-209">Os valores possíveis para a propriedade Context são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="55cb1-209">The possible values for the context property are as follows:</span></span>

* <span data-ttu-id="55cb1-210">**channelTab** : uma guia no cabeçalho de um canal de equipe.</span><span class="sxs-lookup"><span data-stu-id="55cb1-210">**channelTab** : a tab in the header of a team channel.</span></span>
* <span data-ttu-id="55cb1-211">**privateChatTab** : uma guia no cabeçalho de um grupo bate-papo entre um conjunto de usuários que não estão no contexto de uma equipe ou reunião.</span><span class="sxs-lookup"><span data-stu-id="55cb1-211">**privateChatTab** : a tab in the header of a group chat between a set of users not in the context of a team or meeting.</span></span>
* <span data-ttu-id="55cb1-212">**meetingChatTab** : uma guia no cabeçalho de um chat de grupo entre um conjunto de usuários no contexto de uma reunião agendada.</span><span class="sxs-lookup"><span data-stu-id="55cb1-212">**meetingChatTab** : a tab in the header of a group chat between a set of users in the context of a scheduled meeting.</span></span>
* <span data-ttu-id="55cb1-213">**meetingDetailsTab** : uma guia no cabeçalho do modo de exibição detalhes da reunião do calendário.</span><span class="sxs-lookup"><span data-stu-id="55cb1-213">**meetingDetailsTab** : a tab in the header of the meeting details view of the calendar.</span></span>
* <span data-ttu-id="55cb1-214">**meetingSidePanel** : um painel na reunião aberto por meio da barra unificada (u-bar).</span><span class="sxs-lookup"><span data-stu-id="55cb1-214">**meetingSidePanel** : an in-meeting panel opened via the unified bar (u-bar).</span></span>

> [!NOTE]
> <span data-ttu-id="55cb1-215">A propriedade "Context" atualmente não é suportada e, portanto, será ignorada em clientes móveis</span><span class="sxs-lookup"><span data-stu-id="55cb1-215">"Context" property is currently not supported and thus will be ignored on mobile clients</span></span>

## <a name="configure-your-app-for-meeting-scenarios"></a><span data-ttu-id="55cb1-216">Configurar seu aplicativo para cenários de reunião</span><span class="sxs-lookup"><span data-stu-id="55cb1-216">Configure your app for meeting scenarios</span></span>

> [!NOTE]
> * <span data-ttu-id="55cb1-217">Para que seu aplicativo fique visível na Galeria de guias, ele precisa **suportar guias configuráveis** e o **escopo de chat de grupo** .</span><span class="sxs-lookup"><span data-stu-id="55cb1-217">For your app to be visible in the tab gallery it needs to **support configurable tabs** and the **group chat scope** .</span></span>
>
> * <span data-ttu-id="55cb1-218">Os clientes móveis dão suporte a guias apenas nas superfícies de reunião prévia e posterior.</span><span class="sxs-lookup"><span data-stu-id="55cb1-218">Mobile clients support Tabs only in Pre and Post Meeting Surfaces.</span></span> <span data-ttu-id="55cb1-219">As experiências de reunião (painel e caixa de diálogo na reunião) no Mobile estarão disponíveis em breve.</span><span class="sxs-lookup"><span data-stu-id="55cb1-219">The In-meeting experiences (in-meeting dialog and panel) on mobile will be available soon.</span></span> <span data-ttu-id="55cb1-220">Siga as [orientações para guias em celular](../tabs/design/tabs-mobile.md) ao criar suas guias para dispositivos móveis.</span><span class="sxs-lookup"><span data-stu-id="55cb1-220">Follow the [guidance for tabs on mobile](../tabs/design/tabs-mobile.md) when creating your tabs for mobile.</span></span> 

### <a name="pre-meeting"></a><span data-ttu-id="55cb1-221">Pré-reunião</span><span class="sxs-lookup"><span data-stu-id="55cb1-221">Pre-meeting</span></span>

<span data-ttu-id="55cb1-222">Os usuários com funções de organizador e/ou apresentador adicionam guias a uma reunião usando o botão mais ➕ nas páginas **chat** de reunião e **detalhes** da reunião.</span><span class="sxs-lookup"><span data-stu-id="55cb1-222">Users with organizer and/or presenter roles add tabs to a meeting using the plus ➕ button in the meeting **Chat** and meeting **details** pages.</span></span> <span data-ttu-id="55cb1-223">As extensões de mensagens são adicionadas ao via menu de reticências/estouro &#x25CF;&#x25CF;&#x25CF; localizada abaixo da área de mensagem de composição no chat.</span><span class="sxs-lookup"><span data-stu-id="55cb1-223">Messaging extensions are added to via the ellipses/overflow menu &#x25CF;&#x25CF;&#x25CF; located beneath the compose message area in the chat.</span></span> <span data-ttu-id="55cb1-224">Os bots são adicionados a um chat de reunião usando a **@** tecla "" e selecionando **obter bots** .</span><span class="sxs-lookup"><span data-stu-id="55cb1-224">Bots are added to a meeting chat using the " **@** " key and selecting **Get bots** .</span></span>

<span data-ttu-id="55cb1-225">✔ A identidade do usuário *deve* ser confirmada por meio de [guias de SSO](../tabs/how-to/authentication/auth-aad-sso.md).</span><span class="sxs-lookup"><span data-stu-id="55cb1-225">✔ The user identity *must* be confirmed via [Tabs SSO](../tabs/how-to/authentication/auth-aad-sso.md).</span></span> <span data-ttu-id="55cb1-226">Após essa autenticação, o aplicativo pode recuperar a função de usuário por meio da API getparticipante.</span><span class="sxs-lookup"><span data-stu-id="55cb1-226">Following this authentication, the app can retrieve the user role via the GetParticipant API.</span></span>

 <span data-ttu-id="55cb1-227">✔ Com base na função de usuário, o aplicativo agora terá a capacidade de apresentar experiências específicas de função.</span><span class="sxs-lookup"><span data-stu-id="55cb1-227">✔ Based on the user role, the app will now have the capability to present role specific experiences.</span></span> <span data-ttu-id="55cb1-228">Por exemplo, um aplicativo de sondagem pode permitir que somente os organizadores e os apresentadores criem uma nova pesquisa.</span><span class="sxs-lookup"><span data-stu-id="55cb1-228">For example, a polling app can allow only organizers and presenters to create a new poll.</span></span>

> <span data-ttu-id="55cb1-229">**Observação** : as atribuições de função podem ser alteradas enquanto uma reunião estiver em andamento.</span><span class="sxs-lookup"><span data-stu-id="55cb1-229">**NOTE** : Role assignments can be changed while a meeting is in progress.</span></span>  <span data-ttu-id="55cb1-230">*Consulte* [funções em uma reunião do teams](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span><span class="sxs-lookup"><span data-stu-id="55cb1-230">*See* [Roles in a Teams meeting](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span></span> 

### <a name="in-meeting"></a><span data-ttu-id="55cb1-231">Na reunião</span><span class="sxs-lookup"><span data-stu-id="55cb1-231">In-meeting</span></span>

#### <a name="sidepanel"></a><span data-ttu-id="55cb1-232">**sidePanel**</span><span class="sxs-lookup"><span data-stu-id="55cb1-232">**sidePanel**</span></span>

<span data-ttu-id="55cb1-233">✔ Em seu manifesto de aplicativo, adicione **sidePanel** à matriz de **contexto** , conforme descrito acima.</span><span class="sxs-lookup"><span data-stu-id="55cb1-233">✔ In your app manifest add **sidePanel** to the **context** array as described above.</span></span>

<span data-ttu-id="55cb1-234">✔ Na reunião, bem como em todos os cenários, o aplicativo será renderizado em uma guia na reunião que tenha 320px de largura.</span><span class="sxs-lookup"><span data-stu-id="55cb1-234">✔ In the meeting as well as in all scenarios, the app will be rendered in an in-meeting tab that is 320px in width.</span></span> <span data-ttu-id="55cb1-235">Sua guia deve ser otimizada para isso.</span><span class="sxs-lookup"><span data-stu-id="55cb1-235">Your tab must be optimized for this.</span></span> <span data-ttu-id="55cb1-236">*Consulte* [FrameContext interface](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="55cb1-236">*See* , [FrameContext interface](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true)</span></span>

<span data-ttu-id="55cb1-237">✔ Consultar o [SDK do teams](../tabs/how-to/access-teams-context.md#user-context) para usar a API **userContext** para rotear as solicitações de acordo.</span><span class="sxs-lookup"><span data-stu-id="55cb1-237">✔Refer to the [Teams SDK](../tabs/how-to/access-teams-context.md#user-context) to use the **userContext** API to route requests accordingly.</span></span>

<span data-ttu-id="55cb1-238">✔ Consulte o fluxo de autenticação do Microsoft [Teams para guias](../tabs/how-to/authentication/auth-flow-tab.md).</span><span class="sxs-lookup"><span data-stu-id="55cb1-238">✔ Refer to the [Teams authentication flow for tabs](../tabs/how-to/authentication/auth-flow-tab.md).</span></span> <span data-ttu-id="55cb1-239">O fluxo de autenticação para guias é muito semelhante ao fluxo de autenticação para sites.</span><span class="sxs-lookup"><span data-stu-id="55cb1-239">Authentication flow for tabs is very similar to the auth flow for websites.</span></span> <span data-ttu-id="55cb1-240">Portanto, as guias podem usar o OAuth 2,0 diretamente.</span><span class="sxs-lookup"><span data-stu-id="55cb1-240">Thus, tabs can use OAuth 2.0 directly.</span></span> <span data-ttu-id="55cb1-241">*Confira também* a [plataforma de identidade da Microsoft e o fluxo de código de autorização do OAuth 2,0](/azure/active-directory/develop/v2-oauth2-auth-code-flow).</span><span class="sxs-lookup"><span data-stu-id="55cb1-241">*See also* , [Microsoft identity platform and OAuth 2.0 authorization code flow](/azure/active-directory/develop/v2-oauth2-auth-code-flow).</span></span>

#### <a name="in-meeting-dialog"></a><span data-ttu-id="55cb1-242">**caixa de diálogo na reunião**</span><span class="sxs-lookup"><span data-stu-id="55cb1-242">**in-meeting dialog**</span></span>

<span data-ttu-id="55cb1-243">✔ Você deve cumprir as diretrizes de [design da caixa de diálogo na reunião](design/designing-in-meeting-dialog.md).</span><span class="sxs-lookup"><span data-stu-id="55cb1-243">✔ You must adhere to the [in-meeting dialog design guidelines](design/designing-in-meeting-dialog.md).</span></span>

<span data-ttu-id="55cb1-244">✔ Consulte o fluxo de autenticação do Microsoft [Teams para guias](../tabs/how-to/authentication/auth-flow-tab.md).</span><span class="sxs-lookup"><span data-stu-id="55cb1-244">✔ Refer to the [Teams authentication flow for tabs](../tabs/how-to/authentication/auth-flow-tab.md).</span></span>

<span data-ttu-id="55cb1-245">✔ Usar a API de [notificação](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) para sinalizar que uma notificação de bolha precisa ser disparada.</span><span class="sxs-lookup"><span data-stu-id="55cb1-245">✔ Use the [notification](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) API to signal that a bubble notification needs to be triggered.</span></span>

<span data-ttu-id="55cb1-246">✔ Como parte da carga de solicitação de notificação, inclua a URL onde o conteúdo a ser expedido está hospedado.</span><span class="sxs-lookup"><span data-stu-id="55cb1-246">✔ As part of the notification request payload, include the URL where the content to be showcased is hosted.</span></span>

> [!NOTE]
>
> * <span data-ttu-id="55cb1-247">Essas notificações são persistentes por natureza.</span><span class="sxs-lookup"><span data-stu-id="55cb1-247">These notifications are persistent in nature.</span></span> <span data-ttu-id="55cb1-248">Você deve chamar a função [**submitTask ()**](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) para descartar automaticamente após um usuário executar uma ação no modo de exibição da Web.</span><span class="sxs-lookup"><span data-stu-id="55cb1-248">You must invoke the [**submitTask()**](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) function to auto-dismiss after a user takes an action in the web-view.</span></span> <span data-ttu-id="55cb1-249">Esse é um requisito para o envio de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="55cb1-249">This is a requirement for app submission.</span></span> <span data-ttu-id="55cb1-250">*Consulte também* , [SDK do teams: módulo de tarefa](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="55cb1-250">*See also* , [Teams SDK: task module](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).</span></span>
>
> * <span data-ttu-id="55cb1-251">Se quiser que seu aplicativo dê suporte a usuários anônimos, a carga de solicitação de chamada inicial deve confiar no `from.id`  (ID do usuário) solicitar metadados no `from` objeto, e não no `from.aadObjectId` (Azure Active Directory ID do usuário) solicitar metadados.</span><span class="sxs-lookup"><span data-stu-id="55cb1-251">If you want your app to support anonymous users, your initial invoke request payload must rely on the `from.id`  (ID of the user) request metadata in the `from` object, not the `from.aadObjectId` (Azure Active Directory ID of the user) request metadata.</span></span> <span data-ttu-id="55cb1-252">*Consulte* [usando módulos de tarefas em guias](../task-modules-and-cards/task-modules/task-modules-tabs.md) e [criar e enviar o módulo de tarefa](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).</span><span class="sxs-lookup"><span data-stu-id="55cb1-252">*See* [Using task modules in tabs](../task-modules-and-cards/task-modules/task-modules-tabs.md) and [Create and send the task module](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).</span></span>

### <a name="post-meeting"></a><span data-ttu-id="55cb1-253">Pós-reunião</span><span class="sxs-lookup"><span data-stu-id="55cb1-253">Post-meeting</span></span>

<span data-ttu-id="55cb1-254">As configurações pós-instalação e pré-reunião são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="55cb1-254">The post-meeting and pre-meeting configurations are equivalent.</span></span>

## <a name="meeting-app-sample"></a><span data-ttu-id="55cb1-255">Exemplo de aplicativo de reunião</span><span class="sxs-lookup"><span data-stu-id="55cb1-255">Meeting app sample</span></span>

 > [!div class="nextstepaction"]
> [<span data-ttu-id="55cb1-256">Aplicativo gerador de token de reunião</span><span class="sxs-lookup"><span data-stu-id="55cb1-256">Meeting token generator app</span></span>](https://github.com/OfficeDev/microsoft-teams-sample-meetings-token)
