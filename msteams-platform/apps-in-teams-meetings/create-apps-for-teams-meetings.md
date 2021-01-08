---
title: Criar aplicativos para reuniões do Teams
author: laujan
description: criar aplicativos para reuniões do teams
ms.topic: conceptual
ms.author: lajanuar
keywords: API de função de participante do usuário de reuniões de aplicativos do teams
ms.openlocfilehash: e768c2dc6722d006c89927adfe60e03243a076d0
ms.sourcegitcommit: f0dfae429385ef02f61896ad49172c4803ef6622
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/31/2020
ms.locfileid: "49740868"
---
# <a name="create-apps-for-teams-meetings"></a><span data-ttu-id="ec40b-104">Crie aplicativos para reuniões do Teams</span><span class="sxs-lookup"><span data-stu-id="ec40b-104">Create apps for Teams meetings</span></span>

## <a name="prerequisites-and-considerations"></a><span data-ttu-id="ec40b-105">Pré-requisitos e considerações</span><span class="sxs-lookup"><span data-stu-id="ec40b-105">Prerequisites and considerations</span></span>

1. <span data-ttu-id="ec40b-106">Os aplicativos nas reuniões exigem alguns conhecimentos básicos do [desenvolvimento de aplicativos do teams](../overview.md).</span><span class="sxs-lookup"><span data-stu-id="ec40b-106">Apps in meetings require some basic knowledge of [Teams app development](../overview.md).</span></span> <span data-ttu-id="ec40b-107">Um aplicativo em uma reunião pode consistir em [guias](../tabs/what-are-tabs.md), [bots](../bots/what-are-bots.md)e recursos de [extensões de mensagens](../messaging-extensions/what-are-messaging-extensions.md) e exigirá atualizações para o [manifesto do aplicativo](#update-your-app-manifest) Teams para indicar que o aplicativo está disponível para reuniões</span><span class="sxs-lookup"><span data-stu-id="ec40b-107">An app in a meeting can comprise of [tabs](../tabs/what-are-tabs.md), [bots](../bots/what-are-bots.md), and [messaging extensions](../messaging-extensions/what-are-messaging-extensions.md) features and will require updates to the Teams [app manifest](#update-your-app-manifest) to indicate that the app is available for meetings</span></span>

1. <span data-ttu-id="ec40b-108">Para que seu aplicativo funcione no ciclo de vida da reunião como uma guia, ele deve suportar guias configuráveis no [escopo Groupchat](../resources/schema/manifest-schema.md#configurabletabs).</span><span class="sxs-lookup"><span data-stu-id="ec40b-108">For your app to function in the meeting lifecycle as a tab, it must support configurable tabs in the [groupchat scope](../resources/schema/manifest-schema.md#configurabletabs).</span></span> <span data-ttu-id="ec40b-109">*Confira* [estender seu aplicativo do Microsoft Teams com uma guia personalizada](../tabs/how-to/add-tab.md). O suporte ao `groupchat` escopo habilitará o aplicativo em bate-papos [](teams-apps-in-meetings.md#post-meeting-app-experience) de [pré](teams-apps-in-meetings.md#pre-meeting-app-experience) e reunião.</span><span class="sxs-lookup"><span data-stu-id="ec40b-109">*See* [Extend your Teams app with a custom tab](../tabs/how-to/add-tab.md). Supporting the `groupchat` scope will enable your app in [pre-meeting](teams-apps-in-meetings.md#pre-meeting-app-experience) and [post-meeting](teams-apps-in-meetings.md#post-meeting-app-experience) chats.</span></span>

1. <span data-ttu-id="ec40b-110">Os parâmetros de URL da API da reunião podem exigir `meetingId` , `userId` e a [tenantid](/onedrive/find-your-office-365-tenant-id) estão disponíveis como parte da atividade SDK e bot do cliente do teams.</span><span class="sxs-lookup"><span data-stu-id="ec40b-110">Meeting API URL parameters may require `meetingId`, `userId`, and the [tenantId](/onedrive/find-your-office-365-tenant-id) These are available as part of the Teams Client SDK and bot activity.</span></span> <span data-ttu-id="ec40b-111">Além disso, as informações confiáveis para ID de usuário e ID de locatário podem ser recuperadas usando a [autenticação de SSO de guia](../tabs/how-to/authentication/auth-aad-sso.md).</span><span class="sxs-lookup"><span data-stu-id="ec40b-111">Additionally, reliable information for user ID and tenant ID can be retrieved using [Tab SSO authentication](../tabs/how-to/authentication/auth-aad-sso.md).</span></span>

1. <span data-ttu-id="ec40b-112">Algumas APIs de reunião, como `GetParticipant` exigirão um [registro de bot e uma ID de aplicativo de bot](../bots/how-to/create-a-bot-for-teams.md#with-an-azure-subscription) para gerar tokens de autenticação.</span><span class="sxs-lookup"><span data-stu-id="ec40b-112">Some meeting APIs, such as `GetParticipant` will require a [bot registration and bot app ID](../bots/how-to/create-a-bot-for-teams.md#with-an-azure-subscription) to generate auth tokens.</span></span>

1. <span data-ttu-id="ec40b-113">Como desenvolvedor, você deve cumprir as diretrizes gerais de [design da guia do teams](../tabs/design/tabs.md) para cenários anteriores e posteriores à reunião, bem como as [diretrizes da caixa](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog) de diálogo na reunião para a caixa de diálogo na reunião disparada durante uma reunião do teams.</span><span class="sxs-lookup"><span data-stu-id="ec40b-113">As a developer, you must adhere to general [Teams tab design guidelines](../tabs/design/tabs.md) for pre- and post-meeting scenarios as well as the [in-meeting dialog guidelines](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog) for in-meeting dialog triggered during a Teams meeting.</span></span>

1. <span data-ttu-id="ec40b-114">Observe que, para que seu aplicativo seja atualizado em tempo real, ele deve estar atualizado com base nas atividades de evento da reunião.</span><span class="sxs-lookup"><span data-stu-id="ec40b-114">Please note that in order for your app to be updated in real-time, it must be up-to-date based on event activities in the meeting.</span></span> <span data-ttu-id="ec40b-115">Esses eventos podem estar dentro da caixa de diálogo de reunião (consulte o `bot Id` parâmetro de conclusão `Notification Signal API` ) e outras superfícies no ciclo de vida da reunião</span><span class="sxs-lookup"><span data-stu-id="ec40b-115">These events can be within the in-meeting dialog (refer to completion `bot Id` parameter in `Notification Signal API`) and other surfaces across the meeting lifecycle</span></span>

## <a name="meeting-apps-api-reference"></a><span data-ttu-id="ec40b-116">Referência da API de aplicativos de reunião</span><span class="sxs-lookup"><span data-stu-id="ec40b-116">Meeting apps API reference</span></span>

|<span data-ttu-id="ec40b-117">API</span><span class="sxs-lookup"><span data-stu-id="ec40b-117">API</span></span>|<span data-ttu-id="ec40b-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec40b-118">Description</span></span>|<span data-ttu-id="ec40b-119">Solicitação</span><span class="sxs-lookup"><span data-stu-id="ec40b-119">Request</span></span>|<span data-ttu-id="ec40b-120">Origem</span><span class="sxs-lookup"><span data-stu-id="ec40b-120">Source</span></span>|
|---|---|----|---|
|<span data-ttu-id="ec40b-121">**UserContext**</span><span class="sxs-lookup"><span data-stu-id="ec40b-121">**GetUserContext**</span></span>| <span data-ttu-id="ec40b-122">Obter informações contextuais para exibir conteúdo relevante em uma guia do teams.</span><span class="sxs-lookup"><span data-stu-id="ec40b-122">Get contextual information to display relevant content in a Teams tab.</span></span> |<span data-ttu-id="ec40b-123">_**microsoftTeams. GetContext (() => {/*...\* / } )*\*_</span><span class="sxs-lookup"><span data-stu-id="ec40b-123">_**microsoftTeams.getContext( ( ) => {  /*...*/ } )**_</span></span>|<span data-ttu-id="ec40b-124">SDK de cliente do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="ec40b-124">Microsoft Teams client SDK</span></span>|
|<span data-ttu-id="ec40b-125">**Getparticipante**</span><span class="sxs-lookup"><span data-stu-id="ec40b-125">**GetParticipant**</span></span>|<span data-ttu-id="ec40b-126">Essa API permite que um bot busque informações do participante por ID de reunião e ID de participante.</span><span class="sxs-lookup"><span data-stu-id="ec40b-126">This API allows a bot to fetch a participant information by meeting id and participant id.</span></span>|<span data-ttu-id="ec40b-127">**Obter** _**/v1/Meetings/{meetingId}/participants/{participantId}? tenantid = {tenantid}**_</span><span class="sxs-lookup"><span data-stu-id="ec40b-127">**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_</span></span> |<span data-ttu-id="ec40b-128">SDK do Microsoft bot Framework</span><span class="sxs-lookup"><span data-stu-id="ec40b-128">Microsoft Bot Framework SDK</span></span>|
|<span data-ttu-id="ec40b-129">**NotificationSignal**</span><span class="sxs-lookup"><span data-stu-id="ec40b-129">**NotificationSignal**</span></span> |<span data-ttu-id="ec40b-130">Os sinais de reunião serão entregues usando a seguinte API de notificação de conversa existente (para chat do usuário-bot).</span><span class="sxs-lookup"><span data-stu-id="ec40b-130">Meeting signals will be delivered using the following existing conversation notification API (for user-bot chat).</span></span> <span data-ttu-id="ec40b-131">Essa API permite que os desenvolvedores sinalizem com base na ação do usuário final para mostrar uma bolha de diálogo na reunião.</span><span class="sxs-lookup"><span data-stu-id="ec40b-131">This API allows developers to signal based on end-user action to show-case an in-meeting dialog bubble.</span></span>|<span data-ttu-id="ec40b-132">**Postar** _**/v3/Conversations/{conversationId}/Activities**_</span><span class="sxs-lookup"><span data-stu-id="ec40b-132">**POST** _**/v3/conversations/{conversationId}/activities**_</span></span>|<span data-ttu-id="ec40b-133">SDK do Microsoft bot Framework</span><span class="sxs-lookup"><span data-stu-id="ec40b-133">Microsoft Bot Framework SDK</span></span>|

### <a name="getusercontext"></a><span data-ttu-id="ec40b-134">UserContext</span><span class="sxs-lookup"><span data-stu-id="ec40b-134">GetUserContext</span></span>

<span data-ttu-id="ec40b-135">Confira a documentação [obter o contexto da guia de suas equipes](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library) para obter orientação sobre como identificar e recuperar informações contextuais para o seu conteúdo de guia.</span><span class="sxs-lookup"><span data-stu-id="ec40b-135">Please refer to our [Get context for your Teams tab](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library) documentation for guidance on identifying and  retrieving contextual information for your tab content.</span></span> <span data-ttu-id="ec40b-136">Como parte da extensibilidade de reuniões, um novo valor foi adicionado para a carga de resposta:</span><span class="sxs-lookup"><span data-stu-id="ec40b-136">As part of meetings extensibility, a new value has been added for the response payload:</span></span>

<span data-ttu-id="ec40b-137">✔ **MeetingID**: usada por uma guia ao executar no contexto da reunião.</span><span class="sxs-lookup"><span data-stu-id="ec40b-137">✔ **meetingId**: used by a tab when running in the meeting context.</span></span>

### <a name="getparticipant-api"></a><span data-ttu-id="ec40b-138">API getparticipante</span><span class="sxs-lookup"><span data-stu-id="ec40b-138">GetParticipant API</span></span>

> [!NOTE]
>
> * <span data-ttu-id="ec40b-139">Não armazenar as funções do participante em cache, pois o organizador da reunião pode alterar uma função em um determinado momento.</span><span class="sxs-lookup"><span data-stu-id="ec40b-139">Do not cache participant roles since the meeting organizer can change a role at any point in time.</span></span>
>
> * <span data-ttu-id="ec40b-140">O Microsoft Teams atualmente não oferece suporte a grandes listas de distribuição ou tamanhos de lista de mais de 350 participantes da `GetParticipant` API.</span><span class="sxs-lookup"><span data-stu-id="ec40b-140">Teams does not currently support large distribution lists or roster sizes of more than 350 participants for the `GetParticipant` API.</span></span>

#### <a name="query-parameters"></a><span data-ttu-id="ec40b-141">Parâmetros de consulta</span><span class="sxs-lookup"><span data-stu-id="ec40b-141">Query parameters</span></span>

|<span data-ttu-id="ec40b-142">Valor</span><span class="sxs-lookup"><span data-stu-id="ec40b-142">Value</span></span>|<span data-ttu-id="ec40b-143">Tipo</span><span class="sxs-lookup"><span data-stu-id="ec40b-143">Type</span></span>|<span data-ttu-id="ec40b-144">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="ec40b-144">Required</span></span>|<span data-ttu-id="ec40b-145">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec40b-145">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="ec40b-146">**MeetingID**</span><span class="sxs-lookup"><span data-stu-id="ec40b-146">**meetingId**</span></span>| <span data-ttu-id="ec40b-147">string</span><span class="sxs-lookup"><span data-stu-id="ec40b-147">string</span></span> | <span data-ttu-id="ec40b-148">Sim</span><span class="sxs-lookup"><span data-stu-id="ec40b-148">Yes</span></span> | <span data-ttu-id="ec40b-149">O identificador de reunião está disponível por meio do bot Invoke e do teams Client SDK.</span><span class="sxs-lookup"><span data-stu-id="ec40b-149">The meeting identifier is available through Bot Invoke and Teams Client SDK.</span></span>|
|<span data-ttu-id="ec40b-150">**participante de participantes**</span><span class="sxs-lookup"><span data-stu-id="ec40b-150">**participantId**</span></span>| <span data-ttu-id="ec40b-151">string</span><span class="sxs-lookup"><span data-stu-id="ec40b-151">string</span></span> | <span data-ttu-id="ec40b-152">Sim</span><span class="sxs-lookup"><span data-stu-id="ec40b-152">Yes</span></span> | <span data-ttu-id="ec40b-153">O participanteid é a ID de usuário.</span><span class="sxs-lookup"><span data-stu-id="ec40b-153">The participantId is the user ID.</span></span> <span data-ttu-id="ec40b-154">Ele está disponível no SSO de guia, no bot Invoke e no SDK do teams Client.</span><span class="sxs-lookup"><span data-stu-id="ec40b-154">It is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="ec40b-155">É altamente recomendável obter um participanteid do SSO de tabulação.</span><span class="sxs-lookup"><span data-stu-id="ec40b-155">It is highly recommended to get a participantId from the Tab SSO.</span></span> |
|<span data-ttu-id="ec40b-156">**tenantId**</span><span class="sxs-lookup"><span data-stu-id="ec40b-156">**tenantId**</span></span>| <span data-ttu-id="ec40b-157">string</span><span class="sxs-lookup"><span data-stu-id="ec40b-157">string</span></span> | <span data-ttu-id="ec40b-158">Sim</span><span class="sxs-lookup"><span data-stu-id="ec40b-158">Yes</span></span> | <span data-ttu-id="ec40b-159">O tenantid é necessário para os usuários do locatário.</span><span class="sxs-lookup"><span data-stu-id="ec40b-159">The tenantId is required for the tenant users.</span></span> <span data-ttu-id="ec40b-160">Ele está disponível no SSO de guia, no bot Invoke e no SDK do teams Client.</span><span class="sxs-lookup"><span data-stu-id="ec40b-160">It is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="ec40b-161">É altamente recomendável obter um tenantid do SSO de tabulação.</span><span class="sxs-lookup"><span data-stu-id="ec40b-161">It is highly recommended to get a tenantId from the Tab SSO.</span></span> |

#### <a name="example"></a><span data-ttu-id="ec40b-162">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ec40b-162">Example</span></span>

# <a name="cnet"></a>[<span data-ttu-id="ec40b-163">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="ec40b-163">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="javascript"></a>[<span data-ttu-id="ec40b-164">JavaScript</span><span class="sxs-lookup"><span data-stu-id="ec40b-164">JavaScript</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="ec40b-165">JSON</span><span class="sxs-lookup"><span data-stu-id="ec40b-165">JSON</span></span>](#tab/json)

```http
GET /v3/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}
```

<span data-ttu-id="ec40b-166">O corpo da resposta é:</span><span class="sxs-lookup"><span data-stu-id="ec40b-166">The response body is:</span></span>

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

#### <a name="response-codes"></a><span data-ttu-id="ec40b-167">Códigos de resposta</span><span class="sxs-lookup"><span data-stu-id="ec40b-167">Response codes</span></span>

* <span data-ttu-id="ec40b-168">**403**: o aplicativo não tem permissão para obter informações do participante.</span><span class="sxs-lookup"><span data-stu-id="ec40b-168">**403**: The app is not allowed to get participant information.</span></span>  <span data-ttu-id="ec40b-169">Esta é a resposta de erro mais comum e é disparada se o aplicativo não estiver instalado na reunião.</span><span class="sxs-lookup"><span data-stu-id="ec40b-169">This is the most common error response and is triggered if the app is not installed in the meeting.</span></span> <span data-ttu-id="ec40b-170">Por exemplo, se o aplicativo for desabilitado pelo administrador do locatário ou bloqueado durante a migração do site ativo.</span><span class="sxs-lookup"><span data-stu-id="ec40b-170">For example, if the app is disabled by tenant admin or blocked during live site migration.</span></span>
* <span data-ttu-id="ec40b-171">**200**: as informações do participante foram recuperadas com êxito.</span><span class="sxs-lookup"><span data-stu-id="ec40b-171">**200**: Participant information successfully retrieved.</span></span>
* <span data-ttu-id="ec40b-172">**401**: token inválido.</span><span class="sxs-lookup"><span data-stu-id="ec40b-172">**401**: Invalid token.</span></span>
* <span data-ttu-id="ec40b-173">**404**: o participante não pode ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="ec40b-173">**404**: Participant cannot be found.</span></span>
* <span data-ttu-id="ec40b-174">**500**: a reunião expirou (mais de 60 dias desde o término da reunião) ou o participante não tem permissões com base em sua função.</span><span class="sxs-lookup"><span data-stu-id="ec40b-174">**500**: The meeting has either expired (more than 60 days since the meeting ended) or the participant does not have permissions based on their role.</span></span>


<span data-ttu-id="ec40b-175">**Em breve**</span><span class="sxs-lookup"><span data-stu-id="ec40b-175">**Coming Soon**</span></span>

* <span data-ttu-id="ec40b-176">**404**: a reunião expirou ou o participante não pode ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="ec40b-176">**404**: The meeting has either expired or participant cannot be found.</span></span>


### <a name="notificationsignal-api"></a><span data-ttu-id="ec40b-177">API NotificationSignal</span><span class="sxs-lookup"><span data-stu-id="ec40b-177">NotificationSignal API</span></span>

> [!NOTE]
> <span data-ttu-id="ec40b-178">Quando uma caixa de diálogo na reunião é chamada, o mesmo conteúdo também será apresentado como uma mensagem de chat.</span><span class="sxs-lookup"><span data-stu-id="ec40b-178">When an in-meeting dialog is invoked, the same content will also be presented as a chat message.</span></span>

#### <a name="query-parameters"></a><span data-ttu-id="ec40b-179">Parâmetros de consulta</span><span class="sxs-lookup"><span data-stu-id="ec40b-179">Query parameters</span></span>

|<span data-ttu-id="ec40b-180">Valor</span><span class="sxs-lookup"><span data-stu-id="ec40b-180">Value</span></span>|<span data-ttu-id="ec40b-181">Tipo</span><span class="sxs-lookup"><span data-stu-id="ec40b-181">Type</span></span>|<span data-ttu-id="ec40b-182">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="ec40b-182">Required</span></span>|<span data-ttu-id="ec40b-183">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec40b-183">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="ec40b-184">**conversationId**</span><span class="sxs-lookup"><span data-stu-id="ec40b-184">**conversationId**</span></span>| <span data-ttu-id="ec40b-185">string</span><span class="sxs-lookup"><span data-stu-id="ec40b-185">string</span></span> | <span data-ttu-id="ec40b-186">Sim</span><span class="sxs-lookup"><span data-stu-id="ec40b-186">Yes</span></span> | <span data-ttu-id="ec40b-187">O identificador de conversa está disponível como parte da invocação de bot</span><span class="sxs-lookup"><span data-stu-id="ec40b-187">The conversation identifier is available as part of bot invoke</span></span> |

#### <a name="example"></a><span data-ttu-id="ec40b-188">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ec40b-188">Example</span></span>

> [!NOTE]
>
<span data-ttu-id="ec40b-189">O `completionBotId` parâmetro de `externalResourceUrl` é opcional no exemplo de carga solicitada.</span><span class="sxs-lookup"><span data-stu-id="ec40b-189">The `completionBotId` parameter of the `externalResourceUrl` is optional in the requested payload example.</span></span> <span data-ttu-id="ec40b-190">`Bot ID` é declarado no manifesto e o bot recebe um objeto result.</span><span class="sxs-lookup"><span data-stu-id="ec40b-190">`Bot ID` is declared in the manifest and the bot receives a result object.</span></span>
> * <span data-ttu-id="ec40b-191">Os parâmetros Width e Height de externalResourceUrl devem estar em pixels.</span><span class="sxs-lookup"><span data-stu-id="ec40b-191">The externalResourceUrl width and height parameters must be in pixels.</span></span> <span data-ttu-id="ec40b-192">Consulte as [diretrizes de design](design/designing-apps-in-meetings.md) para garantir que as dimensões estejam dentro dos limites permitidos.</span><span class="sxs-lookup"><span data-stu-id="ec40b-192">Refer to the [design guidelines](design/designing-apps-in-meetings.md) to ensure the dimensions are within the allowed limits.</span></span>
> * <span data-ttu-id="ec40b-193">A URL é a página carregada como uma `<iframe>` caixa de diálogo na reunião.</span><span class="sxs-lookup"><span data-stu-id="ec40b-193">The URL is the page loaded as an `<iframe>` in the in-meeting dialog.</span></span> <span data-ttu-id="ec40b-194">O domínio deve estar na matriz do aplicativo `validDomains` em seu manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ec40b-194">The domain must be in the app's `validDomains` array in your app manifest.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="ec40b-195">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="ec40b-195">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="javascript"></a>[<span data-ttu-id="ec40b-196">JavaScript</span><span class="sxs-lookup"><span data-stu-id="ec40b-196">JavaScript</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="ec40b-197">JSON</span><span class="sxs-lookup"><span data-stu-id="ec40b-197">JSON</span></span>](#tab/json)

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

#### <a name="response-codes"></a><span data-ttu-id="ec40b-198">Códigos de resposta</span><span class="sxs-lookup"><span data-stu-id="ec40b-198">Response Codes</span></span>

* <span data-ttu-id="ec40b-199">**201**: atividade com sinal enviado com êxito</span><span class="sxs-lookup"><span data-stu-id="ec40b-199">**201**: activity with signal is successfully sent</span></span>  
* <span data-ttu-id="ec40b-200">**401**: token inválido</span><span class="sxs-lookup"><span data-stu-id="ec40b-200">**401**: invalid token</span></span>  
* <span data-ttu-id="ec40b-201">**201**: atividade com sinal enviada com êxito.</span><span class="sxs-lookup"><span data-stu-id="ec40b-201">**201**: Activity with signal is successfully sent.</span></span> 
* <span data-ttu-id="ec40b-202">**401**: token inválido.</span><span class="sxs-lookup"><span data-stu-id="ec40b-202">**401**: Invalid token.</span></span>
* <span data-ttu-id="ec40b-203">**403**: o aplicativo não pode enviar o sinal.</span><span class="sxs-lookup"><span data-stu-id="ec40b-203">**403**: The app is unable to send the signal.</span></span> <span data-ttu-id="ec40b-204">Isso pode acontecer devido a vários motivos, como o administrador do locatário desabilita o aplicativo, o aplicativo é bloqueado durante a migração do site ativo e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="ec40b-204">This can happen due to various reasons such as the tenant admin disables the app, the app is blocked during live site migration, and so on.</span></span> <span data-ttu-id="ec40b-205">Nesse caso, a carga contém uma mensagem de erro detalhada.</span><span class="sxs-lookup"><span data-stu-id="ec40b-205">In this case, the payload contains a detailed error message.</span></span> 
* <span data-ttu-id="ec40b-206">**404**: o chat de reunião não existe.</span><span class="sxs-lookup"><span data-stu-id="ec40b-206">**404**: Meeting chat doesn't exist.</span></span>
 

## <a name="enable-your-app-for-teams-meetings"></a><span data-ttu-id="ec40b-207">Habilitar o aplicativo para reuniões do teams</span><span class="sxs-lookup"><span data-stu-id="ec40b-207">Enable your app for Teams meetings</span></span>

### <a name="update-your-app-manifest"></a><span data-ttu-id="ec40b-208">Atualizar o manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="ec40b-208">Update your app manifest</span></span>

<span data-ttu-id="ec40b-209">As funcionalidades de aplicativos de reuniões são declaradas em seu manifesto de aplicativo por meio de  ->  **escopos** configurableTabs e matrizes de **contexto** .</span><span class="sxs-lookup"><span data-stu-id="ec40b-209">The meetings app capabilities are declared in your app manifest via the **configurableTabs** -> **scopes** and **context** arrays.</span></span> <span data-ttu-id="ec40b-210">O *escopo* define para quem e o *contexto* define onde seu aplicativo estará disponível.</span><span class="sxs-lookup"><span data-stu-id="ec40b-210">*Scope* defines to whom and *context* defines where your app will be available.</span></span>

> [!NOTE]
> <span data-ttu-id="ec40b-211">Use o [esquema de manifesto da visualização do desenvolvedor](../resources/schema/manifest-schema-dev-preview.md) para experimentá-lo em seu manifesto de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ec40b-211">Please use [Developer Preview manifest schema](../resources/schema/manifest-schema-dev-preview.md) to try this in your app manifest.</span></span>

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

### <a name="context-property"></a><span data-ttu-id="ec40b-212">Propriedade Context</span><span class="sxs-lookup"><span data-stu-id="ec40b-212">Context property</span></span>

<span data-ttu-id="ec40b-213">A guia `context` e `scopes` as propriedades funcionam em harmonia para permitir que você determine onde você deseja que seu aplicativo apareça.</span><span class="sxs-lookup"><span data-stu-id="ec40b-213">The tab `context` and `scopes` properties work in harmony to allow you to determine where you want your app to appear.</span></span> <span data-ttu-id="ec40b-214">As guias no `team` `groupchat` escopo ou podem ter mais de um contexto.</span><span class="sxs-lookup"><span data-stu-id="ec40b-214">Tabs in the `team` or `groupchat` scope can have more than one context.</span></span> <span data-ttu-id="ec40b-215">Os valores possíveis para a propriedade Context são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="ec40b-215">The possible values for the context property are as follows:</span></span>

* <span data-ttu-id="ec40b-216">**channelTab**: uma guia no cabeçalho de um canal de equipe.</span><span class="sxs-lookup"><span data-stu-id="ec40b-216">**channelTab**: a tab in the header of a team channel.</span></span>
* <span data-ttu-id="ec40b-217">**privateChatTab**: uma guia no cabeçalho de um grupo bate-papo entre um conjunto de usuários que não estão no contexto de uma equipe ou reunião.</span><span class="sxs-lookup"><span data-stu-id="ec40b-217">**privateChatTab**: a tab in the header of a group chat between a set of users not in the context of a team or meeting.</span></span>
* <span data-ttu-id="ec40b-218">**meetingChatTab**: uma guia no cabeçalho de um chat de grupo entre um conjunto de usuários no contexto de uma reunião agendada.</span><span class="sxs-lookup"><span data-stu-id="ec40b-218">**meetingChatTab**: a tab in the header of a group chat between a set of users in the context of a scheduled meeting.</span></span>
* <span data-ttu-id="ec40b-219">**meetingDetailsTab**: uma guia no cabeçalho do modo de exibição detalhes da reunião do calendário.</span><span class="sxs-lookup"><span data-stu-id="ec40b-219">**meetingDetailsTab**: a tab in the header of the meeting details view of the calendar.</span></span>
* <span data-ttu-id="ec40b-220">**meetingSidePanel**: um painel na reunião aberto por meio da barra unificada (u-bar).</span><span class="sxs-lookup"><span data-stu-id="ec40b-220">**meetingSidePanel**: an in-meeting panel opened via the unified bar (u-bar).</span></span>

> [!NOTE]
> <span data-ttu-id="ec40b-221">A propriedade "Context" atualmente não é suportada e, portanto, será ignorada em clientes móveis</span><span class="sxs-lookup"><span data-stu-id="ec40b-221">"Context" property is currently not supported and thus will be ignored on mobile clients</span></span>

## <a name="configure-your-app-for-meeting-scenarios"></a><span data-ttu-id="ec40b-222">Configurar seu aplicativo para cenários de reunião</span><span class="sxs-lookup"><span data-stu-id="ec40b-222">Configure your app for meeting scenarios</span></span>

> [!NOTE]
> * <span data-ttu-id="ec40b-223">Para que seu aplicativo fique visível na Galeria de guias, ele precisa **suportar guias configuráveis** e o **escopo de chat de grupo**.</span><span class="sxs-lookup"><span data-stu-id="ec40b-223">For your app to be visible in the tab gallery it needs to **support configurable tabs** and the **group chat scope**.</span></span>
>
> * <span data-ttu-id="ec40b-224">Os clientes móveis dão suporte a guias apenas nas superfícies de reunião prévia e posterior.</span><span class="sxs-lookup"><span data-stu-id="ec40b-224">Mobile clients support Tabs only in Pre and Post Meeting Surfaces.</span></span> <span data-ttu-id="ec40b-225">As experiências de reunião (guia e caixa de diálogo na reunião) no Mobile estarão disponíveis em breve.</span><span class="sxs-lookup"><span data-stu-id="ec40b-225">The in-meeting experiences (in-meeting dialog and tab) on mobile will be available soon.</span></span> <span data-ttu-id="ec40b-226">Siga as [orientações para guias em celular](../tabs/design/tabs-mobile.md) ao criar suas guias para dispositivos móveis.</span><span class="sxs-lookup"><span data-stu-id="ec40b-226">Follow the [guidance for tabs on mobile](../tabs/design/tabs-mobile.md) when creating your tabs for mobile.</span></span>

### <a name="before-a-meeting"></a><span data-ttu-id="ec40b-227">Antes de uma reunião</span><span class="sxs-lookup"><span data-stu-id="ec40b-227">Before a meeting</span></span>

<span data-ttu-id="ec40b-228">Os usuários com funções de organizador e/ou apresentador adicionam guias a uma reunião usando o botão mais ➕ nas páginas **chat** de reunião e **detalhes** da reunião.</span><span class="sxs-lookup"><span data-stu-id="ec40b-228">Users with organizer and/or presenter roles add tabs to a meeting using the plus ➕ button in the meeting **Chat** and meeting **details** pages.</span></span> <span data-ttu-id="ec40b-229">As extensões de mensagens são adicionadas ao via menu de reticências/estouro &#x25CF;&#x25CF;&#x25CF; localizada abaixo da área de mensagem de composição no chat.</span><span class="sxs-lookup"><span data-stu-id="ec40b-229">Messaging extensions are added to via the ellipses/overflow menu &#x25CF;&#x25CF;&#x25CF; located beneath the compose message area in the chat.</span></span> <span data-ttu-id="ec40b-230">Os bots são adicionados a um chat de reunião usando a **@** tecla "" e selecionando **obter bots**.</span><span class="sxs-lookup"><span data-stu-id="ec40b-230">Bots are added to a meeting chat using the "**@**" key and selecting **Get bots**.</span></span>

<span data-ttu-id="ec40b-231">✔ A identidade do usuário *deve* ser confirmada por meio de [guias de SSO](../tabs/how-to/authentication/auth-aad-sso.md).</span><span class="sxs-lookup"><span data-stu-id="ec40b-231">✔ The user identity *must* be confirmed via [Tabs SSO](../tabs/how-to/authentication/auth-aad-sso.md).</span></span> <span data-ttu-id="ec40b-232">Após essa autenticação, o aplicativo pode recuperar a função de usuário por meio da API getparticipante.</span><span class="sxs-lookup"><span data-stu-id="ec40b-232">Following this authentication, the app can retrieve the user role via the GetParticipant API.</span></span>

 <span data-ttu-id="ec40b-233">✔ Com base na função de usuário, o aplicativo agora terá a capacidade de apresentar experiências específicas de função.</span><span class="sxs-lookup"><span data-stu-id="ec40b-233">✔ Based on the user role, the app will now have the capability to present role specific experiences.</span></span> <span data-ttu-id="ec40b-234">Por exemplo, um aplicativo de sondagem pode permitir que somente os organizadores e os apresentadores criem uma nova pesquisa.</span><span class="sxs-lookup"><span data-stu-id="ec40b-234">For example, a polling app can allow only organizers and presenters to create a new poll.</span></span>

> <span data-ttu-id="ec40b-235">**Observação**: as atribuições de função podem ser alteradas enquanto uma reunião estiver em andamento.</span><span class="sxs-lookup"><span data-stu-id="ec40b-235">**NOTE**: Role assignments can be changed while a meeting is in progress.</span></span>  <span data-ttu-id="ec40b-236">*Consulte* [funções em uma reunião do teams](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span><span class="sxs-lookup"><span data-stu-id="ec40b-236">*See* [Roles in a Teams meeting](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span></span> 

### <a name="during-a-meeting"></a><span data-ttu-id="ec40b-237">Durante uma reunião</span><span class="sxs-lookup"><span data-stu-id="ec40b-237">During a meeting</span></span>

#### <a name="sidepanel"></a><span data-ttu-id="ec40b-238">**sidePanel**</span><span class="sxs-lookup"><span data-stu-id="ec40b-238">**sidePanel**</span></span>

<span data-ttu-id="ec40b-239">✔ Em seu manifesto de aplicativo, adicione **sidePanel** à matriz de **contexto** , conforme descrito acima.</span><span class="sxs-lookup"><span data-stu-id="ec40b-239">✔ In your app manifest add **sidePanel** to the **context** array as described above.</span></span>

<span data-ttu-id="ec40b-240">✔ Na reunião, bem como em todos os cenários, o aplicativo será renderizado em uma guia na reunião que tenha 320px de largura.</span><span class="sxs-lookup"><span data-stu-id="ec40b-240">✔ In the meeting as well as in all scenarios, the app will be rendered in an in-meeting tab that is 320px in width.</span></span> <span data-ttu-id="ec40b-241">Sua guia deve ser otimizada para isso.</span><span class="sxs-lookup"><span data-stu-id="ec40b-241">Your tab must be optimized for this.</span></span> <span data-ttu-id="ec40b-242">*Consulte* [FrameContext interface](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/framecontext?view=msteams-client-js-latest&preserve-view=true
)</span><span class="sxs-lookup"><span data-stu-id="ec40b-242">*See*, [FrameContext interface](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/framecontext?view=msteams-client-js-latest&preserve-view=true
)</span></span>

<span data-ttu-id="ec40b-243">✔ Consultar o [SDK do teams](../tabs/how-to/access-teams-context.md#user-context) para usar a API **userContext** para rotear as solicitações de acordo.</span><span class="sxs-lookup"><span data-stu-id="ec40b-243">✔Refer to the [Teams SDK](../tabs/how-to/access-teams-context.md#user-context) to use the **userContext** API to route requests accordingly.</span></span>

<span data-ttu-id="ec40b-244">✔ Consulte o fluxo de autenticação do Microsoft [Teams para guias](../tabs/how-to/authentication/auth-flow-tab.md).</span><span class="sxs-lookup"><span data-stu-id="ec40b-244">✔ Refer to the [Teams authentication flow for tabs](../tabs/how-to/authentication/auth-flow-tab.md).</span></span> <span data-ttu-id="ec40b-245">O fluxo de autenticação para guias é muito semelhante ao fluxo de autenticação para sites.</span><span class="sxs-lookup"><span data-stu-id="ec40b-245">Authentication flow for tabs is very similar to the auth flow for websites.</span></span> <span data-ttu-id="ec40b-246">Portanto, as guias podem usar o OAuth 2,0 diretamente.</span><span class="sxs-lookup"><span data-stu-id="ec40b-246">Thus, tabs can use OAuth 2.0 directly.</span></span> <span data-ttu-id="ec40b-247">*Confira também* a [plataforma de identidade da Microsoft e o fluxo de código de autorização do OAuth 2,0](/azure/active-directory/develop/v2-oauth2-auth-code-flow).</span><span class="sxs-lookup"><span data-stu-id="ec40b-247">*See also*, [Microsoft identity platform and OAuth 2.0 authorization code flow](/azure/active-directory/develop/v2-oauth2-auth-code-flow).</span></span>

<span data-ttu-id="ec40b-248">✔ Extensão de mensagem deve funcionar conforme o esperado quando um usuário está em um modo de exibição na reunião e deve ser capaz de postar cartões de extensão de mensagem de composição.</span><span class="sxs-lookup"><span data-stu-id="ec40b-248">✔ Message extension should work as expected when a user is in an in-meeting view and should be able to post compose message extension cards.</span></span>

<span data-ttu-id="ec40b-249">✔ AppName em-Meeting-ToolTip deve indicar o nome do aplicativo na-barra U da reunião.</span><span class="sxs-lookup"><span data-stu-id="ec40b-249">✔ AppName in-meeting - Tooltip should state the app name in-meeting U-bar.</span></span>

#### <a name="in-meeting-dialog"></a><span data-ttu-id="ec40b-250">**Caixa de diálogo na reunião**</span><span class="sxs-lookup"><span data-stu-id="ec40b-250">**In-meeting dialog**</span></span>

<span data-ttu-id="ec40b-251">✔ Você deve cumprir as diretrizes de [design da caixa de diálogo na reunião](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog).</span><span class="sxs-lookup"><span data-stu-id="ec40b-251">✔ You must adhere to the [in-meeting dialog design guidelines](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog).</span></span>

<span data-ttu-id="ec40b-252">✔ Consulte o fluxo de autenticação do Microsoft [Teams para guias](../tabs/how-to/authentication/auth-flow-tab.md).</span><span class="sxs-lookup"><span data-stu-id="ec40b-252">✔ Refer to the [Teams authentication flow for tabs](../tabs/how-to/authentication/auth-flow-tab.md).</span></span>

<span data-ttu-id="ec40b-253">✔ Usar a API de [notificação](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) para sinalizar que uma notificação de bolha precisa ser disparada.</span><span class="sxs-lookup"><span data-stu-id="ec40b-253">✔ Use the [notification](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) API to signal that a bubble notification needs to be triggered.</span></span>

<span data-ttu-id="ec40b-254">✔ Como parte da carga de solicitação de notificação, inclua a URL onde o conteúdo a ser expedido está hospedado.</span><span class="sxs-lookup"><span data-stu-id="ec40b-254">✔ As part of the notification request payload, include the URL where the content to be showcased is hosted.</span></span>

<span data-ttu-id="ec40b-255">✔ Caixa de diálogo de reunião não deve usar o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="ec40b-255">✔ In-meeting dialog must not use task module.</span></span>

> [!NOTE]
>
> * <span data-ttu-id="ec40b-256">Essas notificações são persistentes por natureza.</span><span class="sxs-lookup"><span data-stu-id="ec40b-256">These notifications are persistent in nature.</span></span> <span data-ttu-id="ec40b-257">Você deve chamar a função [**submitTask ()**](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) para descartar automaticamente após um usuário executar uma ação no modo de exibição da Web.</span><span class="sxs-lookup"><span data-stu-id="ec40b-257">You must invoke the [**submitTask()**](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) function to auto-dismiss after a user takes an action in the web-view.</span></span> <span data-ttu-id="ec40b-258">Esse é um requisito para o envio de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="ec40b-258">This is a requirement for app submission.</span></span> <span data-ttu-id="ec40b-259">*Consulte também*, [SDK do teams: módulo de tarefa](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="ec40b-259">*See also*, [Teams SDK: task module](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).</span></span>
>
> * <span data-ttu-id="ec40b-260">Se quiser que seu aplicativo dê suporte a usuários anônimos, a carga de solicitação de chamada inicial deve confiar no `from.id`  (ID do usuário) solicitar metadados no `from` objeto, e não no `from.aadObjectId` (Azure Active Directory ID do usuário) solicitar metadados.</span><span class="sxs-lookup"><span data-stu-id="ec40b-260">If you want your app to support anonymous users, your initial invoke request payload must rely on the `from.id`  (ID of the user) request metadata in the `from` object, not the `from.aadObjectId` (Azure Active Directory ID of the user) request metadata.</span></span> <span data-ttu-id="ec40b-261">*Consulte* [usando módulos de tarefas em guias](../task-modules-and-cards/task-modules/task-modules-tabs.md) e [criar e enviar o módulo de tarefa](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).</span><span class="sxs-lookup"><span data-stu-id="ec40b-261">*See* [Using task modules in tabs](../task-modules-and-cards/task-modules/task-modules-tabs.md) and [Create and send the task module](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).</span></span>

### <a name="after-a-meeting"></a><span data-ttu-id="ec40b-262">Após uma reunião</span><span class="sxs-lookup"><span data-stu-id="ec40b-262">After a meeting</span></span>

<span data-ttu-id="ec40b-263">As configurações pós-instalação e pré-reunião são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="ec40b-263">The post-meeting and pre-meeting configurations are equivalent.</span></span>

## <a name="meeting-app-sample"></a><span data-ttu-id="ec40b-264">Exemplo de aplicativo de reunião</span><span class="sxs-lookup"><span data-stu-id="ec40b-264">Meeting app sample</span></span>

 > [!div class="nextstepaction"]
> [<span data-ttu-id="ec40b-265">Aplicativo gerador de token de reunião</span><span class="sxs-lookup"><span data-stu-id="ec40b-265">Meeting token generator app</span></span>](https://github.com/OfficeDev/microsoft-teams-sample-meetings-token)
