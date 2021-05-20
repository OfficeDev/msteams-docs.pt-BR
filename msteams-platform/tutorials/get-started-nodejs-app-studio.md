---
title: Tutorial - Crie seu primeiro aplicativo usando Node.js
description: Saiba como começar a construir aplicativos Microsoft Teams com Node.js.
keywords: começando node.js nodejs App Studio
ms.topic: tutorial
localization_priority: Normal
ms.custom: scenarios:getting-started; languages:JavaScript,Node.js
ms.openlocfilehash: 46272671443e07432513b667af424b5c5be05f2e
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566534"
---
# <a name="create-your-first-microsoft-teams-app-using-nodejs"></a><span data-ttu-id="74b2e-104">Crie seu primeiro aplicativo de Microsoft Teams usando Node.js</span><span class="sxs-lookup"><span data-stu-id="74b2e-104">Create your first Microsoft Teams app using Node.js</span></span>

<span data-ttu-id="74b2e-105">Este tutorial ajuda você a começar a criar um aplicativo Microsoft Teams usando Node.js.</span><span class="sxs-lookup"><span data-stu-id="74b2e-105">This tutorial helps you get started creating a Microsoft Teams app using Node.js.</span></span>

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="DownloadAndHost"></a>

## <a name="download-and-host-your-app"></a><span data-ttu-id="74b2e-106">Baixe e hospede seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="74b2e-106">Download and host your app</span></span>

<span data-ttu-id="74b2e-107">Siga estas etapas para baixar e hospedar um aplicativo simples "Hello world" em Teams.</span><span class="sxs-lookup"><span data-stu-id="74b2e-107">Follow these steps to download and host a simple "hello world" app in Teams.</span></span>

<a name="GetPrerequisites"></a>

### <a name="get-prerequisites"></a><span data-ttu-id="74b2e-108">Obter pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="74b2e-108">Get prerequisites</span></span>

<span data-ttu-id="74b2e-109">Para completar este tutorial, você precisa das seguintes ferramentas.</span><span class="sxs-lookup"><span data-stu-id="74b2e-109">To complete this tutorial, you need the following tools.</span></span> <span data-ttu-id="74b2e-110">Se você ainda não os tiver, você pode instalá-los a partir desses links.</span><span class="sxs-lookup"><span data-stu-id="74b2e-110">If you don't already have them you can install them from these links.</span></span>

- [<span data-ttu-id="74b2e-111">Git</span><span class="sxs-lookup"><span data-stu-id="74b2e-111">Git</span></span>](https://git-scm.com/downloads)
- [<span data-ttu-id="74b2e-112">Node.js e NPM</span><span class="sxs-lookup"><span data-stu-id="74b2e-112">Node.js and NPM</span></span>](https://nodejs.org/)
- <span data-ttu-id="74b2e-113">Obtenha qualquer editor de texto ou IDE.</span><span class="sxs-lookup"><span data-stu-id="74b2e-113">Get any text editor or IDE.</span></span> <span data-ttu-id="74b2e-114">Você pode instalar e usar [Visual Studio Code](https://code.visualstudio.com/download) gratuitamente.</span><span class="sxs-lookup"><span data-stu-id="74b2e-114">You can install and use [Visual Studio Code](https://code.visualstudio.com/download) for free.</span></span>

<span data-ttu-id="74b2e-115">Se você vir opções para `git` `node` adicionar, `npm` e ao PATH durante `code` a instalação, opte por fazê-lo.</span><span class="sxs-lookup"><span data-stu-id="74b2e-115">If you see options to add `git`, `node`, `npm`, and `code` to the PATH during installation, choose to do so.</span></span> <span data-ttu-id="74b2e-116">Será útil.</span><span class="sxs-lookup"><span data-stu-id="74b2e-116">It will be handy.</span></span>

<span data-ttu-id="74b2e-117">Verifique se as ferramentas estão disponíveis executando as seguintes em uma janela de terminal:</span><span class="sxs-lookup"><span data-stu-id="74b2e-117">Verify that the tools are available by running the following in a terminal window:</span></span>

> [!NOTE]
> <span data-ttu-id="74b2e-118">Use a janela do terminal com a sua plataforma.</span><span class="sxs-lookup"><span data-stu-id="74b2e-118">Use the terminal window that you are most comfortable with on your platform.</span></span> <span data-ttu-id="74b2e-119">Esses exemplos usam bash (que está incluído no Git), mas esses scripts serão executados na maioria das plataformas.</span><span class="sxs-lookup"><span data-stu-id="74b2e-119">These examples use Bash (which is included in Git), but these scripts will run on most platforms.</span></span>

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

<span data-ttu-id="74b2e-120">Você pode ter uma versão diferente desses aplicativos.</span><span class="sxs-lookup"><span data-stu-id="74b2e-120">You may have a different version of these applications.</span></span> <span data-ttu-id="74b2e-121">Isso não deve ser um problema, exceto para gole.</span><span class="sxs-lookup"><span data-stu-id="74b2e-121">This should not be a problem, except for gulp.</span></span> <span data-ttu-id="74b2e-122">Para o gol de gol, você precisará usar a versão 4.0.0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="74b2e-122">For gulp you'll need to use version 4.0.0 or later.</span></span>

<span data-ttu-id="74b2e-123">Se você não tiver o gole instalado (ou tiver a versão errada instalada), faça-o agora, executando `npm install gulp` na janela do terminal.</span><span class="sxs-lookup"><span data-stu-id="74b2e-123">If you don't have gulp installed (or have the wrong version installed), do so now by running `npm install gulp` in your terminal window.</span></span>

<span data-ttu-id="74b2e-124">Se você tiver instalado Visual Studio Code, você pode verificar a instalação executando:</span><span class="sxs-lookup"><span data-stu-id="74b2e-124">If you have installed Visual Studio Code, you can verify the installation by running:</span></span>

```bash
code --version
1.28.2
929bacba01ef658b873545e26034d1a8067445e9
```

<span data-ttu-id="74b2e-125">Você pode continuar a usar esta janela de terminal para executar os comandos que seguem neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="74b2e-125">You can continue to use this terminal window to run the commands that follow in this tutorial.</span></span>

<a name="DownloadSample"></a>

### <a name="download-the-sample"></a><span data-ttu-id="74b2e-126">Baixe a amostra</span><span class="sxs-lookup"><span data-stu-id="74b2e-126">Download the sample</span></span>

<span data-ttu-id="74b2e-127">Nós fornecemos um simples [Olá, Mundo!](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/nodejs)</span><span class="sxs-lookup"><span data-stu-id="74b2e-127">We have provided a simple [Hello, World!](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/nodejs)</span></span> <span data-ttu-id="74b2e-128">amostra para começar.</span><span class="sxs-lookup"><span data-stu-id="74b2e-128">sample to get you started.</span></span> <span data-ttu-id="74b2e-129">Em uma janela terminal, execute o seguinte comando para clonar o repositório de amostras para sua máquina local:</span><span class="sxs-lookup"><span data-stu-id="74b2e-129">In a terminal window, run the following command to clone the sample repository to your local machine:</span></span>

```bash
git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
```

> [!TIP]
> <span data-ttu-id="74b2e-130">Você pode [bifurcar](https://help.github.com/articles/fork-a-repo/) este [repo](https://github.com/OfficeDev/Microsoft-Teams-Samples) se quiser modificar e verificar suas alterações em seu GitHub repo para referência futura.</span><span class="sxs-lookup"><span data-stu-id="74b2e-130">You can [fork](https://help.github.com/articles/fork-a-repo/) this [repo](https://github.com/OfficeDev/Microsoft-Teams-Samples) if you want to modify and check in your changes to your GitHub repo for future reference.</span></span>

<a name="BuildRun"></a>

### <a name="build-and-run-the-sample"></a><span data-ttu-id="74b2e-131">Criar e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="74b2e-131">Build and run the sample</span></span>

<span data-ttu-id="74b2e-132">Uma vez que o repo é clonado, mude para o diretório que contém a amostra:</span><span class="sxs-lookup"><span data-stu-id="74b2e-132">Once the repo is cloned, change to the directory that holds the sample:</span></span>

```bash
cd Microsoft-Teams-Samples/samples/app-hello-world/nodejs/
```

<span data-ttu-id="74b2e-133">Para construir a amostra, você precisa instalar todas as suas dependências.</span><span class="sxs-lookup"><span data-stu-id="74b2e-133">In order to build the sample, you need to install all its dependencies.</span></span> <span data-ttu-id="74b2e-134">Execute o seguinte comando para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="74b2e-134">Run the following command to do this:</span></span>

```bash
npm install
```

<span data-ttu-id="74b2e-135">Você deveria ver um monte de dependências sendo instaladas.</span><span class="sxs-lookup"><span data-stu-id="74b2e-135">You should see a bunch of dependencies getting installed.</span></span> <span data-ttu-id="74b2e-136">Uma vez terminados, você pode executar o aplicativo:</span><span class="sxs-lookup"><span data-stu-id="74b2e-136">Once they are finished, you can run the app:</span></span>

```bash
npm start
```

<span data-ttu-id="74b2e-137">Quando o aplicativo hello-world é iniciado, ele é exibido `App started listening on port 3333` na janela do terminal.</span><span class="sxs-lookup"><span data-stu-id="74b2e-137">When the hello-world app starts, it displays `App started listening on port 3333` in the terminal window.</span></span>

> [!NOTE]
> <span data-ttu-id="74b2e-138">Se você vir um número de porta diferente exibido na mensagem acima, é porque você tem um conjunto variável de ambiente PORT.</span><span class="sxs-lookup"><span data-stu-id="74b2e-138">If you see a different port number displayed in the message above, it is because you have a PORT environment variable set.</span></span> <span data-ttu-id="74b2e-139">Você pode continuar a usar essa porta ou alterar sua variável de ambiente para 3333.</span><span class="sxs-lookup"><span data-stu-id="74b2e-139">You can continue to use that port or change your environment variable to 3333.</span></span>

<span data-ttu-id="74b2e-140">Neste ponto, você pode abrir uma janela do navegador e navegar para os seguintes URLs para verificar se todos os URLs do aplicativo estão carregando:</span><span class="sxs-lookup"><span data-stu-id="74b2e-140">At this point, you can open a browser window and navigate to the following URLs to verify that all the app URLs are loading:</span></span>

- `http://localhost:3333`
- `http://localhost:3333/hello`
- `http://localhost:3333/first`
- `http://localhost:3333/second`

<a name="HostSample"></a>

### <a name="host-the-sample-app"></a><span data-ttu-id="74b2e-141">Hospede o aplicativo de amostra</span><span class="sxs-lookup"><span data-stu-id="74b2e-141">Host the sample app</span></span>

<span data-ttu-id="74b2e-142">Lembre-se que os aplicativos em Microsoft Teams são aplicativos web expondo um ou mais recursos.</span><span class="sxs-lookup"><span data-stu-id="74b2e-142">Remember that apps in Microsoft Teams are web applications exposing one or more capabilities.</span></span> <span data-ttu-id="74b2e-143">Para que a plataforma Teams carregue seu aplicativo, seu aplicativo deve ser acessível a partir da internet.</span><span class="sxs-lookup"><span data-stu-id="74b2e-143">For the Teams platform to load your app, your app must be reachable from the internet.</span></span> <span data-ttu-id="74b2e-144">Para tornar seu aplicativo acessível a partir da internet, você precisa *hospedar* seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="74b2e-144">To make your app reachable from the internet, you need to *host* your app.</span></span>

<span data-ttu-id="74b2e-145">Para testes locais, você pode executar o aplicativo em sua máquina local e criar um túnel para ele com um ponto final da Web.</span><span class="sxs-lookup"><span data-stu-id="74b2e-145">For local testing you can run the app on your local machine and create a tunnel to it with a web endpoint.</span></span> <span data-ttu-id="74b2e-146">[ngrok](https://ngrok.com) é uma ferramenta gratuita que permite que você faça exatamente isso.</span><span class="sxs-lookup"><span data-stu-id="74b2e-146">[ngrok](https://ngrok.com) is a free tool that lets you do just that.</span></span> <span data-ttu-id="74b2e-147">Com *o ngrok* você pode obter um endereço web como `https://d0ac14a5.ngrok.io` (esta URL é apenas um exemplo).</span><span class="sxs-lookup"><span data-stu-id="74b2e-147">With *ngrok* you can get a web address such as `https://d0ac14a5.ngrok.io` (this URL is just an example).</span></span> <span data-ttu-id="74b2e-148">Você pode [baixar e instalar](https://ngrok.com/download) *ngrok* para o seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="74b2e-148">You can [download and install](https://ngrok.com/download) *ngrok* for your environment.</span></span> <span data-ttu-id="74b2e-149">Certifique-se de adicioná-lo a um local em seu `PATH` .</span><span class="sxs-lookup"><span data-stu-id="74b2e-149">Make sure you add it to a location in your `PATH`.</span></span>

<span data-ttu-id="74b2e-150">Depois de instalá-lo, você pode abrir uma nova janela de terminal e executar o seguinte comando para criar um túnel.</span><span class="sxs-lookup"><span data-stu-id="74b2e-150">Once you install it, you can open a new terminal window and run the following command to create a tunnel.</span></span> <span data-ttu-id="74b2e-151">A amostra usa a porta 3333, então não deixe de especificá-la aqui:</span><span class="sxs-lookup"><span data-stu-id="74b2e-151">The sample uses port 3333, so be sure to specify it here:</span></span>

```bash
ngrok http 3333 -host-header=localhost:3333
```

<span data-ttu-id="74b2e-152">*A Ngrok* ouvirá as solicitações da internet e as encaminhará para o seu aplicativo que será executado na porta 3333.</span><span class="sxs-lookup"><span data-stu-id="74b2e-152">*Ngrok* will listen to requests from the internet and will route them to your app running on port 3333.</span></span> <span data-ttu-id="74b2e-153">Você pode verificar abrindo seu navegador e indo `https://d0ac14a5.ngrok.io/hello` para carregar a página de olá do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="74b2e-153">You can verify by opening your browser and going to `https://d0ac14a5.ngrok.io/hello` to load your app's hello page.</span></span> <span data-ttu-id="74b2e-154">Por favor, certifique-se de usar o endereço de encaminhamento exibido por *ngrok* na sessão do console em vez desta URL.</span><span class="sxs-lookup"><span data-stu-id="74b2e-154">Please be sure to use the forwarding address displayed by *ngrok* in your console session instead of this URL.</span></span>

> [!NOTE]
> <span data-ttu-id="74b2e-155">Se você tiver usado uma porta diferente na [construção e executar](#build-and-run-the-sample) passo acima, certifique-se de usar o mesmo número de porta para configurar o túnel *ngrok.*</span><span class="sxs-lookup"><span data-stu-id="74b2e-155">If you have used a different port in the [build and run](#build-and-run-the-sample) step above, make sure you use the same port number to setup the *ngrok* tunnel.</span></span>
> [!TIP]
> <span data-ttu-id="74b2e-156">É uma boa ideia executar *ngrok* em uma janela de terminal diferente para mantê-lo funcionando sem interferir com o aplicativo de nó que você pode mais tarde ter que parar, reconstruir e reexer.</span><span class="sxs-lookup"><span data-stu-id="74b2e-156">It is a good idea to run *ngrok* in a different terminal window to keep it running without interfering with the node app which you might later have to stop, rebuild and rerun.</span></span> <span data-ttu-id="74b2e-157">A sessão *ngrok* retornará informações úteis de depuração nesta janela.</span><span class="sxs-lookup"><span data-stu-id="74b2e-157">The *ngrok* session will return useful debugging information in this window.</span></span>

<span data-ttu-id="74b2e-158">Há uma versão paga de *ngrok* que permite nomes persistentes.</span><span class="sxs-lookup"><span data-stu-id="74b2e-158">There is a paid version of *ngrok* that allows persistent names.</span></span> <span data-ttu-id="74b2e-159">Se você usar a versão gratuita, seu aplicativo só estará disponível durante a sessão atual na sua máquina de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="74b2e-159">If you use the free version your app will only be available during the current session on your development machine.</span></span> <span data-ttu-id="74b2e-160">Se a máquina estiver desligada ou for dormir, o serviço não estará mais disponível.</span><span class="sxs-lookup"><span data-stu-id="74b2e-160">If the machine is shut down or goes to sleep the service will no longer be available.</span></span> <span data-ttu-id="74b2e-161">Lembre-se disso ao compartilhar o aplicativo para testes por outros usuários.</span><span class="sxs-lookup"><span data-stu-id="74b2e-161">Remember this when sharing the app for testing by other users.</span></span> <span data-ttu-id="74b2e-162">Se você tiver que reiniciar o serviço, ele retornará um novo endereço e você terá que atualizar todos os lugares que usarem esse endereço.</span><span class="sxs-lookup"><span data-stu-id="74b2e-162">If you have to restart the service it will return a new address and you will have to update every place that uses that address.</span></span>

<span data-ttu-id="74b2e-163">Lembre-se, anote a URL do seu aplicativo porque você precisará disso mais tarde quando registrar o aplicativo com Teams usando o estúdio App.</span><span class="sxs-lookup"><span data-stu-id="74b2e-163">Remember, make a note of the URL of your app because you will need this later when you register the app with Teams using App studio.</span></span> <span data-ttu-id="74b2e-164">Bloco de notas funciona bem para este fim.</span><span class="sxs-lookup"><span data-stu-id="74b2e-164">Notepad works fine for this purpose.</span></span>

<a name="DeployToTeams"></a>

## <a name="deploy-your-app-to-microsoft-teams"></a><span data-ttu-id="74b2e-165">Implante seu aplicativo para Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="74b2e-165">Deploy your app to Microsoft Teams</span></span>

<span data-ttu-id="74b2e-166">Neste ponto você tem um aplicativo hospedado na internet, mas você ainda não tem como dizer Teams onde procurá-lo, ou mesmo como seu aplicativo é chamado.</span><span class="sxs-lookup"><span data-stu-id="74b2e-166">At this point you have an app hosted on the internet, but you have no way yet of telling Teams where to look for it, or even what your app is called.</span></span> <span data-ttu-id="74b2e-167">Para fazer isso, agora você tem que criar um pacote de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="74b2e-167">To do this you now have to create an app package.</span></span> <span data-ttu-id="74b2e-168">Isso é pouco mais do que um arquivo de texto que contém o manifesto do aplicativo e alguns ícones que o Teams cliente usará para exibir e marcar corretamente seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="74b2e-168">This is little more than a text file that contains the app manifest and some icons that the Teams client will use to properly display and brand your app.</span></span> <span data-ttu-id="74b2e-169">Você pode criar manualmente este pacote de aplicativos, ou pode usar o App Studio, uma ferramenta que é executada em Teams que simplificará o processo de registro do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="74b2e-169">You can manually create this app package, or you can use App Studio, a tool that runs in Teams that will simplify the process of registering the app.</span></span> <span data-ttu-id="74b2e-170">App Studio é a maneira recomendada de criar e atualizar o pacote de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="74b2e-170">App Studio is the recommended way of creating and updating the app package.</span></span>

<span data-ttu-id="74b2e-171">Para qualquer outro método, você precisará do seguinte:</span><span class="sxs-lookup"><span data-stu-id="74b2e-171">For either method you will need the following:</span></span>

- <span data-ttu-id="74b2e-172">A URL onde seu aplicativo pode ser encontrado na internet.</span><span class="sxs-lookup"><span data-stu-id="74b2e-172">The URL where your app can be found on the internet.</span></span>
- <span data-ttu-id="74b2e-173">Ícones que Teams usarão para marcar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="74b2e-173">Icons that Teams will use to brand your app.</span></span> <span data-ttu-id="74b2e-174">A amostra vem com ícones de espaço reservado localizados em imagens "src\estática\.</span><span class="sxs-lookup"><span data-stu-id="74b2e-174">The sample comes with placeholder icons located in "src\static\images.</span></span> <span data-ttu-id="74b2e-175">O App Studio também fornecerá ícones padrão, se necessário.</span><span class="sxs-lookup"><span data-stu-id="74b2e-175">App Studio also will provide default icons if needed.</span></span>

[!include[Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-your-hosted-app"></a><span data-ttu-id="74b2e-176">Atualize seu aplicativo hospedado</span><span class="sxs-lookup"><span data-stu-id="74b2e-176">Update your hosted app</span></span>

<span data-ttu-id="74b2e-177">O aplicativo de amostra requer que as seguintes variáveis de ambiente sejam definidas para os valores que você fez uma nota anteriormente:</span><span class="sxs-lookup"><span data-stu-id="74b2e-177">The sample app requires the following environment variables to be set to the values you made a note of earlier:</span></span>

```
MICROSOFT_APP_ID=<YOUR BOT'S APP ID>
MICROSOFT_APP_PASSWORD=<YOUR BOT'S PASSWORD>
WEBSITE_NODE_DEFAULT_VERSION=8.9.4
```

<span data-ttu-id="74b2e-178">Como você faz isso difere dependendo de como você hospedou seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="74b2e-178">How you do that differs depending on how you hosted your app.</span></span> <span data-ttu-id="74b2e-179">O importante sobre o uso de variáveis ambientais é que esses valores fazem parte do seu ambiente - eles podem ser acessados pelo código do seu aplicativo, mas eles não estão expostos a terceiros que podem examinar os arquivos que compõem seu site.</span><span class="sxs-lookup"><span data-stu-id="74b2e-179">The important thing about using environment variables is that these values are part of your environment - they can be accessed by the code for your app, but they are not exposed to third parties who might examine the files that make up your site.</span></span>

<span data-ttu-id="74b2e-180">Se você estiver executando o aplicativo usando ngrok, você precisará configurar algumas variáveis ambientais locais.</span><span class="sxs-lookup"><span data-stu-id="74b2e-180">If you are running the app using ngrok you'll need to set up some local environment variables.</span></span> <span data-ttu-id="74b2e-181">Existem muitas maneiras de fazer isso, mas o mais fácil, se você estiver usando Visual Studio Code, é adicionar uma [configuração de lançamento:](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations)</span><span class="sxs-lookup"><span data-stu-id="74b2e-181">There are many ways to do this, but the easiest, if you are using Visual Studio Code, is to add a [launch configuration](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations):</span></span>

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

<span data-ttu-id="74b2e-182">Onde:</span><span class="sxs-lookup"><span data-stu-id="74b2e-182">Where:</span></span>

<span data-ttu-id="74b2e-183">MICROSOFT_APP_ID e MICROSOFT_APP_PASSWORD é o ID e senha, respectivamente, para o seu bot.</span><span class="sxs-lookup"><span data-stu-id="74b2e-183">MICROSOFT_APP_ID and MICROSOFT_APP_PASSWORD is the ID and password, respectively, for your bot.</span></span>
<span data-ttu-id="74b2e-184">NODE_DEBUG mostrará o que está acontecendo no seu bot no console de depuração Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="74b2e-184">NODE_DEBUG will show you what's happening in your bot in the Visual Studio Code debug console.</span></span>
<span data-ttu-id="74b2e-185">NODE_CONFIG_DIR aponta para o diretório na raiz do repositório (por padrão, quando o aplicativo é executado localmente, ele procura-o na pasta src).</span><span class="sxs-lookup"><span data-stu-id="74b2e-185">NODE_CONFIG_DIR points to the directory at the root of the repository (by default, when the app is run locally, it looks for it in the src folder).</span></span>

> [!Note]
> <span data-ttu-id="74b2e-186">Se você não parou npm de antes no tutorial, você precisará executar para que Visual Studio Code para pegar suas variáveis de configuração de `npm stop` lançamento corretamente.</span><span class="sxs-lookup"><span data-stu-id="74b2e-186">If you have not stopped npm from earlier in the tutorial, you'll need to run `npm stop` in order for Visual Studio Code to pickup your launch configuration variables correctly.</span></span>

<a name="ConfigureTheAppTab"></a>

## <a name="configure-the-app-tab"></a><span data-ttu-id="74b2e-187">Configure a guia do aplicativo</span><span class="sxs-lookup"><span data-stu-id="74b2e-187">Configure the app tab</span></span>

<span data-ttu-id="74b2e-188">Depois de instalar o aplicativo em uma equipe, você precisará configurá-lo para mostrar conteúdo.</span><span class="sxs-lookup"><span data-stu-id="74b2e-188">Once you install the app into a team, you will need to configure it to show content.</span></span> <span data-ttu-id="74b2e-189">Vá para um canal na equipe e clique no botão **'+'** para adicionar uma nova guia. Em seguida, você pode escolher `Hello World` entre a lista Adicionar uma **guia.**</span><span class="sxs-lookup"><span data-stu-id="74b2e-189">Go to a channel in the team and click on the **'+'** button to add a new tab. You can then choose `Hello World` from the **Add a tab** list.</span></span> <span data-ttu-id="74b2e-190">Em seguida, você será apresentado com um diálogo de configuração.</span><span class="sxs-lookup"><span data-stu-id="74b2e-190">You will then be presented with a configuration dialog.</span></span> <span data-ttu-id="74b2e-191">Esta caixa de diálogo permitirá que você escolha qual guia exibir neste canal.</span><span class="sxs-lookup"><span data-stu-id="74b2e-191">This dialog will let you choose which tab to display in this channel.</span></span> <span data-ttu-id="74b2e-192">Depois de selecionar a guia e `Save` clicar, você pode ver a `Hello World` guia carregada com a guia escolhida:</span><span class="sxs-lookup"><span data-stu-id="74b2e-192">Once you select the tab and click on `Save` you can see the `Hello World` tab loaded with the tab you chose:</span></span>

<img width="430px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png"/>

### <a name="test-your-bot-in-teams"></a><span data-ttu-id="74b2e-193">Teste seu bot em Teams</span><span class="sxs-lookup"><span data-stu-id="74b2e-193">Test your bot in Teams</span></span>

<span data-ttu-id="74b2e-194">Agora você pode interagir com o bot em Teams.</span><span class="sxs-lookup"><span data-stu-id="74b2e-194">You can now interact with the bot in Teams.</span></span> <span data-ttu-id="74b2e-195">Escolha um canal na equipe onde você registrou seu aplicativo e `@your-bot-name` digite , seguido de sua mensagem.</span><span class="sxs-lookup"><span data-stu-id="74b2e-195">Choose a channel in the team where you registered your app, and type `@your-bot-name`, followed by your message.</span></span> <span data-ttu-id="74b2e-196">Isso é chamado de **\@ menção.**</span><span class="sxs-lookup"><span data-stu-id="74b2e-196">This is called an **\@mention**.</span></span> <span data-ttu-id="74b2e-197">Qualquer mensagem que você enviar para o bot será enviada de volta para você como uma resposta:</span><span class="sxs-lookup"><span data-stu-id="74b2e-197">Whatever message you send to the bot will be sent back to you as a reply:</span></span>

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png"/>

<a name="ComposeRichMessages"></a>

### <a name="test-your-messaging-extension"></a><span data-ttu-id="74b2e-198">Teste sua extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="74b2e-198">Test your messaging extension</span></span>

<span data-ttu-id="74b2e-199">Para testar sua extensão de mensagens, você pode clicar nos três pontos abaixo da caixa de entrada na sua visualização de conversação.</span><span class="sxs-lookup"><span data-stu-id="74b2e-199">To test your messaging extension, you can click on the three dots below the input box in your conversation view.</span></span> <span data-ttu-id="74b2e-200">Um menu aparecerá com o aplicativo **'Hello World'** nele.</span><span class="sxs-lookup"><span data-stu-id="74b2e-200">A menu will pop up with the **'Hello World'** app in it.</span></span> <span data-ttu-id="74b2e-201">Quando você clicar nele, você verá uma série de textos aleatórios.</span><span class="sxs-lookup"><span data-stu-id="74b2e-201">When you click it, you will see a number of random texts.</span></span> <span data-ttu-id="74b2e-202">Você pode escolher qualquer um deles e ele será inserido em sua conversa:</span><span class="sxs-lookup"><span data-stu-id="74b2e-202">You can choose any one of them and it will be inserted it into your conversation:</span></span>

<img width="430px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="430px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

<span data-ttu-id="74b2e-203">Escolha um dos textos aleatórios e verá um cartão formatado e pronto para enviar com sua própria mensagem na parte inferior:</span><span class="sxs-lookup"><span data-stu-id="74b2e-203">Choose one of the random texts, and you will see a card formatted and ready to send with your own message at the bottom:</span></span>

<img width="430px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
