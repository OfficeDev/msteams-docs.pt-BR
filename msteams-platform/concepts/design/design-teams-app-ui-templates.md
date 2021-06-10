---
title: Projetando seu aplicativo com modelos de interface do usuário
author: heath-hamilton
description: Projete seu aplicativo mais rapidamente com componentes de interface do usuário padronizados, layouts e padrões comumente vistos em Microsoft Teams.
ms.author: lajanuar
localization_priority: Normal
ms.topic: reference
ms.openlocfilehash: 5026554070396dcc55390496b6754961e8e037bc
ms.sourcegitcommit: 4224c44d169b1a289cbf1d3353de6bc6de7c7ea8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2021
ms.locfileid: "52644790"
---
# <a name="designing-your-microsoft-teams-app-with-ui-templates"></a><span data-ttu-id="a09a2-103">Projetando seu aplicativo Microsoft Teams com modelos de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="a09a2-103">Designing your Microsoft Teams app with UI templates</span></span>

<span data-ttu-id="a09a2-104">Projete seu Microsoft Teams aplicativo mais rápido com modelos de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="a09a2-104">Design your Microsoft Teams app faster with UI templates.</span></span> <span data-ttu-id="a09a2-105">Os modelos são uma coleção de componentes baseados na interface do usuário fluente que funcionam em casos comuns Teams uso, dando mais tempo para descobrir a melhor experiência para seus usuários.</span><span class="sxs-lookup"><span data-stu-id="a09a2-105">The templates are a collection of Fluent UI-based components that work across common Teams use cases, giving you more time to figure out the best experience for your users.</span></span>

## <a name="getting-started-with-tools-and-samples"></a><span data-ttu-id="a09a2-106">Iniciando com ferramentas e exemplos</span><span class="sxs-lookup"><span data-stu-id="a09a2-106">Getting started with tools and samples</span></span>

<span data-ttu-id="a09a2-107">Os recursos a seguir podem ajudá-lo a projetar e desenvolver seu aplicativo usando modelos de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="a09a2-107">The following resources can help you design and develop your app using UI templates.</span></span>

### <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="a09a2-108">Kit de Interface do Usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="a09a2-108">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="a09a2-109">Pegue modelos de interface do usuário para seu design de aplicativo no kit de interface do usuário Microsoft Teams, que também inclui informações abrangentes sobre uso, anatomia, acessibilidade e práticas recomendadas.</span><span class="sxs-lookup"><span data-stu-id="a09a2-109">Grab UI templates for your app design from the Microsoft Teams UI Kit, which also includes extensive information about usage, anatomy, accessibility, and best practices.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a09a2-110">Obter o kit de interface do usuário (Figma)</span><span class="sxs-lookup"><span data-stu-id="a09a2-110">Get the UI kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

### <a name="microsoft-teams-ui-library"></a><span data-ttu-id="a09a2-111">Microsoft Teams Biblioteca da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="a09a2-111">Microsoft Teams UI Library</span></span>

<span data-ttu-id="a09a2-112">Exibir e testar modelos Teams de interface do usuário individuais e componentes relacionados no navegador.</span><span class="sxs-lookup"><span data-stu-id="a09a2-112">View and test individual Teams UI templates and related components in your browser.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a09a2-113">Experimente a biblioteca da interface do usuário (playground)</span><span class="sxs-lookup"><span data-stu-id="a09a2-113">Try the UI library (playground)</span></span>](https://dev-int.teams.microsoft.com/storybook/main/index.html)

<span data-ttu-id="a09a2-114">Import these templates and related components directly into your Teams app project.</span><span class="sxs-lookup"><span data-stu-id="a09a2-114">Import these templates and related components directly into your Teams app project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a09a2-115">Obter a biblioteca da interface do usuário (GitHub)</span><span class="sxs-lookup"><span data-stu-id="a09a2-115">Get the UI library (GitHub)</span></span>](https://github.com/OfficeDev/microsoft-teams-ui-component-library)

### <a name="sample-app"></a><span data-ttu-id="a09a2-116">Exemplo de aplicativo</span><span class="sxs-lookup"><span data-stu-id="a09a2-116">Sample app</span></span>

<span data-ttu-id="a09a2-117">Instale um aplicativo de exemplo para ver como os modelos de interface do usuário são e se comportam Teams contextos.</span><span class="sxs-lookup"><span data-stu-id="a09a2-117">Install a sample app to see how UI templates look and behave within Teams contexts.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a09a2-118">Obter o aplicativo de exemplo (GitHub)</span><span class="sxs-lookup"><span data-stu-id="a09a2-118">Get the sample app (GitHub)</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-ui-templates/ts)

