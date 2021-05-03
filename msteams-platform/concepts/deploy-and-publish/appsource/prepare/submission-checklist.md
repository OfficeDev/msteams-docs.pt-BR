---
title: Preparar o envio para a Microsoft Store
description: Descreve as etapas finais antes de enviar seu Microsoft Teams aplicativo para ser listado na loja.
ms.topic: how-to
localization_priority: Normal
author: heath-hamilton
ms.author: surbhigupta
ms.openlocfilehash: d46d21c3d984b5688c00857e485210b0f0fcf2c7
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101678"
---
# <a name="prepare-your-microsoft-teams-store-submission"></a><span data-ttu-id="7c0a2-103">Preparar seu envio Microsoft Teams de armazenamento de dados</span><span class="sxs-lookup"><span data-stu-id="7c0a2-103">Prepare your Microsoft Teams store submission</span></span>

<span data-ttu-id="7c0a2-104">Você projetou, criou e testou seu Microsoft Teams aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-104">You've designed, built, and tested your Microsoft Teams app.</span></span> <span data-ttu-id="7c0a2-105">Agora você está pronto para listá-lo para que as pessoas possam descobrir e começar a usar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-105">Now you're ready to list it so people can discover and start using your app.</span></span>

<span data-ttu-id="7c0a2-106">Antes de enviar seu aplicativo para [o Partner Center,](/office/dev/store/use-partner-center-to-submit-to-appsource)certifique-se de ter feito o seguinte.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-106">Before you submit your app to [Partner Center](/office/dev/store/use-partner-center-to-submit-to-appsource), make sure you've done the following.</span></span>

## <a name="validate-your-app-package"></a><span data-ttu-id="7c0a2-107">Validar seu pacote de aplicativos</span><span class="sxs-lookup"><span data-stu-id="7c0a2-107">Validate your app package</span></span>

<span data-ttu-id="7c0a2-108">Embora seu aplicativo possa estar funcionando em um ambiente de teste, você deve verificar o pacote do aplicativo para evitar problemas durante o processo de envio.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-108">While your app may be working in a test environment, you should check your app package to avoid running into issues during the submission process.</span></span>

<span data-ttu-id="7c0a2-109">A Microsoft Teams de validação de aplicativo ajuda você a identificar e corrigir problemas antes de enviar ao Partner Center.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-109">The Microsoft Teams app validation tool helps you identify and fix issues before submitting to Partner Center.</span></span> <span data-ttu-id="7c0a2-110">A ferramenta verifica automaticamente as configurações do aplicativo em relação aos mesmos casos de teste usados durante a validação do armazenamento.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-110">The tool automatically checks your app's configurations against the same test cases used during store validation.</span></span>

