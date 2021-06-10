---
title: Pré-requisitos e referências de API para aplicativos de reuniões do Teams
author: laujan
description: Trabalhar com aplicativos para Teams reuniões
ms.topic: conceptual
ms.author: lajanuar
localization_priority: Normal
keywords: api de função de participante de reuniões de aplicativos do teams
ms.openlocfilehash: f42e827801e21bbd039f52dbb685d4559ae5cf81
ms.sourcegitcommit: 37325179a532897fafbe827dcf9a7ca5fa5e7d0b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2021
ms.locfileid: "52853505"
---
# <a name="prerequisites-and-api-references-for-apps-in-teams-meetings"></a><span data-ttu-id="21ef0-104">Pré-requisitos e referências de API para aplicativos de reuniões do Teams</span><span class="sxs-lookup"><span data-stu-id="21ef0-104">Prerequisites and API references for apps in Teams meetings</span></span>

<span data-ttu-id="21ef0-105">Para expandir os recursos de seus aplicativos no ciclo de vida da reunião, Teams permite que você trabalhe com aplicativos para Teams reuniões.</span><span class="sxs-lookup"><span data-stu-id="21ef0-105">To expand the capabilities of your apps across the meeting lifecycle, Teams enables you to work with apps for Teams meetings.</span></span> <span data-ttu-id="21ef0-106">Você deve passar pelos pré-requisitos e usar as referências da API de aplicativos de reunião para aprimorar a experiência de reunião.</span><span class="sxs-lookup"><span data-stu-id="21ef0-106">You must  go through the prerequisites and you can use the meeting apps API references to enhance the meeting experience.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="21ef0-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="21ef0-107">Prerequisites</span></span>

<span data-ttu-id="21ef0-108">Antes de trabalhar com aplicativos para Teams reuniões, você deve ter uma compreensão do seguinte:</span><span class="sxs-lookup"><span data-stu-id="21ef0-108">Before you work with apps for Teams meetings, you must have an understanding of the following:</span></span>

* <span data-ttu-id="21ef0-109">Você deve ter conhecimento de como desenvolver Teams aplicativos.</span><span class="sxs-lookup"><span data-stu-id="21ef0-109">You must have knowledge of how to develop Teams apps.</span></span> <span data-ttu-id="21ef0-110">Para obter mais informações, [consulte Teams desenvolvimento de aplicativos](../overview.md).</span><span class="sxs-lookup"><span data-stu-id="21ef0-110">For more information, see [Teams app development](../overview.md).</span></span>

