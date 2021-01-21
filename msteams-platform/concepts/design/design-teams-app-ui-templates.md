---
title: Projetando seu aplicativo com modelos de interface do usuário
author: heath-hamilton
description: Projete seu aplicativo mais rapidamente com componentes, layouts e padrões padronizados da interface do usuário geralmente vistos no Microsoft Teams.
ms.author: lajanuar
ms.topic: reference
ms.openlocfilehash: b4d244bbf78ac85042d5caf8ec84afe42e79b3c7
ms.sourcegitcommit: 00c657e3bf57d3b92aca7da941cde47a2eeff4d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "49911923"
---
# <a name="designing-your-microsoft-teams-app-with-ui-templates"></a><span data-ttu-id="2f37f-103">Projetando seu aplicativo Microsoft Teams com modelos de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="2f37f-103">Designing your Microsoft Teams app with UI templates</span></span>

<span data-ttu-id="2f37f-104">Projete seu aplicativo Microsoft Teams mais rapidamente com modelos de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="2f37f-104">Design your Microsoft Teams app faster with UI templates.</span></span> <span data-ttu-id="2f37f-105">Os modelos são um conjunto de componentes baseados na interface do usuário fluente que funcionam em casos de uso comuns do Teams, dando mais tempo para você descobrir a melhor experiência para seus usuários.</span><span class="sxs-lookup"><span data-stu-id="2f37f-105">The templates are a collection of Fluent UI-based components that work across common Teams use cases, giving you more time to figure out the best experience for your users.</span></span>

## <a name="getting-started-with-tools-and-samples"></a><span data-ttu-id="2f37f-106">Getting started with tools and samples</span><span class="sxs-lookup"><span data-stu-id="2f37f-106">Getting started with tools and samples</span></span>

<span data-ttu-id="2f37f-107">Os recursos a seguir podem ajudá-lo a projetar e desenvolver seu aplicativo usando modelos de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="2f37f-107">The following resources can help you design and develop your app using UI templates.</span></span>

### <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="2f37f-108">Kit de interface do usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="2f37f-108">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="2f37f-109">Pegue modelos de interface do usuário para seu design de aplicativo do Kit de Interface do Usuário do Microsoft Teams, que também inclui informações abrangentes sobre uso, anatomia, acessibilidade e práticas recomendadas.</span><span class="sxs-lookup"><span data-stu-id="2f37f-109">Grab UI templates for your app design from the Microsoft Teams UI Kit, which also includes extensive information about usage, anatomy, accessibility, and best practices.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2f37f-110">Obter o kit de interface do usuário (Ltdma)</span><span class="sxs-lookup"><span data-stu-id="2f37f-110">Get the UI kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

### <a name="microsoft-teams-ui-library"></a><span data-ttu-id="2f37f-111">Biblioteca de interface do usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="2f37f-111">Microsoft Teams UI Library</span></span>

<span data-ttu-id="2f37f-112">Exibir e testar modelos de interface do usuário individuais do Teams e componentes relacionados em seu navegador.</span><span class="sxs-lookup"><span data-stu-id="2f37f-112">View and test individual Teams UI templates and related components in your browser.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2f37f-113">Experimente a biblioteca de interface do usuário (playground)</span><span class="sxs-lookup"><span data-stu-id="2f37f-113">Try the UI library (playground)</span></span>](https://dev-int.teams.microsoft.com/storybook/main/index.html)

<span data-ttu-id="2f37f-114">Importe esses modelos e componentes relacionados diretamente para seu projeto de aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="2f37f-114">Import these templates and related components directly into your Teams app project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2f37f-115">Obter a biblioteca de interface do usuário (GitHub)</span><span class="sxs-lookup"><span data-stu-id="2f37f-115">Get the UI library (GitHub)</span></span>](https://github.com/OfficeDev/microsoft-teams-ui-component-library)

### <a name="sample-app"></a><span data-ttu-id="2f37f-116">Aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="2f37f-116">Sample app</span></span>

