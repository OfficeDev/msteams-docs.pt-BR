---
title: Introdução ao app Studio e Node.js
description: Introdução à criação de aplicativos ótimos no Microsoft Teams usando o Node.js e o app Studio
keywords: introdução node.js NodeJS app Studio
ms.topic: tutorial
ms.custom: scenarios:getting-started; languages:JavaScript,Node.js
ms.openlocfilehash: 3d86738d32c049d31a84c6c47746e275db5e6349
ms.sourcegitcommit: 99c35de7e2c604bd8bce392242c2c2fa709cd50b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/06/2020
ms.locfileid: "48931810"
---
# <a name="get-started-on-the-microsoft-teams-platform-with-nodejs-and-app-studio"></a><span data-ttu-id="6c099-104">Introdução à plataforma do Microsoft Teams com o Node.js e o app Studio</span><span class="sxs-lookup"><span data-stu-id="6c099-104">Get started on the Microsoft Teams platform with Node.js and App Studio</span></span>

<span data-ttu-id="6c099-105">A plataforma de desenvolvedor do [Microsoft Teams](/microsoftteams/) facilita a extensão de equipes e a integração de seus próprios aplicativos e serviços diretamente no espaço de trabalho do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="6c099-105">The [Microsoft Teams](/microsoftteams/) developer platform makes it easy for you to extend Teams and integrate your own applications and services seamlessly into the Teams workspace.</span></span> <span data-ttu-id="6c099-106">Esses aplicativos podem ser distribuídos para sua empresa ou para o Teams em todo o mundo.</span><span class="sxs-lookup"><span data-stu-id="6c099-106">These apps can then be distributed to your enterprise or for teams around the world.</span></span>

<span data-ttu-id="6c099-107">Para estender o Microsoft Teams, você precisa criar um aplicativo do Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="6c099-107">To extend Microsoft Teams, you need to create a Microsoft Teams app.</span></span> <span data-ttu-id="6c099-108">Um aplicativo do Microsoft Teams é um aplicativo Web que você hospeda.</span><span class="sxs-lookup"><span data-stu-id="6c099-108">A Microsoft Teams app is a web application that you host.</span></span> <span data-ttu-id="6c099-109">Esse aplicativo pode ser integrado ao espaço de trabalho do usuário no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="6c099-109">This app can then be integrated into the user's workspace in Teams.</span></span>

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="DownloadAndHost"></a>

## <a name="download-and-host-your-app"></a><span data-ttu-id="6c099-110">Baixar e hospedar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="6c099-110">Download and host your app</span></span>

<span data-ttu-id="6c099-111">Siga estas etapas para baixar e hospedar um aplicativo simples "Olá mundo" no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="6c099-111">Follow these steps to download and host a simple "hello world" app in Teams.</span></span>

<a name="GetPrerequisites"></a>

### <a name="get-prerequisites"></a><span data-ttu-id="6c099-112">Obter pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="6c099-112">Get prerequisites</span></span>

<span data-ttu-id="6c099-113">Para concluir este tutorial, você precisa das ferramentas a seguir.</span><span class="sxs-lookup"><span data-stu-id="6c099-113">To complete this tutorial, you need the following tools.</span></span> <span data-ttu-id="6c099-114">Se você ainda não os tiver, poderá instalá-los a partir desses links.</span><span class="sxs-lookup"><span data-stu-id="6c099-114">If you don't already have them you can install them from these links.</span></span>

- [<span data-ttu-id="6c099-115">Git</span><span class="sxs-lookup"><span data-stu-id="6c099-115">Git</span></span>](https://git-scm.com/downloads)
- [<span data-ttu-id="6c099-116">Node.js e NPM</span><span class="sxs-lookup"><span data-stu-id="6c099-116">Node.js and NPM</span></span>](https://nodejs.org/)
- <span data-ttu-id="6c099-117">Obtenha qualquer editor de texto ou IDE.</span><span class="sxs-lookup"><span data-stu-id="6c099-117">Get any text editor or IDE.</span></span> <span data-ttu-id="6c099-118">Você pode instalar e usar o [Visual Studio Code](https://code.visualstudio.com/download) gratuitamente.</span><span class="sxs-lookup"><span data-stu-id="6c099-118">You can install and use [Visual Studio Code](https://code.visualstudio.com/download) for free.</span></span>

<span data-ttu-id="6c099-119">Se você vir opções para adicionar `git` , `node` , `npm` e `code` ao caminho durante a instalação, escolha fazer isso.</span><span class="sxs-lookup"><span data-stu-id="6c099-119">If you see options to add `git`, `node`, `npm`, and `code` to the PATH during installation, choose to do so.</span></span> <span data-ttu-id="6c099-120">Será útil.</span><span class="sxs-lookup"><span data-stu-id="6c099-120">It will be handy.</span></span>

<span data-ttu-id="6c099-121">Verifique se as ferramentas estão disponíveis executando o seguinte em uma janela de terminal:</span><span class="sxs-lookup"><span data-stu-id="6c099-121">Verify that the tools are available by running the following in a terminal window:</span></span>

> [!NOTE]
> <span data-ttu-id="6c099-122">Use a janela do terminal com a qual você se sente mais confortável em sua plataforma.</span><span class="sxs-lookup"><span data-stu-id="6c099-122">Use the terminal window that you are most comfortable with on your platform.</span></span> <span data-ttu-id="6c099-123">Estes exemplos usam o bash (incluído no git), mas esses scripts serão executados na maioria das plataformas.</span><span class="sxs-lookup"><span data-stu-id="6c099-123">These examples use Bash (which is included in Git), but these scripts will run on most platforms.</span></span>

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

<span data-ttu-id="6c099-124">Você pode ter uma versão diferente desses aplicativos.</span><span class="sxs-lookup"><span data-stu-id="6c099-124">You may have a different version of these applications.</span></span> <span data-ttu-id="6c099-125">Isso não deve ser um problema, exceto para o Gulp.</span><span class="sxs-lookup"><span data-stu-id="6c099-125">This should not be a problem, except for gulp.</span></span> <span data-ttu-id="6c099-126">Para o Gulp, você precisará usar a versão 4.0.0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="6c099-126">For gulp you'll need to use version 4.0.0 or later.</span></span>

<span data-ttu-id="6c099-127">Se você não tiver o Gulp instalado (ou se tiver a versão incorreta instalada), faça-o agora executando `npm install gulp` na janela do terminal.</span><span class="sxs-lookup"><span data-stu-id="6c099-127">If you don't have gulp installed (or have the wrong version installed), do so now by running `npm install gulp` in your terminal window.</span></span>

<span data-ttu-id="6c099-128">Se você tiver instalado o Visual Studio Code, é possível verificar a instalação executando:</span><span class="sxs-lookup"><span data-stu-id="6c099-128">If you have installed Visual Studio Code, you can verify the installation by running:</span></span>

```bash
code --version
1.28.2
929bacba01ef658b873545e26034d1a8067445e9
```

<span data-ttu-id="6c099-129">Você pode continuar a usar esta janela de terminal para executar os comandos a seguir neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="6c099-129">You can continue to use this terminal window to run the commands that follow in this tutorial.</span></span>

<a name="DownloadSample"></a>

### <a name="download-the-sample"></a><span data-ttu-id="6c099-130">Baixar o exemplo</span><span class="sxs-lookup"><span data-stu-id="6c099-130">Download the sample</span></span>

<span data-ttu-id="6c099-131">Fornecemos um simples [Olá, mundo!](https://github.com/OfficeDev/msteams-samples-hello-world-nodejs)</span><span class="sxs-lookup"><span data-stu-id="6c099-131">We have provided a simple [Hello, World!](https://github.com/OfficeDev/msteams-samples-hello-world-nodejs)</span></span> <span data-ttu-id="6c099-132">exemplo para começar.</span><span class="sxs-lookup"><span data-stu-id="6c099-132">sample to get you started.</span></span> <span data-ttu-id="6c099-133">Em uma janela de terminal, execute o seguinte comando para clonar o repositório de exemplo para sua máquina local:</span><span class="sxs-lookup"><span data-stu-id="6c099-133">In a terminal window, run the following command to clone the sample repository to your local machine:</span></span>

```bash
git clone https://github.com/OfficeDev/msteams-samples-hello-world-nodejs.git
```

> [!TIP]
> <span data-ttu-id="6c099-134">Você pode [bifurcar](https://help.github.com/articles/fork-a-repo/) este [repositório](https://github.com/OfficeDev/msteams-samples-hello-world-nodejs) se quiser modificar e fazer check-in de suas alterações no repositório do GitHub para referência futura.</span><span class="sxs-lookup"><span data-stu-id="6c099-134">You can [fork](https://help.github.com/articles/fork-a-repo/) this [repo](https://github.com/OfficeDev/msteams-samples-hello-world-nodejs) if you want to modify and check in your changes to your GitHub repo for future reference.</span></span>

<a name="BuildRun"></a>

### <a name="build-and-run-the-sample"></a><span data-ttu-id="6c099-135">Criar e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="6c099-135">Build and run the sample</span></span>

<span data-ttu-id="6c099-136">Depois que o repositório for clonado, mude para o diretório que contém o exemplo:</span><span class="sxs-lookup"><span data-stu-id="6c099-136">Once the repo is cloned, change to the directory that holds the sample:</span></span>

```bash
cd msteams-samples-hello-world-nodejs
```

<span data-ttu-id="6c099-137">Para criar o exemplo, você precisa instalar todas as suas dependências.</span><span class="sxs-lookup"><span data-stu-id="6c099-137">In order to build the sample, you need to install all its dependencies.</span></span> <span data-ttu-id="6c099-138">Execute o seguinte comando para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="6c099-138">Run the following command to do this:</span></span>

```bash
npm install
```

<span data-ttu-id="6c099-139">Você deve ver uma porção de dependências que está sendo instalada.</span><span class="sxs-lookup"><span data-stu-id="6c099-139">You should see a bunch of dependencies getting installed.</span></span> <span data-ttu-id="6c099-140">Após a conclusão, é possível executar o aplicativo:</span><span class="sxs-lookup"><span data-stu-id="6c099-140">Once they are finished, you can run the app:</span></span>

```bash
npm start
```

<span data-ttu-id="6c099-141">Quando o aplicativo Hello-World é iniciado, ele é exibido `App started listening on port 3333` na janela do terminal.</span><span class="sxs-lookup"><span data-stu-id="6c099-141">When the hello-world app starts, it displays `App started listening on port 3333` in the terminal window.</span></span>

> [!NOTE]
> <span data-ttu-id="6c099-142">Se você vir um número de porta diferente exibido na mensagem acima, é porque você tem um conjunto de variáveis de ambiente de porta.</span><span class="sxs-lookup"><span data-stu-id="6c099-142">If you see a different port number displayed in the message above, it is because you have a PORT environment variable set.</span></span> <span data-ttu-id="6c099-143">Você pode continuar a usar essa porta ou alterar sua variável de ambiente para 3333.</span><span class="sxs-lookup"><span data-stu-id="6c099-143">You can continue to use that port or change your environment variable to 3333.</span></span>

<span data-ttu-id="6c099-144">Neste ponto, você pode abrir uma janela do navegador e navegar até as seguintes URLs para verificar se todas as URLs do aplicativo estão sendo carregadas:</span><span class="sxs-lookup"><span data-stu-id="6c099-144">At this point, you can open a browser window and navigate to the following URLs to verify that all the app URLs are loading:</span></span>

- [http://localhost:3333](http://localhost:3333)
- [http://localhost:3333/hello](http://localhost:3333/hello)
- [http://localhost:3333/first](http://localhost:3333/first)
- [http://localhost:3333/second](http://localhost:3333/second)

<a name="HostSample"></a>

### <a name="host-the-sample-app"></a><span data-ttu-id="6c099-145">Hospedar o aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="6c099-145">Host the sample app</span></span>

<span data-ttu-id="6c099-146">Lembre-se de que aplicativos no Microsoft Teams são aplicativos da Web que expõem um ou mais recursos.</span><span class="sxs-lookup"><span data-stu-id="6c099-146">Remember that apps in Microsoft Teams are web applications exposing one or more capabilities.</span></span> <span data-ttu-id="6c099-147">Para que a plataforma do teams carregue seu aplicativo, seu aplicativo deve estar acessível pela Internet.</span><span class="sxs-lookup"><span data-stu-id="6c099-147">For the Teams platform to load your app, your app must be reachable from the internet.</span></span> <span data-ttu-id="6c099-148">Para tornar seu aplicativo alcançável da Internet, você precisa *hospedar* seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6c099-148">To make your app reachable from the internet, you need to *host* your app.</span></span>

<span data-ttu-id="6c099-149">Para teste local, você pode executar o aplicativo na sua máquina local e criar um túnel para ele com um ponto de extremidade da Web.</span><span class="sxs-lookup"><span data-stu-id="6c099-149">For local testing you can run the app on your local machine and create a tunnel to it with a web endpoint.</span></span> <span data-ttu-id="6c099-150">o [ngrok](https://ngrok.com) é uma ferramenta gratuita que permite que você faça exatamente isso.</span><span class="sxs-lookup"><span data-stu-id="6c099-150">[ngrok](https://ngrok.com) is a free tool that lets you do just that.</span></span> <span data-ttu-id="6c099-151">Com o *ngrok* , você pode obter um endereço da Web como `https://d0ac14a5.ngrok.io` (esta URL é apenas um exemplo).</span><span class="sxs-lookup"><span data-stu-id="6c099-151">With *ngrok* you can get a web address such as `https://d0ac14a5.ngrok.io` (this URL is just an example).</span></span> <span data-ttu-id="6c099-152">Você pode [baixar e instalar](https://ngrok.com/download) o *ngrok* para o seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="6c099-152">You can [download and install](https://ngrok.com/download) *ngrok* for your environment.</span></span> <span data-ttu-id="6c099-153">Certifique-se de adicioná-lo a um local no seu `PATH` .</span><span class="sxs-lookup"><span data-stu-id="6c099-153">Make sure you add it to a location in your `PATH`.</span></span>

<span data-ttu-id="6c099-154">Depois de instalá-lo, você pode abrir uma nova janela de terminal e executar o seguinte comando para criar um túnel.</span><span class="sxs-lookup"><span data-stu-id="6c099-154">Once you install it, you can open a new terminal window and run the following command to create a tunnel.</span></span> <span data-ttu-id="6c099-155">O exemplo usa a porta 3333, portanto, certifique-se de especificá-la aqui.</span><span class="sxs-lookup"><span data-stu-id="6c099-155">The sample uses port 3333, so be sure to specify it here.</span></span>

```bash
ngrok http 3333 -host-header=localhost:3333
```

<span data-ttu-id="6c099-156">O *Ngrok* ouvirá as solicitações da Internet e irá encaminhá-las para seu aplicativo em execução na porta 3333.</span><span class="sxs-lookup"><span data-stu-id="6c099-156">*Ngrok* will listen to requests from the internet and will route them to your app running on port 3333.</span></span> <span data-ttu-id="6c099-157">Você pode verificar abrindo seu navegador e indo para `https://d0ac14a5.ngrok.io/hello` carregar a página de saudação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6c099-157">You can verify by opening your browser and going to `https://d0ac14a5.ngrok.io/hello` to load your app's hello page.</span></span> <span data-ttu-id="6c099-158">Certifique-se de usar o endereço de encaminhamento exibido pelo *ngrok* em sua sessão de console, em vez desta URL.</span><span class="sxs-lookup"><span data-stu-id="6c099-158">Please be sure to use the forwarding address displayed by *ngrok* in your console session instead of this URL.</span></span>

> [!NOTE]
> <span data-ttu-id="6c099-159">Se você tiver usado uma porta diferente na etapa [criar e executar](#build-and-run-the-sample) acima, certifique-se de usar o mesmo número de porta para instalar o túnel *ngrok* .</span><span class="sxs-lookup"><span data-stu-id="6c099-159">If you have used a different port in the [build and run](#build-and-run-the-sample) step above, make sure you use the same port number to setup the *ngrok* tunnel.</span></span>
> [!TIP]
> <span data-ttu-id="6c099-160">É uma boa ideia executar o *ngrok* em uma janela de terminal diferente para mantê-lo em execução sem interferir no aplicativo do nó, que pode ser mais tarde interrompido, recriar e executar novamente.</span><span class="sxs-lookup"><span data-stu-id="6c099-160">It is a good idea to run *ngrok* in a different terminal window to keep it running without interfering with the node app which you might later have to stop, rebuild and rerun.</span></span> <span data-ttu-id="6c099-161">A sessão do *ngrok* retornará informações úteis de depuração nesta janela.</span><span class="sxs-lookup"><span data-stu-id="6c099-161">The *ngrok* session will return useful debugging information in this window.</span></span>

<span data-ttu-id="6c099-162">Há uma versão paga do *ngrok* que permite nomes persistentes.</span><span class="sxs-lookup"><span data-stu-id="6c099-162">There is a paid version of *ngrok* that allows persistent names.</span></span> <span data-ttu-id="6c099-163">Se você usar a versão gratuita, seu aplicativo só estará disponível durante a sessão atual em sua máquina de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="6c099-163">If you use the free version your app will only be available during the current session on your development machine.</span></span> <span data-ttu-id="6c099-164">Se o computador estiver desligado ou chegar à suspensão, o serviço não estará mais disponível.</span><span class="sxs-lookup"><span data-stu-id="6c099-164">If the machine is shut down or goes to sleep the service will no longer be available.</span></span> <span data-ttu-id="6c099-165">Lembre-se disso ao compartilhar o aplicativo para teste por outros usuários.</span><span class="sxs-lookup"><span data-stu-id="6c099-165">Remember this when sharing the app for testing by other users.</span></span> <span data-ttu-id="6c099-166">Se for necessário reiniciar o serviço, ele retornará um novo endereço e você terá que atualizar cada lugar que usa esse endereço.</span><span class="sxs-lookup"><span data-stu-id="6c099-166">If you have to restart the service it will return a new address and you will have to update every place that uses that address.</span></span>

<span data-ttu-id="6c099-167">Lembre-se, anote a URL do aplicativo porque você precisará disso mais tarde, quando registrar o aplicativo com o Teams usando o app Studio.</span><span class="sxs-lookup"><span data-stu-id="6c099-167">Remember, make a note of the URL of your app because you will need this later when you register the app with Teams using App studio.</span></span> <span data-ttu-id="6c099-168">O bloco de notas funciona bem para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="6c099-168">Notepad works fine for this purpose.</span></span>

<a name="DeployToTeams"></a>

## <a name="deploy-your-app-to-microsoft-teams"></a><span data-ttu-id="6c099-169">Implantar seu aplicativo no Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="6c099-169">Deploy your app to Microsoft Teams</span></span>

<span data-ttu-id="6c099-170">Neste ponto, você tem um aplicativo hospedado na Internet, mas não tem nenhuma forma de informar às equipes onde procurá-lo, ou até mesmo o que seu aplicativo é chamado.</span><span class="sxs-lookup"><span data-stu-id="6c099-170">At this point you have an app hosted on the internet, but you have no way yet of telling Teams where to look for it, or even what your app is called.</span></span> <span data-ttu-id="6c099-171">Para fazer isso, agora você precisa criar um pacote de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="6c099-171">To do this you now have to create an app package.</span></span> <span data-ttu-id="6c099-172">Isso é pouco mais que um arquivo de texto que contém o manifesto do aplicativo e alguns ícones que o cliente Teams usará para exibir e marcar corretamente o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6c099-172">This is little more than a text file that contains the app manifest and some icons that the Teams client will use to properly display and brand your app.</span></span> <span data-ttu-id="6c099-173">Você pode criar manualmente esse pacote de aplicativos ou pode usar o app Studio, uma ferramenta executada no Teams que simplificará o processo de registro do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6c099-173">You can manually create this app package, or you can use App Studio, a tool that runs in Teams that will simplify the process of registering the app.</span></span> <span data-ttu-id="6c099-174">O app Studio é a maneira recomendada de criar e atualizar o pacote de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="6c099-174">App Studio is the recommended way of creating and updating the app package.</span></span>

<span data-ttu-id="6c099-175">Para ambos os métodos, você precisará do seguinte:</span><span class="sxs-lookup"><span data-stu-id="6c099-175">For either method you will need the following:</span></span>

- <span data-ttu-id="6c099-176">A URL onde seu aplicativo pode ser encontrado na Internet.</span><span class="sxs-lookup"><span data-stu-id="6c099-176">The URL where your app can be found on the internet.</span></span>
- <span data-ttu-id="6c099-177">Ícones que as equipes usarão para marcar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6c099-177">Icons that Teams will use to brand your app.</span></span> <span data-ttu-id="6c099-178">O exemplo vem com ícones de espaço reservado localizados em "src\static\images.</span><span class="sxs-lookup"><span data-stu-id="6c099-178">The sample comes with placeholder icons located in "src\static\images.</span></span> <span data-ttu-id="6c099-179">O app Studio também fornecerá ícones padrão, se necessário.</span><span class="sxs-lookup"><span data-stu-id="6c099-179">App Studio also will provide default icons if needed.</span></span>

[!include[Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-your-hosted-app"></a><span data-ttu-id="6c099-180">Atualizar seu aplicativo hospedado</span><span class="sxs-lookup"><span data-stu-id="6c099-180">Update your hosted app</span></span>

<span data-ttu-id="6c099-181">O aplicativo de exemplo requer que as seguintes variáveis de ambiente sejam definidas para os valores que você fez antes.</span><span class="sxs-lookup"><span data-stu-id="6c099-181">The sample app requires the following environment variables to be set to the values you made a note of earlier.</span></span>

```
MICROSOFT_APP_ID=<YOUR BOT'S APP ID>
MICROSOFT_APP_PASSWORD=<YOUR BOT'S PASSWORD>
WEBSITE_NODE_DEFAULT_VERSION=8.9.4
```

<span data-ttu-id="6c099-182">O modo como você faz isso difere dependendo de como você hospedáou seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6c099-182">How you do that differs depending on how you hosted your app.</span></span> <span data-ttu-id="6c099-183">O importante sobre o uso de variáveis de ambiente é que esses valores fazem parte de seu ambiente-eles podem ser acessados pelo código para seu aplicativo, mas não estão expostos a terceiros que podem examinar os arquivos que fazem parte de seu site.</span><span class="sxs-lookup"><span data-stu-id="6c099-183">The important thing about using environment variables is that these values are part of your environment - they can be accessed by the code for your app, but they are not exposed to third parties who might examine the files that make up your site.</span></span>

<span data-ttu-id="6c099-184">Se você estiver executando o aplicativo usando o ngrok, precisará configurar algumas variáveis de ambiente locais.</span><span class="sxs-lookup"><span data-stu-id="6c099-184">If you are running the app using ngrok you'll need to set up some local environment variables.</span></span> <span data-ttu-id="6c099-185">Há várias maneiras de fazer isso, mas a mais fácil, se você estiver usando o Visual Studio Code, é adicionar uma [configuração de lançamento](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations):</span><span class="sxs-lookup"><span data-stu-id="6c099-185">There are many ways to do this, but the easiest, if you are using Visual Studio Code, is to add a [launch configuration](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations):</span></span>

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

<span data-ttu-id="6c099-186">Onde:</span><span class="sxs-lookup"><span data-stu-id="6c099-186">Where:</span></span>

<span data-ttu-id="6c099-187">MICROSOFT_APP_ID e MICROSOFT_APP_PASSWORD é a ID e a senha, respectivamente, para o bot.</span><span class="sxs-lookup"><span data-stu-id="6c099-187">MICROSOFT_APP_ID and MICROSOFT_APP_PASSWORD is the ID and password, respectively, for your bot.</span></span>
<span data-ttu-id="6c099-188">NODE_DEBUG mostrará o que está acontecendo no bot no console de depuração de código do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6c099-188">NODE_DEBUG will show you what's happening in your bot in the Visual Studio Code debug console.</span></span>
<span data-ttu-id="6c099-189">NODE_CONFIG_DIR aponta para o diretório na raiz do repositório (por padrão, quando o aplicativo é executado localmente, ele o procura na pasta src).</span><span class="sxs-lookup"><span data-stu-id="6c099-189">NODE_CONFIG_DIR points to the directory at the root of the repository (by default, when the app is run locally, it looks for it in the src folder).</span></span>

> [!Note]
> <span data-ttu-id="6c099-190">Se você não tiver parado o NPM de versões anteriores no tutorial, você precisará executar `npm stop` para que o Visual Studio Code retorne suas variáveis de configuração de inicialização corretamente.</span><span class="sxs-lookup"><span data-stu-id="6c099-190">If you have not stopped npm from earlier in the tutorial, you'll need to run `npm stop` in order for Visual Studio Code to pickup your launch configuration variables correctly.</span></span>

<a name="ConfigureTheAppTab"></a>

## <a name="configure-the-app-tab"></a><span data-ttu-id="6c099-191">Configurar a guia aplicativo</span><span class="sxs-lookup"><span data-stu-id="6c099-191">Configure the app tab</span></span>

<span data-ttu-id="6c099-192">Após instalar o aplicativo em uma equipe, você precisará configurá-lo para exibir o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="6c099-192">Once you install the app into a team, you will need to configure it to show content.</span></span> <span data-ttu-id="6c099-193">Vá para um canal na equipe e clique no botão **"+"** para adicionar uma nova guia. Em seguida, você pode escolher `Hello World` na lista **Adicionar uma guia** .</span><span class="sxs-lookup"><span data-stu-id="6c099-193">Go to a channel in the team and click on the **'+'** button to add a new tab. You can then choose `Hello World` from the **Add a tab** list.</span></span> <span data-ttu-id="6c099-194">Em seguida, será exibida uma caixa de diálogo de configuração.</span><span class="sxs-lookup"><span data-stu-id="6c099-194">You will then be presented with a configuration dialog.</span></span> <span data-ttu-id="6c099-195">Esta caixa de diálogo permitirá que você escolha qual guia será exibida neste canal.</span><span class="sxs-lookup"><span data-stu-id="6c099-195">This dialog will let you choose which tab to display in this channel.</span></span> <span data-ttu-id="6c099-196">Depois de selecionar a guia e clicar em `Save` , você poderá ver a `Hello World` guia carregada com a guia escolhida.</span><span class="sxs-lookup"><span data-stu-id="6c099-196">Once you select the tab and click on `Save` you can see the `Hello World` tab loaded with the tab you chose.</span></span>

<img width="430px" src="~/assets/images/samples-hello-world-tab-configure.png" alt-text="Screenshot of configure" />

### <a name="test-your-bot-in-teams"></a><span data-ttu-id="6c099-197">Testar seu bot no Teams</span><span class="sxs-lookup"><span data-stu-id="6c099-197">Test your bot in Teams</span></span>

<span data-ttu-id="6c099-198">Agora você pode interagir com o bot no Teams.</span><span class="sxs-lookup"><span data-stu-id="6c099-198">You can now interact with the bot in Teams.</span></span> <span data-ttu-id="6c099-199">Escolha um canal na equipe em que você registrou seu aplicativo e digite `@your-bot-name` , seguido de sua mensagem.</span><span class="sxs-lookup"><span data-stu-id="6c099-199">Choose a channel in the team where you registered your app, and type `@your-bot-name`, followed by your message.</span></span> <span data-ttu-id="6c099-200">Isso é chamado de **\@ menção**.</span><span class="sxs-lookup"><span data-stu-id="6c099-200">This is called an **\@mention**.</span></span> <span data-ttu-id="6c099-201">Qualquer mensagem enviada ao bot será enviada de volta para você como resposta.</span><span class="sxs-lookup"><span data-stu-id="6c099-201">Whatever message you send to the bot will be sent back to you as a reply.</span></span>

<img width="450px" alt-text="Bot responses" src="~/assets/images/samples-hello-world-bot.png" />

<a name="ComposeRichMessages"></a>

### <a name="test-your-messaging-extension"></a><span data-ttu-id="6c099-202">Testar sua extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="6c099-202">Test your messaging extension</span></span>

<span data-ttu-id="6c099-203">Para testar sua extensão de mensagens, você pode clicar nos três pontos abaixo da caixa de entrada no modo de exibição de conversa.</span><span class="sxs-lookup"><span data-stu-id="6c099-203">To test your messaging extension, you can click on the three dots below the input box in your conversation view.</span></span> <span data-ttu-id="6c099-204">Um menu será exibido com o aplicativo **"Olá mundo"** .</span><span class="sxs-lookup"><span data-stu-id="6c099-204">A menu will pop up with the **'Hello World'** app in it.</span></span> <span data-ttu-id="6c099-205">Quando você clicar nele, verá um número de textos aleatórios.</span><span class="sxs-lookup"><span data-stu-id="6c099-205">When you click it, you will see a number of random texts.</span></span> <span data-ttu-id="6c099-206">Você pode escolher qualquer uma delas e ela será inserida na conversa.</span><span class="sxs-lookup"><span data-stu-id="6c099-206">You can choose any one of them and it will be inserted it into your conversation.</span></span>

<img width="430px" alt-text="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="430px" alt-text="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

<span data-ttu-id="6c099-207">Escolha um dos textos aleatórios, e você verá um cartão formatado e pronto para enviar com sua própria mensagem na parte inferior.</span><span class="sxs-lookup"><span data-stu-id="6c099-207">Choose one of the random texts, and you will see a card formatted and ready to send with your own message at the bottom.</span></span>

<img width="430px" alt-text="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
