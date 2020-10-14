---
title: Introdução-compilar e executar seu primeiro aplicativo
author: heath-hamilton
description: Criar rapidamente um aplicativo do Microsoft Teams que exibe um "Olá, mundo!" mensagem usando o Microsoft Teams Toolkit.
ms.author: lajanuar
ms.date: 10/09/2020
ms.topic: quickstart
ms.openlocfilehash: 20c9eee14649cda23e1d682940f489e78cba24b9
ms.sourcegitcommit: d61f14053fc695bc1956bf50e83956613c19ccca
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/13/2020
ms.locfileid: "48452642"
---
# <a name="build-and-run-your-first-microsoft-teams-app"></a><span data-ttu-id="e1e25-104">Criar e executar seu primeiro aplicativo do Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="e1e25-104">Build and run your first Microsoft Teams app</span></span>

<span data-ttu-id="e1e25-105">Você pode ir direto para o desenvolvimento do Microsoft Teams criando uma guia pessoal que exibe "Olá, mundo!"</span><span class="sxs-lookup"><span data-stu-id="e1e25-105">You can jump right into Microsoft Teams development by building a personal tab that displays "Hello, World!"</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="e1e25-106">1. criar seu projeto de aplicativo</span><span class="sxs-lookup"><span data-stu-id="e1e25-106">1. Create your app project</span></span>

<span data-ttu-id="e1e25-107">Use o Microsoft Teams Toolkit no Visual Studio Code para configurar seu primeiro projeto de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e1e25-107">Use the Microsoft Teams Toolkit in Visual Studio Code to set up your first app project.</span></span>

1. No Visual Studio Code, selecione **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: na barra de atividades à esquerda e escolha **criar um novo aplicativo Teams**.
:::image type="content" source="../assets/images/build-your-first-app/create-teams-app.png" alt-text="Captura de tela mostrando como criar um novo aplicativo com o Visual Studio Code Teams Toolkit.":::
1. <span data-ttu-id="e1e25-110">Insira um nome para seu aplicativo do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="e1e25-110">Enter a name for your Teams app.</span></span> <span data-ttu-id="e1e25-111">(Esse é o nome padrão para seu aplicativo e também o nome do diretório do projeto de aplicativo em sua máquina local.)</span><span class="sxs-lookup"><span data-stu-id="e1e25-111">(This is the default name for your app and also the name of the app project directory on your local machine.)</span></span>
1. <span data-ttu-id="e1e25-112">Na tela **Adicionar recursos** , selecione **Tab** e **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e1e25-112">On the **Add capabilities** screen, select **Tab** then **Next**.</span></span>
:::image type="content" source="../assets/images/build-your-first-app/choose-tab.png" alt-text="Captura de tela mostrando como criar um novo aplicativo com o Visual Studio Code Teams Toolkit.":::
1. <span data-ttu-id="e1e25-114">Verifique a opção de **guia pessoal** e selecione **concluir** na parte inferior da tela para configurar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="e1e25-114">Check the **Personal tab** option and select **Finish** at the bottom of the screen to configure your project.</span></span>

## <a name="2-understand-important-app-project-components"></a><span data-ttu-id="e1e25-115">2. compreender os principais componentes do projeto de aplicativos</span><span class="sxs-lookup"><span data-stu-id="e1e25-115">2. Understand important app project components</span></span>

<span data-ttu-id="e1e25-116">Quando o kit de ferramentas configura seu projeto, você tem os componentes para criar uma guia pessoal básica para o Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="e1e25-116">Once the toolkit configures your project, you have the components to build a basic personal tab for Teams.</span></span> <span data-ttu-id="e1e25-117">Os diretórios e arquivos do projeto são exibidos na área do Explorer do Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="e1e25-117">The project directories and files display in the Explorer area of Visual Studio Code.</span></span>

:::image type="content" source="../assets/images/build-your-first-app/app-project-files.png" alt-text="Captura de tela mostrando como criar um novo aplicativo com o Visual Studio Code Teams Toolkit.":::

