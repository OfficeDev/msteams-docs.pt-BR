---
title: Guias em dispositivos móveis
description: Descreve as diretrizes para projetar guias que funcionam em dispositivos móveis.
ms.topic: conceptual
keywords: guias móveis da estrutura de referência de diretrizes de design do teams
ms.openlocfilehash: 72d1cf4623a9f4c1b5c993f1477f755b51d9fe64
ms.sourcegitcommit: 0e252159f53ff9b4452e0574b759bfe73cbf6c84
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/14/2021
ms.locfileid: "51762022"
---
# <a name="tabs-on-mobile"></a><span data-ttu-id="cd78c-104">Guias em dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="cd78c-104">Tabs on mobile</span></span>

> [!NOTE]
> <span data-ttu-id="cd78c-105">Se você optar por ter sua guia canal/grupo exibida em clientes móveis do Teams, a configuração deve ter um valor para `setSettings()` a `websiteUrl` propriedade (consulte abaixo).</span><span class="sxs-lookup"><span data-stu-id="cd78c-105">If you choose to have your channel/group tab appear on Teams mobile clients, the `setSettings()` configuration must have a value for the `websiteUrl` property (see below).</span></span>

<span data-ttu-id="cd78c-106">Guias personalizadas podem fazer parte de um canal, chat de grupo ou aplicativo pessoal (aplicativos que contêm guias estáticas e/ou um bot um para um).</span><span class="sxs-lookup"><span data-stu-id="cd78c-106">Custom tabs can be part of a channel, group chat, or personal app (apps that contain static tabs and/or a one-to-one bot).</span></span>

<span data-ttu-id="cd78c-107">Aplicativos pessoais estão disponíveis em clientes móveis na gaveta do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cd78c-107">Personal apps are available on mobile clients in the app drawer.</span></span> <span data-ttu-id="cd78c-108">O aplicativo só pode ser instalado de uma área de trabalho ou cliente Web e pode levar até 24 horas para aparecer em clientes móveis.</span><span class="sxs-lookup"><span data-stu-id="cd78c-108">The app can only be installed from a desktop or web client, and can take up to 24 hours to appear on mobile clients.</span></span> <span data-ttu-id="cd78c-109">Como alternativa, você pode impor uma recarga no cliente móvel ao entrar e sair.</span><span class="sxs-lookup"><span data-stu-id="cd78c-109">Alternatively, you can enforce a reload on the mobile client by signing out and in.</span></span> <span data-ttu-id="cd78c-110">Isso deve disponibilizar imediatamente o aplicativo móvel.</span><span class="sxs-lookup"><span data-stu-id="cd78c-110">This should make the mobile app available right away.</span></span>

<span data-ttu-id="cd78c-111">As guias de canal também estão disponíveis no celular.</span><span class="sxs-lookup"><span data-stu-id="cd78c-111">Channel tabs are also available on mobile.</span></span> <span data-ttu-id="cd78c-112">O comportamento padrão atualmente é usar o seu `websiteUrl` para iniciar sua guia em uma janela do navegador.</span><span class="sxs-lookup"><span data-stu-id="cd78c-112">The default behavior is currently to use your `websiteUrl` to launch your tab in a browser window.</span></span> <span data-ttu-id="cd78c-113">No entanto, eles podem ser carregados em um cliente móvel clicando no menu estouro ao lado da guia e escolhendo Abrir , que usará a guia para carregar a guia dentro do cliente móvel `...` do  `contentUrl` Teams.</span><span class="sxs-lookup"><span data-stu-id="cd78c-113">However, they can be loaded on a mobile client by clicking the `...` overflow menu next to the tab and choosing **Open**, which will use your `contentUrl` to load the tab inside the Teams mobile client.</span></span>

## <a name="accessing-personal-tabs"></a><span data-ttu-id="cd78c-114">Acessando guias pessoais</span><span class="sxs-lookup"><span data-stu-id="cd78c-114">Accessing personal tabs</span></span>

<span data-ttu-id="cd78c-115">A ilustração a seguir mostra como você acessa uma guia pessoal no celular.</span><span class="sxs-lookup"><span data-stu-id="cd78c-115">The following illustration shows how you access a personal tab on mobile.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-app-drawer.png" alt-text="Ilustração mostrando a gaveta de aplicativos móveis do Teams." border="false":::

## <a name="accessing-channel-tabs"></a><span data-ttu-id="cd78c-117">Acessando guias de canal</span><span class="sxs-lookup"><span data-stu-id="cd78c-117">Accessing channel tabs</span></span>

<span data-ttu-id="cd78c-118">A ilustração a seguir mostra como você acessa uma guia de canal no celular.</span><span class="sxs-lookup"><span data-stu-id="cd78c-118">The following illustration shows how you access a channel tab on mobile.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab.png" alt-text="Ilustração mostrando uma guia móvel do Teams." border="false":::

## <a name="design-considerations"></a><span data-ttu-id="cd78c-120">Considerações de design</span><span class="sxs-lookup"><span data-stu-id="cd78c-120">Design considerations</span></span>

<span data-ttu-id="cd78c-121">Nossa plataforma móvel permite que os aplicativos sejam uma experiência imersiva com o conteúdo do aplicativo ocupando toda a tela além da navegação principal do Teams.</span><span class="sxs-lookup"><span data-stu-id="cd78c-121">Our mobile platform allows apps to be an immersive experience with the app content taking up all of the screen apart from main Teams navigation.</span></span> <span data-ttu-id="cd78c-122">Para criar uma experiência imersiva que se ajuste ao Teams, siga estas diretrizes.</span><span class="sxs-lookup"><span data-stu-id="cd78c-122">To create an immersive experience that fits with Teams, follow these guidelines.</span></span>

### <a name="responsive-design"></a><span data-ttu-id="cd78c-123">Design responsivo</span><span class="sxs-lookup"><span data-stu-id="cd78c-123">Responsive design</span></span>

<span data-ttu-id="cd78c-124">Como sua guia pode ser aberta em dispositivos com uma ampla variedade de tamanhos de tela, ela precisa seguir princípios de [design responsivo.](https://www.w3schools.com/html/html_responsive.asp)</span><span class="sxs-lookup"><span data-stu-id="cd78c-124">Because your tab can be opened on devices with a wide range of screen sizes, it needs to follow [responsive design](https://www.w3schools.com/html/html_responsive.asp) principles.</span></span> <span data-ttu-id="cd78c-125">Todas as construções principais devem ser acessíveis em dispositivos móveis, e os exibições não devem ser distorcidos.</span><span class="sxs-lookup"><span data-stu-id="cd78c-125">All of the key constructs should be accessible on mobile devices, and the views should not be distorted.</span></span> <span data-ttu-id="cd78c-126">Certifique-se de que, quando a guia for carregada em um dispositivo móvel, todos os botões e links serão facilmente acessíveis usando a navegação baseada em dedos.</span><span class="sxs-lookup"><span data-stu-id="cd78c-126">Ensure that when your tab is loaded on a mobile device, all buttons and links are easily accessible using finger-based navigation.</span></span>

### <a name="layouts"></a><span data-ttu-id="cd78c-127">Layouts</span><span class="sxs-lookup"><span data-stu-id="cd78c-127">Layouts</span></span>

<span data-ttu-id="cd78c-128">Escolher o layout correto para sua guia é importante.</span><span class="sxs-lookup"><span data-stu-id="cd78c-128">Choosing the correct layout for your tab is important.</span></span> <span data-ttu-id="cd78c-129">Você deve considerar o tipo de informação que está apresentando e escolher um layout que as organize para facilitar o consumo.</span><span class="sxs-lookup"><span data-stu-id="cd78c-129">You should consider the kind of information you're presenting, and choose a layout that organizes it for easy consumption.</span></span> <span data-ttu-id="cd78c-130">Algumas opções possíveis são descritas abaixo.</span><span class="sxs-lookup"><span data-stu-id="cd78c-130">Some potential options are outlined below.</span></span>

#### <a name="single-canvas"></a><span data-ttu-id="cd78c-131">Tela única</span><span class="sxs-lookup"><span data-stu-id="cd78c-131">Single canvas</span></span>

<span data-ttu-id="cd78c-132">Esta é uma área grande onde o trabalho é feito.</span><span class="sxs-lookup"><span data-stu-id="cd78c-132">This is one large area where work gets done.</span></span> <span data-ttu-id="cd78c-133">O aplicativo Wiki do Teams segue esse padrão.</span><span class="sxs-lookup"><span data-stu-id="cd78c-133">The Teams Wiki app follows this pattern.</span></span> <span data-ttu-id="cd78c-134">Se você tiver um aplicativo que não separe conteúdo em componentes menores, isso seria um bom ajuste.</span><span class="sxs-lookup"><span data-stu-id="cd78c-134">If you have an app that doesn’t separate content into smaller components this would be a good fit.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-single-canvas.png" alt-text="Ilustração mostrando uma guia de tela única móvel do Teams." border="false":::

#### <a name="list"></a><span data-ttu-id="cd78c-136">List</span><span class="sxs-lookup"><span data-stu-id="cd78c-136">List</span></span>

<span data-ttu-id="cd78c-137">As listas são ótimas para classificar e filtrar grandes quantidades de dados e são ótimas para manter as coisas mais importantes na parte superior.</span><span class="sxs-lookup"><span data-stu-id="cd78c-137">Lists are great for sorting and filtering large quantities of data and are great at keeping the most important things at the top.</span></span> <span data-ttu-id="cd78c-138">É útil usar colunas sortíveis.</span><span class="sxs-lookup"><span data-stu-id="cd78c-138">It is helpful to use sortable columns.</span></span> <span data-ttu-id="cd78c-139">As ações podem ser adicionadas a cada item de lista no menu reellipse.</span><span class="sxs-lookup"><span data-stu-id="cd78c-139">Actions can be added to each list item under the ellipsis menu.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-list.png" alt-text="Ilustração mostrando uma guia de lista móvel do Teams." border="false":::

#### <a name="grid"></a><span data-ttu-id="cd78c-141">Grade</span><span class="sxs-lookup"><span data-stu-id="cd78c-141">Grid</span></span>

<span data-ttu-id="cd78c-142">As grades são úteis para mostrar elementos altamente visuais.</span><span class="sxs-lookup"><span data-stu-id="cd78c-142">Grids are useful for showing elements which are highly visual.</span></span> <span data-ttu-id="cd78c-143">Ele ajuda a incluir um filtro ou controle de pesquisa na parte superior.</span><span class="sxs-lookup"><span data-stu-id="cd78c-143">It helps to include a filter or search control at the top.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-grid.png" alt-text="Ilustração mostrando uma guia móvel do Teams com um layout de grade." border="false":::

### <a name="tabs-with-bots-on-mobile"></a><span data-ttu-id="cd78c-145">Guias com bots no celular</span><span class="sxs-lookup"><span data-stu-id="cd78c-145">Tabs with bots on mobile</span></span>

<span data-ttu-id="cd78c-146">O exemplo a seguir é um aplicativo pessoal que tem guias e um bot.</span><span class="sxs-lookup"><span data-stu-id="cd78c-146">The following example is a personal app that has tabs and a bot.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-with-bot.png" alt-text="Ilustração mostrando como o aplicativo do Teams móvel que tem guias e um bot." border="false":::

## <a name="ui-components"></a><span data-ttu-id="cd78c-148">Componentes da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="cd78c-148">UI components</span></span>

### <a name="color-palettes"></a><span data-ttu-id="cd78c-149">Paletas de cores</span><span class="sxs-lookup"><span data-stu-id="cd78c-149">Color palettes</span></span>

<span data-ttu-id="cd78c-150">Usar nossa paleta neutra aprovada para planos de fundo, notificações, texto e botões ajudará seu aplicativo a se sentir mais em casa no Teams.</span><span class="sxs-lookup"><span data-stu-id="cd78c-150">Using our approved neutral palette for backgrounds, notifications, text, and buttons will help your app feel more at home in Teams.</span></span> <span data-ttu-id="cd78c-151">Como o teams mobile tem dois temas de cores (claro e escuro), é uma boa ideia garantir que seu aplicativo tenha uma ótima aparência em ambos.</span><span class="sxs-lookup"><span data-stu-id="cd78c-151">Since Teams mobile has two colour themes (light and dark), it’s a good idea to make sure your app looks great in both.</span></span>

#### <a name="light-color"></a><span data-ttu-id="cd78c-152">Cor clara</span><span class="sxs-lookup"><span data-stu-id="cd78c-152">Light color</span></span>

![paleta de cores claras](../../assets/images/light-color.png)

#### <a name="dark-color"></a><span data-ttu-id="cd78c-154">Cor escura</span><span class="sxs-lookup"><span data-stu-id="cd78c-154">Dark color</span></span>

![paleta de cores escuras](../../assets/images/dark-color.png)

### <a name="buttons-and-controls"></a><span data-ttu-id="cd78c-156">Botões e controles</span><span class="sxs-lookup"><span data-stu-id="cd78c-156">Buttons and controls</span></span>

<span data-ttu-id="cd78c-157">A maneira como os botões são estilados ajuda a comunicar que tipo de ação eles disparam.</span><span class="sxs-lookup"><span data-stu-id="cd78c-157">The way buttons are styled helps communicate what kind of action they trigger.</span></span> <span data-ttu-id="cd78c-158">Mantemos uma ampla variedade de botões formatados para mostrar diferentes níveis de ênfase.</span><span class="sxs-lookup"><span data-stu-id="cd78c-158">We maintain a wide range of buttons that are formatted to show different levels of emphasis.</span></span> <span data-ttu-id="cd78c-159">Os botões podem ter texto, um ícone ou uma combinação de texto e um ícone.</span><span class="sxs-lookup"><span data-stu-id="cd78c-159">Buttons can have text, an icon, or a combination of text and an icon.</span></span> <span data-ttu-id="cd78c-160">Para comunicar níveis diferentes em uma hierarquia, projetamos botões primários e secundários em cada categoria.</span><span class="sxs-lookup"><span data-stu-id="cd78c-160">To communicate different levels in a hierarchy, we designed primary and secondary buttons within each category.</span></span>

#### <a name="buttons"></a><span data-ttu-id="cd78c-161">Botões</span><span class="sxs-lookup"><span data-stu-id="cd78c-161">Buttons</span></span>

<span data-ttu-id="cd78c-162">Botões primários e secundários.</span><span class="sxs-lookup"><span data-stu-id="cd78c-162">Primary and secondary buttons.</span></span>

![imagem de botões](../../assets/images/buttons.png)

#### <a name="selection-controls"></a><span data-ttu-id="cd78c-164">Controles de seleção</span><span class="sxs-lookup"><span data-stu-id="cd78c-164">Selection controls</span></span>

<span data-ttu-id="cd78c-165">Botões de rádio, caixas de seleção e alternâncias.</span><span class="sxs-lookup"><span data-stu-id="cd78c-165">Radio buttons, checkboxes, and toggles.</span></span>

![controles de seleção](../../assets/images/selection-controls.png)

#### <a name="chiclets-and-pills"></a><span data-ttu-id="cd78c-167">Chiclets e comprimidos</span><span class="sxs-lookup"><span data-stu-id="cd78c-167">Chiclets and pills</span></span>

![chiclets e comprimidos](../../assets/images/chiclets-and-pills.png)

### <a name="typography"></a><span data-ttu-id="cd78c-169">Tipografia</span><span class="sxs-lookup"><span data-stu-id="cd78c-169">Typography</span></span>

<span data-ttu-id="cd78c-170">A tipografia deve ser clara e proposital.</span><span class="sxs-lookup"><span data-stu-id="cd78c-170">Typography should be clear and purposeful.</span></span> <span data-ttu-id="cd78c-171">Enfatizar informações importantes e evitar usar várias fontes e tamanhos para reduzir a confusão.</span><span class="sxs-lookup"><span data-stu-id="cd78c-171">Emphasize important information and avoid using multiple fonts and sizes to reduce confusion.</span></span> <span data-ttu-id="cd78c-172">Recomendamos usar o caso de frase e evitar o uso de todas as caps para localização e legibilidade.</span><span class="sxs-lookup"><span data-stu-id="cd78c-172">We recommend using sentence case and avoiding the usage of all caps for localization and legibility.</span></span>

![tipografia móvel](../../assets/images/mobile-typography.png)

### <a name="fields-and-flyouts"></a><span data-ttu-id="cd78c-174">Campos e flyouts</span><span class="sxs-lookup"><span data-stu-id="cd78c-174">Fields and flyouts</span></span>

<span data-ttu-id="cd78c-175">Campos são áreas onde os usuários podem inserir texto.</span><span class="sxs-lookup"><span data-stu-id="cd78c-175">Fields are areas where users can input text.</span></span> <span data-ttu-id="cd78c-176">Os flyouts são mais leves do que as caixas de diálogo e aparecem no painel superior.</span><span class="sxs-lookup"><span data-stu-id="cd78c-176">Flyouts are more lightweight than dialogs and appear from the top pane.</span></span>

#### <a name="list-controls"></a><span data-ttu-id="cd78c-177">Controles de lista</span><span class="sxs-lookup"><span data-stu-id="cd78c-177">List controls</span></span>

![controles de lista móvel](../../assets/images/mobile-list-controls.png)

#### <a name="field-controls"></a><span data-ttu-id="cd78c-179">Controles de campo</span><span class="sxs-lookup"><span data-stu-id="cd78c-179">Field controls</span></span>

![controles de campo móvel](../../assets/images/mobile-field-controls.png)

## <a name="developer-considerations"></a><span data-ttu-id="cd78c-181">Considerações sobre desenvolvedores</span><span class="sxs-lookup"><span data-stu-id="cd78c-181">Developer considerations</span></span>

<span data-ttu-id="cd78c-182">Ao criar um aplicativo que inclua uma guia, você precisa considerar (e testar) como sua guia funcionará nos clientes Android e iOS do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="cd78c-182">When you're building an app that includes a tab, you need to consider (and test) how your tab will function on both the Android and iOS Microsoft Teams clients.</span></span> <span data-ttu-id="cd78c-183">As seções abaixo delineam alguns dos principais cenários que você precisa considerar.</span><span class="sxs-lookup"><span data-stu-id="cd78c-183">The sections below outline some of the key scenarios you need to consider.</span></span>

### <a name="testing-on-mobile-clients"></a><span data-ttu-id="cd78c-184">Testes em clientes móveis</span><span class="sxs-lookup"><span data-stu-id="cd78c-184">Testing on mobile clients</span></span>

<span data-ttu-id="cd78c-185">Você precisa validar que sua guia funciona corretamente em dispositivos móveis de vários tamanhos e qualidades.</span><span class="sxs-lookup"><span data-stu-id="cd78c-185">You need to validate that your tab functions properly on mobile devices of various sizes and qualities.</span></span> <span data-ttu-id="cd78c-186">Para dispositivos Android, você pode usar [o DevTools](~/tabs/how-to/developer-tools.md) para depurar sua guia enquanto ela estiver em execução.</span><span class="sxs-lookup"><span data-stu-id="cd78c-186">For Android devices, you can use the [DevTools](~/tabs/how-to/developer-tools.md) to debug your tab while it is running.</span></span> <span data-ttu-id="cd78c-187">Recomendamos que você teste em dispositivos de alto e baixo desempenho, bem como em um tablet.</span><span class="sxs-lookup"><span data-stu-id="cd78c-187">We recommend that you test on both high and low performing devices, as well as on a tablet.</span></span>

### <a name="authentication"></a><span data-ttu-id="cd78c-188">Autenticação</span><span class="sxs-lookup"><span data-stu-id="cd78c-188">Authentication</span></span>

<span data-ttu-id="cd78c-189">Para que a autenticação funcione em clientes móveis, você deve atualizar o SDK JavaScript do Teams para pelo menos a versão 1.4.1.</span><span class="sxs-lookup"><span data-stu-id="cd78c-189">For authentication to work on mobile clients, you must upgrade you Teams JavaScript SDK to at least version 1.4.1.</span></span>

### <a name="low-bandwidth-and-intermittent-connections"></a><span data-ttu-id="cd78c-190">Baixa largura de banda e conexões intermitentes</span><span class="sxs-lookup"><span data-stu-id="cd78c-190">Low bandwidth and intermittent connections</span></span>

<span data-ttu-id="cd78c-191">Clientes móveis regularmente precisam funcionar com baixa largura de banda e conexões intermitentes.</span><span class="sxs-lookup"><span data-stu-id="cd78c-191">Mobile clients regularly need to function with low bandwidth and intermittent connections.</span></span> <span data-ttu-id="cd78c-192">Seu aplicativo deve lidar com quaisquer tempos de tempo apropriados fornecendo uma mensagem contextual ao usuário.</span><span class="sxs-lookup"><span data-stu-id="cd78c-192">Your app should handle any timeouts appropriately by providing a contextual message to the user.</span></span> <span data-ttu-id="cd78c-193">Você também deve ter indicadores de progresso do usuário para fornecer comentários aos usuários sobre processos de longa duração.</span><span class="sxs-lookup"><span data-stu-id="cd78c-193">You should also user progress indicators to provide feedback to your users for any long-running processes.</span></span>

> [!NOTE]
> <span data-ttu-id="cd78c-194">As guias são habilitadas no celular somente depois que o aplicativo é adicionado a uma lista de permitir, com base na entrada da equipe de aprovação.</span><span class="sxs-lookup"><span data-stu-id="cd78c-194">Tabs are enabled on mobile only after the application is added to an allow list, based on the input of the approval team.</span></span> <span data-ttu-id="cd78c-195">Para verificar a capacidade de resposta móvel, entre em contato com teamsubm@microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="cd78c-195">To check mobile responsiveness, reach out to teamsubm@microsoft.com.</span></span> 
