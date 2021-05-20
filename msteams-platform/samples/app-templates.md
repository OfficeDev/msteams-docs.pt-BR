---
title: modelos de aplicativos Microsoft Teams
description: Links e descrições de modelos de aplicativos para a plataforma Microsoft Teams
ms.topic: reference
keywords: Microsoft Teams modelos amostras demonstram demonstração
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
# <a name="app-templates-for-microsoft-teams"></a><span data-ttu-id="052f4-104">Modelos de aplicativos para o Teams</span><span class="sxs-lookup"><span data-stu-id="052f4-104">App templates for Microsoft Teams</span></span>

<span data-ttu-id="052f4-105">Modelos de aplicativos são exemplos de aplicativos completos para Microsoft Teams que são de código aberto e estão disponíveis em GitHub.</span><span class="sxs-lookup"><span data-stu-id="052f4-105">App templates are examples of complete apps for Microsoft Teams that are open-source and available on GitHub.</span></span> <span data-ttu-id="052f4-106">Cada modelo de aplicativo contém instruções detalhadas para implantar e instalar esse aplicativo para sua organização.</span><span class="sxs-lookup"><span data-stu-id="052f4-106">Each app template contains detailed instructions for deploying and installing that app for your organization.</span></span> <span data-ttu-id="052f4-107">Ele também fornece um aplicativo de amostra que você pode instalar e começar a usar imediatamente.</span><span class="sxs-lookup"><span data-stu-id="052f4-107">It also provides a sample app that you can install and start using immediately.</span></span> <span data-ttu-id="052f4-108">O código-fonte completo também está disponível, o que permite explorá-lo em detalhes ou bifurcar o código e alterá-lo para atender aos seus requisitos específicos.</span><span class="sxs-lookup"><span data-stu-id="052f4-108">The complete source code is also available, which allows you to explore it in detail or fork the code and alter it to meet your specific requirements.</span></span>
<span data-ttu-id="052f4-109">Todos os modelos de aplicativos são fornecidos nos termos [da Licença do MIT.](https://github.com/OfficeDev/microsoft-teams-apps-eprescription/blob/master/LICENSE)</span><span class="sxs-lookup"><span data-stu-id="052f4-109">All app templates are provided under the [MIT License](https://github.com/OfficeDev/microsoft-teams-apps-eprescription/blob/master/LICENSE) terms.</span></span>

> [!NOTE] 
> <span data-ttu-id="052f4-110">Você deve licenciar e apoiar aplicativos criados a partir de modelos de aplicativos para seus usuários e organizações.</span><span class="sxs-lookup"><span data-stu-id="052f4-110">You must license and support apps created from app templates for your users and organizations.</span></span>

<span data-ttu-id="052f4-111">**&#9734; Indica modelos de aplicativos recém-lançados.**</span><span class="sxs-lookup"><span data-stu-id="052f4-111">**&#9734; Indicates newly released app templates.**</span></span>

### <a name="key-benefits"></a><span data-ttu-id="052f4-112">Principais benefícios</span><span class="sxs-lookup"><span data-stu-id="052f4-112">Key benefits</span></span>

* <span data-ttu-id="052f4-113">**Implantar diretamente na nuvem:** Todos os modelos de aplicativos incluem scripts de implantação que permitem hospedar todos os serviços necessários em Microsoft Azure ou na Plataforma de Energia.</span><span class="sxs-lookup"><span data-stu-id="052f4-113">**Deploy directly to the cloud:** All app templates include deployment scripts that allows you to host all required services in Microsoft Azure or the Power Platform.</span></span> 
* <span data-ttu-id="052f4-114">**Código de amostra recomendado:** Os modelos de aplicativos estão de acordo com as práticas recomendadas em torno de segurança e infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="052f4-114">**Recommended sample code:** The app templates conform to recommended best practices around security and infrastructure.</span></span> <span data-ttu-id="052f4-115">Todas as alterações submetidas à comunidade nos modelos do aplicativo são revisadas para garantir a conformidade.</span><span class="sxs-lookup"><span data-stu-id="052f4-115">All community submitted changes to the app templates are reviewed to ensure conformance.</span></span>
* <span data-ttu-id="052f4-116">**Personalizável e extensível:** Embora todos os modelos de aplicativos sejam implantados com configuração mínima, toda a base de código e scripts de implantação são fornecidos, para que você possa facilmente personalizá-los ou amplie-os para atender às suas necessidades exclusivas.</span><span class="sxs-lookup"><span data-stu-id="052f4-116">**Customizable and extensible:** While all app templates are deployed with minimal configuration, the entire code base and deployment scripts are provided, so that you can easily customize or extend them to fit your unique needs.</span></span>
* <span data-ttu-id="052f4-117">**Documentação detalhada:** Todos os modelos de aplicativos são acompanhados por documentação completa sobre arquitetura de soluções, implantação e etapas de configuração.</span><span class="sxs-lookup"><span data-stu-id="052f4-117">**Detailed documentation:** All app templates are accompanied by end-to-end documentation on solution architecture, deployment, and configuration steps.</span></span>  

## <a name="adoption-bot"></a><span data-ttu-id="052f4-118">Bot de adoção</span><span class="sxs-lookup"><span data-stu-id="052f4-118">Adoption Bot</span></span> 

<span data-ttu-id="052f4-119">Adoption Bot é um bot de chat de cuidados do usuário construído com power virtual agent para Teams PVA.</span><span class="sxs-lookup"><span data-stu-id="052f4-119">Adoption Bot is a user care chat bot built with Power Virtual Agent for Teams PVA.</span></span> <span data-ttu-id="052f4-120">É considerada como a versão PVA do FAQ Plus.</span><span class="sxs-lookup"><span data-stu-id="052f4-120">It is considered as the PVA version of FAQ Plus.</span></span> <span data-ttu-id="052f4-121">Adoção Bot responde mais de 100 perguntas comuns sobre Microsoft 365 e Teams.</span><span class="sxs-lookup"><span data-stu-id="052f4-121">Adoption Bot answers 100+ common questions about Microsoft 365 and Teams.</span></span> <span data-ttu-id="052f4-122">Você pode editar os tópicos existentes, adicionar seus próprios tópicos e ingerir perguntas frequentes existentes.</span><span class="sxs-lookup"><span data-stu-id="052f4-122">You can edit the existing topics, add your own topics, and ingest existing FAQs.</span></span> <span data-ttu-id="052f4-123">Se os usuários precisarem de ajuda adicional, o Adoption Bot pode conectá-los a especialistas ou até mesmo ser estendido para abrir bilhetes de serviço com conectores de fluxo premium.</span><span class="sxs-lookup"><span data-stu-id="052f4-123">If users need additional help, Adoption Bot can connect them to experts or even be extended to open service tickets with premium flow connectors.</span></span> <span data-ttu-id="052f4-124">Este bot é auto-instalado ou incorporado em um aplicativo personalizado, como o [Adoption Hub](https://github.com/akporzondek/adoption_hub).</span><span class="sxs-lookup"><span data-stu-id="052f4-124">This bot is self-installed or built into a custom app, such as the [Adoption Hub](https://github.com/akporzondek/adoption_hub).</span></span>

[<span data-ttu-id="052f4-125">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-125">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-adopt-bot)

## <a name="adoption-tool--champion-management-platform-9734"></a><span data-ttu-id="052f4-126">Ferramenta de Adoção- Plataforma de Gestão Campeã &#9734;</span><span class="sxs-lookup"><span data-stu-id="052f4-126">Adoption Tool- Champion Management Platform &#9734;</span></span>

<span data-ttu-id="052f4-127">O modelo de aplicativo Champion Management Platform (CMP) ajuda você a gerenciar, dimensionar e inspirar seus campeões de trabalho em equipe a conseguir mais.</span><span class="sxs-lookup"><span data-stu-id="052f4-127">The Champion Management Platform (CMP) app template helps you manage, scale, and inspire your teamwork champions to achieve more.</span></span> <span data-ttu-id="052f4-128">Este modelo de aplicativo é construído sobre o Estrutura do SharePoint e carregado em uma guia dentro de uma equipe.</span><span class="sxs-lookup"><span data-stu-id="052f4-128">This app template is built on the SharePoint Framework and loaded into a tab within a team.</span></span> <span data-ttu-id="052f4-129">Os grupos podem aproveitar essa ferramenta para ajudar a gerenciar a adesão ao programa, fornecer uma tabela de classificação e tipos de eventos para registro e ferramentas para sobrepor crachás digitais aos participantes do programa.</span><span class="sxs-lookup"><span data-stu-id="052f4-129">Groups can leverage this tool to help manage program membership, provide a leaderboard and event types for logging, and tools to overlay digital badges to program participants.</span></span>

[<span data-ttu-id="052f4-130">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-130">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-champion-management)

## <a name="adoption-tool--microsoft-365-learning-pathways-get-started-9734"></a><span data-ttu-id="052f4-131">&#9734; de Caminhos de Aprendizagem Microsoft 365 (Introdução Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="052f4-131">Adoption Tool- Microsoft 365 Learning Pathways (Get Started) &#9734;</span></span>

<span data-ttu-id="052f4-132">O modelo de aplicativo Introdução permite que você traga o poder de Microsoft 365 caminhos de aprendizagem dentro de Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="052f4-132">The Get Started app template allows you to bring the power of Microsoft 365 learning pathways inside of Microsoft Teams.</span></span> <span data-ttu-id="052f4-133">Este modelo de aplicativo permite que você conceda fácil acesso a páginas de treinamento específicas ou outros ativos intranet e carregue o conteúdo diretamente dentro de Teams.</span><span class="sxs-lookup"><span data-stu-id="052f4-133">This app template allows you to grant easy access to specific training pages or other intranet assets and load the content directly within Teams.</span></span> <span data-ttu-id="052f4-134">Você também pode alterar o nome do aplicativo ou logotipo para combinar com a marca da sua empresa.</span><span class="sxs-lookup"><span data-stu-id="052f4-134">You can also change the app name or logo to match your company branding.</span></span>

[<span data-ttu-id="052f4-135">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-135">Get it on GitHub</span></span>](https://github.com/msft-teams/tools/tree/master/M365%20Learning%20Pathways)

## <a name="appointment-manager"></a><span data-ttu-id="052f4-136">Gerente de Nomeação</span><span class="sxs-lookup"><span data-stu-id="052f4-136">Appointment Manager</span></span> 

<span data-ttu-id="052f4-137">O Appointment Manager é um modelo de aplicativo Teams para ajudar as empresas a criar, gerenciar e realizar compromissos virtuais com os consumidores através de Teams.</span><span class="sxs-lookup"><span data-stu-id="052f4-137">Appointment Manager is a Teams app template to help businesses create, manage, and conduct virtual appointments with consumers through Teams.</span></span> <span data-ttu-id="052f4-138">Novas solicitações de consulta dos consumidores são visíveis nos canais Teams, onde são rapidamente atribuídos e transferidos para funcionários de uma equipe.</span><span class="sxs-lookup"><span data-stu-id="052f4-138">New appointment requests from consumers are visible in Teams channels, where they are quickly assigned and reassigned to staff in a team.</span></span> <span data-ttu-id="052f4-139">As solicitações de nomeação são visualizadas em níveis de equipe ou pessoais através de guias personalizadas.</span><span class="sxs-lookup"><span data-stu-id="052f4-139">Appointment requests are viewed at team or personal levels through custom tabs.</span></span> <span data-ttu-id="052f4-140">Cada consulta está associada a uma reunião on-line Teams, portanto, a equipe e os consumidores podem facilmente participar da reunião no horário agendado.</span><span class="sxs-lookup"><span data-stu-id="052f4-140">Every appointment is associated with a Teams online meeting, hence the staff and consumers can easily join the meeting at the scheduled time.</span></span>

<span data-ttu-id="052f4-141">O modelo do aplicativo se integra com o Microsoft Bookings para fácil gerenciamento de consultas.</span><span class="sxs-lookup"><span data-stu-id="052f4-141">The app template integrates with Microsoft Bookings for easy appointment management.</span></span> <span data-ttu-id="052f4-142">Os compromissos agendados aparecem automaticamente nos calendários dos funcionários designados, e os consumidores recebem notificações e lembretes de e-mail personalizáveis com links de reunião incorporados.</span><span class="sxs-lookup"><span data-stu-id="052f4-142">Scheduled appointments automatically appear on assigned staff members' calendars, and consumers receive customizable email notifications and reminders with embedded meeting links.</span></span>

[<span data-ttu-id="052f4-143">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-143">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-appointment-manager)

<span data-ttu-id="052f4-144">![Gerente de consulta geral ](../assets/images/appointment-manager-overview.png)
 ![ em Teams](../assets/images/appointment-manager-2.png)</span><span class="sxs-lookup"><span data-stu-id="052f4-144">![Appointment Manager Overview](../assets/images/appointment-manager-overview.png)
![Appointment Manager in Teams](../assets/images/appointment-manager-2.png)</span></span>

## <a name="ask-away"></a><span data-ttu-id="052f4-145">Pergunte</span><span class="sxs-lookup"><span data-stu-id="052f4-145">Ask Away</span></span>

<span data-ttu-id="052f4-146">Ask Away é um [bot Microsoft Teams](../bots/what-are-bots.md) que permite que os usuários realizem perguntas e respostas, chamadas de sessões Q&A dentro de Teams.</span><span class="sxs-lookup"><span data-stu-id="052f4-146">Ask Away is a [Microsoft Teams bot](../bots/what-are-bots.md) that enables users to conduct Question and Answer, called Q&A sessions within Teams.</span></span> <span data-ttu-id="052f4-147">Usando o bot Ask Away, os membros da equipe podem enviar e levantar perguntas compartilhadas por colegas que permitem que os hosts Q&A facilmente reúnam perguntas de primeira linha dentro de um canal ou bate-papo.</span><span class="sxs-lookup"><span data-stu-id="052f4-147">Using the Ask Away bot, team members can submit and up-vote questions shared by colleagues allowing Q&A hosts to easily gather top-of-mind questions within a channel or chat.</span></span> <span data-ttu-id="052f4-148">O bot é usado para realizar uma sessão de Q&A em tempo real em uma reunião de Teams e permite que os participantes enviem perguntas ao vivo através do chat.</span><span class="sxs-lookup"><span data-stu-id="052f4-148">The bot is used to conduct a real-time Q&A session in a Teams meeting and allows attendees to submit questions live through chat.</span></span>

[<span data-ttu-id="052f4-149">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-149">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-askaway)

:::row:::
  :::column span="2":::
    ![Veja o diálogo pop-up da tabela de classificação para os usuários votarem em perguntas](../assets/images/ask-away-app.png)  
:::column-end:::
:::row-end:::

## <a name="associate-insights"></a><span data-ttu-id="052f4-151">Informações associadas</span><span class="sxs-lookup"><span data-stu-id="052f4-151">Associate Insights</span></span>

<span data-ttu-id="052f4-152">O Associate Insights é um modelo [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) que capacita os trabalhadores da primeira linha a capturar e enviar diretamente a opinião, o sentimento e a percepção do cliente.</span><span class="sxs-lookup"><span data-stu-id="052f4-152">Associate Insights is a [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) template that empowers firstline workers to directly capture and submit customer opinion, sentiment, and perception.</span></span> <span data-ttu-id="052f4-153">Os trabalhadores da firstline são frequentemente os primeiros representantes da empresa a se envolver com os clientes em um ponto de contato de um para um.</span><span class="sxs-lookup"><span data-stu-id="052f4-153">Firstline workers are often the first company representative to engage with customers in a one-to-one point-of contact.</span></span> <span data-ttu-id="052f4-154">Os dados coletados são compartilhados e utilizados de forma colaborativa pelas equipes de negócios, como por meio de uma guia de Power BI Teams, para melhoria do produto e melhoria da experiência do cliente.</span><span class="sxs-lookup"><span data-stu-id="052f4-154">The collected data are shared and used collaboratively by business teams, such as through a Power BI Teams tab, for product improvement and enhancing the customer experience.</span></span>

[<span data-ttu-id="052f4-155">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-155">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-associateinsights)

:::row:::
  :::column span="2":::
    ![Visão de feedback de insights gerados pelo aplicativo](../assets/images/associate-insights-app.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Power BI visão de insights gerados pelo aplicativo](../assets/images/associate-insights-app2.png)
:::column-end:::
:::row-end:::

## <a name="attendance"></a><span data-ttu-id="052f4-158">Participação</span><span class="sxs-lookup"><span data-stu-id="052f4-158">Attendance</span></span>

<span data-ttu-id="052f4-159">O aplicativo De Presença é uma [guia Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) que está presa em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="052f4-159">The Attendance app is a [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) tab that are pinned in a team.</span></span> <span data-ttu-id="052f4-160">Ele foi projetado para registrar presença em cenários, como ambientes de aprendizagem e treinamento.</span><span class="sxs-lookup"><span data-stu-id="052f4-160">It is designed to record presence in settings, such as learning and training environments.</span></span> <span data-ttu-id="052f4-161">Os usuários podem marcar ou editar atendimento por até 30 dias no passado e visualizar relatórios de atendimento resumidos para um grupo inteiro ou participantes individuais.</span><span class="sxs-lookup"><span data-stu-id="052f4-161">Users can mark or edit attendance for up to 30 days in the past and view summarized attendance reports for an entire group or individual attendees.</span></span> <span data-ttu-id="052f4-162">Para obter mais informações sobre o atendimento das equipes, consulte [Get it on GitHub](https://github.com/OfficeDev/microsoft-teams-apps-attendance).</span><span class="sxs-lookup"><span data-stu-id="052f4-162">For more information on teams attendance, see [Get it on GitHub](https://github.com/OfficeDev/microsoft-teams-apps-attendance).</span></span>

<span data-ttu-id="052f4-163">A imagem a seguir exibe a demonstração do aplicativo de atendimento:</span><span class="sxs-lookup"><span data-stu-id="052f4-163">The following image displays the attendance app demo:</span></span>  

![Demonstração do aplicativo de atendimento](../assets/images/attendance-app.png)

## <a name="book-a-room"></a><span data-ttu-id="052f4-165">Livro-a-sala</span><span class="sxs-lookup"><span data-stu-id="052f4-165">Book-a-room</span></span>

<span data-ttu-id="052f4-166">Book-a-room é um [bot Microsoft Teams](../bots/what-are-bots.md) que permite aos usuários encontrar e reservar rapidamente uma sala de reunião por 30, 60 ou 90 minutos a partir do momento atual.</span><span class="sxs-lookup"><span data-stu-id="052f4-166">Book-a-room is a [Microsoft Teams bot](../bots/what-are-bots.md) that allows users quickly to find and reserve a meeting room for 30, 60, or 90 minutes starting from the current time.</span></span> <span data-ttu-id="052f4-167">O tempo padrão é de 30 minutos.</span><span class="sxs-lookup"><span data-stu-id="052f4-167">The default time is 30 minutes.</span></span> <span data-ttu-id="052f4-168">Os escopos do robô Book-a-room para conversas pessoais ou 1:1.</span><span class="sxs-lookup"><span data-stu-id="052f4-168">The Book-a-room bot scopes to personal or 1:1 conversations.</span></span> <span data-ttu-id="052f4-169">Para obter mais informações sobre o aplicativo Book-a-room, consulte [Get it on GitHub](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom).</span><span class="sxs-lookup"><span data-stu-id="052f4-169">For more information on Book-a-room app, see [Get it on GitHub](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom).</span></span>  
<span data-ttu-id="052f4-170">A imagem a seguir exibe a demonstração book-a-room:</span><span class="sxs-lookup"><span data-stu-id="052f4-170">The following image displays the Book-a-room demo:</span></span>

![Demonstração de livro-a-room](../assets/images/book-a-room.png)

## <a name="building-access"></a><span data-ttu-id="052f4-172">Acesso ao edifício</span><span class="sxs-lookup"><span data-stu-id="052f4-172">Building Access</span></span>

<span data-ttu-id="052f4-173">Building Access é um aplicativo baseado em [Microsoft Power Platform](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/) que suporta a administração de limites de ocupação predial e normas de distanciamento social, permitindo que os diretores de instalações gerenciem, rastreiem e informem a presença dos funcionários no local.</span><span class="sxs-lookup"><span data-stu-id="052f4-173">Building Access is a Microsoft [Power Platform](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/) based app that supports the administration of building occupancy thresholds and social distancing norms by enabling facilities directors to manage, track, and report employee on-site presence.</span></span> <span data-ttu-id="052f4-174">O aplicativo, construído usando [Power Apps](/powerapps/powerapps-overview)e [Power Automate](/power-automate/getting-started)da Microsoft, integra profundamente com Microsoft Teams e permite que as organizações determinem a prontidão para a construção, estabeleçam critérios de elegibilidade para acesso no local e reúnam insights para o planejamento futuro.</span><span class="sxs-lookup"><span data-stu-id="052f4-174">The app, built using Microsoft [Power Apps](/powerapps/powerapps-overview), and [Power Automate](/power-automate/getting-started), deeply integrates with Microsoft Teams and enables organizations to determine building readiness, establish eligibility criteria for on-site access, and gather insights for future planning.</span></span>

[<span data-ttu-id="052f4-175">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-175">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-buildingaccess)

:::row:::
   :::column span="":::
     ![Cartão de reserva do Building Access](../assets/images/building-access-reservation.png)
   :::column-end:::
   :::column span="":::
      ![Exibição da chave do Building Access](../assets/images/building-access-access-key.png)
   :::column-end:::
:::row-end:::

## <a name="celebrations"></a><span data-ttu-id="052f4-178">Celebrações</span><span class="sxs-lookup"><span data-stu-id="052f4-178">Celebrations</span></span>

<span data-ttu-id="052f4-179">Celebrations é um aplicativo Teams que ajuda os membros da equipe a celebrar os aniversários uns dos outros, aniversários e outros eventos recorrentes.</span><span class="sxs-lookup"><span data-stu-id="052f4-179">Celebrations is a Teams app that helps team members to celebrate each others' birthdays, anniversaries, and other recurring events.</span></span> <span data-ttu-id="052f4-180">Ele lembra ocasiões especiais de todos os membros da equipe e envia uma mensagem amigável em todas as equipes selecionadas no momento da criação do evento, para fazer com que os membros da equipe se sintam especiais em seu dia.</span><span class="sxs-lookup"><span data-stu-id="052f4-180">It remembers special occasions of all the team members and sends a friendly message in all the teams selected at the time of event creation, to make the team members feel special on their day.</span></span>

<span data-ttu-id="052f4-181">O aplicativo fornece uma interface fácil para todos os membros da equipe adicionarem e visualizarem seus eventos pessoalmente e também permite que o usuário selecione as equipes em que os eventos são compartilhados.</span><span class="sxs-lookup"><span data-stu-id="052f4-181">The app provides an easy interface for all the team members to personally add and view their events and also allows the user to select the teams in which the events gets shared.</span></span>

[<span data-ttu-id="052f4-182">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-182">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-celebrations-app)

## <a name="checklist"></a><span data-ttu-id="052f4-183">Lista de verificação</span><span class="sxs-lookup"><span data-stu-id="052f4-183">Checklist</span></span>

<span data-ttu-id="052f4-184">Checklist é um aplicativo de [extensão de mensagens](../messaging-extensions/what-are-messaging-extensions.md) Microsoft Teams personalizado que permite que você colabore com sua equipe criando uma lista de verificação compartilhada em um chat ou canal.</span><span class="sxs-lookup"><span data-stu-id="052f4-184">Checklist is a custom Microsoft Teams [messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that enables you to collaborate with your team by creating a shared checklist in a chat or channel.</span></span> <span data-ttu-id="052f4-185">O aplicativo é suportado em todos os clientes Teams plataforma, como navegador de desktop, iOS e Android.</span><span class="sxs-lookup"><span data-stu-id="052f4-185">The app is supported across all Teams platform clients, such as desktop browser, iOS, and Android.</span></span> <span data-ttu-id="052f4-186">O aplicativo está pronto para implantação como parte de sua assinatura de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="052f4-186">The app is ready for deployment as part of your Microsoft 365 subscription.</span></span>  

[<span data-ttu-id="052f4-187">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-187">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-checklist-app)

:::row:::
:::column span="2":::
    ![Criar checklist na exibição Teams](../assets/images/checklist-app-template-compose-view.gif)  
:::column-end:::
:::row-end:::

## <a name="classroom-drop-in"></a><span data-ttu-id="052f4-189">Drop-in em sala de aula</span><span class="sxs-lookup"><span data-stu-id="052f4-189">Classroom Drop-in</span></span> 

<span data-ttu-id="052f4-190">O Classroom Drop-in é um aplicativo baseado na [Microsoft Power Platform](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/)que permite que os líderes do sistema encontrem equipes de classe, significa salas de aula virtuais e adicionem a si mesmos ou outros a essas equipes de classe por um período de drop-in especificado, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="052f4-190">Classroom Drop-in is a Microsoft [Power Platform](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/)-based app that enables system leaders to find class teams, means virtual classrooms and add themselves or others to these class teams for a specified drop-in period, as needed.</span></span> <span data-ttu-id="052f4-191">O aplicativo construído usando [Power Apps](/powerapps/powerapps-overview) e [Power Automate](/power-automate/getting-started)da Microsoft, integra profundamente com Microsoft Teams para garantir que os institutos educacionais possam otimizar suas operações em um ambiente de aprendizagem híbrido, fornecendo acesso a stakeholders relevantes para equipes de classe por requisitos de negócios.</span><span class="sxs-lookup"><span data-stu-id="052f4-191">The app built using Microsoft [Power Apps](/powerapps/powerapps-overview) and [Power Automate](/power-automate/getting-started), deeply integrates with Microsoft Teams to ensure educational institutes can optimize their operations in a hybrid learning environment by providing access to relevant stakeholders for class teams per business requirements.</span></span>

[<span data-ttu-id="052f4-192">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-192">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-classroom-dropin)

![Solicitação de drop-in em sala de aula](../assets/images/classroom-drop-in-request.png)

## <a name="company-communicator"></a><span data-ttu-id="052f4-194">Communicator da empresa</span><span class="sxs-lookup"><span data-stu-id="052f4-194">Company Communicator</span></span>

<span data-ttu-id="052f4-195">O aplicativo Communicator empresa permite que as equipes corporativas criem e enviem mensagens destinadas a várias equipes ou grande número de funcionários por chat, permitindo que a organização chegue aos funcionários exatamente onde eles colaboram.</span><span class="sxs-lookup"><span data-stu-id="052f4-195">The Company Communicator app enables corporate teams to create and send messages intended for multiple teams or large number of employees over chat allowing organization to reach employees right where they collaborate.</span></span> <span data-ttu-id="052f4-196">Utilize este modelo para vários cenários, como anúncios de novas iniciativas, onboarding de funcionários, aprendizado moderno e desenvolvimento ou transmissões em toda a organização.</span><span class="sxs-lookup"><span data-stu-id="052f4-196">Utilize this template for multiple scenarios such as new initiative announcements, employee onboarding, modern learning, and development or organization-wide broadcasts.</span></span>

<span data-ttu-id="052f4-197">O aplicativo fornece uma interface fácil para usuários designados criarem, visualizarem, colaborarem e enviarem mensagens.</span><span class="sxs-lookup"><span data-stu-id="052f4-197">The app provides an easy interface for designated users to create, preview, collaborate and send messages.</span></span>

<span data-ttu-id="052f4-198">Ele fornece uma base para construir recursos de comunicação direcionados personalizados, como telemetria personalizada, quantos usuários reconheceram ou interagiram com uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="052f4-198">It provides a foundation to build custom targeted communication capabilities such as custom telemetry on how many users acknowledged or interacted with a message.</span></span>

[<span data-ttu-id="052f4-199">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-199">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-company-communicator-app)

![jCompany Communicator compor vista de caixa](../assets/images/CompanyCommunicatorCompose.png)

## <a name="contact-group-lookup"></a><span data-ttu-id="052f4-201">Procurar grupo de contato</span><span class="sxs-lookup"><span data-stu-id="052f4-201">Contact Group Lookup</span></span>

<span data-ttu-id="052f4-202">O aplicativo Contact Group Lookup fornece uma abordagem conveniente e útil para criar, acessar e gerenciar os grupos de contato da sua organização, anteriormente conhecidos como listas de distribuição ou grupos de comunicação.</span><span class="sxs-lookup"><span data-stu-id="052f4-202">The Contact Group Lookup app provides a convenient and useful approach to creating, accessing, and managing your organization's contact groups, formerly known as distribution lists or communication groups.</span></span> <span data-ttu-id="052f4-203">Os usuários podem visualizar e conversar rapidamente com os membros do grupo, visualizar o status do membro e criar um bate-papo em grupo com membros selecionados no grupo de contato, tudo dentro do ambiente Teams.</span><span class="sxs-lookup"><span data-stu-id="052f4-203">Users can quickly view and chat with group members, view member status, and create a group chat with selected members in the contact group, all within the Teams environment.</span></span>

[<span data-ttu-id="052f4-204">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-204">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-app-contactgrouplookup)

:::row:::
:::column span="2":::
    ![Grupo de contato Procura-se fixada visualização de favoritos](../assets/images/contact-group-lookup-favorites.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Demonstração de bate-papo de início de grupo de contato](../assets/images/contact-group-lookup-chat.png)
:::column-end:::
:::row-end:::

## <a name="co-worker-appreciation"></a><span data-ttu-id="052f4-207">Valorização do colega de trabalho</span><span class="sxs-lookup"><span data-stu-id="052f4-207">Co-worker Appreciation</span></span> 

<span data-ttu-id="052f4-208">Usando o modelo de valorização do colega de trabalho em Microsoft Teams, os usuários podem reconhecer as conquistas de seus colegas no contexto Teams.</span><span class="sxs-lookup"><span data-stu-id="052f4-208">Using the co-worker appreciation template in Microsoft Teams, users can recognize their colleagues' achievements within the Teams’ context.</span></span> <span data-ttu-id="052f4-209">Quando os colegas de trabalho escolhem recompensar um colega, os destinatários e outros membros da equipe são marcados em uma conversa de canal e recebem uma notificação sobre os detalhes do prêmio do canal.</span><span class="sxs-lookup"><span data-stu-id="052f4-209">When co-workers select to reward a colleague, recipients and other team members are tagged in a channel conversation and they receive a notification about the channel's award details.</span></span> <span data-ttu-id="052f4-210">Os prêmios são registrados no aplicativo Teams, que é seguro, portátil e facilmente compartilhável.</span><span class="sxs-lookup"><span data-stu-id="052f4-210">The awards are recorded in the Teams app, which is secure, portable, and easily shareable.</span></span> <span data-ttu-id="052f4-211">Esta é considerada como a versão baseada no PowerApps do modelo de aplicativo Open Badges, com uma tabela de classificação.</span><span class="sxs-lookup"><span data-stu-id="052f4-211">This is considered as the PowerApps based version of the Open Badges app template, with a leaderboard.</span></span>

[<span data-ttu-id="052f4-212">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-212">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-coworker-appreciation)

![geral](../assets/images/coworker-appreciation-1.png)

## <a name="crowdsourcer"></a><span data-ttu-id="052f4-214">CrowdSourcer</span><span class="sxs-lookup"><span data-stu-id="052f4-214">CrowdSourcer</span></span>

<span data-ttu-id="052f4-215">CrowdSourcer é um [bot Microsoft Teams](../bots/what-are-bots.md) que fornece às equipes informações consultadas de forma colaborativa dos membros do grupo.</span><span class="sxs-lookup"><span data-stu-id="052f4-215">CrowdSourcer is a [Microsoft Teams bot](../bots/what-are-bots.md) that gives teams queried information sourced collaboratively from group members.</span></span> <span data-ttu-id="052f4-216">Ele ajuda a responder perguntas frequentes, permitindo que os participantes se envolvam ativamente e contribuam para um recurso de informação divertido e útil.</span><span class="sxs-lookup"><span data-stu-id="052f4-216">It helps to answer frequently asked questions while enabling participants to actively engage in and contribute to a fun and helpful information resource.</span></span>

[<span data-ttu-id="052f4-217">Obtê-lo no Github</span><span class="sxs-lookup"><span data-stu-id="052f4-217">Get it on Github</span></span>](https://github.com/OfficeDev/microsoft-teams-crowdsourcer-app)

![Interação do usuário final crowdsource](../assets/images/crowdsourcer.png)

## <a name="custom-stickers"></a><span data-ttu-id="052f4-219">Adesivos personalizados</span><span class="sxs-lookup"><span data-stu-id="052f4-219">Custom Stickers</span></span>

<span data-ttu-id="052f4-220">A auto-expressão é o cerne de uma cultura de equipe saudável.</span><span class="sxs-lookup"><span data-stu-id="052f4-220">Self-expression is core to a healthy team culture.</span></span> <span data-ttu-id="052f4-221">Este modelo de aplicativo é uma [extensão de mensagens](~/messaging-extensions/what-are-messaging-extensions.md) que permite que seus usuários usem adesivos e GIFs personalizados dentro de Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="052f4-221">This app template is a [messaging extension](~/messaging-extensions/what-are-messaging-extensions.md) that enables your users to use custom stickers and GIFs within Microsoft Teams.</span></span> <span data-ttu-id="052f4-222">Este modelo oferece uma experiência de configuração fácil baseada na Web, onde qualquer pessoa com acesso à configuração pode carregar os GIFs, adesivos e imagens que deseja que seus usuários tenham, permitindo que toda a sua equipe use qualquer conjunto de adesivos que você escolher.</span><span class="sxs-lookup"><span data-stu-id="052f4-222">This template provides an easy web-based configuration experience where anyone with configuration access can upload the GIFs, stickers, and images they want their users to have, allowing your entire team to use any set of stickers you choose.</span></span>

<span data-ttu-id="052f4-223">Este aplicativo também permite o fácil compartilhamento de imagens, GIFs, adesivos entre as equipes sem precisar de acesso a sites SharePoint ou canais individuais como mecanismos de armazenamento e compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="052f4-223">This app also enables easy sharing of images, GIFs, stickers across teams without needing access to SharePoint sites or individual channels as storage and sharing mechanisms.</span></span> <span data-ttu-id="052f4-224">Por exemplo, as equipes de produtos podem facilmente compartilhar imagens de produtos e GIFs para mídias sociais, marketing e equipes de vendas programáticamente.</span><span class="sxs-lookup"><span data-stu-id="052f4-224">For example, product teams can easily share product images and GIFs to social media, marketing, and sales teams programmatically.</span></span> <span data-ttu-id="052f4-225">Também pode-se estender este aplicativo acionando um fluxo de notificação para equipes ou indivíduos específicos quando novas imagens e GIFs são disponibilizados.</span><span class="sxs-lookup"><span data-stu-id="052f4-225">One can also extend this app by triggering a notification flow to specific teams or individuals when new images, and GIFs are made available.</span></span>

[<span data-ttu-id="052f4-226">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-226">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-stickers-app)

![Aplicativo de adesivos](../assets/images/stickers.png)

## <a name="employee-ideas"></a><span data-ttu-id="052f4-228">Ideias dos funcionários</span><span class="sxs-lookup"><span data-stu-id="052f4-228">Employee Ideas</span></span>

<span data-ttu-id="052f4-229">O aplicativo Ideias de Funcionários é a versão PowerApps do modelo de aplicativo Great Ideas baseado no Azure.</span><span class="sxs-lookup"><span data-stu-id="052f4-229">The Employee Ideas app is the PowerApps version of the Azure based Great Ideas app template.</span></span> <span data-ttu-id="052f4-230">O aplicativo permite que os usuários Teams configurem e configurem uma campanha de ideias.</span><span class="sxs-lookup"><span data-stu-id="052f4-230">The app enables the Teams users to set up and configure an idea campaign.</span></span> <span data-ttu-id="052f4-231">Uma campanha de ideias é uma categoria para agrupar ideias em torno de temas comuns.</span><span class="sxs-lookup"><span data-stu-id="052f4-231">An idea campaign is a category for grouping ideas around common themes.</span></span>

<span data-ttu-id="052f4-232">Teams usuários também podem realizar as seguintes atividades:</span><span class="sxs-lookup"><span data-stu-id="052f4-232">Teams users can also perform the following activities:</span></span>

* <span data-ttu-id="052f4-233">Configure um formulário de submissão padrão que os funcionários devem enviar para cada ideia.</span><span class="sxs-lookup"><span data-stu-id="052f4-233">Configure a standard submission form that employees must submit for each idea.</span></span> 
* <span data-ttu-id="052f4-234">Revise e gerencie as ideias e lista de campanhas.</span><span class="sxs-lookup"><span data-stu-id="052f4-234">Review and manage the ideas and list of campaigns.</span></span>
* <span data-ttu-id="052f4-235">Modifique e exclua campanhas.</span><span class="sxs-lookup"><span data-stu-id="052f4-235">Modify and delete campaigns.</span></span>
* <span data-ttu-id="052f4-236">Revise os quadros de líderes de ideias.</span><span class="sxs-lookup"><span data-stu-id="052f4-236">Review leader boards of ideas.</span></span>
* <span data-ttu-id="052f4-237">Vote e compartilhe ideias prioriadas.</span><span class="sxs-lookup"><span data-stu-id="052f4-237">Vote for and share prioritized ideas.</span></span>
* <span data-ttu-id="052f4-238">Envie ideias para uma campanha.</span><span class="sxs-lookup"><span data-stu-id="052f4-238">Submit ideas for a campaign.</span></span>
* <span data-ttu-id="052f4-239">Veja a ideia de outro membro da equipe.</span><span class="sxs-lookup"><span data-stu-id="052f4-239">View other team member's idea.</span></span>
* <span data-ttu-id="052f4-240">Vote nas ideias mais curtidas.</span><span class="sxs-lookup"><span data-stu-id="052f4-240">Vote on most liked ideas.</span></span>
* <span data-ttu-id="052f4-241">Reveja o desempenho de suas ideias em comparação com outras dentro de uma campanha.</span><span class="sxs-lookup"><span data-stu-id="052f4-241">Review the performance of their ideas compared with others within a campaign.</span></span>

[<span data-ttu-id="052f4-242">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-242">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-employeeideas)

![Gerenciar a exibição da campanha](../assets/images/employee-ideas-manage-campaigns.png) 

## <a name="e-prescriptions"></a><span data-ttu-id="052f4-244">Prescrições eletrônicos</span><span class="sxs-lookup"><span data-stu-id="052f4-244">E-Prescriptions</span></span> 

<span data-ttu-id="052f4-245">O E-Prescriptions é um aplicativo baseado em [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) que melhora a telemedicina e o cuidado virtual, automatizando o processo de emissão de prescrições e-prescritas aos pacientes.</span><span class="sxs-lookup"><span data-stu-id="052f4-245">E-Prescriptions is a [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) based app that enhances telemedicine and virtual care by automating the process of issuing e-prescriptions to patients.</span></span> <span data-ttu-id="052f4-246">Os profissionais médicos podem revisar rapidamente as consultas, gerar prescrições e e-mails com anexos de prescrição e para pacientes diretamente dentro da plataforma Teams.</span><span class="sxs-lookup"><span data-stu-id="052f4-246">Medical professionals can quickly review appointments, generate e-prescriptions, and send emails with e-prescription attachments to patients directly within the Teams platform.</span></span>

[<span data-ttu-id="052f4-247">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-247">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-eprescription) 

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

## <a name="employee-training"></a><span data-ttu-id="052f4-252">Treinamento de Funcionários</span><span class="sxs-lookup"><span data-stu-id="052f4-252">Employee Training</span></span> 

<span data-ttu-id="052f4-253">O treinamento de funcionários é um aplicativo Microsoft Teams que permite aos organizadores publicar, rastrear e promover eventos de aprendizagem e treinamento para sua organização.</span><span class="sxs-lookup"><span data-stu-id="052f4-253">Employee training is a Microsoft Teams app that enables organizers to easily publish, track, and promote learning and training events for your organization.</span></span>  <span data-ttu-id="052f4-254">Com o aplicativo, os planejadores de eventos podem enviar lembretes e notificações para os inscritos do evento e os funcionários podem indicar interesse em eventos futuros, manter-se atualizado sobre eventos atuais e compartilhar detalhes do evento com os colegas através da extensão de mensagens Teams.</span><span class="sxs-lookup"><span data-stu-id="052f4-254">With the app, event planners can send reminders and notifications to event registrants and employees can indicate interest in upcoming events, stay updated on current events, and share event details with colleagues through the Teams messaging extension.</span></span>

[<span data-ttu-id="052f4-255">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-255">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-employeetraining)

:::row:::
:::column span="2":::
    <span data-ttu-id="052f4-256">**Veja eventos de treinamento de funcionários** ![ Imagem da guia de treinamento dos funcionários](../assets/images/employee-training-discover-tab.png)</span><span class="sxs-lookup"><span data-stu-id="052f4-256">**View employee training events** ![Employee training tab image](../assets/images/employee-training-discover-tab.png)</span></span>  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    <span data-ttu-id="052f4-257">**Crie um evento de treinamento de funcionários** ![ Treinamento de funcionários cria formulário de evento](../assets/images/employee-training-create-event.jpg)</span><span class="sxs-lookup"><span data-stu-id="052f4-257">**Create employee training event** ![Employee training create event form](../assets/images/employee-training-create-event.jpg)</span></span>
:::column-end:::
:::row-end:::

## <a name="expert-finder"></a><span data-ttu-id="052f4-258">Expert Finder</span><span class="sxs-lookup"><span data-stu-id="052f4-258">Expert Finder</span></span>

<span data-ttu-id="052f4-259">Expert Finder é um [bot Microsoft Teams](../bots/what-are-bots.md) que identifica membros específicos da organização com base em suas habilidades, interesses e atributos de educação.</span><span class="sxs-lookup"><span data-stu-id="052f4-259">Expert Finder is a [Microsoft Teams bot](../bots/what-are-bots.md) that identifies specific organization members based on their skills, interests, and education attributes.</span></span> <span data-ttu-id="052f4-260">Os membros encontram especialistas dentro de uma organização que correspondem a uma pesquisa de palavras-chave de Azure Active Directory perfis de usuários.</span><span class="sxs-lookup"><span data-stu-id="052f4-260">Members find experts within an organization that match a keyword search of Azure Active Directory user profiles.</span></span>

[<span data-ttu-id="052f4-261">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-261">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-expertfinder)

![Demonstração de resultados de pesquisa do Expert Finder](../assets/images/expert-finder.png)

## <a name="faq-plus"></a><span data-ttu-id="052f4-263">Perguntas Frequentes Plus</span><span class="sxs-lookup"><span data-stu-id="052f4-263">FAQ Plus</span></span>

<span data-ttu-id="052f4-264">Q conversacional&A bots são uma maneira fácil de fornecer respostas para perguntas frequentemente feitas pelos usuários.</span><span class="sxs-lookup"><span data-stu-id="052f4-264">Conversational Q&A bots are an easy way to provide answers to frequently asked questions by users.</span></span> <span data-ttu-id="052f4-265">Mas, a maioria dos bots não consegue se envolver com os usuários de forma significativa porque não há nenhum humano no loop quando o bot falha.</span><span class="sxs-lookup"><span data-stu-id="052f4-265">But, most bots fail to engage with users in meaningful way because there is no human in the loop when the bot fails.</span></span> <span data-ttu-id="052f4-266">Faq bot é um Q amigável&um bot que traz um humano no loop quando ele é incapaz de ajudar.</span><span class="sxs-lookup"><span data-stu-id="052f4-266">FAQ bot is a friendly Q&A bot that brings a human in the loop when it is unable to help.</span></span> <span data-ttu-id="052f4-267">Pode-se fazer uma pergunta ao bot e o bot responde com uma resposta se ele estiver contido na base de conhecimento.</span><span class="sxs-lookup"><span data-stu-id="052f4-267">One can ask the bot a question and the bot responds with an answer if it is contained in the knowledge base.</span></span> <span data-ttu-id="052f4-268">Caso não, o bot permite que o usuário envie uma consulta que, em seguida, é postada em uma equipe pré-configurada de especialistas que ajudam a fornecer suporte agindo sobre as notificações de dentro da própria equipe.</span><span class="sxs-lookup"><span data-stu-id="052f4-268">If not, the bot allows the user to submit a query which then gets posted to a pre-configured team of experts who help to provide support by acting upon the notifications from within the team itself.</span></span>

> [!NOTE]
> <span data-ttu-id="052f4-269">A versão mais recente do **FAQ Plus** suporta resoluções de Q&A aprimoradas, permitindo que uma equipe de especialistas complete o seguinte:</span><span class="sxs-lookup"><span data-stu-id="052f4-269">The latest release of **FAQ Plus** supports improved Q&A resolutions by enabling a team of experts to complete the following:</span></span>
>
> <span data-ttu-id="052f4-270">&#x2714; Adicione novas&Q diretamente à base de conhecimento usando extensões de mensagens.</span><span class="sxs-lookup"><span data-stu-id="052f4-270">&#x2714; Add new Q&As directly to the knowledge base using message extensions.</span></span>
>
> <span data-ttu-id="052f4-271">&#x2714; Editar e excluir q&A pares adicionados por um bot.</span><span class="sxs-lookup"><span data-stu-id="052f4-271">&#x2714; Edit and delete Q&A pairs added by a bot.</span></span>
>
> <span data-ttu-id="052f4-272">&#x2714; Acompanhe a história de revisão do Q&As.</span><span class="sxs-lookup"><span data-stu-id="052f4-272">&#x2714; Track the revision history of Q&As.</span></span>
>
> <span data-ttu-id="052f4-273">&#x2714; Configure uma resposta com detalhes adicionais para exibir como uma [placa adaptativa](../task-modules-and-cards/cards/cards-reference.md#adaptive-card).</span><span class="sxs-lookup"><span data-stu-id="052f4-273">&#x2714; Configure an answer with additional details to display as an [Adaptive Card](../task-modules-and-cards/cards/cards-reference.md#adaptive-card).</span></span>
>
[<span data-ttu-id="052f4-274">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-274">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-faqplusv2)

![FAQ Plus gif](../assets/images/FAQPlusEndUser.gif)

## <a name="get-support-app"></a><span data-ttu-id="052f4-276">Obter aplicativo de suporte</span><span class="sxs-lookup"><span data-stu-id="052f4-276">Get Support App</span></span>

<span data-ttu-id="052f4-277">O aplicativo Get Support é usado por organizações que estão usando Microsoft Teams, para permitir que qualquer conjunto de usuários solicite assistência aos supervisores.</span><span class="sxs-lookup"><span data-stu-id="052f4-277">The Get Support app is used by organizations that are using Microsoft Teams, to enable any set of users to request assistance from supervisors.</span></span> <span data-ttu-id="052f4-278">Este aplicativo inclui os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="052f4-278">This app includes the following features:</span></span>
* <span data-ttu-id="052f4-279">Solicitando assistência em diferentes categorias de um Aplicativo de Energia.</span><span class="sxs-lookup"><span data-stu-id="052f4-279">Requesting assistance on different categories from a Power App.</span></span>
* <span data-ttu-id="052f4-280">Notificações enviadas aos solicitantes informando-os de quem lebre atribuiu.</span><span class="sxs-lookup"><span data-stu-id="052f4-280">Notifications sent to requestors informing them of who hare assigned.</span></span>
* <span data-ttu-id="052f4-281">Notificações enviadas aos supervisores designados informando-os de quem precisa de assistência.</span><span class="sxs-lookup"><span data-stu-id="052f4-281">Notifications sent to assigned supervisors informing them of who needs assistance.</span></span> 
* <span data-ttu-id="052f4-282">Analisando escaladas e padrões em SharePoint e PowerBI.S.</span><span class="sxs-lookup"><span data-stu-id="052f4-282">Analyzing escalations and patterns in SharePoint and PowerBI.S.</span></span>

[<span data-ttu-id="052f4-283">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-283">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-app-get-support/)

![Obter gif de suporte](../assets/images/get-support.gif)

## <a name="goal-tracker"></a><span data-ttu-id="052f4-285">Rastreador de metas</span><span class="sxs-lookup"><span data-stu-id="052f4-285">Goal Tracker</span></span>

<span data-ttu-id="052f4-286">O aplicativo Goal Tracker é uma solução abrangente para sua organização apoiar o estabelecimento de metas, observando o progresso e reconhecendo o sucesso dentro de Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="052f4-286">The Goal Tracker app is a comprehensive solution for your organization to support establishing goals, observing progress, and acknowledging success within Microsoft Teams.</span></span> <span data-ttu-id="052f4-287">O aplicativo permite que os usuários desvelem, rastreiem e atualizem objetivos em nível profissional, pessoal e de equipe.</span><span class="sxs-lookup"><span data-stu-id="052f4-287">The app enables users to set, track, and update objectives on a professional, personal, and team level.</span></span> <span data-ttu-id="052f4-288">Os membros da equipe também recebem lembretes oportunos e atualizações de status para permanecer focados e manter-se no caminho certo.</span><span class="sxs-lookup"><span data-stu-id="052f4-288">Team members also receive timely reminders and status updates to remain focused and stay on track.</span></span>

[<span data-ttu-id="052f4-289">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-289">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-app-goaltracker)

:::row:::
  :::column span="2":::
    ![Definir metas](../assets/images/goal-tracker-set-goals-view.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Ver metas definidas](../assets/images/goal-tracker-your-goals-view.png)
:::column-end:::
:::row-end:::

## <a name="great-ideas"></a><span data-ttu-id="052f4-292">Grandes Ideias</span><span class="sxs-lookup"><span data-stu-id="052f4-292">Great Ideas</span></span>

<span data-ttu-id="052f4-293">O aplicativo Great Ideas apoia e capacita a inovação e a criatividade dentro de sua organização.</span><span class="sxs-lookup"><span data-stu-id="052f4-293">The Great Ideas app supports and empowers innovation and creativity within your organization.</span></span> <span data-ttu-id="052f4-294">O aplicativo permite que seus funcionários compartilhem ideias com colegas e liderança, descubram novas submissões, contribuições de destaque para consideração por pares e votem nas melhores propostas dentro de Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="052f4-294">The app enables your employees to share ideas with colleagues and leadership, discover new submissions, spotlight contributions for peer consideration, and cast their vote for the best proposals within Microsoft Teams.</span></span>

[<span data-ttu-id="052f4-295">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-295">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-greatideas)

:::row:::
  :::column span="2":::
    ![Exibir ideias submetidas](../assets/images/great-ideas-all-view.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Ver ideias](../assets/images/great-ideas-digest-view.png)
:::column-end:::
:::row-end:::

## <a name="group-activities"></a><span data-ttu-id="052f4-298">Atividades em grupo</span><span class="sxs-lookup"><span data-stu-id="052f4-298">Group Activities</span></span>

<span data-ttu-id="052f4-299">O Group Activities é um aplicativo Microsoft Teams que facilita que os proprietários de equipes criem rapidamente grupos de atividades e gerenciem fluxos de trabalho de colaboração no contexto de Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="052f4-299">Group Activities is a Microsoft Teams app that makes it easy for team owners to quickly create activity groups and manage collaboration workflows within the context of Microsoft Teams.</span></span> <span data-ttu-id="052f4-300">Os autores de atividades são habilitados a criar atividades, distribuir aleatoriamente membros da equipe em grupos e, opcionalmente, fazer com que o bot envie lembretes até que as atividades sejam concluídas.</span><span class="sxs-lookup"><span data-stu-id="052f4-300">Activity authors are enabled to create activities, randomly distribute team members in groups, and optionally have the bot send reminders until activities are complete.</span></span>

[<span data-ttu-id="052f4-301">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-301">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-groupactivities)

:::row:::
  :::column span="2":::
    ![Lista de atividades em grupo em Teams](../assets/images/group-activities-1.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Mensagem de notificação de atividades em grupo em um canal](../assets/images/group-activities-2.png)
:::column-end:::
:::row-end:::

## <a name="group-connect-9734"></a><span data-ttu-id="052f4-304">Conexão &#9734; do Grupo</span><span class="sxs-lookup"><span data-stu-id="052f4-304">Group Connect &#9734;</span></span>

<span data-ttu-id="052f4-305">O Group Conexão é um aplicativo Microsoft Teams que ajuda os membros da organização a descobrir grupos de funcionários e a encontrar informações relevantes para grupos de funcionários.</span><span class="sxs-lookup"><span data-stu-id="052f4-305">Group Connect is a Microsoft Teams app that helps organization members discover employee groups and find information relevant to employee groups.</span></span> <span data-ttu-id="052f4-306">O aplicativo vem embutido com ricas capacidades para os líderes da organização se comunicarem com seus funcionários sobre grupos, eventos e recursos.</span><span class="sxs-lookup"><span data-stu-id="052f4-306">The app comes built-in with rich capabilities for organization leaders to communicate with their employees regarding groups, events, and resources.</span></span> <span data-ttu-id="052f4-307">O aplicativo Group Conexão também combina os membros do grupo entre si na frequência desejada para incentivar a rede e a coesão dentro de um grupo.</span><span class="sxs-lookup"><span data-stu-id="052f4-307">The Group Connect app also matches group members with each other at their desired frequency to encourage networking and cohesion within a group.</span></span> <span data-ttu-id="052f4-308">Para obter mais informações sobre como você pode aproveitar o aplicativo Group Conexão para ajudar os grupos de funcionários a promover dentro de sua organização, consulte o aplicativo em GitHub.</span><span class="sxs-lookup"><span data-stu-id="052f4-308">For more information on how you can leverage the Group Connect app to help employee groups foster within your organization, see the app on GitHub.</span></span>

[<span data-ttu-id="052f4-309">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-309">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-groupconnect)

![Descubra grupos D&I](https://github.com/OfficeDev/microsoft-teams-apps-diversityandinclusion/wiki/Images/temp_group_connect_landing.png)

## <a name="grow-your-skills"></a><span data-ttu-id="052f4-311">Cresça suas habilidades</span><span class="sxs-lookup"><span data-stu-id="052f4-311">Grow Your Skills</span></span>

<span data-ttu-id="052f4-312">O aplicativo Grow Your Skills apoia o crescimento e o desenvolvimento profissional, permitindo que os funcionários contribuam para projetos suplementares para sua organização e, ao mesmo tempo, aprendam novas habilidades.</span><span class="sxs-lookup"><span data-stu-id="052f4-312">The Grow Your Skills app supports professional growth and development by enabling employees to contribute to supplemental projects for your organization while simultaneously learning new skills.</span></span> <span data-ttu-id="052f4-313">Os funcionários podem usar o aplicativo para localizar oportunidades que atendam aos seus interesses, desfrutem de colaboração significativa com os pares e adquiram novos níveis de experiência e recursos, tudo dentro do ambiente Teams.</span><span class="sxs-lookup"><span data-stu-id="052f4-313">Employees can use the app to locate opportunities that meet their interests, enjoy meaningful collaboration with peers, and acquire new levels of expertise and capabilities, all within the Teams environment.</span></span>

[<span data-ttu-id="052f4-314">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-314">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-growyourskills)

:::row:::
  :::column span="2":::
    ![Visualização de projetos disponíveis](../assets/images/grow-your-skills-all-projects-view.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Visão de habilidades adquiridas pelo espectador](../assets/images/grow-your-skills-acquired-skills-view.png)
:::column-end:::
:::row-end:::

## <a name="hr-support"></a><span data-ttu-id="052f4-317">Suporte de RH</span><span class="sxs-lookup"><span data-stu-id="052f4-317">HR Support</span></span>

<span data-ttu-id="052f4-318">O bot de suporte de RH é um robô Q amigável&um bot que traz um profissional de suporte ou especialista da equipe de RH no loop quando ele não pode ajudar.</span><span class="sxs-lookup"><span data-stu-id="052f4-318">HR Support bot is a friendly Q&A bot that brings a support professional or expert from the HR team in the loop when it is unable to help.</span></span> <span data-ttu-id="052f4-319">Pode-se fazer uma pergunta ao bot e o bot responde com uma resposta se ele estiver contido na base de conhecimento.</span><span class="sxs-lookup"><span data-stu-id="052f4-319">One can ask the bot a question and the bot responds with an answer if it is contained in the knowledge base.</span></span> <span data-ttu-id="052f4-320">Caso não, o bot permite que o usuário envie uma consulta que, em seguida, é postada em uma equipe pré-configurada de especialistas que ajudam a fornecer suporte agindo sobre as notificações de dentro de sua própria equipe.</span><span class="sxs-lookup"><span data-stu-id="052f4-320">If not, the bot allows the user to submit a query which then gets posted in a pre-configured team of experts who are help to provide support by acting upon the notifications from within their team itself.</span></span> <span data-ttu-id="052f4-321">Além disso, o bot sugere links para políticas de RH recomendadas ou perguntas, procurando por tags pré-configuradas na questão.</span><span class="sxs-lookup"><span data-stu-id="052f4-321">Additionally, the bot suggests links to recommended HR policies or questions by searching for pre-configured tags in the question.</span></span> <span data-ttu-id="052f4-322">Estas telhas são encontradas na guia associada como uma referência rápida.</span><span class="sxs-lookup"><span data-stu-id="052f4-322">These tiles are found in the associated tab as a quick reference.</span></span> <span data-ttu-id="052f4-323">O Suporte de RH funciona bem para o peso leve Q&A e para fornecer suporte rápido ao lançar novos projetos ou iniciativas na organização.</span><span class="sxs-lookup"><span data-stu-id="052f4-323">HR Support works well for light weight Q&A and to provide quick support when launching new projects or initiatives in the organization.</span></span>

[<span data-ttu-id="052f4-324">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-324">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-hrsupport-app)

![Suporte de RH](../assets/images/expert-user.png)

## <a name="icebreaker"></a><span data-ttu-id="052f4-326">Frases de apresentação</span><span class="sxs-lookup"><span data-stu-id="052f4-326">Icebreaker</span></span>

<span data-ttu-id="052f4-327">Icebreaker é um [bot Microsoft Teams](../bots/what-are-bots.md) que ajuda sua equipe a se aproximar, emparelhando dois membros aleatórios da equipe a cada semana para se encontrar.</span><span class="sxs-lookup"><span data-stu-id="052f4-327">Icebreaker is a [Microsoft Teams bot](../bots/what-are-bots.md) that helps your team get closer by pairing two random team members up every week to meet.</span></span> <span data-ttu-id="052f4-328">O bot facilita o agendamento, sugerindo automaticamente horários livres que funcionam para ambos os membros.</span><span class="sxs-lookup"><span data-stu-id="052f4-328">The bot makes scheduling easy by automatically suggesting free times that work for both members.</span></span> <span data-ttu-id="052f4-329">Fortaleça conexões pessoais e construa uma comunidade de malha com este aplicativo.</span><span class="sxs-lookup"><span data-stu-id="052f4-329">Strengthen personal connections and build a tightly knit community with this app.</span></span>

<span data-ttu-id="052f4-330">Além de incentivar conexões pessoais em toda a sua equipe, o aplicativo Icebreaker pode ajudar a cultivar comunidades baseadas em interesse dentro de sua organização.</span><span class="sxs-lookup"><span data-stu-id="052f4-330">In addition to encouraging personal connections across your entire team, the Icebreaker app can help cultivate interest-based communities within your organization.</span></span> <span data-ttu-id="052f4-331">Por exemplo, você pode usar este aplicativo para um grupo de interesse DevOps para ajudar ideias e práticas recomendadas organicamente espalhadas por toda a sua organização.</span><span class="sxs-lookup"><span data-stu-id="052f4-331">For example, you can use this app for a DevOps interest group to help ideas and best practices organically spread across your organization.</span></span>

[<span data-ttu-id="052f4-332">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-332">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-icebreaker-app)

![Aplicativo icebreaker](../assets/images/icebreaker.png)

## <a name="incentives"></a><span data-ttu-id="052f4-334">Incentivos</span><span class="sxs-lookup"><span data-stu-id="052f4-334">Incentives</span></span>

<span data-ttu-id="052f4-335">Os incentivos são um modelo [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) que gerencia e acompanha a participação incentivada dos colaboradores em atividades designadas, como treinamentos e iniciativas de gestão de mudanças.</span><span class="sxs-lookup"><span data-stu-id="052f4-335">Incentives is a [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) template that manages and tracks incentivized employee participation in designated activities, such as trainings and change management initiatives.</span></span> <span data-ttu-id="052f4-336">Os administradores usam o aplicativo para estabelecer atividades designadas, atribuir pontos para conclusão e especificar níveis de ponto de elegibilidade necessários para recompensas.</span><span class="sxs-lookup"><span data-stu-id="052f4-336">Admins use the app to establish designated activities, assign points for completion, and specify required eligibility point levels for rewards.</span></span> <span data-ttu-id="052f4-337">Os funcionários usam o aplicativo para visualizar seus pontos acumulados e, ao atingir a elegibilidade, solicitar e reivindicar recompensas resgatáveis.</span><span class="sxs-lookup"><span data-stu-id="052f4-337">Employees use the app to view their accumulated points and, upon reaching eligibility, request and claim redeemable rewards.</span></span>

[<span data-ttu-id="052f4-338">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-338">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-incentives)

![Demonstração do aplicativo de incentivos](../assets/images/incentives-app.png)

## <a name="incident-reporter"></a><span data-ttu-id="052f4-340">Repórter de Incidente</span><span class="sxs-lookup"><span data-stu-id="052f4-340">Incident Reporter</span></span>

<span data-ttu-id="052f4-341">Incident Reporter é um [bot Microsoft Teams](../bots/what-are-bots.md) que otimiza a gestão de incidentes em sua organização.</span><span class="sxs-lookup"><span data-stu-id="052f4-341">Incident Reporter is a [Microsoft Teams bot](../bots/what-are-bots.md)  that optimizes the management of incidents in your organization.</span></span> <span data-ttu-id="052f4-342">O bot facilita a coleta automatizada de dados de incidentes, relatórios personalizados de incidentes, notificações relevantes das partes interessadas e rastreamento de incidentes de ponta a ponta.</span><span class="sxs-lookup"><span data-stu-id="052f4-342">The bot facilitates automated incident data collection, customized incident reports, relevant stakeholder notifications, and end-to-end incident tracking.</span></span>

[<span data-ttu-id="052f4-343">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-343">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-incidentreport)

:::row:::
  :::column span="2":::
    ![Visão de escopo do grupo de repórteres incidentes](../assets/images/incident-reporter-02.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Visão de escopo pessoal do repórter incidente](../assets/images/incident-reporter-01.jpg)
:::column-end:::
:::row-end:::

## <a name="inspection"></a><span data-ttu-id="052f4-346">inspeção</span><span class="sxs-lookup"><span data-stu-id="052f4-346">Inspection</span></span> 

 <span data-ttu-id="052f4-347">A inspeção é um aplicativo Microsoft Teams que permite que os trabalhadores da linha de frente inspecionem qualquer coisa, desde locais até ativos e equipamentos.</span><span class="sxs-lookup"><span data-stu-id="052f4-347">Inspection is a Microsoft Teams app that enables front line workers to inspect anything from  locations to assets and equipments.</span></span> <span data-ttu-id="052f4-348">Por exemplo, uma loja de varejo, fábrica ou veículos e máquinas.</span><span class="sxs-lookup"><span data-stu-id="052f4-348">For example, a retail store, manufacturing plant, or vehicles and machines.</span></span> <span data-ttu-id="052f4-349">Existem dois aplicativos nesta solução, cada um destinado a diferentes tipos de usuários.</span><span class="sxs-lookup"><span data-stu-id="052f4-349">There are two apps in this solution, each intended for different types of users.</span></span>

<span data-ttu-id="052f4-350">O aplicativo capacita os trabalhadores da linha de frente a inspecionar um ativo ou área, gerenciar a qualidade dos produtos e serviços ou manter a segurança no local de trabalho.</span><span class="sxs-lookup"><span data-stu-id="052f4-350">The app empowers the front line workers to inspect an asset or area, to manage quality of products and services, or maintain safety at workplace.</span></span> <span data-ttu-id="052f4-351">Facilita a comunicação entre os membros da equipe para resolver problemas encontrados durante a inspeção.</span><span class="sxs-lookup"><span data-stu-id="052f4-351">It facilitates communication between team members to address issues found during inspection.</span></span> <span data-ttu-id="052f4-352">O aplicativo fornece relatórios simples para os gestores agilizarem a resolução de problemas e destacarem tendências.</span><span class="sxs-lookup"><span data-stu-id="052f4-352">The app provides simple reports for managers to expedite issue resolution and highlight trends.</span></span>

[<span data-ttu-id="052f4-353">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-353">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-inspection)

 ![Visão geral da inspeção](../assets/images/inspection-app.png)  


## <a name="issue-reporting"></a><span data-ttu-id="052f4-355">Relatórios de problemas</span><span class="sxs-lookup"><span data-stu-id="052f4-355">Issue Reporting</span></span>

<span data-ttu-id="052f4-356">O aplicativo Issue Reporting capacita os funcionários e gestores a levantar e gerenciar problemas.</span><span class="sxs-lookup"><span data-stu-id="052f4-356">The Issue Reporting app empowers the employees and managers to raise and manage issues.</span></span> <span data-ttu-id="052f4-357">Ele consiste em dois aplicativos, aplicativo de relatórios de em questão para problemas de emissão e aplicativo Gerenciar problemas para gerenciar problemas.</span><span class="sxs-lookup"><span data-stu-id="052f4-357">It consists of two apps, Issue reporting app for reporting issues and Manage Issues app for managing issues.</span></span>

<span data-ttu-id="052f4-358">Os gerentes de equipe usam o aplicativo Gerenciar problemas para configurar a experiência do aplicativo, incluindo o canal no qual Microsoft Teams mensagens e tarefas do Planner são criadas pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="052f4-358">The team managers use the Manage Issues app to configure the app experience, including the channel in which Microsoft Teams messages and Planner tasks are created by the app.</span></span> <span data-ttu-id="052f4-359">Os gerentes também usam o aplicativo para criar formulários de modelo para coletar detalhes quando um usuário relata um problema.</span><span class="sxs-lookup"><span data-stu-id="052f4-359">Managers also use the app to create template forms to collect details when a user reports an issue.</span></span> <span data-ttu-id="052f4-360">Por exemplo, revisar, editar ou excluir formulários de modelo de problema.</span><span class="sxs-lookup"><span data-stu-id="052f4-360">For example, review, edit, or delete issue template forms.</span></span> <span data-ttu-id="052f4-361">O aplicativo também é usado para revisar problemas da equipe, relatar o histórico de problemas e gerenciar eficientemente a resolução de problemas.</span><span class="sxs-lookup"><span data-stu-id="052f4-361">The app is also used to review team issues, report on issue history, and efficiently manage issue resolution.</span></span>

<span data-ttu-id="052f4-362">Os funcionários usam o aplicativo de relatórios de problemas para registrar problemas e detalhes necessários para resolvê-los.</span><span class="sxs-lookup"><span data-stu-id="052f4-362">The employees use the Issue reporting app to log issues and details required to resolve them.</span></span> <span data-ttu-id="052f4-363">O aplicativo também é usado para modificar e resolver problemas existentes e obter uma visão de alto nível dos problemas individuais ou de equipe.</span><span class="sxs-lookup"><span data-stu-id="052f4-363">The app is also used to modify and resolve existing issues and get a high-level view of individual or team issues.</span></span>

[<span data-ttu-id="052f4-364">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-364">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-issuereporting)

![Exibição da equipe de relatórios de problemas](../assets/images/issue-reporting-team-view.png)  

## <a name="new-employee-onboarding"></a><span data-ttu-id="052f4-366">Novo onboarding de funcionários</span><span class="sxs-lookup"><span data-stu-id="052f4-366">New Employee Onboarding</span></span> 

<span data-ttu-id="052f4-367">O New Employee Onboarding é uma solução integrada de Microsoft Teams e [SharePoint Novo Onboarding de Funcionários](https://lookbook.microsoft.com/details/75e60a32-9849-4ed4-b83e-b2b08983ad19) que permite que sua organização forneça uma experiência de onboarding consistente e de alta qualidade para os funcionários em sua jornada de contratação nova.</span><span class="sxs-lookup"><span data-stu-id="052f4-367">New Employee Onboarding is an integrated Microsoft Teams and [SharePoint New Employee Onboarding Solution](https://lookbook.microsoft.com/details/75e60a32-9849-4ed4-b83e-b2b08983ad19) that enables your organization to provide a consistent, high-quality onboarding experience for employees on their new-hire journey.</span></span> <span data-ttu-id="052f4-368">O aplicativo é usado por equipes de recursos humanos e gerentes de contratação para fornecer informações relevantes durante todo o processo de orientação e indução e por novas contratações para compartilhar feedback, fornecer introduções e tarefas completas de onboarding.</span><span class="sxs-lookup"><span data-stu-id="052f4-368">The app is used by human resource teams and hiring managers to provide relevant information throughout the orientation and induction process and by new hires to share feedback, provide introductions, and complete onboarding tasks.</span></span>

[<span data-ttu-id="052f4-369">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-369">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-newemployeeonboarding)

:::row:::
  :::column span="2":::
    <span data-ttu-id="052f4-370">**Novo cartão de boas-vindas do funcionário** ![ Imagem do novo cartão de boas-vindas do funcionário](../assets/images/new-employee-welcome-card.png)</span><span class="sxs-lookup"><span data-stu-id="052f4-370">**New employee welcome card** ![Image of new employee welcome card](../assets/images/new-employee-welcome-card.png)</span></span>
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    <span data-ttu-id="052f4-371">**Nova lista de verificação de funcionários** ![ Imagem da nova lista de verificação de funcionários](../assets/images/new-employee-checklist.png)</span><span class="sxs-lookup"><span data-stu-id="052f4-371">**New employee checklist** ![Image of new employee checklist](../assets/images/new-employee-checklist.png)</span></span>  
:::column-end:::
:::row-end:::

## <a name="open-badges"></a><span data-ttu-id="052f4-372">Crachás Abertos</span><span class="sxs-lookup"><span data-stu-id="052f4-372">Open Badges</span></span>

<span data-ttu-id="052f4-373">Open Badges é um aplicativo Microsoft Teams que permite que os indivíduos ganhem crachás de credenciais de aprendizagem digital dentro do contexto Teams e compartilhem-nos em todos os lugares.</span><span class="sxs-lookup"><span data-stu-id="052f4-373">Open Badges is a Microsoft Teams app that enables individuals to earn digital learning credential badges within the Teams context and share them everywhere.</span></span> <span data-ttu-id="052f4-374">Usando recursos da autoridade de emissão de crachás digitais de terceiros, [o Badgr](https://badgr.org/), crachás premiados são registrados no perfil Badgr de um destinatário e disponíveis para construir e compartilhar uma rica imagem das jornadas de aprendizagem ao longo da vida.</span><span class="sxs-lookup"><span data-stu-id="052f4-374">Using capabilities from the third-party digital badge issuing authority, [Badgr](https://badgr.org/), awarded badges are recorded in a recipient's Badgr profile and available to build and share a rich picture of lifetime learning journeys.</span></span>

[<span data-ttu-id="052f4-375">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-375">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-openbadges)

:::row:::
  :::column span="2":::
    ![Imagem dos crachás disponíveis](../assets/images/open-badges-1.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Exibição de crachás premiados](../assets/images/open-badges-2.png)
:::column-end:::
:::row-end:::

## <a name="poll"></a><span data-ttu-id="052f4-378">pesquisa</span><span class="sxs-lookup"><span data-stu-id="052f4-378">Poll</span></span> 

<span data-ttu-id="052f4-379">A enquete é um aplicativo personalizado de [extensão de mensagens](../messaging-extensions/what-are-messaging-extensions.md) Microsoft Teams que permite criar e enviar pesquisas rapidamente em um chat ou um canal para reunir opiniões e preferências da equipe.</span><span class="sxs-lookup"><span data-stu-id="052f4-379">Poll is a custom Microsoft Teams [messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that enables you to quickly create and send polls in a chat or a channel to gather team opinions and preferences.</span></span> <span data-ttu-id="052f4-380">O aplicativo é suportado em todos os clientes Teams plataforma, como desktop, navegador, iOS e Android e está pronto para implantação como parte de sua assinatura Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="052f4-380">The app is supported across all Teams platform clients, such as desktop, browser, iOS, and Android and is ready for deployment as part of your Microsoft 365 subscription.</span></span>

[<span data-ttu-id="052f4-381">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-381">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-poll-app)

:::row:::
  :::column span="1":::
    ![Criar enquete em Teams visualização](../assets/images/poll-app-template-compose-view.gif)  
:::column-end:::
:::row-end:::

## <a name="quick-responses"></a><span data-ttu-id="052f4-383">Respostas rápidas</span><span class="sxs-lookup"><span data-stu-id="052f4-383">Quick Responses</span></span>

<span data-ttu-id="052f4-384">Quick Responses é um aplicativo Microsoft Teams que oferece uma solução robusta para responder efetivamente às perguntas dos usuários perguntas frequentes.</span><span class="sxs-lookup"><span data-stu-id="052f4-384">Quick Responses is a Microsoft Teams app that delivers a robust solution for effectively answering users' commonly asked questions FAQs.</span></span> <span data-ttu-id="052f4-385">Em vez de responder a cada consulta manual e continuamente repetindo informações, o aplicativo constrói uma biblioteca de respostas para uma experiência interativa do usuário através de [extensões de mensagens](../messaging-extensions/what-are-messaging-extensions.md)Teams .</span><span class="sxs-lookup"><span data-stu-id="052f4-385">Instead of answering each query manually and continuously repeating information, the app builds a library of responses for an interactive user experience through Teams [messaging extensions](../messaging-extensions/what-are-messaging-extensions.md).</span></span>

[<span data-ttu-id="052f4-386">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-386">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-quickresponses)

![Visão amostral das respostas](../assets/images/quick-responses.png)

## <a name="quiz--9734"></a><span data-ttu-id="052f4-388">&#9734; de quiz</span><span class="sxs-lookup"><span data-stu-id="052f4-388">Quiz  &#9734;</span></span>

<span data-ttu-id="052f4-389">Quiz é um aplicativo de [extensão de mensagens Teams](../messaging-extensions/what-are-messaging-extensions.md) personalizado que permite criar um quiz dentro de um chat ou um canal para verificação de conhecimento e resultados instantâneos.</span><span class="sxs-lookup"><span data-stu-id="052f4-389">Quiz is a custom [Teams messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that enables you to create a quiz within a chat or a channel for knowledge check and instantaneous results.</span></span> <span data-ttu-id="052f4-390">Você pode usar quiz para, exames in-class e off-line, verificação de conhecimento dentro da equipe, e para testes divertidos dentro de uma equipe.</span><span class="sxs-lookup"><span data-stu-id="052f4-390">You can use Quiz for, In-class and offline exams, Knowledge check within team, and for fun quizzes within a team.</span></span> <span data-ttu-id="052f4-391">O aplicativo Quiz é suportado em várias plataformas, como Teams clientes desktop, navegador, iOS e Android.</span><span class="sxs-lookup"><span data-stu-id="052f4-391">Quiz app is supported across multiple platforms, such as Teams desktop, browser, iOS, and Android clients.</span></span> <span data-ttu-id="052f4-392">Este aplicativo está pronto para implantação como parte de sua assinatura Microsoft 365 existente.</span><span class="sxs-lookup"><span data-stu-id="052f4-392">This app is ready for deployment as part of your existing Microsoft 365 subscription.</span></span>

[<span data-ttu-id="052f4-393">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-393">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-quiz)

:::row:::
  :::column span="1":::
    ![Criar quiz na exibição Teams](../assets/images/quiz-app-template-compose-view.gif)  
:::column-end:::
:::row-end:::

## <a name="rapid-assist"></a><span data-ttu-id="052f4-395">Assistência rápida</span><span class="sxs-lookup"><span data-stu-id="052f4-395">Rapid Assist</span></span>

<span data-ttu-id="052f4-396">Rapid Assist é um aplicativo baseado em [Microsoft Power Platform](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/) que permite que os associados que enfrentam os clientes se conectem rapidamente com os especialistas para obter respostas rápidas, procurar informações, acompanhar solicitações abertas e permitir que especialistas recebam notificações para receber rapidamente uma chamada para ajudar a responder perguntas.</span><span class="sxs-lookup"><span data-stu-id="052f4-396">Rapid Assist is a Microsoft [Power Platform](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/) based app that allows customer facing associates to rapidly connect with the experts to get quick answers, search for information, follow up open requests, and allow experts to receive notifications to quickly get on a call to help answer questions.</span></span> <span data-ttu-id="052f4-397">O aplicativo construído usando [Power Apps](/powerapps/powerapps-overview) e [Power Automate](/power-automate/getting-started)da Microsoft, integra-se profundamente com Microsoft Teams para permitir que as organizações conectem facilmente os trabalhadores da linha de frente com as ligações corporativas para resolver consultas ao cliente e oferecer uma ótima experiência ao cliente.</span><span class="sxs-lookup"><span data-stu-id="052f4-397">The app built using Microsoft [Power Apps](/powerapps/powerapps-overview) and [Power Automate](/power-automate/getting-started), deeply integrates with Microsoft Teams to enable organizations to easily connect frontline workers with corporate liaisons to resolve customer queries and deliver a great customer experience.</span></span> 

[<span data-ttu-id="052f4-398">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-398">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-rapid-assist)

:::row:::
   :::column span="":::
     ![Interface de solicitação de usuário final](../assets/images/EndUserHome.png)
   :::column-end:::
   :::column span="":::
      ![Visão de solicitação de especialista](../assets/images/ExpertViewRequests.png)
   :::column-end:::
:::row-end:::

## <a name="reflect"></a><span data-ttu-id="052f4-401">refletir</span><span class="sxs-lookup"><span data-stu-id="052f4-401">Reflect</span></span> 

<span data-ttu-id="052f4-402">Reflect é um aplicativo personalizado de [extensão de mensagens](../messaging-extensions/what-are-messaging-extensions.md) Microsoft Teams que fornece um recurso seguro e inclusivo para que seus membros da equipe compartilhem o estado de seu bem-estar emocional com colegas ou líderes de grupo diretamente dentro de Teams.</span><span class="sxs-lookup"><span data-stu-id="052f4-402">Reflect is a custom Microsoft Teams [messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that provides a safe and inclusive resource for your team members to share the state of their emotional well-being with colleagues or group leaders directly within Teams.</span></span> <span data-ttu-id="052f4-403">O aplicativo está disponível em chats de canal, grupo, reunião e 1:1 e a resposta de check-in é definida para público, privado para remetente ou totalmente anônimo.</span><span class="sxs-lookup"><span data-stu-id="052f4-403">The app is available in channel, group, meeting, and 1:1 chats and the check-in response is set to public, private-to-sender, or fully anonymous.</span></span>

[<span data-ttu-id="052f4-404">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-404">Get it on GitHub</span></span>](https://github.com/OfficeDev/Microsoft-Teams-App-Reflect)

:::row:::
    :::column:::
    <span data-ttu-id="052f4-405">**Pesquisa de bem-estar**</span><span class="sxs-lookup"><span data-stu-id="052f4-405">**Well-being poll**</span></span>
    
    ![Refletir enquete de usuários de aplicativos](../assets/images/reflect-app-user-poll.png)
    :::column-end:::
:::row-end:::

## <a name="remote-support"></a><span data-ttu-id="052f4-407">Suporte remoto</span><span class="sxs-lookup"><span data-stu-id="052f4-407">Remote Support</span></span>

<span data-ttu-id="052f4-408">O Remote Support é um [bot Microsoft Teams](../bots/what-are-bots.md) que fornece uma interface focada entre solicitantes de suporte em toda a sua organização e a equipe de suporte interno.</span><span class="sxs-lookup"><span data-stu-id="052f4-408">Remote Support is a [Microsoft Teams bot](../bots/what-are-bots.md) that provides a focused interface between support requesters throughout your organization and the internal support team.</span></span>  <span data-ttu-id="052f4-409">Os usuários finais podem enviar, editar ou retirar solicitações de suporte e a equipe de suporte pode responder, gerenciar e atualizar solicitações todas dentro da plataforma Teams.</span><span class="sxs-lookup"><span data-stu-id="052f4-409">End-users can submit, edit, or withdraw requests for support and the support team can respond, manage, and update requests all within the Teams platform.</span></span>

[<span data-ttu-id="052f4-410">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-410">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-remotesupport)

:::row:::
  :::column span="2":::
    ![Formulário de suporte de solicitação](../assets/images/remote-support-request-form.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Solicitar detalhes de suporte](../assets/images/remote-support-request-details.jpg)
:::column-end:::
:::row-end:::

## <a name="request-a-team"></a><span data-ttu-id="052f4-413">Solicitação-a-equipe</span><span class="sxs-lookup"><span data-stu-id="052f4-413">Request-a-team</span></span>

<span data-ttu-id="052f4-414">Request-a-team é um aplicativo Microsoft Teams que otimiza a criação de novas equipes para sua organização corporativa.</span><span class="sxs-lookup"><span data-stu-id="052f4-414">Request-a-team is a Microsoft Teams app that optimizes new team creation for your enterprise organization.</span></span> <span data-ttu-id="052f4-415">O aplicativo suporta padronização e práticas recomendadas ao criar novas instâncias de equipe através da integração de um formulário de solicitação guiado por assistente, um processo de aprovação incorporado, um painel de status de solicitação e compilações automatizadas da equipe.</span><span class="sxs-lookup"><span data-stu-id="052f4-415">The app supports standardization and best practices when creating new team instances through the integration of a wizard-guided request form, an embedded approval process, a request status dashboard, and automated team builds.</span></span>

[<span data-ttu-id="052f4-416">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-416">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-requestateam)

:::row:::
  :::column span="2":::
    ![Exibição da página de início de uma equipe](../assets/images/request-a-team-two.jpg)
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Visualização da página do assistente de solicitação por equipe](../assets/images/request-a-team-three.png)
:::column-end:::
:::row-end:::

## <a name="scrums-for-channels"></a><span data-ttu-id="052f4-419">Scrums para Canais</span><span class="sxs-lookup"><span data-stu-id="052f4-419">Scrums for Channels</span></span>

<span data-ttu-id="052f4-420">Scrums for Channels é um aplicativo de assistente scrum que permite que os usuários agendem e executem scrums em canais dentro de Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="052f4-420">Scrums for Channels is a scrum assistant app that enables users to schedule and run scrums in channels within Microsoft Teams.</span></span> <span data-ttu-id="052f4-421">O aplicativo é ótimo para equipes remotas e equipes compostas por membros de locais geográficos variados e fusos horários para compartilhar atualizações diárias e garantir a participação em reuniões de stand-up scrum.</span><span class="sxs-lookup"><span data-stu-id="052f4-421">The app is great for remote teams and teams comprised of members from varied geographical locations and time zones to share daily updates and ensure participation in scrum stand-up meetings.</span></span>

[<span data-ttu-id="052f4-422">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-422">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-scrumsforchannels)

> [!NOTE]
> <span data-ttu-id="052f4-423">Para realizar reuniões de scrum em um bate-papo em grupo, consulte o modelo de aplicativo [Scrums for Group Chat.](#scrums-for-group-chat)</span><span class="sxs-lookup"><span data-stu-id="052f4-423">To conduct scrum meetings in a group chat, see [Scrums for Group Chat](#scrums-for-group-chat) app template.</span></span>

:::row:::
  :::column span="2":::
    ![Scrums para visualização de configurações de canais](../assets/images/scrum-for-channels-settings.png)
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Scrums para canais de visualização de status de membro da equipe](../assets/images/scrum-for-channels-status.png)
:::column-end:::
:::row-end:::

## <a name="scrums-for-group-chat"></a><span data-ttu-id="052f4-426">Scrums para bate-papo em grupo</span><span class="sxs-lookup"><span data-stu-id="052f4-426">Scrums for Group Chat</span></span>

> [!NOTE]
> <span data-ttu-id="052f4-427">O modelo do aplicativo Scrums Status é atualizado e agora é Scrums for Group Chat.</span><span class="sxs-lookup"><span data-stu-id="052f4-427">The Scrums Status app template is updated and is now Scrums for Group Chat.</span></span>

<span data-ttu-id="052f4-428">Scrums for Group Chat é um assistente de suporte que permite que os membros do chat em grupo executem reuniões de stand-up assíncronsas e compartilhem facilmente suas atualizações diárias.</span><span class="sxs-lookup"><span data-stu-id="052f4-428">Scrums for Group Chat is a supportive scrum assistant that enables group chat members to run asynchronous stand-up meetings and easily share their daily updates.</span></span> <span data-ttu-id="052f4-429">Ele permite que todos os membros do chat de grupo contribuam para o scrum e visualizem as atualizações feitas por outros no scrum em execução.</span><span class="sxs-lookup"><span data-stu-id="052f4-429">It allows all members of the group chat to contribute to the scrum and view the updates made by others in the running scrum.</span></span>

[<span data-ttu-id="052f4-430">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-430">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-scrumsforgroupchat)

![Scrums para demonstração de bate-papo em grupo](https://raw.githubusercontent.com/wiki/OfficeDev/microsoft-teams-app-scrumstatus/images/StartScrum.jpg)

## <a name="share-now"></a><span data-ttu-id="052f4-432">Compartilhar agora</span><span class="sxs-lookup"><span data-stu-id="052f4-432">Share Now</span></span> 

<span data-ttu-id="052f4-433">O aplicativo Share Now promove a troca positiva de informações entre colegas, permitindo que seus usuários compartilhem facilmente conteúdo dentro do ambiente Teams.</span><span class="sxs-lookup"><span data-stu-id="052f4-433">The Share Now app promotes the positive exchange of information between colleagues by enabling your users to easily share content within the Teams environment.</span></span> <span data-ttu-id="052f4-434">Os usuários engajam o aplicativo para compartilhar itens de interesse com os membros da equipe, descobrir novos conteúdos compartilhados, definir preferências e marcar favoritos para leitura posterior.</span><span class="sxs-lookup"><span data-stu-id="052f4-434">Users engage the app to share items of interest with team members, discover new shared content, set preferences, and bookmark favorites for later reading.</span></span>

[<span data-ttu-id="052f4-435">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-435">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-sharenow)

![Selecione a exibição de conteúdo](../assets/images/share-now-suggested-content.png)

## <a name="sharepoint-list-search"></a><span data-ttu-id="052f4-437">Pesquisa de lista do SharePoint</span><span class="sxs-lookup"><span data-stu-id="052f4-437">SharePoint List Search</span></span>

<span data-ttu-id="052f4-438">A colaboração em Microsoft Teams frequentemente faz referência às informações contidas nos itens em uma lista SharePoint.</span><span class="sxs-lookup"><span data-stu-id="052f4-438">Collaboration in Microsoft Teams quite often references information contained within items in a SharePoint list.</span></span> <span data-ttu-id="052f4-439">Colar um link para o item em questão força todos a mudar o contexto da conversa, encontrar as informações necessárias e, em seguida, retornar ao Teams para continuar a conversa.</span><span class="sxs-lookup"><span data-stu-id="052f4-439">Paste a link to the item in question forces everyone to switch context away from the conversation, find the needed information, then return to Teams to continue the conversation.</span></span> <span data-ttu-id="052f4-440">À medida que a conversa continua, as pessoas têm que voltar ao item de referência várias vezes para verificar novos comentários e atualizar suas memórias das informações contidas no item.</span><span class="sxs-lookup"><span data-stu-id="052f4-440">As the conversation continues  people have to switch back to the reference item multiple times to verify new comments and refresh their memories of the information contained within the item.</span></span> <span data-ttu-id="052f4-441">Essa comutação de contexto cria uma barreira para uma colaboração suave.</span><span class="sxs-lookup"><span data-stu-id="052f4-441">This context switching creates a barrier to smooth collaboration.</span></span>
<span data-ttu-id="052f4-442">Para resolver esse problema, o modelo do aplicativo Listar busca é usado.</span><span class="sxs-lookup"><span data-stu-id="052f4-442">To resolve this problem, the List Search app template is used.</span></span> <span data-ttu-id="052f4-443">Muitos usuários usam SharePoint para alimentar alguns dos principais fluxos de trabalho em suas organizações.</span><span class="sxs-lookup"><span data-stu-id="052f4-443">Many users use SharePoint to power some of the core workflows in their organizations.</span></span> <span data-ttu-id="052f4-444">No entanto, colaborar em torno de listas é difícil.</span><span class="sxs-lookup"><span data-stu-id="052f4-444">However, collaborating around lists is difficult.</span></span> <span data-ttu-id="052f4-445">Usando o modelo do aplicativo List Search em Microsoft Teams, os usuários podem inserir informações de SharePoint listar itens diretamente dentro de uma conversa de chat para aliviar a troca de contexto causada ao simplesmente inserir um link em um chat.</span><span class="sxs-lookup"><span data-stu-id="052f4-445">Using the List Search app template in Microsoft Teams, users can insert information from SharePoint list items directly within a chat conversation to alleviate the context-switching caused when simply inserting a link into a chat.</span></span> <span data-ttu-id="052f4-446">As informações são inseridas como um cartão auto-formatado fácil de ler, ajudando os usuários a permanecerem engajados na conversa.</span><span class="sxs-lookup"><span data-stu-id="052f4-446">The information is inserted as an easy-to-read auto-formatted card, helping the users stay engaged in the conversation.</span></span>

[<span data-ttu-id="052f4-447">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-447">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-list-search-app)

![Aplicativo de pesquisa de listas](../assets/images/list-search-template.png)

## <a name="staff-check-ins"></a><span data-ttu-id="052f4-449">Check-ins da equipe</span><span class="sxs-lookup"><span data-stu-id="052f4-449">Staff Check-ins</span></span>

<span data-ttu-id="052f4-450">O Staff Check-ins é um aplicativo baseado em [Power Apps](/powerapps/powerapps-overview) que permite a comunicação de supervisão entre sua empresa e pessoal de campo.</span><span class="sxs-lookup"><span data-stu-id="052f4-450">Staff Check-ins is a [Power Apps](/powerapps/powerapps-overview) based app that enables oversight communication between your business and field personnel.</span></span> <span data-ttu-id="052f4-451">A equipe pode facilmente fornecer informações críticas e atualizações de status em uma base agendada ou ad-hoc diretamente de Teams.</span><span class="sxs-lookup"><span data-stu-id="052f4-451">Staff can easily provide time-critical information and status updates on either a scheduled or ad-hoc basis directly from Teams.</span></span> <span data-ttu-id="052f4-452">O aplicativo suporta localização em tempo real, fotos, notas, notificações de lembrete e fluxos de trabalho automatizados.</span><span class="sxs-lookup"><span data-stu-id="052f4-452">The app supports real-time location, photos, notes, reminder notifications, and automated workflows.</span></span>

[<span data-ttu-id="052f4-453">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-453">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-staffcheckins)

![Criar exibição de check-in](../assets/images/staff-check-ins-create.png)

## <a name="survey"></a><span data-ttu-id="052f4-455">Pesquisa</span><span class="sxs-lookup"><span data-stu-id="052f4-455">Survey</span></span>

<span data-ttu-id="052f4-456">O Survey é um aplicativo personalizado de [extensão de mensagens](../messaging-extensions/what-are-messaging-extensions.md) Microsoft Teams que permite criar uma pesquisa em um chat ou um canal para coletar dados e obter insights acionáveis.</span><span class="sxs-lookup"><span data-stu-id="052f4-456">Survey is a custom Microsoft Teams [messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that enables you to create a survey in a chat or a channel to gather data and gain actionable insight.</span></span> <span data-ttu-id="052f4-457">O aplicativo é suportado em todos os clientes Teams plataforma, como desktop, navegador, iOS e Android e está pronto para implantação como parte de sua assinatura Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="052f4-457">The app is supported across all Teams platform clients, such as desktop, browser, iOS, and Android and is ready for deployment as part of your Microsoft 365 subscription.</span></span>  

[<span data-ttu-id="052f4-458">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-458">Get it on GitHub</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Survey-app)

:::row:::
  :::column span="2":::
    ![Criar pesquisa em Teams visualização](../assets/images/survey-app-template-compose-view.gif)
:::column-end:::
:::row-end:::

## <a name="time-tally"></a><span data-ttu-id="052f4-460">Contagem de tempo</span><span class="sxs-lookup"><span data-stu-id="052f4-460">Time Tally</span></span> 

<span data-ttu-id="052f4-461">Um projeto pode incluir várias tarefas, e vários projetos podem ser atribuídos aos funcionários.</span><span class="sxs-lookup"><span data-stu-id="052f4-461">A project can include multiple tasks, and various projects can be assigned to employees.</span></span> <span data-ttu-id="052f4-462">Os gestores são obrigados a entender o andamento do projeto através do tempo gasto pelos colaboradores nessas tarefas.</span><span class="sxs-lookup"><span data-stu-id="052f4-462">Managers are required to understand the project progress through the time spent by the employees on these tasks.</span></span> <span data-ttu-id="052f4-463">Isso pode ser uma atividade complicada, pois os funcionários precisam preencher as planilhas de tempo.</span><span class="sxs-lookup"><span data-stu-id="052f4-463">This can be a cumbersome activity, as the employees need to fill in the timesheets.</span></span> <span data-ttu-id="052f4-464">O aplicativo Time Tally permite que os funcionários preencham suas planilhas de tempo rapidamente, usando o dispositivo móvel, e os gerentes não têm que acompanhar os funcionários na entrada da folha de tempo.</span><span class="sxs-lookup"><span data-stu-id="052f4-464">Time Tally app enables employees to fill their timesheets quickly, using the mobile device, and managers do not have to follow up with employees on the timesheet entry.</span></span> <span data-ttu-id="052f4-465">Os gestores podem visualizar a utilização do projeto com base em recursos, e podem aprovar ou rejeitar as entradas.</span><span class="sxs-lookup"><span data-stu-id="052f4-465">Managers get to view the project utilization based on resources, and they can approve or reject the entries.</span></span> <span data-ttu-id="052f4-466">As notificações de lembrete são enviadas para garantir a conformidade com a folha de tempo.</span><span class="sxs-lookup"><span data-stu-id="052f4-466">Reminder notifications are sent to ensure timesheet compliance.</span></span> <span data-ttu-id="052f4-467">Além disso, dados históricos e utilizaçãos estão disponíveis para análise.</span><span class="sxs-lookup"><span data-stu-id="052f4-467">Also, historical data and utilizations are available for analytics.</span></span>

[<span data-ttu-id="052f4-468">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-468">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-timetally)

![Contagem de tempo](../assets/images/11zon_gif.gif)

## <a name="training--9734"></a><span data-ttu-id="052f4-470">&#9734; de treinamento</span><span class="sxs-lookup"><span data-stu-id="052f4-470">Training  &#9734;</span></span>

<span data-ttu-id="052f4-471">O Training é um aplicativo personalizado [de extensão de mensagens Teams](../messaging-extensions/what-are-messaging-extensions.md) que permite que os usuários publiquem um treinamento dentro de um chat ou um canal para compartilhamento de conhecimento offline e upskilling.</span><span class="sxs-lookup"><span data-stu-id="052f4-471">Training is a custom [Teams messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that enables users to publish a training within a chat or a channel for offline knowledge sharing and upskilling.</span></span> <span data-ttu-id="052f4-472">O aplicativo é suportado em vários clientes Teams plataforma, como desktop, navegador, iOS e Android.</span><span class="sxs-lookup"><span data-stu-id="052f4-472">The app is supported across multiple Teams platform clients, such as desktop, browser, iOS, and Android.</span></span> <span data-ttu-id="052f4-473">Este aplicativo está pronto para implantação como parte de sua assinatura de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="052f4-473">This app is ready for deployment as part of your Microsoft 365 subscription.</span></span>

[<span data-ttu-id="052f4-474">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-474">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-training)

:::row:::
  :::column span="1":::
    ![Criar treinamento na visão Teams](../assets/images/training-app-template-compose-view.gif)  
:::column-end:::
:::row-end:::

## <a name="virtual-rounding"></a><span data-ttu-id="052f4-476">Arredondamento Virtual</span><span class="sxs-lookup"><span data-stu-id="052f4-476">Virtual Rounding</span></span>

<span data-ttu-id="052f4-477">Os prestadores de serviços hospitalares e de emergência fazem muitas **rondas** por dia.</span><span class="sxs-lookup"><span data-stu-id="052f4-477">Hospital and emergency room providers make many **rounds** per day.</span></span> <span data-ttu-id="052f4-478">Esses check-ins rápidos nos pacientes destinam-se a fornecer uma verificação de status sobre como o paciente está indo e garantir que as preocupações do paciente sejam tratadas.</span><span class="sxs-lookup"><span data-stu-id="052f4-478">These quick check-ins on patients are intended to provide a status check on how the patient is doing and ensure that the patient’s concerns are addressed.</span></span> <span data-ttu-id="052f4-479">Embora o arredondamento seja uma prática essencial para garantir que os pacientes estejam sendo monitorados por vários tipos de provedores, eles representam um enorme dreno no EPI, pois para cada visita, de cada provedor, uma nova máscara e um novo conjunto de luvas são usados.</span><span class="sxs-lookup"><span data-stu-id="052f4-479">While rounding is an essential practice to ensure patients are being monitored by multiple types of providers, they represent a huge drain on PPE, because for each visit, from each provider, a new mask, and new set of gloves are used.</span></span> <span data-ttu-id="052f4-480">Com estes modelos de aplicativos, os profissionais médicos podem facilmente realizar rodadas virtualmente, através de uma Microsoft Teams reunião entre o provedor e o paciente.</span><span class="sxs-lookup"><span data-stu-id="052f4-480">With this app templates, medical workers can easily conduct rounds virtually, through a Microsoft Teams meeting between the provider and the patient.</span></span>

<span data-ttu-id="052f4-481">A solução virtual de arredondamento também é referenciada no post do [blog](https://aka.ms/teamsvirtualrounding)Microsoft Health and Life Sciences .</span><span class="sxs-lookup"><span data-stu-id="052f4-481">The Virtual Rounding solution is also referenced in the Microsoft Health and Life Sciences [blog post](https://aka.ms/teamsvirtualrounding).</span></span>

[<span data-ttu-id="052f4-482">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-482">Get it on GitHub</span></span>](https://github.com/SmartterHealth/Virtual-Rounding)

![Arredondamento Virtual](../assets/images/virtual-rounding-overview.png)

## <a name="visitor-management"></a><span data-ttu-id="052f4-484">Gestão de Visitantes</span><span class="sxs-lookup"><span data-stu-id="052f4-484">Visitor Management</span></span>

<span data-ttu-id="052f4-485">O aplicativo de Gerenciamento de Visitantes permite que sua organização e funcionários gerenciem de forma fácil e eficiente o processo de visitantes no local, diretamente a partir de Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="052f4-485">The Visitor Management app enables your organization and employees to easily and efficiently manage the on-site visitor process, directly from Microsoft Teams.</span></span> <span data-ttu-id="052f4-486">O aplicativo permite que os funcionários criem solicitações de visitantes, rastreiem centralmente um status de solicitação através do painel de visitantes e recebam notificações em tempo real quando um visitante chega.</span><span class="sxs-lookup"><span data-stu-id="052f4-486">The app enables employees to create visitor requests, centrally track a request status through the visitor dashboard, and receive real-time notifications when a visitor arrives.</span></span>

[<span data-ttu-id="052f4-487">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-487">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-app-visitormanagement)

:::row:::
  :::column span="2":::
    ![Crie uma exibição de solicitação](../assets/images/visitor-management-create-request.png)
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Notificação de chegada de visitantes](../assets/images/visitor-management-notify-host.png)
:::column-end:::
:::row-end:::

## <a name="workplace-awards"></a><span data-ttu-id="052f4-490">Prêmios do Local de Trabalho</span><span class="sxs-lookup"><span data-stu-id="052f4-490">Workplace Awards</span></span>

<span data-ttu-id="052f4-491">O Workplace Awards é um modelo de aplicativo Teams que fornece uma estrutura positiva para promover o reconhecimento e incentivar a cultura de valorização dos funcionários no ambiente de trabalho moderno.</span><span class="sxs-lookup"><span data-stu-id="052f4-491">Workplace Awards is a Teams app template that provides a positive framework to foster recognition and encourage the culture of employee appreciation in the modern workplace.</span></span> <span data-ttu-id="052f4-492">O aplicativo permite que você configure e gerencie recompensas e reconhecimento de funcionários, chamado programa R&R, onde os funcionários podem facilmente nomear e endossar colegas e seu líder R&R pode ver nomeações submetidas, conceder prêmios e anunciar os destinatários.</span><span class="sxs-lookup"><span data-stu-id="052f4-492">The app enables you to setup and manage an employee rewards and recognition, called R&R program where employees can easily nominate and endorse colleagues and your R&R leader can view submitted nominations, grant awards, and announce recipients.</span></span>

[<span data-ttu-id="052f4-493">Colocá-lo em GitHub</span><span class="sxs-lookup"><span data-stu-id="052f4-493">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-workplaceawards)

:::row:::
  :::column span="2":::
    ![<span data-ttu-id="052f4-494">Cartão de indicação de prêmios no local de trabalho</span><span class="sxs-lookup"><span data-stu-id="052f4-494">Workplace awards nomination card</span></span> ](../assets/images/workplace-awards-nominate.png)
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Guia de lista de prêmios no local de trabalho](../assets/images/workplace-awards-champion-tab.png)
:::column-end:::
:::row-end:::

<span data-ttu-id="052f4-496">Para obter mais informações sobre o modelo do aplicativo, consulte [o modelo do Aplicativo](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR2_7qFm_lcZAr4eqEhnLsZ9UMVZGT1lCT0FXUDdZMUM0RkpBS1BESTAwWC4u).</span><span class="sxs-lookup"><span data-stu-id="052f4-496">For more information on app template, see [App template](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR2_7qFm_lcZAr4eqEhnLsZ9UMVZGT1lCT0FXUDdZMUM0RkpBS1BESTAwWC4u).</span></span>

## <a name="see-also"></a><span data-ttu-id="052f4-497">Confira também</span><span class="sxs-lookup"><span data-stu-id="052f4-497">See also</span></span>

[<span data-ttu-id="052f4-498">Integrar aplicativos Web</span><span class="sxs-lookup"><span data-stu-id="052f4-498">Integrate web apps</span></span>](~/samples/integrate-web-apps-overview.md)
