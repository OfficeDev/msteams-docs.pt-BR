---
title: Começar - Criar seu primeiro aplicativo Teams com o Blazor
author: adrianhall
description: Crie rapidamente um aplicativo do Microsoft Teams que exibe uma mensagem "Olá, Mundo!" usando o Microsoft Teams Toolkit e o .NET Blazor.
ms.author: adhal
ms.date: 04/27/2021
ms.topic: quickstart
ms.openlocfilehash: c14f55d014af120cab88044d31ee8600017e3c57
ms.sourcegitcommit: 9d63611974ba8a7e7f19ceea35e50189a2e90434
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2021
ms.locfileid: "53254304"
---
# <a name="build-and-run-your-first-microsoft-teams-app-with-blazor"></a><span data-ttu-id="eb041-104">Criar e executar seu primeiro aplicativo Microsoft Teams com o Blazor</span><span class="sxs-lookup"><span data-stu-id="eb041-104">Build and run your first Microsoft Teams app with Blazor</span></span>

<span data-ttu-id="eb041-105">Neste tutorial, você aprenderá a criar um novo aplicativo Microsoft Teams no .NET/Blazor que implementa um aplicativo pessoal simples para obter informações do microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="eb041-105">In this tutorial, you will learn how to create a new Microsoft Teams app in .NET/Blazor that implements a simple personal app to pull information from the Microsoft Graph.</span></span> <span data-ttu-id="eb041-106">Por exemplo, um *aplicativo pessoal* inclui um conjunto de guias para uso individual.</span><span class="sxs-lookup"><span data-stu-id="eb041-106">For example, a *personal app* includes a set of tabs for individual use.</span></span> <span data-ttu-id="eb041-107">Durante o tutorial, você aprenderá sobre a estrutura de um aplicativo Teams, como executar um aplicativo localmente e como implantar o aplicativo no Azure.</span><span class="sxs-lookup"><span data-stu-id="eb041-107">During the tutorial, you will learn about the structure of a Teams app, how to run an app locally, and how to deploy the app to Azure.</span></span>

<span data-ttu-id="eb041-108">O aplicativo que é compilado exibe informações básicas para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="eb041-108">The app that is built displays basic user information for the current user.</span></span>  <span data-ttu-id="eb041-109">Quando a permissão é concedida, o aplicativo se conectará ao Microsoft Graph como o usuário atual para obter o perfil completo.</span><span class="sxs-lookup"><span data-stu-id="eb041-109">When permission is granted, the app will connect to the Microsoft Graph as the current user to get the complete profile.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="eb041-110">Antes de você começar</span><span class="sxs-lookup"><span data-stu-id="eb041-110">Before you begin</span></span>

<span data-ttu-id="eb041-111">Certifique-se de que seu ambiente de desenvolvimento está definido instalando os pré-requisitos.</span><span class="sxs-lookup"><span data-stu-id="eb041-111">Make sure your development environment is set up by installing the prerequisites.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="eb041-112">Instalar pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="eb041-112">Install prerequisites</span></span>](prerequisites.md)

## <a name="create-your-project"></a><span data-ttu-id="eb041-113">Criar seu projeto</span><span class="sxs-lookup"><span data-stu-id="eb041-113">Create your project</span></span>

<span data-ttu-id="eb041-114">Use o Kit de ferramentas do Teams para criar o seu primeiro projeto:</span><span class="sxs-lookup"><span data-stu-id="eb041-114">Use the Teams Toolkit to create your first project:</span></span>

# <a name="visual-studio-2019"></a>[<span data-ttu-id="eb041-115">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="eb041-115">Visual Studio 2019</span></span>](#tab/vs)

1. <span data-ttu-id="eb041-116">Abra Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="eb041-116">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="eb041-117">Selecione **Criar um novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="eb041-117">Select **Create a new project**.</span></span>

1. <span data-ttu-id="eb041-118">Selecione **Microsoft Teams App** e, em seguida, selecione **Próximo**.</span><span class="sxs-lookup"><span data-stu-id="eb041-118">Select **Microsoft Teams App**, then select **Next**.</span></span>  <span data-ttu-id="eb041-119">Para ajudá-lo a encontrar o modelo, use o tipo de projeto **Microsoft Teams**.</span><span class="sxs-lookup"><span data-stu-id="eb041-119">To help you find the template, use the project type **Microsoft Teams**.</span></span>

1. <span data-ttu-id="eb041-120">Insira um nome e selecione **Next**.</span><span class="sxs-lookup"><span data-stu-id="eb041-120">Enter a name and select **Next**.</span></span>

