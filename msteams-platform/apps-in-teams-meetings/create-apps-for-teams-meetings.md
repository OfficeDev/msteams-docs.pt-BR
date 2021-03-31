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
# <a name="create-apps-for-teams-meetings"></a><span data-ttu-id="783b9-104">Crie aplicativos para reuniões do Teams</span><span class="sxs-lookup"><span data-stu-id="783b9-104">Create apps for Teams meetings</span></span>

## <a name="prerequisites-and-considerations"></a><span data-ttu-id="783b9-105">Pré-requisitos e considerações</span><span class="sxs-lookup"><span data-stu-id="783b9-105">Prerequisites and considerations</span></span>

<span data-ttu-id="783b9-106">Antes de criar aplicativos para reuniões do Teams, você deve ter uma compreensão do seguinte:</span><span class="sxs-lookup"><span data-stu-id="783b9-106">Before you create apps for Teams meetings, you must have an understanding of the following:</span></span>

* <span data-ttu-id="783b9-107">Você deve ter conhecimento de como desenvolver aplicativos do Teams.</span><span class="sxs-lookup"><span data-stu-id="783b9-107">You must have knowledge of how to develop Teams apps.</span></span> <span data-ttu-id="783b9-108">Para obter mais informações, consulte [Desenvolvimento de aplicativos do Teams](../overview.md).</span><span class="sxs-lookup"><span data-stu-id="783b9-108">For more information, see [Teams app development](../overview.md).</span></span>