## <a name="dashboard"></a><span data-ttu-id="a09a2-119">Painel</span><span class="sxs-lookup"><span data-stu-id="a09a2-119">Dashboard</span></span>

<span data-ttu-id="a09a2-120">Um painel exibe diferentes tipos de conteúdo em um local central (Teams aplicativo pessoal ou guia).</span><span class="sxs-lookup"><span data-stu-id="a09a2-120">A dashboard displays different types of content in a central location (Teams personal app or tab).</span></span> <span data-ttu-id="a09a2-121">Os usuários devem ser capazes de personalizar pelo menos parte do que veem em um painel.</span><span class="sxs-lookup"><span data-stu-id="a09a2-121">Users should be able to customize at least some of what they see on a dashboard.</span></span>

### <a name="top-use-cases"></a><span data-ttu-id="a09a2-122">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="a09a2-122">Top use cases</span></span>

* <span data-ttu-id="a09a2-123">Analisar dados</span><span class="sxs-lookup"><span data-stu-id="a09a2-123">Analyze data</span></span>
* <span data-ttu-id="a09a2-124">Métricas de relatório</span><span class="sxs-lookup"><span data-stu-id="a09a2-124">Report metrics</span></span>
* <span data-ttu-id="a09a2-125">Organizar informações diferentes em um só lugar</span><span class="sxs-lookup"><span data-stu-id="a09a2-125">Organize different information in one place</span></span>

# <a name="desktop"></a>[<span data-ttu-id="a09a2-126">Desktop</span><span class="sxs-lookup"><span data-stu-id="a09a2-126">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/dashboard.png" alt-text="Exemplo mostra um modelo de interface do usuário do painel na área de trabalho." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="a09a2-128">Mobile</span><span class="sxs-lookup"><span data-stu-id="a09a2-128">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-dashboard.png" alt-text="Exemplo mostra um modelo de interface do usuário do painel no celular." border="false":::

---

## <a name="data-visualization"></a><span data-ttu-id="a09a2-130">Visualização de dados</span><span class="sxs-lookup"><span data-stu-id="a09a2-130">Data visualization</span></span>

<span data-ttu-id="a09a2-131">Você pode usar tamanhos de cartão diferentes (único, duplo e completo) para empilhar e organizar visualizações de dados na mesma página.</span><span class="sxs-lookup"><span data-stu-id="a09a2-131">You can use different card sizes (single, double, and full) to stack and organize data visualizations on the same page.</span></span> <span data-ttu-id="a09a2-132">A escala de cartões para ajustar o layout da coluna e preencher espaços em branco.</span><span class="sxs-lookup"><span data-stu-id="a09a2-132">The cards scale to fit the column layout and fill in blank spaces.</span></span>

### <a name="top-use-cases"></a><span data-ttu-id="a09a2-133">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="a09a2-133">Top use cases</span></span>

* <span data-ttu-id="a09a2-134">Exibir informações complexas</span><span class="sxs-lookup"><span data-stu-id="a09a2-134">Display complex information</span></span>
* <span data-ttu-id="a09a2-135">Criar um painel</span><span class="sxs-lookup"><span data-stu-id="a09a2-135">Create a dashboard</span></span>

# <a name="desktop"></a>[<span data-ttu-id="a09a2-136">Desktop</span><span class="sxs-lookup"><span data-stu-id="a09a2-136">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/data-viz.png" alt-text="Exemplo mostra um modelo de interface do usuário de visualização de dados na área de trabalho." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="a09a2-138">Mobile</span><span class="sxs-lookup"><span data-stu-id="a09a2-138">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-data-viz.png" alt-text="Exemplo mostra um modelo de interface do usuário de visualização de dados no celular." border="false":::

---

## <a name="empty-state"></a><span data-ttu-id="a09a2-140">Estado vazio</span><span class="sxs-lookup"><span data-stu-id="a09a2-140">Empty state</span></span>

<span data-ttu-id="a09a2-141">O modelo de estado vazio pode ser usado para muitos cenários, incluindo entrar, experiências de primeira executar, mensagens de erro e muito mais.</span><span class="sxs-lookup"><span data-stu-id="a09a2-141">The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span> <span data-ttu-id="a09a2-142">É altamente flexível, adaptá-lo para usar um, alguns ou todos os componentes no design a seguir.</span><span class="sxs-lookup"><span data-stu-id="a09a2-142">It’s highly flexible⁠—adapt it to use one, a few, or all of the components in the following design.</span></span>

### <a name="top-use-cases"></a><span data-ttu-id="a09a2-143">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="a09a2-143">Top use cases</span></span>

