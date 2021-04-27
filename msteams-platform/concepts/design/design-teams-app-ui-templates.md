---
title: Projetando seu aplicativo com modelos de interface do usuário
author: heath-hamilton
description: Projete seu aplicativo mais rapidamente com componentes de interface do usuário padronizados, layouts e padrões comumente vistos no Microsoft Teams.
ms.author: lajanuar
localization_priority: Normal
ms.topic: reference
ms.openlocfilehash: d627ce3b29ffa071d0d7e238c572c7cb69fa4cd9
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020762"
---
# <a name="designing-your-microsoft-teams-app-with-ui-templates"></a><span data-ttu-id="be6a7-103">Projetando seu aplicativo do Microsoft Teams com modelos de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="be6a7-103">Designing your Microsoft Teams app with UI templates</span></span>

<span data-ttu-id="be6a7-104">Projete seu aplicativo do Microsoft Teams mais rapidamente com modelos de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="be6a7-104">Design your Microsoft Teams app faster with UI templates.</span></span> <span data-ttu-id="be6a7-105">Os modelos são uma coleção de componentes baseados na interface do usuário fluente que funcionam em casos comuns de uso do Teams, dando mais tempo para você descobrir a melhor experiência para seus usuários.</span><span class="sxs-lookup"><span data-stu-id="be6a7-105">The templates are a collection of Fluent UI-based components that work across common Teams use cases, giving you more time to figure out the best experience for your users.</span></span>

## <a name="getting-started-with-tools-and-samples"></a><span data-ttu-id="be6a7-106">Iniciando com ferramentas e exemplos</span><span class="sxs-lookup"><span data-stu-id="be6a7-106">Getting started with tools and samples</span></span>

<span data-ttu-id="be6a7-107">Os recursos a seguir podem ajudá-lo a projetar e desenvolver seu aplicativo usando modelos de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="be6a7-107">The following resources can help you design and develop your app using UI templates.</span></span>

### <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="be6a7-108">Kit de Interface do Usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="be6a7-108">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="be6a7-109">Pegue modelos de interface do usuário para seu design de aplicativo no Kit de Interface do Usuário do Microsoft Teams, que também inclui informações abrangentes sobre uso, anatomia, acessibilidade e práticas recomendadas.</span><span class="sxs-lookup"><span data-stu-id="be6a7-109">Grab UI templates for your app design from the Microsoft Teams UI Kit, which also includes extensive information about usage, anatomy, accessibility, and best practices.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="be6a7-110">Obter o kit de interface do usuário (Figma)</span><span class="sxs-lookup"><span data-stu-id="be6a7-110">Get the UI kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

### <a name="microsoft-teams-ui-library"></a><span data-ttu-id="be6a7-111">Biblioteca de interface do usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="be6a7-111">Microsoft Teams UI Library</span></span>

<span data-ttu-id="be6a7-112">Exibir e testar modelos individuais de interface do usuário do Teams e componentes relacionados em seu navegador.</span><span class="sxs-lookup"><span data-stu-id="be6a7-112">View and test individual Teams UI templates and related components in your browser.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="be6a7-113">Experimente a biblioteca da interface do usuário (playground)</span><span class="sxs-lookup"><span data-stu-id="be6a7-113">Try the UI library (playground)</span></span>](https://dev-int.teams.microsoft.com/storybook/main/index.html)

<span data-ttu-id="be6a7-114">Importe esses modelos e componentes relacionados diretamente ao seu projeto de aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="be6a7-114">Import these templates and related components directly into your Teams app project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="be6a7-115">Obter a biblioteca da interface do usuário (GitHub)</span><span class="sxs-lookup"><span data-stu-id="be6a7-115">Get the UI library (GitHub)</span></span>](https://github.com/OfficeDev/microsoft-teams-ui-component-library)

### <a name="sample-app"></a><span data-ttu-id="be6a7-116">Exemplo de aplicativo</span><span class="sxs-lookup"><span data-stu-id="be6a7-116">Sample app</span></span>

<span data-ttu-id="be6a7-117">Instale um aplicativo de exemplo para ver como os modelos de interface do usuário são e se comportam em contextos do Teams.</span><span class="sxs-lookup"><span data-stu-id="be6a7-117">Install a sample app to see how UI templates look and behave within Teams contexts.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="be6a7-118">Obter o aplicativo de exemplo (GitHub)</span><span class="sxs-lookup"><span data-stu-id="be6a7-118">Get the sample app (GitHub)</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-ui-templates/ts)