<span data-ttu-id="2f37f-117">Instale um aplicativo de exemplo para ver a aparência e o comportamento dos modelos de interface do usuário nos contextos do Teams.</span><span class="sxs-lookup"><span data-stu-id="2f37f-117">Install a sample app to see how UI templates look and behave within Teams contexts.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2f37f-118">Obter o aplicativo de exemplo (GitHub)</span><span class="sxs-lookup"><span data-stu-id="2f37f-118">Get the sample app (GitHub)</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-ui-templates/ts)

## <a name="list"></a><span data-ttu-id="2f37f-119">Listar</span><span class="sxs-lookup"><span data-stu-id="2f37f-119">List</span></span>

<span data-ttu-id="2f37f-120">Você pode usar uma lista para exibir itens relacionados em um formato digitalizável e permitir que os usuários tomem ações em uma lista inteira ou itens individuais.</span><span class="sxs-lookup"><span data-stu-id="2f37f-120">You can use a list to display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>

:::image type="content" source="../../assets/images/ui-templates/list.png" alt-text="O exemplo mostra um modelo de interface do usuário de lista." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="2f37f-122">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="2f37f-122">Top use cases</span></span>

* <span data-ttu-id="2f37f-123">Exibir dados</span><span class="sxs-lookup"><span data-stu-id="2f37f-123">Display data</span></span>
* <span data-ttu-id="2f37f-124">Ações contextuais no conteúdo do aplicativo</span><span class="sxs-lookup"><span data-stu-id="2f37f-124">Contextual actions on app content</span></span>

## <a name="dashboard"></a><span data-ttu-id="2f37f-125">Painel</span><span class="sxs-lookup"><span data-stu-id="2f37f-125">Dashboard</span></span>

<span data-ttu-id="2f37f-126">Um painel exibe diferentes tipos de conteúdo em um local central (aplicativo pessoal ou guia do Teams).</span><span class="sxs-lookup"><span data-stu-id="2f37f-126">A dashboard displays different types of content in a central location (Teams personal app or tab).</span></span> <span data-ttu-id="2f37f-127">Os usuários devem ser capazes de personalizar pelo menos parte do que veem em um painel.</span><span class="sxs-lookup"><span data-stu-id="2f37f-127">Users should be able to customize at least some of what they see on a dashboard.</span></span>

:::image type="content" source="../../assets/images/ui-templates/dashboard.png" alt-text="O exemplo mostra um modelo de interface do usuário do painel." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="2f37f-129">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="2f37f-129">Top use cases</span></span>

* <span data-ttu-id="2f37f-130">Analisar dados</span><span class="sxs-lookup"><span data-stu-id="2f37f-130">Analyze data</span></span>
* <span data-ttu-id="2f37f-131">Métricas de relatório</span><span class="sxs-lookup"><span data-stu-id="2f37f-131">Report metrics</span></span>
* <span data-ttu-id="2f37f-132">Organizar informações diferentes em um só lugar</span><span class="sxs-lookup"><span data-stu-id="2f37f-132">Organize different information in one place</span></span>

## <a name="form"></a><span data-ttu-id="2f37f-133">Formulário</span><span class="sxs-lookup"><span data-stu-id="2f37f-133">Form</span></span>

<span data-ttu-id="2f37f-134">Os formulários são usados para coletar, validar e enviar entradas do usuário de maneira estruturada.</span><span class="sxs-lookup"><span data-stu-id="2f37f-134">Forms are used to collect, validate, and submit user input in a structured way.</span></span> <span data-ttu-id="2f37f-135">Limpar a rotulagem e os agrupamentos lógicos dos campos de entrada são fundamentais para uma boa experiência do usuário.</span><span class="sxs-lookup"><span data-stu-id="2f37f-135">Clear labeling and logical groupings of input fields are critical for a good user experience.</span></span>

:::image type="content" source="../../assets/images/ui-templates/form.png" alt-text="O exemplo mostra um modelo de interface do usuário do formulário." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="2f37f-137">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="2f37f-137">Top use cases</span></span>

