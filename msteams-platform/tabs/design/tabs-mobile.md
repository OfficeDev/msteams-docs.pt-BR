---
title: Guias em dispositivos móveis
description: Descreve as diretrizes para a criação de guias que funcionam em dispositivos móveis.
keywords: Diretrizes de design de equipes guias de referência de aplicativos pessoais
ms.openlocfilehash: 928fb8586434eca9cc1577fd45c6b94594724d7f
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672717"
---
# <a name="tabs-on-mobile"></a><span data-ttu-id="a9246-104">Guias em dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="a9246-104">Tabs on mobile</span></span>

> [!Important]
> <span data-ttu-id="a9246-105">O suporte completo para guias em clientes móveis estará disponível em breve.</span><span class="sxs-lookup"><span data-stu-id="a9246-105">Full support for tabs on mobile clients is coming soon.</span></span> <span data-ttu-id="a9246-106">Para se preparar para esta alteração, você deve seguir as orientações ao criar suas guias.</span><span class="sxs-lookup"><span data-stu-id="a9246-106">To prepare for this change you should follow the this guidance when creating your tabs.</span></span> <span data-ttu-id="a9246-107">Os aplicativos pessoais (guias estáticas) estão disponíveis atualmente na [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md).</span><span class="sxs-lookup"><span data-stu-id="a9246-107">Personal apps (static tabs) are currently available in [developer preview](~/resources/dev-preview/developer-preview-intro.md).</span></span> <span data-ttu-id="a9246-108">e as `...` guias de chat de canal/grupo estão disponíveis no menu de excedentes da guia.</span><span class="sxs-lookup"><span data-stu-id="a9246-108">and channel / group chat tabs are available in the `...` overflow menu for the tab.</span></span>
>
> <span data-ttu-id="a9246-109">Quando o suporte completo para guias é liberado:</span><span class="sxs-lookup"><span data-stu-id="a9246-109">When full support for tabs is released:</span></span>
>
> * <span data-ttu-id="a9246-110">Todas as guias sempre estarão disponíveis em dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="a9246-110">All tabs will always be available on mobile</span></span>
> * <span data-ttu-id="a9246-111">O `contentUrl` **será carregado no cliente do Mobile Teams**.</span><span class="sxs-lookup"><span data-stu-id="a9246-111">Your `contentUrl` **will be loaded in the mobile Teams client**.</span></span>
> * <span data-ttu-id="a9246-112">Para guias de canal/grupo, os usuários ainda podem abrir sua guia em um navegador separado `websiteUrl`por meio de `contentUrl` seu, no entanto, seu primeiro será carregado.</span><span class="sxs-lookup"><span data-stu-id="a9246-112">For channel/group tabs, users can still open your tab in a separate browser via your `websiteUrl`, however your `contentUrl` will be loaded first.</span></span>
> * <span data-ttu-id="a9246-113">Se sua guia usa autenticação, você deve atualizar o SDK do JavaScript do Microsoft Teams para a versão 1.4.1 ou posterior, ou a autenticação falhará.</span><span class="sxs-lookup"><span data-stu-id="a9246-113">If your tab uses authentication, you must upgrade your Teams JavaScript SDK to version 1.4.1 or later, or authentication will fail.</span></span>

<span data-ttu-id="a9246-114">As guias personalizadas podem fazer parte de um canal, de um chat de grupo ou de um aplicativo pessoal (aplicativos que contêm guias estáticas e/ou um bot de um para um).</span><span class="sxs-lookup"><span data-stu-id="a9246-114">Custom tabs can be part of a channel, group chat, or personal app (apps that contain static tabs and/or a one-to-one bot).</span></span>

<span data-ttu-id="a9246-115">Os aplicativos pessoais estão disponíveis em clientes móveis na gaveta de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="a9246-115">Personal apps are available on mobile clients in the App Drawer.</span></span> <span data-ttu-id="a9246-116">O aplicativo só pode ser instalado a partir de um cliente da Web ou da área de trabalho, e pode levar até 24 horas para aparecer em clientes móveis.</span><span class="sxs-lookup"><span data-stu-id="a9246-116">The app can only be installed from a desktop or web client, and can take up to 24 hours to appear on mobile clients.</span></span>

