---
title: Diretrizes de design para guias
description: Descreve as diretrizes para a criação de guias de conteúdo e colaboração
keywords: Diretrizes de design de equipes referência configuração de guias
ms.openlocfilehash: adf86678a42e2267af00734e1ef85efced882488
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "41672431"
---
# <a name="content-and-conversations-all-at-once-using-tabs"></a><span data-ttu-id="4cd0f-104">Conteúdo e conversas, todos ao mesmo tempo usando guias</span><span class="sxs-lookup"><span data-stu-id="4cd0f-104">Content and conversations, all at once using tabs</span></span>

> [!Important]
> <span data-ttu-id="4cd0f-105">**Guias em clientes móveis**</span><span class="sxs-lookup"><span data-stu-id="4cd0f-105">**Tabs on Mobile Clients**</span></span>
>
> <span data-ttu-id="4cd0f-106">Siga as [orientações para guias em celular](~/tabs/design/tabs-mobile.md) ao criar suas guias.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-106">Follow the [guidance for tabs on mobile](~/tabs/design/tabs-mobile.md) when creating your tabs.</span></span> <span data-ttu-id="4cd0f-107">Se sua guia usa autenticação, você deve atualizar o SDK do JavaScript do Microsoft Teams para a versão 1.4.1 ou posterior, ou a autenticação falhará.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-107">If your tab uses authentication, you must upgrade your Teams JavaScript SDK to version 1.4.1 or later, or authentication will fail.</span></span>
>
> <span data-ttu-id="4cd0f-108">**Guias pessoais (estáticos) no celular:**</span><span class="sxs-lookup"><span data-stu-id="4cd0f-108">**Personal (static) tabs on mobile:**</span></span>
>
> * <span data-ttu-id="4cd0f-109">As guias estáticas (aplicativo pessoal) estão disponíveis na [visualização do desenvolvedor](~/resources/dev-preview/developer-preview-intro.md).</span><span class="sxs-lookup"><span data-stu-id="4cd0f-109">Static tabs (personal app) are available in [developer preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>
> * <span data-ttu-id="4cd0f-110">Ao criar suas guias estáticas, certifique-se de seguir as [orientações para guias em dispositivos móveis](~/tabs/design/tabs-mobile.md)</span><span class="sxs-lookup"><span data-stu-id="4cd0f-110">While building your static tabs, ensure to follow the [guidance for tabs on mobile](~/tabs/design/tabs-mobile.md)</span></span>
>
> <span data-ttu-id="4cd0f-111">**Guias de canal/grupo (configurável) em dispositivos móveis:**</span><span class="sxs-lookup"><span data-stu-id="4cd0f-111">**Channel/group (configurable) tabs on mobile:**</span></span>
>
> * <span data-ttu-id="4cd0f-112">Os clientes móveis só mostram guias com um valor para `websiteUrl`.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-112">Mobile clients only show tabs that have a value for `websiteUrl`.</span></span> <span data-ttu-id="4cd0f-113">Se quiser que a sua guia apareça nos clientes móveis do Microsoft Teams, você deve definir o `websiteUrl`valor de.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-113">If you want your tab to appear on the Teams mobile clients, you must set the value of `websiteUrl`.</span></span>
> * <span data-ttu-id="4cd0f-114">O comportamento de abertura padrão no Mobile é abrir fora do navegador usando `websiteUrl`o.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-114">Default open behavior on mobile is to open outside in browser using the `websiteUrl`.</span></span> <span data-ttu-id="4cd0f-115">Para aplicativos publicados na loja de aplicativos públicos, se você quiser que a guia de canal seja aberta no Teams por padrão, siga as [orientações para guias em dispositivos móveis](~/tabs/design/tabs-mobile.md)e entre em seu representante de suporte para solicitar a lista branca.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-115">For apps published to the public App Store, if you want your channel tab to open inside teams by default, follow the [guidance for tabs on mobile](~/tabs/design/tabs-mobile.md), and reach out to your support rep to request to be whitelisted.</span></span>

<span data-ttu-id="4cd0f-116">Guias são Canvases que você pode usar para compartilhar conteúdo, reter conversas e hospedar serviços de terceiros, tudo em um fluxo de trabalho orgânica da equipe.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-116">Tabs are canvases that you can use to share content, hold conversations, and host third-party services, all within a team’s organic workflow.</span></span> <span data-ttu-id="4cd0f-117">Quando você cria uma guia no Microsoft Teams, ele coloca seu aplicativo Web front e Center onde ele é facilmente acessível contra conversas principais.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-117">When you build a tab in Microsoft Teams, it puts your web app front and center where it’s easily accessible from key conversations.</span></span>

## <a name="guidelines"></a><span data-ttu-id="4cd0f-118">Diretrizes</span><span class="sxs-lookup"><span data-stu-id="4cd0f-118">Guidelines</span></span>

<span data-ttu-id="4cd0f-119">Uma guia boa deve exibir as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="4cd0f-119">A good tab should display the following characteristics:</span></span>

### <a name="focused-functionality"></a><span data-ttu-id="4cd0f-120">Funcionalidade prioritária</span><span class="sxs-lookup"><span data-stu-id="4cd0f-120">Focused functionality</span></span>

<span data-ttu-id="4cd0f-121">As guias funcionam melhor quando são criadas para atender a uma necessidade específica.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-121">Tabs work best when they’re built to address a specific need.</span></span> <span data-ttu-id="4cd0f-122">Concentre-se em um pequeno conjunto de tarefas ou em um subconjunto de dados que é relevante para o canal em que a guia se encontra.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-122">Focus on a small set of tasks or a subset of data that’s relevant to the channel the tab is in.</span></span>

### <a name="reduced-chrome"></a><span data-ttu-id="4cd0f-123">Cromo reduzido</span><span class="sxs-lookup"><span data-stu-id="4cd0f-123">Reduced chrome</span></span>

<span data-ttu-id="4cd0f-124">Evite criar vários painéis em uma guia, adicionar camadas de navegação ou exigir que os usuários rolem verticalmente e horizontalmente em uma guia. Em outras palavras, tente não ter tabulações na guia.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-124">Avoid creating multiple panels in a tab, adding layers of navigation, or requiring users to scroll both vertically and horizontally in one tab. In other words, try not to have tabs in your tab.</span></span>

> [!TIP]
> <span data-ttu-id="4cd0f-125">Evite criar vários painéis em uma guia, adicionar camadas de navegação ou exigir que os usuários rolem verticalmente e horizontalmente em uma guia.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-125">Avoid creating multiple panels in a tab, adding layers of navigation, or requiring users to scroll both vertically and horizontally in one tab.</span></span>

### <a name="integration"></a><span data-ttu-id="4cd0f-126">Integração</span><span class="sxs-lookup"><span data-stu-id="4cd0f-126">Integration</span></span>

<span data-ttu-id="4cd0f-127">Encontre maneiras de notificar os usuários sobre a atividade da guia postando cartões em uma conversa, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-127">Find ways to notify users about tab activity by posting cards to a conversation, for example.</span></span>

### <a name="conversational"></a><span data-ttu-id="4cd0f-128">Coloquial</span><span class="sxs-lookup"><span data-stu-id="4cd0f-128">Conversational</span></span>

<span data-ttu-id="4cd0f-129">Encontre uma maneira de facilitar a conversa em torno de uma guia. Isso garante que o centro de conversas fique no conteúdo, nos dados ou no processo em mãos.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-129">Find a way to facilitate conversation around a tab. This ensures that conversations center on the content, data, or process at hand.</span></span>

### <a name="streamlined-access"></a><span data-ttu-id="4cd0f-130">Acesso simplificado</span><span class="sxs-lookup"><span data-stu-id="4cd0f-130">Streamlined access</span></span>

<span data-ttu-id="4cd0f-131">Certifique-se de que você está concedendo acesso às pessoas certas no momento certo.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-131">Make sure you’re granting access to the right people at the right time.</span></span> <span data-ttu-id="4cd0f-132">Manter o processo de entrada simples evitará a criação de barreiras para contribuição e colaboração.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-132">Keeping your sign-in process simple will avoid creating barriers to contribution and collaboration.</span></span>

### <a name="personality"></a><span data-ttu-id="4cd0f-133">Personalidade</span><span class="sxs-lookup"><span data-stu-id="4cd0f-133">Personality</span></span>

<span data-ttu-id="4cd0f-134">A tela da guia apresenta uma boa oportunidade para marcar sua experiência.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-134">Your tab canvas presents a good opportunity to brand your experience.</span></span> <span data-ttu-id="4cd0f-135">Incorpore seus próprios logotipos, cores e layouts para comunicar personalidade.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-135">Incorporate your own logos, colors, and layouts to communicate personality.</span></span>

<span data-ttu-id="4cd0f-136">O logotipo é uma parte importante da sua identidade e uma conexão com os usuários.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-136">Your logo is an important part of your identity and a connection with your users.</span></span> <span data-ttu-id="4cd0f-137">Portanto, certifique-se de incluí-lo.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-137">So be sure to include it.</span></span>

* <span data-ttu-id="4cd0f-138">Coloque o logotipo no canto esquerdo ou direito ou ao longo da borda inferior</span><span class="sxs-lookup"><span data-stu-id="4cd0f-138">Place your logo in the left or right corner or along the bottom edge</span></span>
* <span data-ttu-id="4cd0f-139">Mantenha seu logotipo pequeno e discreto</span><span class="sxs-lookup"><span data-stu-id="4cd0f-139">Keep your logo small and unobtrusive</span></span>

> [!TIP]
> <span data-ttu-id="4cd0f-140">Trabalhe com o nosso estilo visual para que seu serviço se sente como parte do teams.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-140">Please work with our visual style so your service feels like a part of Teams.</span></span>

---

## <a name="tab-layouts"></a><span data-ttu-id="4cd0f-141">Layouts de guia</span><span class="sxs-lookup"><span data-stu-id="4cd0f-141">Tab layouts</span></span>

[!include[Tab layouts](~/includes/design/tab-layouts.html)]

---

## <a name="types-of-tabs"></a><span data-ttu-id="4cd0f-142">Tipos de guias</span><span class="sxs-lookup"><span data-stu-id="4cd0f-142">Types of tabs</span></span>

[!include[Tab types](~/includes/design/tab-types.html)]

---

## <a name="configuration-page-height"></a><span data-ttu-id="4cd0f-143">Altura da página de configuração</span><span class="sxs-lookup"><span data-stu-id="4cd0f-143">Configuration page height</span></span>

>[!NOTE]
><span data-ttu-id="4cd0f-144">Em setembro de 2018, a altura da [página de configuração](~/tabs/how-to/create-tab-pages/configuration-page.md) da guia foi aumentada enquanto a largura permanece inalterada.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-144">In September 2018, the height for the tab [configuration page](~/tabs/how-to/create-tab-pages/configuration-page.md) was increased while the width remained unchanged.</span></span> <span data-ttu-id="4cd0f-145">Se o seu aplicativo for projetado para o tamanho mais antigo, a página de configuração da guia terá uma grande quantidade de espaço em branco vertical.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-145">If your app is designed for the older size your tab configuration page will have a great deal of vertical whitespace.</span></span> <span data-ttu-id="4cd0f-146">Aplicativos de repositório herdados isentos dessa alteração precisarão entrar em contato com a Microsoft após a atualização para acomodar as novas dimensões.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-146">Legacy store apps exempted from this change will need to contact Microsoft after updating to accommodate the new dimensions.</span></span>

<span data-ttu-id="4cd0f-147">As dimensões da página de configuração de guia:</span><span class="sxs-lookup"><span data-stu-id="4cd0f-147">The dimensions of the tab configuration page:</span></span>

<img width="450px" title="Tamanhos de guias de configuração" src="~/assets/images/tabs/config-dialog-Contoso2.png" />

### <a name="guidelines-for-tab-configuration-page-format"></a><span data-ttu-id="4cd0f-149">Diretrizes para o formato de página de configuração de guia</span><span class="sxs-lookup"><span data-stu-id="4cd0f-149">Guidelines for tab configuration page format</span></span>

* <span data-ttu-id="4cd0f-150">Baseie a altura mínima da área de conteúdo da página de configuração da guia em elementos gráficos de altura fixa.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-150">Base the minimum height of your content area of your tab configuration page on fixed-height graphic elements.</span></span>
* <span data-ttu-id="4cd0f-151">Calcula o espaço vertical disponível (a altura da área de conteúdo na página de configuração) `window.innerHeight`usando o.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-151">Calculate available vertical space (the height of the content area in the configuration page) using `window.innerHeight`.</span></span> <span data-ttu-id="4cd0f-152">Isso retorna o tamanho do `<iframe>` no qual a página de configuração reside, o que pode ser alterado em versões futuras.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-152">This returns the size of the `<iframe>` in which your configuration page resides, which may change in future releases.</span></span> <span data-ttu-id="4cd0f-153">Usando esse valor, seu conteúdo será ajustado automaticamente para futuras alterações.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-153">By using this value your content will adjust automatically to future changes.</span></span>
* <span data-ttu-id="4cd0f-154">Alocar espaço vertical para os elementos de altura variável menos o que é necessário para os elementos de altura fixa.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-154">Allocate vertical space to the variable-height elements minus what's needed for the fixed-height elements.</span></span>
* <span data-ttu-id="4cd0f-155">Para o estado de *logon* , centralizar o conteúdo verticalmente e horizontalmente.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-155">For the *login* state, vertically and horizontally center the content.</span></span>
* <span data-ttu-id="4cd0f-156">Se você quiser uma imagem de plano de fundo, precisará de uma nova imagem, dimensionada para se ajustar à área (preferencial) ou pode manter a mesma imagem e escolher entre:</span><span class="sxs-lookup"><span data-stu-id="4cd0f-156">If you want a background image, you need either a new image, sized to fit the area (preferred), or you can keep the same image and choose between:</span></span>
  * <span data-ttu-id="4cd0f-157">alinhamento no canto superior esquerdo.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-157">aligning to the upper left hand corner.</span></span>
  * <span data-ttu-id="4cd0f-158">dimensionar a imagem para ajustá-la.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-158">scaling the image to fit.</span></span>

<span data-ttu-id="4cd0f-159">Quando dimensionado corretamente, sua página de configuração de guia deve ser semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="4cd0f-159">When properly sized, your tab configuration page should look similar to this:</span></span>

<img width="450px" title="Nova guia de configuração" src="~/assets/images/tabs/config-dialog-Contoso.png" />

## <a name="best-practices"></a><span data-ttu-id="4cd0f-161">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="4cd0f-161">Best practices</span></span>

### <a name="always-include-a-default-state"></a><span data-ttu-id="4cd0f-162">Sempre incluir um estado padrão</span><span class="sxs-lookup"><span data-stu-id="4cd0f-162">Always include a default state</span></span>

<span data-ttu-id="4cd0f-163">Inclua um estado padrão para facilitar a configuração de guias, mesmo que sua guia seja configurável.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-163">Include a default state to make tabs easy to set up even if your tab is configurable.</span></span>

### <a name="deep-linking"></a><span data-ttu-id="4cd0f-164">Vinculação profunda</span><span class="sxs-lookup"><span data-stu-id="4cd0f-164">Deep linking</span></span>

<span data-ttu-id="4cd0f-165">Sempre que possível, cartões e bots devem se vincular detalhadamente a dados mais ricos em uma guia hospedada. Por exemplo, um cartão pode exibir um resumo dos dados de bug, mas clicar nele pode mostrar o erro inteiro em uma guia.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-165">Whenever possible, cards and bots should deep link to richer data in a hosted tab. For example, a card may show a summary of bug data, but clicking it can shows the entire bug in a tab.</span></span>

### <a name="naming"></a><span data-ttu-id="4cd0f-166">Nomenclatura</span><span class="sxs-lookup"><span data-stu-id="4cd0f-166">Naming</span></span>

<span data-ttu-id="4cd0f-167">Em muitos casos, o nome do seu aplicativo pode criar um ótimo nome de guia.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-167">In many cases, the name of your app may make a great tab name.</span></span> <span data-ttu-id="4cd0f-168">Mas considere nomear suas guias de acordo com a funcionalidade que elas fornecem.</span><span class="sxs-lookup"><span data-stu-id="4cd0f-168">But consider naming your tabs according to the functionality they provide.</span></span>
