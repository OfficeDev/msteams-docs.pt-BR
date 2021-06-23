---
title: Habilitar e configurar seus aplicativos para Teams reuniões
author: surbhigupta
description: Habilitar e configurar seus aplicativos para Teams reuniões
ms.topic: conceptual
ms.openlocfilehash: e31e241a61f40a8dc2b8a1221765bd4755d346ed
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2021
ms.locfileid: "53068640"
---
# <a name="enable-and-configure-your-apps-for-teams-meetings"></a><span data-ttu-id="5c51b-103">Habilitar e configurar seus aplicativos para Teams reuniões</span><span class="sxs-lookup"><span data-stu-id="5c51b-103">Enable and configure your apps for Teams meetings</span></span>

<span data-ttu-id="5c51b-104">Cada equipe tem uma maneira diferente de comunicar e colaborar tarefas.</span><span class="sxs-lookup"><span data-stu-id="5c51b-104">Every team has a different way of communicating and collaborating tasks.</span></span> <span data-ttu-id="5c51b-105">Você pode realizar essas tarefas diferentes personalização Teams aplicativos para reuniões.</span><span class="sxs-lookup"><span data-stu-id="5c51b-105">You can achieve these different tasks by customizing Teams with apps for meetings.</span></span> <span data-ttu-id="5c51b-106">Para personalizar e realizar tarefas diferentes, você deve habilitar seus aplicativos para reuniões Teams e configurar seus aplicativos para estar disponível no escopo de reunião no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5c51b-106">To customize and to achieve different tasks, you must enable your apps for Teams meetings and configure your apps to be available in meeting scope within their app manifest.</span></span>

## <a name="enable-your-app-for-teams-meetings"></a><span data-ttu-id="5c51b-107">Habilitar seu aplicativo para Teams reuniões</span><span class="sxs-lookup"><span data-stu-id="5c51b-107">Enable your app for Teams meetings</span></span>

<span data-ttu-id="5c51b-108">Para habilitar seu aplicativo para reuniões Teams, você deve atualizar o manifesto do aplicativo e usar as propriedades de contexto para determinar onde seu aplicativo deve aparecer.</span><span class="sxs-lookup"><span data-stu-id="5c51b-108">To enable your app for Teams meetings, you must update your app manifest and use the context properties to determine where your app must appear.</span></span>

### <a name="update-your-app-manifest"></a><span data-ttu-id="5c51b-109">Atualizar o manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="5c51b-109">Update your app manifest</span></span>

<span data-ttu-id="5c51b-110">Os recursos do aplicativo de reuniões são declarados no manifesto do aplicativo usando `configurableTabs` `scopes` as matrizes , e `context` .</span><span class="sxs-lookup"><span data-stu-id="5c51b-110">The meetings app capabilities are declared in your app manifest using the `configurableTabs`, `scopes`, and `context` arrays.</span></span> <span data-ttu-id="5c51b-111">O escopo define a quem e o contexto define onde seu aplicativo está disponível.</span><span class="sxs-lookup"><span data-stu-id="5c51b-111">Scope defines to whom and context defines where your app is available.</span></span>

> [!NOTE]
> * <span data-ttu-id="5c51b-112">Tente atualizar o manifesto do aplicativo com o [esquema de manifesto](../resources/schema/manifest-schema-dev-preview.md).</span><span class="sxs-lookup"><span data-stu-id="5c51b-112">Try updating your app manifest with the [manifest schema](../resources/schema/manifest-schema-dev-preview.md).</span></span>
> * <span data-ttu-id="5c51b-113">Os aplicativos em reuniões exigem escopo de groupchat.</span><span class="sxs-lookup"><span data-stu-id="5c51b-113">Apps in meetings require groupchat scope.</span></span> <span data-ttu-id="5c51b-114">O escopo da equipe funciona apenas para guias em canais.</span><span class="sxs-lookup"><span data-stu-id="5c51b-114">The team scope works for tabs in channels only.</span></span>

