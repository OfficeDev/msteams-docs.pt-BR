---
title: Começar - Criar e executar seu primeiro aplicativo
author: heath-hamilton
description: Crie rapidamente um aplicativo do Microsoft Teams que exibe um "Hello, World!" usando a mensagem do Microsoft Teams Toolkit.
ms.author: lajanuar
localization_priority: Normal
ms.date: 11/03/2020
ms.topic: quickstart
ms.openlocfilehash: 1b34c3f3121e834abc8a8a92a8a0ac9a049c9e07
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020881"
---
# <a name="build-and-run-your-first-microsoft-teams-app"></a><span data-ttu-id="ea2e9-104">Criar e executar seu primeiro aplicativo do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="ea2e9-104">Build and run your first Microsoft Teams app</span></span>

<span data-ttu-id="ea2e9-105">Inicie o desenvolvimento do Microsoft Teams criando uma guia pessoal que exibe "Hello, World!".</span><span class="sxs-lookup"><span data-stu-id="ea2e9-105">Start Microsoft Teams development by building a personal tab that displays "Hello, World!".</span></span>
<span data-ttu-id="ea2e9-106">Crie e execute seu primeiro aplicativo do Teams usando as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="ea2e9-106">Build and run your first Teams app using the following steps:</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="ea2e9-107">1. Crie seu projeto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="ea2e9-107">1. Create your app project</span></span>

<span data-ttu-id="ea2e9-108">Use o Microsoft Teams Toolkit código Visual Studio para configurar seu primeiro projeto de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea2e9-108">Use the Microsoft Teams Toolkit in Visual Studio Code to set up your first app project.</span></span> <span data-ttu-id="ea2e9-109">Crie seu projeto de aplicativo usando as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="ea2e9-109">Create your app project using the following steps:</span></span>

1. Em Visual Studio Código, selecione **Microsoft Teams** na Barra de Atividades à esquerda e escolha Criar um novo aplicativo do :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: **Teams.**
1. <span data-ttu-id="ea2e9-111">Quando solicitado, entre com sua conta de desenvolvimento do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="ea2e9-111">When prompted, sign in with your Microsoft 365 development account.</span></span>
1. <span data-ttu-id="ea2e9-112">Na tela **Adicionar recursos,** selecione **Tab** e **Next**.</span><span class="sxs-lookup"><span data-stu-id="ea2e9-112">On the **Add capabilities** screen, select **Tab** then **Next**.</span></span>
:::image type="content" source="../assets/images/build-your-first-app/choose-tab.png" alt-text="Captura de tela mostrando como configurar seu projeto de aplicativo com o Visual Studio Code Teams Toolkit.":::
1. <span data-ttu-id="ea2e9-114">Insira um nome para seu aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="ea2e9-114">Enter a name for your Teams app.</span></span> <span data-ttu-id="ea2e9-115">(Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto do aplicativo em sua máquina local.)</span><span class="sxs-lookup"><span data-stu-id="ea2e9-115">(This is the default name for your app and also the name of the app project directory on your local machine.)</span></span>
1. <span data-ttu-id="ea2e9-116">Marque apenas a **opção Guia Pessoal** e selecione **Concluir** na parte inferior da tela para configurar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="ea2e9-116">Check only the **Personal tab** option and select **Finish** at the bottom of the screen to configure your project.</span></span>

## <a name="2-understand-important-app-project-components"></a><span data-ttu-id="ea2e9-117">2. Entenda componentes importantes do projeto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="ea2e9-117">2. Understand important app project components</span></span>

<span data-ttu-id="ea2e9-118">Depois que o kit de ferramentas configurar seu projeto, você terá os componentes para criar uma guia pessoal básica para o Teams.</span><span class="sxs-lookup"><span data-stu-id="ea2e9-118">Once the toolkit configures your project, you have the components to build a basic personal tab for Teams.</span></span> <span data-ttu-id="ea2e9-119">Os diretórios e arquivos do projeto são exibidos na área Explorer do Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="ea2e9-119">The project directories and files display in the Explorer area of Visual Studio Code.</span></span>

:::image type="content" source="../assets/images/build-your-first-app/app-project-files.png" alt-text="Captura de tela mostrando arquivos de projeto de aplicativo para uma guia pessoal Visual Studio Code.":::

### <a name="app-scaffolding"></a><span data-ttu-id="ea2e9-121">Scaffolding de aplicativos</span><span class="sxs-lookup"><span data-stu-id="ea2e9-121">App scaffolding</span></span>