1. <span data-ttu-id="7c0a2-111">Vá para a ferramenta [Microsoft Teams de validação de aplicativos](https://dev.teams.microsoft.com/appvalidation.html).</span><span class="sxs-lookup"><span data-stu-id="7c0a2-111">Go to the [Microsoft Teams app validation tool](https://dev.teams.microsoft.com/appvalidation.html).</span></span> <span data-ttu-id="7c0a2-112">(Observação: a ferramenta também está disponível no [App Studio](../../../build-and-test/app-studio-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="7c0a2-112">(Note: The tool is also available in [App Studio](../../../build-and-test/app-studio-overview.md).)</span></span>
1. <span data-ttu-id="7c0a2-113">Upload pacote do aplicativo para executar os testes automatizados.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-113">Upload your app package to run the automated tests.</span></span>
1. <span data-ttu-id="7c0a2-114">Vá para **a lista de verificação Preliminar** e revise os casos de teste difíceis de automatizar.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-114">Go to the **Preliminary checklist** and review the test cases that are difficult to automate.</span></span>
1. <span data-ttu-id="7c0a2-115">[Correção de problemas](~/resources/schema/manifest-schema.md) com suas configurações ou aplicativos em geral se os testes automatizados lhe deem erros ou se você não tiver atendido a todos os critérios na lista de verificação.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-115">[Fix issues with your configurations](~/resources/schema/manifest-schema.md) or app in general if the automated tests give you errors or you haven't met all the criteria in the checklist.</span></span>

## <a name="compile-testing-instructions"></a><span data-ttu-id="7c0a2-116">Compilar instruções de teste</span><span class="sxs-lookup"><span data-stu-id="7c0a2-116">Compile testing instructions</span></span>

<span data-ttu-id="7c0a2-117">Forneça instruções e recursos para ajudar os revisadores a testar seu aplicativo, incluindo contas de teste, credenciais e chaves de licença.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-117">Provide instructions and resources to help the reviewers test your app, including test accounts, credentials, and license keys.</span></span> <span data-ttu-id="7c0a2-118">Você pode adicionar instruções no Partner Center ou enviá-las para um local disponível publicamente SharePoint.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-118">You can add instructions in Partner Center or upload them to a publicly available location on SharePoint.</span></span>

### <a name="feature-list"></a><span data-ttu-id="7c0a2-119">Lista de recursos</span><span class="sxs-lookup"><span data-stu-id="7c0a2-119">Feature list</span></span>

<span data-ttu-id="7c0a2-120">Forneça detalhes sobre os recursos do seu aplicativo em Teams e etapas para testar cada um deles.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-120">Provide details about your app's capabilities in Teams and steps for testing each one.</span></span>

### <a name="accounts"></a><span data-ttu-id="7c0a2-121">Contas</span><span class="sxs-lookup"><span data-stu-id="7c0a2-121">Accounts</span></span>

<span data-ttu-id="7c0a2-122">Você deve fornecer contas de teste se seu aplicativo exigir uma licença ou uma lista segura de back-end.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-122">You must provide test accounts if your app requires a license or backend safelisting.</span></span> <span data-ttu-id="7c0a2-123">Todas as contas fornecidas devem incluir dados pré-preenchidos para facilitar o teste.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-123">All accounts you provide must include pre-populated data to facilitate testing.</span></span>

<span data-ttu-id="7c0a2-124">Dependendo dos recursos do seu aplicativo, talvez seja necessário fornecer todos os seguintes:</span><span class="sxs-lookup"><span data-stu-id="7c0a2-124">Depending on your app's features, you may need to provide all of the following:</span></span>

* <span data-ttu-id="7c0a2-125">Conta de administrador (necessária)</span><span class="sxs-lookup"><span data-stu-id="7c0a2-125">Admin account (required)</span></span>
* <span data-ttu-id="7c0a2-126">Conta não administrativa (necessária)</span><span class="sxs-lookup"><span data-stu-id="7c0a2-126">Non-admin account (required)</span></span>
* <span data-ttu-id="7c0a2-127">Uma conta que não está pré-configurada para testar corretamente a experiência de login da primeira vez (necessária)</span><span class="sxs-lookup"><span data-stu-id="7c0a2-127">An account that isn't pre-configured in order to properly test the first-run sign-in experience (required)</span></span>
* <span data-ttu-id="7c0a2-128">Uma conta com acesso a recursos premium ou atualizados (se aplicável)</span><span class="sxs-lookup"><span data-stu-id="7c0a2-128">An account with access to premium or upgraded features (if applicable)</span></span>
* <span data-ttu-id="7c0a2-129">Duas contas no mesmo locatário para testar a experiência de colaboração para aplicativos que funcionam em contextos compartilhados (se aplicável)</span><span class="sxs-lookup"><span data-stu-id="7c0a2-129">Two accounts in the same tenant to test the collaboration experience for apps that work in shared contexts (if applicable)</span></span>

### <a name="tenant-configurations"></a><span data-ttu-id="7c0a2-130">Configurações de locatário</span><span class="sxs-lookup"><span data-stu-id="7c0a2-130">Tenant configurations</span></span>

<span data-ttu-id="7c0a2-131">Se você deve configurar um locatário Teams usar seu aplicativo, inclua essas instruções e contas de administrador e não administrador para validação.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-131">If you must configure a Teams tenant to use your app, include those instructions and admin and non-admin accounts for validation.</span></span>

### <a name="video-optional"></a><span data-ttu-id="7c0a2-132">Vídeo (opcional)</span><span class="sxs-lookup"><span data-stu-id="7c0a2-132">Video (optional)</span></span>

<span data-ttu-id="7c0a2-133">Forneça uma gravação do seu aplicativo para que a Microsoft possa entender totalmente sua funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-133">Provide a recording of your app so that Microsoft can fully understand its functionality.</span></span>

## <a name="create-your-store-listing-details"></a><span data-ttu-id="7c0a2-134">Criar detalhes de listagem da loja</span><span class="sxs-lookup"><span data-stu-id="7c0a2-134">Create your store listing details</span></span>

<span data-ttu-id="7c0a2-135">As informações que você envia ao [Partner Center](https://partner.microsoft.com)&#8212;incluindo seu nome, descrições, ícones e imagens&#8212;se tornam a Teams store e a listagem do Microsoft AppSource para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-135">The information that you submit to [Partner Center](https://partner.microsoft.com)&#8212;including your name, descriptions, icons, and images&#8212;becomes the Teams store and Microsoft AppSource listing for your app.</span></span>

<span data-ttu-id="7c0a2-136">Uma listagem da loja pode ser a primeira impressão de alguém do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-136">A store listing may be someone's first impression of your app.</span></span> <span data-ttu-id="7c0a2-137">Aumente as instalações com uma listagem que transmite efetivamente os benefícios, a funcionalidade e a marca do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-137">Increase installations with a listing that effectively conveys your app's benefits, functionality, and brand.</span></span>

### <a name="specify-a-short-name"></a><span data-ttu-id="7c0a2-138">Especificar um nome curto</span><span class="sxs-lookup"><span data-stu-id="7c0a2-138">Specify a short name</span></span>

<span data-ttu-id="7c0a2-139">O nome do seu aplicativo (especificamente, seu [*nome*](~/resources/schema/manifest-schema.md#name)curto ) desempenha uma função crucial na forma como os usuários o descobrem na loja.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-139">Your app's name (specifically, its [*short name*](~/resources/schema/manifest-schema.md#name)) plays a crucial role in how users discover it in the store.</span></span>

:::row:::

   :::column span="3":::
      :::image type="content" source="../../../../assets/images/store-detail-page/AppName-02.png" alt-text="Exemplo de captura de tela realça onde o nome curto de um aplicativo é exibido em uma listagem da loja.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

<span data-ttu-id="7c0a2-141">Certifique-se de que seu nome curto adera às diretrizes [de validação da loja.](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#11-app-name)</span><span class="sxs-lookup"><span data-stu-id="7c0a2-141">Make sure your short name adheres to the [store validation guidelines](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#11-app-name).</span></span>

### <a name="write-descriptions"></a><span data-ttu-id="7c0a2-142">Descrições de gravação</span><span class="sxs-lookup"><span data-stu-id="7c0a2-142">Write descriptions</span></span>

<span data-ttu-id="7c0a2-143">Você deve ter uma descrição curta e longa do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-143">You must have a short and long description of your app.</span></span>

#### <a name="short-description"></a><span data-ttu-id="7c0a2-144">Descrição breve</span><span class="sxs-lookup"><span data-stu-id="7c0a2-144">Short description</span></span>

<span data-ttu-id="7c0a2-145">Um resumo conciso do seu aplicativo que deve ser original, envolvente e direcionado para seu público-alvo.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-145">A concise summary of your app that should be original, engaging, and directed at your target audience.</span></span> <span data-ttu-id="7c0a2-146">Mantenha a descrição curta em uma frase.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-146">Keep the short description to one sentence.</span></span>

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/ShortDescription-02.png" alt-text="Exemplo de captura de tela realça onde a descrição curta de um aplicativo é exibida em uma listagem da loja.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

<span data-ttu-id="7c0a2-148">Certifique-se de que sua breve descrição segue as diretrizes [de validação da loja.](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#431-short-description)</span><span class="sxs-lookup"><span data-stu-id="7c0a2-148">Make sure your short description adheres to the [store validation guidelines](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#431-short-description).</span></span>

#### <a name="long-description"></a><span data-ttu-id="7c0a2-149">Descrição longa</span><span class="sxs-lookup"><span data-stu-id="7c0a2-149">Long description</span></span>

<span data-ttu-id="7c0a2-150">A descrição longa pode fornecer uma narração que realça os principais recursos do aplicativo, os problemas que ele resolve e seu público-alvo.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-150">The long description can provide a narrative that highlights your app's main features, the problems it solves, and its target audience.</span></span> <span data-ttu-id="7c0a2-151">Embora essa descrição possa ter até 4.000 caracteres, a maioria dos usuários lerá apenas entre 300 e 500 palavras.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-151">While this description can be as long as 4,000 characters, most users will only read between 300-500 words.</span></span>

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/LongDescription-02.png" alt-text="Exemplo de captura de tela realça onde a descrição longa de um aplicativo é exibida em uma listagem da loja.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

<span data-ttu-id="7c0a2-153">Certifique-se de que sua descrição longa segue as diretrizes de validação [da loja.](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#432-long-description)</span><span class="sxs-lookup"><span data-stu-id="7c0a2-153">Make sure your long description adheres to the [store validation guidelines](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#432-long-description).</span></span>

### <a name="adhere-to-icon-design-guidelines"></a><span data-ttu-id="7c0a2-154">Seguir as diretrizes de design de ícones</span><span class="sxs-lookup"><span data-stu-id="7c0a2-154">Adhere to icon design guidelines</span></span>

<span data-ttu-id="7c0a2-155">Os ícones são um dos principais elementos que os usuários veem ao navegar na loja.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-155">Icons are one of the main elements users see when browsing the store.</span></span> <span data-ttu-id="7c0a2-156">Seus ícones devem comunicar a marca e a finalidade do seu aplicativo enquanto também aderem aos requisitos Teams.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-156">Your icons should communicate your app's brand and purpose while also adhering to Teams requirements.</span></span>

<span data-ttu-id="7c0a2-157">Para obter mais informações, consulte [diretrizes sobre como criar Teams ícones de aplicativo.](~/concepts/build-and-test/apps-package.md#app-icons)</span><span class="sxs-lookup"><span data-stu-id="7c0a2-157">For more information, see [guidance on creating Teams app icons](~/concepts/build-and-test/apps-package.md#app-icons).</span></span>

### <a name="capture-screenshots"></a><span data-ttu-id="7c0a2-158">Capturar capturas de tela</span><span class="sxs-lookup"><span data-stu-id="7c0a2-158">Capture screenshots</span></span>

<span data-ttu-id="7c0a2-159">As capturas de tela fornecem uma visualização visual proeminente do seu aplicativo para complementar o nome, o ícone e as descrições do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-159">Screenshots provide a prominent visual preview of your app to complement your app name, icon, and descriptions.</span></span>

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/Screenshot-01.png" alt-text="Exemplo de realçamentos de captura de tela onde as capturas de tela do aplicativo são exibidas em uma listagem da loja.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

<span data-ttu-id="7c0a2-161">Lembre-se do seguinte sobre capturas de tela:</span><span class="sxs-lookup"><span data-stu-id="7c0a2-161">Remember the following about screenshots:</span></span>

* <span data-ttu-id="7c0a2-162">Você pode ter até cinco capturas de tela por listagem.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-162">You can have up to five screenshots per listing.</span></span>
* <span data-ttu-id="7c0a2-163">Os tipos de arquivo com suporte incluem PNG, JPEG e GIF.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-163">Supported file types include PNG, JPEG, and GIF.</span></span>
* <span data-ttu-id="7c0a2-164">As dimensões devem ter 1366 x 768 pixels.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-164">Dimensions should be 1366x768 pixels.</span></span>
* <span data-ttu-id="7c0a2-165">Tamanho máximo de 1.024 KB.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-165">Maximum size of 1,024 KB.</span></span>

<span data-ttu-id="7c0a2-166">Para ver as práticas recomendadas, consulte os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="7c0a2-166">For best practices, see the following resources:</span></span>

* [<span data-ttu-id="7c0a2-167">Teams de validação do armazenamento</span><span class="sxs-lookup"><span data-stu-id="7c0a2-167">Teams store validation guidelines</span></span>](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#44-screenshots)
* [<span data-ttu-id="7c0a2-168">Criar imagens efetivas para os armazenamentos de aplicativos da Microsoft</span><span class="sxs-lookup"><span data-stu-id="7c0a2-168">Craft effective images for Microsoft app stores</span></span>](/office/dev/store/craft-effective-appsource-store-images)

### <a name="create-a-video"></a><span data-ttu-id="7c0a2-169">Criar um vídeo</span><span class="sxs-lookup"><span data-stu-id="7c0a2-169">Create a video</span></span>

<span data-ttu-id="7c0a2-170">Um vídeo em sua listagem pode ser a maneira mais eficaz de comunicar por que as pessoas devem usar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-170">A video in your listing can be the most effective way to communicate why people should use your app.</span></span> <span data-ttu-id="7c0a2-171">Você deve resolver as seguintes perguntas em um vídeo:</span><span class="sxs-lookup"><span data-stu-id="7c0a2-171">You should address the following questions in a video:</span></span>

* <span data-ttu-id="7c0a2-172">Who seu aplicativo é para?</span><span class="sxs-lookup"><span data-stu-id="7c0a2-172">Who is your app for?</span></span>
* <span data-ttu-id="7c0a2-173">Quais problemas seu aplicativo pode resolver?</span><span class="sxs-lookup"><span data-stu-id="7c0a2-173">What problems can your app solve?</span></span>
* <span data-ttu-id="7c0a2-174">Como seu aplicativo funciona?</span><span class="sxs-lookup"><span data-stu-id="7c0a2-174">How does your app work?</span></span>
* <span data-ttu-id="7c0a2-175">Quais outros benefícios você obter com o uso do aplicativo?</span><span class="sxs-lookup"><span data-stu-id="7c0a2-175">What other benefits do you get from using your app?</span></span>

#### <a name="best-practices-for-videos"></a><span data-ttu-id="7c0a2-176">Práticas recomendadas para vídeos</span><span class="sxs-lookup"><span data-stu-id="7c0a2-176">Best practices for videos</span></span>

* <span data-ttu-id="7c0a2-177">Mantenha seu vídeo entre 30 e 90 segundos.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-177">Keep your video between 30-90 seconds.</span></span>
* <span data-ttu-id="7c0a2-178">Aponte para a qualidade.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-178">Aim for quality.</span></span> <span data-ttu-id="7c0a2-179">Em uma listagem, os usuários verão seu vídeo antes das capturas de tela.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-179">In a listing, users will see your video before screenshots.</span></span>

### <a name="select-a-category-for-your-app"></a><span data-ttu-id="7c0a2-180">Selecione uma categoria para seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="7c0a2-180">Select a category for your app</span></span>

<span data-ttu-id="7c0a2-181">Durante o envio, você é solicitado a categorizar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-181">During submission, you're asked to categorize your app.</span></span> <span data-ttu-id="7c0a2-182">A tabela a seguir mapeia Teams categorias de armazenamento para as categorias listadas no [Partner Center](https://aka.ms/PartnerCenterHomePage).</span><span class="sxs-lookup"><span data-stu-id="7c0a2-182">The following table maps Teams store categories to the categories listed in [Partner Center](https://aka.ms/PartnerCenterHomePage).</span></span>

| <span data-ttu-id="7c0a2-183">Teams categorias</span><span class="sxs-lookup"><span data-stu-id="7c0a2-183">Teams categories</span></span>       | <span data-ttu-id="7c0a2-184">Categorias do Partner Center</span><span class="sxs-lookup"><span data-stu-id="7c0a2-184">Partner Center categories</span></span>  |
|:---------------------|:---------------|
| <span data-ttu-id="7c0a2-185">Análise e BI</span><span class="sxs-lookup"><span data-stu-id="7c0a2-185">Analytics and BI</span></span> | <span data-ttu-id="7c0a2-186">Análise, Visualização de Dados e BI</span><span class="sxs-lookup"><span data-stu-id="7c0a2-186">Analytics, Data Visualization and BI</span></span> |
| <span data-ttu-id="7c0a2-187">Desenvolvedor e IT</span><span class="sxs-lookup"><span data-stu-id="7c0a2-187">Developer and IT</span></span> | <span data-ttu-id="7c0a2-188">Ferramentas de Desenvolvedor, Administrador de IT</span><span class="sxs-lookup"><span data-stu-id="7c0a2-188">Developer Tools, IT Admin</span></span> |
| <span data-ttu-id="7c0a2-189">Educação</span><span class="sxs-lookup"><span data-stu-id="7c0a2-189">Education</span></span> | <span data-ttu-id="7c0a2-190">Educação</span><span class="sxs-lookup"><span data-stu-id="7c0a2-190">Education</span></span> |
| <span data-ttu-id="7c0a2-191">Recursos humanos</span><span class="sxs-lookup"><span data-stu-id="7c0a2-191">Human resources</span></span> | <span data-ttu-id="7c0a2-192">Recursos Humanos e Recrutamento</span><span class="sxs-lookup"><span data-stu-id="7c0a2-192">Human Resources and Recruiting</span></span> |
| <span data-ttu-id="7c0a2-193">Produtividade</span><span class="sxs-lookup"><span data-stu-id="7c0a2-193">Productivity</span></span> | <span data-ttu-id="7c0a2-194">Gerenciamento de Conteúdo, Arquivos e documentos, Produtividade, Treinamento e Tutoriais e Utilitários</span><span class="sxs-lookup"><span data-stu-id="7c0a2-194">Content Management, Files and documents, Productivity, Training and Tutorials, and Utilities</span></span> |
| <span data-ttu-id="7c0a2-195">Gerenciamento de projeto</span><span class="sxs-lookup"><span data-stu-id="7c0a2-195">Project management</span></span> | <span data-ttu-id="7c0a2-196">Comunicação, Project Gerenciamento, Fluxo de Trabalho e Gerenciamento de Negócios</span><span class="sxs-lookup"><span data-stu-id="7c0a2-196">Communication, Project Management, Workflow, and Business Management</span></span> |
| <span data-ttu-id="7c0a2-197">Vendas e suporte</span><span class="sxs-lookup"><span data-stu-id="7c0a2-197">Sales and support</span></span> | <span data-ttu-id="7c0a2-198">Gerenciamento de Clientes e Contatos, Suporte ao Cliente, Gerenciamento Financeiro, Vendas e Marketing</span><span class="sxs-lookup"><span data-stu-id="7c0a2-198">Customer and Contact Management, Customer Support, Financial Management, Sales and Marketing</span></span> |
| <span data-ttu-id="7c0a2-199">Social e divertido</span><span class="sxs-lookup"><span data-stu-id="7c0a2-199">Social and fun</span></span> | <span data-ttu-id="7c0a2-200">Galerias de imagem e vídeo, estilo de vida, notícias e clima, social, viagem e navegação</span><span class="sxs-lookup"><span data-stu-id="7c0a2-200">Image and Video Galleries, Lifestyle, News and Weather, Social, Travel, and Navigation</span></span> |

### <a name="localize-your-store-listing"></a><span data-ttu-id="7c0a2-201">Localize sua listagem da loja</span><span class="sxs-lookup"><span data-stu-id="7c0a2-201">Localize your store listing</span></span>

<span data-ttu-id="7c0a2-202">O Partner Center dá [suporte a listagens de armazenamento localizado.](https://docs.microsoft.com/office/dev/store/prepare-localized-solutions)</span><span class="sxs-lookup"><span data-stu-id="7c0a2-202">Partner Center supports [localized store listings](https://docs.microsoft.com/office/dev/store/prepare-localized-solutions).</span></span> <span data-ttu-id="7c0a2-203">Para obter mais informações, [consulte como localizar sua Teams de aplicativos](../../../../concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="7c0a2-203">For more information, see [how to localize your Teams app listing](../../../../concepts/build-and-test/apps-localization.md).</span></span>

## <a name="complete-publisher-verification"></a><span data-ttu-id="7c0a2-204">Concluir Publisher Verificação</span><span class="sxs-lookup"><span data-stu-id="7c0a2-204">Complete Publisher Verification</span></span>

<span data-ttu-id="7c0a2-205">[Publisher Verificação](/azure/active-directory/develop/publisher-verification-overview) é necessária para Teams aplicativos listados na loja. Para obter mais informações, [consulte perguntas frequentes](/azure/active-directory/develop/publisher-verification-overview#frequently-asked-questions), como marcar seu aplicativo como [editor verificado](/azure/active-directory/develop/mark-app-as-publisher-verified)e solucionar problemas de verificação [do editor.](/azure/active-directory/develop/troubleshoot-publisher-verification)</span><span class="sxs-lookup"><span data-stu-id="7c0a2-205">[Publisher Verification](/azure/active-directory/develop/publisher-verification-overview) is required for Teams apps listed in the store.For more information, see [frequently asked questions](/azure/active-directory/develop/publisher-verification-overview#frequently-asked-questions), [how to mark your app as publisher verified](/azure/active-directory/develop/mark-app-as-publisher-verified), and [troubleshoot publisher verification](/azure/active-directory/develop/troubleshoot-publisher-verification).</span></span>

## <a name="complete-publisher-attestation"></a><span data-ttu-id="7c0a2-206">Concluir Publisher Atestado</span><span class="sxs-lookup"><span data-stu-id="7c0a2-206">Complete Publisher Attestation</span></span>

<span data-ttu-id="7c0a2-207">[Publisher Atestado](/microsoft-365-app-certification/docs/attestation) também é necessário para Teams aplicativos listados na loja.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-207">[Publisher Attestation](/microsoft-365-app-certification/docs/attestation) is also required for Teams apps listed in the store.</span></span> <span data-ttu-id="7c0a2-208">O processo inclui a conclusão de uma autoavaliação das práticas de segurança, tratamento de dados e conformidade do seu aplicativo que podem ajudar os clientes em potencial a tomar decisões informadas sobre o uso do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-208">The process includes completing a self-assessment of your app's security, data handling, and compliance practices that can help potential customers make informed decisions about using your app.</span></span>

> [!NOTE]
> <span data-ttu-id="7c0a2-209">Se você estiver enviando um novo aplicativo, não poderá concluir oficialmente Publisher Atestado até que seu aplicativo seja listado na Teams store.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-209">If you're submitting a new app, you can't officially complete Publisher Attestation until your app is listed on the Teams store.</span></span> <span data-ttu-id="7c0a2-210">Se você estiver atualizando um aplicativo listado, conclua Publisher Atestado antes de enviar a versão mais recente do aplicativo para validação.</span><span class="sxs-lookup"><span data-stu-id="7c0a2-210">If you're updating a listed app, complete Publisher Attestation before you submit the latest version of the app for validation.</span></span>

## <a name="next-step"></a><span data-ttu-id="7c0a2-211">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="7c0a2-211">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7c0a2-212">Enviar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="7c0a2-212">Submit your app</span></span>](https://docs.microsoft.com/office/dev/store/add-in-submission-guide)