1. <span data-ttu-id="eb041-121">Insira o nome do aplicativo e o nome da empresa.</span><span class="sxs-lookup"><span data-stu-id="eb041-121">Enter the application name and company name.</span></span>

1. <span data-ttu-id="eb041-122">Selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="eb041-122">Select **Create**.</span></span>  <span data-ttu-id="eb041-123">O nome do aplicativo e o nome da empresa são exibidos para os usuários finais.</span><span class="sxs-lookup"><span data-stu-id="eb041-123">The application name and company name are displayed to your end users.</span></span> <span data-ttu-id="eb041-124">O seu aplicativo do Teams será criado em alguns segundos.</span><span class="sxs-lookup"><span data-stu-id="eb041-124">Your Teams app will be created within a few seconds.</span></span>  <span data-ttu-id="eb041-125">Depois que o projeto for criado, configurar o logom único com o M365:</span><span class="sxs-lookup"><span data-stu-id="eb041-125">After the project is created, set up single sign-on with M365:</span></span>

   1. <span data-ttu-id="eb041-126">Selecione **Project**  >  **Configuração do TeamsFx**  >  **para SSO...**.</span><span class="sxs-lookup"><span data-stu-id="eb041-126">Select **Project** > **TeamsFx** > **Configure for SSO...**.</span></span>
   1. <span data-ttu-id="eb041-127">Quando solicitado, entre em sua conta de administrador do M365.</span><span class="sxs-lookup"><span data-stu-id="eb041-127">When prompted, sign in to your M365 administrator account.</span></span>

# <a name="command-line"></a>[<span data-ttu-id="eb041-128">Linha de comando</span><span class="sxs-lookup"><span data-stu-id="eb041-128">Command line</span></span>](#tab/cli)

1. <span data-ttu-id="eb041-129">Abra um Terminal e selecione o diretório onde você deseja criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="eb041-129">Open a Terminal and select the directory where you wish to create the project.</span></span>

