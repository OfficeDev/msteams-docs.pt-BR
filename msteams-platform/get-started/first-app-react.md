---
title: 'Iniciar: Compilar seu primeiro aplicativo do Teams com React'
author: adrianhall
description: Crie rapidamente um aplicativo do Microsoft Teams que exibe uma mensagem "Olá, Mundo!" usando o Kit de ferramentas do Microsoft Teams e o React.
ms.author: adhal
ms.date: 05/27/2021
ms.topic: quickstart
ms.openlocfilehash: c257bcd805a6b7b38ab657cb31cad961df1c4704
ms.sourcegitcommit: 9d63611974ba8a7e7f19ceea35e50189a2e90434
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2021
ms.locfileid: "53254318"
---
# <a name="build-and-run-your-first-microsoft-teams-app-with-react"></a><span data-ttu-id="fbac0-104">Compilar e executar seu primeiro aplicativo do Microsoft Teams com React</span><span class="sxs-lookup"><span data-stu-id="fbac0-104">Build and run your first Microsoft Teams app with React</span></span>

<span data-ttu-id="fbac0-105">Neste tutorial, você aprenderá a criar um novo aplicativo Microsoft Teams no React que implementa um aplicativo pessoal simples para obter informações do microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="fbac0-105">In this tutorial, you will learn how to create a new Microsoft Teams app in React that implements a simple personal app to pull information from the Microsoft Graph.</span></span> <span data-ttu-id="fbac0-106">Por exemplo, um *aplicativo pessoal* inclui um conjunto de guias para uso individual.</span><span class="sxs-lookup"><span data-stu-id="fbac0-106">For example, a *personal app* includes a set of tabs for individual use.</span></span> <span data-ttu-id="fbac0-107">Durante o tutorial, você aprenderá sobre a estrutura de um aplicativo Teams, como executar um aplicativo localmente e como implantar o aplicativo no Azure.</span><span class="sxs-lookup"><span data-stu-id="fbac0-107">During the tutorial, you will learn about the structure of a Teams app, how to run an app locally, and how to deploy the app to Azure.</span></span>

<span data-ttu-id="fbac0-108">O aplicativo que é compilado exibe informações básicas para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="fbac0-108">The app that is built displays basic user information for the current user.</span></span> <span data-ttu-id="fbac0-109">Quando a permissão é concedida, o aplicativo se conectará ao Microsoft Graph como o usuário atual para obter o perfil completo.</span><span class="sxs-lookup"><span data-stu-id="fbac0-109">When permission is granted, the app will connect to the Microsoft Graph as the current user to get the complete profile.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="fbac0-110">Antes de você começar</span><span class="sxs-lookup"><span data-stu-id="fbac0-110">Before you begin</span></span>

<span data-ttu-id="fbac0-111">Certifique-se de que seu ambiente de desenvolvimento está definido instalando os pré-requisitos.</span><span class="sxs-lookup"><span data-stu-id="fbac0-111">Make sure your development environment is set up by installing the prerequisites.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fbac0-112">Instalar pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="fbac0-112">Install prerequisites</span></span>](prerequisites.md)

## <a name="create-your-project"></a><span data-ttu-id="fbac0-113">Criar seu projeto</span><span class="sxs-lookup"><span data-stu-id="fbac0-113">Create your project</span></span>

<span data-ttu-id="fbac0-114">Use o Kit de ferramentas do Teams para criar o seu primeiro projeto:</span><span class="sxs-lookup"><span data-stu-id="fbac0-114">Use the Teams Toolkit to create your first project:</span></span>

# <a name="visual-studio-code"></a>[<span data-ttu-id="fbac0-115">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="fbac0-115">Visual Studio Code</span></span>](#tab/vscode)

1. <span data-ttu-id="fbac0-116">Abra o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="fbac0-116">Open Visual Studio code.</span></span>
1. <span data-ttu-id="fbac0-117">Abra o Teams Toolkit e selecione o ícone Teams na barra lateral:</span><span class="sxs-lookup"><span data-stu-id="fbac0-117">Open the Teams Toolkit and select the Teams icon in the sidebar:</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="O ícone do Teams na barra lateral do Visual Studio Code":::

