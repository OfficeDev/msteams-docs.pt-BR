---
title: Começar - Criar e executar seu primeiro aplicativo
author: heath-hamilton
description: Crie rapidamente um aplicativo do Microsoft Teams que exibe um "Hello, World!" usando o Kit de Ferramentas do Microsoft Teams.
ms.author: lajanuar
ms.date: 11/03/2020
ms.topic: quickstart
ms.openlocfilehash: bc5d18dd887cbdbf56b8d6d013f53c21d1540370
ms.sourcegitcommit: 5687a901d48bcf2f5a3a086e0f703f854e8b9c21
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2021
ms.locfileid: "49795465"
---
# <a name="build-and-run-your-first-microsoft-teams-app"></a><span data-ttu-id="19032-104">Criar e executar seu primeiro aplicativo Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="19032-104">Build and run your first Microsoft Teams app</span></span>

<span data-ttu-id="19032-105">Você pode entrar no desenvolvimento do Microsoft Teams criando uma guia pessoal que exibe "Hello, World!"</span><span class="sxs-lookup"><span data-stu-id="19032-105">You can jump right into Microsoft Teams development by building a personal tab that displays "Hello, World!"</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="19032-106">1. Criar seu projeto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="19032-106">1. Create your app project</span></span>

<span data-ttu-id="19032-107">Use o Kit de Ferramentas do Microsoft Teams no Visual Studio Code para configurar seu primeiro projeto de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="19032-107">Use the Microsoft Teams Toolkit in Visual Studio Code to set up your first app project.</span></span>

1. No Visual Studio Code, selecione **o Microsoft Teams** na Barra de Atividades à esquerda e escolha Criar um novo aplicativo do :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: **Teams.**
1. <span data-ttu-id="19032-109">Quando solicitado, entre com sua conta de desenvolvimento do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="19032-109">When prompted, sign in with your Microsoft 365 development account.</span></span>
1. <span data-ttu-id="19032-110">Na tela **Adicionar recursos,** selecione **Tab** e **Next.**</span><span class="sxs-lookup"><span data-stu-id="19032-110">On the **Add capabilities** screen, select **Tab** then **Next**.</span></span>
:::image type="content" source="../assets/images/build-your-first-app/choose-tab.png" alt-text="Screenshot showing how to configure your app project with the Visual Studio Code Teams Toolkit.":::
1. <span data-ttu-id="19032-112">Insira um nome para seu aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="19032-112">Enter a name for your Teams app.</span></span> <span data-ttu-id="19032-113">(Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto do aplicativo em seu computador local.)</span><span class="sxs-lookup"><span data-stu-id="19032-113">(This is the default name for your app and also the name of the app project directory on your local machine.)</span></span>
1. <span data-ttu-id="19032-114">Marque somente a **opção de guia** Pessoal e selecione **Concluir** na parte inferior da tela para configurar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="19032-114">Check only the **Personal tab** option and select **Finish** at the bottom of the screen to configure your project.</span></span>

## <a name="2-understand-important-app-project-components"></a><span data-ttu-id="19032-115">2. Compreender componentes importantes do projeto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="19032-115">2. Understand important app project components</span></span>

<span data-ttu-id="19032-116">Depois que o kit de ferramentas configurar seu projeto, você terá os componentes para criar uma guia pessoal básica para o Teams.</span><span class="sxs-lookup"><span data-stu-id="19032-116">Once the toolkit configures your project, you have the components to build a basic personal tab for Teams.</span></span> <span data-ttu-id="19032-117">Os diretórios e arquivos do projeto são exibidos na área Explorer do Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="19032-117">The project directories and files display in the Explorer area of Visual Studio Code.</span></span>

:::image type="content" source="../assets/images/build-your-first-app/app-project-files.png" alt-text="Captura de tela mostrando arquivos de projeto do aplicativo para uma guia pessoal no Visual Studio Code.":::

### <a name="app-scaffolding"></a><span data-ttu-id="19032-119">Scaffolding de aplicativos</span><span class="sxs-lookup"><span data-stu-id="19032-119">App scaffolding</span></span>

<span data-ttu-id="19032-120">O kit de ferramentas cria automaticamente o scaffolding para você no `src` diretório com base nos recursos adicionados durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="19032-120">The toolkit automatically creates scaffolding for you in the `src` directory based on the capabilities you added during setup.</span></span>

<span data-ttu-id="19032-121">Se você criar uma guia durante a instalação, por exemplo, o arquivo no diretório é importante porque ele lida com a inicialização e o roteamento `App.js` `src/components` do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="19032-121">If you create a tab during setup, for example, the `App.js` file in the `src/components` directory is important because it handles the initialization and routing of your app.</span></span> <span data-ttu-id="19032-122">Ele chama o [SDK](../tabs/how-to/using-teams-client-sdk.md) do cliente JavaScript do Microsoft Teams para estabelecer a comunicação entre seu aplicativo e o Teams.</span><span class="sxs-lookup"><span data-stu-id="19032-122">It calls the [Microsoft Teams JavaScript client SDK](../tabs/how-to/using-teams-client-sdk.md) to establish communication between your app and Teams.</span></span>

### <a name="app-id"></a><span data-ttu-id="19032-123">ID do aplicativo</span><span class="sxs-lookup"><span data-stu-id="19032-123">App ID</span></span>

<span data-ttu-id="19032-124">Sua ID de aplicativo do Teams é necessária para configurar seu aplicativo com o App Studio.</span><span class="sxs-lookup"><span data-stu-id="19032-124">Your Teams app ID is needed to configure your app with App Studio.</span></span> <span data-ttu-id="19032-125">Você pode encontrar a ID no `teamsAppId` objeto, que está localizado no arquivo do `package.json` projeto.</span><span class="sxs-lookup"><span data-stu-id="19032-125">You can find the ID in the `teamsAppId` object, which is located in your project's `package.json` file.</span></span>

## <a name="3-build-and-run-your-app"></a><span data-ttu-id="19032-126">3. Crie e execute seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="19032-126">3. Build and run your app</span></span>

<span data-ttu-id="19032-127">No interesse de tempo, você criará e executará seu aplicativo localmente.</span><span class="sxs-lookup"><span data-stu-id="19032-127">In the interest of time, you'll build and run your app locally.</span></span>

<span data-ttu-id="19032-128">(Essas informações também estão disponíveis no kit de `README` ferramentas.)</span><span class="sxs-lookup"><span data-stu-id="19032-128">(This information is also available in the toolkit `README`.)</span></span>

1. <span data-ttu-id="19032-129">Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e `npm install` execute.</span><span class="sxs-lookup"><span data-stu-id="19032-129">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="19032-130">Executar `npm start` .</span><span class="sxs-lookup"><span data-stu-id="19032-130">Run `npm start`.</span></span>

<span data-ttu-id="19032-131">Depois de concluído, há um **compilado com êxito!**</span><span class="sxs-lookup"><span data-stu-id="19032-131">Once complete, there's a **Compiled successfully!**</span></span> <span data-ttu-id="19032-132">no terminal.</span><span class="sxs-lookup"><span data-stu-id="19032-132">message in the terminal.</span></span> <span data-ttu-id="19032-133">Seu aplicativo está em `https://localhost:3000` execução.</span><span class="sxs-lookup"><span data-stu-id="19032-133">Your app is running on `https://localhost:3000`.</span></span>

## <a name="4-sideload-your-app-in-teams"></a><span data-ttu-id="19032-134">4. Fazer sideload do aplicativo no Teams</span><span class="sxs-lookup"><span data-stu-id="19032-134">4. Sideload your app in Teams</span></span>

<span data-ttu-id="19032-135">Seu aplicativo está pronto para ser testado no Teams.</span><span class="sxs-lookup"><span data-stu-id="19032-135">Your app is ready to test in Teams.</span></span> <span data-ttu-id="19032-136">Para fazer isso, você deve ter uma conta que permita o sideload do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="19032-136">To do this, you must have an account that allows app sideloading.</span></span> <span data-ttu-id="19032-137">(Se você não tiver certeza de que tem isso, saiba mais sobre como obter uma conta [de desenvolvimento do Teams.)](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account)</span><span class="sxs-lookup"><span data-stu-id="19032-137">(If you aren't sure you have that, learn about getting a [Teams development account](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account).)</span></span>

> [!TIP]
> <span data-ttu-id="19032-138">Antes de fazer o sideload do aplicativo, verifique se há problemas usando o recurso de validação no [App Studio](../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool), que está incluído no kit de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="19032-138">Before sideloading your app, check for issues using the [validation feature in App Studio](../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool), which is included in the toolkit.</span></span> <span data-ttu-id="19032-139">Os erros devem ser corrigidos para fazer o sideload do aplicativo com êxito.</span><span class="sxs-lookup"><span data-stu-id="19032-139">Errors must be fixed to successfully sideload the app.</span></span>

1. <span data-ttu-id="19032-140">No Visual Studio Code, pressione a **tecla F5** para iniciar um cliente Web do Teams.</span><span class="sxs-lookup"><span data-stu-id="19032-140">In Visual Studio Code, press the **F5** key to launch a Teams web client.</span></span>
1. <span data-ttu-id="19032-141">Para exibir o conteúdo do aplicativo no Teams, especifique que onde o aplicativo está sendo executado ( `localhost` ) é confiável:</span><span class="sxs-lookup"><span data-stu-id="19032-141">To display your app content in Teams, specify that where your app is running (`localhost`) is trustworthy:</span></span>
   1. <span data-ttu-id="19032-142">Abra uma nova guia na mesma janela do navegador (Google Chrome por padrão) que foi aberta após pressionar **F5**.</span><span class="sxs-lookup"><span data-stu-id="19032-142">Open a new tab in the same browser window (Google Chrome by default) which opened after pressing **F5**.</span></span>
   1. <span data-ttu-id="19032-143">Vá para `https://localhost:3000/tab` a página e prossiga para a página.</span><span class="sxs-lookup"><span data-stu-id="19032-143">Go to `https://localhost:3000/tab` and proceed to the page.</span></span>
1. <span data-ttu-id="19032-144">Volte para o Teams.</span><span class="sxs-lookup"><span data-stu-id="19032-144">Go back to Teams.</span></span> <span data-ttu-id="19032-145">Na caixa de diálogo, selecione **Adicionar para instalar** seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="19032-145">In the dialog, select **Add for me** to install your app.</span></span>
:::image type="content" source="../assets/images/build-your-first-app/tab-running.png" alt-text="Screenshot showing an example 'Hello, World!' personal tab app running in Teams.":::

<span data-ttu-id="19032-147">🎉 parabéns!</span><span class="sxs-lookup"><span data-stu-id="19032-147">🎉 Congratulations!</span></span> <span data-ttu-id="19032-148">Seu aplicativo está sendo executado no Teams.</span><span class="sxs-lookup"><span data-stu-id="19032-148">Your app is running in Teams.</span></span>

## <a name="next-step"></a><span data-ttu-id="19032-149">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="19032-149">Next step</span></span>

<span data-ttu-id="19032-150">Expanda a guia pessoal que você acabou de criar ou criar outro tipo de aplicativo do Teams.</span><span class="sxs-lookup"><span data-stu-id="19032-150">Expand on the personal tab you just created or build another type of Teams app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="19032-151">Adicionar à sua guia pessoal</span><span class="sxs-lookup"><span data-stu-id="19032-151">Add to your personal tab</span></span>](../build-your-first-app/build-personal-tab.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="19032-152">Construir uma guia de canal</span><span class="sxs-lookup"><span data-stu-id="19032-152">Build a channel tab</span></span>](../build-your-first-app/build-channel-tab.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="19032-153">Construir um bot</span><span class="sxs-lookup"><span data-stu-id="19032-153">Build a bot</span></span>](../build-your-first-app/build-bot.md)
