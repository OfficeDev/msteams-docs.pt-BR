---
title: Pré-requisitos e referências de API para aplicativos de reuniões do Teams
author: surbhigupta
description: Trabalhar com aplicativos para Teams reuniões
ms.topic: conceptual
ms.author: lajanuar
localization_priority: Normal
keywords: api de função de participante de reuniões de aplicativos do teams
ms.openlocfilehash: bc13fa7b8c3af9a7c48463eab7198e908164ffbe
ms.sourcegitcommit: 0a775ae12419f3bc7484e557f4b4ae815bab64ec
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/08/2021
ms.locfileid: "53333684"
---
# <a name="prerequisites-and-api-references-for-apps-in-teams-meetings"></a><span data-ttu-id="7fc7c-104">Pré-requisitos e referências de API para aplicativos de reuniões do Teams</span><span class="sxs-lookup"><span data-stu-id="7fc7c-104">Prerequisites and API references for apps in Teams meetings</span></span>

<span data-ttu-id="7fc7c-105">Para expandir os recursos de seus aplicativos no ciclo de vida da reunião, Teams permite que você trabalhe com aplicativos para Teams reuniões.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-105">To expand the capabilities of your apps across the meeting lifecycle, Teams enables you to work with apps for Teams meetings.</span></span> <span data-ttu-id="7fc7c-106">Você deve passar pelos pré-requisitos e usar as referências da API de aplicativos de reunião para aprimorar a experiência de reunião.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-106">You must  go through the prerequisites and you can use the meeting apps API references to enhance the meeting experience.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7fc7c-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="7fc7c-107">Prerequisites</span></span>

<span data-ttu-id="7fc7c-108">Antes de trabalhar com aplicativos para Teams reuniões, você deve ter uma compreensão do seguinte:</span><span class="sxs-lookup"><span data-stu-id="7fc7c-108">Before you work with apps for Teams meetings, you must have an understanding of the following:</span></span>

* <span data-ttu-id="7fc7c-109">Você deve ter conhecimento de como desenvolver Teams aplicativos.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-109">You must have knowledge of how to develop Teams apps.</span></span> <span data-ttu-id="7fc7c-110">Para obter mais informações, [consulte Teams desenvolvimento de aplicativos](../overview.md).</span><span class="sxs-lookup"><span data-stu-id="7fc7c-110">For more information, see [Teams app development](../overview.md).</span></span>

* <span data-ttu-id="7fc7c-111">Você deve atualizar o manifesto Teams aplicativo para indicar que o aplicativo está disponível para reuniões.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-111">You must update the Teams app manifest to indicate that the app is available for meetings.</span></span> <span data-ttu-id="7fc7c-112">Para obter mais informações, consulte [manifesto do aplicativo](enable-and-configure-your-app-for-teams-meetings.md#update-your-app-manifest).</span><span class="sxs-lookup"><span data-stu-id="7fc7c-112">For more information, see [app manifest](enable-and-configure-your-app-for-teams-meetings.md#update-your-app-manifest).</span></span>

* <span data-ttu-id="7fc7c-113">Seu aplicativo deve dar suporte a guias configuráveis no escopo de groupchat, para que seu aplicativo funcione no ciclo de vida da reunião como uma guia. Para obter mais informações, consulte [groupchat scope](../resources/schema/manifest-schema.md#configurabletabs) and [build a group tab](../build-your-first-app/build-channel-tab.md).</span><span class="sxs-lookup"><span data-stu-id="7fc7c-113">Your app must support configurable tabs in the groupchat scope, for your app to function in the meeting lifecycle as a tab. For more information, see [groupchat scope](../resources/schema/manifest-schema.md#configurabletabs) and [build a group tab](../build-your-first-app/build-channel-tab.md).</span></span>

* <span data-ttu-id="7fc7c-114">Você deve seguir as diretrizes gerais Teams de design de guia para cenários pré e pós-reunião.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-114">You must adhere to general Teams tab design guidelines for pre and post-meeting scenarios.</span></span> <span data-ttu-id="7fc7c-115">Para experiências durante as reuniões, consulte a guia na reunião e as diretrizes de design da caixa de diálogo na reunião.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-115">For experiences during meetings, refer to the in-meeting tab and in-meeting dialog design guidelines.</span></span> <span data-ttu-id="7fc7c-116">Para obter mais informações, [consulte Teams](../tabs/design/tabs.md)diretrizes de design de guia, diretrizes de [design](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab)de guia na reunião e diretrizes de design de caixa de diálogo [na reunião.](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)</span><span class="sxs-lookup"><span data-stu-id="7fc7c-116">For more information, see [Teams tab design guidelines](../tabs/design/tabs.md), [in-meeting tab design guidelines](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab), and [in-meeting dialog design guidelines](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog).</span></span>

* <span data-ttu-id="7fc7c-117">Você deve dar suporte ao escopo para habilitar seu aplicativo em chats de `groupchat` pré-reunião e pós-reunião.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-117">You must support the `groupchat` scope to enable your app in pre-meeting and post-meeting chats.</span></span> <span data-ttu-id="7fc7c-118">Com a experiência do aplicativo de pré-reunião, você pode encontrar e adicionar aplicativos de reunião e realizar tarefas de pré-reunião.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-118">With the pre-meeting app experience, you can find and add meeting apps and perform pre-meeting tasks.</span></span> <span data-ttu-id="7fc7c-119">Com a experiência do aplicativo pós-reunião, você pode exibir os resultados da reunião, como resultados da pesquisa ou comentários.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-119">With post-meeting app experience, you can view the results of the meeting, such as poll survey results or feedback.</span></span>

* <span data-ttu-id="7fc7c-120">Os parâmetros de URL da API de reunião `meetingId` devem ter , e `userId` `tenantId` .</span><span class="sxs-lookup"><span data-stu-id="7fc7c-120">Meeting API URL parameters must have `meetingId`, `userId`, and `tenantId`.</span></span> <span data-ttu-id="7fc7c-121">Eles estão disponíveis como parte do SDK do cliente Teams atividade de bot.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-121">These are available as part of the Teams Client SDK and bot activity.</span></span> <span data-ttu-id="7fc7c-122">Além disso, você pode recuperar informações confiáveis para a ID do usuário e a ID do locatário usando [a autenticação SSO da guia](../tabs/how-to/authentication/auth-aad-sso.md).</span><span class="sxs-lookup"><span data-stu-id="7fc7c-122">In addition, you can retrieve reliable information for user ID and tenant ID using [tab SSO authentication](../tabs/how-to/authentication/auth-aad-sso.md).</span></span>

* <span data-ttu-id="7fc7c-123">A `GetParticipant` API deve ter um registro de bot e uma ID para gerar tokens de auth.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-123">The `GetParticipant` API must have a bot registration and ID to generate auth tokens.</span></span> <span data-ttu-id="7fc7c-124">Para obter mais informações, [consulte registro de bot e ID](../build-your-first-app/build-bot.md).</span><span class="sxs-lookup"><span data-stu-id="7fc7c-124">For more information, see [bot registration and ID](../build-your-first-app/build-bot.md).</span></span>

* <span data-ttu-id="7fc7c-125">Para que seu aplicativo seja atualizado em tempo real, ele deve estar atualizado com base nas atividades do evento na reunião.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-125">For your app to update in real time, it must be up-to-date based on event activities in the meeting.</span></span> <span data-ttu-id="7fc7c-126">Esses eventos podem estar dentro da caixa de diálogo na reunião e em outros estágios no ciclo de vida da reunião.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-126">These events can be within the in-meeting dialog box and other stages across the meeting lifecycle.</span></span> <span data-ttu-id="7fc7c-127">Para a caixa de diálogo na reunião, consulte o parâmetro completion `bot Id` na `NotificationSignal` API.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-127">For the in-meeting dialog box, see completion `bot Id` parameter in `NotificationSignal` API.</span></span>

* <span data-ttu-id="7fc7c-128">A API de Detalhes da Reunião deve ter um registro de bot e uma ID de bot.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-128">Meeting Details API must have a bot registration and bot ID.</span></span> <span data-ttu-id="7fc7c-129">Requer o SDK de Bot para `TurnContext` obter .</span><span class="sxs-lookup"><span data-stu-id="7fc7c-129">It requires Bot SDK to get `TurnContext`.</span></span>

* <span data-ttu-id="7fc7c-130">Para eventos de reunião em tempo real, você deve estar familiarizado com o objeto disponível por meio `TurnContext` do SDK bot.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-130">For real-time meeting events, you must be familiar with the `TurnContext` object available through the Bot SDK.</span></span> <span data-ttu-id="7fc7c-131">O objeto em contém a carga com o início e a `Activity` `TurnContext` hora de término reais.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-131">The `Activity` object in `TurnContext` contains the payload with the actual start and end time.</span></span> <span data-ttu-id="7fc7c-132">Eventos de reunião em tempo real exigem uma ID de bot registrada na plataforma Teams.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-132">Real-time meeting events require a registered bot ID from the Teams platform.</span></span>

<span data-ttu-id="7fc7c-133">Depois de passar pelos pré-requisitos, você pode usar as referências de API de aplicativos de reunião , , e a API de Detalhes da Reunião que permitem que você acesse informações usando atributos e exibir conteúdo `GetUserContext` `GetParticipant` `NotificationSignal` relevante.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-133">After you have gone through the prerequisites, you can use the meeting apps API references `GetUserContext`, `GetParticipant`, `NotificationSignal`, and Meeting Details API that enable you to access information using attributes and display relevant content.</span></span>

## <a name="meeting-apps-api-references"></a><span data-ttu-id="7fc7c-134">Referências à API de aplicativos de reunião</span><span class="sxs-lookup"><span data-stu-id="7fc7c-134">Meeting apps API references</span></span>

<span data-ttu-id="7fc7c-135">As novas extensibilidades de reunião fornecem APIs que transformam a experiência de reunião.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-135">The new meeting extensibilities provide you with APIs that transform the meeting experience.</span></span> <span data-ttu-id="7fc7c-136">Com esse novo recurso, você pode criar aplicativos ou integrar aplicativos existentes no ciclo de vida da reunião.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-136">With this new capability, you can build apps or integrate existing apps within the meeting lifecycle.</span></span> <span data-ttu-id="7fc7c-137">Você pode usar as APIs para tornar seu aplicativo ciente da reunião.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-137">You can use the APIs to make your app aware of the meeting.</span></span> <span data-ttu-id="7fc7c-138">Você pode escolher quais APIs deseja usar para aprimorar a experiência de reunião.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-138">You can choose which APIs you want to use to enhance the meeting experience.</span></span>

<span data-ttu-id="7fc7c-139">A tabela a seguir fornece uma lista dessas APIs:</span><span class="sxs-lookup"><span data-stu-id="7fc7c-139">The following table provides a list of these APIs:</span></span>

|<span data-ttu-id="7fc7c-140">API</span><span class="sxs-lookup"><span data-stu-id="7fc7c-140">API</span></span>|<span data-ttu-id="7fc7c-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="7fc7c-141">Description</span></span>|<span data-ttu-id="7fc7c-142">Solicitação</span><span class="sxs-lookup"><span data-stu-id="7fc7c-142">Request</span></span>|<span data-ttu-id="7fc7c-143">Origem</span><span class="sxs-lookup"><span data-stu-id="7fc7c-143">Source</span></span>|
|---|---|----|---|
|<span data-ttu-id="7fc7c-144">**GetUserContext**</span><span class="sxs-lookup"><span data-stu-id="7fc7c-144">**GetUserContext**</span></span>| <span data-ttu-id="7fc7c-145">Essa API permite que você receba informações contextuais para exibir conteúdo relevante em Teams guia.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-145">This API enables you to get contextual information to display relevant content in a Teams tab.</span></span> |<span data-ttu-id="7fc7c-146">_**microsoftTeams.getContext( ( ) => { /*...\* / } )*\*_</span><span class="sxs-lookup"><span data-stu-id="7fc7c-146">_**microsoftTeams.getContext( ( ) => {  /*...*/ } )**_</span></span>|<span data-ttu-id="7fc7c-147">Microsoft Teams SDK do cliente</span><span class="sxs-lookup"><span data-stu-id="7fc7c-147">Microsoft Teams Client SDK</span></span>|
|<span data-ttu-id="7fc7c-148">**GetParticipant**</span><span class="sxs-lookup"><span data-stu-id="7fc7c-148">**GetParticipant**</span></span>| <span data-ttu-id="7fc7c-149">Essa API permite que um bot busque informações dos participantes por meio da ID da reunião e da ID do participante.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-149">This API allows a bot to fetch participant information by meeting ID and participant ID.</span></span> |<span data-ttu-id="7fc7c-150">**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_</span><span class="sxs-lookup"><span data-stu-id="7fc7c-150">**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_</span></span> |<span data-ttu-id="7fc7c-151">Microsoft Bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="7fc7c-151">Microsoft Bot Framework SDK</span></span>|
|<span data-ttu-id="7fc7c-152">**NotificationSignal**</span><span class="sxs-lookup"><span data-stu-id="7fc7c-152">**NotificationSignal**</span></span> | <span data-ttu-id="7fc7c-153">Essa API permite que você forneça sinais de reunião que são entregues usando a API de notificação de conversa existente para chat de usuário-bot.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-153">This API enables you to provide meeting signals that are delivered using the existing conversation notification API for user-bot chat.</span></span> <span data-ttu-id="7fc7c-154">Ele permite sinalizar com base na ação do usuário que mostra uma caixa de diálogo na reunião.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-154">It allows you to signal based on user action that shows an in-meeting dialog box.</span></span> |<span data-ttu-id="7fc7c-155">**POST** _**/v3/conversations/{conversationId}/activities**_</span><span class="sxs-lookup"><span data-stu-id="7fc7c-155">**POST** _**/v3/conversations/{conversationId}/activities**_</span></span>|<span data-ttu-id="7fc7c-156">Microsoft Bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="7fc7c-156">Microsoft Bot Framework SDK</span></span>|
|<span data-ttu-id="7fc7c-157">**Detalhes da reunião**</span><span class="sxs-lookup"><span data-stu-id="7fc7c-157">**Meeting Details**</span></span> | <span data-ttu-id="7fc7c-158">Essa API permite que você receba metadados de reunião estáticos.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-158">This API enables you to get static meeting metadata.</span></span> |<span data-ttu-id="7fc7c-159">**GET** _**/v1/meetings/{meetingId}**_</span><span class="sxs-lookup"><span data-stu-id="7fc7c-159">**GET** _**/v1/meetings/{meetingId}**_</span></span>| <span data-ttu-id="7fc7c-160">Bot SDK</span><span class="sxs-lookup"><span data-stu-id="7fc7c-160">Bot SDK</span></span> |

### <a name="getusercontext-api"></a><span data-ttu-id="7fc7c-161">GetUserContext API</span><span class="sxs-lookup"><span data-stu-id="7fc7c-161">GetUserContext API</span></span>

<span data-ttu-id="7fc7c-162">Para identificar e recuperar informações contextuais para o conteúdo da guia, consulte [obter contexto para](../tabs/how-to/access-teams-context.md#get-context-by-using-the-microsoft-teams-javascript-library)sua Teams guia . `meetingId`é usado por uma guia ao ser executado no contexto da reunião e é adicionado para a carga de resposta.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-162">To identify and retrieve contextual information for your tab content, see [get context for your Teams tab](../tabs/how-to/access-teams-context.md#get-context-by-using-the-microsoft-teams-javascript-library). `meetingId` is used by a tab when running in the meeting context and is added for the response payload.</span></span>

### <a name="getparticipant-api"></a><span data-ttu-id="7fc7c-163">GetParticipant API</span><span class="sxs-lookup"><span data-stu-id="7fc7c-163">GetParticipant API</span></span>

> [!NOTE]
> * <span data-ttu-id="7fc7c-164">Não armazenar em cache as funções do participante, pois o organizador da reunião pode alterar as funções a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-164">Do not cache participant roles since the meeting organizer can change the roles any time.</span></span>
> * <span data-ttu-id="7fc7c-165">Teams atualmente não dá suporte a grandes listas de distribuição ou tamanhos de lista de mais de 350 participantes para a `GetParticipant` API.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-165">Teams does not currently support large distribution lists or roster sizes of more than 350 participants for the `GetParticipant` API.</span></span>

<span data-ttu-id="7fc7c-166">A `GetParticipant` API permite que um bot busque informações do participante por meio da ID da reunião e da ID do participante.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-166">The `GetParticipant` API allows a bot to fetch participant information by meeting ID and participant ID.</span></span> <span data-ttu-id="7fc7c-167">A API inclui parâmetros de consulta, exemplos e códigos de resposta.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-167">The API includes query parameters, examples, and response codes.</span></span>

#### <a name="query-parameters"></a><span data-ttu-id="7fc7c-168">Parâmetros de consulta</span><span class="sxs-lookup"><span data-stu-id="7fc7c-168">Query parameters</span></span>

<span data-ttu-id="7fc7c-169">A `GetParticipant` API inclui os seguintes parâmetros de consulta:</span><span class="sxs-lookup"><span data-stu-id="7fc7c-169">The `GetParticipant` API includes the following query parameters:</span></span>

|<span data-ttu-id="7fc7c-170">Valor</span><span class="sxs-lookup"><span data-stu-id="7fc7c-170">Value</span></span>|<span data-ttu-id="7fc7c-171">Tipo</span><span class="sxs-lookup"><span data-stu-id="7fc7c-171">Type</span></span>|<span data-ttu-id="7fc7c-172">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="7fc7c-172">Required</span></span>|<span data-ttu-id="7fc7c-173">Descrição</span><span class="sxs-lookup"><span data-stu-id="7fc7c-173">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="7fc7c-174">**meetingId**</span><span class="sxs-lookup"><span data-stu-id="7fc7c-174">**meetingId**</span></span>| <span data-ttu-id="7fc7c-175">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="7fc7c-175">String</span></span> | <span data-ttu-id="7fc7c-176">Sim</span><span class="sxs-lookup"><span data-stu-id="7fc7c-176">Yes</span></span> | <span data-ttu-id="7fc7c-177">O identificador de reunião está disponível por meio de Bot Invoke e Teams Client SDK.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-177">The meeting identifier is available through Bot Invoke and Teams Client SDK.</span></span>|
|<span data-ttu-id="7fc7c-178">**participantId**</span><span class="sxs-lookup"><span data-stu-id="7fc7c-178">**participantId**</span></span>| <span data-ttu-id="7fc7c-179">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="7fc7c-179">String</span></span> | <span data-ttu-id="7fc7c-180">Sim</span><span class="sxs-lookup"><span data-stu-id="7fc7c-180">Yes</span></span> | <span data-ttu-id="7fc7c-181">A ID do participante é a ID do usuário.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-181">The participant ID is the user ID.</span></span> <span data-ttu-id="7fc7c-182">Ele está disponível em Tab SSO, Bot Invoke e Teams Client SDK.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-182">It is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="7fc7c-183">É recomendável obter uma ID do participante no SSO da guia.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-183">It is recommended to get a participant ID from the Tab SSO.</span></span> |
|<span data-ttu-id="7fc7c-184">**tenantId**</span><span class="sxs-lookup"><span data-stu-id="7fc7c-184">**tenantId**</span></span>| <span data-ttu-id="7fc7c-185">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="7fc7c-185">String</span></span> | <span data-ttu-id="7fc7c-186">Sim</span><span class="sxs-lookup"><span data-stu-id="7fc7c-186">Yes</span></span> | <span data-ttu-id="7fc7c-187">A ID do locatário é necessária para os usuários do locatário.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-187">The tenant ID is required for the tenant users.</span></span> <span data-ttu-id="7fc7c-188">Ele está disponível em Tab SSO, Bot Invoke e Teams Client SDK.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-188">It is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="7fc7c-189">É recomendável obter uma ID de locatário do SSO de tabulação.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-189">It is recommended to get a tenant ID from the Tab SSO.</span></span> |

#### <a name="example"></a><span data-ttu-id="7fc7c-190">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7fc7c-190">Example</span></span>

<span data-ttu-id="7fc7c-191">A `GetParticipant` API inclui os seguintes exemplos:</span><span class="sxs-lookup"><span data-stu-id="7fc7c-191">The `GetParticipant` API includes the following examples:</span></span>

# <a name="c"></a>[<span data-ttu-id="7fc7c-192">C#</span><span class="sxs-lookup"><span data-stu-id="7fc7c-192">C#</span></span>](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  TeamsMeetingParticipant participant = await TeamsInfo.GetMeetingParticipantAsync(turnContext, "yourMeetingId", "yourParticipantId", "yourParticipantTenantId").ConfigureAwait(false);
  TeamsChannelAccount member = participant.User;
  MeetingParticipantInfo meetingInfo = participant.Meeting;
  ConversationAccount conversation = participant.Conversation;

  await turnContext.SendActivityAsync(MessageFactory.Text($"The participant role is: {meetingInfo.Role}"), cancellationToken);
}

```

# <a name="javascript"></a>[<span data-ttu-id="7fc7c-193">JavaScript</span><span class="sxs-lookup"><span data-stu-id="7fc7c-193">JavaScript</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="7fc7c-194">JSON</span><span class="sxs-lookup"><span data-stu-id="7fc7c-194">JSON</span></span>](#tab/json)

```http
GET /v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}
```

---

<span data-ttu-id="7fc7c-195">O corpo de resposta JSON para `GetParticipant` API é:</span><span class="sxs-lookup"><span data-stu-id="7fc7c-195">The JSON response body for `GetParticipant` API is:</span></span>

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

#### <a name="response-codes"></a><span data-ttu-id="7fc7c-196">Códigos de resposta</span><span class="sxs-lookup"><span data-stu-id="7fc7c-196">Response codes</span></span>

<span data-ttu-id="7fc7c-197">A `GetParticipant` API retorna os seguintes códigos de resposta:</span><span class="sxs-lookup"><span data-stu-id="7fc7c-197">The `GetParticipant` API returns the following response codes:</span></span>

|<span data-ttu-id="7fc7c-198">Código da resposta</span><span class="sxs-lookup"><span data-stu-id="7fc7c-198">Response code</span></span>|<span data-ttu-id="7fc7c-199">Descrição</span><span class="sxs-lookup"><span data-stu-id="7fc7c-199">Description</span></span>|
|---|---|
| <span data-ttu-id="7fc7c-200">**403**</span><span class="sxs-lookup"><span data-stu-id="7fc7c-200">**403**</span></span> | <span data-ttu-id="7fc7c-201">O aplicativo não tem permissão para obter informações do participante.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-201">The app is not allowed to get participant information.</span></span> <span data-ttu-id="7fc7c-202">Essa é a resposta de erro mais comum e é disparada se o aplicativo não estiver instalado na reunião.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-202">This is the most common error response and is triggered if the app is not installed in the meeting.</span></span> <span data-ttu-id="7fc7c-203">Por exemplo, se o aplicativo for desabilitado pelo administrador do locatário ou bloqueado durante a migração do site ao vivo.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-203">For example, if the app is disabled by tenant admin or blocked during live site migration.</span></span>|
| <span data-ttu-id="7fc7c-204">**200**</span><span class="sxs-lookup"><span data-stu-id="7fc7c-204">**200**</span></span> | <span data-ttu-id="7fc7c-205">As informações do participante são recuperadas com êxito.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-205">The participant information is successfully retrieved.</span></span>|
| <span data-ttu-id="7fc7c-206">**401**</span><span class="sxs-lookup"><span data-stu-id="7fc7c-206">**401**</span></span> | <span data-ttu-id="7fc7c-207">O aplicativo responde com um token inválido.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-207">The app responds with an invalid token.</span></span>|
| <span data-ttu-id="7fc7c-208">**404**</span><span class="sxs-lookup"><span data-stu-id="7fc7c-208">**404**</span></span> | <span data-ttu-id="7fc7c-209">A reunião expirou ou o participante não pode ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-209">The meeting has either expired or participant cannot be found.</span></span>|

### <a name="notificationsignal-api"></a><span data-ttu-id="7fc7c-210">NotificationSignal API</span><span class="sxs-lookup"><span data-stu-id="7fc7c-210">NotificationSignal API</span></span>

<span data-ttu-id="7fc7c-211">Todos os usuários em uma reunião recebem as notificações enviadas por meio da `NotificationSignal` API.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-211">All users in a meeting receive the notifications sent through the `NotificationSignal` API.</span></span>

> [!NOTE]
> * <span data-ttu-id="7fc7c-212">Quando uma caixa de diálogo na reunião é invocada, o conteúdo é apresentado como uma mensagem de chat.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-212">When an in-meeting dialog box is invoked, the content is presented as a chat message.</span></span>
> * <span data-ttu-id="7fc7c-213">Atualmente, não há suporte para o envio de notificações direcionadas.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-213">Currently, sending targeted notifications is not supported.</span></span>

<span data-ttu-id="7fc7c-214">`NotificationSignal` A API permite que você forneça sinais de reunião que são entregues usando a API de notificação de conversa existente para chat usuário-bot.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-214">`NotificationSignal` API enables you to provide meeting signals that are delivered using the existing conversation notification API for user-bot chat.</span></span> <span data-ttu-id="7fc7c-215">Essa API permite sinalizar com base na ação do usuário que mostra uma caixa de diálogo na reunião.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-215">This API allows you to signal based on user action that shows an in-meeting dialog box.</span></span> <span data-ttu-id="7fc7c-216">A API inclui parâmetros de consulta, exemplos e códigos de resposta.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-216">The API includes query parameter, examples, and response codes.</span></span>

#### <a name="query-parameter"></a><span data-ttu-id="7fc7c-217">Parâmetro de consulta</span><span class="sxs-lookup"><span data-stu-id="7fc7c-217">Query parameter</span></span>

<span data-ttu-id="7fc7c-218">A `NotificationSignal` API inclui o seguinte parâmetro de consulta:</span><span class="sxs-lookup"><span data-stu-id="7fc7c-218">The `NotificationSignal` API includes the following query parameter:</span></span>

|<span data-ttu-id="7fc7c-219">Valor</span><span class="sxs-lookup"><span data-stu-id="7fc7c-219">Value</span></span>|<span data-ttu-id="7fc7c-220">Tipo</span><span class="sxs-lookup"><span data-stu-id="7fc7c-220">Type</span></span>|<span data-ttu-id="7fc7c-221">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="7fc7c-221">Required</span></span>|<span data-ttu-id="7fc7c-222">Descrição</span><span class="sxs-lookup"><span data-stu-id="7fc7c-222">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="7fc7c-223">**conversationId**</span><span class="sxs-lookup"><span data-stu-id="7fc7c-223">**conversationId**</span></span>| <span data-ttu-id="7fc7c-224">String</span><span class="sxs-lookup"><span data-stu-id="7fc7c-224">String</span></span> | <span data-ttu-id="7fc7c-225">Sim</span><span class="sxs-lookup"><span data-stu-id="7fc7c-225">Yes</span></span> | <span data-ttu-id="7fc7c-226">O identificador de conversa está disponível como parte de Bot Invoke.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-226">The conversation identifier is available as part of Bot Invoke.</span></span> |

#### <a name="examples"></a><span data-ttu-id="7fc7c-227">Exemplos</span><span class="sxs-lookup"><span data-stu-id="7fc7c-227">Examples</span></span>

<span data-ttu-id="7fc7c-228">O `Bot ID` é declarado no manifesto e o bot recebe um objeto de resultado.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-228">The `Bot ID` is declared in the manifest and the bot receives a result object.</span></span>

> [!NOTE]
> * <span data-ttu-id="7fc7c-229">O `completionBotId` parâmetro do é opcional no exemplo de carga `externalResourceUrl` solicitada.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-229">The `completionBotId` parameter of the `externalResourceUrl` is optional in the requested payload example.</span></span> <span data-ttu-id="7fc7c-230">`Bot ID` é declarado no manifesto e o bot recebe um objeto de resultado.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-230">`Bot ID` is declared in the manifest and the bot receives a result object.</span></span>
> * <span data-ttu-id="7fc7c-231">Os `externalResourceUrl` parâmetros de largura e altura devem estar em pixels.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-231">The `externalResourceUrl` width and height parameters must be in pixels.</span></span> <span data-ttu-id="7fc7c-232">Para garantir que as dimensões estão dentro dos limites permitidos, consulte [diretrizes de design](design/designing-apps-in-meetings.md).</span><span class="sxs-lookup"><span data-stu-id="7fc7c-232">To ensure the dimensions are within the allowed limits, see [design guidelines](design/designing-apps-in-meetings.md).</span></span>
> * <span data-ttu-id="7fc7c-233">A URL é a página carregada como `<iframe>` uma caixa de diálogo na reunião.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-233">The URL is the page loaded as an `<iframe>` in the in-meeting dialog box.</span></span> <span data-ttu-id="7fc7c-234">O domínio deve estar na matriz do aplicativo `validDomains` no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-234">The domain must be in the app's `validDomains` array in your app manifest.</span></span>

<span data-ttu-id="7fc7c-235">A `NotificationSignal` API inclui os seguintes exemplos:</span><span class="sxs-lookup"><span data-stu-id="7fc7c-235">The `NotificationSignal` API includes the following examples:</span></span>

# <a name="c"></a>[<span data-ttu-id="7fc7c-236">C#</span><span class="sxs-lookup"><span data-stu-id="7fc7c-236">C#</span></span>](#tab/dotnet)

```csharp
Activity activity = MessageFactory.Text("This is a meeting signal test");
activity.TeamsNotifyUser(true, "https://teams.microsoft.com/l/bubble/APP_ID?url=<url>&height=<height>&width=<width>&title=<title>&completionBotId=BOT_APP_ID");
await turnContext.SendActivityAsync(activity).ConfigureAwait(false);
```

# <a name="javascript"></a>[<span data-ttu-id="7fc7c-237">JavaScript</span><span class="sxs-lookup"><span data-stu-id="7fc7c-237">JavaScript</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="7fc7c-238">JSON</span><span class="sxs-lookup"><span data-stu-id="7fc7c-238">JSON</span></span>](#tab/json)

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

#### <a name="response-codes"></a><span data-ttu-id="7fc7c-239">Códigos de resposta</span><span class="sxs-lookup"><span data-stu-id="7fc7c-239">Response codes</span></span>

<span data-ttu-id="7fc7c-240">A `NotificationSignal` API inclui os seguintes códigos de resposta:</span><span class="sxs-lookup"><span data-stu-id="7fc7c-240">The `NotificationSignal` API includes the following response codes:</span></span>

|<span data-ttu-id="7fc7c-241">Código da resposta</span><span class="sxs-lookup"><span data-stu-id="7fc7c-241">Response code</span></span>|<span data-ttu-id="7fc7c-242">Descrição</span><span class="sxs-lookup"><span data-stu-id="7fc7c-242">Description</span></span>|
|---|---|
| <span data-ttu-id="7fc7c-243">**201**</span><span class="sxs-lookup"><span data-stu-id="7fc7c-243">**201**</span></span> | <span data-ttu-id="7fc7c-244">A atividade com sinal é enviada com êxito.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-244">The activity with signal is successfully sent.</span></span> |
| <span data-ttu-id="7fc7c-245">**401**</span><span class="sxs-lookup"><span data-stu-id="7fc7c-245">**401**</span></span> | <span data-ttu-id="7fc7c-246">O aplicativo responde com um token inválido.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-246">The app responds with an invalid token.</span></span> |
| <span data-ttu-id="7fc7c-247">**403**</span><span class="sxs-lookup"><span data-stu-id="7fc7c-247">**403**</span></span> | <span data-ttu-id="7fc7c-248">O aplicativo não consegue enviar o sinal.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-248">The app is unable to send the signal.</span></span> <span data-ttu-id="7fc7c-249">Isso pode acontecer devido a vários motivos, como o administrador de locatários desabilita o aplicativo, o aplicativo é bloqueado durante a migração de site ao vivo e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-249">This can happen due to various reasons such as the tenant admin disables the app, the app is blocked during live site migration, and so on.</span></span> <span data-ttu-id="7fc7c-250">Nesse caso, a carga contém uma mensagem de erro detalhada.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-250">In this case, the payload contains a detailed error message.</span></span> |
| <span data-ttu-id="7fc7c-251">**404**</span><span class="sxs-lookup"><span data-stu-id="7fc7c-251">**404**</span></span> | <span data-ttu-id="7fc7c-252">O chat de reunião não existe.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-252">The meeting chat does not exist.</span></span> |

### <a name="meeting-details-api"></a><span data-ttu-id="7fc7c-253">API de Detalhes da Reunião</span><span class="sxs-lookup"><span data-stu-id="7fc7c-253">Meeting Details API</span></span>

> [!NOTE]
> <span data-ttu-id="7fc7c-254">Esse recurso está disponível apenas na [visualização de desenvolvedor](../resources/dev-preview/developer-preview-intro.md) público.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-254">This feature is currently available in [public developer preview](../resources/dev-preview/developer-preview-intro.md) only.</span></span>

<span data-ttu-id="7fc7c-255">A API Detalhes da Reunião permite que seu aplicativo receba metadados de reunião estáticos.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-255">The Meeting Details API enables your app to get static meeting metadata.</span></span> <span data-ttu-id="7fc7c-256">Esses são pontos de dados que não mudam dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-256">These are data points that do not change dynamically.</span></span>
<span data-ttu-id="7fc7c-257">A API está disponível por meio dos Serviços bot.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-257">The API is available through Bot Services.</span></span>

#### <a name="prerequisite"></a><span data-ttu-id="7fc7c-258">Pré-requisito</span><span class="sxs-lookup"><span data-stu-id="7fc7c-258">Prerequisite</span></span>

<span data-ttu-id="7fc7c-259">Para usar a API de Detalhes da Reunião, você deve obter permissões RSC.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-259">To use the Meeting Details API, you must obtain RSC permissions.</span></span> <span data-ttu-id="7fc7c-260">Use o exemplo a seguir para configurar a propriedade do manifesto do `webApplicationInfo` aplicativo:</span><span class="sxs-lookup"><span data-stu-id="7fc7c-260">Use the following example to configure your app manifest's `webApplicationInfo` property:</span></span>

```json
"webApplicationInfo": {
    "id": "<bot id>",
    "resource": "https://RscPermission",
    "applicationPermissions": [
      "OnlineMeeting.ReadBasic.Chat"
    ]
}
 ```
 
#### <a name="query-parameter"></a><span data-ttu-id="7fc7c-261">Parâmetro de consulta</span><span class="sxs-lookup"><span data-stu-id="7fc7c-261">Query parameter</span></span>

<span data-ttu-id="7fc7c-262">A API De Detalhes da Reunião inclui o seguinte parâmetro de consulta:</span><span class="sxs-lookup"><span data-stu-id="7fc7c-262">The Meeting Details API includes the following query parameter:</span></span>

|<span data-ttu-id="7fc7c-263">Valor</span><span class="sxs-lookup"><span data-stu-id="7fc7c-263">Value</span></span>|<span data-ttu-id="7fc7c-264">Tipo</span><span class="sxs-lookup"><span data-stu-id="7fc7c-264">Type</span></span>|<span data-ttu-id="7fc7c-265">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="7fc7c-265">Required</span></span>|<span data-ttu-id="7fc7c-266">Descrição</span><span class="sxs-lookup"><span data-stu-id="7fc7c-266">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="7fc7c-267">**meetingId**</span><span class="sxs-lookup"><span data-stu-id="7fc7c-267">**meetingId**</span></span>| <span data-ttu-id="7fc7c-268">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="7fc7c-268">String</span></span> | <span data-ttu-id="7fc7c-269">Sim</span><span class="sxs-lookup"><span data-stu-id="7fc7c-269">Yes</span></span> | <span data-ttu-id="7fc7c-270">O identificador de reunião está disponível por meio de Bot Invoke e Teams Client SDK.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-270">The meeting identifier is available through Bot Invoke and Teams Client SDK.</span></span> |

#### <a name="example"></a><span data-ttu-id="7fc7c-271">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7fc7c-271">Example</span></span>

<span data-ttu-id="7fc7c-272">A API De Detalhes da Reunião inclui os seguintes exemplos:</span><span class="sxs-lookup"><span data-stu-id="7fc7c-272">The Meeting Details API includes the following examples:</span></span>

# <a name="c"></a>[<span data-ttu-id="7fc7c-273">C#</span><span class="sxs-lookup"><span data-stu-id="7fc7c-273">C#</span></span>](#tab/dotnet)

```csharp
var connectorClient = turnContext.TurnState.Get<IConnectorClient>();
var creds = connectorClient.Credentials as AppCredentials;
var bearerToken = await creds.GetTokenAsync().ConfigureAwait(false);
var request = new HttpRequestMessage(HttpMethod.Get, new Uri(new Uri(connectorClient.BaseUri.OriginalString), $"v1/meetings/{meetingId}"));
request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", bearerToken);
HttpResponseMessage response = await (connectorClient as ServiceClient<ConnectorClient>).HttpClient.SendAsync(request, CancellationToken.None).ConfigureAwait(false);
string content;
if (response.Content != null)
{
    content = await response.Content.ReadAsStringAsync().ConfigureAwait(false);
}
```

# <a name="javascript"></a>[<span data-ttu-id="7fc7c-274">JavaScript</span><span class="sxs-lookup"><span data-stu-id="7fc7c-274">JavaScript</span></span>](#tab/javascript)

<span data-ttu-id="7fc7c-275">Não disponível</span><span class="sxs-lookup"><span data-stu-id="7fc7c-275">Not available</span></span>

# <a name="json"></a>[<span data-ttu-id="7fc7c-276">JSON</span><span class="sxs-lookup"><span data-stu-id="7fc7c-276">JSON</span></span>](#tab/json)

```http
GET /v1/meetings/{meetingId}
```

---

<span data-ttu-id="7fc7c-277">O corpo da resposta JSON para a API de Detalhes da Reunião é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="7fc7c-277">The JSON response body for Meeting Details API is as follows:</span></span>

```json
{ 
   "details": { 
        "id": "meeting ID", 
        "msGraphResourceId": "", 
        "scheduledStartTime": "2020-08-21T02:30:00+00:00", 
        "scheduledEndTime": "2020-08-21T03:00:00+00:00", 
        "joinUrl": "https://teams.microsoft.com/l/xx", 
        "title": "All Hands", 
        "type": "Scheduled" 
    }, 
    "conversation": { 
            "isGroup": true, 
            “conversationType”: “groupchat”, 
            "id": "meeting chat ID" 
    }, 
    "organizer": { 
        "id": "<organizer user ID>", 
        "aadObjectId": "<AAD ID>", 
        "tenantId": "<Tenant ID>" 
    }
} 
```

## <a name="real-time-teams-meeting-events"></a><span data-ttu-id="7fc7c-278">Eventos de reunião Teams em tempo real</span><span class="sxs-lookup"><span data-stu-id="7fc7c-278">Real-time Teams meeting events</span></span>

> [!NOTE]
> <span data-ttu-id="7fc7c-279">Esse recurso está disponível apenas na [visualização de desenvolvedor](../resources/dev-preview/developer-preview-intro.md) público.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-279">This feature is currently available in [public developer preview](../resources/dev-preview/developer-preview-intro.md) only.</span></span>

<span data-ttu-id="7fc7c-280">O usuário pode receber eventos de reunião em tempo real.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-280">The user can receive real-time meeting events.</span></span> <span data-ttu-id="7fc7c-281">Assim que qualquer aplicativo é associado a uma reunião, o início real da reunião e a hora de término da reunião são compartilhados com o bot.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-281">As soon as any app is associated with a meeting, the actual meeting start and meeting end time are shared with the bot.</span></span>

<span data-ttu-id="7fc7c-282">A hora real de início e término de uma reunião é diferente da hora de início e término agendada.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-282">Actual start and end time of a meeting are different from the scheduled start and end time.</span></span> <span data-ttu-id="7fc7c-283">A API de detalhes da reunião fornece a hora de início e término agendada enquanto o evento fornece a hora real de início e término.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-283">The meeting details API provides the scheduled start and end time while the event provides the actual start and end time.</span></span>

### <a name="prerequisite"></a><span data-ttu-id="7fc7c-284">Pré-requisito</span><span class="sxs-lookup"><span data-stu-id="7fc7c-284">Prerequisite</span></span>

<span data-ttu-id="7fc7c-285">O manifesto do aplicativo deve ter a `webApplicationInfo` propriedade para receber os eventos de início e término da reunião.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-285">Your app manifest must have the `webApplicationInfo` property to receive the meeting start and end events.</span></span> <span data-ttu-id="7fc7c-286">Use o exemplo a seguir para configurar seu manifesto:</span><span class="sxs-lookup"><span data-stu-id="7fc7c-286">Use the following example to configure your manifest:</span></span>

```json
"webApplicationInfo": {
    "id": "<bot id>",
    "resource": "https://RscPermission",
    "applicationPermissions": [
      "OnlineMeeting.ReadBasic.Chat"
    ]
}
 ```

### <a name="example-of-meeting-start-event-payload"></a><span data-ttu-id="7fc7c-287">Exemplo de carga do evento de início da reunião</span><span class="sxs-lookup"><span data-stu-id="7fc7c-287">Example of meeting start event payload</span></span>

<span data-ttu-id="7fc7c-288">O código a seguir fornece um exemplo de carga de evento de início de reunião:</span><span class="sxs-lookup"><span data-stu-id="7fc7c-288">The following code provides an example of meeting start event payload:</span></span>

```json
{ 
    "name": "application/vnd.microsoft.meetingStart", 
    "type": "event", 
    "timestamp": "2021-04-29T16:10:41.1252256Z", 
    "id": "123", 
    "channelId": "msteams", 
    "serviceUrl": "https://microsoft.com", 
    "from": { 
        "id": "userID", 
        "aadObjectId": "aadOnjectId" 
    }, 
    "conversation": { 
        "isGroup": true, 
        "tenantId": "tenantId", 
        "id": "thread id" 
    }, 
    "recipient": { 
        "id": "user Id", 
        "name": "user name" 
    }, 
    "entities": [ 
        { 
            "locale": "en-US", 
            "country": "US", 
            "type": "clientInfo" 
        } 
    ], 
    "channelData": { 
        "tenant": { 
            "id": "channel id" 
        }, 
        "source": null, 
        "meeting": { 
            "id": "meeting id" 
        } 
    }, 
    "value": { 
        "MeetingType": "Scheduled", 
        "Title": "Meeting Start/End Event", 
        "Id":"meeting id", 
        "JoinUrl": "url" 
        "StartTime": "2021-04-29T16:17:17.4388966Z" 
    }, 
    "locale": "en-US" 
}
```

### <a name="example-of-meeting-end-event-payload"></a><span data-ttu-id="7fc7c-289">Exemplo de carga de evento final de reunião</span><span class="sxs-lookup"><span data-stu-id="7fc7c-289">Example of meeting end event payload</span></span>

<span data-ttu-id="7fc7c-290">O código a seguir fornece um exemplo de carga de evento final de reunião:</span><span class="sxs-lookup"><span data-stu-id="7fc7c-290">The following code provides an example of meeting end event payload:</span></span>

```json
{ 
    "name": "application/vnd.microsoft.meetingEnd", 
    "type": "event", 
    "timestamp": "2021-04-29T16:17:17.4388966Z", 
    "id": "123", 
    "channelId": "msteams", 
    "serviceUrl": "https://microsoft.com", 
    "from": { 
        "id": "user id", 
        "aadObjectId": "aadObjectId" 
    }, 
    "conversation": { 
        "isGroup": true, 
        "tenantId": "tenantId", 
        "id": "thread id" 
    }, 
    "recipient": { 
        "id": "user id", 
        "name": "user name" 
    }, 
    "entities": [ 
        { 
            "locale": "en-US", 
            "country": "US", 
            "type": "clientInfo" 
        } 
    ], 
    "channelData": { 
        "tenant": { 
            "id": "channel id" 
        }, 
        "source": null, 
        "meeting": { 
            "id": "meeting Id" 
        } 
    }, 
    "value": { 
        "MeetingType": "Scheduled", 
        "Title": "Meeting Start/End Event in Canary", 
        "Id": "19:meeting_NTM3ZDJjOTUtZGRhOS00MzYxLTk5NDAtMzY4M2IzZWFjZGE1@thread.v2", 
        "JoinUrl": "url", 
        "EndTime": "2021-04-29T16:17:17.4388966Z" 
    }, 
    "locale": "en-US" 
}
```

### <a name="example-of-getting-metadata-of-a-meeting"></a><span data-ttu-id="7fc7c-291">Exemplo de obter metadados de uma reunião</span><span class="sxs-lookup"><span data-stu-id="7fc7c-291">Example of getting metadata of a meeting</span></span>

<span data-ttu-id="7fc7c-292">Seu bot recebe o evento por meio do `OnEventActivityAsync` manipulador.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-292">Your bot receives the event through the `OnEventActivityAsync` handler.</span></span>

<span data-ttu-id="7fc7c-293">Para desserializar a carga json, um objeto modelo é introduzido para obter os metadados de uma reunião.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-293">To deserialize the json payload, a model object is introduced to get the metadata of a meeting.</span></span> <span data-ttu-id="7fc7c-294">Os metadados de uma reunião residem na `value` propriedade na carga do evento.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-294">The metadata of a meeting resides in the `value` property in the event payload.</span></span> <span data-ttu-id="7fc7c-295">O `MeetingStartEndEventvalue` objeto model é criado, cujas variáveis de membro correspondem às chaves sob a propriedade na carga do `value` evento.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-295">The `MeetingStartEndEventvalue` model object is created, whose member variables correspond to the keys under the `value` property in the event payload.</span></span>

<span data-ttu-id="7fc7c-296">O código a seguir mostra como capturar os metadados de uma reunião que é , , , , e de um evento de início e fim de `MeetingType` `Title` `Id` `JoinUrl` `StartTime` `EndTime` reunião:</span><span class="sxs-lookup"><span data-stu-id="7fc7c-296">The following code shows how to capture the metadata of a meeting that is `MeetingType`, `Title`, `Id`, `JoinUrl`, `StartTime`, and `EndTime` from a meeting start and end event:</span></span>

```csharp
protected override async Task OnEventActivityAsync(
ITurnContext<IEventActivity> turnContext, CancellationToken cancellationToken)
{
    // Event Name is either 'application/vnd.microsoft.meetingStart' or 'application/vnd.microsoft.meetingEnd'
    var meetingEventName = turnContext.Activity.Name;
    // Value contains meeting information (ex: meeting type, start time, etc).
    var meetingEventInfo = turnContext.Activity.Value as JObject; 
    var meetingEventInfoObject =
meetingEventInfo.ToObject<MeetingStartEndEventValue>();
    // Create a very simple adaptive card with meeting information
var attachmentCard = createMeetingStartOrEndEventAttachment(meetingEventName,
meetingEventInfoObject);
    await turnContext.SendActivityAsync(MessageFactory.Attachment(attachmentCard));
}
```

<span data-ttu-id="7fc7c-297">MeetingStartEndEventvalue.cs inclui o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="7fc7c-297">The MeetingStartEndEventvalue.cs includes the following code:</span></span>

```csharp
public class MeetingStartEndEventValue
{
    public string Id { get; set; }
    public string Title { get; set; }
    public string MeetingType { get; set; }
    public string JoinUrl { get; set; }
    public string StartTime { get; set; }
    public string EndTime { get; set; }
}
```

## <a name="code-sample"></a><span data-ttu-id="7fc7c-298">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="7fc7c-298">Code sample</span></span>

|<span data-ttu-id="7fc7c-299">Exemplo de nome</span><span class="sxs-lookup"><span data-stu-id="7fc7c-299">Sample name</span></span> | <span data-ttu-id="7fc7c-300">Descrição</span><span class="sxs-lookup"><span data-stu-id="7fc7c-300">Description</span></span> | <span data-ttu-id="7fc7c-301">.NET</span><span class="sxs-lookup"><span data-stu-id="7fc7c-301">.NET</span></span> | <span data-ttu-id="7fc7c-302">Node.js</span><span class="sxs-lookup"><span data-stu-id="7fc7c-302">Node.js</span></span> |
|----------------|-----------------|--------------|--------------|
| <span data-ttu-id="7fc7c-303">Extensibilidade de reuniões</span><span class="sxs-lookup"><span data-stu-id="7fc7c-303">Meetings extensibility</span></span> | <span data-ttu-id="7fc7c-304">Microsoft Teams exemplo de extensibilidade de reunião para tokens de passagem.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-304">Microsoft Teams meeting extensibility sample for passing tokens.</span></span> | [<span data-ttu-id="7fc7c-305">View</span><span class="sxs-lookup"><span data-stu-id="7fc7c-305">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) | [<span data-ttu-id="7fc7c-306">View</span><span class="sxs-lookup"><span data-stu-id="7fc7c-306">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/nodejs) |
| <span data-ttu-id="7fc7c-307">Bot de bolha de conteúdo de reunião</span><span class="sxs-lookup"><span data-stu-id="7fc7c-307">Meeting content bubble bot</span></span> | <span data-ttu-id="7fc7c-308">Microsoft Teams exemplo de extensibilidade de reunião para interagir com o bot de bolha de conteúdo em uma reunião.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-308">Microsoft Teams meeting extensibility sample for interacting with content bubble bot in a meeting.</span></span> | [<span data-ttu-id="7fc7c-309">View</span><span class="sxs-lookup"><span data-stu-id="7fc7c-309">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/csharp) |  [<span data-ttu-id="7fc7c-310">View</span><span class="sxs-lookup"><span data-stu-id="7fc7c-310">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/nodejs)|
| <span data-ttu-id="7fc7c-311">Meeting meetingSidePanel</span><span class="sxs-lookup"><span data-stu-id="7fc7c-311">Meeting meetingSidePanel</span></span> | <span data-ttu-id="7fc7c-312">Microsoft Teams exemplo de extensibilidade de reunião para interagir com o painel lateral na reunião.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-312">Microsoft Teams meeting extensibility sample for interacting with the side panel in-meeting.</span></span> | [<span data-ttu-id="7fc7c-313">View</span><span class="sxs-lookup"><span data-stu-id="7fc7c-313">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/csharp) | [<span data-ttu-id="7fc7c-314">View</span><span class="sxs-lookup"><span data-stu-id="7fc7c-314">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/nodejs)|
| <span data-ttu-id="7fc7c-315">Guia Detalhes na Reunião</span><span class="sxs-lookup"><span data-stu-id="7fc7c-315">Details Tab in Meeting</span></span> | <span data-ttu-id="7fc7c-316">Microsoft Teams exemplo de extensibilidade de reunião para a iteração com a Guia Detalhes em reunião.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-316">Microsoft Teams meeting extensibility sample for iteracting with Details Tab in-meeting.</span></span> | [<span data-ttu-id="7fc7c-317">View</span><span class="sxs-lookup"><span data-stu-id="7fc7c-317">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-details-tab/csharp) | [<span data-ttu-id="7fc7c-318">View</span><span class="sxs-lookup"><span data-stu-id="7fc7c-318">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-details-tab/nodejs)|

## <a name="see-also"></a><span data-ttu-id="7fc7c-319">Confira também</span><span class="sxs-lookup"><span data-stu-id="7fc7c-319">See also</span></span>

* [<span data-ttu-id="7fc7c-320">Diretrizes de design de caixa de diálogo na reunião</span><span class="sxs-lookup"><span data-stu-id="7fc7c-320">In-meeting dialog design guidelines</span></span>](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
* [<span data-ttu-id="7fc7c-321">Teams fluxo de autenticação para guias</span><span class="sxs-lookup"><span data-stu-id="7fc7c-321">Teams authentication flow for tabs</span></span>](../tabs/how-to/authentication/auth-flow-tab.md)
* [<span data-ttu-id="7fc7c-322">Aplicativos para Teams reuniões</span><span class="sxs-lookup"><span data-stu-id="7fc7c-322">Apps for Teams meetings</span></span>](teams-apps-in-meetings.md)

## <a name="next-step"></a><span data-ttu-id="7fc7c-323">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="7fc7c-323">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7fc7c-324">Habilitar e configurar seus aplicativos para Teams reuniões</span><span class="sxs-lookup"><span data-stu-id="7fc7c-324">Enable and configure your apps for Teams meetings</span></span>](enable-and-configure-your-app-for-teams-meetings.md)
