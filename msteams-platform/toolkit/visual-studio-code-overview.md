---
title: Criar aplicativos com o Microsoft Teams Toolkit e Visual Studio Código
description: Começar a criar grandes aplicativos personalizados diretamente Visual Studio Código com o microsoft Teams Toolkit
keywords: kit de ferramentas de código do visual studio do teams
localization_priority: Normal
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: 59f2943f37856c42346b2ffad4e01d88910679ae
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020258"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio-code"></a><span data-ttu-id="bd4d5-104">Criar aplicativos com o Teams Toolkit e Visual Studio Código</span><span class="sxs-lookup"><span data-stu-id="bd4d5-104">Build apps with the Teams Toolkit and Visual Studio Code</span></span>

<span data-ttu-id="bd4d5-105">O Kit de Ferramentas do Microsoft Teams permite criar aplicativos personalizados do Teams diretamente no ambiente do Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="bd4d5-105">The Microsoft Teams Toolkit enables you to create custom Teams apps directly within the Visual Studio Code environment.</span></span> <span data-ttu-id="bd4d5-106">O kit de ferramentas guia você através do processo e fornece o necessário para criar, depurar e iniciar seu aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="bd4d5-106">The toolkit guides you through the process and provides everything you need to build, debug, and launch your Teams app.</span></span>

## <a name="installing-the-teams-toolkit"></a><span data-ttu-id="bd4d5-107">Instalar o teams Toolkit</span><span class="sxs-lookup"><span data-stu-id="bd4d5-107">Installing the Teams Toolkit</span></span>