## <a name="list"></a><span data-ttu-id="be6a7-119">List</span><span class="sxs-lookup"><span data-stu-id="be6a7-119">List</span></span>

<span data-ttu-id="be6a7-120">Você pode usar uma lista para exibir itens relacionados em um formato digitalizável e permitir que os usuários tomem ações em uma lista inteira ou itens individuais.</span><span class="sxs-lookup"><span data-stu-id="be6a7-120">You can use a list to display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>

:::image type="content" source="../../assets/images/ui-templates/list.png" alt-text="Exemplo mostra um modelo de interface do usuário de lista." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="be6a7-122">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="be6a7-122">Top use cases</span></span>

* <span data-ttu-id="be6a7-123">Exibir dados</span><span class="sxs-lookup"><span data-stu-id="be6a7-123">Display data</span></span>
* <span data-ttu-id="be6a7-124">Ações contextuais no conteúdo do aplicativo</span><span class="sxs-lookup"><span data-stu-id="be6a7-124">Contextual actions on app content</span></span>

## <a name="dashboard"></a><span data-ttu-id="be6a7-125">Painel</span><span class="sxs-lookup"><span data-stu-id="be6a7-125">Dashboard</span></span>

<span data-ttu-id="be6a7-126">Um painel exibe diferentes tipos de conteúdo em um local central (aplicativo pessoal ou guia do Teams).</span><span class="sxs-lookup"><span data-stu-id="be6a7-126">A dashboard displays different types of content in a central location (Teams personal app or tab).</span></span> <span data-ttu-id="be6a7-127">Os usuários devem ser capazes de personalizar pelo menos parte do que veem em um painel.</span><span class="sxs-lookup"><span data-stu-id="be6a7-127">Users should be able to customize at least some of what they see on a dashboard.</span></span>

:::image type="content" source="../../assets/images/ui-templates/dashboard.png" alt-text="Exemplo mostra um modelo de interface do usuário do painel." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="be6a7-129">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="be6a7-129">Top use cases</span></span>

* <span data-ttu-id="be6a7-130">Analisar dados</span><span class="sxs-lookup"><span data-stu-id="be6a7-130">Analyze data</span></span>
* <span data-ttu-id="be6a7-131">Métricas de relatório</span><span class="sxs-lookup"><span data-stu-id="be6a7-131">Report metrics</span></span>
* <span data-ttu-id="be6a7-132">Organizar informações diferentes em um só lugar</span><span class="sxs-lookup"><span data-stu-id="be6a7-132">Organize different information in one place</span></span>

## <a name="form"></a><span data-ttu-id="be6a7-133">Formulário</span><span class="sxs-lookup"><span data-stu-id="be6a7-133">Form</span></span>

<span data-ttu-id="be6a7-134">Os formulários são usados para coletar, validar e enviar entrada do usuário de forma estruturada.</span><span class="sxs-lookup"><span data-stu-id="be6a7-134">Forms are used to collect, validate, and submit user input in a structured way.</span></span> <span data-ttu-id="be6a7-135">A rotulagem limpa e os agrupamentos lógicos de campos de entrada são essenciais para uma boa experiência do usuário.</span><span class="sxs-lookup"><span data-stu-id="be6a7-135">Clear labeling and logical groupings of input fields are critical for a good user experience.</span></span>

:::image type="content" source="../../assets/images/ui-templates/form.png" alt-text="Exemplo mostra um modelo de interface do usuário de formulário." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="be6a7-137">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="be6a7-137">Top use cases</span></span>

