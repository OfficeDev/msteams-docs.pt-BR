---
title: Introdução-compilar e executar seu primeiro aplicativo
author: heath-hamilton
description: Criar rapidamente um aplicativo do Microsoft Teams que exibe um "Olá, mundo!" mensagem usando o Microsoft Teams Toolkit.
ms.author: lajanuar
ms.date: 11/03/2020
ms.topic: quickstart
ms.openlocfilehash: 62c4bd950183ceb64fb30b528661cf84e9210d89
ms.sourcegitcommit: 99c35de7e2c604bd8bce392242c2c2fa709cd50b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/06/2020
ms.locfileid: "48931770"
---
# <a name="build-and-run-your-first-microsoft-teams-app"></a><span data-ttu-id="ceacc-104">Criar e executar seu primeiro aplicativo do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="ceacc-104">Build and run your first Microsoft Teams app</span></span>

<span data-ttu-id="ceacc-105">Você pode ir direto para o desenvolvimento do Microsoft Teams criando uma guia pessoal que exibe "Olá, mundo!"</span><span class="sxs-lookup"><span data-stu-id="ceacc-105">You can jump right into Microsoft Teams development by building a personal tab that displays "Hello, World!"</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="ceacc-106">1. criar seu projeto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="ceacc-106">1. Create your app project</span></span>

<span data-ttu-id="ceacc-107">Use o Microsoft Teams Toolkit no Visual Studio Code para configurar seu primeiro projeto de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ceacc-107">Use the Microsoft Teams Toolkit in Visual Studio Code to set up your first app project.</span></span>

1. No Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na barra de atividades à esquerda e escolha **criar um novo aplicativo Teams**.
1. <span data-ttu-id="ceacc-109">Quando solicitado, entre com sua conta de desenvolvimento do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="ceacc-109">When prompted, sign in with your Microsoft 365 development account.</span></span>
1. <span data-ttu-id="ceacc-110">Na tela **Adicionar recursos** , selecione **Tab** e **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="ceacc-110">On the **Add capabilities** screen, select **Tab** then **Next**.</span></span>
:::image type="content" source="../assets/images/build-your-first-app/choose-tab.png" alt-text="Captura de tela mostrando como configurar seu projeto de aplicativo com o Visual Studio Code Teams Toolkit.":::
1. <span data-ttu-id="ceacc-112">Insira um nome para seu aplicativo do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="ceacc-112">Enter a name for your Teams app.</span></span> <span data-ttu-id="ceacc-113">(Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto de aplicativo em sua máquina local.)</span><span class="sxs-lookup"><span data-stu-id="ceacc-113">(This is the default name for your app and also the name of the app project directory on your local machine.)</span></span>
1. <span data-ttu-id="ceacc-114">Marque somente a opção **guia pessoal** e selecione **concluir** na parte inferior da tela para configurar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="ceacc-114">Check only the **Personal tab** option and select **Finish** at the bottom of the screen to configure your project.</span></span>

## <a name="2-understand-important-app-project-components"></a><span data-ttu-id="ceacc-115">2. compreender os principais componentes do projeto de aplicativos</span><span class="sxs-lookup"><span data-stu-id="ceacc-115">2. Understand important app project components</span></span>

<span data-ttu-id="ceacc-116">Quando o kit de ferramentas configura seu projeto, você tem os componentes para criar uma guia pessoal básica para o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="ceacc-116">Once the toolkit configures your project, you have the components to build a basic personal tab for Teams.</span></span> <span data-ttu-id="ceacc-117">Os diretórios e arquivos do projeto são exibidos na área do Explorer do Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="ceacc-117">The project directories and files display in the Explorer area of Visual Studio Code.</span></span>

:::image type="content" source="../assets/images/build-your-first-app/app-project-files.png" alt-text="Captura de tela mostrando arquivos de projeto de aplicativo para uma guia pessoal no Visual Studio Code.":::

### <a name="app-scaffolding"></a><span data-ttu-id="ceacc-119">Aplicativo scaffolding</span><span class="sxs-lookup"><span data-stu-id="ceacc-119">App scaffolding</span></span>

