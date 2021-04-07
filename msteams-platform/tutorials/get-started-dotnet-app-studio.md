---
title: 'Tutorial - Criar seu primeiro aplicativo usando C #'
description: Saiba como começar a criar aplicativos do Microsoft Teams com C# ou .NET.
keywords: getting started .net c# csharp
ms.custom: scenarios:getting-started; languages:ASP.NET,C#
ms.topic: tutorial
ms.date: 11/09/2018
ms.openlocfilehash: 99a0982a0fa453c6eb7ffeea25ba8a2607cf2d5e
ms.sourcegitcommit: f5ee3fa5ef6126d9bf845948d27d9067b3bbb994
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2021
ms.locfileid: "51596256"
---
# <a name="create-your-first-teams-app-using-c-or-net"></a><span data-ttu-id="b1495-104">Crie seu primeiro aplicativo do Teams usando C# ou .NET</span><span class="sxs-lookup"><span data-stu-id="b1495-104">Create your first Teams app using C# or .NET</span></span>

<span data-ttu-id="b1495-105">Este tutorial ajuda você a criar um aplicativo do Microsoft Teams usando C# ou .NET.</span><span class="sxs-lookup"><span data-stu-id="b1495-105">This tutorial helps you to create a Microsoft Teams app using C# or .NET.</span></span> <span data-ttu-id="b1495-106">Para fazer isso, você deve:</span><span class="sxs-lookup"><span data-stu-id="b1495-106">To do this, you must:</span></span>

* <span data-ttu-id="b1495-107">Preparar seu ambiente</span><span class="sxs-lookup"><span data-stu-id="b1495-107">Prepare your environment</span></span>
* <span data-ttu-id="b1495-108">Obter pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b1495-108">Get prerequisites</span></span>
* <span data-ttu-id="b1495-109">Baixar o exemplo</span><span class="sxs-lookup"><span data-stu-id="b1495-109">Download the sample</span></span>
* <span data-ttu-id="b1495-110">Criar e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="b1495-110">Build and run the sample</span></span>
* <span data-ttu-id="b1495-111">Hospedar o aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="b1495-111">Host the sample app</span></span>
* <span data-ttu-id="b1495-112">Atualizar as credenciais do aplicativo hospedado</span><span class="sxs-lookup"><span data-stu-id="b1495-112">Update the credentials for your hosted app</span></span>
* <span data-ttu-id="b1495-113">Configurar a guia do aplicativo</span><span class="sxs-lookup"><span data-stu-id="b1495-113">Configure the app tab</span></span>

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a><span data-ttu-id="b1495-114">Obter pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b1495-114">Get prerequisites</span></span>

<span data-ttu-id="b1495-115">Para concluir este tutorial, você precisa instalar as seguintes ferramentas:</span><span class="sxs-lookup"><span data-stu-id="b1495-115">To complete this tutorial, you need to install the following tools:</span></span>

