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
# <a name="create-apps-for-teams-meetings"></a><span data-ttu-id="caa80-104">Crie aplicativos para reuniões do Teams</span><span class="sxs-lookup"><span data-stu-id="caa80-104">Create apps for Teams meetings</span></span>

## <a name="prerequisites-and-considerations"></a><span data-ttu-id="caa80-105">Pré-requisitos e considerações</span><span class="sxs-lookup"><span data-stu-id="caa80-105">Prerequisites and considerations</span></span>

* <span data-ttu-id="caa80-106">Os aplicativos em reuniões exigem algum conhecimento básico sobre [o desenvolvimento de aplicativos do Teams.](../overview.md)</span><span class="sxs-lookup"><span data-stu-id="caa80-106">Apps in meetings require some basic knowledge of [Teams app development](../overview.md).</span></span> <span data-ttu-id="caa80-107">Um aplicativo em uma reunião pode ser composto [](../messaging-extensions/what-are-messaging-extensions.md) por [guias,](../tabs/what-are-tabs.md) [bots](../bots/what-are-bots.md)e recursos de extensões de mensagens e exigirá atualizações no manifesto do aplicativo [do](#update-your-app-manifest) Teams para indicar que o aplicativo está disponível para reuniões</span><span class="sxs-lookup"><span data-stu-id="caa80-107">An app in a meeting can comprise of [tabs](../tabs/what-are-tabs.md), [bots](../bots/what-are-bots.md), and [messaging extensions](../messaging-extensions/what-are-messaging-extensions.md) features and will require updates to the Teams [app manifest](#update-your-app-manifest) to indicate that the app is available for meetings</span></span>

* <span data-ttu-id="caa80-108">Para que seu aplicativo funcione no ciclo de vida da reunião como uma guia, ele deve dar suporte a guias configuráveis no escopo [de groupchat](../resources/schema/manifest-schema.md#configurabletabs) (consulte como criar [uma guia de grupo](../build-your-first-app/build-channel-tab.md)).</span><span class="sxs-lookup"><span data-stu-id="caa80-108">For your app to function in the meeting lifecycle as a tab, it must support configurable tabs in the [groupchat scope](../resources/schema/manifest-schema.md#configurabletabs) (see how to [build a group tab](../build-your-first-app/build-channel-tab.md)).</span></span> <span data-ttu-id="caa80-109">O suporte `groupchat` ao escopo habilita o aplicativo em chats de [pré-reunião](teams-apps-in-meetings.md#pre-meeting-app-experience) e [pós-reunião.](teams-apps-in-meetings.md#post-meeting-app-experience)</span><span class="sxs-lookup"><span data-stu-id="caa80-109">Supporting the `groupchat` scope will enable your app in [pre-meeting](teams-apps-in-meetings.md#pre-meeting-app-experience) and [post-meeting](teams-apps-in-meetings.md#post-meeting-app-experience) chats.</span></span>

* <span data-ttu-id="caa80-110">Os parâmetros de URL da API de reunião podem exigir , e o tenantId Eles estão disponíveis como parte da atividade do SDK do Cliente do `meetingId` `userId` Teams e do bot. [](/onedrive/find-your-office-365-tenant-id)</span><span class="sxs-lookup"><span data-stu-id="caa80-110">Meeting API URL parameters may require `meetingId`, `userId`, and the [tenantId](/onedrive/find-your-office-365-tenant-id) These are available as part of the Teams Client SDK and bot activity.</span></span> <span data-ttu-id="caa80-111">Além disso, informações confiáveis para iD de usuário e ID de locatário podem ser recuperadas usando [a autenticação tab SSO](../tabs/how-to/authentication/auth-aad-sso.md).</span><span class="sxs-lookup"><span data-stu-id="caa80-111">Additionally, reliable information for user ID and tenant ID can be retrieved using [Tab SSO authentication](../tabs/how-to/authentication/auth-aad-sso.md).</span></span>

* <span data-ttu-id="caa80-112">Algumas APIs de reunião, como , exigem um `GetParticipant` registro de bot e [ID](../build-your-first-app/build-bot.md) para gerar tokens de auth.</span><span class="sxs-lookup"><span data-stu-id="caa80-112">Some meeting APIs, such as `GetParticipant`, require a [bot registration and ID](../build-your-first-app/build-bot.md) to generate auth tokens.</span></span>

* <span data-ttu-id="caa80-113">Você deve seguir as [diretrizes gerais de design](../tabs/design/tabs.md) de guia do Teams para cenários pré e pós-reunião.</span><span class="sxs-lookup"><span data-stu-id="caa80-113">You must adhere to general [Teams tab design guidelines](../tabs/design/tabs.md) for pre- and post-meeting scenarios.</span></span> <span data-ttu-id="caa80-114">Para experiências durante as reuniões, consulte a [guia na reunião](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab) e as [diretrizes](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog) de design da caixa de diálogo na reunião.</span><span class="sxs-lookup"><span data-stu-id="caa80-114">For experiences during meetings, refer to the [in-meeting tab](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab) and [in-meeting dialog](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog) design guidelines.</span></span>

* <span data-ttu-id="caa80-115">Para que seu aplicativo seja atualizado em tempo real, ele deve estar atualizado com base nas atividades do evento na reunião.</span><span class="sxs-lookup"><span data-stu-id="caa80-115">For your app to update in real time, it must be up-to-date based on event activities in the meeting.</span></span> <span data-ttu-id="caa80-116">Esses eventos podem estar dentro da caixa de diálogo na reunião (consulte o parâmetro completion em ) e outras superfícies em todo o ciclo `bot Id` `Notification Signal API` de vida da reunião</span><span class="sxs-lookup"><span data-stu-id="caa80-116">These events can be within the in-meeting dialog (refer to completion `bot Id` parameter in `Notification Signal API`) and other surfaces across the meeting lifecycle</span></span>

## <a name="meeting-apps-api-reference"></a><span data-ttu-id="caa80-117">Referência da API de aplicativos de reunião</span><span class="sxs-lookup"><span data-stu-id="caa80-117">Meeting apps API reference</span></span>

|<span data-ttu-id="caa80-118">API</span><span class="sxs-lookup"><span data-stu-id="caa80-118">API</span></span>|<span data-ttu-id="caa80-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="caa80-119">Description</span></span>|<span data-ttu-id="caa80-120">Solicitação</span><span class="sxs-lookup"><span data-stu-id="caa80-120">Request</span></span>|<span data-ttu-id="caa80-121">Origem</span><span class="sxs-lookup"><span data-stu-id="caa80-121">Source</span></span>|
|---|---|----|---|
|<span data-ttu-id="caa80-122">**GetUserContext**</span><span class="sxs-lookup"><span data-stu-id="caa80-122">**GetUserContext**</span></span>| <span data-ttu-id="caa80-123">Obter informações contextuais para exibir conteúdo relevante em uma guia do Teams.</span><span class="sxs-lookup"><span data-stu-id="caa80-123">Get contextual information to display relevant content in a Teams tab.</span></span> |<span data-ttu-id="caa80-124">_**microsoftTeams.getContext( ( ) => { /*...\* / } )*\*_</span><span class="sxs-lookup"><span data-stu-id="caa80-124">_**microsoftTeams.getContext( ( ) => {  /*...*/ } )**_</span></span>|<span data-ttu-id="caa80-125">SDK de cliente do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="caa80-125">Microsoft Teams client SDK</span></span>|
|<span data-ttu-id="caa80-126">**GetParticipant**</span><span class="sxs-lookup"><span data-stu-id="caa80-126">**GetParticipant**</span></span>|<span data-ttu-id="caa80-127">Essa API permite que um bot busque informações de um participante por meio da ID da reunião e da ID do participante.</span><span class="sxs-lookup"><span data-stu-id="caa80-127">This API allows a bot to fetch a participant information by meeting id and participant id.</span></span>|<span data-ttu-id="caa80-128">**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_</span><span class="sxs-lookup"><span data-stu-id="caa80-128">**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_</span></span> |<span data-ttu-id="caa80-129">Microsoft Bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="caa80-129">Microsoft Bot Framework SDK</span></span>|
|<span data-ttu-id="caa80-130">**NotificationSignal**</span><span class="sxs-lookup"><span data-stu-id="caa80-130">**NotificationSignal**</span></span> |<span data-ttu-id="caa80-131">Os sinais de reunião serão entregues usando a SEGUINTE API de notificação de conversa existente (para chat usuário-bot).</span><span class="sxs-lookup"><span data-stu-id="caa80-131">Meeting signals will be delivered using the following existing conversation notification API (for user-bot chat).</span></span> <span data-ttu-id="caa80-132">Essa API permite que os desenvolvedores sinalizem com base na ação do usuário final para mostrar uma bolha de diálogo na reunião.</span><span class="sxs-lookup"><span data-stu-id="caa80-132">This API allows developers to signal based on end-user action to show-case an in-meeting dialog bubble.</span></span>|<span data-ttu-id="caa80-133">**POST** _**/v3/conversations/{conversationId}/activities**_</span><span class="sxs-lookup"><span data-stu-id="caa80-133">**POST** _**/v3/conversations/{conversationId}/activities**_</span></span>|<span data-ttu-id="caa80-134">Microsoft Bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="caa80-134">Microsoft Bot Framework SDK</span></span>|

### <a name="getusercontext"></a><span data-ttu-id="caa80-135">GetUserContext</span><span class="sxs-lookup"><span data-stu-id="caa80-135">GetUserContext</span></span>

<span data-ttu-id="caa80-136">Consulte nossa documentação da guia [Obter contexto](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library) do Teams para obter orientações sobre a identificação e recuperação de informações contextuais para o conteúdo da guia.</span><span class="sxs-lookup"><span data-stu-id="caa80-136">Please refer to our [Get context for your Teams tab](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library) documentation for guidance on identifying and  retrieving contextual information for your tab content.</span></span> <span data-ttu-id="caa80-137">Como parte da extensibilidade de reuniões, um novo valor foi adicionado para a carga de resposta:</span><span class="sxs-lookup"><span data-stu-id="caa80-137">As part of meetings extensibility, a new value has been added for the response payload:</span></span>

<span data-ttu-id="caa80-138">✔ **meetingId**: usado por uma guia ao executar no contexto da reunião.</span><span class="sxs-lookup"><span data-stu-id="caa80-138">✔ **meetingId**: used by a tab when running in the meeting context.</span></span>

### <a name="getparticipant-api"></a><span data-ttu-id="caa80-139">GetParticipant API</span><span class="sxs-lookup"><span data-stu-id="caa80-139">GetParticipant API</span></span>

> [!NOTE]
>
> * <span data-ttu-id="caa80-140">Não armazenar em cache as funções do participante, pois o organizador da reunião pode alterar uma função a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="caa80-140">Do not cache participant roles since the meeting organizer can change a role at any point in time.</span></span>
>
> * <span data-ttu-id="caa80-141">No momento, o Teams não dá suporte a grandes listas de distribuição ou tamanhos de lista de mais de 350 participantes para a `GetParticipant` API.</span><span class="sxs-lookup"><span data-stu-id="caa80-141">Teams does not currently support large distribution lists or roster sizes of more than 350 participants for the `GetParticipant` API.</span></span>

#### <a name="query-parameters"></a><span data-ttu-id="caa80-142">Parâmetros de consulta</span><span class="sxs-lookup"><span data-stu-id="caa80-142">Query parameters</span></span>

|<span data-ttu-id="caa80-143">Valor</span><span class="sxs-lookup"><span data-stu-id="caa80-143">Value</span></span>|<span data-ttu-id="caa80-144">Tipo</span><span class="sxs-lookup"><span data-stu-id="caa80-144">Type</span></span>|<span data-ttu-id="caa80-145">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="caa80-145">Required</span></span>|<span data-ttu-id="caa80-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="caa80-146">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="caa80-147">**meetingId**</span><span class="sxs-lookup"><span data-stu-id="caa80-147">**meetingId**</span></span>| <span data-ttu-id="caa80-148">string</span><span class="sxs-lookup"><span data-stu-id="caa80-148">string</span></span> | <span data-ttu-id="caa80-149">Sim</span><span class="sxs-lookup"><span data-stu-id="caa80-149">Yes</span></span> | <span data-ttu-id="caa80-150">O identificador de reunião está disponível por meio do Bot Invoke e do SDK do Cliente do Teams.</span><span class="sxs-lookup"><span data-stu-id="caa80-150">The meeting identifier is available through Bot Invoke and Teams Client SDK.</span></span>|
|<span data-ttu-id="caa80-151">**participantId**</span><span class="sxs-lookup"><span data-stu-id="caa80-151">**participantId**</span></span>| <span data-ttu-id="caa80-152">string</span><span class="sxs-lookup"><span data-stu-id="caa80-152">string</span></span> | <span data-ttu-id="caa80-153">Sim</span><span class="sxs-lookup"><span data-stu-id="caa80-153">Yes</span></span> | <span data-ttu-id="caa80-154">O participantId é a ID do usuário.</span><span class="sxs-lookup"><span data-stu-id="caa80-154">The participantId is the user ID.</span></span> <span data-ttu-id="caa80-155">Ele está disponível em Tab SSO, Bot Invoke e Teams Client SDK.</span><span class="sxs-lookup"><span data-stu-id="caa80-155">It is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="caa80-156">É altamente recomendável obter um participantId do SSO da guia.</span><span class="sxs-lookup"><span data-stu-id="caa80-156">It is highly recommended to get a participantId from the Tab SSO.</span></span> |
|<span data-ttu-id="caa80-157">**tenantId**</span><span class="sxs-lookup"><span data-stu-id="caa80-157">**tenantId**</span></span>| <span data-ttu-id="caa80-158">string</span><span class="sxs-lookup"><span data-stu-id="caa80-158">string</span></span> | <span data-ttu-id="caa80-159">Sim</span><span class="sxs-lookup"><span data-stu-id="caa80-159">Yes</span></span> | <span data-ttu-id="caa80-160">A tenantId é necessária para os usuários do locatário.</span><span class="sxs-lookup"><span data-stu-id="caa80-160">The tenantId is required for the tenant users.</span></span> <span data-ttu-id="caa80-161">Ele está disponível em Tab SSO, Bot Invoke e Teams Client SDK.</span><span class="sxs-lookup"><span data-stu-id="caa80-161">It is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="caa80-162">É altamente recomendável obter um tenantId do SSO tab.</span><span class="sxs-lookup"><span data-stu-id="caa80-162">It is highly recommended to get a tenantId from the Tab SSO.</span></span> |

#### <a name="example"></a><span data-ttu-id="caa80-163">Exemplo</span><span class="sxs-lookup"><span data-stu-id="caa80-163">Example</span></span>

# <a name="cnet"></a>[<span data-ttu-id="caa80-164">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="caa80-164">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="javascript"></a>[<span data-ttu-id="caa80-165">JavaScript</span><span class="sxs-lookup"><span data-stu-id="caa80-165">JavaScript</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="caa80-166">JSON</span><span class="sxs-lookup"><span data-stu-id="caa80-166">JSON</span></span>](#tab/json)

```http
GET /v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}
```

<span data-ttu-id="caa80-167">O corpo da resposta é:</span><span class="sxs-lookup"><span data-stu-id="caa80-167">The response body is:</span></span>

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

#### <a name="response-codes"></a><span data-ttu-id="caa80-168">Códigos de resposta</span><span class="sxs-lookup"><span data-stu-id="caa80-168">Response codes</span></span>

* <span data-ttu-id="caa80-169">**403**: O aplicativo não tem permissão para obter informações do participante.</span><span class="sxs-lookup"><span data-stu-id="caa80-169">**403**: The app is not allowed to get participant information.</span></span> <span data-ttu-id="caa80-170">Essa é a resposta de erro mais comum e é disparada se o aplicativo não estiver instalado na reunião.</span><span class="sxs-lookup"><span data-stu-id="caa80-170">This is the most common error response and is triggered if the app is not installed in the meeting.</span></span> <span data-ttu-id="caa80-171">Por exemplo, se o aplicativo for desabilitado pelo administrador do locatário ou bloqueado durante a mitigação de livesite.</span><span class="sxs-lookup"><span data-stu-id="caa80-171">For example, if the app is disabled by tenant admin or blocked during livesite mitigation.</span></span>
* <span data-ttu-id="caa80-172">**200**: Informações do participante recuperadas com êxito.</span><span class="sxs-lookup"><span data-stu-id="caa80-172">**200**: Participant information successfully retrieved.</span></span>
* <span data-ttu-id="caa80-173">**401**: Token inválido.</span><span class="sxs-lookup"><span data-stu-id="caa80-173">**401**: Invalid token.</span></span>
* <span data-ttu-id="caa80-174">**404**: O participante não pode ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="caa80-174">**404**: Participant cannot be found.</span></span>
* <span data-ttu-id="caa80-175">**500**: A reunião expirou (mais de 60 dias desde o fim da reunião) ou o participante não tem permissões com base em sua função.</span><span class="sxs-lookup"><span data-stu-id="caa80-175">**500**: The meeting has either expired (more than 60 days since the meeting ended) or the participant does not have permissions based on their role.</span></span>


<span data-ttu-id="caa80-176">**Em breve**</span><span class="sxs-lookup"><span data-stu-id="caa80-176">**Coming Soon**</span></span>

* <span data-ttu-id="caa80-177">**404**: A reunião expirou ou o participante não pode ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="caa80-177">**404**: The meeting has either expired or participant cannot be found.</span></span>


### <a name="notificationsignal-api"></a><span data-ttu-id="caa80-178">NotificationSignal API</span><span class="sxs-lookup"><span data-stu-id="caa80-178">NotificationSignal API</span></span>

<span data-ttu-id="caa80-179">Todos os usuários em uma reunião recebem as notificações enviadas por meio da API NotificationSignal.</span><span class="sxs-lookup"><span data-stu-id="caa80-179">All users in a meeting receive the notifications sent through the NotificationSignal API.</span></span>

> [!NOTE]
> <span data-ttu-id="caa80-180">Atualmente, não há suporte para o envio de notificações com destino.</span><span class="sxs-lookup"><span data-stu-id="caa80-180">Currently, sending targetted notifications is not supported.</span></span>
> <span data-ttu-id="caa80-181">Quando uma caixa de diálogo na reunião é invocada, o mesmo conteúdo também será apresentado como uma mensagem de chat.</span><span class="sxs-lookup"><span data-stu-id="caa80-181">When an in-meeting dialog is invoked, the same content will also be presented as a chat message.</span></span>

#### <a name="query-parameters"></a><span data-ttu-id="caa80-182">Parâmetros de consulta</span><span class="sxs-lookup"><span data-stu-id="caa80-182">Query parameters</span></span>

|<span data-ttu-id="caa80-183">Valor</span><span class="sxs-lookup"><span data-stu-id="caa80-183">Value</span></span>|<span data-ttu-id="caa80-184">Tipo</span><span class="sxs-lookup"><span data-stu-id="caa80-184">Type</span></span>|<span data-ttu-id="caa80-185">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="caa80-185">Required</span></span>|<span data-ttu-id="caa80-186">Descrição</span><span class="sxs-lookup"><span data-stu-id="caa80-186">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="caa80-187">**conversationId**</span><span class="sxs-lookup"><span data-stu-id="caa80-187">**conversationId**</span></span>| <span data-ttu-id="caa80-188">string</span><span class="sxs-lookup"><span data-stu-id="caa80-188">string</span></span> | <span data-ttu-id="caa80-189">Sim</span><span class="sxs-lookup"><span data-stu-id="caa80-189">Yes</span></span> | <span data-ttu-id="caa80-190">O identificador de conversa está disponível como parte da invocação de bot</span><span class="sxs-lookup"><span data-stu-id="caa80-190">The conversation identifier is available as part of bot invoke</span></span> |

#### <a name="example"></a><span data-ttu-id="caa80-191">Exemplo</span><span class="sxs-lookup"><span data-stu-id="caa80-191">Example</span></span>

<span data-ttu-id="caa80-192">O `Bot ID` é declarado no manifesto e o bot recebe um objeto de resultado.</span><span class="sxs-lookup"><span data-stu-id="caa80-192">The `Bot ID` is declared in the manifest and the bot receives a result object.</span></span> <span data-ttu-id="caa80-193">No exemplo a seguir, `completionBotId` o parâmetro do é opcional na carga `externalResourceUrl` solicitada:</span><span class="sxs-lookup"><span data-stu-id="caa80-193">In the following example, the `completionBotId` parameter of the `externalResourceUrl` is optional in the requested payload:</span></span>

> [!NOTE]
> * <span data-ttu-id="caa80-194">Os `externalResourceUrl` parâmetros de largura e altura devem estar em pixels.</span><span class="sxs-lookup"><span data-stu-id="caa80-194">The `externalResourceUrl` width and height parameters must be in pixels.</span></span> <span data-ttu-id="caa80-195">Para garantir que as dimensões estão dentro dos limites permitidos, consulte [diretrizes de design](design/designing-apps-in-meetings.md).</span><span class="sxs-lookup"><span data-stu-id="caa80-195">To ensure the dimensions are within the allowed limits, see [design guidelines](design/designing-apps-in-meetings.md).</span></span>
> * <span data-ttu-id="caa80-196">A URL é a página carregada como `<iframe>` uma na caixa de diálogo na reunião.</span><span class="sxs-lookup"><span data-stu-id="caa80-196">The URL is the page loaded as an `<iframe>` in the in-meeting dialog.</span></span> <span data-ttu-id="caa80-197">O domínio deve estar na matriz do aplicativo `validDomains` no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="caa80-197">The domain must be in the app's `validDomains` array in your app manifest.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="caa80-198">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="caa80-198">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="javascript"></a>[<span data-ttu-id="caa80-199">JavaScript</span><span class="sxs-lookup"><span data-stu-id="caa80-199">JavaScript</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="caa80-200">JSON</span><span class="sxs-lookup"><span data-stu-id="caa80-200">JSON</span></span>](#tab/json)

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

#### <a name="response-codes"></a><span data-ttu-id="caa80-201">Códigos de resposta</span><span class="sxs-lookup"><span data-stu-id="caa80-201">Response Codes</span></span>

* <span data-ttu-id="caa80-202">**201**: A atividade com sinal é enviada com êxito.</span><span class="sxs-lookup"><span data-stu-id="caa80-202">**201**: Activity with signal is successfully sent.</span></span> 
* <span data-ttu-id="caa80-203">**401**: Token inválido.</span><span class="sxs-lookup"><span data-stu-id="caa80-203">**401**: Invalid token.</span></span>
* <span data-ttu-id="caa80-204">**403**: O aplicativo não consegue enviar o sinal.</span><span class="sxs-lookup"><span data-stu-id="caa80-204">**403**: The app is unable to send the signal.</span></span> <span data-ttu-id="caa80-205">Isso pode acontecer devido a vários motivos, como o administrador de locatários desabilita o aplicativo, o aplicativo é bloqueado durante a migração de site ao vivo e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="caa80-205">This can happen due to various reasons such as the tenant admin disables the app, the app is blocked during live site migration, and so on.</span></span> <span data-ttu-id="caa80-206">Nesse caso, a carga contém uma mensagem de erro detalhada.</span><span class="sxs-lookup"><span data-stu-id="caa80-206">In this case, the payload contains a detailed error message.</span></span> 
* <span data-ttu-id="caa80-207">**404**: O chat de reunião não existe.</span><span class="sxs-lookup"><span data-stu-id="caa80-207">**404**: Meeting chat does not exist.</span></span>
 

## <a name="enable-your-app-for-teams-meetings"></a><span data-ttu-id="caa80-208">Habilitar seu aplicativo para reuniões do Teams</span><span class="sxs-lookup"><span data-stu-id="caa80-208">Enable your app for Teams meetings</span></span>

### <a name="update-your-app-manifest"></a><span data-ttu-id="caa80-209">Atualizar o manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="caa80-209">Update your app manifest</span></span>

<span data-ttu-id="caa80-210">Os recursos do aplicativo de reuniões são declarados no manifesto do aplicativo por meio dos **escopos configurbleTabs**  ->   e **matrizes de** contexto.</span><span class="sxs-lookup"><span data-stu-id="caa80-210">The meetings app capabilities are declared in your app manifest through the **configurableTabs** -> **scopes** and **context** arrays.</span></span> <span data-ttu-id="caa80-211">*O* escopo define a quem e *o contexto* define onde seu aplicativo estará disponível.</span><span class="sxs-lookup"><span data-stu-id="caa80-211">*Scope* defines to whom and *context* defines where your app will be available.</span></span>

> [!NOTE]
> <span data-ttu-id="caa80-212">Use o [esquema de manifesto de Visualização do Desenvolvedor](../resources/schema/manifest-schema-dev-preview.md) para experimentar isso no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="caa80-212">Please use [Developer Preview manifest schema](../resources/schema/manifest-schema-dev-preview.md) to try this in your app manifest.</span></span>

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

### <a name="context-property"></a><span data-ttu-id="caa80-213">Propriedade Context</span><span class="sxs-lookup"><span data-stu-id="caa80-213">Context property</span></span>

<span data-ttu-id="caa80-214">A guia e as propriedades funcionam em harmonia para permitir que você `context` determine onde deseja que seu aplicativo `scopes` apareça.</span><span class="sxs-lookup"><span data-stu-id="caa80-214">The tab `context` and `scopes` properties work in harmony to allow you to determine where you want your app to appear.</span></span> <span data-ttu-id="caa80-215">Guias no `team` escopo ou podem `groupchat` ter mais de um contexto.</span><span class="sxs-lookup"><span data-stu-id="caa80-215">Tabs in the `team` or `groupchat` scope can have more than one context.</span></span> <span data-ttu-id="caa80-216">Os valores possíveis para a propriedade context são os seguinte:</span><span class="sxs-lookup"><span data-stu-id="caa80-216">The possible values for the context property are as follows:</span></span>

* <span data-ttu-id="caa80-217">**channelTab**: uma guia no header de um canal de equipe.</span><span class="sxs-lookup"><span data-stu-id="caa80-217">**channelTab**: a tab in the header of a team channel.</span></span>
* <span data-ttu-id="caa80-218">**privateChatTab**: uma guia no header de um chat de grupo entre um conjunto de usuários que não estão no contexto de uma equipe ou reunião.</span><span class="sxs-lookup"><span data-stu-id="caa80-218">**privateChatTab**: a tab in the header of a group chat between a set of users not in the context of a team or meeting.</span></span>
* <span data-ttu-id="caa80-219">**meetingChatTab**: uma guia no header de um chat de grupo entre um conjunto de usuários no contexto de uma reunião agendada.</span><span class="sxs-lookup"><span data-stu-id="caa80-219">**meetingChatTab**: a tab in the header of a group chat between a set of users in the context of a scheduled meeting.</span></span>
* <span data-ttu-id="caa80-220">**meetingDetailsTab**: uma guia no header da exibição de detalhes da reunião do calendário.</span><span class="sxs-lookup"><span data-stu-id="caa80-220">**meetingDetailsTab**: a tab in the header of the meeting details view of the calendar.</span></span>
* <span data-ttu-id="caa80-221">**meetingSidePanel**: um painel in-meeting aberto por meio da barra unificada (u-bar).</span><span class="sxs-lookup"><span data-stu-id="caa80-221">**meetingSidePanel**: an in-meeting panel opened via the unified bar (u-bar).</span></span>

> [!NOTE]
> <span data-ttu-id="caa80-222">Atualmente, a propriedade "Context" não tem suporte e, portanto, será ignorada em clientes móveis</span><span class="sxs-lookup"><span data-stu-id="caa80-222">"Context" property is currently not supported and thus will be ignored on mobile clients</span></span>

## <a name="configure-your-app-for-meeting-scenarios"></a><span data-ttu-id="caa80-223">Configurar seu aplicativo para cenários de reunião</span><span class="sxs-lookup"><span data-stu-id="caa80-223">Configure your app for meeting scenarios</span></span>

> [!NOTE]
> * <span data-ttu-id="caa80-224">Para que seu aplicativo seja visível na galeria de guias, ele precisa dar suporte a guias **configuráveis** e ao escopo **de chat de grupo.**</span><span class="sxs-lookup"><span data-stu-id="caa80-224">For your app to be visible in the tab gallery it needs to **support configurable tabs** and the **group chat scope**.</span></span>
>
> * <span data-ttu-id="caa80-225">Os clientes móveis só suportam guias em Superfícies de Pré e Pós-Reunião.</span><span class="sxs-lookup"><span data-stu-id="caa80-225">Mobile clients support Tabs only in Pre and Post Meeting Surfaces.</span></span> <span data-ttu-id="caa80-226">As experiências na reunião (caixa de diálogo e guia na reunião) no celular estarão disponíveis em breve.</span><span class="sxs-lookup"><span data-stu-id="caa80-226">The in-meeting experiences (in-meeting dialog and tab) on mobile will be available soon.</span></span> <span data-ttu-id="caa80-227">Siga as [diretrizes para guias em dispositivos móveis](../tabs/design/tabs-mobile.md) ao criar suas guias para dispositivos móveis.</span><span class="sxs-lookup"><span data-stu-id="caa80-227">Follow the [guidance for tabs on mobile](../tabs/design/tabs-mobile.md) when creating your tabs for mobile.</span></span>

### <a name="before-a-meeting"></a><span data-ttu-id="caa80-228">Antes de uma reunião</span><span class="sxs-lookup"><span data-stu-id="caa80-228">Before a meeting</span></span>

<span data-ttu-id="caa80-229">Os usuários com funções de organizador e/ou apresentador adicionam guias a uma reunião usando o botão mais ➕ nas páginas de detalhes do **Chat** e **reunião da** reunião.</span><span class="sxs-lookup"><span data-stu-id="caa80-229">Users with organizer and/or presenter roles add tabs to a meeting using the plus ➕ button in the meeting **Chat** and meeting **details** pages.</span></span> <span data-ttu-id="caa80-230">Extensões de mensagens são adicionadas por meio do menu de releições/estouro &#x25CF;&#x25CF;&#x25CF; localizado abaixo da área de mensagem de composição no chat.</span><span class="sxs-lookup"><span data-stu-id="caa80-230">Messaging extensions are added to via the ellipses/overflow menu &#x25CF;&#x25CF;&#x25CF; located beneath the compose message area in the chat.</span></span> <span data-ttu-id="caa80-231">Bots são adicionados a um chat de reunião usando a **@** tecla " " e **selecionando Obter bots**.</span><span class="sxs-lookup"><span data-stu-id="caa80-231">Bots are added to a meeting chat using the "**@**" key and selecting **Get bots**.</span></span>

<span data-ttu-id="caa80-232">✔ A identidade do *usuário deve* ser confirmada por meio das guias [SSO](../tabs/how-to/authentication/auth-aad-sso.md).</span><span class="sxs-lookup"><span data-stu-id="caa80-232">✔ The user identity *must* be confirmed via [Tabs SSO](../tabs/how-to/authentication/auth-aad-sso.md).</span></span> <span data-ttu-id="caa80-233">Após essa autenticação, o aplicativo pode recuperar a função de usuário por meio da API GetParticipant.</span><span class="sxs-lookup"><span data-stu-id="caa80-233">Following this authentication, the app can retrieve the user role via the GetParticipant API.</span></span>

 <span data-ttu-id="caa80-234">✔ com base na função de usuário, o aplicativo agora terá a capacidade de apresentar experiências específicas de função.</span><span class="sxs-lookup"><span data-stu-id="caa80-234">✔ Based on the user role, the app will now have the capability to present role specific experiences.</span></span> <span data-ttu-id="caa80-235">Por exemplo, um aplicativo de sondagem pode permitir que apenas organizadores e apresentadores criem uma nova sondagem.</span><span class="sxs-lookup"><span data-stu-id="caa80-235">For example, a polling app can allow only organizers and presenters to create a new poll.</span></span>

> <span data-ttu-id="caa80-236">**OBSERVAÇÃO**: as atribuições de função podem ser alteradas enquanto uma reunião está em andamento.</span><span class="sxs-lookup"><span data-stu-id="caa80-236">**NOTE**: Role assignments can be changed while a meeting is in progress.</span></span>  <span data-ttu-id="caa80-237">*Consulte* [Funções em uma reunião do Teams](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span><span class="sxs-lookup"><span data-stu-id="caa80-237">*See* [Roles in a Teams meeting](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span></span> 

### <a name="during-a-meeting"></a><span data-ttu-id="caa80-238">Durante uma reunião</span><span class="sxs-lookup"><span data-stu-id="caa80-238">During a meeting</span></span>

#### <a name="sidepanel"></a><span data-ttu-id="caa80-239">**sidePanel**</span><span class="sxs-lookup"><span data-stu-id="caa80-239">**sidePanel**</span></span>

<span data-ttu-id="caa80-240">✔ Adicionar **sidePanel** no manifesto do aplicativo à matriz **de** contexto conforme descrito acima.</span><span class="sxs-lookup"><span data-stu-id="caa80-240">✔ In your app manifest add **sidePanel** to the **context** array as described above.</span></span>

<span data-ttu-id="caa80-241">✔ Na reunião, bem como em todos os cenários, o aplicativo será renderizado em uma guia na reunião que tem 320px de largura.</span><span class="sxs-lookup"><span data-stu-id="caa80-241">✔ In the meeting as well as in all scenarios, the app will be rendered in an in-meeting tab that is 320px in width.</span></span> <span data-ttu-id="caa80-242">Sua guia deve ser otimizada para isso.</span><span class="sxs-lookup"><span data-stu-id="caa80-242">Your tab must be optimized for this.</span></span> <span data-ttu-id="caa80-243">*Consulte*, [interface FrameContext](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/framecontext?view=msteams-client-js-latest&preserve-view=true
)</span><span class="sxs-lookup"><span data-stu-id="caa80-243">*See*, [FrameContext interface](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/framecontext?view=msteams-client-js-latest&preserve-view=true
)</span></span>

<span data-ttu-id="caa80-244">✔Referir ao [SDK](../tabs/how-to/access-teams-context.md#user-context) do Teams para usar a API **userContext** para rotear solicitações de acordo.</span><span class="sxs-lookup"><span data-stu-id="caa80-244">✔Refer to the [Teams SDK](../tabs/how-to/access-teams-context.md#user-context) to use the **userContext** API to route requests accordingly.</span></span>

<span data-ttu-id="caa80-245">✔ Consulte o fluxo de [autenticação do Teams para guias](../tabs/how-to/authentication/auth-flow-tab.md).</span><span class="sxs-lookup"><span data-stu-id="caa80-245">✔ Refer to the [Teams authentication flow for tabs](../tabs/how-to/authentication/auth-flow-tab.md).</span></span> <span data-ttu-id="caa80-246">O fluxo de autenticação para guias é muito semelhante ao fluxo de autenticação para sites.</span><span class="sxs-lookup"><span data-stu-id="caa80-246">Authentication flow for tabs is very similar to the auth flow for websites.</span></span> <span data-ttu-id="caa80-247">Assim, as guias podem usar o OAuth 2.0 diretamente.</span><span class="sxs-lookup"><span data-stu-id="caa80-247">Thus, tabs can use OAuth 2.0 directly.</span></span> <span data-ttu-id="caa80-248">*Consulte também*, Plataforma de identidade da Microsoft e fluxo de código de autorização [OAuth 2.0](/azure/active-directory/develop/v2-oauth2-auth-code-flow).</span><span class="sxs-lookup"><span data-stu-id="caa80-248">*See also*, [Microsoft identity platform and OAuth 2.0 authorization code flow](/azure/active-directory/develop/v2-oauth2-auth-code-flow).</span></span>

<span data-ttu-id="caa80-249">✔ Extensão de mensagem deve funcionar conforme o esperado quando um usuário estiver em uma exibição em reunião e deve ser capaz de postar cartões de extensão de mensagem de composição.</span><span class="sxs-lookup"><span data-stu-id="caa80-249">✔ Message extension should work as expected when a user is in an in-meeting view and should be able to post compose message extension cards.</span></span>

<span data-ttu-id="caa80-250">✔ AppName na reunião - Dica de ferramenta deve dizer o nome do aplicativo na barra U-bar de reunião.</span><span class="sxs-lookup"><span data-stu-id="caa80-250">✔ AppName in-meeting - Tooltip should state the app name in-meeting U-bar.</span></span>

#### <a name="in-meeting-dialog"></a><span data-ttu-id="caa80-251">**Caixa de diálogo na reunião**</span><span class="sxs-lookup"><span data-stu-id="caa80-251">**In-meeting dialog**</span></span>

<span data-ttu-id="caa80-252">✔ Você deve seguir as diretrizes de design da caixa de [diálogo na reunião.](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)</span><span class="sxs-lookup"><span data-stu-id="caa80-252">✔ You must adhere to the [in-meeting dialog design guidelines](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog).</span></span>

<span data-ttu-id="caa80-253">✔ Consulte o fluxo de [autenticação do Teams para guias](../tabs/how-to/authentication/auth-flow-tab.md).</span><span class="sxs-lookup"><span data-stu-id="caa80-253">✔ Refer to the [Teams authentication flow for tabs](../tabs/how-to/authentication/auth-flow-tab.md).</span></span>

<span data-ttu-id="caa80-254">✔ Use a [API NotificationSignal](create-apps-for-teams-meetings.md#notificationsignal-api) para sinalizar que uma notificação de bolha precisa ser disparada.</span><span class="sxs-lookup"><span data-stu-id="caa80-254">✔ Use the [NotificationSignal API](create-apps-for-teams-meetings.md#notificationsignal-api) to signal that a bubble notification needs to be triggered.</span></span>

<span data-ttu-id="caa80-255">✔ Como parte da carga da solicitação de notificação, inclua a URL onde o conteúdo a ser exibido está hospedado.</span><span class="sxs-lookup"><span data-stu-id="caa80-255">✔ As part of the notification request payload, include the URL where the content to be showcased is hosted.</span></span>

<span data-ttu-id="caa80-256">✔ caixa de diálogo In-meeting não deve usar o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="caa80-256">✔ In-meeting dialog must not use task module.</span></span>

> [!NOTE]
>
> * <span data-ttu-id="caa80-257">Essas notificações são persistentes na natureza.</span><span class="sxs-lookup"><span data-stu-id="caa80-257">These notifications are persistent in nature.</span></span> <span data-ttu-id="caa80-258">Você deve invocar [**a função submitTask()**](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) para descartar automaticamente depois que um usuário realizar uma ação no modo de exibição da Web.</span><span class="sxs-lookup"><span data-stu-id="caa80-258">You must invoke the [**submitTask()**](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) function to auto-dismiss after a user takes an action in the web-view.</span></span> <span data-ttu-id="caa80-259">Esse é um requisito para envio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="caa80-259">This is a requirement for app submission.</span></span> <span data-ttu-id="caa80-260">*Consulte também*, [SDK do Teams: módulo de tarefa](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="caa80-260">*See also*, [Teams SDK: task module](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).</span></span>
>
> * <span data-ttu-id="caa80-261">Se você quiser que seu aplicativo suporte usuários anônimos, sua carga inicial de solicitação de invocação deve depender dos metadados de solicitação (ID do usuário) no objeto, e não nos metadados de solicitação `from.id` `from` (ID do `from.aadObjectId` Azure Active Directory do usuário).</span><span class="sxs-lookup"><span data-stu-id="caa80-261">If you want your app to support anonymous users, your initial invoke request payload must rely on the `from.id`  (ID of the user) request metadata in the `from` object, not the `from.aadObjectId` (Azure Active Directory ID of the user) request metadata.</span></span> <span data-ttu-id="caa80-262">*Consulte* [Usando módulos de tarefa em guias](../task-modules-and-cards/task-modules/task-modules-tabs.md) e Criar e enviar o módulo de [tarefa](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).</span><span class="sxs-lookup"><span data-stu-id="caa80-262">*See* [Using task modules in tabs](../task-modules-and-cards/task-modules/task-modules-tabs.md) and [Create and send the task module](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).</span></span>

### <a name="after-a-meeting"></a><span data-ttu-id="caa80-263">Após uma reunião</span><span class="sxs-lookup"><span data-stu-id="caa80-263">After a meeting</span></span>

<span data-ttu-id="caa80-264">As configurações pós-reunião e pré-reunião são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="caa80-264">The post-meeting and pre-meeting configurations are equivalent.</span></span>

## <a name="meeting-app-sample"></a><span data-ttu-id="caa80-265">Exemplo de aplicativo de reunião</span><span class="sxs-lookup"><span data-stu-id="caa80-265">Meeting app sample</span></span>

 > [!div class="nextstepaction"]
> [<span data-ttu-id="caa80-266">Aplicativo gerador de token de reunião</span><span class="sxs-lookup"><span data-stu-id="caa80-266">Meeting token generator app</span></span>](https://github.com/OfficeDev/microsoft-teams-sample-meetings-token)
