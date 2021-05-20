---
title: Guias em dispositivos móveis
description: Descreve as diretrizes para projetar guias que funcionam no celular.
ms.topic: conceptual
localization_priority: Normal
keywords: equipes projetam diretrizes de referência quadro de aplicativos pessoais guias móveis
ms.openlocfilehash: 853ab2c52edd1f4faedcc92e6f0e8d0821b580c7
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566695"
---
# <a name="tabs-on-mobile"></a><span data-ttu-id="27dc8-104">Guias em dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="27dc8-104">Tabs on mobile</span></span>

<span data-ttu-id="27dc8-105">Você pode incluir guias em Teams canais móveis, chats e aplicativos pessoais.</span><span class="sxs-lookup"><span data-stu-id="27dc8-105">You can include tabs in Teams mobile channels, chats, and personal apps.</span></span>

## <a name="accessing-personal-tabs"></a><span data-ttu-id="27dc8-106">Acessando guias pessoais</span><span class="sxs-lookup"><span data-stu-id="27dc8-106">Accessing personal tabs</span></span>

<span data-ttu-id="27dc8-107">Você pode acessar guias pessoais na gaveta de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="27dc8-107">You can access personal tabs in the app drawer.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-app-drawer.png" alt-text="Ilustração mostrando a Teams gaveta de aplicativos móveis." border="false":::

## <a name="accessing-channel-tabs"></a><span data-ttu-id="27dc8-109">Acessando guias de canais</span><span class="sxs-lookup"><span data-stu-id="27dc8-109">Accessing channel tabs</span></span>

<span data-ttu-id="27dc8-110">Você pode acessar guias de canais e grupos selecionando o botão **Mais** no canal ou chat no qual eles foram adicionados.</span><span class="sxs-lookup"><span data-stu-id="27dc8-110">You can access channel and group tabs by selecting the **More** button in the channel or chat in which they've been added.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab.png" alt-text="Ilustração mostrando uma guia móvel Teams." border="false":::

## <a name="design-considerations"></a><span data-ttu-id="27dc8-112">Considerações de design</span><span class="sxs-lookup"><span data-stu-id="27dc8-112">Design considerations</span></span>

<span data-ttu-id="27dc8-113">Nossa plataforma móvel permite que os aplicativos sejam uma experiência imersiva com o conteúdo do aplicativo ocupando toda a tela além da navegação principal Teams.</span><span class="sxs-lookup"><span data-stu-id="27dc8-113">Our mobile platform allows apps to be an immersive experience with the app content taking up all of the screen apart from main Teams navigation.</span></span> <span data-ttu-id="27dc8-114">Para criar uma experiência imersiva que se encaixe com Teams, siga essas diretrizes.</span><span class="sxs-lookup"><span data-stu-id="27dc8-114">To create an immersive experience that fits with Teams, follow these guidelines.</span></span>

### <a name="responsive-design"></a><span data-ttu-id="27dc8-115">Design responsivo</span><span class="sxs-lookup"><span data-stu-id="27dc8-115">Responsive design</span></span>

<span data-ttu-id="27dc8-116">Como sua guia pode ser aberta em dispositivos com uma ampla gama de tamanhos de tela, ela precisa seguir princípios [de design responsivos.](https://www.w3schools.com/html/html_responsive.asp)</span><span class="sxs-lookup"><span data-stu-id="27dc8-116">Because your tab can be opened on devices with a wide range of screen sizes, it needs to follow [responsive design](https://www.w3schools.com/html/html_responsive.asp) principles.</span></span> <span data-ttu-id="27dc8-117">Todas as construções-chave devem ser acessíveis em dispositivos móveis, e as visualizações não devem ser distorcidas.</span><span class="sxs-lookup"><span data-stu-id="27dc8-117">All of the key constructs should be accessible on mobile devices, and the views should not be distorted.</span></span> <span data-ttu-id="27dc8-118">Certifique-se de que quando sua guia estiver carregada em um dispositivo móvel, todos os botões e links são facilmente acessíveis usando navegação baseada em dedos.</span><span class="sxs-lookup"><span data-stu-id="27dc8-118">Ensure that when your tab is loaded on a mobile device, all buttons and links are easily accessible using finger-based navigation.</span></span>

### <a name="layouts"></a><span data-ttu-id="27dc8-119">Layouts</span><span class="sxs-lookup"><span data-stu-id="27dc8-119">Layouts</span></span>

<span data-ttu-id="27dc8-120">Escolher o layout correto para sua guia é importante.</span><span class="sxs-lookup"><span data-stu-id="27dc8-120">Choosing the correct layout for your tab is important.</span></span> <span data-ttu-id="27dc8-121">Você deve considerar o tipo de informação que está apresentando e escolher um layout que a organize para fácil consumo.</span><span class="sxs-lookup"><span data-stu-id="27dc8-121">You should consider the kind of information you're presenting, and choose a layout that organizes it for easy consumption.</span></span> <span data-ttu-id="27dc8-122">Algumas opções potenciais estão descritas abaixo.</span><span class="sxs-lookup"><span data-stu-id="27dc8-122">Some potential options are outlined below.</span></span>

#### <a name="single-canvas"></a><span data-ttu-id="27dc8-123">Tela única</span><span class="sxs-lookup"><span data-stu-id="27dc8-123">Single canvas</span></span>

<span data-ttu-id="27dc8-124">Esta é uma grande área onde o trabalho é feito.</span><span class="sxs-lookup"><span data-stu-id="27dc8-124">This is one large area where work gets done.</span></span> <span data-ttu-id="27dc8-125">O aplicativo wiki Teams segue esse padrão.</span><span class="sxs-lookup"><span data-stu-id="27dc8-125">The Teams Wiki app follows this pattern.</span></span> <span data-ttu-id="27dc8-126">Se você tem um aplicativo que não separa o conteúdo em componentes menores, isso seria um bom ajuste.</span><span class="sxs-lookup"><span data-stu-id="27dc8-126">If you have an app that doesn’t separate content into smaller components this would be a good fit.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-single-canvas.png" alt-text="Ilustração mostrando uma Teams guia de tela única móvel." border="false":::

#### <a name="list"></a><span data-ttu-id="27dc8-128">List</span><span class="sxs-lookup"><span data-stu-id="27dc8-128">List</span></span>

<span data-ttu-id="27dc8-129">As listas são ótimas para classificar e filtrar grandes quantidades de dados e são ótimas para manter as coisas mais importantes no topo.</span><span class="sxs-lookup"><span data-stu-id="27dc8-129">Lists are great for sorting and filtering large quantities of data and are great at keeping the most important things at the top.</span></span> <span data-ttu-id="27dc8-130">É útil usar colunas classificadas.</span><span class="sxs-lookup"><span data-stu-id="27dc8-130">It is helpful to use sortable columns.</span></span> <span data-ttu-id="27dc8-131">As ações podem ser adicionadas a cada item da lista no menu elipse.</span><span class="sxs-lookup"><span data-stu-id="27dc8-131">Actions can be added to each list item under the ellipsis menu.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-list.png" alt-text="Ilustração mostrando uma guia de lista de celular Teams." border="false":::

#### <a name="grid"></a><span data-ttu-id="27dc8-133">grade</span><span class="sxs-lookup"><span data-stu-id="27dc8-133">Grid</span></span>

<span data-ttu-id="27dc8-134">Grades são úteis para mostrar elementos altamente visuais.</span><span class="sxs-lookup"><span data-stu-id="27dc8-134">Grids are useful for showing elements which are highly visual.</span></span> <span data-ttu-id="27dc8-135">Ajuda a incluir um filtro ou controle de pesquisa na parte superior.</span><span class="sxs-lookup"><span data-stu-id="27dc8-135">It helps to include a filter or search control at the top.</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-grid.png" alt-text="Ilustração mostrando uma guia móvel Teams com um layout de grade." border="false":::

### <a name="tabs-with-bots-on-mobile"></a><span data-ttu-id="27dc8-137">Guias com bots no celular</span><span class="sxs-lookup"><span data-stu-id="27dc8-137">Tabs with bots on mobile</span></span>

<span data-ttu-id="27dc8-138">O exemplo a seguir é um aplicativo pessoal que tem guias e um bot:</span><span class="sxs-lookup"><span data-stu-id="27dc8-138">The following example is a personal app that has tabs and a bot:</span></span>

:::image type="content" source="../../assets/images/tabs/mobile-tab-with-bot.png" alt-text="Ilustração mostrando como o aplicativo de Teams móvel que tem guias e um bot." border="false":::

## <a name="ui-components"></a><span data-ttu-id="27dc8-140">Componentes de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="27dc8-140">UI components</span></span>

### <a name="color-palettes"></a><span data-ttu-id="27dc8-141">Paletas de cores</span><span class="sxs-lookup"><span data-stu-id="27dc8-141">Color palettes</span></span>

<span data-ttu-id="27dc8-142">Usar nossa paleta neutra aprovada para dados, notificações, texto e botões ajudará seu aplicativo a se sentir mais em casa em Teams.</span><span class="sxs-lookup"><span data-stu-id="27dc8-142">Using our approved neutral palette for backgrounds, notifications, text, and buttons will help your app feel more at home in Teams.</span></span> <span data-ttu-id="27dc8-143">Como Teams celular tem dois temas de cores (claro e escuro), é uma boa ideia garantir que seu aplicativo fique ótimo em ambos.</span><span class="sxs-lookup"><span data-stu-id="27dc8-143">Since Teams mobile has two colour themes (light and dark), it’s a good idea to make sure your app looks great in both.</span></span>

#### <a name="light-color"></a><span data-ttu-id="27dc8-144">Cor clara</span><span class="sxs-lookup"><span data-stu-id="27dc8-144">Light color</span></span>

![paleta de cores claras](../../assets/images/light-color.png)

#### <a name="dark-color"></a><span data-ttu-id="27dc8-146">Cor escura</span><span class="sxs-lookup"><span data-stu-id="27dc8-146">Dark color</span></span>

![paleta de cores escuras](../../assets/images/dark-color.png)

### <a name="buttons-and-controls"></a><span data-ttu-id="27dc8-148">Botões e controles</span><span class="sxs-lookup"><span data-stu-id="27dc8-148">Buttons and controls</span></span>

<span data-ttu-id="27dc8-149">A forma como os botões são estilizados ajuda a comunicar que tipo de ação eles acionam.</span><span class="sxs-lookup"><span data-stu-id="27dc8-149">The way buttons are styled helps communicate what kind of action they trigger.</span></span> <span data-ttu-id="27dc8-150">Mantemos uma ampla gama de botões que são formatados para mostrar diferentes níveis de ênfase.</span><span class="sxs-lookup"><span data-stu-id="27dc8-150">We maintain a wide range of buttons that are formatted to show different levels of emphasis.</span></span> <span data-ttu-id="27dc8-151">Os botões podem ter texto, um ícone ou uma combinação de texto e um ícone.</span><span class="sxs-lookup"><span data-stu-id="27dc8-151">Buttons can have text, an icon, or a combination of text and an icon.</span></span> <span data-ttu-id="27dc8-152">Para comunicar diferentes níveis em uma hierarquia, projetamos botões primários e secundários dentro de cada categoria.</span><span class="sxs-lookup"><span data-stu-id="27dc8-152">To communicate different levels in a hierarchy, we designed primary and secondary buttons within each category.</span></span>

#### <a name="buttons"></a><span data-ttu-id="27dc8-153">Botões</span><span class="sxs-lookup"><span data-stu-id="27dc8-153">Buttons</span></span>

<span data-ttu-id="27dc8-154">Botões primários e secundários.</span><span class="sxs-lookup"><span data-stu-id="27dc8-154">Primary and secondary buttons.</span></span>

![imagem botões](../../assets/images/buttons.png)

#### <a name="selection-controls"></a><span data-ttu-id="27dc8-156">Controles de seleção</span><span class="sxs-lookup"><span data-stu-id="27dc8-156">Selection controls</span></span>

<span data-ttu-id="27dc8-157">Botões de rádio, caixas de seleção e alternâncias.</span><span class="sxs-lookup"><span data-stu-id="27dc8-157">Radio buttons, checkboxes, and toggles.</span></span>

![controles de seleção](../../assets/images/selection-controls.png)

#### <a name="chiclets-and-pills"></a><span data-ttu-id="27dc8-159">Chiclets e pílulas</span><span class="sxs-lookup"><span data-stu-id="27dc8-159">Chiclets and pills</span></span>

![chiclets e pílulas](../../assets/images/chiclets-and-pills.png)

### <a name="typography"></a><span data-ttu-id="27dc8-161">Tipografia</span><span class="sxs-lookup"><span data-stu-id="27dc8-161">Typography</span></span>

<span data-ttu-id="27dc8-162">A tipografia deve ser clara e proposital.</span><span class="sxs-lookup"><span data-stu-id="27dc8-162">Typography should be clear and purposeful.</span></span> <span data-ttu-id="27dc8-163">Enfatize informações importantes e evite o uso de várias fontes e tamanhos para reduzir a confusão.</span><span class="sxs-lookup"><span data-stu-id="27dc8-163">Emphasize important information and avoid using multiple fonts and sizes to reduce confusion.</span></span> <span data-ttu-id="27dc8-164">Recomendamos o uso de casos de sentença e evitar o uso de todas as tampas para localização e legibilidade.</span><span class="sxs-lookup"><span data-stu-id="27dc8-164">We recommend using sentence case and avoiding the usage of all caps for localization and legibility.</span></span>

![tipógrafo móvel](../../assets/images/mobile-typography.png)

### <a name="fields-and-flyouts"></a><span data-ttu-id="27dc8-166">Campos e flyouts</span><span class="sxs-lookup"><span data-stu-id="27dc8-166">Fields and flyouts</span></span>

<span data-ttu-id="27dc8-167">Campos são áreas onde os usuários podem inserir texto.</span><span class="sxs-lookup"><span data-stu-id="27dc8-167">Fields are areas where users can input text.</span></span> <span data-ttu-id="27dc8-168">Os flyouts são mais leves do que os diálogos e aparecem do painel superior.</span><span class="sxs-lookup"><span data-stu-id="27dc8-168">Flyouts are more lightweight than dialogs and appear from the top pane.</span></span>

#### <a name="list-controls"></a><span data-ttu-id="27dc8-169">Controles de lista</span><span class="sxs-lookup"><span data-stu-id="27dc8-169">List controls</span></span>

![controles de lista móvel](../../assets/images/mobile-list-controls.png)

#### <a name="field-controls"></a><span data-ttu-id="27dc8-171">Controles de campo</span><span class="sxs-lookup"><span data-stu-id="27dc8-171">Field controls</span></span>

![controles de campo móveis](../../assets/images/mobile-field-controls.png)

## <a name="developer-considerations"></a><span data-ttu-id="27dc8-173">Considerações do desenvolvedor</span><span class="sxs-lookup"><span data-stu-id="27dc8-173">Developer considerations</span></span>

<span data-ttu-id="27dc8-174">Quando você está construindo um aplicativo que inclui uma guia, você precisa considerar (e testar) como sua guia funcionará tanto no Clientes Microsoft Teams Android quanto no iOS.</span><span class="sxs-lookup"><span data-stu-id="27dc8-174">When you're building an app that includes a tab, you need to consider (and test) how your tab will function on both the Android and iOS Microsoft Teams clients.</span></span> <span data-ttu-id="27dc8-175">As seções abaixo descrevem alguns dos principais cenários que você precisa considerar.</span><span class="sxs-lookup"><span data-stu-id="27dc8-175">The sections below outline some of the key scenarios you need to consider.</span></span>

### <a name="authentication"></a><span data-ttu-id="27dc8-176">Autenticação</span><span class="sxs-lookup"><span data-stu-id="27dc8-176">Authentication</span></span>

<span data-ttu-id="27dc8-177">Para que a autenticação funcione em clientes móveis, você deve atualizá-lo Teams JavaScript SDK para pelo menos a versão 1.4.1.</span><span class="sxs-lookup"><span data-stu-id="27dc8-177">For authentication to work on mobile clients, you must upgrade you Teams JavaScript SDK to at least version 1.4.1.</span></span>

### <a name="low-bandwidth-and-intermittent-connections"></a><span data-ttu-id="27dc8-178">Baixa largura de banda e conexões intermitentes</span><span class="sxs-lookup"><span data-stu-id="27dc8-178">Low bandwidth and intermittent connections</span></span>

<span data-ttu-id="27dc8-179">Os clientes móveis precisam funcionar regularmente com baixa largura de banda e conexões intermitentes.</span><span class="sxs-lookup"><span data-stu-id="27dc8-179">Mobile clients regularly need to function with low bandwidth and intermittent connections.</span></span> <span data-ttu-id="27dc8-180">Seu aplicativo deve lidar com quaisquer intervalos apropriadamente, fornecendo uma mensagem contextual ao usuário.</span><span class="sxs-lookup"><span data-stu-id="27dc8-180">Your app should handle any timeouts appropriately by providing a contextual message to the user.</span></span> <span data-ttu-id="27dc8-181">Você também deve fornecer indicadores de progresso para fornecer feedback aos seus usuários para quaisquer processos de longo prazo.</span><span class="sxs-lookup"><span data-stu-id="27dc8-181">You should also user progress indicators to provide feedback to your users for any long-running processes.</span></span>

> [!NOTE]
> <span data-ttu-id="27dc8-182">As guias são habilitadas no celular somente após o aplicativo ser adicionado a uma lista de permissões, com base na entrada da equipe de aprovação.</span><span class="sxs-lookup"><span data-stu-id="27dc8-182">Tabs are enabled on mobile only after the application is added to an allow list, based on the input of the approval team.</span></span> <span data-ttu-id="27dc8-183">Para verificar a capacidade de resposta móvel, entre em contato com teamsubm@microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="27dc8-183">To check mobile responsiveness, reach out to teamsubm@microsoft.com.</span></span>

### <a name="testing-on-mobile-clients"></a><span data-ttu-id="27dc8-184">Testes em clientes móveis</span><span class="sxs-lookup"><span data-stu-id="27dc8-184">Testing on mobile clients</span></span>

<span data-ttu-id="27dc8-185">Você precisa validar que sua guia funciona corretamente em dispositivos móveis de vários tamanhos e qualidades.</span><span class="sxs-lookup"><span data-stu-id="27dc8-185">You need to validate that your tab functions properly on mobile devices of various sizes and qualities.</span></span> <span data-ttu-id="27dc8-186">Para dispositivos Android, você pode usar o [DevTools](~/tabs/how-to/developer-tools.md) para depurar sua guia enquanto ela está em execução.</span><span class="sxs-lookup"><span data-stu-id="27dc8-186">For Android devices, you can use the [DevTools](~/tabs/how-to/developer-tools.md) to debug your tab while it is running.</span></span> <span data-ttu-id="27dc8-187">Recomendamos que você teste em dispositivos de alto e baixo desempenho, incluindo um tablet.</span><span class="sxs-lookup"><span data-stu-id="27dc8-187">We recommend that you test on both high- and low-performance devices, including a tablet.</span></span>

### <a name="distribution"></a><span data-ttu-id="27dc8-188">distribuição</span><span class="sxs-lookup"><span data-stu-id="27dc8-188">Distribution</span></span>

<span data-ttu-id="27dc8-189">Os aplicativos listados na loja Teams devem ser aprovados para que o uso do celular funcione corretamente no Teams cliente móvel.</span><span class="sxs-lookup"><span data-stu-id="27dc8-189">Apps listed on the Teams store must be approved for mobile use to function properly in the Teams mobile client.</span></span> <span data-ttu-id="27dc8-190">A disponibilidade e o comportamento da guia dependem se seu aplicativo é aprovado.</span><span class="sxs-lookup"><span data-stu-id="27dc8-190">Tab availability and behavior depends on whether your app is approved.</span></span>

#### <a name="apps-on-teams-store-approved-for-mobile"></a><span data-ttu-id="27dc8-191">Aplicativos na loja Teams aprovados para celular</span><span class="sxs-lookup"><span data-stu-id="27dc8-191">Apps on Teams store approved for mobile</span></span>

<span data-ttu-id="27dc8-192">A tabela a seguir descreve a disponibilidade e o comportamento da guia quando o aplicativo está listado na loja Teams e aprovado para uso móvel:</span><span class="sxs-lookup"><span data-stu-id="27dc8-192">The following table describes tab availability and behavior when the app is listed on the Teams store and approved for mobile use:</span></span>

|<span data-ttu-id="27dc8-193">Recursos</span><span class="sxs-lookup"><span data-stu-id="27dc8-193">Capability</span></span>   |<span data-ttu-id="27dc8-194">Disponibilidade móvel?</span><span class="sxs-lookup"><span data-stu-id="27dc8-194">Mobile availability?</span></span>   |<span data-ttu-id="27dc8-195">Comportamento móvel</span><span class="sxs-lookup"><span data-stu-id="27dc8-195">Mobile behavior</span></span>|
|----------|-----------|------------|
|<span data-ttu-id="27dc8-196">Canal</span><span class="sxs-lookup"><span data-stu-id="27dc8-196">Channel</span></span> <br /> <span data-ttu-id="27dc8-197">e aba de grupo</span><span class="sxs-lookup"><span data-stu-id="27dc8-197">and group tab</span></span>|<span data-ttu-id="27dc8-198">Sim</span><span class="sxs-lookup"><span data-stu-id="27dc8-198">Yes</span></span>|<span data-ttu-id="27dc8-199">A guia é aberta no Teams cliente móvel usando a configuração do seu `contentUrl` aplicativo.</span><span class="sxs-lookup"><span data-stu-id="27dc8-199">Tab opens in the Teams mobile client using your app's `contentUrl` configuration.</span></span>|
|<span data-ttu-id="27dc8-200">Aplicativo pessoal</span><span class="sxs-lookup"><span data-stu-id="27dc8-200">Personal app</span></span>|<span data-ttu-id="27dc8-201">Sim</span><span class="sxs-lookup"><span data-stu-id="27dc8-201">Yes</span></span>|<span data-ttu-id="27dc8-202">Cada guia na guia do aplicativo pessoal é aberta no Teams cliente móvel usando sua respectiva `contentUrl` configuração.</span><span class="sxs-lookup"><span data-stu-id="27dc8-202">Each tab in the personal app tab opens in the Teams mobile client using its respective `contentUrl` configuration.</span></span>|

#### <a name="apps-on-teams-store-not-approved-for-mobile"></a><span data-ttu-id="27dc8-203">Aplicativos na loja Teams não aprovados para celular</span><span class="sxs-lookup"><span data-stu-id="27dc8-203">Apps on Teams store not approved for mobile</span></span>

<span data-ttu-id="27dc8-204">A tabela a seguir descreve a disponibilidade e o comportamento da guia quando o aplicativo está listado na loja Teams, mas não aprovado para uso móvel:</span><span class="sxs-lookup"><span data-stu-id="27dc8-204">The following table describes tab availability and behavior when the app is listed on the Teams store but not approved for mobile use:</span></span>

| <span data-ttu-id="27dc8-205">Recursos</span><span class="sxs-lookup"><span data-stu-id="27dc8-205">Capability</span></span> | <span data-ttu-id="27dc8-206">Disponibilidade móvel?</span><span class="sxs-lookup"><span data-stu-id="27dc8-206">Mobile availability?</span></span> | <span data-ttu-id="27dc8-207">Comportamento móvel</span><span class="sxs-lookup"><span data-stu-id="27dc8-207">Mobile behavior</span></span> |
|----------|-----------|------------|
|<span data-ttu-id="27dc8-208">Guia de canal e grupo</span><span class="sxs-lookup"><span data-stu-id="27dc8-208">Channel and group tab</span></span>|<span data-ttu-id="27dc8-209">Sim</span><span class="sxs-lookup"><span data-stu-id="27dc8-209">Yes</span></span>|<span data-ttu-id="27dc8-210">A guia é aberta no navegador padrão do dispositivo em vez do Teams cliente móvel usando a configuração do seu `websiteUrl` aplicativo, que também deve ser incluída na função do seu código fonte `setSettings()` [](/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest#functions&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="27dc8-210">Tab opens in the device's default browser instead of the Teams mobile client using your app's `websiteUrl` configuration, which also must be included in your source code's `setSettings()` [function](/javascript/api/@microsoft/teams-js/settings?view=msteams-client-js-latest#functions&preserve-view=true).</span></span> <span data-ttu-id="27dc8-211">No entanto, os usuários ainda podem visualizar a guia no Teams cliente móvel selecionando **Mais** ao lado do aplicativo e escolhendo **Open**, o que aciona a configuração do seu `contentUrl` aplicativo.</span><span class="sxs-lookup"><span data-stu-id="27dc8-211">However, users can still view the tab in the Teams mobile client by selecting **More** next to the app and choosing **Open**, which triggers your app’s `contentUrl` configuration.</span></span>|
|<span data-ttu-id="27dc8-212">Aplicativo pessoal</span><span class="sxs-lookup"><span data-stu-id="27dc8-212">Personal app</span></span>|<span data-ttu-id="27dc8-213">Não</span><span class="sxs-lookup"><span data-stu-id="27dc8-213">No</span></span>|<span data-ttu-id="27dc8-214">Não aplicável</span><span class="sxs-lookup"><span data-stu-id="27dc8-214">Not applicable</span></span>|

#### <a name="apps-not-on-teams-store"></a><span data-ttu-id="27dc8-215">Aplicativos que não estão na loja Teams</span><span class="sxs-lookup"><span data-stu-id="27dc8-215">Apps not on Teams store</span></span>

<span data-ttu-id="27dc8-216">Se você estiver carregando seu aplicativo ou publicando para o catálogo de aplicativos de uma organização, o comportamento da guia será o mesmo que Teams aplicativos de loja aprovados pela Microsoft para dispositivos móveis.</span><span class="sxs-lookup"><span data-stu-id="27dc8-216">If you're sideloading your app or publishing to an org's app catalog, tab behavior will be the same as Teams store apps approved by Microsoft for mobile.</span></span>
