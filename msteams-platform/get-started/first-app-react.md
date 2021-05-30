---
title: 'Iniciar: Compilar seu primeiro aplicativo do Teams com React'
author: adrianhall
description: Crie rapidamente um aplicativo do Microsoft Teams que exibe uma mensagem "Olá, Mundo!" usando o Kit de ferramentas do Microsoft Teams e o React.
ms.author: adhal
ms.date: 05/18/2021
ms.topic: quickstart
ms.openlocfilehash: 4560e332834fec7b681a6b2babf3e881b5e472f7
ms.sourcegitcommit: 2c8b35899dd845acd66f1f927e40d99523c29a91
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/28/2021
ms.locfileid: "52698128"
---
# <a name="build-and-run-your-first-microsoft-teams-app-with-react"></a><span data-ttu-id="eb3a7-104">Compilar e executar seu primeiro aplicativo do Microsoft Teams com React</span><span class="sxs-lookup"><span data-stu-id="eb3a7-104">Build and run your first Microsoft Teams app with React</span></span>

<span data-ttu-id="eb3a7-105">Neste tutorial, você criará um novo aplicativo Microsoft Teams no React que implementa um aplicativo pessoal simples para extrair informações do Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-105">In this tutorial, you will create a new Microsoft Teams app in React that implements a simple personal app to pull information from the Microsoft Graph.</span></span> <span data-ttu-id="eb3a7-106">(Um *aplicativo pessoal* inclui um conjunto de guias com escopo para uso individual.) Durante o tutorial, você aprenderá sobre a estrutura de um aplicativo do Teams, como executar um aplicativo localmente e como implantar o aplicativo no Azure.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-106">(A *personal app* includes a set of tabs scoped for individual use.) During the tutorial, you will learn about the structure of a Teams app, how to run an app locally, and how to deploy the app to Azure.</span></span>

<span data-ttu-id="eb3a7-107">O aplicativo que é compilado exibe informações básicas para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-107">The app that is built displays basic user information for the current user.</span></span>  <span data-ttu-id="eb3a7-108">Quando a permissão é concedida, o aplicativo se conectará ao Microsoft Graph como o usuário atual para obter o perfil completo.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-108">When permission is granted, the app will connect to the Microsoft Graph as the current user to get the complete profile.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="eb3a7-109">Antes de você começar</span><span class="sxs-lookup"><span data-stu-id="eb3a7-109">Before you begin</span></span>

<span data-ttu-id="eb3a7-110">Certifique-se de que o seu ambiente de desenvolvimento esteja configurado, instalando os [pré-requisitos](prerequisites.md)</span><span class="sxs-lookup"><span data-stu-id="eb3a7-110">Make sure your development environment is set up by installing the [prerequisites](prerequisites.md)</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="eb3a7-111">Instalar pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="eb3a7-111">Install prerequisites</span></span>](prerequisites.md)

## <a name="create-your-project"></a><span data-ttu-id="eb3a7-112">Criar seu projeto</span><span class="sxs-lookup"><span data-stu-id="eb3a7-112">Create your project</span></span>

<span data-ttu-id="eb3a7-113">Use o Kit de ferramentas do Teams para criar o seu primeiro projeto:</span><span class="sxs-lookup"><span data-stu-id="eb3a7-113">Use the Teams Toolkit to create your first project:</span></span>

# <a name="visual-studio-code"></a>[<span data-ttu-id="eb3a7-114">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="eb3a7-114">Visual Studio Code</span></span>](#tab/vscode)

1. <span data-ttu-id="eb3a7-115">Abra o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-115">Open Visual Studio code.</span></span>
1. <span data-ttu-id="eb3a7-116">Abra o Kit de ferramentas do Teams selecionando o ícone do Teams na barra lateral:</span><span class="sxs-lookup"><span data-stu-id="eb3a7-116">Open the Teams Toolkit by selecting the Teams icon in the sidebar:</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="O ícone do Teams na barra lateral do Visual Studio Code":::

1. <span data-ttu-id="eb3a7-118">Selecione **Criar Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-118">Select **Create New Project**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Localização do link de Criação de Novo Projeto na barra lateral do Kit de ferramentas do Teams.":::

