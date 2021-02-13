---
title: 'Tutorial : Criar seu primeiro aplicativo usando C #'
description: Saiba como começar a criar aplicativos do Microsoft Teams com C# ou .NET.
keywords: getting started .net c# csharp
ms.custom: scenarios:getting-started; languages:ASP.NET,C#
ms.topic: tutorial
ms.date: 11/09/2018
ms.openlocfilehash: b37a8d555117e38383504dc99d82d564439a3ebf
ms.sourcegitcommit: e3b6bc31059ec77de5fbef9b15c17d358abbca0f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2021
ms.locfileid: "50231516"
---
# <a name="create-your-first-teams-app-using-c-or-net"></a><span data-ttu-id="845f8-104">Crie seu primeiro aplicativo do Teams usando C# ou .NET</span><span class="sxs-lookup"><span data-stu-id="845f8-104">Create your first Teams app using C# or .NET</span></span>

<span data-ttu-id="845f8-105">Este tutorial ajuda você a criar um aplicativo do Microsoft Teams em C# ou .NET.</span><span class="sxs-lookup"><span data-stu-id="845f8-105">This tutorial helps you to create a Microsoft Teams app using C# or .NET.</span></span>

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a><span data-ttu-id="845f8-106">Obter pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="845f8-106">Get prerequisites</span></span>

<span data-ttu-id="845f8-107">Para concluir este tutorial, você precisa obter as seguintes ferramentas:</span><span class="sxs-lookup"><span data-stu-id="845f8-107">To complete this tutorial, you need to get the following tools:</span></span>

