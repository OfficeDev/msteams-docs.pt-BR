---
title: Criar seu aplicativo pessoal
description: Saiba como projetar um aplicativo Teams pessoal e obter o kit Microsoft Teams interface do usuário.
author: heath-hamilton
ms.topic: conceptual
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: 83fad746d71dd196f6efa6526f5c6c28ceac9e20
ms.sourcegitcommit: 4224c44d169b1a289cbf1d3353de6bc6de7c7ea8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2021
ms.locfileid: "52644880"
---
# <a name="designing-your-personal-app-for-microsoft-teams"></a><span data-ttu-id="3ca71-103">Projetar seu aplicativo pessoal para Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="3ca71-103">Designing your personal app for Microsoft Teams</span></span>

<span data-ttu-id="3ca71-104">Um aplicativo pessoal pode ser um bot, um espaço de trabalho privado ou ambos.</span><span class="sxs-lookup"><span data-stu-id="3ca71-104">A personal app can be a bot, private workspace, or both.</span></span> <span data-ttu-id="3ca71-105">Às vezes, funciona como um local para criar ou exibir conteúdo, outras vezes oferece ao usuário uma visão visual de tudo o que é deles quando o aplicativo foi configurado como uma guia em vários canais.</span><span class="sxs-lookup"><span data-stu-id="3ca71-105">Sometimes it functions like a place to create or view content, other times it offers the user a bird’s eye view of everything that's theirs when the app has been configured as a tab in multiple channels.</span></span>

<span data-ttu-id="3ca71-106">Para orientar o design do aplicativo, as informações a seguir descrevem e ilustram como as pessoas podem adicionar, usar e gerenciar aplicativos pessoais Teams.</span><span class="sxs-lookup"><span data-stu-id="3ca71-106">To guide your app design, the following information describes and illustrates how people can add, use, and manage personal apps in Teams.</span></span>

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="3ca71-107">Kit de Interface do Usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="3ca71-107">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="3ca71-108">Você pode encontrar diretrizes abrangentes de design de aplicativo pessoal, incluindo elementos que você pode pegar e modificar conforme necessário, no Kit de interface do usuário Microsoft Teams usuário.</span><span class="sxs-lookup"><span data-stu-id="3ca71-108">You can find comprehensive personal app design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span> <span data-ttu-id="3ca71-109">O kit de interface do usuário também tem tópicos essenciais, como acessibilidade e tamanho responsivo que não são abordados aqui.</span><span class="sxs-lookup"><span data-stu-id="3ca71-109">The UI kit also has essential topics such as accessibility and responsive sizing that aren't covered here.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3ca71-110">Obtenha o Kit de Interface do Usuário do Microsoft Teams (Figma)</span><span class="sxs-lookup"><span data-stu-id="3ca71-110">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-personal-app"></a><span data-ttu-id="3ca71-111">Adicionar um aplicativo pessoal</span><span class="sxs-lookup"><span data-stu-id="3ca71-111">Add a personal app</span></span>

<span data-ttu-id="3ca71-112">Você pode adicionar um aplicativo pessoal do Teams store (AppSource) ou  do flyout do aplicativo selecionando o ícone Mais no lado esquerdo do Teams (mostrado no exemplo a seguir).</span><span class="sxs-lookup"><span data-stu-id="3ca71-112">You can add a personal app from the Teams store (AppSource) or the app flyout by selecting the **More** icon on the left side of Teams (shown in the following example).</span></span>

:::image type="content" source="../../assets/images/personal-apps/add-from-app-flyout.png" alt-text="Exemplo mostra como adicionar um aplicativo pessoal do flyout do aplicativo." border="false":::

## <a name="use-a-personal-app-private-workspace"></a><span data-ttu-id="3ca71-114">Usar um aplicativo pessoal (espaço de trabalho privado)</span><span class="sxs-lookup"><span data-stu-id="3ca71-114">Use a personal app (private workspace)</span></span>