1. <span data-ttu-id="fbac0-119">Selecione **Criar Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="fbac0-119">Select **Create New Project**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Localização do link de Criação de Novo Projeto na barra lateral do Kit de ferramentas do Teams.":::

1. <span data-ttu-id="fbac0-121">Selecione **Criar um novo aplicativo do Teams**.</span><span class="sxs-lookup"><span data-stu-id="fbac0-121">Select **Create a new Teams app**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Início do assistente para Criar Novo Projeto":::

1. <span data-ttu-id="fbac0-123">Na seção **Selecionar recursos,** varify that **Tab** is selected and select **OK**.</span><span class="sxs-lookup"><span data-stu-id="fbac0-123">In the **Select capabilities** section, varify that **Tab** is selected and select **OK**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-capabilities.png" alt-text="Captura de tela mostrando como adicionar capacidades ao seu novo aplicativo.":::

1. <span data-ttu-id="fbac0-125">Na seção **Tipo de hospedagem frontend,** selecione **Azure**.</span><span class="sxs-lookup"><span data-stu-id="fbac0-125">In the **Frontend hosting type** section, select **Azure**.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-hosting.png" alt-text="Captura de tela mostrando como selecionar a hospedagem para seu novo aplicativo.":::

1. <span data-ttu-id="fbac0-127">Na seção **Recursos de nuvem,** selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="fbac0-127">In the **Cloud resources** section, select **OK**.</span></span>  <span data-ttu-id="fbac0-128">Não precisamos de recursos adicionais em nuvem para este tutorial.</span><span class="sxs-lookup"><span data-stu-id="fbac0-128">We do not need additional cloud resources for this tutorial.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-cloud-resources.png" alt-text="Captura de tela mostrando como adicionar recursos em nuvem ao seu novo aplicativo.":::

1. <span data-ttu-id="fbac0-130">Na seção **Linguagem de Programação,** selecione **JavaScript**.</span><span class="sxs-lookup"><span data-stu-id="fbac0-130">In the **Programming Language** section, select **JavaScript**.</span></span>

    :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-programming-languages.png" alt-text="Captura de tela mostrando como selecionar a linguagem de programação.":::

1. <span data-ttu-id="fbac0-132">Selecione uma pasta do espaço de trabalho.</span><span class="sxs-lookup"><span data-stu-id="fbac0-132">Select a workspace folder.</span></span> <span data-ttu-id="fbac0-133">Uma pasta é criada em sua pasta de espaço de trabalho para o projeto que você está criando.</span><span class="sxs-lookup"><span data-stu-id="fbac0-133">A folder is created within your workspace folder for the project you are creating.</span></span>

