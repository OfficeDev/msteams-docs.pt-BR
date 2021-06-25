---
title: 'Tutorial - Criar seu primeiro aplicativo usando C #'
description: Saiba como começar a criar Microsoft Teams aplicativos com C# ou .NET.
keywords: getting started .net c# csharp
ms.custom: scenarios:getting-started; languages:ASP.NET,C#
localization_priority: Normal
ms.topic: tutorial
ms.date: 11/09/2018
ms.openlocfilehash: 58e11312e61124bf09fcb55d2bcd0fc475e75a49
ms.sourcegitcommit: 6e4d2c8e99426125f7b72b9640ee4a4b4f374401
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2021
ms.locfileid: "53114606"
---
# <a name="build-your-first-teams-app-using-c"></a><span data-ttu-id="d7588-104">Criar seu primeiro aplicativo Teams usando C #</span><span class="sxs-lookup"><span data-stu-id="d7588-104">Build your first Teams app using C#</span></span>

<span data-ttu-id="d7588-105">Neste tutorial, você aprenderá a criar seu primeiro aplicativo Microsoft Teams usando o .NET ou C#.</span><span class="sxs-lookup"><span data-stu-id="d7588-105">In this tutorial, you will learn how to build your very first Microsoft Teams app using .NET or C#.</span></span> <span data-ttu-id="d7588-106">Ele também orienta você pelas etapas para:</span><span class="sxs-lookup"><span data-stu-id="d7588-106">It also walks you through the steps to:</span></span>