* <span data-ttu-id="2f37f-138">Entrar</span><span class="sxs-lookup"><span data-stu-id="2f37f-138">Sign in</span></span>
* <span data-ttu-id="2f37f-139">Perfis de usuário</span><span class="sxs-lookup"><span data-stu-id="2f37f-139">User profiles</span></span>
* <span data-ttu-id="2f37f-140">Configurações</span><span class="sxs-lookup"><span data-stu-id="2f37f-140">Settings</span></span>
* <span data-ttu-id="2f37f-141">Coleção de entrada do usuário</span><span class="sxs-lookup"><span data-stu-id="2f37f-141">User input collection</span></span>

## <a name="sign-in"></a><span data-ttu-id="2f37f-142">Entrar</span><span class="sxs-lookup"><span data-stu-id="2f37f-142">Sign in</span></span>

<span data-ttu-id="2f37f-143">Você pode projetar fluxos de entrada do aplicativo para diferentes contextos e provedores de identidade do Teams.</span><span class="sxs-lookup"><span data-stu-id="2f37f-143">You can design app sign-in flows for different Teams contexts and identity providers.</span></span> <span data-ttu-id="2f37f-144">O exemplo a seguir inclui o SSO (logo único), que recomendamos para a experiência de autenticação mais simples.</span><span class="sxs-lookup"><span data-stu-id="2f37f-144">The following example includes single sign-on (SSO), which we recommend for the simplest authentication experience.</span></span>

:::image type="content" source="../../assets/images/ui-templates/sign-in.png" alt-text="O exemplo mostra um modelo de interface do usuário de login." border="false":::

### <a name="top-use-case"></a><span data-ttu-id="2f37f-146">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="2f37f-146">Top use case</span></span>

* <span data-ttu-id="2f37f-147">Autenticar usuários</span><span class="sxs-lookup"><span data-stu-id="2f37f-147">Authenticate users</span></span>

## <a name="task-board"></a><span data-ttu-id="2f37f-148">Quadro de tarefas</span><span class="sxs-lookup"><span data-stu-id="2f37f-148">Task board</span></span>

<span data-ttu-id="2f37f-149">Um quadro de tarefas, às vezes chamado de tabuleiro kanban ou trilhos de mesa, é uma coleção de cartões frequentemente usada para acompanhar o status de itens de trabalho ou tíquetes.</span><span class="sxs-lookup"><span data-stu-id="2f37f-149">A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span> <span data-ttu-id="2f37f-150">Ele também pode ser usado para classificar qualquer tipo de conteúdo em categorias.</span><span class="sxs-lookup"><span data-stu-id="2f37f-150">It can also be used to sort any type of content into categories.</span></span> <span data-ttu-id="2f37f-151">Você pode editar e mover os cartões entre colunas.</span><span class="sxs-lookup"><span data-stu-id="2f37f-151">You can edit and move the cards between columns.</span></span>

:::image type="content" source="../../assets/images/ui-templates/task-board.png" alt-text="O exemplo mostra um modelo de interface do usuário do quadro de tarefas." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="2f37f-153">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="2f37f-153">Top use cases</span></span>

* <span data-ttu-id="2f37f-154">Gerenciamento de projetos.</span><span class="sxs-lookup"><span data-stu-id="2f37f-154">Project management.</span></span> <span data-ttu-id="2f37f-155">Atribuindo tarefas e status de controle</span><span class="sxs-lookup"><span data-stu-id="2f37f-155">Assigning tasks and tracking status</span></span>
* <span data-ttu-id="2f37f-156">Brainstorming.</span><span class="sxs-lookup"><span data-stu-id="2f37f-156">Brainstorming.</span></span> <span data-ttu-id="2f37f-157">Adicionando ideias em categorias diferentes</span><span class="sxs-lookup"><span data-stu-id="2f37f-157">Adding ideas in different categories</span></span>
* <span data-ttu-id="2f37f-158">Classificar exercícios.</span><span class="sxs-lookup"><span data-stu-id="2f37f-158">Sorting exercises.</span></span> <span data-ttu-id="2f37f-159">Organizando qualquer tipo de informação em buckets</span><span class="sxs-lookup"><span data-stu-id="2f37f-159">Organizing any kind of information into buckets</span></span>

