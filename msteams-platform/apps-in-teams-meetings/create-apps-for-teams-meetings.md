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
# <a name="create-apps-for-teams-meetings"></a><span data-ttu-id="e32a1-104">Crie aplicativos para reuniões do Teams</span><span class="sxs-lookup"><span data-stu-id="e32a1-104">Create apps for Teams meetings</span></span>

## <a name="prerequisites-and-considerations"></a><span data-ttu-id="e32a1-105">Pré-requisitos e considerações</span><span class="sxs-lookup"><span data-stu-id="e32a1-105">Prerequisites and considerations</span></span>

<span data-ttu-id="e32a1-106">Antes de criar aplicativos para reuniões Teams, você deve ter uma compreensão das seguintes:</span><span class="sxs-lookup"><span data-stu-id="e32a1-106">Before you create apps for Teams meetings, you must have an understanding of the following:</span></span>

* <span data-ttu-id="e32a1-107">Você deve ter conhecimento de como desenvolver aplicativos Teams.</span><span class="sxs-lookup"><span data-stu-id="e32a1-107">You must have knowledge of how to develop Teams apps.</span></span> <span data-ttu-id="e32a1-108">Para obter mais informações, consulte [Teams desenvolvimento de aplicativos](../overview.md).</span><span class="sxs-lookup"><span data-stu-id="e32a1-108">For more information, see [Teams app development](../overview.md).</span></span>