1. <span data-ttu-id="eb3a7-120">Selecione **Criar um novo aplicativo do Teams**.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-120">Select **Create a new Teams app**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Início do assistente para Criar Novo Projeto":::

1. <span data-ttu-id="eb3a7-122">Na etapa **Selecionar capacidades**, a capacidade da **Guia** já será selecionada.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-122">On the **Select capabilities** step, the **Tab** capability will already be selected.</span></span>  <span data-ttu-id="eb3a7-123">Pressione **OK**.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-123">Press **OK**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-capabilities.png" alt-text="Captura de tela mostrando como adicionar capacidades ao seu novo aplicativo.":::

1. <span data-ttu-id="eb3a7-125">Na etapa **Tipo de hospedagem front-end**, selecione **Azure**.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-125">On the **Frontend hosting type** step, select **Azure**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-hosting.png" alt-text="Captura de tela mostrando como selecionar a hospedagem para seu novo aplicativo.":::

1. <span data-ttu-id="eb3a7-127">Na etapa **Recursos em nuvem**, pressione **OK**.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-127">On the **Cloud resources** step, press **OK**.</span></span>  <span data-ttu-id="eb3a7-128">Não precisamos de recursos adicionais em nuvem para este tutorial.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-128">We do not need additional cloud resources for this tutorial.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-cloud-resources.png" alt-text="Captura de tela mostrando como adicionar recursos em nuvem ao seu novo aplicativo.":::

1. <span data-ttu-id="eb3a7-130">Na etapa **Linguagem de Programação**, selecione **JavaScript**.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-130">On the **Programming Language** step, select **JavaScript**.</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-programming-languages.png" alt-text="Captura de tela mostrando como selecionar a linguagem de programação.":::

1. <span data-ttu-id="eb3a7-132">Selecione uma pasta do espaço de trabalho.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-132">Select a workspace folder.</span></span>  <span data-ttu-id="eb3a7-133">Uma pasta será criada dentro de sua pasta do espaço de trabalho para o projeto que você está criando.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-133">A folder will be created within your workspace folder for the project you are creating.</span></span>

1. <span data-ttu-id="eb3a7-134">Insira um nome adequado para seu aplicativo, como `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-134">Enter a suitable name for your app, like `helloworld`.</span></span>  <span data-ttu-id="eb3a7-135">O nome do aplicativo deve consistir apenas de caracteres alfanuméricos.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-135">The name of the app must consist only of alphanumeric characters.</span></span>  <span data-ttu-id="eb3a7-136">Pressione **Inserir** para continuar.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-136">Press **Enter** to continue.</span></span>

<span data-ttu-id="eb3a7-137">O seu aplicativo do Teams será criado em alguns segundos.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-137">Your Teams app will be created within a few seconds.</span></span>

# <a name="command-line"></a>[<span data-ttu-id="eb3a7-138">Linha de comando</span><span class="sxs-lookup"><span data-stu-id="eb3a7-138">Command line</span></span>](#tab/cli)

<span data-ttu-id="eb3a7-139">Use a CLI `teamsfx` para criar o seu primeiro projeto.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-139">Use the `teamsfx` CLI to create your first project.</span></span>  <span data-ttu-id="eb3a7-140">Inicie pela pasta onde deseja criar a pasta do projeto.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-140">Start from the folder where you want to create the project folder.</span></span>

``` bash
teamsfx new
```

<span data-ttu-id="eb3a7-141">A CLI lhe guiará através de algumas perguntas para criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-141">The CLI walks through some questions to create the project.</span></span>  <span data-ttu-id="eb3a7-142">Cada pergunta lhe dirá como respondê-la (por exemplo, usar as teclas de seta para selecionar uma opção).</span><span class="sxs-lookup"><span data-stu-id="eb3a7-142">Each question will tell you how to answer it (for example, to use arrow keys to select an option).</span></span>  <span data-ttu-id="eb3a7-143">Depois de responder à pergunta, confirme sua escolha pressionando **Inserir**.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-143">When you have answered the question, confirm your choice by pressing **Enter**.</span></span>

1. <span data-ttu-id="eb3a7-144">Selecione **Criar um novo aplicativo do Teams**.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-144">Select **Create a new Teams app**.</span></span>
1. <span data-ttu-id="eb3a7-145">Escolha a capacidade **Guia**.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-145">Choose the **Tab** capability.</span></span>
1. <span data-ttu-id="eb3a7-146">Selecione **Azure** como hospedagem front-end.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-146">Select **Azure** frontend hosting.</span></span>
1. <span data-ttu-id="eb3a7-147">Não selecione nenhum recurso em nuvem.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-147">Do not select any cloud resources.</span></span>
1. <span data-ttu-id="eb3a7-148">Selecione **JavaScript** como linguagem de programação.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-148">Select **JavaScript** as the programming language.</span></span>
1. <span data-ttu-id="eb3a7-149">Pressione **Inserir** para selecionar a pasta padrão do espaço de trabalho.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-149">Press **Enter** to select the default workspace folder.</span></span>
1. <span data-ttu-id="eb3a7-150">Insira um nome adequado para seu aplicativo, como `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-150">Enter a suitable name for your app, like `helloworld`.</span></span>  <span data-ttu-id="eb3a7-151">O nome do aplicativo deve consistir apenas de caracteres alfanuméricos.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-151">The name of the app must consist only of alphanumeric characters.</span></span>

