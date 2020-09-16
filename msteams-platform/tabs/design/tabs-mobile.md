---
title: Guias em dispositivos móveis
description: Descreve as diretrizes para a criação de guias que funcionam em dispositivos móveis.
keywords: Diretrizes de design de equipes guias de referência de aplicativos pessoais
ms.openlocfilehash: d47039c245b8e262af6e1f60bc0c644dc7e65bd6
ms.sourcegitcommit: e8dfcb167274e996395b77d65999991a18f2051a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "47819043"
---
# <a name="tabs-on-mobile"></a><span data-ttu-id="fc870-104">Guias em dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="fc870-104">Tabs on mobile</span></span>

> [!NOTE]
> <span data-ttu-id="fc870-105">Se você optar por ter a guia canal/grupo exibida em clientes móveis do Microsoft Teams, a `setSettings()` configuração deverá ter um valor para a `websiteUrl` Propriedade (veja abaixo).</span><span class="sxs-lookup"><span data-stu-id="fc870-105">If you choose to have your channel/group tab appear on Teams mobile clients, the `setSettings()` configuration must have a value for the `websiteUrl` property (see below).</span></span>

<span data-ttu-id="fc870-106">As guias personalizadas podem fazer parte de um canal, de um chat de grupo ou de um aplicativo pessoal (aplicativos que contêm guias estáticas e/ou um bot de um para um).</span><span class="sxs-lookup"><span data-stu-id="fc870-106">Custom tabs can be part of a channel, group chat, or personal app (apps that contain static tabs and/or a one-to-one bot).</span></span>

<span data-ttu-id="fc870-107">Os aplicativos pessoais estão disponíveis em clientes móveis na gaveta de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="fc870-107">Personal apps are available on mobile clients in the App Drawer.</span></span> <span data-ttu-id="fc870-108">O aplicativo só pode ser instalado a partir de um cliente da Web ou da área de trabalho, e pode levar até 24 horas para aparecer em clientes móveis.</span><span class="sxs-lookup"><span data-stu-id="fc870-108">The app can only be installed from a desktop or web client, and can take up to 24 hours to appear on mobile clients.</span></span>

<span data-ttu-id="fc870-109">As guias de grupo e canal também estão disponíveis em clientes móveis.</span><span class="sxs-lookup"><span data-stu-id="fc870-109">Group and channel tabs are available on mobile clients as well.</span></span> <span data-ttu-id="fc870-110">O comportamento padrão é atualmente usar o `websiteUrl` para iniciar sua guia em uma janela do navegador.</span><span class="sxs-lookup"><span data-stu-id="fc870-110">The default behavior is currently to use your `websiteUrl` to launch your tab in a browser window.</span></span> <span data-ttu-id="fc870-111">No entanto, eles podem ser carregados em um cliente móvel clicando no `...` menu de excedentes ao lado da guia e escolhendo **abrir**, que usará o `contentUrl` para carregar a guia dentro do cliente móvel do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="fc870-111">However, they can be loaded on a mobile client by clicking the `...` overflow menu next to the tab and choosing **Open**, which will use your `contentUrl` to load the tab inside the Teams mobile client.</span></span>

![gaveta de aplicativos móveis](../../assets/images/personal-app-mobile.png)

## <a name="developer-considerations-for-mobile-support"></a><span data-ttu-id="fc870-113">Considerações de desenvolvedor para suporte móvel</span><span class="sxs-lookup"><span data-stu-id="fc870-113">Developer considerations for mobile support</span></span>

<span data-ttu-id="fc870-114">Ao criar um aplicativo que inclua uma guia, você precisa considerar (e testar) como sua guia funcionará nos clientes do Microsoft Teams Android e iOS.</span><span class="sxs-lookup"><span data-stu-id="fc870-114">When you're building an app that includes a tab, you need to consider (and test) how your tab will function on both the Android and iOS Microsoft Teams clients.</span></span> <span data-ttu-id="fc870-115">As seções a seguir descrevem alguns dos principais cenários que você precisa considerar.</span><span class="sxs-lookup"><span data-stu-id="fc870-115">The sections below outline some of the key scenarios you need to consider.</span></span>

### <a name="testing-on-mobile-clients"></a><span data-ttu-id="fc870-116">Testando clientes móveis</span><span class="sxs-lookup"><span data-stu-id="fc870-116">Testing on mobile clients</span></span>

<span data-ttu-id="fc870-117">Você precisa validar que sua guia funciona corretamente em dispositivos móveis de vários tamanhos e qualidades.</span><span class="sxs-lookup"><span data-stu-id="fc870-117">You need to validate that your tab functions properly on mobile devices of various sizes and qualities.</span></span> <span data-ttu-id="fc870-118">Para dispositivos Android, você pode usar o [devtools](~/tabs/how-to/developer-tools.md) para depurar sua guia enquanto estiver sendo executado.</span><span class="sxs-lookup"><span data-stu-id="fc870-118">For Android devices you can use the [DevTools](~/tabs/how-to/developer-tools.md) to debug your tab while it is running.</span></span> <span data-ttu-id="fc870-119">Recomendamos que você teste em dispositivos de desempenho alto e baixo, bem como em um Tablet.</span><span class="sxs-lookup"><span data-stu-id="fc870-119">We recommend that you test on both high and low performing devices, as well as on a tablet.</span></span>

### <a name="responsive-design"></a><span data-ttu-id="fc870-120">Design responsivo</span><span class="sxs-lookup"><span data-stu-id="fc870-120">Responsive design</span></span>

<span data-ttu-id="fc870-121">Como sua guia pode ser aberta em dispositivos com uma ampla variedade de tamanhos de tela, é necessário seguir princípios de [design responsivos](https://www.w3schools.com/html/html_responsive.asp) .</span><span class="sxs-lookup"><span data-stu-id="fc870-121">Because your tab can be opened on devices with a wide range of screen sizes, it needs to follow [responsive design](https://www.w3schools.com/html/html_responsive.asp) principles.</span></span> <span data-ttu-id="fc870-122">Todas as construções de chave devem estar acessíveis em dispositivos móveis, e os modos de exibição não devem ser distorcidos.</span><span class="sxs-lookup"><span data-stu-id="fc870-122">All of the key constructs should be accessible on mobile devices, and the views should not be distorted.</span></span> <span data-ttu-id="fc870-123">Verifique se a guia é carregada em um dispositivo móvel, se todos os botões e links estão facilmente acessíveis usando a navegação baseada em Finger.</span><span class="sxs-lookup"><span data-stu-id="fc870-123">Ensure that when your tab is loaded on a mobile device, all buttons and links are easily accessible using finger-based navigation.</span></span>

### <a name="authentication"></a><span data-ttu-id="fc870-124">Autenticação</span><span class="sxs-lookup"><span data-stu-id="fc870-124">Authentication</span></span>

<span data-ttu-id="fc870-125">Para que a autenticação funcione em clientes móveis, você deve atualizar o SDK do teams JS para pelo menos a versão 1.4.1.</span><span class="sxs-lookup"><span data-stu-id="fc870-125">For authentication to work on mobile clients, you must upgrade you Teams JS SDK to at least version 1.4.1.</span></span>

### <a name="low-bandwidth--intermittent-connections"></a><span data-ttu-id="fc870-126">Baixa largura de banda & conexões intermitentes</span><span class="sxs-lookup"><span data-stu-id="fc870-126">Low bandwidth & intermittent connections</span></span>

<span data-ttu-id="fc870-127">Os clientes móveis precisam funcionar regularmente com baixa largura de banda e conexões intermitentes.</span><span class="sxs-lookup"><span data-stu-id="fc870-127">Mobile clients regularly need to function with low bandwidth and intermittent connections.</span></span> <span data-ttu-id="fc870-128">Seu aplicativo deve lidar com os tempos limite de forma adequada fornecendo uma mensagem contextual para o usuário.</span><span class="sxs-lookup"><span data-stu-id="fc870-128">Your app should handle any timeouts appropriately by providing a contextual message to the user.</span></span> <span data-ttu-id="fc870-129">Você também deve fazer os indicadores de progresso do usuário para fornecer comentários aos seus usuários para todos os processos de execução demorada.</span><span class="sxs-lookup"><span data-stu-id="fc870-129">You should also user progress indicators to provide feedback to your users for any long-running processes.</span></span>

## <a name="design-considerations-for-mobile"></a><span data-ttu-id="fc870-130">Considerações de design para dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="fc870-130">Design considerations for mobile</span></span>

<span data-ttu-id="fc870-131">Nossa plataforma móvel permite que os aplicativos sejam uma experiência de imersão com o conteúdo do aplicativo tirando toda a tela da navegação do teams principal.</span><span class="sxs-lookup"><span data-stu-id="fc870-131">Our mobile platform allows apps to be an immersive experience with the app content taking up all of the screen apart from main Teams navigation.</span></span> <span data-ttu-id="fc870-132">Para criar uma experiência de imersão que se ajuste perfeitamente no cliente Microsoft Teams, siga as diretrizes abaixo.</span><span class="sxs-lookup"><span data-stu-id="fc870-132">To create an immersive experience that fits seamlessly within the Microsoft Teams client, follow the guidelines below.</span></span>

### <a name="layouts"></a><span data-ttu-id="fc870-133">Layouts</span><span class="sxs-lookup"><span data-stu-id="fc870-133">Layouts</span></span>

<span data-ttu-id="fc870-134">Escolher o layout correto para sua guia é importante.</span><span class="sxs-lookup"><span data-stu-id="fc870-134">Choosing the correct layout for your tab is important.</span></span> <span data-ttu-id="fc870-135">Considere o tipo de informação que você está apresentando e escolha um layout que a organize para facilitar o consumo.</span><span class="sxs-lookup"><span data-stu-id="fc870-135">You should consider the kind of information you're presenting, and choose a layout that organizes it for easy consumption.</span></span> <span data-ttu-id="fc870-136">Algumas opções potenciais estão descritas abaixo.</span><span class="sxs-lookup"><span data-stu-id="fc870-136">Some potential options are outlined below.</span></span>

#### <a name="single-canvas"></a><span data-ttu-id="fc870-137">Tela única</span><span class="sxs-lookup"><span data-stu-id="fc870-137">Single canvas</span></span>

<span data-ttu-id="fc870-138">Esta é uma grande área onde o trabalho é concluído.</span><span class="sxs-lookup"><span data-stu-id="fc870-138">This is one large area where work gets done.</span></span> <span data-ttu-id="fc870-139">O aplicativo wiki segue esse padrão.</span><span class="sxs-lookup"><span data-stu-id="fc870-139">The Wiki app follows this pattern.</span></span> <span data-ttu-id="fc870-140">Se você tiver um aplicativo que não separa o conteúdo em componentes menores, isso seria um bom ajuste.</span><span class="sxs-lookup"><span data-stu-id="fc870-140">If you have an app that doesn’t separate content into smaller components this would be a good fit.</span></span>

![layout de tela única](~/assets/images/mobile-single-canvas.png)

#### <a name="list"></a><span data-ttu-id="fc870-142">Listar</span><span class="sxs-lookup"><span data-stu-id="fc870-142">List</span></span>

<span data-ttu-id="fc870-143">As listas são ótimas para classificar e filtrar grandes quantidades de dados e são excelentes para manter as coisas mais importantes na parte superior.</span><span class="sxs-lookup"><span data-stu-id="fc870-143">Lists are great for sorting and filtering large quantities of data and are great at keeping the most important things at the top.</span></span> <span data-ttu-id="fc870-144">É útil usar colunas classificável.</span><span class="sxs-lookup"><span data-stu-id="fc870-144">It is helpful to use sortable columns.</span></span> <span data-ttu-id="fc870-145">As ações podem ser adicionadas a cada item de lista no menu de reticências.</span><span class="sxs-lookup"><span data-stu-id="fc870-145">Actions can be added to each list item under the ellipsis menu.</span></span>

![layout de lista](~/assets/images/mobile-list.png)

#### <a name="grid"></a><span data-ttu-id="fc870-147">Encaixe</span><span class="sxs-lookup"><span data-stu-id="fc870-147">Grid</span></span>

<span data-ttu-id="fc870-148">As grades são úteis para mostrar elementos que são altamente visuais.</span><span class="sxs-lookup"><span data-stu-id="fc870-148">Grids are useful for showing elements which are highly visual.</span></span> <span data-ttu-id="fc870-149">Ele ajuda a incluir um filtro ou controle de pesquisa na parte superior.</span><span class="sxs-lookup"><span data-stu-id="fc870-149">It helps to include a filter or search control at the top.</span></span>

![layout de grade](~/assets/images/mobile-grid.png)

### <a name="tabs-with-bots-on-mobile"></a><span data-ttu-id="fc870-151">Guias com bots em dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="fc870-151">Tabs with bots on mobile</span></span>

<span data-ttu-id="fc870-152">Veja a seguir um exemplo de aplicativo pessoal que contém duas guias estáticas e um bot.</span><span class="sxs-lookup"><span data-stu-id="fc870-152">The below is an example personal app that contains two static tabs and a bot.</span></span>

![guias e bots em dispositivos móveis](~/assets/images/mobile-tab-with-bot.png)

### <a name="ui-components"></a><span data-ttu-id="fc870-154">Componentes da interface de usuário</span><span class="sxs-lookup"><span data-stu-id="fc870-154">UI Components</span></span>

#### <a name="color-palettes"></a><span data-ttu-id="fc870-155">Paletas de cores</span><span class="sxs-lookup"><span data-stu-id="fc870-155">Color palettes</span></span>

<span data-ttu-id="fc870-156">Usar nossa paleta neutra aprovada para planos de fundo, notificações, texto e botões ajudará seu aplicativo a se sentir mais em casa no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="fc870-156">Using our approved neutral palette for backgrounds, notifications, text, and buttons will help your app feel more at home in Teams.</span></span> <span data-ttu-id="fc870-157">Como o Microsoft Teams Mobile tem dois temas de cor (claro e escuro), é uma boa ideia garantir que seu aplicativo fique ótimo em ambos.</span><span class="sxs-lookup"><span data-stu-id="fc870-157">Since Teams mobile has two colour themes (light and dark), it’s a good idea to make sure your app looks great in both.</span></span>

##### <a name="light-color"></a><span data-ttu-id="fc870-158">Cor clara</span><span class="sxs-lookup"><span data-stu-id="fc870-158">Light color</span></span>

![paleta de cores claras](~/assets/images/light-color.png)

##### <a name="dark-color"></a><span data-ttu-id="fc870-160">Cor escura</span><span class="sxs-lookup"><span data-stu-id="fc870-160">Dark color</span></span>

![paleta de cores escuras](~/assets/images/dark-color.png)

#### <a name="buttons-and-controls"></a><span data-ttu-id="fc870-162">Botões e controles</span><span class="sxs-lookup"><span data-stu-id="fc870-162">Buttons and controls</span></span>

<span data-ttu-id="fc870-163">A maneira como os botões são estilizados ajuda a comunicar o tipo de ação que eles disparam.</span><span class="sxs-lookup"><span data-stu-id="fc870-163">The way buttons are styled helps communicate what kind of action they trigger.</span></span> <span data-ttu-id="fc870-164">Mantemos uma ampla variedade de botões formatados para mostrar diferentes níveis de ênfase.</span><span class="sxs-lookup"><span data-stu-id="fc870-164">We maintain a wide range of buttons that are formatted to show different levels of emphasis.</span></span> <span data-ttu-id="fc870-165">Os botões podem ter texto, um ícone ou uma combinação de texto e um ícone.</span><span class="sxs-lookup"><span data-stu-id="fc870-165">Buttons can have text, an icon, or a combination of text and an icon.</span></span> <span data-ttu-id="fc870-166">Para comunicar diferentes níveis em uma hierarquia, projetamos os botões principal e secundário dentro de cada categoria.</span><span class="sxs-lookup"><span data-stu-id="fc870-166">To communicate different levels in a hierarchy, we designed primary and secondary buttons within each category.</span></span>

![imagem de botões](~/assets/images/buttons.png)

![controles de seleção](~/assets/images/selection-controls.png)

![Chiclets e pills](~/assets/images/chiclets-and-pills.png)

#### <a name="typography"></a><span data-ttu-id="fc870-170">Tipografia</span><span class="sxs-lookup"><span data-stu-id="fc870-170">Typography</span></span>

<span data-ttu-id="fc870-171">A tipografia deve ser clara e proposital.</span><span class="sxs-lookup"><span data-stu-id="fc870-171">Typography should be clear and purposeful.</span></span> <span data-ttu-id="fc870-172">Enfatize informações importantes e evite usar várias fontes e tamanhos para reduzir a confusão.</span><span class="sxs-lookup"><span data-stu-id="fc870-172">Emphasize important information and avoid using multiple fonts and sizes to reduce confusion.</span></span> <span data-ttu-id="fc870-173">Recomendamos o uso de maiúsculas e minúsculas e evitar o uso de todos os Caps para a localização e a legibilidade.</span><span class="sxs-lookup"><span data-stu-id="fc870-173">We recommend using sentence case and avoiding the usage of all caps for localization and legibility.</span></span>

![Typograph móvel](~/assets/images/mobile-typography.png)

#### <a name="fields-and-flyouts"></a><span data-ttu-id="fc870-175">Campos e submenus</span><span class="sxs-lookup"><span data-stu-id="fc870-175">Fields and Flyouts</span></span>

<span data-ttu-id="fc870-176">Os campos são áreas onde os usuários podem inserir texto.</span><span class="sxs-lookup"><span data-stu-id="fc870-176">Fields are areas where users can input text.</span></span> <span data-ttu-id="fc870-177">Os submenus são mais leves do que os diálogos e aparecem no painel superior.</span><span class="sxs-lookup"><span data-stu-id="fc870-177">Flyouts are more lightweight than dialogs, and appear from the top pane.</span></span>

##### <a name="list-controls"></a><span data-ttu-id="fc870-178">Controles de lista</span><span class="sxs-lookup"><span data-stu-id="fc870-178">List controls</span></span>

![controles de lista móvel](~/assets/images/mobile-list-controls.png)

##### <a name="field-controls"></a><span data-ttu-id="fc870-180">Controles de campo</span><span class="sxs-lookup"><span data-stu-id="fc870-180">Field controls</span></span>

![controles de campo móvel](~/assets/images/mobile-field-controls.png)
