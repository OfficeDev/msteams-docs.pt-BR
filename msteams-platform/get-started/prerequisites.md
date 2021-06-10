---
title: Começar - Pré-requisitos
author: adrianhall
description: Saiba como começar com o desenvolvimento Microsoft Teams aplicativo e configurar seu ambiente.
ms.author: adhal
ms.date: 05/24/2021
ms.topic: quickstart
ms.openlocfilehash: 73d99f2bbbc69bf13242110a56e13e662655283c
ms.sourcegitcommit: 9cabeaed9baf96c8caeb1497f0bc37abdb787d22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2021
ms.locfileid: "52646609"
---
# <a name="prerequisites-get-started-with-microsoft-teams-app-development"></a><span data-ttu-id="e80e4-103">Pré-requisitos: começar a Microsoft Teams desenvolvimento de aplicativos</span><span class="sxs-lookup"><span data-stu-id="e80e4-103">Prerequisites: Get started with Microsoft Teams app development</span></span>

<span data-ttu-id="e80e4-104">Antes de criar seu primeiro Teams, você deve instalar algumas ferramentas e configurar seu ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="e80e4-104">Before your create your first Teams app, you must install a few tools and set up your development environment.</span></span>

## <a name="install-required-tools"></a><span data-ttu-id="e80e4-105">Instalar ferramentas necessárias</span><span class="sxs-lookup"><span data-stu-id="e80e4-105">Install required tools</span></span>

<span data-ttu-id="e80e4-106">Algumas das ferramentas de que você precisa dependem de como você prefere criar seu Teams aplicativo:</span><span class="sxs-lookup"><span data-stu-id="e80e4-106">Some of the tools you need depend on how you you prefer to build your Teams app:</span></span>