<span data-ttu-id="eb3a7-152">Assim que todas as perguntas forem respondidas, o seu projeto será criado.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-152">Once all the questions have been answered, your project will be created.</span></span>

---

## <a name="take-a-tour-of-the-source-code"></a><span data-ttu-id="eb3a7-153">Faça um tour pelo código-fonte</span><span class="sxs-lookup"><span data-stu-id="eb3a7-153">Take a tour of the source code</span></span>

<span data-ttu-id="eb3a7-154">Se desejar pular esta seção por enquanto, você pode [executar seu aplicativo localmente](#run-your-app-locally).</span><span class="sxs-lookup"><span data-stu-id="eb3a7-154">If you wish to skip this section for now, you can [run your app locally](#run-your-app-locally).</span></span>

<span data-ttu-id="eb3a7-155">Uma vez que o Kit de ferramentas do Teams configura seu projeto, você tem os componentes para compilar um aplicativo pessoal básico para o Teams.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-155">Once the Teams Toolkit configures your project, you have the components to build a basic personal app for Teams.</span></span> <span data-ttu-id="eb3a7-156">Os diretórios e arquivos do projeto são exibidos na área do Explorador do Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-156">The project directories and files display in the Explorer area of Visual Studio Code.</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/react-app-project.png" alt-text="Captura de tela mostrando arquivos de projeto do aplicativo para um aplicativo pessoal no Visual Studio Code.":::

<span data-ttu-id="eb3a7-158">O Kit de ferramentas cria automaticamente scaffolding para você no diretório do projeto com base nas capacidades que você adicionou durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-158">The Toolkit automatically creates scaffolding for you in the project directory based on the capabilities you added during setup.</span></span> <span data-ttu-id="eb3a7-159">O Kit de ferramentas do Teams mantém o estado de seu aplicativo no diretório `.fx`.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-159">The Teams Toolkit maintains its state for your app in the `.fx` directory.</span></span>  <span data-ttu-id="eb3a7-160">Entre outros itens deste diretório:</span><span class="sxs-lookup"><span data-stu-id="eb3a7-160">Among other items in this directory:</span></span>

- <span data-ttu-id="eb3a7-161">Os ícones do aplicativo são armazenados como arquivos PNG em `color.png` e `outline.png`.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-161">The app icons are stored as PNG files in `color.png` and `outline.png`.</span></span>
- <span data-ttu-id="eb3a7-162">O manifesto do aplicativo para publicação no Portal do Desenvolvedor do Teams é armazenado em `manifest.source.json`.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-162">The app manifest for publishing to the Developer Portal for Teams is stored in `manifest.source.json`.</span></span>
- <span data-ttu-id="eb3a7-163">As configurações que você escolheu ao criar o projeto são armazenadas em `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-163">The settings you chose when creating the project are stored in `settings.json`.</span></span>

<span data-ttu-id="eb3a7-164">Como você selecionou a capacidade de guias durante a instalação, o Kit de ferramentas do Teams reúne todo o código necessário para uma guia básica no diretório `tabs`.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-164">Since you selected the tab capability during setup, the Teams Toolkit scaffolds all the necessary code for a basic tab in the `tabs` directory.</span></span> <span data-ttu-id="eb3a7-165">Dentro deste diretório há vários arquivos importantes:</span><span class="sxs-lookup"><span data-stu-id="eb3a7-165">Within this directory there are several important files:</span></span>

- <span data-ttu-id="eb3a7-166">`tabs/src/index.jsx` é o ponto de entrada do front-end do aplicativo, onde o componente principal `App` é renderizado com `ReactDOM.render()`.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-166">`tabs/src/index.jsx` is the front-end app's entry point, where the main `App` component is rendered with `ReactDOM.render()`.</span></span>
- <span data-ttu-id="eb3a7-167">`tabs/src/components/App.jsx` lida com o roteamento de URLs em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-167">`tabs/src/components/App.jsx` handles URL routing in your app.</span></span> <span data-ttu-id="eb3a7-168">Ele chama o [Microsoft Teams JavaScript client SDK](../tabs/how-to/using-teams-client-sdk.md) para estabelecer a comunicação entre seu aplicativo e o Teams.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-168">It calls the [Microsoft Teams JavaScript client SDK](../tabs/how-to/using-teams-client-sdk.md) to establish communication between your app and Teams.</span></span>
- <span data-ttu-id="eb3a7-169">`tabs/src/components/Tab.jsx` contém o código para implementar a IU do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-169">`tabs/src/components/Tab.jsx` contains the code to implement the UI of your app.</span></span>
- <span data-ttu-id="eb3a7-170">`tabs/src/components/TabConfig.jsx` contém o código para implementar a IU que configura seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-170">`tabs/src/components/TabConfig.jsx` contains the code to implement the UI that configures your app.</span></span>

<span data-ttu-id="eb3a7-171">Várias guias são exigidas pelo runtime do Teams, incluindo o aviso de privacidade, os termos de uso e as guias de configuração.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-171">Several tabs are required by the Teams runtime, including the privacy notice, terms of use, and configuration tabs.</span></span>  <span data-ttu-id="eb3a7-172">O código para o aviso de privacidade e os termos de uso estão localizados no mesmo diretório.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-172">The code for the privacy notice and terms of use are located in the same directory.</span></span>

<span data-ttu-id="eb3a7-173">Quando se adiciona a funcionalidade da nuvem, diretórios adicionais são adicionados ao projeto.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-173">When you add cloud functionality, additional directories are added to the project.</span></span>  <span data-ttu-id="eb3a7-174">Principalmente, o diretório `api` retém o código para qualquer Azure Functions que você escreva.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-174">Most notably, the `api` directory holds the code to any Azure Functions you write.</span></span>

## <a name="run-your-app-locally"></a><span data-ttu-id="eb3a7-175">Executar seu aplicativo localmente</span><span class="sxs-lookup"><span data-stu-id="eb3a7-175">Run your app locally</span></span>

<span data-ttu-id="eb3a7-176">O Kit de ferramentas do Teams permite que você execute seu aplicativo localmente.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-176">Teams Toolkit allows you to run your app locally.</span></span>  <span data-ttu-id="eb3a7-177">Isto consiste de várias partes que são necessárias para fornecer a infraestrutura correta que o Teams espera:</span><span class="sxs-lookup"><span data-stu-id="eb3a7-177">This consists of several parts that are necessary to provide the correct infrastructure that Teams expects:</span></span>

- <span data-ttu-id="eb3a7-178">Um aplicativo está registrado no Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-178">An application is registered with Azure Active Directory.</span></span>  <span data-ttu-id="eb3a7-179">Este aplicativo tem permissões associadas ao local de onde o aplicativo é carregado e a quaisquer recursos de back-end que ele acesse.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-179">This application has permissions associated with the location that the app is loaded from and any backend resources it accesses.</span></span>
- <span data-ttu-id="eb3a7-180">Uma API da Web é hospedada para auxiliar nas tarefas de autenticação, atuando como um proxy entre o aplicativo e o Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-180">A web API is hosted to assist with authentication tasks, acting as a proxy between the app and Azure Active Directory.</span></span>  <span data-ttu-id="eb3a7-181">Isto é executado pelo Azure Functions Core Tools.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-181">This is run by Azure Functions Core Tools.</span></span>  <span data-ttu-id="eb3a7-182">Ele pode ser acessado na URL `https://localhost:5000`.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-182">It can be accessed at the URL `https://localhost:5000`.</span></span>
- <span data-ttu-id="eb3a7-183">Os recursos HTML, CSS e JavaScript que compõem o front-end do aplicativo são hospedados em um serviço local.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-183">The HTML, CSS, and JavaScript resources that make up the front end of the app are hosted on a local service.</span></span> <span data-ttu-id="eb3a7-184">Ele pode ser acessado em `https://localhost:3000`.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-184">It can be accessed at `https://localhost:3000`.</span></span>
- <span data-ttu-id="eb3a7-185">Um manifesto de aplicativo é gerado e existe no Portal de Desenvolvedor do Teams.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-185">An app manifest is generated and exists in the Developer Portal for Teams.</span></span>  <span data-ttu-id="eb3a7-186">O Teams usa o manifesto do aplicativo para dizer aos clientes conectados de onde carregar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-186">Teams uses the app manifest to tell connected clients where to load the app from.</span></span>

<span data-ttu-id="eb3a7-187">Depois de fazer isso, o aplicativo pode ser carregado dentro do cliente do Teams.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-187">Once this is done, the app can be loaded within the Teams client.</span></span>  <span data-ttu-id="eb3a7-188">Usamos o cliente Web do Teams para que possamos ver o código HTML, CSS e JavaScript dentro de um ambiente de desenvolvimento web padrão.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-188">We use the Teams web client so that we can see the HTML, CSS, and JavaScript code within a standard web development environment.</span></span>

[!INCLUDE [Adjust your browser launch settings](~/includes/get-started/browser-private-launch.md)]

### <a name="build-and-run-your-app-locally-in-visual-studio-code"></a><span data-ttu-id="eb3a7-189">Compilar e executar seu aplicativo localmente em Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="eb3a7-189">Build and run your app locally in Visual Studio Code</span></span>

<span data-ttu-id="eb3a7-190">Para compilar e executar seu aplicativo localmente:</span><span class="sxs-lookup"><span data-stu-id="eb3a7-190">To build and run your app locally:</span></span>

1. <span data-ttu-id="eb3a7-191">No Visual Studio Code, pressione **F5** para executar seu aplicativo no modo de depuração.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-191">From Visual Studio Code, press **F5** to run your application in debug mode.</span></span>

   > <span data-ttu-id="eb3a7-192">Quando você executa o aplicativo pela primeira vez, todas as dependências são baixadas e o aplicativo é compilado.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-192">When you run the app for the first time, all dependencies are downloaded and the app is built.</span></span>  <span data-ttu-id="eb3a7-193">Uma janela do navegador é aberta automaticamente quando a compilação é concluída.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-193">A browser window automatically opens when the build is complete.</span></span>  <span data-ttu-id="eb3a7-194">Isto pode levar de 3 a 5 minutos para ser concluído.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-194">This can take 3-5 minutes to complete.</span></span>

   <span data-ttu-id="eb3a7-195">O Kit de ferramentas lhe solicitará a instalação de um certificado local, se necessário.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-195">The Toolkit will prompt you to install a local certificate if needed.</span></span> <span data-ttu-id="eb3a7-196">Esse certificado permite que o Teams carregue seu aplicativo a partir de `https://localhost`.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-196">This certificate allows Teams to load your application from `https://localhost`.</span></span> <span data-ttu-id="eb3a7-197">Selecione Sim quando aparecer a seguinte caixa de diálogo:</span><span class="sxs-lookup"><span data-stu-id="eb3a7-197">Select yes when the following dialog appears:</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/ssl-prompt.png" alt-text="Captura de tela mostrando como a solicitação de instalação de um certificado SSL para permitir que o Teams carregue seu aplicativo a partir do localhost.":::

1. <span data-ttu-id="eb3a7-199">O seu navegador da web é iniciado para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-199">Your web browser is started to run the application.</span></span> <span data-ttu-id="eb3a7-200">Se for solicitado a abrir o Microsoft Teams, selecione Cancelar para permanecer no navegador.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-200">If prompted to open Microsoft Teams, select Cancel to remain within the browser.</span></span> <span data-ttu-id="eb3a7-201">Quando solicitado, selecione **Usar o aplicativo da web em vez disso**.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-201">When prompted, select **Use the web app instead**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/launch-web-browser-and-pick-webapp.png" alt-text="Captura de tela mostrando como escolher a versão da web das equipes quando lançadas":::

1. <span data-ttu-id="eb3a7-203">Você pode ser solicitado a entrar.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-203">You may be prompted to sign in.</span></span>  <span data-ttu-id="eb3a7-204">Em caso afirmativo, entre com sua conta M365.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-204">If so, sign in with your M365 account.</span></span>
1. <span data-ttu-id="eb3a7-205">Quando solicitado a instalar o aplicativo no Teams, pressione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-205">When prompted to install the app onto Teams, press **Add**.</span></span>

<span data-ttu-id="eb3a7-206">Seu aplicativo agora será exibido:</span><span class="sxs-lookup"><span data-stu-id="eb3a7-206">Your app will now be displayed:</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/react-finished-app.png" alt-text="Captura de tela do aplicativo concluído":::

<span data-ttu-id="eb3a7-208">Você pode fazer atividades normais de depuração como se isso fosse qualquer outro aplicativo Web (como a configuração de pontos de interrupção).</span><span class="sxs-lookup"><span data-stu-id="eb3a7-208">You can do normal debugging activities as if this were any other web application (such as setting breakpoints).</span></span> <span data-ttu-id="eb3a7-209">O aplicativo dá suporte à recarga dinâmica.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-209">The app supports hot reloading.</span></span>  <span data-ttu-id="eb3a7-210">Se você alterar qualquer arquivo dentro do projeto, a página será recarregada.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-210">If you change any file within the project, the page will be reloaded.</span></span>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="eb3a7-211">Saiba o que acontece quando você executa seu aplicativo localmente no depurador.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-211">Learn what happens when you run your app locally in the debugger.</span></span></summary>

<span data-ttu-id="eb3a7-212">Quando você pressionou F5, o Kit de ferramentas do Teams:</span><span class="sxs-lookup"><span data-stu-id="eb3a7-212">When you pressed F5, the Teams Toolkit:</span></span>

1. <span data-ttu-id="eb3a7-213">Registrou seu aplicativo no Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-213">Registered your application with Azure Active Directory.</span></span>
1. <span data-ttu-id="eb3a7-214">*Fez o sideload* de seu aplicativo no Teams.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-214">*Sideloaded* your app in Teams.</span></span>
1. <span data-ttu-id="eb3a7-215">Iniciou a execução do back-end de seu aplicativo localmente usando o [Azure Functions Core Tools](/azure/azure-functions/functions-run-local?#start).</span><span class="sxs-lookup"><span data-stu-id="eb3a7-215">Started your application backend running locally using [Azure Function Core Tools](/azure/azure-functions/functions-run-local?#start).</span></span>
1. <span data-ttu-id="eb3a7-216">Iniciou a hospedagem local do front-end de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-216">Started your application front-end hosted locally.</span></span>
1. <span data-ttu-id="eb3a7-217">Iniciou o Microsoft Teams em um navegador da Web com um comando para instruir o Teams a fazer o sideload a partir de `https://localhost:3000/tab` (a URL está registrada dentro do manifesto do aplicativo).</span><span class="sxs-lookup"><span data-stu-id="eb3a7-217">Started Microsoft Teams in a web browser with a command to instruct Teams to side load the application from `https://localhost:3000/tab` (the URL is registered inside the application manifest).</span></span>

</details>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="eb3a7-218">Saiba como solucionar problemas comuns ao executar seu aplicativo localmente.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-218">Learn how to troubleshoot common issues when running your app locally.</span></span></summary>

<span data-ttu-id="eb3a7-219">Para executar com êxito seu aplicativo no Teams, você deve ter uma conta do Teams que permite o sideload de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-219">To successfully run your app in Teams, you must have a Teams account that allows app sideloading.</span></span> <span data-ttu-id="eb3a7-220">Para obter mais informações sobre abertura de conta, confira [pré-requisitos](prerequisites.md#enable-sideloading).</span><span class="sxs-lookup"><span data-stu-id="eb3a7-220">For more information on account opening, see [prerequisites](prerequisites.md#enable-sideloading).</span></span>

</details>

[!INCLUDE [Provision and Deploy your app on Azure](~/includes/get-started/azure-provisioning-instructions.md)]

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="eb3a7-221">Saiba o que acontece quando você implanta o seu aplicativo no Azure</span><span class="sxs-lookup"><span data-stu-id="eb3a7-221">Learn what happens when you deployed your app to Azure</span></span></summary>

<span data-ttu-id="eb3a7-222">Antes da implantação, o aplicativo era executado localmente:</span><span class="sxs-lookup"><span data-stu-id="eb3a7-222">Before deployment, the application has been running locally:</span></span>

1. <span data-ttu-id="eb3a7-223">O back-end é executado usando o _Azure Functions Core Tools_.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-223">The backend runs using _Azure Functions Core Tools_.</span></span>
1. <span data-ttu-id="eb3a7-224">O ponto de extremidade HTTP do aplicativo, onde o Microsoft Teams carrega o aplicativo, é executado localmente.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-224">The application HTTP endpoint, where Microsoft Teams loads the application, runs locally.</span></span>

<span data-ttu-id="eb3a7-225">A implantação envolve o provisionamento de recursos em uma assinatura ativa do Azure e a implantação (upload) do código de back-end e front-end do aplicativo para o Azure.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-225">Deployment involves provisioning resources on an active Azure subscription and deploying (uploading) the backend and frontend code for the application to Azure.</span></span>

1. <span data-ttu-id="eb3a7-226">O back-end (se configurado) usa uma variedade de serviços do Azure, incluindo o Serviço de Aplicativo do Azure e o Armazenamento do Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-226">The backend (if configured) uses a variety of Azure services, including Azure App Service and Azure Storage.</span></span>
1. <span data-ttu-id="eb3a7-227">O front-end do aplicativo será implantado em uma conta de Armazenamento do Microsoft Azure configurada para hospedagem Web estática.</span><span class="sxs-lookup"><span data-stu-id="eb3a7-227">The frontend application will be deployed to an Azure Storage account configured for static web hosting.</span></span>

</details>

## <a name="next-steps"></a><span data-ttu-id="eb3a7-228">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="eb3a7-228">Next steps</span></span>

<span data-ttu-id="eb3a7-229">Saiba mais sobre outros métodos para criar aplicativos do Teams:</span><span class="sxs-lookup"><span data-stu-id="eb3a7-229">Learn about other methods for creating Teams apps:</span></span>

- [<span data-ttu-id="eb3a7-230">Criar um aplicativo do Teams com o Blazor</span><span class="sxs-lookup"><span data-stu-id="eb3a7-230">Create a Teams app with Blazor</span></span>](first-app-blazor.md)
- <span data-ttu-id="eb3a7-231">[Criar um aplicativo do Teams como uma Web Part do SharePoint](first-app-spfx.md) (Azure não é necessário)</span><span class="sxs-lookup"><span data-stu-id="eb3a7-231">[Create a Teams app as a SharePoint Web Part](first-app-spfx.md) (Azure not required)</span></span>
- [<span data-ttu-id="eb3a7-232">Criar um programa bot de conversação</span><span class="sxs-lookup"><span data-stu-id="eb3a7-232">Create a conversational bot app</span></span>](first-app-bot.md)
- [<span data-ttu-id="eb3a7-233">Criar uma extensão de mensagem</span><span class="sxs-lookup"><span data-stu-id="eb3a7-233">Create a messaging extension</span></span>](first-message-extension.md)