1. <span data-ttu-id="fbac0-134">Insira um nome adequado para seu aplicativo, como `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="fbac0-134">Enter a suitable name for your app, like `helloworld`.</span></span> <span data-ttu-id="fbac0-135">O nome do aplicativo deve consistir apenas de caracteres alfanuméricos.</span><span class="sxs-lookup"><span data-stu-id="fbac0-135">The name of the app must consist only of alphanumeric characters.</span></span>  <span data-ttu-id="fbac0-136">Pressione **Inserir** para continuar.</span><span class="sxs-lookup"><span data-stu-id="fbac0-136">Press **Enter** to continue.</span></span>

   <span data-ttu-id="fbac0-137">Seu Teams app é criado em alguns segundos.</span><span class="sxs-lookup"><span data-stu-id="fbac0-137">Your Teams app is created within a few seconds.</span></span>

# <a name="command-line"></a>[<span data-ttu-id="fbac0-138">Linha de comando</span><span class="sxs-lookup"><span data-stu-id="fbac0-138">Command line</span></span>](#tab/cli)

<span data-ttu-id="fbac0-139">Use a CLI `teamsfx` para criar o seu primeiro projeto.</span><span class="sxs-lookup"><span data-stu-id="fbac0-139">Use the `teamsfx` CLI to create your first project.</span></span>  <span data-ttu-id="fbac0-140">Inicie pela pasta onde deseja criar a pasta do projeto.</span><span class="sxs-lookup"><span data-stu-id="fbac0-140">Start from the folder where you want to create the project folder.</span></span>

``` bash
teamsfx new
```

<span data-ttu-id="fbac0-141">A CLI lhe guiará através de algumas perguntas para criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="fbac0-141">The CLI walks through some questions to create the project.</span></span> <span data-ttu-id="fbac0-142">Cada pergunta lhe dirá como respondê-la, por exemplo, use teclas de seta para selecionar uma opção.</span><span class="sxs-lookup"><span data-stu-id="fbac0-142">Each question will tell you how to answer it, for example, use arrow keys to select an option.</span></span> <span data-ttu-id="fbac0-143">Depois de responder à pergunta, confirme sua escolha pressionando **Inserir**.</span><span class="sxs-lookup"><span data-stu-id="fbac0-143">When you have answered the question, confirm your choice by pressing **Enter**.</span></span>

1. <span data-ttu-id="fbac0-144">Selecione **Criar um novo aplicativo do Teams**.</span><span class="sxs-lookup"><span data-stu-id="fbac0-144">Select **Create a new Teams app**.</span></span>
1. <span data-ttu-id="fbac0-145">Selecione o **recurso Tab.**</span><span class="sxs-lookup"><span data-stu-id="fbac0-145">Select the **Tab** capability.</span></span>
1. <span data-ttu-id="fbac0-146">Selecione **Azure** como hospedagem front-end.</span><span class="sxs-lookup"><span data-stu-id="fbac0-146">Select **Azure** frontend hosting.</span></span> <span data-ttu-id="fbac0-147">Não selecione nenhum recurso em nuvem.</span><span class="sxs-lookup"><span data-stu-id="fbac0-147">Do not select any cloud resources.</span></span>
1. <span data-ttu-id="fbac0-148">Selecione **JavaScript** como linguagem de programação.</span><span class="sxs-lookup"><span data-stu-id="fbac0-148">Select **JavaScript** as the programming language.</span></span>
1. <span data-ttu-id="fbac0-149">Pressione **Inserir** para selecionar a pasta padrão do espaço de trabalho.</span><span class="sxs-lookup"><span data-stu-id="fbac0-149">Press **Enter** to select the default workspace folder.</span></span>
1. <span data-ttu-id="fbac0-150">Insira um nome adequado para seu aplicativo, como `helloworld`.</span><span class="sxs-lookup"><span data-stu-id="fbac0-150">Enter a suitable name for your app, like `helloworld`.</span></span>  <span data-ttu-id="fbac0-151">O nome do aplicativo deve consistir apenas de caracteres alfanuméricos.</span><span class="sxs-lookup"><span data-stu-id="fbac0-151">The name of the app must consist only of alphanumeric characters.</span></span>

   <span data-ttu-id="fbac0-152">Depois que todas as perguntas foram respondidas, seu projeto é criado.</span><span class="sxs-lookup"><span data-stu-id="fbac0-152">After all the questions have been answered, your project is created.</span></span>

---

## <a name="take-a-tour-of-the-source-code"></a><span data-ttu-id="fbac0-153">Faça um tour pelo código-fonte</span><span class="sxs-lookup"><span data-stu-id="fbac0-153">Take a tour of the source code</span></span>

<span data-ttu-id="fbac0-154">Se desejar pular esta seção por enquanto, você pode [executar seu aplicativo localmente](#run-your-app-locally).</span><span class="sxs-lookup"><span data-stu-id="fbac0-154">If you wish to skip this section for now, you can [run your app locally](#run-your-app-locally).</span></span>

<span data-ttu-id="fbac0-155">Após a Teams Toolkit configura seu projeto, você terá os componentes para criar um aplicativo pessoal básico para Teams.</span><span class="sxs-lookup"><span data-stu-id="fbac0-155">After the Teams Toolkit configures your project, you have the components to build a basic personal app for Teams.</span></span> <span data-ttu-id="fbac0-156">Os diretórios e arquivos do projeto são exibidos na área do Explorador do Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="fbac0-156">The project directories and files display in the Explorer area of Visual Studio Code.</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/react-app-project.png" alt-text="Captura de tela mostrando arquivos de projeto do aplicativo para um aplicativo pessoal no Visual Studio Code.":::

<span data-ttu-id="fbac0-158">O Kit de ferramentas cria automaticamente scaffolding para você no diretório do projeto com base nas capacidades que você adicionou durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="fbac0-158">The Toolkit automatically creates scaffolding for you in the project directory based on the capabilities you added during setup.</span></span> <span data-ttu-id="fbac0-159">O Kit de ferramentas do Teams mantém o estado de seu aplicativo no diretório `.fx`.</span><span class="sxs-lookup"><span data-stu-id="fbac0-159">The Teams Toolkit maintains its state for your app in the `.fx` directory.</span></span>  <span data-ttu-id="fbac0-160">Entre outros itens deste diretório:</span><span class="sxs-lookup"><span data-stu-id="fbac0-160">Among other items in this directory:</span></span>

- <span data-ttu-id="fbac0-161">Os ícones do aplicativo são armazenados como arquivos PNG em `color.png` e `outline.png`.</span><span class="sxs-lookup"><span data-stu-id="fbac0-161">The app icons are stored as PNG files in `color.png` and `outline.png`.</span></span>
- <span data-ttu-id="fbac0-162">O manifesto do aplicativo para publicação no Portal do Desenvolvedor do Teams é armazenado em `manifest.source.json`.</span><span class="sxs-lookup"><span data-stu-id="fbac0-162">The app manifest for publishing to the Developer Portal for Teams is stored in `manifest.source.json`.</span></span>
- <span data-ttu-id="fbac0-163">As configurações que você escolheu ao criar o projeto são armazenadas em `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="fbac0-163">The settings you chose when creating the project are stored in `settings.json`.</span></span>

