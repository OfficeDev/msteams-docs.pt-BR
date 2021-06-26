---
title: Pré-requisitos e referências de API para aplicativos de reuniões do Teams
author: surbhigupta
description: Trabalhar com aplicativos para Teams reuniões
ms.topic: conceptual
ms.author: lajanuar
localization_priority: Normal
keywords: api de função de participante de reuniões de aplicativos do teams
ms.openlocfilehash: da67b447644242caccf5f3a7cfe8d9435286787c
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2021
ms.locfileid: "53139988"
---
# <a name="prerequisites-and-api-references-for-apps-in-teams-meetings"></a><span data-ttu-id="9e0b0-104">Pré-requisitos e referências de API para aplicativos de reuniões do Teams</span><span class="sxs-lookup"><span data-stu-id="9e0b0-104">Prerequisites and API references for apps in Teams meetings</span></span>

<span data-ttu-id="9e0b0-105">Para expandir os recursos de seus aplicativos no ciclo de vida da reunião, Teams permite que você trabalhe com aplicativos para Teams reuniões.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-105">To expand the capabilities of your apps across the meeting lifecycle, Teams enables you to work with apps for Teams meetings.</span></span> <span data-ttu-id="9e0b0-106">Você deve passar pelos pré-requisitos e usar as referências da API de aplicativos de reunião para aprimorar a experiência de reunião.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-106">You must  go through the prerequisites and you can use the meeting apps API references to enhance the meeting experience.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9e0b0-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="9e0b0-107">Prerequisites</span></span>

<span data-ttu-id="9e0b0-108">Antes de trabalhar com aplicativos para Teams reuniões, você deve ter uma compreensão do seguinte:</span><span class="sxs-lookup"><span data-stu-id="9e0b0-108">Before you work with apps for Teams meetings, you must have an understanding of the following:</span></span>

* <span data-ttu-id="9e0b0-109">Você deve ter conhecimento de como desenvolver Teams aplicativos.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-109">You must have knowledge of how to develop Teams apps.</span></span> <span data-ttu-id="9e0b0-110">Para obter mais informações, [consulte Teams desenvolvimento de aplicativos](../overview.md).</span><span class="sxs-lookup"><span data-stu-id="9e0b0-110">For more information, see [Teams app development](../overview.md).</span></span>

* <span data-ttu-id="9e0b0-111">Você deve atualizar o manifesto Teams aplicativo para indicar que o aplicativo está disponível para reuniões.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-111">You must update the Teams app manifest to indicate that the app is available for meetings.</span></span> <span data-ttu-id="9e0b0-112">Para obter mais informações, consulte [manifesto do aplicativo](enable-and-configure-your-app-for-teams-meetings.md#update-your-app-manifest).</span><span class="sxs-lookup"><span data-stu-id="9e0b0-112">For more information, see [app manifest](enable-and-configure-your-app-for-teams-meetings.md#update-your-app-manifest).</span></span>

* <span data-ttu-id="9e0b0-113">Seu aplicativo deve dar suporte a guias configuráveis no escopo de groupchat, para que seu aplicativo funcione no ciclo de vida da reunião como uma guia. Para obter mais informações, consulte [groupchat scope](../resources/schema/manifest-schema.md#configurabletabs) and [build a group tab](../build-your-first-app/build-channel-tab.md).</span><span class="sxs-lookup"><span data-stu-id="9e0b0-113">Your app must support configurable tabs in the groupchat scope, for your app to function in the meeting lifecycle as a tab. For more information, see [groupchat scope](../resources/schema/manifest-schema.md#configurabletabs) and [build a group tab](../build-your-first-app/build-channel-tab.md).</span></span>

* <span data-ttu-id="9e0b0-114">Você deve seguir as diretrizes gerais Teams de design de guia para cenários pré e pós-reunião.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-114">You must adhere to general Teams tab design guidelines for pre and post-meeting scenarios.</span></span> <span data-ttu-id="9e0b0-115">Para experiências durante as reuniões, consulte a guia na reunião e as diretrizes de design da caixa de diálogo na reunião.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-115">For experiences during meetings, refer to the in-meeting tab and in-meeting dialog design guidelines.</span></span> <span data-ttu-id="9e0b0-116">Para obter mais informações, [consulte Teams](../tabs/design/tabs.md)diretrizes de design de guia, diretrizes de [design](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab)de guia na reunião e diretrizes de design de caixa de diálogo [na reunião.](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)</span><span class="sxs-lookup"><span data-stu-id="9e0b0-116">For more information, see [Teams tab design guidelines](../tabs/design/tabs.md), [in-meeting tab design guidelines](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab), and [in-meeting dialog design guidelines](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog).</span></span>

* <span data-ttu-id="9e0b0-117">Você deve dar suporte ao escopo para habilitar seu aplicativo em chats de `groupchat` pré-reunião e pós-reunião.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-117">You must support the `groupchat` scope to enable your app in pre-meeting and post-meeting chats.</span></span> <span data-ttu-id="9e0b0-118">Com a experiência do aplicativo de pré-reunião, você pode encontrar e adicionar aplicativos de reunião e realizar tarefas de pré-reunião.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-118">With the pre-meeting app experience, you can find and add meeting apps and perform pre-meeting tasks.</span></span> <span data-ttu-id="9e0b0-119">Com a experiência do aplicativo pós-reunião, você pode exibir os resultados da reunião, como resultados da pesquisa ou comentários.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-119">With post-meeting app experience, you can view the results of the meeting, such as poll survey results or feedback.</span></span>

* <span data-ttu-id="9e0b0-120">Os parâmetros de URL da API de reunião `meetingId` devem ter , e `userId` `tenantId` .</span><span class="sxs-lookup"><span data-stu-id="9e0b0-120">Meeting API URL parameters must have `meetingId`, `userId`, and `tenantId`.</span></span> <span data-ttu-id="9e0b0-121">Eles estão disponíveis como parte do SDK do cliente Teams atividade de bot.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-121">These are available as part of the Teams Client SDK and bot activity.</span></span> <span data-ttu-id="9e0b0-122">Além disso, você pode recuperar informações confiáveis para a ID do usuário e a ID do locatário usando [a autenticação SSO da guia](../tabs/how-to/authentication/auth-aad-sso.md).</span><span class="sxs-lookup"><span data-stu-id="9e0b0-122">In addition, you can retrieve reliable information for user ID and tenant ID using [tab SSO authentication](../tabs/how-to/authentication/auth-aad-sso.md).</span></span>

* <span data-ttu-id="9e0b0-123">A `GetParticipant` API deve ter um registro de bot e uma ID para gerar tokens de auth.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-123">The `GetParticipant` API must have a bot registration and ID to generate auth tokens.</span></span> <span data-ttu-id="9e0b0-124">Para obter mais informações, [consulte registro de bot e ID](../build-your-first-app/build-bot.md).</span><span class="sxs-lookup"><span data-stu-id="9e0b0-124">For more information, see [bot registration and ID](../build-your-first-app/build-bot.md).</span></span>

* <span data-ttu-id="9e0b0-125">Para que seu aplicativo seja atualizado em tempo real, ele deve estar atualizado com base nas atividades do evento na reunião.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-125">For your app to update in real time, it must be up-to-date based on event activities in the meeting.</span></span> <span data-ttu-id="9e0b0-126">Esses eventos podem estar dentro da caixa de diálogo na reunião e em outros estágios no ciclo de vida da reunião.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-126">These events can be within the in-meeting dialog box and other stages across the meeting lifecycle.</span></span> <span data-ttu-id="9e0b0-127">Para a caixa de diálogo na reunião, consulte o parâmetro completion `bot Id` na `NotificationSignal` API.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-127">For the in-meeting dialog box, see completion `bot Id` parameter in `NotificationSignal` API.</span></span>

* <span data-ttu-id="9e0b0-128">A API de Detalhes da Reunião deve ter um registro de bot e uma ID de bot.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-128">Meeting Details API must have a bot registration and bot ID.</span></span> <span data-ttu-id="9e0b0-129">Requer o SDK de Bot para `TurnContext` obter .</span><span class="sxs-lookup"><span data-stu-id="9e0b0-129">It requires Bot SDK to get `TurnContext`.</span></span>

* <span data-ttu-id="9e0b0-130">Para eventos de reunião em tempo real, você deve estar familiarizado com o objeto disponível por meio `TurnContext` do SDK bot.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-130">For real-time meeting events, you must be familiar with the `TurnContext` object available through the Bot SDK.</span></span> <span data-ttu-id="9e0b0-131">O objeto em contém a carga com o início e a `Activity` `TurnContext` hora de término reais.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-131">The `Activity` object in `TurnContext` contains the payload with the actual start and end time.</span></span> <span data-ttu-id="9e0b0-132">Eventos de reunião em tempo real exigem uma ID de bot registrada na plataforma Teams.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-132">Real-time meeting events require a registered bot ID from the Teams platform.</span></span>

<span data-ttu-id="9e0b0-133">Depois de passar pelos pré-requisitos, você pode usar as referências de API de aplicativos de reunião , , e a API de Detalhes da Reunião que permitem que você acesse informações usando atributos e exibir conteúdo `GetUserContext` `GetParticipant` `NotificationSignal` relevante.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-133">After you have gone through the prerequisites, you can use the meeting apps API references `GetUserContext`, `GetParticipant`, `NotificationSignal`, and Meeting Details API that enable you to access information using attributes and display relevant content.</span></span>

## <a name="meeting-apps-api-references"></a><span data-ttu-id="9e0b0-134">Referências à API de aplicativos de reunião</span><span class="sxs-lookup"><span data-stu-id="9e0b0-134">Meeting apps API references</span></span>

<span data-ttu-id="9e0b0-135">As novas extensibilidades de reunião fornecem APIs que transformam a experiência de reunião.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-135">The new meeting extensibilities provide you with APIs that transform the meeting experience.</span></span> <span data-ttu-id="9e0b0-136">Com esse novo recurso, você pode criar aplicativos ou integrar aplicativos existentes no ciclo de vida da reunião.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-136">With this new capability, you can build apps or integrate existing apps within the meeting lifecycle.</span></span> <span data-ttu-id="9e0b0-137">Você pode usar as APIs para tornar seu aplicativo ciente da reunião.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-137">You can use the APIs to make your app aware of the meeting.</span></span> <span data-ttu-id="9e0b0-138">Você pode escolher quais APIs deseja usar para aprimorar a experiência de reunião.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-138">You can choose which APIs you want to use to enhance the meeting experience.</span></span>

<span data-ttu-id="9e0b0-139">A tabela a seguir fornece uma lista dessas APIs:</span><span class="sxs-lookup"><span data-stu-id="9e0b0-139">The following table provides a list of these APIs:</span></span>

|<span data-ttu-id="9e0b0-140">API</span><span class="sxs-lookup"><span data-stu-id="9e0b0-140">API</span></span>|<span data-ttu-id="9e0b0-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="9e0b0-141">Description</span></span>|<span data-ttu-id="9e0b0-142">Solicitação</span><span class="sxs-lookup"><span data-stu-id="9e0b0-142">Request</span></span>|<span data-ttu-id="9e0b0-143">Origem</span><span class="sxs-lookup"><span data-stu-id="9e0b0-143">Source</span></span>|
|---|---|----|---|
|<span data-ttu-id="9e0b0-144">**GetUserContext**</span><span class="sxs-lookup"><span data-stu-id="9e0b0-144">**GetUserContext**</span></span>| <span data-ttu-id="9e0b0-145">Essa API permite que você receba informações contextuais para exibir conteúdo relevante em Teams guia.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-145">This API enables you to get contextual information to display relevant content in a Teams tab.</span></span> |<span data-ttu-id="9e0b0-146">_**microsoftTeams.getContext( ( ) => { /*...\* / } )*\*_</span><span class="sxs-lookup"><span data-stu-id="9e0b0-146">_**microsoftTeams.getContext( ( ) => {  /*...*/ } )**_</span></span>|<span data-ttu-id="9e0b0-147">Microsoft Teams SDK do cliente</span><span class="sxs-lookup"><span data-stu-id="9e0b0-147">Microsoft Teams Client SDK</span></span>|
|<span data-ttu-id="9e0b0-148">**GetParticipant**</span><span class="sxs-lookup"><span data-stu-id="9e0b0-148">**GetParticipant**</span></span>| <span data-ttu-id="9e0b0-149">Essa API permite que um bot busque informações dos participantes por meio da ID da reunião e da ID do participante.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-149">This API allows a bot to fetch participant information by meeting ID and participant ID.</span></span> |<span data-ttu-id="9e0b0-150">**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_</span><span class="sxs-lookup"><span data-stu-id="9e0b0-150">**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_</span></span> |<span data-ttu-id="9e0b0-151">Microsoft Bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="9e0b0-151">Microsoft Bot Framework SDK</span></span>|
|<span data-ttu-id="9e0b0-152">**NotificationSignal**</span><span class="sxs-lookup"><span data-stu-id="9e0b0-152">**NotificationSignal**</span></span> | <span data-ttu-id="9e0b0-153">Essa API permite que você forneça sinais de reunião que são entregues usando a API de notificação de conversa existente para chat de usuário-bot.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-153">This API enables you to provide meeting signals that are delivered using the existing conversation notification API for user-bot chat.</span></span> <span data-ttu-id="9e0b0-154">Ele permite sinalizar com base na ação do usuário que mostra uma caixa de diálogo na reunião.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-154">It allows you to signal based on user action that shows an in-meeting dialog box.</span></span> |<span data-ttu-id="9e0b0-155">**POST** _**/v3/conversations/{conversationId}/activities**_</span><span class="sxs-lookup"><span data-stu-id="9e0b0-155">**POST** _**/v3/conversations/{conversationId}/activities**_</span></span>|<span data-ttu-id="9e0b0-156">Microsoft Bot Framework SDK</span><span class="sxs-lookup"><span data-stu-id="9e0b0-156">Microsoft Bot Framework SDK</span></span>|
|<span data-ttu-id="9e0b0-157">**Detalhes da reunião**</span><span class="sxs-lookup"><span data-stu-id="9e0b0-157">**Meeting Details**</span></span> | <span data-ttu-id="9e0b0-158">Essa API permite que você receba metadados de reunião estáticos.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-158">This API enables you to get static meeting metadata.</span></span> |<span data-ttu-id="9e0b0-159">**GET** _**/v1/meetings/{meetingId}**_</span><span class="sxs-lookup"><span data-stu-id="9e0b0-159">**GET** _**/v1/meetings/{meetingId}**_</span></span>| <span data-ttu-id="9e0b0-160">Bot SDK</span><span class="sxs-lookup"><span data-stu-id="9e0b0-160">Bot SDK</span></span> |

### <a name="getusercontext-api"></a><span data-ttu-id="9e0b0-161">GetUserContext API</span><span class="sxs-lookup"><span data-stu-id="9e0b0-161">GetUserContext API</span></span>

<span data-ttu-id="9e0b0-162">Para identificar e recuperar informações contextuais para o conteúdo da guia, consulte [obter contexto para](../tabs/how-to/access-teams-context.md#get-context-by-using-the-microsoft-teams-javascript-library)sua Teams guia . `meetingId`é usado por uma guia ao ser executado no contexto da reunião e é adicionado para a carga de resposta.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-162">To identify and retrieve contextual information for your tab content, see [get context for your Teams tab](../tabs/how-to/access-teams-context.md#get-context-by-using-the-microsoft-teams-javascript-library). `meetingId` is used by a tab when running in the meeting context and is added for the response payload.</span></span>

### <a name="getparticipant-api"></a><span data-ttu-id="9e0b0-163">GetParticipant API</span><span class="sxs-lookup"><span data-stu-id="9e0b0-163">GetParticipant API</span></span>

> [!NOTE]
> * <span data-ttu-id="9e0b0-164">Não armazenar em cache as funções do participante, pois o organizador da reunião pode alterar as funções a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-164">Do not cache participant roles since the meeting organizer can change the roles any time.</span></span>
> * <span data-ttu-id="9e0b0-165">Teams atualmente não dá suporte a grandes listas de distribuição ou tamanhos de lista de mais de 350 participantes para a `GetParticipant` API.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-165">Teams does not currently support large distribution lists or roster sizes of more than 350 participants for the `GetParticipant` API.</span></span>

<span data-ttu-id="9e0b0-166">A `GetParticipant` API permite que um bot busque informações do participante por meio da ID da reunião e da ID do participante.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-166">The `GetParticipant` API allows a bot to fetch participant information by meeting ID and participant ID.</span></span> <span data-ttu-id="9e0b0-167">A API inclui parâmetros de consulta, exemplos e códigos de resposta.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-167">The API includes query parameters, examples, and response codes.</span></span>

#### <a name="query-parameters"></a><span data-ttu-id="9e0b0-168">Parâmetros de consulta</span><span class="sxs-lookup"><span data-stu-id="9e0b0-168">Query parameters</span></span>

<span data-ttu-id="9e0b0-169">A `GetParticipant` API inclui os seguintes parâmetros de consulta:</span><span class="sxs-lookup"><span data-stu-id="9e0b0-169">The `GetParticipant` API includes the following query parameters:</span></span>

|<span data-ttu-id="9e0b0-170">Valor</span><span class="sxs-lookup"><span data-stu-id="9e0b0-170">Value</span></span>|<span data-ttu-id="9e0b0-171">Tipo</span><span class="sxs-lookup"><span data-stu-id="9e0b0-171">Type</span></span>|<span data-ttu-id="9e0b0-172">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="9e0b0-172">Required</span></span>|<span data-ttu-id="9e0b0-173">Descrição</span><span class="sxs-lookup"><span data-stu-id="9e0b0-173">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="9e0b0-174">**meetingId**</span><span class="sxs-lookup"><span data-stu-id="9e0b0-174">**meetingId**</span></span>| <span data-ttu-id="9e0b0-175">String</span><span class="sxs-lookup"><span data-stu-id="9e0b0-175">String</span></span> | <span data-ttu-id="9e0b0-176">Sim</span><span class="sxs-lookup"><span data-stu-id="9e0b0-176">Yes</span></span> | <span data-ttu-id="9e0b0-177">O identificador de reunião está disponível por meio de Bot Invoke e Teams Client SDK.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-177">The meeting identifier is available through Bot Invoke and Teams Client SDK.</span></span>|
|<span data-ttu-id="9e0b0-178">**participantId**</span><span class="sxs-lookup"><span data-stu-id="9e0b0-178">**participantId**</span></span>| <span data-ttu-id="9e0b0-179">String</span><span class="sxs-lookup"><span data-stu-id="9e0b0-179">String</span></span> | <span data-ttu-id="9e0b0-180">Sim</span><span class="sxs-lookup"><span data-stu-id="9e0b0-180">Yes</span></span> | <span data-ttu-id="9e0b0-181">A ID do participante é a ID do usuário.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-181">The participant ID is the user ID.</span></span> <span data-ttu-id="9e0b0-182">Ele está disponível em Tab SSO, Bot Invoke e Teams Client SDK.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-182">It is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="9e0b0-183">É recomendável obter uma ID do participante no SSO da guia.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-183">It is recommended to get a participant ID from the Tab SSO.</span></span> |
|<span data-ttu-id="9e0b0-184">**tenantId**</span><span class="sxs-lookup"><span data-stu-id="9e0b0-184">**tenantId**</span></span>| <span data-ttu-id="9e0b0-185">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9e0b0-185">String</span></span> | <span data-ttu-id="9e0b0-186">Sim</span><span class="sxs-lookup"><span data-stu-id="9e0b0-186">Yes</span></span> | <span data-ttu-id="9e0b0-187">A ID do locatário é necessária para os usuários do locatário.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-187">The tenant ID is required for the tenant users.</span></span> <span data-ttu-id="9e0b0-188">Ele está disponível em Tab SSO, Bot Invoke e Teams Client SDK.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-188">It is available in Tab SSO, Bot Invoke, and Teams Client SDK.</span></span> <span data-ttu-id="9e0b0-189">É recomendável obter uma ID de locatário do SSO de tabulação.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-189">It is recommended to get a tenant ID from the Tab SSO.</span></span> |

#### <a name="example"></a><span data-ttu-id="9e0b0-190">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9e0b0-190">Example</span></span>

<span data-ttu-id="9e0b0-191">A `GetParticipant` API inclui os seguintes exemplos:</span><span class="sxs-lookup"><span data-stu-id="9e0b0-191">The `GetParticipant` API includes the following examples:</span></span>

# <a name="c"></a>[<span data-ttu-id="9e0b0-192">C#</span><span class="sxs-lookup"><span data-stu-id="9e0b0-192">C#</span></span>](#tab/dotnet)

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

# <a name="javascript"></a>[<span data-ttu-id="9e0b0-193">JavaScript</span><span class="sxs-lookup"><span data-stu-id="9e0b0-193">JavaScript</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="9e0b0-194">JSON</span><span class="sxs-lookup"><span data-stu-id="9e0b0-194">JSON</span></span>](#tab/json)

```http
GET /v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}
```

* * *

<span data-ttu-id="9e0b0-195">O corpo de resposta JSON para `GetParticipant` API é:</span><span class="sxs-lookup"><span data-stu-id="9e0b0-195">The JSON response body for `GetParticipant` API is:</span></span>

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

#### <a name="response-codes"></a><span data-ttu-id="9e0b0-196">Códigos de resposta</span><span class="sxs-lookup"><span data-stu-id="9e0b0-196">Response codes</span></span>

<span data-ttu-id="9e0b0-197">A `GetParticipant` API inclui os seguintes códigos de resposta:</span><span class="sxs-lookup"><span data-stu-id="9e0b0-197">The `GetParticipant` API includes the following response codes:</span></span>

|<span data-ttu-id="9e0b0-198">Código da resposta</span><span class="sxs-lookup"><span data-stu-id="9e0b0-198">Response code</span></span>|<span data-ttu-id="9e0b0-199">Descrição</span><span class="sxs-lookup"><span data-stu-id="9e0b0-199">Description</span></span>|
|---|---|
| <span data-ttu-id="9e0b0-200">**403**</span><span class="sxs-lookup"><span data-stu-id="9e0b0-200">**403**</span></span> | <span data-ttu-id="9e0b0-201">O aplicativo não tem permissão para obter informações do participante.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-201">The app is not allowed to get participant information.</span></span> <span data-ttu-id="9e0b0-202">Essa é a resposta de erro mais comum e é disparada se o aplicativo não estiver instalado na reunião.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-202">This is the most common error response and is triggered if the app is not installed in the meeting.</span></span> <span data-ttu-id="9e0b0-203">Por exemplo, se o aplicativo for desabilitado pelo administrador do locatário ou bloqueado durante a migração do site ao vivo.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-203">For example, if the app is disabled by tenant admin or blocked during live site migration.</span></span>|
| <span data-ttu-id="9e0b0-204">**200**</span><span class="sxs-lookup"><span data-stu-id="9e0b0-204">**200**</span></span> | <span data-ttu-id="9e0b0-205">As informações do participante são recuperadas com êxito.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-205">The participant information is successfully retrieved.</span></span>|
| <span data-ttu-id="9e0b0-206">**401**</span><span class="sxs-lookup"><span data-stu-id="9e0b0-206">**401**</span></span> | <span data-ttu-id="9e0b0-207">O aplicativo responde com um token inválido.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-207">The app responds with an invalid token.</span></span>|
| <span data-ttu-id="9e0b0-208">**404**</span><span class="sxs-lookup"><span data-stu-id="9e0b0-208">**404**</span></span> | <span data-ttu-id="9e0b0-209">A reunião expirou ou o participante não pode ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-209">The meeting has either expired or participant cannot be found.</span></span>|
| <span data-ttu-id="9e0b0-210">**500**</span><span class="sxs-lookup"><span data-stu-id="9e0b0-210">**500**</span></span> | <span data-ttu-id="9e0b0-211">A reunião expirou (mais de 60 dias) desde que a reunião terminou ou os participantes não têm permissões com base em suas funções.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-211">The meeting has either expired (more than 60 days) since the meeting ended or the participants do not have permissions based on their role.</span></span>|

### <a name="notificationsignal-api"></a><span data-ttu-id="9e0b0-212">NotificationSignal API</span><span class="sxs-lookup"><span data-stu-id="9e0b0-212">NotificationSignal API</span></span>

<span data-ttu-id="9e0b0-213">Todos os usuários em uma reunião recebem as notificações enviadas por meio da `NotificationSignal` API.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-213">All users in a meeting receive the notifications sent through the `NotificationSignal` API.</span></span>

> [!NOTE]
> * <span data-ttu-id="9e0b0-214">Quando uma caixa de diálogo na reunião é invocada, o conteúdo é apresentado como uma mensagem de chat.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-214">When an in-meeting dialog box is invoked, the content is presented as a chat message.</span></span>
> * <span data-ttu-id="9e0b0-215">Atualmente, não há suporte para o envio de notificações direcionadas.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-215">Currently, sending targeted notifications is not supported.</span></span>

<span data-ttu-id="9e0b0-216">`NotificationSignal` A API permite que você forneça sinais de reunião que são entregues usando a API de notificação de conversa existente para chat usuário-bot.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-216">`NotificationSignal` API enables you to provide meeting signals that are delivered using the existing conversation notification API for user-bot chat.</span></span> <span data-ttu-id="9e0b0-217">Essa API permite sinalizar com base na ação do usuário que mostra uma caixa de diálogo na reunião.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-217">This API allows you to signal based on user action that shows an in-meeting dialog box.</span></span> <span data-ttu-id="9e0b0-218">A API inclui parâmetros de consulta, exemplos e códigos de resposta.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-218">The API includes query parameter, examples, and response codes.</span></span>

#### <a name="query-parameter"></a><span data-ttu-id="9e0b0-219">Parâmetro de consulta</span><span class="sxs-lookup"><span data-stu-id="9e0b0-219">Query parameter</span></span>

<span data-ttu-id="9e0b0-220">A `NotificationSignal` API inclui o seguinte parâmetro de consulta:</span><span class="sxs-lookup"><span data-stu-id="9e0b0-220">The `NotificationSignal` API includes the following query parameter:</span></span>

|<span data-ttu-id="9e0b0-221">Valor</span><span class="sxs-lookup"><span data-stu-id="9e0b0-221">Value</span></span>|<span data-ttu-id="9e0b0-222">Tipo</span><span class="sxs-lookup"><span data-stu-id="9e0b0-222">Type</span></span>|<span data-ttu-id="9e0b0-223">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="9e0b0-223">Required</span></span>|<span data-ttu-id="9e0b0-224">Descrição</span><span class="sxs-lookup"><span data-stu-id="9e0b0-224">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="9e0b0-225">**conversationId**</span><span class="sxs-lookup"><span data-stu-id="9e0b0-225">**conversationId**</span></span>| <span data-ttu-id="9e0b0-226">String</span><span class="sxs-lookup"><span data-stu-id="9e0b0-226">String</span></span> | <span data-ttu-id="9e0b0-227">Sim</span><span class="sxs-lookup"><span data-stu-id="9e0b0-227">Yes</span></span> | <span data-ttu-id="9e0b0-228">O identificador de conversa está disponível como parte de Bot Invoke.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-228">The conversation identifier is available as part of Bot Invoke.</span></span> |

#### <a name="examples"></a><span data-ttu-id="9e0b0-229">Exemplos</span><span class="sxs-lookup"><span data-stu-id="9e0b0-229">Examples</span></span>

<span data-ttu-id="9e0b0-230">O `Bot ID` é declarado no manifesto e o bot recebe um objeto de resultado.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-230">The `Bot ID` is declared in the manifest and the bot receives a result object.</span></span>

> [!NOTE]
> * <span data-ttu-id="9e0b0-231">O `completionBotId` parâmetro do é opcional no exemplo de carga `externalResourceUrl` solicitada.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-231">The `completionBotId` parameter of the `externalResourceUrl` is optional in the requested payload example.</span></span> <span data-ttu-id="9e0b0-232">`Bot ID` é declarado no manifesto e o bot recebe um objeto de resultado.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-232">`Bot ID` is declared in the manifest and the bot receives a result object.</span></span>
> * <span data-ttu-id="9e0b0-233">Os `externalResourceUrl` parâmetros de largura e altura devem estar em pixels.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-233">The `externalResourceUrl` width and height parameters must be in pixels.</span></span> <span data-ttu-id="9e0b0-234">Para garantir que as dimensões estão dentro dos limites permitidos, consulte [diretrizes de design](design/designing-apps-in-meetings.md).</span><span class="sxs-lookup"><span data-stu-id="9e0b0-234">To ensure the dimensions are within the allowed limits, see [design guidelines](design/designing-apps-in-meetings.md).</span></span>
> * <span data-ttu-id="9e0b0-235">A URL é a página carregada como `<iframe>` uma caixa de diálogo na reunião.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-235">The URL is the page loaded as an `<iframe>` in the in-meeting dialog box.</span></span> <span data-ttu-id="9e0b0-236">O domínio deve estar na matriz do aplicativo `validDomains` no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-236">The domain must be in the app's `validDomains` array in your app manifest.</span></span>

<span data-ttu-id="9e0b0-237">A `NotificationSignal` API inclui os seguintes exemplos:</span><span class="sxs-lookup"><span data-stu-id="9e0b0-237">The `NotificationSignal` API includes the following examples:</span></span>

# <a name="c"></a>[<span data-ttu-id="9e0b0-238">C#</span><span class="sxs-lookup"><span data-stu-id="9e0b0-238">C#</span></span>](#tab/dotnet)

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

# <a name="javascript"></a>[<span data-ttu-id="9e0b0-239">JavaScript</span><span class="sxs-lookup"><span data-stu-id="9e0b0-239">JavaScript</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="9e0b0-240">JSON</span><span class="sxs-lookup"><span data-stu-id="9e0b0-240">JSON</span></span>](#tab/json)

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

#### <a name="response-codes"></a><span data-ttu-id="9e0b0-241">Códigos de resposta</span><span class="sxs-lookup"><span data-stu-id="9e0b0-241">Response codes</span></span>

<span data-ttu-id="9e0b0-242">A `NotificationSignal` API inclui os seguintes códigos de resposta:</span><span class="sxs-lookup"><span data-stu-id="9e0b0-242">The `NotificationSignal` API includes the following response codes:</span></span>

|<span data-ttu-id="9e0b0-243">Código da resposta</span><span class="sxs-lookup"><span data-stu-id="9e0b0-243">Response code</span></span>|<span data-ttu-id="9e0b0-244">Descrição</span><span class="sxs-lookup"><span data-stu-id="9e0b0-244">Description</span></span>|
|---|---|
| <span data-ttu-id="9e0b0-245">**201**</span><span class="sxs-lookup"><span data-stu-id="9e0b0-245">**201**</span></span> | <span data-ttu-id="9e0b0-246">A atividade com sinal é enviada com êxito.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-246">The activity with signal is successfully sent.</span></span> |
| <span data-ttu-id="9e0b0-247">**401**</span><span class="sxs-lookup"><span data-stu-id="9e0b0-247">**401**</span></span> | <span data-ttu-id="9e0b0-248">O aplicativo responde com um token inválido.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-248">The app responds with an invalid token.</span></span> |
| <span data-ttu-id="9e0b0-249">**403**</span><span class="sxs-lookup"><span data-stu-id="9e0b0-249">**403**</span></span> | <span data-ttu-id="9e0b0-250">O aplicativo não consegue enviar o sinal.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-250">The app is unable to send the signal.</span></span> <span data-ttu-id="9e0b0-251">Isso pode acontecer devido a vários motivos, como o administrador de locatários desabilita o aplicativo, o aplicativo é bloqueado durante a migração de site ao vivo e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-251">This can happen due to various reasons such as the tenant admin disables the app, the app is blocked during live site migration, and so on.</span></span> <span data-ttu-id="9e0b0-252">Nesse caso, a carga contém uma mensagem de erro detalhada.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-252">In this case, the payload contains a detailed error message.</span></span> |
| <span data-ttu-id="9e0b0-253">**404**</span><span class="sxs-lookup"><span data-stu-id="9e0b0-253">**404**</span></span> | <span data-ttu-id="9e0b0-254">O chat de reunião não existe.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-254">The meeting chat does not exist.</span></span> |

### <a name="meeting-details-api"></a><span data-ttu-id="9e0b0-255">API de Detalhes da Reunião</span><span class="sxs-lookup"><span data-stu-id="9e0b0-255">Meeting Details API</span></span>

> [!NOTE]
> <span data-ttu-id="9e0b0-256">Esse recurso está disponível apenas na [visualização de desenvolvedor](../resources/dev-preview/developer-preview-intro.md) público.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-256">This feature is currently available in [public developer preview](../resources/dev-preview/developer-preview-intro.md) only.</span></span>

<span data-ttu-id="9e0b0-257">A API Detalhes da Reunião permite que seu aplicativo receba metadados de reunião estáticos.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-257">The Meeting Details API enables your app to get static meeting metadata.</span></span> <span data-ttu-id="9e0b0-258">Esses são pontos de dados que não mudam dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-258">These are data points that do not change dynamically.</span></span>
<span data-ttu-id="9e0b0-259">A API está disponível por meio dos Serviços bot.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-259">The API is available through Bot Services.</span></span>

#### <a name="query-parameter"></a><span data-ttu-id="9e0b0-260">Parâmetro de consulta</span><span class="sxs-lookup"><span data-stu-id="9e0b0-260">Query parameter</span></span>

<span data-ttu-id="9e0b0-261">A API De Detalhes da Reunião inclui o seguinte parâmetro de consulta:</span><span class="sxs-lookup"><span data-stu-id="9e0b0-261">The Meeting Details API includes the following query parameter:</span></span>

|<span data-ttu-id="9e0b0-262">Valor</span><span class="sxs-lookup"><span data-stu-id="9e0b0-262">Value</span></span>|<span data-ttu-id="9e0b0-263">Tipo</span><span class="sxs-lookup"><span data-stu-id="9e0b0-263">Type</span></span>|<span data-ttu-id="9e0b0-264">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="9e0b0-264">Required</span></span>|<span data-ttu-id="9e0b0-265">Descrição</span><span class="sxs-lookup"><span data-stu-id="9e0b0-265">Description</span></span>|
|---|---|----|---|
|<span data-ttu-id="9e0b0-266">**meetingId**</span><span class="sxs-lookup"><span data-stu-id="9e0b0-266">**meetingId**</span></span>| <span data-ttu-id="9e0b0-267">String</span><span class="sxs-lookup"><span data-stu-id="9e0b0-267">String</span></span> | <span data-ttu-id="9e0b0-268">Sim</span><span class="sxs-lookup"><span data-stu-id="9e0b0-268">Yes</span></span> | <span data-ttu-id="9e0b0-269">O identificador de reunião está disponível por meio de Bot Invoke e Teams Client SDK.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-269">The meeting identifier is available through Bot Invoke and Teams Client SDK.</span></span> |

#### <a name="example"></a><span data-ttu-id="9e0b0-270">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9e0b0-270">Example</span></span>

<span data-ttu-id="9e0b0-271">A API De Detalhes da Reunião inclui os seguintes exemplos:</span><span class="sxs-lookup"><span data-stu-id="9e0b0-271">The Meeting Details API includes the following examples:</span></span>

# <a name="c"></a>[<span data-ttu-id="9e0b0-272">C#</span><span class="sxs-lookup"><span data-stu-id="9e0b0-272">C#</span></span>](#tab/dotnet)

```csharp
var connectorClient = parameters.TurnContext.TurnState.Get<IConnectorClient>();
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

# <a name="javascript"></a>[<span data-ttu-id="9e0b0-273">JavaScript</span><span class="sxs-lookup"><span data-stu-id="9e0b0-273">JavaScript</span></span>](#tab/javascript)

<span data-ttu-id="9e0b0-274">Não disponível</span><span class="sxs-lookup"><span data-stu-id="9e0b0-274">Not available</span></span>

# <a name="json"></a>[<span data-ttu-id="9e0b0-275">JSON</span><span class="sxs-lookup"><span data-stu-id="9e0b0-275">JSON</span></span>](#tab/json)

```http
GET /v1/meetings/{meetingId}
```

---

<span data-ttu-id="9e0b0-276">O corpo da resposta JSON para a API de Detalhes da Reunião é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9e0b0-276">The JSON response body for Meeting Details API is as follows:</span></span>

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

## <a name="real-time-teams-meeting-events"></a><span data-ttu-id="9e0b0-277">Eventos de reunião Teams em tempo real</span><span class="sxs-lookup"><span data-stu-id="9e0b0-277">Real-time Teams meeting events</span></span>

> [!NOTE]
> <span data-ttu-id="9e0b0-278">Esse recurso está disponível apenas na [visualização de desenvolvedor](../resources/dev-preview/developer-preview-intro.md) público.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-278">This feature is currently available in [public developer preview](../resources/dev-preview/developer-preview-intro.md) only.</span></span>

<span data-ttu-id="9e0b0-279">O usuário pode receber eventos de reunião em tempo real.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-279">The user can receive real-time meeting events.</span></span> <span data-ttu-id="9e0b0-280">Assim que qualquer aplicativo é associado a uma reunião, o início real da reunião e a hora de término da reunião são compartilhados com o bot.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-280">As soon as any app is associated with a meeting, the actual meeting start and meeting end time are shared with the bot.</span></span>

<span data-ttu-id="9e0b0-281">A hora real de início e término de uma reunião é diferente da hora de início e término agendada.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-281">Actual start and end time of a meeting are different from the scheduled start and end time.</span></span> <span data-ttu-id="9e0b0-282">A API de detalhes da reunião fornece a hora de início e término agendada enquanto o evento fornece a hora real de início e término.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-282">The meeting details API provides the scheduled start and end time while the event provides the actual start and end time.</span></span>

### <a name="example-of-meeting-start-event-payload"></a><span data-ttu-id="9e0b0-283">Exemplo de carga do evento de início da reunião</span><span class="sxs-lookup"><span data-stu-id="9e0b0-283">Example of meeting start event payload</span></span>

<span data-ttu-id="9e0b0-284">O código a seguir fornece um exemplo de carga de evento de início de reunião:</span><span class="sxs-lookup"><span data-stu-id="9e0b0-284">The following code provides an example of meeting start event payload:</span></span>

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

### <a name="example-of-meeting-end-event-payload"></a><span data-ttu-id="9e0b0-285">Exemplo de carga de evento final de reunião</span><span class="sxs-lookup"><span data-stu-id="9e0b0-285">Example of meeting end event payload</span></span>

<span data-ttu-id="9e0b0-286">O código a seguir fornece um exemplo de carga de evento final de reunião:</span><span class="sxs-lookup"><span data-stu-id="9e0b0-286">The following code provides an example of meeting end event payload:</span></span>

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

### <a name="example-of-getting-metadata-of-a-meeting"></a><span data-ttu-id="9e0b0-287">Exemplo de obter metadados de uma reunião</span><span class="sxs-lookup"><span data-stu-id="9e0b0-287">Example of getting metadata of a meeting</span></span>

<span data-ttu-id="9e0b0-288">Seu bot recebe o evento por meio do `OnEventActivityAsync` manipulador.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-288">Your bot receives the event through the `OnEventActivityAsync` handler.</span></span>

<span data-ttu-id="9e0b0-289">Para desserializar a carga json, um objeto modelo é introduzido para obter os metadados de uma reunião.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-289">To deserialize the json payload, a model object is introduced to get the metadata of a meeting.</span></span> <span data-ttu-id="9e0b0-290">Os metadados de uma reunião residem na `value` propriedade na carga do evento.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-290">The metadata of a meeting resides in the `value` property in the event payload.</span></span> <span data-ttu-id="9e0b0-291">O `MeetingStartEndEventvalue` objeto model é criado, cujas variáveis de membro correspondem às chaves sob a propriedade na carga do `value` evento.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-291">The `MeetingStartEndEventvalue` model object is created, whose member variables correspond to the keys under the `value` property in the event payload.</span></span>

<span data-ttu-id="9e0b0-292">O código a seguir mostra como capturar os metadados de uma reunião que é , , , , e de um evento de início e fim de `MeetingType` `Title` `Id` `JoinUrl` `StartTime` `EndTime` reunião:</span><span class="sxs-lookup"><span data-stu-id="9e0b0-292">The following code shows how to capture the metadata of a meeting that is `MeetingType`, `Title`, `Id`, `JoinUrl`, `StartTime`, and `EndTime` from a meeting start and end event:</span></span>

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

<span data-ttu-id="9e0b0-293">MeetingStartEndEventvalue.cs inclui o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="9e0b0-293">The MeetingStartEndEventvalue.cs includes the following code:</span></span>

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

## <a name="code-sample"></a><span data-ttu-id="9e0b0-294">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="9e0b0-294">Code sample</span></span>

|<span data-ttu-id="9e0b0-295">Exemplo de nome</span><span class="sxs-lookup"><span data-stu-id="9e0b0-295">Sample name</span></span> | <span data-ttu-id="9e0b0-296">Descrição</span><span class="sxs-lookup"><span data-stu-id="9e0b0-296">Description</span></span> | <span data-ttu-id="9e0b0-297">.NET</span><span class="sxs-lookup"><span data-stu-id="9e0b0-297">.NET</span></span> | <span data-ttu-id="9e0b0-298">Node.js</span><span class="sxs-lookup"><span data-stu-id="9e0b0-298">Node.js</span></span> |
|----------------|-----------------|--------------|--------------|
| <span data-ttu-id="9e0b0-299">Extensibilidade de reuniões</span><span class="sxs-lookup"><span data-stu-id="9e0b0-299">Meetings extensibility</span></span> | <span data-ttu-id="9e0b0-300">Microsoft Teams exemplo de extensibilidade de reunião para tokens de passagem.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-300">Microsoft Teams meeting extensibility sample for passing tokens.</span></span> | [<span data-ttu-id="9e0b0-301">View</span><span class="sxs-lookup"><span data-stu-id="9e0b0-301">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) | [<span data-ttu-id="9e0b0-302">View</span><span class="sxs-lookup"><span data-stu-id="9e0b0-302">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/nodejs) |
| <span data-ttu-id="9e0b0-303">Bot de bolha de conteúdo de reunião</span><span class="sxs-lookup"><span data-stu-id="9e0b0-303">Meeting content bubble bot</span></span> | <span data-ttu-id="9e0b0-304">Microsoft Teams exemplo de extensibilidade de reunião para interagir com o bot de bolha de conteúdo em uma reunião.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-304">Microsoft Teams meeting extensibility sample for interacting with content bubble bot in a meeting.</span></span> | [<span data-ttu-id="9e0b0-305">View</span><span class="sxs-lookup"><span data-stu-id="9e0b0-305">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/csharp) |  [<span data-ttu-id="9e0b0-306">View</span><span class="sxs-lookup"><span data-stu-id="9e0b0-306">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/nodejs)|
| <span data-ttu-id="9e0b0-307">Meeting meetingSidePanel</span><span class="sxs-lookup"><span data-stu-id="9e0b0-307">Meeting meetingSidePanel</span></span> | <span data-ttu-id="9e0b0-308">Microsoft Teams exemplo de extensibilidade de reunião para interagir com o painel lateral na reunião.</span><span class="sxs-lookup"><span data-stu-id="9e0b0-308">Microsoft Teams meeting extensibility sample for interacting with the side panel in-meeting.</span></span> | [<span data-ttu-id="9e0b0-309">View</span><span class="sxs-lookup"><span data-stu-id="9e0b0-309">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/csharp) | [<span data-ttu-id="9e0b0-310">View</span><span class="sxs-lookup"><span data-stu-id="9e0b0-310">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/nodejs)|

## <a name="see-also"></a><span data-ttu-id="9e0b0-311">Também consulte</span><span class="sxs-lookup"><span data-stu-id="9e0b0-311">See also</span></span>

* [<span data-ttu-id="9e0b0-312">Diretrizes de design de caixa de diálogo na reunião</span><span class="sxs-lookup"><span data-stu-id="9e0b0-312">In-meeting dialog design guidelines</span></span>](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
* [<span data-ttu-id="9e0b0-313">Teams fluxo de autenticação para guias</span><span class="sxs-lookup"><span data-stu-id="9e0b0-313">Teams authentication flow for tabs</span></span>](../tabs/how-to/authentication/auth-flow-tab.md)
* [<span data-ttu-id="9e0b0-314">Aplicativos para Teams reuniões</span><span class="sxs-lookup"><span data-stu-id="9e0b0-314">Apps for Teams meetings</span></span>](teams-apps-in-meetings.md)

## <a name="next-step"></a><span data-ttu-id="9e0b0-315">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="9e0b0-315">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9e0b0-316">Habilitar e configurar seus aplicativos para Teams reuniões</span><span class="sxs-lookup"><span data-stu-id="9e0b0-316">Enable and configure your apps for Teams meetings</span></span>](enable-and-configure-your-app-for-teams-meetings.md)
