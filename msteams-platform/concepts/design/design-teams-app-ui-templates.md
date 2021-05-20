---
title: Projetando seu aplicativo com modelos de interface do usuário
author: heath-hamilton
description: Projete seu aplicativo mais rapidamente com componentes de Interface do Usuário padronizados, layouts e padrões comumente vistos em Microsoft Teams.
ms.author: lajanuar
localization_priority: Normal
ms.topic: reference
ms.openlocfilehash: 0cd5c6c4525e340f9aa53a78749211783880225a
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566016"
---
# <a name="designing-your-microsoft-teams-app-with-ui-templates"></a><span data-ttu-id="16711-103">Projetando seu aplicativo de Microsoft Teams com modelos de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="16711-103">Designing your Microsoft Teams app with UI templates</span></span>

<span data-ttu-id="16711-104">Projete seu aplicativo Microsoft Teams mais rápido com modelos de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="16711-104">Design your Microsoft Teams app faster with UI templates.</span></span> <span data-ttu-id="16711-105">Os modelos são uma coleção de componentes baseados em Interface do Usuário Fluentes que funcionam em casos comuns de uso Teams, dando-lhe mais tempo para descobrir a melhor experiência para seus usuários.</span><span class="sxs-lookup"><span data-stu-id="16711-105">The templates are a collection of Fluent UI-based components that work across common Teams use cases, giving you more time to figure out the best experience for your users.</span></span>

## <a name="getting-started-with-tools-and-samples"></a><span data-ttu-id="16711-106">Começando com ferramentas e amostras</span><span class="sxs-lookup"><span data-stu-id="16711-106">Getting started with tools and samples</span></span>

<span data-ttu-id="16711-107">Os seguintes recursos podem ajudá-lo a projetar e desenvolver seu aplicativo usando modelos de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="16711-107">The following resources can help you design and develop your app using UI templates.</span></span>

### <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="16711-108">Kit de Interface do Usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="16711-108">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="16711-109">Pegue modelos de interface do usuário para o design do seu aplicativo a partir do Microsoft Teams UI Kit, que também inclui informações extensas sobre uso, anatomia, acessibilidade e práticas recomendadas.</span><span class="sxs-lookup"><span data-stu-id="16711-109">Grab UI templates for your app design from the Microsoft Teams UI Kit, which also includes extensive information about usage, anatomy, accessibility, and best practices.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="16711-110">Obter o kit de interface do usuário (Figma)</span><span class="sxs-lookup"><span data-stu-id="16711-110">Get the UI kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

### <a name="microsoft-teams-ui-library"></a><span data-ttu-id="16711-111">Microsoft Teams Biblioteca de Interface do Usuário</span><span class="sxs-lookup"><span data-stu-id="16711-111">Microsoft Teams UI Library</span></span>

<span data-ttu-id="16711-112">Exibir e testar modelos de interface do usuário individuais Teams e componentes relacionados no seu navegador.</span><span class="sxs-lookup"><span data-stu-id="16711-112">View and test individual Teams UI templates and related components in your browser.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="16711-113">Experimente a biblioteca de interface do usuário (playground)</span><span class="sxs-lookup"><span data-stu-id="16711-113">Try the UI library (playground)</span></span>](https://dev-int.teams.microsoft.com/storybook/main/index.html)

<span data-ttu-id="16711-114">Importe esses modelos e componentes relacionados diretamente no seu projeto de aplicativo Teams.</span><span class="sxs-lookup"><span data-stu-id="16711-114">Import these templates and related components directly into your Teams app project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="16711-115">Obtenha a biblioteca de interface do usuário (GitHub)</span><span class="sxs-lookup"><span data-stu-id="16711-115">Get the UI library (GitHub)</span></span>](https://github.com/OfficeDev/microsoft-teams-ui-component-library)

### <a name="sample-app"></a><span data-ttu-id="16711-116">Aplicativo de amostra</span><span class="sxs-lookup"><span data-stu-id="16711-116">Sample app</span></span>

<span data-ttu-id="16711-117">Instale um aplicativo de exemplo para ver como os modelos de interface do usuário parecem e se comportam dentro de Teams contextos.</span><span class="sxs-lookup"><span data-stu-id="16711-117">Install a sample app to see how UI templates look and behave within Teams contexts.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="16711-118">Obtenha o aplicativo de amostra (GitHub)</span><span class="sxs-lookup"><span data-stu-id="16711-118">Get the sample app (GitHub)</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-ui-templates/ts)

## <a name="list"></a><span data-ttu-id="16711-119">List</span><span class="sxs-lookup"><span data-stu-id="16711-119">List</span></span>

<span data-ttu-id="16711-120">Você pode usar uma lista para exibir itens relacionados em um formato digitalizável e permitir que os usuários tomem ações em uma lista inteira ou itens individuais.</span><span class="sxs-lookup"><span data-stu-id="16711-120">You can use a list to display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>

:::image type="content" source="../../assets/images/ui-templates/list.png" alt-text="O exemplo mostra um modelo de interface do usuário da lista." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="16711-122">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="16711-122">Top use cases</span></span>

* <span data-ttu-id="16711-123">Exibir dados</span><span class="sxs-lookup"><span data-stu-id="16711-123">Display data</span></span>
* <span data-ttu-id="16711-124">Ações contextuais sobre conteúdo de aplicativos</span><span class="sxs-lookup"><span data-stu-id="16711-124">Contextual actions on app content</span></span>

## <a name="dashboard"></a><span data-ttu-id="16711-125">Painel</span><span class="sxs-lookup"><span data-stu-id="16711-125">Dashboard</span></span>

<span data-ttu-id="16711-126">Um painel exibe diferentes tipos de conteúdo em um local central (Teams aplicativo ou guia pessoal).</span><span class="sxs-lookup"><span data-stu-id="16711-126">A dashboard displays different types of content in a central location (Teams personal app or tab).</span></span> <span data-ttu-id="16711-127">Os usuários devem ser capazes de personalizar pelo menos um pouco do que vêem em um painel.</span><span class="sxs-lookup"><span data-stu-id="16711-127">Users should be able to customize at least some of what they see on a dashboard.</span></span>

:::image type="content" source="../../assets/images/ui-templates/dashboard.png" alt-text="O exemplo mostra um modelo de interface do usuário do painel." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="16711-129">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="16711-129">Top use cases</span></span>

* <span data-ttu-id="16711-130">Analisar dados</span><span class="sxs-lookup"><span data-stu-id="16711-130">Analyze data</span></span>
* <span data-ttu-id="16711-131">Métricas de relatório</span><span class="sxs-lookup"><span data-stu-id="16711-131">Report metrics</span></span>
* <span data-ttu-id="16711-132">Organize diferentes informações em um só lugar</span><span class="sxs-lookup"><span data-stu-id="16711-132">Organize different information in one place</span></span>

## <a name="form"></a><span data-ttu-id="16711-133">Formulário</span><span class="sxs-lookup"><span data-stu-id="16711-133">Form</span></span>

<span data-ttu-id="16711-134">Os formulários são usados para coletar, validar e enviar a entrada do usuário de forma estruturada.</span><span class="sxs-lookup"><span data-stu-id="16711-134">Forms are used to collect, validate, and submit user input in a structured way.</span></span> <span data-ttu-id="16711-135">Rotulagem clara e agrupamentos lógicos de campos de entrada são fundamentais para uma boa experiência do usuário.</span><span class="sxs-lookup"><span data-stu-id="16711-135">Clear labeling and logical groupings of input fields are critical for a good user experience.</span></span>

:::image type="content" source="../../assets/images/ui-templates/form.png" alt-text="O exemplo mostra um modelo de interface do usuário de formulário." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="16711-137">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="16711-137">Top use cases</span></span>

* <span data-ttu-id="16711-138">Entrar</span><span class="sxs-lookup"><span data-stu-id="16711-138">Sign in</span></span>
* <span data-ttu-id="16711-139">Perfis de usuário</span><span class="sxs-lookup"><span data-stu-id="16711-139">User profiles</span></span>
* <span data-ttu-id="16711-140">Configurações</span><span class="sxs-lookup"><span data-stu-id="16711-140">Settings</span></span>
* <span data-ttu-id="16711-141">Coleta de entrada do usuário</span><span class="sxs-lookup"><span data-stu-id="16711-141">User input collection</span></span>

## <a name="sign-in"></a><span data-ttu-id="16711-142">Entrar</span><span class="sxs-lookup"><span data-stu-id="16711-142">Sign in</span></span>

<span data-ttu-id="16711-143">Você pode projetar fluxos de login de aplicativos para diferentes Teams contextos e provedores de identidade.</span><span class="sxs-lookup"><span data-stu-id="16711-143">You can design app sign-in flows for different Teams contexts and identity providers.</span></span> <span data-ttu-id="16711-144">O exemplo a seguir inclui o single sign-on (SSO), que recomendamos para a experiência de autenticação mais simples.</span><span class="sxs-lookup"><span data-stu-id="16711-144">The following example includes single sign-on (SSO), which we recommend for the simplest authentication experience.</span></span>

:::image type="content" source="../../assets/images/ui-templates/sign-in.png" alt-text="O exemplo mostra um sinal no modelo de interface do usuário." border="false":::

### <a name="top-use-case"></a><span data-ttu-id="16711-146">Caso de uso superior</span><span class="sxs-lookup"><span data-stu-id="16711-146">Top use case</span></span>

* <span data-ttu-id="16711-147">Autenticar usuários</span><span class="sxs-lookup"><span data-stu-id="16711-147">Authenticate users</span></span>

## <a name="task-board"></a><span data-ttu-id="16711-148">Quadro de tarefas</span><span class="sxs-lookup"><span data-stu-id="16711-148">Task board</span></span>

<span data-ttu-id="16711-149">Um quadro de tarefas, às vezes chamado de placa kanban ou pistas de natação, é uma coleção de cartões frequentemente usados para rastrear o status de itens de trabalho ou bilhetes.</span><span class="sxs-lookup"><span data-stu-id="16711-149">A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span> <span data-ttu-id="16711-150">Ele também pode ser usado para classificar qualquer tipo de conteúdo em categorias.</span><span class="sxs-lookup"><span data-stu-id="16711-150">It can also be used to sort any type of content into categories.</span></span> <span data-ttu-id="16711-151">Você pode editar e mover as cartas entre as colunas.</span><span class="sxs-lookup"><span data-stu-id="16711-151">You can edit and move the cards between columns.</span></span>

:::image type="content" source="../../assets/images/ui-templates/task-board.png" alt-text="O exemplo mostra um modelo de interface do usuário da placa de tarefas." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="16711-153">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="16711-153">Top use cases</span></span>

* <span data-ttu-id="16711-154">gerenciamento de Project: Atribuindo tarefas e status de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="16711-154">Project management: Assigning tasks and tracking status.</span></span>
* <span data-ttu-id="16711-155">Brainstorming: Adicionando ideias em diferentes categorias.</span><span class="sxs-lookup"><span data-stu-id="16711-155">Brainstorming: Adding ideas in different categories.</span></span>
* <span data-ttu-id="16711-156">Exercícios de triagem: Organizando qualquer tipo de informação em baldes.</span><span class="sxs-lookup"><span data-stu-id="16711-156">Sorting exercises: Organizing any kind of information into buckets.</span></span>

## <a name="data-visualization"></a><span data-ttu-id="16711-157">Visualização de dados</span><span class="sxs-lookup"><span data-stu-id="16711-157">Data visualization</span></span>

<span data-ttu-id="16711-158">Você pode usar diferentes tamanhos de cartão (simples, duplo e completo) para empilhar e organizar visualizações de dados na mesma página.</span><span class="sxs-lookup"><span data-stu-id="16711-158">You can use different card sizes (single, double, and full) to stack and organize data visualizations on the same page.</span></span> <span data-ttu-id="16711-159">A escala de cartões para se encaixar no layout da coluna e preencher espaços em branco.</span><span class="sxs-lookup"><span data-stu-id="16711-159">The cards scale to fit the column layout and fill in blank spaces.</span></span>

:::image type="content" source="../../assets/images/ui-templates/data-viz.png" alt-text="O exemplo mostra um modelo de interface do usuário de visualização de dados." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="16711-161">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="16711-161">Top use cases</span></span>

* <span data-ttu-id="16711-162">Exibir informações complexas</span><span class="sxs-lookup"><span data-stu-id="16711-162">Display complex information</span></span>
* <span data-ttu-id="16711-163">Crie um painel de instrumentos</span><span class="sxs-lookup"><span data-stu-id="16711-163">Create a dashboard</span></span>

## <a name="wizard"></a><span data-ttu-id="16711-164">Assistente</span><span class="sxs-lookup"><span data-stu-id="16711-164">Wizard</span></span>

<span data-ttu-id="16711-165">Um assistente guia um usuário através de várias telas para completar uma tarefa (como um processo de configuração).</span><span class="sxs-lookup"><span data-stu-id="16711-165">A wizard guides a user through several screens to complete a task (such as a setup process).</span></span>

:::image type="content" source="../../assets/images/ui-templates/wizard.png" alt-text="O exemplo mostra um modelo de interface do usuário do assistente." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="16711-167">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="16711-167">Top use cases</span></span>

* <span data-ttu-id="16711-168">Configurar</span><span class="sxs-lookup"><span data-stu-id="16711-168">Setup</span></span>
* <span data-ttu-id="16711-169">Integração</span><span class="sxs-lookup"><span data-stu-id="16711-169">Onboarding</span></span>
* <span data-ttu-id="16711-170">Experiências de primeira viagem</span><span class="sxs-lookup"><span data-stu-id="16711-170">First-run experiences</span></span>

## <a name="empty-state"></a><span data-ttu-id="16711-171">Estado vazio</span><span class="sxs-lookup"><span data-stu-id="16711-171">Empty state</span></span>

<span data-ttu-id="16711-172">O modelo de estado vazio pode ser usado para muitos cenários, incluindo login, experiências de primeira execução, mensagens de erro e muito mais.</span><span class="sxs-lookup"><span data-stu-id="16711-172">The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span> <span data-ttu-id="16711-173">É altamente flexível — adaptá-lo para usar um, alguns ou todos os componentes no design a seguir.</span><span class="sxs-lookup"><span data-stu-id="16711-173">It’s highly flexible⁠—adapt it to use one, a few, or all of the components in the following design.</span></span>

:::image type="content" source="../../assets/images/ui-templates/empty-state.png" alt-text="O exemplo mostra um modelo de interface do usuário de estado vazio." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="16711-175">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="16711-175">Top use cases</span></span>

* <span data-ttu-id="16711-176">Entrar</span><span class="sxs-lookup"><span data-stu-id="16711-176">Sign in</span></span>
* <span data-ttu-id="16711-177">Mensagens de boas-vindas e experiências de primeira viagem</span><span class="sxs-lookup"><span data-stu-id="16711-177">Welcome messages and first-run experiences</span></span>
* <span data-ttu-id="16711-178">Mensagens de sucesso</span><span class="sxs-lookup"><span data-stu-id="16711-178">Success messages</span></span>
* <span data-ttu-id="16711-179">Mensagens de erro</span><span class="sxs-lookup"><span data-stu-id="16711-179">Error messages</span></span>

## <a name="notification-bar"></a><span data-ttu-id="16711-180">Notification bar</span><span class="sxs-lookup"><span data-stu-id="16711-180">Notification bar</span></span>

<span data-ttu-id="16711-181">Uma barra de notificação é uma área dedicada para exibir uma mensagem breve e importante que não exige que o usuário tome medidas imediatas.</span><span class="sxs-lookup"><span data-stu-id="16711-181">A notification bar is a dedicated area for displaying a brief, important messages that do not require the user to take immediate action.</span></span> <span data-ttu-id="16711-182">Cores e ícones de fundo específicos estão associados a tipos específicos de mensagens (veja abaixo).</span><span class="sxs-lookup"><span data-stu-id="16711-182">Specific background colors and icons are associated with specific types of messages (see below).</span></span>

:::image type="content" source="../../assets/images/ui-templates/notification-bar.png" alt-text="O exemplo mostra modelos de barras de notificação." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="16711-184">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="16711-184">Top use cases</span></span>

* <span data-ttu-id="16711-185">Mensagens críticas, erros e avisos</span><span class="sxs-lookup"><span data-stu-id="16711-185">Critical messages, errors, and warnings</span></span>
* <span data-ttu-id="16711-186">Mensagens de sucesso</span><span class="sxs-lookup"><span data-stu-id="16711-186">Success messages</span></span>
* <span data-ttu-id="16711-187">Mensagens informacionais ou promocionais</span><span class="sxs-lookup"><span data-stu-id="16711-187">Informational or promotional messages</span></span>

## <a name="left-nav"></a><span data-ttu-id="16711-188">Navegação esquerda</span><span class="sxs-lookup"><span data-stu-id="16711-188">Left nav</span></span>

<span data-ttu-id="16711-189">Use a navegação à esquerda para navegar em várias páginas na guia Teams. No exemplo a seguir, a navegação à esquerda está entre a lista de canais e o conteúdo da guia.</span><span class="sxs-lookup"><span data-stu-id="16711-189">Use the left nav to browse multiple pages within your Teams tab. In the following example, the left nav is between the channel list and tab content.</span></span>

:::image type="content" source="../../assets/images/ui-templates/left-nav.png" alt-text="O exemplo mostra um modelo de navegação à esquerda." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="16711-191">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="16711-191">Top use cases</span></span>

* <span data-ttu-id="16711-192">Navegue por várias páginas em uma guia Teams.</span><span class="sxs-lookup"><span data-stu-id="16711-192">Browse multiple pages within a Teams tab.</span></span>
* <span data-ttu-id="16711-193">Desbre aplicativos complexos em várias páginas.</span><span class="sxs-lookup"><span data-stu-id="16711-193">Break down complex apps into multiple pages.</span></span>