<span data-ttu-id="ceacc-120">O kit de ferramentas cria automaticamente o scaffolding para você no `src` diretório com base nos recursos adicionados durante a configuração.</span><span class="sxs-lookup"><span data-stu-id="ceacc-120">The toolkit automatically creates scaffolding for you in the `src` directory based on the capabilities you added during setup.</span></span>

<span data-ttu-id="ceacc-121">Se você criar uma guia durante a configuração, por exemplo, o `App.js` arquivo no `src/components` diretório é importante porque trata da inicialização e do roteamento do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ceacc-121">If you create a tab during setup, for example, the `App.js` file in the `src/components` directory is important because it handles the initialization and routing of your app.</span></span> <span data-ttu-id="ceacc-122">Ele chama o [SDK do Microsoft Teams](../tabs/how-to/using-teams-client-sdk.md) para estabelecer a comunicação entre o seu aplicativo e o Teams.</span><span class="sxs-lookup"><span data-stu-id="ceacc-122">It calls the [Microsoft Teams SDK](../tabs/how-to/using-teams-client-sdk.md) to establish communication between your app and Teams.</span></span>

### <a name="app-id"></a><span data-ttu-id="ceacc-123">ID do aplicativo</span><span class="sxs-lookup"><span data-stu-id="ceacc-123">App ID</span></span>

<span data-ttu-id="ceacc-124">Sua ID de aplicativo do Microsoft Teams é necessária para configurar seu aplicativo com o app Studio.</span><span class="sxs-lookup"><span data-stu-id="ceacc-124">Your Teams app ID is needed to configure your app with App Studio.</span></span> <span data-ttu-id="ceacc-125">Você pode encontrar a ID no `teamsAppId` objeto, localizada no arquivo do seu projeto `package.json` .</span><span class="sxs-lookup"><span data-stu-id="ceacc-125">You can find the ID in the `teamsAppId` object, which is located in your project's `package.json` file.</span></span>

## <a name="3-build-and-run-your-app"></a><span data-ttu-id="ceacc-126">3. Compilar e executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="ceacc-126">3. Build and run your app</span></span>

<span data-ttu-id="ceacc-127">Nos juros de tempo, você criará e executará seu aplicativo localmente.</span><span class="sxs-lookup"><span data-stu-id="ceacc-127">In the interest of time, you'll build and run your app locally.</span></span>

<span data-ttu-id="ceacc-128">(Essas informações também estão disponíveis no kit de ferramentas `README` .)</span><span class="sxs-lookup"><span data-stu-id="ceacc-128">(This information is also available in the toolkit `README`.)</span></span>

1. <span data-ttu-id="ceacc-129">Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e execute `npm install` .</span><span class="sxs-lookup"><span data-stu-id="ceacc-129">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="ceacc-130">Executar `npm start` .</span><span class="sxs-lookup"><span data-stu-id="ceacc-130">Run `npm start`.</span></span>

<span data-ttu-id="ceacc-131">Após a conclusão, há uma **compilação bem-sucedida!**</span><span class="sxs-lookup"><span data-stu-id="ceacc-131">Once complete, there's a **Compiled successfully!**</span></span> <span data-ttu-id="ceacc-132">mensagem no terminal.</span><span class="sxs-lookup"><span data-stu-id="ceacc-132">message in the terminal.</span></span> <span data-ttu-id="ceacc-133">O aplicativo está sendo executado `https://localhost:3000` .</span><span class="sxs-lookup"><span data-stu-id="ceacc-133">Your app is running on `https://localhost:3000`.</span></span>

## <a name="4-sideload-your-app-in-teams"></a><span data-ttu-id="ceacc-134">4. Sideload seu aplicativo no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="ceacc-134">4. Sideload your app in Teams</span></span>

