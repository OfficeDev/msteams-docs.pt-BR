---
title: Diretrizes de design para guias
description: Descreve as diretrizes para a criação de guias de conteúdo e colaboração
keywords: Teams design Guidelines Reference Framework Tabs Configuration guia canal de configuração guia estática guia de equipes de design simples
ms.openlocfilehash: 2d4e809e3ac11a5742113bf65125848a922c0207
ms.sourcegitcommit: 50571f5c6afc86177c4fe1032fe13366a7b706dd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2020
ms.locfileid: "49576859"
---
# <a name="content-and-conversations-all-at-once-using-tabs"></a><span data-ttu-id="97e0c-104">Conteúdo e conversas, todos ao mesmo tempo usando guias</span><span class="sxs-lookup"><span data-stu-id="97e0c-104">Content and conversations, all at once using tabs</span></span>

> [!Important]
> <span data-ttu-id="97e0c-105">**Guias em clientes móveis**</span><span class="sxs-lookup"><span data-stu-id="97e0c-105">**Tabs on Mobile Clients**</span></span>
>
> <span data-ttu-id="97e0c-106">Siga as [orientações para guias em celular](./tabs-mobile.md) ao criar suas guias.</span><span class="sxs-lookup"><span data-stu-id="97e0c-106">Follow the [guidance for tabs on mobile](./tabs-mobile.md) when creating your tabs.</span></span> <span data-ttu-id="97e0c-107">Se sua guia usa autenticação, você deve atualizar o SDK do JavaScript do Microsoft Teams para a versão 1.4.1 ou posterior, ou a autenticação falhará.</span><span class="sxs-lookup"><span data-stu-id="97e0c-107">If your tab uses authentication, you must upgrade your Teams JavaScript SDK to version 1.4.1 or later, or authentication will fail.</span></span>
>
> <span data-ttu-id="97e0c-108">**Guias de canal/grupo (configurável) em dispositivos móveis:**</span><span class="sxs-lookup"><span data-stu-id="97e0c-108">**Channel/group (configurable) tabs on mobile:**</span></span>
>
> * <span data-ttu-id="97e0c-109">Os clientes móveis só mostram guias configuráveis com um valor para `websiteUrl` .</span><span class="sxs-lookup"><span data-stu-id="97e0c-109">Mobile clients only show configurable tabs that have a value for `websiteUrl`.</span></span> <span data-ttu-id="97e0c-110">Se quiser que a sua guia apareça nos clientes móveis do Microsoft Teams, você deve definir o valor de `websiteUrl` .</span><span class="sxs-lookup"><span data-stu-id="97e0c-110">If you want your tab to appear on the Teams mobile clients, you must set the value of `websiteUrl`.</span></span>
> * <span data-ttu-id="97e0c-111">O comportamento de abertura padrão no Mobile é abrir fora do navegador usando o `websiteUrl` .</span><span class="sxs-lookup"><span data-stu-id="97e0c-111">Default open behavior on mobile is to open outside in browser using the `websiteUrl`.</span></span> <span data-ttu-id="97e0c-112">Para aplicativos publicados na loja de aplicativos públicos, se você quiser que a guia de canal seja aberta no Teams por padrão, siga as [orientações para guias em dispositivos móveis](~/tabs/design/tabs-mobile.md)e entre em seu representante de suporte para solicitar a lista branca.</span><span class="sxs-lookup"><span data-stu-id="97e0c-112">For apps published to the public App Store, if you want your channel tab to open inside teams by default, follow the [guidance for tabs on mobile](~/tabs/design/tabs-mobile.md), and reach out to your support rep to request to be whitelisted.</span></span>

<span data-ttu-id="97e0c-113">Guias são Canvases que você pode usar para compartilhar conteúdo, reter conversas e hospedar serviços de terceiros, tudo em um fluxo de trabalho orgânica da equipe.</span><span class="sxs-lookup"><span data-stu-id="97e0c-113">Tabs are canvases that you can use to share content, hold conversations, and host third-party services, all within a team’s organic workflow.</span></span> <span data-ttu-id="97e0c-114">Quando você cria uma guia no Microsoft Teams, ele coloca seu aplicativo Web front e Center onde ele é facilmente acessível contra conversas principais.</span><span class="sxs-lookup"><span data-stu-id="97e0c-114">When you build a tab in Microsoft Teams, it puts your web app front and center where it’s easily accessible from key conversations.</span></span>

## <a name="guidelines"></a><span data-ttu-id="97e0c-115">Diretrizes</span><span class="sxs-lookup"><span data-stu-id="97e0c-115">Guidelines</span></span>