<span data-ttu-id="fbac0-164">Como você selecionou a capacidade de guias durante a instalação, o Kit de ferramentas do Teams reúne todo o código necessário para uma guia básica no diretório `tabs`.</span><span class="sxs-lookup"><span data-stu-id="fbac0-164">Since you selected the tab capability during setup, the Teams Toolkit scaffolds all the necessary code for a basic tab in the `tabs` directory.</span></span> <span data-ttu-id="fbac0-165">Dentro deste diretório há vários arquivos importantes:</span><span class="sxs-lookup"><span data-stu-id="fbac0-165">Within this directory there are several important files:</span></span>

- <span data-ttu-id="fbac0-166">`tabs/src/index.jsx` é o ponto de entrada do front-end do aplicativo, onde o componente principal `App` é renderizado com `ReactDOM.render()`.</span><span class="sxs-lookup"><span data-stu-id="fbac0-166">`tabs/src/index.jsx` is the front-end app's entry point, where the main `App` component is rendered with `ReactDOM.render()`.</span></span>
- <span data-ttu-id="fbac0-167">`tabs/src/components/App.jsx` lida com o roteamento de URLs em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fbac0-167">`tabs/src/components/App.jsx` handles URL routing in your app.</span></span> <span data-ttu-id="fbac0-168">Ele chama o [Microsoft Teams JavaScript client SDK](../tabs/how-to/using-teams-client-sdk.md) para estabelecer a comunicação entre seu aplicativo e o Teams.</span><span class="sxs-lookup"><span data-stu-id="fbac0-168">It calls the [Microsoft Teams JavaScript client SDK](../tabs/how-to/using-teams-client-sdk.md) to establish communication between your app and Teams.</span></span>
- <span data-ttu-id="fbac0-169">`tabs/src/components/Tab.jsx` contém o código para implementar a IU do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fbac0-169">`tabs/src/components/Tab.jsx` contains the code to implement the UI of your app.</span></span>
- <span data-ttu-id="fbac0-170">`tabs/src/components/TabConfig.jsx` contém o código para implementar a IU que configura seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fbac0-170">`tabs/src/components/TabConfig.jsx` contains the code to implement the UI that configures your app.</span></span>

