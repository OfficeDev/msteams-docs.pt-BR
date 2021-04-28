---
title: Criar aplicativos para reuniões do Teams
author: laujan
description: criar aplicativos para reuniões do teams
ms.topic: conceptual
ms.author: lajanuar
localization_priority: Normal
keywords: api de função de participante de reuniões de aplicativos do teams
ms.openlocfilehash: 741f39c2aca6e99fb7bdfaa1171de4e2bb1e7755
ms.sourcegitcommit: a732789190f59ec1f3699e8ad2f06387e8fe1458
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2021
ms.locfileid: "52058345"
---
# <a name="create-apps-for-teams-meetings"></a><span data-ttu-id="a69d0-104">Crie aplicativos para reuniões do Teams</span><span class="sxs-lookup"><span data-stu-id="a69d0-104">Create apps for Teams meetings</span></span>

## <a name="prerequisites-and-considerations"></a><span data-ttu-id="a69d0-105">Pré-requisitos e considerações</span><span class="sxs-lookup"><span data-stu-id="a69d0-105">Prerequisites and considerations</span></span>

<span data-ttu-id="a69d0-106">Antes de criar aplicativos para reuniões do Teams, você deve ter uma compreensão do seguinte:</span><span class="sxs-lookup"><span data-stu-id="a69d0-106">Before you create apps for Teams meetings, you must have an understanding of the following:</span></span>

* <span data-ttu-id="a69d0-107">Você deve ter conhecimento de como desenvolver aplicativos do Teams.</span><span class="sxs-lookup"><span data-stu-id="a69d0-107">You must have knowledge of how to develop Teams apps.</span></span> <span data-ttu-id="a69d0-108">Para obter mais informações, consulte [Desenvolvimento de aplicativos do Teams](../overview.md).</span><span class="sxs-lookup"><span data-stu-id="a69d0-108">For more information, see [Teams app development](../overview.md).</span></span>