- [<span data-ttu-id="b1495-116">Instalar o Git</span><span class="sxs-lookup"><span data-stu-id="b1495-116">Install Git</span></span>](https://git-scm.com/downloads)
- [<span data-ttu-id="b1495-117">Instalar o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b1495-117">Install Visual Studio</span></span>](https://www.visualstudio.com/downloads/)

<span data-ttu-id="b1495-118">Você pode instalar a edição gratuita da comunidade Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b1495-118">You can install the free community edition of Visual Studio.</span></span> <span data-ttu-id="b1495-119">Durante a instalação, se houver uma opção para adicionar `git` ao caminho, selecione-o.</span><span class="sxs-lookup"><span data-stu-id="b1495-119">During installation, if there is an option to add `git` to the path, select it.</span></span> <span data-ttu-id="b1495-120">Em uma janela de terminal, execute o seguinte comando para verificar sua `git` instalação:</span><span class="sxs-lookup"><span data-stu-id="b1495-120">In a terminal window, run the following command to verify your `git` installation:</span></span>

```bash
$ git --version
git version 2.17.1.windows.2

```

> [!NOTE]
> <span data-ttu-id="b1495-121">Use uma janela de terminal adequada em sua plataforma.</span><span class="sxs-lookup"><span data-stu-id="b1495-121">Use a suitable terminal window on your platform.</span></span> <span data-ttu-id="b1495-122">Esses exemplos usam Git Bash, mas podem ser executados na maioria das plataformas.</span><span class="sxs-lookup"><span data-stu-id="b1495-122">These examples use Git Bash but can be run on most platforms.</span></span>

<span data-ttu-id="b1495-123">Abra a versão mais recente do Visual Studio e instale todas as atualizações.</span><span class="sxs-lookup"><span data-stu-id="b1495-123">Open the latest version of Visual Studio and install any updates.</span></span>

<span data-ttu-id="b1495-124">Você pode usar a mesma janela de terminal para executar os comandos neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="b1495-124">You can use the same terminal window to run the commands in this tutorial.</span></span>

<a name="DownloadSample"></a>

## <a name="download-the-sample"></a><span data-ttu-id="b1495-125">Baixar o exemplo</span><span class="sxs-lookup"><span data-stu-id="b1495-125">Download the sample</span></span>

<span data-ttu-id="b1495-126">Você pode começar com um [Hello, World simples!](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/csharp)</span><span class="sxs-lookup"><span data-stu-id="b1495-126">You can get started with a simple [Hello, World!](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/csharp)</span></span> <span data-ttu-id="b1495-127">exemplo em C#.</span><span class="sxs-lookup"><span data-stu-id="b1495-127">sample in C#.</span></span> <span data-ttu-id="b1495-128">Em uma janela de terminal, execute o seguinte comando para clonar o repositório de exemplo para o computador:</span><span class="sxs-lookup"><span data-stu-id="b1495-128">In a terminal window, run the following command to clone the sample repository to your computer:</span></span>

```bash
git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
```

> [!TIP]
> <span data-ttu-id="b1495-129">Você pode [bifurcar](https://help.github.com/articles/fork-a-repo/) [esse repositório para](https://github.com/OfficeDev/Microsoft-Teams-Samples) modificar e salvar suas alterações no GitHub.</span><span class="sxs-lookup"><span data-stu-id="b1495-129">You can [fork](https://help.github.com/articles/fork-a-repo/) this [repo](https://github.com/OfficeDev/Microsoft-Teams-Samples) to modify and save your changes to GitHub.</span></span>

<a name="BuildRun"></a>

## <a name="build-and-run-the-sample"></a><span data-ttu-id="b1495-130">Criar e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="b1495-130">Build and run the sample</span></span>

<span data-ttu-id="b1495-131">Depois que o repo for clonado, use o Visual Studio para abrir o arquivo de solução **Microsoft.Teams.Samples.HelloWorld.sln** do **diretório Microsoft-Teams-Samples/samples/app-hello-world/csharp** do exemplo.</span><span class="sxs-lookup"><span data-stu-id="b1495-131">After the repo is cloned, use Visual Studio to open the solution file **Microsoft.Teams.Samples.HelloWorld.sln** from the **Microsoft-Teams-Samples/samples/app-hello-world/csharp** directory of the sample.</span></span> <span data-ttu-id="b1495-132">Em seguida, selecione **Criar Solução** no menu **Criar.**</span><span class="sxs-lookup"><span data-stu-id="b1495-132">Then, select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="b1495-133">Para executar o exemplo, pressione **F5** ou selecione **Iniciar Depuração** no menu **Depurar.**</span><span class="sxs-lookup"><span data-stu-id="b1495-133">To run the sample, press **F5** or select **Start Debugging** from the **Debug** menu.</span></span>

<span data-ttu-id="b1495-134">Quando o aplicativo é iniciado, uma janela do navegador é aberta com a raiz do aplicativo iniciado.</span><span class="sxs-lookup"><span data-stu-id="b1495-134">When the app starts, a browser window opens with the root of the app launched.</span></span> <span data-ttu-id="b1495-135">Você pode ir para as SEGUINTES URLs para verificar se todas as URLs do aplicativo estão sendo carregadas:</span><span class="sxs-lookup"><span data-stu-id="b1495-135">You can go to the following URLs to verify that all the app URLs are loading:</span></span>

- [https://localhost:44327/](https://localhost:44327/)
- [https://localhost:44327/hello](https://localhost:44327/hello)
- [https://localhost:44327/first](https://localhost:44327/first)
- [https://localhost:44327/second](https://localhost:44327/second)

<a name="HostSample"></a>

> [!Note]
> <span data-ttu-id="b1495-136">Se você receber um `Could not find a part of the path … bin\roslyn\csc.exe` erro, atualize o pacote com o comando `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r` .</span><span class="sxs-lookup"><span data-stu-id="b1495-136">If you receive an error `Could not find a part of the path … bin\roslyn\csc.exe`, update the package with the command `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r`.</span></span> <span data-ttu-id="b1495-137">Para obter mais informações, [consulte esta pergunta em Stack Overflow](https://stackoverflow.com/questions/32780315).</span><span class="sxs-lookup"><span data-stu-id="b1495-137">For more information, see [this question on Stack Overflow](https://stackoverflow.com/questions/32780315).</span></span>

## <a name="host-the-sample-app"></a><span data-ttu-id="b1495-138">Hospedar o aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="b1495-138">Host the sample app</span></span>

<span data-ttu-id="b1495-139">Os aplicativos no Microsoft Teams são aplicativos Web que fornecem um ou mais recursos.</span><span class="sxs-lookup"><span data-stu-id="b1495-139">Apps in Microsoft Teams are web applications that provide one or more capabilities.</span></span> <span data-ttu-id="b1495-140">Para que a plataforma teams carregue seu aplicativo, seu aplicativo deve estar disponível na Internet.</span><span class="sxs-lookup"><span data-stu-id="b1495-140">For the Teams platform to load your app, your app must be available on the internet.</span></span> <span data-ttu-id="b1495-141">Para fazer isso, você precisa hospedar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b1495-141">To do this, you need to host your app.</span></span> <span data-ttu-id="b1495-142">Você pode hospedá-lo gratuitamente no Microsoft Azure ou criar um túnel para o processo local em seu computador usando `ngrok` .</span><span class="sxs-lookup"><span data-stu-id="b1495-142">You can either host it in Microsoft Azure for free or create a tunnel to the local process on your computer using `ngrok`.</span></span> <span data-ttu-id="b1495-143">Depois de hospedar seu aplicativo, anote sua URL raiz, como `https://yourteamsapp.ngrok.io` ou `https://yourteamsapp.azurewebsites.net` .</span><span class="sxs-lookup"><span data-stu-id="b1495-143">After you host your app, note its root URL, such as `https://yourteamsapp.ngrok.io` or `https://yourteamsapp.azurewebsites.net`.</span></span>

### <a name="tunnel-using-ngrok"></a><span data-ttu-id="b1495-144">Túnel usando ngrok</span><span class="sxs-lookup"><span data-stu-id="b1495-144">Tunnel using ngrok</span></span>

<span data-ttu-id="b1495-145">Para testes rápidos, você pode executar o aplicativo em seu computador e criar um túnel para ele por meio de um ponto de extremidade da Web.</span><span class="sxs-lookup"><span data-stu-id="b1495-145">For quick testing, you can run the app on your computer and create a tunnel to it through a web endpoint.</span></span> <span data-ttu-id="b1495-146">[`ngrok`](https://ngrok.com) é uma ferramenta gratuita com a qual você pode obter um endereço da Web, como `https://d0ac14a5.ngrok.io` .</span><span class="sxs-lookup"><span data-stu-id="b1495-146">[`ngrok`](https://ngrok.com) is a free tool with which you can get a web address, such as `https://d0ac14a5.ngrok.io`.</span></span> <span data-ttu-id="b1495-147">Você pode [baixar e instalar](https://ngrok.com/download) o ngrok e adicioná-lo a um local em seu `PATH` .</span><span class="sxs-lookup"><span data-stu-id="b1495-147">You can [download and install](https://ngrok.com/download) ngrok and add it to a location in your `PATH`.</span></span>

<span data-ttu-id="b1495-148">Depois de instalar `ngrok` , abra uma nova janela de terminal e execute o seguinte comando para criar um túnel:</span><span class="sxs-lookup"><span data-stu-id="b1495-148">After you install `ngrok`, open a new terminal window and run the following command to create a tunnel:</span></span>

```bash
ngrok http 44327 -host-header=localhost:44327
```

<span data-ttu-id="b1495-149">`Ngrok` escuta solicitações da Internet e as encaminha para seu aplicativo em execução na porta 44327.</span><span class="sxs-lookup"><span data-stu-id="b1495-149">`Ngrok` listens to requests from the internet and routes them to your app running on port 44327.</span></span> <span data-ttu-id="b1495-150">Para verificar, abra o navegador e vá `https://d0ac14a5.ngrok.io/hello` para carregar a página hello do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b1495-150">To verify, open your browser and go to `https://d0ac14a5.ngrok.io/hello` to load your app's hello page.</span></span> <span data-ttu-id="b1495-151">Em vez dessa URL, use o endereço de encaminhamento exibido na `ngrok` sessão do console.</span><span class="sxs-lookup"><span data-stu-id="b1495-151">Instead of this URL, use the forwarding address displayed by `ngrok` in your console session.</span></span>

> [!NOTE]
> <span data-ttu-id="b1495-152">Se você tiver usado uma porta diferente na etapa [de com](#build-and-run-the-sample) build e run, certifique-se de usar o mesmo número de porta para configurar o `ngrok` túnel.</span><span class="sxs-lookup"><span data-stu-id="b1495-152">If you have used a different port in the [build and run](#build-and-run-the-sample) step, ensure you use the same port number to setup the `ngrok` tunnel.</span></span>

> [!TIP]
> <span data-ttu-id="b1495-153">É uma boa ideia executar em `ngrok` uma janela de terminal diferente.</span><span class="sxs-lookup"><span data-stu-id="b1495-153">It is a good idea to run `ngrok` in a different terminal window.</span></span> <span data-ttu-id="b1495-154">Isso é feito para evitar `ngrok` a execução sem interferir no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b1495-154">This is done to keep `ngrok` from running without interfering with the app.</span></span> <span data-ttu-id="b1495-155">Você precisa parar, recriar e reprisar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b1495-155">You have to stop, rebuild, and rerun the app.</span></span> <span data-ttu-id="b1495-156">A `ngrok` sessão fornece informações úteis de depuração nesta janela.</span><span class="sxs-lookup"><span data-stu-id="b1495-156">The `ngrok` session provides useful debugging information in this window.</span></span>

<span data-ttu-id="b1495-157">O aplicativo só está disponível durante a sessão atual em seu computador.</span><span class="sxs-lookup"><span data-stu-id="b1495-157">The app is only available during the current session on your computer.</span></span> <span data-ttu-id="b1495-158">Se o computador for desligado ou for desligado, o serviço não estará mais disponível.</span><span class="sxs-lookup"><span data-stu-id="b1495-158">If the machine is shut down or goes to sleep, the service is no longer available.</span></span> <span data-ttu-id="b1495-159">Lembre-se disso quando você compartilhar o aplicativo para testes com outros usuários.</span><span class="sxs-lookup"><span data-stu-id="b1495-159">Remember this when you share the app for testing to other users.</span></span> <span data-ttu-id="b1495-160">Se você tiver que reiniciar o serviço, o aplicativo retornará um novo endereço e você deverá atualizar cada local que usa esse endereço.</span><span class="sxs-lookup"><span data-stu-id="b1495-160">If you have to restart the service, the app returns a new address and you must update every location that uses that address.</span></span> <span data-ttu-id="b1495-161">A versão paga `ngrok` do não tem essa limitação.</span><span class="sxs-lookup"><span data-stu-id="b1495-161">The paid version of `ngrok` does not have this limitation.</span></span>

### <a name="host-in-azure"></a><span data-ttu-id="b1495-162">Host no Azure</span><span class="sxs-lookup"><span data-stu-id="b1495-162">Host in Azure</span></span>

<span data-ttu-id="b1495-163">O Microsoft Azure hospeda seu aplicativo .NET em uma camada gratuita usando infraestrutura compartilhada.</span><span class="sxs-lookup"><span data-stu-id="b1495-163">Microsoft Azure hosts your .NET application on a free tier using shared infrastructure.</span></span> <span data-ttu-id="b1495-164">Isso é suficiente para executar o `Hello World` exemplo.</span><span class="sxs-lookup"><span data-stu-id="b1495-164">This is sufficient to run the `Hello World` sample.</span></span> <span data-ttu-id="b1495-165">Para obter mais informações, [consulte criando uma nova conta gratuita do Azure](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="b1495-165">For more information, see [creating a new free Azure account](https://azure.microsoft.com/free/).</span></span>

<span data-ttu-id="b1495-166">Visual Studio tem suporte integrado para implantação de aplicativos para diferentes provedores, incluindo o Azure.</span><span class="sxs-lookup"><span data-stu-id="b1495-166">Visual Studio has built-in support for app deployment to different providers, including Azure.</span></span>

<img width="530px" alt="Visual Studio" src="~/assets/images/get-started/publishtoazure1.png"/>

[!include [Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-the-credentials-for-your-hosted-app"></a><span data-ttu-id="b1495-167">Atualizar as credenciais do aplicativo hospedado</span><span class="sxs-lookup"><span data-stu-id="b1495-167">Update the credentials for your hosted app</span></span>

<span data-ttu-id="b1495-168">O aplicativo de exemplo exige que as variáveis de ambiente sejam definidas para os valores salvos no arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="b1495-168">The sample app requires the environment variables be set to the values that you saved in the text file.</span></span>

<span data-ttu-id="b1495-169">Abra o arquivo `appsettings.json`.</span><span class="sxs-lookup"><span data-stu-id="b1495-169">Open the `appsettings.json` file.</span></span> <span data-ttu-id="b1495-170">Atualize o **valor do MicrosoftAppId** com sua ID de bot que você salvou no arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="b1495-170">Update the **MicrosoftAppId** value with your bot ID that you saved in the text file.</span></span> <span data-ttu-id="b1495-171">Atualize **o MicrosoftAppPassword** com a senha de bot salva.</span><span class="sxs-lookup"><span data-stu-id="b1495-171">Update the **MicrosoftAppPassword** with the bot password you saved.</span></span>

<img width="560px" alt="Setting the keys" src="~/assets/images/get-started/get-started-net-azure-add-keys.png"/>

<span data-ttu-id="b1495-172">Depois que essas alterações são feitas, reconstróa o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b1495-172">After these changes are made, rebuild the app.</span></span> <span data-ttu-id="b1495-173">Se você estiver usando o ngrok, execute o aplicativo localmente e, se estiver hospedando no Azure, reimplante o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b1495-173">If you are using ngrok, run the app locally, and if you are hosting in Azure, redeploy the app.</span></span>

## <a name="configure-the-app-tab"></a><span data-ttu-id="b1495-174">Configurar a guia do aplicativo</span><span class="sxs-lookup"><span data-stu-id="b1495-174">Configure the app tab</span></span>

<span data-ttu-id="b1495-175">Depois de instalar o aplicativo em uma equipe, você deve configurá-lo para mostrar conteúdo.</span><span class="sxs-lookup"><span data-stu-id="b1495-175">Once you install the app into a team, you must configure it to show content.</span></span> <span data-ttu-id="b1495-176">Vá para um canal na equipe onde você instalou o aplicativo de exemplo e selecione o botão **'+'** para adicionar uma nova guia. Escolha **Hello World** na lista Adicionar **uma** guia.</span><span class="sxs-lookup"><span data-stu-id="b1495-176">Go to a channel in the team where you installed the sample app and select the **'+'** button to add a new tab. Choose **Hello World** from the **Add a tab** list.</span></span> <span data-ttu-id="b1495-177">Uma caixa de diálogo de configuração é exibida que permite que você escolha a guia a ser exibida neste canal.</span><span class="sxs-lookup"><span data-stu-id="b1495-177">A configuration dialog box is displayed that enables you to choose the tab to display in this channel.</span></span> <span data-ttu-id="b1495-178">Depois de selecionar a guia e selecionar **Salvar,** `Hello World` a guia será carregada com a guia.</span><span class="sxs-lookup"><span data-stu-id="b1495-178">After you select the tab and select **Save** the `Hello World` tab is loaded with the tab.</span></span>

<img width="530px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png" />

### <a name="test-your-bot-in-teams"></a><span data-ttu-id="b1495-179">Testar seu bot no Teams</span><span class="sxs-lookup"><span data-stu-id="b1495-179">Test your bot in Teams</span></span>

<span data-ttu-id="b1495-180">Agora você pode testar o bot no Teams.</span><span class="sxs-lookup"><span data-stu-id="b1495-180">Now you can test the bot in Teams.</span></span> <span data-ttu-id="b1495-181">Selecione um canal na equipe em que você registrou seu aplicativo e digite `@your-bot-name` .</span><span class="sxs-lookup"><span data-stu-id="b1495-181">Select a channel in the team where you registered your app and type `@your-bot-name`.</span></span> <span data-ttu-id="b1495-182">Isso é chamado de **\@ menção**.</span><span class="sxs-lookup"><span data-stu-id="b1495-182">This is called an **\@mention**.</span></span> <span data-ttu-id="b1495-183">O bot responde a qualquer mensagem enviada.</span><span class="sxs-lookup"><span data-stu-id="b1495-183">The bot replies to any message that you send.</span></span>

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png" />

### <a name="test-your-messaging-extension"></a><span data-ttu-id="b1495-184">Testar sua extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="b1495-184">Test your messaging extension</span></span>

<span data-ttu-id="b1495-185">Para testar sua extensão de mensagens, você pode selecionar **...** abaixo da caixa de entrada no seu exibição de conversa.</span><span class="sxs-lookup"><span data-stu-id="b1495-185">To test your messaging extension, you can select **...** below the input box in your conversation view.</span></span> <span data-ttu-id="b1495-186">Um menu com o **aplicativo "Hello World"** é exibido.</span><span class="sxs-lookup"><span data-stu-id="b1495-186">A menu with the **'Hello World'** app is displayed.</span></span> <span data-ttu-id="b1495-187">Quando você o seleciona, um conjunto de textos aleatórios é exibido.</span><span class="sxs-lookup"><span data-stu-id="b1495-187">When you select it, a set of random texts is displayed.</span></span> <span data-ttu-id="b1495-188">Você pode selecionar um dos textos aleatórios e que é inserido em sua conversa.</span><span class="sxs-lookup"><span data-stu-id="b1495-188">You can select one of the random text and that is inserted into your conversation.</span></span>

<img width="530px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="530px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

<span data-ttu-id="b1495-189">Selecione um dos textos aleatórios.</span><span class="sxs-lookup"><span data-stu-id="b1495-189">Select one of the random text.</span></span> <span data-ttu-id="b1495-190">Um cartão formatado e pronto para enviar com sua própria mensagem é mostrado.</span><span class="sxs-lookup"><span data-stu-id="b1495-190">A card formatted and ready to send with your own message is shown.</span></span>

<img width="530px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
