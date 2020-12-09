---
title: Criando seu aplicativo pessoal
description: Saiba como criar um aplicativo pessoal do Teams e obter o kit de interface do usuário do Microsoft Teams.
author: heath-hamilton
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 971071be9f345815f5461646d7970efdf05fd5c4
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2020
ms.locfileid: "49604959"
---
# <a name="designing-your-personal-app-for-microsoft-teams"></a><span data-ttu-id="dc88c-103">Projetando seu aplicativo pessoal para o Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="dc88c-103">Designing your personal app for Microsoft Teams</span></span>

<span data-ttu-id="dc88c-104">Um aplicativo pessoal pode ser um bot, um espaço de trabalho privado ou ambos.</span><span class="sxs-lookup"><span data-stu-id="dc88c-104">A personal app can be a bot, private workspace, or both.</span></span> <span data-ttu-id="dc88c-105">Às vezes, ele funciona como um local para criar ou exibir o conteúdo, outras vezes, ele oferece ao usuário uma visão geral de todos os itens que são seus, quando o aplicativo é configurado como uma guia em vários canais.</span><span class="sxs-lookup"><span data-stu-id="dc88c-105">Sometimes it functions like a place to create or view content, other times it offers the user a bird’s eye view of everything that’s theirs when the app has been configured as a tab in multiple channels.</span></span>

<span data-ttu-id="dc88c-106">Para guiar o design do aplicativo, as informações a seguir descrevem e ilustra como as pessoas podem adicionar, usar e gerenciar aplicativos pessoais no Teams.</span><span class="sxs-lookup"><span data-stu-id="dc88c-106">To guide your app design, the following information describes and illustrates how people can add, use, and manage personal apps in Teams.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="dc88c-107">Kit de interface do usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="dc88c-107">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="dc88c-108">Você pode encontrar diretrizes abrangentes de design de aplicativo pessoal, incluindo elementos que podem ser capturados e modificados conforme necessário, no kit de interface do usuário do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="dc88c-108">You can find comprehensive personal app design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span> <span data-ttu-id="dc88c-109">O kit de interface do usuário também tem tópicos essenciais, como acessibilidade e dimensionamento responsivo que não são abordados aqui.</span><span class="sxs-lookup"><span data-stu-id="dc88c-109">The UI kit also has essential topics such as accessibility and responsive sizing that aren't covered here.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dc88c-110">Obter o kit de interface do usuário do Microsoft Teams (figma)</span><span class="sxs-lookup"><span data-stu-id="dc88c-110">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-personal-app"></a><span data-ttu-id="dc88c-111">Adicionar um aplicativo pessoal</span><span class="sxs-lookup"><span data-stu-id="dc88c-111">Add a personal app</span></span>

<span data-ttu-id="dc88c-112">Você pode adicionar um aplicativo pessoal do repositório do Teams (AppSource) ou o submenu do aplicativo selecionando o ícone **mais** no lado esquerdo do Teams (mostrado no exemplo a seguir).</span><span class="sxs-lookup"><span data-stu-id="dc88c-112">You can add a personal app from the Teams store (AppSource) or the app flyout by selecting the **More** icon on the left side of Teams (shown in the following example).</span></span>

:::image type="content" source="../../assets/images/personal-apps/add-from-app-flyout.png" alt-text="O exemplo mostra como adicionar um aplicativo pessoal do submenu de aplicativo." border="false":::

## <a name="use-a-personal-app-private-workspace"></a><span data-ttu-id="dc88c-114">Usar um aplicativo pessoal (espaço de trabalho privado)</span><span class="sxs-lookup"><span data-stu-id="dc88c-114">Use a personal app (private workspace)</span></span>

<span data-ttu-id="dc88c-115">Com um espaço de trabalho privado, você pode visualizar o conteúdo do aplicativo que é significativo para você em um local central sem sair do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="dc88c-115">With a private workspace, you can view app content that's meaningful to you in a central location without leaving Teams.</span></span>

<span data-ttu-id="dc88c-116">(Observação de implementação: o espaço de trabalho privado baseia-se no recurso de [*Tabulação pessoal*](../../build-your-first-app/build-personal-tab.md) .)</span><span class="sxs-lookup"><span data-stu-id="dc88c-116">(Implementation note: The private workspace is based on the [*personal tab*](../../build-your-first-app/build-personal-tab.md) capability.)</span></span>

