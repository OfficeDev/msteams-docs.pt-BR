---
title: Aplicativos em reuniões do Teams
author: laujan
description: visão geral dos aplicativos em reuniões do Teams com base na função de usuário e participante
ms.topic: overview
ms.author: lajanuar
keywords: api de função de participante de reuniões de aplicativos do teams
ms.openlocfilehash: ac4e270090dd89d370d37de88b8cba552b77a5cb
ms.sourcegitcommit: 3727fc58e84b6f1752612884c2e0b25e207fb56e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2021
ms.locfileid: "51382335"
---
# <a name="apps-in-teams-meetings"></a><span data-ttu-id="56a76-104">Aplicativos em reuniões do Teams</span><span class="sxs-lookup"><span data-stu-id="56a76-104">Apps in Teams meetings</span></span>

<span data-ttu-id="56a76-105">As reuniões permitem colaboração, parceria, comunicação informada e comentários compartilhados em um fórum inclusivo e ativo.</span><span class="sxs-lookup"><span data-stu-id="56a76-105">Meetings enable collaboration, partnership, informed communication, and shared feedback in an inclusive and active forum.</span></span> <span data-ttu-id="56a76-106">O aplicativo de reunião pode oferecer uma experiência do usuário para cada estágio do ciclo de vida da reunião, incluindo a experiência do aplicativo pré-reunião, na reunião e pós-reunião, dependendo do status do participante.</span><span class="sxs-lookup"><span data-stu-id="56a76-106">The meeting app can deliver a user experience for each stage of the meeting lifecycle including pre-meeting, in-meeting and post-meeting app experience, depending on the attendee's status.</span></span>

<span data-ttu-id="56a76-107">Os usuários finais do Teams podem acessar aplicativos durante reuniões usando a galeria de guias, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="56a76-107">Teams end-users can access apps during meetings using the tab gallery, for example:</span></span>

* <span data-ttu-id="56a76-108">Pré-estágio de um quadro Kanban</span><span class="sxs-lookup"><span data-stu-id="56a76-108">Pre-stage a Kanban board</span></span>
* <span data-ttu-id="56a76-109">Iniciar uma caixa de diálogo acionável na reunião</span><span class="sxs-lookup"><span data-stu-id="56a76-109">Launch an in-meeting actionable dialog</span></span>
* <span data-ttu-id="56a76-110">Criar uma sondagem pós-reunião</span><span class="sxs-lookup"><span data-stu-id="56a76-110">Create a post-meeting poll</span></span>

<span data-ttu-id="56a76-111">A extensibilidade do aplicativo de reunião do Teams baseia-se nos seguintes conceitos:</span><span class="sxs-lookup"><span data-stu-id="56a76-111">Teams’ meeting app extensibility is based on the following concepts:</span></span>

<span data-ttu-id="56a76-112">✔ ciclo de vida da reunião tem estágios como antes, durante e após o período de tempo de reunião.</span><span class="sxs-lookup"><span data-stu-id="56a76-112">✔ Meeting lifecycle has stages such as before, during, and after meeting time frame.</span></span>  
<span data-ttu-id="56a76-113">✔ Funções de participante em uma reunião, como organizador da reunião, apresentador ou participante.</span><span class="sxs-lookup"><span data-stu-id="56a76-113">✔ Participant roles in a meeting such as meeting organizer, presenter, or attendee.</span></span>  
<span data-ttu-id="56a76-114">✔ Tipos de usuário em uma reunião, como no locatário, convidado, federado ou usuário anônimo do Teams.</span><span class="sxs-lookup"><span data-stu-id="56a76-114">✔ User types in a meeting such as in-tenant, guest, federated, or anonymous Teams user.</span></span>

<span data-ttu-id="56a76-115">Este artigo aborda informações sobre o ciclo de vida da reunião e como integrar guias, bots e extensões de mensagens em sua reunião.</span><span class="sxs-lookup"><span data-stu-id="56a76-115">This article covers information about the meeting lifecycle and how to integrate tabs, bots, and messaging extensions in your meeting.</span></span> <span data-ttu-id="56a76-116">Ele também permite identificar funções de participantes e também usar diferentes tipos de usuário para executar tarefas.</span><span class="sxs-lookup"><span data-stu-id="56a76-116">It also enables you to identify participant roles and also use different user types to perform tasks.</span></span>

> [!NOTE]
> <span data-ttu-id="56a76-117">Para trabalhar com os recursos de extensibilidade do aplicativo de reunião, você deve ter as permissões apropriadas.</span><span class="sxs-lookup"><span data-stu-id="56a76-117">To work with the meeting app extensibility features, you must have the appropriate permissions.</span></span>

### <a name="meeting-lifecycle"></a><span data-ttu-id="56a76-118">Ciclo de vida da reunião</span><span class="sxs-lookup"><span data-stu-id="56a76-118">Meeting lifecycle</span></span>

<span data-ttu-id="56a76-119">O ciclo de vida da reunião consiste na experiência do aplicativo de pré-reunião, na reunião e pós-reunião.</span><span class="sxs-lookup"><span data-stu-id="56a76-119">Meeting lifecycle consists of pre-meeting, in-meeting, and post-meeting app experience.</span></span> <span data-ttu-id="56a76-120">Você pode integrar guias, bots e extensões de mensagens em cada estágio do ciclo de vida da reunião.</span><span class="sxs-lookup"><span data-stu-id="56a76-120">You can integrate tabs, bots, and messaging extensions in each stage of the meeting lifecycle.</span></span>

## <a name="integrate-tabs-into-the-meeting-lifecycle"></a><span data-ttu-id="56a76-121">Integrar guias ao ciclo de vida da reunião</span><span class="sxs-lookup"><span data-stu-id="56a76-121">Integrate tabs into the meeting lifecycle</span></span>

<span data-ttu-id="56a76-122">As guias permitem que os membros da equipe acessem serviços e conteúdo em um espaço específico em um canal ou chat.</span><span class="sxs-lookup"><span data-stu-id="56a76-122">Tabs allow team members to access services and content in a specific space within a channel or chat.</span></span> <span data-ttu-id="56a76-123">Isso permite que a equipe trabalhe diretamente com guias e tenha conversas sobre as ferramentas e dados disponíveis nas guias.</span><span class="sxs-lookup"><span data-stu-id="56a76-123">This lets the team work directly with tabs and have conversations about the tools and data available within tabs.</span></span> <span data-ttu-id="56a76-124">Na reunião do Teams, os usuários podem adicionar uma guia selecionando mais</span><span class="sxs-lookup"><span data-stu-id="56a76-124">In Teams meeting, users can add a tab by selecting plus</span></span> <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/><span data-ttu-id="56a76-125">e escolher o aplicativo que eles querem instalar como uma guia.</span><span class="sxs-lookup"><span data-stu-id="56a76-125">, and choosing the app that they want to install as a tab.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="56a76-126">Se você tiver integrado uma guia à sua reunião, seu aplicativo deverá seguir o fluxo de autenticação de logom único [(SSO)](../tabs/how-to/authentication/auth-aad-sso.md) do Teams para guias.</span><span class="sxs-lookup"><span data-stu-id="56a76-126">If you have integrated a tab with your meeting, then your app must follow the Teams [single sign-on (SSO) authentication flow](../tabs/how-to/authentication/auth-aad-sso.md) for tabs.</span></span>

> [!NOTE]
> * <span data-ttu-id="56a76-127">Os clientes móveis suportam guias somente em estágios pré e pós-reunião.</span><span class="sxs-lookup"><span data-stu-id="56a76-127">Mobile clients support tabs only in pre and post meeting stages.</span></span> <span data-ttu-id="56a76-128">As experiências em reunião que estão na caixa de diálogo e no painel da reunião não estão disponíveis no momento em dispositivos móveis.</span><span class="sxs-lookup"><span data-stu-id="56a76-128">The in-meeting experiences that is in-meeting dialog and panel are currently not available on mobile.</span></span>
> * <span data-ttu-id="56a76-129">Os aplicativos têm suporte apenas em reuniões agendadas privadas.</span><span class="sxs-lookup"><span data-stu-id="56a76-129">Apps are supported only in private scheduled meetings.</span></span>

### <a name="pre-meeting-app-experience"></a><span data-ttu-id="56a76-130">Experiência do aplicativo de pré-reunião</span><span class="sxs-lookup"><span data-stu-id="56a76-130">Pre-meeting app experience</span></span>

<span data-ttu-id="56a76-131">**Experiência de pré-reunião:**</span><span class="sxs-lookup"><span data-stu-id="56a76-131">**Pre-meeting experience:**</span></span>

![experiência de pré-reunião](../assets/images/apps-in-meetings/PreMeeting.png)

<span data-ttu-id="56a76-133">**Guia Pré-reunião:**</span><span class="sxs-lookup"><span data-stu-id="56a76-133">**Pre-meeting tab:**</span></span>

![exibição de guia de pré-reunião](../assets/images/apps-in-meetings/PreMeetingTab.png)

<span data-ttu-id="56a76-135">✔ usuários com permissão são usuários que podem adicionar aplicativos a uma reunião durante diferentes estágios do ciclo de vida da reunião.</span><span class="sxs-lookup"><span data-stu-id="56a76-135">✔ Permissioned users are users who can add apps to a meeting during different stages of the meeting lifecycle.</span></span> <span data-ttu-id="56a76-136">Esses usuários podem adicionar aplicativos a uma reunião por meio da galeria de guias de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="56a76-136">These users can add apps to a meeting through the tab gallery in two ways:</span></span>

   * <span data-ttu-id="56a76-137">Usando a **guia Detalhes** no formulário de agendamento do Teams.</span><span class="sxs-lookup"><span data-stu-id="56a76-137">Using the **Details** tab on the Teams scheduling form.</span></span>

   * <span data-ttu-id="56a76-138">Usando a guia **Chat de** reunião em uma reunião existente.</span><span class="sxs-lookup"><span data-stu-id="56a76-138">Using the meeting **Chat** tab in an existing meeting.</span></span>

<span data-ttu-id="56a76-139">✔ aplicativos tab são acessíveis em reuniões **Páginas detalhes** e **chats** usando um botão de ➕ de adoção.</span><span class="sxs-lookup"><span data-stu-id="56a76-139">✔ Tab apps are accessible in meetings **Details** and **Chats** pages using a plus ➕ button.</span></span>

<span data-ttu-id="56a76-140">✔ layout tab deve estar em um estado organizado se houver mais de dez pesquisas ou pesquisas.</span><span class="sxs-lookup"><span data-stu-id="56a76-140">✔ Tab layout must be in an organized state if there are more than ten polls or surveys.</span></span>

### <a name="in-meeting-app-experience"></a><span data-ttu-id="56a76-141">Experiência do aplicativo na reunião</span><span class="sxs-lookup"><span data-stu-id="56a76-141">In-meeting app experience</span></span>

<span data-ttu-id="56a76-142">✔ aplicativos de reunião são hospedados na barra superior superior da janela de chat e como experiência de guia na reunião usando a guia na reunião. Quando os usuários adicionam uma guia a uma reunião por meio da galeria de guias, os aplicativos que são **durante as experiências de** reunião são mostrados.</span><span class="sxs-lookup"><span data-stu-id="56a76-142">✔ Meeting apps are hosted in the top upper bar of the chat window and as in-meeting tab experience using the in-meeting tab. When users add a tab to a meeting through the tab gallery, apps that are **during meeting** experiences are shown.</span></span>