<span data-ttu-id="ceacc-135">Seu aplicativo está pronto para teste no Teams.</span><span class="sxs-lookup"><span data-stu-id="ceacc-135">Your app is ready to test in Teams.</span></span> <span data-ttu-id="ceacc-136">Para fazer isso, você deve ter uma conta que permita o aplicativo Sideload.</span><span class="sxs-lookup"><span data-stu-id="ceacc-136">To do this, you must have an account that allows app sideloading.</span></span> <span data-ttu-id="ceacc-137">(Se você não tiver certeza de que tem isso, saiba mais sobre como obter uma [conta de desenvolvimento do teams](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account).)</span><span class="sxs-lookup"><span data-stu-id="ceacc-137">(If you aren't sure you have that, learn about getting a [Teams development account](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account).)</span></span>

> [!TIP]
> <span data-ttu-id="ceacc-138">Antes de fazer o Sideload do aplicativo, verifique se há problemas usando o [recurso de validação no app Studio](../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool), que está incluído no kit de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="ceacc-138">Before sideloading your app, check for issues using the [validation feature in App Studio](../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool), which is included in the toolkit.</span></span> <span data-ttu-id="ceacc-139">Os erros devem ser corrigidos para Sideload com êxito o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ceacc-139">Errors must be fixed to successfully sideload the app.</span></span>

1. <span data-ttu-id="ceacc-140">No Visual Studio Code, pressione a tecla **F5** para iniciar um cliente Web do teams.</span><span class="sxs-lookup"><span data-stu-id="ceacc-140">In Visual Studio Code, press the **F5** key to launch a Teams web client.</span></span>
1. <span data-ttu-id="ceacc-141">Para exibir o conteúdo do aplicativo no Teams, especifique o local em que o aplicativo está em execução ( `localhost` ) é confiável:</span><span class="sxs-lookup"><span data-stu-id="ceacc-141">To display your app content in Teams, specify that where your app is running (`localhost`) is trustworthy:</span></span>
   1. <span data-ttu-id="ceacc-142">Abra uma nova guia na mesma janela do navegador (Google Chrome por padrão), aberta após pressionar **F5**.</span><span class="sxs-lookup"><span data-stu-id="ceacc-142">Open a new tab in the same browser window (Google Chrome by default) which opened after pressing **F5**.</span></span>
   1. <span data-ttu-id="ceacc-143">Vá até `https://localhost:3000/tab` a página e vá até ela.</span><span class="sxs-lookup"><span data-stu-id="ceacc-143">Go to `https://localhost:3000/tab` and proceed to the page.</span></span>
1. <span data-ttu-id="ceacc-144">Volte para o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="ceacc-144">Go back to Teams.</span></span> <span data-ttu-id="ceacc-145">Na caixa de diálogo, selecione **Adicionar para mim** para instalar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ceacc-145">In the dialog, select **Add for me** to install your app.</span></span>
:::image type="content" source="../assets/images/build-your-first-app/tab-running.png" alt-text="Captura de tela mostrando um exemplo de aplicativo de guia pessoal _OL_QUOTE_PLACEHOLDER_Olá, mundo!_OL_QUOTE_PLACEHOLDER_ executado no Teams.":::

<span data-ttu-id="ceacc-147">🎉 Parabéns!</span><span class="sxs-lookup"><span data-stu-id="ceacc-147">🎉 Congratulations!</span></span> <span data-ttu-id="ceacc-148">Seu aplicativo está em execução no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="ceacc-148">Your app is running in Teams.</span></span>

## <a name="next-step"></a><span data-ttu-id="ceacc-149">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="ceacc-149">Next step</span></span>

<span data-ttu-id="ceacc-150">Expanda na guia pessoal que você acabou de criar ou criar outro tipo de aplicativo do teams.</span><span class="sxs-lookup"><span data-stu-id="ceacc-150">Expand on the personal tab you just created or build another type of Teams app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ceacc-151">Adicionar à sua guia pessoal</span><span class="sxs-lookup"><span data-stu-id="ceacc-151">Add to your personal tab</span></span>](../build-your-first-app/build-personal-tab.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="ceacc-152">Construir uma guia de canal</span><span class="sxs-lookup"><span data-stu-id="ceacc-152">Build a channel tab</span></span>](../build-your-first-app/build-channel-tab.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="ceacc-153">Construir um bot</span><span class="sxs-lookup"><span data-stu-id="ceacc-153">Build a bot</span></span>](../build-your-first-app/build-bot.md)