## <a name="breadcrumb"></a><span data-ttu-id="16711-194">Trilha</span><span class="sxs-lookup"><span data-stu-id="16711-194">Breadcrumb</span></span>

<span data-ttu-id="16711-195">Migalhas de pão são um auxílio de navegação que transmite a hierarquia do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="16711-195">Breadcrumbs are a navigational aid that convey your app’s hierarchy.</span></span> <span data-ttu-id="16711-196">Eles ajudam os usuários a entender como a página que estão visualizando se encaixa na experiência geral e oferecem acesso de um clique a níveis mais altos nessa hierarquia.</span><span class="sxs-lookup"><span data-stu-id="16711-196">They help users understand how the page they’re viewing fits into the overall experience and afford one-click access to higher levels in that hierarchy.</span></span>

:::image type="content" source="../../assets/images/ui-templates/breadcrumb.png" alt-text="O exemplo mostra um modelo de migalhas de pão." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="16711-198">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="16711-198">Top use cases</span></span>

* <span data-ttu-id="16711-199">Comunicar hierarquia</span><span class="sxs-lookup"><span data-stu-id="16711-199">Communicate hierarchy</span></span>
* <span data-ttu-id="16711-200">Navegação</span><span class="sxs-lookup"><span data-stu-id="16711-200">Navigation</span></span>

## <a name="toolbar"></a><span data-ttu-id="16711-201">Barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="16711-201">Toolbar</span></span>

<span data-ttu-id="16711-202">Uma barra de ferramentas é um recipiente para agrupar um conjunto de controles.</span><span class="sxs-lookup"><span data-stu-id="16711-202">A toolbar is a container for grouping a set of controls.</span></span>

:::image type="content" source="../../assets/images/ui-templates/toolbar.png" alt-text="O exemplo mostra um modelo de barra de ferramentas." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="16711-204">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="16711-204">Top use cases</span></span>

* <span data-ttu-id="16711-205">Ações contextuais sobre conteúdo de aplicativos</span><span class="sxs-lookup"><span data-stu-id="16711-205">Contextual actions on app content</span></span>
* <span data-ttu-id="16711-206">Filtro contextual e encontrar</span><span class="sxs-lookup"><span data-stu-id="16711-206">Contextual filter and find</span></span>
* <span data-ttu-id="16711-207">Navegação e migalhas de pão</span><span class="sxs-lookup"><span data-stu-id="16711-207">Navigation and breadcrumbs</span></span>

## <a name="stage"></a><span data-ttu-id="16711-208">Estágio</span><span class="sxs-lookup"><span data-stu-id="16711-208">Stage</span></span>

<span data-ttu-id="16711-209">O Stage oferece uma maneira de os usuários abrirem uma entidade — como uma imagem, arquivo ou site — em Teams em vez de abri-la em outro aplicativo ou navegador.</span><span class="sxs-lookup"><span data-stu-id="16711-209">Stage offers a way for users to open an entity—like an image, file, or website—in Teams instead of opening it in another app or browser.</span></span> <span data-ttu-id="16711-210">O principal caso de uso do estágio é a visualização; a superfície não deve ser usada para interações complexas.</span><span class="sxs-lookup"><span data-stu-id="16711-210">The primary use case of stage is viewing; the surface should not be used for complex interactions.</span></span>

<span data-ttu-id="16711-211">(Nota de implementação: Construa seu estágio usando um grande [módulo de tarefa](../../task-modules-and-cards/task-modules/design-teams-task-modules.md).)</span><span class="sxs-lookup"><span data-stu-id="16711-211">(Implementation note: Build your stage using a large [task module](../../task-modules-and-cards/task-modules/design-teams-task-modules.md).)</span></span>

:::image type="content" source="../../assets/images/ui-templates/stage.png" alt-text="O exemplo mostra um modelo de palco." border="false":::

### <a name="top-use-cases"></a><span data-ttu-id="16711-213">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="16711-213">Top use cases</span></span>

* <span data-ttu-id="16711-214">Abra uma entidade em Teams em vez de outro aplicativo ou navegador.</span><span class="sxs-lookup"><span data-stu-id="16711-214">Open an entity in Teams instead of another app or browser.</span></span>
* <span data-ttu-id="16711-215">Mídia de holofotes ou outros conteúdos.</span><span class="sxs-lookup"><span data-stu-id="16711-215">Spotlight media or other content.</span></span>