<span data-ttu-id="fbac0-171">Várias guias são exigidas pelo runtime do Teams, incluindo o aviso de privacidade, os termos de uso e as guias de configuração.</span><span class="sxs-lookup"><span data-stu-id="fbac0-171">Several tabs are required by the Teams runtime, including the privacy notice, terms of use, and configuration tabs.</span></span>  <span data-ttu-id="fbac0-172">O código para o aviso de privacidade e os termos de uso estão localizados no mesmo diretório.</span><span class="sxs-lookup"><span data-stu-id="fbac0-172">The code for the privacy notice and terms of use are located in the same directory.</span></span>

<span data-ttu-id="fbac0-173">Quando se adiciona a funcionalidade da nuvem, diretórios adicionais são adicionados ao projeto.</span><span class="sxs-lookup"><span data-stu-id="fbac0-173">When you add cloud functionality, additional directories are added to the project.</span></span>  <span data-ttu-id="fbac0-174">Principalmente, o diretório `api` retém o código para qualquer Azure Functions que você escreva.</span><span class="sxs-lookup"><span data-stu-id="fbac0-174">Most notably, the `api` directory holds the code to any Azure Functions you write.</span></span>

## <a name="run-your-app-locally"></a><span data-ttu-id="fbac0-175">Executar seu aplicativo localmente</span><span class="sxs-lookup"><span data-stu-id="fbac0-175">Run your app locally</span></span>

<span data-ttu-id="fbac0-176">O Kit de ferramentas do Teams permite que você execute seu aplicativo localmente.</span><span class="sxs-lookup"><span data-stu-id="fbac0-176">Teams Toolkit allows you to run your app locally.</span></span>  <span data-ttu-id="fbac0-177">Isto consiste de várias partes que são necessárias para fornecer a infraestrutura correta que o Teams espera:</span><span class="sxs-lookup"><span data-stu-id="fbac0-177">This consists of several parts that are necessary to provide the correct infrastructure that Teams expects:</span></span>

- <span data-ttu-id="fbac0-178">Um aplicativo está registrado no Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="fbac0-178">An application is registered with Azure Active Directory.</span></span>  <span data-ttu-id="fbac0-179">Este aplicativo tem permissões associadas ao local de onde o aplicativo é carregado e a quaisquer recursos de back-end que ele acesse.</span><span class="sxs-lookup"><span data-stu-id="fbac0-179">This application has permissions associated with the location that the app is loaded from and any backend resources it accesses.</span></span>
- <span data-ttu-id="fbac0-180">Uma API da Web é hospedada para auxiliar nas tarefas de autenticação, atuando como um proxy entre o aplicativo e o Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="fbac0-180">A web API is hosted to assist with authentication tasks, acting as a proxy between the app and Azure Active Directory.</span></span>  <span data-ttu-id="fbac0-181">Isto é executado pelo Azure Functions Core Tools.</span><span class="sxs-lookup"><span data-stu-id="fbac0-181">This is run by Azure Functions Core Tools.</span></span>  <span data-ttu-id="fbac0-182">Ele pode ser acessado na URL `https://localhost:5000`.</span><span class="sxs-lookup"><span data-stu-id="fbac0-182">It can be accessed at the URL `https://localhost:5000`.</span></span>
- <span data-ttu-id="fbac0-183">Os recursos HTML, CSS e JavaScript que compõem o front-end do aplicativo são hospedados em um serviço local.</span><span class="sxs-lookup"><span data-stu-id="fbac0-183">The HTML, CSS, and JavaScript resources that make up the front end of the app are hosted on a local service.</span></span> <span data-ttu-id="fbac0-184">Ele pode ser acessado em `https://localhost:3000`.</span><span class="sxs-lookup"><span data-stu-id="fbac0-184">It can be accessed at `https://localhost:3000`.</span></span>
- <span data-ttu-id="fbac0-185">Um manifesto de aplicativo é gerado e existe no Portal de Desenvolvedor do Teams.</span><span class="sxs-lookup"><span data-stu-id="fbac0-185">An app manifest is generated and exists in the Developer Portal for Teams.</span></span>  <span data-ttu-id="fbac0-186">O Teams usa o manifesto do aplicativo para dizer aos clientes conectados de onde carregar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fbac0-186">Teams uses the app manifest to tell connected clients where to load the app from.</span></span>

