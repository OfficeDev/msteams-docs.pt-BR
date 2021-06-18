---
title: Criar aplicativos com o Microsoft Teams Toolkit e Visual Studio Código
description: Começar a criar grandes aplicativos personalizados diretamente Visual Studio Código com o microsoft Teams Toolkit
keywords: kit de ferramentas de código do visual studio do teams
localization_priority: Normal
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: b2cfab5cb2ea2d727608b6ea3bbfec3271b2b039
ms.sourcegitcommit: 14409950307b135265c8582408be5277b35131dd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2021
ms.locfileid: "52994137"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio-code"></a><span data-ttu-id="1e73b-104">Criar aplicativos com o Teams Toolkit e Visual Studio Código</span><span class="sxs-lookup"><span data-stu-id="1e73b-104">Build apps with the Teams Toolkit and Visual Studio Code</span></span>

<span data-ttu-id="1e73b-105">O Teams Toolkit for Visual Studio Code ajuda os desenvolvedores a criar e implantar aplicativos do Teams com identidade integrada, acesso ao armazenamento em nuvem, dados do Microsoft Graph e outros serviços no Azure e no M365 com uma abordagem de "configuração zero" para a experiência do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="1e73b-105">The Teams Toolkit for Visual Studio Code helps developers create and deploy Teams apps with integrated identity, access to cloud storage, data from Microsoft Graph, and other services in Azure and M365 with a “zero-configuration” approach to the developer experience.</span></span>  

<span data-ttu-id="1e73b-106">Você também pode usar o kit de ferramentas com Visual Studio ou como uma CLI (chamada `teamsfx` ).</span><span class="sxs-lookup"><span data-stu-id="1e73b-106">You also can use the toolkit with Visual Studio or as a CLI (called `teamsfx`).</span></span>

## <a name="install-the-teams-toolkit-for-visual-studio-code"></a><span data-ttu-id="1e73b-107">Instalar o teams Toolkit para Visual Studio Código</span><span class="sxs-lookup"><span data-stu-id="1e73b-107">Install the Teams Toolkit for Visual Studio Code</span></span>

1. <span data-ttu-id="1e73b-108">Abra o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="1e73b-108">Open Visual Studio Code.</span></span>
1. <span data-ttu-id="1e73b-109">Selecione o exibição Extensões (**Ctrl+Shift+X**  /  **⌘⇧-X** ou **Exibir > Extensões).**</span><span class="sxs-lookup"><span data-stu-id="1e73b-109">Select the Extensions view (**Ctrl+Shift+X** / **⌘⇧-X** or **View > Extensions**).</span></span>
1. <span data-ttu-id="1e73b-110">Na caixa de pesquisa, digite _Teams Toolkit_.</span><span class="sxs-lookup"><span data-stu-id="1e73b-110">In the search box, enter _Teams Toolkit_.</span></span>
1. <span data-ttu-id="1e73b-111">Selecione no botão de instalação verde ao lado do teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="1e73b-111">Select on the green install button next to the Teams Toolkit.</span></span>

<span data-ttu-id="1e73b-112">Você também pode encontrar o teams Toolkit no [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).</span><span class="sxs-lookup"><span data-stu-id="1e73b-112">You also can find the Teams Toolkit on the [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).</span></span>

<span data-ttu-id="1e73b-113">As ferramentas a seguir são instaladas pela extensão Visual Studio Código quando elas são necessárias.</span><span class="sxs-lookup"><span data-stu-id="1e73b-113">The following tools are installed by the Visual Studio Code extension when they are needed.</span></span> <span data-ttu-id="1e73b-114">Se já estiver instalada, a versão instalada será usada em vez disso.</span><span class="sxs-lookup"><span data-stu-id="1e73b-114">If already installed, the installed version is used instead.</span></span> <span data-ttu-id="1e73b-115">Se estiver usando o Linux (incluindo o WSL), você deve instalar essas ferramentas antes de usar:</span><span class="sxs-lookup"><span data-stu-id="1e73b-115">If using Linux (including WSL), you must install these tools before use:</span></span>