## <a name="data-visualization"></a><span data-ttu-id="2f37f-160">Visualização de dados</span><span class="sxs-lookup"><span data-stu-id="2f37f-160">Data visualization</span></span>

<span data-ttu-id="2f37f-161">Você pode usar tamanhos de cartão diferentes (único, duplo e completo) para empilhar e organizar visualizações de dados na mesma página.</span><span class="sxs-lookup"><span data-stu-id="2f37f-161">You can use different card sizes (single, double, and full) to stack and organize data visualizations on the same page.</span></span> <span data-ttu-id="2f37f-162">Os cartões são dimensionados para caber no layout de coluna e preencher espaços em branco.</span><span class="sxs-lookup"><span data-stu-id="2f37f-162">The cards scale to fit the column layout and fill in blank spaces.</span></span>

:::image type="content" source="../../assets/images/ui-templates/data-viz.png" alt-text="Exemplo mostra um modelo de interface do usuário de visualização de dados." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="2f37f-164">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="2f37f-164">Top use cases</span></span>

* <span data-ttu-id="2f37f-165">Exibir informações complexas</span><span class="sxs-lookup"><span data-stu-id="2f37f-165">Display complex information</span></span>
* <span data-ttu-id="2f37f-166">Criar um painel</span><span class="sxs-lookup"><span data-stu-id="2f37f-166">Create a dashboard</span></span>

## <a name="wizard"></a><span data-ttu-id="2f37f-167">Assistente</span><span class="sxs-lookup"><span data-stu-id="2f37f-167">Wizard</span></span>

<span data-ttu-id="2f37f-168">Um assistente orienta um usuário em várias telas para concluir uma tarefa (como um processo de configuração).</span><span class="sxs-lookup"><span data-stu-id="2f37f-168">A wizard guides a user through several screens to complete a task (such as a setup process).</span></span>

:::image type="content" source="../../assets/images/ui-templates/wizard.png" alt-text="O exemplo mostra um modelo de interface do usuário do assistente." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="2f37f-170">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="2f37f-170">Top use cases</span></span>

* <span data-ttu-id="2f37f-171">Configurar</span><span class="sxs-lookup"><span data-stu-id="2f37f-171">Setup</span></span>
* <span data-ttu-id="2f37f-172">Integração</span><span class="sxs-lookup"><span data-stu-id="2f37f-172">Onboarding</span></span>
* <span data-ttu-id="2f37f-173">Experiências de primeira vez</span><span class="sxs-lookup"><span data-stu-id="2f37f-173">First-run experiences</span></span>

## <a name="empty-state"></a><span data-ttu-id="2f37f-174">Estado vazio</span><span class="sxs-lookup"><span data-stu-id="2f37f-174">Empty state</span></span>

<span data-ttu-id="2f37f-175">O modelo de estado vazio pode ser usado para muitos cenários, incluindo entrar, experiências de primeira executar, mensagens de erro e muito mais.</span><span class="sxs-lookup"><span data-stu-id="2f37f-175">The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span> <span data-ttu-id="2f37f-176">É altamente flexível : adapte-o para usar um, alguns ou todos os componentes no design a seguir.</span><span class="sxs-lookup"><span data-stu-id="2f37f-176">It’s highly flexible⁠—adapt it to use one, a few, or all of the components in the following design.</span></span>

:::image type="content" source="../../assets/images/ui-templates/empty-state.png" alt-text="O exemplo mostra um modelo de interface do usuário de estado vazio." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="2f37f-178">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="2f37f-178">Top use cases</span></span>

* <span data-ttu-id="2f37f-179">Entrar</span><span class="sxs-lookup"><span data-stu-id="2f37f-179">Sign in</span></span>
* <span data-ttu-id="2f37f-180">Mensagens de boas-vindas e experiências de primeira vez</span><span class="sxs-lookup"><span data-stu-id="2f37f-180">Welcome messages and first-run experiences</span></span>
* <span data-ttu-id="2f37f-181">Mensagens de sucesso</span><span class="sxs-lookup"><span data-stu-id="2f37f-181">Success messages</span></span>
* <span data-ttu-id="2f37f-182">Mensagens de erro</span><span class="sxs-lookup"><span data-stu-id="2f37f-182">Error messages</span></span>

## <a name="notification-bar"></a><span data-ttu-id="2f37f-183">Notification bar</span><span class="sxs-lookup"><span data-stu-id="2f37f-183">Notification bar</span></span>

<span data-ttu-id="2f37f-184">Uma barra de notificação é uma área dedicada para exibir mensagens breves e importantes que não exigem que o usuário tome medidas imediatas.</span><span class="sxs-lookup"><span data-stu-id="2f37f-184">A notification bar is a dedicated area for displaying a brief, important messages that do not require the user to take immediate action.</span></span> <span data-ttu-id="2f37f-185">Cores de plano de fundo e ícones específicos estão associados a tipos específicos de mensagens (veja abaixo).</span><span class="sxs-lookup"><span data-stu-id="2f37f-185">Specific background colors and icons are associated with specific types of messages (see below).</span></span>

:::image type="content" source="../../assets/images/ui-templates/notification-bar.png" alt-text="Exemplo mostra modelos de barra de notificação." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="2f37f-187">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="2f37f-187">Top use cases</span></span>

* <span data-ttu-id="2f37f-188">Mensagens críticas, erros e avisos</span><span class="sxs-lookup"><span data-stu-id="2f37f-188">Critical messages, errors, and warnings</span></span>
* <span data-ttu-id="2f37f-189">Mensagens de sucesso</span><span class="sxs-lookup"><span data-stu-id="2f37f-189">Success messages</span></span>
* <span data-ttu-id="2f37f-190">Mensagens informativas ou promocionais</span><span class="sxs-lookup"><span data-stu-id="2f37f-190">Informational or promotional messages</span></span>

## <a name="left-nav"></a><span data-ttu-id="2f37f-191">Nav à esquerda</span><span class="sxs-lookup"><span data-stu-id="2f37f-191">Left nav</span></span>

<span data-ttu-id="2f37f-192">Use a navegação à esquerda para navegar em várias páginas na guia do Teams. No exemplo a seguir, a navegação à esquerda fica entre a lista de canais e o conteúdo da guia.</span><span class="sxs-lookup"><span data-stu-id="2f37f-192">Use the left nav to browse multiple pages within your Teams tab. In the following example, the left nav is between the channel list and tab content.</span></span>

:::image type="content" source="../../assets/images/ui-templates/left-nav.png" alt-text="O exemplo mostra um modelo de nav à esquerda." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="2f37f-194">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="2f37f-194">Top use cases</span></span>

* <span data-ttu-id="2f37f-195">Procurar várias páginas em uma guia do Teams</span><span class="sxs-lookup"><span data-stu-id="2f37f-195">Browse multiple pages within a Teams tab</span></span>
* <span data-ttu-id="2f37f-196">Separar aplicativos complexos em várias páginas</span><span class="sxs-lookup"><span data-stu-id="2f37f-196">Break down complex apps into multiple pages</span></span>

## <a name="breadcrumb"></a><span data-ttu-id="2f37f-197">Navegação estrutural</span><span class="sxs-lookup"><span data-stu-id="2f37f-197">Breadcrumb</span></span>