- <span data-ttu-id="e80e4-107">[Node.js](https://nodejs.org/en/download/) (use a versão mais recente do v14 LTS)</span><span class="sxs-lookup"><span data-stu-id="e80e4-107">[Node.js](https://nodejs.org/en/download/) (use the latest v14 LTS release)</span></span> 
- <span data-ttu-id="e80e4-108">Um navegador com ferramentas de desenvolvedor - como [Microsoft Edge](https://www.microsoft.com/edge) (recomendado) ou [Google Chrome](https://www.google.com/chrome/)</span><span class="sxs-lookup"><span data-stu-id="e80e4-108">A browser with developer tools - such as [Microsoft Edge](https://www.microsoft.com/edge) (recommended) or [Google Chrome](https://www.google.com/chrome/)</span></span>
- <span data-ttu-id="e80e4-109">Se você estiver desenvolvendo com JavaScript, TypeScript ou o Estrutura do SharePoint (SPFx), instale o [Visual Studio Code](https://code.visualstudio.com/download), versão 1.55 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="e80e4-109">If you're developing with JavaScript, TypeScript, or the SharePoint Framework (SPFx), install [Visual Studio Code](https://code.visualstudio.com/download), version 1.55 or later.</span></span>  
- <span data-ttu-id="e80e4-110">Se você estiver desenvolvendo com o .NET, instale o Visual Studio [2019](https://visualstudio.com/download).</span><span class="sxs-lookup"><span data-stu-id="e80e4-110">If you're developing with .NET, install [Visual Studio 2019](https://visualstudio.com/download).</span></span>  <span data-ttu-id="e80e4-111">Certifique-se de instalar o **ASP.NET e desenvolvimento da Web** ou a carga de trabalho de desenvolvimento entre **plataformas do .NET Core.**</span><span class="sxs-lookup"><span data-stu-id="e80e4-111">Ensure you install the **ASP.NET and web development** or **.NET Core cross-platform development** workload.</span></span>

> [!WARNING]
> <span data-ttu-id="e80e4-112">Há problemas conhecidos com `npm@7` , empacotado com o Nó v15 e posterior.</span><span class="sxs-lookup"><span data-stu-id="e80e4-112">There are known issues with `npm@7`, packaged with Node v15 and later.</span></span> <span data-ttu-id="e80e4-113">Se você tiver problemas em `npm install` execução, verifique se está usando o Nó v14 (LTS)</span><span class="sxs-lookup"><span data-stu-id="e80e4-113">If you have problems running `npm install`, ensure you're using Node v14 (LTS)</span></span>

## <a name="install-the-teams-toolkit"></a><span data-ttu-id="e80e4-114">Instalar o Teams Toolkit</span><span class="sxs-lookup"><span data-stu-id="e80e4-114">Install the Teams Toolkit</span></span>

<span data-ttu-id="e80e4-115">O Teams Toolkit ajuda a simplificar o processo de desenvolvimento com ferramentas para provisionar e implantar recursos de nuvem para seu aplicativo, publicar no Teams store e muito mais.</span><span class="sxs-lookup"><span data-stu-id="e80e4-115">The Teams Toolkit helps simplify the development process with tools to provision and deploy cloud resources for your app, publish to the Teams store, and more.</span></span> <span data-ttu-id="e80e4-116">Você pode usar o kit de ferramentas com Visual Studio Code, Visual Studio ou como uma CLI (chamada `teamsfx` ).</span><span class="sxs-lookup"><span data-stu-id="e80e4-116">You can use the toolkit with Visual Studio Code, Visual Studio, or as a CLI (called `teamsfx`).</span></span>

# <a name="visual-studio-code"></a>[<span data-ttu-id="e80e4-117">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e80e4-117">Visual Studio Code</span></span>](#tab/vscode)

1. <span data-ttu-id="e80e4-118">Abra o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="e80e4-118">Open Visual Studio Code.</span></span>
1. <span data-ttu-id="e80e4-119">Selecione o exibição Extensões (**Ctrl+Shift+X**  /  **⌘⇧-X** ou **Exibir > Extensões).**</span><span class="sxs-lookup"><span data-stu-id="e80e4-119">Select the Extensions view (**Ctrl+Shift+X** / **⌘⇧-X** or **View > Extensions**).</span></span>
1. <span data-ttu-id="e80e4-120">Na caixa de pesquisa, digite _Teams Toolkit_.</span><span class="sxs-lookup"><span data-stu-id="e80e4-120">In the search box, enter _Teams Toolkit_.</span></span>
1. <span data-ttu-id="e80e4-121">Selecione no botão de instalação verde ao lado do Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="e80e4-121">Select on the green install button next to the Teams Toolkit.</span></span>

<span data-ttu-id="e80e4-122">Você também pode encontrar o Teams Toolkit no [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).</span><span class="sxs-lookup"><span data-stu-id="e80e4-122">You also can find the Teams Toolkit on the [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).</span></span>

<span data-ttu-id="e80e4-123">As ferramentas a seguir serão instaladas pela extensão Visual Studio Code quando elas são necessárias.</span><span class="sxs-lookup"><span data-stu-id="e80e4-123">The following tools will be installed by the Visual Studio Code extension when they are needed.</span></span>  <span data-ttu-id="e80e4-124">Se já estiver instalada, a versão instalada será usada em vez disso.</span><span class="sxs-lookup"><span data-stu-id="e80e4-124">If already installed, the installed version will be used instead.</span></span>  <span data-ttu-id="e80e4-125">Se estiver usando o Linux (incluindo o WSL), você deve instalar essas ferramentas antes de usar:</span><span class="sxs-lookup"><span data-stu-id="e80e4-125">If using Linux (including WSL), you must install these tools before use:</span></span>

- [<span data-ttu-id="e80e4-126">Ferramentas principais das funções do Azure</span><span class="sxs-lookup"><span data-stu-id="e80e4-126">Azure Functions Core Tools</span></span>](/azure/azure-functions/functions-run-local)

    <span data-ttu-id="e80e4-127">As Ferramentas Principais de Funções do Azure são usadas para executar qualquer componente back-end localmente durante uma execução de depuração local, incluindo os auxiliares de autenticação necessários ao executar seus serviços no Azure.</span><span class="sxs-lookup"><span data-stu-id="e80e4-127">Azure Functions Core Tools is used to run any backend components locally during a local debug run, including the authentication helpers required when running your services in Azure.</span></span>  <span data-ttu-id="e80e4-128">Ele é instalado no diretório do projeto (usando o npm `devDependencies` ).</span><span class="sxs-lookup"><span data-stu-id="e80e4-128">It is installed within the project directory (using the npm `devDependencies`).</span></span>

- [<span data-ttu-id="e80e4-129">.NET SDK</span><span class="sxs-lookup"><span data-stu-id="e80e4-129">.NET SDK</span></span>](/dotnet/core/install/)

    <span data-ttu-id="e80e4-130">O .NET SDK é usado para instalar vinculações personalizadas para implantações de aplicativos de depuração local e funções do Azure.</span><span class="sxs-lookup"><span data-stu-id="e80e4-130">The .NET SDK is used to install customized bindings for local debugging and Azure Functions app deployments.</span></span>  <span data-ttu-id="e80e4-131">Se você não tiver instalado o SDK .NET 3.1 (ou posterior) globalmente, a versão portátil será instalada.</span><span class="sxs-lookup"><span data-stu-id="e80e4-131">If you have not installed the .NET 3.1 (or later) SDK globally, the portable version will be installed.</span></span>

- [<span data-ttu-id="e80e4-132">ngrok</span><span class="sxs-lookup"><span data-stu-id="e80e4-132">ngrok</span></span>](https://ngrok.com/download)

    <span data-ttu-id="e80e4-133">Alguns Teams de aplicativo (bots de conversação, extensões de mensagens e webhooks de entrada) exigem conexões de entrada.</span><span class="sxs-lookup"><span data-stu-id="e80e4-133">Some Teams app features (conversational bots, messaging extensions, and incoming webhooks) require inbound connections.</span></span>  <span data-ttu-id="e80e4-134">Você precisa expor seu sistema de desenvolvimento para Teams através de um túnel.</span><span class="sxs-lookup"><span data-stu-id="e80e4-134">You need to expose your development system to Teams through a tunnel.</span></span>  <span data-ttu-id="e80e4-135">Um túnel não é necessário para aplicativos que incluem apenas guias.</span><span class="sxs-lookup"><span data-stu-id="e80e4-135">A tunnel is not required for apps that only include tabs.</span></span>  <span data-ttu-id="e80e4-136">Este pacote é instalado no diretório do projeto (usando npm `devDependencies` ).</span><span class="sxs-lookup"><span data-stu-id="e80e4-136">This package is installed within the project directory (using npm `devDependencies`).</span></span>

# <a name="visual-studio-2019"></a>[<span data-ttu-id="e80e4-137">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="e80e4-137">Visual Studio 2019</span></span>](#tab/vs)

<span data-ttu-id="e80e4-138">Você pode usar o Visual Studio 2019 para desenvolver Teams aplicativos com o Blazor Server no .NET.</span><span class="sxs-lookup"><span data-stu-id="e80e4-138">You can use Visual Studio 2019 to develop Teams apps with Blazor Server in .NET.</span></span>  <span data-ttu-id="e80e4-139">Se você não pretende desenvolver Teams aplicativos no .NET, instale Visual Studio Code versão do Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="e80e4-139">If you're not intending to develop Teams apps in .NET, install the Visual Studio Code version of Teams Toolkit.</span></span>

<span data-ttu-id="e80e4-140">Para instalar a extensão Teams Toolkit:</span><span class="sxs-lookup"><span data-stu-id="e80e4-140">To install the Teams Toolkit extension:</span></span>

1. <span data-ttu-id="e80e4-141">Abra Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="e80e4-141">Open Visual Studio 2019.</span></span>
1. <span data-ttu-id="e80e4-142">Selecione **Extensões**  >  **Gerenciar Extensões**.</span><span class="sxs-lookup"><span data-stu-id="e80e4-142">Select **Extensions** > **Manage Extensions**.</span></span>
1. <span data-ttu-id="e80e4-143">Na caixa de pesquisa, digite _Teams Toolkit_.</span><span class="sxs-lookup"><span data-stu-id="e80e4-143">In the search box, enter _Teams Toolkit_.</span></span>
1. <span data-ttu-id="e80e4-144">Selecione a Teams Toolkit e selecione **Baixar**.</span><span class="sxs-lookup"><span data-stu-id="e80e4-144">Select the Teams Toolkit extension and select **Download**.</span></span>

<span data-ttu-id="e80e4-145">A extensão será baixada.</span><span class="sxs-lookup"><span data-stu-id="e80e4-145">The extension will be downloaded.</span></span>  <span data-ttu-id="e80e4-146">Feche Visual Studio 2019 para instalar a extensão.</span><span class="sxs-lookup"><span data-stu-id="e80e4-146">Close Visual Studio 2019 to install the extension.</span></span>

# <a name="command-line"></a>[<span data-ttu-id="e80e4-147">Linha de comando</span><span class="sxs-lookup"><span data-stu-id="e80e4-147">Command line</span></span>](#tab/cli)

<span data-ttu-id="e80e4-148">Para instalar a CLI do TeamsFx, use o `npm` gerenciador de pacotes:</span><span class="sxs-lookup"><span data-stu-id="e80e4-148">To install the TeamsFx CLI, use the `npm` package manager:</span></span>

``` bash
npm install -g @microsoft/teamsfx-cli
```

<span data-ttu-id="e80e4-149">Dependendo da configuração, talvez seja necessário usar `sudo` para instalar a CLI:</span><span class="sxs-lookup"><span data-stu-id="e80e4-149">Depending on your configuration, you may need to use `sudo` to install the CLI:</span></span>

``` bash
sudo npm install -g --unsafe-perm @microsoft/teamsfx-cli
```

<span data-ttu-id="e80e4-150">Isso é mais comum em sistemas Linux e macOS.</span><span class="sxs-lookup"><span data-stu-id="e80e4-150">This is more common on Linux and macOS systems.</span></span>

<span data-ttu-id="e80e4-151">Certifique-se de adicionar o cache global npm ao seu PATH.</span><span class="sxs-lookup"><span data-stu-id="e80e4-151">Ensure you add the npm global cache to your PATH.</span></span>  <span data-ttu-id="e80e4-152">Isso normalmente é feito como parte do Node.js instalador.</span><span class="sxs-lookup"><span data-stu-id="e80e4-152">This is normally done as part of the Node.js installer.</span></span>  

<span data-ttu-id="e80e4-153">Você pode usar a CLI com o `teamsfx` comando.</span><span class="sxs-lookup"><span data-stu-id="e80e4-153">You can use the CLI with the `teamsfx` command.</span></span>  <span data-ttu-id="e80e4-154">Verifique se o comando está funcionando executando `teamsfx -h` .</span><span class="sxs-lookup"><span data-stu-id="e80e4-154">Verify that the command is working by running `teamsfx -h`.</span></span>

> [!CAUTION]
> <span data-ttu-id="e80e4-155">Antes de executar o TeamsFx em terminais do PowerShell, você precisa habilitar a política de execução "assinada remotamente" para o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e80e4-155">Before you can run TeamsFx in PowerShell terminals, you need to enable the "remote signed" execution policy for PowerShell.</span></span>  <span data-ttu-id="e80e4-156">Para obter mais informações, consulte a [documentação do PowerShell](/powershell/module/microsoft.powershell.core/about/about_signing).</span><span class="sxs-lookup"><span data-stu-id="e80e4-156">For more information, refer to the [PowerShell documentation](/powershell/module/microsoft.powershell.core/about/about_signing).</span></span>

---

## <a name="install-optional-tools"></a><span data-ttu-id="e80e4-157">Instalar ferramentas opcionais</span><span class="sxs-lookup"><span data-stu-id="e80e4-157">Install optional tools</span></span>

<span data-ttu-id="e80e4-158">Instalar ferramentas de navegador para desenvolvimento de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="e80e4-158">Install browser tools for app development.</span></span> <span data-ttu-id="e80e4-159">Por exemplo, se seu aplicativo for escrito com React, você poderá usar React Ferramentas de Desenvolvedor:</span><span class="sxs-lookup"><span data-stu-id="e80e4-159">For instance, if your app is written with React, you can use React Developer Tools:</span></span>

- [<span data-ttu-id="e80e4-160">React Ferramentas de desenvolvedor para Chrome</span><span class="sxs-lookup"><span data-stu-id="e80e4-160">React Developer Tools for Chrome</span></span>](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi)

<span data-ttu-id="e80e4-161">Se você quiser acessar dados armazenados no Azure ou implantar um back-end baseado em nuvem para seu aplicativo Teams no Azure, instale estas ferramentas:</span><span class="sxs-lookup"><span data-stu-id="e80e4-161">If you want to access data stored in Azure or deploy a cloud-based backend for your Teams app in Azure, install these tools:</span></span>

- [<span data-ttu-id="e80e4-162">Ferramentas do Azure para Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e80e4-162">Azure Tools for Visual Studio Code</span></span>](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack)
- [<span data-ttu-id="e80e4-163">Azure CLI</span><span class="sxs-lookup"><span data-stu-id="e80e4-163">Azure CLI</span></span>](/cli/azure/install-azure-cli)

<span data-ttu-id="e80e4-164">Se você trabalhar com dados Graph microsoft, você deve aprender sobre e marcar o Microsoft Graph Explorer.</span><span class="sxs-lookup"><span data-stu-id="e80e4-164">If you work with Microsoft Graph data, you should learn about and bookmark the Microsoft Graph Explorer.</span></span> <span data-ttu-id="e80e4-165">Essa ferramenta baseada em navegador permite que você consulte o Microsoft Graph fora de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e80e4-165">This browser-based tool allows you to query Microsoft Graph outside of an app.</span></span>

- [<span data-ttu-id="e80e4-166">Microsoft Graph Explorer</span><span class="sxs-lookup"><span data-stu-id="e80e4-166">Microsoft Graph Explorer</span></span>](https://developer.microsoft.com/graph/graph-explorer)

<span data-ttu-id="e80e4-167">Com o Portal do Desenvolvedor para Teams, você pode configurar, gerenciar e distribuir seu aplicativo Teams de Teams (incluindo sua organização ou o Teams store).</span><span class="sxs-lookup"><span data-stu-id="e80e4-167">With the Developer Portal for Teams, you can configure, manage, and distribute your Teams app (including to your org or the Teams store).</span></span>

- [<span data-ttu-id="e80e4-168">Portal do Desenvolvedor do Teams</span><span class="sxs-lookup"><span data-stu-id="e80e4-168">Developer Portal for Teams</span></span>](https://dev.teams.microsoft.com/)

## <a name="enable-sideloading"></a><span data-ttu-id="e80e4-169">Habilitar o sideload</span><span class="sxs-lookup"><span data-stu-id="e80e4-169">Enable sideloading</span></span>

<span data-ttu-id="e80e4-170">Durante o desenvolvimento, você precisará carregar seu aplicativo em Teams sem distribuí-lo.</span><span class="sxs-lookup"><span data-stu-id="e80e4-170">During development, you will need to load your app within Teams without distributing it.</span></span>  <span data-ttu-id="e80e4-171">Isso é conhecido como "sideloading".</span><span class="sxs-lookup"><span data-stu-id="e80e4-171">This is known as "sideloading".</span></span>

1. <span data-ttu-id="e80e4-172">Se você tiver uma Teams, verifique se pode fazer sideload de aplicativos Teams:</span><span class="sxs-lookup"><span data-stu-id="e80e4-172">If you have a Teams account, verify if you can sideload apps in Teams:</span></span>

    1. <span data-ttu-id="e80e4-173">No cliente Teams, selecione **Aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="e80e4-173">In the Teams client, select **Apps**.</span></span>
    1. <span data-ttu-id="e80e4-174">Procure uma opção para Upload **um aplicativo personalizado.**</span><span class="sxs-lookup"><span data-stu-id="e80e4-174">Look for an option to **Upload a custom app**.</span></span>

    :::image type="content" source="~/assets/images/teams-toolkit-v2/upload-custom-app-closeup.png" alt-text="Ilustração mostrando onde Teams você pode carregar um aplicativo personalizado.":::

> [!NOTE]
> <span data-ttu-id="e80e4-176">Se você ainda não puder fazer sideload de aplicativos, fale com o administrador do Teams.</span><span class="sxs-lookup"><span data-stu-id="e80e4-176">If you still can't sideload apps, talk to your Teams administrator.</span></span> <span data-ttu-id="e80e4-177">Confira [habilitar Teams aplicativos personalizados](~/concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) e ativar o carregamento personalizado de aplicativos para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="e80e4-177">See [enable custom Teams apps and turn on custom app uploading](~/concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) for details.</span></span>

## <a name="get-a-free-teams-developer-tenant-optional"></a><span data-ttu-id="e80e4-178">Obter um locatário Teams desenvolvedor gratuito (opcional)</span><span class="sxs-lookup"><span data-stu-id="e80e4-178">Get a free Teams developer tenant (optional)</span></span>

<span data-ttu-id="e80e4-179">Se você não puder ver a opção de sideload ou não tiver uma conta Teams, você poderá obter uma conta de desenvolvedor gratuita Teams ingressar no programa de desenvolvedor do M365.</span><span class="sxs-lookup"><span data-stu-id="e80e4-179">If you cannot see the sideload option, or you don't have a Teams account, you can get a free Teams developer account by joining the M365 developer program.</span></span>  <span data-ttu-id="e80e4-180">O processo de registro leva aproximadamente dois minutos.</span><span class="sxs-lookup"><span data-stu-id="e80e4-180">The registration process takes approximately two minutes.</span></span>

1. <span data-ttu-id="e80e4-181">Vá para o programa [Microsoft 365 desenvolvedor.](https://developer.microsoft.com/microsoft-365/dev-program)</span><span class="sxs-lookup"><span data-stu-id="e80e4-181">Go to the [Microsoft 365 developer program](https://developer.microsoft.com/microsoft-365/dev-program).</span></span>
1. <span data-ttu-id="e80e4-182">Selecione **Ingressar agora** e siga as instruções na tela.</span><span class="sxs-lookup"><span data-stu-id="e80e4-182">Select **Join Now** and follow the onscreen instructions.</span></span>
1. <span data-ttu-id="e80e4-183">Quando você chegar à tela de boas-vindas, selecione **Configurar assinatura do E5**.</span><span class="sxs-lookup"><span data-stu-id="e80e4-183">When you get to the welcome screen, select **Set up E5 subscription**.</span></span>
1. <span data-ttu-id="e80e4-184">Configurar sua conta de administrador.</span><span class="sxs-lookup"><span data-stu-id="e80e4-184">Set up your administrator account.</span></span> <span data-ttu-id="e80e4-185">Depois de concluir, você deverá ver uma tela como esta.</span><span class="sxs-lookup"><span data-stu-id="e80e4-185">Once you finish, you should see a screen like this.</span></span>

    :::image type="content" source="~/assets/images/build-your-first-app/dev-program-subscription.png" alt-text="Exemplo do que você vê depois de se inscrever no programa Microsoft 365 desenvolvedor.":::

1. <span data-ttu-id="e80e4-187">Faça logoff Teams usando a conta de administrador que você acabou de configurar.</span><span class="sxs-lookup"><span data-stu-id="e80e4-187">Log in to Teams using the administrator account you just set up.</span></span>
1. <span data-ttu-id="e80e4-188">Verifique se você agora tem a opção **Upload aplicativo** personalizado.</span><span class="sxs-lookup"><span data-stu-id="e80e4-188">Verify if you now have the **Upload a custom app** option.</span></span>

## <a name="get-a-free-azure-account"></a><span data-ttu-id="e80e4-189">Obter uma conta gratuita do Azure</span><span class="sxs-lookup"><span data-stu-id="e80e4-189">Get a free Azure account</span></span>

<span data-ttu-id="e80e4-190">Se você deseja hospedar seu aplicativo ou acessar recursos no Azure, precisará de uma assinatura do Azure.</span><span class="sxs-lookup"><span data-stu-id="e80e4-190">If you wish to host your app or access resources within Azure, you will need an Azure subscription.</span></span>  <span data-ttu-id="e80e4-191">Você pode [criar uma conta gratuita](https://azure.microsoft.com/free/) antes de começar.</span><span class="sxs-lookup"><span data-stu-id="e80e4-191">You can [create a free account](https://azure.microsoft.com/free/) before you begin.</span></span>

## <a name="sign-in-to-your-microsoft-365-and-azure-accounts"></a><span data-ttu-id="e80e4-192">Entre em suas contas do Microsoft 365 e do Azure</span><span class="sxs-lookup"><span data-stu-id="e80e4-192">Sign in to your Microsoft 365 and Azure accounts</span></span>

<span data-ttu-id="e80e4-193">Você precisará de acesso a duas contas:</span><span class="sxs-lookup"><span data-stu-id="e80e4-193">You will need access to two accounts:</span></span>

- <span data-ttu-id="e80e4-194">Suas Microsoft 365 de conta.</span><span class="sxs-lookup"><span data-stu-id="e80e4-194">Your Microsoft 365 account credentials.</span></span> <span data-ttu-id="e80e4-195">Essa é a conta que você usa para entrar Teams.</span><span class="sxs-lookup"><span data-stu-id="e80e4-195">This is the account that you use to sign in to Teams.</span></span> <span data-ttu-id="e80e4-196">Se você estiver usando um Microsoft 365 de programa de desenvolvedor, essa é a conta de administrador que você configura quando se registrou no programa.</span><span class="sxs-lookup"><span data-stu-id="e80e4-196">If you're using an Microsoft 365 developer program tenant, this is the admin account you set up when you registered for the program.</span></span>
- - <span data-ttu-id="e80e4-197">Suas credenciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="e80e4-197">Your Azure credentials.</span></span> <span data-ttu-id="e80e4-198">Essa é a conta que você usa para acessar o Portal do Azure e para provisionar novos recursos de nuvem para dar suporte ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e80e4-198">This is the account that you use to access the Azure Portal and for provisioning new cloud resources to support your app.</span></span>

# <a name="visual-studio-code"></a>[<span data-ttu-id="e80e4-199">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e80e4-199">Visual Studio Code</span></span>](#tab/vscode)

1. <span data-ttu-id="e80e4-200">Abra Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e80e4-200">Open Visual Studio Code</span></span>
1. <span data-ttu-id="e80e4-201">Selecione o Teams na barra lateral:</span><span class="sxs-lookup"><span data-stu-id="e80e4-201">Select the Teams icon in the sidebar:</span></span>

    :::image type="content" source="~/assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="O ícone do Teams na barra lateral do Visual Studio Code":::

1. <span data-ttu-id="e80e4-203">Selecione **Entrar no M365**.</span><span class="sxs-lookup"><span data-stu-id="e80e4-203">Select **Sign in to M365**.</span></span>

    :::image type="content" source="~/assets/images/teams-toolkit-v2/account-commands.png" alt-text="Local da seção Contas usada para entrar.":::

1. <span data-ttu-id="e80e4-205">O processo de login começará a usar o navegador da Web normal.</span><span class="sxs-lookup"><span data-stu-id="e80e4-205">The sign-in process will start using your normal web browser.</span></span>  <span data-ttu-id="e80e4-206">Conclua o processo de login da sua conta M365.</span><span class="sxs-lookup"><span data-stu-id="e80e4-206">Complete the sign-in process for your M365 account.</span></span>  <span data-ttu-id="e80e4-207">Você será solicitado quando puder fechar o navegador e retornar ao Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="e80e4-207">You will be prompted when you can close the browser and return to Visual Studio Code.</span></span>
1. <span data-ttu-id="e80e4-208">Retorne ao Teams Toolkit dentro Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="e80e4-208">Return to the Teams Toolkit within Visual Studio Code.</span></span>
1. <span data-ttu-id="e80e4-209">Selecione **Entrar no Azure**.</span><span class="sxs-lookup"><span data-stu-id="e80e4-209">Select **Sign in to Azure**.</span></span>

    > [!TIP]
    > <span data-ttu-id="e80e4-210">Se você tiver a extensão da Conta do Azure instalada e estiver usando a mesma conta, ignore esta etapa.</span><span class="sxs-lookup"><span data-stu-id="e80e4-210">If you have the Azure Account extension installed and are using the same account, you can skip this step.</span></span>  <span data-ttu-id="e80e4-211">Você usará automaticamente a mesma conta que está usando em outras extensões.</span><span class="sxs-lookup"><span data-stu-id="e80e4-211">You will automatically use the same account as you are using in other extensions.</span></span>

1. <span data-ttu-id="e80e4-212">O processo de login começará a usar o navegador da Web normal.</span><span class="sxs-lookup"><span data-stu-id="e80e4-212">The sign-in process will start using your normal web browser.</span></span>  <span data-ttu-id="e80e4-213">Conclua o processo de login da sua conta do Azure.</span><span class="sxs-lookup"><span data-stu-id="e80e4-213">Complete the sign-in process for your Azure account.</span></span>  <span data-ttu-id="e80e4-214">Você será solicitado quando puder fechar o navegador e retornar ao Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="e80e4-214">You will be prompted when you can close the browser and return to Visual Studio Code.</span></span>

<span data-ttu-id="e80e4-215">Quando concluída, a seção **CONTAS** da barra lateral mostrará as duas contas separadamente, juntamente com o número de assinaturas usáveis do Azure disponíveis para você.</span><span class="sxs-lookup"><span data-stu-id="e80e4-215">When complete, the **ACCOUNTS** section of the sidebar will show the two accounts separately, together with the number of usable Azure subscriptions available to you.</span></span>  <span data-ttu-id="e80e4-216">Certifique-se de ter pelo menos uma assinatura do Azure acessível disponível.</span><span class="sxs-lookup"><span data-stu-id="e80e4-216">Ensure you have at least one usable Azure subscription available.</span></span>  <span data-ttu-id="e80e4-217">Caso não, saia e use uma conta diferente.</span><span class="sxs-lookup"><span data-stu-id="e80e4-217">If not, sign out and use a different account.</span></span>

# <a name="visual-studio-2019"></a>[<span data-ttu-id="e80e4-218">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="e80e4-218">Visual Studio 2019</span></span>](#tab/vs)

<span data-ttu-id="e80e4-219">Visual Studio 2019 solicitará que você faça logoff em cada serviço conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="e80e4-219">Visual Studio 2019 will prompt you to log in to each service as it is needed.</span></span>  <span data-ttu-id="e80e4-220">Você não precisa entrar em suas contas do M365 e do Azure com antecedência.</span><span class="sxs-lookup"><span data-stu-id="e80e4-220">You do not need to sign in to your M365 and Azure accounts in advance.</span></span>

# <a name="command-line"></a>[<span data-ttu-id="e80e4-221">Linha de comando</span><span class="sxs-lookup"><span data-stu-id="e80e4-221">Command line</span></span>](#tab/cli)

1. <span data-ttu-id="e80e4-222">Entre no Microsoft 365 com a CLI teamsFx:</span><span class="sxs-lookup"><span data-stu-id="e80e4-222">Sign in to Microsoft 365 with the TeamsFx CLI:</span></span>

    ``` bash
    teamsfx account login m365
    ```

    <span data-ttu-id="e80e4-223">O processo de login começará a usar o navegador da Web normal.</span><span class="sxs-lookup"><span data-stu-id="e80e4-223">The sign-in process will start using your normal web browser.</span></span>  <span data-ttu-id="e80e4-224">Conclua o processo de login da sua conta M365.</span><span class="sxs-lookup"><span data-stu-id="e80e4-224">Complete the sign-in process for your M365 account.</span></span>  <span data-ttu-id="e80e4-225">Você será solicitado quando puder fechar o navegador.</span><span class="sxs-lookup"><span data-stu-id="e80e4-225">You will be prompted when you can close the browser.</span></span>

2. <span data-ttu-id="e80e4-226">Entre no Azure com a CLI teamsFx:</span><span class="sxs-lookup"><span data-stu-id="e80e4-226">Sign in to Azure with the TeamsFx CLI:</span></span>

    ``` bash
    teamsfx account login azure
    ```

    <span data-ttu-id="e80e4-227">O processo de login começará a usar o navegador da Web normal.</span><span class="sxs-lookup"><span data-stu-id="e80e4-227">The sign-in process will start using your normal web browser.</span></span>  <span data-ttu-id="e80e4-228">Conclua o processo de login da sua conta do Azure.</span><span class="sxs-lookup"><span data-stu-id="e80e4-228">Complete the sign-in process for your Azure account.</span></span>  <span data-ttu-id="e80e4-229">Você será solicitado quando puder fechar o navegador.</span><span class="sxs-lookup"><span data-stu-id="e80e4-229">You will be prompted when you can close the browser.</span></span>

<span data-ttu-id="e80e4-230">Os logons da conta são compartilhados entre Visual Studio Code e a CLI teamsFx.</span><span class="sxs-lookup"><span data-stu-id="e80e4-230">The account logins are shared between Visual Studio Code and the TeamsFx CLI.</span></span>

---

## <a name="next-steps"></a><span data-ttu-id="e80e4-231">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="e80e4-231">Next steps</span></span>

<span data-ttu-id="e80e4-232">Agora que seu ambiente de desenvolvimento está configurado, você pode criar, criar e implantar seu primeiro Teams aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e80e4-232">Now that your development environment is configured, you can create, build, and deploy your first Teams app.</span></span>

- [<span data-ttu-id="e80e4-233">Crie seu primeiro Teams usando React</span><span class="sxs-lookup"><span data-stu-id="e80e4-233">Create your first Teams app using React</span></span>](first-app-react.md)
- [<span data-ttu-id="e80e4-234">Criar seu primeiro Teams com o Blazor</span><span class="sxs-lookup"><span data-stu-id="e80e4-234">Create your first Teams app with Blazor</span></span>](first-app-blazor.md)
- [<span data-ttu-id="e80e4-235">Crie seu primeiro Teams usando Estrutura do SharePoint (SPFx)</span><span class="sxs-lookup"><span data-stu-id="e80e4-235">Create your first Teams app using SharePoint Framework (SPFx)</span></span>](first-app-spfx.md)
- [<span data-ttu-id="e80e4-236">Criar um programa bot de conversação</span><span class="sxs-lookup"><span data-stu-id="e80e4-236">Create a conversational bot app</span></span>](first-app-bot.md)
- [<span data-ttu-id="e80e4-237">Criar uma extensão de mensagem</span><span class="sxs-lookup"><span data-stu-id="e80e4-237">Create a messaging extension</span></span>](first-message-extension.md)
