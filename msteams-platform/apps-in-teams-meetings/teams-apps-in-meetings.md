---
title: Reuniões de aplicativos para o Teams
author: laujan
description: Visão geral dos aplicativos nas reuniões do Microsoft Teams com base no participante e na função de usuário
ms.topic: overview
ms.author: lajanuar
keywords: API de função de participante do usuário de reuniões de aplicativos do teams
ms.openlocfilehash: e7f0f95566347c06a4ab422565c3f49665a5150e
ms.sourcegitcommit: e92408e751a8f51028908ab7e2415a8051a536c0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2020
ms.locfileid: "48326309"
---
# <a name="apps-in-teams-meetings-release-preview"></a><span data-ttu-id="950b7-104">Aplicativos em reuniões do Teams (versão prévia)</span><span class="sxs-lookup"><span data-stu-id="950b7-104">Apps in Teams meetings (Release Preview)</span></span>

>[!IMPORTANT]
> <span data-ttu-id="950b7-105">Os recursos realçados no Microsoft Teams Release Preview são fornecidos apenas para fins de percepção prévia e feedback.</span><span class="sxs-lookup"><span data-stu-id="950b7-105">Features highlighted in Microsoft Teams Release Preview are provided for early insight and feedback purposes only.</span></span> <span data-ttu-id="950b7-106">Eles podem sofrer alterações antes de poderem ser habilitados.</span><span class="sxs-lookup"><span data-stu-id="950b7-106">They may undergo changes before they can be enabled.</span></span>

