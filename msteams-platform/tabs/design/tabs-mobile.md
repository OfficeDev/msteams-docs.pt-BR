---
title: Guias em dispositivos móveis
description: Descreve as diretrizes para projetar guias que funcionam em dispositivos móveis.
ms.topic: conceptual
localization_priority: Normal
keywords: guias móveis da estrutura de referência de diretrizes de design do teams
ms.openlocfilehash: 853ab2c52edd1f4faedcc92e6f0e8d0821b580c7
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566695"
---
# <a name="tabs-on-mobile"></a><span data-ttu-id="58bcb-104">Guias em dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="58bcb-104">Tabs on mobile</span></span>

<span data-ttu-id="58bcb-105">Você pode incluir guias em Teams, chats e aplicativos pessoais.</span><span class="sxs-lookup"><span data-stu-id="58bcb-105">You can include tabs in Teams mobile channels, chats, and personal apps.</span></span>

## <a name="accessing-personal-tabs"></a><span data-ttu-id="58bcb-106">Acessando guias pessoais</span><span class="sxs-lookup"><span data-stu-id="58bcb-106">Accessing personal tabs</span></span>

<span data-ttu-id="58bcb-107">Você pode acessar guias pessoais na gaveta do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="58bcb-107">You can access personal tabs in the app drawer.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-app-drawer.png" alt-text="Ilustração mostrando a Teams do aplicativo móvel." border="false":::

## <a name="accessing-channel-tabs"></a><span data-ttu-id="58bcb-109">Acessando guias de canal</span><span class="sxs-lookup"><span data-stu-id="58bcb-109">Accessing channel tabs</span></span>

<span data-ttu-id="58bcb-110">Você pode acessar guias de canal e grupo selecionando o botão **Mais** no canal ou chat no qual eles foram adicionados.</span><span class="sxs-lookup"><span data-stu-id="58bcb-110">You can access channel and group tabs by selecting the **More** button in the channel or chat in which they've been added.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab.png" alt-text="Ilustração mostrando uma Teams móvel." border="false":::

## <a name="design-considerations"></a><span data-ttu-id="58bcb-112">Considerações de design</span><span class="sxs-lookup"><span data-stu-id="58bcb-112">Design considerations</span></span>

<span data-ttu-id="58bcb-113">Nossa plataforma móvel permite que os aplicativos sejam uma experiência imersiva com o conteúdo do aplicativo ocupando toda a tela, além da navegação Teams principal.</span><span class="sxs-lookup"><span data-stu-id="58bcb-113">Our mobile platform allows apps to be an immersive experience with the app content taking up all of the screen apart from main Teams navigation.</span></span> <span data-ttu-id="58bcb-114">Para criar uma experiência imersiva que se ajuste ao Teams, siga estas diretrizes.</span><span class="sxs-lookup"><span data-stu-id="58bcb-114">To create an immersive experience that fits with Teams, follow these guidelines.</span></span>

### <a name="responsive-design"></a><span data-ttu-id="58bcb-115">Design responsivo</span><span class="sxs-lookup"><span data-stu-id="58bcb-115">Responsive design</span></span>

