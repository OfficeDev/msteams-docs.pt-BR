---
title: Criar aplicativos com o Microsoft Teams Toolkit e Visual Studio
description: Começar a criar grandes aplicativos personalizados diretamente Visual Studio com o microsoft Teams Toolkit
keywords: kit de ferramentas do visual studio do teams
localization_priority: Normal
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: bf8250e42bdf96073d729a19e921c400f242c67a
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020250"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio"></a><span data-ttu-id="846c7-104">Criar aplicativos com o teams Toolkit e Visual Studio</span><span class="sxs-lookup"><span data-stu-id="846c7-104">Build apps with the Teams Toolkit and Visual Studio</span></span>

<span data-ttu-id="846c7-105">O Kit de Ferramentas do Microsoft Teams permite criar aplicativos personalizados do Teams diretamente no ambiente de desenvolvimento integrado (IDE) do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="846c7-105">The Microsoft Teams Toolkit enables you to create custom Teams apps directly within the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="846c7-106">O kit de ferramentas do Microsoft Teams guia você através do processo e fornece o necessário para criar, depurar e iniciar seu aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="846c7-106">The Microsoft Teams toolkit guides you through the process and provides everything you need to build, debug, and launch your Teams app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="846c7-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="846c7-107">Prerequisites</span></span>

1. [<span data-ttu-id="846c7-108">Habilitar a visualização do desenvolvedor</span><span class="sxs-lookup"><span data-stu-id="846c7-108">Enable developer preview</span></span>](../resources/dev-preview/developer-preview-intro.md#enable-developer-preview)

1. <span data-ttu-id="846c7-109">Certifique-se de que **<span>o ASP.NE</span>T e** o módulo de desenvolvimento da Web foram adicionados à sua Visual Studio instância.</span><span class="sxs-lookup"><span data-stu-id="846c7-109">Make sure that the **<span>ASP.NE</span>T and web development module** has been added to your Visual Studio instance.</span></span> <span data-ttu-id="846c7-110">Você pode verificar seguindo as etapas na documentação Modificar Visual Studio adicionando ou [removendo cargas](/visualstudio/install/modify-visual-studio?view=vs-2019&preserve-view=true) de trabalho e componentes.</span><span class="sxs-lookup"><span data-stu-id="846c7-110">You can check by following the steps in the [Modify Visual Studio by adding or removing workloads and component](/visualstudio/install/modify-visual-studio?view=vs-2019&preserve-view=true) documentation.</span></span>

![módulo de asp.net visual studio](../assets/images/visual-studio-web-dev-module.png)

3. <span data-ttu-id="846c7-112">Se você quiser testar seu aplicativo implantando-o Visual Studio, você precisará ter o IIS (Serviços de Informações da Internet) instalado em seu ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="846c7-112">If you would like test your app by deploying it from Visual Studio, you'll need to have IIS (Internet Information Services) installed in your development environment.</span></span> <span data-ttu-id="846c7-113">Visual Studio não inclui o IIS e ele não está incluído na configuração padrão do Windows 10, do Windows 8 ou do Windows 7; no entanto, você pode baixar a versão mais recente do centro [de download da Microsoft.](https://www.microsoft.com/download/details.aspx?id=48264)</span><span class="sxs-lookup"><span data-stu-id="846c7-113">Visual Studio does not include IIS and it isn't included in the default Windows 10, Windows 8, or Windows 7 configuration; however, you can download the latest version from the [Microsoft download center](https://www.microsoft.com/download/details.aspx?id=48264).</span></span>

![Exibição de página de download do IIS](../assets/images/iis.png)

## <a name="install-the-teams-toolkit"></a><span data-ttu-id="846c7-115">Instalar o teams Toolkit</span><span class="sxs-lookup"><span data-stu-id="846c7-115">Install the Teams Toolkit</span></span>

<span data-ttu-id="846c7-116">O microsoft teams Toolkit para Visual Studio está disponível para download do [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.vsteamstemplate) ou diretamente no menu **Extensões** no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="846c7-116">The Microsoft Teams Toolkit for Visual Studio is available for download from the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.vsteamstemplate) or directly from the **Extensions** menu within Visual Studio.</span></span>

## <a name="using-the-toolkit"></a><span data-ttu-id="846c7-117">Usando o kit de ferramentas</span><span class="sxs-lookup"><span data-stu-id="846c7-117">Using the toolkit</span></span>

- [<span data-ttu-id="846c7-118">Configurar um novo projeto</span><span class="sxs-lookup"><span data-stu-id="846c7-118">Set up a new project</span></span>](#set-up-a-new-teams-project)
- [<span data-ttu-id="846c7-119">Configurar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="846c7-119">Configure your app</span></span>](#configure-your-app)
- [<span data-ttu-id="846c7-120">Empacote seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="846c7-120">Package your app</span></span>](#package-your-app)
- [<span data-ttu-id="846c7-121">Executar seu aplicativo no Teams</span><span class="sxs-lookup"><span data-stu-id="846c7-121">Run your app in Teams</span></span>](#install-and-run-your-app-locally)
- [<span data-ttu-id="846c7-122">Valide o seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="846c7-122">Validate your app</span></span>](#validate-your-app)
- [<span data-ttu-id="846c7-123">Publicar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="846c7-123">Publish your app</span></span>](#publish-your-app-to-teams)

## <a name="set-up-a-new-teams-project"></a><span data-ttu-id="846c7-124">Configurar um novo projeto do Teams</span><span class="sxs-lookup"><span data-stu-id="846c7-124">Set up a new Teams project</span></span>

1. <span data-ttu-id="846c7-125">Selecione **Criar um novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="846c7-125">Select **Create a new project**.</span></span>
1. <span data-ttu-id="846c7-126">Escolha **Microsoft Teams App** e selecione **Próximo**.</span><span class="sxs-lookup"><span data-stu-id="846c7-126">Choose **Microsoft Teams App** and select **Next**.</span></span>
1. <span data-ttu-id="846c7-127">Você chegará na tela **Configurar seu novo** projeto, onde poderá escolher o nome do **projeto,** **Local** e Nome **da solução.**</span><span class="sxs-lookup"><span data-stu-id="846c7-127">You will arrive at the **Configure your new project** screen where you can choose the **Project name**, **Location**, and **Solution name**.</span></span>
1. <span data-ttu-id="846c7-128">Marque a caixa rotulada **Place solution and project no mesmo diretório**.</span><span class="sxs-lookup"><span data-stu-id="846c7-128">Check the box labeled **Place solution and project in the same directory**.</span></span>
1. <span data-ttu-id="846c7-129">Uma janela pop-up rotulada de **Adicionar Recursos** permitirá que você escolha um ou mais recursos para a configuração do projeto.</span><span class="sxs-lookup"><span data-stu-id="846c7-129">A pop-up window labeled **Add Capabilities** will allow you to choose one or more capabilities for your project setup.</span></span>
1. <span data-ttu-id="846c7-130">Selecione o **botão Próximo** para concluir o processo de configuração.</span><span class="sxs-lookup"><span data-stu-id="846c7-130">Select the **Next** button to complete the configuration process.</span></span>
1. <span data-ttu-id="846c7-131">Uma janela pop-up rotulada **Adicionar Recursos** permitirá que você escolha as propriedades para cada recurso selecionado.</span><span class="sxs-lookup"><span data-stu-id="846c7-131">A pop-up window labeled **Add Capabilities** will allow you to choose the properties for each selected capability.</span></span>
1. <span data-ttu-id="846c7-132">Selecione **Concluir** e você pousará na página inicial do **Microsoft Teams Toolkit.**</span><span class="sxs-lookup"><span data-stu-id="846c7-132">Select **Finish** and you will  land on the **Microsoft Teams Toolkit** landing page.</span></span>

## <a name="configure-your-app"></a><span data-ttu-id="846c7-133">Configurar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="846c7-133">Configure your app</span></span>

<span data-ttu-id="846c7-134">Em sua essência, o aplicativo do Teams abrange três componentes:</span><span class="sxs-lookup"><span data-stu-id="846c7-134">At its core, the Teams app embraces three components:</span></span>

  1. <span data-ttu-id="846c7-135">O cliente do Microsoft Teams (Web, desktop ou móvel) onde os usuários interagem com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="846c7-135">The Microsoft Teams client (web, desktop or mobile) where users interact with your app.</span></span>
  1. <span data-ttu-id="846c7-136">Um servidor que responde a solicitações de conteúdo que serão exibidas no Teams, por exemplo, conteúdo de guia HTML ou um cartão adaptável de bot.</span><span class="sxs-lookup"><span data-stu-id="846c7-136">A server that responds to requests for content that will be displayed in Teams, e.g., HTML tab content or a bot adaptive card .</span></span>
  1. <span data-ttu-id="846c7-137">Um pacote [de aplicativos do](/concepts/build-and-test/apps-package.md) Teams que consiste em três arquivos:</span><span class="sxs-lookup"><span data-stu-id="846c7-137">A Teams [app package](/concepts/build-and-test/apps-package.md) consisting of three files:</span></span>

  > [!div class="checklist"]
  >
  > - <span data-ttu-id="846c7-138">O manifest.json</span><span class="sxs-lookup"><span data-stu-id="846c7-138">The manifest.json</span></span>
  > - <span data-ttu-id="846c7-139">Um [ícone de cor](../resources/schema/manifest-schema.md#icons) para seu aplicativo ser exibido no catálogo de aplicativos público ou da organização</span><span class="sxs-lookup"><span data-stu-id="846c7-139">A [color icon](../resources/schema/manifest-schema.md#icons) for your app to display in the public or organization app catalog</span></span>
 > - <span data-ttu-id="846c7-140">Um [ícone de contorno](../resources/schema/manifest-schema.md#icons) para exibição na barra de atividades do Teams.</span><span class="sxs-lookup"><span data-stu-id="846c7-140">An [outline icon](../resources/schema/manifest-schema.md#icons) for display on the Teams activity bar.</span></span>

<span data-ttu-id="846c7-141">Quando um aplicativo é instalado, o cliente do Teams analisará o arquivo de manifesto para determinar as informações necessárias, como o nome do seu aplicativo e a URL onde os serviços estão localizados.</span><span class="sxs-lookup"><span data-stu-id="846c7-141">When an app is installed, the Teams client parses the manifest file to determine needed information like the name of your app and the URL where the services are located.</span></span>

> [!NOTE]
><span data-ttu-id="846c7-142">Se você ainda não fez isso, precisará entrar no Microsoft 365 ou conta para continuar com o processo de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="846c7-142">If you haven't done so already, you will need to sign in to your Microsoft 365  or account to continue with the development process.</span></span>
>
> <span data-ttu-id="846c7-143">Se você não tiver uma conta do Microsoft 365, poderá inscrever-se para uma assinatura do Programa de Desenvolvedor [do Microsoft 365.](https://developer.microsoft.com/microsoft-365/dev-program)</span><span class="sxs-lookup"><span data-stu-id="846c7-143">If you don't have a Microsoft 365 account, you can sign up for a [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program) subscription.</span></span> <span data-ttu-id="846c7-144">Ele é gratuito *por* 90 dias e será continuamente renovado, desde que você esteja usando-o para atividades de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="846c7-144">It's *free* for 90 days and will continually renew as long as you're using it for development activity.</span></span> <span data-ttu-id="846c7-145">Se você tiver uma assinatura do Visual Studio *Enterprise* ou *Professional,* ambos os programas incluirão uma assinatura gratuita de desenvolvedor do Microsoft 365 [](https://aka.ms/MyVisualStudioBenefits), ativa para a vida da sua assinatura Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="846c7-145">If you have a Visual Studio *Enterprise* or *Professional* subscription, both programs include a free Microsoft 365 [developer subscription](https://aka.ms/MyVisualStudioBenefits), active for the life of your Visual Studio subscription.</span></span> <span data-ttu-id="846c7-146">*Consulte* Configurar uma assinatura de desenvolvedor do [Microsoft 365](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).</span><span class="sxs-lookup"><span data-stu-id="846c7-146">*See* [Set up a Microsoft 365 developer subscription](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).</span></span>
>

### <a name="configuration-steps"></a><span data-ttu-id="846c7-147">Etapas de configuração</span><span class="sxs-lookup"><span data-stu-id="846c7-147">Configuration steps</span></span>

1. <span data-ttu-id="846c7-148">Para configurar seu aplicativo, na página inicial do **Microsoft Teams Toolkit,** selecione **Editar pacote de aplicativos** .</span><span class="sxs-lookup"><span data-stu-id="846c7-148">To configure your app, on the **Microsoft Teams Toolkit** landing page, select **Edit app package** .</span></span>
1. <span data-ttu-id="846c7-149">No menu **suspenso Meus Ambientes,** selecione **desenvolvimento**.</span><span class="sxs-lookup"><span data-stu-id="846c7-149">From the **My Environments** drop-down menu, select **development**.</span></span>
1. <span data-ttu-id="846c7-150">Você pousará na página Detalhes **do aplicativo** onde poderá editar os campos de propriedades do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="846c7-150">You will land on the **App details** page where you can edit your app's property fields.</span></span>
1. <span data-ttu-id="846c7-151">A edição dos campos na página detalhes do aplicativo atualiza o conteúdo do arquivo manifest.jsno arquivo que, em última análise, será shipado como parte do pacote de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="846c7-151">Editing the fields in the App details page updates the contents of the manifest.json file that will ultimately ship as part of the app package.</span></span> [<span data-ttu-id="846c7-152">Saiba Mais</span><span class="sxs-lookup"><span data-stu-id="846c7-152">Learn more</span></span>](https://aka.ms/teams-toolkit-manifest)

## <a name="package-your-app"></a><span data-ttu-id="846c7-153">Empacote seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="846c7-153">Package your app</span></span>

<span data-ttu-id="846c7-154">Modificar a página de detalhes **do** aplicativo ou atualizar o **manifesto** ou **arquivos .env** na pasta **.publish** do aplicativo gerará automaticamente seu **arquivoDevelopment.zip.**</span><span class="sxs-lookup"><span data-stu-id="846c7-154">Modifying the **app details** page or updating the **manifest**, or **.env** files in your app's  **.publish** folder will automatically generate your **Development.zip** file.</span></span> <span data-ttu-id="846c7-155">O Development.zip inclui três arquivos necessários — omanifest.js **e** [dois ícones](../concepts/build-and-test/apps-package.md#app-icons).</span><span class="sxs-lookup"><span data-stu-id="846c7-155">The Development.zip file includes three required files — the **manifest.json** and [two icons](../concepts/build-and-test/apps-package.md#app-icons).</span></span>

## <a name="install-and-run-your-app-locally"></a><span data-ttu-id="846c7-156">Instalar e executar seu aplicativo localmente</span><span class="sxs-lookup"><span data-stu-id="846c7-156">Install and run your app locally</span></span>

1. <span data-ttu-id="846c7-157">No menu **suspenso Configurações** da Solução, selecione **Implantar**.</span><span class="sxs-lookup"><span data-stu-id="846c7-157">From the **Solution Configurations** dropdown menu, select **Deploy**.</span></span>

![Menu Configurações da solução](../assets/images/solution-configurations.png)

2. <span data-ttu-id="846c7-159">Selecione o **botão IIS Express + Teams.**</span><span class="sxs-lookup"><span data-stu-id="846c7-159">Select the **IIS Express + Teams** button.</span></span>

1. <span data-ttu-id="846c7-160">O Teams será lançado e o diálogo de instalação do aplicativo deverá aparecer no cliente do Teams.</span><span class="sxs-lookup"><span data-stu-id="846c7-160">Teams will launch and the app installation dialogue should appear in the Teams client.</span></span>

## <a name="validate-your-app"></a><span data-ttu-id="846c7-161">Valide o seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="846c7-161">Validate your app</span></span>

<span data-ttu-id="846c7-162">A **página Validar** permite que você verifique seu pacote de aplicativos antes de enviar seu aplicativo ao AppSource.</span><span class="sxs-lookup"><span data-stu-id="846c7-162">The **Validate** page allows you to check your app package before submitting your app to AppSource.</span></span> <span data-ttu-id="846c7-163">Basta carregar o pacote de manifesto e a ferramenta de validação verificará seu aplicativo em relação a todos os casos de teste relacionados ao manifesto.</span><span class="sxs-lookup"><span data-stu-id="846c7-163">Simply upload the manifest package and the validation tool will check your app against all manifest related test cases.</span></span> <span data-ttu-id="846c7-164">Para cada teste com falha, a descrição fornece um link de documentação para ajudá-lo a corrigir o erro.</span><span class="sxs-lookup"><span data-stu-id="846c7-164">For each failed tests, the description provides a documentation link to help you fix the error.</span></span> <span data-ttu-id="846c7-165">Para os testes difíceis de  automatizar, a lista de verificação preliminar detalha 7 dos casos de teste com falha mais comuns, bem como o link para uma lista de verificação de envio completa.</span><span class="sxs-lookup"><span data-stu-id="846c7-165">For the tests that are hard to automate, the **Preliminary checklist** details 7 of the most common failed test cases as well as link to a complete submission checklist.</span></span>

## <a name="publish-your-app-to-teams"></a><span data-ttu-id="846c7-166">Publicar seu aplicativo no Teams</span><span class="sxs-lookup"><span data-stu-id="846c7-166">Publish your app to Teams</span></span>

<span data-ttu-id="846c7-167">✔ Na home page do projeto, você pode carregar seu aplicativo em uma equipe, enviar seu aplicativo para a loja de aplicativos personalizada da sua empresa para usuários em sua organização ou enviar seu aplicativo para a Fonte do Aplicativo para todos os usuários do Teams.</span><span class="sxs-lookup"><span data-stu-id="846c7-167">✔ On your project home page, you can upload your app to a team, submit your app to your company custom app store for users in your organization, or submit your app to App Source for all Teams users.</span></span>

<span data-ttu-id="846c7-168">✔ seu administrador de IT revisará esses envios.</span><span class="sxs-lookup"><span data-stu-id="846c7-168">✔ Your IT admin will review these submissions.</span></span>

<span data-ttu-id="846c7-169">✔ Você pode retornar à  página Publicar para verificar o status do envio e saber se seu aplicativo foi aprovado ou rejeitado pelo administrador de TI. Também é aqui que você enviará atualizações para seu aplicativo ou cancelará quaisquer envios ativos no momento.</span><span class="sxs-lookup"><span data-stu-id="846c7-169">✔  You can return to the **Publish** page to check on your submission status and learn if your app was approved or rejected by your IT admin. This is also where you'll come to submit updates to your app or cancel any currently active submissions.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="846c7-170">Próxima etapa: manter e dar suporte ao aplicativo publicado</span><span class="sxs-lookup"><span data-stu-id="846c7-170">Next step: Maintaining and supporting your published app</span></span>](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
>