<span data-ttu-id="950b7-107">As reuniões são fundamentais para a produtividade no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="950b7-107">Meetings are key to productivity in Teams.</span></span> <span data-ttu-id="950b7-108">Eles permitem colaboração, parceria, comunicação informada e comentários compartilhados em um fórum inclusivo e ativo.</span><span class="sxs-lookup"><span data-stu-id="950b7-108">They enable collaboration, partnership, informed communication, and shared feedback in an inclusive and active forum.</span></span> <span data-ttu-id="950b7-109">Como desenvolvedor, você pode criar uma [guia configurável](../tabs/what-are-tabs.md#how-do-tabs-work), [bot](../bots/what-are-bots.md)e aplicativos de [extensão de mensagem](../messaging-extensions/what-are-messaging-extensions.md) para aprimorar e enriquecer uma experiência de reunião do teams.</span><span class="sxs-lookup"><span data-stu-id="950b7-109">As a developer, you can create [configurable tab](../tabs/what-are-tabs.md#how-do-tabs-work), [bot](../bots/what-are-bots.md), and [message extension](../messaging-extensions/what-are-messaging-extensions.md) applications to enhance and enrich a Teams meeting experience.</span></span> <span data-ttu-id="950b7-110">Os usuários da reunião podem acessar os aplicativos, por meio da Galeria de guias, para habilitar os cenários relevantes, como preparar um quadro Kanban, iniciar uma caixa de diálogo acionável em reunião ou criar uma votação de reunião.</span><span class="sxs-lookup"><span data-stu-id="950b7-110">Meeting users can access apps, via the tab gallery, to enable relevant scenarios such as pre-staging a Kanban board, launching an in-meeting actionable dialog, or creating a post-meeting poll.</span></span> <span data-ttu-id="950b7-111">O aplicativo de reunião pode fornecer uma experiência do usuário para cada estágio do ciclo de vida da reunião com base no status do participante.</span><span class="sxs-lookup"><span data-stu-id="950b7-111">Your meeting app can deliver a user experience for each stage of the meeting lifecycle based upon attendee status.</span></span>

<span data-ttu-id="950b7-112">Centros de extensibilidade de aplicativos da reunião da equipe em três conceitos:</span><span class="sxs-lookup"><span data-stu-id="950b7-112">Teams’ meeting app extensibility centers on three concepts:</span></span>

<span data-ttu-id="950b7-113">✔ **Ciclo de vida da reunião** — antes, durante e após o período de reunião.</span><span class="sxs-lookup"><span data-stu-id="950b7-113">✔ **Meeting lifecycle** — before, during, and after meeting time frame.</span></span>  
<span data-ttu-id="950b7-114">✔ **Função participante** — organizador da reunião, apresentador ou participante.</span><span class="sxs-lookup"><span data-stu-id="950b7-114">✔ **Participant role** — meeting organizer, presenter, or attendee.</span></span>  
<span data-ttu-id="950b7-115">✔ **Tipo de usuário** , usuário no locatário, convidado, federado ou equipes anônimas.</span><span class="sxs-lookup"><span data-stu-id="950b7-115">✔ **User type** — in-tenant, guest, federated, or anonymous Teams user.</span></span>

<!-- markdownlint-disable MD001 -->
### <a name="meeting-lifecycle-scenarios"></a><span data-ttu-id="950b7-116">Cenários de ciclo de vida da reunião</span><span class="sxs-lookup"><span data-stu-id="950b7-116">Meeting lifecycle scenarios</span></span>

## <a name="tabs"></a><span data-ttu-id="950b7-117">Guias</span><span class="sxs-lookup"><span data-stu-id="950b7-117">Tabs</span></span>

> [!IMPORTANT]
> <span data-ttu-id="950b7-118">Assim como ocorre com todos os aplicativos de guia, seu aplicativo precisará seguir o [fluxo de autenticação SSO](../tabs/how-to/authentication/auth-aad-sso.md) do teams para guias.</span><span class="sxs-lookup"><span data-stu-id="950b7-118">As with all tab applications, Your app will need to follow the Teams [SSO authentication flow](../tabs/how-to/authentication/auth-aad-sso.md) for tabs.</span></span>

### <a name="pre-meeting-app-experience"></a><span data-ttu-id="950b7-119">Experiência do aplicativo de pré-venda</span><span class="sxs-lookup"><span data-stu-id="950b7-119">Pre-meeting app experience</span></span>

<span data-ttu-id="950b7-120">**Experiência antes da reunião:**</span><span class="sxs-lookup"><span data-stu-id="950b7-120">**Pre-meeting experience:**</span></span>

![experiência de pré-venda](../assets/images/apps-in-meetings/PreMeeting.png)

<span data-ttu-id="950b7-122">**Guia antes da reunião:**</span><span class="sxs-lookup"><span data-stu-id="950b7-122">**Pre-meeting tab:**</span></span>

![exibição da guia pré-reunião](../assets/images/apps-in-meetings/PreMeetingTab.png)

<span data-ttu-id="950b7-124">✔ Usuários com permissão podem adicionar aplicativos a uma reunião por meio da Galeria de guias de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="950b7-124">✔ Permissioned users can add apps to a meeting via the tab gallery in two ways:</span></span>

<span data-ttu-id="950b7-125">&emsp;&emsp;&#9679; por meio da guia **detalhes** no formulário de agendamento do teams.</span><span class="sxs-lookup"><span data-stu-id="950b7-125">&emsp;&emsp;&#9679; Via the **Details** tab on the Teams scheduling form.</span></span>

<span data-ttu-id="950b7-126">&emsp;&emsp;&#9679; por meio da guia **chat** de reunião em uma reunião existente.</span><span class="sxs-lookup"><span data-stu-id="950b7-126">&emsp;&emsp;&#9679;  Via the meeting **Chat** tab in an existing meeting.</span></span></br> </br>

<span data-ttu-id="950b7-127">✔ Os aplicativos de guia podem ser acessados em páginas de **detalhes** de reuniões e **chats** usando um botão de adição (➕). |</span><span class="sxs-lookup"><span data-stu-id="950b7-127">✔ Tab apps are accessible in meetings **Details** and **Chats** pages using a plus icon (➕) button.|</span></span>

### <a name="in-meeting-app-experience"></a><span data-ttu-id="950b7-128">Experiência do aplicativo na reunião</span><span class="sxs-lookup"><span data-stu-id="950b7-128">In-meeting app experience</span></span>

<span data-ttu-id="950b7-129">✔ Os aplicativos de reunião serão hospedados na barra superior superior da janela de bate-papo e como experiência de guia na reunião através da guia na reunião. Quando os usuários adicionam uma guia a uma reunião através da Galeria de guias, os aplicativos que estão durante as experiências de **reunião** serão exibidos.</span><span class="sxs-lookup"><span data-stu-id="950b7-129">✔ Meeting apps will be hosted in the top upper bar of the chat window and as in-meeting tab experience via the in-meeting tab. When users add a tab to a meeting through the tab gallery, apps that are **during meeting** experiences will be surfaced.</span></span>

<span data-ttu-id="950b7-130">✔ Usuários com permissão podem adicionar aplicativos enquanto estiverem na reunião.</span><span class="sxs-lookup"><span data-stu-id="950b7-130">✔ Permissioned users can add apps while in the meeting.</span></span>

<span data-ttu-id="950b7-131">✔ Quando carregado no contexto de uma reunião, os aplicativos poderão aproveitar o SDK do cliente do teams para acessar o `meetingId` , `userMri` e `frameContext` para renderizar apropriadamente a experiência.</span><span class="sxs-lookup"><span data-stu-id="950b7-131">✔ When loaded in the context of a meeting, apps will be able to leverage the Teams Client SDK to access the `meetingId`, `userMri`, and `frameContext` to appropriately render the experience.</span></span>

<span data-ttu-id="950b7-132">✔ Para um aplicativo pode ser visível em uma reunião do teams em duas áreas:</span><span class="sxs-lookup"><span data-stu-id="950b7-132">✔ For an app can be visible in a Teams meeting in two areas:</span></span>

<span data-ttu-id="950b7-133">&emsp;&emsp;**Painel lateral**&#9679;.</span><span class="sxs-lookup"><span data-stu-id="950b7-133">&emsp;&emsp;&#9679; **Side panel**.</span></span> </br>

> [!NOTE]
> <span data-ttu-id="950b7-134">Se o _manifesto do aplicativo_ especificar que a guia será [otimizada para o painel lateral](create-apps-for-teams-meetings.md#in-meeting), isso será exibido.</span><span class="sxs-lookup"><span data-stu-id="950b7-134">If your _app manifest_ specifies that your tab is [optimized for side panel](create-apps-for-teams-meetings.md#in-meeting), that is where it will be displayed.</span></span> <span data-ttu-id="950b7-135">Também pode fazer parte de uma experiência de bandeja de compartilhamento, sujeita às diretrizes de design especificadas.</span><span class="sxs-lookup"><span data-stu-id="950b7-135">It can also be part of a share-tray experience, subject to specified design guidelines.</span></span>

<span data-ttu-id="950b7-136">&emsp;&emsp;&#9679; **caixa de diálogo de reunião**.</span><span class="sxs-lookup"><span data-stu-id="950b7-136">&emsp;&emsp;&#9679; **In-meeting dialog**.</span></span> <span data-ttu-id="950b7-137">Use a caixa de diálogo de reunião para exibir conteúdo acionável para os participantes da reunião.</span><span class="sxs-lookup"><span data-stu-id="950b7-137">Use the in-meeting dialog to showcase actionable content for meeting participants.</span></span> <span data-ttu-id="950b7-138">*Consulte* [criar aplicativos para reuniões do teams](create-apps-for-teams-meetings.md).</span><span class="sxs-lookup"><span data-stu-id="950b7-138">*See* [Create Apps for Teams meetings](create-apps-for-teams-meetings.md).</span></span>

<span data-ttu-id="950b7-139">**Experiência de reunião:**</span><span class="sxs-lookup"><span data-stu-id="950b7-139">**In-meeting experience:**</span></span>

![experiência na reunião](../assets/images/apps-in-meetings/in-meeting-experience.png)

![Visão da caixa de diálogo no Meeting](../assets/images/apps-in-meetings/in-meeting-dialog.png)

<span data-ttu-id="950b7-142">**Caixa de diálogo acionável na reunião para usuários:**</span><span class="sxs-lookup"><span data-stu-id="950b7-142">**In-meeting actionable dialog for users:**</span></span>

![exibição da caixa de diálogo](../assets/images/apps-in-meetings/in-meeting-dialog-view.png)

### <a name="post-meeting-app-experience"></a><span data-ttu-id="950b7-144">Experiência do aplicativo após reunião</span><span class="sxs-lookup"><span data-stu-id="950b7-144">Post-meeting app experience</span></span>

<span data-ttu-id="950b7-145">**Experiência de reunião:**</span><span class="sxs-lookup"><span data-stu-id="950b7-145">**Post-meeting experience:**</span></span>

![Exibir reunião](../assets/images/apps-in-meetings/PostMeeting.png)

<span data-ttu-id="950b7-147">O cenário de aplicativo pós-reunião é semelhante à experiência de reunião atual com o benefício adicional de ter guias na superfície.</span><span class="sxs-lookup"><span data-stu-id="950b7-147">The post-meeting app scenario is similar to the current post-meeting experience with the added benefit of having tabs exist within the surface.</span></span> <span data-ttu-id="950b7-148">Usuários com permissão podem adicionar aplicativos da Galeria de guias a uma reunião por meio da guia **detalhes** no formulário de programação de equipes e na guia **chat** de reunião em uma reunião existente.</span><span class="sxs-lookup"><span data-stu-id="950b7-148">Permissioned users can add apps from the tab gallery to a meeting via the **Details** tab on the Teams scheduling form and the meeting **Chat** tab in an existing meeting.</span></span>

### <a name="bots"></a><span data-ttu-id="950b7-149">Bots</span><span class="sxs-lookup"><span data-stu-id="950b7-149">Bots</span></span>

<span data-ttu-id="950b7-150">Para implementação de bot, Confira nossos [bots na documentação de reuniões do Microsoft Teams](../bots/how-to/create-a-bot-for-teams.md#bots-in-teams-meetings) .</span><span class="sxs-lookup"><span data-stu-id="950b7-150">For bot implementation, please see our [Bots in Teams meetings](../bots/how-to/create-a-bot-for-teams.md#bots-in-teams-meetings) documentation.</span></span>

### <a name="messaging-extensions"></a><span data-ttu-id="950b7-151">Extensões de Mensagens</span><span class="sxs-lookup"><span data-stu-id="950b7-151">Messaging Extensions</span></span>

<span data-ttu-id="950b7-152">Para implementação de extensão de mensagens, Confira nossa documentação [de mensagens de reuniões do teams](../messaging-extensions/how-to/create-messaging-extension.md#messaging-extensions-in-teams-meetings) .</span><span class="sxs-lookup"><span data-stu-id="950b7-152">For messaging extension implementation, please see our [Messaging extensions in Teams meetings](../messaging-extensions/how-to/create-messaging-extension.md#messaging-extensions-in-teams-meetings) documentation.</span></span>

## <a name="participant-roles-and-user-types-in-a-meeting"></a><span data-ttu-id="950b7-153">Funções de participante e tipos de usuários em uma reunião</span><span class="sxs-lookup"><span data-stu-id="950b7-153">Participant roles and user types in a meeting</span></span>

![Participantes de uma reunião](../assets/images/apps-in-meetings/participant-roles.png)

### <a name="participant-roles"></a><span data-ttu-id="950b7-155">Funções de participante</span><span class="sxs-lookup"><span data-stu-id="950b7-155">Participant roles</span></span>

<span data-ttu-id="950b7-156">Você pode criar seu aplicativo com autorização específica do participante.</span><span class="sxs-lookup"><span data-stu-id="950b7-156">You can design your app with participant-specific authorization.</span></span> <span data-ttu-id="950b7-157">Por exemplo, talvez apenas um organizador e/ou apresentador possa criar uma pesquisa em reuniões.</span><span class="sxs-lookup"><span data-stu-id="950b7-157">For example, perhaps only an organizer and/or presenter can create a poll in meetings.</span></span> <span data-ttu-id="950b7-158">Embora as configurações de participante padrão sejam determinadas pelo administrador de ti de uma organização, um organizador da reunião pode querer alterar as configurações de uma reunião específica.</span><span class="sxs-lookup"><span data-stu-id="950b7-158">Although default participant settings are determined by an organization's IT administrator, a meeting organizer may want to change the settings for a specific meeting.</span></span> <span data-ttu-id="950b7-159">Os organizadores podem fazer essas alterações na página da Web opções de reunião.</span><span class="sxs-lookup"><span data-stu-id="950b7-159">Organizers can make these changes on the Meeting options web page.</span></span>

1. <span data-ttu-id="950b7-160">**Organizador**.</span><span class="sxs-lookup"><span data-stu-id="950b7-160">**Organizer**.</span></span> <span data-ttu-id="950b7-161">O organizador agenda uma reunião, define as opções de reunião, atribui funções de reunião e inicia a reunião.</span><span class="sxs-lookup"><span data-stu-id="950b7-161">The organizer schedules a meeting, sets the meeting options, assigns meeting roles, and starts the meeting.</span></span> <span data-ttu-id="950b7-162">Somente os usuários com uma conta do M365 (que possui uma licença do Teams) podem ser organizadores e controlar as permissões dos participantes.</span><span class="sxs-lookup"><span data-stu-id="950b7-162">Only users with a M365 account (possessing a Teams license) can be organizers and control attendee permissions.</span></span>
1. <span data-ttu-id="950b7-163">**Apresentador**.</span><span class="sxs-lookup"><span data-stu-id="950b7-163">**Presenter**.</span></span> <span data-ttu-id="950b7-164">Os apresentadores têm praticamente os mesmos recursos do organizador; no entanto, um apresentador não pode remover um organizador da sessão ou modificar as opções de reunião da sessão.</span><span class="sxs-lookup"><span data-stu-id="950b7-164">Presenters have nearly the same capabilities as organizer; however, a presenter cannot remove an organizer from the session or modify meeting options for the session.</span></span> <span data-ttu-id="950b7-165">Por padrão, os participantes que ingressam em uma reunião têm a função apresentador.</span><span class="sxs-lookup"><span data-stu-id="950b7-165">By default, participants joining a meeting have the presenter role.</span></span>
1. <span data-ttu-id="950b7-166">**Participante**.</span><span class="sxs-lookup"><span data-stu-id="950b7-166">**Attendee**.</span></span> <span data-ttu-id="950b7-167">Um participante é um usuário que foi convidado a participar de uma reunião, mas que não está autorizado a atuar como apresentador.</span><span class="sxs-lookup"><span data-stu-id="950b7-167">An attendee is a user who has been invited to attend a meeting but who is not authorized to act as a presenter.</span></span> <span data-ttu-id="950b7-168">Os participantes podem interagir com outros membros da reunião, mas não podem gerenciar nenhuma configuração de reunião ou compartilhar conteúdo.</span><span class="sxs-lookup"><span data-stu-id="950b7-168">Attendees can interact with other meeting members but cannot manage any of the meeting settings or share content.</span></span>

<span data-ttu-id="950b7-169">_Ver_ [ **funções em uma reunião do teams**](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)</span><span class="sxs-lookup"><span data-stu-id="950b7-169">_See_ [**Roles in a Teams meeting**](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)</span></span>

<span data-ttu-id="950b7-170">Você pode acessar a página  **Opções de reunião** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="950b7-170">You can access the  **Meeting options** page as follows:</span></span>

<span data-ttu-id="950b7-171">&#11200; no Microsoft Teams, **vá para** ![ o logotipo calendário calendário ](../assets/images/apps-in-meetings/calendar-logo.png) , selecione uma reunião e, em seguida, **Opções de reunião**.</span><span class="sxs-lookup"><span data-stu-id="950b7-171">&#11200; In Teams, go to **Calendar** ![calendar logo](../assets/images/apps-in-meetings/calendar-logo.png), select a meeting, and then **Meeting options**.</span></span>

<span data-ttu-id="950b7-172">&#11200; em um convite de reunião, selecione **Opções de reunião**.</span><span class="sxs-lookup"><span data-stu-id="950b7-172">&#11200; In a meeting invitation, select **Meeting options**.</span></span>

<span data-ttu-id="950b7-173">&#11200; durante uma reunião, selecione **Mostrar participantes** ![ Mostrar ícone ](../assets/images/apps-in-meetings/show-participants.png) de participantes nos controles da reunião.</span><span class="sxs-lookup"><span data-stu-id="950b7-173">&#11200; During a meeting, select **Show participants** ![show participants icon](../assets/images/apps-in-meetings/show-participants.png) in the meeting controls.</span></span> <span data-ttu-id="950b7-174">Em seguida, acima da lista de participantes, escolha **gerenciar permissões**.</span><span class="sxs-lookup"><span data-stu-id="950b7-174">Then, above the list of participants, choose **Manage permissions**.</span></span>

### <a name="user-types"></a><span data-ttu-id="950b7-175">Tipos de usuários</span><span class="sxs-lookup"><span data-stu-id="950b7-175">User types</span></span>

> [!NOTE]
> <span data-ttu-id="950b7-176">Os tipos de usuário podem participar de reuniões e assumir uma das funções de participante descritas acima.</span><span class="sxs-lookup"><span data-stu-id="950b7-176">User types can join meetings and assume one of the participant roles described above.</span></span> <span data-ttu-id="950b7-177">O tipo de usuário não é exposto como parte da API **getParticipantRole** .</span><span class="sxs-lookup"><span data-stu-id="950b7-177">The User type is not exposed as part of the **getParticipantRole** API.</span></span>

1. <span data-ttu-id="950b7-178">**Dentro do locatário**.</span><span class="sxs-lookup"><span data-stu-id="950b7-178">**In-tenant**.</span></span> <span data-ttu-id="950b7-179">Esses usuários pertencem à organização e têm credenciais no Azure Active Directory para o locatário.</span><span class="sxs-lookup"><span data-stu-id="950b7-179">These users belong to the organization and have credentials in Azure Active Directory for the tenant.</span></span> <span data-ttu-id="950b7-180">Em geral, eles são funcionários remotos ou no local.</span><span class="sxs-lookup"><span data-stu-id="950b7-180">They are usually full-time, onsite or remote employees.</span></span>
1. <span data-ttu-id="950b7-181">**Convidado**.</span><span class="sxs-lookup"><span data-stu-id="950b7-181">**Guest**.</span></span> <span data-ttu-id="950b7-182">Um convidado é um participante de outra organização que tenha sido convidado a acessar o Microsoft Teams ou outros recursos no locatário da sua organização.</span><span class="sxs-lookup"><span data-stu-id="950b7-182">A guest is a participant from another organization who has been invited to access Teams or other resources in your organization's tenant.</span></span> <span data-ttu-id="950b7-183">Os convidados são adicionados ao Active Directory da sua organização e podem receber praticamente todos os mesmos recursos do teams que um membro da equipe nativo com acesso total aos bate-papos, reuniões e arquivos da equipe.</span><span class="sxs-lookup"><span data-stu-id="950b7-183">Guests are added to your organization’s Active Directory and can be given nearly all the same Teams capabilities as a native team member with full access to team chats, meetings, and files.</span></span> <span data-ttu-id="950b7-184">_Ver_ [o acesso de convidados no Microsoft Teams](/microsoftteams/guest-access)</span><span class="sxs-lookup"><span data-stu-id="950b7-184">_See_ [Guest access in Microsoft Teams](/microsoftteams/guest-access)</span></span>
1. <span data-ttu-id="950b7-185">**Federado/externo**.</span><span class="sxs-lookup"><span data-stu-id="950b7-185">**Federated/External**.</span></span> <span data-ttu-id="950b7-186">Um usuário federado é um usuário do teams externo em outra organização que foi convidado a participar de uma reunião.</span><span class="sxs-lookup"><span data-stu-id="950b7-186">A federated user is an external Teams user in another organization who has been invited to join a meeting.</span></span> <span data-ttu-id="950b7-187">Como esses usuários têm credenciais válidas com parceiros federados, eles são tratados como autenticados pelo Teams, mas não têm acesso às suas equipes ou a outros recursos compartilhados da sua organização.</span><span class="sxs-lookup"><span data-stu-id="950b7-187">Since these users have valid credentials with federated partners, they are treated as authenticated by Teams but do not have access to your teams or other shared resources from your organization.</span></span> <span data-ttu-id="950b7-188">Se você deseja que usuários externos tenham acesso a equipes e canais, o acesso de convidados pode ser uma opção melhor.</span><span class="sxs-lookup"><span data-stu-id="950b7-188">If you want external users to have access to teams and channels, guest access might be a better option.</span></span> <span data-ttu-id="950b7-189">_Consulte_ [gerenciar o acesso externo no Microsoft Teams](/microsoftteams/manage-external-access)</span><span class="sxs-lookup"><span data-stu-id="950b7-189">_See_ [Manage external access in Microsoft Teams](/microsoftteams/manage-external-access)</span></span>
1. <span data-ttu-id="950b7-190">**Anônimo**.</span><span class="sxs-lookup"><span data-stu-id="950b7-190">**Anonymous**.</span></span> <span data-ttu-id="950b7-191">Os usuários anônimos não têm uma identidade do Active Directory e não são federados com um locatário.</span><span class="sxs-lookup"><span data-stu-id="950b7-191">Anonymous users do not have an Active Directory identity and are not federated with a tenant.</span></span> <span data-ttu-id="950b7-192">O participante anônimo é como um usuário externo, mas sua identidade não é projetada na reunião.</span><span class="sxs-lookup"><span data-stu-id="950b7-192">The anonymous participant is like an external user, but their identity is not projected into the meeting.</span></span> <span data-ttu-id="950b7-193">Usuários anônimos não poderão acessar aplicativos em uma janela de reunião.</span><span class="sxs-lookup"><span data-stu-id="950b7-193">Anonymous users will not be able to access apps in a meeting window.</span></span>

## <a name="next-steps"></a><span data-ttu-id="950b7-194">Próximos passos</span><span class="sxs-lookup"><span data-stu-id="950b7-194">Next Steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="950b7-195">Crie aplicativos para reuniões do Teams</span><span class="sxs-lookup"><span data-stu-id="950b7-195">Create apps for Teams meetings</span></span>](create-apps-for-teams-meetings.md)
