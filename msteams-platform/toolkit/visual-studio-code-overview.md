---
title: Criar aplicativos com o Microsoft Teams Toolkit e o Visual Studio Code
description: Introdução ao desenvolvimento de aplicativos personalizados de grande parte diretamente no Visual Studio Code com o Microsoft Teams Toolkit
keywords: Kit de ferramentas de código do Visual Studio
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: 41b0eeaeef1c7094fc9c8cbdc05c2db899245fc6
ms.sourcegitcommit: 7e47bf158249050c36d97509eea00e77089a54e6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "49476927"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio-code"></a><span data-ttu-id="84827-104">Criar aplicativos com o Teams Toolkit e o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="84827-104">Build apps with the Teams Toolkit and Visual Studio Code</span></span>

<span data-ttu-id="84827-105">O Microsoft Teams Toolkit permite que você crie aplicativos personalizados do teams diretamente no ambiente de código do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="84827-105">The Microsoft Teams Toolkit enables you to create custom Teams apps directly within the Visual Studio Code environment.</span></span> <span data-ttu-id="84827-106">O kit de ferramentas orienta você durante o processo e oferece tudo o que você precisa para criar, depurar e iniciar o aplicativo Teams.</span><span class="sxs-lookup"><span data-stu-id="84827-106">The toolkit guides you through the process and provides everything you need to build, debug, and launch your Teams app.</span></span>

## <a name="installing-the-teams-toolkit"></a><span data-ttu-id="84827-107">Instalando o Teams Toolkit</span><span class="sxs-lookup"><span data-stu-id="84827-107">Installing the Teams Toolkit</span></span>

<span data-ttu-id="84827-108">O Microsoft Teams Toolkit para Visual Studio Code está disponível para download no [Visual Studio Marketplace](https://aka.ms/teams-toolkit) ou diretamente como uma extensão dentro do Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="84827-108">The Microsoft Teams Toolkit for Visual Studio Code is available for download from the [Visual Studio Marketplace](https://aka.ms/teams-toolkit) or directly as an extension within Visual Studio Code.</span></span>

> [!TIP]
> <span data-ttu-id="84827-109">Após a instalação, você deve ver o Teams Toolkit na barra de atividade de código do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="84827-109">After installation, you should see the Teams Toolkit in the Visual Studio Code activity bar.</span></span> <span data-ttu-id="84827-110">Caso contrário, clique com o botão direito do mouse na barra de atividades e selecione **Microsoft Teams** para fixar o kit de ferramentas para facilitar o acesso.</span><span class="sxs-lookup"><span data-stu-id="84827-110">If not, right-click within the activity bar and select **Microsoft Teams** to pin the toolkit for easy access.</span></span>

## <a name="using-the-toolkit"></a><span data-ttu-id="84827-111">Usando o kit de ferramentas</span><span class="sxs-lookup"><span data-stu-id="84827-111">Using the toolkit</span></span>

- [<span data-ttu-id="84827-112">Configurar um novo projeto</span><span class="sxs-lookup"><span data-stu-id="84827-112">Set up a new project</span></span>](#set-up-a-new-teams-project)
- [<span data-ttu-id="84827-113">Importar um projeto existente</span><span class="sxs-lookup"><span data-stu-id="84827-113">Import an existing project</span></span>](#import-an-existing-teams-app-project)
- [<span data-ttu-id="84827-114">Configurar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="84827-114">Configure your app</span></span>](#configure-your-app)
- [<span data-ttu-id="84827-115">Empacotar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="84827-115">Package your app</span></span>](#package-your-app)
- [<span data-ttu-id="84827-116">Executar o aplicativo localmente ou no Teams</span><span class="sxs-lookup"><span data-stu-id="84827-116">Run your app locally or in Teams</span></span>](#run-your-app)

## <a name="set-up-a-new-teams-project"></a><span data-ttu-id="84827-117">Configurar um novo projeto do teams</span><span class="sxs-lookup"><span data-stu-id="84827-117">Set up a new Teams project</span></span>

1. <span data-ttu-id="84827-118">Crie um espaço de trabalho/pasta para o seu projeto no seu ambiente local.</span><span class="sxs-lookup"><span data-stu-id="84827-118">Create a workspace/folder for your project in your local environment.</span></span>
1. <span data-ttu-id="84827-119">No Visual Studio Code, selecione o ícone Teams</span><span class="sxs-lookup"><span data-stu-id="84827-119">In Visual Studio Code, select the Teams icon</span></span> ![Ícone do Teams](../assets/icons/favicon-16x16.png) <span data-ttu-id="84827-121">na barra de atividades no lado esquerdo da janela.</span><span class="sxs-lookup"><span data-stu-id="84827-121">from the activity bar on the left side of the window.</span></span>
1. <span data-ttu-id="84827-122">Selecione **abrir o Microsoft Teams Toolkit** no menu de comando.</span><span class="sxs-lookup"><span data-stu-id="84827-122">Select **Open the Microsoft Teams Toolkit** from the command menu.</span></span>
1. <span data-ttu-id="84827-123">Selecione **criar um novo aplicativo do teams** no menu de comando.</span><span class="sxs-lookup"><span data-stu-id="84827-123">Select **Create a new Teams app** from the command menu.</span></span>
1. <span data-ttu-id="84827-124">Quando solicitado, insira o nome do espaço de trabalho.</span><span class="sxs-lookup"><span data-stu-id="84827-124">When prompted, enter the name of the workspace .</span></span> <span data-ttu-id="84827-125">Ele será usado como o nome da pasta onde o seu projeto residirá e o nome padrão do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="84827-125">This will be used as both the name of the folder where your project will reside, and the default name of your app.</span></span>
1. <span data-ttu-id="84827-126">Pressione **Enter** e você chegará à tela **Adicionar recursos** para configurar as propriedades do novo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="84827-126">Press **Enter** and you will arrive at the **Add capabilities** screen configure the properties for your new app.</span></span>
1. <span data-ttu-id="84827-127">Selecione o botão **concluir** para concluir o processo de configuração.</span><span class="sxs-lookup"><span data-stu-id="84827-127">Select the **Finish** button to complete the configuration process.</span></span>

## <a name="import-an-existing-teams-app-project"></a><span data-ttu-id="84827-128">Importar um projeto de aplicativo do teams existente</span><span class="sxs-lookup"><span data-stu-id="84827-128">Import an existing Teams app project</span></span>

1. <span data-ttu-id="84827-129">No Visual Studio Code, selecione o ícone Teams</span><span class="sxs-lookup"><span data-stu-id="84827-129">In Visual Studio Code, select the Teams icon</span></span> ![Ícone do Teams](../assets/icons/favicon-16x16.png) <span data-ttu-id="84827-131">na barra de atividades no lado esquerdo da janela.</span><span class="sxs-lookup"><span data-stu-id="84827-131">from the activity bar on the left side of the window.</span></span>
1. <span data-ttu-id="84827-132">Selecione **Importar pacote de aplicativos** no menu de comandos.</span><span class="sxs-lookup"><span data-stu-id="84827-132">Select **Import app package** from the command menu.</span></span>
1. <span data-ttu-id="84827-133">Escolha seu arquivo zip do [pacote de aplicativos do teams](../concepts/build-and-test/apps-package.md) existente.</span><span class="sxs-lookup"><span data-stu-id="84827-133">Choose your existing [Teams app package](../concepts/build-and-test/apps-package.md) zip file.</span></span>
1. <span data-ttu-id="84827-134">Escolha o botão **selecionar pacote de publicação** .</span><span class="sxs-lookup"><span data-stu-id="84827-134">Choose the **Select publishing package** button.</span></span> <span data-ttu-id="84827-135">A guia de configuração do kit de ferramentas deve agora ser preenchida com os detalhes do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="84827-135">The configuration tab of the toolkit should now be populated with your app's details.</span></span>
1. <span data-ttu-id="84827-136">No Visual Studio Code, selecione **arquivo**  ->  **Adicionar pasta ao espaço de trabalho** para adicionar seu diretório de código-fonte ao espaço de trabalho do código do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="84827-136">In Visual Studio Code, select **File** -> **Add Folder to Workspace** to add your source code directory to the Visual Studio Code workspace.</span></span>

## <a name="configure-your-app"></a><span data-ttu-id="84827-137">Configurar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="84827-137">Configure your app</span></span>

<span data-ttu-id="84827-138">Em seu núcleo, o aplicativo Teams engloba três componentes:</span><span class="sxs-lookup"><span data-stu-id="84827-138">At its core, the Teams app embraces three components:</span></span>

  1. <span data-ttu-id="84827-139">O cliente Microsoft Teams (Web, desktop ou celular) onde os usuários interagem com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="84827-139">The Microsoft Teams client (web, desktop or mobile) where users interact with your app.</span></span>
  1. <span data-ttu-id="84827-140">Um servidor que responde às solicitações de conteúdo que será exibido no Microsoft Teams, por exemplo, o conteúdo da guia HTML ou um cartão adaptável de bot.</span><span class="sxs-lookup"><span data-stu-id="84827-140">A server that responds to requests for content that will be displayed in Teams, e.g., HTML tab content or a bot adaptive card .</span></span>
  1. <span data-ttu-id="84827-141">Um [pacote de aplicativos](/concepts/build-and-test/apps-package.md) do teams que consiste em três arquivos:</span><span class="sxs-lookup"><span data-stu-id="84827-141">A Teams [app package](/concepts/build-and-test/apps-package.md) consisting of three files:</span></span>

  > [!div class="checklist"]
  >
  > - <span data-ttu-id="84827-142">O manifest.jsem</span><span class="sxs-lookup"><span data-stu-id="84827-142">The manifest.json</span></span> 
  > - <span data-ttu-id="84827-143">Um [ícone de cor](../resources/schema/manifest-schema.md#icons) para seu aplicativo exibir no catálogo de aplicativos públicos ou de organização</span><span class="sxs-lookup"><span data-stu-id="84827-143">A [color icon](../resources/schema/manifest-schema.md#icons) for your app to display in the public or organization app catalog</span></span>
 > - <span data-ttu-id="84827-144">Um [ícone de estrutura de tópicos](../resources/schema/manifest-schema.md#icons) para exibição na barra de atividades do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="84827-144">An [outline icon](../resources/schema/manifest-schema.md#icons) for display on the Teams activity bar.</span></span>

<span data-ttu-id="84827-145">Quando um aplicativo é instalado, o cliente do teams analisa o arquivo de manifesto para determinar as informações necessárias, como o nome do seu aplicativo e a URL onde os serviços estão localizados.</span><span class="sxs-lookup"><span data-stu-id="84827-145">When an app is installed, the Teams client parses the manifest file to determine needed information like the name of your app and the URL where the services are located.</span></span>

1. <span data-ttu-id="84827-146">Para configurar seu aplicativo, navegue até a guia **Microsoft Teams Toolkit** no Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="84827-146">To configure your app, navigate to the **Microsoft Teams Toolkit** tab in Visual Studio Code.</span></span>
1. <span data-ttu-id="84827-147">Selecione **Editar pacote de aplicativos** para exibir a página de **detalhes do aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="84827-147">Select **Edit app package** to view the **App details** page.</span></span>
1. <span data-ttu-id="84827-148">A edição dos campos na página de detalhes do aplicativo atualiza o conteúdo do manifest.jsem um arquivo que será fornecido como parte do pacote de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="84827-148">Editing the fields in the App details page updates the contents of the manifest.json file that will ultimately ship as part of the app package.</span></span> <span data-ttu-id="84827-149">*Consulte* [Editor de manifesto do App Studio](https://aka.ms/teams-toolkit-manifest)</span><span class="sxs-lookup"><span data-stu-id="84827-149">*See* [App Studio manifest editor](https://aka.ms/teams-toolkit-manifest)</span></span>

## <a name="package-your-app"></a><span data-ttu-id="84827-150">Empacotar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="84827-150">Package your app</span></span>

<span data-ttu-id="84827-151">A modificação da página de **detalhes do aplicativo** ou a atualização do **manifesto** ou arquivos **. env** na pasta do seu aplicativo  **. publish** gerará automaticamente seu arquivo de **Development.zip** .</span><span class="sxs-lookup"><span data-stu-id="84827-151">Modifying the **app details** page or updating the **manifest**, or **.env** files in your app's  **.publish** folder will automatically generate your **Development.zip** file.</span></span> <span data-ttu-id="84827-152">Você precisará incluir [dois ícones](../concepts/build-and-test/apps-package.md#icons) na mesma pasta.</span><span class="sxs-lookup"><span data-stu-id="84827-152">You'll need to include [two icons](../concepts/build-and-test/apps-package.md#icons) in that same folder.</span></span>

## <a name="run-your-app"></a><span data-ttu-id="84827-153">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="84827-153">Run your app</span></span>

### <a name="install-and-run-your-app-locally"></a><span data-ttu-id="84827-154">Instalar e executar o aplicativo localmente</span><span class="sxs-lookup"><span data-stu-id="84827-154">Install and run your app locally</span></span>

<span data-ttu-id="84827-155">Confira o \**Compilar e executar* o conteúdo na página inicial do seu projeto para obter instruções detalhadas sobre como empacotar e testar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="84827-155">Refer to the \**Build and Run* content in your project homepage for detailed instructions on how to package and test your app.</span></span> <span data-ttu-id="84827-156">Em geral, você precisa instalar o servidor do aplicativo, fazê-lo em execução e, em seguida, configurar uma solução de encapsulamento para que o Microsoft Teams possa acessar o conteúdo em execução do localhost.</span><span class="sxs-lookup"><span data-stu-id="84827-156">In general, you need to install your app's server, get it running, then setup a tunneling solution so that Teams can access content running from localhost.</span></span>

### <a name="enable-development-from-localhost"></a><span data-ttu-id="84827-157">Habilitar o desenvolvimento do localhost</span><span class="sxs-lookup"><span data-stu-id="84827-157">Enable development from localhost</span></span>

<span data-ttu-id="84827-158">Se quiser depurar seu aplicativo baseado em guia no localhost usando HTTPS, você precisará informar ao seu navegador para confiar no aplicativo que está sendo servido <https://localhost> .</span><span class="sxs-lookup"><span data-stu-id="84827-158">If you wish to debug your tab based app on localhost using HTTPS, you will need to tell your browser to trust the app being served from <https://localhost>.</span></span> <span data-ttu-id="84827-159">Navegue até <https://localhost:3000/tab>.</span><span class="sxs-lookup"><span data-stu-id="84827-159">Navigate to <https://localhost:3000/tab>.</span></span> <span data-ttu-id="84827-160">Se você vir um aviso indicando que o site não é confiável, escolha a opção para continuar mesmo assim.</span><span class="sxs-lookup"><span data-stu-id="84827-160">If you see a warning indicating that the site isn't trusted, choose the option to proceed anyway.</span></span> <span data-ttu-id="84827-161">Agora, seu aplicativo deve estar acessível no cliente do teams.</span><span class="sxs-lookup"><span data-stu-id="84827-161">Your app should now be accessible from the Teams client.</span></span>

### <a name="run-your-app-in-teams"></a><span data-ttu-id="84827-162">Executar o aplicativo no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="84827-162">Run your app in Teams</span></span>

<span data-ttu-id="84827-163">Pré-requisitos: [habilitar o modo de visualização do desenvolvedor do teams](https://aka.ms/teams-toolkit-enable-devpreview)</span><span class="sxs-lookup"><span data-stu-id="84827-163">Prerequisites: [Enable Teams developer preview mode](https://aka.ms/teams-toolkit-enable-devpreview)</span></span>

1. <span data-ttu-id="84827-164">Navegue até a barra de atividade no lado esquerdo da janela de código do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="84827-164">Navigate to the activity bar on the left side of the Visual Studio Code window.</span></span>
1. <span data-ttu-id="84827-165">Selecione o ícone **executar** para exibir o modo de exibição **executar e depurar** .</span><span class="sxs-lookup"><span data-stu-id="84827-165">Select the **Run** icon to display the **Run and Debug** view.</span></span>
1. <span data-ttu-id="84827-166">Você também pode usar o atalho de teclado `Ctrl+Shift+D` .</span><span class="sxs-lookup"><span data-stu-id="84827-166">You can also use the keyboard shortcut `Ctrl+Shift+D`.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="84827-167">Próxima etapa: manutenção e suporte do seu aplicativo publicado</span><span class="sxs-lookup"><span data-stu-id="84827-167">Next step: Maintaining and supporting your published app</span></span>](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