* <span data-ttu-id="a09a2-144">Entrar</span><span class="sxs-lookup"><span data-stu-id="a09a2-144">Sign in</span></span>
* <span data-ttu-id="a09a2-145">Mensagens de boas-vindas e experiências de primeira fase</span><span class="sxs-lookup"><span data-stu-id="a09a2-145">Welcome messages and first-run experiences</span></span>
* <span data-ttu-id="a09a2-146">Mensagens de sucesso</span><span class="sxs-lookup"><span data-stu-id="a09a2-146">Success messages</span></span>
* <span data-ttu-id="a09a2-147">Mensagens de erro</span><span class="sxs-lookup"><span data-stu-id="a09a2-147">Error messages</span></span>

# <a name="desktop"></a>[<span data-ttu-id="a09a2-148">Desktop</span><span class="sxs-lookup"><span data-stu-id="a09a2-148">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/empty-state.png" alt-text="Exemplo mostra um modelo de interface do usuário de estado vazio na área de trabalho." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="a09a2-150">Mobile</span><span class="sxs-lookup"><span data-stu-id="a09a2-150">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-empty-state.png" alt-text="Exemplo mostra um modelo de interface do usuário de estado vazio no celular." border="false":::

---

## <a name="filter"></a><span data-ttu-id="a09a2-152">Filter</span><span class="sxs-lookup"><span data-stu-id="a09a2-152">Filter</span></span>

<span data-ttu-id="a09a2-153">Um filtro permite reduzir as informações que você vê com base nos critérios selecionados.</span><span class="sxs-lookup"><span data-stu-id="a09a2-153">A filter allows you to reduce the information you see based on the criteria selected.</span></span> <span data-ttu-id="a09a2-154">Você pode incluir filtros com tabelas, listas, cartões e outros componentes que organizam o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="a09a2-154">You can include filters with tables, lists, cards, and other components that organize content.</span></span>

### <a name="top-use-cases"></a><span data-ttu-id="a09a2-155">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="a09a2-155">Top use cases</span></span>

<span data-ttu-id="a09a2-156">Organizar conteúdo em:</span><span class="sxs-lookup"><span data-stu-id="a09a2-156">Organizing content in:</span></span>

* <span data-ttu-id="a09a2-157">Listas</span><span class="sxs-lookup"><span data-stu-id="a09a2-157">Lists</span></span>
* <span data-ttu-id="a09a2-158">Tabelas</span><span class="sxs-lookup"><span data-stu-id="a09a2-158">Tables</span></span>
* <span data-ttu-id="a09a2-159">Painéis</span><span class="sxs-lookup"><span data-stu-id="a09a2-159">Dashboards</span></span>
* <span data-ttu-id="a09a2-160">Visualização de dados</span><span class="sxs-lookup"><span data-stu-id="a09a2-160">Data visualization</span></span>

:::image type="content" source="../../assets/images/ui-templates/filter.png" alt-text="Exemplo mostra um modelo de filtro." border="false":::

## <a name="form"></a><span data-ttu-id="a09a2-162">Formulário</span><span class="sxs-lookup"><span data-stu-id="a09a2-162">Form</span></span>

<span data-ttu-id="a09a2-163">Os formulários são usados para coletar, validar e enviar entrada do usuário de forma estruturada.</span><span class="sxs-lookup"><span data-stu-id="a09a2-163">Forms are used to collect, validate, and submit user input in a structured way.</span></span> <span data-ttu-id="a09a2-164">A rotulagem limpa e os agrupamentos lógicos de campos de entrada são essenciais para uma boa experiência do usuário.</span><span class="sxs-lookup"><span data-stu-id="a09a2-164">Clear labeling and logical groupings of input fields are critical for a good user experience.</span></span>

### <a name="top-use-cases"></a><span data-ttu-id="a09a2-165">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="a09a2-165">Top use cases</span></span>

* <span data-ttu-id="a09a2-166">Entrar</span><span class="sxs-lookup"><span data-stu-id="a09a2-166">Sign in</span></span>
* <span data-ttu-id="a09a2-167">Perfis de usuário</span><span class="sxs-lookup"><span data-stu-id="a09a2-167">User profiles</span></span>
* <span data-ttu-id="a09a2-168">Configurações</span><span class="sxs-lookup"><span data-stu-id="a09a2-168">Settings</span></span>
* <span data-ttu-id="a09a2-169">Coleção de entrada do usuário</span><span class="sxs-lookup"><span data-stu-id="a09a2-169">User input collection</span></span>