<span data-ttu-id="2f37f-198">As navegação são um auxílio de navegação que transmite a hierarquia do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2f37f-198">Breadcrumbs are a navigational aid that convey your app’s hierarchy.</span></span> <span data-ttu-id="2f37f-199">Eles ajudam os usuários a entender como a página que estão exibindo se encaixa na experiência geral e têm acesso de um clique para níveis mais altos nessa hierarquia.</span><span class="sxs-lookup"><span data-stu-id="2f37f-199">They help users understand how the page they’re viewing fits into the overall experience and afford one-click access to higher levels in that hierarchy.</span></span>

:::image type="content" source="../../assets/images/ui-templates/breadcrumb.png" alt-text="O exemplo mostra um modelo de breadcrumb." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="2f37f-201">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="2f37f-201">Top use cases</span></span>

* <span data-ttu-id="2f37f-202">Comunicar hierarquia</span><span class="sxs-lookup"><span data-stu-id="2f37f-202">Communicate hierarchy</span></span>
* <span data-ttu-id="2f37f-203">Navegação</span><span class="sxs-lookup"><span data-stu-id="2f37f-203">Navigation</span></span>

## <a name="toolbar"></a><span data-ttu-id="2f37f-204">Barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="2f37f-204">Toolbar</span></span>

<span data-ttu-id="2f37f-205">Uma barra de ferramentas é um contêiner para agrupar um conjunto de controles.</span><span class="sxs-lookup"><span data-stu-id="2f37f-205">A toolbar is a container for grouping a set of controls.</span></span>

:::image type="content" source="../../assets/images/ui-templates/toolbar.png" alt-text="O exemplo mostra um modelo de barra de ferramentas." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="2f37f-207">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="2f37f-207">Top use cases</span></span>

* <span data-ttu-id="2f37f-208">Ações contextuais no conteúdo do aplicativo</span><span class="sxs-lookup"><span data-stu-id="2f37f-208">Contextual actions on app content</span></span>
* <span data-ttu-id="2f37f-209">Filtro contextual e encontrar</span><span class="sxs-lookup"><span data-stu-id="2f37f-209">Contextual filter and find</span></span>
* <span data-ttu-id="2f37f-210">Navegação e navegação</span><span class="sxs-lookup"><span data-stu-id="2f37f-210">Navigation and breadcrumbs</span></span>

## <a name="stage"></a><span data-ttu-id="2f37f-211">Etapa</span><span class="sxs-lookup"><span data-stu-id="2f37f-211">Stage</span></span>

<span data-ttu-id="2f37f-212">O estágio oferece uma maneira para os usuários abrirem uma entidade, como uma imagem, arquivo ou site, no Teams, em vez de abri-la em outro aplicativo ou navegador.</span><span class="sxs-lookup"><span data-stu-id="2f37f-212">Stage offers a way for users to open an entity—like an image, file, or website—in Teams instead of opening it in another app or browser.</span></span> <span data-ttu-id="2f37f-213">O principal caso de uso do estágio é exibição; a superfície não deve ser usada para interações complexas.</span><span class="sxs-lookup"><span data-stu-id="2f37f-213">The primary use case of stage is viewing; the surface should not be used for complex interactions.</span></span>

<span data-ttu-id="2f37f-214">(Observação de implementação: crie seu estágio usando um módulo [de tarefa grande.)](../../task-modules-and-cards/task-modules/design-teams-task-modules.md)</span><span class="sxs-lookup"><span data-stu-id="2f37f-214">(Implementation note: Build your stage using a large [task module](../../task-modules-and-cards/task-modules/design-teams-task-modules.md).)</span></span>

:::image type="content" source="../../assets/images/ui-templates/stage.png" alt-text="O exemplo mostra um modelo de estágio." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="2f37f-216">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="2f37f-216">Top use cases</span></span>

* <span data-ttu-id="2f37f-217">Abrir uma entidade no Teams em vez de outro aplicativo ou navegador</span><span class="sxs-lookup"><span data-stu-id="2f37f-217">Open an entity in Teams instead of another app or browser</span></span>
* <span data-ttu-id="2f37f-218">Mídia de destaque ou outro conteúdo</span><span class="sxs-lookup"><span data-stu-id="2f37f-218">Spotlight media or other content</span></span>
