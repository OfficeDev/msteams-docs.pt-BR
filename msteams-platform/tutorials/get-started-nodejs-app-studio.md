---
title: Tutorial - Crie seu primeiro aplicativo usando Node.js
description: Saiba como começar a criar aplicativos do Microsoft Teams com Node.js.
keywords: getting started node.js nodejs App Studio
ms.topic: tutorial
ms.custom: scenarios:getting-started; languages:JavaScript,Node.js
ms.openlocfilehash: 61be1056a07952c6cf166dbe183fa257ceaf7227
ms.sourcegitcommit: 6ff8d1244ac386641ebf9401804b8df3854b02dc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/18/2021
ms.locfileid: "50294758"
---
# <a name="create-your-first-microsoft-teams-app-using-nodejs"></a><span data-ttu-id="7a494-104">Crie seu primeiro aplicativo do Microsoft Teams usando Node.js</span><span class="sxs-lookup"><span data-stu-id="7a494-104">Create your first Microsoft Teams app using Node.js</span></span>

<span data-ttu-id="7a494-105">Este tutorial ajuda você a começar a criar um aplicativo do Microsoft Teams usando Node.js.</span><span class="sxs-lookup"><span data-stu-id="7a494-105">This tutorial helps you get started creating a Microsoft Teams app using Node.js.</span></span>

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="DownloadAndHost"></a>

## <a name="download-and-host-your-app"></a><span data-ttu-id="7a494-106">Baixar e hospedar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="7a494-106">Download and host your app</span></span>

<span data-ttu-id="7a494-107">Siga estas etapas para baixar e hospedar um aplicativo simples "hello world" no Teams.</span><span class="sxs-lookup"><span data-stu-id="7a494-107">Follow these steps to download and host a simple "hello world" app in Teams.</span></span>

<a name="GetPrerequisites"></a>

### <a name="get-prerequisites"></a><span data-ttu-id="7a494-108">Obter pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="7a494-108">Get prerequisites</span></span>

<span data-ttu-id="7a494-109">Para concluir este tutorial, você precisa das seguintes ferramentas.</span><span class="sxs-lookup"><span data-stu-id="7a494-109">To complete this tutorial, you need the following tools.</span></span> <span data-ttu-id="7a494-110">Se você ainda não os tiver, poderá instalá-los a partir desses links.</span><span class="sxs-lookup"><span data-stu-id="7a494-110">If you don't already have them you can install them from these links.</span></span>

- [<span data-ttu-id="7a494-111">Git</span><span class="sxs-lookup"><span data-stu-id="7a494-111">Git</span></span>](https://git-scm.com/downloads)
- [<span data-ttu-id="7a494-112">Node.js e NPM</span><span class="sxs-lookup"><span data-stu-id="7a494-112">Node.js and NPM</span></span>](https://nodejs.org/)
- <span data-ttu-id="7a494-113">Obter qualquer editor de texto ou IDE.</span><span class="sxs-lookup"><span data-stu-id="7a494-113">Get any text editor or IDE.</span></span> <span data-ttu-id="7a494-114">Você pode instalar e usar [Visual Studio Código](https://code.visualstudio.com/download) gratuitamente.</span><span class="sxs-lookup"><span data-stu-id="7a494-114">You can install and use [Visual Studio Code](https://code.visualstudio.com/download) for free.</span></span>

<span data-ttu-id="7a494-115">Se você vir opções para adicionar , , e ao PATH durante a `git` `node` `npm` `code` instalação, escolha fazer isso.</span><span class="sxs-lookup"><span data-stu-id="7a494-115">If you see options to add `git`, `node`, `npm`, and `code` to the PATH during installation, choose to do so.</span></span> <span data-ttu-id="7a494-116">Ele será útil.</span><span class="sxs-lookup"><span data-stu-id="7a494-116">It will be handy.</span></span>

<span data-ttu-id="7a494-117">Verifique se as ferramentas estão disponíveis executando o seguinte em uma janela de terminal:</span><span class="sxs-lookup"><span data-stu-id="7a494-117">Verify that the tools are available by running the following in a terminal window:</span></span>

> [!NOTE]
> <span data-ttu-id="7a494-118">Use a janela de terminal com a que você está mais confortável em sua plataforma.</span><span class="sxs-lookup"><span data-stu-id="7a494-118">Use the terminal window that you are most comfortable with on your platform.</span></span> <span data-ttu-id="7a494-119">Esses exemplos usam Bash (que está incluído no Git), mas esses scripts serão executados na maioria das plataformas.</span><span class="sxs-lookup"><span data-stu-id="7a494-119">These examples use Bash (which is included in Git), but these scripts will run on most platforms.</span></span>

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

<span data-ttu-id="7a494-120">Você pode ter uma versão diferente desses aplicativos.</span><span class="sxs-lookup"><span data-stu-id="7a494-120">You may have a different version of these applications.</span></span> <span data-ttu-id="7a494-121">Isso não deve ser um problema, exceto gulp.</span><span class="sxs-lookup"><span data-stu-id="7a494-121">This should not be a problem, except for gulp.</span></span> <span data-ttu-id="7a494-122">Para gulp, você precisará usar a versão 4.0.0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="7a494-122">For gulp you'll need to use version 4.0.0 or later.</span></span>

<span data-ttu-id="7a494-123">Se você não tiver o gulp instalado (ou tiver a versão errada instalada), faça isso agora executando `npm install gulp` na janela do terminal.</span><span class="sxs-lookup"><span data-stu-id="7a494-123">If you don't have gulp installed (or have the wrong version installed), do so now by running `npm install gulp` in your terminal window.</span></span>

<span data-ttu-id="7a494-124">Se você tiver instalado Visual Studio Código, poderá verificar a instalação executando:</span><span class="sxs-lookup"><span data-stu-id="7a494-124">If you have installed Visual Studio Code, you can verify the installation by running:</span></span>

```bash
code --version
1.28.2
929bacba01ef658b873545e26034d1a8067445e9
```

<span data-ttu-id="7a494-125">Você pode continuar a usar essa janela de terminal para executar os comandos a seguir neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="7a494-125">You can continue to use this terminal window to run the commands that follow in this tutorial.</span></span>

<a name="DownloadSample"></a>

### <a name="download-the-sample"></a><span data-ttu-id="7a494-126">Baixar o exemplo</span><span class="sxs-lookup"><span data-stu-id="7a494-126">Download the sample</span></span>

<span data-ttu-id="7a494-127">Fornecemos um [Hello, World simples!](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/nodejs)</span><span class="sxs-lookup"><span data-stu-id="7a494-127">We have provided a simple [Hello, World!](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/nodejs)</span></span> <span data-ttu-id="7a494-128">exemplo para começar.</span><span class="sxs-lookup"><span data-stu-id="7a494-128">sample to get you started.</span></span> <span data-ttu-id="7a494-129">Em uma janela de terminal, execute o seguinte comando para clonar o repositório de exemplo para o computador local:</span><span class="sxs-lookup"><span data-stu-id="7a494-129">In a terminal window, run the following command to clone the sample repository to your local machine:</span></span>

```bash
git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
```

> [!TIP]
> <span data-ttu-id="7a494-130">Você pode [bifurcar](https://help.github.com/articles/fork-a-repo/) [esse repositório](https://github.com/OfficeDev/Microsoft-Teams-Samples) se quiser modificar e verificar suas alterações no repositório do GitHub para referência futura.</span><span class="sxs-lookup"><span data-stu-id="7a494-130">You can [fork](https://help.github.com/articles/fork-a-repo/) this [repo](https://github.com/OfficeDev/Microsoft-Teams-Samples) if you want to modify and check in your changes to your GitHub repo for future reference.</span></span>

<a name="BuildRun"></a>

### <a name="build-and-run-the-sample"></a><span data-ttu-id="7a494-131">Criar e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="7a494-131">Build and run the sample</span></span>

<span data-ttu-id="7a494-132">Depois que o repo for clonado, altere para o diretório que contém o exemplo:</span><span class="sxs-lookup"><span data-stu-id="7a494-132">Once the repo is cloned, change to the directory that holds the sample:</span></span>

```bash
cd Microsoft-Teams-Samples/samples/app-hello-world/nodejs/
```

<span data-ttu-id="7a494-133">Para criar o exemplo, você precisa instalar todas as suas dependências.</span><span class="sxs-lookup"><span data-stu-id="7a494-133">In order to build the sample, you need to install all its dependencies.</span></span> <span data-ttu-id="7a494-134">Execute o seguinte comando para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="7a494-134">Run the following command to do this:</span></span>

```bash
npm install
```

<span data-ttu-id="7a494-135">Você deve ver várias dependências sendo instaladas.</span><span class="sxs-lookup"><span data-stu-id="7a494-135">You should see a bunch of dependencies getting installed.</span></span> <span data-ttu-id="7a494-136">Depois que eles terminarem, você poderá executar o aplicativo:</span><span class="sxs-lookup"><span data-stu-id="7a494-136">Once they are finished, you can run the app:</span></span>

```bash
npm start
```

<span data-ttu-id="7a494-137">Quando o aplicativo hello-world é iniciado, ele é `App started listening on port 3333` exibido na janela do terminal.</span><span class="sxs-lookup"><span data-stu-id="7a494-137">When the hello-world app starts, it displays `App started listening on port 3333` in the terminal window.</span></span>

> [!NOTE]
> <span data-ttu-id="7a494-138">Se você vir um número de porta diferente exibido na mensagem acima, é porque você tem uma variável de ambiente PORT definida.</span><span class="sxs-lookup"><span data-stu-id="7a494-138">If you see a different port number displayed in the message above, it is because you have a PORT environment variable set.</span></span> <span data-ttu-id="7a494-139">Você pode continuar a usar essa porta ou alterar sua variável de ambiente para 3333.</span><span class="sxs-lookup"><span data-stu-id="7a494-139">You can continue to use that port or change your environment variable to 3333.</span></span>

<span data-ttu-id="7a494-140">Neste ponto, você pode abrir uma janela do navegador e navegar até as SEGUINTES URLs para verificar se todas as URLs do aplicativo estão sendo carregadas:</span><span class="sxs-lookup"><span data-stu-id="7a494-140">At this point, you can open a browser window and navigate to the following URLs to verify that all the app URLs are loading:</span></span>

- [http://localhost:3333](http://localhost:3333)
- [http://localhost:3333/hello](http://localhost:3333/hello)
- [http://localhost:3333/first](http://localhost:3333/first)
- [http://localhost:3333/second](http://localhost:3333/second)

<a name="HostSample"></a>

### <a name="host-the-sample-app"></a><span data-ttu-id="7a494-141">Hospedar o aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="7a494-141">Host the sample app</span></span>

<span data-ttu-id="7a494-142">Lembre-se de que os aplicativos no Microsoft Teams são aplicativos Web expondo um ou mais recursos.</span><span class="sxs-lookup"><span data-stu-id="7a494-142">Remember that apps in Microsoft Teams are web applications exposing one or more capabilities.</span></span> <span data-ttu-id="7a494-143">Para que a plataforma do Teams carregue seu aplicativo, seu aplicativo deve ser acessível pela Internet.</span><span class="sxs-lookup"><span data-stu-id="7a494-143">For the Teams platform to load your app, your app must be reachable from the internet.</span></span> <span data-ttu-id="7a494-144">Para tornar seu aplicativo acessível pela Internet, você precisa *hospedar* seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7a494-144">To make your app reachable from the internet, you need to *host* your app.</span></span>

<span data-ttu-id="7a494-145">Para testes locais, você pode executar o aplicativo em sua máquina local e criar um túnel para ele com um ponto de extremidade da Web.</span><span class="sxs-lookup"><span data-stu-id="7a494-145">For local testing you can run the app on your local machine and create a tunnel to it with a web endpoint.</span></span> <span data-ttu-id="7a494-146">[ngrok](https://ngrok.com) é uma ferramenta gratuita que permite que você faça exatamente isso.</span><span class="sxs-lookup"><span data-stu-id="7a494-146">[ngrok](https://ngrok.com) is a free tool that lets you do just that.</span></span> <span data-ttu-id="7a494-147">Com *o ngrok,* você pode obter um endereço da Web como `https://d0ac14a5.ngrok.io` (essa URL é apenas um exemplo).</span><span class="sxs-lookup"><span data-stu-id="7a494-147">With *ngrok* you can get a web address such as `https://d0ac14a5.ngrok.io` (this URL is just an example).</span></span> <span data-ttu-id="7a494-148">Você pode [baixar e instalar](https://ngrok.com/download) o *ngrok* para seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="7a494-148">You can [download and install](https://ngrok.com/download) *ngrok* for your environment.</span></span> <span data-ttu-id="7a494-149">Certifique-se de adicioná-lo a um local em seu `PATH` .</span><span class="sxs-lookup"><span data-stu-id="7a494-149">Make sure you add it to a location in your `PATH`.</span></span>

<span data-ttu-id="7a494-150">Depois de instalá-la, você pode abrir uma nova janela de terminal e executar o seguinte comando para criar um túnel.</span><span class="sxs-lookup"><span data-stu-id="7a494-150">Once you install it, you can open a new terminal window and run the following command to create a tunnel.</span></span> <span data-ttu-id="7a494-151">O exemplo usa a porta 3333, portanto, certifique-se de especificá-la aqui.</span><span class="sxs-lookup"><span data-stu-id="7a494-151">The sample uses port 3333, so be sure to specify it here.</span></span>

```bash
ngrok http 3333 -host-header=localhost:3333
```

<span data-ttu-id="7a494-152">*O Ngrok* ouvirá as solicitações da Internet e as encaminhará para seu aplicativo em execução na porta 3333.</span><span class="sxs-lookup"><span data-stu-id="7a494-152">*Ngrok* will listen to requests from the internet and will route them to your app running on port 3333.</span></span> <span data-ttu-id="7a494-153">Você pode verificar abrindo seu navegador e `https://d0ac14a5.ngrok.io/hello` carregando a página hello do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7a494-153">You can verify by opening your browser and going to `https://d0ac14a5.ngrok.io/hello` to load your app's hello page.</span></span> <span data-ttu-id="7a494-154">Certifique-se de usar o endereço de encaminhamento exibido pelo *ngrok* em sua sessão de console em vez dessa URL.</span><span class="sxs-lookup"><span data-stu-id="7a494-154">Please be sure to use the forwarding address displayed by *ngrok* in your console session instead of this URL.</span></span>

> [!NOTE]
> <span data-ttu-id="7a494-155">Se você tiver usado uma porta diferente na [com](#build-and-run-the-sample) build e execute a etapa acima, certifique-se de usar o mesmo número de porta para configurar o *túnel ngrok.*</span><span class="sxs-lookup"><span data-stu-id="7a494-155">If you have used a different port in the [build and run](#build-and-run-the-sample) step above, make sure you use the same port number to setup the *ngrok* tunnel.</span></span>
> [!TIP]
> <span data-ttu-id="7a494-156">É uma boa ideia executar *o ngrok* em uma janela de terminal diferente para mantê-lo em execução sem interferir no aplicativo de nó que talvez você tenha que parar, recriar e executar de novo.</span><span class="sxs-lookup"><span data-stu-id="7a494-156">It is a good idea to run *ngrok* in a different terminal window to keep it running without interfering with the node app which you might later have to stop, rebuild and rerun.</span></span> <span data-ttu-id="7a494-157">A *sessão ngrok* retornará informações úteis de depuração nesta janela.</span><span class="sxs-lookup"><span data-stu-id="7a494-157">The *ngrok* session will return useful debugging information in this window.</span></span>

<span data-ttu-id="7a494-158">Há uma versão paga do *ngrok* que permite nomes persistentes.</span><span class="sxs-lookup"><span data-stu-id="7a494-158">There is a paid version of *ngrok* that allows persistent names.</span></span> <span data-ttu-id="7a494-159">Se você usar a versão gratuita, seu aplicativo só estará disponível durante a sessão atual em seu computador de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="7a494-159">If you use the free version your app will only be available during the current session on your development machine.</span></span> <span data-ttu-id="7a494-160">Se o computador for desligado ou for parar, o serviço não estará mais disponível.</span><span class="sxs-lookup"><span data-stu-id="7a494-160">If the machine is shut down or goes to sleep the service will no longer be available.</span></span> <span data-ttu-id="7a494-161">Lembre-se disso ao compartilhar o aplicativo para teste por outros usuários.</span><span class="sxs-lookup"><span data-stu-id="7a494-161">Remember this when sharing the app for testing by other users.</span></span> <span data-ttu-id="7a494-162">Se você tiver que reiniciar o serviço, ele retornará um novo endereço e será preciso atualizar todos os lugares que usam esse endereço.</span><span class="sxs-lookup"><span data-stu-id="7a494-162">If you have to restart the service it will return a new address and you will have to update every place that uses that address.</span></span>

<span data-ttu-id="7a494-163">Lembre-se de anotar a URL do seu aplicativo porque você precisará disso mais tarde quando registrar o aplicativo com o Teams usando o App studio.</span><span class="sxs-lookup"><span data-stu-id="7a494-163">Remember, make a note of the URL of your app because you will need this later when you register the app with Teams using App studio.</span></span> <span data-ttu-id="7a494-164">O bloco de notas funciona bem para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="7a494-164">Notepad works fine for this purpose.</span></span>

<a name="DeployToTeams"></a>

## <a name="deploy-your-app-to-microsoft-teams"></a><span data-ttu-id="7a494-165">Implantar seu aplicativo no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="7a494-165">Deploy your app to Microsoft Teams</span></span>

<span data-ttu-id="7a494-166">Neste ponto, você tem um aplicativo hospedado na Internet, mas ainda não tem como dizer ao Teams onde procurar por ele ou mesmo como seu aplicativo é chamado.</span><span class="sxs-lookup"><span data-stu-id="7a494-166">At this point you have an app hosted on the internet, but you have no way yet of telling Teams where to look for it, or even what your app is called.</span></span> <span data-ttu-id="7a494-167">Para fazer isso, agora você precisa criar um pacote de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="7a494-167">To do this you now have to create an app package.</span></span> <span data-ttu-id="7a494-168">Isso é pouco mais do que um arquivo de texto que contém o manifesto do aplicativo e alguns ícones que o cliente do Teams usará para exibir e sinalizar corretamente seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7a494-168">This is little more than a text file that contains the app manifest and some icons that the Teams client will use to properly display and brand your app.</span></span> <span data-ttu-id="7a494-169">Você pode criar manualmente esse pacote de aplicativos ou usar o App Studio, uma ferramenta que é executado no Teams que simplificará o processo de registro do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7a494-169">You can manually create this app package, or you can use App Studio, a tool that runs in Teams that will simplify the process of registering the app.</span></span> <span data-ttu-id="7a494-170">App Studio é a maneira recomendada de criar e atualizar o pacote de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="7a494-170">App Studio is the recommended way of creating and updating the app package.</span></span>

<span data-ttu-id="7a494-171">Para qualquer um dos métodos, você precisará do seguinte:</span><span class="sxs-lookup"><span data-stu-id="7a494-171">For either method you will need the following:</span></span>

- <span data-ttu-id="7a494-172">A URL onde seu aplicativo pode ser encontrado na Internet.</span><span class="sxs-lookup"><span data-stu-id="7a494-172">The URL where your app can be found on the internet.</span></span>
- <span data-ttu-id="7a494-173">Ícones que o Teams usará para fazer a marca do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7a494-173">Icons that Teams will use to brand your app.</span></span> <span data-ttu-id="7a494-174">O exemplo vem com ícones de espaço reservado localizados em "src\static\images.</span><span class="sxs-lookup"><span data-stu-id="7a494-174">The sample comes with placeholder icons located in "src\static\images.</span></span> <span data-ttu-id="7a494-175">O App Studio também fornecerá ícones padrão, se necessário.</span><span class="sxs-lookup"><span data-stu-id="7a494-175">App Studio also will provide default icons if needed.</span></span>

[!include[Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-your-hosted-app"></a><span data-ttu-id="7a494-176">Atualizar seu aplicativo hospedado</span><span class="sxs-lookup"><span data-stu-id="7a494-176">Update your hosted app</span></span>

<span data-ttu-id="7a494-177">O aplicativo de exemplo exige que as seguintes variáveis de ambiente sejam definidas para os valores que você fez uma anotação anteriormente.</span><span class="sxs-lookup"><span data-stu-id="7a494-177">The sample app requires the following environment variables to be set to the values you made a note of earlier.</span></span>

```
MICROSOFT_APP_ID=<YOUR BOT'S APP ID>
MICROSOFT_APP_PASSWORD=<YOUR BOT'S PASSWORD>
WEBSITE_NODE_DEFAULT_VERSION=8.9.4
```

<span data-ttu-id="7a494-178">Como fazer isso difere dependendo de como você hospedou seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7a494-178">How you do that differs depending on how you hosted your app.</span></span> <span data-ttu-id="7a494-179">O importante sobre o uso de variáveis de ambiente é que esses valores fazem parte do seu ambiente - eles podem ser acessados pelo código para seu aplicativo, mas não são expostos a terceiros que podem examinar os arquivos que compusem seu site.</span><span class="sxs-lookup"><span data-stu-id="7a494-179">The important thing about using environment variables is that these values are part of your environment - they can be accessed by the code for your app, but they are not exposed to third parties who might examine the files that make up your site.</span></span>

<span data-ttu-id="7a494-180">Se você estiver executando o aplicativo usando o ngrok, precisará configurar algumas variáveis de ambiente local.</span><span class="sxs-lookup"><span data-stu-id="7a494-180">If you are running the app using ngrok you'll need to set up some local environment variables.</span></span> <span data-ttu-id="7a494-181">Há muitas maneiras de fazer isso, mas a mais fácil, se você estiver usando Visual Studio Código, é adicionar uma configuração [de lançamento](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations):</span><span class="sxs-lookup"><span data-stu-id="7a494-181">There are many ways to do this, but the easiest, if you are using Visual Studio Code, is to add a [launch configuration](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations):</span></span>

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

<span data-ttu-id="7a494-182">Onde:</span><span class="sxs-lookup"><span data-stu-id="7a494-182">Where:</span></span>

<span data-ttu-id="7a494-183">MICROSOFT_APP_ID e MICROSOFT_APP_PASSWORD é a ID e a senha, respectivamente, para seu bot.</span><span class="sxs-lookup"><span data-stu-id="7a494-183">MICROSOFT_APP_ID and MICROSOFT_APP_PASSWORD is the ID and password, respectively, for your bot.</span></span>
<span data-ttu-id="7a494-184">NODE_DEBUG mostrará o que está acontecendo no bot no Visual Studio depuração de código.</span><span class="sxs-lookup"><span data-stu-id="7a494-184">NODE_DEBUG will show you what's happening in your bot in the Visual Studio Code debug console.</span></span>
<span data-ttu-id="7a494-185">NODE_CONFIG_DIR aponta para o diretório na raiz do repositório (por padrão, quando o aplicativo é executado localmente, ele procura por ele na pasta src).</span><span class="sxs-lookup"><span data-stu-id="7a494-185">NODE_CONFIG_DIR points to the directory at the root of the repository (by default, when the app is run locally, it looks for it in the src folder).</span></span>

> [!Note]
> <span data-ttu-id="7a494-186">Se você não tiver interrompido npm de anteriormente no tutorial, você precisará executar para que o código Visual Studio para receber suas variáveis de configuração de `npm stop` início corretamente.</span><span class="sxs-lookup"><span data-stu-id="7a494-186">If you have not stopped npm from earlier in the tutorial, you'll need to run `npm stop` in order for Visual Studio Code to pickup your launch configuration variables correctly.</span></span>

<a name="ConfigureTheAppTab"></a>

## <a name="configure-the-app-tab"></a><span data-ttu-id="7a494-187">Configurar a guia do aplicativo</span><span class="sxs-lookup"><span data-stu-id="7a494-187">Configure the app tab</span></span>

<span data-ttu-id="7a494-188">Depois de instalar o aplicativo em uma equipe, você precisará configurá-lo para mostrar conteúdo.</span><span class="sxs-lookup"><span data-stu-id="7a494-188">Once you install the app into a team, you will need to configure it to show content.</span></span> <span data-ttu-id="7a494-189">Vá para um canal na equipe e clique no botão **'+'** para adicionar uma nova guia. Em seguida, você pode `Hello World` escolher na lista Adicionar **uma** guia.</span><span class="sxs-lookup"><span data-stu-id="7a494-189">Go to a channel in the team and click on the **'+'** button to add a new tab. You can then choose `Hello World` from the **Add a tab** list.</span></span> <span data-ttu-id="7a494-190">Em seguida, você será apresentado com uma caixa de diálogo de configuração.</span><span class="sxs-lookup"><span data-stu-id="7a494-190">You will then be presented with a configuration dialog.</span></span> <span data-ttu-id="7a494-191">Essa caixa de diálogo permitirá que você escolha qual guia exibir neste canal.</span><span class="sxs-lookup"><span data-stu-id="7a494-191">This dialog will let you choose which tab to display in this channel.</span></span> <span data-ttu-id="7a494-192">Depois de selecionar a guia e clicar em, você poderá ver a `Save` guia carregada com a guia `Hello World` escolhida.</span><span class="sxs-lookup"><span data-stu-id="7a494-192">Once you select the tab and click on `Save` you can see the `Hello World` tab loaded with the tab you chose.</span></span>

<img width="430px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png"/>

### <a name="test-your-bot-in-teams"></a><span data-ttu-id="7a494-193">Testar seu bot no Teams</span><span class="sxs-lookup"><span data-stu-id="7a494-193">Test your bot in Teams</span></span>

<span data-ttu-id="7a494-194">Agora você pode interagir com o bot no Teams.</span><span class="sxs-lookup"><span data-stu-id="7a494-194">You can now interact with the bot in Teams.</span></span> <span data-ttu-id="7a494-195">Escolha um canal na equipe em que você registrou seu aplicativo e digite `@your-bot-name` , seguido de sua mensagem.</span><span class="sxs-lookup"><span data-stu-id="7a494-195">Choose a channel in the team where you registered your app, and type `@your-bot-name`, followed by your message.</span></span> <span data-ttu-id="7a494-196">Isso é chamado de **\@ menção**.</span><span class="sxs-lookup"><span data-stu-id="7a494-196">This is called an **\@mention**.</span></span> <span data-ttu-id="7a494-197">Qualquer mensagem que você enviar para o bot será enviada de volta como uma resposta.</span><span class="sxs-lookup"><span data-stu-id="7a494-197">Whatever message you send to the bot will be sent back to you as a reply.</span></span>

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png"/>

<a name="ComposeRichMessages"></a>

### <a name="test-your-messaging-extension"></a><span data-ttu-id="7a494-198">Testar sua extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="7a494-198">Test your messaging extension</span></span>

<span data-ttu-id="7a494-199">Para testar sua extensão de mensagens, você pode clicar nos três pontos abaixo da caixa de entrada no seu exibição de conversa.</span><span class="sxs-lookup"><span data-stu-id="7a494-199">To test your messaging extension, you can click on the three dots below the input box in your conversation view.</span></span> <span data-ttu-id="7a494-200">Um menu será aberto com o **aplicativo "Hello World"** nele.</span><span class="sxs-lookup"><span data-stu-id="7a494-200">A menu will pop up with the **'Hello World'** app in it.</span></span> <span data-ttu-id="7a494-201">Ao clicar nele, você verá vários textos aleatórios.</span><span class="sxs-lookup"><span data-stu-id="7a494-201">When you click it, you will see a number of random texts.</span></span> <span data-ttu-id="7a494-202">Você pode escolher qualquer um deles e ele será inserido em sua conversa.</span><span class="sxs-lookup"><span data-stu-id="7a494-202">You can choose any one of them and it will be inserted it into your conversation.</span></span>

<img width="430px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="430px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

<span data-ttu-id="7a494-203">Escolha um dos textos aleatórios e você verá um cartão formatado e pronto para enviar com sua própria mensagem na parte inferior.</span><span class="sxs-lookup"><span data-stu-id="7a494-203">Choose one of the random texts, and you will see a card formatted and ready to send with your own message at the bottom.</span></span>

<img width="430px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
