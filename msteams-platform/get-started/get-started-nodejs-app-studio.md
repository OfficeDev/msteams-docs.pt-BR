---
title: Tutorial - Crie seu primeiro aplicativo usando Node.js
description: Saiba como começar a criar Microsoft Teams aplicativos com Node.js.
keywords: getting started node.js nodejs App Studio
ms.topic: tutorial
localization_priority: Normal
ms.custom: scenarios:getting-started; languages:JavaScript,Node.js
ms.openlocfilehash: 84c3452c739f67c2908d698b627b5651ff9d5d7a
ms.sourcegitcommit: 9d63611974ba8a7e7f19ceea35e50189a2e90434
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2021
ms.locfileid: "53254337"
---
# <a name="build-your-first-microsoft-teams-app-using-nodejs"></a><span data-ttu-id="4a14c-104">Crie seu primeiro aplicativo Microsoft Teams usando Node.js</span><span class="sxs-lookup"><span data-stu-id="4a14c-104">Build your first Microsoft Teams app using Node.js</span></span>

<span data-ttu-id="4a14c-105">Neste tutorial, você aprenderá a criar seu primeiro aplicativo Microsoft Teams usando Node.js.</span><span class="sxs-lookup"><span data-stu-id="4a14c-105">In this tutorial, you will learn how to build your very first Microsoft Teams app using Node.js.</span></span> <span data-ttu-id="4a14c-106">Ele também orienta você pelas etapas para:</span><span class="sxs-lookup"><span data-stu-id="4a14c-106">It also walks you through the steps to:</span></span> 

