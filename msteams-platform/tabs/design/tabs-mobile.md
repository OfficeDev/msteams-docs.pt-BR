---
title: Guias em dispositivos móveis
description: Descreve as diretrizes para a criação de guias que funcionam em dispositivos móveis.
ms.topic: conceptual
keywords: diretrizes de design de equipes guias móveis de estrutura de referência de aplicativos pessoais
ms.openlocfilehash: 462228daa2179482110e2deb42f0f16ab2f5d5ec
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014170"
---
# <a name="tabs-on-mobile"></a><span data-ttu-id="1de13-104">Guias em dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="1de13-104">Tabs on mobile</span></span>

> [!NOTE]
> <span data-ttu-id="1de13-105">Se você optar por que sua guia canal/grupo apareça em clientes móveis do Teams, a configuração deve ter um valor para `setSettings()` a `websiteUrl` propriedade (veja abaixo).</span><span class="sxs-lookup"><span data-stu-id="1de13-105">If you choose to have your channel/group tab appear on Teams mobile clients, the `setSettings()` configuration must have a value for the `websiteUrl` property (see below).</span></span>

<span data-ttu-id="1de13-106">Guias personalizadas podem fazer parte de um canal, chat em grupo ou aplicativo pessoal (aplicativos que contêm guias estáticas e/ou um bot um-para-um).</span><span class="sxs-lookup"><span data-stu-id="1de13-106">Custom tabs can be part of a channel, group chat, or personal app (apps that contain static tabs and/or a one-to-one bot).</span></span>

<span data-ttu-id="1de13-107">Os aplicativos pessoais estão disponíveis em clientes móveis na gaveta do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1de13-107">Personal apps are available on mobile clients in the app drawer.</span></span> <span data-ttu-id="1de13-108">O aplicativo só pode ser instalado a partir de um cliente da Web ou de desktop e pode levar até 24 horas para aparecer em clientes móveis.</span><span class="sxs-lookup"><span data-stu-id="1de13-108">The app can only be installed from a desktop or web client, and can take up to 24 hours to appear on mobile clients.</span></span>

<span data-ttu-id="1de13-109">As guias de canal também estão disponíveis em dispositivos móveis.</span><span class="sxs-lookup"><span data-stu-id="1de13-109">Channel tabs are also available on mobile.</span></span> <span data-ttu-id="1de13-110">O comportamento padrão atualmente é usar o seu `websiteUrl` para iniciar a guia em uma janela do navegador.</span><span class="sxs-lookup"><span data-stu-id="1de13-110">The default behavior is currently to use your `websiteUrl` to launch your tab in a browser window.</span></span> <span data-ttu-id="1de13-111">No entanto, eles podem ser carregados em um cliente móvel clicando no menu de estouro ao lado da guia e escolhendo Abrir , que usará a guia para carregar a guia dentro do cliente móvel do `...`  `contentUrl` Teams.</span><span class="sxs-lookup"><span data-stu-id="1de13-111">However, they can be loaded on a mobile client by clicking the `...` overflow menu next to the tab and choosing **Open**, which will use your `contentUrl` to load the tab inside the Teams mobile client.</span></span>

## <a name="accessing-personal-tabs"></a><span data-ttu-id="1de13-112">Acessando guias pessoais</span><span class="sxs-lookup"><span data-stu-id="1de13-112">Accessing personal tabs</span></span>

<span data-ttu-id="1de13-113">A ilustração a seguir mostra como você acessa uma guia pessoal no celular.</span><span class="sxs-lookup"><span data-stu-id="1de13-113">The following illustration shows how you access a personal tab on mobile.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-app-drawer.png" alt-text="Ilustração mostrando a gaveta do aplicativo móvel do Teams." border="false":::

## <a name="accessing-channel-tabs"></a><span data-ttu-id="1de13-115">Acessar guias de canal</span><span class="sxs-lookup"><span data-stu-id="1de13-115">Accessing channel tabs</span></span>

<span data-ttu-id="1de13-116">A ilustração a seguir mostra como você acessa uma guia de canal no celular.</span><span class="sxs-lookup"><span data-stu-id="1de13-116">The following illustration shows how you access a channel tab on mobile.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab.png" alt-text="Ilustração mostrando uma guia móvel do Teams." border="false":::

## <a name="design-considerations"></a><span data-ttu-id="1de13-118">Considerações de design</span><span class="sxs-lookup"><span data-stu-id="1de13-118">Design considerations</span></span>

<span data-ttu-id="1de13-119">Nossa plataforma móvel permite que os aplicativos sejam uma experiência imersiva com o conteúdo do aplicativo ocupando toda a tela além da navegação principal do Teams.</span><span class="sxs-lookup"><span data-stu-id="1de13-119">Our mobile platform allows apps to be an immersive experience with the app content taking up all of the screen apart from main Teams navigation.</span></span> <span data-ttu-id="1de13-120">Para criar uma experiência imersiva que se ajuste ao Teams, siga estas diretrizes.</span><span class="sxs-lookup"><span data-stu-id="1de13-120">To create an immersive experience that fits with Teams, follow these guidelines.</span></span>

### <a name="responsive-design"></a><span data-ttu-id="1de13-121">Design responsivo</span><span class="sxs-lookup"><span data-stu-id="1de13-121">Responsive design</span></span>

<span data-ttu-id="1de13-122">Como sua guia pode ser aberta em dispositivos com uma ampla variedade de tamanhos de tela, ela precisa seguir os [princípios de design responsivo.](https://www.w3schools.com/html/html_responsive.asp)</span><span class="sxs-lookup"><span data-stu-id="1de13-122">Because your tab can be opened on devices with a wide range of screen sizes, it needs to follow [responsive design](https://www.w3schools.com/html/html_responsive.asp) principles.</span></span> <span data-ttu-id="1de13-123">Todas as construções de chave devem ser acessíveis em dispositivos móveis, e as exibições não devem ser distorcidas.</span><span class="sxs-lookup"><span data-stu-id="1de13-123">All of the key constructs should be accessible on mobile devices, and the views should not be distorted.</span></span> <span data-ttu-id="1de13-124">Certifique-se de que, quando sua guia for carregada em um dispositivo móvel, todos os botões e links sejam facilmente acessíveis usando a navegação baseada no dedo.</span><span class="sxs-lookup"><span data-stu-id="1de13-124">Ensure that when your tab is loaded on a mobile device, all buttons and links are easily accessible using finger-based navigation.</span></span>

### <a name="layouts"></a><span data-ttu-id="1de13-125">Layouts</span><span class="sxs-lookup"><span data-stu-id="1de13-125">Layouts</span></span>

<span data-ttu-id="1de13-126">Escolher o layout correto para a guia é importante.</span><span class="sxs-lookup"><span data-stu-id="1de13-126">Choosing the correct layout for your tab is important.</span></span> <span data-ttu-id="1de13-127">Você deve considerar o tipo de informação que está apresentando e escolher um layout que as organize para facilitar o consumo.</span><span class="sxs-lookup"><span data-stu-id="1de13-127">You should consider the kind of information you're presenting, and choose a layout that organizes it for easy consumption.</span></span> <span data-ttu-id="1de13-128">Algumas opções possíveis são descritas abaixo.</span><span class="sxs-lookup"><span data-stu-id="1de13-128">Some potential options are outlined below.</span></span>

#### <a name="single-canvas"></a><span data-ttu-id="1de13-129">Tela única</span><span class="sxs-lookup"><span data-stu-id="1de13-129">Single canvas</span></span>

<span data-ttu-id="1de13-130">Esta é uma área grande onde o trabalho é feito.</span><span class="sxs-lookup"><span data-stu-id="1de13-130">This is one large area where work gets done.</span></span> <span data-ttu-id="1de13-131">O aplicativo Wiki do Teams segue esse padrão.</span><span class="sxs-lookup"><span data-stu-id="1de13-131">The Teams Wiki app follows this pattern.</span></span> <span data-ttu-id="1de13-132">Se você tiver um aplicativo que não separe conteúdo em componentes menores, isso seria uma boa opção.</span><span class="sxs-lookup"><span data-stu-id="1de13-132">If you have an app that doesn’t separate content into smaller components this would be a good fit.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-single-canvas.png" alt-text="Ilustração mostrando uma guia de tela única móvel do Teams." border="false":::

#### <a name="list"></a><span data-ttu-id="1de13-134">Listar</span><span class="sxs-lookup"><span data-stu-id="1de13-134">List</span></span>

<span data-ttu-id="1de13-135">As listas são ótimas para classificar e filtrar grandes quantidades de dados e são ótimas para manter as coisas mais importantes na parte superior.</span><span class="sxs-lookup"><span data-stu-id="1de13-135">Lists are great for sorting and filtering large quantities of data and are great at keeping the most important things at the top.</span></span> <span data-ttu-id="1de13-136">É útil usar colunas que podem ser ordenadas.</span><span class="sxs-lookup"><span data-stu-id="1de13-136">It is helpful to use sortable columns.</span></span> <span data-ttu-id="1de13-137">Ações podem ser adicionadas a cada item de lista no menu de re elipses.</span><span class="sxs-lookup"><span data-stu-id="1de13-137">Actions can be added to each list item under the ellipsis menu.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-list.png" alt-text="Ilustração mostrando uma guia de lista móvel do Teams." border="false":::

#### <a name="grid"></a><span data-ttu-id="1de13-139">Grade</span><span class="sxs-lookup"><span data-stu-id="1de13-139">Grid</span></span>

<span data-ttu-id="1de13-140">Grades são úteis para mostrar elementos que são altamente visuais.</span><span class="sxs-lookup"><span data-stu-id="1de13-140">Grids are useful for showing elements which are highly visual.</span></span> <span data-ttu-id="1de13-141">Ele ajuda a incluir um filtro ou controle de pesquisa na parte superior.</span><span class="sxs-lookup"><span data-stu-id="1de13-141">It helps to include a filter or search control at the top.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-grid.png" alt-text="Imagem mostrando uma guia móvel do Teams com um layout de grade." border="false":::

### <a name="tabs-with-bots-on-mobile"></a><span data-ttu-id="1de13-143">Guias com bots em dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="1de13-143">Tabs with bots on mobile</span></span>

<span data-ttu-id="1de13-144">O exemplo a seguir é um aplicativo pessoal que tem guias e um bot.</span><span class="sxs-lookup"><span data-stu-id="1de13-144">The following example is a personal app that has tabs and a bot.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-with-bot.png" alt-text="Imagem mostrando como o aplicativo móvel do Teams tem guias e um bot." border="false":::

## <a name="ui-components"></a><span data-ttu-id="1de13-146">Componentes da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="1de13-146">UI components</span></span>

### <a name="color-palettes"></a><span data-ttu-id="1de13-147">Paletas de cores</span><span class="sxs-lookup"><span data-stu-id="1de13-147">Color palettes</span></span>

<span data-ttu-id="1de13-148">Usar nossa paleta neutra aprovada para planos de fundo, notificações, texto e botões ajudará seu aplicativo a se sentir mais em casa no Teams.</span><span class="sxs-lookup"><span data-stu-id="1de13-148">Using our approved neutral palette for backgrounds, notifications, text, and buttons will help your app feel more at home in Teams.</span></span> <span data-ttu-id="1de13-149">Como o teams mobile tem dois temas coloridos (claro e escuro), é uma boa ideia garantir que seu aplicativo tenha uma ótima aparência em ambos.</span><span class="sxs-lookup"><span data-stu-id="1de13-149">Since Teams mobile has two colour themes (light and dark), it’s a good idea to make sure your app looks great in both.</span></span>

#### <a name="light-color"></a><span data-ttu-id="1de13-150">Cor clara</span><span class="sxs-lookup"><span data-stu-id="1de13-150">Light color</span></span>

![paleta de cores claras](../../assets/images/light-color.png)

#### <a name="dark-color"></a><span data-ttu-id="1de13-152">Cor escura</span><span class="sxs-lookup"><span data-stu-id="1de13-152">Dark color</span></span>

![paleta de cores escuras](../../assets/images/dark-color.png)

### <a name="buttons-and-controls"></a><span data-ttu-id="1de13-154">Botões e controles</span><span class="sxs-lookup"><span data-stu-id="1de13-154">Buttons and controls</span></span>

<span data-ttu-id="1de13-155">A maneira como os botões são estilcionados ajuda a comunicar o tipo de ação que disparam.</span><span class="sxs-lookup"><span data-stu-id="1de13-155">The way buttons are styled helps communicate what kind of action they trigger.</span></span> <span data-ttu-id="1de13-156">Mantemos uma ampla variedade de botões formatados para mostrar diferentes níveis de ênfase.</span><span class="sxs-lookup"><span data-stu-id="1de13-156">We maintain a wide range of buttons that are formatted to show different levels of emphasis.</span></span> <span data-ttu-id="1de13-157">Os botões podem ter texto, um ícone ou uma combinação de texto e um ícone.</span><span class="sxs-lookup"><span data-stu-id="1de13-157">Buttons can have text, an icon, or a combination of text and an icon.</span></span> <span data-ttu-id="1de13-158">Para comunicar níveis diferentes em uma hierarquia, projetamos botões primários e secundários em cada categoria.</span><span class="sxs-lookup"><span data-stu-id="1de13-158">To communicate different levels in a hierarchy, we designed primary and secondary buttons within each category.</span></span>

#### <a name="buttons"></a><span data-ttu-id="1de13-159">Botões</span><span class="sxs-lookup"><span data-stu-id="1de13-159">Buttons</span></span>

<span data-ttu-id="1de13-160">Botões primários e secundários.</span><span class="sxs-lookup"><span data-stu-id="1de13-160">Primary and secondary buttons.</span></span>

![imagem de botões](../../assets/images/buttons.png)

#### <a name="selection-controls"></a><span data-ttu-id="1de13-162">Controles de seleção</span><span class="sxs-lookup"><span data-stu-id="1de13-162">Selection controls</span></span>

<span data-ttu-id="1de13-163">Botões de rádio, caixas de seleção e alternâncias.</span><span class="sxs-lookup"><span data-stu-id="1de13-163">Radio buttons, checkboxes, and toggles.</span></span>

![controles de seleção](../../assets/images/selection-controls.png)

#### <a name="chiclets-and-pills"></a><span data-ttu-id="1de13-165">Mételets e suar</span><span class="sxs-lookup"><span data-stu-id="1de13-165">Chiclets and pills</span></span>

![quedas ereção](../../assets/images/chiclets-and-pills.png)

### <a name="typography"></a><span data-ttu-id="1de13-167">Tipografia</span><span class="sxs-lookup"><span data-stu-id="1de13-167">Typography</span></span>

<span data-ttu-id="1de13-168">A tipografia deve ser clara e proposital.</span><span class="sxs-lookup"><span data-stu-id="1de13-168">Typography should be clear and purposeful.</span></span> <span data-ttu-id="1de13-169">Enfatizar informações importantes e evitar usar várias fontes e tamanhos para reduzir a confusão.</span><span class="sxs-lookup"><span data-stu-id="1de13-169">Emphasize important information and avoid using multiple fonts and sizes to reduce confusion.</span></span> <span data-ttu-id="1de13-170">Recomendamos usar o caso de sentença e evitar o uso de maiúsculas para localização e legibilidade.</span><span class="sxs-lookup"><span data-stu-id="1de13-170">We recommend using sentence case and avoiding the usage of all caps for localization and legibility.</span></span>

![tipográfico móvel](../../assets/images/mobile-typography.png)

### <a name="fields-and-flyouts"></a><span data-ttu-id="1de13-172">Campos e flyouts</span><span class="sxs-lookup"><span data-stu-id="1de13-172">Fields and flyouts</span></span>

<span data-ttu-id="1de13-173">Campos são áreas onde os usuários podem inserir texto.</span><span class="sxs-lookup"><span data-stu-id="1de13-173">Fields are areas where users can input text.</span></span> <span data-ttu-id="1de13-174">Os flyouts são mais leves do que as caixas de diálogo e aparecem no painel superior.</span><span class="sxs-lookup"><span data-stu-id="1de13-174">Flyouts are more lightweight than dialogs and appear from the top pane.</span></span>

#### <a name="list-controls"></a><span data-ttu-id="1de13-175">Controles de lista</span><span class="sxs-lookup"><span data-stu-id="1de13-175">List controls</span></span>

![controles de lista móvel](../../assets/images/mobile-list-controls.png)

#### <a name="field-controls"></a><span data-ttu-id="1de13-177">Controles de campo</span><span class="sxs-lookup"><span data-stu-id="1de13-177">Field controls</span></span>

![controles de campo móvel](../../assets/images/mobile-field-controls.png)

## <a name="developer-considerations"></a><span data-ttu-id="1de13-179">Considerações sobre o desenvolvedor</span><span class="sxs-lookup"><span data-stu-id="1de13-179">Developer considerations</span></span>

<span data-ttu-id="1de13-180">Ao criar um aplicativo que inclui uma guia, você precisa considerar (e testar) como sua guia funcionará nos clientes do Microsoft Teams para Android e iOS.</span><span class="sxs-lookup"><span data-stu-id="1de13-180">When you're building an app that includes a tab, you need to consider (and test) how your tab will function on both the Android and iOS Microsoft Teams clients.</span></span> <span data-ttu-id="1de13-181">As seções a seguir destacam alguns dos principais cenários que você precisa considerar.</span><span class="sxs-lookup"><span data-stu-id="1de13-181">The sections below outline some of the key scenarios you need to consider.</span></span>

### <a name="testing-on-mobile-clients"></a><span data-ttu-id="1de13-182">Teste em clientes móveis</span><span class="sxs-lookup"><span data-stu-id="1de13-182">Testing on mobile clients</span></span>

<span data-ttu-id="1de13-183">Você precisa validar se a guia funciona corretamente em dispositivos móveis de vários tamanhos e qualidades.</span><span class="sxs-lookup"><span data-stu-id="1de13-183">You need to validate that your tab functions properly on mobile devices of various sizes and qualities.</span></span> <span data-ttu-id="1de13-184">Para dispositivos Android, você pode usar [o DevTools](~/tabs/how-to/developer-tools.md) para depurar sua guia enquanto ela estiver em execução.</span><span class="sxs-lookup"><span data-stu-id="1de13-184">For Android devices, you can use the [DevTools](~/tabs/how-to/developer-tools.md) to debug your tab while it is running.</span></span> <span data-ttu-id="1de13-185">Recomendamos que você teste em dispositivos de alto e baixo desempenho, bem como em um tablet.</span><span class="sxs-lookup"><span data-stu-id="1de13-185">We recommend that you test on both high and low performing devices, as well as on a tablet.</span></span>

### <a name="authentication"></a><span data-ttu-id="1de13-186">Autenticação</span><span class="sxs-lookup"><span data-stu-id="1de13-186">Authentication</span></span>

<span data-ttu-id="1de13-187">Para que a autenticação funcione em clientes móveis, você deve atualizar o SDK JavaScript do Teams para pelo menos a versão 1.4.1.</span><span class="sxs-lookup"><span data-stu-id="1de13-187">For authentication to work on mobile clients, you must upgrade you Teams JavaScript SDK to at least version 1.4.1.</span></span>

### <a name="low-bandwidth-and-intermittent-connections"></a><span data-ttu-id="1de13-188">Baixa largura de banda e conexões intermitentes</span><span class="sxs-lookup"><span data-stu-id="1de13-188">Low bandwidth and intermittent connections</span></span>

<span data-ttu-id="1de13-189">Clientes móveis precisam funcionar regularmente com baixa largura de banda e conexões intermitentes.</span><span class="sxs-lookup"><span data-stu-id="1de13-189">Mobile clients regularly need to function with low bandwidth and intermittent connections.</span></span> <span data-ttu-id="1de13-190">Seu aplicativo deve lidar com os tempos-tempos de forma adequada, fornecendo uma mensagem contextual para o usuário.</span><span class="sxs-lookup"><span data-stu-id="1de13-190">Your app should handle any timeouts appropriately by providing a contextual message to the user.</span></span> <span data-ttu-id="1de13-191">Você também deve ter indicadores de progresso do usuário para fornecer comentários aos usuários sobre processos de longa duração.</span><span class="sxs-lookup"><span data-stu-id="1de13-191">You should also user progress indicators to provide feedback to your users for any long-running processes.</span></span>
