---
title: 'Tutorial : Criar seu primeiro aplicativo usando C #'
description: Saiba como começar a criar aplicativos do Microsoft Teams com C#/.NET.
keywords: getting started .net c# csharp
ms.custom: scenarios:getting-started; languages:ASP.NET,C#
ms.topic: tutorial
ms.date: 11/09/2018
ms.openlocfilehash: c28c4d00c375b8e37f82c343eec2c5405ae0c1c8
ms.sourcegitcommit: fa64b83c0b534bf7a89f256880d5b5ca193e4b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2021
ms.locfileid: "50037036"
---
# <a name="create-your-first-microsoft-teams-app-using-c"></a><span data-ttu-id="1781f-104">Criar seu primeiro aplicativo Do Microsoft Teams usando C #</span><span class="sxs-lookup"><span data-stu-id="1781f-104">Create your first Microsoft Teams app using C#</span></span>

<span data-ttu-id="1781f-105">Este tutorial ajuda você a começar a criar um aplicativo do Microsoft Teams em C# no .NET.</span><span class="sxs-lookup"><span data-stu-id="1781f-105">This tutorial helps you get started creating a Microsoft Teams app using C# on .NET.</span></span>

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a><span data-ttu-id="1781f-106">Obter pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="1781f-106">Get prerequisites</span></span>

<span data-ttu-id="1781f-107">Para concluir este tutorial, você precisa obter as seguintes ferramentas:</span><span class="sxs-lookup"><span data-stu-id="1781f-107">To complete this tutorial, you need to get the following tools:</span></span>