<span data-ttu-id="ea2e9-122">O kit de ferramentas cria automaticamente o scaffolding para você no `src` diretório com base nos recursos adicionados durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="ea2e9-122">The toolkit automatically creates scaffolding for you in the `src` directory based on the capabilities you added during setup.</span></span>

<span data-ttu-id="ea2e9-123">Se você criar uma guia durante a instalação, por exemplo, o arquivo no diretório será importante porque ele lida com a inicialização e o `App.js` `src/components` roteamento do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea2e9-123">If you create a tab during setup, for example, the `App.js` file in the `src/components` directory is important because it handles the initialization and routing of your app.</span></span> <span data-ttu-id="ea2e9-124">Ele chama o [SDK](../tabs/how-to/using-teams-client-sdk.md) do cliente JavaScript do Microsoft Teams para estabelecer comunicação entre seu aplicativo e o Teams.</span><span class="sxs-lookup"><span data-stu-id="ea2e9-124">It calls the [Microsoft Teams JavaScript client SDK](../tabs/how-to/using-teams-client-sdk.md) to establish communication between your app and Teams.</span></span>

### <a name="app-id"></a><span data-ttu-id="ea2e9-125">ID do aplicativo</span><span class="sxs-lookup"><span data-stu-id="ea2e9-125">App ID</span></span>

<span data-ttu-id="ea2e9-126">Configure seu aplicativo com o App Studio usando a ID do aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="ea2e9-126">Configure your app with App Studio using the Teams app ID.</span></span> <span data-ttu-id="ea2e9-127">Encontre a ID no `teamsAppId` objeto, que está localizado no arquivo do seu `package.json` projeto.</span><span class="sxs-lookup"><span data-stu-id="ea2e9-127">Find the ID in the `teamsAppId` object, which is located in your project's `package.json` file.</span></span>

## <a name="3-build-and-run-your-app"></a><span data-ttu-id="ea2e9-128">3. Crie e execute seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="ea2e9-128">3. Build and run your app</span></span>

<span data-ttu-id="ea2e9-129">Crie e execute seu aplicativo localmente para economizar tempo.</span><span class="sxs-lookup"><span data-stu-id="ea2e9-129">Build and run your app locally to save time.</span></span> <span data-ttu-id="ea2e9-130">Essas informações também estão disponíveis no kit de ferramentas `README` .</span><span class="sxs-lookup"><span data-stu-id="ea2e9-130">This information is also available in the toolkit `README`.</span></span> <span data-ttu-id="ea2e9-131">Crie e execute seu aplicativo usando as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="ea2e9-131">Build and run your app using the following steps:</span></span>

1. <span data-ttu-id="ea2e9-132">Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e execute `npm install` .</span><span class="sxs-lookup"><span data-stu-id="ea2e9-132">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="ea2e9-133">Executar `npm start` .</span><span class="sxs-lookup"><span data-stu-id="ea2e9-133">Run `npm start`.</span></span>

<span data-ttu-id="ea2e9-134">Depois de concluído, há um **Compilado com êxito!**</span><span class="sxs-lookup"><span data-stu-id="ea2e9-134">Once complete, there's a **Compiled successfully!**</span></span> <span data-ttu-id="ea2e9-135">mensagem no terminal.</span><span class="sxs-lookup"><span data-stu-id="ea2e9-135">message in the terminal.</span></span> <span data-ttu-id="ea2e9-136">Seu aplicativo está sendo executado em `https://localhost:3000` .</span><span class="sxs-lookup"><span data-stu-id="ea2e9-136">Your app is running on `https://localhost:3000`.</span></span>

## <a name="4-sideload-your-app-in-teams"></a><span data-ttu-id="ea2e9-137">4. Fazer sideload do aplicativo no Teams</span><span class="sxs-lookup"><span data-stu-id="ea2e9-137">4. Sideload your app in Teams</span></span>

<span data-ttu-id="ea2e9-138">Seu aplicativo está pronto para teste no Teams.</span><span class="sxs-lookup"><span data-stu-id="ea2e9-138">Your app is ready to test in Teams.</span></span> <span data-ttu-id="ea2e9-139">Para fazer isso, você deve ter uma conta de desenvolvimento do Microsoft 365 que permita o sideload de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="ea2e9-139">To do this, you must have a Microsoft 365 development account that allows app sideloading.</span></span> <span data-ttu-id="ea2e9-140">Para obter mais informações sobre a abertura da conta, consulte [Conta de desenvolvimento do Teams.](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account)</span><span class="sxs-lookup"><span data-stu-id="ea2e9-140">For more information on account opening, see [Teams development account](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account).</span></span> 

