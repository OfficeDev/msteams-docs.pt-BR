---
title: Começar - Criar seu primeiro aplicativo Teams com o Blazor
author: adrianhall
description: Crie rapidamente um Microsoft Teams que exibe um "Hello, World!" usando o Microsoft Teams Toolkit e o .NET Blazor.
ms.author: adhal
ms.date: 04/27/2021
ms.topic: quickstart
ms.openlocfilehash: 861b6921d7a2092a746ea7dc1399f8aaa523e207
ms.sourcegitcommit: 9cabeaed9baf96c8caeb1497f0bc37abdb787d22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2021
ms.locfileid: "52646612"
---
# <a name="build-and-run-your-first-microsoft-teams-app-with-blazor"></a><span data-ttu-id="2ccbc-104">Criar e executar seu primeiro aplicativo Microsoft Teams com o Blazor</span><span class="sxs-lookup"><span data-stu-id="2ccbc-104">Build and run your first Microsoft Teams app with Blazor</span></span>

<span data-ttu-id="2ccbc-105">Neste tutorial, você criará um novo aplicativo Microsoft Teams no .NET/Blazor que implementa um aplicativo pessoal simples para obter informações do microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-105">In this tutorial, you will create a new Microsoft Teams app in .NET/Blazor that implements a simple personal app to pull information from the Microsoft Graph.</span></span> <span data-ttu-id="2ccbc-106">(Um *aplicativo pessoal* inclui um conjunto de guias com escopo para uso individual.)  Durante o tutorial, você aprenderá sobre a estrutura de um aplicativo Teams, como executar um aplicativo localmente e como implantar o aplicativo no Azure.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-106">(A *personal app* includes a set of tabs scoped for individual use.)  During the tutorial, you will learn about the structure of a Teams app, how to run an app locally, and how to deploy the app to Azure.</span></span>

<span data-ttu-id="2ccbc-107">O aplicativo criado exibe informações básicas do usuário para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-107">The app that is built displays basic user information for the current user.</span></span>  <span data-ttu-id="2ccbc-108">Quando a permissão for concedida, o aplicativo se conectará ao microsoft Graph como o usuário atual para obter o perfil completo.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-108">When permission is granted, the app will connect to the Microsoft Graph as the current user to get the complete profile.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="2ccbc-109">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="2ccbc-109">Before you begin</span></span>

<span data-ttu-id="2ccbc-110">Certifique-se de que seu ambiente de desenvolvimento está definido instalando os [pré-requisitos](prerequisites.md)</span><span class="sxs-lookup"><span data-stu-id="2ccbc-110">Make sure your development environment is set up by installing the [prerequisites](prerequisites.md)</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2ccbc-111">Pré-requisitos de instalação</span><span class="sxs-lookup"><span data-stu-id="2ccbc-111">Install prerequisites</span></span>](prerequisites.md)

## <a name="create-your-project"></a><span data-ttu-id="2ccbc-112">Criar seu projeto</span><span class="sxs-lookup"><span data-stu-id="2ccbc-112">Create your project</span></span>

<span data-ttu-id="2ccbc-113">Use o Teams Toolkit para criar seu primeiro projeto:</span><span class="sxs-lookup"><span data-stu-id="2ccbc-113">Use the Teams Toolkit to create your first project:</span></span>

# <a name="visual-studio-2019"></a>[<span data-ttu-id="2ccbc-114">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="2ccbc-114">Visual Studio 2019</span></span>](#tab/vs)

1. <span data-ttu-id="2ccbc-115">Abra Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-115">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="2ccbc-116">Selecione **Criar um novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-116">Select **Create a new project**.</span></span>

1. <span data-ttu-id="2ccbc-117">Selecione **Microsoft Teams App** e pressione **Next**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-117">Select **Microsoft Teams App**, then press **Next**.</span></span>  <span data-ttu-id="2ccbc-118">Para ajudá-lo a encontrar o modelo, use o tipo de projeto **Microsoft Teams**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-118">To help you find the template, use the project type **Microsoft Teams**.</span></span>