<span data-ttu-id="e1e25-119">Vamos reservar alguns momentos para entender alguns dos principais arquivos que os desenvolvedores de aplicativos do teams trabalham.</span><span class="sxs-lookup"><span data-stu-id="e1e25-119">Let's take a moment to understand some of the key files Teams app developers work with.</span></span>

### <a name="app-manifest-manifestjson"></a><span data-ttu-id="e1e25-120">Manifesto do aplicativo ( `manifest.json` )</span><span class="sxs-lookup"><span data-stu-id="e1e25-120">App manifest (`manifest.json`)</span></span>

<span data-ttu-id="e1e25-121">Localizado no `.publish` diretório, o manifesto do aplicativo é o ponto de partida para qualquer projeto de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e1e25-121">Located in the `.publish` directory, the app manifest is the starting point for any app project.</span></span> <span data-ttu-id="e1e25-122">O manifesto define os atributos fundamentais do aplicativo e aponta para os recursos necessários.</span><span class="sxs-lookup"><span data-stu-id="e1e25-122">The manifest defines your app's fundamental attributes and points to required resources.</span></span> <span data-ttu-id="e1e25-123">Quando você instala um aplicativo, o Teams analisa o manifesto para entender como renderizar seu aplicativo no cliente.</span><span class="sxs-lookup"><span data-stu-id="e1e25-123">When you install an app, Teams parses the manifest to understand how to render your app in the client.</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="e1e25-124">Aplicativo scaffolding</span><span class="sxs-lookup"><span data-stu-id="e1e25-124">App scaffolding</span></span>

<span data-ttu-id="e1e25-125">O kit de ferramentas cria automaticamente o scaffolding para você no `src` diretório com base nos recursos adicionados durante a configuração.</span><span class="sxs-lookup"><span data-stu-id="e1e25-125">The toolkit automatically creates scaffolding for you in the `src` directory based on the capabilities you added during setup.</span></span>

<span data-ttu-id="e1e25-126">Se você criar uma guia durante a configuração, por exemplo, o `App.js` arquivo no `src/components` diretório é importante porque trata da inicialização e do roteamento do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e1e25-126">If you create a tab during setup, for example, the `App.js` file in the `src/components` directory is important because it handles the initialization and routing of your app.</span></span> <span data-ttu-id="e1e25-127">Ele chama o [SDK do Microsoft Teams](../tabs/how-to/using-teams-client-sdk.md) para estabelecer a comunicação entre o seu aplicativo e o Teams.</span><span class="sxs-lookup"><span data-stu-id="e1e25-127">It calls the [Microsoft Teams SDK](../tabs/how-to/using-teams-client-sdk.md) to establish communication between your app and Teams.</span></span>

### <a name="app-package-developmentzip"></a><span data-ttu-id="e1e25-128">Pacote de aplicativos ( `Development.zip` )</span><span class="sxs-lookup"><span data-stu-id="e1e25-128">App package (`Development.zip`)</span></span>

<span data-ttu-id="e1e25-129">Localizado no `.publish` diretório, você precisará do pacote de aplicativos para [Sideload seu aplicativo](../concepts/deploy-and-publish/overview.md#upload-your-app-directly) no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="e1e25-129">Located in the `.publish` directory, you need the app package to [sideload your app](../concepts/deploy-and-publish/overview.md#upload-your-app-directly) in Teams.</span></span> <span data-ttu-id="e1e25-130">O pacote também é usado durante [a publicação no catálogo de aplicativos da sua organização](../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) ou no [AppSource](../concepts/deploy-and-publish/appsource/publish.md).</span><span class="sxs-lookup"><span data-stu-id="e1e25-130">The package is also used when [publishing to your organization's app catalog](../concepts/deploy-and-publish/overview.md#publish-to-your-organizations-app-catalog) or [AppSource](../concepts/deploy-and-publish/appsource/publish.md).</span></span>

<span data-ttu-id="e1e25-131">Veja alguns detalhes sobre os arquivos de pacote de aplicativos:</span><span class="sxs-lookup"><span data-stu-id="e1e25-131">Here are some details about the app package files:</span></span>

|<span data-ttu-id="e1e25-132">Nome</span><span class="sxs-lookup"><span data-stu-id="e1e25-132">Name</span></span>|<span data-ttu-id="e1e25-133">Tipo</span><span class="sxs-lookup"><span data-stu-id="e1e25-133">Type</span></span>|<span data-ttu-id="e1e25-134">Size</span><span class="sxs-lookup"><span data-stu-id="e1e25-134">Size</span></span>|<span data-ttu-id="e1e25-135">Local do manifesto</span><span class="sxs-lookup"><span data-stu-id="e1e25-135">Manifest location</span></span>|<span data-ttu-id="e1e25-136">Nome do arquivo de kit</span><span class="sxs-lookup"><span data-stu-id="e1e25-136">Toolkit filename</span></span>|
|---|---|:---:|:---:|-----|
|<span data-ttu-id="e1e25-137">**Manifesto do aplicativo**</span><span class="sxs-lookup"><span data-stu-id="e1e25-137">**App manifest**</span></span>|`.json`| <span data-ttu-id="e1e25-138">—</span><span class="sxs-lookup"><span data-stu-id="e1e25-138">—</span></span> | <span data-ttu-id="e1e25-139">—</span><span class="sxs-lookup"><span data-stu-id="e1e25-139">—</span></span> |`.publish/manifest.json`|
|<span data-ttu-id="e1e25-140">**Logotipo colorido**</span><span class="sxs-lookup"><span data-stu-id="e1e25-140">**Color logo**</span></span>|`.png`|<span data-ttu-id="e1e25-141">192 &times; 192 pixels</span><span class="sxs-lookup"><span data-stu-id="e1e25-141">192&times;192 pixels</span></span>|`icon.color`|`.publish/color.png`|
|<span data-ttu-id="e1e25-142">**Logotipo da estrutura de tópicos**</span><span class="sxs-lookup"><span data-stu-id="e1e25-142">**Outline logo**</span></span>|`.png`|<span data-ttu-id="e1e25-143">32 &times; 32 pixels</span><span class="sxs-lookup"><span data-stu-id="e1e25-143">32&times;32 pixels</span></span>|`icon.outline`|`.publish/outline.png`|

## <a name="3-run-your-app"></a><span data-ttu-id="e1e25-144">3. Execute seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="e1e25-144">3. Run your app</span></span>

<span data-ttu-id="e1e25-145">Nos juros de tempo, você criará e executará seu aplicativo localmente.</span><span class="sxs-lookup"><span data-stu-id="e1e25-145">In the interest of time, you'll build and run your app locally.</span></span>

<span data-ttu-id="e1e25-146">(Essas informações também estão disponíveis no kit de ferramentas `README` .)</span><span class="sxs-lookup"><span data-stu-id="e1e25-146">(This information is also available in the toolkit `README`.)</span></span>

1. <span data-ttu-id="e1e25-147">Em um terminal, vá para o diretório raiz do seu projeto de aplicativo e execute `npm install` .</span><span class="sxs-lookup"><span data-stu-id="e1e25-147">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="e1e25-148">Executar `npm start` .</span><span class="sxs-lookup"><span data-stu-id="e1e25-148">Run `npm start`.</span></span> <span data-ttu-id="e1e25-149">Após a conclusão, há uma **compilação bem-sucedida!**</span><span class="sxs-lookup"><span data-stu-id="e1e25-149">Once complete, there's a **Compiled successfully!**</span></span> <span data-ttu-id="e1e25-150">mensagem no terminal.</span><span class="sxs-lookup"><span data-stu-id="e1e25-150">message in the terminal.</span></span>
1. <span data-ttu-id="e1e25-151">Abra um navegador e vá para `https://localhost:3000` para exibir uma página da Web em branco chamada **Guia do Microsoft Teams**. (Não se preocupe se você não consegue ver conteúdo na página.)</span><span class="sxs-lookup"><span data-stu-id="e1e25-151">Open a browser and go to `https://localhost:3000` to view a blank webpage called **Microsoft Teams Tab**. (Don't worry that you can't see any content on the page.)</span></span><br/>
   :::image type="content" source="../assets/images/build-your-first-app/local-host-tab.png" alt-text="Captura de tela mostrando como criar um novo aplicativo com o Visual Studio Code Teams Toolkit.":::

## <a name="4-set-up-a-secure-tunnel-to-your-app"></a><span data-ttu-id="e1e25-153">4. configurar um túnel seguro para seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="e1e25-153">4. Set up a secure tunnel to your app</span></span>

<span data-ttu-id="e1e25-154">Seu aplicativo está em execução no servidor Web local.</span><span class="sxs-lookup"><span data-stu-id="e1e25-154">Your app is up and running on your local web server.</span></span> <span data-ttu-id="e1e25-155">Para executar seu aplicativo no Teams, você deve tornar seu `localhost` acessível por meio de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e1e25-155">To run your app in Teams, you must make your `localhost` accessible through HTTPS.</span></span>

<span data-ttu-id="e1e25-156">Instale o [ngrok](https://ngrok.com/download) se ainda não tiver feito isso.</span><span class="sxs-lookup"><span data-stu-id="e1e25-156">Install [ngrok](https://ngrok.com/download) if you haven't already.</span></span> <span data-ttu-id="e1e25-157">Ao executar essa ferramenta, você cria duas URLs disponíveis globalmente que apontam para o servidor Web local ( `http://localhost:3000` ).</span><span class="sxs-lookup"><span data-stu-id="e1e25-157">When you run this tool, you create two globally available URLs that point to your local web server (`http://localhost:3000`).</span></span> <span data-ttu-id="e1e25-158">Você precisa da URL de encaminhamento que começa com `HTTPS` .</span><span class="sxs-lookup"><span data-stu-id="e1e25-158">You need the forwarding URL that begins with `HTTPS`.</span></span>

1. <span data-ttu-id="e1e25-159">Abra um novo terminal e execute `ngrok http 3000` .</span><span class="sxs-lookup"><span data-stu-id="e1e25-159">Open a new terminal and run `ngrok http 3000`.</span></span>
1. <span data-ttu-id="e1e25-160">Copie a URL HTTPS que você está vendo (Confira o exemplo a seguir).</span><span class="sxs-lookup"><span data-stu-id="e1e25-160">Copy the HTTPS URL you're provided (see the following example).</span></span>
:::image type="content" source="../assets/images/build-your-first-app/ngrok-running.png" alt-text="Captura de tela mostrando como criar um novo aplicativo com o Visual Studio Code Teams Toolkit.":::
1. <span data-ttu-id="e1e25-162">Em seu `.publish` diretório, abra `Development.env` .</span><span class="sxs-lookup"><span data-stu-id="e1e25-162">In your `.publish` directory, open `Development.env`.</span></span>
1. <span data-ttu-id="e1e25-163">Substitua o `baseUrl0` valor pela URL copiada.</span><span class="sxs-lookup"><span data-stu-id="e1e25-163">Replace the `baseUrl0` value with the copied URL.</span></span> <span data-ttu-id="e1e25-164">(Por exemplo, alterar `baseUrl0=http://localhost:3000` para `baseUrl0=https://85528b2b3ba5.ngrok.io` .)</span><span class="sxs-lookup"><span data-stu-id="e1e25-164">(For example, change `baseUrl0=http://localhost:3000` to `baseUrl0=https://85528b2b3ba5.ngrok.io`.)</span></span>

<span data-ttu-id="e1e25-165">O manifesto do aplicativo agora aponta para onde você está hospedando o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e1e25-165">Your app manifest now points to where you're hosting the app.</span></span>

## <a name="5-sideload-your-app-in-teams"></a><span data-ttu-id="e1e25-166">5. Sideload seu aplicativo no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="e1e25-166">5. Sideload your app in Teams</span></span>

<span data-ttu-id="e1e25-167">Com o aplicativo em execução e acessível via HTTPS, você está pronto para carregá-lo no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="e1e25-167">With your app running and accessible via HTTPS, you're ready to upload it to Teams.</span></span>

> [!TIP]
> <span data-ttu-id="e1e25-168">Antes de fazer o Sideload do aplicativo, verifique se há problemas usando o [recurso de validação do kit de ferramentas](../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool).</span><span class="sxs-lookup"><span data-stu-id="e1e25-168">Before sideloading your app, check for issues using the [toolkit's validation feature](../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md#teams-app-validation-tool).</span></span> <span data-ttu-id="e1e25-169">Os erros devem ser corrigidos para Sideload com êxito o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e1e25-169">Errors must be fixed to successfully sideload the app.</span></span>

1. <span data-ttu-id="e1e25-170">Faça logon no cliente do teams com sua conta que permita o aplicativo Sideload.</span><span class="sxs-lookup"><span data-stu-id="e1e25-170">Log in to the Teams client with your account that allows app sideloading.</span></span> <span data-ttu-id="e1e25-171">(Se você não tiver certeza de que tem isso, saiba mais sobre como obter uma [conta de desenvolvimento do teams](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account).)</span><span class="sxs-lookup"><span data-stu-id="e1e25-171">(If you aren't sure you have that, learn about getting a [Teams development account](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account).)</span></span>
1. <span data-ttu-id="e1e25-172">Selecione **aplicativos**e, em seguida, escolha **carregar um aplicativo personalizado**.</span><span class="sxs-lookup"><span data-stu-id="e1e25-172">Select **Apps**, then choose **Upload a custom app**.</span></span>
1. <span data-ttu-id="e1e25-173">Vá para a pasta do projeto de aplicativo `.publish` e selecione `Development.zip` .</span><span class="sxs-lookup"><span data-stu-id="e1e25-173">Go to your app project `.publish` folder and select `Development.zip`.</span></span> <span data-ttu-id="e1e25-174">Uma janela restrita de instalação é exibida.</span><span class="sxs-lookup"><span data-stu-id="e1e25-174">An installation modal displays.</span></span>
:::image type="content" source="../assets/images/build-your-first-app/add-teams-app.png" alt-text="Captura de tela mostrando como criar um novo aplicativo com o Visual Studio Code Teams Toolkit.":::
1. <span data-ttu-id="e1e25-176">Selecione **Adicionar** para instalar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e1e25-176">Select **Add** to install your app.</span></span>
:::image type="content" source="../assets/images/build-your-first-app/tab-running.png" alt-text="Captura de tela mostrando como criar um novo aplicativo com o Visual Studio Code Teams Toolkit.":::

<span data-ttu-id="e1e25-178">🎉 Parabéns!</span><span class="sxs-lookup"><span data-stu-id="e1e25-178">🎉 Congratulations!</span></span> <span data-ttu-id="e1e25-179">Seu aplicativo está em execução no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="e1e25-179">Your app is running in Teams.</span></span>

## <a name="next-step"></a><span data-ttu-id="e1e25-180">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="e1e25-180">Next step</span></span>

<span data-ttu-id="e1e25-181">Expanda na guia pessoal que você acabou de criar ou criar outro tipo de aplicativo do teams.</span><span class="sxs-lookup"><span data-stu-id="e1e25-181">Expand on the personal tab you just created or build another type of Teams app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e1e25-182">Adicionar à sua guia pessoal</span><span class="sxs-lookup"><span data-stu-id="e1e25-182">Add to your personal tab</span></span>](../build-your-first-app/build-personal-tab.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="e1e25-183">Construir uma guia de canal</span><span class="sxs-lookup"><span data-stu-id="e1e25-183">Build a channel tab</span></span>](../build-your-first-app/build-channel-tab.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="e1e25-184">Construir um bot</span><span class="sxs-lookup"><span data-stu-id="e1e25-184">Build a bot</span></span>](../build-your-first-app/build-bot.md)