<span data-ttu-id="a9246-117">As guias de grupo e canal também estão disponíveis em clientes móveis.</span><span class="sxs-lookup"><span data-stu-id="a9246-117">Group and channel tabs are available on mobile clients as well.</span></span> <span data-ttu-id="a9246-118">O comportamento padrão é atualmente usar o `websiteUrl` para iniciar sua guia em uma janela do navegador.</span><span class="sxs-lookup"><span data-stu-id="a9246-118">The default behavior is currently to use your `websiteUrl` to launch your tab in a browser window.</span></span> <span data-ttu-id="a9246-119">No entanto, eles podem ser carregados em um cliente móvel clicando `...` no menu de excedentes ao lado da guia e escolhendo **abrir**, que `contentUrl` usará o para carregar a guia dentro do cliente móvel do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="a9246-119">However, they can be loaded on a mobile client by clicking the `...` overflow menu next to the tab and choosing **Open**, which will use your `contentUrl` to load the tab inside the Teams mobile client.</span></span>

![gaveta de aplicativos móveis](~/assets/images/app-drawer.png)

## <a name="developer-considerations-for-mobile-support"></a><span data-ttu-id="a9246-121">Considerações de desenvolvedor para suporte móvel</span><span class="sxs-lookup"><span data-stu-id="a9246-121">Developer considerations for mobile support</span></span>

<span data-ttu-id="a9246-122">Ao criar um aplicativo que inclua uma guia, você precisa considerar (e testar) como sua guia funcionará nos clientes do Microsoft Teams Android e iOS.</span><span class="sxs-lookup"><span data-stu-id="a9246-122">When you're building an app that includes a tab, you need to consider (and test) how your tab will function on both the Android and iOS Microsoft Teams clients.</span></span> <span data-ttu-id="a9246-123">As seções a seguir descrevem alguns dos principais cenários que você precisa considerar.</span><span class="sxs-lookup"><span data-stu-id="a9246-123">The sections below outline some of the key scenarios you need to consider.</span></span>

### <a name="testing-on-mobile-clients"></a><span data-ttu-id="a9246-124">Testando clientes móveis</span><span class="sxs-lookup"><span data-stu-id="a9246-124">Testing on mobile clients</span></span>

<span data-ttu-id="a9246-125">Você precisa validar que sua guia funciona corretamente em dispositivos móveis de vários tamanhos e qualidades.</span><span class="sxs-lookup"><span data-stu-id="a9246-125">You need to validate that your tab functions properly on mobile devices of various sizes and qualities.</span></span> <span data-ttu-id="a9246-126">Para dispositivos Android, você pode usar o [devtools](~/tabs/how-to/developer-tools.md) para depurar sua guia enquanto estiver sendo executado.</span><span class="sxs-lookup"><span data-stu-id="a9246-126">For Android devices you can use the [DevTools](~/tabs/how-to/developer-tools.md) to debug your tab while it is running.</span></span> <span data-ttu-id="a9246-127">Recomendamos que você teste em dispositivos de desempenho alto e baixo, bem como em um Tablet.</span><span class="sxs-lookup"><span data-stu-id="a9246-127">We recommend that you test on both high and low performing devices, as well as on a tablet.</span></span>

### <a name="responsive-design"></a><span data-ttu-id="a9246-128">Design responsivo</span><span class="sxs-lookup"><span data-stu-id="a9246-128">Responsive design</span></span>