1. [<span data-ttu-id="d7588-107">Preparar seu ambiente</span><span class="sxs-lookup"><span data-stu-id="d7588-107">Prepare your environment</span></span>](#prepare-your-environment)
1. [<span data-ttu-id="d7588-108">Obter pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d7588-108">Get prerequisites</span></span>](#GetPrerequisites)
1. [<span data-ttu-id="d7588-109">Baixar o exemplo</span><span class="sxs-lookup"><span data-stu-id="d7588-109">Download the sample</span></span>](#DownloadSample)
1. [<span data-ttu-id="d7588-110">Criar e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="d7588-110">Build and run the sample</span></span>](#BuildRun)
1. [<span data-ttu-id="d7588-111">Hospedar o aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="d7588-111">Host the sample app</span></span>](#hostsample)
1. [<span data-ttu-id="d7588-112">Atualizar as credenciais do aplicativo hospedado</span><span class="sxs-lookup"><span data-stu-id="d7588-112">Update the credentials for your hosted app</span></span>](#updatecredentials)
1. [<span data-ttu-id="d7588-113">Configurar a guia do aplicativo</span><span class="sxs-lookup"><span data-stu-id="d7588-113">Configure the app tab</span></span>](#configureapptab)

<a name="prepare-your-environment"></a>
[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a><span data-ttu-id="d7588-114">Obter pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d7588-114">Get prerequisites</span></span>

<span data-ttu-id="d7588-115">Para concluir este tutorial, você precisa instalar as seguintes ferramentas:</span><span class="sxs-lookup"><span data-stu-id="d7588-115">To complete this tutorial, you need to install the following tools:</span></span>

- [<span data-ttu-id="d7588-116">Instalar o Git</span><span class="sxs-lookup"><span data-stu-id="d7588-116">Install Git</span></span>](https://git-scm.com/downloads)
- [<span data-ttu-id="d7588-117">Instalar o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d7588-117">Install Visual Studio</span></span>](https://www.visualstudio.com/downloads/)

<span data-ttu-id="d7588-118">Você pode instalar a edição gratuita da comunidade Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d7588-118">You can install the free community edition of Visual Studio.</span></span> <span data-ttu-id="d7588-119">Durante a instalação, se houver uma opção para adicionar `git` ao caminho, selecione-o.</span><span class="sxs-lookup"><span data-stu-id="d7588-119">During installation, if there is an option to add `git` to the path, select it.</span></span> <span data-ttu-id="d7588-120">Em uma janela de terminal, execute o seguinte comando para verificar sua `git` instalação:</span><span class="sxs-lookup"><span data-stu-id="d7588-120">In a terminal window, run the following command to verify your `git` installation:</span></span>

```bash
$ git --version
git version 2.17.1.windows.2

```

> [!NOTE]
> <span data-ttu-id="d7588-121">Use uma janela de terminal adequada em sua plataforma.</span><span class="sxs-lookup"><span data-stu-id="d7588-121">Use a suitable terminal window on your platform.</span></span> <span data-ttu-id="d7588-122">Esses exemplos usam Git Bash, mas podem ser executados na maioria das plataformas.</span><span class="sxs-lookup"><span data-stu-id="d7588-122">These examples use Git Bash but can be run on most platforms.</span></span>

<span data-ttu-id="d7588-123">Abra a versão mais recente do Visual Studio e instale todas as atualizações.</span><span class="sxs-lookup"><span data-stu-id="d7588-123">Open the latest version of Visual Studio and install any updates.</span></span>

<span data-ttu-id="d7588-124">Você pode usar a mesma janela de terminal para executar os comandos neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="d7588-124">You can use the same terminal window to run the commands in this tutorial.</span></span>

<a name="DownloadSample"></a>

## <a name="download-the-sample"></a><span data-ttu-id="d7588-125">Baixar o exemplo</span><span class="sxs-lookup"><span data-stu-id="d7588-125">Download the sample</span></span>

<span data-ttu-id="d7588-126">Você pode começar com um [Hello, World simples!](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/csharp)</span><span class="sxs-lookup"><span data-stu-id="d7588-126">You can get started with a simple [Hello, World!](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/csharp)</span></span> <span data-ttu-id="d7588-127">exemplo em C#.</span><span class="sxs-lookup"><span data-stu-id="d7588-127">sample in C#.</span></span> <span data-ttu-id="d7588-128">Em uma janela de terminal, execute o seguinte comando para clonar o repositório de exemplo para o computador:</span><span class="sxs-lookup"><span data-stu-id="d7588-128">In a terminal window, run the following command to clone the sample repository to your computer:</span></span>

```bash
git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
```

> [!TIP]
> <span data-ttu-id="d7588-129">Você pode [bifurcar](https://help.github.com/articles/fork-a-repo/) [esse repo](https://github.com/OfficeDev/Microsoft-Teams-Samples) para modificar e salvar suas alterações no GitHub.</span><span class="sxs-lookup"><span data-stu-id="d7588-129">You can [fork](https://help.github.com/articles/fork-a-repo/) this [repo](https://github.com/OfficeDev/Microsoft-Teams-Samples) to modify and save your changes to GitHub.</span></span>

<a name="BuildRun"></a>

## <a name="build-and-run-the-sample"></a><span data-ttu-id="d7588-130">Criar e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="d7588-130">Build and run the sample</span></span>

<span data-ttu-id="d7588-131">Você pode criar e executar o smaple depois que ele for clonado.</span><span class="sxs-lookup"><span data-stu-id="d7588-131">You can build and run the smaple after it is cloned.</span></span> 

<span data-ttu-id="d7588-132">**Para criar e executar o exemplo clonado**</span><span class="sxs-lookup"><span data-stu-id="d7588-132">**To build and run the cloned sample**</span></span>

1. <span data-ttu-id="d7588-133">Abra o arquivo de **solução Microsoft.Teams. Samples.HelloWorld.sln** do **diretório Microsoft-Teams-Samples/samples/app-hello-world/csharp** do exemplo.</span><span class="sxs-lookup"><span data-stu-id="d7588-133">Open the solution file **Microsoft.Teams.Samples.HelloWorld.sln** from the **Microsoft-Teams-Samples/samples/app-hello-world/csharp** directory of the sample.</span></span>
1. <span data-ttu-id="d7588-134">Selecione **Criar Solução** no menu Criar. </span><span class="sxs-lookup"><span data-stu-id="d7588-134">Select **Build Solution** from the **Build** menu.</span></span>
1. <span data-ttu-id="d7588-135">Selecione a **tecla F5** ou selecione **Iniciar Depuração** no menu **Depurar** para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="d7588-135">Select the **F5** key, or select **Start Debugging** from the **Debug** menu to run the sample.</span></span>

<span data-ttu-id="d7588-136">Quando o aplicativo é iniciado, uma janela do navegador é aberta com a raiz do aplicativo iniciado.</span><span class="sxs-lookup"><span data-stu-id="d7588-136">When the app starts, a browser window opens with the root of the app launched.</span></span> <span data-ttu-id="d7588-137">Você pode ir para as SEGUINTES URLs para verificar se todas as URLs do aplicativo estão sendo carregadas:</span><span class="sxs-lookup"><span data-stu-id="d7588-137">You can go to the following URLs to verify that all the app URLs are loading:</span></span>

- `https://localhost:44327/`
- `https://localhost:44327/hello`
- `https://localhost:44327/first`
- `https://localhost:44327/second`

> [!Note]
> <span data-ttu-id="d7588-138">Se você receber um `Could not find a part of the path … bin\roslyn\csc.exe` erro, atualize o pacote com o comando `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r` .</span><span class="sxs-lookup"><span data-stu-id="d7588-138">If you receive an error `Could not find a part of the path … bin\roslyn\csc.exe`, update the package with the command `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r`.</span></span> <span data-ttu-id="d7588-139">Para obter mais informações, [consulte esta pergunta em Stack Overflow](https://stackoverflow.com/questions/32780315).</span><span class="sxs-lookup"><span data-stu-id="d7588-139">For more information, see [this question on Stack Overflow](https://stackoverflow.com/questions/32780315).</span></span>

<a name="hostsample"></a>
## <a name="deploy-your-sample-app"></a><span data-ttu-id="d7588-140">Implantar seu aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="d7588-140">Deploy your sample app</span></span>

<span data-ttu-id="d7588-141">Os aplicativos Microsoft Teams são aplicativos Web que fornecem um ou mais recursos.</span><span class="sxs-lookup"><span data-stu-id="d7588-141">Apps in Microsoft Teams are web applications that provide one or more capabilities.</span></span> <span data-ttu-id="d7588-142">Para que Teams plataforma de carregamento do aplicativo, seu aplicativo deve estar disponível na Internet.</span><span class="sxs-lookup"><span data-stu-id="d7588-142">For the Teams platform to load your app, your app must be available on the internet.</span></span> <span data-ttu-id="d7588-143">Para fazer isso, você precisa hospedar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d7588-143">To do this, you need to host your app.</span></span> <span data-ttu-id="d7588-144">Você pode hospedá-lo Microsoft Azure gratuitamente ou criar um túnel para o processo local em seu computador usando `ngrok` .</span><span class="sxs-lookup"><span data-stu-id="d7588-144">You can either host it in Microsoft Azure for free or create a tunnel to the local process on your computer using `ngrok`.</span></span> <span data-ttu-id="d7588-145">Depois de hospedar seu aplicativo, anote sua URL raiz, como `https://yourteamsapp.ngrok.io` ou `https://yourteamsapp.azurewebsites.net` .</span><span class="sxs-lookup"><span data-stu-id="d7588-145">After you host your app, make a note of its root URL, such as `https://yourteamsapp.ngrok.io` or `https://yourteamsapp.azurewebsites.net`.</span></span>

### <a name="tunnel-using-ngrok"></a><span data-ttu-id="d7588-146">Tunnel usando ngrok</span><span class="sxs-lookup"><span data-stu-id="d7588-146">Tunnel using ngrok</span></span>

<span data-ttu-id="d7588-147">Para testes rápidos, você pode executar o aplicativo em seu computador e criar um túnel para ele por meio de um ponto de extremidade da Web.</span><span class="sxs-lookup"><span data-stu-id="d7588-147">For quick testing, you can run the app on your computer and create a tunnel to it through a web endpoint.</span></span> <span data-ttu-id="d7588-148">[`ngrok`](https://ngrok.com) é uma ferramenta gratuita com a qual você pode obter um endereço da Web, como `https://d0ac14a5.ngrok.io` .</span><span class="sxs-lookup"><span data-stu-id="d7588-148">[`ngrok`](https://ngrok.com) is a free tool with which you can get a web address, such as `https://d0ac14a5.ngrok.io`.</span></span> <span data-ttu-id="d7588-149">Você pode [baixar e instalar](https://ngrok.com/download) o ngrok e adicioná-lo a um local em seu `PATH` .</span><span class="sxs-lookup"><span data-stu-id="d7588-149">You can [download and install](https://ngrok.com/download) ngrok and add it to a location in your `PATH`.</span></span>

<span data-ttu-id="d7588-150">Depois de instalar `ngrok` , abra uma nova janela de terminal e execute o seguinte comando para criar um túnel:</span><span class="sxs-lookup"><span data-stu-id="d7588-150">After you install `ngrok`, open a new terminal window and run the following command to create a tunnel:</span></span>

```bash
ngrok http 44327 -host-header=localhost:44327
```

<span data-ttu-id="d7588-151">`Ngrok` responde a solicitações da Internet e as encaminha para seu aplicativo em execução na porta 44327.</span><span class="sxs-lookup"><span data-stu-id="d7588-151">`Ngrok` responds to requests from the internet and routes them to your app running on port 44327.</span></span> 

<span data-ttu-id="d7588-152">**Para verificar a resposta**</span><span class="sxs-lookup"><span data-stu-id="d7588-152">**To verify the response**</span></span>

1. <span data-ttu-id="d7588-153">Abra seu navegador e vá para `https://d0ac14a5.ngrok.io/hello` .</span><span class="sxs-lookup"><span data-stu-id="d7588-153">Open your browser and go to `https://d0ac14a5.ngrok.io/hello`.</span></span> <span data-ttu-id="d7588-154">Isso carregará a página Hello do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d7588-154">This will load your app's Hello page.</span></span>
1. <span data-ttu-id="d7588-155">Em vez da URL mencionada na Etapa 1, use o endereço de encaminhamento exibido `ngrok` na sessão do console.</span><span class="sxs-lookup"><span data-stu-id="d7588-155">Instead of the URL mentioned in Step 1, use the forwarding address displayed by `ngrok` in your console session.</span></span>
    > [!NOTE]
    > <span data-ttu-id="d7588-156">Se você tiver usado uma porta diferente na etapa [de com](#build-and-run-the-sample) build e run, certifique-se de usar o mesmo número de porta para configurar o `ngrok` túnel.</span><span class="sxs-lookup"><span data-stu-id="d7588-156">If you have used a different port in the [build and run](#build-and-run-the-sample) step, ensure you use the same port number to setup the `ngrok` tunnel.</span></span>
    > [!TIP]
    > <span data-ttu-id="d7588-157">É uma boa ideia executar em `ngrok` uma janela de terminal diferente.</span><span class="sxs-lookup"><span data-stu-id="d7588-157">It is a good idea to run `ngrok` in a different terminal window.</span></span> <span data-ttu-id="d7588-158">Isso é feito para evitar `ngrok` a execução sem interferir no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d7588-158">This is done to keep `ngrok` from running without interfering with the app.</span></span> <span data-ttu-id="d7588-159">Você precisa parar, recriar e reprisar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d7588-159">You have to stop, rebuild, and rerun the app.</span></span> <span data-ttu-id="d7588-160">A `ngrok` sessão fornece informações úteis de depuração nesta janela.</span><span class="sxs-lookup"><span data-stu-id="d7588-160">The `ngrok` session provides useful debugging information in this window.</span></span>

    <span data-ttu-id="d7588-161">O aplicativo só está disponível durante a sessão atual em seu computador.</span><span class="sxs-lookup"><span data-stu-id="d7588-161">The app is only available during the current session on your computer.</span></span> <span data-ttu-id="d7588-162">Se o computador for desligado ou for desligado, o serviço não estará mais disponível.</span><span class="sxs-lookup"><span data-stu-id="d7588-162">If the machine is shut down or goes to sleep, the service is no longer available.</span></span> <span data-ttu-id="d7588-163">Lembre-se disso quando você compartilhar o aplicativo para testes com outros usuários.</span><span class="sxs-lookup"><span data-stu-id="d7588-163">Remember this when you share the app for testing to other users.</span></span> <span data-ttu-id="d7588-164">Se você tiver que reiniciar o serviço, o aplicativo retornará um novo endereço e você deverá atualizar cada local que usa esse endereço.</span><span class="sxs-lookup"><span data-stu-id="d7588-164">If you have to restart the service, the app returns a new address and you must update every location that uses that address.</span></span> <span data-ttu-id="d7588-165">A versão paga `ngrok` do não tem essa limitação.</span><span class="sxs-lookup"><span data-stu-id="d7588-165">The paid version of `ngrok` does not have this limitation.</span></span>

### <a name="host-in-azure"></a><span data-ttu-id="d7588-166">Host no Azure</span><span class="sxs-lookup"><span data-stu-id="d7588-166">Host in Azure</span></span>

<span data-ttu-id="d7588-167">Microsoft Azure hospeda seu aplicativo .NET em uma camada gratuita usando infraestrutura compartilhada.</span><span class="sxs-lookup"><span data-stu-id="d7588-167">Microsoft Azure hosts your .NET application on a free tier using shared infrastructure.</span></span> <span data-ttu-id="d7588-168">Isso é suficiente para executar o `Hello World` exemplo.</span><span class="sxs-lookup"><span data-stu-id="d7588-168">This is sufficient to run the `Hello World` sample.</span></span> <span data-ttu-id="d7588-169">Para obter mais informações, [consulte criando uma nova conta gratuita do Azure](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="d7588-169">For more information, see [creating a new free Azure account](https://azure.microsoft.com/free/).</span></span>

<span data-ttu-id="d7588-170">Visual Studio tem suporte integrado para implantação de aplicativos para diferentes provedores, incluindo o Azure:</span><span class="sxs-lookup"><span data-stu-id="d7588-170">Visual Studio has built-in support for app deployment to different providers, including Azure:</span></span>

<img width="530px" alt="Visual Studio" src="~/assets/images/get-started/publishtoazure1.png"/>

<span data-ttu-id="d7588-171">**Atualizar o pacote do aplicativo**</span><span class="sxs-lookup"><span data-stu-id="d7588-171">**Update the app package**</span></span>

# <a name="app-studio"></a>[<span data-ttu-id="d7588-172">App Studio</span><span class="sxs-lookup"><span data-stu-id="d7588-172">App Studio</span></span>](#tab/AS)

[!include [Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

# <a name="developer-portal"></a>[<span data-ttu-id="d7588-173">Portal do Desenvolvedor</span><span class="sxs-lookup"><span data-stu-id="d7588-173">Developer Portal</span></span>](#tab/DP)

<span data-ttu-id="d7588-174">**Para instalar o Portal do Desenvolvedor (visualização) Teams**</span><span class="sxs-lookup"><span data-stu-id="d7588-174">**To install Developer Portal (preview) in Teams**</span></span>


1. <span data-ttu-id="d7588-175">Selecione o **ícone Aplicativos** na parte inferior da barra à esquerda e procure o **Portal do Desenvolvedor.**</span><span class="sxs-lookup"><span data-stu-id="d7588-175">Select the **Apps** icon at the bottom of the left-hand bar, and search for **Developer Portal**.</span></span>

    <img width="430px" alt="Screenshot of TDP" src="~/assets/images/Screen1.png"/>

1. <span data-ttu-id="d7588-176">Selecione **Portal do Desenvolvedor** e selecione **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="d7588-176">Select **Developer Portal** and select **Open**.</span></span>

    <img width="430px" alt="Screenshot of TDP Open" src="~/assets/images/screen2.png"/>

1. <span data-ttu-id="d7588-177">Selecione a guia Aplicativos e selecione **Importar um aplicativo existente.**</span><span class="sxs-lookup"><span data-stu-id="d7588-177">Select the Apps tab and select **Import an existing app**.</span></span>

    <img width="430px" alt="Screenshot of import app in tdp" src="~/assets/images/screen3.png"/>

1. <span data-ttu-id="d7588-178">Selecione **Hello World** e selecione **Importar**.</span><span class="sxs-lookup"><span data-stu-id="d7588-178">Select **Hello World** and select **Import**.</span></span> <span data-ttu-id="d7588-179">O **aplicativo Hello World** é importado no Portal do Desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="d7588-179">The **Hello World** app is imported in Developer Portal.</span></span> 

    <span data-ttu-id="d7588-180">Você pode configurar seu aplicativo usando o Teams Portal do Desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="d7588-180">You can configure your app using the Teams Developer Portal.</span></span> <span data-ttu-id="d7588-181">O Manifesto é encontrado em Distribute.</span><span class="sxs-lookup"><span data-stu-id="d7588-181">The Manifest is found under Distribute.</span></span> <span data-ttu-id="d7588-182">Você pode usar o Manifesto para configurar recursos, recursos necessários e outros atributos importantes para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d7588-182">You can use the Manifest to configure capabilities, required resources, and other important attributes for your app.</span></span> <span data-ttu-id="d7588-183">Para obter mais detalhes sobre como configurar seu aplicativo usando o Portal do Desenvolvedor, [consulte Teams Portal do Desenvolvedor.](../concepts/build-and-test/teams-developer-portal.md)</span><span class="sxs-lookup"><span data-stu-id="d7588-183">For more details on how to configure your app using Developer Portal, see [Teams Developer Portal](../concepts/build-and-test/teams-developer-portal.md).</span></span>

    <img width="430px" alt="Screenshot of configure tdp" src="~/assets/images/Screen4.png"/>
---

<a name="updatecredentials"></a>
## <a name="update-the-credentials-for-your-hosted-app"></a><span data-ttu-id="d7588-184">Atualizar as credenciais do aplicativo hospedado</span><span class="sxs-lookup"><span data-stu-id="d7588-184">Update the credentials for your hosted app</span></span>

<span data-ttu-id="d7588-185">O aplicativo de exemplo exige que as variáveis de ambiente sejam definidas como os valores salvos no arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="d7588-185">The sample app requires the environment variables to be set to the values that you saved in the text file.</span></span>

<span data-ttu-id="d7588-186">**Para atualizar as credenciais do aplicativo hospedado**</span><span class="sxs-lookup"><span data-stu-id="d7588-186">**To update the credentials for your hosted app**</span></span>

1. <span data-ttu-id="d7588-187">Abra o arquivo `appsettings.json`.</span><span class="sxs-lookup"><span data-stu-id="d7588-187">Open the `appsettings.json` file.</span></span> 
1. <span data-ttu-id="d7588-188">Atualize o **valor do MicrosoftAppId** com sua ID de bot que você salvou no arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="d7588-188">Update the **MicrosoftAppId** value with your bot ID that you saved in the text file.</span></span> 
1. <span data-ttu-id="d7588-189">Atualize **o MicrosoftAppPassword** com a senha de bot que você salvou.</span><span class="sxs-lookup"><span data-stu-id="d7588-189">Update the **MicrosoftAppPassword** with the bot password that you saved.</span></span>

    <img width="560px" alt="Setting the keys" src="~/assets/images/get-started/get-started-net-azure-add-keys.png"/>

    <span data-ttu-id="d7588-190">Depois que essas alterações são feitas, reconstróa o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d7588-190">After these changes are made, rebuild the app.</span></span> <span data-ttu-id="d7588-191">Se você estiver usando o ngrok, execute o aplicativo localmente e, se estiver hospedando no Azure, reimplante o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d7588-191">If you are using ngrok, run the app locally, and if you are hosting in Azure, redeploy the app.</span></span>

<a name="configureapptab"></a>
## <a name="configure-the-app-tab"></a><span data-ttu-id="d7588-192">Configurar a guia do aplicativo</span><span class="sxs-lookup"><span data-stu-id="d7588-192">Configure the app tab</span></span>

<span data-ttu-id="d7588-193">Depois de instalar o aplicativo em equipes, você deve configurá-lo para exibir o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="d7588-193">After you have installed the app into teams, you must configure it to display the content.</span></span> 

<span data-ttu-id="d7588-194">**Para configurar a guia do aplicativo**</span><span class="sxs-lookup"><span data-stu-id="d7588-194">**To configure the app tab**</span></span>

1. <span data-ttu-id="d7588-195">Vá para um canal na equipe onde você instalou o aplicativo de exemplo e selecione o botão **'+'** para adicionar uma nova guia.</span><span class="sxs-lookup"><span data-stu-id="d7588-195">Go to a channel in the team where you installed the sample app and select the **'+'** button to add a new tab.</span></span>
1. <span data-ttu-id="d7588-196">Selecione **Hello World** na lista Adicionar **uma** guia.</span><span class="sxs-lookup"><span data-stu-id="d7588-196">Select **Hello World** from the **Add a tab** list.</span></span> <span data-ttu-id="d7588-197">Uma caixa de diálogo de configuração é exibida que permite selecionar a guia a ser exibida neste canal.</span><span class="sxs-lookup"><span data-stu-id="d7588-197">A configuration dialog box is displayed that enables you to select the tab to display in this channel.</span></span> 
1. <span data-ttu-id="d7588-198">Selecione **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="d7588-198">Select **Save**.</span></span> <span data-ttu-id="d7588-199">A `Hello World` guia é carregada com a guia.</span><span class="sxs-lookup"><span data-stu-id="d7588-199">The `Hello World` tab is loaded with the tab.</span></span>

    <img width="530px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png" />

### <a name="test-your-bot-in-teams"></a><span data-ttu-id="d7588-200">Teste seu bot no Teams</span><span class="sxs-lookup"><span data-stu-id="d7588-200">Test your bot in Teams</span></span>

<span data-ttu-id="d7588-201">Agora você pode testar o bot Teams.</span><span class="sxs-lookup"><span data-stu-id="d7588-201">You can now test the bot in Teams.</span></span> 

<span data-ttu-id="d7588-202">**Para testar seu bot**</span><span class="sxs-lookup"><span data-stu-id="d7588-202">**To test your bot**</span></span>

* <span data-ttu-id="d7588-203">Selecione um canal na equipe em que você registrou seu aplicativo e digite `@your-bot-name` .</span><span class="sxs-lookup"><span data-stu-id="d7588-203">Select a channel in the team where you registered your app and type `@your-bot-name`.</span></span> <span data-ttu-id="d7588-204">Isso é chamado de **\@ menção**.</span><span class="sxs-lookup"><span data-stu-id="d7588-204">This is called an **\@mention**.</span></span> <span data-ttu-id="d7588-205">O bot responde a qualquer mensagem enviada.</span><span class="sxs-lookup"><span data-stu-id="d7588-205">The bot replies to any message that you send.</span></span>

    <img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png" />

### <a name="test-your-messaging-extension"></a><span data-ttu-id="d7588-206">Testar sua extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="d7588-206">Test your messaging extension</span></span>

<span data-ttu-id="d7588-207">Para testar sua extensão de mensagens, selecione **...** abaixo da caixa de entrada no seu exibição de conversa.</span><span class="sxs-lookup"><span data-stu-id="d7588-207">To test your messaging extension, select **...** below the input box in your conversation view.</span></span> <span data-ttu-id="d7588-208">Um menu com o **aplicativo "Hello World"** é exibido.</span><span class="sxs-lookup"><span data-stu-id="d7588-208">A menu with the **'Hello World'** app is displayed.</span></span> <span data-ttu-id="d7588-209">Quando você o seleciona, um conjunto de textos aleatórios é exibido.</span><span class="sxs-lookup"><span data-stu-id="d7588-209">When you select it, a set of random texts is displayed.</span></span> <span data-ttu-id="d7588-210">Você pode selecionar um dos textos aleatórios e que é inserido em sua conversa.</span><span class="sxs-lookup"><span data-stu-id="d7588-210">You can select one of the random text and that is inserted into your conversation.</span></span>

<img width="530px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu1.png" />

<img width="530px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result1.png" />

<span data-ttu-id="d7588-211">Selecione um dos textos aleatórios.</span><span class="sxs-lookup"><span data-stu-id="d7588-211">Select one of the random text.</span></span> <span data-ttu-id="d7588-212">Um cartão formatado e pronto para enviar com sua própria mensagem é mostrado.</span><span class="sxs-lookup"><span data-stu-id="d7588-212">A card formatted and ready to send with your own message is shown.</span></span>

<img width="530px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />

## <a name="see-also"></a><span data-ttu-id="d7588-213">Confira também</span><span class="sxs-lookup"><span data-stu-id="d7588-213">See also</span></span>

* [<span data-ttu-id="d7588-214">Visão geral dos tutoriais</span><span class="sxs-lookup"><span data-stu-id="d7588-214">Tutorials Overview</span></span>](code-samples.md)
* [<span data-ttu-id="d7588-215">Exemplos de código</span><span class="sxs-lookup"><span data-stu-id="d7588-215">Code Samples</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples)