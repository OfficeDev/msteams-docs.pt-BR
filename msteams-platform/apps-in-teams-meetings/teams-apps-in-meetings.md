---
title: Aplicativos em reuniões do Teams
author: laujan
description: visão geral dos aplicativos em reuniões do Teams com base na função de usuário e participante
ms.topic: overview
ms.author: lajanuar
keywords: api de função de participante de reuniões de aplicativos do teams
ms.openlocfilehash: 51fe2e0ebdaa56197bbebd1e5dbcf90698fb1f92
ms.sourcegitcommit: 23ed7edf145df10dcfba15c43978eae9e0d451a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2021
ms.locfileid: "50753550"
---
# <a name="apps-in-teams-meetings"></a><span data-ttu-id="42cb5-104">Aplicativos em reuniões do Teams</span><span class="sxs-lookup"><span data-stu-id="42cb5-104">Apps in Teams meetings</span></span>

<span data-ttu-id="42cb5-105">As reuniões são fundamentais para a produtividade no Teams.</span><span class="sxs-lookup"><span data-stu-id="42cb5-105">Meetings are key to productivity in Teams.</span></span> <span data-ttu-id="42cb5-106">Eles permitem colaboração, parceria, comunicação informada e comentários compartilhados em um fórum inclusivo e ativo.</span><span class="sxs-lookup"><span data-stu-id="42cb5-106">They enable collaboration, partnership, informed communication, and shared feedback in an inclusive and active forum.</span></span> <span data-ttu-id="42cb5-107">Como desenvolvedor, você pode criar aplicativos [de guia,](../tabs/what-are-tabs.md#how-do-tabs-work) [bot](../bots/what-are-bots.md)e extensão de [mensagem](../messaging-extensions/what-are-messaging-extensions.md) configuráveis para aprimorar e enriquecer uma experiência de reunião do Teams.</span><span class="sxs-lookup"><span data-stu-id="42cb5-107">As a developer, you can create [configurable tab](../tabs/what-are-tabs.md#how-do-tabs-work), [bot](../bots/what-are-bots.md), and [message extension](../messaging-extensions/what-are-messaging-extensions.md) applications to enhance and enrich a Teams meeting experience.</span></span> <span data-ttu-id="42cb5-108">Os usuários da reunião podem acessar aplicativos, por meio da galeria de guias, para habilitar cenários relevantes, como pré-preparação de um quadro Kanban, iniciar uma caixa de diálogo ativas na reunião ou criar uma sondagem pós-reunião.</span><span class="sxs-lookup"><span data-stu-id="42cb5-108">Meeting users can access apps, via the tab gallery, to enable relevant scenarios such as pre-staging a Kanban board, launching an in-meeting actionable dialog, or creating a post-meeting poll.</span></span> <span data-ttu-id="42cb5-109">Seu aplicativo de reunião pode oferecer uma experiência do usuário para cada estágio do ciclo de vida da reunião com base no status do participante.</span><span class="sxs-lookup"><span data-stu-id="42cb5-109">Your meeting app can deliver a user experience for each stage of the meeting lifecycle based upon attendee status.</span></span>

<span data-ttu-id="42cb5-110">Centros de extensibilidade do aplicativo de reunião do Teams em três conceitos:</span><span class="sxs-lookup"><span data-stu-id="42cb5-110">Teams’ meeting app extensibility centers on three concepts:</span></span>

<span data-ttu-id="42cb5-111">✔ ciclo **de** vida da reunião — antes, durante e após o período de tempo de reunião.</span><span class="sxs-lookup"><span data-stu-id="42cb5-111">✔ **Meeting lifecycle** — before, during, and after meeting time frame.</span></span>  
<span data-ttu-id="42cb5-112">✔ Função **participante** — organizador da reunião, apresentador ou participante.</span><span class="sxs-lookup"><span data-stu-id="42cb5-112">✔ **Participant role** — meeting organizer, presenter, or attendee.</span></span>  
<span data-ttu-id="42cb5-113">✔ Tipo **de usuário** — no locatário, convidado, federado ou usuário anônimo do Teams.</span><span class="sxs-lookup"><span data-stu-id="42cb5-113">✔ **User type** — in-tenant, guest, federated, or anonymous Teams user.</span></span>

<!-- markdownlint-disable MD001 -->
### <a name="meeting-lifecycle-scenarios"></a><span data-ttu-id="42cb5-114">Cenários de ciclo de vida de reunião</span><span class="sxs-lookup"><span data-stu-id="42cb5-114">Meeting lifecycle scenarios</span></span>

## <a name="tabs"></a><span data-ttu-id="42cb5-115">Guias</span><span class="sxs-lookup"><span data-stu-id="42cb5-115">Tabs</span></span>

> [!IMPORTANT]
> <span data-ttu-id="42cb5-116">Assim como em todos os aplicativos de tabulação, seu aplicativo precisará seguir o fluxo de autenticação [SSO](../tabs/how-to/authentication/auth-aad-sso.md) do Teams para guias.</span><span class="sxs-lookup"><span data-stu-id="42cb5-116">As with all tab applications, Your app will need to follow the Teams [SSO authentication flow](../tabs/how-to/authentication/auth-aad-sso.md) for tabs.</span></span>

> [!NOTE]
> * <span data-ttu-id="42cb5-117">Os clientes móveis suportam guias somente em superfícies de pré-reunião e pós-reunião.</span><span class="sxs-lookup"><span data-stu-id="42cb5-117">Mobile clients support tabs only in pre-meeting and post-meeting surfaces.</span></span> <span data-ttu-id="42cb5-118">As experiências na reunião, como a caixa de diálogo na reunião e o painel no celular estarão disponíveis em breve.</span><span class="sxs-lookup"><span data-stu-id="42cb5-118">The in-meeting experiences, such as in-meeting dialog and panel on mobile will be available soon.</span></span>
> * <span data-ttu-id="42cb5-119">Os aplicativos têm suporte apenas em reuniões agendadas privadas.</span><span class="sxs-lookup"><span data-stu-id="42cb5-119">Apps are supported only in private scheduled meetings.</span></span>

### <a name="pre-meeting-app-experience"></a><span data-ttu-id="42cb5-120">Experiência do aplicativo de pré-reunião</span><span class="sxs-lookup"><span data-stu-id="42cb5-120">Pre-meeting app experience</span></span>

<span data-ttu-id="42cb5-121">**Experiência de pré-reunião:**</span><span class="sxs-lookup"><span data-stu-id="42cb5-121">**Pre-meeting experience:**</span></span>

![experiência de pré-reunião](../assets/images/apps-in-meetings/PreMeeting.png)

<span data-ttu-id="42cb5-123">**Guia Pré-reunião:**</span><span class="sxs-lookup"><span data-stu-id="42cb5-123">**Pre-meeting tab:**</span></span>

![exibição de guia de pré-reunião](../assets/images/apps-in-meetings/PreMeetingTab.png)

<span data-ttu-id="42cb5-125">✔ usuários com permissão podem adicionar aplicativos a uma reunião por meio da galeria de guias de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="42cb5-125">✔ Permissioned users can add apps to a meeting via the tab gallery in two ways:</span></span>

<span data-ttu-id="42cb5-126">&emsp;&emsp;&#9679; por meio da guia **Detalhes** no formulário de agendamento do Teams.</span><span class="sxs-lookup"><span data-stu-id="42cb5-126">&emsp;&emsp;&#9679; Via the **Details** tab on the Teams scheduling form.</span></span>

<span data-ttu-id="42cb5-127">&emsp;&emsp;&#9679; por meio da guia **Chat de** reunião em uma reunião existente.</span><span class="sxs-lookup"><span data-stu-id="42cb5-127">&emsp;&emsp;&#9679;  Via the meeting **Chat** tab in an existing meeting.</span></span></br> </br>

<span data-ttu-id="42cb5-128">✔ aplicativos tab são acessíveis em reuniões **Páginas detalhes** e **chats** usando um botão de ícone de a mais (➕) .|</span><span class="sxs-lookup"><span data-stu-id="42cb5-128">✔ Tab apps are accessible in meetings **Details** and **Chats** pages using a plus icon (➕) button.|</span></span>

<span data-ttu-id="42cb5-129">✔ layout da guia deve estar em um estado organizado se houver mais de dez pesquisas ou pesquisas.</span><span class="sxs-lookup"><span data-stu-id="42cb5-129">✔  Tab layout should be in an organized state if there are more than ten polls or surveys.</span></span>

### <a name="in-meeting-app-experience"></a><span data-ttu-id="42cb5-130">Experiência do aplicativo na reunião</span><span class="sxs-lookup"><span data-stu-id="42cb5-130">In-meeting app experience</span></span>

<span data-ttu-id="42cb5-131">✔ aplicativos de reunião serão hospedados na barra superior superior da janela de chat e como experiência de guia na reunião por meio da guia na reunião. Quando os usuários adicionam uma guia a uma reunião por meio da galeria de guias, os aplicativos que estão **durante** as experiências de reunião serão ativos.</span><span class="sxs-lookup"><span data-stu-id="42cb5-131">✔ Meeting apps will be hosted in the top upper bar of the chat window and as in-meeting tab experience via the in-meeting tab. When users add a tab to a meeting through the tab gallery, apps that are **during meeting** experiences will be surfaced.</span></span>

<span data-ttu-id="42cb5-132">✔ usuários com permissão podem adicionar aplicativos durante a reunião.</span><span class="sxs-lookup"><span data-stu-id="42cb5-132">✔ Permissioned users can add apps while in the meeting.</span></span>

<span data-ttu-id="42cb5-133">✔ Quando carregado no contexto de uma reunião, os aplicativos poderão aproveitar o SDK do Cliente do Teams para acessar o , e renderizar adequadamente `meetingId` `userMri` a `frameContext` experiência.</span><span class="sxs-lookup"><span data-stu-id="42cb5-133">✔ When loaded in the context of a meeting, apps will be able to leverage the Teams Client SDK to access the `meetingId`, `userMri`, and `frameContext` to appropriately render the experience.</span></span>

<span data-ttu-id="42cb5-134">✔ Exportar um resultado de uma pesquisa ou sondagens deve notificar os usuários informando, "resultados baixados com êxito".</span><span class="sxs-lookup"><span data-stu-id="42cb5-134">✔ Exporting a result of a survey or polls should notify the users stating, ‘results successfully downloaded’.</span></span>

<span data-ttu-id="42cb5-135">✔ para que um aplicativo seja visível em uma reunião do Teams em duas áreas:</span><span class="sxs-lookup"><span data-stu-id="42cb5-135">✔ For an app to be visible in a Teams meeting in two areas:</span></span>

<span data-ttu-id="42cb5-136">&emsp;&emsp;&#9679; Painel **lateral**.</span><span class="sxs-lookup"><span data-stu-id="42cb5-136">&emsp;&emsp;&#9679; **Side panel**.</span></span> </br>

> [!NOTE]
> <span data-ttu-id="42cb5-137">Se o _manifesto do aplicativo_ especificar que sua guia é otimizada para o painel [lateral,](create-apps-for-teams-meetings.md#during-a-meeting)é onde ela será exibida.</span><span class="sxs-lookup"><span data-stu-id="42cb5-137">If your _app manifest_ specifies that your tab is [optimized for side panel](create-apps-for-teams-meetings.md#during-a-meeting), that is where it will be displayed.</span></span> <span data-ttu-id="42cb5-138">Ele também pode fazer parte de uma experiência de bandeja de compartilhamento, sujeito a diretrizes de design especificadas.</span><span class="sxs-lookup"><span data-stu-id="42cb5-138">It can also be part of a share-tray experience, subject to specified design guidelines.</span></span>

<span data-ttu-id="42cb5-139">&emsp;&emsp;&#9679; caixa **de diálogo na reunião**.</span><span class="sxs-lookup"><span data-stu-id="42cb5-139">&emsp;&emsp;&#9679; **In-meeting dialog**.</span></span> <span data-ttu-id="42cb5-140">Use a caixa de diálogo na reunião para mostrar conteúdo a actionable para os participantes da reunião.</span><span class="sxs-lookup"><span data-stu-id="42cb5-140">Use the in-meeting dialog to showcase actionable content for meeting participants.</span></span> <span data-ttu-id="42cb5-141">*Consulte* [Criar aplicativos para reuniões do Teams.](create-apps-for-teams-meetings.md)</span><span class="sxs-lookup"><span data-stu-id="42cb5-141">*See* [Create Apps for Teams meetings](create-apps-for-teams-meetings.md).</span></span>

<span data-ttu-id="42cb5-142">**Experiência na reunião:**</span><span class="sxs-lookup"><span data-stu-id="42cb5-142">**In-meeting experience:**</span></span>

![experiência na reunião](../assets/images/apps-in-meetings/in-meeting-experience.png)

![Exibição de diálogo na reunião](../assets/images/apps-in-meetings/in-meeting-dialog.png)

<span data-ttu-id="42cb5-145">**Caixa de diálogo a actionable na reunião para usuários:**</span><span class="sxs-lookup"><span data-stu-id="42cb5-145">**In-meeting actionable dialog for users:**</span></span>

![exibição de caixa de diálogo](../assets/images/apps-in-meetings/in-meeting-dialog-view.png)

### <a name="post-meeting-app-experience"></a><span data-ttu-id="42cb5-147">Experiência de aplicativo pós-reunião</span><span class="sxs-lookup"><span data-stu-id="42cb5-147">Post-meeting app experience</span></span>

<span data-ttu-id="42cb5-148">**Experiência pós-reunião:**</span><span class="sxs-lookup"><span data-stu-id="42cb5-148">**Post-meeting experience:**</span></span>

![pós-exibição de reunião](../assets/images/apps-in-meetings/PostMeeting.png)

<span data-ttu-id="42cb5-150">✔ O cenário do aplicativo pós-reunião é semelhante à experiência atual pós-reunião com o benefício adicionado de ter guias que existem dentro da superfície.</span><span class="sxs-lookup"><span data-stu-id="42cb5-150">✔ The post-meeting app scenario is similar to the current post-meeting experience with the added benefit of having tabs that exist within the surface.</span></span> 

<span data-ttu-id="42cb5-151">✔ usuários com permissão podem adicionar aplicativos da galeria  de guias a uma reunião por meio da guia Detalhes no formulário de agendamento do Teams e na guia **Chat** de reunião em uma reunião existente.</span><span class="sxs-lookup"><span data-stu-id="42cb5-151">✔ Permissioned users can add apps from the tab gallery to a meeting via the **Details** tab on the Teams scheduling form and the meeting **Chat** tab in an existing meeting.</span></span>

<span data-ttu-id="42cb5-152">✔ layout da guia deve estar em um estado organizado se houver mais de dez pesquisas ou pesquisas.</span><span class="sxs-lookup"><span data-stu-id="42cb5-152">✔  Tab layout should be in an organized state if there are more than ten polls or surveys.</span></span>

### <a name="bots"></a><span data-ttu-id="42cb5-153">Bots</span><span class="sxs-lookup"><span data-stu-id="42cb5-153">Bots</span></span>

<span data-ttu-id="42cb5-154">Para implementação de bot, comece com [a complicação de um bot](../build-your-first-app/build-bot.md) e continue com a criação de [aplicativos para reuniões do Teams.](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-reference)</span><span class="sxs-lookup"><span data-stu-id="42cb5-154">For bot implementation, start with [build a bot](../build-your-first-app/build-bot.md) and then continue with [create apps for Teams meetings](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-reference).</span></span>

### <a name="messaging-extensions"></a><span data-ttu-id="42cb5-155">Extensões de mensagens</span><span class="sxs-lookup"><span data-stu-id="42cb5-155">Messaging extensions</span></span>

<span data-ttu-id="42cb5-156">Para implementação de extensão de mensagens, comece com [a criação](../messaging-extensions/how-to/create-messaging-extension.md) de uma extensão de mensagens e continue com a criação de [aplicativos para reuniões do Teams.](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-reference)</span><span class="sxs-lookup"><span data-stu-id="42cb5-156">For messaging extension implementation, start with [build a messaging extension](../messaging-extensions/how-to/create-messaging-extension.md) and then continue with [create apps for Teams meetings](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-reference).</span></span>

## <a name="participant-roles-and-user-types-in-a-meeting"></a><span data-ttu-id="42cb5-157">Funções de participante e tipos de usuário em uma reunião</span><span class="sxs-lookup"><span data-stu-id="42cb5-157">Participant roles and user types in a meeting</span></span>

![Participantes de uma reunião](../assets/images/apps-in-meetings/participant-roles.png)

### <a name="participant-roles"></a><span data-ttu-id="42cb5-159">Funções de participante</span><span class="sxs-lookup"><span data-stu-id="42cb5-159">Participant roles</span></span>

<span data-ttu-id="42cb5-160">Você pode projetar seu aplicativo com autorização específica do participante.</span><span class="sxs-lookup"><span data-stu-id="42cb5-160">You can design your app with participant-specific authorization.</span></span> <span data-ttu-id="42cb5-161">Por exemplo, talvez apenas um organizador e/ou apresentador possam criar uma sondagem em reuniões.</span><span class="sxs-lookup"><span data-stu-id="42cb5-161">For example, perhaps only an organizer and/or presenter can create a poll in meetings.</span></span> <span data-ttu-id="42cb5-162">Embora as configurações de participantes padrão sejam determinadas pelo administrador de IT de uma organização, um organizador da reunião pode querer alterar as configurações de uma reunião específica.</span><span class="sxs-lookup"><span data-stu-id="42cb5-162">Although default participant settings are determined by an organization's IT administrator, a meeting organizer may want to change the settings for a specific meeting.</span></span> <span data-ttu-id="42cb5-163">Os organizadores podem fazer essas alterações na página da Web opções de reunião.</span><span class="sxs-lookup"><span data-stu-id="42cb5-163">Organizers can make these changes on the Meeting options web page.</span></span>

1. <span data-ttu-id="42cb5-164">**Organizador**.</span><span class="sxs-lookup"><span data-stu-id="42cb5-164">**Organizer**.</span></span> <span data-ttu-id="42cb5-165">O organizador agenda uma reunião, define as opções de reunião, atribui funções de reunião e inicia a reunião.</span><span class="sxs-lookup"><span data-stu-id="42cb5-165">The organizer schedules a meeting, sets the meeting options, assigns meeting roles, and starts the meeting.</span></span> <span data-ttu-id="42cb5-166">Somente usuários com uma conta M365 (que possuem uma licença do Teams) podem ser organizadores e controlar as permissões do participante.</span><span class="sxs-lookup"><span data-stu-id="42cb5-166">Only users with a M365 account (possessing a Teams license) can be organizers and control attendee permissions.</span></span>
1. <span data-ttu-id="42cb5-167">**Apresentador**.</span><span class="sxs-lookup"><span data-stu-id="42cb5-167">**Presenter**.</span></span> <span data-ttu-id="42cb5-168">Os apresentadores têm quase os mesmos recursos que o organizador; no entanto, um apresentador não pode remover um organizador da sessão ou modificar opções de reunião para a sessão.</span><span class="sxs-lookup"><span data-stu-id="42cb5-168">Presenters have nearly the same capabilities as organizer; however, a presenter cannot remove an organizer from the session or modify meeting options for the session.</span></span> <span data-ttu-id="42cb5-169">Por padrão, os participantes que participam de uma reunião têm a função de apresentador.</span><span class="sxs-lookup"><span data-stu-id="42cb5-169">By default, participants joining a meeting have the presenter role.</span></span>
1. <span data-ttu-id="42cb5-170">**Participante**.</span><span class="sxs-lookup"><span data-stu-id="42cb5-170">**Attendee**.</span></span> <span data-ttu-id="42cb5-171">Um participante é um usuário que foi convidado a participar de uma reunião, mas que não está autorizado a atuar como apresentador.</span><span class="sxs-lookup"><span data-stu-id="42cb5-171">An attendee is a user who has been invited to attend a meeting but who is not authorized to act as a presenter.</span></span> <span data-ttu-id="42cb5-172">Os participantes podem interagir com outros membros da reunião, mas não podem gerenciar nenhuma das configurações de reunião ou compartilhar conteúdo.</span><span class="sxs-lookup"><span data-stu-id="42cb5-172">Attendees can interact with other meeting members but cannot manage any of the meeting settings or share content.</span></span>

<span data-ttu-id="42cb5-173">_Consulte_ [ **Funções em uma reunião do Teams**](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)</span><span class="sxs-lookup"><span data-stu-id="42cb5-173">_See_ [**Roles in a Teams meeting**](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)</span></span>

<span data-ttu-id="42cb5-174">Você pode acessar a página  **Opções de reunião** da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="42cb5-174">You can access the  **Meeting options** page as follows:</span></span>

<span data-ttu-id="42cb5-175">&#11200; No Teams, vá  para o logotipo do ![ ](../assets/images/apps-in-meetings/calendar-logo.png) calendário, selecione uma reunião e opções **de reunião.**</span><span class="sxs-lookup"><span data-stu-id="42cb5-175">&#11200; In Teams, go to **Calendar** ![calendar logo](../assets/images/apps-in-meetings/calendar-logo.png), select a meeting, and then **Meeting options**.</span></span>

<span data-ttu-id="42cb5-176">&#11200; Em um convite de reunião, selecione **Opções de reunião**.</span><span class="sxs-lookup"><span data-stu-id="42cb5-176">&#11200; In a meeting invitation, select **Meeting options**.</span></span>

<span data-ttu-id="42cb5-177">&#11200; Durante uma reunião, selecione **Mostrar que os** participantes mostram o ícone dos participantes nos ![ ](../assets/images/apps-in-meetings/show-participants.png) controles de reunião.</span><span class="sxs-lookup"><span data-stu-id="42cb5-177">&#11200; During a meeting, select **Show participants** ![show participants icon](../assets/images/apps-in-meetings/show-participants.png) in the meeting controls.</span></span> <span data-ttu-id="42cb5-178">Em seguida, acima da lista de participantes, escolha **Gerenciar permissões**.</span><span class="sxs-lookup"><span data-stu-id="42cb5-178">Then, above the list of participants, choose **Manage permissions**.</span></span>

### <a name="user-types"></a><span data-ttu-id="42cb5-179">Tipos de usuários</span><span class="sxs-lookup"><span data-stu-id="42cb5-179">User types</span></span>

> [!NOTE]
> <span data-ttu-id="42cb5-180">Os tipos de usuário podem ingressar em reuniões e assumir uma das funções de participante descritas acima.</span><span class="sxs-lookup"><span data-stu-id="42cb5-180">User types can join meetings and assume one of the participant roles described above.</span></span> <span data-ttu-id="42cb5-181">O tipo de usuário não é exposto como parte da API **getParticipantRole.**</span><span class="sxs-lookup"><span data-stu-id="42cb5-181">The User type is not exposed as part of the **getParticipantRole** API.</span></span>

1. <span data-ttu-id="42cb5-182">**In-tenant**.</span><span class="sxs-lookup"><span data-stu-id="42cb5-182">**In-tenant**.</span></span> <span data-ttu-id="42cb5-183">Esses usuários pertencem à organização e têm credenciais no Azure Active Directory para o locatário.</span><span class="sxs-lookup"><span data-stu-id="42cb5-183">These users belong to the organization and have credentials in Azure Active Directory for the tenant.</span></span> <span data-ttu-id="42cb5-184">Eles geralmente são funcionários em tempo integral, no local ou remotos.</span><span class="sxs-lookup"><span data-stu-id="42cb5-184">They are usually full-time, onsite or remote employees.</span></span>
1. <span data-ttu-id="42cb5-185">**Convidado**.</span><span class="sxs-lookup"><span data-stu-id="42cb5-185">**Guest**.</span></span> <span data-ttu-id="42cb5-186">Um convidado é um participante de outra organização que foi convidado a acessar o Teams ou outros recursos no locatário da sua organização.</span><span class="sxs-lookup"><span data-stu-id="42cb5-186">A guest is a participant from another organization who has been invited to access Teams or other resources in your organization's tenant.</span></span> <span data-ttu-id="42cb5-187">Os convidados são adicionados ao Active Directory da sua organização e podem receber quase todos os mesmos recursos do Teams como um membro nativo da equipe com acesso total a chats, reuniões e arquivos de equipe.</span><span class="sxs-lookup"><span data-stu-id="42cb5-187">Guests are added to your organization’s Active Directory and can be given nearly all the same Teams capabilities as a native team member with full access to team chats, meetings, and files.</span></span> <span data-ttu-id="42cb5-188">_Consulte_ [Acesso de convidados no Microsoft Teams](/microsoftteams/guest-access)</span><span class="sxs-lookup"><span data-stu-id="42cb5-188">_See_ [Guest access in Microsoft Teams](/microsoftteams/guest-access)</span></span>
1. <span data-ttu-id="42cb5-189">**Federado/Externo**.</span><span class="sxs-lookup"><span data-stu-id="42cb5-189">**Federated/External**.</span></span> <span data-ttu-id="42cb5-190">Um usuário federado é um usuário externo do Teams em outra organização que foi convidado a participar de uma reunião.</span><span class="sxs-lookup"><span data-stu-id="42cb5-190">A federated user is an external Teams user in another organization who has been invited to join a meeting.</span></span> <span data-ttu-id="42cb5-191">Como esses usuários têm credenciais válidas com parceiros federados, eles são tratados como autenticados pelo Teams, mas não têm acesso às suas equipes ou a outros recursos compartilhados de sua organização.</span><span class="sxs-lookup"><span data-stu-id="42cb5-191">Since these users have valid credentials with federated partners, they are treated as authenticated by Teams but do not have access to your teams or other shared resources from your organization.</span></span> <span data-ttu-id="42cb5-192">Se você quiser que os usuários externos tenham acesso a equipes e canais, o acesso de convidados pode ser uma opção melhor.</span><span class="sxs-lookup"><span data-stu-id="42cb5-192">If you want external users to have access to teams and channels, guest access might be a better option.</span></span> <span data-ttu-id="42cb5-193">_Consulte_ [Gerenciar acesso externo no Microsoft Teams](/microsoftteams/manage-external-access)</span><span class="sxs-lookup"><span data-stu-id="42cb5-193">_See_ [Manage external access in Microsoft Teams](/microsoftteams/manage-external-access)</span></span>
1. <span data-ttu-id="42cb5-194">**Anônimo**.</span><span class="sxs-lookup"><span data-stu-id="42cb5-194">**Anonymous**.</span></span> <span data-ttu-id="42cb5-195">Os usuários anônimos não têm uma identidade do Active Directory e não são federados com um locatário.</span><span class="sxs-lookup"><span data-stu-id="42cb5-195">Anonymous users do not have an Active Directory identity and are not federated with a tenant.</span></span> <span data-ttu-id="42cb5-196">O participante anônimo é como um usuário externo, mas sua identidade não é projetada para a reunião.</span><span class="sxs-lookup"><span data-stu-id="42cb5-196">The anonymous participant is like an external user, but their identity is not projected into the meeting.</span></span> <span data-ttu-id="42cb5-197">Os usuários anônimos não poderão acessar aplicativos em uma janela de reunião.</span><span class="sxs-lookup"><span data-stu-id="42cb5-197">Anonymous users will not be able to access apps in a meeting window.</span></span>

## <a name="next-steps"></a><span data-ttu-id="42cb5-198">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="42cb5-198">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="42cb5-199">Criar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="42cb5-199">Design your app</span></span>](../apps-in-teams-meetings/design/designing-apps-in-meetings.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="42cb5-200">Criar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="42cb5-200">Build your app</span></span>](create-apps-for-teams-meetings.md)
