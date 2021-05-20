---
title: Preparar o envio para a Microsoft Store
description: Descreve os passos finais antes de enviar seu aplicativo Microsoft Teams a ser listado na loja.
ms.topic: how-to
localization_priority: Normal
author: heath-hamilton
ms.author: surbhigupta
ms.openlocfilehash: 975d3ef8fc8bdc8d6d7c336cf3a61a3a42ef5315
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566030"
---
# <a name="prepare-your-microsoft-teams-store-submission"></a><span data-ttu-id="ff427-103">Prepare sua submissão de loja de Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="ff427-103">Prepare your Microsoft Teams store submission</span></span>

<span data-ttu-id="ff427-104">Você projetou, construiu e testou seu aplicativo de Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="ff427-104">You've designed, built, and tested your Microsoft Teams app.</span></span> <span data-ttu-id="ff427-105">Agora você está pronto para listá-lo para que as pessoas possam descobrir e começar a usar o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff427-105">Now you're ready to list it so people can discover and start using your app.</span></span>

<span data-ttu-id="ff427-106">Antes de enviar seu aplicativo para o [Partner Center,](/office/dev/store/use-partner-center-to-submit-to-appsource)certifique-se de ter feito o seguinte.</span><span class="sxs-lookup"><span data-stu-id="ff427-106">Before you submit your app to [Partner Center](/office/dev/store/use-partner-center-to-submit-to-appsource), make sure you've done the following.</span></span>

## <a name="validate-your-app-package"></a><span data-ttu-id="ff427-107">Valide seu pacote de aplicativos</span><span class="sxs-lookup"><span data-stu-id="ff427-107">Validate your app package</span></span>

<span data-ttu-id="ff427-108">Embora seu aplicativo possa estar funcionando em um ambiente de teste, você deve verificar seu pacote de aplicativos para evitar problemas durante o processo de envio.</span><span class="sxs-lookup"><span data-stu-id="ff427-108">While your app may be working in a test environment, you should check your app package to avoid running into issues during the submission process.</span></span>

<span data-ttu-id="ff427-109">A ferramenta de validação de aplicativos Microsoft Teams ajuda a identificar e corrigir problemas antes de se submeter à Central de Parceiros.</span><span class="sxs-lookup"><span data-stu-id="ff427-109">The Microsoft Teams app validation tool helps you identify and fix issues before submitting to Partner Center.</span></span> <span data-ttu-id="ff427-110">A ferramenta verifica automaticamente as configurações do seu aplicativo em relação aos mesmos casos de teste usados durante a validação da loja.</span><span class="sxs-lookup"><span data-stu-id="ff427-110">The tool automatically checks your app's configurations against the same test cases used during store validation.</span></span>