1. [<span data-ttu-id="4a14c-107">Preparar seu ambiente</span><span class="sxs-lookup"><span data-stu-id="4a14c-107">Prepare your environment</span></span>](#prepare-environment)
1. [<span data-ttu-id="4a14c-108">Obter pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="4a14c-108">Get prerequisites</span></span>](#GetPrerequisites)
1. [<span data-ttu-id="4a14c-109">Baixar o exemplo</span><span class="sxs-lookup"><span data-stu-id="4a14c-109">Download the sample</span></span>](#DownloadSample)
1. [<span data-ttu-id="4a14c-110">Criar e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="4a14c-110">Build and run the sample</span></span>](#BuildRun)
1. [<span data-ttu-id="4a14c-111">Hospedar o aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="4a14c-111">Host the sample app</span></span>](#HostSample)
1. [<span data-ttu-id="4a14c-112">Atualizar as credenciais do aplicativo hospedado</span><span class="sxs-lookup"><span data-stu-id="4a14c-112">Update the credentials for your hosted app</span></span>](#updatecredentials)
1. [<span data-ttu-id="4a14c-113">Configurar a guia do aplicativo</span><span class="sxs-lookup"><span data-stu-id="4a14c-113">Configure the app tab</span></span>](#ConfigureTheAppTab)

<a name="prepare-environment"></a>

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

### <a name="download-and-host-your-app"></a><span data-ttu-id="4a14c-114">Baixar e hospedar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="4a14c-114">Download and host your app</span></span>

<span data-ttu-id="4a14c-115">Siga estas etapas para baixar e hospedar um aplicativo simples de "hello world" Teams.</span><span class="sxs-lookup"><span data-stu-id="4a14c-115">Follow these steps to download and host a simple "hello world" app in Teams.</span></span>

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a><span data-ttu-id="4a14c-116">Obter pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="4a14c-116">Get prerequisites</span></span>

<span data-ttu-id="4a14c-117">Para concluir este tutorial, você precisa das seguintes ferramentas.</span><span class="sxs-lookup"><span data-stu-id="4a14c-117">To complete this tutorial, you need the following tools.</span></span> <span data-ttu-id="4a14c-118">Se você ainda não os tiver, poderá instalá-los a partir desses links.</span><span class="sxs-lookup"><span data-stu-id="4a14c-118">If you don't already have them you can install them from these links.</span></span>

- [<span data-ttu-id="4a14c-119">Git</span><span class="sxs-lookup"><span data-stu-id="4a14c-119">Git</span></span>](https://git-scm.com/downloads)
- [<span data-ttu-id="4a14c-120">Node.js e NPM</span><span class="sxs-lookup"><span data-stu-id="4a14c-120">Node.js and NPM</span></span>](https://nodejs.org/)
- <span data-ttu-id="4a14c-121">Obter qualquer editor de texto ou IDE.</span><span class="sxs-lookup"><span data-stu-id="4a14c-121">Get any text editor or IDE.</span></span> <span data-ttu-id="4a14c-122">Você pode instalar e usar [Visual Studio Code](https://code.visualstudio.com/download) gratuitamente.</span><span class="sxs-lookup"><span data-stu-id="4a14c-122">You can install and use [Visual Studio Code](https://code.visualstudio.com/download) for free.</span></span>

<span data-ttu-id="4a14c-123">Se você vir opções para adicionar , , e ao PATH durante a `git` `node` `npm` `code` instalação, selecione as opções.</span><span class="sxs-lookup"><span data-stu-id="4a14c-123">If you see options to add `git`, `node`, `npm`, and `code` to the PATH during installation, select the options.</span></span> 

<span data-ttu-id="4a14c-124">Verifique se as ferramentas estão disponíveis executando o seguinte em uma janela de terminal:</span><span class="sxs-lookup"><span data-stu-id="4a14c-124">Verify that the tools are available by running the following in a terminal window:</span></span>

> [!NOTE]
> <span data-ttu-id="4a14c-125">Use a janela de terminal com a que você está mais confortável em sua plataforma.</span><span class="sxs-lookup"><span data-stu-id="4a14c-125">Use the terminal window that you are most comfortable with on your platform.</span></span> <span data-ttu-id="4a14c-126">Esses exemplos usam Bash (que está incluído no Git), mas esses scripts serão executados na maioria das plataformas.</span><span class="sxs-lookup"><span data-stu-id="4a14c-126">These examples use Bash (which is included in Git), but these scripts will run on most platforms.</span></span>

```bash
$ git --version
git version 2.19.0.windows.1

$ node -v
v8.9.3

$ npm -v
5.5.1

$ gulp -v
CLI version 2.3.0
Local version 4.0.2
```

<span data-ttu-id="4a14c-127">Você pode ter uma versão diferente desses aplicativos.</span><span class="sxs-lookup"><span data-stu-id="4a14c-127">You may have a different version of these applications.</span></span> <span data-ttu-id="4a14c-128">Isso não deve ser um problema, exceto gulp.</span><span class="sxs-lookup"><span data-stu-id="4a14c-128">This should not be a problem, except for gulp.</span></span> <span data-ttu-id="4a14c-129">Para gulp, você precisará usar a versão 4.0.0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="4a14c-129">For gulp you'll need to use version 4.0.0 or later.</span></span>

<span data-ttu-id="4a14c-130">Se você não tiver o gulp instalado (ou tiver a versão errada instalada), faça isso agora executando `npm install gulp` na janela do terminal.</span><span class="sxs-lookup"><span data-stu-id="4a14c-130">If you don't have gulp installed (or have the wrong version installed), do so now by running `npm install gulp` in your terminal window.</span></span>

<span data-ttu-id="4a14c-131">Se você tiver instalado Visual Studio Code, você poderá verificar a instalação executando:</span><span class="sxs-lookup"><span data-stu-id="4a14c-131">If you have installed Visual Studio Code, you can verify the installation by running:</span></span>

```bash
code --version
1.28.2
929bacba01ef658b873545e26034d1a8067445e9
```

<span data-ttu-id="4a14c-132">Você pode continuar a usar essa janela de terminal para executar os comandos a seguir neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="4a14c-132">You can continue to use this terminal window to run the commands that follow in this tutorial.</span></span>

<a name="DownloadSample"></a>

## <a name="download-the-sample"></a><span data-ttu-id="4a14c-133">Baixar o exemplo</span><span class="sxs-lookup"><span data-stu-id="4a14c-133">Download the sample</span></span>

<span data-ttu-id="4a14c-134">Fornecemos um [Hello, World simples!](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/nodejs)</span><span class="sxs-lookup"><span data-stu-id="4a14c-134">We have provided a simple [Hello, World!](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/nodejs)</span></span> <span data-ttu-id="4a14c-135">exemplo para começar.</span><span class="sxs-lookup"><span data-stu-id="4a14c-135">sample to get you started.</span></span> <span data-ttu-id="4a14c-136">Em uma janela de terminal, execute o seguinte comando para clonar o repositório de exemplo para o computador local:</span><span class="sxs-lookup"><span data-stu-id="4a14c-136">In a terminal window, run the following command to clone the sample repository to your local machine:</span></span>

```bash
git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
```

> [!TIP]
> <span data-ttu-id="4a14c-137">Você pode [bifurcar](https://help.github.com/articles/fork-a-repo/) [esse repo](https://github.com/OfficeDev/Microsoft-Teams-Samples) se quiser modificar e verificar suas alterações no seu GitHub para referência futura.</span><span class="sxs-lookup"><span data-stu-id="4a14c-137">You can [fork](https://help.github.com/articles/fork-a-repo/) this [repo](https://github.com/OfficeDev/Microsoft-Teams-Samples) if you want to modify and check in your changes to your GitHub repo for future reference.</span></span>

<a name="BuildRun"></a>

## <a name="build-and-run-the-sample"></a><span data-ttu-id="4a14c-138">Criar e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="4a14c-138">Build and run the sample</span></span>

<span data-ttu-id="4a14c-139">Depois que o repositório for clonado, execute o comando alterar diretório no terminal para alterar o diretório para o exemplo:</span><span class="sxs-lookup"><span data-stu-id="4a14c-139">After the repository is cloned, run the change directory command in terminal to change the directory to the sample:</span></span>

```bash
cd Microsoft-Teams-Samples/samples/app-hello-world/nodejs/
```

<span data-ttu-id="4a14c-140">Para criar o exemplo, você precisa instalar todas as suas dependências.</span><span class="sxs-lookup"><span data-stu-id="4a14c-140">In order to build the sample, you need to install all its dependencies.</span></span> <span data-ttu-id="4a14c-141">Execute o seguinte comando para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="4a14c-141">Run the following command to do this:</span></span>

```bash
npm install
```

<span data-ttu-id="4a14c-142">Você deve ver várias dependências sendo instaladas.</span><span class="sxs-lookup"><span data-stu-id="4a14c-142">You should see a bunch of dependencies getting installed.</span></span> <span data-ttu-id="4a14c-143">Após a instalação, você pode executar o aplicativo com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="4a14c-143">After installation you can run the app with the following command:</span></span>

```bash
npm start
```

<span data-ttu-id="4a14c-144">Quando o aplicativo hello-world é iniciado, ele é `App started listening on port 3333` exibido na janela do terminal.</span><span class="sxs-lookup"><span data-stu-id="4a14c-144">When the hello-world app starts, it displays `App started listening on port 3333` in the terminal window.</span></span>

> [!NOTE]
> <span data-ttu-id="4a14c-145">Se você vir um número de porta diferente exibido na mensagem acima, é porque você tem uma variável de ambiente PORT definida.</span><span class="sxs-lookup"><span data-stu-id="4a14c-145">If you see a different port number displayed in the message above, it is because you have a PORT environment variable set.</span></span> <span data-ttu-id="4a14c-146">Você pode continuar a usar essa porta ou alterar sua variável de ambiente para 3333.</span><span class="sxs-lookup"><span data-stu-id="4a14c-146">You can continue to use that port or change your environment variable to 3333.</span></span>

<span data-ttu-id="4a14c-147">Neste ponto, você pode abrir uma janela do navegador e navegar até as SEGUINTES URLs para verificar se todas as URLs do aplicativo estão sendo carregadas:</span><span class="sxs-lookup"><span data-stu-id="4a14c-147">At this point, you can open a browser window and navigate to the following URLs to verify that all the app URLs are loading:</span></span>

- `http://localhost:3333`
- `http://localhost:3333/hello`
- `http://localhost:3333/first`
- `http://localhost:3333/second`

<a name="HostSample"></a>

## <a name="deploy-your-sample-app"></a><span data-ttu-id="4a14c-148">Implantar seu aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="4a14c-148">Deploy your sample app</span></span>

<span data-ttu-id="4a14c-149">Lembre-se de que os aplicativos Microsoft Teams são aplicativos Web expondo um ou mais recursos.</span><span class="sxs-lookup"><span data-stu-id="4a14c-149">Remember that apps in Microsoft Teams are web applications exposing one or more capabilities.</span></span> <span data-ttu-id="4a14c-150">Para que Teams plataforma de carregamento do aplicativo, seu aplicativo deve ser acessível pela Internet.</span><span class="sxs-lookup"><span data-stu-id="4a14c-150">For the Teams platform to load your app, your app must be reachable from the internet.</span></span> <span data-ttu-id="4a14c-151">Para tornar seu aplicativo acessível pela Internet, você precisa *hospedar* seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4a14c-151">To make your app reachable from the internet, you need to *host* your app.</span></span>

<span data-ttu-id="4a14c-152">Para testes locais, você pode executar o aplicativo em sua máquina local e criar um túnel para ele com um ponto de extremidade da Web.</span><span class="sxs-lookup"><span data-stu-id="4a14c-152">For local testing you can run the app on your local machine and create a tunnel to it with a web endpoint.</span></span> <span data-ttu-id="4a14c-153">[ngrok](https://ngrok.com) é uma ferramenta gratuita que permite que você faça exatamente isso.</span><span class="sxs-lookup"><span data-stu-id="4a14c-153">[ngrok](https://ngrok.com) is a free tool that lets you do just that.</span></span> <span data-ttu-id="4a14c-154">Com *o ngrok,* você pode obter um endereço da Web como `https://d0ac14a5.ngrok.io` (essa URL é apenas um exemplo).</span><span class="sxs-lookup"><span data-stu-id="4a14c-154">With *ngrok* you can get a web address such as `https://d0ac14a5.ngrok.io` (this URL is just an example).</span></span> <span data-ttu-id="4a14c-155">Você pode [baixar e instalar](https://ngrok.com/download) o *ngrok* para seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="4a14c-155">You can [download and install](https://ngrok.com/download) *ngrok* for your environment.</span></span> <span data-ttu-id="4a14c-156">Certifique-se de adicioná-lo a um local em seu `PATH` .</span><span class="sxs-lookup"><span data-stu-id="4a14c-156">Make sure you add it to a location in your `PATH`.</span></span>

<span data-ttu-id="4a14c-157">Depois de instalá-la, você pode abrir uma nova janela de terminal e executar o seguinte comando para criar um túnel.</span><span class="sxs-lookup"><span data-stu-id="4a14c-157">After you install it, you can open a new terminal window and run the following command to create a tunnel.</span></span> <span data-ttu-id="4a14c-158">O exemplo usa a porta 3333, portanto, certifique-se de especificá-la aqui:</span><span class="sxs-lookup"><span data-stu-id="4a14c-158">The sample uses port 3333, so be sure to specify it here:</span></span>

```bash
ngrok http 3333 -host-header=localhost:3333
```

<span data-ttu-id="4a14c-159">*O Ngrok* ouvirá as solicitações da Internet e as encaminhará para seu aplicativo em execução na porta 3333.</span><span class="sxs-lookup"><span data-stu-id="4a14c-159">*Ngrok* will listen to requests from the internet and will route them to your app running on port 3333.</span></span> <span data-ttu-id="4a14c-160">Você pode verificar abrindo seu navegador e `https://d0ac14a5.ngrok.io/hello` carregando a página hello do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4a14c-160">You can verify by opening your browser and going to `https://d0ac14a5.ngrok.io/hello` to load your app's hello page.</span></span> <span data-ttu-id="4a14c-161">Certifique-se de usar o endereço de encaminhamento exibido pelo *ngrok* em sua sessão de console em vez dessa URL.</span><span class="sxs-lookup"><span data-stu-id="4a14c-161">Please be sure to use the forwarding address displayed by *ngrok* in your console session instead of this URL.</span></span>

> [!NOTE]
> <span data-ttu-id="4a14c-162">Se você tiver usado uma porta diferente na [com](#build-and-run-the-sample) build e execute a etapa acima, certifique-se de usar o mesmo número de porta para configurar o *túnel ngrok.*</span><span class="sxs-lookup"><span data-stu-id="4a14c-162">If you have used a different port in the [build and run](#build-and-run-the-sample) step above, make sure you use the same port number to setup the *ngrok* tunnel.</span></span>
> [!TIP]
> <span data-ttu-id="4a14c-163">É uma boa ideia executar *o ngrok* em uma janela de terminal diferente para mantê-lo em execução sem interferir no aplicativo de nó que talvez você tenha que parar, recriar e executar de novo.</span><span class="sxs-lookup"><span data-stu-id="4a14c-163">It is a good idea to run *ngrok* in a different terminal window to keep it running without interfering with the node app which you might later have to stop, rebuild and rerun.</span></span> <span data-ttu-id="4a14c-164">A *sessão ngrok* retornará informações úteis de depuração nesta janela.</span><span class="sxs-lookup"><span data-stu-id="4a14c-164">The *ngrok* session will return useful debugging information in this window.</span></span>

<span data-ttu-id="4a14c-165">Há uma versão paga do *ngrok* que permite nomes persistentes.</span><span class="sxs-lookup"><span data-stu-id="4a14c-165">There is a paid version of *ngrok* that allows persistent names.</span></span> <span data-ttu-id="4a14c-166">Se você usar a versão gratuita, seu aplicativo só estará disponível durante a sessão atual em seu computador de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="4a14c-166">If you use the free version your app will only be available during the current session on your development machine.</span></span> <span data-ttu-id="4a14c-167">Se o computador for desligado ou for parar, o serviço não estará mais disponível.</span><span class="sxs-lookup"><span data-stu-id="4a14c-167">If the machine is shut down or goes to sleep the service will no longer be available.</span></span> <span data-ttu-id="4a14c-168">Lembre-se disso ao compartilhar o aplicativo para teste por outros usuários.</span><span class="sxs-lookup"><span data-stu-id="4a14c-168">Remember this when sharing the app for testing by other users.</span></span> <span data-ttu-id="4a14c-169">Se você tiver que reiniciar o serviço, ele retornará um novo endereço e será preciso atualizar todos os lugares que usam esse endereço.</span><span class="sxs-lookup"><span data-stu-id="4a14c-169">If you have to restart the service it will return a new address and you will have to update every place that uses that address.</span></span>

<span data-ttu-id="4a14c-170">Anote a URL do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4a14c-170">Make a note of the URL of your app.</span></span> <span data-ttu-id="4a14c-171">Você precisará disso mais tarde quando registrar o aplicativo com Teams app studio ou Portal do Desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="4a14c-171">You will need this later when you register the app with Teams using App studio or Developer Portal.</span></span>

<a name="DeployToTeams"></a>

## <a name="deploy-your-app-to-microsoft-teams"></a><span data-ttu-id="4a14c-172">Implantar seu aplicativo para Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="4a14c-172">Deploy your app to Microsoft Teams</span></span>

<span data-ttu-id="4a14c-173">Neste ponto, você tem um aplicativo hospedado na Internet, mas ainda não tem como dizer Teams onde procurar ou até mesmo o que seu aplicativo é chamado.</span><span class="sxs-lookup"><span data-stu-id="4a14c-173">At this point you have an app hosted on the internet, but you have no way yet of telling Teams where to look for it, or even what your app is called.</span></span> <span data-ttu-id="4a14c-174">Para fazer isso, agora você precisa criar um pacote de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="4a14c-174">To do this you now have to create an app package.</span></span> <span data-ttu-id="4a14c-175">Isso é pouco mais do que um arquivo de texto que contém o manifesto do aplicativo e alguns ícones que o Teams cliente usará para exibir e identidade visual adequadamente seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4a14c-175">This is little more than a text file that contains the app manifest and some icons that the Teams client will use to properly display and brand your app.</span></span> <span data-ttu-id="4a14c-176">Você pode criar manualmente esse pacote de aplicativos ou usar o App Studio ou o Portal do Desenvolvedor, ferramentas que são Teams, que simplificarão o processo de registro do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4a14c-176">You can manually create this app package, or you can use App Studio or Developer Portal, tools that run in Teams, that will simplify the process of registering the app.</span></span> <span data-ttu-id="4a14c-177">O App Studio e o Portal do Desenvolvedor são as maneiras recomendadas de criar e atualizar o pacote de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="4a14c-177">App Studio and Developer Portal are the recommended ways of creating and updating the app package.</span></span>

<span data-ttu-id="4a14c-178">Para qualquer um dos métodos, você precisará do seguinte:</span><span class="sxs-lookup"><span data-stu-id="4a14c-178">For either method you will need the following:</span></span>

- <span data-ttu-id="4a14c-179">A URL onde seu aplicativo pode ser encontrado na Internet.</span><span class="sxs-lookup"><span data-stu-id="4a14c-179">The URL where your app can be found on the internet.</span></span>
- <span data-ttu-id="4a14c-180">Ícones que Teams usarão para fazer a marca do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4a14c-180">Icons that Teams will use to brand your app.</span></span> <span data-ttu-id="4a14c-181">O exemplo vem com ícones de espaço reservado localizados em "src\static\images.</span><span class="sxs-lookup"><span data-stu-id="4a14c-181">The sample comes with placeholder icons located in "src\static\images.</span></span> <span data-ttu-id="4a14c-182">O App Studio também fornecerá ícones padrão, se necessário.</span><span class="sxs-lookup"><span data-stu-id="4a14c-182">App Studio also will provide default icons if needed.</span></span>

<span data-ttu-id="4a14c-183">**Atualizar o pacote do aplicativo**</span><span class="sxs-lookup"><span data-stu-id="4a14c-183">**Update the app package**</span></span>

# <a name="app-studio"></a>[<span data-ttu-id="4a14c-184">App Studio</span><span class="sxs-lookup"><span data-stu-id="4a14c-184">App Studio</span></span>](#tab/AS)

[!include [Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

# <a name="developer-portal"></a>[<span data-ttu-id="4a14c-185">Portal do Desenvolvedor</span><span class="sxs-lookup"><span data-stu-id="4a14c-185">Developer Portal</span></span>](#tab/DP)

<span data-ttu-id="4a14c-186">**Para instalar o Portal do Desenvolvedor (visualização) Teams**</span><span class="sxs-lookup"><span data-stu-id="4a14c-186">**To install Developer Portal (preview) in Teams**</span></span>

1. <span data-ttu-id="4a14c-187">Selecione o **ícone Aplicativos** na parte inferior da barra à esquerda e procure o **Portal do Desenvolvedor.**</span><span class="sxs-lookup"><span data-stu-id="4a14c-187">Select the **Apps** icon at the bottom of the left-hand bar, and search for **Developer Portal**.</span></span>

    <img width="430px" alt="Screenshot of TDP" src="~/assets/images/Screen1.png"/>

1. <span data-ttu-id="4a14c-188">Selecione **Portal do Desenvolvedor** e selecione **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="4a14c-188">Select **Developer Portal** and select **Open**.</span></span>

    <img width="430px" alt="Screenshot of TDP Open" src="~/assets/images/screen2.png"/>

1. <span data-ttu-id="4a14c-189">Selecione a guia Aplicativos e selecione **Importar um aplicativo existente.**</span><span class="sxs-lookup"><span data-stu-id="4a14c-189">Select the Apps tab and select **Import an existing app**.</span></span>

    <img width="430px" alt="Screenshot of import app in tdp" src="~/assets/images/screen3.png"/>

1. <span data-ttu-id="4a14c-190">Selecione **Hello World** e selecione **Importar**.</span><span class="sxs-lookup"><span data-stu-id="4a14c-190">Select **Hello World** and select **Import**.</span></span> <span data-ttu-id="4a14c-191">O **aplicativo Hello World** é importado no Portal do Desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="4a14c-191">The **Hello World** app is imported in Developer Portal.</span></span> 

    <span data-ttu-id="4a14c-192">Você pode configurar seu aplicativo usando o Teams Portal do Desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="4a14c-192">You can configure your app using the Teams Developer Portal.</span></span> <span data-ttu-id="4a14c-193">O Manifesto é encontrado em Distribute.</span><span class="sxs-lookup"><span data-stu-id="4a14c-193">The Manifest is found under Distribute.</span></span> <span data-ttu-id="4a14c-194">Você pode usar o Manifesto para configurar recursos, recursos necessários e outros atributos importantes para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4a14c-194">You can use the Manifest to configure capabilities, required resources, and other important attributes for your app.</span></span> <span data-ttu-id="4a14c-195">Para obter mais detalhes sobre como configurar seu aplicativo usando o Portal do Desenvolvedor, [consulte Teams Portal do Desenvolvedor.](../concepts/build-and-test/teams-developer-portal.md)</span><span class="sxs-lookup"><span data-stu-id="4a14c-195">For more details on how to configure your app using Developer Portal, see [Teams Developer Portal](../concepts/build-and-test/teams-developer-portal.md).</span></span>

    <img width="430px" alt="Screenshot of configure tdp" src="~/assets/images/Screen4.png"/>

---
<a name="updatecredentials"></a>

## <a name="update-the-credentials-for-your-hosted-app"></a><span data-ttu-id="4a14c-196">Atualizar as credenciais do aplicativo hospedado</span><span class="sxs-lookup"><span data-stu-id="4a14c-196">Update the credentials for your hosted app</span></span>

<span data-ttu-id="4a14c-197">O aplicativo de exemplo exige que as seguintes variáveis de ambiente sejam definidas para os valores que você fez uma anotação anteriormente:</span><span class="sxs-lookup"><span data-stu-id="4a14c-197">The sample app requires the following environment variables to be set to the values you made a note of earlier:</span></span>

```
MICROSOFT_APP_ID=<YOUR BOT'S APP ID>
MICROSOFT_APP_PASSWORD=<YOUR BOT'S PASSWORD>
WEBSITE_NODE_DEFAULT_VERSION=8.9.4
```

<span data-ttu-id="4a14c-198">Como fazer isso difere dependendo de como você hospedou seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4a14c-198">How you do that differs depending on how you hosted your app.</span></span> <span data-ttu-id="4a14c-199">O importante sobre o uso de variáveis de ambiente é que esses valores fazem parte do seu ambiente - eles podem ser acessados pelo código para seu aplicativo, mas não são expostos a terceiros que podem examinar os arquivos que compusem seu site.</span><span class="sxs-lookup"><span data-stu-id="4a14c-199">The important thing about using environment variables is that these values are part of your environment - they can be accessed by the code for your app, but they are not exposed to third parties who might examine the files that make up your site.</span></span>

<span data-ttu-id="4a14c-200">Se você estiver executando o aplicativo usando o ngrok, precisará configurar algumas variáveis de ambiente local.</span><span class="sxs-lookup"><span data-stu-id="4a14c-200">If you are running the app using ngrok you'll need to set up some local environment variables.</span></span> <span data-ttu-id="4a14c-201">Há muitas maneiras de fazer isso, mas a mais fácil, se você estiver usando Visual Studio Code, é adicionar uma configuração [de início](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations):</span><span class="sxs-lookup"><span data-stu-id="4a14c-201">There are many ways to do this, but the easiest, if you are using Visual Studio Code, is to add a [launch configuration](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations):</span></span>

``` 
{
    "type": "node",
    "request": "launch",
    "name": "Launch - Teams Debug",
    "program": "${workspaceRoot}/src/app.js",
    "cwd": "${workspaceFolder}/src",
    "env": {
        "BASE_URI": "https://yourNgrokURL.ngrok.io",
        "MICROSOFT_APP_ID": "00000000-0000-0000-0000-000000000000",
        "MICROSOFT_APP_PASSWORD": "yourBotAppPassword",
        "NODE_DEBUG": "botbuilder",
        "SUPPRESS_NO_CONFIG_WARNING": "y",
        "NODE_CONFIG_DIR": "../config"
    }
}
```

<span data-ttu-id="4a14c-202">Onde:</span><span class="sxs-lookup"><span data-stu-id="4a14c-202">Where:</span></span>

<span data-ttu-id="4a14c-203">MICROSOFT_APP_ID e MICROSOFT_APP_PASSWORD é a ID e a senha, respectivamente, para seu bot.</span><span class="sxs-lookup"><span data-stu-id="4a14c-203">MICROSOFT_APP_ID and MICROSOFT_APP_PASSWORD is the ID and password, respectively, for your bot.</span></span>
<span data-ttu-id="4a14c-204">NODE_DEBUG mostrará o que está acontecendo em seu bot no console Visual Studio Code depuração.</span><span class="sxs-lookup"><span data-stu-id="4a14c-204">NODE_DEBUG will show you what's happening in your bot in the Visual Studio Code debug console.</span></span>
<span data-ttu-id="4a14c-205">NODE_CONFIG_DIR aponta para o diretório na raiz do repositório (por padrão, quando o aplicativo é executado localmente, ele procura por ele na pasta src).</span><span class="sxs-lookup"><span data-stu-id="4a14c-205">NODE_CONFIG_DIR points to the directory at the root of the repository (by default, when the app is run locally, it looks for it in the src folder).</span></span>

> [!Note]
> <span data-ttu-id="4a14c-206">Se você não tiver parado npm no início do tutorial, precisará ser executado para que Visual Studio Code suas variáveis de configuração de início `npm stop` corretamente.</span><span class="sxs-lookup"><span data-stu-id="4a14c-206">If you have not stopped npm from earlier in the tutorial, you'll need to run `npm stop` in order for Visual Studio Code to pickup your launch configuration variables correctly.</span></span>

<a name="ConfigureTheAppTab"></a>

## <a name="configure-the-app-tab"></a><span data-ttu-id="4a14c-207">Configurar a guia do aplicativo</span><span class="sxs-lookup"><span data-stu-id="4a14c-207">Configure the app tab</span></span>

<span data-ttu-id="4a14c-208">Depois de instalar o aplicativo em uma equipe, você precisará configurá-lo para mostrar conteúdo.</span><span class="sxs-lookup"><span data-stu-id="4a14c-208">After you install the app into a team, you will need to configure it to show content.</span></span> <span data-ttu-id="4a14c-209">Vá para um canal na equipe e clique no botão **'+'** para adicionar uma nova guia. Em seguida, você pode `Hello World` escolher na lista Adicionar **uma** guia.</span><span class="sxs-lookup"><span data-stu-id="4a14c-209">Go to a channel in the team and click on the **'+'** button to add a new tab. You can then choose `Hello World` from the **Add a tab** list.</span></span> <span data-ttu-id="4a14c-210">Em seguida, você será apresentado com uma caixa de diálogo de configuração.</span><span class="sxs-lookup"><span data-stu-id="4a14c-210">You will then be presented with a configuration dialog.</span></span> <span data-ttu-id="4a14c-211">Essa caixa de diálogo permitirá que você escolha qual guia exibir neste canal.</span><span class="sxs-lookup"><span data-stu-id="4a14c-211">This dialog will let you choose which tab to display in this channel.</span></span> <span data-ttu-id="4a14c-212">Depois de selecionar a guia e clicar em **Salvar,** você pode ver a `Hello World` guia carregada com a guia escolhida:</span><span class="sxs-lookup"><span data-stu-id="4a14c-212">After you select the tab and click **Save** you can see the `Hello World` tab loaded with the tab you chose:</span></span>

<img width="430px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png"/>

### <a name="test-your-bot-in-teams"></a><span data-ttu-id="4a14c-213">Teste seu bot no Teams</span><span class="sxs-lookup"><span data-stu-id="4a14c-213">Test your bot in Teams</span></span>

<span data-ttu-id="4a14c-214">Agora você pode interagir com o bot no Teams.</span><span class="sxs-lookup"><span data-stu-id="4a14c-214">You can now interact with the bot in Teams.</span></span> <span data-ttu-id="4a14c-215">Escolha um canal na equipe onde você registrou seu aplicativo e digite `@your-bot-name` , seguido de sua mensagem.</span><span class="sxs-lookup"><span data-stu-id="4a14c-215">Choose a channel in the team where you registered your app, and type `@your-bot-name`, followed by your message.</span></span> <span data-ttu-id="4a14c-216">Isso é chamado de **\@ menção**.</span><span class="sxs-lookup"><span data-stu-id="4a14c-216">This is called an **\@mention**.</span></span> <span data-ttu-id="4a14c-217">Qualquer mensagem que você enviar para o bot será enviada de volta como uma resposta:</span><span class="sxs-lookup"><span data-stu-id="4a14c-217">Whatever message you send to the bot will be sent back to you as a reply:</span></span>

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png"/>

<a name="ComposeRichMessages"></a>

### <a name="test-your-messaging-extension"></a><span data-ttu-id="4a14c-218">Testar sua extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="4a14c-218">Test your messaging extension</span></span>

<span data-ttu-id="4a14c-219">**Para testar sua extensão de mensagens**</span><span class="sxs-lookup"><span data-stu-id="4a14c-219">**To test your messaging extension**</span></span>
1. <span data-ttu-id="4a14c-220">Selecione os três pontos abaixo da caixa de entrada no seu exibição de conversa.</span><span class="sxs-lookup"><span data-stu-id="4a14c-220">Select the three dots below the input box in your conversation view.</span></span> <span data-ttu-id="4a14c-221">Um menu com o **aplicativo "Hello World"** é exibido.</span><span class="sxs-lookup"><span data-stu-id="4a14c-221">A menu with the **'Hello World'** app is displayed.</span></span>
1. <span data-ttu-id="4a14c-222">Selecione o menu.</span><span class="sxs-lookup"><span data-stu-id="4a14c-222">Select the menu.</span></span> <span data-ttu-id="4a14c-223">Um conjunto de textos aleatórios é exibido.</span><span class="sxs-lookup"><span data-stu-id="4a14c-223">A set of random texts is displayed.</span></span> <span data-ttu-id="4a14c-224">Você pode selecionar um dos textos aleatórios e que é inserido em sua conversa.</span><span class="sxs-lookup"><span data-stu-id="4a14c-224">You can select one of the random text and that is inserted into your conversation.</span></span>

    <img width="430px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu1.png" />

    <img width="430px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result1.png" />

1. <span data-ttu-id="4a14c-225">Selecione um dos textos aleatórios e você verá um cartão formatado e pronto para enviar com sua própria mensagem na parte inferior:</span><span class="sxs-lookup"><span data-stu-id="4a14c-225">Select one of the random texts, and you will see a card formatted and ready to send with your own message at the bottom:</span></span>

    <img width="430px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />

 ## <a name="see-also"></a><span data-ttu-id="4a14c-226">Confira também</span><span class="sxs-lookup"><span data-stu-id="4a14c-226">See also</span></span>

* [<span data-ttu-id="4a14c-227">Visão geral dos tutoriais</span><span class="sxs-lookup"><span data-stu-id="4a14c-227">Tutorials Overview</span></span>](code-samples.md)
* [<span data-ttu-id="4a14c-228">Criar um programa bot de conversação</span><span class="sxs-lookup"><span data-stu-id="4a14c-228">Create a conversational bot app</span></span>](first-app-bot.md)
* [<span data-ttu-id="4a14c-229">Criar uma extensão de mensagem</span><span class="sxs-lookup"><span data-stu-id="4a14c-229">Create a messaging extension</span></span>](first-message-extension.md)
* [<span data-ttu-id="4a14c-230">Exemplos de código</span><span class="sxs-lookup"><span data-stu-id="4a14c-230">Code Samples</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples)