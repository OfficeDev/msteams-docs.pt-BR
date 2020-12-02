---
title: Introdução-compilar e executar seu primeiro aplicativo
author: heath-hamilton
description: Criar rapidamente um aplicativo do Microsoft Teams que exibe um "Olá, mundo!" mensagem usando o Microsoft Teams Toolkit.
ms.author: lajanuar
ms.date: 11/03/2020
ms.topic: quickstart
ms.openlocfilehash: 2d357ef71bfc4c498b54d94f9d0717cf886df17d
ms.sourcegitcommit: bfdcd122b6b4ffc52d92320d4741f870c07f0542
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2020
ms.locfileid: "49552476"
---
# <a name="build-and-run-your-first-microsoft-teams-app"></a><span data-ttu-id="8bf51-104">Criar e executar seu primeiro aplicativo do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="8bf51-104">Build and run your first Microsoft Teams app</span></span>

<span data-ttu-id="8bf51-105">Você pode ir direto para o desenvolvimento do Microsoft Teams criando uma guia pessoal que exibe "Olá, mundo!"</span><span class="sxs-lookup"><span data-stu-id="8bf51-105">You can jump right into Microsoft Teams development by building a personal tab that displays "Hello, World!"</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="8bf51-106">1. criar seu projeto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="8bf51-106">1. Create your app project</span></span>

<span data-ttu-id="8bf51-107">Use o Microsoft Teams Toolkit no Visual Studio Code para configurar seu primeiro projeto de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8bf51-107">Use the Microsoft Teams Toolkit in Visual Studio Code to set up your first app project.</span></span>

1. No Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na barra de atividades à esquerda e escolha **criar um novo aplicativo Teams**.
1. <span data-ttu-id="8bf51-109">Quando solicitado, entre com sua conta de desenvolvimento do Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="8bf51-109">When prompted, sign in with your Microsoft 365 development account.</span></span>
1. <span data-ttu-id="8bf51-110">Na tela **Adicionar recursos** , selecione **Tab** e **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="8bf51-110">On the **Add capabilities** screen, select **Tab** then **Next**.</span></span>
:::image type="content" source="../assets/images/build-your-first-app/choose-tab.png" alt-text="Captura de tela mostrando como configurar seu projeto de aplicativo com o Visual Studio Code Teams Toolkit.":::
1. <span data-ttu-id="8bf51-112">Insira um nome para seu aplicativo do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="8bf51-112">Enter a name for your Teams app.</span></span> <span data-ttu-id="8bf51-113">(Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto de aplicativo em sua máquina local.)</span><span class="sxs-lookup"><span data-stu-id="8bf51-113">(This is the default name for your app and also the name of the app project directory on your local machine.)</span></span>
1. <span data-ttu-id="8bf51-114">Marque somente a opção **guia pessoal** e selecione **concluir** na parte inferior da tela para configurar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="8bf51-114">Check only the **Personal tab** option and select **Finish** at the bottom of the screen to configure your project.</span></span>

> [!NOTE]

> <span data-ttu-id="8bf51-115">Para instalar o pacote do aplicativo depois de criar um novo projeto no kit de ferramentas, pressione F5/executar.</span><span class="sxs-lookup"><span data-stu-id="8bf51-115">To install your app package after creating a new project in the toolkit, press F5/run.</span></span> <span data-ttu-id="8bf51-116">Ele iniciará o Chrome e instalará seu pacote.</span><span class="sxs-lookup"><span data-stu-id="8bf51-116">It will launch Chrome and install your package.</span></span> <span data-ttu-id="8bf51-117">O pacote é armazenado no app Studio e instalado usando o `appId` .</span><span class="sxs-lookup"><span data-stu-id="8bf51-117">The package is stored in App Studio and installed using the `appId`.</span></span>

## <a name="2-understand-important-app-project-components"></a><span data-ttu-id="8bf51-118">2. compreender os principais componentes do projeto de aplicativos</span><span class="sxs-lookup"><span data-stu-id="8bf51-118">2. Understand important app project components</span></span>

<span data-ttu-id="8bf51-119">Quando o kit de ferramentas configura seu projeto, você tem os componentes para criar uma guia pessoal básica para o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="8bf51-119">Once the toolkit configures your project, you have the components to build a basic personal tab for Teams.</span></span> <span data-ttu-id="8bf51-120">Os diretórios e arquivos do projeto são exibidos na área do Explorer do Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="8bf51-120">The project directories and files display in the Explorer area of Visual Studio Code.</span></span>

:::image type="content" source="../assets/images/build-your-first-app/app-project-files.png" alt-text="Captura de tela mostrando arquivos de projeto de aplicativo para uma guia pessoal no Visual Studio Code.":::

### <a name="app-scaffolding"></a><span data-ttu-id="8bf51-122">Aplicativo scaffolding</span><span class="sxs-lookup"><span data-stu-id="8bf51-122">App scaffolding</span></span>

<span data-ttu-id="8bf51-123">O kit de ferramentas cria automaticamente o scaffolding para você no `src` diretório com base nos recursos adicionados durante a configuração.</span><span class="sxs-lookup"><span data-stu-id="8bf51-123">The toolkit automatically creates scaffolding for you in the `src` directory based on the capabilities you added during setup.</span></span>

<span data-ttu-id="8bf51-124">Se você criar uma guia durante a configuração, por exemplo, o `App.js` arquivo no `src/components` diretório é importante porque trata da inicialização e do roteamento do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8bf51-124">If you create a tab during setup, for example, the `App.js` file in the `src/components` directory is important because it handles the initialization and routing of your app.</span></span> <span data-ttu-id="8bf51-125">Ele chama o [SDK do Microsoft Teams](../tabs/how-to/using-teams-client-sdk.md) para estabelecer a comunicação entre o seu aplicativo e o Teams.</span><span class="sxs-lookup"><span data-stu-id="8bf51-125">It calls the [Microsoft Teams SDK](../tabs/how-to/using-teams-client-sdk.md) to establish communication between your app and Teams.</span></span>

### <a name="app-id"></a><span data-ttu-id="8bf51-126">ID do aplicativo</span><span class="sxs-lookup"><span data-stu-id="8bf51-126">App ID</span></span>

<span data-ttu-id="8bf51-127">Sua ID de aplicativo do Microsoft Teams é necessária para configurar seu aplicativo com o app Studio.</span><span class="sxs-lookup"><span data-stu-id="8bf51-127">Your Teams app ID is needed to configure your app with App Studio.</span></span> <span data-ttu-id="8bf51-128">Você pode encontrar a ID no `teamsAppId` objeto, localizada no arquivo do seu projeto `package.json` .</span><span class="sxs-lookup"><span data-stu-id="8bf51-128">You can find the ID in the `teamsAppId` object, which is located in your project's `package.json` file.</span></span>

## <a name="3-build-and-run-your-app"></a><span data-ttu-id="8bf51-129">3. Compilar e executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="8bf51-129">3. Build and run your app</span></span>

<span data-ttu-id="8bf51-130">Nos juros de tempo, você criará e executará seu aplicativo localmente.</span><span class="sxs-lookup"><span data-stu-id="8bf51-130">In the interest of time, you'll build and run your app locally.</span></span>

<span data-ttu-id="8bf51-131">(Essas informações também estão disponíveis no kit de ferramentas `README` .)</span><span class="sxs-lookup"><span data-stu-id="8bf51-131">(This information is also available in the toolkit `README`.)</span></span>

1. <span data-ttu-id="8bf51-132">Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e execute `npm install` .</span><span class="sxs-lookup"><span data-stu-id="8bf51-132">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="8bf51-133">Executar `npm start` .</span><span class="sxs-lookup"><span data-stu-id="8bf51-133">Run `npm start`.</span></span>

<span data-ttu-id="8bf51-134">Após a conclusão, há uma **compilação bem-sucedida!**</span><span class="sxs-lookup"><span data-stu-id="8bf51-134">Once complete, there's a **Compiled successfully!**</span></span> <span data-ttu-id="8bf51-135">mensagem no terminal.</span><span class="sxs-lookup"><span data-stu-id="8bf51-135">message in the terminal.</span></span> <span data-ttu-id="8bf51-136">O aplicativo está sendo executado `https://localhost:3000` .</span><span class="sxs-lookup"><span data-stu-id="8bf51-136">Your app is running on `https://localhost:3000`.</span></span>

## <a name="4-sideload-your-app-in-teams"></a><span data-ttu-id="8bf51-137">4. Sideload seu aplicativo no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="8bf51-137">4. Sideload your app in Teams</span></span>

<span data-ttu-id="8bf51-138">Seu aplicativo está pronto para teste no Teams.</span><span class="sxs-lookup"><span data-stu-id="8bf51-138">Your app is ready to test in Teams.</span></span> <span data-ttu-id="8bf51-139">Para fazer isso, você deve ter uma conta que permita o aplicativo Sideload.</span><span class="sxs-lookup"><span data-stu-id="8bf51-139">To do this, you must have an account that allows app sideloading.</span></span> <span data-ttu-id="8bf51-140">(Se você não tiver certeza de que tem isso, saiba mais sobre como obter uma [conta de desenvolvimento do teams](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account).)</span><span class="sxs-lookup"><span data-stu-id="8bf51-140">(If you aren't sure you have that, learn about getting a [Teams development account](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account).)</span></span>

> [!TIP]
> <span data-ttu-id="8bf51-141">Antes de fazer o Sideload do aplicativo, verifique se há problemas usando o [recurso de validação no app Studio](../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool), que está incluído no kit de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="8bf51-141">Before sideloading your app, check for issues using the [validation feature in App Studio](../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool), which is included in the toolkit.</span></span> <span data-ttu-id="8bf51-142">Os erros devem ser corrigidos para Sideload com êxito o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8bf51-142">Errors must be fixed to successfully sideload the app.</span></span>

1. <span data-ttu-id="8bf51-143">No Visual Studio Code, pressione a tecla **F5** para iniciar um cliente Web do teams.</span><span class="sxs-lookup"><span data-stu-id="8bf51-143">In Visual Studio Code, press the **F5** key to launch a Teams web client.</span></span>
1. <span data-ttu-id="8bf51-144">Para exibir o conteúdo do aplicativo no Teams, especifique o local em que o aplicativo está em execução ( `localhost` ) é confiável:</span><span class="sxs-lookup"><span data-stu-id="8bf51-144">To display your app content in Teams, specify that where your app is running (`localhost`) is trustworthy:</span></span>
   1. <span data-ttu-id="8bf51-145">Abra uma nova guia na mesma janela do navegador (Google Chrome por padrão), aberta após pressionar **F5**.</span><span class="sxs-lookup"><span data-stu-id="8bf51-145">Open a new tab in the same browser window (Google Chrome by default) which opened after pressing **F5**.</span></span>
   1. <span data-ttu-id="8bf51-146">Vá até `https://localhost:3000/tab` a página e vá até ela.</span><span class="sxs-lookup"><span data-stu-id="8bf51-146">Go to `https://localhost:3000/tab` and proceed to the page.</span></span>
1. <span data-ttu-id="8bf51-147">Volte para o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="8bf51-147">Go back to Teams.</span></span> <span data-ttu-id="8bf51-148">Na caixa de diálogo, selecione **Adicionar para mim** para instalar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8bf51-148">In the dialog, select **Add for me** to install your app.</span></span>
:::image type="content" source="../assets/images/build-your-first-app/tab-running.png" alt-text="Captura de tela mostrando um exemplo de aplicativo de guia pessoal &quot;Olá, mundo!&quot; executado no Teams.":::

<span data-ttu-id="8bf51-150">🎉 Parabéns!</span><span class="sxs-lookup"><span data-stu-id="8bf51-150">🎉 Congratulations!</span></span> <span data-ttu-id="8bf51-151">Seu aplicativo está em execução no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="8bf51-151">Your app is running in Teams.</span></span>

## <a name="next-step"></a><span data-ttu-id="8bf51-152">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="8bf51-152">Next step</span></span>

<span data-ttu-id="8bf51-153">Expanda na guia pessoal que você acabou de criar ou criar outro tipo de aplicativo do teams.</span><span class="sxs-lookup"><span data-stu-id="8bf51-153">Expand on the personal tab you just created or build another type of Teams app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8bf51-154">Adicionar à sua guia pessoal</span><span class="sxs-lookup"><span data-stu-id="8bf51-154">Add to your personal tab</span></span>](../build-your-first-app/build-personal-tab.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="8bf51-155">Construir uma guia de canal</span><span class="sxs-lookup"><span data-stu-id="8bf51-155">Build a channel tab</span></span>](../build-your-first-app/build-channel-tab.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="8bf51-156">Construir um bot</span><span class="sxs-lookup"><span data-stu-id="8bf51-156">Build a bot</span></span>](../build-your-first-app/build-bot.md)