# <a name="desktop"></a>[<span data-ttu-id="a09a2-170">Desktop</span><span class="sxs-lookup"><span data-stu-id="a09a2-170">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/form.png" alt-text="Exemplo mostra um modelo de interface do usuário de formulário na área de trabalho." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="a09a2-172">Mobile</span><span class="sxs-lookup"><span data-stu-id="a09a2-172">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-form.png" alt-text="Exemplo mostra um modelo de interface do usuário de formulário no celular." border="false":::

---

## <a name="list"></a><span data-ttu-id="a09a2-174">List</span><span class="sxs-lookup"><span data-stu-id="a09a2-174">List</span></span>

<span data-ttu-id="a09a2-175">Você pode usar uma lista para exibir itens relacionados em um formato digitalizável e permitir que os usuários tomem ações em uma lista inteira ou itens individuais.</span><span class="sxs-lookup"><span data-stu-id="a09a2-175">You can use a list to display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>

### <a name="top-use-cases"></a><span data-ttu-id="a09a2-176">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="a09a2-176">Top use cases</span></span>

* <span data-ttu-id="a09a2-177">Exibir dados</span><span class="sxs-lookup"><span data-stu-id="a09a2-177">Display data</span></span>
* <span data-ttu-id="a09a2-178">Ações contextuais no conteúdo do aplicativo</span><span class="sxs-lookup"><span data-stu-id="a09a2-178">Contextual actions on app content</span></span>

# <a name="desktop"></a>[<span data-ttu-id="a09a2-179">Desktop</span><span class="sxs-lookup"><span data-stu-id="a09a2-179">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/list.png" alt-text="Exemplo mostra um modelo de interface do usuário de lista na área de trabalho." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="a09a2-181">Mobile</span><span class="sxs-lookup"><span data-stu-id="a09a2-181">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-list.png" alt-text="Exemplo mostra um modelo de interface do usuário de lista no celular." border="false":::

---

## <a name="sign-in"></a><span data-ttu-id="a09a2-183">Entrar</span><span class="sxs-lookup"><span data-stu-id="a09a2-183">Sign in</span></span>

<span data-ttu-id="a09a2-184">Você pode projetar fluxos de entrada de aplicativos para diferentes Teams contextos e provedores de identidade.</span><span class="sxs-lookup"><span data-stu-id="a09a2-184">You can design app sign-in flows for different Teams contexts and identity providers.</span></span> <span data-ttu-id="a09a2-185">O exemplo a seguir inclui o logom único (SSO), que recomendamos para a experiência de autenticação mais simples.</span><span class="sxs-lookup"><span data-stu-id="a09a2-185">The following example includes single sign-on (SSO), which we recommend for the simplest authentication experience.</span></span>

### <a name="top-use-case"></a><span data-ttu-id="a09a2-186">Caso de uso superior</span><span class="sxs-lookup"><span data-stu-id="a09a2-186">Top use case</span></span>

* <span data-ttu-id="a09a2-187">Autenticar usuários</span><span class="sxs-lookup"><span data-stu-id="a09a2-187">Authenticate users</span></span>

# <a name="desktop"></a>[<span data-ttu-id="a09a2-188">Desktop</span><span class="sxs-lookup"><span data-stu-id="a09a2-188">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/sign-in.png" alt-text="Exemplo mostra um modelo de interface do usuário de login na área de trabalho." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="a09a2-190">Mobile</span><span class="sxs-lookup"><span data-stu-id="a09a2-190">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-sign-in.png" alt-text="Exemplo mostra um modelo de interface do usuário de login no celular." border="false":::

---

## <a name="settings"></a><span data-ttu-id="a09a2-192">Configurações</span><span class="sxs-lookup"><span data-stu-id="a09a2-192">Settings</span></span>

<span data-ttu-id="a09a2-193">Configurações telas são onde os usuários podem configurar suas preferências com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a09a2-193">Settings screens are where users can configure their preferences with your app.</span></span> <span data-ttu-id="a09a2-194">(Observação: Configurações é um contêiner para [componentes básicos da interface do usuário](~/concepts/design/design-teams-app-basic-ui-components.md).)</span><span class="sxs-lookup"><span data-stu-id="a09a2-194">(Note: Settings is a container for [basic UI components](~/concepts/design/design-teams-app-basic-ui-components.md).)</span></span>

### <a name="top-use-case"></a><span data-ttu-id="a09a2-195">Caso de uso superior</span><span class="sxs-lookup"><span data-stu-id="a09a2-195">Top use case</span></span>

* <span data-ttu-id="a09a2-196">Gerenciar recursos do aplicativo</span><span class="sxs-lookup"><span data-stu-id="a09a2-196">Manage app features</span></span>