* <span data-ttu-id="21ef0-111">Você deve atualizar o manifesto Teams aplicativo para indicar que o aplicativo está disponível para reuniões.</span><span class="sxs-lookup"><span data-stu-id="21ef0-111">You must update the Teams app manifest to indicate that the app is available for meetings.</span></span> <span data-ttu-id="21ef0-112">Para obter mais informações, consulte [manifesto do aplicativo](enable-and-configure-your-app-for-teams-meetings.md#update-your-app-manifest).</span><span class="sxs-lookup"><span data-stu-id="21ef0-112">For more information, see [app manifest](enable-and-configure-your-app-for-teams-meetings.md#update-your-app-manifest).</span></span>

* <span data-ttu-id="21ef0-113">Seu aplicativo deve dar suporte a guias configuráveis no escopo de groupchat, para que seu aplicativo funcione no ciclo de vida da reunião como uma guia. Para obter mais informações, consulte [groupchat scope](../resources/schema/manifest-schema.md#configurabletabs) and [build a group tab](../build-your-first-app/build-channel-tab.md).</span><span class="sxs-lookup"><span data-stu-id="21ef0-113">Your app must support configurable tabs in the groupchat scope, for your app to function in the meeting lifecycle as a tab. For more information, see [groupchat scope](../resources/schema/manifest-schema.md#configurabletabs) and [build a group tab](../build-your-first-app/build-channel-tab.md).</span></span>

* <span data-ttu-id="21ef0-114">Você deve seguir as diretrizes gerais Teams de design de guia para cenários pré e pós-reunião.</span><span class="sxs-lookup"><span data-stu-id="21ef0-114">You must adhere to general Teams tab design guidelines for pre and post-meeting scenarios.</span></span> <span data-ttu-id="21ef0-115">Para experiências durante as reuniões, consulte a guia na reunião e as diretrizes de design da caixa de diálogo na reunião.</span><span class="sxs-lookup"><span data-stu-id="21ef0-115">For experiences during meetings, refer to the in-meeting tab and in-meeting dialog design guidelines.</span></span> <span data-ttu-id="21ef0-116">Para obter mais informações, [consulte Teams](../tabs/design/tabs.md)diretrizes de design de guia, diretrizes de [design](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab)de guia na reunião e diretrizes de design de caixa de diálogo [na reunião.](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)</span><span class="sxs-lookup"><span data-stu-id="21ef0-116">For more information, see [Teams tab design guidelines](../tabs/design/tabs.md), [in-meeting tab design guidelines](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab), and [in-meeting dialog design guidelines](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog).</span></span>

* <span data-ttu-id="21ef0-117">Você deve dar suporte ao escopo para habilitar seu aplicativo em chats de `groupchat` pré-reunião e pós-reunião.</span><span class="sxs-lookup"><span data-stu-id="21ef0-117">You must support the `groupchat` scope to enable your app in pre-meeting and post-meeting chats.</span></span> <span data-ttu-id="21ef0-118">Com a experiência do aplicativo de pré-reunião, você pode encontrar e adicionar aplicativos de reunião e realizar tarefas de pré-reunião.</span><span class="sxs-lookup"><span data-stu-id="21ef0-118">With the pre-meeting app experience, you can find and add meeting apps and perform pre-meeting tasks.</span></span> <span data-ttu-id="21ef0-119">Com a experiência do aplicativo pós-reunião, você pode exibir os resultados da reunião, como resultados da pesquisa ou comentários.</span><span class="sxs-lookup"><span data-stu-id="21ef0-119">With post-meeting app experience, you can view the results of the meeting, such as poll survey results or feedback.</span></span>

* <span data-ttu-id="21ef0-120">Os parâmetros de URL da API de reunião `meetingId` devem ter , e `userId` `tenantId` .</span><span class="sxs-lookup"><span data-stu-id="21ef0-120">Meeting API URL parameters must have `meetingId`, `userId`, and `tenantId`.</span></span> <span data-ttu-id="21ef0-121">Eles estão disponíveis como parte do SDK do cliente Teams atividade de bot.</span><span class="sxs-lookup"><span data-stu-id="21ef0-121">These are available as part of the Teams Client SDK and bot activity.</span></span> <span data-ttu-id="21ef0-122">Além disso, você pode recuperar informações confiáveis para a ID do usuário e a ID do locatário usando [a autenticação SSO da guia](../tabs/how-to/authentication/auth-aad-sso.md).</span><span class="sxs-lookup"><span data-stu-id="21ef0-122">In addition, you can retrieve reliable information for user ID and tenant ID using [tab SSO authentication](../tabs/how-to/authentication/auth-aad-sso.md).</span></span>

* <span data-ttu-id="21ef0-123">A `GetParticipant` API deve ter um registro de bot e uma ID para gerar tokens de auth.</span><span class="sxs-lookup"><span data-stu-id="21ef0-123">The `GetParticipant` API must have a bot registration and ID to generate auth tokens.</span></span> <span data-ttu-id="21ef0-124">Para obter mais informações, [consulte registro de bot e ID](../build-your-first-app/build-bot.md).</span><span class="sxs-lookup"><span data-stu-id="21ef0-124">For more information, see [bot registration and ID](../build-your-first-app/build-bot.md).</span></span>

* <span data-ttu-id="21ef0-125">Para que seu aplicativo seja atualizado em tempo real, ele deve estar atualizado com base nas atividades do evento na reunião.</span><span class="sxs-lookup"><span data-stu-id="21ef0-125">For your app to update in real time, it must be up-to-date based on event activities in the meeting.</span></span> <span data-ttu-id="21ef0-126">Esses eventos podem estar dentro da caixa de diálogo na reunião e em outros estágios no ciclo de vida da reunião.</span><span class="sxs-lookup"><span data-stu-id="21ef0-126">These events can be within the in-meeting dialog box and other stages across the meeting lifecycle.</span></span> <span data-ttu-id="21ef0-127">Para a caixa de diálogo na reunião, consulte o parâmetro completion `bot Id` na `NotificationSignal` API.</span><span class="sxs-lookup"><span data-stu-id="21ef0-127">For the in-meeting dialog box, see completion `bot Id` parameter in `NotificationSignal` API.</span></span>

<span data-ttu-id="21ef0-128">Depois de passar pelos pré-requisitos, você pode usar as referências de API de aplicativos de reunião e isso permite acessar informações usando atributos e exibir `GetUserContext` `GetParticipant` conteúdo `NotificationSignal` relevante.</span><span class="sxs-lookup"><span data-stu-id="21ef0-128">After you have gone through the prerequisites, you can use the meeting apps API references `GetUserContext`, `GetParticipant`, and `NotificationSignal` that enable you to access information using attributes and display relevant content.</span></span>

## <a name="meeting-apps-api-references"></a><span data-ttu-id="21ef0-129">Referências à API de aplicativos de reunião</span><span class="sxs-lookup"><span data-stu-id="21ef0-129">Meeting apps API references</span></span>

<span data-ttu-id="21ef0-130">As novas extensibilidades de reunião fornecem APIs que transformam a experiência de reunião.</span><span class="sxs-lookup"><span data-stu-id="21ef0-130">The new meeting extensibilities provide you with APIs that transform the meeting experience.</span></span> <span data-ttu-id="21ef0-131">Com esse novo recurso, você pode criar aplicativos ou integrar aplicativos existentes no ciclo de vida da reunião.</span><span class="sxs-lookup"><span data-stu-id="21ef0-131">With this new capability, you can build apps or integrate existing apps within the meeting lifecycle.</span></span> <span data-ttu-id="21ef0-132">Você pode usar as APIs para tornar seu aplicativo ciente da reunião.</span><span class="sxs-lookup"><span data-stu-id="21ef0-132">You can use the APIs to make your app aware of the meeting.</span></span> <span data-ttu-id="21ef0-133">Você pode escolher quais APIs deseja usar para aprimorar a experiência de reunião.</span><span class="sxs-lookup"><span data-stu-id="21ef0-133">You can choose which APIs you want to use to enhance the meeting experience.</span></span>

<span data-ttu-id="21ef0-134">A tabela a seguir fornece uma lista dessas APIs:</span><span class="sxs-lookup"><span data-stu-id="21ef0-134">The following table provides a list of these APIs:</span></span>

|<span data-ttu-id="21ef0-135">API</span><span class="sxs-lookup"><span data-stu-id="21ef0-135">API</span></span>|<span data-ttu-id="21ef0-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="21ef0-136">Description</span></span>|<span data-ttu-id="21ef0-137">Solicitação</span><span class="sxs-lookup"><span data-stu-id="21ef0-137">Request</span></span>|<span data-ttu-id="21ef0-138">Source</span><span class="sxs-lookup"><span data-stu-id="21ef0-138">Source</span></span>|
|---|---|----|---|
|<span data-ttu-id="21ef0-139">**GetUserContext**</span><span class="sxs-lookup"><span data-stu-id="21ef0-139">**GetUserContext**</span></span>| <span data-ttu-id="21ef0-140">Essa API permite que você receba informações contextuais para exibir conteúdo relevante em Teams guia.</span><span class="sxs-lookup"><span data-stu-id="21ef0-140">This API enables you to get contextual information to display relevant content in a Teams tab.</span></span> |<span data-ttu-id="21ef0-141">_**microsoftTeams.getContext( ( ) => { /*...\* / } )*\*_</span><span class="sxs-lookup"><span data-stu-id="21ef0-141">_**microsoftTeams.getContext( ( ) => {  /*...*/ } )**_</span></span>|<span data-ttu-id="21ef0-142">Microsoft Teams SDK do cliente</span><span class="sxs-lookup"><span data-stu-id="21ef0-142">Microsoft Teams Client SDK</span></span>|
|<span data-ttu-id="21ef0-143">**GetParticipant**</span><span class="sxs-lookup"><span data-stu-id="21ef0-143">**GetParticipant**</span></span>| <span data-ttu-id="21ef0-144">Essa API permite que um bot busque informações dos participantes por meio da ID da reunião e da ID do participante.</span><span class="sxs-lookup"><span data-stu-id="21ef0-144">This API allows a bot to fetch participant information by meeting ID and participant ID.</span></span> |<span data-ttu-id="21ef0-145">**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_</span><span class="sxs-lookup"><span data-stu-id="21ef0-145">**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_</span></span> |<span data-ttu-id="21ef0-146">Microsoft Bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="21ef0-146">Microsoft Bot Framework SDK</span></span>|
|<span data-ttu-id="21ef0-147">**NotificationSignal**</span><span class="sxs-lookup"><span data-stu-id="21ef0-147">**NotificationSignal**</span></span> | <span data-ttu-id="21ef0-148">Essa API permite que você forneça sinais de reunião que são entregues usando a API de notificação de conversa existente para chat de usuário-bot.</span><span class="sxs-lookup"><span data-stu-id="21ef0-148">This API enables you to provide meeting signals that are delivered using the existing conversation notification API for user-bot chat.</span></span> <span data-ttu-id="21ef0-149">Ele permite sinalizar com base na ação do usuário que mostra uma caixa de diálogo na reunião.</span><span class="sxs-lookup"><span data-stu-id="21ef0-149">It allows you to signal based on user action that shows an in-meeting dialog box.</span></span> |<span data-ttu-id="21ef0-150">**POST** _**/v3/conversations/{conversationId}/activities**_</span><span class="sxs-lookup"><span data-stu-id="21ef0-150">**POST** _**/v3/conversations/{conversationId}/activities**_</span></span>|<span data-ttu-id="21ef0-151">Microsoft Bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="21ef0-151">Microsoft Bot Framework SDK</span></span>|

### <a name="getusercontext-api"></a><span data-ttu-id="21ef0-152">GetUserContext API</span><span class="sxs-lookup"><span data-stu-id="21ef0-152">GetUserContext API</span></span>

<span data-ttu-id="21ef0-153">Para identificar e recuperar informações contextuais para o conteúdo da guia, consulte [obter contexto para](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library)sua Teams guia . `meetingId`é usado por uma guia ao ser executado no contexto da reunião e é adicionado para a carga de resposta.</span><span class="sxs-lookup"><span data-stu-id="21ef0-153">To identify and retrieve contextual information for your tab content, see [get context for your Teams tab](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library). `meetingId` is used by a tab when running in the meeting context and is added for the response payload.</span></span>

### <a name="getparticipant-api"></a><span data-ttu-id="21ef0-154">GetParticipant API</span><span class="sxs-lookup"><span data-stu-id="21ef0-154">GetParticipant API</span></span>

> [!NOTE]
> * <span data-ttu-id="21ef0-155">Não armazenar em cache as funções do participante, pois o organizador da reunião pode alterar as funções a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="21ef0-155">Do not cache participant roles since the meeting organizer can change the roles any time.</span></span>
> * <span data-ttu-id="21ef0-156">Teams atualmente não dá suporte a grandes listas de distribuição ou tamanhos de lista de mais de 350 participantes para a `GetParticipant` API.</span><span class="sxs-lookup"><span data-stu-id="21ef0-156">Teams does not currently support large distribution lists or roster sizes of more than 350 participants for the `GetParticipant` API.</span></span>

<span data-ttu-id="21ef0-157">A `GetParticipant` API permite que um bot busque informações do participante por meio da ID da reunião e da ID do participante.</span><span class="sxs-lookup"><span data-stu-id="21ef0-157">The `GetParticipant` API allows a bot to fetch participant information by meeting ID and participant ID.</span></span> <span data-ttu-id="21ef0-158">A API inclui parâmetros de consulta, exemplos e códigos de resposta.</span><span class="sxs-lookup"><span data-stu-id="21ef0-158">The API includes query parameters, examples, and response codes.</span></span>

#### <a name="query-parameters"></a><span data-ttu-id="21ef0-159">Parâmetros de consulta</span><span class="sxs-lookup"><span data-stu-id="21ef0-159">Query parameters</span></span>

<span data-ttu-id="21ef0-160">A `GetParticipant` API inclui os seguintes parâmetros de consulta:</span><span class="sxs-lookup"><span data-stu-id="21ef0-160">The `GetParticipant` API includes the following query parameters:</span></span>

|<span data-ttu-id="21ef0-161">Valor</span><span class="sxs-lookup"><span data-stu-id="21ef0-161">Value</span></span>|<span data-ttu-id="21ef0-162">Tipo</span><span class="sxs-lookup"><span data-stu-id="21ef0-162">Type</span></span>|<span data-ttu-id="21ef0-163">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="21ef0-163">Required</span></span>|<span data-ttu-id="21ef0-164">Descrição</span><span class="sxs-lookup"><span data-stu-id="21ef0-164">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="21ef0-165">**meetingId**</span><span class="sxs-lookup"><span data-stu-id="21ef0-165">**meetingId**</span></span>| <span data-ttu-id="21ef0-166">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="21ef0-166">String</span></span> | <span data-ttu-id="21ef0-167">Sim</span><span class="sxs-lookup"><span data-stu-id="21ef0-167">Yes</span></span> | <span data-ttu-id="21ef0-168">O identificador de reunião está disponível por meio de Bot Invoke e Teams Client SDK.</span><span class="sxs-lookup"><span data-stu-id="21ef0-168">The meeting identifier is available through Bot Invoke and Teams Client SDK.</span></span>|
|<span data-ttu-id="21ef0-169">**participantId**</span><span class="sxs-lookup"><span data-stu-id="21ef0-169">**participantId**</span></span>| <span data-ttu-id="21ef0-170">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="21ef0-170">String</span></span> | <span data-ttu-id="21ef0-171">Sim</span><span class="sxs-lookup"><span data-stu-id="21ef0-171">Yes</span></span> | <span data-ttu-id="21ef0-172">A ID do participante é a ID do usuário.</span><span class="sxs-lookup"><span data-stu-id="21ef0-172">The participant ID is the user ID.</span></span> <span data-ttu-id="21ef0-173">Ele está disponível em Tab SSO, Bot Invoke e Teams Client SDK.</span><span class="sxs-lookup"><span data-stu-id="21ef0-173">It is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="21ef0-174">É recomendável obter uma ID do participante no SSO da guia.</span><span class="sxs-lookup"><span data-stu-id="21ef0-174">It is recommended to get a participant ID from the Tab SSO.</span></span> |
|<span data-ttu-id="21ef0-175">**tenantId**</span><span class="sxs-lookup"><span data-stu-id="21ef0-175">**tenantId**</span></span>| <span data-ttu-id="21ef0-176">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="21ef0-176">String</span></span> | <span data-ttu-id="21ef0-177">Sim</span><span class="sxs-lookup"><span data-stu-id="21ef0-177">Yes</span></span> | <span data-ttu-id="21ef0-178">A ID do locatário é necessária para os usuários do locatário.</span><span class="sxs-lookup"><span data-stu-id="21ef0-178">The tenant ID is required for the tenant users.</span></span> <span data-ttu-id="21ef0-179">Ele está disponível em Tab SSO, Bot Invoke e Teams Client SDK.</span><span class="sxs-lookup"><span data-stu-id="21ef0-179">It is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="21ef0-180">É recomendável obter uma ID de locatário do SSO de tabulação.</span><span class="sxs-lookup"><span data-stu-id="21ef0-180">It is recommended to get a tenant ID from the Tab SSO.</span></span> |

#### <a name="example"></a><span data-ttu-id="21ef0-181">Exemplo</span><span class="sxs-lookup"><span data-stu-id="21ef0-181">Example</span></span>

<span data-ttu-id="21ef0-182">A `GetParticipant` API inclui os seguintes exemplos:</span><span class="sxs-lookup"><span data-stu-id="21ef0-182">The `GetParticipant` API includes the following examples:</span></span>

# <a name="c"></a>[<span data-ttu-id="21ef0-183">C#</span><span class="sxs-lookup"><span data-stu-id="21ef0-183">C#</span></span>](#tab/dotnet)

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

# <a name="javascript"></a>[<span data-ttu-id="21ef0-184">JavaScript</span><span class="sxs-lookup"><span data-stu-id="21ef0-184">JavaScript</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="21ef0-185">JSON</span><span class="sxs-lookup"><span data-stu-id="21ef0-185">JSON</span></span>](#tab/json)

```http
GET /v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}
```

* * *

<span data-ttu-id="21ef0-186">O corpo de resposta JSON para `GetParticipant` API é:</span><span class="sxs-lookup"><span data-stu-id="21ef0-186">The JSON response body for `GetParticipant` API is:</span></span>

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

#### <a name="response-codes"></a><span data-ttu-id="21ef0-187">Códigos de resposta</span><span class="sxs-lookup"><span data-stu-id="21ef0-187">Response codes</span></span>

<span data-ttu-id="21ef0-188">A `GetParticipant` API inclui os seguintes códigos de resposta:</span><span class="sxs-lookup"><span data-stu-id="21ef0-188">The `GetParticipant` API includes the following response codes:</span></span>

|<span data-ttu-id="21ef0-189">Código da resposta</span><span class="sxs-lookup"><span data-stu-id="21ef0-189">Response code</span></span>|<span data-ttu-id="21ef0-190">Descrição</span><span class="sxs-lookup"><span data-stu-id="21ef0-190">Description</span></span>|
|---|---|
| <span data-ttu-id="21ef0-191">**403**</span><span class="sxs-lookup"><span data-stu-id="21ef0-191">**403**</span></span> | <span data-ttu-id="21ef0-192">O aplicativo não tem permissão para obter informações do participante.</span><span class="sxs-lookup"><span data-stu-id="21ef0-192">The app is not allowed to get participant information.</span></span> <span data-ttu-id="21ef0-193">Essa é a resposta de erro mais comum e é disparada se o aplicativo não estiver instalado na reunião.</span><span class="sxs-lookup"><span data-stu-id="21ef0-193">This is the most common error response and is triggered if the app is not installed in the meeting.</span></span> <span data-ttu-id="21ef0-194">Por exemplo, se o aplicativo for desabilitado pelo administrador do locatário ou bloqueado durante a migração do site ao vivo.</span><span class="sxs-lookup"><span data-stu-id="21ef0-194">For example, if the app is disabled by tenant admin or blocked during live site migration.</span></span>|
| <span data-ttu-id="21ef0-195">**200**</span><span class="sxs-lookup"><span data-stu-id="21ef0-195">**200**</span></span> | <span data-ttu-id="21ef0-196">As informações do participante são recuperadas com êxito.</span><span class="sxs-lookup"><span data-stu-id="21ef0-196">The participant information is successfully retrieved.</span></span>|
| <span data-ttu-id="21ef0-197">**401**</span><span class="sxs-lookup"><span data-stu-id="21ef0-197">**401**</span></span> | <span data-ttu-id="21ef0-198">O aplicativo responde com um token inválido.</span><span class="sxs-lookup"><span data-stu-id="21ef0-198">The app responds with an invalid token.</span></span>|
| <span data-ttu-id="21ef0-199">**404**</span><span class="sxs-lookup"><span data-stu-id="21ef0-199">**404**</span></span> | <span data-ttu-id="21ef0-200">A reunião expirou ou o participante não pode ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="21ef0-200">The meeting has either expired or participant cannot be found.</span></span>|
| <span data-ttu-id="21ef0-201">**500**</span><span class="sxs-lookup"><span data-stu-id="21ef0-201">**500**</span></span> | <span data-ttu-id="21ef0-202">A reunião expirou (mais de 60 dias) desde que a reunião terminou ou os participantes não têm permissões com base em suas funções.</span><span class="sxs-lookup"><span data-stu-id="21ef0-202">The meeting has either expired (more than 60 days) since the meeting ended or the participants do not have permissions based on their role.</span></span>|

### <a name="notificationsignal-api"></a><span data-ttu-id="21ef0-203">NotificationSignal API</span><span class="sxs-lookup"><span data-stu-id="21ef0-203">NotificationSignal API</span></span>

<span data-ttu-id="21ef0-204">Todos os usuários em uma reunião recebem as notificações enviadas por meio da `NotificationSignal` API.</span><span class="sxs-lookup"><span data-stu-id="21ef0-204">All users in a meeting receive the notifications sent through the `NotificationSignal` API.</span></span>

> [!NOTE]
> * <span data-ttu-id="21ef0-205">Quando uma caixa de diálogo na reunião é invocada, o conteúdo é apresentado como uma mensagem de chat.</span><span class="sxs-lookup"><span data-stu-id="21ef0-205">When an in-meeting dialog box is invoked, the content is presented as a chat message.</span></span>
> * <span data-ttu-id="21ef0-206">Atualmente, não há suporte para o envio de notificações direcionadas.</span><span class="sxs-lookup"><span data-stu-id="21ef0-206">Currently, sending targeted notifications is not supported.</span></span>

<span data-ttu-id="21ef0-207">`NotificationSignal` A API permite que você forneça sinais de reunião que são entregues usando a API de notificação de conversa existente para chat usuário-bot.</span><span class="sxs-lookup"><span data-stu-id="21ef0-207">`NotificationSignal` API enables you to provide meeting signals that are delivered using the existing conversation notification API for user-bot chat.</span></span> <span data-ttu-id="21ef0-208">Essa API permite sinalizar com base na ação do usuário que mostra uma caixa de diálogo na reunião.</span><span class="sxs-lookup"><span data-stu-id="21ef0-208">This API allows you to signal based on user action that shows an in-meeting dialog box.</span></span> <span data-ttu-id="21ef0-209">A API inclui parâmetros de consulta, exemplos e códigos de resposta.</span><span class="sxs-lookup"><span data-stu-id="21ef0-209">The API includes query parameter, examples, and response codes.</span></span>

#### <a name="query-parameter"></a><span data-ttu-id="21ef0-210">Parâmetro de consulta</span><span class="sxs-lookup"><span data-stu-id="21ef0-210">Query parameter</span></span>

<span data-ttu-id="21ef0-211">A `NotificationSignal` API inclui o seguinte parâmetro de consulta:</span><span class="sxs-lookup"><span data-stu-id="21ef0-211">The `NotificationSignal` API includes the following query parameter:</span></span>

|<span data-ttu-id="21ef0-212">Valor</span><span class="sxs-lookup"><span data-stu-id="21ef0-212">Value</span></span>|<span data-ttu-id="21ef0-213">Tipo</span><span class="sxs-lookup"><span data-stu-id="21ef0-213">Type</span></span>|<span data-ttu-id="21ef0-214">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="21ef0-214">Required</span></span>|<span data-ttu-id="21ef0-215">Descrição</span><span class="sxs-lookup"><span data-stu-id="21ef0-215">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="21ef0-216">**conversationId**</span><span class="sxs-lookup"><span data-stu-id="21ef0-216">**conversationId**</span></span>| <span data-ttu-id="21ef0-217">String</span><span class="sxs-lookup"><span data-stu-id="21ef0-217">String</span></span> | <span data-ttu-id="21ef0-218">Sim</span><span class="sxs-lookup"><span data-stu-id="21ef0-218">Yes</span></span> | <span data-ttu-id="21ef0-219">O identificador de conversa está disponível como parte de Bot Invoke.</span><span class="sxs-lookup"><span data-stu-id="21ef0-219">The conversation identifier is available as part of Bot Invoke.</span></span> |

#### <a name="examples"></a><span data-ttu-id="21ef0-220">Exemplos</span><span class="sxs-lookup"><span data-stu-id="21ef0-220">Examples</span></span>

<span data-ttu-id="21ef0-221">O `Bot ID` é declarado no manifesto e o bot recebe um objeto de resultado.</span><span class="sxs-lookup"><span data-stu-id="21ef0-221">The `Bot ID` is declared in the manifest and the bot receives a result object.</span></span>

> [!NOTE]
> * <span data-ttu-id="21ef0-222">O `completionBotId` parâmetro do é opcional no exemplo de carga `externalResourceUrl` solicitada.</span><span class="sxs-lookup"><span data-stu-id="21ef0-222">The `completionBotId` parameter of the `externalResourceUrl` is optional in the requested payload example.</span></span> <span data-ttu-id="21ef0-223">`Bot ID` é declarado no manifesto e o bot recebe um objeto de resultado.</span><span class="sxs-lookup"><span data-stu-id="21ef0-223">`Bot ID` is declared in the manifest and the bot receives a result object.</span></span>
> * <span data-ttu-id="21ef0-224">Os `externalResourceUrl` parâmetros de largura e altura devem estar em pixels.</span><span class="sxs-lookup"><span data-stu-id="21ef0-224">The `externalResourceUrl` width and height parameters must be in pixels.</span></span> <span data-ttu-id="21ef0-225">Para garantir que as dimensões estão dentro dos limites permitidos, consulte [diretrizes de design](design/designing-apps-in-meetings.md).</span><span class="sxs-lookup"><span data-stu-id="21ef0-225">To ensure the dimensions are within the allowed limits, see [design guidelines](design/designing-apps-in-meetings.md).</span></span>
> * <span data-ttu-id="21ef0-226">A URL é a página carregada como `<iframe>` uma caixa de diálogo na reunião.</span><span class="sxs-lookup"><span data-stu-id="21ef0-226">The URL is the page loaded as an `<iframe>` in the in-meeting dialog box.</span></span> <span data-ttu-id="21ef0-227">O domínio deve estar na matriz do aplicativo `validDomains` no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="21ef0-227">The domain must be in the app's `validDomains` array in your app manifest.</span></span>

<span data-ttu-id="21ef0-228">A `NotificationSignal` API inclui os seguintes exemplos:</span><span class="sxs-lookup"><span data-stu-id="21ef0-228">The `NotificationSignal` API includes the following examples:</span></span>

# <a name="c"></a>[<span data-ttu-id="21ef0-229">C#</span><span class="sxs-lookup"><span data-stu-id="21ef0-229">C#</span></span>](#tab/dotnet)

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

# <a name="javascript"></a>[<span data-ttu-id="21ef0-230">JavaScript</span><span class="sxs-lookup"><span data-stu-id="21ef0-230">JavaScript</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="21ef0-231">JSON</span><span class="sxs-lookup"><span data-stu-id="21ef0-231">JSON</span></span>](#tab/json)

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

---

#### <a name="response-codes"></a><span data-ttu-id="21ef0-232">Códigos de resposta</span><span class="sxs-lookup"><span data-stu-id="21ef0-232">Response codes</span></span>

<span data-ttu-id="21ef0-233">A `NotificationSignal` API inclui os seguintes códigos de resposta:</span><span class="sxs-lookup"><span data-stu-id="21ef0-233">The `NotificationSignal` API includes the following response codes:</span></span>

|<span data-ttu-id="21ef0-234">Código da resposta</span><span class="sxs-lookup"><span data-stu-id="21ef0-234">Response code</span></span>|<span data-ttu-id="21ef0-235">Descrição</span><span class="sxs-lookup"><span data-stu-id="21ef0-235">Description</span></span>|
|---|---|
| <span data-ttu-id="21ef0-236">**201**</span><span class="sxs-lookup"><span data-stu-id="21ef0-236">**201**</span></span> | <span data-ttu-id="21ef0-237">A atividade com sinal é enviada com êxito.</span><span class="sxs-lookup"><span data-stu-id="21ef0-237">The activity with signal is successfully sent.</span></span> |
| <span data-ttu-id="21ef0-238">**401**</span><span class="sxs-lookup"><span data-stu-id="21ef0-238">**401**</span></span> | <span data-ttu-id="21ef0-239">O aplicativo responde com um token inválido.</span><span class="sxs-lookup"><span data-stu-id="21ef0-239">The app responds with an invalid token.</span></span> |
| <span data-ttu-id="21ef0-240">**403**</span><span class="sxs-lookup"><span data-stu-id="21ef0-240">**403**</span></span> | <span data-ttu-id="21ef0-241">O aplicativo não consegue enviar o sinal.</span><span class="sxs-lookup"><span data-stu-id="21ef0-241">The app is unable to send the signal.</span></span> <span data-ttu-id="21ef0-242">Isso pode acontecer devido a vários motivos, como o administrador de locatários desabilita o aplicativo, o aplicativo é bloqueado durante a migração de site ao vivo e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="21ef0-242">This can happen due to various reasons such as the tenant admin disables the app, the app is blocked during live site migration, and so on.</span></span> <span data-ttu-id="21ef0-243">Nesse caso, a carga contém uma mensagem de erro detalhada.</span><span class="sxs-lookup"><span data-stu-id="21ef0-243">In this case, the payload contains a detailed error message.</span></span> |
| <span data-ttu-id="21ef0-244">**404**</span><span class="sxs-lookup"><span data-stu-id="21ef0-244">**404**</span></span> | <span data-ttu-id="21ef0-245">O chat de reunião não existe.</span><span class="sxs-lookup"><span data-stu-id="21ef0-245">The meeting chat does not exist.</span></span> |

## <a name="code-sample"></a><span data-ttu-id="21ef0-246">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="21ef0-246">Code sample</span></span>

|<span data-ttu-id="21ef0-247">Exemplo de nome</span><span class="sxs-lookup"><span data-stu-id="21ef0-247">Sample name</span></span> | <span data-ttu-id="21ef0-248">Descrição</span><span class="sxs-lookup"><span data-stu-id="21ef0-248">Description</span></span> | <span data-ttu-id="21ef0-249">.NET</span><span class="sxs-lookup"><span data-stu-id="21ef0-249">.NET</span></span> | <span data-ttu-id="21ef0-250">Node.js</span><span class="sxs-lookup"><span data-stu-id="21ef0-250">Node.js</span></span> |
|----------------|-----------------|--------------|--------------|
| <span data-ttu-id="21ef0-251">Extensibilidade de reuniões</span><span class="sxs-lookup"><span data-stu-id="21ef0-251">Meetings extensibility</span></span> | <span data-ttu-id="21ef0-252">Microsoft Teams exemplo de extensibilidade de reunião para tokens de passagem.</span><span class="sxs-lookup"><span data-stu-id="21ef0-252">Microsoft Teams meeting extensibility sample for passing tokens.</span></span> | [<span data-ttu-id="21ef0-253">View</span><span class="sxs-lookup"><span data-stu-id="21ef0-253">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) | [<span data-ttu-id="21ef0-254">View</span><span class="sxs-lookup"><span data-stu-id="21ef0-254">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/nodejs) |
| <span data-ttu-id="21ef0-255">Bot de bolha de conteúdo de reunião</span><span class="sxs-lookup"><span data-stu-id="21ef0-255">Meeting content bubble bot</span></span> | <span data-ttu-id="21ef0-256">Microsoft Teams exemplo de extensibilidade de reunião para interagir com o bot de bolha de conteúdo em uma reunião.</span><span class="sxs-lookup"><span data-stu-id="21ef0-256">Microsoft Teams meeting extensibility sample for interacting with content bubble bot in a meeting.</span></span> | [<span data-ttu-id="21ef0-257">View</span><span class="sxs-lookup"><span data-stu-id="21ef0-257">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/csharp) |  [<span data-ttu-id="21ef0-258">View</span><span class="sxs-lookup"><span data-stu-id="21ef0-258">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/nodejs)|
| <span data-ttu-id="21ef0-259">Meeting meetingSidePanel</span><span class="sxs-lookup"><span data-stu-id="21ef0-259">Meeting meetingSidePanel</span></span> | <span data-ttu-id="21ef0-260">Microsoft Teams exemplo de extensibilidade de reunião para interagir com o painel lateral na reunião.</span><span class="sxs-lookup"><span data-stu-id="21ef0-260">Microsoft Teams meeting extensibility sample for interacting with the side panel in-meeting.</span></span> | [<span data-ttu-id="21ef0-261">View</span><span class="sxs-lookup"><span data-stu-id="21ef0-261">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/csharp) | [<span data-ttu-id="21ef0-262">View</span><span class="sxs-lookup"><span data-stu-id="21ef0-262">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/nodejs)|

## <a name="see-also"></a><span data-ttu-id="21ef0-263">Confira também</span><span class="sxs-lookup"><span data-stu-id="21ef0-263">See also</span></span>

* [<span data-ttu-id="21ef0-264">Diretrizes de design de caixa de diálogo na reunião</span><span class="sxs-lookup"><span data-stu-id="21ef0-264">In-meeting dialog design guidelines</span></span>](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
* [<span data-ttu-id="21ef0-265">Teams fluxo de autenticação para guias</span><span class="sxs-lookup"><span data-stu-id="21ef0-265">Teams authentication flow for tabs</span></span>](../tabs/how-to/authentication/auth-flow-tab.md)
* [<span data-ttu-id="21ef0-266">Aplicativos para Teams reuniões</span><span class="sxs-lookup"><span data-stu-id="21ef0-266">Apps for Teams meetings</span></span>](teams-apps-in-meetings.md)

## <a name="next-step"></a><span data-ttu-id="21ef0-267">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="21ef0-267">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="21ef0-268">Habilitar e configurar seus aplicativos para Teams reuniões</span><span class="sxs-lookup"><span data-stu-id="21ef0-268">Enable and configure your apps for Teams meetings</span></span>](enable-and-configure-your-app-for-teams-meetings.md)