> [!TIP]
> <span data-ttu-id="ea2e9-141">Verifique se há problemas antes de fazer sideload do aplicativo, usando o recurso de validação no [App Studio](../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool), que está incluído no kit de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="ea2e9-141">Check for issues before sideloading your app, using the [validation feature in App Studio](../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool), which is included in the toolkit.</span></span> <span data-ttu-id="ea2e9-142">Correção dos erros para fazer sideload com êxito do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea2e9-142">Fix the errors to successfully sideload the app.</span></span>

<span data-ttu-id="ea2e9-143">Fazer sideload do aplicativo no Teams usando as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="ea2e9-143">Sideload your app in Teams using the following steps:</span></span>

> [!NOTE]
> <span data-ttu-id="ea2e9-144">Para habilitar o sideload antes de fazer sideload do aplicativo no Teams, siga as etapas em [Ativar o sideload do aplicativo.](../concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading)</span><span class="sxs-lookup"><span data-stu-id="ea2e9-144">To enable sideloading before you sideload your app in Teams, follow the steps in [Turn on app sideloading](../concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading).</span></span>

1. <span data-ttu-id="ea2e9-145">Selecione a **chave F5** para iniciar um cliente Web do Teams Visual Studio Código.</span><span class="sxs-lookup"><span data-stu-id="ea2e9-145">Select the **F5** key to launch a Teams web client in Visual Studio Code.</span></span>
1. <span data-ttu-id="ea2e9-146">Para exibir o conteúdo do aplicativo no Teams, especifique que onde seu aplicativo está sendo executado ( `localhost` ) é confiável:</span><span class="sxs-lookup"><span data-stu-id="ea2e9-146">To display your app content in Teams, specify that where your app is running (`localhost`) is trustworthy:</span></span>
   1. <span data-ttu-id="ea2e9-147">Abra uma nova guia na mesma janela do navegador (Google Chrome por padrão) que foi aberta após pressionar **F5**.</span><span class="sxs-lookup"><span data-stu-id="ea2e9-147">Open a new tab in the same browser window (Google Chrome by default) which opened after pressing **F5**.</span></span>
   1. <span data-ttu-id="ea2e9-148">Vá para `https://localhost:3000/tab` e prossiga para a página.</span><span class="sxs-lookup"><span data-stu-id="ea2e9-148">Go to `https://localhost:3000/tab` and proceed to the page.</span></span>
1. <span data-ttu-id="ea2e9-149">Volte para o Teams.</span><span class="sxs-lookup"><span data-stu-id="ea2e9-149">Go back to Teams.</span></span> <span data-ttu-id="ea2e9-150">Na caixa de diálogo, selecione **Adicionar para que eu** instale seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea2e9-150">In the dialog, select **Add for me** to install your app.</span></span>
:::image type="content" source="../assets/images/build-your-first-app/tab-running.png" alt-text="Captura de tela mostrando um exemplo de aplicativo de guia pessoal &quot;Hello, World!&quot; em execução no Teams.":::

<span data-ttu-id="ea2e9-152">🎉 parabéns!</span><span class="sxs-lookup"><span data-stu-id="ea2e9-152">🎉 Congratulations!</span></span> <span data-ttu-id="ea2e9-153">Seu aplicativo está sendo executado no Teams.</span><span class="sxs-lookup"><span data-stu-id="ea2e9-153">Your app is running in Teams.</span></span>

## <a name="next-step"></a><span data-ttu-id="ea2e9-154">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="ea2e9-154">Next step</span></span>

<span data-ttu-id="ea2e9-155">Expanda na guia pessoal que você acabou de criar ou criar outro tipo de aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="ea2e9-155">Expand on the personal tab you just created or build another type of Teams app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ea2e9-156">Adicionar à sua guia pessoal</span><span class="sxs-lookup"><span data-stu-id="ea2e9-156">Add to your personal tab</span></span>](../build-your-first-app/build-personal-tab.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="ea2e9-157">Construir uma guia de canal</span><span class="sxs-lookup"><span data-stu-id="ea2e9-157">Build a channel tab</span></span>](../build-your-first-app/build-channel-tab.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="ea2e9-158">Construir um bot</span><span class="sxs-lookup"><span data-stu-id="ea2e9-158">Build a bot</span></span>](../build-your-first-app/build-bot.md)