<span data-ttu-id="5c51b-115">O manifesto do aplicativo deve incluir o seguinte trecho de código:</span><span class="sxs-lookup"><span data-stu-id="5c51b-115">The app manifest must include the following code snippet:</span></span>

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
> <span data-ttu-id="5c51b-116">`meetingStage` está disponível no momento apenas na [visualização do](../resources/dev-preview/developer-preview-intro.md) desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="5c51b-116">`meetingStage` is currently available in [developer preview](../resources/dev-preview/developer-preview-intro.md) only.</span></span>

### <a name="context-property"></a><span data-ttu-id="5c51b-117">Propriedade Context</span><span class="sxs-lookup"><span data-stu-id="5c51b-117">Context property</span></span>

<span data-ttu-id="5c51b-118">A propriedade determina o que deve ser mostrado quando um usuário invoca um aplicativo em uma reunião, dependendo de onde o usuário `context` invoca o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5c51b-118">The `context` property determines what must be shown when a user invokes an app in a meeting depending on where the user invokes the app.</span></span> <span data-ttu-id="5c51b-119">A guia `context` e `scopes` as propriedades permitem determinar onde seu aplicativo deve aparecer.</span><span class="sxs-lookup"><span data-stu-id="5c51b-119">The tab `context` and `scopes` properties enable you to determine where your app must appear.</span></span> <span data-ttu-id="5c51b-120">Guias no `team` escopo ou podem `groupchat` ter mais de um contexto.</span><span class="sxs-lookup"><span data-stu-id="5c51b-120">Tabs in the `team` or `groupchat` scope can have more than one context.</span></span> <span data-ttu-id="5c51b-121">A seguir estão os valores da propriedade da qual você pode usar todos ou `context` alguns dos valores:</span><span class="sxs-lookup"><span data-stu-id="5c51b-121">Following are the values for the `context` property from which you can use all or some of the values:</span></span>

|<span data-ttu-id="5c51b-122">Valor</span><span class="sxs-lookup"><span data-stu-id="5c51b-122">Value</span></span>|<span data-ttu-id="5c51b-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="5c51b-123">Description</span></span>|
|---|---|
| <span data-ttu-id="5c51b-124">**channelTab**</span><span class="sxs-lookup"><span data-stu-id="5c51b-124">**channelTab**</span></span> | <span data-ttu-id="5c51b-125">Uma guia no header de um canal de equipe.</span><span class="sxs-lookup"><span data-stu-id="5c51b-125">A tab in the header of a team channel.</span></span> |
| <span data-ttu-id="5c51b-126">**privateChatTab**</span><span class="sxs-lookup"><span data-stu-id="5c51b-126">**privateChatTab**</span></span> | <span data-ttu-id="5c51b-127">Uma guia no header de um chat de grupo entre um conjunto de usuários, não no contexto de uma equipe ou reunião.</span><span class="sxs-lookup"><span data-stu-id="5c51b-127">A tab in the header of a group chat between a set of users, not in the context of a team or meeting.</span></span> |
| <span data-ttu-id="5c51b-128">**meetingChatTab**</span><span class="sxs-lookup"><span data-stu-id="5c51b-128">**meetingChatTab**</span></span> | <span data-ttu-id="5c51b-129">Uma guia no header de um chat de grupo entre um conjunto de usuários no contexto de uma reunião agendada.</span><span class="sxs-lookup"><span data-stu-id="5c51b-129">A tab in the header of a group chat between a set of users in the context of a scheduled meeting.</span></span> |
| <span data-ttu-id="5c51b-130">**meetingDetailsTab**</span><span class="sxs-lookup"><span data-stu-id="5c51b-130">**meetingDetailsTab**</span></span> | <span data-ttu-id="5c51b-131">Uma guia no header da exibição de detalhes da reunião do calendário.</span><span class="sxs-lookup"><span data-stu-id="5c51b-131">A tab in the header of the meeting details view of the calendar.</span></span> |
| <span data-ttu-id="5c51b-132">**meetingSidePanel**</span><span class="sxs-lookup"><span data-stu-id="5c51b-132">**meetingSidePanel**</span></span> | <span data-ttu-id="5c51b-133">Um painel na reunião foi aberto por meio da barra unificada (U-bar).</span><span class="sxs-lookup"><span data-stu-id="5c51b-133">An in-meeting panel opened through the unified bar (U-bar).</span></span> |
| <span data-ttu-id="5c51b-134">**meetingStage**</span><span class="sxs-lookup"><span data-stu-id="5c51b-134">**meetingStage**</span></span> | <span data-ttu-id="5c51b-135">Um aplicativo do meetingSidePanel pode ser compartilhado no estágio de reunião.</span><span class="sxs-lookup"><span data-stu-id="5c51b-135">An app from the meetingSidePanel can be shared to the meeting stage.</span></span> |