1. <span data-ttu-id="2ccbc-119">Dê um bom nome ao projeto e à solução e pressione **Next**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-119">Give the project and solution a good name, then press **Next**.</span></span>

1. <span data-ttu-id="2ccbc-120">Forneça o nome do aplicativo e o nome da empresa e pressione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-120">Provide the application name and company name, then press **Create**.</span></span>  <span data-ttu-id="2ccbc-121">O nome do aplicativo e o nome da empresa são exibidos para os usuários finais.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-121">The application name and company name are displayed to your end users.</span></span>

1. <span data-ttu-id="2ccbc-122">Seu Teams aplicativo será criado em alguns segundos.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-122">Your Teams app will be created within a few seconds.</span></span>  <span data-ttu-id="2ccbc-123">Depois que o projeto for criado, configurar o logom único com o M365:</span><span class="sxs-lookup"><span data-stu-id="2ccbc-123">Once the project is created, set up single sign-on with M365:</span></span>

   - <span data-ttu-id="2ccbc-124">Selecione **Project**  >  **Configuração do TeamsFx**  >  **para SSO...**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-124">Select **Project** > **TeamsFx** > **Configure for SSO...**.</span></span>
   - <span data-ttu-id="2ccbc-125">Quando solicitado, entre em sua conta de administrador do M365.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-125">When prompted, sign in to your M365 administrator account.</span></span>

# <a name="command-line"></a>[<span data-ttu-id="2ccbc-126">Linha de comando</span><span class="sxs-lookup"><span data-stu-id="2ccbc-126">Command line</span></span>](#tab/cli)

1. <span data-ttu-id="2ccbc-127">Abra um Terminal e selecione o diretório onde você deseja criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-127">Open a Terminal and select the directory where you wish to create the project.</span></span>

1. <span data-ttu-id="2ccbc-128">Execute `dotnet new -i` para instalar o modelo de NuGet:</span><span class="sxs-lookup"><span data-stu-id="2ccbc-128">Run `dotnet new -i` to install the template from NuGet:</span></span>

   ``` bash
   dotnet new -i Microsoft.TeamsApp.Blazor
   ```

   <span data-ttu-id="2ccbc-129">Você só precisa fazer isso na primeira vez ou ao atualizar o modelo.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-129">You only need to do this the first time or when updating the template.</span></span>

1. <span data-ttu-id="2ccbc-130">Criar um diretório:</span><span class="sxs-lookup"><span data-stu-id="2ccbc-130">Create a directory:</span></span>

   ``` bash
   mkdir helloworld
   ```

1. <span data-ttu-id="2ccbc-131">Execute `dotnet new` para criar um novo projeto:</span><span class="sxs-lookup"><span data-stu-id="2ccbc-131">Run `dotnet new` to create a new project:</span></span>

   ``` bash
   dotnet new teamsapp --shortName my-teams-app --companyName "My Company"
   ```

1. <span data-ttu-id="2ccbc-132">Depois de scaffolded, configure o projeto para Teams implantação:</span><span class="sxs-lookup"><span data-stu-id="2ccbc-132">Once scaffolded, configure the project for Teams deployment:</span></span>

   ``` bash
   teamsfx init
   ```

<span data-ttu-id="2ccbc-133">Agora você pode abrir a solução em Visual Studio para depuração.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-133">You can now open the solution in Visual Studio for debugging.</span></span>

---

## <a name="take-a-tour-of-the-source-code"></a><span data-ttu-id="2ccbc-134">Fazer um tour pelo código-fonte</span><span class="sxs-lookup"><span data-stu-id="2ccbc-134">Take a tour of the source code</span></span>