1. <span data-ttu-id="eb041-130">Execute `dotnet new -i` para instalar o modelo de NuGet:</span><span class="sxs-lookup"><span data-stu-id="eb041-130">Run `dotnet new -i` to install the template from NuGet:</span></span>

   ``` bash
   dotnet new --install Microsoft.TeamsFx.VisualStudio.ProjectTemplates::0.1.43-beta
   ```

   <span data-ttu-id="eb041-131">Você só precisa fazer isso na primeira vez ou ao atualizar o modelo.</span><span class="sxs-lookup"><span data-stu-id="eb041-131">You only need to do this the first time or when updating the template.</span></span> <span data-ttu-id="eb041-132">Verifique [NuGet](https://www.nuget.org/packages/Microsoft.TeamsFx.VisualStudio.ProjectTemplates/) a versão mais recente deste pacote.</span><span class="sxs-lookup"><span data-stu-id="eb041-132">Check [NuGet](https://www.nuget.org/packages/Microsoft.TeamsFx.VisualStudio.ProjectTemplates/) for the latest version of this package.</span></span>

1. <span data-ttu-id="eb041-133">Criar um diretório:</span><span class="sxs-lookup"><span data-stu-id="eb041-133">Create a directory:</span></span>

   ``` bash
   mkdir helloworld
   ```

1. <span data-ttu-id="eb041-134">Execute `dotnet new` para criar um novo projeto:</span><span class="sxs-lookup"><span data-stu-id="eb041-134">Run `dotnet new` to create a new project:</span></span>

   ``` bash
   dotnet new teamsapp --shortName my-teams-app --companyName "My Company"
   ```

1. <span data-ttu-id="eb041-135">Após o scaffolding, configure o projeto para Teams implantação:</span><span class="sxs-lookup"><span data-stu-id="eb041-135">After scaffolding, configure the project for Teams deployment:</span></span>

   ``` bash
   teamsfx init
   ```

   <span data-ttu-id="eb041-136">Agora você pode abrir a solução em Visual Studio para depuração.</span><span class="sxs-lookup"><span data-stu-id="eb041-136">You can now open the solution in Visual Studio for debugging.</span></span>

---

## <a name="take-a-tour-of-the-source-code"></a><span data-ttu-id="eb041-137">Faça um tour pelo código-fonte</span><span class="sxs-lookup"><span data-stu-id="eb041-137">Take a tour of the source code</span></span>

<span data-ttu-id="eb041-138">Se desejar pular esta seção por enquanto, você pode [executar seu aplicativo localmente](#run-your-app-locally).</span><span class="sxs-lookup"><span data-stu-id="eb041-138">If you wish to skip this section for now, you can [run your app locally](#run-your-app-locally).</span></span>

<span data-ttu-id="eb041-139">Após a Teams Toolkit configura seu projeto, você terá os componentes para criar um aplicativo pessoal básico para Teams.</span><span class="sxs-lookup"><span data-stu-id="eb041-139">After the Teams Toolkit configures your project, you have the components to build a basic personal app for Teams.</span></span> <span data-ttu-id="eb041-140">Os diretórios e arquivos do projeto são exibidos na área Do Explorador de Soluções Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="eb041-140">The project directories and files display in the Solution Explorer area of Visual Studio 2019.</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/blazor-file-layout.png" alt-text="Captura de tela mostrando arquivos de projeto de aplicativo para um aplicativo pessoal Visual Studio 2019.":::

- <span data-ttu-id="eb041-142">Os ícones do aplicativo são armazenados como arquivos PNG em `color.png` e `outline.png`.</span><span class="sxs-lookup"><span data-stu-id="eb041-142">The app icons are stored as PNG files in `color.png` and `outline.png`.</span></span>
- <span data-ttu-id="eb041-143">O manifesto do aplicativo para publicação por meio do Portal do Desenvolvedor para Teams é armazenado em `Properties/manifest.json` .</span><span class="sxs-lookup"><span data-stu-id="eb041-143">The app manifest for publishing through the Developer Portal for Teams is stored in `Properties/manifest.json`.</span></span>
- <span data-ttu-id="eb041-144">Um controlador back-end é fornecido para `Controllers/BackendController.cs` ajudar na autenticação.</span><span class="sxs-lookup"><span data-stu-id="eb041-144">A backend controller is provided in `Controllers/BackendController.cs` for assisting with authentication.</span></span>

<span data-ttu-id="eb041-145">Desde que você criou um aplicativo de tabulação durante a instalação, o Teams Toolkit estrutura todo o código necessário para uma guia básica como [um Servidor Blazor](/aspnet/core/blazor).</span><span class="sxs-lookup"><span data-stu-id="eb041-145">Since you created a tab app during setup, the Teams Toolkit scaffolds all the necessary code for a basic tab as a [Blazor Server](/aspnet/core/blazor).</span></span>

- <span data-ttu-id="eb041-146">`Pages/Tab.razor` é o ponto de entrada do aplicativo front-end.</span><span class="sxs-lookup"><span data-stu-id="eb041-146">`Pages/Tab.razor` is the front-end application's entry point.</span></span>
- <span data-ttu-id="eb041-147">`TeamsFx.cs`e `JS/src/index.js` é usado para inicializar comunicações com o Teams host.</span><span class="sxs-lookup"><span data-stu-id="eb041-147">`TeamsFx.cs` and `JS/src/index.js` is used for initializing communications with the Teams host.</span></span>

<span data-ttu-id="eb041-148">Você pode adicionar funcionalidade de back-end adicionando ASP.NET Core controladores adicionais ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eb041-148">You can add backend functionality by adding additional ASP.NET Core controllers to your application.</span></span>

## <a name="run-your-app-locally"></a><span data-ttu-id="eb041-149">Executar seu aplicativo localmente</span><span class="sxs-lookup"><span data-stu-id="eb041-149">Run your app locally</span></span>

<span data-ttu-id="eb041-150">O Kit de ferramentas do Teams permite que você execute seu aplicativo localmente.</span><span class="sxs-lookup"><span data-stu-id="eb041-150">Teams Toolkit allows you to run your app locally.</span></span>  <span data-ttu-id="eb041-151">Isto consiste de várias partes que são necessárias para fornecer a infraestrutura correta que o Teams espera:</span><span class="sxs-lookup"><span data-stu-id="eb041-151">This consists of several parts that are necessary to provide the correct infrastructure that Teams expects:</span></span>

- <span data-ttu-id="eb041-152">Um aplicativo está registrado no Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="eb041-152">An application is registered with Azure Active Directory.</span></span>  <span data-ttu-id="eb041-153">Este aplicativo tem permissões associadas ao local de onde o aplicativo é carregado e a quaisquer recursos de back-end que ele acesse.</span><span class="sxs-lookup"><span data-stu-id="eb041-153">This application has permissions associated with the location that the app is loaded from and any backend resources it accesses.</span></span>
- <span data-ttu-id="eb041-154">Uma API da Web é hospedada (por meio IIS Express) para ajudar com tarefas de autenticação, atuando como um proxy entre o aplicativo e Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="eb041-154">A web API is hosted (via IIS Express) to assist with authentication tasks, acting as a proxy between the app and Azure Active Directory.</span></span>  
- <span data-ttu-id="eb041-155">Um manifesto de aplicativo é gerado e existe no Portal de Desenvolvedor do Teams.</span><span class="sxs-lookup"><span data-stu-id="eb041-155">An app manifest is generated and exists in the Developer Portal for Teams.</span></span>  <span data-ttu-id="eb041-156">O Teams usa o manifesto do aplicativo para dizer aos clientes conectados de onde carregar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eb041-156">Teams uses the app manifest to tell connected clients where to load the app from.</span></span>

<span data-ttu-id="eb041-157">Depois que isso for feito, o aplicativo poderá ser carregado no cliente Teams cliente.</span><span class="sxs-lookup"><span data-stu-id="eb041-157">After this is done, the app can be loaded within the Teams client.</span></span>  <span data-ttu-id="eb041-158">Usamos o cliente Web do Teams para que possamos ver o código HTML, CSS e JavaScript dentro de um ambiente de desenvolvimento web padrão.</span><span class="sxs-lookup"><span data-stu-id="eb041-158">We use the Teams web client so that we can see the HTML, CSS, and JavaScript code within a standard web development environment.</span></span>

<span data-ttu-id="eb041-159">Para compilar e executar seu aplicativo localmente:</span><span class="sxs-lookup"><span data-stu-id="eb041-159">To build and run your app locally:</span></span>


1. <span data-ttu-id="eb041-160">Na Visual Studio Code, pressione a **tecla F5** para executar seu aplicativo no modo de depuração.</span><span class="sxs-lookup"><span data-stu-id="eb041-160">From Visual Studio Code, press the **F5** key to run your application in debug mode.</span></span>


1. <span data-ttu-id="eb041-161">Se solicitado, instale o certificado SSL auto-assinado para depuração local.</span><span class="sxs-lookup"><span data-stu-id="eb041-161">If requested, install the self-signed SSL certificate for local debugging.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/ssl-prompt.png" alt-text="Captura de tela mostrando como a solicitação de instalação de um certificado SSL para permitir que o Teams carregue seu aplicativo a partir do localhost.":::

1. <span data-ttu-id="eb041-163">O Teams é carregado em um navegador da Web e você será solicitado a entrar.</span><span class="sxs-lookup"><span data-stu-id="eb041-163">Teams will be loaded in a web browser, and you will be prompted to sign in.</span></span> <span data-ttu-id="eb041-164">Se for solicitado a abrir o Microsoft Teams, selecione Cancelar para permanecer no navegador.</span><span class="sxs-lookup"><span data-stu-id="eb041-164">If prompted to open Microsoft Teams, select Cancel to remain within the browser.</span></span> <span data-ttu-id="eb041-165">Entre com sua conta do M365.</span><span class="sxs-lookup"><span data-stu-id="eb041-165">Sign in with your M365 account.</span></span>

1. <span data-ttu-id="eb041-166">Quando solicitado a instalar o aplicativo no Teams, selecione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="eb041-166">When prompted to install the app onto Teams, select **Add**.</span></span>

   <span data-ttu-id="eb041-167">Seu aplicativo agora será exibido:</span><span class="sxs-lookup"><span data-stu-id="eb041-167">Your app will now be displayed:</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-completed-app.png" alt-text="Captura de tela do aplicativo concluído":::

   <span data-ttu-id="eb041-169">Você pode executar as atividades de depuração como se fosse qualquer outro aplicativo Web, como a definição de pontos de interrupção.</span><span class="sxs-lookup"><span data-stu-id="eb041-169">You can perform the debugging activities as if this were any other web application like setting breakpoints.</span></span> <span data-ttu-id="eb041-170">O aplicativo dá suporte à recarga dinâmica.</span><span class="sxs-lookup"><span data-stu-id="eb041-170">The app supports hot reloading.</span></span>  <span data-ttu-id="eb041-171">Se você alterar qualquer arquivo dentro do projeto, a página será recarregada.</span><span class="sxs-lookup"><span data-stu-id="eb041-171">If you change any file within the project, the page will be reloaded.</span></span>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="eb041-172">Saiba o que acontece quando você executa seu aplicativo localmente no depurador.</span><span class="sxs-lookup"><span data-stu-id="eb041-172">Learn what happens when you run your app locally in the debugger.</span></span></summary>

<span data-ttu-id="eb041-173">Quando você pressiona a **tecla F5,** o Teams Toolkit:</span><span class="sxs-lookup"><span data-stu-id="eb041-173">When you press the **F5** key, the Teams Toolkit:</span></span>

1. <span data-ttu-id="eb041-174">Registra seu aplicativo com Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="eb041-174">Registers your application with Azure Active Directory.</span></span>
1. <span data-ttu-id="eb041-175">Registra seu aplicativo para "side loading" no Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="eb041-175">Registers your application for "side loading" in Microsoft Teams.</span></span>
1. <span data-ttu-id="eb041-176">Inicia o back-end do aplicativo em execução localmente.</span><span class="sxs-lookup"><span data-stu-id="eb041-176">Starts your application backend running locally.</span></span>
1. <span data-ttu-id="eb041-177">Inicia o front-end do aplicativo hospedado localmente.</span><span class="sxs-lookup"><span data-stu-id="eb041-177">Starts your application front-end hosted locally.</span></span>
1. <span data-ttu-id="eb041-178">Inicia Microsoft Teams em um navegador da Web com um comando para instruir Teams carregar o aplicativo de lado (a URL é registrada dentro do manifesto do aplicativo).</span><span class="sxs-lookup"><span data-stu-id="eb041-178">Starts Microsoft Teams in a web browser with a command to instruct Teams to side load the application (the URL is registered inside the application manifest).</span></span>

</details>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="eb041-179">Saiba como solucionar problemas comuns ao executar seu aplicativo localmente.</span><span class="sxs-lookup"><span data-stu-id="eb041-179">Learn how to troubleshoot common issues when running your app locally.</span></span></summary>

<span data-ttu-id="eb041-180">Para executar seu aplicativo com êxito Teams, você deve ter uma conta Microsoft 365 de desenvolvimento que permita o carregamento do lado do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eb041-180">To successfully run your app in Teams, you must have a Microsoft 365 development account that allows app side loading.</span></span> <span data-ttu-id="eb041-181">Para obter mais informações sobre abertura de conta, confira [Pré-requisitos](prerequisites.md#enable-sideloading).</span><span class="sxs-lookup"><span data-stu-id="eb041-181">For more information on account opening, see [Prerequisites](prerequisites.md#enable-sideloading).</span></span>

</details>

## <a name="deploy-your-app-to-azure"></a><span data-ttu-id="eb041-182">Implantar seu aplicativo no Azure</span><span class="sxs-lookup"><span data-stu-id="eb041-182">Deploy your app to Azure</span></span>

<span data-ttu-id="eb041-183">A implantação consiste em duas etapas:</span><span class="sxs-lookup"><span data-stu-id="eb041-183">Deployment consists of two steps:</span></span> 

1. <span data-ttu-id="eb041-184">Recursos de nuvem necessários são criados.</span><span class="sxs-lookup"><span data-stu-id="eb041-184">Necessary cloud resources are created.</span></span> <span data-ttu-id="eb041-185">Isso também é conhecido como provisionamento.</span><span class="sxs-lookup"><span data-stu-id="eb041-185">This is also known as provisioning.</span></span>
1. <span data-ttu-id="eb041-186">Comece a codificar e copie seu aplicativo para os recursos de nuvem criados.</span><span class="sxs-lookup"><span data-stu-id="eb041-186">Start coding and copy your app into the created cloud resources.</span></span>

> <span data-ttu-id="eb041-187">**Visualizar**</span><span class="sxs-lookup"><span data-stu-id="eb041-187">**PREVIEW**</span></span>
>
> <span data-ttu-id="eb041-188">O suporte para aplicativos Blazor é novo no Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="eb041-188">Support for Blazor apps is new in Teams Toolkit.</span></span>  <span data-ttu-id="eb041-189">O provisionamento e a implantação são feitos com uma combinação de Visual Studio 2019 e o Portal do Desenvolvedor para Teams.</span><span class="sxs-lookup"><span data-stu-id="eb041-189">Provisioning and deployment are done with a combination of Visual Studio 2019 and the Developer Portal for Teams.</span></span>

## <a name="provision-and-deploy-your-app-to-azure-app-service"></a><span data-ttu-id="eb041-190">Provisionar e implantar seu aplicativo no Serviço de Aplicativo do Azure</span><span class="sxs-lookup"><span data-stu-id="eb041-190">Provision and deploy your app to Azure App Service</span></span>

1. <span data-ttu-id="eb041-191">No Explorador de Soluções, clique com o botão direito do mouse no nó do projeto e selecione **Publicar**.</span><span class="sxs-lookup"><span data-stu-id="eb041-191">In Solution Explorer, right-click the project node and select **Publish**.</span></span> <span data-ttu-id="eb041-192">Você também pode usar o item de menu **Criar**  >  **Publicar.**</span><span class="sxs-lookup"><span data-stu-id="eb041-192">You can also use the **Build** > **Publish** menu item.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish1.png" alt-text="Selecione a operação Publicar no projeto":::

1. <span data-ttu-id="eb041-194">Na janela **Publicar,** selecione **Azure** e selct **Next**.</span><span class="sxs-lookup"><span data-stu-id="eb041-194">In the **Publish** window, select **Azure** and selct **Next**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish2.png" alt-text="Selecione O Azure como o destino de publicação":::

1. <span data-ttu-id="eb041-196">Selecione Serviço de Aplicativo do **Azure (Windows)** e selecione **Próximo**.</span><span class="sxs-lookup"><span data-stu-id="eb041-196">Select **Azure App Service (Windows)** and select **Next**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish3.png" alt-text="Selecione Serviço de Aplicativo do Azure como o destino de publicação":::

1. <span data-ttu-id="eb041-198">Selecione **+** para criar uma nova instância do Serviço de Aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eb041-198">Select **+** to create a new App Service instance.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish4.png" alt-text="Crie uma nova instância.":::

1. <span data-ttu-id="eb041-200">Na caixa de diálogo Criar Serviço de Aplicativo **(Windows),** os campos  de entrada **Nome,** Nome da **Assinatura,** Grupo de Recursos e Plano de Hospedagem são preenchidos. </span><span class="sxs-lookup"><span data-stu-id="eb041-200">In the **Create App Service (Windows)** dialog, the **Name**, **Subscription name**, **Resource Group**, and **Hosting Plan** entry fields are populated.</span></span> <span data-ttu-id="eb041-201">Se você já tiver um Serviço de Aplicativo em execução, as configurações existentes serão selecionadas.</span><span class="sxs-lookup"><span data-stu-id="eb041-201">If you have already got an App Service running, existing settings are selected.</span></span>  <span data-ttu-id="eb041-202">Você pode optar por criar um novo grupo de recursos e um plano de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="eb041-202">You can opt to create a new resource group and hosting plan.</span></span>  <span data-ttu-id="eb041-203">Quando estiver pronto, selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="eb041-203">When ready, select **Create**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish5.png" alt-text="Selecionar plano de hospedagem e assinatura":::

1. <span data-ttu-id="eb041-205">Na caixa **de diálogo Publicar,** a instância recém-criada foi selecionada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="eb041-205">In the **Publish** dialog, the newly created instance has been automatically selected.</span></span>  <span data-ttu-id="eb041-206">Quando estiver pronto, selecione **Concluir**.</span><span class="sxs-lookup"><span data-stu-id="eb041-206">When ready, select **Finish**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish6.png" alt-text="Selecione a nova instância.":::

1. <span data-ttu-id="eb041-208">Selecione o **ícone Editar** (lápis) ao lado de **Modo de** Implantação e selecione **Autocontiver**.</span><span class="sxs-lookup"><span data-stu-id="eb041-208">Select the **Edit** (pencil) icon next to **Deployment Mode**, and select **Self-contained**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish8.png" alt-text="Selecione o modo de implantação autoconstrutivo.":::

1. <span data-ttu-id="eb041-210">Selecionar **Publicar**.</span><span class="sxs-lookup"><span data-stu-id="eb041-210">Select **Publish**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/blazor-vs2019-publish7.png" alt-text="Publicar seu aplicativo no serviço de aplicativo":::

   <span data-ttu-id="eb041-212">Visual Studio implanta o aplicativo no Serviço de Aplicativo do Azure e o aplicativo Web é carregado no navegador.</span><span class="sxs-lookup"><span data-stu-id="eb041-212">Visual Studio deploys the app to your Azure App Service, and the web app loads in your browser.</span></span>  <span data-ttu-id="eb041-213">Adicione `/tab` ao final da URL para ver sua página.</span><span class="sxs-lookup"><span data-stu-id="eb041-213">Add `/tab` to the end of the URL to see your page.</span></span>

   <span data-ttu-id="eb041-214">O painel **Publicar propriedades** do projeto mostra a URL do site e outros detalhes.</span><span class="sxs-lookup"><span data-stu-id="eb041-214">The project properties **Publish** pane shows the site URL and other details.</span></span> <span data-ttu-id="eb041-215">Anote a URL do site.</span><span class="sxs-lookup"><span data-stu-id="eb041-215">Make a note of the site URL.</span></span>

## <a name="create-an-environment-for-your-app"></a><span data-ttu-id="eb041-216">Criar um ambiente para seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="eb041-216">Create an environment for your app</span></span>

<span data-ttu-id="eb041-217">O Portal do Desenvolvedor para Teams gerencia de onde as guias do seu aplicativo são carregadas com um **Environment**.</span><span class="sxs-lookup"><span data-stu-id="eb041-217">The Developer Portal for Teams manages where the tabs for your app are loaded from with an **Environment**.</span></span>  

<span data-ttu-id="eb041-218">**Para criar um ambiente:**</span><span class="sxs-lookup"><span data-stu-id="eb041-218">**To create an environment:**</span></span>

1. <span data-ttu-id="eb041-219">Abra o [Portal do Desenvolvedor para Teams](https://dev.teams.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="eb041-219">Open the [Developer Portal for Teams](https://dev.teams.microsoft.com).</span></span>  <span data-ttu-id="eb041-220">Entre com sua conta administrativa do M365.</span><span class="sxs-lookup"><span data-stu-id="eb041-220">Sign in with your M365 administrative account.</span></span>

1. <span data-ttu-id="eb041-221">Na barra lateral, selecione **Aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="eb041-221">From the sidebar, select **Apps**.</span></span>

1. <span data-ttu-id="eb041-222">Se você tiver apenas um aplicativo, ele será selecionado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="eb041-222">If you only have one app, it will be automatically selected.</span></span>  <span data-ttu-id="eb041-223">Caso não seja, selecione seu aplicativo na lista.</span><span class="sxs-lookup"><span data-stu-id="eb041-223">If not, select your app from the list.</span></span>

1. <span data-ttu-id="eb041-224">Selecione **Ambientes**.</span><span class="sxs-lookup"><span data-stu-id="eb041-224">Select **Environments**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments1.png" alt-text="Selecionar ambientes":::

1. <span data-ttu-id="eb041-226">Selecione **Criar seu primeiro ambiente**.</span><span class="sxs-lookup"><span data-stu-id="eb041-226">Select **Create your first environment**.</span></span>

1. <span data-ttu-id="eb041-227">Insira um nome para seu ambiente e selecione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="eb041-227">Enter a name for your environment and select **Add**.</span></span> <span data-ttu-id="eb041-228">Por exemplo, `_Production_`.</span><span class="sxs-lookup"><span data-stu-id="eb041-228">For example, `_Production_`.</span></span>

1. <span data-ttu-id="eb041-229">Selecione **Criar sua primeira variável de ambiente**.</span><span class="sxs-lookup"><span data-stu-id="eb041-229">Select **Create your first environment variable**.</span></span>

1. <span data-ttu-id="eb041-230">Insira `azure_app_url` para o **nome**.</span><span class="sxs-lookup"><span data-stu-id="eb041-230">Enter `azure_app_url` for the **Name**.</span></span>  <span data-ttu-id="eb041-231">Insira a URL do site do Azure sem `https://` o valor . </span><span class="sxs-lookup"><span data-stu-id="eb041-231">Enter your Azure site URL without the `https://` as the **Value**.</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments2.png" alt-text="Criar variável de ambiente":::

   <span data-ttu-id="eb041-233">Pressione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="eb041-233">Press **Add**.</span></span>

## <a name="update-the-app-manifest"></a><span data-ttu-id="eb041-234">Atualizar o manifesto do aplicativo</span><span class="sxs-lookup"><span data-stu-id="eb041-234">Update the app manifest</span></span>

<span data-ttu-id="eb041-235">O manifesto do aplicativo carrega a guia de uma `localhost` URL.</span><span class="sxs-lookup"><span data-stu-id="eb041-235">The app manifest loads the tab from a `localhost` URL.</span></span>  <span data-ttu-id="eb041-236">Nesta seção, você configurará o manifesto do aplicativo para carregar a guia da URL listada no ambiente que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="eb041-236">In this section, you will configure the app manifest to load the tab from the URL listed within the environment you just created.</span></span>

1. <span data-ttu-id="eb041-237">Na barra lateral, selecione **Informações básicas**.</span><span class="sxs-lookup"><span data-stu-id="eb041-237">From the sidebar, select **Basic information**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments3.png" alt-text="Selecionar informações básicas":::

1. <span data-ttu-id="eb041-239">Há vários locais dentro do manifesto que listam uma `locahost:XXXXX` como parte de uma URL.</span><span class="sxs-lookup"><span data-stu-id="eb041-239">There are several places within the manifest that list a `locahost:XXXXX` as part of a URL.</span></span>  <span data-ttu-id="eb041-240">Substitua todas as ocorrências `{{azure_app_url}}` por , incluindo as chaves.</span><span class="sxs-lookup"><span data-stu-id="eb041-240">Replace all occurrences with `{{azure_app_url}}`, including the curly braces.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments4.png" alt-text="Ajustar informações básicas para o ambiente":::

1. <span data-ttu-id="eb041-242">Quando estiver concluído, selecione **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="eb041-242">When complete, select **Save**.</span></span>

1. <span data-ttu-id="eb041-243">Na barra lateral, selecione **Recursos**.</span><span class="sxs-lookup"><span data-stu-id="eb041-243">From the sidebar, select **Capabilities**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments5.png" alt-text="Selecionar recursos":::

1. <span data-ttu-id="eb041-245">Selecione **Guia Pessoal**.</span><span class="sxs-lookup"><span data-stu-id="eb041-245">Select **Personal Tab**.</span></span>
1. <span data-ttu-id="eb041-246">Ao lado da **Guia Pessoal,** selecione os pontos tríplices e selecione **Editar**.</span><span class="sxs-lookup"><span data-stu-id="eb041-246">Next to the **Personal Tab**, select the triple dots, then select **Edit**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments6.png" alt-text="Editar configurações de tabulação pessoal":::

1. <span data-ttu-id="eb041-248">Substitua a URL pela variável de ambiente nos campos **Url de Conteúdo** e Url **do** Site.</span><span class="sxs-lookup"><span data-stu-id="eb041-248">Replace the URL with the environment variable within the **Content Url** and **Website Url** fields.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments7.png" alt-text="Editar URLs de tabulação pessoal":::

1. <span data-ttu-id="eb041-250">Selecione **Atualizar**.</span><span class="sxs-lookup"><span data-stu-id="eb041-250">Select **Update**.</span></span>

1. <span data-ttu-id="eb041-251">Selecione **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="eb041-251">Select **Save**.</span></span>

1. <span data-ttu-id="eb041-252">Na barra lateral, selecione **Single Sign-On**.</span><span class="sxs-lookup"><span data-stu-id="eb041-252">From the sidebar, select **Single Sign-On**.</span></span>

1. <span data-ttu-id="eb041-253">Substitua o `localhost` URI de **ID do aplicativo** por `{{azure_app_url}}` .</span><span class="sxs-lookup"><span data-stu-id="eb041-253">Replace the `localhost` within the **Application ID URI** with `{{azure_app_url}}`.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments8.png" alt-text="Editar URI de ID de aplicativo de login único":::

1. <span data-ttu-id="eb041-255">Selecione **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="eb041-255">Select **Save**.</span></span>

1. <span data-ttu-id="eb041-256">Na barra lateral, selecione **Domínios**.</span><span class="sxs-lookup"><span data-stu-id="eb041-256">From the sidebar, select **Domains**.</span></span>

1. <span data-ttu-id="eb041-257">Selecione **Adicionar um domínio**.</span><span class="sxs-lookup"><span data-stu-id="eb041-257">Select **Add a domain**.</span></span>

1. <span data-ttu-id="eb041-258">Se `{{azure_app_url}}` não estiver listado como um domínio válido, adicione-o como um domínio válido e selecione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="eb041-258">If `{{azure_app_url}}` is not listed as a valid domain, add it as a valid domain, then select **Add**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/devcenter-environments9.png" alt-text="Adicionar um domínio":::

   <span data-ttu-id="eb041-260">Agora você pode usar a **opção Visualizar Teams** na parte superior da página para iniciar seu aplicativo dentro Teams.</span><span class="sxs-lookup"><span data-stu-id="eb041-260">You can now use the **Preview in Teams** option at the top of the page to launch your app within Teams.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb041-261">Confira também</span><span class="sxs-lookup"><span data-stu-id="eb041-261">See also</span></span>

* [<span data-ttu-id="eb041-262">Visão geral dos tutoriais</span><span class="sxs-lookup"><span data-stu-id="eb041-262">Tutorials Overview</span></span>](code-samples.md)
* [<span data-ttu-id="eb041-263">Criar um programa bot de conversação</span><span class="sxs-lookup"><span data-stu-id="eb041-263">Create a conversational bot app</span></span>](first-app-bot.md)
* [<span data-ttu-id="eb041-264">Criar uma extensão de mensagem</span><span class="sxs-lookup"><span data-stu-id="eb041-264">Create a messaging extension</span></span>](first-message-extension.md)
* [<span data-ttu-id="eb041-265">Exemplos de código</span><span class="sxs-lookup"><span data-stu-id="eb041-265">Code Samples</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples)