<span data-ttu-id="fbac0-187">Depois que isso for feito, o aplicativo poderá ser carregado no cliente Teams cliente.</span><span class="sxs-lookup"><span data-stu-id="fbac0-187">After this is done, the app can be loaded within the Teams client.</span></span>  <span data-ttu-id="fbac0-188">Usamos o cliente Web do Teams para que possamos ver o código HTML, CSS e JavaScript dentro de um ambiente de desenvolvimento web padrão.</span><span class="sxs-lookup"><span data-stu-id="fbac0-188">We use the Teams web client so that we can see the HTML, CSS, and JavaScript code within a standard web development environment.</span></span>

### <a name="build-and-run-your-app-locally-in-visual-studio-code"></a><span data-ttu-id="fbac0-189">Compilar e executar seu aplicativo localmente em Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="fbac0-189">Build and run your app locally in Visual Studio Code</span></span>

<span data-ttu-id="fbac0-190">Para compilar e executar seu aplicativo localmente:</span><span class="sxs-lookup"><span data-stu-id="fbac0-190">To build and run your app locally:</span></span>

1. <span data-ttu-id="fbac0-191">No Visual Studio Code, pressione **F5** para executar seu aplicativo no modo de depuração.</span><span class="sxs-lookup"><span data-stu-id="fbac0-191">From Visual Studio Code, press **F5** to run your application in debug mode.</span></span>

   > <span data-ttu-id="fbac0-192">Quando você executa o aplicativo pela primeira vez, todas as dependências são baixadas e o aplicativo é compilado.</span><span class="sxs-lookup"><span data-stu-id="fbac0-192">When you run the app for the first time, all dependencies are downloaded and the app is built.</span></span>  <span data-ttu-id="fbac0-193">Uma janela do navegador é aberta automaticamente quando a compilação é concluída.</span><span class="sxs-lookup"><span data-stu-id="fbac0-193">A browser window automatically opens when the build is complete.</span></span>  <span data-ttu-id="fbac0-194">Isto pode levar de 3 a 5 minutos para ser concluído.</span><span class="sxs-lookup"><span data-stu-id="fbac0-194">This can take 3-5 minutes to complete.</span></span>

   <span data-ttu-id="fbac0-195">A Toolkit solicita que você instale um certificado local, se necessário.</span><span class="sxs-lookup"><span data-stu-id="fbac0-195">The Toolkit prompts you to install a local certificate if required.</span></span> <span data-ttu-id="fbac0-196">Esse certificado permite que o Teams carregue seu aplicativo a partir de `https://localhost`.</span><span class="sxs-lookup"><span data-stu-id="fbac0-196">This certificate allows Teams to load your application from `https://localhost`.</span></span> <span data-ttu-id="fbac0-197">Selecione Sim quando aparecer a seguinte caixa de diálogo:</span><span class="sxs-lookup"><span data-stu-id="fbac0-197">Select yes when the following dialog appears:</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/ssl-prompt.png" alt-text="Captura de tela mostrando como a solicitação de instalação de um certificado SSL para permitir que o Teams carregue seu aplicativo a partir do localhost.":::

1. <span data-ttu-id="fbac0-199">O navegador da Web começa a executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fbac0-199">Your web browser starts to run the app.</span></span> <span data-ttu-id="fbac0-200">Se for solicitado a abrir Teams área de trabalho, selecione **Cancelar** para permanecer no navegador.</span><span class="sxs-lookup"><span data-stu-id="fbac0-200">If prompted to open Teams desktop, select **Cancel** to remain in the browser.</span></span> <span data-ttu-id="fbac0-201">Você também pode ser solicitado a alternar para a área de trabalho Teams outras vezes; selecione o Teams web quando isso acontecer.</span><span class="sxs-lookup"><span data-stu-id="fbac0-201">You may also be prompted to switch to Teams desktop at other times; select the Teams web app when this happens.</span></span>

   :::image type="content" source="../assets/images/teams-toolkit-v2/launch-web-browser-and-pick-webapp.png" alt-text="Captura de tela mostrando como escolher a versão da web das equipes quando lançadas":::

