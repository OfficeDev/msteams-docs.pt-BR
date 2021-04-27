---
title: Criar módulos de tarefa
author: heath-hamilton
description: Saiba como projetar módulos de tarefa para aplicativos do Teams e obter o Kit de interface do usuário do Microsoft Teams.
localization_priority: Normal
ms.author: lajanuar
ms.topic: reference
ms.openlocfilehash: 3502a705bfe1bf99a5dc0edff5c5a54265cc6ca1
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019542"
---
# <a name="designing-task-modules-for-your-microsoft-teams-app"></a><span data-ttu-id="3b26f-103">Projetando módulos de tarefas para seu aplicativo do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="3b26f-103">Designing task modules for your Microsoft Teams app</span></span>

<span data-ttu-id="3b26f-104">Você pode criar experiências pop-up modais em seu aplicativo do Teams com módulos de tarefa.</span><span class="sxs-lookup"><span data-stu-id="3b26f-104">You can create modal popup experiences in your Teams app with task modules.</span></span> <span data-ttu-id="3b26f-105">Use esse recurso para exibir mídia e informações ricas ou concluir uma tarefa complexa.</span><span class="sxs-lookup"><span data-stu-id="3b26f-105">Use this capability to display rich media and information or complete a complex task.</span></span>

:::image type="content" source="../../assets/images/task-module/task-module-overview.png" alt-text="Exemplo mostra um módulo de tarefa." border="false":::

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="3b26f-107">Kit de Interface do Usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="3b26f-107">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="3b26f-108">Você pode encontrar diretrizes de design de módulo de tarefa mais abrangentes, incluindo elementos que você pode obter e modificar conforme necessário, no Kit de interface do usuário do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="3b26f-108">You can find more comprehensive task module design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3b26f-109">Obtenha o Kit de Interface do Usuário do Microsoft Teams (Figma)</span><span class="sxs-lookup"><span data-stu-id="3b26f-109">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="open-a-task-module"></a><span data-ttu-id="3b26f-110">Abrir um módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="3b26f-110">Open a task module</span></span>

<span data-ttu-id="3b26f-111">Os módulos de tarefa podem ser lançados de praticamente qualquer lugar em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3b26f-111">Task modules can be launched from almost anywhere in your app.</span></span>

* <span data-ttu-id="3b26f-112">**Guia**: Um módulo de tarefa pode ser lançado a partir de qualquer link em uma guia. Use em cenários em que você deseja que o usuário se concentre em uma interação.</span><span class="sxs-lookup"><span data-stu-id="3b26f-112">**Tab**: A task module can be launched from any link within a tab. Use in scenarios where you want the user to focus on an interaction.</span></span>
* <span data-ttu-id="3b26f-113">**Bot**: um módulo de tarefa pode ser lançado a partir de um link dentro de uma mensagem bot.</span><span class="sxs-lookup"><span data-stu-id="3b26f-113">**Bot**: A task module can be launched from a link inside a bot message.</span></span>
* <span data-ttu-id="3b26f-114">**Cartão Adaptável**: um módulo de tarefa pode ser lançado a partir de um Cartão Adaptável (enviado com uma extensão de mensagens ou por um bot) quando um usuário seleciona um botão.</span><span class="sxs-lookup"><span data-stu-id="3b26f-114">**Adaptive Card**: A task module can be launched from an Adaptive Card (sent with a messaging extension or by a bot) when a user selects a button.</span></span>
* <span data-ttu-id="3b26f-115">**Extensão de mensagens (comandos de ação)**: As extensões de mensagens permitem que você tome uma ação específica no conteúdo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="3b26f-115">**Messaging extension (action commands)**: Messaging extensions allow you to take a particular action on message content.</span></span> <span data-ttu-id="3b26f-116">Selecionar uma ação abre um módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="3b26f-116">Selecting an action opens a task module.</span></span>
* <span data-ttu-id="3b26f-117">**Extensão de mensagens (contexto** da caixa de redação) : Na caixa de redação, você pode projetar uma extensão de mensagens para abrir um módulo de tarefa em vez do flyout típico.</span><span class="sxs-lookup"><span data-stu-id="3b26f-117">**Messaging extension (compose box context)**: In the compose box, you can design a messaging extension to open a task module instead of the typical flyout.</span></span> <span data-ttu-id="3b26f-118">Reserve módulos de tarefa para interações complexas, como a conclusão de um formulário.</span><span class="sxs-lookup"><span data-stu-id="3b26f-118">Reserve task modules for complex interactions, such as completing a form.</span></span>