* <span data-ttu-id="be6a7-138">Entrar</span><span class="sxs-lookup"><span data-stu-id="be6a7-138">Sign in</span></span>
* <span data-ttu-id="be6a7-139">Perfis de usuário</span><span class="sxs-lookup"><span data-stu-id="be6a7-139">User profiles</span></span>
* <span data-ttu-id="be6a7-140">Settings</span><span class="sxs-lookup"><span data-stu-id="be6a7-140">Settings</span></span>
* <span data-ttu-id="be6a7-141">Coleção de entrada do usuário</span><span class="sxs-lookup"><span data-stu-id="be6a7-141">User input collection</span></span>

## <a name="sign-in"></a><span data-ttu-id="be6a7-142">Entrar</span><span class="sxs-lookup"><span data-stu-id="be6a7-142">Sign in</span></span>

<span data-ttu-id="be6a7-143">Você pode projetar fluxos de entrada de aplicativos para diferentes contextos do Teams e provedores de identidade.</span><span class="sxs-lookup"><span data-stu-id="be6a7-143">You can design app sign-in flows for different Teams contexts and identity providers.</span></span> <span data-ttu-id="be6a7-144">O exemplo a seguir inclui o logom único (SSO), que recomendamos para a experiência de autenticação mais simples.</span><span class="sxs-lookup"><span data-stu-id="be6a7-144">The following example includes single sign-on (SSO), which we recommend for the simplest authentication experience.</span></span>

:::image type="content" source="../../assets/images/ui-templates/sign-in.png" alt-text="Exemplo mostra um modelo de interface do usuário de login." border="false":::

### <a name="top-use-case"></a><span data-ttu-id="be6a7-146">Caso de uso superior</span><span class="sxs-lookup"><span data-stu-id="be6a7-146">Top use case</span></span>

* <span data-ttu-id="be6a7-147">Autenticar usuários</span><span class="sxs-lookup"><span data-stu-id="be6a7-147">Authenticate users</span></span>

## <a name="task-board"></a><span data-ttu-id="be6a7-148">Quadro de Tarefas</span><span class="sxs-lookup"><span data-stu-id="be6a7-148">Task board</span></span>

<span data-ttu-id="be6a7-149">Um quadro de tarefas, às vezes chamado de quadro de kanban ou faixas de nadador, é uma coleção de cartões frequentemente usada para rastrear o status de itens de trabalho ou tíquetes.</span><span class="sxs-lookup"><span data-stu-id="be6a7-149">A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span> <span data-ttu-id="be6a7-150">Ele também pode ser usado para classificar qualquer tipo de conteúdo em categorias.</span><span class="sxs-lookup"><span data-stu-id="be6a7-150">It can also be used to sort any type of content into categories.</span></span> <span data-ttu-id="be6a7-151">Você pode editar e mover os cartões entre colunas.</span><span class="sxs-lookup"><span data-stu-id="be6a7-151">You can edit and move the cards between columns.</span></span>

:::image type="content" source="../../assets/images/ui-templates/task-board.png" alt-text="Exemplo mostra um modelo de interface do usuário do quadro de tarefas." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="be6a7-153">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="be6a7-153">Top use cases</span></span>

* <span data-ttu-id="be6a7-154">Gerenciamento de projetos.</span><span class="sxs-lookup"><span data-stu-id="be6a7-154">Project management.</span></span> <span data-ttu-id="be6a7-155">Atribuindo tarefas e status de controle</span><span class="sxs-lookup"><span data-stu-id="be6a7-155">Assigning tasks and tracking status</span></span>
* <span data-ttu-id="be6a7-156">Brainstorming.</span><span class="sxs-lookup"><span data-stu-id="be6a7-156">Brainstorming.</span></span> <span data-ttu-id="be6a7-157">Adicionar ideias em categorias diferentes</span><span class="sxs-lookup"><span data-stu-id="be6a7-157">Adding ideas in different categories</span></span>
* <span data-ttu-id="be6a7-158">Exercícios de classificação.</span><span class="sxs-lookup"><span data-stu-id="be6a7-158">Sorting exercises.</span></span> <span data-ttu-id="be6a7-159">Organizar qualquer tipo de informação em buckets</span><span class="sxs-lookup"><span data-stu-id="be6a7-159">Organizing any kind of information into buckets</span></span>