<span data-ttu-id="2ccbc-135">Se quiser ignorar essa seção por enquanto, você pode [executar seu aplicativo localmente.](#run-your-app-locally)</span><span class="sxs-lookup"><span data-stu-id="2ccbc-135">If you wish to skip this section for now, you can [run your app locally](#run-your-app-locally).</span></span>

<span data-ttu-id="2ccbc-136">Depois que Teams Toolkit configura seu projeto, você tem os componentes para criar um aplicativo pessoal básico para Teams.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-136">Once the Teams Toolkit configures your project, you have the components to build a basic personal app for Teams.</span></span> <span data-ttu-id="2ccbc-137">Os diretórios e arquivos do projeto são exibidos na área Do Explorador de Soluções Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-137">The project directories and files display in the Solution Explorer area of Visual Studio 2019.</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/blazor-file-layout.png" alt-text="Captura de tela mostrando arquivos de projeto de aplicativo para um aplicativo pessoal Visual Studio 2019.":::

- <span data-ttu-id="2ccbc-139">Os ícones do aplicativo são armazenados como arquivos PNG `color.png` em `outline.png` e .</span><span class="sxs-lookup"><span data-stu-id="2ccbc-139">The app icons are stored as PNG files in `color.png` and `outline.png`.</span></span>
- <span data-ttu-id="2ccbc-140">O manifesto do aplicativo para publicação por meio do Portal do Desenvolvedor para Teams é armazenado em `Properties/manifest.json` .</span><span class="sxs-lookup"><span data-stu-id="2ccbc-140">The app manifest for publishing through the Developer Portal for Teams is stored in `Properties/manifest.json`.</span></span>
- <span data-ttu-id="2ccbc-141">Um controlador back-end é fornecido para `Controllers/BackendController.cs` ajudar na autenticação.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-141">A backend controller is provided in `Controllers/BackendController.cs` for assisting with authentication.</span></span>

<span data-ttu-id="2ccbc-142">Desde que você criou um aplicativo de tabulação durante a instalação, o Teams Toolkit estrutura todo o código necessário para uma guia básica como [um Servidor Blazor](/aspnet/core/blazor).</span><span class="sxs-lookup"><span data-stu-id="2ccbc-142">Since you created a tab app during setup, the Teams Toolkit scaffolds all the necessary code for a basic tab as a [Blazor Server](/aspnet/core/blazor).</span></span>

- <span data-ttu-id="2ccbc-143">`Pages/Tab.razor` é o ponto de entrada do aplicativo front-end.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-143">`Pages/Tab.razor` is the front-end application's entry point.</span></span>
- <span data-ttu-id="2ccbc-144">`TeamsFx.cs`e `JS/src/index.js` é usado para inicializar comunicações com o Teams host.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-144">`TeamsFx.cs` and `JS/src/index.js` is used for initializing communications with the Teams host.</span></span>

<span data-ttu-id="2ccbc-145">Você pode adicionar funcionalidade de back-end adicionando ASP.NET Core controladores adicionais ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-145">You can add backend functionality by adding additional ASP.NET Core controllers to your application.</span></span>

## <a name="run-your-app-locally"></a><span data-ttu-id="2ccbc-146">Executar seu aplicativo localmente</span><span class="sxs-lookup"><span data-stu-id="2ccbc-146">Run your app locally</span></span>

<span data-ttu-id="2ccbc-147">Teams Toolkit permite que você execute seu aplicativo localmente.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-147">Teams Toolkit allows you to run your app locally.</span></span>  <span data-ttu-id="2ccbc-148">Isso consiste em várias partes necessárias para fornecer a infraestrutura correta que Teams espera:</span><span class="sxs-lookup"><span data-stu-id="2ccbc-148">This consists of several parts that are necessary to provide the correct infrastructure that Teams expects:</span></span>

- <span data-ttu-id="2ccbc-149">Um aplicativo é registrado com Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-149">An application is registered with Azure Active Directory.</span></span>  <span data-ttu-id="2ccbc-150">Esse aplicativo tem permissões associadas ao local de onde o aplicativo é carregado e a todos os recursos de back-end que ele acessa.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-150">This application has permissions associated with the location that the app is loaded from and any backend resources it accesses.</span></span>
- <span data-ttu-id="2ccbc-151">Uma API da Web é hospedada (por meio IIS Express) para ajudar com tarefas de autenticação, atuando como um proxy entre o aplicativo e Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-151">A web API is hosted (via IIS Express) to assist with authentication tasks, acting as a proxy between the app and Azure Active Directory.</span></span>  
- <span data-ttu-id="2ccbc-152">Um manifesto de aplicativo é gerado e existe no Portal do Desenvolvedor para Teams.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-152">An app manifest is generated and exists in the Developer Portal for Teams.</span></span>  <span data-ttu-id="2ccbc-153">Teams usa o manifesto do aplicativo para dizer aos clientes conectados de onde carregar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-153">Teams uses the app manifest to tell connected clients where to load the app from.</span></span>

<span data-ttu-id="2ccbc-154">Depois que isso for feito, o aplicativo poderá ser carregado no Teams cliente.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-154">Once this is done, the app can be loaded within the Teams client.</span></span>  <span data-ttu-id="2ccbc-155">Usamos o Teams web para que possamos ver o código HTML, CSS e JavaScript em um ambiente de desenvolvimento da Web padrão.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-155">We use the Teams web client so that we can see the HTML, CSS, and JavaScript code within a standard web development environment.</span></span>

<span data-ttu-id="2ccbc-156">Para criar e executar seu aplicativo localmente:</span><span class="sxs-lookup"><span data-stu-id="2ccbc-156">To build and run your app locally:</span></span>

1. <span data-ttu-id="2ccbc-157">No Visual Studio Code, pressione **F5** para executar seu aplicativo no modo de depuração.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-157">From Visual Studio Code, press **F5** to run your application in debug mode.</span></span>

1. <span data-ttu-id="2ccbc-158">Se solicitado, instale o certificado SSL auto-assinado para depuração local.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-158">If requested, install the self-signed SSL certificate for local debugging.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/ssl-prompt.png" alt-text="Captura de tela mostrando como o prompt para instalar um certificado SSL para permitir Teams carregar seu aplicativo do localhost.":::

1. <span data-ttu-id="2ccbc-160">Teams será carregado em um navegador da Web e você será solicitado a entrar.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-160">Teams will be loaded in a web browser, and you will be prompted to sign in.</span></span> <span data-ttu-id="2ccbc-161">Se for solicitado a abrir Microsoft Teams, selecione Cancelar para permanecer no navegador.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-161">If prompted to open Microsoft Teams, select Cancel to remain within the browser.</span></span> <span data-ttu-id="2ccbc-162">Entre com sua conta do M365.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-162">Sign in with your M365 account.</span></span>
1. <span data-ttu-id="2ccbc-163">Quando solicitado a instalar o aplicativo no Teams, pressione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-163">When prompted to install the app onto Teams, press **Add**.</span></span>

<span data-ttu-id="2ccbc-164">Seu aplicativo agora será exibido:</span><span class="sxs-lookup"><span data-stu-id="2ccbc-164">Your app will now be displayed:</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/blazor-completed-app.png" alt-text="Captura de tela do aplicativo concluído":::

<span data-ttu-id="2ccbc-166">Você pode fazer atividades normais de depuração como se fosse qualquer outro aplicativo Web (como definir pontos de interrupção).</span><span class="sxs-lookup"><span data-stu-id="2ccbc-166">You can do normal debugging activities as if this were any other web application (such as setting breakpoints).</span></span> <span data-ttu-id="2ccbc-167">O aplicativo dá suporte ao recarregamento a quente.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-167">The app supports hot reloading.</span></span>  <span data-ttu-id="2ccbc-168">Se você alterar qualquer arquivo dentro do projeto, a página será recarregada.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-168">If you change any file within the project, the page will be reloaded.</span></span>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="2ccbc-169">Saiba o que acontece quando você executar seu aplicativo localmente no depurador.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-169">Learn what happens when you run your app locally in the debugger.</span></span></summary>

<span data-ttu-id="2ccbc-170">Quando você pressionou F5, o Teams Toolkit:</span><span class="sxs-lookup"><span data-stu-id="2ccbc-170">When you pressed F5, the Teams Toolkit:</span></span>

1. <span data-ttu-id="2ccbc-171">Registrou seu aplicativo com Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-171">Registered your application with Azure Active Directory.</span></span>
1. <span data-ttu-id="2ccbc-172">Registrou seu aplicativo para "side loading" no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-172">Registered your application for "side loading" in Microsoft Teams.</span></span>
1. <span data-ttu-id="2ccbc-173">Iniciou o back-end do aplicativo em execução localmente.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-173">Started your application backend running locally.</span></span>
1. <span data-ttu-id="2ccbc-174">Iniciou o front-end do aplicativo hospedado localmente.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-174">Started your application front-end hosted locally.</span></span>
1. <span data-ttu-id="2ccbc-175">Iniciado Microsoft Teams em um navegador da Web com um comando para instruir Teams carregar lateralmente o aplicativo (a URL é registrada dentro do manifesto do aplicativo).</span><span class="sxs-lookup"><span data-stu-id="2ccbc-175">Started Microsoft Teams in a web browser with a command to instruct Teams to side load the application (the URL is registered inside the application manifest).</span></span>

</details>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="2ccbc-176">Saiba como solucionar problemas comuns ao executar seu aplicativo localmente.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-176">Learn how to troubleshoot common issues when running your app locally.</span></span></summary>

<span data-ttu-id="2ccbc-177">Para executar seu aplicativo com êxito Teams, você deve ter uma conta Microsoft 365 de desenvolvimento que permita o carregamento do lado do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-177">To successfully run your app in Teams, you must have a Microsoft 365 development account that allows app side loading.</span></span> <span data-ttu-id="2ccbc-178">Para obter mais informações sobre a abertura da conta, consulte [Prerequisites](prerequisites.md#enable-sideloading).</span><span class="sxs-lookup"><span data-stu-id="2ccbc-178">For more information on account opening, see [Prerequisites](prerequisites.md#enable-sideloading).</span></span>

</details>

## <a name="deploy-your-app-to-azure"></a><span data-ttu-id="2ccbc-179">Implantar seu aplicativo no Azure</span><span class="sxs-lookup"><span data-stu-id="2ccbc-179">Deploy your app to Azure</span></span>

<span data-ttu-id="2ccbc-180">A implantação consiste em duas etapas.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-180">Deployment consists of two steps.</span></span>  <span data-ttu-id="2ccbc-181">Primeiro, os recursos de nuvem necessários são criados (também conhecidos como provisionamento), em seguida, o código que com o seu aplicativo é copiado para os recursos de nuvem criados.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-181">First, necessary cloud resources are created (also known as provisioning), then the code that makes up your app is copied into the created cloud resources.</span></span>

> <span data-ttu-id="2ccbc-182">**Visualizar**</span><span class="sxs-lookup"><span data-stu-id="2ccbc-182">**PREVIEW**</span></span>
>
> <span data-ttu-id="2ccbc-183">O suporte para aplicativos Blazor é novo no Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-183">Support for Blazor apps is new in Teams Toolkit.</span></span>  <span data-ttu-id="2ccbc-184">O provisionamento e a implantação são feitos com uma combinação de Visual Studio 2019 e o Portal do Desenvolvedor para Teams.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-184">Provisioning and deployment are done with a combination of Visual Studio 2019 and the Developer Portal for Teams.</span></span>

## <a name="provision-and-deploy-your-app-to-azure-app-service"></a><span data-ttu-id="2ccbc-185">Provisionar e implantar seu aplicativo no Serviço de Aplicativo do Azure</span><span class="sxs-lookup"><span data-stu-id="2ccbc-185">Provision and deploy your app to Azure App Service</span></span>

1. <span data-ttu-id="2ccbc-186">No Explorador de Soluções, clique com o botão direito do mouse no nó do projeto e escolha **Publicar** (ou use o **item** de menu Criar  >  **Publicar).**</span><span class="sxs-lookup"><span data-stu-id="2ccbc-186">In Solution Explorer, right-click the project node and choose **Publish** (or use the **Build** > **Publish** menu item).</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish1.png" alt-text="Selecione a operação Publicar no projeto":::

1. <span data-ttu-id="2ccbc-188">Na janela **Publicar,** selecione **Azure**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-188">In the **Publish** window, select **Azure**.</span></span>  <span data-ttu-id="2ccbc-189">Pressione **Next**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-189">Press **Next**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish2.png" alt-text="Selecione O Azure como o destino de publicação":::

1. <span data-ttu-id="2ccbc-191">Selecione Serviço de Aplicativo do **Azure (Windows)**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-191">Select **Azure App Service (Windows)**.</span></span>  <span data-ttu-id="2ccbc-192">Pressione **Next**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-192">Press **Next**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish3.png" alt-text="Selecione Serviço de Aplicativo do Azure como o destino de publicação":::

1. <span data-ttu-id="2ccbc-194">Selecione **+** para criar uma nova instância do Serviço de Aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-194">Select **+** to create a new App Service instance.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish4.png" alt-text="Crie uma nova instância.":::

1. <span data-ttu-id="2ccbc-196">Na caixa de diálogo Criar Serviço de Aplicativo **(Windows),** os campos  de entrada **Nome,** Nome da **Assinatura,** Grupo de Recursos e Plano de Hospedagem são preenchidos. </span><span class="sxs-lookup"><span data-stu-id="2ccbc-196">In the **Create App Service (Windows)** dialog, the **Name**, **Subscription name**, **Resource Group**, and **Hosting Plan** entry fields are populated.</span></span> <span data-ttu-id="2ccbc-197">Se você já tiver um Serviço de Aplicativo em execução, as configurações existentes serão selecionadas.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-197">If you have already got an App Service running, existing settings will be selected.</span></span>  <span data-ttu-id="2ccbc-198">Você pode optar por criar um novo grupo de recursos e um plano de hospedagem (Recomendado).</span><span class="sxs-lookup"><span data-stu-id="2ccbc-198">You can opt to create a new resource group and hosting plan (Recommended).</span></span>  <span data-ttu-id="2ccbc-199">Quando estiver pronto, selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-199">When ready, select **Create**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish5.png" alt-text="Selecionar plano de hospedagem e assinatura":::

1. <span data-ttu-id="2ccbc-201">Na caixa **de diálogo Publicar,** a instância recém-criada foi selecionada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-201">In the **Publish** dialog, the newly created instance has been automatically selected.</span></span>  <span data-ttu-id="2ccbc-202">Quando estiver pronto, selecione **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-202">When ready, select **Finish**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish6.png" alt-text="Selecione a nova instância.":::

1. <span data-ttu-id="2ccbc-204">Pressione o **ícone Editar** (lápis) ao lado de Modo **de Implantação** e selecione **Autocontiver**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-204">Press the **Edit** (pencil) icon next to **Deployment Mode**, then select **Self-contained**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish8.png" alt-text="Selecione o modo de implantação autoconstrutivo.":::

1. <span data-ttu-id="2ccbc-206">Selecionar **Publicar**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-206">Select **Publish**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish7.png" alt-text="Publicar seu aplicativo no serviço de aplicativo":::

<span data-ttu-id="2ccbc-208">Visual Studio implanta o aplicativo no Serviço de Aplicativo do Azure e o aplicativo Web é carregado no navegador.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-208">Visual Studio deploys the app to your Azure App Service, and the web app loads in your browser.</span></span>  <span data-ttu-id="2ccbc-209">Adicione `/tab` ao final da URL para ver sua página.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-209">Add `/tab` to the end of the URL to see your page.</span></span>

<span data-ttu-id="2ccbc-210">O painel **Publicar propriedades** do projeto mostra a URL do site e outros detalhes.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-210">The project properties **Publish** pane shows the site URL and other details.</span></span> <span data-ttu-id="2ccbc-211">Anote a URL do site.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-211">Make a note of the site URL.</span></span>

## <a name="create-an-environment-for-your-app"></a><span data-ttu-id="2ccbc-212">Criar um ambiente para seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="2ccbc-212">Create an environment for your app</span></span>

<span data-ttu-id="2ccbc-213">O Portal do Desenvolvedor para Teams gerencia de onde as guias do seu aplicativo são carregadas com um **Environment**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-213">The Developer Portal for Teams manages where the tabs for your app are loaded from with an **Environment**.</span></span>  <span data-ttu-id="2ccbc-214">Para criar um ambiente:</span><span class="sxs-lookup"><span data-stu-id="2ccbc-214">To create an environment:</span></span>

1. <span data-ttu-id="2ccbc-215">Abra o [Portal do Desenvolvedor para Teams](https://dev.teams.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="2ccbc-215">Open the [Developer Portal for Teams](https://dev.teams.microsoft.com).</span></span>  <span data-ttu-id="2ccbc-216">Entre com sua conta administrativa do M365.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-216">Sign in with your M365 administrative account.</span></span>

1. <span data-ttu-id="2ccbc-217">Na barra lateral, selecione **Aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-217">From the sidebar, select **Apps**.</span></span>

1. <span data-ttu-id="2ccbc-218">Se você tiver apenas um aplicativo, ele será selecionado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-218">If you only have one app, it will be automatically selected.</span></span>  <span data-ttu-id="2ccbc-219">Caso não seja, selecione seu aplicativo na lista.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-219">If not, select your app from the list.</span></span>

1. <span data-ttu-id="2ccbc-220">Selecione **Ambientes**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-220">Select **Environments**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments1.png" alt-text="Selecionar ambientes":::

1. <span data-ttu-id="2ccbc-222">Selecione **Criar seu primeiro ambiente**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-222">Select **Create your first environment**.</span></span>

1. <span data-ttu-id="2ccbc-223">Insira um nome para seu ambiente e pressione **Adicionar**; por _exemplo, Produção_.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-223">Enter a name for your environment, then press **Add**; for example _Production_.</span></span>

1. <span data-ttu-id="2ccbc-224">Com o ambiente recém-criado selecionado, pressione **Criar sua primeira variável de ambiente**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-224">With the newly created environment selected, press **Create your first environment variable**.</span></span>

1. <span data-ttu-id="2ccbc-225">Insira `azure_app_url` para o **nome**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-225">Enter `azure_app_url` for the **Name**.</span></span>  <span data-ttu-id="2ccbc-226">Insira a URL do site do Azure (sem `https://` a ) como o **Valor**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-226">Enter your Azure site URL (without the `https://`) as the **Value**.</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments2.png" alt-text="Criar variável de ambiente":::

   <span data-ttu-id="2ccbc-228">Pressione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-228">Press **Add**.</span></span>

## <a name="update-the-app-manifest"></a><span data-ttu-id="2ccbc-229">Atualizar o manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="2ccbc-229">Update the app manifest</span></span>

<span data-ttu-id="2ccbc-230">O manifesto do aplicativo está carregando a guia de uma `localhost` URL.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-230">The app manifest is loading the tab from a `localhost` URL.</span></span>  <span data-ttu-id="2ccbc-231">Nesta seção, você ajustará o manifesto do aplicativo para carregar a guia da URL listada no ambiente que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-231">In this section, you will adjust the app manifest to load the tab from the URL listed within the environment you just created.</span></span>

1. <span data-ttu-id="2ccbc-232">Na barra lateral, selecione **Informações básicas**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-232">From the sidebar, select **Basic information**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments3.png" alt-text="Selecionar informações básicas":::

1. <span data-ttu-id="2ccbc-234">Há vários locais dentro do manifesto que listam uma `locahost:XXXXX` como parte de uma URL.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-234">There are several places within the manifest that list a `locahost:XXXXX` as part of a URL.</span></span>  <span data-ttu-id="2ccbc-235">Substitua todas as ocorrências `{{azure_app_url}}` por (incluindo as chaves).</span><span class="sxs-lookup"><span data-stu-id="2ccbc-235">Replace all occurrences with `{{azure_app_url}}` (including the curly braces).</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments4.png" alt-text="Ajustar informações básicas para o ambiente":::

1. <span data-ttu-id="2ccbc-237">Quando estiver concluído, pressione **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-237">When complete, press **Save**.</span></span>

1. <span data-ttu-id="2ccbc-238">Na barra lateral, selecione **Recursos**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-238">From the sidebar, select **Capabilities**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments5.png" alt-text="Selecionar recursos":::

1. <span data-ttu-id="2ccbc-240">Selecione **Guia Pessoal**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-240">Select **Personal Tab**.</span></span>
1. <span data-ttu-id="2ccbc-241">Ao lado da **Guia Pessoal,** selecione os pontos tríplices e selecione **Editar**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-241">Next to the **Personal Tab**, select the triple dots, then select **Edit**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments6.png" alt-text="Editar configurações de tabulação pessoal":::

1. <span data-ttu-id="2ccbc-243">Substitua a URL pela variável de ambiente nos campos **Url de Conteúdo** e Url **do** Site.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-243">Replace the URL with the environment variable within the **Content Url** and **Website Url** fields.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments7.png" alt-text="Editar URLs de tabulação pessoal":::

1. <span data-ttu-id="2ccbc-245">Pressione **Update**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-245">Press **Update**.</span></span>

1. <span data-ttu-id="2ccbc-246">Clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-246">Press **Save**.</span></span>

1. <span data-ttu-id="2ccbc-247">Na barra lateral, selecione **Single Sign-On**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-247">From the sidebar, select **Single Sign-On**.</span></span>

1. <span data-ttu-id="2ccbc-248">Substitua o `localhost` URI de **ID do aplicativo** por `{{azure_app_url}}` .</span><span class="sxs-lookup"><span data-stu-id="2ccbc-248">Replace the `localhost` within the **Application ID URI** with `{{azure_app_url}}`.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments8.png" alt-text="Editar URI de ID de aplicativo de login único":::

1. <span data-ttu-id="2ccbc-250">Clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-250">Press **Save**.</span></span>

1. <span data-ttu-id="2ccbc-251">Na barra lateral, pressione **Domínios**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-251">From the sidebar, press **Domains**.</span></span>

1. <span data-ttu-id="2ccbc-252">Pressione **Adicionar um domínio**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-252">Press **Add a domain**.</span></span>

1. <span data-ttu-id="2ccbc-253">Se `{{azure_app_url}}` não estiver listado como um domínio válido, adicione-o como um domínio válido e pressione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-253">If `{{azure_app_url}}` is not listed as a valid domain, add it as a valid domain, then press **Add**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments9.png" alt-text="Adicionar um domínio":::

<span data-ttu-id="2ccbc-255">Agora você pode usar o **botão Visualizar Teams** na parte superior da página para iniciar seu aplicativo em Teams.</span><span class="sxs-lookup"><span data-stu-id="2ccbc-255">You can now use the **Preview in Teams** button at the top of the page to launch your app within Teams.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2ccbc-256">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="2ccbc-256">Next steps</span></span>

<span data-ttu-id="2ccbc-257">Saiba mais sobre outros métodos para criar Teams aplicativos:</span><span class="sxs-lookup"><span data-stu-id="2ccbc-257">Learn about other methods for creating Teams apps:</span></span>

- [<span data-ttu-id="2ccbc-258">Criar um Teams com React</span><span class="sxs-lookup"><span data-stu-id="2ccbc-258">Create a Teams app with React</span></span>](first-app-react.md)
- <span data-ttu-id="2ccbc-259">[Criar um Teams como uma Web Part SharePoint](first-app-spfx.md) (o Azure não é necessário)</span><span class="sxs-lookup"><span data-stu-id="2ccbc-259">[Create a Teams app as a SharePoint Web Part](first-app-spfx.md) (Azure not required)</span></span>
- [<span data-ttu-id="2ccbc-260">Criar um aplicativo bot de conversação</span><span class="sxs-lookup"><span data-stu-id="2ccbc-260">Create a conversational bot app</span></span>](first-app-bot.md)
- [<span data-ttu-id="2ccbc-261">Criar uma extensão de mensagens</span><span class="sxs-lookup"><span data-stu-id="2ccbc-261">Create a messaging extension</span></span>](first-message-extension.md)