1. <span data-ttu-id="fbac0-203">Entre com sua conta M365 quando solicitado.</span><span class="sxs-lookup"><span data-stu-id="fbac0-203">Sign in with your M365 account when prompted.</span></span>
1. <span data-ttu-id="fbac0-204">Quando solicitado a instalar o aplicativo no Teams, pressione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="fbac0-204">When prompted to install the app onto Teams, press **Add**.</span></span>

<span data-ttu-id="fbac0-205">Seu aplicativo agora é exibido:</span><span class="sxs-lookup"><span data-stu-id="fbac0-205">Your app is now displayed:</span></span>

:::image type="content" source="../assets/images/teams-toolkit-v2/react-finished-app.png" alt-text="Captura de tela do aplicativo concluído":::

<span data-ttu-id="fbac0-207">Você pode fazer atividades normais de depuração como se fosse qualquer outro aplicativo Web, como a configuração de pontos de interrupção.</span><span class="sxs-lookup"><span data-stu-id="fbac0-207">You can do normal debugging activities as if this were any other web application, such as setting breakpoints.</span></span> <span data-ttu-id="fbac0-208">O aplicativo dá suporte à recarga dinâmica.</span><span class="sxs-lookup"><span data-stu-id="fbac0-208">The app supports hot reloading.</span></span> <span data-ttu-id="fbac0-209">Se você alterar qualquer arquivo dentro do projeto, a página será recarregada.</span><span class="sxs-lookup"><span data-stu-id="fbac0-209">If you change any file within the project, the page will be reloaded.</span></span>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="fbac0-210">Saiba o que acontece quando você executa seu aplicativo localmente no depurador.</span><span class="sxs-lookup"><span data-stu-id="fbac0-210">Learn what happens when you run your app locally in the debugger.</span></span></summary>

<span data-ttu-id="fbac0-211">Quando você pressiona a **tecla F5,** o Teams Toolkit:</span><span class="sxs-lookup"><span data-stu-id="fbac0-211">When you press the **F5** key, the Teams Toolkit:</span></span>

* <span data-ttu-id="fbac0-212">Registra seu aplicativo com Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="fbac0-212">Registers your application with Azure Active Directory.</span></span>
* <span data-ttu-id="fbac0-213">*Sideloads* your app in Teams.</span><span class="sxs-lookup"><span data-stu-id="fbac0-213">*Sideloads* your app in Teams.</span></span>
* <span data-ttu-id="fbac0-214">Inicia o back-end do aplicativo em execução localmente usando as Ferramentas Principais da [Função do Azure.](/azure/azure-functions/functions-run-local?#start)</span><span class="sxs-lookup"><span data-stu-id="fbac0-214">Starts your application backend running locally using [Azure Function Core Tools](/azure/azure-functions/functions-run-local?#start).</span></span>
* <span data-ttu-id="fbac0-215">Inicia o front-end do aplicativo hospedado localmente.</span><span class="sxs-lookup"><span data-stu-id="fbac0-215">Starts your application front-end hosted locally.</span></span>
* <span data-ttu-id="fbac0-216">Inicia Microsoft Teams em um navegador da Web com um comando para instruir Teams a carregar o aplicativo de lado a partir de `https://localhost:3000/tab` .</span><span class="sxs-lookup"><span data-stu-id="fbac0-216">Starts Microsoft Teams in a web browser with a command to instruct Teams to side load the application from `https://localhost:3000/tab`.</span></span> <span data-ttu-id="fbac0-217">Essa é a URL registrada no manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fbac0-217">This is the URL registered in the application manifest.</span></span>

</details>

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="fbac0-218">Saiba como solucionar problemas comuns ao executar seu aplicativo localmente.</span><span class="sxs-lookup"><span data-stu-id="fbac0-218">Learn how to troubleshoot common issues when running your app locally.</span></span></summary>

<span data-ttu-id="fbac0-219">Para executar com êxito seu aplicativo no Teams, você deve ter uma conta do Teams que permite o sideload de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fbac0-219">To successfully run your app in Teams, you must have a Teams account that allows app sideloading.</span></span> <span data-ttu-id="fbac0-220">Para obter mais informações sobre abertura de conta, confira [pré-requisitos](prerequisites.md#enable-sideloading).</span><span class="sxs-lookup"><span data-stu-id="fbac0-220">For more information on account opening, see [prerequisites](prerequisites.md#enable-sideloading).</span></span>

</details>

[!INCLUDE [Provision and Deploy your app on Azure](~/includes/get-started/azure-provisioning-instructions.md)]

<!-- markdownlint-disable MD033 -->
<details>
<summary><span data-ttu-id="fbac0-221">Saiba o que acontece quando você implanta o seu aplicativo no Azure</span><span class="sxs-lookup"><span data-stu-id="fbac0-221">Learn what happens when you deployed your app to Azure</span></span></summary>

<span data-ttu-id="fbac0-222">Antes da implantação, o aplicativo era executado localmente:</span><span class="sxs-lookup"><span data-stu-id="fbac0-222">Before deployment, the application has been running locally:</span></span>

* <span data-ttu-id="fbac0-223">O back-end é executado usando o **Azure Functions Core Tools**.</span><span class="sxs-lookup"><span data-stu-id="fbac0-223">The backend runs using **Azure Functions Core Tools**.</span></span>
* <span data-ttu-id="fbac0-224">O ponto de extremidade HTTP do aplicativo, onde o Microsoft Teams carrega o aplicativo, é executado localmente.</span><span class="sxs-lookup"><span data-stu-id="fbac0-224">The application HTTP endpoint, where Microsoft Teams loads the application, runs locally.</span></span>

<span data-ttu-id="fbac0-225">A implantação envolve o provisionamento de recursos em uma assinatura ativa do Azure e a implantação ou carregamento do código back-end e front-end do aplicativo para o Azure.</span><span class="sxs-lookup"><span data-stu-id="fbac0-225">Deployment involves provisioning resources on an active Azure subscription and deploying or uploading the backend and frontend code for the application to Azure.</span></span>

* <span data-ttu-id="fbac0-226">O back-end, se configurado, usa uma variedade de serviços do Azure, incluindo o Azure App Service e o Azure Armazenamento.</span><span class="sxs-lookup"><span data-stu-id="fbac0-226">The backend if configured uses a variety of Azure services, including Azure App Service and Azure Storage.</span></span>
* <span data-ttu-id="fbac0-227">O front-end do aplicativo será implantado em uma conta de Armazenamento do Microsoft Azure configurada para hospedagem Web estática.</span><span class="sxs-lookup"><span data-stu-id="fbac0-227">The frontend application will be deployed to an Azure Storage account configured for static web hosting.</span></span>

</details>

## <a name="see-also"></a><span data-ttu-id="fbac0-228">Confira também</span><span class="sxs-lookup"><span data-stu-id="fbac0-228">See also</span></span>

* [<span data-ttu-id="fbac0-229">Visão geral dos tutoriais</span><span class="sxs-lookup"><span data-stu-id="fbac0-229">Tutorials Overview</span></span>](code-samples.md)
* [<span data-ttu-id="fbac0-230">Criar um programa bot de conversação</span><span class="sxs-lookup"><span data-stu-id="fbac0-230">Create a conversational bot app</span></span>](first-app-bot.md)
* [<span data-ttu-id="fbac0-231">Criar uma extensão de mensagem</span><span class="sxs-lookup"><span data-stu-id="fbac0-231">Create a messaging extension</span></span>](first-message-extension.md)
* [<span data-ttu-id="fbac0-232">Exemplos de código</span><span class="sxs-lookup"><span data-stu-id="fbac0-232">Code Samples</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples)