## <a name="data-visualization"></a><span data-ttu-id="be6a7-160">Visualização de dados</span><span class="sxs-lookup"><span data-stu-id="be6a7-160">Data visualization</span></span>

<span data-ttu-id="be6a7-161">Você pode usar tamanhos de cartão diferentes (único, duplo e completo) para empilhar e organizar visualizações de dados na mesma página.</span><span class="sxs-lookup"><span data-stu-id="be6a7-161">You can use different card sizes (single, double, and full) to stack and organize data visualizations on the same page.</span></span> <span data-ttu-id="be6a7-162">A escala de cartões para ajustar o layout da coluna e preencher espaços em branco.</span><span class="sxs-lookup"><span data-stu-id="be6a7-162">The cards scale to fit the column layout and fill in blank spaces.</span></span>

:::image type="content" source="../../assets/images/ui-templates/data-viz.png" alt-text="Exemplo mostra um modelo de interface do usuário de visualização de dados." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="be6a7-164">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="be6a7-164">Top use cases</span></span>

* <span data-ttu-id="be6a7-165">Exibir informações complexas</span><span class="sxs-lookup"><span data-stu-id="be6a7-165">Display complex information</span></span>
* <span data-ttu-id="be6a7-166">Criar um painel</span><span class="sxs-lookup"><span data-stu-id="be6a7-166">Create a dashboard</span></span>

## <a name="wizard"></a><span data-ttu-id="be6a7-167">Assistente</span><span class="sxs-lookup"><span data-stu-id="be6a7-167">Wizard</span></span>

<span data-ttu-id="be6a7-168">Um assistente orienta um usuário por várias telas para concluir uma tarefa (como um processo de instalação).</span><span class="sxs-lookup"><span data-stu-id="be6a7-168">A wizard guides a user through several screens to complete a task (such as a setup process).</span></span>

:::image type="content" source="../../assets/images/ui-templates/wizard.png" alt-text="Exemplo mostra um modelo de interface do usuário do assistente." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="be6a7-170">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="be6a7-170">Top use cases</span></span>

* <span data-ttu-id="be6a7-171">Configurar</span><span class="sxs-lookup"><span data-stu-id="be6a7-171">Setup</span></span>
* <span data-ttu-id="be6a7-172">Integração</span><span class="sxs-lookup"><span data-stu-id="be6a7-172">Onboarding</span></span>
* <span data-ttu-id="be6a7-173">Experiências de primeira</span><span class="sxs-lookup"><span data-stu-id="be6a7-173">First-run experiences</span></span>

## <a name="empty-state"></a><span data-ttu-id="be6a7-174">Estado vazio</span><span class="sxs-lookup"><span data-stu-id="be6a7-174">Empty state</span></span>

<span data-ttu-id="be6a7-175">O modelo de estado vazio pode ser usado para muitos cenários, incluindo entrar, experiências de primeira executar, mensagens de erro e muito mais.</span><span class="sxs-lookup"><span data-stu-id="be6a7-175">The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span> <span data-ttu-id="be6a7-176">É altamente flexível, adaptá-lo para usar um, alguns ou todos os componentes no design a seguir.</span><span class="sxs-lookup"><span data-stu-id="be6a7-176">It’s highly flexible⁠—adapt it to use one, a few, or all of the components in the following design.</span></span>

:::image type="content" source="../../assets/images/ui-templates/empty-state.png" alt-text="Exemplo mostra um modelo de interface do usuário de estado vazio." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="be6a7-178">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="be6a7-178">Top use cases</span></span>

