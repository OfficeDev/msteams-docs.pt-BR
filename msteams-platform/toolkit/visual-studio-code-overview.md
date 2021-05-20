---
title: Crie aplicativos com o Microsoft Teams Toolkit e Visual Studio Code
description: Comece a construir ótimos aplicativos personalizados diretamente dentro de Visual Studio Code com o Microsoft Teams Toolkit
keywords: equipes estúdio visual código kit ferramentas
localization_priority: Normal
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: efd0962e9c4c0d64dbac47caf29b2e56907937b3
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566555"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio-code"></a><span data-ttu-id="84691-104">Crie aplicativos com os Teams Toolkit e Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="84691-104">Build apps with the Teams Toolkit and Visual Studio Code</span></span>

<span data-ttu-id="84691-105">O Kit de Ferramentas do Microsoft Teams permite criar aplicativos personalizados do Teams diretamente no ambiente do Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="84691-105">The Microsoft Teams Toolkit enables you to create custom Teams apps directly within the Visual Studio Code environment.</span></span> <span data-ttu-id="84691-106">O kit de ferramentas guia você através do processo e fornece o necessário para criar, depurar e iniciar seu aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="84691-106">The toolkit guides you through the process and provides everything you need to build, debug, and launch your Teams app.</span></span>

## <a name="installing-the-teams-toolkit"></a><span data-ttu-id="84691-107">Instalando o Teams Toolkit</span><span class="sxs-lookup"><span data-stu-id="84691-107">Installing the Teams Toolkit</span></span>

