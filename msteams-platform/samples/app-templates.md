---
title: Modelos de aplicativo do Microsoft Teams
description: Links e descrições de modelos de aplicativo para a plataforma do Microsoft Teams
ms.topic: reference
keywords: Demonstração de exemplos de modelos do Microsoft Teams
ms.author: lajanuar
author: laujan
ms.openlocfilehash: 098325d973ad1fa5306761cd60c6504d808cea9d
ms.sourcegitcommit: 0628a85293f7e26de3490e4dd23a54e586cdfeca
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2021
ms.locfileid: "51493052"
---
# <a name="app-templates-for-microsoft-teams"></a><span data-ttu-id="9a6a3-104">Modelos de aplicativos para o Teams</span><span class="sxs-lookup"><span data-stu-id="9a6a3-104">App templates for Microsoft Teams</span></span>

<span data-ttu-id="9a6a3-105">Modelos de aplicativo são exemplos de aplicativos completos para o Microsoft Teams que são de código aberto e disponíveis no GitHub.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-105">App templates are examples of complete apps for Microsoft Teams that are open-source and available on GitHub.</span></span> <span data-ttu-id="9a6a3-106">Cada modelo de aplicativo contém instruções detalhadas para implantar e instalar esse aplicativo para sua organização.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-106">Each app template contains detailed instructions for deploying and installing that app for your organization.</span></span> <span data-ttu-id="9a6a3-107">Ele também fornece um aplicativo de exemplo que você pode instalar e começar a usar imediatamente.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-107">It also provides a sample app that you can install and begin using immediately.</span></span> <span data-ttu-id="9a6a3-108">O código-fonte completo também está disponível, o que permite explorá-lo em detalhes ou bifurcar o código e alterá-lo para atender aos seus requisitos específicos.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-108">The complete source code is available too, which allows you to explore it in detail or fork the code and alter it to meet your specific requirements.</span></span>
<span data-ttu-id="9a6a3-109">Todos os modelos de aplicativo são fornecidos nos termos de [Licença do MIT.](https://github.com/OfficeDev/microsoft-teams-apps-eprescription/blob/master/LICENSE)</span><span class="sxs-lookup"><span data-stu-id="9a6a3-109">All app templates are provided under the [MIT License](https://github.com/OfficeDev/microsoft-teams-apps-eprescription/blob/master/LICENSE) terms.</span></span>
>[!NOTE] 
><span data-ttu-id="9a6a3-110">Você, não a Microsoft, deve licenciar e dar suporte a aplicativos criados a partir de modelos de aplicativos para seus usuários e organizações.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-110">You, not Microsoft must license and support apps created from app templates for your users and organizations.</span></span>

<span data-ttu-id="9a6a3-111">**&#9734; Indica modelos de aplicativo recém-lançados.**</span><span class="sxs-lookup"><span data-stu-id="9a6a3-111">**&#9734; Indicates newly released app templates.**</span></span>

### <a name="key-benefits"></a><span data-ttu-id="9a6a3-112">Principais benefícios</span><span class="sxs-lookup"><span data-stu-id="9a6a3-112">Key benefits</span></span>

* <span data-ttu-id="9a6a3-113">**Implantar diretamente na nuvem:** Todos os modelos de aplicativo incluem scripts de implantação que permitem hospedar todos os serviços necessários no Microsoft Azure ou na Plataforma Power.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-113">**Deploy directly to the cloud:** All app templates include deployment scripts that allows you to host all required services in Microsoft Azure or the Power Platform.</span></span> 
* <span data-ttu-id="9a6a3-114">**Código de exemplo recomendado:** Os modelos de aplicativo estão em conformidade com as práticas recomendadas em torno da segurança e da infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-114">**Recommended sample code:** The app templates conform to recommended best practices around security and infrastructure.</span></span> <span data-ttu-id="9a6a3-115">Todas as alterações enviadas pela comunidade aos modelos de aplicativos são revisadas para garantir a conformidade.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-115">All community submitted changes to the app templates are reviewed to ensure conformance.</span></span>
* <span data-ttu-id="9a6a3-116">**Personalizável e extensível:** Embora todos os modelos de aplicativo possam ser implantados com configuração mínima, fornecemos toda a base de código e scripts de implantação para que você possa personalizá-los ou estendí-los facilmente para se ajustar às suas necessidades exclusivas.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-116">**Customizable and extensible:** While all app templates can be deployed with minimal configuration, we provide the entire code base and deployment scripts so that you can easily customize or extend them to fit your unique needs.</span></span>
* <span data-ttu-id="9a6a3-117">**Documentação detalhada:** Todos os modelos de aplicativo são acompanhados por documentação de ponta a ponta em etapas de arquitetura de solução, implantação e configuração.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-117">**Detailed documentation:** All app templates are accompanied by end-to-end documentation on solution architecture, deployment, and configuration steps.</span></span>  

## <a name="adoption-bot-9734"></a><span data-ttu-id="9a6a3-118">Adoção bot &#9734;</span><span class="sxs-lookup"><span data-stu-id="9a6a3-118">Adoption Bot &#9734;</span></span>

<span data-ttu-id="9a6a3-119">O Bot de Adoção é um bot de chat de cuidado do usuário criado com o Power Virtual Agent for Teams (PVA).</span><span class="sxs-lookup"><span data-stu-id="9a6a3-119">Adoption Bot is a user care chat bot built with Power Virtual Agent for Teams (PVA).</span></span> <span data-ttu-id="9a6a3-120">Ele pode ser considerado como a versão PVA do FAQPlus.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-120">It can be considered as the PVA version of FAQPlus.</span></span> <span data-ttu-id="9a6a3-121">O Bot de Adoção responde a mais de 100 perguntas comuns sobre o Microsoft 365 e o Teams.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-121">Adoption Bot answers 100+ common questions about Microsoft 365 and Teams.</span></span> <span data-ttu-id="9a6a3-122">Você pode editar os tópicos existentes, adicionar seus próprios tópicos e ingerir perguntas frequentes existentes.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-122">You can edit the existing topics, add your own topics, and ingest existing FAQs.</span></span> <span data-ttu-id="9a6a3-123">Se os usuários precisarem de ajuda adicional, o Bot de Adoção poderá conectá-los a especialistas ou até mesmo ser estendido para abrir tíquetes de serviço com conectores de fluxo premium. Esse bot pode ser instalado por conta própria ou integrado a um aplicativo personalizado, como o [Hub de Adoção.](https://github.com/akporzondek/adoption_hub)</span><span class="sxs-lookup"><span data-stu-id="9a6a3-123">If users need additional help, Adoption Bot can connect them to experts or even be extended to open service tickets with premium flow connectors.This bot can be installed on it's own or built into a custom app like the [Adoption Hub](https://github.com/akporzondek/adoption_hub).</span></span>

[<span data-ttu-id="9a6a3-124">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-124">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-adopt-bot)

## <a name="appointment-manager-9734"></a><span data-ttu-id="9a6a3-125">Gerenciador de Compromissos &#9734;</span><span class="sxs-lookup"><span data-stu-id="9a6a3-125">Appointment Manager &#9734;</span></span>

<span data-ttu-id="9a6a3-126">O Gerenciador de Compromissos é um modelo de aplicativo do Teams para ajudar as empresas a criar, gerenciar e conduzir compromissos virtuais com os consumidores por meio do Teams.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-126">Appointment Manager is a Teams app template to help businesses create, manage, and conduct virtual appointments with consumers through Teams.</span></span> <span data-ttu-id="9a6a3-127">As novas solicitações de compromisso dos consumidores ficam visíveis nos canais do Teams, onde eles podem ser atribuídos e reatribuídos rapidamente à equipe em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-127">New appointment requests from consumers are visible in Teams channels, where they can quickly be assigned and reassigned to staff in a team.</span></span> <span data-ttu-id="9a6a3-128">As solicitações de compromisso podem ser exibidas em níveis de equipe ou pessoal por meio de guias personalizadas.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-128">Appointment requests can be viewed at team or personal levels through custom tabs.</span></span> <span data-ttu-id="9a6a3-129">Cada compromisso é associado a uma reunião online do Teams, portanto, a equipe e os consumidores podem participar facilmente da reunião no horário agendado.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-129">Every appointment is associated with a Teams online meeting, hence the staff and consumers can easily join the meeting at the scheduled time.</span></span>

<span data-ttu-id="9a6a3-130">O modelo de aplicativo se integra ao Microsoft Bookings para facilitar o gerenciamento de compromissos.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-130">The app template integrates with Microsoft Bookings for easy appointment management.</span></span> <span data-ttu-id="9a6a3-131">Os compromissos agendados aparecem automaticamente nos calendários dos membros da equipe atribuídos, e os consumidores recebem notificações de email e lembretes personalizáveis com links de reunião incorporados.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-131">Scheduled appointments automatically appear on assigned staff members' calendars, and consumers receive customizable email notifications and reminders with embedded meeting links.</span></span>

[<span data-ttu-id="9a6a3-132">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-132">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-appointment-manager)

<span data-ttu-id="9a6a3-133">![Gerenciador de Compromissos Visão Geral ](../assets/images/appointment-manager-overview.png)
 ![ do Gerenciador de Compromissos no Teams](../assets/images/appointment-manager-2.png)</span><span class="sxs-lookup"><span data-stu-id="9a6a3-133">![Appointment Manager Overview](../assets/images/appointment-manager-overview.png)
![Appointment Manager in Teams](../assets/images/appointment-manager-2.png)</span></span>

## <a name="ask-away"></a><span data-ttu-id="9a6a3-134">Ask Away</span><span class="sxs-lookup"><span data-stu-id="9a6a3-134">Ask Away</span></span>

<span data-ttu-id="9a6a3-135">Ask Away é um [bot do Microsoft Teams](../bots/what-are-bots.md) que permite que os usuários conduzam sessões de Q&A (Pergunta e Resposta) no Teams.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-135">Ask Away is a [Microsoft Teams bot](../bots/what-are-bots.md) that enables users to conduct Q&A (Question and Answer) sessions within Teams.</span></span> <span data-ttu-id="9a6a3-136">Usando o bot Ask Away, os membros da equipe podem enviar e fazer perguntas de votação compartilhadas por colegas, permitindo que os hosts de Q&A reúnam facilmente perguntas importantes em um canal ou chat.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-136">Using the Ask Away bot, team members can submit and up-vote questions shared by colleagues allowing Q&A hosts to easily gather top-of-mind questions within a channel or chat.</span></span> <span data-ttu-id="9a6a3-137">O bot pode ser usado para conduzir um Q em tempo real&uma sessão em uma reunião do Teams e permite que os participantes enviem perguntas ao vivo via chat.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-137">The bot can be used to conduct a real-time Q&A session in a Teams meeting and allows attendees to submit questions live via chat.</span></span>

[<span data-ttu-id="9a6a3-138">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-138">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-askaway)

:::row:::
  :::column span="2":::
    ![Exibição da caixa de diálogo pop-up de quadro de líderes para que os usuários votem em perguntas](../assets/images/ask-away-app.png)  
:::column-end:::
:::row-end:::

## <a name="associate-insights"></a><span data-ttu-id="9a6a3-140">Informações associadas</span><span class="sxs-lookup"><span data-stu-id="9a6a3-140">Associate Insights</span></span>

<span data-ttu-id="9a6a3-141">Associate Insights é um [modelo do Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) que permite que os funcionários de primeira linha capturem e enviem diretamente a opinião, o sentimento e a percepção do cliente.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-141">Associate Insights is a [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) template that empowers firstline workers to directly capture and submit customer opinion, sentiment, and perception.</span></span> <span data-ttu-id="9a6a3-142">Os funcionários de primeira linha geralmente são o primeiro representante da empresa a se envolver com os clientes em um ponto de contato de um para um.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-142">Firstline workers are often the first company representative to engage with customers in a one-to-one point-of contact.</span></span> <span data-ttu-id="9a6a3-143">Os dados coletados podem ser compartilhados e usados de forma colaborativa por equipes de negócios, por exemplo, por meio de uma guia do Power BI Teams, para melhorar o produto e melhorar a experiência do cliente.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-143">The collected data can be shared and used collaboratively by business teams, e.g., via a Power BI Teams tab, for product improvement and enhancing the customer experience.</span></span>

[<span data-ttu-id="9a6a3-144">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-144">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-associateinsights)

:::row:::
  :::column span="2":::
    ![Exibição de feedback de insights gerados pelo aplicativo](../assets/images/associate-insights-app.png)  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Exibição do Power BI de insights gerados pelo aplicativo](../assets/images/associate-insights-app2.png)
:::column-end:::
:::row-end:::

## <a name="attendance"></a><span data-ttu-id="9a6a3-147">Participação</span><span class="sxs-lookup"><span data-stu-id="9a6a3-147">Attendance</span></span>

<span data-ttu-id="9a6a3-148">O aplicativo De presença é uma [guia do Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) que pode ser fixada em uma equipe.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-148">The Attendance app is a [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) tab that can be pinned in a team.</span></span> <span data-ttu-id="9a6a3-149">Ele foi projetado para registrar a presença, normalmente em configurações como ambientes de aprendizado e treinamento.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-149">It is designed to record presence, typically in settings such as learning and training environments.</span></span> <span data-ttu-id="9a6a3-150">Os usuários podem marcar ou editar a participação por até 30 dias no passado e exibir relatórios de participação resumidos para um grupo inteiro ou participantes individuais.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-150">Users can mark or edit attendance for up to 30 days in the past and view summarized attendance reports for an entire group or individual attendees.</span></span>

[<span data-ttu-id="9a6a3-151">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-151">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-attendance)

![Demonstração do aplicativo de participação](../assets/images/attendance-app.png)

## <a name="book-a-room"></a><span data-ttu-id="9a6a3-153">Book-a-room</span><span class="sxs-lookup"><span data-stu-id="9a6a3-153">Book-a-room</span></span>

<span data-ttu-id="9a6a3-154">Book-a-room é um bot do [Microsoft Teams](../bots/what-are-bots.md) que permite aos usuários encontrar e reservar rapidamente uma sala de reunião para 30 (padrão), 60 ou 90 minutos a partir da hora atual.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-154">Book-a-room is a [Microsoft Teams bot](../bots/what-are-bots.md) that lets users quickly find and reserve a meeting room for 30 (default), 60, or 90 minutes starting from the current  time.</span></span> <span data-ttu-id="9a6a3-155">Os escopos de bot book-a-room para conversas pessoais ou 1:1.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-155">The Book-a-room bot scopes to personal or 1:1 conversations.</span></span>

[<span data-ttu-id="9a6a3-156">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-156">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-bookaroom)

![Demonstração de book-a-room](../assets/images/book-a-room.png)

## <a name="building-access"></a><span data-ttu-id="9a6a3-158">Criando o Access</span><span class="sxs-lookup"><span data-stu-id="9a6a3-158">Building Access</span></span>

<span data-ttu-id="9a6a3-159">O Building Access é um aplicativo baseado na Plataforma Do Microsoft [Power](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/)que oferece suporte à administração da criação de limites de ocupação e de normas de distanciamento social, permitindo que os diretores de instalações gerenciem, acompanhem e reportem a presença do funcionário no local.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-159">Building Access is a Microsoft [Power Platform](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/)-based app that supports the administration of building occupancy thresholds and social distancing norms by enabling facilities directors to manage, track, and report employee on-site presence.</span></span> <span data-ttu-id="9a6a3-160">O aplicativo, criado usando o Microsoft [Power Apps](/powerapps/powerapps-overview)e o [Power Automate,](/power-automate/getting-started)integra-se profundamente com o Microsoft Teams e permite que as organizações determinem a preparação para a criação, estabeleçam critérios de qualificação para acesso local e reúnam ideias para o planejamento futuro.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-160">The app, built using Microsoft [Power Apps](/powerapps/powerapps-overview), and [Power Automate](/power-automate/getting-started), deeply integrates with Microsoft Teams and enables organizations to determine building readiness, establish eligibility criteria for on-site access, and gather insights for future planning.</span></span>

[<span data-ttu-id="9a6a3-161">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-161">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-buildingaccess)

:::row:::
   :::column span="":::
     ![Criar cartão de reserva do Access](../assets/images/building-access-reservation.png)
   :::column-end:::
   :::column span="":::
      ![Exibição de teclas do Building Access](../assets/images/building-access-access-key.png)
   :::column-end:::
:::row-end:::

## <a name="celebrations"></a><span data-ttu-id="9a6a3-164">Celebrações</span><span class="sxs-lookup"><span data-stu-id="9a6a3-164">Celebrations</span></span>

<span data-ttu-id="9a6a3-165">Celebrações é um aplicativo do Teams que ajuda os membros da equipe a comemorar aniversários, aniversários e outros eventos recorrentes.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-165">Celebrations is a Teams app that helps team members celebrate each others' birthdays, anniversaries, and other recurring events.</span></span> <span data-ttu-id="9a6a3-166">Ele lembra ocasiões especiais de todos os membros da equipe e envia uma mensagem amigável em todas as equipes selecionadas no momento da criação do evento, para fazer com que os membros da equipe se sintam especiais em seus dias.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-166">It remembers special occasions of all the team members and sends a friendly message in all the teams selected at the time of event creation, to make the team members feel special on their day.</span></span>

<span data-ttu-id="9a6a3-167">O aplicativo fornece uma interface fácil para todos os membros da equipe adicionarem e exibirem seus eventos pessoalmente e também permitem que o usuário selecione as equipes nas quais os eventos são compartilhados.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-167">The app provides an easy interface for all the team members to personally add and view their events and also allows the user to select the teams in which the events gets shared.</span></span>

[<span data-ttu-id="9a6a3-168">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-168">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-celebrations-app)

## <a name="checklist"></a><span data-ttu-id="9a6a3-169">Lista de verificação</span><span class="sxs-lookup"><span data-stu-id="9a6a3-169">Checklist</span></span>

<span data-ttu-id="9a6a3-170">Lista de verificação é um aplicativo de extensão de mensagens personalizado do Microsoft [Teams](../messaging-extensions/what-are-messaging-extensions.md) que permite que você colabore com sua equipe criando uma lista de verificação compartilhada em um chat ou canal.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-170">Checklist is a custom Microsoft Teams [messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that enables you to collaborate with your team by creating a shared checklist in a chat or channel.</span></span> <span data-ttu-id="9a6a3-171">O aplicativo tem suporte em todos os clientes de plataforma do Teams — desktop, navegador, iOS e Android — e está pronto para implantação como parte da sua assinatura do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-171">The app is supported across all Teams platform clients —  desktop, browser, iOS, and Android — and is ready for deployment as part of your Microsoft 365 subscription.</span></span>  

[<span data-ttu-id="9a6a3-172">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-172">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-checklist-app )

:::row:::
:::column span="2":::
    ![Criar lista de verificação no exibição do Teams](../assets/images/checklist-app-template-compose-view.gif)  
:::column-end:::
:::row-end:::

## <a name="classroom-drop-in-9734"></a><span data-ttu-id="9a6a3-174">Lista de ida e &#9734;</span><span class="sxs-lookup"><span data-stu-id="9a6a3-174">Classroom Drop-in &#9734;</span></span>

<span data-ttu-id="9a6a3-175">O Drop-in de sala de aula é um aplicativo baseado na Plataforma [Microsoft Power](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/)que permite que os líderes do sistema encontrem equipes de classe (salas de aula virtuais) e adicionem a si mesmos ou outras pessoas a essas equipes de classe por um período de entrega especificado, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-175">Classroom Drop-in is a Microsoft [Power Platform](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/)-based app that enables system leaders to find class teams (virtual classrooms) and add themselves or others to these class teams for a specified drop-in period, as needed.</span></span> <span data-ttu-id="9a6a3-176">O aplicativo criado usando o Microsoft [Power Apps](/powerapps/powerapps-overview) e o [Power Automate](/power-automate/getting-started), integra-se profundamente ao Microsoft Teams para garantir que os institutos educacionais possam otimizar suas operações em um ambiente de aprendizado híbrido, fornecendo acesso a participantes relevantes para equipes de classe por requisitos comerciais.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-176">The app built using Microsoft [Power Apps](/powerapps/powerapps-overview) and [Power Automate](/power-automate/getting-started), deeply integrates with Microsoft Teams to ensure educational institutes can optimize their operations in a hybrid learning environment by providing access to relevant stakeholders for class teams per business requirements.</span></span>

[<span data-ttu-id="9a6a3-177">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-177">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-classroom-dropin)

![Solicitação de drop-in de sala de aula](../assets/images/classroom-drop-in-request.png)

## <a name="company-communicator"></a><span data-ttu-id="9a6a3-179">Communicator da empresa</span><span class="sxs-lookup"><span data-stu-id="9a6a3-179">Company Communicator</span></span>

<span data-ttu-id="9a6a3-180">O aplicativo Communicator company permite que as equipes corporativas criem e enviem mensagens destinadas a várias equipes ou a um grande número de funcionários por chat, permitindo que a organização chegue aos funcionários exatamente onde colaboram.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-180">The Company Communicator app enables corporate teams to create and send messages intended for multiple teams or large number of employees over chat allowing organization to reach employees right where they collaborate.</span></span> <span data-ttu-id="9a6a3-181">Utilize esse modelo para vários cenários, como novos comunicados de iniciativa, integração de funcionários, aprendizado e desenvolvimento modernos ou transmissões em toda a organização.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-181">Utilize this template for multiple scenarios such as new initiative announcements, employee onboarding, modern learning and development or organization-wide broadcasts.</span></span>

<span data-ttu-id="9a6a3-182">O aplicativo fornece uma interface fácil para usuários designados criar, visualizar, colaborar e enviar mensagens.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-182">The app provides an easy interface for designated users to create, preview, collaborate and send messages.</span></span>

<span data-ttu-id="9a6a3-183">Ele fornece uma base para criar recursos personalizados de comunicação direcionada, como telemetria personalizada, em quantos usuários reconheceram ou interagiram com uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-183">It provides a foundation to build custom targeted communication capabilities such as custom telemetry on how many users acknowledged or interacted with a message.</span></span>

[<span data-ttu-id="9a6a3-184">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-184">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-company-communicator-app)

![jCompany Communicator de caixa de redação](../assets/images/CompanyCommunicatorCompose.png)

## <a name="contact-group-lookup"></a><span data-ttu-id="9a6a3-186">Procurar grupo de contatos</span><span class="sxs-lookup"><span data-stu-id="9a6a3-186">Contact Group Lookup</span></span>

<span data-ttu-id="9a6a3-187">O aplicativo de Pesquisa de Grupo de Contatos fornece uma abordagem conveniente e útil para criar, acessar e gerenciar grupos de contatos da sua organização (anteriormente conhecidos como listas de distribuição ou grupos de comunicação).</span><span class="sxs-lookup"><span data-stu-id="9a6a3-187">The Contact Group Lookup app provides a convenient and useful approach to creating, accessing, and managing your organization's contact groups (formerly known as distribution lists or communication groups).</span></span> <span data-ttu-id="9a6a3-188">Os usuários podem exibir e conversar rapidamente com membros do grupo, exibir o status do membro e criar um chat de grupo com membros selecionados no grupo de contatos, tudo dentro do ambiente do Teams.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-188">Users can quickly view and chat with group members, view member status, and create a group chat with selected members in the contact group, all within the Teams environment.</span></span>

[<span data-ttu-id="9a6a3-189">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-189">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-app-contactgrouplookup)

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

## <a name="co-worker-appreciation-9734"></a><span data-ttu-id="9a6a3-192">Co-worker Appreciation &#9734;</span><span class="sxs-lookup"><span data-stu-id="9a6a3-192">Co-worker Appreciation &#9734;</span></span>

<span data-ttu-id="9a6a3-193">Usando o modelo de reconhecimento de colegas de trabalho no Microsoft Teams, os usuários podem reconhecer as conquistas de seus colegas no contexto do Teams.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-193">Using the co-worker appreciation template in Microsoft Teams, users can recognize their colleagues' achievements within the Teams’ context.</span></span> <span data-ttu-id="9a6a3-194">Quando os colegas de trabalho selecionam recompensar um colega, os destinatários e outros membros da equipe são marcados em uma conversa de canal e recebem uma notificação sobre os detalhes do prêmio do canal.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-194">When co-workers select to reward a colleague, recipients and other team members are tagged in a channel conversation and they receive a notification about the channel's award details.</span></span> <span data-ttu-id="9a6a3-195">Os prêmios são registrados no aplicativo teams, que é seguro, portátil e facilmente compartilhável.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-195">The awards are recorded in the Teams app, which is secure, portable, and easily shareable.</span></span> <span data-ttu-id="9a6a3-196">Isso pode ser considerado como a versão baseada no PowerApps do modelo de aplicativo Open Badges, com uma tabela de classificação.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-196">This can be considered as the PowerApps based version of the Open Badges app template, with a leaderboard.</span></span>

[<span data-ttu-id="9a6a3-197">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-197">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-coworker-appreciation)

![Geral](../assets/images/coworker-appreciation-1.png)

## <a name="crowdsourcer"></a><span data-ttu-id="9a6a3-199">CrowdSourcer</span><span class="sxs-lookup"><span data-stu-id="9a6a3-199">CrowdSourcer</span></span>

<span data-ttu-id="9a6a3-200">CrowdSourcer é um [bot do Microsoft Teams](../bots/what-are-bots.md) que fornece informações consultadas às equipes de forma colaborativa de membros do grupo.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-200">CrowdSourcer is a [Microsoft Teams bot](../bots/what-are-bots.md) that gives teams queried information sourced collaboratively from group members.</span></span> <span data-ttu-id="9a6a3-201">É uma ótima maneira de responder a perguntas frequentes enquanto permite que os participantes se envolvam ativamente e contribuam para um recurso de informações divertido e útil.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-201">It's a great way to answer frequently asked questions while enabling participants to actively engage in and contribute to a fun and helpful information resource.</span></span>

[<span data-ttu-id="9a6a3-202">Obter no Github</span><span class="sxs-lookup"><span data-stu-id="9a6a3-202">Get it on Github</span></span>](https://github.com/OfficeDev/microsoft-teams-crowdsourcer-app)

![Interação do usuário final do Crowdsource](../assets/images/crowdsourcer.png)

## <a name="custom-stickers"></a><span data-ttu-id="9a6a3-204">Adesivos personalizados</span><span class="sxs-lookup"><span data-stu-id="9a6a3-204">Custom Stickers</span></span>

<span data-ttu-id="9a6a3-205">A auto expressão é fundamental para uma cultura de equipe saudável.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-205">Self-expression is core to a healthy team culture.</span></span> <span data-ttu-id="9a6a3-206">Este modelo de aplicativo é uma [extensão de mensagens](~/messaging-extensions/what-are-messaging-extensions.md) que permite que seus usuários usem adesivos personalizados e GIFs no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-206">This app template is a [messaging extension](~/messaging-extensions/what-are-messaging-extensions.md) that enables your users to use custom stickers and GIFs within Microsoft Teams.</span></span> <span data-ttu-id="9a6a3-207">Este modelo oferece uma experiência de configuração baseada na Web fácil, onde qualquer pessoa com acesso à configuração pode carregar os GIFs/adesivos/imagens que deseja que seus usuários finais tenham, permitindo que toda a sua equipe use qualquer conjunto de adesivos que você escolher.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-207">This template provides an easy web-based configuration experience where anyone with configuration access can upload the GIFs/stickers/images they want their end-users to have, allowing your entire team to use any set of stickers you chose.</span></span>

<span data-ttu-id="9a6a3-208">Este aplicativo também permite o compartilhamento fácil de imagens/GIFs/adesivos entre equipes sem precisar de acesso a sites do SharePoint ou canais individuais como mecanismos de armazenamento e compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-208">This app also enables easy sharing of images/GIFs/stickers across teams without needing access to SharePoint sites or individual channels as storage and sharing mechanisms.</span></span> <span data-ttu-id="9a6a3-209">Por exemplo, as equipes de produtos podem compartilhar facilmente imagens de produto e GIFs para redes sociais, marketing e equipes de vendas programaticamente.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-209">For example, product teams can easily share product images and GIFs to social media, marketing and sales teams programmatically.</span></span> <span data-ttu-id="9a6a3-210">Também é possível estender esse aplicativo disparando um fluxo de notificação para equipes/indivíduos específicos quando novas imagens/GIFs são disponibilizadas.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-210">One can also extend this app by triggering a notification flow to specific teams/individuals when new images/GIFs are made available.</span></span>

[<span data-ttu-id="9a6a3-211">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-211">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-stickers-app)

![Aplicativo Stickers](../assets/images/stickers.png)

## <a name="employee-ideas"></a><span data-ttu-id="9a6a3-213">Ideias de funcionários</span><span class="sxs-lookup"><span data-stu-id="9a6a3-213">Employee Ideas</span></span>

<span data-ttu-id="9a6a3-214">O aplicativo Ideias de Funcionários é a versão do PowerApps do modelo de aplicativo Great Ideas baseado no Azure.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-214">The Employee Ideas app is the PowerApps version of the Azure based Great Ideas app template.</span></span> <span data-ttu-id="9a6a3-215">O aplicativo permite que os usuários do Teams configurem e configurem uma campanha de ideias.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-215">The app enables the Teams users to set up and configure an idea campaign.</span></span> <span data-ttu-id="9a6a3-216">Uma campanha de ideias é uma categoria para agrupar ideias em torno de temas comuns.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-216">An idea campaign is a category for grouping ideas around common themes.</span></span>

<span data-ttu-id="9a6a3-217">Os usuários do Teams também podem executar as seguintes atividades:</span><span class="sxs-lookup"><span data-stu-id="9a6a3-217">Teams users can also perform following activities:</span></span>
* <span data-ttu-id="9a6a3-218">Configure um formulário de envio padrão que os funcionários precisam enviar para cada ideia.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-218">Configure a standard submission form that employees need to submit for each idea.</span></span> 
* <span data-ttu-id="9a6a3-219">Revise e gerencie as ideias e a lista de campanhas.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-219">Review and manage the ideas and list of campaigns.</span></span>
* <span data-ttu-id="9a6a3-220">Modificar e excluir campanhas.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-220">Modify and delete campaigns.</span></span>
* <span data-ttu-id="9a6a3-221">Revise os conselhos de líderes de ideias.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-221">Review leader boards of ideas.</span></span>
* <span data-ttu-id="9a6a3-222">Vote e compartilhe ideias priorizadas.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-222">Vote for and share prioritized ideas.</span></span>
* <span data-ttu-id="9a6a3-223">Enviar ideias para uma campanha.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-223">Submit ideas for a campaign.</span></span>
* <span data-ttu-id="9a6a3-224">Exibir a ideia de outro membro da equipe.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-224">View other team member's idea.</span></span>
* <span data-ttu-id="9a6a3-225">Vote nas ideias mais curtidas.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-225">Vote on most liked ideas.</span></span>
* <span data-ttu-id="9a6a3-226">Revise o desempenho de suas ideias em comparação com outras em uma campanha.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-226">Review the performance of their ideas compared with others within a campaign.</span></span>

[<span data-ttu-id="9a6a3-227">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-227">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-employeeideas)

![Gerenciar exibição de campanha](../assets/images/employee-ideas-manage-campaigns.png) 

## <a name="e-prescriptions"></a><span data-ttu-id="9a6a3-229">E-Prescriptions</span><span class="sxs-lookup"><span data-stu-id="9a6a3-229">E-Prescriptions</span></span> 

<span data-ttu-id="9a6a3-230">E-Prescriptions é um aplicativo baseado em [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app)que aprimora a telemedicina e o cuidado virtual automatizando o processo de emissão de prescrições e para os pacientes.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-230">E-Prescriptions is a [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app)-based app that enhances telemedicine and virtual care by automating the process of issuing e-prescriptions to patients.</span></span> <span data-ttu-id="9a6a3-231">Os profissionais médicos podem revisar rapidamente os compromissos, gerar prescrições e enviar emails com anexos de prescrição e para os pacientes diretamente dentro da plataforma do Teams.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-231">Medical professionals can quickly review appointments, generate e-prescriptions, and send emails with e-prescription attachments to patients directly within the Teams platform.</span></span>

[<span data-ttu-id="9a6a3-232">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-232">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-eprescription) 

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

## <a name="employee-training"></a><span data-ttu-id="9a6a3-237">Treinamento de funcionários</span><span class="sxs-lookup"><span data-stu-id="9a6a3-237">Employee Training</span></span> 

<span data-ttu-id="9a6a3-238">Treinamento de funcionários é um aplicativo do Microsoft Teams que permite que os organizadores publiquem, acompanhem e promovam facilmente eventos de aprendizado e treinamento para sua organização.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-238">Employee training is a Microsoft Teams app that enables organizers to easily publish,  track, and promote learning and training events for your organization.</span></span>  <span data-ttu-id="9a6a3-239">Com o aplicativo, os planejadores de eventos podem enviar lembretes e notificações para os registrantes de eventos e os funcionários podem indicar interesse nos eventos futuros, manter-se atualizados sobre eventos atuais e compartilhar detalhes do evento com colegas por meio da extensão de mensagens do Teams.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-239">With the app, event planners can send reminders and notifications to event registrants and employees can indicate interest in upcoming events, stay updated on current events, and share event details with colleagues via the Teams messaging extension.</span></span>

[<span data-ttu-id="9a6a3-240">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-240">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-employeetraining)

:::row:::
:::column span="2":::
    <span data-ttu-id="9a6a3-241">**Exibir eventos de treinamento de funcionários** ![ Imagem da guia treinamento de funcionários](../assets/images/employee-training-discover-tab.png)</span><span class="sxs-lookup"><span data-stu-id="9a6a3-241">**View employee training events** ![Employee training tab image](../assets/images/employee-training-discover-tab.png)</span></span>  
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    <span data-ttu-id="9a6a3-242">**Criar evento de treinamento de funcionários** ![ Treinamento de funcionários criar formulário de evento](../assets/images/employee-training-create-event.jpg)</span><span class="sxs-lookup"><span data-stu-id="9a6a3-242">**Create employee training event** ![Employee training create event form](../assets/images/employee-training-create-event.jpg)</span></span>
:::column-end:::
:::row-end:::

## <a name="expert-finder"></a><span data-ttu-id="9a6a3-243">Expert Finder</span><span class="sxs-lookup"><span data-stu-id="9a6a3-243">Expert Finder</span></span>

<span data-ttu-id="9a6a3-244">O Expert Finder é um [bot do Microsoft Teams](../bots/what-are-bots.md) que identifica membros específicos da organização com base em suas habilidades, interesses e atributos de educação.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-244">Expert Finder is a [Microsoft Teams bot](../bots/what-are-bots.md) that identifies specific organization members based on their skills, interests, and education attributes.</span></span> <span data-ttu-id="9a6a3-245">Os membros encontram especialistas em uma organização que combinam com uma pesquisa de palavra-chave de perfis de usuário do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-245">Members find experts within an organization  that match a keyword search of Azure Active Directory user profiles.</span></span>

[<span data-ttu-id="9a6a3-246">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-246">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-expertfinder)

![Demonstração de resultados da pesquisa do Expert Finder](../assets/images/expert-finder.png)

## <a name="faq-plus"></a><span data-ttu-id="9a6a3-248">Perguntas Frequentes Plus</span><span class="sxs-lookup"><span data-stu-id="9a6a3-248">FAQ Plus</span></span>

<span data-ttu-id="9a6a3-249">Conversational Q&Um bots é uma maneira fácil de fornecer respostas para perguntas frequentes pelos usuários.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-249">Conversational Q&A bots are an easy way to provide answers to frequently asked questions by users.</span></span> <span data-ttu-id="9a6a3-250">No entanto, a maioria dos bots não consegue se envolver com os usuários de maneira significativa porque não há humanos no loop quando o bot falha.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-250">However, most bots fail to engage with users in meaningful way because there is no human in the loop when the bot fails.</span></span> <span data-ttu-id="9a6a3-251">O bot de perguntas frequentes é&um bot que traz um humano no loop quando não consegue ajudar.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-251">FAQ bot is a friendly Q&A bot that brings a human in the loop when it is unable to help.</span></span> <span data-ttu-id="9a6a3-252">É possível fazer uma pergunta ao bot e o bot responde com uma resposta se ele estiver contido na base de dados de conhecimento.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-252">One can ask the bot a question and the bot responds with an answer if it is contained in the knowledge base.</span></span> <span data-ttu-id="9a6a3-253">Caso não seja, o bot permite que o usuário envie uma consulta que, em seguida, é postada para uma equipe pré-configurada de especialistas que ajudam a fornecer suporte atuando sobre as notificações de dentro da própria equipe.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-253">If not, the bot allows the user to submit a query which then gets posted to a pre-configured team of experts who help to provide support by acting upon the notifications from within the team itself.</span></span>

> [!NOTE]
> <span data-ttu-id="9a6a3-254">A versão mais recente do **FaQ Plus** oferece suporte a resoluções de Q&A aprimoradas, permitindo que uma equipe de especialistas conclua o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9a6a3-254">The latest release of **FAQ Plus** supports improved Q&A resolutions by enabling a team of experts to complete the following:</span></span>
>
> <span data-ttu-id="9a6a3-255">&#x2714; Adicionar novo Q&Diretamente à base de dados de conhecimento usando extensões de mensagem.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-255">&#x2714; Add new Q&As directly to the knowledge base using message extensions.</span></span>
>
> <span data-ttu-id="9a6a3-256">&#x2714; Editar e excluir P&Pares A adicionados por um bot.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-256">&#x2714; Edit and delete Q&A pairs added by a bot.</span></span>
>
> <span data-ttu-id="9a6a3-257">&#x2714; o histórico de revisão de Q&As.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-257">&#x2714; Track the revision history of Q&As.</span></span>
>
> <span data-ttu-id="9a6a3-258">&#x2714; Configurar uma resposta com detalhes adicionais para exibição como um [cartão adaptável.](../task-modules-and-cards/cards/cards-reference.md#adaptive-card)</span><span class="sxs-lookup"><span data-stu-id="9a6a3-258">&#x2714; Configure an answer with additional details to display as an [adaptive card](../task-modules-and-cards/cards/cards-reference.md#adaptive-card).</span></span>
>
[<span data-ttu-id="9a6a3-259">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-259">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-faqplusv2)

![FAQ Plus gif](../assets/images/FAQPlusEndUser.gif)

## <a name="get-support-app-9734"></a><span data-ttu-id="9a6a3-261">Obter suporte de aplicativos &#9734;</span><span class="sxs-lookup"><span data-stu-id="9a6a3-261">Get Support App &#9734;</span></span>

<span data-ttu-id="9a6a3-262">O aplicativo Obter Suporte pode ser usado por organizações que estão usando o Microsoft Teams para permitir que qualquer conjunto de usuários solicite assistência de supervisores.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-262">The Get Support app can be used by organizations that are using Microsoft Teams, to enable any set of users to request assistance from supervisors.</span></span> <span data-ttu-id="9a6a3-263">Este aplicativo inclui vários recursos, como:</span><span class="sxs-lookup"><span data-stu-id="9a6a3-263">This app includes various features, such as:</span></span>
-   <span data-ttu-id="9a6a3-264">Solicitando assistência em diferentes categorias de um Power App</span><span class="sxs-lookup"><span data-stu-id="9a6a3-264">Requesting assistance on different categories from a Power App</span></span>
-   <span data-ttu-id="9a6a3-265">Notificações enviadas aos solicitadores informando quem foi atribuído</span><span class="sxs-lookup"><span data-stu-id="9a6a3-265">Notifications sent to requestors informing them of who has been assigned</span></span> 
-   <span data-ttu-id="9a6a3-266">Notificações enviadas a supervisores atribuídos informando quem precisa de assistência</span><span class="sxs-lookup"><span data-stu-id="9a6a3-266">Notifications sent to assigned supervisors informing them of who needs assistance</span></span> 
-   <span data-ttu-id="9a6a3-267">Analisando escalonamentos e padrões no SharePoint e no PowerBI</span><span class="sxs-lookup"><span data-stu-id="9a6a3-267">Analyzing escalations and patterns in SharePoint and PowerBI</span></span>

[<span data-ttu-id="9a6a3-268">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-268">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-app-get-support/)

![Obter Gif de Suporte](../assets/images/get-support.gif)

## <a name="goal-tracker"></a><span data-ttu-id="9a6a3-270">Rastreador de Meta</span><span class="sxs-lookup"><span data-stu-id="9a6a3-270">Goal Tracker</span></span>

<span data-ttu-id="9a6a3-271">O aplicativo Rastreador de Metas é uma solução abrangente para sua organização para dar suporte ao estabelecimento de metas, observar o progresso e reconhecer o sucesso no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-271">The Goal Tracker app is a comprehensive solution for your organization to support establishing goals, observing progress, and acknowledging success within Microsoft Teams.</span></span> <span data-ttu-id="9a6a3-272">O aplicativo permite aos usuários definir, rastrear e atualizar objetivos em um nível profissional, pessoal e de equipe.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-272">The app enables users to set, track, and update objectives on a professional, personal, and team level.</span></span> <span data-ttu-id="9a6a3-273">Os membros da equipe também recebem lembretes e atualizações de status em tempo há tempo para permanecerem focados e permanecerem no controle.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-273">Team members also receive timely reminders and status updates to remain focused and stay on track.</span></span>

[<span data-ttu-id="9a6a3-274">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-274">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-app-goaltracker)

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

## <a name="great-ideas"></a><span data-ttu-id="9a6a3-277">Ótimas ideias</span><span class="sxs-lookup"><span data-stu-id="9a6a3-277">Great Ideas</span></span>

<span data-ttu-id="9a6a3-278">O aplicativo Grandes Ideias dá suporte e capacita a inovação e a criatividade em sua organização.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-278">The Great Ideas app supports and empowers innovation and creativity within your organization.</span></span> <span data-ttu-id="9a6a3-279">O aplicativo permite que seus funcionários compartilhem ideias com colegas e liderança, descubram novos envios, destaquem as contribuições para consideração por pares e votem nas melhores propostas do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-279">The app enables your employees to share ideas with colleagues and leadership, discover new submissions, spotlight contributions for peer consideration, and cast their vote for the best proposals within Microsoft Teams.</span></span>

[<span data-ttu-id="9a6a3-280">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-280">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-greatideas)

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

## <a name="group-activities"></a><span data-ttu-id="9a6a3-283">Atividades de grupo</span><span class="sxs-lookup"><span data-stu-id="9a6a3-283">Group Activities</span></span>

<span data-ttu-id="9a6a3-284">Atividades de grupo é um aplicativo do Microsoft Teams que facilita que os proprietários da equipe criem rapidamente grupos de atividades e gerenciem fluxos de trabalho de colaboração no contexto do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-284">Group Activities is a Microsoft Teams app that makes it easy for team owners to quickly create activity groups and manage collaboration workflows within the context of Microsoft Teams.</span></span> <span data-ttu-id="9a6a3-285">Os autores de atividades estão habilitados para criar atividades, distribuir aleatoriamente membros da equipe em grupos e, opcionalmente, fazer com que o bot envie lembretes até que as atividades sejam concluídas.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-285">Activity authors are enabled to create activities, randomly distribute team members in groups, and optionally have the bot send reminders until activities are complete.</span></span>

[<span data-ttu-id="9a6a3-286">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-286">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-groupactivities)

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

## <a name="grow-your-skills"></a><span data-ttu-id="9a6a3-289">Aumentar suas habilidades</span><span class="sxs-lookup"><span data-stu-id="9a6a3-289">Grow Your Skills</span></span>

<span data-ttu-id="9a6a3-290">O aplicativo Crescer Suas Habilidades dá suporte ao crescimento e ao desenvolvimento profissional, permitindo que os funcionários contribuam com projetos complementares para sua organização e, ao mesmo tempo, aprendam novas habilidades.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-290">The Grow Your Skills app supports professional growth and development by enabling employees to contribute to supplemental projects for your organization while simultaneously learning new skills.</span></span> <span data-ttu-id="9a6a3-291">Os funcionários podem usar o aplicativo para localizar oportunidades que atendem aos seus interesses, desfrutar de colaboração significativa com pares e adquirir novos níveis de experiência e recursos, tudo dentro do ambiente do Teams.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-291">Employees can use the app to locate opportunities that meet their interests, enjoy meaningful collaboration with peers, and acquire new levels of expertise and capabilities, all within the Teams environment.</span></span>

[<span data-ttu-id="9a6a3-292">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-292">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-growyourskills)

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

## <a name="hr-support"></a><span data-ttu-id="9a6a3-295">Suporte de RH</span><span class="sxs-lookup"><span data-stu-id="9a6a3-295">HR Support</span></span>

<span data-ttu-id="9a6a3-296">O bot de Suporte de RH é um bot Q amigável&um bot que traz um profissional/especialista de suporte da equipe de RH no loop quando não consegue ajudar.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-296">HR Support bot is a friendly Q&A bot that brings a support professional/expert from the HR team in the loop when it is unable to help.</span></span> <span data-ttu-id="9a6a3-297">É possível fazer uma pergunta ao bot e o bot responde com uma resposta se ele estiver contido na base de dados de conhecimento.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-297">One can ask the bot a question and the bot responds with an answer if it is contained in the knowledge base.</span></span> <span data-ttu-id="9a6a3-298">Caso não seja, o bot permite que o usuário envie uma consulta que, em seguida, é postada em uma equipe pré-configurada de especialistas que ajudam a fornecer suporte agindo sobre as notificações de dentro de sua própria equipe.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-298">If not, the bot allows the user to submit a query which then gets posted in a pre-configured team of experts who are help to provide support by acting upon the notifications from within their team itself.</span></span> <span data-ttu-id="9a6a3-299">Além disso, o bot sugere links para políticas/perguntas recomendadas de RH pesquisando marcas pré-configuradas na pergunta.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-299">Additionally, the bot suggests links to recommended HR policies/questions by searching for pre-configured tags in the question.</span></span> <span data-ttu-id="9a6a3-300">Esses blocos também podem ser encontrados na guia associada como uma referência rápida.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-300">These tiles can also be found in the associated tab as a quick reference.</span></span> <span data-ttu-id="9a6a3-301">O Suporte de RH funciona bem para QnA de peso leve e para fornecer suporte rápido ao iniciar novos projetos/iniciativas na organização.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-301">HR Support works well for light weight QnA and to provide quick support when launching new projects/initiatives in the organization.</span></span>

[<span data-ttu-id="9a6a3-302">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-302">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-hrsupport-app)

![Suporte de RH](../assets/images/expert-user.png)

## <a name="icebreaker"></a><span data-ttu-id="9a6a3-304">Frases de apresentação</span><span class="sxs-lookup"><span data-stu-id="9a6a3-304">Icebreaker</span></span>

<span data-ttu-id="9a6a3-305">Icebreaker é um [bot do Microsoft Teams](../bots/what-are-bots.md) que ajuda sua equipe a se aproximar emparelhando dois membros aleatórios da equipe a cada semana para se reunir.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-305">Icebreaker is a [Microsoft Teams bot](../bots/what-are-bots.md) that helps your team get closer by pairing two random team members up every week to meet.</span></span> <span data-ttu-id="9a6a3-306">O bot facilita o agendamento sugerindo automaticamente tempos livres que funcionam para ambos os membros.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-306">The bot makes scheduling easy by automatically suggesting free times that work for both members.</span></span> <span data-ttu-id="9a6a3-307">Fortaleça conexões pessoais e crie uma comunidade estreita com esse aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-307">Strengthen personal connections and build a tightly knit community with this app.</span></span>

<span data-ttu-id="9a6a3-308">Além de incentivar conexões pessoais em toda a sua equipe, o aplicativo Icebreaker pode ajudar a criar comunidades baseadas em interesse em sua organização.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-308">In addition to encouraging personal connections across your entire team, the Icebreaker app can help cultivate interest-based communities within your organization.</span></span> <span data-ttu-id="9a6a3-309">Por exemplo, você pode usar esse aplicativo para um grupo de interesse de DevOps para ajudar ideias e práticas recomendadas a se propagar organicamente pela sua organização.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-309">For example, you can use this app for a DevOps interest group to help ideas and best practices organically spread across your organization.</span></span>

[<span data-ttu-id="9a6a3-310">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-310">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-icebreaker-app)

![Aplicativo quebra-gelo](../assets/images/icebreaker.png)

## <a name="incentives"></a><span data-ttu-id="9a6a3-312">Incentivos</span><span class="sxs-lookup"><span data-stu-id="9a6a3-312">Incentives</span></span>

<span data-ttu-id="9a6a3-313">Incentivos é um [modelo do Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) que gerencia e rastreia a participação de funcionários incentivados em atividades designadas, como treinamentos e iniciativas de gerenciamento de alterações.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-313">Incentives is a [Power Apps](/powerapps/maker/canvas-apps/embed-teams-app) template that manages and tracks incentivized employee participation in designated activities such as trainings and change management initiatives.</span></span> <span data-ttu-id="9a6a3-314">Os administradores usam o aplicativo para estabelecer atividades designadas, atribuir pontos para conclusão e especificar níveis de pontos de qualificação necessários para recompensas.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-314">Admins use the app to establish designated activities, assign points for completion, and specify required eligibility point levels for rewards.</span></span> <span data-ttu-id="9a6a3-315">Os funcionários usam o aplicativo para exibir seus pontos acumulados e, ao chegarem à qualificação, solicitam e solicitam recompensas resgatáveis.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-315">Employees use the app to view their accumulated points and, upon reaching eligibility, request and claim redeemable rewards.</span></span>

[<span data-ttu-id="9a6a3-316">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-316">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-incentives)

![Demonstração de aplicativo de incentivos](../assets/images/incentives-app.png)

## <a name="incident-reporter"></a><span data-ttu-id="9a6a3-318">Incident Reporter</span><span class="sxs-lookup"><span data-stu-id="9a6a3-318">Incident Reporter</span></span>

<span data-ttu-id="9a6a3-319">Incident Reporter é um [bot do Microsoft Teams](../bots/what-are-bots.md)  que otimiza o gerenciamento de incidentes em sua organização.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-319">Incident Reporter is a [Microsoft Teams bot](../bots/what-are-bots.md)  that optimizes the management of incidents in your organization.</span></span> <span data-ttu-id="9a6a3-320">O bot facilita a coleta automatizada de dados de incidentes, relatórios de incidentes personalizados, notificações relevantes de participantes e controle de incidentes de ponta a ponta.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-320">The bot facilitates automated incident data collection, customized incident reports, relevant stakeholder notifications, and end-to-end incident tracking.</span></span>

[<span data-ttu-id="9a6a3-321">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-321">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-incidentreport)

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

## <a name="inspection-9734"></a><span data-ttu-id="9a6a3-324">Inspeção &#9734;</span><span class="sxs-lookup"><span data-stu-id="9a6a3-324">Inspection &#9734;</span></span>

 <span data-ttu-id="9a6a3-325">A inspeção é um aplicativo do Microsoft Teams que permite que os funcionários de linha de frente inspecionem qualquer coisa de locais para ativos e equipamentos.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-325">Inspection is a Microsoft Teams app that enables front line workers to inspect anything from  locations to assets and equipments.</span></span> <span data-ttu-id="9a6a3-326">Por exemplo, uma loja de varejo, uma fábrica de manufatura ou veículos e máquinas.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-326">For example, a retail store, manufacturing plant, or vehicles and machines.</span></span> <span data-ttu-id="9a6a3-327">Há dois aplicativos nesta solução, cada um destinado a tipos diferentes de usuários.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-327">There are two apps in this solution, each intended for different types of users.</span></span>

<span data-ttu-id="9a6a3-328">O aplicativo capacita os funcionários de linha de frente a inspecionar um ativo ou área, gerenciar a qualidade de produtos e serviços ou manter a segurança no local de trabalho.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-328">The app empowers the front line workers to inspect an asset or area, to manage quality of products and services, or maintain safety at workplace.</span></span> <span data-ttu-id="9a6a3-329">Facilita a comunicação entre membros da equipe para resolver problemas encontrados durante a inspeção.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-329">It facilitates communication between team members to address issues found during inspection.</span></span> <span data-ttu-id="9a6a3-330">O aplicativo fornece relatórios simples para os gerentes agilizarem a resolução de problemas e realçam as tendências.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-330">The app provides simple reports for managers to expedite issue resolution and highlight trends.</span></span>

[<span data-ttu-id="9a6a3-331">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-331">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-inspection)

 ![Visão geral da inspeção](../assets/images/inspection-app.png)  


## <a name="issue-reporting"></a><span data-ttu-id="9a6a3-333">Relatório de Problemas</span><span class="sxs-lookup"><span data-stu-id="9a6a3-333">Issue Reporting</span></span>

<span data-ttu-id="9a6a3-334">O aplicativo Relatório de Problemas capacita os funcionários e gerentes a levantar e gerenciar problemas.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-334">The Issue Reporting app empowers the employees and managers to raise and manage issues.</span></span> <span data-ttu-id="9a6a3-335">Ele consiste em dois aplicativos, Emitir aplicativo de relatório para problemas de relatórios e gerenciar problemas do aplicativo para gerenciar problemas.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-335">It consists of two apps, Issue reporting app for reporting issues and Manage Issues app for managing issues.</span></span>

<span data-ttu-id="9a6a3-336">Os gerentes de equipe usam o aplicativo Gerenciar Problemas para configurar a experiência do aplicativo, incluindo o canal no qual as mensagens do Microsoft Teams e tarefas do Planner são criadas pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-336">The team managers use the Manage Issues app to configure the app experience, including the channel in which Microsoft Teams messages and Planner tasks are created by the app.</span></span> <span data-ttu-id="9a6a3-337">Os gerentes também usam o aplicativo para criar formulários de modelo para coletar detalhes quando um usuário relata um problema.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-337">Managers also use the app to create template forms to collect details when a user reports an issue.</span></span> <span data-ttu-id="9a6a3-338">Por exemplo, revise, edite ou exclua formulários de modelo de problema.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-338">For example, review, edit, or delete issue template forms.</span></span> <span data-ttu-id="9a6a3-339">O aplicativo também pode ser usado para revisar problemas de equipe, relatar o histórico de problemas e gerenciar com eficiência a resolução de problemas.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-339">The app can also be used to review team issues, report on issue history, and efficiently manage issue resolution.</span></span>

<span data-ttu-id="9a6a3-340">Os funcionários usam o aplicativo Demissão de relatórios para registrar problemas e detalhes necessários para resolvê-los.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-340">The employees use the Issue reporting app to log issues and details required to resolve them.</span></span> <span data-ttu-id="9a6a3-341">O aplicativo também é usado para modificar e resolver problemas existentes e obter uma visão de alto nível de problemas individuais ou de equipe.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-341">The app is also used to modify and resolve existing issues and get a high-level view of individual or team issues.</span></span>

[<span data-ttu-id="9a6a3-342">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-342">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-issuereporting)

![Emitir exibição de equipe de relatórios](../assets/images/issue-reporting-team-view.png)  

## <a name="new-employee-onboarding"></a><span data-ttu-id="9a6a3-344">Integração de novos funcionários</span><span class="sxs-lookup"><span data-stu-id="9a6a3-344">New Employee Onboarding</span></span> 

<span data-ttu-id="9a6a3-345">A Integração de Novos Funcionários é uma Solução integrada de Integração de Novos Funcionários do Microsoft Teams e do [SharePoint](https://lookbook.microsoft.com/details/75e60a32-9849-4ed4-b83e-b2b08983ad19) que permite que sua organização forneça uma experiência de integração consistente e de alta qualidade para os funcionários em sua jornada de nova contratação.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-345">New Employee Onboarding is an integrated Microsoft Teams and [SharePoint New Employee Onboarding Solution](https://lookbook.microsoft.com/details/75e60a32-9849-4ed4-b83e-b2b08983ad19) that enables your organization to provide a consistent, high-quality onboarding experience for employees on their new-hire journey.</span></span> <span data-ttu-id="9a6a3-346">O aplicativo pode ser usado por equipes de recursos humanos e gerentes de contratação para fornecer informações relevantes em todo o processo de orientação e indução e por novos contratados para compartilhar comentários, fornecer apresentações e concluir tarefas de integração.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-346">The app can be used by human resource teams and hiring managers to provide relevant information throughout the orientation and induction process and by new hires to share feedback, provide introductions, and complete onboarding tasks.</span></span>

[<span data-ttu-id="9a6a3-347">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-347">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-newemployeeonboarding)

:::row:::
  :::column span="2":::
    <span data-ttu-id="9a6a3-348">**Novo cartão de boas-vindas do funcionário** ![ Imagem do novo cartão de boas-vindas do funcionário](../assets/images/new-employee-welcome-card.png)</span><span class="sxs-lookup"><span data-stu-id="9a6a3-348">**New employee welcome card** ![Image of new employee welcome card](../assets/images/new-employee-welcome-card.png)</span></span>
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    <span data-ttu-id="9a6a3-349">**Nova lista de verificação de funcionários** ![ Imagem da nova lista de verificação de funcionários](../assets/images/new-employee-checklist.png)</span><span class="sxs-lookup"><span data-stu-id="9a6a3-349">**New employee checklist** ![Image of new employee checklist](../assets/images/new-employee-checklist.png)</span></span>  
:::column-end:::
:::row-end:::

## <a name="open-badges"></a><span data-ttu-id="9a6a3-350">Selos abertos</span><span class="sxs-lookup"><span data-stu-id="9a6a3-350">Open Badges</span></span>

<span data-ttu-id="9a6a3-351">Open Badges é um aplicativo do Microsoft Teams que permite que as pessoas ganhem selos de credencial de aprendizagem digital no contexto do Teams e compartilhem-os em todos os lugares.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-351">Open Badges is a Microsoft Teams app that enables individuals to earn digital learning credential badges within the Teams context and share them everywhere.</span></span> <span data-ttu-id="9a6a3-352">Usando recursos da autoridade de emissão de selo digital de terceiros, [o Badgr](https://badgr.org/), os selos concedidos são registrados no perfil Badgr de um destinatário e disponíveis para criar e compartilhar uma imagem rica das jornadas de aprendizado de vida útil.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-352">Using capabilities from the third-party digital badge issuing authority, [Badgr](https://badgr.org/), awarded badges are recorded in a recipient's Badgr profile and available to build and share a rich picture of lifetime learning journeys.</span></span>

[<span data-ttu-id="9a6a3-353">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-353">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-openbadges)

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

## <a name="poll"></a><span data-ttu-id="9a6a3-356">Sondagem</span><span class="sxs-lookup"><span data-stu-id="9a6a3-356">Poll</span></span> 

<span data-ttu-id="9a6a3-357">Poll é um aplicativo de extensão de mensagens personalizado do Microsoft [Teams](../messaging-extensions/what-are-messaging-extensions.md) que permite que você crie e envie votações rapidamente em um chat ou canal para coletar opiniões e preferências da equipe.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-357">Poll is a custom Microsoft Teams [messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that enables you to quickly create and send polls in a chat or a channel to gather team opinions and preferences.</span></span> <span data-ttu-id="9a6a3-358">O aplicativo tem suporte em todos os clientes de plataforma do Teams — desktop, navegador, iOS e Android — e está pronto para implantação como parte da sua assinatura do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-358">The app is supported across all Teams platform clients — desktop, browser, iOS, and Android  — and is ready for deployment as part of your Microsoft 365 subscription.</span></span>

[<span data-ttu-id="9a6a3-359">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-359">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-poll-app)

:::row:::
  :::column span="1":::
    ![Criar sondagem no exibição do Teams](../assets/images/poll-app-template-compose-view.gif)  
:::column-end:::
:::row-end:::

## <a name="quick-responses"></a><span data-ttu-id="9a6a3-361">Respostas rápidas</span><span class="sxs-lookup"><span data-stu-id="9a6a3-361">Quick Responses</span></span>

<span data-ttu-id="9a6a3-362">Respostas Rápidas é um aplicativo do Microsoft Teams que oferece uma solução robusta para responder efetivamente às perguntas frequentes (perguntas frequentes) dos usuários.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-362">Quick Responses is a Microsoft Teams app that delivers a robust solution for effectively answering users' commonly asked questions (FAQs).</span></span> <span data-ttu-id="9a6a3-363">Em vez de responder a cada consulta manualmente e continuamente repetindo informações, o aplicativo criará uma biblioteca de respostas para uma experiência interativa do usuário por meio de extensões de mensagens [do](../messaging-extensions/what-are-messaging-extensions.md)Teams.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-363">Instead of answering each query manually and  continuously repeating information, the app will build a library of responses for an interactive user experience via Teams [messaging extensions](../messaging-extensions/what-are-messaging-extensions.md).</span></span>

[<span data-ttu-id="9a6a3-364">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-364">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-quickresponses)

![Exemplo de exibição de respostas](../assets/images/quick-responses.png)


## <a name="rapid-assist"></a><span data-ttu-id="9a6a3-366">Assistência Rápida</span><span class="sxs-lookup"><span data-stu-id="9a6a3-366">Rapid Assist</span></span>

<span data-ttu-id="9a6a3-367">O Rapid Assist é um aplicativo baseado na Plataforma [Microsoft Power](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/) que permite que os associados voltados para o cliente se conectem rapidamente com os especialistas para obter respostas rápidas, pesquisar informações, acompanhar solicitações abertas e permitir que os especialistas recebam notificações para receber rapidamente uma chamada para ajudar a responder a perguntas.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-367">Rapid Assist is a Microsoft [Power Platform](https://powerapps.microsoft.com/blog/now-in-preview-customize-teams-with-built-in-power-platform-capabilities/) based app that allows customer facing associates to rapidly connect with the experts to get quick answers, search for information, follow up open requests, and allow experts to receive notifications to quickly get on a call to help answer questions.</span></span> <span data-ttu-id="9a6a3-368">O aplicativo criado usando o Microsoft [Power Apps](/powerapps/powerapps-overview) e o [Power Automate](/power-automate/getting-started), integra-se profundamente ao Microsoft Teams para permitir que as organizações conectem facilmente os funcionários de linha de frente com as ligações corporativas para resolver as consultas do cliente e oferecer uma ótima experiência do cliente.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-368">The app built using Microsoft [Power Apps](/powerapps/powerapps-overview) and [Power Automate](/power-automate/getting-started), deeply integrates with Microsoft Teams to enable organizations to easily connect frontline workers with corporate liaisons to resolve customer queries and deliver a great customer experience.</span></span> 

[<span data-ttu-id="9a6a3-369">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-369">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-rapid-assist)

:::row:::
   :::column span="":::
     ![Interface de solicitação de usuário final](../assets/images/EndUserHome.png)
   :::column-end:::
   :::column span="":::
      ![Exibição de solicitação de especialista](../assets/images/ExpertViewRequests.png)
   :::column-end:::
:::row-end:::

## <a name="reflect"></a><span data-ttu-id="9a6a3-372">Reflect</span><span class="sxs-lookup"><span data-stu-id="9a6a3-372">Reflect</span></span> 

<span data-ttu-id="9a6a3-373">Reflect é um aplicativo de extensão de mensagens personalizado do Microsoft [Teams](../messaging-extensions/what-are-messaging-extensions.md) que fornece um recurso seguro e inclusivo para os membros da equipe compartilharem o estado de seu bem-estar emocional com colegas e/ou líderes de grupo diretamente no Teams.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-373">Reflect is a custom Microsoft Teams [messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that provides a safe and inclusive resource for your team members to share the state of their emotional well-being with colleagues and/or group leaders directly within Teams.</span></span> <span data-ttu-id="9a6a3-374">O aplicativo está disponível em chats de canal, grupo, reunião e 1:1, e a resposta de check-in pode ser definida como pública, privada para remetente ou totalmente anônima.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-374">The app is available in channel, group, meeting, and 1:1 chats and the check-in response can be set to public, private-to-sender, or fully anonymous.</span></span>

[<span data-ttu-id="9a6a3-375">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-375">Get it on GitHub</span></span>](https://github.com/OfficeDev/Microsoft-Teams-App-Reflect)

:::row:::
    :::column:::
    <span data-ttu-id="9a6a3-376">**Sondagem de bem-estar**</span><span class="sxs-lookup"><span data-stu-id="9a6a3-376">**Well-being poll**</span></span>
    
    ![Refletir sondagem do usuário do aplicativo](../assets/images/reflect-app-user-poll.png)
    :::column-end:::
:::row-end:::

## <a name="remote-support"></a><span data-ttu-id="9a6a3-378">Suporte remoto</span><span class="sxs-lookup"><span data-stu-id="9a6a3-378">Remote Support</span></span>

<span data-ttu-id="9a6a3-379">O Suporte Remoto é um [bot do Microsoft Teams](../bots/what-are-bots.md) que fornece uma interface focada entre os solicitadores de suporte em toda a sua organização e a equipe de suporte interno.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-379">Remote Support is a [Microsoft Teams bot](../bots/what-are-bots.md) that provides a focused interface between support requesters throughout your organization and the internal support team.</span></span>  <span data-ttu-id="9a6a3-380">Os usuários finais podem enviar, editar ou retirar solicitações de suporte e a equipe de suporte pode responder, gerenciar e atualizar todas as solicitações dentro da plataforma do Teams.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-380">End-users can submit, edit, or withdraw requests for support and the support team can respond, manage, and update requests all within the Teams platform.</span></span>

[<span data-ttu-id="9a6a3-381">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-381">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-remotesupport)

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

## <a name="request-a-team"></a><span data-ttu-id="9a6a3-384">Request-a-team</span><span class="sxs-lookup"><span data-stu-id="9a6a3-384">Request-a-team</span></span>

<span data-ttu-id="9a6a3-385">Request-a-team é um aplicativo do Microsoft Teams que otimiza a criação de nova equipe para sua organização corporativa.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-385">Request-a-team is a Microsoft Teams app that optimizes new team creation for your enterprise organization.</span></span> <span data-ttu-id="9a6a3-386">O aplicativo dá suporte à padronização e às práticas recomendadas ao criar novas instâncias de equipe por meio da integração de um formulário de solicitação orientado pelo assistente, um processo de aprovação incorporado, um painel de status de solicitação e com builds de equipe automatizados.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-386">The app supports standardization and best practices when creating new team instances through the integration of a wizard-guided request form, an embedded approval process, a request status dashboard, and automated team builds.</span></span>

[<span data-ttu-id="9a6a3-387">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-387">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-requestateam)

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

## <a name="scrums-for-channels"></a><span data-ttu-id="9a6a3-390">Scrums for Channels</span><span class="sxs-lookup"><span data-stu-id="9a6a3-390">Scrums for Channels</span></span>

<span data-ttu-id="9a6a3-391">O Scrums for Channels é um aplicativo assistente scrum que permite que os usuários agendem e executem scrums em canais dentro do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-391">Scrums for Channels is a scrum assistant app that enables users to schedule and run scrums in channels within Microsoft Teams.</span></span> <span data-ttu-id="9a6a3-392">O aplicativo é ótimo para equipes remotas e equipes compostas por membros de locais geográficos e fusos horário variados para compartilhar atualizações diárias e garantir a participação em reuniões de stand-up scrum.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-392">The app is great for remote teams and teams comprised of members from varied geographical locations and time zones to share daily updates and ensure participation in scrum stand-up meetings.</span></span>

[<span data-ttu-id="9a6a3-393">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-393">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-scrumsforchannels)

> [!NOTE]
> <span data-ttu-id="9a6a3-394">Para conduzir reuniões scrum em um chat em grupo, consulte nosso modelo de aplicativo [Scrums for Group Chat.](#scrums-for-group-chat)</span><span class="sxs-lookup"><span data-stu-id="9a6a3-394">To conduct scrum meetings in a group chat, please see our [Scrums for Group Chat](#scrums-for-group-chat) app template.</span></span>

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

## <a name="scrums-for-group-chat"></a><span data-ttu-id="9a6a3-397">Scrums para Chat em Grupo</span><span class="sxs-lookup"><span data-stu-id="9a6a3-397">Scrums for Group Chat</span></span>

> [!NOTE]
> <span data-ttu-id="9a6a3-398">O modelo de aplicativo Status do Scrums foi atualizado e agora é Scrums para Chat de Grupo.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-398">The Scrums Status app template has been updated and is now Scrums for Group Chat.</span></span>

<span data-ttu-id="9a6a3-399">O Scrums for Group Chat é um assistente de scrum de suporte que permite que os membros do chat de grupo executem reuniões de stand-up assíncronas e compartilhem facilmente suas atualizações diárias.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-399">Scrums for Group Chat is a supportive scrum assistant that enables group chat members to run asynchronous stand-up meetings and easily share their daily updates.</span></span> <span data-ttu-id="9a6a3-400">Ele permite que todos os membros do chat de grupo contribuam para o scrum e exibir as atualizações feitas por outras pessoas no scrum em execução.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-400">It allows all members of the group chat to contribute to the scrum and view the updates made by others in the running scrum.</span></span>

[<span data-ttu-id="9a6a3-401">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-401">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-scrumsforgroupchat)

![Demonstração do Scrums for Group Chat](https://raw.githubusercontent.com/wiki/OfficeDev/microsoft-teams-app-scrumstatus/images/StartScrum.jpg)

## <a name="share-now"></a><span data-ttu-id="9a6a3-403">Compartilhar Agora</span><span class="sxs-lookup"><span data-stu-id="9a6a3-403">Share Now</span></span> 

<span data-ttu-id="9a6a3-404">O aplicativo Compartilhar Agora promove a troca positiva de informações entre colegas permitindo que seus usuários compartilhem facilmente conteúdo no ambiente do Teams.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-404">The Share Now app promotes the positive exchange of information between colleagues by enabling your users to easily share content within the Teams environment.</span></span> <span data-ttu-id="9a6a3-405">Os usuários envolvem o aplicativo para compartilhar itens de interesse com membros da equipe, descobrir novo conteúdo compartilhado, definir preferências e favoritos de indicador para leitura posterior.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-405">Users engage the app to share items of interest with team members, discover new shared content, set preferences, and bookmark favorites for later reading.</span></span>

[<span data-ttu-id="9a6a3-406">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-406">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-sharenow)

![Selecionar exibição de conteúdo](../assets/images/share-now-suggested-content.png)

## <a name="sharepoint-list-search"></a><span data-ttu-id="9a6a3-408">Pesquisa de lista do SharePoint</span><span class="sxs-lookup"><span data-stu-id="9a6a3-408">SharePoint List Search</span></span>

<span data-ttu-id="9a6a3-409">A colaboração no Microsoft Teams frequentemente faz referência a informações contidas em itens em uma lista do SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-409">Collaboration in Microsoft Teams quite often references information contained within items in a SharePoint list.</span></span> <span data-ttu-id="9a6a3-410">Simplesmente colar um link ao item em questão força todos a mudarem de contexto da conversa, encontrar as informações necessárias e retornar ao Teams para continuar a conversa.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-410">Simply pasting a link to the item in question forces everyone to switch context away from the conversation, find the needed information, then return to Teams to continue the conversation.</span></span> <span data-ttu-id="9a6a3-411">À medida que a conversa continua normalmente, as pessoas terão que voltar para o item de referência várias vezes para verificar novos comentários e atualizar suas recordações das informações contidas no item.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-411">As the conversation continues typically people will have to switch back to the reference item multiple times to verify new comments and refresh their memories of the information contained within the item.</span></span> <span data-ttu-id="9a6a3-412">Essa alternação de contexto cria uma barreira para suavizar a colaboração e é uma receita para as coisas que passam pelas trincas.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-412">This context switching creates a barrier to smooth collaboration, and is a recipe for things falling through the cracks.</span></span>

<span data-ttu-id="9a6a3-413">Para ajudar a aliviar essa dor, estamos felizes em trazer para você o modelo de aplicativo de Pesquisa de Lista.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-413">To help alleviate this pain, we are happy to bring to you the List Search app template.</span></span> <span data-ttu-id="9a6a3-414">Milhões de usuários usam o SharePoint para dar energia a alguns dos principais fluxos de trabalho em suas organizações.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-414">Millions of users use SharePoint to power some of the core workflows in their organizations.</span></span> <span data-ttu-id="9a6a3-415">No entanto, a colaboração em torno de listas pode ser especialmente tediosa.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-415">However, collaborating around lists can be especially tedious.</span></span> <span data-ttu-id="9a6a3-416">Usando o modelo de aplicativo de Pesquisa de Lista no Microsoft Teams, os usuários podem inserir informações de itens de lista do SharePoint diretamente em uma conversa de chat para aliviar a alternância de contexto causada ao simplesmente inserir um link em um chat.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-416">Using the List Search app template in Microsoft Teams, users can insert information from SharePoint list items directly within a chat conversation to alleviate the context-switching caused when simply inserting a link into a chat.</span></span> <span data-ttu-id="9a6a3-417">As informações são inseridas como um cartão de formatação automática fácil de ler, ajudando os usuários a permanecer envolvidos na conversa.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-417">The information is inserted as an easy-to-read auto-formatted card, helping your users stay engaged in the conversation.</span></span>

[<span data-ttu-id="9a6a3-418">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-418">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-list-search-app)

![Aplicativo de Pesquisa de Lista](../assets/images/list-search-template.png)

## <a name="staff-check-ins"></a><span data-ttu-id="9a6a3-420">Check-ins de equipe</span><span class="sxs-lookup"><span data-stu-id="9a6a3-420">Staff Check-ins</span></span>

<span data-ttu-id="9a6a3-421">Os Check-ins de equipe são um aplicativo baseado em [Power Apps](/powerapps/powerapps-overview)que permite a comunicação de supervisão entre sua empresa e a equipe de campo.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-421">Staff Check-ins is a [Power Apps](/powerapps/powerapps-overview)-based app that enables oversight communication between your business and field personnel.</span></span> <span data-ttu-id="9a6a3-422">A equipe pode fornecer informações e atualizações de status de tempo críticos facilmente em uma base agendada ou ad hoc diretamente do Teams.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-422">Staff can easily provide time-critical information and status updates on either a scheduled or ad-hoc basis directly from Teams.</span></span> <span data-ttu-id="9a6a3-423">O aplicativo oferece suporte a locais, fotos e anotações em tempo real, bem como notificações de lembrete e fluxos de trabalho automatizados.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-423">The app supports real-time location, photos, and notes as well as reminder notifications and automated workflows.</span></span>

[<span data-ttu-id="9a6a3-424">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-424">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-staffcheckins)

![Criar exibição de check-in](../assets/images/staff-check-ins-create.png)

## <a name="survey"></a><span data-ttu-id="9a6a3-426">Pesquisa</span><span class="sxs-lookup"><span data-stu-id="9a6a3-426">Survey</span></span>

<span data-ttu-id="9a6a3-427">A pesquisa é um aplicativo de extensão de mensagens personalizado do Microsoft [Teams](../messaging-extensions/what-are-messaging-extensions.md) que permite que você crie uma pesquisa em um chat ou canal para coletar dados e obter informações ativas.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-427">Survey is a custom Microsoft Teams [messaging extension](../messaging-extensions/what-are-messaging-extensions.md) app that enables you to create a survey in a chat or a channel to gather data and gain actionable insight.</span></span>  <span data-ttu-id="9a6a3-428">O aplicativo tem suporte em todos os clientes de plataforma do Teams — desktop, navegador, iOS e Android — e está pronto para implantação como parte da sua assinatura do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-428">The app is supported across all Teams platform clients — desktop, browser, iOS, and Android — and is ready for deployment as part of your Microsoft 365 subscription.</span></span>  

[<span data-ttu-id="9a6a3-429">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-429">Get it on GitHub</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Survey-app)

:::row:::
  :::column span="2":::
    ![Criar pesquisa no exibição do Teams](../assets/images/survey-app-template-compose-view.gif)
:::column-end:::
:::row-end:::

## <a name="time-tally-9734"></a><span data-ttu-id="9a6a3-431">Time Tally &#9734;</span><span class="sxs-lookup"><span data-stu-id="9a6a3-431">Time Tally &#9734;</span></span>

<span data-ttu-id="9a6a3-432">Um projeto pode incluir várias tarefas e vários projetos podem ser atribuídos aos funcionários.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-432">A project can include multiple tasks, and various projects can be assigned to employees.</span></span> <span data-ttu-id="9a6a3-433">Os gerentes são obrigados a entender o andamento do projeto pelo tempo gasto pelos funcionários nessas tarefas.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-433">Managers are required to understand the project progress through the time spent by the employees on these tasks.</span></span> <span data-ttu-id="9a6a3-434">Isso pode ser uma atividade complicada, pois os funcionários precisam preencher os quadro de horários.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-434">This can be a cumbersome activity, as the employees need to fill in the timesheets.</span></span> <span data-ttu-id="9a6a3-435">O aplicativo Time Tally permite que os funcionários preencham seus quadro de horários rapidamente, usando o dispositivo móvel, e os gerentes não têm que acompanhar os funcionários na entrada do quadro de horários.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-435">Time Tally app enables employees to fill their timesheets quickly, using the mobile device, and managers do not have to follow up with employees on the timesheet entry.</span></span> <span data-ttu-id="9a6a3-436">Os gerentes podem exibir a utilização do projeto com base em recursos e podem aprovar ou rejeitar as entradas.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-436">Managers get to view the project utilization based on resources, and they can approve or reject the entries.</span></span> <span data-ttu-id="9a6a3-437">As notificações de lembrete são enviadas para garantir a conformidade do quadro de horários.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-437">Reminder notifications are sent to ensure timesheet compliance.</span></span> <span data-ttu-id="9a6a3-438">Além disso, dados históricos e utilizações estão disponíveis para análise.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-438">Also, historical data and utilizations are available for analytics.</span></span>

[<span data-ttu-id="9a6a3-439">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-439">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-timetally)

![Time Tally](../assets/images/11zon_gif.gif)

## <a name="virtual-rounding"></a><span data-ttu-id="9a6a3-441">Arredondamento Virtual</span><span class="sxs-lookup"><span data-stu-id="9a6a3-441">Virtual Rounding</span></span>

<span data-ttu-id="9a6a3-442">Os provedores de sala de emergência e de emergência fazem dezenas e, muitas vezes, centenas de **rodadas** por dia.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-442">Hospital and emergency room providers make dozens, and often hundreds of **rounds** per day.</span></span> <span data-ttu-id="9a6a3-443">Esses check-ins rápidos em pacientes destinam-se a fornecer uma verificação de status sobre como o paciente está fazendo e garantir que as preocupações do paciente sejam resolvidas.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-443">These quick check-ins on patients are intended to provide a status check on how the patient is doing and ensure that the patient’s concerns are addressed.</span></span> <span data-ttu-id="9a6a3-444">Embora o arredondamento seja uma prática essencial para garantir que os pacientes sejam monitorados por vários tipos de provedores, eles representam um dreno enorme no PPE, pois para cada visita, de cada provedor, uma nova máscara e um novo conjunto de luvas devem ser usados.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-444">While rounding is an essential practice to ensure patients are being monitored by multiple types of providers, they represent a huge drain on PPE, because for each visit, from each provider, a new mask, and new set of gloves must be used.</span></span> <span data-ttu-id="9a6a3-445">Com esses modelos de aplicativo, os funcionários médicos podem conduzir facilmente rodadas virtualmente, por meio de uma reunião do Microsoft Teams entre o provedor e o paciente.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-445">With this app templates, medical workers can easily conduct rounds virtually, through a Microsoft Teams meeting between the provider and the patient.</span></span>

<span data-ttu-id="9a6a3-446">A solução de Arredondamento Virtual também é referenciada na postagem do [blog](https://aka.ms/teamsvirtualrounding)do Microsoft Health and Life Sciences.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-446">The Virtual Rounding solution is also referenced in the Microsoft Health and Life Sciences [blog post](https://aka.ms/teamsvirtualrounding).</span></span>

[<span data-ttu-id="9a6a3-447">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-447">Get it on GitHub</span></span>](https://github.com/SmartterHealth/Virtual-Rounding)

![Arredondamento Virtual](../assets/images/virtual-rounding-overview.png)

## <a name="visitor-management"></a><span data-ttu-id="9a6a3-449">Gerenciamento de Visitantes</span><span class="sxs-lookup"><span data-stu-id="9a6a3-449">Visitor Management</span></span>

<span data-ttu-id="9a6a3-450">O aplicativo de Gerenciamento de Visitantes permite que sua organização e funcionários gerenciem de forma fácil e eficiente o processo de visitante local, diretamente do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-450">The Visitor Management app enables your organization and employees to easily and efficiently manage the on-site visitor process, directly from Microsoft Teams.</span></span> <span data-ttu-id="9a6a3-451">O aplicativo permite que os funcionários criem solicitações de visitante, rastreiem centralmente um status de solicitação por meio do painel de visitantes e recebam notificações em tempo real quando um visitante chegar.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-451">The app enables employees to create visitor requests, centrally track a request status through the visitor dashboard, and receive real-time notifications when a visitor arrives.</span></span>

[<span data-ttu-id="9a6a3-452">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-452">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-app-visitormanagement)

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

## <a name="workplace-awards"></a><span data-ttu-id="9a6a3-455">Workplace Awards</span><span class="sxs-lookup"><span data-stu-id="9a6a3-455">Workplace Awards</span></span>

<span data-ttu-id="9a6a3-456">Workplace Awards é um modelo de aplicativo do Teams que fornece uma estrutura positiva para promover o reconhecimento e incentivar a cultura de valorização dos funcionários no local de trabalho moderno.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-456">Workplace Awards is a Teams app template that provides a positive framework to foster recognition and encourage the culture of employee appreciation in the modern workplace.</span></span> <span data-ttu-id="9a6a3-457">O aplicativo permite que você configure e gerencie um programa R&R (recompensas e reconhecimento de funcionários), onde os funcionários podem facilmente nomear e endossar colegas e seu líder R&R pode exibir indicações enviadas, conceder prêmios e anunciar destinatários.</span><span class="sxs-lookup"><span data-stu-id="9a6a3-457">The app enables you to setup and manage an employee rewards and recognition (R&R) program where employees can easily nominate and endorse colleagues and your R&R leader can view submitted nominations, grant awards, and announce recipients.</span></span>

[<span data-ttu-id="9a6a3-458">Obter no GitHub</span><span class="sxs-lookup"><span data-stu-id="9a6a3-458">Get it on GitHub</span></span>](https://github.com/OfficeDev/microsoft-teams-apps-workplaceawards)

:::row:::
  :::column span="2":::
    ![<span data-ttu-id="9a6a3-459">Cartão de nomeação de prêmio de local de trabalho</span><span class="sxs-lookup"><span data-stu-id="9a6a3-459">Workplace awards nomination card</span></span> ](../assets/images/workplace-awards-nominate.png)
:::column-end:::
:::row-end:::
:::row:::
:::column span="2":::
    ![Guia de lista de prêmios do local de trabalho](../assets/images/workplace-awards-champion-tab.png)
:::column-end:::
:::row-end:::

<span data-ttu-id="9a6a3-461">Tem uma ideia de um modelo de aplicativo que você gostaria de ver?</span><span class="sxs-lookup"><span data-stu-id="9a6a3-461">Have an idea for an app template you'd like to see?</span></span> <span data-ttu-id="9a6a3-462">[Por favor, nos avise](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR2_7qFm_lcZAr4eqEhnLsZ9UMVZGT1lCT0FXUDdZMUM0RkpBS1BESTAwWC4u).</span><span class="sxs-lookup"><span data-stu-id="9a6a3-462">[Please let us know](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR2_7qFm_lcZAr4eqEhnLsZ9UMVZGT1lCT0FXUDdZMUM0RkpBS1BESTAwWC4u).</span></span>