## <a name="anatomy"></a><span data-ttu-id="3b26f-119">Anatomia</span><span class="sxs-lookup"><span data-stu-id="3b26f-119">Anatomy</span></span>

:::image type="content" source="../../assets/images/task-module/task-module-anatomy.png" alt-text="Ilustração mostrando a anatomia da interface do usuário de um módulo de tarefa." border="false":::

<span data-ttu-id="3b26f-121">Os módulos de tarefa são superfícies muito flexíveis.</span><span class="sxs-lookup"><span data-stu-id="3b26f-121">Task modules are very flexible surfaces.</span></span> <span data-ttu-id="3b26f-122">Eles podem ser construídos com iframes, a partir de outros modelos de interface do usuário, para hospedar experiências criadas por parceiros.</span><span class="sxs-lookup"><span data-stu-id="3b26f-122">They can be built with iframes, pulling in other UI templates, to host partner-built experiences.</span></span> <span data-ttu-id="3b26f-123">Isso é preferencial para a experiência mais polida.</span><span class="sxs-lookup"><span data-stu-id="3b26f-123">This is preferred for the most polished experience.</span></span>

<span data-ttu-id="3b26f-124">Eles também podem ser construídos com a estrutura [cartão](../../task-modules-and-cards/cards/design-effective-cards.md) adaptável, que pode ser uma maneira mais simples e mais rápida de executar cenários comuns (como formulários).</span><span class="sxs-lookup"><span data-stu-id="3b26f-124">They can also be built with the [Adaptive Card](../../task-modules-and-cards/cards/design-effective-cards.md) framework, which can be a simpler and faster way to execute common scenarios (such as forms).</span></span>

|<span data-ttu-id="3b26f-125">Contador</span><span class="sxs-lookup"><span data-stu-id="3b26f-125">Counter</span></span>|<span data-ttu-id="3b26f-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="3b26f-126">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="3b26f-127">1</span><span class="sxs-lookup"><span data-stu-id="3b26f-127">1</span></span>|<span data-ttu-id="3b26f-128">**ícone de aplicativo**</span><span class="sxs-lookup"><span data-stu-id="3b26f-128">**App icon**</span></span>|
|<span data-ttu-id="3b26f-129">2</span><span class="sxs-lookup"><span data-stu-id="3b26f-129">2</span></span>|<span data-ttu-id="3b26f-130">**Nome do** aplicativo : Nome completo do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3b26f-130">**App name**: Full name of your app.</span></span>|
|<span data-ttu-id="3b26f-131">3</span><span class="sxs-lookup"><span data-stu-id="3b26f-131">3</span></span>|<span data-ttu-id="3b26f-132">**Header**: Tornar os headers claros e concisos.</span><span class="sxs-lookup"><span data-stu-id="3b26f-132">**Header**: Make headers clear and concise.</span></span> <span data-ttu-id="3b26f-133">Descreva a tarefa que você deseja que os usuários concluam.</span><span class="sxs-lookup"><span data-stu-id="3b26f-133">Describe the task you want users to complete.</span></span>
|<span data-ttu-id="3b26f-134">4 </span><span class="sxs-lookup"><span data-stu-id="3b26f-134">4</span></span>|<span data-ttu-id="3b26f-135">**Botão Fechar**: Permite que os usuários encontrem o conteúdo do aplicativo que eles querem inserir.</span><span class="sxs-lookup"><span data-stu-id="3b26f-135">**Close button**: Allows users to find app content they want to insert.</span></span>|
|<span data-ttu-id="3b26f-136">5 </span><span class="sxs-lookup"><span data-stu-id="3b26f-136">5</span></span>|<span data-ttu-id="3b26f-137">**iframe**: espaço responsivo que hospeda o conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3b26f-137">**iframe**: Responsive space that hosts your app content.</span></span>|
|<span data-ttu-id="3b26f-138">6 </span><span class="sxs-lookup"><span data-stu-id="3b26f-138">6</span></span>|<span data-ttu-id="3b26f-139">**Ações (opcional)**: Botões relacionados ao conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3b26f-139">**Actions (optional)**: Buttons related to your app content.</span></span>|

## <a name="designing-with-ui-templates"></a><span data-ttu-id="3b26f-140">Projetando com modelos de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="3b26f-140">Designing with UI templates</span></span>

<span data-ttu-id="3b26f-141">Considere usar modelos para layouts comuns dentro de seus módulos de tarefas.</span><span class="sxs-lookup"><span data-stu-id="3b26f-141">Consider using templates for common layouts inside your task modules.</span></span> <span data-ttu-id="3b26f-142">Cada um deles é feito de componentes menores para criar um design elegante e responsivo que pode ser usado fora da caixa ou personalizado para seu cenário ou com a aparência da sua marca.</span><span class="sxs-lookup"><span data-stu-id="3b26f-142">Each one is made up of smaller components to create an elegant, responsive design that can be used out of the box or customized for your scenario or with your brand look and feel.</span></span>

* <span data-ttu-id="3b26f-143">[Lista](../../concepts/design/design-teams-app-ui-templates.md#list): as listas podem exibir itens relacionados em um formato digitalizável e permitir que os usuários tomem ações em uma lista inteira ou itens individuais.</span><span class="sxs-lookup"><span data-stu-id="3b26f-143">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="3b26f-144">[Formulário](../../concepts/design/design-teams-app-ui-templates.md#form): Os formulários são para coletar, validar e enviar entrada do usuário de forma estruturada.</span><span class="sxs-lookup"><span data-stu-id="3b26f-144">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="3b26f-145">[Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): o modelo de estado vazio pode ser usado para muitos cenários, incluindo entrar, experiências de primeira executar, mensagens de erro e muito mais.</span><span class="sxs-lookup"><span data-stu-id="3b26f-145">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>

## <a name="examples"></a><span data-ttu-id="3b26f-146">Exemplos</span><span class="sxs-lookup"><span data-stu-id="3b26f-146">Examples</span></span>

### <a name="list"></a><span data-ttu-id="3b26f-147">List</span><span class="sxs-lookup"><span data-stu-id="3b26f-147">List</span></span>

<span data-ttu-id="3b26f-148">As listas funcionam bem em um módulo de tarefa porque são fáceis de examinar.</span><span class="sxs-lookup"><span data-stu-id="3b26f-148">Lists work nicely in a task module because they’re easy to scan.</span></span>

:::image type="content" source="../../assets/images/task-module/list.png" alt-text="Lista de exemplos em um módulo de tarefa." border="false":::

### <a name="form"></a><span data-ttu-id="3b26f-150">Formulário</span><span class="sxs-lookup"><span data-stu-id="3b26f-150">Form</span></span>

<span data-ttu-id="3b26f-151">Os módulos de tarefa são um ótimo local para superfície de formulários com entradas de usuário sequenciais e validação em linha.</span><span class="sxs-lookup"><span data-stu-id="3b26f-151">Task modules are a great place to surface forms with sequential user inputs and inline validation.</span></span> <span data-ttu-id="3b26f-152">Você pode aproveitar cartões adaptáveis como uma maneira de incorporar elementos de formulário.</span><span class="sxs-lookup"><span data-stu-id="3b26f-152">You can leverage Adaptive Cards as a way to embed form elements.</span></span>

:::image type="content" source="../../assets/images/task-module/form.png" alt-text="Formulário de exemplo em um módulo de tarefa." border="false":::

### <a name="sign-in"></a><span data-ttu-id="3b26f-154">Entrar</span><span class="sxs-lookup"><span data-stu-id="3b26f-154">Sign in</span></span>

<span data-ttu-id="3b26f-155">Crie um fluxo de login ou de assinatura focado com uma série de módulos de tarefas, deixando que os usuários se movam facilmente através de etapas sequenciais.</span><span class="sxs-lookup"><span data-stu-id="3b26f-155">Create a focused sign in or sign-up flow with a series of task modules, letting users move easily through sequential steps.</span></span>

:::image type="content" source="../../assets/images/task-module/sign-in.png" alt-text="Experiência de login de exemplo em um módulo de tarefa." border="false":::

### <a name="media"></a><span data-ttu-id="3b26f-157">Mídia</span><span class="sxs-lookup"><span data-stu-id="3b26f-157">Media</span></span>

<span data-ttu-id="3b26f-158">Incorporar conteúdo de mídia em um módulo de tarefa para uma experiência de exibição focada.</span><span class="sxs-lookup"><span data-stu-id="3b26f-158">Embed media content in a task module for a focused viewing experience.</span></span>

:::image type="content" source="../../assets/images/task-module/media.png" alt-text="Exemplo de conteúdo de mídia em um módulo de tarefa." border="false":::

### <a name="empty-state"></a><span data-ttu-id="3b26f-160">Estado vazio</span><span class="sxs-lookup"><span data-stu-id="3b26f-160">Empty state</span></span>

<span data-ttu-id="3b26f-161">Use para mensagens de boas-vindas, erros e sucesso.</span><span class="sxs-lookup"><span data-stu-id="3b26f-161">Use for welcome, error, and success messages.</span></span>

:::image type="content" source="../../assets/images/task-module/empty-state.png" alt-text="Exemplo de estado vazio em um módulo de tarefa." border="false":::

### <a name="image-gallery"></a><span data-ttu-id="3b26f-163">Galeria de imagens</span><span class="sxs-lookup"><span data-stu-id="3b26f-163">Image gallery</span></span>

<span data-ttu-id="3b26f-164">Incorporar um carrossel de galeria em um iframe.</span><span class="sxs-lookup"><span data-stu-id="3b26f-164">Embed a gallery carousel in an iframe.</span></span>

:::image type="content" source="../../assets/images/task-module/image-gallery.png" alt-text="Galeria de imagens de exemplo em um módulo de tarefa." border="false":::

### <a name="poll"></a><span data-ttu-id="3b26f-166">Sondagem</span><span class="sxs-lookup"><span data-stu-id="3b26f-166">Poll</span></span>

<span data-ttu-id="3b26f-167">Este exemplo mostra os resultados da sondagem lançados de um Cartão Adaptável.</span><span class="sxs-lookup"><span data-stu-id="3b26f-167">This example shows poll results launched from an Adaptive Card.</span></span> <span data-ttu-id="3b26f-168">A sondagem também pode ser colocada dentro de um módulo de tarefas.</span><span class="sxs-lookup"><span data-stu-id="3b26f-168">The poll can be placed inside a task module, too.</span></span>

:::image type="content" source="../../assets/images/task-module/poll.png" alt-text="Sondagem de exemplo em um módulo de tarefa." border="false":::

## <a name="best-practices"></a><span data-ttu-id="3b26f-170">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="3b26f-170">Best practices</span></span>

### <a name="usability"></a><span data-ttu-id="3b26f-171">Usabilidade</span><span class="sxs-lookup"><span data-stu-id="3b26f-171">Usability</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/usability-do.png" alt-text="Exemplo mostrando uma prática prática de módulo de tarefa." border="false":::

#### <a name="do-use-one-task-module-at-a-time"></a><span data-ttu-id="3b26f-173">Fazer: usar um módulo de tarefa por vez</span><span class="sxs-lookup"><span data-stu-id="3b26f-173">Do: Use one task module at a time</span></span>

<span data-ttu-id="3b26f-174">O objetivo é concentrar o usuário na conclusão de uma tarefa, afinal!</span><span class="sxs-lookup"><span data-stu-id="3b26f-174">The goal is to focus the user on completing a task after all!</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/usability-dont.png" alt-text="Exemplo mostra uma prática prática de módulo de tarefa." border="false":::

#### <a name="dont-pop-a-dialog-on-top-of-a-task-module"></a><span data-ttu-id="3b26f-176">Não: pop uma caixa de diálogo em cima de um módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="3b26f-176">Don't: Pop a dialog on top of a task module</span></span>

<span data-ttu-id="3b26f-177">Isso cria uma experiência de usuário confusa e sem foco.</span><span class="sxs-lookup"><span data-stu-id="3b26f-177">This creates an unfocused, confusing user experience.</span></span>

   :::column-end:::
:::row-end:::

### <a name="responsive"></a><span data-ttu-id="3b26f-178">Dinâmico</span><span class="sxs-lookup"><span data-stu-id="3b26f-178">Responsive</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/responsive-do.png" alt-text="Exemplo mostra as práticas práticas práticas do módulo de tarefas." border="false":::

#### <a name="do-make-sure-the-content-is-responsive"></a><span data-ttu-id="3b26f-180">Fazer: certifique-se de que o conteúdo seja responsivo</span><span class="sxs-lookup"><span data-stu-id="3b26f-180">Do: Make sure the content is responsive</span></span>

<span data-ttu-id="3b26f-181">Embora os Cartões Adaptáveis hospedados em um módulo de tarefa renderizarão bem em dispositivos móveis, se você optar por usar um iframe para hospedar conteúdo do aplicativo, certifique-se de que a interface do usuário seja responsiva e funcione bem entre dispositivos.</span><span class="sxs-lookup"><span data-stu-id="3b26f-181">While Adaptive Cards hosted in a task module render well on mobile devices, if you choose to use an iframe to host app content, make sure the UI is responsive and works well across devices.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/responsive-dont.png" alt-text="O exemplo exibe uma prática prática de módulo de tarefa." border="false":::

#### <a name="dont-use-horizontal-scroll-bars"></a><span data-ttu-id="3b26f-183">Não: use barras de rolagem horizontal</span><span class="sxs-lookup"><span data-stu-id="3b26f-183">Don't: Use horizontal scroll bars</span></span>

<span data-ttu-id="3b26f-184">É uma prática melhor manter o conteúdo focado e não muito longo.</span><span class="sxs-lookup"><span data-stu-id="3b26f-184">It's a best practice to keep content focused and not too lengthy.</span></span> <span data-ttu-id="3b26f-185">Se um rolagem for necessário, role verticalmente e não horizontalmente.</span><span class="sxs-lookup"><span data-stu-id="3b26f-185">If a scroll is necessary, scroll vertically and not horizontally.</span></span>

   :::column-end:::
:::row-end:::

### <a name="simplicity"></a><span data-ttu-id="3b26f-186">Simplicidade</span><span class="sxs-lookup"><span data-stu-id="3b26f-186">Simplicity</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/simplicity-do.png" alt-text="O exemplo exibe as práticas práticas práticas do módulo de tarefa." border="false":::

#### <a name="do-keep-it-short"></a><span data-ttu-id="3b26f-188">Do: mantenha-o curto</span><span class="sxs-lookup"><span data-stu-id="3b26f-188">Do: Keep it short</span></span>

<span data-ttu-id="3b26f-189">Você pode criar facilmente um assistente de várias etapas, mas isso não significa necessariamente que você deve!</span><span class="sxs-lookup"><span data-stu-id="3b26f-189">You can easily create a multi-step wizard, but that doesn't necessarily mean you should!</span></span> <span data-ttu-id="3b26f-190">Um módulo de tarefa de várias telas pode ser problemático porque as mensagens de entrada estão distraindo e tentando que os usuários saiam.</span><span class="sxs-lookup"><span data-stu-id="3b26f-190">A multi-screen task module can be problematic because incoming messages are distracting and tempt users to exit.</span></span> <span data-ttu-id="3b26f-191">Se sua tarefa estiver realmente envolvida, saia para uma página da Web completa em vez de um módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="3b26f-191">If your task is really involved, pop out to a full webpage instead of a task module.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/simplicity-dont.png" alt-text="Ilustração mostrando uma prática prática de módulo de tarefa." border="false":::

#### <a name="dont-do-long-interactions"></a><span data-ttu-id="3b26f-193">Não: Fazer interações longas</span><span class="sxs-lookup"><span data-stu-id="3b26f-193">Don't: Do long interactions</span></span>

<span data-ttu-id="3b26f-194">Tente manter suas interações curtas e diretas.</span><span class="sxs-lookup"><span data-stu-id="3b26f-194">Try to keep your interactions short and to the point.</span></span>

   :::column-end:::
:::row-end:::

### <a name="error-messages"></a><span data-ttu-id="3b26f-195">Mensagens de erro</span><span class="sxs-lookup"><span data-stu-id="3b26f-195">Error messages</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/error-messages-do.png" alt-text="A ilustração mostra uma prática prática de módulo de tarefa." border="false":::

#### <a name="do-use-inline-error-messages"></a><span data-ttu-id="3b26f-197">Fazer: usar mensagens de erro em linha</span><span class="sxs-lookup"><span data-stu-id="3b26f-197">Do: Use inline error messages</span></span>

<span data-ttu-id="3b26f-198">Consulte o modelo de interface do usuário de formulários para ver diretrizes sobre o tratamento de erros em linha.</span><span class="sxs-lookup"><span data-stu-id="3b26f-198">See the forms UI template for guidelines on inline error handling.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/error-messages-dont.png" alt-text="A ilustração exibe uma prática prática de módulo de tarefa." border="false":::

#### <a name="dont-put-error-messages-in-dialogs"></a><span data-ttu-id="3b26f-200">Não: colocar mensagens de erro em caixas de diálogo</span><span class="sxs-lookup"><span data-stu-id="3b26f-200">Don't: Put error messages in dialogs</span></span>

<span data-ttu-id="3b26f-201">Não pop uma mensagem de erro em uma caixa de diálogo em cima de um módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="3b26f-201">Don't pop an error message in a dialog on top of a task modules.</span></span> <span data-ttu-id="3b26f-202">Ele cria uma experiência de usuário confusa.</span><span class="sxs-lookup"><span data-stu-id="3b26f-202">It creates a confusing user experience.</span></span>

   :::column-end:::
:::row-end:::