<span data-ttu-id="bd4d5-108">O Microsoft Teams Toolkit para Visual Studio Code está disponível para download do [Visual Studio Marketplace](https://aka.ms/teams-toolkit) ou diretamente como uma extensão dentro do Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="bd4d5-108">The Microsoft Teams Toolkit for Visual Studio Code is available for download from the [Visual Studio Marketplace](https://aka.ms/teams-toolkit) or directly as an extension within Visual Studio Code.</span></span>

> [!TIP]
> <span data-ttu-id="bd4d5-109">Após a instalação, você deve ver o teams Toolkit na barra de atividades Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="bd4d5-109">After installation, you should see the Teams Toolkit in the Visual Studio Code activity bar.</span></span> <span data-ttu-id="bd4d5-110">Caso não seja, clique com o botão direito do mouse na barra de atividades e selecione **Microsoft Teams** para fixar o kit de ferramentas para facilitar o acesso.</span><span class="sxs-lookup"><span data-stu-id="bd4d5-110">If not, right-click within the activity bar and select **Microsoft Teams** to pin the toolkit for easy access.</span></span>

## <a name="using-the-toolkit"></a><span data-ttu-id="bd4d5-111">Usando o kit de ferramentas</span><span class="sxs-lookup"><span data-stu-id="bd4d5-111">Using the toolkit</span></span>

- [<span data-ttu-id="bd4d5-112">Configurar um novo projeto</span><span class="sxs-lookup"><span data-stu-id="bd4d5-112">Set up a new project</span></span>](#set-up-a-new-teams-project)
- [<span data-ttu-id="bd4d5-113">Importar um projeto existente</span><span class="sxs-lookup"><span data-stu-id="bd4d5-113">Import an existing project</span></span>](#import-an-existing-teams-app-project)
- [<span data-ttu-id="bd4d5-114">Configurar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="bd4d5-114">Configure your app</span></span>](#configure-your-app)
- [<span data-ttu-id="bd4d5-115">Empacote seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="bd4d5-115">Package your app</span></span>](#package-your-app)
- [<span data-ttu-id="bd4d5-116">Executar seu aplicativo localmente ou no Teams</span><span class="sxs-lookup"><span data-stu-id="bd4d5-116">Run your app locally or in Teams</span></span>](#run-your-app)

## <a name="set-up-a-new-teams-project"></a><span data-ttu-id="bd4d5-117">Configurar um novo projeto do Teams</span><span class="sxs-lookup"><span data-stu-id="bd4d5-117">Set up a new Teams project</span></span>

1. <span data-ttu-id="bd4d5-118">Crie um espaço de trabalho/pasta para seu projeto em seu ambiente local.</span><span class="sxs-lookup"><span data-stu-id="bd4d5-118">Create a workspace/folder for your project in your local environment.</span></span>
1. <span data-ttu-id="bd4d5-119">Em Visual Studio Código, selecione o ícone do Teams</span><span class="sxs-lookup"><span data-stu-id="bd4d5-119">In Visual Studio Code, select the Teams icon</span></span> ![Ícone do Teams](../assets/icons/favicon-16x16.png) <span data-ttu-id="bd4d5-121">da barra de atividades no lado esquerdo da janela.</span><span class="sxs-lookup"><span data-stu-id="bd4d5-121">from the activity bar on the left side of the window.</span></span>
1. <span data-ttu-id="bd4d5-122">Selecione **Abrir o microsoft teams Toolkit** no menu de comando.</span><span class="sxs-lookup"><span data-stu-id="bd4d5-122">Select **Open the Microsoft Teams Toolkit** from the command menu.</span></span>
1. <span data-ttu-id="bd4d5-123">Selecione **Criar um novo aplicativo do Teams** no menu de comando.</span><span class="sxs-lookup"><span data-stu-id="bd4d5-123">Select **Create a new Teams app** from the command menu.</span></span>
1. <span data-ttu-id="bd4d5-124">Quando solicitado, digite o nome do espaço de trabalho .</span><span class="sxs-lookup"><span data-stu-id="bd4d5-124">When prompted, enter the name of the workspace .</span></span> <span data-ttu-id="bd4d5-125">Isso será usado como o nome da pasta onde seu projeto irá residir e o nome padrão do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bd4d5-125">This will be used as both the name of the folder where your project will reside, and the default name of your app.</span></span>
1. <span data-ttu-id="bd4d5-126">Pressione **Enter** e você chegará à tela **Adicionar recursos** configurar as propriedades do seu novo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bd4d5-126">Press **Enter** and you will arrive at the **Add capabilities** screen configure the properties for your new app.</span></span>
1. <span data-ttu-id="bd4d5-127">Selecione o **botão Concluir** para concluir o processo de configuração.</span><span class="sxs-lookup"><span data-stu-id="bd4d5-127">Select the **Finish** button to complete the configuration process.</span></span>

## <a name="import-an-existing-teams-app-project"></a><span data-ttu-id="bd4d5-128">Importar um projeto de aplicativo existente do Teams</span><span class="sxs-lookup"><span data-stu-id="bd4d5-128">Import an existing Teams app project</span></span>

1. <span data-ttu-id="bd4d5-129">Em Visual Studio Código, selecione o ícone do Teams</span><span class="sxs-lookup"><span data-stu-id="bd4d5-129">In Visual Studio Code, select the Teams icon</span></span> ![Ícone do Teams](../assets/icons/favicon-16x16.png) <span data-ttu-id="bd4d5-131">da barra de atividades no lado esquerdo da janela.</span><span class="sxs-lookup"><span data-stu-id="bd4d5-131">from the activity bar on the left side of the window.</span></span>
1. <span data-ttu-id="bd4d5-132">Selecione **Importar pacote de aplicativos** no menu de comando.</span><span class="sxs-lookup"><span data-stu-id="bd4d5-132">Select **Import app package** from the command menu.</span></span>
1. <span data-ttu-id="bd4d5-133">Escolha o arquivo zip do [pacote de aplicativos do Teams](../concepts/build-and-test/apps-package.md) existente.</span><span class="sxs-lookup"><span data-stu-id="bd4d5-133">Choose your existing [Teams app package](../concepts/build-and-test/apps-package.md) zip file.</span></span>
1. <span data-ttu-id="bd4d5-134">Escolha o **botão Selecionar pacote de publicação.**</span><span class="sxs-lookup"><span data-stu-id="bd4d5-134">Choose the **Select publishing package** button.</span></span> <span data-ttu-id="bd4d5-135">A guia de configuração do kit de ferramentas agora deve ser preenchida com os detalhes do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bd4d5-135">The configuration tab of the toolkit should now be populated with your app's details.</span></span>
1. <span data-ttu-id="bd4d5-136">Em Visual Studio Código, selecione **Adicionar** Pasta de Arquivo ao Espaço de Trabalho para adicionar seu diretório de código-fonte ao espaço de trabalho  ->   Visual Studio Código.</span><span class="sxs-lookup"><span data-stu-id="bd4d5-136">In Visual Studio Code, select **File** -> **Add Folder to Workspace** to add your source code directory to the Visual Studio Code workspace.</span></span>

## <a name="configure-your-app"></a><span data-ttu-id="bd4d5-137">Configurar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="bd4d5-137">Configure your app</span></span>

<span data-ttu-id="bd4d5-138">Em sua essência, o aplicativo do Teams abrange três componentes:</span><span class="sxs-lookup"><span data-stu-id="bd4d5-138">At its core, the Teams app embraces three components:</span></span>

  1. <span data-ttu-id="bd4d5-139">O cliente do Microsoft Teams (Web, desktop ou móvel) onde os usuários interagem com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bd4d5-139">The Microsoft Teams client (web, desktop or mobile) where users interact with your app.</span></span>
  1. <span data-ttu-id="bd4d5-140">Um servidor que responde a solicitações de conteúdo que serão exibidas no Teams, por exemplo, conteúdo de guia HTML ou um cartão adaptável de bot.</span><span class="sxs-lookup"><span data-stu-id="bd4d5-140">A server that responds to requests for content that will be displayed in Teams, e.g., HTML tab content or a bot adaptive card .</span></span>
  1. <span data-ttu-id="bd4d5-141">Um pacote [de aplicativos do](/concepts/build-and-test/apps-package.md) Teams que consiste em três arquivos:</span><span class="sxs-lookup"><span data-stu-id="bd4d5-141">A Teams [app package](/concepts/build-and-test/apps-package.md) consisting of three files:</span></span>

  > [!div class="checklist"]
  >
  > - <span data-ttu-id="bd4d5-142">O manifest.json</span><span class="sxs-lookup"><span data-stu-id="bd4d5-142">The manifest.json</span></span> 
  > - <span data-ttu-id="bd4d5-143">Um [ícone de cor](../resources/schema/manifest-schema.md#icons) para seu aplicativo ser exibido no catálogo de aplicativos público ou da organização</span><span class="sxs-lookup"><span data-stu-id="bd4d5-143">A [color icon](../resources/schema/manifest-schema.md#icons) for your app to display in the public or organization app catalog</span></span>
 > - <span data-ttu-id="bd4d5-144">Um [ícone de contorno](../resources/schema/manifest-schema.md#icons) para exibição na barra de atividades do Teams.</span><span class="sxs-lookup"><span data-stu-id="bd4d5-144">An [outline icon](../resources/schema/manifest-schema.md#icons) for display on the Teams activity bar.</span></span>

<span data-ttu-id="bd4d5-145">Quando um aplicativo é instalado, o cliente do Teams analisará o arquivo de manifesto para determinar as informações necessárias, como o nome do seu aplicativo e a URL onde os serviços estão localizados.</span><span class="sxs-lookup"><span data-stu-id="bd4d5-145">When an app is installed, the Teams client parses the manifest file to determine needed information like the name of your app and the URL where the services are located.</span></span>

1. <span data-ttu-id="bd4d5-146">Para configurar seu aplicativo, navegue até a guia **Microsoft Teams Toolkit** no Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="bd4d5-146">To configure your app, navigate to the **Microsoft Teams Toolkit** tab in Visual Studio Code.</span></span>
1. <span data-ttu-id="bd4d5-147">Selecione **Editar pacote de aplicativos** para exibir a página Detalhes **do** aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bd4d5-147">Select **Edit app package** to view the **App details** page.</span></span>
1. <span data-ttu-id="bd4d5-148">A edição dos campos na página detalhes do aplicativo atualiza o conteúdo do arquivo manifest.jsno arquivo que, em última análise, será shipado como parte do pacote de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="bd4d5-148">Editing the fields in the App details page updates the contents of the manifest.json file that will ultimately ship as part of the app package.</span></span> <span data-ttu-id="bd4d5-149">*Consulte* [Editor de manifesto do App Studio](https://aka.ms/teams-toolkit-manifest)</span><span class="sxs-lookup"><span data-stu-id="bd4d5-149">*See* [App Studio manifest editor](https://aka.ms/teams-toolkit-manifest)</span></span>

## <a name="package-your-app"></a><span data-ttu-id="bd4d5-150">Empacote seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="bd4d5-150">Package your app</span></span>

<span data-ttu-id="bd4d5-151">Modificar a **página de** detalhes do aplicativo, os arquivos de manifesto ou **.env** na pasta **.publish** do aplicativo gerará automaticamente seu **arquivoDevelopment.zip.** </span><span class="sxs-lookup"><span data-stu-id="bd4d5-151">Modifying the **app details** page, **manifest**, or **.env** files in your app's  **.publish** folder will automatically generate your **Development.zip** file.</span></span> <span data-ttu-id="bd4d5-152">Você precisará incluir dois [ícones](../concepts/build-and-test/apps-package.md#app-icons) na mesma pasta.</span><span class="sxs-lookup"><span data-stu-id="bd4d5-152">You'll need to include [two icons](../concepts/build-and-test/apps-package.md#app-icons) in that same folder.</span></span>

## <a name="install-and-run-your-app-locally"></a><span data-ttu-id="bd4d5-153">Instalar e executar seu aplicativo localmente</span><span class="sxs-lookup"><span data-stu-id="bd4d5-153">Install and run your app locally</span></span>

## <a name="run-your-app"></a><span data-ttu-id="bd4d5-154">Executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="bd4d5-154">Run your app</span></span>

### <a name="install-and-run-your-app-locally"></a><span data-ttu-id="bd4d5-155">Instalar e executar seu aplicativo localmente</span><span class="sxs-lookup"><span data-stu-id="bd4d5-155">Install and run your app locally</span></span>

<span data-ttu-id="bd4d5-156">Consulte a página inicial \**Criar* e Executar conteúdo em seu projeto para obter instruções detalhadas sobre como empacotar e testar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bd4d5-156">Refer to the \**Build and Run* content in your project homepage for detailed instructions on how to package and test your app.</span></span> <span data-ttu-id="bd4d5-157">Em geral, você precisa instalar o servidor do aplicativo, fazer com que ele seja executado e, em seguida, configurar uma solução de túnel para que o Teams possa acessar o conteúdo executado do localhost.</span><span class="sxs-lookup"><span data-stu-id="bd4d5-157">In general, you need to install your app's server, get it running, then setup a tunneling solution so that Teams can access content running from localhost.</span></span>

### <a name="enable-development-from-localhost"></a><span data-ttu-id="bd4d5-158">Habilitar o desenvolvimento do localhost</span><span class="sxs-lookup"><span data-stu-id="bd4d5-158">Enable development from localhost</span></span>

<span data-ttu-id="bd4d5-159">Se você deseja depurar seu aplicativo baseado em guia em localhost usando HTTPS, você precisará dizer ao navegador para confiar no aplicativo que está sendo servido de <https://localhost> .</span><span class="sxs-lookup"><span data-stu-id="bd4d5-159">If you wish to debug your tab based app on localhost using HTTPS, you will need to tell your browser to trust the app being served from <https://localhost>.</span></span> <span data-ttu-id="bd4d5-160">Navegue até <https://localhost:3000/tab>.</span><span class="sxs-lookup"><span data-stu-id="bd4d5-160">Navigate to <https://localhost:3000/tab>.</span></span> <span data-ttu-id="bd4d5-161">Se você vir um aviso indicando que o site não é confiável, escolha a opção para prosseguir de qualquer maneira.</span><span class="sxs-lookup"><span data-stu-id="bd4d5-161">If you see a warning indicating that the site isn't trusted, choose the option to proceed anyway.</span></span> <span data-ttu-id="bd4d5-162">Seu aplicativo agora deve estar acessível a partir do cliente do Teams.</span><span class="sxs-lookup"><span data-stu-id="bd4d5-162">Your app should now be accessible from the Teams client.</span></span>

### <a name="run-your-app-in-teams"></a><span data-ttu-id="bd4d5-163">Executar seu aplicativo no Teams</span><span class="sxs-lookup"><span data-stu-id="bd4d5-163">Run your app in Teams</span></span>

<span data-ttu-id="bd4d5-164">Pré-requisitos: [Habilitar o modo de visualização do desenvolvedor do Teams](https://aka.ms/teams-toolkit-enable-devpreview)</span><span class="sxs-lookup"><span data-stu-id="bd4d5-164">Prerequisites: [Enable Teams developer preview mode](https://aka.ms/teams-toolkit-enable-devpreview)</span></span>

1. <span data-ttu-id="bd4d5-165">Navegue até a barra de atividades no lado esquerdo da janela Visual Studio Código.</span><span class="sxs-lookup"><span data-stu-id="bd4d5-165">Navigate to the activity bar on the left side of the Visual Studio Code window.</span></span>
1. <span data-ttu-id="bd4d5-166">Selecione o **ícone Executar** para exibir o **exibição Executar e Depurar.**</span><span class="sxs-lookup"><span data-stu-id="bd4d5-166">Select the **Run** icon to display the **Run and Debug** view.</span></span>
1. <span data-ttu-id="bd4d5-167">Você também pode usar o atalho do teclado `Ctrl+Shift+D` .</span><span class="sxs-lookup"><span data-stu-id="bd4d5-167">You can also use the keyboard shortcut `Ctrl+Shift+D`.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bd4d5-168">Próxima etapa: manter e dar suporte ao aplicativo publicado</span><span class="sxs-lookup"><span data-stu-id="bd4d5-168">Next step: Maintaining and supporting your published app</span></span>](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