<span data-ttu-id="a9246-129">Como sua guia pode ser aberta em dispositivos com uma ampla variedade de tamanhos de tela, é necessário seguir princípios de [design responsivos](https://www.w3schools.com/html/html_responsive.asp) .</span><span class="sxs-lookup"><span data-stu-id="a9246-129">Because your tab can be opened on devices with a wide range of screen sizes, it needs to follow [responsive design](https://www.w3schools.com/html/html_responsive.asp) principles.</span></span> <span data-ttu-id="a9246-130">Todas as construções de chave devem estar acessíveis em dispositivos móveis, e os modos de exibição não devem ser distorcidos.</span><span class="sxs-lookup"><span data-stu-id="a9246-130">All of the key constructs should be accessible on mobile devices, and the views should not be distorted.</span></span> <span data-ttu-id="a9246-131">Verifique se a guia é carregada em um dispositivo móvel, se todos os botões e links estão facilmente acessíveis usando a navegação baseada em Finger.</span><span class="sxs-lookup"><span data-stu-id="a9246-131">Ensure that when your tab is loaded on a mobile device, all buttons and links are easily accessible using finger-based navigation.</span></span>

### <a name="authentication"></a><span data-ttu-id="a9246-132">Autenticação</span><span class="sxs-lookup"><span data-stu-id="a9246-132">Authentication</span></span>

<span data-ttu-id="a9246-133">Para que a autenticação funcione em clientes móveis, você deve atualizar o SDK do teams JS para pelo menos a versão 1.4.1.</span><span class="sxs-lookup"><span data-stu-id="a9246-133">For authentication to work on mobile clients, you must upgrade you Teams JS SDK to at least version 1.4.1.</span></span>

### <a name="low-bandwidth--intermittent-connections"></a><span data-ttu-id="a9246-134">Baixa largura de banda & conexões intermitentes</span><span class="sxs-lookup"><span data-stu-id="a9246-134">Low bandwidth & intermittent connections</span></span>

<span data-ttu-id="a9246-135">Os clientes móveis precisam funcionar regularmente com baixa largura de banda e conexões intermitentes.</span><span class="sxs-lookup"><span data-stu-id="a9246-135">Mobile clients regularly need to function with low bandwidth and intermittent connections.</span></span> <span data-ttu-id="a9246-136">Seu aplicativo deve lidar com os tempos limite de forma adequada fornecendo uma mensagem contextual para o usuário.</span><span class="sxs-lookup"><span data-stu-id="a9246-136">Your app should handle any timeouts appropriately by providing a contextual message to the user.</span></span> <span data-ttu-id="a9246-137">Você também deve fazer os indicadores de progresso do usuário para fornecer comentários aos seus usuários para todos os processos de execução demorada.</span><span class="sxs-lookup"><span data-stu-id="a9246-137">You should also user progress indicators to provide feedback to your users for any long-running processes.</span></span>

## <a name="design-considerations-for-mobile"></a><span data-ttu-id="a9246-138">Considerações de design para dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="a9246-138">Design considerations for mobile</span></span>

<span data-ttu-id="a9246-139">Nossa plataforma móvel permite que os aplicativos sejam uma experiência de imersão com o conteúdo do aplicativo tirando toda a tela da navegação do teams principal.</span><span class="sxs-lookup"><span data-stu-id="a9246-139">Our mobile platform allows apps to be an immersive experience with the app content taking up all of the screen apart from main Teams navigation.</span></span> <span data-ttu-id="a9246-140">Para criar uma experiência de imersão que se ajuste perfeitamente no cliente Microsoft Teams, siga as diretrizes abaixo.</span><span class="sxs-lookup"><span data-stu-id="a9246-140">To create an immersive experience that fits seamlessly within the Microsoft Teams client, follow the guidelines below.</span></span>

### <a name="layouts"></a><span data-ttu-id="a9246-141">Layouts</span><span class="sxs-lookup"><span data-stu-id="a9246-141">Layouts</span></span>

<span data-ttu-id="a9246-142">Escolher o layout correto para sua guia é importante.</span><span class="sxs-lookup"><span data-stu-id="a9246-142">Choosing the correct layout for your tab is important.</span></span> <span data-ttu-id="a9246-143">Considere o tipo de informação que você está apresentando e escolha um layout que a organize para facilitar o consumo.</span><span class="sxs-lookup"><span data-stu-id="a9246-143">You should consider the kind of information you're presenting, and choose a layout that organizes it for easy consumption.</span></span> <span data-ttu-id="a9246-144">Algumas opções potenciais estão descritas abaixo.</span><span class="sxs-lookup"><span data-stu-id="a9246-144">Some potential options are outlined below.</span></span>

#### <a name="single-canvas"></a><span data-ttu-id="a9246-145">Tela única</span><span class="sxs-lookup"><span data-stu-id="a9246-145">Single canvas</span></span>

<span data-ttu-id="a9246-146">Esta é uma grande área onde o trabalho é concluído.</span><span class="sxs-lookup"><span data-stu-id="a9246-146">This is one large area where work gets done.</span></span> <span data-ttu-id="a9246-147">O aplicativo wiki segue esse padrão.</span><span class="sxs-lookup"><span data-stu-id="a9246-147">The Wiki app follows this pattern.</span></span> <span data-ttu-id="a9246-148">Se você tiver um aplicativo que não separa o conteúdo em componentes menores, isso seria um bom ajuste.</span><span class="sxs-lookup"><span data-stu-id="a9246-148">If you have an app that doesn’t separate content into smaller components this would be a good fit.</span></span>

![layout de tela única](~/assets/images/mobile-single-canvas.png)

#### <a name="list"></a><span data-ttu-id="a9246-150">Listar</span><span class="sxs-lookup"><span data-stu-id="a9246-150">List</span></span>

<span data-ttu-id="a9246-151">As listas são ótimas para classificar e filtrar grandes quantidades de dados e são excelentes para manter as coisas mais importantes na parte superior.</span><span class="sxs-lookup"><span data-stu-id="a9246-151">Lists are great for sorting and filtering large quantities of data and are great at keeping the most important things at the top.</span></span> <span data-ttu-id="a9246-152">É útil usar colunas classificável.</span><span class="sxs-lookup"><span data-stu-id="a9246-152">It is helpful to use sortable columns.</span></span> <span data-ttu-id="a9246-153">As ações podem ser adicionadas a cada item de lista no menu de reticências.</span><span class="sxs-lookup"><span data-stu-id="a9246-153">Actions can be added to each list item under the ellipsis menu.</span></span>

![layout de lista](~/assets/images/mobile-list.png)

#### <a name="grid"></a><span data-ttu-id="a9246-155">Encaixe</span><span class="sxs-lookup"><span data-stu-id="a9246-155">Grid</span></span>

<span data-ttu-id="a9246-156">As grades são úteis para mostrar elementos que são altamente visuais.</span><span class="sxs-lookup"><span data-stu-id="a9246-156">Grids are useful for showing elements which are highly visual.</span></span> <span data-ttu-id="a9246-157">Ele ajuda a incluir um filtro ou controle de pesquisa na parte superior.</span><span class="sxs-lookup"><span data-stu-id="a9246-157">It helps to include a filter or search control at the top.</span></span>

![layout de grade](~/assets/images/mobile-grid.png)

### <a name="tabs-with-bots-on-mobile"></a><span data-ttu-id="a9246-159">Guias com bots em dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="a9246-159">Tabs with bots on mobile</span></span>

<span data-ttu-id="a9246-160">Veja a seguir um exemplo de aplicativo pessoal que contém duas guias estáticas e um bot.</span><span class="sxs-lookup"><span data-stu-id="a9246-160">The below is an example personal app that contains two static tabs and a bot.</span></span>

![guias e bots em dispositivos móveis](~/assets/images/mobile-tab-with-bot.png)

### <a name="ui-components"></a><span data-ttu-id="a9246-162">Componentes da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="a9246-162">UI Components</span></span>

#### <a name="color-palettes"></a><span data-ttu-id="a9246-163">Paletas de cores</span><span class="sxs-lookup"><span data-stu-id="a9246-163">Color palettes</span></span>

<span data-ttu-id="a9246-164">Usar nossa paleta neutra aprovada para planos de fundo, notificações, texto e botões ajudará seu aplicativo a se sentir mais em casa no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="a9246-164">Using our approved neutral palette for backgrounds, notifications, text, and buttons will help your app feel more at home in Teams.</span></span> <span data-ttu-id="a9246-165">Como o Microsoft Teams Mobile tem dois temas de cor (claro e escuro), é uma boa ideia garantir que seu aplicativo fique ótimo em ambos.</span><span class="sxs-lookup"><span data-stu-id="a9246-165">Since Teams mobile has two colour themes (light and dark), it’s a good idea to make sure your app looks great in both.</span></span>

##### <a name="light-color"></a><span data-ttu-id="a9246-166">Cor clara</span><span class="sxs-lookup"><span data-stu-id="a9246-166">Light color</span></span>

![paleta de cores claras](~/assets/images/light-color.png)

##### <a name="dark-color"></a><span data-ttu-id="a9246-168">Cor escura</span><span class="sxs-lookup"><span data-stu-id="a9246-168">Dark color</span></span>

![paleta de cores escuras](~/assets/images/dark-color.png)

#### <a name="buttons-and-controls"></a><span data-ttu-id="a9246-170">Botões e controles</span><span class="sxs-lookup"><span data-stu-id="a9246-170">Buttons and controls</span></span>

<span data-ttu-id="a9246-171">A maneira como os botões são estilizados ajuda a comunicar o tipo de ação que eles disparam.</span><span class="sxs-lookup"><span data-stu-id="a9246-171">The way buttons are styled helps communicate what kind of action they trigger.</span></span> <span data-ttu-id="a9246-172">Mantemos uma ampla variedade de botões formatados para mostrar diferentes níveis de ênfase.</span><span class="sxs-lookup"><span data-stu-id="a9246-172">We maintain a wide range of buttons that are formatted to show different levels of emphasis.</span></span> <span data-ttu-id="a9246-173">Os botões podem ter texto, um ícone ou uma combinação de texto e um ícone.</span><span class="sxs-lookup"><span data-stu-id="a9246-173">Buttons can have text, an icon, or a combination of text and an icon.</span></span> <span data-ttu-id="a9246-174">Para comunicar diferentes níveis em uma hierarquia, projetamos os botões principal e secundário dentro de cada categoria.</span><span class="sxs-lookup"><span data-stu-id="a9246-174">To communicate different levels in a hierarchy, we designed primary and secondary buttons within each category.</span></span>

![recolhe](~/assets/images/buttons.png)

![controles de seleção](~/assets/images/selection-controls.png)

![Chiclets e pills](~/assets/images/chiclets-and-pills.png)

#### <a name="typography"></a><span data-ttu-id="a9246-178">Tipografia</span><span class="sxs-lookup"><span data-stu-id="a9246-178">Typography</span></span>

<span data-ttu-id="a9246-179">A tipografia deve ser clara e proposital.</span><span class="sxs-lookup"><span data-stu-id="a9246-179">Typography should be clear and purposeful.</span></span> <span data-ttu-id="a9246-180">Enfatize informações importantes e evite usar várias fontes e tamanhos para reduzir a confusão.</span><span class="sxs-lookup"><span data-stu-id="a9246-180">Emphasize important information and avoid using multiple fonts and sizes to reduce confusion.</span></span> <span data-ttu-id="a9246-181">Recomendamos o uso de maiúsculas e minúsculas e evitar o uso de todos os Caps para a localização e a legibilidade.</span><span class="sxs-lookup"><span data-stu-id="a9246-181">We recommend using sentence case and avoiding the usage of all caps for localization and legibility.</span></span>

![Typograph móvel](~/assets/images/mobile-typography.png)

#### <a name="fields-and-flyouts"></a><span data-ttu-id="a9246-183">Campos e submenus</span><span class="sxs-lookup"><span data-stu-id="a9246-183">Fields and Flyouts</span></span>

<span data-ttu-id="a9246-184">Os campos são áreas onde os usuários podem inserir texto.</span><span class="sxs-lookup"><span data-stu-id="a9246-184">Fields are areas where users can input text.</span></span> <span data-ttu-id="a9246-185">Os submenus são mais leves do que os diálogos e aparecem no painel superior.</span><span class="sxs-lookup"><span data-stu-id="a9246-185">Flyouts are more lightweight than dialogs, and appear from the top pane.</span></span>

##### <a name="list-controls"></a><span data-ttu-id="a9246-186">Controles de lista</span><span class="sxs-lookup"><span data-stu-id="a9246-186">List controls</span></span>

![controles de lista móvel](~/assets/images/mobile-list-controls.png)

##### <a name="field-controls"></a><span data-ttu-id="a9246-188">Controles de campo</span><span class="sxs-lookup"><span data-stu-id="a9246-188">Field controls</span></span>

![controles de campo móvel](~/assets/images/mobile-field-controls.png)
