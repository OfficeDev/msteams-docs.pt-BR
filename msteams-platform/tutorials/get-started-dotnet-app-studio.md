---
title: Introdução ao C#/.NET
description: Introdução à criação de aplicativos ótimos no Microsoft Teams usando o C#/.NET
keywords: Introdução ao .net c# Csharp
ms.custom: scenarios:getting-started; languages:ASP.NET,C#
ms.topic: tutorial
ms.date: 11/09/2018
ms.openlocfilehash: 61237cd3178fcb41357230536827f732faf65ee4
ms.sourcegitcommit: 510ae42f72798fb24ddef0afa771ecd9d38e5348
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2020
ms.locfileid: "43550956"
---
# <a name="get-started-on-the-microsoft-teams-platform-with-cnet-and-app-studio"></a><span data-ttu-id="917fb-104">Introdução à plataforma do Microsoft Teams com o C#/.NET e o app Studio</span><span class="sxs-lookup"><span data-stu-id="917fb-104">Get started on the Microsoft Teams platform with C#/.NET and App Studio</span></span>

<span data-ttu-id="917fb-105">A plataforma de desenvolvedor do [Microsoft Teams](/microsoftteams/) facilita a extensão de equipes e a integração de seus próprios aplicativos e serviços diretamente no espaço de trabalho do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="917fb-105">The [Microsoft Teams](/microsoftteams/) developer platform makes it easy for you to extend Teams and integrate your own applications and services seamlessly into the Teams workspace.</span></span> <span data-ttu-id="917fb-106">Esses aplicativos podem ser distribuídos para sua empresa ou para o Teams em todo o mundo.</span><span class="sxs-lookup"><span data-stu-id="917fb-106">These apps can then be distributed to your enterprise or for teams around the world.</span></span>

<span data-ttu-id="917fb-107">Para estender o Microsoft Teams, você precisará criar um aplicativo do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="917fb-107">To extend Microsoft Teams, you will need to create a Microsoft Teams app.</span></span> <span data-ttu-id="917fb-108">Um aplicativo do Microsoft Teams é um aplicativo Web que você hospeda.</span><span class="sxs-lookup"><span data-stu-id="917fb-108">A Microsoft Teams app is a web application that you host.</span></span> <span data-ttu-id="917fb-109">Esse aplicativo pode ser integrado ao espaço de trabalho do usuário no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="917fb-109">This app can then be integrated into the user's workspace in Teams.</span></span>

<span data-ttu-id="917fb-110">Este tutorial ajuda você a começar a criar um aplicativo do Microsoft Teams usando C# no .NET.</span><span class="sxs-lookup"><span data-stu-id="917fb-110">This tutorial helps you get started creating a Microsoft Teams app using C# on .NET.</span></span> <span data-ttu-id="917fb-111">Você pode testar o aplicativo carregando-o em uma equipe para a qual tenha permissões ou em um locatário de teste criado usando o programa de desenvolvedor do Office.</span><span class="sxs-lookup"><span data-stu-id="917fb-111">You can test the app by loading it into a Team that you have permissions for, or into a test tenant created using the Office Developer Program.</span></span>

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a><span data-ttu-id="917fb-112">Obter pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="917fb-112">Get prerequisites</span></span>

<span data-ttu-id="917fb-113">Para concluir este tutorial, você precisa obter as seguintes ferramentas:</span><span class="sxs-lookup"><span data-stu-id="917fb-113">To complete this tutorial, you need to get the following tools:</span></span>

