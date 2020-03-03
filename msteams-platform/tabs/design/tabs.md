---
title: Diretrizes de design para guias
description: Descreve as diretrizes para a criação de guias de conteúdo e colaboração
keywords: Diretrizes de design de equipes referência configuração de guias
ms.openlocfilehash: c718dd897d314ecb5acfbb7cc537b8eead142b0c
ms.sourcegitcommit: 646a8224523be7db96f9686e22d420d62d55d4b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2020
ms.locfileid: "42365259"
---
# <a name="content-and-conversations-all-at-once-using-tabs"></a><span data-ttu-id="262d4-104">Conteúdo e conversas, todos ao mesmo tempo usando guias</span><span class="sxs-lookup"><span data-stu-id="262d4-104">Content and conversations, all at once using tabs</span></span>

> [!Important]
> <span data-ttu-id="262d4-105">**Guias em clientes móveis**</span><span class="sxs-lookup"><span data-stu-id="262d4-105">**Tabs on Mobile Clients**</span></span>
>
> <span data-ttu-id="262d4-106">Siga as [orientações para guias em celular](./tabs-mobile.md) ao criar suas guias.</span><span class="sxs-lookup"><span data-stu-id="262d4-106">Follow the [guidance for tabs on mobile](./tabs-mobile.md) when creating your tabs.</span></span> <span data-ttu-id="262d4-107">Se sua guia usa autenticação, você deve atualizar o SDK do JavaScript do Microsoft Teams para a versão 1.4.1 ou posterior, ou a autenticação falhará.</span><span class="sxs-lookup"><span data-stu-id="262d4-107">If your tab uses authentication, you must upgrade your Teams JavaScript SDK to version 1.4.1 or later, or authentication will fail.</span></span>
>
> <span data-ttu-id="262d4-108">**Guias pessoais (estáticos) no celular:**</span><span class="sxs-lookup"><span data-stu-id="262d4-108">**Personal (static) tabs on mobile:**</span></span>
>
> * <span data-ttu-id="262d4-109">As guias estáticas (aplicativo pessoal) estão disponíveis na [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md).</span><span class="sxs-lookup"><span data-stu-id="262d4-109">Static tabs (personal app) are available in [developer preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>
> * <span data-ttu-id="262d4-110">Ao criar suas guias estáticas, certifique-se de seguir as [orientações para guias em dispositivos móveis](~/tabs/design/tabs-mobile.md)</span><span class="sxs-lookup"><span data-stu-id="262d4-110">While building your static tabs, ensure to follow the [guidance for tabs on mobile](~/tabs/design/tabs-mobile.md)</span></span>
>
> <span data-ttu-id="262d4-111">**Guias de canal/grupo (configurável) em dispositivos móveis:**</span><span class="sxs-lookup"><span data-stu-id="262d4-111">**Channel/group (configurable) tabs on mobile:**</span></span>
>
> * <span data-ttu-id="262d4-112">Os clientes móveis só mostram guias com um valor para `websiteUrl`.</span><span class="sxs-lookup"><span data-stu-id="262d4-112">Mobile clients only show tabs that have a value for `websiteUrl`.</span></span> <span data-ttu-id="262d4-113">Se quiser que a sua guia apareça nos clientes móveis do Microsoft Teams, você deve definir o `websiteUrl`valor de.</span><span class="sxs-lookup"><span data-stu-id="262d4-113">If you want your tab to appear on the Teams mobile clients, you must set the value of `websiteUrl`.</span></span>
> * <span data-ttu-id="262d4-114">O comportamento de abertura padrão no Mobile é abrir fora do navegador usando `websiteUrl`o.</span><span class="sxs-lookup"><span data-stu-id="262d4-114">Default open behavior on mobile is to open outside in browser using the `websiteUrl`.</span></span> <span data-ttu-id="262d4-115">Para aplicativos publicados na loja de aplicativos públicos, se você quiser que a guia de canal seja aberta no Teams por padrão, siga as [orientações para guias em dispositivos móveis](~/tabs/design/tabs-mobile.md)e entre em seu representante de suporte para solicitar a lista branca.</span><span class="sxs-lookup"><span data-stu-id="262d4-115">For apps published to the public App Store, if you want your channel tab to open inside teams by default, follow the [guidance for tabs on mobile](~/tabs/design/tabs-mobile.md), and reach out to your support rep to request to be whitelisted.</span></span>

<span data-ttu-id="262d4-116">Guias são Canvases que você pode usar para compartilhar conteúdo, reter conversas e hospedar serviços de terceiros, tudo em um fluxo de trabalho orgânica da equipe.</span><span class="sxs-lookup"><span data-stu-id="262d4-116">Tabs are canvases that you can use to share content, hold conversations, and host third-party services, all within a team’s organic workflow.</span></span> <span data-ttu-id="262d4-117">Quando você cria uma guia no Microsoft Teams, ele coloca seu aplicativo Web front e Center onde ele é facilmente acessível contra conversas principais.</span><span class="sxs-lookup"><span data-stu-id="262d4-117">When you build a tab in Microsoft Teams, it puts your web app front and center where it’s easily accessible from key conversations.</span></span>

## <a name="guidelines"></a><span data-ttu-id="262d4-118">Diretrizes</span><span class="sxs-lookup"><span data-stu-id="262d4-118">Guidelines</span></span>

<span data-ttu-id="262d4-119">Uma guia boa deve exibir as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="262d4-119">A good tab should display the following characteristics:</span></span>

### <a name="focused-functionality"></a><span data-ttu-id="262d4-120">Funcionalidade prioritária</span><span class="sxs-lookup"><span data-stu-id="262d4-120">Focused functionality</span></span>

<span data-ttu-id="262d4-121">As guias funcionam melhor quando são criadas para atender a uma necessidade específica.</span><span class="sxs-lookup"><span data-stu-id="262d4-121">Tabs work best when they’re built to address a specific need.</span></span> <span data-ttu-id="262d4-122">Concentre-se em um pequeno conjunto de tarefas ou em um subconjunto de dados que é relevante para o canal em que a guia se encontra.</span><span class="sxs-lookup"><span data-stu-id="262d4-122">Focus on a small set of tasks or a subset of data that’s relevant to the channel the tab is in.</span></span>

### <a name="reduced-chrome"></a><span data-ttu-id="262d4-123">Cromo reduzido</span><span class="sxs-lookup"><span data-stu-id="262d4-123">Reduced chrome</span></span>

<span data-ttu-id="262d4-124">Evite criar vários painéis em uma guia, adicionar camadas de navegação ou exigir que os usuários rolem verticalmente e horizontalmente em uma guia. Em outras palavras, tente não ter tabulações na guia.</span><span class="sxs-lookup"><span data-stu-id="262d4-124">Avoid creating multiple panels in a tab, adding layers of navigation, or requiring users to scroll both vertically and horizontally in one tab. In other words, try not to have tabs in your tab.</span></span>

### <a name="integration"></a><span data-ttu-id="262d4-125">Integração</span><span class="sxs-lookup"><span data-stu-id="262d4-125">Integration</span></span>

<span data-ttu-id="262d4-126">Encontre maneiras de notificar os usuários sobre a atividade da guia postando cartões em uma conversa, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="262d4-126">Find ways to notify users about tab activity by posting cards to a conversation, for example.</span></span>

### <a name="conversational"></a><span data-ttu-id="262d4-127">Coloquial</span><span class="sxs-lookup"><span data-stu-id="262d4-127">Conversational</span></span>

<span data-ttu-id="262d4-128">Encontre uma maneira de facilitar a conversa em torno de uma guia. Isso garante que o centro de conversas fique no conteúdo, nos dados ou no processo em mãos.</span><span class="sxs-lookup"><span data-stu-id="262d4-128">Find a way to facilitate conversation around a tab. This ensures that conversations center on the content, data, or process at hand.</span></span>

### <a name="streamlined-access"></a><span data-ttu-id="262d4-129">Acesso simplificado</span><span class="sxs-lookup"><span data-stu-id="262d4-129">Streamlined access</span></span>

<span data-ttu-id="262d4-130">Certifique-se de que você está concedendo acesso às pessoas certas no momento certo.</span><span class="sxs-lookup"><span data-stu-id="262d4-130">Make sure you’re granting access to the right people at the right time.</span></span> <span data-ttu-id="262d4-131">Manter o processo de entrada simples evitará a criação de barreiras para contribuição e colaboração.</span><span class="sxs-lookup"><span data-stu-id="262d4-131">Keeping your sign-in process simple will avoid creating barriers to contribution and collaboration.</span></span>

### <a name="responsiveness-to-window-sizing"></a><span data-ttu-id="262d4-132">Capacidade de resposta para dimensionamento de janela</span><span class="sxs-lookup"><span data-stu-id="262d4-132">Responsiveness to window sizing</span></span>

<span data-ttu-id="262d4-133">As equipes podem ser usadas em tamanhos de janela tão pequenos quanto 720px, então garantir que uma guia possa ser usada em uma pequena janela seja tão importante quanto a usabilidade em resoluções muito altas.</span><span class="sxs-lookup"><span data-stu-id="262d4-133">Teams can be used in window sizes as small as 720px, so making sure that a tab is usable in a small window is just as important as usability at very high resolutions.</span></span>

### <a name="flat-navigation"></a><span data-ttu-id="262d4-134">Navegação simples</span><span class="sxs-lookup"><span data-stu-id="262d4-134">Flat navigation</span></span>

<span data-ttu-id="262d4-135">Pedimos aos desenvolvedores não adicionar o portal inteiro a uma guia. manter a navegação relativamente simples ajuda a manter um modelo de conversa mais simples.</span><span class="sxs-lookup"><span data-stu-id="262d4-135">We ask developers not to add their entire portal to a tab. Keeping the navigation relatively flat helps maintain a simpler conversational model.</span></span> <span data-ttu-id="262d4-136">Em outras palavras, a conversa é sobre uma lista de coisas, como itens de trabalho triantigos, ou uma única coisa, como uma espec.</span><span class="sxs-lookup"><span data-stu-id="262d4-136">In other words, the conversation is about a list of things, such as triaged work items, or a single thing, like a spec.</span></span>

<span data-ttu-id="262d4-137">Há desafios de navegação inerentes com uma hierarquia de navegação profunda em conversas encadeadas.</span><span class="sxs-lookup"><span data-stu-id="262d4-137">There are inherent navigational challenges with deep navigation hierarchy, within threaded conversations.</span></span> <span data-ttu-id="262d4-138">Para a melhor experiência do usuário, a navegação de guia deve ser mantida no mínimo e ser projetada da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="262d4-138">For the best user experience, your tab navigation should be kept to a minimum and be designed as follows:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="262d4-139">**Abre um módulo de tarefa, como um item de trabalho individual ou uma entidade**.</span><span class="sxs-lookup"><span data-stu-id="262d4-139">**Opens a task module such as an individual work item or entity**.</span></span> <span data-ttu-id="262d4-140">Isso impede totalmente o chat e é a melhor opção para manter o chat especificamente sobre a guia e não as subentidades ou experiências de edição.</span><span class="sxs-lookup"><span data-stu-id="262d4-140">This precludes chat entirely and is the best option to keep chat specifically about the tab and not the sub-entities or editing experiences.</span></span>
>* <span data-ttu-id="262d4-141">**Abre uma pseudo caixa de diálogo em um iframe**.</span><span class="sxs-lookup"><span data-stu-id="262d4-141">**Opens a pseudo dialog in an iframe**.</span></span> <span data-ttu-id="262d4-142">Se usado com um plano de fundo em tela, recomendamos usar a cor mais clara em vez do escuro.</span><span class="sxs-lookup"><span data-stu-id="262d4-142">If used with a screened background we recommend using the lighter color rather than the dark.</span></span> <span data-ttu-id="262d4-143">A `app-gray-10 at 30%` transparência funciona bem.</span><span class="sxs-lookup"><span data-stu-id="262d4-143">The `app-gray-10 at 30%` transparency works well.</span></span>
>* <span data-ttu-id="262d4-144">**Abre uma página do navegador**.</span><span class="sxs-lookup"><span data-stu-id="262d4-144">**Opens a browser page**.</span></span>

### <a name="personality"></a><span data-ttu-id="262d4-145">Personalidade</span><span class="sxs-lookup"><span data-stu-id="262d4-145">Personality</span></span>

<span data-ttu-id="262d4-146">A tela da guia apresenta uma ótima oportunidade de marcar sua experiência.</span><span class="sxs-lookup"><span data-stu-id="262d4-146">Your tab canvas presents a great opportunity to brand your experience.</span></span> <span data-ttu-id="262d4-147">O logotipo é uma parte importante da sua identidade e conexão com os usuários. portanto, não se esqueça de incluí-lo:</span><span class="sxs-lookup"><span data-stu-id="262d4-147">Your logo is an important part of your identity and connection with your users., so be sure to include it:</span></span>

> [!div class="checklist"]
>
>* <span data-ttu-id="262d4-148">Coloque o logotipo no canto esquerdo ou direito ou ao longo da borda inferior</span><span class="sxs-lookup"><span data-stu-id="262d4-148">Place your logo in the left or right corner or along the bottom edge</span></span>
> * <span data-ttu-id="262d4-149">Mantenha seu logotipo pequeno e discreto</span><span class="sxs-lookup"><span data-stu-id="262d4-149">Keep your logo small and unobtrusive</span></span>

<span data-ttu-id="262d4-150">A incorporação de suas próprias cores e layouts twill também ajuda na comunicação de personalidade.</span><span class="sxs-lookup"><span data-stu-id="262d4-150">Incorporating your own colors and layouts twill also aid in communicating personality.</span></span>

> [!TIP]
> <span data-ttu-id="262d4-151">Trabalhe com o nosso estilo visual para que seu serviço se sente como parte do teams.</span><span class="sxs-lookup"><span data-stu-id="262d4-151">Please work with our visual style so your service feels like a part of Teams.</span></span> <span data-ttu-id="262d4-152">*Consulte*, por exemplo [Teams Colors] (/Concepts/design/Components/Typography.MD</span><span class="sxs-lookup"><span data-stu-id="262d4-152">*See*, for example [Teams Colors](/concepts/design/components/typography.md</span></span>

---

## <a name="tab-layouts"></a><span data-ttu-id="262d4-153">Layouts de guia</span><span class="sxs-lookup"><span data-stu-id="262d4-153">Tab layouts</span></span>

[!INCLUDE [Tab layouts](../../includes/design/tab-layouts.html)]

---

## <a name="types-of-tabs"></a><span data-ttu-id="262d4-154">Tipos de guias</span><span class="sxs-lookup"><span data-stu-id="262d4-154">Types of tabs</span></span>

[!INCLUDE [Tab types](../../includes/design/tab-types.html)]

---

## <a name="configuration-page-height"></a><span data-ttu-id="262d4-155">Altura da página de configuração</span><span class="sxs-lookup"><span data-stu-id="262d4-155">Configuration page height</span></span>

>[!IMPORTANT]
><span data-ttu-id="262d4-156">Em setembro de 2018, a altura da [página de configuração](~/tabs/how-to/create-tab-pages/configuration-page.md) da guia foi aumentada enquanto a largura permanece inalterada.</span><span class="sxs-lookup"><span data-stu-id="262d4-156">In September 2018, the height for the tab [configuration page](~/tabs/how-to/create-tab-pages/configuration-page.md) was increased while the width remained unchanged.</span></span> <span data-ttu-id="262d4-157">Se o seu aplicativo for projetado para o tamanho mais antigo, a página de configuração da guia terá uma grande quantidade de espaço em branco vertical.</span><span class="sxs-lookup"><span data-stu-id="262d4-157">If your app is designed for the older size your tab configuration page will have a great deal of vertical whitespace.</span></span> <span data-ttu-id="262d4-158">Aplicativos de repositório herdados isentos dessa alteração precisarão entrar em contato com a Microsoft após a atualização para acomodar as novas dimensões.</span><span class="sxs-lookup"><span data-stu-id="262d4-158">Legacy store apps exempted from this change will need to contact Microsoft after updating to accommodate the new dimensions.</span></span>

<span data-ttu-id="262d4-159">As dimensões da página de configuração de guia:</span><span class="sxs-lookup"><span data-stu-id="262d4-159">The dimensions of the tab configuration page:</span></span>

<img width="450px" title="Tamanhos de guias de configuração" src="~/assets/images/tabs/config-dialog-Contoso2.png" />

### <a name="guidelines-for-tab-configuration-page-format"></a><span data-ttu-id="262d4-161">Diretrizes para o formato de página de configuração de guia</span><span class="sxs-lookup"><span data-stu-id="262d4-161">Guidelines for tab configuration page format</span></span>

* <span data-ttu-id="262d4-162">Baseie a altura mínima da área de conteúdo da página de configuração da guia em elementos gráficos de altura fixa.</span><span class="sxs-lookup"><span data-stu-id="262d4-162">Base the minimum height of your content area of your tab configuration page on fixed-height graphic elements.</span></span>
* <span data-ttu-id="262d4-163">Calcula o espaço vertical disponível (a altura da área de conteúdo na página de configuração) `window.innerHeight`usando o.</span><span class="sxs-lookup"><span data-stu-id="262d4-163">Calculate available vertical space (the height of the content area in the configuration page) using `window.innerHeight`.</span></span> <span data-ttu-id="262d4-164">Isso retorna o tamanho do `<iframe>` no qual a página de configuração reside, o que pode ser alterado em versões futuras.</span><span class="sxs-lookup"><span data-stu-id="262d4-164">This returns the size of the `<iframe>` in which your configuration page resides, which may change in future releases.</span></span> <span data-ttu-id="262d4-165">Usando esse valor, seu conteúdo será ajustado automaticamente para futuras alterações.</span><span class="sxs-lookup"><span data-stu-id="262d4-165">By using this value your content will adjust automatically to future changes.</span></span>
* <span data-ttu-id="262d4-166">Alocar espaço vertical para os elementos de altura variável menos o que é necessário para os elementos de altura fixa.</span><span class="sxs-lookup"><span data-stu-id="262d4-166">Allocate vertical space to the variable-height elements minus what's needed for the fixed-height elements.</span></span>
* <span data-ttu-id="262d4-167">Para o estado de *logon* , centralizar o conteúdo verticalmente e horizontalmente.</span><span class="sxs-lookup"><span data-stu-id="262d4-167">For the *login* state, vertically and horizontally center the content.</span></span>
* <span data-ttu-id="262d4-168">Se você quiser uma imagem de plano de fundo, precisará de uma nova imagem, dimensionada para se ajustar à área (preferencial) ou pode manter a mesma imagem e escolher entre:</span><span class="sxs-lookup"><span data-stu-id="262d4-168">If you want a background image, you need either a new image, sized to fit the area (preferred), or you can keep the same image and choose between:</span></span>
  * <span data-ttu-id="262d4-169">alinhamento no canto superior esquerdo.</span><span class="sxs-lookup"><span data-stu-id="262d4-169">aligning to the upper left hand corner.</span></span>
  * <span data-ttu-id="262d4-170">dimensionar a imagem para ajustá-la.</span><span class="sxs-lookup"><span data-stu-id="262d4-170">scaling the image to fit.</span></span>

<span data-ttu-id="262d4-171">Quando dimensionado corretamente, sua página de configuração de guia deve ser semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="262d4-171">When properly sized, your tab configuration page should look similar to this:</span></span>

<img width="450px" title="Nova guia de configuração" src="~/assets/images/tabs/config-dialog-Contoso.png" />

## <a name="best-practices"></a><span data-ttu-id="262d4-173">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="262d4-173">Best practices</span></span>

### <a name="always-include-a-default-state"></a><span data-ttu-id="262d4-174">Sempre incluir um estado padrão</span><span class="sxs-lookup"><span data-stu-id="262d4-174">Always include a default state</span></span>

<span data-ttu-id="262d4-175">Inclua um estado padrão para facilitar a configuração de guias, mesmo que sua guia seja configurável.</span><span class="sxs-lookup"><span data-stu-id="262d4-175">Include a default state to make tabs easy to set up even if your tab is configurable.</span></span>

### <a name="deep-linking"></a><span data-ttu-id="262d4-176">Vinculação profunda</span><span class="sxs-lookup"><span data-stu-id="262d4-176">Deep linking</span></span>

<span data-ttu-id="262d4-177">Sempre que possível, cartões e bots devem se vincular detalhadamente a dados mais ricos em uma guia hospedada. Por exemplo, um cartão pode exibir um resumo dos dados de bug, mas clicar nele pode mostrar o erro inteiro em uma guia.</span><span class="sxs-lookup"><span data-stu-id="262d4-177">Whenever possible, cards and bots should deep link to richer data in a hosted tab. For example, a card may show a summary of bug data, but clicking it can shows the entire bug in a tab.</span></span>

### <a name="naming"></a><span data-ttu-id="262d4-178">Nomenclatura</span><span class="sxs-lookup"><span data-stu-id="262d4-178">Naming</span></span>

<span data-ttu-id="262d4-179">Em muitos casos, o nome do seu aplicativo criará um nome de guia ótimo.</span><span class="sxs-lookup"><span data-stu-id="262d4-179">In many cases, the name of your app will make a great tab name.</span></span> <span data-ttu-id="262d4-180">Mas, também considere nomear suas guias de acordo com a funcionalidade que elas fornecem.</span><span class="sxs-lookup"><span data-stu-id="262d4-180">But, also consider naming your tabs according to the functionality they provide.</span></span>

## <a name="notifications-for-tabs"></a><span data-ttu-id="262d4-181">Notificações para guias</span><span class="sxs-lookup"><span data-stu-id="262d4-181">Notifications for tabs</span></span>

<span data-ttu-id="262d4-182">Há dois modos de notificação para alterações de conteúdo de guia:</span><span class="sxs-lookup"><span data-stu-id="262d4-182">There are two modes of notification for tab content changes:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="262d4-183">**Use a API do aplicativo para notificar os usuários sobre as alterações**.</span><span class="sxs-lookup"><span data-stu-id="262d4-183">**Use the app api to notify users of changes**.</span></span> <span data-ttu-id="262d4-184">Esta mensagem aparecerá no feed de atividades do usuário e no link profundo para a guia. *consulte*  [criar links de profundas para conteúdo e recursos no Microsoft Teams](/concepts/build-and-test/deep-links?view=msteams-client-js-latest)</span><span class="sxs-lookup"><span data-stu-id="262d4-184">This message will show up in the user’s activity feed and deep link to the tab. *See*  [Create deep links to content and features in Microsoft Teams](/concepts/build-and-test/deep-links?view=msteams-client-js-latest)</span></span>
> * <span data-ttu-id="262d4-185">**Use um bot**.</span><span class="sxs-lookup"><span data-stu-id="262d4-185">**Use a bot**.</span></span> <span data-ttu-id="262d4-186">Esse método é preferível, especialmente se o thread de guia for direcionado.</span><span class="sxs-lookup"><span data-stu-id="262d4-186">This method is preferred especially if the Tab thread is targeted.</span></span> <span data-ttu-id="262d4-187">O resultado será que a conversa encadeada da guia será movida para o modo de exibição como ativo recentemente.</span><span class="sxs-lookup"><span data-stu-id="262d4-187">The result will be that the tab’s threaded conversation will be moved into view as recently active.</span></span> <span data-ttu-id="262d4-188">Esse método também permite uma certa sofisticação na forma como a notificação é enviada.</span><span class="sxs-lookup"><span data-stu-id="262d4-188">This method also allows for some sophistication in how the notification is sent.</span></span>

  <span data-ttu-id="262d4-189">Enviar uma mensagem para um thread de guia aumenta a conscientização da atividade para todos os usuários sem notificar explicitamente todos.</span><span class="sxs-lookup"><span data-stu-id="262d4-189">Sending a message to a tab thread increases the awareness of activity to all users without explicitly notifying everyone.</span></span> <span data-ttu-id="262d4-190">Isso é conscientização sem ruído.</span><span class="sxs-lookup"><span data-stu-id="262d4-190">This is awareness without noise.</span></span> <span data-ttu-id="262d4-191">Além disso, quando você `@mention` especifica os usuários, a mesma notificação será colocada em seus feeds, vinculando-os diretamente ao encadeamento de tabulação.</span><span class="sxs-lookup"><span data-stu-id="262d4-191">In addition, when you `@mention`  specific users the same notification will be placed in their feed, deep linking them to the tab thread directly.</span></span>
