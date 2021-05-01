---
title: Criar uma listagem de loja para seu aplicativo
description: Descreve como criar uma listagem de loja para seu Microsoft Teams app.
ms.topic: how-to
localization_priority: Normal
author: heath-hamilton
ms.author: surbhigupta
ms.openlocfilehash: 270936ca967c17caaa8a56f85057b20ca3d6a409
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101426"
---
# <a name="create-a-store-listing-for-your-microsoft-teams-app"></a><span data-ttu-id="37e0d-103">Criar uma listagem da loja para seu Microsoft Teams app</span><span class="sxs-lookup"><span data-stu-id="37e0d-103">Create a store listing for your Microsoft Teams app</span></span>

<span data-ttu-id="37e0d-104">As informações que você envia ao [Partner Center](https://partner.microsoft.com)&#8212;incluindo seu nome, descrições, ícones e imagens&#8212;se tornam o Microsoft Teams store e a listagem do Microsoft AppSource para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="37e0d-104">The information that you submit to [Partner Center](https://partner.microsoft.com)&#8212;including your name, descriptions, icons, and images&#8212;becomes the Microsoft Teams store and Microsoft AppSource listing for your app.</span></span>

<span data-ttu-id="37e0d-105">Uma listagem da loja pode ser a primeira impressão de alguém do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="37e0d-105">A store listing may be someone's first impression of your app.</span></span> <span data-ttu-id="37e0d-106">Aumente suas instalações com uma listagem que transmite efetivamente os benefícios, a funcionalidade e a marca do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="37e0d-106">Increase your installations with a listing that effectively conveys your app's benefits, functionality, and brand.</span></span>

## <a name="specify-a-short-name"></a><span data-ttu-id="37e0d-107">Especificar um nome curto</span><span class="sxs-lookup"><span data-stu-id="37e0d-107">Specify a short name</span></span>

<span data-ttu-id="37e0d-108">O nome do seu aplicativo (especificamente, seu [*nome*](~/resources/schema/manifest-schema.md#name)curto ) desempenha uma função crucial na forma como os usuários o descobrem na loja.</span><span class="sxs-lookup"><span data-stu-id="37e0d-108">Your app's name (specifically, its [*short name*](~/resources/schema/manifest-schema.md#name)) plays a crucial role in how users discover it in the store.</span></span>

<span data-ttu-id="37e0d-109">O exemplo a seguir destaca onde o nome curto de um aplicativo é exibido em uma listagem da loja.</span><span class="sxs-lookup"><span data-stu-id="37e0d-109">The following example highlights where an app's short name displays in a store listing.</span></span>

:::image type="content" source="../../../../assets/images/store-detail-page/AppName-02.png" alt-text="Exemplo de captura de tela realça onde o nome curto de um aplicativo é exibido em uma listagem da loja.":::

### <a name="best-practices-for-names"></a><span data-ttu-id="37e0d-111">Práticas recomendadas para nomes</span><span class="sxs-lookup"><span data-stu-id="37e0d-111">Best practices for names</span></span>

<span data-ttu-id="37e0d-112">**Faça:**</span><span class="sxs-lookup"><span data-stu-id="37e0d-112">**Do:**</span></span>

* <span data-ttu-id="37e0d-113">Escolha um nome simples e memorável que indica o que seu aplicativo faz.</span><span class="sxs-lookup"><span data-stu-id="37e0d-113">Choose a simple, memorable name that hints at what your app does.</span></span>
* <span data-ttu-id="37e0d-114">Seja distinto.</span><span class="sxs-lookup"><span data-stu-id="37e0d-114">Be distinctive.</span></span>
* <span data-ttu-id="37e0d-115">Evite erros de digitação e gramatical.</span><span class="sxs-lookup"><span data-stu-id="37e0d-115">Avoid typos and grammatical errors.</span></span>

<span data-ttu-id="37e0d-116">**Não faça:**</span><span class="sxs-lookup"><span data-stu-id="37e0d-116">**Don't:**</span></span>

* <span data-ttu-id="37e0d-117">Use termos profano ou depreciativo.</span><span class="sxs-lookup"><span data-stu-id="37e0d-117">Use profane or derogatory terms.</span></span>
* <span data-ttu-id="37e0d-118">Use linguagem racial ou culturalmente insensível.</span><span class="sxs-lookup"><span data-stu-id="37e0d-118">Use racially or culturally insensitive language.</span></span>
* <span data-ttu-id="37e0d-119">Use termos genéricos ou nomes semelhantes aos aplicativos existentes.</span><span class="sxs-lookup"><span data-stu-id="37e0d-119">Use generic terms or names similar to existing apps.</span></span>
* <span data-ttu-id="37e0d-120">Inclua "Teams", "Microsoft", nomes de produtos da Microsoft existentes/futuros ou "aplicativo" no nome.</span><span class="sxs-lookup"><span data-stu-id="37e0d-120">Include "Teams", "Microsoft", existing/upcoming Microsoft product names, or  "app" in the name.</span></span>

> [!NOTE]
> <span data-ttu-id="37e0d-121">Se seu aplicativo faz parte de uma parceria oficial com a Microsoft, o nome do seu aplicativo deve vir primeiro (por exemplo, *Salesforce Connector para* Microsoft Teams ).</span><span class="sxs-lookup"><span data-stu-id="37e0d-121">If your app is part of an official partnership with Microsoft, the name of your app must come first (for example, *Salesforce Connector for Microsoft Teams*).</span></span>

## <a name="write-descriptions"></a><span data-ttu-id="37e0d-122">Descrições de gravação</span><span class="sxs-lookup"><span data-stu-id="37e0d-122">Write descriptions</span></span>

<span data-ttu-id="37e0d-123">Você precisa de uma descrição curta e longa do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="37e0d-123">You need a short and long description of your app.</span></span>

### <a name="short-description"></a><span data-ttu-id="37e0d-124">Descrição breve</span><span class="sxs-lookup"><span data-stu-id="37e0d-124">Short description</span></span>

<span data-ttu-id="37e0d-125">Um resumo conciso do seu aplicativo que deve ser original, envolvente e direcionado para seu público-alvo.</span><span class="sxs-lookup"><span data-stu-id="37e0d-125">A concise summary of your app that should be original, engaging, and directed at your target audience.</span></span> <span data-ttu-id="37e0d-126">O ideal é manter a descrição curta em uma frase.</span><span class="sxs-lookup"><span data-stu-id="37e0d-126">Ideally, keep the short description to one sentence.</span></span>

<span data-ttu-id="37e0d-127">O exemplo a seguir destaca onde a descrição curta de um aplicativo é exibida em uma listagem da loja:</span><span class="sxs-lookup"><span data-stu-id="37e0d-127">The following example highlights where an app's short description displays in a store listing:</span></span>

:::image type="content" source="~/assets/images/store-detail-page/ShortDescription-02.png" alt-text="Exemplo de captura de tela realça onde a descrição curta de um aplicativo é exibida em uma listagem da loja.":::

#### <a name="best-practices-for-short-descriptions"></a><span data-ttu-id="37e0d-129">Práticas recomendadas para descrições curtas</span><span class="sxs-lookup"><span data-stu-id="37e0d-129">Best practices for short descriptions</span></span>

<span data-ttu-id="37e0d-130">**Faça:**</span><span class="sxs-lookup"><span data-stu-id="37e0d-130">**Do:**</span></span>

* <span data-ttu-id="37e0d-131">Fale primeiro as informações mais importantes.</span><span class="sxs-lookup"><span data-stu-id="37e0d-131">Put the most important information first.</span></span>
* <span data-ttu-id="37e0d-132">Inclua palavras-chave que os clientes provavelmente procurarão.</span><span class="sxs-lookup"><span data-stu-id="37e0d-132">Include keywords that customers are likely to search for.</span></span>

<span data-ttu-id="37e0d-133">**Não faça:**</span><span class="sxs-lookup"><span data-stu-id="37e0d-133">**Don't:**</span></span>

* <span data-ttu-id="37e0d-134">Repita o nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="37e0d-134">Repeat your app name.</span></span>
* <span data-ttu-id="37e0d-135">Conte com jargão ou terminologia especializada.</span><span class="sxs-lookup"><span data-stu-id="37e0d-135">Rely on jargon or specialized terminology.</span></span> <span data-ttu-id="37e0d-136">(Não é possível supor que os usuários saibam o que procurar.)</span><span class="sxs-lookup"><span data-stu-id="37e0d-136">(You can't assume users know what to look for.)</span></span>

### <a name="long-description"></a><span data-ttu-id="37e0d-137">Descrição longa</span><span class="sxs-lookup"><span data-stu-id="37e0d-137">Long description</span></span>

<span data-ttu-id="37e0d-138">A descrição longa pode fornecer uma narração envolvente que realça os principais recursos do seu aplicativo, os problemas que ele resolve e seu público-alvo.</span><span class="sxs-lookup"><span data-stu-id="37e0d-138">The long description can provide an engaging narrative that highlights your app's main features, the problems it solves, and its target audience.</span></span> <span data-ttu-id="37e0d-139">Embora essa descrição possa ter até 4.000 caracteres, a maioria dos usuários lerá apenas entre 300 e 500 palavras.</span><span class="sxs-lookup"><span data-stu-id="37e0d-139">While this description can be as long as 4000 characters, most users will only read between 300-500 words.</span></span>

<span data-ttu-id="37e0d-140">O exemplo a seguir destaca onde a descrição longa de um aplicativo é exibida em uma listagem da loja:</span><span class="sxs-lookup"><span data-stu-id="37e0d-140">The following example highlights where an app's long description displays in a store listing:</span></span>

:::image type="content" source="~/assets/images/store-detail-page/ShortDescription-02.png" alt-text="Exemplo de captura de tela realça onde a descrição longa de um aplicativo é exibida em uma listagem da loja.":::

#### <a name="usage-examples"></a><span data-ttu-id="37e0d-142">Exemplos de uso</span><span class="sxs-lookup"><span data-stu-id="37e0d-142">Usage examples</span></span>

<span data-ttu-id="37e0d-143">As frases a seguir são exemplos do que é permitido ao escrever descrições longas:</span><span class="sxs-lookup"><span data-stu-id="37e0d-143">The following phrases are examples of what's allowed when writing long descriptions:</span></span>

* <span data-ttu-id="37e0d-144">"<seu *nome de aplicativo*> funciona com Microsoft Teams"</span><span class="sxs-lookup"><span data-stu-id="37e0d-144">"<*Your app name*> works with Microsoft Teams"</span></span>
* <span data-ttu-id="37e0d-145">"... um <*tipo de aplicativo>* para Microsoft Teams"</span><span class="sxs-lookup"><span data-stu-id="37e0d-145">"... a <*type of app*> for Microsoft Teams"</span></span>
* <span data-ttu-id="37e0d-146">"<seu *nome de aplicativo*> se integra ao Microsoft Teams"</span><span class="sxs-lookup"><span data-stu-id="37e0d-146">"<*Your app name*> integrates with Microsoft Teams"</span></span>
* <span data-ttu-id="37e0d-147">"... integrado ao Microsoft Teams"</span><span class="sxs-lookup"><span data-stu-id="37e0d-147">"... integrated with Microsoft Teams"</span></span>
* <span data-ttu-id="37e0d-148">"... para usuários que trabalham com Microsoft Teams"</span><span class="sxs-lookup"><span data-stu-id="37e0d-148">"... for users working with Microsoft Teams"</span></span>
* <span data-ttu-id="37e0d-149">"... para <*tarefa específica>* dentro Microsoft Teams"</span><span class="sxs-lookup"><span data-stu-id="37e0d-149">"... for <*specific task*> within Microsoft Teams"</span></span>
* <span data-ttu-id="37e0d-150">"... built on ..."</span><span class="sxs-lookup"><span data-stu-id="37e0d-150">"... built on ..."</span></span>
* <span data-ttu-id="37e0d-151">"... é executado em ..."</span><span class="sxs-lookup"><span data-stu-id="37e0d-151">"... runs on ..."</span></span>
* <span data-ttu-id="37e0d-152">"... habilitado por ..."</span><span class="sxs-lookup"><span data-stu-id="37e0d-152">"... enabled by ..."</span></span>
* <span data-ttu-id="37e0d-153">"... desenvolvido para ..."</span><span class="sxs-lookup"><span data-stu-id="37e0d-153">"... developed for ..."</span></span>
* <span data-ttu-id="37e0d-154">"... projetado para ..."</span><span class="sxs-lookup"><span data-stu-id="37e0d-154">"... designed for ..."</span></span>

#### <a name="best-practices-for-long-descriptions"></a><span data-ttu-id="37e0d-155">Práticas recomendadas para descrições longas</span><span class="sxs-lookup"><span data-stu-id="37e0d-155">Best practices for long descriptions</span></span>

<span data-ttu-id="37e0d-156">**Faça:**</span><span class="sxs-lookup"><span data-stu-id="37e0d-156">**Do:**</span></span>

* <span data-ttu-id="37e0d-157">Use [Markdown](https://support.office.com/article/use-markdown-formatting-in-teams-4d10bd65-55e2-4b2d-a1f3-2bebdcd2c772) para formatar sua descrição.</span><span class="sxs-lookup"><span data-stu-id="37e0d-157">Use [Markdown](https://support.office.com/article/use-markdown-formatting-in-teams-4d10bd65-55e2-4b2d-a1f3-2bebdcd2c772) to format your description.</span></span>
* <span data-ttu-id="37e0d-158">List features with bullet points so it's easier to scan the description.</span><span class="sxs-lookup"><span data-stu-id="37e0d-158">List features with bullet points so it's easier to scan the description.</span></span>
* <span data-ttu-id="37e0d-159">Use voz ativa e fale diretamente com os usuários (por exemplo, *você pode ...*).</span><span class="sxs-lookup"><span data-stu-id="37e0d-159">Use active voice and speak to users directly (for example, *You can ...*).</span></span>
* <span data-ttu-id="37e0d-160">Inclua uma ajuda ou um link de suporte.</span><span class="sxs-lookup"><span data-stu-id="37e0d-160">Include a help or support link.</span></span>
* <span data-ttu-id="37e0d-161">Identifique o seguinte, se aplicável: limitações, configurar informações, dependências de conta e atualizações de versão.</span><span class="sxs-lookup"><span data-stu-id="37e0d-161">Identify the following if applicable: limitations, set up information, account dependencies, and release updates.</span></span>

<span data-ttu-id="37e0d-162">**Não faça:**</span><span class="sxs-lookup"><span data-stu-id="37e0d-162">**Don't:**</span></span>

* <span data-ttu-id="37e0d-163">Exceder 500 palavras.</span><span class="sxs-lookup"><span data-stu-id="37e0d-163">Exceed 500 words.</span></span>
* <span data-ttu-id="37e0d-164">Inclua muitas palavras-chave.</span><span class="sxs-lookup"><span data-stu-id="37e0d-164">Include too many keywords.</span></span> <span data-ttu-id="37e0d-165">(Isso distrai e não ajuda as pessoas a encontrar seu aplicativo.)</span><span class="sxs-lookup"><span data-stu-id="37e0d-165">(It's distracting and won't help people find your app.)</span></span>
* <span data-ttu-id="37e0d-166">Use o seguinte idioma, a menos que o aplicativo tenha passado por um processo de certificação oficial:</span><span class="sxs-lookup"><span data-stu-id="37e0d-166">Use the following language unless the app has gone through an official certification process:</span></span>
  * <span data-ttu-id="37e0d-167">"... certificado para ..."</span><span class="sxs-lookup"><span data-stu-id="37e0d-167">"... certified for ..."</span></span>
  * <span data-ttu-id="37e0d-168">" ... alimentado por ..."</span><span class="sxs-lookup"><span data-stu-id="37e0d-168">" ... powered by ..."</span></span>

### <a name="best-practices-for-all-descriptions"></a><span data-ttu-id="37e0d-169">Práticas recomendadas para todas as descrições</span><span class="sxs-lookup"><span data-stu-id="37e0d-169">Best practices for all descriptions</span></span>

<span data-ttu-id="37e0d-170">**Faça:**</span><span class="sxs-lookup"><span data-stu-id="37e0d-170">**Do:**</span></span>

* <span data-ttu-id="37e0d-171">Fazer referência a nomes de produtos da Microsoft somente quando necessário.</span><span class="sxs-lookup"><span data-stu-id="37e0d-171">Reference Microsoft product names only when necessary.</span></span> <span data-ttu-id="37e0d-172">Para obter mais informações sobre as diretrizes, consulte [Diretrizes de Marca](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general)e Marca da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="37e0d-172">For more information on the guidelines, see [Microsoft Trademark and Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general).</span></span>
* <span data-ttu-id="37e0d-173">Se você precisar fazer referência **Teams,** escreva a primeira referência como **Microsoft Teams**.</span><span class="sxs-lookup"><span data-stu-id="37e0d-173">If you need to reference **Teams**, write the first reference as **Microsoft Teams**.</span></span> <span data-ttu-id="37e0d-174">Referências subsequentes podem ser reduzidas **para Teams**.</span><span class="sxs-lookup"><span data-stu-id="37e0d-174">Subsequent references can be shortened to **Teams**.</span></span>
* <span data-ttu-id="37e0d-175">Consulte **Microsoft 365** em vez de **Office 365**.</span><span class="sxs-lookup"><span data-stu-id="37e0d-175">Refer to **Microsoft 365** instead of **Office 365**.</span></span>
* <span data-ttu-id="37e0d-176">Evite erros de digitação e gramatical.</span><span class="sxs-lookup"><span data-stu-id="37e0d-176">Avoid typos and grammatical errors.</span></span>
* <span data-ttu-id="37e0d-177">Evite maiúsculas desnecessárias (por exemplo, **Usuários** em vez de **usuários**).</span><span class="sxs-lookup"><span data-stu-id="37e0d-177">Avoid unnecessary capitalizations (for example, **Users** instead of **users**).</span></span>
* <span data-ttu-id="37e0d-178">Evite acrônimos.</span><span class="sxs-lookup"><span data-stu-id="37e0d-178">Avoid acronyms.</span></span>

<span data-ttu-id="37e0d-179">**Não faça:**</span><span class="sxs-lookup"><span data-stu-id="37e0d-179">**Don't:**</span></span>

* <span data-ttu-id="37e0d-180">Abreviar a Microsoft como **MS** ou **MSFT**.</span><span class="sxs-lookup"><span data-stu-id="37e0d-180">Abbreviate Microsoft as **MS** or **MSFT**.</span></span>
* <span data-ttu-id="37e0d-181">Indique que o aplicativo é uma oferta da Microsoft, incluindo o uso de lemas ou linhas de marcação da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="37e0d-181">Indicate the app is an offering from Microsoft, including using Microsoft slogans or taglines.</span></span>
* <span data-ttu-id="37e0d-182">Use nomes de marca protegidos por direitos autorais que você não possui.</span><span class="sxs-lookup"><span data-stu-id="37e0d-182">Use copyrighted brand names you don't own.</span></span>

## <a name="adhere-to-icon-design-guidelines"></a><span data-ttu-id="37e0d-183">Seguir as diretrizes de design de ícones</span><span class="sxs-lookup"><span data-stu-id="37e0d-183">Adhere to icon design guidelines</span></span>

<span data-ttu-id="37e0d-184">Os ícones são um dos principais elementos que os usuários veem ao navegar na loja.</span><span class="sxs-lookup"><span data-stu-id="37e0d-184">Icons are one of the main elements users see when browsing the store.</span></span> <span data-ttu-id="37e0d-185">Seus ícones devem comunicar a finalidade da marca do seu aplicativo enquanto também aderem aos Teams requisitos.</span><span class="sxs-lookup"><span data-stu-id="37e0d-185">Your icons should communicate your app's brand purpose while also adhering to Teams requirements.</span></span>

<span data-ttu-id="37e0d-186">Para obter mais informações, [consulte orientações específicas sobre como projetar Teams ícones do aplicativo.](~/concepts/build-and-test/apps-package.md#app-icons)</span><span class="sxs-lookup"><span data-stu-id="37e0d-186">For more information, see [specific guidance on designing Teams app icons](~/concepts/build-and-test/apps-package.md#app-icons).</span></span>

## <a name="capture-screenshots"></a><span data-ttu-id="37e0d-187">Capturar capturas de tela</span><span class="sxs-lookup"><span data-stu-id="37e0d-187">Capture screenshots</span></span>

<span data-ttu-id="37e0d-188">As capturas de tela fornecem uma visualização visual proeminente do seu aplicativo para complementar o nome, o ícone e as descrições do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="37e0d-188">Screenshots provide a prominent visual preview of your app to complement your app name, icon, and descriptions.</span></span>

### <a name="requirements-for-screenshots"></a><span data-ttu-id="37e0d-189">Requisitos para capturas de tela</span><span class="sxs-lookup"><span data-stu-id="37e0d-189">Requirements for screenshots</span></span>

* <span data-ttu-id="37e0d-190">Até cinco capturas de tela por listagem.</span><span class="sxs-lookup"><span data-stu-id="37e0d-190">Up to five screenshots per listing.</span></span>
* <span data-ttu-id="37e0d-191">Os tipos de arquivo com suporte incluem PNG, JPEG e GIF.</span><span class="sxs-lookup"><span data-stu-id="37e0d-191">Supported file types include PNG, JPEG, and GIF.</span></span>
* <span data-ttu-id="37e0d-192">As dimensões devem ter 1366 x 768 pixels.</span><span class="sxs-lookup"><span data-stu-id="37e0d-192">Dimensions should be 1366x768 pixels.</span></span>
* <span data-ttu-id="37e0d-193">Tamanho máximo de 1.024 KB.</span><span class="sxs-lookup"><span data-stu-id="37e0d-193">Maximum size of 1,024 KB.</span></span>

### <a name="best-practices-for-screenshots"></a><span data-ttu-id="37e0d-194">Práticas recomendadas para capturas de tela</span><span class="sxs-lookup"><span data-stu-id="37e0d-194">Best practices for screenshots</span></span>

<span data-ttu-id="37e0d-195">**Faça:**</span><span class="sxs-lookup"><span data-stu-id="37e0d-195">**Do:**</span></span>

* <span data-ttu-id="37e0d-196">Concentre-se nos recursos do seu aplicativo (por exemplo, como as pessoas podem se comunicar com seu bot).</span><span class="sxs-lookup"><span data-stu-id="37e0d-196">Focus on your app's capabilities (for example, how people can communicate with your bot).</span></span>
* <span data-ttu-id="37e0d-197">Inclua conteúdo que represente com precisão seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="37e0d-197">Include content that accurately represents your app.</span></span>
* <span data-ttu-id="37e0d-198">Use texto criteriosamente.</span><span class="sxs-lookup"><span data-stu-id="37e0d-198">Use text judiciously.</span></span>
* Capturas de tela de quadro com uma cor que reflete sua marca e incluem conteúdo de marketing, semelhante ao exemplo do [Freshdesk](https://appsource.microsoft.com/product/office/WA104381505?src=office&tab=Overview) a seguir (requisitos de dimensão se aplicam a toda a imagem e não apenas à captura de tela): Exemplo de captura de tela do aplicativo de terceiros   :::image type="content" source="../../../../assets/images/freshdesk.png" alt-text="Freshdesk":::

<span data-ttu-id="37e0d-200">**Não faça:**</span><span class="sxs-lookup"><span data-stu-id="37e0d-200">**Don't:**</span></span>

* <span data-ttu-id="37e0d-201">Mostrar dispositivos específicos, como telefones ou laptops.</span><span class="sxs-lookup"><span data-stu-id="37e0d-201">Show specific devices, such as phones or laptops.</span></span>
* <span data-ttu-id="37e0d-202">Exibe o cromado ou a interface do usuário que não está em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="37e0d-202">Display chrome or UI that isn't in your app.</span></span>
* <span data-ttu-id="37e0d-203">Capture qualquer Teams ou interface do usuário do navegador em suas capturas de tela.</span><span class="sxs-lookup"><span data-stu-id="37e0d-203">Capture any Teams or browser UI in your screenshots.</span></span>
* <span data-ttu-id="37e0d-204">Inclua simulações que refletem imprecisamente a interface do usuário real do aplicativo, como mostrar seu aplicativo em um navegador em vez de uma guia Teams.</span><span class="sxs-lookup"><span data-stu-id="37e0d-204">Include mockups that inaccurately reflect your app's actual UI, such as showing your app in  a browser instead of a Teams tab.</span></span>

<span data-ttu-id="37e0d-205">Para obter mais práticas recomendadas, consulte [craft effective images for Microsoft app stores](/office/dev/store/craft-effective-appsource-store-images).</span><span class="sxs-lookup"><span data-stu-id="37e0d-205">For more best practices, see [craft effective images for Microsoft app stores](/office/dev/store/craft-effective-appsource-store-images).</span></span>

## <a name="create-a-video"></a><span data-ttu-id="37e0d-206">Criar um vídeo</span><span class="sxs-lookup"><span data-stu-id="37e0d-206">Create a video</span></span>

<span data-ttu-id="37e0d-207">Um vídeo pode ser a maneira mais eficaz de comunicar por que as pessoas devem usar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="37e0d-207">A video can be the most effective way to communicate why people should use your app.</span></span> <span data-ttu-id="37e0d-208">Você deve resolver as seguintes perguntas em um vídeo:</span><span class="sxs-lookup"><span data-stu-id="37e0d-208">You should address the following questions in a video:</span></span>

* <span data-ttu-id="37e0d-209">Who seu aplicativo é para?</span><span class="sxs-lookup"><span data-stu-id="37e0d-209">Who is your app for?</span></span>
* <span data-ttu-id="37e0d-210">Quais problemas seu aplicativo pode resolver?</span><span class="sxs-lookup"><span data-stu-id="37e0d-210">What problems can your app solve?</span></span>
* <span data-ttu-id="37e0d-211">Como seu aplicativo funciona?</span><span class="sxs-lookup"><span data-stu-id="37e0d-211">How does your app work?</span></span>
* <span data-ttu-id="37e0d-212">Quais outros benefícios você obter com o uso do aplicativo?</span><span class="sxs-lookup"><span data-stu-id="37e0d-212">What other benefits do you get from using your app?</span></span>

<span data-ttu-id="37e0d-213">Se você incluir um vídeo, ele aparecerá antes das capturas de tela na listagem.</span><span class="sxs-lookup"><span data-stu-id="37e0d-213">If you include a video, it appears before your screenshots in the listing.</span></span>

### <a name="best-practices-for-videos"></a><span data-ttu-id="37e0d-214">Práticas recomendadas para vídeos</span><span class="sxs-lookup"><span data-stu-id="37e0d-214">Best practices for videos</span></span>

* <span data-ttu-id="37e0d-215">Mantenha seu vídeo entre 30 e 90 segundos.</span><span class="sxs-lookup"><span data-stu-id="37e0d-215">Keep your video between 30-90 seconds.</span></span>
* <span data-ttu-id="37e0d-216">Aponte para a qualidade.</span><span class="sxs-lookup"><span data-stu-id="37e0d-216">Aim for quality.</span></span> <span data-ttu-id="37e0d-217">Em uma listagem, os usuários verão seu vídeo antes das capturas de tela.</span><span class="sxs-lookup"><span data-stu-id="37e0d-217">In a listing, users will see your video before screenshots.</span></span>

## <a name="localize-your-store-listing"></a><span data-ttu-id="37e0d-218">Localize sua listagem da loja</span><span class="sxs-lookup"><span data-stu-id="37e0d-218">Localize your store listing</span></span>

<span data-ttu-id="37e0d-219">O Partner Center dá [suporte a listagens de armazenamento localizado.](https://docs.microsoft.com/office/dev/store/prepare-localized-solutions)</span><span class="sxs-lookup"><span data-stu-id="37e0d-219">Partner Center supports [localized store listings](https://docs.microsoft.com/office/dev/store/prepare-localized-solutions).</span></span> <span data-ttu-id="37e0d-220">Para obter mais informações, [consulte como localizar sua Teams de aplicativos](../../../../concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="37e0d-220">For more information, see [how to localize your Teams app listing](../../../../concepts/build-and-test/apps-localization.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="37e0d-221">Confira também</span><span class="sxs-lookup"><span data-stu-id="37e0d-221">See also</span></span>

* [<span data-ttu-id="37e0d-222">Criar listagens Microsoft 365 Stores eficazes</span><span class="sxs-lookup"><span data-stu-id="37e0d-222">Create effective Microsoft 365 Stores listings</span></span>](/office/dev/store/create-effective-office-store-listings)
* <span data-ttu-id="37e0d-223">Teams de design de aplicativos para [cópia e conteúdo e](~/concepts/design/design-teams-app-fundamentals.md#copy-and-content) expressão de [marca](~/concepts/design/design-teams-app-fundamentals.md#brand-expression)</span><span class="sxs-lookup"><span data-stu-id="37e0d-223">Teams app design guidelines for [copy and content](~/concepts/design/design-teams-app-fundamentals.md#copy-and-content) and [brand expression](~/concepts/design/design-teams-app-fundamentals.md#brand-expression)</span></span>
* [<span data-ttu-id="37e0d-224">Diretrizes de marca e marca da Microsoft</span><span class="sxs-lookup"><span data-stu-id="37e0d-224">Microsoft Trademark and Brand Guidelines</span></span>](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general)

## <a name="next-step"></a><span data-ttu-id="37e0d-225">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="37e0d-225">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="37e0d-226">Preparar o envio da loja</span><span class="sxs-lookup"><span data-stu-id="37e0d-226">Prepare your store submission</span></span>](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md)