- [<span data-ttu-id="917fb-114">Instalar o Git</span><span class="sxs-lookup"><span data-stu-id="917fb-114">Install Git</span></span>](https://git-scm.com/downloads)
- <span data-ttu-id="917fb-115">[Instale o Visual Studio](https://www.visualstudio.com/downloads/).</span><span class="sxs-lookup"><span data-stu-id="917fb-115">[Install Visual Studio](https://www.visualstudio.com/downloads/).</span></span> <span data-ttu-id="917fb-116">Você pode instalar a edição gratuita da Comunidade.</span><span class="sxs-lookup"><span data-stu-id="917fb-116">You can install the free community edition.</span></span>

<span data-ttu-id="917fb-117">Se você vir uma opção para adicionar `git` ao caminho durante a instalação, escolha fazer isso.</span><span class="sxs-lookup"><span data-stu-id="917fb-117">If you see an option to add `git` to the PATH during installation, choose to do so.</span></span> <span data-ttu-id="917fb-118">Será útil.</span><span class="sxs-lookup"><span data-stu-id="917fb-118">It will be handy.</span></span>

<span data-ttu-id="917fb-119">Verifique a `git` instalação executando o seguinte em uma janela de terminal:</span><span class="sxs-lookup"><span data-stu-id="917fb-119">Verify your `git` installation by running the following in a terminal window:</span></span>
> [!NOTE]
> <span data-ttu-id="917fb-120">Use a janela do terminal com a qual você se sente mais confortável em sua plataforma.</span><span class="sxs-lookup"><span data-stu-id="917fb-120">Use the terminal window that you are most comfortable with on your platform.</span></span> <span data-ttu-id="917fb-121">Estes exemplos usam o bash, mas serão executados na maioria das plataformas.</span><span class="sxs-lookup"><span data-stu-id="917fb-121">These examples use Bash, but will run on most platforms.</span></span>

```bash
$ git --version
git version 2.17.1.windows.2

```

<span data-ttu-id="917fb-122">Certifique-se de iniciar a versão mais recente do Visual Studio e instalar as atualizações, se mostradas.</span><span class="sxs-lookup"><span data-stu-id="917fb-122">Make sure to launch the latest version of Visual Studio and install any updates if shown.</span></span>

<span data-ttu-id="917fb-123">Você pode continuar a usar esta janela de terminal para executar os comandos a seguir neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="917fb-123">You can continue to use this terminal window to run the commands that follow in this tutorial.</span></span>

<a name="DownloadSample"></a>

## <a name="download-the-sample"></a><span data-ttu-id="917fb-124">Baixar o exemplo</span><span class="sxs-lookup"><span data-stu-id="917fb-124">Download the sample</span></span>

<span data-ttu-id="917fb-125">Fornecemos um simples [Olá, mundo!](https://github.com/OfficeDev/msteams-samples-hello-world-csharp)</span><span class="sxs-lookup"><span data-stu-id="917fb-125">We have provided a simple [Hello, World!](https://github.com/OfficeDev/msteams-samples-hello-world-csharp)</span></span> <span data-ttu-id="917fb-126">exemplo em C# para ajudá-lo a começar.</span><span class="sxs-lookup"><span data-stu-id="917fb-126">sample in C# to get you started.</span></span> <span data-ttu-id="917fb-127">Em uma janela de terminal, execute o seguinte comando para clonar o repositório de exemplo para sua máquina local:</span><span class="sxs-lookup"><span data-stu-id="917fb-127">In a terminal window, run the following command to clone the sample repository to your local machine:</span></span>

```bash
git clone https://github.com/OfficeDev/msteams-samples-hello-world-csharp.git
```

> [!TIP]
> <span data-ttu-id="917fb-128">Você pode [bifurcar](https://help.github.com/articles/fork-a-repo/) este [repositório](https://github.com/OfficeDev/msteams-samples-hello-world-csharp) se quiser modificar e fazer check-in de suas alterações no GitHub para referência futura.</span><span class="sxs-lookup"><span data-stu-id="917fb-128">You can [fork](https://help.github.com/articles/fork-a-repo/) this [repo](https://github.com/OfficeDev/msteams-samples-hello-world-csharp) if you want to modify and check in your changes to GitHub for future reference.</span></span>

<a name="BuildRun"></a>

## <a name="build-and-run-the-sample"></a><span data-ttu-id="917fb-129">Criar e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="917fb-129">Build and run the sample</span></span>

<span data-ttu-id="917fb-130">Depois que o repositório é clonado, use o Visual Studio para abrir o `Microsoft.Teams.Samples.HelloWorld.sln` arquivo de solução no diretório raiz do exemplo e `Build Solution` clique no `Build` menu.</span><span class="sxs-lookup"><span data-stu-id="917fb-130">Once the repo is cloned, use Visual Studio to open the solution file `Microsoft.Teams.Samples.HelloWorld.sln` from the root directory of the sample and click `Build Solution` from the `Build` menu.</span></span> <span data-ttu-id="917fb-131">Você pode executar o exemplo pressionando `F5` ou escolhendo `Start Debugging` o `Debug` menu.</span><span class="sxs-lookup"><span data-stu-id="917fb-131">You can run the sample by pressing `F5` or choosing `Start Debugging` from the `Debug` menu.</span></span>

<span data-ttu-id="917fb-132">Quando o aplicativo for iniciado, você verá uma janela do navegador aberta com a raiz do aplicativo iniciado.</span><span class="sxs-lookup"><span data-stu-id="917fb-132">When the app starts, you will see a browser window open with the root of the app launched.</span></span> <span data-ttu-id="917fb-133">Você pode navegar até as seguintes URLs para verificar se todas as URLs de aplicativo estão sendo carregadas:</span><span class="sxs-lookup"><span data-stu-id="917fb-133">You can navigate to the following URLs to verify that all the app URLs are loading:</span></span>

- [http://localhost:3333](http://localhost:3333)
- [http://localhost:3333/hello](http://localhost:3333/hello)
- [http://localhost:3333/first](http://localhost:3333/first)
- [http://localhost:3333/second](http://localhost:3333/second)

<a name="HostSample"></a>

> [!Note]
> <span data-ttu-id="917fb-134">Se você receber uma mensagem de `Could not find a part of the path … bin\roslyn\csc.exe`erro, tente atualizar o pacote com o `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r`comando.</span><span class="sxs-lookup"><span data-stu-id="917fb-134">If you receive an error like `Could not find a part of the path … bin\roslyn\csc.exe`, try updating the package with the command `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r`.</span></span> <span data-ttu-id="917fb-135">Confira [esta pergunta sobre StackOverflow](https://stackoverflow.com/questions/32780315) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="917fb-135">See [this question on StackOverflow](https://stackoverflow.com/questions/32780315) for additional details.</span></span>

## <a name="host-the-sample-app"></a><span data-ttu-id="917fb-136">Hospedar o aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="917fb-136">Host the sample app</span></span>

<span data-ttu-id="917fb-137">Lembre-se de que aplicativos no Microsoft Teams são aplicativos da Web que expõem um ou mais recursos.</span><span class="sxs-lookup"><span data-stu-id="917fb-137">Remember that apps in Microsoft Teams are web applications exposing one or more capabilities.</span></span> <span data-ttu-id="917fb-138">Para que a plataforma do teams carregue seu aplicativo, seu aplicativo deve estar acessível pela Internet.</span><span class="sxs-lookup"><span data-stu-id="917fb-138">For the Teams platform to load your app, your app must be reachable from the internet.</span></span> <span data-ttu-id="917fb-139">Para tornar seu aplicativo alcançável da Internet, você precisa hospedar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="917fb-139">To make your app reachable from the internet, you need to host your app.</span></span> <span data-ttu-id="917fb-140">Você pode hospedá-lo no Microsoft Azure gratuitamente ou criar um túnel para o processo local em sua máquina de desenvolvimento usando `ngrok`o.</span><span class="sxs-lookup"><span data-stu-id="917fb-140">You can either host it in Microsoft Azure for free or create a tunnel to the local process on your development machine using `ngrok`.</span></span> <span data-ttu-id="917fb-141">Quando você terminar de hospedar seu aplicativo, anote sua URL raiz.</span><span class="sxs-lookup"><span data-stu-id="917fb-141">When you finish hosting your app make a note of its root URL.</span></span> <span data-ttu-id="917fb-142">Ele terá uma aparência semelhante a `https://yourteamsapp.ngrok.io` : `https://yourteamsapp.azurewebsites.net`ou.</span><span class="sxs-lookup"><span data-stu-id="917fb-142">It will look something like: `https://yourteamsapp.ngrok.io` or `https://yourteamsapp.azurewebsites.net`.</span></span>

### <a name="tunnel-using-ngrok"></a><span data-ttu-id="917fb-143">Túnel usando ngrok</span><span class="sxs-lookup"><span data-stu-id="917fb-143">Tunnel using ngrok</span></span>

<span data-ttu-id="917fb-144">Para testes rápidos, você pode executar o aplicativo na sua máquina local e criar um túnel para ele por meio de um ponto de extremidade da Web.</span><span class="sxs-lookup"><span data-stu-id="917fb-144">For quick testing you can run the app on your local machine and create a tunnel to it through a web endpoint.</span></span> <span data-ttu-id="917fb-145">o [ngrok](https://ngrok.com) é uma ferramenta gratuita que permite que você faça exatamente isso.</span><span class="sxs-lookup"><span data-stu-id="917fb-145">[ngrok](https://ngrok.com) is a free tool that lets you do just that.</span></span> <span data-ttu-id="917fb-146">Com o ngrok, você pode obter um endereço da `https://d0ac14a5.ngrok.io` Web como (esta URL é apenas um exemplo).</span><span class="sxs-lookup"><span data-stu-id="917fb-146">With ngrok you can get a web address such as `https://d0ac14a5.ngrok.io` (this URL is just an example).</span></span> <span data-ttu-id="917fb-147">Você pode [baixar e instalar](https://ngrok.com/download) o ngrok para o seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="917fb-147">You can [download and install](https://ngrok.com/download) ngrok for your environment.</span></span> <span data-ttu-id="917fb-148">Certifique-se de adicioná-lo a um local `PATH`no seu.</span><span class="sxs-lookup"><span data-stu-id="917fb-148">Make sure you add it to a location in your `PATH`.</span></span>

<span data-ttu-id="917fb-149">Depois de instalá-lo, você pode abrir uma nova janela de terminal e executar o seguinte comando para criar um túnel.</span><span class="sxs-lookup"><span data-stu-id="917fb-149">Once you install it, you can open a new terminal window and run the following command to create a tunnel.</span></span> <span data-ttu-id="917fb-150">O exemplo usa a porta 3333, portanto, certifique-se de especificá-la aqui.</span><span class="sxs-lookup"><span data-stu-id="917fb-150">The sample uses port 3333, so be sure to specify it here.</span></span>

```bash
ngrok http 3333 -host-header=localhost:3333
```

<span data-ttu-id="917fb-151">O Ngrok ouvirá as solicitações da Internet e irá encaminhá-las para seu aplicativo em execução na porta 3333.</span><span class="sxs-lookup"><span data-stu-id="917fb-151">Ngrok will listen to requests from the internet and will route them to your app running on port 3333.</span></span> <span data-ttu-id="917fb-152">Você pode verificar abrindo seu navegador e indo `https://d0ac14a5.ngrok.io/hello` para carregar a página de saudação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="917fb-152">You can verify by opening your browser and going to `https://d0ac14a5.ngrok.io/hello` to load your app's hello page.</span></span> <span data-ttu-id="917fb-153">Certifique-se de usar o endereço de encaminhamento exibido pelo ngrok em sua sessão de console, em vez desta URL.</span><span class="sxs-lookup"><span data-stu-id="917fb-153">Please be sure to use the forwarding address displayed by ngrok in your console session instead of this URL.</span></span>

> [!NOTE]
> <span data-ttu-id="917fb-154">Se você tiver usado uma porta diferente na etapa [criar e executar](#build-and-run-the-sample) acima, certifique-se de usar o mesmo número de porta para instalar `ngrok` o túnel.</span><span class="sxs-lookup"><span data-stu-id="917fb-154">If you have used a different port in the [build and run](#build-and-run-the-sample) step above, make sure you use the same port number to setup the `ngrok` tunnel.</span></span>
> [!TIP]
> <span data-ttu-id="917fb-155">É uma boa ideia executar `ngrok` em uma janela diferente do terminal para mantê-la em execução sem interferir no aplicativo, que pode ser mais tarde interrompido, recriar e executar novamente.</span><span class="sxs-lookup"><span data-stu-id="917fb-155">It is a good idea to run `ngrok` in a different terminal window to keep it running without interfering with the app which you might later have to stop, rebuild and rerun.</span></span> <span data-ttu-id="917fb-156">A `ngrok` sessão retornará informações de depuração úteis nesta janela.</span><span class="sxs-lookup"><span data-stu-id="917fb-156">The `ngrok` session will return useful debugging information in this window.</span></span>

<span data-ttu-id="917fb-157">O aplicativo só estará disponível durante a sessão atual em sua máquina de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="917fb-157">The app will only be available during the current session on your development machine.</span></span> <span data-ttu-id="917fb-158">Se o computador estiver desligado ou chegar à suspensão, o serviço não estará mais disponível.</span><span class="sxs-lookup"><span data-stu-id="917fb-158">If the machine is shut down or goes to sleep the service will no longer be available.</span></span> <span data-ttu-id="917fb-159">Lembre-se disso ao compartilhar o aplicativo para teste por outros usuários.</span><span class="sxs-lookup"><span data-stu-id="917fb-159">Remember this when sharing the app for testing by other users.</span></span> <span data-ttu-id="917fb-160">Se for necessário reiniciar o serviço, ele retornará um novo endereço e você terá que atualizar cada lugar que usa esse endereço.</span><span class="sxs-lookup"><span data-stu-id="917fb-160">If you have to restart the service it will return a new address and you will have to update every place that uses that address.</span></span> <span data-ttu-id="917fb-161">A versão paga do Ngrok não tem essa limitação.</span><span class="sxs-lookup"><span data-stu-id="917fb-161">The paid version of Ngrok does not have this limitation.</span></span>

### <a name="host-in-azure"></a><span data-ttu-id="917fb-162">Host no Azure</span><span class="sxs-lookup"><span data-stu-id="917fb-162">Host in Azure</span></span>

<span data-ttu-id="917fb-163">O Microsoft Azure permite que você hospede seu aplicativo .NET em uma camada gratuita usando a infraestrutura compartilhada.</span><span class="sxs-lookup"><span data-stu-id="917fb-163">Microsoft Azure lets you host your .NET application on a free tier using shared infrastructure.</span></span> <span data-ttu-id="917fb-164">Isso será suficiente para executar este `Hello World` exemplo.</span><span class="sxs-lookup"><span data-stu-id="917fb-164">This will be sufficient to run this `Hello World` sample.</span></span> <span data-ttu-id="917fb-165">Consulte [criar uma nova conta gratuita](https://azure.microsoft.com/free/) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="917fb-165">See [creating a new free account](https://azure.microsoft.com/free/) for more information.</span></span>

<span data-ttu-id="917fb-166">O Visual Studio oferece suporte interno à implantação de aplicativos para diferentes provedores, incluindo o Azure.</span><span class="sxs-lookup"><span data-stu-id="917fb-166">Visual Studio has built-in support for app deployment to different providers, including Azure.</span></span>

<img width="530px" src="~/assets/images/get-started/publishtoazure1.png" title="Visual Studio"/>

[!include[Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-the-credentials-for-your-hosted-app"></a><span data-ttu-id="917fb-168">Atualizar as credenciais para seu aplicativo hospedado</span><span class="sxs-lookup"><span data-stu-id="917fb-168">Update the credentials for your hosted app</span></span>

<span data-ttu-id="917fb-169">O aplicativo de exemplo requer que as seguintes variáveis de ambiente sejam definidas para os valores que você fez antes.</span><span class="sxs-lookup"><span data-stu-id="917fb-169">The sample app requires the following environment variables to be set to the values you made a note of earlier.</span></span>

<span data-ttu-id="917fb-170">Abra o arquivo Web. config e localize a seção *appSettings* .</span><span class="sxs-lookup"><span data-stu-id="917fb-170">Open up the web.config file and find the *appSettings* section.</span></span> <span data-ttu-id="917fb-171">Atualize o valor *MicrosoftAppId* com a ID de bot que você salvou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="917fb-171">Update the *MicrosoftAppId* value with your Bot ID that you saved earlier.</span></span> <span data-ttu-id="917fb-172">Atualize o *MicrosoftAppPassword* com a senha de bot que você salvou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="917fb-172">Update the *MicrosoftAppPassword* with the Bot password you saved earlier.</span></span>

<img width="560px" src="~/assets/images/get-started/get-started-net-azure-add-keys.png" title="definir as chaves"/>

<span data-ttu-id="917fb-174">Depois que essas alterações forem feitas, reconstrua o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="917fb-174">Once these changes are made, rebuild the app.</span></span> <span data-ttu-id="917fb-175">Se você estiver usando o ngrok, execute o aplicativo localmente e, se estiver hospedando no Azure, reimplante o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="917fb-175">If you are using ngrok, run the app locally, and if you are hosting in Azure redeploy the app.</span></span>

## <a name="configure-the-app-tab"></a><span data-ttu-id="917fb-176">Configurar a guia aplicativo</span><span class="sxs-lookup"><span data-stu-id="917fb-176">Configure the app tab</span></span>

<span data-ttu-id="917fb-177">Após instalar o aplicativo em uma equipe, você precisará configurá-lo para exibir o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="917fb-177">Once you install the app into a team, you will need to configure it to show content.</span></span> <span data-ttu-id="917fb-178">Vá para um canal na equipe em que você instalou o exemplo de aplicativo e clique no botão **"+"** para adicionar uma nova guia. Em seguida, você `Hello World` pode escolher na lista **Adicionar uma guia** .</span><span class="sxs-lookup"><span data-stu-id="917fb-178">Go to a channel in the team where you installed the sample app and click on the **'+'** button to add a new tab. You can then choose `Hello World` from the **Add a tab** list.</span></span> <span data-ttu-id="917fb-179">Em seguida, será exibida uma caixa de diálogo de configuração.</span><span class="sxs-lookup"><span data-stu-id="917fb-179">You will then be presented with a configuration dialog.</span></span> <span data-ttu-id="917fb-180">Esta caixa de diálogo permitirá que você escolha qual guia será exibida neste canal.</span><span class="sxs-lookup"><span data-stu-id="917fb-180">This dialog will let you choose which tab to display in this channel.</span></span> <span data-ttu-id="917fb-181">Depois de selecionar a guia e clicar em `Save` , você poderá ver a `Hello World` guia carregada com a guia escolhida.</span><span class="sxs-lookup"><span data-stu-id="917fb-181">Once you select the tab and click on `Save` then you can see the `Hello World` tab loaded with the tab you chose.</span></span>

<img width="530px" src="~/assets/images/samples-hello-world-tab-configure.png" title="Captura de tela da configuração" />

### <a name="test-your-bot-in-teams"></a><span data-ttu-id="917fb-183">Testar seu bot no Teams</span><span class="sxs-lookup"><span data-stu-id="917fb-183">Test your bot in Teams</span></span>

<span data-ttu-id="917fb-184">Agora você pode interagir com o bot no Teams.</span><span class="sxs-lookup"><span data-stu-id="917fb-184">You can now interact with the bot in Teams.</span></span> <span data-ttu-id="917fb-185">Escolha um canal na equipe onde você registrou seu aplicativo e digite `@your-bot-name`.</span><span class="sxs-lookup"><span data-stu-id="917fb-185">Choose a channel in the team where you registered your app, and type `@your-bot-name`.</span></span> <span data-ttu-id="917fb-186">Isso é chamado de \*\* \@menção\*\*.</span><span class="sxs-lookup"><span data-stu-id="917fb-186">This is called an **\@mention**.</span></span> <span data-ttu-id="917fb-187">Qualquer mensagem enviada ao bot será enviada de volta para você como resposta.</span><span class="sxs-lookup"><span data-stu-id="917fb-187">Whatever message you send to the bot will be sent back to you as a reply.</span></span>

<img width="450px" title="Respostas de bot" src="~/assets/images/samples-hello-world-bot.png" />

### <a name="test-your-messaging-extension"></a><span data-ttu-id="917fb-189">Testar sua extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="917fb-189">Test your messaging extension</span></span>

<span data-ttu-id="917fb-190">Para testar sua extensão de mensagens, você pode clicar nos três pontos abaixo da caixa de entrada no modo de exibição de conversa.</span><span class="sxs-lookup"><span data-stu-id="917fb-190">To test your messaging extension, you can click on the three dots below the input box in your conversation view.</span></span> <span data-ttu-id="917fb-191">Um menu será exibido com o aplicativo **"Olá mundo"** .</span><span class="sxs-lookup"><span data-stu-id="917fb-191">A menu will pop up with the **'Hello World'** app in it.</span></span> <span data-ttu-id="917fb-192">Quando você clicar nele, verá um monte de textos aleatórios aparecendo.</span><span class="sxs-lookup"><span data-stu-id="917fb-192">When you click it, you will see a bunch of random texts showing up.</span></span> <span data-ttu-id="917fb-193">Você pode escolher qualquer uma delas e ela será inserida na conversa.</span><span class="sxs-lookup"><span data-stu-id="917fb-193">You can choose any one of them and it will be inserted it into your conversation.</span></span>

<img width="530px" title="Menu de extensão de mensagens" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="530px" title="Resultado da extensão de mensagens" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

<span data-ttu-id="917fb-196">Escolha um dos textos aleatórios, e você verá um cartão formatado e pronto para enviar com sua própria mensagem na parte inferior.</span><span class="sxs-lookup"><span data-stu-id="917fb-196">Choose one of the random texts, and you will see a card formatted and ready to send with your own message at the bottom.</span></span>

<img width="530px" title="Envio de extensão de mensagens" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