### <a name="anatomy-personal-app-private-workspace"></a><span data-ttu-id="dc88c-117">Anatomia: aplicativo pessoal (espaço de trabalho privado)</span><span class="sxs-lookup"><span data-stu-id="dc88c-117">Anatomy: Personal app (private workspace)</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-component-anatomy.png" alt-text="O exemplo mostra a anatomia do componente da guia pessoal." border="false":::

|<span data-ttu-id="dc88c-119">Contador</span><span class="sxs-lookup"><span data-stu-id="dc88c-119">Counter</span></span>|<span data-ttu-id="dc88c-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="dc88c-120">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="dc88c-121">A</span><span class="sxs-lookup"><span data-stu-id="dc88c-121">A</span></span>|<span data-ttu-id="dc88c-122">**Atribuição de aplicativos**: o logotipo e o nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dc88c-122">**App attribution**: Your app logo and name.</span></span>|
|<span data-ttu-id="dc88c-123">B</span><span class="sxs-lookup"><span data-stu-id="dc88c-123">B</span></span>|<span data-ttu-id="dc88c-124">**Guias**: fornece navegação para seu aplicativo pessoal.</span><span class="sxs-lookup"><span data-stu-id="dc88c-124">**Tabs**: Provides navigation for your personal app.</span></span> <span data-ttu-id="dc88c-125">Por exemplo, inclua uma guia **sobre** ou **ajuda** .</span><span class="sxs-lookup"><span data-stu-id="dc88c-125">For example, include an **About** or **Help** tab.</span></span>|
|<span data-ttu-id="dc88c-126">C</span><span class="sxs-lookup"><span data-stu-id="dc88c-126">C</span></span>|<span data-ttu-id="dc88c-127">**Pop-up View**: envia o conteúdo do aplicativo de uma janela pai para uma janela filho autônoma.</span><span class="sxs-lookup"><span data-stu-id="dc88c-127">**Popout view**: Pushes your app content from a parent window to a standalone child window.</span></span>|
|<span data-ttu-id="dc88c-128">D</span><span class="sxs-lookup"><span data-stu-id="dc88c-128">D</span></span>|<span data-ttu-id="dc88c-129">**Mais menu**: inclui informações e opções adicionais do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dc88c-129">**More menu**: Includes additional app information and options.</span></span> <span data-ttu-id="dc88c-130">(Você poderia, opcionalmente, fazer **configurações** uma guia.)</span><span class="sxs-lookup"><span data-stu-id="dc88c-130">(You could alternatively make **Settings** a tab.)</span></span>|

:::image type="content" source="../../assets/images/personal-apps/personal-tab-structural-anatomy.png" alt-text="O exemplo mostra a anatomia estrutural da guia pessoal." border="false":::

|<span data-ttu-id="dc88c-132">Contador</span><span class="sxs-lookup"><span data-stu-id="dc88c-132">Counter</span></span>|<span data-ttu-id="dc88c-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="dc88c-133">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="dc88c-134">A</span><span class="sxs-lookup"><span data-stu-id="dc88c-134">A</span></span>|<span data-ttu-id="dc88c-135">**Guias**: fornece navegação para seu aplicativo pessoal.</span><span class="sxs-lookup"><span data-stu-id="dc88c-135">**Tabs**: Provides navigation for your personal app.</span></span>|
|<span data-ttu-id="dc88c-136">1 </span><span class="sxs-lookup"><span data-stu-id="dc88c-136">1</span></span>|<span data-ttu-id="dc88c-137">**iframe**: exibe o conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dc88c-137">**iframe**: Displays your app content.</span></span>|

### <a name="designing-with-ui-templates"></a><span data-ttu-id="dc88c-138">Projetando com modelos de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="dc88c-138">Designing with UI templates</span></span>

<span data-ttu-id="dc88c-139">Use um dos seguintes modelos de interface do usuário do Microsoft Teams para ajudar a criar sua guia pessoal:</span><span class="sxs-lookup"><span data-stu-id="dc88c-139">Use one of the following Teams UI templates to help design your personal tab:</span></span>