:::image type="content" source="../../assets/images/ui-templates/settings.png" alt-text="Exemplo mostra um modelo de configurações." border="false":::

## <a name="task-board"></a><span data-ttu-id="a09a2-198">Quadro de Tarefas</span><span class="sxs-lookup"><span data-stu-id="a09a2-198">Task board</span></span>

<span data-ttu-id="a09a2-199">Um quadro de tarefas, às vezes chamado de quadro de kanban ou faixas de nadador, é uma coleção de cartões frequentemente usada para rastrear o status de itens de trabalho ou tíquetes.</span><span class="sxs-lookup"><span data-stu-id="a09a2-199">A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span> <span data-ttu-id="a09a2-200">Ele também pode ser usado para classificar qualquer tipo de conteúdo em categorias.</span><span class="sxs-lookup"><span data-stu-id="a09a2-200">It can also be used to sort any type of content into categories.</span></span> <span data-ttu-id="a09a2-201">Você pode editar e mover os cartões entre colunas.</span><span class="sxs-lookup"><span data-stu-id="a09a2-201">You can edit and move the cards between columns.</span></span>

### <a name="top-use-cases"></a><span data-ttu-id="a09a2-202">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="a09a2-202">Top use cases</span></span>

* <span data-ttu-id="a09a2-203">Gerenciamento de projetos.</span><span class="sxs-lookup"><span data-stu-id="a09a2-203">Project management.</span></span> <span data-ttu-id="a09a2-204">Atribuindo tarefas e status de controle</span><span class="sxs-lookup"><span data-stu-id="a09a2-204">Assigning tasks and tracking status</span></span>
* <span data-ttu-id="a09a2-205">Brainstorming.</span><span class="sxs-lookup"><span data-stu-id="a09a2-205">Brainstorming.</span></span> <span data-ttu-id="a09a2-206">Adicionar ideias em categorias diferentes</span><span class="sxs-lookup"><span data-stu-id="a09a2-206">Adding ideas in different categories</span></span>
* <span data-ttu-id="a09a2-207">Exercícios de classificação.</span><span class="sxs-lookup"><span data-stu-id="a09a2-207">Sorting exercises.</span></span> <span data-ttu-id="a09a2-208">Organizar qualquer tipo de informação em buckets</span><span class="sxs-lookup"><span data-stu-id="a09a2-208">Organizing any kind of information into buckets</span></span>

# <a name="desktop"></a>[<span data-ttu-id="a09a2-209">Desktop</span><span class="sxs-lookup"><span data-stu-id="a09a2-209">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/task-board.png" alt-text="Exemplo mostra um modelo de interface do usuário do quadro de tarefas na área de trabalho." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="a09a2-211">Mobile</span><span class="sxs-lookup"><span data-stu-id="a09a2-211">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-task-board.png" alt-text="Exemplo mostra um modelo de interface do usuário do quadro de tarefas no celular." border="false":::

---

## <a name="wizard"></a><span data-ttu-id="a09a2-213">Assistente</span><span class="sxs-lookup"><span data-stu-id="a09a2-213">Wizard</span></span>

<span data-ttu-id="a09a2-214">Um assistente orienta um usuário por várias telas para concluir uma tarefa (como um processo de instalação).</span><span class="sxs-lookup"><span data-stu-id="a09a2-214">A wizard guides a user through several screens to complete a task (such as a setup process).</span></span>

### <a name="top-use-cases"></a><span data-ttu-id="a09a2-215">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="a09a2-215">Top use cases</span></span>

* <span data-ttu-id="a09a2-216">Configurar</span><span class="sxs-lookup"><span data-stu-id="a09a2-216">Setup</span></span>
* <span data-ttu-id="a09a2-217">Integração</span><span class="sxs-lookup"><span data-stu-id="a09a2-217">Onboarding</span></span>
* <span data-ttu-id="a09a2-218">Experiências de primeira</span><span class="sxs-lookup"><span data-stu-id="a09a2-218">First-run experiences</span></span>

# <a name="desktop"></a>[<span data-ttu-id="a09a2-219">Desktop</span><span class="sxs-lookup"><span data-stu-id="a09a2-219">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/ui-templates/wizard.png" alt-text="Exemplo mostra um modelo de interface do usuário do assistente na área de trabalho." border="false":::

# <a name="mobile"></a>[<span data-ttu-id="a09a2-221">Mobile</span><span class="sxs-lookup"><span data-stu-id="a09a2-221">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/ui-templates/mobile-wizard.png" alt-text="Exemplo mostra um modelo de interface do usuário do assistente no celular." border="false":::

---