<span data-ttu-id="97e0c-116">Uma guia boa deve exibir as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="97e0c-116">A good tab should display the following characteristics:</span></span>

### <a name="focused-functionality"></a><span data-ttu-id="97e0c-117">Funcionalidade prioritária</span><span class="sxs-lookup"><span data-stu-id="97e0c-117">Focused functionality</span></span>

<span data-ttu-id="97e0c-118">As guias funcionam melhor quando são criadas para atender a uma necessidade específica.</span><span class="sxs-lookup"><span data-stu-id="97e0c-118">Tabs work best when they’re built to address a specific need.</span></span> <span data-ttu-id="97e0c-119">Concentre-se em um pequeno conjunto de tarefas ou em um subconjunto de dados que é relevante para o canal em que a guia se encontra.</span><span class="sxs-lookup"><span data-stu-id="97e0c-119">Focus on a small set of tasks or a subset of data that’s relevant to the channel the tab is in.</span></span>

### <a name="reduced-chrome"></a><span data-ttu-id="97e0c-120">Cromo reduzido</span><span class="sxs-lookup"><span data-stu-id="97e0c-120">Reduced chrome</span></span>

<span data-ttu-id="97e0c-121">Evite criar vários painéis em uma guia, adicionar camadas de navegação ou exigir que os usuários rolem verticalmente e horizontalmente em uma guia. Em outras palavras, tente não ter tabulações na guia.</span><span class="sxs-lookup"><span data-stu-id="97e0c-121">Avoid creating multiple panels in a tab, adding layers of navigation, or requiring users to scroll both vertically and horizontally in one tab. In other words, try not to have tabs in your tab.</span></span>

### <a name="integration"></a><span data-ttu-id="97e0c-122">Integração</span><span class="sxs-lookup"><span data-stu-id="97e0c-122">Integration</span></span>