* <span data-ttu-id="dc88c-140">[Lista](../../concepts/design/design-teams-app-ui-templates.md#list): as listas podem exibir itens relacionados em um formato verificável e permitir que os usuários executem ações em uma lista inteira ou em itens individuais.</span><span class="sxs-lookup"><span data-stu-id="dc88c-140">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="dc88c-141">[Quadro de tarefas](../../concepts/design/design-teams-app-ui-templates.md#task-board): um quadro de tarefas, às vezes chamado de um quadro Kanban ou uma pista de baixo, é uma coleção de cartões usados para acompanhar o status de itens de trabalho ou tíquetes.</span><span class="sxs-lookup"><span data-stu-id="dc88c-141">[Task board](../../concepts/design/design-teams-app-ui-templates.md#task-board): A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span>
* <span data-ttu-id="dc88c-142">[Painel](../../concepts/design/design-teams-app-ui-templates.md#dashboard): um painel é uma tela contendo vários cartões que oferecem uma visão geral de dados ou conteúdo.</span><span class="sxs-lookup"><span data-stu-id="dc88c-142">[Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): A dashboard is a canvas containing multiple cards that provide an overview of data or content.</span></span>
* <span data-ttu-id="dc88c-143">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): formulários são para coletar, validar e enviar entradas do usuário de forma estruturada.</span><span class="sxs-lookup"><span data-stu-id="dc88c-143">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="dc88c-144">[Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): o modelo de estado vazio pode ser usado para vários cenários, incluindo o login, experiências de tela de apresentação, mensagens de erro e muito mais.</span><span class="sxs-lookup"><span data-stu-id="dc88c-144">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>
* <span data-ttu-id="dc88c-145">[NAV à esquerda](../../concepts/design/design-teams-app-ui-templates.md#left-nav): o modelo de navegação à esquerda pode ajudar se sua guia requer alguma navegação.</span><span class="sxs-lookup"><span data-stu-id="dc88c-145">[Left nav](../../concepts/design/design-teams-app-ui-templates.md#left-nav): The left nav template can help if your tab requires some navigation.</span></span> <span data-ttu-id="dc88c-146">Em geral, você deve manter a navegação de guia no mínimo.</span><span class="sxs-lookup"><span data-stu-id="dc88c-146">In general, you should keep tab navigation to a minimum.</span></span>

## <a name="use-a-personal-app-bot"></a><span data-ttu-id="dc88c-147">Usar um aplicativo pessoal (bot)</span><span class="sxs-lookup"><span data-stu-id="dc88c-147">Use a personal app (bot)</span></span>

<span data-ttu-id="dc88c-148">Os aplicativos pessoais podem incluir um bot para conversas de uma em um e notificações privadas (por exemplo, quando um colega posta um comentário na sua prancheta).</span><span class="sxs-lookup"><span data-stu-id="dc88c-148">Personal apps can include a bot for one-on-one conversations and private notifications (for instance, when a colleague posts a comment on your artboard).</span></span> <span data-ttu-id="dc88c-149">O bot está disponível em uma guia que você especificar.</span><span class="sxs-lookup"><span data-stu-id="dc88c-149">The bot is available in a tab you specify.</span></span>

### <a name="anatomy-personal-app-bot"></a><span data-ttu-id="dc88c-150">Anatomia: aplicativo pessoal (bot)</span><span class="sxs-lookup"><span data-stu-id="dc88c-150">Anatomy: Personal app (bot)</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-bot-anatomy.png" alt-text="O exemplo mostra a anatomia do componente de bot pessoal." border="false":::

|<span data-ttu-id="dc88c-152">Contador</span><span class="sxs-lookup"><span data-stu-id="dc88c-152">Counter</span></span>|<span data-ttu-id="dc88c-153">Descrição</span><span class="sxs-lookup"><span data-stu-id="dc88c-153">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="dc88c-154">A</span><span class="sxs-lookup"><span data-stu-id="dc88c-154">A</span></span>|<span data-ttu-id="dc88c-155">**Guia bot**: por exemplo, inclua uma guia **chat** para acessar conversas e notificações de bot.</span><span class="sxs-lookup"><span data-stu-id="dc88c-155">**Bot tab**: For example, include a **Chat** tab to access bot conversations and notifications.</span></span>|
|<span data-ttu-id="dc88c-156">B</span><span class="sxs-lookup"><span data-stu-id="dc88c-156">B</span></span>|<span data-ttu-id="dc88c-157">**Mensagem de bot**: os bots geralmente enviam mensagens e notificações na forma de um cartão (como um cartão adaptável).</span><span class="sxs-lookup"><span data-stu-id="dc88c-157">**Bot message**: Bots often send messages and notifications in the form of a card (such as an Adaptive Card).</span></span>|
|<span data-ttu-id="dc88c-158">C</span><span class="sxs-lookup"><span data-stu-id="dc88c-158">C</span></span>|<span data-ttu-id="dc88c-159">**Caixa de composição**: campo de entrada para envio de mensagens ao bot.</span><span class="sxs-lookup"><span data-stu-id="dc88c-159">**Compose box**: Input field for sending messages to the bot.</span></span>|

## <a name="best-practices"></a><span data-ttu-id="dc88c-160">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="dc88c-160">Best practices</span></span>

### <a name="tab-priority"></a><span data-ttu-id="dc88c-161">Prioridade de tabulação</span><span class="sxs-lookup"><span data-stu-id="dc88c-161">Tab priority</span></span>

#### <a name="do-show-the-most-relevant-content-in-the-first-tab"></a><span data-ttu-id="dc88c-162">Fazer: mostrar o conteúdo mais relevante na primeira guia</span><span class="sxs-lookup"><span data-stu-id="dc88c-162">Do: Show the most relevant content in the first tab</span></span>

<span data-ttu-id="dc88c-163">Com o dimensionamento responsivo, as guias à direita podem ficar truncadas ou fora de visão.</span><span class="sxs-lookup"><span data-stu-id="dc88c-163">With responsive sizing, tabs on the right may become truncated or out of view.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-priority-do.png" alt-text="O exemplo mostra uma prática recomendada de aplicativo pessoal." border="false":::

#### <a name="dont-lead-with-secondary-content-or-metadata"></a><span data-ttu-id="dc88c-165">Não: liderança com conteúdo secundário ou metadados</span><span class="sxs-lookup"><span data-stu-id="dc88c-165">Don’t: Lead with secondary content or metadata</span></span>

<span data-ttu-id="dc88c-166">Como um aplicativo Web padrão, a navegação de guia deve progredir em uma ordem que ajuda a fazer sentido dos principais recursos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dc88c-166">Like a standard web app, tab navigation should progress in an order that helps make sense of your app’s primary features.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-priority-dont.png" alt-text="O exemplo mostra uma prática recomendada de aplicativo pessoal." border="false":::

### <a name="tab-hierarchy"></a><span data-ttu-id="dc88c-168">Hierarquia de guias</span><span class="sxs-lookup"><span data-stu-id="dc88c-168">Tab hierarchy</span></span>

#### <a name="do-tabs-should-be-of-equal-hierarchy-and-represent-key-app-pages"></a><span data-ttu-id="dc88c-169">Fazer: as guias devem ser de hierarquia igual e representar páginas de aplicativo de chave</span><span class="sxs-lookup"><span data-stu-id="dc88c-169">Do: Tabs should be of equal hierarchy and represent key app pages</span></span>

<span data-ttu-id="dc88c-170">Suas guias devem categorizar os principais recursos e conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dc88c-170">Your tabs should categorize your app’s primary features and content.</span></span> <span data-ttu-id="dc88c-171">Com o dimensionamento responsivo, o conteúdo à direita pode ficar truncado ou fora do modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="dc88c-171">With responsive sizing, content on the right may become truncated or out of view.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-hierarchy-do.png" alt-text="O exemplo mostra uma prática recomendada de aplicativo pessoal." border="false":::

#### <a name="dont-include-different-levels-of-hierarchy"></a><span data-ttu-id="dc88c-173">Não: incluir níveis diferentes de hierarquia</span><span class="sxs-lookup"><span data-stu-id="dc88c-173">Don't: Include different levels of hierarchy</span></span>

<span data-ttu-id="dc88c-174">O conteúdo deve progredir em uma ordem lógica que ajude os usuários a fazer sentido.</span><span class="sxs-lookup"><span data-stu-id="dc88c-174">Your content should progress in a logical order that helps users make sense of it.</span></span> <span data-ttu-id="dc88c-175">Se você tiver duas guias que estão intimamente relacionadas, considere combiná-las em uma guia.</span><span class="sxs-lookup"><span data-stu-id="dc88c-175">If you have two tabs that are closely related, consider combining them into one tab.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-hierarchy-dont.png" alt-text="O exemplo mostra uma prática recomendada de aplicativo pessoal." border="false":::

### <a name="first-run-experience"></a><span data-ttu-id="dc88c-177">Tela de apresentação</span><span class="sxs-lookup"><span data-stu-id="dc88c-177">First-run experience</span></span>

#### <a name="do-include-a-first-run-experience"></a><span data-ttu-id="dc88c-178">Fazer: incluir uma experiência de primeira execução</span><span class="sxs-lookup"><span data-stu-id="dc88c-178">Do: Include a first-run experience</span></span>

<span data-ttu-id="dc88c-179">Deve haver pelo menos uma tela de boas-vindas na primeira vez que você usa um aplicativo pessoal.</span><span class="sxs-lookup"><span data-stu-id="dc88c-179">There should be at least a welcome screen the first time you use a personal app.</span></span> <span data-ttu-id="dc88c-180">Para bots, descreva o que seu bot pode fazer e forneça ações rápidas, como um botão de entrada.</span><span class="sxs-lookup"><span data-stu-id="dc88c-180">For bots, describe what your bot can do and provide quick actions, such as a sign-in button.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-fre-do.png" alt-text="O exemplo mostra uma prática recomendada de aplicativo pessoal." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-fre-do.png" alt-text="O exemplo mostra uma prática recomendada de aplicativo pessoal." border="false":::

#### <a name="dont-start-with-a-blank-screen"></a><span data-ttu-id="dc88c-183">Não: começar com uma tela em branco</span><span class="sxs-lookup"><span data-stu-id="dc88c-183">Don't: Start with a blank screen</span></span>

<span data-ttu-id="dc88c-184">Os usuários podem ser confundidos se nada é exibido na primeira vez que executam o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dc88c-184">Users might be confused if nothing displays the first time they run your app.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-fre-dont.png" alt-text="O exemplo mostra uma prática recomendada de aplicativo pessoal." border="false":::

### <a name="personalized-content"></a><span data-ttu-id="dc88c-186">Conteúdo personalizado</span><span class="sxs-lookup"><span data-stu-id="dc88c-186">Personalized content</span></span>

#### <a name="do-aggregate-app-content-relevant-to-a-user"></a><span data-ttu-id="dc88c-187">Fazer: agregar o conteúdo do aplicativo relevante a um usuário</span><span class="sxs-lookup"><span data-stu-id="dc88c-187">Do: Aggregate app content relevant to a user</span></span>

<span data-ttu-id="dc88c-188">Seja uma guia ou um bot pessoal, exiba o conteúdo relacionado à atividade de um usuário em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dc88c-188">Whether it's a personal tab or bot, display content related to only a user's activity in your app.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-personalized-content-do.png" alt-text="O exemplo mostra uma prática recomendada de aplicativo pessoal." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-personalized-content-do.png" alt-text="O exemplo mostra uma prática recomendada de aplicativo pessoal." border="false":::

#### <a name="dont-show-unrelated-or-overly-broad-content"></a><span data-ttu-id="dc88c-191">Não: Mostrar conteúdo abrangente ou muito amplo</span><span class="sxs-lookup"><span data-stu-id="dc88c-191">Don’t: Show unrelated or overly broad content</span></span>

<span data-ttu-id="dc88c-192">Em contextos pessoais, não exibe conteúdo para equipes que um usuário não faz parte do.</span><span class="sxs-lookup"><span data-stu-id="dc88c-192">In personal contexts, don’t display content for teams a user isn't part of.</span></span> <span data-ttu-id="dc88c-193">O conteúdo do bot pessoal deve se concentrar na pessoa, não em um grupo.</span><span class="sxs-lookup"><span data-stu-id="dc88c-193">Personal bot content should focus on the individual—not a group.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-personalized-content-dont.png" alt-text="O exemplo mostra uma prática recomendada de aplicativo pessoal." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-personalized-content-dont.png" alt-text="O exemplo mostra uma prática recomendada de aplicativo pessoal." border="false":::

### <a name="complex-app-features"></a><span data-ttu-id="dc88c-196">Recursos de aplicativos complexos</span><span class="sxs-lookup"><span data-stu-id="dc88c-196">Complex app features</span></span>

#### <a name="do-allow-users-to-access-complex-features-in-a-browser"></a><span data-ttu-id="dc88c-197">Fazer: permitir que os usuários acessem recursos complexos em um navegador</span><span class="sxs-lookup"><span data-stu-id="dc88c-197">Do: Allow users to access complex features in a browser</span></span>

<span data-ttu-id="dc88c-198">Seu aplicativo deve se concentrar nas tarefas principais no Teams, mas você ainda pode exibir o aplicativo completo autônomo em um navegador.</span><span class="sxs-lookup"><span data-stu-id="dc88c-198">Your app should focus on core tasks in Teams, but you can still view the full, standalone app in a browser.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-feature-do.png" alt-text="O exemplo mostra uma prática recomendada de aplicativo pessoal." border="false":::

#### <a name="dont-include-your-entire-app"></a><span data-ttu-id="dc88c-200">Não: inclua todo o aplicativo</span><span class="sxs-lookup"><span data-stu-id="dc88c-200">Don’t: Include your entire app</span></span>

<span data-ttu-id="dc88c-201">A menos que você tenha criado o aplicativo especificamente para o Teams, provavelmente tem recursos que não fazem sentido em uma ferramenta de colaboração.</span><span class="sxs-lookup"><span data-stu-id="dc88c-201">Unless you created your app specifically for Teams, you probably have features that don’t make sense in a collaboration tool.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-feature-dont.png" alt-text="O exemplo mostra uma prática recomendada de aplicativo pessoal." border="false":::

## <a name="manage-a-personal-tab"></a><span data-ttu-id="dc88c-203">Gerenciar uma guia pessoal</span><span class="sxs-lookup"><span data-stu-id="dc88c-203">Manage a personal tab</span></span>

<span data-ttu-id="dc88c-204">No lado esquerdo do Teams, os usuários podem clicar com o botão direito do mouse no aplicativo pessoal para fixar, remover e configurar outras opções de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="dc88c-204">On the left side of Teams, users can right click the personal app to pin, remove, and configure other app options.</span></span>

:::image type="content" source="../../assets/images/personal-apps/manage-personal-tab.png" alt-text="O exemplo mostra opções para gerenciar um aplicativo pessoal." border="false":::

## <a name="learn-more"></a><span data-ttu-id="dc88c-206">Saiba mais</span><span class="sxs-lookup"><span data-stu-id="dc88c-206">Learn more</span></span>

<span data-ttu-id="dc88c-207">Essas outras diretrizes de design podem ajudar dependendo do escopo do seu aplicativo pessoal:</span><span class="sxs-lookup"><span data-stu-id="dc88c-207">These other design guidelines may help depending on the scope of your personal app:</span></span>

* [<span data-ttu-id="dc88c-208">Criar sua guia</span><span class="sxs-lookup"><span data-stu-id="dc88c-208">Designing your tab</span></span>](../../tabs/design/tabs.md)
* [<span data-ttu-id="dc88c-209">Projetando o bot</span><span class="sxs-lookup"><span data-stu-id="dc88c-209">Designing you bot</span></span>](../../bots/design/bots.md)

## <a name="validate-your-design"></a><span data-ttu-id="dc88c-210">Validar o design</span><span class="sxs-lookup"><span data-stu-id="dc88c-210">Validate your design</span></span>

<span data-ttu-id="dc88c-211">Se você planeja publicar seu aplicativo no AppSource, você deve compreender os problemas de design que geralmente causam falha nos aplicativos durante o envio.</span><span class="sxs-lookup"><span data-stu-id="dc88c-211">If you plan to publish your app to AppSource, you should understand the design issues that commonly cause apps to fail during submission.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dc88c-212">Verificar diretrizes de validação de design</span><span class="sxs-lookup"><span data-stu-id="dc88c-212">Check design validation guidelines</span></span>](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