* <span data-ttu-id="e32a1-109">Você deve atualizar o manifesto do aplicativo Teams para indicar que o aplicativo está disponível para reuniões.</span><span class="sxs-lookup"><span data-stu-id="e32a1-109">You must update the Teams app manifest to indicate that the app is available for meetings.</span></span> <span data-ttu-id="e32a1-110">Para obter mais informações, consulte [manifesto do aplicativo](#update-your-app-manifest).</span><span class="sxs-lookup"><span data-stu-id="e32a1-110">For more information, see [app manifest](#update-your-app-manifest).</span></span>

* <span data-ttu-id="e32a1-111">Para que seu aplicativo funcione no ciclo de vida de reunião como uma guia, ele deve suportar guias configuráveis no escopo do groupchat.</span><span class="sxs-lookup"><span data-stu-id="e32a1-111">For your app to function in the meeting lifecycle as a tab, it must support configurable tabs in the groupchat scope.</span></span> <span data-ttu-id="e32a1-112">Para obter mais informações, consulte [o escopo do groupchat](../resources/schema/manifest-schema.md#configurabletabs) e [construa uma guia de grupo](../build-your-first-app/build-channel-tab.md).</span><span class="sxs-lookup"><span data-stu-id="e32a1-112">For more information, see [groupchat scope](../resources/schema/manifest-schema.md#configurabletabs) and [build a group tab](../build-your-first-app/build-channel-tab.md).</span></span>

* <span data-ttu-id="e32a1-113">Você deve seguir as diretrizes gerais de design de guias Teams para cenários pré e pós-reunião.</span><span class="sxs-lookup"><span data-stu-id="e32a1-113">You must adhere to general Teams tab design guidelines for pre- and post-meeting scenarios.</span></span> <span data-ttu-id="e32a1-114">Para obter experiências durante as reuniões, consulte a guia de reunião e as diretrizes de design de diálogo em reunião.</span><span class="sxs-lookup"><span data-stu-id="e32a1-114">For experiences during meetings, refer to the in-meeting tab and in-meeting dialog design guidelines.</span></span> <span data-ttu-id="e32a1-115">Para obter mais informações, consulte Teams diretrizes de design de [guias,](../tabs/design/tabs.md) [diretrizes de design de guias em reunião](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab) e [diretrizes de design de diálogo em reunião.](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)</span><span class="sxs-lookup"><span data-stu-id="e32a1-115">For more information, see [Teams tab design guidelines](../tabs/design/tabs.md), [in-meeting tab design guidelines](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab) and [in-meeting dialog design guidelines](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog).</span></span>

* <span data-ttu-id="e32a1-116">Você deve apoiar o `groupchat` escopo para habilitar seu aplicativo em chats pré-reunião e pós-reunião.</span><span class="sxs-lookup"><span data-stu-id="e32a1-116">You must support the `groupchat` scope to enable your app in pre-meeting and post-meeting chats.</span></span> <span data-ttu-id="e32a1-117">Com a experiência de aplicativo pré-encontro, você pode encontrar e adicionar aplicativos de reunião e executar tarefas pré-reunião.</span><span class="sxs-lookup"><span data-stu-id="e32a1-117">With the pre-meeting app experience, you can find and add meeting apps and perform pre-meeting tasks.</span></span> <span data-ttu-id="e32a1-118">Com a experiência do aplicativo pós-reunião, você pode ver os resultados da reunião, como resultados da pesquisa ou feedback.</span><span class="sxs-lookup"><span data-stu-id="e32a1-118">With post-meeting app experience, you can view the results of the meeting, such as poll survey results or feedback.</span></span>

* <span data-ttu-id="e32a1-119">Atender aos parâmetros de URL da API deve `meetingId` `userId` ter, e `tenantId` .</span><span class="sxs-lookup"><span data-stu-id="e32a1-119">Meeting API URL parameters must have `meetingId`, `userId`, and `tenantId`.</span></span> <span data-ttu-id="e32a1-120">Estes estão disponíveis como parte da atividade de Teams cliente SDK e bot.</span><span class="sxs-lookup"><span data-stu-id="e32a1-120">These are available as part of the Teams client SDK and bot activity.</span></span> <span data-ttu-id="e32a1-121">Além disso, informações confiáveis para ID do usuário e ID do inquilino podem ser recuperadas usando [autenticação Tab SSO](../tabs/how-to/authentication/auth-aad-sso.md).</span><span class="sxs-lookup"><span data-stu-id="e32a1-121">In addition, reliable information for user ID and tenant ID can be retrieved using [Tab SSO authentication](../tabs/how-to/authentication/auth-aad-sso.md).</span></span>

* <span data-ttu-id="e32a1-122">A `GetParticipant` API deve ter um registro de bot e ID para gerar tokens auth.</span><span class="sxs-lookup"><span data-stu-id="e32a1-122">The `GetParticipant` API must have a bot registration and ID to generate auth tokens.</span></span> <span data-ttu-id="e32a1-123">Para obter mais informações, consulte [registro de bot e ID](../build-your-first-app/build-bot.md).</span><span class="sxs-lookup"><span data-stu-id="e32a1-123">For more information, see [bot registration and ID](../build-your-first-app/build-bot.md).</span></span>

* <span data-ttu-id="e32a1-124">Para que seu aplicativo atualize em tempo real, ele deve estar atualizado com base nas atividades do evento na reunião.</span><span class="sxs-lookup"><span data-stu-id="e32a1-124">For your app to update in real time, it must be up-to-date based on event activities in the meeting.</span></span> <span data-ttu-id="e32a1-125">Esses eventos podem estar dentro da caixa de diálogo presencial e outras etapas ao longo do ciclo de vida do encontro.</span><span class="sxs-lookup"><span data-stu-id="e32a1-125">These events can be within the in-meeting dialog box and other stages across the meeting lifecycle.</span></span> <span data-ttu-id="e32a1-126">Para a caixa de diálogo em reunião, consulte o parâmetro de conclusão `bot Id` em `Notification Signal API` .</span><span class="sxs-lookup"><span data-stu-id="e32a1-126">For the in-meeting dialog box, see completion `bot Id` parameter in `Notification Signal API`.</span></span>

## <a name="meeting-apps-api-reference"></a><span data-ttu-id="e32a1-127">Referência de API de aplicativos de reunião</span><span class="sxs-lookup"><span data-stu-id="e32a1-127">Meeting apps API reference</span></span>

|<span data-ttu-id="e32a1-128">API</span><span class="sxs-lookup"><span data-stu-id="e32a1-128">API</span></span>|<span data-ttu-id="e32a1-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="e32a1-129">Description</span></span>|<span data-ttu-id="e32a1-130">Solicitação</span><span class="sxs-lookup"><span data-stu-id="e32a1-130">Request</span></span>|<span data-ttu-id="e32a1-131">Origem</span><span class="sxs-lookup"><span data-stu-id="e32a1-131">Source</span></span>|
|---|---|----|---|
|<span data-ttu-id="e32a1-132">**GetUserContext**</span><span class="sxs-lookup"><span data-stu-id="e32a1-132">**GetUserContext**</span></span>| <span data-ttu-id="e32a1-133">Esta API permite que você obtenha informações contextuais para exibir conteúdo relevante em uma guia Teams.</span><span class="sxs-lookup"><span data-stu-id="e32a1-133">This API enables you to get contextual information to display relevant content in a Teams tab.</span></span> |<span data-ttu-id="e32a1-134">_**microsoftTeams.getContext( => { /*...\* / } )*\*_</span><span class="sxs-lookup"><span data-stu-id="e32a1-134">_**microsoftTeams.getContext( ( ) => {  /*...*/ } )**_</span></span>|<span data-ttu-id="e32a1-135">Microsoft Teams cliente SDK</span><span class="sxs-lookup"><span data-stu-id="e32a1-135">Microsoft Teams client SDK</span></span>|
|<span data-ttu-id="e32a1-136">**GetParticipant**</span><span class="sxs-lookup"><span data-stu-id="e32a1-136">**GetParticipant**</span></span>| <span data-ttu-id="e32a1-137">Esta API permite que um bot busque informações dos participantes atendendo o ID e o ID do participante.</span><span class="sxs-lookup"><span data-stu-id="e32a1-137">This API allows a bot to fetch participant information by meeting ID and participant ID.</span></span> |<span data-ttu-id="e32a1-138">**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_</span><span class="sxs-lookup"><span data-stu-id="e32a1-138">**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_</span></span> |<span data-ttu-id="e32a1-139">Microsoft Bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="e32a1-139">Microsoft Bot Framework SDK</span></span>|
|<span data-ttu-id="e32a1-140">**NotificaçõesSignal**</span><span class="sxs-lookup"><span data-stu-id="e32a1-140">**NotificationSignal**</span></span> | <span data-ttu-id="e32a1-141">Esta API permite que você forneça sinais de reunião que são entregues usando a API de notificação de conversação existente para o chat usuário-bot.</span><span class="sxs-lookup"><span data-stu-id="e32a1-141">This API enables you to provide meeting signals that are delivered using the existing conversation notification API for user-bot chat.</span></span> <span data-ttu-id="e32a1-142">Ele permite que você sinalize com base na ação do usuário que mostra uma caixa de diálogo em reunião.</span><span class="sxs-lookup"><span data-stu-id="e32a1-142">It allows you to signal based on user action that shows an in-meeting dialog box.</span></span> |<span data-ttu-id="e32a1-143">**POST** _**/v3/conversations/{conversationId}/activities**_</span><span class="sxs-lookup"><span data-stu-id="e32a1-143">**POST** _**/v3/conversations/{conversationId}/activities**_</span></span>|<span data-ttu-id="e32a1-144">Microsoft Bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="e32a1-144">Microsoft Bot Framework SDK</span></span>|

### <a name="getusercontext"></a><span data-ttu-id="e32a1-145">GetUserContext</span><span class="sxs-lookup"><span data-stu-id="e32a1-145">GetUserContext</span></span>

<span data-ttu-id="e32a1-146">Para identificar e recuperar informações contextuais para o conteúdo da guia, consulte [obter contexto para sua guia Teams](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library). `meetingId`é usado por uma guia ao executar no contexto da reunião e é adicionado para a carga de resposta.</span><span class="sxs-lookup"><span data-stu-id="e32a1-146">To identify and retrieve contextual information for your tab content, see [get context for your Teams tab](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library). `meetingId` is used by a tab when running in the meeting context and is added for the response payload.</span></span>

### <a name="getparticipant-api"></a><span data-ttu-id="e32a1-147">GetParticipant API</span><span class="sxs-lookup"><span data-stu-id="e32a1-147">GetParticipant API</span></span>

> [!NOTE]
> * <span data-ttu-id="e32a1-148">Não em cache de funções participantes, uma vez que o organizador do encontro pode mudar uma função a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="e32a1-148">Do not cache participant roles since the meeting organizer can change a role any time.</span></span>
> * <span data-ttu-id="e32a1-149">Teams atualmente não suporta grandes listas de distribuição ou tamanhos de listas de mais de 350 participantes para a `GetParticipant` API.</span><span class="sxs-lookup"><span data-stu-id="e32a1-149">Teams does not currently support large distribution lists or roster sizes of more than 350 participants for the `GetParticipant` API.</span></span>

#### <a name="query-parameters"></a><span data-ttu-id="e32a1-150">Parâmetros de consulta</span><span class="sxs-lookup"><span data-stu-id="e32a1-150">Query parameters</span></span>

|<span data-ttu-id="e32a1-151">Valor</span><span class="sxs-lookup"><span data-stu-id="e32a1-151">Value</span></span>|<span data-ttu-id="e32a1-152">Tipo</span><span class="sxs-lookup"><span data-stu-id="e32a1-152">Type</span></span>|<span data-ttu-id="e32a1-153">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="e32a1-153">Required</span></span>|<span data-ttu-id="e32a1-154">Descrição</span><span class="sxs-lookup"><span data-stu-id="e32a1-154">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="e32a1-155">**reuniãoId**</span><span class="sxs-lookup"><span data-stu-id="e32a1-155">**meetingId**</span></span>| <span data-ttu-id="e32a1-156">string</span><span class="sxs-lookup"><span data-stu-id="e32a1-156">string</span></span> | <span data-ttu-id="e32a1-157">Sim</span><span class="sxs-lookup"><span data-stu-id="e32a1-157">Yes</span></span> | <span data-ttu-id="e32a1-158">O identificador de reunião está disponível através do Bot Invoke e Teams Cliente SDK.</span><span class="sxs-lookup"><span data-stu-id="e32a1-158">The meeting identifier is available through Bot Invoke and Teams Client SDK.</span></span>|
|<span data-ttu-id="e32a1-159">**participantId**</span><span class="sxs-lookup"><span data-stu-id="e32a1-159">**participantId**</span></span>| <span data-ttu-id="e32a1-160">string</span><span class="sxs-lookup"><span data-stu-id="e32a1-160">string</span></span> | <span data-ttu-id="e32a1-161">Sim</span><span class="sxs-lookup"><span data-stu-id="e32a1-161">Yes</span></span> | <span data-ttu-id="e32a1-162">O ID participante é o ID do usuário.</span><span class="sxs-lookup"><span data-stu-id="e32a1-162">The participant ID is the user ID.</span></span> <span data-ttu-id="e32a1-163">Está disponível no Tab SSO, Bot Invoke e Teams Client SDK.</span><span class="sxs-lookup"><span data-stu-id="e32a1-163">It is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="e32a1-164">Recomenda-se obter um ID participante do Tab SSO.</span><span class="sxs-lookup"><span data-stu-id="e32a1-164">It is recommended to get a participant ID from the Tab SSO.</span></span> |
|<span data-ttu-id="e32a1-165">**tenantId**</span><span class="sxs-lookup"><span data-stu-id="e32a1-165">**tenantId**</span></span>| <span data-ttu-id="e32a1-166">string</span><span class="sxs-lookup"><span data-stu-id="e32a1-166">string</span></span> | <span data-ttu-id="e32a1-167">Sim</span><span class="sxs-lookup"><span data-stu-id="e32a1-167">Yes</span></span> | <span data-ttu-id="e32a1-168">A identificação do inquilino é necessária para os usuários do inquilino.</span><span class="sxs-lookup"><span data-stu-id="e32a1-168">The tenant ID is required for the tenant users.</span></span> <span data-ttu-id="e32a1-169">Está disponível no Tab SSO, Bot Invoke e Teams Client SDK.</span><span class="sxs-lookup"><span data-stu-id="e32a1-169">It is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="e32a1-170">Recomenda-se obter um ID de inquilino do Tab SSO.</span><span class="sxs-lookup"><span data-stu-id="e32a1-170">It is recommended to get a tenant ID from the Tab SSO.</span></span> |

#### <a name="example"></a><span data-ttu-id="e32a1-171">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e32a1-171">Example</span></span>

# <a name="c"></a>[<span data-ttu-id="e32a1-172">C#</span><span class="sxs-lookup"><span data-stu-id="e32a1-172">C#</span></span>](#tab/dotnet)

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

# <a name="javascript"></a>[<span data-ttu-id="e32a1-173">JavaScript</span><span class="sxs-lookup"><span data-stu-id="e32a1-173">JavaScript</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="e32a1-174">JSON</span><span class="sxs-lookup"><span data-stu-id="e32a1-174">JSON</span></span>](#tab/json)

```http
GET /v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}
```

* * *

<span data-ttu-id="e32a1-175">O corpo de resposta JSON para `GetParticipant` API é:</span><span class="sxs-lookup"><span data-stu-id="e32a1-175">The JSON response body for `GetParticipant` API is:</span></span>

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

#### <a name="response-codes"></a><span data-ttu-id="e32a1-176">Códigos de resposta</span><span class="sxs-lookup"><span data-stu-id="e32a1-176">Response codes</span></span>

|<span data-ttu-id="e32a1-177">Código da resposta</span><span class="sxs-lookup"><span data-stu-id="e32a1-177">Response code</span></span>|<span data-ttu-id="e32a1-178">Descrição</span><span class="sxs-lookup"><span data-stu-id="e32a1-178">Description</span></span>|
|---|---|
| <span data-ttu-id="e32a1-179">**403**</span><span class="sxs-lookup"><span data-stu-id="e32a1-179">**403**</span></span> | <span data-ttu-id="e32a1-180">O aplicativo não tem permissão para obter informações do participante.</span><span class="sxs-lookup"><span data-stu-id="e32a1-180">The app is not allowed to get participant information.</span></span> <span data-ttu-id="e32a1-181">Esta é a resposta de erro mais comum e é acionada se o aplicativo não for instalado na reunião.</span><span class="sxs-lookup"><span data-stu-id="e32a1-181">This is the most common error response and is triggered if the app is not installed in the meeting.</span></span> <span data-ttu-id="e32a1-182">Por exemplo, se o aplicativo for desativado por administrador de inquilinos ou bloqueado durante a migração do site ao vivo.</span><span class="sxs-lookup"><span data-stu-id="e32a1-182">For example, if the app is disabled by tenant admin or blocked during live site migration.</span></span>|
| <span data-ttu-id="e32a1-183">**200**</span><span class="sxs-lookup"><span data-stu-id="e32a1-183">**200**</span></span> | <span data-ttu-id="e32a1-184">As informações do participante são recuperadas com sucesso.</span><span class="sxs-lookup"><span data-stu-id="e32a1-184">The participant information is successfully retrieved.</span></span>|
| <span data-ttu-id="e32a1-185">**401**</span><span class="sxs-lookup"><span data-stu-id="e32a1-185">**401**</span></span> | <span data-ttu-id="e32a1-186">O aplicativo responde com um token inválido.</span><span class="sxs-lookup"><span data-stu-id="e32a1-186">The app responds with an invalid token.</span></span>|
| <span data-ttu-id="e32a1-187">**404**</span><span class="sxs-lookup"><span data-stu-id="e32a1-187">**404**</span></span> | <span data-ttu-id="e32a1-188">A reunião expirou ou o participante não pode ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="e32a1-188">The meeting has either expired or participant cannot be found.</span></span>|
| <span data-ttu-id="e32a1-189">**500**</span><span class="sxs-lookup"><span data-stu-id="e32a1-189">**500**</span></span> | <span data-ttu-id="e32a1-190">A reunião já expirou mais de 60 dias desde o término da reunião ou o participante não tem permissões com base em seu papel.</span><span class="sxs-lookup"><span data-stu-id="e32a1-190">The meeting has either expired more than 60 days since the meeting ended or the participant does not have permissions based on their role.</span></span>|

### <a name="notificationsignal-api"></a><span data-ttu-id="e32a1-191">NotificaçõesA API do sinal</span><span class="sxs-lookup"><span data-stu-id="e32a1-191">NotificationSignal API</span></span>

<span data-ttu-id="e32a1-192">Todos os usuários em uma reunião recebem as notificações enviadas através da `NotificationSignal` API.</span><span class="sxs-lookup"><span data-stu-id="e32a1-192">All users in a meeting receive the notifications sent through the `NotificationSignal` API.</span></span>

> [!NOTE]
> * <span data-ttu-id="e32a1-193">Quando uma caixa de diálogo em reunião é invocada, o conteúdo é apresentado como uma mensagem de bate-papo.</span><span class="sxs-lookup"><span data-stu-id="e32a1-193">When an in-meeting dialog box is invoked, the content is presented as a chat message.</span></span>
> * <span data-ttu-id="e32a1-194">Atualmente, o envio de notificações direcionadas não é suportado.</span><span class="sxs-lookup"><span data-stu-id="e32a1-194">Currently, sending targeted notifications is not supported.</span></span>

#### <a name="query-parameters"></a><span data-ttu-id="e32a1-195">Parâmetros de consulta</span><span class="sxs-lookup"><span data-stu-id="e32a1-195">Query parameters</span></span>

|<span data-ttu-id="e32a1-196">Valor</span><span class="sxs-lookup"><span data-stu-id="e32a1-196">Value</span></span>|<span data-ttu-id="e32a1-197">Tipo</span><span class="sxs-lookup"><span data-stu-id="e32a1-197">Type</span></span>|<span data-ttu-id="e32a1-198">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="e32a1-198">Required</span></span>|<span data-ttu-id="e32a1-199">Descrição</span><span class="sxs-lookup"><span data-stu-id="e32a1-199">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="e32a1-200">**conversationId**</span><span class="sxs-lookup"><span data-stu-id="e32a1-200">**conversationId**</span></span>| <span data-ttu-id="e32a1-201">string</span><span class="sxs-lookup"><span data-stu-id="e32a1-201">string</span></span> | <span data-ttu-id="e32a1-202">Sim</span><span class="sxs-lookup"><span data-stu-id="e32a1-202">Yes</span></span> | <span data-ttu-id="e32a1-203">O identificador de conversação está disponível como parte da invocação do bot.</span><span class="sxs-lookup"><span data-stu-id="e32a1-203">The conversation identifier is available as part of bot invoke.</span></span> |

#### <a name="example"></a><span data-ttu-id="e32a1-204">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e32a1-204">Example</span></span>

<span data-ttu-id="e32a1-205">O `Bot ID` é declarado no manifesto e o bot recebe um objeto resultante.</span><span class="sxs-lookup"><span data-stu-id="e32a1-205">The `Bot ID` is declared in the manifest and the bot receives a result object.</span></span>

> [!NOTE]
> * <span data-ttu-id="e32a1-206">O `completionBotId` parâmetro do é opcional no exemplo de carga `externalResourceUrl` solicitada.</span><span class="sxs-lookup"><span data-stu-id="e32a1-206">The `completionBotId` parameter of the `externalResourceUrl` is optional in the requested payload example.</span></span> <span data-ttu-id="e32a1-207">`Bot ID` é declarado no manifesto e o bot recebe um objeto resultante.</span><span class="sxs-lookup"><span data-stu-id="e32a1-207">`Bot ID` is declared in the manifest and the bot receives a result object.</span></span>
> * <span data-ttu-id="e32a1-208">Os `externalResourceUrl` parâmetros de largura e altura devem estar em pixels.</span><span class="sxs-lookup"><span data-stu-id="e32a1-208">The `externalResourceUrl` width and height parameters must be in pixels.</span></span> <span data-ttu-id="e32a1-209">Para garantir que as dimensões estejam dentro dos limites permitidos, consulte [as diretrizes de design](design/designing-apps-in-meetings.md).</span><span class="sxs-lookup"><span data-stu-id="e32a1-209">To ensure the dimensions are within the allowed limits, see [design guidelines](design/designing-apps-in-meetings.md).</span></span>
> * <span data-ttu-id="e32a1-210">A URL é a página carregada como uma `<iframe>` caixa de diálogo em reunião.</span><span class="sxs-lookup"><span data-stu-id="e32a1-210">The URL is the page loaded as an `<iframe>` in the in-meeting dialog box.</span></span> <span data-ttu-id="e32a1-211">O domínio deve estar na matriz do aplicativo no manifesto do `validDomains` aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e32a1-211">The domain must be in the app's `validDomains` array in your app manifest.</span></span>

# <a name="c"></a>[<span data-ttu-id="e32a1-212">C#</span><span class="sxs-lookup"><span data-stu-id="e32a1-212">C#</span></span>](#tab/dotnet)

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

# <a name="javascript"></a>[<span data-ttu-id="e32a1-213">JavaScript</span><span class="sxs-lookup"><span data-stu-id="e32a1-213">JavaScript</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="e32a1-214">JSON</span><span class="sxs-lookup"><span data-stu-id="e32a1-214">JSON</span></span>](#tab/json)

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

#### <a name="response-codes"></a><span data-ttu-id="e32a1-215">Códigos de resposta</span><span class="sxs-lookup"><span data-stu-id="e32a1-215">Response codes</span></span>

|<span data-ttu-id="e32a1-216">Código da resposta</span><span class="sxs-lookup"><span data-stu-id="e32a1-216">Response code</span></span>|<span data-ttu-id="e32a1-217">Descrição</span><span class="sxs-lookup"><span data-stu-id="e32a1-217">Description</span></span>|
|---|---|
| <span data-ttu-id="e32a1-218">**201**</span><span class="sxs-lookup"><span data-stu-id="e32a1-218">**201**</span></span> | <span data-ttu-id="e32a1-219">A atividade com sinal é enviada com sucesso.</span><span class="sxs-lookup"><span data-stu-id="e32a1-219">The activity with signal is successfully sent.</span></span> |
| <span data-ttu-id="e32a1-220">**401**</span><span class="sxs-lookup"><span data-stu-id="e32a1-220">**401**</span></span> | <span data-ttu-id="e32a1-221">O aplicativo responde com um token inválido.</span><span class="sxs-lookup"><span data-stu-id="e32a1-221">The app responds with an invalid token.</span></span> |
| <span data-ttu-id="e32a1-222">**403**</span><span class="sxs-lookup"><span data-stu-id="e32a1-222">**403**</span></span> | <span data-ttu-id="e32a1-223">O aplicativo não pode enviar o sinal.</span><span class="sxs-lookup"><span data-stu-id="e32a1-223">The app is unable to send the signal.</span></span> <span data-ttu-id="e32a1-224">Isso pode acontecer devido a várias razões como o administrador inquilino desativa o aplicativo, o aplicativo é bloqueado durante a migração ao vivo do site, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="e32a1-224">This can happen due to various reasons such as the tenant admin disables the app, the app is blocked during live site migration, and so on.</span></span> <span data-ttu-id="e32a1-225">Neste caso, a carga contém uma mensagem de erro detalhada.</span><span class="sxs-lookup"><span data-stu-id="e32a1-225">In this case, the payload contains a detailed error message.</span></span> |
| <span data-ttu-id="e32a1-226">**404**</span><span class="sxs-lookup"><span data-stu-id="e32a1-226">**404**</span></span> | <span data-ttu-id="e32a1-227">O bate-papo de reunião não existe.</span><span class="sxs-lookup"><span data-stu-id="e32a1-227">The meeting chat does not exist.</span></span> |

## <a name="enable-your-app-for-teams-meetings"></a><span data-ttu-id="e32a1-228">Habilite seu aplicativo para reuniões Teams</span><span class="sxs-lookup"><span data-stu-id="e32a1-228">Enable your app for Teams meetings</span></span>

### <a name="update-your-app-manifest"></a><span data-ttu-id="e32a1-229">Atualize seu manifesto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="e32a1-229">Update your app manifest</span></span>

<span data-ttu-id="e32a1-230">Os recursos do aplicativo de reuniões são declarados no manifesto do aplicativo usando o `configurableTabs` `scopes` , e `context` arrays.</span><span class="sxs-lookup"><span data-stu-id="e32a1-230">The meetings app capabilities are declared in your app manifest using the `configurableTabs`, `scopes`, and `context` arrays.</span></span> <span data-ttu-id="e32a1-231">Escopo define para quem e contexto define onde seu aplicativo está disponível.</span><span class="sxs-lookup"><span data-stu-id="e32a1-231">Scope defines to whom and context defines where your app is available.</span></span>

> [!NOTE]
> <span data-ttu-id="e32a1-232">Tente atualizar seu manifesto de aplicativo com o [esquema manifesto](../resources/schema/manifest-schema-dev-preview.md).</span><span class="sxs-lookup"><span data-stu-id="e32a1-232">Try updating your app manifest with the [manifest schema](../resources/schema/manifest-schema-dev-preview.md).</span></span>
> <span data-ttu-id="e32a1-233">Aplicativos em reuniões precisam de escopo *de groupchat.*</span><span class="sxs-lookup"><span data-stu-id="e32a1-233">Apps in meetings need *groupchat* scope.</span></span> <span data-ttu-id="e32a1-234">O escopo *da equipe* funciona apenas para guias em canais.</span><span class="sxs-lookup"><span data-stu-id="e32a1-234">The *team* scope works for tabs in channels only.</span></span>

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
> <span data-ttu-id="e32a1-235">`meetingStage` atualmente está disponível apenas na pré-visualização do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="e32a1-235">`meetingStage` is currently available in developer preview only.</span></span>

### <a name="context-property"></a><span data-ttu-id="e32a1-236">Propriedade Context</span><span class="sxs-lookup"><span data-stu-id="e32a1-236">Context property</span></span>

<span data-ttu-id="e32a1-237">A guia `context` e as propriedades permitem determinar onde seu aplicativo deve `scopes` aparecer.</span><span class="sxs-lookup"><span data-stu-id="e32a1-237">The tab `context` and `scopes` properties enable you to determine where your app must appear.</span></span> <span data-ttu-id="e32a1-238">Guias no `team` escopo ou podem ter mais de um `groupchat` contexto.</span><span class="sxs-lookup"><span data-stu-id="e32a1-238">Tabs in the `team` or `groupchat` scope can have more than one context.</span></span> <span data-ttu-id="e32a1-239">A seguir estão os valores para a `context` propriedade a partir da qual você pode usar todos ou alguns dos valores:</span><span class="sxs-lookup"><span data-stu-id="e32a1-239">Following are the values for the `context` property from which you can use all or some of the values:</span></span>

|<span data-ttu-id="e32a1-240">Valor</span><span class="sxs-lookup"><span data-stu-id="e32a1-240">Value</span></span>|<span data-ttu-id="e32a1-241">Descrição</span><span class="sxs-lookup"><span data-stu-id="e32a1-241">Description</span></span>|
|---|---|
| <span data-ttu-id="e32a1-242">**channelTab**</span><span class="sxs-lookup"><span data-stu-id="e32a1-242">**channelTab**</span></span> | <span data-ttu-id="e32a1-243">Uma guia na cabeçalho de um canal de equipe.</span><span class="sxs-lookup"><span data-stu-id="e32a1-243">A tab in the header of a team channel.</span></span> |
| <span data-ttu-id="e32a1-244">**privateChatTab**</span><span class="sxs-lookup"><span data-stu-id="e32a1-244">**privateChatTab**</span></span> | <span data-ttu-id="e32a1-245">Uma guia no cabeçalho de um bate-papo em grupo entre um conjunto de usuários que não estão no contexto de uma equipe ou reunião.</span><span class="sxs-lookup"><span data-stu-id="e32a1-245">A tab in the header of a group chat between a set of users not in the context of a team or meeting.</span></span> |
| <span data-ttu-id="e32a1-246">**reuniãoChatTab**</span><span class="sxs-lookup"><span data-stu-id="e32a1-246">**meetingChatTab**</span></span> | <span data-ttu-id="e32a1-247">Uma guia no cabeçalho de um bate-papo em grupo entre um conjunto de usuários no contexto de uma reunião agendada.</span><span class="sxs-lookup"><span data-stu-id="e32a1-247">A tab in the header of a group chat between a set of users in the context of a scheduled meeting.</span></span> |
| <span data-ttu-id="e32a1-248">**reuniãoDetailsTab**</span><span class="sxs-lookup"><span data-stu-id="e32a1-248">**meetingDetailsTab**</span></span> | <span data-ttu-id="e32a1-249">Uma guia no cabeçalho da reunião detalha a visualização do calendário.</span><span class="sxs-lookup"><span data-stu-id="e32a1-249">A tab in the header of the meeting details view of the calendar.</span></span> |
| <span data-ttu-id="e32a1-250">**reuniãoSidePanel**</span><span class="sxs-lookup"><span data-stu-id="e32a1-250">**meetingSidePanel**</span></span> | <span data-ttu-id="e32a1-251">Um painel de reunião aberto através do bar unificado (U-bar).</span><span class="sxs-lookup"><span data-stu-id="e32a1-251">An in-meeting panel opened via the unified bar (U-bar).</span></span> |
| <span data-ttu-id="e32a1-252">**palco de reunião**</span><span class="sxs-lookup"><span data-stu-id="e32a1-252">**meetingStage**</span></span> | <span data-ttu-id="e32a1-253">Um aplicativo do painel lateral pode ser compartilhado na fase de reunião.</span><span class="sxs-lookup"><span data-stu-id="e32a1-253">An app from the sidepanel can be shared to the meeting stage.</span></span> |

> [!NOTE]
> <span data-ttu-id="e32a1-254">`Context` atualmente, a propriedade não é suportada em clientes móveis.</span><span class="sxs-lookup"><span data-stu-id="e32a1-254">`Context` property is currently not supported on mobile clients.</span></span>

## <a name="configure-your-app-for-meeting-scenarios"></a><span data-ttu-id="e32a1-255">Configure seu aplicativo para cenários de reunião</span><span class="sxs-lookup"><span data-stu-id="e32a1-255">Configure your app for meeting scenarios</span></span>

> [!NOTE]
> * <span data-ttu-id="e32a1-256">Para que seu aplicativo seja visível na galeria de guias, ele deve suportar guias configuráveis e o escopo de bate-papo em grupo.</span><span class="sxs-lookup"><span data-stu-id="e32a1-256">For your app to be visible in the tab gallery it must support configurable tabs and the group chat scope.</span></span>
> * <span data-ttu-id="e32a1-257">Os clientes móveis suportam guias apenas em etapas pré e pós-reunião.</span><span class="sxs-lookup"><span data-stu-id="e32a1-257">Mobile clients support tabs only in pre and post meeting stages.</span></span>
> * <span data-ttu-id="e32a1-258">As experiências de encontro que são caixa de diálogo e guia no atendimento atualmente não são suportadas em clientes móveis.</span><span class="sxs-lookup"><span data-stu-id="e32a1-258">The in-meeting experiences that is in-meeting dialog box and tab is currently not supported on mobile clients.</span></span> <span data-ttu-id="e32a1-259">Para obter mais informações, consulte [orientação para guias no celular](../tabs/design/tabs-mobile.md) ao criar suas guias para celular.</span><span class="sxs-lookup"><span data-stu-id="e32a1-259">For more information, see [guidance for tabs on mobile](../tabs/design/tabs-mobile.md) when creating your tabs for mobile.</span></span>

### <a name="before-a-meeting"></a><span data-ttu-id="e32a1-260">Antes de uma reunião</span><span class="sxs-lookup"><span data-stu-id="e32a1-260">Before a meeting</span></span>

<span data-ttu-id="e32a1-261">Antes de uma reunião, os usuários podem adicionar guias, bots e extensões de mensagens a uma reunião.</span><span class="sxs-lookup"><span data-stu-id="e32a1-261">Before a meeting, users can add tabs, bots and messaging extensions to a meeting.</span></span> <span data-ttu-id="e32a1-262">Usuários com funções de organizador e apresentador podem adicionar guias a uma reunião.</span><span class="sxs-lookup"><span data-stu-id="e32a1-262">Users with organizer and presenter roles can add tabs to a meeting.</span></span>

<span data-ttu-id="e32a1-263">**Para adicionar uma guia a uma reunião**</span><span class="sxs-lookup"><span data-stu-id="e32a1-263">**To add a tab to a meeting**</span></span>

1. <span data-ttu-id="e32a1-264">Em seu calendário, selecione uma reunião à qual deseja adicionar uma guia.</span><span class="sxs-lookup"><span data-stu-id="e32a1-264">In your calendar, select a meeting to which you want to add a tab.</span></span>
1. <span data-ttu-id="e32a1-265">Selecione a guia **Detalhes** e selecione mais</span><span class="sxs-lookup"><span data-stu-id="e32a1-265">Select the **Details** tab and select plus</span></span> <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/><span data-ttu-id="e32a1-266">.</span><span class="sxs-lookup"><span data-stu-id="e32a1-266">.</span></span> <span data-ttu-id="e32a1-267">A galeria de guias aparece.</span><span class="sxs-lookup"><span data-stu-id="e32a1-267">The tab gallery appears.</span></span>

    ![Experiência de pré-encontro](../assets/images/apps-in-meetings/PreMeeting.png)

1. <span data-ttu-id="e32a1-269">Na galeria de guias, selecione o aplicativo que deseja adicionar e siga as etapas conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="e32a1-269">In the tab gallery, select the app that you want to add and follow the steps as required.</span></span> <span data-ttu-id="e32a1-270">O aplicativo é instalado como uma guia.</span><span class="sxs-lookup"><span data-stu-id="e32a1-270">The app is installed as a tab.</span></span>
    > [!NOTE] 
    > <span data-ttu-id="e32a1-271">Atualmente, na guia reuniões, não é suportada a obtenção de detalhes de reunião e informações dos participantes.</span><span class="sxs-lookup"><span data-stu-id="e32a1-271">Currently, in meetings tab, getting meeting details and participant information is not supported.</span></span>

<span data-ttu-id="e32a1-272">**Para adicionar uma extensão de mensagens a uma reunião**</span><span class="sxs-lookup"><span data-stu-id="e32a1-272">**To add a messaging extension to a meeting**</span></span>

1. <span data-ttu-id="e32a1-273">Selecione as elipses ou o menu de estouro &#x25CF;&#x25CF;&#x25CF; localizado na área de compor mensagens no chat.</span><span class="sxs-lookup"><span data-stu-id="e32a1-273">Select the ellipses or overflow menu &#x25CF;&#x25CF;&#x25CF; located in the compose message area in the chat.</span></span>
1. <span data-ttu-id="e32a1-274">Selecione o aplicativo que deseja adicionar e siga as etapas conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="e32a1-274">Select the app that you want to add and follow the steps as required.</span></span> <span data-ttu-id="e32a1-275">O aplicativo é instalado como uma extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="e32a1-275">The app is installed as a messaging extension.</span></span>

<span data-ttu-id="e32a1-276">**Para adicionar um bot a uma reunião**</span><span class="sxs-lookup"><span data-stu-id="e32a1-276">**To add a bot to a meeting**</span></span>

<span data-ttu-id="e32a1-277">Em um bate-papo de reunião, insira a **@** chave e selecione Obter **bots**.</span><span class="sxs-lookup"><span data-stu-id="e32a1-277">In a meeting chat enter the **@** key and select **Get bots**.</span></span>

> [!NOTE]
> * <span data-ttu-id="e32a1-278">A identidade do usuário deve ser confirmada usando [o Tabs SSO](../tabs/how-to/authentication/auth-aad-sso.md).</span><span class="sxs-lookup"><span data-stu-id="e32a1-278">The user identity must be confirmed using [Tabs SSO](../tabs/how-to/authentication/auth-aad-sso.md).</span></span> <span data-ttu-id="e32a1-279">Após a autenticação, o aplicativo pode recuperar a função do usuário usando a `GetParticipant` API.</span><span class="sxs-lookup"><span data-stu-id="e32a1-279">After authentication, the app can retrieve the user role using the `GetParticipant` API.</span></span>
> * <span data-ttu-id="e32a1-280">Com base na função do usuário, o aplicativo tem a capacidade de fornecer experiências específicas de função.</span><span class="sxs-lookup"><span data-stu-id="e32a1-280">Based on the user role, the app has the capability to provide role specific experiences.</span></span> <span data-ttu-id="e32a1-281">Por exemplo, um aplicativo de votação permite apenas que organizadores e apresentadores criem uma nova enquete.</span><span class="sxs-lookup"><span data-stu-id="e32a1-281">For example, a polling app allows only organizers and presenters to create a new poll.</span></span>
> * <span data-ttu-id="e32a1-282">As atribuições de papéis podem ser alteradas enquanto uma reunião está em andamento.</span><span class="sxs-lookup"><span data-stu-id="e32a1-282">Role assignments can be changed while a meeting is in progress.</span></span> <span data-ttu-id="e32a1-283">Para obter mais informações, consulte [papéis em uma reunião Teams](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span><span class="sxs-lookup"><span data-stu-id="e32a1-283">For more information, see [roles in a Teams meeting](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span></span>

### <a name="during-a-meeting"></a><span data-ttu-id="e32a1-284">Durante uma reunião</span><span class="sxs-lookup"><span data-stu-id="e32a1-284">During a meeting</span></span>

#### <a name="sidepanel"></a><span data-ttu-id="e32a1-285">sidePanel</span><span class="sxs-lookup"><span data-stu-id="e32a1-285">sidePanel</span></span>

<span data-ttu-id="e32a1-286">Com o sidePanel, você pode personalizar experiências em um encontro que permite aos organizadores e apresentadores ter diferentes conjuntos de pontos de vista e ações.</span><span class="sxs-lookup"><span data-stu-id="e32a1-286">With the sidePanel, you can customize experiences in a meeting that enable organizers and presenters to have different set of views and actions.</span></span> <span data-ttu-id="e32a1-287">No manifesto do aplicativo, você deve adicionar o painel lateral à matriz de contexto.</span><span class="sxs-lookup"><span data-stu-id="e32a1-287">In your app manifest, you must add sidePanel to the context array.</span></span> <span data-ttu-id="e32a1-288">Na reunião e em todos os cenários, o aplicativo é renderizado em uma guia de reunião que tem 320 pixels de largura.</span><span class="sxs-lookup"><span data-stu-id="e32a1-288">In the meeting and in all scenarios, the app is rendered in an in-meeting tab that is 320 pixels in width.</span></span> <span data-ttu-id="e32a1-289">Para obter mais informações, consulte [a interface FrameContext](/javascript/api/@microsoft/teams-js/framecontext?view=msteams-client-js-latest&preserve-view=true
).</span><span class="sxs-lookup"><span data-stu-id="e32a1-289">For more information, see [FrameContext interface](/javascript/api/@microsoft/teams-js/framecontext?view=msteams-client-js-latest&preserve-view=true
).</span></span>

<span data-ttu-id="e32a1-290">Para usar a `userContext` API para rotear as solicitações de acordo, consulte [Teams SDK](../tabs/how-to/access-teams-context.md#user-context).</span><span class="sxs-lookup"><span data-stu-id="e32a1-290">To use the `userContext` API to route requests accordingly, see [Teams SDK](../tabs/how-to/access-teams-context.md#user-context).</span></span> <span data-ttu-id="e32a1-291">Consulte [Teams fluxo de autenticação para guias](../tabs/how-to/authentication/auth-flow-tab.md).</span><span class="sxs-lookup"><span data-stu-id="e32a1-291">See [Teams authentication flow for tabs](../tabs/how-to/authentication/auth-flow-tab.md).</span></span> <span data-ttu-id="e32a1-292">O fluxo de autenticação para guias é muito semelhante ao fluxo de auth para sites.</span><span class="sxs-lookup"><span data-stu-id="e32a1-292">Authentication flow for tabs is very similar to the auth flow for websites.</span></span> <span data-ttu-id="e32a1-293">Assim, as guias podem usar o OAuth 2.0 diretamente.</span><span class="sxs-lookup"><span data-stu-id="e32a1-293">So tabs can use OAuth 2.0 directly.</span></span> <span data-ttu-id="e32a1-294">Veja, [fluxo de código de autorização plataforma de identidade da Microsoft e OAuth 2.0](/azure/active-directory/develop/v2-oauth2-auth-code-flow).</span><span class="sxs-lookup"><span data-stu-id="e32a1-294">See, [Microsoft identity platform and OAuth 2.0 authorization code flow](/azure/active-directory/develop/v2-oauth2-auth-code-flow).</span></span>

<span data-ttu-id="e32a1-295">A extensão de mensagens funciona como esperado quando um usuário está em uma exibição de reunião e o usuário pode postar cartões de extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="e32a1-295">Messaging extension works as expected when a user is in an in-meeting view and the user can post compose message extension cards.</span></span> <span data-ttu-id="e32a1-296">AppName na reunião é uma dica de ferramenta que afirma o nome do aplicativo em reunião U-bar.</span><span class="sxs-lookup"><span data-stu-id="e32a1-296">AppName in-meeting is a tooltip that states the app name in-meeting U-bar.</span></span>

> [!NOTE]
> <span data-ttu-id="e32a1-297">Use a versão 1.7.0 ou superior do [Teams SDK,](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)pois as versões anteriores não suportam o painel lateral.</span><span class="sxs-lookup"><span data-stu-id="e32a1-297">Use version 1.7.0 or higher of [Teams SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true), as versions prior to it do not support the side panel.</span></span>

#### <a name="in-meeting-dialog"></a><span data-ttu-id="e32a1-298">Caixa de diálogo na reunião</span><span class="sxs-lookup"><span data-stu-id="e32a1-298">In-meeting dialog</span></span>

<span data-ttu-id="e32a1-299">A caixa de diálogo presencial pode ser usada para engajar os participantes durante a reunião e coletar informações ou feedback durante a reunião.</span><span class="sxs-lookup"><span data-stu-id="e32a1-299">The in-meeting dialog box can be used to engage participants during the meeting and collect information or feedback during the meeting.</span></span> <span data-ttu-id="e32a1-300">Use a [`NotificationSignal`](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) API para sinalizar que uma notificação de bolha deve ser acionada.</span><span class="sxs-lookup"><span data-stu-id="e32a1-300">Use the [`NotificationSignal`](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) API to signal that a bubble notification must be triggered.</span></span> <span data-ttu-id="e32a1-301">Como parte da carga de solicitação de notificação, inclua a URL onde o conteúdo a ser mostrado está hospedado.</span><span class="sxs-lookup"><span data-stu-id="e32a1-301">As part of the notification request payload, include the URL where the content to be shown is hosted.</span></span>

<span data-ttu-id="e32a1-302">O diálogo de reunião não deve usar o módulo de tarefas.</span><span class="sxs-lookup"><span data-stu-id="e32a1-302">In-meeting dialog must not use task module.</span></span> <span data-ttu-id="e32a1-303">O módulo de tarefa não é invocado em um bate-papo de reunião.</span><span class="sxs-lookup"><span data-stu-id="e32a1-303">Task module is not invoked in a meeting chat.</span></span> <span data-ttu-id="e32a1-304">Uma URL de recurso externo é usada para exibir bolha de conteúdo em uma reunião.</span><span class="sxs-lookup"><span data-stu-id="e32a1-304">An external resource URL is used to display content bubble in a meeting.</span></span> <span data-ttu-id="e32a1-305">Você pode usar o `submitTask` método para enviar dados em um bate-papo de reunião.</span><span class="sxs-lookup"><span data-stu-id="e32a1-305">You can use the `submitTask` method to submit data in a meeting chat.</span></span>

> [!NOTE]
> * <span data-ttu-id="e32a1-306">Você deve invocar a função [submitTask()](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) para descartar automaticamente depois que um usuário tomar uma ação na exibição da Web.</span><span class="sxs-lookup"><span data-stu-id="e32a1-306">You must invoke the [submitTask()](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) function to dismiss automatically after a user takes an action in the web-view.</span></span> <span data-ttu-id="e32a1-307">Este é um requisito para submissão de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="e32a1-307">This is a requirement for app submission.</span></span> <span data-ttu-id="e32a1-308">Para obter mais informações, consulte [Teams módulo de tarefas SDK](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="e32a1-308">For more information, see [Teams SDK task module](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).</span></span>
> * <span data-ttu-id="e32a1-309">Se você quiser que seu aplicativo apoie usuários anônimos, sua carga inicial de solicitação de invocação deve depender dos `from.id` metadados de solicitação no `from` objeto, não nos `from.aadObjectId` metadados de solicitação.</span><span class="sxs-lookup"><span data-stu-id="e32a1-309">If you want your app to support anonymous users, your initial invoke request payload must rely on the `from.id` request metadata in the `from` object, not the `from.aadObjectId` request metadata.</span></span> <span data-ttu-id="e32a1-310">`from.id`é o ID do usuário e `from.aadObjectId` é o ID Azure Active Directory (AAD) do usuário.</span><span class="sxs-lookup"><span data-stu-id="e32a1-310">`from.id` is the user ID and `from.aadObjectId` is the Azure Active Directory (AAD) ID of the user.</span></span> <span data-ttu-id="e32a1-311">Para obter mais informações, consulte [o uso de módulos de tarefas nas guias](../task-modules-and-cards/task-modules/task-modules-tabs.md) e [crie e envie o módulo de tarefas](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).</span><span class="sxs-lookup"><span data-stu-id="e32a1-311">For more information, see [using task modules in tabs](../task-modules-and-cards/task-modules/task-modules-tabs.md) and [create and send the task module](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).</span></span>

#### <a name="share-to-stage"></a><span data-ttu-id="e32a1-312">Compartilhar para o palco</span><span class="sxs-lookup"><span data-stu-id="e32a1-312">Share to stage</span></span> 

> [!NOTE]
> * <span data-ttu-id="e32a1-313">Este recurso está atualmente disponível apenas na visualização do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="e32a1-313">This capability is currently available in developer preview only.</span></span>
> * <span data-ttu-id="e32a1-314">Para usar esse recurso, o aplicativo deve suportar um painel lateral em reunião.</span><span class="sxs-lookup"><span data-stu-id="e32a1-314">To use this feature, the app must support an in-meeting sidepanel.</span></span>


<span data-ttu-id="e32a1-315">Esse recurso dá aos desenvolvedores a capacidade de compartilhar um aplicativo para a fase de reunião.</span><span class="sxs-lookup"><span data-stu-id="e32a1-315">This capability gives developers the ability to share an app to the meeting stage.</span></span> <span data-ttu-id="e32a1-316">Ao possibilitar a participação na etapa de reunião, os participantes do encontro podem colaborar em tempo real.</span><span class="sxs-lookup"><span data-stu-id="e32a1-316">By enabling share to the meeting stage, meeting participants can collaborate in real-time.</span></span> 

<span data-ttu-id="e32a1-317">O contexto necessário está `meetingStage` no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e32a1-317">The required context is `meetingStage` in the app manifest.</span></span> <span data-ttu-id="e32a1-318">Um pré-requisito para isso é ter o `meetingSidePanel` contexto.</span><span class="sxs-lookup"><span data-stu-id="e32a1-318">A prerequisite for this is to have the `meetingSidePanel` context.</span></span> <span data-ttu-id="e32a1-319">Isso permite que o botão **Compartilhar** no painel lateral seja despecido na seguinte imagem:</span><span class="sxs-lookup"><span data-stu-id="e32a1-319">This enables the **Share** button in the sidepanel as depecited in the following image:</span></span>

  ![share_to_stage_during_meeting experiência](~/assets/images/apps-in-meetings/share_to_stage_during_meeting.png)

<span data-ttu-id="e32a1-321">A mudança manifesto necessária para habilitar essa capacidade é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="e32a1-321">The manifest change that is needed to enable this capability is as follows:</span></span> 

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



### <a name="after-a-meeting"></a><span data-ttu-id="e32a1-322">Após uma reunião</span><span class="sxs-lookup"><span data-stu-id="e32a1-322">After a meeting</span></span>

<span data-ttu-id="e32a1-323">As configurações pós-reunião e pré-reunião são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="e32a1-323">The post-meeting and pre-meeting configurations are equivalent.</span></span>

## <a name="code-sample"></a><span data-ttu-id="e32a1-324">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="e32a1-324">Code sample</span></span>

|<span data-ttu-id="e32a1-325">Nome da amostra</span><span class="sxs-lookup"><span data-stu-id="e32a1-325">Sample name</span></span> | <span data-ttu-id="e32a1-326">Descrição</span><span class="sxs-lookup"><span data-stu-id="e32a1-326">Description</span></span> | <span data-ttu-id="e32a1-327">.NET</span><span class="sxs-lookup"><span data-stu-id="e32a1-327">.NET</span></span> | <span data-ttu-id="e32a1-328">Node.js</span><span class="sxs-lookup"><span data-stu-id="e32a1-328">Node.js</span></span> |
|----------------|-----------------|--------------|--------------|
| <span data-ttu-id="e32a1-329">Extensibilidade de reuniões</span><span class="sxs-lookup"><span data-stu-id="e32a1-329">Meetings extensibility</span></span> | <span data-ttu-id="e32a1-330">Microsoft Teams amostra de extensibilidade de reunião para tokens de passagem.</span><span class="sxs-lookup"><span data-stu-id="e32a1-330">Microsoft Teams meeting extensibility sample for passing tokens.</span></span> | [<span data-ttu-id="e32a1-331">View</span><span class="sxs-lookup"><span data-stu-id="e32a1-331">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) | [<span data-ttu-id="e32a1-332">View</span><span class="sxs-lookup"><span data-stu-id="e32a1-332">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/nodejs) |
| <span data-ttu-id="e32a1-333">Meeting content bubble bot</span><span class="sxs-lookup"><span data-stu-id="e32a1-333">Meeting content bubble bot</span></span> | <span data-ttu-id="e32a1-334">Microsoft Teams a amostra de extensibilidade de reunião para interagir com o bot bolha de conteúdo em uma reunião.</span><span class="sxs-lookup"><span data-stu-id="e32a1-334">Microsoft Teams meeting extensibility sample for interacting with content bubble bot in a meeting.</span></span> | [<span data-ttu-id="e32a1-335">View</span><span class="sxs-lookup"><span data-stu-id="e32a1-335">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/csharp) |  [<span data-ttu-id="e32a1-336">View</span><span class="sxs-lookup"><span data-stu-id="e32a1-336">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/nodejs)|
| <span data-ttu-id="e32a1-337">Reunião SidePanel</span><span class="sxs-lookup"><span data-stu-id="e32a1-337">Meeting SidePanel</span></span> | <span data-ttu-id="e32a1-338">Microsoft Teams amostra de extensibilidade de reunião para iteracting com o painel lateral em reunião.</span><span class="sxs-lookup"><span data-stu-id="e32a1-338">Microsoft Teams meeting extensibility sample for iteracting with the side panel in-meeting.</span></span> | [<span data-ttu-id="e32a1-339">View</span><span class="sxs-lookup"><span data-stu-id="e32a1-339">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/csharp) |

## <a name="see-also"></a><span data-ttu-id="e32a1-340">Confira também</span><span class="sxs-lookup"><span data-stu-id="e32a1-340">See also</span></span>

* [<span data-ttu-id="e32a1-341">Diretrizes de design de diálogo em reunião</span><span class="sxs-lookup"><span data-stu-id="e32a1-341">In-meeting dialog design guidelines</span></span>](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
* [<span data-ttu-id="e32a1-342">fluxo de autenticação Teams para guias</span><span class="sxs-lookup"><span data-stu-id="e32a1-342">Teams authentication flow for tabs</span></span>](../tabs/how-to/authentication/auth-flow-tab.md)