* <span data-ttu-id="be6a7-179">Entrar</span><span class="sxs-lookup"><span data-stu-id="be6a7-179">Sign in</span></span>
* <span data-ttu-id="be6a7-180">Mensagens de boas-vindas e experiências de primeira fase</span><span class="sxs-lookup"><span data-stu-id="be6a7-180">Welcome messages and first-run experiences</span></span>
* <span data-ttu-id="be6a7-181">Mensagens de sucesso</span><span class="sxs-lookup"><span data-stu-id="be6a7-181">Success messages</span></span>
* <span data-ttu-id="be6a7-182">Mensagens de erro</span><span class="sxs-lookup"><span data-stu-id="be6a7-182">Error messages</span></span>

## <a name="notification-bar"></a><span data-ttu-id="be6a7-183">Notification bar</span><span class="sxs-lookup"><span data-stu-id="be6a7-183">Notification bar</span></span>

<span data-ttu-id="be6a7-184">Uma barra de notificação é uma área dedicada para exibir uma mensagem breve e importante que não exige que o usuário tome medidas imediatas.</span><span class="sxs-lookup"><span data-stu-id="be6a7-184">A notification bar is a dedicated area for displaying a brief, important messages that do not require the user to take immediate action.</span></span> <span data-ttu-id="be6a7-185">Cores e ícones específicos de plano de fundo estão associados a tipos específicos de mensagens (consulte abaixo).</span><span class="sxs-lookup"><span data-stu-id="be6a7-185">Specific background colors and icons are associated with specific types of messages (see below).</span></span>

:::image type="content" source="../../assets/images/ui-templates/notification-bar.png" alt-text="Exemplo mostra modelos de barra de notificação." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="be6a7-187">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="be6a7-187">Top use cases</span></span>

* <span data-ttu-id="be6a7-188">Mensagens críticas, erros e avisos</span><span class="sxs-lookup"><span data-stu-id="be6a7-188">Critical messages, errors, and warnings</span></span>
* <span data-ttu-id="be6a7-189">Mensagens de sucesso</span><span class="sxs-lookup"><span data-stu-id="be6a7-189">Success messages</span></span>
* <span data-ttu-id="be6a7-190">Mensagens informativas ou promocionais</span><span class="sxs-lookup"><span data-stu-id="be6a7-190">Informational or promotional messages</span></span>

## <a name="left-nav"></a><span data-ttu-id="be6a7-191">Nav esquerdo</span><span class="sxs-lookup"><span data-stu-id="be6a7-191">Left nav</span></span>

<span data-ttu-id="be6a7-192">Use a navegação esquerda para navegar por várias páginas na guia Teams. No exemplo a seguir, a navegação à esquerda está entre a lista de canais e o conteúdo da guia.</span><span class="sxs-lookup"><span data-stu-id="be6a7-192">Use the left nav to browse multiple pages within your Teams tab. In the following example, the left nav is between the channel list and tab content.</span></span>

:::image type="content" source="../../assets/images/ui-templates/left-nav.png" alt-text="Exemplo mostra um modelo de nav esquerdo." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="be6a7-194">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="be6a7-194">Top use cases</span></span>

* <span data-ttu-id="be6a7-195">Procurar várias páginas em uma guia do Teams</span><span class="sxs-lookup"><span data-stu-id="be6a7-195">Browse multiple pages within a Teams tab</span></span>
* <span data-ttu-id="be6a7-196">Separar aplicativos complexos em várias páginas</span><span class="sxs-lookup"><span data-stu-id="be6a7-196">Break down complex apps into multiple pages</span></span>

## <a name="breadcrumb"></a><span data-ttu-id="be6a7-197">Trilha</span><span class="sxs-lookup"><span data-stu-id="be6a7-197">Breadcrumb</span></span>

<span data-ttu-id="be6a7-198">Os breadcrumbs são um auxílio de navegação que transmitem a hierarquia do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="be6a7-198">Breadcrumbs are a navigational aid that convey your app’s hierarchy.</span></span> <span data-ttu-id="be6a7-199">Eles ajudam os usuários a entender como a página que estão exibindo se encaixa na experiência geral e proporcionam acesso de um clique a níveis mais altos nessa hierarquia.</span><span class="sxs-lookup"><span data-stu-id="be6a7-199">They help users understand how the page they’re viewing fits into the overall experience and afford one-click access to higher levels in that hierarchy.</span></span>

:::image type="content" source="../../assets/images/ui-templates/breadcrumb.png" alt-text="Exemplo mostra um modelo de breadcrumb." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="be6a7-201">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="be6a7-201">Top use cases</span></span>

* <span data-ttu-id="be6a7-202">Hierarquia de comunicações</span><span class="sxs-lookup"><span data-stu-id="be6a7-202">Communicate hierarchy</span></span>
* <span data-ttu-id="be6a7-203">Navegação</span><span class="sxs-lookup"><span data-stu-id="be6a7-203">Navigation</span></span>

## <a name="toolbar"></a><span data-ttu-id="be6a7-204">Barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="be6a7-204">Toolbar</span></span>

<span data-ttu-id="be6a7-205">Uma barra de ferramentas é um contêiner para agrupar um conjunto de controles.</span><span class="sxs-lookup"><span data-stu-id="be6a7-205">A toolbar is a container for grouping a set of controls.</span></span>

:::image type="content" source="../../assets/images/ui-templates/toolbar.png" alt-text="Exemplo mostra um modelo de barra de ferramentas." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="be6a7-207">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="be6a7-207">Top use cases</span></span>

* <span data-ttu-id="be6a7-208">Ações contextuais no conteúdo do aplicativo</span><span class="sxs-lookup"><span data-stu-id="be6a7-208">Contextual actions on app content</span></span>
* <span data-ttu-id="be6a7-209">Filtro contextual e local</span><span class="sxs-lookup"><span data-stu-id="be6a7-209">Contextual filter and find</span></span>
* <span data-ttu-id="be6a7-210">Navegação e controles de navegação</span><span class="sxs-lookup"><span data-stu-id="be6a7-210">Navigation and breadcrumbs</span></span>

## <a name="stage"></a><span data-ttu-id="be6a7-211">Estágio</span><span class="sxs-lookup"><span data-stu-id="be6a7-211">Stage</span></span>

<span data-ttu-id="be6a7-212">O estágio oferece uma maneira de os usuários abrirem uma entidade, como uma imagem, arquivo ou site, no Teams, em vez de abri-la em outro aplicativo ou navegador.</span><span class="sxs-lookup"><span data-stu-id="be6a7-212">Stage offers a way for users to open an entity—like an image, file, or website—in Teams instead of opening it in another app or browser.</span></span> <span data-ttu-id="be6a7-213">O principal caso de uso do estágio é exibição; a superfície não deve ser usada para interações complexas.</span><span class="sxs-lookup"><span data-stu-id="be6a7-213">The primary use case of stage is viewing; the surface should not be used for complex interactions.</span></span>

<span data-ttu-id="be6a7-214">(Observação de implementação: crie seu estágio usando um módulo [de tarefa grande](../../task-modules-and-cards/task-modules/design-teams-task-modules.md).)</span><span class="sxs-lookup"><span data-stu-id="be6a7-214">(Implementation note: Build your stage using a large [task module](../../task-modules-and-cards/task-modules/design-teams-task-modules.md).)</span></span>

:::image type="content" source="../../assets/images/ui-templates/stage.png" alt-text="Exemplo mostra um modelo de estágio." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="be6a7-216">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="be6a7-216">Top use cases</span></span>

* <span data-ttu-id="be6a7-217">Abra uma entidade no Teams em vez de outro aplicativo ou navegador</span><span class="sxs-lookup"><span data-stu-id="be6a7-217">Open an entity in Teams instead of another app or browser</span></span>
* <span data-ttu-id="be6a7-218">Mídia em destaque ou outro conteúdo</span><span class="sxs-lookup"><span data-stu-id="be6a7-218">Spotlight media or other content</span></span>