<span data-ttu-id="3ca71-115">Com um espaço de trabalho privado, você pode exibir o conteúdo do aplicativo que é significativo para você em um local central sem sair Teams.</span><span class="sxs-lookup"><span data-stu-id="3ca71-115">With a private workspace, you can view app content that's meaningful to you in a central location without leaving Teams.</span></span>

<span data-ttu-id="3ca71-116">(Observação de implementação: o espaço de trabalho privado é baseado no [*recurso de guia*](../../build-your-first-app/build-personal-tab.md) pessoal.)</span><span class="sxs-lookup"><span data-stu-id="3ca71-116">(Implementation note: The private workspace is based on the [*personal tab*](../../build-your-first-app/build-personal-tab.md) capability.)</span></span>

### <a name="anatomy-personal-app-private-workspace"></a><span data-ttu-id="3ca71-117">Anatomia: aplicativo pessoal (espaço de trabalho privado)</span><span class="sxs-lookup"><span data-stu-id="3ca71-117">Anatomy: Personal app (private workspace)</span></span>

# <a name="desktop"></a>[<span data-ttu-id="3ca71-118">Desktop</span><span class="sxs-lookup"><span data-stu-id="3ca71-118">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/personal-apps/personal-tab-component-anatomy.png" alt-text="Exemplo mostra a anatomia do componente da guia pessoal." border="false":::

|<span data-ttu-id="3ca71-120">Contador</span><span class="sxs-lookup"><span data-stu-id="3ca71-120">Counter</span></span>|<span data-ttu-id="3ca71-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="3ca71-121">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="3ca71-122">A</span><span class="sxs-lookup"><span data-stu-id="3ca71-122">A</span></span>|<span data-ttu-id="3ca71-123">**Atribuição do aplicativo**: o logotipo e o nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3ca71-123">**App attribution**: Your app logo and name.</span></span>|
|<span data-ttu-id="3ca71-124">B</span><span class="sxs-lookup"><span data-stu-id="3ca71-124">B</span></span>|<span data-ttu-id="3ca71-125">**Guias**: fornece navegação para seu aplicativo pessoal.</span><span class="sxs-lookup"><span data-stu-id="3ca71-125">**Tabs**: Provides navigation for your personal app.</span></span>|
|<span data-ttu-id="3ca71-126">C</span><span class="sxs-lookup"><span data-stu-id="3ca71-126">C</span></span>|<span data-ttu-id="3ca71-127">**Exibição pop-out**: empurra o conteúdo do aplicativo de uma janela pai para uma janela filha autônoma.</span><span class="sxs-lookup"><span data-stu-id="3ca71-127">**Popout view**: Pushes your app content from a parent window to a standalone child window.</span></span>|
|<span data-ttu-id="3ca71-128">D</span><span class="sxs-lookup"><span data-stu-id="3ca71-128">D</span></span>|<span data-ttu-id="3ca71-129">**Mais menu**: inclui opções e informações adicionais do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3ca71-129">**More menu**: Includes additional app options and information.</span></span> <span data-ttu-id="3ca71-130">(Você poderia, alternativamente, **Configurações** uma guia.)</span><span class="sxs-lookup"><span data-stu-id="3ca71-130">(You could alternatively make **Settings** a tab.)</span></span>|

:::image type="content" source="../../assets/images/personal-apps/personal-tab-structural-anatomy.png" alt-text="Exemplo mostra a anatomia estrutural da guia pessoal." border="false":::

|<span data-ttu-id="3ca71-132">Contador</span><span class="sxs-lookup"><span data-stu-id="3ca71-132">Counter</span></span>|<span data-ttu-id="3ca71-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="3ca71-133">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="3ca71-134">A</span><span class="sxs-lookup"><span data-stu-id="3ca71-134">A</span></span>|<span data-ttu-id="3ca71-135">**Guias**: fornece navegação para seu aplicativo pessoal.</span><span class="sxs-lookup"><span data-stu-id="3ca71-135">**Tabs**: Provides navigation for your personal app.</span></span>|
|<span data-ttu-id="3ca71-136">1</span><span class="sxs-lookup"><span data-stu-id="3ca71-136">1</span></span>|<span data-ttu-id="3ca71-137">**iframe**: exibe o conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3ca71-137">**iframe**: Displays your app content.</span></span>|

# <a name="mobile"></a>[<span data-ttu-id="3ca71-138">Mobile</span><span class="sxs-lookup"><span data-stu-id="3ca71-138">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/personal-apps/mobile-personal-tab-component-anatomy.png" alt-text="Exemplo mostra a anatomia do componente da guia pessoal." border="false":::

|<span data-ttu-id="3ca71-140">Contador</span><span class="sxs-lookup"><span data-stu-id="3ca71-140">Counter</span></span>|<span data-ttu-id="3ca71-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="3ca71-141">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="3ca71-142">A</span><span class="sxs-lookup"><span data-stu-id="3ca71-142">A</span></span>|<span data-ttu-id="3ca71-143">**Atribuição de aplicativo**: Seu nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3ca71-143">**App attribution**: Your app name.</span></span>|
|<span data-ttu-id="3ca71-144">B</span><span class="sxs-lookup"><span data-stu-id="3ca71-144">B</span></span>|<span data-ttu-id="3ca71-145">**Guias**: fornece navegação para seu aplicativo pessoal.</span><span class="sxs-lookup"><span data-stu-id="3ca71-145">**Tabs**: Provides navigation for your personal app.</span></span>|
|<span data-ttu-id="3ca71-146">C</span><span class="sxs-lookup"><span data-stu-id="3ca71-146">C</span></span>|<span data-ttu-id="3ca71-147">**Mais menu**: inclui opções e informações adicionais do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3ca71-147">**More menu**: Includes additional app options and information.</span></span>|
|<span data-ttu-id="3ca71-148">D</span><span class="sxs-lookup"><span data-stu-id="3ca71-148">D</span></span>|<span data-ttu-id="3ca71-149">**Navegação primária**: fornece navegação para seu aplicativo outros recursos Teams principais.</span><span class="sxs-lookup"><span data-stu-id="3ca71-149">**Primary navigation**: Provides navigation to your app other main Teams features.</span></span>|

:::image type="content" source="../../assets/images/personal-apps/mobile-personal-tab-structural-anatomy.png" alt-text="Exemplo mostra a anatomia estrutural da guia pessoal." border="false":::

|<span data-ttu-id="3ca71-151">Contador</span><span class="sxs-lookup"><span data-stu-id="3ca71-151">Counter</span></span>|<span data-ttu-id="3ca71-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="3ca71-152">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="3ca71-153">A</span><span class="sxs-lookup"><span data-stu-id="3ca71-153">A</span></span>|<span data-ttu-id="3ca71-154">**Guias**: fornece navegação para seu aplicativo pessoal.</span><span class="sxs-lookup"><span data-stu-id="3ca71-154">**Tabs**: Provides navigation for your personal app.</span></span>|
|<span data-ttu-id="3ca71-155">1</span><span class="sxs-lookup"><span data-stu-id="3ca71-155">1</span></span>|<span data-ttu-id="3ca71-156">**webview**: exibe o conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3ca71-156">**webview**: Displays your app content.</span></span>|

---

### <a name="designing-with-ui-templates-and-advanced-components"></a><span data-ttu-id="3ca71-157">Projetando com modelos de interface do usuário e componentes avançados</span><span class="sxs-lookup"><span data-stu-id="3ca71-157">Designing with UI templates and advanced components</span></span>

<span data-ttu-id="3ca71-158">Use um dos seguintes Teams e componentes para ajudar a projetar sua guia pessoal:</span><span class="sxs-lookup"><span data-stu-id="3ca71-158">Use one of the following Teams templates and components to help design your personal tab:</span></span>