<span data-ttu-id="56a76-143">✔ usuários com permissão podem adicionar aplicativos durante a reunião.</span><span class="sxs-lookup"><span data-stu-id="56a76-143">✔ Permissioned users can add apps while in the meeting.</span></span>

<span data-ttu-id="56a76-144">✔ Quando carregado no contexto de uma reunião, os aplicativos podem aproveitar o SDK do Cliente do Teams para acessar o , e renderizar adequadamente `meetingId` `userMri` a `frameContext` experiência.</span><span class="sxs-lookup"><span data-stu-id="56a76-144">✔ When loaded in the context of a meeting, apps can leverage the Teams Client SDK to access the `meetingId`, `userMri`, and `frameContext` to appropriately render the experience.</span></span>

<span data-ttu-id="56a76-145">✔ Exportar um resultado de uma pesquisa ou sondagem notifica os usuários que os resultados foram baixados com êxito.</span><span class="sxs-lookup"><span data-stu-id="56a76-145">✔ Exporting a result of a survey or poll notifies the users that the results successfully downloaded.</span></span>

<span data-ttu-id="56a76-146">✔ Um aplicativo fica visível em uma reunião do Teams no painel lateral ou na caixa de diálogo na reunião.</span><span class="sxs-lookup"><span data-stu-id="56a76-146">✔ An app is visible in a Teams meeting in the side panel or the in-meeting dialog box.</span></span> <span data-ttu-id="56a76-147">Use a caixa de diálogo na reunião para mostrar conteúdo a actionable para os participantes da reunião.</span><span class="sxs-lookup"><span data-stu-id="56a76-147">Use the in-meeting dialog to showcase actionable content for meeting participants.</span></span> <span data-ttu-id="56a76-148">*Consulte* [Criar aplicativos para reuniões do Teams.](create-apps-for-teams-meetings.md)</span><span class="sxs-lookup"><span data-stu-id="56a76-148">*See* [Create Apps for Teams meetings](create-apps-for-teams-meetings.md).</span></span>

   > [!NOTE]
   > <span data-ttu-id="56a76-149">O manifesto do aplicativo especifica que sua guia é [otimizada](create-apps-for-teams-meetings.md#during-a-meeting)para o painel lateral , que é onde ele é exibido.</span><span class="sxs-lookup"><span data-stu-id="56a76-149">Your app manifest specifies that your tab is [optimized for side panel](create-apps-for-teams-meetings.md#during-a-meeting), that is where it is displayed.</span></span> <span data-ttu-id="56a76-150">Ele também pode fazer parte de uma experiência de bandeja de compartilhamento, sujeito a diretrizes de design especificadas.</span><span class="sxs-lookup"><span data-stu-id="56a76-150">It can also be part of a share-tray experience, subject to specified design guidelines.</span></span>

<span data-ttu-id="56a76-151">As imagens a seguir exibem o aplicativo como uma caixa de diálogo na reunião e como um painel lateral separado:</span><span class="sxs-lookup"><span data-stu-id="56a76-151">The following images display the app as an in-meeting dialog box and as a separate side panel:</span></span>

![Experiência na reunião](../assets/images/apps-in-meetings/in-meeting-experience.png)

![Exibição de diálogo na reunião](../assets/images/apps-in-meetings/in-meeting-dialog.png)

#### <a name="in-meeting-actionable-dialog-for-users"></a><span data-ttu-id="56a76-154">Caixa de diálogo a actionable na reunião para usuários</span><span class="sxs-lookup"><span data-stu-id="56a76-154">In-meeting actionable dialog for users</span></span>

![Exibição de caixa de diálogo](../assets/images/apps-in-meetings/in-meeting-dialog-view.png)

### <a name="post-meeting-app-experience"></a><span data-ttu-id="56a76-156">Experiência de aplicativo pós-reunião</span><span class="sxs-lookup"><span data-stu-id="56a76-156">Post-meeting app experience</span></span>

![Exibição pós-reunião](../assets/images/apps-in-meetings/PostMeeting.png)

<span data-ttu-id="56a76-158">✔ O cenário do aplicativo pós-reunião é semelhante à experiência atual pós-reunião com o benefício adicionado de ter guias que existem dentro da superfície.</span><span class="sxs-lookup"><span data-stu-id="56a76-158">✔ The post-meeting app scenario is similar to the current post-meeting experience with the added benefit of having tabs that exist within the surface.</span></span>

<span data-ttu-id="56a76-159">✔ os usuários com permissão podem adicionar aplicativos da  galeria de guias a uma reunião usando a guia Detalhes no formulário de agendamento do Teams e a guia **Chat** de reunião em uma reunião existente.</span><span class="sxs-lookup"><span data-stu-id="56a76-159">✔ Permissioned users can add apps from the tab gallery to a meeting using the **Details** tab on the Teams scheduling form and the meeting **Chat** tab in an existing meeting.</span></span>

<span data-ttu-id="56a76-160">✔ layout da guia deve ser organizado quando houver mais de dez pesquisas ou pesquisas.</span><span class="sxs-lookup"><span data-stu-id="56a76-160">✔  Tab layout must be organized when there are more than ten polls or surveys.</span></span>

### <a name="integrate-bots-into-the-meeting-lifecycle"></a><span data-ttu-id="56a76-161">Integrar bots ao ciclo de vida da reunião</span><span class="sxs-lookup"><span data-stu-id="56a76-161">Integrate bots into the meeting lifecycle</span></span>

<span data-ttu-id="56a76-162">Para implementação de bot, comece com [a complicação de um bot](../build-your-first-app/build-bot.md) e continue com a criação de [aplicativos para reuniões do Teams.](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-reference)</span><span class="sxs-lookup"><span data-stu-id="56a76-162">For bot implementation, start with [build a bot](../build-your-first-app/build-bot.md) and then continue with [create apps for Teams meetings](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-reference).</span></span>

### <a name="integrate-messaging-extensions-into-the-meeting-lifecycle"></a><span data-ttu-id="56a76-163">Integrar extensões de mensagens ao ciclo de vida da reunião</span><span class="sxs-lookup"><span data-stu-id="56a76-163">Integrate messaging extensions into the meeting lifecycle</span></span>

<span data-ttu-id="56a76-164">Para implementação de extensão de mensagens, comece com [a criação](../messaging-extensions/how-to/create-messaging-extension.md) de uma extensão de mensagens e continue com a criação de [aplicativos para reuniões do Teams.](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-reference)</span><span class="sxs-lookup"><span data-stu-id="56a76-164">For messaging extension implementation, start with [build a messaging extension](../messaging-extensions/how-to/create-messaging-extension.md) and then continue with [create apps for Teams meetings](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-reference).</span></span>

## <a name="participant-roles-and-user-types-in-a-meeting"></a><span data-ttu-id="56a76-165">Funções de participante e tipos de usuário em uma reunião</span><span class="sxs-lookup"><span data-stu-id="56a76-165">Participant roles and user types in a meeting</span></span>

![Participantes de uma reunião](../assets/images/apps-in-meetings/participant-roles.png)

### <a name="participant-roles"></a><span data-ttu-id="56a76-167">Funções de participante</span><span class="sxs-lookup"><span data-stu-id="56a76-167">Participant roles</span></span>

<span data-ttu-id="56a76-168">As configurações de participante padrão são determinadas pelo administrador de IT de uma organização.</span><span class="sxs-lookup"><span data-stu-id="56a76-168">Default participant settings are determined by an organization's IT administrator.</span></span> <span data-ttu-id="56a76-169">Veja a seguir as funções dos participantes em uma reunião:</span><span class="sxs-lookup"><span data-stu-id="56a76-169">The following are the participant roles in a meeting:</span></span>

* <span data-ttu-id="56a76-170">**Organizador**: o organizador agenda uma reunião, define as opções de reunião, atribui funções de reunião e inicia a reunião.</span><span class="sxs-lookup"><span data-stu-id="56a76-170">**Organizer**: The organizer schedules a meeting, sets the meeting options, assigns meeting roles, and starts the meeting.</span></span> <span data-ttu-id="56a76-171">Somente usuários com uma conta M365 com uma licença do Teams podem ser organizadores e controlar as permissões do participante.</span><span class="sxs-lookup"><span data-stu-id="56a76-171">Only users with a M365 account with a Teams license can be organizers and control attendee permissions.</span></span> <span data-ttu-id="56a76-172">Um organizador da reunião pode alterar as configurações de uma reunião específica.</span><span class="sxs-lookup"><span data-stu-id="56a76-172">A meeting organizer can change the settings for a specific meeting.</span></span> <span data-ttu-id="56a76-173">Os organizadores podem fazer essas alterações na página da Web **opções de** reunião.</span><span class="sxs-lookup"><span data-stu-id="56a76-173">Organizers can make these changes on the **Meeting options** web page.</span></span>
* <span data-ttu-id="56a76-174">**Apresentador :** os apresentadores têm os mesmos recursos que o organizador.</span><span class="sxs-lookup"><span data-stu-id="56a76-174">**Presenter**: Presenters have the same capabilities as organizer.</span></span> <span data-ttu-id="56a76-175">No entanto, um apresentador não pode remover um organizador da sessão ou modificar opções de reunião para a sessão.</span><span class="sxs-lookup"><span data-stu-id="56a76-175">However, a presenter cannot remove an organizer from the session or modify meeting options for the session.</span></span> <span data-ttu-id="56a76-176">Por padrão, os participantes que participam de uma reunião têm a função de apresentador.</span><span class="sxs-lookup"><span data-stu-id="56a76-176">By default, participants joining a meeting have the presenter role.</span></span>
* <span data-ttu-id="56a76-177">**Participante**: um participante é um usuário que foi convidado a participar de uma reunião, mas que não está autorizado a atuar como apresentador.</span><span class="sxs-lookup"><span data-stu-id="56a76-177">**Attendee**: An attendee is a user who has been invited to attend a meeting but who is not authorized to act as a presenter.</span></span> <span data-ttu-id="56a76-178">Os participantes podem interagir com outros membros da reunião, mas não podem gerenciar nenhuma das configurações de reunião ou compartilhar conteúdo.</span><span class="sxs-lookup"><span data-stu-id="56a76-178">Attendees can interact with other meeting members but cannot manage any of the meeting settings or share content.</span></span>

<span data-ttu-id="56a76-179">Somente um organizador ou apresentador pode adicionar, remover ou desinstalar aplicativos.</span><span class="sxs-lookup"><span data-stu-id="56a76-179">Only an organizer or presenter can add, remove, or uninstall apps.</span></span> <span data-ttu-id="56a76-180">Somente organizador ou apresentador pode criar votações em uma reunião.</span><span class="sxs-lookup"><span data-stu-id="56a76-180">Only organizer or presenter can create polls in a meeting.</span></span>

<span data-ttu-id="56a76-181">Para obter mais informações, [consulte funções em uma reunião do Teams](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span><span class="sxs-lookup"><span data-stu-id="56a76-181">For more information, see [roles in a Teams meeting](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).</span></span>

<span data-ttu-id="56a76-182">Você pode acessar a página  **Opções de reunião** da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="56a76-182">You can access the  **Meeting options** page as follows:</span></span>

* <span data-ttu-id="56a76-183">No Teams, vá **para** o logotipo do ![ ](../assets/images/apps-in-meetings/calendar-logo.png) calendário, selecione uma reunião e, em seguida, **opções de reunião.**</span><span class="sxs-lookup"><span data-stu-id="56a76-183">In Teams, go to **Calendar** ![calendar logo](../assets/images/apps-in-meetings/calendar-logo.png), select a meeting, and then **Meeting options**.</span></span>

* <span data-ttu-id="56a76-184">Em um convite de reunião, selecione **Opções de reunião**.</span><span class="sxs-lookup"><span data-stu-id="56a76-184">In a meeting invitation, select **Meeting options**.</span></span>

* <span data-ttu-id="56a76-185">Durante uma reunião, selecione **Mostrar que os participantes** mostram o ícone dos participantes nos ![ ](../assets/images/apps-in-meetings/show-participants.png) controles de reunião.</span><span class="sxs-lookup"><span data-stu-id="56a76-185">During a meeting, select **Show participants** ![show participants icon](../assets/images/apps-in-meetings/show-participants.png) in the meeting controls.</span></span> <span data-ttu-id="56a76-186">Em seguida, acima da lista de participantes, escolha **Gerenciar permissões**.</span><span class="sxs-lookup"><span data-stu-id="56a76-186">Then, above the list of participants, choose **Manage permissions**.</span></span>

### <a name="user-types"></a><span data-ttu-id="56a76-187">Tipos de usuários</span><span class="sxs-lookup"><span data-stu-id="56a76-187">User types</span></span>

> [!NOTE]
> <span data-ttu-id="56a76-188">Os usuários com tipos de usuário específicos atribuídos a eles podem participar de reuniões e assumir uma das funções de participante descritas nas [funções de participante.](#participant-roles)</span><span class="sxs-lookup"><span data-stu-id="56a76-188">Users with specific user types assigned to them can join meetings and assume one of the participant roles described in [participant roles](#participant-roles).</span></span> <span data-ttu-id="56a76-189">O tipo de usuário não está incluído na API **getParticipantRole.**</span><span class="sxs-lookup"><span data-stu-id="56a76-189">The user type is not included in the **getParticipantRole** API.</span></span>

<span data-ttu-id="56a76-190">Os seguintes tipos de usuário identificam o que cada usuário pode fazer e o que podem acessar:</span><span class="sxs-lookup"><span data-stu-id="56a76-190">The following user types identify what each user can do and what they can access:</span></span>

* <span data-ttu-id="56a76-191">**In-tenant**: Os usuários no locatário pertencem à organização e têm credenciais no Azure Active Directory (AAD) para o locatário.</span><span class="sxs-lookup"><span data-stu-id="56a76-191">**In-tenant**: In-tenant users belong to the organization and have credentials in Azure Active Directory (AAD) for the tenant.</span></span> <span data-ttu-id="56a76-192">Eles geralmente são funcionários em tempo integral, no local ou remotos.</span><span class="sxs-lookup"><span data-stu-id="56a76-192">They are usually full-time, onsite, or remote employees.</span></span> <span data-ttu-id="56a76-193">Um usuário no locatário pode ser um organizador, apresentador ou participante.</span><span class="sxs-lookup"><span data-stu-id="56a76-193">An in-tenant user can be an organizer, presenter, or attendee.</span></span>
* <span data-ttu-id="56a76-194">**Convidado**: um convidado é um participante de outra organização convidado para acessar o Teams ou outros recursos no locatário da organização.</span><span class="sxs-lookup"><span data-stu-id="56a76-194">**Guest**: A guest is a participant from another organization invited to access Teams or other resources in the organization's tenant.</span></span> <span data-ttu-id="56a76-195">Os convidados são adicionados ao AAD da sua organização e têm os mesmos recursos do Teams como um membro nativo da equipe com acesso a chats, reuniões e arquivos de equipe.</span><span class="sxs-lookup"><span data-stu-id="56a76-195">Guests are added to your organization’s AAD and have the same Teams capabilities as a native team member with access to team chats, meetings, and files.</span></span> <span data-ttu-id="56a76-196">Um usuário convidado pode ser organizador, apresentador ou participante.</span><span class="sxs-lookup"><span data-stu-id="56a76-196">A guest user can be an organizer, presenter, or attendee.</span></span> <span data-ttu-id="56a76-197">Para obter mais informações, consulte [acesso de convidados no Teams](/microsoftteams/guest-access).</span><span class="sxs-lookup"><span data-stu-id="56a76-197">For more information, see [guest access in Teams](/microsoftteams/guest-access).</span></span>
* <span data-ttu-id="56a76-198">**Federado ou externo**: um usuário federado é um usuário externo do Teams em outra organização que foi convidado a participar de uma reunião.</span><span class="sxs-lookup"><span data-stu-id="56a76-198">**Federated or external**: A federated user is an external Teams user in another organization who has been invited to join a meeting.</span></span> <span data-ttu-id="56a76-199">Esses usuários têm credenciais válidas com parceiros federados e são autorizados pelo Teams.</span><span class="sxs-lookup"><span data-stu-id="56a76-199">These users have valid credentials with federated partners and are authorized by Teams.</span></span> <span data-ttu-id="56a76-200">Eles não têm acesso às suas equipes ou a outros recursos compartilhados da sua organização.</span><span class="sxs-lookup"><span data-stu-id="56a76-200">They do not have access to your teams or other shared resources from your organization.</span></span> <span data-ttu-id="56a76-201">O acesso de convidados é uma opção melhor para usuários externos ter acesso a equipes e canais.</span><span class="sxs-lookup"><span data-stu-id="56a76-201">Guest access is a better option for external users to have access to teams and channels.</span></span> <span data-ttu-id="56a76-202">Para obter mais informações, consulte [manage external access in Teams](/microsoftteams/manage-external-access).</span><span class="sxs-lookup"><span data-stu-id="56a76-202">For more information, see [manage external access in Teams](/microsoftteams/manage-external-access).</span></span>
* <span data-ttu-id="56a76-203">**Anônimo**: os usuários anônimos não têm uma identidade AAD e não são federados com um locatário.</span><span class="sxs-lookup"><span data-stu-id="56a76-203">**Anonymous**: Anonymous users do not have an AAD identity and are not federated with a tenant.</span></span> <span data-ttu-id="56a76-204">O participante anônimo é como um usuário externo, mas sua identidade não é projetada na reunião.</span><span class="sxs-lookup"><span data-stu-id="56a76-204">The anonymous participant is like an external user, but their identity is not projected in the meeting.</span></span> <span data-ttu-id="56a76-205">Os usuários anônimos não podem acessar aplicativos em uma janela de reunião.</span><span class="sxs-lookup"><span data-stu-id="56a76-205">Anonymous users are not able to access apps in a meeting window.</span></span> <span data-ttu-id="56a76-206">Um usuário anônimo não pode ser organizador, mas pode ser apresentador ou participante.</span><span class="sxs-lookup"><span data-stu-id="56a76-206">An anonymous user cannot be an organizer but can be a presenter or attendee.</span></span>

## <a name="see-also"></a><span data-ttu-id="56a76-207">Confira também</span><span class="sxs-lookup"><span data-stu-id="56a76-207">See also</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="56a76-208">Tab</span><span class="sxs-lookup"><span data-stu-id="56a76-208">Tab</span></span>](../tabs/what-are-tabs.md#how-do-tabs-work)

> [!div class="nextstepaction"]
> [<span data-ttu-id="56a76-209">Bot</span><span class="sxs-lookup"><span data-stu-id="56a76-209">Bot</span></span>](../bots/what-are-bots.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="56a76-210">Extensão de mensagem</span><span class="sxs-lookup"><span data-stu-id="56a76-210">Messaging extension</span></span>](../messaging-extensions/what-are-messaging-extensions.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="56a76-211">Criar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="56a76-211">Design your app</span></span>](../apps-in-teams-meetings/design/designing-apps-in-meetings.md)

## <a name="next-steps"></a><span data-ttu-id="56a76-212">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="56a76-212">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="56a76-213">Criar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="56a76-213">Build your app</span></span>](create-apps-for-teams-meetings.md)
