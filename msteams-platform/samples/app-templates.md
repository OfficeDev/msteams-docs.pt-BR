---
title: Modelos de aplicativos do Microsoft Teams
description: Links e descrições dos modelos de aplicativo para a plataforma Microsoft Teams
ms.topic: reference
keywords: Demonstração de exemplos de modelos do Microsoft Teams
ms.author: lajanuar
author: laujan
ms.openlocfilehash: 401d1e5878a026b2ff066114e4d41a0a54c0cf09
ms.sourcegitcommit: 55a4246e62d69d631a63bdd33de34f1b62cc0132
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2021
ms.locfileid: "50093961"
---
# <a name="app-templates-for-microsoft-teams"></a><span data-ttu-id="01ca3-104">Modelos de aplicativo para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="01ca3-104">App Templates for Microsoft Teams</span></span>

<span data-ttu-id="01ca3-105">Modelos de aplicativos são aplicativos prontos para produção para o Microsoft Teams que são orientados pela comunidade, de código aberto e disponíveis no GitHub.</span><span class="sxs-lookup"><span data-stu-id="01ca3-105">App templates are production-ready apps for Microsoft Teams that are community driven, open-source, and available on GitHub.</span></span> <span data-ttu-id="01ca3-106">Cada um deles contém instruções detalhadas para implantar e instalar esse aplicativo para sua organização, fornecendo um aplicativo pronto para uso que você pode instalar e começar a usar imediatamente.</span><span class="sxs-lookup"><span data-stu-id="01ca3-106">Each contains detailed instructions for deploying and installing that app for your organization, providing a ready-to-use app that you can install and begin using immediately.</span></span> <span data-ttu-id="01ca3-107">O código-fonte completo também está disponível, para que você possa explorá-lo em detalhes ou bifurcar o código e alterá-lo para atender às suas necessidades específicas.</span><span class="sxs-lookup"><span data-stu-id="01ca3-107">The complete source code is available as well, so you can explore it in detail, or fork the code and alter it to meet your specific needs.</span></span>

<span data-ttu-id="01ca3-108">**&#9734; Indica modelos de aplicativo lançados recentemente.**</span><span class="sxs-lookup"><span data-stu-id="01ca3-108">**&#9734; Indicates newly released app templates.**</span></span>

### <a name="key-benefits"></a><span data-ttu-id="01ca3-109">Principais benefícios</span><span class="sxs-lookup"><span data-stu-id="01ca3-109">Key benefits</span></span>

* <span data-ttu-id="01ca3-110">**Experiência de plug and play:** Todos os modelos de aplicativo incluem scripts de implantações que permitirão que você hospede todos os serviços necessários no Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="01ca3-110">**Plug and play experience:** All app templates include deployments scripts that will allow you to host all necessary services in Microsoft Azure.</span></span> <span data-ttu-id="01ca3-111">Nenhuma codificação é necessária para implantar os aplicativos.</span><span class="sxs-lookup"><span data-stu-id="01ca3-111">No coding is required to deploy the apps.</span></span>
* <span data-ttu-id="01ca3-112">**Código pronto para produção:** Os modelos de aplicativos estão em conformidade com as práticas recomendadas de segurança e infraestrutura, e todas as alterações enviadas à comunidade são revisadas para garantir a conformidade contínua.</span><span class="sxs-lookup"><span data-stu-id="01ca3-112">**Production-ready code:** The app templates conform to recommended best practices around security and infrastructure, and all community submitted changes to them are reviewed to ensure continued conformance.</span></span>
* <span data-ttu-id="01ca3-113">**Personalizável e extensível:** Enquanto todos os modelos de aplicativos estão prontos para implantação como estão, fornecemos toda a base de código e scripts de implantação para que você possa personalizá-los ou estendizá-los facilmente de acordo com suas necessidades exclusivas.</span><span class="sxs-lookup"><span data-stu-id="01ca3-113">**Customizable and extensible:** While all app templates are ready to deploy as they are, we provide the entire code base and deployment scripts so that you can easily customize or extend them to fit your unique needs.</span></span>
* <span data-ttu-id="01ca3-114">**Documentação detalhada & suporte:** Todos os modelos de aplicativo são acompanhados pela documentação de ponta a ponta sobre as etapas de arquitetura, implantação e configuração da solução.</span><span class="sxs-lookup"><span data-stu-id="01ca3-114">**Detailed documentation & support:** All app templates are accompanied by end-to-end documentation on solution architecture, deployment, and configuration steps.</span></span> <span data-ttu-id="01ca3-115">Os repositórios também são monitorados, portanto, informe todos os problemas encontrados a fim de emitir um problema no GitHub.</span><span class="sxs-lookup"><span data-stu-id="01ca3-115">The repositories are monitored as well, so please report any issues you encounter by raising an Issue on GitHub.</span></span>

## <a name="adoption-bot-9734"></a><span data-ttu-id="01ca3-116">Adoção de bots &#9734;</span><span class="sxs-lookup"><span data-stu-id="01ca3-116">Adoption Bot &#9734;</span></span>

<span data-ttu-id="01ca3-117">Bot de adoção é um bot de chat com cuidado do usuário criado com o Power Virtual Agent para Teams (PVA).</span><span class="sxs-lookup"><span data-stu-id="01ca3-117">Adoption Bot is a user care chat bot built with Power Virtual Agent for Teams (PVA).</span></span> <span data-ttu-id="01ca3-118">Ele pode ser considerado como a versão PVA do FAQPlus.</span><span class="sxs-lookup"><span data-stu-id="01ca3-118">It can be considered as the PVA version of FAQPlus.</span></span> <span data-ttu-id="01ca3-119">O Bot de Adoção responde mais de 100 perguntas comuns sobre o Microsoft 365 e o Teams.</span><span class="sxs-lookup"><span data-stu-id="01ca3-119">Adoption Bot answers 100+ common questions about Microsoft 365 and Teams.</span></span> <span data-ttu-id="01ca3-120">Você pode editar os tópicos incluídos, adicionar seus próprios tópicos e ingerir perguntas frequentes existentes.</span><span class="sxs-lookup"><span data-stu-id="01ca3-120">You can edit the included topics, add your own topics, and ingest existing FAQs.</span></span> <span data-ttu-id="01ca3-121">Se os usuários precisam de ajuda adicional, o Bot de Adoção pode conectá-los a especialistas ou até mesmo ser estendido para abrir tíquetes de serviço com conectores de fluxo premium.</span><span class="sxs-lookup"><span data-stu-id="01ca3-121">If users need additional help, Adoption Bot can connect them to experts or even be extended to open service tickets with premium flow connectors.</span></span>