<span data-ttu-id="84691-108">O Microsoft Teams Toolkit para Visual Studio Code está disponível para download no [Visual Studio Marketplace](https://aka.ms/teams-toolkit) ou diretamente como uma extensão dentro de Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="84691-108">The Microsoft Teams Toolkit for Visual Studio Code is available for download from the [Visual Studio Marketplace](https://aka.ms/teams-toolkit) or directly as an extension within Visual Studio Code.</span></span>

> [!TIP]
> <span data-ttu-id="84691-109">Após a instalação, você deve ver o Teams Toolkit na barra de atividades Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="84691-109">After installation, you should see the Teams Toolkit in the Visual Studio Code activity bar.</span></span> <span data-ttu-id="84691-110">Caso não, clique com o botão direito do mouse na barra de atividades e selecione **Microsoft Teams** para fixar o kit de ferramentas para fácil acesso.</span><span class="sxs-lookup"><span data-stu-id="84691-110">If not, right-click within the activity bar and select **Microsoft Teams** to pin the toolkit for easy access.</span></span>

## <a name="using-the-toolkit"></a><span data-ttu-id="84691-111">Usando o kit de ferramentas</span><span class="sxs-lookup"><span data-stu-id="84691-111">Using the toolkit</span></span>

- [<span data-ttu-id="84691-112">Criar um novo projeto</span><span class="sxs-lookup"><span data-stu-id="84691-112">Set up a new project</span></span>](#set-up-a-new-teams-project)
- [<span data-ttu-id="84691-113">Importar um projeto existente</span><span class="sxs-lookup"><span data-stu-id="84691-113">Import an existing project</span></span>](#import-an-existing-teams-app-project)
- [<span data-ttu-id="84691-114">Configure seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="84691-114">Configure your app</span></span>](#configure-your-app)
- [<span data-ttu-id="84691-115">Empacote seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="84691-115">Package your app</span></span>](#package-your-app)
- [<span data-ttu-id="84691-116">Execute seu aplicativo localmente ou em Teams</span><span class="sxs-lookup"><span data-stu-id="84691-116">Run your app locally or in Teams</span></span>](#run-your-app)

## <a name="set-up-a-new-teams-project"></a><span data-ttu-id="84691-117">Criar um novo projeto de Teams</span><span class="sxs-lookup"><span data-stu-id="84691-117">Set up a new Teams project</span></span>

1. <span data-ttu-id="84691-118">Crie um espaço de trabalho ou pasta para o seu projeto em seu ambiente local.</span><span class="sxs-lookup"><span data-stu-id="84691-118">Create a workspace or folder for your project in your local environment.</span></span>
1. <span data-ttu-id="84691-119">Em Visual Studio Code, selecione o ícone Teams</span><span class="sxs-lookup"><span data-stu-id="84691-119">In Visual Studio Code, select the Teams icon</span></span> ![Ícone do Teams](../assets/icons/favicon-16x16.png) <span data-ttu-id="84691-121">da barra de atividade no lado esquerdo da janela.</span><span class="sxs-lookup"><span data-stu-id="84691-121">from the activity bar on the left side of the window.</span></span>
1. <span data-ttu-id="84691-122">Selecione **Abrir o Microsoft Teams Toolkit** no menu de comando.</span><span class="sxs-lookup"><span data-stu-id="84691-122">Select **Open the Microsoft Teams Toolkit** from the command menu.</span></span>
1. <span data-ttu-id="84691-123">Selecione **Criar um novo aplicativo de Teams** no menu de comando.</span><span class="sxs-lookup"><span data-stu-id="84691-123">Select **Create a new Teams app** from the command menu.</span></span>
1. <span data-ttu-id="84691-124">Quando solicitado, digite o nome do espaço de trabalho .</span><span class="sxs-lookup"><span data-stu-id="84691-124">When prompted, enter the name of the workspace .</span></span> <span data-ttu-id="84691-125">Isso será usado tanto como o nome da pasta onde seu projeto irá residir, quanto o nome padrão do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="84691-125">This will be used as both the name of the folder where your project will reside, and the default name of your app.</span></span>
1. <span data-ttu-id="84691-126">Pressione **Enter** e você chegará à tela **Adicionar recursos** configurar as propriedades para o seu novo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="84691-126">Press **Enter** and you will arrive at the **Add capabilities** screen configure the properties for your new app.</span></span>
1. <span data-ttu-id="84691-127">Selecione o botão **Terminar** para concluir o processo de configuração.</span><span class="sxs-lookup"><span data-stu-id="84691-127">Select the **Finish** button to complete the configuration process.</span></span>

## <a name="import-an-existing-teams-app-project"></a><span data-ttu-id="84691-128">Importar um projeto de aplicativo de Teams existente</span><span class="sxs-lookup"><span data-stu-id="84691-128">Import an existing Teams app project</span></span>

1. <span data-ttu-id="84691-129">Em Visual Studio Code, selecione o ícone Teams</span><span class="sxs-lookup"><span data-stu-id="84691-129">In Visual Studio Code, select the Teams icon</span></span> ![Ícone do Teams](../assets/icons/favicon-16x16.png) <span data-ttu-id="84691-131">da barra de atividade no lado esquerdo da janela.</span><span class="sxs-lookup"><span data-stu-id="84691-131">from the activity bar on the left side of the window.</span></span>
1. <span data-ttu-id="84691-132">Selecione **o pacote de aplicativos de importação** no menu de comando.</span><span class="sxs-lookup"><span data-stu-id="84691-132">Select **Import app package** from the command menu.</span></span>
1. <span data-ttu-id="84691-133">Escolha o arquivo zip do [pacote de Teams](../concepts/build-and-test/apps-package.md) existente.</span><span class="sxs-lookup"><span data-stu-id="84691-133">Choose your existing [Teams app package](../concepts/build-and-test/apps-package.md) zip file.</span></span>
1. <span data-ttu-id="84691-134">Escolha o botão **Selecionar pacote de publicação.**</span><span class="sxs-lookup"><span data-stu-id="84691-134">Choose the **Select publishing package** button.</span></span> <span data-ttu-id="84691-135">A guia de configuração do kit de ferramentas deve agora ser preenchida com os detalhes do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="84691-135">The configuration tab of the toolkit should now be populated with your app's details.</span></span>
1. <span data-ttu-id="84691-136">Em Visual Studio Code, selecione **Arquivo**  ->  **Adicionar pasta ao espaço de trabalho** para adicionar seu diretório de código-fonte ao espaço de trabalho Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="84691-136">In Visual Studio Code, select **File** -> **Add Folder to Workspace** to add your source code directory to the Visual Studio Code workspace.</span></span>

## <a name="configure-your-app"></a><span data-ttu-id="84691-137">Configure seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="84691-137">Configure your app</span></span>

<span data-ttu-id="84691-138">Em sua essência, o aplicativo Teams abraça três componentes:</span><span class="sxs-lookup"><span data-stu-id="84691-138">At its core, the Teams app embraces three components:</span></span>

  1. <span data-ttu-id="84691-139">O Microsoft Teams cliente (web, desktop ou celular) onde os usuários interagem com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="84691-139">The Microsoft Teams client (web, desktop or mobile) where users interact with your app.</span></span>
  1. <span data-ttu-id="84691-140">Um servidor que responde a solicitações de conteúdo que será exibido em Teams.</span><span class="sxs-lookup"><span data-stu-id="84691-140">A server that responds to requests for content that will be displayed in Teams.</span></span> <span data-ttu-id="84691-141">Por exemplo, conteúdo de guia HTML ou um cartão adaptativo de bot.</span><span class="sxs-lookup"><span data-stu-id="84691-141">For example, HTML tab content or a bot adaptive card.</span></span>
  1. <span data-ttu-id="84691-142">Um [pacote de aplicativo](/concepts/build-and-test/apps-package.md) Teams composto por três arquivos:</span><span class="sxs-lookup"><span data-stu-id="84691-142">A Teams [app package](/concepts/build-and-test/apps-package.md) consisting of three files:</span></span>

      > [!div class="checklist"]
      >
      > - <span data-ttu-id="84691-143">O manifest.js.</span><span class="sxs-lookup"><span data-stu-id="84691-143">The manifest.json.</span></span> 
      > - <span data-ttu-id="84691-144">Um [ícone de cores](../resources/schema/manifest-schema.md#icons) para seu aplicativo ser exibido no catálogo do aplicativo público ou de organização.</span><span class="sxs-lookup"><span data-stu-id="84691-144">A [color icon](../resources/schema/manifest-schema.md#icons) for your app to display in the public or organization app catalog.</span></span>
      > - <span data-ttu-id="84691-145">Um [ícone de contorno](../resources/schema/manifest-schema.md#icons) para exibição na barra de atividades Teams.</span><span class="sxs-lookup"><span data-stu-id="84691-145">An [outline icon](../resources/schema/manifest-schema.md#icons) for display on the Teams activity bar.</span></span>

<span data-ttu-id="84691-146">Quando um aplicativo é instalado, o cliente Teams analisa o arquivo manifesto para determinar informações necessárias, como o nome do seu aplicativo e a URL onde os serviços estão localizados.</span><span class="sxs-lookup"><span data-stu-id="84691-146">When an app is installed, the Teams client parses the manifest file to determine needed information like the name of your app and the URL where the services are located.</span></span>

1. <span data-ttu-id="84691-147">Para configurar seu aplicativo, navegue até a guia **Microsoft Teams Toolkit** em Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="84691-147">To configure your app, navigate to the **Microsoft Teams Toolkit** tab in Visual Studio Code.</span></span>
1. <span data-ttu-id="84691-148">Selecione **Editar pacote de aplicativo** para exibir a página de detalhes do **Aplicativo.**</span><span class="sxs-lookup"><span data-stu-id="84691-148">Select **Edit app package** to view the **App details** page.</span></span>
1. <span data-ttu-id="84691-149">A edição dos campos na página de detalhes do App atualiza o conteúdo do manifest.jsno arquivo que, em última análise, será enviado como parte do pacote do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="84691-149">Editing the fields in the App details page updates the contents of the manifest.json file that will ultimately ship as part of the app package.</span></span> <span data-ttu-id="84691-150">Para obter mais informações, consulte [o editor manifesto do App Studio](https://aka.ms/teams-toolkit-manifest)</span><span class="sxs-lookup"><span data-stu-id="84691-150">For more information, See [App Studio manifest editor](https://aka.ms/teams-toolkit-manifest)</span></span>

## <a name="package-your-app"></a><span data-ttu-id="84691-151">Empacote seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="84691-151">Package your app</span></span>

<span data-ttu-id="84691-152">Modificar os **detalhes** do aplicativo página, **manifesto** ou **arquivos .env** na pasta **.publish** do seu aplicativo gerará automaticamente o **seu arquivoDevelopment.zip.**</span><span class="sxs-lookup"><span data-stu-id="84691-152">Modifying the **app details** page, **manifest**, or **.env** files in your app's  **.publish** folder will automatically generate your **Development.zip** file.</span></span> <span data-ttu-id="84691-153">Você precisará incluir [dois ícones](../concepts/build-and-test/apps-package.md#app-icons) na mesma pasta.</span><span class="sxs-lookup"><span data-stu-id="84691-153">You'll need to include [two icons](../concepts/build-and-test/apps-package.md#app-icons) in that same folder.</span></span>

## <a name="install-and-run-your-app-locally"></a><span data-ttu-id="84691-154">Instale e execute seu aplicativo localmente</span><span class="sxs-lookup"><span data-stu-id="84691-154">Install and run your app locally</span></span>

## <a name="run-your-app"></a><span data-ttu-id="84691-155">Execute seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="84691-155">Run your app</span></span>

### <a name="install-and-run-your-app-locally"></a><span data-ttu-id="84691-156">Instale e execute seu aplicativo localmente</span><span class="sxs-lookup"><span data-stu-id="84691-156">Install and run your app locally</span></span>

<span data-ttu-id="84691-157">Consulte o conteúdo **Build and Run** na página inicial do projeto para obter instruções detalhadas sobre como empacotar e testar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="84691-157">Refer to the **Build and Run** content in your project homepage for detailed instructions on how to package and test your app.</span></span> <span data-ttu-id="84691-158">Em geral, você precisa instalar o servidor do seu aplicativo, fazê-lo funcionar e, em seguida, configurar uma solução de tunelamento para que Teams possa acessar o conteúdo executado a partir do local.</span><span class="sxs-lookup"><span data-stu-id="84691-158">In general, you need to install your app's server, get it running, then setup a tunneling solution so that Teams can access content running from localhost.</span></span>

### <a name="enable-development-from-localhost"></a><span data-ttu-id="84691-159">Permitir o desenvolvimento a partir do localhost</span><span class="sxs-lookup"><span data-stu-id="84691-159">Enable development from localhost</span></span>

<span data-ttu-id="84691-160">Se você deseja depurar seu aplicativo baseado em guia no localhost usando HTTPS, você precisará dizer ao seu navegador para confiar no aplicativo que está sendo servido <https://localhost> .</span><span class="sxs-lookup"><span data-stu-id="84691-160">If you wish to debug your tab based app on localhost using HTTPS, you will need to tell your browser to trust the app being served from <https://localhost>.</span></span> <span data-ttu-id="84691-161">Navegue até <https://localhost:3000/tab>.</span><span class="sxs-lookup"><span data-stu-id="84691-161">Navigate to <https://localhost:3000/tab>.</span></span> <span data-ttu-id="84691-162">Se você vir um aviso indicando que o site não é confiável, escolha a opção de prosseguir de qualquer maneira.</span><span class="sxs-lookup"><span data-stu-id="84691-162">If you see a warning indicating that the site isn't trusted, choose the option to proceed anyway.</span></span> <span data-ttu-id="84691-163">Seu aplicativo agora deve ser acessível a partir do cliente Teams.</span><span class="sxs-lookup"><span data-stu-id="84691-163">Your app should now be accessible from the Teams client.</span></span>

### <a name="run-your-app-in-teams"></a><span data-ttu-id="84691-164">Execute seu aplicativo em Teams</span><span class="sxs-lookup"><span data-stu-id="84691-164">Run your app in Teams</span></span>

<span data-ttu-id="84691-165">Pré-requisitos: [Habilitar Teams modo de visualização do desenvolvedor](https://aka.ms/teams-toolkit-enable-devpreview)</span><span class="sxs-lookup"><span data-stu-id="84691-165">Prerequisites: [Enable Teams developer preview mode](https://aka.ms/teams-toolkit-enable-devpreview)</span></span>

1. <span data-ttu-id="84691-166">Navegue até a barra de atividade no lado esquerdo da janela Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="84691-166">Navigate to the activity bar on the left side of the Visual Studio Code window.</span></span>
1. <span data-ttu-id="84691-167">Selecione o ícone **Executar** para exibir a **exibição de Executar e Depurar.**</span><span class="sxs-lookup"><span data-stu-id="84691-167">Select the **Run** icon to display the **Run and Debug** view.</span></span>
1. <span data-ttu-id="84691-168">Você também pode usar o atalho do teclado `Ctrl+Shift+D` .</span><span class="sxs-lookup"><span data-stu-id="84691-168">You can also use the keyboard shortcut `Ctrl+Shift+D`.</span></span>

## <a name="next-step"></a><span data-ttu-id="84691-169">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="84691-169">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="84691-170">Mantendo e apoiando seu aplicativo publicado</span><span class="sxs-lookup"><span data-stu-id="84691-170">Maintaining and supporting your published app</span></span>](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