> [!NOTE]
> <span data-ttu-id="5c51b-136">`Context` atualmente, não há suporte para clientes móveis.</span><span class="sxs-lookup"><span data-stu-id="5c51b-136">`Context` property is currently not supported on mobile clients.</span></span>

<span data-ttu-id="5c51b-137">Depois de habilitar seu aplicativo para Teams reuniões, você deve configurar seu aplicativo antes de uma reunião, durante uma reunião e após uma reunião.</span><span class="sxs-lookup"><span data-stu-id="5c51b-137">After you enable your app for Teams meetings, you must configure your app before a meeting, during a meeting, and after a meeting.</span></span>

## <a name="configure-your-app-for-meeting-scenarios"></a><span data-ttu-id="5c51b-138">Configurar seu aplicativo para cenários de reunião</span><span class="sxs-lookup"><span data-stu-id="5c51b-138">Configure your app for meeting scenarios</span></span>

> [!NOTE]
> * <span data-ttu-id="5c51b-139">Para que seu aplicativo seja visível na galeria de guias, ele deve dar suporte a guias configuráveis e ao escopo de chat de grupo.</span><span class="sxs-lookup"><span data-stu-id="5c51b-139">For your app to be visible in the tab gallery, it must support configurable tabs and the group chat scope.</span></span>
> * <span data-ttu-id="5c51b-140">Os clientes móveis suportam guias somente em estágios pré e pós-reunião.</span><span class="sxs-lookup"><span data-stu-id="5c51b-140">Mobile clients support tabs only in pre and post meeting stages.</span></span>
> * <span data-ttu-id="5c51b-141">As experiências na reunião que estão na caixa de diálogo e na guia da reunião atualmente não são suportadas em clientes móveis.</span><span class="sxs-lookup"><span data-stu-id="5c51b-141">The in-meeting experiences that is in-meeting dialog box and tab is currently not supported on mobile clients.</span></span> <span data-ttu-id="5c51b-142">Para obter mais informações, consulte [diretrizes para guias em dispositivos móveis](../tabs/design/tabs-mobile.md) ao criar suas guias para dispositivos móveis.</span><span class="sxs-lookup"><span data-stu-id="5c51b-142">For more information, see [guidance for tabs on mobile](../tabs/design/tabs-mobile.md) while creating your tabs for mobile.</span></span>

