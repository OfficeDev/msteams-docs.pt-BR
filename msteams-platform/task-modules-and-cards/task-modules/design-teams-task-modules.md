---
title: Criando módulos de tarefas
author: heath-hamilton
description: Saiba como projetar módulos de tarefa para aplicativos do Teams e obter o kit de interface do usuário do Microsoft Teams.
ms.author: lajanuar
ms.topic: reference
ms.openlocfilehash: 41584ecf58ca7718290e58e5845549e4579dac64
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2020
ms.locfileid: "49605836"
---
# <a name="designing-task-modules-for-your-microsoft-teams-app"></a><span data-ttu-id="e6588-103">Criando módulos de tarefas para seu aplicativo do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="e6588-103">Designing task modules for your Microsoft Teams app</span></span>

<span data-ttu-id="e6588-104">Você pode criar experiências de pop-up modais no seu aplicativo do teams com módulos de tarefa.</span><span class="sxs-lookup"><span data-stu-id="e6588-104">You can create modal popup experiences in your Teams app with task modules.</span></span> <span data-ttu-id="e6588-105">Use este recurso para exibir mídia avançada e informações ou concluir uma tarefa complexa.</span><span class="sxs-lookup"><span data-stu-id="e6588-105">Use this capability to display rich media and information or complete a complex task.</span></span>

:::image type="content" source="../../assets/images/task-module/task-module-overview.png" alt-text="O exemplo mostra um módulo de tarefa." border="false":::

## <a name="microsoft-teams-ui-kit"></a><span data-ttu-id="e6588-107">Kit de interface do usuário do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="e6588-107">Microsoft Teams UI Kit</span></span>

<span data-ttu-id="e6588-108">Você pode encontrar mais abrangentes diretrizes de design de módulo de tarefa, incluindo elementos que podem ser capturados e modificados conforme necessário, no kit de interface do usuário do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="e6588-108">You can find more comprehensive task module design guidelines, including elements that you can grab and modify as needed, in the Microsoft Teams UI Kit.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e6588-109">Obter o kit de interface do usuário do Microsoft Teams (figma)</span><span class="sxs-lookup"><span data-stu-id="e6588-109">Get the Microsoft Teams UI Kit (Figma)</span></span>](https://www.figma.com/community/file/916836509871353159)

## <a name="open-a-task-module"></a><span data-ttu-id="e6588-110">Abrir um módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="e6588-110">Open a task module</span></span>

<span data-ttu-id="e6588-111">Os módulos de tarefa podem ser iniciados de quase qualquer lugar em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e6588-111">Task modules can be launched from almost anywhere in your app.</span></span>

* <span data-ttu-id="e6588-112">**Guia**: um módulo de tarefa pode ser iniciado em qualquer link dentro de uma Tabulação ou iframe.</span><span class="sxs-lookup"><span data-stu-id="e6588-112">**Tab**: A task module can be launched from any link within a tab or iframe.</span></span> <span data-ttu-id="e6588-113">Use em cenários em que você deseja que o usuário se concentre em uma interação.</span><span class="sxs-lookup"><span data-stu-id="e6588-113">Use in scenarios where you want the user to focus on an interaction.</span></span>
* <span data-ttu-id="e6588-114">**Bot**: um módulo de tarefa pode ser iniciado em um link dentro de uma mensagem de bot.</span><span class="sxs-lookup"><span data-stu-id="e6588-114">**Bot**: A task module can be launched from a link inside a bot message.</span></span>
* <span data-ttu-id="e6588-115">**Cartão adaptável**: um módulo de tarefa pode ser iniciado a partir de um cartão adaptável (enviado com uma extensão de mensagens ou por um bot) quando um usuário seleciona um botão.</span><span class="sxs-lookup"><span data-stu-id="e6588-115">**Adaptive Card**: A task module can be launched from an Adaptive Card (sent with a messaging extension or by a bot) when a user selects a button.</span></span>
* <span data-ttu-id="e6588-116">**Extensão de mensagens (comandos de ação)**: as extensões de mensagens permitem executar uma ação específica no conteúdo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="e6588-116">**Messaging extension (action commands)**: Messaging extensions allow you to take a particular action on message content.</span></span> <span data-ttu-id="e6588-117">Selecionar uma ação abre um módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="e6588-117">Selecting an action opens a task module.</span></span>
* <span data-ttu-id="e6588-118">**Extensão de mensagens (contexto da caixa de composição)**: na caixa compor, você pode criar uma extensão de mensagens para abrir um módulo de tarefa em vez do submenu típico.</span><span class="sxs-lookup"><span data-stu-id="e6588-118">**Messaging extension (compose box context)**: In the compose box, you can design a messaging extension to open a task module instead of the typical flyout.</span></span> <span data-ttu-id="e6588-119">Reserve módulos de tarefas para interações complexas, como preencher um formulário.</span><span class="sxs-lookup"><span data-stu-id="e6588-119">Reserve task modules for complex interactions, such as completing a form.</span></span>

## <a name="anatomy"></a><span data-ttu-id="e6588-120">Anatomia</span><span class="sxs-lookup"><span data-stu-id="e6588-120">Anatomy</span></span>

:::image type="content" source="../../assets/images/task-module/task-module-anatomy.png" alt-text="Ilustração mostrando a anatomia de interface do usuário de um módulo de tarefa." border="false":::

<span data-ttu-id="e6588-122">Os módulos de tarefa são superfícies muito flexíveis.</span><span class="sxs-lookup"><span data-stu-id="e6588-122">Task modules are very flexible surfaces.</span></span> <span data-ttu-id="e6588-123">Eles podem ser criados com IFrames, puxando outros modelos de interface do usuário para hospedar experiências criadas pelo parceiro.</span><span class="sxs-lookup"><span data-stu-id="e6588-123">They can be built with iframes, pulling in other UI templates, to host partner-built experiences.</span></span> <span data-ttu-id="e6588-124">Isso é preferível para a experiência mais elegante.</span><span class="sxs-lookup"><span data-stu-id="e6588-124">This is preferred for the most polished experience.</span></span>

<span data-ttu-id="e6588-125">Eles também podem ser criados com a estrutura de [cartão adaptável](../../task-modules-and-cards/cards/design-effective-cards.md) , que pode ser uma maneira mais simples e rápida de executar cenários comuns (como formulários).</span><span class="sxs-lookup"><span data-stu-id="e6588-125">They can also be built with the [Adaptive Card](../../task-modules-and-cards/cards/design-effective-cards.md) framework, which can be a simpler and faster way to execute common scenarios (such as forms).</span></span>

|<span data-ttu-id="e6588-126">Contador</span><span class="sxs-lookup"><span data-stu-id="e6588-126">Counter</span></span>|<span data-ttu-id="e6588-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="e6588-127">Description</span></span>|
|----------|-----------|
|<span data-ttu-id="e6588-128">1</span><span class="sxs-lookup"><span data-stu-id="e6588-128">1</span></span>|<span data-ttu-id="e6588-129">**ícone de aplicativo**</span><span class="sxs-lookup"><span data-stu-id="e6588-129">**App icon**</span></span>|
|<span data-ttu-id="e6588-130">2 </span><span class="sxs-lookup"><span data-stu-id="e6588-130">2</span></span>|<span data-ttu-id="e6588-131">**Nome do aplicativo**: nome completo do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e6588-131">**App name**: Full name of your app.</span></span>|
|<span data-ttu-id="e6588-132">3 </span><span class="sxs-lookup"><span data-stu-id="e6588-132">3</span></span>|<span data-ttu-id="e6588-133">**Cabeçalho**: torne os cabeçalhos claros e concisos.</span><span class="sxs-lookup"><span data-stu-id="e6588-133">**Header**: Make headers clear and concise.</span></span> <span data-ttu-id="e6588-134">Descreva a tarefa que você deseja que os usuários concluam.</span><span class="sxs-lookup"><span data-stu-id="e6588-134">Describe the task you want users to complete.</span></span>
|<span data-ttu-id="e6588-135">4 </span><span class="sxs-lookup"><span data-stu-id="e6588-135">4</span></span>|<span data-ttu-id="e6588-136">**Botão fechar**: permite que os usuários encontrem o conteúdo de aplicativo que desejam inserir.</span><span class="sxs-lookup"><span data-stu-id="e6588-136">**Close button**: Allows users to find app content they want to insert.</span></span>|
|<span data-ttu-id="e6588-137">5 </span><span class="sxs-lookup"><span data-stu-id="e6588-137">5</span></span>|<span data-ttu-id="e6588-138">**iframe**: espaço responsivo que hospeda o conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e6588-138">**iframe**: Responsive space that hosts your app content.</span></span>|
|<span data-ttu-id="e6588-139">6 </span><span class="sxs-lookup"><span data-stu-id="e6588-139">6</span></span>|<span data-ttu-id="e6588-140">**Ações (opcional)**: botões relacionados ao conteúdo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e6588-140">**Actions (optional)**: Buttons related to your app content.</span></span>|

## <a name="designing-with-ui-templates"></a><span data-ttu-id="e6588-141">Projetando com modelos de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="e6588-141">Designing with UI templates</span></span>

<span data-ttu-id="e6588-142">Considere usar modelos para layouts comuns dentro de seus módulos de tarefas.</span><span class="sxs-lookup"><span data-stu-id="e6588-142">Consider using templates for common layouts inside your task modules.</span></span> <span data-ttu-id="e6588-143">Cada uma é composta por componentes menores para criar um design elegante e responsivo que pode ser usado fora da caixa ou personalizado para o seu cenário ou com a aparência da marca.</span><span class="sxs-lookup"><span data-stu-id="e6588-143">Each one is made up of smaller components to create an elegant, responsive design that can be used out of the box or customized for your scenario or with your brand look and feel.</span></span>

* <span data-ttu-id="e6588-144">[Lista](../../concepts/design/design-teams-app-ui-templates.md#list): as listas podem exibir itens relacionados em um formato verificável e permitir que os usuários executem ações em uma lista inteira ou em itens individuais.</span><span class="sxs-lookup"><span data-stu-id="e6588-144">[List](../../concepts/design/design-teams-app-ui-templates.md#list): Lists can display related items in a scannable format and allow users to take actions on an entire list or individual items.</span></span>
* <span data-ttu-id="e6588-145">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): formulários são para coletar, validar e enviar entradas do usuário de forma estruturada.</span><span class="sxs-lookup"><span data-stu-id="e6588-145">[Form](../../concepts/design/design-teams-app-ui-templates.md#form): Forms are for collecting, validating, and submitting user input in a structured way.</span></span>
* <span data-ttu-id="e6588-146">[Estado vazio](../../concepts/design/design-teams-app-ui-templates.md#empty-state): o modelo de estado vazio pode ser usado para vários cenários, incluindo o login, experiências de tela de apresentação, mensagens de erro e muito mais.</span><span class="sxs-lookup"><span data-stu-id="e6588-146">[Empty state](../../concepts/design/design-teams-app-ui-templates.md#empty-state): The empty state template can be used for many scenarios, including sign in, first-run experiences, error messages, and more.</span></span>

## <a name="examples"></a><span data-ttu-id="e6588-147">Exemplos</span><span class="sxs-lookup"><span data-stu-id="e6588-147">Examples</span></span>

### <a name="list"></a><span data-ttu-id="e6588-148">Listar</span><span class="sxs-lookup"><span data-stu-id="e6588-148">List</span></span>

<span data-ttu-id="e6588-149">As listas funcionam bem em um módulo de tarefa, pois elas são fáceis de examinar.</span><span class="sxs-lookup"><span data-stu-id="e6588-149">Lists work nicely in a task module because they’re easy to scan.</span></span>

:::image type="content" source="../../assets/images/task-module/list.png" alt-text="Exemplo de lista em um módulo de tarefa." border="false":::

### <a name="form"></a><span data-ttu-id="e6588-151">Formulário</span><span class="sxs-lookup"><span data-stu-id="e6588-151">Form</span></span>

<span data-ttu-id="e6588-152">Os módulos de tarefa são um ótimo local para a superfície de formulários com entradas de usuário sequenciais e validação embutida.</span><span class="sxs-lookup"><span data-stu-id="e6588-152">Task modules are a great place to surface forms with sequential user inputs and inline validation.</span></span> <span data-ttu-id="e6588-153">Você pode aproveitar cartões adaptáveis como uma maneira de incorporar elementos de formulário.</span><span class="sxs-lookup"><span data-stu-id="e6588-153">You can leverage Adaptive Cards as a way to embed form elements.</span></span>

:::image type="content" source="../../assets/images/task-module/form.png" alt-text="Formulário de exemplo em um módulo de tarefa." border="false":::

### <a name="sign-in"></a><span data-ttu-id="e6588-155">Entrar</span><span class="sxs-lookup"><span data-stu-id="e6588-155">Sign in</span></span>

<span data-ttu-id="e6588-156">Criar um fluxo de entrada ou de inscrição focalizado com uma série de módulos de tarefa, permitindo que os usuários se movimentem facilmente por meio de etapas sequenciais.</span><span class="sxs-lookup"><span data-stu-id="e6588-156">Create a focused sign in or sign-up flow with a series of task modules, letting users move easily through sequential steps.</span></span>

:::image type="content" source="../../assets/images/task-module/sign-in.png" alt-text="Experiência de entrada de exemplo em um módulo de tarefa." border="false":::

### <a name="media"></a><span data-ttu-id="e6588-158">Mídia</span><span class="sxs-lookup"><span data-stu-id="e6588-158">Media</span></span>

<span data-ttu-id="e6588-159">Incorpore conteúdo de mídia em um módulo de tarefa para uma experiência de exibição focalizada.</span><span class="sxs-lookup"><span data-stu-id="e6588-159">Embed media content in a task module for a focused viewing experience.</span></span>

:::image type="content" source="../../assets/images/task-module/media.png" alt-text="Exemplo de conteúdo de mídia em um módulo de tarefa." border="false":::

### <a name="empty-state"></a><span data-ttu-id="e6588-161">Estado vazio</span><span class="sxs-lookup"><span data-stu-id="e6588-161">Empty state</span></span>

<span data-ttu-id="e6588-162">Use para mensagens de boas-vindas, erros e sucesso.</span><span class="sxs-lookup"><span data-stu-id="e6588-162">Use for welcome, error, and success messages.</span></span>

:::image type="content" source="../../assets/images/task-module/empty-state.png" alt-text="Exemplo de estado vazio em um módulo de tarefa." border="false":::

### <a name="image-gallery"></a><span data-ttu-id="e6588-164">Galeria de imagens</span><span class="sxs-lookup"><span data-stu-id="e6588-164">Image gallery</span></span>

<span data-ttu-id="e6588-165">Insira um carrossel de galeria dentro de um iframe.</span><span class="sxs-lookup"><span data-stu-id="e6588-165">Embed a gallery carousel inside an iframe.</span></span>

:::image type="content" source="../../assets/images/task-module/image-gallery.png" alt-text="Exemplo de galeria de imagens em um módulo de tarefa." border="false":::

### <a name="poll"></a><span data-ttu-id="e6588-167">Quanto</span><span class="sxs-lookup"><span data-stu-id="e6588-167">Poll</span></span>

<span data-ttu-id="e6588-168">Este exemplo mostra os resultados da pesquisa iniciados a partir de um cartão adaptável.</span><span class="sxs-lookup"><span data-stu-id="e6588-168">This example shows poll results launched from an Adaptive Card.</span></span>

:::image type="content" source="../../assets/images/task-module/poll.png" alt-text="Pesquisa de exemplo em um módulo de tarefa." border="false":::

## <a name="best-practices"></a><span data-ttu-id="e6588-170">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="e6588-170">Best practices</span></span>

### <a name="usability"></a><span data-ttu-id="e6588-171">Praticidade</span><span class="sxs-lookup"><span data-stu-id="e6588-171">Usability</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/usability-do.png" alt-text="Exemplo mostrando uma prática recomendada de módulo de tarefa." border="false":::

#### <a name="do-use-one-task-module-at-a-time"></a><span data-ttu-id="e6588-173">Fazer: usar um módulo de tarefa por vez</span><span class="sxs-lookup"><span data-stu-id="e6588-173">Do: Use one task module at a time</span></span>

<span data-ttu-id="e6588-174">O objetivo é concentrar o usuário na conclusão de uma tarefa após tudo!</span><span class="sxs-lookup"><span data-stu-id="e6588-174">The goal is to focus the user on completing a task after all!</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/usability-dont.png" alt-text="Exemplo mostrando uma prática recomendada de módulo de tarefa." border="false":::

#### <a name="dont-pop-a-dialog-on-top-of-a-task-module"></a><span data-ttu-id="e6588-176">Não: pop uma caixa de diálogo na parte superior de um módulo de tarefa</span><span class="sxs-lookup"><span data-stu-id="e6588-176">Don't: Pop a dialog on top of a task module</span></span>

<span data-ttu-id="e6588-177">Isso cria uma experiência de usuário desfocada e confusa.</span><span class="sxs-lookup"><span data-stu-id="e6588-177">This creates an unfocused, confusing user experience.</span></span>

   :::column-end:::
:::row-end:::

### <a name="responsive"></a><span data-ttu-id="e6588-178">Dinâmico</span><span class="sxs-lookup"><span data-stu-id="e6588-178">Responsive</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/responsive-do.png" alt-text="Exemplo mostrando uma prática recomendada de módulo de tarefa." border="false":::

#### <a name="do-make-sure-the-content-is-responsive"></a><span data-ttu-id="e6588-180">Fazer: Certifique-se de que o conteúdo é responsivo</span><span class="sxs-lookup"><span data-stu-id="e6588-180">Do: Make sure the content is responsive</span></span>

<span data-ttu-id="e6588-181">Enquanto os cartões adaptáveis hospedados em um módulo de tarefa são renderizados em dispositivos móveis, se você optar por usar um iframe para hospedar o conteúdo do aplicativo, certifique-se de que a interface do usuário seja responsiva e funcione bem entre os dispositivos.</span><span class="sxs-lookup"><span data-stu-id="e6588-181">While Adaptive Cards hosted in a task module render well on mobile devices, if you choose to use an iframe to host app content, make sure the UI is responsive and works well across devices.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/responsive-dont.png" alt-text="Exemplo mostrando uma prática recomendada de módulo de tarefa." border="false":::

#### <a name="dont-use-horizontal-scrollbars"></a><span data-ttu-id="e6588-183">Não: usar barras de rolagem horizontais</span><span class="sxs-lookup"><span data-stu-id="e6588-183">Don't: Use horizontal scrollbars</span></span>

<span data-ttu-id="e6588-184">É uma prática recomendada manter o conteúdo focado e muito longo.</span><span class="sxs-lookup"><span data-stu-id="e6588-184">It's a best practice to keep content focused and not too lengthy.</span></span> <span data-ttu-id="e6588-185">Se uma rolagem for necessária, role verticalmente e não horizontalmente.</span><span class="sxs-lookup"><span data-stu-id="e6588-185">If a scroll is necessary, scroll vertically and not horizontally.</span></span>

   :::column-end:::
:::row-end:::

### <a name="simplicity"></a><span data-ttu-id="e6588-186">Devido</span><span class="sxs-lookup"><span data-stu-id="e6588-186">Simplicity</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/simplicity-do.png" alt-text="Exemplo mostrando uma prática recomendada de módulo de tarefa." border="false":::

#### <a name="do-keep-it-short"></a><span data-ttu-id="e6588-188">Fazer: Mantenha-o curto</span><span class="sxs-lookup"><span data-stu-id="e6588-188">Do: Keep it short</span></span>

<span data-ttu-id="e6588-189">Você pode criar facilmente um assistente de várias etapas, mas isso não significa necessariamente que você deve!</span><span class="sxs-lookup"><span data-stu-id="e6588-189">You can easily create a multi-step wizard, but that doesn't necessarily mean you should!</span></span> <span data-ttu-id="e6588-190">Um módulo de tarefa de várias telas pode ser problemático porque as mensagens de entrada estão distraindo e tentam sair.</span><span class="sxs-lookup"><span data-stu-id="e6588-190">A multi-screen task module can be problematic because incoming messages are distracting and tempt users to exit.</span></span> <span data-ttu-id="e6588-191">Se a tarefa estiver realmente envolvida, desapareça para uma página da Web completa em vez de um módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="e6588-191">If your task is really involved, pop out to a full webpage instead of a task module.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/simplicity-dont.png" alt-text="Exemplo mostrando uma prática recomendada de módulo de tarefa." border="false":::

#### <a name="dont-do-long-interactions"></a><span data-ttu-id="e6588-193">Não: fazer interações longas</span><span class="sxs-lookup"><span data-stu-id="e6588-193">Don't: Do long interactions</span></span>

<span data-ttu-id="e6588-194">Tente manter suas interações curtas e ao ponto.</span><span class="sxs-lookup"><span data-stu-id="e6588-194">Try to keep your interactions short and to the point.</span></span>

   :::column-end:::
:::row-end:::

### <a name="error-messages"></a><span data-ttu-id="e6588-195">Mensagens de erro</span><span class="sxs-lookup"><span data-stu-id="e6588-195">Error messages</span></span>

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/error-messages-do.png" alt-text="Exemplo mostrando uma prática recomendada de módulo de tarefa." border="false":::

#### <a name="do-use-inline-error-messages"></a><span data-ttu-id="e6588-197">Fazer: usar mensagens de erro embutidas</span><span class="sxs-lookup"><span data-stu-id="e6588-197">Do: Use inline error messages</span></span>

<span data-ttu-id="e6588-198">Consulte o modelo de interface do usuário de formulários para obter diretrizes sobre o tratamento de erros embutido.</span><span class="sxs-lookup"><span data-stu-id="e6588-198">See the forms UI template for guidelines on inline error handling.</span></span>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/error-messages-dont.png" alt-text="Exemplo mostrando uma prática recomendada de módulo de tarefa." border="false":::

#### <a name="dont-put-error-messages-in-dialogs"></a><span data-ttu-id="e6588-200">Não: colocar mensagens de erro em caixas de diálogo</span><span class="sxs-lookup"><span data-stu-id="e6588-200">Don't: Put error messages in dialogs</span></span>

<span data-ttu-id="e6588-201">Não é exibida uma mensagem de erro em uma caixa de diálogo na parte superior de um módulo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="e6588-201">Don't pop an error message in a dialog on top of a task modules.</span></span> <span data-ttu-id="e6588-202">Ele cria uma experiência de usuário confusa.</span><span class="sxs-lookup"><span data-stu-id="e6588-202">It creates a confusing user experience.</span></span>

   :::column-end:::
:::row-end:::