- [<span data-ttu-id="1781f-108">Instalar o Git</span><span class="sxs-lookup"><span data-stu-id="1781f-108">Install Git</span></span>](https://git-scm.com/downloads)
- <span data-ttu-id="1781f-109">[Instale o Visual Studio.](https://www.visualstudio.com/downloads/)</span><span class="sxs-lookup"><span data-stu-id="1781f-109">[Install Visual Studio](https://www.visualstudio.com/downloads/).</span></span> <span data-ttu-id="1781f-110">Você pode instalar a edição gratuita da comunidade.</span><span class="sxs-lookup"><span data-stu-id="1781f-110">You can install the free community edition.</span></span>

<span data-ttu-id="1781f-111">Se você vir uma opção para adicionar `git` ao PATH durante a instalação, opte por fazer isso.</span><span class="sxs-lookup"><span data-stu-id="1781f-111">If you see an option to add `git` to the PATH during installation, choose to do so.</span></span> <span data-ttu-id="1781f-112">Ele será útil.</span><span class="sxs-lookup"><span data-stu-id="1781f-112">It will be handy.</span></span>

<span data-ttu-id="1781f-113">Verifique sua `git` instalação executando o seguinte em uma janela de terminal:</span><span class="sxs-lookup"><span data-stu-id="1781f-113">Verify your `git` installation by running the following in a terminal window:</span></span>
> [!NOTE]
> <span data-ttu-id="1781f-114">Use a janela de terminal com a que você mais se sente confortável em sua plataforma.</span><span class="sxs-lookup"><span data-stu-id="1781f-114">Use the terminal window that you are most comfortable with on your platform.</span></span> <span data-ttu-id="1781f-115">Esses exemplos usam Bash, mas serão executados na maioria das plataformas.</span><span class="sxs-lookup"><span data-stu-id="1781f-115">These examples use Bash, but will run on most platforms.</span></span>

```bash
$ git --version
git version 2.17.1.windows.2

```

<span data-ttu-id="1781f-116">Certifique-se de iniciar a versão mais recente do Visual Studio e instalar as atualizações, se mostrado.</span><span class="sxs-lookup"><span data-stu-id="1781f-116">Make sure to launch the latest version of Visual Studio and install any updates if shown.</span></span>

<span data-ttu-id="1781f-117">Você pode continuar a usar essa janela de terminal para executar os comandos a seguir neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="1781f-117">You can continue to use this terminal window to run the commands that follow in this tutorial.</span></span>

<a name="DownloadSample"></a>

## <a name="download-the-sample"></a><span data-ttu-id="1781f-118">Baixar o exemplo</span><span class="sxs-lookup"><span data-stu-id="1781f-118">Download the sample</span></span>

<span data-ttu-id="1781f-119">Fornecemos um [Hello, World simples!](https://github.com/OfficeDev/msteams-samples-hello-world-csharp)</span><span class="sxs-lookup"><span data-stu-id="1781f-119">We have provided a simple [Hello, World!](https://github.com/OfficeDev/msteams-samples-hello-world-csharp)</span></span> <span data-ttu-id="1781f-120">em C# para começar.</span><span class="sxs-lookup"><span data-stu-id="1781f-120">sample in C# to get you started.</span></span> <span data-ttu-id="1781f-121">Em uma janela de terminal, execute o seguinte comando para clonar o repositório de exemplo para sua máquina local:</span><span class="sxs-lookup"><span data-stu-id="1781f-121">In a terminal window, run the following command to clone the sample repository to your local machine:</span></span>

```bash
git clone https://github.com/OfficeDev/msteams-samples-hello-world-csharp.git
```

> [!TIP]
> <span data-ttu-id="1781f-122">Você pode [bifurcar](https://help.github.com/articles/fork-a-repo/) [esse repositório](https://github.com/OfficeDev/msteams-samples-hello-world-csharp) se quiser modificar e fazer check-in de suas alterações no GitHub para referência futura.</span><span class="sxs-lookup"><span data-stu-id="1781f-122">You can [fork](https://help.github.com/articles/fork-a-repo/) this [repo](https://github.com/OfficeDev/msteams-samples-hello-world-csharp) if you want to modify and check in your changes to GitHub for future reference.</span></span>

<a name="BuildRun"></a>

## <a name="build-and-run-the-sample"></a><span data-ttu-id="1781f-123">Criar e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="1781f-123">Build and run the sample</span></span>

<span data-ttu-id="1781f-124">Depois que o repo for clonado, use o Visual Studio para abrir o arquivo de solução no diretório raiz do exemplo e clique `Microsoft.Teams.Samples.HelloWorld.sln` `Build Solution` no `Build` menu.</span><span class="sxs-lookup"><span data-stu-id="1781f-124">Once the repo is cloned, use Visual Studio to open the solution file `Microsoft.Teams.Samples.HelloWorld.sln` from the root directory of the sample and click `Build Solution` from the `Build` menu.</span></span> <span data-ttu-id="1781f-125">Você pode executar o exemplo pressionando `F5` ou escolhendo `Start Debugging` no `Debug` menu.</span><span class="sxs-lookup"><span data-stu-id="1781f-125">You can run the sample by pressing `F5` or choosing `Start Debugging` from the `Debug` menu.</span></span>

<span data-ttu-id="1781f-126">Quando o aplicativo for iniciado, você verá uma janela do navegador aberta com a raiz do aplicativo iniciada.</span><span class="sxs-lookup"><span data-stu-id="1781f-126">When the app starts, you will see a browser window open with the root of the app launched.</span></span> <span data-ttu-id="1781f-127">Você pode navegar até as URLs a seguir para verificar se todas as URLs do aplicativo estão sendo carregadas:</span><span class="sxs-lookup"><span data-stu-id="1781f-127">You can navigate to the following URLs to verify that all the app URLs are loading:</span></span>

- [http://localhost:3333](http://localhost:3333)
- [http://localhost:3333/hello](http://localhost:3333/hello)
- [http://localhost:3333/first](http://localhost:3333/first)
- [http://localhost:3333/second](http://localhost:3333/second)

<a name="HostSample"></a>

> [!Note]
> <span data-ttu-id="1781f-128">Se você receber um erro como `Could not find a part of the path … bin\roslyn\csc.exe` , tente atualizar o pacote com o comando `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r` .</span><span class="sxs-lookup"><span data-stu-id="1781f-128">If you receive an error like `Could not find a part of the path … bin\roslyn\csc.exe`, try updating the package with the command `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r`.</span></span> <span data-ttu-id="1781f-129">Veja [esta pergunta no StackOverflow para](https://stackoverflow.com/questions/32780315) obter detalhes adicionais.</span><span class="sxs-lookup"><span data-stu-id="1781f-129">See [this question on StackOverflow](https://stackoverflow.com/questions/32780315) for additional details.</span></span>

## <a name="host-the-sample-app"></a><span data-ttu-id="1781f-130">Hospedar o aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="1781f-130">Host the sample app</span></span>

<span data-ttu-id="1781f-131">Lembre-se de que os aplicativos no Microsoft Teams são aplicativos Web expondo um ou mais recursos.</span><span class="sxs-lookup"><span data-stu-id="1781f-131">Remember that apps in Microsoft Teams are web applications exposing one or more capabilities.</span></span> <span data-ttu-id="1781f-132">Para a plataforma do Teams carregar seu aplicativo, seu aplicativo deve estar acessível pela Internet.</span><span class="sxs-lookup"><span data-stu-id="1781f-132">For the Teams platform to load your app, your app must be reachable from the internet.</span></span> <span data-ttu-id="1781f-133">Para tornar seu aplicativo acessível pela Internet, você precisa hospedar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1781f-133">To make your app reachable from the internet, you need to host your app.</span></span> <span data-ttu-id="1781f-134">Você pode hospedá-lo no Microsoft Azure gratuitamente ou criar um túnel para o processo local em sua máquina de desenvolvimento `ngrok` usando.</span><span class="sxs-lookup"><span data-stu-id="1781f-134">You can either host it in Microsoft Azure for free or create a tunnel to the local process on your development machine using `ngrok`.</span></span> <span data-ttu-id="1781f-135">Quando você terminar de hospedar seu aplicativo, anote sua URL raiz.</span><span class="sxs-lookup"><span data-stu-id="1781f-135">When you finish hosting your app make a note of its root URL.</span></span> <span data-ttu-id="1781f-136">Ele será parecido com: `https://yourteamsapp.ngrok.io` ou `https://yourteamsapp.azurewebsites.net` .</span><span class="sxs-lookup"><span data-stu-id="1781f-136">It will look something like: `https://yourteamsapp.ngrok.io` or `https://yourteamsapp.azurewebsites.net`.</span></span>

### <a name="tunnel-using-ngrok"></a><span data-ttu-id="1781f-137">Túnel usando ngrok</span><span class="sxs-lookup"><span data-stu-id="1781f-137">Tunnel using ngrok</span></span>

<span data-ttu-id="1781f-138">Para testes rápidos, você pode executar o aplicativo em seu computador local e criar um túnel para ele por meio de um ponto de extremidade da Web.</span><span class="sxs-lookup"><span data-stu-id="1781f-138">For quick testing you can run the app on your local machine and create a tunnel to it through a web endpoint.</span></span> <span data-ttu-id="1781f-139">[O ngrok](https://ngrok.com) é uma ferramenta gratuita que permite que você faça exatamente isso.</span><span class="sxs-lookup"><span data-stu-id="1781f-139">[ngrok](https://ngrok.com) is a free tool that lets you do just that.</span></span> <span data-ttu-id="1781f-140">Com ngrok, você pode obter um endereço da Web como `https://d0ac14a5.ngrok.io` (essa URL é apenas um exemplo).</span><span class="sxs-lookup"><span data-stu-id="1781f-140">With ngrok you can get a web address such as `https://d0ac14a5.ngrok.io` (this URL is just an example).</span></span> <span data-ttu-id="1781f-141">Você pode [baixar e instalar](https://ngrok.com/download) o ngrok para seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="1781f-141">You can [download and install](https://ngrok.com/download) ngrok for your environment.</span></span> <span data-ttu-id="1781f-142">Certifique-se de adicioná-lo a um local em seu `PATH` .</span><span class="sxs-lookup"><span data-stu-id="1781f-142">Make sure you add it to a location in your `PATH`.</span></span>

<span data-ttu-id="1781f-143">Depois de instalá-lo, você pode abrir uma nova janela de terminal e executar o seguinte comando para criar um túnel.</span><span class="sxs-lookup"><span data-stu-id="1781f-143">Once you install it, you can open a new terminal window and run the following command to create a tunnel.</span></span> <span data-ttu-id="1781f-144">O exemplo usa a porta 3333, portanto, certifique-se de especificá-la aqui.</span><span class="sxs-lookup"><span data-stu-id="1781f-144">The sample uses port 3333, so be sure to specify it here.</span></span>

```bash
ngrok http 3333 -host-header=localhost:3333
```

<span data-ttu-id="1781f-145">O Ngrok escutará solicitações da Internet e as encaminhará para seu aplicativo em execução na porta 3333.</span><span class="sxs-lookup"><span data-stu-id="1781f-145">Ngrok will listen to requests from the internet and will route them to your app running on port 3333.</span></span> <span data-ttu-id="1781f-146">Você pode verificar abrindo o navegador e `https://d0ac14a5.ngrok.io/hello` carregando a página hello do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1781f-146">You can verify by opening your browser and going to `https://d0ac14a5.ngrok.io/hello` to load your app's hello page.</span></span> <span data-ttu-id="1781f-147">Certifique-se de usar o endereço de encaminhamento exibido pelo ngrok na sessão do console em vez dessa URL.</span><span class="sxs-lookup"><span data-stu-id="1781f-147">Please be sure to use the forwarding address displayed by ngrok in your console session instead of this URL.</span></span>

> [!NOTE]
> <span data-ttu-id="1781f-148">Se você tiver usado uma [](#build-and-run-the-sample) porta diferente na com build e execute a etapa acima, certifique-se de usar o mesmo número de porta para configurar o `ngrok` túnel.</span><span class="sxs-lookup"><span data-stu-id="1781f-148">If you have used a different port in the [build and run](#build-and-run-the-sample) step above, make sure you use the same port number to setup the `ngrok` tunnel.</span></span>
> [!TIP]
> <span data-ttu-id="1781f-149">É uma boa ideia executar em uma janela de terminal diferente para mantê-la em execução sem interferir no aplicativo, que talvez seja preciso parar, recriar `ngrok` e executar outra vez.</span><span class="sxs-lookup"><span data-stu-id="1781f-149">It is a good idea to run `ngrok` in a different terminal window to keep it running without interfering with the app which you might later have to stop, rebuild and rerun.</span></span> <span data-ttu-id="1781f-150">A `ngrok` sessão retornará informações úteis de depuração nesta janela.</span><span class="sxs-lookup"><span data-stu-id="1781f-150">The `ngrok` session will return useful debugging information in this window.</span></span>

<span data-ttu-id="1781f-151">O aplicativo só estará disponível durante a sessão atual em sua máquina de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="1781f-151">The app will only be available during the current session on your development machine.</span></span> <span data-ttu-id="1781f-152">Se o computador for desligado ou for para sleep, o serviço não estará mais disponível.</span><span class="sxs-lookup"><span data-stu-id="1781f-152">If the machine is shut down or goes to sleep the service will no longer be available.</span></span> <span data-ttu-id="1781f-153">Lembre-se disso ao compartilhar o aplicativo para teste por outros usuários.</span><span class="sxs-lookup"><span data-stu-id="1781f-153">Remember this when sharing the app for testing by other users.</span></span> <span data-ttu-id="1781f-154">Se você tiver que reiniciar o serviço, ele retornará um novo endereço e você terá que atualizar todos os lugares que usam esse endereço.</span><span class="sxs-lookup"><span data-stu-id="1781f-154">If you have to restart the service it will return a new address and you will have to update every place that uses that address.</span></span> <span data-ttu-id="1781f-155">A versão paga do Ngrok não tem essa limitação.</span><span class="sxs-lookup"><span data-stu-id="1781f-155">The paid version of Ngrok does not have this limitation.</span></span>

### <a name="host-in-azure"></a><span data-ttu-id="1781f-156">Host no Azure</span><span class="sxs-lookup"><span data-stu-id="1781f-156">Host in Azure</span></span>

<span data-ttu-id="1781f-157">O Microsoft Azure permite que você hospede seu aplicativo .NET em uma camada gratuita usando a infraestrutura compartilhada.</span><span class="sxs-lookup"><span data-stu-id="1781f-157">Microsoft Azure lets you host your .NET application on a free tier using shared infrastructure.</span></span> <span data-ttu-id="1781f-158">Isso será suficiente para executar este `Hello World` exemplo.</span><span class="sxs-lookup"><span data-stu-id="1781f-158">This will be sufficient to run this `Hello World` sample.</span></span> <span data-ttu-id="1781f-159">Confira [a criação de uma nova conta gratuita](https://azure.microsoft.com/free/) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="1781f-159">See [creating a new free account](https://azure.microsoft.com/free/) for more information.</span></span>

<span data-ttu-id="1781f-160">O Visual Studio tem suporte integrado para implantação de aplicativos para diferentes provedores, incluindo o Azure.</span><span class="sxs-lookup"><span data-stu-id="1781f-160">Visual Studio has built-in support for app deployment to different providers, including Azure.</span></span>

<img width="530px" alt="Visual Studio" src="~/assets/images/get-started/publishtoazure1.png"/>

[!include [Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-the-credentials-for-your-hosted-app"></a><span data-ttu-id="1781f-161">Atualizar as credenciais para seu aplicativo hospedado</span><span class="sxs-lookup"><span data-stu-id="1781f-161">Update the credentials for your hosted app</span></span>

<span data-ttu-id="1781f-162">O aplicativo de exemplo requer que as seguintes variáveis de ambiente sejam definidas com os valores que você anoou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1781f-162">The sample app requires the following environment variables to be set to the values you made a note of earlier.</span></span>

<span data-ttu-id="1781f-163">Abra o appsettings.jsno arquivo.</span><span class="sxs-lookup"><span data-stu-id="1781f-163">Open up the appsettings.json file.</span></span> <span data-ttu-id="1781f-164">Atualize o *valor de MicrosoftAppId* com sua ID de Bot que você salvou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1781f-164">Update the *MicrosoftAppId* value with your Bot ID that you saved earlier.</span></span> <span data-ttu-id="1781f-165">Atualize *o MicrosoftAppPassword* com a senha de Bot salva anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1781f-165">Update the *MicrosoftAppPassword* with the Bot password you saved earlier.</span></span>

<img width="560px" alt="Setting the keys" src="~/assets/images/get-started/get-started-net-azure-add-keys.png"/>

<span data-ttu-id="1781f-166">Depois que essas alterações são feitas, recomando o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1781f-166">Once these changes are made, rebuild the app.</span></span> <span data-ttu-id="1781f-167">Se você estiver usando o ngrok, execute o aplicativo localmente e, se estiver hospedando no Azure, reimplante o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1781f-167">If you are using ngrok, run the app locally, and if you are hosting in Azure redeploy the app.</span></span>

## <a name="configure-the-app-tab"></a><span data-ttu-id="1781f-168">Configurar a guia do aplicativo</span><span class="sxs-lookup"><span data-stu-id="1781f-168">Configure the app tab</span></span>

<span data-ttu-id="1781f-169">Depois de instalar o aplicativo em uma equipe, você precisará configurá-lo para mostrar conteúdo.</span><span class="sxs-lookup"><span data-stu-id="1781f-169">Once you install the app into a team, you will need to configure it to show content.</span></span> <span data-ttu-id="1781f-170">Vá para um canal na equipe em que você instalou o aplicativo de exemplo e clique no botão **'+'** para adicionar uma nova guia. Em seguida, você `Hello World` pode escolher na lista Adicionar **uma** guia.</span><span class="sxs-lookup"><span data-stu-id="1781f-170">Go to a channel in the team where you installed the sample app and click on the **'+'** button to add a new tab. You can then choose `Hello World` from the **Add a tab** list.</span></span> <span data-ttu-id="1781f-171">Em seguida, você receberá uma caixa de diálogo de configuração.</span><span class="sxs-lookup"><span data-stu-id="1781f-171">You will then be presented with a configuration dialog.</span></span> <span data-ttu-id="1781f-172">Essa caixa de diálogo permitirá que você escolha qual guia exibir neste canal.</span><span class="sxs-lookup"><span data-stu-id="1781f-172">This dialog will let you choose which tab to display in this channel.</span></span> <span data-ttu-id="1781f-173">Depois de selecionar a guia e clicar, você poderá ver a `Save` guia carregada com a guia `Hello World` escolhida.</span><span class="sxs-lookup"><span data-stu-id="1781f-173">Once you select the tab and click on `Save` then you can see the `Hello World` tab loaded with the tab you chose.</span></span>

<img width="530px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png" />

### <a name="test-your-bot-in-teams"></a><span data-ttu-id="1781f-174">Testar seu bot no Teams</span><span class="sxs-lookup"><span data-stu-id="1781f-174">Test your bot in Teams</span></span>

<span data-ttu-id="1781f-175">Agora você pode interagir com o bot no Teams.</span><span class="sxs-lookup"><span data-stu-id="1781f-175">You can now interact with the bot in Teams.</span></span> <span data-ttu-id="1781f-176">Escolha um canal na equipe onde você registrou seu aplicativo e digite `@your-bot-name` .</span><span class="sxs-lookup"><span data-stu-id="1781f-176">Choose a channel in the team where you registered your app, and type `@your-bot-name`.</span></span> <span data-ttu-id="1781f-177">Isso é chamado de **\@ menção.**</span><span class="sxs-lookup"><span data-stu-id="1781f-177">This is called an **\@mention**.</span></span> <span data-ttu-id="1781f-178">Qualquer mensagem enviada para o bot será enviada de volta como uma resposta.</span><span class="sxs-lookup"><span data-stu-id="1781f-178">Whatever message you send to the bot will be sent back to you as a reply.</span></span>

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png" />

### <a name="test-your-messaging-extension"></a><span data-ttu-id="1781f-179">Testar sua extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="1781f-179">Test your messaging extension</span></span>

<span data-ttu-id="1781f-180">Para testar sua extensão de mensagens, você pode clicar nos três pontos abaixo da caixa de entrada na exibição de conversa.</span><span class="sxs-lookup"><span data-stu-id="1781f-180">To test your messaging extension, you can click on the three dots below the input box in your conversation view.</span></span> <span data-ttu-id="1781f-181">Um menu será aberto com o **aplicativo "Hello World"** nele.</span><span class="sxs-lookup"><span data-stu-id="1781f-181">A menu will pop up with the **'Hello World'** app in it.</span></span> <span data-ttu-id="1781f-182">Ao clicar nele, você verá vários textos aleatórios aparecendo.</span><span class="sxs-lookup"><span data-stu-id="1781f-182">When you click it, you will see a bunch of random texts showing up.</span></span> <span data-ttu-id="1781f-183">Você pode escolher qualquer um deles e ele será inserido na conversa.</span><span class="sxs-lookup"><span data-stu-id="1781f-183">You can choose any one of them and it will be inserted it into your conversation.</span></span>

<img width="530px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="530px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

<span data-ttu-id="1781f-184">Escolha um dos textos aleatórios e você verá um cartão formatado e pronto para enviar com sua própria mensagem na parte inferior.</span><span class="sxs-lookup"><span data-stu-id="1781f-184">Choose one of the random texts, and you will see a card formatted and ready to send with your own message at the bottom.</span></span>

<img width="530px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