[<span data-ttu-id="01ca3-122">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-122">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-adopt-bot)

## <a name="appointment-manager-9734"></a><span data-ttu-id="01ca3-123">Gerenciador de compromissos &#9734;</span><span class="sxs-lookup"><span data-stu-id="01ca3-123">Appointment Manager &#9734;</span></span>

<span data-ttu-id="01ca3-124">O Gerenciador de Compromissos é um modelo de aplicativo do Teams para ajudar as empresas a criar, gerenciar e conduzir compromissos virtuais com os consumidores por meio do Teams.</span><span class="sxs-lookup"><span data-stu-id="01ca3-124">Appointment Manager is a Teams app template to help businesses create, manage, and conduct virtual appointments with consumers through Teams.</span></span> <span data-ttu-id="01ca3-125">As novas solicitações de compromissos dos consumidores são visíveis nos canais do Teams, onde eles podem ser atribuídos e reatribuídos rapidamente aos funcionários de uma equipe.</span><span class="sxs-lookup"><span data-stu-id="01ca3-125">New appointment requests from consumers are visible in Teams channels, where they can quickly be assigned and reassigned to staff in a team.</span></span> <span data-ttu-id="01ca3-126">As solicitações de compromisso podem ser visualizadas em níveis de equipe ou pessoal por meio de guias personalizadas.</span><span class="sxs-lookup"><span data-stu-id="01ca3-126">Appointment requests can be viewed at team or personal levels through custom tabs.</span></span> <span data-ttu-id="01ca3-127">Cada compromisso é associado a uma reunião online do Teams, por isso, os funcionários e os consumidores podem facilmente ingressar na reunião no horário agendado.</span><span class="sxs-lookup"><span data-stu-id="01ca3-127">Every appointment is associated with a Teams online meeting, hence the staff and consumers can easily join the meeting at the scheduled time.</span></span>

<span data-ttu-id="01ca3-128">O modelo de aplicativo se integra ao Microsoft Bookings para facilitar o gerenciamento de compromissos.</span><span class="sxs-lookup"><span data-stu-id="01ca3-128">The app template integrates with Microsoft Bookings for easy appointment management.</span></span> <span data-ttu-id="01ca3-129">Os compromissos agendados aparecem automaticamente nos calendários dos membros da equipe atribuídos, e os consumidores recebem notificações por email e lembretes personalizáveis com links de reunião incorporados.</span><span class="sxs-lookup"><span data-stu-id="01ca3-129">Scheduled appointments automatically appear on assigned staff members' calendars, and consumers receive customizable email notifications and reminders with embedded meeting links.</span></span>

[<span data-ttu-id="01ca3-130">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-130">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-appointment-manager)

<span data-ttu-id="01ca3-131">![Gerenciador de Compromissos de ](../assets/images/appointment-manager-overview.png)
 ![ Visão Geral do Gerenciador de Compromissos no Teams](../assets/images/appointment-manager-2.png)</span><span class="sxs-lookup"><span data-stu-id="01ca3-131">![Appointment Manager Overview](../assets/images/appointment-manager-overview.png)
![Appointment Manager in Teams](../assets/images/appointment-manager-2.png)</span></span>

## <a name="ask-away"></a><span data-ttu-id="01ca3-132">Pergunte-se</span><span class="sxs-lookup"><span data-stu-id="01ca3-132">Ask Away</span></span>

<span data-ttu-id="01ca3-133">Ask Away é um [bot do Microsoft Teams](../bots/what-are-bots.md) que permite que os usuários conduzam sessões de perguntas&A (pergunta e resposta) no Teams.</span><span class="sxs-lookup"><span data-stu-id="01ca3-133">Ask Away is a [Microsoft Teams bot](../bots/what-are-bots.md) that enables users to conduct Q&A (Question and Answer) sessions within Teams.</span></span> <span data-ttu-id="01ca3-134">Usando o bot Pergunte-se, os membros da equipe podem enviar e votações compartilhadas por colegas, permitindo que os hosts de P&e R reúnam facilmente perguntas mais importantes em um canal ou chat.</span><span class="sxs-lookup"><span data-stu-id="01ca3-134">Using the Ask Away bot, team members can submit and up-vote questions shared by colleagues allowing Q&A hosts to easily gather top-of-mind questions within a channel or chat.</span></span> <span data-ttu-id="01ca3-135">O bot pode ser usado para conduzir perguntas e respostas em tempo real&Uma sessão em uma reunião do Teams e permite que os participantes enviem perguntas ao vivo por meio de chat.</span><span class="sxs-lookup"><span data-stu-id="01ca3-135">The bot can be used to conduct a real-time Q&A session in a Teams meeting and allows attendees to submit questions live via chat.</span></span>

[<span data-ttu-id="01ca3-136">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-136">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-askaway)

:::row:::
  :::column span="2":::
    ![View of the leaderboard pop-up dialog for users to vote on questions](../assets/images/ask-away-app.png)  
:::column-end:::
:::row-end:::

## <a name="associate-insights"></a><span data-ttu-id="01ca3-138">Informações associadas</span><span class="sxs-lookup"><span data-stu-id="01ca3-138">Associate Insights</span></span>

<span data-ttu-id="01ca3-139">O Associate Insights é um [modelo do Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) que capacita os trabalhadores da linha de frente a capturar e enviar diretamente opiniões, opiniões e percepção dos clientes.</span><span class="sxs-lookup"><span data-stu-id="01ca3-139">Associate Insights is a [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) template that empowers firstline workers to directly capture and submit customer opinion, sentiment, and perception.</span></span> <span data-ttu-id="01ca3-140">Os trabalhadores da linha de frente geralmente são os primeiros representantes da empresa a se envolver com clientes em um ponto de contato um-para-um.</span><span class="sxs-lookup"><span data-stu-id="01ca3-140">Firstline workers are often the first company representative to engage with customers in a one-to-one point-of contact.</span></span> <span data-ttu-id="01ca3-141">Os dados coletados podem ser compartilhados e usados de forma colaborativa por equipes de negócios, por exemplo, por meio de uma guia do Power BI Teams, para melhorar o produto e aprimorar a experiência do cliente.</span><span class="sxs-lookup"><span data-stu-id="01ca3-141">The collected data can be shared and used collaboratively by business teams, e.g., via a Power BI Teams tab, for product improvement and enhancing the customer experience.</span></span>

[<span data-ttu-id="01ca3-142">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-142">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-associateinsights)

:::row:::
  :::column span="2":::
    ![Exibição de comentários das informações geradas pelo aplicativo](../assets/images/associate-insights-app.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Exibição do Power BI de insights gerados pelo aplicativo](../assets/images/associate-insights-app2.png)
:::column-end:::
:::row-end:::

## <a name="attendance"></a><span data-ttu-id="01ca3-145">Participação</span><span class="sxs-lookup"><span data-stu-id="01ca3-145">Attendance</span></span>

<span data-ttu-id="01ca3-146">O aplicativo Presença é uma [guia do Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) que pode ser fixada em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="01ca3-146">The Attendance app is a [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) tab that can be pinned in a team.</span></span> <span data-ttu-id="01ca3-147">Ele foi projetado para registrar a presença, normalmente em configurações como ambientes de aprendizagem e treinamento.</span><span class="sxs-lookup"><span data-stu-id="01ca3-147">It is designed to record presence, typically in settings such as learning and training environments.</span></span> <span data-ttu-id="01ca3-148">Os usuários podem marcar ou editar a participação por até 30 dias no passado e exibir relatórios resumidos de presença para um grupo inteiro ou participantes individuais.</span><span class="sxs-lookup"><span data-stu-id="01ca3-148">Users can mark or edit attendance for up to 30 days in the past and view summarized attendance reports for an entire group or individual attendees.</span></span>

[<span data-ttu-id="01ca3-149">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-149">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-attendance)

![Demonstração do aplicativo de participação](../assets/images/attendance-app.png)

## <a name="book-a-room"></a><span data-ttu-id="01ca3-151">Book-a-room</span><span class="sxs-lookup"><span data-stu-id="01ca3-151">Book-a-room</span></span>

<span data-ttu-id="01ca3-152">Book-a-room é um bot do [Microsoft Teams](../bots/what-are-bots.md) que permite aos usuários encontrar e reservar rapidamente uma sala de reunião por 30 (padrão), 60 ou 90 minutos a partir da hora atual.</span><span class="sxs-lookup"><span data-stu-id="01ca3-152">Book-a-room is a [Microsoft Teams bot](../bots/what-are-bots.md) that lets users quickly find and reserve a meeting room for 30 (default), 60, or 90 minutes starting from the current  time.</span></span> <span data-ttu-id="01ca3-153">Os escopos de bot de sala de livro para conversas pessoais ou 1:1.</span><span class="sxs-lookup"><span data-stu-id="01ca3-153">The Book-a-room bot scopes to personal or 1:1 conversations.</span></span>

[<span data-ttu-id="01ca3-154">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-154">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom)

![Demonstração de livro em sala](../assets/images/book-a-room.png)

## <a name="building-access"></a><span data-ttu-id="01ca3-156">Acesso à construção</span><span class="sxs-lookup"><span data-stu-id="01ca3-156">Building Access</span></span>

<span data-ttu-id="01ca3-157">O Building Access é um aplicativo baseado no Microsoft [Power Platform](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/)que oferece suporte à administração da criação de limites de acumulação e de padrões de distanciamento social, permitindo que os diretores de instalações gerenciem, rastreiem e reportem a presença de funcionários no local.</span><span class="sxs-lookup"><span data-stu-id="01ca3-157">Building Access is a Microsoft [Power Platform](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/)-based app that supports the administration of building occupancy thresholds and social distancing norms by enabling facilities directors to manage, track, and report employee on-site presence.</span></span> <span data-ttu-id="01ca3-158">O aplicativo, criado usando o Microsoft [Power Apps](/powerapps/powerapps-overview)e o [Power Automate,](/power-automate/getting-started)integra-se profundamente ao Microsoft Teams e permite que as organizações determinem a preparação da construção, estabeleçam critérios de qualificação para o acesso local e reúnam ideias para planejamento futuro.</span><span class="sxs-lookup"><span data-stu-id="01ca3-158">The app, built using Microsoft [Power Apps](/powerapps/powerapps-overview), and [Power Automate](/power-automate/getting-started), deeply integrates with Microsoft Teams and enables organizations to determine building readiness, establish eligibility criteria for on-site access, and gather insights for future planning.</span></span>

[<span data-ttu-id="01ca3-159">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-159">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-buildingaccess)

:::row:::
   :::column span="":::
     ![Cartão de reserva do Building Access](../assets/images/building-access-reservation.png)
   :::column-end:::
   :::column span="":::
      ![Criação de visualização de teclas do Access](../assets/images/building-access-access-key.png)
   :::column-end:::
:::row-end:::

## <a name="celebrations"></a><span data-ttu-id="01ca3-162">Celebrações</span><span class="sxs-lookup"><span data-stu-id="01ca3-162">Celebrations</span></span>

<span data-ttu-id="01ca3-163">Celebrações é um aplicativo do Teams que ajuda os membros da equipe a celebrar aniversários, datas de aniversário e outros eventos recorrentes entre si.</span><span class="sxs-lookup"><span data-stu-id="01ca3-163">Celebrations is a Teams app that helps team members celebrate each others' birthdays, anniversaries, and other recurring events.</span></span> <span data-ttu-id="01ca3-164">Ele lembra ocasiões especiais de todos os membros da equipe e envia uma mensagem amigável em todas as equipes selecionadas no momento da criação do evento, para fazer com que os membros da equipe se sintam especiais em seus dias.</span><span class="sxs-lookup"><span data-stu-id="01ca3-164">It remembers special occasions of all the team members and sends a friendly message in all the teams selected at the time of event creation, to make the team members feel special on their day.</span></span>

<span data-ttu-id="01ca3-165">O aplicativo fornece uma interface fácil para todos os membros da equipe adicionarem e exibirem seus eventos pessoalmente e também permitem que o usuário selecione as equipes nas quais os eventos são compartilhados.</span><span class="sxs-lookup"><span data-stu-id="01ca3-165">The app provides an easy interface for all the team members to personally add and view their events and also allows the user to select the teams in which the events gets shared.</span></span>

[<span data-ttu-id="01ca3-166">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-166">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-celebrations-app)

## <a name="checklist"></a><span data-ttu-id="01ca3-167">Lista de verificação</span><span class="sxs-lookup"><span data-stu-id="01ca3-167">Checklist</span></span>

<span data-ttu-id="01ca3-168">A lista de verificação é um aplicativo de extensão de mensagens personalizado do Microsoft [Teams](../messaging-extensions/what-are-messaging-extensions.md) que permite que você colabore com sua equipe criando uma lista de verificação compartilhada em um chat ou canal.</span><span class="sxs-lookup"><span data-stu-id="01ca3-168">Checklist is a custom Microsoft Teams [messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that enables you to collaborate with your team by creating a shared checklist in a chat or channel.</span></span> <span data-ttu-id="01ca3-169">O aplicativo tem suporte em todos os clientes da plataforma Teams — desktop, navegador, iOS e Android — e está pronto para implantação como parte da sua assinatura do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="01ca3-169">The app is supported across all Teams platform clients —  desktop, browser, iOS, and Android — and is ready for deployment as part of your Microsoft 365 subscription.</span></span>  

[<span data-ttu-id="01ca3-170">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-170">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-checklist-app )

:::row:::
:::column span="2":::
    ![Criar lista de verificação no visualização do Teams](../assets/images/checklist-app-template-compose-view.gif)  
:::column-end:::
:::row-end:::

## <a name="classroom-drop-in-9734"></a><span data-ttu-id="01ca3-172">Drop-in classroom &#9734;</span><span class="sxs-lookup"><span data-stu-id="01ca3-172">Classroom Drop-in &#9734;</span></span>

<span data-ttu-id="01ca3-173">O Drop-in sala de aula é um aplicativo baseado na Plataforma do Microsoft [Power Que](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/)permite que os líderes do sistema encontrem equipes de classe (salas de aula virtuais) e adicionem a si mesmos ou outras pessoas a essas equipes de classe por um período de lista de participantes especificado, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="01ca3-173">Classroom Drop-in is a Microsoft [Power Platform](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/)-based app that enables system leaders to find class teams (virtual classrooms) and add themselves or others to these class teams for a specified drop-in period, as needed.</span></span> <span data-ttu-id="01ca3-174">O aplicativo criado usando o Microsoft [Power Apps](/powerapps/powerapps-overview) e o [Power Automate](/power-automate/getting-started)se integra profundamente ao Microsoft Teams para garantir que as instituições educacionais possam otimizar suas operações em um ambiente de aprendizado híbrido, fornecendo acesso a participantes relevantes para equipes de classe de acordo com os requisitos de negócios.</span><span class="sxs-lookup"><span data-stu-id="01ca3-174">The app built using Microsoft [Power Apps](/powerapps/powerapps-overview) and [Power Automate](/power-automate/getting-started), deeply integrates with Microsoft Teams to ensure educational institutes can optimize their operations in a hybrid learning environment by providing access to relevant stakeholders for class teams per business requirements.</span></span>

[<span data-ttu-id="01ca3-175">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-175">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-classroom-dropin)

![Solicitação de lista de salas de aula](../assets/images/classroom-drop-in-request.png)

## <a name="company-communicator"></a><span data-ttu-id="01ca3-177">Communicator da empresa</span><span class="sxs-lookup"><span data-stu-id="01ca3-177">Company Communicator</span></span>

<span data-ttu-id="01ca3-178">O aplicativo Communicator da Empresa permite que as equipes corporativas criem e enviem mensagens destinadas a várias equipes ou a um grande número de funcionários por chat, permitindo que a organização alcance os funcionários exatamente onde eles colaboram.</span><span class="sxs-lookup"><span data-stu-id="01ca3-178">The Company Communicator app enables corporate teams to create and send messages intended for multiple teams or large number of employees over chat allowing organization to reach employees right where they collaborate.</span></span> <span data-ttu-id="01ca3-179">Utilize esse modelo para vários cenários, como novos anúncios de iniciativa, integração de funcionários, aprendizado e desenvolvimento modernos ou transmissões em toda a organização.</span><span class="sxs-lookup"><span data-stu-id="01ca3-179">Utilize this template for multiple scenarios such as new initiative announcements, employee onboarding, modern learning and development or organization-wide broadcasts.</span></span>

<span data-ttu-id="01ca3-180">O aplicativo fornece uma interface fácil para os usuários designados criarem, visualizarem, colaborarem e enviarem mensagens.</span><span class="sxs-lookup"><span data-stu-id="01ca3-180">The app provides an easy interface for designated users to create, preview, collaborate and send messages.</span></span>

<span data-ttu-id="01ca3-181">Ele fornece uma base para criar recursos personalizados de comunicação direcionada, como telemetria personalizada, sobre quantos usuários reconheceram ou interagiram com uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="01ca3-181">It provides a foundation to build custom targeted communication capabilities such as custom telemetry on how many users acknowledged or interacted with a message.</span></span>

[<span data-ttu-id="01ca3-182">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-182">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-company-communicator-app)

![jCompany Communicator compose box view](../assets/images/CompanyCommunicatorCompose.png)

## <a name="contact-group-lookup"></a><span data-ttu-id="01ca3-184">Contact Group Lookup</span><span class="sxs-lookup"><span data-stu-id="01ca3-184">Contact Group Lookup</span></span>

<span data-ttu-id="01ca3-185">O aplicativo De pesquisa de grupo de contatos fornece uma abordagem conveniente e útil para criar, acessar e gerenciar grupos de contatos da sua organização (anteriormente conhecidos como listas de distribuição ou grupos de comunicação).</span><span class="sxs-lookup"><span data-stu-id="01ca3-185">The Contact Group Lookup app provides a convenient and useful approach to creating, accessing, and managing your organization's contact groups (formerly known as distribution lists or communication groups).</span></span> <span data-ttu-id="01ca3-186">Os usuários podem exibir e conversar rapidamente com membros do grupo, exibir o status do membro e criar um chat em grupo com os membros selecionados no grupo de contatos, tudo no ambiente do Teams.</span><span class="sxs-lookup"><span data-stu-id="01ca3-186">Users can quickly view and chat with group members, view member status, and create a group chat with selected members in the contact group, all within the Teams environment.</span></span>

[<span data-ttu-id="01ca3-187">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-187">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-app-contactgrouplookup)

:::row:::
:::column span="2":::
    ![Exibição de favoritos fixados da Lookup de Grupo de Contatos](../assets/images/contact-group-lookup-favorites.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Demonstração de início do chat da Lookup de Grupo de Contatos](../assets/images/contact-group-lookup-chat.png)
:::column-end:::
:::row-end:::

## <a name="co-worker-appreciation-9734"></a><span data-ttu-id="01ca3-190">Co-funcionários e &#9734;</span><span class="sxs-lookup"><span data-stu-id="01ca3-190">Co-worker Appreciation &#9734;</span></span>

<span data-ttu-id="01ca3-191">Usando o modelo de reconhecimento de colegas de trabalho no Microsoft Teams, os usuários podem reconhecer as conquistas de seus colegas dentro do contexto do Teams.</span><span class="sxs-lookup"><span data-stu-id="01ca3-191">Using the co-worker appreciation template in Microsoft Teams, users can recognize their colleagues' achievements within the Teams’ context.</span></span> <span data-ttu-id="01ca3-192">Quando colegas de trabalho selecionam recompensar um colega, os destinatários e outros membros da equipe são marcados em uma conversa de canal e recebem uma notificação sobre os detalhes de prêmio do canal.</span><span class="sxs-lookup"><span data-stu-id="01ca3-192">When co-workers select to reward a colleague, recipients and other team members are tagged in a channel conversation and they receive a notification about the channel's award details.</span></span> <span data-ttu-id="01ca3-193">Os prêmio são gravados no aplicativo teams, que é seguro, portátil e facilmente compartilhável.</span><span class="sxs-lookup"><span data-stu-id="01ca3-193">The awards are recorded in the Teams app, which is secure, portable, and easily shareable.</span></span> <span data-ttu-id="01ca3-194">Isso pode ser considerado como a versão baseada no PowerApps do modelo de aplicativo Open Badges, com um placar de líderes.</span><span class="sxs-lookup"><span data-stu-id="01ca3-194">This can be considered as the PowerApps based version of the Open Badges app template, with a leaderboard.</span></span>

[<span data-ttu-id="01ca3-195">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-195">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-coworker-appreciation)

![Geral](../assets/images/coworker-appreciation-1.png)

## <a name="crowdsourcer"></a><span data-ttu-id="01ca3-197">CrowdSourcer</span><span class="sxs-lookup"><span data-stu-id="01ca3-197">CrowdSourcer</span></span>

<span data-ttu-id="01ca3-198">CrowdSourcer é um [bot do Microsoft Teams](../bots/what-are-bots.md) que fornece informações consultadas de forma colaborativa dos membros do grupo.</span><span class="sxs-lookup"><span data-stu-id="01ca3-198">CrowdSourcer is a [Microsoft Teams bot](../bots/what-are-bots.md) that gives teams queried information sourced collaboratively from group members.</span></span> <span data-ttu-id="01ca3-199">É uma ótima maneira de responder a perguntas frequentes, permitindo que os participantes se envolvam ativamente e contribuam com um recurso de informações divertido e útil.</span><span class="sxs-lookup"><span data-stu-id="01ca3-199">It's a great way to answer frequently asked questions while enabling participants to actively engage in and contribute to a fun and helpful information resource.</span></span>

[<span data-ttu-id="01ca3-200">Obter no Github</span><span class="sxs-lookup"><span data-stu-id="01ca3-200">Get it on Github</span></span>](https://github.com/OfficeDev/microsoft-teams-crowdsourcer-app)

![Interação do usuário final do Crowdsource](../assets/images/crowdsourcer.png)

## <a name="custom-stickers"></a><span data-ttu-id="01ca3-202">Adesivos personalizados</span><span class="sxs-lookup"><span data-stu-id="01ca3-202">Custom Stickers</span></span>

<span data-ttu-id="01ca3-203">A auto-expressão é fundamental para uma cultura de equipe saudável.</span><span class="sxs-lookup"><span data-stu-id="01ca3-203">Self-expression is core to a healthy team culture.</span></span> <span data-ttu-id="01ca3-204">Esse modelo de aplicativo é uma [extensão de mensagens](~/messaging-extensions/what-are-messaging-extensions.md) que permite que os usuários usem figurinhas personalizadas e GIFs no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="01ca3-204">This app template is a [messaging extension](~/messaging-extensions/what-are-messaging-extensions.md) that enables your users to use custom stickers and GIFs within Microsoft Teams.</span></span> <span data-ttu-id="01ca3-205">Esse modelo fornece uma experiência de configuração fácil baseada na Web em que qualquer pessoa com acesso à configuração pode carregar GIFs/figurinhas/imagens que eles querem que seus usuários finais tenham, permitindo que toda a sua equipe use qualquer conjunto de figurinhas que você escolher.</span><span class="sxs-lookup"><span data-stu-id="01ca3-205">This template provides an easy web-based configuration experience where anyone with configuration access can upload the GIFs/stickers/images they want their end-users to have, allowing your entire team to use any set of stickers you chose.</span></span>

<span data-ttu-id="01ca3-206">Esse aplicativo também permite o compartilhamento fácil de imagens/GIFs/figurinhas entre equipes sem precisar acessar sites do SharePoint ou canais individuais como mecanismos de armazenamento e compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="01ca3-206">This app also enables easy sharing of images/GIFs/stickers across teams without needing access to SharePoint sites or individual channels as storage and sharing mechanisms.</span></span> <span data-ttu-id="01ca3-207">Por exemplo, as equipes de produto podem compartilhar facilmente imagens de produtos e GIFs para redes sociais, equipes de marketing e vendas programaticamente.</span><span class="sxs-lookup"><span data-stu-id="01ca3-207">For example, product teams can easily share product images and GIFs to social media, marketing and sales teams programmatically.</span></span> <span data-ttu-id="01ca3-208">Também é possível estender esse aplicativo acionando um fluxo de notificação para equipes/indivíduos específicos quando novas imagens/GIFs são disponibilizadas.</span><span class="sxs-lookup"><span data-stu-id="01ca3-208">One can also extend this app by triggering a notification flow to specific teams/individuals when new images/GIFs are made available.</span></span>

[<span data-ttu-id="01ca3-209">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-209">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-stickers-app)

![App Figurinhas](../assets/images/stickers.png)

## <a name="employee-ideas-9734"></a><span data-ttu-id="01ca3-211">Ideias de funcionários &#9734;</span><span class="sxs-lookup"><span data-stu-id="01ca3-211">Employee Ideas &#9734;</span></span>

<span data-ttu-id="01ca3-212">O aplicativo Ideias de Funcionários é a versão do PowerApps do modelo de aplicativo Great Ideas baseado no Azure.</span><span class="sxs-lookup"><span data-stu-id="01ca3-212">The Employee Ideas app is the PowerApps version of the Azure based Great Ideas app template.</span></span> <span data-ttu-id="01ca3-213">O aplicativo permite que os usuários do Teams configurem e configurem uma campanha de ideias.</span><span class="sxs-lookup"><span data-stu-id="01ca3-213">The app enables the Teams users to set up and configure an idea campaign.</span></span> <span data-ttu-id="01ca3-214">Uma campanha de ideias é uma categoria para agrupar ideias em torno de temas comuns.</span><span class="sxs-lookup"><span data-stu-id="01ca3-214">An idea campaign is a category for grouping ideas around common themes.</span></span>

<span data-ttu-id="01ca3-215">Os usuários do Teams também podem realizar as seguintes atividades:</span><span class="sxs-lookup"><span data-stu-id="01ca3-215">Teams users can also perform following activities:</span></span>
* <span data-ttu-id="01ca3-216">Configure um formulário de envio padrão que os funcionários precisem enviar para cada ideia.</span><span class="sxs-lookup"><span data-stu-id="01ca3-216">Configure a standard submission form that employees need to submit for each idea.</span></span> 
* <span data-ttu-id="01ca3-217">Revise e gerencie as ideias e a lista de campanhas.</span><span class="sxs-lookup"><span data-stu-id="01ca3-217">Review and manage the ideas and list of campaigns.</span></span>
* <span data-ttu-id="01ca3-218">Modificar e excluir campanhas.</span><span class="sxs-lookup"><span data-stu-id="01ca3-218">Modify and delete campaigns.</span></span>
* <span data-ttu-id="01ca3-219">Revise os placares de líderes de ideias.</span><span class="sxs-lookup"><span data-stu-id="01ca3-219">Review leader boards of ideas.</span></span>
* <span data-ttu-id="01ca3-220">Vote e compartilhe ideias priorizadas.</span><span class="sxs-lookup"><span data-stu-id="01ca3-220">Vote for and share prioritized ideas.</span></span>
* <span data-ttu-id="01ca3-221">Envie ideias para uma campanha.</span><span class="sxs-lookup"><span data-stu-id="01ca3-221">Submit ideas for a campaign.</span></span>
* <span data-ttu-id="01ca3-222">Exibir a ideia de outro membro da equipe.</span><span class="sxs-lookup"><span data-stu-id="01ca3-222">View other team member's idea.</span></span>
* <span data-ttu-id="01ca3-223">Vote na maioria das ideias curtidas.</span><span class="sxs-lookup"><span data-stu-id="01ca3-223">Vote on most liked ideas.</span></span>
* <span data-ttu-id="01ca3-224">Revise o desempenho de suas ideias em comparação com outras pessoas em uma campanha.</span><span class="sxs-lookup"><span data-stu-id="01ca3-224">Review the performance of their ideas compared with others within a campaign.</span></span>

[<span data-ttu-id="01ca3-225">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-225">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-employeeideas)

![Gerenciar exibição de campanha](../assets/images/employee-ideas-manage-campaigns.png) 

## <a name="e-prescriptions"></a><span data-ttu-id="01ca3-227">Prescrições E</span><span class="sxs-lookup"><span data-stu-id="01ca3-227">E-Prescriptions</span></span> 

<span data-ttu-id="01ca3-228">Prescrições E é um aplicativo baseado em [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app)que melhora a telemedicina e os cuidados virtuais automatizando o processo de emissão de prescrições para pacientes.</span><span class="sxs-lookup"><span data-stu-id="01ca3-228">E-Prescriptions is a [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app)-based app that enhances telemedicine and virtual care by automating the process of issuing e-prescriptions to patients.</span></span> <span data-ttu-id="01ca3-229">Os profissionais médicos podem revisar rapidamente os compromissos, gerar prescrições e enviar emails com anexos de prescrição de e-mail aos pacientes diretamente na plataforma do Teams.</span><span class="sxs-lookup"><span data-stu-id="01ca3-229">Medical professionals can quickly review appointments, generate e-prescriptions, and send emails with e-prescription attachments to patients directly within the Teams platform.</span></span>

[<span data-ttu-id="01ca3-230">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-230">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-eprescription) 

:::row:::
:::column span="2":::
    ![Captura de tela do aplicativo E-Prescrições.](../assets/images/e-prescriptions-app-template.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Captura de tela do aplicativo E-Prescrições.](../assets/images/e-prescriptions-app-template-admin.png)
:::column-end:::
:::row-end:::


## <a name="emergency-button-power-9734"></a><span data-ttu-id="01ca3-235">Power &#9734;</span><span class="sxs-lookup"><span data-stu-id="01ca3-235">Emergency Button Power &#9734;</span></span>

<span data-ttu-id="01ca3-236">O aplicativo De energia do botão de emergência pode ser usado por organizações que estão usando o Microsoft Teams para permitir que qualquer conjunto de usuários solicite assistência de supervisores.</span><span class="sxs-lookup"><span data-stu-id="01ca3-236">The Emergency Button Power app can be used by organizations that are using Microsoft Teams, to enable any set of users to request assistance from supervisors.</span></span> <span data-ttu-id="01ca3-237">Esse aplicativo inclui vários recursos, como:</span><span class="sxs-lookup"><span data-stu-id="01ca3-237">This app includes various features, such as:</span></span>
-   <span data-ttu-id="01ca3-238">Solicitar assistência em diferentes categorias de um Power App</span><span class="sxs-lookup"><span data-stu-id="01ca3-238">Requesting assistance on different categories from a Power App</span></span>
-   <span data-ttu-id="01ca3-239">Notificações enviadas aos solicitadores informando quem foi atribuído</span><span class="sxs-lookup"><span data-stu-id="01ca3-239">Notifications sent to requestors informing them of who has been assigned</span></span> 
-   <span data-ttu-id="01ca3-240">Notificações enviadas a supervisores atribuídos informando sobre quem precisa de assistência</span><span class="sxs-lookup"><span data-stu-id="01ca3-240">Notifications sent to assigned supervisors informing them of who needs assistance</span></span> 
-   <span data-ttu-id="01ca3-241">Exibindo trilhas de auditoria mantidas no SharePoint</span><span class="sxs-lookup"><span data-stu-id="01ca3-241">Viewing audit trails held in SharePoint</span></span>

[<span data-ttu-id="01ca3-242">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-242">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-emergency-button-app)


## <a name="employee-training"></a><span data-ttu-id="01ca3-243">Treinamento de funcionários</span><span class="sxs-lookup"><span data-stu-id="01ca3-243">Employee Training</span></span> 

<span data-ttu-id="01ca3-244">O treinamento de funcionários é um aplicativo do Microsoft Teams que permite que os organizadores publiquem, acompanhem e promovam facilmente eventos de aprendizagem e treinamento para sua organização.</span><span class="sxs-lookup"><span data-stu-id="01ca3-244">Employee training is a Microsoft Teams app that enables organizers to easily publish,  track, and promote learning and training events for your organization.</span></span>  <span data-ttu-id="01ca3-245">Com o aplicativo, os planejadores de eventos podem enviar lembretes e notificações a registrants de eventos e os funcionários podem indicar interesse em eventos futuros, manter-se atualizado sobre eventos atuais e compartilhar detalhes do evento com colegas por meio da extensão de mensagens do Teams.</span><span class="sxs-lookup"><span data-stu-id="01ca3-245">With the app, event planners can send reminders and notifications to event registrants and employees can indicate interest in upcoming events, stay updated on current events, and share event details with colleagues via the Teams messaging extension.</span></span>

[<span data-ttu-id="01ca3-246">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-246">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-employeetraining)

:::row:::
:::column span="2":::
    <span data-ttu-id="01ca3-247">**Exibir eventos de treinamento de funcionários** ![ Imagem da guia treinamento de funcionários](../assets/images/employee-training-discover-tab.png)</span><span class="sxs-lookup"><span data-stu-id="01ca3-247">**View employee training events** ![Employee training tab image](../assets/images/employee-training-discover-tab.png)</span></span>  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    <span data-ttu-id="01ca3-248">**Criar evento de treinamento de funcionários** ![ Employee training create event form](../assets/images/employee-training-create-event.jpg)</span><span class="sxs-lookup"><span data-stu-id="01ca3-248">**Create employee training event** ![Employee training create event form](../assets/images/employee-training-create-event.jpg)</span></span>
:::column-end:::
:::row-end:::

## <a name="expert-finder"></a><span data-ttu-id="01ca3-249">Expert Finder</span><span class="sxs-lookup"><span data-stu-id="01ca3-249">Expert Finder</span></span>

<span data-ttu-id="01ca3-250">O Expert Finder é um [bot do Microsoft Teams](../bots/what-are-bots.md) que identifica membros específicos da organização com base em suas habilidades, interesses e atributos de educação.</span><span class="sxs-lookup"><span data-stu-id="01ca3-250">Expert Finder is a [Microsoft Teams bot](../bots/what-are-bots.md) that identifies specific organization members based on their skills, interests, and education attributes.</span></span> <span data-ttu-id="01ca3-251">Os membros encontram especialistas em uma organização que corresponderem a uma pesquisa de palavra-chave de perfis de usuário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="01ca3-251">Members find experts within an organization  that match a keyword search of Azure Active Directory user profiles.</span></span>

[<span data-ttu-id="01ca3-252">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-252">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-expertfinder)

![Demonstração dos resultados da pesquisa do Expert Finder](../assets/images/expert-finder.png)

## <a name="faq-plus"></a><span data-ttu-id="01ca3-254">Perguntas Frequentes Plus</span><span class="sxs-lookup"><span data-stu-id="01ca3-254">FAQ Plus</span></span>

<span data-ttu-id="01ca3-255">Os bots de P e&conversa são uma maneira fácil de fornecer respostas a perguntas frequentes feita pelos usuários.</span><span class="sxs-lookup"><span data-stu-id="01ca3-255">Conversational Q&A bots are an easy way to provide answers to frequently asked questions by users.</span></span> <span data-ttu-id="01ca3-256">No entanto, a maioria dos bots falha ao interagir com os usuários de maneira significativa porque não há humanos no loop quando o bot falha.</span><span class="sxs-lookup"><span data-stu-id="01ca3-256">However, most bots fail to engage with users in meaningful way because there is no human in the loop when the bot fails.</span></span> <span data-ttu-id="01ca3-257">O bot de perguntas frequentes é&um bot que traz uma pessoa ao loop quando não consegue ajudar.</span><span class="sxs-lookup"><span data-stu-id="01ca3-257">FAQ bot is a friendly Q&A bot that brings a human in the loop when it is unable to help.</span></span> <span data-ttu-id="01ca3-258">É possível fazer uma pergunta ao bot e o bot responderá com uma resposta se ele estiver contido na base de dados de conhecimento.</span><span class="sxs-lookup"><span data-stu-id="01ca3-258">One can ask the bot a question and the bot responds with an answer if it is contained in the knowledge base.</span></span> <span data-ttu-id="01ca3-259">Caso não seja, o bot permite que o usuário envie uma consulta que, em seguida, é postada para uma equipe pré-configurada de especialistas que ajudam a fornecer suporte agindo sobre as notificações de dentro da própria equipe.</span><span class="sxs-lookup"><span data-stu-id="01ca3-259">If not, the bot allows the user to submit a query which then gets posted to a pre-configured team of experts who help to provide support by acting upon the notifications from within the team itself.</span></span>

> [!NOTE]
> <span data-ttu-id="01ca3-260">A versão mais recente do **FaQ Plus** oferece suporte a resoluções de perguntas e&A aprimoradas, permitindo que uma equipe de especialistas conclua o seguinte:</span><span class="sxs-lookup"><span data-stu-id="01ca3-260">The latest release of **FAQ Plus** supports improved Q&A resolutions by enabling a team of experts to complete the following:</span></span>
>
> <span data-ttu-id="01ca3-261">&#x2714; adicionar novas perguntas&Como diretamente à base de dados de conhecimento usando extensões de mensagem.</span><span class="sxs-lookup"><span data-stu-id="01ca3-261">&#x2714; Add new Q&As directly to the knowledge base using message extensions.</span></span>
>
> <span data-ttu-id="01ca3-262">&#x2714; Editar e excluir pares de&A adicionados por um bot.</span><span class="sxs-lookup"><span data-stu-id="01ca3-262">&#x2714; Edit and delete Q&A pairs added by a bot.</span></span>
>
> <span data-ttu-id="01ca3-263">&#x2714; Controlar o histórico de revisão de P&As.</span><span class="sxs-lookup"><span data-stu-id="01ca3-263">&#x2714; Track the revision history of Q&As.</span></span>
>
> <span data-ttu-id="01ca3-264">&#x2714; configurar uma resposta com detalhes adicionais para exibir como um [cartão adaptável.](../task-modules-and-cards/cards/cards-reference.md#adaptive-card)</span><span class="sxs-lookup"><span data-stu-id="01ca3-264">&#x2714; Configure an answer with additional details to display as an [adaptive card](../task-modules-and-cards/cards/cards-reference.md#adaptive-card).</span></span>
>
[<span data-ttu-id="01ca3-265">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-265">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-faqplusv2)

![Gif de Perguntas Frequentes Plus](../assets/images/FAQPlusEndUser.gif)

## <a name="goal-tracker"></a><span data-ttu-id="01ca3-267">Goal Tracker</span><span class="sxs-lookup"><span data-stu-id="01ca3-267">Goal Tracker</span></span>

<span data-ttu-id="01ca3-268">O aplicativo Goal Tracker é uma solução abrangente para sua organização dar suporte ao estabelecimento de metas, observar o progresso e confirmar o sucesso no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="01ca3-268">The Goal Tracker app is a comprehensive solution for your organization to support establishing goals, observing progress, and acknowledging success within Microsoft Teams.</span></span> <span data-ttu-id="01ca3-269">O aplicativo permite aos usuários definir, acompanhar e atualizar objetivos em nível profissional, pessoal e de equipe.</span><span class="sxs-lookup"><span data-stu-id="01ca3-269">The app enables users to set, track, and update objectives on a professional, personal, and team level.</span></span> <span data-ttu-id="01ca3-270">Os membros da equipe também recebem lembretes e atualizações de status o mais rápido possível para permanecerem focados e se manterem no controle.</span><span class="sxs-lookup"><span data-stu-id="01ca3-270">Team members also receive timely reminders and status updates to remain focused and stay on track.</span></span>

[<span data-ttu-id="01ca3-271">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-271">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-app-goaltracker)

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

## <a name="great-ideas"></a><span data-ttu-id="01ca3-274">Ótimas ideias</span><span class="sxs-lookup"><span data-stu-id="01ca3-274">Great Ideas</span></span>

<span data-ttu-id="01ca3-275">O aplicativo Great Ideas dá suporte e capacita a inovação e a criatividade em sua organização.</span><span class="sxs-lookup"><span data-stu-id="01ca3-275">The Great Ideas app supports and empowers innovation and creativity within your organization.</span></span> <span data-ttu-id="01ca3-276">O aplicativo permite que seus funcionários compartilhem ideias com colegas e lideranças, descubram novos envios, destaquem as contribuições para consideração do par e votem pelas melhores propostas no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="01ca3-276">The app enables your employees to share ideas with colleagues and leadership, discover new submissions, spotlight contributions for peer consideration, and cast their vote for the best proposals within Microsoft Teams.</span></span>

[<span data-ttu-id="01ca3-277">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-277">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-greatideas)

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

## <a name="group-activities"></a><span data-ttu-id="01ca3-280">Atividades de grupo</span><span class="sxs-lookup"><span data-stu-id="01ca3-280">Group Activities</span></span>

<span data-ttu-id="01ca3-281">Atividades de grupo é um aplicativo do Microsoft Teams que torna mais fácil para os proprietários de equipe criar rapidamente grupos de atividades e gerenciar fluxos de trabalho de colaboração dentro do contexto do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="01ca3-281">Group Activities is a Microsoft Teams app that makes it easy for team owners to quickly create activity groups and manage collaboration workflows within the context of Microsoft Teams.</span></span> <span data-ttu-id="01ca3-282">Os autores de atividades são habilitados para criar atividades, distribuir aleatoriamente membros da equipe em grupos e, opcionalmente, fazer com que o bot envie lembretes até que as atividades sejam concluídas.</span><span class="sxs-lookup"><span data-stu-id="01ca3-282">Activity authors are enabled to create activities, randomly distribute team members in groups, and optionally have the bot send reminders until activities are complete.</span></span>

[<span data-ttu-id="01ca3-283">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-283">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-groupactivities)

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

## <a name="grow-your-skills"></a><span data-ttu-id="01ca3-286">Aumentar suas habilidades</span><span class="sxs-lookup"><span data-stu-id="01ca3-286">Grow Your Skills</span></span>

<span data-ttu-id="01ca3-287">O aplicativo Crescer suas Habilidades dá suporte ao crescimento e desenvolvimento profissional, permitindo que os funcionários contribuam com projetos suplementares para sua organização enquanto aprendem simultaneamente novas habilidades.</span><span class="sxs-lookup"><span data-stu-id="01ca3-287">The Grow Your Skills app supports professional growth and development by enabling employees to contribute to supplemental projects for your organization while simultaneously learning new skills.</span></span> <span data-ttu-id="01ca3-288">Os funcionários podem usar o aplicativo para localizar oportunidades que atendem aos seus interesses, aproveitar uma colaboração significativa com colegas e adquirir novos níveis de experiência e recursos, tudo isso no ambiente do Teams.</span><span class="sxs-lookup"><span data-stu-id="01ca3-288">Employees can use the app to locate opportunities that meet their interests, enjoy meaningful collaboration with peers, and acquire new levels of expertise and capabilities, all within the Teams environment.</span></span>

[<span data-ttu-id="01ca3-289">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-289">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-growyourskills)

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

## <a name="hr-support"></a><span data-ttu-id="01ca3-292">Suporte de RH</span><span class="sxs-lookup"><span data-stu-id="01ca3-292">HR Support</span></span>

<span data-ttu-id="01ca3-293">O bot de Suporte de RH é um bot de perguntas e&um bot que traz um profissional de suporte/especialista da equipe de RH no loop quando não consegue ajudar.</span><span class="sxs-lookup"><span data-stu-id="01ca3-293">HR Support bot is a friendly Q&A bot that brings a support professional/expert from the HR team in the loop when it is unable to help.</span></span> <span data-ttu-id="01ca3-294">É possível fazer uma pergunta ao bot e o bot responderá com uma resposta se ele estiver contido na base de dados de conhecimento.</span><span class="sxs-lookup"><span data-stu-id="01ca3-294">One can ask the bot a question and the bot responds with an answer if it is contained in the knowledge base.</span></span> <span data-ttu-id="01ca3-295">Caso não seja, o bot permite que o usuário envie uma consulta que, em seguida, é postada em uma equipe pré-configurada de especialistas que ajudam a fornecer suporte agindo sobre as notificações de dentro da própria equipe.</span><span class="sxs-lookup"><span data-stu-id="01ca3-295">If not, the bot allows the user to submit a query which then gets posted in a pre-configured team of experts who are help to provide support by acting upon the notifications from within their team itself.</span></span> <span data-ttu-id="01ca3-296">Além disso, o bot sugere links para políticas/perguntas de RH recomendadas pesquisando por marcas pré-configuradas na pergunta.</span><span class="sxs-lookup"><span data-stu-id="01ca3-296">Additionally, the bot suggests links to recommended HR policies/questions by searching for pre-configured tags in the question.</span></span> <span data-ttu-id="01ca3-297">Esses blocos também podem ser encontrados na guia associada como uma referência rápida.</span><span class="sxs-lookup"><span data-stu-id="01ca3-297">These tiles can also be found in the associated tab as a quick reference.</span></span> <span data-ttu-id="01ca3-298">O Suporte de RH funciona bem para QnA leve e para fornecer suporte rápido ao iniciar novos projetos/iniciativas na organização.</span><span class="sxs-lookup"><span data-stu-id="01ca3-298">HR Support works well for light weight QnA and to provide quick support when launching new projects/initiatives in the organization.</span></span>

[<span data-ttu-id="01ca3-299">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-299">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-hrsupport-app)

![Suporte de RH](../assets/images/expert-user.png)

## <a name="icebreaker"></a><span data-ttu-id="01ca3-301">Frases de apresentação</span><span class="sxs-lookup"><span data-stu-id="01ca3-301">Icebreaker</span></span>

<span data-ttu-id="01ca3-302">O Icebreaker é um [bot do Microsoft Teams](../bots/what-are-bots.md) que ajuda sua equipe a se aproximar emparelhando dois membros aleatórios da equipe a cada semana para se reunirem.</span><span class="sxs-lookup"><span data-stu-id="01ca3-302">Icebreaker is a [Microsoft Teams bot](../bots/what-are-bots.md) that helps your team get closer by pairing two random team members up every week to meet.</span></span> <span data-ttu-id="01ca3-303">O bot facilita o agendamento sugerindo automaticamente horários gratuitos que funcionam para ambos os membros.</span><span class="sxs-lookup"><span data-stu-id="01ca3-303">The bot makes scheduling easy by automatically suggesting free times that work for both members.</span></span> <span data-ttu-id="01ca3-304">Fortalece as conexões pessoais e crie uma comunidade fortemente rígida com esse aplicativo.</span><span class="sxs-lookup"><span data-stu-id="01ca3-304">Strengthen personal connections and build a tightly knit community with this app.</span></span>

<span data-ttu-id="01ca3-305">Além de incentivar conexões pessoais em toda a sua equipe, o aplicativo Icebreaker pode ajudar a promover comunidades baseadas em interesse em sua organização.</span><span class="sxs-lookup"><span data-stu-id="01ca3-305">In addition to encouraging personal connections across your entire team, the Icebreaker app can help cultivate interest-based communities within your organization.</span></span> <span data-ttu-id="01ca3-306">Por exemplo, você pode usar esse aplicativo para um grupo de interesse de DevOps para ajudar ideias e práticas recomendadas propagadas organicamente em toda a organização.</span><span class="sxs-lookup"><span data-stu-id="01ca3-306">For example, you can use this app for a DevOps interest group to help ideas and best practices organically spread across your organization.</span></span>

[<span data-ttu-id="01ca3-307">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-307">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-icebreaker-app)

![Aplicativo Icebreaker](../assets/images/icebreaker.png)

## <a name="incentives"></a><span data-ttu-id="01ca3-309">Incentivos</span><span class="sxs-lookup"><span data-stu-id="01ca3-309">Incentives</span></span>

<span data-ttu-id="01ca3-310">Incentivos é um modelo [do Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) que gerencia e acompanha a participação incentivada dos funcionários em atividades designadas, como treinamentos e iniciativas de gerenciamento de mudanças.</span><span class="sxs-lookup"><span data-stu-id="01ca3-310">Incentives is a [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) template that manages and tracks incentivized employee participation in designated activities such as trainings and change management initiatives.</span></span> <span data-ttu-id="01ca3-311">Os administradores usam o aplicativo para estabelecer atividades designadas, atribuir pontos para conclusão e especificar níveis de ponto de qualificação necessários para recompensas.</span><span class="sxs-lookup"><span data-stu-id="01ca3-311">Admins use the app to establish designated activities, assign points for completion, and specify required eligibility point levels for rewards.</span></span> <span data-ttu-id="01ca3-312">Os funcionários usam o aplicativo para exibir seus pontos acumulados e, ao atingirem a qualificação, solicitar e reivindicar recompensas resgatáveis.</span><span class="sxs-lookup"><span data-stu-id="01ca3-312">Employees use the app to view their accumulated points and, upon reaching eligibility, request and claim redeemable rewards.</span></span>

[<span data-ttu-id="01ca3-313">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-313">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-incentives)

![Demonstração de aplicativo de incentivos](../assets/images/incentives-app.png)

## <a name="incident-reporter"></a><span data-ttu-id="01ca3-315">Incident Reporter</span><span class="sxs-lookup"><span data-stu-id="01ca3-315">Incident Reporter</span></span>

<span data-ttu-id="01ca3-316">O Incident Reporter é um [bot do Microsoft Teams](../bots/what-are-bots.md)  que otimiza o gerenciamento de incidentes em sua organização.</span><span class="sxs-lookup"><span data-stu-id="01ca3-316">Incident Reporter is a [Microsoft Teams bot](../bots/what-are-bots.md)  that optimizes the management of incidents in your organization.</span></span> <span data-ttu-id="01ca3-317">O bot facilita a coleta automatizada de dados de incidentes, relatórios de incidentes personalizados, notificações relevantes de participantes e controle de incidentes de ponta a ponta.</span><span class="sxs-lookup"><span data-stu-id="01ca3-317">The bot facilitates automated incident data collection, customized incident reports, relevant stakeholder notifications, and end-to-end incident tracking.</span></span>

[<span data-ttu-id="01ca3-318">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-318">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-incidentreport)

:::row:::
  :::column span="2":::
    ![Exibição de escopo do grupo de relatório de incidentes](../assets/images/incident-reporter-02.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Exibição de escopo pessoal do relatório de incidentes](../assets/images/incident-reporter-01.jpg)
:::column-end:::
:::row-end:::

## <a name="inspection-9734"></a><span data-ttu-id="01ca3-321">Inspeção &#9734;</span><span class="sxs-lookup"><span data-stu-id="01ca3-321">Inspection &#9734;</span></span>

 <span data-ttu-id="01ca3-322">Inspeção é um aplicativo do Microsoft Teams que permite que os funcionários de linha de frente inspecionem tudo, desde locais até ativos e equipamentos.</span><span class="sxs-lookup"><span data-stu-id="01ca3-322">Inspection is a Microsoft Teams app that enables front line workers to inspect anything from  locations to assets and equipments.</span></span> <span data-ttu-id="01ca3-323">Por exemplo, uma loja de varejo, fábrica de manufatura ou veículos e máquinas.</span><span class="sxs-lookup"><span data-stu-id="01ca3-323">For example, a retail store, manufacturing plant, or vehicles and machines.</span></span> <span data-ttu-id="01ca3-324">Há dois aplicativos nesta solução, cada um destinado a tipos diferentes de usuários.</span><span class="sxs-lookup"><span data-stu-id="01ca3-324">There are two apps in this solution, each intended for different types of users.</span></span>

<span data-ttu-id="01ca3-325">O aplicativo permite que os funcionários de linha de frente inspecionem um ativo ou área, gerenciem a qualidade de produtos e serviços ou mantenham a segurança no local de trabalho.</span><span class="sxs-lookup"><span data-stu-id="01ca3-325">The app empowers the front line workers to inspect an asset or area, to manage quality of products and services, or maintain safety at workplace.</span></span> <span data-ttu-id="01ca3-326">Ela facilita a comunicação entre os membros da equipe para resolver problemas encontrados durante a inspeção.</span><span class="sxs-lookup"><span data-stu-id="01ca3-326">It facilitates communication between team members to address issues found during inspection.</span></span> <span data-ttu-id="01ca3-327">O aplicativo fornece relatórios simples para que os gerentes agilizarem a resolução de problemas e realçam as tendências.</span><span class="sxs-lookup"><span data-stu-id="01ca3-327">The app provides simple reports for managers to expedite issue resolution and highlight trends.</span></span>

[<span data-ttu-id="01ca3-328">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-328">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-inspection)

 ![Visão geral da inspeção](../assets/images/inspection-app.png)  


## <a name="issue-reporting-9734"></a><span data-ttu-id="01ca3-330">Relatório de problemas &#9734;</span><span class="sxs-lookup"><span data-stu-id="01ca3-330">Issue Reporting &#9734;</span></span>

<span data-ttu-id="01ca3-331">O aplicativo Relatório de Problemas capacita os funcionários e gerentes a criar e gerenciar problemas.</span><span class="sxs-lookup"><span data-stu-id="01ca3-331">The Issue Reporting app empowers the employees and managers to raise and manage issues.</span></span> <span data-ttu-id="01ca3-332">Ele consiste em dois aplicativos, o aplicativo Emitir relatórios para relatar problemas e o aplicativo Gerenciar Problemas para gerenciar problemas.</span><span class="sxs-lookup"><span data-stu-id="01ca3-332">It consists of two apps, Issue reporting app for reporting issues and Manage Issues app for managing issues.</span></span>

<span data-ttu-id="01ca3-333">Os gerentes de equipe usam o aplicativo Gerenciar Problemas para configurar a experiência do aplicativo, incluindo o canal no qual as mensagens do Microsoft Teams e as tarefas do Planner são criadas pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="01ca3-333">The team managers use the Manage Issues app to configure the app experience, including the channel in which Microsoft Teams messages and Planner tasks are created by the app.</span></span> <span data-ttu-id="01ca3-334">Os gerentes também usam o aplicativo para criar formulários de modelo para coletar detalhes quando um usuário relata um problema.</span><span class="sxs-lookup"><span data-stu-id="01ca3-334">Managers also use the app to create template forms to collect details when a user reports an issue.</span></span> <span data-ttu-id="01ca3-335">Por exemplo, revise, edite ou exclua formulários de modelo de problema.</span><span class="sxs-lookup"><span data-stu-id="01ca3-335">For example, review, edit, or delete issue template forms.</span></span> <span data-ttu-id="01ca3-336">O aplicativo também pode ser usado para revisar problemas da equipe, relatar o histórico de problemas e gerenciar com eficiência a resolução de problemas.</span><span class="sxs-lookup"><span data-stu-id="01ca3-336">The app can also be used to review team issues, report on issue history, and efficiently manage issue resolution.</span></span>

<span data-ttu-id="01ca3-337">Os funcionários usam o aplicativo Relatório de Problemas para registrar problemas e detalhes necessários para resolvê-los.</span><span class="sxs-lookup"><span data-stu-id="01ca3-337">The employees use the Issue reporting app to log issues and details required to resolve them.</span></span> <span data-ttu-id="01ca3-338">O aplicativo também é usado para modificar e resolver problemas existentes e obter uma visão de alto nível de problemas individuais ou da equipe.</span><span class="sxs-lookup"><span data-stu-id="01ca3-338">The app is also used to modify and resolve existing issues and get a high-level view of individual or team issues.</span></span>

[<span data-ttu-id="01ca3-339">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-339">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-issuereporting)

![Visão da equipe de relatórios de problemas](../assets/images/issue-reporting-team-view.png)  

## <a name="new-employee-onboarding"></a><span data-ttu-id="01ca3-341">Integração de novos funcionários</span><span class="sxs-lookup"><span data-stu-id="01ca3-341">New Employee Onboarding</span></span> 

<span data-ttu-id="01ca3-342">A Integração de Novos Funcionários é uma Solução integrada de Integração de Novos Funcionários do Microsoft Teams e do [SharePoint](https://lookbook.microsoft.com/details/75e60a32-9849-4ed4-b83e-b2b08983ad19) que permite que sua organização forneça uma experiência de integração consistente e de alta qualidade para os funcionários em sua jornada de novos contratados.</span><span class="sxs-lookup"><span data-stu-id="01ca3-342">New Employee Onboarding is an integrated Microsoft Teams and [SharePoint New Employee Onboarding Solution](https://lookbook.microsoft.com/details/75e60a32-9849-4ed4-b83e-b2b08983ad19) that enables your organization to provide a consistent, high-quality onboarding experience for employees on their new-hire journey.</span></span> <span data-ttu-id="01ca3-343">O aplicativo pode ser usado por equipes de recursos humanos e gerentes de contratação para fornecer informações relevantes durante todo o processo de orientação e avaliação e por novos contratados para compartilhar comentários, fornecer introduções e concluir tarefas de integração.</span><span class="sxs-lookup"><span data-stu-id="01ca3-343">The app can be used by human resource teams and hiring managers to provide relevant information throughout the orientation and induction process and by new hires to share feedback, provide introductions, and complete onboarding tasks.</span></span>

[<span data-ttu-id="01ca3-344">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-344">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-newemployeeonboarding)

:::row:::
  :::column span="2":::
    <span data-ttu-id="01ca3-345">**Cartão de boas-vindas do novo funcionário** ![ Imagem do cartão de boas-vindas do novo funcionário](../assets/images/new-employee-welcome-card.png)</span><span class="sxs-lookup"><span data-stu-id="01ca3-345">**New employee welcome card** ![Image of new employee welcome card](../assets/images/new-employee-welcome-card.png)</span></span>
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    <span data-ttu-id="01ca3-346">**Lista de verificação de novos funcionários** ![ Imagem da lista de verificação de novos funcionários](../assets/images/new-employee-checklist.png)</span><span class="sxs-lookup"><span data-stu-id="01ca3-346">**New employee checklist** ![Image of new employee checklist](../assets/images/new-employee-checklist.png)</span></span>  
:::column-end:::
:::row-end:::

## <a name="open-badges"></a><span data-ttu-id="01ca3-347">Selos abertos</span><span class="sxs-lookup"><span data-stu-id="01ca3-347">Open Badges</span></span>

<span data-ttu-id="01ca3-348">Selos Abertos é um aplicativo do Microsoft Teams que permite que as pessoas ganhem selos de credenciais de aprendizagem digital dentro do contexto do Teams e compartilhem-os em todos os lugares.</span><span class="sxs-lookup"><span data-stu-id="01ca3-348">Open Badges is a Microsoft Teams app that enables individuals to earn digital learning credential badges within the Teams context and share them everywhere.</span></span> <span data-ttu-id="01ca3-349">Usando recursos da autoridade de emissão de selos digitais de terceiros, [Badgr](https://badgr.org/), selos concedidos são registrados no perfil Badgr de um destinatário e disponíveis para criar e compartilhar uma imagem rica de jornadas de aprendizagem do tempo de vida.</span><span class="sxs-lookup"><span data-stu-id="01ca3-349">Using capabilities from the third-party digital badge issuing authority, [Badgr](https://badgr.org/), awarded badges are recorded in a recipient's Badgr profile and available to build and share a rich picture of lifetime learning journeys.</span></span>

[<span data-ttu-id="01ca3-350">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-350">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-openbadges)

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

## <a name="poll"></a><span data-ttu-id="01ca3-353">Sondagem</span><span class="sxs-lookup"><span data-stu-id="01ca3-353">Poll</span></span> 

<span data-ttu-id="01ca3-354">O Poll é um aplicativo de extensão de mensagens personalizado do Microsoft [Teams](../messaging-extensions/what-are-messaging-extensions.md) que permite que você crie e envie votações rapidamente em um chat ou em um canal para coletar opiniões e preferências da equipe.</span><span class="sxs-lookup"><span data-stu-id="01ca3-354">Poll is a custom Microsoft Teams [messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that enables you to quickly create and send polls in a chat or a channel to gather team opinions and preferences.</span></span> <span data-ttu-id="01ca3-355">O aplicativo tem suporte em todos os clientes da plataforma Teams — desktop, navegador, iOS e Android — e está pronto para implantação como parte da sua assinatura do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="01ca3-355">The app is supported across all Teams platform clients — desktop, browser, iOS, and Android  — and is ready for deployment as part of your Microsoft 365 subscription.</span></span>

[<span data-ttu-id="01ca3-356">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-356">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-poll-app)

:::row:::
  :::column span="1":::
    ![Criar votação no visualização do Teams](../assets/images/poll-app-template-compose-view.gif)  
:::column-end:::
:::row-end:::

## <a name="quick-responses"></a><span data-ttu-id="01ca3-358">Respostas rápidas</span><span class="sxs-lookup"><span data-stu-id="01ca3-358">Quick Responses</span></span>

<span data-ttu-id="01ca3-359">Respostas Rápidas é um aplicativo do Microsoft Teams que oferece uma solução robusta para responder com eficiência às perguntas frequentes (perguntas frequentes) frequentes dos usuários.</span><span class="sxs-lookup"><span data-stu-id="01ca3-359">Quick Responses is a Microsoft Teams app that delivers a robust solution for effectively answering users' commonly asked questions (FAQs).</span></span> <span data-ttu-id="01ca3-360">Em vez de responder cada consulta manualmente e continuamente repetindo informações, o aplicativo criará uma biblioteca de respostas para uma experiência interativa do usuário por meio de extensões de mensagens [do](../messaging-extensions/what-are-messaging-extensions.md)Teams.</span><span class="sxs-lookup"><span data-stu-id="01ca3-360">Instead of answering each query manually and  continuously repeating information, the app will build a library of responses for an interactive user experience via Teams [messaging extensions](../messaging-extensions/what-are-messaging-extensions.md).</span></span>

[<span data-ttu-id="01ca3-361">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-361">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-quickresponses)

![Exemplo de exibição de respostas](../assets/images/quick-responses.png)

## <a name="rapid-assist-9734"></a><span data-ttu-id="01ca3-363">Assistência Rápida &#9734;</span><span class="sxs-lookup"><span data-stu-id="01ca3-363">Rapid Assist &#9734;</span></span>

<span data-ttu-id="01ca3-364">A Assistência Rápida é um aplicativo baseado no Microsoft [Power Platform](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/) que permite que os associados voltados ao cliente se conectem rapidamente aos especialistas para obter respostas rápidas, pesquisar informações, acompanhar solicitações abertas e permitir que os especialistas recebam notificações para receber rapidamente uma chamada para ajudar a responder perguntas.</span><span class="sxs-lookup"><span data-stu-id="01ca3-364">Rapid Assist is a Microsoft [Power Platform](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/) based app that allows customer facing associates to rapidly connect with the experts to get quick answers, search for information, follow up open requests, and allow experts to receive notifications to quickly get on a call to help answer questions.</span></span> <span data-ttu-id="01ca3-365">O aplicativo criado usando o Microsoft [Power Apps](/powerapps/powerapps-overview) e o [Power Automate](/power-automate/getting-started)se integra profundamente ao Microsoft Teams para permitir que as organizações conectem facilmente funcionários de linha de frente com ligações corporativas para resolver consultas de clientes e proporcionar uma excelente experiência ao cliente.</span><span class="sxs-lookup"><span data-stu-id="01ca3-365">The app built using Microsoft [Power Apps](/powerapps/powerapps-overview) and [Power Automate](/power-automate/getting-started), deeply integrates with Microsoft Teams to enable organizations to easily connect frontline workers with corporate liaisons to resolve customer queries and deliver a great customer experience.</span></span> 

[<span data-ttu-id="01ca3-366">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-366">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-rapid-assist)

:::row:::
   :::column span="":::
     ![Interface de solicitação do usuário final](../assets/images/EndUserHome.png)
   :::column-end:::
   :::column span="":::
      ![Exibição de solicitação de especialista](../assets/images/ExpertViewRequests.png)
   :::column-end:::
:::row-end:::

## <a name="reflect"></a><span data-ttu-id="01ca3-369">Refletir</span><span class="sxs-lookup"><span data-stu-id="01ca3-369">Reflect</span></span> 

<span data-ttu-id="01ca3-370">O Reflect é um aplicativo de extensão de mensagens personalizado do Microsoft [Teams](../messaging-extensions/what-are-messaging-extensions.md) que fornece um recurso seguro e inclusivo para que os membros da equipe compartilhem o estado de bem-estar delas com colegas e/ou líderes de grupo diretamente no Teams.</span><span class="sxs-lookup"><span data-stu-id="01ca3-370">Reflect is a custom Microsoft Teams [messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that provides a safe and inclusive resource for your team members to share the state of their emotional well-being with colleagues and/or group leaders directly within Teams.</span></span> <span data-ttu-id="01ca3-371">O aplicativo está disponível em chats de canal, grupo, reunião e 1:1, e a resposta de check-in pode ser definida como pública, privada para remetente ou totalmente anônima.</span><span class="sxs-lookup"><span data-stu-id="01ca3-371">The app is available in channel, group, meeting, and 1:1 chats and the check-in response can be set to public, private-to-sender, or fully anonymous.</span></span>

[<span data-ttu-id="01ca3-372">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-372">Get it on GitHub</span></span>](https://github.com/OfficeDev/Microsoft-Teams-App-Reflect)

:::row:::
    :::column:::
    <span data-ttu-id="01ca3-373">**Sondagem de bem-estar**</span><span class="sxs-lookup"><span data-stu-id="01ca3-373">**Well-being poll**</span></span>
    
    ![Refletir sondagem do usuário do aplicativo](../assets/images/reflect-app-user-poll.png)
    :::column-end:::
:::row-end:::

## <a name="remote-support"></a><span data-ttu-id="01ca3-375">Suporte remoto</span><span class="sxs-lookup"><span data-stu-id="01ca3-375">Remote Support</span></span>

<span data-ttu-id="01ca3-376">O Suporte Remoto é um [bot do Microsoft Teams](../bots/what-are-bots.md) que fornece uma interface focada entre os solicitantes de suporte em toda a organização e a equipe de suporte interno.</span><span class="sxs-lookup"><span data-stu-id="01ca3-376">Remote Support is a [Microsoft Teams bot](../bots/what-are-bots.md) that provides a focused interface between support requesters throughout your organization and the internal support team.</span></span>  <span data-ttu-id="01ca3-377">Os usuários finais podem enviar, editar ou retirar solicitações de suporte, e a equipe de suporte pode responder, gerenciar e atualizar todas as solicitações dentro da plataforma do Teams.</span><span class="sxs-lookup"><span data-stu-id="01ca3-377">End-users can submit, edit, or withdraw requests for support and the support team can respond, manage, and update requests all within the Teams platform.</span></span>

[<span data-ttu-id="01ca3-378">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-378">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-remotesupport)

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

## <a name="request-a-team"></a><span data-ttu-id="01ca3-381">Request-a-team</span><span class="sxs-lookup"><span data-stu-id="01ca3-381">Request-a-team</span></span>

<span data-ttu-id="01ca3-382">Request-a-team é um aplicativo do Microsoft Teams que otimiza a criação de novas equipes para sua organização corporativa.</span><span class="sxs-lookup"><span data-stu-id="01ca3-382">Request-a-team is a Microsoft Teams app that optimizes new team creation for your enterprise organization.</span></span> <span data-ttu-id="01ca3-383">O aplicativo oferece suporte à padronização e às práticas recomendadas ao criar novas instâncias de equipe por meio da integração de um formulário de solicitação orientado por assistente, um processo de aprovação incorporado, um painel de status de solicitação e builds automatizados da equipe.</span><span class="sxs-lookup"><span data-stu-id="01ca3-383">The app supports standardization and best practices when creating new team instances through the integration of a wizard-guided request form, an embedded approval process, a request status dashboard, and automated team builds.</span></span>

[<span data-ttu-id="01ca3-384">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-384">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-requestateam)

:::row:::
  :::column span="2":::
    ![Exibição da página de início de solicitação de uma equipe](../assets/images/request-a-team-two.jpg)
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Exibição de página do assistente de solicitação de equipe](../assets/images/request-a-team-three.png)
:::column-end:::
:::row-end:::

## <a name="scrums-for-channels"></a><span data-ttu-id="01ca3-387">Scrums para canais</span><span class="sxs-lookup"><span data-stu-id="01ca3-387">Scrums for Channels</span></span>

<span data-ttu-id="01ca3-388">O Scrums for Channels é um aplicativo assistente scrum que permite aos usuários agendar e executar o scrums em canais no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="01ca3-388">Scrums for Channels is a scrum assistant app that enables users to schedule and run scrums in channels within Microsoft Teams.</span></span> <span data-ttu-id="01ca3-389">O aplicativo é ótimo para equipes remotas e equipes compostas por membros de localidades geográficas e fusos horário variados para compartilhar atualizações diárias e garantir a participação em reuniões de stand-up.</span><span class="sxs-lookup"><span data-stu-id="01ca3-389">The app is great for remote teams and teams comprised of members from varied geographical locations and time zones to share daily updates and ensure participation in scrum stand-up meetings.</span></span>

[<span data-ttu-id="01ca3-390">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-390">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-scrumsforchannels)

> [!NOTE]
> <span data-ttu-id="01ca3-391">Para realizar reuniões scrum em um chat em grupo, confira nosso modelo de aplicativo [Scrums para Chat de](#scrums-for-group-chat) Grupo.</span><span class="sxs-lookup"><span data-stu-id="01ca3-391">To conduct scrum meetings in a group chat, please see our [Scrums for Group Chat](#scrums-for-group-chat) app template.</span></span>

:::row:::
  :::column span="2":::
    ![Exibição de configurações de canais do Scrums](../assets/images/scrum-for-channels-settings.png)
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Exibição de status do membro da equipe do Scrums para canais](../assets/images/scrum-for-channels-status.png)
:::column-end:::
:::row-end:::

## <a name="scrums-for-group-chat"></a><span data-ttu-id="01ca3-394">Scrums para Chat de Grupo</span><span class="sxs-lookup"><span data-stu-id="01ca3-394">Scrums for Group Chat</span></span>

> [!NOTE]
> <span data-ttu-id="01ca3-395">O modelo de aplicativo Status do Scrums foi atualizado e agora é o Scrums para Chat de Grupo.</span><span class="sxs-lookup"><span data-stu-id="01ca3-395">The Scrums Status app template has been updated and is now Scrums for Group Chat.</span></span>

<span data-ttu-id="01ca3-396">O Scrums para Chat de Grupo é um assistente de suporte do Scrum que permite que os membros do chat de grupo executem reuniões de stand-up assíncronas e compartilhem facilmente suas atualizações diárias.</span><span class="sxs-lookup"><span data-stu-id="01ca3-396">Scrums for Group Chat is a supportive scrum assistant that enables group chat members to run asynchronous stand-up meetings and easily share their daily updates.</span></span> <span data-ttu-id="01ca3-397">Ele permite que todos os membros do chat de grupo contribuam para o scrum e veja as atualizações feitas por outras pessoas na execução do scrum.</span><span class="sxs-lookup"><span data-stu-id="01ca3-397">It allows all members of the group chat to contribute to the scrum and view the updates made by others in the running scrum.</span></span>

[<span data-ttu-id="01ca3-398">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-398">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-scrumsforgroupchat)

![Demonstração do Scrums para Chat de Grupo](https://raw.githubusercontent.com/wiki/OfficeDev/microsoft-teams-app-scrumstatus/images/StartScrum.jpg)

## <a name="share-now"></a><span data-ttu-id="01ca3-400">Compartilhar Agora</span><span class="sxs-lookup"><span data-stu-id="01ca3-400">Share Now</span></span> 

<span data-ttu-id="01ca3-401">O aplicativo Compartilhar Agora promove a troca positiva de informações entre colegas, permitindo que seus usuários compartilhem conteúdo facilmente no ambiente do Teams.</span><span class="sxs-lookup"><span data-stu-id="01ca3-401">The Share Now app promotes the positive exchange of information between colleagues by enabling your users to easily share content within the Teams environment.</span></span> <span data-ttu-id="01ca3-402">Os usuários envolvem o aplicativo para compartilhar itens de interesse com membros da equipe, descobrir novo conteúdo compartilhado, definir preferências e marcar favoritos para leitura posterior.</span><span class="sxs-lookup"><span data-stu-id="01ca3-402">Users engage the app to share items of interest with team members, discover new shared content, set preferences, and bookmark favorites for later reading.</span></span>

[<span data-ttu-id="01ca3-403">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-403">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-sharenow)

![Selecionar exibição de conteúdo](../assets/images/share-now-suggested-content.png)

## <a name="sharepoint-list-search"></a><span data-ttu-id="01ca3-405">Pesquisa de lista do SharePoint</span><span class="sxs-lookup"><span data-stu-id="01ca3-405">SharePoint List Search</span></span>

<span data-ttu-id="01ca3-406">A colaboração no Microsoft Teams muitas vezes faz referência a informações contidas em itens em uma lista do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="01ca3-406">Collaboration in Microsoft Teams quite often references information contained within items in a SharePoint list.</span></span> <span data-ttu-id="01ca3-407">Simplesmente colar um link para o item em questão força todos a alternar o contexto para longe da conversa, encontrar as informações necessárias e, em seguida, retornar ao Teams para continuar a conversa.</span><span class="sxs-lookup"><span data-stu-id="01ca3-407">Simply pasting a link to the item in question forces everyone to switch context away from the conversation, find the needed information, then return to Teams to continue the conversation.</span></span> <span data-ttu-id="01ca3-408">À medida que a conversa continua, normalmente as pessoas terão que voltar para o item de referência várias vezes para verificar novos comentários e atualizar seus comentários sobre as informações contidas no item.</span><span class="sxs-lookup"><span data-stu-id="01ca3-408">As the conversation continues typically people will have to switch back to the reference item multiple times to verify new comments and refresh their memories of the information contained within the item.</span></span> <span data-ttu-id="01ca3-409">Essa mudança de contexto cria uma barreira para suavizar a colaboração e é uma receita para coisas que estão passando por obstáculos.</span><span class="sxs-lookup"><span data-stu-id="01ca3-409">This context switching creates a barrier to smooth collaboration, and is a recipe for things falling through the cracks.</span></span>

<span data-ttu-id="01ca3-410">Para ajudar a aliviar essa dor, estamos satisfeitos em trazer para você o modelo de aplicativo de Pesquisa de Lista.</span><span class="sxs-lookup"><span data-stu-id="01ca3-410">To help alleviate this pain, we are happy to bring to you the List Search app template.</span></span> <span data-ttu-id="01ca3-411">Milhões de usuários usam o SharePoint para dar energia a alguns dos fluxos de trabalho principais em suas organizações.</span><span class="sxs-lookup"><span data-stu-id="01ca3-411">Millions of users use SharePoint to power some of the core workflows in their organizations.</span></span> <span data-ttu-id="01ca3-412">No entanto, colaborar em listas pode ser especialmente tedioso.</span><span class="sxs-lookup"><span data-stu-id="01ca3-412">However, collaborating around lists can be especially tedious.</span></span> <span data-ttu-id="01ca3-413">Usando o modelo de aplicativo de Pesquisa de Lista no Microsoft Teams, os usuários podem inserir informações de itens de lista do SharePoint diretamente em uma conversa de chat para aliviar a alternância de contexto causada ao simplesmente inserir um link em um chat.</span><span class="sxs-lookup"><span data-stu-id="01ca3-413">Using the List Search app template in Microsoft Teams, users can insert information from SharePoint list items directly within a chat conversation to alleviate the context-switching caused when simply inserting a link into a chat.</span></span> <span data-ttu-id="01ca3-414">As informações são inseridas como um cartão de formatação automática fácil de ler, ajudando os usuários a se manterem envolvidos na conversa.</span><span class="sxs-lookup"><span data-stu-id="01ca3-414">The information is inserted as an easy-to-read auto-formatted card, helping your users stay engaged in the conversation.</span></span>

[<span data-ttu-id="01ca3-415">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-415">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-list-search-app)

![Aplicativo de Pesquisa de Lista](../assets/images/list-search-template.png)

## <a name="staff-check-ins"></a><span data-ttu-id="01ca3-417">Check-ins de equipe</span><span class="sxs-lookup"><span data-stu-id="01ca3-417">Staff Check-ins</span></span>

<span data-ttu-id="01ca3-418">Os Check-ins de Equipe são um aplicativo baseado em [Power Apps](/powerapps/powerapps-overview)que permite a comunicação de supervisão entre sua empresa e a equipe de campo.</span><span class="sxs-lookup"><span data-stu-id="01ca3-418">Staff Check-ins is a [Power Apps](/powerapps/powerapps-overview)-based app that enables oversight communication between your business and field personnel.</span></span> <span data-ttu-id="01ca3-419">A equipe pode facilmente fornecer informações e atualizações de status com tempo crítico em uma base agendada ou ad hoc diretamente do Teams.</span><span class="sxs-lookup"><span data-stu-id="01ca3-419">Staff can easily provide time-critical information and status updates on either a scheduled or ad-hoc basis directly from Teams.</span></span> <span data-ttu-id="01ca3-420">O aplicativo dá suporte a localização, fotos e anotações em tempo real, bem como notificações de lembrete e fluxos de trabalho automatizados.</span><span class="sxs-lookup"><span data-stu-id="01ca3-420">The app supports real-time location, photos, and notes as well as reminder notifications and automated workflows.</span></span>

[<span data-ttu-id="01ca3-421">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-421">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-staffcheckins)

![Criar exibição de check-in](../assets/images/staff-check-ins-create.png)

## <a name="survey"></a><span data-ttu-id="01ca3-423">Pesquisa</span><span class="sxs-lookup"><span data-stu-id="01ca3-423">Survey</span></span>

<span data-ttu-id="01ca3-424">A pesquisa é um aplicativo de extensão de mensagens personalizado do Microsoft [Teams](../messaging-extensions/what-are-messaging-extensions.md) que permite criar uma pesquisa em um chat ou em um canal para coletar dados e obter informações ativas.</span><span class="sxs-lookup"><span data-stu-id="01ca3-424">Survey is a custom Microsoft Teams [messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that enables you to create a survey in a chat or a channel to gather data and gain actionable insight.</span></span>  <span data-ttu-id="01ca3-425">O aplicativo tem suporte em todos os clientes da plataforma Teams — desktop, navegador, iOS e Android — e está pronto para implantação como parte da sua assinatura do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="01ca3-425">The app is supported across all Teams platform clients — desktop, browser, iOS, and Android — and is ready for deployment as part of your Microsoft 365 subscription.</span></span>  

[<span data-ttu-id="01ca3-426">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-426">Get it on GitHub</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Survey-app)

:::row:::
  :::column span="2":::
    ![Criar pesquisa na exibição do Teams](../assets/images/survey-app-template-compose-view.gif)
:::column-end:::
:::row-end:::

## <a name="virtual-rounding-9734"></a><span data-ttu-id="01ca3-428">Arredondamento virtual &#9734;</span><span class="sxs-lookup"><span data-stu-id="01ca3-428">Virtual Rounding &#9734;</span></span>

<span data-ttu-id="01ca3-429">Os provedores de sala de emergência e hospital fazem dezenas e, muitas vezes, centenas de "rodadas" por dia.</span><span class="sxs-lookup"><span data-stu-id="01ca3-429">Hospital and emergency room providers make dozens, and often hundreds of “rounds” per day.</span></span> <span data-ttu-id="01ca3-430">Esses check-ins rápidos em pacientes destinam-se a fornecer uma verificação de status sobre como o paciente está se saindo e garantir que as preocupações do paciente sejam tratadas.</span><span class="sxs-lookup"><span data-stu-id="01ca3-430">These quick check-ins on patients are intended to provide a status check on how the patient is doing and ensure that the patient’s concerns are addressed.</span></span> <span data-ttu-id="01ca3-431">Embora o arredondamento seja uma prática essencial para garantir que os pacientes sejam monitorados por vários tipos de provedores, eles representam um enorme esvaziamento no PPE, porque para cada visita, de cada provedor, uma nova máscara e um novo conjunto de pacientes devem ser usados.</span><span class="sxs-lookup"><span data-stu-id="01ca3-431">While rounding is an essential practice to ensure patients are being monitored by multiple types of providers, they represent a huge drain on PPE, because for each visit, from each provider, a new mask, and new set of gloves must be used.</span></span> <span data-ttu-id="01ca3-432">Com esses modelos de aplicativo, os funcionários médicos podem conduzir facilmente turnos virtualmente, por meio de uma reunião do Microsoft Teams entre o provedor e o paciente.</span><span class="sxs-lookup"><span data-stu-id="01ca3-432">With this app templates, medical workers can easily conduct rounds virtually, through a Microsoft Teams meeting between the provider and the patient.</span></span>

<span data-ttu-id="01ca3-433">A solução de Arredondamento Virtual também é referenciada na postagem do blog De Ciências da Vida e Saúde [da](https://aka.ms/teamsvirtualrounding)Microsoft.</span><span class="sxs-lookup"><span data-stu-id="01ca3-433">The Virtual Rounding solution is also referenced in the Microsoft Health and Life Sciences [blog post](https://aka.ms/teamsvirtualrounding).</span></span>

[<span data-ttu-id="01ca3-434">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-434">Get it on GitHub</span></span>](https://github.com/SmartterHealth/Virtual-Rounding)

![Arredondamento Virtual](../assets/images/virtual-rounding-overview.png)

## <a name="visitor-management"></a><span data-ttu-id="01ca3-436">Gerenciamento de Visitantes</span><span class="sxs-lookup"><span data-stu-id="01ca3-436">Visitor Management</span></span>

<span data-ttu-id="01ca3-437">O aplicativo Gerenciamento de Visitantes permite que sua organização e seus funcionários gerenciem de forma fácil e eficiente o processo de visitante local, diretamente do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="01ca3-437">The Visitor Management app enables your organization and employees to easily and efficiently manage the on-site visitor process, directly from Microsoft Teams.</span></span> <span data-ttu-id="01ca3-438">O aplicativo permite que os funcionários criem solicitações de visitantes, acompanhem centralmente o status de uma solicitação por meio do painel do visitante e recebam notificações em tempo real quando um visitante chega.</span><span class="sxs-lookup"><span data-stu-id="01ca3-438">The app enables employees to create visitor requests, centrally track a request status through the visitor dashboard, and receive real-time notifications when a visitor arrives.</span></span>

[<span data-ttu-id="01ca3-439">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-439">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-app-visitormanagement)

:::row:::
  :::column span="2":::
    ![Criar um exibição de solicitação](../assets/images/visitor-management-create-request.png)
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Notificação de chegada de visitante](../assets/images/visitor-management-notify-host.png)
:::column-end:::
:::row-end:::

## <a name="workplace-awards"></a><span data-ttu-id="01ca3-442">Workplace Awards</span><span class="sxs-lookup"><span data-stu-id="01ca3-442">Workplace Awards</span></span>

<span data-ttu-id="01ca3-443">O Workplace Awards é um modelo de aplicativo do Teams que fornece uma estrutura positiva para promover o reconhecimento e incentivar a cultura do reconhecimento dos funcionários no local de trabalho moderno.</span><span class="sxs-lookup"><span data-stu-id="01ca3-443">Workplace Awards is a Teams app template that provides a positive framework to foster recognition and encourage the culture of employee appreciation in the modern workplace.</span></span> <span data-ttu-id="01ca3-444">O aplicativo permite que você configure e gerencie um programa de recompensas e reconhecimento de funcionários (R&R), onde os funcionários podem facilmente nomear e nomear colegas e seu líder R&R pode exibir indicaçãos enviadas, conceder concessões e anunciar destinatários.</span><span class="sxs-lookup"><span data-stu-id="01ca3-444">The app enables you to setup and manage an employee rewards and recognition (R&R) program where employees can easily nominate and endorse colleagues and your R&R leader can view submitted nominations, grant awards, and announce recipients.</span></span>

[<span data-ttu-id="01ca3-445">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="01ca3-445">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-workplaceawards)

:::row:::
  :::column span="2":::
    ![<span data-ttu-id="01ca3-446">Cartão de indicação de prêmio no local de trabalho</span><span class="sxs-lookup"><span data-stu-id="01ca3-446">Workplace awards nomination card</span></span> ](../assets/images/workplace-awards-nominate.png)
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Guia da lista de prêmio do local de trabalho](../assets/images/workplace-awards-champion-tab.png)
:::column-end:::
:::row-end:::

<span data-ttu-id="01ca3-448">Tem uma ideia de um modelo de aplicativo que gostaria de ver?</span><span class="sxs-lookup"><span data-stu-id="01ca3-448">Have an idea for an app template you'd like to see?</span></span> <span data-ttu-id="01ca3-449">[Por favor, nos avise.](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR2_7qFm_lcZAr4eqEhnLsZ9UMVZGT1lCT0FXUDdZMUM0RkpBS1BESTAwWC4u)</span><span class="sxs-lookup"><span data-stu-id="01ca3-449">[Please let us know](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR2_7qFm_lcZAr4eqEhnLsZ9UMVZGT1lCT0FXUDdZMUM0RkpBS1BESTAwWC4u).</span></span>