1. <span data-ttu-id="ff427-111">Acesse a [ferramenta de validação de aplicativos Microsoft Teams](https://dev.teams.microsoft.com/appvalidation.html).</span><span class="sxs-lookup"><span data-stu-id="ff427-111">Go to the [Microsoft Teams app validation tool](https://dev.teams.microsoft.com/appvalidation.html).</span></span> <span data-ttu-id="ff427-112">(Nota: A ferramenta também está disponível no [App Studio](../../../build-and-test/app-studio-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="ff427-112">(Note: The tool is also available in [App Studio](../../../build-and-test/app-studio-overview.md).)</span></span>
1. <span data-ttu-id="ff427-113">Upload seu pacote de aplicativos para executar os testes automatizados.</span><span class="sxs-lookup"><span data-stu-id="ff427-113">Upload your app package to run the automated tests.</span></span>
1. <span data-ttu-id="ff427-114">Vá para a **lista preliminar** e revise os casos de teste difíceis de automatizar.</span><span class="sxs-lookup"><span data-stu-id="ff427-114">Go to the **Preliminary checklist** and review the test cases that are difficult to automate.</span></span>
1. <span data-ttu-id="ff427-115">[Corrija problemas com suas configurações](~/resources/schema/manifest-schema.md) ou aplicativo em geral se os testes automatizados lhe derem erros ou você não tiver atendido todos os critérios na lista de verificação.</span><span class="sxs-lookup"><span data-stu-id="ff427-115">[Fix issues with your configurations](~/resources/schema/manifest-schema.md) or app in general if the automated tests give you errors or you haven't met all the criteria in the checklist.</span></span>

## <a name="compile-testing-instructions"></a><span data-ttu-id="ff427-116">Compilar instruções de teste</span><span class="sxs-lookup"><span data-stu-id="ff427-116">Compile testing instructions</span></span>

<span data-ttu-id="ff427-117">Forneça instruções e recursos para ajudar os revisores a testar seu aplicativo, incluindo contas de teste, credenciais e chaves de licença.</span><span class="sxs-lookup"><span data-stu-id="ff427-117">Provide instructions and resources to help the reviewers test your app, including test accounts, credentials, and license keys.</span></span> <span data-ttu-id="ff427-118">Você pode adicionar instruções no Partner Center ou enviá-las para um local disponível publicamente em SharePoint.</span><span class="sxs-lookup"><span data-stu-id="ff427-118">You can add instructions in Partner Center or upload them to a publicly available location on SharePoint.</span></span>

### <a name="feature-list"></a><span data-ttu-id="ff427-119">Lista de recursos</span><span class="sxs-lookup"><span data-stu-id="ff427-119">Feature list</span></span>

<span data-ttu-id="ff427-120">Forneça detalhes sobre os recursos do seu aplicativo em Teams e passos para testar cada um.</span><span class="sxs-lookup"><span data-stu-id="ff427-120">Provide details about your app's capabilities in Teams and steps for testing each one.</span></span>

### <a name="accounts"></a><span data-ttu-id="ff427-121">Contas</span><span class="sxs-lookup"><span data-stu-id="ff427-121">Accounts</span></span>

<span data-ttu-id="ff427-122">Você deve fornecer contas de teste se o seu aplicativo exigir uma licença ou fazer backup da lista de segurança.</span><span class="sxs-lookup"><span data-stu-id="ff427-122">You must provide test accounts if your app requires a license or backend safelisting.</span></span> <span data-ttu-id="ff427-123">Todas as contas que você fornece devem incluir dados pré-preenchidos para facilitar o teste.</span><span class="sxs-lookup"><span data-stu-id="ff427-123">All accounts you provide must include pre-populated data to facilitate testing.</span></span>

<span data-ttu-id="ff427-124">Dependendo dos recursos do seu aplicativo, você pode precisar fornecer todos os seguintes:</span><span class="sxs-lookup"><span data-stu-id="ff427-124">Depending on your app's features, you may need to provide all of the following:</span></span>

* <span data-ttu-id="ff427-125">Conta de administração (necessária)</span><span class="sxs-lookup"><span data-stu-id="ff427-125">Admin account (required)</span></span>
* <span data-ttu-id="ff427-126">Conta de administração não (necessária)</span><span class="sxs-lookup"><span data-stu-id="ff427-126">Non-admin account (required)</span></span>
* <span data-ttu-id="ff427-127">Uma conta que não está pré-configurada para testar adequadamente a experiência de login de primeira execução (necessária)</span><span class="sxs-lookup"><span data-stu-id="ff427-127">An account that isn't pre-configured in order to properly test the first-run sign-in experience (required)</span></span>
* <span data-ttu-id="ff427-128">Uma conta com acesso a recursos premium ou atualizados (se aplicável)</span><span class="sxs-lookup"><span data-stu-id="ff427-128">An account with access to premium or upgraded features (if applicable)</span></span>
* <span data-ttu-id="ff427-129">Duas contas no mesmo inquilino para testar a experiência de colaboração de aplicativos que funcionam em contextos compartilhados (se aplicável)</span><span class="sxs-lookup"><span data-stu-id="ff427-129">Two accounts in the same tenant to test the collaboration experience for apps that work in shared contexts (if applicable)</span></span>

### <a name="tenant-configurations"></a><span data-ttu-id="ff427-130">Configurações de inquilinos</span><span class="sxs-lookup"><span data-stu-id="ff427-130">Tenant configurations</span></span>

<span data-ttu-id="ff427-131">Se você deve configurar um inquilino Teams para usar seu aplicativo, inclua essas instruções e contas de administração e não administradores para validação.</span><span class="sxs-lookup"><span data-stu-id="ff427-131">If you must configure a Teams tenant to use your app, include those instructions and admin and non-admin accounts for validation.</span></span>

### <a name="video-optional"></a><span data-ttu-id="ff427-132">Vídeo (opcional)</span><span class="sxs-lookup"><span data-stu-id="ff427-132">Video (optional)</span></span>

<span data-ttu-id="ff427-133">Forneça uma gravação do seu aplicativo para que a Microsoft possa entender completamente sua funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="ff427-133">Provide a recording of your app so that Microsoft can fully understand its functionality.</span></span>

## <a name="create-your-store-listing-details"></a><span data-ttu-id="ff427-134">Crie detalhes de listagem de sua loja</span><span class="sxs-lookup"><span data-stu-id="ff427-134">Create your store listing details</span></span>

<span data-ttu-id="ff427-135">As informações que você envia para o [Partner Center](https://partner.microsoft.com)&#8212;incluindo seu nome, descrições, ícones e imagens&#8212;se torna a Teams loja e a listagem do Microsoft AppSource para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff427-135">The information that you submit to [Partner Center](https://partner.microsoft.com)&#8212;including your name, descriptions, icons, and images&#8212;becomes the Teams store and Microsoft AppSource listing for your app.</span></span>

<span data-ttu-id="ff427-136">Uma lista de lojas pode ser a primeira impressão de alguém do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff427-136">A store listing may be someone's first impression of your app.</span></span> <span data-ttu-id="ff427-137">Aumente as instalações com uma listagem que transmite efetivamente os benefícios, funcionalidades e marca do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff427-137">Increase installations with a listing that effectively conveys your app's benefits, functionality, and brand.</span></span>

### <a name="specify-a-short-name"></a><span data-ttu-id="ff427-138">Especifique um nome curto</span><span class="sxs-lookup"><span data-stu-id="ff427-138">Specify a short name</span></span>

<span data-ttu-id="ff427-139">O nome do seu aplicativo (especificamente, seu [*nome curto*](~/resources/schema/manifest-schema.md#name)) desempenha um papel crucial na forma como os usuários o descobrem na loja.</span><span class="sxs-lookup"><span data-stu-id="ff427-139">Your app's name (specifically, its [*short name*](~/resources/schema/manifest-schema.md#name)) plays a crucial role in how users discover it in the store.</span></span>

:::row:::

   :::column span="3":::
      :::image type="content" source="../../../../assets/images/store-detail-page/AppName-02.png" alt-text="Exemplos de captura de tela destacam onde o nome curto de um aplicativo é exibido em uma listagem de loja.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

<span data-ttu-id="ff427-141">Certifique-se de que seu nome curto adere às [diretrizes de validação](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#11-app-name)da loja .</span><span class="sxs-lookup"><span data-stu-id="ff427-141">Make sure your short name adheres to the [store validation guidelines](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#11-app-name).</span></span>

### <a name="write-descriptions"></a><span data-ttu-id="ff427-142">Escrever descrições</span><span class="sxs-lookup"><span data-stu-id="ff427-142">Write descriptions</span></span>

<span data-ttu-id="ff427-143">Você deve ter uma descrição curta e longa do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff427-143">You must have a short and long description of your app.</span></span>

#### <a name="short-description"></a><span data-ttu-id="ff427-144">Descrição breve</span><span class="sxs-lookup"><span data-stu-id="ff427-144">Short description</span></span>

<span data-ttu-id="ff427-145">Um resumo conciso do seu aplicativo que deve ser original, envolvente e direcionado ao seu público-alvo.</span><span class="sxs-lookup"><span data-stu-id="ff427-145">A concise summary of your app that should be original, engaging, and directed at your target audience.</span></span> <span data-ttu-id="ff427-146">Mantenha a descrição curta para uma frase.</span><span class="sxs-lookup"><span data-stu-id="ff427-146">Keep the short description to one sentence.</span></span>

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/ShortDescription-02.png" alt-text="Exemplos de captura de tela destacam onde a descrição curta de um aplicativo é exibida em uma listagem de loja.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

<span data-ttu-id="ff427-148">Certifique-se de que sua descrição curta adere às [diretrizes de validação](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#431-short-description)da loja .</span><span class="sxs-lookup"><span data-stu-id="ff427-148">Make sure your short description adheres to the [store validation guidelines](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#431-short-description).</span></span>

#### <a name="long-description"></a><span data-ttu-id="ff427-149">Descrição longa</span><span class="sxs-lookup"><span data-stu-id="ff427-149">Long description</span></span>

<span data-ttu-id="ff427-150">A longa descrição pode fornecer uma narrativa que destaca as principais características do seu aplicativo, os problemas que ele resolve e seu público-alvo.</span><span class="sxs-lookup"><span data-stu-id="ff427-150">The long description can provide a narrative that highlights your app's main features, the problems it solves, and its target audience.</span></span> <span data-ttu-id="ff427-151">Embora esta descrição possa ser de até 4.000 caracteres, a maioria dos usuários só lerá entre 300-500 palavras.</span><span class="sxs-lookup"><span data-stu-id="ff427-151">While this description can be as long as 4,000 characters, most users will only read between 300-500 words.</span></span>

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/LongDescription-02.png" alt-text="Exemplos de captura de tela destacam onde a longa descrição de um aplicativo é exibida em uma listagem de loja.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

<span data-ttu-id="ff427-153">Certifique-se de que sua longa descrição adere às [diretrizes de validação](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#432-long-description)da loja .</span><span class="sxs-lookup"><span data-stu-id="ff427-153">Make sure your long description adheres to the [store validation guidelines](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#432-long-description).</span></span>

### <a name="adhere-to-icon-design-guidelines"></a><span data-ttu-id="ff427-154">Adere às diretrizes de design de ícones</span><span class="sxs-lookup"><span data-stu-id="ff427-154">Adhere to icon design guidelines</span></span>

<span data-ttu-id="ff427-155">Ícones são um dos principais elementos que os usuários vêem ao navegar na loja.</span><span class="sxs-lookup"><span data-stu-id="ff427-155">Icons are one of the main elements users see when browsing the store.</span></span> <span data-ttu-id="ff427-156">Seus ícones devem comunicar a marca e o propósito do seu aplicativo, ao mesmo tempo em que adsuem aos requisitos Teams.</span><span class="sxs-lookup"><span data-stu-id="ff427-156">Your icons should communicate your app's brand and purpose while also adhering to Teams requirements.</span></span>

<span data-ttu-id="ff427-157">Para obter mais informações, consulte [orientações sobre a criação de ícones de aplicativos Teams](~/concepts/build-and-test/apps-package.md#app-icons).</span><span class="sxs-lookup"><span data-stu-id="ff427-157">For more information, see [guidance on creating Teams app icons](~/concepts/build-and-test/apps-package.md#app-icons).</span></span>

### <a name="capture-screenshots"></a><span data-ttu-id="ff427-158">Capturar capturas de tela</span><span class="sxs-lookup"><span data-stu-id="ff427-158">Capture screenshots</span></span>

<span data-ttu-id="ff427-159">As capturas de tela fornecem uma visualização visual proeminente do seu aplicativo para complementar o nome do aplicativo, o ícone e as descrições.</span><span class="sxs-lookup"><span data-stu-id="ff427-159">Screenshots provide a prominent visual preview of your app to complement your app name, icon, and descriptions.</span></span>

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/Screenshot-01.png" alt-text="Exemplos de captura de tela destacam onde capturas de tela de aplicativos são exibidas em uma listagem de loja.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

<span data-ttu-id="ff427-161">Lembre-se dos seguintes capturas de tela:</span><span class="sxs-lookup"><span data-stu-id="ff427-161">Remember the following about screenshots:</span></span>

* <span data-ttu-id="ff427-162">Você pode ter até cinco capturas de tela por listagem.</span><span class="sxs-lookup"><span data-stu-id="ff427-162">You can have up to five screenshots per listing.</span></span>
* <span data-ttu-id="ff427-163">Os tipos de arquivos suportados incluem PNG, JPEG e GIF.</span><span class="sxs-lookup"><span data-stu-id="ff427-163">Supported file types include PNG, JPEG, and GIF.</span></span>
* <span data-ttu-id="ff427-164">As dimensões devem ser de 1366x768 pixels.</span><span class="sxs-lookup"><span data-stu-id="ff427-164">Dimensions should be 1366x768 pixels.</span></span>
* <span data-ttu-id="ff427-165">Tamanho máximo de 1.024 KB.</span><span class="sxs-lookup"><span data-stu-id="ff427-165">Maximum size of 1,024 KB.</span></span>

<span data-ttu-id="ff427-166">Para obter as melhores práticas, consulte os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="ff427-166">For best practices, see the following resources:</span></span>

* [<span data-ttu-id="ff427-167">Teams diretrizes de validação de lojas</span><span class="sxs-lookup"><span data-stu-id="ff427-167">Teams store validation guidelines</span></span>](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#44-screenshots)
* [<span data-ttu-id="ff427-168">Criar imagens eficazes para lojas de aplicativos da Microsoft</span><span class="sxs-lookup"><span data-stu-id="ff427-168">Craft effective images for Microsoft app stores</span></span>](/office/dev/store/craft-effective-appsource-store-images)

### <a name="create-a-video"></a><span data-ttu-id="ff427-169">Crie um vídeo</span><span class="sxs-lookup"><span data-stu-id="ff427-169">Create a video</span></span>

<span data-ttu-id="ff427-170">Um vídeo em sua listagem pode ser a maneira mais eficaz de comunicar por que as pessoas devem usar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff427-170">A video in your listing can be the most effective way to communicate why people should use your app.</span></span> <span data-ttu-id="ff427-171">Você deve abordar as seguintes perguntas em um vídeo:</span><span class="sxs-lookup"><span data-stu-id="ff427-171">You should address the following questions in a video:</span></span>

* <span data-ttu-id="ff427-172">Who é o seu aplicativo?</span><span class="sxs-lookup"><span data-stu-id="ff427-172">Who is your app for?</span></span>
* <span data-ttu-id="ff427-173">Quais problemas seu aplicativo pode resolver?</span><span class="sxs-lookup"><span data-stu-id="ff427-173">What problems can your app solve?</span></span>
* <span data-ttu-id="ff427-174">Como funciona seu aplicativo?</span><span class="sxs-lookup"><span data-stu-id="ff427-174">How does your app work?</span></span>
* <span data-ttu-id="ff427-175">Que outros benefícios você recebe com o uso do seu aplicativo?</span><span class="sxs-lookup"><span data-stu-id="ff427-175">What other benefits do you get from using your app?</span></span>

#### <a name="best-practices-for-videos"></a><span data-ttu-id="ff427-176">Melhores práticas para vídeos</span><span class="sxs-lookup"><span data-stu-id="ff427-176">Best practices for videos</span></span>

* <span data-ttu-id="ff427-177">Mantenha seu vídeo entre 30 e 90 segundos.</span><span class="sxs-lookup"><span data-stu-id="ff427-177">Keep your video between 30-90 seconds.</span></span>
* <span data-ttu-id="ff427-178">Mire na qualidade.</span><span class="sxs-lookup"><span data-stu-id="ff427-178">Aim for quality.</span></span> <span data-ttu-id="ff427-179">Em uma listagem, os usuários verão seu vídeo antes das capturas de tela.</span><span class="sxs-lookup"><span data-stu-id="ff427-179">In a listing, users will see your video before screenshots.</span></span>

### <a name="select-a-category-for-your-app"></a><span data-ttu-id="ff427-180">Selecione uma categoria para o seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="ff427-180">Select a category for your app</span></span>

<span data-ttu-id="ff427-181">Durante a apresentação, você é solicitado a categorizar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff427-181">During submission, you're asked to categorize your app.</span></span> <span data-ttu-id="ff427-182">Os mapas de tabela a seguir Teams categorias de loja para as categorias listadas no [Partner Center](https://aka.ms/PartnerCenterHomePage).</span><span class="sxs-lookup"><span data-stu-id="ff427-182">The following table maps Teams store categories to the categories listed in [Partner Center](https://aka.ms/PartnerCenterHomePage).</span></span>

| <span data-ttu-id="ff427-183">categorias Teams</span><span class="sxs-lookup"><span data-stu-id="ff427-183">Teams categories</span></span>       | <span data-ttu-id="ff427-184">Categorias do Centro de Parceiros</span><span class="sxs-lookup"><span data-stu-id="ff427-184">Partner Center categories</span></span>  |
|:---------------------|:---------------|
| <span data-ttu-id="ff427-185">Analytics e BI</span><span class="sxs-lookup"><span data-stu-id="ff427-185">Analytics and BI</span></span> | <span data-ttu-id="ff427-186">Analytics, Visualização de Dados e BI</span><span class="sxs-lookup"><span data-stu-id="ff427-186">Analytics, Data Visualization and BI</span></span> |
| <span data-ttu-id="ff427-187">Desenvolvedor e TI</span><span class="sxs-lookup"><span data-stu-id="ff427-187">Developer and IT</span></span> | <span data-ttu-id="ff427-188">Ferramentas de desenvolvedor, administrador de TI</span><span class="sxs-lookup"><span data-stu-id="ff427-188">Developer Tools, IT Admin</span></span> |
| <span data-ttu-id="ff427-189">Educação</span><span class="sxs-lookup"><span data-stu-id="ff427-189">Education</span></span> | <span data-ttu-id="ff427-190">Educação</span><span class="sxs-lookup"><span data-stu-id="ff427-190">Education</span></span> |
| <span data-ttu-id="ff427-191">Recursos humanos</span><span class="sxs-lookup"><span data-stu-id="ff427-191">Human resources</span></span> | <span data-ttu-id="ff427-192">Recursos Humanos e Recrutamento</span><span class="sxs-lookup"><span data-stu-id="ff427-192">Human Resources and Recruiting</span></span> |
| <span data-ttu-id="ff427-193">Produtividade</span><span class="sxs-lookup"><span data-stu-id="ff427-193">Productivity</span></span> | <span data-ttu-id="ff427-194">Gerenciamento de Conteúdo, Arquivos e documentos, Produtividade, Treinamento e Tutoriais e Utilidades</span><span class="sxs-lookup"><span data-stu-id="ff427-194">Content Management, Files and documents, Productivity, Training and Tutorials, and Utilities</span></span> |
| <span data-ttu-id="ff427-195">Gerenciamento de projeto</span><span class="sxs-lookup"><span data-stu-id="ff427-195">Project management</span></span> | <span data-ttu-id="ff427-196">Comunicação, Gestão de Project, Fluxo de Trabalho e Gestão de Negócios</span><span class="sxs-lookup"><span data-stu-id="ff427-196">Communication, Project Management, Workflow, and Business Management</span></span> |
| <span data-ttu-id="ff427-197">Vendas e suporte</span><span class="sxs-lookup"><span data-stu-id="ff427-197">Sales and support</span></span> | <span data-ttu-id="ff427-198">Gestão de Clientes e Contatos, Suporte ao Cliente, Gestão Financeira, Vendas e Marketing</span><span class="sxs-lookup"><span data-stu-id="ff427-198">Customer and Contact Management, Customer Support, Financial Management, Sales and Marketing</span></span> |
| <span data-ttu-id="ff427-199">Social e divertido</span><span class="sxs-lookup"><span data-stu-id="ff427-199">Social and fun</span></span> | <span data-ttu-id="ff427-200">Galerias de Imagens e Vídeos, Estilo de Vida, Notícias e Clima, Social, Viagem e Navegação</span><span class="sxs-lookup"><span data-stu-id="ff427-200">Image and Video Galleries, Lifestyle, News and Weather, Social, Travel, and Navigation</span></span> |

### <a name="localize-your-store-listing"></a><span data-ttu-id="ff427-201">Localize sua lista de lojas</span><span class="sxs-lookup"><span data-stu-id="ff427-201">Localize your store listing</span></span>

<span data-ttu-id="ff427-202">O Partner Center suporta [listagens localizadas de lojas](/office/dev/store/prepare-localized-solutions).</span><span class="sxs-lookup"><span data-stu-id="ff427-202">Partner Center supports [localized store listings](/office/dev/store/prepare-localized-solutions).</span></span> <span data-ttu-id="ff427-203">Para obter mais informações, consulte [como localizar sua lista de aplicativos Teams](../../../../concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="ff427-203">For more information, see [how to localize your Teams app listing](../../../../concepts/build-and-test/apps-localization.md).</span></span>

## <a name="complete-publisher-verification"></a><span data-ttu-id="ff427-204">Verificação completa de Publisher</span><span class="sxs-lookup"><span data-stu-id="ff427-204">Complete Publisher Verification</span></span>

<span data-ttu-id="ff427-205">[Publisher Verificação](/azure/active-directory/develop/publisher-verification-overview) é necessária para Teams aplicativos listados na loja.</span><span class="sxs-lookup"><span data-stu-id="ff427-205">[Publisher Verification](/azure/active-directory/develop/publisher-verification-overview) is required for Teams apps listed in the store.</span></span> <span data-ttu-id="ff427-206">Para obter mais informações, consulte [perguntas frequentes,](/azure/active-directory/develop/publisher-verification-overview#frequently-asked-questions) [como marcar seu aplicativo como editor verificado](/azure/active-directory/develop/mark-app-as-publisher-verified)e [solucionar problemas de verificação do editor](/azure/active-directory/develop/troubleshoot-publisher-verification).</span><span class="sxs-lookup"><span data-stu-id="ff427-206">For more information, see [frequently asked questions](/azure/active-directory/develop/publisher-verification-overview#frequently-asked-questions), [how to mark your app as publisher verified](/azure/active-directory/develop/mark-app-as-publisher-verified), and [troubleshoot publisher verification](/azure/active-directory/develop/troubleshoot-publisher-verification).</span></span>

## <a name="complete-publisher-attestation"></a><span data-ttu-id="ff427-207">Attestation completo de Publisher</span><span class="sxs-lookup"><span data-stu-id="ff427-207">Complete Publisher Attestation</span></span>

<span data-ttu-id="ff427-208">[Publisher Attestation](/microsoft-365-app-certification/docs/attestation) também é necessário para Teams aplicativos listados na loja.</span><span class="sxs-lookup"><span data-stu-id="ff427-208">[Publisher Attestation](/microsoft-365-app-certification/docs/attestation) is also required for Teams apps listed in the store.</span></span> <span data-ttu-id="ff427-209">O processo inclui completar uma autoavaliação das práticas de segurança, manipulação de dados e conformidade do seu aplicativo que podem ajudar potenciais clientes a tomar decisões informadas sobre o uso do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff427-209">The process includes completing a self-assessment of your app's security, data handling, and compliance practices that can help potential customers make informed decisions about using your app.</span></span>

> [!NOTE]
> <span data-ttu-id="ff427-210">Se você está enviando um novo aplicativo, você não pode completar oficialmente Publisher Attestation até que seu aplicativo esteja listado na loja Teams.</span><span class="sxs-lookup"><span data-stu-id="ff427-210">If you're submitting a new app, you can't officially complete Publisher Attestation until your app is listed on the Teams store.</span></span> <span data-ttu-id="ff427-211">Se você estiver atualizando um aplicativo listado, complete Publisher Attestation antes de enviar a versão mais recente do aplicativo para validação.</span><span class="sxs-lookup"><span data-stu-id="ff427-211">If you're updating a listed app, complete Publisher Attestation before you submit the latest version of the app for validation.</span></span>

## <a name="next-step"></a><span data-ttu-id="ff427-212">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="ff427-212">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ff427-213">Enviar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="ff427-213">Submit your app</span></span>](/office/dev/store/add-in-submission-guide)