* <span data-ttu-id="a69d0-109">Você deve atualizar o manifesto do aplicativo do Teams para indicar que o aplicativo está disponível para reuniões.</span><span class="sxs-lookup"><span data-stu-id="a69d0-109">You must update the Teams app manifest to indicate that the app is available for meetings.</span></span> <span data-ttu-id="a69d0-110">Para obter mais informações, consulte [manifesto do aplicativo](#update-your-app-manifest).</span><span class="sxs-lookup"><span data-stu-id="a69d0-110">For more information, see [app manifest](#update-your-app-manifest).</span></span>

* <span data-ttu-id="a69d0-111">Para que seu aplicativo funcione no ciclo de vida da reunião como uma guia, ele deve dar suporte a guias configuráveis no escopo de groupchat.</span><span class="sxs-lookup"><span data-stu-id="a69d0-111">For your app to function in the meeting lifecycle as a tab, it must support configurable tabs in the groupchat scope.</span></span> <span data-ttu-id="a69d0-112">Para obter mais informações, consulte [groupchat scope](../resources/schema/manifest-schema.md#configurabletabs) and [build a group tab](../build-your-first-app/build-channel-tab.md).</span><span class="sxs-lookup"><span data-stu-id="a69d0-112">For more information, see [groupchat scope](../resources/schema/manifest-schema.md#configurabletabs) and [build a group tab](../build-your-first-app/build-channel-tab.md).</span></span>

* <span data-ttu-id="a69d0-113">Você deve seguir as diretrizes gerais de design de guia do Teams para cenários pré e pós-reunião.</span><span class="sxs-lookup"><span data-stu-id="a69d0-113">You must adhere to general Teams tab design guidelines for pre- and post-meeting scenarios.</span></span> <span data-ttu-id="a69d0-114">Para experiências durante as reuniões, consulte a guia na reunião e as diretrizes de design da caixa de diálogo na reunião.</span><span class="sxs-lookup"><span data-stu-id="a69d0-114">For experiences during meetings, refer to the in-meeting tab and in-meeting dialog design guidelines.</span></span> <span data-ttu-id="a69d0-115">Para obter mais informações, consulte Diretrizes de design de [guia do Teams,](../tabs/design/tabs.md)diretrizes de [design](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab) da guia de reunião e diretrizes de design de caixa de diálogo [na reunião.](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)</span><span class="sxs-lookup"><span data-stu-id="a69d0-115">For more information, see [Teams tab design guidelines](../tabs/design/tabs.md), [in-meeting tab design guidelines](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab) and [in-meeting dialog design guidelines](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog).</span></span>

* <span data-ttu-id="a69d0-116">Você deve dar suporte ao escopo para habilitar seu aplicativo em chats de `groupchat` pré-reunião e pós-reunião.</span><span class="sxs-lookup"><span data-stu-id="a69d0-116">You must support the `groupchat` scope to enable your app in pre-meeting and post-meeting chats.</span></span> <span data-ttu-id="a69d0-117">Com a experiência do aplicativo de pré-reunião, você pode encontrar e adicionar aplicativos de reunião e realizar tarefas de pré-reunião.</span><span class="sxs-lookup"><span data-stu-id="a69d0-117">With the pre-meeting app experience, you can find and add meeting apps and perform pre-meeting tasks.</span></span> <span data-ttu-id="a69d0-118">Com a experiência do aplicativo pós-reunião, você pode exibir os resultados da reunião, como resultados da pesquisa ou comentários.</span><span class="sxs-lookup"><span data-stu-id="a69d0-118">With post-meeting app experience, you can view the results of the meeting, such as poll survey results or feedback.</span></span>

* <span data-ttu-id="a69d0-119">Os parâmetros de URL da API de reunião `meetingId` devem ter , e `userId` `tenantId` .</span><span class="sxs-lookup"><span data-stu-id="a69d0-119">Meeting API URL parameters must have `meetingId`, `userId`, and `tenantId`.</span></span> <span data-ttu-id="a69d0-120">Eles estão disponíveis como parte da atividade de SDK e bot do cliente do Teams.</span><span class="sxs-lookup"><span data-stu-id="a69d0-120">These are available as part of the Teams client SDK and bot activity.</span></span> <span data-ttu-id="a69d0-121">Além disso, informações confiáveis para iD de usuário e ID de locatário podem ser recuperadas usando [a autenticação tab SSO](../tabs/how-to/authentication/auth-aad-sso.md).</span><span class="sxs-lookup"><span data-stu-id="a69d0-121">In addition, reliable information for user ID and tenant ID can be retrieved using [Tab SSO authentication](../tabs/how-to/authentication/auth-aad-sso.md).</span></span>

* <span data-ttu-id="a69d0-122">A `GetParticipant` API deve ter um registro de bot e uma ID para gerar tokens de auth.</span><span class="sxs-lookup"><span data-stu-id="a69d0-122">The `GetParticipant` API must have a bot registration and ID to generate auth tokens.</span></span> <span data-ttu-id="a69d0-123">Para obter mais informações, [consulte registro de bot e ID](../build-your-first-app/build-bot.md).</span><span class="sxs-lookup"><span data-stu-id="a69d0-123">For more information, see [bot registration and ID](../build-your-first-app/build-bot.md).</span></span>

* <span data-ttu-id="a69d0-124">Para que seu aplicativo seja atualizado em tempo real, ele deve estar atualizado com base nas atividades do evento na reunião.</span><span class="sxs-lookup"><span data-stu-id="a69d0-124">For your app to update in real time, it must be up-to-date based on event activities in the meeting.</span></span> <span data-ttu-id="a69d0-125">Esses eventos podem estar dentro da caixa de diálogo na reunião e em outros estágios no ciclo de vida da reunião.</span><span class="sxs-lookup"><span data-stu-id="a69d0-125">These events can be within the in-meeting dialog box and other stages across the meeting lifecycle.</span></span> <span data-ttu-id="a69d0-126">Para a caixa de diálogo na reunião, consulte o parâmetro completion `bot Id` em `Notification Signal API` .</span><span class="sxs-lookup"><span data-stu-id="a69d0-126">For the in-meeting dialog box, see completion `bot Id` parameter in `Notification Signal API`.</span></span>

## <a name="meeting-apps-api-reference"></a><span data-ttu-id="a69d0-127">Referência da API de aplicativos de reunião</span><span class="sxs-lookup"><span data-stu-id="a69d0-127">Meeting apps API reference</span></span>

|<span data-ttu-id="a69d0-128">API</span><span class="sxs-lookup"><span data-stu-id="a69d0-128">API</span></span>|<span data-ttu-id="a69d0-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="a69d0-129">Description</span></span>|<span data-ttu-id="a69d0-130">Solicitação</span><span class="sxs-lookup"><span data-stu-id="a69d0-130">Request</span></span>|<span data-ttu-id="a69d0-131">Origem</span><span class="sxs-lookup"><span data-stu-id="a69d0-131">Source</span></span>|
|---|---|----|---|
|<span data-ttu-id="a69d0-132">**GetUserContext**</span><span class="sxs-lookup"><span data-stu-id="a69d0-132">**GetUserContext**</span></span>| <span data-ttu-id="a69d0-133">Essa API permite que você receba informações contextuais para exibir conteúdo relevante em uma guia do Teams.</span><span class="sxs-lookup"><span data-stu-id="a69d0-133">This API enables you to get contextual information to display relevant content in a Teams tab.</span></span> |<span data-ttu-id="a69d0-134">_**microsoftTeams.getContext( ( ) => { /*...\* / } )*\*_</span><span class="sxs-lookup"><span data-stu-id="a69d0-134">_**microsoftTeams.getContext( ( ) => {  /*...*/ } )**_</span></span>|<span data-ttu-id="a69d0-135">SDK de cliente do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="a69d0-135">Microsoft Teams client SDK</span></span>|
|<span data-ttu-id="a69d0-136">**GetParticipant**</span><span class="sxs-lookup"><span data-stu-id="a69d0-136">**GetParticipant**</span></span>| <span data-ttu-id="a69d0-137">Essa API permite que um bot busque informações dos participantes por meio da ID da reunião e da ID do participante.</span><span class="sxs-lookup"><span data-stu-id="a69d0-137">This API allows a bot to fetch participant information by meeting ID and participant ID.</span></span> |<span data-ttu-id="a69d0-138">**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_</span><span class="sxs-lookup"><span data-stu-id="a69d0-138">**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_</span></span> |<span data-ttu-id="a69d0-139">Microsoft Bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="a69d0-139">Microsoft Bot Framework SDK</span></span>|
|<span data-ttu-id="a69d0-140">**NotificationSignal**</span><span class="sxs-lookup"><span data-stu-id="a69d0-140">**NotificationSignal**</span></span> | <span data-ttu-id="a69d0-141">Essa API permite que você forneça sinais de reunião que são entregues usando a API de notificação de conversa existente para chat de usuário-bot.</span><span class="sxs-lookup"><span data-stu-id="a69d0-141">This API enables you to provide meeting signals that are delivered using the existing conversation notification API for user-bot chat.</span></span> <span data-ttu-id="a69d0-142">Ele permite sinalizar com base na ação do usuário que mostra uma caixa de diálogo na reunião.</span><span class="sxs-lookup"><span data-stu-id="a69d0-142">It allows you to signal based on user action that shows an in-meeting dialog box.</span></span> |<span data-ttu-id="a69d0-143">**POST** _**/v3/conversations/{conversationId}/activities**_</span><span class="sxs-lookup"><span data-stu-id="a69d0-143">**POST** _**/v3/conversations/{conversationId}/activities**_</span></span>|<span data-ttu-id="a69d0-144">Microsoft Bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="a69d0-144">Microsoft Bot Framework SDK</span></span>|

### <a name="getusercontext"></a><span data-ttu-id="a69d0-145">GetUserContext</span><span class="sxs-lookup"><span data-stu-id="a69d0-145">GetUserContext</span></span>

<span data-ttu-id="a69d0-146">Para identificar e recuperar informações contextuais para o conteúdo da guia, consulte [obter contexto para a guia Do Teams.](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library) `meetingId` é usado por uma guia ao ser executado no contexto da reunião e é adicionado para a carga de resposta.</span><span class="sxs-lookup"><span data-stu-id="a69d0-146">To identify and retrieve contextual information for your tab content, see [get context for your Teams tab](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library). `meetingId` is used by a tab when running in the meeting context and is added for the response payload.</span></span>

### <a name="getparticipant-api"></a><span data-ttu-id="a69d0-147">GetParticipant API</span><span class="sxs-lookup"><span data-stu-id="a69d0-147">GetParticipant API</span></span>

> [!NOTE]
> * <span data-ttu-id="a69d0-148">Não armazenar em cache as funções do participante, pois o organizador da reunião pode alterar uma função a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="a69d0-148">Do not cache participant roles since the meeting organizer can change a role any time.</span></span>
> * <span data-ttu-id="a69d0-149">No momento, o Teams não dá suporte a grandes listas de distribuição ou tamanhos de lista de mais de 350 participantes para a `GetParticipant` API.</span><span class="sxs-lookup"><span data-stu-id="a69d0-149">Teams does not currently support large distribution lists or roster sizes of more than 350 participants for the `GetParticipant` API.</span></span>

#### <a name="query-parameters"></a><span data-ttu-id="a69d0-150">Parâmetros de consulta</span><span class="sxs-lookup"><span data-stu-id="a69d0-150">Query parameters</span></span>

|<span data-ttu-id="a69d0-151">Valor</span><span class="sxs-lookup"><span data-stu-id="a69d0-151">Value</span></span>|<span data-ttu-id="a69d0-152">Tipo</span><span class="sxs-lookup"><span data-stu-id="a69d0-152">Type</span></span>|<span data-ttu-id="a69d0-153">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="a69d0-153">Required</span></span>|<span data-ttu-id="a69d0-154">Descrição</span><span class="sxs-lookup"><span data-stu-id="a69d0-154">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="a69d0-155">**meetingId**</span><span class="sxs-lookup"><span data-stu-id="a69d0-155">**meetingId**</span></span>| <span data-ttu-id="a69d0-156">string</span><span class="sxs-lookup"><span data-stu-id="a69d0-156">string</span></span> | <span data-ttu-id="a69d0-157">Sim</span><span class="sxs-lookup"><span data-stu-id="a69d0-157">Yes</span></span> | <span data-ttu-id="a69d0-158">O identificador de reunião está disponível por meio do Bot Invoke e do SDK do Cliente do Teams.</span><span class="sxs-lookup"><span data-stu-id="a69d0-158">The meeting identifier is available through Bot Invoke and Teams Client SDK.</span></span>|
|<span data-ttu-id="a69d0-159">**participantId**</span><span class="sxs-lookup"><span data-stu-id="a69d0-159">**participantId**</span></span>| <span data-ttu-id="a69d0-160">string</span><span class="sxs-lookup"><span data-stu-id="a69d0-160">string</span></span> | <span data-ttu-id="a69d0-161">Sim</span><span class="sxs-lookup"><span data-stu-id="a69d0-161">Yes</span></span> | <span data-ttu-id="a69d0-162">A ID do participante é a ID do usuário.</span><span class="sxs-lookup"><span data-stu-id="a69d0-162">The participant ID is the user ID.</span></span> <span data-ttu-id="a69d0-163">Ele está disponível em Tab SSO, Bot Invoke e Teams Client SDK.</span><span class="sxs-lookup"><span data-stu-id="a69d0-163">It is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="a69d0-164">É recomendável obter uma ID do participante no SSO da guia.</span><span class="sxs-lookup"><span data-stu-id="a69d0-164">It is recommended to get a participant ID from the Tab SSO.</span></span> |
|<span data-ttu-id="a69d0-165">**tenantId**</span><span class="sxs-lookup"><span data-stu-id="a69d0-165">**tenantId**</span></span>| <span data-ttu-id="a69d0-166">string</span><span class="sxs-lookup"><span data-stu-id="a69d0-166">string</span></span> | <span data-ttu-id="a69d0-167">Sim</span><span class="sxs-lookup"><span data-stu-id="a69d0-167">Yes</span></span> | <span data-ttu-id="a69d0-168">A ID do locatário é necessária para os usuários do locatário.</span><span class="sxs-lookup"><span data-stu-id="a69d0-168">The tenant ID is required for the tenant users.</span></span> <span data-ttu-id="a69d0-169">Ele está disponível em Tab SSO, Bot Invoke e Teams Client SDK.</span><span class="sxs-lookup"><span data-stu-id="a69d0-169">It is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="a69d0-170">É recomendável obter uma ID de locatário do SSO de tabulação.</span><span class="sxs-lookup"><span data-stu-id="a69d0-170">It is recommended to get a tenant ID from the Tab SSO.</span></span> |

#### <a name="example"></a><span data-ttu-id="a69d0-171">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a69d0-171">Example</span></span>

# <a name="c"></a>[<span data-ttu-id="a69d0-172">C#</span><span class="sxs-lookup"><span data-stu-id="a69d0-172">C#</span></span>](#tab/dotnet)

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

# <a name="javascript"></a>[<span data-ttu-id="a69d0-173">JavaScript</span><span class="sxs-lookup"><span data-stu-id="a69d0-173">JavaScript</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="a69d0-174">JSON</span><span class="sxs-lookup"><span data-stu-id="a69d0-174">JSON</span></span>](#tab/json)

```http
GET /v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}
```

* * *

<span data-ttu-id="a69d0-175">O corpo de resposta JSON para `GetParticipant` API é:</span><span class="sxs-lookup"><span data-stu-id="a69d0-175">The JSON response body for `GetParticipant` API is:</span></span>

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

#### <a name="response-codes"></a><span data-ttu-id="a69d0-176">Códigos de resposta</span><span class="sxs-lookup"><span data-stu-id="a69d0-176">Response codes</span></span>

|<span data-ttu-id="a69d0-177">Código da resposta</span><span class="sxs-lookup"><span data-stu-id="a69d0-177">Response code</span></span>|<span data-ttu-id="a69d0-178">Descrição</span><span class="sxs-lookup"><span data-stu-id="a69d0-178">Description</span></span>|
|---|---|
| <span data-ttu-id="a69d0-179">**403**</span><span class="sxs-lookup"><span data-stu-id="a69d0-179">**403**</span></span> | <span data-ttu-id="a69d0-180">O aplicativo não tem permissão para obter informações do participante.</span><span class="sxs-lookup"><span data-stu-id="a69d0-180">The app is not allowed to get participant information.</span></span> <span data-ttu-id="a69d0-181">Essa é a resposta de erro mais comum e é disparada se o aplicativo não estiver instalado na reunião.</span><span class="sxs-lookup"><span data-stu-id="a69d0-181">This is the most common error response and is triggered if the app is not installed in the meeting.</span></span> <span data-ttu-id="a69d0-182">Por exemplo, se o aplicativo for desabilitado pelo administrador do locatário ou bloqueado durante a migração do site ao vivo.</span><span class="sxs-lookup"><span data-stu-id="a69d0-182">For example, if the app is disabled by tenant admin or blocked during live site migration.</span></span>|
| <span data-ttu-id="a69d0-183">**200**</span><span class="sxs-lookup"><span data-stu-id="a69d0-183">**200**</span></span> | <span data-ttu-id="a69d0-184">As informações do participante são recuperadas com êxito.</span><span class="sxs-lookup"><span data-stu-id="a69d0-184">The participant information is successfully retrieved.</span></span>|
| <span data-ttu-id="a69d0-185">**401**</span><span class="sxs-lookup"><span data-stu-id="a69d0-185">**401**</span></span> | <span data-ttu-id="a69d0-186">O aplicativo responde com um token inválido.</span><span class="sxs-lookup"><span data-stu-id="a69d0-186">The app responds with an invalid token.</span></span>|
| <span data-ttu-id="a69d0-187">**404**</span><span class="sxs-lookup"><span data-stu-id="a69d0-187">**404**</span></span> | <span data-ttu-id="a69d0-188">A reunião expirou ou o participante não pode ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="a69d0-188">The meeting has either expired or participant cannot be found.</span></span>|
| <span data-ttu-id="a69d0-189">**500**</span><span class="sxs-lookup"><span data-stu-id="a69d0-189">**500**</span></span> | <span data-ttu-id="a69d0-190">A reunião expirou mais de 60 dias desde que a reunião terminou ou o participante não tem permissões com base em sua função.</span><span class="sxs-lookup"><span data-stu-id="a69d0-190">The meeting has either expired more than 60 days since the meeting ended or the participant does not have permissions based on their role.</span></span>|

### <a name="notificationsignal-api"></a><span data-ttu-id="a69d0-191">NotificationSignal API</span><span class="sxs-lookup"><span data-stu-id="a69d0-191">NotificationSignal API</span></span>

<span data-ttu-id="a69d0-192">Todos os usuários em uma reunião recebem as notificações enviadas por meio da `NotificationSignal` API.</span><span class="sxs-lookup"><span data-stu-id="a69d0-192">All users in a meeting receive the notifications sent through the `NotificationSignal` API.</span></span>

> [!NOTE]
> * <span data-ttu-id="a69d0-193">Quando uma caixa de diálogo na reunião é invocada, o conteúdo é apresentado como uma mensagem de chat.</span><span class="sxs-lookup"><span data-stu-id="a69d0-193">When an in-meeting dialog box is invoked, the content is presented as a chat message.</span></span>
> * <span data-ttu-id="a69d0-194">Atualmente, não há suporte para o envio de notificações direcionadas.</span><span class="sxs-lookup"><span data-stu-id="a69d0-194">Currently, sending targeted notifications is not supported.</span></span>

#### <a name="query-parameters"></a><span data-ttu-id="a69d0-195">Parâmetros de consulta</span><span class="sxs-lookup"><span data-stu-id="a69d0-195">Query parameters</span></span>

|<span data-ttu-id="a69d0-196">Valor</span><span class="sxs-lookup"><span data-stu-id="a69d0-196">Value</span></span>|<span data-ttu-id="a69d0-197">Tipo</span><span class="sxs-lookup"><span data-stu-id="a69d0-197">Type</span></span>|<span data-ttu-id="a69d0-198">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="a69d0-198">Required</span></span>|<span data-ttu-id="a69d0-199">Descrição</span><span class="sxs-lookup"><span data-stu-id="a69d0-199">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="a69d0-200">**conversationId**</span><span class="sxs-lookup"><span data-stu-id="a69d0-200">**conversationId**</span></span>| <span data-ttu-id="a69d0-201">string</span><span class="sxs-lookup"><span data-stu-id="a69d0-201">string</span></span> | <span data-ttu-id="a69d0-202">Sim</span><span class="sxs-lookup"><span data-stu-id="a69d0-202">Yes</span></span> | <span data-ttu-id="a69d0-203">O identificador de conversa está disponível como parte da invocação de bot</span><span class="sxs-lookup"><span data-stu-id="a69d0-203">The conversation identifier is available as part of bot invoke</span></span> |

#### <a name="example"></a><span data-ttu-id="a69d0-204">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a69d0-204">Example</span></span>

<span data-ttu-id="a69d0-205">O `Bot ID` é declarado no manifesto e o bot recebe um objeto de resultado.</span><span class="sxs-lookup"><span data-stu-id="a69d0-205">The `Bot ID` is declared in the manifest and the bot receives a result object.</span></span>

> [!NOTE]
> * <span data-ttu-id="a69d0-206">O `completionBotId` parâmetro do é opcional no exemplo de carga `externalResourceUrl` solicitada.</span><span class="sxs-lookup"><span data-stu-id="a69d0-206">The `completionBotId` parameter of the `externalResourceUrl` is optional in the requested payload example.</span></span> <span data-ttu-id="a69d0-207">`Bot ID` é declarado no manifesto e o bot recebe um objeto de resultado.</span><span class="sxs-lookup"><span data-stu-id="a69d0-207">`Bot ID` is declared in the manifest and the bot receives a result object.</span></span>
> * <span data-ttu-id="a69d0-208">Os `externalResourceUrl` parâmetros de largura e altura devem estar em pixels.</span><span class="sxs-lookup"><span data-stu-id="a69d0-208">The `externalResourceUrl` width and height parameters must be in pixels.</span></span> <span data-ttu-id="a69d0-209">Para garantir que as dimensões estão dentro dos limites permitidos, consulte [diretrizes de design](design/designing-apps-in-meetings.md).</span><span class="sxs-lookup"><span data-stu-id="a69d0-209">To ensure the dimensions are within the allowed limits, see [design guidelines](design/designing-apps-in-meetings.md).</span></span>
> * <span data-ttu-id="a69d0-210">A URL é a página carregada como `<iframe>` uma caixa de diálogo na reunião.</span><span class="sxs-lookup"><span data-stu-id="a69d0-210">The URL is the page loaded as an `<iframe>` in the in-meeting dialog box.</span></span> <span data-ttu-id="a69d0-211">O domínio deve estar na matriz do aplicativo `validDomains` no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a69d0-211">The domain must be in the app's `validDomains` array in your app manifest.</span></span>

# <a name="c"></a>[<span data-ttu-id="a69d0-212">C#</span><span class="sxs-lookup"><span data-stu-id="a69d0-212">C#</span></span>](#tab/dotnet)

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

# <a name="javascript"></a>[<span data-ttu-id="a69d0-213">JavaScript</span><span class="sxs-lookup"><span data-stu-id="a69d0-213">JavaScript</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="a69d0-214">JSON</span><span class="sxs-lookup"><span data-stu-id="a69d0-214">JSON</span></span>](#tab/json)

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

#### <a name="response-codes"></a><span data-ttu-id="a69d0-215">Códigos de resposta</span><span class="sxs-lookup"><span data-stu-id="a69d0-215">Response codes</span></span>

|<span data-ttu-id="a69d0-216">Código da resposta</span><span class="sxs-lookup"><span data-stu-id="a69d0-216">Response code</span></span>|<span data-ttu-id="a69d0-217">Descrição</span><span class="sxs-lookup"><span data-stu-id="a69d0-217">Description</span></span>|
|---|---|
| <span data-ttu-id="a69d0-218">**201**</span><span class="sxs-lookup"><span data-stu-id="a69d0-218">**201**</span></span> | <span data-ttu-id="a69d0-219">A atividade com sinal é enviada com êxito</span><span class="sxs-lookup"><span data-stu-id="a69d0-219">The activity with signal is successfully sent</span></span> |
| <span data-ttu-id="a69d0-220">**401**</span><span class="sxs-lookup"><span data-stu-id="a69d0-220">**401**</span></span> | <span data-ttu-id="a69d0-221">O aplicativo responde com um token inválido.</span><span class="sxs-lookup"><span data-stu-id="a69d0-221">The app responds with an invalid token.</span></span> |
| <span data-ttu-id="a69d0-222">**403**</span><span class="sxs-lookup"><span data-stu-id="a69d0-222">**403**</span></span> | <span data-ttu-id="a69d0-223">O aplicativo não consegue enviar o sinal.</span><span class="sxs-lookup"><span data-stu-id="a69d0-223">The app is unable to send the signal.</span></span> <span data-ttu-id="a69d0-224">Isso pode acontecer devido a vários motivos, como o administrador de locatários desabilita o aplicativo, o aplicativo é bloqueado durante a migração de site ao vivo e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="a69d0-224">This can happen due to various reasons such as the tenant admin disables the app, the app is blocked during live site migration, and so on.</span></span> <span data-ttu-id="a69d0-225">Nesse caso, a carga contém uma mensagem de erro detalhada.</span><span class="sxs-lookup"><span data-stu-id="a69d0-225">In this case, the payload contains a detailed error message.</span></span> |
| <span data-ttu-id="a69d0-226">**404**</span><span class="sxs-lookup"><span data-stu-id="a69d0-226">**404**</span></span> | <span data-ttu-id="a69d0-227">O chat de reunião não existe.</span><span class="sxs-lookup"><span data-stu-id="a69d0-227">The meeting chat does not exist.</span></span> |

## <a name="enable-your-app-for-teams-meetings"></a><span data-ttu-id="a69d0-228">Habilitar seu aplicativo para reuniões do Teams</span><span class="sxs-lookup"><span data-stu-id="a69d0-228">Enable your app for Teams meetings</span></span>

### <a name="update-your-app-manifest"></a><span data-ttu-id="a69d0-229">Atualizar o manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="a69d0-229">Update your app manifest</span></span>

<span data-ttu-id="a69d0-230">Os recursos do aplicativo de reuniões são declarados no manifesto do aplicativo usando `configurableTabs` `scopes` as matrizes , e `context` .</span><span class="sxs-lookup"><span data-stu-id="a69d0-230">The meetings app capabilities are declared in your app manifest using the `configurableTabs`, `scopes`, and `context` arrays.</span></span> <span data-ttu-id="a69d0-231">O escopo define a quem e o contexto define onde seu aplicativo está disponível.</span><span class="sxs-lookup"><span data-stu-id="a69d0-231">Scope defines to whom and context defines where your app is available.</span></span>

> [!NOTE]
> <span data-ttu-id="a69d0-232">Tente atualizar o manifesto do aplicativo com o [esquema de manifesto](../resources/schema/manifest-schema-dev-preview.md).</span><span class="sxs-lookup"><span data-stu-id="a69d0-232">Try updating your app manifest with the [manifest schema](../resources/schema/manifest-schema-dev-preview.md).</span></span>
> <span data-ttu-id="a69d0-233">Aplicativos em reuniões precisam *de escopo de groupchat.*</span><span class="sxs-lookup"><span data-stu-id="a69d0-233">Apps in meetings need *groupchat* scope.</span></span> <span data-ttu-id="a69d0-234">O *escopo da* equipe funciona apenas para guias em canais.</span><span class="sxs-lookup"><span data-stu-id="a69d0-234">The *team* scope works for tabs in channels only.</span></span>

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
> <span data-ttu-id="a69d0-235">`meetingStage` está disponível no momento apenas na visualização do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="a69d0-235">`meetingStage` is currently available in developer preview only.</span></span>

### <a name="context-property"></a><span data-ttu-id="a69d0-236">Propriedade Context</span><span class="sxs-lookup"><span data-stu-id="a69d0-236">Context property</span></span>

<span data-ttu-id="a69d0-237">A guia `context` e `scopes` as propriedades permitem determinar onde seu aplicativo deve aparecer.</span><span class="sxs-lookup"><span data-stu-id="a69d0-237">The tab `context` and `scopes` properties enable you to determine where your app must appear.</span></span> <span data-ttu-id="a69d0-238">Guias no `team` escopo ou podem `groupchat` ter mais de um contexto.</span><span class="sxs-lookup"><span data-stu-id="a69d0-238">Tabs in the `team` or `groupchat` scope can have more than one context.</span></span> <span data-ttu-id="a69d0-239">A seguir estão os valores da propriedade da qual você pode usar todos ou `context` alguns dos valores:</span><span class="sxs-lookup"><span data-stu-id="a69d0-239">Following are the values for the `context` property from which you can use all or some of the values:</span></span>

|<span data-ttu-id="a69d0-240">Valor</span><span class="sxs-lookup"><span data-stu-id="a69d0-240">Value</span></span>|<span data-ttu-id="a69d0-241">Descrição</span><span class="sxs-lookup"><span data-stu-id="a69d0-241">Description</span></span>|
|---|---|
| <span data-ttu-id="a69d0-242">**channelTab**</span><span class="sxs-lookup"><span data-stu-id="a69d0-242">**channelTab**</span></span> | <span data-ttu-id="a69d0-243">Uma guia no header de um canal de equipe.</span><span class="sxs-lookup"><span data-stu-id="a69d0-243">A tab in the header of a team channel.</span></span> |
| <span data-ttu-id="a69d0-244">**privateChatTab**</span><span class="sxs-lookup"><span data-stu-id="a69d0-244">**privateChatTab**</span></span> | <span data-ttu-id="a69d0-245">Uma guia no header de um chat de grupo entre um conjunto de usuários que não está no contexto de uma equipe ou reunião.</span><span class="sxs-lookup"><span data-stu-id="a69d0-245">A tab in the header of a group chat between a set of users not in the context of a team or meeting.</span></span> |
| <span data-ttu-id="a69d0-246">**meetingChatTab**</span><span class="sxs-lookup"><span data-stu-id="a69d0-246">**meetingChatTab**</span></span> | <span data-ttu-id="a69d0-247">Uma guia no header de um chat de grupo entre um conjunto de usuários no contexto de uma reunião agendada.</span><span class="sxs-lookup"><span data-stu-id="a69d0-247">A tab in the header of a group chat between a set of users in the context of a scheduled meeting.</span></span> |
| <span data-ttu-id="a69d0-248">**meetingDetailsTab**</span><span class="sxs-lookup"><span data-stu-id="a69d0-248">**meetingDetailsTab**</span></span> | <span data-ttu-id="a69d0-249">Uma guia no header da exibição de detalhes da reunião do calendário.</span><span class="sxs-lookup"><span data-stu-id="a69d0-249">A tab in the header of the meeting details view of the calendar.</span></span> |
| <span data-ttu-id="a69d0-250">**meetingSidePanel**</span><span class="sxs-lookup"><span data-stu-id="a69d0-250">**meetingSidePanel**</span></span> | <span data-ttu-id="a69d0-251">Um painel na reunião foi aberto por meio da barra unificada (U-bar).</span><span class="sxs-lookup"><span data-stu-id="a69d0-251">An in-meeting panel opened via the unified bar (U-bar).</span></span> |
| <span data-ttu-id="a69d0-252">**meetingStage**</span><span class="sxs-lookup"><span data-stu-id="a69d0-252">**meetingStage**</span></span> | <span data-ttu-id="a69d0-253">Um aplicativo do sidepanel pode ser compartilhado no estágio de reunião.</span><span class="sxs-lookup"><span data-stu-id="a69d0-253">An app from the sidepanel can be shared to the meeting stage.</span></span> |

> [!NOTE]
> <span data-ttu-id="a69d0-254">`Context` atualmente, não há suporte para clientes móveis.</span><span class="sxs-lookup"><span data-stu-id="a69d0-254">`Context` property is currently not supported on mobile clients.</span></span>

## <a name="configure-your-app-for-meeting-scenarios"></a><span data-ttu-id="a69d0-255">Configurar seu aplicativo para cenários de reunião</span><span class="sxs-lookup"><span data-stu-id="a69d0-255">Configure your app for meeting scenarios</span></span>

> [!NOTE]
> * <span data-ttu-id="a69d0-256">Para que seu aplicativo seja visível na galeria de guias, ele deve dar suporte a guias configuráveis e ao escopo de chat de grupo.</span><span class="sxs-lookup"><span data-stu-id="a69d0-256">For your app to be visible in the tab gallery it must support configurable tabs and the group chat scope.</span></span>
> * <span data-ttu-id="a69d0-257">Os clientes móveis suportam guias somente em estágios pré e pós-reunião.</span><span class="sxs-lookup"><span data-stu-id="a69d0-257">Mobile clients support tabs only in pre and post meeting stages.</span></span>
> * <span data-ttu-id="a69d0-258">As experiências na reunião que estão na caixa de diálogo e na guia da reunião atualmente não são suportadas em clientes móveis.</span><span class="sxs-lookup"><span data-stu-id="a69d0-258">The in-meeting experiences that is in-meeting dialog box and tab is currently not supported on mobile clients.</span></span> <span data-ttu-id="a69d0-259">Para obter mais informações, consulte [diretrizes para guias em dispositivos móveis](../tabs/design/tabs-mobile.md) ao criar suas guias para dispositivos móveis.</span><span class="sxs-lookup"><span data-stu-id="a69d0-259">For more information, see [guidance for tabs on mobile](../tabs/design/tabs-mobile.md) when creating your tabs for mobile.</span></span>

### <a name="before-a-meeting"></a><span data-ttu-id="a69d0-260">Antes de uma reunião</span><span class="sxs-lookup"><span data-stu-id="a69d0-260">Before a meeting</span></span>

<span data-ttu-id="a69d0-261">Antes de uma reunião, os usuários podem adicionar guias, bots e extensões de mensagens a uma reunião.</span><span class="sxs-lookup"><span data-stu-id="a69d0-261">Before a meeting, users can add tabs, bots and messaging extensions to a meeting.</span></span> <span data-ttu-id="a69d0-262">Os usuários com funções de organizador e apresentador podem adicionar guias a uma reunião.</span><span class="sxs-lookup"><span data-stu-id="a69d0-262">Users with organizer and presenter roles can add tabs to a meeting.</span></span>

<span data-ttu-id="a69d0-263">**Para adicionar uma guia a uma reunião**</span><span class="sxs-lookup"><span data-stu-id="a69d0-263">**To add a tab to a meeting**</span></span>

1. <span data-ttu-id="a69d0-264">Em seu calendário, selecione uma reunião à qual deseja adicionar uma guia.</span><span class="sxs-lookup"><span data-stu-id="a69d0-264">In your calendar, select a meeting to which you want to add a tab.</span></span>
1. <span data-ttu-id="a69d0-265">Selecione a **guia Detalhes** e selecione mais</span><span class="sxs-lookup"><span data-stu-id="a69d0-265">Select the **Details** tab and select plus</span></span> <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/><span data-ttu-id="a69d0-266">.</span><span class="sxs-lookup"><span data-stu-id="a69d0-266">.</span></span> <span data-ttu-id="a69d0-267">A galeria de guias é exibida.</span><span class="sxs-lookup"><span data-stu-id="a69d0-267">The tab gallery appears.</span></span>

    ![Experiência de pré-reunião](../assets/images/apps-in-meetings/PreMeeting.png)

1. <span data-ttu-id="a69d0-269">Na galeria de guias, selecione o aplicativo que você deseja adicionar e siga as etapas conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="a69d0-269">In the tab gallery, select the app that you want to add and follow the steps as required.</span></span> <span data-ttu-id="a69d0-270">O aplicativo é instalado como uma guia.</span><span class="sxs-lookup"><span data-stu-id="a69d0-270">The app is installed as a tab.</span></span>
    > [!NOTE] 
    > <span data-ttu-id="a69d0-271">Atualmente, na guia reuniões, não há suporte para obter detalhes da reunião e informações dos participantes.</span><span class="sxs-lookup"><span data-stu-id="a69d0-271">Currently, in meetings tab, getting meeting details and participant information is not supported.</span></span>

<span data-ttu-id="a69d0-272">**Para adicionar uma extensão de mensagens a uma reunião**</span><span class="sxs-lookup"><span data-stu-id="a69d0-272">**To add a messaging extension to a meeting**</span></span>

1. <span data-ttu-id="a69d0-273">Selecione as releições ou o menu de estouro &#x25CF;&#x25CF;&#x25CF; localizado na área de mensagem de redação no chat.</span><span class="sxs-lookup"><span data-stu-id="a69d0-273">Select the ellipses or overflow menu &#x25CF;&#x25CF;&#x25CF; located in the compose message area in the chat.</span></span>
1. <span data-ttu-id="a69d0-274">Selecione o aplicativo que você deseja adicionar e siga as etapas conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="a69d0-274">Select the app that you want to add and follow the steps as required.</span></span> <span data-ttu-id="a69d0-275">O aplicativo é instalado como uma extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="a69d0-275">The app is installed as a messaging extension.</span></span>

<span data-ttu-id="a69d0-276">**Para adicionar um bot a uma reunião**</span><span class="sxs-lookup"><span data-stu-id="a69d0-276">**To add a bot to a meeting**</span></span>

<span data-ttu-id="a69d0-277">Em um chat de reunião, insira **@** a chave e selecione Obter **bots**.</span><span class="sxs-lookup"><span data-stu-id="a69d0-277">In a meeting chat enter the **@** key and select **Get bots**.</span></span>

> [!NOTE]
> * <span data-ttu-id="a69d0-278">A identidade do usuário deve ser confirmada usando [Guias SSO](../tabs/how-to/authentication/auth-aad-sso.md).</span><span class="sxs-lookup"><span data-stu-id="a69d0-278">The user identity must be confirmed using [Tabs SSO](../tabs/how-to/authentication/auth-aad-sso.md).</span></span> <span data-ttu-id="a69d0-279">Após a autenticação, o aplicativo pode recuperar a função de usuário usando a `GetParticipant` API.</span><span class="sxs-lookup"><span data-stu-id="a69d0-279">After authentication, the app can retrieve the user role using the `GetParticipant` API.</span></span>
> * <span data-ttu-id="a69d0-280">Com base na função de usuário, o aplicativo tem a capacidade de fornecer experiências específicas de função.</span><span class="sxs-lookup"><span data-stu-id="a69d0-280">Based on the user role, the app has the capability to provide role specific experiences.</span></span> <span data-ttu-id="a69d0-281">Por exemplo, um aplicativo de sondagem permite que apenas organizadores e apresentadores criem uma nova sondagem.</span><span class="sxs-lookup"><span data-stu-id="a69d0-281">For example, a polling app allows only organizers and presenters to create a new poll.</span></span>
> * <span data-ttu-id="a69d0-282">As atribuições de função podem ser alteradas enquanto uma reunião está em andamento.</span><span class="sxs-lookup"><span data-stu-id="a69d0-282">Role assignments can be changed while a meeting is in progress.</span></span> <span data-ttu-id="a69d0-283">Para obter mais informações, [consulte funções em uma reunião do Teams](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span><span class="sxs-lookup"><span data-stu-id="a69d0-283">For more information, see [roles in a Teams meeting](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span></span>

### <a name="during-a-meeting"></a><span data-ttu-id="a69d0-284">Durante uma reunião</span><span class="sxs-lookup"><span data-stu-id="a69d0-284">During a meeting</span></span>

#### <a name="sidepanel"></a><span data-ttu-id="a69d0-285">sidePanel</span><span class="sxs-lookup"><span data-stu-id="a69d0-285">sidePanel</span></span>

<span data-ttu-id="a69d0-286">Com o sidePanel, você pode personalizar experiências em uma reunião que permitem que organizadores e apresentadores tenham diferentes tipos de exibição e ações.</span><span class="sxs-lookup"><span data-stu-id="a69d0-286">With the sidePanel, you can customize experiences in a meeting that enable organizers and presenters to have different set of views and actions.</span></span> <span data-ttu-id="a69d0-287">No manifesto do aplicativo, você deve adicionar sidePanel à matriz de contexto.</span><span class="sxs-lookup"><span data-stu-id="a69d0-287">In your app manifest, you must add sidePanel to the context array.</span></span> <span data-ttu-id="a69d0-288">Na reunião e em todos os cenários, o aplicativo é renderizado em uma guia na reunião que tem 320 pixels de largura.</span><span class="sxs-lookup"><span data-stu-id="a69d0-288">In the meeting and in all scenarios, the app is rendered in an in-meeting tab that is 320 pixels in width.</span></span> <span data-ttu-id="a69d0-289">Para obter mais informações, consulte [Interface FrameContext](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/framecontext?view=msteams-client-js-latest&preserve-view=true
).</span><span class="sxs-lookup"><span data-stu-id="a69d0-289">For more information, see [FrameContext interface](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/framecontext?view=msteams-client-js-latest&preserve-view=true
).</span></span>

<span data-ttu-id="a69d0-290">Para usar a `userContext` API para rotear solicitações de acordo, consulte [Teams SDK](../tabs/how-to/access-teams-context.md#user-context).</span><span class="sxs-lookup"><span data-stu-id="a69d0-290">To use the `userContext` API to route requests accordingly, see [Teams SDK](../tabs/how-to/access-teams-context.md#user-context).</span></span> <span data-ttu-id="a69d0-291">Consulte [Fluxo de autenticação do Teams para guias](../tabs/how-to/authentication/auth-flow-tab.md).</span><span class="sxs-lookup"><span data-stu-id="a69d0-291">See [Teams authentication flow for tabs](../tabs/how-to/authentication/auth-flow-tab.md).</span></span> <span data-ttu-id="a69d0-292">O fluxo de autenticação para guias é muito semelhante ao fluxo de autenticação para sites.</span><span class="sxs-lookup"><span data-stu-id="a69d0-292">Authentication flow for tabs is very similar to the auth flow for websites.</span></span> <span data-ttu-id="a69d0-293">Portanto, as guias podem usar o OAuth 2.0 diretamente.</span><span class="sxs-lookup"><span data-stu-id="a69d0-293">So tabs can use OAuth 2.0 directly.</span></span> <span data-ttu-id="a69d0-294">Consulte a plataforma de identidade da Microsoft e o fluxo de código de autorização do [OAuth 2.0.](/azure/active-directory/develop/v2-oauth2-auth-code-flow)</span><span class="sxs-lookup"><span data-stu-id="a69d0-294">See, [Microsoft identity platform and OAuth 2.0 authorization code flow](/azure/active-directory/develop/v2-oauth2-auth-code-flow).</span></span>

<span data-ttu-id="a69d0-295">A extensão de mensagens funciona conforme o esperado quando um usuário está em uma exibição em reunião e o usuário pode postar cartões de extensão de mensagem de composição.</span><span class="sxs-lookup"><span data-stu-id="a69d0-295">Messaging extension works as expected when a user is in an in-meeting view and the user can post compose message extension cards.</span></span> <span data-ttu-id="a69d0-296">AppName in-meeting é uma dica de ferramenta que informa o nome do aplicativo na U-bar de reunião.</span><span class="sxs-lookup"><span data-stu-id="a69d0-296">AppName in-meeting is a tooltip that states the app name in-meeting U-bar.</span></span>

> [!NOTE]
> <span data-ttu-id="a69d0-297">Use a versão 1.7.0 ou superior do [SDK](https://docs.microsoft.com/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)do Teams, pois as versões anteriores a ele não suportam o painel lateral.</span><span class="sxs-lookup"><span data-stu-id="a69d0-297">Use version 1.7.0 or higher of [Teams SDK](https://docs.microsoft.com/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true), as versions prior to it do not support the side panel.</span></span>

#### <a name="in-meeting-dialog"></a><span data-ttu-id="a69d0-298">Caixa de diálogo na reunião</span><span class="sxs-lookup"><span data-stu-id="a69d0-298">In-meeting dialog</span></span>

<span data-ttu-id="a69d0-299">A caixa de diálogo na reunião pode ser usada para envolver os participantes durante a reunião e coletar informações ou comentários durante a reunião.</span><span class="sxs-lookup"><span data-stu-id="a69d0-299">The in-meeting dialog box can be used to engage participants during the meeting and collect information or feedback during the meeting.</span></span> <span data-ttu-id="a69d0-300">Use a [`NotificationSignal`](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) API para sinalizar que uma notificação de bolha deve ser disparada.</span><span class="sxs-lookup"><span data-stu-id="a69d0-300">Use the [`NotificationSignal`](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) API to signal that a bubble notification must be triggered.</span></span> <span data-ttu-id="a69d0-301">Como parte da carga da solicitação de notificação, inclua a URL onde o conteúdo a ser mostrado está hospedado.</span><span class="sxs-lookup"><span data-stu-id="a69d0-301">As part of the notification request payload, include the URL where the content to be shown is hosted.</span></span>

<span data-ttu-id="a69d0-302">A caixa de diálogo na reunião não deve usar o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="a69d0-302">In-meeting dialog must not use task module.</span></span> <span data-ttu-id="a69d0-303">O módulo de tarefa não é invocado em um chat de reunião.</span><span class="sxs-lookup"><span data-stu-id="a69d0-303">Task module is not invoked in a meeting chat.</span></span> <span data-ttu-id="a69d0-304">Uma URL de recurso externo é usada para exibir a bolha de conteúdo em uma reunião.</span><span class="sxs-lookup"><span data-stu-id="a69d0-304">An external resource URL is used to display content bubble in a meeting.</span></span> <span data-ttu-id="a69d0-305">Você pode usar o `submitTask` método para enviar dados em um chat de reunião.</span><span class="sxs-lookup"><span data-stu-id="a69d0-305">You can use the `submitTask` method to submit data in a meeting chat.</span></span>

> [!NOTE]
> * <span data-ttu-id="a69d0-306">Você deve invocar [a função submitTask()](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) para descartar automaticamente depois que um usuário realizar uma ação no web-view.</span><span class="sxs-lookup"><span data-stu-id="a69d0-306">You must invoke the [submitTask()](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) function to dismiss automatically after a user takes an action in the web-view.</span></span> <span data-ttu-id="a69d0-307">Esse é um requisito para envio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a69d0-307">This is a requirement for app submission.</span></span> <span data-ttu-id="a69d0-308">Para obter mais informações, consulte [Módulo de tarefas do SDK do Teams.](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="a69d0-308">For more information, see [Teams SDK task module](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).</span></span>
> * <span data-ttu-id="a69d0-309">Se você quiser que seu aplicativo suporte usuários anônimos, sua carga inicial de solicitação de invocação deve depender dos metadados de solicitação no objeto, não `from.id` `from` nos `from.aadObjectId` metadados de solicitação.</span><span class="sxs-lookup"><span data-stu-id="a69d0-309">If you want your app to support anonymous users, your initial invoke request payload must rely on the `from.id` request metadata in the `from` object, not the `from.aadObjectId` request metadata.</span></span> <span data-ttu-id="a69d0-310">`from.id` é a ID do usuário e é a ID do `from.aadObjectId` Azure Active Directory (AAD) do usuário.</span><span class="sxs-lookup"><span data-stu-id="a69d0-310">`from.id` is the user ID and `from.aadObjectId` is the Azure Active Directory (AAD) ID of the user.</span></span> <span data-ttu-id="a69d0-311">Para obter mais informações, [consulte using task modules in tabs](../task-modules-and-cards/task-modules/task-modules-tabs.md) e [create and send the task module](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).</span><span class="sxs-lookup"><span data-stu-id="a69d0-311">For more information, see [using task modules in tabs](../task-modules-and-cards/task-modules/task-modules-tabs.md) and [create and send the task module](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).</span></span>

#### <a name="share-to-stage"></a><span data-ttu-id="a69d0-312">Compartilhar em estágio</span><span class="sxs-lookup"><span data-stu-id="a69d0-312">Share to stage</span></span> 

> [!NOTE]
> * <span data-ttu-id="a69d0-313">Esse recurso está disponível apenas na visualização do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="a69d0-313">This capability is currently available in developer preview only.</span></span>
> * <span data-ttu-id="a69d0-314">Para usar esse recurso, o aplicativo deve dar suporte a um sidepanel na reunião.</span><span class="sxs-lookup"><span data-stu-id="a69d0-314">To use this feature, the app must support an in-meeting sidepanel.</span></span>


<span data-ttu-id="a69d0-315">Esse recurso oferece aos desenvolvedores a capacidade de compartilhar um aplicativo no estágio de reunião.</span><span class="sxs-lookup"><span data-stu-id="a69d0-315">This capability gives developers the ability to share an app to the meeting stage.</span></span> <span data-ttu-id="a69d0-316">Habilitando o compartilhamento para o estágio de reunião, os participantes da reunião podem colaborar em tempo real.</span><span class="sxs-lookup"><span data-stu-id="a69d0-316">By enabling share to the meeting stage, meeting participants can collaborate in real-time.</span></span> 

<span data-ttu-id="a69d0-317">O contexto necessário está `meetingStage` no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a69d0-317">The required context is `meetingStage` in the app manifest.</span></span> <span data-ttu-id="a69d0-318">Um pré-requisito para isso é ter o `meetingSidePanel` contexto.</span><span class="sxs-lookup"><span data-stu-id="a69d0-318">A prerequisite for this is to have the `meetingSidePanel` context.</span></span> <span data-ttu-id="a69d0-319">Isso habilita **o botão Compartilhar** no sidepanel conforme solicitado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="a69d0-319">This enables the **Share** button in the sidepanel as depecited in the following image:</span></span>

  ![share_to_stage_during_meeting experiência](~/assets/images/apps-in-meetings/share_to_stage_during_meeting.png)

<span data-ttu-id="a69d0-321">A alteração de manifesto necessária para habilitar esse recurso é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="a69d0-321">The manifest change that is needed to enable this capability is as follows:</span></span> 

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



### <a name="after-a-meeting"></a><span data-ttu-id="a69d0-322">Após uma reunião</span><span class="sxs-lookup"><span data-stu-id="a69d0-322">After a meeting</span></span>

<span data-ttu-id="a69d0-323">As configurações pós-reunião e pré-reunião são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="a69d0-323">The post-meeting and pre-meeting configurations are equivalent.</span></span>

## <a name="code-sample"></a><span data-ttu-id="a69d0-324">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="a69d0-324">Code sample</span></span>

|<span data-ttu-id="a69d0-325">Exemplo de nome</span><span class="sxs-lookup"><span data-stu-id="a69d0-325">Sample name</span></span> | <span data-ttu-id="a69d0-326">Descrição</span><span class="sxs-lookup"><span data-stu-id="a69d0-326">Description</span></span> | <span data-ttu-id="a69d0-327">.NET</span><span class="sxs-lookup"><span data-stu-id="a69d0-327">.NET</span></span> | <span data-ttu-id="a69d0-328">Node.js</span><span class="sxs-lookup"><span data-stu-id="a69d0-328">Node.js</span></span> |
|----------------|-----------------|--------------|--------------|
| <span data-ttu-id="a69d0-329">Extensibilidade de reuniões</span><span class="sxs-lookup"><span data-stu-id="a69d0-329">Meetings extensibility</span></span> | <span data-ttu-id="a69d0-330">Exemplo de extensibilidade de reunião do Microsoft Teams para tokens de passagem.</span><span class="sxs-lookup"><span data-stu-id="a69d0-330">Microsoft Teams meeting extensibility sample for passing tokens.</span></span> | [<span data-ttu-id="a69d0-331">View</span><span class="sxs-lookup"><span data-stu-id="a69d0-331">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) | |
| <span data-ttu-id="a69d0-332">Bot de bolha de conteúdo de reunião</span><span class="sxs-lookup"><span data-stu-id="a69d0-332">Meeting content bubble bot</span></span> | <span data-ttu-id="a69d0-333">Exemplo de extensibilidade de reunião do Microsoft Teams para interagir com o bot de bolha de conteúdo em uma reunião.</span><span class="sxs-lookup"><span data-stu-id="a69d0-333">Microsoft Teams meeting extensibility sample for interacting with content bubble bot in a meeting.</span></span> | [<span data-ttu-id="a69d0-334">View</span><span class="sxs-lookup"><span data-stu-id="a69d0-334">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/csharp) |  [<span data-ttu-id="a69d0-335">View</span><span class="sxs-lookup"><span data-stu-id="a69d0-335">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/nodejs)|

## <a name="see-also"></a><span data-ttu-id="a69d0-336">Confira também</span><span class="sxs-lookup"><span data-stu-id="a69d0-336">See also</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a69d0-337">Diretrizes de design de caixa de diálogo na reunião</span><span class="sxs-lookup"><span data-stu-id="a69d0-337">In-meeting dialog design guidelines</span></span>](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
> [!div class="nextstepaction"]
> [<span data-ttu-id="a69d0-338">Fluxo de autenticação do Teams para guias</span><span class="sxs-lookup"><span data-stu-id="a69d0-338">Teams authentication flow for tabs</span></span>](../tabs/how-to/authentication/auth-flow-tab.md)