* <span data-ttu-id="3ca71-159">[Lista](../../concepts/design/design-teams-app-ui-templates.md#list): as listas podem exibir itens relacionados em um formato digitalizável e permitir que os usuários tomem ações em uma lista inteira ou itens individuais.</span><span class="sxs-lookup"><span data-stu-id="3ca71-159">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="3ca71-160">[Quadro de](../../concepts/design/design-teams-app-ui-templates.md#task-board)tarefas : um quadro de tarefas, às vezes chamado de quadro kanban ou faixas de nadador, é uma coleção de cartões frequentemente usada para rastrear o status de itens de trabalho ou tíquetes.</span><span class="sxs-lookup"><span data-stu-id="3ca71-160">[Task board](../../concepts/design/design-teams-app-ui-templates.md#task-board): A task board, sometimes called a kanban board or swim lanes, is a collection of cards often used to track the status of work items or tickets.</span></span>
* <span data-ttu-id="3ca71-161">[Painel](../../concepts/design/design-teams-app-ui-templates.md#dashboard): um painel é uma tela que contém vários cartões que fornecem uma visão geral dos dados ou conteúdo.</span><span class="sxs-lookup"><span data-stu-id="3ca71-161">[Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): A dashboard is a canvas containing multiple cards that provide an overview of data or content.</span></span>
* <span data-ttu-id="3ca71-162">[Formulário](../../concepts/design/design-teams-app-ui-templates.md#form): Os formulários são para coletar, validar e enviar entrada do usuário de forma estruturada.</span><span class="sxs-lookup"><span data-stu-id="3ca71-162">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="3ca71-163">[Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): o modelo de estado vazio pode ser usado para muitos cenários, incluindo entrar, experiências de primeira executar, mensagens de erro e muito mais.</span><span class="sxs-lookup"><span data-stu-id="3ca71-163">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>
* <span data-ttu-id="3ca71-164">[Navegação à esquerda](~/concepts/design/design-teams-app-advanced-ui-components.md#left-nav): O componente de navegação esquerdo pode ajudar se seu aplicativo pessoal exigir alguma navegação.</span><span class="sxs-lookup"><span data-stu-id="3ca71-164">[Left nav](~/concepts/design/design-teams-app-advanced-ui-components.md#left-nav): The left nav component can help if your personal app requires some navigation.</span></span> <span data-ttu-id="3ca71-165">Em geral, você deve manter a navegação no mínimo.</span><span class="sxs-lookup"><span data-stu-id="3ca71-165">In general, you should keep navigation to a minimum.</span></span>

## <a name="use-a-personal-app-bot"></a><span data-ttu-id="3ca71-166">Usar um aplicativo pessoal (bot)</span><span class="sxs-lookup"><span data-stu-id="3ca71-166">Use a personal app (bot)</span></span>

<span data-ttu-id="3ca71-167">Aplicativos pessoais podem incluir um bot para conversas um-a-um e notificações privadas (por exemplo, quando um colega posta um comentário em sua prancheta).</span><span class="sxs-lookup"><span data-stu-id="3ca71-167">Personal apps can include a bot for one-on-one conversations and private notifications (for instance, when a colleague posts a comment on your artboard).</span></span> <span data-ttu-id="3ca71-168">O bot está disponível em uma guia especificada.</span><span class="sxs-lookup"><span data-stu-id="3ca71-168">The bot is available in a tab you specify.</span></span>

### <a name="anatomy-personal-app-bot"></a><span data-ttu-id="3ca71-169">Anatomia: aplicativo pessoal (bot)</span><span class="sxs-lookup"><span data-stu-id="3ca71-169">Anatomy: Personal app (bot)</span></span>

# <a name="desktop"></a>[<span data-ttu-id="3ca71-170">Desktop</span><span class="sxs-lookup"><span data-stu-id="3ca71-170">Desktop</span></span>](#tab/desktop)

:::image type="content" source="../../assets/images/personal-apps/personal-bot-anatomy.png" alt-text="Exemplo mostra a anatomia do componente de bot pessoal." border="false":::

|<span data-ttu-id="3ca71-172">Contador</span><span class="sxs-lookup"><span data-stu-id="3ca71-172">Counter</span></span>|<span data-ttu-id="3ca71-173">Descrição</span><span class="sxs-lookup"><span data-stu-id="3ca71-173">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="3ca71-174">A</span><span class="sxs-lookup"><span data-stu-id="3ca71-174">A</span></span>|<span data-ttu-id="3ca71-175">**Guia Bot**: Por exemplo, inclua uma guia **Chat** para acessar as conversas de bot e notificações.</span><span class="sxs-lookup"><span data-stu-id="3ca71-175">**Bot tab**: For example, include a **Chat** tab to access bot conversations and notifications.</span></span>|
|<span data-ttu-id="3ca71-176">B</span><span class="sxs-lookup"><span data-stu-id="3ca71-176">B</span></span>|<span data-ttu-id="3ca71-177">**Mensagem bot**: os bots geralmente enviam mensagens e notificações na forma de um cartão (como um Cartão Adaptável).</span><span class="sxs-lookup"><span data-stu-id="3ca71-177">**Bot message**: Bots often send messages and notifications in the form of a card (such as an Adaptive Card).</span></span>|
|<span data-ttu-id="3ca71-178">C</span><span class="sxs-lookup"><span data-stu-id="3ca71-178">C</span></span>|<span data-ttu-id="3ca71-179">**Caixa de redação**: Campo de entrada para envio de mensagens para o bot.</span><span class="sxs-lookup"><span data-stu-id="3ca71-179">**Compose box**: Input field for sending messages to the bot.</span></span>|

# <a name="mobile"></a>[<span data-ttu-id="3ca71-180">Mobile</span><span class="sxs-lookup"><span data-stu-id="3ca71-180">Mobile</span></span>](#tab/mobile)

:::image type="content" source="../../assets/images/personal-apps/mobile-personal-bot-anatomy.png" alt-text="Exemplo mostra a anatomia do componente de bot pessoal." border="false":::

|<span data-ttu-id="3ca71-182">Contador</span><span class="sxs-lookup"><span data-stu-id="3ca71-182">Counter</span></span>|<span data-ttu-id="3ca71-183">Descrição</span><span class="sxs-lookup"><span data-stu-id="3ca71-183">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="3ca71-184">A</span><span class="sxs-lookup"><span data-stu-id="3ca71-184">A</span></span>|<span data-ttu-id="3ca71-185">**Ponto de entrada do bot**: Ponto de entrada para os usuários acessarem o recurso bot em seu aplicativo pessoal.</span><span class="sxs-lookup"><span data-stu-id="3ca71-185">**Bot entry point**: Entry point for users to access the bot feature in your personal app.</span></span>|
|<span data-ttu-id="3ca71-186">B</span><span class="sxs-lookup"><span data-stu-id="3ca71-186">B</span></span>|<span data-ttu-id="3ca71-187">**Botão Voltar**: leva os usuários de volta para o espaço de trabalho privado.</span><span class="sxs-lookup"><span data-stu-id="3ca71-187">**Back button**: Takes users back to the private workspace.</span></span>|
|<span data-ttu-id="3ca71-188">C</span><span class="sxs-lookup"><span data-stu-id="3ca71-188">C</span></span>|<span data-ttu-id="3ca71-189">**Mensagem bot**: os bots geralmente enviam mensagens e notificações na forma de um cartão (como um Cartão Adaptável).</span><span class="sxs-lookup"><span data-stu-id="3ca71-189">**Bot message**: Bots often send messages and notifications in the form of a card (such as an Adaptive Card).</span></span>|
|<span data-ttu-id="3ca71-190">D</span><span class="sxs-lookup"><span data-stu-id="3ca71-190">D</span></span>|<span data-ttu-id="3ca71-191">**Caixa de redação**: Campo de entrada para envio de mensagens para o bot.</span><span class="sxs-lookup"><span data-stu-id="3ca71-191">**Compose box**: Input field for sending messages to the bot.</span></span>|

---

## <a name="manage-a-personal-tab"></a><span data-ttu-id="3ca71-192">Gerenciar uma guia pessoal</span><span class="sxs-lookup"><span data-stu-id="3ca71-192">Manage a personal tab</span></span>

<span data-ttu-id="3ca71-193">No lado esquerdo da Teams, os usuários podem clicar com o botão direito do mouse no aplicativo pessoal para fixar, remover e configurar outras opções de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3ca71-193">On the left side of Teams, users can right click the personal app to pin, remove, and configure other app options.</span></span>

:::image type="content" source="../../assets/images/personal-apps/manage-personal-tab.png" alt-text="Exemplo mostra opções para gerenciar um aplicativo pessoal." border="false":::

## <a name="best-practices"></a><span data-ttu-id="3ca71-195">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="3ca71-195">Best practices</span></span>

<span data-ttu-id="3ca71-196">Use essas recomendações para criar uma experiência de aplicativo de qualidade.</span><span class="sxs-lookup"><span data-stu-id="3ca71-196">Use these recommendations to create a quality app experience.</span></span>

### <a name="tab-priority"></a><span data-ttu-id="3ca71-197">Prioridade de tabulação</span><span class="sxs-lookup"><span data-stu-id="3ca71-197">Tab priority</span></span>

#### <a name="do-show-the-most-relevant-content-in-the-first-tab"></a><span data-ttu-id="3ca71-198">Do: Mostrar o conteúdo mais relevante na primeira guia</span><span class="sxs-lookup"><span data-stu-id="3ca71-198">Do: Show the most relevant content in the first tab</span></span>

<span data-ttu-id="3ca71-199">Com o ressamento responsivo, as guias à direita podem ficar truncadas ou fora de exibição.</span><span class="sxs-lookup"><span data-stu-id="3ca71-199">With responsive sizing, tabs on the right may become truncated or out of view.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-priority-do.png" alt-text="Exemplo mostra um aplicativo pessoal exibindo o conteúdo mais relevante na primeira guia." border="false":::

#### <a name="dont-lead-with-secondary-content-or-metadata"></a><span data-ttu-id="3ca71-201">Não: Levar com conteúdo ou metadados secundários</span><span class="sxs-lookup"><span data-stu-id="3ca71-201">Don’t: Lead with secondary content or metadata</span></span>

<span data-ttu-id="3ca71-202">Como um aplicativo Web padrão, a navegação por tabulação deve progredir em uma ordem que ajude a entender os principais recursos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3ca71-202">Like a standard web app, tab navigation should progress in an order that helps make sense of your app’s primary features.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-priority-dont.png" alt-text="Exemplo mostra um aplicativo pessoal à frente com conteúdo ou metadados secundários." border="false":::

### <a name="tab-hierarchy"></a><span data-ttu-id="3ca71-204">Hierarquia de guias</span><span class="sxs-lookup"><span data-stu-id="3ca71-204">Tab hierarchy</span></span>

#### <a name="do-tabs-should-be-of-equal-hierarchy-and-represent-key-app-pages"></a><span data-ttu-id="3ca71-205">Do: As guias devem ser de hierarquia igual e representar páginas principais do aplicativo</span><span class="sxs-lookup"><span data-stu-id="3ca71-205">Do: Tabs should be of equal hierarchy and represent key app pages</span></span>

<span data-ttu-id="3ca71-206">Suas guias devem categorizar os principais recursos e conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3ca71-206">Your tabs should categorize your app’s primary features and content.</span></span> <span data-ttu-id="3ca71-207">Com o ressamento responsivo, o conteúdo à direita pode ficar truncado ou fora de exibição.</span><span class="sxs-lookup"><span data-stu-id="3ca71-207">With responsive sizing, content on the right may become truncated or out of view.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-hierarchy-do.png" alt-text="Exemplo mostra um aplicativo pessoal com guias de hierarquia igual." border="false":::

#### <a name="dont-include-different-levels-of-hierarchy"></a><span data-ttu-id="3ca71-209">Não: inclua diferentes níveis de hierarquia</span><span class="sxs-lookup"><span data-stu-id="3ca71-209">Don't: Include different levels of hierarchy</span></span>

<span data-ttu-id="3ca71-210">Seu conteúdo deve progredir em uma ordem lógica que ajude os usuários a entender isso.</span><span class="sxs-lookup"><span data-stu-id="3ca71-210">Your content should progress in a logical order that helps users make sense of it.</span></span> <span data-ttu-id="3ca71-211">Se você tiver duas guias intimamente relacionadas, considere combiná-las em uma guia.</span><span class="sxs-lookup"><span data-stu-id="3ca71-211">If you have two tabs that are closely related, consider combining them into one tab.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-hierarchy-dont.png" alt-text="Exemplo mostra um aplicativo pessoal com diferentes níveis de hierarquia." border="false":::

### <a name="first-run-experience"></a><span data-ttu-id="3ca71-213">Tela de apresentação</span><span class="sxs-lookup"><span data-stu-id="3ca71-213">First-run experience</span></span>

#### <a name="do-include-a-first-run-experience"></a><span data-ttu-id="3ca71-214">Do: Incluir uma experiência de primeira executar</span><span class="sxs-lookup"><span data-stu-id="3ca71-214">Do: Include a first-run experience</span></span>

<span data-ttu-id="3ca71-215">Deve haver pelo menos uma tela de boas-vindas na primeira vez que você usar um aplicativo pessoal.</span><span class="sxs-lookup"><span data-stu-id="3ca71-215">There should be at least a welcome screen the first time you use a personal app.</span></span> <span data-ttu-id="3ca71-216">Para bots, descreva o que seu bot pode fazer e forneça ações rápidas, como um botão de login.</span><span class="sxs-lookup"><span data-stu-id="3ca71-216">For bots, describe what your bot can do and provide quick actions, such as a sign-in button.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-fre-do.png" alt-text="Exemplo mostra o que fazer durante uma experiência de primeira executar um aplicativo pessoal." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-fre-do.png" alt-text="Outro exemplo mostra o que fazer durante uma experiência de primeira executar um aplicativo pessoal." border="false":::

#### <a name="dont-start-with-a-blank-screen"></a><span data-ttu-id="3ca71-219">Não: Comece com uma tela em branco</span><span class="sxs-lookup"><span data-stu-id="3ca71-219">Don't: Start with a blank screen</span></span>

<span data-ttu-id="3ca71-220">Os usuários podem ficar confusos se nada for exibido na primeira vez em que executarem seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3ca71-220">Users might be confused if nothing displays the first time they run your app.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-fre-dont.png" alt-text="Exemplo mostra o que não fazer durante uma experiência de primeira executar um aplicativo pessoal." border="false":::

### <a name="personalized-content"></a><span data-ttu-id="3ca71-222">Conteúdo personalizado</span><span class="sxs-lookup"><span data-stu-id="3ca71-222">Personalized content</span></span>

#### <a name="do-aggregate-app-content-relevant-to-a-user"></a><span data-ttu-id="3ca71-223">Do: Agregar conteúdo de aplicativo relevante para um usuário</span><span class="sxs-lookup"><span data-stu-id="3ca71-223">Do: Aggregate app content relevant to a user</span></span>

<span data-ttu-id="3ca71-224">Seja uma guia pessoal ou bot, exibe conteúdo relacionado apenas à atividade de um usuário em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3ca71-224">Whether it's a personal tab or bot, display content related to only a user's activity in your app.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-personalized-content-do.png" alt-text="Exemplo mostra o que fazer com um aplicativo pessoal e conteúdo personalizado." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-personalized-content-do.png" alt-text="Outro exemplo mostra o que fazer com um aplicativo pessoal e conteúdo personalizado." border="false":::

#### <a name="dont-show-unrelated-or-overly-broad-content"></a><span data-ttu-id="3ca71-227">Não: mostrar conteúdo não relacionado ou muito amplo</span><span class="sxs-lookup"><span data-stu-id="3ca71-227">Don’t: Show unrelated or overly broad content</span></span>

<span data-ttu-id="3ca71-228">Em contextos pessoais, não exibir conteúdo para equipes da qual um usuário não faz parte.</span><span class="sxs-lookup"><span data-stu-id="3ca71-228">In personal contexts, don’t display content for teams a user isn't part of.</span></span> <span data-ttu-id="3ca71-229">O conteúdo do bot pessoal deve se concentrar no indivíduo, não em um grupo.</span><span class="sxs-lookup"><span data-stu-id="3ca71-229">Personal bot content should focus on the individual—not a group.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-personalized-content-dont.png" alt-text="Exemplo mostra o que não fazer com um aplicativo pessoal e conteúdo personalizado." border="false":::

:::image type="content" source="../../assets/images/personal-apps/personal-bot-personalized-content-dont.png" alt-text="Outro exemplo mostra o que não fazer com um aplicativo pessoal e conteúdo personalizado." border="false":::

### <a name="complex-app-features"></a><span data-ttu-id="3ca71-232">Recursos complexos do aplicativo</span><span class="sxs-lookup"><span data-stu-id="3ca71-232">Complex app features</span></span>

#### <a name="do-allow-users-to-access-complex-features-in-a-browser"></a><span data-ttu-id="3ca71-233">Fazer: permitir que os usuários acessem recursos complexos em um navegador</span><span class="sxs-lookup"><span data-stu-id="3ca71-233">Do: Allow users to access complex features in a browser</span></span>

<span data-ttu-id="3ca71-234">Seu aplicativo deve se concentrar nas tarefas principais no Teams, mas você ainda pode exibir o aplicativo completo e autônomo em um navegador.</span><span class="sxs-lookup"><span data-stu-id="3ca71-234">Your app should focus on core tasks in Teams, but you can still view the full, standalone app in a browser.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-feature-do.png" alt-text="Exemplo mostra como lidar com recursos complexos de aplicativo com um aplicativo pessoal." border="false":::

#### <a name="dont-include-your-entire-app"></a><span data-ttu-id="3ca71-236">Não: inclua seu aplicativo inteiro</span><span class="sxs-lookup"><span data-stu-id="3ca71-236">Don’t: Include your entire app</span></span>

<span data-ttu-id="3ca71-237">A menos que você tenha criado seu aplicativo especificamente para Teams, você provavelmente terá recursos que não fazem sentido em uma ferramenta de colaboração.</span><span class="sxs-lookup"><span data-stu-id="3ca71-237">Unless you created your app specifically for Teams, you probably have features that don’t make sense in a collaboration tool.</span></span>

:::image type="content" source="../../assets/images/personal-apps/personal-tab-feature-dont.png" alt-text="Exemplo mostra como não manipular recursos complexos do aplicativo com um aplicativo pessoal." border="false":::

## <a name="see-also"></a><span data-ttu-id="3ca71-239">Confira também</span><span class="sxs-lookup"><span data-stu-id="3ca71-239">See also</span></span>

<span data-ttu-id="3ca71-240">Essas outras diretrizes de design podem ajudar, dependendo do escopo do seu aplicativo pessoal:</span><span class="sxs-lookup"><span data-stu-id="3ca71-240">These other design guidelines may help depending on the scope of your personal app:</span></span>

* [<span data-ttu-id="3ca71-241">Projetando sua guia</span><span class="sxs-lookup"><span data-stu-id="3ca71-241">Designing your tab</span></span>](../../tabs/design/tabs.md)
* [<span data-ttu-id="3ca71-242">Projetando um bot</span><span class="sxs-lookup"><span data-stu-id="3ca71-242">Designing you bot</span></span>](../../bots/design/bots.md)
