---
title: Microsoft Teams de aplicativos
description: Links e descrições de modelos de aplicativos para a Microsoft Teams plataforma
ms.topic: reference
keywords: Microsoft Teams exemplos de modelos
localization_priority: Normal
ms.author: lajanuar
author: laujan
ms.openlocfilehash: 8cfb066ee3c202fb8611a61bbde3058207a62a35
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566237"
---
# <a name="app-templates-for-microsoft-teams"></a><span data-ttu-id="4af47-104">Modelos de aplicativos para o Teams</span><span class="sxs-lookup"><span data-stu-id="4af47-104">App templates for Microsoft Teams</span></span>

<span data-ttu-id="4af47-105">Modelos de aplicativo são exemplos de aplicativos completos para Microsoft Teams que são de código aberto e disponíveis em GitHub.</span><span class="sxs-lookup"><span data-stu-id="4af47-105">App templates are examples of complete apps for Microsoft Teams that are open-source and available on GitHub.</span></span> <span data-ttu-id="4af47-106">Cada modelo de aplicativo contém instruções detalhadas para implantar e instalar esse aplicativo para sua organização.</span><span class="sxs-lookup"><span data-stu-id="4af47-106">Each app template contains detailed instructions for deploying and installing that app for your organization.</span></span> <span data-ttu-id="4af47-107">Ele também fornece um aplicativo de exemplo que você pode instalar e começar a usar imediatamente.</span><span class="sxs-lookup"><span data-stu-id="4af47-107">It also provides a sample app that you can install and start using immediately.</span></span> <span data-ttu-id="4af47-108">O código-fonte completo também está disponível, o que permite explorá-lo em detalhes ou bifurcar o código e alterá-lo para atender aos seus requisitos específicos.</span><span class="sxs-lookup"><span data-stu-id="4af47-108">The complete source code is also available, which allows you to explore it in detail or fork the code and alter it to meet your specific requirements.</span></span>
<span data-ttu-id="4af47-109">Todos os modelos de aplicativo são fornecidos nos termos de [Licença do MIT.](https://github.com/OfficeDev/microsoft-teams-apps-eprescription/blob/master/LICENSE)</span><span class="sxs-lookup"><span data-stu-id="4af47-109">All app templates are provided under the [MIT License](https://github.com/OfficeDev/microsoft-teams-apps-eprescription/blob/master/LICENSE) terms.</span></span>

> [!NOTE] 
> <span data-ttu-id="4af47-110">Você deve licenciar e dar suporte a aplicativos criados a partir de modelos de aplicativos para seus usuários e organizações.</span><span class="sxs-lookup"><span data-stu-id="4af47-110">You must license and support apps created from app templates for your users and organizations.</span></span>

<span data-ttu-id="4af47-111">**&#9734; Indica modelos de aplicativo recém-lançados.**</span><span class="sxs-lookup"><span data-stu-id="4af47-111">**&#9734; Indicates newly released app templates.**</span></span>

### <a name="key-benefits"></a><span data-ttu-id="4af47-112">Principais benefícios</span><span class="sxs-lookup"><span data-stu-id="4af47-112">Key benefits</span></span>

* <span data-ttu-id="4af47-113">**Implantar diretamente na nuvem:** Todos os modelos de aplicativo incluem scripts de implantação que permitem hospedar todos os serviços necessários no Microsoft Azure ou na Plataforma Power.</span><span class="sxs-lookup"><span data-stu-id="4af47-113">**Deploy directly to the cloud:** All app templates include deployment scripts that allows you to host all required services in Microsoft Azure or the Power Platform.</span></span> 
* <span data-ttu-id="4af47-114">**Código de exemplo recomendado:** Os modelos de aplicativo estão em conformidade com as práticas recomendadas em torno da segurança e da infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="4af47-114">**Recommended sample code:** The app templates conform to recommended best practices around security and infrastructure.</span></span> <span data-ttu-id="4af47-115">Todas as alterações enviadas pela comunidade aos modelos de aplicativos são revisadas para garantir a conformidade.</span><span class="sxs-lookup"><span data-stu-id="4af47-115">All community submitted changes to the app templates are reviewed to ensure conformance.</span></span>
* <span data-ttu-id="4af47-116">**Personalizável e extensível:** Embora todos os modelos de aplicativo sejam implantados com configuração mínima, toda a base de código e scripts de implantação são fornecidos, para que você possa personalizá-los ou estendí-los facilmente para se ajustar às suas necessidades exclusivas.</span><span class="sxs-lookup"><span data-stu-id="4af47-116">**Customizable and extensible:** While all app templates are deployed with minimal configuration, the entire code base and deployment scripts are provided, so that you can easily customize or extend them to fit your unique needs.</span></span>
* <span data-ttu-id="4af47-117">**Documentação detalhada:** Todos os modelos de aplicativo são acompanhados por documentação de ponta a ponta em etapas de arquitetura de solução, implantação e configuração.</span><span class="sxs-lookup"><span data-stu-id="4af47-117">**Detailed documentation:** All app templates are accompanied by end-to-end documentation on solution architecture, deployment, and configuration steps.</span></span>  

## <a name="adoption-bot"></a><span data-ttu-id="4af47-118">Bot de adoção</span><span class="sxs-lookup"><span data-stu-id="4af47-118">Adoption Bot</span></span> 

<span data-ttu-id="4af47-119">O Bot de Adoção é um bot de chat de cuidado do usuário criado com o Power Virtual Agent para Teams PVA.</span><span class="sxs-lookup"><span data-stu-id="4af47-119">Adoption Bot is a user care chat bot built with Power Virtual Agent for Teams PVA.</span></span> <span data-ttu-id="4af47-120">Ele é considerado como a versão PVA do FaQ Plus.</span><span class="sxs-lookup"><span data-stu-id="4af47-120">It is considered as the PVA version of FAQ Plus.</span></span> <span data-ttu-id="4af47-121">O Bot de Adoção responde a mais de 100 perguntas comuns sobre Microsoft 365 e Teams.</span><span class="sxs-lookup"><span data-stu-id="4af47-121">Adoption Bot answers 100+ common questions about Microsoft 365 and Teams.</span></span> <span data-ttu-id="4af47-122">Você pode editar os tópicos existentes, adicionar seus próprios tópicos e ingerir perguntas frequentes existentes.</span><span class="sxs-lookup"><span data-stu-id="4af47-122">You can edit the existing topics, add your own topics, and ingest existing FAQs.</span></span> <span data-ttu-id="4af47-123">Se os usuários precisarem de ajuda adicional, o Bot de Adoção poderá conectá-los a especialistas ou até mesmo ser estendido para abrir tíquetes de serviço com conectores de fluxo premium.</span><span class="sxs-lookup"><span data-stu-id="4af47-123">If users need additional help, Adoption Bot can connect them to experts or even be extended to open service tickets with premium flow connectors.</span></span> <span data-ttu-id="4af47-124">Esse bot é auto-instalado ou integrado a um aplicativo personalizado, como o [Hub de Adoção](https://github.com/akporzondek/adoption_hub).</span><span class="sxs-lookup"><span data-stu-id="4af47-124">This bot is self-installed or built into a custom app, such as the [Adoption Hub](https://github.com/akporzondek/adoption_hub).</span></span>

[<span data-ttu-id="4af47-125">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-125">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-adopt-bot)

## <a name="adoption-tool--champion-management-platform-9734"></a><span data-ttu-id="4af47-126">Ferramenta de Adoção - Plataforma de Gerenciamento de Campeões &#9734;</span><span class="sxs-lookup"><span data-stu-id="4af47-126">Adoption Tool- Champion Management Platform &#9734;</span></span>

<span data-ttu-id="4af47-127">O modelo de aplicativo da Plataforma de Gerenciamento de Campeões (CMP) ajuda você a gerenciar, dimensionar e inspirar seus defensores do trabalho em equipe a obter mais.</span><span class="sxs-lookup"><span data-stu-id="4af47-127">The Champion Management Platform (CMP) app template helps you manage, scale, and inspire your teamwork champions to achieve more.</span></span> <span data-ttu-id="4af47-128">Esse modelo de aplicativo é criado no Estrutura do SharePoint e carregado em uma guia dentro de uma equipe.</span><span class="sxs-lookup"><span data-stu-id="4af47-128">This app template is built on the SharePoint Framework and loaded into a tab within a team.</span></span> <span data-ttu-id="4af47-129">Os grupos podem aproveitar essa ferramenta para ajudar a gerenciar a associação ao programa, fornecer uma tabela de líderes e tipos de eventos para registro em log e ferramentas para sobrepor selos digitais aos participantes do programa.</span><span class="sxs-lookup"><span data-stu-id="4af47-129">Groups can leverage this tool to help manage program membership, provide a leaderboard and event types for logging, and tools to overlay digital badges to program participants.</span></span>

[<span data-ttu-id="4af47-130">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-130">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-champion-management)

## <a name="adoption-tool--microsoft-365-learning-pathways-get-started-9734"></a><span data-ttu-id="4af47-131">Ferramenta de Adoção- Microsoft 365 caminhos de aprendizagem (Introdução) &#9734;</span><span class="sxs-lookup"><span data-stu-id="4af47-131">Adoption Tool- Microsoft 365 Learning Pathways (Get Started) &#9734;</span></span>

<span data-ttu-id="4af47-132">O Introdução de aplicativo permite que você traga o poder de Microsoft 365 de aprendizado dentro do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="4af47-132">The Get Started app template allows you to bring the power of Microsoft 365 learning pathways inside of Microsoft Teams.</span></span> <span data-ttu-id="4af47-133">Este modelo de aplicativo permite que você conceda fácil acesso a páginas de treinamento específicas ou a outros ativos de intranet e carregue o conteúdo diretamente no Teams.</span><span class="sxs-lookup"><span data-stu-id="4af47-133">This app template allows you to grant easy access to specific training pages or other intranet assets and load the content directly within Teams.</span></span> <span data-ttu-id="4af47-134">Você também pode alterar o nome do aplicativo ou o logotipo para corresponder à identidade visual da sua empresa.</span><span class="sxs-lookup"><span data-stu-id="4af47-134">You can also change the app name or logo to match your company branding.</span></span>

[<span data-ttu-id="4af47-135">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-135">Get it on GitHub</span></span>](https://github.com/msft-teams/tools/tree/master/M365%20Learning%20Pathways)

## <a name="appointment-manager"></a><span data-ttu-id="4af47-136">Gerenciador de Compromissos</span><span class="sxs-lookup"><span data-stu-id="4af47-136">Appointment Manager</span></span> 

<span data-ttu-id="4af47-137">O Gerenciador de Compromissos é um Teams de aplicativos para ajudar as empresas a criar, gerenciar e conduzir compromissos virtuais com os consumidores por meio Teams.</span><span class="sxs-lookup"><span data-stu-id="4af47-137">Appointment Manager is a Teams app template to help businesses create, manage, and conduct virtual appointments with consumers through Teams.</span></span> <span data-ttu-id="4af47-138">As novas solicitações de compromisso dos consumidores ficam visíveis Teams canais, onde são atribuídas rapidamente e reatribuídas à equipe em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="4af47-138">New appointment requests from consumers are visible in Teams channels, where they are quickly assigned and reassigned to staff in a team.</span></span> <span data-ttu-id="4af47-139">As solicitações de compromisso são exibidas em níveis de equipe ou pessoal por meio de guias personalizadas.</span><span class="sxs-lookup"><span data-stu-id="4af47-139">Appointment requests are viewed at team or personal levels through custom tabs.</span></span> <span data-ttu-id="4af47-140">Cada compromisso é associado a uma reunião Teams online, portanto, a equipe e os consumidores podem participar facilmente da reunião no horário agendado.</span><span class="sxs-lookup"><span data-stu-id="4af47-140">Every appointment is associated with a Teams online meeting, hence the staff and consumers can easily join the meeting at the scheduled time.</span></span>

<span data-ttu-id="4af47-141">O modelo de aplicativo se integra ao Microsoft Bookings para facilitar o gerenciamento de compromissos.</span><span class="sxs-lookup"><span data-stu-id="4af47-141">The app template integrates with Microsoft Bookings for easy appointment management.</span></span> <span data-ttu-id="4af47-142">Os compromissos agendados aparecem automaticamente nos calendários dos membros da equipe atribuídos, e os consumidores recebem notificações de email e lembretes personalizáveis com links de reunião incorporados.</span><span class="sxs-lookup"><span data-stu-id="4af47-142">Scheduled appointments automatically appear on assigned staff members' calendars, and consumers receive customizable email notifications and reminders with embedded meeting links.</span></span>

[<span data-ttu-id="4af47-143">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-143">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-appointment-manager)

<span data-ttu-id="4af47-144">![Gerenciador de Compromissos Visão Geral ](../assets/images/appointment-manager-overview.png)
 ![ do Gerenciador de Compromissos no Teams](../assets/images/appointment-manager-2.png)</span><span class="sxs-lookup"><span data-stu-id="4af47-144">![Appointment Manager Overview](../assets/images/appointment-manager-overview.png)
![Appointment Manager in Teams](../assets/images/appointment-manager-2.png)</span></span>

## <a name="ask-away"></a><span data-ttu-id="4af47-145">Ask Away</span><span class="sxs-lookup"><span data-stu-id="4af47-145">Ask Away</span></span>

<span data-ttu-id="4af47-146">Ask Away é um [Microsoft Teams que](../bots/what-are-bots.md) permite que os usuários conduzam Perguntas e Respostas, chamadas de Q&A em Teams.</span><span class="sxs-lookup"><span data-stu-id="4af47-146">Ask Away is a [Microsoft Teams bot](../bots/what-are-bots.md) that enables users to conduct Question and Answer, called Q&A sessions within Teams.</span></span> <span data-ttu-id="4af47-147">Usando o bot Ask Away, os membros da equipe podem enviar e fazer perguntas de votação compartilhadas por colegas, permitindo que os hosts de Q&A reúnam facilmente perguntas importantes em um canal ou chat.</span><span class="sxs-lookup"><span data-stu-id="4af47-147">Using the Ask Away bot, team members can submit and up-vote questions shared by colleagues allowing Q&A hosts to easily gather top-of-mind questions within a channel or chat.</span></span> <span data-ttu-id="4af47-148">O bot é usado para conduzir uma sessão Q&A em tempo real em uma reunião Teams e permite que os participantes enviem perguntas ao vivo por chat.</span><span class="sxs-lookup"><span data-stu-id="4af47-148">The bot is used to conduct a real-time Q&A session in a Teams meeting and allows attendees to submit questions live through chat.</span></span>

[<span data-ttu-id="4af47-149">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-149">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-askaway)

:::row:::
  :::column span="2":::
    ![Exibição da caixa de diálogo pop-up de quadro de líderes para que os usuários votem em perguntas](../assets/images/ask-away-app.png)  
:::column-end:::
:::row-end:::

## <a name="associate-insights"></a><span data-ttu-id="4af47-151">Informações associadas</span><span class="sxs-lookup"><span data-stu-id="4af47-151">Associate Insights</span></span>

<span data-ttu-id="4af47-152">Associate Insights é um [modelo Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) que capacita os funcionários de primeira linha a capturar e enviar diretamente a opinião, o sentimento e a percepção do cliente.</span><span class="sxs-lookup"><span data-stu-id="4af47-152">Associate Insights is a [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) template that empowers firstline workers to directly capture and submit customer opinion, sentiment, and perception.</span></span> <span data-ttu-id="4af47-153">Os funcionários de primeira linha geralmente são o primeiro representante da empresa a se envolver com os clientes em um ponto de contato de um para um.</span><span class="sxs-lookup"><span data-stu-id="4af47-153">Firstline workers are often the first company representative to engage with customers in a one-to-one point-of contact.</span></span> <span data-ttu-id="4af47-154">Os dados coletados são compartilhados e usados de forma colaborativa por equipes de negócios, como por meio de uma guia Power BI Teams, para melhorar o produto e melhorar a experiência do cliente.</span><span class="sxs-lookup"><span data-stu-id="4af47-154">The collected data are shared and used collaboratively by business teams, such as through a Power BI Teams tab, for product improvement and enhancing the customer experience.</span></span>

[<span data-ttu-id="4af47-155">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-155">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-associateinsights)

:::row:::
  :::column span="2":::
    ![Exibição de feedback de insights gerados pelo aplicativo](../assets/images/associate-insights-app.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Power BI exibição de insights gerados pelo aplicativo](../assets/images/associate-insights-app2.png)
:::column-end:::
:::row-end:::

## <a name="attendance"></a><span data-ttu-id="4af47-158">Participação</span><span class="sxs-lookup"><span data-stu-id="4af47-158">Attendance</span></span>

<span data-ttu-id="4af47-159">O aplicativo de participação é [uma Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) guia que é fixada em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="4af47-159">The Attendance app is a [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) tab that are pinned in a team.</span></span> <span data-ttu-id="4af47-160">Ele foi projetado para registrar a presença em configurações, como ambientes de aprendizado e treinamento.</span><span class="sxs-lookup"><span data-stu-id="4af47-160">It is designed to record presence in settings, such as learning and training environments.</span></span> <span data-ttu-id="4af47-161">Os usuários podem marcar ou editar a participação por até 30 dias no passado e exibir relatórios de participação resumidos para um grupo inteiro ou participantes individuais.</span><span class="sxs-lookup"><span data-stu-id="4af47-161">Users can mark or edit attendance for up to 30 days in the past and view summarized attendance reports for an entire group or individual attendees.</span></span> <span data-ttu-id="4af47-162">Para obter mais informações sobre a participação das equipes, consulte [Get it on GitHub](https://github.com/OfficeDev/microsoft-teams-apps-attendance).</span><span class="sxs-lookup"><span data-stu-id="4af47-162">For more information on teams attendance, see [Get it on GitHub](https://github.com/OfficeDev/microsoft-teams-apps-attendance).</span></span>

<span data-ttu-id="4af47-163">A imagem a seguir exibe a demonstração do aplicativo de participação:</span><span class="sxs-lookup"><span data-stu-id="4af47-163">The following image displays the attendance app demo:</span></span>  

![Demonstração do aplicativo de participação](../assets/images/attendance-app.png)

## <a name="book-a-room"></a><span data-ttu-id="4af47-165">Book-a-room</span><span class="sxs-lookup"><span data-stu-id="4af47-165">Book-a-room</span></span>

<span data-ttu-id="4af47-166">Book-a-room é um [Microsoft Teams que](../bots/what-are-bots.md) permite aos usuários encontrar e reservar rapidamente uma sala de reunião por 30, 60 ou 90 minutos a partir da hora atual.</span><span class="sxs-lookup"><span data-stu-id="4af47-166">Book-a-room is a [Microsoft Teams bot](../bots/what-are-bots.md) that allows users quickly to find and reserve a meeting room for 30, 60, or 90 minutes starting from the current time.</span></span> <span data-ttu-id="4af47-167">O tempo padrão é de 30 minutos.</span><span class="sxs-lookup"><span data-stu-id="4af47-167">The default time is 30 minutes.</span></span> <span data-ttu-id="4af47-168">Os escopos de bot book-a-room para conversas pessoais ou 1:1.</span><span class="sxs-lookup"><span data-stu-id="4af47-168">The Book-a-room bot scopes to personal or 1:1 conversations.</span></span> <span data-ttu-id="4af47-169">Para obter mais informações sobre o aplicativo Book-a-room, consulte [Get it on GitHub](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom).</span><span class="sxs-lookup"><span data-stu-id="4af47-169">For more information on Book-a-room app, see [Get it on GitHub](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom).</span></span>  
<span data-ttu-id="4af47-170">A imagem a seguir exibe a demonstração Book-a-room:</span><span class="sxs-lookup"><span data-stu-id="4af47-170">The following image displays the Book-a-room demo:</span></span>

![Demonstração de book-a-room](../assets/images/book-a-room.png)

## <a name="building-access"></a><span data-ttu-id="4af47-172">Criando o Access</span><span class="sxs-lookup"><span data-stu-id="4af47-172">Building Access</span></span>

<span data-ttu-id="4af47-173">O Building Access é um aplicativo baseado na Plataforma Do Microsoft [Power](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/) que oferece suporte à administração da criação de limites de ocupação e de normas de distanciamento social, permitindo que os diretores de instalações gerenciem, acompanhem e reportem a presença do funcionário no local.</span><span class="sxs-lookup"><span data-stu-id="4af47-173">Building Access is a Microsoft [Power Platform](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/) based app that supports the administration of building occupancy thresholds and social distancing norms by enabling facilities directors to manage, track, and report employee on-site presence.</span></span> <span data-ttu-id="4af47-174">O aplicativo, criado usando o Microsoft [Power Apps](/powerapps/powerapps-overview)e [o Power Automate,](/power-automate/getting-started)integra-se profundamente ao Microsoft Teams e permite que as organizações determinem a preparação para a criação, estabeleçam critérios de qualificação para acesso no site e reúnam ideias para o planejamento futuro.</span><span class="sxs-lookup"><span data-stu-id="4af47-174">The app, built using Microsoft [Power Apps](/powerapps/powerapps-overview), and [Power Automate](/power-automate/getting-started), deeply integrates with Microsoft Teams and enables organizations to determine building readiness, establish eligibility criteria for on-site access, and gather insights for future planning.</span></span>

[<span data-ttu-id="4af47-175">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-175">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-buildingaccess)

:::row:::
   :::column span="":::
     ![Criar cartão de reserva do Access](../assets/images/building-access-reservation.png)
   :::column-end:::
   :::column span="":::
      ![Exibição de teclas do Building Access](../assets/images/building-access-access-key.png)
   :::column-end:::
:::row-end:::

## <a name="celebrations"></a><span data-ttu-id="4af47-178">Celebrações</span><span class="sxs-lookup"><span data-stu-id="4af47-178">Celebrations</span></span>

<span data-ttu-id="4af47-179">Celebrações é um Teams que ajuda os membros da equipe a comemorar aniversários, aniversários e outros eventos recorrentes.</span><span class="sxs-lookup"><span data-stu-id="4af47-179">Celebrations is a Teams app that helps team members to celebrate each others' birthdays, anniversaries, and other recurring events.</span></span> <span data-ttu-id="4af47-180">Ele lembra ocasiões especiais de todos os membros da equipe e envia uma mensagem amigável em todas as equipes selecionadas no momento da criação do evento, para fazer com que os membros da equipe se sintam especiais em seus dias.</span><span class="sxs-lookup"><span data-stu-id="4af47-180">It remembers special occasions of all the team members and sends a friendly message in all the teams selected at the time of event creation, to make the team members feel special on their day.</span></span>

<span data-ttu-id="4af47-181">O aplicativo fornece uma interface fácil para todos os membros da equipe adicionarem e exibirem seus eventos pessoalmente e também permitem que o usuário selecione as equipes nas quais os eventos são compartilhados.</span><span class="sxs-lookup"><span data-stu-id="4af47-181">The app provides an easy interface for all the team members to personally add and view their events and also allows the user to select the teams in which the events gets shared.</span></span>

[<span data-ttu-id="4af47-182">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-182">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-celebrations-app)

## <a name="checklist"></a><span data-ttu-id="4af47-183">Lista de verificação</span><span class="sxs-lookup"><span data-stu-id="4af47-183">Checklist</span></span>

<span data-ttu-id="4af47-184">Checklist é um aplicativo [](../messaging-extensions/what-are-messaging-extensions.md) de extensão Microsoft Teams mensagens personalizado que permite que você colabore com sua equipe criando uma lista de verificação compartilhada em um chat ou canal.</span><span class="sxs-lookup"><span data-stu-id="4af47-184">Checklist is a custom Microsoft Teams [messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that enables you to collaborate with your team by creating a shared checklist in a chat or channel.</span></span> <span data-ttu-id="4af47-185">O aplicativo tem suporte em todos os clientes Teams plataforma, como navegador de área de trabalho, iOS e Android.</span><span class="sxs-lookup"><span data-stu-id="4af47-185">The app is supported across all Teams platform clients, such as desktop browser, iOS, and Android.</span></span> <span data-ttu-id="4af47-186">O aplicativo está pronto para implantação como parte de sua assinatura Microsoft 365 usuário.</span><span class="sxs-lookup"><span data-stu-id="4af47-186">The app is ready for deployment as part of your Microsoft 365 subscription.</span></span>  

[<span data-ttu-id="4af47-187">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-187">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-checklist-app)

:::row:::
:::column span="2":::
    ![Criar lista de verificação no Teams exibição](../assets/images/checklist-app-template-compose-view.gif)  
:::column-end:::
:::row-end:::

## <a name="classroom-drop-in"></a><span data-ttu-id="4af47-189">Drop-in de sala de aula</span><span class="sxs-lookup"><span data-stu-id="4af47-189">Classroom Drop-in</span></span> 

<span data-ttu-id="4af47-190">O Drop-in de sala de aula é um aplicativo baseado na Plataforma [Microsoft Power](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/)que permite que os líderes do sistema encontrem equipes de classe, significa salas de aula virtuais e adicionem a si mesmos ou outras pessoas a essas equipes de classe por um período de entrega especificado, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="4af47-190">Classroom Drop-in is a Microsoft [Power Platform](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/)-based app that enables system leaders to find class teams, means virtual classrooms and add themselves or others to these class teams for a specified drop-in period, as needed.</span></span> <span data-ttu-id="4af47-191">O aplicativo criado usando o Microsoft [Power Apps](/powerapps/powerapps-overview) e [o Power Automate](/power-automate/getting-started), integra-se profundamente ao Microsoft Teams para garantir que os institutos educacionais possam otimizar suas operações em um ambiente de aprendizado híbrido, fornecendo acesso a participantes relevantes para equipes de classe por requisitos comerciais.</span><span class="sxs-lookup"><span data-stu-id="4af47-191">The app built using Microsoft [Power Apps](/powerapps/powerapps-overview) and [Power Automate](/power-automate/getting-started), deeply integrates with Microsoft Teams to ensure educational institutes can optimize their operations in a hybrid learning environment by providing access to relevant stakeholders for class teams per business requirements.</span></span>

[<span data-ttu-id="4af47-192">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-192">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-classroom-dropin)

![Solicitação de drop-in de sala de aula](../assets/images/classroom-drop-in-request.png)

## <a name="company-communicator"></a><span data-ttu-id="4af47-194">Communicator da empresa</span><span class="sxs-lookup"><span data-stu-id="4af47-194">Company Communicator</span></span>

<span data-ttu-id="4af47-195">O aplicativo Communicator company permite que as equipes corporativas criem e enviem mensagens destinadas a várias equipes ou a um grande número de funcionários por chat, permitindo que a organização chegue aos funcionários exatamente onde colaboram.</span><span class="sxs-lookup"><span data-stu-id="4af47-195">The Company Communicator app enables corporate teams to create and send messages intended for multiple teams or large number of employees over chat allowing organization to reach employees right where they collaborate.</span></span> <span data-ttu-id="4af47-196">Utilize esse modelo para vários cenários, como novos comunicados de iniciativa, integração de funcionários, aprendizado moderno e desenvolvimento ou transmissões em toda a organização.</span><span class="sxs-lookup"><span data-stu-id="4af47-196">Utilize this template for multiple scenarios such as new initiative announcements, employee onboarding, modern learning, and development or organization-wide broadcasts.</span></span>

<span data-ttu-id="4af47-197">O aplicativo fornece uma interface fácil para usuários designados criar, visualizar, colaborar e enviar mensagens.</span><span class="sxs-lookup"><span data-stu-id="4af47-197">The app provides an easy interface for designated users to create, preview, collaborate and send messages.</span></span>

<span data-ttu-id="4af47-198">Ele fornece uma base para criar recursos personalizados de comunicação direcionada, como telemetria personalizada, em quantos usuários reconheceram ou interagiram com uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="4af47-198">It provides a foundation to build custom targeted communication capabilities such as custom telemetry on how many users acknowledged or interacted with a message.</span></span>

[<span data-ttu-id="4af47-199">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-199">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-company-communicator-app)

![jCompany Communicator de caixa de redação](../assets/images/CompanyCommunicatorCompose.png)

## <a name="contact-group-lookup"></a><span data-ttu-id="4af47-201">Procurar grupo de contatos</span><span class="sxs-lookup"><span data-stu-id="4af47-201">Contact Group Lookup</span></span>

<span data-ttu-id="4af47-202">O aplicativo de Pesquisa de Grupo de Contatos fornece uma abordagem conveniente e útil para criar, acessar e gerenciar os grupos de contatos da sua organização, anteriormente conhecidos como listas de distribuição ou grupos de comunicação.</span><span class="sxs-lookup"><span data-stu-id="4af47-202">The Contact Group Lookup app provides a convenient and useful approach to creating, accessing, and managing your organization's contact groups, formerly known as distribution lists or communication groups.</span></span> <span data-ttu-id="4af47-203">Os usuários podem exibir e conversar rapidamente com membros do grupo, exibir o status do membro e criar um chat de grupo com membros selecionados no grupo de contatos, tudo dentro do ambiente Teams de grupo.</span><span class="sxs-lookup"><span data-stu-id="4af47-203">Users can quickly view and chat with group members, view member status, and create a group chat with selected members in the contact group, all within the Teams environment.</span></span>

[<span data-ttu-id="4af47-204">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-204">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-app-contactgrouplookup)

:::row:::
:::column span="2":::
    ![Visão de favoritos fixados da Aparência de Grupo de Contato](../assets/images/contact-group-lookup-favorites.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Demonstração de chat inicial de Lookup de Grupo de Contato](../assets/images/contact-group-lookup-chat.png)
:::column-end:::
:::row-end:::

## <a name="co-worker-appreciation"></a><span data-ttu-id="4af47-207">Reconhecimento de colegas de trabalho</span><span class="sxs-lookup"><span data-stu-id="4af47-207">Co-worker Appreciation</span></span> 

<span data-ttu-id="4af47-208">Usando o modelo de reconhecimento de colegas de trabalho no Microsoft Teams, os usuários podem reconhecer as conquistas de seus colegas no contexto Teams do usuário.</span><span class="sxs-lookup"><span data-stu-id="4af47-208">Using the co-worker appreciation template in Microsoft Teams, users can recognize their colleagues' achievements within the Teams’ context.</span></span> <span data-ttu-id="4af47-209">Quando os colegas de trabalho selecionam recompensar um colega, os destinatários e outros membros da equipe são marcados em uma conversa de canal e recebem uma notificação sobre os detalhes do prêmio do canal.</span><span class="sxs-lookup"><span data-stu-id="4af47-209">When co-workers select to reward a colleague, recipients and other team members are tagged in a channel conversation and they receive a notification about the channel's award details.</span></span> <span data-ttu-id="4af47-210">Os prêmios são registrados no aplicativo Teams, que é seguro, portátil e compartilhável facilmente.</span><span class="sxs-lookup"><span data-stu-id="4af47-210">The awards are recorded in the Teams app, which is secure, portable, and easily shareable.</span></span> <span data-ttu-id="4af47-211">Isso é considerado como a versão baseada no PowerApps do modelo de aplicativo Open Badges, com uma tabela de classificação.</span><span class="sxs-lookup"><span data-stu-id="4af47-211">This is considered as the PowerApps based version of the Open Badges app template, with a leaderboard.</span></span>

[<span data-ttu-id="4af47-212">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-212">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-coworker-appreciation)

![Geral](../assets/images/coworker-appreciation-1.png)

## <a name="crowdsourcer"></a><span data-ttu-id="4af47-214">CrowdSourcer</span><span class="sxs-lookup"><span data-stu-id="4af47-214">CrowdSourcer</span></span>

<span data-ttu-id="4af47-215">CrowdSourcer é um [Microsoft Teams que](../bots/what-are-bots.md) fornece informações consultadas às equipes de forma colaborativa de membros do grupo.</span><span class="sxs-lookup"><span data-stu-id="4af47-215">CrowdSourcer is a [Microsoft Teams bot](../bots/what-are-bots.md) that gives teams queried information sourced collaboratively from group members.</span></span> <span data-ttu-id="4af47-216">Ele ajuda a responder a perguntas frequentes ao permitir que os participantes se envolvam ativamente e contribuam para um recurso de informações divertido e útil.</span><span class="sxs-lookup"><span data-stu-id="4af47-216">It helps to answer frequently asked questions while enabling participants to actively engage in and contribute to a fun and helpful information resource.</span></span>

[<span data-ttu-id="4af47-217">Obter no Github</span><span class="sxs-lookup"><span data-stu-id="4af47-217">Get it on Github</span></span>](https://github.com/OfficeDev/microsoft-teams-crowdsourcer-app)

![Interação do usuário final do Crowdsource](../assets/images/crowdsourcer.png)

## <a name="custom-stickers"></a><span data-ttu-id="4af47-219">Adesivos personalizados</span><span class="sxs-lookup"><span data-stu-id="4af47-219">Custom Stickers</span></span>

<span data-ttu-id="4af47-220">A auto expressão é fundamental para uma cultura de equipe saudável.</span><span class="sxs-lookup"><span data-stu-id="4af47-220">Self-expression is core to a healthy team culture.</span></span> <span data-ttu-id="4af47-221">Este modelo de aplicativo é uma extensão [de](~/messaging-extensions/what-are-messaging-extensions.md) mensagens que permite que seus usuários usem adesivos personalizados e GIFs em Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="4af47-221">This app template is a [messaging extension](~/messaging-extensions/what-are-messaging-extensions.md) that enables your users to use custom stickers and GIFs within Microsoft Teams.</span></span> <span data-ttu-id="4af47-222">Este modelo oferece uma experiência de configuração baseada na Web fácil, onde qualquer pessoa com acesso à configuração pode carregar os GIFs, adesivos e imagens que eles querem que seus usuários tenham, permitindo que toda a sua equipe use qualquer conjunto de adesivos que você escolher.</span><span class="sxs-lookup"><span data-stu-id="4af47-222">This template provides an easy web-based configuration experience where anyone with configuration access can upload the GIFs, stickers, and images they want their users to have, allowing your entire team to use any set of stickers you choose.</span></span>

<span data-ttu-id="4af47-223">Este aplicativo também permite fácil compartilhamento de imagens, GIFs, adesivos entre equipes sem precisar de acesso a sites SharePoint ou canais individuais como mecanismos de armazenamento e compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="4af47-223">This app also enables easy sharing of images, GIFs, stickers across teams without needing access to SharePoint sites or individual channels as storage and sharing mechanisms.</span></span> <span data-ttu-id="4af47-224">Por exemplo, as equipes de produtos podem compartilhar facilmente imagens de produto e GIFs para equipes de mídia social, marketing e vendas programaticamente.</span><span class="sxs-lookup"><span data-stu-id="4af47-224">For example, product teams can easily share product images and GIFs to social media, marketing, and sales teams programmatically.</span></span> <span data-ttu-id="4af47-225">Também é possível estender esse aplicativo disparando um fluxo de notificação para equipes ou indivíduos específicos quando novas imagens e GIFs são disponibilizados.</span><span class="sxs-lookup"><span data-stu-id="4af47-225">One can also extend this app by triggering a notification flow to specific teams or individuals when new images, and GIFs are made available.</span></span>

[<span data-ttu-id="4af47-226">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-226">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-stickers-app)

![Aplicativo Stickers](../assets/images/stickers.png)

## <a name="employee-ideas"></a><span data-ttu-id="4af47-228">Ideias de funcionários</span><span class="sxs-lookup"><span data-stu-id="4af47-228">Employee Ideas</span></span>

<span data-ttu-id="4af47-229">O aplicativo Ideias de Funcionários é a versão do PowerApps do modelo de aplicativo Great Ideas baseado no Azure.</span><span class="sxs-lookup"><span data-stu-id="4af47-229">The Employee Ideas app is the PowerApps version of the Azure based Great Ideas app template.</span></span> <span data-ttu-id="4af47-230">O aplicativo permite que os usuários Teams configurar e configurar uma campanha de ideias.</span><span class="sxs-lookup"><span data-stu-id="4af47-230">The app enables the Teams users to set up and configure an idea campaign.</span></span> <span data-ttu-id="4af47-231">Uma campanha de ideias é uma categoria para agrupar ideias em torno de temas comuns.</span><span class="sxs-lookup"><span data-stu-id="4af47-231">An idea campaign is a category for grouping ideas around common themes.</span></span>

<span data-ttu-id="4af47-232">Teams usuários também podem executar as seguintes atividades:</span><span class="sxs-lookup"><span data-stu-id="4af47-232">Teams users can also perform the following activities:</span></span>

* <span data-ttu-id="4af47-233">Configure um formulário de envio padrão que os funcionários devem enviar para cada ideia.</span><span class="sxs-lookup"><span data-stu-id="4af47-233">Configure a standard submission form that employees must submit for each idea.</span></span> 
* <span data-ttu-id="4af47-234">Revise e gerencie as ideias e a lista de campanhas.</span><span class="sxs-lookup"><span data-stu-id="4af47-234">Review and manage the ideas and list of campaigns.</span></span>
* <span data-ttu-id="4af47-235">Modificar e excluir campanhas.</span><span class="sxs-lookup"><span data-stu-id="4af47-235">Modify and delete campaigns.</span></span>
* <span data-ttu-id="4af47-236">Revise os conselhos de líderes de ideias.</span><span class="sxs-lookup"><span data-stu-id="4af47-236">Review leader boards of ideas.</span></span>
* <span data-ttu-id="4af47-237">Vote e compartilhe ideias priorizadas.</span><span class="sxs-lookup"><span data-stu-id="4af47-237">Vote for and share prioritized ideas.</span></span>
* <span data-ttu-id="4af47-238">Enviar ideias para uma campanha.</span><span class="sxs-lookup"><span data-stu-id="4af47-238">Submit ideas for a campaign.</span></span>
* <span data-ttu-id="4af47-239">Exibir a ideia de outro membro da equipe.</span><span class="sxs-lookup"><span data-stu-id="4af47-239">View other team member's idea.</span></span>
* <span data-ttu-id="4af47-240">Vote nas ideias mais curtidas.</span><span class="sxs-lookup"><span data-stu-id="4af47-240">Vote on most liked ideas.</span></span>
* <span data-ttu-id="4af47-241">Revise o desempenho de suas ideias em comparação com outras em uma campanha.</span><span class="sxs-lookup"><span data-stu-id="4af47-241">Review the performance of their ideas compared with others within a campaign.</span></span>

[<span data-ttu-id="4af47-242">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-242">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-employeeideas)

![Gerenciar exibição de campanha](../assets/images/employee-ideas-manage-campaigns.png) 

## <a name="e-prescriptions"></a><span data-ttu-id="4af47-244">E-Prescriptions</span><span class="sxs-lookup"><span data-stu-id="4af47-244">E-Prescriptions</span></span> 

<span data-ttu-id="4af47-245">O E-Prescriptions [](/powerapps/maker/canvas-apps/embed-teams-app) é um aplicativo baseado em Power Apps que aprimora a telemedicina e o cuidado virtual automatizando o processo de emissão de prescrições e para os pacientes.</span><span class="sxs-lookup"><span data-stu-id="4af47-245">E-Prescriptions is a [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) based app that enhances telemedicine and virtual care by automating the process of issuing e-prescriptions to patients.</span></span> <span data-ttu-id="4af47-246">Os profissionais médicos podem revisar rapidamente os compromissos, gerar prescrições e enviar emails com anexos de prescrição e para os pacientes diretamente dentro da plataforma Teams.</span><span class="sxs-lookup"><span data-stu-id="4af47-246">Medical professionals can quickly review appointments, generate e-prescriptions, and send emails with e-prescription attachments to patients directly within the Teams platform.</span></span>

[<span data-ttu-id="4af47-247">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-247">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-eprescription) 

:::row:::
:::column span="2":::
    ![Captura de tela do aplicativo E-Prescriptions.](../assets/images/e-prescriptions-app-template.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Captura de tela do aplicativo E-Prescriptions.](../assets/images/e-prescriptions-app-template-admin.png)
:::column-end:::
:::row-end:::

## <a name="employee-training"></a><span data-ttu-id="4af47-252">Treinamento de funcionários</span><span class="sxs-lookup"><span data-stu-id="4af47-252">Employee Training</span></span> 

<span data-ttu-id="4af47-253">Treinamento de funcionários é um Microsoft Teams que permite que os organizadores publiquem, acompanhem e promovam facilmente eventos de aprendizado e treinamento para sua organização.</span><span class="sxs-lookup"><span data-stu-id="4af47-253">Employee training is a Microsoft Teams app that enables organizers to easily publish, track, and promote learning and training events for your organization.</span></span>  <span data-ttu-id="4af47-254">Com o aplicativo, os planejadores de eventos podem enviar lembretes e notificações para os registrantes de eventos e os funcionários podem indicar interesse nos próximos eventos, manter-se atualizados sobre eventos atuais e compartilhar detalhes do evento com colegas por meio da extensão de mensagens Teams.</span><span class="sxs-lookup"><span data-stu-id="4af47-254">With the app, event planners can send reminders and notifications to event registrants and employees can indicate interest in upcoming events, stay updated on current events, and share event details with colleagues through the Teams messaging extension.</span></span>

[<span data-ttu-id="4af47-255">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-255">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-employeetraining)

:::row:::
:::column span="2":::
    <span data-ttu-id="4af47-256">**Exibir eventos de treinamento de funcionários** ![ Imagem da guia treinamento de funcionários](../assets/images/employee-training-discover-tab.png)</span><span class="sxs-lookup"><span data-stu-id="4af47-256">**View employee training events** ![Employee training tab image](../assets/images/employee-training-discover-tab.png)</span></span>  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    <span data-ttu-id="4af47-257">**Criar evento de treinamento de funcionários** ![ Treinamento de funcionários criar formulário de evento](../assets/images/employee-training-create-event.jpg)</span><span class="sxs-lookup"><span data-stu-id="4af47-257">**Create employee training event** ![Employee training create event form](../assets/images/employee-training-create-event.jpg)</span></span>
:::column-end:::
:::row-end:::

## <a name="expert-finder"></a><span data-ttu-id="4af47-258">Expert Finder</span><span class="sxs-lookup"><span data-stu-id="4af47-258">Expert Finder</span></span>

<span data-ttu-id="4af47-259">O Expert Finder é [um Microsoft Teams que](../bots/what-are-bots.md) identifica membros específicos da organização com base em suas habilidades, interesses e atributos de educação.</span><span class="sxs-lookup"><span data-stu-id="4af47-259">Expert Finder is a [Microsoft Teams bot](../bots/what-are-bots.md) that identifies specific organization members based on their skills, interests, and education attributes.</span></span> <span data-ttu-id="4af47-260">Os membros encontram especialistas em uma organização que combinam com uma pesquisa de palavra-chave de Azure Active Directory perfis de usuário.</span><span class="sxs-lookup"><span data-stu-id="4af47-260">Members find experts within an organization that match a keyword search of Azure Active Directory user profiles.</span></span>

[<span data-ttu-id="4af47-261">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-261">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-expertfinder)

![Demonstração de resultados da pesquisa do Expert Finder](../assets/images/expert-finder.png)

## <a name="faq-plus"></a><span data-ttu-id="4af47-263">Perguntas Frequentes Plus</span><span class="sxs-lookup"><span data-stu-id="4af47-263">FAQ Plus</span></span>

<span data-ttu-id="4af47-264">Conversational Q&Um bots é uma maneira fácil de fornecer respostas para perguntas frequentes pelos usuários.</span><span class="sxs-lookup"><span data-stu-id="4af47-264">Conversational Q&A bots are an easy way to provide answers to frequently asked questions by users.</span></span> <span data-ttu-id="4af47-265">Porém, a maioria dos bots não consegue se envolver com os usuários de maneira significativa porque não há nenhum humano no loop quando o bot falha.</span><span class="sxs-lookup"><span data-stu-id="4af47-265">But, most bots fail to engage with users in meaningful way because there is no human in the loop when the bot fails.</span></span> <span data-ttu-id="4af47-266">O bot de perguntas frequentes é&um bot que traz um humano no loop quando não consegue ajudar.</span><span class="sxs-lookup"><span data-stu-id="4af47-266">FAQ bot is a friendly Q&A bot that brings a human in the loop when it is unable to help.</span></span> <span data-ttu-id="4af47-267">É possível fazer uma pergunta ao bot e o bot responde com uma resposta se ele estiver contido na base de dados de conhecimento.</span><span class="sxs-lookup"><span data-stu-id="4af47-267">One can ask the bot a question and the bot responds with an answer if it is contained in the knowledge base.</span></span> <span data-ttu-id="4af47-268">Caso não seja, o bot permite que o usuário envie uma consulta que, em seguida, é postada para uma equipe pré-configurada de especialistas que ajudam a fornecer suporte atuando sobre as notificações de dentro da própria equipe.</span><span class="sxs-lookup"><span data-stu-id="4af47-268">If not, the bot allows the user to submit a query which then gets posted to a pre-configured team of experts who help to provide support by acting upon the notifications from within the team itself.</span></span>

> [!NOTE]
> <span data-ttu-id="4af47-269">A versão mais recente do **FaQ Plus** oferece suporte a resoluções de Q&A aprimoradas, permitindo que uma equipe de especialistas conclua o seguinte:</span><span class="sxs-lookup"><span data-stu-id="4af47-269">The latest release of **FAQ Plus** supports improved Q&A resolutions by enabling a team of experts to complete the following:</span></span>
>
> <span data-ttu-id="4af47-270">&#x2714; Adicionar novo Q&Diretamente à base de dados de conhecimento usando extensões de mensagem.</span><span class="sxs-lookup"><span data-stu-id="4af47-270">&#x2714; Add new Q&As directly to the knowledge base using message extensions.</span></span>
>
> <span data-ttu-id="4af47-271">&#x2714; Editar e excluir P&Pares A adicionados por um bot.</span><span class="sxs-lookup"><span data-stu-id="4af47-271">&#x2714; Edit and delete Q&A pairs added by a bot.</span></span>
>
> <span data-ttu-id="4af47-272">&#x2714; o histórico de revisão de Q&As.</span><span class="sxs-lookup"><span data-stu-id="4af47-272">&#x2714; Track the revision history of Q&As.</span></span>
>
> <span data-ttu-id="4af47-273">&#x2714; Configurar uma resposta com detalhes adicionais para exibição como um [Cartão Adaptável.](../task-modules-and-cards/cards/cards-reference.md#adaptive-card)</span><span class="sxs-lookup"><span data-stu-id="4af47-273">&#x2714; Configure an answer with additional details to display as an [Adaptive Card](../task-modules-and-cards/cards/cards-reference.md#adaptive-card).</span></span>
>
[<span data-ttu-id="4af47-274">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-274">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-faqplusv2)

![FAQ Plus gif](../assets/images/FAQPlusEndUser.gif)

## <a name="get-support-app"></a><span data-ttu-id="4af47-276">Obter aplicativo de suporte</span><span class="sxs-lookup"><span data-stu-id="4af47-276">Get Support App</span></span>

<span data-ttu-id="4af47-277">O aplicativo Obter Suporte é usado por organizações que estão usando Microsoft Teams, para permitir que qualquer conjunto de usuários solicite assistência de supervisores.</span><span class="sxs-lookup"><span data-stu-id="4af47-277">The Get Support app is used by organizations that are using Microsoft Teams, to enable any set of users to request assistance from supervisors.</span></span> <span data-ttu-id="4af47-278">Este aplicativo inclui os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="4af47-278">This app includes the following features:</span></span>
* <span data-ttu-id="4af47-279">Solicitando assistência em diferentes categorias de um Power App.</span><span class="sxs-lookup"><span data-stu-id="4af47-279">Requesting assistance on different categories from a Power App.</span></span>
* <span data-ttu-id="4af47-280">Notificações enviadas aos solicitadores informando quem foi atribuído.</span><span class="sxs-lookup"><span data-stu-id="4af47-280">Notifications sent to requestors informing them of who hare assigned.</span></span>
* <span data-ttu-id="4af47-281">Notificações enviadas a supervisores atribuídos informando quem precisa de assistência.</span><span class="sxs-lookup"><span data-stu-id="4af47-281">Notifications sent to assigned supervisors informing them of who needs assistance.</span></span> 
* <span data-ttu-id="4af47-282">Analisando escalonamentos e padrões em SharePoint e PowerBI.S.</span><span class="sxs-lookup"><span data-stu-id="4af47-282">Analyzing escalations and patterns in SharePoint and PowerBI.S.</span></span>

[<span data-ttu-id="4af47-283">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-283">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-app-get-support/)

![Obter Gif de Suporte](../assets/images/get-support.gif)

## <a name="goal-tracker"></a><span data-ttu-id="4af47-285">Rastreador de Meta</span><span class="sxs-lookup"><span data-stu-id="4af47-285">Goal Tracker</span></span>

<span data-ttu-id="4af47-286">O aplicativo Rastreador de Metas é uma solução abrangente para sua organização para dar suporte ao estabelecimento de metas, à observação do progresso e ao reconhecimento do sucesso dentro Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="4af47-286">The Goal Tracker app is a comprehensive solution for your organization to support establishing goals, observing progress, and acknowledging success within Microsoft Teams.</span></span> <span data-ttu-id="4af47-287">O aplicativo permite aos usuários definir, rastrear e atualizar objetivos em um nível profissional, pessoal e de equipe.</span><span class="sxs-lookup"><span data-stu-id="4af47-287">The app enables users to set, track, and update objectives on a professional, personal, and team level.</span></span> <span data-ttu-id="4af47-288">Os membros da equipe também recebem lembretes e atualizações de status em tempo há tempo para permanecerem focados e permanecerem no controle.</span><span class="sxs-lookup"><span data-stu-id="4af47-288">Team members also receive timely reminders and status updates to remain focused and stay on track.</span></span>

[<span data-ttu-id="4af47-289">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-289">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-app-goaltracker)

:::row:::
  :::column span="2":::
    ![Definir metas](../assets/images/goal-tracker-set-goals-view.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Exibir metas definidas](../assets/images/goal-tracker-your-goals-view.png)
:::column-end:::
:::row-end:::

## <a name="great-ideas"></a><span data-ttu-id="4af47-292">Ótimas ideias</span><span class="sxs-lookup"><span data-stu-id="4af47-292">Great Ideas</span></span>

<span data-ttu-id="4af47-293">O aplicativo Grandes Ideias dá suporte e capacita a inovação e a criatividade em sua organização.</span><span class="sxs-lookup"><span data-stu-id="4af47-293">The Great Ideas app supports and empowers innovation and creativity within your organization.</span></span> <span data-ttu-id="4af47-294">O aplicativo permite que seus funcionários compartilhem ideias com colegas e liderança, descubram novos envios, destaquem as contribuições para consideração por pares e votem nas melhores propostas dentro Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="4af47-294">The app enables your employees to share ideas with colleagues and leadership, discover new submissions, spotlight contributions for peer consideration, and cast their vote for the best proposals within Microsoft Teams.</span></span>

[<span data-ttu-id="4af47-295">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-295">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-greatideas)

:::row:::
  :::column span="2":::
    ![Exibir ideias enviadas](../assets/images/great-ideas-all-view.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Exibir ideias](../assets/images/great-ideas-digest-view.png)
:::column-end:::
:::row-end:::

## <a name="group-activities"></a><span data-ttu-id="4af47-298">Atividades de grupo</span><span class="sxs-lookup"><span data-stu-id="4af47-298">Group Activities</span></span>

<span data-ttu-id="4af47-299">Atividades de grupo é um Microsoft Teams que facilita que os proprietários da equipe criem rapidamente grupos de atividades e gerenciem fluxos de trabalho de colaboração no contexto de Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="4af47-299">Group Activities is a Microsoft Teams app that makes it easy for team owners to quickly create activity groups and manage collaboration workflows within the context of Microsoft Teams.</span></span> <span data-ttu-id="4af47-300">Os autores de atividades estão habilitados para criar atividades, distribuir aleatoriamente membros da equipe em grupos e, opcionalmente, fazer com que o bot envie lembretes até que as atividades sejam concluídas.</span><span class="sxs-lookup"><span data-stu-id="4af47-300">Activity authors are enabled to create activities, randomly distribute team members in groups, and optionally have the bot send reminders until activities are complete.</span></span>

[<span data-ttu-id="4af47-301">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-301">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-groupactivities)

:::row:::
  :::column span="2":::
    ![Lista de atividades de grupo no Teams](../assets/images/group-activities-1.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Mensagem de notificação de atividade de grupo em um canal](../assets/images/group-activities-2.png)
:::column-end:::
:::row-end:::

## <a name="group-connect-9734"></a><span data-ttu-id="4af47-304">Grupo Conexão &#9734;</span><span class="sxs-lookup"><span data-stu-id="4af47-304">Group Connect &#9734;</span></span>

<span data-ttu-id="4af47-305">Grupo Conexão é um aplicativo Microsoft Teams que ajuda os membros da organização a descobrir grupos de funcionários e a encontrar informações relevantes para grupos de funcionários.</span><span class="sxs-lookup"><span data-stu-id="4af47-305">Group Connect is a Microsoft Teams app that helps organization members discover employee groups and find information relevant to employee groups.</span></span> <span data-ttu-id="4af47-306">O aplicativo vem integrado com recursos avançados para os líderes da organização se comunicarem com seus funcionários em relação a grupos, eventos e recursos.</span><span class="sxs-lookup"><span data-stu-id="4af47-306">The app comes built-in with rich capabilities for organization leaders to communicate with their employees regarding groups, events, and resources.</span></span> <span data-ttu-id="4af47-307">O aplicativo Conexão grupo também corresponde aos membros do grupo uns com os outros na frequência desejada para incentivar a rede e a coesão dentro de um grupo.</span><span class="sxs-lookup"><span data-stu-id="4af47-307">The Group Connect app also matches group members with each other at their desired frequency to encourage networking and cohesion within a group.</span></span> <span data-ttu-id="4af47-308">Para obter mais informações sobre como você pode aproveitar o aplicativo Conexão group para ajudar os grupos de funcionários a promover em sua organização, consulte o aplicativo no GitHub.</span><span class="sxs-lookup"><span data-stu-id="4af47-308">For more information on how you can leverage the Group Connect app to help employee groups foster within your organization, see the app on GitHub.</span></span>

[<span data-ttu-id="4af47-309">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-309">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-groupconnect)

![Descobrir grupos de&I](https://github.com/OfficeDev/microsoft-teams-apps-diversityandinclusion/wiki/Images/temp_group_connect_landing.png)

## <a name="grow-your-skills"></a><span data-ttu-id="4af47-311">Aumentar suas habilidades</span><span class="sxs-lookup"><span data-stu-id="4af47-311">Grow Your Skills</span></span>

<span data-ttu-id="4af47-312">O aplicativo Crescer Suas Habilidades dá suporte ao crescimento e ao desenvolvimento profissional, permitindo que os funcionários contribuam com projetos complementares para sua organização e, ao mesmo tempo, aprendam novas habilidades.</span><span class="sxs-lookup"><span data-stu-id="4af47-312">The Grow Your Skills app supports professional growth and development by enabling employees to contribute to supplemental projects for your organization while simultaneously learning new skills.</span></span> <span data-ttu-id="4af47-313">Os funcionários podem usar o aplicativo para localizar oportunidades que atendem aos seus interesses, desfrutar de colaboração significativa com pares e adquirir novos níveis de experiência e recursos, tudo dentro do ambiente Teams.</span><span class="sxs-lookup"><span data-stu-id="4af47-313">Employees can use the app to locate opportunities that meet their interests, enjoy meaningful collaboration with peers, and acquire new levels of expertise and capabilities, all within the Teams environment.</span></span>

[<span data-ttu-id="4af47-314">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-314">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-growyourskills)

:::row:::
  :::column span="2":::
    ![Exibição de projetos disponíveis](../assets/images/grow-your-skills-all-projects-view.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Exibição de habilidades adquiridas do visualizador](../assets/images/grow-your-skills-acquired-skills-view.png)
:::column-end:::
:::row-end:::

## <a name="hr-support"></a><span data-ttu-id="4af47-317">Suporte de RH</span><span class="sxs-lookup"><span data-stu-id="4af47-317">HR Support</span></span>

<span data-ttu-id="4af47-318">O bot de Suporte de RH é um Q&um bot que traz um profissional de suporte ou especialista da equipe de RH no loop quando não consegue ajudar.</span><span class="sxs-lookup"><span data-stu-id="4af47-318">HR Support bot is a friendly Q&A bot that brings a support professional or expert from the HR team in the loop when it is unable to help.</span></span> <span data-ttu-id="4af47-319">É possível fazer uma pergunta ao bot e o bot responde com uma resposta se ele estiver contido na base de dados de conhecimento.</span><span class="sxs-lookup"><span data-stu-id="4af47-319">One can ask the bot a question and the bot responds with an answer if it is contained in the knowledge base.</span></span> <span data-ttu-id="4af47-320">Caso não seja, o bot permite que o usuário envie uma consulta que, em seguida, é postada em uma equipe pré-configurada de especialistas que ajudam a fornecer suporte agindo sobre as notificações de dentro de sua própria equipe.</span><span class="sxs-lookup"><span data-stu-id="4af47-320">If not, the bot allows the user to submit a query which then gets posted in a pre-configured team of experts who are help to provide support by acting upon the notifications from within their team itself.</span></span> <span data-ttu-id="4af47-321">Além disso, o bot sugere links para políticas ou perguntas recomendadas de RH pesquisando marcas pré-configuradas na pergunta.</span><span class="sxs-lookup"><span data-stu-id="4af47-321">Additionally, the bot suggests links to recommended HR policies or questions by searching for pre-configured tags in the question.</span></span> <span data-ttu-id="4af47-322">Esses blocos são encontrados na guia associada como uma referência rápida.</span><span class="sxs-lookup"><span data-stu-id="4af47-322">These tiles are found in the associated tab as a quick reference.</span></span> <span data-ttu-id="4af47-323">O Suporte de RH funciona bem para Q&A e para fornecer suporte rápido ao iniciar novos projetos ou iniciativas na organização.</span><span class="sxs-lookup"><span data-stu-id="4af47-323">HR Support works well for light weight Q&A and to provide quick support when launching new projects or initiatives in the organization.</span></span>

[<span data-ttu-id="4af47-324">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-324">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-hrsupport-app)

![Suporte de RH](../assets/images/expert-user.png)

## <a name="icebreaker"></a><span data-ttu-id="4af47-326">Frases de apresentação</span><span class="sxs-lookup"><span data-stu-id="4af47-326">Icebreaker</span></span>

<span data-ttu-id="4af47-327">Icebreaker é um [Microsoft Teams que](../bots/what-are-bots.md) ajuda sua equipe a se aproximar emparelhando dois membros aleatórios da equipe a cada semana para se reunir.</span><span class="sxs-lookup"><span data-stu-id="4af47-327">Icebreaker is a [Microsoft Teams bot](../bots/what-are-bots.md) that helps your team get closer by pairing two random team members up every week to meet.</span></span> <span data-ttu-id="4af47-328">O bot facilita o agendamento sugerindo automaticamente tempos livres que funcionam para ambos os membros.</span><span class="sxs-lookup"><span data-stu-id="4af47-328">The bot makes scheduling easy by automatically suggesting free times that work for both members.</span></span> <span data-ttu-id="4af47-329">Fortaleça conexões pessoais e crie uma comunidade estreita com esse aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4af47-329">Strengthen personal connections and build a tightly knit community with this app.</span></span>

<span data-ttu-id="4af47-330">Além de incentivar conexões pessoais em toda a sua equipe, o aplicativo Icebreaker pode ajudar a criar comunidades baseadas em interesse em sua organização.</span><span class="sxs-lookup"><span data-stu-id="4af47-330">In addition to encouraging personal connections across your entire team, the Icebreaker app can help cultivate interest-based communities within your organization.</span></span> <span data-ttu-id="4af47-331">Por exemplo, você pode usar esse aplicativo para um grupo de DevOps de interesse para ajudar a propagar ideias e práticas recomendadas de forma orgânica em sua organização.</span><span class="sxs-lookup"><span data-stu-id="4af47-331">For example, you can use this app for a DevOps interest group to help ideas and best practices organically spread across your organization.</span></span>

[<span data-ttu-id="4af47-332">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-332">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-icebreaker-app)

![Aplicativo quebra-gelo](../assets/images/icebreaker.png)

## <a name="incentives"></a><span data-ttu-id="4af47-334">Incentivos</span><span class="sxs-lookup"><span data-stu-id="4af47-334">Incentives</span></span>

<span data-ttu-id="4af47-335">Incentivos é um [modelo Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) que gerencia e rastreia a participação de funcionários incentivados em atividades designadas, como treinamentos e iniciativas de gerenciamento de alterações.</span><span class="sxs-lookup"><span data-stu-id="4af47-335">Incentives is a [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) template that manages and tracks incentivized employee participation in designated activities, such as trainings and change management initiatives.</span></span> <span data-ttu-id="4af47-336">Os administradores usam o aplicativo para estabelecer atividades designadas, atribuir pontos para conclusão e especificar níveis de pontos de qualificação necessários para recompensas.</span><span class="sxs-lookup"><span data-stu-id="4af47-336">Admins use the app to establish designated activities, assign points for completion, and specify required eligibility point levels for rewards.</span></span> <span data-ttu-id="4af47-337">Os funcionários usam o aplicativo para exibir seus pontos acumulados e, ao chegarem à qualificação, solicitam e solicitam recompensas resgatáveis.</span><span class="sxs-lookup"><span data-stu-id="4af47-337">Employees use the app to view their accumulated points and, upon reaching eligibility, request and claim redeemable rewards.</span></span>

[<span data-ttu-id="4af47-338">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-338">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-incentives)

![Demonstração de aplicativo de incentivos](../assets/images/incentives-app.png)

## <a name="incident-reporter"></a><span data-ttu-id="4af47-340">Incident Reporter</span><span class="sxs-lookup"><span data-stu-id="4af47-340">Incident Reporter</span></span>

<span data-ttu-id="4af47-341">Incident Reporter é um [Microsoft Teams que](../bots/what-are-bots.md) otimiza o gerenciamento de incidentes em sua organização.</span><span class="sxs-lookup"><span data-stu-id="4af47-341">Incident Reporter is a [Microsoft Teams bot](../bots/what-are-bots.md)  that optimizes the management of incidents in your organization.</span></span> <span data-ttu-id="4af47-342">O bot facilita a coleta automatizada de dados de incidentes, relatórios de incidentes personalizados, notificações relevantes de participantes e controle de incidentes de ponta a ponta.</span><span class="sxs-lookup"><span data-stu-id="4af47-342">The bot facilitates automated incident data collection, customized incident reports, relevant stakeholder notifications, and end-to-end incident tracking.</span></span>

[<span data-ttu-id="4af47-343">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-343">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-incidentreport)

:::row:::
  :::column span="2":::
    ![Exibição de escopo do grupo de repórter de incidentes](../assets/images/incident-reporter-02.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Exibição de escopo pessoal do repórter de incidentes](../assets/images/incident-reporter-01.jpg)
:::column-end:::
:::row-end:::

## <a name="inspection"></a><span data-ttu-id="4af47-346">Inspeção</span><span class="sxs-lookup"><span data-stu-id="4af47-346">Inspection</span></span> 

 <span data-ttu-id="4af47-347">A inspeção é um Microsoft Teams que permite que os funcionários de linha de frente inspecionem qualquer coisa de locais para ativos e equipamentos.</span><span class="sxs-lookup"><span data-stu-id="4af47-347">Inspection is a Microsoft Teams app that enables front line workers to inspect anything from  locations to assets and equipments.</span></span> <span data-ttu-id="4af47-348">Por exemplo, uma loja de varejo, uma fábrica de manufatura ou veículos e máquinas.</span><span class="sxs-lookup"><span data-stu-id="4af47-348">For example, a retail store, manufacturing plant, or vehicles and machines.</span></span> <span data-ttu-id="4af47-349">Há dois aplicativos nesta solução, cada um destinado a tipos diferentes de usuários.</span><span class="sxs-lookup"><span data-stu-id="4af47-349">There are two apps in this solution, each intended for different types of users.</span></span>

<span data-ttu-id="4af47-350">O aplicativo capacita os funcionários de linha de frente a inspecionar um ativo ou área, gerenciar a qualidade de produtos e serviços ou manter a segurança no local de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4af47-350">The app empowers the front line workers to inspect an asset or area, to manage quality of products and services, or maintain safety at workplace.</span></span> <span data-ttu-id="4af47-351">Facilita a comunicação entre membros da equipe para resolver problemas encontrados durante a inspeção.</span><span class="sxs-lookup"><span data-stu-id="4af47-351">It facilitates communication between team members to address issues found during inspection.</span></span> <span data-ttu-id="4af47-352">O aplicativo fornece relatórios simples para os gerentes agilizarem a resolução de problemas e realçam as tendências.</span><span class="sxs-lookup"><span data-stu-id="4af47-352">The app provides simple reports for managers to expedite issue resolution and highlight trends.</span></span>

[<span data-ttu-id="4af47-353">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-353">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-inspection)

 ![Visão geral da inspeção](../assets/images/inspection-app.png)  


## <a name="issue-reporting"></a><span data-ttu-id="4af47-355">Relatório de Problemas</span><span class="sxs-lookup"><span data-stu-id="4af47-355">Issue Reporting</span></span>

<span data-ttu-id="4af47-356">O aplicativo Relatório de Problemas capacita os funcionários e gerentes a levantar e gerenciar problemas.</span><span class="sxs-lookup"><span data-stu-id="4af47-356">The Issue Reporting app empowers the employees and managers to raise and manage issues.</span></span> <span data-ttu-id="4af47-357">Ele consiste em dois aplicativos, Emitir aplicativo de relatório para problemas de relatórios e gerenciar problemas do aplicativo para gerenciar problemas.</span><span class="sxs-lookup"><span data-stu-id="4af47-357">It consists of two apps, Issue reporting app for reporting issues and Manage Issues app for managing issues.</span></span>

<span data-ttu-id="4af47-358">Os gerentes de equipe usam o aplicativo Gerenciar Problemas para configurar a experiência do aplicativo, incluindo o canal no qual Microsoft Teams mensagens e tarefas do Planner são criadas pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4af47-358">The team managers use the Manage Issues app to configure the app experience, including the channel in which Microsoft Teams messages and Planner tasks are created by the app.</span></span> <span data-ttu-id="4af47-359">Os gerentes também usam o aplicativo para criar formulários de modelo para coletar detalhes quando um usuário relata um problema.</span><span class="sxs-lookup"><span data-stu-id="4af47-359">Managers also use the app to create template forms to collect details when a user reports an issue.</span></span> <span data-ttu-id="4af47-360">Por exemplo, revise, edite ou exclua formulários de modelo de problema.</span><span class="sxs-lookup"><span data-stu-id="4af47-360">For example, review, edit, or delete issue template forms.</span></span> <span data-ttu-id="4af47-361">O aplicativo também é usado para revisar problemas de equipe, relatar o histórico de problemas e gerenciar com eficiência a resolução de problemas.</span><span class="sxs-lookup"><span data-stu-id="4af47-361">The app is also used to review team issues, report on issue history, and efficiently manage issue resolution.</span></span>

<span data-ttu-id="4af47-362">Os funcionários usam o aplicativo Demissão de relatórios para registrar problemas e detalhes necessários para resolvê-los.</span><span class="sxs-lookup"><span data-stu-id="4af47-362">The employees use the Issue reporting app to log issues and details required to resolve them.</span></span> <span data-ttu-id="4af47-363">O aplicativo também é usado para modificar e resolver problemas existentes e obter uma visão de alto nível de problemas individuais ou de equipe.</span><span class="sxs-lookup"><span data-stu-id="4af47-363">The app is also used to modify and resolve existing issues and get a high-level view of individual or team issues.</span></span>

[<span data-ttu-id="4af47-364">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-364">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-issuereporting)

![Emitir exibição de equipe de relatórios](../assets/images/issue-reporting-team-view.png)  

## <a name="new-employee-onboarding"></a><span data-ttu-id="4af47-366">Integração de novos funcionários</span><span class="sxs-lookup"><span data-stu-id="4af47-366">New Employee Onboarding</span></span> 

<span data-ttu-id="4af47-367">A Integração de Novos Funcionários é uma solução integrada Microsoft Teams e SharePoint Nova Integração de Funcionários que permite [que sua](https://lookbook.microsoft.com/details/75e60a32-9849-4ed4-b83e-b2b08983ad19) organização forneça uma experiência de integração consistente e de alta qualidade para os funcionários em sua jornada de nova contratação.</span><span class="sxs-lookup"><span data-stu-id="4af47-367">New Employee Onboarding is an integrated Microsoft Teams and [SharePoint New Employee Onboarding Solution](https://lookbook.microsoft.com/details/75e60a32-9849-4ed4-b83e-b2b08983ad19) that enables your organization to provide a consistent, high-quality onboarding experience for employees on their new-hire journey.</span></span> <span data-ttu-id="4af47-368">O aplicativo é usado por equipes de recursos humanos e gerentes de contratação para fornecer informações relevantes em todo o processo de orientação e indução e por novos contratados para compartilhar comentários, fornecer apresentações e concluir tarefas de integração.</span><span class="sxs-lookup"><span data-stu-id="4af47-368">The app is used by human resource teams and hiring managers to provide relevant information throughout the orientation and induction process and by new hires to share feedback, provide introductions, and complete onboarding tasks.</span></span>

[<span data-ttu-id="4af47-369">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-369">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-newemployeeonboarding)

:::row:::
  :::column span="2":::
    <span data-ttu-id="4af47-370">**Novo cartão de boas-vindas do funcionário** ![ Imagem do novo cartão de boas-vindas do funcionário](../assets/images/new-employee-welcome-card.png)</span><span class="sxs-lookup"><span data-stu-id="4af47-370">**New employee welcome card** ![Image of new employee welcome card](../assets/images/new-employee-welcome-card.png)</span></span>
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    <span data-ttu-id="4af47-371">**Nova lista de verificação de funcionários** ![ Imagem da nova lista de verificação de funcionários](../assets/images/new-employee-checklist.png)</span><span class="sxs-lookup"><span data-stu-id="4af47-371">**New employee checklist** ![Image of new employee checklist](../assets/images/new-employee-checklist.png)</span></span>  
:::column-end:::
:::row-end:::

## <a name="open-badges"></a><span data-ttu-id="4af47-372">Selos abertos</span><span class="sxs-lookup"><span data-stu-id="4af47-372">Open Badges</span></span>

<span data-ttu-id="4af47-373">O Open Badges é um Microsoft Teams que permite que as pessoas ganhem selos de credencial de aprendizagem digital no contexto Teams e compartilhem-os em todos os lugares.</span><span class="sxs-lookup"><span data-stu-id="4af47-373">Open Badges is a Microsoft Teams app that enables individuals to earn digital learning credential badges within the Teams context and share them everywhere.</span></span> <span data-ttu-id="4af47-374">Usando recursos da autoridade de emissão de selo digital de terceiros, [o Badgr](https://badgr.org/), os selos concedidos são registrados no perfil Badgr de um destinatário e disponíveis para criar e compartilhar uma imagem rica das jornadas de aprendizado de vida útil.</span><span class="sxs-lookup"><span data-stu-id="4af47-374">Using capabilities from the third-party digital badge issuing authority, [Badgr](https://badgr.org/), awarded badges are recorded in a recipient's Badgr profile and available to build and share a rich picture of lifetime learning journeys.</span></span>

[<span data-ttu-id="4af47-375">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-375">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-openbadges)

:::row:::
  :::column span="2":::
    ![Imagem de selos disponíveis](../assets/images/open-badges-1.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Exibição de selos concedidos](../assets/images/open-badges-2.png)
:::column-end:::
:::row-end:::

## <a name="poll"></a><span data-ttu-id="4af47-378">Sondagem</span><span class="sxs-lookup"><span data-stu-id="4af47-378">Poll</span></span> 

<span data-ttu-id="4af47-379">Poll é um aplicativo [](../messaging-extensions/what-are-messaging-extensions.md) de extensão Microsoft Teams mensagens personalizado que permite que você crie e envie votações rapidamente em um chat ou canal para reunir opiniões e preferências de equipe.</span><span class="sxs-lookup"><span data-stu-id="4af47-379">Poll is a custom Microsoft Teams [messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that enables you to quickly create and send polls in a chat or a channel to gather team opinions and preferences.</span></span> <span data-ttu-id="4af47-380">O aplicativo tem suporte em todos os clientes da plataforma Teams, como desktop, navegador, iOS e Android, e está pronto para implantação como parte da sua assinatura Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="4af47-380">The app is supported across all Teams platform clients, such as desktop, browser, iOS, and Android and is ready for deployment as part of your Microsoft 365 subscription.</span></span>

[<span data-ttu-id="4af47-381">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-381">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-poll-app)

:::row:::
  :::column span="1":::
    ![Criar sondagem no Teams exibição](../assets/images/poll-app-template-compose-view.gif)  
:::column-end:::
:::row-end:::

## <a name="quick-responses"></a><span data-ttu-id="4af47-383">Respostas rápidas</span><span class="sxs-lookup"><span data-stu-id="4af47-383">Quick Responses</span></span>

<span data-ttu-id="4af47-384">Respostas Rápidas é um Microsoft Teams que oferece uma solução robusta para responder efetivamente às perguntas frequentes dos usuários.</span><span class="sxs-lookup"><span data-stu-id="4af47-384">Quick Responses is a Microsoft Teams app that delivers a robust solution for effectively answering users' commonly asked questions FAQs.</span></span> <span data-ttu-id="4af47-385">Em vez de responder a cada consulta manualmente e continuamente repetindo informações, o aplicativo cria uma biblioteca de respostas para uma experiência interativa do usuário por meio de extensões de Teams [de mensagens.](../messaging-extensions/what-are-messaging-extensions.md)</span><span class="sxs-lookup"><span data-stu-id="4af47-385">Instead of answering each query manually and continuously repeating information, the app builds a library of responses for an interactive user experience through Teams [messaging extensions](../messaging-extensions/what-are-messaging-extensions.md).</span></span>

[<span data-ttu-id="4af47-386">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-386">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-quickresponses)

![Exemplo de exibição de respostas](../assets/images/quick-responses.png)

## <a name="quiz--9734"></a><span data-ttu-id="4af47-388">Teste &#9734;</span><span class="sxs-lookup"><span data-stu-id="4af47-388">Quiz  &#9734;</span></span>

<span data-ttu-id="4af47-389">Quiz é um aplicativo de extensão [Teams](../messaging-extensions/what-are-messaging-extensions.md) mensagens personalizado que permite que você crie um teste em um chat ou um canal para verificação de conhecimento e resultados instantâneos.</span><span class="sxs-lookup"><span data-stu-id="4af47-389">Quiz is a custom [Teams messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that enables you to create a quiz within a chat or a channel for knowledge check and instantaneous results.</span></span> <span data-ttu-id="4af47-390">Você pode usar Quiz para, exames em classe e offline, Verificação de conhecimento dentro da equipe e testes divertidos em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="4af47-390">You can use Quiz for, In-class and offline exams, Knowledge check within team, and for fun quizzes within a team.</span></span> <span data-ttu-id="4af47-391">O aplicativo quiz é suportado em várias plataformas, como clientes Teams desktop, navegador, iOS e Android.</span><span class="sxs-lookup"><span data-stu-id="4af47-391">Quiz app is supported across multiple platforms, such as Teams desktop, browser, iOS, and Android clients.</span></span> <span data-ttu-id="4af47-392">Este aplicativo está pronto para implantação como parte de sua assinatura Microsoft 365 existente.</span><span class="sxs-lookup"><span data-stu-id="4af47-392">This app is ready for deployment as part of your existing Microsoft 365 subscription.</span></span>

[<span data-ttu-id="4af47-393">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-393">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-quiz)

:::row:::
  :::column span="1":::
    ![Criar Quiz no Teams exibição](../assets/images/quiz-app-template-compose-view.gif)  
:::column-end:::
:::row-end:::

## <a name="rapid-assist"></a><span data-ttu-id="4af47-395">Assistência Rápida</span><span class="sxs-lookup"><span data-stu-id="4af47-395">Rapid Assist</span></span>

<span data-ttu-id="4af47-396">O Rapid Assist é um aplicativo baseado na Plataforma [Microsoft Power](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/) que permite que os associados voltados para o cliente se conectem rapidamente com os especialistas para obter respostas rápidas, pesquisar informações, acompanhar solicitações abertas e permitir que os especialistas recebam notificações para receber rapidamente uma chamada para ajudar a responder a perguntas.</span><span class="sxs-lookup"><span data-stu-id="4af47-396">Rapid Assist is a Microsoft [Power Platform](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/) based app that allows customer facing associates to rapidly connect with the experts to get quick answers, search for information, follow up open requests, and allow experts to receive notifications to quickly get on a call to help answer questions.</span></span> <span data-ttu-id="4af47-397">O aplicativo criado usando o Microsoft [Power Apps](/powerapps/powerapps-overview) e [Power Automate](/power-automate/getting-started), integra-se profundamente ao Microsoft Teams para permitir que as organizações conectem facilmente os funcionários de linha de frente com ligações corporativas para resolver consultas de clientes e oferecer uma ótima experiência do cliente.</span><span class="sxs-lookup"><span data-stu-id="4af47-397">The app built using Microsoft [Power Apps](/powerapps/powerapps-overview) and [Power Automate](/power-automate/getting-started), deeply integrates with Microsoft Teams to enable organizations to easily connect frontline workers with corporate liaisons to resolve customer queries and deliver a great customer experience.</span></span> 

[<span data-ttu-id="4af47-398">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-398">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-rapid-assist)

:::row:::
   :::column span="":::
     ![Interface de solicitação de usuário final](../assets/images/EndUserHome.png)
   :::column-end:::
   :::column span="":::
      ![Exibição de solicitação de especialista](../assets/images/ExpertViewRequests.png)
   :::column-end:::
:::row-end:::

## <a name="reflect"></a><span data-ttu-id="4af47-401">Reflect</span><span class="sxs-lookup"><span data-stu-id="4af47-401">Reflect</span></span> 

<span data-ttu-id="4af47-402">Reflect é um aplicativo [](../messaging-extensions/what-are-messaging-extensions.md) de extensão Microsoft Teams mensagens personalizado que fornece um recurso seguro e inclusivo para os membros da equipe compartilharem o estado de seu bem-estar emocional com colegas ou líderes de grupo diretamente no Teams.</span><span class="sxs-lookup"><span data-stu-id="4af47-402">Reflect is a custom Microsoft Teams [messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that provides a safe and inclusive resource for your team members to share the state of their emotional well-being with colleagues or group leaders directly within Teams.</span></span> <span data-ttu-id="4af47-403">O aplicativo está disponível em chats de canal, grupo, reunião e 1:1, e a resposta de check-in é definida como pública, privada para remetente ou totalmente anônima.</span><span class="sxs-lookup"><span data-stu-id="4af47-403">The app is available in channel, group, meeting, and 1:1 chats and the check-in response is set to public, private-to-sender, or fully anonymous.</span></span>

[<span data-ttu-id="4af47-404">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-404">Get it on GitHub</span></span>](https://github.com/OfficeDev/Microsoft-Teams-App-Reflect)

:::row:::
    :::column:::
    <span data-ttu-id="4af47-405">**Sondagem de bem-estar**</span><span class="sxs-lookup"><span data-stu-id="4af47-405">**Well-being poll**</span></span>
    
    ![Refletir sondagem do usuário do aplicativo](../assets/images/reflect-app-user-poll.png)
    :::column-end:::
:::row-end:::

## <a name="remote-support"></a><span data-ttu-id="4af47-407">Suporte remoto</span><span class="sxs-lookup"><span data-stu-id="4af47-407">Remote Support</span></span>

<span data-ttu-id="4af47-408">O Suporte Remoto é um [Microsoft Teams que](../bots/what-are-bots.md) fornece uma interface focada entre solicitadores de suporte em toda a sua organização e a equipe de suporte interno.</span><span class="sxs-lookup"><span data-stu-id="4af47-408">Remote Support is a [Microsoft Teams bot](../bots/what-are-bots.md) that provides a focused interface between support requesters throughout your organization and the internal support team.</span></span>  <span data-ttu-id="4af47-409">Os usuários finais podem enviar, editar ou retirar solicitações de suporte e a equipe de suporte pode responder, gerenciar e atualizar todas as solicitações na plataforma Teams.</span><span class="sxs-lookup"><span data-stu-id="4af47-409">End-users can submit, edit, or withdraw requests for support and the support team can respond, manage, and update requests all within the Teams platform.</span></span>

[<span data-ttu-id="4af47-410">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-410">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-remotesupport)

:::row:::
  :::column span="2":::
    ![Solicitar formulário de suporte](../assets/images/remote-support-request-form.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Solicitar detalhes de suporte](../assets/images/remote-support-request-details.jpg)
:::column-end:::
:::row-end:::

## <a name="request-a-team"></a><span data-ttu-id="4af47-413">Request-a-team</span><span class="sxs-lookup"><span data-stu-id="4af47-413">Request-a-team</span></span>

<span data-ttu-id="4af47-414">Request-a-team é um Microsoft Teams que otimiza a criação de nova equipe para sua organização corporativa.</span><span class="sxs-lookup"><span data-stu-id="4af47-414">Request-a-team is a Microsoft Teams app that optimizes new team creation for your enterprise organization.</span></span> <span data-ttu-id="4af47-415">O aplicativo dá suporte à padronização e às práticas recomendadas ao criar novas instâncias de equipe por meio da integração de um formulário de solicitação orientado pelo assistente, um processo de aprovação incorporado, um painel de status de solicitação e com builds de equipe automatizados.</span><span class="sxs-lookup"><span data-stu-id="4af47-415">The app supports standardization and best practices when creating new team instances through the integration of a wizard-guided request form, an embedded approval process, a request status dashboard, and automated team builds.</span></span>

[<span data-ttu-id="4af47-416">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-416">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-requestateam)

:::row:::
  :::column span="2":::
    ![Exibição de página inicial de solicitação de equipe](../assets/images/request-a-team-two.jpg)
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Exibição de página do assistente de solicitação de equipe](../assets/images/request-a-team-three.png)
:::column-end:::
:::row-end:::

## <a name="scrums-for-channels"></a><span data-ttu-id="4af47-419">Scrums for Channels</span><span class="sxs-lookup"><span data-stu-id="4af47-419">Scrums for Channels</span></span>

<span data-ttu-id="4af47-420">O Scrums for Channels é um aplicativo assistente scrum que permite que os usuários agendem e executem scrums em canais dentro Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="4af47-420">Scrums for Channels is a scrum assistant app that enables users to schedule and run scrums in channels within Microsoft Teams.</span></span> <span data-ttu-id="4af47-421">O aplicativo é ótimo para equipes remotas e equipes compostas por membros de locais geográficos e fusos horário variados para compartilhar atualizações diárias e garantir a participação em reuniões de stand-up scrum.</span><span class="sxs-lookup"><span data-stu-id="4af47-421">The app is great for remote teams and teams comprised of members from varied geographical locations and time zones to share daily updates and ensure participation in scrum stand-up meetings.</span></span>

[<span data-ttu-id="4af47-422">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-422">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-scrumsforchannels)

> [!NOTE]
> <span data-ttu-id="4af47-423">Para conduzir reuniões scrum em um chat em grupo, consulte [Scrums for Group Chat app](#scrums-for-group-chat) template.</span><span class="sxs-lookup"><span data-stu-id="4af47-423">To conduct scrum meetings in a group chat, see [Scrums for Group Chat](#scrums-for-group-chat) app template.</span></span>

:::row:::
  :::column span="2":::
    ![Scrums para exibição de configurações de canais](../assets/images/scrum-for-channels-settings.png)
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Scrums para exibição de status de membro da equipe de canais](../assets/images/scrum-for-channels-status.png)
:::column-end:::
:::row-end:::

## <a name="scrums-for-group-chat"></a><span data-ttu-id="4af47-426">Scrums para Chat em Grupo</span><span class="sxs-lookup"><span data-stu-id="4af47-426">Scrums for Group Chat</span></span>

> [!NOTE]
> <span data-ttu-id="4af47-427">O modelo de aplicativo Status do Scrums foi atualizado e agora é Scrums para Chat de Grupo.</span><span class="sxs-lookup"><span data-stu-id="4af47-427">The Scrums Status app template is updated and is now Scrums for Group Chat.</span></span>

<span data-ttu-id="4af47-428">O Scrums for Group Chat é um assistente de scrum de suporte que permite que os membros do chat de grupo executem reuniões de stand-up assíncronas e compartilhem facilmente suas atualizações diárias.</span><span class="sxs-lookup"><span data-stu-id="4af47-428">Scrums for Group Chat is a supportive scrum assistant that enables group chat members to run asynchronous stand-up meetings and easily share their daily updates.</span></span> <span data-ttu-id="4af47-429">Ele permite que todos os membros do chat de grupo contribuam para o scrum e exibir as atualizações feitas por outras pessoas no scrum em execução.</span><span class="sxs-lookup"><span data-stu-id="4af47-429">It allows all members of the group chat to contribute to the scrum and view the updates made by others in the running scrum.</span></span>

[<span data-ttu-id="4af47-430">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-430">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-scrumsforgroupchat)

![Demonstração do Scrums for Group Chat](https://raw.githubusercontent.com/wiki/OfficeDev/microsoft-teams-app-scrumstatus/images/StartScrum.jpg)

## <a name="share-now"></a><span data-ttu-id="4af47-432">Compartilhar Agora</span><span class="sxs-lookup"><span data-stu-id="4af47-432">Share Now</span></span> 

<span data-ttu-id="4af47-433">O aplicativo Compartilhar Agora promove a troca positiva de informações entre colegas permitindo que seus usuários compartilhem facilmente conteúdo no ambiente Teams.</span><span class="sxs-lookup"><span data-stu-id="4af47-433">The Share Now app promotes the positive exchange of information between colleagues by enabling your users to easily share content within the Teams environment.</span></span> <span data-ttu-id="4af47-434">Os usuários envolvem o aplicativo para compartilhar itens de interesse com membros da equipe, descobrir novo conteúdo compartilhado, definir preferências e favoritos de indicador para leitura posterior.</span><span class="sxs-lookup"><span data-stu-id="4af47-434">Users engage the app to share items of interest with team members, discover new shared content, set preferences, and bookmark favorites for later reading.</span></span>

[<span data-ttu-id="4af47-435">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-435">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-sharenow)

![Selecionar exibição de conteúdo](../assets/images/share-now-suggested-content.png)

## <a name="sharepoint-list-search"></a><span data-ttu-id="4af47-437">Pesquisa de lista do SharePoint</span><span class="sxs-lookup"><span data-stu-id="4af47-437">SharePoint List Search</span></span>

<span data-ttu-id="4af47-438">A colaboração Microsoft Teams muitas vezes faz referência às informações contidas em itens em uma SharePoint lista.</span><span class="sxs-lookup"><span data-stu-id="4af47-438">Collaboration in Microsoft Teams quite often references information contained within items in a SharePoint list.</span></span> <span data-ttu-id="4af47-439">Colar um link para o item em questão força todos a alternar o contexto da conversa, encontrar as informações necessárias e retornar ao Teams para continuar a conversa.</span><span class="sxs-lookup"><span data-stu-id="4af47-439">Paste a link to the item in question forces everyone to switch context away from the conversation, find the needed information, then return to Teams to continue the conversation.</span></span> <span data-ttu-id="4af47-440">À medida que a conversa continua, as pessoas têm que voltar para o item de referência várias vezes para verificar novos comentários e atualizar suas recordações das informações contidas no item.</span><span class="sxs-lookup"><span data-stu-id="4af47-440">As the conversation continues  people have to switch back to the reference item multiple times to verify new comments and refresh their memories of the information contained within the item.</span></span> <span data-ttu-id="4af47-441">Essa alternação de contexto cria uma barreira para suavizar a colaboração.</span><span class="sxs-lookup"><span data-stu-id="4af47-441">This context switching creates a barrier to smooth collaboration.</span></span>
<span data-ttu-id="4af47-442">Para resolver esse problema, o modelo de aplicativo de Pesquisa de Lista é usado.</span><span class="sxs-lookup"><span data-stu-id="4af47-442">To resolve this problem, the List Search app template is used.</span></span> <span data-ttu-id="4af47-443">Muitos usuários usam SharePoint para dar energia a alguns dos principais fluxos de trabalho em suas organizações.</span><span class="sxs-lookup"><span data-stu-id="4af47-443">Many users use SharePoint to power some of the core workflows in their organizations.</span></span> <span data-ttu-id="4af47-444">No entanto, é difícil colaborar em torno de listas.</span><span class="sxs-lookup"><span data-stu-id="4af47-444">However, collaborating around lists is difficult.</span></span> <span data-ttu-id="4af47-445">Usando o modelo de aplicativo de Pesquisa de Lista no Microsoft Teams, os usuários podem inserir informações de itens de lista SharePoint diretamente em uma conversa de chat para aliviar a alternância de contexto causada ao simplesmente inserir um link em um chat.</span><span class="sxs-lookup"><span data-stu-id="4af47-445">Using the List Search app template in Microsoft Teams, users can insert information from SharePoint list items directly within a chat conversation to alleviate the context-switching caused when simply inserting a link into a chat.</span></span> <span data-ttu-id="4af47-446">As informações são inseridas como um cartão de formatação automática fácil de ler, ajudando os usuários a permanecer envolvidos na conversa.</span><span class="sxs-lookup"><span data-stu-id="4af47-446">The information is inserted as an easy-to-read auto-formatted card, helping the users stay engaged in the conversation.</span></span>

[<span data-ttu-id="4af47-447">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-447">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-list-search-app)

![Aplicativo de Pesquisa de Lista](../assets/images/list-search-template.png)

## <a name="staff-check-ins"></a><span data-ttu-id="4af47-449">Check-ins de equipe</span><span class="sxs-lookup"><span data-stu-id="4af47-449">Staff Check-ins</span></span>

<span data-ttu-id="4af47-450">Os Check-ins de equipe são [um aplicativo Power Apps](/powerapps/powerapps-overview) baseado em segurança que permite a comunicação de supervisão entre sua empresa e a equipe de campo.</span><span class="sxs-lookup"><span data-stu-id="4af47-450">Staff Check-ins is a [Power Apps](/powerapps/powerapps-overview) based app that enables oversight communication between your business and field personnel.</span></span> <span data-ttu-id="4af47-451">A equipe pode fornecer informações e atualizações de status de tempo críticos facilmente em uma base agendada ou ad hoc diretamente do Teams.</span><span class="sxs-lookup"><span data-stu-id="4af47-451">Staff can easily provide time-critical information and status updates on either a scheduled or ad-hoc basis directly from Teams.</span></span> <span data-ttu-id="4af47-452">O aplicativo dá suporte a locais, fotos, anotações, notificações de lembrete e fluxos de trabalho automatizados em tempo real.</span><span class="sxs-lookup"><span data-stu-id="4af47-452">The app supports real-time location, photos, notes, reminder notifications, and automated workflows.</span></span>

[<span data-ttu-id="4af47-453">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-453">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-staffcheckins)

![Criar exibição de check-in](../assets/images/staff-check-ins-create.png)

## <a name="survey"></a><span data-ttu-id="4af47-455">Pesquisa</span><span class="sxs-lookup"><span data-stu-id="4af47-455">Survey</span></span>

<span data-ttu-id="4af47-456">A pesquisa é um [](../messaging-extensions/what-are-messaging-extensions.md) aplicativo Microsoft Teams de extensão de mensagens personalizado que permite que você crie uma pesquisa em um chat ou canal para coletar dados e obter informações ativas.</span><span class="sxs-lookup"><span data-stu-id="4af47-456">Survey is a custom Microsoft Teams [messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that enables you to create a survey in a chat or a channel to gather data and gain actionable insight.</span></span> <span data-ttu-id="4af47-457">O aplicativo tem suporte em todos os clientes da plataforma Teams, como desktop, navegador, iOS e Android, e está pronto para implantação como parte da sua assinatura Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="4af47-457">The app is supported across all Teams platform clients, such as desktop, browser, iOS, and Android and is ready for deployment as part of your Microsoft 365 subscription.</span></span>  

[<span data-ttu-id="4af47-458">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-458">Get it on GitHub</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Survey-app)

:::row:::
  :::column span="2":::
    ![Criar pesquisa no Teams exibição](../assets/images/survey-app-template-compose-view.gif)
:::column-end:::
:::row-end:::

## <a name="time-tally"></a><span data-ttu-id="4af47-460">Time Tally</span><span class="sxs-lookup"><span data-stu-id="4af47-460">Time Tally</span></span> 

<span data-ttu-id="4af47-461">Um projeto pode incluir várias tarefas e vários projetos podem ser atribuídos aos funcionários.</span><span class="sxs-lookup"><span data-stu-id="4af47-461">A project can include multiple tasks, and various projects can be assigned to employees.</span></span> <span data-ttu-id="4af47-462">Os gerentes são obrigados a entender o andamento do projeto pelo tempo gasto pelos funcionários nessas tarefas.</span><span class="sxs-lookup"><span data-stu-id="4af47-462">Managers are required to understand the project progress through the time spent by the employees on these tasks.</span></span> <span data-ttu-id="4af47-463">Isso pode ser uma atividade complicada, pois os funcionários precisam preencher os quadro de horários.</span><span class="sxs-lookup"><span data-stu-id="4af47-463">This can be a cumbersome activity, as the employees need to fill in the timesheets.</span></span> <span data-ttu-id="4af47-464">O aplicativo Time Tally permite que os funcionários preencham seus quadro de horários rapidamente, usando o dispositivo móvel, e os gerentes não têm que acompanhar os funcionários na entrada do quadro de horários.</span><span class="sxs-lookup"><span data-stu-id="4af47-464">Time Tally app enables employees to fill their timesheets quickly, using the mobile device, and managers do not have to follow up with employees on the timesheet entry.</span></span> <span data-ttu-id="4af47-465">Os gerentes podem exibir a utilização do projeto com base em recursos e podem aprovar ou rejeitar as entradas.</span><span class="sxs-lookup"><span data-stu-id="4af47-465">Managers get to view the project utilization based on resources, and they can approve or reject the entries.</span></span> <span data-ttu-id="4af47-466">As notificações de lembrete são enviadas para garantir a conformidade do quadro de horários.</span><span class="sxs-lookup"><span data-stu-id="4af47-466">Reminder notifications are sent to ensure timesheet compliance.</span></span> <span data-ttu-id="4af47-467">Além disso, dados históricos e utilizações estão disponíveis para análise.</span><span class="sxs-lookup"><span data-stu-id="4af47-467">Also, historical data and utilizations are available for analytics.</span></span>

[<span data-ttu-id="4af47-468">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-468">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-timetally)

![Time Tally](../assets/images/11zon_gif.gif)

## <a name="training--9734"></a><span data-ttu-id="4af47-470">Treinamento &#9734;</span><span class="sxs-lookup"><span data-stu-id="4af47-470">Training  &#9734;</span></span>

<span data-ttu-id="4af47-471">O treinamento é [um](../messaging-extensions/what-are-messaging-extensions.md) aplicativo de extensão Teams mensagens personalizado que permite que os usuários publiquem um treinamento em um chat ou um canal para compartilhamento de conhecimento offline e upskilling.</span><span class="sxs-lookup"><span data-stu-id="4af47-471">Training is a custom [Teams messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that enables users to publish a training within a chat or a channel for offline knowledge sharing and upskilling.</span></span> <span data-ttu-id="4af47-472">O aplicativo tem suporte em vários clientes Teams plataforma, como desktop, navegador, iOS e Android.</span><span class="sxs-lookup"><span data-stu-id="4af47-472">The app is supported across multiple Teams platform clients, such as desktop, browser, iOS, and Android.</span></span> <span data-ttu-id="4af47-473">Este aplicativo está pronto para implantação como parte de sua assinatura Microsoft 365 de usuário.</span><span class="sxs-lookup"><span data-stu-id="4af47-473">This app is ready for deployment as part of your Microsoft 365 subscription.</span></span>

[<span data-ttu-id="4af47-474">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-474">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-training)

:::row:::
  :::column span="1":::
    ![Criar Treinamento no Teams exibição](../assets/images/training-app-template-compose-view.gif)  
:::column-end:::
:::row-end:::

## <a name="virtual-rounding"></a><span data-ttu-id="4af47-476">Arredondamento Virtual</span><span class="sxs-lookup"><span data-stu-id="4af47-476">Virtual Rounding</span></span>

<span data-ttu-id="4af47-477">Os provedores de hospital e de emergência fazem muitas **rodadas** por dia.</span><span class="sxs-lookup"><span data-stu-id="4af47-477">Hospital and emergency room providers make many **rounds** per day.</span></span> <span data-ttu-id="4af47-478">Esses check-ins rápidos em pacientes destinam-se a fornecer uma verificação de status sobre como o paciente está fazendo e garantir que as preocupações do paciente sejam resolvidas.</span><span class="sxs-lookup"><span data-stu-id="4af47-478">These quick check-ins on patients are intended to provide a status check on how the patient is doing and ensure that the patient’s concerns are addressed.</span></span> <span data-ttu-id="4af47-479">Embora o arredondamento seja uma prática essencial para garantir que os pacientes sejam monitorados por vários tipos de provedores, eles representam um dreno enorme no PPE, pois para cada visita, de cada provedor, uma nova máscara e um novo conjunto de luvas são usados.</span><span class="sxs-lookup"><span data-stu-id="4af47-479">While rounding is an essential practice to ensure patients are being monitored by multiple types of providers, they represent a huge drain on PPE, because for each visit, from each provider, a new mask, and new set of gloves are used.</span></span> <span data-ttu-id="4af47-480">Com esses modelos de aplicativo, os funcionários médicos podem conduzir facilmente rodadas virtualmente, por meio de uma reunião Microsoft Teams entre o provedor e o paciente.</span><span class="sxs-lookup"><span data-stu-id="4af47-480">With this app templates, medical workers can easily conduct rounds virtually, through a Microsoft Teams meeting between the provider and the patient.</span></span>

<span data-ttu-id="4af47-481">A solução de Arredondamento Virtual também é referenciada na postagem do [blog](https://aka.ms/teamsvirtualrounding)Microsoft Health e Life Sciences.</span><span class="sxs-lookup"><span data-stu-id="4af47-481">The Virtual Rounding solution is also referenced in the Microsoft Health and Life Sciences [blog post](https://aka.ms/teamsvirtualrounding).</span></span>

[<span data-ttu-id="4af47-482">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-482">Get it on GitHub</span></span>](https://github.com/SmartterHealth/Virtual-Rounding)

![Arredondamento Virtual](../assets/images/virtual-rounding-overview.png)

## <a name="visitor-management"></a><span data-ttu-id="4af47-484">Gerenciamento de Visitantes</span><span class="sxs-lookup"><span data-stu-id="4af47-484">Visitor Management</span></span>

<span data-ttu-id="4af47-485">O aplicativo de Gerenciamento de Visitantes permite que sua organização e funcionários gerenciem de forma fácil e eficiente o processo de visitante local, diretamente Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="4af47-485">The Visitor Management app enables your organization and employees to easily and efficiently manage the on-site visitor process, directly from Microsoft Teams.</span></span> <span data-ttu-id="4af47-486">O aplicativo permite que os funcionários criem solicitações de visitante, rastreiem centralmente um status de solicitação por meio do painel de visitantes e recebam notificações em tempo real quando um visitante chegar.</span><span class="sxs-lookup"><span data-stu-id="4af47-486">The app enables employees to create visitor requests, centrally track a request status through the visitor dashboard, and receive real-time notifications when a visitor arrives.</span></span>

[<span data-ttu-id="4af47-487">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-487">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-app-visitormanagement)

:::row:::
  :::column span="2":::
    ![Criar um exibição de solicitação](../assets/images/visitor-management-create-request.png)
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Notificação de chegada do visitante](../assets/images/visitor-management-notify-host.png)
:::column-end:::
:::row-end:::

## <a name="workplace-awards"></a><span data-ttu-id="4af47-490">Workplace Awards</span><span class="sxs-lookup"><span data-stu-id="4af47-490">Workplace Awards</span></span>

<span data-ttu-id="4af47-491">Workplace Awards é um Teams de aplicativos que fornece uma estrutura positiva para promover o reconhecimento e incentivar a cultura da valorização dos funcionários no local de trabalho moderno.</span><span class="sxs-lookup"><span data-stu-id="4af47-491">Workplace Awards is a Teams app template that provides a positive framework to foster recognition and encourage the culture of employee appreciation in the modern workplace.</span></span> <span data-ttu-id="4af47-492">O aplicativo permite que você configure e gerencie recompensas e reconhecimento de funcionários, chamado R&R programa onde os funcionários podem facilmente nomear e endossar colegas e seu líder R&R pode exibir nomeações enviadas, conceder prêmios e anunciar destinatários.</span><span class="sxs-lookup"><span data-stu-id="4af47-492">The app enables you to setup and manage an employee rewards and recognition, called R&R program where employees can easily nominate and endorse colleagues and your R&R leader can view submitted nominations, grant awards, and announce recipients.</span></span>

[<span data-ttu-id="4af47-493">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="4af47-493">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-workplaceawards)

:::row:::
  :::column span="2":::
    ![<span data-ttu-id="4af47-494">Cartão de nomeação de prêmio de local de trabalho</span><span class="sxs-lookup"><span data-stu-id="4af47-494">Workplace awards nomination card</span></span> ](../assets/images/workplace-awards-nominate.png)
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Guia de lista de prêmios do local de trabalho](../assets/images/workplace-awards-champion-tab.png)
:::column-end:::
:::row-end:::

<span data-ttu-id="4af47-496">Para obter mais informações sobre o modelo de aplicativo, consulte [Modelo de aplicativo](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR2_7qFm_lcZAr4eqEhnLsZ9UMVZGT1lCT0FXUDdZMUM0RkpBS1BESTAwWC4u).</span><span class="sxs-lookup"><span data-stu-id="4af47-496">For more information on app template, see [App template](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR2_7qFm_lcZAr4eqEhnLsZ9UMVZGT1lCT0FXUDdZMUM0RkpBS1BESTAwWC4u).</span></span>

## <a name="see-also"></a><span data-ttu-id="4af47-497">Confira também</span><span class="sxs-lookup"><span data-stu-id="4af47-497">See also</span></span>

[<span data-ttu-id="4af47-498">Integrar aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="4af47-498">Integrate web apps</span></span>](~/samples/integrate-web-apps-overview.md)