- [<span data-ttu-id="1e73b-116">Ferramentas principais das funções do Azure</span><span class="sxs-lookup"><span data-stu-id="1e73b-116">Azure Functions Core Tools</span></span>](/azure/azure-functions/functions-run-local)

    <span data-ttu-id="1e73b-117">As Ferramentas Principais de Funções do Azure são usadas para executar qualquer componente back-end localmente durante uma execução de depuração local, incluindo os auxiliares de autenticação necessários ao executar seus serviços no Azure.</span><span class="sxs-lookup"><span data-stu-id="1e73b-117">Azure Functions Core Tools is used to run any backend components locally during a local debug run, including the authentication helpers required when running your services in Azure.</span></span> <span data-ttu-id="1e73b-118">Ele é instalado no diretório do projeto usando o npm `devDependencies` .</span><span class="sxs-lookup"><span data-stu-id="1e73b-118">It is installed within the project directory using the npm `devDependencies`.</span></span>

- [<span data-ttu-id="1e73b-119">.NET SDK</span><span class="sxs-lookup"><span data-stu-id="1e73b-119">.NET SDK</span></span>](/dotnet/core/install/)

    <span data-ttu-id="1e73b-120">O .NET SDK é usado para instalar vinculações personalizadas para implantações de aplicativos de depuração local e funções do Azure.</span><span class="sxs-lookup"><span data-stu-id="1e73b-120">The .NET SDK is used to install customized bindings for local debugging and Azure Functions app deployments.</span></span> <span data-ttu-id="1e73b-121">Se você não tiver instalado o SDK .NET 3.1 ou posterior globalmente, a versão portátil será instalada.</span><span class="sxs-lookup"><span data-stu-id="1e73b-121">If you have not installed the .NET 3.1 or later SDK globally, the portable version is installed.</span></span>