<span data-ttu-id="5c51b-143">Teams reuniões fornece uma experiência colaborativa exclusiva para sua organização.</span><span class="sxs-lookup"><span data-stu-id="5c51b-143">Teams meetings provides a unique collaborative experience for your organization.</span></span> <span data-ttu-id="5c51b-144">Ele oferece a oportunidade de configurar seu aplicativo para diferentes cenários de reunião.</span><span class="sxs-lookup"><span data-stu-id="5c51b-144">It provides the opportunity to configure your app for different meeting scenarios.</span></span> <span data-ttu-id="5c51b-145">Você pode configurar seus aplicativos para aprimorar a experiência de reunião com base na função de participante ou no tipo de usuário.</span><span class="sxs-lookup"><span data-stu-id="5c51b-145">You can configure your apps to enhance the meeting experience based on participant role or user type.</span></span> <span data-ttu-id="5c51b-146">Agora você pode identificar quais ações podem ser tomadas nos seguintes cenários de reunião:</span><span class="sxs-lookup"><span data-stu-id="5c51b-146">Now you can identify what actions can be taken in the following meeting scenarios:</span></span>
* [<span data-ttu-id="5c51b-147">Pré-reunião</span><span class="sxs-lookup"><span data-stu-id="5c51b-147">Pre-meeting</span></span>](#pre-meeting)
* [<span data-ttu-id="5c51b-148">In-meeting</span><span class="sxs-lookup"><span data-stu-id="5c51b-148">In-meeting</span></span>](#in-meeting)
* [<span data-ttu-id="5c51b-149">Pós-reunião</span><span class="sxs-lookup"><span data-stu-id="5c51b-149">Post-meeting</span></span>](#post-meeting)

### <a name="pre-meeting"></a><span data-ttu-id="5c51b-150">Pré-reunião</span><span class="sxs-lookup"><span data-stu-id="5c51b-150">Pre-meeting</span></span>

<span data-ttu-id="5c51b-151">Antes de uma reunião, os usuários podem adicionar guias, bots e extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="5c51b-151">Before a meeting, users can add tabs, bots, and messaging extensions.</span></span> <span data-ttu-id="5c51b-152">Os usuários com funções de organizador e apresentador podem adicionar guias a uma reunião.</span><span class="sxs-lookup"><span data-stu-id="5c51b-152">Users with organizer and presenter roles can add tabs to a meeting.</span></span>

<span data-ttu-id="5c51b-153">**Para adicionar uma guia a uma reunião**</span><span class="sxs-lookup"><span data-stu-id="5c51b-153">**To add a tab to a meeting**</span></span>

1. <span data-ttu-id="5c51b-154">Em seu calendário, selecione uma reunião à qual deseja adicionar uma guia.</span><span class="sxs-lookup"><span data-stu-id="5c51b-154">In your calendar, select a meeting to which you want to add a tab.</span></span>
1. <span data-ttu-id="5c51b-155">Selecione a **guia Detalhes** e selecione</span><span class="sxs-lookup"><span data-stu-id="5c51b-155">Select the **Details** tab and select</span></span> <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/><span data-ttu-id="5c51b-156">.</span><span class="sxs-lookup"><span data-stu-id="5c51b-156">.</span></span>

    ![Experiência de pré-reunião](../assets/images/apps-in-meetings/PreMeeting.png)

1. <span data-ttu-id="5c51b-158">Na galeria de guias exibida, selecione o aplicativo que você deseja adicionar e siga as etapas conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="5c51b-158">In the tab gallery that appears, select the app that you want to add and follow the steps as required.</span></span> <span data-ttu-id="5c51b-159">O aplicativo é instalado como uma guia.</span><span class="sxs-lookup"><span data-stu-id="5c51b-159">The app is installed as a tab.</span></span>

    > [!NOTE]
    > <span data-ttu-id="5c51b-160">Atualmente, na guia reuniões, não há suporte para obter detalhes da reunião e informações dos participantes.</span><span class="sxs-lookup"><span data-stu-id="5c51b-160">Currently, in meetings tab, getting meeting details and participant information is not supported.</span></span>

<span data-ttu-id="5c51b-161">**Para adicionar uma extensão de mensagens a uma reunião**</span><span class="sxs-lookup"><span data-stu-id="5c51b-161">**To add a messaging extension to a meeting**</span></span>

1. <span data-ttu-id="5c51b-162">Selecione as releições &#x25CF;&#x25CF;&#x25CF; localizadas na área de mensagem de composição no chat.</span><span class="sxs-lookup"><span data-stu-id="5c51b-162">Select the ellipses &#x25CF;&#x25CF;&#x25CF; located in the compose message area in the chat.</span></span>
1. <span data-ttu-id="5c51b-163">Selecione o aplicativo que você deseja adicionar e siga as etapas conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="5c51b-163">Select the app that you want to add and follow the steps as required.</span></span> <span data-ttu-id="5c51b-164">O aplicativo é instalado como uma extensão de mensagens.</span><span class="sxs-lookup"><span data-stu-id="5c51b-164">The app is installed as a messaging extension.</span></span>

<span data-ttu-id="5c51b-165">**Para adicionar um bot a uma reunião**</span><span class="sxs-lookup"><span data-stu-id="5c51b-165">**To add a bot to a meeting**</span></span>

<span data-ttu-id="5c51b-166">Em um chat de reunião, insira a **@** chave e selecione Obter **bots**.</span><span class="sxs-lookup"><span data-stu-id="5c51b-166">In a meeting chat, enter the **@** key and select **Get bots**.</span></span>

> [!NOTE]
> * <span data-ttu-id="5c51b-167">A identidade do usuário deve ser confirmada usando [Guias SSO](../tabs/how-to/authentication/auth-aad-sso.md).</span><span class="sxs-lookup"><span data-stu-id="5c51b-167">The user identity must be confirmed using [Tabs SSO](../tabs/how-to/authentication/auth-aad-sso.md).</span></span> <span data-ttu-id="5c51b-168">Após a autenticação, o aplicativo pode recuperar a função de usuário usando a `GetParticipant` API.</span><span class="sxs-lookup"><span data-stu-id="5c51b-168">After authentication, the app can retrieve the user role using the `GetParticipant` API.</span></span>
> * <span data-ttu-id="5c51b-169">Com base na função de usuário, o aplicativo tem a capacidade de fornecer experiências específicas de função.</span><span class="sxs-lookup"><span data-stu-id="5c51b-169">Based on the user role, the app has the capability to provide role specific experiences.</span></span> <span data-ttu-id="5c51b-170">Por exemplo, um aplicativo de sondagem permite que apenas organizadores e apresentadores criem uma nova sondagem.</span><span class="sxs-lookup"><span data-stu-id="5c51b-170">For example, a polling app allows only organizers and presenters to create a new poll.</span></span>
> * <span data-ttu-id="5c51b-171">As atribuições de função podem ser alteradas enquanto uma reunião está em andamento.</span><span class="sxs-lookup"><span data-stu-id="5c51b-171">Role assignments can be changed while a meeting is in progress.</span></span> <span data-ttu-id="5c51b-172">Para obter mais informações, [consulte funções em uma Teams reunião](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span><span class="sxs-lookup"><span data-stu-id="5c51b-172">For more information, see [roles in a Teams meeting](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span></span>

### <a name="in-meeting"></a><span data-ttu-id="5c51b-173">In-meeting</span><span class="sxs-lookup"><span data-stu-id="5c51b-173">In-meeting</span></span>

<span data-ttu-id="5c51b-174">Durante uma reunião, você pode usar a caixa de diálogo meetingSidePanel ou in-meeting para criar experiências exclusivas para seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="5c51b-174">During a meeting, you can use the meetingSidePanel or the in-meeting dialog box to build unique experiences for your apps.</span></span>

#### <a name="meetingsidepanel"></a><span data-ttu-id="5c51b-175">meetingSidePanel</span><span class="sxs-lookup"><span data-stu-id="5c51b-175">meetingSidePanel</span></span>

<span data-ttu-id="5c51b-176">Com o meetingSidePanel, você pode personalizar experiências em uma reunião que permite que os organizadores e apresentadores tenham diferentes tipos de exibição e ações.</span><span class="sxs-lookup"><span data-stu-id="5c51b-176">With the meetingSidePanel, you can customize experiences in a meeting that enable organizers and presenters to have different set of views and actions.</span></span> <span data-ttu-id="5c51b-177">No manifesto do aplicativo, você deve adicionar meetingSidePanel à matriz de contexto.</span><span class="sxs-lookup"><span data-stu-id="5c51b-177">In your app manifest, you must add meetingSidePanel to the context array.</span></span> <span data-ttu-id="5c51b-178">Na reunião e em todos os cenários, o aplicativo é renderizado em uma guia na reunião que tem 320 pixels de largura.</span><span class="sxs-lookup"><span data-stu-id="5c51b-178">In the meeting and in all scenarios, the app is rendered in an in-meeting tab that is 320 pixels in width.</span></span> <span data-ttu-id="5c51b-179">Para obter mais informações, consulte [Interface FrameContext](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="5c51b-179">For more information, see [FrameContext interface](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true).</span></span>

<span data-ttu-id="5c51b-180">Para usar a `userContext` API para rotear solicitações de acordo, [consulte Teams SDK](../tabs/how-to/access-teams-context.md#user-context).</span><span class="sxs-lookup"><span data-stu-id="5c51b-180">To use the `userContext` API to route requests accordingly, see [Teams SDK](../tabs/how-to/access-teams-context.md#user-context).</span></span> <span data-ttu-id="5c51b-181">Para obter mais informações, [consulte Teams fluxo de autenticação para guias](../tabs/how-to/authentication/auth-flow-tab.md).</span><span class="sxs-lookup"><span data-stu-id="5c51b-181">For more information, see [Teams authentication flow for tabs](../tabs/how-to/authentication/auth-flow-tab.md).</span></span> <span data-ttu-id="5c51b-182">O fluxo de autenticação para guias é muito semelhante ao fluxo de autenticação para sites.</span><span class="sxs-lookup"><span data-stu-id="5c51b-182">Authentication flow for tabs is very similar to the authentication flow for websites.</span></span> <span data-ttu-id="5c51b-183">Portanto, as guias podem usar o OAuth 2.0 diretamente.</span><span class="sxs-lookup"><span data-stu-id="5c51b-183">So tabs can use OAuth 2.0 directly.</span></span> <span data-ttu-id="5c51b-184">Para obter mais informações, consulte plataforma de identidade da Microsoft fluxo de código de autorização [do OAuth 2.0 e do OAuth 2.0.](/azure/active-directory/develop/v2-oauth2-auth-code-flow)</span><span class="sxs-lookup"><span data-stu-id="5c51b-184">For more information, see [Microsoft identity platform and OAuth 2.0 authorization code flow](/azure/active-directory/develop/v2-oauth2-auth-code-flow).</span></span>

<span data-ttu-id="5c51b-185">A extensão de mensagens funciona conforme o esperado quando um usuário está em uma exibição em reunião e o usuário pode postar cartões de extensão de mensagem de composição.</span><span class="sxs-lookup"><span data-stu-id="5c51b-185">Messaging extension works as expected when a user is in an in-meeting view, and the user can post compose message extension cards.</span></span> <span data-ttu-id="5c51b-186">AppName in-meeting é uma dica de ferramenta que informa o nome do aplicativo na U-bar de reunião.</span><span class="sxs-lookup"><span data-stu-id="5c51b-186">AppName in-meeting is a tooltip that states the app name in-meeting U-bar.</span></span>

> [!NOTE]
> <span data-ttu-id="5c51b-187">Use a versão 1.7.0 ou superior do [Teams SDK,](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)pois as versões anteriores a ele não suportam o painel lateral.</span><span class="sxs-lookup"><span data-stu-id="5c51b-187">Use version 1.7.0 or higher of [Teams SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true), as versions prior to it do not support the side panel.</span></span>

#### <a name="in-meeting-dialog-box"></a><span data-ttu-id="5c51b-188">Caixa de diálogo na reunião</span><span class="sxs-lookup"><span data-stu-id="5c51b-188">In-meeting dialog box</span></span>

<span data-ttu-id="5c51b-189">A caixa de diálogo na reunião pode ser usada para envolver os participantes durante a reunião e coletar informações ou comentários durante a reunião.</span><span class="sxs-lookup"><span data-stu-id="5c51b-189">The in-meeting dialog box can be used to engage participants during the meeting and collect information or feedback during the meeting.</span></span> <span data-ttu-id="5c51b-190">Use a [`NotificationSignal`](create-apps-for-teams-meetings.md#notificationsignal-api) API para sinalizar que uma notificação de bolha deve ser disparada.</span><span class="sxs-lookup"><span data-stu-id="5c51b-190">Use the [`NotificationSignal`](create-apps-for-teams-meetings.md#notificationsignal-api) API to signal that a bubble notification must be triggered.</span></span> <span data-ttu-id="5c51b-191">Como parte da carga da solicitação de notificação, inclua a URL onde o conteúdo a ser mostrado está hospedado.</span><span class="sxs-lookup"><span data-stu-id="5c51b-191">As part of the notification request payload, include the URL where the content to be shown is hosted.</span></span>

<span data-ttu-id="5c51b-192">A caixa de diálogo na reunião não deve usar o módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="5c51b-192">In-meeting dialog must not use task module.</span></span> <span data-ttu-id="5c51b-193">O módulo de tarefa não é invocado em um chat de reunião.</span><span class="sxs-lookup"><span data-stu-id="5c51b-193">Task module is not invoked in a meeting chat.</span></span> <span data-ttu-id="5c51b-194">Uma URL de recurso externo é usada para exibir a bolha de conteúdo em uma reunião.</span><span class="sxs-lookup"><span data-stu-id="5c51b-194">An external resource URL is used to display content bubble in a meeting.</span></span> <span data-ttu-id="5c51b-195">Você pode usar o `submitTask` método para enviar dados em um chat de reunião.</span><span class="sxs-lookup"><span data-stu-id="5c51b-195">You can use the `submitTask` method to submit data in a meeting chat.</span></span>

> [!NOTE]
> * <span data-ttu-id="5c51b-196">Você deve invocar [a função submitTask()](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) para descartar automaticamente depois que um usuário realizar uma ação no visualização da Web.</span><span class="sxs-lookup"><span data-stu-id="5c51b-196">You must invoke the [submitTask()](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) function to dismiss automatically after a user takes an action in the web view.</span></span> <span data-ttu-id="5c51b-197">Esse é um requisito para envio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5c51b-197">This is a requirement for app submission.</span></span> <span data-ttu-id="5c51b-198">Para obter mais informações, consulte Teams módulo de tarefa [do SDK.](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="5c51b-198">For more information, see [Teams SDK task module](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).</span></span>
> * <span data-ttu-id="5c51b-199">Se você quiser que seu aplicativo suporte usuários anônimos, sua carga inicial de solicitação de invocação deve depender dos metadados de solicitação no objeto, não `from.id` `from` nos `from.aadObjectId` metadados de solicitação.</span><span class="sxs-lookup"><span data-stu-id="5c51b-199">If you want your app to support anonymous users, your initial invoke request payload must rely on the `from.id` request metadata in the `from` object, not the `from.aadObjectId` request metadata.</span></span> <span data-ttu-id="5c51b-200">`from.id`é a ID do usuário `from.aadObjectId` e é a ID Azure Active Directory (AAD) do usuário.</span><span class="sxs-lookup"><span data-stu-id="5c51b-200">`from.id` is the user ID and `from.aadObjectId` is the Azure Active Directory (AAD) ID of the user.</span></span> <span data-ttu-id="5c51b-201">Para obter mais informações, [consulte using task modules in tabs](../task-modules-and-cards/task-modules/task-modules-tabs.md) e [create and send the task module](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).</span><span class="sxs-lookup"><span data-stu-id="5c51b-201">For more information, see [using task modules in tabs](../task-modules-and-cards/task-modules/task-modules-tabs.md) and [create and send the task module](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).</span></span>

#### <a name="share-to-stage"></a><span data-ttu-id="5c51b-202">Compartilhar em estágio</span><span class="sxs-lookup"><span data-stu-id="5c51b-202">Share to stage</span></span>

> [!NOTE]
> * <span data-ttu-id="5c51b-203">Esse recurso está disponível apenas na visualização [do](../resources/dev-preview/developer-preview-intro.md) desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="5c51b-203">This capability is currently available in [developer preview](../resources/dev-preview/developer-preview-intro.md) only.</span></span>
> * <span data-ttu-id="5c51b-204">Para usar esse recurso, o aplicativo deve dar suporte a uma reunião em reuniãoSidePanel.</span><span class="sxs-lookup"><span data-stu-id="5c51b-204">To use this feature, the app must support an in-meeting meetingSidePanel.</span></span>

<span data-ttu-id="5c51b-205">Esse recurso oferece aos desenvolvedores a capacidade de compartilhar um aplicativo no estágio de reunião.</span><span class="sxs-lookup"><span data-stu-id="5c51b-205">This capability gives developers the ability to share an app to the meeting stage.</span></span> <span data-ttu-id="5c51b-206">Habilitando o compartilhamento para o estágio de reunião, os participantes da reunião podem colaborar em tempo real.</span><span class="sxs-lookup"><span data-stu-id="5c51b-206">By enabling share to the meeting stage, meeting participants can collaborate in real-time.</span></span>

<span data-ttu-id="5c51b-207">O contexto necessário está `meetingStage` no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5c51b-207">The required context is `meetingStage` in the app manifest.</span></span> <span data-ttu-id="5c51b-208">Um pré-requisito para isso é ter o `meetingSidePanel` contexto.</span><span class="sxs-lookup"><span data-stu-id="5c51b-208">A prerequisite for this is to have the `meetingSidePanel` context.</span></span> <span data-ttu-id="5c51b-209">Isso habilita **o Compartilhamento** no meetingSidePanel.</span><span class="sxs-lookup"><span data-stu-id="5c51b-209">This enables **Share** in the meetingSidePanel.</span></span>

![Compartilhar em estágios durante a experiência de reunião](~/assets/images/apps-in-meetings/share_to_stage_during_meeting.png)

<span data-ttu-id="5c51b-211">A alteração de manifesto necessária para habilitar esse recurso é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="5c51b-211">The manifest change that is needed to enable this capability is as follows:</span></span>

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

### <a name="post-meeting"></a><span data-ttu-id="5c51b-212">Pós-reunião</span><span class="sxs-lookup"><span data-stu-id="5c51b-212">Post-meeting</span></span>

<span data-ttu-id="5c51b-213">As configurações pós-reunião [e pré-reunião](#pre-meeting) são as mesmas.</span><span class="sxs-lookup"><span data-stu-id="5c51b-213">The post-meeting and [pre-meeting](#pre-meeting) configurations are the same.</span></span>

## <a name="code-sample"></a><span data-ttu-id="5c51b-214">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="5c51b-214">Code sample</span></span>

|<span data-ttu-id="5c51b-215">Exemplo de nome</span><span class="sxs-lookup"><span data-stu-id="5c51b-215">Sample name</span></span> | <span data-ttu-id="5c51b-216">Descrição</span><span class="sxs-lookup"><span data-stu-id="5c51b-216">Description</span></span> | <span data-ttu-id="5c51b-217">Amostra</span><span class="sxs-lookup"><span data-stu-id="5c51b-217">Sample</span></span> |
|----------------|-----------------|--------------|----------------|-----------|
| <span data-ttu-id="5c51b-218">Aplicativo de reunião</span><span class="sxs-lookup"><span data-stu-id="5c51b-218">Meeting app</span></span> | <span data-ttu-id="5c51b-219">Demonstra como usar o aplicativo Gerador de Token de Reunião para solicitar um token, que é gerado sequencialmente para que cada participante tenha uma oportunidade justa de interagir.</span><span class="sxs-lookup"><span data-stu-id="5c51b-219">Demonstrates how to use the Meeting Token Generator app to request a token, which is generated sequentially so that each participant has a fair opportunity to interact.</span></span> <span data-ttu-id="5c51b-220">Isso pode ser útil em situações como reuniões scrum,&A e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="5c51b-220">This can be useful in situations like scrum meetings, Q&A sessions, and so on.</span></span> | [<span data-ttu-id="5c51b-221">View</span><span class="sxs-lookup"><span data-stu-id="5c51b-221">View</span></span>](https://github.com/OfficeDev/microsoft-teams-sample-meetings-token) |

## <a name="see-also"></a><span data-ttu-id="5c51b-222">Confira também</span><span class="sxs-lookup"><span data-stu-id="5c51b-222">See also</span></span>

* [<span data-ttu-id="5c51b-223">Diretrizes de design de caixa de diálogo na reunião</span><span class="sxs-lookup"><span data-stu-id="5c51b-223">In-meeting dialog design guidelines</span></span>](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
* [<span data-ttu-id="5c51b-224">Teams fluxo de autenticação para guias</span><span class="sxs-lookup"><span data-stu-id="5c51b-224">Teams authentication flow for tabs</span></span>](../tabs/how-to/authentication/auth-flow-tab.md)