<span data-ttu-id="97e0c-123">Encontre maneiras de notificar os usuários sobre a atividade de guia postando [cartões adaptáveis](../../task-modules-and-cards/what-are-cards.md#adaptive-cards) a uma conversa.</span><span class="sxs-lookup"><span data-stu-id="97e0c-123">Find ways to notify users about tab activity by posting [adaptive cards](../../task-modules-and-cards/what-are-cards.md#adaptive-cards) to a conversation.</span></span>

### <a name="conversational"></a><span data-ttu-id="97e0c-124">Coloquial</span><span class="sxs-lookup"><span data-stu-id="97e0c-124">Conversational</span></span>

<span data-ttu-id="97e0c-125">Encontre uma maneira de facilitar a conversa em torno de uma guia. Isso garante que o centro de conversas fique no conteúdo, nos dados ou no processo em mãos.</span><span class="sxs-lookup"><span data-stu-id="97e0c-125">Find a way to facilitate conversation around a tab. This ensures that conversations center on the content, data, or process at hand.</span></span>

### <a name="streamlined-access"></a><span data-ttu-id="97e0c-126">Acesso simplificado</span><span class="sxs-lookup"><span data-stu-id="97e0c-126">Streamlined access</span></span>

<span data-ttu-id="97e0c-127">Certifique-se de que você está concedendo acesso às pessoas certas no momento certo.</span><span class="sxs-lookup"><span data-stu-id="97e0c-127">Make sure you’re granting access to the right people at the right time.</span></span> <span data-ttu-id="97e0c-128">Manter o processo de entrada simples evitará a criação de barreiras para contribuição e colaboração.</span><span class="sxs-lookup"><span data-stu-id="97e0c-128">Keeping your sign-in process simple will avoid creating barriers to contribution and collaboration.</span></span>

### <a name="responsiveness-to-window-sizing"></a><span data-ttu-id="97e0c-129">Capacidade de resposta para dimensionamento de janela</span><span class="sxs-lookup"><span data-stu-id="97e0c-129">Responsiveness to window sizing</span></span>

<span data-ttu-id="97e0c-130">As equipes podem ser usadas em tamanhos de janela tão pequenos quanto 720px, então garantir que uma guia possa ser usada em uma pequena janela seja tão importante quanto a usabilidade em resoluções muito altas.</span><span class="sxs-lookup"><span data-stu-id="97e0c-130">Teams can be used in window sizes as small as 720px, so making sure that a tab is usable in a small window is just as important as usability at very high resolutions.</span></span>

### <a name="flat-navigation"></a><span data-ttu-id="97e0c-131">Navegação simples</span><span class="sxs-lookup"><span data-stu-id="97e0c-131">Flat navigation</span></span>

<span data-ttu-id="97e0c-132">Pedimos aos desenvolvedores não adicionar o portal inteiro a uma guia. Manter a navegação relativamente simples ajuda a manter um modelo de conversa mais simples.</span><span class="sxs-lookup"><span data-stu-id="97e0c-132">We ask developers not to add their entire portal to a tab. Keeping the navigation relatively flat helps maintain a simpler conversational model.</span></span> <span data-ttu-id="97e0c-133">Em outras palavras, a conversa é sobre uma lista de coisas, como itens de trabalho triantigos, ou uma única coisa, como uma espec.</span><span class="sxs-lookup"><span data-stu-id="97e0c-133">In other words, the conversation is about a list of things, such as triaged work items, or a single thing, like a spec.</span></span>

<span data-ttu-id="97e0c-134">Há desafios de navegação inerentes com uma hierarquia de navegação profunda em conversas encadeadas.</span><span class="sxs-lookup"><span data-stu-id="97e0c-134">There are inherent navigational challenges with deep navigation hierarchy, within threaded conversations.</span></span> <span data-ttu-id="97e0c-135">Para a melhor experiência do usuário, a navegação de guia deve ser mantida no mínimo e ser projetada da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="97e0c-135">For the best user experience, your tab navigation should be kept to a minimum and be designed as follows:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="97e0c-136">**Abre um módulo de tarefa, como um item de trabalho individual ou uma entidade**.</span><span class="sxs-lookup"><span data-stu-id="97e0c-136">**Opens a task module such as an individual work item or entity**.</span></span> <span data-ttu-id="97e0c-137">Isso impede totalmente o chat e é a melhor opção para manter o chat especificamente sobre a guia e não as subentidades ou experiências de edição.</span><span class="sxs-lookup"><span data-stu-id="97e0c-137">This precludes chat entirely and is the best option to keep chat specifically about the tab and not the sub-entities or editing experiences.</span></span>
>* <span data-ttu-id="97e0c-138">**Abre uma pseudo caixa de diálogo em um iframe**.</span><span class="sxs-lookup"><span data-stu-id="97e0c-138">**Opens a pseudo dialog in an iframe**.</span></span> <span data-ttu-id="97e0c-139">Se usado com um plano de fundo em tela, recomendamos usar a cor mais clara em vez do escuro.</span><span class="sxs-lookup"><span data-stu-id="97e0c-139">If used with a screened background we recommend using the lighter color rather than the dark.</span></span> <span data-ttu-id="97e0c-140">A `app-gray-10 at 30%` transparência funciona bem.</span><span class="sxs-lookup"><span data-stu-id="97e0c-140">The `app-gray-10 at 30%` transparency works well.</span></span>
>* <span data-ttu-id="97e0c-141">**Abre uma página do navegador**.</span><span class="sxs-lookup"><span data-stu-id="97e0c-141">**Opens a browser page**.</span></span>

### <a name="personality"></a><span data-ttu-id="97e0c-142">Personalidade</span><span class="sxs-lookup"><span data-stu-id="97e0c-142">Personality</span></span>

<span data-ttu-id="97e0c-143">A tela da guia apresenta uma ótima oportunidade de marcar sua experiência.</span><span class="sxs-lookup"><span data-stu-id="97e0c-143">Your tab canvas presents a great opportunity to brand your experience.</span></span> <span data-ttu-id="97e0c-144">O logotipo é uma parte importante da sua identidade e conexão com os usuários. portanto, não se esqueça de incluí-lo:</span><span class="sxs-lookup"><span data-stu-id="97e0c-144">Your logo is an important part of your identity and connection with your users., so be sure to include it:</span></span>

> [!div class="checklist"]
>
>* <span data-ttu-id="97e0c-145">Coloque o logotipo no canto esquerdo ou direito ou ao longo da borda inferior</span><span class="sxs-lookup"><span data-stu-id="97e0c-145">Place your logo in the left or right corner or along the bottom edge</span></span>
> * <span data-ttu-id="97e0c-146">Mantenha seu logotipo pequeno e discreto</span><span class="sxs-lookup"><span data-stu-id="97e0c-146">Keep your logo small and unobtrusive</span></span>

<span data-ttu-id="97e0c-147">A incorporação de suas próprias cores e layouts twill também ajuda na comunicação de personalidade.</span><span class="sxs-lookup"><span data-stu-id="97e0c-147">Incorporating your own colors and layouts twill also aid in communicating personality.</span></span>

> [!TIP]
> <span data-ttu-id="97e0c-148">Trabalhe com o nosso estilo visual para que seu serviço se sente como parte do teams.</span><span class="sxs-lookup"><span data-stu-id="97e0c-148">Please work with our visual style so your service feels like a part of Teams.</span></span> <span data-ttu-id="97e0c-149">*Confira*, por exemplo, [cores de equipes](../../concepts/design/components/color.md)</span><span class="sxs-lookup"><span data-stu-id="97e0c-149">*See*, for example [Teams Colors](../../concepts/design/components/color.md)</span></span>

---

## <a name="tab-layouts"></a><span data-ttu-id="97e0c-150">Layouts de guia</span><span class="sxs-lookup"><span data-stu-id="97e0c-150">Tab layouts</span></span>

[!INCLUDE [Tab layouts](../../includes/design/tab-layouts.html)]

---

## <a name="types-of-tabs"></a><span data-ttu-id="97e0c-151">Tipos de guias</span><span class="sxs-lookup"><span data-stu-id="97e0c-151">Types of tabs</span></span>

[!INCLUDE [Tab types](../../includes/design/tab-types.html)]

---

## <a name="configuration-page-height"></a><span data-ttu-id="97e0c-152">Altura da página de configuração</span><span class="sxs-lookup"><span data-stu-id="97e0c-152">Configuration page height</span></span>

>[!IMPORTANT]
><span data-ttu-id="97e0c-153">Em setembro de 2018, a altura da [página de configuração](~/tabs/how-to/create-tab-pages/configuration-page.md) da guia foi aumentada enquanto a largura permanece inalterada.</span><span class="sxs-lookup"><span data-stu-id="97e0c-153">In September 2018, the height for the tab [configuration page](~/tabs/how-to/create-tab-pages/configuration-page.md) was increased while the width remained unchanged.</span></span> <span data-ttu-id="97e0c-154">Se o seu aplicativo for projetado para o tamanho mais antigo, a página de configuração da guia terá uma grande quantidade de espaço em branco vertical.</span><span class="sxs-lookup"><span data-stu-id="97e0c-154">If your app is designed for the older size your tab configuration page will have a great deal of vertical whitespace.</span></span> <span data-ttu-id="97e0c-155">Aplicativos de repositório herdados isentos dessa alteração precisarão entrar em contato com a Microsoft após a atualização para acomodar as novas dimensões.</span><span class="sxs-lookup"><span data-stu-id="97e0c-155">Legacy store apps exempted from this change will need to contact Microsoft after updating to accommodate the new dimensions.</span></span>

<span data-ttu-id="97e0c-156">As dimensões da página de configuração de guia:</span><span class="sxs-lookup"><span data-stu-id="97e0c-156">The dimensions of the tab configuration page:</span></span>


<img width="450px" title="Tamanhos de guias de configuração" src="~/assets/images/tabs/config-dialog-Contoso2.png" alt="sizes for config tabs" />


### <a name="guidelines-for-tab-configuration-page-format"></a><span data-ttu-id="97e0c-158">Diretrizes para o formato de página de configuração de guia</span><span class="sxs-lookup"><span data-stu-id="97e0c-158">Guidelines for tab configuration page format</span></span>

* <span data-ttu-id="97e0c-159">Baseie a altura mínima da área de conteúdo da página de configuração da guia em elementos gráficos de altura fixa.</span><span class="sxs-lookup"><span data-stu-id="97e0c-159">Base the minimum height of your content area of your tab configuration page on fixed-height graphic elements.</span></span>
* <span data-ttu-id="97e0c-160">Calcula o espaço vertical disponível (a altura da área de conteúdo na página de configuração) usando o `window.innerHeight` .</span><span class="sxs-lookup"><span data-stu-id="97e0c-160">Calculate available vertical space (the height of the content area in the configuration page) using `window.innerHeight`.</span></span> <span data-ttu-id="97e0c-161">Isso retorna o tamanho do `<iframe>` no qual a página de configuração reside, o que pode ser alterado em versões futuras.</span><span class="sxs-lookup"><span data-stu-id="97e0c-161">This returns the size of the `<iframe>` in which your configuration page resides, which may change in future releases.</span></span> <span data-ttu-id="97e0c-162">Usando esse valor, seu conteúdo será ajustado automaticamente para futuras alterações.</span><span class="sxs-lookup"><span data-stu-id="97e0c-162">By using this value your content will adjust automatically to future changes.</span></span>
* <span data-ttu-id="97e0c-163">Alocar espaço vertical para os elementos de altura variável menos o que é necessário para os elementos de altura fixa.</span><span class="sxs-lookup"><span data-stu-id="97e0c-163">Allocate vertical space to the variable-height elements minus what's needed for the fixed-height elements.</span></span>
* <span data-ttu-id="97e0c-164">Para o estado de *logon* , centralizar o conteúdo verticalmente e horizontalmente.</span><span class="sxs-lookup"><span data-stu-id="97e0c-164">For the *login* state, vertically and horizontally center the content.</span></span>
* <span data-ttu-id="97e0c-165">Se você quiser uma imagem de plano de fundo, precisará de uma nova imagem, dimensionada para se ajustar à área (preferencial) ou pode manter a mesma imagem e escolher entre:</span><span class="sxs-lookup"><span data-stu-id="97e0c-165">If you want a background image, you need either a new image, sized to fit the area (preferred), or you can keep the same image and choose between:</span></span>
  * <span data-ttu-id="97e0c-166">alinhamento no canto superior esquerdo.</span><span class="sxs-lookup"><span data-stu-id="97e0c-166">aligning to the upper left hand corner.</span></span>
  * <span data-ttu-id="97e0c-167">dimensionar a imagem para ajustá-la.</span><span class="sxs-lookup"><span data-stu-id="97e0c-167">scaling the image to fit.</span></span>

<span data-ttu-id="97e0c-168">Quando dimensionado corretamente, sua página de configuração de guia deve ser semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="97e0c-168">When properly sized, your tab configuration page should look similar to this:</span></span>

<img width="450px" title="Nova guia de configuração" src="~/assets/images/tabs/config-dialog-Contoso.png" alt="new config tab"/>

## <a name="best-practices"></a><span data-ttu-id="97e0c-170">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="97e0c-170">Best practices</span></span>

### <a name="always-include-a-default-state"></a><span data-ttu-id="97e0c-171">Sempre incluir um estado padrão</span><span class="sxs-lookup"><span data-stu-id="97e0c-171">Always include a default state</span></span>

<span data-ttu-id="97e0c-172">Inclua um estado padrão para facilitar a configuração de guias, mesmo que sua guia seja configurável.</span><span class="sxs-lookup"><span data-stu-id="97e0c-172">Include a default state to make tabs easy to set up even if your tab is configurable.</span></span>

### <a name="deep-linking"></a><span data-ttu-id="97e0c-173">Vinculação profunda</span><span class="sxs-lookup"><span data-stu-id="97e0c-173">Deep linking</span></span>

<span data-ttu-id="97e0c-174">Sempre que possível, cartões e bots devem se vincular detalhadamente a dados mais ricos em uma guia hospedada. Por exemplo, um cartão pode exibir um resumo dos dados de bug, mas clicar nele pode mostrar o erro inteiro em uma guia.</span><span class="sxs-lookup"><span data-stu-id="97e0c-174">Whenever possible, cards and bots should deep link to richer data in a hosted tab. For example, a card may show a summary of bug data, but clicking it can shows the entire bug in a tab.</span></span>

### <a name="naming"></a><span data-ttu-id="97e0c-175">Nomenclatura</span><span class="sxs-lookup"><span data-stu-id="97e0c-175">Naming</span></span>

<span data-ttu-id="97e0c-176">Em muitos casos, o nome do seu aplicativo criará um nome de guia ótimo.</span><span class="sxs-lookup"><span data-stu-id="97e0c-176">In many cases, the name of your app will make a great tab name.</span></span> <span data-ttu-id="97e0c-177">Mas, também considere nomear suas guias de acordo com a funcionalidade que elas fornecem.</span><span class="sxs-lookup"><span data-stu-id="97e0c-177">But, also consider naming your tabs according to the functionality they provide.</span></span>

### <a name="multi-window"></a><span data-ttu-id="97e0c-178">Várias janelas</span><span class="sxs-lookup"><span data-stu-id="97e0c-178">Multi-window</span></span>

<span data-ttu-id="97e0c-179">As guias de canal que têm recursos de edição complexos devem abrir o modo de exibição editor em várias janelas, em vez de uma guia.</span><span class="sxs-lookup"><span data-stu-id="97e0c-179">Channel tabs that have complex editing capabilities must open the editor view in multi-window rather than a tab.</span></span>

### <a name="no-horizontal-scrolling"></a><span data-ttu-id="97e0c-180">Sem rolagem horizontal</span><span class="sxs-lookup"><span data-stu-id="97e0c-180">No horizontal scrolling</span></span>

<span data-ttu-id="97e0c-181">A guia não deve ter rolagem horizontal.</span><span class="sxs-lookup"><span data-stu-id="97e0c-181">Tab should not have horizontal scrolling.</span></span>

### <a name="easy-navigation"></a><span data-ttu-id="97e0c-182">Navegação fácil</span><span class="sxs-lookup"><span data-stu-id="97e0c-182">Easy navigation</span></span>

<span data-ttu-id="97e0c-183">A navegação dentro de um aplicativo de guia deve ser fácil de seguir, ou seja, as páginas têm o seguinte, onde necessário/aplicável:</span><span class="sxs-lookup"><span data-stu-id="97e0c-183">Navigation inside a tab app must be easy to follow i.e. pages have the following where necessary/applicable:</span></span>
* <span data-ttu-id="97e0c-184">Botões voltar</span><span class="sxs-lookup"><span data-stu-id="97e0c-184">Back buttons</span></span>
* <span data-ttu-id="97e0c-185">Cabeçalhos de página</span><span class="sxs-lookup"><span data-stu-id="97e0c-185">Page headers</span></span>
* <span data-ttu-id="97e0c-186">Estrutural</span><span class="sxs-lookup"><span data-stu-id="97e0c-186">Breadcrumbs</span></span>
* <span data-ttu-id="97e0c-187">Menus de reficação</span><span class="sxs-lookup"><span data-stu-id="97e0c-187">Hamburger menus</span></span>

### <a name="undo-last-action"></a><span data-ttu-id="97e0c-188">Desfazer última ação</span><span class="sxs-lookup"><span data-stu-id="97e0c-188">Undo last action</span></span>

<span data-ttu-id="97e0c-189">O usuário deve ser capaz de desfazer a última ação no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="97e0c-189">User must be able to undo their last action in the app.</span></span>

### <a name="share-content"></a><span data-ttu-id="97e0c-190">Compartilhar conteúdo</span><span class="sxs-lookup"><span data-stu-id="97e0c-190">Share content</span></span>

<span data-ttu-id="97e0c-191">Os aplicativos pessoais devem permitir que os usuários compartilhem conteúdo de uma experiência de aplicativo pessoal com outros membros da equipe.</span><span class="sxs-lookup"><span data-stu-id="97e0c-191">Personal apps should enable users to share content from a personal app experience with other team members.</span></span> <span data-ttu-id="97e0c-192">A guia canal deve fornecer navegação que complementa a navegação principal do Teams, em vez de entrar em conflito com ela (como barras de navegação do trilho esquerdo).</span><span class="sxs-lookup"><span data-stu-id="97e0c-192">Channel tab must provide navigation that complements the main Teams navigation, rather than conflicting with it (such as left rail nav-bars).</span></span>

### <a name="single-view"></a><span data-ttu-id="97e0c-193">Modo de exibição único</span><span class="sxs-lookup"><span data-stu-id="97e0c-193">Single view</span></span>

<span data-ttu-id="97e0c-194">Os aplicativos pessoais devem apresentar conteúdo de instâncias com escopo de chat de grupo ou de equipe desse aplicativo em um modo de exibição único, por exemplo, um usuário do Trello deve ser capaz de ver todas as instâncias das placas do Trello que participam em um nível de equipe em seu aplicativo pessoal.</span><span class="sxs-lookup"><span data-stu-id="97e0c-194">Personal apps should present content from team or group chat scoped instances of that app in a single view, e.g., a Trello user should be able to see all instances of Trello boards they participate in at a team level in their personal app.</span></span>

### <a name="no-app-bar"></a><span data-ttu-id="97e0c-195">Nenhuma barra de aplicativos</span><span class="sxs-lookup"><span data-stu-id="97e0c-195">No app bar</span></span>

<span data-ttu-id="97e0c-196">As guias não devem fornecer uma barra de aplicativos com ícones no trilho esquerdo que estejam em conflito com a navegação do teams principal.</span><span class="sxs-lookup"><span data-stu-id="97e0c-196">Tabs should not provide an app bar with icons in the left rail that conflicts with the main Teams navigation.</span></span>

### <a name="navigation"></a><span data-ttu-id="97e0c-197">Navegação</span><span class="sxs-lookup"><span data-stu-id="97e0c-197">Navigation</span></span>

<span data-ttu-id="97e0c-198">Guias não devem ter mais de três níveis de navegação no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="97e0c-198">Tabs should not have more than 3 levels of navigation within the app.</span></span>

### <a name="l2l3-view"></a><span data-ttu-id="97e0c-199">Modo de exibição L2/L3</span><span class="sxs-lookup"><span data-stu-id="97e0c-199">L2/L3 view</span></span>

<span data-ttu-id="97e0c-200">As páginas secundárias e terciários em uma guia devem ser abertas em um modo de exibição L2/L3 na área de guia principal que é navegada por navegação estrutural.</span><span class="sxs-lookup"><span data-stu-id="97e0c-200">Secondary and tertiary pages in a tab should be opened in an L2/L3 view in the main tab area that is navigated via the breadcrumb.</span></span>

### <a name="no-link-to-external-browser"></a><span data-ttu-id="97e0c-201">Nenhum link para o navegador externo</span><span class="sxs-lookup"><span data-stu-id="97e0c-201">No link to external browser</span></span>

<span data-ttu-id="97e0c-202">Os destinos de link em guias não devem ser vinculados a um navegador externo, mas devem ser vinculados a elementos div contidos no Teams.</span><span class="sxs-lookup"><span data-stu-id="97e0c-202">Link targets in tabs should not link to an external browser but should link to div elements contained within Teams.</span></span> <span data-ttu-id="97e0c-203">Por exemplo, dentro de módulos de tarefas, guias, etc.</span><span class="sxs-lookup"><span data-stu-id="97e0c-203">For example, inside task Modules, tabs, etc.</span></span>

## <a name="notifications-for-tabs"></a><span data-ttu-id="97e0c-204">Notificações para guias</span><span class="sxs-lookup"><span data-stu-id="97e0c-204">Notifications for tabs</span></span>

<span data-ttu-id="97e0c-205">Há dois modos de notificação para alterações de conteúdo de guia:</span><span class="sxs-lookup"><span data-stu-id="97e0c-205">There are two modes of notification for tab content changes:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="97e0c-206">**Use a API do aplicativo para notificar os usuários sobre as alterações**.</span><span class="sxs-lookup"><span data-stu-id="97e0c-206">**Use the app API to notify users of changes**.</span></span> <span data-ttu-id="97e0c-207">Esta mensagem aparecerá no feed de atividades do usuário e no link profundo para a guia. *consulte*  [criar links de profundas para conteúdo e recursos no Microsoft Teams](../../concepts/build-and-test/deep-links.md?view=msteams-client-js-latest&preserve-view=true )</span><span class="sxs-lookup"><span data-stu-id="97e0c-207">This message will show up in the user’s activity feed and deep link to the tab. *See*  [Create deep links to content and features in Microsoft Teams](../../concepts/build-and-test/deep-links.md?view=msteams-client-js-latest&preserve-view=true )</span></span>

> * <span data-ttu-id="97e0c-208">**Use um bot**.</span><span class="sxs-lookup"><span data-stu-id="97e0c-208">**Use a bot**.</span></span> <span data-ttu-id="97e0c-209">Esse método é preferível, especialmente se o thread de guia for direcionado.</span><span class="sxs-lookup"><span data-stu-id="97e0c-209">This method is preferred especially if the Tab thread is targeted.</span></span> <span data-ttu-id="97e0c-210">O resultado será que a conversa encadeada da guia será movida para o modo de exibição como ativo recentemente.</span><span class="sxs-lookup"><span data-stu-id="97e0c-210">The result will be that the tab’s threaded conversation will be moved into view as recently active.</span></span> <span data-ttu-id="97e0c-211">Esse método também permite uma certa sofisticação na forma como a notificação é enviada.</span><span class="sxs-lookup"><span data-stu-id="97e0c-211">This method also allows for some sophistication in how the notification is sent.</span></span>

<span data-ttu-id="97e0c-212">Enviar uma mensagem para um thread de guia aumenta a conscientização da atividade para todos os usuários sem notificar explicitamente todos.</span><span class="sxs-lookup"><span data-stu-id="97e0c-212">Sending a message to a tab thread increases the awareness of activity to all users without explicitly notifying everyone.</span></span> <span data-ttu-id="97e0c-213">Isso é conscientização sem ruído.</span><span class="sxs-lookup"><span data-stu-id="97e0c-213">This is awareness without noise.</span></span> <span data-ttu-id="97e0c-214">Além disso, quando você `@mention`  especifica os usuários, a mesma notificação será colocada em seus feeds, vinculando-os diretamente ao encadeamento de tabulação.</span><span class="sxs-lookup"><span data-stu-id="97e0c-214">In addition, when you `@mention`  specific users the same notification will be placed in their feed, deep linking them to the tab thread directly.</span></span>

### <a name="tab-design-best-practices"></a><span data-ttu-id="97e0c-215">Práticas recomendadas de design da guia</span><span class="sxs-lookup"><span data-stu-id="97e0c-215">Tab design best practices</span></span>

* <span data-ttu-id="97e0c-216">As guias pessoais/estáticas devem permitir que os usuários compartilhem conteúdo de uma experiência de aplicativo pessoal com outros membros da equipe.</span><span class="sxs-lookup"><span data-stu-id="97e0c-216">Personal/Static tabs should enable users to share content from a personal app experience with another team members.</span></span>
* <span data-ttu-id="97e0c-217">Guias pessoais/estáticas podem apresentar conteúdo de instâncias com escopo de chat de grupo ou equipe do aplicativo em um único modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="97e0c-217">Personal/Static tabs may present content from team or group chat scoped instances of that app in a single view.</span></span>
* <span data-ttu-id="97e0c-218">Os destinos de link em guias não devem ser vinculados a um navegador externo, mas devem ser vinculados a elementos div contidos no Teams (exemplo-interno, módulos de tarefas, guias, etc.).</span><span class="sxs-lookup"><span data-stu-id="97e0c-218">Link targets in tabs should not link to an external browser but should link to div elements contained within Teams (example-inside, task modules, tabs, etc).</span></span>
* <span data-ttu-id="97e0c-219">As guias devem ser responsivas aos temas da equipe.</span><span class="sxs-lookup"><span data-stu-id="97e0c-219">Tabs should be responsive to Team’s themes.</span></span> <span data-ttu-id="97e0c-220">Quando o tema do teams é alterado, o tema dentro do aplicativo também deve ser alterado para refletir esse tema.</span><span class="sxs-lookup"><span data-stu-id="97e0c-220">When the Teams theme is changed, the theme within the app should also change to reflect that theme.</span></span>
* <span data-ttu-id="97e0c-221">As guias devem usar componentes com estilo de equipe onde for possível.</span><span class="sxs-lookup"><span data-stu-id="97e0c-221">Tabs should use Teams-styled components where possible.</span></span> <span data-ttu-id="97e0c-222">Isso significa adotar fontes do Teams, digitar rampas, paletas de cores, sistema de grade, movimento, Tom de voz, etc.</span><span class="sxs-lookup"><span data-stu-id="97e0c-222">It means adopting Teams fonts, type ramps, color palettes, grid system, motion, tone of voice, etc.</span></span>
* <span data-ttu-id="97e0c-223">As guias devem usar os comportamentos de interação do teams para navegação na página, posição e uso de caixas de diálogo, hierarquias de informações, etc.</span><span class="sxs-lookup"><span data-stu-id="97e0c-223">Tabs should use Teams interaction behaviors for in-page navigation, position, and use of dialogs, information hierarchies, etc.</span></span>
* <span data-ttu-id="97e0c-224">As guias devem usar o menu e/ou Breadcrumbs da equipe padrão para navegação no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="97e0c-224">Tabs should use the standard Teams hamburger menu and/or breadcrumb for in-app navigation.</span></span> <span data-ttu-id="97e0c-225">As guias não devem fornecer uma barra de aplicativos com ícones no trilho esquerdo que estejam em conflito com a navegação do teams principal.</span><span class="sxs-lookup"><span data-stu-id="97e0c-225">Tabs should not provide an app bar with icons in the left rail that conflicts with the main Teams navigation.</span></span>
* <span data-ttu-id="97e0c-226">Guias não devem ter mais do que três níveis de navegação no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="97e0c-226">Tabs should not have more than three levels of navigation within the app.</span></span>
* <span data-ttu-id="97e0c-227">As páginas secundárias e terciários em uma guia devem ser abertas em um modo de exibição L2/L3 na área de guia principal que é navegada por navegação estrutural.</span><span class="sxs-lookup"><span data-stu-id="97e0c-227">Secondary and tertiary pages in a tab should be opened in an L2/L3 view in the main tab area that is navigated via the breadcrumb.</span></span>
* <span data-ttu-id="97e0c-228">Guias que têm recursos de edição complexos dentro do aplicativo devem abrir o modo de exibição editor em várias janelas, em vez de uma guia (para área de trabalho e Web).</span><span class="sxs-lookup"><span data-stu-id="97e0c-228">Tabs that have complex editing capabilities within the app should open the editor view in multi-window rather than a tab (for desktop and web).</span></span>
* <span data-ttu-id="97e0c-229">Para uma experiência de usuário aprimorada, inclua um bot pessoal que envia uma mensagem de boas-vindas ao usuário na primeira execução e responde aos comandos **Hi**, **Help** e **Hello** .</span><span class="sxs-lookup"><span data-stu-id="97e0c-229">For improved user experience include a personal bot that sends a welcome message to the user on the first run and responds to the **hi**, **help**, and **hello** commands.</span></span> <span data-ttu-id="97e0c-230">Você pode consultar a documentação sobre [bots de conversa](../../bots/what-are-bots.md#in-a-one-to-one-chat) para obter mais assistência.</span><span class="sxs-lookup"><span data-stu-id="97e0c-230">You can refer to the documentation on [conversational bots](../../bots/what-are-bots.md#in-a-one-to-one-chat) for further assistance.</span></span>