- [<span data-ttu-id="1e73b-122">ngrok</span><span class="sxs-lookup"><span data-stu-id="1e73b-122">ngrok</span></span>](https://ngrok.com/download)

    <span data-ttu-id="1e73b-123">Alguns recursos de aplicativo do Teams (bots de conversa, extensões de mensagens e webhooks de entrada) exigem conexões de entrada.</span><span class="sxs-lookup"><span data-stu-id="1e73b-123">Some Teams app features (conversational bots, messaging extensions, and incoming webhooks) require inbound connections.</span></span>  <span data-ttu-id="1e73b-124">Você precisa expor seu sistema de desenvolvimento ao Teams por meio de um túnel.</span><span class="sxs-lookup"><span data-stu-id="1e73b-124">You need to expose your development system to Teams through a tunnel.</span></span> <span data-ttu-id="1e73b-125">Um túnel não é necessário para aplicativos que incluem apenas guias.</span><span class="sxs-lookup"><span data-stu-id="1e73b-125">A tunnel is not required for apps that only include tabs.</span></span>  <span data-ttu-id="1e73b-126">Este pacote é instalado no diretório do projeto (usando npm `devDependencies` ).</span><span class="sxs-lookup"><span data-stu-id="1e73b-126">This package is installed within the project directory (using npm `devDependencies`).</span></span>

## <a name="use-the-teams-toolkit-for-visual-studio-code"></a><span data-ttu-id="1e73b-127">Usar o Toolkit teams para Visual Studio Código</span><span class="sxs-lookup"><span data-stu-id="1e73b-127">Use the Teams Toolkit for Visual Studio Code</span></span>

- [<span data-ttu-id="1e73b-128">Configurar um novo projeto</span><span class="sxs-lookup"><span data-stu-id="1e73b-128">Set up a new project</span></span>](#set-up-a-new-teams-project)
- [<span data-ttu-id="1e73b-129">Configurar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="1e73b-129">Configure your app</span></span>](#configure-your-app)
- [<span data-ttu-id="1e73b-130">Executar seu aplicativo localmente</span><span class="sxs-lookup"><span data-stu-id="1e73b-130">Run your app locally</span></span>](#install-and-run-your-app-locally)
- [<span data-ttu-id="1e73b-131">Publicar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="1e73b-131">Publish your app</span></span>](#publish-your-app-to-teams)

## <a name="set-up-a-new-teams-project"></a><span data-ttu-id="1e73b-132">Configurar um novo projeto do Teams</span><span class="sxs-lookup"><span data-stu-id="1e73b-132">Set up a new Teams project</span></span>

<span data-ttu-id="1e73b-133">O Teams Toolkit pode criar aplicativos react hospedados em web parts do Azure ou SPFx hospedadas em seu ambiente do SharePoint M365.</span><span class="sxs-lookup"><span data-stu-id="1e73b-133">The Teams Toolkit can create React apps that are hosted in Azure or SPFx web parts that are hosted on your M365 SharePoint environment.</span></span> <span data-ttu-id="1e73b-134">Para criar um novo aplicativo React a ser hospedado no Azure:</span><span class="sxs-lookup"><span data-stu-id="1e73b-134">To create a new React app to be hosted on Azure:</span></span>

1. <span data-ttu-id="1e73b-135">Abra o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="1e73b-135">Open Visual Studio code.</span></span>
1. <span data-ttu-id="1e73b-136">Abra o Kit de ferramentas do Teams selecionando o ícone do Teams na barra lateral:</span><span class="sxs-lookup"><span data-stu-id="1e73b-136">Open the Teams Toolkit by selecting the Teams icon in the sidebar:</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="O ícone do Teams na barra lateral do Visual Studio Code":::

1. <span data-ttu-id="1e73b-138">Selecione **Criar Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="1e73b-138">Select **Create New Project**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Localização do link de Criação de Novo Projeto na barra lateral do Kit de ferramentas do Teams.":::

1. <span data-ttu-id="1e73b-140">Selecione **Criar um novo aplicativo do Teams**.</span><span class="sxs-lookup"><span data-stu-id="1e73b-140">Select **Create a new Teams app**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Início do assistente para Criar Novo Projeto":::

1. <span data-ttu-id="1e73b-142">Na etapa **Selecionar recursos,** o recurso **Tab** já está selecionado.</span><span class="sxs-lookup"><span data-stu-id="1e73b-142">On the **Select capabilities** step, the **Tab** capability is already selected.</span></span> <span data-ttu-id="1e73b-143">Você também pode, opcionalmente, selecionar **Bot** e **Extensão de Mensagens.**</span><span class="sxs-lookup"><span data-stu-id="1e73b-143">You can also optionally select **Bot** and **Messaging Extension**.</span></span>  <span data-ttu-id="1e73b-144">Pressione **OK**.</span><span class="sxs-lookup"><span data-stu-id="1e73b-144">Press **OK**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-capabilities.png" alt-text="Captura de tela mostrando como adicionar capacidades ao seu novo aplicativo.":::

1. <span data-ttu-id="1e73b-146">Na etapa **Tipo de hospedagem front-end**, selecione **Azure**.</span><span class="sxs-lookup"><span data-stu-id="1e73b-146">On the **Frontend hosting type** step, select **Azure**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-hosting.png" alt-text="Captura de tela mostrando como selecionar a hospedagem para seu novo aplicativo.":::

1. <span data-ttu-id="1e73b-148">Opcionalmente, na etapa **Recursos de nuvem,** selecione recursos de nuvem que seu aplicativo usa.</span><span class="sxs-lookup"><span data-stu-id="1e73b-148">Optionally, on the **Cloud resources** step, select cloud resources that your application uses.</span></span> <span data-ttu-id="1e73b-149">Você pode selecionar CRUD (criar, ler, atualizar e excluir) acesso a uma tabela SQL ou uma API:</span><span class="sxs-lookup"><span data-stu-id="1e73b-149">You can select CRUD (create, read, update, and delete) access to a SQL table or an API:</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-cloud-resources.png" alt-text="Captura de tela mostrando como adicionar recursos em nuvem ao seu novo aplicativo.":::

1. <span data-ttu-id="1e73b-151">Na etapa **Linguagem de Programação,** você pode escolher **JavaScript** ou **TypeScript**:</span><span class="sxs-lookup"><span data-stu-id="1e73b-151">On the **Programming Language** step, you can choose **JavaScript** or **TypeScript**:</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-programming-languages.png" alt-text="Captura de tela mostrando como selecionar a linguagem de programação.":::

1. <span data-ttu-id="1e73b-153">Selecione uma pasta do espaço de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1e73b-153">Select a workspace folder.</span></span> <span data-ttu-id="1e73b-154">Uma pasta é criada em sua pasta de espaço de trabalho para o projeto que você está criando.</span><span class="sxs-lookup"><span data-stu-id="1e73b-154">A folder is created within your workspace folder for the project you are creating.</span></span>

1. <span data-ttu-id="1e73b-155">Insira um nome adequado para seu aplicativo, como `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="1e73b-155">Enter a suitable name for your app, like `helloworld`.</span></span> <span data-ttu-id="1e73b-156">O nome do aplicativo deve consistir apenas de caracteres alfanuméricos.</span><span class="sxs-lookup"><span data-stu-id="1e73b-156">The name of the app must consist only of alphanumeric characters.</span></span>  <span data-ttu-id="1e73b-157">Pressione **Inserir** para continuar.</span><span class="sxs-lookup"><span data-stu-id="1e73b-157">Press **Enter** to continue.</span></span>

<span data-ttu-id="1e73b-158">Seu aplicativo do Teams é criado em alguns segundos.</span><span class="sxs-lookup"><span data-stu-id="1e73b-158">Your Teams app is created within a few seconds.</span></span> <span data-ttu-id="1e73b-159">O aplicativo scaffolded contém código para manipular o login único com o Azure Active Directory e o acesso ao Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="1e73b-159">The scaffolded app contains code to handle single sign-on with Azure Active Directory and access to the Microsoft Graph.</span></span>  <span data-ttu-id="1e73b-160">Se você selecionou recursos do Azure, o código para esses recursos também estará disponível.</span><span class="sxs-lookup"><span data-stu-id="1e73b-160">If you selected Azure resources, then the code for those resources is also available.</span></span>

<span data-ttu-id="1e73b-161">Para ver um passo a passo do processo de criação e publicação do SPFx, consulte o [tutorial SPFx](../get-started/first-app-spfx.md).</span><span class="sxs-lookup"><span data-stu-id="1e73b-161">For a walk-through of the SPFx creation and publication process, see the [SPFx tutorial](../get-started/first-app-spfx.md).</span></span>

## <a name="configure-your-app"></a><span data-ttu-id="1e73b-162">Configurar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="1e73b-162">Configure your app</span></span>

<span data-ttu-id="1e73b-163">Em sua essência, o aplicativo do Teams abrange três componentes:</span><span class="sxs-lookup"><span data-stu-id="1e73b-163">At its core, the Teams app embraces three components:</span></span>

  1. <span data-ttu-id="1e73b-164">O cliente do Microsoft Teams (Web, desktop ou móvel) onde os usuários interagem com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1e73b-164">The Microsoft Teams client (web, desktop or mobile) where users interact with your app.</span></span>
  1. <span data-ttu-id="1e73b-165">Um servidor que responde a solicitações de conteúdo que é exibido no Teams.</span><span class="sxs-lookup"><span data-stu-id="1e73b-165">A server that responds to requests for content that is displayed in Teams.</span></span> <span data-ttu-id="1e73b-166">Por exemplo, conteúdo da guia HTML ou um cartão adaptável do bot.</span><span class="sxs-lookup"><span data-stu-id="1e73b-166">For example, HTML tab content or a bot Adaptive Card.</span></span>
  1. <span data-ttu-id="1e73b-167">Um pacote de aplicativos do Teams consiste em três arquivos:</span><span class="sxs-lookup"><span data-stu-id="1e73b-167">A Teams app package consists of three files:</span></span>

      > [!div class="checklist"]
      >
      > - <span data-ttu-id="1e73b-168">A manifest.jsestá.</span><span class="sxs-lookup"><span data-stu-id="1e73b-168">The manifest.json.</span></span>
      > - <span data-ttu-id="1e73b-169">Um [ícone de cor](../resources/schema/manifest-schema.md#icons) para seu aplicativo ser exibido no catálogo de aplicativos público ou da organização.</span><span class="sxs-lookup"><span data-stu-id="1e73b-169">A [color icon](../resources/schema/manifest-schema.md#icons) for your app to display in the public or organization app catalog.</span></span>
      > - <span data-ttu-id="1e73b-170">Um [ícone de contorno](../resources/schema/manifest-schema.md#icons) para exibição na barra de atividades do Teams.</span><span class="sxs-lookup"><span data-stu-id="1e73b-170">An [outline icon](../resources/schema/manifest-schema.md#icons) for display on the Teams activity bar.</span></span>

<span data-ttu-id="1e73b-171">O manifesto e os ícones são armazenados na `.fx` pasta do seu projeto antes de serem carregados para o Teams.</span><span class="sxs-lookup"><span data-stu-id="1e73b-171">The manifest and icons are stored in the `.fx` folder of your project prior to being uploaded to Teams.</span></span> <span data-ttu-id="1e73b-172">Quando um aplicativo é instalado, o cliente do Teams analisará o arquivo de manifesto para determinar as informações necessárias, como o nome do seu aplicativo e a URL onde os serviços estão localizados.</span><span class="sxs-lookup"><span data-stu-id="1e73b-172">When an app is installed, the Teams client parses the manifest file to determine needed information like the name of your app and the URL where the services are located.</span></span>

1. <span data-ttu-id="1e73b-173">Para configurar seu aplicativo, navegue até a guia **Teams Toolkit** no Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="1e73b-173">To configure your app, navigate to the **Teams Toolkit** tab in Visual Studio Code.</span></span>
1. <span data-ttu-id="1e73b-174">Selecione **Editor de Manifesto** na **seção** Projeto.</span><span class="sxs-lookup"><span data-stu-id="1e73b-174">Select **Manifest Editor** in the **Project** section.</span></span>

<span data-ttu-id="1e73b-175">A edição dos campos na página detalhes do aplicativo atualiza o conteúdo do manifest.jsno arquivo que é finalmente enviado como parte do pacote do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1e73b-175">Editing the fields in the App details page updates the contents of the manifest.json file that is ultimately shipped as part of the app package.</span></span>

## <a name="install-and-run-your-app-locally"></a><span data-ttu-id="1e73b-176">Instalar e executar seu aplicativo localmente</span><span class="sxs-lookup"><span data-stu-id="1e73b-176">Install and run your app locally</span></span>

<span data-ttu-id="1e73b-177">Para compilar e executar seu aplicativo localmente:</span><span class="sxs-lookup"><span data-stu-id="1e73b-177">To build and run your app locally:</span></span>

1. <span data-ttu-id="1e73b-178">No Visual Studio Code, pressione **F5** para executar seu aplicativo no modo de depuração.</span><span class="sxs-lookup"><span data-stu-id="1e73b-178">From Visual Studio Code, press **F5** to run your application in debug mode.</span></span>

   > <span data-ttu-id="1e73b-179">Quando você executa o aplicativo pela primeira vez, todas as dependências são baixadas e o aplicativo é compilado.</span><span class="sxs-lookup"><span data-stu-id="1e73b-179">When you run the app for the first time, all dependencies are downloaded and the app is built.</span></span>  <span data-ttu-id="1e73b-180">Uma janela do navegador é aberta automaticamente quando a compilação é concluída.</span><span class="sxs-lookup"><span data-stu-id="1e73b-180">A browser window automatically opens when the build is complete.</span></span>  <span data-ttu-id="1e73b-181">Isto pode levar de 3 a 5 minutos para ser concluído.</span><span class="sxs-lookup"><span data-stu-id="1e73b-181">This can take 3-5 minutes to complete.</span></span>

   <span data-ttu-id="1e73b-182">O kit de ferramentas solicita que você instale um certificado local, se necessário.</span><span class="sxs-lookup"><span data-stu-id="1e73b-182">The toolkit prompts you to install a local certificate if required.</span></span> <span data-ttu-id="1e73b-183">Esse certificado permite que o Teams carregue seu aplicativo a partir de `https://localhost`.</span><span class="sxs-lookup"><span data-stu-id="1e73b-183">This certificate allows Teams to load your application from `https://localhost`.</span></span> <span data-ttu-id="1e73b-184">Selecione Sim quando aparecer a seguinte caixa de diálogo:</span><span class="sxs-lookup"><span data-stu-id="1e73b-184">Select yes when the following dialog appears:</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/ssl-prompt.png" alt-text="Captura de tela mostrando como a solicitação de instalação de um certificado SSL para permitir que o Teams carregue seu aplicativo a partir do localhost.":::

1. <span data-ttu-id="1e73b-186">O seu navegador da web é iniciado para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1e73b-186">Your web browser is started to run the application.</span></span> <span data-ttu-id="1e73b-187">Se for solicitado a abrir o Microsoft Teams, selecione Cancelar para permanecer no navegador.</span><span class="sxs-lookup"><span data-stu-id="1e73b-187">If prompted to open Microsoft Teams, select Cancel to remain within the browser.</span></span> <span data-ttu-id="1e73b-188">Você também pode ser solicitado a alternar para o aplicativo teams em outras ocasiões.</span><span class="sxs-lookup"><span data-stu-id="1e73b-188">You may also be prompted to switch to the Teams application at other times.</span></span> <span data-ttu-id="1e73b-189">Selecione o aplicativo Web quando isso acontecer.</span><span class="sxs-lookup"><span data-stu-id="1e73b-189">Select the web app when this happens.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/launch-web-browser-and-pick-webapp.png" alt-text="Captura de tela mostrando como escolher a versão da web das equipes quando lançadas":::

1. <span data-ttu-id="1e73b-191">Você pode ser solicitado a entrar.</span><span class="sxs-lookup"><span data-stu-id="1e73b-191">You may be prompted to sign in.</span></span> <span data-ttu-id="1e73b-192">Em caso afirmativo, entre com sua conta M365.</span><span class="sxs-lookup"><span data-stu-id="1e73b-192">If so, sign in with your M365 account.</span></span>
1. <span data-ttu-id="1e73b-193">Quando solicitado a instalar o aplicativo no Teams, pressione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="1e73b-193">When prompted to install the app onto Teams, press **Add**.</span></span>

<span data-ttu-id="1e73b-194">Tanto o back-end quanto o front-end são conectados ao depurador Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="1e73b-194">Both the backend and frontend are hooked into the Visual Studio Code debugger.</span></span>  <span data-ttu-id="1e73b-195">Isso permite definir pontos de interrupção em qualquer lugar em seu código e inspecionar o estado.</span><span class="sxs-lookup"><span data-stu-id="1e73b-195">This allows you to set breakpoints anywhere in your code and inspect state.</span></span>  <span data-ttu-id="1e73b-196">Você também pode usar qualquer ferramenta de depuração de front-end (como as Ferramentas de Desenvolvedor do React) no navegador.</span><span class="sxs-lookup"><span data-stu-id="1e73b-196">You can also use any frontend debugging tools (such as the React Developer Tools) within the browser.</span></span>  <span data-ttu-id="1e73b-197">Para obter mais informações sobre a depuração no Visual Studio Code, revise [a documentação](https://code.visualstudio.com/Docs/editor/debugging).</span><span class="sxs-lookup"><span data-stu-id="1e73b-197">For more information about debugging in Visual Studio Code, review [the documentation](https://code.visualstudio.com/Docs/editor/debugging).</span></span>

## <a name="publish-your-app-to-teams"></a><span data-ttu-id="1e73b-198">Publicar seu aplicativo no Teams</span><span class="sxs-lookup"><span data-stu-id="1e73b-198">Publish your app to Teams</span></span>

<span data-ttu-id="1e73b-199">Antes que ele possa ser usado por outras pessoas, você deve publicar seu aplicativo no Portal do Desenvolvedor para o Teams.</span><span class="sxs-lookup"><span data-stu-id="1e73b-199">Before it can be used by other people, you must publish your app to the Developer Portal for Teams.</span></span>

1. <span data-ttu-id="1e73b-200">Para publicar seu aplicativo, navegue até a guia **Teams Toolkit** no Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="1e73b-200">To publish your app, navigate to the **Teams Toolkit** tab in Visual Studio Code.</span></span>
1. <span data-ttu-id="1e73b-201">Selecione **Publicar no Teams** na seção **Project.**</span><span class="sxs-lookup"><span data-stu-id="1e73b-201">Select **Publish to Teams** in the **Project** section.</span></span>

<span data-ttu-id="1e73b-202">Se estiver usando a hospedagem do Azure, você deverá ter provisionado e implantado na nuvem.</span><span class="sxs-lookup"><span data-stu-id="1e73b-202">If using Azure hosting, you must have provisioned and deployed to the cloud.</span></span> <span data-ttu-id="1e73b-203">Para ver um passo a passo do processo SPFx publicação, consulte o [tutorial SPFx .](../get-started/first-app-spfx.md)</span><span class="sxs-lookup"><span data-stu-id="1e73b-203">For a walk-through of the SPFx publication process, see the [SPFx tutorial](../get-started/first-app-spfx.md).</span></span>

## <a name="next-step"></a><span data-ttu-id="1e73b-204">Próxima etapa</span><span class="sxs-lookup"><span data-stu-id="1e73b-204">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1e73b-205">Mantendo e dando suporte ao aplicativo publicado</span><span class="sxs-lookup"><span data-stu-id="1e73b-205">Maintaining and supporting your published app</span></span>](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