- [<span data-ttu-id="845f8-108">Instalar o Git</span><span class="sxs-lookup"><span data-stu-id="845f8-108">Install Git</span></span>](https://git-scm.com/downloads)
- <span data-ttu-id="845f8-109">[Instale o Visual Studio.](https://www.visualstudio.com/downloads/)</span><span class="sxs-lookup"><span data-stu-id="845f8-109">[Install Visual Studio](https://www.visualstudio.com/downloads/).</span></span> <span data-ttu-id="845f8-110">Você pode instalar a edição gratuita da comunidade.</span><span class="sxs-lookup"><span data-stu-id="845f8-110">You can install the free community edition.</span></span>

<span data-ttu-id="845f8-111">Durante a instalação, se houver uma opção para adicionar `git` ao PATH, escolha-a.</span><span class="sxs-lookup"><span data-stu-id="845f8-111">During installation, if there is an option to add `git` to the PATH, choose it.</span></span>

<span data-ttu-id="845f8-112">Em uma janela de terminal, execute o seguinte comando para verificar sua `git` instalação:</span><span class="sxs-lookup"><span data-stu-id="845f8-112">In a terminal window, run the following command to verify your `git` installation:</span></span>

```bash
$ git --version
git version 2.17.1.windows.2

```

> [!NOTE]
> <span data-ttu-id="845f8-113">Use uma janela de terminal adequada em sua plataforma.</span><span class="sxs-lookup"><span data-stu-id="845f8-113">Use a suitable terminal window on your platform.</span></span> <span data-ttu-id="845f8-114">Esses exemplos usam Bash, mas são executados na maioria das plataformas.</span><span class="sxs-lookup"><span data-stu-id="845f8-114">These examples use Bash but run on most platforms.</span></span>

<span data-ttu-id="845f8-115">Certifique-se de iniciar a versão mais recente do Visual Studio e instalar as atualizações.</span><span class="sxs-lookup"><span data-stu-id="845f8-115">Make sure to launch the latest version of Visual Studio and install any updates.</span></span>

<span data-ttu-id="845f8-116">Você pode usar a mesma janela de terminal para executar os comandos neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="845f8-116">You can use the same terminal window to run the commands in this tutorial.</span></span>

<a name="DownloadSample"></a>

## <a name="download-the-sample"></a><span data-ttu-id="845f8-117">Baixar o exemplo</span><span class="sxs-lookup"><span data-stu-id="845f8-117">Download the sample</span></span>

<span data-ttu-id="845f8-118">Você pode começar com um [Hello, World simples!](https://github.com/OfficeDev/msteams-samples-hello-world-csharp)</span><span class="sxs-lookup"><span data-stu-id="845f8-118">You can get started with a simple [Hello, World!](https://github.com/OfficeDev/msteams-samples-hello-world-csharp)</span></span> <span data-ttu-id="845f8-119">em C#.</span><span class="sxs-lookup"><span data-stu-id="845f8-119">sample in C#.</span></span> <span data-ttu-id="845f8-120">Em uma janela de terminal, execute o seguinte comando para clonar o repositório de exemplo para sua máquina local:</span><span class="sxs-lookup"><span data-stu-id="845f8-120">In a terminal window, run the following command to clone the sample repository to your local machine:</span></span>

```bash
git clone https://github.com/OfficeDev/msteams-samples-hello-world-csharp.git
```

> [!TIP]
> <span data-ttu-id="845f8-121">Você pode [bifurcar](https://help.github.com/articles/fork-a-repo/) [esse repositório para](https://github.com/OfficeDev/msteams-samples-hello-world-csharp) modificar e salvar suas alterações no GitHub para referência.</span><span class="sxs-lookup"><span data-stu-id="845f8-121">You can [fork](https://help.github.com/articles/fork-a-repo/) this [repo](https://github.com/OfficeDev/msteams-samples-hello-world-csharp) to modify and save your changes to GitHub for reference.</span></span>

<a name="BuildRun"></a>

## <a name="build-and-run-the-sample"></a><span data-ttu-id="845f8-122">Criar e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="845f8-122">Build and run the sample</span></span>

<span data-ttu-id="845f8-123">Depois que o repo for clonado, use o Visual Studio para abrir o arquivo de solução no diretório raiz do exemplo e `Microsoft.Teams.Samples.HelloWorld.sln` `Build Solution` selecione no `Build` menu.</span><span class="sxs-lookup"><span data-stu-id="845f8-123">After the repo is cloned, use Visual Studio to open the solution file `Microsoft.Teams.Samples.HelloWorld.sln` from the root directory of the sample and select `Build Solution` from the `Build` menu.</span></span> <span data-ttu-id="845f8-124">Para executar o exemplo, `F5` pressione ou escolha no `Start Debugging` `Debug` menu.</span><span class="sxs-lookup"><span data-stu-id="845f8-124">To run the sample press `F5` or choose `Start Debugging` from the `Debug` menu.</span></span>

<span data-ttu-id="845f8-125">Quando o aplicativo é iniciado, uma janela do navegador é aberta com a raiz do aplicativo iniciado.</span><span class="sxs-lookup"><span data-stu-id="845f8-125">When the app starts, a browser window opens with the root of the app launched.</span></span> <span data-ttu-id="845f8-126">Você pode navegar até as URLs a seguir para verificar se todas as URLs do aplicativo estão sendo carregadas:</span><span class="sxs-lookup"><span data-stu-id="845f8-126">You can navigate to the following URLs to verify that all the app URLs are loading:</span></span>

- [https://localhost:44327/](https://localhost:44327/)
- [https://localhost:44327/hello](https://localhost:44327/hello)
- [https://localhost:44327/first](https://localhost:44327/first)
- <span data-ttu-id="845f8-127">[https://localhost:44327/second]https://localhost:44327/second)</span><span class="sxs-lookup"><span data-stu-id="845f8-127">[https://localhost:44327/second]https://localhost:44327/second)</span></span>

<a name="HostSample"></a>

> [!Note]
> <span data-ttu-id="845f8-128">Se você receber um `Could not find a part of the path … bin\roslyn\csc.exe` erro, atualize o pacote com o `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r` comando.</span><span class="sxs-lookup"><span data-stu-id="845f8-128">If you receive an error `Could not find a part of the path … bin\roslyn\csc.exe`, update the package with the command `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r`.</span></span> <span data-ttu-id="845f8-129">Para obter mais informações, [consulte esta pergunta no StackOverflow](https://stackoverflow.com/questions/32780315).</span><span class="sxs-lookup"><span data-stu-id="845f8-129">For more information, see [this question on StackOverflow](https://stackoverflow.com/questions/32780315).</span></span>

## <a name="host-the-sample-app"></a><span data-ttu-id="845f8-130">Hospedar o aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="845f8-130">Host the sample app</span></span>

<span data-ttu-id="845f8-131">Os aplicativos no Microsoft Teams são aplicativos Web que fornecem um ou mais recursos.</span><span class="sxs-lookup"><span data-stu-id="845f8-131">Apps in Microsoft Teams are web applications that provide one or more capabilities.</span></span> <span data-ttu-id="845f8-132">Para a plataforma do Teams carregar seu aplicativo, seu aplicativo deve estar acessível pela Internet.</span><span class="sxs-lookup"><span data-stu-id="845f8-132">For the Teams platform to load your app, your app must be reachable from the internet.</span></span> <span data-ttu-id="845f8-133">Para tornar seu aplicativo acessível pela Internet, você precisa hospedar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="845f8-133">To make your app reachable from the internet, you need to host your app.</span></span> <span data-ttu-id="845f8-134">Você pode hospedá-lo no Microsoft Azure gratuitamente ou criar um túnel para o processo local em sua máquina de desenvolvimento `ngrok` usando.</span><span class="sxs-lookup"><span data-stu-id="845f8-134">You can either host it in Microsoft Azure for free or create a tunnel to the local process on your development machine using `ngrok`.</span></span> <span data-ttu-id="845f8-135">Quando você terminar de hospedar seu aplicativo, anote sua URL raiz.</span><span class="sxs-lookup"><span data-stu-id="845f8-135">When you finish hosting your app, note its root URL.</span></span> <span data-ttu-id="845f8-136">Por exemplo, `https://yourteamsapp.ngrok.io` ou `https://yourteamsapp.azurewebsites.net` .</span><span class="sxs-lookup"><span data-stu-id="845f8-136">For example, `https://yourteamsapp.ngrok.io` or `https://yourteamsapp.azurewebsites.net`.</span></span>

### <a name="tunnel-using-ngrok"></a><span data-ttu-id="845f8-137">Túnel usando ngrok</span><span class="sxs-lookup"><span data-stu-id="845f8-137">Tunnel using ngrok</span></span>

<span data-ttu-id="845f8-138">Para testes rápidos, você pode executar o aplicativo no computador local e criar um túnel para ele por meio de um ponto de extremidade da Web.</span><span class="sxs-lookup"><span data-stu-id="845f8-138">For quick testing, you can run the app on your local machine and create a tunnel to it through a web endpoint.</span></span> <span data-ttu-id="845f8-139">[ngrok](https://ngrok.com) é uma ferramenta gratuita com a qual você pode obter um endereço da Web, como `https://d0ac14a5.ngrok.io` .</span><span class="sxs-lookup"><span data-stu-id="845f8-139">[ngrok](https://ngrok.com) is a free tool with which you can get a web address such as `https://d0ac14a5.ngrok.io`.</span></span> <span data-ttu-id="845f8-140">Você pode [baixar e instalar](https://ngrok.com/download) o ngrok.</span><span class="sxs-lookup"><span data-stu-id="845f8-140">You can [download and install](https://ngrok.com/download) ngrok.</span></span> <span data-ttu-id="845f8-141">Certifique-se de adicioná-lo a um local em seu `PATH` .</span><span class="sxs-lookup"><span data-stu-id="845f8-141">Make sure you add it to a location in your `PATH`.</span></span>

<span data-ttu-id="845f8-142">Depois de instalar o ngrok, abra uma nova janela de terminal e execute o seguinte comando para criar um túnel:</span><span class="sxs-lookup"><span data-stu-id="845f8-142">After you install ngrok, open a new terminal window and run the following command to create a tunnel:</span></span>

```bash
ngrok http 44327 -host-header=localhost:44327
```

<span data-ttu-id="845f8-143">O exemplo usa a porta 44327 para especificá-la.</span><span class="sxs-lookup"><span data-stu-id="845f8-143">The sample uses port 44327 be sure to specify it.</span></span>

<span data-ttu-id="845f8-144">O Ngrok escuta solicitações da Internet e as encaminha para seu aplicativo em execução na porta 44327.</span><span class="sxs-lookup"><span data-stu-id="845f8-144">Ngrok listens to requests from the internet and routes them to your app running on port 44327.</span></span> <span data-ttu-id="845f8-145">Para verificar, abra o navegador e vá `https://d0ac14a5.ngrok.io/hello` para carregar a página hello do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="845f8-145">To verify, open your browser and go to `https://d0ac14a5.ngrok.io/hello` to load your app's hello page.</span></span> <span data-ttu-id="845f8-146">Em vez dessa URL, use o endereço de encaminhamento exibido pelo ngrok na sessão do console.</span><span class="sxs-lookup"><span data-stu-id="845f8-146">Instead of this URL, use the forwarding address displayed by ngrok in your console session.</span></span>

> [!NOTE]
> <span data-ttu-id="845f8-147">Se você usou uma porta diferente na etapa de [com](#build-and-run-the-sample) build e de executar, certifique-se de usar o mesmo número de porta para configurar o `ngrok` túnel.</span><span class="sxs-lookup"><span data-stu-id="845f8-147">If you have used a different port in the [build and run](#build-and-run-the-sample) step, make sure you use the same port number to setup the `ngrok` tunnel.</span></span>

> [!TIP]
> <span data-ttu-id="845f8-148">É uma boa ideia executar em `ngrok` uma janela de terminal diferente.</span><span class="sxs-lookup"><span data-stu-id="845f8-148">It is a good idea to run `ngrok` in a different terminal window.</span></span> <span data-ttu-id="845f8-149">Isso é feito para impedir que o ngrok seja executado sem interferir no aplicativo, que você precisa parar, recriar e executar de novo.</span><span class="sxs-lookup"><span data-stu-id="845f8-149">This is done to keep ngrok from running without interfering with the app, which you have to stop, rebuild, and rerun.</span></span> <span data-ttu-id="845f8-150">A `ngrok` sessão fornece informações úteis de depuração nesta janela.</span><span class="sxs-lookup"><span data-stu-id="845f8-150">The `ngrok` session provides useful debugging information in this window.</span></span>

<span data-ttu-id="845f8-151">O aplicativo só está disponível durante a sessão atual em seu computador de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="845f8-151">The app is only available during the current session on your development machine.</span></span> <span data-ttu-id="845f8-152">Se o computador for desligado ou ficar em sleep, o serviço não estará mais disponível.</span><span class="sxs-lookup"><span data-stu-id="845f8-152">If the machine is shut down or goes to sleep, the service is no longer available.</span></span> <span data-ttu-id="845f8-153">Lembre-se disso quando compartilhar o aplicativo para teste com outros usuários.</span><span class="sxs-lookup"><span data-stu-id="845f8-153">Remember this when you share the app for testing to other users.</span></span> <span data-ttu-id="845f8-154">Se você tiver que reiniciar o serviço, o aplicativo retornará um novo endereço e você deverá atualizar todos os locais que usam esse endereço.</span><span class="sxs-lookup"><span data-stu-id="845f8-154">If you have to restart the service, the app returns a new address and you must update every location that uses that address.</span></span> <span data-ttu-id="845f8-155">A versão paga do ngrok não tem essa limitação.</span><span class="sxs-lookup"><span data-stu-id="845f8-155">The paid version of ngrok does not have this limitation.</span></span>

### <a name="host-in-azure"></a><span data-ttu-id="845f8-156">Host no Azure</span><span class="sxs-lookup"><span data-stu-id="845f8-156">Host in Azure</span></span>

<span data-ttu-id="845f8-157">O Microsoft Azure hospeda seu aplicativo .NET em uma camada gratuita usando a infraestrutura compartilhada.</span><span class="sxs-lookup"><span data-stu-id="845f8-157">Microsoft Azure hosts your .NET application on a free tier using shared infrastructure.</span></span> <span data-ttu-id="845f8-158">Isso é suficiente para executar o `Hello World` exemplo.</span><span class="sxs-lookup"><span data-stu-id="845f8-158">This is sufficient to run the `Hello World` sample.</span></span> <span data-ttu-id="845f8-159">Para obter mais informações, consulte [a criação de uma nova conta gratuita.](https://azure.microsoft.com/free/)</span><span class="sxs-lookup"><span data-stu-id="845f8-159">For more information, see [creating a new free account](https://azure.microsoft.com/free/).</span></span>

<span data-ttu-id="845f8-160">O Visual Studio tem suporte integrado para implantação de aplicativos para diferentes provedores, incluindo o Azure.</span><span class="sxs-lookup"><span data-stu-id="845f8-160">Visual Studio has built-in support for app deployment to different providers, including Azure.</span></span>

<img width="530px" alt="Visual Studio" src="~/assets/images/get-started/publishtoazure1.png"/>

[!include [Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-the-credentials-for-your-hosted-app"></a><span data-ttu-id="845f8-161">Atualizar as credenciais do aplicativo hospedado</span><span class="sxs-lookup"><span data-stu-id="845f8-161">Update the credentials for your hosted app</span></span>

<span data-ttu-id="845f8-162">O aplicativo de exemplo requer que as seguintes variáveis de ambiente sejam definidas com os valores que você anoou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="845f8-162">The sample app requires the following environment variables to be set to the values you made a note of earlier.</span></span>

<span data-ttu-id="845f8-163">Abra o appsettings.jsno arquivo.</span><span class="sxs-lookup"><span data-stu-id="845f8-163">Open up the appsettings.json file.</span></span> <span data-ttu-id="845f8-164">Atualize o *valor de MicrosoftAppId* com sua ID de Bot que você salvou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="845f8-164">Update the *MicrosoftAppId* value with your Bot ID that you saved earlier.</span></span> <span data-ttu-id="845f8-165">Atualize *o MicrosoftAppPassword* com a senha de Bot salva anteriormente.</span><span class="sxs-lookup"><span data-stu-id="845f8-165">Update the *MicrosoftAppPassword* with the Bot password you saved earlier.</span></span>

<img width="560px" alt="Setting the keys" src="~/assets/images/get-started/get-started-net-azure-add-keys.png"/>

<span data-ttu-id="845f8-166">Depois que essas alterações são feitas, recomando o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="845f8-166">Once these changes are made, rebuild the app.</span></span> <span data-ttu-id="845f8-167">Se você estiver usando o ngrok, execute o aplicativo localmente e, se estiver hospedando no Azure, reimplante o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="845f8-167">If you are using ngrok, run the app locally, and if you are hosting in Azure redeploy the app.</span></span>

## <a name="configure-the-app-tab"></a><span data-ttu-id="845f8-168">Configurar a guia do aplicativo</span><span class="sxs-lookup"><span data-stu-id="845f8-168">Configure the app tab</span></span>

<span data-ttu-id="845f8-169">Depois de instalar o aplicativo em uma equipe, você precisará configurá-lo para mostrar conteúdo.</span><span class="sxs-lookup"><span data-stu-id="845f8-169">Once you install the app into a team, you will need to configure it to show content.</span></span> <span data-ttu-id="845f8-170">Vá para um canal na equipe em que você instalou o aplicativo de exemplo e clique no botão **'+'** para adicionar uma nova guia. Em seguida, você `Hello World` pode escolher na lista Adicionar **uma** guia.</span><span class="sxs-lookup"><span data-stu-id="845f8-170">Go to a channel in the team where you installed the sample app and click on the **'+'** button to add a new tab. You can then choose `Hello World` from the **Add a tab** list.</span></span> <span data-ttu-id="845f8-171">Em seguida, você receberá uma caixa de diálogo de configuração.</span><span class="sxs-lookup"><span data-stu-id="845f8-171">You will then be presented with a configuration dialog.</span></span> <span data-ttu-id="845f8-172">Essa caixa de diálogo permitirá que você escolha qual guia exibir neste canal.</span><span class="sxs-lookup"><span data-stu-id="845f8-172">This dialog will let you choose which tab to display in this channel.</span></span> <span data-ttu-id="845f8-173">Depois de selecionar a guia e clicar na guia, você poderá ver a `Save` guia carregada com a guia `Hello World` escolhida.</span><span class="sxs-lookup"><span data-stu-id="845f8-173">Once you select the tab and click on `Save` then you can see the `Hello World` tab loaded with the tab you chose.</span></span>

<img width="530px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png" />

### <a name="test-your-bot-in-teams"></a><span data-ttu-id="845f8-174">Testar seu bot no Teams</span><span class="sxs-lookup"><span data-stu-id="845f8-174">Test your bot in Teams</span></span>

<span data-ttu-id="845f8-175">Agora você pode interagir com o bot no Teams.</span><span class="sxs-lookup"><span data-stu-id="845f8-175">You can now interact with the bot in Teams.</span></span> <span data-ttu-id="845f8-176">Escolha um canal na equipe onde você registrou seu aplicativo e `@your-bot-name` digite.</span><span class="sxs-lookup"><span data-stu-id="845f8-176">Choose a channel in the team where you registered your app and type `@your-bot-name`.</span></span> <span data-ttu-id="845f8-177">Isso é chamado de **\@ menção.**</span><span class="sxs-lookup"><span data-stu-id="845f8-177">This is called an **\@mention**.</span></span> <span data-ttu-id="845f8-178">Qualquer mensagem enviada para o bot será enviada de volta como uma resposta.</span><span class="sxs-lookup"><span data-stu-id="845f8-178">Whatever message you send to the bot will be sent back to you as a reply.</span></span>

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png" />

### <a name="test-your-messaging-extension"></a><span data-ttu-id="845f8-179">Testar sua extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="845f8-179">Test your messaging extension</span></span>

<span data-ttu-id="845f8-180">Para testar sua extensão de mensagens, você pode clicar nos três pontos abaixo da caixa de entrada na exibição de conversa.</span><span class="sxs-lookup"><span data-stu-id="845f8-180">To test your messaging extension, you can click on the three dots below the input box in your conversation view.</span></span> <span data-ttu-id="845f8-181">Um menu será aberto com o **aplicativo "Hello World"** nele.</span><span class="sxs-lookup"><span data-stu-id="845f8-181">A menu will pop up with the **'Hello World'** app in it.</span></span> <span data-ttu-id="845f8-182">Ao clicar nele, você verá vários textos aleatórios aparecendo.</span><span class="sxs-lookup"><span data-stu-id="845f8-182">When you click it, you will see a bunch of random texts showing up.</span></span> <span data-ttu-id="845f8-183">Você pode escolher qualquer um deles e ele será inserido em sua conversa.</span><span class="sxs-lookup"><span data-stu-id="845f8-183">You can choose any one of them and it is inserted into your conversation.</span></span>

<img width="530px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="530px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

<span data-ttu-id="845f8-184">Escolha um dos textos aleatórios e você verá um cartão formatado e pronto para enviar com sua própria mensagem na parte inferior.</span><span class="sxs-lookup"><span data-stu-id="845f8-184">Choose one of the random texts, and you will see a card formatted and ready to send with your own message at the bottom.</span></span>

<img width="530px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