<span data-ttu-id="58bcb-116">Como sua guia pode ser aberta em dispositivos com uma ampla variedade de tamanhos de tela, ela precisa seguir princípios de [design responsivo.](https://www.w3schools.com/html/html_responsive.asp)</span><span class="sxs-lookup"><span data-stu-id="58bcb-116">Because your tab can be opened on devices with a wide range of screen sizes, it needs to follow [responsive design](https://www.w3schools.com/html/html_responsive.asp) principles.</span></span> <span data-ttu-id="58bcb-117">Todas as construções principais devem ser acessíveis em dispositivos móveis, e os exibições não devem ser distorcidos.</span><span class="sxs-lookup"><span data-stu-id="58bcb-117">All of the key constructs should be accessible on mobile devices, and the views should not be distorted.</span></span> <span data-ttu-id="58bcb-118">Certifique-se de que, quando a guia for carregada em um dispositivo móvel, todos os botões e links serão facilmente acessíveis usando a navegação baseada em dedos.</span><span class="sxs-lookup"><span data-stu-id="58bcb-118">Ensure that when your tab is loaded on a mobile device, all buttons and links are easily accessible using finger-based navigation.</span></span>

### <a name="layouts"></a><span data-ttu-id="58bcb-119">Layouts</span><span class="sxs-lookup"><span data-stu-id="58bcb-119">Layouts</span></span>

<span data-ttu-id="58bcb-120">Escolher o layout correto para sua guia é importante.</span><span class="sxs-lookup"><span data-stu-id="58bcb-120">Choosing the correct layout for your tab is important.</span></span> <span data-ttu-id="58bcb-121">Você deve considerar o tipo de informação que está apresentando e escolher um layout que as organize para facilitar o consumo.</span><span class="sxs-lookup"><span data-stu-id="58bcb-121">You should consider the kind of information you're presenting, and choose a layout that organizes it for easy consumption.</span></span> <span data-ttu-id="58bcb-122">Algumas opções possíveis são descritas abaixo.</span><span class="sxs-lookup"><span data-stu-id="58bcb-122">Some potential options are outlined below.</span></span>

#### <a name="single-canvas"></a><span data-ttu-id="58bcb-123">Tela única</span><span class="sxs-lookup"><span data-stu-id="58bcb-123">Single canvas</span></span>

<span data-ttu-id="58bcb-124">Esta é uma área grande onde o trabalho é feito.</span><span class="sxs-lookup"><span data-stu-id="58bcb-124">This is one large area where work gets done.</span></span> <span data-ttu-id="58bcb-125">O Teams wiki segue esse padrão.</span><span class="sxs-lookup"><span data-stu-id="58bcb-125">The Teams Wiki app follows this pattern.</span></span> <span data-ttu-id="58bcb-126">Se você tiver um aplicativo que não separe conteúdo em componentes menores, isso seria um bom ajuste.</span><span class="sxs-lookup"><span data-stu-id="58bcb-126">If you have an app that doesn’t separate content into smaller components this would be a good fit.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-single-canvas.png" alt-text="Ilustração mostrando uma Teams única tela móvel." border="false":::

#### <a name="list"></a><span data-ttu-id="58bcb-128">List</span><span class="sxs-lookup"><span data-stu-id="58bcb-128">List</span></span>

<span data-ttu-id="58bcb-129">As listas são ótimas para classificar e filtrar grandes quantidades de dados e são ótimas para manter as coisas mais importantes na parte superior.</span><span class="sxs-lookup"><span data-stu-id="58bcb-129">Lists are great for sorting and filtering large quantities of data and are great at keeping the most important things at the top.</span></span> <span data-ttu-id="58bcb-130">É útil usar colunas sortíveis.</span><span class="sxs-lookup"><span data-stu-id="58bcb-130">It is helpful to use sortable columns.</span></span> <span data-ttu-id="58bcb-131">As ações podem ser adicionadas a cada item de lista no menu reellipse.</span><span class="sxs-lookup"><span data-stu-id="58bcb-131">Actions can be added to each list item under the ellipsis menu.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-list.png" alt-text="Ilustração mostrando uma guia Teams lista móvel." border="false":::

#### <a name="grid"></a><span data-ttu-id="58bcb-133">Grade</span><span class="sxs-lookup"><span data-stu-id="58bcb-133">Grid</span></span>

<span data-ttu-id="58bcb-134">As grades são úteis para mostrar elementos altamente visuais.</span><span class="sxs-lookup"><span data-stu-id="58bcb-134">Grids are useful for showing elements which are highly visual.</span></span> <span data-ttu-id="58bcb-135">Ele ajuda a incluir um filtro ou controle de pesquisa na parte superior.</span><span class="sxs-lookup"><span data-stu-id="58bcb-135">It helps to include a filter or search control at the top.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-grid.png" alt-text="Ilustração mostrando uma Teams móvel com um layout de grade." border="false":::

### <a name="tabs-with-bots-on-mobile"></a><span data-ttu-id="58bcb-137">Guias com bots no celular</span><span class="sxs-lookup"><span data-stu-id="58bcb-137">Tabs with bots on mobile</span></span>

<span data-ttu-id="58bcb-138">O exemplo a seguir é um aplicativo pessoal que tem guias e um bot:</span><span class="sxs-lookup"><span data-stu-id="58bcb-138">The following example is a personal app that has tabs and a bot:</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-with-bot.png" alt-text="Ilustração mostrando como o aplicativo Teams celular que tem guias e um bot." border="false":::

## <a name="ui-components"></a><span data-ttu-id="58bcb-140">Componentes da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="58bcb-140">UI components</span></span>

### <a name="color-palettes"></a><span data-ttu-id="58bcb-141">Paletas de cores</span><span class="sxs-lookup"><span data-stu-id="58bcb-141">Color palettes</span></span>

<span data-ttu-id="58bcb-142">Usar nossa paleta neutra aprovada para planos de fundo, notificações, texto e botões ajudará seu aplicativo a se sentir mais em casa no Teams.</span><span class="sxs-lookup"><span data-stu-id="58bcb-142">Using our approved neutral palette for backgrounds, notifications, text, and buttons will help your app feel more at home in Teams.</span></span> <span data-ttu-id="58bcb-143">Como Teams celular tem dois temas de cores (claro e escuro), é uma boa ideia garantir que seu aplicativo tenha uma ótima aparência em ambos.</span><span class="sxs-lookup"><span data-stu-id="58bcb-143">Since Teams mobile has two colour themes (light and dark), it’s a good idea to make sure your app looks great in both.</span></span>

#### <a name="light-color"></a><span data-ttu-id="58bcb-144">Cor clara</span><span class="sxs-lookup"><span data-stu-id="58bcb-144">Light color</span></span>

![paleta de cores claras](../../assets/images/light-color.png)

#### <a name="dark-color"></a><span data-ttu-id="58bcb-146">Cor escura</span><span class="sxs-lookup"><span data-stu-id="58bcb-146">Dark color</span></span>

![paleta de cores escuras](../../assets/images/dark-color.png)

### <a name="buttons-and-controls"></a><span data-ttu-id="58bcb-148">Botões e controles</span><span class="sxs-lookup"><span data-stu-id="58bcb-148">Buttons and controls</span></span>

<span data-ttu-id="58bcb-149">A maneira como os botões são estilados ajuda a comunicar que tipo de ação eles disparam.</span><span class="sxs-lookup"><span data-stu-id="58bcb-149">The way buttons are styled helps communicate what kind of action they trigger.</span></span> <span data-ttu-id="58bcb-150">Mantemos uma ampla variedade de botões formatados para mostrar diferentes níveis de ênfase.</span><span class="sxs-lookup"><span data-stu-id="58bcb-150">We maintain a wide range of buttons that are formatted to show different levels of emphasis.</span></span> <span data-ttu-id="58bcb-151">Os botões podem ter texto, um ícone ou uma combinação de texto e um ícone.</span><span class="sxs-lookup"><span data-stu-id="58bcb-151">Buttons can have text, an icon, or a combination of text and an icon.</span></span> <span data-ttu-id="58bcb-152">Para comunicar níveis diferentes em uma hierarquia, projetamos botões primários e secundários em cada categoria.</span><span class="sxs-lookup"><span data-stu-id="58bcb-152">To communicate different levels in a hierarchy, we designed primary and secondary buttons within each category.</span></span>

#### <a name="buttons"></a><span data-ttu-id="58bcb-153">Botões</span><span class="sxs-lookup"><span data-stu-id="58bcb-153">Buttons</span></span>

<span data-ttu-id="58bcb-154">Botões primários e secundários.</span><span class="sxs-lookup"><span data-stu-id="58bcb-154">Primary and secondary buttons.</span></span>

![imagem de botões](../../assets/images/buttons.png)

#### <a name="selection-controls"></a><span data-ttu-id="58bcb-156">Controles de seleção</span><span class="sxs-lookup"><span data-stu-id="58bcb-156">Selection controls</span></span>

<span data-ttu-id="58bcb-157">Botões de rádio, caixas de seleção e alternâncias.</span><span class="sxs-lookup"><span data-stu-id="58bcb-157">Radio buttons, checkboxes, and toggles.</span></span>

![controles de seleção](../../assets/images/selection-controls.png)

#### <a name="chiclets-and-pills"></a><span data-ttu-id="58bcb-159">Chiclets e comprimidos</span><span class="sxs-lookup"><span data-stu-id="58bcb-159">Chiclets and pills</span></span>

![chiclets e comprimidos](../../assets/images/chiclets-and-pills.png)

### <a name="typography"></a><span data-ttu-id="58bcb-161">Tipografia</span><span class="sxs-lookup"><span data-stu-id="58bcb-161">Typography</span></span>

<span data-ttu-id="58bcb-162">A tipografia deve ser clara e proposital.</span><span class="sxs-lookup"><span data-stu-id="58bcb-162">Typography should be clear and purposeful.</span></span> <span data-ttu-id="58bcb-163">Enfatizar informações importantes e evitar usar várias fontes e tamanhos para reduzir a confusão.</span><span class="sxs-lookup"><span data-stu-id="58bcb-163">Emphasize important information and avoid using multiple fonts and sizes to reduce confusion.</span></span> <span data-ttu-id="58bcb-164">Recomendamos usar o caso de frase e evitar o uso de todas as caps para localização e legibilidade.</span><span class="sxs-lookup"><span data-stu-id="58bcb-164">We recommend using sentence case and avoiding the usage of all caps for localization and legibility.</span></span>

![tipografia móvel](../../assets/images/mobile-typography.png)

### <a name="fields-and-flyouts"></a><span data-ttu-id="58bcb-166">Campos e flyouts</span><span class="sxs-lookup"><span data-stu-id="58bcb-166">Fields and flyouts</span></span>

<span data-ttu-id="58bcb-167">Campos são áreas onde os usuários podem inserir texto.</span><span class="sxs-lookup"><span data-stu-id="58bcb-167">Fields are areas where users can input text.</span></span> <span data-ttu-id="58bcb-168">Os flyouts são mais leves do que as caixas de diálogo e aparecem no painel superior.</span><span class="sxs-lookup"><span data-stu-id="58bcb-168">Flyouts are more lightweight than dialogs and appear from the top pane.</span></span>

#### <a name="list-controls"></a><span data-ttu-id="58bcb-169">Controles de lista</span><span class="sxs-lookup"><span data-stu-id="58bcb-169">List controls</span></span>

![controles de lista móvel](../../assets/images/mobile-list-controls.png)

#### <a name="field-controls"></a><span data-ttu-id="58bcb-171">Controles de campo</span><span class="sxs-lookup"><span data-stu-id="58bcb-171">Field controls</span></span>

![controles de campo móvel](../../assets/images/mobile-field-controls.png)

## <a name="developer-considerations"></a><span data-ttu-id="58bcb-173">Considerações sobre desenvolvedores</span><span class="sxs-lookup"><span data-stu-id="58bcb-173">Developer considerations</span></span>

<span data-ttu-id="58bcb-174">Ao criar um aplicativo que inclua uma guia, você precisa considerar (e testar) como sua guia funcionará nos clientes android e iOS Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="58bcb-174">When you're building an app that includes a tab, you need to consider (and test) how your tab will function on both the Android and iOS Microsoft Teams clients.</span></span> <span data-ttu-id="58bcb-175">As seções abaixo delineam alguns dos principais cenários que você precisa considerar.</span><span class="sxs-lookup"><span data-stu-id="58bcb-175">The sections below outline some of the key scenarios you need to consider.</span></span>

### <a name="authentication"></a><span data-ttu-id="58bcb-176">Autenticação</span><span class="sxs-lookup"><span data-stu-id="58bcb-176">Authentication</span></span>

<span data-ttu-id="58bcb-177">Para que a autenticação funcione em clientes móveis, você deve atualizar Teams SDK JavaScript para pelo menos a versão 1.4.1.</span><span class="sxs-lookup"><span data-stu-id="58bcb-177">For authentication to work on mobile clients, you must upgrade you Teams JavaScript SDK to at least version 1.4.1.</span></span>

### <a name="low-bandwidth-and-intermittent-connections"></a><span data-ttu-id="58bcb-178">Baixa largura de banda e conexões intermitentes</span><span class="sxs-lookup"><span data-stu-id="58bcb-178">Low bandwidth and intermittent connections</span></span>

<span data-ttu-id="58bcb-179">Clientes móveis regularmente precisam funcionar com baixa largura de banda e conexões intermitentes.</span><span class="sxs-lookup"><span data-stu-id="58bcb-179">Mobile clients regularly need to function with low bandwidth and intermittent connections.</span></span> <span data-ttu-id="58bcb-180">Seu aplicativo deve lidar com quaisquer tempos de tempo apropriados fornecendo uma mensagem contextual ao usuário.</span><span class="sxs-lookup"><span data-stu-id="58bcb-180">Your app should handle any timeouts appropriately by providing a contextual message to the user.</span></span> <span data-ttu-id="58bcb-181">Você também deve ter indicadores de progresso do usuário para fornecer comentários aos usuários sobre processos de longa duração.</span><span class="sxs-lookup"><span data-stu-id="58bcb-181">You should also user progress indicators to provide feedback to your users for any long-running processes.</span></span>

> [!NOTE]
> <span data-ttu-id="58bcb-182">As guias são habilitadas no celular somente depois que o aplicativo é adicionado a uma lista de permitir, com base na entrada da equipe de aprovação.</span><span class="sxs-lookup"><span data-stu-id="58bcb-182">Tabs are enabled on mobile only after the application is added to an allow list, based on the input of the approval team.</span></span> <span data-ttu-id="58bcb-183">Para verificar a capacidade de resposta móvel, entre em contato com teamsubm@microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="58bcb-183">To check mobile responsiveness, reach out to teamsubm@microsoft.com.</span></span>

### <a name="testing-on-mobile-clients"></a><span data-ttu-id="58bcb-184">Testes em clientes móveis</span><span class="sxs-lookup"><span data-stu-id="58bcb-184">Testing on mobile clients</span></span>

<span data-ttu-id="58bcb-185">Você precisa validar que sua guia funciona corretamente em dispositivos móveis de vários tamanhos e qualidades.</span><span class="sxs-lookup"><span data-stu-id="58bcb-185">You need to validate that your tab functions properly on mobile devices of various sizes and qualities.</span></span> <span data-ttu-id="58bcb-186">Para dispositivos Android, você pode usar [o DevTools](~/tabs/how-to/developer-tools.md) para depurar sua guia enquanto ela estiver em execução.</span><span class="sxs-lookup"><span data-stu-id="58bcb-186">For Android devices, you can use the [DevTools](~/tabs/how-to/developer-tools.md) to debug your tab while it is running.</span></span> <span data-ttu-id="58bcb-187">Recomendamos que você teste em dispositivos de alto e baixo desempenho, incluindo um tablet.</span><span class="sxs-lookup"><span data-stu-id="58bcb-187">We recommend that you test on both high- and low-performance devices, including a tablet.</span></span>

### <a name="distribution"></a><span data-ttu-id="58bcb-188">Distribuição</span><span class="sxs-lookup"><span data-stu-id="58bcb-188">Distribution</span></span>

<span data-ttu-id="58bcb-189">Os aplicativos listados no Teams devem ser aprovados para uso móvel para funcionar corretamente no cliente Teams celular.</span><span class="sxs-lookup"><span data-stu-id="58bcb-189">Apps listed on the Teams store must be approved for mobile use to function properly in the Teams mobile client.</span></span> <span data-ttu-id="58bcb-190">A disponibilidade e o comportamento de tabulação dependem da aprovação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="58bcb-190">Tab availability and behavior depends on whether your app is approved.</span></span>

#### <a name="apps-on-teams-store-approved-for-mobile"></a><span data-ttu-id="58bcb-191">Aplicativos no Teams store aprovados para dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="58bcb-191">Apps on Teams store approved for mobile</span></span>

<span data-ttu-id="58bcb-192">A tabela a seguir descreve a disponibilidade e o comportamento da guia quando o aplicativo é listado no Teams e aprovado para uso móvel:</span><span class="sxs-lookup"><span data-stu-id="58bcb-192">The following table describes tab availability and behavior when the app is listed on the Teams store and approved for mobile use:</span></span>

|<span data-ttu-id="58bcb-193">Recursos</span><span class="sxs-lookup"><span data-stu-id="58bcb-193">Capability</span></span>   |<span data-ttu-id="58bcb-194">Disponibilidade móvel?</span><span class="sxs-lookup"><span data-stu-id="58bcb-194">Mobile availability?</span></span>   |<span data-ttu-id="58bcb-195">Comportamento móvel</span><span class="sxs-lookup"><span data-stu-id="58bcb-195">Mobile behavior</span></span>|
|----------|-----------|------------|
|<span data-ttu-id="58bcb-196">Canal</span><span class="sxs-lookup"><span data-stu-id="58bcb-196">Channel</span></span> <br /> <span data-ttu-id="58bcb-197">e guia grupo</span><span class="sxs-lookup"><span data-stu-id="58bcb-197">and group tab</span></span>|<span data-ttu-id="58bcb-198">Sim</span><span class="sxs-lookup"><span data-stu-id="58bcb-198">Yes</span></span>|<span data-ttu-id="58bcb-199">A guia é aberta Teams cliente móvel usando a configuração do `contentUrl` aplicativo.</span><span class="sxs-lookup"><span data-stu-id="58bcb-199">Tab opens in the Teams mobile client using your app's `contentUrl` configuration.</span></span>|
|<span data-ttu-id="58bcb-200">Aplicativo pessoal</span><span class="sxs-lookup"><span data-stu-id="58bcb-200">Personal app</span></span>|<span data-ttu-id="58bcb-201">Sim</span><span class="sxs-lookup"><span data-stu-id="58bcb-201">Yes</span></span>|<span data-ttu-id="58bcb-202">Cada guia na guia aplicativo pessoal é aberta no cliente Teams móvel usando sua respectiva `contentUrl` configuração.</span><span class="sxs-lookup"><span data-stu-id="58bcb-202">Each tab in the personal app tab opens in the Teams mobile client using its respective `contentUrl` configuration.</span></span>|

#### <a name="apps-on-teams-store-not-approved-for-mobile"></a><span data-ttu-id="58bcb-203">Aplicativos na Teams não aprovados para dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="58bcb-203">Apps on Teams store not approved for mobile</span></span>

<span data-ttu-id="58bcb-204">A tabela a seguir descreve a disponibilidade e o comportamento da guia quando o aplicativo está listado no Teams, mas não aprovado para uso móvel:</span><span class="sxs-lookup"><span data-stu-id="58bcb-204">The following table describes tab availability and behavior when the app is listed on the Teams store but not approved for mobile use:</span></span>

| <span data-ttu-id="58bcb-205">Recursos</span><span class="sxs-lookup"><span data-stu-id="58bcb-205">Capability</span></span> | <span data-ttu-id="58bcb-206">Disponibilidade móvel?</span><span class="sxs-lookup"><span data-stu-id="58bcb-206">Mobile availability?</span></span> | <span data-ttu-id="58bcb-207">Comportamento móvel</span><span class="sxs-lookup"><span data-stu-id="58bcb-207">Mobile behavior</span></span> |
|----------|-----------|------------|
|<span data-ttu-id="58bcb-208">Guia Canal e grupo</span><span class="sxs-lookup"><span data-stu-id="58bcb-208">Channel and group tab</span></span>|<span data-ttu-id="58bcb-209">Sim</span><span class="sxs-lookup"><span data-stu-id="58bcb-209">Yes</span></span>|<span data-ttu-id="58bcb-210">A guia é aberta no navegador padrão do dispositivo, em vez do cliente Teams móvel usando a configuração do aplicativo, que também deve ser incluído na função do `websiteUrl` `setSettings()` [código-fonte.](/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest#functions&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="58bcb-210">Tab opens in the device's default browser instead of the Teams mobile client using your app's `websiteUrl` configuration, which also must be included in your source code's `setSettings()` [function](/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest#functions&preserve-view=true).</span></span> <span data-ttu-id="58bcb-211">No entanto, os usuários ainda podem exibir a guia no cliente Teams móvel selecionando **Mais** ao lado do aplicativo e escolhendo **Abrir**, o que dispara a configuração do `contentUrl` aplicativo.</span><span class="sxs-lookup"><span data-stu-id="58bcb-211">However, users can still view the tab in the Teams mobile client by selecting **More** next to the app and choosing **Open**, which triggers your app’s `contentUrl` configuration.</span></span>|
|<span data-ttu-id="58bcb-212">Aplicativo pessoal</span><span class="sxs-lookup"><span data-stu-id="58bcb-212">Personal app</span></span>|<span data-ttu-id="58bcb-213">Não</span><span class="sxs-lookup"><span data-stu-id="58bcb-213">No</span></span>|<span data-ttu-id="58bcb-214">Não aplicável</span><span class="sxs-lookup"><span data-stu-id="58bcb-214">Not applicable</span></span>|

#### <a name="apps-not-on-teams-store"></a><span data-ttu-id="58bcb-215">Aplicativos que não Teams loja</span><span class="sxs-lookup"><span data-stu-id="58bcb-215">Apps not on Teams store</span></span>

<span data-ttu-id="58bcb-216">Se você estiver fazendo sideload do seu aplicativo ou publicação no catálogo de aplicativos de uma organização, o comportamento da guia será o mesmo Teams aplicativos da loja aprovados pela Microsoft para dispositivos móveis.</span><span class="sxs-lookup"><span data-stu-id="58bcb-216">If you're sideloading your app or publishing to an org's app catalog, tab behavior will be the same as Teams store apps approved by Microsoft for mobile.</span></span>