* <span data-ttu-id="783b9-109">Você deve atualizar o manifesto do aplicativo do Teams para indicar que o aplicativo está disponível para reuniões.</span><span class="sxs-lookup"><span data-stu-id="783b9-109">You must update the Teams app manifest to indicate that the app is available for meetings.</span></span> <span data-ttu-id="783b9-110">Para obter mais informações, consulte [manifesto do aplicativo](#update-your-app-manifest).</span><span class="sxs-lookup"><span data-stu-id="783b9-110">For more information, see [app manifest](#update-your-app-manifest).</span></span>

* <span data-ttu-id="783b9-111">Para que seu aplicativo funcione no ciclo de vida da reunião como uma guia, ele deve dar suporte a guias configuráveis no escopo de groupchat.</span><span class="sxs-lookup"><span data-stu-id="783b9-111">For your app to function in the meeting lifecycle as a tab, it must support configurable tabs in the groupchat scope.</span></span> <span data-ttu-id="783b9-112">Para obter mais informações, consulte [groupchat scope](../resources/schema/manifest-schema.md#configurabletabs) and [build a group tab](../build-your-first-app/build-channel-tab.md).</span><span class="sxs-lookup"><span data-stu-id="783b9-112">For more information, see [groupchat scope](../resources/schema/manifest-schema.md#configurabletabs) and [build a group tab](../build-your-first-app/build-channel-tab.md).</span></span>

* <span data-ttu-id="783b9-113">Você deve seguir as diretrizes gerais de design de guia do Teams para cenários pré e pós-reunião.</span><span class="sxs-lookup"><span data-stu-id="783b9-113">You must adhere to general Teams tab design guidelines for pre- and post-meeting scenarios.</span></span> <span data-ttu-id="783b9-114">Para experiências durante as reuniões, consulte a guia na reunião e as diretrizes de design da caixa de diálogo na reunião.</span><span class="sxs-lookup"><span data-stu-id="783b9-114">For experiences during meetings, refer to the in-meeting tab and in-meeting dialog design guidelines.</span></span> <span data-ttu-id="783b9-115">Para obter mais informações, consulte Diretrizes de design de [guia do Teams,](../tabs/design/tabs.md)diretrizes de [design](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab) da guia de reunião e diretrizes de design de caixa de diálogo [na reunião.](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)</span><span class="sxs-lookup"><span data-stu-id="783b9-115">For more information, see [Teams tab design guidelines](../tabs/design/tabs.md), [in-meeting tab design guidelines](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab) and [in-meeting dialog design guidelines](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog).</span></span>

* <span data-ttu-id="783b9-116">Você deve dar suporte ao escopo para habilitar seu aplicativo em chats de `groupchat` pré-reunião e pós-reunião.</span><span class="sxs-lookup"><span data-stu-id="783b9-116">You must support the `groupchat` scope to enable your app in pre-meeting and post-meeting chats.</span></span> <span data-ttu-id="783b9-117">Com a experiência do aplicativo de pré-reunião, você pode encontrar e adicionar aplicativos de reunião e realizar tarefas de pré-reunião.</span><span class="sxs-lookup"><span data-stu-id="783b9-117">With the pre-meeting app experience, you can find and add meeting apps and perform pre-meeting tasks.</span></span> <span data-ttu-id="783b9-118">Com a experiência do aplicativo pós-reunião, você pode exibir os resultados da reunião, como resultados da pesquisa ou comentários.</span><span class="sxs-lookup"><span data-stu-id="783b9-118">With post-meeting app experience, you can view the results of the meeting, such as poll survey results or feedback.</span></span>

* <span data-ttu-id="783b9-119">Os parâmetros de URL da API de reunião `meetingId` devem ter , e `userId` `tenantId` .</span><span class="sxs-lookup"><span data-stu-id="783b9-119">Meeting API URL parameters must have `meetingId`, `userId`, and `tenantId`.</span></span> <span data-ttu-id="783b9-120">Eles estão disponíveis como parte da atividade de SDK e bot do cliente do Teams.</span><span class="sxs-lookup"><span data-stu-id="783b9-120">These are available as part of the Teams client SDK and bot activity.</span></span> <span data-ttu-id="783b9-121">Além disso, informações confiáveis para iD de usuário e ID de locatário podem ser recuperadas usando [a autenticação tab SSO](../tabs/how-to/authentication/auth-aad-sso.md).</span><span class="sxs-lookup"><span data-stu-id="783b9-121">In addition, reliable information for user ID and tenant ID can be retrieved using [Tab SSO authentication](../tabs/how-to/authentication/auth-aad-sso.md).</span></span>

* <span data-ttu-id="783b9-122">A `GetParticipant` API deve ter um registro de bot e uma ID para gerar tokens de auth.</span><span class="sxs-lookup"><span data-stu-id="783b9-122">The `GetParticipant` API must have a bot registration and ID to generate auth tokens.</span></span> <span data-ttu-id="783b9-123">Para obter mais informações, [consulte registro de bot e ID](../build-your-first-app/build-bot.md).</span><span class="sxs-lookup"><span data-stu-id="783b9-123">For more information, see [bot registration and ID](../build-your-first-app/build-bot.md).</span></span>

* <span data-ttu-id="783b9-124">Para que seu aplicativo seja atualizado em tempo real, ele deve estar atualizado com base nas atividades do evento na reunião.</span><span class="sxs-lookup"><span data-stu-id="783b9-124">For your app to update in real time, it must be up-to-date based on event activities in the meeting.</span></span> <span data-ttu-id="783b9-125">Esses eventos podem estar dentro da caixa de diálogo na reunião e em outros estágios no ciclo de vida da reunião.</span><span class="sxs-lookup"><span data-stu-id="783b9-125">These events can be within the in-meeting dialog box and other stages across the meeting lifecycle.</span></span> <span data-ttu-id="783b9-126">Para a caixa de diálogo na reunião, consulte o parâmetro completion `bot Id` em `Notification Signal API` .</span><span class="sxs-lookup"><span data-stu-id="783b9-126">For the in-meeting dialog box, see completion `bot Id` parameter in `Notification Signal API`.</span></span>

## <a name="meeting-apps-api-reference"></a><span data-ttu-id="783b9-127">Referência da API de aplicativos de reunião</span><span class="sxs-lookup"><span data-stu-id="783b9-127">Meeting apps API reference</span></span>

|<span data-ttu-id="783b9-128">API</span><span class="sxs-lookup"><span data-stu-id="783b9-128">API</span></span>|<span data-ttu-id="783b9-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="783b9-129">Description</span></span>|<span data-ttu-id="783b9-130">Solicitação</span><span class="sxs-lookup"><span data-stu-id="783b9-130">Request</span></span>|<span data-ttu-id="783b9-131">Origem</span><span class="sxs-lookup"><span data-stu-id="783b9-131">Source</span></span>|
|---|---|----|---|
|<span data-ttu-id="783b9-132">**GetUserContext**</span><span class="sxs-lookup"><span data-stu-id="783b9-132">**GetUserContext**</span></span>| <span data-ttu-id="783b9-133">Essa API permite que você receba informações contextuais para exibir conteúdo relevante em uma guia do Teams.</span><span class="sxs-lookup"><span data-stu-id="783b9-133">This API enables you to get contextual information to display relevant content in a Teams tab.</span></span> |<span data-ttu-id="783b9-134">_**microsoftTeams.getContext( ( ) => { /*...\* / } )*\*_</span><span class="sxs-lookup"><span data-stu-id="783b9-134">_**microsoftTeams.getContext( ( ) => {  /*...*/ } )**_</span></span>|<span data-ttu-id="783b9-135">SDK de cliente do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="783b9-135">Microsoft Teams client SDK</span></span>|
|<span data-ttu-id="783b9-136">**GetParticipant**</span><span class="sxs-lookup"><span data-stu-id="783b9-136">**GetParticipant**</span></span>| <span data-ttu-id="783b9-137">Essa API permite que um bot busque informações dos participantes por meio da ID da reunião e da ID do participante.</span><span class="sxs-lookup"><span data-stu-id="783b9-137">This API allows a bot to fetch participant information by meeting ID and participant ID.</span></span> |<span data-ttu-id="783b9-138">**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_</span><span class="sxs-lookup"><span data-stu-id="783b9-138">**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_</span></span> |<span data-ttu-id="783b9-139">Microsoft Bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="783b9-139">Microsoft Bot Framework SDK</span></span>|
|<span data-ttu-id="783b9-140">**NotificationSignal**</span><span class="sxs-lookup"><span data-stu-id="783b9-140">**NotificationSignal**</span></span> | <span data-ttu-id="783b9-141">Essa API permite que você forneça sinais de reunião que são entregues usando a API de notificação de conversa existente para chat de usuário-bot.</span><span class="sxs-lookup"><span data-stu-id="783b9-141">This API enables you to provide meeting signals that are delivered using the existing conversation notification API for user-bot chat.</span></span> <span data-ttu-id="783b9-142">Ele permite sinalizar com base na ação do usuário que mostra uma caixa de diálogo na reunião.</span><span class="sxs-lookup"><span data-stu-id="783b9-142">It allows you to signal based on user action that shows an in-meeting dialog box.</span></span> |<span data-ttu-id="783b9-143">**POST** _**/v3/conversations/{conversationId}/activities**_</span><span class="sxs-lookup"><span data-stu-id="783b9-143">**POST** _**/v3/conversations/{conversationId}/activities**_</span></span>|<span data-ttu-id="783b9-144">Microsoft Bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="783b9-144">Microsoft Bot Framework SDK</span></span>|

### <a name="getusercontext"></a><span data-ttu-id="783b9-145">GetUserContext</span><span class="sxs-lookup"><span data-stu-id="783b9-145">GetUserContext</span></span>

<span data-ttu-id="783b9-146">Para identificar e recuperar informações contextuais para o conteúdo da guia, consulte [obter contexto para a guia Do Teams.](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library) `meetingId` é usado por uma guia ao ser executado no contexto da reunião e é adicionado para a carga de resposta.</span><span class="sxs-lookup"><span data-stu-id="783b9-146">To identify and retrieve contextual information for your tab content, see [get context for your Teams tab](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library). `meetingId` is used by a tab when running in the meeting context and is added for the response payload.</span></span>

### <a name="getparticipant-api"></a><span data-ttu-id="783b9-147">GetParticipant API</span><span class="sxs-lookup"><span data-stu-id="783b9-147">GetParticipant API</span></span>

> [!NOTE]
> * <span data-ttu-id="783b9-148">Não armazenar em cache as funções do participante, pois o organizador da reunião pode alterar uma função a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="783b9-148">Do not cache participant roles since the meeting organizer can change a role any time.</span></span>
> * <span data-ttu-id="783b9-149">No momento, o Teams não dá suporte a grandes listas de distribuição ou tamanhos de lista de mais de 350 participantes para a `GetParticipant` API.</span><span class="sxs-lookup"><span data-stu-id="783b9-149">Teams does not currently support large distribution lists or roster sizes of more than 350 participants for the `GetParticipant` API.</span></span>

#### <a name="query-parameters"></a><span data-ttu-id="783b9-150">Parâmetros de consulta</span><span class="sxs-lookup"><span data-stu-id="783b9-150">Query parameters</span></span>

|<span data-ttu-id="783b9-151">Valor</span><span class="sxs-lookup"><span data-stu-id="783b9-151">Value</span></span>|<span data-ttu-id="783b9-152">Tipo</span><span class="sxs-lookup"><span data-stu-id="783b9-152">Type</span></span>|<span data-ttu-id="783b9-153">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="783b9-153">Required</span></span>|<span data-ttu-id="783b9-154">Descrição</span><span class="sxs-lookup"><span data-stu-id="783b9-154">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="783b9-155">**meetingId**</span><span class="sxs-lookup"><span data-stu-id="783b9-155">**meetingId**</span></span>| <span data-ttu-id="783b9-156">string</span><span class="sxs-lookup"><span data-stu-id="783b9-156">string</span></span> | <span data-ttu-id="783b9-157">Sim</span><span class="sxs-lookup"><span data-stu-id="783b9-157">Yes</span></span> | <span data-ttu-id="783b9-158">O identificador de reunião está disponível por meio do Bot Invoke e do SDK do Cliente do Teams.</span><span class="sxs-lookup"><span data-stu-id="783b9-158">The meeting identifier is available through Bot Invoke and Teams Client SDK.</span></span>|
|<span data-ttu-id="783b9-159">**participantId**</span><span class="sxs-lookup"><span data-stu-id="783b9-159">**participantId**</span></span>| <span data-ttu-id="783b9-160">string</span><span class="sxs-lookup"><span data-stu-id="783b9-160">string</span></span> | <span data-ttu-id="783b9-161">Sim</span><span class="sxs-lookup"><span data-stu-id="783b9-161">Yes</span></span> | <span data-ttu-id="783b9-162">A ID do participante é a ID do usuário.</span><span class="sxs-lookup"><span data-stu-id="783b9-162">The participant ID is the user ID.</span></span> <span data-ttu-id="783b9-163">Ele está disponível em Tab SSO, Bot Invoke e Teams Client SDK.</span><span class="sxs-lookup"><span data-stu-id="783b9-163">It is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="783b9-164">É recomendável obter uma ID do participante no SSO da guia.</span><span class="sxs-lookup"><span data-stu-id="783b9-164">It is recommended to get a participant ID from the Tab SSO.</span></span> |
|<span data-ttu-id="783b9-165">**tenantId**</span><span class="sxs-lookup"><span data-stu-id="783b9-165">**tenantId**</span></span>| <span data-ttu-id="783b9-166">string</span><span class="sxs-lookup"><span data-stu-id="783b9-166">string</span></span> | <span data-ttu-id="783b9-167">Sim</span><span class="sxs-lookup"><span data-stu-id="783b9-167">Yes</span></span> | <span data-ttu-id="783b9-168">A ID do locatário é necessária para os usuários do locatário.</span><span class="sxs-lookup"><span data-stu-id="783b9-168">The tenant ID is required for the tenant users.</span></span> <span data-ttu-id="783b9-169">Ele está disponível em Tab SSO, Bot Invoke e Teams Client SDK.</span><span class="sxs-lookup"><span data-stu-id="783b9-169">It is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="783b9-170">É recomendável obter uma ID de locatário do SSO de tabulação.</span><span class="sxs-lookup"><span data-stu-id="783b9-170">It is recommended to get a tenant ID from the Tab SSO.</span></span> |

#### <a name="example"></a><span data-ttu-id="783b9-171">Exemplo</span><span class="sxs-lookup"><span data-stu-id="783b9-171">Example</span></span>

# <a name="c"></a>[<span data-ttu-id="783b9-172">C#</span><span class="sxs-lookup"><span data-stu-id="783b9-172">C#</span></span>](#tab/dotnet)

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

# <a name="javascript"></a>[<span data-ttu-id="783b9-173">JavaScript</span><span class="sxs-lookup"><span data-stu-id="783b9-173">JavaScript</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="783b9-174">JSON</span><span class="sxs-lookup"><span data-stu-id="783b9-174">JSON</span></span>](#tab/json)

```http
GET /v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}
```

* * *

<span data-ttu-id="783b9-175">O corpo de resposta JSON para `GetParticipant` API é:</span><span class="sxs-lookup"><span data-stu-id="783b9-175">The JSON response body for `GetParticipant` API is:</span></span>

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

#### <a name="response-codes"></a><span data-ttu-id="783b9-176">Códigos de resposta</span><span class="sxs-lookup"><span data-stu-id="783b9-176">Response codes</span></span>

|<span data-ttu-id="783b9-177">Código da resposta</span><span class="sxs-lookup"><span data-stu-id="783b9-177">Response code</span></span>|<span data-ttu-id="783b9-178">Descrição</span><span class="sxs-lookup"><span data-stu-id="783b9-178">Description</span></span>|
|---|---|
| <span data-ttu-id="783b9-179">**403**</span><span class="sxs-lookup"><span data-stu-id="783b9-179">**403**</span></span> | <span data-ttu-id="783b9-180">O aplicativo não tem permissão para obter informações do participante.</span><span class="sxs-lookup"><span data-stu-id="783b9-180">The app is not allowed to get participant information.</span></span> <span data-ttu-id="783b9-181">Essa é a resposta de erro mais comum e é disparada se o aplicativo não estiver instalado na reunião.</span><span class="sxs-lookup"><span data-stu-id="783b9-181">This is the most common error response and is triggered if the app is not installed in the meeting.</span></span> <span data-ttu-id="783b9-182">Por exemplo, se o aplicativo for desabilitado pelo administrador do locatário ou bloqueado durante a migração do site ao vivo.</span><span class="sxs-lookup"><span data-stu-id="783b9-182">For example, if the app is disabled by tenant admin or blocked during live site migration.</span></span>|
| <span data-ttu-id="783b9-183">**200**</span><span class="sxs-lookup"><span data-stu-id="783b9-183">**200**</span></span> | <span data-ttu-id="783b9-184">As informações do participante são recuperadas com êxito.</span><span class="sxs-lookup"><span data-stu-id="783b9-184">The participant information is successfully retrieved.</span></span>|
| <span data-ttu-id="783b9-185">**401**</span><span class="sxs-lookup"><span data-stu-id="783b9-185">**401**</span></span> | <span data-ttu-id="783b9-186">O aplicativo responde com um token inválido.</span><span class="sxs-lookup"><span data-stu-id="783b9-186">The app responds with an invalid token.</span></span>|
| <span data-ttu-id="783b9-187">**404**</span><span class="sxs-lookup"><span data-stu-id="783b9-187">**404**</span></span> | <span data-ttu-id="783b9-188">A reunião expirou ou o participante não pode ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="783b9-188">The meeting has either expired or participant cannot be found.</span></span>|
| <span data-ttu-id="783b9-189">**500**</span><span class="sxs-lookup"><span data-stu-id="783b9-189">**500**</span></span> | <span data-ttu-id="783b9-190">A reunião expirou mais de 60 dias desde que a reunião terminou ou o participante não tem permissões com base em sua função.</span><span class="sxs-lookup"><span data-stu-id="783b9-190">The meeting has either expired more than 60 days since the meeting ended or the participant does not have permissions based on their role.</span></span>|

### <a name="notificationsignal-api"></a><span data-ttu-id="783b9-191">NotificationSignal API</span><span class="sxs-lookup"><span data-stu-id="783b9-191">NotificationSignal API</span></span>

<span data-ttu-id="783b9-192">Todos os usuários em uma reunião recebem as notificações enviadas por meio da `NotificationSignal` API.</span><span class="sxs-lookup"><span data-stu-id="783b9-192">All users in a meeting receive the notifications sent through the `NotificationSignal` API.</span></span>

> [!NOTE]
> * <span data-ttu-id="783b9-193">Quando uma caixa de diálogo na reunião é invocada, o conteúdo é apresentado como uma mensagem de chat.</span><span class="sxs-lookup"><span data-stu-id="783b9-193">When an in-meeting dialog box is invoked, the content is presented as a chat message.</span></span>
> * <span data-ttu-id="783b9-194">Atualmente, não há suporte para o envio de notificações direcionadas.</span><span class="sxs-lookup"><span data-stu-id="783b9-194">Currently, sending targeted notifications is not supported.</span></span>

#### <a name="query-parameters"></a><span data-ttu-id="783b9-195">Parâmetros de consulta</span><span class="sxs-lookup"><span data-stu-id="783b9-195">Query parameters</span></span>

|<span data-ttu-id="783b9-196">Valor</span><span class="sxs-lookup"><span data-stu-id="783b9-196">Value</span></span>|<span data-ttu-id="783b9-197">Tipo</span><span class="sxs-lookup"><span data-stu-id="783b9-197">Type</span></span>|<span data-ttu-id="783b9-198">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="783b9-198">Required</span></span>|<span data-ttu-id="783b9-199">Descrição</span><span class="sxs-lookup"><span data-stu-id="783b9-199">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="783b9-200">**conversationId**</span><span class="sxs-lookup"><span data-stu-id="783b9-200">**conversationId**</span></span>| <span data-ttu-id="783b9-201">string</span><span class="sxs-lookup"><span data-stu-id="783b9-201">string</span></span> | <span data-ttu-id="783b9-202">Sim</span><span class="sxs-lookup"><span data-stu-id="783b9-202">Yes</span></span> | <span data-ttu-id="783b9-203">O identificador de conversa está disponível como parte da invocação de bot</span><span class="sxs-lookup"><span data-stu-id="783b9-203">The conversation identifier is available as part of bot invoke</span></span> |

#### <a name="example"></a><span data-ttu-id="783b9-204">Exemplo</span><span class="sxs-lookup"><span data-stu-id="783b9-204">Example</span></span>

<span data-ttu-id="783b9-205">O `Bot ID` é declarado no manifesto e o bot recebe um objeto de resultado.</span><span class="sxs-lookup"><span data-stu-id="783b9-205">The `Bot ID` is declared in the manifest and the bot receives a result object.</span></span>

> [!NOTE]
> * <span data-ttu-id="783b9-206">O `completionBotId` parâmetro do é opcional no exemplo de carga `externalResourceUrl` solicitada.</span><span class="sxs-lookup"><span data-stu-id="783b9-206">The `completionBotId` parameter of the `externalResourceUrl` is optional in the requested payload example.</span></span> <span data-ttu-id="783b9-207">`Bot ID` é declarado no manifesto e o bot recebe um objeto de resultado.</span><span class="sxs-lookup"><span data-stu-id="783b9-207">`Bot ID` is declared in the manifest and the bot receives a result object.</span></span>
> * <span data-ttu-id="783b9-208">Os `externalResourceUrl` parâmetros de largura e altura devem estar em pixels.</span><span class="sxs-lookup"><span data-stu-id="783b9-208">The `externalResourceUrl` width and height parameters must be in pixels.</span></span> <span data-ttu-id="783b9-209">Para garantir que as dimensões estão dentro dos limites permitidos, consulte [diretrizes de design](design/designing-apps-in-meetings.md).</span><span class="sxs-lookup"><span data-stu-id="783b9-209">To ensure the dimensions are within the allowed limits, see [design guidelines](design/designing-apps-in-meetings.md).</span></span>
> * <span data-ttu-id="783b9-210">A URL é a página carregada como `<iframe>` uma caixa de diálogo na reunião.</span><span class="sxs-lookup"><span data-stu-id="783b9-210">The URL is the page loaded as an `<iframe>` in the in-meeting dialog box.</span></span> <span data-ttu-id="783b9-211">O domínio deve estar na matriz do aplicativo `validDomains` no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="783b9-211">The domain must be in the app's `validDomains` array in your app manifest.</span></span>

# <a name="c"></a>[<span data-ttu-id="783b9-212">C#</span><span class="sxs-lookup"><span data-stu-id="783b9-212">C#</span></span>](#tab/dotnet)

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

# <a name="javascript"></a>[<span data-ttu-id="783b9-213">JavaScript</span><span class="sxs-lookup"><span data-stu-id="783b9-213">JavaScript</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="783b9-214">JSON</span><span class="sxs-lookup"><span data-stu-id="783b9-214">JSON</span></span>](#tab/json)

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

#### <a name="response-codes"></a><span data-ttu-id="783b9-215">Códigos de resposta</span><span class="sxs-lookup"><span data-stu-id="783b9-215">Response codes</span></span>

|<span data-ttu-id="783b9-216">Código da resposta</span><span class="sxs-lookup"><span data-stu-id="783b9-216">Response code</span></span>|<span data-ttu-id="783b9-217">Descrição</span><span class="sxs-lookup"><span data-stu-id="783b9-217">Description</span></span>|
|---|---|
| <span data-ttu-id="783b9-218">**201**</span><span class="sxs-lookup"><span data-stu-id="783b9-218">**201**</span></span> | <span data-ttu-id="783b9-219">A atividade com sinal é enviada com êxito</span><span class="sxs-lookup"><span data-stu-id="783b9-219">The activity with signal is successfully sent</span></span> |
| <span data-ttu-id="783b9-220">**401**</span><span class="sxs-lookup"><span data-stu-id="783b9-220">**401**</span></span> | <span data-ttu-id="783b9-221">O aplicativo responde com um token inválido.</span><span class="sxs-lookup"><span data-stu-id="783b9-221">The app responds with an invalid token.</span></span> |
| <span data-ttu-id="783b9-222">**403**</span><span class="sxs-lookup"><span data-stu-id="783b9-222">**403**</span></span> | <span data-ttu-id="783b9-223">O aplicativo não consegue enviar o sinal.</span><span class="sxs-lookup"><span data-stu-id="783b9-223">The app is unable to send the signal.</span></span> <span data-ttu-id="783b9-224">Isso pode acontecer devido a vários motivos, como o administrador de locatários desabilita o aplicativo, o aplicativo é bloqueado durante a migração de site ao vivo e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="783b9-224">This can happen due to various reasons such as the tenant admin disables the app, the app is blocked during live site migration, and so on.</span></span> <span data-ttu-id="783b9-225">Nesse caso, a carga contém uma mensagem de erro detalhada.</span><span class="sxs-lookup"><span data-stu-id="783b9-225">In this case, the payload contains a detailed error message.</span></span> |
| <span data-ttu-id="783b9-226">**404**</span><span class="sxs-lookup"><span data-stu-id="783b9-226">**404**</span></span> | <span data-ttu-id="783b9-227">O chat de reunião não existe.</span><span class="sxs-lookup"><span data-stu-id="783b9-227">The meeting chat does not exist.</span></span> |

## <a name="enable-your-app-for-teams-meetings"></a><span data-ttu-id="783b9-228">Habilitar seu aplicativo para reuniões do Teams</span><span class="sxs-lookup"><span data-stu-id="783b9-228">Enable your app for Teams meetings</span></span>

### <a name="update-your-app-manifest"></a><span data-ttu-id="783b9-229">Atualizar o manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="783b9-229">Update your app manifest</span></span>

<span data-ttu-id="783b9-230">Os recursos do aplicativo de reuniões são declarados no manifesto do aplicativo usando `configurableTabs` `scopes` as matrizes , e `context` .</span><span class="sxs-lookup"><span data-stu-id="783b9-230">The meetings app capabilities are declared in your app manifest using the `configurableTabs`, `scopes`, and `context` arrays.</span></span> <span data-ttu-id="783b9-231">O escopo define a quem e o contexto define onde seu aplicativo está disponível.</span><span class="sxs-lookup"><span data-stu-id="783b9-231">Scope defines to whom and context defines where your app is available.</span></span>

> [!NOTE]
> <span data-ttu-id="783b9-232">Tente atualizar o manifesto do aplicativo com o [esquema de manifesto](../resources/schema/manifest-schema-dev-preview.md).</span><span class="sxs-lookup"><span data-stu-id="783b9-232">Try updating your app manifest with the [manifest schema](../resources/schema/manifest-schema-dev-preview.md).</span></span>

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

### <a name="context-property"></a><span data-ttu-id="783b9-233">Propriedade Context</span><span class="sxs-lookup"><span data-stu-id="783b9-233">Context property</span></span>

<span data-ttu-id="783b9-234">A guia `context` e `scopes` as propriedades permitem determinar onde seu aplicativo deve aparecer.</span><span class="sxs-lookup"><span data-stu-id="783b9-234">The tab `context` and `scopes` properties enable you to determine where your app must appear.</span></span> <span data-ttu-id="783b9-235">Guias no `team` escopo ou podem `groupchat` ter mais de um contexto.</span><span class="sxs-lookup"><span data-stu-id="783b9-235">Tabs in the `team` or `groupchat` scope can have more than one context.</span></span> <span data-ttu-id="783b9-236">A seguir estão os valores da propriedade da qual você pode usar todos ou `context` alguns dos valores:</span><span class="sxs-lookup"><span data-stu-id="783b9-236">Following are the values for the `context` property from which you can use all or some of the values:</span></span>

|<span data-ttu-id="783b9-237">Valor</span><span class="sxs-lookup"><span data-stu-id="783b9-237">Value</span></span>|<span data-ttu-id="783b9-238">Descrição</span><span class="sxs-lookup"><span data-stu-id="783b9-238">Description</span></span>|
|---|---|
| <span data-ttu-id="783b9-239">**channelTab**</span><span class="sxs-lookup"><span data-stu-id="783b9-239">**channelTab**</span></span> | <span data-ttu-id="783b9-240">Uma guia no header de um canal de equipe.</span><span class="sxs-lookup"><span data-stu-id="783b9-240">A tab in the header of a team channel.</span></span> |
| <span data-ttu-id="783b9-241">**privateChatTab**</span><span class="sxs-lookup"><span data-stu-id="783b9-241">**privateChatTab**</span></span> | <span data-ttu-id="783b9-242">Uma guia no header de um chat de grupo entre um conjunto de usuários que não está no contexto de uma equipe ou reunião.</span><span class="sxs-lookup"><span data-stu-id="783b9-242">A tab in the header of a group chat between a set of users not in the context of a team or meeting.</span></span> |
| <span data-ttu-id="783b9-243">**meetingChatTab**</span><span class="sxs-lookup"><span data-stu-id="783b9-243">**meetingChatTab**</span></span> | <span data-ttu-id="783b9-244">Uma guia no header de um chat de grupo entre um conjunto de usuários no contexto de uma reunião agendada.</span><span class="sxs-lookup"><span data-stu-id="783b9-244">A tab in the header of a group chat between a set of users in the context of a scheduled meeting.</span></span> |
| <span data-ttu-id="783b9-245">**meetingDetailsTab**</span><span class="sxs-lookup"><span data-stu-id="783b9-245">**meetingDetailsTab**</span></span> | <span data-ttu-id="783b9-246">Uma guia no header da exibição de detalhes da reunião do calendário.</span><span class="sxs-lookup"><span data-stu-id="783b9-246">A tab in the header of the meeting details view of the calendar.</span></span> |
| <span data-ttu-id="783b9-247">**meetingSidePanel**</span><span class="sxs-lookup"><span data-stu-id="783b9-247">**meetingSidePanel**</span></span> | <span data-ttu-id="783b9-248">Um painel na reunião foi aberto por meio da barra unificada (U-bar).</span><span class="sxs-lookup"><span data-stu-id="783b9-248">An in-meeting panel opened via the unified bar (U-bar).</span></span> |

> [!NOTE]
> <span data-ttu-id="783b9-249">`Context` atualmente, não há suporte para clientes móveis.</span><span class="sxs-lookup"><span data-stu-id="783b9-249">`Context` property is currently not supported on mobile clients.</span></span>

## <a name="configure-your-app-for-meeting-scenarios"></a><span data-ttu-id="783b9-250">Configurar seu aplicativo para cenários de reunião</span><span class="sxs-lookup"><span data-stu-id="783b9-250">Configure your app for meeting scenarios</span></span>

> [!NOTE]
> * <span data-ttu-id="783b9-251">Para que seu aplicativo seja visível na galeria de guias, ele deve dar suporte a guias configuráveis e ao escopo de chat de grupo.</span><span class="sxs-lookup"><span data-stu-id="783b9-251">For your app to be visible in the tab gallery it must support configurable tabs and the group chat scope.</span></span>
> * <span data-ttu-id="783b9-252">Os clientes móveis suportam guias somente em estágios pré e pós-reunião.</span><span class="sxs-lookup"><span data-stu-id="783b9-252">Mobile clients support tabs only in pre and post meeting stages.</span></span>
> * <span data-ttu-id="783b9-253">As experiências na reunião que estão na caixa de diálogo e na guia da reunião atualmente não são suportadas em clientes móveis.</span><span class="sxs-lookup"><span data-stu-id="783b9-253">The in-meeting experiences that is in-meeting dialog box and tab is currently not supported on mobile clients.</span></span> <span data-ttu-id="783b9-254">Para obter mais informações, consulte [diretrizes para guias em dispositivos móveis](../tabs/design/tabs-mobile.md) ao criar suas guias para dispositivos móveis.</span><span class="sxs-lookup"><span data-stu-id="783b9-254">For more information, see [guidance for tabs on mobile](../tabs/design/tabs-mobile.md) when creating your tabs for mobile.</span></span>

### <a name="before-a-meeting"></a><span data-ttu-id="783b9-255">Antes de uma reunião</span><span class="sxs-lookup"><span data-stu-id="783b9-255">Before a meeting</span></span>

<span data-ttu-id="783b9-256">Antes de uma reunião, os usuários podem adicionar guias, bots e extensões de mensagens a uma reunião.</span><span class="sxs-lookup"><span data-stu-id="783b9-256">Before a meeting, users can add tabs, bots and messaging extensions to a meeting.</span></span> <span data-ttu-id="783b9-257">Os usuários com funções de organizador e apresentador podem adicionar guias a uma reunião.</span><span class="sxs-lookup"><span data-stu-id="783b9-257">Users with organizer and presenter roles can add tabs to a meeting.</span></span>

<span data-ttu-id="783b9-258">**Para adicionar uma guia a uma reunião**</span><span class="sxs-lookup"><span data-stu-id="783b9-258">**To add a tab to a meeting**</span></span>

1. <span data-ttu-id="783b9-259">Em seu calendário, selecione uma reunião à qual deseja adicionar uma guia.</span><span class="sxs-lookup"><span data-stu-id="783b9-259">In your calendar, select a meeting to which you want to add a tab.</span></span>
1. <span data-ttu-id="783b9-260">Selecione a **guia Detalhes** e selecione mais</span><span class="sxs-lookup"><span data-stu-id="783b9-260">Select the **Details** tab and select plus</span></span> <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/><span data-ttu-id="783b9-261">.</span><span class="sxs-lookup"><span data-stu-id="783b9-261">.</span></span> <span data-ttu-id="783b9-262">A galeria de guias é exibida.</span><span class="sxs-lookup"><span data-stu-id="783b9-262">The tab gallery appears.</span></span>

    ![Experiência de pré-reunião](../assets/images/apps-in-meetings/PreMeeting.png)

1. <span data-ttu-id="783b9-264">Na galeria de guias, selecione o aplicativo que você deseja adicionar e siga as etapas conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="783b9-264">In the tab gallery, select the app that you want to add and follow the steps as required.</span></span> <span data-ttu-id="783b9-265">O aplicativo é instalado como uma guia.</span><span class="sxs-lookup"><span data-stu-id="783b9-265">The app is installed as a tab.</span></span>
    > [!NOTE] 
    > <span data-ttu-id="783b9-266">Atualmente, na guia reuniões, não há suporte para obter detalhes da reunião e informações dos participantes.</span><span class="sxs-lookup"><span data-stu-id="783b9-266">Currently, in meetings tab, getting meeting details and participant information is not supported.</span></span>

<span data-ttu-id="783b9-267">**Para adicionar uma extensão de mensagens a uma reunião**</span><span class="sxs-lookup"><span data-stu-id="783b9-267">**To add a messaging extension to a meeting**</span></span>

1. <span data-ttu-id="783b9-268">Selecione as releições ou o menu de estouro &#x25CF;&#x25CF;&#x25CF; localizado na área de mensagem de redação no chat.</span><span class="sxs-lookup"><span data-stu-id="783b9-268">Select the ellipses or overflow menu &#x25CF;&#x25CF;&#x25CF; located in the compose message area in the chat.</span></span>
1. <span data-ttu-id="783b9-269">Selecione o aplicativo que você deseja adicionar e siga as etapas conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="783b9-269">Select the app that you want to add and follow the steps as required.</span></span> <span data-ttu-id="783b9-270">O aplicativo é instalado como uma extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="783b9-270">The app is installed as a messaging extension.</span></span>

<span data-ttu-id="783b9-271">**Para adicionar um bot a uma reunião**</span><span class="sxs-lookup"><span data-stu-id="783b9-271">**To add a bot to a meeting**</span></span>

<span data-ttu-id="783b9-272">Em um chat de reunião, insira **@** a chave e selecione Obter **bots**.</span><span class="sxs-lookup"><span data-stu-id="783b9-272">In a meeting chat enter the **@** key and select **Get bots**.</span></span>

> [!NOTE]
> * <span data-ttu-id="783b9-273">A identidade do usuário deve ser confirmada usando [Guias SSO](../tabs/how-to/authentication/auth-aad-sso.md).</span><span class="sxs-lookup"><span data-stu-id="783b9-273">The user identity must be confirmed using [Tabs SSO](../tabs/how-to/authentication/auth-aad-sso.md).</span></span> <span data-ttu-id="783b9-274">Após a autenticação, o aplicativo pode recuperar a função de usuário usando a `GetParticipant` API.</span><span class="sxs-lookup"><span data-stu-id="783b9-274">After authentication, the app can retrieve the user role using the `GetParticipant` API.</span></span>
> * <span data-ttu-id="783b9-275">Com base na função de usuário, o aplicativo tem a capacidade de fornecer experiências específicas de função.</span><span class="sxs-lookup"><span data-stu-id="783b9-275">Based on the user role, the app has the capability to provide role specific experiences.</span></span> <span data-ttu-id="783b9-276">Por exemplo, um aplicativo de sondagem permite que apenas organizadores e apresentadores criem uma nova sondagem.</span><span class="sxs-lookup"><span data-stu-id="783b9-276">For example, a polling app allows only organizers and presenters to create a new poll.</span></span>
> * <span data-ttu-id="783b9-277">As atribuições de função podem ser alteradas enquanto uma reunião está em andamento.</span><span class="sxs-lookup"><span data-stu-id="783b9-277">Role assignments can be changed while a meeting is in progress.</span></span> <span data-ttu-id="783b9-278">Para obter mais informações, [consulte funções em uma reunião do Teams](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span><span class="sxs-lookup"><span data-stu-id="783b9-278">For more information, see [roles in a Teams meeting](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span></span>

### <a name="during-a-meeting"></a><span data-ttu-id="783b9-279">Durante uma reunião</span><span class="sxs-lookup"><span data-stu-id="783b9-279">During a meeting</span></span>

#### <a name="sidepanel"></a><span data-ttu-id="783b9-280">sidePanel</span><span class="sxs-lookup"><span data-stu-id="783b9-280">sidePanel</span></span>

<span data-ttu-id="783b9-281">Com o sidePanel, você pode personalizar experiências em uma reunião que permitem que organizadores e apresentadores tenham diferentes tipos de exibição e ações.</span><span class="sxs-lookup"><span data-stu-id="783b9-281">With the sidePanel, you can customize experiences in a meeting that enable organizers and presenters to have different set of views and actions.</span></span> <span data-ttu-id="783b9-282">No manifesto do aplicativo, você deve adicionar sidePanel à matriz de contexto.</span><span class="sxs-lookup"><span data-stu-id="783b9-282">In your app manifest, you must add sidePanel to the context array.</span></span> <span data-ttu-id="783b9-283">Na reunião e em todos os cenários, o aplicativo é renderizado em uma guia na reunião que tem 320 pixels de largura.</span><span class="sxs-lookup"><span data-stu-id="783b9-283">In the meeting and in all scenarios, the app is rendered in an in-meeting tab that is 320 pixels in width.</span></span> <span data-ttu-id="783b9-284">Para obter mais informações, consulte [Interface FrameContext](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/framecontext?view=msteams-client-js-latest&preserve-view=true
).</span><span class="sxs-lookup"><span data-stu-id="783b9-284">For more information, see [FrameContext interface](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/framecontext?view=msteams-client-js-latest&preserve-view=true
).</span></span>

<span data-ttu-id="783b9-285">Para usar a `userContext` API para rotear solicitações de acordo, consulte [Teams SDK](../tabs/how-to/access-teams-context.md#user-context).</span><span class="sxs-lookup"><span data-stu-id="783b9-285">To use the `userContext` API to route requests accordingly, see [Teams SDK](../tabs/how-to/access-teams-context.md#user-context).</span></span> <span data-ttu-id="783b9-286">Consulte [Fluxo de autenticação do Teams para guias](../tabs/how-to/authentication/auth-flow-tab.md).</span><span class="sxs-lookup"><span data-stu-id="783b9-286">See [Teams authentication flow for tabs](../tabs/how-to/authentication/auth-flow-tab.md).</span></span> <span data-ttu-id="783b9-287">O fluxo de autenticação para guias é muito semelhante ao fluxo de autenticação para sites.</span><span class="sxs-lookup"><span data-stu-id="783b9-287">Authentication flow for tabs is very similar to the auth flow for websites.</span></span> <span data-ttu-id="783b9-288">Portanto, as guias podem usar o OAuth 2.0 diretamente.</span><span class="sxs-lookup"><span data-stu-id="783b9-288">So tabs can use OAuth 2.0 directly.</span></span> <span data-ttu-id="783b9-289">Consulte a plataforma de identidade da Microsoft e o fluxo de código de autorização do [OAuth 2.0.](/azure/active-directory/develop/v2-oauth2-auth-code-flow)</span><span class="sxs-lookup"><span data-stu-id="783b9-289">See, [Microsoft identity platform and OAuth 2.0 authorization code flow](/azure/active-directory/develop/v2-oauth2-auth-code-flow).</span></span>

<span data-ttu-id="783b9-290">A extensão de mensagens funciona conforme o esperado quando um usuário está em uma exibição em reunião e o usuário pode postar cartões de extensão de mensagem de composição.</span><span class="sxs-lookup"><span data-stu-id="783b9-290">Messaging extension works as expected when a user is in an in-meeting view and the user can post compose message extension cards.</span></span> <span data-ttu-id="783b9-291">AppName in-meeting é uma dica de ferramenta que informa o nome do aplicativo na U-bar de reunião.</span><span class="sxs-lookup"><span data-stu-id="783b9-291">AppName in-meeting is a tooltip that states the app name in-meeting U-bar.</span></span>

#### <a name="in-meeting-dialog"></a><span data-ttu-id="783b9-292">Caixa de diálogo na reunião</span><span class="sxs-lookup"><span data-stu-id="783b9-292">In-meeting dialog</span></span>

<span data-ttu-id="783b9-293">A caixa de diálogo na reunião pode ser usada para envolver os participantes durante a reunião e coletar informações ou comentários durante a reunião.</span><span class="sxs-lookup"><span data-stu-id="783b9-293">The in-meeting dialog box can be used to engage participants during the meeting and collect information or feedback during the meeting.</span></span> <span data-ttu-id="783b9-294">Use a [`NotificationSignal`](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) API para sinalizar que uma notificação de bolha deve ser disparada.</span><span class="sxs-lookup"><span data-stu-id="783b9-294">Use the [`NotificationSignal`](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) API to signal that a bubble notification must be triggered.</span></span> <span data-ttu-id="783b9-295">Como parte da carga da solicitação de notificação, inclua a URL onde o conteúdo a ser mostrado está hospedado.</span><span class="sxs-lookup"><span data-stu-id="783b9-295">As part of the notification request payload, include the URL where the content to be shown is hosted.</span></span>

<span data-ttu-id="783b9-296">A caixa de diálogo na reunião não deve usar o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="783b9-296">In-meeting dialog must not use task module.</span></span> <span data-ttu-id="783b9-297">O módulo de tarefa não é invocado em um chat de reunião.</span><span class="sxs-lookup"><span data-stu-id="783b9-297">Task module is not invoked in a meeting chat.</span></span> <span data-ttu-id="783b9-298">Uma URL de recurso externo é usada para exibir a bolha de conteúdo em uma reunião.</span><span class="sxs-lookup"><span data-stu-id="783b9-298">An external resource URL is used to display content bubble in a meeting.</span></span> <span data-ttu-id="783b9-299">Você pode usar o `submitTask` método para enviar dados em um chat de reunião.</span><span class="sxs-lookup"><span data-stu-id="783b9-299">You can use the `submitTask` method to submit data in a meeting chat.</span></span>

> [!NOTE]
> * <span data-ttu-id="783b9-300">Você deve invocar [a função submitTask()](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) para descartar automaticamente depois que um usuário realizar uma ação no web-view.</span><span class="sxs-lookup"><span data-stu-id="783b9-300">You must invoke the [submitTask()](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) function to dismiss automatically after a user takes an action in the web-view.</span></span> <span data-ttu-id="783b9-301">Esse é um requisito para envio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="783b9-301">This is a requirement for app submission.</span></span> <span data-ttu-id="783b9-302">Para obter mais informações, consulte [Módulo de tarefas do SDK do Teams.](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="783b9-302">For more information, see [Teams SDK task module](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).</span></span>
> * <span data-ttu-id="783b9-303">Se você quiser que seu aplicativo suporte usuários anônimos, sua carga inicial de solicitação de invocação deve depender dos metadados de solicitação no objeto, não `from.id` `from` nos `from.aadObjectId` metadados de solicitação.</span><span class="sxs-lookup"><span data-stu-id="783b9-303">If you want your app to support anonymous users, your initial invoke request payload must rely on the `from.id` request metadata in the `from` object, not the `from.aadObjectId` request metadata.</span></span> <span data-ttu-id="783b9-304">`from.id` é a ID do usuário e é a ID do `from.aadObjectId` Azure Active Directory (AAD) do usuário.</span><span class="sxs-lookup"><span data-stu-id="783b9-304">`from.id` is the user ID and `from.aadObjectId` is the Azure Active Directory (AAD) ID of the user.</span></span> <span data-ttu-id="783b9-305">Para obter mais informações, [consulte using task modules in tabs](../task-modules-and-cards/task-modules/task-modules-tabs.md) e [create and send the task module](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).</span><span class="sxs-lookup"><span data-stu-id="783b9-305">For more information, see [using task modules in tabs](../task-modules-and-cards/task-modules/task-modules-tabs.md) and [create and send the task module](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).</span></span>

### <a name="after-a-meeting"></a><span data-ttu-id="783b9-306">Após uma reunião</span><span class="sxs-lookup"><span data-stu-id="783b9-306">After a meeting</span></span>

<span data-ttu-id="783b9-307">As configurações pós-reunião e pré-reunião são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="783b9-307">The post-meeting and pre-meeting configurations are equivalent.</span></span>

## <a name="code-sample"></a><span data-ttu-id="783b9-308">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="783b9-308">Code sample</span></span>

|<span data-ttu-id="783b9-309">Exemplo de nome</span><span class="sxs-lookup"><span data-stu-id="783b9-309">Sample name</span></span> | <span data-ttu-id="783b9-310">Descrição</span><span class="sxs-lookup"><span data-stu-id="783b9-310">Description</span></span> | <span data-ttu-id="783b9-311">C#</span><span class="sxs-lookup"><span data-stu-id="783b9-311">C#</span></span> |
|----------------|-----------------|--------------|
| <span data-ttu-id="783b9-312">Extensibilidade de reuniões</span><span class="sxs-lookup"><span data-stu-id="783b9-312">Meetings extensibility</span></span> | <span data-ttu-id="783b9-313">Exemplo de extensibilidade de reunião do Microsoft Teams para tokens de passagem.</span><span class="sxs-lookup"><span data-stu-id="783b9-313">Microsoft Teams meeting extensibility sample for passing tokens.</span></span> | [<span data-ttu-id="783b9-314">View</span><span class="sxs-lookup"><span data-stu-id="783b9-314">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) |
| <span data-ttu-id="783b9-315">Bot de bolha de conteúdo de reunião</span><span class="sxs-lookup"><span data-stu-id="783b9-315">Meeting content bubble bot</span></span> | <span data-ttu-id="783b9-316">Exemplo de extensibilidade de reunião do Microsoft Teams para interagir com o bot de bolha de conteúdo em uma reunião.</span><span class="sxs-lookup"><span data-stu-id="783b9-316">Microsoft Teams meeting extensibility sample for interacting with content bubble bot in a meeting.</span></span> | [<span data-ttu-id="783b9-317">View</span><span class="sxs-lookup"><span data-stu-id="783b9-317">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/csharp) |

## <a name="see-also"></a><span data-ttu-id="783b9-318">Confira também</span><span class="sxs-lookup"><span data-stu-id="783b9-318">See also</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="783b9-319">Diretrizes de design de caixa de diálogo na reunião</span><span class="sxs-lookup"><span data-stu-id="783b9-319">In-meeting dialog design guidelines</span></span>](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
> [!div class="nextstepaction"]
> [<span data-ttu-id="783b9-320">Fluxo de autenticação do Teams para guias</span><span class="sxs-lookup"><span data-stu-id="783b9-320">Teams authentication flow for tabs</span></span>](../tabs/how-to/authentication/auth-flow-tab.md)
