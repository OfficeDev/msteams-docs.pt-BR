---
title: Aplicativos em reuniões do Teams
author: laujan
description: visão geral dos aplicativos em reuniões do Teams com base na função de participante e usuário
ms.topic: overview
ms.author: lajanuar
keywords: teams apps meetings user participant role api
ms.openlocfilehash: 217737cbbf73104d4d78cf817e6df0244229c53c
ms.sourcegitcommit: 4539479289b43812eaae07a1c0f878bed815d2d2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/12/2021
ms.locfileid: "49797754"
---
# <a name="apps-in-teams-meetings"></a><span data-ttu-id="630cd-104">Aplicativos em reuniões do Teams</span><span class="sxs-lookup"><span data-stu-id="630cd-104">Apps in Teams meetings</span></span>

<span data-ttu-id="630cd-105">As reuniões são fundamentais para a produtividade no Teams.</span><span class="sxs-lookup"><span data-stu-id="630cd-105">Meetings are key to productivity in Teams.</span></span> <span data-ttu-id="630cd-106">Eles permitem colaboração, parceria, comunicação informada e comentários compartilhados em um fórum inclusivo e ativo.</span><span class="sxs-lookup"><span data-stu-id="630cd-106">They enable collaboration, partnership, informed communication, and shared feedback in an inclusive and active forum.</span></span> <span data-ttu-id="630cd-107">Como desenvolvedor, você pode criar [aplicativos](../tabs/what-are-tabs.md#how-do-tabs-work) [](../messaging-extensions/what-are-messaging-extensions.md) de guia configurável, [bot](../bots/what-are-bots.md)e extensão de mensagem para aprimorar e enriquecer uma experiência de reunião do Teams.</span><span class="sxs-lookup"><span data-stu-id="630cd-107">As a developer, you can create [configurable tab](../tabs/what-are-tabs.md#how-do-tabs-work), [bot](../bots/what-are-bots.md), and [message extension](../messaging-extensions/what-are-messaging-extensions.md) applications to enhance and enrich a Teams meeting experience.</span></span> <span data-ttu-id="630cd-108">Os usuários da reunião podem acessar aplicativos, por meio da galeria de guias, para habilitar cenários relevantes, como pré-preparação de um quadro kanban, lançamento de uma caixa de diálogo a actionable na reunião ou criação de uma votação pós-reunião.</span><span class="sxs-lookup"><span data-stu-id="630cd-108">Meeting users can access apps, via the tab gallery, to enable relevant scenarios such as pre-staging a Kanban board, launching an in-meeting actionable dialog, or creating a post-meeting poll.</span></span> <span data-ttu-id="630cd-109">Seu aplicativo de reunião pode oferecer uma experiência de usuário para cada estágio do ciclo de vida da reunião com base no status do participante.</span><span class="sxs-lookup"><span data-stu-id="630cd-109">Your meeting app can deliver a user experience for each stage of the meeting lifecycle based upon attendee status.</span></span>

<span data-ttu-id="630cd-110">A extensibilidade do aplicativo de reunião do Teams é voltada para três conceitos:</span><span class="sxs-lookup"><span data-stu-id="630cd-110">Teams’ meeting app extensibility centers on three concepts:</span></span>

<span data-ttu-id="630cd-111">✔ ciclo **de vida da** reunião — antes, durante e após o período da reunião.</span><span class="sxs-lookup"><span data-stu-id="630cd-111">✔ **Meeting lifecycle** — before, during, and after meeting time frame.</span></span>  
<span data-ttu-id="630cd-112">✔ **participante** — organizador da reunião, apresentador ou participante.</span><span class="sxs-lookup"><span data-stu-id="630cd-112">✔ **Participant role** — meeting organizer, presenter, or attendee.</span></span>  
<span data-ttu-id="630cd-113">✔ tipo **de usuário** — usuário do Teams no locatário, convidado, federado ou anônimo.</span><span class="sxs-lookup"><span data-stu-id="630cd-113">✔ **User type** — in-tenant, guest, federated, or anonymous Teams user.</span></span>

<!-- markdownlint-disable MD001 -->
### <a name="meeting-lifecycle-scenarios"></a><span data-ttu-id="630cd-114">Cenários de ciclo de vida de reunião</span><span class="sxs-lookup"><span data-stu-id="630cd-114">Meeting lifecycle scenarios</span></span>

## <a name="tabs"></a><span data-ttu-id="630cd-115">Guias</span><span class="sxs-lookup"><span data-stu-id="630cd-115">Tabs</span></span>

> [!IMPORTANT]
> <span data-ttu-id="630cd-116">Assim como em todos os aplicativos de guia, seu aplicativo precisará seguir o fluxo de autenticação [SSO](../tabs/how-to/authentication/auth-aad-sso.md) do Teams para guias.</span><span class="sxs-lookup"><span data-stu-id="630cd-116">As with all tab applications, Your app will need to follow the Teams [SSO authentication flow](../tabs/how-to/authentication/auth-aad-sso.md) for tabs.</span></span>

> [!NOTE]
> <span data-ttu-id="630cd-117">Os clientes móveis só suportam Guias em Superfícies de Pré e Pós-Reunião.</span><span class="sxs-lookup"><span data-stu-id="630cd-117">Mobile clients support Tabs only in Pre and Post Meeting Surfaces.</span></span> <span data-ttu-id="630cd-118">As experiências na reunião (caixa de diálogo e painel na reunião) em dispositivos móveis estarão disponíveis em breve</span><span class="sxs-lookup"><span data-stu-id="630cd-118">The In-meeting experiences (in-meeting dialog and panel) on mobile will be available soon</span></span>

### <a name="pre-meeting-app-experience"></a><span data-ttu-id="630cd-119">Experiência de aplicativo de pré-reunião</span><span class="sxs-lookup"><span data-stu-id="630cd-119">Pre-meeting app experience</span></span>

<span data-ttu-id="630cd-120">**Experiência de pré-reunião:**</span><span class="sxs-lookup"><span data-stu-id="630cd-120">**Pre-meeting experience:**</span></span>

![experiência de pré-reunião](../assets/images/apps-in-meetings/PreMeeting.png)

<span data-ttu-id="630cd-122">**Guia Pré-reunião:**</span><span class="sxs-lookup"><span data-stu-id="630cd-122">**Pre-meeting tab:**</span></span>

![visualização da guia pré-reunião](../assets/images/apps-in-meetings/PreMeetingTab.png)

<span data-ttu-id="630cd-124">✔ usuários com permissão podem adicionar aplicativos a uma reunião por meio da galeria de guias de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="630cd-124">✔ Permissioned users can add apps to a meeting via the tab gallery in two ways:</span></span>

<span data-ttu-id="630cd-125">&emsp;&emsp;&#9679; por meio da **guia Detalhes** do formulário de agendamento do Teams.</span><span class="sxs-lookup"><span data-stu-id="630cd-125">&emsp;&emsp;&#9679; Via the **Details** tab on the Teams scheduling form.</span></span>

<span data-ttu-id="630cd-126">&emsp;&emsp;&#9679; por meio da **guia Chat de** reunião em uma reunião existente.</span><span class="sxs-lookup"><span data-stu-id="630cd-126">&emsp;&emsp;&#9679;  Via the meeting **Chat** tab in an existing meeting.</span></span></br> </br>

<span data-ttu-id="630cd-127">✔ os aplicativos de guia  podem ser acessados em páginas de Detalhes e **Chats** de reuniões usando um botão de ícone de a ➕(|)</span><span class="sxs-lookup"><span data-stu-id="630cd-127">✔ Tab apps are accessible in meetings **Details** and **Chats** pages using a plus icon (➕) button.|</span></span>

<span data-ttu-id="630cd-128">✔ layout da guia deve estar em um estado organizado se houver mais de dez votações ou pesquisas.</span><span class="sxs-lookup"><span data-stu-id="630cd-128">✔  Tab layout should be in an organized state if there are more than ten polls or surveys.</span></span>

### <a name="in-meeting-app-experience"></a><span data-ttu-id="630cd-129">Experiência do aplicativo na reunião</span><span class="sxs-lookup"><span data-stu-id="630cd-129">In-meeting app experience</span></span>

<span data-ttu-id="630cd-130">✔ aplicativos de reunião serão hospedados na barra superior da janela de chat e como experiência de guia na reunião por meio da guia na reunião. Quando os usuários adicionam uma guia a uma reunião por meio da galeria de guias, os aplicativos que estão **durante as experiências** de reunião serão divulgados.</span><span class="sxs-lookup"><span data-stu-id="630cd-130">✔ Meeting apps will be hosted in the top upper bar of the chat window and as in-meeting tab experience via the in-meeting tab. When users add a tab to a meeting through the tab gallery, apps that are **during meeting** experiences will be surfaced.</span></span>

<span data-ttu-id="630cd-131">✔ usuários com permissão podem adicionar aplicativos durante a reunião.</span><span class="sxs-lookup"><span data-stu-id="630cd-131">✔ Permissioned users can add apps while in the meeting.</span></span>

<span data-ttu-id="630cd-132">✔ Quando carregados no contexto de uma reunião, os aplicativos poderão aproveitar o SDK do Cliente do Teams para acessar o , e renderizar adequadamente a `meetingId` `userMri` `frameContext` experiência.</span><span class="sxs-lookup"><span data-stu-id="630cd-132">✔ When loaded in the context of a meeting, apps will be able to leverage the Teams Client SDK to access the `meetingId`, `userMri`, and `frameContext` to appropriately render the experience.</span></span>

<span data-ttu-id="630cd-133">✔ exportar um resultado de uma pesquisa ou votações deve notificar os usuários informando, "resultados baixados com êxito".</span><span class="sxs-lookup"><span data-stu-id="630cd-133">✔ Exporting a result of a survey or polls should notify the users stating, ‘results successfully downloaded’.</span></span>

<span data-ttu-id="630cd-134">✔ um aplicativo ficar visível em uma reunião do Teams em duas áreas:</span><span class="sxs-lookup"><span data-stu-id="630cd-134">✔ For an app to be visible in a Teams meeting in two areas:</span></span>

<span data-ttu-id="630cd-135">&emsp;&emsp;&#9679; painel **lateral.**</span><span class="sxs-lookup"><span data-stu-id="630cd-135">&emsp;&emsp;&#9679; **Side panel**.</span></span> </br>

> [!NOTE]
> <span data-ttu-id="630cd-136">Se o _manifesto do_ aplicativo especifica que a guia é otimizada para o painel [lateral,](create-apps-for-teams-meetings.md#during-a-meeting)é onde ela será exibida.</span><span class="sxs-lookup"><span data-stu-id="630cd-136">If your _app manifest_ specifies that your tab is [optimized for side panel](create-apps-for-teams-meetings.md#during-a-meeting), that is where it will be displayed.</span></span> <span data-ttu-id="630cd-137">Ele também pode fazer parte de uma experiência de bandeja de compartilhamento, sujeito às diretrizes de design especificadas.</span><span class="sxs-lookup"><span data-stu-id="630cd-137">It can also be part of a share-tray experience, subject to specified design guidelines.</span></span>

<span data-ttu-id="630cd-138">&emsp;&emsp;&#9679; caixa **de diálogo na reunião.**</span><span class="sxs-lookup"><span data-stu-id="630cd-138">&emsp;&emsp;&#9679; **In-meeting dialog**.</span></span> <span data-ttu-id="630cd-139">Use a caixa de diálogo na reunião para demonstrar conteúdo a actionable para os participantes da reunião.</span><span class="sxs-lookup"><span data-stu-id="630cd-139">Use the in-meeting dialog to showcase actionable content for meeting participants.</span></span> <span data-ttu-id="630cd-140">*Confira* [Criar aplicativos para reuniões do Teams.](create-apps-for-teams-meetings.md)</span><span class="sxs-lookup"><span data-stu-id="630cd-140">*See* [Create Apps for Teams meetings](create-apps-for-teams-meetings.md).</span></span>

<span data-ttu-id="630cd-141">**Experiência na reunião:**</span><span class="sxs-lookup"><span data-stu-id="630cd-141">**In-meeting experience:**</span></span>

![experiência na reunião](../assets/images/apps-in-meetings/in-meeting-experience.png)

![Exibição de caixa de diálogo na reunião](../assets/images/apps-in-meetings/in-meeting-dialog.png)

<span data-ttu-id="630cd-144">**Caixa de diálogo a actionable na reunião para os usuários:**</span><span class="sxs-lookup"><span data-stu-id="630cd-144">**In-meeting actionable dialog for users:**</span></span>

![exibição de caixa de diálogo](../assets/images/apps-in-meetings/in-meeting-dialog-view.png)

### <a name="post-meeting-app-experience"></a><span data-ttu-id="630cd-146">Experiência de aplicativo pós-reunião</span><span class="sxs-lookup"><span data-stu-id="630cd-146">Post-meeting app experience</span></span>

<span data-ttu-id="630cd-147">**Experiência pós-reunião:**</span><span class="sxs-lookup"><span data-stu-id="630cd-147">**Post-meeting experience:**</span></span>

![post meeting view](../assets/images/apps-in-meetings/PostMeeting.png)

<span data-ttu-id="630cd-149">✔ O cenário de aplicativo pós-reunião é semelhante à experiência pós-reunião atual, com o benefício agregado de ter guias existentes na superfície.</span><span class="sxs-lookup"><span data-stu-id="630cd-149">✔ The post-meeting app scenario is similar to the current post-meeting experience with the added benefit of having tabs that exist within the surface.</span></span> 

<span data-ttu-id="630cd-150">✔ Os usuários com permissão podem adicionar aplicativos da  galeria de guias a uma reunião por meio da guia Detalhes no formulário de agendamento do Teams e na guia **Chat** de reunião em uma reunião existente.</span><span class="sxs-lookup"><span data-stu-id="630cd-150">✔ Permissioned users can add apps from the tab gallery to a meeting via the **Details** tab on the Teams scheduling form and the meeting **Chat** tab in an existing meeting.</span></span>

<span data-ttu-id="630cd-151">✔ layout da guia deve estar em um estado organizado se houver mais de dez votações ou pesquisas.</span><span class="sxs-lookup"><span data-stu-id="630cd-151">✔  Tab layout should be in an organized state if there are more than ten polls or surveys.</span></span>

### <a name="bots"></a><span data-ttu-id="630cd-152">Bots</span><span class="sxs-lookup"><span data-stu-id="630cd-152">Bots</span></span>

<span data-ttu-id="630cd-153">Para implementação de bot, confira nossos [Bots na documentação de reuniões do Teams.](../bots/how-to/create-a-bot-for-teams.md#bots-in-teams-meetings)</span><span class="sxs-lookup"><span data-stu-id="630cd-153">For bot implementation, please see our [Bots in Teams meetings](../bots/how-to/create-a-bot-for-teams.md#bots-in-teams-meetings) documentation.</span></span>

### <a name="messaging-extensions"></a><span data-ttu-id="630cd-154">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="630cd-154">Messaging Extensions</span></span>

<span data-ttu-id="630cd-155">Para a implementação da extensão de mensagens, confira nossas [extensões de mensagens na documentação de reuniões do Teams.](../messaging-extensions/how-to/create-messaging-extension.md#messaging-extensions-in-teams-meetings)</span><span class="sxs-lookup"><span data-stu-id="630cd-155">For messaging extension implementation, please see our [Messaging extensions in Teams meetings](../messaging-extensions/how-to/create-messaging-extension.md#messaging-extensions-in-teams-meetings) documentation.</span></span>

## <a name="participant-roles-and-user-types-in-a-meeting"></a><span data-ttu-id="630cd-156">Funções de participante e tipos de usuário em uma reunião</span><span class="sxs-lookup"><span data-stu-id="630cd-156">Participant roles and user types in a meeting</span></span>

![Participantes em uma reunião](../assets/images/apps-in-meetings/participant-roles.png)

### <a name="participant-roles"></a><span data-ttu-id="630cd-158">Funções de participante</span><span class="sxs-lookup"><span data-stu-id="630cd-158">Participant roles</span></span>

<span data-ttu-id="630cd-159">Você pode projetar seu aplicativo com autorização específica do participante.</span><span class="sxs-lookup"><span data-stu-id="630cd-159">You can design your app with participant-specific authorization.</span></span> <span data-ttu-id="630cd-160">Por exemplo, talvez apenas um organizador e/ou apresentador possam criar uma votação em reuniões.</span><span class="sxs-lookup"><span data-stu-id="630cd-160">For example, perhaps only an organizer and/or presenter can create a poll in meetings.</span></span> <span data-ttu-id="630cd-161">Embora as configurações de participantes padrão sejam determinadas pelo administrador de IT de uma organização, um organizador da reunião pode querer alterar as configurações de uma reunião específica.</span><span class="sxs-lookup"><span data-stu-id="630cd-161">Although default participant settings are determined by an organization's IT administrator, a meeting organizer may want to change the settings for a specific meeting.</span></span> <span data-ttu-id="630cd-162">Os organizadores podem fazer essas alterações na página da Web de opções de reunião.</span><span class="sxs-lookup"><span data-stu-id="630cd-162">Organizers can make these changes on the Meeting options web page.</span></span>

1. <span data-ttu-id="630cd-163">**Organizador**.</span><span class="sxs-lookup"><span data-stu-id="630cd-163">**Organizer**.</span></span> <span data-ttu-id="630cd-164">O organizador agenda uma reunião, define as opções de reunião, atribui funções de reunião e inicia a reunião.</span><span class="sxs-lookup"><span data-stu-id="630cd-164">The organizer schedules a meeting, sets the meeting options, assigns meeting roles, and starts the meeting.</span></span> <span data-ttu-id="630cd-165">Somente os usuários com uma conta do M365 (que possuem uma licença do Teams) podem ser organizadores e controlar as permissões dos participantes.</span><span class="sxs-lookup"><span data-stu-id="630cd-165">Only users with a M365 account (possessing a Teams license) can be organizers and control attendee permissions.</span></span>
1. <span data-ttu-id="630cd-166">**Apresentador.**</span><span class="sxs-lookup"><span data-stu-id="630cd-166">**Presenter**.</span></span> <span data-ttu-id="630cd-167">Os apresentadores têm quase os mesmos recursos que o organizador; no entanto, um apresentador não pode remover um organizador da sessão ou modificar as opções de reunião da sessão.</span><span class="sxs-lookup"><span data-stu-id="630cd-167">Presenters have nearly the same capabilities as organizer; however, a presenter cannot remove an organizer from the session or modify meeting options for the session.</span></span> <span data-ttu-id="630cd-168">Por padrão, os participantes que participam de uma reunião têm a função de apresentador.</span><span class="sxs-lookup"><span data-stu-id="630cd-168">By default, participants joining a meeting have the presenter role.</span></span>
1. <span data-ttu-id="630cd-169">**Attendee**.</span><span class="sxs-lookup"><span data-stu-id="630cd-169">**Attendee**.</span></span> <span data-ttu-id="630cd-170">Um participante é um usuário que foi convidado a participar de uma reunião, mas que não está autorizado a atuar como apresentador.</span><span class="sxs-lookup"><span data-stu-id="630cd-170">An attendee is a user who has been invited to attend a meeting but who is not authorized to act as a presenter.</span></span> <span data-ttu-id="630cd-171">Os participantes podem interagir com outros membros da reunião, mas não podem gerenciar as configurações da reunião ou compartilhar conteúdo.</span><span class="sxs-lookup"><span data-stu-id="630cd-171">Attendees can interact with other meeting members but cannot manage any of the meeting settings or share content.</span></span>

<span data-ttu-id="630cd-172">_Ver_ [ **Funções em uma reunião do Teams**](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)</span><span class="sxs-lookup"><span data-stu-id="630cd-172">_See_ [**Roles in a Teams meeting**](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)</span></span>

<span data-ttu-id="630cd-173">Você pode acessar a  **página de opções de** reunião da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="630cd-173">You can access the  **Meeting options** page as follows:</span></span>

<span data-ttu-id="630cd-174">&#11200; Teams, vá para **o** logotipo do ![ ](../assets/images/apps-in-meetings/calendar-logo.png) calendário, selecione uma reunião e, em seguida, opções **de reunião.**</span><span class="sxs-lookup"><span data-stu-id="630cd-174">&#11200; In Teams, go to **Calendar** ![calendar logo](../assets/images/apps-in-meetings/calendar-logo.png), select a meeting, and then **Meeting options**.</span></span>

<span data-ttu-id="630cd-175">&#11200; Em um convite de reunião, selecione opções **de reunião.**</span><span class="sxs-lookup"><span data-stu-id="630cd-175">&#11200; In a meeting invitation, select **Meeting options**.</span></span>

<span data-ttu-id="630cd-176">&#11200; Durante uma reunião, selecione **Mostrar** participantes que mostram o ![ ícone dos participantes nos ](../assets/images/apps-in-meetings/show-participants.png) controles da reunião.</span><span class="sxs-lookup"><span data-stu-id="630cd-176">&#11200; During a meeting, select **Show participants** ![show participants icon](../assets/images/apps-in-meetings/show-participants.png) in the meeting controls.</span></span> <span data-ttu-id="630cd-177">Em seguida, acima da lista de participantes, escolha **Gerenciar permissões.**</span><span class="sxs-lookup"><span data-stu-id="630cd-177">Then, above the list of participants, choose **Manage permissions**.</span></span>

### <a name="user-types"></a><span data-ttu-id="630cd-178">Tipos de usuários</span><span class="sxs-lookup"><span data-stu-id="630cd-178">User types</span></span>

> [!NOTE]
> <span data-ttu-id="630cd-179">Os tipos de usuário podem ingressar em reuniões e assumir uma das funções de participante descritas acima.</span><span class="sxs-lookup"><span data-stu-id="630cd-179">User types can join meetings and assume one of the participant roles described above.</span></span> <span data-ttu-id="630cd-180">O tipo de usuário não é exposto como parte da API **getParticipantRole.**</span><span class="sxs-lookup"><span data-stu-id="630cd-180">The User type is not exposed as part of the **getParticipantRole** API.</span></span>

1. <span data-ttu-id="630cd-181">**No locatário.**</span><span class="sxs-lookup"><span data-stu-id="630cd-181">**In-tenant**.</span></span> <span data-ttu-id="630cd-182">Esses usuários pertencem à organização e têm credenciais no Azure Active Directory para o locatário.</span><span class="sxs-lookup"><span data-stu-id="630cd-182">These users belong to the organization and have credentials in Azure Active Directory for the tenant.</span></span> <span data-ttu-id="630cd-183">Geralmente, eles são funcionários em tempo integral, no local ou remotos.</span><span class="sxs-lookup"><span data-stu-id="630cd-183">They are usually full-time, onsite or remote employees.</span></span>
1. <span data-ttu-id="630cd-184">**Convidado**.</span><span class="sxs-lookup"><span data-stu-id="630cd-184">**Guest**.</span></span> <span data-ttu-id="630cd-185">Um convidado é um participante de outra organização que foi convidado a acessar o Teams ou outros recursos no locatário da sua organização.</span><span class="sxs-lookup"><span data-stu-id="630cd-185">A guest is a participant from another organization who has been invited to access Teams or other resources in your organization's tenant.</span></span> <span data-ttu-id="630cd-186">Os convidados são adicionados ao Active Directory da sua organização e podem receber quase todos os mesmos recursos do Teams de um membro nativo da equipe com acesso total a chats, reuniões e arquivos da equipe.</span><span class="sxs-lookup"><span data-stu-id="630cd-186">Guests are added to your organization’s Active Directory and can be given nearly all the same Teams capabilities as a native team member with full access to team chats, meetings, and files.</span></span> <span data-ttu-id="630cd-187">_Ver_ [acesso de convidados no Microsoft Teams](/microsoftteams/guest-access)</span><span class="sxs-lookup"><span data-stu-id="630cd-187">_See_ [Guest access in Microsoft Teams](/microsoftteams/guest-access)</span></span>
1. <span data-ttu-id="630cd-188">**Federado/Externo**.</span><span class="sxs-lookup"><span data-stu-id="630cd-188">**Federated/External**.</span></span> <span data-ttu-id="630cd-189">Um usuário federado é um usuário externo do Teams em outra organização que foi convidado a ingressar em uma reunião.</span><span class="sxs-lookup"><span data-stu-id="630cd-189">A federated user is an external Teams user in another organization who has been invited to join a meeting.</span></span> <span data-ttu-id="630cd-190">Como esses usuários têm credenciais válidas com parceiros federados, eles são tratados como autenticados pelo Teams, mas não têm acesso às suas equipes ou outros recursos compartilhados da sua organização.</span><span class="sxs-lookup"><span data-stu-id="630cd-190">Since these users have valid credentials with federated partners, they are treated as authenticated by Teams but do not have access to your teams or other shared resources from your organization.</span></span> <span data-ttu-id="630cd-191">Se você quiser que usuários externos tenham acesso a equipes e canais, o acesso de convidados pode ser uma opção melhor.</span><span class="sxs-lookup"><span data-stu-id="630cd-191">If you want external users to have access to teams and channels, guest access might be a better option.</span></span> <span data-ttu-id="630cd-192">_Confira_ [Gerenciar o acesso externo no Microsoft Teams](/microsoftteams/manage-external-access)</span><span class="sxs-lookup"><span data-stu-id="630cd-192">_See_ [Manage external access in Microsoft Teams](/microsoftteams/manage-external-access)</span></span>
1. <span data-ttu-id="630cd-193">**Anônimo**.</span><span class="sxs-lookup"><span data-stu-id="630cd-193">**Anonymous**.</span></span> <span data-ttu-id="630cd-194">Os usuários anônimos não têm uma identidade do Active Directory e não são federados com um locatário.</span><span class="sxs-lookup"><span data-stu-id="630cd-194">Anonymous users do not have an Active Directory identity and are not federated with a tenant.</span></span> <span data-ttu-id="630cd-195">O participante anônimo é como um usuário externo, mas sua identidade não é projetada para a reunião.</span><span class="sxs-lookup"><span data-stu-id="630cd-195">The anonymous participant is like an external user, but their identity is not projected into the meeting.</span></span> <span data-ttu-id="630cd-196">Os usuários anônimos não poderão acessar aplicativos em uma janela de reunião.</span><span class="sxs-lookup"><span data-stu-id="630cd-196">Anonymous users will not be able to access apps in a meeting window.</span></span>

## <a name="next-steps"></a><span data-ttu-id="630cd-197">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="630cd-197">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="630cd-198">Criar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="630cd-198">Design your app</span></span>](create-apps-for-teams-meetings.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="630cd-199">Criar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="630cd-199">Build your app</span></span>](create-apps-for-teams-meetings.md)
